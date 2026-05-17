---
title: kafka topics
tags:
  - kafka
  - linux
---

A **Topic** is the core way that data is organized.



```
\Create a topic:
./bin/kafka-topics.sh --create --topic topic-1 --partitions 3 --replication-factor 3 --bootstrap-server localhost:9092
```

## The Core Characteristics

- **Append-Only Log:** A topic is essentially an ordered list of messages. New data is always added to the end.
- **Immutable:** Once a message is written to a topic, it cannot be changed or deleted (until it expires based on time or size).
- **Multi-Subscriber:** Unlike a traditional "message queue" where data is deleted once read, many different applications can read from the same Kafka topic at the same time without interfering with each other.


## Replication: The "Safety Net"

When you create a topic, you usually set a **Replication Factor** (usually 3).

- This means Kafka creates copies of every partition and spreads them across different brokers.
- If one broker crashes, the topic remains available because the other copies (replicas) take over.