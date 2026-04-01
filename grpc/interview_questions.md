# 🎯 gRPC Interview Questions

---

# What is gRPC?

gRPC is a high-performance RPC framework that uses Protocol Buffers for communication.

---

# gRPC vs REST?

gRPC:
- Binary
- Faster
- Strong contract

REST:
- JSON
- Slower
- Flexible

---

# What is Proto File?

Defines service contract including methods and messages.

---

# What is Stub?

Auto-generated client code used to call server methods.

---

# What is Channel?

Connection between client and server using HTTP/2.

---

# Types of gRPC?

- Unary
- Server streaming
- Client streaming
- Bidirectional

---

# Why gRPC is fast?

Uses:
- Binary serialization
- HTTP/2

---

# What is Streaming?

Sending multiple messages in a single connection.

---

# When to Use gRPC?

- Microservices communication
- High-performance systems

---

# When NOT to Use?

- Public APIs
- Browser-based apps

---

# Real-Time Use Case

Used in microservices where services need fast communication.

---

# Simple Answer

gRPC is used for fast and efficient communication between services using strongly defined contracts.

---

# 🔥 Advanced gRPC Interview Questions (Must Know)

---

# Internal Working Questions

---

## How does gRPC achieve high performance?

gRPC uses Protocol Buffers (binary serialization) and HTTP/2, which supports multiplexing and reduces latency compared to REST APIs that use JSON over HTTP/1.1.

---

## Why HTTP/2 is important in gRPC?

HTTP/2 allows:
- Multiple requests over single connection
- Header compression
- Faster data transfer

---

## What is multiplexing?

Multiplexing allows multiple requests and responses to be sent over a single TCP connection without waiting for previous ones to complete.

---

## What happens when client calls a gRPC method?

1. Client calls stub method  
2. Request serialized (Protobuf)  
3. Sent via HTTP/2  
4. Server receives request  
5. Server processes logic  
6. Response serialized and sent back  

---

# Scenario-Based Questions

---

## When will you choose gRPC over REST?

- Internal microservices communication  
- High performance required  
- Real-time streaming  

---

## When will you NOT use gRPC?

- Public APIs  
- Browser-based apps (without proxy)  
- When human-readable APIs are needed  

---

## How do you handle versioning in gRPC?

- Never change existing fields  
- Add new fields instead  
- Use versioned packages (v1, v2)

---

## How do you ensure backward compatibility?

- Do not remove fields  
- Do not change field numbers  
- Add optional fields only  

---

# Debugging Questions

---

## How to debug gRPC APIs?

- Use tools like grpcurl or Postman  
- Enable logging in server  
- Check proto file mismatch  

---

## Why am I getting "unimplemented method" error?

Reason:
- Method not implemented in server  
- Proto file mismatch  

---

## Why connection refused?

- Server not running  
- Wrong port  

---

# Performance Questions

---

## How to improve gRPC performance?

- Use connection pooling  
- Optimize message size  
- Use streaming instead of multiple calls  

---

## What is deadline/timeout in gRPC?

Defines maximum time client waits for response.

If exceeded → request fails.

---

# Security Questions

---

## How is security handled in gRPC?

- TLS encryption  
- Authentication using tokens (JWT)  

---

## Difference between TLS and SSL?

TLS is the modern and secure version of SSL.

---

# Streaming Questions (VERY IMPORTANT)

---

## What is bidirectional streaming?

Both client and server send messages continuously over same connection.

---

## Real example of streaming?

- Chat application  
- Live notifications  

---

# Comparison Questions

---

## gRPC vs REST vs GraphQL?

gRPC:
- Fast
- Binary
- Strict contract

REST:
- Simple
- JSON
- Widely used

GraphQL:
- Flexible queries
- Client controls data

---

# Tricky Questions

---

## Can we use gRPC in browser?

Not directly. Use gRPC-Web with proxy.

---

## Is gRPC stateless?

Yes, like REST, but supports streaming connections.

---

## Can gRPC replace REST completely?

No. REST is better for public APIs, gRPC for internal services.

---

# Real Project Question

---

## How you used gRPC in your project?

We used gRPC for internal communication between microservices to reduce latency and improve performance. It helped us define strong contracts and enabled efficient data transfer using Protocol Buffers.

---

# One-Line Summary

gRPC is used for fast, efficient, and structured communication between services, especially in microservice architectures.

---