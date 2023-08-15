---
title: "Jenkins Declarative Pipeline with Docker"
datePublished: Tue Aug 15 2023 08:09:13 GMT+0000 (Coordinated Universal Time)
cuid: cllc0vt87000i09mo0adp6lmv
slug: jenkins-declarative-pipeline-with-docker
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1692086874681/ef759cf2-4145-4a4c-a3ec-4d50fab14d22.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1692086942274/7cfae4c7-fb27-473b-b073-9be1ed419f43.png
tags: docker, devops, jenkins, 90daysofdevops, jenkins-declarative-pipeline

---

> Welcome to the new blog
> 
> Here we'll make a complete project using Jenkins declarative pipeline
> 
> Kindly go through previous blog to understand about declarative pipeline :[here](https://srdev.hashnode.dev/getting-started-with-jenkins-declarative-pipeline)

## Jenkins Declarative Pipeline

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692079619065/9f8abecc-95f5-4ad8-b028-c43c66f54ea8.png align="center")

### Let's understand more about the Jenkins declarative pipeline :

* In Jenkins, a Declarative Pipeline is a way to define your software delivery process as code. It's intended to make building continuous integration and continuous delivery (CI/CD) pipelines easier by providing a structured and opinionated syntax. Rather than scripting the pipeline logic from scratch, Declarative Pipelines allow you to describe the desired flow of your pipeline using a human-readable and simple syntax.
    
* For example :
    
    ```plaintext
    pipeline {
        agent any
        stages {
            stage('Build') {
                steps {
                    echo 'Building the application...'
                }
            }
            stage('Test') {
                steps {
                    echo 'Running tests...'
                }
            }
            stage('Deploy') {
                steps {
                    echo 'Deploying the application...'
                }
            }
        }
        post {
            always {
                echo 'Pipeline completed.'
            }
        }
    }
    ```
    
    * In this example, the pipeline runs on any available agent goes through three stages (Build, Test, Deploy), and then always prints a message indicating pipeline completion.
        
* By default, stages in a Jenkins Declarative <mark>Pipeline run sequentially</mark>, meaning one stage starts only after the previous stage has been completed successfully.
    
* We can also <mark>Integrate third-party tools seamlessly</mark> into your pipeline for enhanced functionality. Integrate security scanning, performance testing, or code analysis tools directly into your pipeline stages (such as docker).
    

### Let's make a project Integrating the docker and Jenkins pipeline :

**Pre-requisites :**

* Jenkins, docker must be installed
    
* make sure you add Jenkins and $USER to the docker group
    
* Install the docker pipeline plugin in Jenkins (Not necessary)
    

**Step 1:** Go to your Jenkins dashboard ( refer [this](https://srdev.hashnode.dev/getting-started-with-jenkins) ), click on New item give a name and select Pipeline.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692083627377/f614a00f-fce9-4e1c-8961-e0cd81643b5e.png align="center")

**Step 2:** Scroll down and check on git , and give URL of your GitHub repo

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692083688761/1191044b-cea3-42d9-8a79-ebc7ab75c591.png align="center")

* If you want to build any triggers, you can check mark on GitHub hook
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692083726735/100f196f-bdc8-47fb-be4b-b1b60e7698c6.png align="center")
    

**Step 3:** Let's write the groovy syntax for the pipeline

Here's the basic structure of the stages :

```plaintext
pipeline {
    agent any
    stages {
        stage("Clone Code") {
            steps {
                echo "Cloning the code"
            }
        }
        stage("Build") {
            steps {
                echo "Building the image"
            }
        }
        stage("Push To Docker Hub") {
            steps {
                echo "Pushing the image to docker hub"
            }
        }
        stage("Deploy") {
            steps {
                echo "Deploying the container"
            }
        }
    }
}
```

* Save it and click on Build now to check if it's working, as you can see we have successfully built the structure
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692083849465/78b3b3d7-1e09-4e58-8abd-f342c3e767c2.png align="center")
    

**Step 4:** Go back to configure and pass commands in the pipeline script to clone the GitHub repo, build the docker image, push it to the docker hub and finally deploy it

* In this, we <mark>use "sh" to write shell commands in Groovy syntax</mark>
    

```plaintext
pipeline {
    agent any
    stages {
        stage("Clone Code") {
            steps {
                echo "Cloning the code"
                git url:"https://github.com/srahul0502/django-todo-cicd.git", branch: "develop"
            }
        }
        stage("Build") {
            steps {
                echo "Building the image"
                sh "docker build -t django-app ."
            }
        }
        stage("Push To Docker Hub") {
            steps {
                echo "Pushing the image to docker hub"
                withCredentials([usernamePassword(credentialsId:"dockerHub" ,passwordVariable:"dockerHubPass" ,usernameVariable:"dockerHubUser")]){
                sh "docker tag django-app ${env.dockerHubUser}/django-app:latest"
                sh "docker login -u ${env.dockerHubUser} -p ${env.dockerHubPass}"
                sh "docker push ${env.dockerHubUser}/django-app:latest"
                }
            }
        }
        stage("Deploy") {
            steps {
                echo "Deploying the container"
                sh "docker run -d -p 8000:8000 srahul0502/django-app:latest"
            }
        }
    }
}
```

Let's break down this syntax :

**Stage "Clone Code" :**

* git URL - in this, we pass the GitHub repo URL , branch to be cloned
    

**Stage "Build" :**

* We use sh to write shell commands in groovy
    
* docker build -t django-app. is used to build the image out of a docker file in the GitHub repo it will clone
    

**Stage "Push to docker Hub" :**

* Here we push the image to the docker hub, for that we have to first login to docker hub, for that we <mark>use environment variables to pass username and password</mark> to log in.
    
* And we save these environment variables under an ID , now let's see how to create environment variables and use them
    
    * Go to manage Jenkins &gt; Security &gt; credentials &gt;system &gt; add credentials
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692084559137/cef3e7d5-57db-4119-a36a-d474b75e4b0a.png align="center")
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692084612107/c306af76-5d34-4bb8-bee2-3e8a45598657.png align="center")
        
        Under kind select "Username with Password
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692084658590/4a034f57-ac89-4f20-b464-b47dd9f5576e.png align="center")
        
        Fill in all the remaining details, <mark>username and password of your dockerhub account</mark>, as you can see there's an ID section where these variables will be stored,<mark>make sure you remeber the id </mark> .
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692084749109/0c940614-3fab-4e98-8b3a-2fce5c8b0729.png align="center")
        
        Click on add/save and you are done with creating the env variable
        
    * Now we use <mark>withCredentials</mark> which is a groovy syntax to use the credentials and passed them where ever it was required.
        
    * Make sure you tag your image with your username to push it to the docker hub username/image.
        

> Pushing to dockerHub completely depends on you, you can skip this if you want, but you can learn about env variables and how to use them. Give it a try.

**Stage "Deploy" :**

* Deployed the container to port 8000 in detached more (running in the background)
    

**Step 5:** Click on Build..!!

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692085274457/6d0f79fc-f17f-4eea-a668-50f9164d7cb9.png align="center")

* Successfully built and deployed
    
* It pushed the image to the docker hub as well
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692085322633/37e20787-eeff-4536-b5e4-32976e79f53c.png align="center")
    

**Finally deployed :**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692085346848/0e9e09d0-041e-4a63-81f9-bc04a5d33eee.png align="center")

> I hope now you can create your own declarative pipeline for your projects..!!
> 
> Happy Learning :D