# Indice

1. [[#Introducción a XML]]
# Introducción a XML

XML (Extensible Markup Language) es un lenguaje desarrollado por el W3C basado en SGML. Su propósito es almacenar e intercambiar datos estructurados. Se trata de un metalenguaje que permite definir otros lenguajes, como:

- GML (Geography Markup Language)
    
- MathML (Mathematical Markup Language)
    
- RSS (Really Simple Syndication)
    
- SVG (Scalable Vector Graphics)
    
- XHTML (Extensible HyperText Markup Language)
    

Para trabajar con XML, se utilizan editores y procesadores XML. Los editores permiten crear y modificar documentos XML, mientras que los procesadores validan y leen los archivos XML. Algunos procesadores como los XSLT ayudan a convertir XML en HTML.

# Estructura de un documento XML

Los documentos XML son archivos de texto organizados en una estructura de árbol. Se componen de:

- **Prólogo:** Opcional, contiene información sobre el documento, como la versión XML y codificación.
    
- **Ejemplar:** Obligatorio, es el contenido del documento con elementos jerárquicos.
    
# Elementos XML

Los elementos son la base de XML. Se escriben con etiquetas y pueden contener valores, otros elementos o atributos. Ejemplo básico:

```XML
<nombre>Elsa</nombre>
```

- **Elementos vacíos:** Son lo que no tienen contenido

```XML
<nombre/>
```

- **Relaciones padre-hijo:** Un elemento puede contener uno o más elementos.

```XML
<persona>
    <nombre>Elsa</nombre>
    <fecha-de-nacimiento>
        <día>18</día>
        <mes>6</mes>
        <año>1996</año>
    </fecha-de-nacimiento>
    <ciudad>Pamplona</ciudad>
</persona>
```

- **Contenido Mixto:** Puede combinar texto y elementos

```XML
<persona>
    <nombre>Elsa</nombre> vive en <ciudad>Pamplona</ciudad>.
</persona>
```

En este caso `persona` contiene `nombre` y `ciudad` en una misma línea.

# Normas básicas de sintaxis

Los nombres de las etiquetas deben ser descriptivos, distinguibles entre mayúsculas y minúsculas, y cumplir normas específicas.

>[!FAIL] Mala práctica
>```XML
><día>18</día>
>```
>
>❗ Aquí esta etiqueta esta usando tildes en ambas etiquetas.

>[!CHECK] Buena prática
>```XML
><dia>18</dia>
>```
>
>✅ Aquí ambas etiquetas no usan tildes.


# Atributos XML

Los atributos nos proporcionan información adicional dentro de los elementos de un documento XML.

```XML
<producto codigo="G45">
    <nombre color="negro" precio="12.56">Gorro de lana</nombre>
</producto>
```

✅ **Explicación :**

1. Aquí `producto` tiene un atributo `código` al que se le asigna un valor, y también contiene al elemento `nombre`.
   
2. Ahora, `nombre` tiene dos atributos `(color | precio)` con sus respectiva información, y esta etiqueta tiene contenido `Gorro de lana`.

# Declaración XML

Indica la versión y codificación usando este línea:

```XML
<?xml version="1.0" encoding="UTF-8"?>
```

También puede incluir e atributo `standalone` :

```XML
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
```

✅ Si pones `yes` , significa que el documento no depende de una DTD externa (quiere decir que es independiente).

# Validez y Bien Formado

Un documento debe cumplir estos 2 apartados:
- **Bien Formado / Formateado:** Cumple las reglas básicas de XML.
- **Válido:** Cumple las reglas de una DTD o esquema definido.

>[!FAIL] Ejemplo mal hecho:

```XML
<clientes>
    <cliente>
        <nombre>AcerSA <CIF>5666333</CIF>
    </cliente>
</clientes>
```

❗**Observaciones:**

1. La etiqueta `nombre` no tiene etiqueta de cierre.
2. La etiqueta `CIF` esta puesto en la misma línea de la etiqueta `nombre`.
   
>[!CHECK] Corrección

```XML
<clientes>
    <cliente>
        <nombre>AcerSA</nombre>
        <CIF>5666333</CIF>
    </cliente>
</clientes>
```

✅ Aquí corregimos los apartados antes mencionados.

# Referencias a entidades

Algunos caracteres especiales deben representarse con código


- `<` -> `&lt;`
- `>` -> `&gt;`
- `"` -> `&quot;`
- `'` -> `&apos;`
- `&` -> `&amp;`

>[!EXAMPLE] Ejemplo con caracteres especiales

```XML
<mensaje>El precio es &lt; 100 euros</mensaje>
```

✅ Gracias a esto el texto se interpretaría de esta manera *El precio es < 100 euros.*

# Secciones CDATA

 Permiten incluir código sin que sea interpreado.

```XML
<script>
    <![CDATA[
    public class HelloWorld {
        public static void main (String[] args) {
            System.out.println("¡Hola, mundo!");
        }
    }
    ]]>
</script>
```

# ¿Qué son los espacios de nombres en XML?

Un espacio de nombres XML es una forma de identificar y diferenciar etiquetas que podrían tener el mismo nombre pero significar cosas distintas en diferentes documentos o contextos. Se definen usando el atributo `xmlns`, que establece una referencia única.

```XML
<nombre>Juan Pérez</nombre>
<nombre>Madrid</nombre>
```

### **Cómo definir un espacio de nombres**

Para diferenciar estos elementos, se pueden usar espacios de nombres:

```XML
<persona:nombre xmlns:persona="http://ejemplo.com/personas">Juan Pérez</persona:nombre>
<ciudad:nombre xmlns:ciudad="http://ejemplo.com/ciudades">Madrid</ciudad:nombre>
```

Aquí definimos dos espacios de nombres:

- `persona:nombre` está bajo `http://ejemplo.com/personas`
    
- `ciudad:nombre` está bajo `http://ejemplo.com/ciudades`