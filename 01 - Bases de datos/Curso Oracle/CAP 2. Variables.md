# Concepto

Las variables en PL/SQL, son nombres que se le asignan a un área de almacenamiento que los programas pueden manipular.

Son los datos que utilizamos cada vez que hacemos configuraciones en la base de datos con los distintos objetos, procedimientos y funciones.

Cada variable tiene un tipo de datos específico, por medio de los tipos de datos vamos a definir la cantidad de caracteres manejan las distintas variables.

El nombre de una variable es una palabra conformada por letras, números y caracteres especiales (máximo 30 caracateres).

**Ejemplos :**

```MD
- mivarible
- mivariable2
- mi_variable
- $mivariable
- $_miVarible
```


---

## Tipos de Variables

En PL/SQL , podemos manejar variables con fechas y horas, registros, Strings, colecciones de datos, ETC.

>[!WARNING] Información para trabajar con variables
>Para trabajar con variables necesitamos habilitar la salida de script de mensajes.
>**Para ello, usaremos el siguiente código:**
>
>```PLSQL
>SET SERVEROUTPUT ON
>```
>

>[!Check] DATO IMPORTANTE:
>Cuando trabajamos con variables debemos declararlos en el bloque `declare`.
>
>```PLSQL
>DECLARE 
>--Aquí se declara las variables
>
>BEGIN
>--Aquí va nuestro programa
>END;
>```
## Tipos Básicos de Variables

- **Integer :** Variable que almacena valores enteros.

```PLSQL
DECLARE
--Aqui ejemplos de Integer
identificador integer := 50;
BEGIN
-- Aqui va el procedimiento
END;
```

>[!note] Descripción del ejemplo
>Lo que hicimos es crear un variable llamada `identificador` de tipo `integer` que le asignamos un valor número de `50`.

- **Varchar :** Variable que almacena valores alfanuméricos (ósea letras y números).

```PLSQL
DECLARE
--Aqui ejemplos de VARCHAR
nombre VARCHAR(25):='Jaren Andre';
BEGIN
-- Aqui va el procedimiento
END;
```

>[!note] Descripción del ejemplo
>Lo que hicimos , es definir que la cantidad de caracteres que tendrá `nombre` serán `25` y le declaramos estos caracteres `'Jaren Andre'`.