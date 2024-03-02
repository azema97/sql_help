# NTILE()

La función `NTILE()` en SQL Server se utiliza para dividir un conjunto de datos en un número específico de grupos o baldes (tiles) basados en un orden específico. La función asigna un número de baldes a cada fila en función del número total de baldes especificado y el orden especificado.

Aquí tienes un ejemplo de cómo usar la función `NTILE()` con `PARTITION BY` en SQL Server:

Supongamos que tenemos una tabla llamada `Empleados` con columnas `ID_Empleado`, `Departamento` y `Salario`, y queremos dividir los empleados en tres grupos dentro de cada departamento basado en su salario, de modo que cada grupo tenga aproximadamente el mismo número de empleados. Podemos hacerlo así:

```sql
SELECT 
    ID_Empleado,
    Departamento,
    Salario,
    NTILE(3) OVER (PARTITION BY Departamento ORDER BY Salario) AS GrupoSalario
FROM 
    Empleados;
```

En este ejemplo, `NTILE(3) OVER (PARTITION BY Departamento ORDER BY Salario)` dividirá los empleados en tres grupos dentro de cada departamento, basándose en su salario y ordenándolos por salario dentro de cada departamento. Cada empleado recibirá un número de grupo que indica a qué grupo pertenece en función de su salario en relación con los demás empleados del mismo departamento.