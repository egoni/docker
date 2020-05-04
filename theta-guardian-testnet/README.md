# Guardian node for the theta guardian testnet Docker
Docker image that runs the guardian node for the theta guardian testnet in a container for easy deployment.

## Requirement
* Project-specific hardware requirements
* Docker

Instructions for Ubuntu 18.04.4 LTS Docker installation can be found [here](https://github.com/egoni/docker/blob/master/README.md)
## Start
### Create volume
```
docker volume create --name=theta-data
```
### Start
```
docker run -v theta-data:/opt/theta --name=theta-guardian-testnet -it -p 30001:30001 theta-guardian-testnet:latest
```
On prompt type your guardian node password, to dettach press <kbd>CTRL</kbd>+<kbd>P</kbd> followed by <kbd>CTRL</kbd>+<kbd>Q</kbd>.
### Get sync status
```
docker exec theta-guardian-testnet thetacli query status
```

See [here](https://github.com/thetatoken/guardian-testnet-guide/blob/master/docs/CLI.md#running-a-guardian-node-through-command-line) for more information