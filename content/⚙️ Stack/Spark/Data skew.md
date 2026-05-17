---
title: Data skew
tags:
  - spark
---
### Signs of skew:

- A few tasks take much longer than others.
- Some partitions are huge (seen in [[Spark]] UI under _Stages → Tasks → Shuffle Read_).
- High shuffle read size for a few partitions.

# **Common Causes**

- **Join on a key with uneven distribution** (e.g., user_id where some users have millions of rows)
- **GroupBy on a skewed key**
- **Repartition by a column with skew**
- **Broadcast join failure due to big table**

A. **Salting (Hash + Random Prefix)**
B. Do a two-stage aggregation.
C. Avoid `repartition(col)` on skewed keys
D. [[Spark]] Config Tuning:
	- Increase shuffle partitions
	- Increase parallelism
	- Enable skew join optimization