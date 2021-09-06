## **Lux Docker Playbook.**


**Docker** is a software platform for building applications based on containers small and lightweight execution environments that make shared use of the operating system kernel but otherwise run in isolation from one another. 

- Docker helps developers build lightweight and portable software containers that simplify application development, testing, and deployment. 
- Docker containers are minimalistic and enable portability.
- Docker containers enable composability.
- Docker containers ease orchestration and scaling.


### **Installation**

**1). Linux**

```bash
curl -sSL https://get.docker.com/ | sh
```

**2). Mac**

- Use this link to download the dmg.

https://download.docker.com/mac/stable/Docker.dmg

**3). Windows.**

- Use the msi installer:

https://download.docker.com/win/stable/InstallDocker.msi


### **Docker Registries & Repositories**

**Login to a Registry**

```bash
docker login
docker login localhost:8080
``` 
**Logout from a Registry**

```bash
docker logout
docker logout localhost:8080
```

**Searching an Image**

```bash
docker search nginx
```
**Pulling an Image**

```bash
docker pull nginx
```

**Pushing an Image** 

```bash
docker push eon01/nginx
```

Running Containers
Creating a Container
docker create -t -i eon01/infinite --name infinite
Running a Container
docker run -it --name infinite -d eon01/infinite
Renaming a Container
docker rename infinite infinity
Removing a Container
docker rm infinite
Updating a Container
docker update --cpu-shares 512 -m 300M infinite
Starting & Stopping Containers
Starting
docker start nginx
Stopping
docker stop nginx
Restarting
docker restart nginx
Pausing
docker pause nginx
Unpausing
docker unpause nginx
Blocking a Container
docker wait nginx
Sending a SIGKILL
docker kill nginx
Connecting to an Existing Container
docker attach nginx
Getting Information about Containers
Running Containers
docker ps
docker ps -a
Container Logs
docker logs infinite
Inspecting Containers
docker inspect infinite
docker inspect --format '{{ .NetworkSettings.IPAddress }}' $(docker ps -q)
Containers Events
docker events infinite
Public Ports
docker port infinite
Running Processes
docker top infinite
Container Resource Usage
docker stats infinite
Inspecting Changes to Files or Directories on a Container’s Filesystem
docker diff infinite
Manipulating Images
Listing Images
docker images
Building Images
docker build .
docker build github.com/creack/docker-firefox
docker build - < Dockerfile
docker build - < context.tar.gz
docker build -t eon/infinite .
docker build -f myOtherDockerfile .
curl example.com/remote/Dockerfile | docker build -f - .
Removing an Image
docker rmi nginx
Loading a Tarred Repository from a File or the Standard Input Stream
docker load < ubuntu.tar.gz
docker load --input ubuntu.tar
Save an Image to a Tar Archive
docker save busybox > ubuntu.tar
Showing the History of an Image
docker history
Creating an Image Fron a Container
docker commit nginx
Tagging an Image
docker tag nginx eon01/nginx
Pushing an Image
docker push eon01/nginx
Networking
Creating Networks
docker network create -d overlay MyOverlayNetwork
docker network create -d bridge MyBridgeNetwork
docker network create -d overlay \
  --subnet=192.168.0.0/16 \
  --subnet=192.170.0.0/16 \
  --gateway=192.168.0.100 \
  --gateway=192.170.0.100 \
  --ip-range=192.168.1.0/24 \
  --aux-address="my-router=192.168.1.5" --aux-address="my-switch=192.168.1.6" \
  --aux-address="my-printer=192.170.1.5" --aux-address="my-nas=192.170.1.6" \
  MyOverlayNetwork


**Writing Your First Dockerfile.** 

Dockerfile is the text file that will contain the directives on how to build your docker image. Below are some Dockerfile instructions that you should know:

```docker
FROM — set the base image
RUN — execute a command in the container
COPY — supports the basic copying of local files into the container
ENV — set environment variable
WORKDIR — set the working directory
ENTRYPOINT — set the image’s main command, allowing that image to be run as though it was that command
VOLUME — create mount-point for a volume
CMD — set executable for container
```
For example, let’s see what a Dockerfile for a Flask application could look like:

FROM golang:1.11-alpine

WORKDIR /go/src/app
COPY . .

RUN go get -d -v ./...
RUN go install -v ./...

CMD ["app"]


Be sure to always indicate a specific version of the base image you would like to use because you never know when the ‘Latest’ image will be changed.

You can then build and run the Docker image:

```
 docker build -t myapp
```

This command will create an image tagged myapp from your Dockerfile

```bash
docker run -it --name my-running-app myapp 
```

With this, the container/image is production ready.


Docker is a strong tool for creating and running applications both locally and in production. Numerous CI/CD tools like Jenkins, TravisCI, CircleCI, etc. are now fully supported and integrated with Docker, which makes your changes from environment to environment very easy. This tutorial has just scratched the basic part of the Docker world. Below are some a few resources to help get you out.


Play with Docker, this is an online playground for Docker. It will allow you to practice any of the Docker commands we went over, without having to install anything onto your machine. The best part is it’s free and easy to use.
