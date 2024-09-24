# LAG()

La función `LAG()` en SQL Server es una función de ventana que se utiliza para acceder a los datos de una fila anterior sin tener que hacer una auto-unión. Es decir, te permite obtener el valor de una columna en la fila anterior al registro actual.

Por ejemplo, si tienes una tabla de ventas y quieres comparar las ventas de cada mes con las del mes anterior, puedes usar la función `LAG()`.

Aquí tienes un ejemplo:
```sql
SELECT 
    Month, 
    Sales, 
    LAG(Sales) OVER(ORDER BY Month) as PreviousMonthSales
FROM Sales
```


En este código, `LAG(Sales) OVER(ORDER BY Month)` devuelve las ventas del mes anterior para cada fila. La cláusula `OVER(ORDER BY Month)` especifica el orden en el que se deben considerar las filas (en este caso, por mes).

Si hay alguna fila para la cual no hay ninguna fila anterior (por ejemplo, la primera fila), `LAG()` devuelve NULL. Puedes proporcionar un segundo argumento a `LAG()` para especificar un valor predeterminado en lugar de NULL en estos casos.

Por ejemplo:

```sql
SELECT 
    Month, 
    Sales, 
    LAG(Sales, 1, 0) OVER(ORDER BY Month) as PreviousMonthSales
FROM Sales
```

En este código, `LAG(Sales, 1, 0)` devolverá 0 si no hay ninguna fila anterior.