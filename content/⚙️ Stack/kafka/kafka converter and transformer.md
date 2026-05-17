---
title: kafka converter and transformer
tags:
  - kafka
  - linux
---

In Kafka Connect, **Converters** and **Transformers** (Single Message Transforms or SMTs) are both used to modify data, but they happen at different stages and serve completely different purposes.

Think of it like an international shipping port:

- **The Transformer** is the inspector who opens the box, repaints the item, or masks a secret part before it’s loaded.
    
- **The Converter** is the specialized crane that packages that item into a standard shipping container (like JSON or Avro) so it can actually be moved onto the ship (Kafka).