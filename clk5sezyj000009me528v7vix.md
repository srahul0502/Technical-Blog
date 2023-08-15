---
title: "Linux For DevOps"
datePublished: Sun Jul 16 2023 18:45:52 GMT+0000 (Coordinated Universal Time)
cuid: clk5sezyj000009me528v7vix
slug: linux-for-devops
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1689520743196/2f32a627-157f-40a4-82d9-eec9e6f5c20e.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1689533139067/876dad50-654a-4c91-ba1f-78c29149a1f5.png
tags: devops, linux-for-beginners, linux-basics, linux-commands, 90daysofdevops

---

# 🐧Linux Fundamentals

## 🐧Introduction

* Linux, symbolized by the charming penguin 🐧, is an open-source operating system that has brought a revolutionary impact to the field of computing. In this blog post, we will dive into the captivating universe of Linux, comprehending its essence, examining various distributions, unraveling its structure, exploring its robust security measures, and investigating its extensive applications within the realm of IT.
    

## 🐧What is Linux🤔❓

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689522326429/bce9bb2b-05d5-43f7-99e2-594fce62ab66.jpeg align="center")

⌨️ Linux is an operating system, like the heart of your device, that helps it run smoothly and perform different tasks.

🔧 It's known for being powerful, versatile, and reliable, like a trusty tool in your digital toolbox.

🔓 Linux is open-source, which means its inner workings are transparent and accessible for exploration and customization.

✨ Overall, Linux provides a stable, secure, and customizable foundation for your digital experience, giving you the freedom to do more with your device.

## 🐧What is Linux Distribution⁉️

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689523280463/cb412ee8-19ee-4494-9101-20c0067c0d9f.jpeg align="center")

🐧🍊🚀 A Linux distribution, or distro for short, is a complete package of Linux that includes the Linux kernel along with various software, tools, and applications.

🐧🔴🎩 Distros often provide a user-friendly interface, making Linux more accessible to non-technical users.

🐧🎯⚙️ They come in diverse flavors, each tailored to different user needs, preferences, and objectives.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689523684607/7b568928-5a74-493e-8f51-32a6d2321f03.jpeg align="center")

## 📚 Types of Linux Distros

📗 **Debian-based Distros** (e.g., Ubuntu, Linux Mint, Debian):

* Known for stability, ease of use, and extensive software repositories.
    
* Popular among beginners and general desktop users.
    

📕 **Red Hat-based Distros** (e.g., Fedora, CentOS, Red Hat Enterprise Linux):

* Preferred by enterprise users and system administrators.
    
* Emphasize security, stability, and long-term support.
    

📘 **Arch-based Distros** (e.g., Arch Linux, Manjaro, EndeavourOS):

* Geared towards experienced users and enthusiasts.
    
* Offer cutting-edge software and a highly customizable experience.
    

## 🐧What is the Linux Architecture 🏗️❓

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689526283525/a4b605f5-4f9e-45c0-b592-dcab2b7b72b9.jpeg align="center")

🏚️ Think of Linux as a house with different layers. The bottom layer is the **<mark>hardware</mark>**, which includes the physical components like the processor, memory, and storage.

⌨️ On top of the hardware, we have the **<mark>Linux kernel</mark>**, which acts as the brain of the system. The kernel manages the hardware resources, allowing programs and applications to run smoothly.

💻 On top of the Kernel, we have the **<mark>Linux shell</mark>**, which is also known as the command-line interface (CLI), which is a text-based interface used for interacting with the operating system.

🐚 On the top of the Shell, we have **<mark>applications and utilities</mark>**, which are simple applications and tools.

## 🐧Linux File-System❗

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689533884802/5afd666e-3276-4045-a599-517d074779ad.png align="center")

* Linux organizes files and folders in a hierarchical structure like a virtual filing cabinet.
    
* The top-level directory is called the root directory and is represented by a forward slash ("/").
    
* Important directories in Linux and their functions include:
    

1. /bin: Holds essential tools and programs needed for basic system functions.
    
2. /etc: Stores configuration files for system-wide settings, network configurations, and service startup scripts.
    
3. /home: Each user has their own folder here to store personal files, documents, and settings.
    
4. /var: Contains variable data that changes frequently, such as log files and temporary files.
    
5. /usr: Holds software-related files, including programs, libraries, and shared data. /opt: Used for additional software installations not included in the default system distribution.
    
6. /root: The home folder for the system administrator (root user), separate from user-specific home directories.
    
7. /boot: Contains files necessary for system startup, including the bootloader and kernel.
    
8. /dev: Represents connected devices such as hard drives, USB devices, and terminals.
    
9. /proc: Provides information about running processes and system status.
    
10. /tmp: Used for storing temporary files that are cleared upon system restart.
    

* File permissions in Linux control who can access and modify files.
    
* Each file and folder has permissions set for the owner, group, and others.
    

## 🐧How Linux is so secure🛡️❓

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689528198908/95a1a875-a06b-4a9c-977c-ad5f7515fc28.jpeg align="center")

🔒 Linux boasts robust security features:

* **User privilege separation:** Users and system processes are isolated, limiting unauthorized access.
    
* **Permissions and access controls:** Fine-grained control over file and directory access.
    
* **Regular security updates:** Prompt identification and mitigation of vulnerabilities due to the active open-source community.
    

---

## 🐧Basic Linux Commands

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689529372870/a825d285-9039-45f5-accd-19cd8200cec2.png align="center")

<details data-node-type="hn-details-summary"><summary>ls- List directory contents</summary><div data-type="detailsContent">Lists files, directories</div></details>![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689535305462/c3d816d9-a6e8-403a-99c6-0c73da41da1e.png align="center")

<details data-node-type="hn-details-summary"><summary>cd- Change the current directory</summary><div data-type="detailsContent">cd &lt;directory&gt;</div></details>![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689535317656/d95e6cea-09d8-4fd2-87f9-6f45ffab9dfe.png align="center")

<details data-node-type="hn-details-summary"><summary>pwd- Print working directory</summary><div data-type="detailsContent">Displays the current working directory path</div></details>![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689535327251/dfc8abd3-3b82-456c-be3d-5e23a2cc956b.png align="center")

<details data-node-type="hn-details-summary"><summary>cp- Copy a file</summary><div data-type="detailsContent">cp SOURCE DEST</div></details>![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689535337251/1a33df45-8269-462e-b540-896411f260ae.png align="center")

<details data-node-type="hn-details-summary"><summary>mv- Move(rename) a file</summary><div data-type="detailsContent">mv SOURCE DEST</div></details>![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689535346476/d48fb3a3-5b87-4c20-a5f0-9e25f6b7d6b6.png align="center")

<details data-node-type="hn-details-summary"><summary>mkdir- Make a directory</summary><div data-type="detailsContent">Make DIRECTORY</div></details>![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689535362452/67bd94a5-e392-44ff-bacd-4e964dc13498.png align="center")

<details data-node-type="hn-details-summary"><summary>rm – Remove files or directories</summary><div data-type="detailsContent">Does not remove directories by default</div></details>![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689535372026/f4259cb5-8db8-4f39-bd38-963efee84cbd.png align="center")

<details data-node-type="hn-details-summary"><summary>apt-get- Advanced Packaging Tool</summary><div data-type="detailsContent">Handles the management of application packages</div></details>![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689535385331/e94f94d3-744a-4956-9aae-35a0d274994a.png align="center")

<details data-node-type="hn-details-summary"><summary>sudo su - sudo executes the command as a super user</summary><div data-type="detailsContent">su- become a super user</div></details>![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689535402658/6a2e4190-6e90-4541-aff7-83e3cce13fac.png align="center")

<details data-node-type="hn-details-summary"><summary>passwd- Change a user account password</summary><div data-type="detailsContent">passwd</div></details>![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689535416235/d94ff289-a2e5-43e4-b909-0cc7dc08d7bb.png align="center")

<details data-node-type="hn-details-summary"><summary>cat- Display the content of the file</summary><div data-type="detailsContent">cat filename</div></details>![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689535427539/c4e2e28b-a7bf-4281-9dad-5a566ed47b52.png align="center")

<details data-node-type="hn-details-summary"><summary>touch- Creates empty files(changes timestamp also)</summary><div data-type="detailsContent">touch filename</div></details>![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689535438769/d919afc1-31f2-496a-bf3b-dac1b38b8777.png align="center")

<details data-node-type="hn-details-summary"><summary>echo- displaying lines of text or string that are passed as arguments</summary><div data-type="detailsContent">echo "content"</div></details>![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689535451087/95bd2a97-2259-484a-b887-b1d0756880f6.png align="center")

<details data-node-type="hn-details-summary"><summary>whoami- allows Linux users to see the currently logged-in user</summary><div data-type="detailsContent">whoami</div></details>![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689535466625/e12f0585-fe2c-4b12-843c-80cacc2b2db5.png align="center")

<details data-node-type="hn-details-summary"><summary>history- to display the history of the commands executed by the user</summary><div data-type="detailsContent">history</div></details>![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689535477874/f384a631-1169-4ced-bb36-a922e6b373f7.png align="center")

<details data-node-type="hn-details-summary"><summary>date- displays or sets the date and time</summary><div data-type="detailsContent">date</div></details>![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689535486770/5dd5481b-2c5f-42d3-9d56-d0c3892e74d4.png align="center")

> These were some of the basic commands. Happy Learning :D