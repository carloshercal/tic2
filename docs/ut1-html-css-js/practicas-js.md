---
title: UT1 — Prácticas de JavaScript
---

# Prácticas de JavaScript

Esta página recoge los ejercicios para practicar, paso a paso, lo visto en [JavaScript — Interactividad](javascript.md). Siguen el mismo orden que los apuntes: empiezan por cómo incluir JavaScript en una página y terminan con funciones y botones.

## Antes de empezar

Cada ejercicio va en **su propia carpeta** dentro de `ejercicios-js/` de tu repositorio, con esta estructura:

```
ejercicios-js/
└── ej01-hola-js/
    ├── index.html
    └── js/
        └── script.js
```

- **Ejercicio 1:** escribes tú todo el HTML.
- **Ejercicios 2 a 10:** tienes un **HTML de partida** en el enunciado. Crea el `index.html`, copia dentro el código tal cual y crea `js/script.js` vacío. El HTML ya trae el `<script src="js/script.js">` al final del `<body>`. Todo tu trabajo va en `script.js`.
- Abre `index.html` con **Live Server**. Cada vez que guardes, la página se recarga y el código vuelve a ejecutarse desde el principio (las ventanas de `prompt()` vuelven a salir).
- Ten **siempre abierta la consola** (**F12 → Consola**): ahí aparecen los `console.log()` y, en rojo, los errores con el número de línea.
- Comenta tu código con `//` explicando qué hace cada parte.
- Al terminar cada ejercicio, haz *commit* y *push* (sigue la guía [Subir tus ejercicios a GitHub](github.md)).

| Nº | Ejercicio | Contenido de los apuntes |
|---|---|---|
| 1 | Hola, JavaScript | Formas de incluir JavaScript y de mostrar datos |
| 2 | Preséntate | Ventanas emergentes, variables, constantes y concatenación |
| 3 | Calculadora | `Number()` y operadores aritméticos y de asignación |
| 4 | Mi semana | Arrays |
| 5 | Entrada al concierto | `if`, `if`/`else` y operadores lógicos |
| 6 | Calificaciones | `else if` |
| 7 | Cuenta atrás | Bucle `while` |
| 8 | Adivina el número | Bucle `do...while` |
| 9 | Tabla y playlist | Bucle `for` y recorrido de arrays |
| 10 | Me gusta | Funciones y eventos (`onclick`) |

---

## Ejercicio 1 — Hola, JavaScript

**Objetivo:** incluir JavaScript de las tres formas posibles (interno, externo y en línea) y usar distintas formas de mostrar datos.

**Pasos:**

1. Crea la carpeta `ej01-hola-js/` con un `index.html` válido (`lang="es"`, `charset` UTF-8 y `<title>`) y un archivo `js/script.js` vacío.
2. En el `<body>` escribe un `<h1>` con «Hola, JavaScript» y un párrafo con `id="demo"` y el texto «Este texto lo va a cambiar JavaScript.».
3. **En línea:** añade un botón `<button>` con el texto «Púlsame» y el atributo `onclick="alert('Has pulsado el botón')"`.
4. **Interno:** debajo del botón, añade un bloque `<script>` con un `alert()` que diga «Hola desde JavaScript interno».
5. **Externo:** justo antes de `</body>`, enlaza `js/script.js`. En ese archivo:
   - escribe en la consola «Hola desde el archivo script.js» con `console.log()`;
   - escribe en la consola el resultado de `5 + 6`;
   - cambia el contenido del párrafo `#demo` con `document.getElementById("demo").innerHTML` por un texto tuyo.
6. Recarga la página y observa **en qué orden** pasan las cosas. Pulsa el botón. Escribe al final del `<body>` un comentario HTML que explique el orden y por qué el `alert` del botón no sale hasta que lo pulsas.

**Resultado esperado:** al abrir la página sale primero la ventana «Hola desde JavaScript interno». Al cerrarla, el párrafo muestra tu texto y en la consola aparecen el saludo y el número 11. La ventana «Has pulsado el botón» solo sale al pulsar el botón.

**Entrega:** `ejercicios-js/ej01-hola-js/` (`index.html` + `js/script.js`).

**Ampliación opcional:** añade en `script.js` un `document.write("<p>Escrito con document.write</p>")` y fíjate en dónde aparece el párrafo dentro de la página.

---

## Ejercicio 2 — Preséntate

**Objetivo:** pedir datos con `prompt()` y `confirm()`, guardarlos en variables y constantes, y mostrarlos en la página uniendo textos con `+`.

**HTML de partida:** crea la carpeta `ej02-presentacion/`, copia este código en su `index.html` y crea `js/script.js` vacío.

```html
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Ejercicio 2 — Preséntate</title>
</head>
<body>
  <h1>Ficha de presentación</h1>
  <p id="saludo"></p>
  <p id="localidad"></p>
  <p id="musica"></p>

  <script src="js/script.js"></script>
</body>
</html>
```

**Pasos:**

En `js/script.js`:

1. Declara una **constante** `CURSO` con el valor `"2º de Bachillerato"`.
2. Pide con `prompt()` el **nombre**, la **localidad** (con un valor inicial, por ejemplo `"Mi pueblo"`) y la **edad**, y guarda cada respuesta en una variable con `let`.
3. Pregunta con `confirm()` si le gusta la música y guarda la respuesta en la variable `gustaMusica`.
4. Escribe en los párrafos de la página, uniendo textos y variables con `+`:
   - `#saludo`: «Hola, *nombre*. Estudias *curso* y tienes *edad* años.»
   - `#localidad`: «Vives en *localidad*.»
   - `#musica`: «¿Te gusta la música? » seguido del valor de `gustaMusica`.
5. Muestra en la consola el tipo de `edad` y de `gustaMusica` con `typeof`. Escribe en un comentario por qué `edad` es un `string` aunque hayas escrito un número.
6. Al final del archivo, intenta cambiar el valor de `CURSO`. Mira el error de la consola, cópialo en un comentario y deja esa línea comentada.

**Resultado esperado:** salen tres ventanas para escribir y una de Aceptar/Cancelar. Después, la página muestra los tres párrafos con tus datos, y el último termina en `true` o `false` según el botón que hayas pulsado. En la consola aparecen `string` y `boolean`.

**Entrega:** `ejercicios-js/ej02-presentacion/`.

**Ampliación opcional:** pulsa **Cancelar** en el primer `prompt()` y observa qué aparece en lugar del nombre. Explícalo en un comentario.

---

## Ejercicio 3 — Calculadora

**Objetivo:** convertir texto en número con `Number()` y usar los operadores aritméticos y de asignación.

**HTML de partida:** crea la carpeta `ej03-calculadora/`, copia este código en su `index.html` y crea `js/script.js` vacío.

```html
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Ejercicio 3 — Calculadora</title>
</head>
<body>
  <h1>Calculadora</h1>
  <p>Números introducidos: <span id="numeros"></span></p>
  <ul>
    <li>Suma: <span id="suma"></span></li>
    <li>Resta: <span id="resta"></span></li>
    <li>Multiplicación: <span id="multiplicacion"></span></li>
    <li>División: <span id="division"></span></li>
    <li>Resto de la división: <span id="resto"></span></li>
    <li>Primer número al cuadrado: <span id="potencia"></span></li>
  </ul>
  <p id="puntos"></p>

  <script src="js/script.js"></script>
</body>
</html>
```

**Pasos:**

1. Pide dos números con `prompt()` y guárdalos en `a` y `b` **sin convertirlos**. Escribe `a + b` en `#suma` y prueba con 5 y 3. Anota en un comentario qué sale y por qué.
2. Ahora convierte los dos valores con `Number()` y comprueba que la suma ya es correcta.
3. Escribe en `#numeros` los dos números (por ejemplo «5 y 3») y en cada `span` de la lista el resultado de su operación: `+`, `-`, `*`, `/`, `%` y `a ** 2`.
4. Declara `let puntos = 10;` y, en este orden: súmale `a` con `+=`, multiplícalo por 2 con `*=` y súmale 1 con `++`. Muestra el resultado en `#puntos`.
5. Calcula a mano cuánto debe salir `puntos` con a = 5 y escríbelo en un comentario con la operación completa.

**Resultado esperado:** con 5 y 3: suma 8, resta 2, multiplicación 15, división 1.666…, resto 2 y cuadrado 25. Los puntos finales son 31.

**Entrega:** `ejercicios-js/ej03-calculadora/`.

**Ampliación opcional:** escribe una letra en lugar de un número y observa el resultado (`NaN`). Prueba también a dividir entre 0.

---

## Ejercicio 4 — Mi semana

**Objetivo:** crear arrays, acceder a sus elementos por la posición, usar `length` y modificar un elemento.

**HTML de partida:** crea la carpeta `ej04-mi-semana/`, copia este código en su `index.html` y crea `js/script.js` vacío.

```html
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Ejercicio 4 — Mi semana</title>
</head>
<body>
  <h1>Mi semana</h1>
  <p id="total"></p>
  <p id="primero"></p>
  <p id="elegido"></p>
  <p id="cambio"></p>

  <script src="js/script.js"></script>
</body>
</html>
```

**Pasos:**

1. Crea un array `dias` con los siete días de la semana.
2. Crea otro array `planes` con **siete** cosas que haces cada día (entrenar, clase de música, biblioteca…), en el mismo orden que los días.
3. En `#total`, muestra cuántos días tiene la semana usando `dias.length`.
4. En `#primero`, muestra «El Lunes toca: …» usando la posición 0 de los dos arrays.
5. Pide con `prompt()` un número del 1 al 7 (conviértelo con `Number()`) y muestra en `#elegido` el día y el plan correspondientes. Recuerda que las posiciones empiezan en 0.
6. Cambia el plan del domingo por otro distinto (asignando un valor nuevo a esa posición) y muéstralo en `#cambio`.
7. Recarga y escribe un 8 en el `prompt()`. Explica en un comentario qué sale y por qué.

**Resultado esperado:** con un 3, la página muestra «La semana tiene 7 días.», «El Lunes toca: …», «El Miércoles toca: …» y el cambio de planes del domingo. Con un 8 aparece `undefined`, porque esa posición no existe.

**Entrega:** `ejercicios-js/ej04-mi-semana/`.

**Ampliación opcional:** muestra el último día del array sin escribir el número 6, usando `dias.length - 1`.

---

## Ejercicio 5 — Entrada al concierto

**Objetivo:** tomar decisiones con `if` y `if`/`else`, combinando condiciones con los operadores lógicos `&&` y `||`.

**HTML de partida:** crea la carpeta `ej05-concierto/`, copia este código en su `index.html` y crea `js/script.js` vacío.

```html
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Ejercicio 5 — Entrada al concierto</title>
</head>
<body>
  <h1>Concierto de Los Recreos</h1>
  <p>Edad mínima: 16 años. Entrada: 8 € (5 € con el carné del instituto o si eres menor de 18).</p>
  <p id="acceso"></p>
  <p id="precio"></p>
  <p id="aviso"></p>

  <script src="js/script.js"></script>
</body>
</html>
```

**Pasos:**

1. Pide la **edad** con `prompt()` (conviértela a número). Pregunta con `confirm()` si tiene **entrada reservada** y, con otro `confirm()`, si tiene el **carné del instituto**.
2. **Acceso** (`&&`): si tiene 16 años o más **y** entrada reservada, escribe en `#acceso` «Puedes pasar al concierto.»; si no, «Lo siento, no puedes pasar.».
3. **Precio** (`||`): si tiene carné **o** es menor de 18, la entrada cuesta 5 €; si no, 8 €. Escríbelo en `#precio`.
4. **Aviso** (`if` simple): solo si es menor de 16, escribe en `#aviso` cuántos años le faltan para poder entrar.
5. Prueba **al menos tres casos** distintos y anota en un comentario qué sale en cada uno.

**Resultado esperado:** con 17 años, entrada y sin carné: «Puedes pasar» y 5 €. Con 14 años: «No puedes pasar», 5 € y «Te faltan 2 años…». Con 20 años, sin entrada ni carné: «No puedes pasar» y 8 €, y el párrafo del aviso queda vacío.

**Entrega:** `ejercicios-js/ej05-concierto/`.

**Ampliación opcional:** usa `!` para mostrar, si **no** tiene entrada reservada, el mensaje «Reserva tu entrada en conserjería».

---

## Ejercicio 6 — Calificaciones

**Objetivo:** usar el condicional múltiple `else if` y comprobar que las condiciones se evalúan en orden.

**HTML de partida:** crea la carpeta `ej06-notas/`, copia este código en su `index.html` y crea `js/script.js` vacío.

```html
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Ejercicio 6 — Calificaciones</title>
</head>
<body>
  <h1>Calificaciones de TIC II</h1>
  <p id="resultado"></p>

  <script src="js/script.js"></script>
</body>
</html>
```

**Pasos:**

1. Pide una nota con `prompt()` y conviértela con `Number()`.
2. Declara una variable `calificacion` sin valor.
3. Con `if` / `else if` / `else`, guarda en `calificacion` el texto que corresponde:
   - menor que 0 **o** mayor que 10 (`||`): «Nota no válida»;
   - menor que 5: «Insuficiente»;
   - menor que 6: «Suficiente»;
   - menor que 7: «Bien»;
   - menor que 9: «Notable»;
   - en cualquier otro caso: «Sobresaliente».
4. Escribe en `#resultado` la nota y la calificación (por ejemplo «Nota: 7.5 → Notable»).
5. Prueba con 4, 7.5, 9 y 11. Escribe en un comentario por qué en la condición de «Suficiente» no hace falta comprobar también que la nota es mayor o igual que 5.

**Resultado esperado:** 4 → Insuficiente, 7.5 → Notable, 9 → Sobresaliente y 11 → Nota no válida. Los decimales se escriben con punto.

**Entrega:** `ejercicios-js/ej06-notas/`.

**Ampliación opcional:** pide tres notas, calcula la media y muestra su calificación. Cuidado con los paréntesis: `(n1 + n2 + n3) / 3`.

---

## Ejercicio 7 — Cuenta atrás

**Objetivo:** repetir instrucciones con un bucle `while` e ir acumulando un texto con `+=`.

**HTML de partida:** crea la carpeta `ej07-cuenta-atras/`, copia este código en su `index.html` y crea `js/script.js` vacío.

```html
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Ejercicio 7 — Cuenta atrás</title>
</head>
<body>
  <h1>Cuenta atrás para las vacaciones</h1>
  <p id="cuenta"></p>

  <script src="js/script.js"></script>
</body>
</html>
```

**Pasos:**

1. Pide con `prompt()` desde qué número empieza la cuenta atrás (pon `"10"` como valor inicial) y conviértelo a número.
2. Declara una variable `texto` con una cadena vacía (`""`).
3. Con un bucle `while`, mientras el número sea mayor que 0:
   - muéstralo en la consola;
   - añádelo a `texto` seguido de `"... "` (usa `+=`);
   - réstale 1.
4. Al salir del bucle, añade «¡Vacaciones!» a `texto` y escríbelo en `#cuenta`.
5. Prueba a empezar en 0. Explica en un comentario qué pasa y por qué.

**Resultado esperado:** empezando en 5, la página muestra «5... 4... 3... 2... 1... ¡Vacaciones!» y la consola, los números del 5 al 1. Empezando en 0, solo sale «¡Vacaciones!»: el bucle no da ninguna vuelta.

**Entrega:** `ejercicios-js/ej07-cuenta-atras/`.

> **Cuidado:** si te olvidas de restar 1, el bucle no termina nunca y la pestaña se queda colgada. Ciérrala, corrige el código y vuelve a abrirla.

**Ampliación opcional:** debajo, con otro `while`, calcula la suma de todos los números desde 1 hasta el número que haya escrito el usuario (con 5: 1 + 2 + 3 + 4 + 5 = 15).

---

## Ejercicio 8 — Adivina el número

**Objetivo:** usar el bucle `do...while` para repetir una pregunta hasta que el usuario acierte.

**HTML de partida:** crea la carpeta `ej08-adivina/`, copia este código en su `index.html` y crea `js/script.js` vacío.

```html
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Ejercicio 8 — Adivina el número</title>
</head>
<body>
  <h1>Adivina el número</h1>
  <p>He pensado un número del 1 al 10. ¿Lo adivinas?</p>
  <p id="resultado"></p>

  <script src="js/script.js"></script>
</body>
</html>
```

**Pasos:**

1. Declara una constante `SECRETO` con un número del 1 al 10 elegido por ti.
2. Declara una variable `intento` (sin valor) y otra `intentos` que empiece en 0.
3. Con un bucle `do...while`:
   - pide un número con `prompt()` y guárdalo (convertido) en `intento`;
   - suma 1 a `intentos`;
   - si `intento` es menor que `SECRETO`, muestra con `alert()` «Más alto»; si es mayor, «Más bajo».
   - Repite **mientras** `intento` sea distinto de `SECRETO` (`!==`).
4. Al salir del bucle, escribe en `#resultado` cuál era el número y en cuántos intentos se ha acertado.
5. Explica en un comentario por qué aquí es mejor `do...while` que `while`.

**Resultado esperado:** si el número secreto es 7 y se escribe 3, 9 y 7, salen las ventanas «Más alto» y «Más bajo», y la página muestra «¡Acertaste! Era el 7. Lo has conseguido en 3 intentos.».

**Entrega:** `ejercicios-js/ej08-adivina/`.

**Ampliación opcional:** haz que el número secreto cambie cada vez con `Math.floor(Math.random() * 10) + 1` (da un número al azar del 1 al 10).

---

## Ejercicio 9 — Tabla y playlist

**Objetivo:** repetir un número fijo de veces con `for` y recorrer un array con `for` y `length`.

**HTML de partida:** crea la carpeta `ej09-tablas/`, copia este código en su `index.html` y crea `js/script.js` vacío.

```html
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Ejercicio 9 — Tabla y playlist</title>
</head>
<body>
  <h1>Bucles for</h1>
  <h2 id="titulo-tabla">Tabla de multiplicar</h2>
  <ul id="tabla"></ul>

  <h2>Mi playlist</h2>
  <ol id="playlist"></ol>
  <p id="total"></p>

  <script src="js/script.js"></script>
</body>
</html>
```

**Pasos:**

**Parte A — Tabla de multiplicar**

1. Pide un número con `prompt()` y cambia el `#titulo-tabla` por «Tabla del *número*».
2. Declara una variable `filas` con una cadena vacía.
3. Con un `for` que vaya del 1 al 10, añade a `filas` en cada vuelta un elemento de lista con la operación, por ejemplo `"<li>7 × 3 = 21</li>"`.
4. Al terminar el bucle, escribe `filas` en la lista `#tabla` con `innerHTML`.

**Parte B — Playlist**

5. Crea un array `canciones` con al menos **cinco** canciones que te gusten.
6. Con un `for` que vaya de 0 hasta `canciones.length` (sin llegar), construye un `<li>` por canción y escribe el resultado en `#playlist`.
7. Escribe en `#total` cuántas canciones hay.
8. Añade una canción más al array y comprueba que aparece sin tocar el bucle.

**Resultado esperado:** con un 7, la página muestra «Tabla del 7» y una lista del «7 × 1 = 7» al «7 × 10 = 70». Debajo aparece la playlist numerada (es un `<ol>`) y el total de canciones.

**Entrega:** `ejercicios-js/ej09-tablas/`.

**Ampliación opcional:** muestra la tabla de multiplicar dentro de una `<table>` de HTML, con una fila `<tr>` por operación.

---

## Ejercicio 10 — Me gusta

**Objetivo:** crear funciones y ejecutarlas al pulsar botones con `onclick`, modificando la página con `innerHTML` y leyendo un campo con `.value`.

**HTML de partida:** crea la carpeta `ej10-me-gusta/`, copia este código en su `index.html` y crea `js/script.js` vacío. Fíjate en que cada botón ya llama a una función que todavía no existe: la tienes que crear tú.

```html
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Ejercicio 10 — Me gusta</title>
</head>
<body>
  <h1>Canción de la semana</h1>
  <article>
    <h2>Verano en la plaza</h2>
    <p>Los Recreos</p>
    <p>Me gusta: <span id="contador">0</span></p>
    <button onclick="sumar()">Me gusta</button>
    <button onclick="restar()">Quitar me gusta</button>
    <button onclick="reiniciar()">Reiniciar</button>
  </article>

  <h2>Propón una canción</h2>
  <p>
    <label for="cancion">Título de la canción:</label>
    <input type="text" id="cancion">
    <button onclick="proponer()">Proponer</button>
  </p>
  <p id="propuesta"></p>

  <script src="js/script.js"></script>
</body>
</html>
```

**Pasos:**

1. Declara, **fuera de las funciones**, una variable `meGusta` que empiece en 0.
2. Crea una función `mostrar()` que escriba el valor de `meGusta` en `#contador`.
3. Crea las funciones de los botones:
   - `sumar()`: suma 1 a `meGusta` y llama a `mostrar()`;
   - `restar()`: resta 1, **pero solo si** `meGusta` es mayor que 0, y llama a `mostrar()`;
   - `reiniciar()`: vuelve a poner `meGusta` a 0 y llama a `mostrar()`.
4. Crea la función `proponer()`: lee lo escrito en el campo `#cancion` con `.value` y escribe en `#propuesta` «Gracias. Has propuesto: *título*».
5. Escribe en un comentario por qué `meGusta` se declara fuera de las funciones.

**Resultado esperado:** cada clic en «Me gusta» sube el contador; «Quitar me gusta» lo baja, pero nunca por debajo de 0; «Reiniciar» lo deja en 0. Al escribir un título y pulsar «Proponer», aparece el mensaje debajo. Nada de esto recarga la página.

**Entrega:** `ejercicios-js/ej10-me-gusta/`.

**Ampliación opcional:** cuando el contador llegue a 10, muestra debajo «¡Canción del mes!». Si quieres, añade un contador de «Me gusta» a tu mini-sitio del ejercicio 10 de CSS.

---

[⬅ Volver a UT1](index.md) · [Ir a Instalación de VS Code](instalacion-vscode.md) · [Ir a HTML5](html.md) · [Ir a Prácticas de HTML5](practicas-html.md) · [Ir a Subir tus ejercicios a GitHub](github.md) · [Ir a CSS](css.md) · [Ir a Prácticas de CSS](practicas-css.md) · [Ir a JavaScript](javascript.md) · [Ir a Publicación web avanzada](publicacion-web.md)