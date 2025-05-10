# Herencia

Permite que una clase (subclase o derivada) herede las propiedades y comportamientos(métodos) de otra clase.

La relación nace la clase principal (superclase o clase base) con las clases que heredan de estas(clases hijas).

**Función :** Reutiliza código y establece una relación(superclase con clase hija).

>[!EXAMPLE] EJEMPLO DE HERENCIA
>``` JAVA
>
>// Superclase(clase base)
>class Animal {
>    String nombre;
>    Animal(String nombre) {
>        this.nombre = nombre;
>    }
>    void hablar() {
>        System.out.println("El animal hace un sonido");
>    }
>}
>
>// Clase Hija (subclase o derivada)
>class Perro extends Animal {
>    Perro(String nombre) {
>        super(nombre);
>    }
>    @Override
>    void hablar() {
>        System.out.println("El perro ladra");
>    }
>// Si queremos que se herede el método hablar de la  
>//  clase Animal usammos la siguiente fila de código :  
>// public void ejecutar() {  
>//        super.hablar  
>//    }
>
>//Clase que crea el objeto perro y ejecuta un método
>    public static void main(String[] args) {
>        Perro miPerro = new Perro("Fido");
  >      miPerro.hablar();  // Output: El perro ladra
 >   }
>}
>```

>[!INFO] Explicación
> 1. **Clase Animal :** Es la superclase que tiene un atributo `nombre` y un método `hablar()` que imprime "El animal hace sonido"
> 2. **Constructor de Animal :** Este constructor inicializa el nombre del animal
> 3. **Clase Perro :** Esta clase hija (subclase) hereda de animal. Utiliza `super(nombre)` para llamar al constructor de la superclase.
> 4. **Método hablar :** Este método sobrescribe el método `hablar()d` de `Animal` para proporcionar una implementación específica para los perros, que imprime "El perro ladra".
> 5. **Método Main :** Aquí es donde se crea un objeto `Perro` y se llama el método `hablar()`.

# Abstracción
La **abstracción** en la Programación Orientada a Objetos es un concepto que nos permite enfocarnos en lo esencial y ocultar los detalles innecesarios.
Por medio de clases y métodos abstractos, aquellos que solo se definen pero no se usan(implementan).
Esto permite enfocarse en "¿que hace?" un objeto , en lugar de de ¿Como lo hace?.

>[!EXAMPLE] EJEMPLO DE ABSTRACCIÓN (Figuras)
>```Java
> abstract class Figura {
>    abstract double area();
>}
>
>class Circulo extends Figura {
>    double radio;
>
>    Circulo(double radio) {
>        this.radio = radio;
>    }
>
>    @Override
>    double area() {
>        return 3.14159 * radio * radio;
>    }
>
>    public static void main(String[] args) {
>        Circulo miCirculo = new Circulo(5);
>        System.out.println(miCirculo.area());  // Output: 78.53975
>    }
>}
>
>```

>[!INFO] EXPLICACIÓN DE ABSTRACCIÓN
>1. **Clase Abstracta Figura :** Esta clase define un método un método abstracto `area()` que debe ser implementado en sus clases hijas(subclases).
>2. **Clase Circulo :** Esta clase hija(subclase) extiende de `Figura` e implementa el método `area()`.
>3. **Constructor de Circulo :** Inicializa el radio del círculo.
>4. **Método area() :** Calcula el área del circulo utilizando la fórmula πr².
>5. **Método Main :** Crea un objeto `circulo` con un radio de 5 y muestra el área calculada.

>[!cite] Nota personal
Para entender mejor la abstracción, consideremos la clase padre (superclase) abstracta `Figura`, que contiene un método abstracto `area()`. Este método no tiene implementación en la superclase, solo define que todas las clases hijas (subclases) deben implementar su propia versión de `area()`.
>
>En el ejemplo anterior, la clase `Circulo` es una subclase de `Figura` y proporciona una implementación específica del método `area()`, calculando el área del círculo usando la fórmula *3.14159 × radio × radio.*
>
>Si creamos una nueva clase como `Rectangulo`, también heredaría de `Figura` y tendría que implementar el método `area()` para calcular el área del rectángulo utilizando una fórmula diferente. Por ejemplo:

---

>[!EXAMPLE] EJEMPLO DE ABSTRACCIÓN(Vehiculos)
>```JAVA
>// Superclase Abstracta
>abstract class Vehiculo {
>	String marca;
>	
>	// Método constructor
>	Vehiculo(String marca){
>		this.marca = marca;
>	}
>
>	abstract void arrancar(); //Es el método abstracto
>}
>
>//Clase hija Coche extiende de Vehiculo
>public class Coche extends Vehiculo{
>	//Método Constructor
>	Coche(String marca){
>		super(marca);
>	}
>
>	//Método arrancar
>	void arrancar(){
>		System.out.println("El coche " + marca + " está arrancando.");
>	}
>}
>
>//Clase hija Moto extiende de Vehiculo
>public class Moto extends Vehiculo{
>	
>	//Constructor
>	Moto(String marca){
>		super(marca);
>	}
>	
>	//Método arrancar
>	void arrancar(){
>		System.out.println("La moto " + marca + " esta arrancando.");
>	}
>}
>```

>[!info] EXPLICACIÓN DE ABSTRACCIÓN (vehiculos)
># Vehiculo (Clase Padre Abstracto)
>```JAVA
>
>asbtract class Vehiculo{
>	String marca;
>	
>	Vehiculo(String marca){
>		this.marca = marca;
>	}
>	
>	abstract void arrancar();
>}
>```
>  - Esta clase abstracta define una común que tendrá todos los vehículos.
>  - Tiene un atributo `marca` que almacena la marca del vehículo.
>  - El constructor `Vehiculo(String marca)` inicializa el atributo `marca`.
>  - El método abstracto `arrancar` no tiene implementación aquí, lo que significa que cada clase hija(subclase) debe tener su propia implementación. 
>    
># Clase Coche (Clase hija)
>```JAVA
>
>class Coche extends Vehiculo{
>	Coche(String marca){
>		super(marca)
>	}
>	
>	void arrancar(){
>		System.out.println("El coche " + marca + " esta arrancando");
>	}
>}
>```
>  - Esta clase extiende de `Vehiculo`.
>  - Su constructor `Coche(String marca)` llama al constructor de la superclase `Vehículo` utilizando `super(marca)` para inicializar el atributo `marca`.
>  - Proporciona su propia implementación del método `arrancar()`, que imprime un mensaje específico para los coches
> 
> 
> # Clase Motocicleta (Clase hija)
> 
>```JAVA
>class Motocicleta extends Vehiculo{
>	Motocicleta(String marca){
>		super(marca);
>	}
>
>	void arrancaar(){
>		System.out.print("La motocicleta " + marca + " esta arrancando");
>	}
>}
>``` 
>  - Similar a la clase `Coche`, esta clase extiende de `Vehiculo`.
>  - Su constructor también llama al constructor de `Vehículo` utilizando `super(marca)`.
>  - Proporciona su implementación del método `arrancar`, que imprime un mensaje específico para las motocicletas.

>[!CITE] NOTA PERSONAL
>La palabra `super` se utiliza en Java para llamar el constructor de la superclase(clase padre) desde la subclase(clase hija).
>Esto es útil para inicializar atributos heredados de la super clase.


# Interfaces
Es una estructura que define un conjunto de métodos que las clases deben implementar.
Asegura que cualquier clase que implementa la interfaz siga una serie de métodos específicos.

- **Declaración :** Se declara utilizando la palabra clave `inteface`. Los métodos dentro de una interfaz son abstractos por defecto , es decir, solo tienen una firma(nombre,parámetros y tipo de retorno) y  no tiene implementación.

```JAVA
Interface Volador{
	void Volar(); //Método abstracto
}
```

- **Implementación :** Las clases que implementan una interfaz deben implementar todos lo métodos declarados en la interfaz.

```JAVA
//Clase Pajaro implementa la interface volador
class Pajaro implements Volador{
	public void volar(){
		System.out.println("El pájaro vuela");
	}
}

//Clase avion implenta la interface volador
class Avion implements Volador{
	public void Volar(){
		System.out.println("El avión vuela");
	}
}
```

- **Polimorfismo :** Las interfaces permiten tratar objetos de diferentes clases que usen la misma interfaz de manera uniforme.
  Esto se le conoce como polimorfismo

```JAVA
public class Main{
	public static void main(String[] arg){
		Volador pajaro = new Pajaro();
		Volador avion = new Avion();

		pajaro.volar(); //Output: El pájaro vuela
		avion.volar(); //Output: El avion vuela
	}
}
```

- **Métodos por defecto y estático :** Desde java 8 , las interfaces pueden contener métodos con implementación usando la palabra clave `default` (para métodos por defecto) y `static` (para métodos estáticos).

```JAVA
//Interface Volador
interface Volador{
	void volar(): //Método Abstracto

	default void despegar(){
		System.out.println("Preparándose para despegar");
	}

	default void aterrizar(){
		System.out.println("Aterrizando");
	}
}
```

```JAVA
//Clase Pajaro
class pajaro implements Volador{
	public void volar(){
		System.out.println("El pajaro vuela");
	}
}
```

```JAVA
//Clase Main
public class Main {
	public static void main(String[] args){
		Volador pajaro = new Pajaro();
		pajaro.volar();     //Output: El pájaro vuela
		pajaro.despegar();  //Output: Preparándose para despegar
	}
}
```

>[!Example] Ejemplo de interfaces

- Declaramos un interfaz `Volador`
```JAVA
interface Volador();
	void volar();      //Método abstracto
	void aterrizar();  // Método abstracto
```

- Luego, implementamos estos métodos a las clases Pájaro y Avión. De lo contrario, el compilador nos dará error.

```Java
//Clase Pajaro
class Pajaro implements Volador {
    @Override
    public void volar() {
        System.out.println("El pájaro vuela");
    }

    @Override
    public void aterrizar() {
        System.out.println("El pájaro aterriza");
    }
}
```

```JAVA
//Clase avion
class Avion implements Volador {
    @Override
    public void volar() {
        System.out.println("El avión vuela");
    }

    @Override
    public void aterrizar() {
        System.out.println("El avión aterriza");
    }
}
```

```JAVA
// Clase Main
public class Main {
    public static void main(String[] args) {
        Volador miPajaro = new Pajaro();
        Volador miAvion = new Avion();

        miPajaro.volar();       // Output: El pájaro vuela
        miPajaro.aterrizar();   // Output: El pájaro aterriza

        miAvion.volar();        // Output: El avión vuela
        miAvion.aterrizar();    // Output: El avión aterriza
    }
}
```

>[!CITE] Resumen
>  - Si una clase una interfaz , debe implementar todos los métodos de la interfaz.
>  - No podemos omitir métodos , todos deben ser implementados, o la clase será abstracta.

# Recursividad

