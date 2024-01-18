---
title: "GitOps Unveiled: Journey into the Enchanted Realm of Simplicity"
datePublished: Thu Jan 18 2024 09:44:33 GMT+0000 (Coordinated Universal Time)
cuid: clrj0zb8f000o09ib0s8k5msm
slug: gitops-unveiled-journey-into-the-enchanted-realm-of-simplicity
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1705570145455/f1b4b0aa-88ea-430a-9efa-642387d0277f.webp
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1705570298969/29a89d3d-5b24-4573-bc9d-695f3619c4c8.webp
tags: github, devops, gitops, devops-articles, 90daysofdevops, trainwithshubham

---

# **ℹ️What is GitOps?**

![GitOps](https://codefresh.io/wp-content/uploads/2023/06/GitOps_Graphic-1024x363.png align="left")

GitOps is like a wizard that uses Git repositories as a magical spellbook for managing infrastructure. It turns code submissions into a journey through Continuous Integration (CI) and Continuous Delivery (CD), where security, infrastructure, and application rules are checked and applied. Every change isn't just noted; it's saved in a version history, offering the ability to undo changes if needed.

![GitOps Model Practices](https://imgs.search.brave.com/fadYthHOWxEYigW3Wy0j6kXlLlYgLH8SyeU6yRkAp1Q/rs:fit:500:0:0/g:ce/aHR0cHM6Ly9jb2Rl/ZnJlc2guaW8vd3At/Y29udGVudC91cGxv/YWRzLzIwMjMvMDYv/R2l0T3BzLU1vZGVs/LVByYWN0aWNlcy5w/bmc align="center")

### **🕸️GitOps Unveils:**

* A simple and reliable workflow for building applications.
    
* Increased security by setting rules for applications upfront.
    
* Improved reliability with Git acting as a central hub.
    
* Consistency across different computing environments.
    

Various tools work together to create the GitOps framework—Git repositories, Kubernetes, CI/CD tools, and configuration management tools.

# **ℹ️**How It Was Before GitOps

In the pre-GitOps era, developers faced challenges like manual interventions, a lack of transparency, and inconsistencies across environments. It was like orchestrating a grand symphony without a conductor.

Examples:

* Manual Intervention: Updates required hands-on interventions, leading to increased error risks.
    
* Lack of Transparency: Tracking changes was challenging, creating uncertainty about who, what, and when.
    
* Inconsistency Across Environments: Different environments often ended up out of sync, causing headaches for developers.
    

## 🕸️GitOps Unveiled: From Principles to Practical Magic

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1705569420916/84de1480-7aea-4291-978f-0fd1a8c6a07d.webp align="center")

### 🕸️Understanding the Essence of GitOps

In the mystical realm of software development, the fortification of GitOps stands as an impervious fortress against the chaotic storms of coding seas. Let's embark on a journey, exploring the three pillars of GitOps magic that transform development landscapes.

### **1\. Immutable Coding Domain for Developers:**

**Before GitOps:** In the turbulent coding seas, changes were like ships lost without a compass. Alterations were prone to getting tangled in the chaotic waves of updates.

**With GitOps:** Developers, armed with Git, ensure the sanctity of their changes. Git becomes an unyielding fortress, preserving every commit as an indelible mark in history. Imagine a developer, Alice, commits her code changes:

```bash
git commit -m "Feature: Enchanted Spell Casting"
git push origin main
```

These changes now stand as immovable pillars in the coding fortress, unaltered and eternally preserved.

### 2\. Git as the Supreme Arbiter:

**Before GitOps:** Changes were made haphazardly, leading to inconsistencies and chaos in the digital landscape. The lack of a central authority left the city vulnerable to erratic alterations.

**With GitOps:** Git takes its role as the single source of truth seriously. Every change is verified and documented, ensuring the digital landscape mirrors the desired state. Consider a scenario where multiple developers attempt to modify a critical configuration file:

```bash
# Developer 1
git checkout -b feature-update
# Make changes
git commit -m "Updated Configuration"
git push origin feature-update

# Developer 2
git pull origin main
# Conflicting changes arise
# Git prompts resolution before proceeding
```

Git acts as the arbiter, ensuring conflicts are resolved before changes are accepted, preventing chaos in the digital city.

### 3\. Guardianship Against Unintended Changes:

**Before GitOps:** The tech city is vulnerable to unintended alterations with no clear oversight. Changes happen silently, like whispers in the wind.

**With GitOps:** Git becomes the impervious shield against unintended changes. The audit trail it provides acts as a vigilant guardian, revealing every move made within its sacred walls. Consider an inadvertent change made by a developer, Bob:

```bash
# Bob unintentionally makes changes
git commit -m "Oops! Unintended Alteration"
git push origin main
```

GitOps, acting as the vigilant guardian, reveals Bob's unintentional alteration, preserving the sanctity of the digital city.

### 🕸️GitOps Enchantment: Spells Unveiled

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1705569559269/d99ad189-5851-41f8-b4d8-6284d09755ca.webp align="center")

### **1\. Declarative Configuration: Simplifying the Spellbook**

**Before GitOps:** In the ancient coding scrolls, developers labored over intricate scripts and followed convoluted rituals.

**With GitOps:** Behold the enchantment of a simple "to-do list" in code! Imagine a Kubernetes manifest residing in a Git repository:

```bash
apiVersion: apps/v1
kind: Deployment
metadata:
  name: my-app
spec:
  replicas: 3
  template:
    metadata:
      labels:
        app: my-app
    spec:
      containers:
      - name: my-app-container
        image: my-app:latest
```

This wizardry replaces the need for complex scripts, making the desired system state crystal clear.

### **2\. Continuous Delivery: ArgoCD, the Deployment Mage**

**Before GitOps:** Deployments were akin to manual wand-waving, prone to human errors and missteps.

**With GitOps:** Enter ArgoCD, the deployment mage! Changes in the sacred Git repository trigger automatic updates, seamlessly aligning your system with the desired state:

```bash
argocd app create my-app \
  --repo https://github.com/my-org/my-repo.git \
  --path path/to/app \
  --dest-server https://kubernetes.default.svc \
  --dest-namespace my-namespace
```

With ArgoCD's magical touch, manual deployments fade away, replaced by automated wonders that mirror the coded intentions.

# **ℹ️Why GitOps?**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1705569710914/5cce70c3-b6bf-4cee-a9db-dfbca3bbc0fe.png align="center")

GitOps doesn't just promise; it delivers the DevOps dream. Organizations embracing DevOps witness incredible boosts in innovation and stability. GitOps, like a seasoned alchemist, takes these philosophies and transforms them into tangible results.

* Developers code at their pace without waiting, as changes via Git become the norm.
    
* Ops teams gain visibility, traceability, and quick issue reproduction, enhancing overall security.
    
* A detailed audit trail reduces the risk of unwanted changes, making organizations agile in responding to business changes.
    

# **ℹ️How to Get Started with GitOps**

GitOps isn't limited to Kubernetes; it's a versatile approach that can be applied to different infrastructures and deployment methods. Whether you're navigating the Kubernetes universe or traditional IT landscapes, GitOps adapts to your needs.

* Manage infrastructure declaratively; GitOps often works well with Kubernetes and cloud-native development.
    
* Ansible, a powerful tool, can be used alongside GitOps to manage applications across different environments.
    
* GitOps handles development pipelines, application code, configuration management, Kubernetes cluster setup, and deployments on Kubernetes or container registries.
    

# **ℹ️**GitOps Workflow:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1705569602652/06d881cd-10be-4a0b-a998-d8f709f805c3.webp align="center")

### 1\. Infrastructure as Code (IaC):

Declare your infrastructure and application configurations using Infrastructure as Code (IaC). This involves creating Kubernetes manifests (YAML files) to define resources like deployments, services, and configurations.

### 2\. Git Repository:

Establish a Git repository (e.g., on GitHub) to store your IaC files. This repository becomes the single source of truth for your application and infrastructure.

### 3\. Version Control:

Use Git's version control to track changes. Each modification, addition, or deletion is captured in a commit, creating a detailed history of your configurations.

### 4\. Pull Request (Optional):

For collaboration, developers may use pull requests. This allows proposed changes to be reviewed and ensures alignment with project standards before merging into the main branch.

### 5\. Automated CI/CD Pipelines:

Set up Continuous Integration (CI) and Continuous Delivery (CD) pipelines that automatically trigger when changes are pushed to the Git repository.

### 6\. Artifact Generation:

CI pipelines build and test the IaC, generating deployable artifacts. For Kubernetes, this could include container images, Helm charts, or other deployment artifacts.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1705568129153/c0a231d2-7893-4301-ad0b-baff660c551f.jpeg align="center")

### 7\. Git Repository Acts as the Source of Truth:

The Git repository reflects and actively manages the desired state of your infrastructure and application. It serves as a versioned, auditable source of truth for your project.

### 8\. Deployment Automation:

Deployments are automated based on changes in the Git repository. Tools like ArgoCD or Flux continuously monitor the repository and automatically apply changes to the target Kubernetes cluster, ensuring the desired state is consistently and seamlessly managed.

## Example: Deploying a Microservices Application on Kubernetes

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1705569358141/ba397f42-a7c8-455f-88e5-6dc5a5096819.png align="center")

**1\. Git Repository:**

* Create a Git repository to store Kubernetes manifests and related configuration files.
    

**2\. Develop New Feature:**

* A developer adds a new feature by modifying Kubernetes deployment files in the Git repository.
    

**3\. Push Changes to Git:**

* The developer pushes the changes to the Git repository.
    

**4\. CI/CD Pipeline Triggered:**

* The CI/CD pipeline is automatically triggered by the Git push.
    

**5\. Build and Test:**

* The pipeline builds container images, runs tests, and generates deployment artifacts.
    

**6\. Artifact Versioning:**

* Artifacts are versioned and stored in the Git repository, reflecting and managing the desired state.
    

**7\. Git Repository Updated:**

* The Git repository is updated with the new commit, actively managing the desired state.
    

**8\. Deployment Automation:**

* ArgoCD detects the Git repository change and automatically deploys the new version to the Kubernetes cluster, ensuring the continuous and seamless management of the desired state.
    

**9\. Rollback (Optional):**

* If issues arise, GitOps allows for easy rollback by reverting to a previous commit in the Git repository, ensuring the desired state is restored swiftly.
    

# **ℹ️**Benefits of the GitOps Transformation

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1705568222274/e49ca2b0-3079-4896-9cae-ed247402a0f4.webp align="center")

### **1\. Collaboration and Transparency: The Illumination**

**Before GitOps:** Collaboration was a labyrinth through different tools and channels. Navigating through various platforms for updates and changes resembled a complex puzzle.

**With GitOps:** Changes are unveiled in a grand spectacle, transparent, auditable, and subject to team review—all in one place, an illumination of collaboration. Picture a well-lit stage where every modification is showcased, fostering a collaborative environment that is both transparent and efficient.

### **2\. Consistent Environments: The Harmony**

**Before GitOps:** Maintaining harmony across different environments was a significant challenge. Each realm, be it development, testing, or production, played its own tune, often leading to a cacophony of inconsistencies.

**With GitOps:** GitOps ensures that your development, testing, and production realms resonate with the same melody, reducing the discord of configuration drift. Imagine an orchestra playing in perfect harmony, where each environment follows the same score, creating a symphony of consistency.

### **3\. Automated Rollbacks: The Resurrection**

**Before GitOps:** Reverting to a previous state required manual incantations. It was like navigating through a maze of commands to bring the system back to life after errors.

**With GitOps:** Automated rollbacks resurrect your system by reverting to the last known good state in Git, a magical resurrection after errors. Visualize a wizard's wand effortlessly undoing any missteps, ensuring a swift recovery to a stable and reliable state.

## Additional Advantages:

### Security 🔒

GitOps fortifies your systems with enhanced security measures, ensuring that your digital citadel remains impervious to unwanted intrusions and vulnerabilities.

### Faster Deployment or Faster Time to Market ⚡

GitOps accelerates the deployment process, reducing time-to-market. Your innovations swiftly materialize, gaining a competitive edge in the dynamic landscape of technology.

### Version Control 📝

Embrace the power of version control in GitOps, where every modification is meticulously documented. Navigate through the historical timeline, ensuring a clear understanding of changes and facilitating seamless collaboration.

### Automation 🤖

Experience the magic of automation in GitOps. Mundane tasks transform into orchestrated wonders, allowing your team to focus on innovation while repetitive processes are handled with precision.