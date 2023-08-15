---
title: "Getting Started With Jenkins Declarative Pipeline"
datePublished: Tue Aug 15 2023 04:49:52 GMT+0000 (Coordinated Universal Time)
cuid: cllbtrg5q000208l49yln1i04
slug: getting-started-with-jenkins-declarative-pipeline
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1692074890094/d0d49456-219c-4c56-acc0-287d39842e25.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1692074954282/d805373d-a48e-4790-9cd1-a79772ac5602.png
tags: devops, jenkins, 90daysofdevops, 90daysofdevops-chanllenge, 90daysofdevops-devops-projectdevelopment-nonitbackground-github-docker-cloudplatforms-ec2-aws-elasticbeanstalk-lambdafunctions-devopspipelines-terraform-jenkins-docker-devsecops-scm-git-gitlab-bitbucket-buildtools-griddle-maven-ant-msbuild-monitoringtools-prometheus-grafana-ansible-ai-chatgpt-valueaddition-realworldproblems

---

## 📜 Some basic terms for understanding

**What is a Pipeline ⁉️**

* A pipeline is a collection of steps or jobs interlinked in a sequence.
    
* **Example:** Imagine you're baking a cake. You have a step-by-step process: mixing ingredients, baking, and decorating. A pipeline is like this process, but for software. It's a set of automated steps that take your code and handle things like testing and putting it live. This way, changes to your code are tested and deployed consistently.
    

**What do you mean by Declarative pipeline**⁉️

* Declarative is a more recent and advanced implementation of a pipeline as a code.
    
* **Example:** Think of this like a recipe card with simple instructions. It's a modern way to describe your software pipeline. You write down the steps in an easy-to-read way, focusing on what each step does. It's like following a straightforward recipe without getting too fancy.
    

**What is a Scripted Pipeline**⁉️

* Scripted was the first and most traditional implementation of the pipeline as a code in Jenkins. It was designed as a general-purpose DSL (Domain Specific Language) built with Groovy.
    
* Example: This is like being a skilled chef who can create recipes from scratch. With Scripted Pipelines, you have more control and freedom. You can write detailed instructions using a special scripting language. It's like crafting a recipe exactly the way you want it, but it might get a bit complex.
    

**What is the difference between declarative and scripted pipeline**⁉️

* Both Declarative and Scripted Pipelines help automate the process of making and delivering software. Declarative is like using a simple recipe card, while Scripted gives you the power to create a custom recipe. Which one you choose depends on how complicated your software process is and how comfortable you are with writing special instructions.
    

# 📜 Why you should have a Pipeline🤔

Let's understand this by comparing without pipeline and with pipeline:

Imagine you're building a mobile app that lets users create and share to-do lists. You and your team are constantly adding new features and fixing bugs. Without a pipeline, your process might look something like this:

**Without a Pipeline:**

1. A developer makes changes to the code.
    
2. They manually build the app on their local machine.
    
3. They do some testing, but it's hard to cover all scenarios.
    
4. If everything seems okay, they manually upload the app to a server for deployment.
    
5. Sometimes it works fine, but other times the app breaks in unexpected ways.
    
6. You spend a lot of time troubleshooting and fixing issues in production.
    
7. The process is slow, error-prone, and you're not sure which version of the app is running where.
    

Now, let's see how having a pipeline improves this situation:

**With a Pipeline:**

1. A developer makes changes to the code and pushes them to the version control system (e.g., Git).
    
2. The pipeline automatically detects the code changes and starts the process.
    
3. The pipeline first builds the app, converting the code into a working application.
    
4. Automated tests run on the built app to check for bugs and issues.
    
5. If the tests pass, the pipeline deploys the app to a testing environment.
    
6. Automated tests run again in the testing environment to catch any environment-specific issues.
    
7. If all tests pass, the pipeline can deploy the app to a staging environment for final testing.
    
8. Once the app is thoroughly tested in the staging environment, the pipeline can deploy it to the production environment for users to access.
    
9. The entire process is automated, repeatable, and consistent.
    

In this example, a pipeline streamlines your development and deployment process, making it faster, more reliable, and less error-prone. It's like having a conveyor belt that takes your code through various checks and stages before it reaches your users.

## How to create a Jenkins pipeline🤔⁉️

The definition of a Jenkins Pipeline is written into a text file (called a <mark>Jenkinsfile</mark>) which in turn can be committed to a project’s source control repository. This is the foundation of "Pipeline-as-code"; treating the CD pipeline as a part of the application to be versioned and reviewed like any other code.

In the context of Jenkins, pipelines are defined using the <mark>Groovy scripting language</mark>. Groovy is a dynamic programming language that runs on the Java Virtual Machine (JVM), which makes it suitable for integration with Java-based tools and frameworks like Jenkins

Creating a Jenkinsfile and committing it to source control provides several immediate benefits:

* Automatically creates a Pipeline build process for all branches and pull requests.
    
* Code review/iteration on the Pipeline (along with the remaining source code).
    

Pipeline Syntax:

```plaintext
pipeline {
    agent any 
    stages {
        stage('Build') { 
            steps {
                // 
            }
        }
        stage('Test') { 
            steps {
                // 
            }
        }
        stage('Deploy') { 
            steps {
                // 
            }
        }
    }
}
```

## Hands-on💻

* Create a New Job, this time select Pipeline instead of Freestyle Project.
    
* Follow the Official Jenkins [Hello world example](https://www.jenkins.io/doc/pipeline/tour/hello-world/)
    
* Complete the example using the Declarative pipeline
    

**Pre-requisite:**

* Make sure you <mark>install docker </mark> otherwise it will be line DOCKER ❓ WHO❓and add user, jenkins to docker group by using `sudo usermod -aG docker $USER` , `sudo usermod -aG docker jenkins`
    
* And install <mark>docker pipeline plugin </mark> from manage jenkins&gt;plug in &gt;Available plugin
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692077926096/57b5c945-7564-4345-9244-6f8c74820cfd.png align="center")
    

**Step 1 :** From your jenkins dashboard click on create job/ new item( If you don't know how to do that it's never late , you can refer [this](https://srdev.hashnode.dev/getting-started-with-jenkins) ) , then give <mark>name to your job</mark> and select <mark>pipeline</mark> .

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692073487583/759b2365-0220-4f5d-962e-50eb4dc95c23.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692073501523/d2c0afce-7450-4439-8e1e-8d2ef7bc6a4e.png align="center")

**Step 2:** Give a description as you want , scroll down under pipeline script , paste / write your script , save it and click on build now.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692073591273/b0acf4ac-0c5f-4367-b5ab-cd1867ccb1f0.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692073615088/d5be1b05-5c14-4b9b-a777-fd6f3a55addf.png align="center")

> you can refer [Hello world example](https://www.jenkins.io/doc/pipeline/tour/hello-world/) for the basic scripts

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692073712770/f65084bb-2962-48e7-9e0d-a4226ad29282.png align="center")

That's it..!! you have created your first pipeline

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692073872514/dc7e247b-6669-4c71-b066-81e7e6c3aaf3.png align="center")

You can click on build number (left hand side bottom) for console output and pipeline steps .

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692073931021/f97d31a7-abb8-4941-9ef9-4e3d8807224a.png align="center")

> You can add your github repo in the step 2 where you give a description , Jenkins will automatically detect any new Branches or Pull Requests that are created in your repository and start running Pipelines for them.

> I hope now you can create your pipelines !!
> 
> Will learn more about them in further blogs
> 
> Stay tuned !!
> 
> Happy Learning :D