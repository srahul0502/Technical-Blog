---
title: "Basics Of  Git & GitHub"
datePublished: Mon Jul 24 2023 09:03:53 GMT+0000 (Coordinated Universal Time)
cuid: clkgn5dar000e0am79yt1afth
slug: basics-of-git-github
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1690180476572/77fbb5ea-c633-453f-bb2e-0bbccaf07e78.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1690189424051/7b32d2ac-bad5-47a3-8fd0-c253c3060f41.jpeg
tags: linux, github, git, devops, 90daysofdevops

---

Hey everyone, hope you all are doing good let's get started with the basics of Git and Git Hub...

## What is Git 🤔⁉️

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690181386031/806c6fc4-457a-4e5f-b9c6-1e83c0e32973.png align="center")

* Git is a version control system that allows you to track file changes and collaborate on files with numerous people. It is most typically used in software development, but it may be used to track changes to any collection of files.
    
* Git is a superhero among developers! It's a useful tool for keeping track of modifications to their projects. Consider it a digital notebook that records every modification you make to your code.
    

## What is Github 🤔⁉️

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690181601079/35c62931-1844-4ea6-9241-85e3e1ac0af5.png align="center")

* GitHub is a web-based platform that hosts Git-based version management. It is a Microsoft subsidiary that provides all of Git's distributed version control and source code management (SCM) functionalities as well as its own. GitHub is a popular site for developers to share and collaborate on projects, and it is also used to host open-source projects.
    
* GitHub is a giant playground where developers can share their projects with the rest of the world. It's a website that stores Git repositories and allows developers to collaborate and show off their cool inventions/creations.
    

What is version control ⁉️

* Assume you're working on a group project and you routinely save several versions of your document to keep track of changes and prevent losing progress. Version control systems are similar to the magic that powers this process, but they are used for software and other digital undertakings.
    
* Version control is a system that keeps track of changes to a file or set of files over time so that you may go back in time and retrieve specific versions. It lets you revert files to a previous state, return the entire project to a previous state, compare changes over time, check who last edited something that might be causing a problem, who originated an issue and when, and much more.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690182332218/24d5cec5-9d2e-48e4-8742-ead2db781288.png align="center")
    

Types of Version Control Systems 🤔

* There are two main types of version control systems: centralized version control systems and distributed version control systems.
    
* Centralized Version Control System (CVCS) :
    
    * A centralised version control system stores all of the project's files and history on a central server. Team members use this central repository directly, checking out files to make changes and then checking them back in. CVCS examples include CVS and Subversion.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690183416244/50ff08c1-d090-4613-83e8-e93230b7ebf5.png align="center")
        
* Distributed Version Control System (DVCS) :
    
    * Version control is taken to the next level with distributed version control systems. Each member of the team has a local copy of the entire project, including its history. This implies they can work alone, even while not connected to the internet. Git and Mercurial are two prominent DVCSs.
        
    * In simple words , it allows developers to "clone" an entire repository, including the entire version history of the project. This means that they have a complete local copy of the repository, including all branches and past versions. Developers can work independently and then later merge their changes back into the main repository.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690183927675/7505b973-3043-43bf-833c-eafedfeb4832.png align="center")
        

## Why do we use Distributed Version Control over Centralized Version Control ⁉️

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690184310223/59a95c5f-c334-432c-a964-b5174119e731.png align="center")

* **Better collaboration:** Every developer in a DVCS has a complete copy of the repository, including the whole history of all changes. This makes it easier for developers to collaborate because they don't have to constantly contact with a central server to commit their modifications or check what changes others have made.
    
* **Improved speed:** Because developers have a local copy of the repository, they can commit changes and conduct other version control tasks more quickly because they aren't communicating with a central server.
    
* **Greater flexibility:** With a DVCS, developers can work offline and commit their changes when they reconnect to the internet. They can also choose to share their changes with a subset of the team rather than pushing them all to a central server.
    
* **Enhanced security:** The repository history in a DVCS is saved on numerous servers and machines, making it more resistant to data loss. It can be difficult to recover lost data if the central server in a CVCS fails or the repository becomes damaged.
    

## Installing Git 🖥️

* You can install git on your system by downloading it from the official website [https://git-scm.com/downloads](https://git-scm.com/downloads)
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690185019870/3ad2a346-cc86-4be2-ae9e-ccabbf64421c.png align="center")
    
* Then Click on the system on which you want to install it and follow the steps as instructed.
    
* Create a free account on GitHub by signing up at [https://github.com/](https://github.com/)
    

## Understanding how Git works using Commands 😯

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690185759507/3ae6f2bc-ac23-4e6b-bf82-3b416ce9d5e4.png align="center")

Let's understand how git and github works by creating repository and cloning it to your local machine / system :

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690186741820/0c449884-fd3f-48ab-b087-42fba52945dd.png align="center")

* After signing up, click on + symbol and click on New repository as shown in above image.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690187041165/5632461b-babe-4352-baf3-a4a722a4f7c8.png align="center")
    
* Give the repository name as you line and click on the Add a README file checkbox and then click on create repository
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690187162465/9b936122-c998-4b10-b856-dcff814583d6.png align="center")
    
* Tadaa🥳 you have created your first repo.
    
* To clone the repo to your local machine , click on code and copy the link
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690187301266/6ff2603e-3994-4f58-97fe-9e0db48b9ee7.png align="center")
    
* Use the command git clone "url" in the terminal to clone the repo on your local machine .
    
    ```bash
    git clone https://github.com/srahul0502/practice.git
    # go to the repo in your local machine using cd to make changes
    cd practice
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690187606026/153acd73-548f-4d37-8e1f-8dabf45a154c.png align="center")
    
* Make the changes you want , suppose i add a text file "demo.txt" and add some text into it and then commit them to the repository using git
    
    * Create "demo.txt" using vim or nano , add some txt and save it.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690188038899/f227102f-34c8-4f8b-a987-aeed3648b155.png align="center")
        
        * Here it says that it is not in the staging area so ....
            
    * Before commiting it to the repo we add it to the staging area by using **git add filename .**
        
        ```bash
        # to add it the staging area
        git add demo.txt
        # to add all the content present in repo to staging area we can use
        git add .
        # to check the status that it is in the staging area or not we use
        git status
        ```
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690188225482/5901ee39-5c67-4baa-ab37-b5d434ad8f4d.png align="center")
        
        * We successfully added the "demo.txt" file on the staging area
            
        * Now you can commit the changes to the repo
            
    * To commit the changes we use **git commit -m "commit message"**
        
        ```bash
        # we use -m to add a commit message 
        git commit -m "text file added"
        ```
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690188705261/729414c3-6485-497f-af9e-89b52a5aef66.png align="center")
        
        * Here we have successfully commited the text file to the local repo with commit message.
            
    * Now , to push the changes to the GitHub repo we use the command git push origin main
        
        ```bash
        # to the push the changes to the main branch of the github repo
        git push origin main
        ```
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690189187217/b1e2372d-93c9-4c6f-bcb3-28d094a62abe.png align="center")
        
        * We have successfully pushed the changes to the Github repo
            
            ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690189283650/7d0e8598-10f8-4970-a5dd-155b0e354675.png align="center")
            

> I hope you understood how to create github account and how to make changes and push them to the github
> 
> Stay tuned for more updates
> 
> Happy Learning :D