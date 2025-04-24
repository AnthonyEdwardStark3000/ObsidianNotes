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
##### SQL constraints
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
**Composite key - Making two or more columns as Primary key

```
CREATE TABLE OrderDetail (OrderID INTEGER,ProductID INTEGER,
DateOfPurchase DATE,Price FLOAT CONSTRAINT pk_orderdetail PRIMARY KEY(OrderID,ProductID));

-- Using ALTER statement it should be made an Non-nullable column

CREATE TABLE OrderDetail (OrderID INTEGER NOT NULL,ProductID INTEGER NOT NULL,
DateOfPurchase DATE,Price FLOAT);

ALTER TABLE OrderDetail ADD CONSTRAINT pk_orderdetail PRIMARY KEY(OrderID,ProductID);
```
**NOT NULL Constraint

By default an table can have null values in it's fields , for restricting this ==NOT NULL constraint== can be used .

```
CREATE TABLE OrderDetail (OrderID INTEGER NOT NULL,ProductID INTEGER,
DateOfPurchase DATE,Price FLOAT);

-- Using ALTER statement for adding Not-null constraint

ALTER TABLE OrderDetail ALTER COLUMN ProductID INTEGER NOT NULL
```
**Unique Constraints

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
**Default constraint

Assigns the default value to the column if no value is provided to that column during insertion of data .
