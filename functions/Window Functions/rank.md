# RANK()

La función `RANK()` en SQL Server es una función de ventana que asigna un rango a cada fila dentro de un conjunto de resultados, basándose en el orden especificado. Si varias filas tienen el mismo valor de clasificación, se les asigna el mismo rango, y el siguiente rango disponible se salta en función del número de filas con el mismo valor de clasificación.

Aquí tienes un ejemplo de cómo usar la función `RANK()` en SQL Server:

Supongamos que tenemos una tabla llamada `Estudiantes` con columnas `ID_Estudiante`, `Nombre`, `Edad` y `Puntuacion`, y queremos clasificar a los estudiantes según su puntuación en orden descendente. Podemos hacerlo así:

```sql
SELECT 
    ID_Estudiante,
    Nombre,
    Edad,
    Puntuacion,
    RANK() OVER (ORDER BY Puntuacion DESC) AS Ranking
FROM 
    Estudiantes;
```

En este ejemplo, `RANK() OVER (ORDER BY Puntuacion DESC)` asignará un rango a cada estudiante en función de su puntuación, ordenando los estudiantes de mayor a menor puntuación. Si varios estudiantes tienen la misma puntuación, se les asignará el mismo rango y el siguiente rango disponible se saltará.