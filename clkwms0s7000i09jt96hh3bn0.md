---
title: "Day-05: TWS BashBlaze Challenge 🔥"
datePublished: Fri Aug 04 2023 13:37:49 GMT+0000 (Coordinated Universal Time)
cuid: clkwms0s7000i09jt96hh3bn0
slug: day-05-tws-bashblaze-challenge
tags: linux, bash, scripting, 90daysofdevops, twsbashblazechallenge-trainwithshubham

---

## Log Analyzer and Report Generator

## Task

Write a Bash script that automates the process of analyzing log files and generating a daily summary report. The script should perform the following steps:

1. **Input:** The script should take the path to the log file as a command-line argument.
    
    ```bash
    #!/bin/bash
    
    echo "Log Analyzer & Report Generator"
    
    # Check if a log file path is provided as a command-line argument
    if [ $# -ne 1 ]; then
        echo "Usage: $0 <path_to_log_file>"
        exit 1
    fi
    
    log_file="$1"
    
    # Check if the log file exists
    if [ ! -f "$log_file" ]; then
        echo "Error: Log file '$log_file' not found."
        exit 1
    fi
    ```
    
2. **Error Count:** Analyze the log file and count the number of error messages. An error message can be identified by a specific keyword (e.g., "ERROR" or "Failed"). Print the total error count.
    
    ```bash
    # Count and print the total error count based on keywords using grep
    count_errors=$(grep -ciE "Error|failed" "$log_file")
    echo -e "\nNumber of errors found in log file: $count_errors"
    ```
    
3. **Critical Events:** Search for lines containing the keyword "CRITICAL" and print those lines along with the line number.
    
    ```bash
    # Printing critical errors 
    critical_error=$(grep -n "CRITICAL" "$log_file")
    echo -e "\nThese are the lines containing the keyword 'CRITICAL':"
    echo -e "\n$critical_error"
    ```
    
4. **Top Error Messages:** Identify the top 5 most common error messages and display them along with their occurrence count.
    
    ```bash
    # Identify and display top 5 most common error messages with occurrence count
    top_errors=$(grep -iE "error|failed" "$log_file" | sort | uniq -c | sort -nr | head -n 5 | awk '{$1=$1; for(i=1;i<=NF;i++) { printf "%-2s ", $i } printf "\n"}')
    # Display the results with left-aligned columns
    echo -e "\nTop 5 most common error messages:"
    echo "___________________________________"
    echo "$top_errors"
    ```
    
5. **Summary Report:** Generate a summary report in a separate text file. The report should include:
    
    * Date of analysis
        
    * Log file name
        
    * Total lines processed
        
    * Total error count
        
    * Top 5 error messages with their occurrence count
        
    * List of critical events with line numbers
        
        ```bash
        # Generate Summary Report
        summary_file="summary_report.txt"
        
        {
            echo "Date of analysis: $(date)"
            echo "Log file name: $log_file"
            echo "Total lines processed: $(wc -l < "$log_file")"
            echo "Total error count: $count_errors"
            echo -e "\nTop 5 error messages with occurrence count:"
            echo "$top_errors"
            echo -e "\nList of critical events (with line numbers):"
            echo "$critical_error"
        } > "$summary_file"
        
        echo -e "\nSummary report generated: $summary_file"
        ```
        
6. **Optional Enhancement:** Add a feature to automatically archive or move processed log files to a designated directory after analysis.
    
    ```bash
    # Ask the user if they want to archive the log file
    read -p "Do you want to archive the log file? (y/n): " choice
    if [ "$choice" == "y" ] || [ "$choice" == "Y" ]; then
        read -p "Enter the destination directory for archiving: " destination_dir
        if [ ! -d "$destination_dir" ]; then
            echo "Creating destination directory: $destination_dir"
            mkdir -p "$destination_dir"
        fi
    
        archive_name=$(basename "$log_file").$(date +"%Y%m%d%H%M%S").tar.gz
        tar -czvf "$destination_dir/$archive_name" "$log_file"
        echo -e "\nLog file archived to: $destination_dir/$archive_name"
    else
        echo "You chose not to archive the log file."
        echo "Thank you for using our script."
    fi
    ```
    
    FINAL SOLUTION:
    
    ```bash
    #!/bin/bash
    
    echo "Log Analyzer & Report Generator"
    
    # Check if a log file path is provided as a command-line argument
    if [ $# -ne 1 ]; then
        echo "Usage: $0 <path_to_log_file>"
        exit 1
    fi
    
    log_file="$1"
    
    # Check if the log file exists
    if [ ! -f "$log_file" ]; then
        echo "Error: Log file '$log_file' not found."
        exit 1
    fi
    
    # Count and print the total error count based on keywords using grep
    count_errors=$(grep -ciE "Error|failed" "$log_file")
    echo -e "\nNumber of errors found in log file: $count_errors"
    
    # Printing critical errors 
    critical_error=$(grep -n "CRITICAL" "$log_file")
    echo -e "\nThese are the lines containing the keyword 'CRITICAL':"
    echo -e "\n$critical_error"
    
    # Identify and display top 5 most common error messages with occurrence count
    top_errors=$(grep -iE "error|failed" "$log_file" | sort | uniq -c | sort -nr | head -n 5 | awk '{$1=$1; for(i=1;i<=NF;i++) { printf "%-2s ", $i } printf "\n"}')
    # Display the results with left-aligned columns
    echo -e "\nTop 5 most common error messages:"
    echo "___________________________________"
    echo "$top_errors"
    
    # Generate Summary Report
    summary_file="summary_report.txt"
    
    {
        echo "Date of analysis: $(date)"
        echo "Log file name: $log_file"
        echo "Total lines processed: $(wc -l < "$log_file")"
        echo "Total error count: $count_errors"
        echo -e "\nTop 5 error messages with occurrence count:"
        echo "$top_errors"
        echo -e "\nList of critical events (with line numbers):"
        echo "$critical_error"
    } > "$summary_file"
    
    echo -e "\nSummary report generated: $summary_file"
    
    # Ask the user if they want to archive the log file
    read -p "Do you want to archive the log file? (y/n): " choice
    if [ "$choice" == "y" ] || [ "$choice" == "Y" ]; then
        read -p "Enter the destination directory for archiving: " destination_dir
        if [ ! -d "$destination_dir" ]; then
            echo "Creating destination directory: $destination_dir"
            mkdir -p "$destination_dir"
        fi
    
        archive_name=$(basename "$log_file").$(date +"%Y%m%d%H%M%S").tar.gz
        tar -czvf "$destination_dir/$archive_name" "$log_file"
        echo -e "\nLog file archived to: $destination_dir/$archive_name"
    else
        echo "You chose not to archive the log file."
        echo "Thank you for using our script."
    fi
    
    #!/bin/bash
    
    echo "Log Analyzer & Report Generator"
    
    # Check if a log file path is provided as a command-line argument
    if [ $# -ne 1 ]; then
        echo "Usage: $0 <path_to_log_file>"
        exit 1
    fi
    
    log_file="$1"
    
    # Check if the log file exists
    if [ ! -f "$log_file" ]; then
        echo "Error: Log file '$log_file' not found."
        exit 1
    fi
    
    # Count and print the total error count based on keywords using grep
    count_errors=$(grep -ciE "Error|failed" "$log_file")
    echo -e "\nNumber of errors found in log file: $count_errors"
    
    # Printing critical errors 
    critical_error=$(grep -n "CRITICAL" "$log_file")
    echo -e "\nThese are the lines containing the keyword 'CRITICAL':"
    echo -e "\n$critical_error"
    
    # Identify and display top 5 most common error messages with occurrence count
    top_errors=$(grep -iE "error|failed" "$log_file" | sort | uniq -c | sort -nr | head -n 5 | awk '{$1=$1; for(i=1;i<=NF;i++) { printf "%-2s ", $i } printf "\n"}')
    # Display the results with left-aligned columns
    echo -e "\nTop 5 most common error messages:"
    echo "___________________________________"
    echo "$top_errors"
    
    # Generate Summary Report
    summary_file="summary_report.txt"
    
    {
        echo "Date of analysis: $(date)"
        echo "Log file name: $log_file"
        echo "Total lines processed: $(wc -l < "$log_file")"
        echo "Total error count: $count_errors"
        echo -e "\nTop 5 error messages with occurrence count:"
        echo "$top_errors"
        echo -e "\nList of critical events (with line numbers):"
        echo "$critical_error"
    } > "$summary_file"
    
    echo -e "\nSummary report generated: $summary_file"
    
    # Ask the user if they want to archive the log file
    read -p "Do you want to archive the log file? (y/n): " choice
    if [ "$choice" == "y" ] || [ "$choice" == "Y" ]; then
        read -p "Enter the destination directory for archiving: " destination_dir
        if [ ! -d "$destination_dir" ]; then
            echo "Creating destination directory: $destination_dir"
            mkdir -p "$destination_dir"
        fi
    
        archive_name=$(basename "$log_file").$(date +"%Y%m%d%H%M%S").tar.gz
        tar -czvf "$destination_dir/$archive_name" "$log_file"
        echo -e "\nLog file archived to: $destination_dir/$archive_name"
    else
        echo "You chose not to archive the log file."
        echo "Thank you for using our script."
    fi
    ```
    
    * Save it as log\_analyzer.sh and give required permissions 'chmod +x log\_analyzer.sh'
        
    * Execute it using ./log\_analyzer.sh &lt;path to log file&gt;
        
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691156217671/1b64cb11-7d45-4334-ad25-ee3f721a6514.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691156228242/c977e072-6290-4e9d-a4cc-19b3a9f83238.png align="center")