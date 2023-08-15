---
title: "Advanced Linux Shell Scripting With Crontab"
datePublished: Thu Jul 20 2023 17:26:57 GMT+0000 (Coordinated Universal Time)
cuid: clkbfcwy0000n0amdbphldty8
slug: advanced-linux-shell-scripting-with-crontab
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1689860296657/69511dfa-c814-4358-876e-43bd86fb00e2.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1689877512531/97ec920a-7b3c-417f-a23b-e4913340a7fe.jpeg
tags: linux, terminal, bash, 90daysofdevops, tws

---

## 👤 User Input and Arguments⁉️

* Let's start with something which I couldn't cover in my last blog :D
    
* Let's understand how we can take input from the users :
    

**read:**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689861509278/de3f866f-f7e7-411e-9e9d-ab9713126fb9.png align="center")

* The "read" command is like a friendly way for a computer program to ask you for information. It can ask you questions and wait patiently for your answers.
    
* Once you tell it something, it stores your response so it can use it later in the program. It's like having a conversation with the computer, and it helps the program do what it's supposed to do based on your input.
    
* Example:
    
    ```bash
    #!/bin/bash
    
    echo "Heyy , What's your name ?"
    read name
    # waits until the inout is provided by user and 
    # stores it in variable called "name".
    echo "Hello $name , Welcome to my blog"
    ```
    
    * Save this in a .sh file and change the permission using chmod to make it executable and then execute it using **./filename.sh** .
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689862047319/96e53d19-73e7-40f7-842d-f0f933885b07.png align="center")
        

## ➿Understanding Loops

* **if else:**
    
    * "if-else" holds a special place as it empowers developers to make decisions and create dynamic, interactive scripts.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689862703020/e098b6d7-a9e7-4c1c-a9ea-469206514c25.png align="center")
        
    * In this blog post, we will dive deep into the world of "if-else" in shell scripting, explaining its syntax, usage, and providing practical examples to help beginners understand and harness its potential
        
    * **Example :** Let's understand this by writing a script to find the greatest number .
        
        ```bash
        #!/bin/bash
        
        a=1000
        b=500
        c=250
        
        if [[ $a -gt $b && $a -gt $c ]] #gt- greater than
        then
        # if the above condition is satisfied then print
        echo "A is greater"
        elif [[ $b -gt $a && $b -gt $c ]]
        # if it doesn't satisfy then check for this condition
        then
        #if it satisfies this condition then print
        echo "B is greater"
        else
        # if none of the above condition is satisfied then print 
        echo "C is greater"
        fi
        ```
        
        * let's understand the syntax :
            
            * we have initialized the values of a , b and c
                
            * then comes the if\[condition\] which says if a is greater than b && a is greater than c then echo "a is greater".
                
                * && moves to next only when both the statements are true
                    
                    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689863558012/c496c569-cf45-4bfa-941c-ed863c1c6473.png align="center")
                    
                * elif : similar to else if\[condition\] , if the previous condition is not satisfied then check for this condition
                    
                * fi : this is used to close the elseif loop
                    
            
            ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689863790334/3ae915a8-8dd8-4d90-9ec6-ed0016b610fe.png align="center")
            
* **for loop :**
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689866169601/48035c48-eaf8-4aa4-b7ac-60de11049bad.png align="center")
    
    * In shell scripting, the "for" loop allows you to repeat a series of commands for each item in a list. It's like having a helper that goes through the list and helps you perform tasks on each item without repeating yourself.
        
        ```bash
        # SYNTAX
        for (condition)
        do
           statement
        done
        ```
        
        Let's understand with an example of printing numbers 0-10
        
        ```bash
        #!/bin/bash
        
        for ((i=0; i<10; i++))
        do
        echo "$i"
        done
        ```
        
        * **i=0:** We start by setting the variable i to 0, which means we begin counting from zero.
            
        * **i&lt;10:** As long as i is less than 10, the loop will continue. So, we will count from 0 to 9, but when i becomes 10, the loop will stop.
            
        * **i++:** After each iteration (count), we increase the value of i by 1. So, it goes from 0 to 1, then 1 to 2, and so on until it reaches 9.
            
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689866472361/77403642-fecd-42e0-87bc-89159c43aeee.png align="center")
        
* While loop :
    
    * With the while loop, you can repeatedly run a sequence of instructions up until a certain condition is met. It is typically employed when modifying a variable's value repeatedly.
        
        ```bash
        #SYNTAX
        while [ condition ];
        do
            # statements
            # commands
        done
        ```
        
    * Let's take an example:
        
        ```bash
        #!/bin/bash
        a=7
        while [ $a -gt 4 ];
        do
            echo $a
            ((a--))
        done
        
        echo "Out of the loop"
        ```
        
        * the loop is iterated till the condition is false. As soon as the variable a becomes 4, the condition is evaluated to false and the loop skips the command block and starts executing the commands after the block.
            
            ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689867131242/41a3cab7-5756-4bdb-ae5c-4098a018f650.png align="center")
            

---

## 📜Creating Directories Dynamically

Let's practice by writing some scripts for the following problems:

* Write a bash script that when the script is executed with three given arguments (one is directory name and second is start number of directories and third is the end number of directories ) it creates specified number of directories with a dynamic directory name.
    
    ```bash
    #!/bin/bash
    
    if [ $# != 3 ]
    then
            echo "Can't proceed \n Please give three arguments to continue"
            exit 1
    
    fi
    
    echo "Creating directory as per your requirement"
    start_day=$2
    end_day=$3
    
    for (( i=start_day; i<=end_day; i++ ))
    do
            mkdir $1$i
    done
    
    echo "Here are your directories:"
    ls
    ```
    
* Paste the above code in .sh file and give required permissions(chmod 777 filename.sh) . And run it using ./filename.sh.
    
* Let's understand the script:
    
    * **"if \[ $# -ne 3 \]; then ":** This line checks the number of arguments passed to the script. The special variable $# holds the count of command-line arguments. The script expects exactly three arguments: &lt;directory\_prefix&gt;, &lt;start\_number&gt;, and &lt;end\_number&gt;. If the number of arguments is not equal to 3, the script prints a usage message and exits with a non-zero status (indicating an error).
        
    * Then we pass arguments to the start\_day and end\_day and run a for loop iterating the same.
        
        * $1: filename, $2: start\_day , $3: end\_day
            
        * argument $2 and $3 are under $i
            
        * mkdir $1$i : creates directory taking filename argument , start\_day , end\_day.
            
        * We pass these arguments when we execute the script:
            
            * ./filename.sh day 1 90
                
            
            ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689868057294/0161db1e-4fef-4890-b3f7-c783cf45f330.png align="center")
            

---

## 📜 Create a Script to backup all your work

* ```bash
      #!/bin/bash
      
      src_dir=/home/srahul/scripts
      tgt_dir=/home/srahul/backup
      
      curr_timestamp=$(date "+%Y-%m-%d-%H-%M-%S")
      
      echo "Taking backup on $curr_timestamp"
      backup_file=$tgt_dir/$curr_timestamp.tgz
      #echo "$backup_file"
      
      tar czf $backup_file --absolute-names $src_dir
      
      echo "Backup Complete"
    ```
    
* **src\_dir=/home/srahul/scripts:** This line sets the source directory that needs to be backed up. Change /home/srahul/scripts to the actual path of the directory you want to backup.
    
* **tgt\_dir=/home/srahul/backup:** This line sets the target directory where the backup file will be stored. Change /home/srahul/backup to the desired destination path.
    
* **curr\_timestamp=$(date "+%Y-%m-%d-%H-%M-%S"):** This line generates the current timestamp in the format YYYY-MM-DD-HH-MM-SS using the date command and stores it in the variable curr\_timestamp.
    
* **echo "Taking backup on $curr\_timestamp":** This line prints a message indicating that the backup process is starting and displays the current timestamp.
    
* **backup\_file=$tgt\_dir/$curr\_timestamp.tgz:** This line sets the backup filename by concatenating the target directory ($tgt\_dir) with the current timestamp and a .tgz extension. The resulting filename will be something like /home/srahul/backup/2023-07-20-15-30-45.tgz
    
* **tar czf $backup\_file --absolute-names $src\_dir:** This line creates a compressed tar archive file (.tgz) of the source directory ($src\_dir) and saves it with the previously generated filename ($backup\_file).
    
* **echo "Backup Complete":** After the backup process is finished, this line prints a message indicating that the backup is complete.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689869039341/809c1ab0-8b6a-4688-9211-00f9942d0d17.png align="center")
    
* *Basically ,this script takes a backup of the specified source directory ($src\_dir) and saves it as a compressed .tgz archive in the target directory ($tgt\_dir). The archive file is named with the current timestamp, making it easy to distinguish backups created at different times. The script provides clear feedback on the backup process by printing messages before and after the backup operation.*
    

## 🔙Automating Backups (Cron and Crontab)

* **What is Cron?**
    
    Cron is a time-based job scheduler on Unix-like systems. It allows you to schedule and execute tasks, such as running scripts, at specified intervals, dates, or times.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689870084073/62468a8e-17cb-406f-910f-ca060e57e82a.png align="center")
    
* **What is Crontab?**
    
    Crontab is the configuration file used to define cron jobs. It holds the schedule and command(s) to be executed for each scheduled job.
    
    * checking for cronjob , as the image says there's no crontab for this user.
        
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689870720684/8f527139-be08-45d9-9273-aa1876a105c0.png align="center")
    

Let's create a cronjob:

* type "crontab -e" it will ask you to choose the editor , choose as per your comfort.
    
* Then you'll get the editor as below:
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689870896105/8e098011-2492-4a2e-a035-5751342b09ab.png align="center")
    
* We schedule the time to run the echo and save it in test\_cron.txt
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689870974646/dc768d59-6d82-497e-9ec9-3caa54972d42.png align="center")
    
* Create a cronjob to automate backup :
    
    * create filename.sh and copy the command as below
        
        ```bash
        #!/bin/bash
        
        src_dir=/home/srahul/scripts
        tgt_dir=/home/srahul/backup
        
        curr_timestamp=$(date "+%Y-%m-%d-%H-%M-%S")
        
        echo "Taking backup on $curr_timestamp"
        backup_file=$tgt_dir/$curr_timestamp.tgz
        #echo "$backup_file"
        
        tar czf $backup_file --absolute-names $src_dir
        
        echo "Backup Complete"
        ```
        
        * Type crontab -e and select your editor and do the scheduling part
            
            ```bash
            40 4 * * * /home/srahul/backup.sh
            ```
            
        * And wait for the cronjob to be done
            

## 📜Creating users and displaying usernames

* Firstly we have write shell script to create and display users.
    
    ```bash
    #!/bin/bash
    
    # Define an array with the names of the users to add
    users=("user1" "user2")
    
    # Loop through the users array to add each user
    for user in "${users[@]}"
    do
        sudo useradd "$user" -m -s /bin/bash
        echo "$user:userpassword" | sudo chpasswd
        echo "User: $user"
    done
    ```
    
    * **users=("user1" "user2") :** In this line, we define an array called users that contains the usernames of the users we want to add. In this example, we have three usernames: "user1," "user2".
        
    * Then there is a for loop that iterates through the users array. It uses the variable user as a placeholder to represent each username in the array.
        
    * The "$user" variable holds the current username being processed by the loop. The options -m and -s /bin/bash create a home directory for the user and set the default shell to /bin/bash.
        
    * Next, we set the passwords for each user. The echo command prints the string "$user:userpassword" and then pipes the output to the sudo chpasswd command. The chpasswd command reads the username and password from the standard input and sets the password for the specified user.
        
    * After adding the user and setting the password, we display the username of the newly created user. The line echo "User: $user" prints "User: username" on the terminal, where username is the name of the user that was just added.
        
    * Give the required permissions(chmod +x filename.sh) and execute it using ./filename.sh.
        

> THIS MIGHT SEEM LENGTHY COZ OF THE WAY I TRIED TO MAKE EVERYONE UNDERSTAND :D
> 
> STAY TUNED FOR MORE ADVANCED CONTENT
> 
> HAPPY LEARNING :D