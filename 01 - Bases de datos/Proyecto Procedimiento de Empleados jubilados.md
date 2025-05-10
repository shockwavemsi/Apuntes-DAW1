# Concepto del procedimiento

Crea un procedimiento almacenado en PL/SQL que almacene en una tabla `jubilacion` , aquellos empleados que cumplan las una de las siguientes condiciones:

- Tener más de 65 años o tener al menos 60 años y más de 35 años trabajados.

**Comportamientos del procedimiento :**

- Insertar el empleado jubilado en la tabla `jubilados`
- Borrar el empleado de la tabla `empleados` si esta en la tabla `jubilados`.

**Tablas utilizadas :**

- Empleados
- Departamentos
- Jubilados
- Periodos_de_trabajo

# Scripts

```PLSQL
-- Creación de la tabla de Empleados
CREATE TABLE EMP(
    EMP_NO NUMBER PRIMARY KEY,
    APELLIDO VARCHAR2(25),
    FECHA_NAC DATE,
    OFICIO VARCHAR2(25),
    DIR NUMBER,
    FECHA_ALT DATE,
    SALARIO NUMBER,
    COMISION NUMBER,
    DEPT_NO INT,
    FOREIGN KEY (DEPT_NO) REFERENCES DEPT(DEPT_NO)
);

-- Creación de la tabla de Departamentos
CREATE TABLE DEPT(
    DEPT_NO NUMBER PRIMARY KEY,
    DNOMBRE VARCHAR2(25),
    LOC VARCHAR2(25)
);

-- Creación de la tabla de historial_laboral
CREATE TABLE historial_laboral(
    EMP_NO NUMBER,
    FECHA_INICIO DATE,
    FECHA_FIN DATE,
    FOREIGN KEY (EMP_NO) REFERENCES EMP(EMP_NO)
);

-- Creación de la tabla de Jubilados
CREATE TABLE Jubilados(
    EMP_NO NUMBER PRIMARY KEY,
    APELLIDO VARCHAR2(25),
    FECHA_JUBLACION DATE
);

-- Insertamos datos en Departamentos
INSERT INTO DEPT VALUES(10, 'Contabilidad', 'Sevilla');
INSERT INTO DEPT VALUES(20, 'Investigación', 'Madrid');
INSERT INTO DEPT VALUES(30, 'Ventas', 'Barcelona');
INSERT INTO DEPT VALUES(40, 'Producción', 'Bilbao');

-- Insertamos datos en Empleados
INSERT INTO EMP VALUES(7369, 'SANCHEZ', 'EMPLEADO', 7902, TO_DATE('1980-12-17', 'YYYY-MM-DD'), 104000, NULL, 20);
INSERT INTO EMP VALUES(7499, 'ARROYO', 'VENDEDOR', 7698, TO_DATE('1981-02-22', 'YYYY-MM-DD'), 208000, 39000, 30);
INSERT INTO EMP VALUES(7521, 'SALA', 'VENDEDOR', 7698, TO_DATE('1981-02-22', 'YYYY-MM-DD'), 162500, 65000, 30);
INSERT INTO EMP VALUES(7566, 'JIMENEZ', 'DIRECTOR', 7839, TO_DATE('1981-04-02', 'YYYY-MM-DD'), 386750, NULL, 20);
INSERT INTO EMP VALUES(7654, 'MARTIN', 'VENDEDOR', 7698, TO_DATE('1981-09-28', 'YYYY-MM-DD'), 182000, 182000, 30);
INSERT INTO EMP VALUES(7698, 'NEGRO', 'DIRECTOR', 7839, TO_DATE('1981-05-01', 'YYYY-MM-DD'), 370500, NULL, 30);
INSERT INTO EMP VALUES(7782, 'CEREZO', 'DIRECTOR', 7839, TO_DATE('1981-06-09', 'YYYY-MM-DD'), 318500, NULL, 10);
INSERT INTO EMP VALUES(7788, 'GIL', 'ANALISTA', 7566, TO_DATE('1987-03-30', 'YYYY-MM-DD'), 390000, NULL, 20);
INSERT INTO EMP VALUES(7839, 'REY', 'PRESIDENTE', NULL, TO_DATE('1981-11-17', 'YYYY-MM-DD'), 650000, NULL, 10);
INSERT INTO EMP VALUES(7844, 'TOVAR', 'VENDEDOR', 7698, TO_DATE('1981-09-08', 'YYYY-MM-DD'), 195000, 0, 30);
INSERT INTO EMP VALUES(7876, 'ALONSO', 'EMPLEADO', 7788, TO_DATE('1987-05-03', 'YYYY-MM-DD'), 143000, NULL, 20);
INSERT INTO EMP VALUES(7900, 'JIMENO', 'EMPLEADO', 7698, TO_DATE('1981-12-03', 'YYYY-MM-DD'), 123500, NULL, 30);
INSERT INTO EMP VALUES(7902, 'FERNANDEZ', 'ANALISTA', 7566, TO_DATE('1981-12-03', 'YYYY-MM-DD'), 390000, NULL, 20);
INSERT INTO EMP VALUES(7934, 'MUÑOZ', 'EMPLEADO', 7782, TO_DATE('1982-02-23', 'YYYY-MM-DD'), 169000, NULL, 10);

```


# Procedimiento Almacenado

```PLSQL
CREATE OR REPLACE PROCEDURE gestionar_emp_jubilados
AS
    CURSOR c1 IS 
        SELECT EMP_NO, APELLIDO, FECHA_ALT, FEC, FECHA_NAC 
        FROM EMP;

    anios_trabajados NUMBER(2);
    edad_emp NUMBER(2); -- Cambiado de DATE a NUMBER(2)
    esta_jubilado NUMBER(1) := 0;

BEGIN
    FOR reg IN c1 LOOP
        -- Verificamos si el empleado ya está jubilado
        SELECT COUNT(*) INTO esta_jubilado
        FROM Jubilados
        WHERE EMP_NO = reg.EMP_NO;

        IF esta_jubilado = 0 THEN
            -- Calculamos los años trabajados
            SELECT ROUND(SUM(MONTHS_BETWEEN(fecha_salida, fecha_entrada)) / 12, 0)
            INTO anios_trabajados
            FROM historial_laboral
            WHERE EMP_NO = reg.EMP_NO;

            -- Calcular la edad del empleado
            edad_emp := ROUND(MONTHS_BETWEEN(SYSDATE, reg.FECHA_NAC) / 12, 0);

            -- Evaluamos las condiciones de la jubilación
            IF edad_emp >= 65 OR (edad_emp >= 60 AND anios_trabajados >= 35) THEN
                INSERT INTO Jubilados (EMP_NO, APELLIDO, FECHA_JUBILACION) -- Corregido el nombre de la columna
                VALUES (reg.EMP_NO, reg.APELLIDO, SYSDATE);

                DELETE FROM EMP WHERE EMP_NO = reg.EMP_NO;
            END IF;
        END IF;
    END LOOP;

    COMMIT;
END;
/

```