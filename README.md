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

## Containers for Development

To simplify the development environment set up, we use containers that already **contain** all that we need to code, test & run our application.  
This way, we don't have to set up our dev environment every time we start using a new machine, which can be time consuming.  

We just build a Docker image once, then we run a Docker container from this image, and we log in to that container to start working.   
It's fast, it's repeatable, it's lightweight, it's scalable, and it's secure.

All we need is an host system that can run Docker...  

## Containers for Deployment

What is true for setting up a development environment is also true for deploying applications, or updating them.  
We just build an image containing all the things our application needs to run, we test it, and we run a container from it




@7/284
