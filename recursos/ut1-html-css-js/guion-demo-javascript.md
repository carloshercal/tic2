# Guion del ejemplo en directo: JavaScript («Viaje de fin de curso»), semana del 20 al 23 de octubre

> **Documento interno del profesor.** Va en `recursos/ut1-html-css-js/`. El código final y cada resultado esperado se han comprobado en Chromium, igual que los errores provocados.

## Resumen

| | |
|---|---|
| **Qué es** | La web del viaje de fin de curso de 2º de Bachillerato, con el HTML ya hecho. Cada sesión se le añade un bloque de JavaScript que rellena una parte de la página: bienvenida, presupuesto, destinos y «¿Puedes venir?». Sigue el orden de `javascript.md`. |
| **Duración** | 4 sesiones, de 20 a 30 min de demo en cada una. El resto de la sesión se dedica a los ejercicios de `practicas-js.md`. |
| **Dónde** | Repositorio `demo-profesor`, carpeta `ejercicios-js/demo-viaje/` (`index.html` + `js/script.js`). Un *commit* por bloque. |
| **Pantalla** | VS Code a la izquierda y, a la derecha, el navegador con Live Server y la **consola abierta** (F12 → Consola), todo visible en el proyector. |
| **Tema** | Es distinto del de los ejercicios (presentación, calculadora, semana, concierto, notas), así que lo que hace el alumnado no es copiar la demo. |

### Secuenciación de la semana

| Sesión | Fecha | Demo | Teoría (`javascript.md`) | Prácticas |
|---|---|---|---|---|
| 1 | Mar 20/10 | Bloque 1 (~20 min) | Inclusión de JavaScript, sintaxis, formas de mostrar datos | Ej. 1 — Hola, JavaScript |
| 2 | Mié 21/10 | Bloque 2 (~25 min) | Ventanas emergentes, variables y constantes, tipos de datos, concatenar | Ej. 2 — Preséntate |
| 3 | Jue 22/10 | Bloques 3 y 4 (~30 min) | Convertir texto en número, operadores aritméticos, de asignación e incremento, arrays | Ej. 3 — Calculadora y Ej. 4 — Mi semana |
| 4 | Vie 23/10 | Bloque 5 (~25 min) | Operadores de comparación y lógicos, `if`, `if`/`else`, `else if` | Ej. 5 — Entrada al concierto y Ej. 6 — Calificaciones |

- La sesión 3 es la más apretada. Si no da tiempo, el ejercicio 4 se termina en casa o se pasa al martes 27/10.
- La semana siguiente (bucles y funciones) se puede seguir con la misma página: los bloques 6 y 7 quedan por escribir.

### Antes de la sesión 1

1. En `demo-profesor`, crea `ejercicios-js/demo-viaje/` con el `index.html` de este guion y un `js/script.js` **vacío**.
2. Ábrelo con Live Server y comprueba que se ve la página sin contenido dinámico: el subtítulo dice «Página en construcción» y los párrafos están vacíos.
3. Haz *commit* («Demo JS: HTML de partida») y *push*.

### Ritmo de cada paso

1. Escribe el código **sin guardar**.
2. Pregunta: «¿Qué creéis que va a pasar?». Deja que respondan.
3. Guarda (`Ctrl + S`). Live Server recarga y el código vuelve a ejecutarse **desde el principio**: por eso las ventanas de `prompt()` vuelven a salir en cada guardado.
4. Comentad si acertaron. Las predicciones que suelen fallar van marcadas con ⚠️.

---

## HTML de partida

Cada `id` corresponde a un paso del guion. El `<script>` ya está al final del `<body>`. Durante la semana **no se toca el HTML**, salvo en la sesión 1, cuando se añade un script interno y se mueve el `<script>` para provocar el error A.

```html
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Viaje de fin de curso</title>
</head>
<body>
  <header>
    <h1>Viaje de fin de curso</h1>
    <p id="subtitulo">Página en construcción</p>
  </header>

  <main>
    <section>
      <h2>Bienvenida</h2>
      <p id="saludo"></p>
      <p id="datos"></p>
    </section>

    <section>
      <h2>Presupuesto</h2>
      <ul>
        <li>Alumnos: <span id="alumnos"></span></li>
        <li>Personas en total (con el profesorado): <span id="personas"></span></li>
        <li>Coste total (solo pagan los alumnos): <span id="total"></span> €</li>
        <li>Recaudado con la rifa y la lotería: <span id="recaudado"></span> €</li>
        <li>Precio final por alumno: <span id="precio-alumno"></span> €</li>
        <li>Alumnos sueltos al repartir habitaciones triples: <span id="sueltos"></span></li>
      </ul>
    </section>

    <section>
      <h2>Destinos</h2>
      <p id="destinos"></p>
      <p id="votado"></p>
      <p id="cambio"></p>
    </section>

    <section>
      <h2>¿Puedes venir?</h2>
      <p id="autorizacion"></p>
      <p id="asistencia"></p>
      <p id="plaza"></p>
      <p id="recordatorio"></p>
      <p id="descuento"></p>
      <p id="tarifa"></p>
    </section>
  </main>

  <footer>
    <button onclick="alert('Salida: lunes 12 de abril a las 7:00 desde la puerta del instituto')">Ver fecha de salida</button>
  </footer>

  <script src="js/script.js"></script>
</body>
</html>
```

> Antes de escribir código, recorre el HTML con la clase durante un minuto: «cada párrafo vacío con `id` es un hueco que va a rellenar JavaScript». Señala el `<script>` del final.

---

## Sesión 1 · Martes 20/10

Introducción (5 min, sin código): HTML es el esqueleto, CSS la piel y JavaScript el cerebro. JavaScript lo **interpreta el navegador**, y por eso no guarda nada en el servidor (eso lo hace PHP). Enseña la consola: F12 → Consola.

### Bloque 1 — Incluir JavaScript y mostrar datos (~20 min)

**Paso 1 · En línea**

Pulsa el botón «Ver fecha de salida» del pie, que ya está en el HTML.

- **Pregunta:** ¿dónde está el código que abre la ventana?
- **Resultado:** sale la ventana con la fecha de salida.
- **Comentario:** el código va en el atributo `onclick`. Fíjate en las comillas **simples** dentro de las dobles: si fueran dobles, cerrarían el atributo antes de tiempo. Es la forma «en línea»: útil para algo cortito, pero no para programar.

**Paso 2 · Interno**

En el HTML, justo **encima** del `<script src="js/script.js">`, añade:

```html
<script>
  alert("Hola desde el script interno");
</script>
```

- **Pregunta:** ¿cuándo sale esta ventana?
- **Resultado:** nada más cargar la página, sin pulsar nada. Mientras está abierta, la página no responde.
- **Comentario:** el código que no está dentro de un evento se ejecuta al cargar, de arriba abajo.

**Paso 3 · Externo**

En `js/script.js`:

```js
console.log("Hola desde script.js");
document.getElementById("subtitulo").innerHTML = "2º de Bachillerato · Curso 2026-27";
```

- **Pregunta:** ⚠️ ¿qué aparece antes, el `alert` del script interno o el subtítulo nuevo?
- **Resultado:** primero sale el `alert`. Mientras está abierto, el subtítulo sigue diciendo «Página en construcción». Al aceptarlo, cambia el subtítulo y en la consola aparece «Hola desde script.js».
- **Comentario:** el script interno está antes en el HTML, así que se ejecuta antes. `console.log()` no se ve en la página: es para nosotros, los programadores.

Borra el script interno del HTML: si no, el `alert` saldrá cada vez que guardes.

**Paso 4 · `document.write()`** (probar y borrar)

Añade al final de `script.js`:

```js
document.write("<p>Texto escrito con document.write</p>");
```

- **Pregunta:** ¿dónde aparece el párrafo?
- **Resultado:** al final de la página, debajo del botón, porque se escribe justo donde está el `<script>`.
- **Comentario:** no elegimos dónde escribe. Con `getElementById` + `innerHTML` decidimos qué hueco rellenar: es lo que usaremos siempre. Borra la línea.

**❌ Error provocado A — el `<script>` en el `<head>`**

Mueve `<script src="js/script.js"></script>` al `<head>` y guarda.

- **Resultado:** el subtítulo vuelve a «Página en construcción» y en la consola sale, en rojo, `Uncaught TypeError: Cannot set properties of null (setting 'innerHTML')`.
- **Explicación:** el script se ejecuta antes de que exista el párrafo `#subtitulo`, así que `getElementById` no encuentra nada (`null`). Haz clic en el enlace del error para ir a la línea. Vuelve a poner el `<script>` al final del `<body>`.

**❌ Error provocado B — mayúsculas**

Cambia `getElementById` por `getElementByID` y guarda.

- **Resultado:** `document.getElementByID is not a function`.
- **Explicación:** JavaScript distingue mayúsculas de minúsculas. Corrígelo.

> **Commit:** «Demo JS: incluir JavaScript y mostrar datos».
>
> **Al terminar:** ejercicio 1 de `practicas-js.md`.

---

## Sesión 2 · Miércoles 21/10

Repaso de dos minutos: «¿por qué el `<script>` va al final del `<body>`?».

### Bloque 2 — Ventanas emergentes, variables y concatenación (~25 min)

**Paso 5 · `prompt()` y una variable**

```js
// ---------- 2. Ventanas emergentes, variables y concatenación ----------

let nombre = prompt("¿Cómo te llamas?");
console.log(nombre);
```

- **Pregunta:** ¿dónde se guarda lo que escribo?
- **Resultado:** sale la ventana. Escribe «Lucía» y la consola muestra `Lucía`.
- **Comentario:** `let` crea una «caja» con nombre, `nombre`, y el `=` guarda dentro lo que devuelve `prompt()`. Recarga y pulsa **Cancelar**: la consola muestra `null`.

**Paso 6 · Constante y concatenación**

```js
const CURSO = "2º de Bachillerato";

document.getElementById("saludo").innerHTML = "Hola, " + nombre + ". Esta es la web del viaje de " + CURSO + ".";
```

- **Resultado:** «Hola, Lucía. Esta es la web del viaje de 2º de Bachillerato.».
- **Comentario:** con textos, el `+` **une**. Lo que va entre comillas sale tal cual; lo que va sin comillas es una variable y sale su valor.

**❌ Error provocado C — los espacios**

Quita el espacio de `"Hola, "` (que quede `"Hola,"`) y el de `" Esta es…"`.

- **Resultado:** «Hola,Lucía.Esta es la web…»: las palabras salen pegadas.
- **Explicación:** JavaScript no añade espacios por su cuenta: hay que ponerlos dentro de las comillas. Corrígelo.

**Paso 7 · `confirm()` y booleanos**

```js
let vienes = confirm("¿Vas a venir al viaje?");
document.getElementById("datos").innerHTML = "¿Vienes al viaje? " + vienes;
```

- **Pregunta:** ¿qué saldrá en la página si pulso Aceptar? ¿Y Cancelar?
- **Resultado:** `true` o `false`.
- **Comentario:** es un valor **booleano**. Mañana lo usaremos para tomar decisiones.

**Paso 8 · `typeof`**

```js
let edad = prompt("¿Cuántos años tienes?");

console.log(typeof nombre);
console.log(typeof vienes);
console.log(typeof edad);
```

- **Pregunta:** ⚠️ escribe 17 en la edad. ¿De qué tipo será `edad`?
- **Resultado:** `string`, `boolean` y **`string`**.
- **Comentario:** `prompt()` **siempre** devuelve texto, aunque escribas un número. Apúntalo en la pizarra: mañana nos va a dar un problema.

**Paso 9 · `let` o `const`**

Añade debajo:

```js
CURSO = "1º de Bachillerato";
```

- **Resultado:** `Uncaught TypeError: Assignment to constant variable.`, y todo lo que hay debajo de esa línea deja de ejecutarse.
- **Explicación:** una constante no puede cambiar. Pregunta por qué `nombre` va con `let` y `CURSO` con `const`. Deja la línea comentada, con el error copiado:

```js
// CURSO = "1º de Bachillerato";   // TypeError: Assignment to constant variable.
```

**Paso extra · `undefined`** (en la consola, sin guardar)

Escribe en la consola `let x;` y luego `x`: sale `undefined`, una variable declarada sin valor.

> **Commit:** «Demo JS: variables, ventanas y concatenación».
>
> **Al terminar:** ejercicio 2 de `practicas-js.md`.

---

## Sesión 3 · Jueves 22/10

### Paso 0 · Aparcar los `prompt` de ayer (~2 min)

Con tres ventanas en cada guardado, la demo se hace lenta. Sustituye cada `prompt()`/`confirm()` de la sesión 2 por un valor fijo y deja la ventana comentada:

```js
let nombre = "Lucía";                                   // prompt("¿Cómo te llamas?");
let vienes = true;                                      // confirm("¿Vas a venir al viaje?");
let edad = "17";                                        // prompt("¿Cuántos años tienes?");
```

- **Comentario:** es un truco habitual al programar: valores de prueba para no repetir lo mismo cada vez. Fíjate en que `edad` va entre comillas, porque es lo que devolvía `prompt()`.

### Bloque 3 — `Number()` y operadores (~15 min)

**Paso 10 · La suma que no suma**

```js
// ---------- 3. Number() y operadores ----------

let alumnos = prompt("¿Cuántos alumnos vienen?");
let profesores = prompt("¿Cuántos profesores acompañan?");
let personas = alumnos + profesores;

document.getElementById("alumnos").innerHTML = alumnos;
document.getElementById("personas").innerHTML = personas;
```

- **Pregunta:** ⚠️ 40 alumnos y 4 profesores. ¿Cuántas personas en total?
- **Resultado:** **404**. Siempre hay alguien que dice «¡error 404!».
- **Explicación:** son dos textos, `"40"` y `"4"`, y el `+` los une. Era lo que anotamos ayer en la pizarra.

**Paso 11 · `Number()`**

Cambia las dos primeras líneas:

```js
let alumnos = Number(prompt("¿Cuántos alumnos vienen?"));
let profesores = Number(prompt("¿Cuántos profesores acompañan?"));
```

- **Resultado:** 44 personas.
- **Comentario:** `Number()` convierte el texto en número. Prueba a escribir «cuarenta»: sale `NaN` (*Not a Number*).

**Paso 12 · Aritméticos**

```js
const PRECIO = 350;
let total = alumnos * PRECIO;

document.getElementById("total").innerHTML = total;
document.getElementById("sueltos").innerHTML = alumnos % 3;
```

- **Pregunta:** ¿qué hace el `%`?
- **Resultado:** 14000 € y 1 alumno suelto.
- **Comentario:** `%` es el **resto** de la división: 40 entre 3 da 13 habitaciones y sobra 1. Con 39 alumnos sobrarían 0.

> ⚠️ Si alguien pregunta: `"40" * 350` sí da 14000 aunque no se convierta, porque `*` solo sirve para números y JavaScript convierte por su cuenta. El problema es solo el `+`, que también sirve para unir textos. Por eso convertimos siempre.

**Paso 13 · Asignación y paréntesis**

```js
let recaudado = 0;
recaudado += 1200;                                      // rifa
recaudado += 800;                                       // lotería

let precioAlumno = (total - recaudado) / alumnos;

document.getElementById("recaudado").innerHTML = recaudado;
document.getElementById("precio-alumno").innerHTML = precioAlumno;
```

- **Resultado:** 2000 € recaudados y 300 € por alumno.
- **Comentario:** `+=` es «súmale a lo que ya tenía». Quita los paréntesis y pregunta qué sale: 14000 − 2000 / 40 = **13950**, porque la división va antes que la resta. Vuelve a ponerlos.

**Paso 14 · `++` y el orden de ejecución**

Al final del bloque, añade:

```js
profesores++;                                           // se apunta un profesor más
```

- **Pregunta:** ⚠️ ¿cuántas personas salen ahora?
- **Resultado:** **siguen saliendo 44**.
- **Explicación:** `personas` se calculó **antes**, cuando había 4 profesores, y no se recalcula sola. El código se ejecuta de arriba abajo. Mueve `profesores++;` justo **encima** de `let personas = …` y ya salen 45.

> **Commit:** «Demo JS: Number() y operadores».

### Bloque 4 — Arrays (~12 min)

**Paso 15 · Crear y leer un array**

```js
// ---------- 4. Arrays ----------

const destinos = ["Roma", "Lisboa", "Praga"];

document.getElementById("destinos").innerHTML = "Hay " + destinos.length + " destinos propuestos: " + destinos[0] + ", " + destinos[1] + " y " + destinos[2] + ".";
```

- **Pregunta:** ⚠️ si Roma es el primero, ¿qué número tiene?
- **Resultado:** «Hay 3 destinos propuestos: Roma, Lisboa y Praga.».
- **Comentario:** las posiciones **empiezan en 0**. `length` dice cuántos elementos hay (3), pero el último está en la posición 2.

**Paso 16 · Votar**

```js
let voto = Number(prompt("Vota: 1 = Roma, 2 = Lisboa, 3 = Praga"));
document.getElementById("votado").innerHTML = "Has votado: " + destinos[voto];
```

- **Pregunta:** ⚠️ voto 2. ¿Qué sale?
- **Resultado:** «Has votado: **Praga**». Vota 3: «Has votado: **undefined**».
- **Explicación:** las personas contamos desde 1 y el array desde 0. Corrígelo con `destinos[voto - 1]`: con 2 sale Lisboa.

**Paso 17 · Cambiar un elemento**

```js
destinos[2] = "Ámsterdam";
document.getElementById("cambio").innerHTML = "Praga sale de la lista. Último destino: " + destinos[destinos.length - 1];
```

- **Resultado:** «Praga sale de la lista. Último destino: Ámsterdam».
- **Comentario:** `destinos.length - 1` es siempre la última posición, haya los elementos que haya.

> ⚠️ Si alguien pregunta por qué se puede cambiar un `const`: `const` impide sustituir el array **entero** por otro (`destinos = […]` da error), pero sí deja cambiar lo que hay dentro. No hace falta profundizar más.

> **Commit:** «Demo JS: arrays».
>
> **Al terminar:** ejercicios 3 y 4 de `practicas-js.md`.

---

## Sesión 4 · Viernes 23/10

### Paso 0 · Recuperar y aparcar ventanas (~2 min)

Hoy hacen falta la edad y la asistencia de verdad, y no hacen falta los profesores ni el voto. Deja esas líneas así:

```js
let vienes = confirm("¿Vas a venir al viaje?");
let edad = Number(prompt("¿Cuántos años tienes?"));
// ...
let profesores = 4;                                     // Number(prompt("¿Cuántos profesores acompañan?"));
// ...
let voto = 2;                                           // Number(prompt("Vota: 1 = Roma, 2 = Lisboa, 3 = Praga"));
```

- **Comentario:** la edad ya lleva `Number()`, porque hoy la vamos a **comparar** con números. La consola dice ahora `number` en el `typeof` de la edad.

### Bloque 5 — Condicionales y operadores lógicos (~25 min)

Antes de escribir, prueba los operadores de comparación **en la consola** para calentar: `17 >= 18`, `40 === 40`, `5 == "5"` (`true`) frente a `5 === "5"` (`false`). Recomendación para la pizarra: comparar siempre con `===`.

**Paso 18 · `if` simple**

```js
// ---------- 5. Condicionales ----------

if (edad < 18) {
  document.getElementById("autorizacion").innerHTML = "Eres menor de edad: necesitas la autorización firmada.";
}
```

- **Pregunta:** ¿qué pasa si tengo 19 años?
- **Resultado:** con 17 sale el aviso. Con 19 **no pasa nada**: el párrafo se queda vacío.
- **Comentario:** el `if` sin `else` solo actúa cuando se cumple la condición.

**Paso 19 · `if` / `else`**

```js
if (vienes) {
  document.getElementById("asistencia").innerHTML = "¡Te esperamos, " + nombre + "!";
} else {
  document.getElementById("asistencia").innerHTML = "Te echaremos de menos, " + nombre + ".";
}
```

- **Resultado:** con Aceptar, «¡Te esperamos, Lucía!»; con Cancelar, «Te echaremos de menos, Lucía.».
- **Comentario:** `vienes` ya es `true` o `false`, así que no hace falta escribir `vienes === true`.

**Paso 20 · `&&` y `!`**

```js
let pagado = confirm("¿Has pagado la reserva?");

if (vienes && pagado) {
  document.getElementById("plaza").innerHTML = "Plaza confirmada.";
} else {
  document.getElementById("plaza").innerHTML = "Plaza sin confirmar.";
}

if (vienes && !pagado) {
  document.getElementById("recordatorio").innerHTML = "Recuerda pagar la reserva antes del 27 de noviembre.";
}
```

- **Pregunta:** dibuja en la pizarra la tabla de las cuatro combinaciones (viene/no viene × ha pagado/no ha pagado) y pide que predigan cada una antes de probarla.
- **Resultado:** solo «viene y ha pagado» confirma la plaza. El recordatorio sale **únicamente** con «viene y no ha pagado».
- **Comentario:** `!pagado` se lee «no ha pagado».

**Paso 21 · `||`, sin ventanas**

```js
let rifa = true;
let loteria = false;

if (rifa || loteria) {
  document.getElementById("descuento").innerHTML = "Has vendido rifa o lotería: tienes 20 € de descuento.";
} else {
  document.getElementById("descuento").innerHTML = "Sin descuento: todavía puedes vender rifa o lotería.";
}
```

- **Pregunta:** ¿qué valores tengo que poner para que salga «Sin descuento»?
- **Resultado:** solo con `false` y `false`. Cambia los valores en el código y guarda para comprobar las cuatro combinaciones.
- **Comentario:** con `||` basta con que se cumpla **una**.

**Paso 22 · `else if`**

```js
let precioGrupo;

if (alumnos >= 50) {
  precioGrupo = 280;
} else if (alumnos >= 40) {
  precioGrupo = 300;
} else if (alumnos >= 30) {
  precioGrupo = 330;
} else {
  precioGrupo = 350;
}

document.getElementById("tarifa").innerHTML = "Con " + alumnos + " alumnos, la agencia nos deja el viaje a " + precioGrupo + " € por persona.";
```

- **Pregunta:** ⚠️ con 52 alumnos se cumplen las tres condiciones (52 ≥ 50, ≥ 40 y ≥ 30). ¿Qué precio sale?
- **Resultado:** con 52, 280 €; con 40, 300 €; con 25, 350 €.
- **Explicación:** se comprueban **en orden** y solo se ejecuta el **primer** bloque que se cumple. Pregunta qué pasaría si `alumnos >= 30` fuera la primera condición: con 52 alumnos saldría 330 €.

**❌ Error provocado D — `=` en lugar de `===`**

Cambia la primera condición por `if (alumnos = 50)`, guarda y escribe 40 alumnos.

- **Resultado:** la tarifa dice «Con **50** alumnos… 280 €», aunque hemos escrito 40. En el presupuesto siguen saliendo 40, porque esas líneas se ejecutaron antes.
- **Explicación:** un solo `=` **guarda** 50 en `alumnos` en lugar de comparar, y la condición se da por cumplida. Vuelve a dejar `alumnos >= 50`.

> **Commit:** «Demo JS: condicionales». Haz *push* y enseña en github.com el historial de la semana: un *commit* por bloque.
>
> **Al terminar:** ejercicios 5 y 6 de `practicas-js.md`.

---

## `js/script.js` al final de la semana

Así queda el archivo tras la sesión 4, sin los errores provocados ni los pasos de probar y borrar. Es el código comprobado en el navegador.

```js
// Viaje de fin de curso — ejemplo en directo de JavaScript

// ---------- 1. Incluir JavaScript y mostrar datos ----------

console.log("Hola desde script.js");
document.getElementById("subtitulo").innerHTML = "2º de Bachillerato · Curso 2026-27";

// ---------- 2. Ventanas emergentes, variables y concatenación ----------

const CURSO = "2º de Bachillerato";
let nombre = "Lucía";                                   // prompt("¿Cómo te llamas?");
let vienes = confirm("¿Vas a venir al viaje?");
let edad = Number(prompt("¿Cuántos años tienes?"));

document.getElementById("saludo").innerHTML = "Hola, " + nombre + ". Esta es la web del viaje de " + CURSO + ".";
document.getElementById("datos").innerHTML = "¿Vienes al viaje? " + vienes;

console.log(typeof nombre);   // "string"
console.log(typeof vienes);   // "boolean"
console.log(typeof edad);     // "number" (en la sesión 2 era "string": aún no usábamos Number())

// CURSO = "1º de Bachillerato";   // TypeError: Assignment to constant variable.

// ---------- 3. Number() y operadores ----------

const PRECIO = 350;
let alumnos = Number(prompt("¿Cuántos alumnos vienen?"));
let profesores = 4;                                     // Number(prompt("¿Cuántos profesores acompañan?"));

profesores++;                                           // se apunta uno más: ANTES de calcular personas
let personas = alumnos + profesores;
let total = alumnos * PRECIO;

let recaudado = 0;
recaudado += 1200;                                      // rifa
recaudado += 800;                                       // lotería

let precioAlumno = (total - recaudado) / alumnos;

document.getElementById("alumnos").innerHTML = alumnos;
document.getElementById("personas").innerHTML = personas;
document.getElementById("total").innerHTML = total;
document.getElementById("recaudado").innerHTML = recaudado;
document.getElementById("precio-alumno").innerHTML = precioAlumno;
document.getElementById("sueltos").innerHTML = alumnos % 3;

// ---------- 4. Arrays ----------

const destinos = ["Roma", "Lisboa", "Praga"];
let voto = 2;                                           // Number(prompt("Vota: 1 = Roma, 2 = Lisboa, 3 = Praga"));

document.getElementById("destinos").innerHTML = "Hay " + destinos.length + " destinos propuestos: " + destinos[0] + ", " + destinos[1] + " y " + destinos[2] + ".";
document.getElementById("votado").innerHTML = "Has votado: " + destinos[voto - 1];

destinos[2] = "Ámsterdam";                              // se cambia un elemento (const no lo impide)
document.getElementById("cambio").innerHTML = "Praga sale de la lista. Último destino: " + destinos[destinos.length - 1];

// ---------- 5. Condicionales ----------

// Condicional simple
if (edad < 18) {
  document.getElementById("autorizacion").innerHTML = "Eres menor de edad: necesitas la autorización firmada.";
}

// Condicional doble
if (vienes) {
  document.getElementById("asistencia").innerHTML = "¡Te esperamos, " + nombre + "!";
} else {
  document.getElementById("asistencia").innerHTML = "Te echaremos de menos, " + nombre + ".";
}

// && y !
let pagado = confirm("¿Has pagado la reserva?");

if (vienes && pagado) {
  document.getElementById("plaza").innerHTML = "Plaza confirmada.";
} else {
  document.getElementById("plaza").innerHTML = "Plaza sin confirmar.";
}

if (vienes && !pagado) {
  document.getElementById("recordatorio").innerHTML = "Recuerda pagar la reserva antes del 27 de noviembre.";
}

// ||
let rifa = true;
let loteria = false;

if (rifa || loteria) {
  document.getElementById("descuento").innerHTML = "Has vendido rifa o lotería: tienes 20 € de descuento.";
} else {
  document.getElementById("descuento").innerHTML = "Sin descuento: todavía puedes vender rifa o lotería.";
}

// else if
let precioGrupo;

if (alumnos >= 50) {
  precioGrupo = 280;
} else if (alumnos >= 40) {
  precioGrupo = 300;
} else if (alumnos >= 30) {
  precioGrupo = 330;
} else {
  precioGrupo = 350;
}

document.getElementById("tarifa").innerHTML = "Con " + alumnos + " alumnos, la agencia nos deja el viaje a " + precioGrupo + " € por persona.";
```

## Resultado comprobado

Respuestas: Aceptar (viene), 17 años, 40 alumnos y Cancelar (no ha pagado).

| Parte de la página | Qué se ve |
|---|---|
| Subtítulo | 2º de Bachillerato · Curso 2026-27 |
| Bienvenida | Hola, Lucía. Esta es la web del viaje de 2º de Bachillerato. · ¿Vienes al viaje? true |
| Presupuesto | 40 alumnos · 45 personas · 14000 € · 2000 € recaudados · 300 € por alumno · 1 suelto |
| Destinos | Hay 3 destinos propuestos: Roma, Lisboa y Praga. · Has votado: Lisboa · Último destino: Ámsterdam |
| ¿Puedes venir? | Autorización (menor de edad) · ¡Te esperamos, Lucía! · Plaza sin confirmar. · Recordatorio de pago · 20 € de descuento · 300 € por persona |

Otros casos comprobados: 25 alumnos → 270 € por alumno y tarifa de 350 €; 52 alumnos → tarifa de 280 € (el precio por alumno sale 311.53846153846155: buen momento para comentar que los decimales largos se pueden redondear más adelante).

---

## Si algo se tuerce en directo

- **No pasa nada al guardar:** abre la consola. Un error en rojo **detiene todo lo que hay debajo**, aunque esté bien escrito. Haz clic en el enlace del error para ir a la línea.
- **Las ventanas no dejan trabajar:** aparca más `prompt()` con valores fijos, como en el paso 0.
- **Te has quedado sin saber qué se ha ejecutado:** añade `console.log()` con el valor de la variable sospechosa. Es la herramienta de depuración que queremos que copien.
- **Hay que volver atrás:** cada bloque tiene su *commit*. En VS Code, panel Source Control → *Discard Changes* para volver al último.
