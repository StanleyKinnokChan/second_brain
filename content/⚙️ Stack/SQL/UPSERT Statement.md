---
title: 
tags:
  - Template
  - SQL
---
```
MERGE INTO Dim_Product AS target
USING (VALUES (?, ?, ?, ?, ?)) AS source (ProductID, ProductName, Price, StartDate, Version)
ON target.ProductID = source.ProductID
WHEN MATCHED THEN
    UPDATE SET
        target.ProductName = source.ProductName,
        target.Price = source.Price,
        target.EndDate = DATEADD(DAY, -1, source.StartDate),
        target.Version = source.Version - 1
WHEN NOT MATCHED THEN
    INSERT (ProductID, ProductName, Price, StartDate, EndDate, Version)
    VALUES (source.ProductID, source.ProductName, source.Price, source.StartDate, '9999-12-31', source.Version);

```
