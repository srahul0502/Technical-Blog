---
title: "Day-04 : TWS BashBlaze Challenge 🔥"
datePublished: Thu Aug 03 2023 15:31:43 GMT+0000 (Coordinated Universal Time)
cuid: clkvben3b000a09mj27sg4rfc
slug: day-04-tws-bashblaze-challenge
tags: linux, bash, bash-script, twsbashblazechallenge, twsbashblazechallenge-trainwithshubham

---

## Monitor Process

1. **Process Selection:**
    
    * The script should accept a command-line argument to specify the target process to monitor. For example: `./monitor_process.sh <process_name>`.
        
        ```bash
        #!/bin/bash
        
        # Check if the correct number of command-line arguments is provided
        # $# is a special variable in Bash that holds the number of arguments passed to a script
        if [ $# -ne 1 ]; then
            echo "Usage: $0 <process_name>"
            exit 1
        fi
        ```
        
2. **Process Existence Check:**
    
    * Implement a function that checks if the specified process is currently running on the system.
        
    * If the process is running, print a message indicating its presence.
        
        ```bash
        # Continuous loop to monitor and restart the process
        while true
         do
            # Check if the specified process is running
            # pgrep command is used to find or signal processes based on their names
            if pgrep -x "$process_name" >/dev/null; then
                echo "Process '$process_name' is running."
                # Reset restart attempts if the process is running
                restart_attempts=0
        ```
        
3. **Restarting the Process:**
    
    * If the process is not running, implement a function that attempts to restart the process automatically.
        
    * Print a message indicating the attempt to restart the process.
        
    * Ensure the script does not enter an infinite loop while restarting the process. Limit the number of restart attempts.
        
        ```bash
        else
          # Check if restart attempts are within the limit
          if [ "$restart_attempts" -lt "$max_attempts" ]; then
          echo "Process $process_name is not running. Attempting to restart..."
                    
          # Add the command to restart the process here
          sudo systemctl restart "$process_name"
        
          # Increment the restart attempts counter
          ((restart_attempts++))  
          else
           echo "Maximum restart attempts reached. Please check the process manually."
        ```
        
4. **Automation:**
    
    * Provide instructions on how to schedule the script to run at regular intervals using a cron job or any other appropriate scheduling method.
        
        ```bash
        # To schedule the script to run at regular intervals using a cron job:
        # Open the crontab configuration using: crontab -e.
        # Add a line to specify the interval and the script path, for example, to run every 2 minutes:
        */2 * * * * /path/to/monitor_process.sh <process_name>
        ```
        
5. **Documentation:**
    
    * Include clear and concise comments in the script to explain its logic and functionality.
        
    * Write a separate document describing the purpose of the script, how to use it, and any specific considerations.
        

**Bonus:**

* Implement a notification mechanism (e.g., email, Slack message) to alert administrators if the process requires manual intervention after a certain number of restart attempts.
    
    ```bash
     # Send notification if restart attempts reach the threshold
     if [ "$restart_attempts" -ge "$notification_threshold" ]
      then
         echo "Sending email notification to administrators..."
         subject="Process Monitoring Alert"
         message="Process '$process_name' failed to restart after $max_attempts attempts."           
        # Send email using the mail command
        echo -e "$message" | mail -s "$subject" <user@gmail.com>
    ```
    
* For the above mechanism to work u need to install mailutils and postfix using `sudo apt install mailutils` and do the necessary configuration .
    
* You can refer this [tutorial](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-postfix-as-a-send-only-smtp-server-on-ubuntu-16-04) for step by step process.
    

### Final Solution :

```bash
#!/bin/bash

# Check if the correct number of command-line arguments is provided
if [ $# -ne 1 ]; then
    echo "Usage: $0 <process_name>"
    exit 1
fi

# Get the process name from the command-line argument
process_name="$1"

# Set the maximum number of restart attempts and the notification threshold
max_attempts=3
notification_threshold=2

# Initialize the counter for restart attempts
restart_attempts=0

# Continuous loop to monitor and restart the process
while true
 do
    # Check if the specified process is running
    if pgrep -x "$process_name" >/dev/null; then
        echo "Process '$process_name' is running."
        restart_attempts=0  # Reset restart attempts if the process is running
    else
        # Check if restart attempts are within the limit
        if [ "$restart_attempts" -lt "$max_attempts" ]; then
            echo "Process $process_name is not running. Attempting to restart..."
            
            # Add the command to restart the process here
            sudo systemctl restart "$process_name"

            # Increment the restart attempts counter
            ((restart_attempts++))  
        else
            echo "Maximum restart attempts reached. Please check the process manually."
            
            # Send notification if restart attempts reach the threshold
            if [ "$restart_attempts" -ge "$notification_threshold" ]; then
                echo "Sending email notification to administrators..."
                subject="Process Monitoring Alert"
                message="Process '$process_name' failed to restart after $max_attempts attempts."
                
                # Send email using the mail command
                echo -e "$message" | mail -s "$subject" srahul.sr0502@gmail.com
            fi
            # Exit the script with an error status
            exit 1  
        fi
    fi
    # Adjust the interval as needed before checking agains
    sleep 5  # Adjust the interval as needed before checking again
done
```

* Save this script as monitor\_process.sh and give necessary permission :
    
    * chmod +x monitor\_process.sh
        
    * execute the script by ./monitor\_process.sh &lt;process name&gt;
        

# Monitoring Metrics Script with Sleep Mechanism

### Task 1: Implementing Basic Metrics Monitoring

Write a Bash script that monitors the CPU usage, memory usage, and disk space usage of the system. The script should display these metrics in a clear and organized manner, allowing users to interpret the data easily. The script should use the top, free, and df commands to fetch the metrics.

```bash
 case "$choice" in
        1)
            # Display system metrics
            clear
            echo "System Metrics:"
            echo "----------------"
            
            # Fetch CPU usage and format
            cpu_usage=$(top -bn 1 | awk '/Cpu/ {print $2}')
            cpu_usage="${cpu_usage}%"
            
            # Fetch memory usage and format
            mem_usage=$(free -h | awk '/Mem:/ {print $3}')
            
            # Fetch disk space usage and format
            disk_usage=$(df -h / | awk '/\// {print $5}')
            
            echo "CPU Usage: $cpu_usage   Mem Usage: $mem_usage   Disk Space: $disk_usage"
            ;;
```

### Task 2: User-Friendly Interface

Enhance the script by providing a user-friendly interface that allows users to interact with the script through the terminal. Display a simple menu with options to view the metrics and an option to exit the script.

```bash

#!/bin/bash

# Continuous loop for the menu
while true; do
    clear
    echo "Monitoring Script Menu:"
    echo "1. Display System Metrics"
    echo "2. Monitor a Specific Service"
    echo "3. Exit"
    read -p "Enter your choice: " choice
```

### Task 3: Continuous Monitoring with Sleep

Introduce a loop in the script to allow continuous monitoring until the user chooses to exit. After displaying the metrics, add a "sleep" mechanism to pause the monitoring for a specified interval before displaying the metrics again. Allow the user to specify the sleep interval.

```bash
 # Allow the user to specify the sleep interval
    read -p "Enter sleep interval in seconds (0 to exit): " sleep_interval

    # Exit the loop if sleep interval is 0
    if [ "$sleep_interval" -eq 0 ]; then
        echo "Exiting the script."
        exit 0
    fi

    # Sleep for the specified interval
    sleep "$sleep_interval"
```

### Task 4: Monitoring a Specific Service (e.g., Nginx)

Extend the script to monitor a specific service like Nginx. Check if the service is running and display its status. If it is not running, provide an option for the user to start the service. Use the systemctl or appropriate command to check and control the service.

```bash
# Monitor a specific service
            clear
            read -p "Enter the name of the service to monitor: " service_name
            if systemctl is-active "$service_name" >/dev/null
	     then
                echo "$service_name is running."
            else
                echo "$service_name is not running."
                read -p "Do you want to start $service_name? (y/n): " start_choice
                if [ "$start_choice" = "y" ]
                 then
                    sudo systemctl start "$service_name"
                    echo "Starting $service_name..."
                fi
            fi
            ;;
```

### Task 5: Allow User to Choose a Different Service

Modify the script to give the user the option to monitor a different service of their choice. Prompt the user to enter the name of the service they want to monitor, and display its status accordingly.

### Task 6: Error Handling

Implement error handling in the script to handle scenarios where commands fail or inputs are invalid. Display meaningful error messages to guide users on what went wrong and how to fix it.

```bash
# Handle invalid input
echo "Invalid choice. Please select a valid option."
;;
```

### Task 7: Documentation

Add comments within the script to explain the purpose of each function, variable, and section of the code. Provide a clear and concise README file explaining how to use the script, the available options, and the purpose of the script.

## Final Solution :

```bash
#!/bin/bash

# Continuous loop for the menu
while true
 do
    clear
    echo "Monitoring Script Menu:"
    echo "1. Display System Metrics"
    echo "2. Monitor a Specific Service"
    echo "3. Exit"
    read -p "Enter your choice: " choice

    case "$choice" in
        1)
            # Display system metrics
            clear
            echo "System Metrics:"
            echo "----------------"
            
            # Fetch CPU usage and format
            cpu_usage=$(top -bn 1 | awk '/Cpu/ {print $2}')
            cpu_usage="${cpu_usage}%"
            
            # Fetch memory usage and format
            mem_usage=$(free -h | awk '/Mem:/ {print $3}')
            
            # Fetch disk space usage and format
            disk_usage=$(df -h / | awk '/\// {print $5}')
            
            echo "CPU Usage: $cpu_usage   Mem Usage: $mem_usage   Disk Space: $disk_usage"
            ;;
    
        2)
            # Monitor a specific service
            clear
            read -p "Enter the name of the service to monitor: " service_name
            if systemctl is-active "$service_name" >/dev/null
	     then
                echo "$service_name is running."
            else
                echo "$service_name is not running."
                read -p "Do you want to start $service_name? (y/n): " start_choice
                if [ "$start_choice" = "y" ]
                 then
                    sudo systemctl start "$service_name"
                    echo "Starting $service_name..."
                fi
            fi
            ;;
        3)
            # Exit the script
            echo "Exiting the script."
            exit 0
            ;;
        *)
            # Handle invalid input
            echo "Invalid choice. Please select a valid option."
            ;;
    esac

    # Allow the user to specify the sleep interval
    read -p "Enter sleep interval in seconds (0 to exit): " sleep_interval

    # Exit the loop if sleep interval is 0
    if [ "$sleep_interval" -eq 0 ]; then
        echo "Exiting the script."
        exit 0
    fi

    # Sleep for the specified interval
    sleep "$sleep_interval"

    read -p "Press Enter to continue..."
done
```

* Save the script as monitor\_metrics.sh and give the permissions required:
    
    * chmod +x monitor\_metrics.sh
        
    * Execute it ./monitor\_metrics.sh