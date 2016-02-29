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
'''
### SQL Statement

### Delete Statement

### Update Statement
