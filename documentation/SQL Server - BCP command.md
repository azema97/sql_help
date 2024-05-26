# 📓 BCP Command

The BCP utility performs the following tasks:
- Bulk exports data from a SQL Server table into a data file.
- Bulk exports data from a query.
- Bulk imports data from a data file into a SQL Server table.
- Generates format files.

To check the BCP version execute `bcp /v` command.

---

### The BCP Utility

- When performing database maintenance you will occassionally find the need to export data out of your database tables to an operating system for storage, or conversely import data to a table from a file.
- You may need to data backup or insert data that comes from a 3rd party export.
- SQL Server 2019 makes this process simple by the **Bulk Copy Utilily** (BCP).
- It work directly at OS Level by-passing SQL Server 2019.
- Therefore, triggers are not fired, indexes are not created automatically.

---

### Use Cases

Understanding this parameters:
- `database.schema.table` 
- `out/in/queryout` 
- `-c` means it will be a character file.
- `-d` to specify the database to export/import data.
- `-P` to specify a password.
- `-t ','` specifies the delimiter, on this case a comma (,) for csv files. You could use a `\t` for a tsv file.
- `-T` means that it will use the Windows authentication to connect with SQL Server.
- `-U` is used to specify the user.
- `-S ServerName` specifies the name of the server.
- `-w` stands for "fixed-width format", and don't use a delimiter to separate the fields.

We can do the following processes:
- Export data into a .txt file from SQL Server: `bcp database.schema.table out "C:\Route\data.txt" -c -T -S ServerName`
- Import data from a .csv file into SQL Server: `bcp database.schema.table in "C:\Route\data.csv" -c -t ',' -T -S ServerName`
- Export data into a .txt file using a QUERY: `bcp "SELECT * FROM database.schema.table" queryout "C:\Route\data.txt" -S ServerName -d database -T -w`
 
🌐 NOTE: `-C 65001` is important to upload files as utf-8 file (which recognizes different special characters from many languages)