# Zcoind Docker
Docker image that runs the Zcoin zcoind node in a container for easy deployment.

## Requirement
* Project-specific hardware requirements
* Docker

Instructions for Ubuntu 18.04.4 LTS Docker installation can be found [here](https://github.com/egoni/docker/blob/master/README.md)
## Start
### Create volume
```
docker volume create --name=zcoind-data
```
### For normal node
```
docker run -v zcoind-data:/opt/zcoin --name=zcoind-node -d \
 -p 8168:8168 \
 zcoind:latest
```
### For masternode
```
docker run -v zcoind-data:/opt/zcoin --name=zcoind-node -d \
 --env MASTERNODEIP=X.X.X.X \
 --env MASTERNODEKEY=12345467j9828nf91idm94ngdf988888888888dddddddddssddd \
 -p 8168:8168 \
 zcoind:latest
```
### For testnet node
```
docker run -v zcoind-data:/opt/zcoin --name=zcoind-node -d \
 --env TESTNET=1 \
 -p 8168:8168 \
 zcoind:latest
```
## Update
Stop container
```
docker stop zcoind-node
```
Remove container
```
docker rm zcoind-node
```
Pull new image
```
docker pull egoni/zcoind:latest
```
Run container
```
docker run -v zcoind-data:/opt/zcoin --name=zcoind-node -d \
 -p 8168:8168 \
 zcoind:latest
```

