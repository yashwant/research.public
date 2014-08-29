---
layout: post
title: "Docker Container Virtualization"
slug: "research-docker-container-virtualization"
date: 2014-08-29 11:52
comments: true
categories: [virtualization]
tags: [docker, virtualization, devops, container, lxc]
published: true
---

# Docker

Docker is a tool that can package an application and its dependencies in a virtual container. This container can then be run on any Linux server that has docker installed.

This has benefits for several groups of people:

* Sysadmins can deploy and run any app on any infrastructure (that supports docker) quickly and reliably.
* Developers can easily test and develop applications in a docker containers that can be distributed to other developers and even staging/production. This way the typical "it worked in dev/on my laptop" can be avoided.

Docker extends Linux Containers (LXC) with a high-level API providing lightweight virtualization that runs processes in isolation. Containers offer quite some pros over virtual machines e.g. :

* You don't need an entire seperate operating system for your application
* Setting up containers is a lot faster than setting up a VM
* Containers are less resource hungry than VMs. They only take up as much memory/CPU as they need.

Competitors are e.g. Googles **[Kubernetes](https://github.com/GoogleCloudPlatform/kubernetes)** which looks a lot like a consumer version of their own internal [Omega](http://research.google.com/pubs/pub41684.html) scheduler.

Organizations that use Docker are e.g. Atlassian, eBay, Gilt, Groupon, RelateIQ, Spotify, Tutum

**Docker support**

* Amazon EC2
* CoreOS
* Google App Engine/ Compute Engine
* Microsoft Azure Cloud

## The 3 docker components

### Images - Build component

Docker images are basically a read-only template out of which docker containers are instantiated. Images contain all the information on a certain type of container.

These images can either be defined by Dockerfiles or by commiting a container. When trying to run a container, docker will automatically download the image you specified. This will become more clear at the examples.

### Registries - Distribution component

We need a way to share our images with other locations: enter the registry.

Docker provides a public hub where you can upload and share your images. (https://hub.docker.com/) You get one free private repository and unlimited public repositories. You could also host your own registry, more instructions can be found here: http://blog.docker.com/2013/07/how-to-use-your-own-registry/

Once the image is on a registry, you can run the same container on another location.

### Containers - Run component

Containers are created from an image. These containers hold everything needed for our apps to run. These containers can be run/started/stopped/removed/...

It is possible to turn a container into an image by using the docker commit command.

#### What are those containers?

* Technically `~chroot` on steroids
* a container is a set of processes (running on top of the common kernel)
* isolated from the rest of the machine
* using *namespaces* to have private view of the system (network interfaces, PID tree, mountpoints… )
* and *cgroups* to have metered/ limited/ reserved resources
* The default container format is called *libcontainer*. Docker also supports traditional Linux containers using LXC. In the future, Docker may support other container formats, for example, by integrating with BSD Jails or Solaris Zones.

## Basic commands

Simple example:

* `docker run ubuntu:14.04 date`
	* `docker run` means execute the run command
	* `ubuntu:14.04` instantiate a container of Ubuntu version 14.04
	* `date` is the command that our container will execute

### Lifecycle

* `docker run` - creates a container
* `docker stop <container name>` - stops it
* `docker start <container name>` - will start it again
* `docker restart` - restarts a container
* `docker kill` - sends a SIGKILL to a container
* `docker attach` - will connect to a running container
	* Ctrl+c – for a quiet exit
	* Ctrl-\ – to detach with a stack trace
* `docker wait` - blocks until container stops
* `docker remove <container name>`
* `docker run -t -i -p 8080:80 kristofdm/lamp /bin/bash`
	* `docker run` means execute the run command
	* `-t` means that we want a tty to be applied
	* `-i` means that we want to be able to interact with our container
	* `-p` port mapping! host_port:container_port. Our websites will be available at localhost:8080
	* `kristofdm/lamp` is a simple LAMP image
	* `bin/bash` is the command that the container will execute
* `docker run -p 8080:80 -v /home/drupal-7.28:/var/www/ kristofdm/drupal:latest /start.sh`
	* `-v` stands for volume. In this case, a volume shared between the host and the container.
* If you want a transient container, `docker run -rm` will remove the container after it stops.

### Info

* `docker ps` - shows running containers.
* `docker ps -a` - shows running and stopped containers.
* `docker inspect` - looks at all the info on a container (including IP address).
* `docker logs` - gets logs from container.
* `docker events` - gets events from container.
* `docker port` - shows public facing port of container.
* `docker top` - shows running processes in container.
* `docker diff` - shows changed files in the container's FS.

### Import / Export

There does not seem to be a way to use Docker directly to import files into a container's filesystem. The closest thing is to mount a host file or directory as a data volume and copy it from inside the container.

* `docker cp` - copies files or folders out of a container's filesystem.
* `docker export` - turns container filesystem into tarball.

### Entering a Docker Container

* `nsenter` allows you to run any command (e.g. a shell) inside a container that's already running another command (e.g. your database or webserver). This allows you to see all mounted volumes, check on processes, log files etc. inside a running container.

### Images

#### Lifecycle

* `docker images` - shows all images
* `docker import` - creates an image from a tarball.
* `docker build` - creates image from Dockerfile.
* `docker commit` - creates image from a container.
* `docker rmi` - removes an image.
* `docker insert` - inserts a file from URL into image. (kind of odd, you'd think images would be immutable after create)
* `docker load` - loads an image from a tar archive as STDIN, including images and tags (as of 0.7).
* `docker save` - saves an image to a tar archive stream to STDOUT with all parent layers, tags & versions (as of 0.7).

#### Info

* `docker history` - shows history of image.
* `docker tag` - tags an image to a name (local or registry).

#### Registry & Repository

A repository is a *hosted* collection of tagged images that together create the file system for a container.

A registry is a host -- a server that stores repositories and provides an HTTP API for [managing the uploading and downloading of repositories](http://docs.docker.com/userguide/dockerrepos/).

Docker.io hosts its own [index](https://registry.hub.docker.com) to a central registry which contains a large number of repositories.

* `docker login` - to login to a registry.
* `docker search` - searches registry for image.
* `docker pull` - pulls an image from registry to local machine.
* `docker push` - pushes an image to the registry from local machine.

#### Shortcuts

* `docker rm -f $(docker ps -a -q) ; docker rmi $(docker images -q -a)` - removing all containers and images

## Dockerfile

Dockerfile Syntax Example

	# Dockerfile to install Nginx
	# VERSION 2 - EDITION 1
	FROM ubuntu
	MAINTAINER O.S. Tezer, ostezer@gmail.com

Docker uses the **Dockerfile** to build images. The build process is initiated by the `docker build` command.

`docker build -t="my_nginx_image"` - the -t flag allows us to specify a name for our new image, here my_nginx_image.

### Dockerfile Commands

* `MAINTAINER <author name>` - set an author field
* `RUN <command>` - execute a command in a shell or exec form. The RUN instruction adds a new layer on top of the newly created image.
* `ADD <src> <destination>` - copy files from one location to another using the ADD instruction. It takes two arguments <source> and <destination>. The destination is a path in the container. The source can be either a URL or a file in the context of the launch config.
* `CMD ["executable","param1","param2"]` or `CMD ["param1","param2"]` or `CMD command param1 param2` - defaults for an executing container are provided using the CMD command. DockerFile allows usage of the CMD instruction only once. Multiple usage of CMD nullifies all previous CMD instructions.
* `EXPOSE <port>` - specify the port on which the container will be listening at runtime by running the EXPOSE instruction.
* `ENTRYPOINT [‘executable’, ‘param1’,’param2’]` or `ENTRYPOINT command param1 param2` - configure a container to run as an executable, which means a specific application can be set as default and run every time a container is created using the image. This also means that the image will be used only to run and target the specific application each time it is called.
* `ENV` - The ENV command is used to set the environment variables (one or more). These variables consist of “key = value” pairs which can be accessed within the container by scripts and applications alike. This functionality of docker offers an enormous amount of flexibility for running programs.
* `FROM` - defines the base image to use to start the build process.
* `USER` - the USER directive is used to set the UID (or username) which is to run the container based on the image being built.
* `VOLUME` - the VOLUME command is used to enable access from your container to a directory on the host machine (i.e. mounting it).
* `WORKDIR` - the WORKDIR directive is used to set where the command defined with CMD is to be executed.

## Working with Docker Hub

* `docker login` - login to your Docker Hub account. Your authentication credentials will be stored in the .dockercfg authentication file in your home directory.

### Automated Builds

1. Create a [Docker Hub](https://hub.docker.com) account and login.
2. Link your GitHub or BitBucket account through the ["Link Accounts"](https://registry.hub.docker.com/account/accounts/) menu.
3. [Configure an Automated Build](https://registry.hub.docker.com/builds/).
4. Pick a GitHub or BitBucket project that has a `Dockerfile` that you want to build.
5. Pick the branch you want to build (the default is the `master` branch).
6. Give the Automated Build a name.
7. Assign an optional Docker tag to the Build.
8. Specify where the `Dockerfile` is located. The default is `/`.

Once the Automated Build is configured it will automatically trigger a build and, in a few minutes, you should see your new Automated Build on the [Docker Hub](https://hub.docker.com) Registry. It will stay in sync with your GitHub and BitBucket repository until you deactivate the Automated Build.

If you want to see the status of your [Automated Builds](https://registry.hub.docker.com/builds/), you can go to your Automated Builds page on the Docker Hub, and it will show you the status of your builds and their build history.

### Run you own Private Docker Image Repository

* Github: [docker/docker-registry](https://github.com/docker/docker-registry)
* [Docker Registry or How to Run your own Private Docker Image Repository](https://blog.codecentric.de/en/2014/02/docker-registry-run-private-docker-image-repository/)
* Github: [lukaspustina/docker-registry-demo](https://github.com/lukaspustina/docker-registry-demo) – Show how to use a private Docker image repository / registry.

## Installation (OS X)

If you are running Mac OS X you should install Homebrew for easier handling…

### Install Homebrew

	ruby -e "$(curl -fsSL https://raw.github.com/Homebrew/homebrew/go/install)"

### Install VirtualBox

With Homebrew, it’s trivial to install VirtualBox which is a prerequisite to running docker on OS X:

	brew update
	brew tap phinze/homebrew-cask
	brew install brew-cask
	brew cask install virtualbox

### Option 1: Install boot2docker

Boot2docker is a small script that helps download and setup a minimal Linux VM that will be in charge of running docker daemon.

	brew install boot2docker
	boot2docker init
	boot2docker up
	export DOCKER_HOST=tcp://localhost:4243
	# docker will be automatically too, since it is a boot2docker dependancy

### Option 2: Install CoreOS with Vagrant

* work in progress

### Other installation methods

* [Running Docker with EC2](https://docs.docker.com/installation/amazon/)

## Docker security

Docker daemon runs with root privileges, which implies there are some issues that need extra care. Some interesting points include the following:

* Control of Docker daemon should only be given to authorized users as Docker allows directory sharing with a guest container without limiting access rights.
* The REST API endpoint now supports UNIX sockets, thereby preventing cross-site-scripting attacks.
* REST API can be exposed over HTTP using appropriate trusted networks and VPNs.
* Run Docker exclusively on a server (when done), isolating all other services.

Some key Docker security features include the following:

1. Processes, when run as non-privileged users in the containers, maintain a good level of security.
2. Apparmor, SELinux, GRSEC solutions can be used for an extra layer of security.
3. There’s a capability to inherit security features from other containerization systems.

### Interesting articles

* [Docker security I: SELinux](http://opensource.com/business/14/7/docker-security-selinux)
* Slideshare: [LXC, Docker, security: is it safe to run applications in Linux Containers?](http://de.slideshare.net/jpetazzo/is-it-safe-to-run-applications-in-linux-containers)
* [Securing Docker’s Future with SELinux and the Open Source Way](https://www.openshift.com/blogs/securing-docker’s-future-with-selinux-and-the-open-source-way)

## Snippets unsorted

Some things I found as interesting but I did not manage to sort right now.

* `VBoxManage modifyvm "boot2docker-vm" --natpf1 "tcp-port4000,tcp,,4000,,4000"`
* .dockerignore - https://github.com/docker/docker/blob/master/.dockerignore

## Open questions

These are still some things I have to learn about… (this is more or less a reminder to myself)

* How does **nsenter** work?