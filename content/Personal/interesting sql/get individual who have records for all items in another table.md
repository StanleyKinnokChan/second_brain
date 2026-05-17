---
title: 
tags:
  - sql
---
ref: Leetcode 1045. Customers Who Bought All Products

```
CREATE TABLE Customer (
    customer_id INT,
    product_key INT,
    PRIMARY KEY (customer_id, product_key)
);

CREATE TABLE Product (
    product_key INT PRIMARY KEY
);

INSERT INTO Customer (customer_id, product_key) VALUES
(1, 5),
(2, 6),
(3, 5),
(3, 6),
(1, 6);

INSERT INTO Product (product_key) VALUES
(5),
(6);
```

```sql
select customer_id from Customer
group by customer_id
having count(distinct product_key) = (select count(distinct product_key) from Product)
;
```