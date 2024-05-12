# 🗝️ Constraints

In SQL (Structured Query Language), **a constraint is a rule or restriction applied to a table column or a set of columns that enforces data integrity and consistency**. Constraints define certain conditions that must be met for data to be entered into or updated within a table. They help maintain the accuracy, reliability, and validity of the data stored in a database.

Here are some common types of constraints in SQL:

1. **Primary Key Constraint**: A primary key constraint uniquely identifies each record in a table. It ensures that the values in the specified column(s) are unique and not null. Only one primary key constraint can be defined for a table.

2. **Foreign Key Constraint**: A foreign key constraint establishes a relationship between two tables by enforcing referential integrity. It ensures that the values in a column (or set of columns) in one table match the values in another table's primary key or unique key column(s).

3. **Unique Constraint**: A unique constraint ensures that the values in the specified column(s) are unique across all rows in the table. Unlike a primary key constraint, multiple unique constraints can be defined for a table, and null values are allowed (except in cases where the column is also marked as NOT NULL).

4. **Check Constraint**: A check constraint defines a condition that must be true for each row in the table. It allows you to enforce domain integrity by limiting the values that can be inserted or updated in a column based on a specified condition.

5. **Not Null Constraint**: A not null constraint ensures that a column does not contain null values. It requires that every row in the table has a non-null value for the specified column.

Constraints are essential for maintaining the integrity and consistency of the data in a database and help prevent data entry errors and inconsistencies. They are specified during the creation of a table using the CREATE TABLE statement or added afterward using the ALTER TABLE statement.