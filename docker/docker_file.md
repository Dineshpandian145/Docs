# 🐳 Dockerfile (Complete Guide)

---

# 1. What is a Dockerfile?

## ✅ Answer (Interview Style)

A Dockerfile is a text file that contains a set of instructions used to build a Docker image.

It defines:
- Base image
- Dependencies
- Application code
- Commands to run the application

---

# 2. Why Do We Use Dockerfile?

## ✅ Answer

To automate the process of creating Docker images.

---

## 🎯 Real-Time Example

Instead of manually:
- Installing Go
- Installing dependencies
- Copying code

We define everything in Dockerfile → build once → use anywhere

---

# 3. Basic Dockerfile Example (Go App)

```dockerfile
FROM golang:1.22-alpine

WORKDIR /app

COPY . .

RUN go build -o app

CMD ["./app"]


# 4. Dockerfile Instructions (Complete List)

---

## 🔹 FROM

### ✅ Purpose
Defines the base image for the container.

### 📌 Example
FROM ubuntu:20.04

---

## 🔹 WORKDIR

### ✅ Purpose
Sets the working directory inside the container.

### 📌 Example
WORKDIR /app

---

## 🔹 COPY

### ✅ Purpose
Copies files from local system to container.

### 📌 Example
COPY . .

---

## 🔹 ADD

### ✅ Purpose
Similar to COPY, but also supports:
- Downloading files from URL
- Extracting compressed files

### 📌 Example
ADD file.tar.gz /app/

---

## 🔹 RUN

### ✅ Purpose
Executes commands during image build time.

### 📌 Example
RUN apt-get update && apt-get install -y curl

---

## 🔹 CMD

### ✅ Purpose
Defines default command when container starts.

### 📌 Example
CMD ["node", "app.js"]

---

## 🔹 ENTRYPOINT

### ✅ Purpose
Defines the main command that always runs.

### 📌 Example
ENTRYPOINT ["python"]

---

## 🔹 EXPOSE

### ✅ Purpose
Documents which port the container uses.

### 📌 Example
EXPOSE 8080

---

## 🔹 ENV

### ✅ Purpose
Sets environment variables inside container.

### 📌 Example
ENV PORT=8080

---

## 🔹 ARG

### ✅ Purpose
Defines build-time variables.

### 📌 Example
ARG VERSION=1.0

---

## 🔹 LABEL

### ✅ Purpose
Adds metadata to image.

### 📌 Example
LABEL version="1.0"

---

## 🔹 VOLUME

### ✅ Purpose
Creates a mount point for persistent data.

### 📌 Example
VOLUME /data

---

## 🔹 USER

### ✅ Purpose
Specifies which user runs the container.

### 📌 Example
USER appuser

---

## 🔹 SHELL

### ✅ Purpose
Overrides default shell.

### 📌 Example
SHELL ["/bin/bash", "-c"]

---

## 🔹 HEALTHCHECK

### ✅ Purpose
Checks if container is healthy.

### 📌 Example
HEALTHCHECK CMD curl --fail http://localhost:8080 || exit 1

---

## 🔹 ONBUILD

### ✅ Purpose
Executes instructions when image is used as base for another build.

### 📌 Example
ONBUILD COPY . /app

---

## 🔹 STOPSIGNAL

### ✅ Purpose
Defines system call signal to stop container.

### 📌 Example
STOPSIGNAL SIGTERM

---

# 🧠 Interview Tip

👉 Most commonly used:
- FROM
- WORKDIR
- COPY
- RUN
- CMD
- EXPOSE
- ENV

👉 Advanced (less asked but important):
- ENTRYPOINT
- VOLUME
- HEALTHCHECK
- ARG

---

# 🔥 Summary

- Dockerfile instructions define how image is built  
- Some run at build time (RUN, ARG)  
- Some run at container start (CMD, ENTRYPOINT)  

---