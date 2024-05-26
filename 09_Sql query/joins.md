# JOINS

##  join

![image](https://github.com/parthmern/dbms/assets/125397720/311a2bd9-ef2c-4386-8124-52cd38fdc951)

```
SELECT columns FROM table1 AS t1 LEFT JOIN table2 AS t2 ON t1.id = t2.id
UNION
SELECT columns FROM table1 AS t1 RIGHT JOIN table2 AS t2 ON t1.id = t2.id;

-- there is not any word like FULL OUTER JOIN, so we need to use UNION
```

```
-- Explanation of Aliases in MySQL
-- Aliases in MySQL are used to give a temporary name to a table or a column in a table for the purpose of a particular query.
-- It works as a nickname for expressing the tables or column names. It makes the query short and neat.

SELECT *
FROM USER_TABLE AS a
INNER JOIN ORDER_TABLE AS b
ON a.USER_ID = b.USER_ID;

SELECT *
FROM USER_TABLE a
INNER JOIN ORDER_TABLE b
ON a.USER_ID = b.USER_ID;

```

## CROSS jOIN

```
SELECT column_list FROM table1 CROSS JOIN table2;

```