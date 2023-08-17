---
title: "Launching Kubernetes Cluster with Deployment"
datePublished: Thu Aug 17 2023 16:35:17 GMT+0000 (Coordinated Universal Time)
cuid: cllfdubvm000409l4bgwoh73k
slug: launching-kubernetes-cluster-with-deployment
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1692289970971/2bd2a7ad-71da-4a45-bc9b-8a73512e3598.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1692290074060/c1c99094-94cf-4977-996e-5a7db4e3e342.png
tags: deployment, kubernetes, devops, devops-articles, 90daysofdevops

---

## What is Deployment in k8s⁉️

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692286116150/a919a02c-e7e0-4b6c-93c2-b7f963e43e8b.png align="center")

* A Deployment provides declarative updates for Pods and ReplicaSets.
    
* A Kubernetes deployment provides a declarative way to define and manage the desired state of your application, making it easier to handle updates and changes without manual intervention
    
* Kubernetes deployments offer more than just managing the deployment of containerized applications; they also provide features like auto-scaling and auto-healing to enhance the overall reliability and performance of your applications.
    
    * **Auto-Scaling:** When lots of people start using your app, Kubernetes can automatically create more copies of it to handle the extra traffic. This helps your app stay fast and responsive.
        
    * **Auto-Healing:** Sometimes parts of your app might stop working. Kubernetes notices this and replaces the broken parts with new ones automatically, so your app keeps running smoothly without you having to fix things manually.
        

## 🔑Key Concepts Of Kubernetes Deployment:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692286092236/38681f87-b69f-4a5b-8eb7-644b3f17bc46.jpeg align="center")

1. **Pods:** Think of pods as tiny packages for your apps. They can hold one or more containers. All containers in a pod share things like the network and storage. Pods are like buddies that work closely together.
    
2. **ReplicaSets:** ReplicaSets make sure you always have the right number of pod copies running. They're like guardians that watch over your app to keep it available and handle more users. Handling ReplicaSets can get a bit tricky.
    
3. **Deployments:** Imagine Deployments as managers for ReplicaSets. They let you easily say how your app should look and work. You can say how many copies (replicas) you want, what they should look like, and even how updates should happen.
    
    * **Scaling:** With Deployments, you can make your app bigger or smaller by changing the number of copies.
        
    * **Rolling Updates:** If you want to change your app without causing downtime, Deployments help by slowly putting in new copies and taking out old ones.
        
    * **Rollbacks:** If something goes wrong with an update, you can go back to the way things were before.
        
4. **Updating Strategies:**
    
    * **Rolling Update:** When you update, this method switches out old containers for new ones bit by bit. It's like changing clothes without anyone noticing.
        
    * **Recreate:** This way involves changing everything at once by getting rid of old containers and bringing in new ones. It's like closing your shop for a short while to put up new items.
        
5. **Health Checks:** Kubernetes keeps an eye on your containers. It checks if they're ready to work (readiness) and if they're still doing their job (liveness). It's like a doctor making sure everyone's healthy and active.
    

## 🛠️Creating a Deployment

* Let's start with cloning the repo using `git clone <repo url>`, build the image and push it to the docker hub, we are <mark>using the docker hub as a centralized registry so that it be accessed by Kubernetes from anywhere</mark>,we can use other centralized registries as well.
    
* Use `docker build -t todoapp:v1 .` to build the image with tag todoapp:v1
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692286898537/8affd30c-12e0-4492-9aa0-1d848badc79c.png align="center")
    
* Let's delete the pod and check once
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692288045134/ac7ae332-16fa-4aaf-9883-d7e65ba672a6.png align="center")
    
* As you can see, once you delete it it's completely gone, now we have learnt the concept of deployment, auto-healing, and auto-scaling, let's implement it and test it.
    
* Now let's create a pod for the same, create a pod. yaml file and paste the below
    
    ```yaml
    apiVersion: v1
    kind: Pod
    metadata:
      name: todo-pod
    spec:
      containers:
      - name: todo-app
        image: srahul0502/todoapp:v1
        ports:
        - containerPort: 8000
    ```
    
* Run the above using `kubectl apply -f pod.yaml` and check if it is created or not
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692287354306/117b8890-5581-45e1-975a-cbf1c0edc6a7.png align="center")
    

* Let's create a deployment for the todo app just like we did for nginx in [previous blog](https://srdev.hashnode.dev/setting-up-minikube-and-launching-your-first-cluster-with-nginx)
    
    ```yaml
    apiVersion: apps/v1
    kind: Deployment
    metadata:
      name: todo-deployment
      labels:
        app: todo-app
    spec:
      replicas: 3
      selector:
        matchLabels:
          app: todo-app
      template:
        metadata:
          labels:
            app: todo-app
        spec:
          containers:
          - name: todo-app
            image: srahul0502/todoapp:v1
            ports:
            - containerPort: 8000
    ```
    
* Let's break down the above code :
    
    * **Deployment Info:**
        
        * `apiVersion` and `kind` tell Kubernetes that this is a Deployment.
            
        * `metadata` includes the name "todo-deployment" and labels to identify the app as "todo-app".
            
    * **Specifying Replica Count:**
        
        * `spec.replicas` says we want 3 copies (replicas) of our app running.
            
    * **Selecting Pods:**
        
        * `spec.selector` helps the ReplicaSet know which Pods to manage.
            
        * `matchLabels` says to find Pods with the label "app: todo-app".
            
    * **Pod Template:**
        
        * `spec.template` defines how the Pods look.
            
        * `metadata.labels` sets the label "app: todo-app" for the Pods.
            
        * `spec.containers` lists what runs inside each Pod.
            
    * **Container Details:**
        
        * `name` is "todo-app" for the container.
            
        * `image` specifies the container image to use ("srahul0502/todoapp:v1").
            
        * `ports` tell's Kubernetes that the app inside the container listens on port 8000.
            
    * This whole setup means you want to deploy an app called "todo-app" using three replicas. The app runs in containers based on the "srahul0502/todoapp:v1" image, and each container listens on port 8000. The labels and selectors make sure everything is organized correctly so that Kubernetes can manage and scale your app.
        
* Save the file as deployment.yaml and execute it by running kubectl apply -f deployment.yaml
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692287596606/00cc2d66-e461-4dc1-8033-bef69ba42de0.png align="center")
    
* We have given replica as 3 so it generated 3 copies of the pod.
    
* If we give replica as 1 in the above yaml file , it will run only 1 pod
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692287792269/eaa49b0f-59d3-4bd4-b442-346833104004.png align="center")
    
* Let's delete the pod and check :
    
    * Use kubectl delete &lt;name&gt;
        
    * And check if it auto-heals or not
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692287851512/49fdda88-6278-4717-a8f1-d026812e67d3.png align="center")
        
    * As soon as it get's to know that the app/pod is about to go down it deployes the other app/pod before the other pod get's down or crashes completely
        

> I hope now you can create your own pods and launch them using kubernetes deployment
> 
> Stay tuned !!
> 
> Happy Learning :D