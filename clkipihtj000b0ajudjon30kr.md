---
title: "Deep Dive Into Git And GitHub II"
datePublished: Tue Jul 25 2023 19:45:37 GMT+0000 (Coordinated Universal Time)
cuid: clkipihtj000b0ajudjon30kr
slug: deep-dive-into-git-and-github-ii
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1690309549348/d5251be4-4d0e-4875-8681-5d7102c2a7b0.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1690314327404/ca82caa1-cbeb-48b4-88e6-09afef97d2ed.png
tags: linux, github, git, devops, 90daysofdevops

---

## **🔸Git Stash: Saving Work in Progress🤔**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690310135989/ec071ed5-3fb3-411a-bd76-2aec5dc1d2d8.jpeg align="center")

* Consider that you are creating a painting or a story. Midway through, someone asks for your assistance with something else. You must complete your work if you don't want to lose your progress. Git stash functions as a kind of enchanted bookmark that saves your work momentarily so you can return to it later.
    
* You must first create a new branch and make some changes to it before you can use Git stash. After that, you can save those changes using the git stash command. By doing this, the changes will be recorded in a new stash instead of remaining in your working directory. These adjustments can be made later. The list of stored changes is displayed by the git stash list command.
    
* Additionally, you can delete a stash using git stash drop and all the stashes at once using git stash clear.
    

## **🔸Git Cherry-Pick: Choosing Specific Changes ❗**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690310479799/ceaa3e26-9622-404d-ad3e-154d9c56e668.png align="center")

* Using the Git cherry-pick command, you can pick out particular commits from one branch and apply them to another. When you want to selectively apply changes made in one branch to another, this can be helpful.
    
* You must first create two new branches and commit some changes to them before you can use git cherry-pick. The specific commits from one branch are then chosen and applied to the other branch using the git cherry-pick command with the specified commit\_hash.
    

## 🔸Resolving Conflicts:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690310834978/80947f10-8e48-419d-a9f4-7bec1a934a32.png align="center")

* When merging or rebasing branches that have diverged, conflicts can arise, and you must manually resolve the conflicts before git can continue with the merge/rebase. The git status command displays the files that have conflicts, the git diff command compares the versions that are at odds, and the git add command is used to add the files that have been resolved.
    

## 🔸Understanding through Hand-On :

* Task 1:
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690313665175/14dc52e4-b124-451f-bb7d-70612cf38755.png align="center")
    

* To create a new branch we use "git checkout -b branch name" and make changes by creating and modifying files.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690311074232/ee7ccaca-a4a4-4dee-822c-33b1cbf02d01.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690311126730/87c1f18a-8ac8-4e8d-82bd-49ab5106b441.png align="center")
    
* Create another branch , make changes ad commit them and bring the changes back from stash using git stash pop and apply them on top of new commits
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690311172916/49496bf7-71e4-4e60-a3dc-b4cfef6df634.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690311389110/b8f83b1b-d0df-4d3e-aca4-59de64dcc7fd.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690311423339/c8d77802-1f1e-4c35-8b1c-185671716586.png align="center")
    
* Task 2:
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690311706646/decfd1ff-eec2-42d4-b7d5-91ed48264fa2.png align="center")
    
* Now , change the branch to dev to make the commits as given in the task
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690311826869/dd84d82f-bc53-403f-9847-0ba1a3d1dfdf.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690311876121/391a4e81-a56d-49ce-ab88-3ca457a9325c.png align="center")
    
* Check the commits made using "git log"
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690312006741/fb09ad16-366d-4edd-a516-d7abac3f7cc1.png align="center")
    
* All these commits messages should be reflected in the Production branch too which will come out from the Master branch (Hint: try rebase)
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690313336080/c11e9198-7083-461d-a298-6c94d2222347.png align="center")
    
* Task 3:
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690313750605/480c2145-204d-4af3-bf4f-4bb046dfb6ea.png align="center")
    
* Change your branch to the production branch (if you are not in production),pick commit using git cherry-pick &lt;commit-hash&gt; of the commit you want to pick, and then add the lines as given in the task.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690313897326/df708df6-39b1-4c7f-be32-b27737898d85.png align="center")
    
* Resolving the error :
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690313996226/93a6abab-6256-4023-969d-45528fff4e1f.png align="center")
    
* Commit - Optimized Feature
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690314055054/91744fb3-2510-4807-a412-032774ca6d6b.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690314076878/df80d4b7-4bc0-4204-bda9-0350e71c6343.png align="center")
    

> I hope now you know about git stash , how to use it , git cherry-pick
> 
> Stay tuned for more updates
> 
> Happy Learning :D