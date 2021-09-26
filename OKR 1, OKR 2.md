## OKR 1, OKR 2 scripts

Here is a short descriptions on how to measure OKR 1, OKR 2

These scripts were used for Grafana + Telegraf Dashboard 

http://194.163.131.85:3000/d/pIinMgN7k/joystream-monitoring?orgId=1&from=now-3h&to=now&refresh=10s 

### Prerequisites 

Install a script that every 10 minutes run Helios and save the output to the  following file.

This output will be used as an entry point for OKR 1, OKR 2 measurements.

Here is a text of a script:

```

#!/bin/bash

while true
do

/root/.volta/bin/yarn  --cwd /root/joystream/ helios --skip-asset-tests  >  /tmp/helios_tmp.txt

if [ -s /tmp/helios_tmp.txt ]; then
        # The file is not-empty.

        #rm /tmp/helios.txt
        mv /tmp/helios_tmp.txt /tmp/helios.txt

        sed -i '1d' /tmp/helios.txt
        sed -i '1d' /tmp/helios.txt
        sed -i '$ d' /tmp/helios.txt

        echo "`date -u`" > /tmp/lastrun.txt

fi

  sleep 600
done

```

Use your own pathes to the Yarn executable and to the folder where Joystream is installed.

The output file will have the following name 
```
/tmp/helios_tmp.txt
```

# OKR 1

This script should be run with an argument (Worker ID)

It returns 1 if the node is live (according to Helios output), othervise it returns 0. 

```
#!/bin/bash

i=$(jq -r  '.providers[] | select(.providerId=='${1}') | .status' /tmp/helios.txt)

if [[ "$i" == "OK" ]]; then
  echo "1"
else
  echo "0"
fi

```

# OKR 2

This script should be run with an argument (Worker ID)

It returns information about concentration of nodes in across datacenters.

It use Worked ID to find out in which AS the Worker's node is located. And then, it tries to find out whether other Workers have nodes in the same AS. 

Example output:
```
AS Number is 21409. There are 1 nodes in the same AS. Nodes concentration is 1/8.

```


```
#!/bin/bash


function returnASNumberByID() {
id=${1}
fullUrl=$(jq -r  '.providers[] | select(.providerId=='$id') | .endpoint' /tmp/helios.txt)
domain=$(sed -e 's/[^/]*\/\/\([^@]*@\)\?\([^:/]*\).*/\2/' <<< $fullUrl)

#echo $domain
if [ -z "$domain" ]
then
      #$var is empty"
      asNumber=''
else
      #\$var is NOT empty"

	ip=$(dig +short $domain)

	#return AS name
	asNumber=$(dig $(dig -x $ip | grep PTR | tail -n 1 | grep -Eo '[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}').origin.asn.cymru.com TXT +short | head -n1 | sed -r 's/^([^.]+).*$/\1/; s/^[^0-9]*([0-9]+).*$/\1/')
fi

echo $asNumber
}

targetASNumber=$(returnASNumberByID ${1})

if [ -z "$targetASNumber" ]
then
      # "\$var is empty"
      echo 'AS Number is EMPTY.'

else
      # "\$var is NOT empty"

declare -i        totalCounter=0
declare -i        theSameAS=0
shopt -s lastpipe # enable lastpipe

       jq -r  '.providers[].providerId' /tmp/helios.txt | while read i; do
       # do stuff with 

       #totalCounter=$[$totalCounter +1]
       tmpASNumber=$(returnASNumberByID $i) 

       #echo $tmpASNumber
       if [ -z "$tmpASNumber" ] 
       then
          continue
       fi
      
       if [ "$tmpASNumber" == "$targetASNumber" ]
       then
            theSameAS=$[$theSameAS +1]
       fi
       totalCounter=$[$totalCounter +1]

       done

       shopt -u lastpipe # disable lastpipe

       cons=$theSameAS/$totalCounter
       echo 'AS Number is '$targetASNumber'. There are '$theSameAS' nodes in the same AS. Nodes concentration is '$cons'.'
       fi

```
