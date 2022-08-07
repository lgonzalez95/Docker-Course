# What is docker?
Docker is a tool designed to make it easier to create,
deploy, and run applications using containers.
Containers allow developers to package up an application,
with all of the parts it needs, such as libraries
and other dependecies, and ship it all out as one package.

# What is a docker container?
A container is a standard unit of software that packages 
up code and all its dependencies so the application runs 
quickly and reliably from one computing environment to another.
**An instance of an image is called a container, the virtual operating system itself**

## Namespace
The id or the name of the process for a given container.

## Cgroups
Control Groups (cgroups) are a feature of the Linux kernel that allow 
you to limit the access processes and containers have to system resources 
such as CPU, RAM, IOPS and network.

# What is a docker image?
A Docker container image is a lightweight, standalone, 
executable package of software that includes everything 
needed to run an application: code, runtime, system tools, 
system libraries and settings.

Images can exist without containers, whereas a container needs to run an 
image to exist. Therefore, containers are dependent on images and use them 
to construct a run-time environment and run an application.
**An image is produced after compiling a Dockerfile**


## Container vs VM
The key differentiator between containers and virtual machines is that virtual 
machines virtualize an **entire machine down to the hardware layers** and containers 
only virtualize software layers **above the operating system level**.

## Docker file
Plained text file where we define the instructions to create our images.

### Basic Docker File Format
FROM centos
RUN yum -y install httpd
CMD appachectl -DFOREGROUND

## Docker Host
The "house" of all the containers that we will create
It is created when we install docker in our machine.
The docker CLI interacts with the docker daemon through 
an API.

### If we try to create a container without an image, then docker will download the image automatically

## How to ignore files in the current context?
Create .dockerignore file and add all directories

## Docker Volume
Allow to persist the data after a container dies.
- Normal Volumes: We create a folder with the command docker volume create volumeName
- Bind Volumes: Mapping done from one docker host folder to container folder.
- Anonymous Volumes: Volumes with random numeric name, we don't specify any folder when creatig them

## Networks
If we don't specify the network, docker will link the container to the bridge default network
Default networks can't be deleted: bridge, host, none.
When we create networks by ourselves then we can ping the containers attached to it by their names.

## The host network
Allows to create a network as the network of the docker host is.
The new network inherits the attributes that the docker host has.

## The none network
The none network allows to have containers without networks.
If a container is created here, the container wouldn't have any network

## Docker compose
Allows to create multi container applications by
managing images, container, volumes and networks 
in one single yaml file.

# Docker best practices
### 1. One service per container
### 2. Build context should be small
### 3. Avoid unnecessary packages
### 4. Less layers
