1. Listar todos los archivos del directorio bin. 
   ![[Pasted image 20250327122200.png]]
2. Listar todos los archivos del directorio tmp. 
   ![[Pasted image 20250327122256.png]]
3. Listar todos los archivos del directorio etc que empiecen por t en orden inverso. 
   ![[Pasted image 20250327122514.png]]
4. Listar todos los archivos del directorio dev que empiecen por tty y tengan 5 caracteres.
   ![[Pasted image 20250327122555.png]] 
5. Listar todos los archivos del directorio dev que empiecen por tty y acaben en 1,2,3 ó 4.
   ![[Pasted image 20250327122625.png]] 
6. Listar todos los archivos del directorio dev que empiecen por t y acaben en C1. (No puedo porque no hay cotenido dentro de este fichero).
7. Listar todos los archivos, incluidos los ocultos, del directorio raíz. 
   ![[Pasted image 20250328083037.png]]
8. Listar todos los archivos del directorio etc que no empiecen por t. 
   ![[Pasted image 20250328083131.png]]
9. Listar todos los archivos del directorio usr y sus subdirectorios. 
   ![[Pasted image 20250328083255.png]]
   ![[Pasted image 20250328083313.png]]
10. Cambiarse al directorio tmp. 
    ![[Pasted image 20250328083355.png]]
11. Verificar que el directorio actual ha cambiado. 
    ![[Pasted image 20250328083424.png]]
12. Mostrar el día y la hora actual.
    ![[Pasted image 20250328083439.png]]
13. Con un solo comando posicionarse en el directorio $HOME. 
    ![[Pasted image 20250328083514.png]]
14. Verificar que se está en él. 
    ![[Pasted image 20250328083526.png]]
15. Listar todos los ficheros del directorio HOME mostrando su número de inodo. 
    ![[Pasted image 20250328083550.png]]
16. Borrar todos los archivos y directorios visibles de vuestro directorio PRUEBA. 
    ![[Pasted image 20250328083807.png]]
17. Crear los directorios dir1, dir2 y dir3 en el directorio PRUEBA. Dentro de dir1 crear el directorio dir11. Dentro del directorio dir3 crear el directorio dir31. Dentro del directorio dir31, crear los directorios dir311 y dir312. 
    ![[Pasted image 20250328083920.png]]
    ![[Pasted image 20250328083936.png]]
    ![[Pasted image 20250328084039.png]]
    ![[Pasted image 20250328084123.png]]
    
18. Copiar el archivo /etc/motd a un archivo llamado mensaje de vuestro directorio PRUEBA. 
    
    ![[Pasted image 20250401191707.png]]
    ![[Pasted image 20250401191739.png]]
19. Copiar mensaje en dir1, dir2 y dir3. 
    ![[Pasted image 20250401192428.png]]
20. Comprobar el ejercicio anterior mediante un solo comando. 
    ![[Pasted image 20250401192540.png]]
21. Copiar los archivos del directorio rc.d que se encuentra en /etc al directorio dir31. 
    ![[Pasted image 20250328084736.png]]
    ![[Pasted image 20250328084710.png]]
    ![[Pasted image 20250328084724.png]]
22. Copiar en el directorio dir311 los archivos de /bin que tengan una a como segunda letra y su nombre tenga cuatro letras. 
    ![[Pasted image 20250328084916.png]]
    
    
    ![[Pasted image 20250328084825.png]]
    ![[Pasted image 20250328084905.png]]
23. Copiar el directorio de otro usuario y sus subdirectorios debajo de dir11 (incluido el propio directorio). 
    ![[Pasted image 20250328090726.png]]
    ![[Pasted image 20250328090746.png]]
24. Mover el directorio dir31 y sus subdirectorios debajo de dir2. 
    ![[Pasted image 20250328090911.png]]
    ![[Pasted image 20250328091024.png]]
25. Mostrar por pantalla los archivos ordinarios del directorio HOME y sus subdirectorios. 
    ![[Pasted image 20250328090957.png]]
26. Ocultar el archivo mensaje del directorio dir3. 
    ![[Pasted image 20250328091312.png]]
    ![[Pasted image 20250328091408.png]]
    ![[Pasted image 20250328091340.png]]
    ![[Pasted image 20250328091545.png]]
27. Borrar los archivos y directorios de dir1, incluido el propio directorio. 
    ![[Pasted image 20250401192721.png]]
    ![[Pasted image 20250401192736.png]]
28. **Copiar a** `dir312` **los ficheros de** `/dev` **que empiecen por** `t`**, terminen en una letra** `a-b`**, y tengan cinco letras:**
    
    ![[Pasted image 20250401213557.png]]
    
    Nota: En si en esta carpeta no existe archivos con el rango rango de letras que pedimos, si lo hacemos nos dira que no existen , por esto , no le puse el rango de letras.
29. Borrar los archivos de dir312 que no acaben en b y tengan una q como cuarta letra. 
    
    ![[Pasted image 20250401213839.png]]
30. Mover el directorio dir312 debajo de dir3.
    
    ![[Pasted image 20250401214141.png]]
    
31. Crear un enlace simbólico al directorio dir1 dentro del directorio dir3 llamado enlacedir1. 
	    ![[Pasted image 20250402190052.png]]
    
32. Posicionarse en dir3 y, empleando el enlace creado en el ejercicio anterior, crear el directorio nuevo1 dentro de dir1. 
		![[Pasted image 20250402190130.png]]
    
33. Utilizando el enlace creado copiar los archivos que empiecen por u del directorio /bin en directorio nuevo1. 
	    ![[Pasted image 20250402190228.png]]
34. Crear dos enlaces duros del fichero fich1, llamarlo enlace, en los directorios dir1 y dir2. 
	    ![[Pasted image 20250402190303.png]]
35. Borrar el archivo fich1 y copiar enlace en dir3. 
    ![[Pasted image 20250402190329.png]]
36. Crear un enlace simbólico (llamado enlafich1) al fichero enlace de dir2 en dir1. 1/4 Ejercicio práctico de comandos Linux 1º de SMR 
	    ![[Pasted image 20250402190415.png]]
37. Posicionarse en dir1 y, mediante el enlace creado, copiar el archivo fichl dentro de dir311. 
	![[Pasted image 20250402190440.png]]    

38. Seguir en dir1 y, mediante el enlace creado, sacar por pantalla las líneas que tiene el archivo fich1. 
	    ![[Pasted image 20250402190514.png]]
39. Borrar el fichero fich1 de dir2 
	    ![[Pasted image 20250402190543.png]]
40. Borrar todos los archivos y directorios creados durante los ejercicios. 
    ![[Pasted image 20250402190611.png]]
41. Crear el directorio dir2 y dir3 en el directorio PRUEBA ¿Cuáles son los actuales permisos del directorio dir2? 
	    ![[Pasted image 20250402190640.png]]
42. Utilizando la notación simbólica, eliminar todos los permisos de escritura (propietario, grupo, otros) del directorio dir2. 
	    ![[Pasted image 20250402190703.png]]
43. Utilizando la notación octal, eliminar el permiso de lectura del directorio dir2, al resto de los usuarios. 
    ![[Pasted image 20250402190734.png]]
44. ¿Cuáles son ahora los permisos asociados a dir2?
	    ![[Pasted image 20250402190807.png]]
45. Crear bajo dir2, un directorio llamado dir2l. 
	    ![[Pasted image 20250402190834.png]]
46. Concederse a sí mismo permiso de escritura en el directorio dir2 e intentar de nuevo el paso anterior. 
	    ![[Pasted image 20250402190914.png]]
47. ¿Cuáles son los valores por omisión asignados a los archivos?
    
Por defecto, los permisos de archivo suelen ser:

- **Archivos:** `rw-r--r--` (644)
    
- **Directorios:** `rwxr-xr-x` (755)
    
![[Pasted image 20250402191007.png]]
Puedes verificar el comportamiento por omisión ejecutando:
48. Cambiar el directorio actual al directorio dir3. Imprimir su trayectoria completa para verificar el cambio. 
    ![[Pasted image 20250402191058.png]]
49. ¿Cuáles son los permisos asignados en su momento a este directorio? 
    ![[Pasted image 20250402191117.png]]
50. Establecer mediante el comando umask (buscar este comando) los siguientes valores por omisión: rwxr--r-- para los directorios y rw-r--r-- para los archivos ordinarios.

- **Directorios:** `rwxr--r--`
    
- **Archivos:** `rw-r--r--`
    

Primero, calcula el valor de `umask` necesario. Para estos permisos:

- **Directorios:** `777 - 744 = 033`
    
- **Archivos:** `666 - 644 = 022`
    

Entonces, configura el valor

![[Pasted image 20250402191205.png]]: