# ⚙️ Kafka Setup Guide

---

# Install Kafka

Download Kafka:
https://kafka.apache.org/downloads

---

# Start Zookeeper

bin/zookeeper-server-start.sh config/zookeeper.properties

---

# Start Kafka Server

bin/kafka-server-start.sh config/server.properties

---

# Create Topic

bin/kafka-topics.sh --create --topic my-topic --bootstrap-server localhost:9092

---

# Produce Message

bin/kafka-console-producer.sh --topic my-topic --bootstrap-server localhost:9092

---

# Consume Message

bin/kafka-console-consumer.sh --topic my-topic --from-beginning --bootstrap-server localhost:9092

---

# Real Project Setup

- Use Docker for Kafka
- Configure multiple brokers
- Use Kafka client libraries (Go, Java)

---

# Simple Explanation

Start Kafka → Create topic → Send message → Consume message

---

# 🚀 Kafka Setup Using Docker

---

# Why Use Docker for Kafka?

In real projects, we don’t install Kafka manually because:
- Setup is complex
- Version conflicts
- Hard to manage dependencies

Docker solves this by:
- Running Kafka in containers
- Easy setup and teardown
- Consistent environment

---

# Architecture (Docker Setup)

We need:
- Zookeeper (manages Kafka cluster)
- Kafka Broker (message server)

Flow:
Zookeeper → Kafka → Producer → Consumer

---

# Step 1: Create docker-compose.yml

Create a file named:

docker-compose.yml

---

# Step 2: Add Configuration

version: '3'

services:

  zookeeper:
    image: confluentinc/cp-zookeeper:latest
    container_name: zookeeper
    ports:
      - "2181:2181"
    environment:
      ZOOKEEPER_CLIENT_PORT: 2181

  kafka:
    image: confluentinc/cp-kafka:latest
    container_name: kafka
    ports:
      - "9092:9092"
    depends_on:
      - zookeeper
    environment:
      KAFKA_BROKER_ID: 1
      KAFKA_ZOOKEEPER_CONNECT: zookeeper:2181
      KAFKA_ADVERTISED_LISTENERS: PLAINTEXT://localhost:9092
      KAFKA_OFFSETS_TOPIC_REPLICATION_FACTOR: 1

---

# Step 3: Start Kafka

Run:

docker-compose up -d

---

# Step 4: Verify Containers

docker ps

You should see:
- zookeeper
- kafka

---

# Step 5: Create Topic

docker exec -it kafka bash

Inside container:

kafka-topics --create \
--topic test-topic \
--bootstrap-server localhost:9092 \
--partitions 1 \
--replication-factor 1

---

# Step 6: Produce Message

kafka-console-producer \
--topic test-topic \
--bootstrap-server localhost:9092

Type messages and press enter.

---

# Step 7: Consume Message

Open new terminal:

docker exec -it kafka bash

kafka-console-consumer \
--topic test-topic \
--from-beginning \
--bootstrap-server localhost:9092

---

# Real Project Flow

1. Backend sends message → Kafka  
2. Kafka stores in topic  
3. Consumer service reads message  
4. Processes asynchronously  

---

# Common Issues

---

## Kafka not connecting

Check:
- Port 9092 exposed
- Docker running

---

## Cannot create topic

Reason:
- Kafka not fully started

Fix:
Wait few seconds after startup

---

## Connection refused

Fix:
Check KAFKA_ADVERTISED_LISTENERS

---

# Important Config Explanation

---

## KAFKA_ADVERTISED_LISTENERS

Defines how clients connect to Kafka.

For local:
PLAINTEXT://localhost:9092

---

## ZOOKEEPER_CONNECT

Kafka uses Zookeeper to manage cluster.

---

# Stop Kafka

docker-compose down

---

# Simple Explanation

Docker runs Kafka and Zookeeper containers, allowing us to start a Kafka server quickly and test producers and consumers.

---

# Summary

Using Docker, we can quickly set up Kafka, create topics, and test message flow without complex installation.

---