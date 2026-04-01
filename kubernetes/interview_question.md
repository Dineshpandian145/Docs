# ☸️ Kubernetes Complete Guide (Deep Understanding)

---

# 1. What is Kubernetes?

Kubernetes is a container orchestration system used to manage containerized applications across multiple machines.

In real-world projects, we don’t run a single container. We run many containers, and managing them manually becomes difficult.

Kubernetes helps to:
- Deploy applications automatically
- Scale applications based on traffic
- Restart failed containers
- Manage networking between services

---

# 2. Why Kubernetes is Needed?

Consider a backend application running in Docker.

Problems:
- If container crashes → app goes down
- If traffic increases → app becomes slow
- If server fails → downtime
- Managing multiple containers is complex

Kubernetes solves this by:
- Running multiple copies of the app
- Automatically restarting failed containers
- Distributing traffic
- Running across multiple nodes

---

# 3. Kubernetes Architecture

Kubernetes has two main parts:

---

## 🔹 Control Plane (Master Node)

This is the brain of Kubernetes. It manages the entire cluster.

### API Server
- Entry point for all operations
- All commands (kubectl) go through API server

### Scheduler
- Decides which node should run a pod
- Based on resources (CPU, memory)

### Controller Manager
- Maintains desired state
- Example: If 3 pods are required and 1 fails → creates a new one

### etcd
- Key-value database
- Stores cluster state, configuration, and metadata

---

## 🔹 Worker Node

Worker nodes run the actual applications.

### Kubelet
- Communicates with control plane
- Ensures containers are running

### Container Runtime
- Runs containers (Docker / containerd)

### Kube Proxy
- Handles networking and routing traffic to pods

---

# 4. What is kubectl?

kubectl is a command-line tool used to interact with Kubernetes.

It sends requests to the API Server.

Examples:
- Deploy application
- Check pod status
- View logs
- Debug issues

---

# 5. Core Concepts

---

## 🔹 Pod

A Pod is the smallest unit in Kubernetes.

- Contains one or more containers
- Shares network and storage

Example:
Your Go backend runs inside a pod.

Important:
Kubernetes manages Pods, not containers directly.

---

## 🔹 ReplicaSet

Ensures a specific number of pods are always running.

Example:
replicas = 3  

If 1 pod crashes → new pod is created automatically.

---

## 🔹 Deployment

Deployment manages ReplicaSets and Pods.

It helps to:
- Create pods
- Update pods
- Scale pods

Example:
You deploy your backend with 3 replicas.  
If traffic increases → scale to 5 replicas.

---

## 🔹 Service

Pods are temporary and their IP keeps changing.

Service provides a stable way to access pods.

Types:

### ClusterIP
- Internal communication

### NodePort
- Access from outside using node IP

### LoadBalancer
- External load balancer (used in cloud)

---

## 🔹 Namespace

Used to organize resources.

Example:
- dev
- test
- prod

---

## 🔹 ConfigMap

Stores configuration data.

Example:
- App configuration
- Environment variables

---

## 🔹 Secret

Stores sensitive data.

Example:
- Passwords
- Tokens

---

## 🔹 Volume

Used for persistent storage.

Example:
Database data should not be lost when pod restarts.

---

# 6. How Kubernetes Works (Step-by-Step)

1. You write a YAML file (Deployment, Service)
2. Run: kubectl apply
3. Request goes to API Server
4. Scheduler selects a worker node
5. Pod is created on that node
6. Kubelet starts container
7. Service exposes the application

---

# 7. Real-Time Example (End-to-End)

Application:
- Go Backend
- PostgreSQL
- Redis

Flow:

1. Build Docker image
2. Push to registry
3. Create Deployment YAML
4. Deploy using kubectl
5. Kubernetes creates pods
6. Service exposes backend
7. Users access application

If traffic increases:
- Increase replicas
- Kubernetes creates more pods

If a pod crashes:
- Automatically replaced

---

# 8. Scaling

Manual scaling:
kubectl scale deployment myapp --replicas=5

Kubernetes creates more pods and distributes traffic.

---

# 9. Self-Healing

If a pod crashes:
- Kubernetes detects failure
- New pod is created automatically

---

# 10. Load Balancing

Service distributes traffic across multiple pods.

Example:
3 pods running → traffic shared equally

---

# 11. Common Debug Flow

If application is not working:

1. Check pods  
kubectl get pods  

2. Describe pod  
kubectl describe pod <pod-name>  

3. Check logs  
kubectl logs <pod-name>  

4. Enter pod  
kubectl exec -it <pod-name> -- sh  

---

# 12. Important Differences

---

## Pod vs Container

Container → runs application  
Pod → wraps container  

---

## Deployment vs ReplicaSet

ReplicaSet → maintains count  
Deployment → manages ReplicaSet + updates  

---

## Docker vs Kubernetes

Docker → runs container  
Kubernetes → manages containers  

---

# 13. Key Points to Remember

- Kubernetes manages containers automatically  
- Pod is the smallest unit  
- Deployment controls pods  
- Service exposes application  
- etcd stores cluster data  
- Controller Manager maintains desired state  
- Scheduler decides node placement  
- Kubelet runs containers  

---

# 14. Simple Way to Explain Entire Flow

You:
- Write YAML  
- Apply using kubectl  

Kubernetes:
- Decides where to run  
- Creates pods  
- Runs containers  
- Exposes application  
- Handles failures  

---

# 15. Final Summary

Kubernetes is used to manage large-scale containerized applications.

It ensures:
- High availability  
- Automatic scaling  
- Fault tolerance  
- Easy deployment  

---