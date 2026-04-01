# 🚀 Architecture Diagram (Docker + Kubernetes + AWS)

---

# Overall Flow Diagram

                 ┌────────────────────────────┐
                 │        👤 User             │
                 └────────────┬───────────────┘
                              │ HTTP Request
                              ▼
                 ┌────────────────────────────┐
                 │     🌐 EC2 Instance        │
                 │ (Public IP / Entry Point)  │
                 └────────────┬───────────────┘
                              │
                              ▼
                 ┌────────────────────────────┐
                 │   ☸ Kubernetes Cluster     │
                 └────────────┬───────────────┘
                              │
               ┌──────────────┴──────────────┐
               ▼                             ▼
     ┌──────────────────┐         ┌──────────────────┐
     │   📦 Pod 1        │         │   📦 Pod 2        │
     │ (App Container)   │         │ (App Container)   │
     └─────────┬────────┘         └─────────┬────────┘
               │                              │
               └──────────┬───────────────────┘
                          ▼
               ┌────────────────────────────┐
               │   🔀 Kubernetes Service    │
               │ (Load Balancing Layer)     │
               └────────────┬───────────────┘
                            │
                            ▼
                 ┌────────────────────────────┐
                 │   🧠 Backend Application   │
                 │   (Go / API Layer)        │
                 └────────────┬───────────────┘
                              │
              ┌───────────────┼────────────────┐
              ▼                                ▼
 ┌────────────────────────┐         ┌────────────────────────┐
 │   🗂️ AWS S3 Storage     │         │   ⚡ AWS Lambda         │
 │ (Images / Files)       │         │ (Background Tasks)     │
 └────────────┬───────────┘         └────────────┬───────────┘
              │                                │
              ▼                                ▼
   File Stored & URL Generated     Process Image / Event Logic

---

# Docker Flow (Build & Push)

Developer Machine
        │
        ▼
┌────────────────────────────┐
│   🐳 Docker Build Image    │
└────────────┬───────────────┘
             ▼
┌────────────────────────────┐
│   📦 Docker Registry       │
│   (Docker Hub / ECR)       │
└────────────┬───────────────┘
             ▼
┌────────────────────────────┐
│   ☸ Kubernetes Pulls Image │
└────────────────────────────┘

---

# Request Flow (Step-by-Step)

1. User sends request from browser or mobile  
2. Request reaches EC2 public IP  
3. Kubernetes receives the request  
4. Service routes request to one of the pods  
5. Pod processes request  

If file upload:
- File stored in S3  

If background task:
- Lambda is triggered  

6. Response sent back to user  

---

# Simple Explanation

User → EC2 → Kubernetes → Pods → Backend → S3 / Lambda → Response

---

# One-Line Interview Explanation

The user request hits the EC2 instance, Kubernetes routes it to running pods, the backend processes the request, stores files in S3 if needed, triggers Lambda for background tasks, and returns the response to the user.

---