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
The `LAG()` function is a **window function** that allows you to **look back at a previous row's value** within the result set  **without using a self-join**.

**LEAD** : -
The `LEAD()` function lets you **look forward** to a **next row’s value** within the result set similar to how `LAG()` looks backward.

```
-- LEAD AND LAG
SELECT ProductID,StandardCost,ModifiedDate,LAG(StandardCost)OVER(PARTITION BY ProductID
ORDER BY ModifiedDate)AS Previous_value,LEAD(StandardCost)OVER(PARTITION BY ProductID
ORDER BY ModifiedDate)AS Next_value FROM Production.ProductCostHistory ORDER BY ProductID,ModifiedDate;
```
![[Pasted image 20250510112429.png]]
LEAD() LAG() By default sees one value before the current value and after the current value but can be made to see custom values before and after and to show custom results instead of NULL if no value is present .
LAG(StandardCost,2,0) sees and displays two values before the current value and displays 0.00 instead of NULL and the same can be applied for LEAD() as well.
![[Pasted image 20250510112943.png]]
![[Pasted image 20250510113039.png]]
ROW_NUMBER : -
	The ROW_NUMBER() window function assigns a unique sequential integer to each row within a partition of a result set, starting from 1. It’s useful for ranking, pagination, or identifying row positions.
```
SELECT ProductID,StandardCost,ModifiedDate,ROW_NUMBER()
OVER(PARTITION BY ProductID ORDER BY ModifiedDate) AS Rno
FROM Production.ProductCostHistory;

```
![[Pasted image 20250510130728.png]]
```
WITH Latest_data AS (
SELECT ProductID,StandardCost,ModifiedDate,ROW_NUMBER()
OVER(PARTITION BY ProductID ORDER BY ModifiedDate DESC) AS Rno
FROM Production.ProductCostHistory
)
SELECT * FROM Latest_data WHERE Rno =1;

```
![[Pasted image 20250510131130.png]]
ROW_NUMBER() is mostly used for removing duplicate data and retrieving the latest record.

**Rank** : -
	The RANK() window function assigns a rank to each row within a partition of a result set, based on the order specified in the ORDER BY clause. Rows with equal values for the ordering criteria receive the same rank, but the function leaves gaps in the ranking sequence for duplicate values (unlike DENSE_RANK()).

```
SELECT *,RANK()OVER(PARTITION BY DEPARTMENT_ID ORDER BY SALARY DESC) AS RANK FROM EmployeesManager;
```
![[Pasted image 20250510132904.png]]

> Here if there is an duplicate in Rank , like there are 2 employees having same rank 11 , then the next employee will have rank 13 , if three employees having rank 11 then the next will have 14.

==And In-order to avoid the above mentioned process and allot consecutive numbers DENSE_RANK can be used==

**DENSE RANK** : -
```
-- Dense rank
SELECT *, DENSE_RANK()OVER(PARTITION BY DEPARTMENT_ID ORDER BY SALARY DESC) 
AS DENSE_RANK FROM EmployeesManager;
```
![[Pasted image 20250510133522.png]]

**NTILE** : -
	NTILE window function divides an ordered result set into a specified number of approximately equal buckets (or tiles) and assigns each row a bucket number from 1 to the number of buckets. It’s useful for tasks like ranking data into quartiles, deciles, or other quantiles.
	
```
SELECT *, NTILE(10)OVER(ORDER BY SALARY DESC) AS GroupBucket FROM EmployeesManager;
```
![[Pasted image 20250510134117.png]]

PARTITION BY can be replaced using WINDOW()

```
SELECT *, DENSE_RANK()OVER win 
AS DENSE_RANK FROM EmployeesManager WINDOW win AS(PARTITION BY DEPARTMENT_ID ORDER BY SALARY DESC);
```
**Temp Table** : - Used for temporarily storing the data without creating a table using physical memory .
Temporary tables can be classified into two types
1. Local temporary table and
2. Global temporary table. 
![[Pasted image 20250510135239.png]]
Temp table can be created using any of the following two ways
```
-- Temporary table will be created
SELECT * INTO #tmp_person FROM Production.Product;

SELECT * FROM #tmp_person

-- Or
CREATE TABLE #tmp_person_id(
	ProductID INTEGER
);

INSERT INTO #tmp_person_id SELECT ProductID FROM Production.Product WHERE ProductModelID = 23;


SELECT * FROM #tmp_person_id;

```
![[Pasted image 20250510161841.png]]
==Local temporary tables are accessible only at that particular session and  are automatically dropped (deleted/disposed) at the end of the session . Or can be deleted explicitly using the DROP table query. ==

> Global temporary tables are created using ## instead of # before it's name and are accessible from other sessions as well.

```
-- creates Global temp table.
SELECT * INTO ##tmp_person_global FROM Production.Product;

SELECT * FROM ##tmp_person_global;
```
![[Pasted image 20250510162959.png]]

**Store Procedure**

> Store procedure is known as ==Pre-compiled code== as it will get compiled and stored in executable form. So it will not get compiled during every execution thus making it perform better. 


![[Pasted image 20250510163113.png]]

```
-- Store procedure without parameters
CREATE PROCEDURE GetEmployeeData
AS BEGIN
SELECT * FROM Person.Person
END


EXEC GetEmployeeData;

-- with parameter

CREATE PROCEDURE GetEmployeeDataByDeptID @personID INT
AS BEGIN
SELECT * FROM Person.Person WHERE BusinessEntityID=@personID
END

EXEC GetEmployeeDataByDeptID 10; -- Input parameter
-- or
EXEC GetEmployeeDataByDeptID @personID=10;

-- default parameter
ALTER PROCEDURE GetEmployeeDataByDeptID @personID INT =10
AS BEGIN
SELECT * FROM Person.Person WHERE BusinessEntityID=@personID
END
```

**Output parameter for Store Procedure**

```
-- output parameter
ALTER PROCEDURE GetEmployeeDataByDeptID @personID INT =10, @personCount INT OUT
AS
BEGIN
SELECT @personCount = COUNT(*) FROM Person.Person WHERE BusinessEntityID = @personID
END

DECLARE @count INT
EXEC GetEmployeeDataByDeptID 20,@count OUT
SELECT @count;
```
![[Pasted image 20250510165444.png]]

**Index**
	An **index** in MySQL is a database structure that improves the speed of data retrieval operations on a table by providing a quick lookup mechanism. It works like an index in a book, allowing the database to find rows faster without scanning the entire table. However, indexes come with trade-offs: they speed up SELECT queries but can slow down INSERT, UPDATE, and DELETE operations because the index must be updated.
	
### Clustered Index

- **Definition**: A clustered index determines the **physical order** of data rows in the table. The table's data is stored in the same order as the index, meaning the data is physically sorted based on the indexed column(s).
- **Key Points**:
    - There can be **only one clustered index** per table because the data can only be physically arranged in one order.
    - In MySQL, the **primary key** is typically the clustered index (e.g., in InnoDB). If no primary key exists, the first unique index with non-null columns may be used, or InnoDB creates an internal clustered index.
    - **Benefit**: Fast retrieval for range queries, searches, or joins on the indexed column since the data is already sorted.
    - **Example**: In a users table with a primary key on id, the rows are physically stored in
### Non-Clustered Index

- **Definition**: A non-clustered index is a separate structure that stores a copy of the indexed column(s) along with **pointers** (references) to the actual data rows in the table. The table's data remains in its original order (or clustered index order), and the non-clustered index acts like a lookup table.
- **Key Points**:
    - A table can have **multiple non-clustered indexes** because they don't affect the physical data order.
    - In MySQL, indexes like INDEX, UNIQUE, or FULLTEXT (on non-primary key columns) are non-clustered.
    - **Benefit**: Speeds up queries on columns not part of the clustered index, but slightly slower than a clustered index because it requires an extra step to follow the pointer.
    - **Example**: An index on the city column in the users table stores city values and pointers to the corresponding rows.

    > By default the database creates a ==clustered index on Primary Key and non-clustered index on Unique key constraint .== 

```
CREATE TABLE EmployeeIndex(
	EmployeeID INTEGER PRIMARY KEY,
	FirstName VARCHAR(200),
	LastName VARCHAR(200) UNIQUE,
	DateOfBirth DATE,
	Gender CHAR(1),
	DepartmentID INTEGER);
```
![[Pasted image 20250511180949.png]]
Explicitly non-clustered index can be created using the following
```
SELECT * INTO EmployeeIndexNonClusteredIndex FROM EmployeeIndex;

CREATE INDEX idx_lastName ON EmployeeIndexNonClusteredIndex(LastName);
```
![[Pasted image 20250511181551.png]]
Non clustered unique index can be created using 
```
CREATE UNIQUE INDEX idx_firstName ON EmployeeIndexNonClusteredIndex(FirstName);
```
![[Pasted image 20250511181726.png]]
Clustered index can be created using
```
CREATE CLUSTERED INDEX idx_clstr_lastName ON EmployeeIndexNonClusteredIndex(LastName);
```
![[Pasted image 20250511182316.png]]
> A table can have ==only one clustered index== in it, and if the ==Primary key is created after creating clustered index it will be created as an non clustered index ==.

```
ALTER TABLE EmployeeIndexNonClusteredIndex ADD CONSTRAINT
pk_const PRIMARY KEY(EmployeeID);
```
![[Pasted image 20250511182805.png]]
Dropping Index
```
DROP INDEX EmployeeIndexNonClusteredIndex.idx_clstr_lastName;
-- Drop index tableName.IndexName
```
Multiple index
```
CREATE INDEX multiple_index ON EmployeeIndexNonClusteredIndex(FirstName,LastName);
```
![[Pasted image 20250511183700.png]]
Now this will arrange the values in alphabetical order according to their first name then by their last name in that arranged result.

F_Nm L_Nm
![[Pasted image 20250511183758.png]]
And this kind of index are useful for the following queries
```
SELECT * FROM EmployeeIndexNonClusteredIndex WHERE FirstName = 'aaa' AND LastName = 'bbb';
```
**Trigger**
	A special type of Store Procedure that automatically runs when an event occurs in the database server .
	A **trigger** is a database object associated with a table that automatically executes a predefined set of SQL statements when certain events (CRUD operations) occur on that table.
	Trigger contains an set of SQL statements in it . 
![[Pasted image 20250511184531.png]]
- Automatically update the last_updated column whenever a user’s first_name or city is updated.
![[Pasted image 20250511213344.png]]
Triggers will generate two virtual tables.
![[Pasted image 20250511213531.png]]
```
-- Creating table to make an entry after insert operation in Employee Table.

CREATE TABLE employees_audit(
	Employee_ID INTEGER,
	Operation VARCHAR(100),
	UpdatedDate DATETIME
);

-- Creating trigger
CREATE TRIGGER trg_emp_audit
ON Employee
AFTER INSERT AS BEGIN 
INSERT INTO employees_audit
SELECT EmployeeID,'INSERT',GETDATE() FROM inserted
END;

SELECT * FROM Employee;
INSERT INTO Employee VALUES(3000,'Trigger','Check','2025-05-11','M',11,1002);

SELECT * FROM employees_audit;
```
![[Pasted image 20250511214648.png]]
Altering a trigger
```
-- Alter trigger
ALTER TRIGGER trg_emp_audit ON Employee
AFTER INSERT,DELETE AS
BEGIN
	INSERT INTO employees_audit 
	SELECT EmployeeID,'Insert',GETDATE() FROM inserted
UNION ALL
	SELECT EmployeeID,'Deleted',GETDATE() FROM deleted
END

DELETE FROM Employee WHERE EmployeeID = 1002;
```
![[Pasted image 20250511215549.png]]
 ```
 SELECT * INTO employees_copy FROM Employee;
ALTER TABLE employees_copy ADD active BIT,EndDate DATETIME;
SELECT * FROM employees_copy;

CREATE TRIGGER trg_emp_delete
ON employees_copy 
INSTEAD OF DELETE AS
BEGIN
	update employees_copy SET active = 0,EndDate=GETDATE() WHERE EmployeeID IN(
		SELECT EmployeeID FROM deleted
	)
END

SELECT * FROM employees_copy;
DELETE FROM employees_copy WHERE EmployeeID = 1003;
```
![[Pasted image 20250511220753.png]]
![[Pasted image 20250511220835.png]]
**Functions in SQL**
![[Pasted image 20250511223202.png]]
Set of SQL statements that does an action and returns an output value based on the Input parameters provided.

> Functions may or may not have an Input parameter but should definitely return a value .

Functions can be classified into
1. System functions (Build in functions)
	![[Pasted image 20250511223418.png|250]]
2. Custom functions (User defined functions)
		![[Pasted image 20250511223521.png|350]]
-Scalar functions - If the retuned value of a function is an single row value then such functions are known as Scalar functions .

```
CREATE FUNCTION
	udf_add_numbers(@a INT,@b INT)
	RETURNS INT
	BEGIN
		RETURN @a + @b
	END

SELECT dbo.udf_add_numbers(2,10) AS Result;	
```
![[Pasted image 20250511224409.png]]
![[Pasted image 20250511224457.png]]
```
CREATE FUNCTION
	dbo.udf_PassOrFail(@marks INT)
	RETURNS CHAR(1) AS
	BEGIN
		DECLARE @grade CHAR(1)
		IF (@marks>=35)
			SET @grade = 'P'
        ELSE
			SET @grade = 'F'	
	RETURN @grade
	END

SELECT StudentID,Name,
dbo.udf_PassOrFail(Tamil) AS Tamil,
dbo.udf_PassOrFail(Physics) AS Physics,
dbo.udf_PassOrFail(Chemistry) AS Chemistry,
dbo.udf_PassOrFail(English) AS English,
dbo.udf_PassOrFail(Biology) AS Biology,
dbo.udf_PassOrFail(Maths) AS Maths FROM StudentMarks;
```
![[Pasted image 20250513080819.png]]
> scalar value functions can be used as how columns are used in a table .
```
SELECT * FROM studentMarks WHERE dbo.udf_PassOrFail(Biology) ='P';
```
**Table valued functions** - Unlike scalar functions table valued function does not return a single value , instead it returns the table itself.

> Table valued functions are also known as ==Parameterized views== .

Table valued functions are classified into two types
1. Inline table valued functions and
2. Multi-valued table valued functions .

```
-- Inline table valued functions

CREATE FUNCTION dbo.udf_EmpByDept(@deptID INT)
RETURNS TABLE
AS
RETURN SELECT * FROM Employee WHERE EmployeeID = @deptID


SELECT * FROM dbo.udf_EmpByDept(1003);

-- Multi valued table functions
CREATE FUNCTION dbo.udf_Persons()
RETURNS	@personData TABLE(ID INT,PersonName VARCHAR(100))
AS 
BEGIN
INSERT INTO @personData
SELECT EmployeeID,FirstName FROM Employee
INSERT INTO @personData
SELECT StudentID, FirstName FROM NewStudents
RETURN 
END


SELECT * FROM dbo.udf_Persons()
```
![[Pasted image 20250513213953.png]]
![[Pasted image 20250513214002.png]]
![[Pasted image 20250513214017.png]]
![[Pasted image 20250513214033.png]]
![[Pasted image 20250513214046.png]]
![[Pasted image 20250513214103.png]]
![[Pasted image 20250513214122.png]]

**Cursor** : -
![[Pasted image 20250513214223.png|360]]
==This scenario can be considered with set operations==
![[Pasted image 20250513214330.png]]
This can be considered as ==Cursor==
![[Pasted image 20250513214404.png]]
![[Pasted image 20250513214412.png]]
```
DECLARE @id INT
DECLARE @value INT
DECLARE @runningTotal INT = 0
DECLARE RunningTotalCursor CURSOR FOR
SELECT ID,Value FROM SalesData ORDER BY ID

OPEN RunningTotalCursor
FETCH NEXT FROM RunningTotalCursor INTO @id,@value
WHILE @@FETCH_STATUS = 0 
BEGIN 
	SET @runningTotal = @runningTotal + @value
	UPDATE SalesData SET RunningTotal = @runningTotal WHERE ID = @id
	FETCH NEXT FROM RunningTotalCursor INTO @id,@value
END
CLOSE RunningTotalCursor
DEALLOCATE RunningTotalCursor
```   
![[Pasted image 20250513220434.png]]
![[Pasted image 20250513221356.png|400]]
![[Pasted image 20250513221440.png|300]]

**Transactions** : -
![[Pasted image 20250513224732.png|600]]
![[Pasted image 20250513224846.png|500]]
```
BEGIN TRANSACTION
DELETE FROM employees WHERE employee_id = 101

-- The transaction will be reverted now.
ROLLBACK TRANSACTION
SELECT * FROM employees WHERE employee_id = 101

-- commit transaction to make changes permanent
BEGIN TRANSACTION
UPDATE employees SET department_id = 1 WHERE employee_id = 103
COMMIT TRANSACTION


SELECT * FROM employees WHERE employee_id = 103
ROLLBACK TRANSACTION
```
![[Pasted image 20250513225512.png]]
```
BEGIN TRANSACTION
UPDATE BankAccount SET Balance = Balance - 1000 WHERE AccountNumber = 3456789012;
UPDATE BankAccount SET Balance = Balance + 1000 WHERE AccountNumber = 1122334455;

IF @@ERROR<>0
	ROLLBACK TRANSACTION
ELSE
	COMMIT TRANSACTION
```
**Save Transaction** - You want to save transactions using MySQL’s transaction control to ensure data integrity (e.g., if a transaction fails, it rolls back).
![[Pasted image 20250513231404.png]]
```
BEGIN TRANSACTION
INSERT INTO BankAccount (AccountID, AccountNumber, Balance) VALUES
(4, 3456789014, 18000.60);
SAVE TRANSACTION First_Insert
INSERT INTO BankAccount (AccountID, AccountNumber, Balance) VALUES
(5, 3756789014, 19000);

SELECT (1/0)
IF @@ERROR <> 0
	ROLLBACK TRANSACTION First_Insert
ELSE
	COMMIT TRANSACTION
```
![[Pasted image 20250513231505.png]]
![[Pasted image 20250513231515.png]]
![[Pasted image 20250513231840.png|350]]
![[Pasted image 20250513231948.png|440]]
**Merge** : - 
![[Pasted image 20250513232034.png|450]]

![[Pasted image 20250513232134.png|350]]
![[Pasted image 20250513232152.png]]
![[Pasted image 20250513232231.png]]
The value needs to be updated in the target table .
![[Pasted image 20250513232253.png]]
These values needs to be inserted in the target table .
![[Pasted image 20250513232357.png]]
These values needs to be deleted from the target table .

> MERGE statement should always be terminated by a semicolon. 

```
MERGE EmployeeTarget AS T
USING EmployeeSource AS S
ON T.Employee_ID = S.Employee_ID -- all PK's should be used here using AND statement

WHEN MATCHED THEN
UPDATE SET
T.FIRST_NAME = S.FIRST_NAME,
T.LAST_NAME = S.LAST_NAME,
T.SALARY = S.SALARY,
T.MANAGER_ID = S.MANAGER_ID,
T.DEPARTMENT_ID = S.DEPARTMENT_ID

WHEN NOT MATCHED BY TARGET THEN 
INSERT(Employee_ID,FIRST_NAME,LAST_NAME,SALARY,MANAGER_ID,DEPARTMENT_ID)
VALUES(S.Employee_ID,S.FIRST_NAME,S.LAST_NAME,S.SALARY,S.MANAGER_ID,S.DEPARTMENT_ID)

WHEN NOT MATCHED BY SOURCE THEN DELETE;
```
![[Pasted image 20250514224716.png|450]]

**Scheduling Jobs in SqlServer** : -
![[Pasted image 20250514224858.png|240]]

![[Pasted image 20250514225759.png |440]]

