---
title: "Day-03 : TWS BashBlaze Challenge 🔥"
datePublished: Wed Aug 02 2023 15:26:15 GMT+0000 (Coordinated Universal Time)
cuid: clktvrrp7000d09jx856a63hd
slug: day-03-tws-bashblaze-challenge
tags: linux, devops, 90daysofdevops, twsbashblazechallenge, twsbashblazechallenge-trainwithshubham

---

## Challenge: User Account Management

## Part 1: Account Creation

* Implement an option -c or --create that allows the script to create a new user account. The script should prompt the user to enter the new username and password.
    
* Ensure that the script checks whether the username is available before creating the account. If the username already exists, display an appropriate message and exit gracefully.
    
* After creating the account, display a success message with the newly created username.
    
    ```bash
    # Create a new user account 
    
    if [ "$1" == "-c" ] || [ "$1" == "--create" ]
     then
        read -p "Enter a new username: " username
        id "$username" &>/dev/null
        if [ $? -eq 0 ]; then
            echo "The username '$username' already exists. Please choose a different username."
        else
            sudo useradd -m "$username"
            sudo passwd "$username"
            echo "User account '$username' created successfully."
        fi
    ```
    

## Part 2: Account Deletion

* Implement an option -d or --delete that allows the script to delete an existing user account. The script should prompt the user to enter the username of the account to be deleted.
    
* Ensure that the script checks whether the username exists before attempting to delete the account. If the username does not exist, display an appropriate message and exit gracefully.
    
* After successfully deleting the account, display a confirmation message with the deleted username.
    
    ```bash
    elif [ "$1" == "-d" ] || [ "$1" == "--delete" ]
     then
        read -p "Enter the username to delete: " username
        id "$username" &>/dev/null
        if [ $? -eq 0 ]; then
            sudo userdel -r "$username"
            echo "Done! Account '$username' deleted successfully."
        else
            echo "Sorry, The username '$username' doesn't exist.Please enter a valid username"
    
        fi
    ```
    

## Part 3: Password Reset

* Implement an option -r or --reset that allows the script to reset the password of an existing user account. The script should prompt the user to enter the username and the new password.
    
* Ensure that the script checks whether the username exists before attempting to reset the password. If the username does not exist, display an appropriate message and exit gracefully.
    
* After resetting the password, display a success message with the username and the updated password.
    
* ```bash
    elif [ "$1" == "-r" ] || [ "$1" == "--reset" ]
     then
        read -p "Enter the username to reset password: " username
        id "$username" &>/dev/null
        if [ $? -eq 0 ]; then
            sudo passwd "$username"
            echo "Password for '$username' reset successfully."
        else
            echo "Uh-oh! '$username' doesn't exist."
        fi
    ```
    

## Part 4: List User Accounts

* Implement an option -l or --list that allows the script to list all user accounts on the system. The script should display the usernames and their corresponding user IDs (UID).
    
    ```bash
    elif [ "$1" == "-l" ] || [ "$1" == "--list" ]
     then
        echo "User accounts on the system :"
        echo "Username   UID"
        echo "----------------"
        awk -F: '{print $1 "   " $3}' /etc/passwd
    ```
    

## Part 5: Help and Usage Information

* Implement an option -h or --help that displays usage information and the available command-line options for the script.
    
    ```bash
    if [ "$1" == "-h" ] || [ "$1" == "--help" ]
     then
        echo "Usage: $0 [OPTIONS]"
        echo "Options:"
        echo "  -c, --create  Create a new user account."
        echo "  -d, --delete  Delete an existing user account."
        echo "  -r, --reset   Reset password for an existing user account."
        echo "  -l, --list    List all user accounts on the system."
        echo "  -h, --help    Show this help message"
        echo "  -i, --info    Display the user information"
        echo "  -m, --modify  Modify user properties"
        exit 0
    fi
    ```
    

## Bonus Points (Optional)

* If you want to challenge yourself further, you can add additional features to the script, such as:
    
* Displaying more detailed information about user accounts (e.g., home directory, shell, etc.).
    
    ```bash
    # Display detailed information about a user account
    
    elif [ "$1" == "-i" ] || [ "$1" == "--info" ]
     then
        read -p "Enter username to display information: " info_username
        if id "$info_username" &>/dev/null; then
            finger "$info_username"
        else
            echo "Error: Username '$info_username' does not exist."
        fi
    ```
    
* Allowing the modification of user account properties (e.g., username, user ID, etc.).
    

```bash
# Modify user accoun properties

elif [ "$1" == "-m" ] || [ "$1" == "--modify" ]
 then
    read -p "Enter username to modify properties: " modify_username
    if id "$modify_username" &>/dev/null; then
        read -p "Enter new username (leave empty to keep current): " new_username
        read -p "Enter new UID (leave empty to keep current): " new_uid
        if [[ -n "$new_username" ]]; then
            sudo usermod -l "$new_username" "$modify_username"
            echo "Username for user '$modify_username' changed to '$new_username'."
        fi
        if [[ -n "$new_uid" ]]; then
            sudo usermod -u "$new_uid" "$modify_username"
            echo "UID for user '$modify_username' changed to '$new_uid'."
        fi
    else
        echo "Error: Username '$modify_username' does not exist."
    fi
```

Handle Invalid options

```bash
# Handle invalid options

else
    echo "Oops! Invalid option: $1"
    echo "Use '$0 -h' to see available options."
    exit 1
fi
```

## FINAL SOLUTION :

```bash
#!/bin/bash

# Check for help option

if [ "$1" == "-h" ] || [ "$1" == "--help" ]
 then
    echo "Usage: $0 [OPTIONS]"
    echo "Options:"
    echo "  -c, --create  Create a new user account."
    echo "  -d, --delete  Delete an existing user account."
    echo "  -r, --reset   Reset password for an existing user account."
    echo "  -l, --list    List all user accounts on the system."
    echo "  -h, --help    Show this help message"
    echo "  -i, --info    Display the user information"
    echo "  -m, --modify  Modify user properties"
    exit 0
fi

# Create a new user account 

if [ "$1" == "-c" ] || [ "$1" == "--create" ]
 then
    read -p "Enter a new username: " username
    id "$username" &>/dev/null
    if [ $? -eq 0 ]; then
        echo "The username '$username' already exists. Please choose a different username."
    else
        sudo useradd -m "$username"
        sudo passwd "$username"
        echo "User account '$username' created successfully."
    fi

# Delete an existing user account 

elif [ "$1" == "-d" ] || [ "$1" == "--delete" ]
 then
    read -p "Enter the username to delete: " username
    id "$username" &>/dev/null
    if [ $? -eq 0 ]; then
        sudo userdel -r "$username"
        echo "Done! Account '$username' deleted successfully."
    else
        echo "Sorry, The username '$username' doesn't exist.Please enter a valid username"

    fi
    
# Reset password for a user account

elif [ "$1" == "-r" ] || [ "$1" == "--reset" ]
 then
    read -p "Enter the username to reset password: " username
    id "$username" &>/dev/null
    if [ $? -eq 0 ]; then
        sudo passwd "$username"
        echo "Password for '$username' reset successfully."
    else
        echo "Uh-oh! '$username' doesn't exist."
    fi

# List all the user accounts

elif [ "$1" == "-l" ] || [ "$1" == "--list" ]
 then
    echo "User accounts on the system :"
    echo "Username   UID"
    echo "----------------"
    awk -F: '{print $1 "   " $3}' /etc/passwd
    

# Display detailed information about a user account

elif [ "$1" == "-i" ] || [ "$1" == "--info" ]
 then
    read -p "Enter username to display information: " info_username
    if id "$info_username" &>/dev/null; then
        finger "$info_username"
    else
        echo "Error: Username '$info_username' does not exist."
    fi

# Modify user accoun properties

elif [ "$1" == "-m" ] || [ "$1" == "--modify" ]
 then
    read -p "Enter username to modify properties: " modify_username
    if id "$modify_username" &>/dev/null; then
        read -p "Enter new username (leave empty to keep current): " new_username
        read -p "Enter new UID (leave empty to keep current): " new_uid
        if [[ -n "$new_username" ]]; then
            sudo usermod -l "$new_username" "$modify_username"
            echo "Username for user '$modify_username' changed to '$new_username'."
        fi
        if [[ -n "$new_uid" ]]; then
            sudo usermod -u "$new_uid" "$modify_username"
            echo "UID for user '$modify_username' changed to '$new_uid'."
        fi
    else
        echo "Error: Username '$modify_username' does not exist."
    fi

# Handle invalid options

else
    echo "Oops! Invalid option: $1"
    echo "Use '$0 -h' to see available options."
    exit 1
fi
```