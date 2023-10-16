# Ntile (SQL Server)

Distributes the rows in an ordered partition into a specified number of groups. The groups are numbered, starting at one. For each row, NTILE returns the number of the group to which the row belongs.

```sql
NTILE (integer_expression) OVER ( [ <partition_by_clause> ] < order_by_clause > )
```

---

### Example

Certainly! The `NTILE()` function in SQL Server is used to divide the result set into a specified number of roughly equal-sized buckets and assigns a bucket number to each row. Here's an example of how you can use the `NTILE()` function with the `Employees` table:

| EmployeeID | EmployeeName | Department |
|------------|--------------|------------|
| 1          | Alice        | IT         |
| 2          | Bob          | HR         |
| 3          | Charlie      | IT         |
| 4          | David        | Sales      |
| 5          | Emma         | IT         |

Let's say you want to divide employees into three buckets based on their `EmployeeID` within each department. You can use the `NTILE()` function like this:

```sql
SELECT EmployeeID, EmployeeName, Department,
       NTILE(3) OVER (PARTITION BY Department ORDER BY EmployeeID) AS BucketNumber
FROM Employees;
```

In this query:

- `NTILE(3)` divides the result set into three buckets.
- `OVER (PARTITION BY Department ORDER BY EmployeeID)` specifies that the division into buckets should be done separately for each department and the order in which the buckets are assigned is based on the `EmployeeID` column.

The result of the query might look something like this:

| EmployeeID | EmployeeName | Department | BucketNumber |
|------------|--------------|------------|--------------|
| 1          | Alice        | IT         | 1            |
| 3          | Charlie      | IT         | 2            |
| 5          | Emma         | IT         | 3            |
| 2          | Bob          | HR         | 1            |
| 4          | David        | Sales      | 1            |

In this result set, the `BucketNumber` column represents the bucket to which each employee belongs within their respective departments. Employees are divided into three buckets based on their `EmployeeID` within each department.