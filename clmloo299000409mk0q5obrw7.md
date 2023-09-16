---
title: "Unlocking the Power of Terraform Modules"
datePublished: Sat Sep 16 2023 07:04:40 GMT+0000 (Coordinated Universal Time)
cuid: clmloo299000409mk0q5obrw7
slug: unlocking-the-power-of-terraform-modules
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1694847840148/5bf3a444-75b8-44ea-ba14-dfb892a47c21.webp
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1694847794111/ae0960cc-f6ba-4be8-9d2c-2c576a95a7d5.png
tags: devops, terraform, devops-articles, 90daysofdevops, terrafor

---

Are you ready to embark on a journey into the exciting world of Terraform modules? If you're new to Terraform, you might be wondering what all the buzz is about when it comes to "modules." In this beginner-friendly guide, we'll break down what Terraform modules are, why they're essential, and the incredible benefits they offer.

## 🌟 Unveiling Terraform Modules: Your Infrastructure's Best Friends

### **What Are Modules in Terraform?**

In Terraform, a module is like a ready-made recipe for creating a specific piece of your infrastructure. Think of it as a set of instructions that defines how to build a particular component, such as a virtual machine, database, or network configuration.

Imagine you're building a house. Instead of crafting every brick and nail yourself, you can use pre-designed modules for common elements like doors, windows, and plumbing. Terraform modules work in a similar way. They save you time and effort by encapsulating infrastructure configurations into reusable units.

### **Why Do We Need Modules in Terraform?**

Now, let's explore why Terraform modules are so crucial:

1. **Modularity**: In the world of Terraform, modularity means breaking down your infrastructure into smaller, manageable pieces. Modules enable you to organize your code into neat, self-contained units, making it easier to understand and maintain.
    
2. **Abstraction**: Modules abstract away the complexity of infrastructure provisioning. They allow you to focus on what you want to create rather than the nitty-gritty details of how to create it. This abstraction simplifies your code and reduces the risk of errors.
    
3. **Reusability**: Once you've created a module for a specific resource or configuration, you can use it in multiple projects. This promotes code reuse, saving you from reinventing the wheel every time you need a similar component.
    
4. **Collaboration**: In a team setting, modules foster collaboration. Team members can create standardized modules that others can easily include in their Terraform configurations. This consistency ensures everyone is on the same page and reduces configuration drift.
    

## ✨ Benefits of Using Modules in Terraform

Now that we know what Terraform modules are and why they're essential, let's delve into the advantages they bring:

### 1\. Reusability: Unlocking the Magic of Efficiency

Imagine you're provisioning AWS EC2 instances for various projects. Instead of rewriting the same code for each instance, you can create a reusable EC2 module. This module can accept different input variables, allowing you to create instances with various specifications. The result? Less repetitive coding, fewer chances for errors, and increased productivity.

**Example:**

```bash
module "web_servers" {
  source = "./modules/vm"
  count  = 5  # Create 5 VMs
  # Other variables specific to VMs
}
```

This module allows you to create any number of VMs by simply adjusting the count variable and specifying your unique configurations.

### 2\. Maintainability: Keeping Your Infrastructure Shipshape

As your infrastructure grows, maintaining your Terraform code can become challenging. Modules offer a solution by encapsulating each piece of your infrastructure. When you need to make changes or updates, you can focus on a single module without affecting the rest of your configuration. This isolation simplifies debugging and ensures stability.

**Example:** Over time, your infrastructure evolves. You need to update security groups, add new features, or change instance types. Without modules, managing these changes can be a nightmare.

With modules, you can isolate each component. If you need to update your VMs, you can focus on the VM module without affecting other parts of your infrastructure.

### 3\. Collaboration: Building Together, Growing Together

In a team setting, modules foster collaboration and knowledge sharing. Team members can create well-documented modules that encapsulate best practices and company standards. These modules can then be easily shared and reused across projects, promoting consistency and reducing the learning curve for new team members.

**Example:** Suppose you work on a team, and different members are responsible for different parts of your infrastructure. Modules make it easy to collaborate. Each team member can work on their modules, ensuring that everyone follows the same conventions and standards.

### 4\. Scalability: Growing Your Infrastructure Seamlessly

Modules adapt seamlessly to the growth of your infrastructure. As you need to add more instances, databases, or other resources, you can simply instantiate modules with different input variables. This scalability allows you to expand your infrastructure without rewriting or reconfiguring your entire Terraform codebase.

**Example:** As your business grows, you'll need more of everything: more servers, more databases, and more services. Modules are incredibly scalable. You can use the same module for a small development environment or a massive production setup, just by adjusting variables.

### 5\. Readability: Bringing Clarity to Complexity

Large Terraform configurations can become unwieldy and difficult to understand. Modules enhance code readability by breaking your configuration into smaller, self-contained pieces. Each module focuses on a specific aspect of your infrastructure, making your Terraform code more accessible to both you and your teammates.

**Example:** Imagine a large Terraform configuration file that handles your entire infrastructure. It becomes challenging to understand and maintain. Modules break this complexity into smaller, digestible parts.

```bash
module "web_servers" {
  source = "./modules/vm"
  # Configuration for VM module
}

module "database" {
  source = "./modules/database"
  # Configuration for database module
}

# ... and so on
```

Each module focuses on a specific aspect of your infrastructure, making your Terraform code readable and comprehensible.

# 🏗️ Building a Terraform Module for an AWS EC2 Instance

In this beginner-friendly guide, we'll create a Terraform module to encapsulate reusable infrastructure configuration for an AWS EC2 instance. Terraform modules help you organize and reuse your infrastructure code, making it scalable and maintainable. Let's break down the code you provided and explain each part step by step.

## 📁 Essential Files for the Module

Before diving into the code, let's understand the essential files that make up our Terraform module:

1. [**terraform.tf**](http://terraform.tf): This file specifies the Terraform version and provider, setting the stage for our AWS EC2 instance module.
    
2. [**variables.tf**](http://variables.tf): Here, we define input variables that allow customization of the EC2 instance, such as the Amazon Machine Image (AMI) ID, instance type, and names.
    
3. [**ec2.tf**](http://ec2.tf): This file defines our AWS EC2 instance resource. It specifies its configuration, including the AMI ID and instance type.
    
4. [**s3.tf**](http://s3.tf) **(optional)**: If needed, this file defines an S3 bucket resource within the module.
    
5. [**dynamodb.tf**](http://dynamodb.tf) **(optional)**: This file allows you to include DynamoDB table configurations within the module.
    

Now, let's explore each file and its role in our module.

## 🚀 Module Code

### [`terraform.tf`](http://terraform.tf)

```bash
terraform {
  required_providers {
    aws = {
      source  = "hashicorp/aws"
      version = "~> 5.0"
    }
  }
}

provider "aws" {
  region = "us-east-1" # Replace with your desired AWS region
}
```

In this file, we specify the Terra

form provider (AWS in this case) and its version. The `provider` block configures the AWS region, which you can customize by replacing `"us-east-1"` with your preferred region.

### [`variables.tf`](http://variables.tf)

```bash
variable "ami_id" {
  default = "ami-053b0d53c279acc90"
}

variable "instance_type" {
  default = "t2.micro"
}

variable "instance_name" {
  type = string
}

variable "bucket_name" {
  type = string
}

variable "table_name" {
  type = string
}

variable "env_name" {
  type = string
}
```

This file defines input variables with default values, allowing you to customize your EC2 instance and other resources. Variables like `ami_id` and `instance_type` have default values, but `instance_name`, `bucket_name`, `table_name`, and `env_name` require specific values.

### [`ec2.tf`](http://ec2.tf)

```bash
resource "aws_instance" "terra_Day5_instance" {
  ami           = var.ami_id
  instance_type = var.instance_type

  tags = {
    Name = "${var.env_name}-${var.instance_name}"
  }
}
```

This file defines the AWS EC2 instance resource using the variables from [`variables.tf`](http://variables.tf). It specifies the AMI ID, instance type, and assigns tags to the instance for identification.

### [`s3.tf`](http://s3.tf) (optional)

```bash
resource "aws_s3_bucket" "my-terra-day5-bucket" {
  bucket = "${var.env_name}-${var.bucket_name}"
}
```

If you need an S3 bucket as part of your module, you can include this file. It defines an S3 bucket resource using a naming convention based on your environment and bucket name.

### [`dynamodb.tf`](http://dynamodb.tf) (optional)

```bash
resource "aws_dynamodb_table" "my-terra-day5-table" {
  name         = "${var.env_name}-${var.table_name}"
  billing_mode = "PAY_PER_REQUEST"

  hash_key = "day5terratable"

  attribute {
    name = "day5terratable"
    type = "S"
  }
}
```

Similarly, if you require a DynamoDB table, you can use this file. It defines a DynamoDB table resource with a naming convention based on your environment and table name.  
  
You can also put it in a single file just like below :  

```bash
# Define the required provider and version
terraform {
  required_providers {
    aws = {
      source  = "hashicorp/aws"
      version = "~> 3.0"
    }
  }
}

# Configure the AWS provider
provider "aws" {
  region = "us-east-1" # Replace with your desired AWS region
}

# Define input variables
variable "ami_id" {
  default = "ami-053b0d53c279acc90"
}

variable "instance_type" {
  default = "t2.micro"
}

variable "instance_name" {
  default = "terraweek-day5-instance"
}

variable "bucket_name" {
  default = "my-terraweek-day5-bucket"
}

variable "table_name" {
  default = "my-terraweek-day5-table"
}
variable "env_name" {
  type    = string
  default = "dev" # Default to "dev," but you can change it as needed
}


# Create an AWS EC2 instance
resource "aws_instance" "terra_Day5_instance" {
  ami           = var.ami_id
  instance_type = var.instance_type

  tags = {
    Name = "${var.env_name}-${var.instance_name}"
  }
}

# Create an optional S3 bucket
resource "aws_s3_bucket" "my-terra-day5-bucket" {
  bucket = "${var.env_name}-${var.bucket_name}"
}

# Create an optional DynamoDB table
resource "aws_dynamodb_table" "my-terra-day5-table" {
  name         = "${var.env_name}-${var.table_name}"
  billing_mode = "PAY_PER_REQUEST"

  hash_key = "day5terratable"

  attribute {
    name = "day5terratable"
    type = "S"
  }
}
```

Use `terraform init` , `terraform plan` , `terraform apply`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694846776634/8bb43124-2b28-4b84-b6f5-1ef3ba7af3bb.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694846946438/d5e3246c-60ec-4d78-b3db-e1a733b3bd2b.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694846954092/428e2bb3-ee20-4a6c-b533-2ce6dbee7ae4.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694846959259/8811442a-e453-4c48-af0a-dfd96f8eeeac.png align="center")

## 💡 Using the Module: Bringing Your Infrastructure to Life

To use this module in your Terraform project, follow these steps:

1. Create a directory for your Terraform project.
    
2. Inside your project directory, create a [`main.tf`](http://main.tf) file.
    
3. In your [`main.tf`](http://main.tf), define the different EC2 instance configurations using the module:
    

```bash
# Dev/qa
module "dev-terra-app" {
  source        = "./terraform-day5-module/module"
  env_name      = "dev"
  instance_type = "t2.micro"
  ami_id        = "ami-053b0d53c279acc90"
  instance_name = "terra_Day5_instance"
  bucket_name   = "my-terraweek-day5-bucket"
  table_name    = "my-terraweek-day5-table"
}

# Staging
module "stag-terra-app" {
  source        = "./terraform-day5-module/module"
  env_name      = "stage"
  instance_type = "t2.small"
  ami_id        = "ami-053b0d53c279acc90"
  instance_name = "terra_Day5_instance"
  bucket_name   = "my-terraweek-day5-bucket"
  table_name    = "my-terraweek-day5-table"
}

# Production
module "prod-terra-app" {
  source        = "./terraform-day5-module/module"
  env_name      = "prod"
  instance_type = "t2.medium"
  ami_id        = "ami-053b0d53c279acc90"
  instance_name = "terra_Day5_instance"
  bucket_name   = "my-terraweek-day5-bucket"
  table_name    = "my-terraweek-day5-table"
}
```

By defining these modules in your [`main.tf`](http://main.tf), you can create AWS EC2 instances with different configurations for various environments: Dev/qa, Staging, and Production.

# 🔓 Leveraging the Power of Modular Composition and Module Versioning for Infrastructure as Code

In today's fast-paced world of cloud computing, efficiently managing infrastructure is paramount. Infrastructure as Code (IaC) is the backbone of this transformation, and Terraform stands as one of the leading IaC tools. Within Terraform, two fundamental concepts, **Modular Composition** and **Module Versioning**, shine as the stars of IaC, offering tremendous potential for creating reusable and maintainable infrastructure configurations.

## 💡 Unraveling the Magic of Modular Composition

### **What is Modular Composition?**

Modular Composition is Terraform's secret sauce that allows you to break down your infrastructure code into smaller, reusable modules. Gone are the days of monolithic configurations; now, you can create specialized modules for each piece of your infrastructure puzzle, like networking, databases, or application servers.

### **The Art of Reusability**

1. **Effortless Repetition**: Once you've crafted a module for a specific component, you can use it across different projects. Say goodbye to repetitive code writing!
    
2. **Zen-like Simplicity**: Smaller, focused modules are easier to comprehend and maintain. Debugging and troubleshooting become less of a headache.
    
3. **Parallel Progress**: Modularization empowers your teams to work on different modules simultaneously, significantly speeding up development and boosting productivity.
    
4. **Built-in Consistency**: Modules enable you to establish standardized configurations for specific components, ensuring uniformity across your infrastructure.
    

### **Deconstructing a Terraform Module**

A typical Terraform module structure looks like this:

```bash
my-module/
    ├── main.tf
    ├── variables.tf
    ├── outputs.tf
    └── README.md
```

* [`main.tf`](http://main.tf): This file is the heart of the module. It defines the resources and their configurations.
    
* [`variables.tf`](http://variables.tf): Here, you declare input variables that users can customize when utilizing the module, making it flexible and versatile.
    
* [`outputs.tf`](http://outputs.tf): This file specifies the output values that other parts of your infrastructure might need from the module.
    
* [`README.md`](http://README.md): Your documentation headquarters, explaining how to utilize the module and any other pertinent information.
    

### **Embracing Modular Composition**

To use a module in your Terraform configuration, you specify the module source and provide values for its input variables. A simplified example looks like this:

```bash
module "web_server" {
  source = "./modules/my-module"
  var1   = "value1"
  var2   = "value2"
}
```

By adopting this modular approach, you can construct infrastructure configurations that are not only modular but also reusable and easy to maintain.

## 🧩 Module Versioning: The Guardians of Stability

### **What is Module Versioning?**

Module Versioning is the practice of tagging Terraform modules with versions to monitor changes and updates. This ensures the stability, predictability, and compatibility of your infrastructure, especially when dealing with multiple

teams, projects, and dependencies.

### **Terraform Registry and Version Constraints**

Terraform modules can reside on the Terraform Registry or other version control systems like GitHub. When using modules, you can define version constraints to specify which version of a module to use. Version constraints are your trusty shield against unexpected module changes that could disrupt your infrastructure.

### **The Gifts of Module Versioning**

1. **Stability Reigns Supreme**: Versioning keeps your infrastructure stable even as modules evolve. You can update modules independently while retaining control over the versions used in your configuration.
    
2. **Predictability at its Best**: By setting version constraints, you explicitly define compatibility, reducing the risk of unexpected changes impacting your infrastructure.
    
3. **Seamless Collaboration**: Different teams can confidently work on their modules and share them across projects. They can dictate which module versions to use, ensuring consistency.
    
4. **Easy Rollback**: Should a new module version cause issues, you can gracefully roll back to a previous version by adjusting the version constraint, providing a safety net for your infrastructure.
    

### **Crafting a Module Versioning Strategy**

* **Specify Version Constraints**: Always, without exception, specify version constraints for modules in your configuration to safeguard against unforeseen updates.
    
* **Embrace Semantic Versioning**: Follow the principles of semantic versioning (SemVer) when creating and versioning your modules. SemVer consists of three segments: MAJOR.MINOR.PATCH.
    
* **Leverage Version Control Systems**: Host and manage your modules using version control systems like Git. This enables you to tag specific releases and versions.
    
* **Stay Updated**: Regularly review and update module dependencies to ensure security patches and enhancements are applied.
    
* **Document Changes**: Keep your module users informed by documenting module changes and version history in the module's README file.
    

## 🏆 In Conclusion: Reusable Modules, Stable Foundations

Modular Composition and Module Versioning are your trusted companions in the Terraform journey. By embracing these concepts, you unlock the potential to build scalable, maintainable, and predictable Infrastructure as Code. Break down your configurations into reusable modules, manage versions diligently, and watch your infrastructure management become a breeze.

These principles not only optimize your workflows but also foster collaboration among your teams. So, get ready to embark on a journey where infrastructure management is efficient, reliable, and, most importantly, reusable. With Terraform, the possibilities are endless.

# 🔒 Locking Terraform Module Versions for Stable Infrastructure

When you're managing your infrastructure using Terraform, maintaining stability is a top priority. You don't want your infrastructure code to break unexpectedly due to changes in module dependencies. To ensure stability and predictability, you can lock Terraform module versions. In this guide, we'll explore two common methods for doing this: using a [`versions.tf`](http://versions.tf) file and the `required_providers` block within your root module.

## Using a [`versions.tf`](http://versions.tf) File

One way to lock Terraform module versions is by creating a [`versions.tf`](http://versions.tf) file in your project directory. This file allows you to specify the required versions of providers and modules and pin the module versions you want to use.

Here's an example of a [`versions.tf`](http://versions.tf) file:

```bash
terraform {
  required_version = ">= 0.12, < 0.14" # Set the Terraform version constraint
}

provider "aws" {
  version = ">= 3.0, < 4.0" # Set the AWS provider version constraint
  region  = "us-east-1"
}

module "example_module" {
  source  = "terraform-aws-modules/vpc/aws"
  version = "v2.0.0" # Pin the module version
}
```

In this example, we've pinned the version of the `terraform-aws-modules/vpc/aws` module to `v2.0.0`. When you run `terraform init`, Terraform will use this specific module version.

## Using the `required_providers` Block

Another approach to lock module versions is by using the `required_providers` block within your root module's configuration. This method not only locks module versions but also locks the provider version you intend to use.

Here's an example of how to use the `required_providers` block:

```bash
terraform {
  required_version = ">= 0.12, < 0.14" # Set the Terraform version constraint
}

provider "aws" {
  version = ">= 3.0, < 4.0" # Set the AWS provider version constraint
  region  = "us-east-1"
}

module "example_module" {
  source = "terraform-aws-modules/vpc/aws"
}

terraform {
  required_providers {
    aws = {
      source  = "hashicorp/aws"
      version = "3.0.0" # Pin the AWS provider version
    }
  }
}
```

In this example, we've pinned both the module (`terraform-aws-modules/vpc/aws`) and the AWS provider versions. When you initialize your Terraform configuration, Terraform will use the specified module and provider versions.

By using either of these methods, you can ensure that Terraform uses the exact versions of modules and providers that you've tested and approved for your infrastructure. This minimizes the risk of unexpected changes during deployments and contributes to the stability and reliability of your infrastructure code.

Locking Terraform module versions is a fundamental practice for any Terraform project, and it helps you maintain a solid and dependable infrastructure over time.

## 🛠️ Additional Methods (Optional)

In addition to the methods discussed above, there are alternative approaches to locking Terraform module versions:

### 1\. Using Git Tags

Git tags are a convenient way to mark specific releases of your modules in a Git repository. You can use these tags to lock module versions in your Terraform configurations.

### 2\. Terraform Module Sources with Fixed Versions

If you want to be even more explicit about the version you're using, you can specify a fixed version in the module source URL.

### 3\. Using Terraform CLI Flags

You can lock module versions using the Terraform CLI flags while running `terraform init`. This method is useful when you want to lock versions temporarily without modifying your configuration files.

### 4\. Module Pinning via Terraform Cloud or Enterprise

If you're using Terraform Cloud or Terraform Enterprise, you can leverage their workspace settings to pin module versions.

### 5\. Automate Version Updates

Consider using automation tools or scripts to regularly check for updates to your module dependencies.

Remember that the choice of method depends on your specific requirements and constraints. It's essential to select the one that best fits your project's needs while ensuring stability and predictability.

---

With Terraform, you're not just building infrastructure; you're sculpting it with precision and ensuring its reliability. The combination of modular composition and version locking empowers you to create, manage, and evolve infrastructure as code that stands the test of time.

Happy Terraforming!