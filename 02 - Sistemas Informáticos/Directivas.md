# Práctica guiada de configuración de GPOs:

1. Los usuarios normales NO tienen derecho a cambiar la hora :
    Entrar con un usuario normal (no administrador, probar a pulsar +L) e intenta cambiar la hora del ordenador = (Reloj/Boton derecho/Ajustar fecha y hora). 
    
    NO PUEDE, porque como Usuario normal y corriente tiene restringido este derecho. 
    
    Vamos a darles derecho al grupo clase1 para que ellos sí puedan cambiar la hora . Para ello entramos con un Administrador y accedemos a la consola de directivas:
    
    `Inicio/Ejecutar/gpedit.msc` (Directiva de grupo)
    
	Siguiendo la ruta: Directiva Equipo Local / Configuracion del equipo/Configuracion de Windows / Configuracion de seguridad / Directivas locales / Asignacion de derechos de usuarios / Cambiar la hora del sistema.
	
	Agregamos el grupo clase1. 
	![[{D32AF2D9-5A31-4DEC-B1F0-3800811BC2ED}.png]]
	
	Ahora entramos con un usuario de este grupo y comprobamos que ahora puede cambiar la hora. 
	![[{52701CC0-E498-4D72-9B35-56B90C12F97D}.png]]
	
	Otros derechos que podemos asignar son: 
	- Saltarse la comprobacion de recorrido: permiso para recorrer una carpeta aunque se le haya denegado. 
	- Realizar tareas de mantenimiento de volumenes: permiso para limpiar y desfragmentar discos. 
	- Apagar el Sistema: Para que pueda apagar el ordenador. 
	- Tomar posesion de archivos y otros objetos: cualquier usuario puede hacerse propietario de una carpeta protegida con permisos. 
	- Denegar el acceso desde la red a este equipo: impide que un usuario entre en el equipo a traves de la red. 
	- Inicio de sesion local: estos usuarios podrán acceder al equipo.
	  
2. Lo que vamos a hacer ahora se aplicará a todos los usuarios que utilicen el equipo. 
   
   Vamos a crear dos pequeños archivos bat para monitorizar el encendido y apagado del equipo. 
   
   Para ello creamos en C:\ dos archivos con el contenido que se indica: 
	   Nombre fichero 1: encendido.bat 
	
	contenido:
	```bat
	echo "El equipo se ha encendido a las " >> c:\registroOnOff.log
	DATE /T >> c:\registroOnOff.log
	TIME /T >> c:\registroOnOff.log
	```
	
	Nombre fichero 2: apagado.bat 
	contenido: 
	
```Bat
echo “El equipo se ha apagado a las “ >> c:\registroOnOff.log 
	DATE /T >> c:\registroOnOff.log 
	TIME /T >> c:\registroOnOff.log 
```

![[{91E07C38-3F20-492A-BBA5-D74A241F1221} 1.png]]

Vamos ahora a hacer que estos dos ficheros por lotes se ejecuten al inicio y cuando se apague el equipo, para ello vamos a :
	
Configuracion del equipo / Configuracion de Windows / Scripts (inicio/apagado) / Inicio y añadimos C:\encendido.bat 
![[{C9C360DD-AF04-439E-8BBC-C009C3D89606}.png]]

Ahora hacemos lo mismo en Configuracion del equipo / Configuracion de Windows / Scripts (inicio/apagado) / Apagado y añadimos C:\apagado.bat 

![[{2C05DB2D-4116-433A-973F-91FC7EE90873}.png]]
	
Cada vez que encendamos o apagemos el ordenador, se grabará la hora en el archivo registroOnOff.log

3. A continuacion tenemos una lista de directivas que puedes buscarlas en tu Windows y probar alguna de ellas: 
- Configuracion del equipo / Configuracion de Windows / Configuracion de seguridad / Directivas de cuentas/Directivas de contrasenas se configuran los parámetros que rigen las contraseñas cuando creamos un usuario (alteramos la configuracion por defecto).
  ![[{C36E4D6A-BA6C-462B-84B1-89BCA2CF4A6B}.png]] 
- Configuración del equipo / Configuracion de Windows / Configuracion de seguridad / Directivas de cuentas / Directivas de bloqueo de cuentas: establecemos el numero de errores de autenticacion que permitimos a un usuario antes de bloquear su cuenta. 
  ![[{3007305A-57F2-453F-B62C-78C4D62F724B}.png]]
- Configuracion del equipo / Configuracion de Windows / Configuracion de seguridad / Directivas locales / Directivas de auditorias: se establece un archivo donde se guardarán los informes de errores, inicios, sucesos, cambios, etc. 
  
  ![[{5A1C3CF1-07F4-42C6-845A-7B7D953E035E}.png]]
- Configuracion del equipo / Configuracion de Windows / Configuracion de seguridad / Directivas locales / Opciones de seguridad: en estas opciones podemos cambiar 
	- El nombre de la cuenta de invitado. 
	- Cambiar nombre de cuenta de administrador  
	- Permitir formatear y expulsar medios extraíbles. Restringir el acceso a CDROM (Solo a los usuarios normales, el Administrador podría entrar). 
	- Inicio sesion interactiva para pedir a los usuarios que cambien su contraseña antes que caduque.  
	- Inicio sesión interactiva : comunicar textos a todos los usuarios que inician la sesion.
	  
	  ![[{8A73C129-539B-4A43-964D-BFE1C536DEF7}.png]]
	
- Configuracion del equipo / Configuracion de seguridad / Directivas locales / Asignacion de derechos / Tener acceso a este equipo desde la red.
  
  ![[{F32E973E-4906-4D99-9C83-DD2EA69DB219}.png]]
  
- Configuracion del equipo / Configuracion de Windows / Configuracion de seguridad / Directiva de restriccion de software: aquí habría que pinchar el boton derecho del raton y elegir Nuevas directivas de restriccion de software. Y ahora Reglas adicionales. De esta manera se puede impedir la ejecucion de programas (luego lo haremos en el ejercicio 4). 
  
  ![[{AE282F2F-06BB-4AC9-BCF2-539D73C62B08}.png]]
  
- Configuracion del equipo / Plantillas administrativas / Sistema / Desactivar reproduccion automática de CDROM. 
  
  ![[{85BD47D0-8DDB-4DA2-9DE9-7CF7BBE61A20}.png]]

- Configuracion de usuario / Plantillas administrativass podemos configurar aspectos de Windows como el Menu inicio, el Escritorio, el Panel de control, Carpetas compartidas, la Red, Sistema y Componentes de Windows, etc.

![[{4EBFF1A8-D16A-4C2A-8EE7-678CEF62DFE4} 1.png]]


4. Ejemplo de restriccion de ejecucion de software: 
	- Nos dirigimos a Configuracion del equipo / Configuracion de Windows / Configuracion de seguridad / Directiva de restriccion de software / Reglas adicionales: 
	- Ahora en el Panel de la derecha (en la zona blanca) hay que pulsar el boton derecho del raton para elegir Regla de nueva ruta Como ejemplo vamos impedir que la Calculadora se ejecute. 
	- Indicamos la ruta del ejecutable de la calculadora que será así: Cs\ Windows\System32\calc.exe 
	- ![[{D2909B96-F9B8-44EB-8136-19248748C098}.png]]
	- En Nivel de seguridad elegimos No permitido. Aceptamos y deberemos cerrar e iniciar de nuevo sesion para que se aplique la directiva. Tambien podemos probar a actualizar las directivas desde la línea de comandos con la orden gpupdate o bien si se resiste gpupdate /force. 
	  
![[{7499B442-3A41-4AF1-9E0A-CE5F7D5D9A7D}.png]]

- Ahora se puede comprobar que no se puede ejecutar la Calculadora. 
- Si queremos excluir de esta prohibicion a los administradores podemos hacerlo en: Configuracion del equipo / Configuracion de Windows / Configuracion de seguridad / Directiva de restriccion de software / Obligatoriedad Ahora en Configuracion del equipo / Configuracion de Windows / Configuracion de seguridad / Directiva de restriccion de software / Tipos de archivos, podemos especificar los tipos de archivos que admitirán este tipo de restricciones. ¡Ojo! Si una aplicacion está restringida mediante la "Regla de restriccion de ruta" y la cambiamos de carpeta dejará de estar restringida.
