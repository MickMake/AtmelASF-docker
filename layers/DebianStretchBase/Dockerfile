FROM debian:stretch-slim

ENV USER=mick

MAINTAINER MickMake <mick@mickmake.com>
LABEL version="1.0"
LABEL description="Docker container for building with ASF."


RUN DEBIAN_FRONTEND=noninteractive; export DEBIAN_FRONTEND; \
	apt-get -y update && \
	apt-get -y upgrade && \
	apt-get -y install make automake autoconf openocd gcc-arm-none-eabi gdb-arm-none-eabi binutils-arm-none-eabi libnewlib-arm-none-eabi libstdc++-arm-none-eabi-newlib && \
	apt-get -y remove publicsuffix openssl rename netbase libusb-0.1-4 libusb-1.0-0 libnettle6 libpsl5 libunistring0 ca-certificates libgpm2 libhidapi-hidraw0 libidn11 libjim0.76 libmagic-mgc libmagic1 libtasn1-6 && \
	dpkg --purge   publicsuffix openssl rename netbase libusb-0.1-4 libusb-1.0-0 libnettle6 libpsl5 libunistring0 ca-certificates libgpm2 libhidapi-hidraw0 libidn11 libjim0.76 libmagic-mgc libmagic1 libtasn1-6 && \
	apt-get -y autoremove && \
	apt-get -y clean && \
	rm -rf /var/lib/apt/lists/

