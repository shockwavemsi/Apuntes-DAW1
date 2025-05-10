## 1. Usuarios y Grupos
1. Abre la consola de gestión de usuarios y grupos locales ejecutando `lusrmgr.msc`.
   
![[{A243047F-60AB-4240-AABC-71731F8FFDDC}.png]]

![[{ABCB21C3-29A4-4B9E-BA47-94F961050BE6}.png]]

2. Crea nuevos usuarios con los siguientes nombres:
	1. alumno1
	2. alumno2
	3. alumno3
	4. alumno4
	5. profesor
	   
	   ![[{97A06AAD-24EB-47E0-8F5B-DBF257415A81}.png]]
3. Crea varios grupos con los siguientes nombres :
	1. clase1
	2. clase3
	3. profesores
	   ![[{D6105A5C-2187-4AA6-BF5B-825C5EC4A646}.png]]
4. Añade los usuarios a sus respectivos grupos:
![[{79E7CE0C-BA28-45A7-9318-D0974D28399E}.png]]
![[{C02F3B31-CAE8-42C4-8DE8-333A898D6FF6} 1.png]]
![[{D9884433-7129-477B-BAAF-B6752DFDEA73}.png]]

## 2. Consolas

Voy a describir cada consola y lo que puedes hacer en ellas. Para los pantallazos, necesitarías abrir cada una de las consolas en tu equipo y capturar la pantalla.

- **compmgmt.msc**: Administración del equipo
    
    - Permite acceder a herramientas como el visor de eventos, carpetas compartidas, administración de discos, y más.
      ![[{9E0296FE-65B8-4E11-8CA7-5D7788E53B03}.png]]
        
- **gpedit.msc**: Editor de directivas de grupo
    
    - Permite gestionar las políticas de seguridad y configuración para usuarios y equipos en un dominio.
    - ![[{D2E1DA17-8FEF-4740-850F-31F6924E325C}.png]]
        
- **devmgmt.msc**: Administrador de dispositivos
    
    - Permite ver y gestionar los dispositivos instalados en el equipo, como adaptadores de red, unidades de disco, y más.
    - ![[{4DFA5B42-1880-46BC-B4A6-60B85117D6B4}.png]]
        
- **diskmgmt.msc**: Administración de discos
    
    - Permite crear, eliminar, y formatear particiones de disco, así como asignar letras de unidad.
    - ![[{BD7BE212-25B1-4F2B-BC44-4355EB308100}.png]]
        
- **lusrmgr.msc**: Gestión de usuarios y grupos locales
    
    - Permite crear y gestionar usuarios y grupos locales, así como asignar permisos.
    - ![[{42FF8746-806A-4D98-A50E-6A1EA414C792}.png]]
        
- **services.msc**: Administración de servicios
    
    - Permite ver y gestionar los servicios que se ejecutan en el equipo, iniciar, detener, y configurar servicios.
    - ![[{AD10DD1F-DC33-40F7-B1B7-CA4A8C3F89D5}.png]]

## 3. Consola Personalizada

- Abre la consola genérica ejecutando `mmc`.
- ![[{512415F5-FC69-4DB7-9807-6934B1BAF3AB}.png]]
    
- Ve a "Archivo" y selecciona "Agregar o quitar complemento".
- ![[{536A4F6B-E1DC-4E4B-A412-C117521A9177}.png]]
    
- Añade los complementos que necesites, como "Administración de discos", "Editor de directivas de grupo", etc.
- ![[{23A36FA3-E317-4710-89AF-55A62AB010C5}.png]]
    
- Guarda la consola con el nombre miSuperConsola.msc.
- ![[{C98CED3E-C71A-469A-ABD7-C0B4309EF5EB}.png]]

## Modo Dios

El "Modo Dios" es una carpeta oculta en Windows que proporciona acceso a todas las herramientas de administración del sistema en un solo lugar.

Para activarlo:

1. Crea una nueva carpeta en el escritorio.
   ![[{19F03258-47F7-4616-8401-4D0E7E6B1627}.png]]
    
2. Renómbrala como: `GodMode.{ED7BA470-8E54-465E-825C-99712043E01C}`
    ![[{3D9EA985-D34C-4745-83FA-CF85E19D0F02}.png]]
3. Presiona Enter. La carpeta cambiará de icono y se convertirá en un acceso directo a todas las herramientas de administración de Windows.
   ![[{C29B5D3F-0D29-434F-919E-41FC806A420E}.png]]
   ![[{36651E27-0B63-420A-BB43-D5881DD69535}.png]]