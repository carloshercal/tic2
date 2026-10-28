# Soluciones — Prácticas de JavaScript (UT1)
> **Documento interno del profesor. No publicar** (va en `recursos/ut1-html-css-js/`, fuera de `docs/`).
>
> En los ejercicios 2 a 10 el alumnado parte del HTML que se da en el enunciado y no tiene que modificarlo: todo el trabajo va en `js/script.js`. Por eso, de esos ejercicios solo se incluye el `script.js`.
>
> Soluciones de referencia de `docs/ut1-html-css-js/practicas-js.md`. Todas se han ejecutado en Chromium con las respuestas indicadas en «Qué comprobar», y los resultados del enunciado salen de este mismo código.

## Ejercicio 1 — Hola, JavaScript

Carpeta: `ejercicios-js/ej01-hola-js/`

**`index.html`**

```html
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Ejercicio 1 — Hola, JavaScript</title>
</head>
<body>
  <h1>Hola, JavaScript</h1>
  <p id="demo">Este texto lo va a cambiar JavaScript.</p>

  <!-- 3. En línea: el código va en el atributo onclick -->
  <button onclick="alert('Has pulsado el botón')">Púlsame</button>

  <!-- 1. Interno: se ejecuta nada más cargar la página -->
  <script>
    alert("Hola desde JavaScript interno");
  </script>

  <!-- 2. Externo: al final del body, cuando el párrafo #demo ya existe -->
  <script src="js/script.js"></script>
  <!--
    ORDEN OBSERVADO:
    - Primero sale el alert del script interno, porque está antes en el HTML.
    - Al cerrarlo se ejecuta script.js: cambia el párrafo y escribe en la consola.
    - El alert del botón solo aparece al pulsarlo (es un evento).
  -->
</body>
</html>
```

**`js/script.js`**

```js
// Archivo externo del ejercicio 1
console.log("Hola desde el archivo script.js");           // solo se ve en la consola (F12)
console.log(5 + 6);                                        // 11

document.getElementById("demo").innerHTML = "Este párrafo lo ha escrito script.js. 5 + 6 = " + (5 + 6);
```

Qué comprobar: el `<script src>` va al final del `<body>` y la ruta incluye la carpeta `js/`. Comillas simples dentro del `onclick` (las dobles cierran el atributo). Ampliación: `document.write` añade el párrafo **al final** del contenido existente, porque el script se ejecuta mientras se carga la página, justo en ese punto.

## Ejercicio 2 — Preséntate

Carpeta: `ejercicios-js/ej02-presentacion/`

**`js/script.js`**

```js
// Constante: el curso no va a cambiar
const CURSO = "2º de Bachillerato";

// Variables: guardan lo que escribe el usuario
let nombre = prompt("¿Cómo te llamas?");
let localidad = prompt("¿De qué localidad eres?", "Mi pueblo");
let edad = prompt("¿Cuántos años tienes?");
let gustaMusica = confirm("¿Te gusta la música? (Aceptar = sí, Cancelar = no)");

// Concatenación con + (ojo a los espacios dentro de las comillas)
document.getElementById("saludo").innerHTML = "Hola, " + nombre + ". Estudias " + CURSO + " y tienes " + edad + " años.";
document.getElementById("localidad").innerHTML = "Vives en " + localidad + ".";
document.getElementById("musica").innerHTML = "¿Te gusta la música? " + gustaMusica;

// typeof: prompt devuelve texto aunque escribas un número
console.log(typeof edad);          // "string"
console.log(typeof gustaMusica);   // "boolean"

// Paso 6: si descomentas la línea siguiente, la consola muestra un error
// CURSO = "1º de Bachillerato";   // TypeError: Assignment to constant variable.
```

Qué comprobar (probado con Lucía / Navalmoral / 17 / Aceptar): «Hola, Lucía. Estudias 2º de Bachillerato y tienes 17 años.», «Vives en Navalmoral.» y «¿Te gusta la música? true». Consola: `string` y `boolean`. Error típico: olvidar los espacios dentro de las comillas («Hola,Lucía»). Ampliación: al cancelar, `prompt()` devuelve `null` y aparece «Hola, null».

## Ejercicio 3 — Calculadora

Carpeta: `ejercicios-js/ej03-calculadora/`

**`js/script.js`**

```js
// Paso 2 (prueba sin convertir): con 5 y 3, a + b daba "53" porque prompt devuelve texto.
// Number() convierte el texto en número para poder operar.
let a = Number(prompt("Escribe el primer número:"));
let b = Number(prompt("Escribe el segundo número:"));

document.getElementById("numeros").innerHTML = a + " y " + b;
document.getElementById("suma").innerHTML = a + b;
document.getElementById("resta").innerHTML = a - b;
document.getElementById("multiplicacion").innerHTML = a * b;
document.getElementById("division").innerHTML = a / b;
document.getElementById("resto").innerHTML = a % b;
document.getElementById("potencia").innerHTML = a ** 2;

// Operadores de asignación e incremento
let puntos = 10;
puntos += a;    // puntos = puntos + a
puntos *= 2;    // puntos = puntos * 2
puntos++;       // suma 1
document.getElementById("puntos").innerHTML = "Puntos finales: " + puntos;
// Con a = 5: (10 + 5) * 2 + 1 = 31
```

Qué comprobar (probado con 5 y 3): 8, 2, 15, 1.6666666666666667, 2, 25 y «Puntos finales: 31». En el paso 1 debe aparecer comentado el «53». Ampliación: con una letra sale `NaN` en todo; al dividir entre 0 sale `Infinity` (y el resto, `NaN`).

## Ejercicio 4 — Mi semana

Carpeta: `ejercicios-js/ej04-mi-semana/`

**`js/script.js`**

```js
// Dos arrays "paralelos": la posición 0 de uno va con la posición 0 del otro
const dias = ["Lunes", "Martes", "Miércoles", "Jueves", "Viernes", "Sábado", "Domingo"];
const planes = ["Entreno de baloncesto", "Clase de guitarra", "Biblioteca", "Entreno de baloncesto", "Cine con amigos", "Partido", "Descanso"];

document.getElementById("total").innerHTML = "La semana tiene " + dias.length + " días.";
document.getElementById("primero").innerHTML = "El " + dias[0] + " toca: " + planes[0] + ".";

// El usuario escribe del 1 al 7, pero las posiciones van del 0 al 6: restamos 1
let numero = Number(prompt("Escribe un número de día (1 = lunes, 7 = domingo):"));
document.getElementById("elegido").innerHTML = "El " + dias[numero - 1] + " toca: " + planes[numero - 1] + ".";

// Modificar un elemento del array
planes[6] = "Hacer los deberes de TIC";
document.getElementById("cambio").innerHTML = "Cambio de planes: el " + dias[6] + " toca: " + planes[6] + ".";

// Paso 6: con 8, dias[7] no existe y sale "undefined"
```

Qué comprobar (probado con 3 y con 8): con 3, «El Miércoles toca: Biblioteca.»; con 8, «El undefined toca: undefined.». Error típico: escribir `dias[numero]` sin restar 1 (con un 3 sale el jueves). Ampliación: `dias[dias.length - 1]` → «Domingo».

## Ejercicio 5 — Entrada al concierto

Carpeta: `ejercicios-js/ej05-concierto/`

**`js/script.js`**

```js
let edad = Number(prompt("¿Cuántos años tienes?"));
let tieneEntrada = confirm("¿Has reservado entrada? (Aceptar = sí)");
let tieneCarne = confirm("¿Tienes el carné del instituto? (Aceptar = sí)");

// Condicional doble con && : hay que cumplir LAS DOS condiciones
if (edad >= 16 && tieneEntrada) {
  document.getElementById("acceso").innerHTML = "Puedes pasar al concierto.";
} else {
  document.getElementById("acceso").innerHTML = "Lo siento, no puedes pasar.";
}

// Condicional doble con || : basta con cumplir UNA de las dos
if (tieneCarne || edad < 18) {
  document.getElementById("precio").innerHTML = "Tu entrada cuesta 5 €.";
} else {
  document.getElementById("precio").innerHTML = "Tu entrada cuesta 8 €.";
}

// Condicional simple: solo hace algo si se cumple
if (edad < 16) {
  document.getElementById("aviso").innerHTML = "Te faltan " + (16 - edad) + " años para poder entrar.";
}
```

Qué comprobar (probados los tres casos del enunciado): 17 + entrada + sin carné → pasa, 5 €; 14 + entrada + carné → no pasa, 5 €, «Te faltan 2 años para poder entrar.»; 20 sin entrada ni carné → no pasa, 8 €. Error típico: `16 - edad` sin paréntesis dentro de la concatenación (`"Te faltan " + 16 - edad` da `NaN`). Ampliación:

```js
if (!tieneEntrada) {
  document.getElementById("aviso").innerHTML += " Reserva tu entrada en conserjería.";
}
```

## Ejercicio 6 — Calificaciones

Carpeta: `ejercicios-js/ej06-notas/`

**`js/script.js`**

```js
let nota = Number(prompt("Escribe tu nota (de 0 a 10):"));
let calificacion;

// Primero descartamos las notas imposibles con ||
if (nota < 0 || nota > 10) {
  calificacion = "Nota no válida";
} else if (nota < 5) {      // se comprueban en orden: aquí ya sabemos que nota >= 0
  calificacion = "Insuficiente";
} else if (nota < 6) {
  calificacion = "Suficiente";
} else if (nota < 7) {
  calificacion = "Bien";
} else if (nota < 9) {
  calificacion = "Notable";
} else {
  calificacion = "Sobresaliente";
}

document.getElementById("resultado").innerHTML = "Nota: " + nota + " → " + calificacion;
```

Qué comprobar (probado con 4, 7.5, 9 y 11): Insuficiente, Notable, Sobresaliente y Nota no válida. El comentario del paso 5 debe explicar que, si se llega a ese `else if`, las condiciones anteriores han sido falsas, así que ya se sabe que la nota es mayor o igual que 5. Error típico: escribir la coma decimal (`7,5`) → `NaN`, que no cumple ninguna comparación y acaba en «Sobresaliente»; buen momento para comentarlo en clase. Ampliación:

```js
let n1 = Number(prompt("Primera nota:"));
let n2 = Number(prompt("Segunda nota:"));
let n3 = Number(prompt("Tercera nota:"));
let media = (n1 + n2 + n3) / 3;
```

## Ejercicio 7 — Cuenta atrás

Carpeta: `ejercicios-js/ej07-cuenta-atras/`

**`js/script.js`**

```js
let cuentaAtras = Number(prompt("¿Desde qué número empezamos la cuenta atrás?", "10"));
let texto = "";   // aquí iremos acumulando los números

while (cuentaAtras > 0) {
  console.log(cuentaAtras);
  texto += cuentaAtras + "... ";   // texto = texto + cuentaAtras + "... "
  cuentaAtras--;                   // sin esta línea, el bucle no termina nunca
}

texto += "¡Vacaciones!";
document.getElementById("cuenta").innerHTML = texto;
// Paso 4: con 0 (o un número negativo) la condición es falsa desde el principio:
// el bucle no da ninguna vuelta y solo se ve "¡Vacaciones!".
```

Qué comprobar (probado con 5 y con 0): «5... 4... 3... 2... 1... ¡Vacaciones!» y, con 0, solo «¡Vacaciones!». Ampliación:

```js
let limite = 5;   // o el número que escribió el usuario, guardado antes del bucle
let i = 1;
let suma = 0;
while (i <= limite) {
  suma += i;
  i++;
}
// suma vale 15
```

Ojo: para la ampliación hay que guardar el número del usuario en otra variable **antes** del primer bucle, porque `cuentaAtras` acaba valiendo 0.

## Ejercicio 8 — Adivina el número

Carpeta: `ejercicios-js/ej08-adivina/`

**`js/script.js`**

```js
const SECRETO = 7;
let intento;
let intentos = 0;

// do...while: hay que preguntar al menos una vez, así que la condición va al final
do {
  intento = Number(prompt("Escribe un número del 1 al 10:"));
  intentos++;

  if (intento < SECRETO) {
    alert("Más alto");
  } else if (intento > SECRETO) {
    alert("Más bajo");
  }
} while (intento !== SECRETO);   // se repite mientras NO acierte

document.getElementById("resultado").innerHTML = "¡Acertaste! Era el " + SECRETO + ". Lo has conseguido en " + intentos + " intentos.";
```

Qué comprobar (probado con 3, 9 y 7): «Más alto», «Más bajo» y «Lo has conseguido en 3 intentos.». Con `do...while` la pregunta se hace al menos una vez sin tener que repetir el `prompt()` antes del bucle. Aviso: si pulsan Cancelar, `Number(null)` vale 0 y el juego sigue preguntando; para salir hay que acertar (o cerrar la pestaña). Ampliación: `const SECRETO = Math.floor(Math.random() * 10) + 1;`.

## Ejercicio 9 — Tabla y playlist

Carpeta: `ejercicios-js/ej09-tablas/`

**`js/script.js`**

```js
// ---- Parte A: tabla de multiplicar ----
let numero = Number(prompt("¿Qué tabla de multiplicar quieres ver?"));
document.getElementById("titulo-tabla").innerHTML = "Tabla del " + numero;

let filas = "";
for (let i = 1; i <= 10; i++) {          // de 1 a 10: diez vueltas
  filas += "<li>" + numero + " × " + i + " = " + numero * i + "</li>";
}
document.getElementById("tabla").innerHTML = filas;

// ---- Parte B: recorrer un array ----
const canciones = ["Luces de la ciudad", "Camino de vuelta", "Verano en la plaza", "Domingo lento", "Aula 12"];

let lista = "";
for (let i = 0; i < canciones.length; i++) {   // de 0 a length - 1
  lista += "<li>" + canciones[i] + "</li>";
}
document.getElementById("playlist").innerHTML = lista;
document.getElementById("total").innerHTML = "Total: " + canciones.length + " canciones.";
```

Qué comprobar (probado con 7): diez filas del «7 × 1 = 7» al «7 × 10 = 70» y la playlist con 5 canciones. Error típico: escribir `innerHTML =` **dentro** del bucle en lugar de `+=` sobre la variable, de modo que solo se ve la última fila. Otro: `i <= canciones.length`, que añade un `undefined` al final. Ampliación: igual que la parte A, pero construyendo `"<tr><td>" + numero + " × " + i + "</td><td>" + numero * i + "</td></tr>"` y escribiéndolo en un `<table>`.

## Ejercicio 10 — Me gusta

Carpeta: `ejercicios-js/ej10-me-gusta/`

**`js/script.js`**

```js
// Variable fuera de las funciones: así conserva su valor entre clic y clic
let meGusta = 0;

// Función auxiliar: escribe el valor actual en la página
function mostrar() {
  document.getElementById("contador").innerHTML = meGusta;
}

function sumar() {
  meGusta++;
  mostrar();
}

function restar() {
  if (meGusta > 0) {   // no dejamos que baje de 0
    meGusta--;
  }
  mostrar();
}

function reiniciar() {
  meGusta = 0;
  mostrar();
}

function proponer() {
  let titulo = document.getElementById("cancion").value;   // .value: lo escrito en el campo
  document.getElementById("propuesta").innerHTML = "Gracias. Has propuesto: " + titulo;
}
```

Qué comprobar (probado: 3 clics en «Me gusta» y 1 en «Quitar» → 2; «Reiniciar» y «Quitar» → 0; propuesta «Domingo lento» mostrada): el contador nunca baja de 0. Si declaran `let meGusta = 0;` **dentro** de `sumar()`, el contador no acumula los clics (se queda en 0 o en 1, según cómo lo hayan escrito), porque la variable se crea de nuevo en cada clic: es la explicación que se pide en el paso 5. Error típico: nombre de la función distinto del que pone el `onclick` (por ejemplo `Sumar()`) → en la consola, «sumar is not defined». Ampliación, dentro de `mostrar()`:

```js
if (meGusta >= 10) {
  document.getElementById("contador").innerHTML = meGusta + " · ¡Canción del mes!";
}
```