# SQL COMMANDS -- DDL, DML, DCL, TCL

DDL, DML, DCL, and TCL are the four primary functional categories of commands used in Structured Query Language (SQL) to manage relational databases. There is also a fifth closely related category known as DQL (Data Query Language). [1, 2, 3]
Here is a quick overview of how these command groups break down:
Category [1, 2, 3, 4, 5, 6]
Full Name
Primary Purpose
Common Commands
DDL
Data Definition Language
Manages the structural schema of the database.
CREATE, ALTER, DROP, TRUNCATE
DML
Data Manipulation Language
Manages the actual records stored inside the tables.
INSERT, UPDATE, DELETE
DQL
Data Query Language
Retrieves or reads data from the database.
SELECT
DCL
Data Control Language
Manages user access, security, and permissions.
GRANT, REVOKE
TCL
Transaction Control Language
Manages multi-step transaction execution and rollback safety.
COMMIT, ROLLBACK, SAVEPOINT


🔧 1. DDL (Data Definition Language)
DDL commands deal exclusively with the blueprint or structural schema of your database. They define how tables, indexes, and views are built. [1, 2, 3]
CREATE: Builds a brand-new database object, like a table or a view.
ALTER: Modifies the structure of an existing database table (e.g., adding or removing a column).
DROP: Deletes a table or database permanently from the system.
TRUNCATE: Completely empties a table of all its records but leaves the physical table shell intact. [1, 2, 3]
✍️ 2. DML (Data Manipulation Language) [1, 2]
DML commands work directly with the rows of data stored inside your existing table structures. [1, 2] – CRUD
INSERT: Adds new rows or records to a table.
SELECT: Read data from a table
UPDATE: Modifies existing data fields within a table.
DELETE: Removes specific rows from a table based on a condition. [1, 2]
(Note: While some educational systems group SELECT under DML, it is officially classified on its own as DQL because it only reads data without modifying it.) [1, 2, 3, 4]
🔒 3. DCL (Data Control Language)
DCL commands act as the security framework for your database management system. Database Administrators (DBAs) use them to control who has permission to view or edit specific data. [1, 2, 3]
GRANT: Gives a user or role specific privileges to access or modify database objects.
REVOKE: Withdraws previously assigned permissions from a specific user. [1, 2]
⚡ 4. TCL (Transaction Control Language) [1, 2, 3]
TCL commands manage changes made by DML commands by grouping them into safe operations called transactions. They ensure data stays accurate, preventing a script from breaking halfway through a critical step (like a bank transfer). [1, 2, 3, 4]
COMMIT: Saves all changes made during the current transaction permanently to the database.
ROLLBACK: Undoes changes and reverts the data back to its last saved state if an error happens.
SAVEPOINT: Sets a temporary checkpoint within a transaction so you can partially roll back to it if needed. [1, 2, 3, 4]

# REFERENCES

[DDL, DQL, DML, DCL and TCL Commands - SQL](https://www.geeksforgeeks.org/sql/sql-ddl-dql-dml-dcl-tcl-commands/)
