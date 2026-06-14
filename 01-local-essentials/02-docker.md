# Docker: Packaging and Isolating Workloads

## Why We Use It at Federated Engineers

At `Federated Engineers`, we run the vast majority of our production workloads on container orchestration platforms like **Amazon EKS (Kubernetes)** and **Amazon ECS**. 

Before your code ever reaches the AWS cloud, it has to be containerized. Docker allows us to bundle our application code, runtime, system tools, and libraries into a single immutable package called an **Image**. This guarantees that the exact same code you test on your laptop behaves identically when deployed to a cluster of hundreds of servers in AWS. 

Mastering Docker locally, specifically how containers build, store data and talk to each other over networks is an absolute prerequisite to managing cloud architecture.

---

## Anatomy of a Dockerfile

A `Dockerfile` is a text document containing the step-by-step instructions Docker reads to assemble your container image. You must be thoroughly comfortable with these major instructions:

* **`FROM`**: Defines the base image (e.g., `FROM python:3.11-slim` or `FROM node:20-alpine`). Every Dockerfile must start with this.

* **`WORKDIR`**: Sets the working directory *inside* the container for any subsequent instructions. Think of it as a terminal `cd` command.

* **`COPY`**: Copies files or directories from your local host machine into the container's filesystem.

* **`RUN`**: Executes commands *during the build process* to install dependencies (e.g., `RUN pip install -r requirements.txt` or `RUN apt-get update`).

* **`ENV`**: Sets environment variables that persist inside the container at runtime.

* **`EXPOSE`**: Documentational instruction telling Docker which port the container listens on at runtime (e.g., `EXPOSE 8080`).

* **`CMD`**: The default command that executes *only when the container starts up*. There can only be one `CMD` per Dockerfile.

---

## Packaging & Pushing: Shifting from Docker Hub to AWS ECR

An image built on your machine is isolated until you push it to a **Container Registry**. In this module, you will practice pushing to **Docker Hub**, which acts as our conceptual stepping stone. 

When you move to our production repositories, you will use the exact same lifecycle commands to push images to **Amazon ECR (Elastic Container Registry)**:


## Deep Dive: Networks and Volumes

To build resilient multi-container platforms, you must understand how Docker handles state and communication:

### Docker Volumes (Data Persistence)

Containers are ephemeral, if a container is deleted, any data written inside its isolated filesystem vanishes. We use Docker Volumes to mount a directory from the host machine into the container. This ensures that database records or application logs persist safely even if the container crashes or restarts.

### Docker Networks (Container-to-Container Communication)

Docker provides an embedded DNS server for containers. When containers are attached to the same custom bridge network,
they don't need to know each other's IP addresses; they can communicate securely using just their Container
Names as hostnames.


## Fast-Track Resources

### Curated Videos

📺 [Docker crash course](https://www.youtube.com/watch?v=3c-iBn73dDE) 

📺 [Docker Storage & Volumes Explained Simply](https://www.youtube.com/watch?v=ZAPX21TMkkQ) : Learn how to keep your data from disappearing.

📺 [Docker Networking Deep Dive](https://www.youtube.com/watch?v=OU6xOM0SE4o) : Crucial for understanding how multiple containers talk to each other.


### Official Documentation

- [Official Dockerfile Reference Manual](https://docs.docker.com/reference/dockerfile/)

- [Docker Engine Networking Overview](https://docs.docker.com/engine/network/)
