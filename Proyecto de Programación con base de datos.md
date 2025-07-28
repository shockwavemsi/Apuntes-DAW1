# Estructura

![[Pasted image 20250728165035.png]]

# TABLAS DE LA BASE DE DATOS

>[!Tabla] # Usuario
> - **PK(Id_Usuario)** (INT)	
> - Nombre (STRING)
> - Apellido (STRING)
> - Email (VARCHAR)

>[!Tabla] # Libro
> - **PK(Id_Usuario)** (INT)	
> - Nombre (STRING)
> - Apellido (STRING)
> - Email (VARCHAR)

>[!Tabla] # Libros_Prestados
>- **PK(Id_Prestamo,Id_Libro,Id_Usuario)**	
>- *FK(Id_Libro)* de **LIBRO(Id_Libro)**
>- *FK(Id_Usuario)* de **USUARIO(Id_Usuario)**
>- Fecha_Prestamo (DATE)
>- Fecha_Devolucion (DATE)

>[!tabla] # Telefonos
> - **PK(Id_Usuario,Telefono)** (INT)
> - *FK(Id_Usuario)* de **USUARIO(Id_Usuario)**

>[!tabla] # Multas
>- **PK(Id_Multa,Id_Usuario)** (INT)
>- *FK(Id_Usuario)* de **Usuario(Id_Usuario)**
>- Tiempo_de_sancion (DATE)

---