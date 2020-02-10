# Taken from https://github.com/Homegear/Homegear-Docker/blob/master/rpi-stable/Dockerfile
FROM resin/rpi-raspbian:stretch
MAINTAINER Jan Schulz-Hofen <hassio@0.jan.sh>

RUN apt-get update && apt-get -y install apt-transport-https \
    && wget \
    && ca-certificates \
    && apt-utils \
    && gnupg \
    && ntp \
    && tzdata \
    && vim \
    && less \
    && htop \
    && wget https://homegear.eu/packages/Release.key \
    && apt-key add Release.key && rm Release.key \
    && echo 'deb https://homegear.eu/packages/Raspbian/ stretch/' >> /etc/apt/sources.list.d/homegear.list

RUN apt-get update && apt-get -y install \
    && homegear \
    && homegear-nodes-core \
    && homegear-nodes-extra \
    && homegear-max \
    && rm -f /etc/homegear/dh1024.pem \
    && rm -f /etc/homegear/homegear.crt \
    && rm -f /etc/homegear/homegear.key \
    && cp -R /etc/homegear /etc/homegear.config \
    && cp -R /var/lib/homegear /var/lib/homegear.data \
    && apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

COPY start.sh /start.sh
RUN chmod +x /start.sh
CMD /start.sh

EXPOSE 2001 2002 2003
