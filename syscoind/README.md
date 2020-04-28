# Syscoin
## Requirement
* Project-specific hardware requirements
* Docker

Instructions for Ubuntu 18.04.4 LTS Docker installation can be found [here](https://github.com/egoni/docker/blob/master/README.md)
## Setup
### Create volume
```
docker volume create --name=syscoind-data
```
### For normal node
```
docker run -v syscoind-data:/opt/syscoin --name=syscoind-node -d \
 -p 30303:30303 \
 -p 8369:8369 \
 syscoind:latest
```
### For masternode node
```
docker run -v syscoind-data:/opt/syscoin --name=syscoind-node -d \
 --env MASTERNODEIP=X.X.X.X \
 --env MASTERNODEKEY=12345467j9828nf91idm94ngdf988888888888dddddddddssddd \
 -p 30303:30303 \
 -p 8369:8369 \
 syscoind:latest
```
### For testnet node
```
docker run -v syscoind-data:/opt/syscoin --name=syscoind-node -d \
 --env TESTNET=1 \
 -p 30303:30303 \
 -p 18369:18369 \
 syscoind:latest
```
## Update
Stop container
```
docker stop syscoind-node
```
Remove container
```
docker rm syscoind-node
```
Pull new image
```
docker pull egoni/syscoind:latest
```
Run container
```
docker run -v syscoind-data:/opt/syscoin --name=syscoind-node -d \
 -p 30303:30303 \
 -p 8369:8369 \
 syscoind:latest
```

