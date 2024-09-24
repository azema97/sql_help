# LAST_VALUE()

La función `LAST_VALUE()` en SQL Server es una función de ventana que devuelve el último valor de la columna seleccionada del conjunto de resultados, según el orden especificado.

Esta función puede ser útil cuando necesitas comparar el valor de una fila con el último valor de un conjunto de filas. Por ejemplo, si tienes una tabla de ventas y quieres comparar las ventas de cada mes con las ventas del último mes, puedes usar la función `LAST_VALUE()`.

Aquí tienes un ejemplo:

```sql
SELECT 
    Month, 
    Sales, 
    LAST_VALUE(Sales) OVER(ORDER BY Month) as LastMonthSales
FROM Sales
```

En este código, `LAST_VALUE(Sales) OVER(ORDER BY Month)` devuelve las ventas del último mes para cada fila. La cláusula `OVER(ORDER BY Month)` especifica el orden en el que se deben considerar las filas (en este caso, por mes).

Es importante mencionar que, a menos que se especifique lo contrario con las cláusulas `ROWS/RANGE`, `LAST_VALUE()` considerará todas las filas desde el inicio hasta el final del conjunto de resultados (o partición), lo que puede dar resultados inesperados debido al comportamiento predeterminado de las ventanas de cuadros. Para obtener el último valor dentro de cada partición como se esperaría intuitivamente, se debe usar `ROWS BETWEEN CURRENT ROW AND UNBOUNDED FOLLOWING`.

Por ejemplo:
```sql
SELECT 
    DepartmentId,
    EmployeeId, 
    Salary, 
    LAST_VALUE(Salary) OVER(PARTITION BY DepartmentId ORDER BY Salary ROWS BETWEEN CURRENT ROW AND UNBOUNDED FOLLOWING) as LowestSalaryInDepartment
FROM Employees
```


En este código, `LAST_VALUE(Salary) OVER(PARTITION BY DepartmentId ORDER BY Salary ROWS BETWEEN CURRENT ROW AND UNBOUNDED FOLLOWING)` devuelve el salario más bajo en el mismo departamento para cada empleado.