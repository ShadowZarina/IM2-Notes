# SQL OPERATORS

SQL operators are keywords and symbols used to perform operations with data values.

SQL operators are used in SQL statements like SELECT, WHERE, LIKE, etc.

SQL operators is categorized into the following types:

Arithmetic operators
Comparison operators
Compound operators
Bitwise operators
Logical operators
SQL Arithmetic Operators
Operator	Description	Example
+	Addition	
-	Subtraction	
*	Multiplication	
/	Division	
%	Modulus	
SQL Comparison Operators
Operator	Description	Example
=	Equal to	
>	Greater than	
<	Less than	
>=	Greater than or equal to	
<=	Less than or equal to	
<>	Not equal to	
REMOVE ADS

SQL Compound Operators
Operator	Description
+=	Add equals
-=	Subtract equals
*=	Multiply equals
/=	Divide equals
%=	Modulo equals
&=	Bitwise AND equals
^=	Bitwise exclusive equals
|*=	Bitwise OR equals
SQL Bitwise Operators
Operator	Description
&	Bitwise AND
|	Bitwise OR
^	Bitwise exclusive OR
~	Bitwise NOT
SQL Logical Operators
Operator	Description	Example
ALL	TRUE if all of the subquery values meet the condition	
AND	TRUE if all the conditions separated by AND is TRUE	
ANY	TRUE if any of the subquery values meet the condition	
BETWEEN	TRUE if the operand is within the range of comparisons	
EXISTS	TRUE if the subquery returns one or more records	
IN	TRUE if the operand is equal to one of a list of expressions	
LIKE	TRUE if the operand matches a pattern	
NOT	Displays a record if the condition(s) is NOT TRUE	
OR	TRUE if any of the conditions separated by OR is TRUE	
SOME	TRUE if any of the subquery values meet the condition

# REFERENCE

[SQL Operators](https://www.w3schools.com/sql/sql_operators.asp)

# EXAMPLE SYNTAX

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


[SQL Operators](https://www.w3schools.com/sql/sql_operators.asp)
*/
