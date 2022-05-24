# What are microservices?

Microservices are an architectural and organizational approach to software development where software is composed of small independent services that communicate over well-defined APIs. These services are owned by small, self-contained teams.

Microservices architectures make applications easier to scale and faster to develop, enabling innovation and accelerating time-to-market for new features.

# Monolithic vs. Microservices Architecture

With monolithic architectures, all processes are tightly coupled and run as a single service. This means that if one process of the application experiences a spike in demand, the entire architecture must be scaled. Adding or improving a monolithic application’s features becomes more complex as the code base grows. This complexity limits experimentation and makes it difficult to implement new ideas. Monolithic architectures add risk for application availability because many dependent and tightly coupled processes increase the impact of a single process failure.

With a microservices architecture, an application is built as independent components that run each application process as a service. These services communicate via a well-defined interface using lightweight APIs. Services are built for business capabilities and each service performs a single function. Because they are independently run, each service can be updated, deployed, and scaled to meet demand for specific functions of an application.

### Diagram Showing Monolithic Application Being Broken Down into Microservices
![](https://i.imgur.com/WfexM5J.png)

# Characteristics of Microservices

## Autonomous 

Each component service in a microservices architecture can be developed, deployed, operated, and scaled without affecting the functioning of other services. Services do not need to share any of their code or implementation with other services. Any communication between individual components happens via well-defined APIs.

## Specialized

Each service is designed for a set of capabilities and focuses on solving a specific problem. If developers contribute more code to a service over time and the service becomes complex, it can be broken into smaller services.

# Benefits of Microservices 

## Flexible Scaling

Microservices allow each service to be independently scaled to meet demand for the application feature it supports. This enables teams to right-size infrastructure needs, accurately measure the cost of a feature, and maintain availability if a service experiences a spike in demand.

## Agility 

Microservices foster an organization of small, independent teams that take ownership of their services. Teams act within a small and well understood context, and are empowered to work more independently and more quickly. This shortens development cycle times. You benefit significantly from the aggregate throughput of the organization.

## Easy Deployment

Microservices enable continuous integration and continuous delivery, making it easy to try out new ideas and to roll back if something doesn’t work. The low cost of failure enables experimentation, makes it easier to update code, and accelerates time-to-market for new features.

## Reusable Code

Dividing software into small, well-defined modules enables teams to use functions for multiple purposes. A service written for a certain function can be used as a building block for another feature. This allows an application to bootstrap off itself, as developers can create new capabilities without writing code from scratch.

## Resilience

Service independence increases an application’s resistance to failure. In a monolithic architecture, if a single component fails, it can cause the entire application to fail. With microservices, applications handle total service failure by degrading functionality and not crashing the entire application.

# Disadvantages of Microservices

## Communication Issues

There is a high chance of failure during communication between different services - especially if there are a lot of existing services all communicating with one another.

## Complex

Microservices has all the associated complexities of the distributed system. It will be difficult to manage a large number of services. It may also be difficult to carry out testing over such a distributed system.

# Use Case

Think about a school. Originally, the number of students won't change and there is no need to scale. In this case, a monolith architecture can be used. But if the school expands, buying new campuses and increasing its number of students, then microservices can be used as a way the business scale up (and/or scale out) to meet the new demands.

# What is Containerisation 

* Containerization is a form of virtualization where applications run in isolated user spaces, called containers, while using the same shared operating system (OS). A container is essentially a fully packaged and portable computing environment.

* Everything an application needs to run (its libraries, configuration files, and dependencies) is encapsulated and isolated in its container. The container itself is abstracted away from the host OS, with only limited access to underlying resources—much like a lightweight virtual machine (VM). 

* With containerization, there’s less overhead during startup and no need to set up a separate guest OS for each application since they all share the same OS kernel. Because of this high efficiency, containerization is commonly used for packaging up the many individual microservices that make up modern apps.

# Containerisation vs Virtualisation 

### Overview
Virtualization and containerization are the two most frequently used mechanisms to host applications in a computer system. Virtualization uses the notion of a virtual machine as the fundamental unit. Containerization, on the other hand, uses the concept of a container.

### Containerisation
For example, a Docker container is a lightweight, standalone, executable package of software that includes everything needed to run an application: code, runtime, system tools, system libraries and settings.

### Differences
The key differentiator between containers and virtual machines is that virtual machines virtualize an entire machine down to the hardware layers and containers only virtualize software layers above the operating system level.

![](https://i.imgur.com/a6LUSnm.png)

- With docker, integration is easier (it does not care about the OS).

- Faster set up with containerisation.

- Containerisation takes up less storage.

- Docker shares the resources from the OS, and vagrant takes the resources.

# What is Docker

Docker is a set of platform as a service products that use OS-level virtualization to deliver software in packages called containers.

## How does it work?

Docker provides an API for interacting with the Docker daemon (a daemon is a computer program that runs as a background process, rather than being under the direct control of an interactive user). 

When you try to run a container, Docker will first try to check your local machine for the image. If it is not there, it will fetch the appropriate image from the registry (docker hub) using an API.

![](https://i.imgur.com/Li9yyDS.png)

## Difference between image and container?

Images are immutable. When we want to use images, we use the docker run command and this will create a container from the image.

## Docker Container Lifecycle

![](https://i.imgur.com/Q1wBPp4.png)

* Created: A container that has been created but not started. The container gets created from an image.

* Running: A container running with all its processes

* Paused: A container whose processes have been paused

* Stopped: A container whose processes have been stopped

* Deleted: A container in a dead state

### Docker commands

* Windows users should use `alias docker="winpty docker"` for the below commands to work.

* `docker run hello-world`: This first looks locally. Then it looks on the registry (on docker hub). It then displays the message if it finds it. The command is case sensitive.

* `docker images`: lists all the local images

* `docker run -d -p 80:80 nginx`: this will run the image, and the 80:80 is an example of port mapping. -d stands for detached - if there is an error, kill the container and run this command without -d to see the logs.

* `docker ps -a`: Lists all the running containers.

* `docker exec -it idhereok bash`: The exec command is used to interact with already running containers on the Docker host. It allows you to start a session within the default directory of the container.

* `docker stop containeridhere`: Stops a running container(it does save changes).

* `docker rm containeridhere -f`: Completely removes a container.

* `docker image rm`: Removes an image.

* `docker cp ./index.html 8c913389dc59:/usr/share/nginx/html/`: Example of copying a file from the localhost to the container.

* `docker commit containerid samuelwalters/test:version2`: Making a commit with docker.

* `docker push samuelwalters/test:version2`: Making a push with docker.

* `docker run -d -p 80:80 samuelwalters/test:version2`: Running a container. If it does not exist locally, this will pull the image from the registry on docker hub (where my repository is).

* `docker logs containerid`: useful for debugging.

* `nano Dockerfile`. 

* `docker build -t samuelwalters/eng110_sam_nginx:v2 .`.

* Create a file called `Dockerfile` (it is case sensitive). Look at the following lines of code that can be placed inside this:

```docker
# Create a docker file to build a customised docker image
# Choose a base image
FROM nginx

# Label the image
LABEL MAINTAINER=SWALTERS@SPARTAGLOBAL.COM

# Migrate/transfer/copy/move data from localhost to our image/container. 
COPY index.html /usr/share/nginx/html/

# Expose 80
EXPOSE 80

# Launch the app - run this command at the end
CMD ["nginx", "-g", "daemon off;"]
```

* Or run the app with these lines (place Dockerfile inside the app folder):

```docker
# select base image to build our own customised node app microservice

FROM node

# set working directory 
WORKDIR /usr/src/app

# install node_modules
ADD package.json /usr/src/app/package.json

COPY package*.json ./

RUN npm install -g npm@latest

RUN npm install express

# define the port
COPY . . 
# start the app with CMD

CMD ["node", "app.js"]
```

* Because the above image uses port 3000, use the command `docker run -d -p 80:3000 samuelwalters/app:v5` to run it. 