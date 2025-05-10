Es una área donde se ubica toda la codificación compleja de un programa **PL/SQL**

Se entiende como , que toda la codificación se coloca en un bloque PL/SQL

Los bloques están definidos por cuatro palabras clave.

- **DECLARE (Sección declarativa) :** Dentro de este se colocan las sentencias, variables, constantes y otros elementos de código.
  Que pueden ser re-utilizados dentro del propio bloque.
- **BEGIN (Sección Ejecutable) :** Dentro se colocan las sentencias que se ejecutaran cuando se ejecute el bloque.
  
>[!info] Punto Importante:
>Aquí se se ubica las instrucciones más importantes que realizara un programa.
  
- **EXCEPTION (Sección de manejo de Excepciones/Errores/Situaciones) :** Es especialmente estructurada para atrapar y manejar cualquier excepción, que se produzca durante la ejecución del `BEGIN` . 
  
>[!info] Punto importante
>Dependiendo de la instrucciones que se le manden al `BEGIN`, si devuelve algo que no se ejecuta según lo que defina el `BEGIN`, eso se maneja en el `EXCEPTION` (sean errores o también que no se encuentren datos).
  
- **END(Final del programa) :** Define el final de nuestro programa

---

>[!check] Un dato interesante:
>El `BEGIN` es obligatorio dentro de un programa de PL/SQL, por otro , no es necesario `DECLARE` y `EXCEPTION`, si no se utilizarán dentro del programa.

# Tipos de Bloque de PL/SQL

## Bloque Anónimos

- Se construyen de forma dinámica y se ejecutan una sola vez.
- No tiene nombre

```PLSQL
BEGIN

--Aqui va el programa

END; 
--Aquí los termina
```

## Bloques con nombres

- Son bloques con nombre, que al igual de que los anónimos se construyen generalmente, de forma dinámica y se ejecutan una sola vez.

```PLSQL
--Ejemplo queda pendiente
```  

# Disparadores(Triggers)

Son bloques con nombre que se almacenan en la base de datos.

Tampoco suelen cambiar después de su construcción y se ejecutan varias veces.

