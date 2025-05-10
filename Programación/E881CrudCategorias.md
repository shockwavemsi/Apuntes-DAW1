# Código Completo

```Java
import java.sql.*;
import java.util.Scanner;

public class AgendaApp {
    private static final String URL = "jdbc:mysql://localhost:3307/agenda";
    private static final String USER = "root";
    private static final String PASSWORD = "";

    public static void main(String[] args) {
        try (Connection connection = DriverManager.getConnection(URL, USER, PASSWORD);
             Scanner scanner = new Scanner(System.in)) {

            int option;
            do {
                System.out.println("\nMenú de la agenda:");
                System.out.println("1. Listar categorías");
                System.out.println("2. Insertar nueva categoría");
                System.out.println("3. Eliminar categoría");
                System.out.println("4. Modificar categoría");
                System.out.println("5. Salir");
                System.out.print("Seleccione una opción: ");
                option = scanner.nextInt();
                scanner.nextLine(); 

                switch (option) {
                    case 1 -> listarCategorias(connection);
                    case 2 -> insertarCategoria(connection, scanner);
                    case 3 -> eliminarCategoria(connection, scanner);
                    case 4 -> modificarCategoria(connection, scanner);
                    case 5 -> System.out.println("Saliendo...");
                    default -> System.out.println("Opción no válida. Intente de nuevo.");
                }
            } while (option != 5);

        } catch (SQLException e) {
            System.err.println("Error de conexión: " + e.getMessage());
        }
    }

    private static void listarCategorias(Connection connection) throws SQLException {
        String query = "SELECT * FROM Categoria ORDER BY nombre";
        try (Statement stmt = connection.createStatement();
             ResultSet rs = stmt.executeQuery(query)) {

            System.out.println("\nCategorías disponibles:");
            while (rs.next()) {
                System.out.println(rs.getInt("id") + ". " + rs.getString("nombre"));
            }
        }
    }

    private static void insertarCategoria(Connection connection, Scanner scanner) throws SQLException {
        System.out.print("Ingrese el nombre de la nueva categoría: ");
        String nombre = scanner.nextLine();
        String query = "INSERT INTO Categoria (nombre) VALUES (?)";

        try (PreparedStatement pstmt = connection.prepareStatement(query)) {
            pstmt.setString(1, nombre);
            pstmt.executeUpdate();
            System.out.println("Categoría añadida correctamente.");
        }
    }

    private static void eliminarCategoria(Connection connection, Scanner scanner) throws SQLException {
        System.out.print("Ingrese el ID de la categoría a eliminar: ");
        int id = scanner.nextInt();
        scanner.nextLine();
        String query = "DELETE FROM Categoria WHERE id = ?";

        try (PreparedStatement pstmt = connection.prepareStatement(query)) {
            pstmt.setInt(1, id);
            int rowsAffected = pstmt.executeUpdate();
            if (rowsAffected > 0) {
                System.out.println("Categoría eliminada.");
            } else {
                System.out.println("No se encontró la categoría con el ID especificado.");
            }
        }
    }

    private static void modificarCategoria(Connection connection, Scanner scanner) throws SQLException {
        System.out.print("Ingrese el ID de la categoría a modificar: ");
        int id = scanner.nextInt();
        scanner.nextLine();
        System.out.print("Ingrese el nuevo nombre de la categoría: ");
        String nuevoNombre = scanner.nextLine();

        String query = "UPDATE Categoria SET nombre = ? WHERE id = ?";
        try (PreparedStatement pstmt = connection.prepareStatement(query)) {
            pstmt.setString(1, nuevoNombre);
            pstmt.setInt(2, id);
            int rowsAffected = pstmt.executeUpdate();
            if (rowsAffected > 0) {
                System.out.println("Categoría actualizada correctamente.");
            } else {
                System.out.println("No se encontró la categoría con el ID especificado.");
            }
        }
    }
}

```

---
# Funcionamiento

## 1. Conexión con la base de datos

El programa se conecta con la base de datos ubicada en `localhost:3307/agenda`, con el usuario `root` y sin contraseña.

```JAVA
public class AgendaApp {

//Declaramos estos atributos inmutables(osea que no se pueden editar), para con información para acceder a la base de datos.
    private static final String URL = "jdbc:mysql://localhost:3307/agenda";
    private static final String USER = "root";
    private static final String PASSWORD = "";

    public static void main(String[] args) {
    // Con un `Try-catch` intentamos conectar con la base de datos.

	    try (Connection connection = DriverManager.getConnection(URL, USER, PASSWORD)) {
    // Establecemos la conexión con la base de datos usando las variables definidas.
    
    // Aquí irían las operaciones con la conexión.

		} catch (Exception e) { // Manejamos posibles excepciones con la conexión.
    System.err.println("Error de conexión: " + e.getMessage()); // Mostramos el mensaje de error en caso de falla.
		}

	}
}
```


---

## 2. Menú interactivo

El usuario podrá interactuar con el usuario mediante la terminal, para que sea más simple, imprimiremos un menú con opciones para que se le sea más sencillo elegir una operación.

```Java
try (Connection connection = DriverManager.getConnection(URL, USER, PASSWORD)) { // En caso de que conecte a la BD, ahoras lo siguiente
    
		Scanner scanner = new Scanner(System.in)) // Instanciamos un Scanner

            int option; // Creamos una variable que almacene el número de la opción en `option`.
            do {
	            // Luego Imprimimos el siguiente menú
                System.out.println("\nMenú de la agenda:");
                System.out.println("1. Listar categorías");
                System.out.println("2. Insertar nueva categoría");
                System.out.println("3. Eliminar categoría");
                System.out.println("4. Modificar categoría");
                System.out.println("5. Salir");
                System.out.print("Seleccione una opción: ");
                option = scanner.nextInt();// Le pedimos al usuario que escriba un número y lo guardamos en `option`.
                scanner.nextLine(); // El '.nextLine()' limpia el scanner para evitar problemas.

				// Con un 'Switch' dependiendo la opción llamaremos a ciertos métodos con ciertos parámetros.
                switch (option) {
                    case 1 -> listarCategorias(connection);
                    case 2 -> insertarCategoria(connection, scanner);
                    case 3 -> eliminarCategoria(connection, scanner);
                    case 4 -> modificarCategoria(connection, scanner);
                    case 5 -> System.out.println("Saliendo...");
                    default -> System.out.println("Opción no válida. Intente de nuevo.");
         }
    } while (option != 5);// El bucle seguirá mientras 'option' sea diferente de 5.
}
```

---
## 3. Uso de **PreparedStatement** y **Stament**

Para consultas dinámicas que usan parámetros,usamos `PreparedStatement`, y para las simples, usamos `Statement`.

>[!TIP] Con 'Statement'

```Java
// Este ejemplo usa el 'Stament', para un consulta simple
private static void listarCategorias(Connection connection) throws SQLException {
        String query = "SELECT * FROM Categoria ORDER BY nombre";
        try (Statement stmt = connection.createStatement();
             ResultSet rs = stmt.executeQuery(query)) {

            System.out.println("\nCategorías disponibles:");
            while (rs.next()) {
                System.out.println(rs.getInt("id") + ". " + rs.getString("nombre"));
            }
        }
    }
```

>[!TIP] Con 'PreparedStatement'

```Java
// En este ejemplo usa el 'PreparedStament' para un inserción de datos con varios parámetros.
private static void insertarCategoria(Connection connection, Scanner scanner) throws SQLException {
        System.out.print("Ingrese el nombre de la nueva categoría: ");
        String nombre = scanner.nextLine();
        String query = "INSERT INTO Categoria (nombre) VALUES (?)";

        try (PreparedStatement pstmt = connection.prepareStatement(query)) {
            pstmt.setString(1, nombre);
            pstmt.executeUpdate();
            System.out.println("Categoría añadida correctamente.");
        }
    }
```

---

## 4. Métodos

### 4.1 Listar Categorías

Este método nos permite devolver todas las categorías con sus respectivos `ID` y `Nombre`, para ello solo necesita de parámetro de entrada el `Connection`.

```Java
// Es un método `private static`, lo que significa que solo puede ser usado dentro de la misma clase y no requiere una instancia de la clase para ejecutarse.
private static void listarCategorias(Connection connection) {

	// Almacenamos en un 'String' la consulta
    String query = "SELECT * FROM Categoria ORDER BY nombre";

	//Se crea un `Statement`, que es el objeto que permite ejecutar consultas SQL.
    try (Statement stmt = connection.createStatement();
	//`stmt.executeQuery(query)` ejecuta la consulta y devuelve los resultados en un objeto `ResultSet`, que actúa como un cursor sobre los datos obtenidos.
         ResultSet rs = stmt.executeQuery(query)) {

        System.out.println("\nCategorías disponibles:");

		//Es método avanza el siguiente registro en el 'ResultSet'.
        while (rs.next()) {
            System.out.println(rs.getInt("id") + ". " + rs.getString("nombre"));
        }

    } catch (SQLException e) {
        System.err.println("Error al listar categorías: " + e.getMessage());
    }
}
```

### 4.2 Insertar Categorías

```Java
private static void insertarCategoria(Connection connection, Scanner scanner) throws SQLException {
        System.out.print("Ingrese el nombre de la nueva categoría: ");
        String nombre = scanner.nextLine();
        String query = "INSERT INTO Categoria (nombre) VALUES (?)";

        try (PreparedStatement pstmt = connection.prepareStatement(query)) {
            pstmt.setString(1, nombre);
            pstmt.executeUpdate();
            System.out.println("Categoría añadida correctamente.");
        }
    }
```

### 4.3 Eliminar Categorías

```Java
private static void eliminarCategoria(Connection connection, Scanner scanner) throws SQLException {
        System.out.print("Ingrese el ID de la categoría a eliminar: ");
        int id = scanner.nextInt();
        scanner.nextLine();
        String query = "DELETE FROM Categoria WHERE id = ?";

        try (PreparedStatement pstmt = connection.prepareStatement(query)) {
            pstmt.setInt(1, id);
            int rowsAffected = pstmt.executeUpdate();
            if (rowsAffected > 0) {
                System.out.println("Categoría eliminada.");
            } else {
                System.out.println("No se encontró la categoría con el ID especificado.");
            }
        }
    }
```

### 4.4 Modificar Categorías

