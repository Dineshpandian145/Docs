# 🐳 Docker Basics

---

# 1. What is Docker?

## ✅ Answer (Interview Style)

Docker is a containerization tool used to package an application along with its dependencies, libraries, and runtime into a single unit called an image.

This ensures the application runs consistently across different environments like development, testing, and production.

Docker helps solve the “it works on my machine” problem.

---

## 🎯 Real-Time Example

In a team project, if a new developer joins:
- Without Docker → They must install all dependencies manually
- With Docker → They just run the container

This saves time and avoids environment issues.

---

# 2. What is Containerization?

## ✅ Answer

Containerization is a process of packaging an application with all its dependencies so it can run consistently in any environment.

---

## 🧠 Simple Understanding

- Application + Dependencies = Container
- Runs same everywhere

---

# 3. What is Docker Image?

## ✅ Answer

A Docker image is a read-only template that contains:
- Application code
- Runtime
- Libraries
- Dependencies

It is used to create containers.

---

## 🎯 Example

Think of an image like a **blueprint**.

---

# 4. What is Docker Container?

## ✅ Answer

A container is a running instance of a Docker image.

You can run multiple containers from a single image.

---

## 🎯 Example

- Image = Class
- Container = Object

---

# 5. Difference Between Image and Container

| Image | Container |
|------|----------|
| Blueprint | Running instance |
| Read-only | Read-write |
| Static | Dynamic |

---

# 6. Why Do We Use Docker?

## ✅ Answer

Docker is used to:
- Ensure environment consistency
- Simplify deployment
- Reduce setup time
- Improve scalability
- Isolate applications

---

## 🎯 Real-Time Use Case

Backend (Go) + Database (PostgreSQL) + Cache (Redis)

Without Docker:
- Install all manually

With Docker:
- Run everything using containers

---

# 7. Docker Architecture

## ✅ Components

- Docker Client → CLI (docker commands)
- Docker Daemon → Runs containers
- Docker Image → Template
- Docker Container → Running app

---

## 🧠 Flow

docker build → creates image  
docker run → creates container  

---

# 8. Docker Lifecycle

Dockerfile → Image → Container

---

# 9. Where Do We Use Docker?

## ✅ Development
- Local setup
- Testing

## ✅ CI/CD Pipeline
- Build once, deploy anywhere

## ✅ Production
- Run scalable applications

---

# 10. Advantages of Docker

- Lightweight
- Fast startup
- Easy deployment
- Consistent environment
- Better resource utilization

---

# 11. Limitations of Docker

- Not full isolation like VM
- Security concerns (shared kernel)
- Requires container management (Kubernetes)

---

# 12. Docker vs Virtual Machine

| Docker | Virtual Machine |
|--------|----------------|
| Lightweight | Heavy |
| Shares OS kernel | Full OS |
| Fast startup | Slow |
| Less memory | More memory |

---

# 13. Common Interview Questions

---

## ❓ What problem does Docker solve?

Docker solves environment inconsistency issues and simplifies deployment.

---

## ❓ Can we run multiple containers from one image?

Yes, we can run multiple containers from a single image.

---

## ❓ Is Docker a VM?

No, Docker is not a VM. It uses containerization, which is lightweight and faster.

---

## ❓ Does Docker install dependencies automatically?

Yes, dependencies are defined in the Dockerfile and installed during image build.

---

# 🔥 Summary

- Image = Template  
- Container = Running instance  
- Docker = Containerization tool  
- Ensures consistency across environments  

---