# @@SERVICENAME
Returns the name of the Registry key under which SQL Server is running. @@SERVICENAME returns 'MSSQLSERVER' if the current instance is the default; this function returns the instance name if the current instance is a named instance.

```sql
SELECT @@SERVICENAME AS 'Service Name';
```

```bash
Service Name                    
------------------------------  
MSSQLSERVER
```