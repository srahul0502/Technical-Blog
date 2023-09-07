---
title: "Hands-On Practice: Launching an EC2 Instance with Jenkins and IAM Role Creation"
datePublished: Thu Sep 07 2023 13:28:13 GMT+0000 (Coordinated Universal Time)
cuid: clm97enja000m0amvbzeg7bd0
slug: hands-on-practice-launching-an-ec2-instance-with-jenkins-and-iam-role-creation
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1694092874142/d088506b-4655-4064-b362-8530b328caff.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1694093270040/bc700b95-ce36-4fc6-9a6a-685e31e4c180.png
tags: aws, devops, devops-articles, 90daysofdevops, 90daysofdevops-chanllenge

---

# AWS:

Amazon Web Services is one of the most popular Cloud Provider that has free tier too for students and Cloud enthutiasts for their Handson while learning (Create your free account today to explore more on it).

You can read more about it from [here](https://aws.amazon.com/what-is-aws/)

## User Data in AWS:

* When you launch an instance in Amazon EC2, you have the option of passing user data to the instance that can be used to perform common automated configuration tasks and even run scripts after the instance starts. You can pass two types of user data to Amazon EC2: shell scripts and cloud-init directives.
    
* You can also pass this data into the launch instance wizard as plain text, as a file (this is useful for launching instances using the command line tools), or as base64-encoded text (for API calls).
    
* This will save time and manual effort everytime you launch an instance and want to install any application on it like apache, docker, Jenkins etc.
    
* You can read more about it from [here](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/user-data.html)
    

# IAM:

AWS Identity and Access Management (IAM) is a web service that helps you securely control access to AWS resources. With IAM, you can centrally manage permissions that control which AWS resources users can access. You use IAM to control who is authenticated (signed in) and authorized (has permissions) to use resources.

You can read more about itfrom [here](https://docs.aws.amazon.com/IAM/latest/UserGuide/introduction.html)

# Hands-On Practice :

### **Task 1: Launch EC2 Instance with Pre-installed Jenkins and Verify Accessibility**

**Step 1: Log in to AWS Console**

Log in to your AWS Management Console using your AWS account credentials.

**Step 2: Launch EC2 Instance**

Go to the EC2 Dashboard.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694091668654/36520659-2cd8-4c07-a2a1-6535125b1a71.png align="center")

Click on the "Launch Instance" button to create a new EC2 instance.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694091682918/efa97fef-3e8a-49e0-b716-ca26f7580b28.png align="center")

**Step 3: Choose an Amazon Machine Image (AMI)**

Select an AMI in which you want Jenkins to be pre-installed. You may need to create a custom AMI with Jenkins installed if one is not available.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694091724348/de6b1289-4b21-41d1-9e4f-0361c6ed7e40.png align="center")

**Step 4: Choose an Instance Type**

Select the instance type that suits your needs. For Jenkins, a t2.micro instance is often sufficient for small to moderate workloads.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694091736109/219919f5-a8bb-4ff3-9654-bf24f3178532.png align="center")

**Step 5: Configure Instance Details**

In the "Configure Instance Details" section, select the ree tier one and select the key pair which you have created before , if not you can create one by clicking on create keypair

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694091829760/87563a5d-7f4b-40a3-874a-697852c5243e.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694091838632/a953e255-6e99-49a6-8b7e-ef51688b2aea.png align="center")

**Step 6: Add Storage**

Configure the storage size and type for your EC2 instance. Ensure it has enough space for Jenkins and your projects.

**Step 7: Add Tags (Optional)**

You can add tags to your instance for easier identification.

**Step 8: Configure Security Group**

Create or select a security group that allows incoming traffic on port 8080 (default Jenkins port) so you can access Jenkins via the web browser.

**Step 9: Configure User Data**

In the "Configure Instance" step, scroll down to the "Advanced Details" section.

In the "User data" field, paste the script that installs Jenkins and any other necessary configurations.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694091856320/b976f871-5499-485c-abe6-676bddc9d73f.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694091873097/67d34723-8463-4bff-b0a9-7ac1478d3293.png align="center")

Here's the script , that installs jenkins , paste this in the user data , or you can create a .sh file and upload it here .

```bash
#!/bin/bash

sudo apt-get update
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

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694091971460/ea575efe-7687-4a1b-9886-678ea5642a95.png align="center")

**Step 10: Go back to the Network Security and Add the port**

Here we go back to the network security and click on edit and scroll down , click on Add rules .

Add port 8080 , as it's the default port on which jenkis runs , Under source type select Anywhere or My IP.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694092108565/de6f11fd-fd5e-4b05-b2b9-b95fd7407f80.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694092129975/fd13ca1d-a4f3-45ab-87aa-eb88fd86660f.png align="center")

Alternative of Step 10 :

**Step 10: Configure Security Group Rules**

In the EC2 Dashboard, go to the "Security Groups" section, and edit the security group associated with your EC2 instance.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694092297019/a68776cf-b349-4ff0-ac98-e6913e542a2c.png align="center")

Add an inbound rule to allow incoming traffic on port 8080.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694092307305/9209ee22-95d7-417b-aa9d-044f85060fb3.png align="center")

**Step 11: Launch the Instance**

Click "Launch Instances" to create the EC2 instance.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694092323412/2546ed5d-f641-4ed8-aa50-628fd12c80df.png align="center")

**Step 12: Wait for Instance to Start**

Wait for the instance to be created and initialized. You can monitor the progress in the EC2 Dashboard.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694092351096/471cfb32-4ba4-42c8-9ff8-a1715acf2c97.png align="center")

**Step 13: Access Jenkins**

Once the instance is running, note down its public IP address.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694092351096/471cfb32-4ba4-42c8-9ff8-a1715acf2c97.png align="center")

**Step 16: Access Jenkins in Browser**

Open a web browser and enter the public IP address of your EC2 instance followed by ":8080" (e.g., [`http://public_ip:8080`](http://public_ip:8080)) to access the Jenkins web interface.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694092403118/9f19432d-d47d-418b-a183-3266796437aa.png align="center")

**Step 17: Complete Jenkins Setup**

Follow the on-screen instructions to complete the initial setup of Jenkins.

By following these steps, you'll have launched an EC2 instance with Jenkins pre-installed, including the step to configure the user data script for installation, and verified its accessibility through a web browser.

### **Task 2: Understanding AWS Identity and Access Management (IAM) and Creating Roles**

**Step 1: Log in to AWS Console**

* Open your web browser and navigate to the AWS Management Console ([https://aws.amazon.com/](https://aws.amazon.com/)).
    
* Log in with your AWS account credentials.
    

**Step 2: Access the IAM Dashboard**

* From the AWS Management Console, click on the "Services" menu and select "IAM" under the "Security, Identity, & Compliance" section.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694092439525/196beb34-a071-4eb0-9cd3-cf054efe167c.png align="center")
    

**Step 3: Create the DevOps-User Role**

* In the IAM Dashboard, click on "Roles" in the left navigation pane.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694092460183/0d0ac5b4-15c0-4be6-b34f-6a3ec9fdc6ff.png align="center")
    
* Click the "Create role" button.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694092470002/97937371-05be-42af-a6eb-97ba95cda5d5.png align="center")
    
* In the "Select type of trusted entity" section, choose "AWS service" as the trusted entity type.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694092482580/23c5174c-94c5-4afc-99d6-b8c4529fd3ec.png align="center")
    
* In the "Choose the use case" section, you can either select a predefined use case policy or create a custom policy. Since this is for a DevOps role, you may want to select the "EC2" use case, which allows EC2 instances to assume this role. Click "Next: Permissions" when ready.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694092502840/a1a19b51-9251-4e65-8db3-032f183b1a80.png align="center")
    
* In the "Permissions" section:
    
    * Search for and select policies that grant permissions relevant to your DevOps-User role. This may include permissions for managing AWS resources and services required for your DevOps processes.
        
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694092517241/44d8b3e9-98d9-4340-b96b-360fdf9aa231.png align="center")
    
* Provide a meaningful name and description for the role, such as "DevOps-User."
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694092709037/642d4d00-a502-4834-b418-7a015b177054.png align="center")
    
* Click "Create role" to create the DevOps-User role.
    

**Step 4: Create the Test-User Role**

* Follow the same steps as above to create a Test-User role, but this time, customize the name and permissions to align with the needs of your Test-User role.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694092604709/bb88d857-db69-4044-a478-b02d403a1f17.png align="center")
    

**Step 5: Create the Admin Role**

* Follow the same steps as above to create an Admin role, but customize the name and permissions to align with the needs of your Admin role. Admin roles typically have more extensive permissions for managing AWS resources.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694092615437/accc5fff-43da-47a3-b179-6b787b4b44e9.png align="center")
    

**Step 6: Verify and Review Roles**

* After creating all three roles, review the list of roles in the IAM Dashboard to ensure that DevOps-User, Test-User, and Admin have been successfully created with their respective permissions.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694092622324/83cd39c1-215e-4cb4-862b-51e3255c285e.png align="center")
    

You have now successfully created three IAM roles: DevOps-User, Test-User, and Admin. Each of these roles can be associated with specific AWS resources or users, allowing fine-grained access control within your AWS environment. Be sure to manage the permissions for each role according to the responsibilities and access requirements of your DevOps, testing, and administrative teams.