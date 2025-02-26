# Docker-Course (Apr 2023)

**Resources**:
- https://www.youtube.com/watch?v=RqTEHSBrYFw
- https://courses.devopsdirective.com/docker-beginner-to-pro/lessons/00-introduction/01-main
- https://github.com/sidpalas/devops-directive-docker-course

---

# Intro

## Demo Application

It will be a minimal 3-tier web application with:
- a React front-end
- 2 API implementations:
  - Node.js
  - Golang
- a PostgreSQL database

And it will be deployed via **Docker Swarm**, the container orchestrator built into Docker.  

---

# Part 1 - History and Motivation

## Motivation for Containers

Containers aim to address two main aspects of the software development lifecycle:
- Development
- Deployment

Containers make both development and deployment processes simpler and more reliable.  
They help ensure that the local environment is as close as possible to the production environment, reducing the chances of errors when translating from local to production systems.

### Containers for Development

Historically, setting up a development environment involved complex and error-prone processes.  
Docker simplifies this by allowing developers to run a single command, `docker-compose up`, and have a compatible environment across Windows, Mac, and Linux systems.  

### Containers for Deployment

Deploying applications used to involve several steps, such as creating a server, configuring dependencies, and copying the application code.  
Containers introduce a single standardized package, simplifying deployment by only requiring a container runtime and the container image.

## What is a container?

### Container vs Container image

A Docker container **image** is a lightweight, standalone, executable package of software that includes everything needed to run an application.  
This package contains:
- underlying OS dependencies
- Runtime dependencies 
- Libraries
- The application code

A container is like a class in Object-Oriented Programming, while a container is an instantiation of that class.  
A container image allows us to create one or more standardized copies that are the same every time.  

### The Open Container Initiative (OCI)

The OCI is an industry collaboration that aims to create open standards for container formats.  
It was founded by companies like Docker, Google, VMware, Microsoft, Dell, IBM, and Oracle.  

The OCI defines 3 primary specifications:
- **Image specification**: defines the image's metadata and format, including a serializable file system.
- **Runtime specification**: describes how to run a container using an image adhering to the Image specification.
- **Distribution specification**: outlines how images should be distributed, such as through registries, pushing, and pulling images.

Docker is a specific implementation of the OCI standard.  

## History of Virtualization





