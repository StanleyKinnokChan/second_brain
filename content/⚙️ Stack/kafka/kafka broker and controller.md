---
title: kafka broker and controller
tags:
  - kafka
  - linux
---
Both are **roles** that a Kafka server plays. Every Controller is a Broker, but not every Broker is the Controller.
A Broker is a single Kafka server. Its primary job is to handle the **Data Plane**—the actual movement of messages
