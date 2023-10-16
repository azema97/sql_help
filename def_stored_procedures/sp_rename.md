# sp_rename

Changes the name of a user-created object in the current database. This object can be a table, index, column, alias data type, or Microsoft.NET Framework common language runtime (CLR) user-defined type.

The following example renames the `TerritoryID` column in the `SalesTerritory` table to `TerrID`:
```sql
EXEC sp_rename 'Sales.SalesTerritory.TerritoryID', 'TerrID', 'COLUMN'
```