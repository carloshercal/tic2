# Soluciones — Prácticas de CSS (UT1)
> En los ejercicios 2 a 9 el alumnado parte del HTML que se da en el enunciado (en los ejercicios 2, 3, 4 y 9 lo completa siguiendo los pasos); el `index.html` de cada solución es el HTML final esperado.
>
> Soluciones de referencia de `docs/ut1-html-css-js/practicas-css.md`. Todas se han abierto en el navegador y las capturas de la página pública (`docs/img/css-practica-NN.png`) salen de este mismo código.

## Ejercicio 1 — Hola, mundo con estilo

Carpeta: `ejercicios-css/ej01-formas-css/`

**`index.html`**

```html
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Ejercicio 1 — Formas de aplicar CSS</title>
  <!-- 3. CSS externo: va primero -->
  <link rel="stylesheet" href="css/estilos.css">
  <!-- 2. CSS interno: va después del link, así que gana al externo si chocan -->
  <style>
    h1 { color: orange; }
    p { color: gray; }
  </style>
</head>
<body>
  <h1>¡Hola, mundo!</h1>
  <!-- 1. CSS en línea: gana siempre -->
  <p style="color: green;">Este párrafo tiene estilo en línea: sale verde aunque el CSS interno diga gris.</p>
  <p>Este párrafo solo recibe el CSS interno: sale gris.</p>
  <p>Estudio 2º de Bachillerato en el instituto y esta es mi primera página con CSS.</p>
  <!--
    PRIORIDAD OBSERVADA:
    - El h1 sale NARANJA: el <style> está después del <link> y ambos cambian el color.
    - Si movemos el <link> debajo del <style>, el h1 sale AZUL.
    - El primer párrafo sale VERDE: el estilo en línea gana siempre.
  -->
</body>
</html>
```

**`css/estilos.css`**

```css
/* Hoja de estilos externa del ejercicio 1 */
body {
  background-color: #f0f8ff;
}

h1 {
  color: blue; /* Pierde contra el CSS interno porque el <link> va antes */
}
```

Qué comprobar: el `<link>` va antes del `<style>` y el comentario final explica la prioridad (en línea > el que esté más abajo en el `<head>`). Error típico: poner el `<link>` fuera del `<head>` o escribir `href="estilos.css"` sin la carpeta `css/`.

## Ejercicio 2 — Mi playlist

Carpeta: `ejercicios-css/ej02-selectores-basicos/`

**`index.html`**

```html
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Ejercicio 2 — Mi playlist</title>
  <link rel="stylesheet" href="css/estilos.css">
</head>
<body>
  <h1>Mi playlist para estudiar</h1>
  <p id="intro">Estas son las canciones que escucho cuando preparo los exámenes.</p>
  <p>Las marcadas en rojo son mis favoritas.</p>

  <h2>Canciones</h2>
  <ul>
    <li class="favorita">Luces de la ciudad</li>
    <li>Camino de vuelta</li>
    <li class="favorita nueva">Verano en la plaza</li>
    <li>Domingo lento</li>
  </ul>

  <h2>Grupos que más escucho</h2>
  <ol>
    <li>Los Recreos</li>
    <li class="favorita">Tercera Planta</li>
    <li>Aula 12</li>
  </ol>
</body>
</html>
```

**`css/estilos.css`**

```css
/* Selector universal: todos los elementos */
* {
  font-family: Arial, sans-serif;
}

/* Selector de tipo: todos los párrafos */
p {
  color: #555555;
}

/* Unión de selectores: h1 y h2 a la vez */
h1, h2 {
  color: navy;
}

/* Selector de id: un único elemento (el primer párrafo) */
#intro {
  font-weight: bold;
}

/* Selector de clase: se repite en varios elementos */
.favorita {
  color: crimson;
}

/* Segunda clase: el elemento con class="favorita nueva" recibe las dos */
.nueva {
  background-color: yellow;
}
```

Qué comprobar: `id` único, clases sin punto en el HTML y la unión `h1, h2` en una sola regla. Error típico: escribir `class="favorita, nueva"` (con coma) en lugar de separar las clases con un espacio.

## Ejercicio 3 — Semana Cultural

Carpeta: `ejercicios-css/ej03-selectores-relacion/`

**`index.html`**

```html
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Ejercicio 3 — Semana Cultural</title>
  <link rel="stylesheet" href="css/estilos.css">
</head>
<body>
  <h1>Semana Cultural del instituto</h1>
  <h2>Lunes</h2>
  <p>Inauguración a las <span>10:00</span> en el salón de actos, <em>con <span>entrada libre</span></em>.</p>
  <h2>Martes</h2>
  <p>Durante toda la semana habrá <span class="verde">teatro</span>, <span class="azul">música</span> y <span class="naranja">deporte</span> en el patio.</p>
  <h2>Miércoles</h2>
  <p>Torneo de ajedrez en la biblioteca.</p>
</body>
</html>
```

**`css/estilos.css`**

```css
/* Paso 1 (descendiente): p span { color: blue; } coloreaba los DOS span del lunes.
   Paso 2 (hijo directo): con > solo se colorea el span que es hijo directo del <p>.
   El segundo span ("entrada libre") está dentro de <em>, así que ya no sale azul. */
p > span {
  color: blue;
}

/* Todos los h2 en verde... */
h2 {
  color: green;
}

/* ...salvo el que va justo después del h1 (hermano adyacente) */
h1 + h2 {
  color: red;
}

/* Todos los p que van después del h1, con el mismo padre (hermanos en general) */
h1 ~ p {
  background-color: #fffbe6;
}

/* Combinación: solo los span que tienen esa clase.
   Son más específicos que "p > span", por eso ganan. */
span.verde {
  color: green;
}

span.azul {
  color: darkblue;
}

span.naranja {
  color: darkorange;
}
```

Qué comprobar: el comentario del paso 2 explica que `>` solo selecciona hijos directos. `span.verde` gana a `p > span` porque una clase es más específica que dos etiquetas. Ampliación: `<p class="aviso">Torneo de <span class="especial">ajedrez</span> en la biblioteca.</p>` y `.aviso .especial { color: purple; }` (dos clases: gana a `p > span`).

## Ejercicio 4 — Enlaces de interés

Carpeta: `ejercicios-css/ej04-enlaces/`

**`index.html`**

```html
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Ejercicio 4 — Enlaces de interés</title>
  <link rel="stylesheet" href="css/estilos.css">
</head>
<body>
  <h1>Enlaces de interés para 2º de Bachillerato</h1>
  <nav>
    <ul>
      <li><a href="#">Inicio (enlace interno)</a></li>
      <li><a href="#">Horario del curso (enlace interno)</a></li>
      <li><a href="https://www.w3schools.com/css/" target="_blank" class="externo">Tutorial de CSS</a></li>
      <li><a href="https://developer.mozilla.org/es/" target="_blank" class="externo oficial">Documentación de MDN</a></li>
    </ul>
  </nav>
  <p>Los enlaces en negrita se abren en una pestaña nueva.</p>
  <p lang="en">Tip: always check the official documentation first.</p>
</body>
</html>
```

**`css/estilos.css`**

```css
/* ---- Selectores de atributo ----
   Van ANTES que las pseudoclases: así :hover (escrito más abajo)
   puede sobrescribir su color de fondo. */

/* [atributo]: enlaces que tienen target (se abren en pestaña nueva) */
a[target] {
  font-weight: bold;
}

/* [atributo="valor"]: solo los enlaces con href="#" (internos de prueba) */
a[href="#"] {
  background-color: #eeeeee;
}

/* [atributo~="valor"]: class contiene la palabra "oficial" (aunque tenga más clases) */
a[class~="oficial"] {
  background-color: #dff5df;
}

/* ---- Pseudoclases de enlaces, en orden: link, visited, hover, active ---- */
a:link {
  color: blue;
}

a:visited {
  color: purple;
}

a:hover {
  color: white;
  background-color: darkblue;
}

a:active {
  color: orange;
}

/* Pseudoclase de idioma: párrafos en inglés */
p:lang(en) {
  color: gray;
}
```

Qué comprobar: orden LVHA y selectores de atributo **antes** de las pseudoclases. Si están después, `a[href="#"]` y `a[class~="oficial"]` anulan el fondo de `:hover` (misma especificidad, gana la última).

## Ejercicio 5 — Lista de la compra

Carpeta: `ejercicios-css/ej05-lista-compra/`

**`index.html`**

```html
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Ejercicio 5 — Lista de la compra</title>
  <link rel="stylesheet" href="css/estilos.css">
</head>
<body>
  <h1>Lista de la compra para la cena de clase</h1>

  <div id="carniceria">
    <h2>Carnicería</h2>
    <ul>
      <li>Pollo para la barbacoa</li>
      <li>Chorizo <span class="oferta">en oferta</span></li>
      <li>Hamburguesas</li>
    </ul>
  </div>

  <div id="pescaderia">
    <h2>Pescadería</h2>
    <ul>
      <li>Merluza</li>
      <li>Gambas <span class="oferta">en oferta</span></li>
      <li>Calamares</li>
    </ul>
  </div>
</body>
</html>
```

**`css/estilos.css`**

```css
/* Palabra clave */
body {
  background-color: whitesmoke;
}

/* HSL: tono 210 (azul), saturación 60 %, luminosidad 30 % */
h1 {
  color: hsl(210, 60%, 30%);
}

/* Hexadecimal: rojo muy claro */
#carniceria {
  background-color: #ffe0e0;
}

/* RGB: azul muy claro */
#pescaderia {
  background-color: rgb(220, 235, 255);
}

/* RGBA: amarillo con transparencia (se ve el fondo de la caja a través) */
.oferta {
  background-color: rgba(255, 200, 0, 0.5);
  font-weight: bold;
}
```

Qué comprobar: los cinco formatos de color. Ampliación: `body { background-image: url("../img/textura.png"); }` (la ruta es relativa al archivo CSS, no al HTML).

## Ejercicio 6 — Cartel de un concierto

Carpeta: `ejercicios-css/ej06-cartel-concierto/`

**`index.html`**

```html
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Ejercicio 6 — Cartel del concierto</title>
  <link rel="stylesheet" href="css/estilos.css">
</head>
<body>
  <header>
    <h1>Los Recreos en concierto</h1>
    <p class="subtitulo">Fiesta de fin de trimestre</p>
  </header>
  <main>
    <p class="fecha">Viernes 19 de diciembre · 18:00 · Pabellón del instituto</p>
    <p>El grupo formado por alumnado de 2º de Bachillerato vuelve al escenario con canciones nuevas y alguna versión sorpresa. Lo recaudado se destinará al viaje de fin de curso.</p>
    <p class="precio">Entrada: <s>8 €</s> 5 € con el carné del instituto</p>
    <p class="centrado"><a href="#">Reserva tu entrada</a></p>
  </main>
</body>
</html>
```

**`css/estilos.css`**

```css
body {
  font-family: Verdana, Arial, sans-serif; /* Si no hay Verdana, Arial; si no, cualquier sin serifa */
  background-color: #1b1b2f;
  color: #f5f5f5;
}

header {
  text-align: center;
}

h1 {
  font-family: Impact, "Arial Black", fantasy; /* Nombre con espacios: entre comillas */
  font-size: 48px;
  color: #ffcc00;
}

.subtitulo {
  font-style: italic;
  font-size: x-large;
}

.fecha {
  font-weight: bold;
  text-align: center;
}

main p {
  text-align: justify;
  text-indent: 2em; /* Sangría de la primera línea */
}

/* Los párrafos centrados no llevan sangría */
.fecha,
.centrado {
  text-indent: 0;
}

.precio s {
  text-decoration: line-through; /* <s> ya lo tacha; aquí lo dejamos explícito */
  color: #999999;
}

.centrado {
  text-align: center;
}

a {
  color: #ffcc00;
  font-size: large;
  font-weight: bold;
  text-decoration: none; /* Quita el subrayado */
}

a:hover {
  text-decoration: underline;
}
```

Qué comprobar: nombres de fuente con espacios entre comillas y familia genérica al final. Si Impact no está instalada, el navegador usa la siguiente: es justo lo que se quiere mostrar.

## Ejercicio 7 — Mi deporte

Carpeta: `ejercicios-css/ej07-unidades/`

**`index.html`**

```html
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Ejercicio 7 — Unidades de medida</title>
  <link rel="stylesheet" href="css/estilos.css">
</head>
<body>
  <div class="portada">
    <h1>Mi deporte: el voleibol</h1>
  </div>
  <main>
    <h2>Cómo se juega</h2>
    <p>Dos equipos de seis jugadores separados por una red. <span class="nota">(En vóley playa son dos por equipo.)</span></p>
    <h2>Por qué me gusta</h2>
    <p>Es un deporte de equipo en el que nadie puede ganar solo.</p>
  </main>
  <footer>
    <p>Texto del pie en píxeles: no cambia aunque cambie la fuente raíz.</p>
  </footer>
</body>
</html>
```

**`css/estilos.css`**

```css
/* Tamaño de la fuente raíz: todo lo que va en rem depende de este valor.
   Prueba a cambiarlo a 20px y observa qué crece y qué no. */
html {
  font-size: 16px;
}

body {
  font-family: Arial, sans-serif;
}

/* vh: 30 % del alto de la ventana */
.portada {
  height: 30vh;
  background-color: #2e7d32;
  color: white;
}

h1 {
  font-size: 2.5rem; /* 2,5 × 16px = 40px */
}

h2 {
  font-size: 1.5rem; /* 1,5 × 16px = 24px */
  color: #2e7d32;
}

p {
  font-size: 1rem; /* 16px */
}

/* em dentro de font-size: relativo a la fuente del padre (el <p>) */
.nota {
  font-size: 0.75em; /* 0,75 × 16px = 12px */
  color: gray;
}

/* %: 80 % del ancho del padre (<body>) */
main {
  width: 80%;
  background-color: #f1f8e9;
}

/* px: tamaño fijo, no depende de la fuente raíz */
footer p {
  font-size: 12px;
}
```

Qué comprobar: con la raíz a 20px, el `h1` pasa a 50px, los `h2` a 30px, los párrafos a 20px y la nota a 15px; el pie sigue en 12px. Comprobado en navegador: la nota mide 12px con la raíz a 16px.

## Ejercicio 8 — Liga del recreo

Carpeta: `ejercicios-css/ej08-modelo-caja/`

**`index.html`**

```html
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Ejercicio 8 — Liga del recreo</title>
  <link rel="stylesheet" href="css/estilos.css">
</head>
<body>
  <main>
    <h1>Liga de fútbol sala del recreo</h1>
    <article class="equipo">
      <h2>Los Galácticos de 1ºA</h2>
      <p>Líderes con 12 puntos. Juegan los martes.</p>
    </article>
    <article class="equipo">
      <h2>Tercera Planta FC</h2>
      <p>Segundos con 9 puntos. Juegan los miércoles.</p>
    </article>
    <article class="equipo campeon">
      <h2>Aula 12</h2>
      <p>Campeones de la temporada pasada.</p>
    </article>
  </main>
</body>
</html>
```

**`css/estilos.css`**

```css
body {
  font-family: Arial, sans-serif;
  background-color: #eceff1;
}

/* Caja central: 600px de contenido, centrada con margin auto */
main {
  width: 600px;
  margin: 0 auto;
  padding: 20px;
  background-color: white;
}

h1 {
  border-bottom: 3px solid #1565c0; /* Solo el borde inferior */
  padding-bottom: 10px;
}

.equipo {
  width: 400px;              /* content */
  padding: 15px 25px;        /* 15px arriba/abajo, 25px izquierda/derecha */
  border: 2px solid #1565c0;
  margin: 20px auto;         /* 20px arriba/abajo; centrada a los lados */
  background-color: #e3f2fd;
}
/* Ancho de la caja visible de .equipo:
   400 (content) + 25 + 25 (padding) + 2 + 2 (border) = 454px */

/* Segunda clase: cambia solo el estilo y el color del borde */
.campeon {
  border-style: dashed;
  border-color: #f9a825;
  border-width: 4px;
}
/* Con border de 4px: 400 + 50 + 8 = 458px */
```

Qué comprobar: los cálculos de los comentarios. Anchos comprobados en navegador: 454px (`.equipo`) y 458px (`.campeon`). Ampliación: con `padding: 15px` → 400 + 30 + 4 = 434px.

## Ejercicio 9 — Tablón de anuncios

Carpeta: `ejercicios-css/ej09-posicionamiento/`

**`index.html`**

```html
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Ejercicio 9 — Tablón de anuncios</title>
  <link rel="stylesheet" href="css/estilos.css">
</head>
<body>
  <header id="inicio">
    <h1>Tablón de anuncios</h1>
  </header>
  <main>
    <article class="anuncio">
      <span class="etiqueta">NUEVO</span>
      <h2>Club de lectura</h2>
      <p>Primera reunión el jueves en la biblioteca, en el segundo recreo.</p>
    </article>
    <article class="anuncio">
      <h2>Se busca batería</h2>
      <p>El grupo del instituto necesita batería para el concierto de diciembre.</p>
    </article>
    <article class="anuncio desplazado">
      <h2>Objetos perdidos</h2>
      <p>Esta tarjeta está desplazada con position: relative. Fíjate en que su hueco original sigue ahí.</p>
    </article>
    <article class="anuncio">
      <span class="etiqueta">NUEVO</span>
      <h2>Excursión a la sierra</h2>
      <p>Entrega la autorización firmada antes del viernes.</p>
    </article>
    <article class="anuncio">
      <h2>Torneo de ajedrez</h2>
      <p>Inscripciones abiertas en conserjería.</p>
    </article>
  </main>
  <a href="#inicio" class="subir">↑ Arriba</a>
</body>
</html>
```

**`css/estilos.css`**

```css
body {
  font-family: Arial, sans-serif;
  background-color: #efe6d8;
}

main {
  width: 500px;
  margin: 0 auto;
}

.anuncio {
  position: relative;   /* Referencia para la etiqueta absolute que lleva dentro */
  padding: 10px 20px;
  border: 1px solid #bca98a;
  margin-bottom: 30px;
  background-color: #fffdf7;
}

/* Se coloca respecto a su antecesor posicionado: el .anuncio */
.etiqueta {
  position: absolute;
  top: -10px;
  right: 10px;
  padding: 3px 8px;
  background-color: crimson;
  color: white;
  font-weight: bold;
  font-size: 12px;
}

/* Se desplaza respecto a su posición normal, pero conserva su hueco */
.desplazado {
  top: 10px;
  left: 40px;
  background-color: #fff3cd;
}

/* Fijo respecto a la ventana: no se mueve al hacer scroll */
.subir {
  position: fixed;
  bottom: 20px;
  right: 20px;
  padding: 10px 15px;
  background-color: #37474f;
  color: white;
  text-decoration: none;
}
```

Qué comprobar: `.desplazado` se mueve porque el elemento también tiene la clase `anuncio`, que ya le da `position: relative`. Sin ese `relative`, las etiquetas se colocan respecto a la página (comprobado: ambas en la esquina superior derecha).

## Ejercicio 10 — Mi web con estilo

Carpeta: `ejercicios-css/ej10-sintesis/`

**`index.html`**

```html
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Inicio — Baloncesto en el insti</title>
  <link rel="stylesheet" href="css/estilos.css">
</head>
<body>
  <header>
    <p class="logo">Baloncesto en el insti</p>
    <nav>
      <a href="index.html">Inicio</a>
      <a href="sobre-mi.html">Sobre mí</a>
      <a href="contacto.html">Contacto</a>
    </nav>
  </header>
  <main>
    <h1>El baloncesto en nuestro instituto</h1>
    <img src="img/pista.svg" alt="Dibujo de una pista de baloncesto vista desde arriba" width="400" height="220">
    <p>Cada recreo, la pista del patio se llena de partidos de tres contra tres. En esta web te cuento cómo empezó todo y cómo puedes apuntarte.</p>
    <p>Más información en la <a href="https://www.feb.es" target="_blank">Federación Española de Baloncesto</a>.</p>
  </main>
  <footer>
    <p>Página creada para la UT1 de TIC II · Curso 2026-2027</p>
  </footer>
</body>
</html>
```

**`sobre-mi.html`**

```html
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Sobre mí — Baloncesto en el insti</title>
  <link rel="stylesheet" href="css/estilos.css">
</head>
<body>
  <header>
    <p class="logo">Baloncesto en el insti</p>
    <nav>
      <a href="index.html">Inicio</a>
      <a href="sobre-mi.html">Sobre mí</a>
      <a href="contacto.html">Contacto</a>
    </nav>
  </header>
  <main>
    <h1>Por qué me gusta el baloncesto</h1>
    <p>Empecé a jugar en <strong>1º de ESO</strong> y desde entonces no he parado. Lo que más me gusta es que <em>todo el equipo</em> cuenta.</p>
    <ul>
      <li>Se juega en equipo.</li>
      <li>Se puede practicar en cualquier pista del barrio.</li>
      <li>Cada partido es distinto.</li>
    </ul>
  </main>
  <footer>
    <p>Página creada para la UT1 de TIC II · Curso 2026-2027</p>
  </footer>
</body>
</html>
```

**`contacto.html`**

```html
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Contacto — Baloncesto en el insti</title>
  <link rel="stylesheet" href="css/estilos.css">
</head>
<body>
  <header>
    <p class="logo">Baloncesto en el insti</p>
    <nav>
      <a href="index.html">Inicio</a>
      <a href="sobre-mi.html">Sobre mí</a>
      <a href="contacto.html">Contacto</a>
    </nav>
  </header>
  <main>
    <h1>Contacto</h1>
    <form action="#" method="post">
      <p>
        <label for="nombre">Nombre</label><br>
        <input type="text" id="nombre" name="nombre">
      </p>
      <p>
        <label for="correo">Correo</label><br>
        <input type="email" id="correo" name="correo">
      </p>
      <p>
        <label for="mensaje">Mensaje</label><br>
        <textarea id="mensaje" name="mensaje" rows="5"></textarea>
      </p>
      <p>
        <input type="submit" value="Enviar" class="boton">
      </p>
    </form>
  </main>
  <footer>
    <p>Página creada para la UT1 de TIC II · Curso 2026-2027</p>
  </footer>
</body>
</html>
```

**`css/estilos.css`**

```css
/* Hoja común a las tres páginas del mini-sitio */

/* ---------- General ---------- */
body {
  margin: 0;
  font-family: Verdana, Arial, sans-serif;
  color: #263238;
  background-color: #fafafa;
}

/* ---------- Cabecera y menú ---------- */
header {
  padding: 10px 20px;
  background-color: #e65100;
}

.logo {
  margin: 0;
  font-size: 1.5rem;
  font-weight: bold;
  color: white;
}

nav {
  margin-top: 10px;
}

nav a {
  margin-right: 15px;    /* Separación entre enlaces del menú */
  color: white;
  text-decoration: none;
}

nav a:hover {
  text-decoration: underline;
}

/* ---------- Contenido ---------- */
main {
  width: 80%;
  margin: 20px auto;
  padding: 20px;
  border: 1px solid #dddddd;
  background-color: white;
}

h1 {
  color: #e65100;
  border-bottom: 2px solid #e65100;
  padding-bottom: 5px;
}

main p {
  text-align: justify;
}

main a {
  color: #e65100;
  font-weight: bold;
}

/* ---------- Formulario ---------- */
label {
  font-weight: bold;
}

input,
textarea {
  width: 60%;
  padding: 8px;
  margin-top: 5px;
  border: 1px solid #b0bec5;
}

/* Combinación: input que además tiene la clase boton */
input.boton {
  width: auto;
  background-color: #e65100;
  color: white;
  border: none;
  font-weight: bold;
}

input.boton:hover {
  background-color: #bf360c;
}

/* ---------- Pie ---------- */
footer {
  padding: 10px;
  text-align: center;
  font-size: 12px;
  color: white;
  background-color: #37474f;
}
```

Solución de referencia sobre un mini-sitio de ejemplo (tema: baloncesto). Cada alumno partirá de su propio sitio, así que lo que se valora es que la hoja cumpla la lista del paso 3. La imagen `img/pista.svg` es un dibujo de ejemplo. El menú se hace con enlaces directamente dentro de `<nav>` (sin lista) para no necesitar `display`, que todavía no se ha visto.
