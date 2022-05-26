### Links

* [Microservices](#What-are-microservices?)

* [Kubernetes](#Kubernetes-Open-Source-Container-Orchestration-Tool)

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

Microservices allow each service to be independently scaled to meet demand for the application feature it supports (instead of scaling up the application as a whole - as with monolithic architectures). This enables teams to right-size infrastructure needs, accurately measure the cost of a feature, and maintain availability if a service experiences a spike in demand.

## Easier Testing (via Fault Isolation)

You can test the various components and isolate any problems quickly which allows you to give a more prompt solution.

## Agility 

Microservices foster an organization of small, independent teams that take ownership of their services. Teams act within a small and well understood context, and are empowered to work more independently and more quickly. This shortens development cycle times. You benefit significantly from the aggregate throughput of the organization.

(Easy to divide the workload as different groups of people can work on different services - more ends up getting done which shortens the product development lifecycle.)

## Easy Deployment

Microservices enable continuous integration and continuous delivery, making it easy to try out new ideas and to roll back if something doesn’t work. The low cost of failure enables experimentation, makes it easier to update code, and accelerates time-to-market for new features.

## Reusable Code

Dividing software into small, well-defined modules enables teams to use functions for multiple purposes. A service written for a certain function can be used as a building block for another feature. This allows an application to bootstrap off itself, as developers can create new capabilities without writing code from scratch.

## Resilience

Service independence increases an application’s resistance to failure. In a monolithic architecture, if a single component fails, it can cause the entire application to fail. With microservices, applications handle total service failure by degrading functionality and not crashing the entire application.

(The system won't crash just because one component stops working - for example, if there were a bug in the database, there would just be an error message when another service sends a request to it.)

# Disadvantages of Microservices

## Communication Issues

There is a high chance of failure during communication between different services - especially if there are a lot of existing services all communicating with one another.

## Complex

Microservices has all the associated complexities of the distributed system. It will be difficult to manage a large number of services. 

(Need to know how APIs work - need lots of experience under your belt about how different services can interact with one another.)

# Use Case

Think about a school. Originally, the number of students won't change and there is no need to scale. In this case, a monolith architecture can be used. But if the school expands, buying new campuses and increasing its number of students, then microservices can be used as a way the business scale up (and/or scale out) to meet the new demands.

# What is Containerisation 

* Containerization is a form of virtualization where applications run in isolated user spaces, called containers, while using the same shared operating system (OS). A container is essentially a fully packaged and portable computing environment.

* Everything an application needs to run (its libraries, configuration files, and dependencies) is encapsulated and isolated in its container. The container itself is abstracted away from the host OS, with only limited access to underlying resources—much like a lightweight virtual machine (VM). 

* With containerization, there’s less overhead during startup and no need to set up a separate guest OS for each application since they all share the same OS kernel. Because of this high efficiency, containerization is commonly used for packaging up the many individual microservices that make up modern apps.

# Containerisation vs Virtualisation 

* Containerisation - resources shared directly with the host which allows you to run a lot of docker containers, whereas you would only be able to run a few VMs. VMs has to quarantine off a set amount of resources: harddrive space, memory, and processing power, emulate hardware, and boot an entire OS. Then the VM communicates with the host computer through a translator application on the host's OS called a hypervisor. But docker communicates natively with the system kernel, bypassing the middleman on linux machines (and on windows).

Docker also uses less disk space as it uses a layered file system. If you have multiple docker images using the same base image, docker will only keep a single copy of the files needed and share it with each container. 

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

## Why Docker?

After more than a decade in use, Docker remains the de facto container standard because of its ability to integrate with a broad array of tools and platforms, such as Kubernetes. 

Docker features a virtual production environment known as a container that can be easily shared with others.

Compresses images easier, reducing their storage capacity by up to 4 times. (1GB to 250MB).

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
FROM node
#Set working directory
WORKDIR /usr/src/app
# Add packages
ADD package.json /usr/src/app/package.json
# Copy packages
COPY package*.json ./
# Install npm
RUN npm install -g npm@latest
# Run npm
RUN npm install express
# Copy everything from current working directory over to container's current working directory
COPY . . 
# Allow port 300
EXPOSE 3000
# Start the app
CMD ["node", "app.js"]
```

* Because the above image uses port 3000, use the command `docker run -d -p 80:3000 samuelwalters/app:v5` to run it. 

* Even try building from the below docker as well which is compressed (because it uses node:alpine)!

```docker
FROM node:alpine
WORKDIR /usr/src/app

#Set working directory
WORKDIR /usr/src/app
# Add packages
ADD package.json /usr/src/app/package.json
# Copy packages
COPY package*.json ./
# Install npm
RUN npm install -g npm@latest
# Run npm
RUN npm install express
# Copy everything from current working directory over to container's current working directory
COPY . . 
# Allow port 300
EXPOSE 3000
# Start the app
CMD ["node", "app.js"]
```

### Setting app up with mongodb

> 1. `docker run --name db -d mongo:latest`.

> 2. Add this to `set_up.yml`:

```yaml
version: '5'

services:

  db:
    image: mongo
    restart: always
    build: .
    ports:
      - "27017:27017"
    volumes:
      - 'db:/data/db'
    command: mongod --bind_ip 0.0.0.0

  app:
    build: ./eng110_dock/app # this is running the docker build command at this destination
    restart: always
    ports: 
      - "3000:3000"
    links:
      - db
    environment:
      - DB_HOST=mongodb://db:27017/posts
    depends_on:
      - mongo
volumes:
  db: 
```

* Run the command `docker-compose -f set_up.yml up -d`.

* To get the seeds to work, use the command `docker exec -it containerid node seeds/seed.js`. 

* Run this command to bring down the containers (and networks): `docker-compose -f set_up.yml down`.

### Miscellaneous commands

* `docker volume create eng110`.

* `docker volumne ls`.

* `docker history samuelwalters/app:v9`.

* `docker inspect samuelwalters/app:v9`. 

# Kubernetes - Open Source Container Orchestration Tool

Kubernetes, also known as K8s, is an open-source system for automating deployment, scaling, and management of containerized applications. It groups containers that make up an application into logical units for easy management and discovery.

## Kubernetes Benefits

### Self-healing
Kubernetes restarts containers that fail, replaces containers, kills containers that don't respond to your user-defined health check, and doesn't advertise them to clients until they are ready to serve.

### Load balancing and Service Discovery
Kubernetes can expose a container using the DNS name or using their own IP address. If traffic to a container is high, Kubernetes is able to load balance and distribute the network traffic so that the deployment is stable.

### Automated rollouts and rollbacks.
You can describe the desired state for your deployed containers using Kubernetes, and it can change the actual state to the desired state at a controlled rate. For example, you can automate Kubernetes to create new containers for your deployment, remove existing containers and adopt all their resources to the new container.

### Automatic bin packing

You provide Kubernetes with a cluster of nodes that it can use to run containerized tasks. You tell Kubernetes how much CPU and memory (RAM) each container needs. Kubernetes can fit containers onto your nodes to make the best use of your resources.

### Secret and Configuration Management
Kubernetes lets you store and manage sensitive information, such as passwords, OAuth tokens, and SSH keys. You can deploy and update secrets and application configuration without rebuilding your container images, and without exposing secrets in your stack configuration.

### Storage orchestration
Kubernetes allows you to automatically mount a storage system of your choice, such as local storages, public cloud providers, and more.

# Why Kubernetes?

Cloud is expensive, and businesses might need services running all the time.

## Use case

If there were three courses running, with 12-13 people each, then k8 won't have to be used as docker compose will be able to do the job. 

But if this was to scale to a million users, then k8 would need to be used. And yet docker compose isn't useless: it depends upon what the client's requirements are.

# Kubernetes Micro-Services

![](https://i.imgur.com/smnqTWu.png)

* Container: A container image is a ready-to-run software package, containing everything needed to run an application: the code and any runtime it requires, application and system libraries, and default values for any essential settings.

* Pod: Pods contain one or more containers, such as Docker containers. When a Pod runs multiple containers, the containers are managed as a single entity and share the Pod's resources. Generally, running multiple containers in a single Pod is an advanced use case. Pods also contain shared networking and storage resources for their containers:


    1. Network: Pods are automatically assigned unique IP addresses. Pod containers share the same network namespace, including IP address and network ports. Containers in a Pod communicate with each other inside the Pod on localhost.
    2. Storage: Pods can specify a set of shared storage volumes that can be shared among the containers.

* Service: To expose your app, you need a Service. A Service resource makes Pods accessible to other Pods or users outside the cluster. Without a Service, a Pod cannot be accessed at all. A Service forwards requests to a set of Pods. In this regard, a Service is akin to a load balancer.

### A Service forwarding requests to a set of Pods:

  ![](https://i.imgur.com/PiGyteu.png)

* Service Accounts: Kubernetes service accounts are Kubernetes resources, created and managed using the Kubernetes API, meant to be used by in-cluster Kubernetes-created entities, such as Pods, to authenticate to the Kubernetes API server or external services.

* Volume: A Kubernetes volume is a directory that contains data accessible to containers in a given Pod in the orchestration and scheduling platform.

* Persistent volume: A persistent volume is a volume plug-in that has a lifecycle independent of any individual pod that uses the persistent volume. For example, with regard to MongoDB, this storage must not be affected by whatever happens to the MongoDB Pod. If the MongoDB Pod is deleted, the storage will persist — if the MongoDB Pod is moved to another node, the storage will persist. (Persistent volume exists so storage can survive the shutdown of one or more containers.)

* A PersistentVolumeClaim (PVC) is a request for storage by a user. It is similar to a Pod. Pods consume node resources and PVCs consume PV resources. Pods can request specific levels of resources (CPU and Memory). Claims can request specific size and access modes (e.g., they can be mounted ReadWriteOnce, ReadOnlyMany or ReadWriteMany).

* ContainerPort: The ContainerPort defines the port on which the app can be reached.

* Namespace: Namespaces are essential objects for dividing and managing Kubernetes clusters. Kubernetes namespaces allow us to logically segregate and assign resources to individual users, teams or applications. Kubernetes Namespaces provide the basic building blocks for resource usage allowance, access control and isolation for applications, users or groups of users. By using Kubernetes Namespaces, you can increase resource efficiencies, as a single Kubernetes cluster can now be used for a diverse set of workloads.

* ConfigMaps: A ConfigMap is an API object used to store non-confidential data in key-value pairs. Pods can consume ConfigMaps as environment variables, command-line arguments, or as configuration files in a volume. This allows you to decouple environment-specific configurations from your container images so that your applications become easily portable.

## Kubernetes ReplicaSet

A ReplicaSet is a process that runs multiple instances of a Pod and keeps the specified number of Pods constant. Its purpose is to maintain the specified number of Pod instances running in a cluster at any given time to prevent users from losing access to their application when a Pod fails or is inaccessible.

What's great about ReplicaSets is you can make live changes to the .yml file, and the user won't notice anything as the application will still be running. For example, you can edit the number of replicas from 3 to 5 and the app will not go down. 

![](https://i.imgur.com/H57GFjz.png)

## Kubernetes Architecture Diagram

![](https://i.imgur.com/XjYxJvj.png)

## Kubernetes Architecture Diagram for Class Task

![](https://i.imgur.com/zaxjKzi.png)

#### Set up

> 1. Go to the `k8` folder.

> 2. Run the commands `kubectl create -f mongo.yml` and `kubectl create -f app-deploy.yml`. 

> 3. Run this command `kubectl exec podname node seeds/seed.js` to display posts on the /posts page.

> 4. Go to localhost (port 80) and check the /posts page.

### Kubernetes: Volume
At its core, a volume is a directory, possibly with some data in it, which is accessible to the containers in a pod.

#### Why is a volume necessary?
On-disk files in a container are ephemeral, which presents some problems for non-trivial applications when running in containers. One problem is the loss of files when a container crashes. The kubelet restarts the container but with a clean state. Persistent volumes can solve this problem as they exist beyond the lifetime of a pod. When a pod ceases to exist, Kubernetes destroys ephemeral volumes; however, Kubernetes does not destroy persistent volumes. For any kind of volume in a given pod, data is preserved across container restarts.

##### Difference between Persistent Volume (PV) and Persistent Volume Claim

![](https://www.portworx.com/wp-content/uploads/2018/02/media-20180208.png)

* A PersistentVolume (PV) is a piece of storage in the cluster that has been provisioned by an administrator. PVs are resources in the cluster just like a node is a cluster resource. PVs have a lifecycle independent of any individual Pod that uses the PV.

* A PersistentVolumeClaim (PVC) is a request for storage by a user. It is similar to a Pod. Pods consume node resources and PVCs consume PV resources. Claims can request specific size and access modes (e.g., they can be mounted ReadWriteOnce, ReadOnlyMany or ReadWriteMany). 

##### Bind PVC to PV

Only PVs of the requested class, ones with the same storageClassName as the PVC, can be bound to the PVC.

## Kubernetes Commands

* `kubectl cluster-info`: A useful way to tell if K8 is running properly.

* `kubectl`: a command line tool used to run commands against Kubernetes clusters.

* `kubectl delete deploy/pod/pvc/svc namehere`: Deletes the specified entity.

* `kubectl get`: List one or more resources. For example, you can use these commands:

  ```
  kubectl get namespace
  kubectl get rs
  kubectl get service
  kubectl get pvc
  kubectl get svc
  kubectl get deploy
  kubectl get all
  kubectl get pv
  ```

* `kubectl describe`: Display detailed state of one or more resources, including the uninitialized ones by default. For example, you could use these commands:

  ```
  kubectl describe svc
  kubectl describe deploy namehere
  ```

* `kubectl exec`: Execute a command against a container in a pod.

* `kubectl create -f app-deploy.yml`: Create one or more resources from a file.