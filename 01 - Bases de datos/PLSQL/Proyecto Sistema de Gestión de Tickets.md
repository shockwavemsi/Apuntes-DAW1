# CONCEPTO

Crea un procedimiento almacenado que calcule el total generado de un mes específico, este mes será un dato que lo dará el usuario

Para ello seguirás la siguiente estructura, también que habrá un expansión que veremos más adelante.

- **Facturas**
	- ID_Factura
	- Fecha
	
- **Linea_Factura**
	- N_Linea_Factura
	- Articulo
	- ID_Factura
	- Unidades
- **Devoluciones**
	- N_Linea_Factura
	- ID_Factura
	- Unidades

---

## **Expansiones**

Una vez creado terminado la primera parte, ahora crearemos una nueva tabla, con la misma estructura que la tabla `Devoluciones` que se llamará `Lineas_Facturas_Definitivas` , aquí se almacenará las filas de factura que no se devolvieron en su totalidad(*Se refiere a los restantes*).

**Ejemplo:**

Un cliente pide 3 borradores y devuelve 2, queda 1, este restante se debe almacenar en esta nueva tabla.

---
## **Ideas**

Usaremos un cursor que procese las facturas que coincidan con el mes a calcular.

```PLSQL
CURSOR SELECT * FROM factura WHERE MONTH(Fecha) = mes;
```

Luego vamos a la tabla y usamos una función agregada para calcular.

---
# SCRIPTS DEL EJERCICIO

>[!NOTE] SCRIPT DE LAS TABLAS
>```sql
>-- Tabla "Facturas"
>CREATE TABLE Facturas(
>    ID_Factura NUMBER PRIMARY KEY,
>    Fecha DATE
>);
>
>-- Tabla "Productos"
>CREATE TABLE Productos(
>    ID_Producto NUMBER PRIMARY KEY,
>    Nombre VARCHAR2(50),
>    Precio NUMBER(5,2)
>);
>
>-- Tabla "Linea_Productos"
>CREATE TABLE Linea_Productos(
>    N_Linea NUMBER,
>    ID_Factura NUMBER,
>    ID_Producto NUMBER,
>    Unidades_Pedidas NUMBER,
>    FOREIGN KEY (ID_Factura) REFERENCES Facturas(ID_Factura),
>    FOREIGN KEY (ID_Producto) REFERENCES Productos(ID_Producto),
>    PRIMARY KEY (N_Linea, ID_Factura)
>);
>
>-- Tabla "Devoluciones"
>CREATE TABLE Devoluciones(
>    N_Linea_Factura NUMBER,
>    ID_Factura NUMBER,
>    Unidades NUMBER,
>    FOREIGN KEY (N_Linea_Factura, ID_Factura) REFERENCES Linea_Productos(N_Linea, ID_Factura)
>);
>```

---
>[!IMPORTANT] PROCEDIMIENTO ALMACENADO: Calcular_total_mes
>```sql
>CREATE OR REPLACE PROCEDURE Calcular_total_mes(
>    p_mes IN VARCHAR2
>) AS
>    Total_Recaudado NUMBER(10,2); -- Total Recaudado
>    mes_no_existe EXCEPTION;
>    validar_mes NUMBER;
>BEGIN
>    -- Configurar el idioma de la sesión para asegurar que los meses se devuelvan en español
>    EXECUTE IMMEDIATE 'ALTER SESSION SET NLS_DATE_LANGUAGE = ''SPANISH''';
>
>    -- Validación de mes
>    SELECT COUNT(*) INTO validar_mes FROM Facturas f
>    WHERE TRIM(UPPER(TO_CHAR(f.Fecha, 'MONTH', 'NLS_DATE_LANGUAGE = SPANISH'))) = TRIM(UPPER(p_mes));
>
>    -- Si 'validar_mes' es 0, lanzamos una excepción
>    IF validar_mes = 0 THEN
>        RAISE mes_no_existe;
>    END IF;
>
>    -- Calcular el total recaudado
>    SELECT NVL(SUM(lp.Unidades_Pedidas * p.Precio), 0) 
>    INTO Total_Recaudado 
>    FROM Linea_Productos lp
>    INNER JOIN Facturas f ON f.ID_Factura = lp.ID_Factura
>    INNER JOIN Productos p ON p.ID_Producto = lp.ID_Producto
>    WHERE TRIM(UPPER(TO_CHAR(f.Fecha, 'MONTH', 'NLS_DATE_LANGUAGE = SPANISH'))) = TRIM(UPPER(p_mes));
>
>    -- Si no hay ventas, mostrar mensaje
>    IF Total_Recaudado = 0 THEN
>        DBMS_OUTPUT.PUT_LINE('El mes ' || p_mes || ' no tiene ventas.');
>    ELSE
>        DBMS_OUTPUT.PUT_LINE('Total recaudado para ' || p_mes || ': ' || Total_Recaudado);
>    END IF;
>
>EXCEPTION
>    WHEN mes_no_existe THEN
>        DBMS_OUTPUT.PUT_LINE('El mes ' || p_mes || ' no existe, intente con otro.');
>    WHEN OTHERS THEN
>        DBMS_OUTPUT.PUT_LINE('Ocurrió un error al calcular el total del mes: ' || SQLERRM);
>END;
>```
