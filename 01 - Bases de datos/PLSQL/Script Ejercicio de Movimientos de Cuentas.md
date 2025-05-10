1. **Creación de la tablas:**
   
```PLSQL
-- Creación de la tabla de cuentas
CREATE TABLE cuentas(
	id_cuenta NUMBER(10) PRIMARY KEY,
	BAL NUMBER(10) CHECK (BAL >= 0) -- Restricción: "BAL" no almacenará numero negativos.
);

CREATE TABLE movimientos(
	id_cuenta NUMBER(10),
	--o VARCHAR2(1) CHECK (o IN ('u','i','d')),
	opert_type VARCHAR2(1),
	nuevo_valor NUMBER(10) CHECK (nuevo_valor >= 0),
	estado VARCHAR2(50),
	fecha_operación DATE
);
```

2. **Inserción de los datos**

```PLSQL
-- Insertamos Datos a la tabla cuentas
INSERT INTO cuentas VALUES(1,1000);
INSERT INTO cuentas VALUES(2,2000);
INSERT INTO cuentas VALUES(3,1500);
INSERT INTO cuentas VALUES(4,6500);
INSERT INTO cuentas VALUES(5,500);

-- Insertamos Datos a la tabla movimientos
INSERT INTO movimientos VALUES (3,'u',599,NULL,SYSDATE);
INSERT INTO movimientos VALUES (6,'i',20099,NULL,SYSDATE);
INSERT INTO movimientos VALUES (5,'d',NULL,NULL,SYSDATE);
INSERT INTO movimientos VALUES (7,'u',1599,NULL,SYSDATE);
INSERT INTO movimientos VALUES (1,'i',399,NULL,SYSDATE);
INSERT INTO movimientos VALUES (9,'d',NULL,NULL,SYSDATE);
INSERT INTO movimientos VALUES (10,'x',NULL,NULL,SYSDATE);
```

3. **Creación del procedimiento almacenado**

- Procedimiento Original
```PLSQL
DECLARE
    CURSOR c1 IS 
        SELECT id_cuenta, oper_type, nuevo_valor 
        FROM movimientos
        ORDER BY fecha_operacion
        FOR UPDATE OF estado;

BEGIN
    FOR reg IN c1 LOOP
        reg.v_oper_type := UPPER(reg.v_oper_type);

        -- En caso de que "reg.v_oper_type" sea igual a 'U', actualizamos
        IF reg.v_oper_type = 'U' THEN
            UPDATE cuentas 
            SET BAL = reg.nuevo_valor
            WHERE id_cuenta = reg.id_cuenta;
        
            -- Si no se actualiza nada, insertamos los valores
            IF SQL%NOTFOUND THEN
                INSERT INTO cuentas VALUES (reg.id_cuenta, reg.nuevo_valor);
                UPDATE movimientos 
                SET estado = 'Actualizar: ID no encontrado. Valores insertados'
                WHERE CURRENT OF c1;
            END IF;

        -- Si se confirma la actualización, también actualizamos "estado".
        ELSE 
            UPDATE movimientos 
            SET estado = 'Actualizar: Confirmado..'
            WHERE CURRENT OF c1;
        END IF;

        -- En caso de que "reg.v_oper_type" sea igual a 'I', insertamos
        ELSIF reg.oper_type = 'I' THEN
            BEGIN
                INSERT INTO cuentas VALUES (reg.id_cuenta, reg.nuevo_valor);
                UPDATE movimientos 
                SET estado = 'Insertar: Confirmado..'
                WHERE CURRENT OF c1;
            EXCEPTION
                WHEN DUP_VAL_ON_INDEX THEN
                    UPDATE cuentas 
                    SET BAL = reg.nuevo_valor
                    WHERE id_cuenta = reg.id_cuenta;

                    UPDATE movimientos 
                    SET estado = 'Insertar: ID existente. Actualizamos valores'
                    WHERE CURRENT OF c1; 
            END;

        -- En caso de que "reg.v_oper_type" sea igual a 'D', borraremos.
        ELSIF reg.oper_type = 'D' THEN
            DELETE FROM cuentas 
            WHERE id_cuenta = reg.id_cuenta;

            -- Si no se borra nada, actualizamos estado con "ID no encontrado"
            IF SQL%NOTFOUND THEN 
                UPDATE movimientos 
                SET estado = 'Borrar: ID no encontrado'
                WHERE CURRENT OF c1;
            ELSE 
                -- Si se confirma el borrado, también actualizamos "estado"
                UPDATE movimientos 
                SET estado = 'Borrar: Confirmado..'
                WHERE CURRENT OF c1;    
            END IF;
        END IF;
    END LOOP;

    COMMIT;
END;

```

- Procedimiento alterado con al IA

```PLSQL

```

```PLSQL
DECLARE
 n_cuenta NUMBER (2) := 6;
 fila cuentas%rowtype;
BEGIN
 SELECT * INTO fila
 FROM cuentas
 WHERE id_cuenta = n_cuenta;

 DBMS_OUTPUT.PUT_LINE('Información de la cuenta ');
 DBMS_OUTPUT.PUT_LINE('Nº de cuenta : ' || n_cuenta);
 DBMS_OUTPUT.PUT_LINE('Saldo de la cuenta :' || fila.BAL);

EXCEPTION
	WHEN others THEN
	DBMS_OUTPUT.PUT_LINE('La cuenta no existe');
END;
```

- Antes:
	- ![[Pasted image 20250422095528.png]]
- Despues: