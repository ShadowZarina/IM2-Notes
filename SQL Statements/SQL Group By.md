# The SQL GROUP BY Statement
The GROUP BY statement is used to group rows that have the same values into summary rows, like "Find the number of customers in each country".
The GROUP BY statement is almost always used in conjunction with aggregate functions, like COUNT(), MAX(), MIN(), SUM(), AVG(), to perform calculations on each group.

## Count vs group by vs order by
-- COUNT
SELECT COUNT(first_name) FROM customers;
-- GROUP BY
SELECT * FROM customers GROUP BY UserID;
-- ORDER BY
SELECT * FROM customers ORDER BY UserID DESC;
-- HAVING
SELECT * FROM customers GROUP BY UserID HAVING UserID < 2000;


-- 20. 
SELECT category_id, COUNT(*) FROM products GROUP BY category_id;

-- 21. 
SELECT customer_id, SUM(total_amount) FROM orders GROUP BY customer_id;

-- 22.
SELECT category_id, MAX(price) FROM products GROUP BY category_id; 

-- 23.
SELECT customer_id, COUNT(*) FROM orders GROUP BY customer_id;

-- 24.
SELECT product_id, SUM(quantity) FROM order_items GROUP BY product_id;

-- 25.
SELECT DATE(order_date) AS order_day, AVG(total_amount) FROM orders GROUP BY DATE(order_date);

-- 26.
SELECT category_id FROM products GROUP BY category_id HAVING COUNT(*) > 5;

-- 27. 
SELECT customer_id FROM orders GROUP BY customer_id HAVING SUM(total_amount) > 500.00;

-- 28. 
SELECT category_id FROM products GROUP BY category_id HAVING AVG(price) < 50.00;

-- 29. 
SELECT product_id FROM order_items GROUP BY product_id HAVING SUM(quantity) > 100;

-- 30. 
SELECT customer_id, COUNT(*) AS order_count FROM orders GROUP BY customer_id HAVING COUNT(*) > 3 ORDER BY order_count DESC;
