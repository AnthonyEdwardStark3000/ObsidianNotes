# What is a Database?

A database is an organized collection of data used to store, retrieve, update, and manage information efficiently.

### Examples

- Employee Management
    
- Banking Systems
    
- E-commerce Orders
    
- Hospital Records
    

---

# Types of Databases

## 1. Relational Database (RDBMS)

Stores data in the form of tables.

### Features

- Rows and Columns
    
- Relationships using Keys
    
- Structured Schema
    
- SQL Support
    

### Examples

- MySQL
    
- Microsoft SQL Server
    
- PostgreSQL
    
- Oracle Database
    

---

## 2. NoSQL Database

Non-relational databases that store data in flexible formats.

### Types

- Document Database
    
- Key-Value Database
    
- Graph Database
    
- Column-Based Database
    

### Examples

- MongoDB
    
- Redis
    
- Cassandra
    

---

# What is SQL?

SQL = Structured Query Language

Used for:

- Creating tables
    
- Fetching data
    
- Updating data
    
- Deleting data
    
- Managing databases
    

```sql
SELECT * FROM Employees;
```

---

# Table Structure

Example: Employee Table

|EmployeeId|Name|DepartmentId|
|---|---|---|
|1|Suresh|101|
|2|Arun|102|

### Important Terms

- Row → Single Record
    
- Column → Field/Property
    
- Table → Collection of related data
    

---

# Keys in Database

Keys help identify records uniquely and create relationships.

---

# Primary Key

Uniquely identifies each row.

## Rules

- Cannot be NULL
    
- Must be Unique
    
- One Primary Key per table
    

```sql
EmployeeId INT PRIMARY KEY
```

### Example

|EmployeeId|Name|
|---|---|
|1|Suresh|
|2|Arun|

---

# Foreign Key

Used to create relationship between tables.

## Example

### Department Table

|DepartmentId|DepartmentName|
|---|---|
|101|HR|
|102|IT|

### Employee Table

|EmployeeId|Name|DepartmentId|
|---|---|---|
|1|Suresh|101|

Here:  
`DepartmentId` in Employee table is a Foreign Key.

```sql
FOREIGN KEY (DepartmentId)
REFERENCES Department(DepartmentId)
```

## Purpose

- Maintains referential integrity
    
- Prevents invalid references
    

---

# Unique Key

Ensures unique values.

## Difference from Primary Key

- Multiple Unique Keys allowed
    
- Usually allows one NULL value
    

```sql
Email VARCHAR(100) UNIQUE
```

---

# Composite Key

Combination of multiple columns to uniquely identify a record.

```sql
PRIMARY KEY(StudentId, CourseId)
```

---

# Candidate Key

Columns eligible to become Primary Key.

### Example

- Email
    
- AadhaarNumber
    

Both are unique → candidate keys.

---

# Relationships in Database

---

# One-to-One Relationship

One record maps to one record.

### Example

- Person ↔ Passport
    

---

# One-to-Many Relationship

Most commonly used relationship.

### Example

- One Department → Many Employees
    

---

# Many-to-Many Relationship

### Example

- Students ↔ Courses
    

Handled using a Junction Table.

|StudentId|CourseId|
|---|---|

---

# SQL vs NoSQL

|Feature|SQL|NoSQL|
|---|---|---|
|Structure|Table-based|Flexible|
|Schema|Fixed|Dynamic|
|Relationships|Strong|Limited|
|Scaling|Vertical|Horizontal|
|Transactions|ACID|BASE|
|Best For|Structured data|Large scalable systems|

---

# When to Use SQL?

Use SQL databases when:

- Relationships are important
    
- Transactions are critical
    
- Data consistency is required
    

### Examples

- Banking Systems
    
- ERP Applications
    
- Inventory Systems
    

---

# When to Use NoSQL?

Use NoSQL databases when:

- Schema changes frequently
    
- Massive scalability needed
    
- High-speed distributed systems
    

### Examples

- Chat Applications
    
- Logging Systems
    
- Social Media Platforms
    

---

# ACID Properties

Important interview topic.

---

# Atomicity

Transaction either:

- Completes fully
    
- Or rolls back completely
    

### Example

Money transfer transaction.

---

# Consistency

Database remains valid after transaction.

---

# Isolation

Transactions should not affect each other.

---

# Durability

Committed data remains even after crash.

---

# Normalization

Process of reducing redundancy.

## Goals

- Avoid duplicate data
    
- Improve consistency
    
- Reduce anomalies
    

---

# First Normal Form (1NF)

- No repeating groups
    
- Atomic values only
    

---

# Second Normal Form (2NF)

- No partial dependency
    

---

# Third Normal Form (3NF)

- No transitive dependency
    

### Interview Point

Most real-world systems use up to 3NF.

---

# Denormalization

Combining tables intentionally for performance optimization.

### Used In

- Reporting Systems
    
- Analytics
    
- Read-heavy applications
    

---

# MySQL

MySQL

Open-source relational database.

## Features

- Lightweight
    
- Fast
    
- Easy to learn
    
- Popular with web applications
    

## Commonly Used With

- ASP.NET Core
    
- Dapper
    
- Entity Framework Core
    

---

# MySQL Storage Engines

## InnoDB (Default)

- Supports transactions
    
- Supports foreign keys
    
- ACID compliant
    

## MyISAM

- Faster reads
    
- No transactions
    

---

# Microsoft SQL Server

Microsoft SQL Server

Enterprise-level database from [Microsoft](https://www.microsoft.com/sql-server?utm_source=chatgpt.com)

## Features

- Excellent .NET integration
    
- Advanced security
    
- Strong transaction support
    
- High scalability
    

---

# SSMS (SQL Server Management Studio)

SQL Server Management Studio

Tool used to manage SQL Server.

## Used For

- Writing Queries
    
- Backup/Restore
    
- Job Scheduling
    
- Monitoring
    

---

# PostgreSQL

PostgreSQL

Advanced open-source database.

## Features

- Strong SQL compliance
    
- Excellent JSON support
    
- Advanced indexing
    
- High performance
    

### Special Capability

Supports:

- Relational Data
    
- Semi-structured JSON Data
    

---

# Oracle Database

Oracle Database

Enterprise database from [Oracle](https://www.oracle.com/database/?utm_source=chatgpt.com)

## Features

- Massive scalability
    
- High performance
    
- Advanced enterprise tools
    
- Strong security
    

### Commonly Used In

- Banking
    
- Telecom
    
- Large Enterprises
    

---

# Difference Between MySQL, SQL Server, PostgreSQL, Oracle

|Feature|MySQL|SQL Server|PostgreSQL|Oracle|
|---|---|---|---|---|
|Company|Oracle|Microsoft|Community|Oracle|
|Open Source|Yes|Partial|Yes|Mostly No|
|Best For|Web Apps|Enterprise .NET Apps|Advanced Systems|Large Enterprises|
|Cost|Free|Paid/Free Editions|Free|Expensive|
|Learning Curve|Easy|Medium|Medium|Hard|
|JSON Support|Moderate|Good|Excellent|Excellent|

---

# Why All Use SQL But Still Different?

All databases use SQL, but differ because of:

---

# Internal Engine Architecture

Each DB has different:

- Query Optimizer
    
- Storage Engine
    
- Execution Plan
    
- Memory Management
    

---

# Feature Differences

### MySQL

- Lightweight
    
- Faster simple reads
    

### SQL Server

- Best .NET ecosystem integration
    

### PostgreSQL

- Advanced JSON + indexing support
    

### Oracle

- Enterprise clustering and scalability
    

---

# Syntax Differences

## MySQL

```sql
SELECT * FROM Employees LIMIT 10;
```

---

## SQL Server

```sql
SELECT TOP 10 * FROM Employees;
```

---

## PostgreSQL

```sql
SELECT * FROM Employees LIMIT 10;
```

---

## Oracle

```sql
SELECT * FROM Employees FETCH FIRST 10 ROWS ONLY;
```

---

# Indexing

Indexes improve query performance.

---

# Clustered Index

- Physically sorts table data
    
- One per table
    

---

# Non-Clustered Index

- Separate structure storing pointers
    
- Multiple allowed
    

---

# DELETE vs TRUNCATE vs DROP

|Feature|DELETE|TRUNCATE|DROP|
|---|---|---|---|
|Removes|Rows|All Rows|Entire Table|
|WHERE Clause|Allowed|Not Allowed|Not Applicable|
|Rollback|Possible|Limited|Not Possible|
|Structure Deleted|No|No|Yes|

---

# Real-Time Usage for .NET Backend Developer

As a .NET backend developer, you will:

- Design tables
    
- Create relationships
    
- Write optimized SQL queries
    
- Use joins
    
- Handle transactions
    
- Create indexes
    
- Use Dapper or EF Core
    
- Write stored procedures
    
- Optimize performance
    

---

# Important Interview Summary

## SQL Databases

- Structured
    
- Table-based
    
- ACID compliant
    
- Strong relationships
    

---

## NoSQL Databases

- Flexible schema
    
- Horizontally scalable
    
- Best for unstructured data
    

---

## Key Concepts

- Primary Key → Unique identity
    
- Foreign Key → Relationship
    
- Unique Key → Enforces uniqueness
    

---

## Popular Databases

### MySQL

- Lightweight
    
- Easy to learn
    
- Popular for APIs
    

### SQL Server

- Best with .NET ecosystem
    

### PostgreSQL

- Advanced modern backend systems
    

### Oracle

- Enterprise-grade applications
# SQL Interview Notes — Database Commands (Obsidian Friendly)

---

# SQL Command Categories

SQL commands are mainly divided into 5 categories:

|Category|Full Form|Purpose|
|---|---|---|
|DDL|Data Definition Language|Structure related operations|
|DML|Data Manipulation Language|Data modification|
|DQL|Data Query Language|Fetching data|
|DCL|Data Control Language|Permissions and access|
|TCL|Transaction Control Language|Transaction handling|

---

# 1. DDL — Data Definition Language

Used to define or modify database structure.

---

# CREATE DATABASE

Used to create a new database.

```sql
CREATE DATABASE stores;
```

## Similar Queries

```sql
CREATE DATABASE company;
```

```sql
CREATE DATABASE employee_management;
```

---

# USE DATABASE

Selects the database for current operations.

```sql
USE stores;
```

## Similar Queries

```sql
USE company;
```

---

# ALTER DATABASE

Used to modify database properties.

```sql
ALTER DATABASE stores READ ONLY = 0;
```

## Meaning

- `0` → Read and Write allowed
    
- `1` → Read-only mode
    

---

# DROP DATABASE

Deletes the entire database permanently.

```sql
DROP DATABASE stores;
```

## Similar Queries

```sql
DROP DATABASE company;
```

---

# Important Interview Difference

|Command|Purpose|
|---|---|
|DELETE|Deletes rows|
|TRUNCATE|Removes all rows|
|DROP|Deletes complete object|

---

# CREATE TABLE

Used to create a table.

```sql
CREATE TABLE Employees(
    _id INT PRIMARY KEY,
    Name VARCHAR(100),
    Age INT,
    Email VARCHAR(200)
);
```

---

# Important Datatypes

|Datatype|Purpose|
|---|---|
|INT|Integer values|
|VARCHAR|Variable-length string|
|DATE|Stores date|
|DECIMAL|Decimal numbers|

---

# Another CREATE TABLE Example

```sql
CREATE TABLE Employees(
    emp_id INT PRIMARY KEY,
    emp_name VARCHAR(50),
    salary DECIMAL(7,2),
    join_date DATE
);
```

---

# ALTER TABLE

Used to modify existing table structure.

---

# Rename Column

```sql
ALTER TABLE Employees
RENAME COLUMN _id TO emp_id;
```

## Similar Query

```sql
ALTER TABLE Employees
RENAME COLUMN Name TO emp_name;
```

---

# Modify Column

Used to change datatype or size.

```sql
ALTER TABLE Employees
MODIFY COLUMN emp_name VARCHAR(50);
```

## Similar Queries

```sql
ALTER TABLE Employees
MODIFY COLUMN salary DECIMAL(10,2);
```

```sql
ALTER TABLE Employees
MODIFY COLUMN Email VARCHAR(255);
```

---

# DROP COLUMN

Removes columns from table.

```sql
ALTER TABLE Employees
DROP COLUMN Age,
DROP COLUMN Email;
```

## Similar Queries

```sql
ALTER TABLE Employees
DROP COLUMN salary;
```

---

# ADD COLUMN

Adds new columns.

```sql
ALTER TABLE Employees
ADD COLUMN salary DECIMAL(7,2),
ADD COLUMN join_date DATE;
```

## Similar Queries

```sql
ALTER TABLE Employees
ADD COLUMN phone_number VARCHAR(15);
```

---

# RENAME TABLE Using ALTER

```sql
ALTER TABLE Employees
RENAME TO employees;
```

---

# RENAME TABLE

Alternative syntax.

```sql
RENAME TABLE employees TO family;
```

## Similar Queries

```sql
RENAME TABLE family TO employee_family;
```

---

# DESCRIBE TABLE

Displays table structure.

```sql
DESC Employees;
```

## Alternative Query

```sql
DESCRIBE Employees;
```

---

# TRUNCATE TABLE

Removes all rows from table.

```sql
TRUNCATE TABLE Employees;
```

## Important

- Structure remains
    
- Faster than DELETE
    
- Cannot use WHERE clause
    

---

# DROP TABLE

Deletes entire table.

```sql
DROP TABLE Employees;
```

---

# Interview Difference — DELETE vs TRUNCATE vs DROP

|Feature|DELETE|TRUNCATE|DROP|
|---|---|---|---|
|Removes|Selected Rows|All Rows|Entire Table|
|WHERE Allowed|Yes|No|No|
|Rollback|Yes|Limited|No|
|Structure Deleted|No|No|Yes|

---

# 2. DML — Data Manipulation Language

Used to manipulate data inside tables.

---

# INSERT

Adds records into table.

```sql
INSERT INTO family(emp_id, emp_name, salary, join_date)
VALUES(1, 'Suresh', 50000.00, '2026-05-19');
```

## Multiple Insert

```sql
INSERT INTO family
VALUES
(2, 'Arun', 45000.00, '2026-01-10'),
(3, 'Karthik', 60000.00, '2026-02-15');
```

---

# UPDATE

Modifies existing records.

```sql
UPDATE family
SET salary = 70000
WHERE emp_id = 1;
```

## Update Multiple Columns

```sql
UPDATE family
SET emp_name = 'Suresh Babu',
    salary = 80000
WHERE emp_id = 1;
```

---

# DELETE

Deletes rows from table.

```sql
DELETE FROM family
WHERE emp_id = 2;
```

## Delete All Rows

```sql
DELETE FROM family;
```

---

# 3. DQL — Data Query Language

Used to fetch/read data.

---

# SELECT

Fetches data from table.

```sql
SELECT * FROM family;
```

---

# Select Specific Columns

```sql
SELECT emp_name, salary
FROM family;
```

---

# WHERE Clause

Filters records.

```sql
SELECT *
FROM family
WHERE salary > 50000;
```

---

# ORDER BY

Sorts data.

```sql
SELECT *
FROM family
ORDER BY salary DESC;
```

---

# LIMIT

Restricts number of rows.

```sql
SELECT *
FROM family
LIMIT 5;
```

---

# DISTINCT

Removes duplicates.

```sql
SELECT DISTINCT salary
FROM family;
```

---

# LIKE Operator

Pattern matching.

```sql
SELECT *
FROM family
WHERE emp_name LIKE 'S%';
```

---

# IN Operator

Matches multiple values.

```sql
SELECT *
FROM family
WHERE emp_id IN (1,2,3);
```

---

# BETWEEN Operator

Range filtering.

```sql
SELECT *
FROM family
WHERE salary BETWEEN 30000 AND 70000;
```

---

# Aggregate Functions

---

# COUNT

```sql
SELECT COUNT(*) FROM family;
```

---

# SUM

```sql
SELECT SUM(salary) FROM family;
```

---

# AVG

```sql
SELECT AVG(salary) FROM family;
```

---

# MAX and MIN

```sql
SELECT MAX(salary), MIN(salary)
FROM family;
```

---

# GROUP BY

Groups records.

```sql
SELECT salary, COUNT(*)
FROM family
GROUP BY salary;
```

---

# HAVING

Filters grouped records.

```sql
SELECT salary, COUNT(*)
FROM family
GROUP BY salary
HAVING COUNT(*) > 1;
```

---

# 4. TCL — Transaction Control Language

Used to manage transactions.

---

# START TRANSACTION

```sql
START TRANSACTION;
```

---

# COMMIT

Permanently saves changes.

```sql
COMMIT;
```

---

# ROLLBACK

Undo changes before commit.

```sql
ROLLBACK;
```

---

# SAVEPOINT

Creates rollback checkpoint.

```sql
SAVEPOINT sp1;
```

---

# 5. DCL — Data Control Language

Used for permissions/security.

---

# GRANT

Provides access.

```sql
GRANT SELECT, INSERT
ON family
TO 'user1';
```

---

# REVOKE

Removes access.

```sql
REVOKE INSERT
ON family
FROM 'user1';
```

---

# Important Interview Notes

---

# DDL Commands

Affect database structure.

Examples:

- CREATE
    
- ALTER
    
- DROP
    
- TRUNCATE
    

---

# DML Commands

Affect data inside tables.

Examples:

- INSERT
    
- UPDATE
    
- DELETE
    

---

# DQL Commands

Used to retrieve data.

Examples:

- SELECT
    

---

# TCL Commands

Manage transactions.

Examples:

- COMMIT
    
- ROLLBACK
    
- SAVEPOINT
    

---

# DCL Commands

Manage permissions.

Examples:

- GRANT
    
- REVOKE
    

---

# Real-Time Backend Developer Usage

As a .NET backend developer:

- DDL → Table design & migrations
    
- DML → CRUD operations
    
- DQL → APIs and reporting queries
    
- TCL → Transaction handling
    
- DCL → User permissions
    

---

# Common Interview Questions

---

# Why TRUNCATE is Faster than DELETE?

Because:

- TRUNCATE removes all rows directly
    
- Minimal logging
    
- Does not scan rows individually
    

---

# Why Use PRIMARY KEY?

- Ensures uniqueness
    
- Improves indexing
    
- Maintains entity integrity
    

---

# Why Use FOREIGN KEY?

- Maintains relationships
    
- Prevents invalid references
    
- Ensures referential integrity
    

---

# Best Practices

## Naming Convention

Use:

```sql
snake_case
```

Example:

```sql
employee_details
```

Avoid:

```sql
EmployeeDetails
```

---

# Professional SQL Practices

- Use meaningful column names
    
- Always define Primary Keys
    
- Use indexes for frequently searched columns
    
- Avoid `SELECT *` in production
    
- Use transactions for critical operations
    
- Normalize tables properly
  
# MySQL INSERT Statement — Obsidian Notes

---

# INSERT Statement in MySQL

Used to add records (rows) into a table.

Category:

- DML (Data Manipulation Language)
    

---

# Basic Syntax

```sql
INSERT INTO table_name(column1, column2)
VALUES(value1, value2);
```

---

# Example Table

```sql
CREATE TABLE family(
    emp_id INT PRIMARY KEY,
    emp_name VARCHAR(50),
    salary DECIMAL(7,2),
    join_date DATE
);
```

---

# Insert Single Row

```sql
INSERT INTO family(emp_id, emp_name, salary, join_date)
VALUES(1, 'Suresh', 50000.00, '2026-05-20');
```

---

# Verify Data

```sql
SELECT * FROM family;
```

---

# Insert Multiple Rows

```sql
INSERT INTO family(emp_id, emp_name, salary, join_date)
VALUES
(2, 'Arun', 45000.00, '2026-01-15'),
(3, 'Karthik', 60000.00, '2026-02-10'),
(4, 'Rahul', 55000.00, '2026-03-05');
```

---

# Insert Without Column Names

Possible only when values match exact table order.

```sql
INSERT INTO family
VALUES(5, 'Vignesh', 65000.00, '2026-04-01');
```

---

# Professional Best Practice

Always specify column names.

Recommended:

```sql
INSERT INTO family(emp_id, emp_name, salary, join_date)
VALUES(6, 'Ajay', 70000.00, '2026-05-01');
```

Avoid:

```sql
INSERT INTO family
VALUES(6, 'Ajay', 70000.00, '2026-05-01');
```

Reason:

- Prevents errors if column order changes
    
- Improves readability
    
- Easier maintenance
    

---

# Insert NULL Values

```sql
INSERT INTO family(emp_id, emp_name, salary, join_date)
VALUES(7, 'Kumar', NULL, NULL);
```

---

# Insert Current Date

```sql
INSERT INTO family(emp_id, emp_name, salary, join_date)
VALUES(8, 'Ravi', 40000.00, CURDATE());
```

---

# Insert Using SET Syntax

Alternative syntax.

```sql
INSERT INTO family
SET
emp_id = 9,
emp_name = 'Praveen',
salary = 52000.00,
join_date = '2026-05-21';
```

---

# Insert Data from Another Table

```sql
INSERT INTO employee_backup(emp_id, emp_name)
SELECT emp_id, emp_name
FROM family;
```

---

# AUTO_INCREMENT Example

Automatically generates IDs.

```sql
CREATE TABLE employees(
    emp_id INT AUTO_INCREMENT PRIMARY KEY,
    emp_name VARCHAR(50),
    salary DECIMAL(7,2)
);
```

---

# Insert with AUTO_INCREMENT

```sql
INSERT INTO employees(emp_name, salary)
VALUES('Suresh', 50000.00);
```

Generated automatically:

|emp_id|emp_name|salary|
|---|---|---|
|1|Suresh|50000|

---

# Common INSERT Errors

---

# Duplicate Primary Key

```sql
INSERT INTO family(emp_id, emp_name)
VALUES(1, 'Duplicate');
```

Error:

- Primary Key must be unique
    

---

# Column Count Mismatch

```sql
INSERT INTO family
VALUES(10, 'Arun');
```

Error:

- Missing values for remaining columns
    

---

# Datatype Mismatch

```sql
INSERT INTO family(emp_id, salary)
VALUES('abc', 'xyz');
```

Error:

- Invalid datatype conversion
    

---

# INSERT IGNORE

Skips duplicate errors.

```sql
INSERT IGNORE INTO family(emp_id, emp_name)
VALUES(1, 'Suresh');
```

---

# REPLACE INTO

Deletes old row and inserts new row if key exists.

```sql
REPLACE INTO family(emp_id, emp_name)
VALUES(1, 'Updated Name');
```

---

# INSERT vs UPDATE

|INSERT|UPDATE|
|---|---|
|Adds new row|Modifies existing row|
|Creates record|Changes record|
|Uses VALUES|Uses SET|

---

# Real-Time Backend Developer Usage

In .NET backend development:

- APIs insert records into database
    
- Registration forms
    
- Order creation
    
- Payment records
    
- Logging systems
    

Usually done using:

- Dapper
    
- Entity Framework Core
    
- Stored Procedures
    

---

# Dapper INSERT Example (.NET)

```csharp
string query = @"
INSERT INTO family(emp_name, salary)
VALUES(@Name, @Salary)";

await connection.ExecuteAsync(query, new
{
    Name = "Suresh",
    Salary = 50000
});
```

---

# Interview Questions

---

# Difference Between INSERT and UPDATE

|INSERT|UPDATE|
|---|---|
|Creates new row|Modifies existing row|
|Uses VALUES|Uses SET|
|Adds data|Changes data|

---

# What Happens if Primary Key Already Exists?

MySQL throws:

- Duplicate Key Error
    

Unless:

- `INSERT IGNORE`
    
- `REPLACE INTO`
    
- `ON DUPLICATE KEY UPDATE`
    

is used.

---

# ON DUPLICATE KEY UPDATE

Used for UPSERT behavior.

```sql
INSERT INTO family(emp_id, emp_name, salary)
VALUES(1, 'Suresh', 60000)
ON DUPLICATE KEY UPDATE
salary = 60000;
```

---

# Best Practices

- Always specify column names
    
- Use transactions for critical inserts
    
- Validate data before insert
    
- Use parameterized queries in backend
    
- Avoid hardcoded SQL values
    
- Use AUTO_INCREMENT for IDs when possible
    

---

# Important Summary

## INSERT

- Adds rows into table
    
- DML command
    

## VALUES

- Specifies row data
    

## AUTO_INCREMENT

- Generates IDs automatically
    

## INSERT IGNORE

- Skips duplicate errors
    

## ON DUPLICATE KEY UPDATE

- Performs UPSERT operation
  
# MySQL UPDATE, DELETE, COMMIT & ROLLBACK Notes (Obsidian Friendly)

---

# UPDATE Query in MySQL

Category:

- DML (Data Manipulation Language)
    

Used to modify existing records in a table.

---

# Basic Syntax

```sql
UPDATE table_name
SET column_name = value
WHERE condition;
```

---

# Example Table

|emp_id|emp_name|salary|
|---|---|---|
|1|Suresh|50000|
|2|Arun|45000|

---

# Update Single Column

```sql
UPDATE family
SET salary = 60000
WHERE emp_id = 1;
```

---

# Before Update

|emp_id|emp_name|salary|
|---|---|---|
|1|Suresh|50000|

---

# After Update

|emp_id|emp_name|salary|
|---|---|---|
|1|Suresh|60000|

---

# Update Multiple Columns

```sql
UPDATE family
SET
emp_name = 'Suresh Babu',
salary = 75000
WHERE emp_id = 1;
```

---

# Update All Rows

```sql
UPDATE family
SET salary = 30000;
```

⚠️ Warning:

- Updates every row
    
- Dangerous in production
    

---

# DELETE Query in MySQL

Category:

- DML (Data Manipulation Language)
    

Used to remove rows from a table.

---

# Basic Syntax

```sql
DELETE FROM table_name
WHERE condition;
```

---

# Delete Specific Row

```sql
DELETE FROM family
WHERE emp_id = 2;
```

---

# Delete All Rows

```sql
DELETE FROM family;
```

⚠️ Deletes all records but table structure remains.

---

# UPDATE vs DELETE

|UPDATE|DELETE|
|---|---|
|Modifies rows|Removes rows|
|Uses SET|Uses DELETE FROM|
|Data remains|Data removed|

---

# SQL_SAFE_UPDATES

Important MySQL safety feature.

Prevents accidental:

- UPDATE without WHERE
    
- DELETE without WHERE
    

---

# Example Error

```sql
UPDATE family
SET salary = 10000;
```

May throw:

> Error Code: 1175  
> You are using safe update mode

---

# Check Current Setting

```sql
SELECT @@SQL_SAFE_UPDATES;
```

---

# Disable SQL_SAFE_UPDATES

```sql
SET SQL_SAFE_UPDATES = 0;
```

---

# Enable SQL_SAFE_UPDATES

```sql
SET SQL_SAFE_UPDATES = 1;
```

---

# Best Practice

Always use:

```sql
WHERE
```

clause in:

- UPDATE
    
- DELETE
    

---

# AUTOCOMMIT in MySQL

By default, MySQL uses:

```sql
AUTOCOMMIT = ON
```

Meaning:

- Every query is automatically saved permanently.
    

---

# Example

```sql
UPDATE family
SET salary = 80000
WHERE emp_id = 1;
```

Immediately saved permanently.

Cannot rollback later.

---

# Check AUTOCOMMIT Status

```sql
SELECT @@AUTOCOMMIT;
```

---

# Disable AUTOCOMMIT

```sql
SET AUTOCOMMIT = 0;
```

Now changes are NOT saved automatically.

---

# What Happens After Disabling AUTOCOMMIT?

Changes become temporary until:

```sql
COMMIT;
```

or

```sql
ROLLBACK;
```

is executed.

---

# Transaction Flow

```sql
SET AUTOCOMMIT = 0;

UPDATE family
SET salary = 90000
WHERE emp_id = 1;

ROLLBACK;
```

Result:

- Changes undone
    

---

# Another Example

```sql
SET AUTOCOMMIT = 0;

UPDATE family
SET salary = 90000
WHERE emp_id = 1;

COMMIT;
```

Result:

- Changes saved permanently
    

---

# COMMIT

Category:

- TCL (Transaction Control Language)
    

Used to permanently save transaction changes.

---

# Syntax

```sql
COMMIT;
```

---

# How COMMIT Works

When AUTOCOMMIT is OFF:

MySQL stores changes temporarily in transaction session.

COMMIT:

- Finalizes changes
    
- Writes changes permanently
    
- Makes data visible to others
    

---

# Real-World Example

Bank Transfer:

```sql
SET AUTOCOMMIT = 0;

UPDATE accounts
SET balance = balance - 1000
WHERE account_id = 1;

UPDATE accounts
SET balance = balance + 1000
WHERE account_id = 2;

COMMIT;
```

Both updates succeed together.

---

# ROLLBACK

Category:

- TCL (Transaction Control Language)
    

Used to undo transaction changes.

---

# Syntax

```sql
ROLLBACK;
```

---

# How ROLLBACK Works

If transaction not committed yet:

- All changes are reverted
    
- Database returns to previous state
    

---

# Example

```sql
SET AUTOCOMMIT = 0;

DELETE FROM family
WHERE emp_id = 1;

ROLLBACK;
```

Result:

- Deleted row restored
    

---

# Important Rule

ROLLBACK works only:

- Before COMMIT
    
- With transactional storage engine like InnoDB
    

---

# After COMMIT

```sql
COMMIT;
```

ROLLBACK cannot undo changes anymore.

Because data already permanently saved.

---

# Transaction Lifecycle

---

# Step 1 — Disable AUTOCOMMIT

```sql
SET AUTOCOMMIT = 0;
```

---

# Step 2 — Execute Queries

```sql
UPDATE family
SET salary = 100000
WHERE emp_id = 1;
```

---

# Step 3A — Save Permanently

```sql
COMMIT;
```

OR

# Step 3B — Undo Changes

```sql
ROLLBACK;
```

---

# SAVEPOINT

Creates checkpoint inside transaction.

---

# Example

```sql
SET AUTOCOMMIT = 0;

SAVEPOINT before_delete;

DELETE FROM family
WHERE emp_id = 2;

ROLLBACK TO before_delete;
```

---

# Transaction Example (Professional Interview Example)

```sql
SET AUTOCOMMIT = 0;

UPDATE accounts
SET balance = balance - 500
WHERE account_id = 1;

UPDATE accounts
SET balance = balance + 500
WHERE account_id = 2;

COMMIT;
```

Purpose:

- Ensures money transfer consistency
    

If second query fails:

```sql
ROLLBACK;
```

No money loss occurs.

---

# ACID Properties Related to Transactions

---

# Atomicity

Either:

- Entire transaction succeeds  
    OR
    
- Entire transaction fails
    

---

# Consistency

Database remains valid.

---

# Isolation

Transactions do not interfere.

---

# Durability

Committed data survives crashes.

---

# Important Interview Questions

---

# Difference Between DELETE and TRUNCATE

|DELETE|TRUNCATE|
|---|---|
|Removes selected rows|Removes all rows|
|WHERE allowed|WHERE not allowed|
|Can rollback|Limited rollback|
|Slower|Faster|

---

# Why Disable AUTOCOMMIT?

To:

- Group multiple queries
    
- Maintain consistency
    
- Prevent partial updates
    

Used in:

- Banking
    
- Payments
    
- Inventory systems
    

---

# What Happens If COMMIT Not Executed?

When session closes:

- MySQL automatically rolls back uncommitted changes
    

---

# Can We ROLLBACK After COMMIT?

❌ No

Because COMMIT permanently saves data.

---

# Real-Time .NET Backend Usage

In .NET applications:

- Transactions used for critical operations
    
- Common with:
    
    - Dapper
        
    - Entity Framework Core
        
    - ADO.NET
        

---

# Dapper Transaction Example

```csharp
using var transaction = connection.BeginTransaction();

try
{
    await connection.ExecuteAsync(query1, transaction: transaction);

    await connection.ExecuteAsync(query2, transaction: transaction);

    transaction.Commit();
}
catch
{
    transaction.Rollback();
}
```

---

# Best Practices

- Always use WHERE in UPDATE/DELETE
    
- Use transactions for critical operations
    
- Keep transactions short
    
- Commit quickly
    
- Avoid long-running locks
    
- Use InnoDB for transactional support
    

---

# Important Summary

## UPDATE

- Modifies rows
    

## DELETE

- Removes rows
    

## SQL_SAFE_UPDATES

- Prevents accidental mass updates/deletes
    

## AUTOCOMMIT

- Automatically saves changes
    

## COMMIT

- Permanently saves transaction
    

## ROLLBACK

- Undoes transaction before commit
    

## SAVEPOINT

- Creates partial rollback point
  
# MySQL Constraints Notes — Obsidian Friendly

---

# What are Constraints in MySQL?

Constraints are rules applied to table columns to enforce:

- Data accuracy
    
- Data integrity
    
- Validations
    
- Relationships
    

---

# Types of Constraints

|Constraint|Purpose|
|---|---|
|PRIMARY KEY|Unique identifier|
|FOREIGN KEY|Maintains relationships|
|UNIQUE|Prevents duplicate values|
|NOT NULL|Prevents NULL values|
|CHECK|Validates conditions|
|DEFAULT|Sets default value|
|AUTO_INCREMENT|Automatically generates numbers|

---

# PRIMARY KEY Constraint

Ensures:

- Unique values
    
- No NULL values
    

---

# Create Table with PRIMARY KEY

```sql
CREATE TABLE employees(
    emp_id INT PRIMARY KEY,
    emp_name VARCHAR(50)
);
```

---

# Add PRIMARY KEY Using ALTER TABLE

```sql
ALTER TABLE employees
ADD PRIMARY KEY(emp_id);
```

---

# Remove PRIMARY KEY

```sql
ALTER TABLE employees
DROP PRIMARY KEY;
```

---

# UNIQUE Constraint

Prevents duplicate values.

---

# UNIQUE While Creating Table

```sql
CREATE TABLE employees(
    emp_id INT PRIMARY KEY,
    email VARCHAR(100) UNIQUE
);
```

---

# UNIQUE Using ALTER TABLE

```sql
ALTER TABLE employees
ADD CONSTRAINT uq_email
UNIQUE(email);
```

---

# Remove UNIQUE Constraint

## MySQL internally creates index

```sql
ALTER TABLE employees
DROP INDEX uq_email;
```

---

# Example

Valid:

|email|
|---|
|[abc@gmail.com](mailto:abc@gmail.com)|
|[xyz@gmail.com](mailto:xyz@gmail.com)|

Invalid:

|email|
|---|
|[abc@gmail.com](mailto:abc@gmail.com)|
|[abc@gmail.com](mailto:abc@gmail.com)|

---

# NOT NULL Constraint

Prevents NULL values.

---

# NOT NULL While Creating Table

```sql
CREATE TABLE employees(
    emp_id INT PRIMARY KEY,
    emp_name VARCHAR(50) NOT NULL
);
```

---

# Add NOT NULL Using ALTER TABLE

```sql
ALTER TABLE employees
MODIFY emp_name VARCHAR(50) NOT NULL;
```

---

# Remove NOT NULL Constraint

```sql
ALTER TABLE employees
MODIFY emp_name VARCHAR(50) NULL;
```

---

# CHECK Constraint

Validates conditions before inserting/updating data.

---

# CHECK While Creating Table

```sql
CREATE TABLE employees(
    emp_id INT PRIMARY KEY,
    age INT CHECK(age >= 18)
);
```

---

# CHECK Using ALTER TABLE

```sql
ALTER TABLE employees
ADD CONSTRAINT chk_age
CHECK(age >= 18);
```

---

# Remove CHECK Constraint

```sql
ALTER TABLE employees
DROP CHECK chk_age;
```

---

# Example

Valid:

```sql
INSERT INTO employees
VALUES(1, 25);
```

Invalid:

```sql
INSERT INTO employees
VALUES(2, 15);
```

---

# DEFAULT Constraint

Provides default value when no value supplied.

---

# DEFAULT While Creating Table

```sql
CREATE TABLE employees(
    emp_id INT PRIMARY KEY,
    country VARCHAR(50) DEFAULT 'India'
);
```

---

# DEFAULT Using ALTER TABLE

```sql
ALTER TABLE employees
ALTER country
SET DEFAULT 'India';
```

---

# Remove DEFAULT Constraint

```sql
ALTER TABLE employees
ALTER country
DROP DEFAULT;
```

---

# Example

```sql
INSERT INTO employees(emp_id)
VALUES(1);
```

Automatically inserts:

|emp_id|country|
|---|---|
|1|India|

---

# FOREIGN KEY Constraint

Maintains relationship between tables.

---

# FOREIGN KEY While Creating Table

```sql
CREATE TABLE departments(
    dept_id INT PRIMARY KEY,
    dept_name VARCHAR(50)
);
```

```sql
CREATE TABLE employees(
    emp_id INT PRIMARY KEY,
    emp_name VARCHAR(50),
    dept_id INT,
    FOREIGN KEY(dept_id)
    REFERENCES departments(dept_id)
);
```

---

# Add FOREIGN KEY Using ALTER TABLE

```sql
ALTER TABLE employees
ADD CONSTRAINT fk_department
FOREIGN KEY(dept_id)
REFERENCES departments(dept_id);
```

---

# Remove FOREIGN KEY

```sql
ALTER TABLE employees
DROP FOREIGN KEY fk_department;
```

---

# Purpose of FOREIGN KEY

Prevents invalid references.

Example:

- Cannot assign employee to non-existing department
    

---

# AUTO_INCREMENT Constraint

Automatically generates sequential numbers.

---

# AUTO_INCREMENT While Creating Table

```sql
CREATE TABLE employees(
    emp_id INT AUTO_INCREMENT PRIMARY KEY,
    emp_name VARCHAR(50)
);
```

---

# Insert Example

```sql
INSERT INTO employees(emp_name)
VALUES('Suresh');
```

Generated automatically:

|emp_id|emp_name|
|---|---|
|1|Suresh|

---

# Change AUTO_INCREMENT Starting Value

```sql
ALTER TABLE employees
AUTO_INCREMENT = 100;
```

---

# Composite PRIMARY KEY

Combination of multiple columns.

---

# Example

```sql
CREATE TABLE student_courses(
    student_id INT,
    course_id INT,
    PRIMARY KEY(student_id, course_id)
);
```

---

# Constraint Naming

Professional practice:

- Always give meaningful names
    

---

# Example

```sql
ALTER TABLE employees
ADD CONSTRAINT chk_salary
CHECK(salary > 0);
```

---

# Why Use Constraints?

Constraints ensure:

- Data integrity
    
- Data consistency
    
- Prevent invalid data
    
- Maintain relationships
    

---

# Real-Time Backend Examples

|Constraint|Real-Time Usage|
|---|---|
|PRIMARY KEY|User ID|
|UNIQUE|Email|
|NOT NULL|Username|
|CHECK|Age >= 18|
|DEFAULT|Country = India|
|FOREIGN KEY|Department Mapping|
|AUTO_INCREMENT|Auto-generated IDs|

---

# Important Interview Questions

---

# Difference Between PRIMARY KEY and UNIQUE

|PRIMARY KEY|UNIQUE|
|---|---|
|Only one per table|Multiple allowed|
|Cannot be NULL|Can allow NULL|
|Main identifier|Alternate uniqueness|

---

# Difference Between NULL and NOT NULL

|NULL|NOT NULL|
|---|---|
|Value may be missing|Value mandatory|

---

# Why Use CHECK Constraint?

To enforce business rules.

Example:

- Salary > 0
    
- Age >= 18
    

---

# Why Use DEFAULT Constraint?

Provides fallback value automatically.

---

# Can Table Have Multiple UNIQUE Constraints?

✅ Yes

Example:

- Email unique
    
- Phone unique
    

---

# Can Table Have Multiple PRIMARY KEYS?

❌ No

But:  
✅ Composite primary key possible.

---

# Best Practices

- Always define PRIMARY KEY
    
- Use FOREIGN KEY for relationships
    
- Use NOT NULL for mandatory fields
    
- Use CHECK for validations
    
- Use UNIQUE for emails/usernames
    
- Use meaningful constraint names
    
- Prefer AUTO_INCREMENT for IDs
    

---

# Professional Interview Summary

## PRIMARY KEY

- Unique + NOT NULL
    

## FOREIGN KEY

- Maintains relationships
    

## UNIQUE

- Prevents duplicates
    

## NOT NULL

- Mandatory field
    

## CHECK

- Validation rule
    

## DEFAULT

- Automatic fallback value
    

## AUTO_INCREMENT

- Automatic ID generation


# MySQL DEFAULT Constraint

## Definition

The **DEFAULT constraint** is used to assign a default value to a column when no value is specified during an `INSERT` operation.

If a value is not provided for the column, MySQL automatically inserts the default value.

---

## Creating a Table

```sql
CREATE TABLE products(
    p_id INT,
    p_name VARCHAR(100),
    price DECIMAL(6,2)
);
```

### Table Structure

|Column|Data Type|
|---|---|
|p_id|INT|
|p_name|VARCHAR(100)|
|price|DECIMAL(6,2)|

Initially, the `price` column has no default value.

---

## Adding a DEFAULT Constraint

```sql
ALTER TABLE products
ALTER COLUMN price SET DEFAULT 15;
```

This statement sets the default value of the `price` column to **15.00**.

---

## Inserting Data Without Specifying Price

```sql
INSERT INTO products (p_id, p_name)
VALUES (1, 'check');
```

Since no value is provided for `price`, MySQL automatically uses the default value.

---

## Result

```sql
SELECT * FROM products;
```

Output:

|p_id|p_name|price|
|---|---|---|
|1|check|15.00|

---

## Inserting a Custom Price

```sql
INSERT INTO products
VALUES (2, 'Pen', 25.50);
```

Output:

|p_id|p_name|price|
|---|---|---|
|1|check|15.00|
|2|Pen|25.50|

The default value is ignored because a price was explicitly supplied.

---

## Benefits of DEFAULT Constraints

- Prevents NULL values when a sensible default exists.
    
- Reduces the amount of data that must be supplied during inserts.
    
- Maintains consistency across records.
    
- Simplifies data entry.
    

---

## Important Notes

1. The default value is used **only when the column is omitted** from the `INSERT` statement.
    
2. If `NULL` is explicitly inserted, MySQL stores `NULL` (unless the column is defined as `NOT NULL`).
    
3. Existing records are not modified when a default constraint is added.
    

---

## Example Summary

```sql
CREATE TABLE products(
    p_id INT,
    p_name VARCHAR(100),
    price DECIMAL(6,2)
);

ALTER TABLE products
ALTER COLUMN price SET DEFAULT 15;

INSERT INTO products (p_id, p_name)
VALUES (1, 'check');

SELECT * FROM products;
```

Result:

```text
+------+--------+-------+
| p_id | p_name | price |
+------+--------+-------+
| 1    | check  | 15.00 |
+------+--------+-------+
```

The value `15.00` is automatically inserted because of the DEFAULT constraint.

One caveat: `ALTER COLUMN price SET DEFAULT 15` works in newer MySQL versions. In older versions, you may need:

```sql
ALTER TABLE products
MODIFY price DECIMAL(6,2) DEFAULT 15;
```

Both approaches achieve the same goal: assigning a default value to the `price` column.

# MySQL PRIMARY KEY and AUTO_INCREMENT

## Definition

### PRIMARY KEY

A **PRIMARY KEY** uniquely identifies each record in a table.

Characteristics:

- Cannot contain `NULL` values.
    
- Values must be unique.
    
- Only one primary key is allowed per table.
    

### AUTO_INCREMENT

The **AUTO_INCREMENT** attribute automatically generates a unique number whenever a new row is inserted.

Characteristics:

- Typically used with integer columns.
    
- Commonly applied to primary key columns.
    
- Starts at `1` by default and increments by `1`.
    

---

# Creating a Table with PRIMARY KEY and AUTO_INCREMENT

```sql
CREATE TABLE transactions(
    t_id INT PRIMARY KEY AUTO_INCREMENT,
    amount DECIMAL(5,2)
);
```

## Table Structure

```sql
DESC transactions;
```

Output:

|Field|Type|Null|Key|Default|Extra|
|---|---|---|---|---|---|
|t_id|int|NO|PRI|NULL|auto_increment|
|amount|decimal(5,2)|YES||NULL||

---

# Inserting Records

Since `t_id` is auto-generated, it does not need to be included in the INSERT statement.

```sql
INSERT INTO transactions(amount)
VALUES(112.60);
```

View the data:

```sql
SELECT * FROM transactions;
```

Output:

|t_id|amount|
|---|---|
|1|112.60|

The value `1` is automatically assigned to `t_id`.

---

# Dropping the Table

```sql
DROP TABLE transactions;
```

---

# Adding PRIMARY KEY and AUTO_INCREMENT Using ALTER TABLE

Suppose the table was created without constraints:

```sql
CREATE TABLE transactions(
    t_id INT,
    amount DECIMAL(5,2)
);
```

## Step 1: Add Primary Key

```sql
ALTER TABLE transactions
ADD CONSTRAINT PRIMARY KEY(t_id);
```

This makes `t_id` the primary key.

---

## Step 2: Add AUTO_INCREMENT

```sql
ALTER TABLE transactions
MODIFY t_id INT AUTO_INCREMENT;
```

This enables automatic number generation for `t_id`.

---

## Step 3: Insert Data

```sql
INSERT INTO transactions(amount)
VALUES(100.56);
```

View the result:

```sql
SELECT * FROM transactions;
```

Output:

|t_id|amount|
|---|---|
|1|100.56|

MySQL automatically generates the primary key value.

---

# Why Use PRIMARY KEY with AUTO_INCREMENT?

## Advantages

### Unique Identification

Every record receives a unique ID.

```text
1
2
3
4
...
```

### No Manual ID Management

Developers do not need to generate IDs manually.

### Faster Searching

Primary keys are automatically indexed, improving query performance.

### Data Integrity

Duplicate IDs are prevented automatically.

---

# Best Practice

Use an integer primary key with AUTO_INCREMENT for transaction, customer, product, and employee tables.

Example:

```sql
CREATE TABLE transactions(
    t_id INT PRIMARY KEY AUTO_INCREMENT,
    amount DECIMAL(5,2)
);
```

This is the most common and recommended approach in MySQL.

---

# Summary

```sql
CREATE TABLE transactions(
    t_id INT PRIMARY KEY AUTO_INCREMENT,
    amount DECIMAL(5,2)
);

INSERT INTO transactions(amount)
VALUES(112.60);

SELECT * FROM transactions;
```

Result:

```text
+------+--------+
| t_id | amount |
+------+--------+
| 1    | 112.60 |
+------+--------+
```

`t_id` is automatically generated, unique, and serves as the table's primary key.

# MySQL AUTO_INCREMENT Starting Value

## Definition

The `AUTO_INCREMENT` attribute automatically generates sequential numeric values for a column.

By default, numbering starts at **1** and increases by **1** for each new record.

MySQL allows you to change the next value that will be generated using the `AUTO_INCREMENT` table option.

---

## Syntax

```sql
ALTER TABLE table_name
AUTO_INCREMENT = starting_value;
```

Example:

```sql
ALTER TABLE transactions
AUTO_INCREMENT = 100;
```

This sets the next generated value of the auto-increment column to **100**.

---

## Example

### Create Table

```sql
CREATE TABLE transactions(
    t_id INT PRIMARY KEY AUTO_INCREMENT,
    amount DECIMAL(5,2)
);
```

### Set Starting Value

```sql
ALTER TABLE transactions
AUTO_INCREMENT = 100;
```

### Insert Records

```sql
INSERT INTO transactions(amount)
VALUES(250.50);

INSERT INTO transactions(amount)
VALUES(175.25);
```

### View Data

```sql
SELECT * FROM transactions;
```

Output:

|t_id|amount|
|---|---|
|100|250.50|
|101|175.25|

The first generated ID starts at 100 instead of 1.

---

## Important Notes

### Must Be Greater Than Existing Values

If the table already contains records, the new AUTO_INCREMENT value must be greater than the current maximum primary key value.

Example:

Current data:

|t_id|
|---|
|1|
|2|
|3|

Valid:

```sql
ALTER TABLE transactions
AUTO_INCREMENT = 100;
```

Ignored/ineffective:

```sql
ALTER TABLE transactions
AUTO_INCREMENT = 2;
```

MySQL will continue from the next available value after the maximum existing ID.

---

### Affects Future Inserts Only

Changing the AUTO_INCREMENT value does not modify existing records.

Example:

Before:

|t_id|
|---|
|1|
|2|
|3|

After:

```sql
ALTER TABLE transactions
AUTO_INCREMENT = 100;
```

Existing records remain unchanged.

New records will receive IDs starting from 100.

---

## Use Cases

- Custom invoice numbers
    
- Order tracking systems
    
- Employee IDs
    
- Migration of legacy data
    
- Reserving ID ranges for specific environments
    

---

## Complete Example

```sql
CREATE TABLE transactions(
    t_id INT PRIMARY KEY AUTO_INCREMENT,
    amount DECIMAL(5,2)
);

ALTER TABLE transactions
AUTO_INCREMENT = 100;

INSERT INTO transactions(amount)
VALUES(500.00);

SELECT * FROM transactions;
```

Result:

```text
+------+--------+
| t_id | amount |
+------+--------+
| 100  | 500.00 |
+------+--------+
```

The next automatically generated primary key value begins at **100**.

# MySQL Foreign Key Constraints

## What is a Foreign Key?

A **Foreign Key** is a column (or set of columns) in one table that refers to the **Primary Key** of another table.

It establishes a relationship between two tables and enforces **referential integrity**.

### Example

**Customers Table**

|c_id|c_name|
|---|---|
|1|Suresh|
|2|Dinesh|

**Transactions Table**

|t_id|amount|customer_id|
|---|---|---|
|1|99.99|1|

Here, `customer_id` in the `transactions` table references `c_id` in the `customers` table.

---

# Creating Parent Table

```sql
CREATE TABLE customers(
    c_id INT PRIMARY KEY AUTO_INCREMENT,
    c_name VARCHAR(100),
    age INT
);
```

Insert sample data:

```sql
INSERT INTO customers(c_name, age)
VALUES
('Suresh',25),
('Dinesh',27);
```

---

# Creating Child Table with Foreign Key

```sql
CREATE TABLE transactions(
    t_id INT PRIMARY KEY AUTO_INCREMENT,
    amount DECIMAL(5,2),
    customer_id INT,
    FOREIGN KEY(customer_id)
    REFERENCES customers(c_id)
);
```

Relationship:

```text
customers
---------
c_id (PK)

      |
      |
      V

transactions
------------
customer_id (FK)
```

---

# Why Are NULL Values Allowed in Foreign Keys?

A foreign key enforces:

> "If a value exists, it must exist in the parent table."

It does **not** mean a value is mandatory.

Example:

```sql
INSERT INTO transactions(amount)
VALUES(10.00);
```

Since no customer is specified:

```text
customer_id = NULL
```

This is valid.

Similarly:

```sql
INSERT INTO transactions(amount, customer_id)
VALUES(10.00, NULL);
```

is also valid.

### Reason

Some records may legitimately have no related parent record yet.

Examples:

- Guest orders
    
- Unassigned employees
    
- Pending transactions
    
- Optional relationships
    

---

# Making a Foreign Key NOT NULL

If every transaction must belong to a customer:

```sql
CREATE TABLE transactions(
    t_id INT PRIMARY KEY AUTO_INCREMENT,
    amount DECIMAL(5,2),
    customer_id INT NOT NULL,
    FOREIGN KEY(customer_id)
    REFERENCES customers(c_id)
);
```

Now this will fail:

```sql
INSERT INTO transactions(amount)
VALUES(10.00);
```

Error:

```text
Column 'customer_id' cannot be null
```

---

# Referential Integrity

Valid:

```sql
INSERT INTO transactions(amount, customer_id)
VALUES(99.99,1);
```

Because customer 1 exists.

Invalid:

```sql
INSERT INTO transactions(amount, customer_id)
VALUES(99.99,100);
```

Error:

```text
Cannot add or update a child row:
a foreign key constraint fails
```

Because customer 100 does not exist.

---

# Adding a Foreign Key Using ALTER TABLE

Suppose the table already exists.

```sql
CREATE TABLE transactions(
    t_id INT PRIMARY KEY AUTO_INCREMENT,
    amount DECIMAL(5,2),
    customer_id INT
);
```

Add the foreign key later:

```sql
ALTER TABLE transactions
ADD CONSTRAINT fk_c_id
FOREIGN KEY(customer_id)
REFERENCES customers(c_id);
```

### Components

- `fk_c_id` → Constraint name
    
- `customer_id` → Foreign key column
    
- `customers(c_id)` → Referenced primary key
    

---

# Viewing Foreign Key Information

```sql
SHOW CREATE TABLE transactions;
```

or

```sql
DESC transactions;
```

---

# Dropping a Foreign Key

First identify its name.

Example:

```sql
SHOW CREATE TABLE transactions;
```

Output may show:

```text
transactions_ibfk_1
```

Drop it:

```sql
ALTER TABLE transactions
DROP FOREIGN KEY transactions_ibfk_1;
```

If you named the constraint:

```sql
ALTER TABLE transactions
DROP FOREIGN KEY fk_c_id;
```

---

# Can a Table Have Multiple Foreign Keys?

Yes.

Example:

```sql
CREATE TABLE orders(
    order_id INT PRIMARY KEY,
    customer_id INT,
    product_id INT,

    FOREIGN KEY(customer_id)
        REFERENCES customers(c_id),

    FOREIGN KEY(product_id)
        REFERENCES products(p_id)
);
```

Relationship:

```text
orders
 |
 |---- customer_id --> customers
 |
 |---- product_id  --> products
```

A table can have many foreign keys.

---

# Can a Table Have Multiple Primary Keys?

No.

A table can have only **one PRIMARY KEY constraint**.

Invalid:

```sql
CREATE TABLE test(
    id INT PRIMARY KEY,
    code INT PRIMARY KEY
);
```

MySQL Error:

```text
Multiple primary key defined
```

---

# Composite Primary Key

Although only one PRIMARY KEY constraint is allowed, it can contain multiple columns.

Example:

```sql
CREATE TABLE enrollments(
    student_id INT,
    course_id INT,

    PRIMARY KEY(student_id, course_id)
);
```

This is called a **Composite Primary Key**.

Unique combinations:

|student_id|course_id|
|---|---|
|1|101|
|1|102|
|2|101|

---

# Summary

## Foreign Key

- Creates relationships between tables.
    
- References a primary key in another table.
    
- Enforces referential integrity.
    

## NULL Foreign Keys

Allowed by default because the relationship may be optional.

## NOT NULL Foreign Keys

Use when every child record must reference a parent record.

```sql
customer_id INT NOT NULL
```

## ALTER TABLE

Add foreign key:

```sql
ALTER TABLE transactions
ADD CONSTRAINT fk_c_id
FOREIGN KEY(customer_id)
REFERENCES customers(c_id);
```

Drop foreign key:

```sql
ALTER TABLE transactions
DROP FOREIGN KEY fk_c_id;
```

## Key Facts

- One table can have many foreign keys.
    
- One table can have only one primary key constraint.
    
- A primary key can contain multiple columns (composite primary key).
    
- Foreign key values must either:
    
    - Exist in the parent table, or
        
    - Be NULL (unless NOT NULL is specified).
        

A useful rule to remember:

> **Primary Key = "Every row must have a unique identity."**  
> **Foreign Key = "If a relationship is specified, it must point to a valid parent row."**

# Deleting Parent Records and Foreign Key Constraints

## Scenario

Suppose we have the following tables:

### Customers (Parent Table)

|c_id|c_name|
|---|---|
|1|Suresh|
|2|Dinesh|

### Transactions (Child Table)

|t_id|amount|customer_id|
|---|---|---|
|1|99.99|1|
|2|999.90|1|

Notice that `customer_id = 1` in the `transactions` table refers to customer `c_id = 1`.

---

## Attempting to Delete the Parent Record

```sql
DELETE FROM customers
WHERE c_id = 1;
```

MySQL returns:

```text
Error Code: 1451

Cannot delete or update a parent row:
a foreign key constraint fails

transactions,
CONSTRAINT fk_c_id
FOREIGN KEY (customer_id)
REFERENCES customers (c_id)
```

---

# Why Does This Error Occur?

The foreign key constraint protects the relationship between the tables.

If MySQL allowed the deletion:

```text
customers
---------
1  Suresh   <-- Deleted

transactions
------------
1  99.99  customer_id = 1
2 999.90  customer_id = 1
```

The transaction records would point to a customer that no longer exists.

These records are called **orphan records**.

To prevent data inconsistency, MySQL blocks the deletion.

---

# Parent Table vs Child Table

```text
customers
   |
   | Referenced By
   V
transactions
```

- `customers` = Parent table
    
- `transactions` = Child table
    

A parent row cannot be deleted while child rows are still referencing it.

---

# Solution 1: Delete Child Records First

Delete the related transactions:

```sql
DELETE FROM transactions
WHERE customer_id = 1;
```

Then delete the customer:

```sql
DELETE FROM customers
WHERE c_id = 1;
```

This is the safest and most common approach.

---

# Solution 2: Set Foreign Keys to NULL

If the foreign key column allows NULL values:

```sql
UPDATE transactions
SET customer_id = NULL
WHERE customer_id = 1;
```

Now the customer can be deleted:

```sql
DELETE FROM customers
WHERE c_id = 1;
```

Result:

|t_id|amount|customer_id|
|---|---|---|
|1|99.99|NULL|
|2|999.90|NULL|

The transactions remain, but are no longer associated with any customer.

---

# Solution 3: ON DELETE CASCADE

MySQL can automatically delete child records when the parent is deleted.

Create the foreign key like this:

```sql
CREATE TABLE transactions(
    t_id INT PRIMARY KEY AUTO_INCREMENT,
    amount DECIMAL(5,2),
    customer_id INT,

    CONSTRAINT fk_c_id
    FOREIGN KEY(customer_id)
    REFERENCES customers(c_id)
    ON DELETE CASCADE
);
```

Now:

```sql
DELETE FROM customers
WHERE c_id = 1;
```

MySQL automatically deletes:

```text
Customer 1
AND
All related transactions
```

---

# Solution 4: ON DELETE SET NULL

Instead of deleting child records, MySQL can automatically set the foreign key to NULL.

```sql
CREATE TABLE transactions(
    t_id INT PRIMARY KEY AUTO_INCREMENT,
    amount DECIMAL(5,2),
    customer_id INT,

    CONSTRAINT fk_c_id
    FOREIGN KEY(customer_id)
    REFERENCES customers(c_id)
    ON DELETE SET NULL
);
```

When customer 1 is deleted:

Before:

|t_id|amount|customer_id|
|---|---|---|
|1|99.99|1|

After:

|t_id|amount|customer_id|
|---|---|---|
|1|99.99|NULL|

The transaction remains but loses its customer reference.

---

# Referential Integrity Rule

A foreign key guarantees:

> Every foreign key value must either:
> 
> - Match an existing primary key value in the parent table, or
>     
> - Be NULL (if NULLs are allowed).
>     

Because of this rule, MySQL prevents deleting parent rows that are still being referenced.

---

# Summary

Without special options:

```sql
DELETE FROM customers
WHERE c_id = 1;
```

fails if child rows exist.

Possible solutions:

|Method|Result|
|---|---|
|Delete child rows first|Parent can be deleted|
|Set child foreign keys to NULL|Parent can be deleted|
|ON DELETE CASCADE|Child rows deleted automatically|
|ON DELETE SET NULL|Foreign keys become NULL automatically|

This behavior exists to maintain **referential integrity** and prevent orphan records in the database.

A useful way to think about it:

- **Primary Key** = "I am the record being referenced."
    
- **Foreign Key** = "I depend on another record."
    
- **ON DELETE CASCADE** = "If the parent goes away, delete me too."

# SQL Joins — Interview Notes (Obsidian Friendly)

## What is a JOIN?

A **JOIN** is used to combine rows from two or more tables based on a related column between them.

In your example:

- **customers** → Left Table
    
- **transactions** → Right Table
    
- Common column:
    
    ```sql
    customers.c_id = transactions.customer_id
    ```
    

---

# Sample Tables

## customers

|c_id|name|
|---|---|
|1|Alice|
|2|Bob|
|3|Charlie|
|4|David|

## transactions

|transaction_id|customer_id|amount|
|---|---|---|
|101|1|500|
|102|1|700|
|103|2|300|
|104|5|1000|

---

# 1. INNER JOIN

## Definition

Returns only matching records from both tables.

```sql
SELECT
    c.*,
    t.amount AS transfer
FROM customers c
INNER JOIN transactions t
ON c.c_id = t.customer_id;
```

### Result

|c_id|name|transfer|
|---|---|---|
|1|Alice|500|
|1|Alice|700|
|2|Bob|300|

### Visualization

```text
Customers    Transactions

   (A) ∩ (B)

Only common records
```

### Interview Point

Most commonly used join.

Use when:

- You only need matching data.
    
- Ignore orphan records.
    

Example:

```sql
Get customers who have made transactions.
```

---

# 2. LEFT JOIN

## Definition

Returns:

- All rows from left table
    
- Matching rows from right table
    
- NULL if no match
    

```sql
SELECT
    c.*,
    t.amount AS transfer
FROM customers c
LEFT JOIN transactions t
ON c.c_id = t.customer_id;
```

### Result

|c_id|name|transfer|
|---|---|---|
|1|Alice|500|
|1|Alice|700|
|2|Bob|300|
|3|Charlie|NULL|
|4|David|NULL|

### Visualization

```text
(A)

All records from customers
+ matching transactions
```

### Use Cases

Find customers who never purchased:

```sql
SELECT c.*
FROM customers c
LEFT JOIN transactions t
ON c.c_id = t.customer_id
WHERE t.customer_id IS NULL;
```

### Interview Question

**Find customers without transactions.**

```sql
SELECT c.*
FROM customers c
LEFT JOIN transactions t
ON c.c_id = t.customer_id
WHERE t.customer_id IS NULL;
```

---

# 3. RIGHT JOIN

## Definition

Returns:

- All rows from right table
    
- Matching rows from left table
    
- NULL if no match
    

```sql
SELECT
    c.*,
    t.amount AS transfer
FROM customers c
RIGHT JOIN transactions t
ON c.c_id = t.customer_id;
```

### Result

|c_id|name|transfer|
|---|---|---|
|1|Alice|500|
|1|Alice|700|
|2|Bob|300|
|NULL|NULL|1000|

(customer_id = 5 doesn't exist)

### Visualization

```text
(B)

All records from transactions
+ matching customers
```

### Use Cases

Find invalid transactions:

```sql
SELECT t.*
FROM customers c
RIGHT JOIN transactions t
ON c.c_id = t.customer_id
WHERE c.c_id IS NULL;
```

---

# 4. FULL OUTER JOIN

## Definition

Returns:

- All rows from left table
    
- All rows from right table
    
- Matching where possible
    

### MySQL Note

MySQL does **NOT** support FULL OUTER JOIN directly.

Simulate using:

```sql
SELECT
    c.*,
    t.amount
FROM customers c
LEFT JOIN transactions t
ON c.c_id = t.customer_id

UNION

SELECT
    c.*,
    t.amount
FROM customers c
RIGHT JOIN transactions t
ON c.c_id = t.customer_id;
```

### Visualization

```text
(A) + (B)

Everything from both tables
```

### Use Cases

Data reconciliation.

Example:

```sql
Compare customer records and transaction records.
```

---

# 5. CROSS JOIN

## Definition

Returns Cartesian Product.

Every row from first table joins every row from second table.

```sql
SELECT *
FROM customers
CROSS JOIN transactions;
```

### Formula

```text
Rows Returned

= rows in table A × rows in table B
```

Example:

```text
4 customers × 4 transactions = 16 rows
```

### Use Cases

Generate combinations.

Example:

```sql
Products × Sizes
Students × Subjects
```

---

# 6. SELF JOIN

## Definition

A table joined with itself.

Useful when rows relate to other rows in the same table.

Example employee hierarchy:

|emp_id|emp_name|manager_id|
|---|---|---|
|1|John|NULL|
|2|Sam|1|
|3|Mike|1|

```sql
SELECT
    e.emp_name AS Employee,
    m.emp_name AS Manager
FROM employees e
LEFT JOIN employees m
ON e.manager_id = m.emp_id;
```

### Result

|Employee|Manager|
|---|---|
|John|NULL|
|Sam|John|
|Mike|John|

### Use Cases

- Employee ↔ Manager
    
- Category ↔ Parent Category
    
- Referral Systems
    

---

# 7. NATURAL JOIN

## Definition

Automatically joins columns with the same name.

```sql
SELECT *
FROM customers
NATURAL JOIN transactions;
```

### Warning ⚠️

Rarely used in production.

Reason:

```text
Schema changes can break queries unexpectedly.
```

Prefer:

```sql
INNER JOIN ... ON ...
```

---

# JOIN Comparison Table

|Join Type|Matching Records|Left Unmatched|Right Unmatched|
|---|---|---|---|
|INNER JOIN|✅|❌|❌|
|LEFT JOIN|✅|✅|❌|
|RIGHT JOIN|✅|❌|✅|
|FULL OUTER JOIN|✅|✅|✅|
|CROSS JOIN|Every Combination|N/A|N/A|
|SELF JOIN|Same Table|Depends|Depends|
|NATURAL JOIN|Auto Match Columns|Depends|Depends|

---

# Frequently Asked Interview Questions

## Q1: Difference between INNER JOIN and LEFT JOIN?

### INNER JOIN

Returns only matching rows.

```sql
SELECT *
FROM customers c
INNER JOIN transactions t
ON c.c_id = t.customer_id;
```

### LEFT JOIN

Returns all customers even if transaction doesn't exist.

```sql
SELECT *
FROM customers c
LEFT JOIN transactions t
ON c.c_id = t.customer_id;
```

---

## Q2: How to find records that do not match?

### Customers without transactions

```sql
SELECT c.*
FROM customers c
LEFT JOIN transactions t
ON c.c_id = t.customer_id
WHERE t.customer_id IS NULL;
```

---

## Q3: How to find orphan transactions?

```sql
SELECT t.*
FROM customers c
RIGHT JOIN transactions t
ON c.c_id = t.customer_id
WHERE c.c_id IS NULL;
```

---

## Q4: Which join is fastest?

Generally:

```text
INNER JOIN
    ↓
LEFT/RIGHT JOIN
    ↓
FULL OUTER JOIN (simulated)
    ↓
CROSS JOIN
```

Actual performance depends on:

- Indexes
    
- Table size
    
- Query plan
    
- Database engine
    

---

# Real-World Examples

## Banking

```sql
customers
transactions
```

Find customer transaction history.

```sql
SELECT c.name, t.amount
FROM customers c
INNER JOIN transactions t
ON c.c_id = t.customer_id;
```

---

## E-Commerce

```sql
orders
customers
```

Find order owner.

```sql
SELECT o.order_id, c.name
FROM orders o
JOIN customers c
ON o.customer_id = c.customer_id;
```

---

## HR Management

```sql
employees
departments
```

Find employee department.

```sql
SELECT e.emp_name, d.department_name
FROM employees e
JOIN departments d
ON e.department_id = d.department_id;
```

---

# Interview One-Liner

```text
INNER JOIN  -> Only matching records
LEFT JOIN   -> All left + matching right
RIGHT JOIN  -> All right + matching left
FULL JOIN   -> Everything from both tables
CROSS JOIN  -> Every combination
SELF JOIN   -> Table joined with itself
NATURAL JOIN-> Auto join on same column names
```

> Rule to remember: "The table written before JOIN is the LEFT table, and the table written after JOIN is the RIGHT table."

# MySQL Functions 
---

# Why Do Functions Exist?

Functions exist to:

1. **Avoid repeating logic**
    
2. **Improve readability**
    
3. **Encapsulate business rules**
    
4. **Transform data**
    
5. **Perform calculations**
    
6. **Handle NULL values**
    
7. **Reuse logic across queries**
    

Without functions:

```sql
SELECT salary * 12
FROM employees;
```

With reusable function:

```sql
SELECT AnnualSalary(salary)
FROM employees;
```

---

# Types of Functions in MySQL

## 1. Built-in Functions

Already provided by MySQL.

Examples:

```sql
COUNT()
SUM()
AVG()
MAX()
MIN()
NOW()
UPPER()
LOWER()
COALESCE()
IFNULL()
DATEDIFF()
CONCAT()
```

---

## 2. User Defined Functions (UDF)

Functions created by developers.

Example:

```sql
DELIMITER $$

CREATE FUNCTION AnnualSalary(monthlySalary DECIMAL(10,2))
RETURNS DECIMAL(12,2)

BEGIN
    RETURN monthlySalary * 12;
END $$

DELIMITER ;
```

Usage:

```sql
SELECT AnnualSalary(25000);
```

Output:

```text
300000
```

---

# Built-in Functions Every .NET + MySQL Developer Should Know

---

# NULL Handling Functions

## COALESCE()

Returns first non-null value.

```sql
SELECT COALESCE(NULL,NULL,'John');
```

Output:

```text
John
```

---

Example:

```sql
SELECT
    employee_name,
    COALESCE(phone,'Not Available')
FROM employees;
```

### Why useful?

Without COALESCE:

```text
NULL
```

With COALESCE:

```text
Not Available
```

---

## IFNULL()

MySQL specific.

```sql
SELECT IFNULL(NULL,'Unknown');
```

Output:

```text
Unknown
```

---

Difference:

```sql
COALESCE(NULL,NULL,'A')
```

works with multiple values.

```sql
IFNULL(NULL,'A')
```

works with only two values.

---

# String Functions

---

## CONCAT()

```sql
SELECT CONCAT(first_name,' ',last_name);
```

Output:

```text
Tony Stark
```

---

## UPPER()

```sql
SELECT UPPER('tony');
```

Output:

```text
TONY
```

---

## LOWER()

```sql
SELECT LOWER('TONY');
```

Output:

```text
tony
```

---

## LENGTH()

```sql
SELECT LENGTH('Tony');
```

Output:

```text
4
```

---

## SUBSTRING()

```sql
SELECT SUBSTRING('Anthony',1,3);
```

Output:

```text
Ant
```

---

## REPLACE()

```sql
SELECT REPLACE('Tony Stark','Tony','Ironman');
```

Output:

```text
Ironman Stark
```

---

# Date Functions

Very common in enterprise applications.

---

## NOW()

Current date + time

```sql
SELECT NOW();
```

---

## CURDATE()

Current date

```sql
SELECT CURDATE();
```

---

## YEAR()

```sql
SELECT YEAR('2025-01-10');
```

Output:

```text
2025
```

---

## MONTH()

```sql
SELECT MONTH('2025-01-10');
```

Output:

```text
1
```

---

## DATEDIFF()

```sql
SELECT DATEDIFF('2025-01-10','2025-01-01');
```

Output:

```text
9
```

---

## TIMESTAMPDIFF()

Age calculation interview favorite.

```sql
SELECT
TIMESTAMPDIFF(YEAR,birth_date,CURDATE())
AS age
FROM employees;
```

---

# Aggregate Functions

Used with GROUP BY.

---

## COUNT()

```sql
SELECT COUNT(*)
FROM employees;
```

---

## SUM()

```sql
SELECT SUM(salary)
FROM employees;
```

---

## AVG()

```sql
SELECT AVG(salary)
FROM employees;
```

---

## MAX()

```sql
SELECT MAX(salary)
FROM employees;
```

---

## MIN()

```sql
SELECT MIN(salary)
FROM employees;
```

---

# Conditional Functions

---

## IF()

```sql
SELECT
IF(salary > 50000,
   'High',
   'Low');
```

---

## CASE

Interview favorite.

```sql
SELECT
employee_name,
CASE
    WHEN salary >= 50000 THEN 'Senior'
    WHEN salary >= 30000 THEN 'Mid'
    ELSE 'Junior'
END AS category
FROM employees;
```

---

# Numeric Functions

---

## ROUND()

```sql
SELECT ROUND(123.456,2);
```

Output:

```text
123.46
```

---

## CEIL()

```sql
SELECT CEIL(12.1);
```

Output:

```text
13
```

---

## FLOOR()

```sql
SELECT FLOOR(12.9);
```

Output:

```text
12
```

---

## ABS()

```sql
SELECT ABS(-100);
```

Output:

```text
100
```

---

# User Defined Functions (UDF)

---

## Create Function

```sql
DELIMITER $$

CREATE FUNCTION GetBonus
(
    salary DECIMAL(10,2)
)
RETURNS DECIMAL(10,2)

BEGIN

    RETURN salary * 0.10;

END $$

DELIMITER ;
```

---

Usage:

```sql
SELECT GetBonus(50000);
```

Output:

```text
5000
```

---

# Can a Function Exist Without Returning a Value?

## In MySQL: NO

Every function must return something.

This is mandatory:

```sql
RETURNS datatype
```

and

```sql
RETURN value;
```

Example:

```sql
CREATE FUNCTION Test()
RETURNS INT

BEGIN

END
```

❌ Invalid

---

Valid:

```sql
CREATE FUNCTION Test()
RETURNS INT

BEGIN

    RETURN 1;

END
```

✅ Valid

---

# Then How Do We Execute Logic Without Returning Anything?

Use a **Stored Procedure**.

---

## Procedure Example

```sql
DELIMITER $$

CREATE PROCEDURE IncreaseSalary()
BEGIN

    UPDATE employees
    SET salary = salary + 1000;

END $$

DELIMITER ;
```

Execute:

```sql
CALL IncreaseSalary();
```

Notice:

```text
Procedure -> May return nothing
Function  -> Must return a value
```

---

# Function vs Procedure

|Feature|Function|Procedure|
|---|---|---|
|Must Return Value|✅ Yes|❌ No|
|Can be used in SELECT|✅ Yes|❌ No|
|Can return multiple result sets|❌ No|✅ Yes|
|Mainly for calculations|✅ Yes|⚠️ Sometimes|
|Business process execution|❌ Not ideal|✅ Ideal|

---

# How to Retrieve Function Return Value?

### Directly

```sql
SELECT GetBonus(50000);
```

---

### Alias

```sql
SELECT GetBonus(50000) AS Bonus;
```

---

### Store in Variable

```sql
SET @bonus = GetBonus(50000);

SELECT @bonus;
```

---

# Real .NET Developer Use Cases

### COALESCE

Avoid nulls in APIs

```sql
SELECT
COALESCE(email,'No Email')
FROM customers;
```

---

### CONCAT

Full Name generation

```sql
SELECT CONCAT(first_name,' ',last_name)
FROM employees;
```

---

### CASE

Status mapping

```sql
CASE
WHEN status = 1 THEN 'Active'
ELSE 'Inactive'
END
```

---

### DATEDIFF

Order aging

```sql
SELECT DATEDIFF(CURDATE(),order_date);
```

---

### COUNT

Dashboard cards

```sql
SELECT COUNT(*)
FROM customers;
```

---

### SUM

Revenue reports

```sql
SELECT SUM(amount)
FROM transactions;
```

---

# Interview One-Liners

```text
COALESCE()  -> First non-null value
IFNULL()    -> Replace null with value
CONCAT()    -> Join strings
DATEDIFF()  -> Difference between dates
COUNT()     -> Number of rows
SUM()       -> Total
AVG()       -> Average
CASE        -> Conditional logic
ROUND()     -> Decimal rounding
NOW()       -> Current timestamp
```

```text
Function:
- Must return one value
- Can be used inside SELECT

Procedure:
- May or may not return values
- Executed using CALL
- Used for business operations and data modifications
```
