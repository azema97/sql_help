# 🗑️ Drop Duplicates

You can use window functions and the `ROW_NUMBER()` function to delete duplicate rows in SQL Server. Here's a general approach:

1. Use the `ROW_NUMBER()` function partitioned by the columns that you want to check for duplicates.
2. Assign a row number to each row within the partition.
3. Delete the rows where the row number is greater than 1, as those are duplicates.

Here's an example:

Suppose you have a table called `YourTable` with columns `ID`, `Column1`, `Column2`, and you want to remove duplicate rows based on the combination of `Column1` and `Column2`.

```sql
WITH CTE AS (
    SELECT *,
           ROW_NUMBER() OVER (PARTITION BY Column1, Column2 ORDER BY ID) AS RowNumber
    FROM YourTable
)
DELETE FROM CTE
WHERE RowNumber > 1;
```

Explanation:
- The `ROW_NUMBER()` function assigns a unique number to each row within the partition defined by `Column1` and `Column2`, ordered by `ID` (or any other column that you consider appropriate).
- The `CTE` (Common Table Expression) selects all columns from `YourTable` along with the row number.
- The `DELETE` statement removes rows from the CTE where the row number is greater than 1, effectively deleting duplicate rows while keeping only one instance of each unique combination of `Column1` and `Column2`.

Remember to replace `YourTable`, `Column1`, `Column2`, and `ID` with the actual table name and column names in your database. Also, ensure you have appropriate backups or safeguards in place before executing delete statements to prevent accidental data loss.