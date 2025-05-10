51. Crear cuatro nuevos directorios
    ![[Pasted image 20250413152448.png]]
52. Comprobar los permisos de acceso de los directorios recién creados para comprobar el funcionamiento del comando umask.
    ![[Pasted image 20250413152515.png]]
53. Crear el fichero uno . Quitarle todos los permisos de lectura. Comprobarlo. Intentar borrar dicho fichero.
    ![[Pasted image 20250413152718.png]]
54. Quitarle todos los permisos de paso al directorio dir2 y otorgarle todos los demás.
  ![[Pasted image 20250413172203.png]]
55. Crear en el directorio propio:
	1. El directorio carpeta1 con los tres permisos para el propietario, dentro de él fich1 con lectura y escritura para todos y fich2 con lectura y escritura para el propietario y solo lectura para el resto.
	   ![[Pasted image 20250413172415.png]]
	2. El directorio carpeta2 con todos los permisos para el propietario y lectura y ejecución para los del mismo grupo. Dentro file1 con lectura y escritura para el propietario y los del grupo y file2 con los mismos para el propietario y solo lectura para el grupo.
	   ![[Pasted image 20250413172641.png]]
56. Desde otro usuario probar todas las operaciones que se pueden hacer en los ficheros y directorios creados.
    ![[Pasted image 20250413173245.png]]
57. Visualizar la trayectoria completa del directorio actual. Crear dos directorios llamados correo y fuentes debajo del directorio actual.
    ![[Pasted image 20250413174016.png]]
58. Posicionarse en el directorio fuentes y crear los directorios dir1, dir2, dir3.
    ![[Pasted image 20250413174100.png]]
59. Crear el directorio menus bajo correo sin moverse del directorio actual.
    ![[Pasted image 20250413174258.png]]
60. Posicionarse en el directorio HOME. Borrar los directorios que cuelgan de fuentes que acaben en un número que no sea el 1.
    ![[Pasted image 20250413174551.png]]
61. Ver si existe el archivo tty2 en el directorio dev. En caso de que exista, ver su fecha de creación o actualización.
    ![[Pasted image 20250413174634.png]]
62. Ver los permisos que tienen los archivos que empiecen por tt del directorio /dev.
    ![[Pasted image 20250413174826.png]]
63. Visualizar la lista de los archivos ordinarios que están en el directorio /usr/bin.
    ![[Pasted image 20250413174955.png]]
64. Visualizar la lista de todos los directorios que cuelgan del raíz.
    ![[Pasted image 20250413175113.png]]
65. Visualizar la lista de todos los ficheros que pertenezcan a root.
    ![[Pasted image 20250413175222.png]]
66. Visualizar la lista de todos los ficheros .h del directorio /usr/include.
    ![[Pasted image 20250413175350.png]]
67. Ejecutar todos los comandos que empiecen por ls del directorio /bin.
    ![[Pasted image 20250413175449.png]]
68. Visualizar de qué tipo son todos y cada uno de ficheros de todo el árbol del sistema propiedad de un usuario conocido.
    ![[Pasted image 20250413175744.png]]
69. Crear el directorio uno en el directorio HOME con permiso de escritura y paso para el propietario, de lectura y paso para los usuarios de su mismo grupo y ningún permiso para el resto de usuarios.
    ![[Pasted image 20250413175916.png]]
70. Crear el directorio uno1 dentro del directorio creado en el ejercicio anterior con todos lo permisos para el usuario, ninguno para los usuarios del grupo y permiso de escritura para el resto de usuarios.
    ![[Pasted image 20250413175940.png]]