---
title: "A Comprehensive Guide to Building and Deploying a Three-Tier Architecture on AWS"
datePublished: Tue Oct 17 2023 07:48:33 GMT+0000 (Coordinated Universal Time)
cuid: clnu0vwpl000009mf2chgcc63
slug: a-comprehensive-guide-to-building-and-deploying-a-three-tier-architecture-on-aws
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1697528757753/61ced295-7cf3-4023-9037-16af3b265072.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1697528876203/a3d5a6d1-29bf-4bb1-a53f-6acf770363aa.png
tags: docker, aws, devops, terraform, 90daysofdevops

---

# 🏗️ Introduction

In today's fast-paced digital landscape, robust and scalable applications are a necessity. A three-tier architecture is a popular design pattern for creating modern applications, and Amazon Web Services (AWS) provides a powerful platform to bring this architecture to life. In this comprehensive guide, we'll take you through the entire process, step by step. You'll learn how to clone the necessary code, set up an AWS account, install Docker and Terraform, build Docker images, and deploy a three-tier architecture.

# 🏗️ Prerequisites

Before we dive into the technical aspects, it's essential to ensure you have the prerequisites in place:

* A Linux system
    
* Docker and Terraform installed
    
* An AWS account
    

# 🏗️ AWS Configuration

To work with AWS, you'll need an AWS account. If you don't have one, head over to the [AWS Console](https://aws.amazon.com/console/) to create an account. Ensure you have your AWS Access Key ID and Secret Access Key ready for AWS CLI configuration. Certainly, here are the installation and configuration steps for the AWS CLI in proper markdown format:

To work with AWS services from your command line, you can install and configure the AWS Command Line Interface (CLI) on your Linux system using the following commands:

**Step 1: Install AWS CLI**

First, open a terminal and install the AWS CLI by running the following command:

```bash
sudo apt install awscli
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697526932608/c8e12622-7ea8-4709-ba10-84b4b4bbd716.png align="center")

**Step 2: Configure AWS CLI**

After installing the AWS CLI, you need to configure it with your AWS credentials. Run the following command:

```bash
aws configure
```

This command will prompt you to enter the following information:

* **AWS Access Key ID:** Enter your unique AWS Access Key ID.
    
* **AWS Secret Access Key:** Provide the secret key associated with your AWS Access Key ID.
    
* **Default region name:** Specify the default AWS region you want to use (e.g., `us-east-1`).
    
* **Default output format:** You can keep the default setting as JSON unless you have a specific preference.
    

Example:

```bash
AWS Access Key ID: YourAccessKey
AWS Secret Access Key: YourSecretKey
Default region name: us-east-1
Default output format: json
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697526504573/66d7e26c-42c0-431d-844e-9a0d960d1a69.png align="center")

After completing these steps, you have successfully installed and configured the AWS CLI on your Linux system. It is now ready to interact with AWS services directly from your command line.

# 🏗️ Understanding the Three-Tier Architecture

A three-tier architecture is a common design pattern for modern applications. It comprises three interconnected tiers, each serving a specific purpose:

1. **Web or Presentation Tier**
    
    The web or presentation tier is the user's initial point of contact. This tier is responsible for receiving user requests from web browsers and presenting data from other tiers. In AWS, it's often hosted on publicly accessible EC2 instances and load balancers.
    
2. **Application Tier**
    
    The application tier contains the core business logic and handles the bulk of the processing. It manages user requests from the presentation tier and interacts with the database tier to retrieve or store data. In our architecture, this tier is represented by private EC2 instances.
    
3. **Database Tier**
    
    The database tier is responsible for storing and managing the data processed in the application tier. It comprises database servers that ensure secure and reliable data storage. In this guide, we use Amazon RDS (Relational Database Service) to provide data persistence and reliability.
    

# 🏗️ Deploying Three-Tier Architecture

With a clear understanding of the architecture, let's delve into the AWS components that constitute our three-tier setup:

* **Virtual Private Cloud (VPC)**: Set up a VPC to provide network isolation and control over your resources.
    
* **Public Subnets**: Create public subnets to house the public-facing components, including public Load Balancers and presentation tier EC2 instances.
    
* **Private Subnets**: Configure private subnets for hosting your application and database tiers. These subnets enhance security by isolating them from the public internet.
    
* **Auto Scaling Groups**: Create two Auto Scaling Groups: one for the presentation tier and another for the application tier. Auto Scaling dynamically adjusts instance counts based on traffic and resource requirements.
    
* **Security Groups**: Define five Security Groups to manage inbound and outbound traffic rules, ensuring authorized communication within your architecture.
    
* **Load Balancers**: Utilize two Load Balancers. One is public-facing to distribute incoming traffic to the presentation tier instances, while the other is private-facing, routing traffic to the application tier instances, enhancing availability and reliability.
    
* **Private EC2 Instances**: Representing the application tier, these instances reside in private subnets and handle core application logic while remaining hidden from the public internet.
    
* **Public EC2 Instances**: Public EC2 instances form the presentation tier, located in public subnets, and serve as the user interaction layer.
    
* **NAT Gateways**: Set up two NAT Gateways associated with private subnets. They allow private instances to initiate outbound connections to the internet while maintaining their isolation.
    
* **Elastic IP Addresses**: Associate one Elastic IP address with each NAT Gateway to provide static, publicly routable addresses, ensuring reliable connectivity.
    
* **RDS Instance**: The RDS instance serves as the database tier, offering a managed relational database service that is highly available and scalable, ensuring data persistence and reliability.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697531188973/9fd7b066-575f-485e-a504-b2f6e17e69c3.gif align="center")

# 🏗️ Repository Setup

To get started, clone the repository that contains all the necessary configurations and scripts:

```bash
git clone https://github.com/srahul0502/terrform_threetierarch
```

After cloning, navigate to the repository directory:

```bash
cd terrform_threetierarch
```

# 🏗️ Docker Installation

Docker is a fundamental tool for containerizing your application. Make sure Docker is installed and configured correctly on your Linux system.

Follow these steps to install Docker on a Linux system.

1. **Install Docker:**
    
    Update your package list and install Docker using the following commands:
    
    ```bash
    sudo apt update
    sudo apt install docker.io
    ```
    
2. **Add Your User to the Docker Group:**
    
    Add your user to the `docker` group to allow running Docker commands without `sudo`. Replace `$USER` with your actual username.
    
    ```bash
    sudo usermod -aG docker $USER
    ```
    
    After making this change, you may need to log out and log back in or restart your session for group membership changes to take effect.
    
3. **Start and Enable Docker:**
    
    Start the Docker service and configure it to start at boot:
    
    ```bash
    sudo systemctl start docker
    sudo systemctl enable docker
    ```
    
4. **Verify Docker Installation:**
    
    To ensure that Docker is correctly installed and your user has Docker access, check the Docker version:
    
    ```bash
    docker --version
    ```
    
    This command should display the Docker version.
    
5. **Test Docker Installation:**
    
    You can test Docker by running a simple container, such as the "hello-world" container:
    
    ```bash
    docker run hello-world
    ```
    

Docker should download and run the "hello-world" container as a confirmation that Docker is functioning correctly.

Make sure to refer to the official Docker documentation or the documentation specific to your Linux distribution if you encounter any issues, as the exact steps may vary based on your distribution.

Refer to this [blog](https://srdev.hashnode.dev/series/docker) for complete understanding and tutorial on installing docker

# 🏗️ Terraform Installation

Terraform is your infrastructure as code (IaC) tool. Install the Terraform CLI on your Linux system.

Follow these steps to install Terraform on a Linux machine:

1. Update your package list to ensure you have the latest information about available packages:
    
    ```bash
    sudo apt-get update
    ```
    
2. Install the `unzip` utility to extract the Terraform archive:
    
    ```bash
    sudo apt-get install -y unzip
    ```
    
3. Download the Terraform binary for your system (replace the URL with the latest version if needed):
    
    ```bash
    wget https://releases.hashicorp.com/terraform/0.12.26/terraform_0.12.26_linux_amd64.zip
    ```
    
4. Extract the downloaded Terraform binary:
    
    ```bash
    unzip terraform_0.12.26_linux_amd64.zip
    ```
    
5. Move the Terraform binary to a directory in your system's PATH, making it accessible from anywhere in your terminal:
    
    ```bash
    sudo mv terraform /usr/local/bin/
    ```
    
6. Verify the installation by checking the Terraform version:
    
    ```bash
    terraform --version
    ```
    

This should display the installed Terraform version, confirming that the installation was successful.

# 🏗️ Give Permission to setup-ecrs.sh

Once you've cloned the repository, navigate to its root directory and grant execute permission to the setup-ecrs.sh script using this command:

```bash
chmod +x setup-ecrs.sh
```

# 🏗️ Create ECR Repository and Send Images to ECR

Now, you're ready to create an Amazon Elastic Container Registry (ECR) repository and push Docker images to it.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697527848130/e6c95bd7-051e-4404-9043-c6ded5dbdb62.png align="center")

**Amazon Elastic Container Registry (ECR)** is a fully managed Docker container registry provided by Amazon Web Services (AWS). It allows you to easily store, manage, and deploy Docker container images. ECR is integrated with other AWS services and provides a secure and scalable solution for container image management.

Ensure that Docker is installed and configured properly, and then run the following script:

```bash
./setup-ecrs.sh
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697528078566/b48274f2-f101-4bf1-b001-c8d3f04d5241.png align="center")

This script will build and push Docker images to the ECR repository, getting you ready for the next steps.

# 🏗️ Terraform Setup

**Navigate to the terraform folder within the cloned repository:**

```bash
cd terraform
```

**Start by initializing Terraform:**

```bash
terraform init
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697528095121/b6f4d48a-2a3b-4a85-ac56-a37470cff6bf.png align="center")

This command initializes the working directory, downloading necessary provider plugins and modules.

To preview the changes Terraform will make, run:

```bash
terraform plan
```

The plan command shows you a summary of the resources Terraform will create, modify, or delete.

To apply the changes and create the infrastructure on AWS, execute:

```bash
terraform apply
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697528149006/0cdef51c-4ec8-447d-9284-82749901c010.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697528172764/2bed9249-0582-4224-9e83-304bbc766f06.png align="center")

Follow the prompts, and confirm with a "yes" when prompted.

And that's it! You've successfully executed the provided steps to clone the code, set up an AWS account, install Docker and Terraform on Windows, prepare the ECR repository, and deploy the infrastructure using Terraform.

Let's check if the components are created or not

**Instances :**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697528329258/9a44323a-92f3-47ea-97cd-e5cf23f8a30e.png align="center")

**RDS :**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697528342438/6a5911f5-48bc-48f6-bca4-99c79c8ec6f0.png align="center")

**Load Balancer :**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697528352285/679a1082-8179-4327-8e43-231a442ccef2.png align="center")

**Auto Scaling Group (ASG) :**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697528371308/c9ddcbee-fa52-4309-8f25-c5c2e7f2766b.png align="center")

**NAT Gateway :**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697528383191/1a1af7ab-9aef-4e0e-820c-ecf55e4e88a1.png align="center")

You can refer to this [blog](https://srdev.hashnode.dev/series/terraform) to learn about terraform

# 🏗️ Testing the Application

To test the deployed application, follow these steps:

**1\. Hit the Front End Load Balancer**

Open your web browser and navigate to the Front End Load Balancer URL, which should look something like:

```bash
front-end-lb-**********.us-east-1.elb.amazonaws.com/
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697528207666/965065c0-34ec-4e77-b5a1-13556c6a668a.png align="center")

**2\. Request to the Presentation Layer**

Request to the presentation layer, which forwards the requests to the application layer via the internal Load Balancer. This action will create a table called "users" and add two users to the table.

Use the following URL:

```bash
front-end-lb-**********.us-east-1.elb.amazonaws.com/init
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697528237851/be557e02-8f59-4b62-8be9-7c02f5667240.png align="center")

**3\. View the Users Table**

To view the "users" table, you can call the following URL:

```bash
front-end-lb-**********.us-east-1.elb.amazonaws.com/users
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697528263731/7a1d724d-606c-403c-b10f-398a49b04188.png align="center")

# 🏗️ Deleting the Architecture

Once you've completed your testing and want to delete the architecture, use Terraform to do so:

```bash
terraform destroy
```

Follow the prompts, and confirm with a "yes" when prompted.

And that's it! You've successfully executed the provided steps to set up and test a three-tier architecture on AWS. When you're done, you can easily tear down the infrastructure using Terraform.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697528478005/ab3ea727-0075-4e6e-b769-a793d1d8c5ae.png align="center")

> You now possess the skills to create, manage, and test a three-tier architecture on AWS, ready to tackle future cloud projects.
> 
> Happy architecting!