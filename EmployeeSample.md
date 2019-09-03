-- all the available fields 
SELECT * FROM Employee;

-- only specific Columns FROM the table 
SELECT ID,Salary FROM Employee;

-- DISTINCT 
SELECT with DISTINCT keyword

-- SQL Alias
SELECT Name AS Employee Name, Salary AS Compensation FROM Employee;


-- AGGREGATE FUNCTIONS
SELECT CONCAT(Name, '(', Department, ')') as name ,Salary FROM Employee;
SELECT  COUNT(Name) FROM Employee;
SELECT  SUM(Salary) FROM Employee;
SELECT  MAX(Salary) FROM Employee;
SELECT  AVG(Salary) FROM Employee;
SELECT  MIN(Salary) FROM Employee;


-- Equal To (=) condition
SELECT * FROM Employee WHERE ID=1;

-- Greater Than (>) condition
SELECT * FROM Employee WHERE Salary>70000;

-- Greater Than or Equal To (>=) condition
SELECT * FROM Employee WHERE Salary>=70000;


Less Than  (<) condition	
SELECT * FROM Employee WHERE Salary<40000;


Less Than  or Equal To (<=) condition
SELECT * FROM Employee WHERE Salary<=20000;


Not Equal To (!=) / (<>) condition
SELECT * FROM Employee WHERE Branch !='Pune' ;


AND Operator
SELECT * FROM Employee WHERE Salary>=70000 AND Gender='Female';


OR Operator
SELECT * FROM Employee WHERE Salary>=70000 OR Gender='Female';


combine AND & OR operators.
SELECT * FROM Employee WHERE (Salary>70000 AND Gender='Female') OR Branch='Pune';

BETWEEN clause
SELECT * FROM Employee WHERE Salary BETWEEN 70000 AND 90000;



IN Keyword
SELECT * FROM Employee WHERE Branch IN ('Pune', 'Mumbai');


LIKE keyword.
Find records of employees whose Names ends with character ‘y’
SELECT * FROM Employee WHERE Name LIKE '%y';

Find records of employees whose Names starts with character ‘J’
SELECT * FROM Employee WHERE Name LIKE 'J%';

Find records of employees whose Names start with character ‘R’ and end with character ‘t’.  In between any characters are allowed
SELECT * FROM Employee WHERE Name LIKE 'R%t';

This query finds records with employee names of pattern ‘nn’ in between a employee name.
SELECT * FROM Employee WHERE Name LIKE '%nn%';

Find records of employees with a Name having exact 5 characters and that starts with “M”
SELECT * FROM Employee WHERE Name LIKE 'M - - - - ';


Find records of employees with a Name that have “o” in the second position.
SELECT * FROM Employee WHERE Name LIKE '_o%';

Find records of employees whose Branch is Not Pune and Mumbai.
SELECT * FROM Employee WHERE Branch NOT IN ('Pune', 'Mumbai');

Find records of employees whose ID is Not between 5 and 10
SELECT * FROM Employee WHERE ID NOT BETWEEN 5 AND 10;

Find records of employees whose name does NOT start with “M”:
SELECT * FROM Employee WHERE Name NOT LIKE 'M%';






