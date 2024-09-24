# LEAD()

La función `LEAD()` en SQL Server es una función de ventana que proporciona acceso a una fila en una posición específica después de la fila actual. Es decir, te permite obtener el valor de una columna en la fila siguiente al registro actual.

Por ejemplo, si tienes una tabla de ventas y quieres comparar las ventas de cada mes con las del próximo mes, puedes usar la función `LEAD()`.

Aquí tienes un ejemplo:
```sql
SELECT 
    Month, 
    Sales, 
    LEAD(Sales) OVER(ORDER BY Month) as NextMonthSales
FROM Sales
```


En este código, `LEAD(Sales) OVER(ORDER BY Month)` devuelve las ventas del próximo mes para cada fila. La cláusula `OVER(ORDER BY Month)` especifica el orden en el que se deben considerar las filas (en este caso, por mes).

Si hay alguna fila para la cual no hay ninguna fila siguiente (por ejemplo, la última fila), LEAD() devuelve NULL. Puedes proporcionar un segundo argumento a `LEAD()` para especificar un valor predeterminado en lugar de NULL en estos casos.

Por ejemplo:
```sql
SELECT 
    Month, 
    Sales, 
    LEAD(Sales, 1, 0) OVER(ORDER BY Month) as NextMonthSales
FROM Sales
```

En este código, `LEAD(Sales, 1, 0)` devolverá 0 si no hay ninguna fila siguiente.