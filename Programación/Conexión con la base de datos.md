# 1.1 Conexión con la base de datos

Para conectar con la base de datos con Java, utilizaremos el JDBC.

## 1.1.1 Importación de las librerías


```Java
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.SQLException;
```

Aquí se importan las clases necesarias para manejar la conexión con la base de datos:

- `Connection:` Representa la conexión con la base de datos.
- `DriverManager:` Se encarga de administrar los controladores de bases de datos y proporcionar una conexión.
- `SQLException:` Maneja los errores relacionados con SQL.

## 1.1.2 Definición de credenciales y URL

```JAVA
String url = "jdbc:mysql://localhost:3307/agenda"; 
String username = "root"; 
String password = ""; 
```

- La variable `url` indica la dirección de la base de datos. Se usa el protocolo `jdbc:mysql://`, el servidor (`localhost`), el puerto (`3307`), y el nombre de la base (`agenda`).
    
- `username` y `password` son las credenciales para acceder a la base de datos. Aquí, `root` es el usuario y la contraseña está vacía.

## 1.1.3 Establecimiento de conexión

```JAVA
try (Connection connection = DriverManager.getConnection(url, username, password)) {
    System.out.println("¡Conexión establecida correctamente!");
} catch (SQLException e) {
    System.err.println("Error al conectar: " + e.getMessage());
}
```

- Se usa `DriverManager.getConnection(url, username, password)` para establecer la conexión con MySQL.
    
- La conexión se maneja dentro de un bloque `try-with-resources`, lo que significa que se cerrará automáticamente después de ejecutar el código.
    
- Si la conexión es exitosa, se muestra `"¡Conexión establecida correctamente!"`.
    
- Si ocurre un error (`SQLException`), se captura en el bloque `catch` y se imprime el mensaje de error.

## 1.1.4 Resumen

Este código intenta conectarse a una base de datos MySQL llamada `agenda`, ubicada en el puerto `3307` en `localhost`, usando el usuario `root`. Si la conexión falla, muestra un mensaje de error.