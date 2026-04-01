# 🐳 Docker Interview Questions (Complete Guide)

---

## ❓ What is Docker?

### ✅ Answer
Docker is a containerization tool used to package an application along with its dependencies into a single unit called an image.

This image can run anywhere without environment issues.

### 🎯 Example
A developer builds an app → works locally  
Another developer runs it → fails  

Docker solves this by packaging everything together.

---

## ❓ What is a Docker Image?

### ✅ Answer
A Docker image is a read-only template that contains:
- Application code
- Dependencies
- Runtime

It is used to create containers.

---

## ❓ What is a Docker Container?

### ✅ Answer
A container is a running instance of a Docker image.

### 🎯 Example
Image = Class  
Container = Object  

---

## ❓ Difference between Image and Container?

| Image | Container |
|------|----------|
| Template | Running instance |
| Read-only | Read-write |

---

## ❓ What is Dockerfile?

### ✅ Answer
A Dockerfile is a file that contains instructions to build a Docker image.

---

## ❓ What is docker-compose?

### ✅ Answer
docker-compose is used to run multiple containers using a single YAML file.

---

# 🚀 Intermediate Level

---

## ❓ What happens when you run `docker run myapp`?

### ✅ Answer
1. Docker checks if image exists locally  
2. If not → pulls from registry  
3. Creates a container  
4. Allocates CPU/memory  
5. Sets up networking  
6. Runs CMD/ENTRYPOINT  
7. Container starts  

---

## ❓ Difference between docker run and docker start?

### ✅ Answer
- docker run → creates + starts container  
- docker start → starts existing container  

---

## ❓ What is port mapping?

### ✅ Answer
It connects container port to host port.

### 🎯 Example
docker run -p 8080:8080 myapp  
Access app via browser.

---

## ❓ What is Docker Volume?

### ✅ Answer
A volume is used to persist data outside the container.

### 🎯 Example
Database data should not be lost when container stops.

---

## ❓ What is Docker Network?

### ✅ Answer
Docker network allows containers to communicate with each other.

### 🎯 Example
Backend connects to DB using service name.

---

## ❓ Difference between COPY and ADD?

### ✅ Answer
COPY → simple file copy  
ADD → supports URL and extraction  

---

## ❓ What is .dockerignore?

### ✅ Answer
Used to exclude unnecessary files while building image.

---

# 🔥 Advanced Level

---

## ❓ What is multi-stage build?

### ✅ Answer
It reduces image size by separating build and runtime environments.

### 🎯 Example
Build Go app → copy only binary → smaller image

---

## ❓ What is Docker caching?

### ✅ Answer
Docker caches layers to speed up builds.

If no changes → reuse layers.

---

## ❓ Difference between CMD and ENTRYPOINT?

### ✅ Answer

CMD:
- Default command  
- Can override  

ENTRYPOINT:
- Fixed command  
- Always runs  

---

## ❓ What is Docker Registry?

### ✅ Answer
A place to store Docker images.

---

## ❓ What is Docker Hub?

### ✅ Answer
Docker Hub is a cloud-based public registry to store and share images.

---

## ❓ What is container orchestration?

### ✅ Answer
Managing multiple containers automatically (scaling, recovery, load balancing).

### 🎯 Example
Kubernetes

---

# 💡 Real-World Scenario Questions

---

## ❓ How do you deploy a Dockerized app?

### ✅ Answer
1. Write Dockerfile  
2. Build image  
3. Push to registry  
4. Deploy using Kubernetes or cloud  

---

## ❓ How do you debug a container issue?

### ✅ Answer
- Check logs → docker logs  
- Access container → docker exec  
- Verify environment/config  

---

## ❓ What happens if a container crashes?

### ✅ Answer
- Docker → container stops  
- Kubernetes → restarts automatically  

---

## ❓ How do containers communicate?

### ✅ Answer
Using internal network and service names.

---

# 🧠 Tricky Questions

---

## ❓ Can we run multiple containers from one image?

Yes, multiple containers can be created from a single image.

---

## ❓ Is Docker a virtual machine?

No, Docker uses containerization, not virtualization.

---

## ❓ Does Docker support multiple OS?

Yes, Docker supports Linux, Windows, and macOS.

---

## ❓ Can containers share data?

Yes, using volumes.

---

## ❓ What is default Docker network?

bridge network

---

# 🔥 Summary

- Docker simplifies deployment  
- Image = template  
- Container = running instance  
- Dockerfile = build instructions  
- docker-compose = multi-container tool  

---