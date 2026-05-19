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