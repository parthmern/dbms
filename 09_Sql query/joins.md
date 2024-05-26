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


## UNION

```
SELECT * FROM table1
UNION
SELECT * FROM table2;
```

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

## MINUS

```
SELECT id FROM table1 LEFT JOIN table2 USING(id) WHERE table2.id IS NULL;
```