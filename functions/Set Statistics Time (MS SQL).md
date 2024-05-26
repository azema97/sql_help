# SET STATISTICS TIME

La función `SET STATISTICS TIME` en SQL Server se utiliza para obtener información sobre el tiempo que tarda el servidor en ejecutar una consulta. Cuando activas esta opción antes de ejecutar una consulta, el servidor te proporciona estadísticas detalladas sobre el tiempo empleado en diferentes etapas de la ejecución de la consulta. Esto incluye el tiempo total transcurrido desde que se envía la solicitud hasta que se devuelve el último conjunto de resultados, así como el tiempo dedicado a la CPU y al tiempo de E/S.

Esta información puede ser útil para identificar cuellos de botella en consultas y procedimientos almacenados, ayudándote a optimizar el rendimiento de tus consultas SQL. Por ejemplo, si observas que una consulta está consumiendo mucho tiempo de CPU, podrías investigar formas de optimizarla, como agregar índices adecuados o ajustar la estructura de la consulta.

Aquí tienes un ejemplo básico de cómo usar `SET STATISTICS TIME` en SQL Server:

Supongamos que queremos obtener estadísticas de tiempo para la ejecución de una consulta simple que selecciona algunos datos de una tabla llamada `Clientes`. Primero, activamos las estadísticas de tiempo con `SET STATISTICS TIME ON`, luego ejecutamos nuestra consulta y finalmente desactivamos las estadísticas de tiempo con `SET STATISTICS TIME OFF`. Aquí está el script:

```sql
-- Activamos las estadísticas de tiempo
SET STATISTICS TIME ON;

-- Consulta que queremos medir
SELECT *
FROM Clientes
WHERE Ciudad = 'Madrid';

-- Desactivamos las estadísticas de tiempo
SET STATISTICS TIME OFF;
```


Para activar las estadísticas de tiempo, utilizas `ON`, y para desactivarlas, utilizas `OFF`. Una vez activadas, las estadísticas de tiempo se aplicarán a todas las consultas ejecutadas en la sesión actual de SQL Server hasta que se desactiven o hasta que cierre la sesión.