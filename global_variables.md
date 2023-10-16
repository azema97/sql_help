# Global Variables (@@)

---

#### @@SERVERNAME
Returns the name of the local server that is running SQL Server.


```sql
SELECT @@SERVERNAME AS 'Server Name'
```

```bash
Server Name  
---------------------------------  
name_of_the_server
```

#### @@SERVICENAME
Returns the name of the Registry key under which SQL Server is running. @@SERVICENAME returns 'MSSQLSERVER' if the current instance is the default; this function returns the instance name if the current instance is a named instance.

```sql
SELECT @@SERVICENAME AS 'Service Name';
```

```bash
Service Name                    
------------------------------  
MSSQLSERVER
```

#### @@LANGUAGE
Returns the name of the language currently being used.

```sql
SELECT @@LANGUAGE AS 'Language Name';
```

```bash
Language Name                   
------------------------------  
us_english
```

#### @@VERSION
Returns system and build information for the current installation of SQL Server.

```sql
SELECT @@VERSION AS 'SQL Server Version';
```

```bash
SQL Server Version                   
------------------------------  
Microsoft SQL Server 2022 (RTM) - 16.0.1000.6 (X64)   Oct  8 2022 05:58:25   Copyright (C) 2022 Microsoft Corporation  Express Edition (64-bit) on Windows 10 Pro 10.0 <X64> (Build 19045: ) (Hypervisor) 
```