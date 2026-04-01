# ☸️ Kubernetes Architecture (Complete Flow)

---

# 🧠 High-Level Idea

Kubernetes manages applications by controlling:
- Where containers run
- How many run
- How they communicate
- How they recover from failure

---

# 🏗️ Architecture Diagram

                ┌─────────────────────────────┐
                │      Control Plane          │
                │  (Master Node / Brain)      │
                │                             │
                │  ┌───────────────────────┐  │
                │  │     API Server       │◄──────────── kubectl
                │  └───────────────────────┘  │
                │             │               │
                │  ┌───────────────────────┐  │
                │  │      Scheduler       │  │
                │  └───────────────────────┘  │
                │             │               │
                │  ┌───────────────────────┐  │
                │  │ Controller Manager   │  │
                │  └───────────────────────┘  │
                │             │               │
                │  ┌───────────────────────┐  │
                │  │        etcd          │  │
                │  └───────────────────────┘  │
                └─────────────┬───────────────┘
                              │
        ──────────────────────┼──────────────────────
                              │
      ┌───────────────────────┴───────────────────────┐
      │               Worker Nodes                    │
      │                                               │
      │   ┌───────────────┐     ┌───────────────┐     │
      │   │   Node 1      │     │   Node 2      │     │
      │   │               │     │               │     │
      │   │  ┌─────────┐  │     │  ┌─────────┐  │     │
      │   │  │  Pod 1  │  │     │  │  Pod 3  │  │     │
      │   │  │ (App)   │  │     │  │ (App)   │  │     │
      │   │  └─────────┘  │     │  └─────────┘  │     │
      │   │               │     │               │     │
      │   │  ┌─────────┐  │     │  ┌─────────┐  │     │
      │   │  │  Pod 2  │  │     │  │  Pod 4  │  │     │
      │   │  └─────────┘  │     │  └─────────┘  │     │
      │   │               │     │               │     │
      │   │ Kubelet       │     │ Kubelet       │     │
      │   │ Kube Proxy    │     │ Kube Proxy    │     │
      │   │ Container RT  │     │ Container RT  │     │
      │   └───────────────┘     └───────────────┘     │
      │                                               │
      └───────────────────────────────────────────────┘


---

# 🧩 Components Explanation

---

## 🔹 Control Plane (Brain)

This controls everything in Kubernetes.

### API Server
- Entry point for all operations
- Every command goes through this

Example:
kubectl apply → API Server receives request

---

### Scheduler
- Decides where to run pods
- Checks CPU, memory, availability

---

### Controller Manager
- Maintains desired state

Example:
You want 3 pods → only 2 running  
Controller creates 1 more automatically

---

### etcd
- Stores all cluster data
- Like database for Kubernetes

Stores:
- Pod info
- Node info
- Configurations

---

## 🔹 Worker Nodes (Execution Layer)

These run your applications.

---

### Kubelet
- Communicates with control plane
- Starts containers
- Monitors pods

---

### Container Runtime
- Runs containers
- Example: Docker, containerd

---

### Kube Proxy
- Handles networking
- Routes traffic to correct pods

---

### Pods
- Smallest unit
- Runs your application

---

# 🔄 End-to-End Flow

---

## Step 1: User Deploys Application

You run:

kubectl apply -f deployment.yaml

---

## Step 2: API Server Receives Request

- Validates request
- Stores data in etcd

---

## Step 3: Scheduler Assigns Node

- Finds best worker node
- Assigns pod to that node

---

## Step 4: Kubelet Starts Container

- Pulls Docker image
- Runs container inside pod

---

## Step 5: Application is Running

- Pods are now active
- Service exposes the app

---

# 🌍 Real-Time Request Flow


Example:

1. User hits API  
2. Service receives request  
3. Service selects one pod  
4. Pod processes request  
5. Response sent back  

---

# ⚙️ Real-Time Example

Application:
- Go Backend
- PostgreSQL
- Redis

Flow:

1. Backend deployed using Deployment
2. Multiple pods created
3. Service exposes backend
4. Users access application

If traffic increases:
- More pods created

If pod crashes:
- New pod created automatically

---

# 🔥 Key Strengths

- Auto scaling
- Self healing
- Load balancing
- High availability

---

# 🧠 Simple Way to Explain

You:
- Write YAML
- Run kubectl

Kubernetes:
- Decides where to run
- Creates pods
- Runs containers
- Exposes app
- Handles failures

---

# 📌 Final Summary

- Control Plane → Brain  
- Worker Node → Executes application  
- Pod → Runs app  
- Service → Exposes app  
- etcd → Stores data  

---