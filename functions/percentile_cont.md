# Percentile_Cont (SQL Server)

Calculates a percentile based on a continuous distribution of the column value in SQL Server. The result is interpolated and might not be equal to any of the specific values in the column.

```sql
PERCENTILE_CONT ( numeric_literal )   
    WITHIN GROUP ( ORDER BY order_by_expression [ ASC | DESC ] )  
    OVER ( [ <partition_by_clause> ] )
```

---

### Example

The `PERCENTILE_CONT()` function in SQL Server is used to calculate a specific percentile value within a group of rows. Here's an example of how you can use the `PERCENTILE_CONT()` function with the `Employees` table:

| EmployeeID | EmployeeName | Department |
|------------|--------------|------------|
| 1          | Alice        | IT         |
| 2          | Bob          | HR         |
| 3          | Charlie      | IT         |
| 4          | David        | Sales      |
| 5          | Emma         | IT         |

Let's say you want to find the 50th percentile (median) of employee IDs within each department. You can use the `PERCENTILE_CONT()` function like this:

```sql
SELECT Department,
       PERCENTILE_CONT(0.5) WITHIN GROUP (ORDER BY EmployeeID) OVER (PARTITION BY Department) AS MedianEmployeeID
FROM Employees;
```

In this query:

- `PERCENTILE_CONT(0.5)` calculates the median (50th percentile) value.
- `WITHIN GROUP (ORDER BY EmployeeID)` specifies the order in which the percentile value is calculated, in this case, it's ordered by `EmployeeID`.
- `OVER (PARTITION BY Department)` divides the result set into partitions by the `Department` column, so the percentile calculation is performed separately for each department.

The result of the query will be:

| Department | MedianEmployeeID |
|------------|------------------|
| IT         | 3                |
| HR         | 2                |
| Sales      | 4                |

In this result set, the `MedianEmployeeID` column represents the median employee ID for each department. The `PERCENTILE_CONT()` function has calculated the 50th percentile (median) employee ID within each department group.