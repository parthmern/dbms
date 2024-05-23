```
-- Create the database
CREATE DATABASE ORG;

-- Show all databases
SHOW DATABASES;

-- Select the database to use
USE ORG;

-- Create the Worker table
CREATE TABLE Worker (
    WORKER_ID INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
    FIRST_NAME CHAR(25),
    LAST_NAME CHAR(25),
    SALARY INT,
    JOINING_DATE DATETIME,
    DEPARTMENT CHAR(25)
);

```

another table

```
-- Create the Bonus table
CREATE TABLE Bonus (
    WORKER_REF_ID INT,
    BONUS_AMOUNT INT,
    BONUS_DATE DATETIME,
    FOREIGN KEY (WORKER_REF_ID)
    REFERENCES Worker (WORKER_ID)
    ON DELETE CASCADE
);

```

another table

```

-- Create the Title table
CREATE TABLE Title (
    WORKER_REF_ID INT,
    WORKER_TITLE CHAR(25),
    AFFECTED_FROM DATETIME,
    FOREIGN KEY (WORKER_REF_ID)
    REFERENCES Worker (WORKER_ID)
    ON DELETE CASCADE
);

```

![image](https://github.com/parthmern/dbms/assets/125397720/ce8170c9-5d35-46b7-ad5a-761b6cd550dd)

```

-- INSERTING MULTIPLE VALUES

INSERT INTO Worker (
    WORKER_ID,
    FIRST_NAME,
    LAST_NAME,
    SALARY,
    JOINING_DATE,
    DEPARTMENT
) VALUES
(1, 'Monika', 'Arora', 100000, '2020-02-14 09:00:00', 'HR'),
(2, 'Niharika', 'Verma', 80000, '2020-02-14 09:00:00', 'Admin'),
(3, 'Vishal', 'Singhal', 300000, '2020-02-14 09:00:00', 'HR'),
(4, 'Amitabh', 'Singh', 500000, '2020-02-14 09:00:00', 'Admin'),
(5, 'Vivek', 'Bhati', 500000, '2011-06-14 09:00:00', 'Admin'),
(6, 'Vipul', 'Diwan', 200000, '2011-06-14 09:00:00', 'Account'),
(7, 'Satish', 'Kundre', 75000, '2008-04-10 09:00:00', 'Account'),
(8, 'Geetika', 'Chauhan', 90000, '2020-02-14 09:00:00', 'Admin');


```

```

-- INSERTING INTO Bonus table
INSERT INTO Bonus (
    WORKER_REF_ID,
    BONUS_AMOUNT,
    BONUS_DATE
) VALUES
(1, 5000, '2020-02-16'),
(2, 3000, '2011-06-16'),
(3, 4000, '2020-02-16'),
(1, 4500, '2020-02-16'),
(2, 3500, '2011-06-16');

```

## Retrival examples

```

-- Adding two numbers
SELECT 11 + 12;
-- This query will return the sum of 11 and 12, which is 23.

-- Getting the current date and time
SELECT NOW();
-- This query will return the current date and time when the query is executed.

-- Converting a string to uppercase
SELECT UCASE('parth');
-- This query will convert the string 'parth' to uppercase, returning 'PARTH'.

-- Converting a string to lowercase
SELECT LCASE('PARTH');
-- This query will convert the string 'PARTH' to lowercase, returning 'parth'.

-- Selecting all columns from the Worker table
SELECT * FROM Worker;
-- This query will return all records and all columns from the Worker table.

-- Selecting all records from Worker where the DEPARTMENT is 'HR'
SELECT * FROM Worker WHERE DEPARTMENT = 'HR';
-- This query will return all records from the Worker table where the DEPARTMENT column is 'HR'.

-- Selecting all records from Worker where the SALARY is greater than 8000
SELECT * FROM Worker WHERE SALARY > 8000;
-- This query will return all records from the Worker table where the SALARY column is greater than 8000.

-- Selecting specific columns (FIRST_NAME and WORKER_ID) from Worker where SALARY is greater than 8000
SELECT FIRST_NAME, WORKER_ID FROM Worker WHERE SALARY > 8000;
-- This query will return only the FIRST_NAME and WORKER_ID columns from the Worker table for records where the SALARY column is greater than 8000.


-- BETWEEN SOMETHING RANGE
SELECT * FROM Worker WHERE SALARY BETWEEN 80000 AND 300000 ;
-- here 80000 and 300000 is inclusive

-- Using OR
SELECT * FROM Worker WHERE DEPARTMENT = 'HR' OR DEPARTMENT = 'Admin' OR DEPARTMENT = 'Account';

-- to reduce multiple OR
-- Using IN
SELECT * FROM Worker WHERE DEPARTMENT IN ('HR', 'Admin', 'Account');

-- NOT 
-- ! ( IN ('HR', 'Admin', 'Account') )
SELECT * FROM Worker WHERE DEPARTMENT NOT IN ('HR', 'Admin', 'Account');

-- AND
SELECT * FROM Worker WHERE DEPARTMENT = 'HR' AND SALARY > 80000;

-- IS NULL
-- showing null values from table row
SELECT * FROM Worker WHERE SALARY IS NULL;

```

#### wildcards

```

-- Using '%' Wildcard:
-- The '%' wildcard represents any number of characters (including zero) from 0 to n.
-- It is similar to the '*' asterisk in regular expressions.

-- Example:
-- Selecting all records from the `customer` table where the `name` ends with 'p'.
SELECT * FROM customer WHERE name LIKE '%p';

-- Selecting all records from the `customer` table where the `name` contains 'John' anywhere in the string.
SELECT * FROM customer WHERE name LIKE '%John%';

-- Using '_' Wildcard:
-- The '_' wildcard represents exactly one character.

-- Example:
-- Selecting all records from the `customer` table where the `name` has exactly three characters and starts with 'J'.
SELECT * FROM customer WHERE name LIKE 'J__';

-- Combining '%' and '_' Wildcards:
-- The combination of '%' and '_' can be used to match specific patterns.

-- Example:
-- Selecting all records from the `customer` table where the `name` starts with 'A', followed by any two characters, and ends with 'n'.
SELECT * FROM customer WHERE name LIKE 'A__n';

-- Note: The '_' wildcard matches exactly one character, while the '%' wildcard matches any number of characters (including zero).


```