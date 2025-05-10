
## 1. Validación XML : DTD

**DTD (Document Type Definition)** define la **estructura** de un documento XML para validarlo.

- Un documento XML es **válido** si cumple con la estructura definida en la DTD y está **bien formado**.
    
- Existen dos tipos de **DTD**:
    
    1. **Interna**: Se define dentro del propio XML.
        
    2. **Externa**: Se almacena en un archivo aparte y se referencia desde el XML.
       
- Se usa la declaración `<!DOCTYPE>` para asociar el XML a la DTD.
    
- En la DTD se pueden declarar:
    
    - **Elementos** (`<!ELEMENT>`): Pueden contener texto, otros elementos o estar vacíos.
        
    - **Atributos** (`<!ATTLIST>`): Definen características adicionales de los elementos.
        
    - **Entidades** (`<!ENTITY>`): Permiten reutilizar contenido.
        
    - **Notaciones** (`<!NOTATION>`): Se usan para entidades externas no analizables.

---

## 2. Operadores

| Operador | Descripción                                               |
| -------- | --------------------------------------------------------- |
| `?`      | **Opcional**, puede aparecer **0 o 1** veces.             |
| `*`      | **Puede aparecer 0, 1 o más veces** (cualquier cantidad). |
| `+`      | **Debe aparecer al menos 1 vez, pero puede repetirse**.   |

---
## 3.Diferencias entre **#PCDATA** y **CDATA**

### **#PCDATA (Parsed Character Data)**

- Se usa en **DTD** para definir que un elemento XML puede contener **texto libre**.
    
- Significa que el procesador XML **puede interpretar** caracteres especiales como `&`, `<`, `>` y reemplazarlos por sus equivalentes.
    
- Se escribe así en DTD:
  
```XML
<!ELEMENT nombre (#PCDATA)>
```

🔹 **Ejemplo XML válido**:

```XML
<nombre>Juan &amp; María</nombre>
```

👉 Aquí, `&amp;` representa `&`, que será interpretado correctamente en XML.

### **CDATA (Character Data)**

- Se usa en **atributos** dentro de una DTD, indicando que el valor del atributo puede ser **cualquier texto libre**.
    
- No tiene restricciones sobre caracteres especiales (`&`, `<`, `>`), ya que dentro de un atributo no necesitan ser interpretados.
    
- Se define en una DTD así:
  
```XML
<!ATTLIST ciudad pais CDATA #REQUIRED>
```

🔹 **Ejemplo XML válido**:

```XML
<ciudad pais="España & Italia">Madrid</ciudad>
```

👉 Aquí, el atributo `pais` contiene caracteres especiales sin necesidad de escaparlos.

### 🧐 **Diferencia clave**

- `#PCDATA` se usa en **elementos XML**, permitiendo solo texto que será **interpretado** por XML.
    
- `CDATA` se usa en **atributos**, permitiendo **cualquier texto libre** sin restricciones.

---

## Tipos de Normas en atributos DTD

| **Norma**             | **Significado**                                           |
| --------------------- | --------------------------------------------------------- |
| **Valor por defecto** | Se asigna un valor si el atributo no está presente.       |
| `#REQUIRED`           | El atributo es **obligatorio**, debe aparecer siempre.    |
| `#IMPLIED`            | El atributo es **opcional**, puede omitirse sin problema. |
| `#FIXED`              | El atributo **siempre** tendrá un valor fijo predefinido. |
1️⃣ **Atributo obligatorio (**`#REQUIRED`**)**:

```XML
<!ATTLIST ciudad pais CDATA #REQUIRED>
```

☑ En el XML, **todas** las ciudades deben tener el atributo `pais`, de lo contrario el documento no será válido.

2️⃣ **Atributo opcional (**`#IMPLIED`**)**:

```XML
<!ATTLIST ciudad poblacion CDATA #IMPLIED>
```

☑ En el XML, **puede** escribirse el atributo `poblacion`, pero no es obligatorio.

3️⃣ **Atributo con valor fijo (**`#FIXED`**)**:

```XML
<!ATTLIST producto moneda CDATA #FIXED "EUR">
```

☑ En el XML, **todos** los productos tendrán el atributo `moneda="EUR"` automáticamente.


---

## 📝 Ejercicios para aprender DTD

Vamos a practicar con unos ejercicios. Intenta resolverlos y dime si necesitas ayuda. 🚀

#### **Ejercicio 1 - DTD Interna**

Dado el siguiente XML, define una DTD interna válida:

```XML

<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE persona [
    <!-- Escribe aquí la DTD interna -->
]>
<persona>
    <nombre>Elena</nombre>
    <edad>25</edad>
</persona>

```

📌 **Pista**: Recuerda que `nombre` y `edad` contienen texto, así que usa `#PCDATA`.

🔍 **Cómo hacerlo**:

1. Declara el elemento raíz `persona`, indicando que contiene `nombre` y `edad`.
    
2. Declara los elementos `nombre` y `edad`, especificando que contienen texto.

```XML
<!DOCTYPE persona [
    <!ELEMENT persona (nombre, edad)>
    <!ELEMENT nombre (#PCDATA)>
    <!ELEMENT edad (#PCDATA)>
]>
```

💡 **Explicación**: `persona` es el elemento principal, y `nombre` y `edad` contienen texto (`#PCDATA`).

---

#### **Ejercicio 2 - DTD Externa**

>[!Attention] Diferencias de DTD externa
>Existen dos tipos de DTD externa: privada y pública. Para las privadas se utiliza SYSTEM y para las públicas PUBLIC.
>```xml
><--!Esta es una DTD privada-->
><!DOCTYPE elemento-raíz SYSTEM "URI">
> 
><--!Esta es una DTD pública-->
><!DOCTYPE elemento-raíz PUBLIC "identificador-público" "URI">
>```

Define una DTD externa en un archivo llamado `persona.dtd`, que valide el siguiente XML:

>[!NOTe]

```XML

<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE persona SYSTEM "persona.dtd">
<persona>
    <nombre>Diego</nombre>
    <profesion>Ingeniero</profesion>
</persona>

```

📌 **Pista**: La DTD debe declarar el elemento raíz `persona`, que contiene `nombre` y `profesion`.

🔍 **Cómo hacerlo**:

1. Crea un archivo `persona.dtd`.
    
2. Define el elemento `persona`, indicando que contiene `nombre` y `profesion`.
    
3. Declara `nombre` y `profesion` como elementos de texto.
    

✅ **Contenido de** `persona.dtd`:

```XML

<!ELEMENT persona (nombre, profesion)>
<!ELEMENT nombre (#PCDATA)>
<!ELEMENT profesion (#PCDATA)>

```

#### **Ejercicio 3 - Atributos**

Declara una **DTD interna** que permita que el siguiente XML tenga un atributo obligatorio `pais` en `ciudad`:

```XML

<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE ciudad [
    <!-- Escribe aquí la DTD interna -->
]>
<ciudad pais="España">Madrid</ciudad>

```

📌 **Pista**: Usa `<!ATTLIST ciudad pais CDATA #REQUIRED>`.

🔍 **Cómo hacerlo**:

1. Declara `ciudad` como elemento de texto.
    
2. Agrega un atributo `pais`, de tipo **CDATA** (texto) y obligatorio (`#REQUIRED`).
    

✅ **Solución**:

```XML

<!DOCTYPE ciudad [
    <!ELEMENT ciudad (#PCDATA)>
    <!ATTLIST ciudad pais CDATA #REQUIRED>
]>

```


---

#### **Ejercicio - Definiendo una DTD**

📌 **Objetivo**: Diseñar una DTD para validar un XML que almacene información sobre **cursos de formación**.

El documento XML debe incluir:

- Un elemento raíz llamado `cursos`.
    
- Un elemento `curso`, que contiene:
    
    - `titulo` (texto),
        
    - `descripcion` (texto),
        
    - `duracion` (número seguido de "horas"),
        
    - `modalidad` (puede ser "presencial" o "online").
        

#### **Tareas**

1️⃣ **Crea una DTD interna** dentro del siguiente XML:

```XML
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE cursos [
    <!-- Escribe aquí la DTD interna -->
]>
<cursos>
    <curso>
        <titulo>Introducción a XML</titulo>
        <descripcion>Curso básico sobre XML y DTD.</descripcion>
        <duracion>40 horas</duracion>
        <modalidad>online</modalidad>
    </curso>
</cursos>

```

📌 **Pista**: Recuerda que `titulo`, `descripcion` y `modalidad` contienen texto, mientras que `duracion` debe seguir un formato específico.

2️⃣ **Crea una DTD externa**, guardándola en un archivo llamado `cursos.dtd`, que valide el siguiente XML:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE cursos SYSTEM "cursos.dtd">
<cursos>
    <curso>
        <titulo>Desarrollo Web</titulo>
        <descripcion>Aprende HTML, CSS y JavaScript.</descripcion>
        <duracion>60 horas</duracion>
        <modalidad>presencial</modalidad>
    </curso>
</cursos>

```

📌 **Pista**: En la DTD, debes usar `<!ATTLIST>` para definir `modalidad` como un atributo **enumerado**, con valores "presencial" o "online".

---

✅ **Solución**:

1️⃣ Solución de la creación de la DTD interna

```XML
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE cursos [
    <!ELEMENT cursos (curso)+>
    <!ELEMENT curso (titulo,descripcion,duracion,modalidad)>
    <!ELEMENT titulo (#PCDATA)>
    <!ELEMENT descripcion #PCDATA>
    <!ELEMENT duracion #PCDATA>
    <!ELEMENT modalidad #PCDATA>
]>
<cursos>
    <curso>
        <titulo>Introducción a XML</titulo>
        <descripcion>Curso básico sobre XML y DTD.</descripcion>
        <duracion>40 horas</duracion>
        <modalidad>online</modalidad>
    </curso>
</cursos>

```

2️⃣ Solución de la creación de la DTD externa

```XML

<!ELEMENT cursos (curso)+>
<!ELEMENT curso (titulo, descripcion, duracion, modalidad)>
<!ELEMENT titulo (#PCDATA)>
<!ELEMENT descripcion (#PCDATA)>
<!ELEMENT duracion (#PCDATA)>
<!ATTLIST curso modalidad (presencial | online) #REQUIRED>
<!ATTLIST curso duracion CDATA #REQUIRED>

```

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE cursos SYSTEM "cursos.dtd">
<cursos>
    <curso>
        <titulo>Desarrollo Web</titulo>
        <descripcion>Aprende HTML, CSS y JavaScript.</descripcion>
        <duracion>60 horas</duracion>
        <modalidad>presencial</modalidad>
    </curso>
</cursos>

```

---

## Ejercicio Avanzado de DTD Interna

1. **Ejercicio - DTD para una Biblioteca Digital**

📌 **Objetivo**: Diseñar una **DTD interna** para estructurar un archivo XML que almacene información sobre **libros y autores**.

El XML debe incluir:

- Un **elemento raíz** llamado `biblioteca`.
    
- Cada **libro** debe contener:
    
    - `titulo` (texto).
        
    - `autor` (puede tener uno o más autores).
        
    - `genero` (puede ser **novela, ensayo, poesía o teatro**).
        
    - `editorial` (texto).
        
    - `precio` (opcional, con atributo `moneda`).
        
- El **autor** tiene un atributo obligatorio `id`, que es **único**.
    
- Se debe permitir que `biblioteca` contenga **varios libros** (`libro+`).
    
- El `precio` debe tener un valor numérico y su moneda por defecto debe ser `"EUR"`.
    

📌 **Pistas**: 1️⃣ Usa `ID` para que `id` sea un identificador único en `autor`. 2️⃣ Usa `|` para que `genero` tenga opciones limitadas. 3️⃣ Usa `*` para que `autor` pueda repetirse varias veces dentro de `libro`. 4️⃣ Usa `#IMPLIED` para que `precio` sea opcional.

### Respuesta correcta

```XML
<!DOCTYPE biblioteca [
    <!ELEMENT biblioteca (libro+)>
    <!ELEMENT libro (titulo,autor+,genero,editorial,precio?)>
    <!ELEMENT titulo (#PCDATA)>

    <!ELEMENT autor (#PCDATA)>
    <!ATTLIST autor id ID #REQUIRED>

    <!ELEMENT genero (#PCDATA)>
    <!ATTLIST genero tipo (novela|ensayo|poesía|teatro) #REQUIRED>

    <!ELEMENT editorial (#PCDATA)>

    <!ELEMENT precio (#PCDATA)>
    <!ATTLIST precio moneda CDATA "EUR">
]>

<biblioteca>
    <libro>
        <titulo>El Gran Libro XML</titulo>
        <autor id="sw">Juan Pérez</autor>
        <genero tipo="novela">Ficción histórica</genero>
        <editorial>Editorial Central</editorial>
        <precio moneda="eur">19.99</precio>
    </libro>
</biblioteca>
```