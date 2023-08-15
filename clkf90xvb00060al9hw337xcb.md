---
title: "File Permissions And Access Control Lists In 
                                                     Linux"
datePublished: Sun Jul 23 2023 09:40:45 GMT+0000 (Coordinated Universal Time)
cuid: clkf90xvb00060al9hw337xcb
slug: file-permissions-and-access-control-lists-in-linux
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1690097442508/8f322f65-6c95-491e-abe9-f87269428bae.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1690105474730/4ef7be05-7b51-46e2-8a5a-6be45c88a285.png
tags: linux, devops, linux-for-beginners, 90daysofdevops

---

## 📝 What are file permissions ⁉️

* Consider file permissions to be doors with different locks. Each lock permits different activities to be done with the files.
    
* File permissions are rules that determine who can access a file and what actions they can perform on it.
    

## 🌀 Types Of File Permissions⁉️

* There are 3 types of permissions :
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690098275925/c7ea62cc-0ebe-4fa6-b5f5-261b5a405342.png align="center")
    
    * **Read Permission:** It's like giving someone a book to read. They can see what's inside, but they can't make any changes.
        
        * Denoted / Represented by "**r**"
            
    * **Write Permission:** Imagine a notebook where someone can write new things or edit existing ones.
        
        * Denoted / Represented by "**w**"
            
    * **Execute Permission:** This is like giving someone a magic wand that brings a story to life. They can run programs or scripts.
        
        * Denoted / Represented by "**x**"
            
    * For example, You keep a private diary (a file). You have the key (read permission) to open it and see your thoughts, but others cannot access it unless you grant them access.
        

## 🎚️ Permission Levels🤔❗

* Think of your friends and family. Each group can do different things with your stuff.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690099001371/e234e844-1dc9-4eea-b4e0-6198294ea054.webp align="center")
    
    * Owner: You! You have full control over the file and its permissions.
        
        * "chown" is used to change owner permission of a file or directory.
            
    * Group: Your close friends who you trust with certain things.
        
        * "chgrp" is used to change the group permission of a file or directory.
            
    * Others: Everyone else who's not in the first two groups.
        
* Example: You're the owner of a puzzle, and you can decide which pieces to share with your friends (the group). Others can't play with it unless you give them a piece.
    

## 🔄How to change file permissions⁉️

* We use "chmod" (change file mode) , which is used to change the access permission of the file .
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690101953410/0b02a61a-b0a7-4446-b715-3b2584f9b851.png align="center")
    
* Type the command " ls -ltr " to list out the files with the permissions they have:
    
    * l - long listing format
        
    * r - reverse order while sorting
        
    * t - sort by time
        
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690101974414/2c441283-5b40-40e9-b365-79343c3052f5.jpeg align="center")
    

Let's understand how to change permissions :

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690102103638/dd20f983-8618-4917-8785-13ae8f0a57da.jpeg align="center")

```bash
chmod 765 filename.sh
# given rwx permission to the owner.(read , write , execute)
# rw permission to the group.( read , write)
# rx permission to the other.( read and execute)
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690102561579/41e37d90-1aef-416a-83cf-7e9eca909886.png align="center")

Permission changed from:

* ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690102599406/ddb528dd-e00a-4b1d-9e01-35de54441c43.png align="center")
    
* It had only rwx for user , r-x for group and w-x for others
    
* Changed to :
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690102659527/295b267c-d9ef-4450-af57-a576d91ad784.png align="center")
    
* Now it has permission rwx for user, r-x for group and r-x for others
    

## 🦾What is Access Control List

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690103204241/457dab7d-658b-4a0e-9e41-f4a05ad88034.jpeg align="center")

* ACLs are similar to having a supercharged lock on your files and folders. It goes beyond simple permissions and allows you to choose who can and cannot do what with your belongings. It's ideal for granting varying levels of access to different persons.
    

Consider that you have a treasure trove (a file) that you wish to share with your buddies. Some can just see inside (read), while others can add to it (write), and only a few can bring it to life (execute). That's where ACL excels: you can specify who gets which key to your treasure trove.

## 🔧How to use ACL

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690103330254/8b9d15f7-a1a4-41e0-b479-8f3dcee1e966.png align="center")

* Consider the person's name (username) and what they can do (read, write, execute) before granting access to a file or folder.
    
* To set the permission entry, use the "setfacl" command:
    
    ```bash
    # To add permission for user
    setfacl -m u:username:permissions path
    # Below is the example
    setfacl -m u:srahul:rwx /scripts/if_else.sh
    # to remove permissions
    setfacl -x u:username path
    ```
    
* To see who can access your file, just ask the lock by using the "getfacl" command:
    
    ```bash
    getfacl filename
    # or 
    getfacl path
    ```
    

> I hope now you all know how to change the file permissions and access control lists.
> 
> Happy Learning :D