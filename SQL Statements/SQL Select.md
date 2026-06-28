# SQL SELECT

[SQL SELECT Statement](https://www.w3schools.com/sql/sql_select.asp)

The SQL SELECT Statement
The SELECT statement is used to select data from a database.

ExampleGet your own SQL Server
Return data from the Customers table:

SELECT CustomerName, City FROM Customers;
SELECT Syntax
SELECT column1, column2, ...
FROM table_name;

Here, column1, column2, ... are the column names in the table you want to select data from.

The table_name represents the name of the table you want to select data from.

# EXAMPLE 1
Below is a selection from the Customers table used in the examples:

CustomerID	CustomerName	ContactName	Address	City	PostalCode	Country
1

Alfreds Futterkiste	Maria Anders	Obere Str. 57	Berlin	12209	Germany
2	Ana Trujillo Emparedados y helados	Ana Trujillo	Avda. de la Constitución 2222	México D.F.	05021	Mexico
3	Antonio Moreno Taquería	Antonio Moreno	Mataderos 2312	México D.F.	05023	Mexico
4

Around the Horn	Thomas Hardy	120 Hanover Sq.	London	WA1 1DP	UK
5	Berglunds snabbköp	Christina Berglund	Berguvsvägen 8	Luleå	S-958 22	Sweden
REMOVE ADS

Select ALL Columns
To select ALL columns, without specifying every column name, use the SELECT * syntax:

Example
Select ALL columns from the "Customers" table:

SELECT * FROM Customers;

# EXAMPLE 2

```
-- DROP TABLE IF EXISTS CustomerInfo


create table CustomerInfo (
  CustID int not null primary key auto_increment,
  CustomerFName varchar(30) not null,
  CustomerLName varchar(30) not null,
  City varchar(30) not null,
  Country varchar(30) not null
);


insert into CustomerInfo (CustomerFName, CustomerLName, City, Country)
values
('John','Cardinal','Stavanger','Norway'),
('James','Cardinal','Taipei','Taiwan'),
('Jason','Jones','Paris','France'),
('Jenny','Warner','Tokyo','Japan'),
('Jake','Jenner','Rome','Italy');


-- SELECT * FROM CustomerInfo;
SELECT CustomerFName, CustomerLName FROM CustomerInfo;
SELECT * FROM CustomerInfo WHERE CustID = 3;
```

```
-- DROP TABLE IF EXISTS CustomerInfo


create table CustomerInfo (
  CustID int not null primary key auto_increment,
  CustomerFName varchar(30) not null,
  CustomerLName varchar(30) not null,
  City varchar(30) not null,
  Country varchar(30) not null,
  Age int not null
);


insert into CustomerInfo (CustomerFName, CustomerLName, City, Country, Age)
values
('John','Cardinal','Stavanger','Norway', 30),
('James','Cardinal','Taipei','Taiwan', 25),
('Jason','Jones','Paris','France', 22),
('Jenny','Warner','Tokyo','Japan', 31),
('Jake','Jenner','Rome','Italy', 19);


SELECT CustomerFName, CustomerLName, MAX(Age) FROM CustomerInfo;


/*
ALTER TABLE CustomerInfo ADD COLUMN Age int not null;


-- How to add the age values for all records after executing the alter table query?
UPDATE TABLE CustomerInfo SET Age = 30 WHERE CustID = 1;
UPDATE TABLE CustomerInfo SET Age = 25 WHERE CustID = 2;
UPDATE TABLE CustomerInfo SET Age = 22 WHERE CustID = 3;
UPDATE TABLE CustomerInfo SET Age = 31 WHERE CustID = 4;
UPDATE TABLE CustomerInfo SET Age = 19 WHERE CustID = 5;


SELECT * FROM CustomerInfo;
*/
```


# EXAMPLE 3

```
/*
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
*/
```

