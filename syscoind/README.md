# Syscoin
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