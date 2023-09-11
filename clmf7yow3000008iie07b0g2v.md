---
title: "Amazon Simple Storage Service (Amazon S3): Your Essential Guide to Cloud Storage"
datePublished: Mon Sep 11 2023 18:30:25 GMT+0000 (Coordinated Universal Time)
cuid: clmf7yow3000008iie07b0g2v
slug: amazon-simple-storage-service-amazon-s3-your-essential-guide-to-cloud-storage
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1694455482640/27a88686-e375-45db-98c8-7dc77b735100.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1694457012809/f110b93a-6adf-46ff-9fd2-4c29f3160820.png
tags: aws, devops, s3, devops-articles, 90daysofdevops

---

# What is Amazon S3 ⁉️

Amazon Simple Storage Service, commonly known as Amazon S3, is like your digital storage unit in the cloud. It's a super versatile, secure, and scalable way to store and manage your data. Whether you're a beginner or a pro, let's dive into the world of Amazon S3 using simple examples.

**1\. Buckets: Your Virtual Storage Containers**

Think of an S3 bucket as a virtual container or a folder in the cloud where you can store your files. Each bucket has a unique name, and you can create as many as you need.

**Example:** Imagine you have a digital camera, and you want to store your photos securely. You can create an S3 bucket named "MyPhotoAlbum" to keep all your pictures.

**2\. Objects: Your Digital Assets**

Objects in S3 are like the individual files you store within your buckets. These can be anything from photos and videos to documents and database backups.

**Example:** Inside your "MyPhotoAlbum" bucket, you can have objects like "vacation.jpg" or "birthday.mp4."

**3\. Storage Classes: Choose Based on Your Needs**

Amazon S3 offers different storage classes to match your data's access patterns and cost requirements:

* **Standard**: For frequently accessed data.
    
* **Intelligent-Tiering**: Automatically moves objects between different storage classes based on changing access patterns.
    
* **Glacier**: For long-term archive storage with retrieval times from minutes to hours.
    

**Example:** If you have business data that's rarely accessed, you can save costs by using the "Glacier" storage class.

**4\. Permissions: Keep Your Data Secure**

You can control who can access your S3 buckets and objects using Access Control Lists (ACLs) and Bucket Policies. This ensures your data's privacy and security.

**Example:** You want to share your vacation photos with your family, so you give them read access to the "MyPhotoAlbum" bucket.

**5\. Versioning: Protect Your Data**

S3 allows you to enable versioning, which keeps multiple versions of an object. This helps prevent accidental deletions or overwrites.

**Example:** You accidentally delete a photo. With versioning enabled, you can easily recover the previous version.

**6\. Data Transfer: Easy Upload and Download**

You can upload and download your data to and from S3 using the AWS Management Console, AWS CLI, SDKs, or third-party tools.

**Example:** You use the AWS CLI to upload your latest photos to the "MyPhotoAlbum" bucket.

**7\. Data Lifecycle: Automate Data Management**

S3 allows you to create rules for automating data management, like moving objects to cheaper storage classes or deleting old files.

**Example:** You set a rule to move files older than one year to the "Glacier" storage class to save costs.

**8\. Logging and Monitoring: Keep an Eye on Your Data**

Amazon S3 provides tools for monitoring and logging, helping you track who's accessing your data and when.

**Example:** You use S3's logging feature to audit access to your sensitive business documents.

**9\. Cross-Region Replication: Disaster Recovery**

You can replicate your S3 objects to another AWS region for disaster recovery and data availability.

**Example:** You replicate your important financial data from your primary AWS region to a backup region.

**10\. Integration: S3 Works with Everything**

Amazon S3 seamlessly integrates with other AWS services like AWS Lambda, Amazon Redshift, and AWS Glue, making it a central part of your cloud ecosystem.

**Example:** You use AWS Lambda to trigger a workflow whenever a new file is uploaded to your S3 bucket.

So, whether you're storing personal photos, running a business, or managing critical data, Amazon S3 has you covered. It's the Swiss Army knife of cloud storage, providing durability, scalability, security, and flexibility for all your data needs. Dive in and start exploring the world of Amazon S3 today!

# ☁️Hands-On Practice

## **Task 01: Setting Up an EC2 Instance, S3 Bucket, and SSH Connection**

Step 1: Create an EC2 Instance

* I hope you know how to create an EC2 Instance by now
    
* You refer this [blog](https://srdev.hashnode.dev/hands-on-practice-launching-an-ec2-instance-with-jenkins-and-iam-role-creation) to understand how to create an EC2 instance
    

Step 2: **Create an S3 Bucket and Upload a File**

1. **Log in to AWS Management Console**:
    
    * If you're not already logged in, log in to the AWS Management Console.
        
2. **Navigate to S3**:
    
    * Go to the S3 service by clicking on "Services" in the top left corner and selecting "S3" under the "Storage" category.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694449605124/57a5eb9b-9099-476b-99aa-0525ea325612.png align="center")
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694449622184/4f9b90f9-bc96-4aa4-a038-64a3711d66ce.png align="center")
        
3. **Create a Bucket**:
    
    * Click the "Create bucket" button.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694449632712/93b457b7-c58d-4af8-a04b-207121adbe80.png align="center")
        
    * Follow the prompts to configure your bucket, including choosing a unique bucket name, selecting a region, and configuring any other desired settings.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694449641994/74390bda-999d-4acf-a033-6b73fd37761c.png align="center")
        
    * Click "Create bucket."
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694450102200/8d2da128-0f22-45ce-ab11-318adefd46d9.png align="center")
        
4. **Upload a File**:
    
    * After creating the bucket, click on the bucket name to enter it.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694450102200/8d2da128-0f22-45ce-ab11-318adefd46d9.png align="center")
        
    * Click the "Upload" button.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694450130459/ffad7836-d451-4d22-87ea-50dd1dbdb39c.png align="center")
        
    * Select the file you want to upload from your local computer.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694450146167/421523cf-c511-485b-8a5b-8079bac1348a.png align="center")
        
    * Click "Upload" again to upload the file to the bucket.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694450175995/2ae322b9-d9f6-43eb-a75c-fb62ef00a9f5.png align="center")
        
    
    Step 3: **Access the File from the EC2 Instance using AWS CLI**
    
    1. **Install AWS CLI on your EC2 Instance**:
        
        * If AWS CLI is not already installed on your EC2 instance, you can do so by running the following commands:
            
            ```bash
              sudo apt-get update
              sudo apt-get install -y awscli
              sudo apt-get update
            
            # check verion
            aws --version
            ```
            
            ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694451809256/7a70f1a7-cf33-408c-9c26-691d951a7878.png align="center")
            
        
        **Configure AWS CLI**:
        
        * Run the `aws configure` command and provide your AWS Access Key ID, Secret Access Key, default region name, and output format when prompted. You can find these credentials in your AWS account.
            
            ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694451818129/8ddc7c35-cffe-4d15-b53d-705f6070cb7d.png align="center")
            
    2. **Download the File from S3**:
        
        * Use the `aws s3 cp` command to download the file from your S3 bucket to your EC2 instance. For example:
            
            ```bash
            aws s3 cp s3://your-bucket-name/your-file-name /path/to/destination/on/ec2
            ```
            
        
        * Replace `your-bucket-name` with the actual bucket name and `your-file-name` with the name of the file you uploaded. Specify the desired destination path on your EC2 instance.
            
            ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694451877612/4d93ac35-d447-439d-8151-d1a437e2108a.png align="center")
            
    
    Now, you've completed the tasks of launching an EC2 instance, creating an S3 bucket, uploading a file to it, and accessing that file from the EC2 instance using AWS CLI.
    

## Task 02: EC2 Snapshot, New Instance Launch, S3 File Download, and Content Verification

### **Part 1: Creating an EC2 Snapshot and Launching a New Instance**

1. **Log in to AWS Console**: Sign in to your AWS Management Console.
    
2. **Navigate to EC2**: Access the Amazon EC2 service in the AWS Console.
    
3. **Select EC2 Instance**: Choose the EC2 instance for which you want to create a snapshot.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694451897447/cbe7cb0c-fb88-47cb-be53-01bd47b2d1ed.png align="center")
    
4. **Create Snapshot**:
    
    * Right-click on the selected instance or use the "Actions" dropdown.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694451911695/6c3bd358-2d61-45cc-92d4-7c114d28dd9c.png align="center")
        
    * Configure the snapshot by setting up the resource type to instance , select the instance you want to snap. Then click on create snapshot
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694453533318/6beffc0a-aaad-4161-9e81-ee436aae2736.png align="center")
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694453607123/b8769d37-8a4a-4ec7-9271-c556c842634b.png align="center")
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694453619901/ec53f1ed-a0bc-4c7f-bff1-550c452d7353.png align="center")
        
    * Select the snapshot and go to actions , select create image from snapshot to create an AMI
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694453981945/b334e5d1-cc2d-44ec-8640-cb6c855759d8.png align="center")
        
5. **Configure Image**: In the "Create Image" wizard, provide a name and description for the image. You can also add tags if necessary.
    
    Provide name and description for the image and click on create image.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694453856104/f49b336c-7283-4799-8d35-21eec5b7273b.png align="center")
    
6. **Create Snapshot**: Click the "Create Image" button. This initiates the snapshot creation process. Wait for it to complete.
    
    Select "Create Image (EBS AMI)" or "Create Image."
    
    * ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694454049988/b62a7cc1-e7ec-48dc-88b7-799b22ebca3b.png align="center")
        
7. **Navigate to AMIs**: Once the snapshot is created, go to the "AMIs" section on the left sidebar of the EC2 Dashboard.
    
    Go to the AMI section EC2 &gt; AMI (check the left hand side bottom panel)
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694455169891/f5347732-0d8f-43fe-8c96-5799f7c0f466.png align="center")
    
8. **Select the Snapshot Image**: Now you can see the image that we have created
    
    Choose the newly created AMI from the list of available images.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694454251688/81b8ce4f-4404-49e8-8791-b7f6450e0ac5.png align="center")
    
9. **Launch Instance**: Click the "Actions" dropdown and select "Launch Instance" to create a new EC2 instance from the selected image.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694454729814/f9bc3405-918c-4f45-b61d-4fd45b521e77.png align="center")
    
10. **Configure Instance**: Follow the instance creation wizard to configure the new instance, including selecting an instance type, security groups, and other settings. You can also modify storage if needed.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694454744004/c79d9c06-d487-4eeb-a64f-14884f69ecfe.png align="center")
    
11. **Review and Launch**: Review your configuration, and click "Launch" to create the new EC2 instance.
    
12. **Create or Select a Key Pair**: If prompted, create or select an existing key pair to access the new EC2 instance.
    
13. **Launch Instance**: Click "Launch Instances" to start the instance creation process.
    
14. **Wait for Instance to Start**: Wait for the new EC2 instance to reach a running state.
    

### **Part 2: Downloading a File from S3 Bucket**

1. **SSH into Original EC2 Instance**: Use an SSH client to connect to your original EC2 instance.
    
2. **Install AWS CLI (if not already installed)**:
    
    ```bash
    sudo apt-get update
    sudo apt-get install awscli
    ```
    
3. **Configure AWS CLI**: Configure the AWS CLI on the original EC2 instance with your AWS credentials using the `aws configure` command.
    
4. **Download File from S3**: Utilize the AWS CLI `aws s3 cp` command to download the desired file from your S3 bucket to the original EC2 instance:
    
    ```bash
    aws s3 cp s3://your-bucket-name/path/to/file /path/on/ec2/
    ```
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694454841268/1320f40e-324a-4d3b-8665-0920468952b1.png align="center")

> I hope you understood the concept of S3 , kindly refer previous blogs to understand how to create EC2 instance with aws-cli pre-installed.
> 
> Stay tuned for more updates !!
> 
> Happy Cloud Learning :D