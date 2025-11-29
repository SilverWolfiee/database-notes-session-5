# Joins
hi


## Foreign Key
```sql
CREATE TABLE Coffee(
	CoffeeID INT PRIMARY KEY,
    CoffeeName VARCHAR(55) NOT NULL,
    CoffeeTypeID INT NOT NULL,
    FOREIGN KEY (CoffeeTypeID) REFERENCES CoffeeType(CoffeeTypeID) 
)
```

## Inner Join
```sql
-- Inner Join
SELECT *
FROM Coffee c JOIN coffeetype ct ON c.CoffeeTypeID = ct.CoffeeTypeID;
```
## RIGHT JOIN
``` sql
-- Right JOIN

SELECT *
FROM Coffee c RIGHT JOIN CoffeeType ct ON c.CoffeeTypeID = ct.CoffeeTypeID;

```

## LEFT JOIN
```sql
-- LEFT JOIN
SELECT *
FROM Coffee c LEFT JOIN coffeetype ct ON c.CoffeeTypeID = ct.CoffeeTypeID;
```


## FULL OUTER JOIN(MariaDB friendly)
```sql
-- FULL OUTER JOIN
SELECT *
FROM coffee c 
LEFT JOIN coffeetype ct 
    ON c.CoffeeTypeID = ct.CoffeeTypeID

UNION

SELECT *
FROM coffee c 
RIGHT JOIN coffeetype ct 
    ON c.CoffeeTypeID = ct.CoffeeTypeID;
```



# Premises
```sql
CREATE TABLE Student(
	ID INT PRIMARY KEY,
    Name VARCHAR(50) NOT NULL

);
CREATE TABLE TA (
    ID INT PRIMARY KEY,
    Name VARCHAR(50) NOT NULL
);

INSERT INTO Student VALUES
(1, 'kaftle'),
(2, 'SilverWolf'),
(3, 'nvg'),
(4, 'Hulina');


INSERT INTO TA VALUES
(1, 'kaftle'),
(2, 'SilverWolf'),
(3, 'Genzy'),
(4, 'Kokona')
```

## UNION(remove duplicates across tables)
```sql
SELECT Name FROM Student
UNION
Select Name FROM TA;

```
## UNION ALL (not removing duplicate data)
```sql
SELECT Name FROM Student
UNION ALL
Select Name FROM TA;

```

## Intersect(find data that exist in both)
```sql 
SELECT Name FROM Student
INTERSECT
Select Name FROM TA;
```
## EXCEPT (reverse of intersect)
```sql
SELECT Name FROM Student
EXCEPT
Select Name FROM TA;
```

# index
```sql
CREATE TABLE Staff (
    StaffID INT PRIMARY KEY,
    StaffName VARCHAR(55) NOT NULL,
    StaffAge INT NOT NULL
);

CREATE INDEX StaffAgeIndex ON Staff(StaffAge);
```
An index in SQL is similar to an index in a book:
It helps the database find rows faster.
Instead of scanning the entire table, the DB can jump directly to matching values.

speeds up select queries but slows down update insert delete queries


# view()
```sql
CREATE VIEW LongSelect AS 
SELECT * FROM Coffee; -- anggap querynya panjang bgt--
```

this can shorten the query to just
```sql
SELECT * FROM LongSelect
```