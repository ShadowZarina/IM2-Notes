# JUNE 25, 2026

```
SELECT ItemPrice, ShippingCost, (ItemPrice * Quantity) + ShippingCost AS TotalInvoice FROM Cart;

SELECT * FROM SystemLogs WHERE LogID % 2 = 0;

SELECT * FROM Table WHERE Column <> 'Exclusion';

SELECT * FROM Table where (UserID & 4) > 0;

UPDATE Table SET Column += 100 WHERE Condition;

SELECT (customer_id | 2) AS MarkedRoute FROM customers;
```

```
SELECT * FROM Table WHERE Con1 AND Con2;

SELECT * FROM Table WHERE Column IN (Val1, Val2, Val3) AND NOT (first_name = '');

SELECT * FROM Table WHERE Column BETWEEN Min AND Max;

SELECT * FROM customers WHERE first_name LIKE 'Al___';

SELECT DISTINCT first_name FROM customers;
```

```
WHERE - predicate filter BEFORE row grouping
GROUP BY - aggregates records sharing common values into distinct summaries
HAVING - predicate filter evaluated AFTER row grouping occurs (for filtering aggregates)
ORDER BY - ASC or DESC
LIMIT/TOP - caps total rows returned
```
```
SELECT Column1, COUNT(*) FROM customers
WHERE Column2 = 'Filter' GROUP BY Column 1
HAVING COUNT(*) > 1 
ORDER BY Column1 DESC
LIMIT 5;
```
