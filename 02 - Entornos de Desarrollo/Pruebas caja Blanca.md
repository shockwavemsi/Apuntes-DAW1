# Tipos de Test

1. Test Simple (`@Test`)
   Útil para probar funciones individuales.
   
   Por ejemplo, `testResta()` verifica si `Calculadora2.resta(20,10)` devuelve 10 correctamente.
   
```java
@Test // Esta notación es recomendables para código simple, 
//pero no para varios switchs, if o elseif.  
void testResta() {  
    int resultadoEsperado = 10;  
    int resultado = Calculadora2.resta(20,10);  
    assertEquals(resultadoEsperado, resultado,"Fallo en resta");  
}
```

---

2. Test Parametrizado (`@ParameterizedTest`)
   Se usa para testear una función con **múltiples valores de entrada.**
   - `@CsvSource`: Nos permite probar la función `suma()` con diferentes conjuntos de números (`10,20,30`).
   - `@ValueSource` : Evalúa valores **uno por uno**.

    Por ejemplo, `testEsPar( int num )` prueba su número entre 1 - 9 son pares.
    
```java
@ParameterizedTest  
@ValueSource(ints = {1,2,3,4,5,6,7,8,9}) // Esto mete un valor único, osea uno por uno, aca serian 9 pruebas  
void testEsPar(int num) {  
    assertTrue(Calculadora2.esPar(num),"Es true???"); // El assertTrue ayuda a tratar booleanos y queremos que el resultado sea un true.  
}
```

```java
@ParameterizedTest  
@ValueSource(ints = {1,2,3,4,5,6,7,8,9}) // Esto mete un valor único, osea uno por uno, aca serian 9 pruebas  
void testNoEsPar(int num) {  
    assertFalse(Calculadora2.esPar(num),"Es false???"); // El assertFalse ayuda a tratar booleanos y queremos que el resultado esperado sea un false.  
}
```

---

3. Afirmaciones(`assertEquals`,`assertTrue`, `assertFalse`)

- `assertEquals(valorEsperado, resultado)`: Compara el valor esperado con el resultado real.
    <br>
- `assertTrue(condición)`: Verifica que la condición sea `true` (Ejemplo: `esPar(num)`).
    <br>
- `assertFalse(condición)`: Verifica que la condición sea `false` (Ejemplo: `noEsPar(num)`).

---

4. Anotaciones nuevas

- `@BeforeEach`: Se ejecuta antes de cada test para configurar datos
  
```Java
@BeforeEach
    void setUp() {
        System.out.println("🔹 Empezó el test");
    }
```
 
- `@AfterEach`: Se ejecuta después para limpiar recursos
  
```java
@AfterEach
    void tearDown() {
        System.out.println("✅ Terminó el test");
    }
```