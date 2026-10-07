---
title: UT1 — JavaScript
---

# JavaScript — Interactividad

**JavaScript** es un lenguaje de programación que se ejecuta en el navegador y permite dar comportamiento a una página web. Mientras que HTML **estructura** y CSS da **estilo**, JavaScript **programa** lo que pasa en la página.

Con JavaScript podemos:

- Modificar el contenido de la página sin recargarla.
- Validar los datos de un formulario antes de enviarlo.
- Conseguir efectos gráficos y reaccionar a lo que hace el usuario (pulsar un botón, escribir en un campo…).

JavaScript es un lenguaje **interpretado**: el navegador lee el código y lo ejecuta directamente, sin compilarlo antes. Por eso se dice que es un lenguaje de *script* **del navegador** (o del lado del cliente).

> **Lo que JavaScript no hace (en el navegador):** no guarda datos en una base de datos del servidor. Para eso se usan lenguajes que se ejecutan **en el servidor**, como PHP.

## Inclusión de JavaScript en una página

Al igual que ocurre con CSS, el código JavaScript se puede incluir de tres formas:

1. **Externa** (recomendada): en un archivo `.js` independiente, enlazado con la etiqueta `<script>`. En la plantilla de ejercicios, el archivo va en la carpeta `js/`.

   ```html
   <script src="js/script.js"></script>
   ```

2. **Interna**: dentro de una etiqueta `<script>` en el propio documento HTML.

   ```html
   <script>
     alert("Hola desde JavaScript");
   </script>
   ```

3. **En línea**: como valor de un atributo de evento de un elemento HTML (por ejemplo `onclick`).

   ```html
   <button onclick="alert('Hola')">Púlsame</button>
   ```

**¿Dónde se pone el `<script>`?** En esta unidad lo pondremos **al final del `<body>`**, justo antes de `</body>`. Así, cuando el código se ejecuta, todos los elementos de la página ya existen y podemos modificarlos.

```html
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <title>Mi primer JavaScript</title>
</head>
<body>
  <p id="demo">Hola, mundo</p>

  <script src="js/script.js"></script>
</body>
</html>
```

> En ejemplos antiguos verás `<script type="text/javascript" ...>`. En HTML5 el atributo `type` ya no hace falta.

## Reglas básicas de sintaxis

- Cada instrucción (sentencia) termina, por convención, con punto y coma `;`.
- Se ignoran los espacios en blanco y los saltos de línea de más: úsalos para que el código se lea bien.
- Distingue mayúsculas de minúsculas (*case sensitive*): `nombre` y `Nombre` son cosas distintas.
- No hace falta indicar el tipo de dato de una variable: JavaScript lo deduce del valor.
- Los bloques de código se delimitan con llaves `{ }`.
- Los comentarios se escriben con `//` (una línea) o `/* ... */` (varias líneas).
- Las sentencias se ejecutan **en el orden en que aparecen**, de arriba abajo:

```js
document.write("<h1>Esto es una cabecera H1</h1>");   // se ejecuta primero
document.write("<p>Esto es un párrafo</p>");          // se ejecuta después
```

A veces no queremos que el código se ejecute nada más cargar la página, sino **cuando ocurra algo** (un **evento**), por ejemplo, cuando el usuario pulse un botón. Lo veremos en el apartado [Funciones y eventos](#funciones-y-eventos).

## Formas de mostrar datos

JavaScript puede mostrar datos de varias maneras:

- **Escribir en un elemento HTML**, usando `innerHTML` junto con `document.getElementById(id)` para localizar ese elemento por su atributo `id`.
- **Escribir en la salida del documento**, usando `document.write()`.
- **Escribir en un cuadro de alerta**, usando `window.alert()` (o simplemente `alert()`).
- **Escribir en la consola del navegador**, usando `console.log()`. Es muy útil para buscar errores, porque no interrumpe la página como `alert()`.

```html
<p id="demo"></p>
<script>
  document.getElementById("demo").innerHTML = 5 + 6;   // escribe "11" dentro del párrafo
</script>
```

```js
document.write(5 + 6);   // escribe "11" en el propio documento
alert(5 + 6);            // muestra "11" en una ventana emergente
console.log(5 + 6);      // muestra "11" en la consola (F12 → pestaña Consola)
```

> La consola (**F12 → Consola**) es también donde el navegador te avisa de los **errores** de tu código, en rojo y con el número de línea. Tenla siempre abierta mientras programas.

## Ventanas emergentes

JavaScript tiene tres funciones para comunicarse con el usuario mediante ventanas emergentes:

| Función | Qué muestra | Qué devuelve |
|---|---|---|
| `alert(mensaje)` | Un mensaje y el botón **Aceptar** | Nada |
| `confirm(mensaje)` | Un mensaje y los botones **Aceptar** y **Cancelar** | `true` (Aceptar) o `false` (Cancelar) |
| `prompt(mensaje, valorInicial)` | Un mensaje y una caja de texto | El **texto** escrito, o `null` si se pulsa Cancelar |

```js
alert("Hola, mundo");
let seguir = confirm("¿Deseas continuar?");
let edad = prompt("¿Cuántos años tienes?", "Introduce tus años");
```

## Variables y constantes

Una **variable** es un espacio con nombre donde guardamos un valor para usarlo después. Se declaran con `let` y su valor puede cambiar:

```js
let numero = 5;      // declarar e inicializar
numero = 8;          // cambiar su valor (sin let)

let numero1, numero2 = 1;   // varias a la vez: numero1 queda sin valor (undefined)
numero1 = 2;
```

Una **constante** se declara con `const` y su valor **no puede cambiar**. Si se intenta, da error:

```js
const PI = 3.1416;
PI = 3;   // ❌ TypeError: Assignment to constant variable.
```

> En código antiguo verás variables declaradas con `var`. Funciona, pero hoy se usa `let`. En TIC II usaremos siempre `let` y `const`.

**Nombres de variables:** sin espacios ni tildes, no pueden empezar por un número y se suelen escribir en *camelCase* (la primera palabra en minúscula y las siguientes empezando por mayúscula): `nombreAlumno`, `notaFinal`, `cuentaAtras`.

## Tipos de datos

Los tipos de datos de JavaScript se dividen en **primitivos** (un único valor simple) y **no primitivos** (estructuras más complejas).

| Tipo | Ejemplo | Para qué |
|---|---|---|
| **Number** | `42`, `3.14` | Números enteros y decimales (el decimal se escribe con punto) |
| **String** | `"Hola"`, `'Hola'` | Textos (cadenas de caracteres), siempre entre comillas |
| **Boolean** | `true`, `false` | Verdadero o falso |
| **undefined** | `let x;` | Variable declarada pero sin valor |
| **null** | `let x = null;` | Ausencia de valor puesta a propósito |
| **Array** *(no primitivo)* | `["rojo", "verde"]` | Lista de valores |
| **Object** *(no primitivo)* | — | Estructura más compleja (no lo veremos en esta unidad) |

> Existen otros tipos menos usados (`BigInt` para números enormes, `Symbol`…) que no necesitamos en esta unidad.

Para saber de qué tipo es un valor, usa `typeof`:

```js
console.log(typeof 42);       // "number"
console.log(typeof "42");     // "string"  ← ¡ojo, entre comillas es texto!
console.log(typeof true);     // "boolean"
```

## Unir textos (concatenar)

El operador `+` con textos **une** (concatena) las cadenas. Es la forma de construir mensajes con variables:

```js
let nombre = "Lucía";
let curso = "2º de Bachillerato";

alert("Hola, " + nombre + ". Estás en " + curso + ".");
// Hola, Lucía. Estás en 2º de Bachillerato.
```

Fíjate en los **espacios** dentro de las comillas: si no los pones, las palabras salen pegadas.

## Convertir texto en número

`prompt()` **siempre devuelve texto**, aunque el usuario escriba un número. Y si sumamos dos textos con `+`, se **unen** en vez de sumarse:

```js
let a = prompt("Primer número:");    // el usuario escribe 5 → a vale "5"
let b = prompt("Segundo número:");   // el usuario escribe 3 → b vale "3"
alert(a + b);                         // "53" ❌
```

Para operar con ellos, hay que convertirlos con `Number()`:

```js
let a = Number(prompt("Primer número:"));
let b = Number(prompt("Segundo número:"));
alert(a + b);                         // 8 ✅
```

Si el texto no es un número (por ejemplo `"hola"`), `Number()` devuelve `NaN` (*Not a Number*, «no es un número»).

## Arrays

Un **array** es una colección de valores guardados en una sola variable. En lugar de esto:

```js
const dia1 = "Lunes";
const dia2 = "Martes";
// ...
const dia7 = "Domingo";
```

escribimos:

```js
const dias = ["Lunes", "Martes", "Miércoles", "Jueves", "Viernes", "Sábado", "Domingo"];
```

Cada elemento tiene una **posición** (índice), que **empieza en 0**:

```js
let diaSeleccionado = dias[0];   // "Lunes"
let otroDia = dias[3];           // "Jueves"
console.log(dias.length);        // 7 (número de elementos)

let colores = ["rojo", "verde", "azul"];
colores[1] = "amarillo";         // cambia el segundo elemento → ["rojo", "amarillo", "azul"]
```

El último elemento está siempre en la posición `length - 1`.

## Operadores

Los operadores sirven para asignar valores a las variables, hacer operaciones matemáticas y comparar valores.

### Aritméticos

| Operador | Nombre | Ejemplo (`a = 10`, `b = 3`) |
|---|---|---|
| `+` | Suma | `a + b` → `13` |
| `-` | Resta | `a - b` → `7` |
| `*` | Multiplicación | `a * b` → `30` |
| `/` | División | `a / b` → `3.333…` |
| `%` | Módulo (resto de la división) | `a % b` → `1` |
| `**` | Potencia | `a ** 2` → `100` |

```js
let numero1 = 10;
let numero2 = 5;
let resultado = numero1 / numero2;   // 2
resultado = 3 + numero1;             // 13
resultado = (numero1 + numero2) * 2; // 30: los paréntesis se calculan primero
```

> El módulo `%` es muy útil para saber si un número es **par**: `numero % 2` vale `0` si es par.

### De asignación

| Operador | Equivale a |
|---|---|
| `a = b` | Guarda en `a` el valor de `b` |
| `a += b` | `a = a + b` |
| `a -= b` | `a = a - b` |
| `a *= b` | `a = a * b` |
| `a /= b` | `a = a / b` |
| `a %= b` | `a = a % b` |

```js
let puntos = 10;
puntos += 5;   // puntos vale 15
```

### Incremento y decremento

`a++` suma 1 a la variable y `a--` le resta 1. Se usan mucho en los bucles.

```js
let contador = 0;
contador++;   // contador vale 1
contador--;   // contador vale 0
```

> También existen `++a` y `--a` (preincremento y predecremento). La diferencia con `a++` solo se nota si los usas dentro de otra operación: `++a` suma **antes** de usar el valor y `a++`, **después**. Para empezar, úsalos siempre solos en su línea y no habrá diferencia. El signo `-` delante de una variable (`-a`) le cambia el signo.

### De comparación

Comparan dos valores y devuelven `true` o `false`:

| Operador | Significado |
|---|---|
| `==` | Igual valor (no comprueba el tipo) |
| `===` | Igual valor **y** igual tipo |
| `!=` | Distinto valor |
| `!==` | Distinto valor o distinto tipo |
| `>` `<` | Mayor que, menor que |
| `>=` `<=` | Mayor o igual que, menor o igual que |

```js
let a = 5;
let b = "5";
a == b;    // true  (mismo valor)
a === b;   // false (distinto tipo: number y string)
```

> No confundas `=` (asignar un valor) con `==` o `===` (comparar). Recomendación: compara siempre con `===`.

### Lógicos

Combinan varias condiciones:

| Operador | Nombre | Devuelve `true` si… |
|---|---|---|
| `&&` | Y (AND) | **las dos** condiciones son verdaderas |
| <code>&#124;&#124;</code> | O (OR) | **alguna** de las condiciones es verdadera |
| `!` | NO (NOT) | la condición es falsa (le da la vuelta) |

```js
true && true     // true
true && false    // false
true || false    // true
false || false   // false
!true            // false

let edad = 17;
let tieneEntrada = true;
edad >= 16 && tieneEntrada;   // true: cumple las dos
```

## Estructuras de control

Hasta ahora, el código se ejecuta línea a línea, de arriba abajo. Las **estructuras de control** alteran ese orden: permiten **tomar decisiones** (condicionales) y **repetir** un bloque de instrucciones (bucles).

### Condicional simple: `if`

Ejecuta el bloque **solo si** se cumple la condición:

```js
let nota = 9;

if (nota >= 9) {
  alert("¡Enhorabuena, sobresaliente!");
}
```

### Condicional doble: `if` / `else`

Ejecuta un bloque si se cumple la condición y **otro** si no se cumple:

```js
let edad = 18;

if (edad >= 18) {
  alert("Eres mayor de edad");
} else {
  alert("Todavía eres menor de edad");
}
```

### Condicional múltiple: `else if`

Cuando hay más de dos casos, se encadenan condiciones. Se comprueban **en orden** y solo se ejecuta el primer bloque que se cumple:

```js
let nota = 7;

if (nota < 5) {
  alert("Insuficiente");
} else if (nota < 7) {
  alert("Suficiente o Bien");
} else if (nota < 9) {
  alert("Notable");
} else {
  alert("Sobresaliente");
}
```

### Bucle `while` (mientras… hacer)

Repite el bloque **mientras** se cumpla la condición. La condición se comprueba **antes** de cada vuelta, así que puede que el bloque no se ejecute nunca:

```js
let cuentaAtras = 10;          // iniciamos la variable fuera del bucle

while (cuentaAtras > 0) {      // mientras sea mayor que 0
  console.log(cuentaAtras);    // mostramos su valor en cada vuelta
  cuentaAtras--;               // restamos 1 (si no, el bucle no acabaría nunca)
}

console.log("¡Despegue!");
```

### Bucle `do...while` (hacer… mientras)

Igual que `while`, pero la condición se comprueba **después** de cada vuelta, así que el bloque se ejecuta **al menos una vez**. Es ideal para preguntar algo al usuario hasta que responda lo que esperamos:

```js
let respuesta;

do {
  respuesta = confirm("¿Te gusta JavaScript?");
} while (respuesta);   // se repite mientras pulse Aceptar (true)
```

### Bucle `for`

Se usa cuando sabemos **cuántas veces** queremos repetir. Reúne en una línea la inicialización, la condición y la actualización:

```js
// for (inicialización; condición; actualización) { ... }
for (let i = 0; i < 5; i++) {
  console.log("Vuelta número " + i);   // de 0 a 4: cinco vueltas
}
```

Combinado con `length`, el `for` permite **recorrer un array**:

```js
const asignaturas = ["TIC II", "Matemáticas", "Historia", "Inglés"];

for (let i = 0; i < asignaturas.length; i++) {
  console.log(asignaturas[i]);
}
```

## Funciones y eventos

Una **función** es un bloque de código con nombre que **no se ejecuta hasta que se la llama**. Se define con `function`:

```js
function saludar() {
  alert("¡Hola!");
}

saludar();   // ahora sí se ejecuta
```

Un **evento** es algo que ocurre en la página: pulsar un botón, pasar el ratón por encima, etc. Con el atributo `onclick` hacemos que un botón llame a una función al pulsarlo. Dentro de la función, `document.getElementById()` localiza un elemento por su `id`:

- `.innerHTML` lee o cambia el **contenido** de un elemento.
- `.value` lee lo que el usuario ha escrito en un **campo de formulario** (siempre como texto).

```html
<label for="nombre">Tu nombre:</label>
<input type="text" id="nombre">
<button onclick="saludar()">Saludar</button>
<p id="mensaje"></p>

<script>
  function saludar() {
    let nombre = document.getElementById("nombre").value;
    document.getElementById("mensaje").innerHTML = "¡Hola, " + nombre + "!";
  }
</script>
```

Al pulsar el botón, el párrafo muestra el saludo **sin recargar la página**.

## Errores frecuentes

- **El código no hace nada.** Abre la consola (**F12 → Consola**): el error aparece en rojo con el archivo y la línea. Revisa también que la ruta del `<script src="js/script.js">` sea correcta.
- **`Cannot set properties of null`.** `getElementById` no encuentra el elemento: el `id` está mal escrito (distingue mayúsculas) o el `<script>` está en el `<head>`, antes de que exista el elemento. Ponlo al final del `<body>`.
- **`5 + 3` da `53`.** Los valores vienen de `prompt()` o de `.value` y son texto. Conviértelos con `Number()`.
- **`NaN` como resultado.** Has convertido con `Number()` algo que no es un número (letras, una coma decimal en vez de punto, o se ha pulsado Cancelar en un sitio donde se esperaba otro dato).
- **Usar `=` en una condición.** `if (nota = 10)` **asigna** 10 a `nota` en lugar de comparar. Se escribe `if (nota === 10)`.
- **Bucle infinito (la página se queda colgada).** Se te ha olvidado actualizar la variable de la condición (`i++`, `cuentaAtras--`…). Cierra la pestaña y corrígelo.
- **`undefined` al leer un array.** Te has salido de las posiciones: el primer elemento es `[0]` y el último `[length - 1]`.
- **`Assignment to constant variable`.** Intentas cambiar una variable declarada con `const`. Si su valor tiene que cambiar, decláralo con `let`.
- **Textos sin comillas o comillas que no cierran.** `alert(Hola)` busca una variable llamada `Hola`; se escribe `alert("Hola")`. Si el texto lleva comillas dobles dentro, envuélvelo con simples: `'Dijo "hola"'`.
- **Mayúsculas.** `Alert()`, `Console.log()` o `document.getElementByID()` no existen: se escriben `alert()`, `console.log()` y `document.getElementById()`.

---

[⬅ Volver a UT1](index.md) · [Ir a Instalación de VS Code](instalacion-vscode.md) · [Ir a HTML5](html.md) · [Ir a Prácticas de HTML5](practicas-html.md) · [Ir a Subir tus ejercicios a GitHub](github.md) · [Ir a CSS](css.md) · [Ir a Prácticas de CSS](practicas-css.md) · [Ir a Prácticas de JavaScript](practicas-js.md) · [Ir a Publicación web avanzada](publicacion-web.md)