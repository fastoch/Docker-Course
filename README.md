# Docker-Course (Apr 2023)

**Resources**:
- https://www.youtube.com/watch?v=RqTEHSBrYFw
- https://courses.devopsdirective.com/docker-beginner-to-pro/lessons/00-introduction/01-main
- https://github.com/sidpalas/devops-directive-docker-course

---

# Intro

## Demo Application

The application we will develop will be a minimal 3-tier web application with:
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

### Bare metal

Before virtualization was invented, all programs ran directly on the host system.  
The terminology many people use for this is "bare metal".  

With a bare metal system, the operating system, binaries/libraries, and applications are installed and run directly onto the physical hardware.  

Direct access to the hardware can be useful for specific cases, but can lead to:
- hellish dependency conflicts
- low utilization efficiency
- large blast radius
- slow start up and shut down speed
- very slow provisioning & decommissioning

### Virtual Machines

Virtual machines use a system called a "hypervisor" that can carve up the host resources into multiple isolated virtual hardware configurations 
which you can then treat as their own systems (each with an OS, binaries/libraries, and applications).  

This helps improve upon some of the challenges presented by bare metal:
- no dependency conflicts
- better utilization efficiency
- small blast radius
- faster startup and shutdown
- faster provisioning and decommissioning

### Containers

Containers are similar to virtual machines in that they provide an isolated environment for installing and configuring binaries/libraries, 
but rather than virtualizing at the hardware layer, containers use native Linux features (cgroups + namespaces) to provide that isolation while 
still sharing the same kernel.  

This approach results in containers being more lightweight than virtual machines, but not providing the same level of isolation:  
- no dependency conflicts
- even better utilization efficiency
- small blast radius
- even faster startup and shutdown
- even faster provisioning and decommissioning

---

# Part 2 - Technology Overview

This chapter explores the 3 core Linux features that enable containers to function:
- cgroups
- namespaces
- union filesystems

## Linux Building Blocks

Cgroups and namespaces to provide resource constraints and application isolation respectively.  
Containers use a union filesystem that enables images to be built upon common layers, making building and sharing images fast and efficient.  

### Docker did not invent containers

For example, LXC containers (https://linuxcontainers.org/) was implemented in 2008, five years before Docker launched.   
That being said, Docker made huge strides in developer experience, which helped container technologies gain mass adoption.  

### Cgroups

Cgroups are a Linux kernel feature which allows processes to be organized into hierarchical groups whose usage of various types of resources can 
then be limited and monitored.  

By using cgroups, a container runtime is able to specify what a container should be able to use. For example:
- use up to xx% of CPU cycles (cpu.shares)
- use up to xxMB of memory (memory.limit_in_bytes)
- throttle reads to xxMB/s (blkio.throttle.read_bps_device)

### Namespaces 

A namespace wraps a global system resource in an abstraction that makes it appear to the processes within that namespace 
that they have their own isolated instance of the global resource.  

Changes to the global resource are visible to other processes that are members of the namespace, but are invisible to other processes.  

With namespaces, a container runtime is able to: 
- keep processes outside of the container invisible within the container
- map the user inside the container to a different user on the host
- Create separate views of system resources for each container, such as process IDs, network interfaces, and file systems
- Enable containers to run as root inside their namespace without actually being root on the host system, enhancing security
- Manage resource allocation and limit access to host resources, preventing containers from disrupting the host or other containers
- Provide a secure and stable environment by leveraging features of the host operating system to create isolated execution contexts

### Union filesystems

A union filesystem allows files and directories of separate filesystems, known as branches, to be transparently overlaid, forming a single coherent filesystem.   
Contents of directories which have the same path within the merged branches will be seen together in a single merged directory, within the new virtual filesystem.  

This approach allows for efficient use of space because common layers can be shared.  
For example, if multiple containers from the same image are created on a single host, the container runtime only has to allocate a thin overlay specific to each container, 
while the underlying image layers can be shared.  

More detail on understanding the implications of these filesystems on data persistence can be found in Part 4 - Using 3rd party containers.  

---

Docker provides a convenient user experience (UX) by packaging the underlying technologies (namespaces, cgroups, and union filesystems) into an easy-to-use desktop application.  
For a deeper exploration of these topics

---

## Docker application architecture

While Docker is often referred to as a container runtime, it's important to note that Docker itself is a complete platform built on top of lower-level components.  

The Docker stack consists of several parts:
- **Docker CLI** (docker-cli): The user interface for interacting with Docker.
- **Docker daemon** (containerd): A high-level daemon process that manages the container environment.
- **RunC**: The actual low-level container runtime responsible for creating and running containers1.


---

# Part 3 - Installation and Set Up

---

# Part 4 - Using 3rd Party Container Images

---

# Part 5 - Example Web Application

---

# Part 6 - Building Container Images

---

# Part 7 - Container Registries

---

# Part 8 - Running Containers

---

# Part 9 - Container Security

---

# Part 10 - Interacting with Docker Objects

---

# Part 11 - Development Workflow

---

# Part 12 - Deploying Containers

--- 

# Part 13 - Course Wrap Up



