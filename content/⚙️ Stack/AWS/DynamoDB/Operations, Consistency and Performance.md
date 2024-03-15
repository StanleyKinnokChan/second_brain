# Operations, Consistency and Performance

**Reading and writing (2 modes)**

- on-demand
    - on-demand - unknown/ unpredictable amount, low admin
    - price per million R or W units
- provisioned…RCU & WCU set on a per table basis
    - every operation consumes **at least 1 RCU/WCU**
    - 1 RCU is 1x4kb read operation/s
    - 1 WCU is 1x1kb write operation/s
- every table has a RCU & WCU burst pool (300 seconds)

**Operation:**

**Query (retrieve data)**

- just extracting the value
- only search for PK and optionally SK
- run query for PK and SK at once operation can save RCU

    [[Operations, Consistency and Performance/Untitled.png]]


**Scan**

- least efficient but most flexible
- move through the table item by item, entire table is consumed and discard the one that don’t need (expansive)
- all attributes can be used for searching

    [[Operations, Consistency and Performance/Untitled 1.png]]


**Consistency Model**

- consistency ⇒ the data being read = data updated intermediate
- one storage node is chosen to be leader, data is replicated to other nodes in few milliseconds

**2 Consistency Model**

- Eventually consistent reads (default)
    - access one of the nodes randomly, scaling better & cost reduction
    - a small chance of reading outdated data
    - prioritizes availability with low latency
    - 50% of cost compared to Strongly consistent reads
- Strongly consistent reads
    - always read the leader nodes

**Total WCU required calculation**

1. calculate the avg. size per item
2. WCU per item by round(size/ 1kb)
3. multiple by avg no. of item/s

**Total RCU required calculation**

1. calculate the avg. size per item
2. RCU per item by round(size/ 4kb)
3. multiple by avg no. of item/s (for strongly consistent)
4. further divided by 2 if it is Eventually consistent reads
