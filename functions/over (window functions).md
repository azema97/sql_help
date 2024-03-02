# 🪟 Window Functions

Las funciones de ventana (window functions) en SQL son funciones analíticas que operan en un conjunto de filas (ventana) definido por ciertas condiciones, como rangos o particiones, en lugar de operar en una sola fila a la vez como lo hacen las funciones agregadas tradicionales.

En Microsoft SQL Server, puedes usar funciones de ventana como `ROW_NUMBER`, `RANK`, `DENSE_RANK`, `NTILE`, `LAG`, `LEAD`, entre otras, para realizar cálculos avanzados sobre conjuntos de datos ordenados. Aquí tienes un ejemplo básico utilizando la función `ROW_NUMBER`:

Supongamos que tenemos una tabla llamada `Productos` con columnas `ID_Producto`, `Nombre`, `Precio` y queremos asignar un número de fila a cada producto basado en su precio, ordenando los productos de menor a mayor precio. Podemos hacerlo así:

```sql
SELECT 
    ID_Producto,
    Nombre,
    Precio,
    ROW_NUMBER() OVER (ORDER BY Precio) AS NumeroDeFila
FROM 
    Productos;
```

En este ejemplo, `ROW_NUMBER() OVER (ORDER BY Precio)` asignará un número de fila a cada producto según su precio, ordenando los productos de menor a mayor precio. Esto nos permite identificar el rango de cada producto en función de su precio.

---

## OVER (PARTITION BY ... ORDER BY ...)

Aquí tenemos un ejemplo de cómo usar la cláusula `PARTITION BY` en SQL Server:

Supongamos que tenemos una tabla llamada `Ventas` con columnas `ID_Venta`, `ID_Producto`, `Fecha` y `Cantidad`, y queremos calcular la suma acumulativa de las ventas para cada producto, pero reiniciando la suma para cada producto distinto. Podemos hacerlo utilizando la función `SUM` con `PARTITION BY` de la siguiente manera:

```sql
SELECT 
    ID_Venta,
    ID_Producto,
    Fecha,
    Cantidad,
    SUM(Cantidad) OVER (PARTITION BY ID_Producto ORDER BY Fecha) AS SumaAcumulativaPorProducto
FROM 
    Ventas;
```

En este ejemplo, `SUM(Cantidad) OVER (PARTITION BY ID_Producto ORDER BY Fecha)` calculará la suma acumulativa de la cantidad de ventas para cada producto, reiniciando la suma para cada producto distinto y ordenando por fecha. Esto nos permitirá ver cómo se acumula la cantidad vendida de cada producto a lo largo del tiempo.