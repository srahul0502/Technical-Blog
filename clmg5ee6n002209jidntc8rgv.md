---
title: "Mastering Terraform's HCL: Blocks, Parameters, Variables, and AWS EC2 Instances"
datePublished: Tue Sep 12 2023 10:06:25 GMT+0000 (Coordinated Universal Time)
cuid: clmg5ee6n002209jidntc8rgv
slug: mastering-terraforms-hcl-blocks-parameters-variables-and-aws-ec2-instances
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1694512334274/195ba8c8-3ba2-4b32-8b4e-de013b9173ee.webp
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1694513151565/945a6d96-a962-4b7d-8c0a-82c8e6d37536.png
tags: aws, devops, terraform, devops-articles, 90daysofdevops

---

# Introduction

Terraform is a powerful tool for managing infrastructure, and HCL is the language it uses to define configurations. In this guide, we'll break down HCL into digestible pieces, providing definitions, examples, and explanations to make your Terraform learning journey smooth and enjoyable.

# Understanding HCL Blocks, Parameters, and Arguments

## Introduction to HCL

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694511176837/23264167-c8c0-4ee0-a799-97230d77411b.webp align="center")

* HCL, or HashiCorp Configuration Language, is the language used by Terraform for defining infrastructure configurations. It is designed to be easy to read and write, making it accessible for both beginners and experienced infrastructure engineers. HCL uses a declarative syntax, meaning you specify what you want to create or configure, and Terraform takes care of the how.
    

## HCL Blocks

* In Terraform, configurations are organized into **blocks**. Each block serves a specific purpose and defines resources, providers, data sources, and more. Let's take a closer look at these blocks:
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694510243879/01c0b97e-91e9-4b9f-a12d-cfcc1b54f8c9.png align="center")
    

### Resource Blocks

* **Resource blocks** are used to declare infrastructure resources like virtual machines or databases. A resource block consists of the resource type, a resource name, parameters, and a set of arguments defining its properties. Here's an example:
    

```bash
resource "aws_instance" "example" {
 ami           = "ami-0c55b159cbfafe1f0"  # Argument: ami
 instance_type = "t2.micro"              # Argument: instance_type
}
```

* **Syntax Reference:**
    

```bash
resource "<RESOURCE_TYPE>" "<RESOURCE_NAME>" {
 <PARAMETER_NAME> = "<PARAMETER_VALUE>"
 ...
 <ARGUMENT_NAME>  = "<ARGUMENT_VALUE>"
 ...
}
```

### Data Source Blocks

* **Data source blocks** allow you to fetch information from existing resources outside your configuration. They are used to query external data and use it within your Terraform configuration. Data source blocks also have parameters and arguments. Here's an example:
    

```bash
data "aws_ami" "example" {
 most_recent = true                 # Argument: most_recent
 
 filter {
   name   = "name"                 # Argument: name
   values = ["my-ami-name"]        # Argument: values
 }
}
```

* **Syntax Reference:**
    

```bash
data "<DATA_SOURCE_TYPE>" "<DATA_SOURCE_NAME>" {
 <PARAMETER_NAME> = "<PARAMETER_VALUE>"
 ...
 <ARGUMENT_NAME>  = "<ARGUMENT_VALUE>"
 ...
}
```

### Why Blocks, Parameters, and Arguments Matter

* Understanding blocks, parameters, and arguments is essential because they form the foundation of your Terraform configurations. Blocks define what you want to create or query, parameters specify how it should behave, and arguments provide the values to make it happen.
    
* As you work with Terraform, you'll encounter various block types, each with its own set of parameters and expected arguments. Mastery of these concepts empowers you to build, modify, and manage infrastructure efficiently.
    
* With this understanding, you're well-equipped to dive deeper into Terraform and create complex infrastructure configurations with confidence. Remember to refer to Terraform's official documentation for specific block types, their associated parameters, and their expected arguments as you explore further.
    

# Parameters and Arguments in Terraform: What Are They?

## Parameters

* **Parameters** are like settings or options for creating something in Terraform. Think of them as the building blocks that tell Terraform what you want to create.
    
* In Terraform, parameters are attributes that define the behavior of a particular block. Each block type (e.g., resource, data, provider) has its own set of parameters, and these parameters specify what the block should do. Think of parameters as configuration settings for a block.
    

## Arguments

* **Arguments** are the specific details or values you provide to those settings or parameters. They tell Terraform exactly how you want to create something.
    
* Arguments are the values assigned to parameters. They determine the specific configuration of the block by providing the necessary values to the parameters. Arguments are where you define the properties or characteristics of the block you're creating.
    

### Example 1: Building a House

Imagine you're building a house with Terraform. Let's break it down:

### Parameters (Settings)

* **House Type**: This is a parameter. You can choose between "Single-Family" or "Apartment" as options.
    
* **Roof Material**: Another parameter. You can choose "Tiles" or "Metal."
    
* **Color**: A parameter for the color of your house. Options could be "Blue," "Red," or "Yellow."
    

### Arguments (Specific Choices)

* Now, let's add the arguments—the specific choices you make:
    

* You choose "Single-Family" as the **House Type**, so that's your argument for this parameter.
    
* For **Roof Material**, you decide on "Tiles."
    
* And for the **Color**, you go with "Blue."
    

So, in Terraform, you'd have something like:

```bash
house {
  type   = "Single-Family"   # Argument for House Type parameter
  roof   = "Tiles"           # Argument for Roof Material parameter
  color  = "Blue"            # Argument for Color parameter
}
```

### Example 2: Ordering Pizza

Let's apply the same idea to ordering pizza:

### Parameters (Pizza Options)

* **Size**: You can choose "Small," "Medium," or "Large."
    
* **Toppings**: Here, you get to pick what goes on your pizza. It's a parameter with lots of options.
    
* **Crust**: Options like "Thin," "Thick," or "Stuffed" for the crust type.
    

### Arguments (Your Pizza Order)

Now, let's make your pizza order—the specific choices:

* You choose a "Medium" pizza for the **Size**.
    
* For **Toppings**, you want "Pepperoni" and "Mushrooms."
    
* And you prefer a "Thin" crust.
    

So, in Terraform pizza terms:

```bash
pizza {
  size   = "Medium"          # Argument for Size parameter
  toppings = ["Pepperoni", "Mushrooms"]  # Argument for Toppings parameter
  crust  = "Thin"            # Argument for Crust parameter
}
```

## Example in terms of AWS EC2 Instance

### Example 1: Resource Block (AWS EC2 Instance)

In this example, we'll create a resource block for an AWS EC2 instance using Terraform. Here's the syntax:

```bash
resource "aws_instance" "example" {
  ami           = "ami-0c55b159cbfafe1f0"  # Argument: ami
  instance_type = "t2.micro"              # Argument: instance_type
}
```

In this code snippet:

* `aws_instance` is the resource type.
    
* `"example"` is the resource name.
    
* `ami` and `instance_type` are parameters.
    
* `"ami-0c55b159cbfafe1f0"` and `"t2.micro"` are arguments assigned to the parameters.
    

### Example 2: Data Source Block (AWS AMI Data)

In this example, we'll use a data source block to fetch information about an AWS AMI. Here's the syntax:

```bash
data "aws_ami" "example" {
  most_recent = true                 # Argument: most_recent
  
  filter {
    name   = "name"                 # Argument: name
    values = ["my-ami-name"]        # Argument: values
  }
}
```

In this code snippet:

* `aws_ami` is the data source type.
    
* `"example"` is the data source name.
    
* `most_recent`, `name`, and `values` are parameters.
    
* `true`, `"name"`, and `["my-ami-name"]` are arguments assigned to the parameters.
    

In both examples, parameters (`ami`, `instance_type`, `most_recent`, `name`, `values`) define the configuration settings for the blocks (resource or data source), while arguments provide the specific values for those settings.

In Terraform, parameters are like the options on a menu, such as choosing the size of a pizza or the type of house. Arguments, on the other hand, are your specific selections from that menu, like ordering a medium pizza or a single-family house. These parameters and arguments are used to tell Terraform exactly what you want to create or configure in your infrastructure. Terraform's documentation provides detailed information on what parameters are available and what values they expect for different parts of your infrastructure.

# Variables, Data Types, and Expressions in HCL: What Are They?

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694511149847/d3b7c6c4-5435-4795-8c22-c20e7288dd1f.png align="center")

**Variables** are like placeholders where you can store different pieces of information you might need later. It's like putting labels on containers to help you remember what's inside.

**Data Types** are categories that tell you what kind of information you're storing in those containers. For example, you might have containers for numbers, words, or true/false statements.

**Expressions** are like the math you use to calculate something. You can use expressions to work with the information stored in your containers (variables).

## Example 1: Grocery Shopping List

Imagine you're making a grocery shopping list with Terraform concepts:

### Variables (Containers)

* **Fruits**: This is a variable where you'll store different fruits you want to buy.
    
* **Budget**: Another variable that holds the amount of money you're willing to spend.
    

### Data Types (Types of Information)

Now, let's talk about data types, which define what kind of information you're storing:

* **Fruits** is a list variable, so it can store multiple items.
    
* **Budget** is a number variable, as it represents an amount in dollars.
    

### Expressions (Calculations)

You can also use expressions to help you shop:

* When you add up the prices of all the fruits you want, that's an expression.
    
* Comparing the total cost with your budget is another expression to decide if you can afford everything.
    

So, in Terraform grocery terms:

```bash
shopping_list {
  fruits = ["Apples", "Bananas", "Oranges"]  # List of fruits (Variable)
  budget = 50                               # Budget in dollars (Variable)
}

total_cost = price("Apples") + price("Bananas") + price("Oranges")  # Expression to calculate total cost

can_afford_all = total_cost <= budget  # Expression to check if you can afford everything
```

## Example 2: Travel Planning

Let's apply the same idea to planning a trip:

### Variables (Containers)

* **Destination**: A variable to store the name of the place you want to visit.
    
* **Distance**: Another variable for how far it is from your home.
    

### Data Types (Types of Information)

* **Destination** is a text variable since it stores words.
    
* **Distance** is a number variable since it's about miles or kilometers.
    

### Expressions (Calculations)

You can use expressions to make decisions about your trip:

* Checking if the distance is manageable in a day is an expression.
    
* Comparing the destination with your dream vacation spot is another expression to see if it matches.
    

So, in Terraform travel terms:

```bash
travel_plan {
  destination = "Paris"     # Destination (Variable)
  distance    = 3000       # Distance in miles (Variable)
}

can_reach_in_a_day = distance <= 500  # Expression to check if you can reach it in a day

dream_destination = destination == "Bora Bora"  # Expression to compare with your dream spot
```

In Terraform, variables are like labeled containers (e.g., fruits, destination), data types tell you what's inside (e.g., text, number), and expressions are the calculations or decisions you make (e.g., total cost, can reach in a day). This helps Terraform understand and use the information you provide.

Another Example for Data Type and Expression : Sure! Let's create a similar example that defines variables, data types, and expressions in Terraform using a person's information.

```bash
variable "age" {
  type    = number
  default = 25
}

variable "name" {
  type    = string
  default = "Alice Smith"
}

variable "is_student" {
  type = bool
  default = false
}

output "greeting" {
  value = "Hello, ${var.name}. You are ${var.age} years old."
}

output "student_status" {
  value = var.is_student ? "You are a student." : "You are not a student."
}
```

In this example:

1. We have defined three variables:
    
    * `age` (Number): Represents the person's age. The default value is set to 25.
        
    * `name` (String): Represents the person's name. The default value is "Alice Smith."
        
    * `is_student` (Boolean): Represents whether the person is a student. The default value is set to false.
        
2. We use the `output` blocks to display information:
    
    * `greeting`: Generates a greeting message that includes the person's name and age.
        
    * `student_status`: Determines whether the person is a student based on the `is_student` variable and provides a corresponding status message.
        

This example demonstrates how Terraform variables, data types (number, string, bool), and expressions can be used to manage and display information about a person.

# Practice writing Terraform configurations using HCL syntax

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694510907961/3857ae71-1a62-40c3-aea5-57a06ae9fcd3.png align="center")

## Let's create an AWS instance using HCL syntax

Certainly! Here's the detailed guide for creating an AWS EC2 instance using Terraform, including explanations of the syntax:

**Creating an AWS EC2 Instance with Terraform: Step-by-Step Guide**

**Step 1: Set Up Your Terraform Environment**

Before you begin, ensure you have Terraform installed on your system. If you haven't already installed it, you can download it from the official Terraform website [here](https://www.terraform.io/downloads.html).

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694505786486/8361d44f-47df-4ffb-92a8-8a9f6c821fc8.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694506468784/0d39c899-8a51-4f2c-9f7b-00d1fe58fab2.png align="center")

**Step 2: Configure AWS Credentials**

Ensure you have AWS credentials configured on your system. You can do this by setting up your AWS Access Key ID and Secret Access Key as environment variables or by using the AWS Command Line Interface (CLI) with `aws configure`.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694506484733/2a17d94b-9d60-40c4-a05d-024a4cf80ed7.png align="center")

**Step 2: Create a Terraform Configuration File**

Create a new directory for your Terraform project and create a `.tf` file (e.g., `main.tf`) to define your infrastructure.

```bash
# main.tf

# Configure the AWS provider
provider "aws" {
  region = "us-east-1"  # Modify the region as needed
}

# Create an AWS EC2 instance
resource "aws_instance" "MyInstance" {
  ami           = "ami-053b0d53c279acc90"  # Specify your desired AMI ID
  instance_type = "t2.micro"     # Choose the instance type

  tags = {
    Name = "TerraInstance"
  }
}
```

In this Terraform configuration:

* The `provider` block configures the AWS provider and specifies the AWS region you want to use. You can modify the `region` attribute as needed.
    
* The `resource` block defines an AWS EC2 instance using the `aws_instance` resource type. Customize the `ami`, `instance_type`, `key_name`, `subnet_id`, and tags according to your requirements.
    
* If you haven't installed terraform , you can include that within this under required\_providers block Certainly! Here's the Terraform code for creating an AWS EC2 instance with `required_providers` in a more readable format:
    

```bash
# main.tf

# Declare the required AWS provider and version
terraform {
  required_providers {
    aws = {
      source  = "hashicorp/aws"
      version = "3.0.0"  # Specify the desired AWS provider version
    }
  }
}

# Configure the AWS provider
provider "aws" {
  region = "us-east-1"  # Modify the region as needed
}

# Define the AWS EC2 instance
resource "aws_instance" "example" {
  ami           = "ami-12345678"  # Specify your desired AMI ID
  instance_type = "t2.micro"     # Choose the instance type
  key_name      = "your-key-pair-name"  # Specify your SSH key pair
  subnet_id     = "subnet-123456789"    # Specify the subnet ID

  tags = {
    Name = "ExampleInstance"
  }
}
```

In this format:

* We have comments for each section to explain its purpose.
    
* The `required_providers` block is clearly labelled to indicate that it declares the AWS provider and specifies the version.
    
* The `provider` block for AWS specifies the region.
    
* The `resource` block for AWS EC2 instance includes comments for each parameter to describe its purpose.
    

**Step 3: Initialize Terraform**

Open a terminal or command prompt and navigate to the directory containing your Terraform configuration

In your project directory, run the following command to initialize Terraform:

```bash
terraform init
```

This command initializes Terraform and downloads the necessary provider plugins.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694507665728/c4a48277-64b2-4a6f-b245-128e6db15ef1.png align="center")

**Step 4: Preview Changes**

Use the `terraform plan` command to preview the changes Terraform intends to make:

```bash
terraform plan
```

This command displays a summary of the changes Terraform plans to apply based on your configuration.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694507804803/f7a24529-ab3b-4f5b-aa54-127f4c8aea76.png align="center")

**Step 5: Apply Changes**

If the plan looks correct and you're ready to create the EC2 instance, run:

```bash
terraform apply
```

Terraform will prompt you for confirmation. Type `yes` to proceed.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694508829693/fef19079-d992-4e22-8e31-444c98a0dc9d.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694508834754/5b1c4dfc-2d52-4ca5-b998-032fae896d9e.png align="center")

**Step 6: Verify the EC2 Instance**

After the `apply` command completes, Terraform will provide information about the resources it created. You can also verify the EC2 instance's status in the AWS Management Console.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694508845266/9e00d7a7-fb9b-4a7b-8fe2-edb6518f0ae1.png align="center")

**Step 7: Destroy Resources (Optional)**

If you want to remove the resources created by Terraform, you can run:

```bash
terraform destroy
```

This command will prompt you for confirmation before deleting any resources.

**Step 9: Clean Up**

Always remember to clean up resources when you're done to avoid unexpected charges. Use the `terraform destroy` command or delete resources manually from the AWS Management Console.

By following these steps, you've successfully created an AWS EC2 instance using Terraform and gained a better understanding of Terraform configuration syntax and usage. You can further customize your infrastructure by adding more resources and configurations to your Terraform files.

> I hope you understood the concept of Terraform configuration syntax and usage
> 
> Happy Terraforming :D