---
title: Data loading pattern
tags:
  - data-engineering
---
Fullload
incremental
- watermark (state aware, no second load)
- CDC (handle deletion)
- appending
- merging (idempotency)
event-driven