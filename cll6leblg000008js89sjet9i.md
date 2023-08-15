---
title: "Getting Started with Jenkins"
datePublished: Fri Aug 11 2023 12:56:52 GMT+0000 (Coordinated Universal Time)
cuid: cll6leblg000008js89sjet9i
slug: getting-started-with-jenkins
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1691758556565/787e8cbe-d167-4782-8a78-e61ed05fc9dc.webp
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1691758604059/55c403a8-1a97-4816-9d8d-27b27858abc3.png
tags: devops, jenkins, devops-articles, 90daysofdevops, 90daysofdevops-devops-projectdevelopment-nonitbackground-github-docker-cloudplatforms-ec2-aws-elasticbeanstalk-lambdafunctions-devopspipelines-terraform-jenkins-docker-devsecops-scm-git-gitlab-bitbucket-buildtools-griddle-maven-ant-msbuild-monitoringtools-prometheus-grafana-ansible-ai-chatgpt-valueaddition-realworldproblems

---

## What is Jenkins⁉️

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691743461119/21b3f5da-8c36-44e2-ae3e-bb12976faa1c.gif align="center")

* Jenkins is a Java-based open source continuous integration-continuous delivery and deployment (CI/CD) automation software DevOps tool. It is used to implement pipelines, which are CI/CD workflows.
    
* Jenkins uses plugins to achieve Continuous Integration. Plugins enable the integration of different DevOps stages. If you want to integrate a specific tool, you must first install its plugins. For instance, Git, Maven 2 projects, Amazon EC2, HTML publishers, and so on.
    
* Jenkins is an automation tool that is an open-source server that allows all developers to build, test, and deploy software. Because it is written in java, it works or runs on java. We can use Jenkins to perform continuous integration of projects (jobs) or end-to-end automation.
    

## How and where it is used ❓🤔

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691746839078/14d9ee4f-95b1-4671-b87b-011758e37131.png align="center")

* The strength of Jenkins lies in its ability to automate and orchestrate various stages of the software development lifecycle. In this chapter, we'll look at how Jenkins is used to streamline development processes in real-world scenario.
    
* **CI (Continuous Integration):**
    
    * Continuous Integration entails integrating code changes from multiple developers into a shared repository regularly. Jenkins is critical in automating this process:
        
    * Jenkins can monitor version control systems (for example, Git) for new commits. Jenkins pulls the most recent code when changes are detected.
        
    * Jenkins can initiate the build process, which includes compiling the code and generating executable artefacts.
        
    * Jenkins can run unit tests to ensure that code changes have not introduced new bugs or regressions.
        
    * Jenkins generates comprehensive reports on build status, test results, and code coverage. If any tests fail, developers are notified immediately.
        
* **Continuous Delivery (CD):**
    
    * **Continuous Delivery** extends the CI process by automating the deployment of tested code to various environments, ensuring that it's ready for release.
        
    * **Staging and QA**: Jenkins can deploy the built artefacts to staging or QA environments, allowing testing in an environment that closely resembles production.
        
    * **Integration Testing**: Automated integration tests can be run to verify that different components of the software work harmoniously.
        
    * **User Acceptance Testing (UAT)**: Jenkins can facilitate UAT by deploying to a UAT environment, where stakeholders can validate the software.
        
    * **Production Deployment**: Once the software passes all tests and approvals, Jenkins can automate the deployment to production, minimizing manual intervention and potential errors.
        
* **Automation Pipelines:**
    
    * One of Jenkins' key features is the ability to define pipelines as code, which offers several benefits.
        
    * **Reproducibility**: Pipeline code stored in version control ensures that pipeline configurations are consistent across environments.
        
    * **Versioning**: Changes to the pipeline can be tracked, enabling easy collaboration and rollbacks if needed.
        
    * **Scalability**: Jenkins pipelines can be designed to run on multiple agents simultaneously, distributing workload and reducing build times.
        
* **Scheduled Jobs and Triggered Builds:**
    
    * Jenkins can be configured to perform tasks on a schedule or in response to events:
        
        * **Nightly Builds**: Regular nightly builds can be scheduled to ensure that code changes from different developers are integrated daily.
            
        * **Triggered Builds**: Jenkins can be set to build and test whenever a specific event occurs, like a new commit, a pull request, or a code merge.
            
* **Notifications and Reporting:**
    
    * Jenkins keeps development teams informed about the status of builds and deployments.
        
    * **Email Notifications**: Developers receive email notifications about build results, test failures, and other critical events.
        
    * **Integration with Chat Tools**: Jenkins can be integrated with messaging platforms like Slack, providing real-time updates to development teams.
        
* **Plugin Integration:**
    
    * Jenkins' plugin ecosystem enhances its functionality:
        
    * **Version Control Integration**: Plugins enable seamless integration with version control systems, fetching code updates and triggering builds.
        
    * **Cloud Services**: Jenkins can use plugins to interact with cloud services like AWS, Azure, and Google Cloud, facilitating deployment and infrastructure management.
        

## Benefits of using Jenkins📈

**1\. Automation: Making Things Easier and Error-Free**

Imagine having a robot assistant that can take care of repetitive tasks for you. Jenkins is like that for developers. It does the repetitive and boring tasks automatically, which means fewer chances of mistakes and faster work.

**2\. Continuous Integration (CI): Catching Mistakes Early**

Picture this: you're building a puzzle, and you check every piece as you add it to make sure it fits perfectly. That's what Jenkins does with code. It checks the pieces of code as they're added, finding any problems before they become big issues. This helps fix things faster and keeps the project moving smoothly.

**3\. Continuous Delivery (CD): Smooth Delivery of Ready Stuff**

Think of Jenkins as a super-efficient delivery service for software. Once the code is checked and ready, Jenkins makes sure it's delivered to where it's supposed to go—like a staging area for testing or directly to the real users. This saves time and effort and ensures that only reliable code reaches the users.

**4\. Extensibility: Tailoring to Your Needs**

Imagine a toolbox with tons of tools that you can pick and choose from to create your perfect toolkit. Jenkins is a bit like that. It comes with a bunch of tools (called plugins) that you can use to add new features or customize things to fit your project's unique needs.

**5\. Scalability: Growing Without Problems**

Think of your project like a garden. As it grows, you need more space and resources to keep it healthy. Jenkins can handle small gardens and huge ones too. It can spread its work across multiple computers, so your project can keep growing without slowing down.

In simple terms, Jenkins is like a reliable helper that automates tasks, catches problems early, delivers code smoothly, can be customized to your liking, and grows with your project. It's like having a superhero sidekick for your software development journey!

## How to install 🤯⁉️

**Step 1: Checking Java** Before you start, you need to make sure your computer has Java installed. Think of Java as the engine that powers Jenkins.

1. Open your terminal: This is like a text-based control center for your computer.
    
2. Type in: `java -version`
    
3. Press Enter.
    

If you see a version number (like "Java 11" or similar), you're good to go. If you don't see anything or it says Java is not found, you need to install Java before proceeding.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691749088035/5d92df81-c621-4e14-aa4b-86c5a0997be7.png align="center")

```bash
# Install java
sudo apt-get install openjdk-17-jdk
```

**Step 2: Installing Jenkins**

```bash
curl -fsSL https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key | sudo tee \
  /usr/share/keyrings/jenkins-keyring.asc > /dev/null
echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
  https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null
sudo apt-get update
sudo apt-get install jenkins
```

* Run the above code in your terminal and jenkins will be install in your system
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691749701055/3a56af5d-2806-445d-aa7d-06bb96fc4085.png align="center")
    

**Step 3 Checking Status :**

* To check the status you can run `service jenkins status`
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691749733995/cdd0949c-8d56-47c0-a56a-151a7bebc582.png align="center")
    
* If it's not running you can run `systemctl start jenkins` and to start jenkins automatically run `systemctl enable jenkins`
    

**Step 4: Accessing Jenkins**

1. Open your web browser (like Chrome, Firefox, or Edge).
    
2. In the address bar at the top, type: [`http://localhost:8080`](http://localhost:8080) and press Enter.
    
    Here i have typed and IP:port
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691750136470/cf870aa7-977a-400d-be30-c68e60efbbd8.png align="center")
    
3. A page will appear asking for a password. To find the password, go back to the terminal and type: `sudo cat /var/lib/jenkins/secrets/initialAdminPassword`
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691750292322/1551682e-ce7b-442a-aaad-04e3cd85060e.png align="center")
    
4. Copy the password from the terminal and paste it into the password field on the browser page.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691750335100/82925310-43e5-452d-8589-3f82376f063c.png align="center")
    
5. Follow the on-screen instructions to finish setting up Jenkins, creating an admin user, and installing suggested plugins .
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691750395238/2c274532-daf0-4e8e-b13f-3a51f50d7846.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691750520658/e02f7cdc-925d-43a1-b083-1bb57a255440.png align="center")
    
6. Follow the instructions and create first admin user
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691751541700/074c5a62-9372-4ab1-8634-35c344a54fb9.png align="center")
    
7. After finishing all the steps , you will see this window
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691751630240/5c72c7d6-7e0d-4f9a-af83-66b098ba4ea0.png align="center")

## Hands-On 💻

* Let's create a freestyle pipeline to print "Hello World!!" or any message you want .
    
* After logging in to jenkins dashboard , click on <mark>New Item</mark> to create a new job.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691753324491/0e59b0b4-3e55-4e27-adda-ee1089018d42.png align="center")
    
* Now , it will ask you to enter item name and choose the type of project , wrtie your item name and select <mark>freestyle project</mark> and click on OK .
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691753423715/a3bdb82e-e436-4e0a-a2cf-10d8f4f5895e.png align="center")
    
* After this , it will ask you for a description , you can give any simple description for this .
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691753589676/25bc223b-6e6c-46c2-93b3-18fba03afa86.png align="center")
    
* Now scroll down till u find <mark>Build steps</mark> , click on it and select <mark>Execute Shell</mark> and enter the command you want to execute and save .
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691753669432/c7ffe394-487a-4cf8-8e45-d0a506e3df01.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691753764260/59778c1a-77fd-40c0-a359-39bded11e429.png align="center")
    
* Now click on Build Now to build the project .
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691753773901/258ab49b-7a7c-4701-a425-7f0b4fdfe658.png align="center")
    
* When the build is finished, click on the build number on the left hand side to see the console output. The output of the "echo" command will be displayed.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691753871519/d92bace9-461d-4772-bb0e-9ab958a9e84f.png align="center")
    

> I hope now you can create your own freestyle projects on Jenkins..!
> 
> Happy Learning :D