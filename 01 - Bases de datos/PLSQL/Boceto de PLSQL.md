### **Ejercicio PL/SQL: Gestión de Clientes y Compras con Descuento**

Estás desarrollando un sistema de gestión para una tienda y necesitas implementar un procedimiento almacenado que registre la compra de un cliente, aplicando un descuento cuando corresponda.

#### **Requisitos del ejercicio:**

1. **Debe incluir una variable booleana** que indique si la compra ha sido completada con éxito y si se aplicó un descuento.
    
2. **Debe existir una variable con valor por defecto**, por ejemplo, `descuento NUMBER DEFAULT 0.05`, que represente un descuento estándar aplicado a compras mayores a 100 unidades monetarias.
    
3. **Debe manejar excepciones**, de manera que si el cliente no existe en la base de datos, se genere un error y la transacción no se realice.
    
4. **Debe afectar la columna** `total` **en la tabla** `compras`, aplicando el descuento si el monto supera el límite establecido.
    
5. **Debe realizar una llamada al procedimiento** `registrar_compra` con valores de prueba.
    

#### **Detalles adicionales:**

- La tabla `clientes` tiene las columnas `id_cliente`, `nombre` y `email`.
    
- La tabla `compras` tiene las columnas `id_compra`, `id_cliente`, `total` y `fecha_compra`.
    
- Si el cliente no existe, el procedimiento debe lanzar una excepción.
    
- Si la compra se registra correctamente, la variable booleana debe cambiar a `TRUE`.
    
- Se debe calcular el total con el descuento y almacenarlo en la tabla `compras`.

# Resolución

## **1. Creación de las tablas**

```PLSQL
CREATE TABLE clientes(
	id_cliente PRIMARY KEY,
	nombre VARCHAR2(50) NOT NULL,
	email VARCHAR2(50) NOT NULL
);

CREATE TABLE compras(
	id_compra NUMBER PRIMARY KEY,
	id_cliente NUMBER,
	total (10,2)NUMBER NOT NULL,
	fecha_compra DATE,
	FOREIGN KEY id_cliente REFERENCES clientes(id_cliente)
);
```

## **2. Creación del procedimiento almacenado**

````PLSQL
CREATE OR REPLACE PROCEDURE registrar_compra(
	-- Declaración de parametros de entrada
	r_id_cliente IN NUMBER,
	r_total IN NUMBER
) AS
	--Declaración de varibales del procedimiento
	verificamos_cliente NUMBER;
	cliente_no_existente EXCEPTION; -- Excepcion en caso de que el cliente no exista
	compra_valida BOOLEAN := FALSE; -- Varible Booleana
	total_final NUMBER; -- Aquí se guarda el total ya calculado
	descuento NUMBER DEFAULT 0.05;  -- Descuento con valor del "5%"

BEGIN
  -- Verificamos si el cliente existe
  SELECT COUNT(*) INTO verificamos_cliente FROM clientes
  WHERE id_cliente = r_id_cliente;

  IF verificamos_cliente = 0 THEN
    RAISE cliente_no_existente;
  END IF;

  -- Calculamos el total_final con el descuento
  total_final := r_total;
  IF total_final > 100 THEN
    total_final := total_final - (total_final * descuento);
    compra_valida := TRUE;
  END IF;

  -- Insertamos los datos a la base de datos
  INSERT INTO compras(id_compra, id_cliente, total, fecha_compra)
  VALUES (SEQ_COMPRAS.NEXTVAL, r_id_cliente, total_final, SYSDATE);

  -- Subimos los cambios a la base de datos
  COMMIT;

  -- Mensajes según el descuento aplicado
  IF compra_valida THEN
    DBMS_OUTPUT.PUT_LINE('Se registró la compra con descuento correctamente.');
  ELSE
    DBMS_OUTPUT.PUT_LINE('Se registró la compra sin descuento correctamente.');
  END IF;

EXCEPTION
  WHEN cliente_no_existente THEN
    DBMS_OUTPUT.PUT_LINE('Error: El cliente no está registrado.');
END;
```