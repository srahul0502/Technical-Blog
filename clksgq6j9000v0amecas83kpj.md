---
title: "Day-02 : TWS BashBlaze Challenge 🔥"
datePublished: Tue Aug 01 2023 15:37:21 GMT+0000 (Coordinated Universal Time)
cuid: clksgq6j9000v0amecas83kpj
slug: day-02-tws-bashblaze-challenge
tags: linux, devops, twsbashblazechallenge-trainwithshubham

---

## Day 2.0 explore :

### Part 1: File and Directory Exploration

1. Upon execution without any command-line arguments, the script will display a welcome message and list all the files and directories in the current path.
    
2. For each file and directory, the script will print its name and size in human-readable format (e.g., KB, MB, GB). This information will be obtained using the ls command with appropriate options.
    
3. The list of files and directories will be displayed in a loop until the user decides to exit the explorer.
    
    ```bash
    #!/bin/bash
    
    # Display welcome message and list files/directories
    echo "Welcome to the Interactive File and Directory Explorer!"
    echo "Current path: $(pwd)"
    echo -e "\nFiles and Directories in the Current Path:"
    for item in ./*; do
        prefix="-"
        size=$(du -sh "$item" | cut -f1)
        name=$(basename "$item")
        echo "$prefix $name ($size)"
    done
    ```
    

## Part 2: Character Counting

1. After displaying the file and directory list, the script will prompt the user to enter a line of text.
    
2. The script will read the user's input until an empty string is entered (i.e., the user presses Enter without any text).
    
3. For each line of text entered by the user, the script will count the number of characters in that line.
    
4. The character count for each line entered by the user will be displayed.
    
    ```bash
    # Interactive loop
    while true 
    do
        # Ask the user to enter a line of text
        # Prompt the user to enter a line of text and store the input into the variable user_input
        read -p "Enter a line of text (Press Enter without text to exit): " user_input
    
        # Check if the user pressed Enter without entering any text (exit the loop in this case)
        # -z is a test operator used to check if the given string is empty
        if [ -z "$user_input" ] 
        then
            echo "Exiting the Interactive Explorer. Goodbye!"
            break
        fi
    
        # Count and display the number of characters in the entered text
        # '#' symbol, when used in this context, denotes the length of the variable's value.
        #  So, ${#user_input} returns the number of characters in the value of the user_input variable.
        echo "Character Count: ${#user_input}"
    done
    ```
    
    ## Solution :
    
    ```bash
    #!/bin/bash
    
    # Display welcome message and list files/directories
    echo "Welcome to the Interactive File and Directory Explorer!"
    echo "Current path: $(pwd)"
    echo -e "\nFiles and Directories in the Current Path:"
    # /* is a glob pattern that matches all files and directories in the current directory
    for item in ./*
    do
        prefix="-"
        # 'du' -estimate file space usage , '-s'(short summary) tells
        # 'du' to display only the total size of the specified file or directory
        # '-h' display the size in human readable format 
        size=$(du -sh "$item" | cut -f1)
        # cut -f1 : we extract only the size portion and ignore the path
        name=$(basename "$item")
        echo "$prefix $name ($size)"
    done
    # Interactive loop
    while true 
    do
        # Ask the user to enter a line of text
        # Prompt the user to enter a line of text and store the input into the variable user_input
        read -p "Enter a line of text (Press Enter without text to exit): " user_input
    
        # Check if the user pressed Enter without entering any text (exit the loop in this case)
        # -z is a test operator used to check if the given string is empty
        if [ -z "$user_input" ] 
        then
            echo "Exiting the Interactive Explorer. Goodbye!"
            break
        fi
    
        # Count and display the number of characters in the entered text
        # '#' symbol, when used in this context, denotes the length of the variable's value.
        #  So, ${#user_input} returns the number of characters in the value of the user_input variable.
        echo "Character Count: ${#user_input}"
    done
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690904192350/d84a6496-38c0-41d5-8d22-8ebb245619c0.png align="center")
    

## Day 2.1 Backup :

## Directory Backup with Rotation

Create a bash script that takes a directory path as a command-line argument and performs a backup of the directory. The script should create timestamped backup folders and copy all the files from the specified directory into the backup folder.

## SOLUTION :

```bash
#!/bin/bash

# Check if a directory path is provided as a command-line argument
# checks if the number of command-line arguments is not equal to 1
if [ $# -ne 1 ]
 then
    echo "Usage: $0 <directory_path>"
    exit 1
fi

# Validate if the provided argument is a directory
backup_source="$1"
# The -d test operator checks if the given path exists and is a directory
if [ ! -d "$backup_source" ]
 then
    echo "Error: The provided path is not a valid directory."
    exit 1
fi

# Create a timestamp for the backup folder
backup_time=$(date +"%Y-%m-%d_%H-%M-%S")
backup_folder="${backup_source}/backup_${backup_time}"

# Perform the backup
# rsync is a powerful file copying tool
rsync -Rr "$backup_source" "$backup_folder" || {echo "Error: Backup failed." exit 1}

# Perform rotation to keep only the last 3 backups
# here we list the folders in reverse chronological order and remove the older backups
ls -dt "${backup_source}/backup_"* | tail -n +4 | xargs rm -rf

# Provide feedback to the user
echo "Backup created: $backup_folder."
```