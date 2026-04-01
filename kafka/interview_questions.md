# 🎯 Kafka Interview Questions

---

# What is Kafka?

Kafka is a distributed messaging system used for real-time data streaming.

---

# Kafka vs RabbitMQ?

Kafka:
- Distributed
- High throughput

RabbitMQ:
- Simple
- Message queue

---

# What is Topic?

A logical channel where messages are stored.

---

# What is Partition?

A topic is divided into partitions for scalability.

---

# What is Offset?

Unique ID for each message.

---

# What is Consumer Group?

Group of consumers reading data.

---

# Why Kafka is fast?

- Sequential disk writes
- Partitioning
- Batching

---

# Scenario Questions

---

## When to use Kafka?

- Event-driven systems
- Logging systems
- Real-time analytics

---

## When not to use Kafka?

- Simple request-response APIs

---

# Real-Time Use Case

Used in microservices for async communication.

---

# Simple Answer

Kafka is used to handle large-scale real-time data streams efficiently.

---

# 🔥 Advanced Kafka Concepts

---

# What is Replication?

Kafka replicates data across brokers to prevent data loss.

---

# What is Leader and Follower?

Leader:
- Handles read/write

Follower:
- Replicates data

---

# What is ISR (In-Sync Replica)?

Set of replicas that are fully synced.

---

# What is Retention?

Kafka stores messages for a fixed time.

---

# What is Exactly Once?

Ensures message is processed only once.

---

# What is At Least Once?

Message may be processed multiple times.

---

# What is At Most Once?

Message may be lost but not duplicated.

---

# Real Problem

Duplicate message handling → Use idempotent consumers

---

# Simple Explanation

Kafka ensures reliable data streaming using replication and partitioning.

---