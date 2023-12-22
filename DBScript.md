# DB script

```
#!/bin/bash

sudo apt update -y
sudo apt upgrade -y

wget -qO - https://www.mongodb.org/static/pgp/server-3.2.asc | sudo apt-key add -
echo "deb http://repo.mongodb.org/apt/ubuntu xenial/mongodb-org/3.2 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.2.list

sudo apt-get update
sudo apt-get install -y mongodb-org
sudo apt-get install -y mongodb-org=3.2.22 mongodb-org-server=3.2.22 mongodb-org-shell=3.2.22 mongodb-org-mongos=3.2.22 mongodb-org-tools=3.2.22
mongo -version

sed -i 's/bindIp: 127.0.0.1/bindIp: 0.0.0.0/' /etc/mongod.conf

sudo service mongod start

sudo systemctl enable mongod
```


