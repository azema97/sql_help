# Row_Number (SQL Server)

Numbers the output of a result set. More specifically, returns the sequential number of a row within a partition of a result set, starting at 1 for the first row in each partition.

ROW_NUMBER and RANK are similar. ROW_NUMBER numbers all rows sequentially (for example 1, 2, 3, 4, 5). RANK provides the same numeric value for ties (for example 1, 2, 2, 4, 5).

- NOTE: ROW_NUMBER is a temporary value calculated when the query is run. To persist numbers in a table, see IDENTITY Property and SEQUENCE.

```sql
ROW_NUMBER ( )   
    OVER ( [ PARTITION BY value_expression , ... [ n ] ] order_by_clause )
```

---

### Example

In SQL Server, the `ROW_NUMBER()` function is used to assign a unique sequential integer to each row within a partition of a result set. Here's an example of how you can use the `ROW_NUMBER()` function:

Let's say you have a table called `Employees` with the following data:

| EmployeeID | EmployeeName | Department |
|------------|--------------|------------|
| 1          | Alice        | IT         |
| 2          | Bob          | HR         |
| 3          | Charlie      | IT         |
| 4          | David        | Sales      |
| 5          | Emma         | IT         |

If you want to assign a unique row number to each employee within their respective departments, you can use the `ROW_NUMBER()` function like this:

```sql
SELECT EmployeeID, EmployeeName, Department,
       ROW_NUMBER() OVER (PARTITION BY Department ORDER BY EmployeeName) AS RowNumber
FROM Employees;
```

In this query:

- `PARTITION BY Department` divides the result set into partitions to which the `ROW_NUMBER()` function is applied. In this case, it's partitioning by the `Department` column.
- `ORDER BY EmployeeName` specifies the order in which the row numbers are assigned within each partition. Here, the row numbers are assigned based on the alphabetical order of employee names within each department.

The result of the query will be:

| EmployeeID | EmployeeName | Department | RowNumber |
|------------|--------------|------------|-----------|
| 1          | Alice        | IT         | 1         |
| 3          | Charlie      | IT         | 2         |
| 5          | Emma         | IT         | 3         |
| 2          | Bob          | HR         | 1         |
| 4          | David        | Sales      | 1         |

In this result set, the `RowNumber` column represents the unique row number assigned to each employee within their respective departments based on the alphabetical order of their names.