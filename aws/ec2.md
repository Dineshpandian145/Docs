# ☁️ EC2 (Elastic Compute Cloud) - Complete Understanding

---

# What is EC2?

EC2 is a virtual server provided by AWS that allows us to run applications in the cloud.

Instead of buying a physical machine, we create a virtual machine using EC2 and use it just like our own system. We can install software, run applications, and manage everything as we do on a normal computer.

In simple terms, EC2 is like renting a computer from AWS over the internet.

---

# Why EC2 is Needed?

In traditional systems, companies had to:
- Buy servers
- Maintain hardware
- Handle scaling manually

This leads to:
- High cost
- Maintenance effort
- Downtime during scaling

EC2 solves these problems by:
- Providing servers on demand
- Allowing easy scaling
- Reducing cost (pay only for usage)

---

# Real-Time Example

Suppose you built a Go backend application.

Instead of running it on your local machine, you:
- Launch an EC2 instance
- Install Docker
- Run your application

Now your backend is available on the internet, and users can access it using the EC2 public IP.

---

# Types of EC2 Instances

AWS provides different types of instances based on use case.

For example:
- General purpose → balanced CPU and memory
- Compute optimized → high CPU
- Memory optimized → high RAM

In real projects, we choose based on application needs.

---

# Key Components of EC2

---

## Instance

An instance is the virtual server itself.

It includes:
- CPU
- Memory
- Storage
- Operating system

---

## AMI (Amazon Machine Image)

AMI is a template used to create an EC2 instance.

It contains:
- OS (Ubuntu, Amazon Linux)
- Pre-installed software

Example:
If you choose Ubuntu AMI, your EC2 will start with Ubuntu installed.

---

## Instance Type

Defines hardware configuration.

Example:
- t2.micro → small instance
- m5.large → bigger instance

---

## Key Pair

Used for secure login.

- Public key → stored in EC2
- Private key (.pem file) → used to connect

Without key pair, you cannot access the server.

---

## Security Group

Acts like a firewall.

It controls:
- Which ports are open
- Who can access the instance

Example:
- Port 22 → SSH
- Port 80 → HTTP
- Port 3000 → application

---

## Elastic IP

A fixed public IP address.

Normally, EC2 public IP changes when restarted.  
Elastic IP ensures a static IP.

---

## EBS (Elastic Block Storage)

Storage attached to EC2.

Used to:
- Store application data
- Store OS files

---

# How to Setup EC2 (Step-by-Step)

---

## Step 1: Launch Instance

- Go to AWS console
- Select EC2 → Launch Instance
- Choose OS (Ubuntu)

---

## Step 2: Choose Instance Type

- Select t2.micro (for testing)

---

## Step 3: Configure Security Group

Allow:
- SSH (22)
- HTTP (80)
- Custom ports (like 8080)

---

## Step 4: Create Key Pair

- Download .pem file
- Keep it safe

---

## Step 5: Launch Instance

Instance starts in a few seconds.

---

## Step 6: Connect to EC2

Use SSH:

ssh -i key.pem ubuntu@<public-ip>

Now you are inside your cloud server.

---

# Running Application on EC2

Once connected:

1. Install Docker  
2. Pull your image  
3. Run container  

Example:

docker run -p 8080:8080 myapp

Now your application is live.

---

# Real-World Flow

Developer:
- Builds Docker image
- Pushes to registry

EC2:
- Pulls image
- Runs application

User:
- Accesses app using public IP

---

# Common Issues

---

## Cannot connect to EC2

Reason:
- Port 22 not open
- Wrong key

---

## Application not accessible

Reason:
- Port not open in security group
- Container not running

---

## Permission error (SSH)

Fix:

chmod 400 key.pem

---

# Best Practices

- Use security groups carefully
- Avoid using root user
- Use Elastic IP for production
- Monitor CPU and memory

---

# Simple Way to Explain

EC2 is a virtual machine in AWS where we can run our applications.

We create an instance, connect using SSH, install required tools, and deploy our application. It gives us full control over the system, just like a real server.

---

# Summary

EC2 allows us to run applications in the cloud without managing physical hardware. It provides flexibility, scalability, and full control over the environment.

---