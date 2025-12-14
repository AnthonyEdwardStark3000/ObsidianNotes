
-- Tech with hema
---
# 📘 **MySQL Functions — Complete Notes (Obsidian-Friendly)**

---

## ## 🧩 **What is a Function in MySQL?**

A **function** in MySQL is a stored program that:

* Accepts **input parameters**
* Performs **calculations or operations**
* Returns **exactly one value** (scalar)

🔔 **Important:**
Unlike SQL Server or PostgreSQL, **MySQL does NOT support table-valued functions**.
MySQL UDFs (User Defined Functions) can only return a **scalar** value.
Returning a table is **not possible** from a MySQL FUNCTION.

If table-like results are needed → use:

* Views
* Stored procedures (with SELECT result sets)
* JSON returning functions

---

# ## ⭐ **Advantages of Functions in MySQL**

* ✔ Can be used **inside SQL queries** (SELECT, WHERE, ORDER BY)
* ✔ Increases code reusability
* ✔ Improves maintainability
* ✔ Useful for **business rules**, **calculations**, **data formatting**
* ✔ Executes faster for repetitive logic
* ✔ Helps maintain consistent logic across the system

---

# ## 🧨 **Function Limitations in MySQL**

* ❌ Cannot perform **DML** (INSERT / UPDATE / DELETE)
* ❌ Cannot return a **table**
* ❌ Cannot use transactions (COMMIT/ROLLBACK)
* ❌ No OUT parameters
* ✔ Only **IN parameters** are allowed
* ✔ Must return **ONE scalar value**

---

# ## 🔄 Functions & DML Statements

MySQL functions **cannot** modify data.

```sql
-- ❌ Not allowed inside a FUNCTION
INSERT INTO ...
UPDATE ...
DELETE ...
CREATE TABLE ...
```

Why?
Functions must be **deterministic** and safe to be used inside queries.

---

# ## 🎯 Output Parameters & Multiple Return Values

MySQL functions:

* ❌ do NOT support OUT parameters
* ❌ do NOT support returning multiple values
* ✔ You can only return **one scalar value**

To simulate multiple values:

* return a JSON string
* return a delimited string

Example:

```sql
RETURN JSON_OBJECT('name', v_name, 'age', v_age);
```

---

# ## 🧪 **System Functions vs User-Defined Functions (UDF)**

### ### 1️⃣ **System Functions**

Built-in MySQL functions:

Examples:

```sql
SELECT NOW(), CONCAT('hi',' there'), ABS(-5), ROUND(3.14);
```

---

### ### 2️⃣ **User-Defined Functions (UDF) — Scalar**

Created by users; must return **one value**.

Example function:

```sql
CREATE FUNCTION add_tax(price DECIMAL(10,2))
RETURNS DECIMAL(10,2)
DETERMINISTIC
BEGIN
    RETURN price * 1.18;
END;
```

Use:

```sql
SELECT add_tax(100);
```

---

# ## 🪄 Scalar Functions Used Like Columns

You can use scalar functions anywhere a column expression is allowed:

```sql
SELECT id, name, add_tax(price) AS price_with_tax
FROM products
WHERE add_tax(price) > 500;
```

---

# ## 🔧 BEGIN / DECLARE / IF ELSE in MySQL Functions

### ### **Basic Function Example**

```sql
DELIMITER $$

CREATE FUNCTION grade(marks INT)
RETURNS VARCHAR(10)
DETERMINISTIC
BEGIN
    DECLARE result VARCHAR(10);

    IF marks >= 90 THEN
        SET result = 'A';
    ELSEIF marks >= 75 THEN
        SET result = 'B';
    ELSE
        SET result = 'C';
    END IF;

    RETURN result;
END $$

DELIMITER ;
```

Use:

```sql
SELECT grade(88);
```

---

# ## 🔁 **Altering a Function**

MySQL does NOT support `ALTER FUNCTION` directly.

To alter:

1. Drop the function
2. Recreate it

```sql
DROP FUNCTION IF EXISTS grade;

CREATE FUNCTION grade(...)
...
```

---

# # ❗ **About Table-Valued Functions in MySQL**

### ### 🚫 MySQL does **NOT** support:

* Inline table-valued functions
* Multi-statement table-valued functions
* Returning table variables

These exist in SQL Server, not in MySQL.

### ✔ MySQL alternatives:

* Views (static)
* Stored procedures (return result sets)
* JSON-returning functions

---

# ## 🧵 **Table-Valued Function Equivalent (Parameterized View)**

### MySQL workaround: Stored Procedure with parameters

```sql
DELIMITER $$

CREATE PROCEDURE get_orders_by_customer(IN cid INT)
BEGIN
    SELECT * FROM orders WHERE customer_id = cid;
END $$

DELIMITER ;
```

Call:

```sql
CALL get_orders_by_customer(5);
```

---

# # 🧩 **Function Calling Another Function in MySQL**

Example:

```sql
CREATE FUNCTION get_discount(price DECIMAL(10,2))
RETURNS DECIMAL(10,2)
DETERMINISTIC
BEGIN
    RETURN price * 0.10;
END;
```

Create second function:

```sql
CREATE FUNCTION final_price(price DECIMAL(10,2))
RETURNS DECIMAL(10,2)
DETERMINISTIC
BEGIN
    RETURN price - get_discount(price); -- calling another function
END;
```

Use:

```sql
SELECT final_price(100);
```

---

# # ⚔️ **MySQL Functions vs Stored Procedures**

| Feature             | Function               | Stored Procedure                    |
| ------------------- | ---------------------- | ----------------------------------- |
| Return value        | ✔ Must return 1 scalar | ✔ Can return 0, 1, many result sets |
| Output parameters   | ❌ Not allowed          | ✔ IN, OUT, INOUT                    |
| DML allowed         | ❌ No                   | ✔ Yes                               |
| Use in SELECT       | ✔ Yes                  | ❌ No                                |
| Transaction control | ❌ No                   | ✔ Yes                               |
| Return table        | ❌ No                   | ✔ Yes (via SELECT)                  |
| Error handling      | Limited                | Advanced                            |
| Use case            | Simple calculations    | Complex business logic              |

---

# ## 📘 Example: Function vs Stored Procedure

### ### 1️⃣ Function — scalar calculation

```sql
CREATE FUNCTION calc_bonus(salary DECIMAL(10,2))
RETURNS DECIMAL(10,2)
DETERMINISTIC
BEGIN
    RETURN salary * 0.20;
END;
```

Use:

```sql
SELECT name, calc_bonus(salary) FROM employee;
```

---

### ### 2️⃣ Stored Procedure — return table + perform logic

```sql
DELIMITER $$

CREATE PROCEDURE employee_bonus_report()
BEGIN
    SELECT name,
           salary,
           (salary * 0.20) AS bonus
    FROM employee;
END $$

DELIMITER ;
```

Use:

```sql
CALL employee_bonus_report();
```

---

# # 🚀 Production-Level Function Example

### Tax calculation + JSON multi-value return

```sql
DELIMITER $$

CREATE FUNCTION product_summary(pid INT)
RETURNS JSON
DETERMINISTIC
BEGIN
    DECLARE p_name VARCHAR(100);
    DECLARE p_price DECIMAL(10,2);
    DECLARE p_tax DECIMAL(10,2);

    SELECT name, price INTO p_name, p_price
    FROM products
    WHERE id = pid;

    SET p_tax = p_price * 0.18;

    RETURN JSON_OBJECT(
        'name', p_name,
        'price', p_price,
        'tax', p_tax,
        'price_with_tax', p_price + p_tax
    );
END $$

DELIMITER ;
```

Use:

```sql
SELECT product_summary(3);
```

---

# # 🧱 Full Example: Professional Stored Procedure (Parameterized View)

```sql
DELIMITER $$

CREATE PROCEDURE sales_report(
    IN start_date DATE,
    IN end_date DATE,
    IN min_amount DECIMAL(10,2)
)
BEGIN
    SELECT order_id, customer_id, total_amount, order_date
    FROM sales
    WHERE order_date BETWEEN start_date AND end_date
      AND total_amount >= min_amount
    ORDER BY order_date DESC;
END $$

DELIMITER ;
```

Call:

```sql
CALL sales_report('2024-01-01','2024-01-31', 500);
```

---

# # 📘 Summary (Copy-Paste Friendly for Obsidian)

``
## MySQL Functions Summary

### Key Points
- Return only 1 value
- No DML statements
- No OUT parameters
- Can be used in SELECT
- Cannot return tables

### Types
- System Functions
- User Defined Scalar Functions

### Alternatives to Table-Valued Functions
- Stored Procedures
- Views
- JSON returning functions

# Function vs Procedure

- Function → 1 value, no DML
- Procedure → complex logic, tables, DML, OUT parameters
``
Below are **two deliverables** exactly as you requested:

1. **Obsidian Flashcards (using ==cloze== + spaced-repetition syntax)**
2. **A Complete MySQL Functions Cheat-Sheet Page (Obsidian friendly)**

Everything is optimized for **Obsidian + Anki-style spaced repetition** and can be pasted directly into your vault.

---

# 🧠 **1. Obsidian Flashcards (Ready-to-Paste)**

Format uses the Obsidian/Anki plugin syntax:
``
## MySQL Functions — Flashcards

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


### Can functions be used in SELECT statements?
Can MySQL functions be used in SELECT?  
<!--SR-->  
==Yes==, they work like column expressions.  


### Can stored procedures be used inside SELECT?
Can stored procedures be used inside SELECT queries?  
<!--SR-->  
==No==, procedures cannot be used in SELECT.  


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


### MySQL table-valued functions support
Does MySQL support table-valued functions?  
<!--SR-->  
==No==, only scalar functions.  

### Alternatives to table-valued functions
Alternatives to table-valued functions in MySQL?  
<!--SR-->  
==Stored procedures==, ==views==, ==JSON returning functions==  


### BEGIN / END usage in functions
BEGIN/END allowed in MySQL functions?  
<!--SR-->  
==Yes==, functions can use BEGIN, DECLARE, IF, CASE, etc.  


### Function calling another function
Can one MySQL function call another?  
<!--SR-->  
==Yes==, functions can call other functions.  


### ALTER FUNCTION in MySQL
How do you modify a MySQL function?  
<!--SR-->  
==DROP and CREATE== (no direct ALTER FUNCTION).  


### Deterministic keyword
What does DETERMINISTIC mean in a function?  
<!--SR-->  
The function always returns the ==same output for the same input==.  


### System functions
Examples of system functions?  
<!--SR-->  
==NOW() , CONCAT(), ABS(), ROUND()==  


### User-defined functions
What must a user-defined function return?  
<!--SR-->  
==One scalar value==.  
``

---

# 📘 **2. Complete MySQL Functions Cheat-Sheet (Obsidian Page)**

Perfect for your vault as a structured reference guide.
``
# MySQL Functions — Complete Cheat-Sheet

---

## 📌 Overview
MySQL functions are stored programs that **accept input and return exactly one value**.  
They are commonly used for **calculations, formatting, validation**, and can be used inside queries.

---

## ✔ Advantages
- Reusable business logic  
- Can be used in SELECT, WHERE, ORDER BY  
- Performance benefits for repeated logic  
- Ensures consistent computations  

---

## ❌ Limitations
- No INSERT, UPDATE, DELETE  
- No OUT/INOUT parameters  
- No transactions  
- No multiple return values  
- Cannot return a table  
- Must return exactly ONE value  

---

## 🧪 Types of Functions

### 1️⃣ System Functions (Built-In)
Examples:
- `NOW()`
- `CONCAT()`
- `ABS()`
- `CEIL()`
- `LOWER()`

### 2️⃣ User-Defined Functions (UDF)
- Created with `CREATE FUNCTION`
- Must return one scalar value
- Can contain logic (IF/ELSE/CASE)

---

## 🧱 Function Syntax Template

```sql
DELIMITER $$

CREATE FUNCTION function_name(param datatype)
RETURNS return_datatype
DETERMINISTIC
BEGIN
    -- variable declarations
    -- logic
    RETURN value;
END $$

DELIMITER ;
````

---

## ✨ Basic Example: Scalar Function

```sql
CREATE FUNCTION add_tax(price DECIMAL(10,2))
RETURNS DECIMAL(10,2)
DETERMINISTIC
BEGIN
    RETURN price * 1.18;
END;
```

Usage:

```sql
SELECT add_tax(100);
```

---

## ⚙ BEGIN / DECLARE / IF Example

```sql
DELIMITER $$

CREATE FUNCTION grade(marks INT)
RETURNS VARCHAR(5)
DETERMINISTIC
BEGIN
    DECLARE result VARCHAR(5);

    IF marks >= 90 THEN
        SET result = 'A';
    ELSEIF marks >= 75 THEN
        SET result = 'B';
    ELSE
        SET result = 'C';
    END IF;

    RETURN result;
END $$

DELIMITER ;
```

---

## 🔁 Calling a Function from Another Function

```sql
CREATE FUNCTION discount(price DECIMAL(10,2))
RETURNS DECIMAL(10,2)
DETERMINISTIC
BEGIN
    RETURN price * 0.10;
END;

CREATE FUNCTION final_price(price DECIMAL(10,2))
RETURNS DECIMAL(10,2)
DETERMINISTIC
BEGIN
    RETURN price - discount(price);
END;
```

---

## ❌ Table-Valued Functions in MySQL

MySQL does **not** support TVFs (unlike SQL Server).

### Alternatives:

* Stored procedures (return result sets)
* Views
* JSON-returning scalar functions

---

## JSON Return Example (emulating multi-value output)

```sql
DELIMITER $$

CREATE FUNCTION product_summary(pid INT)
RETURNS JSON
DETERMINISTIC
BEGIN
    DECLARE pname VARCHAR(100);
    DECLARE pprice DECIMAL(10,2);

    SELECT name, price INTO pname, pprice
    FROM products WHERE id = pid;

    RETURN JSON_OBJECT(
        'name', pname,
        'price', pprice,
        'price_with_tax', pprice * 1.18
    );
END $$

DELIMITER ;
```

---

## 🔨 How to Modify a Function (No ALTER)

```
DROP FUNCTION IF EXISTS grade;

CREATE FUNCTION grade(...) ...
```

---

## ⚔️ Functions vs Stored Procedures

### ✔ When to Use Functions

* Formatting values
* Calculation logic
* Reusable rules
* Query expressions

### ✔ When to Use Stored Procedures

* Multiple SQL statements
* DML operations
* Returning tables
* Business workflows
* Using OUT/INOUT params

---

## 🧩 Comparison Table

| Feature        | Function  | Procedure    |
| -------------- | --------- | ------------ |
| Return value   | ONE value | None or Many |
| DML allowed    | ❌ No      | ✔ Yes        |
| OUT parameters | ❌ No      | ✔ Yes        |
| Use in SELECT  | ✔ Yes     | ❌ No         |
| Transactions   | ❌ No      | ✔ Yes        |
| Return table   | ❌ No      | ✔ Yes        |

---

## 📌 Stored Procedure Example (TVF Alternative)

```sql
DELIMITER $$

CREATE PROCEDURE get_orders_by_customer(IN cid INT)
BEGIN
    SELECT * FROM orders WHERE customer_id = cid;
END $$

DELIMITER ;
```

Usage:

```sql
CALL get_orders_by_customer(5);
```

---

## 📘 Production-Level Example

```sql
DELIMITER $$

CREATE FUNCTION calc_employee_rating(attendance INT, sales INT)
RETURNS VARCHAR(20)
DETERMINISTIC
BEGIN
    IF sales >= 500 AND attendance > 95 THEN
        RETURN 'Excellent';
    ELSEIF sales >= 300 THEN
        RETURN 'Good';
    ELSE
        RETURN 'Average';
    END IF;
END $$

DELIMITER ;
```

Usage:

```sql
SELECT employee_name, calc_employee_rating(attendance, sales)
FROM employees;
```

---

# 🔐 Title: Advanced Stored Procedures Concepts (Encryption, CTE, Functions & More)

## 🔐 1. Encryption in Stored Procedures

### ✅ Definition (Interview-Ready)

**Encryption in Stored Procedures** is used to **hide the internal SQL logic** of the procedure from users.  
It prevents others from viewing or reverse-engineering business logic stored inside the database.

> Encryption protects **intellectual property**, **business rules**, and **security-sensitive queries**.

---

### 🔹 Why Encrypt Stored Procedures?

- 🔒 Protect business logic
    
- 🛡 Prevent unauthorized access
    
- 📦 Hide complex calculations
    
- 🧠 Prevent accidental modification
    

---

### 🔹 Creating an Encrypted Stored Procedure

```sql
CREATE PROCEDURE GetEmployeeSalary
WITH ENCRYPTION
AS
BEGIN
    SELECT EmployeeId, Salary
    FROM Employees;
END;
```

📌 After encryption:

```sql
sp_helptext GetEmployeeSalary;
-- Result: The text is encrypted and cannot be displayed
```

---

### ⚠ Important Interview Notes

- Encryption is **not strong cryptography**
    
- SQL Server encrypts metadata, **not runtime data**
    
- Once encrypted → **cannot be decrypted**
    
- Always keep **source code backup**
    

---

## 🔁 2. CTE (Common Table Expression) Inside Stored Procedures

---

### ✅ Definition

A **CTE** is a **temporary named result set** used to simplify **complex queries**, improve **readability**, and support **recursive logic**.

---

### 🔹 Why Use CTE in Stored Procedures?

- Replace complex subqueries
    
- Improve readability
    
- Perform hierarchical / recursive queries
    
- Reuse result inside the SP
    

---

### 🔹 Basic CTE Example Inside SP

```sql
CREATE PROCEDURE GetHighSalaryEmployees
AS
BEGIN
    WITH HighSalaryCTE AS (
        SELECT EmployeeId, Name, Salary
        FROM Employees
        WHERE Salary > 70000
    )
    SELECT * FROM HighSalaryCTE;
END;
```

---

### 🔹 CTE with Aggregation

```sql
CREATE PROCEDURE GetDepartmentWiseSalary
AS
BEGIN
    WITH DeptCTE AS (
        SELECT DepartmentId, SUM(Salary) AS TotalSalary
        FROM Employees
        GROUP BY DepartmentId
    )
    SELECT * FROM DeptCTE;
END;
```

---

### 🔹 Recursive CTE in Stored Procedure (Hierarchy)

```sql
CREATE PROCEDURE GetEmployeeHierarchy
AS
BEGIN
    WITH EmployeeCTE AS (
        SELECT EmployeeId, ManagerId, Name
        FROM Employees
        WHERE ManagerId IS NULL

        UNION ALL

        SELECT e.EmployeeId, e.ManagerId, e.Name
        FROM Employees e
        INNER JOIN EmployeeCTE c
        ON e.ManagerId = c.EmployeeId
    )
    SELECT * FROM EmployeeCTE;
END;
```

📌 **Very commonly asked in interviews**

---

## 🧮 3. Functions vs Stored Procedures

---

### ✅ Definition

A **Function** is a database object that:

- Always returns a value
    
- Can be used inside SELECT
    
- Cannot modify data (generally)
    

---

### 🔹 Types of Functions

|Type|Description|
|---|---|
|Scalar Function|Returns single value|
|Table-Valued Function|Returns table|
|Inline TVF|Lightweight, optimized|

---

## 🔹 Scalar Function Example

```sql
CREATE FUNCTION dbo.CalculateTax (@Salary DECIMAL)
RETURNS DECIMAL
AS
BEGIN
    RETURN @Salary * 0.10;
END;
```

Usage:

```sql
SELECT Name, dbo.CalculateTax(Salary) AS Tax
FROM Employees;
```

---

## 🔹 Table-Valued Function Example

```sql
CREATE FUNCTION dbo.GetEmployeesByDept (@DeptId INT)
RETURNS TABLE
AS
RETURN
(
    SELECT * FROM Employees WHERE DepartmentId = @DeptId
);
```

Usage:

```sql
SELECT * FROM dbo.GetEmployeesByDept(2);
```

---

### ⚠ Function vs SP (Interview Table)

|Feature|Function|Stored Procedure|
|---|---|---|
|Returns value|✅ Mandatory|❌ Optional|
|Can modify data|❌|✅|
|Can use TRY/CATCH|❌|✅|
|Can use Transactions|❌|✅|
|Can return multiple result sets|❌|✅|

---

## 🔁 4. Multiple Result Sets in Stored Procedure

---

### ✅ Definition

A Stored Procedure **can return multiple result sets** using multiple SELECT statements.

---

### 🔹 Example

```sql
CREATE PROCEDURE GetDashboardData
AS
BEGIN
    SELECT * FROM Customers;
    SELECT * FROM Orders;
    SELECT * FROM Products;
END;
```

📌 Very common for **dashboard APIs**

---

## 🔄 5. Multiple Operations in One Stored Procedure

### ✅ Interview Answer

**Yes**, a Stored Procedure can contain:

- Multiple SELECTs
    
- INSERT
    
- UPDATE
    
- DELETE
    
- All inside one transaction
    

---

### 🔹 Example: SELECT + UPDATE + DELETE

```sql
CREATE PROCEDURE ManageOrders
    @OrderId INT
AS
BEGIN
    BEGIN TRANSACTION;

    SELECT * FROM Orders WHERE OrderId = @OrderId;

    UPDATE Orders
    SET Status = 'Processed'
    WHERE OrderId = @OrderId;

    DELETE FROM OrderLogs
    WHERE OrderId = @OrderId;

    COMMIT TRANSACTION;
END;
```

---

## 🧪 6. TRY…CATCH & Error Handling in SP

```sql
CREATE PROCEDURE SafeUpdate
AS
BEGIN
    BEGIN TRY
        BEGIN TRANSACTION;
        UPDATE Accounts SET Balance = Balance - 100 WHERE Id = 1;
        COMMIT;
    END TRY
    BEGIN CATCH
        ROLLBACK;
        THROW;
    END CATCH
END;
```

---

## 🚀 7. Production-Ready Complex Stored Procedure

### 🔥 Example: Business Dashboard SP

```sql
CREATE PROCEDURE GetBusinessDashboard
    @StartDate DATE,
    @EndDate DATE
AS
BEGIN
    -- Customers
    SELECT COUNT(*) AS TotalCustomers FROM Customers;

    -- Revenue
    SELECT SUM(Amount) AS TotalRevenue
    FROM Orders
    WHERE OrderDate BETWEEN @StartDate AND @EndDate;

    -- Top Products
    SELECT TOP 5 ProductId, COUNT(*) AS Sales
    FROM Orders
    GROUP BY ProductId
    ORDER BY Sales DESC;

    -- Update audit
    UPDATE DashboardAudit
    SET LastGenerated = GETDATE();
END;
```

📌 **Perfect real-world SP example**

---

## 🎯 Interview One-Liners (Very Important)

- **CTE improves readability and recursion**
    
- **Encrypted SP hides business logic**
    
- **Functions return values, SPs perform actions**
    
- **SPs can handle transactions**
    
- **Multiple SELECTs = multiple result sets**
    
- **SPs are pre-compiled → better performance**
    

---

## 🧠 Final Interview Answer (Direct)

> **Yes**, a Stored Procedure can execute **multiple SELECT queries across different tables**, along with **multiple UPDATE and DELETE operations**, inside a **single transaction**, making it ideal for **complex business workflows**.

---
# 🚀 Title: Stored Procedure Performance Tuning

## Index Usage • Deadlocks • Isolation Levels

---

## 1️⃣ Stored Procedure Performance Tuning

### ✅ What is SP Performance Tuning? (Interview Definition)

**Stored Procedure performance tuning** is the process of **optimizing execution time, CPU usage, memory usage, and I/O cost** of stored procedures by improving **query design, indexing, parameter usage, and execution plans**.

---

## 🔥 Why SPs Can Become Slow?

Common real-world reasons:

- ❌ Missing or wrong indexes
    
- ❌ Parameter sniffing issues
    
- ❌ SELECT *
    
- ❌ Non-SARGable queries
    
- ❌ Large result sets
    
- ❌ Poor transaction handling
    
- ❌ Blocking & deadlocks
    

---

## 2️⃣ Index Usage Inside Stored Procedures

---

### ✅ What is an Index? (Quick Definition)

An **index** is a database structure that **speeds up data retrieval** by reducing full table scans.

> Indexes are the **#1 performance factor** in stored procedures.

---

## 🔹 How SQL Uses Indexes Inside SP

SQL Server:

1. Compiles SP
    
2. Creates **Execution Plan**
    
3. Chooses indexes based on:
    
    - WHERE clause
        
    - JOIN conditions
        
    - ORDER BY
        
    - GROUP BY
        

---

## 🔹 Example: SP WITHOUT Index (Slow)

```sql
CREATE PROCEDURE GetOrdersByCustomer
    @CustomerId INT
AS
BEGIN
    SELECT *
    FROM Orders
    WHERE CustomerId = @CustomerId;
END;
```

🚨 If `Orders.CustomerId` is **not indexed** → **Table Scan**

---

## 🔹 Add Proper Index (Huge Improvement)

```sql
CREATE INDEX IX_Orders_CustomerId
ON Orders(CustomerId);
```

✅ Result:

- Index Seek
    
- Faster execution
    
- Lower CPU & IO
    

---

## 🔹 Composite Index (Production-Ready)

```sql
CREATE INDEX IX_Orders_Customer_Date
ON Orders(CustomerId, OrderDate);
```

Best for queries like:

```sql
SELECT *
FROM Orders
WHERE CustomerId = @CustomerId
AND OrderDate >= '2024-01-01';
```

---

## 🔹 Covering Index (Advanced)

```sql
CREATE INDEX IX_Orders_Cover
ON Orders(CustomerId)
INCLUDE (OrderDate, Amount, Status);
```

📌 Prevents **Key Lookup**  
📌 Extremely important for high-traffic SPs

---

## ❌ Common Index Mistakes in SPs

|Mistake|Impact|
|---|---|
|SELECT *|Index ignored|
|Functions in WHERE|Index not used|
|CAST/CONVERT|Non-SARGable|
|LIKE '%abc'|Index scan|

---

## 🔹 Bad Query (Index Ignored)

```sql
WHERE YEAR(OrderDate) = 2024
```

### ✅ Optimized Query

```sql
WHERE OrderDate >= '2024-01-01'
AND OrderDate < '2025-01-01'
```

---

## 3️⃣ Parameter Sniffing (Very Important)

---

### ✅ What is Parameter Sniffing?

SQL Server **uses first parameter value** passed to SP to generate execution plan and **reuses it** for future executions.

📌 This can cause **performance degradation**.

---

### 🔹 Example Problem

```sql
EXEC GetOrdersByCustomer @CustomerId = 1;     -- small data
EXEC GetOrdersByCustomer @CustomerId = 9999; -- huge data
```

Same plan reused → inefficient

---

### ✅ Solutions

#### 🔹 OPTION (RECOMPILE)

```sql
SELECT *
FROM Orders
WHERE CustomerId = @CustomerId
OPTION (RECOMPILE);
```

#### 🔹 Local Variable Trick

```sql
DECLARE @LocalCustomerId INT = @CustomerId;

SELECT *
FROM Orders
WHERE CustomerId = @LocalCustomerId;
```

---

## 4️⃣ Deadlocks in Stored Procedures

---

### ✅ What is a Deadlock? (Interview Definition)

A **deadlock** occurs when **two or more transactions wait for each other’s locked resources indefinitely**, and SQL Server kills one transaction automatically.

---

### 🔥 Real-World Deadlock Example

Transaction 1:

```sql
UPDATE Accounts SET Balance -= 100 WHERE Id = 1;
UPDATE Accounts SET Balance += 100 WHERE Id = 2;
```

Transaction 2:

```sql
UPDATE Accounts SET Balance -= 50 WHERE Id = 2;
UPDATE Accounts SET Balance += 50 WHERE Id = 1;
```

📌 Classic deadlock scenario

---

## 🔹 How SQL Resolves Deadlock?

- SQL Server chooses **deadlock victim**
    
- Rolls back one transaction
    
- Throws error 1205
    

---

## 🛡 How to Prevent Deadlocks (Production Rules)

### ✅ 1. Always Access Tables in Same Order

```sql
-- Correct order everywhere
UPDATE Accounts WHERE Id = 1;
UPDATE Accounts WHERE Id = 2;
```

---

### ✅ 2. Keep Transactions Short

❌ BAD:

```sql
BEGIN TRAN
-- long business logic
COMMIT
```

✅ GOOD:

```sql
BEGIN TRAN
UPDATE ...
COMMIT
```

---

### ✅ 3. Use Proper Indexes

Indexes reduce lock duration  
➡ Faster execution  
➡ Less blocking

---

### ✅ 4. Use TRY/CATCH with Rollback

```sql
BEGIN TRY
    BEGIN TRAN
    -- statements
    COMMIT
END TRY
BEGIN CATCH
    ROLLBACK
END CATCH
```

---

## 5️⃣ Isolation Levels (VERY IMPORTANT)

---

### ✅ What is Isolation Level?

Isolation level defines **how and when data locks are applied** during transactions.

---

## 🔹 SQL Server Isolation Levels

|Level|Problems Allowed|
|---|---|
|Read Uncommitted|Dirty Reads|
|Read Committed|Default|
|Repeatable Read|No non-repeatable|
|Serializable|Full isolation|
|Snapshot|Version-based|

---

## 🔹 READ UNCOMMITTED (Fastest, Risky)

```sql
SET TRANSACTION ISOLATION LEVEL READ UNCOMMITTED;
```

- Allows dirty reads
    
- Used for reports
    

---

## 🔹 READ COMMITTED (Default)

```sql
SET TRANSACTION ISOLATION LEVEL READ COMMITTED;
```

- No dirty reads
    
- Allows blocking
    

---

## 🔹 SNAPSHOT ISOLATION (Best for High Concurrency)

```sql
ALTER DATABASE MyDB SET ALLOW_SNAPSHOT_ISOLATION ON;
```

```sql
SET TRANSACTION ISOLATION LEVEL SNAPSHOT;
```

📌 Uses row versioning  
📌 Avoids blocking & deadlocks  
📌 Excellent for APIs

---

## 6️⃣ Production-Ready Stored Procedure (All Concepts)

```sql
CREATE PROCEDURE TransferMoney
    @FromAccount INT,
    @ToAccount INT,
    @Amount DECIMAL(10,2)
AS
BEGIN
    SET NOCOUNT ON;
    SET TRANSACTION ISOLATION LEVEL READ COMMITTED;

    BEGIN TRY
        BEGIN TRANSACTION;

        UPDATE Accounts
        SET Balance = Balance - @Amount
        WHERE AccountId = @FromAccount;

        UPDATE Accounts
        SET Balance = Balance + @Amount
        WHERE AccountId = @ToAccount;

        COMMIT;
    END TRY
    BEGIN CATCH
        ROLLBACK;
        THROW;
    END CATCH
END;
```

✔ Indexed  
✔ Deadlock-safe order  
✔ Transaction safe  
✔ Production ready

---

## 🎯 Interview One-Line Answers

- **Indexes are the biggest performance factor in SPs**
    
- **Deadlocks occur due to conflicting locks**
    
- **Isolation level controls concurrency behavior**
    
- **Snapshot isolation reduces blocking**
    
- **Parameter sniffing causes inconsistent performance**

---
Below is a **complete, interview-ready + production-ready guide** on **TEMP TABLES in SQL Server**, written the same way senior backend / database interviews expect.

This is **concept → why → when → how → performance → comparisons → production patterns**.

---

# 🚀 Title: Temporary Tables (Temp Tables) in SQL Server

---

## 1️⃣ What is a Temp Table? (Interview Definition)

A **temporary table** is a table that is **created at runtime**, stored in the **tempdb system database**, and **automatically removed** when its **session or scope ends**.

📌 Used to **store intermediate results** during complex operations.

---

## 2️⃣ Why Temp Tables Exist (Real-World Need)

Temp tables are used when:

- Complex joins are expensive
    
- Same dataset is reused multiple times
    
- Large intermediate results are needed
    
- Indexing is required on intermediate data
    
- CTEs become unreadable or inefficient
    

---

## 3️⃣ Where Temp Tables Are Stored?

```
System Databases
 └── tempdb
     └── Temporary Tables
```

✔ Physically stored in **tempdb**  
✔ Managed automatically by SQL Server

---

## 4️⃣ How to Create Temp Tables

---

## 🔹 Method 1: SELECT INTO (Quick & Easy)

```sql
SELECT *
INTO #TempOrders
FROM Orders
WHERE OrderDate >= '2024-01-01';
```

✅ Automatically creates table  
❌ No control over data types  
❌ No constraints initially

---

## 🔹 Method 2: CREATE TABLE (Production Preferred)

```sql
CREATE TABLE #TempOrders
(
    OrderId INT,
    CustomerId INT,
    OrderDate DATE,
    Amount DECIMAL(10,2)
);
```

Then insert data:

```sql
INSERT INTO #TempOrders
SELECT OrderId, CustomerId, OrderDate, Amount
FROM Orders
WHERE OrderDate >= '2024-01-01';
```

✔ Full control  
✔ Best for production

---

## 🔹 Other Ways to Create Temp Tables

### ▶ From Stored Procedure Output

```sql
INSERT INTO #TempOrders
EXEC GetOrdersByDate '2024-01-01';
```

---

## 5️⃣ Operations Allowed on Temp Tables

Temp tables support **almost all operations**:

✔ SELECT  
✔ INSERT  
✔ UPDATE  
✔ DELETE  
✔ JOIN  
✔ INDEX  
✔ ALTER  
✔ CONSTRAINTS

🚫 Triggers (not allowed)

---

## 6️⃣ Scope & Session of Temp Tables

---

## 🔹 What is a Session?

A **session** is created when:

- You open a query window
    
- Application opens DB connection
    
- Stored procedure execution starts
    

Each session has a **unique SPID**.

---

## 🔹 Local Temp Table (`#Temp`)

```sql
CREATE TABLE #MyTempTable (...);
```

### Scope:

- Available **only in current session**
    
- Destroyed when:
    
    - Session ends
        
    - Stored procedure finishes
        

---

## 🔹 Example

```sql
CREATE PROCEDURE TestTemp
AS
BEGIN
    CREATE TABLE #Temp (Id INT);
END;
```

➡ `#Temp` disappears after SP execution

---

## 🔹 Global Temp Table (`##Temp`)

```sql
CREATE TABLE ##GlobalTemp
(
    Id INT
);
```

### Scope:

- Visible to **all sessions**
    
- Removed when **last session using it closes**
    

⚠️ Rarely recommended in production

---

## 7️⃣ Altering & Dropping Temp Tables

---

### 🔹 ALTER Temp Table

```sql
ALTER TABLE #TempOrders
ADD Status VARCHAR(20);
```

✔ Allowed  
✔ Common in complex flows

---

### 🔹 Drop Temp Table

```sql
DROP TABLE #TempOrders;
```

📌 Optional — SQL Server auto-cleans, but **explicit DROP is best practice**

---

## 8️⃣ How Temp Tables Are Automatically Removed?

SQL Server:

- Tracks temp table ownership via **session id**
    
- When session ends:
    
    - SQL Server deletes metadata
        
    - Frees space in tempdb
        

✔ Automatic lifecycle management

---

## 9️⃣ Indexing Temp Tables (🔥 HUGE PERFORMANCE BOOST)

---

### 🔹 Why Index Temp Tables?

Without index → Table Scan  
With index → Index Seek

Especially useful when:

- Temp table is large
    
- Used in joins
    
- Queried multiple times
    

---

### 🔹 Example Without Index (Slow)

```sql
SELECT *
FROM #TempOrders
WHERE CustomerId = 100;
```

---

### 🔹 Add Index

```sql
CREATE INDEX IX_TempOrders_CustomerId
ON #TempOrders(CustomerId);
```

📈 Massive performance improvement

---

## 🔹 Unique / Primary Key Constraint

```sql
ALTER TABLE #TempOrders
ADD CONSTRAINT PK_TempOrders PRIMARY KEY (OrderId);
```

### Benefits:

- Enforces uniqueness
    
- Automatically creates clustered index
    
- Faster joins
    
- Better execution plans
    

---

## 1️⃣0️⃣ Temp Tables vs CTEs (VERY IMPORTANT)

---

### 🔹 What is a CTE?

CTE = Common Table Expression  
It is **not stored** physically.

```sql
WITH OrderCTE AS (
    SELECT * FROM Orders WHERE Amount > 1000
)
SELECT * FROM OrderCTE;
```

---

## 🔥 Key Differences

|Feature|Temp Table|CTE|
|---|---|---|
|Stored physically|✅ Yes|❌ No|
|Index allowed|✅ Yes|❌ No|
|Reusable|✅ Yes|❌ No|
|Multiple references|✅ Yes|❌ Re-evaluated|
|Best for large data|✅ Yes|❌ No|

---

## 🔹 Are Temp Tables Faster Than CTEs?

👉 **YES**, when:

- Data is large
    
- Reused multiple times
    
- Indexed
    

CTE is better when:

- Simple queries
    
- Single-use logic
    
- Readability
    

---

## 1️⃣1️⃣ Complex Join: Normal vs Temp Table

---

### ❌ Normal Join (Expensive)

```sql
SELECT *
FROM Orders o
JOIN OrderItems oi ON o.Id = oi.OrderId
JOIN Products p ON oi.ProductId = p.Id
WHERE o.OrderDate >= '2024-01-01';
```

➡ Recalculates joins every time

---

### ✅ Using Temp Table (Optimized)

```sql
SELECT o.Id, o.CustomerId, o.OrderDate
INTO #TempOrders
FROM Orders o
WHERE o.OrderDate >= '2024-01-01';

CREATE INDEX IX_TempOrders_Id ON #TempOrders(Id);

SELECT *
FROM #TempOrders t
JOIN OrderItems oi ON t.Id = oi.OrderId
JOIN Products p ON oi.ProductId = p.Id;
```

📈 Faster  
📈 Reduced IO  
📈 Better execution plan

---

## 1️⃣2️⃣ Advantages of Temp Tables

✔ Improves performance  
✔ Supports indexing  
✔ Stores intermediate results  
✔ Improves readability  
✔ Reduces repeated computation  
✔ Excellent for reporting & batch jobs

---

## 1️⃣3️⃣ Concepts Used Along with Temp Tables

- Stored Procedures
    
- Transactions
    
- Indexes
    
- Constraints
    
- CTE (hybrid approach)
    
- Dynamic SQL
    
- TRY/CATCH
    
- Pagination
    
- Batch processing
    

---

## 1️⃣4️⃣ Production-Ready Temp Table Example

```sql
CREATE PROCEDURE GetCustomerSummary
AS
BEGIN
    CREATE TABLE #CustomerOrders
    (
        CustomerId INT PRIMARY KEY,
        TotalOrders INT,
        TotalAmount DECIMAL(12,2)
    );

    INSERT INTO #CustomerOrders
    SELECT 
        CustomerId,
        COUNT(*),
        SUM(Amount)
    FROM Orders
    GROUP BY CustomerId;

    SELECT *
    FROM #CustomerOrders
    WHERE TotalAmount > 10000;

    DROP TABLE #CustomerOrders;
END;
```

✔ Indexed  
✔ Aggregated  
✔ Clean lifecycle  
✔ Production quality

---

## 🎯 Interview One-Line Answers

- **Temp tables are stored in tempdb**
    
- **They support indexes and constraints**
    
- **Faster than CTEs for large reusable datasets**
    
- **Dropped automatically when session ends**
    
- **Best for complex joins & reporting**
    

---

## 🔥 Next Topics You May Want

- Temp table vs Table variable
    
- Memory grants & tempdb contention
    
- Batch processing patterns
    
- Pagination using temp tables
    
- SP + temp table best practices


✅ **CTE document is now fully generated** in the canvas with:

- Interview-ready **definitions**
    
- Clear **syntax explanation**
    
- **Beginner → production-ready examples**
    
- ✅ Joins with CTE
    
- ✅ Multiple CTEs with joins
    
- ✅ Recursive CTE (hierarchy)
    
- ✅ Comparisons with **SP, Functions, Temp Tables, Cursors, Triggers, Window Functions**
    
- ✅ Lifetime, use-cases, when to use & when not to use
    
- ✅ Final **one-paragraph interview summary**

---

> **Doubt:** What is hierarchical data and how is the data in that hierarchy retrieved?

---

## ✅ What is Hierarchical Data?

**Hierarchical data** is data that has a **parent–child relationship**, where each record can have:

- **One parent** (except the root)
    
- **Zero or more children**
    

This structure forms a **tree-like hierarchy**.

### 📌 Real-world examples

- Organization chart (CEO → Managers → Employees)
    
- Categories & subcategories (Electronics → Mobiles → Android)
    
- Menu & submenus
    
- Folder & subfolders
    
- Comments & replies
    

---

## 🧠 How is Hierarchical Data Stored in a Database?

Usually using a **self-referencing table**.

### Example Table: `Employees`

```sql
CREATE TABLE Employees (
    EmployeeId INT PRIMARY KEY,
    EmployeeName VARCHAR(100),
    ManagerId INT NULL
);
```

👉 `ManagerId` refers to **EmployeeId of the same table**

### Sample Data

```sql
INSERT INTO Employees VALUES
(1, 'CEO', NULL),
(2, 'CTO', 1),
(3, 'CFO', 1),
(4, 'Engineering Manager', 2),
(5, 'Developer', 4),
(6, 'Accountant', 3);
```

### Visual Hierarchy

```
CEO
├── CTO
│   └── Engineering Manager
│       └── Developer
└── CFO
    └── Accountant
```

---

## ❌ Why Normal SELECT Fails for Hierarchies

```sql
SELECT * FROM Employees;
```

🚫 This only returns **flat rows**, not parent–child relationships.

To traverse hierarchy → **Recursive Query is required**.

---

## ✅ Correct Way: Recursive CTE (Most Important)

### 🔑 Why CTE?

- CTE supports **recursion**
    
- Ideal for **hierarchical traversal**
    
- Clean, readable, production-safe
    

---

## 🔹 Basic Recursive CTE Example

```sql
WITH EmployeeHierarchy AS (
    -- Anchor member (root)
    SELECT
        EmployeeId,
        EmployeeName,
        ManagerId,
        0 AS Level
    FROM Employees
    WHERE ManagerId IS NULL

    UNION ALL

    -- Recursive member
    SELECT
        e.EmployeeId,
        e.EmployeeName,
        e.ManagerId,
        eh.Level + 1
    FROM Employees e
    INNER JOIN EmployeeHierarchy eh
        ON e.ManagerId = eh.EmployeeId
)
SELECT * FROM EmployeeHierarchy;
```

---

## 🧩 How This Works (Step-by-Step)

### 1️⃣ Anchor Query

```sql
WHERE ManagerId IS NULL
```

✔ Gets the **root node (CEO)**

### 2️⃣ Recursive Query

```sql
e.ManagerId = eh.EmployeeId
```

✔ Fetches **children of previous level**

### 3️⃣ UNION ALL

✔ Combines parent + child repeatedly

### 4️⃣ Level Column

✔ Shows **depth of hierarchy**

---

## 📊 Output Example

|EmployeeId|EmployeeName|ManagerId|Level|
|---|---|---|---|
|1|CEO|NULL|0|
|2|CTO|1|1|
|3|CFO|1|1|
|4|Engineering Manager|2|2|
|6|Accountant|3|2|
|5|Developer|4|3|

---

## 🔹 Retrieve Only Subtree (Example)

### Get all employees under CTO

```sql
WITH CTE AS (
    SELECT * FROM Employees WHERE EmployeeId = 2
    UNION ALL
    SELECT e.* FROM Employees e
    INNER JOIN CTE c ON e.ManagerId = c.EmployeeId
)
SELECT * FROM CTE;
```

---

## 🔹 Hierarchy with Indentation (Readable)

```sql
SELECT
    REPLICATE('---', Level) + EmployeeName AS HierarchyView
FROM EmployeeHierarchy;
```

Output:

```
CEO
---CTO
------Engineering Manager
---------Developer
---CFO
------Accountant
```

---

## ⚙️ Production Use-Cases

- Organization tree
    
- Category navigation
    
- Approval workflows
    
- Folder structures
    
- Permission inheritance
    

---

## 🎯 Interview-Ready Definition

**Hierarchical data** is data organized in a parent–child relationship where records form a tree structure. In SQL Server, hierarchical data is efficiently retrieved using **recursive Common Table Expressions (CTEs)**, which repeatedly join a table to itself until the full hierarchy is traversed.

---

## ⚠️ Key Interview Notes

- Recursive CTE = **BEST approach**
    
- Avoid cursors for hierarchies ❌
    
- Temp tables only when hierarchy reused multiple times
    
- Max recursion default = **100 levels** (`OPTION (MAXRECURSION n)`)
