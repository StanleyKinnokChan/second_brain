# TTL

- allows you to define a **per-item timestamp** to determine when an item is no longer needed
- deletes the item from your table **without consuming any write throughput** at specified timestamp
- deletion is a background system process and don’t impact table performance
- no extra cost to reduce stored data volumes
- use case: sensitive data after n year (GDPR)
