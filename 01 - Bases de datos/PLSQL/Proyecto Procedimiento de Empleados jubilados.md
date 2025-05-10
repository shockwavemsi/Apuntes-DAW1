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
-- Creación de tabla
```