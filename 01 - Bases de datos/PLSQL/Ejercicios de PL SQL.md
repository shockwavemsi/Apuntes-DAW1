# Sistema de gestión de pedidos

## Creación de la tabla

```PLSQL
CREATE TABLE pedidos (
	id_pedido NUMBER PRIMARY KEY,
	estado VARCHAR2(20) NOT NULL CHECK (estado IN ('Pendiente','Enviado'.'Entregado'))
	fecha_envio DATE
);
```

## Creación del procedimiento almacenado

```PLSQL
CREATE OR REPLACE PROCEDURE actualizar_pedido (
	--Aqui declaramos que tipos de parametros tendra nuestro procedimientos almacenado
	p_id_pedido IN NUMBER,
	p_estado IN VARCHAR2
) AS
	--Aquí declaramos las variables y excepciones que tendra nuestro programa.
	e_estado_invalido EXCEPTION; --Excepción para estado inválido
	tiene_envio BOOLEAN := FALSE; --Variable booleana
	tiempo_maximo_envio NUMBER DEFAULT 7; -- Días máximo de envío
BEGIN
	--Validación del estado
	IF p_estado NOT IN ('Pendiente','Enviado','Entregado') THEN
	RAISE e_estado_invalido;
	END IF;

	--Actualización en la tabla
	UPDATE pedidos
	SET estado = p_estado
		fecha_envio = 
		--Usaremos un case when para insertar una fecha en caso de que el pedido lo enviaron o no.
		--En caso de que este enviado insertaremos la fecha actual del sistema.
		--En caso de que no este enviado o otro "estado" le pondremos null.
		CASE
			WHEN p_estado = 'Enviado' THEN SYSDATE 
			ELSE NULL
		END
	WHERE id_pedido = p_id_pedido;

	COMMIT; --Los cambios los sube a la base de datos
	
	--Evaluar si e pedido fue enviado
	IF p_estado = 'Enviado' THEN
		tiene_envio := TRUE;
	END IF;

	--MEnsaje informativo
	IF tiene_envio THEN
		DBMS_OUTPUT.PUT_LINE('Pedido enviado correctamente.');
	ELSE
    DBMS_OUTPUT.PUT_LINE('El pedido aún no ha sido enviado.');
	END IF;

EXCEPTION
  WHEN e_estado_invalido THEN
    DBMS_OUTPUT.PUT_LINE('Error: Estado de pedido inválido.');
END;
```

# Gestión de Clientes y Compras

## Creación de las tablas

```PLSQL
CREATE TABLE clientes(
	id_cliente NUMBER PRIMARY KEY,
	nombre VARCHAR2(50) NOT NULL,
	email VARCHAR2(50) NOT NULL
);

CREATE TABLE compras(
	id_compra NUMBER PRIMARY KEY,
	id_cliente NUMBER,
	total NUMBER(10,2) NOT NULL,
	fecha_compra DATE,
	FOREIGN KEY (id_cliente) REFERENCES clientes(id_cliente)
);
```

## Procedimiento Almacenado

```PLSQL
CREATE OR REPLACE PROCEDURE registrar_compra(
	-- Declaración de los parametros de entrada
  p_id_cliente IN NUMBER,
  p_total IN NUMBER
) AS
	-- Declaración de las variables del procedimiento almacenado
  e_cliente_inexistente EXCEPTION; -- Excepción si el cliente no existe
  tiene_descuento BOOLEAN := FALSE; -- Variable booleana
  descuento NUMBER DEFAULT 0.05; -- 5% de descuento por compras mayores a 100
  v_total_final NUMBER; -- Monto final después del descuento
  v_cliente_existente NUMBER; -- Variable para verificar existencia del cliente
BEGIN
  -- Verificar si el cliente existe
  SELECT COUNT(*) INTO v_cliente_existente 
  FROM clientes 
  WHERE id_cliente = p_id_cliente;

	-- En caso de que el cliente_existente sea "0" lanzará un excepción
  IF v_cliente_existente = 0 THEN
    RAISE e_cliente_inexistente;
  END IF;

  -- Aplicar descuento si el total es mayor a 100
  v_total_final := p_total;
	  --En caso de que el total sea mayor a 100 haremos la siguiente operación
  IF p_total > 100 THEN
		--El resultado de este operación se guaradra en la "varible v_total_final".
    v_total_final := p_total - (p_total * descuento);
    tiene_descuento := TRUE;
  END IF;

  -- Insertar la compra
  INSERT INTO compras (id_compra, id_cliente, total, fecha_compra)
  VALUES (SEQ_COMPRAS.NEXTVAL, p_id_cliente, v_total_final, SYSDATE);
	
	-- Subir los cambios a la base de datos
  COMMIT;

  -- Mensajes según el descuento aplicado
  IF tiene_descuento THEN
    DBMS_OUTPUT.PUT_LINE('Compra registrada con un descuento del 5%. Total final: ' || v_total_final);
  ELSE
    DBMS_OUTPUT.PUT_LINE('Compra registrada sin descuento. Total final: ' || v_total_final);
  END IF;

EXCEPTION
  WHEN e_cliente_inexistente THEN
    DBMS_OUTPUT.PUT_LINE('Error: Cliente no registrado.');
END;
/

```

