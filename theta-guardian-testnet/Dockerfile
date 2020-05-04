FROM debian:stable-slim
MAINTAINER egoni <eg0ni@protonmail.com>

# run tasks
RUN apt-get update && apt-get upgrade curl -y \
        && groupadd -g 1000 theta \
        && useradd -u 1000 -g theta -s /bin/bash -m theta -d /opt/theta \
        && curl -k --output /usr/local/bin/theta `curl -k 'https://guardian-testnet-data.thetatoken.org/binary?os=linux&name=theta'` \
        && curl -k --output /usr/local/bin/thetacli `curl -k 'https://guardian-testnet-data.thetatoken.org/binary?os=linux&name=thetacli'` \
        && curl -k --output /opt/theta/.theta/snapshot --create-dirs `curl -k https://guardian-testnet-data.thetatoken.org/snapshot` \
        && curl -k --output /opt/theta/.theta/config.yaml `curl -k 'https://guardian-testnet-data.thetatoken.org/config?is_guardian=true'` \
        && chmod a+x /usr/local/bin/theta* \
        && chown theta:theta -R /opt/theta/.theta

# change user
USER theta

# prepare directory for volume container
VOLUME ["/opt/theta"]

# expose tcp ports
EXPOSE 30001 16888 6060

# go to home directory
WORKDIR /opt/theta/

# run daemon
CMD ["theta","start"]