#### Overview 
Data : - Raw unprocessed facts
Database : - Organized collection of data and it supports data storage and manipulation of data .
DBMS : - platform to manage the database
![[Pasted image 20250413185133.png|400|400]]
![[Pasted image 20250413185314.png|300|300]]
Types of DBMS : -
1. Flatfile DBMS
2. Hierarchial DBMS
3. Network DBMS
4. Relational DBMS
5. Non-relational DBMS

Relational DBMS (RDBMS) : -
 Here data's will be stored in Rows and Columns format or can be mentioned as data's are stored in Table format . 
 ![[Pasted image 20250413185523.png|500|500]]
 ![[Pasted image 20250413185645.png|400|400]]
 Here the data's will be stored in a predefined format . ![[Pasted image 20250413185736.png|400|400]]
 Example : - Here the insert operation can be performed only if the data is in correct format as the created table structure. 
 ![[Pasted image 20250413185845.png |400|400]]
 And follows an relationship between tables .
 ![[Pasted image 20250413185940.png]]
SQL : - DBMS is an interface between the users and the database and SQL acts as an native language for communication with the database . 
![[Pasted image 20250413190540.png |300|300]]
Types of SQL commands : -
	1. DDL
	2. DML
	3. DQL
	4. TCL
	5. DCL

DDL (Data Definition Language) : -
  The commands that defines the structure of Data Base objects are known as DDL commands . 
  CREATE - Creating and defining the columns that should be available in the database table . 
  ALTER - For changing the structure of the objects .
  TRUNCATE  -  For deleting the data in the table along with the space alloted to it, here table structure will be remained .
  DROP - To drop the database object completely along with its table structure.

   ![[Pasted image 20250413191644.png |900|]]
   DML (Data Manipulation Language) : - 
	   Commands used to manipulate the data in the database are known as DML.
	INSERT -  For inserting a new record into the database .
	UPDATE  - For modifying the data already present . 
	DELETE - For deleting the already present data .
	![[Pasted image 20250413192008.png | 400 |600]]
	DQL (Data Query Language) : -
		For retrieving the data present in the database . 
		SELECT - Used for retrieving the data present in the database . 
		![[Pasted image 20250413192136.png|400|300]]
TCL (Transaction Control Language) : -
	In some scenerio's we might want to execute five to six statements and all those statements should get executed successfully or incase if any one of those statement gets failed then all those five statements should get rollback and does not manipulate the data .
	COMMIT - If all the statements inside the transaction gets executed successfully then commit it .
	 ROLLBACK - If any of the statement gets failed then rollback for not affecting the data .
	 SAVE - Just a save point for transactions for partial rollbacks between transactions .
	 ![[Pasted image 20250413192712.png]]
	 DCL (Data Control Language) : -
		 Mostly used by administrators for providing and removing accesses .
		 GRANT - For providing database access .
		 REVOKE - For removing database access .![[Pasted image 20250413192855.png]]
Basic usage of common SQL commands : -
```
-- create database
CREATE DATABASE university;
-- use that database
USE university;

-- create table in that database
CREATE TABLE students(rollno INTEGER,name VARCHAR(300),
department VARCHAR(200),age INTEGER,date_of_birth DATE,gender CHAR(1));

SELECT * FROM students;

-- insert into table
INSERT INTO students VALUES(1,'student1','MCA',21,'2000-01-01','M');

-- insert another one column to the table structure
ALTER TABLE students ADD gpa FLOAT;

-- update the gpa column value in the above inserted table
UPDATE students SET gpa = 12.1 WHERE rollno=1;


ALTER TABLE students DROP COLUMN age;

-- Delete a record from the database 
DELETE FROM students WHERE rollno = 1;

-- truncate table
TRUNCATE TABLE students;

-- drop table , delete the structure
DROP TABLE students;

-- delete the database
DROP DATABASE university;
```	 	
Where clause usage with different operators : -
Operators used in where clause 
 = , <> , < , > , <= , >= , BETWEEN , IN , LIKE

```
#### Where Clause
```
SELECT TOP (1000) [AddressID]
      ,[AddressLine1]
      ,[AddressLine2]
      ,[City]
      ,[StateProvinceID]
      ,[PostalCode]
      ,[SpatialLocation]
      ,[rowguid]
      ,[ModifiedDate]
  FROM [AdventureWorks2019].[Person].[Address]



  SELECT TOP(10) * FROM Person.Address;

  -- WHERE CLAUSE

SELECT * FROM Production.Product WHERE ProductID = 322;
SELECT * FROM Production.Product WHERE ProductID >= 322;
SELECT * FROM Production.Product WHERE ProductID <= 322;


SELECT * FROM Production.Product WHERE ProductID >= 200 AND ProductID<=900;
SELECT * FROM Production.Product WHERE ProductID BETWEEN 300 AND 500;
SELECT * FROM Production.Product WHERE Color = 'Silver';
SELECT * FROM Production.Product WHERE Color <> 'Silver';
SELECT * FROM Production.Product WHERE Color IN ('Silver','Black','Red');
SELECT * FROM Production.Product WHERE Color NOT IN ('Silver','Black','Red');
SELECT * FROM Production.Product WHERE Color = 'Silver' AND StandardCost > 1000.00;
SELECT * FROM Production.Product WHERE Color = 'Silver' OR StandardCost > 1000.00;
SELECT * FROM Production.Product WHERE Size IS NULL;
SELECT * FROM Production.Product WHERE Size IS NOT NULL;
SELECT * FROM Production.Product WHERE SellStartDate = '2008-04-30';
SELECT * FROM Production.Product WHERE SellStartDate BETWEEN '2008-04-30' AND '2012-05-30';
```

#### Wildcards in sql 
When we don't exactly know the value but know particular portion like name start with HL

```
-- wildcards
SELECT * FROM Production.Product WHERE ProductNumber LIKE 'FC%';
SELECT * FROM Production.Product WHERE Name LIKE '%Cage';
SELECT * FROM Production.Product WHERE Name LIKE '%Frame';
SELECT * FROM Production.Product WHERE ProductNumber LIKE 'FR%R38%2';
SELECT * FROM Production.Product WHERE ProductNumber LIKE 'FR-R38B-_2';
SELECT * FROM Production.Product WHERE ProductNumber LIKE '_R%';
SELECT * FROM Person.Person WHERE FirstName LIKE 'A[ab]%';
SELECT * FROM Person.Address WHERE AddressLine1 LIKE '[a-z]%';
SELECT * FROM Person.Address WHERE AddressLine1 LIKE '[0-9]%';
SELECT * FROM Person.Address WHERE AddressLine1 LIKE '[a-z0-9]%';
SELECT * FROM Person.Address WHERE AddressLine1 LIKE '[a-z0-9#$]%';
SELECT * FROM Person.Address WHERE PostalCode LIKE '[0-9][0-9][0-9][0-9][0-9]';
SELECT * FROM Production.Product WHERE ProductNumber LIKE 'FR-R92%';
SELECT * FROM Production.Product WHERE ProductNumber LIKE 'FR-R92[^B]%';
SELECT * FROM Person.Address WHERE AddressLine1 LIKE '[^a-z0-9]%';
SELECT * FROM Person.Address WHERE AddressLine1 LIKE '%_%';
-- To display the address that contains _ in it's AddressLine1
SELECT * FROM Person.Address WHERE AddressLine1 LIKE '%[_]%';
```


#### Primary Key constraints
##### SQL constraints .
Applying rules for the data in the table is known as constraints .
![[Pasted image 20250420112826.png]]****
```
CREATE TABLE students (StudentID INTEGER PRIMARY KEY,FirstName VARCHAR(30),
LastName VARCHAR(20),DateOfBirth DATE,Gender CHAR(1));

-- OR

CREATE TABLE students (StudentID INTEGER,FirstName VARCHAR(30),
LastName VARCHAR(20),DateOfBirth DATE,Gender CHAR(1),CONSTRAINT Pk_students	PRIMARY KEY(StudentID));

-- Using ALTER statement it should be made an Non-nullable column

CREATE TABLE students (StudentID INTEGER NOT NULL,FirstName VARCHAR(30),
LastName VARCHAR(20),DateOfBirth DATE,Gender CHAR(1));

ALTER TABLE students ADD PRIMARY KEY(StudentID);
ALTER TABLE students ADD CONSTRAINT Pk_students PRIMARY KEY(StudentID);


ALTER TABLE students DROP CONSTRAINT Pk_students;
```
**Composite key - Making two or more columns as Primary key .

```
CREATE TABLE OrderDetail (OrderID INTEGER,ProductID INTEGER,
DateOfPurchase DATE,Price FLOAT CONSTRAINT pk_orderdetail PRIMARY KEY(OrderID,ProductID));

-- Using ALTER statement it should be made an Non-nullable column

CREATE TABLE OrderDetail (OrderID INTEGER NOT NULL,ProductID INTEGER NOT NULL,
DateOfPurchase DATE,Price FLOAT);

ALTER TABLE OrderDetail ADD CONSTRAINT pk_orderdetail PRIMARY KEY(OrderID,ProductID);
```
**NOT NULL Constraint . 

By default an table can have null values in it's fields , for restricting this ==NOT NULL constraint== can be used .

```
CREATE TABLE OrderDetail (OrderID INTEGER NOT NULL,ProductID INTEGER,
DateOfPurchase DATE,Price FLOAT);

-- Using ALTER statement for adding Not-null constraint

ALTER TABLE OrderDetail ALTER COLUMN ProductID INTEGER NOT NULL
```
**Unique Constraints .

![[Pasted image 20250422214911.png |400 |400]]
```
-- Unique constraint while creating a table
CREATE TABLE students (StudentID INTEGER,FirstName VARCHAR(30),
LastName VARCHAR(20),DateOfBirth DATE,Gender CHAR(1),AadharNumber BIGINT UNIQUE);

-- Unique constraint by adding constraint name
CREATE TABLE students (StudentID INTEGER,FirstName VARCHAR(30),
LastName VARCHAR(20),DateOfBirth DATE,Gender CHAR(1),AadharNumber BIGINT, 
CONSTRAINT Uc_students UNIQUE(StudentID));


-- Unique constraint for two or more columns  by adding constraint name
CREATE TABLE students (StudentID INTEGER,FirstName VARCHAR(30),
LastName VARCHAR(20),DateOfBirth DATE,Gender CHAR(1),AadharNumber BIGINT, 
CONSTRAINT Uc_students UNIQUE(StudentID,AadharNumber));

-- Unique constraint while altering a table
ALTER TABLE students ADD UNIQUE(AadharNumber);
ALTER TABLE students ADD CONSTRAINT Uc_students UNIQUE(AadharNumber);

-- Drop constraint
ALTER TABLE students DROP CONSTRAINT(Uc_students);
```
**Check Constraints
For applying restrictions for particular column in a table check constraints are used . 

```
CREATE TABLE employee(EmployeeID INTEGER PRIMARY KEY, FirstName VARCHAR(200),LastName VARCHAR(200),
DateOfBirth DATE,Gender CHAR(1),Salary INT CHECK(Salary>3000));

CREATE TABLE employee(EmployeeID INTEGER PRIMARY KEY,FirstName VARCHAR(200),LastName VARCHAR(200),
DateOfBirth DATE,Gender CHAR(1),Salary INT,CONSTRAINT CHK_EMPLOYEE CHECK(
Salary>3000 AND DateOfBirth >= '1980-01-01'));

-- Check constraint using alter statement
ALTER TABLE employee ADD CHECK(Salary>3000);
ALTER TABLE employee ADD CONSTRAINT CHK_Employee CHECK(Salary>3000 AND DateOfBirth>='1980-01-02');

-- Drop the check constraint
ALTER TABLE employee DROP CONSTRAINT CHK_Employee;
```
**Default constraint .

Assigns the default value to the column if no value is provided to that column during insertion of data .

```
CREATE TABLE NewStudents(StudentID INTEGER PRIMARY KEY,FirstName VARCHAR(100),
LastName VARCHAR(100),DateOfBirth DATE,Gender CHAR(1),Country VARCHAR(10) DEFAULT 'India');

INSERT INTO NewStudents(StudentID,FirstName,LastName,DateOfBirth,Gender)
VALUES(12,'FName','LName','12-02-24','M');

SELECT * FROM NewStudents;

-- Adding default constraint using alter statement

ALTER TABLE NewStudents ADD CONSTRAINT Df_students DEFAULT 'India' FOR Country;

-- Drop constraint
ALTER TABLE NewStudents DROP CONSTRAINT Df_students;
```

**Foreign Key Constraint .

Particular column of a table referring PK of another table is known as Foreign Key .
![[Pasted image 20250424223041.png]]
```
CREATE TABLE Course(
CourseID INTEGER PRIMARY KEY,
CourseName VARCHAR(100),
StaffName VARCHAR(100)
);

INSERT INTO Course(CourseID,CourseName,StaffName)VALUES(1,'Physics','Name');
INSERT INTO Course VALUES(2,'Maths','Name'),(3,'Computer','Name'),(4,'Tamil','Name');

--  Foreign Key
CREATE TABLE Students(StudentID INTEGER PRIMARY KEY,FirstName VARCHAR(100),LastName VARCHAR(100),
DateOfBirth DATE,Gender CHAR(1),CourseID INTEGER FOREIGN KEY REFERENCES Course(CourseID));

-- Or
CREATE TABLE Students(StudentID INTEGER PRIMARY KEY,FirstName VARCHAR(100),LastName VARCHAR(100),
DateOfBirth DATE,Gender CHAR(1),CourseID INTEGER,CONSTRAINT FK_Students FOREIGN KEY(CourseID)
REFERENCES
Course(CourseID));

INSERT INTO Students VALUES(1,'FName','LName','12-01-2024','M',3);

-- This will cause Foreign Key constraint error

INSERT INTO Students VALUES(1,'FName','LName','12-01-2024','M',53);
```
![[Pasted image 20250429220927.png|1000]]
```
DELETE FROM Course WHERE CourseID = 3;
```
![[Pasted image 20250429221224.png|900]]
```
-- Using alter statement to create constraint
ALTER TABLE Students ADD CONSTRAINT Fk_Students FOREIGN KEY (CourseID) REFERENCES Course(CourseID);

-- or
ALTER TABLE Students ADD FOREIGN KEY(CourseID)REFERENCES Course(CourseID);

-- Drop constraint
ALTER TABLE Students DROP CONSTRAINT Fk_Students;
```

**Aggregate Functions
![[Pasted image 20250501104753.png|580]]
![[Pasted image 20250501104831.png]]
***Aggregate Functions - ==Reads an set of values as Input and returns an single value as output.==

```
SELECT COUNT(ProductID) FROM Production.Product;
SELECT SUM(ListPrice) FROM Production.Product;
SELECT MIN(ListPrice) FROM Production.Product WHERE ListPrice > 0;
SELECT MAX(ListPrice) FROM Production.Product;
SELECT AVG(ListPrice) FROM Production.Product
```
**Using the Aggregate function with GroupBy clause .**
Group By is used for grouping a particular column having same value and performing operations based on that value .

```
SELECT Color,COUNT(Color) AS CountInNumbers FROM Production.Product GROUP BY Color;
SELECT Color,COUNT(Color) AS num_of_products FROM Production.Product WHERE Color IS NOT NULL GROUP BY Color;
SELECT Color,SUM(ListPrice) AS total_list_price FROM Production.Product WHERE Color IS NOT NULL GROUP BY Color;
SELECT Color,Size,AVG(ListPrice) AS avg_list_price FROM Production.Product WHERE Color IS NOT NULL GROUP BY Color,Size;
SELECT Color,Size,AVG(ListPrice) AS avg_list_price FROM Production.Product WHERE Color IS NOT NULL AND Size IS NOT NULL GROUP BY
Color,Size ORDER BY Color,Size;
SELECT Color,COUNT(ProductID) AS num_of_products FROM Production.Product GROUP BY Color;
SELECT Color,SUM(ListPrice) AS total_list_price FROM Production.Product WHERE Color IS NOT NULL GROUP BY Color; 
SELECT Color,Size,AVG(ListPrice) AS avg_list_price FROM Production.Product WHERE Color IS NOT NULL GROUP BY Color,Size;
SELECT Color,Size,AVG(ListPrice) AS avg_list_price FROM Production.Product WHERE Color IS NOT NULL AND Size IS NOT NULL 
   GROUP BY Color,Size ORDER BY Color,Size;
   ```
**Having With GroupBy**
Where clause is used for normally applying condition to the table and Having clause is used for applying conditions on an Aggregate functions. Having clause is always used along with Group By clause.

```
   -- Having clause
SELECT Color,COUNT(ProductID) AS num_of_products FROM Production.Product WHERE Color IS NOT NULL GROUP BY Color
	HAVING COUNT(ProductID)>10;

SELECT Color,COUNT(ProductID) AS num_of_products FROM Production.Product WHERE Color IS NOT NULL 
GROUP BY Color HAVING SUM(ListPrice)>300;

SELECT Color AS distinct_color FROM Production.Product WHERE Color IS NOT NULL GROUP BY Color;
SELECT Color,Size FROM Production.Product WHERE Color IS NOT NULL AND Size IS NOT NULL GROUP BY
	Color,Size ORDER BY Color,Size;
SELECT DISTINCT Color FROM Production.Product;
SELECT DISTINCT Color,Size FROM Production.Product WHERE Color IS NOT NULL AND Size IS NOT NULL ORDER BY Color,Size;
```

**Joins in SQL**
 Joining rows between two tables by using the related columns in those two tables.
![[Pasted image 20250502231010.png]]	
![[Pasted image 20250503223644.png]]
![[Pasted image 20250503223752.png|350]]
![[Pasted image 20250503223830.png|360]]
**Inner Join**
Used to retrieve the records that are common in both the left and the right table .
![[Pasted image 20250503224023.png]]
So the records related to DepartmentID's 11,12,13,14 will be retrieved and displayed.

```
CREATE TABLE Employee(EmployeeID INTEGER PRIMARY KEY,FirstName VARCHAR(100),LastName VARCHAR(100),DateOfBirth DATE,
Gender CHAR(1),DepartmentID INTEGER);

INSERT INTO Employee VALUES(1001,'Aishwarya','Jayaram','2005-05-24','F',11),
(1002,'Anand','Venkat','2005-05-22','M',22),
(1003,'Bala','Sundaram','2004-11-02','M',22),
(1004,'Deepa','Mani','2004-12-09','F',22),
(1005,'Deepa','Mahesh','2005-05-29','F',22),
(1006,'Gokul','Ram','2004-11-27','M',22),
(1007,'Shreya','Gopi','2005-06-20','F',22),
(1008,'Abdul','Rahman','2005-07-30','M',22);

SELECT * FROM Employee;


CREATE TABLE Department(DepartmentID INTEGER,DepartmentName VARCHAR(100));
INSERT INTO Department VALUES(11,'Engineering'),
(12,'Finance'),(13,'Sales'),(14,'Marketing');

SELECT * FROM Department;


SELECT * FROM Employee INNER JOIN Department ON Employee.DepartmentID = Department.DepartmentID;
-- or
SELECT * FROM Employee e INNER JOIN Department d ON e.DepartmentID = d.DepartmentID;

SELECT e.FirstName,e.LastName,d.DepartmentName FROM Employee e  INNER JOIN Department d on e.DepartmentID = d.DepartmentID;
```

**Outer Join**
**Left outer Join** : - 
	Here the table in the ==left side takes advantage as it takes the non-matching records from the table in the  left side along with the matching records from the table in the right side==.
```
SELECT * FROM Department d LEFT JOIN Employee e ON d.DepartmentID = e.DepartmentID;
```
![[Pasted image 20250503230133.png]]
**Right outer Join** : - 
	Here the table in the ==right side takes advantage as it takes the non-matching records from the table in the right side along with the matching records from the table in the left side==.
```
SELECT * FROM Department d RIGHT JOIN Employee e ON d.DepartmentID = e.DepartmentID;
```
![[Pasted image 20250503231853.png]]
**Full outer Join** : - 
	Here the matching records from both the tables will get displayed along with the non-matching records from the left table and the non-matching records from the right table  .
```
SELECT * FROM Department d FULL JOIN Employee e ON d.DepartmentID = e.DepartmentID;

```
![[Pasted image 20250503232334.png|590]]

**Self Join**
![[Pasted image 20250503232516.png|150]]
To Join a table with itself self join is used.

![[Pasted image 20250503232644.png|500]]
Here Employees are managed by Managers denotes by ManagerID , where they themselves are Employees at the end. 1001 employee is managed by 1002 where he himself is an employee and is managed by 1003.

Here self join can be used to find the manager name of each employees .
![[Pasted image 20250503232918.png]]
```
ALTER TABLE Employee ADD ManagerID INTEGER;

SELECT e1.EmployeeID,e1.FirstName,e1.LastName,e1.ManagerID,e2.FirstName+' '+e2.LastName AS ManagerName
	FROM Employee e1 JOIN Employee e2 ON e1.EmployeeID = e2.ManagerID;

```
![[Pasted image 20250503234227.png]]
```
SELECT e1.EmployeeID,e1.FirstName,e1.LastName,e1.ManagerID,e2.FirstName+' '+e2.LastName AS ManagerName FROM employee e1
	LEFT JOIN Employee e2 ON e1.EmployeeID = e2.ManagerID;
```
**Cross Join**
![[Pasted image 20250504081418.png|450]]
When we want to Join all the records from Table A with all the records in Table B Cross Join can be used.
![[Pasted image 20250504081703.png]]
```
 SELECT e1.FirstName+' '+e1.LastName AS Employee_1,e2.FirstName+' '+e2.LastName AS Employee_2 FROM employee e1
	CROSS JOIN Employee e2;
```
Cross Join doesn't need any ON condition as all the records from Table A will be Joined with all the records from Table B.

> Cross Join is also known as Cartesian product. As the result will be the product of the number of records in each tables and no-filter is used while selecting the data's (8 x 8  =64, 5 x 6 =30) .

```
SELECT e1.FirstName+' '+e1.LastName AS Employee_1,e2.FirstName+' '+e2.LastName AS Employee_2 FROM employee e1
	CROSS JOIN Employee e2 WHERE e1.EmployeeID <> e2.EmployeeID;
```
**Views**
![[Pasted image 20250504162755.png|560]]
![[Pasted image 20250504165248.png]]
We use Joins for associating the Department with Employee, so this process can be implemented by creating it as an view and that view can be executed whenever needed . Views are used for hiding the PIA details and executing the query as simple as possible.

```
SELECT e.EmployeeID,e.FirstName,e.LastName,e.DepartmentID,d.DepartmentName
 FROM  Employee e JOIN Department d ON e.DepartmentID = d.DepartmentID;

 -- Creating View
CREATE VIEW employee_dept_details AS 
 SELECT e.EmployeeID,e.FirstName,e.LastName,e.DepartmentID,d.DepartmentName
 FROM  Employee e JOIN Department d ON e.DepartmentID = d.DepartmentID;

-- Executing View

SELECT * FROM employee_dept_details;


CREATE VIEW employee_details AS
	SELECT * FROM Employee;

SELECT * FROM employee_details;
```
> Views are also known as virtual tables as views doesn't take physical memory .

![[Pasted image 20250504171324.png]]
**altering a view definition**
```
ALTER VIEW employee_details AS SELECT * FROM Employee WHERE EmployeeID <> 1001;
```
==If the view definition points to an particular row we can even perform insert operation also. Cannot be used if the view definition contains multiple tables and perform JOINS in it and if the table retrieves DISTINCT values or Aggregates or Group By clause, or Pivot or Unpivot operator.==

```
INSERT INTO employee_details VALUES(1009,'Suresh','Babu','2000-03-09','M',12,NULL);
```
Similarly we can also perform other operations like update and delete as well
```
UPDATE employee_details SET FirstName = 'Stark',LastName = 'Tony' WHERE EmployeeID = 1009;

DELETE FROM employee_details WHERE EmployeeID = 1009;
```
**Delete the view**
```
DROP VIEW employee_details;
```
**Creating user access**
```
CREATE LOGIN test_login WITH PASSWORD = 'test1234';
CREATE USER test_user FOR LOGIN test_login;

-- Grant permission to access this view
GRANT SELECT ON employee_details TO test_user;
```
Here the user entered by using this login will have access to open the employee_details view only.

**SubQueries**

```
-- Select all the sales territory where rowguid = '52A5179D-3239-4157-AE29-17E868296DC0'
SELECT * FROM Sales.SalesPerson WHERE rowguid = '52A5179D-3239-4157-AE29-17E868296DC0';
SELECT * FROM Sales.SalesTerritory WHERE TerritoryID = 5;

SELECT * FROM Sales.SalesTerritory WHERE TerritoryID = (
	SELECT TerritoryID FROM Sales.SalesPerson WHERE rowguid = '52A5179D-3239-4157-AE29-17E868296DC0'
);

SELECT * FROM Sales.SalesTerritory WHERE TerritoryID IN (
	SELECT TerritoryID FROM Sales.SalesPerson WHERE CommissionPct = '0.01'
);

SELECT * FROM Employees WHERE departmentID IN (
	SELECT departmentID FROM departments WHERE LocationID IN 
	  (SELECT LocationID FROM Locations WHERE LocationName='TORONTO'));

-- create a new table called as employee toronto and insert all the employees from Toronto
SELECT * INTO employees_toronto FROM Employees WHERE 1=0; -- creates a table structure similar to Employees into employees_toronto

INSERT INTO employees_toronto SELECT * FROM employees WHERE Department_ID IN (
	SELECT Department_ID FROM departments WHERE Location_ID IN(
	SELECT Location_ID FROM Locations WHERE City='Toronto'
));

-- Update salary of all employees whose salary is less than the average salary to average salary

UPDATE Employees SET salary = ( SELECT AVG(salary) FROM Employees )
WHERE salary < ( SELECT AVG(salary) FROM Employees );

-- DELETE All employees whose department is either 'Administration' or 'Marketing'
DELETE FROM Employees WHERE Department_ID IN(
	SELECT Department_ID FROM Departments WHERE DepartmentName IN(
	'Administration','Marketing'));
```
**Correlated subquery**

SubQueries cannot be executed separately here. Inner Query depends on the Outer Query for it's execution .
```
-- List all employees whose salary is less than the avg salary in that department
SELECT * FROM Employees 
E1 WHERE Salary < (SELECT AVG(Salary) FROM Employees E2 WHERE E2.Department_ID = E1.Department_ID);
```
**Exists / Not Exists**
![[Pasted image 20250506222856.png]]
```
SELECT * FROM Salesman s WHERE EXISTS (
	SELECT 1 FROM orders o WHERE s.salesman_id = o.salesman_id
);


SELECT * FROM Salesman s WHERE NOT EXISTS(
	SELECT 1 FROM orders o WHERE s.salesman_id = o.salesman_id
);
```
**Any/All**
![[Pasted image 20250506224210.png]]
Any operator is used for comparing a particular column of an record with a list of values .

```
/*
	List all employees whose salary is greater than the avg salary of any of the Departments
*/

SELECT * FROM employees WHERE Salary > ANY(
	SELECT avg_salary FROM ( 
	 SELECT department_id, AVG(salary) AS avg_salary FROM employees GROUP BY department_id) AS temp
);

```
![[Pasted image 20250506230015.png]]
All is also similar to Any but all the values should get satisfied.
```
/*
List of all employees whose salary is less than the salary of all the employees working for 
DepartmentId 30
*/

SELECT * FROM employees WHERE salary < ALL (
SELECT salary FROM employees WHERE department_id = 30);
```
**CTE**
![[Pasted image 20250506231050.png]]
CTE is known as ==Temporary named Result set .==

```
-- Complex Query with subquery in it
SELECT PI.ProductID,Total_Quantity,PV.StandardPrice,PV.BusinessEntityID FROM
(SELECT ProductID,SUM(Quantity) AS Total_Quantity FROM Production.ProductInventory
GROUP BY ProductID HAVING SUM(Quantity)<100 ) PI JOIN Purchasing.ProductVendor 
PV ON PI.ProductID = PV.ProductID;

-- This can be split into CTE for easy understanding
WITH low_quantity_product AS 
(SELECT ProductID,SUM(Quantity) AS Total_Quantity FROM Production.ProductInventory
GROUP BY ProductID HAVING SUM(Quantity)<100)

SELECT QP.ProductID,Total_Quantity,PV.StandardPrice,PV.BusinessEntityID FROM low_quantity_product
QP JOIN Purchasing.ProductVendor PV ON QP.ProductID = PV.ProductID;
```

CTE is used for breaking complex queries into smaller simpler one's for better readability and understanding .

**Window functions .**
![[Pasted image 20250507232415.png]]
A **window function** in MySQL performs a **calculation across a set of table rows** that are somehow related to the current row. Unlike aggregate functions, which return a single result for a group, **window functions return a value for each row** while retaining the individual row details.

```
SELECT *,SUM(Salary) OVER() AS TOTAL_SALARY FROM employees;

```

![[Pasted image 20250507233120.png]]
Consider a scenario where we want to display the total salary of each department based on the department ID

```
-- Performing Aggregation based on particular column
SELECT *,SUM(Salary) OVER(PARTITION BY department_id) AS TOTAL_SALARY FROM employees;
```
![[Pasted image 20250507233528.png]]
```
-- Performing Aggregation based on particular column as running total
SELECT *,SUM(Salary) OVER(PARTITION BY department_id ORDER BY employee_id) 
AS TOTAL_SALARY FROM employees;

```
![[Pasted image 20250507234132.png]]
![[Pasted image 20250507234411.png]]
**Value window functions**
1. FIRST_VALUE
2. LAST_VALUE
3. LAG
4. LEAD 

**First Value** : - This window function is used to check the initial value when it was created.
```
SELECT ProductID,StandardCost,ModifiedDate FROM Production.ProductCostHistory
ORDER BY ProductID,ModifiedDate; --This displays the product details with its order according to
-- its Date of modification.

```
![[Pasted image 20250510105020.png]]
```
-- First value
SELECT ProductID,StandardCost,ModifiedDate,FIRST_VALUE(StandardCost) OVER(PARTITION BY ProductID
ORDER BY ModifiedDate) AS Initial_value FROM Production.ProductCostHistory
ORDER BY ProductID,ModifiedDate;
```
![[Pasted image 20250510105452.png]]
**Last Value** : - This window function is used to check the final value of the field.
```
SELECT ProductID,StandardCost,ModifiedDate,FIRST_VALUE(StandardCost)OVER(PARTITION BY ProductID
ORDER BY ModifiedDate)AS Initital_value, LAST_VALUE(StandardCost)OVER(PARTITION BY ProductID 
ORDER BY ModifiedDate) AS Final_value FROM Production.ProductCostHistory 
ORDER BY ProductID,ModifiedDate;
```
![[Pasted image 20250510110501.png]]
This is displaying final value for each ProductID based on its previous entries data. This is not the expected result so the ==LAST_VALUE() should be used along with Frame window (RANGE BETWEEN UNBOUNDED PRECEDING AND UNBOUNDED FOLLOWING)==
```
-- Last Value
SELECT ProductID,StandardCost,ModifiedDate,FIRST_VALUE(StandardCost)OVER(PARTITION BY ProductID
ORDER BY ModifiedDate)AS Initital_value, LAST_VALUE(StandardCost)OVER(PARTITION BY ProductID 
ORDER BY ModifiedDate RANGE BETWEEN UNBOUNDED PRECEDING AND UNBOUNDED FOLLOWING) AS Final_value
FROM Production.ProductCostHistory 
ORDER BY ProductID,ModifiedDate;
```
![[Pasted image 20250510111517.png]]

**LAG** : - 