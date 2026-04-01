# 🏗️ Kafka Architecture

---

# High-Level Flow

Producer → Topic → Partition → Broker → Consumer

---

# Diagram

Producer
   │
   ▼
┌────────────────────┐
│      Topic         │
│  (Logical Stream)  │
└─────────┬──────────┘
          ▼
┌────────────────────┐
│    Partition       │
│ (Data Segments)    │
└─────────┬──────────┘
          ▼
┌────────────────────┐
│      Broker        │
│ (Kafka Server)     │
└─────────┬──────────┘
          ▼
     Consumer

---

# Components

---

## Producer

Sends messages to Kafka.

---

## Consumer

Reads messages from Kafka.

---

## Topic

Logical channel where messages are stored.

---

## Partition

Splits topic into smaller parts for scalability.

---

## Broker

Kafka server that stores data.

---

## Consumer Group

Multiple consumers working together.

---

# Real Application Flow

1. Producer sends message  
2. Message stored in topic  
3. Topic divided into partitions  
4. Stored in broker  
5. Consumer reads message  

---

# Simple Explanation

Producer sends data → Kafka stores → Consumer reads

---