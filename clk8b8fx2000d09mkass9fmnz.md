---
title: "Basic Linux Shell Scripting"
datePublished: Tue Jul 18 2023 13:08:11 GMT+0000 (Coordinated Universal Time)
cuid: clk8b8fx2000d09mkass9fmnz
slug: basic-linux-shell-scripting
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1689684576306/0fed1f7b-81c3-4462-93f5-e010ddae88ff.webp
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1689684919634/7fc51fd8-62c4-4aab-8a27-a3cbc5bc97bc.jpeg
tags: linux, bash, devops, shell-scripting, 90daysofdevops

---

## ℹ️ Introduction

* Automation is crucial to streamlining and improving numerous tasks in the DevOps environment. Shell scripting, which enables system administrators and developers to automate repetitive activities and increase efficiency, is one of the crucial tools in the DevOps toolbox.
    
* The foundations of shell scripting will be discussed in this blog article, with a special emphasis on the shebang notation, notably #!/bin/bash and its alternate, #!/bin/sh.
    

## 📝 What is Shell Scripting?

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689664213933/1b515376-232d-4215-882d-aca34b912aed.jpeg align="center")

⌨️ Writing scripts using a shell interpreter is referred to as shell scripting. A command-line application known as a shell interpreter runs commands taken from a script file.

Different shell languages, including:

* Bash (Bourne Again SHell), sh (Bourne Shell), csh (C Shell), and others, can be used to create shell scripts.
    

⌨️ Shell scripting enables DevOps professionals to automate a variety of operations, such as configuration management, file manipulation, application deployment, and system administration.

## 🔍 Understanding #!/bin/bash#️⃣

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689666964956/a5a99b9d-4e47-4db9-af1c-d544792aaa34.png align="center")

🥇 The first line of a script file is the shebang line, commonly referred to as the hashbang or the interpreter directive.

#️⃣ It starts with #! followed by the path to the shell interpreter. Here's what #!/bin/bash means:

* #!/bin/bash indicates that the script should be interpreted by the Bash shell.
    
* Bash is a powerful shell available on most Unix-based systems, including Linux.
    
* Bash offers a wide range of features like variables, conditionals, loops, functions, and more.
    
* It supports command execution, string manipulation, file handling, and process control.
    

⌨️ With its robust capabilities, Bash enables DevOps practitioners to write complex and sophisticated scripts to automate tasks effectively.

ℹ️ Variables, conditionals, loops, functions, and more are among the numerous programming constructs available in Bash. Additionally, it offers comprehensive support for command execution, string manipulation, file handling, and process control.

## 🔀 Can we write #!/bin/sh instead🤔❓

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689667744686/11b9c08e-dd1f-4dba-9dca-6c5809182235.jpeg align="center")

🙌 Yes, you can substitute #!/bin/sh for #!/bin/bash in the shebang line. Depending on the setup of the system, the Bourne Shell (sh) or a shell that is compatible with it interprets the script in this case.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689667790153/955b255a-ca84-481f-a3eb-2c8e45a3bc63.jpeg align="center")

🤔 One of the most well-known and well-established shell interpreters is the Bourne Shell. It may not have all of the more complex features and capabilities that Bash offers, but it still provides a strong foundation for simple scripting requirements.

#️⃣ Using #!/bin/sh instead of #!/bin/bash can make your script more portable across different Unix-like systems

⌨️ Using #!/bin/sh ensures that your script will work in environments where Bash might not be available or might be located in a different path.

## ⌨️ Writing Shell Scripts#️⃣❗

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689668084913/025f1834-f44c-43b3-822e-cfe60b0ca95b.gif align="center")

* Lets understand this by solving few questions :
    

1. **Write a Shell Script which prints I will complete #90DaysofDevOps challenge**
    
    ```bash
    #!/bin/bash
    
    echo "I will complete #90DaysOfDevOps challenge"
    ```
    
    **📜 Steps to Follow :**
    
    1. Open a text editor and create a new file.
        
        * Open terminal and type nano/vim to open the text editor
            
            ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689680800675/d96333a1-5e14-4d68-9cec-669234183744.png align="center")
            
    2. Copy and paste the above script into the file.
        
        * Copy paste the above script into the editor
            
            ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689680829296/bf9bce2a-f1a8-440e-bd6e-aa3fba24c60c.png align="center")
            
    3. Save the file with a .sh extension (e.g., [challenge.sh](http://challenge.sh)).
        
        * Exit the editor by ctrl+x
            
        * press y to save the file
            
        * After that it'll ask you to name the file , save it with .sh extension and press enter
            
            ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689680873360/6d3eac39-ac63-4587-a854-2244bd433596.png align="center")
            
    4. Open a terminal or command prompt.
        
    5. Navigate to the directory where you saved the script.
        
        * Use cd(change directory) to navigate to the directory where you saved the script
            
    6. Run the script by typing ./[challenge.sh](http://challenge.sh) and pressEnter.
        
        ```bash
        ./challenge.sh
        # to execute the filr
        ```
        
    7. 📁 If you get error such as "permission denied"when you use\*\*./ filename.sh\*\* then follow the steps given below:
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689681217746/1976a9fa-a8f9-4ab5-8522-687dace95818.png align="center")
        
        * You need to give execute and read permissions to the file with .sh extension
            
            * This can be done by using chmod(change file access mode) command.
                
                ```bash
                chmod u+r+x challenge.sh
                # only read and execute permission to the current user
                or 
                chmod +x challenge.sh
                # only execute permission
                or 
                chmod 777 filename.sh 
                # gives all the permissions w+x+r  
                # read , write and execute permissions are given
                ```
                
            * In the above command :
                
                * u stands for - user
                    
                * r stands for - read
                    
                * x stands for - execute
                    
                * w stands for - write
                    
            * **chmod u+r+x** will grant only the owner of that file reading and execution permissions whereas **chmod +x** filename is same as **chmod a+x filename**.
                
2. **Write a Shell Script to take user input, input from arguments and print the variables.**
    
    ```bash
    #!/bin/bash
    
    # Prompt the user for input
    echo "Enter your name:"
    read name
    
    # Check if command-line arguments are provided
    if [ $# -gt 0 ]; then
        # If arguments are provided, assign the first argument to the variable
        argument=$1
    else
        # If no arguments are provided, assign a default value to the variable
        argument="No argument provided"
    fi
    
    # Print the variables
    echo "User input: $name"
    echo "Command-line argument: $argument"
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689684422310/fa092d3c-8224-463b-ac73-3fcb76808b26.png align="center")
    
    **📜 Let's Understand this line by line :**
    
    * **#!/bin/bash:** This is the shebang line, which specifies the shell interpreter to use (in this case, Bash)
        
    * **echo "Enter your name:" :** This line prompts the user to enter their name and displays the message on the terminal.
        
    * **read name :** The read command is used to read input from the user. In this case, it reads the user's input and assigns it to the variable "name" .
        
    * **if \[ $# -gt 0 \]; then :** This is an if statement that checks if any command-line arguments are provided. $# represents the number of command-line arguments passed to the script. If the number of arguments is greater than 0, it means at least one argument is provided.
        
    * **argument=$1 :** If command-line arguments are provided, the first argument ($1) is assigned to the variable argument.
        
    * **else :** If no command-line arguments are provided, the script proceeds to the else block.
        
    * **argument=”No argument provided”:** In the else block, a default value of “No argument provided” is assigned to the argument variable.
        
    * **echo “User input: $name”:** This line prints the value of the name variable, which contains the user's input.
        
    * **echo “Command-line argument: $argument”:** This line prints the value of the argument variable, which contains the command-line argument (if provided) or the default value.
        
    
    *The script combines user input and command-line argument handling to print both the user's input and the command-line argument (if any) to the terminal.*
    
    * *By using the read command, the script waits for the user to enter their name before proceeding. If a command-line argument is provided when executing the script, it will be assigned to the argument variable.*
        
    * *otherwise, a default value will be used. Finally, the script displays the values of both variables, name and argument, using the echo command.*
        
    
    📜 **As we understood the script , lets move to the execution part:**
    
    * The exection is same as we did in the first question.
        
    * U have to copy paste the above script and save the file with .sh extension and run it using **./fielane.sh** or **bash filename.sh ( to avoid errors) .**
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689685635516/6fbf3c40-a136-44b7-bcdd-bfa288a9ff82.png align="center")
        
    * The script will prompt you to enter your name. After entering your name, press Enter. Then, it will check if any command-line arguments are provided. If an argument is given, it will be assigned to the argument variable. If no argument is provided, a default value will be assigned.
        
        The script will then print the user input and the command-line argument (if provided).
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689683025790/93b6ac0d-5dc4-4115-b58d-77571fa6f2c9.png align="center")
        
3. **Write an Example of If else in Shell Scripting by comparing 2 numbers.**
    

```bash
#!/bin/bash

number1=10
number2=5

if [ $number1 -gt $number2 ]; then
    echo "$number1 is greater than $number2"
elif [ $number1 -lt $number2 ]; then
    echo "$number1 is less than $number2"
else
    echo "$number1 is equal to $number2"
fi
```

📜 **Let's understand this script line by line:**

* **#!/bin/bash:** This is the shebang line, specifying the shell interpreter as Bash.
    
* **if \[ $number1 -gt $number2 \]; then:** This if statement compares the values of number1 and number2. The -gt operator checks if $number1 is greater than $number2.
    
* **echo "$number1 is greater than $number2":** If number1 is greater than number2, this line will be executed and print the corresponding message.
    
* **elif \[ $number1 -lt $number2 \]; then:** If the condition in the if statement is false, the script proceeds to this elif block. The -lt operator checks if $number1 is less than $number2.
    
* **echo "$number1 is less than $number2":** If number1 is less than number2, this line will be executed and print the corresponding message.
    
* else: If both the if and elif conditions are false, the script proceeds to this else block.
    
* **echo "$number1 is equal to $number2":** If none of the above conditions are true, this line will be executed and print the corresponding message.
    

**📜 Let's go to the execution part :**

* It is similar to the above two questions .
    
* Copy paste the above script in a file and save it with .sh extension.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689685654235/408268cf-3b1e-4480-9be0-8da5069e0c9b.png align="center")
    
* execute it by running ./finename.sh , if you get error such as "permission denied"
    
    change it using **chmod +x filename.sh** or give all permissions at once using **chmod 777 filename.sh**
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689748898571/676c081c-89a3-4751-82e1-24608f8a279c.png align="center")

> I hope it gave you idea about the shell scripting , Please let me know if any changes needed, i know the explaination part is kinda boring but i'm sure that it'll make you understand Scripting better.
> 
> Happy Learning :D
> 
> Stay Tuned D