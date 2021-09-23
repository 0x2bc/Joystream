### AvailableSpaceChecker

This script will check your available disk space and print on HTTP page with the following address http://your_ip_address:1500 

Login your server. Run the following commands:

```
touch /tmp/freeStorage.sh
```

```
chmod +x /tmp/freeStorage.sh
```
```
nano /tmp/freeStorage.sh
```

Insert text
                                                                                                                
```
#!/bin/bash


freeStorage=$(df -P | awk 'NR>2{sum+=$2}END{print sum/1000000}' | awk '{print int(($1+0.25)/0.5)*0.5}')
while true ; do echo -e "HTTP/1.1 200 OK\n\n $freeStorage" | nc -l -p 1500 -q 1; done

```
Save file

```
touch /etc/systemd/system/freeStorage.service
```
```
  nano  /etc/systemd/system/freeStorage.service
  ```

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


Save file

```
systemctl start freeStorage
```
```
systemctl enable freeStorage
```


check HTTP page http://<your ip>:1500 
you should see your free storeage size here
