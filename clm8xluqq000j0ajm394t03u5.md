---
title: "Getting Started With AWS"
datePublished: Thu Sep 07 2023 08:53:53 GMT+0000 (Coordinated Universal Time)
cuid: clm8xluqq000j0ajm394t03u5
slug: getting-started-with-aws
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1694076617084/b1669780-6e8c-47d7-b18f-57589de6c5c2.gif
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1694076812849/6b64e277-c6de-4106-8a9e-7d08627142a7.gif
tags: aws, devops, devops-articles, devops-journey, 90daysofdevops

---

# **☁️ Amazon Web Services (AWS):**

AWS, or Amazon Web Services, is a cloud computing platform provided by Amazon. It offers a wide range of services and resources that allow individuals and organizations to build and run applications, store and analyze data, host websites, and much more, all without the need to invest in and maintain physical hardware. Here are some key aspects of AWS:

1. **Global Infrastructure:** AWS operates data centers in multiple regions around the world. This global presence enables users to deploy their applications and services closer to their end-users, improving performance and reliability.
    
2. **Pay-as-You-Go:** AWS follows a pay-as-you-go pricing model, which means users are billed only for the resources they use. This flexibility allows cost-effective scaling up or down based on demand.
    
3. **Services:** AWS offers a vast array of services, including but not limited to:
    
    * **Compute:** Services like Amazon EC2 (Elastic Compute Cloud) provide virtual servers for running applications.
        
    * **Storage:** AWS provides scalable storage solutions such as Amazon S3 (Simple Storage Service) for files and Amazon RDS (Relational Database Service) for databases.
        
    * **Networking:** AWS offers tools for managing networks, load balancing, and content delivery.
        
    * **Machine Learning:** AWS has services like Amazon SageMaker for machine learning and artificial intelligence applications.
        
    * **Security:** AWS provides a wide range of security tools and features to protect data and applications.
        

Some of the practical examples of using AWS are :

1. **Host a Static Website:** Use Amazon S3 to host a basic HTML website.
    
2. **Launch a Virtual Server:** Start an EC2 instance, install a web server, and deploy a simple web app.
    
3. **Set Up a Database:** Create a MySQL database using Amazon RDS.
    
4. **Store Files:** Learn Amazon S3 by uploading and accessing files.
    
5. **Balance Traffic:** Use Elastic Load Balancer (ELB) to distribute web traffic across multiple servers.
    
6. **Automate with Lambda:** Create a serverless function to perform tasks triggered by events.
    
7. **Manage Users:** Experiment with IAM to control who can access AWS resources.
    
8. **Monitor Resources:** Set up monitoring and alerts using Amazon CloudWatch.
    
9. **Secure Network:** Build a Virtual Private Cloud (VPC) with security groups.
    
10. **Basic DevOps:** Try AWS CodeCommit, CodeBuild, and CodeDeploy for code management and deployment.
    

# **☁️ AWS Identity and Access Management (IAM):**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694076606861/238539a1-da75-443b-94da-412392fbdedb.png align="center")

IAM is a service within AWS that allows you to control who can access your AWS resources and what actions they can perform. Here's a closer look at IAM:

1. **User Management:** IAM lets you create and manage individual users or groups of users. Each user is assigned unique security credentials (like access keys and passwords) to access AWS services.
    
2. **Resource Permissions:** IAM enables you to define fine-grained permissions for each user or group. You can specify which AWS resources (e.g., EC2 instances, S3 buckets) they can access and what actions (e.g., read, write, delete) they can perform on those resources.
    
3. **Security Best Practices:** IAM helps you adhere to security best practices by implementing the principle of least privilege. This means users are granted only the minimum permissions needed to perform their tasks, reducing the risk of unauthorized access.
    
4. **Multi-Factor Authentication (MFA):** IAM supports MFA, an additional layer of security that requires users to provide two or more verification factors (e.g., a password and a one-time code from a mobile app) to access their AWS accounts.
    
5. **Integration with AWS Services:** IAM integrates seamlessly with various AWS services, allowing you to control access to not only AWS Management Console but also APIs, CLI, and SDKs.
    

# ☁️ Hands-On Practice

Certainly! Let's break down the detailed steps for both Task 1 and Task 2:

### **Task 1: Creating an IAM User and Launching an EC2 Instance**

1. **Log into the AWS Management Console:**
    
    * Go to the AWS Management Console at [https://aws.amazon.com/](https://aws.amazon.com/).
        
    * Sign in with your AWS account credentials or create a new AWS account if you don't have one.
        
2. **Access IAM Service:**
    
    * From the AWS Management Console, navigate to the IAM (Identity and Access Management) service. It's usually located under the "Security, Identity, & Compliance" section.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694072737088/14d77482-3014-48d7-816e-169ccc2570c2.png align="center")
        
3. **Create a New IAM User:**
    
    * Inside the IAM dashboard, select "Users" from the left-hand menu.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694073017369/1ea1a3b5-eb09-4f80-ab74-1c277e8c9461.png align="center")
        
    * Click the "Add user / Create User" button to create a new IAM user.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694073099970/05d7d70f-1615-47ea-8940-d3be07b50ab5.png align="center")
        
    * Enter a username of your choice (e.g., "EC2User") and select the "Provide user access to AWS management console" checkbox , then select "I want to create an IAM user" Check Box.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694073315726/1d779e5f-41a1-42b9-85db-6798d93fbef7.png align="center")
        
    * Set a custom password , and select " user must create a new password at next sign-in " so that the user can set their on password when login .
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694073300596/3388ffb1-fd78-42f8-8928-473213ca1d10.png align="center")
        
4. **Attach Permissions:**
    
    * In the permissions step, choose "Attach policies directly."
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694073352968/df10649e-01e8-47fa-b74b-efb692dc5409.png align="center")
        
    * Search for and select the "AmazonEC2FullAccess" policy. This policy grants full access to Amazon EC2 resources.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694073365953/897d34e3-d04b-4f92-9e81-d45d6d71993f.png align="center")
        
    * Click "Next" to review, and then click "Create user."
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694073416938/d7302e1e-1754-410f-98c0-d3ca326bd040.png align="center")
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694073462503/29f16fd8-f639-44bd-9508-337696bd509d.png align="center")
        
5. **Launch an EC2 Instance:**
    
    * Now, you'll use the IAM user to launch an EC2 instance .
        
    * Log into the AWS Management Console if you're not already logged in.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694073513999/da467294-49b8-4c98-8fd7-10a01287ebd3.png align="center")
        
        Now it'll ask you to set a new password
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694073557021/174e0fe9-44b6-489c-aeac-464f5c25ef73.png align="center")
        
    * Navigate to the EC2 service.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694073638681/37d43ed7-dea8-4c99-8a19-7739edf66089.png align="center")
        
6. **Launch an EC2 Instance:**
    
    * Click the "Launch Instance" button to create a new virtual machine.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694073715736/1ce120de-ebc5-42b4-b80b-1f0de9964c43.png align="center")
        
    * Follow the EC2 instance creation wizard, selecting the desired instance type and other settings.
        
        * Name of the instance:
            
            ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694073843829/a1f3635a-d7e1-4360-8286-c13d72a2866a.png align="center")
            
        * Os type : here i have selected ubuntu
            
            ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694073872762/55f17b56-de94-428e-8089-0109a64aa6ce.png align="center")
            
        * Select the instance type and create new Key pair : here I have selected t2.micro which is free tier .
            
            ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694073943621/2042ed85-ec1d-43b9-9bd8-788b974abcff.png align="center")
            
        * A key pair is used for secure authentication and access control to instances (virtual machines) created using Amazon Elastic Compute Cloud (EC2) and for other AWS services. Key pairs consist of two parts: a public key and a private key.
            
            ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694073995025/0a155b29-3fa5-4bdb-bbf4-61da0508e421.png align="center")
            
    * Now click on launch instance and wait for the prompt saying succesfully created.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694074191454/f2884f8f-5d11-402f-b51e-e9c1e66f9ca8.png align="center")
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694074206772/a7774105-5765-4af2-8b47-0ce44aaa35c4.png align="center")
        
7. **Connect to EC2 Instance and Install Jenkins and Docker:**
    
    * Once the EC2 instance is running, you can connect to it via SSH using the private key you specified during instance creation.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694074227729/73eab401-a671-4545-b258-dd1e0100cc73.png align="center")
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694074304719/b8ae74b7-a3ef-4c24-afca-ca78bd679d92.png align="center")
        
    * Go to SSH client and copy the example and paste it in your terminal
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694074317860/9bef3f55-8788-4026-9762-d58214eaa41d.png align="center")
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694074362728/173bf250-94d0-456f-a63e-036a814b8426.png align="center")
        
    * Once logged in, you can run a shell script to install Jenkins and Docker. Now we'll run a bash script to install docker and jenkins .
        
        ```bash
        #!/bin/bash
        
        #installing docker
        sudo apt-get update
        sudo apt-get install docker.io -y
        sudo usermod -aG docker $USER
        sudo systemctl start docker
        sudo systemctl enable docker
        	
        #installing java
        sudo apt update
        java -version
        sudo apt-get install -y default-jre
        javac -version
        
        #installing jenkins
        curl -fsSL https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key | sudo tee \
                    /usr/share/keyrings/jenkins-keyring.asc > /dev/null
        echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
                    https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
                        /etc/apt/sources.list.d/jenkins.list > /dev/null
        sudo apt update
        sudo apt-get install -y jenkins
        sudo systemctl start jenkins.service
        sudo systemctl enable jenkins
        ```
        
    * Use any editor such as nano or vim , copy the script and save it as <mark>install_docker_jenkins.sh</mark>
        
    * Give the necessary permissions (execute permission) use `chmod +x` filename to give execute permission. Use ./filename.sh to execute the script.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694074590805/130e5fef-32f1-409f-9d9f-aebd4f52b8c2.png align="center")
        
    * Now check the status of docker and jenkins using command
        
        ```bash
        sudo systemctl status docker 
        sudo systemctl status jenkins
        ```
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694074735159/28937a98-ac4d-45d6-bbd2-aafb76bc76d1.png align="center")
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694074750844/5894a848-bcba-4715-80c7-e7a3c60eb55f.png align="center")
        

### **Task 2: Creating IAM Users for a DevOps Team**

1. **Log into the AWS Management Console:**
    
    * If you're not already logged in, access the AWS Management Console.
        
2. **Access IAM Service:**
    
    * Navigate to the IAM service as explained in Task 1.
        
3. **Create IAM Users:**
    
    * Inside the IAM dashboard, select "Users" from the left-hand menu.
        
    * Click the "Add user" button to create three IAM users, one for each member of your DevOps team. Provide usernames and select "Provide user access to AWS management console" for each user.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694075434475/68b8444e-79d7-4057-85f6-a28b77c22dc6.png align="center")
        
4. **Assign Users to a DevOps Group:**
    
    * After creating the users, you can group them together. Select "Groups" from the left-hand menu and create a new group (e.g., "Avengers-DevOps").
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694075511820/0ac9d01c-9a89-4521-9c10-8832a81858f2.png align="center")
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694075542490/30d91e47-215c-48ce-86d4-2e3b22d19d42.png align="center")
        
    * Add the three IAM users to this group.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694075564676/47a7b4df-ffc7-44e9-9a12-7f7e6aa9a911.png align="center")
        
5. **Create an IAM Policy:**
    
    * To define what actions the Avengers-DevOps team members can perform, you'll need to create an IAM policy.
        
    * Scroll down and you will find policy.
        
    * Use the policy editor to specify the permissions you want. For example, you can grant permissions to access specific EC2 instances, manage S3 buckets, and interact with other AWS services.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694075664184/c63cbb54-fca7-44e6-9f22-271ef0445c60.png align="center")
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694075675480/29a7a3a3-f2b7-4552-ab11-0d9970c823bb.png align="center")
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694075685037/07b36bf3-2053-494d-9c03-221fe2425d51.png align="center")
        
    * Now click on Create Group on bottom right hand side .
        
    * Now if you go the user group sectio in IAM , you can see that the group is created.
        
    * Now, each user is associated with a specific DevOps group with the necessary IAM policies. You can add more users by clicking “Add users”.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694075894012/318683f5-25cf-4c40-a98c-bedcbd146fbe.png align="center")
        

* Now, your Avengers-DevOps team members (the IAM users) are part of thec"Avengers-DevOps Group" and have the permissions defined by the IAM policy you created. This allows them to collaborate on AWS resources while adhering to access control and security best practices.
    

> I hope now you understood how to create and IAM User.  
> Happy Learning :D