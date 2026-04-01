# ☸️ Deployment YAML - Deep Understanding

---

# 1. What is a Deployment?

A Deployment is used to manage application pods in Kubernetes.

It helps to:
- Create pods
- Maintain desired number of pods
- Update application (rolling update)
- Scale application

You never create pods directly in real projects.  
You always use Deployment.

---

# 2. Basic Deployment YAML

```yaml
apiVersion: apps/v1
kind: Deployment

metadata:
  name: myapp

spec:
  replicas: 2

  selector:
    matchLabels:
      app: myapp

  template:
    metadata:
      labels:
        app: myapp

    spec:
      containers:
      - name: myapp
        image: myapp:latest
        ports:
        - containerPort: 8080