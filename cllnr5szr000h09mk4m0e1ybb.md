---
title: "Mastering Kubernetes ReplicaSets: Scaling and Ensuring High Availability in Your Container Orchestration""
datePublished: Wed Aug 23 2023 13:10:17 GMT+0000 (Coordinated Universal Time)
cuid: cllnr5szr000h09mk4m0e1ybb
slug: mastering-kubernetes-replicasets-scaling-and-ensuring-high-availability-in-your-container-orchestration
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1692796034415/e09af59c-655e-4bec-869b-a3017b58c919.png
tags: kubernetes, devops, devops-articles, 90daysofdevops, 90daysofdevops-chanllenge

---

## 🕸️ Introduction

* The container orchestration platform Kubernetes has transformed the way we deploy, manage, and scale applications. The ReplicaSet is a fundamental building block of Kubernetes. In this blog post, we'll debunk ReplicaSets by explaining what they are, how they work, and why they're so important for ensuring high availability and scalability in your Kubernetes deployments.
    

## 🕸️ Understanding ReplicaSets

* A ReplicaSet in Kubernetes is a declarative approach to ensuring that a specified number of identical pods are running at any given time. It acts as a controller, continuously monitoring the state of your pods and making adjustments to maintain the desired number.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692791228560/e123649c-4e89-4348-a2d8-1c981a9c6499.png align="center")
    

## 🕸️ How ReplicaSets Work

Imagine you have a web application that serves traffic. You want to ensure that, regardless of failures or increased traffic, there are always three identical instances of your application running. This is where a <mark>ReplicaSet</mark> comes in.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692791486769/ed6f34b2-273a-4d36-8195-8fdadd1e578b.png align="center")

* **Pod Template:** You define a template for your pods, specifying the container image, resources, and other configurations.
    
* **Replica Count:** You specify the desired number of replicas, in this case, three.
    
* **Controller:** The ReplicaSet controller constantly observes the state of your pods. If it detects fewer than three pods, it creates new ones based on the defined template. If there are more than three, it terminates the excess pods.
    
* **Desired State:** The ReplicaSet maintains a desired state, ensuring that the actual state (the number of pods running) matches it. If a pod crashes or is terminated, a new one is automatically created to replace it.
    
* **Ensuring High Availability**
    
    One of the key roles of ReplicaSets is ensuring high availability. Let's consider an example:
    
    * Imagine one of your pods becomes unhealthy due to a node failure or an application crash. The ReplicaSet controller detects this and automatically replaces the failed pod with a new one. This rapid response to failures ensures that your application remains available to users, even in the face of hardware or software issues.
        
* **Scaling Applications**
    
    * Scalability is another critical aspect of ReplicaSets. Suppose your application suddenly experiences a surge in traffic due to a viral post or a marketing campaign. You can easily scale up your application by updating the replica count in the ReplicaSet from 3 to, say, 5. The controller will take care of launching the additional pods, distributing the load, and maintaining the desired state.
        

## 🕸️ Understanding With Example

* They are very similar to other Kubernetes resources in that you must specify the apiVersion, kind, metadata, and spec, which is the first thing to keep in mind.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692795883895/f7739217-1cb9-41a6-9299-6784eb87c860.png align="center")
    

Here's an [example](https://kubernetes.io/docs/concepts/workloads/controllers/replicaset/) of how ReplicaSet Manifest file looks like

```yaml
apiVersion: apps/v1
kind: ReplicaSet
metadata:
  name: frontend
  labels:
    app: guestbook
    tier: frontend
spec:
  # modify replicas according to your case
  replicas: 3
  selector:
    matchLabels:
      tier: frontend
  template:
    metadata:
      labels:
        tier: frontend
    spec:
      containers:
      - name: php-redis
        image: gcr.io/google_samples/gb-frontend:v3
```

* First of all, this ReplicaSet is simulating a situation in which you have three pods running a frontend demo application in your environment. Many of the fields will be familiar to you if you've ever created a manifest file for a straightforward pod or deployment. Let's focus on the first section in more detail:
    
    ```yaml
    apiVersion: apps/v1
    kind: ReplicaSet
    metadata:
      name: frontend
      labels:
        app: guestbook
        tier: frontend
    ```
    
* The first two fields are straightforward and constant, so they never change. Kubernetes is only told what it can work with by the apiVersion and kind parameters, which should never be different. You are defining the name and labels of the metadata as you descend the hierarchy. You'll be able to keep a better eye on the resources you have available to you in your environment if you do this.
    
* Moving on to the next section 'spec' field :
    
    ```yaml
    spec:
      # modify replicas according to your case
      replicas: 3
      selector:
        matchLabels:
          tier: frontend
    ```
    
* This field's <mark>replicas</mark> value is set to 3 ,indicating that the desired state is to have three identical pods managed by this resource.
    
* The <mark>selector</mark> field is then used to determine which pods should be controlled by the resource. This is done with the help of a label selector defined in the <mark>matchLabels</mark> section. In this case, the label selector specifies that this resource should manage pods with the label tier: frontend.
    
* Now we have to define the actual template of the pod :
    
    ```yaml
      template:
        metadata:
          labels:
            tier: frontend
        spec:
          containers:
          - name: php-redis
            image: gcr.io/google_samples/gb-frontend:v3
    ```
    
* This is similar to defining any other pod. First, you specify the metadata field, which is labelled tier: frontend in this case. As you can see, we specified that the ReplicaSet would look for this when determining which pods it needed to own. So double-check that it corresponds to what you wrote earlier in the manifest.
    
* You can apply this by running
    
    `kubectl apply -f` [`https://kubernetes.io/examples/controllers/frontend.yaml`](https://kubernetes.io/examples/controllers/frontend.yaml)
    
* Run kubectl get rs to see the deployed replicaset `kubectl get rs`
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692795295900/a739de57-6642-498f-a341-d60bdbb57fdb.png align="center")
    

## 🕸️Simple Difference Between ReplicaSet and Deployment

* **ReplicaSet:** Consider a ReplicaSet as a fundamental worker that guarantees a predetermined number of identical workers (pods) are constantly active. The situation is analogous to having a manager order "We need three workers doing this task at all times." In order to keep three employees working, the manager promptly replaces any absent or ill employees.
    
* **Deployment:** Now, a Deployment is like an astute manager who not only says, "We need three workers," but also understands how to seamlessly switch between various sets of workers. Imagine that you want to upgrade the various uniforms (application versions) that your employees are currently sporting. When you change uniforms (update your app), the deployment manager can make sure that work doesn't stop.
    
* Deployments are typically recommended for most use cases due to their <mark>higher-level abstractions, rolling update capabilities, and support for scaling and rollbacks</mark>. ReplicaSets are more suitable when you need fine-grained control over pod scaling and updates or when working with other controllers like StatefulSets, DaemonSets, or PetSets.
    

> A ReplicaSet is good for keeping a fixed number of workers (pods) on the job, while a Deployment is excellent at managing updates and changes to those workers without causing downtime.
> 
> You can mention the replica in the deployment manifest file itself !

> I hope now you can create your replicaset manifest file or use it in the deployment manifest file !!
> 
>   
> Happy Learning :D