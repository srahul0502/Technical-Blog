---
title: "Advance Git & GitHub"
datePublished: Mon Jul 24 2023 19:27:50 GMT+0000 (Coordinated Universal Time)
cuid: clkh9fsbx000209l56f668pmd
slug: advance-git-github
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1690213294010/be5fd9c2-48e3-4121-b1e9-99007a7c45e5.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1690226862010/880a6df2-c390-4e31-bebf-5e1f2b0af479.png
tags: linux, github, git, devops, 90daysofdevops

---

## What is Git and Why It's Important⁉️

* Git is a version control system that allows you to track file changes and collaborate on files with numerous people. It is most typically used in software development, but it may be used to track changes to any collection of files.
    

Let's understand why It is important:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690221008552/56a983c0-c7d9-4d55-80b3-52269509aa14.jpeg align="center")

* **Better Teamwork:** With Git, each team member has their own copy of the project and may work on it independently. It's like having your own personal playground to experiment with ideas without affecting others. When you're ready to demonstrate your work to the team, you may effortlessly share your edits with them.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690221151468/ac2a67ea-ca0a-4c1e-92ee-d6bd5196bfea.jpeg align="center")
    
* **Avoiding Mistakes:** Think of Git as a time machine for your project. If you make a mistake, you may quickly go back in time to when everything was working correctly. No more worrying about making mistakes!
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690221263613/fbb6c6ab-7a0f-4f46-84bf-fea13f4ebf85.webp align="center")
    
* **Keeping Things Organised:** Git is similar to a virtual notebook in that it preserves a complete history of all modifications made to the project. It's like having a magical book that tells you who did what, when they did it, and why. It assists you in comprehending the project's journey and maintains everything organised.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690221374510/94ecfeef-a133-4a69-a15b-8eb639529933.webp align="center")
    
* **Working Anywhere:** With Git, you can work on your project even when you're not connected to the internet. You can keep making changes and saving them in your own space, and when you're back online, you can share your work with others.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690221610917/cb9feee3-e672-4ac7-b070-5948ce5cd5f5.png align="center")
    
* **Combining Everyone's Work:** Git acts as a superpower that enables your team to easily combine everyone's edits. It's similar to blending various components to make a great cake while making sure every component blends seamlessly.
    

## What is the difference between main branch and master branch⁉️

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690222185916/519e7ae1-76a1-4eac-9529-a3125ceefdd3.png align="center")

* Assume you're constructing a lovely garden with your friends, and you're using a magical blueprint to guide your efforts. This blueprint functions as a version control system, allowing you to keep track of all changes and progress.
    
    You will be working on two main sections in this garden project: the flower garden and the vegetable garden. You want to keep things organised, so you divide your blueprint into two sections: one for the flower garden and one for the vegetable garden.
    
* Main branch:
    
    * The main branch is similar to a central section of your blueprint, but it focuses on a specific aspect of the project. In our case, it is solely for the flower garden. It includes all of the information and updates about the flowers, their colours, and how they will be arranged.
        
    * In our garden project, for example, the main branch represents the plan for the flower garden. It includes information about the different types of flowers, where they are placed, and any changes or improvements made to that section.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690222613469/4d78291d-5f8f-435d-99e3-9e829c7eabfc.jpeg align="center")
        
* Master branch :
    
    * The master branch is similar to the main section of your blueprint, where you put all of the important and final project information. It functions as a central hub, containing the most recent and polished version of your garden plan.
        
    * In our garden project, for example, the master branch represents the overall plan for the entire garden. It contains important details such as the layout, design, and main elements of both the flower and vegetable gardens.
        
* Summary :
    
    * The master branch holds the entire project's final version, including both the flower and vegetable garden plans.
        
    * The main branch is like a subset of the master branch, focusing only on the flower garden part of the project.
        
    * The main branch and the master branch function as distinct sections of your magical blueprint. The master branch contains the overall project plan, whereas the main branch focuses on a specific component of the project. You can easily keep your garden project organised and create a beautiful masterpiece by using both branches!
        
    * When everything is in order, merge the main branch back into the master branch so that the final plan includes both the flower and vegetable gardens.
        

## What is the difference between Git and GitHub🤔⁉️

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690223002057/1d9a8be0-3f0b-4b63-b178-4356998831a7.jpeg align="center")

* Git is a tool that allows developers to keep track of their code changes, whereas GitHub is an online platform that allows them to store and share their code notebooks with others. They make coding a fun and collaborative adventure when they work together!
    

## What is the difference between local Repository and Remote Repository⁉️

Let's understand the difference local and remote repository:

* Local Repository :
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690223287007/cf378bac-c6cb-42a7-a2f9-edca288de62c.png align="center")
    
    * A local repository is similar to your own private stash of files and folders on your computer. It houses all of your important work and changes. Consider it a magical treasure chest in which you can save and organise everything related to your project.
        
    * Assume you're working on a story and have a special notebook on your desk. You save anything new you write or changes you make to the story in this notebook. That notebook is your local repository, where you keep all of your creative work safe and secure.
        
* Remote Repository:
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690223323855/98fbb73e-af9f-4c17-9a8e-394d61730398.png align="center")
    
    * A remote repository is similar to fantastic cloud storage where you can collaborate with friends and share your work. It works like a special library where your team members can collaborate on the same project while also seeing what you've accomplished.
        
    * Consider a sizable library where many people can add and borrow books. Your remote repository resembles one of those library books. You place a copy of your notebook in the library (the remote repository) when you're ready to share your story with others or solicit their assistance. Your story is now available for all of your friends to see, comment on, and even adopt.
        
* Summary :
    
    Your local repository is your private workspace where you do all your work, while the remote repository is like a shared library where you can showcase your work, collaborate with others, and make magic together
    

## How to connect local repository to Remote repository⁉️

* From Remote : This happens with the help of the Git Fork command when the repository is already available on GitHub. User makes a git fork or git clone to the same repository at local.
    
* ***From local :*** *This happens with the help of the Git Remote command when the repository is first created on local. And then the user connects it to the remote repository*
    
* We can use " git remote " command to connect a Git local repository with GitHub remote repository :
    
    ```bash
    # to connect to the remote repository
    git remote add origin "url of repository on github"
    git remote add origin https://github.com/srahul0502/practice.git
    
    # push the repository from local repo to remote repo
    git push -u origin master
    ```
    
    * Even if you clone the repository from github and use git clone in your system
        
        you will get connected to the remote repository
        
        ```bash
        git clone https://github.com/srahul0502/practice.git
        # it gets connected to the remote repo as we have cloned from there
        # we just have config username and email to push the changes to origin
        # to check if your are connected to any remote repository or not
        git remote -v 
        ```
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690224289189/ec48ed9e-cda4-42f9-aa6c-f311ed499b7a.png align="center")
        

## How to set your user name and email address in the config file ⁉️

To set your username and email address associated with your github account we use :

```bash
  git config --global user.email "you@example.com"
  git config --global user.name "Your Name"
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690224498220/7903c2d4-7549-4f02-9f8f-9d0bd0c0121a.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690224561738/c4563060-20b4-4e38-9d94-448f77444650.png align="center")

* After doing these you can easily commit the changes and push them to the remote repository
    

## Password Authentication 🤔⁉️

* You might get error while pushing the changes to the remote repository , it will as you for username and password associated with github .
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690224713981/a7a8d8dc-84d5-4b31-9f75-51c5a59a3d12.png align="center")
    
* I know it is difficult to enter your credentials for each push you make and even If you get error after getting credentials you can follow the steps below to solve or make it easy :
    
    * Go to GitHub settings &gt; Developer settings(scroll down you will find it in left bottom) &gt; Personal access tokens &gt; Tokens Classic
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690224959361/5ecc74be-0f94-4be3-abd5-1f0acd5a8f09.png align="center")
        
        * Click on Generate new token and then go to Generate new token (classic).
            
            ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690225041110/67d27d71-26be-4e3b-8393-2142aff88110.png align="center")
            
        * Give the name you want to and select the number of days you want the token to be active and click on Repo check box , scroll down and generate token.
            
            ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690225157826/02d961af-257b-4d9c-84fb-d5d4c215c6b5.png align="center")
            
        * Copy the token and go to cmd
            
            ```bash
            git remote set-url origin https://token-key@github url
            # example 
            git remote set-url origin https://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@github.com/srahul0502/practice.git
            ```
            
        * Now , you can easily push the changes to the remote repo without giving any credentials for the days you have created the token.
            
            ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690225371802/dd0650bd-598d-487b-9a67-f1d63b92a8a4.png align="center")
            

## Hands-on😁

* Create a repository named "Devops" on GitHub
    
* Connect your local repository to the repository on GitHub.
    
* Create a new file in Devops/Git/Day-02.txt & add some content to it
    
* Push your local commits to the repository on GitHub
    

Let's create a repository as we did in our previous blog , [https://srdev.hashnode.dev/basics-of-git-github](https://srdev.hashnode.dev/basics-of-git-github) (if you didn't go through, please go through it once)

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690226174773/c03d266d-6d84-4fe0-9932-8d974ed67ff4.png align="center")

* After naming the repo click on check box to add README file and create repo
    

Now , Clone this repo to your local system using git clone :

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690226310355/b31caec3-62c0-4901-a8d8-a76caea4e5aa.png align="center")

```bash
git clone https://github.com/srahul0502/Devops.git
# go to the repo by using cd
cd Devops
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690226380218/22ed6da0-383f-4b1d-bd3c-d3ec9ec825f3.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690226399905/2c5b39df-ed2e-487f-ac09-0ca1a78fab76.png align="center")

Now , create folder "Git" using mkdir and use nano filename to create and edit the file

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690226447081/fdc0f1a2-43ec-4a5f-9812-a52600e2e285.png align="center")

After creating and modifying the content of the file , go back to the Devops folder using " cd.. " to add all the contents present in Devops to Staging area using " git add " , git add . (adds all the content presend to staging area) and use git status to check status.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690226552799/91c9cec3-58ee-48d4-86e0-8c26acdf6af8.png align="center")

Now commit your changes with a commit message :

```bash
git commit -m "Folder and file added "
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690226663751/ada2365b-e45f-44de-a68f-f927b005c518.png align="center")

Now push them to the remote repository using "git push"

```bash
git push origin main
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690226724217/101fd4ca-7919-4d8a-956f-a495c482b7e0.png align="center")

Now got Github and refresh your page and tadaa🥳

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690226751141/66994746-ef91-46b7-aea5-bf1f1d9081eb.png align="center")

> I hope you all understood the concept
> 
> Stay tuned for more updates
> 
> Happy Learning :D