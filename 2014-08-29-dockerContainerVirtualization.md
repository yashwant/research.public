---
layout: post
title: "Docker Container Virtualization"
slug: "research-docker-container-virtualization"
date: 2014-09-17 11:40
comments: true
categories: [virtualization]
tags: [docker, virtualization, devops, container, lxc, libcontainer]
published: true
---

# Docker

Docker is a tool that can package an application and its dependencies in a virtual container. This container can then be run on any Linux server that has docker installed.

This has benefits for several groups of people:

* Sysadmins can deploy and run any app on any infrastructure (that supports docker) quickly and reliably.
* Developers can easily test and develop applications in a docker containers that can be distributed to other developers and even staging/production. This way the typical "it worked in dev/on my laptop" can be avoided.

Docker includes the [libcontainer](https://github.com/docker/libcontainer) library as a reference implementation for containers, and builds on top of libvirt, LXC (Linux containers) and systemd-nspawn, which provide interfaces to the facilities provided by the Linux kernel. 

![How libcontainer works with Linux services](http://cdn-static.zdnet.com/i/r/story/70/00/030397/libcontainer-diagram-620x465.png?hash=AGV3ZTD3Lw&upscale=1)

[Source (image)](http://www.zdnet.com/docker-libcontainer-unifies-linux-container-powers-7000030397/)

Containers offer quite some pros over virtual machines e.g. :

* You don't need an entire separate operating system for your application
* Setting up containers is a lot faster than setting up a VM
* Containers are less resource hungry than VMs. They only take up as much memory/CPU as they need.

Organizations that use Docker are e.g. Atlassian, eBay, Gilt, Groupon, RelateIQ, Spotify, Tutum

**Docker (Host) support**

* Amazon EC2
* CoreOS
* Google App Engine/ Compute Engine
* Microsoft Azure Cloud
* Ubuntu, RHEL, Debian, CentOS, Fedora, Oracle Linux, SuSe, Arch Linux, Gentoo

Docker can be run on any x64 host (64-bit architecture e.g. x86_64 and amd64 only – 32-bit is **not** supported) running a modern Linux kernel (>= 3.8). The kernel must support an appropriate storage driver e.g. Device Mapper, AUFS, vfs, btfrs (default is usually Device Mapper).

## The 3 docker components

### Images - Build component

At the base of a container is a boot filesystem, **bootfs** which resembles the typical Linux/Unix boot filesystem. When a container has booted, it is moved into memory, and the boot filesystem is unmounted to free up the **RAM** used by the **initrd** disk image. Docker next layers a root filesystem, **rootfs**, on top of the boot filesystem. This **rootfs** can be one or more operating systems (e.g., a Debian or Ubuntu filesystem).

In opposite to traditional Linux distributions **rootfs** stays in read-only mode and Docker takes advantage of a **union mount** to add more read only filesystems onto the root filesystem. A **union mount** is a mount that allows several filesystems to be mounted at one time but appear to be one filesystem. The union mount overlays the filesystems on top of one another so that the resulting filesystem may contain files and subdirectories from any or all of the underlying filesystems.

Docker calls each of these filesystems images. Images can be layered on top of one another. Images can either be defined by Dockerfiles or by committing a container. When trying to run a container, docker will automatically download the image you specified. This will become more clear at the examples.

The Docker filesystem layers look like this…

* Writeable Container
* Image
	* Add e.g. Apache
* Image
	* Add e.g. emacs
* Base Image
	* e.g. Ubuntu
* bootfs
	* cgroups, namespace, device mapper
	* Kernel

When Docker first starts a container, the initial read-write layer is empty. As changes occur, they are applied to this layer; for example, if you want to change a file, then that file will be copied from the read-only layer below into the read-write layer. The read-only version of the file will still exist but it is now hidden underneath the copy.  
This pattern is traditionally called "copy on write" and is one of the features that makes Docker so powerful.

Local images live on the local Docker host in the `/var/lib/docker` and `var/lib/docker/containers` directory. Each image will be inside a directory named for your storage driver; for example, *aufs* or *devicemapper*. 

#### Base images

* [phusion/baseimage-docker](http://phusion.github.io/baseimage-docker/), comes with init processes for syslog-ng, cron daemon, sshd, runit. **Attention:** It is highly [discussable](https://news.ycombinator.com/item?id=7951042) if adding sshd is a good idea. Out of security reasons *nsenter* would probably be the way to go…
	* Github: [phusion/baseimage-docker](https://github.com/phusion/baseimage-docker)
	* Docker registry: [phusion/baseimage](https://registry.hub.docker.com/u/phusion/baseimage/)

### Registries - Distribution component

Images live inside repositories, and repositories live on registries. There are two types of registries: public and private.

Docker, Inc. itself provides a **[public hub](https://hub.docker.com/)** where you can upload and share your images. You get one free private repository and unlimited public repositories. You could also **host your own registry**, more instructions can be found [here](http://blog.docker.com/2013/07/how-to-use-your-own-registry/).

Once the image is on a registry, you can run the same container on another location.

### Containers - Run component

Containers are created from an image. These containers hold everything needed for your apps to run. These containers can be run/started/stopped/removed/...

It is possible to turn a container into an image by using the docker commit command.

#### What are those containers?

* technically `~chroot` on steroids
* a container is a set of processes (running on top of the common kernel)
* isolated from the rest of the machine
* using *namespaces* to have private view of the system (network interfaces, PID tree, mount points… )
* and *cgroups* to have metered/limited/reserved resources
* the default container format is called *libcontainer*. Docker also supports traditional Linux containers using LXC. In the future, Docker may support other container formats, for example, by integrating with BSD Jails or Solaris Zones.
* process isolation, network isolation, resource isolation
* logging: STDOUT, STDERR and STIN from the container are collected, logged, and available for analysis or trouble-shooting
* interactive shell: you can create a pseudo-tty and attach to STDIN to provide an interactive shell to your container

## Basic commands

Simple example:

* `docker run ubuntu:14.04 date`
	* `docker run` - means execute the run command
	* `ubuntu:14.04` - instantiate a container of Ubuntu version 14.04
	* `date` - is the command that our container will execute
*  `--name` – Docker automatically generates a name at random for each container. If you want to specify a particular container name in place of the automatically generated name, you use the `--name` flag.

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
* `docker run -t -i -p 8080:80 <yourname>/apache2 /bin/bash`
	* `docker run` - means execute the run command
	* `-t` - means that you want a tty to be applied
	* `-i` - means that you want to be able to interact with your container
	* `-p` - port mapping! host_port:container_port. Your website will be available at localhost:8080
	* `<yourname>/apache2` is a simple Apache2 image
	* `bin/bash` is the command that the container will execute
* `docker run -p 8080:80 -v /home/apache2/var/www/ <yourname>/apache2:latest /start.sh`
	* `-v` - stands for volume. In this case, a volume shared between the host and the container.
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

* `docker cp` - copies files or folders out of a container's filesystem.
* `docker export` - turns container filesystem into tarball.

### Entering a Docker Container

* `nsenter` allows you to run any command (e.g. a shell) inside a container that's already running another command (e.g. your database or web server). This allows you to see all mounted volumes, check on processes, log files etc. inside a running container.

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

A registry is a host - a server that stores repositories and provides an HTTP API for [managing the uploading and downloading of repositories](http://docs.docker.com/userguide/dockerrepos/).

Docker.io hosts its own [index](https://registry.hub.docker.com) to a central registry which contains a large number of repositories.

* `docker login` - to login to a registry.
* `docker search` - searches registry for image.
* `docker pull` - pulls an image from registry to local machine.
* `docker push` - pushes an image to the registry from local machine.

#### Shortcuts

* `docker rm -f $(docker ps -a -q) ; docker rmi $(docker images -q -a)` - removing all containers and images

## Dockerfile

There are two ways to create a Docker image. a) via the `docker commit command` or b) via the `docker build command` with a **Dockerfile** e.g. 

* `docker build -t="my_container_image"` - the `-t` flag allows us to specify a name for our new image, here my\_container\_image.
* `docker build -t="my_container_image:tag01" .`

If a file named **.dockerignore** exists in the root of the build context then it is interpreted as a newline-separated list of exclusion patterns. Much like a **.gitignore** file it excludes the listed files from being upload to the build context.

### Using the build cache for templating

```
FROM guttertec/ubuntu:14.04
MAINTAINER Axel Quack "mail@axelquack.de"

ENV REFRESHED_AT_2014-09-16
RUN apt-get --qq update
```

The **ENV** instruction sets environment variables in the image. In this case, the ENV instruction set an environment variable called REFRESHED_AT, showing when the template was last updated. Whenever you want to refresh the build you just change the date in the ENV instruction.

### Dockerfile Commands

* `MAINTAINER <author name>` - set an author field
* `RUN <command>` - execute a command in a shell or exec form. The RUN instruction adds a new layer on top of the newly created image.
* `ADD <src> <destination>` - copy files from one location to another using the ADD instruction. It takes two arguments <source> and <destination>. The destination is a path in the container. The source can be either a URL or a file in the context of the launch config.
* `CMD ["executable", "param1", "param2"]` or `CMD ["param1", "param2"]` or `CMD command param1 param2` - defaults for an executing container are provided using the CMD command. DockerFile allows usage of the CMD instruction only once. Multiple usage of CMD nullifies all previous CMD instructions.
* `EXPOSE <port>` - specify the port on which the container will be listening at runtime by running the EXPOSE instruction.
* `ENTRYPOINT ["executable", "param1", "param2"]` or `ENTRYPOINT command param1 param2` - configure a container to run as an executable, which means a specific application can be set as default and run every time a container is created using the image. This also means that the image will be used only to run and target the specific application each time it is called.
* `ENV` - The ENV command is used to set the environment variables (one or more). These variables consist of “key = value” pairs which can be accessed within the container by scripts and applications alike. This functionality of docker offers an enormous amount of flexibility for running programs.
* `FROM` - defines the base image to use to start the build process.
* `USER` - the USER directive is used to set the UID (or username) which is to run the container based on the image being built.
	* `USER nginx`, `USER user`, `USER user:group`, `USER uid`, `USER uid:gid`, `USER user:gid`, `USER uid:group`
* `VOLUME` - the VOLUME command is used to enable access from your container to a directory on the host machine (i.e. mounting it).
* `WORKDIR` - the WORKDIR directive is used to set where the command defined with CMD is to be executed.
* `ONBUILD` - the ONBUILD instruction adds triggers to images.

## Working with Docker Hub

* `docker login` - login to your Docker Hub account. Your authentication credentials will be stored in the .dockercfg authentication file in your home directory.

### Deployments

#### Automated Builds

1. Create a [Docker Hub](https://hub.docker.com) account and login.
2. Link your GitHub or BitBucket account through the ["Link Accounts"](https://registry.hub.docker.com/account/accounts/) menu.
3. [Configure an Automated Build](https://registry.hub.docker.com/builds/).
4. Pick a GitHub or BitBucket project that has a `Dockerfile` that you want to build.
5. Pick the branch you want to build (the default is the `master` branch).
6. Give the "Automated Build" a name.
7. Assign an optional Docker tag to the Build.
8. Specify where the `Dockerfile` is located. The default is `/`.

Once the Automated Build is configured it will automatically trigger a build and, in a few minutes, you should see your new Automated Build on the [Docker Hub](https://hub.docker.com) Registry. It will stay in sync with your GitHub and BitBucket repository until you deactivate the Automated Build.

If you want to see the status of your [Automated Builds](https://registry.hub.docker.com/builds/), you can go to your Automated Builds page on the Docker Hub, and it will show you the status of your builds and their build history.

#### AWS

* Elastic Beanstalk
	* [Deploying AWS Elastic Beanstalk Applications from Docker Containers](http://docs.aws.amazon.com/elasticbeanstalk/latest/dg/create_deploy_docker.html)
* EC2
	* [Docker on AWS EC2](https://docs.docker.com/installation/amazon/)

## Run your own Docker registry

* Github: [docker/docker-registry](https://github.com/docker/docker-registry)
* [Docker Registry or How to Run your own Private Docker Image Repository](https://blog.codecentric.de/en/2014/02/docker-registry-run-private-docker-image-repository/)
* Github: [lukaspustina/docker-registry-demo](https://github.com/lukaspustina/docker-registry-demo) – Show how to use a private Docker image repository / registry.
* **commercial alternative** [Quay](http://www.quay.io) (bought by CoreOS)

## Docker installation (OS X)

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
	# docker will be automatically too, since it is a boot2docker dependency

#### Share folders with boot2docker

Usually you can not use *Shared Folders* with boot2docker outside of the VM. Though there are still a few workarounds…

* [dduportal / boot2docker](https://vagrantcloud.com/dduportal/boot2docker) - this a box for running boot2docker with a virtual box shared folder capability. Usage : `vagrant init dduportal/boot2docker && vagrant up`
* through containers…
	* access via NFS: `docker pull cpuguy83/nfs-server` and then `docker run -d --name nfs --privileged cpuguy83/nfs-server /path/to/share`
	* access via Samba `docker pull svendowideit/samba` and then `docker run svendowideit/samba data`

Share between containers is surely [possible](https://docs.docker.com/userguide/dockervolumes/).

### Option 2: Install Kitematic

* [Kitematic](https://kitematic.com)

### Option 3: Install CoreOS with Vagrant

* I actually try to document my learnings at: [CoreOS Linux for Massive Server Deployment](http://research.axelquack.de/virtualization/2014/09/04/coreos.html)

### Other installation methods

* [Running Docker with EC2](https://docs.docker.com/installation/amazon/)

## Docker user interfaces

* [Shipyard](http://shipyard-project.com) gives you the ability to manage Docker resources, including containers, images, hosts, and more from a single management interface.
	* [Manage docker hosts with shipyard](http://serverascode.com/2014/05/25/docker-shipyard-multihost.html)
* [DockerUI](https://github.com/crosbymichael/dockerui) is a web interface that allows you to interact with the Docker Remote API. It is written in JavaScript using the AngularJS framework.
* [maDocker](https://github.com/izifortune/maDocker) is a Web UI written in NodeJS and Backbone

## Docker orchestration (untested)

* **[Fig](http://www.fig.sh)** is an open source tool developed by the Orchard team and then acquired by Docker, Inc..
	* Video: [Orchestrating Docker containers in production using Fig](https://www.youtube.com/watch?v=SEtRg8siQWw)
* **[Consul](http://www.consul.io)** by Hashicorp (Vagrant etc.) is a distributed, highly available service discovery tool. It allows services to register themselves with Consul and share that registration information in a highly-available and distributed manner. It is also interesting because it provides both a DNS-based query interface and a HTTP-based API to query the information. The choice of interfaces, especially the DNS-based interface, allows you to easily drop Consul into your existing environment.
* **[Apache Mesos](http://mesos.apache.org)** is a highly-available cluster management tool. Not specifically designed to work with Docker it instead has an interface, [Deimos](https://github.com/mesosphere/deimos), to allow you to use Docker container with Mesos.
* Github: **[spotify/helios](https://github.com/spotify/helios)** is a Docker orchestration patform for deploying and managing containers across an entire fleet. It creates a "job" abstraction that you can deploy to one or more Helios hosts running Docker.
* **[fleet & etcd](https://coreos.com/using-coreos/systemd/)** are released by the CoreOS team. Fleet is a cluster management tool and etcd is highly-available key value store for shared configuration and service discovery. Fleet combines systemd and etcd to provide cluster management and scheduling for Docker containers. Think of it as an extension of systemd that operates at the cluster level instead of the machine level.
	* Video: [Automating Service Orchestration with Docker and CoreOS](https://www.openstack.org/summit/openstack-summit-atlanta-2014/session-videos/presentation/automating-service-orchestration-with-docker-and-coreos)
* Github: [GoogleCloudPlatform/kubernetes](https://github.com/GoogleCloudPlatform/kubernetes). **Kubernetes** is a container cluster management tool open sourced by Google. It allows you to deploy and scale applications using Docker across multiple hosts. Kubernetes is primarily targeted at applications comprised of multiple containers, such as elastic, distributed micro-services.
	* [Running Kubernetes Example on CoreOS, Part 1](https://coreos.com/blog/running-kubernetes-example-on-CoreOS-part-1/)
	* [Running Kubernetes Example on CoreOS, Part 2](https://coreos.com/blog/running-kubernetes-example-on-CoreOS-part-2/)
	* [Kubernetes and Vagrant](https://github.com/GoogleCloudPlatform/kubernetes/blob/master/docs/getting-started-guides/vagrant.md)
	* Video: [Google I/O 2014 - Containerizing the Cloud with Docker on Google Cloud Platform](https://www.youtube.com/watch?v=tsk0pWf4ipw)
	* Github: [Azure/azure-kubernetes-visualizer](https://github.com/Azure/azure-kubernetes-visualizer) by Microsoft
* Github: **[newrelic/centurion](https://github.com/newrelic/centurion)** is focussed on being a Docker-based deployment tool open sourced by the New Relic team. Centurion takes containers from a Docker registry and runs them on a fleet of hosts with the correct environment variables, host volume mappings, and port mappings. It is designed to help you do continuous deployment with Docker.
* Github: **[libswarm](https://github.com/docker/libswarm)** is more of a library or toolkit and is designed to help you compose network services. It provides standard interfaces for connecting services across distributed systems. It has got some initial, Docker-focussed services, but is building a library of services to allow you to integrate a variety of other services, including many of the ones mentioned before.

### other

* [Serf](http://www.serfdom.io)
* [Flynn](https://flynn.io)
* Github: [signalfuse/maestro-ng](https://github.com/signalfuse/maestro-ng)
* [Deis](http://deis.io), builds on Docker and CoreOS
* Github: [progrium/dokku](https://github.com/progrium/dokku)
* [decking](http://decking.io)
* Github: [mesosphere/marathon](https://github.com/mesosphere/marathon)
* [tutum](https://www.tutum.co) (Webservice)
* Github: [ClusterHQ/flocker](https://github.com/ClusterHQ/flocker)

## Docker for Continuous Integration

* [Jenkins.CI](http://jenkins-ci.org)
* **alternatives**
	* [Strider](http://stridercd.com). Open Source Continuous Integration & Deployment Server.
	* [Drone.io](http://www.drone.io) is a SAAS continuous integration platform that connects to GitHub, Bitbucket and Google Code repositories written in a wide variety of languages, including Python, Node.js, Ruby, Go, and numerous others. It runs the test suites of repositories added to it inside a Docker container.
	* [Shippable]() is a free, hosted continuous integration and deployment service for GitHub and Bitbucket. Docker is natively supported.
	* [Wercker](http://wercker.com)
	* [Shippable](http://www.shippable.com)
	* [Codeship](https://www.codeship.io)
	* [go Continuous Delivery](http://www.go.cd)

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

### Interesting…

#### … resources

* [Docker homepage](https://www.docker.com)
* [Docker hub](https://hub.docker.com)
* [Docker blog](http://blog.docker.com)
* [Docker documentation](http://docs.docker.com)
* [Docker Forge](https://github.com/dockerforge)

#### … articles

* [Docker security I: SELinux](http://opensource.com/business/14/7/docker-security-selinux)
* Slideshare: [LXC, Docker, security: is it safe to run applications in Linux Containers?](http://de.slideshare.net/jpetazzo/is-it-safe-to-run-applications-in-linux-containers)
* [Securing Docker’s Future with SELinux and the Open Source Way](https://www.openshift.com/blogs/securing-docker’s-future-with-selinux-and-the-open-source-way)
* [An update on container support on Google Cloud Platform](http://googlecloudplatform.blogspot.de/2014/06/an-update-on-container-support-on-google-cloud-platform.html)
* Video: [Be a happier developer with Docker: Tricks of the trade Nicola Paolucci (Atlassian)](https://www.youtube.com/watch?v=XCVOxht34Hs&feature=youtu.be) **Done**

#### … courses

* [CloudAcademy: Getting started with Docker](https://cloudacademy.com/cloud-computing/courses/getting-started-with-docker/)

## Snippets unsorted

Some things I found as interesting but I did not manage to sort right now.

* `VBoxManage modifyvm "boot2docker-vm" --natpf1 "tcp-port4000,tcp,,4000,,4000"`
* .dockerignore - https://github.com/docker/docker/blob/master/.dockerignore

## Open questions

These are still some things I have to learn about… (this is more or less a reminder to myself)

* How does **nsenter** work?