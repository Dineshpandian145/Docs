# 🐳 Docker Commands (With Use Cases)

---

# 1. Build Docker Image

## 🔹 Command

docker build -t myapp .

## ✅ Explanation

- Builds a Docker image from Dockerfile
- `-t` → tag (name of image)
- `.` → current directory

---

## 🎯 Use Case

When you write a Dockerfile and want to create an image.

---

# 2. Run Container

## 🔹 Command

docker run myapp

## ✅ Explanation

- Creates and starts a container from the image

---

## 🎯 Use Case

To start your application

---

# 3. Run with Port Mapping

## 🔹 Command

docker run -p 8080:8080 myapp

## ✅ Explanation

- Maps container port to host port
- Format: host:container

---

## 🎯 Use Case

Access your app in browser:
http://localhost:8080

---

# 4. Run in Detached Mode

## 🔹 Command

docker run -d myapp

## ✅ Explanation

- Runs container in background

---

## 🎯 Use Case

For long-running applications (backend servers)

---

# 5. Run with Name

## 🔹 Command

docker run --name mycontainer myapp

## ✅ Explanation

- Assigns custom name to container

---

# 6. List Running Containers

## 🔹 Command

docker ps

---

# 7. List All Containers

## 🔹 Command

docker ps -a

---

# 8. Stop Container

## 🔹 Command

docker stop <container-id>

---

# 9. Start Container

## 🔹 Command

docker start <container-id>

---

# 10. Restart Container

## 🔹 Command

docker restart <container-id>

---

# 11. Remove Container

## 🔹 Command

docker rm <container-id>

---

# 12. Remove Image

## 🔹 Command

docker rmi myapp

---

# 13. List Images

## 🔹 Command

docker images

---

# 14. View Logs

## 🔹 Command

docker logs <container-id>

---

## 🎯 Use Case

Debug application issues

---

# 15. Execute Inside Container

## 🔹 Command

docker exec -it <container-id> sh

## ✅ Explanation

- `-it` → interactive terminal
- Access container shell

---

## 🎯 Use Case

Check files, debug issues inside container

---

# 16. Copy Files

## 🔹 Command

docker cp file.txt <container-id>:/app/

---

# 17. Pull Image from Docker Hub

## 🔹 Command

docker pull nginx

---

## 🎯 Use Case

Download public images

---

# 18. Push Image to Docker Hub

## 🔹 Command

docker push username/myapp

---

## 🎯 Use Case

Share your image

---

# 19. Remove All Stopped Containers

## 🔹 Command

docker container prune

---

# 20. Remove All Unused Images

## 🔹 Command

docker image prune

---

# 🧠 Important Interview Questions

---

## ❓ Difference between docker run and docker start?

docker run:
- Creates + starts container

docker start:
- Starts existing container

---

## ❓ What is port mapping?

It connects container port to host port.

---

## ❓ Why use -d?

To run container in background.

---

## ❓ Why use docker exec?

To access running container and debug issues.

---

# 🎯 Real-Time Scenario

Backend (Go API) running in container:

- Start container → docker run -d -p 8080:8080 myapp  
- Check logs → docker logs  
- Debug → docker exec  

---

# 🔥 Summary

- build → create image  
- run → start container  
- ps → list containers  
- logs → debug  
- exec → access container  

---