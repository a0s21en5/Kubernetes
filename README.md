# Kubernetes Overview

---

## What is Kubernetes?

Kubernetes (also called **K8s**) is an open-source **container orchestration platform** that automates:

- Deployment of applications  
- Scaling of applications  
- Management of containerized applications  
- Handling failures, restarts, and self-healing  

### Origin
- Originally developed by **Google**  
- Internal code name: **Borg**  
- Released publicly in **2014**  
- Donated to **CNCF (Cloud Native Computing Foundation)**  
- Now a **graduated CNCF project** — mature and enterprise-ready  

---

# Monolithic vs Microservices

## Monolithic Application
- Entire application runs as a **single unit**  
- Hard to **scale specific components**  
- One failure can impact the whole application  
- Slow and less flexible deployment cycles  

## Microservices Architecture
- Application is split into **small, independent services**  
- Each service can be deployed, scaled, and updated separately  
- Failures are isolated  
- Faster development and deployment cycles  
- Ideal for cloud-native environments  

### Kubernetes & Microservices
Kubernetes is designed to support **microservices-based deployments** through:
- Independent scaling  
- Automated deployments  
- Self-healing  
- Container orchestration  

---

# Kubernetes Nodes & Cluster

## What is a Node?
- A **Node** is a single physical or virtual **server**  
- In simple terms: **One Node = One Server**  
- Nodes run workloads using Pods  

## What is a Cluster?
- A **Cluster** = multiple nodes working together  
- Enables distributed, scalable computing  

## Components of a Kubernetes Cluster
- **Master Node(s)** — control and manage cluster  
- **Worker Node(s)** — run application Pods  

---

# Where Do Containers Run?

- **All applications, Pods, and containers run only on Worker Nodes**  
- **Master Node never runs application containers**  
- Worker Nodes provide compute power for workloads  

---

# Master Node Components

## 1. API Server
- Gateway for all cluster communication  
- Processes commands from `kubectl`  
- Validates and manages cluster operations  

## 2. Scheduler
- Decides which worker node runs each Pod  
- Assigns based on CPU, RAM, and available resources  

## 3. Controller Manager
- Maintains the **desired state** of the cluster  
- Example: If a Pod crashes, it recreates it  

## 4. etcd
- Distributed key-value database  
- Stores:
  - Pod & node info  
  - Cluster metadata  
  - Configurations  
- Acts as Kubernetes’ **single source of truth**  

---

# Worker Node Components

## 1. Kubelet
- Node agent running on every worker node  
- Ensures containers are running & healthy  
- Communicates with API Server  
- Starts/stops containers as needed  

## 2. Kube-proxy (Service Proxy)
- Handles **cluster networking**  
- Routes traffic to the correct Pods  
- Exposes Kubernetes Services  

---

# Pods

- Smallest **deployable unit** in Kubernetes  
- Acts as an **isolated environment** containing 1 or more containers  
- Shares:
  - Network  
  - Storage  
  - Runtime configuration  

## Best Practice
- Prefer **1 container per Pod**  
- Use multi-container Pods only when necessary  
  (e.g., **sidecar pattern** for logging, proxies, helpers)

---

# Container Networking (CNI)

Kubernetes uses **CNI plugins** to provide networking between:
- Master Node ↔ Worker Node  
- Worker Node ↔ Worker Node  
- Pod ↔ Pod (cluster-wide)  

CNI handles:
- IP allocation  
- Routing  
- Pod connectivity  

## Popular CNI Networks
### Weave Net
- Simple, automatic routing and IP management  

### Calico
- High performance  
- Strong security & network policies support  

### Flannel
- Easy and lightweight networking  

### Cilium
- Advanced networking with **eBPF**  
- High performance and security  

---

# kubectl

`kubectl` is the **command-line tool** for interacting with Kubernetes.

- Acts as the **Kubernetes console**  
- Commands like:
  - `kubectl get`  
  - `kubectl apply`  
  - `kubectl create`  
- All communication goes through the **API Server**  

Used for managing:
- Pods  
- Deployments  
- Services  
- Cluster state  

---
