---
title: "Jenkins Freestyle Project"
datePublished: Sun Aug 13 2023 07:10:54 GMT+0000 (Coordinated Universal Time)
cuid: cll93x4ia000009jwbphl88i9
slug: jenkins-freestyle-project
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1691910604745/bb8132af-6a07-4900-a47e-bc4b2930e610.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1691910643680/6236a86e-faff-45ea-b433-b6524d60ba65.png
tags: devops, jenkins, 90daysofdevops, 90daysofdevops-devops-projectdevelopment-nonitbackground-github-docker-cloudplatforms-ec2-aws-elasticbeanstalk-lambdafunctions-devopspipelines-terraform-jenkins-docker-devsecops-scm-git-gitlab-bitbucket-buildtools-griddle-maven-ant-msbuild-monitoringtools-prometheus-grafana-ansible-ai-chatgpt-valueaddition-realworldproblems, freestyle-jenkins-project

---

## What is CI/CD⁉️

* The practise of automating the integration of code changes from multiple developers into a single codebase is known as Continuous Integration (CI). It is a software development practise in which developers frequently commit their work to a central code repository (Github or Stash). Then, upon integration, there are automated tools that build the newly committed code and perform code reviews, among other things. Continuous Integration's main goals are to find and fix bugs faster, to make the process of integrating code across a team of developers easier, to improve software quality, and to reduce the time it takes to release new feature updates.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691864868094/190df95e-3d22-4c83-be55-0d72e22e035c.png align="center")
    
* Continuous Delivery (CD) is performed after Continuous Integration to ensure that new changes are delivered to our customers in a timely and error-free manner. This includes performing integration and regression tests in the staging area (which is similar to the production environment) to ensure that the final release does not fail in production. It ensures that the release process is automated so that we always have a release-ready product and can deploy our application at any time.
    

## What Is a Build Job⁉️

A Jenkins build job contains the settings for automating a specific task or step in the application development process. Gathering dependencies, compiling, archiving, or transforming code, and testing and deploying code in various environments are examples of these tasks.

Jenkins provides support for a variety of build jobs, including freestyle projects, pipelines, multi-configuration projects, folders, multibranch pipelines, and organisation folders.

## Types Of Jobs ⁉️

Majorly used job types are :

1. **Freestyle project:**
    
    * One of the most basic job types is the freestyle project. It allows you to define a build sequence using a graphical interface. Each step can consist of actions such as compiling code, running tests, deploying artefacts, and more. While it provides flexibility, it may necessitate more manual configuration than other job types.
        
2. **Pipeline:**
    
    * Jenkins is in charge of the pipeline. Pipeline is a powerful and adaptable programming language for defining build and deployment processes. You can script your entire build pipeline, including stages, steps, conditional logic, and parallel execution. This type is commonly used for complex and adaptable automation workflows.
        
3. **Multibranch Pipeline:**
    
    * When dealing with multiple branches of code, which is common in software development, this type of job is critical. It detects and builds branches automatically, ensuring continuous integration for each branch. It is especially useful for keeping separate pipelines for different branches.
        
4. **Parameterized Build:**
    
    * Parameterized builds are commonly used when it is necessary to customise builds based on various inputs. This job type allows users to provide parameters when triggering a build, allowing for build process variations.
        
5. **Scheduled Build:**
    
    * Scheduled builds are used to automate repetitive tasks at predefined times or on a recurring basis. They are frequently used for tasks such as nightly builds, backups, and maintenance operations.
        
6. **GitHub Organisation:**
    
    * As more projects are hosted on platforms like GitHub, the GitHub Organisation job type aids in the automation of project discovery and creation within a GitHub organisation. It simplifies the integration of GitHub projects with Jenkins.
        
7. **Distributed Build:**
    
    * This job type is critical for improving resource utilisation and shortening build times. It entails distributing build tasks across multiple agents or nodes, allowing builds to run concurrently on different machines.
        

## What is a freestyle Project ⁉️

The basic understanding is mentioned above..

Let's understand this in brief by making a freestyle project:

* create a agent for your app. ( which you deployed from docker in earlier task)
    
* Create a new Jenkins freestyle project for your app.
    
* In the "Build" section of the project, add a build step to run the "docker build" command to build the image for the container.
    
* Add a second step to run the "docker run" command to start a container using the image created in step 3.
    

**Step 1:** Set-up your jenkins by following [this](https://srdev.hashnode.dev/getting-started-with-jenkins)

**Step 2:** When you see your dashboard, go to create job

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691904791367/5391f9fe-b2f9-4af8-b459-29ed5e168233.png align="center")

**Step 3:** Enter item name and select the type of project

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691906182817/c5058868-ec8d-4c39-9ff5-34b95947a359.png align="center")

**Step4 :** The next step is configuration , give a suitable description and add url of your github repo(project)

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691906324174/34a840a4-1569-4624-82c9-4b58e1fa06fb.png align="center")

**Step 5:** Scroll down and check on git in Source code management , paste your github project url , Go to Build steps and select Execute Shell and give the command you want to execute. Make sure you have added inbound rule for port 8000 in your EC2 instance

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691906452943/7fc7454b-09b8-4f8f-a66c-7322cf688bb8.png align="center")

**Step 6:** Save it and click on build now

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691906602197/6af32de6-646c-481c-8bc0-e561d7fb5565.png align="center")

**Step 7 :** Click on the build number and go to console output to see how's the process going on

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691906705818/b860df46-560f-4f77-949f-677a0d8ac5d1.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691906718739/7a51d3d0-25d5-4cfe-8348-23f3e9379c21.png align="center")

**Output:**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691906746337/e74fb763-3ed8-49dd-a555-7b04333765af.png align="center")

**Let's do the same with two-tier flask application:**

* Clone the repro from [github repository](https://github.com/srahul0502/two-tier-flask-app.git)
    
* All the steps are same as above :
    
    * give your description, github url , Select git in Source Code Management and paste the url .
        
* There is a change when you will go to build steps
    
    * Select execute shell
        
    * Use `docker-compose` to bring up the container
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691907344053/f8b4e31d-71bd-4eaf-8fe6-0128f74cbbef.png align="center")
        
    * We used `docker-compose down` to bring down the container if it's already running.
        
* Now , as we did in the above project , click on build number and go to console output.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691907432660/dbc9dc30-fe39-4198-b2c1-df701fb64914.png align="center")
    
* Tadaaa 🥳🥳 , You have successfully created a freestyle project !!
    

> I hope now you can create your own free-style projects on Jenkins  
> Make sure you go through the previous blog to setup your Jenkins successfully
> 
> Happy Learning :D