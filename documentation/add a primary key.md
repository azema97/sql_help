# 🗝️ Primary Key

---

### Add a primary key for an existing table
Adding a primary key to an existing table in SQL Server involves using the ALTER TABLE statement. Here's a general outline of how you can do it:

```sql
ALTER TABLE table_name
ADD CONSTRAINT constraint_name PRIMARY KEY (column_name);
```

Replace `table_name` with the name of your existing table, `constraint_name` with the name you want to give to your primary key constraint, and `column_name` with the name of the column you want to set as the primary key.

Here's an example:

Let's say you have a table called `Employees` with columns `EmployeeID`, `FirstName`, and `LastName`, and you want to set `EmployeeID` as the primary key:

```sql
ALTER TABLE Employees
ADD CONSTRAINT PK_Employees PRIMARY KEY (EmployeeID);
```

After executing this SQL statement, the `EmployeeID` column will be set as the primary key for the `Employees` table. Make sure that the column you're setting as the primary key does not contain any duplicate or NULL values, as primary keys must be unique and not null.

---

### Add a primary key on a new table

When creating a table in SQL Server, you can specify a primary key constraint as part of the table creation syntax. Here's how you can do it:

```sql
CREATE TABLE table_name (
    column1 datatype1 [NULL | NOT NULL],
    column2 datatype2 [NULL | NOT NULL],
    ...
    CONSTRAINT constraint_name PRIMARY KEY (column_name)
);
```

Replace `table_name` with the name of your new table, `constraint_name` with the name you want to give to your primary key constraint, `column_name` with the name of the column you want to set as the primary key, and `datatype1`, `datatype2`, etc., with the data types for each column.

Here's an example:

```sql
CREATE TABLE Employees (
    EmployeeID INT NOT NULL,
    FirstName VARCHAR(50),
    LastName VARCHAR(50),
    CONSTRAINT PK_Employees PRIMARY KEY (EmployeeID)
);
```

In this example, a table called `Employees` is created with columns `EmployeeID`, `FirstName`, and `LastName`, and the `EmployeeID` column is set as the primary key using the `PRIMARY KEY` constraint.