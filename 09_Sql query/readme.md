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
SELECT UPPER('PARTH');
-- This query will convert the string 'parth' to uppercase, returning 'PARTH'.

-- Converting a string to lowercase
SELECT LCASE('PARTH');
SELECT LOWER('PARTH');
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

#### ascending and descending

```

-- Ascending Order (default):
-- The following query selects all records from the `Worker` table and orders them by the `salary` column in ascending order by default.
SELECT * FROM Worker ORDER BY salary;

-- Ascending Order (explicit):
-- The following query is equivalent to the previous one but explicitly specifies ascending order using the `ASC` keyword.
SELECT * FROM Worker ORDER BY salary ASC;

-- Descending Order:
-- The following query selects all records from the `Worker` table and orders them by the `salary` column in descending order using the `DESC` keyword.
SELECT * FROM Worker ORDER BY salary DESC;

```

#### distinct

```
SELECT DISTINCT department FROM worker;

- total departments in one by one row : HR, Admin, Finance, Admin, HR, Admin
- answer : HR, Admin, Finance
 
```

#### GROUP BY with aggregation

```

-- [video] https://youtu.be/FztbYXeOEQ4?si=cuzv77BsfEp-oA5l

-- GROUP BY
SELECT department FROM Worker GROUP BY department ;
-- if i am not using any aggregation here so it acts as DISTINCT

-- here count number per department
SELECT department, COUNT(department) FROM Worker GROUP BY department ;
-- here staring department and after grp by department is going to be same

-- min salary per department
SELECT department, COUNT(salary) FROM Worker GROUP BY department ;

-- COUNT(), SUM(), AVG(), MIN(), MAX()

------------------------------------------------------------------------------

-- HAVING key word 
-- same as WHERE but while using GROUP BY we have to use having insted of where

SELECT department, SUM(salary) FROM Worker GROUP BY department HAVING COUNT(salary) > 40000 ;

```

# DDL constraints / keys

#### primary key
```
CREATE TABLE Customer (
    id INT NOT NULL PRIMARY KEY,
    branch_id INT,
    first_name CHAR(50),
    last_name CHAR(50)
);

---------------------------------------

CREATE TABLE Customer (
    id INT NOT NULL,
    branch_id INT,
    first_name VARCHAR(50),
    last_name VARCHAR(50),
    PRIMARY KEY (id)
);

```

#### forign key

```
CREATE TABLE Orders (
    id INT NOT NULL PRIMARY KEY,
    delivery_date DATE,
    order_placed_date DATE,
    cust_id INT,
    FOREIGN KEY (cust_id) REFERENCES Customer(id)
);

-- here forign key is "cust_id" which is refering to the customer table's primary key named "id"
```

#### unique
```
CREATE TABLE Customer (
    ....
    email VARCHAR(1024) UNIQUE
);
```

#### check / validation CONSTRAINT
```
CREATE TABLE Customer (
    id INT NOT NULL PRIMARY KEY,

    age INT,
    CONSTRAINT age_check CHECK (age > 12)
);

-- CONSTRAINT age_check : This names the constraint as age_check
-- CHECK (age > 12) : This specifies that the age column must contain values greater than 12.

-------------------------------------------------------------

-- “age_check”, can also avoid this, MySQL generates name of constraint automatically.

CREATE TABLE Customer (
    id INT NOT NULL PRIMARY KEY,
   
    age INT,
    CHECK (age > 12)
);

```

#### default

```
CREATE TABLE account (
    id INT NOT NULL PRIMARY KEY,
    ...

    saving_rate DOUBLE NOT NULL DEFAULT 4.25
);
```

# ALTER operation


#### ADD - new column
```
ALTER TABLE customer
ADD age INT NOT NULL;
```

#### MODIFY - Change datatype of an attribute.
```
ALTER TABLE customer
MODIFY price DOUBLE;
-- float to double datatype
-- the absence of DEFAULT and NOT NULL specifications indicates that the column will retain its existing settings for these properties

```

#### CHANGE column name
```
ALTER TABLE customer
CHANGE COLUMN name customer_name VARCHAR(1024);

-- If you want to keep the existing data type, you can omit the data type specification, and MySQL will retain the existing data type for the column.

```

#### DROP COLUMN
```
ALTER TABLE customer 
DROP COLUMN col_name;

```

#### RENAME the table
```
ALTER TABLE oldTableName RENAME TO newTableName;
```

# DML - data manuplation language

#### INSERT
```
INSERT INTO table_name (col1, col2, col3)
VALUES 
    (v1, v2, v3),
    (val1, val2, val3);

---------------------------------------------------------

INSERT INTO table_name 
VALUES 
    (v1, v2, v3),
    (val1, val2, val3);

-- here col names are not imp it will take it automatically values by using the predefined cols order

---------------------------------------------------------
-- above 2 ways might not work in sql

INSERT ALL 
    INTO employees (employeenumber, firstname, lastname, email, jobtitle, officecode, reportsto, extension) 
    VALUES (7879, 'parth', 'patel', 'prpatel52@myseneca.ca', 'Cashier', 4, 1088, 'prpatel52')
    INTO employees (employeenumber, firstname, lastname, email, jobtitle, officecode, reportsto, extension) 
    VALUES (7777, 'dhruv', 'desai', 'dhruv@gmail.com', 'Cashier', 5, 1088, 'dhruvdk')
SELECT * FROM dual;


```

#### UPDATE
```
UPDATE table_name
SET col1Name = 1, col2Name = 'abc'
WHERE id = 1;
```

##### ON UPDATE CASCADE
```
-- Can be added to the table while creating constraints. Suppose there is a situation where we have two tables
such that primary key of one table is the foreign key for another table. if we update the primary key of the first
table then using the ON UPDATE CASCADE foreign key of the second table automatically get updated.

CREATE TABLE customers (
    id INT PRIMARY KEY,
    name VARCHAR(100)
);

CREATE TABLE orders (
    order_id INT PRIMARY KEY,
    customer_id INT,
    order_date DATE,
    FOREIGN KEY (customer_id) REFERENCES customers(id) ON UPDATE CASCADE
);


-- inserting
INSERT INTO customers (id, name) VALUES (1, 'Alice');
INSERT INTO orders (order_id, customer_id, order_date) VALUES (101, 1, '2024-05-25');

-- updating  
UPDATE customers SET id = 2 WHERE id = 1;

-- After this update, the customer_id in the orders table will automatically be updated from 1 to 2 because of the ON UPDATE CASCADE clause
```

#### DELETE row
```
DELETE FROM table_name
WHERE id = 1;

-- IF YOU DO THIS WITHOUT CONDITION then it is going to delete all cols
```

##### DELETE CASCADE - (to overcome DELETE constraint of Referential constraints)
```
CREATE TABLE customer (
    id INT PRIMARY KEY,
    name VARCHAR(100)
);

CREATE TABLE order (
    order_id INT PRIMARY KEY,
    delivery_date DATE,
    cust_id INT,
    FOREIGN KEY (cust_id) REFERENCES customer(id) ON DELETE CASCADE
);

-- The 'order' table references the 'customer' table.
-- Using 'ON DELETE CASCADE' ensures that when a row in the 'customer' table is deleted,
-- all related rows in the 'order' table are automatically deleted.
```

##### ON DELETE NULL - (can FK have null values?)
```
CREATE TABLE customer (
    id INT PRIMARY KEY,
    name VARCHAR(100)
);

-- The 'order' table references the 'customer' table.
-- Using 'ON DELETE SET NULL' ensures that when a row in the 'customer' table is deleted,
-- the 'cust_id' in the 'order' table is set to NULL.

CREATE TABLE `order` (
    order_id INT PRIMARY KEY,
    delivery_date DATE,
    cust_id INT,
    FOREIGN KEY (cust_id) REFERENCES customer(id) ON DELETE SET NULL
);

```

#### REPLACE - if data is already present then replace that data OR if data is not there then add that data

```
-- if data is already present then replace that data OR if data is not there then add that data
-- if it behaves like replace then all old entries of that row becomes NLLL

REPLACE INTO student (id, class) VALUES (2, 11), (3, 8);

REPLACE INTO student SET id = 4, class = 3;

```

#### exta things

```

-- sub string and concate

-- SUBSTR means
-- SUBSTR(string_expression, start_position, length)
-- SUBSTR(FIRSTNAME, 1, 1) ===> first_initial

SELECT (SUBSTR(FIRSTNAME, 1, 1) || LASTNAME) AS USERNAME
FROM employee2;

-------------------------------------------------
-- find index or postiton
SELECT INSTR(first_name, 'b') AS position
FROM worker
WHERE first_name = 'Amitabh';

-- give ans as 6

--------------------------------------------------
-- Limit rows
SELECT column1, column2, ...
FROM table_name
LIMIT number_of_rows;

SELECT *
FROM employees
LIMIT 5;
-- only 5 rows shows as output even if output has more than 5 rows

---------------------------------------------------

-- Q-4. Write an SQL query to print the first three characters of  FIRST_NAME from Worker table.
select substring(first_name, 1, 3) from worker;

-- Q-5. Write an SQL query to find the position of the alphabet (‘b’) in the first name column ‘Amitabh’ from Worker table.
select INSTR(first_name, 'B') from worker where first_name = 'Amitabh';

-- Q-6. Write an SQL query to print the FIRST_NAME from Worker table after removing white spaces from the right side.
select RTRIM(first_name) from worker;

-- Q-7. Write an SQL query to print the DEPARTMENT from Worker table after removing white spaces from the left side.
select LTRIM(first_name) from worker;

-- Q-8. Write an SQL query that fetches the unique values of DEPARTMENT from Worker table and prints its length.
select distinct department, LENGTH(department) from worker;

-- Q-9. Write an SQL query to print the FIRST_NAME from Worker table after replacing ‘a’ with ‘A’.
select REPLACE(first_name, 'a', 'A')  from worker;

-- Q-10. Write an SQL query to print the FIRST_NAME and LAST_NAME from Worker table into a single column COMPLETE_NAME.
-- A space char should separate them.
select CONCAT(first_name, ' ', last_name) AS COMPLETE_NAME from worker;

-- Q-20. Write an SQL query to print details of the Workers who have joined in Feb’2014.
select * from worker where YEAR(joining_date) = 2014 AND MONTH(joining_date) = 02;

-- Q-26. Write an SQL query to show only odd rows from a table.
-- select * from worker where MOD (WORKER_ID, 2) != 0;    -- modulas
select * from worker where MOD (WORKER_ID, 2) <> 0;       -- <> behaves like not equal

-- Q-28. Write an SQL query to clone a new table from another table.
CREATE TABLE worker_clone LIKE worker;
INSERT INTO worker_clone select * from worker;
select * from worker_clone;

-- how to do same in single query ? 
CREATE TABLE worker_clone AS 
SELECT * 
FROM worker;

-- Q-31. Write an SQL query to show the current date and time.
-- DUAL
select curdate();
select now();

-- Q-32. Write an SQL query to show the top n (say 5) records of a table order by descending salary.
select * from worker order by salary desc LIMIT 5;

-- Q-33. Write an SQL query to determine the nth (say n=5) highest salary from a table.
select * from worker order by salary desc LIMIT 4,1;

-- Q-34. Write an SQL query to determine the 5th highest salary without using LIMIT keyword.
select salary from worker w1
WHERE 4 = (
SELECT COUNT(DISTINCT (w2.salary))
from worker w2
where w2.salary >= w1.salary
);

-- Q-35. Write an SQL query to fetch the list of employees with the same salary.
-- using JOIN without join
select w1.* from worker w1, worker w2 where w1.salary = w2.salary and w1.worker_id != w2.worker_id;

-- Q-36. Write an SQL query to show the second highest salary from a table using sub-query.
select max(salary) from worker
where salary not in (select max(salary) from worker);

-- Q-37. Write an SQL query to show one row twice in results from a table.
select * from worker
UNION ALL
select * from worker ORDER BY worker_id;

-- Q-39. Write an SQL query to fetch the first 50% records from a table.
select * from worker where worker_id <= ( select count(worker_id)/2 from worker);

-- Q-42. Write an SQL query to show the last record from a table.
select * from worker where worker_id = (select max(worker_id) from worker);

-- Q-43. Write an SQL query to fetch the first row of a table.
select * from worker where worker_id = (select min(worker_id) from worker);

------------------------------------------------------

```