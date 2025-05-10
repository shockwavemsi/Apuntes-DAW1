# Tema 5

# MS-DOS

Es un acrónimos de Disk Operating System, creado por Microsoft, instalado en la mayoria de ordenadores y PC.

## ¿Cómo arrancar MS-DOS?

Después de arrancar el programa, aparece habitualmente `C:\>` , este también llamado "prompt", que se representa junto con el curso parpadeando `|` , indicando que puede recibir ordenes.

## Consultar versión

Escribe en seguido del símbolo `C:\>` la palabra `VER` y presiona intro.

# Cambiar de unidad 

 - El símbolo `C:\>` indica que esta la unidad "C"(del disco que se este usando).
 - Para cambiar de unidad , escribe la unidad seguido de dos puntos y pulsa intro.
   
```msdos
C:\> A:
A:\>
```

## Teclas importantes:

- Para reiniciar el ordenador , en caso de colgarse `Ctrl + Alt + Supr`
- Para detener un bucle infinito `Ctrl + c`

## Ayuda del DOS:

- Para acceder la ayuda interactiva del DOS escribe `HELP` y pulsa intro.
  
```MSDOS
C:\> HELP
```

- Para ayuda específica de una orden , escribe la orden seguido de `/?`.

```MSDOS
C:\> DIR/?
```

# Gestión de archivos:

- Los archivos tiene un nombre(máximo 8 caracteres) y una extensión.

>[!EXAMPLE] Ejemplos
>  - texto1.txt
>  - tarea.doc
>  - paginaWeb.html

>[!CAUTION] Normas en la gestión
>Evita caracteres especiales en los nombres de los archivos o con nombres vitales del sistemas.

## Visualizar el contenido de una unidad

 - Para ver los listados de archivos y carpetas de una unidad escribe `DIR`.

```MSDOS
C:\> DIR
```
- Para listar archivos con pausa ,escribe `DIR /P`.
  
```MSDOS
C:\> DIR /P
```
  
- Para listar los archivos a los ancho, escribe `DIR /W`

```MSDOS
C:\> DIR /W
```

- Para ordenar los archivos por tamaño , escribe `DIR /O:S`.

```MSDOS
C:\> DIR /O:S
```

- Para información específica de un archivo, escribe `DIR [nombre del archivo]`

```MSDOS
REM Esto es un ejemplo
C:\> DIR tarea.txt
```

## Comodines

- El Asterisco (`*`): Sustituye a un grupo de caracteres en el nombre del archivo.
- Interrogación(`?`): Sustituye a un solo carácter en el nombre del archivo.

```MSDOS
REM lista todos los archivos que tengan una extensión
C:\> DIR *.TXT 

REM Lista archivos que tengan la estructura de AUTOEXE, sin importar la última letra del nombre.
C:\> DIR AUTOEXE?.BAT
```

## Prepara un disquete para escribir información

- Si es disquete es nuevo , puede que necesites formatearlo escribe `FORMT [nombre de la unidad] :`.

```MSDOS
Rem comando para formatear un disquete
C:\> FORMAT A:
```

## Hacer un disco del sistema:

- Un disco del sistema contiene archivos necesarios para arrancar un ordenador, escribe `FORMAT [nombre de la unidad]:/S`

```MSDOS
C:\> FORMAT B:/S
```

## Recuperar información de un disquete formateado

>[!INFO] Información importante
>Solo funciona si el disquete fue formateado recientemente y no se hizo ninguna acción adicional.

- Para recuperar la información de un disco formateado, escribe `UNFORMAT [nombre de la unidad]:`.

```MSDOS
A:\> UNFORMAT A:
```

## Formatear un disquete al 100%

-  Para formatear un disquete al 100%, escriba `FORMAT [nombre de la unidad]: /U`.

```MSDOS
A:\> FORMAT C: /U
```

## Copiar un disquete:

- Utiliza la utilidad `DISKCOPY`
- Para copiar un disquete, escriba `DISKCOPY [Unidad origen]: [Unidad destino]:`.
```MSDOS
REM En este ejemplo el comando DISKCOPY, copia la información de la unidad F: y la manda a la unidad A:.

F:\> DISKCOPY F: A:
```

## Comprobación del estado de un disco:

- Utiliza la utilidad `CHKDSK`
- Para verificar el contenido y lista de fallos de un disco, escribe `CHKDSK [nombre de la unidad]: /F /V` 

```MSDOS
REM El /F corrige errores en el disco
REM El /V muestra el contenido de cada archivo.

C:\> chkdsk C: /F /V
```

## Establecer una etiqueta al disco:

- Para asignar un "título" al disco, escribe `LABEL [nombre de la unidad]: [título a poner]`.
- Para visualizar el "título" del disco: `VOL [nombre de la unida]:`.

```MSDOS
REM Comando para asignar un título
A:\> LABEL A: SOUND

REM Comando para ver el titulo del disco
A:\> VOL A:
```

## Limpiar la pantalla

- Para limpiar la pantalla , escribe `CLS`

```MSDOS
C:\> CLS
```


# Fecha y hora del sistema:

- **Cambiar la hora:**
    
    - **Comando:** `TIME`
        
    - Ejemplo: Escribe `TIME` y pulsa Intro. Introduce la hora correcta o simplemente pulsa Intro para dejarla como está.
        
- **Cambiar la fecha:**
    
    - **Comando:** `DATE`
        
    - Ejemplo: Escribe `DATE` y pulsa Intro. Introduce la fecha correcta o simplemente pulsa Intro para dejarla como está.

# Copiar ficheros:
- **Comando:** `COPY`
        
    - Ejemplo: Escribe `COPY C:\FACTURA.TXT A:FACTUR_1.TXT` y pulsa Intro para copiar un archivo y cambiarle el nombre.
        
    - Ejemplo: Escribe `COPY C:\FACTURA.TXT A:` y pulsa Intro para copiar un archivo sin cambiarle el nombre.
        
    - **Verificación:** Usa el modificador `/V` para verificar la copia (e.g., `COPY C:\FACTURA.TXT A: /V`).
        
# Mover ficheros:
  - **Comando:** `MOVE`
        
    - Ejemplo: Escribe `MOVE DIBUIX1.BMP A:` y pulsa Intro para mover un archivo.
        
    - Ejemplo: Escribe `MOVE *.BMP A:` y pulsa Intro para mover varios archivos con la extensión BMP.
        
# Comparar el contenido de dos ficheros:
    
 - **Comando:** `FC`
        
    - Ejemplo: Escribe `FC C:\NOTES.TXT A:\NOTES.TXT` y pulsa Intro para comparar dos archivos.
        
# Borrar ficheros:
    
- **Comando:** `DEL`
        
    - Ejemplo: Escribe `DEL C:\AMICS.TXT` y pulsa Intro para borrar un archivo.
        
# Recuperar archivos borrados:
    
- **Comando:** `UNDELETE`
        
    - Ejemplo: Escribe `UNDELETE C:\AMICS.TXT` y pulsa Intro para intentar recuperar un archivo borrado.
        
# Renombrar ficheros:
    
- **Comando:** `REN`
        
    - Ejemplo: Escribe `REN WEB.HTM PERSONAL.HTM` y pulsa Intro para renombrar un archivo.

# Directorios

- **Creación de directorios:**
    
    - **Comando:** `MD`
        
    - Ejemplo: Escribe `MD APUNTS` y pulsa Intro para crear un directorio llamado APUNTS.
        
# Cambiar de directorio:
    
- **Comando:** `CD`
        
    - Ejemplo: Escribe `CD APUNTS` y pulsa Intro para cambiar al directorio APUNTS.
        
    - Ejemplo: Escribe `CD..` y pulsa Intro para volver al directorio padre.
        
# Estructura del árbol de directorios:**
    
 - **Comando:** `TREE`
        
    - Ejemplo: Escribe `TREE` y pulsa Intro para obtener un listado de los directorios y subdirectorios.
        
# Mover o copiar información entre directorios:**
    
- **Copiar archivos:**
        
    - **Comando:** `COPY`
            
    - Ejemplo: Escribe `COPY A:\ART.TXT C:\APUNTS\HISTORIA` y pulsa Intro para copiar un archivo.
            
- **Mover archivos:**
        
     - **Comando:** `MOVE`
            
    - Ejemplo: Escribe `MOVE A:\ART.TXT C:\APUNTS\HISTORIA` y pulsa Intro para mover un archivo.
            
## Borrar directorios:
    
 - **Comando:** `DELTREE`
        
    - Ejemplo: Escribe `DELTREE C:\APUNTS` y pulsa Intro para borrar todo un directorio (incluidos sus subdirectorios y archivos interiores).
        
# Edición de archivos:
    
- **Comando:** `EDIT`
        
    - Ejemplo: Escribe `EDIT` y pulsa Intro para entrar al editor del DOS.