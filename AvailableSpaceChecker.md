## AvailableSpaceChecker

The script will check your available disk space and send this information to HTTP page.
The address of HTTP page is http://your_ip_address:1500 

### Setup guide

Login your server. Run the following commands:

```
nano /tmp/freeStorage.sh
```

The following script will find accessible space in your $home folder.
Insert text. 
                                                                                                                
```
#!/bin/bash


freeStorage=$(df -BG $( getent passwd "$USER" | cut -d: -f6 ) | awk 'END{print $4}' | sed 's/[^0-9]*//g')
while true ; do echo -e "HTTP/1.1 200 OK\n\n $freeStorage" | nc -l -p 1500 -q 1; done

```
Notes:
This script will return all available space in your home folder (usually /root folder).
If you have extra space that is not mounted to this folder and as a result cannot be instantly used by IPFS, it will not be counted by script. 
If you have IPFS folder not in your home directory please see Bug fixing section for more further steps. 


Save file (Ctrl+o). Press Enter. Exit file (Ctrl+x)

Set executable rights for your script

```
chmod +x /tmp/freeStorage.sh
```
 
 Create a service that will run your script in a backbround.
 
```
  nano  /etc/systemd/system/freeStorage.service
  ```

The service file below supposed you are a root user. 
If you are not, please adjust the script accordingly.

Insert text

```
[Unit]
Description=demo service
After=network.target
StartLimitIntervalSec=0
[Service]
Type=simple
Restart=always
RestartSec=1
User=root
ExecStart=/tmp/freeStorage.sh

[Install]
WantedBy=multi-user.target
```


Save file (Ctrl+o). Press Enter. Exit file (Ctrl+x)

Start your service.

```
systemctl start freeStorage
```

Set your service to automatically run every time your server is restarted.

```
systemctl enable freeStorage
```


Everything is ready. Now you can check HTTP page http://your_ip_address:1500 and see your total available disk space. The output is provided in GB.

### Bug fixing

##### Bug fixing 1

If there is no output on http://your_ip_address:1500, please open 1500 port by the following command

```
iptables -I INPUT -p tcp -m tcp --dport 1500 -j ACCEPT
```

Then restart your service
```
systemctl restart freeStorage
```

#### Bug fixing 2

If your IPFS folder is not in your root folder make the following changes to the /tmp/freeStorage.sh script

This part returns the path to your home folder

```$( getent passwd "$USER" | cut -d: -f6 ) ```

You can change it to your CUSTOM path to IPFS folder. For example 

``` 
'/tmp/.ipfs/'
```

