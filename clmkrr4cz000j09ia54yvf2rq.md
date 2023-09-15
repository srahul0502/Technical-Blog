---
title: "Unraveling the Magic of Terraform State Management"
datePublished: Fri Sep 15 2023 15:43:15 GMT+0000 (Coordinated Universal Time)
cuid: clmkrr4cz000j09ia54yvf2rq
slug: unraveling-the-magic-of-terraform-state-management
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1694785698588/c7089fd9-a78e-4bb5-96cb-a9873aabb5a1.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1694792272998/c41cd7f5-28a2-4a92-89a2-0d53bbc33618.png
tags: aws, devops, terraform, devops-articles, 90daysofdevops

---

# 📌The Essence of Terraform State

## What is Terraform State⁉️

Think of Terraform as your magical architect who can build entire kingdoms in the cloud. But there's a small catch – this architect tends to forget things. That's where Terraform state comes in.

**Terraform state is like a diary for your architect.** It's where your architect writes down all the details of the buildings they've created, like what they look like and where they are.

## Why Terraform State Matters

1. **Keeping Track of What's Built**: Imagine if your architect built the same house twice in different places. Not very efficient, right? Terraform state prevents such mistakes by reminding your architect of what's already been built.
    
2. **Understanding How Things Connect**: In your world of building, you can't have a bridge if there's no river, right? Terraform state helps your architect understand how different parts of your kingdom are connected.
    
3. **Not Forgetting the Details**: Suppose you decide to paint all your buildings pink. Terraform state helps your architect remember which ones need a new coat of paint./
    

# 📌Understanding the importance of Terraform

Imagine you are using Terraform to manage the infrastructure of a web application hosted on AWS. Your infrastructure includes components like an EC2 instance, an RDS database, a load balancer, and a security group.

1. **Without Terraform State:**
    
    In the absence of Terraform state, you would need to manually keep track of the current state of your infrastructure. You might have a rough idea of what resources were provisioned, but it would be challenging to maintain a precise record.
    
    For instance, you know that you created an EC2 instance with ID `i-1234567890abcdef0`, but you can't be sure of its exact configuration, such as its instance type, security group associations, or tags.
    
2. **With Terraform State:**
    
    Terraform state stores detailed information about each resource you manage. For example, it knows that:
    
    * EC2 instance `i-1234567890abcdef0` is of type `t2.micro`, has a specific IAM role attached, and is associated with a security group allowing port 80 traffic.
        
    * The RDS database instance has specific configuration options, including its storage size and database engine version.
        
    * The load balancer is distributing traffic across your EC2 instances.
        
    
    Now, let's say you want to update the instance type of your EC2 instance to `t2.small`. Terraform state helps you in the following ways:
    
    * It accurately identifies the current state of the EC2 instance.
        
    * When you run `terraform plan`, Terraform compares this current state with your desired configuration and suggests the necessary changes.
        
    * After applying the changes with `terraform apply`, Terraform updates the state to reflect the new configuration.
        
    
    Terraform state ensures that your infrastructure is always in the desired state and helps you make informed decisions about changes and updates.
    

## Terraform State: The Elemental Foundation

Imagine Terraform state as the personal journal of your magical architect. It meticulously records every detail about the structures they've summoned, their characteristics, and their whereabouts.

## The Significance of Terraform State

Why does Terraform state hold such a pivotal role? Let's delve deeper:

1. **Preserving Building Memory**: Think of your architect inadvertently crafting identical castles in distant lands – far from ideal! Terraform state prevents such mishaps by reminding your architect of existing creations.
    
2. **Revealing Interconnections**: In the realm of creation, bridges don't manifest without rivers. Terraform state unveils these connections, ensuring buildings stand in harmony.
    
3. **Safeguarding the Details**: Suppose you decide to paint all your structures azure. Terraform state ensures your architect doesn't forget which ones require a fresh coat.
    

## The Critical Role of Terraform State

Terraform state is like the secret recipe for a delicious dish. It plays a crucial role in two main areas:

1. **Keeping Things Consistent**: Think about a house with a missing roof. If someone accidentally removes it, your architect would notice because Terraform state reminds them that the roof should be there. This keeps your kingdom looking consistent.
    
2. **Understanding What Relies on What**: In your world of construction, you can't build a treehouse if there's no tree. Terraform state helps your architect understand these connections. It ensures that buildings go up in the right order.
    

## The Essence of Terraform

Now, let's unlock why Terraform, combined with its state management prowess, stands as a cornerstone for contemporary infrastructure governance:

* **Infrastructure as Code (IaC)**: Terraform empowers you to erect your digital realm by scripting your vision, akin to penning a saga. It enhances the organization and reliability of your domain.
    
* **Realm Regeneration**: Picture regenerating your entire realm at will. Terraform accomplishes precisely that with minimal commands, invaluable for testing or starting anew.
    
* **Kingdom Scaling**: Whether you rule a hamlet or a colossal empire, Terraform adapts effortlessly to your domain's size. You can extend your realm as needed, sans complications.
    
* **Collaborative Sorcery**: Terraform fosters collaboration. Numerous architects can toil on diverse sections of your realm simultaneously, facilitated by Terraform's harmonious orchestration.
    
* **Economical Rule**: Terraform assists in judicious domain management. Unneeded structures can be dismantled, saving treasury riches via prudent cloud resource management.
    
* **Sovereign Command**: Empowered by Terraform state, you become the unchallenged sovereign of your domain. You discern every happening, set mandates, and oversee flawless operation.
    

# 📌Local vs. Remote State Management: Choosing the Right Path

Terraform is a fantastic tool for creating and managing your cloud infrastructure using code. However, when you're building something complex, you need to manage what Terraform creates, like virtual machines, networks, and databases. This is where Terraform's "state" comes into play. It's like keeping track of all the changes and creations Terraform makes on your cloud playground.

## Understanding Local State Storage

### What is Local State?

Local state storage in Terraform is like having a diary where you write down everything you're doing but keeping it all to yourself. When you use local state, Terraform keeps track of everything on your own computer, right where you're running Terraform commands. It's simple and works well for small projects or when you're just experimenting.

### How to Use Local State

1. **Create Your Terraform Configuration**: You start with a file that tells Terraform what to build. Here's a simple example:
    
    ```bash
    # main.tf
    
    provider "aws" {
      region = "us-east-1"
    }
    
    resource "aws_instance" "example" {
      ami           = "ami-0c55b159cbfafe1f0"
      instance_type = "t2.micro"
    }
    ```
    
2. **Get Terraform Ready**: Run `terraform init` in your terminal. This gets Terraform set up and ready to work with your plan.
    
3. **Start Building**: Execute `terraform apply`, and Terraform starts building your cloud resources. It remembers what it's building in your local state.
    
4. **Check Your Diary**: Your local state is saved as a file in your project directory, often named something like `terraform.tfstate`. It contains all the details about what you've created.
    

### Pros of Local State

* **Simple Setup**: It's easy to get started because everything is on your computer.
    
* **Quick Access**: You can check your diary (state file) instantly, making it handy for small projects or quick changes.
    
* **Works Offline**: You can use Terraform without needing an internet connection.
    

### Cons of Local State

* **No Teamwork**: It doesn't work well when multiple people want to play in your cloud playground. It's a solo act.
    
* **Limited Security**: Your diary (state file) might contain sensitive info, and keeping it secure is your responsibility.
    
* **Local Troubles**: If your computer crashes or you delete your diary accidentally, you might lose all your progress.
    

### Challenges in Local State Storage

1. **Lack of Collaboration**: It doesn't work well for teams. Multiple people can't easily work on the same infrastructure.
    
2. **Security Risks**: Your diary (state file) may contain sensitive info. If not protected properly, it can be a security risk.
    
3. **Data Loss Risk**: Storing state locally means it's vulnerable to local machine failures, accidental deletions, or corruption.
    
4. **Scalability Issues**: As your project grows, managing state files on individual machines becomes more complex and error-prone.
    

## Remote State Storage: The Collaborative Magic

### What is Remote State?

Remote state storage is like having a shared diary in a secure vault that everyone on your team can access. When you use remote state, Terraform keeps your diary in a safe place outside your computer, making it ideal for teamwork and larger projects.

### How to Use Remote State

Storing Terraform state remotely involves using a dedicated remote backend. Here's how it generally works:

#### 1\. Configure Your Backend

In your Terraform configuration, you set up the backend you want to use, specifying where and how to store your state. Here's an example using AWS S3:

```bash
# backend.tf

terraform {
  backend "s3" {
    bucket         = "my-terraform-state"
    key            = "terraform.tfstate"
    region         = "us-east-1"
    encrypt        = true
    access_key     = "your-access-key"
    secret_key     = "your-secret-key"
  }
}
```

#### 2\. Initialize Terraform

Run `terraform init` again. Terraform now knows that your state is stored remotely.

#### 3\. Apply Changes

Execute `terraform apply` as usual, and Terraform will store the state in your chosen remote location.

### **Pros of Remote State**

* **Team Collaboration**: Everyone on your team can access and work on the same infrastructure, promoting teamwork.
    
* **Enhanced Security**: Your state is more secure, with better access controls, protecting your data.
    
* **Safety Net**: Even if your computer crashes, your state is safe, allowing you to recover easily.
    
* **Scales with Ease**: Works well for larger projects that need to grow.
    

### **Cons of Remote State**

* **Complex Setup**: It's a bit more complicated to set up, especially if you're new to Terraform.
    
* **Needs the Internet**: You must be online to access and manage your state.
    
* **Possible Costs**: Some remote services might come with additional costs, depending on usage.
    
* **Access Control Challenges**: Setting up access controls correctly can be tricky and potentially lead to security risks.
    

### **Challenges in Remote State Storage**

1. **Complex Configuration**: Setting up remote state storage can be more complex, especially for beginners.
    
2. **Internet Dependency**: You need an internet connection to access and manage your state.
    
3. **Access Control Complexity**: Ensuring proper access controls and permissions in remote storage systems can be complex and prone to misconfigurations.
    
4. **Additional Costs**: Some remote storage solutions may involve additional costs, especially in cloud environments.
    

## Choosing Between Local and Remote State

### Use Cases

The choice between local and remote state largely depends on your project's characteristics:

* **Local State**:
    
    * Best for small projects or experiments.
        
    * Suitable when working offline or with limited connectivity.
        
    * Useful for individual learning and exploration.
        
* **Remote State**:
    
    * Ideal for teamwork and collaborative projects.
        
    * Essential for production environments where security and reliability are crucial.
        
    * Recommended for projects with long-term scalability requirements.
        
    
    Here's a handy table comparing local and remote state storage:
    
    | Aspect | Local State | Remote State |
    | --- | --- | --- |
    | Storage Location | On your computer or server | On a remote storage system |
    | Collaboration | Not suitable for teamwork | Ideal for team collaboration |
    | Security | Limited access control | Enhanced security controls |
    | Offline Access | Yes | Depends on remote service |
    | Disaster Recovery | Vulnerable to local issues | Protected against failures |
    | Scalability | Limited to local resources | Scales with remote service |
    | Use Cases | Small projects, testing | Production and teamwork |
    

### Considerations

When deciding which state storage option to choose, consider the following factors:

* **Project Scale**: How large is your project? Small projects may benefit from the simplicity of local state, while larger, collaborative efforts demand remote state.
    
* **Teamwork**: Are you working with others? If yes, remote state is the way to go to ensure seamless collaboration.
    
* **Security**: Do you have sensitive data in your infrastructure? Remote state provides better security controls.
    
* **Internet Access**: Is internet access readily available where you work? Remote state requires an internet connection.
    
* **Long-Term Goals**: Consider your project's long-term goals. If you plan to scale or maintain your infrastructure over time, remote state offers more benefits.
    

When choosing remote state storage in Terraform, it's essential to carefully consider a backend that suits your infrastructure and security needs. You have various backend options to choose from, each catering to different requirements.

Cloud providers like AWS, Azure, and GCP offer their backend options, tailored to their cloud ecosystems. Additionally, there are more generic choices available, such as the HTTP backend or Terraform Cloud, designed to facilitate remote state management.

To implement a remote backend in your Terraform project, you'll need to make specific adjustments to your Terraform configuration file (usually named [terraform.tf](http://terraform.tf)). This configuration file acts as the blueprint for your infrastructure and includes the necessary settings for remote state storage.

Here's an example of a simple Terraform configuration file ([terraform.tf](http://terraform.tf)) that creates an AWS S3 bucket. We'll also go through the steps to initialize it for local state storage, as a starting point:

```bash
# terraform.tf

# Define the provider and region
provider "aws" {
  region = "us-east-1"
}

# Create an AWS S3 bucket
resource "aws_s3_bucket" "s3-bucket-test" {
  bucket = "test-s3-local-bucket"
  acl    = "private"
}

# Output the bucket name
output "bucket_name" {
  value = aws_s3_bucket.s3-bucket-test.id
}
```

# 📌Configuring AWS S3 as Your Terraform Remote Backend: A Step-by-Step Guide

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694784828369/cef8b7fc-e53d-473f-8573-420d03a9bf91.png align="center")

Remote state management is a crucial part of using Terraform effectively. It allows you to securely store your Terraform state files and collaborate with your team. One popular choice for remote state management is using AWS S3 as a backend to keep your Terraform state files. Let's break down the setup and configuration steps in a beginner-friendly way.

Remote state management is a crucial component of Terraform infrastructure management, ensuring secure storage and enabling collaboration. Let's explore one of the popular choices for remote state management: using AWS S3 as a backend for storing Terraform state files. We'll also touch upon why AWS S3 is a preferred option and what a remote backend is.

## Why AWS S3 for Remote State Management?

Amazon Simple Storage Service (AWS S3) is a reliable and highly scalable cloud storage service offered by Amazon Web Services. It is commonly chosen as a remote state backend for Terraform for several reasons:

* **Reliability**: AWS S3 is designed for high availability and durability, making it a dependable choice for storing critical infrastructure state data.
    
* **Scalability**: S3 can easily scale to accommodate the state files of projects of all sizes. Whether you're managing a small application or a large-scale infrastructure, S3 can handle the load.
    
* **Security**: AWS provides robust security features for S3, allowing you to control access to your state files and encrypt them for enhanced protection.
    
* **Accessibility**: S3 is accessible from anywhere, making it suitable for team collaboration and remote work scenarios.
    
* **Integration**: Terraform seamlessly integrates with AWS services, making S3 a natural choice for state management in AWS-centric environments.
    

## Setting Up AWS S3 as the Remote Backend

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694784980598/2a616600-ac2f-42c1-a0fa-b4f0f5386721.png align="center")

Now, let's walk through how to configure AWS S3 as your Terraform remote backend.

### 1\. Terraform Configuration ([`terraform.tf`](http://terraform.tf))

```bash
# terraform.tf

terraform {
  required_providers {
    aws = {
      source = "hashicorp/aws"
      version = "~> 5.0"
    }
  }
}
```

**Explanation**:

* In this section, we're telling Terraform which tools it should use.
    
* Imagine this as specifying the type of car (AWS) you want to drive and its version.
    
* We're saying, "Terraform, use AWS version 5.0 or a newer one."
    

### 2\. AWS Provider Configuration ([`provider.tf`](http://provider.tf))

```bash
# provider.tf

provider "aws" {
  region = "us-east-1" # You can pick a different place if you like
}
```

**Explanation**:

* Here, we're setting up the connection to AWS, like entering your address in a GPS.
    
* `region` is like choosing a destination on your GPS. We're saying, "Go to the 'us-east-1' area of AWS."
    

### 3\. DynamoDB Table and S3 Bucket ([`resource.tf`](http://resource.tf))

```bash
# resource.tf

resource "aws_dynamodb_table" "my_state_table" {
  name           = "terraweek_state_table"
  billing_mode   = "PAY_PER_REQUEST"
  hash_key       = "LockID"

  attribute {
    name = "LockID"
    type = "S"
  }
}

resource "aws_s3_bucket" "my_state_bucket" {
  bucket = "terraweek-day4" # Choose a unique name, like naming your pet
}
```

**Explanation**:

* This part is where we describe what we want to create in AWS.
    
* Think of `aws_dynamodb_table` as a blueprint for creating a special table in AWS (DynamoDB).
    
* `name` is like giving your new table a name, say "My Special Table."
    
* `billing_mode` tells AWS how to charge you. We're choosing "PAY\_PER\_REQUEST" because it's like paying only when you use it.
    
* The `attribute` part says we're adding a special attribute called "LockID," which is a text (string).
    

S3 Bucket

* `aws_s3_bucket` is like telling AWS to create a big online storage box (S3 bucket).
    
* `bucket` is where you name your storage box. It must be unique, like naming your pet; for example, "MyAwesomeStorage."
    

### Initializing and Applying Changes

Now, after writing down what we want, we have to make it happen:

1\. Initialize Terraform

```bash
terraform init
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694791806942/e1e13eba-7f7a-42d8-a77e-173e80afb00d.png align="center")

**Explanation**:

* This is like starting your car's engine. It gets Terraform ready to do the work.
    

2\. Plan and Apply Changes

```bash
terraform plan
terraform apply
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694791791551/80dfa6bb-96b3-4d48-a8fd-3b93c95859af.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694791845715/c99db590-bd92-42f5-acfa-e080bb7efa95.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694791875412/033a5d41-9989-4f5a-a83f-739da044c8c8.png align="center")

**Explanation**:

* `terraform plan` is like asking Terraform to tell you what it's going to do before it does it. It's like checking your GPS before driving.
    
* `terraform apply` is like telling Terraform, "Go ahead, make it happen!" It's like pressing the gas pedal and letting the car drive to your chosen destination.
    

3\. List Remote State Resources

```bash
terraform state list
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694791775675/011ea9a9-cfb3-4962-b05d-3a9c229ddfcd.png align="center")

**Explanation**:

* If you ever want to see a list of what Terraform created in AWS, this command shows you that list. It's like checking what's in your storage box.
    

By following these steps and understanding the code, you can effectively use AWS S3 as your Terraform remote storage, making your infrastructure management safe and easy.

# **📌Configuring Remote State Storage with AWS S3: Your Terraforming Adventure Begins!**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694784867941/1292454e-1dd2-400c-b174-bc84bd040d87.png align="center")

Implementing remote state storage is a strategic choice in Terraform infrastructure management. By configuring a remote backend, such as AWS S3, you can securely store your Terraform state files and unlock a range of valuable advantages:

1. **Streamlined Collaboration**: Multiple team members can seamlessly collaborate on the same infrastructure project, eliminating conflicts and ensuring efficient teamwork.
    
2. **Enhanced Security**: Your state files are safeguarded in a secure remote location, protecting them from unauthorized access and accidental deletions.
    
3. **Concurrent Control**: Remote state management includes locking mechanisms that prevent simultaneous changes by multiple users, ensuring the integrity of your infrastructure.
    
4. **Effortless Accessibility**: With state files stored remotely, you can access and manage your infrastructure from anywhere, empowering your team to work effectively, regardless of location.
    

Now, let's explore how to set up AWS S3 as the remote backend for your Terraform state, facilitating these advantages effectively."

**Step 1: Create Configuration Files**

Imagine this as the first step of building a puzzle. We're going to create some special files that will help Terraform understand what we want to do.

In your project folder, create three files: [`terraform.tf`](http://terraform.tf), [`providers.tf`](http://providers.tf), and [`resources.tf`](http://resources.tf).

**Step 2: Configure Terraform Backend**

Now, let's set up a secret treasure chest where Terraform will store its magic spells (state files). Open the [`terraform.tf`](http://terraform.tf) file and add these enchanting lines:

```bash
terraform {
  required_providers {
    aws = {
      source = "hashicorp/aws"
      version = "~> 5.0"
    }
  }
  backend "s3" {
    bucket         = "terraweek-day4"
    key            = "terraform.tfstate"
    region         = "us-east-1"
    dynamodb_table = "terraweek_state_table"
  }
}
```

Think of this as creating a mystical connection to AWS S3, a realm where our Terraform spells will be safely stored.

**Step 3: Configure AWS Provider**

Now, we need to tell Terraform that we want to tap into the immense power of AWS. Open [`providers.tf`](http://providers.tf) and add this incantation:

```bash
provider "aws" {
  region = "us-east-1"
}
```

Imagine you're summoning the spirit of AWS in the US East region to do your bidding.

**Step 4: Define Infrastructure Resources**

Here's the fun part! In [`resources.tf`](http://resources.tf), you can describe the magical objects you want to create. For example:

```bash
resource "aws_instance" "terra_backend_instance" {
  ami           = "ami-053b0d53c279acc90"
  instance_type = "t2.micro"
  tags = {
    Name = "terraform_instances"
  }
}
```

This spell conjures a tiny AWS instance with a specific appearance (AMI) and powers (instance type).

**Step 5: Initialize and Apply Changes**

You're almost there! Now, let's put your wizard hat on:

* Run `terraform init` to prepare your magical staff (Terraform).
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694791582435/b79f0652-668c-4950-8a2e-e12e743bcf39.png align="center")
    
* Use `terraform plan` to peer into the crystal ball and see what changes Terraform will make.
    
* Finally, cast the `terraform apply` spell to bring your creation to life in the AWS realm!
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694791590811/7c9552bd-29f1-4d9b-b767-2a270822a84a.png align="center")
    

**Step 6: Verification**

To ensure your spells worked as intended:

* Cast the `terraform state list` spell to see the magical beings Terraform is managing.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694791683418/3cb09684-fce3-4a9f-9e43-c5b6b14d6d2a.png align="center")
    
* Journey to your AWS S3 bucket and find the `terraform.tfstate` relic. It contains the secrets of your creations.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694791693564/83f52f23-53c1-48ae-9db6-f1d36d0d22d6.png align="center")
    
* Seek the mystical DynamoDB table you mentioned earlier; it helps keep the balance.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694791717130/98c5a373-b775-465b-a823-41cb2d0497db.png align="center")
    
* Lastly, check that your newly summoned AWS instance is happily roaming in the region you specified.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694791734047/02001418-ded2-44c8-b45b-913b313d86a2.png align="center")
    

# **Finally, We Did It!🙌🥳**

Congratulations, brave Terraform sorcerer! You've successfully configured remote state storage with AWS S3, unlocking the power of collaborative infrastructure management. You've harnessed the magic of Terraform to conjure AWS resources and stored their secrets securely in the cloud. By following this enchanting journey, you've learned how to:

1. Set up Terraform configuration files.
    
2. Establish a remote backend using AWS S3.
    
3. Configure the AWS provider for spellcasting.
    
4. Define and create AWS resources.
    
5. Initialize, plan, and apply your infrastructure changes.
    
6. Verify the results of your Terraform spells.
    

But remember, just like any skilled wizard, your journey doesn't end here. Terraform offers a vast landscape of possibilities for orchestrating and managing your cloud kingdom. As you continue to explore, you'll discover advanced incantations, powerful modules, and secrets that will help you shape your digital realm with even greater precision and efficiency.

> **In the world of Terraform, as in all endeavours, practice will make perfect. Keep conjuring, keep learning, and you'll become a true wizard of infrastructure. May your cloud kingdom thrive and your spells always run successfully!**
> 
> **Happy Terraforming, and may your adventures in infrastructure continue to be magical!**