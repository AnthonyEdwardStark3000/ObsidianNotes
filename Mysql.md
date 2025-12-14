can copy and paste this entire block directly into Obsidian or any Markdown editor.

---

# Overview

**Data:** Raw unprocessed facts  
**Database:** Organized collection of data and it supports data storage and manipulation of data.  
**DBMS:** Platform to manage the database.

![[Pasted image 20250413185133.png|400|400]]  

![alt text](./images/Pasted%20image%2020250413185133.png)

  
![[Pasted image 20250413185314.png|300|300]]

## Types of DBMS

- Flatfile DBMS
    
- Hierarchical DBMS
    
- Network DBMS
    
- Relational DBMS
    
- Non-relational DBMS
    

### Relational DBMS (RDBMS)

Here data will be stored in Rows and Columns format (Table format).  
![[Pasted image 20250413185523.png|500|500]]  
![[Pasted image 20250413185645.png|400|400]]

Here the data will be stored in a predefined format.  
![[Pasted image 20250413185736.png|400|400]]

**Example:** The insert operation can be performed only if the data is in correct format as the created table structure.  
![[Pasted image 20250413185845.png |400|400]]

And follows a relationship between tables.  
![[Pasted image 20250413185940.png]]

---

# SQL (Structured Query Language)

DBMS is an interface between the users and the database, and SQL acts as a native language for communication with the database.  
![[Pasted image 20250413190540.png |300|300]]

## Types of SQL commands

1. **DDL** (Data Definition Language)
    
2. **DML** (Data Manipulation Language)
    
3. **DQL** (Data Query Language)
    
4. **TCL** (Transaction Control Language)
    
5. **DCL** (Data Control Language)
    

### 1. DDL (Data Definition Language)

The commands that define the structure of Database objects.

- **CREATE:** Creating and defining the columns that should be available in the database table.
    
- **ALTER:** For changing the structure of the objects.
    
- **TRUNCATE:** For deleting the data in the table along with the space allotted to it; here table structure will remain.
    
- **DROP:** To drop the database object completely along with its table structure.
    

![[Pasted image 20250413191644.png |900|]]

### 2. DML (Data Manipulation Language)

Commands used to manipulate the data in the database.

- **INSERT:** For inserting a new record into the database.
    
- **UPDATE:** For modifying the data already present.
    
- **DELETE:** For deleting the already present data.
    

![[Pasted image 20250413192008.png | 400 |600]]

### 3. DQL (Data Query Language)

For retrieving the data present in the database.

- **SELECT:** Used for retrieving the data present in the database.
    

![[Pasted image 20250413192136.png|400|300]]

### 4. TCL (Transaction Control Language)

Used to manage transactions (a group of statements that should execute together).

- **COMMIT:** If all statements execute successfully, save changes.
    
- **ROLLBACK:** If any statement fails, revert changes.
    
- **SAVE:** A save point for transactions for partial rollbacks.
    

![[Pasted image 20250413192712.png]]

### 5. DCL (Data Control Language)

Mostly used by administrators for providing and removing access.

- **GRANT:** For providing database access.
    
- **REVOKE:** For removing database access.
    

![[Pasted image 20250413192855.png]]

---

# Basic Usage of Common SQL Commands

code SQL

downloadcontent_copy

expand_less

    `-- create database CREATE DATABASE university;  -- use that database USE university;  -- create table in that database CREATE TABLE students(     rollno INTEGER,     name VARCHAR(300),     department VARCHAR(200),     age INTEGER,     date_of_birth DATE,     gender CHAR(1) );  SELECT * FROM students;  -- insert into table INSERT INTO students VALUES(1,'student1','MCA',21,'2000-01-01','M');  -- insert another one column to the table structure ALTER TABLE students ADD gpa FLOAT;  -- update the gpa column value in the above inserted table UPDATE students SET gpa = 12.1 WHERE rollno=1;  ALTER TABLE students DROP COLUMN age;  -- Delete a record from the database  DELETE FROM students WHERE rollno = 1;  -- truncate table TRUNCATE TABLE students;  -- drop table , delete the structure DROP TABLE students;  -- delete the database DROP DATABASE university;`
  

---

# Where Clause

**Operators:** =, <>, <, >, <=, >=, BETWEEN, IN, LIKE

code SQL

downloadcontent_copy

expand_less

    `SELECT TOP (1000) [AddressID] ,[AddressLine1] ,[AddressLine2] ,[City] ,[StateProvinceID] ,[PostalCode] ,[SpatialLocation] ,[rowguid] ,[ModifiedDate] FROM [AdventureWorks2019].[Person].[Address]  SELECT TOP(10) * FROM Person.Address;  -- WHERE CLAUSE EXAMPLES SELECT * FROM Production.Product WHERE ProductID = 322; SELECT * FROM Production.Product WHERE ProductID >= 322; SELECT * FROM Production.Product WHERE ProductID <= 322;  SELECT * FROM Production.Product WHERE ProductID >= 200 AND ProductID<=900; SELECT * FROM Production.Product WHERE ProductID BETWEEN 300 AND 500; SELECT * FROM Production.Product WHERE Color = 'Silver'; SELECT * FROM Production.Product WHERE Color <> 'Silver'; SELECT * FROM Production.Product WHERE Color IN ('Silver','Black','Red'); SELECT * FROM Production.Product WHERE Color NOT IN ('Silver','Black','Red'); SELECT * FROM Production.Product WHERE Color = 'Silver' AND StandardCost > 1000.00; SELECT * FROM Production.Product WHERE Color = 'Silver' OR StandardCost > 1000.00; SELECT * FROM Production.Product WHERE Size IS NULL; SELECT * FROM Production.Product WHERE Size IS NOT NULL; SELECT * FROM Production.Product WHERE SellStartDate = '2008-04-30'; SELECT * FROM Production.Product WHERE SellStartDate BETWEEN '2008-04-30' AND '2012-05-30';`
  

## Wildcards in SQL

Used when we don't know the exact value.

code SQL

downloadcontent_copy

expand_less

    `-- wildcards SELECT * FROM Production.Product WHERE ProductNumber LIKE 'FC%'; SELECT * FROM Production.Product WHERE Name LIKE '%Cage'; SELECT * FROM Production.Product WHERE Name LIKE '%Frame'; SELECT * FROM Production.Product WHERE ProductNumber LIKE 'FR%R38%2'; SELECT * FROM Production.Product WHERE ProductNumber LIKE 'FR-R38B-2'; SELECT * FROM Production.Product WHERE ProductNumber LIKE 'R%';  -- Bracket usage SELECT * FROM Person.Person WHERE FirstName LIKE 'A[ab]%'; SELECT * FROM Person.Address WHERE AddressLine1 LIKE '[a-z]%'; SELECT * FROM Person.Address WHERE AddressLine1 LIKE '[0-9]%'; SELECT * FROM Person.Address WHERE AddressLine1 LIKE '[a-z0-9]%'; SELECT * FROM Person.Address WHERE AddressLine1 LIKE '[a-z0-9#$]%'; SELECT * FROM Person.Address WHERE PostalCode LIKE '[0-9][0-9][0-9][0-9][0-9]';  -- Not in bracket SELECT * FROM Production.Product WHERE ProductNumber LIKE 'FR-R92%'; SELECT * FROM Production.Product WHERE ProductNumber LIKE 'FR-R92[^B]%'; SELECT * FROM Person.Address WHERE AddressLine1 LIKE '[^a-z0-9]%'; SELECT * FROM Person.Address WHERE AddressLine1 LIKE '%%';  -- To display the address that contains _ in it's AddressLine1 SELECT * FROM Person.Address WHERE AddressLine1 LIKE '%[]%';`
  

---

# SQL Constraints

Applying rules for the data in the table.

### Primary Key

code SQL

downloadcontent_copy

expand_less

    `CREATE TABLE students (     StudentID INTEGER PRIMARY KEY,     FirstName VARCHAR(30),     LastName VARCHAR(20),     DateOfBirth DATE,     Gender CHAR(1) );  -- OR via Constraint Name CREATE TABLE students (     StudentID INTEGER,     FirstName VARCHAR(30),     LastName VARCHAR(20),     DateOfBirth DATE,     Gender CHAR(1),     CONSTRAINT Pk_students PRIMARY KEY(StudentID) );  -- Using ALTER (Must be Non-nullable) CREATE TABLE students (     StudentID INTEGER NOT NULL,     FirstName VARCHAR(30),     LastName VARCHAR(20),     DateOfBirth DATE,     Gender CHAR(1) );  ALTER TABLE students ADD PRIMARY KEY(StudentID); ALTER TABLE students ADD CONSTRAINT Pk_students PRIMARY KEY(StudentID);  ALTER TABLE students DROP CONSTRAINT Pk_students;`
  

**Composite Key:** Making two or more columns as Primary key.

code SQL

downloadcontent_copy

expand_less

    `CREATE TABLE OrderDetail (     OrderID INTEGER,     ProductID INTEGER,     DateOfPurchase DATE,     Price FLOAT,     CONSTRAINT pk_orderdetail PRIMARY KEY(OrderID,ProductID) );  -- Using ALTER CREATE TABLE OrderDetail (OrderID INTEGER NOT NULL, ProductID INTEGER NOT NULL, DateOfPurchase DATE, Price FLOAT); ALTER TABLE OrderDetail ADD CONSTRAINT pk_orderdetail PRIMARY KEY(OrderID,ProductID);`
  

### NOT NULL Constraint

code SQL

downloadcontent_copy

expand_less

    `CREATE TABLE OrderDetail (     OrderID INTEGER NOT NULL,     ProductID INTEGER,     DateOfPurchase DATE,     Price FLOAT );  -- Using ALTER statement ALTER TABLE OrderDetail ALTER COLUMN ProductID INTEGER NOT NULL;`
  

### Unique Constraints

code SQL

downloadcontent_copy

expand_less

    `-- Unique constraint while creating a table CREATE TABLE students (     StudentID INTEGER,     FirstName VARCHAR(30),     LastName VARCHAR(20),     DateOfBirth DATE,     Gender CHAR(1),     AadharNumber BIGINT UNIQUE );  -- Unique constraint by adding constraint name CREATE TABLE students (     StudentID INTEGER,     FirstName VARCHAR(30),     LastName VARCHAR(20),     DateOfBirth DATE,     Gender CHAR(1),     AadharNumber BIGINT,     CONSTRAINT Uc_students UNIQUE(StudentID) );  -- Using ALTER ALTER TABLE students ADD UNIQUE(AadharNumber); ALTER TABLE students ADD CONSTRAINT Uc_students UNIQUE(AadharNumber);  -- Drop constraint ALTER TABLE students DROP CONSTRAINT Uc_students;`
  

### Check Constraints

code SQL

downloadcontent_copy

expand_less

    `CREATE TABLE employee(     EmployeeID INTEGER PRIMARY KEY,      FirstName VARCHAR(200),     LastName VARCHAR(200),     DateOfBirth DATE,     Gender CHAR(1),     Salary INT CHECK(Salary>3000) );  -- Check constraint using alter ALTER TABLE employee ADD CHECK(Salary>3000); ALTER TABLE employee ADD CONSTRAINT CHK_Employee CHECK(Salary>3000 AND DateOfBirth>='1980-01-02');  -- Drop the check constraint ALTER TABLE employee DROP CONSTRAINT CHK_Employee;`
  

### Default Constraint

code SQL

downloadcontent_copy

expand_less

    `CREATE TABLE NewStudents(     StudentID INTEGER PRIMARY KEY,     FirstName VARCHAR(100),     LastName VARCHAR(100),     DateOfBirth DATE,     Gender CHAR(1),     Country VARCHAR(10) DEFAULT 'India' );  INSERT INTO NewStudents(StudentID,FirstName,LastName,DateOfBirth,Gender) VALUES(12,'FName','LName','12-02-24','M');  SELECT * FROM NewStudents;  -- Adding default constraint using alter statement ALTER TABLE NewStudents ADD CONSTRAINT Df_students DEFAULT 'India' FOR Country;  -- Drop constraint ALTER TABLE NewStudents DROP CONSTRAINT Df_students;`
  

### Foreign Key Constraint

Particular column of a table referring PK of another table.

code SQL

downloadcontent_copy

expand_less

    `CREATE TABLE Course(     CourseID INTEGER PRIMARY KEY,     CourseName VARCHAR(100),     StaffName VARCHAR(100) );  INSERT INTO Course(CourseID,CourseName,StaffName) VALUES(1,'Physics','Name'); INSERT INTO Course VALUES(2,'Maths','Name'),(3,'Computer','Name'),(4,'Tamil','Name');  -- Foreign Key CREATE TABLE Students(     StudentID INTEGER PRIMARY KEY,     FirstName VARCHAR(100),     LastName VARCHAR(100),     DateOfBirth DATE,     Gender CHAR(1),     CourseID INTEGER FOREIGN KEY REFERENCES Course(CourseID) );  -- Using ALTER ALTER TABLE Students ADD CONSTRAINT Fk_Students FOREIGN KEY (CourseID) REFERENCES Course(CourseID);  -- Drop constraint ALTER TABLE Students DROP CONSTRAINT Fk_Students;`
  

---

# Aggregate Functions

Reads a set of values as Input and returns a single value as output.

code SQL

downloadcontent_copy

expand_less

    `SELECT COUNT(ProductID) FROM Production.Product; SELECT SUM(ListPrice) FROM Production.Product; SELECT MIN(ListPrice) FROM Production.Product WHERE ListPrice > 0; SELECT MAX(ListPrice) FROM Production.Product; SELECT AVG(ListPrice) FROM Production.Product;`
  

### Group By

Used for grouping a particular column having same value and performing operations based on that value.

code SQL

downloadcontent_copy

expand_less

    `SELECT Color,COUNT(Color) AS CountInNumbers FROM Production.Product GROUP BY Color;  SELECT Color,SUM(ListPrice) AS total_list_price FROM Production.Product WHERE Color IS NOT NULL GROUP BY Color;  SELECT Color,Size,AVG(ListPrice) AS avg_list_price FROM Production.Product  WHERE Color IS NOT NULL AND Size IS NOT NULL  GROUP BY Color,Size ORDER BY Color,Size;`
  

### Having Clause

WHERE is used for rows, HAVING is used for aggregates (always with Group By).

code SQL

downloadcontent_copy

expand_less

    `SELECT Color,COUNT(ProductID) AS num_of_products  FROM Production.Product  WHERE Color IS NOT NULL  GROUP BY Color HAVING COUNT(ProductID)>10;  SELECT Color,COUNT(ProductID) AS num_of_products  FROM Production.Product  WHERE Color IS NOT NULL GROUP BY Color HAVING SUM(ListPrice)>300;`
  

---

# Joins

Joining rows between two tables by using the related columns.

### Inner Join

Retrieves records common to both tables.

code SQL

downloadcontent_copy

expand_less

    `CREATE TABLE Employee(EmployeeID INTEGER PRIMARY KEY,FirstName VARCHAR(100),LastName VARCHAR(100),DateOfBirth DATE, Gender CHAR(1),DepartmentID INTEGER);  CREATE TABLE Department(DepartmentID INTEGER,DepartmentName VARCHAR(100));  SELECT * FROM Employee INNER JOIN Department ON Employee.DepartmentID = Department.DepartmentID; -- or with aliases SELECT e.FirstName,e.LastName,d.DepartmentName FROM Employee e INNER JOIN Department d on e.DepartmentID = d.DepartmentID;`
  

### Outer Joins

- **Left Outer Join:** Left table takes advantage (All from Left + Matching from Right).
    
    code SQL
    
    downloadcontent_copy
    
    expand_less
    
        `SELECT * FROM Department d LEFT JOIN Employee e ON d.DepartmentID = e.DepartmentID;`
      
    
- **Right Outer Join:** Right table takes advantage (All from Right + Matching from Left).
    
    code SQL
    
    downloadcontent_copy
    
    expand_less
    
        `SELECT * FROM Department d RIGHT JOIN Employee e ON d.DepartmentID = e.DepartmentID;`
      
    
- **Full Outer Join:** All records from both tables.
    
    code SQL
    
    downloadcontent_copy
    
    expand_less
    
        `SELECT * FROM Department d FULL JOIN Employee e ON d.DepartmentID = e.DepartmentID;`
      
    

### Self Join

Joining a table with itself (e.g., Employees and Managers).

code SQL

downloadcontent_copy

expand_less

    `ALTER TABLE Employee ADD ManagerID INTEGER;  SELECT e1.EmployeeID, e1.FirstName, e1.LastName, e1.ManagerID, e2.FirstName+' '+e2.LastName AS ManagerName FROM Employee e1 JOIN Employee e2 ON e1.EmployeeID = e2.ManagerID;`
  

### Cross Join

Cartesian product (All records from A × All records from B).

code SQL

downloadcontent_copy

expand_less

    `SELECT e1.FirstName+' '+e1.LastName AS Employee_1, e2.FirstName+' '+e2.LastName AS Employee_2  FROM employee e1 CROSS JOIN Employee e2;`
  

---

# Views

Virtual tables that don't take physical memory. Used for hiding complexity.

code SQL

downloadcontent_copy

expand_less

    `-- Creating View CREATE VIEW employee_dept_details AS SELECT e.EmployeeID,e.FirstName,e.LastName,e.DepartmentID,d.DepartmentName FROM Employee e JOIN Department d ON e.DepartmentID = d.DepartmentID;  -- Executing View SELECT * FROM employee_dept_details;  -- Altering View ALTER VIEW employee_details AS SELECT * FROM Employee WHERE EmployeeID <> 1001;  -- Drop View DROP VIEW employee_details;`
  

---

# SubQueries

code SQL

downloadcontent_copy

expand_less

    `SELECT * FROM Sales.SalesTerritory WHERE TerritoryID = (     SELECT TerritoryID FROM Sales.SalesPerson WHERE rowguid = '52A5179D-3239-4157-AE29-17E868296DC0' );  -- Update salary based on average UPDATE Employees SET salary = ( SELECT AVG(salary) FROM Employees ) WHERE salary < ( SELECT AVG(salary) FROM Employees );`
  

### Correlated Subquery

Inner Query depends on the Outer Query.

code SQL

downloadcontent_copy

expand_less

    `-- List all employees whose salary is less than the avg salary in that department SELECT * FROM Employees E1  WHERE Salary < (SELECT AVG(Salary) FROM Employees E2 WHERE E2.Department_ID = E1.Department_ID);`
  

### Exists / Not Exists

code SQL

downloadcontent_copy

expand_less

    `SELECT * FROM Salesman s WHERE EXISTS (     SELECT 1 FROM orders o WHERE s.salesman_id = o.salesman_id );`
  

### Any / All

code SQL

downloadcontent_copy

expand_less

    `-- Salary greater than average of ANY department SELECT * FROM employees WHERE Salary > ANY(     SELECT avg_salary FROM (         SELECT department_id, AVG(salary) AS avg_salary FROM employees GROUP BY department_id     ) AS temp );  -- Salary less than ALL employees in Dept 30 SELECT * FROM employees WHERE salary < ALL (     SELECT salary FROM employees WHERE department_id = 30 );`
  

---

# CTE (Common Table Expression)

Temporary named result set.

code SQL

downloadcontent_copy

expand_less

    `WITH low_quantity_product AS (     SELECT ProductID,SUM(Quantity) AS Total_Quantity      FROM Production.ProductInventory     GROUP BY ProductID HAVING SUM(Quantity)<100 ) SELECT QP.ProductID, Total_Quantity, PV.StandardPrice  FROM low_quantity_product QP  JOIN Purchasing.ProductVendor PV ON QP.ProductID = PV.ProductID;`
  

---

# Window Functions

Performs a calculation across a set of table rows related to the current row.

code SQL

downloadcontent_copy

expand_less

    `-- Aggregation with Partition SELECT *, SUM(Salary) OVER(PARTITION BY department_id) AS TOTAL_SALARY FROM employees;  -- Running Total SELECT *, SUM(Salary) OVER(PARTITION BY department_id ORDER BY employee_id) AS TOTAL_SALARY FROM employees;`
  

### Value Window Functions

- **FIRST_VALUE / LAST_VALUE**
    
- **LAG / LEAD**
    

code SQL

downloadcontent_copy

expand_less

    `-- First Value SELECT ProductID, StandardCost, ModifiedDate, FIRST_VALUE(StandardCost) OVER(PARTITION BY ProductID ORDER BY ModifiedDate) AS Initial_value  FROM Production.ProductCostHistory;  -- LEAD AND LAG (Previous and Next values) SELECT ProductID, StandardCost, ModifiedDate, LAG(StandardCost) OVER(PARTITION BY ProductID ORDER BY ModifiedDate) AS Previous_value, LEAD(StandardCost) OVER(PARTITION BY ProductID ORDER BY ModifiedDate) AS Next_value  FROM Production.ProductCostHistory;`
  

### Ranking Functions

- **ROW_NUMBER():** Unique sequential integer.
    
- **RANK():** Rank with gaps for duplicates (1, 1, 3).
    
- **DENSE_RANK():** Rank without gaps (1, 1, 2).
    
- **NTILE():** Divides into buckets.
    

code SQL

downloadcontent_copy

expand_less

    `-- Row Number to find latest data WITH Latest_data AS (     SELECT ProductID, StandardCost, ModifiedDate,     ROW_NUMBER() OVER(PARTITION BY ProductID ORDER BY ModifiedDate DESC) AS Rno     FROM Production.ProductCostHistory ) SELECT * FROM Latest_data WHERE Rno = 1;  -- Dense Rank SELECT *, DENSE_RANK() OVER(PARTITION BY DEPARTMENT_ID ORDER BY SALARY DESC) AS DENSE_RANK  FROM EmployeesManager;`
  

---

# Temp Tables

Stored in tempdb.

code SQL

downloadcontent_copy

expand_less

    `-- Local Temp Table (Session specific) SELECT * INTO #tmp_person FROM Production.Product; -- OR CREATE TABLE #tmp_person_id(ProductID INTEGER);  -- Global Temp Table (Visible to all) SELECT * INTO ##tmp_person_global FROM Production.Product;`
  

---

# Stored Procedures

Pre-compiled code.

code SQL

downloadcontent_copy

expand_less

    `-- With parameter CREATE PROCEDURE GetEmployeeDataByDeptID @personID INT AS BEGIN     SELECT * FROM Person.Person WHERE BusinessEntityID=@personID END  EXEC GetEmployeeDataByDeptID 10;  -- With Output parameter ALTER PROCEDURE GetEmployeeDataByDeptID @personID INT = 10, @personCount INT OUT AS BEGIN     SELECT @personCount = COUNT(*) FROM Person.Person WHERE BusinessEntityID = @personID END`
  

---

# Indexes

Improves speed of data retrieval.

- **Clustered Index:** Determines physical order of data (Only 1 per table).
    
- **Non-Clustered Index:** Logical order, pointers to data.
    

code SQL

downloadcontent_copy

expand_less

    `-- Create Non-Clustered CREATE INDEX idx_lastName ON EmployeeIndexNonClusteredIndex(LastName);  -- Create Clustered CREATE CLUSTERED INDEX idx_clstr_lastName ON EmployeeIndexNonClusteredIndex(LastName);  -- Drop Index DROP INDEX EmployeeIndexNonClusteredIndex.idx_clstr_lastName;`
  

---

# Triggers

Automated SQL statements on events.

code SQL

downloadcontent_copy

expand_less

    `CREATE TRIGGER trg_emp_audit ON Employee AFTER INSERT AS  BEGIN     INSERT INTO employees_audit     SELECT EmployeeID, 'INSERT', GETDATE() FROM inserted END;`
  

---

# Functions in SQL

- **Scalar Functions:** Returns single value.
    
- **Table Valued Functions:** Returns a table.
    

code SQL

downloadcontent_copy

expand_less

    `-- Scalar Function CREATE FUNCTION dbo.udf_add_numbers(@a INT, @b INT) RETURNS INT BEGIN     RETURN @a + @b END  SELECT dbo.udf_add_numbers(2,10);  -- Table Valued Function (Inline) CREATE FUNCTION dbo.udf_EmpByDept(@deptID INT) RETURNS TABLE AS RETURN SELECT * FROM Employee WHERE EmployeeID = @deptID;`
  

---

# Cursors

Used for row-by-row processing.

code SQL

downloadcontent_copy

expand_less

    `DECLARE @id INT DECLARE @value INT DECLARE @runningTotal INT = 0 DECLARE RunningTotalCursor CURSOR FOR SELECT ID, Value FROM SalesData ORDER BY ID  OPEN RunningTotalCursor FETCH NEXT FROM RunningTotalCursor INTO @id, @value WHILE @@FETCH_STATUS = 0 BEGIN     SET @runningTotal = @runningTotal + @value     UPDATE SalesData SET RunningTotal = @runningTotal WHERE ID = @id     FETCH NEXT FROM RunningTotalCursor INTO @id, @value END CLOSE RunningTotalCursor DEALLOCATE RunningTotalCursor`
  

---

# Transactions & Merge

code SQL

downloadcontent_copy

expand_less

    `BEGIN TRANSACTION     UPDATE BankAccount SET Balance = Balance - 1000 WHERE AccountNumber = 3456789012;     UPDATE BankAccount SET Balance = Balance + 1000 WHERE AccountNumber = 1122334455;  IF @@ERROR <> 0     ROLLBACK TRANSACTION ELSE     COMMIT TRANSACTION`
  

### Merge Statement

code SQL

downloadcontent_copy

expand_less

    `MERGE EmployeeTarget AS T USING EmployeeSource AS S ON T.Employee_ID = S.Employee_ID  WHEN MATCHED THEN     UPDATE SET T.FIRST_NAME = S.FIRST_NAME WHEN NOT MATCHED BY TARGET THEN     INSERT(Employee_ID, FIRST_NAME) VALUES(S.Employee_ID, S.FIRST_NAME) WHEN NOT MATCHED BY SOURCE THEN DELETE;`
  

---

# Recursive CTE

Used for hierarchical data.

code SQL

downloadcontent_copy

expand_less

    `WITH generative_numbers AS(     SELECT 1 AS number      UNION ALL     SELECT number + 1 FROM generative_numbers     WHERE number < 50 ) SELECT * FROM generative_numbers;`
  

---

# Dynamic SQL

Changing the query during runtime.

code SQL

downloadcontent_copy

expand_less

    `DECLARE @sql NVARCHAR(MAX) SET @sql = 'SELECT * FROM employees' EXEC sp_executesql @sql;  -- With parameters DECLARE @sql2 NVARCHAR(MAX) DECLARE @emp_id INT = 105 SET @sql2 = 'SELECT * FROM employees WHERE employee_id = ' + CAST(@emp_id AS VARCHAR) EXEC sp_executesql @sql2;`
  

---

---

# Tech with hema - Interview Notes & Flashcards

## MySQL Functions Summary

### Key Points

- Return only 1 value
    
- No DML statements
    
- No OUT parameters
    
- Can be used in SELECT
    
- Cannot return tables
    

### Function vs Procedure

- **Function** → 1 value, no DML
    
- **Procedure** → complex logic, tables, DML, OUT parameters
    

---

## Obsidian Flashcards

### What is a MySQL function?

What is a MySQL function?

<!--SR-->  

A stored program that takes input and returns **one scalar value**.

### Can MySQL functions return multiple values?

Can MySQL functions return multiple values?

<!--SR-->  

==No==, only one scalar value is allowed.

### Can MySQL functions perform DML (INSERT/UPDATE/DELETE)?

Can MySQL functions perform DML?

<!--SR-->  

==No==, DML is not allowed in MySQL functions.

### Difference: Function vs Procedure — return values

Function vs Procedure: return values?

<!--SR-->  

Function → ==must return 1 value==  
Procedure → ==0 or many result sets==

### Difference: Function vs Procedure — DML

Which supports DML (INSERT/UPDATE/DELETE)?

<!--SR-->  

==Stored procedure only==

### Output parameters

Do MySQL functions support IN, OUT, INOUT parameters?

<!--SR-->  

==Only IN==; OUT/INOUT not allowed.

---

## Stored Procedure Performance Tuning

### 1. Index Usage Inside Stored Procedures

**What is an Index?**  
An index is a database structure that speeds up data retrieval by reducing full table scans.

**Example: SP WITHOUT Index (Slow)**

code SQL

downloadcontent_copy

expand_less

    `CREATE PROCEDURE GetOrdersByCustomer @CustomerId INT AS BEGIN     SELECT * FROM Orders WHERE CustomerId = @CustomerId; END;`
  

- Result: Table Scan.
    

**Add Proper Index (Huge Improvement)**

code SQL

downloadcontent_copy

expand_less

    `CREATE INDEX IX_Orders_CustomerId ON Orders(CustomerId);`
  

- Result: Index Seek.
    

### 2. Parameter Sniffing

SQL Server uses the first parameter value passed to SP to generate an execution plan and reuses it.

**Solution: OPTION (RECOMPILE)**

code SQL

downloadcontent_copy

expand_less

    `SELECT * FROM Orders WHERE CustomerId = @CustomerId OPTION (RECOMPILE);`
  

### 3. Deadlocks

Occurs when two transactions wait for each other’s locked resources indefinitely.  
**Prevention:**

1. Always Access Tables in Same Order.
    
2. Keep Transactions Short.
    
3. Use Proper Indexes.
    

### 4. Isolation Levels

- **READ UNCOMMITTED:** Fastest, Dirty Reads.
    
- **READ COMMITTED:** Default.
    
- **SNAPSHOT:** Uses row versioning, avoids blocking.
    

---

## Temporary Tables (Temp Tables)

**Definition:** A temporary table is created at runtime, stored in tempdb, and automatically removed when its session ends.

**Method 1: SELECT INTO**

code SQL

downloadcontent_copy

expand_less

    `SELECT * INTO #TempOrders FROM Orders WHERE OrderDate >= '2024-01-01';`
  

**Method 2: CREATE TABLE (Best Practice)**

code SQL

downloadcontent_copy

expand_less

    `CREATE TABLE #TempOrders (OrderId INT, Amount DECIMAL(10,2)); INSERT INTO #TempOrders SELECT OrderId, Amount FROM Orders;`
  

**Temp Tables vs CTEs**

- **Temp Table:** Stored physically, Index allowed, Reusable, Best for large data.
    
- **CTE:** Not stored physically, No Index, Best for readability/recursion.
    

---

## Hierarchical Data (Recursive CTE)

**Definition:** Data organized in a parent–child relationship (e.g., Org Chart).

**Example: Recursive CTE**

code SQL

downloadcontent_copy

expand_less

    `WITH EmployeeHierarchy AS (     -- Anchor member (root)     SELECT EmployeeId, EmployeeName, ManagerId, 0 AS Level     FROM Employees WHERE ManagerId IS NULL      UNION ALL      -- Recursive member     SELECT e.EmployeeId, e.EmployeeName, e.ManagerId, eh.Level + 1     FROM Employees e     INNER JOIN EmployeeHierarchy eh ON e.ManagerId = eh.EmployeeId ) SELECT * FROM EmployeeHierarchy;`