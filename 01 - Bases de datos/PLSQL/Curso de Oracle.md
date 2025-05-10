# Comprender las Características Principales de PL/SQL

Para familiarizarnos con PL/SQL este ejemplo:

Este programa procesa un pedido de una raqueta de tenis.

1. Declara una variable de tipo `ǸUMBER` para almacenar la cantidad de raquetas de tenis en mano.
2. Después , recupera la cantidad disponible de una tabla de base de datos llamada `inventory`.
	1. Si la cantidad es mayor a cero, el programa actualiza la tabla e inserta un registro de compra en otra tabla con nombre `purchase_record`.
	2. En caso contrario, el programa inserta un registro fuera de stock en el `purchase_record` mesa.

```PLSQL
-- disponible en línea en el archivo 'examp1'
DECLARE
	qty_on_hand NUMBER(5);

BEGIN
	SELECT quantity INTO qty_on_hand FROM inventory
		WHERE product = 'TENNINS RACKET'
			FOR UPDATE OF quantity;
	IF qty_on_hand > 0 THEN
		UPDATE inventory SET quantity = quantity - 1  -- Comprobar cantidad
			WHERE producto = 'TENNIS RACKET';
		INSERT INTO purchase_record
			VALUES('Tennis racket purchased',SYSDATE);
	ELSE
		INSERT INTO purchase_record
			VALUES('Out of tennis rackets',SYSDATE);
	END IF;
	COMMIT;
END;
```

✅ Con PL/SQL podemos tenemos podemos hacer varias funciones como:

 - Podemos usar sentencias SQL para manipular datos de Oracle y sentencias de flujo de control para procesar los datos.
- También podemos declarar constantes y variables
- Definir procedimientos y funciones
- Atrapar errores de tiempo de ejecución
- Atrapar excepciones
- Entre muchas otras cosas

En resumen, nos da la posibilidad de combinar el poder de manipulación de datos SQL con el poder de procesamiento de datos de los lenguajes de procedimiento.

# Estructura de bloque

PL/SQL es un lenguaje de programación estructurado en bloques lógicos, que pueden contener subbloques anidados. Este enfoque facilita la resolución de problemas dividiéndolos en partes más pequeñas. Cada bloque agrupa declaraciones relacionadas, que dejan de existir al completarse. Un bloque PL/SQL consta de tres partes: declarativa, ejecutable y manejo de excepciones, siendo la ejecutable la única obligatoria.