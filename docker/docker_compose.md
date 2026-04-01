# 🐳 Docker Compose (Complete Guide)

---

# 1. What is Docker Compose?

## ✅ Answer (Interview Style)

Docker Compose is a tool used to define and run multiple containers using a single YAML file.

It helps manage multi-service applications like backend, database, and cache together.

---

# 2. Why Do We Use Docker Compose?

## ✅ Answer

To simplify running multiple containers without manually starting each container.

---

## 🎯 Real-Time Example

Project with:
- Go Backend
- PostgreSQL DB
- Redis Cache

Without docker-compose:
- Run 3 separate docker commands

With docker-compose:
- Run everything with one command

---

# 3. docker-compose.yaml Structure

```yaml
version: "3"

services:
  app:
    build: .
    ports:
      - "8080:8080"

  db:
    image: postgres:15
    environment:
      POSTGRES_PASSWORD: secret

  redis:
    image: redis:7