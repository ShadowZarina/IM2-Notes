# COVERAGE

## 1. Data Definition Language (DDL)
- **CREATE**: Defining and establishing new tables.
- **DROP**: Removing existing tables completely from the database.
- **ALTER**: Modifying the structure of an existing table (e.g., adding, deleting, or modifying columns).
- **TRUNCATE**: Deleting all data rows within a table while preserving its structure.

## 2. Data Manipulation Language (DML) – Table Modifications
- **INSERT**: Appending new rows of records into a table.
- **DELETE**: Removing specific rows of records from a table.
- **UPDATE**: Modifying existing data values within a table.

## 3. Data Manipulation Language (DML) – Single-Table Queries
- **SELECT** Statement: Retrieving and displaying specific data columns.
- **Arithmetic** Expressions: Utilizing mathematical operators within query clauses.
- Comparison and Logical Operators: Filtering criteria using **comparison operations (e.g., =, <, >, !=) and logical combinations (AND, OR, NOT)**.
- Restricting Rows: Implementing precise conditional filtering using the **WHERE** clause.
- Sorting Rows: Ordering output results sequentially using the **ORDER BY** clause (Ascending/Descending).
- SQL Built-in Functions: Applying **standard built-in SQL functions** to handle and transform data outputs.

- -----------------

# ADDITIONAL NOTES

## 1. Arithmetic Expressions
- Arithmetic Expressions: +, -, *, /, %
  
## 2. Additional Operations/Functions
- IN/NOT IN
- **FOREIGN KEY**: FOREIGN KEY (customer_id) REFERENCES customers(customer_id);

### CONSTRAINTS
- PRIMARY KEY
- FOREIGN KEY: FOREIGN KEY (customer_id) REFERENCES customers(customer_id);
- UNIQUE
- NOT NULL
- DEFAULT
- CHECK

### DATABASE STATEMEBTS
- CREATE DATABASE:
```
CREATE DATABASE IF NOT EXISTS db_name;
USE db_name;
```

- RENAME DATABASE (doesn't directly exist, must move tables to new database):
```
-- Move each table (Repeat for every table)
RENAME TABLE old_db_name.table_name TO new_db_name.table_name;

-- Drop the old database
DROP DATABASE old_db_name;
```

- DROP DATABASE: DROP DATABASE db_name;

### TABLE STATEMENTS
- ADD TABLE: CREATE TABLE table_name ();
- DROP TABLE: DROP TABLE table_name;
- UPDATE TABLE: UPDATE table SET column = value WHERE condition;
- TRUNCATE TABLE (delete data): TRUNCATE TABLE table
- RENAME TABLE: RENAME TABLE old_table_name TO new_table_name;

### COLUMN STATEMENTS
- ADD COLUMN: ALTER TABLE table_name ADD COLUMN column_name TYPE;
- DROP COLUMN: ALTER TABLE table_name DROP COLUMN column_name;
- MODIFY COLUMN: ALTER TABLE table_name MODIFY COLUMN column_name TYPE;
- RENAME COLUMN: ALTER TABLE table_name RENAME COLUMN old_name TO new_name;

## 3. Standard Built-in SQL Functions
   - Aggregate Functions
   - String (Scalar) Functions
   - Numeric & Math Functions
   - Date & Time Functions
   - Advanced & Conditional Functions

### a. Aggregate Functions<br>
These functions compress data from multiple rows into a single summary value and are heavily utilized alongside GROUP BY clauses.
- COUNT(): Counts the number of rows or non-null values.
- SUM(): Calculates the total addition of a numeric column.
- AVG(): Computes the average value of a numeric column.
- MIN(): Returns the lowest value in a set.
- MAX(): Returns the highest value in a set.

### b. String (Scalar) Functions<br>
Used to inspect, modify, format, and slice textual data strings.
- UPPER() / LOWER(): Converts characters to all uppercase or lowercase.TRIM(): Removes leading and trailing whitespace from a text block.
- CONCAT(): Chains two or more individual text strings together.
- SUBSTRING() (or SUBSTR): Extracts a specific portion of text from a string.
- LENGTH() (or LEN): Counts and returns the total character length of a string.
- REPLACE(): Swaps specific text patterns inside a string with alternative text.

### c. Numeric & Math Functions<br>
Designed to perform math equations, rounding tasks, and numerical data modifications.
- ROUND(): Rounds a number to a specified number of decimal places.
- CEIL() / CEILING(): Rounds a fraction up to the nearest integer value.
- FLOOR(): Rounds a fraction down to the nearest integer value.
- ABS(): Returns the absolute (positive) value of any given number.
- MOD(): Evaluates and returns the remainder of a division operation.

### d. Date & Time Functions<br>
Help capture, manipulate, shift, and isolate calendar dates and timestamps.
- CURRENT_DATE (or CURDATE): Displays the current calendar system date.
- CURRENT_TIMESTAMP (or NOW): Yields the current exact date and system clock time.
- EXTRACT() (or YEAR/MONTH/DAY): Pulls isolated individual parts from a datetime value.
- DATEDIFF(): Measures the duration gap or number of days between two dates.

### e. Advanced & Conditional Functions<br>
These functions inspect data logical structures or safely swap out missing values.
- COALESCE(): Scans a sequence of inputs and returns the very first non-null value.
- NULLIF(): Evaluates two values, returning a null if they are completely identical.
- CAST(): Forces a value to safely convert into a completely different database datatype.

# REFERENCES
[SQL Server Functions](https://www.w3schools.com/sql/sql_ref_sqlserver.asp)

------------------

1. MySQL String Functions
String functions in MySQL are used to manipulate and analyze text data stored in string columns. Common string operations include extracting substrings, converting cases, concatenating strings, and searching for specific patterns within a string.

Common String Functions
1.1 CONCAT()
The CONCAT() function is used to combine two or more strings into a single string.

Syntax:
1	SELECT CONCAT(string1, string2, ...);
2	
Example:
Concatenate a customer’s first name and last name.

1	SELECT CONCAT(first_name, ' ', last_name) AS full_name
2	FROM customers;
3	
1.2 LENGTH()
The LENGTH() function returns the length of a string (in bytes).

Syntax:
1	SELECT LENGTH(string);
2	
Example:
Get the length of a customer’s email address.

1	SELECT LENGTH(email) AS email_length
2	FROM customers;
3	
1.3 LOWER() and UPPER()
The LOWER() function converts a string to lowercase, while the UPPER() function converts a string to uppercase.

Syntax:
1	SELECT LOWER(string);
2	SELECT UPPER(string);
3	
Example:
Convert a customer’s name to uppercase.

1	SELECT UPPER(first_name) AS uppercase_name
2	FROM customers;
3	
1.4 SUBSTRING()
The SUBSTRING() function extracts a part of a string, starting from a specified position and optionally for a specified length.

Syntax:
1	SELECT SUBSTRING(string, start_position, length);
2	
Example:
Extract the first three characters from a customer’s first name.

1	SELECT SUBSTRING(first_name, 1, 3) AS short_name
2	FROM customers;
3	
1.5 TRIM()
The TRIM() function removes leading and trailing spaces from a string.

Syntax:
1	SELECT TRIM(string);
2	
Example:
Trim whitespace from a customer’s name.

1	SELECT TRIM(first_name) AS trimmed_name
2	FROM customers;
3	
1.6 REPLACE()
The REPLACE() function replaces all occurrences of a substring within a string with another substring.

Syntax:
1	SELECT REPLACE(string, search_string, replacement_string);
2	
Example:
Replace all instances of 'gmail' with 'outlook' in email addresses.

1	SELECT REPLACE(email, 'gmail', 'outlook') AS updated_email
2	FROM customers;
3	
2. MySQL Numeric Functions
Numeric functions allow you to perform mathematical calculations and manipulate numeric data in SQL queries. These functions include operations for rounding numbers, calculating sums, and generating random values.

Common Numeric Functions
2.1 ABS()
The ABS() function returns the absolute value of a number.

Syntax:
1	SELECT ABS(number);
2	
Example:
Get the absolute value of a negative transaction amount.

1	SELECT ABS(transaction_amount) AS absolute_amount
2	FROM transactions;
3	
2.2 ROUND()
The ROUND() function rounds a number to a specified number of decimal places.

Syntax:
1	SELECT ROUND(number, decimal_places);
2	
Example:
Round a product price to two decimal places.

1	SELECT ROUND(price, 2) AS rounded_price
2	FROM products;
3	
2.3 CEIL() and FLOOR()
The CEIL() function rounds a number up to the nearest integer, while the FLOOR() function rounds a number down to the nearest integer.

Syntax:
1	SELECT CEIL(number);
2	SELECT FLOOR(number);
3	
Example:
Round a product price up and down.

1	SELECT CEIL(price) AS ceiling_price, FLOOR(price) AS floor_price
2	FROM products;
3	
2.4 MOD()
The MOD() function returns the remainder of a division operation.

Syntax:
1	SELECT MOD(number1, number2);
2	
Example:
Find the remainder when dividing a quantity by a number.

1	SELECT MOD(quantity, 5) AS remainder
2	FROM inventory;
3	
2.5 POW()
The POW() function raises a number to a specified power (exponent).

Syntax:
1	SELECT POW(base, exponent);
2	
Example:
Calculate the square of a number.

1	SELECT POW(4, 2) AS square;
2	
2.6 RAND()
The RAND() function generates a random decimal value between 0 and 1.

Syntax:
1	SELECT RAND();
2	
Example:
Generate a random value for a promotional discount.

1	SELECT RAND() * 100 AS discount;
2	
3. MySQL Date Functions
Date functions allow you to manipulate and format date and time values. These functions are useful for calculating intervals, extracting parts of a date, and formatting dates.

Common Date Functions
3.1 CURDATE()
The CURDATE() function returns the current date.

Syntax:
1	SELECT CURDATE();
2	
Example:
Retrieve the current date.

1	SELECT CURDATE() AS current_date;
2	
3.2 NOW()
The NOW() function returns the current date and time.

Syntax:
1	SELECT NOW();
2	
Example:
Retrieve the current date and time.

1	SELECT NOW() AS current_datetime;
2	
3.3 DATE_FORMAT()
The DATE_FORMAT() function formats a date according to a specified format.

Syntax:
1	SELECT DATE_FORMAT(date, format);
2	
Example:
Format an order date as 'Month Day, Year'.

1	SELECT DATE_FORMAT(order_date, '%M %d, %Y') AS formatted_date
2	FROM orders;
3	
3.4 DATEDIFF()
The DATEDIFF() function returns the difference between two dates, measured in days.

Syntax:
1	SELECT DATEDIFF(date1, date2);
2	
Example:
Calculate the number of days between an order date and the current date.

1	SELECT DATEDIFF(CURDATE(), order_date) AS days_since_order
2	FROM orders;
3	
3.5 DATE_ADD()
The DATE_ADD() function adds a specified time interval to a date.

Syntax:
1	SELECT DATE_ADD(date, INTERVAL value unit);
2	
Example:
Add 30 days to an order date to calculate the delivery deadline.

1	SELECT DATE_ADD(order_date, INTERVAL 30 DAY) AS delivery_deadline
2	FROM orders;
3	
3.6 EXTRACT()
The EXTRACT() function extracts a specific part of a date (such as the year, month, or day).

Syntax:
1	SELECT EXTRACT(part FROM date);
2	
Example:
Extract the year from a customer’s registration date.

1	SELECT EXTRACT(YEAR FROM registration_date) AS registration_year
2	FROM customers;
3	
