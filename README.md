# Variouse Blockchain Docker Images
## Requirements
* Ubuntu 18.04.4 LTS 
## Install Docker
Always follow the instructions from [https://docs.docker.com/install/linux/docker-ce/ubuntu/](https://docs.docker.com/install/linux/docker-ce/ubuntu/), the following instructions are only a quick reference:
```
apt-get remove docker docker-engine docker.io containerd runc
apt-get update
apt-get install -y \
 apt-transport-https \
 ca-certificates \
 curl \
 gnupg-agent \
 software-properties-common
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | apt-key add -
add-apt-repository \
 "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
 $(lsb_release -cs) \
 stable"
apt-get install -y docker-ce docker-ce-cli containerd.io
```
Test the installation
```
docker run hello-world
```