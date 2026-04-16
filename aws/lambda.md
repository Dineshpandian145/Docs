# ☁️ AWS Lambda - Complete Understanding

---

# What is Lambda?

AWS Lambda is a serverless compute service that allows us to run code without managing any servers.

In traditional systems, we need to create servers (like EC2), install software, and maintain them. But in Lambda, we just write the code, upload it, and AWS takes care of running it.

In simple terms, Lambda executes your code only when needed, without requiring a server to be always running.

---

# Why Lambda is Needed?

In real-world applications, not all tasks require a continuously running server.

Some operations are:
- Event-based
- Short-lived
- Background tasks

If we use EC2 for these:
- Server runs all the time
- Wastes cost
- Requires maintenance

Lambda solves this by:
- Running code only when triggered
- Automatically scaling
- Charging only for execution time

---

# Real-Time Example

Consider an application where users upload images.

Flow:
- User uploads image to S3
- S3 triggers Lambda
- Lambda resizes the image
- Stores processed image back in S3

Here, no server is continuously running. Lambda executes only when the upload happens.

---

# Key Components of Lambda

---

## Function

A Lambda function is the code that we write.

It contains:
- Business logic
- Input handling
- Output response

Example:
A function to process uploaded files.

---

## Event Source (Trigger)

Lambda runs based on events.

Common triggers:
- S3 (file upload)
- API Gateway (HTTP request)
- CloudWatch (scheduled jobs)

---

## Execution Role (IAM Role)

Defines permissions for Lambda.

Example:
- Read from S3
- Write to database

Without proper role, Lambda cannot access other AWS services.

---

## Handler

The entry point of Lambda function.

Example (Python):
def handler(event, context):

This function is executed when Lambda runs.

---

## Timeout & Memory

We configure:
- Execution time limit
- Memory allocation

Lambda stops if it exceeds timeout.

---

# How to Setup Lambda (Step-by-Step)

---

## Step 1: Create Function

- Go to AWS console
- Open Lambda service
- Click "Create Function"

---

## Step 2: Choose Runtime

Select language:
- Python
- Node.js
- Go

---

## Step 3: Write Code

Example:

def handler(event, context):
    return "Hello from Lambda"

---

## Step 4: Configure Trigger

Example:
- Connect S3 bucket
- Or API Gateway

---

## Step 5: Deploy & Test

- Click Deploy
- Run test event

---

# Lambda with API Gateway (Important)

We can expose Lambda as an API.

Flow:
- Client sends HTTP request
- API Gateway receives request
- Triggers Lambda
- Lambda processes and returns response

This is used to build serverless APIs.

---

# Lambda with S3

Flow:
- File uploaded to S3
- S3 triggers Lambda
- Lambda processes file

---

# Real-World Architecture

User → Upload file → S3  
S3 → Trigger → Lambda  
Lambda → Process → Store back  

---

# Advantages of Lambda

- No server management
- Auto scaling
- Cost efficient
- Easy integration with AWS services

---

# Limitations

- Execution time limit
- Not suitable for long-running apps
- Cold start delay (initial latency)

---

# Common Issues

---

## Timeout Error

Reason:
- Function runs too long

Fix:
- Increase timeout
- Optimize code

---

## Permission Denied

Reason:
- Missing IAM role permissions

---

## Cold Start Delay

Reason:
- Lambda not used recently

---

# Best Practices

- Keep functions small
- Use proper memory configuration
- Handle errors properly
- Use environment variables

---

# Simple Way to Explain

Lambda is used to run code automatically when an event happens, without managing servers.

It is mainly used for background processing, automation, and serverless APIs.

---

# Summary

Lambda allows us to execute code on demand without maintaining infrastructure. It is highly scalable, cost-efficient, and ideal for event-driven applications.

---


# 🚀 Go Lambda API – Step-by-Step Deployment Guide

This project demonstrates how to build and deploy a simple **Go API using AWS Lambda and API Gateway**.

---

# 📌 Overview

We are building a simple API:

```
GET /hello
```

Response:

```
Hello Dinesh
```

---

# 🏗️ Architecture

```
Client (Browser / Postman)
        ↓
API Gateway
        ↓
AWS Lambda (Go)
        ↓
Response
```

---

# ⚙️ Prerequisites

Make sure you have installed:

* Go (>= 1.20)
* AWS CLI (configured with credentials)
* ZIP utility

---

# 📁 Project Structure

```
.
├── main.go
├── go.mod
└── function.zip
```

---

# 🧾 Step 1: Create Go Application

Create a file `main.go`:

```go
package main

import (
	"context"
	"fmt"

	"github.com/aws/aws-lambda-go/lambda"
)

type Request struct {
	Name string `json:"name"`
}

type Response struct {
	Message string `json:"message"`
}

func handler(ctx context.Context, req Request) (Response, error) {
	name := req.Name
	if name == "" {
		name = "Dinesh"
	}

	return Response{
		Message: fmt.Sprintf("Hello %s", name),
	}, nil
}

func main() {
	lambda.Start(handler)
}
```

---

# 📦 Step 2: Initialize Go Module

```bash
go mod init hello-lambda
go get github.com/aws/aws-lambda-go/lambda
```

---

# 🔨 Step 3: Build Binary for Lambda

```bash
GOOS=linux GOARCH=amd64 go build -o main
```

---

# 📁 Step 4: Create Deployment Package

```bash
zip function.zip main
```

---

# ☁️ Step 5: Create Lambda Function

1. Go to AWS Console
2. Navigate to Lambda
3. Click **Create Function**
4. Choose:

   * Runtime: Go
5. Upload `function.zip`
6. Set handler:

   ```
   main
   ```

---

# 🌐 Step 6: Create API Gateway

1. Go to API Gateway
2. Create **HTTP API**
3. Add route:

   ```
   GET /hello
   ```
4. Attach the Lambda function

---

# 🚀 Step 7: Deploy API

* Click **Deploy**
* Copy the generated URL

Example:

```
https://abc123.execute-api.amazonaws.com/hello
```

---

# 🧪 Step 8: Test API

### Browser:

```
https://your-url/hello
```

### Postman (Optional):

```json
{
  "name": "Dinesh"
}
```

### Expected Response:

```json
{
  "message": "Hello Dinesh"
}
```

---

# 🔥 Optional Improvements

### Use API Gateway Proxy

```go
import "github.com/aws/aws-lambda-go/events"

func handler(req events.APIGatewayProxyRequest) (events.APIGatewayProxyResponse, error)
```

---

### Add Logging

```go
fmt.Println("Request received:", req)
```

---

### Use Environment Variables

```go
os.Getenv("ENV")
```

---

# ⚠️ Common Issues

| Issue                 | Fix                                |
| --------------------- | ---------------------------------- |
| Lambda not triggering | Check API Gateway integration      |
| Wrong response format | Use correct struct or proxy format |
| Build not working     | Ensure GOOS=linux                  |

---

# 🎯 Summary

* Lambda runs your Go code without managing servers
* API Gateway exposes HTTP endpoints
* You only pay when your code runs

---