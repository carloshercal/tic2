---
title: UT1 — JavaScript
---

# JavaScript — Interactividad

**JavaScript** es un lenguaje de programación que se ejecuta en el navegador y permite dotar de comportamiento dinámico a una página web: reaccionar a acciones del usuario, validar formularios, modificar el contenido sin recargar la página, etc. Mientras que HTML estructura y CSS da estilo, JavaScript **programa** el comportamiento.

## Inclusión de JavaScript en una página

Al igual que ocurre con CSS, el código JavaScript se puede incluir de tres formas:

1. **Externa** (recomendada): en un archivo `.js` independiente, enlazado con la etiqueta `<script>`.

   ```html
   <script src="script.js"></script>
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

## Reglas básicas de sintaxis

- Cada instrucción termina, por convención, con punto y coma `;`.
- El código distingue mayúsculas de minúsculas (*case sensitive*): `variable` y `Variable` son cosas distintas.
- Los comentarios se escriben con `//` (una línea) o `/* ... */` (varias líneas).
- Los bloques de código se delimitan con llaves `{ }`.

## Formas de mostrar datos en JavaScript

JavaScript puede mostrar datos de varias maneras:

- **Escribir en un elemento HTML**, usando `innerHTML` junto con `document.getElementById(id)` para localizar ese elemento por su atributo `id`.
- **Escribir en la salida del documento**, usando `document.write()`.
- **Escribir en un cuadro de alerta**, usando `window.alert()` (o simplemente `alert()`).
- **Escribir en la consola del navegador**, usando `console.log()` — muy útil para depuración, ya que no interrumpe la página como sí hace `alert()`.

```html
<p id="demo"></p>
<script>
  document.getElementById("demo").innerHTML = 5 + 6;   // escribe "11" dentro del párrafo
</script>
```

```js
document.write(5 + 6);   // escribe "11" en el propio documento (solo recomendable antes de cargar la página)
alert(5 + 6);             // muestra "11" en una ventana emergente
console.log(5 + 6);       // muestra "11" en la consola del navegador (F12 → pestaña Consola)
```

## Ventanas emergentes

Además de `alert()`, JavaScript ofrece otras dos funciones para interactuar con el usuario mediante ventanas emergentes:

```js
alert("Este es un mensaje");             // Muestra un aviso
confirm("¿Deseas continuar?");           // Pregunta Sí/No, devuelve true o false
prompt("Escribe tu nombre:", "Valor por defecto"); // Pide un dato, devuelve el texto introducido
```

## Variables

Se declaran con `let` (variable, valor modificable) o `const` (constante, su valor no puede reasignarse):

```js
let nombre = "Ana";
const PI = 3.1416;

nombre = "Carlos";  // válido, es una variable
// PI = 3;          // error, es una constante
```

## Tipos de datos

- **String** (cadena de texto): `"Hola"` o `'Hola'`.
- **Number** (número): `42`, `3.14`.
- **Boolean** (booleano): `true` / `false`.
- **Array** (lista de valores).
- **Object** (objeto).
- `undefined` (variable declarada sin valor) y `null` (ausencia intencionada de valor).

## Arrays

Un array almacena una colección ordenada de valores, accesibles por su posición (empezando en `0`):

```js
let colores = ["rojo", "verde", "azul"];

console.log(colores[0]);   // "rojo"
colores[1] = "amarillo";   // modifica el segundo elemento
colores.length;            // número de elementos del array (3)
```

## Operadores

- **Aritméticos**: `+`, `-`, `*`, `/`, `%` (resto de una división).
- **Asignación**: `=`, `+=`, `-=`, `*=`, `/=`.
- **Comparación**: `==` (igual, sin comprobar el tipo), `===` (igual, comprobando también el tipo), `!=`, `!==`, `>`, `<`, `>=`, `<=`.
- **Lógicos**: `&&` (Y), `||` (O), `!` (negación).
- **Incremento/decremento**: `++`, `--`.

```js
let a = 5;
let b = "5";
a == b;   // true  (mismo valor)
a === b;  // false (distinto tipo: number vs string)
```

## Estructuras de control

### Condicional `if` / `else`

```js
let edad = 17;

if (edad >= 18) {
  console.log("Eres mayor de edad");
} else {
  console.log("Eres menor de edad");
}
```

### Bucle `while`

Repite el bloque **mientras** se cumpla la condición (se comprueba antes de cada vuelta):

```js
let i = 0;
while (i < 5) {
  console.log(i);
  i++;
}
```

### Bucle `do...while`

Igual que `while`, pero comprueba la condición **después** de cada vuelta, por lo que el bloque se ejecuta siempre al menos una vez:

```js
let i = 0;
do {
  console.log(i);
  i++;
} while (i < 5);
```

### Bucle `for`

Combina en una sola línea la inicialización, la condición y el incremento:

```js
for (let i = 0; i < 5; i++) {
  console.log(i);
}
```

---

[⬅ Volver a UT1](index.md) · [Ir a HTML5](html.md) · [Ir a Prácticas de HTML5](practicas-html.md) · [Ir a CSS](css.md) · [Ir a Publicación web avanzada](publicacion-web.md)