---
title: "Docker Volume & Docker Network"
datePublished: Wed Aug 09 2023 11:19:56 GMT+0000 (Coordinated Universal Time)
cuid: cll3n1yuz000009l6f0euaso7
slug: docker-volume-docker-network
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1691579871682/a87908cc-3901-4164-a107-875da220dabb.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1691579894236/d495e736-f963-4eaa-b754-d49b21bab320.png
tags: docker, devops, 90daysofdevops, 90daysofdevops-chanllenge, 90daysofdevops-devops-projectdevelopment-nonitbackground-github-docker-cloudplatforms-ec2-aws-elasticbeanstalk-lambdafunctions-devopspipelines-terraform-jenkins-docker-devsecops-scm-git-gitlab-bitbucket-buildtools-griddle-maven-ant-msbuild-monitoringtools-prometheus-grafana-ansible-ai-chatgpt-valueaddition-realworldproblems

---

## Docker Volumes

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691550476826/7440ca82-7f91-4a0b-ae39-69747ea952d6.png align="center")

* Docker allows you to create something called volumes. Volumes are like separate storage areas that can be accessed by containers. They allow you to store data, like a database, outside the container, so it doesn't get deleted when the container is deleted. You can also mount from the same volume and create more containers having same data.
    
* Docker volumes are like special containers just for data. They're designed to keep your important stuff safe, even if the main application container changes or goes away. It's like having a secure vault that you can open and access whenever you need, no matter what's happening with the application container.
    
* You can read more about docker volumes [here](https://docs.docker.com/storage/volumes/)
    

## Docker Network

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691550643741/b9e29bdd-c5df-42fb-ae50-b5061381e295.png align="center")

* Docker allows you to create virtual spaces called networks, where you can connect multiple containers (small packages that hold all the necessary files for a specific application to run) together. This way, the containers can communicate with each other and with the host machine (the computer on which the Docker is installed). When we run a container, it has its own storage space that is only accessible by that specific container. If we want to share that storage space with other containers, we can't do that.
    
* When you create containers without specifying a network, Docker puts them in a default bridge network. This is like the default neighbourhood where all houses are connected. They can chat with each other, but they're kind of hidden from the outside world.
    
* You can read more about docker network [here](https://docs.docker.com/network/) .
    

## Simplify the Deployment of Multi-Container Apps with Docker-Compose

* Let's Create a multi-container docker-compose file that will bring UP and bring DOWN containers in a single shot ( Example - Create application and database container )
    
* Do not take stress about the front-end code or the back-end code it'll be provided by the developer ( [code](https://github.com/srahul0502/two-tier-flask-app) ) , our work is to create a docker file for the project and docker-compose to configure and start multiple containers.
    

### Docker file

* Let's begin with the docker file :
    
    ```bash
    # Use an official Python runtime as the base image
    FROM python:3.9-slim
    ```
    
    it's using the official Python 3.9 image with the "slim" variant. This image provides the runtime environment for your Python application
    
    ```bash
    # Set the working directory in the container
    WORKDIR /app
    ```
    
    This command sets the working directory within the container to /app. It's the directory where your application's files will be stored
    
    ```bash
    # install required packages for system
    RUN apt-get update \
        && apt-get upgrade -y \
        && apt-get install -y gcc default-libmysqlclient-dev pkg-config \
        && rm -rf /var/lib/apt/lists/*
    ```
    
    Here, you're updating the package list, upgrading existing packages, and installing specific packages (gcc, default-libmysqlclient-dev, pkg-config) that your application might need. It's common to install system-level dependencies before installing Python packages.
    
    ```bash
    # Copy the requirements file into the container
    COPY requirements.txt .
    ```
    
    This line copies the requirements.txt file from your local directory into the /app directory in the container. The requirements.txt file typically lists the Python packages required by your application.
    
    ```bash
    # Install app dependencies
    RUN pip install mysqlclient
    RUN pip install --no-cache-dir -r requirements.txt
    ```
    
    First, it installs the mysqlclient package, which is a MySQL client library. Then, it installs the packages listed in requirements.txt using pip. The --no-cache-dir option ensures that the package cache is not stored in the image to reduce its size.
    
    ```bash
    # Copy the rest of the application code
    COPY . .
    ```
    
    This command copies the remaining files from your local directory into the /app directory in the container .
    
    ```bash
    
    # Specify the command to run your application
    CMD ["python", "app.py"]
    ```
    
    Finally, this line sets the default command to run when the container starts. In this case, it runs the [app.py](http://app.py) Python script using the Python interpreter.
    
* Docker file :
    
    ```bash
    # Use an official Python runtime as the base image
    FROM python:3.9-slim
    
    # Set the working directory in the container
    WORKDIR /app
    
    # install required packages for system
    RUN apt-get update \
        && apt-get upgrade -y \
        && apt-get install -y gcc default-libmysqlclient-dev pkg-config \
        && rm -rf /var/lib/apt/lists/*
    
    # Copy the requirements file into the container
    COPY requirements.txt .
    
    # Install app dependencies
    RUN pip install mysqlclient
    RUN pip install --no-cache-dir -r requirements.txt
    
    # Copy the rest of the application code
    COPY . .
    
    # Specify the command to run your application
    CMD ["python", "app.py"]
    ```
    
    You can build an image to test whether docker file is working properly or not `docker build . -t test-two-tier-backend` this builds an image with tag test-two-tier-backend.
    

### Docker-Compose

* Let's create a docker-compose file to bring up and bring down the containers in a single shot.
    
    ```bash
    version: '3'
    services:
      # Backend service (your application)
      backend:
        build:
          context: .   # Build context is the current directory
        ports:
          - "5000:5000"   # Map host port 5000 to container port 5000
        environment:
          MYSQL_HOST: mysql
          MYSQL_USER: root
          MYSQL_PASSWORD: test@123
          MYSQL_DB: two_tier
        depends_on:  # Wait for the MySQL service to be ready
          - mysql
    
      mysql:
        image: mysql:5.7
        ports:
          - "8000:8000"  # maps port 8000 of the host to port 8000 of the container
        environment:
          MYSQL_ROOT_PASSWORD: test@123
          MYSQL_DATABASE: two_tier
          MYSQL_USER: devops
          MYSQL_PASSWORD: devops
        volumes:
          - mysql-data:/var/lib/mysql  # Mount the volume for MySQL data storage
    # Define a volume named "mysql-data" for MySQL data storage
    volumes:
      mysql-data:
    ```
    
    * This Docker Compose file defines a multi-container environment with two services: backend (representing your application) and mysql (representing the MySQL database)
        
    * **The backend service:** It builds the application from the current directory (where the Dockerfile is located). Maps host port 5000 to container port 5000, allowing access to the backend service from outside the container. Sets environment variables for connecting to the MySQL database. Depends on the mysql service, ensuring the database is ready before the backend starts.
        
    * **The mysql service:** Uses the MySQL 5.7 image from Docker Hub. Sets environment variables for configuring MySQL (root password, database name, user, and password). Mounts a volume named mysql-data to persist MySQL data.
        
    * **The volumes section:** Defines the mysql-data volume, which is used to store MySQL data separately from the container.
        
* **Docker-compose up command :**
    
    * We can use the docker-compose up command with the -d flag to start a multi-container application in detached mode. `docker-compose up -d`
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691555934834/1d3dff22-2d26-456e-b316-f8716c752cca.png align="center")
        
* **Docker-compose scale command:**
    
    * We can use the docker-compose scale command to increase or decrease the number of replicas for a specific service. You can also add [replicas](https://stackoverflow.com/questions/63408708/how-to-scale-from-within-docker-compose-file) in the deployment file for auto-scaling.
        
    * `docker-compose up -d --scale backend=2`
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691571949390/20f4a06d-dc03-4269-bdb2-7c946873614d.png align="center")
        
* **Docker-compose down command:**
    
    * We use the docker-compose down command to stop and remove all containers, networks, and volumes associated with the application.
        
    * `docker-compose down`
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691572077532/062bb2c9-c2e0-48d2-a1cc-643224157dc2.png align="center")
        

### Docker Volume:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691577518803/bb37a9ae-e1bd-46ae-bd94-e7568d3a5ab8.png align="center")

**Docker Volumes:**

* Docker Volumes are a way to persist data generated by Docker containers. They are stored outside the container, which means the data can be shared across containers and persists even if the container is deleted.
    
* To use Docker Volumes, you can use the -v flag when you start a container. For example:
    
    ```bash
    docker run -v /host/path:/container/path myimage
    #This will create a Docker Volume that maps the directory at 
    # /host/path on the host machine to the directory at /container/path 
    # inside the container. If the directory does not exist on the host machine, Docker will create it.
    ```
    
* To use the same Docker Volume across multiple containers, you can use the same -v flag when starting each container. For example:
    
    ```bash
    docker run -v myvolume:/data myimage
    # This will create a Docker Volume named myvolume and map it to the 
    # directory at /data inside the container. You can then use the same myvolume volume 
    # with other containers by using the same command.
    ```
    

**Named-Volumes:**

* Named Volumes are similar to Docker Volumes, but they are managed by Docker and have additional features such as backup and restore.
    
* To use Named Volumes, you can specify them in your `docker-compose.yml` file. For example:
    
    ```bash
    version: "3.9"
    services:
      db:
        image: mysql:5.7
        volumes:
          - myvolume:/var/lib/mysql/data
    volumes:
      myvolume:
    ```
    
* This will create a Named Volume named `myvolume` and map it to the directory at `/var/lib/postgresql/data` inside the container. You can then use the same `myvolume` volume with other services by specifying it in the `volumes` section.
    
* To use the same Named Volume across multiple containers, you can use the same volume name in the `volumes` section of each service.
    
    ```bash
    version: "3.9"
    services:
      app:
        image: myapp:latest
        volumes:
          - myvolume:/app/data
      db:
        image: mysql:5.7
        volumes:
          - myvolume:/var/lib/mysql/data
    volumes:
      myvolume:
    ```
    
* This will create a Named Volume named myvolume and map it to the directory at /app/data inside the app service and /var/lib/postgresql/data inside the db service. You can then use the same myvolume volume with other services by specifying it in the volumes section.
    

**Volume to Share file Between multiple containers:**

* Let's create a docker volume to share files and directories between multiple containers.
    
    ```bash
    docker volume create --name Volume1 --opt type=none --opt device=/home/ubuntu/docker-project/volumes --opt o=bind
    # Create a Docker volume with a specific name
    docker volume create --name Volume1
    
    # Specify volume creation options
    # Use volume type "none", which means Docker won't manage the volume's lifecycle
    # Set the source directory for the volume as "/home/ubuntu/docker-project/volumes" on the host machine
    # Create the volume as a bind mount, making the host directory contents accessible in the container
    docker volume create --name Volume1 \
      --opt type=none \
      --opt device=/home/ubuntu/docker-project/volumes \
      --opt o=bind
    ```
    
    * `type=none` specifies that Docker won't manage the volume's lifecycle.
        
    * `device=/home/ubuntu/docker-project/volumes` designate the source directory on the host machine.
        
    * `o=bind` creates the volume as a bind mount, allowing the container to access the host directory's content.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691576738283/3495a2c8-9bcf-4427-9306-cdeb435d2471.png align="center")
        
* Create two or more containers that read and write data to the same volume using the docker run --mount command.
    
    ```bash
    docker run -d --name writer-container --mount source=Volume1,target=/data ubuntu sleep infinity
    # Run a Docker container in the background (detached mode)
    docker run -d \
    
    # Give the container a name for easy identification
    --name writer-container \
    
    # Connect a storage space named "Volume1" to the container
    # Make the contents of "Volume1" available inside the container at /data
    --mount source=Volume1,target=/data \
    
    # Start the container based on the "ubuntu" software environment
    # This provides a basic operating system to work with
    ubuntu 
    
    # Keep the container active by having it sleep indefinitely
    # This allows you to interact with the container even though it's not performing any tasks
    sleep infinity
    
    docker run -d --name reader-container --mount source=Volume1,target=/data ubuntu sleep infinity
    # u can seee the above comments u will understand the code
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691576995617/105ed61b-47ed-4e3c-a928-861e02445ec7.png align="center")
    
* Let's go the writer container and write something such as message.txt
    
    ```bash
    # executes it in interactive mode
    docker exec -it writer-container bash
    cd data
    echo"Hello Container 1"> message.txt
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691577203343/97bfe416-6e5f-44a3-b9cd-9b2f1ba09df7.png align="center")
    
* Now , go the other container and check if it has the same file or not
    
    ```bash
    docker exec -it reader-container bash
    cd data
    cat message.txt
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691577272657/8cc477f2-cdcd-4303-afcd-31ccc2cb109c.png align="center")
    
* Tadaaaaaa !!!! both the containers share the same volume and the data exists in both the containers.
    
* Now how to remove the containers and the volumes
    
    ```bash
    # kill the container 
    docker kill <container-id/name>
    # Removes the container
    docker rm <container-id/name>
    # List the volumes
    docker volume ls
    # remove the volume
    docker volume rm <volume-name>
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691577380761/41c9941e-b5a6-4c6c-92fc-292f4016892e.png align="center")
    

> I hope you now you can create your own volumes and attach to the containers
> 
> Happy Learning :D