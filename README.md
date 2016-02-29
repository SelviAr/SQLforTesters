# SQLforTesters
This is SQL code snippets


### Create Statements
```SQL
-- Create new Customer table to store all the constomer information
CREATE TABLE Customer(
PersonID INT IDENTITY(1,1),
FirstName VARCHAR(30) NOT NULL,
LastName VARCHAR(30) NOT NULL,
DateofBith DATETIME
Age INT,
Sex CHAR(10),
ActiveUser bit
)
```

### Insert Statements
```SQL

-- Create data using insert data
-- to save the data in the databse
INSERT INTO Person ( FirstName, LastName, Age, Sex, AMIAWESOME) 
VALUES ('Rams', 'Pal', 40, 'M', 1)

--Multiple INSERTs
INSERT INTO Person ( FirstName, LastName, Age, Sex, AMIAWESOME) 
VALUES ('Sel', 'A', 'F')
VALUES ('Mike', 'J', 'M')

--From some other table
INSERT INTO Person ( FirstName, LastName, Age, Sex, AMIAWESOME)
SELECT ( FirstName, LastName, Age, Sex, AMIAWESOME)
FROM SOME_OTHER_TABLE
```

### SQL Statement
```SQL

-- Get all all the data from the person table
SELECT * FROM Person

-- Get selected column from the person table
SELECT FirstName, AGE FROM Person

-- Provide alias name to the column
SELECT FirstName, AGE as Totalnoofyearintheearth FROM Person

--Create dynamic column using existing table column, and provide alias name
SELECT FirstName + ' ' +  LastName AS FullName, AGE FROM Person

-- Calling functions
SELECT UPPER(FirstName) AS FirstName, LastName FROM Person

--Filtering Records
SELECT * FROM Person WHERE PersonID = 2

SELECT * FROM Person WHERE FirstName = 'Rams'

--Not equal to
SELECT * FROM Person WHERE FirstName != 'Rams'

SELECT * FROM Person WHERE age > 36

SELECT * FROM Person WHERE FirstName LIKE '%am%'

--AND
SELECT * FROM Person WHERE age > 36 AND FirstName = 'Rams'

--OR
SELECT * FROM Person WHERE age > 36 OR Sex = 'F'

SELECT * FROM Person WHERE SEX IN ('M', 'F')

SELECT * FROM Person WHERE SEX NOT IN ('M', 'F')

--Get name size more than 3
SELECT * FROM Person WHERE LEN(FirstName) > 2

--Get all aweome user
SELECT * FROM Person WHERE AmIAwesome = 1
```

### Delete Statement
```SQL
DELETE FROM Person

DELETE FROM Person WHERE PHONE IS NULL AND EMAIL IS NULL

```


### Update Statement
```SQL
UPDATE ATTENDEE SET EMAIL = UPPER(EMAIL)

UPDATE ATTENDEE SET VIP = 1 WHERE ATTENDEE_ID IN (3,4)

```


### Group Statements
```SQL

SELECT COUNT(*) AS record_count FROM Person;

SELECT COUNT(*) AS record_count FROM Person  WHERE age > 36



SELECT year, COUNT(*) AS record_count FROM station_data
WHERE tornado = 1
GROUP BY year;



SELECT year, month, COUNT(*) AS record_count FROM station_data
WHERE tornado = 1
GROUP BY year, month
ORDER BY year, month


SELECT month, AVG(temp) as avg_temp
FROM station_data
WHERE year >= 2000
GROUP BY month


SELECT year, SUM(snow_depth) as total_snow
FROM station_data
WHERE year >= 2000
GROUP BY year


```


### Inbuild Function
```SQL
 SUM(), MAX(), MIN(), AVG(), and COUNT() 
```


### Join Statements
```SQL
FROM CUSTOMER INNER JOIN CUSTOMER_ORDER
ON CUSTOMER.CUSTOMER_ID = CUSTOMER_ORDER.CUSTOMER_ID


```


### Views


### Custom Functions

### Stored Procedure

