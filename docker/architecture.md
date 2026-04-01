# 🐳 Docker Architecture (Complete Flow)

---

# 🧠 High-Level Idea

Docker is used to build, ship, and run applications inside containers.

It ensures:
- Same environment everywhere
- Easy deployment
- Fast execution

---

# 🏗️ Architecture Diagram
    ┌──────────────────────────────┐
    │        Docker Client         │
    │   (CLI / Docker Commands)    │
    └─────────────┬────────────────┘
                  │
                  ▼
    ┌──────────────────────────────┐
    │        Docker Daemon         │
    │         (dockerd)            │
    │                              │
    │  ┌───────────────┐          │
    │  │   Images      │          │
    │  └───────────────┘          │
    │          │                  │
    │  ┌───────────────┐          │
    │  │  Containers   │          │
    │  └───────────────┘          │
    │                              │
    └─────────────┬────────────────┘
                  │
                  ▼
    ┌──────────────────────────────┐
    │      Docker Registry         │
    │   (Docker Hub / Private)     │
    └──────────────────────────────┘


---

# 🧩 Components Explanation

---

## 🔹 Docker Client

This is where you run commands.

Examples:
- docker build
- docker run
- docker pull

The client sends requests to Docker Daemon.

---

## 🔹 Docker Daemon (dockerd)

This is the main engine of Docker.

It:
- Builds images
- Runs containers
- Manages storage and networking

All Docker operations happen here.

---

## 🔹 Docker Images

An image is a blueprint of your application.

It contains:
- Code
- Dependencies
- Runtime

Images are read-only.

---

## 🔹 Docker Containers

A container is a running instance of an image.

It:
- Runs your application
- Has its own environment
- Is isolated from other containers

---

## 🔹 Docker Registry

A place to store images.

Examples:
- Docker Hub
- Private registry

You push and pull images from here.

---

# 🔄 End-to-End Flow

---

## Step 1: Build Image

You write a Dockerfile and run:

docker build -t myapp .

Docker:
- Reads Dockerfile
- Creates image

---

## Step 2: Push Image

docker push myapp

Image stored in registry.

---

## Step 3: Run Container

docker run -p 8080:8080 myapp

Docker:
- Creates container
- Runs application

---

# 🌍 Real-Time Flow


Example:

1. User hits API  
2. Request goes to container  
3. Application processes  
4. Response returned  

---

# ⚙️ Real-Time Example

Application:
- Go backend

Flow:

1. Write code  
2. Create Dockerfile  
3. Build image  
4. Run container  

If another developer runs:
- Same image → same behavior  

No environment issue.

---

# 🧠 Dockerfile Role

Dockerfile defines how image is built.

Example:

```dockerfile
FROM golang:1.22

WORKDIR /app

COPY . .

RUN go build -o main

CMD ["./main"]