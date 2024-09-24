# FIRST_VALUE()

La función `FIRST_VALUE()` en SQL Server es una función de ventana que devuelve el primer valor de la columna seleccionada del conjunto de resultados, según el orden especificado.

Esta función puede ser útil cuando necesitas comparar el valor de una fila con el primer valor de un conjunto de filas. Por ejemplo, si tienes una tabla de ventas y quieres comparar las ventas de cada mes con las ventas del primer mes, puedes usar la función `FIRST_VALUE()`.

Aquí tienes un ejemplo:
```sql
SELECT 
    Month, 
    Sales, 
    FIRST_VALUE(Sales) OVER(ORDER BY Month) as FirstMonthSales
FROM Sales
```


En este código, `FIRST_VALUE(Sales) OVER(ORDER BY Month)` devuelve las ventas del primer mes para cada fila. La cláusula `OVER(ORDER BY Month)` especifica el orden en el que se deben considerar las filas (en este caso, por mes).

Es importante mencionar que `FIRST_VALUE()` siempre devolverá el primer valor del conjunto de resultados, independientemente de la posición de la fila actual. Si deseas obtener el primer valor dentro de un grupo específico de filas, puedes usar la cláusula `PARTITION BY` junto con `ORDER BY` en la cláusula `OVER`.

Por ejemplo:
```sql
SELECT 
    DepartmentId,
    EmployeeId, 
    Salary, 
    FIRST_VALUE(Salary) OVER(PARTITION BY DepartmentId ORDER BY Salary DESC) as HighestSalaryInDepartment
FROM Employees
```

En este código, `FIRST_VALUE(Salary) OVER(PARTITION BY DepartmentId ORDER BY Salary DESC)` devuelve el salario más alto en el mismo departamento para cada empleado.