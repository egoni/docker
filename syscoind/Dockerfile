FROM debian:stable-slim
MAINTAINER egoni <eg0ni@protonmail.com>

# get syscoin binaries
ADD https://github.com/syscoin/syscoin/releases/download/v4.1.3/syscoin-4.1.3-x86_64-linux-gnu.tar.gz /tmp/

# get sentinel binaries
ADD https://github.com/syscoin/sentinel/archive/1.1.1.tar.gz /tmp/

# installing script and configuration files
COPY ./bin/* /usr/local/bin/

# run tasks
RUN apt-get update && apt-get upgrade -y \
	&& apt-get install -y python3-virtualenv virtualenv net-tools telnet \
	&& groupadd -g 1000 syscoin \
	&& useradd -u 1000 -g syscoin -s /bin/bash -m syscoin -d /opt/syscoin \
	&& tar -xvf /tmp/syscoin-*.tar.gz -C /tmp/ \
	&& tar -xvf /tmp/1.1.1.tar.gz -C /tmp/ \
	&& cp /tmp/syscoin*/bin/* /usr/local/bin \
	&& cp -r /tmp/sentinel* /opt/sentinel \
	&& rm -rf /tmp/syscoin* \
	&& rm -rf /tmp/sentinel* \
	&& chmod a+x /usr/local/bin/* \
	&& chown syscoin:syscoin -R /opt/syscoin \
	&& chown syscoin:syscoin -R /opt/sentinel

# change user
USER syscoin

# installing sentinel
RUN cd /opt/sentinel && virtualenv -p python3 ./venv \
	&& ./venv/bin/pip install -r requirements.txt \
	&& sed -i -e 's/#syscoin_conf=\/home\/YOURUSERNAME\/.syscoincore\/syscoin.conf/syscoin_conf=\/opt\/syscoin\/.syscoin\/syscoin.conf/g' /opt/sentinel/sentinel.conf \
	&& chown syscoin:syscoin -R /opt/sentinel

# prepare directory for volume container
VOLUME ["/opt/syscoin"]

# expose tcp ports
EXPOSE 30303 8369 18369 18370

# go to home directory
WORKDIR /opt/syscoin

# run daemon
CMD ["syscoin_start"]
