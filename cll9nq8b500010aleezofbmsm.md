---
title: "Complete Jenkins CI/CD Project"
datePublished: Sun Aug 13 2023 16:25:25 GMT+0000 (Coordinated Universal Time)
cuid: cll9nq8b500010aleezofbmsm
slug: complete-jenkins-cicd-project
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1691938395447/04e5b963-092a-4680-825a-2a99ce4fb39f.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1691943873323/faff23dc-cb50-4e28-9f55-5819e4523c58.png
tags: devops, jenkins, cicd-cjy1vtdk2005kjjs17n8couc3, devops-articles, 90daysofdevops

---

## 🔁CI/CD

1. **Building and Checking (Continuous Integration):** Imagine you're all working on a big puzzle together. Whenever someone adds a new puzzle piece, Jenkins steps in to make sure it fits well and looks good. This helps prevent any odd or mismatched pieces from sneaking in. If there's a problem, Jenkins raises a flag so you can fix it before things get messy.
    
2. **Testing and Delivering (Continuous Deployment):** Once the puzzle is complete, Jenkins helps you do some tests to make sure everything works smoothly. It's like trying out the puzzle to see if all the parts are in the right place. If anything seems off, Jenkins lets you know so you can fix it before others see the puzzle.
    
3. **Guiding the Process (Pipeline Automation):** Think of Jenkins as a coach helping you play a game. It breaks down the puzzle-solving into steps: first finding the right pieces, then assembling them, and finally making sure everything's working. Whenever you finish one step, Jenkins tells you to move on to the next. This helps you avoid mistakes and confusion.
    

So, Jenkins is like your clever friend who watches over the puzzle-making process. It makes sure the pieces fit well, tests everything to make sure it's right, and helps you follow the right steps. This way, you can build and share your puzzle (or software) without any headaches!

## Hands-on💻

* Fork this [repo](https://github.com/srahul0502/node-todo-cicd/blob/master/views/todo.ejs) to your repository .
    
* Follow [these](https://srdev.hashnode.dev/jenkins-freestyle-project) steps to create a jenkins job , all the steps are same except few steps that is github integration which i will be showing here
    
* The first step is to generate a ssh key first using `ssh-keygen`
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691941567024/1087af18-ca7e-4cf4-beff-cf478c1dd89d.png align="center")
    
* As you can see , a private key (id\_rsa) and a public key (id\_rsa.pub) is generated.
    
* Now go to your github account &gt; settings &gt; SSH and GPG keys &gt; create
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691941667432/0e574de2-b248-445f-9593-3971481c9774.png align="center")
    
* Paste the public key in the key section and click on add SSH key.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691941715170/1f6e5a41-78ee-4bf3-9d30-2f63ab7cd0d2.png align="center")
    
    * As you can see the Authentication is generated
        
* Now , in jenkins go to configure then go to github where u have pasted the url of github repu , under that there is crerdential section , click on add
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691941824204/902d10af-5231-4d2f-bea9-b0daf714fbaf.png align="center")
    
* Now add the credentials , under kind select SSH username with privatekey , give username as ubuntu (instance name) and under private key paste the private key(id\_rsa) and add.
    
* You can use cat command to see the private key
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691942161433/2fd8b9de-07e1-4bc1-a1da-882357e36d7f.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691941916960/47fc3d86-0d0d-41ab-a8e3-95102f9f2368.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691941926514/7ba337e1-0ffe-47c0-b57d-f4f99a74c356.png align="center")
    
* Now , go back and under credentials you can see the username that you have created recently add it .
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691942029389/bc8e9e9e-c7fc-4eae-8e5d-4aa9a34a3299.png align="center")
    
* After this step , you have to install Github Integration plugin to make this integration happen. Go to Manage jenkins &gt; plugins &gt; Availaable Plugin &gt; search Github integration and install it , jenkins might restart after that.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691942116603/1d610dfd-2a49-4cf9-8e9a-282ef31723b5.png align="center")
    

**NOW WE CAN PROCEED WITH THE PROJECT :**

* After adding github url and credentials and setting up the github intergration, go to build steps &gt; execute shell and paste this. and save it just like we did in previous blog.
    
    ```bash
    echo "Code Cloned"
    docker build . -t node-app
    echo "Code built..!!"
    # make sure you install docker compose before itself
    docker-compose down
    docker-compose up -d
    echo "Container is up"
    ```
    
* Now click on build now for the exection
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691942408033/e9fb483d-3fa2-49d6-80fe-e8c3f6adc288.png align="center")
    
* As you can see the build is successfull !! and the project is running
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691942460309/ef4bdc28-1e6f-4496-bd66-99a10a2be3cc.png align="center")
    

## 🪝Webhook

* Lets move to the interesting part
    

### What is webhook⁉️

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691942901989/cae714eb-925a-4589-b5ad-bdc1720009e8.png align="center")

* When certain events occur in a GitHub repository, a webhook is used to automatically trigger actions in external systems or services. To streamline workflows and automate various tasks, webhooks are commonly used to integrate GitHub repositories with other tools, services, or systems. When a specific event occurs in a repository, such as a new commit, a pull request, or the opening of an issue, GitHub will send an HTTP POST payload to a user-specified URL. This payload contains information about the event, allowing the external system to respond appropriately.
    

### How to setup ⁉️

* **Creating the Webhook:**
    
    * Go to your GitHub repository.
        
    * Click on the "Settings" tab.
        
    * Select "Webhooks" from the left sidebar.
        
    * Click the "Add webhook" button.
        
* **Configuring the Webhook:**
    
    * Enter the Payload URL: This is the URL of the endpoint in your communication tool that will receive the webhook payload.
        
        **(EC2 instance public ip/github-webhook)**
        
    * Choose the Content type for the payload. JSON is a common choice.
        
    * Select the events that should trigger the webhook. In this case, you'd choose the "Issues" event, specifically the "Opened" event.
        
        **(select "just the push event , includes push , commit)**
        
    * Optionally, you can configure other settings such as secret tokens for security.
        
        **(click on add webhook and wait till you get the green tick mark)**
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691942957657/108c3e47-9100-4e27-947d-6e568fec4335.png align="center")
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691943012467/f7c23e90-ac1b-44b4-9335-c76d6f685f28.png align="center")
        
* Now if you commit anything in your repo , jenkins will start building automatically !! (build #2 , this started automatically when i committed something new)
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691943139118/ea782f2e-a538-4321-bfd4-da5ec3deb8e5.png align="center")
    

> I hope you understood about webhooks and how to configure them and github integration as well  
> Make sure you go through the previous blog to understand how to setup the project
> 
> Happy Learning :D