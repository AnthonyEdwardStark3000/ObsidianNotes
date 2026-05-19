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