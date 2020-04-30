FROM debian:stable-slim
MAINTAINER egoni <eg0ni@protonmail.com>

# get zcoin binaries
ADD https://github.com/zcoinofficial/zcoin/releases/download/v0.13.8.10/zcoin-0.13.8.10-linux64.tar.gz /tmp/

# installing script and configuration files
COPY ./bin/* /usr/local/bin/

# run tasks
RUN apt-get update && apt-get upgrade -y \
	&& groupadd -g 1000 zcoin \
	&& useradd -u 1000 -g zcoin -s /bin/bash -m zcoin -d /opt/zcoin \
	&& tar -xvf /tmp/zcoin-*.tar.gz -C /tmp/ \
	&& cp /tmp/zcoin*/bin/* /usr/local/bin \
	&& rm -rf /tmp/zcoin* \
	&& chmod a+x /usr/local/bin/* \
	&& chown zcoin:zcoin -R /opt/zcoin

# change user
USER zcoin

# prepare directory for volume container
VOLUME ["/opt/zcoin"]

# expose tcp ports
EXPOSE 8168 18168

# go to home directory
WORKDIR /opt/zcoin

# run daemon
CMD ["zcoind_start"]