# DENSE_RANK()

La función `DENSE_RANK()` en SQL Server es similar a la función `RANK()`, pero a diferencia de `RANK()`, no omite rangos cuando hay filas con el mismo valor de clasificación. En otras palabras, la función `DENSE_RANK()` asigna un rango a cada fila en un conjunto de resultados, asegurándose de que no haya brechas en los rangos cuando hay filas con el mismo valor de clasificación.

Aquí tienes un ejemplo de cómo usar la función `DENSE_RANK()` en SQL Server:

Supongamos que tenemos una tabla llamada `Estudiantes` con columnas `ID_Estudiante`, `Nombre`, `Edad` y `Puntuacion`, y queremos clasificar a los estudiantes según su puntuación en orden descendente. Podemos hacerlo así:

```sql
SELECT 
    ID_Estudiante,
    Nombre,
    Edad,
    Puntuacion,
    DENSE_RANK() OVER (ORDER BY Puntuacion DESC) AS RankingDenso
FROM 
    Estudiantes;
```

En este ejemplo, `DENSE_RANK() OVER (ORDER BY Puntuacion DESC)` asignará un rango a cada estudiante en función de su puntuación, ordenando los estudiantes de mayor a menor puntuación. Si varios estudiantes tienen la misma puntuación, se les asignará el mismo rango, pero no se saltará ningún rango, lo que significa que no habrá brechas en los rangos.