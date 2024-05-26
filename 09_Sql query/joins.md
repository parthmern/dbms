# JOINS

```
scaler article = https://www.scaler.com/topics/sql/joins-in-sql/
```

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

![cross-join-meaning](https://github.com/parthmern/dbms/assets/125397720/109df4d8-6aef-4677-a6e3-59e7d63ab175)

```
SELECT column_list FROM table1 CROSS JOIN table2;

```

## SELF join

```
SELECT columns FROM table1 AS t1
INNER JOIN table2 AS t2 ON t1.id = t2.id;

-- no separate keyword

- UNARY relation ( employee manages employee)
```

## Join without using join keywords

```
SELECT * FROM table1, table2 WHERE condition;

SELECT artist_name, album_name, year_recorded
FROM artist, album
WHERE artist.id = album.artist_id;

-- using inner joins without inner keyword
```

# SET operations

```
article = https://medium.com/@ritusantra/sql-set-operators-ms-sql-server-9ee311f48ee6
```

![image](https://github.com/parthmern/dbms/assets/125397720/48c6bb77-6538-4433-a744-28ea1bc7fba0)


## UNION

```
SELECT * FROM table1
UNION
SELECT * FROM table2;
```

![image](https://github.com/parthmern/dbms/assets/125397720/d27575eb-aa33-467c-b0e6-8781dfe7a8fe)


## INTERSECT

```
SELECT * FROM table1
INTERSECT
SELECT * FROM table2;

-- but in sql we donot have word like intersect so we need to emulate

SELECT DISTINCT id FROM table1
INNER JOIN table2 ON USING(id);

SELECT DSITINCT id FROM table1
INNER JOIN table2 ON table1.id = table2.id;

```

![image](https://github.com/parthmern/dbms/assets/125397720/c10c39fe-5ab2-4a39-8f0b-fd7386c9171e)


## MINUS / EXCEPT

```
SELECT id FROM table1 LEFT JOIN table2 USING(id) WHERE table2.id IS NULL;
```
![image](https://github.com/parthmern/dbms/assets/125397720/6b688e97-83ce-470d-8aff-1749c30eff52)
