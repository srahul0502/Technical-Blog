---
title: "IAM Programmatic access and AWS CLI 🚀 ☁"
datePublished: Sun Sep 10 2023 02:11:54 GMT+0000 (Coordinated Universal Time)
cuid: clmctkfye000209l2bvlpcs72
slug: iam-programmatic-access-and-aws-cli
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1694310311363/fc946840-026e-477d-b8b4-5f84908e6999.jpeg
tags: aws, devops, devops-articles, 90daysofdevops

---

## 🔑 AWS Programmatic Access

**AWS programmatic access** refers to the ability to interact with AWS services and resources using code, scripts, or command-line tools, rather than through the AWS Management Console, which is the web-based graphical user interface. Programmatic access is crucial for automation, scripting, and managing AWS resources at scale. It involves the use of AWS access keys, specifically:

* **Access Key ID:** A unique identifier for an AWS user.
    
* **Secret Access Key:** A secret key associated with the Access Key ID.
    

Here's what you need to know about AWS programmatic access:

* **Purpose:** Programmatic access allows you to automate AWS tasks, integrate AWS services into your applications, and manage AWS resources using APIs (Application Programming Interfaces) and command-line tools.
    
* **Security:** Access keys must be kept secure, as they provide full access to your AWS resources. They should not be exposed or shared unnecessarily.
    
* **Usage:** AWS programmatic access is commonly used for tasks such as deploying and managing EC2 instances, automating data backups to S3, and invoking AWS Lambda functions.
    
* **Permissions:** Access to AWS resources is controlled through AWS Identity and Access Management (IAM) policies, which specify what actions a user or application can perform.
    

## ©️ AWS CLI (Command Line Interface)

**AWS CLI (Command Line Interface)** is a unified, command-line tool provided by AWS to interact with AWS services from the terminal or command prompt. It offers a powerful and efficient way to manage AWS resources, ideal for developers, administrators, and automation tasks. Here are the key aspects of AWS CLI:

* **Installation:** You can install AWS CLI on various operating systems, including Linux, macOS, and Windows. The installation process is straightforward.
    
* **Configuration:** To use AWS CLI, you must configure it with your AWS credentials, including the Access Key ID and Secret Access Key. You can also set default regions and output formats during configuration.
    
* **Commands:** AWS CLI provides a wide range of commands for managing AWS services. These commands are organized by AWS service and allow you to perform actions like creating EC2 instances, listing S3 buckets, configuring security groups, and much more.
    
* **Scripting and Automation:** AWS CLI is script-friendly, enabling you to create scripts and automate AWS tasks. This is particularly useful for infrastructure as code (IaC) deployments using tools like AWS CloudFormation.
    
* **Extensions:** AWS CLI can be extended with additional plugins and tools to enhance its functionality for specific use cases.
    
* **Cross-Platform:** AWS CLI is cross-platform, meaning you can use it on various operating systems with the same commands and syntax.
    
* **Access Control:** The AWS CLI respects AWS IAM permissions, ensuring that users and applications can only perform actions for which they have been granted access.
    

# ☁️Hands-On Practice

# Task-01: Create AWS\_ACCESS\_KEY\_ID and AWS\_SECRET\_ACCESS\_KEY from AWS Console

## Step 1: Create an IAM user

* Create an IAM user just like we created in previous blogs
    
* You can refer to this [blog](https://srdev.hashnode.dev/getting-started-with-aws) for the steps of creating an IAM user.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694266924327/9d097d43-9d8e-4f26-ab05-763882ad255c.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694266949888/1ca7bcb8-8e8a-4874-8853-941444d708d0.png align="center")
    

## Step 2: Save Access Key Credentials

* After the user is created, click on the user name and you will see all the information about the user
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694267172350/70556e4a-780f-429b-884c-b9762c954549.png align="center")
    
* Click on the security credentials.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694267192900/744b5036-a787-4ab4-aa31-c549069ff792.png align="center")
    
* Scroll down to the access key and click on Create Access Key
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694267210371/53b5127e-9318-43e5-8d8b-3ff76c6b41af.png align="center")
    
* Select Command Line Interface (CLI) then provide an optional tag
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694267238185/75b3afb8-f3c7-45de-8a0c-8530166342e5.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694267325063/04679433-057e-455c-bbe0-9d9ed6ca6924.png align="center")
    
* Now, you will see a confirmation screen. It will display the user's username and an option to download the CSV file containing the user's access key ID and secret access key.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694267346751/a15bda06-0ddf-4560-8e0f-2cd296975811.png align="center")
    
* Download the CSV file and store it securely. This file contains sensitive credentials and should not be shared or exposed.
    

# Task-02: Setup and install AWS CLI and configure your account credentials

## Step 1: Create an Instance

* Create an EC2 instance just like we created in the [previous blog](https://srdev.hashnode.dev/hands-on-practice-launching-an-ec2-instance-with-jenkins-and-iam-role-creation).
    
* In the Advance Details , to go User data and paste the below script to install
    
    aws-cli and click on launch instance.
    
    ```bash
    #!/bin/bash
    
    sudo apt-get update
    sudo apt-get install -y awscli
    sudo apt-get update
    ```
    
* Connect to the instance via SSH
    
* You can refer the [previous blog](https://srdev.hashnode.dev/hands-on-practice-launching-an-ec2-instance-with-jenkins-and-iam-role-creation).
    

## Step 2: Configure AWS CLI

1. After launching the instamce, you need to check the aws --version to confirm if aws-cli is installed or not and to configure it with the credentials you obtained earlier.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694267648618/4bfcb602-f45f-4e09-82f8-f21cc22cb92c.png align="center")
    
2. In your terminal, run the following command to configure AWS CLI:
    
    ```shell
    aws configure
    ```
    
3. You will be prompted to enter the following information:
    
    * AWS Access Key ID: Enter the Access Key ID from the CSV file you downloaded during Task-01.
        
    * AWS Secret Access Key: Enter the Secret Access Key from the CSV file.
        
    * Default region name: Enter the AWS region you want to use as the default (e.g., "us-east-1").
        
    * Default output format: You can leave this as "json" or choose another format.
        
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694267669994/5379345f-ad24-4c64-89eb-82f8cd1b22fc.png align="center")
    
4. After entering this information, the AWS CLI will be configured with your IAM user's credentials.
    

You have now successfully created an IAM user and configured AWS CLI on your local machine. You can use the CLI to interact with AWS services using the credentials of the IAM user you created.  
  
You can refer this [**blog**](https://www.bdrsuite.com/blog/aws-for-beginners-provisioning-iam-users-and-programmatic-access-in-aws-part-6/) for more understanding  
  
  

> I hope now you can configure your AWS CLI .  
> Stay tuned fo rmore content !!  
> Happy Learning :D