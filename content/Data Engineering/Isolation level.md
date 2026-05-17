---
title: Isolation level
tags:
  - data-engineering
  - database
---
The **isolation level** defines **what one transaction can “see” while other transactions are still in progress** (not yet committed).
### 🅐 **Snapshot**

- Think of it like: _“I get my own frozen copy of the data when I start.”_
- Once your transaction starts, you keep reading that **same version** of the data, even if someone else changes it later.
- Other people’s updates won’t affect what you see until you finish.

✅ **Good:** Avoids most conflicts and gives consistent results.  
⚠️ **Bad:** You might not see the latest updates until you restart.

🔹 **Used in:** [[Snowflake]], PostgreSQL (as “Repeatable Read” in some systems).

---

### 🅑 **Repeatable Read**

- Think of it like: _“If I read something once, I’ll always see the same value during my transaction.”_
- Prevents others from changing the rows you’ve already read.
- However, **new rows** that match your query (inserted by others later) might **still appear** if you run the same query again (called a _phantom read_).

✅ **Good:** Stable reads for data you already looked at.  
⚠️ **Bad:** Still vulnerable to “phantom” new rows appearing.

---

### 🅒 **Read Committed**

- Think of it like: _“I can only see data that’s been saved (committed).”_
- You’ll see other people’s changes **only after they finish their transaction.**
- But if you read the same data twice, it could change between reads because someone else committed a change in between.

✅ **Good:** Prevents seeing half-done (uncommitted) changes.  
⚠️ **Bad:** You can get **inconsistent reads** within your own transaction.

---

### 🅓 **Read Uncommitted**

- Think of it like: _“I can see even data that’s not finished being written.”_
- You might see **temporary or uncommitted** data from other transactions.
- This is called a **dirty read** — and that data could disappear or change if the other transaction rolls back.

✅ **Good:** Fastest, no waiting.  
⚠️ **Bad:** Very unsafe — can see wrong or temporary data.

---

### 📊 Summary Table

|Isolation Level|Can See Uncommitted Data?|Repeatable Reads?|Phantom Reads?|Typical Use|
|---|---|---|---|---|
|Read Uncommitted|✅ Yes|❌ No|✅ Yes|Testing, rarely used|
|Read Committed|❌ No|❌ No|✅ Yes|Most common default|
|Repeatable Read|❌ No|✅ Yes|✅ Yes|Financial operations|
|Snapshot / Serializable|❌ No|✅ Yes|❌ No|Analytics, [[Snowflake]]|
