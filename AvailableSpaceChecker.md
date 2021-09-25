## AvailableSpaceChecker

The script will check your available disk space and send this information to HTTP page.
The address of HTTP page is http://your_ip_address:1500 

### Setup guide

Login your server. Run the following commands:

```
nano /tmp/freeStorage.sh
```

Insert text
                                                                                                                
```
#!/bin/bash


freeStorage=$(df -P | awk 'NR>2{sum+=$2}END{print sum/1000000}' | awk '{print int(($1+0.25)/0.5)*0.5}')
while true ; do echo -e "HTTP/1.1 200 OK\n\n $freeStorage" | nc -l -p 1500 -q 1; done

```
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

If there is no output on http://your_ip_address:1500, please open 1500 port by the following command

```
iptables -I INPUT -p tcp -m tcp --dport 1500 -j ACCEPT
```

Then restart your service
```
systemctl restart freeStorage
```
