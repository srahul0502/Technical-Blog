---
title: "Jenkins Agents: Your Path to Smooth CI/CD Scaling"
datePublished: Tue Aug 15 2023 12:19:55 GMT+0000 (Coordinated Universal Time)
cuid: cllc9u7y6000k09mxbt6maxoy
slug: jenkins-agents-your-path-to-smooth-cicd-scaling
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1692101941709/df74cff6-01c6-4966-b04b-a2882a16c4fc.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1692101978049/cd3ccb8a-cd27-403b-b2c0-a5179c335613.png
tags: devops, jenkins, devops-articles, 90daysofdevops, 90daysofdevops-chanllenge

---

## 👤Jenkins Master (Server)

* Jenkins’s server or master node holds all key configurations. The Jenkins master server is like a control server that orchestrates all the workflow defined in the pipelines. For example, scheduling a job, monitoring the jobs, etc.
    

## 👤Jenkins Agent

* An agent is typically a machine or container that connects to a Jenkins master and this agent actually executes all the steps mentioned in a Job. When you create a Jenkins job, you have to assign an agent to it. Every agent has a label as a unique identifier.
    
* When you trigger a Jenkins job from the master, the actual execution happens on the agent node that is configured in the job.
    
* A single, monolithic Jenkins installation can work great for a small team with a relatively small number of projects. As your needs grow, however, it often becomes necessary to scale up. Jenkins provides a way to do this called “master to agent connection.” Instead of serving the Jenkins UI and running build jobs all on a single system, you can provide Jenkins with agents to handle the execution of jobs while the master serves the Jenkins UI and acts as a control node.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692097085494/5c3896e8-d27f-4213-af50-73c95015dafd.webp align="center")
    

## 👤Configure Jenkins Agent

### Let's understand how to set up Jenkins master-agent setup.

* The first step is to create two EC2 instances and name them accordingly, I named them jenkins\_master and Jenkins\_agent.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692097383920/8b73d604-bd2a-4822-a4f9-b3bc27fb8c51.png align="center")
    
* Now Go to the jenkins\_master instance install docker and jenkins , add $USER and jenkins to docker group using `sudo usermod -aG docker $USER` & `sudo usermod -aG docker jenkins` . If you followd yesterdays blog then it will be more easy for you to underdstand this one.
    
* In jenkins\_master : go to .ssh directory and generate key
    
    ```bash
    cd .ssh
    ssh-keygen 
    # or i would suggest to go with this
    ssh-keygen -t ed25519
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692097746069/869417dd-91c6-41b0-9348-4e55eb87a268.png align="center")
    
* Copy the public key (id\_rsa.pub) use cat id\_rsa.pub to display the key
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692097839039/49d93d51-fe5d-40a6-8792-c61e602a603d.png align="center")
    
* Paste it in jenkins\_agent instance : go to the <mark>jenkins_agent</mark> instance , copy the public key in <mark>.ssh/authorized_keys</mark> .
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692097957260/69beb039-c0e2-475b-a431-8c5f61bf9cf3.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692097970187/878eeebd-7f9d-4e0e-90b8-6cb8312261dc.png align="center")
    

Come to the Jenkins\_master instance and try to connect to the jenkins\_agent via ssh

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692098012305/0ef7c0f0-d510-4b48-a2c9-b7236067c327.png align="center")

* This shows that I'm successfully connected to jenkins\_agent (check the IP) , now we can proceed with the next step.
    

### **Setting-up Agent in Jenkins**

* Go to Jenkins, just like we did in our previous blog ip:8080, go to set up an agent on the dashboard ( if you don't see that go to manage Jenkins&gt; Nodes )
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692098236217/9ac5954c-ece7-4fbf-972b-7d65d4e485b8.png align="center")
    
* It will ask to set node name, check mark on permanent agent and then create !!
    

Then on the next page, you will be asked to enter a few details such as description, remote directory, Host ip and credentials

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692098392666/e2bece71-5965-495b-952c-696091bee7a6.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692098430910/ea9c7e41-ae21-44b9-b5af-c07c97d961a8.png align="center")

* In the label, u can give any name, suppose I'll deploy a Django app I'll label it as Django, I named it a dev to deploy all development parts.
    
* In the launch method select it as <mark>Launch agents via SSH</mark> as we have shared the public key with jenkins\_agents.
    
* Host: give IP of jenkins\_agent (agent instance)
    
* Credentials: This is the major part, click on add
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692098692314/0e5ed6b0-ec4a-4119-8092-0cfc15210854.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692098806979/9eea8529-3043-4ebd-a7ba-eec403462e8f.png align="center")
    
    * Select the SSH username with the private key, id to store the private key and scroll down and add your private key to this
        
        use `cat id_rsa` to display
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692098826961/7f24acf3-63cd-46d6-acb2-f5ce8218a0a0.png align="center")
        
* In the Host key verification strategy select <mark>Non-Verifying Verification strategy</mark>
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692098951090/84813953-f71b-47c0-8cc3-06ad26dbe5c2.png align="center")
    
* Click on Create and tadaaa agent node is created !!
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692098993813/af770909-00ca-459e-9435-851fd758c808.png align="center")
    
* Refresh it once or click on the node and click on Launch node
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692099038974/2fb84588-602f-4ddb-8477-6d67631cc135.png align="center")
    

### Deploying the project

As we have seen in [this](https://srdev.hashnode.dev/jenkins-declarative-pipeline-with-docker) blog we will be deploying the same in the agent node.

The only difference in the pipeline script is

```bash
pipeline {
    agent { label "dev-agent" }
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

* The only difference is in **<mark>agents</mark> : we have specified the agent on which we want to deploy.**
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692099377048/79f1ec89-f3e6-4dd5-9fb5-66cb0e5ce084.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692099452506/05427950-8b1d-471b-b156-959c94ab7f75.png align="center")

* You can see this on the lefthand side bottom
    

### Error Handling💀:

* You might get an error while setting up the agent on Jenkins
    
* This might be due to extra spaces or incorrect key
    
* You can resolve this by generating another key as I have mentioned in the above steps `ssh-keygen ed25519`
    
* Difference between ed25519 and rsa :
    
    * Ed25519: Ed25519 uses 256-bit keys, making it relatively short but still secure due to the strength of the elliptic curve.
        
    * RSA: RSA keys are generally longer, often 2048 or 4096 bits, to achieve similar levels of security.
        

> I hope you found this useful
> 
> kindly go through [this](https://srdev.hashnode.dev/jenkins-declarative-pipeline-with-docker) to understand the deployment of the project
> 
> Happy Learning :D