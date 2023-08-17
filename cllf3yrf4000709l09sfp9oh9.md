---
title: "Setting up Minikube and Launching Your First Cluster with Nginx"
datePublished: Thu Aug 17 2023 11:58:48 GMT+0000 (Coordinated Universal Time)
cuid: cllf3yrf4000709l09sfp9oh9
slug: setting-up-minikube-and-launching-your-first-cluster-with-nginx
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1692273452899/7e16c8ad-a8ea-434d-ba48-227f71e4b799.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1692273518405/289d4fb7-2590-4210-a70f-eb1aae64ded4.png
tags: kubernetes, devops, technical-writing-1, devops-articles, 90daysofdevops

---

## 🌟 Introduction

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692261264606/eb60a31f-7d94-424b-b96f-1b2b8a3f5281.jpeg align="center")

* Minikube is a tool that allows you to run a local Kubernetes cluster on your computer. It is a lightweight and easy-to-use tool that is ideal for developers, beginners, and applications that require specialized deployment.
    
* Minikube creates a single-node Kubernetes cluster on your computer using a virtual machine. This allows you to test and develop Kubernetes applications without having to set up a full-scale cluster.
    
* Minikube is also useful for learning about Kubernetes. It provides a simple and interactive way to experiment with Kubernetes concepts and features.
    
* Here are some of the benefits of using Minikube:
    
    * It is lightweight and easy to use.
        
    * It can be used on macOS, Linux, and Windows.
        
    * It allows you to test and develop Kubernetes applications without having to set up a full-scale cluster.
        
    * It is a great way to learn about Kubernetes.
        

## 🛠️ Prerequisites

* Make sure you have installed docker correctly and added the user to the docker group, and restart once after adding a user to the docker group.
    
* If you are using an AWS instance use t2.medium having 2-CPU because Minikube requires 2 CPUs. As we have discussed in the previous blog, there are two servers Master and Worker both utilize 1 complete CPU so we use t2.medium.
    

## 🚀 Installing Minikube

* Let's get started with installing Minikube
    
* Update the indexing of your system using `sudo apt update`
    
* Let's start with install Kubectl first , I hope you know what is kubectl refer [this](https://srdev.hashnode.dev/getting-started-with-kubernetes) and [this](https://kubernetes.io/docs/tasks/tools/install-kubectl-linux/) for Kubectl installation
    
    ```bash
    curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
    ```
    
    ```bash
    # give execute permissions and move it to the local/bin
    chmod +x ./kubectl
    sudo mv ./kubectl /usr/local/bin/kubectl
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692272297167/0f854798-505b-430e-9d95-a19b86bb356e.png align="center")
    
* Now, Install docker if you didn't, i mentioned it in the pre-requisites as well
    
    ```bash
    # updating and installing docker
    sudo apt-get update && sudo apt-get install docker.io -y
    # adding user to docker group
    sudo usermod -aG docker $USER
    ```
    
* Now we'll install Conntrack, It is used by Kubernetes to keep track of the connections between pods and services. This is necessary because Kubernetes uses a stateful networking model, where each pod has its own IP address and port.
    
    ```bash
    sudo apt install conntrack -y
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692272371880/22aa2ec9-452a-4d70-a26e-5da9751508a1.png align="center")
    
* Here come's the Minikube installation, you can refer to this [doc](https://minikube.sigs.k8s.io/docs/start/)
    
    ```bash
    # this is there in the document,this installs minikube directly in local/bin
    curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
    sudo install minikube-linux-amd64 /usr/local/bin/minikube
    # this installs the minikube,gives execute permission and move it to local/bin
    curl -Lo minikube https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64 
    && chmod +x minikube && sudo mv minikube /usr/local/bin/
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692272383999/ba33ca2f-d6f3-4db0-8ca6-2ce6c56f0ca3.png align="center")
    
* Now, we need a driver (VM or docker) to run the minikube, so we'll use docker as a driver to run the minikube
    
* For this you have to give permission to docker, we have already given while installing docker but you can also use this:
    
    ```bash
    sudo usermod -aG docker $USER & newgrp docker
    # temporarily switches your shell session to the "docker" group, allowing you to use Docker without sudo for that session only. 
    # The effect is lost when you close the terminal or start a new terminal window.
    # Better to go with 
    sudo usermod -aG docker $USER
    ```
    
* Let's start the minikube
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692265257306/26850ac0-96b5-48dc-b08b-8136b4295bf9.gif align="center")
    
    * Run `minikube start --driver=docker`
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692272415642/8d7266a4-9233-4353-bef1-7daf75e7a43d.png align="center")
        

## Let's understand the concept of **pod**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692273019923/6cf63cb3-9cbb-484e-9cad-f060e2244a49.png align="center")

* Pods are the smallest deployable units of computing that you can create and manage in Kubernetes.
    
* A Pod (as in a pod of whales or pea pod) is a group of one or more containers, with shared storage and network resources, and a specification for how to run the containers. A Pod's contents are always co-located and co-scheduled, and run in a shared context. A Pod models an application-specific "logical host": it contains one or more application containers that are relatively tightly coupled.
    
* You can refer to my previous [blog](https://srdev.hashnode.dev/getting-started-with-kubernetes) for a more detailed explanation.
    

### Let's Create our first pod on Kubernetes using Minikube

* Create a file pod. yaml and paste the below code :
    
    ```yaml
    apiVersion: v1
    kind: Pod
    metadata:
      name: nginx
    spec:
      containers:
      - name: nginx
        image: nginx:1.14.2
        ports:
        - containerPort: 8000
    ```
    
    * You can refer [this](https://kubernetes.io/docs/concepts/workloads/pods/) for the code documentation
        
    * Now to check if pod is created or not , use `kubectl get pods` and `kubectl get pods -o wide` for a detailed view.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692272502536/c4dbd6ab-cfe4-439e-a762-f762ebc8e454.png align="center")
        
    * As you can see our pod i running on IP : 10.244.0.3
        
    * Let's check it, we have to inside the Kubernetes cluster, minikube makes this really easy, just type `minikube ssh` to get inside and then use curl to get the data from the IP
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692272657701/c6c9efe0-78f9-49ce-8d69-9f2edb127fd7.png align="center")
        
    * As you can see nginx is running inside a pod ...!!
        
    * Whooaa !!
        

> I hope you can create your own pods now  
> We'll learn about deployment , auto healing and auto scaling in my upcoming blog
> 
> Stay Tuned !!
> 
> Happy Learning :D