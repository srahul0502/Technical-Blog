---
title: "Understanding Kubernetes Services"
datePublished: Fri Aug 25 2023 14:58:02 GMT+0000 (Coordinated Universal Time)
cuid: cllqpw2lu000309k4g694eqie
slug: understanding-kubernetes-services
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1692966535463/84ea563f-8e55-4420-a68b-c9719f6b2592.jpeg
tags: kubernetes, devops, devops-articles, 90daysofdevops, 90daysofdevops-chanllenge

---

Kubernetes Services acts as the intermediaries, ensuring your applications can communicate effectively and be accessed from the outside world. In this guide, we'll explore Kubernetes Services in simple terms, explain their significance, and demonstrate how to use them. Examples and a step-by-step demo will provide clarity for beginners.

## 🕸️Understanding Kubernetes Services

### **In Layman's Terms**:

Kubernetes Services are like the friendly traffic managers in a bustling city. They help various parts of your application connect with each other and ensure that your application's door is open for visitors from the outside.

### **In Technical Jargon**:

Kubernetes Services establishes a stable, easy-to-find address that enables different components of your application to communicate seamlessly. They also ensure your application can be reached from external sources.

## 🕸️Types of Kubernetes Services

Kubernetes offers various Service types, each with a unique role. Let's explore them using relatable examples:

### **1\. ClusterIP Service**

* **Purpose**: A ClusterIP Service acts like an internal phone system within a company. It enables different teams within your application to communicate privately, excluding external interference.
    
* **Example**: Imagine your application as a vast office space; ClusterIP ensures that the design team can interact with the development team without outsiders intruding.
    
    ```yaml
    apiVersion: v1
    kind: Service
    metadata:
      name: my-clusterip-service
    spec:
      selector:
        app: my-app
      ports:
        - protocol: TCP
          port: 80
          targetPort: 8080
    ```
    

### **2\. NodePort Service**

* **Purpose**: A NodePort Service resembles the main entrance to an apartment building. It grants external users access to specific apartments (segments of your app).
    
* **Example**: If your app were an apartment complex, NodePort would open the front door for guests to explore.
    
    ```yaml
    apiVersion: v1
    kind: Service
    metadata:
      name: my-nodeport-service
    spec:
      type: NodePort
      selector:
        app: my-app
      ports:
        - protocol: TCP
          port: 80
          targetPort: 8080
    ```
    

### **3\. LoadBalancer Service**

* **Purpose**: A LoadBalancer Service is akin to having a friendly museum guide during a crowded exhibition. It ensures that visitors (users) experience your app without overcrowding.
    
* **Example**: If your app were a popular museum, a LoadBalancer guarantees a pleasant and organized visit for all guests.
    
    ```yaml
    apiVersion: v1
    kind: Service
    metadata:
      name: my-loadbalancer-service
    spec:
      type: LoadBalancer
      selector:
        app: my-app
      ports:
        - protocol: TCP
          port: 80
          targetPort: 8080
    ```
    

### **4\. ExternalName Service**

* **Purpose**: An ExternalName Service is like a well-organized contact list on your phone. It simplifies your app's connections to external resources by using familiar names rather than complicated numerical addresses.
    
* **Example**: If your app needed to call an external delivery service, ExternalName would make it as straightforward as dialling a friend's name.
    
    ```yaml
    apiVersion: v1
    kind: Service
    metadata:
      name: my-external-service
    spec:
      type: ExternalName
      externalName: external-service.example.com
    ```
    

## 🕸️How to Create a Kubernetes Service

Creating a Kubernetes Service is as easy as following a recipe. Here's a simplified process:

**Step 1: Document Your Recipe (Service Description)**

* Similar to jotting down your favourite recipe, describe the type of Service you want (ClusterIP, NodePort, LoadBalancer, or ExternalName) and specify which part of your app it should connect to.
    

**Step 2: Hand Over Your Recipe to Kubernetes**

* Imagine you're handing your recipe to a skilled chef. Use a straightforward command to convey your Service recipe to Kubernetes. Kubernetes reads your instructions and takes care of the technical aspects.
    

**Step 3: Witness the Results**

Once Kubernetes finishes its tasks, your Service is ready to go, like a delectable dish emerging from the kitchen. Your app is now accessible and can communicate effortlessly.

## 🕸️Why Kubernetes Services Are Valuable

Kubernetes Services offer numerous advantages:

* **Seamless Communication**: They ensure different parts of your app interact effortlessly, much like employees in a well-structured office.
    
* **Global Accessibility**: With the appropriate Service type, your app becomes accessible to users worldwide, like an online store open around the clock.
    
* **Reliability**: They guarantee your app remains available, even during spikes in popularity, much like a restaurant that never runs out of seating.
    

## 🕸️Hands-On Demo: Creating a Kubernetes Service

Let's put theory into practice. In this hands-on demo, we'll create a simple Kubernetes Service together.

**Scenario**: You have a web app and want to make it accessible to the world using a NodePort Service.

**Demo Steps**:

1. Document the Service description (recipe) in a YAML file.
    
2. Utilize `kubectl` (Kubernetes command line) to apply the recipe.
    
3. Access your app using the NodePort.
    

```yaml
apiVersion: v1
kind: Service
metadata:
  name: my-web-app-service
spec:
  selector:
    app: my-web-app
  ports:
    - protocol: TCP
      port: 80
      targetPort: 8080
  type: NodePort
```

Let's break down what each part of this manifest does:

* `apiVersion` and `kind`: These lines specify that we're defining a Kubernetes Service.
    
* `metadata`: This section allows you to name your Service (`my-web-app-service` in this case).
    
* `spec`: This is where you describe the specifications for your Service:
    
    * `selector`: This is crucial. It tells Kubernetes which pods should be associated with this Service. In this example, pods with the label `app: my-web-app` will be part of this Service.
        
    * `ports`: Here, we define how traffic should be directed. This Service listens on port 80 (HTTP) and forwards it to the pods' port 8080.
        
    * `type`: This specifies the Service type. In this case, it's set to `NodePort`, which means you're creating a NodePort Service that allows external access to your app.
        

When you apply this manifest using `kubectl apply -f your-file.yaml`, Kubernetes will create the Service based on these specifications. In this example, it will create a NodePort Service named `my-web-app-service` that directs traffic to pods with the label `app: my-web-app` on port 8080.

Remember to adjust the labels, ports, and other settings to match your specific application requirements when creating your own Service manifest file.

> I hope you understood about services and now you can create your own service  
> Happy Learning :D