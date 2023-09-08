---
title: "Creating a High-Performance Web Environment on AWS with Load Balancing"
datePublished: Fri Sep 08 2023 14:58:15 GMT+0000 (Coordinated Universal Time)
cuid: clmaq29sx000208l2az55cxx5
slug: creating-a-high-performance-web-environment-on-aws-with-load-balancing
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1694183155857/bd70f8c1-973a-4e22-bce2-8bf3dfde20bc.png
tags: aws, devops, load-balancing, devops-articles, 90daysofdevops

---

# ☁️Introduction

In today's digital age, where websites and applications serve millions of users simultaneously, ensuring consistent performance and reliability is crucial. Load balancing is a fundamental technique that plays a vital role in achieving these objectives. In this beginner-friendly guide, we'll explore what load balancing is and delve into Amazon Web Services (AWS) Elastic Load Balancing (ELB) service, including its three types of load balancers: Application Load Balancer (ALB), Network Load Balancer (NLB), and Classic Load Balancer (CLB).

# ☁️What is Load Balancing?

Imagine a popular online store that experiences a sudden surge in traffic due to a flash sale. Without load balancing, a single server might become overwhelmed, leading to slow response times or even crashes. Load balancing is the solution to this problem. It involves distributing incoming traffic across multiple servers to ensure they work efficiently and remain available.

Load balancers act as traffic cops, directing users' requests to the least busy server in a cluster. This prevents any single server from getting overloaded, leading to a smoother and more responsive user experience.

# ☁️AWS Elastic Load Balancing (ELB)

Amazon Web Services (AWS) is a cloud computing platform offering a wide range of services to help businesses scale their applications and infrastructure. Elastic Load Balancing (ELB) is one such service provided by AWS, designed to automate and simplify the process of load balancing.

## Types of ELB Load Balancers

AWS Elastic Load Balancing offers three main types of load balancers, each tailored to different use cases.

### 1\. Application Load Balancer (ALB)

ALB operates at **Layer 7** of the OSI model, which means it can make routing decisions based on application-level information, such as HTTP/HTTPS headers. ALB is ideal for applications that require advanced routing and support for microservices.

**Key Features:**

* **Content-Based Routing:** ALB can route traffic based on the content of requests, making it suitable for hosting multiple websites or applications on the same set of servers.
    
* **WebSockets:** It supports WebSocket traffic, making it suitable for real-time applications like chat or gaming.
    
* **Path-Based Routing:** ALB can route requests based on the URL path, enabling you to host multiple services on a single set of servers.
    

### 2\. Network Load Balancer (NLB)

NLB operates at **Layer 4**, making it suitable for applications that require high throughput and low latency. It's often used for TCP/UDP-based services.

**Key Features:**

* **Ultra-Low Latency:** NLB is designed for extreme performance and is ideal for applications that need minimal processing delay.
    
* **Static IP Addresses:** It provides a static IP address for the load balancer, making it suitable for scenarios where IP address stability is crucial.
    
* **Support for IP Target Groups:** NLB allows you to route traffic to specific IP addresses, which can be useful for specialized setups.
    

### 3\. Classic Load Balancer (CLB)

CLB is an older load balancer type operating at **Layer 4**, primarily suited for applications that require basic load balancing features. While it lacks some of the advanced capabilities of ALB and NLB, it can still be effective for certain use cases.

**Key Features:**

* **Simple Configuration:** CLB is straightforward to set up and configure, making it suitable for basic load-balancing needs.
    
* **HTTP and TCP Load Balancing:** It supports both HTTP/HTTPS and TCP/SSL load balancing.
    

# Task 1: Setting up EC2 Instances with Apache Web Server

## Step 1: Launch Two EC2 Instances

* Log in to your AWS Management Console.
    
* Navigate to the EC2 service.
    
* Click on "Instances" in the left-hand menu and then click the "Launch Instances" button.
    
* Select an Ubuntu AMI as your instance type. Choose an appropriate instance type based on your requirements.
    
* In the "Configure Instance Details" section, under "Advanced Details," paste the following User Data script to install Apache and modify the index.html file:
    

```bash
#!/bin/bash
apt-get update -y
apt-get install apache2 -y
echo "Hi there, I'm Tony Stark, known to some as Iron Man.
Welcome to the Multiverse, where possibilities are endless!" > /var/www/html/index.html
```

* For the second instance, use the following User Data script:
    

```bash
#!/bin/bash
apt-get update -y
apt-get install apache2 -y
echo "<h1 style='font-weight: bold;'> Welcome, Marvel Superfan! </h1><p>You've stumbled upon an undisclosed high-tech facility, where dreams come true!</p>" > /var/www/html/index.html
```

* Complete the instance launch process, including configuring security groups and key pairs as needed.
    
* We have done the same in the previous blogs, you can refer it here if you get stuck in the above steps: [blog](https://srdev.hashnode.dev/hands-on-practice-launching-an-ec2-instance-with-jenkins-and-iam-role-creation)
    

## Step 2: Copy Public IP Addresses

* Once the instances are running, go to the EC2 dashboard.
    
* Locate the two instances you just launched, and under the "Description" tab, copy the "Public IPv4 address" for each instance.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694174219062/6e4415e6-a823-48f7-b08e-822c0685739d.png align="center")

## Step 3: Access Apache Web Servers

* Open a web browser.
    
* Paste the "Public IPv4 address" of the first instance **\[ Marvel\]** into the address bar and press Enter. You should see a webpage displaying the content.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694174158106/cedadd75-8d71-40dd-a7ca-179654909711.png align="center")
    
* Similarly, paste the "Public IPv4 address" of the second instance **\[Marvel-Fan\]** into the address bar and press Enter. You should see a webpage displaying the content.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694174253292/730c68a3-a749-4633-a190-13f3133f91a4.png align="center")
    

# Task 2: Creating an Application Load Balancer (ALB)

## Step 1: Create an Application Load Balancer

* Log in to your AWS Management Console.
    
* Navigate to the EC2 service.
    
* In the left-hand menu, under "Load Balancing," select "Load Balancers."
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694179422529/2310a7f3-fd9b-443c-ab00-7193e5cad756.png align="center")
    
* Click the "Create Load Balancer" button.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694179431936/c86ed69c-d86a-4d04-ab50-4947eb5e0bcd.png align="center")
    
* Choose "Application Load Balancer" as the load balancer type.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694180062242/69a47f15-8f26-4ccb-9625-292c25ed1f49.png align="center")
    
* Configure your ALB settings, including a name
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694180165169/46adf821-b82a-41b1-9d0a-ae8beeef9fd3.png align="center")
    

## Step 2: Creating Target Group

* Now, Scroll down to the Networking and Mapping where you have to select the VPC and the subnet. Click on Create Target Groups.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694181150623/b7911cea-e4aa-4a99-8e78-a5dc92fc1913.png align="center")
    
* Select Instances in the basic configuration, then provide the target group name
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694181299656/fb6a53d6-1635-4f8a-b019-0ff6c6cfdbbd.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694181317498/c8566c99-cf4c-45f8-a03a-b2eb958f5556.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694181369889/61b62af7-1fdc-4f8e-845b-5a11705a1494.png align="center")
    
* After clicking on next you have to register targets which are your instances, select them and click on include as pending below.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694181444714/8631c32c-6c9a-491a-97e2-87c6710a3f07.png align="center")
    
* Review the target and click on Create target group
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694181483272/64551bfc-1df4-48e7-a17c-c2c4a9979e30.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694181508638/243295f6-4b61-47f1-a32f-5587d84fcfc2.png align="center")
    
* Go back to the previous tab of creating load balancer, in the network mapping section, check mark on all the mappings.
    

## Step 3: Creating a Security Group

* Scroll down, you will find security groups.
    
* By default AWS provides you a group But it is Good practice to create new one so click on Create New Security Group in the Security Group Section. It will take you to the new tab on the browser.
    
* **Click the "Create Security Group" button.**
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694180357131/99a3b115-9ba5-40dc-9953-ada9586d097c.png align="center")

* Now, it will redirect you to the new page where you have to provide the group name, and description and set inbound rules.
    
* Set Inbound Rule to HTTP port 80 keep rest all by default and click on Create Group. and Click on Create.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694180521672/7989fa9e-abb2-4969-b2ed-10ad07e2c486.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694180531191/d6b93286-355a-4ab5-bfb9-f1b881d294e1.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694180614415/26a40528-961a-4f5e-afc3-6c22c85841c9.png align="center")
    
* Go back to the previous tab of Creating load balancer, Security group section and refresh the list, Select the group that you have created just now.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694180711767/d5be944a-d60a-4661-8f48-54fc2d6f177b.png align="center")
    
* Scroll down to the listening and Routing Section :
    
* Refresh the list where it is asking for the target group and select the target group that we have created before in the network mapping section
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694182040361/67c7f215-09bb-4553-b3df-0e6a18f2f236.png align="center")
    
* Check the summary and click on Create on Load Balancer
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694182097070/dffe8c9a-c66e-46c9-884f-ab991623b499.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694182140260/55fb412f-4859-40d0-a3d8-7c3d93b87dbb.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694182280297/b8136393-80be-4f6c-b6b1-4c1fad8f8538.png align="center")
    
* Copy the DNS in your browser , and refresh to check the output.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694182598282/989ea673-6e56-4958-aefa-0bb9c8ffa184.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694182604157/4fcce058-19af-475c-af14-1980fb602363.png align="center")
    

> I hope you understood the concept of load balancer
> 
> Happy Learning :D