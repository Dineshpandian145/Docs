# 🏗️ gRPC Architecture

---

# High-Level Architecture

Client → Stub → gRPC Channel → Network → Server → Service Implementation

---

# Flow Diagram

Client Application
        │
        ▼
┌────────────────────┐
│   Client Stub      │
│ (Auto Generated)   │
└─────────┬──────────┘
          │
          ▼
┌────────────────────┐
│   gRPC Channel     │
│ (HTTP/2 Transport) │
└─────────┬──────────┘
          │
          ▼
     🌐 Network
          │
          ▼
┌────────────────────┐
│   gRPC Server      │
└─────────┬──────────┘
          ▼
┌────────────────────┐
│ Service Logic      │
│ (Your Code)        │
└────────────────────┘

---

# Components

---

## Proto File

Defines:
- Services
- Methods
- Request & Response

---

## Client Stub

- Auto-generated code
- Used to call server methods

---

## Server

- Implements service methods
- Handles requests

---

## Channel

- Connection between client and server
- Uses HTTP/2

---

# Real Application Flow

1. Client calls method using stub  
2. Request serialized using Protobuf  
3. Sent over HTTP/2  
4. Server receives request  
5. Server processes logic  
6. Response sent back  

---

# Types of Communication

---

## Unary

One request → One response  

---

## Server Streaming

One request → Multiple responses  

---

## Client Streaming

Multiple requests → One response  

---

## Bidirectional Streaming

Multiple requests ↔ Multiple responses  

---

# Simple Explanation

Client calls a function → gRPC sends request → Server processes → returns response

---