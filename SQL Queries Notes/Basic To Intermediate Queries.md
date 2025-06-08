# SQL Notes with Explanations and Use Cases

---

## 1. **Database & Table Creation**

```sql
CREATE DATABASE college;
USE college;
```
👉 *Creates and selects the database 'college'.*

```sql
CREATE TABLE Student(
    rollno INT PRIMARY KEY,
    name VARCHAR(50),
    marks INT NOT NULL,
    grade VARCHAR(1),
    city VARCHAR(20)
);
```
👉 *Defines a 'Student' table with constraints like PRIMARY KEY and NOT NULL.*

---

## 2. **Insert Records**

```sql
INSERT INTO Student (rollno, name, marks, grade, city)
VALUES 
(101, "Anil", 78, "C", "PUNE"),
(102, "Bhumika", 93, "A", "MUMBAI"),
(103, "Chetan", 85, "B", "MUMBAI"),
(104, "Dhruv", 96, "A", "DELHI"),
(105, "Emanuel", 12, "F", "DELHI"),
(106, "Farah", 82, "B", "DELHI");
```
👉 *Adds multiple student records.*

---

## 3. **Display Tables & Data**

```sql
SHOW DATABASES;
SHOW TABLES;
SELECT * FROM Student;
```
👉 *Lists databases, tables and shows all data from Student.*

---

## 4. **Filtering Data (WHERE, AND, OR, BETWEEN, IN, NOT IN)**

```sql
SELECT * FROM Student WHERE marks > 80 AND city = "Mumbai";
```
👉 *Students scoring >80 and from Mumbai.*

```sql
SELECT * FROM Student WHERE marks BETWEEN 80 AND 90;
SELECT * FROM Student WHERE city IN ("DELHI", "Gurgaon");
```
👉 *BETWEEN for ranges, IN for multiple value matches.*

---

## 5. **LIMIT and ORDER BY**

```sql
SELECT * FROM Student ORDER BY marks DESC LIMIT 3;
```
👉 *Top 3 scorers.*

```sql
SELECT * FROM Student ORDER BY city ASC;
```
👉 *Sorts by city in ascending order.*

---

## 6. **Aggregate Functions & Grouping**

```sql
SELECT MAX(marks), MIN(marks), AVG(marks), COUNT(marks) FROM Student;
```
👉 *Gives max, min, average, and count of marks.*

```sql
SELECT city, AVG(marks) FROM Student GROUP BY city ORDER BY city ASC;
```
👉 *City-wise average marks.*

```sql
SELECT grade, COUNT(name) FROM Student GROUP BY grade ORDER BY COUNT(name) ASC;
```
👉 *Grade-wise student count.*

---

## 7. **GROUP BY with HAVING**

```sql
SELECT city, COUNT(rollno) FROM Student GROUP BY city HAVING MAX(marks) > 90;
```
👉 *Group by city but only show groups where max marks > 90.*

---

## 8. **UPDATE Queries**

```sql
UPDATE Student SET marks = 55 WHERE rollno = 105;
UPDATE Student SET grade = "C" WHERE grade = "F";
UPDATE Student SET grade = "D" WHERE marks < 60;
UPDATE Student SET marks = marks + 1;
```
👉 *Modifies specific rows, including arithmetic updates.*

---

## 9. **DELETE Queries**

```sql
DELETE FROM Student WHERE marks < 60;
```
👉 *Removes students with marks < 60.*

---

## 10. **ALTER TABLE**

```sql
ALTER TABLE Student ADD COLUMN age INT NOT NULL DEFAULT 19;
ALTER TABLE Student MODIFY age VARCHAR(3);
ALTER TABLE Student CHANGE age stud_age INT;
ALTER TABLE Student DROP COLUMN stud_age;
ALTER TABLE Student RENAME TO student_data;
ALTER TABLE student_data RENAME TO Student;
```
👉 *Used for structural changes in tables (add, modify, rename, drop columns/tables).* 

---

## 11. **TRUNCATE vs DELETE**

```sql
TRUNCATE TABLE Student;
```
👉 *Deletes all rows faster, cannot be rolled back.*

---

## 12. **Join Between Tables**

```sql
CREATE TABLE Dept (
    id INT PRIMARY KEY,
    name VARCHAR(50)
);

CREATE TABLE Teacher (
    id INT PRIMARY KEY,
    name VARCHAR(50),
    dept_id INT,
    FOREIGN KEY(dept_id) REFERENCES Dept(id)
    ON UPDATE CASCADE
    ON DELETE CASCADE
);
```
👉 *Sets up foreign key constraints with cascade options.*

```sql
SELECT t.name FROM Teacher t WHERE dept_id = 102;
```
👉 *Fetches teachers in English department.*

---

## 13. **ALTER, DELETE with Foreign Keys**

```sql
UPDATE Dept SET id = 111 WHERE id = 102;
DELETE FROM Dept WHERE id = 103;
```
👉 *Updates and deletes in Dept cascade to Teacher.*

---

## 14. **JOINS (Inner, Left, Right, Full)**

```sql
-- Tables:
CREATE TABLE Student2 (student_id INT PRIMARY KEY, name VARCHAR(50));
CREATE TABLE Course (student_id INT PRIMARY KEY, course VARCHAR(50));
```

```sql
SELECT * FROM Student2 INNER JOIN Course ON Student2.student_id = Course.student_id;
SELECT * FROM Student2 LEFT JOIN Course ON Student2.student_id = Course.student_id;
SELECT * FROM Student2 RIGHT JOIN Course ON Student2.student_id = Course.student_id;
```
👉 *Various types of joins to match or retrieve unmatched data.*

```sql
-- FULL OUTER JOIN workaround using UNION
SELECT * FROM Student2 LEFT JOIN Course ON Student2.student_id = Course.student_id
UNION
SELECT * FROM Student2 RIGHT JOIN Course ON Student2.student_id = Course.student_id;
```

---

## 15. **Find Unmatched Records (Anti Joins)**

```sql
-- Students without courses:
SELECT * FROM Student2 s LEFT JOIN Course c ON s.student_id = c.student_id WHERE c.student_id IS NULL;

-- Courses without students:
SELECT * FROM Student2 s RIGHT JOIN Course c ON s.student_id = c.student_id WHERE s.student_id IS NULL;
```

---

## 16. **Self Join (Manager - Employee)**

```sql
CREATE TABLE Employee (
    id INT PRIMARY KEY,
    name VARCHAR(50),
    manager_id INT
);

-- Find manager-employee pairs:
SELECT a.name AS manager_name, b.name FROM Employee a JOIN Employee b ON a.id = b.manager_id;
```

---

## 17. **UNION vs UNION ALL**

```sql
SELECT name FROM Employee UNION SELECT name FROM Employee;
SELECT name FROM Employee UNION ALL SELECT name FROM Employee;
```
👉 *UNION removes duplicates, UNION ALL keeps them.*

---

## 18. **Subqueries**

```sql
SELECT name, marks FROM Student WHERE marks > (SELECT AVG(marks) FROM Student);
SELECT name, rollno FROM Student WHERE rollno IN (SELECT rollno FROM Student WHERE rollno % 2 = 0);
```
👉 *Subqueries used to compute values and filter data.*

---

## 19. **Views**

```sql
CREATE VIEW view1 AS SELECT rollno, name FROM Student;
SELECT * FROM view1;
```
👉 *Views are virtual tables for simplified queries or security.*
