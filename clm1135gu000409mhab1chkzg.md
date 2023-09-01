---
title: "MongoDB Replica Set Setup"
datePublished: Fri Sep 01 2023 20:09:10 GMT+0000 (Coordinated Universal Time)
cuid: clm1135gu000409mhab1chkzg
slug: mongodb-replica-set-setup
tags: mongodb, devops, devops-articles

---

---

## **Prerequisites:**

Before running this script, ensure you have the following prerequisites met:

1. **Linux Environment:** This script is designed for a Linux-based operating system. It's been tested on Ubuntu but should work on other Debian-based distributions.
    
2. **Root or Sudo Access:** You need root or sudo privileges to execute the installation and configuration steps.
    
3. **Internet Connection:** Make sure your server has access to the internet to download required packages and MongoDB.
    

---

## **Script Explanation:**

Now, let's break down the script into clear steps:

---

### **Step 1: Update System Packages**

```bash
sudo apt update
```

* **Purpose**: Update the list of available software packages on your system.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693598354875/0fcb1ec5-2ea1-4d5b-ba63-e40dfa783184.png align="center")
    

---

### **Step 2: Install Required Packages**

```bash
sudo apt-get install -y gnupg curl
```

* **Purpose**: Install necessary packages `gnupg` and `curl` for handling MongoDB setup.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693598382830/79c5c865-083b-4a74-b090-c30953c78631.png align="center")
    

---

### **Step 3: Add MongoDB GPG Key**

```bash
curl -fsSL https://www.mongodb.org/static/pgp/server-5.0.asc | sudo gpg --dearmor -o /usr/share/keyrings/mongodb-archive-keyring.gpg
```

* **Purpose**: Download MongoDB's GPG key and store it in a secure location.
    

---

### **Step 4: Add MongoDB Repository**

```bash
echo "deb [signed-by=/usr/share/keyrings/mongodb-archive-keyring.gpg] https://repo.mongodb.org/apt/ubuntu focal/mongodb-org/5.0 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-5.0.list
```

* **Purpose**: Add the MongoDB repository to your list of trusted software sources.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693598427155/53fb417d-6323-4b34-81c7-df775c5f2e7e.png align="center")
    

---

### **Step 5: Update System Packages Again**

```bash
sudo apt-get update
```

* **Purpose**: Update the package list with the MongoDB repository included.
    

---

### **Step 6: Install libssl1.1 Package (Dependency for MongoDB)**

```bash
wget http://archive.ubuntu.com/ubuntu/pool/main/o/openssl/libssl1.1_1.1.1f-1ubuntu2_amd64.deb
sudo dpkg -i libssl1.1_1.1.1f-1ubuntu2_amd64.deb
```

* **Purpose**: Download and install `libssl1.1`, a library MongoDB depends on.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693598445330/101b5420-0870-4905-96bd-bb00b29f4385.png align="center")
    

---

### **Step 7: Install MongoDB and Configure**

```bash
sudo apt-get install -y mongodb-org
sudo systemctl start mongod
sudo systemctl daemon-reload
sudo systemctl enable mongod
```

* **Purpose**: Install MongoDB, start its service, reload the configuration, and enable it to start automatically.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693598482847/ea89cf02-997b-43fa-9eb2-227c23b4cf9d.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693598466260/63ba183d-e75f-4b8a-b117-37c0196a7468.png align="center")
    

---

### **Step 8: Create MongoDB Configuration for Replica Set**

```bash
# ... (Configuration Details) ...
replication:
  replSetName: "rs0"
```

* **Purpose**: Create a configuration file specifying data path, port, and replication settings.
    
    ```plaintext
    # mongod.conf
    
    # for documentation of all options, see:
    #   http://docs.mongodb.org/manual/reference/configuration-options/
    
    # Where and how to store data.
    storage:
      dbPath: /var/lib/mongodb
      journal:
        enabled: true
      wiredTiger:
        engineConfig:
          cacheSizeGB: 1
    
    # where to write logging data.
    systemLog:
      destination: file
      logAppend: true
      path: /var/log/mongodb/mongod.log
    
    # network interfaces
    net:
      port: 27017
      bindIp: 127.0.0.1
    
    
    # how the process runs
    processManagement:
      timeZoneInfo: /usr/share/zoneinfo
    
    # The following lines disable JavaScript execution.
    security:
      javascriptEnabled: false
    #operationProfiling:
    
    replication:
      replSetName: "rs0"
    
    #sharding:
    
    ## Enterprise-Only Options:
    
    #auditLog:
    
    #snmp:
    ```
    

---

### **Step 9: Start MongoDB with New Configuration**

```bash
sudo mongod --config /etc/mongod.conf
```

* **Purpose**: Start MongoDB using the newly created configuration file.
    

---

### **Step 10: Restart MongoDB**

```bash
sudo systemctl restart mongod
```

* **Purpose**: Restart MongoDB to apply the changes.
    

---

### **Step 11: Start the First MongoDB Instance**

```bash
sudo mongod --dbpath "/var/lib/mongodb" --logpath "/var/lib/mongodb/log/mongod.log" --port 27017 --storageEngine=wiredTiger --wiredTigerCacheSizeGB 1 --journal --replSet rs0 --noScripting
```

* **Purpose**: Launch the initial MongoDB instance with specific settings.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693598755783/4c7ff005-f570-4c6e-8a12-9d40ba429780.png align="center")
    

---

### **Step 12: MongoDB Shell and Initialize Replica Set**

```bash
mongo --port 27017 --eval "..."
```

* **Purpose**: Use the MongoDB shell to set up the replica set configuration, add members, and an arbiter.
    

---

### **Step 13: Display Replica Set Status and Setup Completion Message**

```bash
mongo --port 27017 --eval "rs.status()"
echo "MongoDB replica set setup is complete."
```

* **Purpose**: Check and display the status of the replica set and confirm the setup's completion.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693598783232/17e00c85-3fa3-4804-8aaf-8ce3ea8b1d15.png align="center")
    

---

This script automates the setup of a MongoDB replica set, ensuring MongoDB version 5.0, specific configurations, and multiple members, including an arbiter. It also disables JavaScript execution for enhanced security.

Ensure that you meet the prerequisites and run each step sequentially. This script simplifies the process of configuring MongoDB for replica sets, making it easier to manage and maintain a MongoDB cluster.

---

Feel free to save this explanation as a PDF document for future reference.