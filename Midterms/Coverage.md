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
- UPDATE TABLE: UPDATE table SET column = value WHERE

### COLUMN STATEMENTS
- ADD COLUMN: ALTER TABLE table_name ADD column_name TYPE;
- DROP COLUMN: ALTER TABLE table_name DROP COLUMN column_name;
- MODIFY COLUMN: ALTER TABLE table_name MODIFY column_name TYPE;
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
- AVG(): Computes the average value of a numeric column.MIN(): Returns the lowest value in a set.
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
