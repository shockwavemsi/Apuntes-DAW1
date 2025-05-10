# Fundamentos de CSS
- Los comentarios en CSS se escriben con este formato:

```HTML
/*Aquí dentro escribes tu comentario*/
```

- La forma más eficiente de aplicar estilos,es por medio de las hojas de estilos externas.
  
```HTML
<link rel="stylesheet" href="estilos.css">
```

- La sintaxis básica de CSS tiene la siguiente estructura:

```CSS
selector{
	propiedad: valor;
}
```

# Colores y Estilos de Texto
- Para cambiar el color de fondo se utiliza la propiedad `background-color:` seguido de nombre o código hexadecimal del color.  

```CSS
/*Para cambiar el color de fondo se usa:*/
selector{
	background-color:#FFFF;
}
```

- Para cambiar el color del texto se utiliza la propiedad `color:` seguido del nombre o código hexadecimal del color.

```CSS
/*Se utiliza para cambiar el color del texto*/
selector{
	color:#FFFF;
}
```

- Para cambiar la fuente del texto utilizamos la propiedad `font-family:` seguido de fuente que queremos cambiar.

```CSS
/*Utilizamos para cambiar la fuente de un texto*/
selector{
	font-family:/*Aqui va la fuente o familia fuente*/;
}
```

- Para cambiar el tamaño de un texto utilizamos la propiedad `font-size:` seguido del valor y la unidad de medida.

```CSS
selector{
	font-size:/*Aquí el valor con la unidad de medida*/;
}
```

# Espacio y tamaño
- `Margin :` Propiedad para controlar el margen externo.
- `Padding:` Propiedad que define el relleno interno.
- `box-sizing:` `border-box:` : Permite incluir un padding y bordes en el ancho total del elemento.

aca una imagen.

# Selectores en CSS

- `* {}` : Selecciona todos lo elementos.
- `.clase {}` : Selecciona los elementos de una clase específica.
- `#id {}` : Selecciona los elementos de un ID específico.
- `div p {}` : Selecciona `<p>` dentro de un `<div>` (selector descendente).

# Modelo de Caja y Posicionamiento

- Propiedades Importantes: `width` , `height` ,`padding` , `margind`
	- Posicionamiento : `position :` `static` || `relative` || `absolute` || `fixed` || `sticky`.
	- Organizar: `display :` || `block` || `inline` || `inline-block` || `flex` ||`grid`.

# Flexbox y Grid

- **Flexbox** (`display: flex;`) , es bueno para diseño en una sola dimensión (fila o columna).
- **Grid** (`display: grid;`), bueno para estructura en dos dimensiones (filas y columnas).

>[!EXAMPLE] Ejemplo de CSS grid
>```CSS
>.container {
>    display: grid;
>    grid-template-columns: 1fr 2fr;
>    grid-template-rows: auto;
>}
>```

# Unidades de Medida
- **Absolutas :** `px`,`cm`,`mm`.
- **Relativas :** `%%`, `em`, `rem`, `vw`, `vh`, `fr` (para Grid).

# Enlaces y Hojas de Estilos Externos
- Para enlazar una hoja de estilos CSS , usamos la etiqueta `link` con la propiedad `rel = "stylesheet"` y `hreft = "nombre_de_hoja_de_estilos.css"`

```HTML
<link rel="stylesheet" href="styles.css">
```