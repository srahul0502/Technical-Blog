---
title: "Linux Package Management And Systemctl"
datePublished: Sun Jul 23 2023 14:05:01 GMT+0000 (Coordinated Universal Time)
cuid: clkfigscb000a09mz1j520659
slug: linux-package-management-and-systemctl
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1690121044915/67d5eec1-6ed8-4b1b-b980-06b14b7c5eb1.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1690121057476/f1fda8c6-28c4-4230-bc5e-23635ef1c07e.jpeg
tags: linux, devops, devops-articles, systemctl, 90daysofdevops

---

## 📦What is a package manager in Linux⁉️

* On a Linux system, a package manager is a software utility that simplifies the process of installing, upgrading, configuring, and removing software packages. It ensures that all package requirements are met, which speeds up the installation process.
    
* The package manager automatically takes care of any additional files and libraries needed for a program to work properly.
    

## 📦What is a Package in package manager

* A "package" in a package manager refers to a bundled collection of files that comprise a software program or library. This package includes all of the components and information required to install, update, or uninstall the software from your computer. These packages are used by the package manager to conduct software installation and management on your system.
    
* In simple terms , A package is usually referred to an application but it could be a GUI application, command line tool or a software library (required by other software programs). A package is essentially an archive file containing the binary executable, configuration file and sometimes information about the dependencies.
    

## 📦 Types of Package Manager

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690116869670/a674f855-0fff-41b2-a2a2-9be66e65878b.avif align="center")

* For Debian-based distributions like Debian, Ubuntu, Linux Mint, and more
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690116820897/f6595694-ebf8-4edb-9910-ff4fe6ed60bc.png align="center")
    
    * We use apt(advanced packaged tool), apt-get which uses .deb packages and manages dependencies automatically .
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690118313498/3eba7981-53e3-40a0-8018-b4444500e374.png align="center")
        
    * We can also use DPKG which is a low-level package manager used in Debian-based distributions and it is responsible for installing, unpacking, and managing individual .deb packages.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690118327522/3e225064-fcb7-4fc5-8e7b-f988ec925548.png align="center")
        
* For Red Hat-based distributions like Fedora, CentOS, RHEL (Red Hat Enterprise Linux), and more
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690116828794/65228d1e-9c9b-4557-bc97-8623f99024a3.png align="center")
    
    * We use RPM (RPM Package Manager) which is a low-level package manager used in Red Hat-based distributions and handles individual .rpm packages and their installation.
        
    * We can also use DNF (Dandified Yum) which uses .rpm packages and resolves dependencies automatically.
        

## ⚒️ Installing Tools Using Package Managers

* Let's install docker using package manager on ubuntu
    
    * For ubuntu we use apt to install tools/packages
        
    
    ```bash
    # to install docker
    sudo apt intall docker.io
    # to add the individual to the group for Docker
    sudo usermod -aG docker $USER
    # restart your computer 
    # to check for containers in a runningn state or to verify it is installed
    sudo docker ps
    ```
    
    * To Install the same on CentOS or Red Hat-based distributions
        
        * We can use yum or dnf
            
            ```bash
            sudp yum install docker.io
            # or
            sudo yum install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
            # to check the running status 
            sudo systemctl status docker
            # You can refer the link attached to know how to install it step
            # by step with out errors 
            https://docs.docker.com/engine/install/centos/
            ```
            
* To Install Jenkins on Ubuntu , we have to check for the java version and update it to the latest
    
    ```bash
    # to check the version
    java --version
    # to install the latest version
    sudo apt install openjdk-17-jre
    # to install jenkins 
    sudo apt-get install jenkins
    # to check the status 
    sudo systemctl status jenkins
    # If you want to go through the complete documentation
    https://www.jenkins.io/doc/book/installing/linux/
    ```
    
* To install jenkins on CentOS or Red Hat-based distributions
    
    ```bash
    # to install latest version of java 
    sudo yum install java-17-openjdk
    # to install jenkins 
    sudo yum install jenkins
    # to enable the service or jenkins
    sudo systemctl enable jenkins
    # to check the status 
    sudo systemctl status jenkins
    # the complete documentation is here 
    https://www.jenkins.io/doc/book/installing/linux/#red-hat-centos
    ```
    

## 🖥️ Understanding Systemclt and Systemd

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690118416770/65b2a8ea-387f-4fb6-a515-540029acbb41.png align="center")

* Systemctl :
    
    * Consider systemctl to be the "remote control" for your Linux system. Systemctl, like a remote control, allows you to manage the services and processes that run behind the scenes on your computer. These services handle critical duties such as networking, printing, and other critical processes.
        
    * It acts as an interface to interact with systemd, allowing you to start, stop, restart, enable, disable, and check the status of services.
        
        ```bash
        # to start a service let's take sshd
        sudo systemctl start sshd
        # to stop the sevice
        sudo systemctl stop sshd
        # to check the status 
        sudo systemctl status sshd
        ```
        
* Systemd:
    
    * Systemd is a system and service manager for Linux operating systems.
        
    * It is in charge of initializing the system, managing services, handling devices, and keeping user sessions active.
        
* How Systemctl and Systemd Work Together 🤔
    
    * Systemctl connects with systemd and acts as a simple tool for controlling services.
        
    * Systemd is the core programme that handles service management and other system operations.
        
* Let's check the service of docker in our system
    
    * type " sudo systemctl status docker " to check status
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690120116061/cfeca669-b959-430b-b44b-fa881cc03b23.png align="center")
        
    * It indicates the it is currently active(running).
        
* Let's check the status of jenkins and stop the service to see the difference
    
    * type " sudo systemctl status jenkins " to check the status
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690120218015/fd31457b-0b92-43ce-b59d-6b1ac04423d7.png align="center")
        
    * It indicates that it is currently in active state (running)
        
    * Let's stop the service and check the difference
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690120282056/f8589971-7ead-42e4-8960-7b26703d3afd.png align="center")
        
    * It indicates that the service is inactive(dead)
        
* There are two different commands:
    
    * systemctl status docker and service docker status
        
    * There's no much difference between them it's just that systectl status docker is used on systems with systemd , while service docker status is used on systems with SysV Init (older linux systems).
        

> I hope you all got some idea about Package managment , package , how to install them , checking status ..
> 
> Stay tuned for further updates
> 
> Happy Learning :D