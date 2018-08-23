# Install ubnt controller in Ubuntu 16.04LTS in GCP / AWS

## Follow this guide to setup the instance in GCP / AWS

https://help.ubnt.com/hc/en-us/articles/209376117-UniFi-Install-a-UniFi-Cloud-Controller-on-Amazon-Web-Services

```
$ give me super-powers
```

{% hint style="info" %}
 Notice Ubuntu 16.04LTS default use Java 9 runtime. Which is NOT support by the controller in 5.8.24.

Mongodb has to be 3.4.x
{% endhint %}

SSH to the instance and follow the step to install

```
# Fix unable to resolve host error
sudo nano -w /etc/hosts

# Install java 8
# http://tipsonubuntu.com/2016/07/31/install-oracle-java-8-9-ubuntu-16-04-linux-mint-18/

sudo add-apt-repository ppa:webupd8team/java
sudo apt update; sudo apt install oracle-java8-installer
java -version

sudo apt install oracle-java8-set-default

# Install mongodb 3.4.x
# https://docs.mongodb.com/v3.4/tutorial/install-mongodb-on-ubuntu/

sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 0C49F3730359A14518585931BC711F9BA15703C6

echo "deb [ arch=amd64,arm64 ] http://repo.mongodb.org/apt/ubuntu xenial/mongodb-org/3.4 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.4.list

sudo apt-get update

sudo apt-get install -y mongodb-org

# https://help.ubnt.com/hc/en-us/articles/220066768-UniFi-How-to-Install-Update-via-APT-on-Debian-or-Ubuntu

sudo echo 'deb http://www.ubnt.com/downloads/unifi/debian stable ubiquiti' | sudo tee /etc/apt/sources.list.d/100-ubnt-unifi.list

sudo wget -O /etc/apt/trusted.gpg.d/unifi-repo.gpg https://dl.ubnt.com/unifi/unifi-repo.gpg 

sudo apt-get update

sudo apt install unifi

```



