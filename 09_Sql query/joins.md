# JOINS

## Inner join

![image](https://github.com/parthmern/dbms/assets/125397720/311a2bd9-ef2c-4386-8124-52cd38fdc951)


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
