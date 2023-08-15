---
title: "Docker Compose"
datePublished: Mon Aug 07 2023 13:43:04 GMT+0000 (Coordinated Universal Time)
cuid: cll0xabzh000r09joaj3r5v5l
slug: docker-compose
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1691408557020/abd0270f-2fbd-40d1-a625-e51865ea3819.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1691415607034/d8d9a2fa-72d7-4d2e-84ad-6c1748b237b0.png
tags: docker, devops, 90daysofdevops, 90daysofdevops-chanllenge, 90daysofdevops-devops-projectdevelopment-nonitbackground-github-docker-cloudplatforms-ec2-aws-elasticbeanstalk-lambdafunctions-devopspipelines-terraform-jenkins-docker-devsecops-scm-git-gitlab-bitbucket-buildtools-griddle-maven-ant-msbuild-monitoringtools-prometheus-grafana-ansible-ai-chatgpt-valueaddition-realworldproblems

---

## What is Docker compose ❓

* Docker Compose is a tool that was developed to help define and share multi-container applications.
    
* With Compose, we can create a YAML file to define the services and with a single command, can spin everything up or tear it all down.
    
* Docker Compose is a powerful tool for defining and managing multi-container applications through the use of a simple, human-readable YAML file. It allows developers to describe a whole application stack - including services, networks, and volumes - in a single file, making complex application setups easier to share and collaborate on.
    

## What is YAML ⁉️

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691408928879/fc010ee7-bd68-41c3-8f25-3ebad89cec16.avif align="center")

* YAML is a data serialisation format that allows for script interaction. It is commonly used to create configuration files because it prioritises human readability over JSON.
    
* YAML files use a .yml or .yaml extension, and follow specific syntax rules.
    
* Example :
    

```bash
#Comment: This is a supermarket list using YAML
#Note that - character represents the list
---
food: 
  - vegetables: tomatoes #first list item
  - fruits: #second list item
      citrics: oranges 
      tropical: bananas
      nuts: peanuts
      sweets: raisins
```

* You can read about YAML [here](https://www.redhat.com/en/topics/automation/what-is-yaml)
    

## 📜Docker compose file

* Let's create a docker-compose file
    

```bash
# Specify the version of the Docker Compose file format
version: '3'

# Define services (containers) for the application
services:
  # Configuration for the frontend web server (Nginx)
  frontend:
    # Use the latest Nginx image from Docker Hub
    image: nginx:latest
    # Map port 80 on the host to port 80 in the container
    ports:
      - "80:80"

  # Configuration for the backend database (MySQL)
  backend:
    # Use the latest MySQL image from Docker Hub
    image: mysql:latest
    # Set environment variables for the MySQL container
    environment:
      # Set the root password for the MySQL database
      MYSQL_ROOT_PASSWORD: example_password
      # The backend service uses a custom backend image mysql:latest and is linked to the frontend service
      links:
        - frontend
```

* We specify the Compose file version as `'3'`.
    
* We define two services: frontend and backend
    
* For the `frontend` service:
    
    * We use the latest Nginx image.
        
    * We map port 80 on the host to port 80 in the container.
        
* For the `backend` service:
    
    * We use the latest MySQL image.
        
    * We set the `MYSQL_ROOT_PASSWORD` environment variable for MySQL.
        
    * The backend service uses a custom backend image mysql:latest and is linked to the frontend service .
        
* So , the above was a simple docker compose file which is simple to understand but yeah you have to practice :D
    

## 📜Docker Commands :

* Let's understand how to pull and image and run it as coontainer and then try to understand how to stop or kill the running container and remove the running containers.
    
* Pull a pre-existing Docker image from a public repository (e.g. Docker Hub)
    
    * [Docker Hub](https://hub.docker.com) contains many pre-built images that you can `pull` and try without needing to define and configure your own.
        
    * To download a particular image, or set of images (i.e., a repository), use `docker pull`.
        
        ```bash
        #syntax 
        docker pull [OPTIONS] NAME[:TAG|@DIGEST]
        
        #example
        docker pull nginx
        ```
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691415923663/e130471c-8fa8-40ce-801c-50f17dfccb4b.png align="center")
        
* Run the container as a non-root user
    
    ```bash
    # syntax
    docker run -d --name my-container --user $(id -u):$(id -g) <image_name>
    # Example
    ```
    
    * `-d`: Run the container in detached mode.
        
    * `--name my-container`: Assign a name to the container (replace `my-container` with your preferred name).
        
    * `--user $(id -u):$(id -g)`: Run the container as a non-root user (the `id -u` gets the current user's user ID, and `id -g` gets the group ID).
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691413911520/c4c65671-9a98-49d7-89f4-22fc6873d719.png align="center")
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691413924509/30cf9ff7-35d5-413f-842a-71b668551926.png align="center")
        
* Use usermod command to give user permission to docker and reboot once
    
    ```bash
    sudo usermod -aG docker $USER
    # -aG - addes the user to docker group
    # usermod - modify user attributes
    sudo reboot
    ```
    
* Inspect the container's running processes and exposed ports using `docker inspect`
    
    ```bash
    # syntax
    docker inspect <image name>
    #example
    docker inspect NGINX
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691414485498/9942d97f-799c-4267-addb-b355b8b137d6.png align="center")
    
* use docker log command to view container's log output
    
    ```bash
     docker logs [OPTIONS] CONTAINER
    ```
    
* Use docker stop command to stop the container
    
    ```bash
    docker stop <image name>
    #example
    docker stop NGINX
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691415327595/695cf767-5c20-4827-9f45-f4a1e3215ea5.png align="center")
    
* Use docker start container to start the container
    
    ```bash
    docker start <image name>
    #example
    docker start NGINX
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691415435299/0a0ab733-d7d1-47f5-8680-859c93e45b7e.png align="center")
    

## How to run Docker commands without sudo?

* Make sure docker is installed and system is updated (This is already been completed as a part of previous tasks):
    
* `sudo usermod -a -G docker $USER`
    
* Reboot the machine `sudo reboot`.
    

> I hope now you can pull an image ,run it ,start and stop and atlast inspect the container as well ..  
> See you again with some more knowledge
> 
> Happy Learning :D