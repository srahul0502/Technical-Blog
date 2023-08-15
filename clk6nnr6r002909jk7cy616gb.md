---
title: "Understanding Linux Terminal Shell 
                                                 & 
                         Basic Linux Commands"
datePublished: Mon Jul 17 2023 09:20:29 GMT+0000 (Coordinated Universal Time)
cuid: clk6nnr6r002909jk7cy616gb
slug: understanding-linux-terminal-shell-basic-linux-commands
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1689575742208/816b3a22-3b75-4e1e-a3ae-dad9dd1f7091.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1689585616395/cef36872-cace-4ef5-b35e-6d800a4f9e7a.jpeg
tags: linux, devops, linux-for-beginners, devops-journey, 90daysofdevops

---

## 🐧 What is a Terminal Shell? 🖥️

* A terminal shell is a program that understands and executes commands you type.
    
* The Linux terminal shell is a text-based interface that lets you communicate with the system using commands.
    
* It acts as a middleman between you and the operating system, making it easier to interact with the system using text.
    

## 🐧How does it work 🤯❓

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689578198059/62327cce-8fa2-4b11-830e-5254d7b988b7.jpeg align="center")

1. **Prompt**
    
    * 📜 When you open the terminal, you'll see a prompt (usually $ or #) waiting for your command.
        
    * $: Represents Normal User
        
    * #: Represnts Root User / Super User / Admin
        
    * 🐚 It means the shell is ready to accept your instructions.
        
2. **Commands**
    
    * 🖊️ You can type commands after the prompt to perform specific tasks.
        
    * 🐚 Commands can be simple (like listing files) or complex (like searching for text in files).
        
    * 🔢 Command parameters or options modify how the command behaves.
        
3. **Command Execution**
    
    * ▶️ After you press Enter, the shell interprets and executes the command.
        
    * 🐚 It looks for the command in specific places on the system using the PATH variable.
        
    * 🚀 When found, it loads the command into memory and runs it.
        
4. **Output** **and Error Messages**
    
    * 📤 The command may produce output or error messages, displayed in the terminal.
        
    * 🐚 Output can be text, data, or even graphical information, depending on the command.
        
    * ⚠️ Error messages tell you if something went wrong during command execution.
        
5. **Scripting and Automation**
    
    * 📜 Shell scripting lets you create scripts with multiple commands.
        
    * 🤖 These scripts automate repetitive tasks, saving time and effort.
        
    * 🐚 By running a script, you can avoid typing individual commands repeatedly.
        

## 🐧 Understanding Using Basic Commands❗

Let's understand it by solving some basic questions:

Part 1:

1. Check your present working directory
    
    *pwd : present/print working directory*
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689581828012/6904df46-f5d3-4a50-89fe-942bced1963b.png align="center")
    
2. List all the files or directories including hidden files
    
    *ls -a : list files or directories including hidden files or directories*
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689581856691/f682e004-65b9-4856-a74a-5e793c553c7e.png align="center")
    
3. Create a nested directory A/B/C/D/E
    
    *mkdir : used to make directory*
    
    *mkdir -p A/B/C/D/E : Creates nested directories*
    
    *\-p : parent*
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689585348199/282562e9-c0bb-4686-8290-5643e5749c2d.png align="center")
    

---

Let's level up with some more questions :

1. **To view what's written in a file**
    
    *cat : read the content of the file*
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689583464188/e6f87dbf-d0f0-4c42-9112-7bf21cfe5acf.png align="center")
    
2. **To change the access permissions of files.**
    
    *chmod : change the access mode of a file*
    
    * Every file in Linux has one of three permission types: read (r), write (w), or 
        
        execue (x).
        
    * Three types of users can have these rights set: the file's owner (u), the group to which the file belongs (g), and other users (o), who are neither the owner nor a member of the group.
        
    * We employ a combination of letters and symbols to alter the permissions. For instance: -
        
        * The file owner is given read, write, and execute permissions using the 
            
            command "chmod u+rwx example.txt".
            
        * Removing the group's and others' read permissions using 
            
            "chmod go-r example.txt"
            
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689583591614/eea19656-7f73-4bc6-bc09-2784baf757ee.png align="center")
    
3. **To check which commands you have run till now.**
    
    *history : used to view the previously executed command*
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689583690252/8a51f2f5-4e00-440e-9e2f-f8b6eb4b474b.png align="center")
    
4. **To remove a directory/ Folder.**
    
    *rmdir : used to remove/delete directory*
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689583780446/d8bab4ec-5aa9-42d9-85fe-c49bf5fa7ef5.png align="center")
    
5. **To create a fruits.txt file and to view the content.**
    
    vim filename : creates a file and views the content for read/modify.
    
    nano can also be used , it works the same.They directly open editors to view and edit the content
    
    * we can also use "touch" to create empty files
        
    * To read the content of the file we use "cat"
        
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689583977008/bc0a20f6-b86a-482f-a028-cda4438d31a1.png align="center")
    
6. **Add content in devops.txt (One in each line) - Apple, Mango, Banana, Cherry, Kiwi, Orange, Guava.**
    
    *use nano/vim and edit the content*
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689584143088/49cb74a8-e5dd-4b69-9111-43284cea480a.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689584155831/c05afda2-e016-4d81-afb1-82377a9e6782.png align="center")
    
7. **To Show only top three fruits from the file.**
    
    *head : print the top N number of data of the given input*
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689584459693/b8442c1d-bff5-4574-be1d-c62ed28639a2.png align="center")
    
8. **To Show only bottom three fruits from the file.**
    
    *tail : prints the last few number of lines of a certain file*
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689584550924/5552a3ea-99eb-4acb-922a-d291609f6fc0.png align="center")
    
9. **To create another file Colors.txt and to view the content.**
    
    *use nano or vim to create and view the content*
    
    * we can also use "touch" to create empty files
        
    * To read the content of the file we use "cat"
        
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689584843987/393153cd-46be-4fb0-b3e8-40037734ad6a.png align="center")
    
10. **Add content in Colors.txt (One in each line) - Red, Pink, White, Black, Blue, Orange, Purple, Grey.**
    
    *use nano or vim to edit the content*
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689584899492/595d065b-df77-4c97-9698-3549deb27021.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689584881883/cce19236-0399-4164-bd24-66cca24eaea5.png align="center")
    
11. **To find the difference between fruits.txt and Colors.txt file.**
    
    *diff : compares two files and produces a list of the differences between the two.*
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689585116164/610c52a8-f657-479a-9102-25b07f607500.png align="center")
    

> Other commands will be explored in Advance Linux . Stay tuned :D
> 
> Happy Learning :D