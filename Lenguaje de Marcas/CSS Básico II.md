# Ejercicio 1
```CSS
/* Todos los elementos de la página */

body{

font-family: "Open Sans", Arial, sans-serif;

font-size: 1.2em;

line-height: 1.6;

color: #494949;}

/* Todos los párrafos de la página */

p{

color: #666;}

/* Todos los elementos h1 de la página */

h1{

font-weight: bold;

font-size: 3em;}

/* Todos los párrafos de clase "entradilla"*/

.entradilla p{

font-weight: bold;

font-size: 2em;}

/* Todos los párrafos que estén en div con id "noticia-principal" */

#noticia-principal p{

color: green;

padding: 1em;}

/* Todos los span que estén dentro de párrafos*/

span{

background: yellowgreen;}

/* Todos los elementos con id "noticia-principal" o con id "noticia-secundaria" */

#noticia-principal{

background: pink;

border: 1px solid black;

padding: 2em;

border-radius: 10px;}

#noticia-secundaria{

background: pink;

border: 1px solid black;

padding: 2em;

border-radius: 10px;}

/* Todos los enlaces que estén dentro de párrafos con clase "entradilla" */

a{

text-decoration: none;

color: orange;

font-weight: bold;}
```

# Ejercicio 2
```CSS
/* Todos los elementos de la página */

body{

font-family: "Open Sans", Arial, sans-serif;

font-size: 14px;

line-height: 1.6;

color: #494949;

}

/* Todos los párrafos de la página */

p{

color: #666;

}

/* Todos los elementos h1 de la página */

h1{

font-weight: bold;

font-size: 22px;

color: #DD1E64;

}

/*todos los elementos con clase producto*/

.producto{

background-color: pink;

}

/*todos los elementos con clase descripción*/

.descripcion{

font-size: 16px;

text-decoration: underline;

font-weight: bold;

}

/*los elementos <span> de clase especial que estén dentro de un <h1>*/

.especial{

font-weight: bold;

font-size: 20px;

color: yellowgreen;

background-color: black;

}

/*las imágenes que estén en un elemento con id destacado*/

#destacado img{

width: 100%;

}

/*el elemento con id anuncio*/

#anuncio{

width: 60%;

margin: auto;

background-color: #DD1E64;

}

/*los párrafos que estén dentro de un elemento con id anuncio*/

#anuncio p{

color: white;

}
```

# Ejercicio 3
```CSS
body{

font-size: 16px;

font-family: Arial, Helvetica, sans-serif;}

/* Todos los párrafos de la página */

p{

color: #555;}

/* Todos los párrafos contenidos en #primero */

#primero p{

color: #369;}

/* Todos los enlaces de la página */

a{

color: #C30;}

/* Los elementos <em> contenidos en #primero */

#primero em{

color: #0000BB;

background-color: #FFFFCC;}

/* Todos los elementos <em> con la clase "especial" en toda la página */

.especial{

color: #FFFF00;

background: #000000;}

/* Todos los elementos <span> contenidos en la clase "normal" */

.normal span{

font-weight: bold;}
```

# Ejercicio 4

```HTML
<!DOCTYPE html>

<html lang="Es">

<head>

<meta charset="UTF-8">

<meta name="viewport" content="width=device-width, initial-scale=1.0">

<link rel="stylesheet" href="styles.css">

<title>CSS_básico_II</title>

</head>

<body>

<table border="1">

<tr><td id="teal">teal</td><td class="table_red" id="teal">teal</td><td class="table_green" id="teal">teal</td><td class="table_blue" id="teal">teal</td></tr>

<tr><td id="red">red</td><td class="table_red" id="red">red</td><td class="table_green" id="red">red</td><td class="table_blue" id="red">red</td></tr>

<tr><td id="blue">blue</td><td class="table_red" id="blue">blue</td><td class="table_green" id="blue">blue</td><td class="table_blue" id="blue">blue</td></tr>

<tr><td id="orange">orange</td><td class="table_red" id="orange">orange</td><td class="table_green" id="orange">orange</td><td class="table_blue" id="orange">orange</td></tr>

<tr><td id="purple">purple</td><td class="table_red" id="purple">purple</td><td class="table_green" id="purple">purple</td><td class="table_blue" id="purple">purple</td></tr>

<tr><td id="olive">olive</td><td class="table_red" id="olive">olive</td><td class="table_green" id="olive">olive</td><td class="table_blue" id="olive">olive</td></tr>

<tr><td id="fuchsia">fuchsia</td><td class="table_red" id="fuchsia">fuchsia</td><td class="table_green" id="fuchsia">fuchsia</td><td class="table_blue" id="fuchsia">fuchsia</td></tr>

<tr><td id="green">green</td><td class="table_red" id="green">green</td><td class="table_green" id="green">green</td><td class="table_blue" id="green">green</td></tr>

</table>

</body>

</html>

```

```CSS
#teal{

color: teal;

}

  

#red{

color: red;

}

  

#blue{

color: blue;

}

  

#orange{

color: orange;

}

  

#purple{

color: purple;

}

  

#olive{

color: olive;

}

  

#fuchsia{

color: fuchsia;

}

  

#green{

color: green;

}

  

.table_red{

background-color: red;

}

.table_blue{

background-color: blue;

}

.table_green{

background-color: green;

}
```