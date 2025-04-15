1. Add a New Column to a Table

ALTER TABLE workers ADD joining_date DATETIME;

Explanation:
This command adds a new column named joining_date to the workers table.

DATETIME is a data type used to store both date and time (e.g., 2021-02-11 00:00:00).

Initially, all existing rows will have NULL in the new column because no values are set yet.

2. View Table Data

SELECT * FROM workers;
Explanation:
This command retrieves all columns and rows from the workers table.
It is used to verify that the column was successfully added and to view current data.

1. Update Data in a Table
sql
Copy
Edit
UPDATE workers SET joining_date = '2021-02-11' WHERE workers_id = 1;
UPDATE workers SET joining_date = '2020-03-10' WHERE workers_id = 2;
UPDATE workers SET joining_date = '2010-04-20' WHERE workers_id = 3;
Explanation:
These commands update the joining_date field for specific rows in the table based on the workers_id.

SET is used to assign a new value to a column.

WHERE ensures only the specific row is updated.
Without WHERE, all rows would be updated.

4. View Updated Table
sql
Copy
Edit
SELECT * FROM workers;
Explanation:
This command is used again to confirm that the joining_date column was successfully updated with the new values.

5. Remove a Column from a Table
sql
Copy
Edit
ALTER TABLE workers DROP joining_date;
Explanation:
This command removes the joining_date column from the table permanently.

Once a column is dropped, all data in it is lost.

Use this carefully, especially in real projects.

6. Verify Table After Column Deletion
sql
Copy
Edit
SELECT * FROM workers;
Explanation:
Used to confirm that the joining_date column has been removed and the table structure is back to the original state.

✅ Summary of Concepts Practiced

Command	Purpose
ALTER TABLE ADD	Add a new column
UPDATE	Change values in specific rows
SELECT *	View entire table
ALTER TABLE DROP	Remove a column from the table