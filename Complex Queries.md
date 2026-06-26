# JUNE 24, 2026

```
1. Use modulo operator to isolate customer records where the customer_id is an even number

SELECT * FROM customers WHERE customer_id % 2 = 0;

2. Find all data columns from customers where UserID is strictly greater than 502.

SELECT * FROM customers WHERE UserID > 502;

3. Increment UserID value by 1000 for all customers whose accounts were created before ‘2026-06-24 11:20’

// NOTE: PHPMyAdmin does NOT support += symbols

UPDATE customers SET UserID += 1000 WHERE created_at = ‘2026-06-24 11:20’

4. Use bitwise AND (&) operator to parse the customers table and return rows where checking UserID column against an entitlement bitmask of 4 returns a positive state

SELECT * FROM customers WHERE (UserID & 4) > 0;

// STUDY BITWISE AND, OR, XOR

5. Write a filtering query using BETWEEN to pull all data rows from customers where the created_at date falls between ‘2026-06-24 00:00:00’ and ‘2026-06-24 23:59:59’

SELECT * FROM customers WHERE created_at BETWEEN ‘2026-06-24 00:00:00’ AND ‘2026-06-24 23:59:59’;

6. Write a query using LIKE and a % wildcard to extract rows whose email values explicitly end with @corporate.com

SELECT * FROM customers WHERE email LIKE ‘%corporate.com’;

7. Use the COUNT() aggregate function to calculate the total number of customer profiles registered in the table

SELECT COUNT(*) FROM customers

8. Write a query that casts created_at to a date

```

Count vs group by vs order by
- Count = 5
– SELECT COUNT(first_name) FROM customers;
- Group By 
– SELECT * FROM customers GROUP BY UserID;
- Order By
– SELECT * FROM customers ORDER BY UserID DESC;

```
CREATE TABLE products ( 
ProductID INT(11) PRIMARY KEY NOT NULL, 
SKU VARCHAR(20) NOT NULL, 
Price DECIMAL(10,2) 
); 

CREATE TABLE users ( 
UserID INT(11) PRIMARY KEY NOT NULL, 
Username VARCHAR(50) NOT NULL, 
CreatedAt DATETIME 
); 

CREATE TABLE customers ( 
customer_id INT(11) PRIMARY KEY NOT NULL, 
first_name VARCHAR(50) NOT NULL, 
last_name VARCHAR(50) NOT NULL, 
email VARCHAR(100), 
created_at DATETIME, 
UserID INT(11) REFERENCES users(UserID) 
); 

CREATE TABLE orders (
  OrderID INT(11) PRIMARY KEY NOT NULL,
  UserID INT(11) NOT NULL,
  OrderDate DATE NOT NULL,
  Total DECIMAL(10,2)
);


INSERT INTO products VALUES 
(1, 'PR123',249.99), 
(2, 'PR124',120.00), 
(3, 'PR125',25.50), 
(4, 'PR126',89.95), 
(5, 'PR127',149.00); 

INSERT INTO users VALUES 
(501, 'alex_g','2026-06-24 11:15:00'), 
(502, 'sarah_m','2026-06-24 11:16:12'), 
(503, 'dev_jay','2026-06-24 11:18:45'), 
(504, 'elena_r','2026-06-24 11:20:01'), 
(505, 'sam_t','2026-06-24 11:22:30'); 

INSERT INTO customers VALUES 
(1, 'Alex','Grahan','alex.g@corporate.com','2026-06-24 11:15:00',501), 
(2, 'Sarah','Monroe','sarah.m@corporate.com','2026-06-24 11:16:12',502), 
(3, 'Dev','Jayzen','dev.jay@corporate.com','2026-06-24 11:18:45',503), 
(4, 'Elena','Roberts','elena.r@corporate.com','2026-06-24 11:20:01',504), 
(5, 'Sam','Traxton','sam.t@corporate.com','2026-06-24 11:22:30',505);

INSERT INTO orders VALUES
(1,1,'2026-02-05',249.99),
(2,2,'2026-02-10',174.50),
(3,3,'2026-02-15',199.99),
(4,4,'2026-02-20',74.99),
(5,5,'2026-03-02',349.99);
```

```
--1. Use modulo operator to isolate customer records where the customer_id is an even number

SELECT * FROM customers WHERE customer_id % 2 = 0;

--2. Find all data columns from customers where UserID is strictly greater than 502.

SELECT * FROM customers WHERE UserID > 502;

--3. Increment UserID value by 1000 for all customers whose accounts were created before ‘2026-06-24 11:20’

--// NOTE: PHPMyAdmin does NOT support += symbols

UPDATE customers SET UserID += 1000 WHERE created_at = ‘2026-06-24 11:20’

--4. Use bitwise AND (&) operator to parse the customers table and return rows where checking UserID column against an entitlement bitmask of 4 returns a positive state

SELECT * FROM customers WHERE (UserID & 4) > 0;

--// STUDY BITWISE AND, OR, XOR

--5. Write a filtering query using BETWEEN to pull all data rows from customers where the created_at date falls between ‘2026-06-24 00:00:00’ and ‘2026-06-24 23:59:59’

SELECT * FROM customers WHERE created_at BETWEEN ‘2026-06-24 00:00:00’ AND ‘2026-06-24 23:59:59’;

--6. Write a query using LIKE and a % wildcard to extract rows whose email values explicitly end with @corporate.com

SELECT * FROM customers WHERE email LIKE ‘%corporate.com’;

--7. Use the COUNT() aggregate function to calculate the total number of customer profiles registered in the table

SELECT COUNT(*) FROM customers

--8. Write a query that casts created_at to a date
```

```
-- COUNT
SELECT COUNT(first_name) FROM customers;
-- GROUP BY
SELECT * FROM customers GROUP BY UserID;
-- ORDER BY
SELECT * FROM customers ORDER BY UserID DESC;
-- HAVING
SELECT * FROM customers GROUP BY UserID HAVING UserID < 2000;
```

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
