# ROW_NUMBER()

La función `ROW_NUMBER()` en SQL Server asigna un número de fila único a cada fila dentro de un conjunto de resultados, de acuerdo con el orden especificado. A diferencia de las funciones `RANK()` y `DENSE_RANK()`, `ROW_NUMBER()` no maneja empates, cada fila recibirá un número de fila único incluso si hay filas con los mismos valores de clasificación.

Aquí tienes un ejemplo de cómo usar la función `ROW_NUMBER()` con `PARTITION BY` en SQL Server:

Supongamos que tenemos una tabla llamada `Empleados` con columnas `ID_Empleado`, `Departamento`, `Nombre` y `Salario`, y queremos asignar un número de fila a cada empleado dentro de cada departamento, ordenando por salario de manera descendente. Podemos hacerlo así:

```sql
SELECT 
    ID_Empleado,
    Departamento,
    Nombre,
    Salario,
    ROW_NUMBER() OVER (PARTITION BY Departamento ORDER BY Salario DESC) AS NumeroDeFilaPorDepartamento
FROM 
    Empleados;
```

En este ejemplo, `ROW_NUMBER() OVER (PARTITION BY Departamento ORDER BY Salario DESC)` asignará un número de fila único a cada empleado dentro de cada departamento, ordenando los empleados por salario de manera descendente. Cada empleado obtendrá un número de fila único dentro de su departamento.