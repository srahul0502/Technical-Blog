---
title: "Day-06: TWS BashBlaze Challenge 🔥"
datePublished: Sat Aug 05 2023 13:07:26 GMT+0000 (Coordinated Universal Time)
cuid: clky14taf00040al8fghw8db3
slug: day-06-tws-bashblaze-challenge
tags: linux, bash, 90daysofdevops, tws, twsbashblazechallenge-trainwithshubham

---

# The Mysterious Script

```bash
#!/bin/bash

# Welcome to the Mysterious Script Challenge!
# Your task is to unravel the mystery behind this script and understand what it does.
# Once you've deciphered its objective, your mission is to improve the script by adding comments and explanations for clarity.

# DISCLAIMER: This script is purely fictional and does not perform any harmful actions.
# It's designed to challenge your scripting skills and creativity.

# Function to perform mysterious transformations
mysterious_function() {
    local input_file="$1"
    local output_file="$2"

    # Step 1: Apply a Caesar cipher-like transformation (rotate letters by 13 positions)
    tr 'A-Za-z' 'N-ZA-Mn-za-m' < "$input_file" > "$output_file"

    # Step 2: Reverse the content of the output file
    rev "$output_file" > "reversed_temp.txt"

    # Step 3: Generate a random number between 1 and 10
    random_number=$(( ( RANDOM % 10 ) + 1 ))

    # Mystery loop: Repeat the following steps 'random_number' times
    for (( i=0; i<$random_number; i++ )); do
        # Step 4: Reverse the content of 'reversed_temp.txt'
        rev "reversed_temp.txt" > "temp_rev.txt"

        # Step 5: Apply the same Caesar cipher-like transformation on the reversed content
        tr 'A-Za-z' 'N-ZA-Mn-za-m' < "temp_rev.txt" > "temp_enc.txt"

        # Step 6: Replace 'reversed_temp.txt' with the newly encrypted content
        mv "temp_enc.txt" "reversed_temp.txt"
    done

    # Clean up temporary files
    rm "temp_rev.txt"

    # The mystery continues...
    # Step 7: Reverse the final content and save it to the output file
    rev "reversed_temp.txt" > "$output_file"

    # Step 8: Clean up remaining temporary files
    rm "reversed_temp.txt"

    # The mystery concludes!
}

# Main Script Execution

echo "Welcome to the Mysterious Script Challenge!"
echo "Please provide an input file and an output file."

# Ask for input and output file paths
read -p "Enter the input file path: " input_file
read -p "Enter the output file path: " output_file

# Check if the input file exists
if [ ! -f "$input_file" ]; then
    echo "Error: Input file not found!"
    exit 1
fi

# Call the mysterious function to begin the process
mysterious_function "$input_file" "$output_file"

# Display the mysterious output
echo "The mysterious process is complete. Check the '$output_file' for the result!"
```

# Restaurant Order System Challenge

```bash
#!/bin/bash

# Function to read and display the menu from menu.txt file
function display_menu() {
    echo "Welcome to the Restaurant!"
    echo "Menu:"
    
    local menu_file="menu.txt"
    local item_number=1
    
    # Read and display menu items and prices from menu.txt
    while IFS=',' read -r item price; do
        echo "$item_number. $item - ₹$price"
        ((item_number++))
    done < "$menu_file"
}

# Function to calculate the total bill
function calculate_total_bill() {
    local total=0
    local menu_file="menu.txt"

    # Create an associative array to store menu item prices
    declare -A item_prices
    while IFS=',' read -r item price; do
        item_prices["$item_number"]=${price//[^0-9]/}
        ((item_number++))
    done < "$menu_file"

    # Calculate the total bill based on the order
    for item_number in "${!order[@]}"; do
        quantity=${order["$item_number"]}
        price=${item_prices["$item_number"]}
        subtotal=$((price * quantity))
        total=$((total + subtotal))
    done

    echo "$total"
}

# Function to handle invalid user input
function handle_invalid_input() {
    echo "Invalid input! Please enter a valid item number and quantity."
}

# Main script
display_menu

# Ask for the customer's name
echo -n "Please enter your name: "
read customer_name

# Ask for the order
echo "Please enter the item number and quantity (e.g., 1 2 for two Burgers):"
read -a input_order

# Process the customer's order
declare -A order
for (( i=0; i<${#input_order[@]}; i+=2 )); do
    item_number="${input_order[i]}"
    quantity="${input_order[i+1]}"
    order["$item_number"]=$quantity
done

# Calculate the total bill
total_bill=$(calculate_total_bill)

# Display the total bill with a personalized thank-you message
echo "Thank you, $customer_name! Your total bill is ₹$total_bill."
```

# Recursive Directory Search Challenge

```bash
#!/bin/bash

# Check if exactly two arguments are provided
if [ $# -ne 2 ]; then
    echo "Usage: $0 <directory> <target file>"
    exit 1
fi

# Define a recursive function to search for the target file
recursive_search() {
    local dir="$1"
    local target="$2"

    # Loop through entries (files and directories) in the given directory
    for entry in "$dir"/*; do
        if [ -f "$entry" ] && [ "$(basename "$entry")" = "$target" ]; then
            # If a file with the target name is found, print its path and exit
            echo "File found: $entry"
            exit 0
        elif [ -d "$entry" ]; then
            # If an entry is a directory, recursively search within it
            recursive_search "$entry" "$target"
        fi
    done
}

# Get the search directory and target file from command-line arguments
search_directory="$1"
target_file="$2"

# Check if the specified directory exists
if [ ! -d "$search_directory" ]; then
    echo "Directory not found: $search_directory"
    exit 1
fi

# Get the absolute path of the search directory
absolute_path=$(cd "$search_directory" && pwd)


# Initiate the recursive search
recursive_search "$absolute_path" "$target_file"

# If target file is not found, print an error message
echo "File not found: $target_file"
exit 1
```

Kindly visit my github Repo for detailed documentation: [https://github.com/srahul0502/BashBlaze-7-Days-of-Bash-Scripting-Challenge/tree/dev/Challenges/Day\_6](https://github.com/srahul0502/BashBlaze-7-Days-of-Bash-Scripting-Challenge/tree/dev/Challenges/Day_6)