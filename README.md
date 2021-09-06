## **Lux Academy Docker All Round .**


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

### **Running Containers**

**Creating a Container**

```bash
docker create -t -i mycont
```
**Running a Container**

```bash
>>>docker run -p 5000:5000 -t -i myapp  
```

**Renaming a Container**

```bash
docker rename myapp mybestapp 
```

Removing a Container

``bash
docker rm myappv
```

Updating a Container

```
docker update
```


**Writing Your First Dockerfile.** 

Dockerfile is the text file that will contain the directives on how to build your docker image. Below are some Dockerfile instructions that you should know:


- **FROM** — set the base image
- **RUN** — execute a command in the container
- **COPY** — supports the basic copying of local files into the container
- **ENV** — set environment variable
**WORKDIR** — set the working directory
**ENTRYPOINT** — set the image’s main command, allowing that image to be run as though it was that command
**VOLUME** — create mount-point for a volume
**CMD** — set executable for container

For example, let’s see what a Dockerfile for a Flask application could look like:

```dockerfile
FROM python:3.6

COPY . /src


COPY ./requirements.txt /src/requirements.txt

WORKDIR src

EXPOSE 5000

RUN pip install -r requirements.txt


CMD [ "python", "app.py" ]
```

Be sure to always indicate a specific version of the base image you would like to use because you never know when the ‘Latest’ image will be changed.

You can then build and run the Docker image:

```
 docker build -t myapp
```

This command will create an image tagged myapp from your Dockerfile

```bash
docker run -it myapp 
```

With this, the container/image is production ready.


Docker is a strong tool for creating and running applications both locally and in production. Numerous CI/CD tools like Jenkins, TravisCI, CircleCI, etc. are now fully supported and integrated with Docker, which makes your changes from environment to environment very easy. This tutorial has just scratched the basic part of the Docker world. Below are some a few resources to help get you out.


Play with Docker, this is an online playground for Docker. It will allow you to practice any of the Docker commands we went over, without having to install anything onto your machine. The best part is it’s free and easy to use.
