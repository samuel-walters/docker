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

# Use Case

Think about a school. Originally, the number of students won't change and there is no need to scale. In this case, a monolith architecture can be used. But if the school expands, buying new campuses and increasing its number of students, then microservices can be used as a way to help scale up and match the new demands.

# Containerisation vs Virtualisation 

Virtualization and containerization are the two most frequently used mechanisms to host applications in a computer system. Virtualization uses the notion of a virtual machine as the fundamental unit. Containerization, on the other hand, uses the concept of a container.

### commands

docker run hello-world

first looks locally. Then look to registry (docker hub). Then display the message. It is case sensitive

docker images

lists all the local images

docker run -d -p 80:80 nginx --> This is port mapping. 

docker ps -a

docker images

alias docker="winpty docker"

docker exec -it idhereok bash

docker stop containeridhere (saves changes)

docker rm containeridhere -f (removes it completely)

docker cp ./index.html 8c913389dc59:/usr/share/nginx/html/