# Update

The UPDATE statement is used to modify the existing records in a table.

```sql
UPDATE table_name
SET column1 = value1, column2 = value2, ...
WHERE condition;
```

The following SQL statement will update the ContactName to "Juan" for all records where country is "Mexico":
```sql
UPDATE Customers
SET ContactName='Juan'
WHERE Country='Mexico';
```

Source: https://www.w3schools.com/sql/sql_update.asp