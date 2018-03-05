# This Dockerfile pulls in everything in one hit, as opposed to using layers.

# Run a shell:
# docker run --rm -it -v "$PWD":/home/build mickmake/linux-asf2:latest /bin/bash
#
# Run 'make' in the current dir:
# docker run --rm -it -v "$PWD":/home/build mickmake/linux-asf2:latest

FROM debian:stretch-slim

ENV USER=mick

MAINTAINER MickMake <mick@mickmake.com>
LABEL version="1.0"
LABEL description="Docker container for building with ASF v3.37."


RUN DEBIAN_FRONTEND=noninteractive; export DEBIAN_FRONTEND; \
	apt-get -y update && \
	apt-get -y upgrade && \
	apt-get -y install wget unzip make automake autoconf openocd gcc-arm-none-eabi gdb-arm-none-eabi binutils-arm-none-eabi libnewlib-arm-none-eabi libstdc++-arm-none-eabi-newlib && \
	cd /usr/local && \
	echo "Fetching XDF... please wait..." && \
	wget --progress=bar:force -O /tmp/xdf.zip http://ww1.microchip.com/downloads/en/DeviceDoc/xdk-asf-3.37.zip && \
	unzip -qq /tmp/xdf.zip && \
	rm -rf /usr/local/__MACOSX/ /tmp/xdf.zip && \
	apt-get -y autoremove && apt-get -y clean && rm -rf /var/lib/apt/lists/

ENV ASF=/usr/local/xdk-asf-3.37

WORKDIR /home/build
CMD ["make"]

