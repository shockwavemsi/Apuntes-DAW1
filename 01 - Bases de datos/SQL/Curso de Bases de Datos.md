# 1. El lenguaje de DDL de SQL

![[Pasted image 20250204202238.png]]

El **DDL** (_Data Definition Language_) o **Lenguaje de Definición de Datos** es la parte de SQL dedicada a la definición de los datos. Las sentencias **DDL** son las siguientes:

- `CREATE`: se utiliza para crear objetos como bases de datos, tablas, vistas, índices, _triggers_ y procedimientos almacenados.
- `DROP`: se utiliza para eliminar los objetos de la base de datos.
- `ALTER`: se utiliza para modificar los objetos de la base de datos.
- `SHOW`: se utiliza para consultar los objetos de la base de datos.

Otras sentencias de utilidad que usaremos en esta unidad son:

- `USE`: se utiliza para indicar la base de datos con la que queremos trabajar.
- `DESCRIBE`: se utiliza para mostrar información sobre la estructura de una tabla.
# Creación de base de datos

```SQL
CREATE {DATABASE | SCHEMA} [IF NOT EXIXTS] nombre_base_datos;
```

- `DATABASE`  y `SCHEMA` son sinónimos
- `IF NOT EXISTS` crea la base de datos si no existe una base de datos con el mismo nombre.

>[!EXAMPLE] Ejemplo
>Si no especificamos el set de caracteres en la creación de la base de datos , se usará `latin1` por defecto.
>
>```SQL
>CREATE DATABASE nombre_base_datos;
>```
>
>```SQL
>CREATE DATABASE nombre_base_datos CHARACTER SET utf8;
>```

El **contejamiento** , es le criterio que vamos a utilizar para ordenar las cadenas de caracteres de la base de datos. Si no especificamos , por defecto, se usará el que set de caracteres asignado. 

>[!EXAMPLE] Ejemplo
>Para el set de caracteres `utf8` se usa `utf8_general_ci`.
>Este ejemplo demuestra como especificar cotejamiento de forma explícita:
>```SQL
>CREATE DATABASE nombre_base_datos CHARACTER SET utf8 COLLATE `utf8_general_ci`;
>```

# CHARACTER SET y COLLATE

- `CHARACTER SET` : Especifica el set de caracteres que vamos utilizar en la base de datos.
- `COLLATE` : Especifica el tipo de cotejamiento que vamos a utilizar en la base de datos. Indica el criterio que vamos a seguir para ordenar las cadenas de caracteres.

Para ver los set de caracteres que tenemos disponibles :

```SQL
SHOW CARACTER SET;
```

Para consultar qué tipo de cotejamiento hay disponibles para usar :

```SQL
SHOW COLLATION;
```

Para hacer una consulta más especifica sobre los tipos de cotejamiento que podemos usar con `utf8` :

```SQL
SHOW COLLATION LIKE `utf8`;
```

El cotejamiento puede ser:

- case-sensitive (_cs): Los caracteres `a` y `A` son diferentes.
- case-insensitive (_ci): Los caracteres `a` y `A` son iguales.
- binary (_bin): Dos caracteres son iguales si los valores de su representación numérica son iguales.

Para consultar qué set de caracteres y qué cotejamiento está utilizando una determinada base de datos podemos consultar el valor de las variables `character_set_database` y `collation_database`.

En primer lugar seleccionamos la base de datos con la que vamos a trabajar.

```
USE database;
```

Y una vez seleccionada, consultamos el valor de las variables `character_set_database` y `collation_database`.

```
SELECT @@character_set_database, @@collation_database;
```

### 2.1.4 Ejemplo de cómo afecta el cotejamiento al ordenar una tabla

Suponemos que tenemos una tabla que contiene cadenas de caracteres codificadas en `latin1`.

```SQL
CREATE TABLE t (c CHAR(3) CHARACTER SET latin1);

INSERT INTO t (c) VALUES('AAA'),('bbb'),('aaa'),('BBB');

SELECT c FROM t;
+------+
| c    |
+------+
| AAA  |
| bbb  |
| aaa  |
| BBB  |
+------+
```

Ahora vamos a obtener los registros de la tabla aplicando diferentes tipos de cotejamiento:

- Cotejamiento **case-sensitive** (los caracteres `a` y `A` son diferentes).

```SQL
SELECT c FROM t ORDER BY c COLLATE latin1_general_cs;
+------+
| c    |
+------+
| AAA  |
| aaa  |
| BBB  |
| bbb  |
+------+
```

- Cotejamiento **case-insensitive** (los caracteres `a` y `A` son iguales).

```SQL
SELECT c FROM t ORDER BY c COLLATE latin1_swedish_ci;
+------+
| c    |
+------+
| AAA  |
| aaa  |
| bbb  |
| BBB  |
+------+
```

- Cotejamiento **binary** (dos caracteres son iguales si los valores de su representación numérica son iguales).

```SQL
SELECT c FROM t ORDER BY c COLLATE latin1_bin;
+------+
| c    |
+------+
| AAA  |
| BBB  |
| aaa  |
| bbb  |
+------+
```