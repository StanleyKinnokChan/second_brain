---
title: 
tags:
  - sql
---
```
CREATE TABLE staff_dummy (
    Code INT PRIMARY KEY,
    Name VARCHAR(50)
);

INSERT INTO staff_dummy (Code, Name) VALUES
(1234, 'Stanley'),
(1235, 'Stanley'),
(1236, 'Stanley'),
(1237, 'Stanley'),
(1238, 'James'),
(1239, 'James'),
(1240, 'James'),
(1241, 'May'),
(1242, 'May'),
(1243, 'Julia');
```


```
SELECT Name,COUNT(*) 
FROM staff_dummy 
GROUP BY Name
HAVING COUNT(*)>3
```

