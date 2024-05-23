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