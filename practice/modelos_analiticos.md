# ETL en SQL (modelos analíticos)

Crear una tabla llamada clientes con las siguientes columnas: id_empleado, nombre, apellido y departamento.
```sql
CREATE TABLE clients(
    id_empleado INT,
    nombre VARCHAR(40),
    apellido VARCHAR(40),
    departamento VARCHAR(40),
    PRIMARY KEY (id_empleado)
);
```

Insertar datos en las tabla.
```sql
INSERT INTO empleados (id_empleado,nombre,apellido,departamento)
VALUES (1, 'Juan', 'Pérez', 'Ventas'),
       (2, 'Ana', 'García', 'Finanzas'),
       (3, 'Luis', 'Martínez', 'Marketing'),
       (4, 'Sofía', 'Rodríguez', 'Ventas'),
       (5, 'Juan', 'Pérez', 'Ventas');
```

Crear un código para identificar datos duplicados.
```sql
SELECT nombre, apellido, departamento, COUNT(*)
FROM empleados
GROUP BY nombre, apellido, departamento
HAVING COUNT(*) > 1;
```

Opción 1: Eliminar registros duplicados utilizando ROW_NUMBER().
```sql
WITH tabla_cte AS (
  SELECT *, ROW_NUMBER() OVER (PARTITION BY nombre, apellido, departamento ORDER BY id_empleado) AS fila_numero
  FROM empleados
  )
  DELETE FROM tabla_cte
WHERE fila_numero > 1;
```

Opción 2: Eliminar registros duplicados con la cláusula DELETE y JOIN.
```sql
DELETE e1
FROM empleados e1   --intersección del conjunto empleados
INNER JOIN empleados e2
ON e1.nombre = e2.nombre AND e1.apellido = e2.apellido AND e1.departamento = e2.departamento
WHERE e1.id_empleado < e2.id_empleado; --criterio para decidir cuál de los registros duplicados debe eliminarse
```