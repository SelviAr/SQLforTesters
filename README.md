# SQLforTesters
This is SQL code snippets


##Table of Contents

- [Create Statement](#create-statements)
- [Drop Table Statements](#drop-table-statements)
- [Insert Statement](#insert-statements)
- [Select Statement](#select-statements)
- [Delete Statement](#delete-statements)
- [Group Statement](#group-statements)
- [Orderby Statement](#orderby-statements)
- [join Statement](#join-statements)
- [views](#views)
- [Custom Functions](#custom-functions)
- [Stored Procedure](#stored-procedure)
 
### Create Statements
```SQL

-- Create a new Customer table to store customer information
CREATE TABLE Customers(
	CustomerID	INT IDENTITY(1,1) PRIMARY KEY,
	FirstName	NVARCHAR(30) NOT NULL,
	LastName	NVARCHAR(30) NOT NULL,
	DateofBith	DATETIME,
	Age			INT,
	Sex			NCHAR(1),
	ActiveUser	BIT,
	CreatedDate DATETIME DEFAULT GETDATE()
)

-- This table is used to store the customers address
CREATE TABLE Addresses(
	AddressID	INT IDENTITY(1,1) PRIMARY KEY,
	CustomerID	INT NOT NULL,
	AddressType	NVARCHAR(10),	--HOME, BUSINESS
	FullAddress	NVARCHAR(50) NOT NULL,
	City		NVARCHAR(30),
	Zipcode		NVARCHAR(30),
	StateCode	NCHAR(2),
	CreatedDate DATETIME DEFAULT GETDATE()
)

```

### Drop Table Statements
```SQL

--Delete the Customer table from the databse
DROP TABLE Customers

--Delete the Addresses table from the databse
DROP TABLE Addresses

```


### Insert Statements
```SQL

-- Create data in the Customers table using INSERT statement
-- Use INSERT statement to save the data in the Customers table
INSERT INTO Customers ( FirstName, LastName, DateofBith, Age, Sex, ActiveUser) 
VALUES ('Selvi', 'Aru', '10-10-1985', 30, 'F', 1)

--Multiple INSERTs
INSERT INTO Customers ( FirstName, LastName, DateofBith, Age, Sex, ActiveUser) VALUES 
('Vikram', 'Pal', '07-05-2005', 10, 'M', 1),
('Akshi', 'Pal', '05-04-2009', 7, 'F', 1),
('Mike', 'J', '05-04-1975', 40, 'M', 1)


INSERT INTO Addresses (CustomerID, AddressType, FullAddress, City, Zipcode, StateCode) VALUES 
(1, 'HOME', '100 Mowry Ave', 'Fremont', '94536', 'CA'),
(1, 'BUSINESS', '100 Fremont Blvd', 'Fremont', '94538', 'CA')	


--Moving data from one table to another table
INSERT INTO Customers_Temp (FirstName, LastName, DateofBith, Age, Sex )
SELECT FirstName, LastName, DateofBith, Age, Sex
FROM Customers

```

### SELECT Statements
```SQL

-- Get all the data from the Customers table
SELECT * FROM Customers

-- Get selected column from the Customers table
SELECT FirstName, Age FROM Customers

-- Provide alias name to the column
SELECT FirstName, Age as CustomerAge FROM Customers

--Create dynamic column using existing table column, and provide alias name
SELECT FirstName + ' ' +  LastName AS FullName, Age FROM Customers

--Filtering Records
-- Filtering data by the primary key value (Unique value)
SELECT * FROM Customers WHERE CustomerID = 2

-- Get all the customers who's firstname is Selvi
SELECT * FROM Customers WHERE FirstName = 'Selvi'

-- Get all the customers who's firstname is not Rams
SELECT * FROM Customers WHERE FirstName != 'Selvi'

-- Get all the customers who's age is more than 36
SELECT * FROM Customers WHERE age > 36

-- Get all the customers who's name contains elv in it
SELECT * FROM Customers WHERE FirstName LIKE '%elv%'		-- Using LIKE

-- Get all the customer's name is Selvi and age older than 36
SELECT * FROM Customers WHERE age > 36 AND FirstName = 'Selvi' --AND Condition

-- Get all the customer' who's age older than 36 or the female customers 
SELECT * FROM Customers WHERE age > 36 OR Sex = 'F'		--OR Condition

-- Get all the customer who's age is 20 or 30 or 40
SELECT * FROM Customers WHERE Age IN (20, 30, 40)		-- IN Condition

-- Get all the customer who's age is not 20 or 30 or 40
SELECT * FROM Customers WHERE Age NOT IN (20, 30, 40)	-- NOT IN Condition

--Get all aweome user
SELECT * FROM Customers WHERE ActiveUser = 1

-- Get first 10 customers from the table
SELECT TOP 10 * FROM Customers;

-- Get first 50 percentage of Customers from the table
SELECT TOP 50 PERCENT * FROM Customers;

--Get list of unique value from the column 
SELECT DISTINCT FirstName FROM Customers

```

### Delete Statements
```SQL

-- Delete all the data from the table Customers
DELETE FROM Customers

DELETE FROM Customers WHERE Age > 40 AND Sex = 'F'

```


### Update Statements
```SQL

UPDATE Customers SET FirstName = UPPER(FirstName)

UPDATE Customers SET ActiveUser = 0 WHERE Age < 10

```

### Inbuild SQL Functions
```SQL

-- Get number of rows in the Customers table
SELECT COUNT(*) AS TotalNoOfCustomers FROM Customers

-- Get number of rows in the Customers table who's age is more than 36
SELECT COUNT(*) AS TotalNoOfCustomers  FROM Customers  WHERE Age > 36

SELECT SUM(Age) AS record_count FROM Customers
SELECT MAX(Age) AS record_count FROM Customers
SELECT MIN(Age) AS record_count FROM Customers
SELECT AVG(Age) AS record_count FROM Customers

SELECT UPPER(FirstName) AS FirstName, LastName FROM Customers
SELECT FirstName, UPPER(FirstName) AS LengthofTheName  FROM Customers
SELECT FirstName, UPPER(FirstName) AS LengthofTheName  FROM Customers
 
-- Get all the customer who's firstname contains at least 6 characters
SELECT * FROM Customers WHERE LEN(FirstName) > 5 --Using function in the WHERE condition

```


### Group Statements
```SQL

SELECT Sex, COUNT(*) AS record_count FROM Customers
WHERE  Age > 10
GROUP BY Sex;

```

### Orderby Statements

```SQL

SELECT * FROM Customers 
ORDER BY FirstName 

SELECT * FROM Customers
ORDER BY FirstName ASC, LastName DESC;

```


### Join Statements
```SQL

--SQL INNER JOIN
SELECT * FROM Customers  INNER JOIN Addresses ON Customers.CustomerID = Addresses.CustomerID

SELECT * FROM Customers C INNER JOIN Addresses A ON C.CustomerID = A.CustomerID

--SQL LEFT JOIN 
SELECT Customers.CustomerName, Orders.OrderID
FROM Customers
LEFT JOIN Orders
ON Customers.CustomerID=Orders.CustomerID
ORDER BY Customers.CustomerName;

--SQL RIGHT JOIN
SELECT Orders.OrderID, Employees.FirstName
FROM Orders
RIGHT JOIN Employees
ON Orders.EmployeeID=Employees.EmployeeID
ORDER BY Orders.OrderID;

--SQL FULL OUTER JOIN
SELECT Customers.CustomerName, Orders.OrderID
FROM Customers
FULL OUTER JOIN Orders
ON Customers.CustomerID=Orders.CustomerID
ORDER BY Customers.CustomerName;

--SQL UNION
SELECT column_name(s) FROM FremontCustomers
UNION
SELECT column_name(s) FROM SanjoseCustomers

```


### Views
```SQL
--Create view
CREATE VIEW view_name
AS
SELECT column_name(s)
FROM table_name
WHERE condition

--Run the view
SELECT * FROM view_name

--Delete VIEW
DROP VIEW view_name
```


### Custom Functions
```SQL
-- User defined function to calculate age for the given date
CREATE FUNCTION dbo.CalculateAge (@DateofBirth DateTime)
RETURNS INT
AS 
BEGIN
    DECLARE @Age INT

	SET @Age =   FLOOR(DATEDIFF(day,@DateofBirth,GETDATE())/365.242199)

    RETURN @Age
END
GO

-- Use the function CalculateAge
SELECT dbo.CalculateAge ('01/01/1976')

UPDATE Customers SET Age = dbo.CalculateAge (DateofBirth)
```

### Stored Procedure
```SQL

CREATE PROCEDURE dbo.ExportCustomersData
	@FirstName nvarchar(50) = NULL,
    @LastName nvarchar(50) = NULL 
AS 
BEGIN
    SET NOCOUNT ON;
    
    INSERT INTO WareHouseData (FullName) VALUES(@FirstName + ' ' + @LastName)
    
END
GO

-- Execute stored procedure ExportCustomersData
EXECUTE dbo.ExportCustomersData N'Selvi', N'Arm';
-- Or
EXEC dbo.ExportCustomersData  @FirstName = N'Selvi', @LastName = N'Arm'
GO
-- Or
EXECUTE dbo.ExportCustomersData @FirstName = N'Selvi', @LastName = N'Arm';
GO


```
