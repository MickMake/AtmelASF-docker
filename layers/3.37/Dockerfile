# This Dockerfile uses a layered approach to creating the ASF build container.

FROM mickmake/debian-base-asf:stretch

ENV USER=mick

MAINTAINER MickMake <mick@mickmake.com>
LABEL version="1.0"
LABEL description="Docker container for building with ASF."


RUN DEBIAN_FRONTEND=noninteractive; export DEBIAN_FRONTEND; \
	apt-get -y update && \
	apt-get -y install wget unzip && \
	cd /usr/local && \
	echo "Fetching XDF... please wait..." && \
	wget --progress=bar:force -O /tmp/xdf.zip http://ww1.microchip.com/downloads/en/DeviceDoc/xdk-asf-3.37.zip && \
	unzip -qq /tmp/xdf.zip && \
	rm -rf /usr/local/__MACOSX/ /tmp/xdf.zip && \
	apt-get -y autoremove && apt-get -y clean && rm -rf /var/lib/apt/lists/

ENV ASF=/usr/local/xdk-asf-3.37

WORKDIR /home/build
CMD ["make"]

