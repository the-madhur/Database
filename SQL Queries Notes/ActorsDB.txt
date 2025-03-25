**MySQL Notes: Working with ACTORSDATABASE**

### 1. Creating a Database
```sql
CREATE DATABASE ACTORSDATABASE;
```

### 2. Viewing Available Databases
```sql
SHOW DATABASES;
```

### 3. Using the Created Database
```sql
USE ACTORSDATABASE;
```

### 4. Creating a Table
```sql
CREATE TABLE Actors (
    Name VARCHAR(50),
    Gender VARCHAR(10),
    Charges INT,
    ID INT
);
```

### 5. Viewing Table Structure
```sql
DESC Actors;
```

### 6. Inserting Records into the Table
```sql
INSERT INTO Actors (Name, Gender, Charges, ID) VALUES
    ("RDJ", "MALE", 1000000, 1),
    ("Chris Evans", "MALE", 10000, 2),
    ("Johnny Depp", "MALE", 120000, 3),
    ("Vin Diesel", "MALE", 30000, 4),
    ("Chris Hemsworth", "MALE", 500000, 5);
```

### 7. Selecting All Records
```sql
SELECT * FROM Actors;
```

### 8. Filtering Records (Excluding a Specific Value)
```sql
SELECT * FROM Actors WHERE Charges != 30000;
```

### 9. Updating a Record
```sql
UPDATE Actors SET Name = "Robert Downey Jr" WHERE Name = "RDJ";
```

### 10. Filtering Records Using `IN`
```sql
SELECT * FROM Actors WHERE Charges IN (10000, 30000, 500000);
```

### 11. Filtering Records Using `NOT IN`
```sql
SELECT * FROM Actors WHERE Charges NOT IN (10000, 30000, 500000);
```

### 12. Using `LIKE` for Pattern Matching
#### a) Names Starting with 'C'
```sql
SELECT * FROM Actors WHERE Name LIKE 'C%';
```
#### b) Names Ending with 'pp'
```sql
SELECT * FROM Actors WHERE Name LIKE '%pp';
```
#### c) Names Containing 'is'
```sql
SELECT * FROM Actors WHERE Name LIKE '%is%';
```
#### d) Multiple Conditions in `LIKE`
```sql
SELECT * FROM Actors WHERE Name LIKE '%is%' OR Name LIKE '%th';
```
#### e) Using Underscore `_` for Single Character Matching
```sql
SELECT * FROM Actors WHERE Name LIKE 'C_r__';
```
```sql
SELECT * FROM Actors WHERE Gender LIKE 'M_l_';
```
```sql
SELECT * FROM Actors WHERE Name LIKE 'V__ Di____';
```

### Notes:
- The `LIKE` operator is case-insensitive by default.
- `%` matches any number of characters, while `_` matches a single character.
- `IN` and `NOT IN` are useful for filtering specific values efficiently.
- `UPDATE` modifies existing records; use it carefully.
- `DESC` helps check table structures before performing queries.

This example provides a fundamental understanding of MySQL queries using ACTORSDATABASE.

