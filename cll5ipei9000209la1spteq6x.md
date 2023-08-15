---
title: "Docker Important interview Questions"
datePublished: Thu Aug 10 2023 18:53:44 GMT+0000 (Coordinated Universal Time)
cuid: cll5ipei9000209la1spteq6x
slug: docker-important-interview-questions
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1691690700906/1627655a-d6d8-4aa3-a52b-acf850c4195f.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1691693613112/7282544f-b4b5-4c03-a73b-65017ba6a71e.png
tags: docker, docker-images, 90daysofdevops, 90daysofdevops-devops-projectdevelopment-nonitbackground-github-docker-cloudplatforms-ec2-aws-elasticbeanstalk-lambdafunctions-devopspipelines-terraform-jenkins-docker-devsecops-scm-git-gitlab-bitbucket-buildtools-griddle-maven-ant-msbuild-monitoringtools-prometheus-grafana-ansible-ai-chatgpt-valueaddition-realworldproblems, 90daysofdevopschallenge

---

1. What is the Difference between an Image, Container and Engine?
    
    * **Docker Images:** Docker images are lightweight, standalone, executable software packages that include everything needed to run a piece of software, such as the code, runtime, libraries, and system tools. Dockerfiles are used to generate images.
        
    * **Docker Containers:** A Docker container is an instance of a Docker image that is running. Containers isolate applications, ensuring that they run consistently across multiple environments. The Docker engine is the central component of Docker. It is made up of two parts: the Docker daemon, which manages images and containers, and the Docker client, which communicates with the daemon via the Docker API.
        
    * Go through this for a more detailed explanation [Know](https://phoenixnap.com/kb/docker-image-vs-container) More.
        
2. What is the Difference between the Docker command COPY vs ADD?
    
    * **COPY**: In a Dockerfile, the COPY command copies files and directories from the host machine to the container filesystem. It is simple and does not use any automatic extraction.
        
    * **ADD**: The ADD command copies files and directories as well, but it also has extra features like automatic tarball extraction and URL downloads. It can be used to copy remote files and extract compressed archives.
        
    * Go through this for more detailed explaination [know more](https://www.geeksforgeeks.org/difference-between-the-copy-and-add-commands-in-a-dockerfile/)
        
3. What is the Difference between the Docker command CMD vs RUN?
    
    * **RUN**: In a Dockerfile, the RUN command is used to execute commands during the image build process. It is commonly used to install software, configure dependencies, and configure the image.
        
    * **CMD**: The CMD command specifies the default command to run when a container is launched from an image. It specifies the container's primary process.
        
    * Go through this for more info [know more](https://www.geeksforgeeks.org/difference-between-run-vs-cmd-vs-entrypoint-docker-commands/)
        
4. How Will you reduce the size of the Docker image?
    
    * Select a light base image, such as Alpine Linux.
        
    * Reduce the number of layers by chaining and combining commands.
        
    * Create smaller final images by using multi-stage builds and copying only necessary artefacts.
        
    * After each build step, delete any temporary or unnecessary files.
        
    * To exclude unnecessary files from the build context, use a.dockerignore file.
        
    * For specific use cases, consider using alternative runtimes such as distroless images.You can also use slim and bullseye .
        
    * Here is more detailed explaination [know more](https://depot.dev/blog/how-to-reduce-your-docker-image-size)
        
5. Why and when to use Docker?
    
    * Why: Docker provides a consistent environment for applications, ensuring that they run consistently across development, testing, and production. It improves collaboration, speeds up deployment, and makes better use of resources.
        
    * When: Docker is useful for developing microservices, deploying complex applications, ensuring reproducibility, and optimising server usage through containerization.
        
6. Explain the Docker components and how they interact with each other.
    
    * Docker Daemon: The Docker Daemon is in charge of Docker container and image management. It listens for commands from the Docker API, processes them, and manages container lifecycles.
        
    * Docker Client: A command-line tool that communicates with the Docker daemon using the Docker API. Users can interact with containers and images.
        
    * Docker Images: Docker images are container templates. They are made up of layers and are used to make containers.
        
    * Docker Containers: Containers are instances of Docker images that are running. They encapsulate and isolate applications.
        
    * Docker Registry: The Docker registry is a repository for Docker images that allows users to share and distribute them.
        
    * Read this for more explaination [know more](https://geekflare.com/docker-architecture/) .
        
7. Explain the terminology: Docker Compose, Docker File, Docker Image, Docker Container?
    
    * Docker Compose is a tool for defining and running multi-container applications. It configures the application's services, networks, and volumes using a YAML file.
        
    * A Dockerfile is a script that contains instructions for creating a Docker image. It specifies the base image, adds files, configures environment variables, and does other things.
        
    * A Docker image is a packaged, executable software package that includes code, runtime, libraries, and dependencies.
        
    * Containers are made from images. A Docker container is a programmable instance of a Docker image. It isolates and consistently encapsulates the application and its dependencies.
        
8. In what real scenarios have you used Docker?
    
    * Docker was used to deploy individual microservices as containers, allowing for better scalability and maintainability of the application architecture.
        
    * CI/CD Pipelines: Docker was integrated into the CI/CD pipeline, allowing developers to build and test applications within containers to ensure consistency across stages.
        
    * Local Development: Using Docker to create consistent development environments, we were able to reduce "it works on my machine" issues while also improving collaboration.
        
    * Docker was used to easily scale applications by running multiple container instances across a cluster of machines. Isolating legacy applications within containers to encapsulate dependencies and reduce conflicts with the host system.
        
9. Docker vs Hypervisor?
    
    * Docker: Containerization is used by Docker to provide lightweight, isolated environments that share the host OS kernel. Containers are more efficient, allowing for faster startup and better resource utilisation.
        
    * Hypervisors: Virtual machines (VMs) that run full operating systems are created by hypervisors. When compared to containers, VMs provide greater isolation but consume more resources.
        
    * Refer this for more [know more](https://www.educba.com/hypervisor-vs-docker/) .
        
10. What are the advantages and disadvantages of using docker?
    
    * **Advantages:**
        
        * Docker allows for the quick and consistent deployment of applications. Environment Consistency: Docker ensures that applications run consistently in a variety of environments.
            
        * Containers share the host OS kernel, resulting in efficient resource utilisation.
            
        * Scalability: Docker facilitates application scaling via container orchestration platforms.
            
        * Containers provide isolation between applications, which improves security.
            
    * **Disadvantages:**
        
        * Docker networking can be complicated, especially in multi-container and multi-host setups.
            
        * Security Issues: Inadequate configuration can lead to security flaws. Docker containers are typically used for command-line applications and have limited GUI support.
            
        * Docker has a learning curve, which is especially important for users who are new to containerization.
            
11. What is a Docker namespace?
    
    * A Docker namespace is a mechanism that allows processes to be isolated within containers. It ensures that processes inside a container are isolated from other containers and the host system. To achieve this isolation, Docker employs namespaces such as PID, user, network, mount, and others.
        
12. What is a Docker registry?
    
    * A Docker registry is a location where Docker images can be stored and shared. It serves as a central repository for images, allowing users to create containers by pulling images from the registry. Docker Hub, Google Container Registry, and Amazon ECR are a few examples.
        
    * You can practice that here [practice here](https://dockerlabs.collabnix.com/beginners/build-private-docker-registry.html) .
        
13. What is an entry point?
    
    * The default command that is executed when a container is started from a Docker image is the entry point. It specifies the main process that should run inside the container. The docker run command can be used to override the entry point.
        
14. How to implement CI/CD in Docker?
    
    * CI/CD with Docker entails:
        
        * Docker images are used in the pipeline's build and test stages. A registry for storing built Docker images.
            
        * Pulling the most recent image and launching containers to automate deployment.
            
        * Orchestration tools such as Kubernetes can help to manage the deployment process even further.
            
15. Will data on the container be lost when the docker container exits?
    
    * Data in a container's filesystem is not saved after the container exits by default. You can use Docker volumes or bind mounts to connect container paths to host paths to persist data.
        
16. What is a Docker swarm?
    
    * Docker Swarm is a native Docker clustering and orchestration solution. It enables you to create and manage a cluster of Docker nodes, with features such as load balancing, high availability, and service scaling.
        
17. What are the docker commands for the following:
    
    * view running containers : `docker ps`
        
    * command to run the container under a specific name:
        
        `docker run --name <container_name> <image>`
        
    * command to export a docker:
        
        `docker export <container_id> > <output_file>.tar`
        
    * command to import an already existing docker image:
        
        `docker import <input_file>.tar`
        
    * commands to delete a container:
        
        `docker rm <container_id>`
        
    * command to remove all stopped containers, unused networks, build caches, and dangling images?
        
        `docker system prune`
        
18. What are the common docker practices to reduce the size of Docker Image?
    
    * **Use Lightweight Base Images**: Alpine Linux is a good example of a lightweight base image.
        
    * **Layers Minimise**: Combine commands to reduce the number of layers in an image.
        
    * **Multi-Stage Builds**: Use multi-stage builds to create final images with only the artefacts that are required.
        
    * **Optimise Dependencies**: Only include dependencies and libraries that are necessary.
        
    * **docker ignore**: Removes unwanted files from the build context.
        
    * **Cache Utilisation**: Configure commands to use Docker's layer caching mechanism. Remove temporary files and caches from the same layer.
        

> I hope you now can answer most of your interview questions on docker !!
> 
> You can go through my docker series to understand more in detail.
> 
> Happy Learning :D