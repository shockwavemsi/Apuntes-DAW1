# Tipos de Datos de Fechas en SQL

- **DATE :** Almacena una fecha en el formato `YYYY-MM-DD`. Solo contiene la fecha, sin la hora.

```SQL
CREATE TABLE EjemploFecha (
	Fecha DATE	
);
```

- **TIME** : Almacena una hora del día en el formato `HH:MM:SS`. Solo contiene la hora, sin la parte de la fecha.

```SQL
CREATE TABLE Ejemplos (
	Hora TIME
);
```

- **DATE TIME :** Almacena una fecha y hora en el formato `YYYY-MM-DD` `HH:MM:SS` . Es uno de tipos de datos más comúnes.

```SQL
CREATE TABLE EjemploHora (
	FechaHora DATETIME
);
```

- **TIMESTAMP :** Similar al `DATETIME` , pero también incluye la zona horaria. Es útil para registrar eventos con precisión temporal.

```SQL
CREATE TABLE EjemploTimestamp{
	Tiempo TIMESTAMP
};
```

- **YEAR :** Almacena solo el año en formato `YYYY` . Puede ser útil para trabajar con datos que solo necesitan el año.

```SQL
CREATE TABLE EjemploAnio{
	Anio YEAR
};
```

# Funciones Comunes para Trabajar con Fechas

- **CURDATE()** o **CURRENT_DATE:** Devuelve la fecha actual.

```SQL
SELECT CURDATE();  -- o SELECT CURRENT_DATE;
```

- **CURTIME()** o **CURRENT_TIME:** Devuelve la hora actual

```SQL
SELECT CURTIME(); -- o SELECT CURRENT_TIME;
```

- **NOW()** o **CURRENT_TIMESTAMP** : Devuelve la fecha y hora actuales.

```SQL
SELECT NOW();  -- o SELECT CURRENT_TIMESTAMP;
```

- **DATE_FORMAT(fecha, formato)**: Da formato a una fecha específica según el formato indicado.

```SQL
SELECT DATE_FORMAT(NOW(), '%d/%m/%Y %H:%i:%s') AS FechaFormateada;
```

- **DATEDIFF(fecha1, fecha2)**: Devuelve la diferencia en días entre dos fechas.

```SQL
SELECT DATEDIFF('2025-12-31', '2025-01-01') AS DiferenciaDias;
```

- **DATE_ADD(fecha, INTERVAL cantidad tipo)**: Añade un intervalo a una fecha.

```SQL
SELECT DATE_ADD('2025-01-01', INTERVAL 10 DAY) AS NuevaFecha;
```

- **DATE_SUB(fecha, INTERVAL cantidad tipo)**: Sustrae un intervalo de una fecha.

```SQL
SELECT DATE_SUB('2025-01-01', INTERVAL 10 DAY) AS NuevaFecha;
```

- **EXTRACT(parte FROM fecha)**: Extrae una parte específica de una fecha (como año, mes, día, hora, etc.).

```SQL
SELECT EXTRACT(YEAR FROM NOW()) AS AnioActual;
```

# Ejemplo Práctico Sencillo

Supongamos que tienes una tabla `Pedidos` con una columna `FechaPedido` de tipo `DATETIME`. Puedes realizar varias operaciones con las fechas, como calcular la antigüedad de los pedidos:

```SQL
CREATE TABLE Pedidos (
    PedidoID INT PRIMARY KEY,
    ClienteID INT,
    FechaPedido DATETIME,
    Monto DECIMAL(10, 2)
);

INSERT INTO Pedidos (PedidoID, ClienteID, FechaPedido, Monto) VALUES
(1, 1, '2025-01-10 14:30:00', 150.00),
(2, 2, '2025-01-15 09:15:00', 200.00),
(3, 3, '2025-02-20 18:45:00', 300.00),
(4, 4, '2025-02-25 11:00:00', 250.00);

-- Calcular la antigüedad de cada pedido en días
SELECT PedidoID, 
       FechaPedido, 
       DATEDIFF(NOW(), FechaPedido) AS DiasAntiguedad
FROM Pedidos;

```

Este ejemplo devolverá la antigüedad en días de cada pedido respecto a la fecha y hora actuales.

# Ejemplos Prácticas Avanzados

- **Extraer partes específicas de una fecha:**
	- Usa `YEAR()` , `MONTH()` , y `DAY()` para obtener el año, mes y día de una columna de fecha.
	  
```SQL
SELECT EMP_NO, APELLIDO, 
		YEAR(FECHA_ALT) AS Anio, 
		MONTH(FECHA_ALT) AS Mes, 
		DAY(FECHA_ALT) AS Dia 
FROM EMP;
```

- **Calcular la diferencia entre dos fechas :**
	- Usa `TIMESTAMPDIFF()` para calcular la antigüedad en años de los empleados.
	- Usa `DATEDIFF` para calcular la  cantidad de días desde la contratación.
```SQL
SELECT EMP_NO, APELLIDO, TIMESTAMPDIFF(YEAR, FECHA_ALT, CURDATE()) AS Antiguedad FROM EMP;
SELECT EMP_NO, APELLIDO, DATEDIFF(CURDATE(), FECHA_ALT) AS DiasTrabajados FROM EMP;
```

- **Agregar intervalos de tiempo a una fecha:**
	- Usa `DATE_ADD()` para agregar intervalos de tiempo a una fecha.

```SQL

SELECT EMP_NO, APELLIDO, FECHA_ALT, DATE_ADD(FECHA_ALT, INTERVAL 1 YEAR) AS FechaMasUnAnio FROM EMP;
SELECT EMP_NO, APELLIDO, FECHA_ALT, DATE_ADD(FECHA_ALT, INTERVAL 30 DAY) AS FechaMasTreintaDias FROM EMP;

```
- Restar intervalos de tiempo a una fecha:
	- Usa `DATE_SUB` para restar intervalos de tiempo a una fecha.

```SQL

SELECT EMP_NO, APELLIDO, FECHA_ALT, DATE_SUB(FECHA_ALT, INTERVAL 6 MONTH) AS FechaMenosSeisMeses FROM EMP;

```

- Obtener el día de la semana o el nombre del mes:
	- Usa `DAYOFWEEK()` : Obtener el número del día de la semana.
	- USA `DAYNAME()` : Obtener el nombre del día.
	- USA `MONTHNAME()` : Obtener el nombre del mes.

```SQL

SELECT EMP_NO, APELLIDO, FECHA_ALT, DAYOFWEEK(FECHA_ALT) AS DiaSemana FROM EMP;
SELECT EMP_NO, APELLIDO, FECHA_ALT, DAYNAME(FECHA_ALT) AS NombreDia FROM EMP;
SELECT EMP_NO, APELLIDO, FECHA_ALT, MONTHNAME(FECHA_ALT) AS NombreMes FROM EMP;

```

- Formatear la fecha :
	- Usa `DATE_FORMAT()` para mostrar la fecha en diferentes formatos.

```SQL

SELECT EMP_NO, APELLIDO, DATE_FORMAT(FECHA_ALT, '%d-%m-%Y') AS FechaFormateada FROM EMP;
SELECT EMP_NO, APELLIDO, DATE_FORMAT(FECHA_ALT, '%M %d, %Y') AS FechaFormateada FROM EMP;

```

- Comparar fechas:
	- Usa operadores de comparación (`BETWEEN`) para comparar las fechas.

```SQL

SELECT EMP_NO, APELLIDO, FECHA_ALT FROM EMP WHERE FECHA_ALT > '1985-01-01';
SELECT EMP_NO, APELLIDO, FECHA_ALT FROM EMP WHERE FECHA_ALT BETWEEN '1981-01-01' AND '1982-12-31';

```

- Funciones de fecha y hora actuales:
	- Usa `CURDATE()` : Para obtener la fecha actual.
	- Usa `NOW` : Para obtener la fecha y hora actuales.
	- Usa `CURTIME()` : Para obtener la hora actual.

```SQL

SELECT CURDATE() AS FechaActual;
SELECT NOW() AS FechaHoraActual;
SELECT CURTIME() AS HoraActual;

```

- Último día del mes:
	- Usa `LAST_DAY()` para obtener el último día del mes de una fecha.

```SQL

SELECT EMP_NO, APELLIDO, FECHA_ALT, LAST_DAY(FECHA_ALT) AS UltimoDiaMes FROM EMP;

```

- Agrega un intervalo específico y calcular fechas futuras.
	- Usa `ADDDATE()` para calcular fechas futuras añadiendo un intervalo específico a una fecha.

```SQL

SELECT EMP_NO, APELLIDO, FECHA_ALT, ADDDATE(FECHA_ALT, INTERVAL 1 YEAR) AS ProximaRevision FROM EMP;

```

- Diferencias detallas en años,meses y días:
	- Usa `TIMESTAMPDIFF()` y `DATADIFF()` para calcular diferencias exactas en años, meses y días entre dos fechas.

```SQL

SELECT EMP_NO, APELLIDO, 
       TIMESTAMPDIFF(YEAR, FECHA_ALT, CURDATE()) AS Anios, 
       TIMESTAMPDIFF(MONTH, FECHA_ALT, CURDATE()) % 12 AS Meses, 
       DATEDIFF(CURDATE(), DATE_ADD(FECHA_ALT, INTERVAL TIMESTAMPDIFF(YEAR, FECHA_ALT, CURDATE()) YEAR)) % 30 AS Dias 
FROM EMP;

```