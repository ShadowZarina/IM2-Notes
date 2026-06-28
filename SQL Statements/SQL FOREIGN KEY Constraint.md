# MySQL FOREIGN KEY Constraint

The FOREIGN KEY constraint establishes a link between two tables, and prevents action that will destroy the link between them.
A FOREIGN KEY is a column in a table that refers to the PRIMARY KEY in another table.
The table with the foreign key column is called the child table, and the table with the primary key column is called the referenced or parent table.
The FOREIGN KEY constraint prevents invalid data from being inserted into the foreign key column (in the child table), because the value has to exist in the parent table.
The FOREIGN KEY constraint also prevents you from deleting a record in the parent table, if related rows still exist in the child table. 
Assume we have two tables:
Persons Table
PersonID
LastName
FirstName
Age
1
Hansen
Ola
30
2
Svendson
Tove
23

Orders Table
OrderID
OrderNumber
PersonID
3
22456
2
4
24562
1

Here we see that the "PersonID" column in the "Orders" table points to the "PersonID" column in the "Persons" table.
The "PersonID" column in the "Persons" table is the PRIMARY KEY in the "Persons" table.
The "PersonID" column in the "Orders" table is the FOREIGN KEY in the "Orders" table.

REMOVE ADS

FOREIGN KEY on CREATE TABLE
The following SQL creates a FOREIGN KEY constraint on the "PersonID" column upon creation of the "Orders" table:
CREATE TABLE Orders (
	OrderID int PRIMARY KEY,
	OrderNumber int NOT NULL,
	PersonID int,
    CONSTRAINT fk_Person
    FOREIGN KEY (PersonID)
    REFERENCES Persons(PersonID)
);

FOREIGN KEY on ALTER TABLE
To create a FOREIGN KEY constraint on the "PersonID" column after the "Orders" table is created, use the following SQL:
ALTER TABLE Orders
ADD CONSTRAINT fk_Person
FOREIGN KEY (PersonID)
REFERENCES Persons(PersonID);

Drop a FOREIGN KEY Constraint
To drop a FOREIGN KEY constraint, use the following SQL:
ALTER TABLE Orders
DROP FOREIGN KEY fk_Person;

# REFERENCE

[SQL FOREIGN KEY Constraint](https://www.w3schools.com/mySQL/mysql_foreignkey.asp)

# EXAMPLE DATABASE

ACTIVITY (6/23/26, TUES)

/*

-- 1. customers table
CREATE TABLE customers (
  customer_id INTEGER PRIMARY KEY AUTOINCREMENT,
  first_name VARCHAR(50) NOT NULL,
  last_name VARCHAR(50) NOT NULL,
  email VARCHAR(100) NOT NULL UNIQUE,
  created_at DATETIME DEFAULT CURRENT_TIMESTAMP
);

-- 2. categories table
CREATE TABLE categories (
  category_id INTEGER PRIMARY KEY AUTOINCREMENT,
  category_name VARCHAR(50) NOT NULL,
  description LONGTEXT
);

-- 3. products table 
CREATE TABLE products (
  product_id INTEGER PRIMARY KEY AUTOINCREMENT,
  product_name VARCHAR(100) NOT NULL,
  category_id INTEGER,
  price DECIMAL(10,2) NOT NULL,
  stock_quantity INTEGER DEFAULT 0,
  FOREIGN KEY (category_id) REFERENCES categories(category_id)
);
 
-- 4. orders table 
CREATE TABLE orders (
  order_id INTEGER PRIMARY KEY AUTOINCREMENT,
  customer_id INTEGER,
  order_date DATETIME DEFAULT CURRENT_TIMESTAMP,
  total_amount DECIMAL(10,2) NOT NULL,
  FOREIGN KEY (customer_id) REFERENCES customers(customer_id)
);

-- 5. order_items table
CREATE TABLE order_items (
  order_item_id INTEGER PRIMARY KEY AUTOINCREMENT,
  order_id INTEGER,
  product_id INTEGER,
  quantity INTEGER NOT NULL,
  unit_price DECIMAL(10,2) NOT NULL,
  FOREIGN KEY (order_id) REFERENCES orders(order_id),
  FOREIGN KEY (product_id) REFERENCES products(product_id)
  );
  */
/*
  INSERT INTO customers (first_name, last_name, email, created_at) VALUES
('Liam', 'Smith', 'liam.smith@email.com', '2026-01-10 09:15:00'),
('Olivia', 'Johnson', 'olivia.j@email.com', '2026-01-12 14:22:00'),
('Noah', 'Williams', 'noah.w@email.com', '2026-01-15 11:05:00'),
('Emma', 'Brown', 'emma.brown@email.com', '2026-01-18 16:40:00'),
('Oliver', 'Jones', 'oliver.j@email.com', '2026-02-01 10:30:00'),
('Ava', 'Garcia', 'ava.g@email.com', '2026-02-03 08:12:00'),
('Elijah', 'Miller', 'elijah.m@email.com', '2026-02-14 13:55:00'),
('Charlotte', 'Davis', 'charlotte.d@email.com', '2026-02-20 17:18:00'),
('William', 'Rodriguez', 'william.r@email.com', '2026-03-01 12:00:00'),
('Sophia', 'Martinez', 'sophia.m@email.com', '2026-03-05 09:45:00'),
('James', 'Hernandez', 'james.h@email.com', '2026-03-10 15:30:00'),
('Amelia', 'Lopez', 'amelia.l@email.com', '2026-03-22 11:12:00'),
('Benjamin', 'Gonzalez', 'ben.g@email.com', '2026-04-02 14:20:00'),
('Isabella', 'Wilson', 'isabella.w@email.com', '2026-04-09 10:05:00'),
('Lucas', 'Anderson', 'lucas.a@email.com', '2026-04-15 16:50:00'),
('Mia', 'Thomas', 'mia.t@email.com', '2026-05-01 08:34:00'),
('Henry', 'Taylor', 'henry.t@email.com', '2026-05-12 13:15:00'),
('Evelyn', 'Moore', 'evelyn.m@email.com', '2026-05-19 11:40:00'),
('Alexander', 'Jackson', 'alex.j@email.com', '2026-06-02 09:25:00'),
('Harper', 'Martin', 'harper.m@email.com', '2026-06-15 15:10:00');
*/

/*
INSERT INTO categories (category_name, description) VALUES
('Electronics', 'Gadgets, devices, and computing essentials.'),
('Apparel', 'Premium clothing, footwear, and accessories.'),
('Home & Kitchen', 'Furniture, smart appliances, and kitchenware.'),
('Books', 'Fiction, non-fiction, textbooks, and novels.'),
('Sports & Outdoors', 'Fitness gear, camping equipment, and sportswear.'),
('Beauty & Personal Care', 'Skincare, cosmetics, and grooming tools.'),
('Automotive', 'Car care, tools, and vehicular accessories.'),
('Toys & Games', 'Board games, action figures, and educational toys.'),
('Groceries', 'Pantry staples, snacks, and beverages.'),
('Office Supplies', 'Stationery, notebooks, and desk organization.'),
('Pet Supplies', 'Food, toys, and grooming items for pets.'),
('Health & Wellness', 'Vitamins, supplements, and first-aid gear.'),
('Tools & Home Improvement', 'Hand tools, lighting, and hardware.'),
('Garden & Outdoor', 'Plants, lawnmowers, and patio furniture.'),
('Music & Instruments', 'Vinyl records, instruments, and audio gear.'),
('Jewelry', 'Watches, rings, necklaces, and bracelets.'),
('Baby Products', 'Strollers, diapers, and nursery essentials.'),
('Travel Gear', 'Luggage, backpacks, and travel accessories.'),
('Arts & Crafts', 'Painting supplies, yarn, and crafting tools.'),
('Video Games', 'Gaming consoles, titles, and controllers.');

*/
/*
INSERT INTO products (product_name, category_id, price, stock_quantity) VALUES
('Wireless Noise-Canceling Headphones', 1, 249.99, 45),
('Ergonomic Mechanical Keyboard', 1, 120.00, 30),
('Premium Cotton Crewneck T-Shirt', 2, 25.50, 120),
('Weatherproof Running Jacket', 2, 89.95, 60),
('Stainless Steel Smart Coffee Maker', 3, 149.00, 25),
('Non-Stick Ceramic Cookware Set (10-Piece)', 3, 199.99, 15),
('"The Data Revolution" (Hardcover)', 4, 29.99, 80),
('Quantum Mechanics for Beginners', 4, 45.00, 40),
('Ultra-Lightweight Backpacking Tent', 5, 185.00, 20),
('Adjustable Smart Dumbbell Set', 5, 349.99, 12),
('Hydrating Hyaluronic Serum', 6, 32.00, 200),
('Professional Cordless Hair Clipper', 6, 65.00, 55),
('Portable Car Jump Starter', 7, 79.99, 35),
('High-Gloss Car Wax Kit', 7, 24.50, 90),
('Strategy Board Game: Mars Colony', 8, 55.00, 42),
('Organic Matcha Green Tea Powder', 9, 19.99, 150),
('Leather Hardbound Journal', 10, 18.00, 300),
('Orthopedic Memory Foam Dog Bed', 11, 59.99, 28),
('Electric Cordless Drill Set', 13, 115.00, 50),
('Next-Gen Gaming Console (500GB)', 20, 499.99, 8);
*/

/*
INSERT INTO orders (customer_id, order_date, total_amount) VALUES
(1, '2026-02-05 10:14:00', 249.99),
(2, '2026-02-10 15:30:00', 174.50),
(3, '2026-02-15 11:22:00', 199.99),
(4, '2026-02-20 09:05:00', 74.99),
(5, '2026-03-02 14:45:00', 349.99),
(1, '2026-03-12 16:20:00', 145.50),
(6, '2026-03-25 13:10:00', 32.00),
(7, '2026-04-01 10:00:00', 264.99),
(8, '2026-04-05 11:55:00', 185.00),
(9, '2026-04-12 17:34:00', 54.49),
(10, '2026-04-18 08:15:00', 149.00),
(11, '2026-04-26 12:40:00', 499.99),
(12, '2026-05-02 15:22:00', 65.00),
(13, '2026-05-10 09:50:00', 25.50),
(14, '2026-05-18 14:12:00', 115.00),
(15, '2026-05-28 11:05:00', 119.98),
(16, '2026-06-02 16:30:00', 59.99),
(17, '2026-06-08 10:25:00', 215.49),
(18, '2026-06-12 13:45:00', 89.95),
(19, '2026-06-20 14:00:00', 143.00);
*/

/*
INSERT INTO order_items (order_id, product_id, quantity, unit_price) VALUES
(1, 1, 1, 249.99),
(2, 5, 1, 149.00),
(2, 14, 1, 24.50),
(3, 6, 1, 199.99),
(4, 7, 1, 29.99),
(4, 8, 1, 45.00),
(5, 10, 1, 349.99),
(6, 2, 1, 120.00),
(6, 3, 1, 25.50),
(7, 11, 1, 32.00),
(8, 13, 1, 79.99),
(8, 9, 1, 185.00),
(9, 9, 1, 185.00),
(10, 14, 1, 24.50),
(10, 17, 1, 18.00),
(11, 1, 1, 249.99),
(11, 5, 1, 149.00), 
(12, 20, 1, 499.99),
(13, 12, 1, 65.00),
(14, 3, 1, 25.50),
(15, 19, 1, 115.00),
(16, 18, 1, 59.99),
(16, 18, 1, 59.99),
(17, 18, 1, 59.99),
(18, 16, 1, 19.99),
(18, 6, 1, 199.99),
(19, 4, 1, 89.95),
(20, 8, 1, 45.00),
(20, 2, 1, 98.00);
*/

# SAMPLE QUERIES

-- 1. 
INSERT INTO customers (first_name, last_name, email) 
VALUES ('Alice', 'Smith', 'alice.smith@email.com');

-- 2. 
INSERT INTO categories (category_name, description) 
VALUES ('Electronics', 'Gadgets and devices.');

-- 3. 
INSERT INTO products (product_name, category_id, price, stock_quantity) 
VALUES ('Wireless Mouse', 1, 25.50, 50);

-- 4. 
UPDATE products SET price = 19.99 WHERE product_id = 10; 

-- 5. 
UPDATE products SET stock_quantity = stock_quantity + 10 WHERE category_id = 2;

-- 6. 
UPDATE customers SET email = 'new.email@example.com' WHERE customer_id = 5;

-- 7. 
DELETE FROM products WHERE product_id = 15;

-- 8. 
DELETE FROM orders WHERE total_amount = 0;

-- 9. 
SELECT * FROM products WHERE price > 100.00;

-- 10.
SELECT * FROM customers WHERE last_name LIKE 'M%';

-- 11. 
SELECT * FROM orders WHERE order_date BETWEEN '2026-01-01' AND '2026-06-30';

-- 12. 
SELECT * FROM products WHERE stock_quantity BETWEEN 1 AND 10 AND category_id = 3;

-- 13. 
SELECT * FROM order_items WHERE quantity > 5 OR unit_price < 15.00;

-- 14.
SELECT COUNT(*) FROM customers;

-- 15. 
SELECT MAX(price), MIN(price) FROM products;

-- 16. 
SELECT AVG(total_amount) FROM orders;

-- 17. 
SELECT SUM(total_amount) FROM orders;

-- 18. 
SELECT COUNT(*) FROM order_items WHERE quantity > 1;

-- 19. 
SELECT AVG(unit_price) FROM order_items;

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

