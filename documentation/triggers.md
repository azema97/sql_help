# Triggers

Triggers in SQL Server are special types of stored procedures that automatically execute in response to certain events on a particular table or view. Here's an example of how you can create a trigger for the `Employees` table to explain how triggers work.

Let's create a trigger that automatically logs changes to the `Employees` table in a separate table called `EmployeeAuditLog`. The trigger will be fired whenever an `INSERT`, `UPDATE`, or `DELETE` operation is performed on the `Employees` table.

First, let's create the `EmployeeAuditLog` table where we will store the audit log information:

```sql
CREATE TABLE EmployeeAuditLog (
    AuditLogID INT PRIMARY KEY,
    EmployeeID INT,
    EmployeeName VARCHAR(255),
    Department VARCHAR(255),
    AuditAction VARCHAR(50),
    AuditDate DATETIME
);
```

Next, let's create the trigger:

```sql
CREATE TRIGGER trg_EmployeeChanges
ON Employees
AFTER INSERT, UPDATE, DELETE
AS
BEGIN
    SET NOCOUNT ON;

    IF (SELECT COUNT(*) FROM inserted) > 0
    BEGIN
        -- Insert audit records for INSERTED data
        INSERT INTO EmployeeAuditLog (EmployeeID, EmployeeName, Department, AuditAction, AuditDate)
        SELECT EmployeeID, EmployeeName, Department, 'INSERT', GETDATE()
        FROM inserted;
    END

    IF (SELECT COUNT(*) FROM deleted) > 0
    BEGIN
        -- Insert audit records for DELETED data
        INSERT INTO EmployeeAuditLog (EmployeeID, EmployeeName, Department, AuditAction, AuditDate)
        SELECT EmployeeID, EmployeeName, Department, 'DELETE', GETDATE()
        FROM deleted;
    END
END;
```

In this trigger:

- `AFTER INSERT, UPDATE, DELETE` specifies that the trigger will be fired after an `INSERT`, `UPDATE`, or `DELETE` operation on the `Employees` table.
- `inserted` and `deleted` are special tables in SQL Server that hold the affected rows during an `INSERT`, `UPDATE`, or `DELETE` operation.
- The trigger inserts audit log records into the `EmployeeAuditLog` table based on the data in the `inserted` and `deleted` tables, along with the type of action ('INSERT' or 'DELETE') and the current timestamp.

Now, whenever you perform an `INSERT`, `UPDATE`, or `DELETE` operation on the `Employees` table, the trigger will automatically log the changes in the `EmployeeAuditLog` table. This is a basic example of how triggers work in SQL Server, allowing you to automate actions based on changes in your database tables.