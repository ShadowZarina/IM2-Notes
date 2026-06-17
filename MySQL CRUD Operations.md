CRUD operations—Create, Read, Update, and Delete—are the four fundamental operations for managing data in a relational database like MySQL. These operations allow you to insert new data into a database, retrieve and display data, modify existing data, and remove unwanted data. Understanding how to perform CRUD operations using Structured Query Language (SQL) is essential for interacting with MySQL databases.

This topic will cover each CRUD operation in detail, along with SQL queries and practical examples to demonstrate how to work with data in MySQL.

# What are CRUD Operations?
CRUD stands for Create, Read, Update, and Delete. These operations form the basic foundation for working with any data in a MySQL database:

- Create: Inserting new data into tables.
- Read: Retrieving and displaying data from tables.
- Update: Modifying existing data in tables.
- Delete: Removing data from tables.

## 1. Create: Inserting Data into Tables
The CREATE operation is used to insert new records into a table. This is achieved using the INSERT INTO statement, specifying the table name, column names, and the values to be inserted.

Syntax:
1	INSERT INTO table_name (column1, column2, column3, ...)
2	VALUES (value1, value2, value3, ...);

Example:
Let’s insert data into a Customers table.

1	INSERT INTO customers (customer_id, name, email, phone)
2	VALUES (1, 'John Smith', 'john@example.com', '555-1234');

customer_id	name	email	phone
1	John Smith	john@example.com	555-1234
Inserting Multiple Rows:
You can insert multiple rows in one query.

1	INSERT INTO customers (customer_id, name, email, phone)
2	VALUES
3	(2, 'Jane Doe', 'jane@example.com', '555-5678'),
4	(3, 'Alex Turner', 'alex@example.com', '555-8765');

## 2. Read: Retrieving Data from Tables
The READ operation is used to query and retrieve data from a table. This is done using the SELECT statement. You can specify which columns to display, apply conditions using the WHERE clause, and sort results using the ORDER BY clause.

Syntax:
1	SELECT column1, column2, column3, ...
2	FROM table_name
3	WHERE condition
4	ORDER BY column_name;

Example:
Retrieve all customer records from the Customers table.

1	SELECT * FROM customers;

customer_id	name	email	phone
1	John Smith	john@example.com	555-1234
2	Jane Doe	jane@example.com	555-5678
3	Alex Turner	alex@example.com	555-8765
Reading Specific Columns:
Retrieve only the name and email columns.

1	SELECT name, email FROM customers;

Using the WHERE Clause:
Retrieve customer information for a specific customer.

1	SELECT * FROM customers WHERE customer_id = 1;

Sorting Results:
Retrieve all customers and sort them by name in ascending order.

1	SELECT * FROM customers ORDER BY name ASC;

## 3. Update: Modifying Existing Data
The UPDATE operation is used to modify existing records in a table. The UPDATE statement allows you to change values in one or more columns, using the SET clause to specify the new values and the WHERE clause to limit which rows are updated.

Syntax:
1	UPDATE table_name
2	SET column1 = value1, column2 = value2, ...
3	WHERE condition;

Example:
Update the email address for the customer with customer_id = 1.

1	UPDATE customers
2	SET email = 'john.smith@example.com'
3	WHERE customer_id = 1;

customer_id	name	email	phone
1	John Smith	john.smith@example.com	555-1234
Updating Multiple Columns:
Update both the email and phone number for customer_id = 2.

1	UPDATE customers
2	SET email = 'jane.doe@example.com', phone = '555-4321'
3	WHERE customer_id = 2;

Updating Multiple Rows:
Update the phone number for all customers whose name contains 'Smith'.

1	UPDATE customers
2	SET phone = '555-0000'
3	WHERE name LIKE '%Smith%';

## 4. Delete: Removing Data from Tables
The DELETE operation removes rows from a table. The DELETE FROM statement is used to specify which rows to delete, using the WHERE clause to target specific records.

Syntax:
1	DELETE FROM table_name
2	WHERE condition;

Example:
Delete the customer with customer_id = 1.

1	DELETE FROM customers
2	WHERE customer_id = 1;

Deleting Multiple Rows:
Delete all customers whose name is 'Jane Doe'.

1	DELETE FROM customers
2	WHERE name = 'Jane Doe';

Deleting All Rows:
To delete all rows from a table (while keeping the table structure intact), use the DELETE statement without a WHERE clause.

1	DELETE FROM customers;

Alternatively, use TRUNCATE to achieve the same result more efficiently.

1	TRUNCATE TABLE customers;

# Best Practices for CRUD Operations in MySQL
Use WHERE Clause Carefully: When updating or deleting data, always use the WHERE clause to target specific rows. Failure to do so can result in modifying or deleting all rows.
Backup Data: Before performing mass updates or deletions, create a backup of the affected tables or data to avoid accidental loss.
Use Transactions for Safety: For critical updates or deletes, wrap the operations inside a transaction to ensure data consistency.
Use Parameterized Queries: When working with user input, use parameterized queries to prevent SQL injection attacks.
Limit Data When Reading: Use LIMIT and OFFSET clauses when retrieving large datasets to improve query performance.

Example Scenario: Managing Customer Data
Create: Insert new customers into the database.
1	INSERT INTO customers (customer_id, name, email, phone)
2	VALUES (1, 'John Smith', 'john.smith@example.com', '555-1234'),
3	       (2, 'Jane Doe', 'jane.doe@example.com', '555-5678');

Read: Retrieve all customer records.
1	SELECT * FROM customers;

Update: Update the phone number for customer_id = 1.
1	UPDATE customers
2	SET phone = '555-0000'
3	WHERE customer_id = 1;

Delete: Remove the customer with customer_id = 2.
1	DELETE FROM customers
2	WHERE customer_id = 2;

# ALTER TABLE Statement

SQL ALTER TABLE Statement
The ALTER TABLE statement is used to add, delete, or modify columns in an existing table.

The ALTER TABLE statement is also used to add and drop various constraints on an existing table.

Common ALTER TABLE operations are:

Add column - Adds a new column to a table
Drop column - Deletes a column in a table
Rename column - Renames a column
Modify column - Changes the data type, size, or constraints of a column
Add constraint - Adds a new constraint
Rename table - Renames a table
ALTER TABLE - ADD Column
To add a column in a table, use the following syntax:

Syntax
ALTER TABLE table_name
ADD column_name datatype;
The following SQL adds an "Email" column to the "Customers" table:

ExampleGet your own SQL Server
ALTER TABLE Customers
ADD Email varchar(255);
ALTER TABLE - DROP COLUMN
To delete a column in a table, use the following syntax (notice that some database systems don't allow deleting a column):

Syntax
ALTER TABLE table_name
DROP COLUMN column_name;
The following SQL deletes the "Email" column from the "Customers" table:

Example
ALTER TABLE Customers
DROP COLUMN Email;
ALTER TABLE - RENAME COLUMN
To rename a column in a table, use the following syntax:

Syntax
ALTER TABLE table_name
RENAME COLUMN old_name to new_name;
To rename a column in a table in SQL Server, use the following syntax:

Syntax for SQL Server:
EXEC sp_rename 'table_name.old_name', 'new_name', 'COLUMN';
REMOVE ADS

ALTER TABLE - MODIFY Datatype
To modify the data type, size or constraints of a column in a table, use the following syntax:

Syntax for SQL Server / MS Access:
ALTER TABLE table_name
ALTER COLUMN column_name new_datatype constraint;
Syntax for MySQL / Oracle:
ALTER TABLE table_name
MODIFY column_name new_datatype constraint;
The following SQL modifies the size of the "Email" column to varchar(100), and we also add a NOT NULL constraint:

Example
ALTER TABLE Customers
MODIFY Email varchar(100) NOT NULL;
ALTER TABLE - ADD CONSTRAINT
To add a constraint to an existing table, use the following syntax:

Syntax
ALTER TABLE table_name
ADD CONSTRAINT constraint_name constraint_definition;
The following SQL adds a constraint named "CHK_Age" that is a CHECK constraint that ensures that the "Age" column has a value of 18 and above:

Example
ALTER TABLE Members
ADD CONSTRAINT CHK_Age CHECK (Age >= 18);
ALTER TABLE - Rename table
To rename a table, use the following syntax:

Syntax
ALTER TABLE table_name
RENAME TO new_table_name;
The following SQL renames the "Customers" table to "Clients":

Example
ALTER TABLE Customers
RENAME TO Clients;
REMOVE ADS

SQL ALTER TABLE Example
Assume we have a "Persons" table, that looks like this:

ID	LastName	FirstName	Address	City
1	Hansen	Ola	Timoteivn 10	Sandnes
2	Svendson	Tove	Borgvn 23	Sandnes
3	Pettersen	Kari	Storgt 20	Stavanger
Now we want to add a column named "DateOfBirth" in the "Persons" table.

We use the following SQL statement:

Example
ALTER TABLE Persons
ADD DateOfBirth date;
Notice that the new column, "DateOfBirth", is of type date and is going to hold a date. The data type specifies what type of data the column can hold. For a complete reference of all the data types available in MS Access, MySQL, and SQL Server, go to our complete Data Types reference.

The "Persons" table will now look like this:

ID	LastName	FirstName	Address	City	DateOfBirth
1	Hansen	Ola	Timoteivn 10	Sandnes	 
2	Svendson	Tove	Borgvn 23	Sandnes	 
3	Pettersen	Kari	Storgt 20	Stavanger	 
Change Data Type Example
Now we want to change the data type of the column named "DateOfBirth" in the "Persons" table.

We use the following SQL statement:

Example
ALTER TABLE Persons
ALTER COLUMN DateOfBirth year;
Notice that the "DateOfBirth" column is now of type year and is going to hold a year in a two- or four-digit format.

DROP COLUMN Example
Next, we want to delete the column named "DateOfBirth" in the "Persons" table.

We use the following SQL statement:

Example
ALTER TABLE Persons
DROP COLUMN DateOfBirth;

# INSERT INTO Statement

The INSERT INTO statement is used to insert new records in a table.

It is possible to write the INSERT INTO statement in two ways:

Syntax 1
Specify both the column names and the values to be inserted:

INSERT INTO table_name (column1, column2, column3, ...)
VALUES (value1, value2, value3, ...);

Syntax 2
If you insert values for ALL the columns of the table, you can omit the column names.

However, the order of the values must be in the same order as the columns in the table:

INSERT INTO table_name
VALUES (value1, value2, value3, ...);

Demo Database
Below is a selection from the Customers table used in the examples:

CustomerID	CustomerName	ContactName	Address	City	PostalCode	Country
89	White Clover Markets	Karl Jablonski	305 - 14th Ave. S. Suite 3B	Seattle	98128	USA
90

Wilman Kala	Matti Karttunen	Keskuskatu 45	Helsinki	21240	Finland
91

Wolski	Zbyszek	ul. Filtrowa 68	Walla	01-012	Poland

REMOVE ADS

INSERT INTO Example
Here we insert values for ALL the columns of the table, so we omit the column names.

The following SQL inserts a new record in the "Customers" table:

ExampleGet your own SQL Server
INSERT INTO Customers
VALUES ('Cardinal', 'Tom B. Erichsen', 'Skagen 21', 'Stavanger', '4006', 'Norway');
The last record in the "Customers" table will now look like this:

CustomerID	CustomerName	ContactName	Address	City	PostalCode	Country
92	Cardinal	Tom B. Erichsen	Skagen 21	Stavanger	4006	Norway
Notice that we did not insert any number into the CustomerID field!

The CustomerID column is an auto-increment field and will be automatically generated when a new record is inserted.

Insert Data Only in Specific Columns
Here we insert values only in some specific columns of the table.

The following SQL inserts a new record - but only inserts data in the "CustomerName", "City", and "Country" columns (CustomerID will be updated automatically):

Example
INSERT INTO Customers (CustomerName, City, Country)
VALUES ('Cardinal', 'Stavanger', 'Norway');
The last record in the "Customers" table will now look like this:

CustomerID	CustomerName	ContactName	Address	City	PostalCode	Country
92	Cardinal	null	null	Stavanger	null	Norway
REMOVE ADS

Insert Multiple Rows
To insert multiple rows of data, we use the same INSERT INTO statement, but with multiple values:

The following SQL inserts three new records in the "Customers" table:

Example
INSERT INTO Customers (CustomerName, ContactName, Address, City, PostalCode, Country)
VALUES
('Cardinal', 'Tom B. Erichsen', 'Skagen 21', 'Stavanger', '4006', 'Norway'),
('Greasy Burger', 'Per Olsen', 'Gateveien 15', 'Sandnes', '4306', 'Norway'),
('Tasty Tee', 'Finn Egan', 'Streetroad 19B', 'Liverpool', 'L1 0AA', 'UK');
Note: Make sure you separate each set of values with a comma ,.
# Conclusion
The CRUD operations—Create, Read, Update, and Delete—are the core functions for interacting with a MySQL database. 
They allow you to manage the data stored in the database effectively. Using the INSERT statement, you can add new records. 
With SELECT, you can retrieve data, apply filters, and sort the results. The UPDATE statement allows you to modify existing data, 
while DELETE helps you remove unwanted records. By mastering these operations, you can efficiently manage the data within your MySQL database.

# References

[SQL ALTER TABLE Statement](https://www.w3schools.com/sql/sql_alter.asp)<br>
[SQL INSERT INTO Statement](https://www.w3schools.com/sql/sql_insert.asp)
