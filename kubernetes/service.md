
---

# 📁 File: `service.yaml`

```markdown id="k8sservice02"
# ☸️ Service YAML - Networking Clarity

---

# 1. What is a Service?

A Service is used to expose your application to users or other services.

Problem:
- Pods are temporary
- Their IP keeps changing

Solution:
- Service provides a stable IP and name

---

# 2. Basic Service YAML

```yaml
apiVersion: v1
kind: Service

metadata:
  name: myapp-service

spec:
  type: NodePort

  selector:
    app: myapp

  ports:
    - port: 80
      targetPort: 8080
      nodePort: 30007