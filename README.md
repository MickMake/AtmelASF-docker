![WPLib-Box](https://www.mickmake.com/banner.png)


# ASF build Docker container
This repository provides you with a full development environment supporting [ASF](http://asf.atmel.com/docs/latest/) within a Docker container. It currently provides version 3.37 of ASF.


## Quick Start (for the impatient)

Pull down the GitHub repo and build. This make take a while. It ends up being around 2.4GB.
```
git clone https://github.com/mickmake/AtmelASF-docker.git
cd AtmelASF-docker/full
make build
```

Then run a shell within that container:

`make shell`

Or change directory to your source tree and compile using 'make':
```
cd /some/dir/on/your/pc
docker run --rm -i -t -v "$PWD":/home/build mickmake/debian-asf:3.37 make
```


## Supported tags and respective Dockerfiles
`3.37`, `latest` _([3.37/Dockerfile](https://github.com/mickmakes/AtmelASF-docker/blob/master/full/3.37/Dockerfile))_

`3.37`, `latest` _([3.37/Dockerfile](https://github.com/mickmakes/AtmelASF-docker/blob/master/layers/3.37/Dockerfile))_



## Using this container.
Two options.
1. Pull from Docker Hub.
2. Or you can use the GitHub method to build and run the container.
The container ends up being around 2.4GB. DockerHub should be the quickest method if you don't want to customize.


## Using it from Docker Hub

### Links
(Docker Hub repo)[https://hub.docker.com/r/mickmake/debian-asf/]

(Docker Cloud repo)[https://cloud.docker.com/swarm/mickmake/repository/docker/mickmake/debian-asf/]


### Setup from Docker Hub
A simple `docker pull mickmake/debian-asf` will pull down the latest version.


### Runtime from Docker Hub
start - Spin up a Docker container with the correct runtime configs. This will later support remote builds, (to avoid restarting containers).

`docker run -d --name debian-asf-3.37 -v "$PWD":/home/build mickmake/debian-asf:3.37`

stop - Stop a Docker container.

`docker stop debian-asf-3.37`

run - Run a Docker container in the foreground, (all STDOUT and STDERR will go to console). The Container will be removed on termination.

`docker run --rm -v "$PWD":/home/build mickmake/debian-asf:3.37`

shell - Run a shell, (/bin/bash), within a Docker container.

`docker run --rm -i -t -v "$PWD":/home/build mickmake/debian-asf:3.37 /bin/bash`

make - Run make within the current directory.

`docker run --rm -i -t -v "$PWD":/home/build mickmake/debian-asf:3.37`

rm - Remove the Docker container. Not needed if you use the `-i -t` flags.

`docker container rm debian-asf-3.37`


## Using it from GitHub repo

### Setup from GitHub repo
Simply clone this repository to your local machine

`git clone https://github.com/mickmakes/AtmelASF-docker.git`


### Building from GitHub repo
You have two build choices:
1. [Using a layered approach](https://github.com/mickmakes/AtmelASF-docker/blob/master/full/) - This will allow you to build on top of other base containers, such as Debian, Alpine, etc.
2. [All-in-one](https://github.com/mickmakes/AtmelASF-docker/blob/master/layers/) - Will build straight from the O/S reference container.


`make build` - Build Docker images. Build all versions from the base directory or specific versions from each directory.


`make list` - List already built Docker images. List all versions from the base directory or specific versions from each directory.


`make clean` - Remove already built Docker images. Remove all versions from the base directory or specific versions from each directory.


`make push` - Push already built Docker images to Docker Hub, (only for WPLib admins). Push all versions from the base directory or specific versions from each directory.


### Runtime from GitHub repo
When you `cd` into a version directory you can also perform a few more actions.

`make start` - Spin up a Docker container with the correct runtime configs.


`make stop` - Stop a Docker container.


`make run` - Run a Docker container in the foreground, (all STDOUT and STDERR will go to console). The Container be removed on termination.


`make shell` - Run a shell, (/bin/bash), within a Docker container.


`make rm` - Remove the Docker container.


`make test` - Will issue a `stop`, `rm`, `clean`, `build`, `create` and `start` on a Docker container.


