# ⚙️ gRPC Setup Guide (Go)

---

# Install Required Tools

---

## Install Protocol Buffer Compiler

Download:
https://grpc.io/docs/protoc-installation/

Verify:
protoc --version

---

## Install Go Plugins

go install google.golang.org/protobuf/cmd/protoc-gen-go@latest  
go install google.golang.org/grpc/cmd/protoc-gen-go-grpc@latest  

---

# Create Proto File

example.proto

syntax = "proto3";

package example;

option go_package = "example/proto";

service UserService {
  rpc GetUser (UserRequest) returns (UserResponse);
}

message UserRequest {
  string id = 1;
}

message UserResponse {
  string name = 1;
}

---

# Generate Code

protoc --go_out=. --go-grpc_out=. example.proto

---

# Run Server

- Implement service
- Start gRPC server

---

# Run Client

- Use generated stub
- Call methods

---

# How to Add New Method

1. Update proto file:

rpc CreateUser (CreateUserRequest) returns (UserResponse);

2. Regenerate code:

protoc --go_out=. --go-grpc_out=. example.proto

3. Implement method in server

---

# How to Change Version

---

## Backward Compatible Changes

Allowed:
- Add new fields
- Add new methods

---

## Breaking Changes (Avoid)

- Remove fields
- Change field numbers

---

## Versioning Strategy

Use:
- v1, v2 in package

Example:

package user.v1;

---

# Best Practice

Never reuse field numbers.

---