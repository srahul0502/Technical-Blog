---
title: "Understanding Kubernetes Namespaces"
datePublished: Fri Aug 25 2023 11:39:41 GMT+0000 (Coordinated Universal Time)
cuid: cllqiszjz000q09lde7enauqy
slug: understanding-kubernetes-namespaces
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1692963460366/4bdb4c06-d1e2-4633-ba15-d692e11b3747.png
tags: kubernetes, devops, devops-articles, 90daysofdevops, 90daysofdevops-chanllenge

---

## 🕸️Introduction to Kubernetes Namespaces

### What is Kubernetes?

* Kubernetes is like a master organizer for your applications. It ensures your software runs smoothly, scales when necessary, and maintains a well-organized environment.
    

### The Importance of Namespaces

* Think of Kubernetes as a manager of a massive playground with various games. To prevent games from overlapping or interfering with one another, Kubernetes uses Namespaces.
    
* **Namespaces** are like designated areas in the playground, ensuring your soccer game doesn't disrupt the tag game next door.
    
* **Definition**: In Kubernetes, a **Namespace** is a logical, virtual cluster within a physical Kubernetes cluster. It allows you to create distinct environments, each with its own set of resources and access controls.
    

## 🕸️Kubernetes Initial (Default) Namespaces

* In Kubernetes, several initial namespaces serve specific roles. These namespaces are created by default when you set up a Kubernetes cluster. Understanding these namespaces is crucial for managing Kubernetes resources effectively.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692955677312/e00d86bc-cdc6-488e-912d-72635906126c.png align="center")
    

### **Default Namespace**

* **Purpose**: The `default` namespace is the default location for resources created without specifying a namespace. It serves as the default namespace for resource creation unless otherwise specified.
    
* **Use Cases**: It's commonly used for small-scale or early-stage projects where resource isolation isn't a top priority.
    
* **Example**: If you create a pod without specifying a namespace, it will be placed in the `default` namespace:
    

```bash
kubectl create pod my-pod
```

* ### **kube-system Namespace**
    

* **Purpose**: The `kube-system` namespace is dedicated to system-level Kubernetes resources, including those created by Kubernetes itself. It houses essential components like the Kubernetes API server, the scheduler, and the DNS server.
    
* **Use Cases**: It's designed for managing cluster-level components separately from user applications.
    

**Example**: To list all resources in the `kube-system` namespace, you can use:

```bash
kubectl get all -n kube-system
```

### **kube-public Namespace**

* **Purpose**: The `kube-public` namespace is reserved for resources accessible to all users, even those without specific RBAC permissions. It's a space for sharing cluster-wide information.
    
* **Use Cases**: It's typically used for resources like ConfigMaps that need to be globally visible.
    
* **Example**: To create a ConfigMap in the `kube-public` namespace:
    

```bash
kubectl create configmap my-configmap --namespace=kube-public
```

### **kube-node-lease Namespace**

* **Purpose**: The `kube-node-lease` namespace is a new addition, introduced in Kubernetes 1.14. It's part of the Node Heartbeat feature, where nodes periodically lease node conditions to the control plane.
    
* **Use Cases**: This namespace is primarily for internal Kubernetes use and is typically not manipulated by users or administrators.
    
* **Example**: User-initiated actions are typically not performed in this namespace.
    

### **kube-ingress Namespace**

* **Purpose**: The `kube-ingress` namespace is often used for Ingress Controllers, which manage external access to services within the cluster.
    
* **Use Cases**: It's used for managing Ingress resources that control traffic routing into the cluster.
    
* **Example**: To deploy an Ingress Controller in the `kube-ingress` namespace:
    

```bash
kubectl create deployment my-ingress-controller --namespace=kube-ingress --image=my-ingress-controller-image
```

## 🕸️Resource Management with Namespaces

* Resource management is critical in Kubernetes to ensure fair resource allocation among different applications or teams. Kubernetes allows you to define resource quotas and limits at the namespace level.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692956153244/63662e51-1c1b-407c-8165-d63f79fcc6a9.png align="center")
    

### Controlling Resources

Resource management in Kubernetes is akin to having referees oversee a game. Kubernetes uses Resource Quotas and Limits to manage resources within Namespaces.

* **Resource Quotas**: These are limits on resources, much like setting the maximum number of soccer balls your team can have. Kubernetes ensures you don't exceed these quotas.
    
* **Resource Limits**: These are akin to saying, "Each player can't use more than this much energy." It ensures that resource usage remains fair.
    

**Use Cases:**

* **Team Isolation**: If multiple teams share a Kubernetes cluster, assigning each team to a separate namespace helps prevent resource conflicts. You can set resource quotas to ensure fair allocation.
    
* **Resource Guarantees**: Critical applications can be assured a minimum level of resources within a namespace, safeguarding them from resource shortages caused by other applications.
    

**Example**: To create a ResourceQuota in a namespace:

```yaml
apiVersion: v1
kind: ResourceQuota
metadata:
  name: my-resource-quota
spec:
  hard:
    pods: "10"
    requests.cpu: "4"
    requests.memory: 4Gi
    limits.cpu: "8"
    limits.memory: 8Gi
```

In this example, we define a ResourceQuota that limits the number of pods, CPU requests, CPU limits, memory requests, and memory limits within the namespace.

## 🕸️Creating and Managing Custom Namespaces

Creating a custom namespace in Kubernetes is straightforward using the `kubectl` command:

```bash
kubectl create namespace my-team-environment
```

* This command creates a new namespace called `my-team-environment`, providing a separate playground for your team's applications.
    
* **Access Control**: Kubernetes allows you to set RBAC (Role-Based Access Control) policies at the namespace level, controlling which users or service accounts have access to resources within a specific namespace.
    
* **Resource Quotas and Limits**: Namespaces are used to set resource quotas and limits. For instance, you can define that a particular namespace should not consume more than a specified amount of CPU or memory.
    
* **Network Policies**: Network policies can be applied at the namespace level, controlling how traffic is allowed or denied between pods within the same namespace or across namespaces.
    

**let's go through the steps to create a namespace, update a deployment to use that namespace, and then apply the updated deployment.**

**Step 1: Create a Namespace**

Use the following command to create a namespace:

```bash
kubectl create namespace <namespace-name>
```

Replace `<namespace-name>` with the desired name for your namespace.

**Step 2: Update the Deployment YAML**

Assuming you have a Deployment defined in a YAML file (let's call it `deployment.yml`), you need to specify the namespace in that file. Open the `deployment.yml` file and look for the `metadata` section. Add the `namespace` field under `metadata` and set it to your chosen namespace name. Here's an example:

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: my-deployment
  namespace: <namespace-name> # Add this line with your namespace name
```

**Step 3: Apply the Updated Deployment**

Now, apply the updated deployment YAML using the following command:

```bash
kubectl apply -f deployment.yml -n <namespace-name>
```

Replace `<namespace-name>` with the same namespace name you used in the previous steps.

**Step 4: Verify the Namespace**

To verify that the namespace has been created and the deployment is running in that namespace, you can list the namespaces and check the status of your deployment:

List all namespaces:

```bash
kubectl get namespaces
```

Check the status of your deployment in the specified namespace:

```bash
kubectl get deployment -n <namespace-name>
```

You should see your deployment listed, indicating that it's running within the specified namespace.

That's it! You've successfully created a namespace, updated a deployment to use that namespace, and verified the namespace and deployment status in your Kubernetes cluster.

> I hope now you can create your own namespace
> 
> Happy Learning