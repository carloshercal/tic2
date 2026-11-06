# Guion de la demo: GitHub Copilot para el proyecto final (vie 6/11)

## Resumen

| | |
|---|---|
| **Qué es** | Una demo en directo sobre una mini-web de ejemplo, el «Club de lectura del instituto», que ya tiene las funcionalidades A, B y C del proyecto **con dos fallos escondidos**. Copilot se usa para planificar, depurar, entender y revisar, nunca para hacer el proyecto. |
| **Duración** | ~30 min de demo + ~20 min de actividad guiada del alumnado (`copilot.md`). |
| **Dónde** | Repositorio `demo-profesor`, carpeta `proyecto-demo/` (`index.html` + `css/estilos.css` + `js/inicio.js`). Los archivos están en el [anexo](#anexo-archivos-de-partida). |
| **Pantalla** | VS Code a la izquierda, con el **chat de Copilot abierto** en el panel lateral, y el navegador con Live Server y la consola (F12) a la derecha. Sube el zoom de VS Code (`Ctrl` + `+`) y el tamaño de letra del chat. |
| **Mensaje central** | «Copilot es un compañero que sabe mucho pero a veces se equivoca con total seguridad. Si no sabes explicarlo, no es tuyo.» |

### Antes de clase (10 min)

1. En tu VS Code, comprueba que Copilot está activo con tu cuenta de GitHub: escribe algo en un `.html` y mira si sale texto en gris.
2. **No** crees todavía `.github/copilot-instructions.md` en `demo-profesor`: el bloque 1 enseña la diferencia entre tenerlo y no tenerlo. Si ya existe, renómbralo a `copilot-instructions.md.bak`.
3. Crea `proyecto-demo/` con los tres archivos del anexo y ábrelo con Live Server. Deben verse dos cosas raras: la lista de «Próximas lecturas» vacía y un error rojo en la consola. Es lo esperado.
4. **Ensaya los prompts** de los bloques 1, 4 y 6. Si alguna respuesta sale muy distinta de lo que describe el guion, haz una captura: te sirve de plan B.
5. Cupo: la demo gasta unas **12-15 consultas de chat**. Con el plan Free el cupo mensual es limitado, así que no repitas consultas en clase sin necesidad.
6. Pide al alumnado que entre con **VS Code abierto y su repositorio clonado**, y que tenga a mano el tema que ha entregado en Teams.

### Ritmo de cada paso

1. Lee el prompt **en voz alta** antes de enviarlo: el objetivo es que aprendan a preguntar.
2. Antes de leer la respuesta, pregunta: «¿Qué creéis que va a contestar?».
3. Lee la respuesta con ellos y **compruébala siempre en el navegador**. Las respuestas que pueden variar van marcadas con 🎲.
4. Termina cada bloque con la frase en **negrita** («Lo que se llevan»).

---

## Bloque 0 — Qué es y cuáles son las reglas (~3 min, sin ordenador)

- Copilot está **dentro de VS Code** y hace tres cosas: sugiere código mientras escribes, responde en un chat y edita código seleccionado.
- Proyecta la tabla «Reglas de uso en el proyecto» de [copilot.md](https://carloshercal.github.io/tic2/ut1-html-css-js/copilot.html#reglas-de-uso-en-el-proyecto). Insiste en dos cosas:
  - Se usa el modo **Ask**, nunca **Agent**.
  - En la presentación pueden pedir un **cambio en directo**: quien deja que Copilot lo haga todo, no lo sabe hacer.
- Privacidad: lo que se escribe en el chat sale hacia los servidores de GitHub. Nada de datos personales.

**Lo que se llevan: Copilot ayuda a aprender; no aprende por ti.**

---

## Bloque 1 — Configurarlo para la asignatura (~6 min)

**Paso 1 · Sin instrucciones** 🎲

Abre `js/inicio.js`, abre el chat en modo **Ask** y escribe:

```
Quiero que, al llegar a 10 lectores apuntados, aparezca un mensaje «¡Grupo completo!» y el botón deje de sumar. ¿Cómo lo hago?
```

- **Pregunta:** ¿qué tipo de código creéis que va a proponer?
- **Resultado probable:** una solución correcta, pero a menudo con cosas que **no hemos visto**: `addEventListener`, `querySelector`, plantillas con `` ` `` y `${}`, funciones flecha `=>` o `button.disabled = true`.
- **Comentario:** señálalas en pantalla. «¿Sabríais explicar esto en la presentación? Es lo que el profesor busca al corregir».

**Paso 2 · Crear el archivo de instrucciones**

En la raíz de `demo-profesor`, crea `.github/copilot-instructions.md` y pega el contenido del apartado «Las instrucciones del repositorio» de `copilot.md`. Guarda.

**Paso 3 · Con instrucciones** 🎲

Abre un **chat nuevo** (botón `+` del panel) y repite exactamente el mismo prompt.

- **Resultado probable:** responde en español, explica antes la idea y usa `if`, `onclick`, `getElementById` e `innerHTML`, como en clase.
- **Comentario:** el archivo no se ve en la web, pero Copilot lo lee en cada consulta. **Es el paso 2 de la actividad de hoy.** Recuerda: va en la raíz del repositorio, no dentro de `proyecto/`.

> Si en el paso 3 sigue saliendo algo no visto, mejor todavía: enseña cómo se pide «Rehazlo usando solo lo que pone en mis instrucciones».

**Lo que se llevan: primero configuras a Copilot; después le pides cosas.**

---

## Bloque 2 — Sugerencias mientras escribes (~4 min)

**Paso 4 · Un comentario que guía la sugerencia**

En `index.html`, dentro de la primera `<section>`, debajo del botón, escribe:

```html
<!-- Lista no ordenada con los tres días de reunión del club y su horario -->
```

Pulsa Intro y espera el texto en gris.

- **Pregunta:** ¿lo acepto entero con Tab?
- **Comentario:** acepta **palabra a palabra** con `Ctrl` + `→` y lee en voz alta lo que entra. Señala lo que se ha inventado (días, horas) y que **el contenido lo decides tú**.

**Paso 5 · La sugerencia que no encaja** ⚠️

Ve a `js/inicio.js`, al final de `apuntarme()`, y empieza a escribir `document.getElementById("`.

- **Resultado probable:** propone un `id` que **no existe** en tu HTML (por ejemplo `"contador"` o `"mensaje-socios"`).
- **Comentario:** Copilot adivina, no comprueba. Si aceptas un `id` que no existe, tendrás `Cannot set properties of null`. Descártalo con `Esc`.

**Lo que se llevan: Tab solo después de leer.**

---

## Bloque 3 — Planificar con el chat (~3 min)

**Paso 6 · Prompt pobre contra prompt bueno** 🎲

Escribe primero el pobre:

```
hazme una web de un club de lectura
```

- **Resultado probable:** una página entera de código, o pide permiso para crear archivos. No te ayuda a aprender y no cumple los requisitos.

Ahora el bueno (proyecta las cuatro partes: contexto, qué quiero, límites y formato):

```
Estoy en 2º de Bachillerato y hago un sitio web sobre el club de lectura del instituto para el proyecto de TIC II. Tiene que tener 3 páginas, una tabla, un formulario, un widget con iframe y tres funcionalidades JavaScript: un botón, un array recorrido con for y la validación del formulario. Propón qué iría en cada página y qué funcionalidad pondría en cada una. No escribas código.
```

- **Comentario:** la respuesta es un **plan**, no código. Cada uno lo adapta a su tema: **es el paso 5 de la actividad de hoy**, y lo apuntan en el borrador del README.

**Lo que se llevan: contexto + qué quieres + límites + formato.**

---

## Bloque 4 — Depurar pidiendo pistas (~6 min)

**Paso 7 · Fallo 1: la lista vacía**

Enseña el navegador: la lista de «Próximas lecturas» está vacía y la consola dice, en rojo:

```
Uncaught TypeError: Cannot set properties of null (setting 'innerHTML')
```

- **Pregunta:** antes de preguntar a nadie, ¿qué significa este error? Ya lo visteis en JavaScript.

En `js/inicio.js`, **selecciona** el bloque B (del `const lecturas` hasta el `innerHTML`) y escribe en el chat:

```
Al cargar la página sale este error: Cannot set properties of null (setting 'innerHTML'). Dame una pista de qué puede fallar en el código seleccionado, pero no me des la solución.
```

- **Resultado probable** 🎲: que `getElementById` no encuentra el elemento y que revises el `id`.
- **Comentario:** la pista es buena, pero el arreglo lo haces tú. Busca el `id` en el HTML (`libros`), corrige `"lista-libros"` por `"libros"` y guarda. Aparecen los tres libros y la consola queda limpia.

**Paso 8 · Fallo 2: el mensaje que desaparece**

Escribe un título y 300 páginas y pulsa **Enviar**.

- **Resultado:** el mensaje aparece un instante y **desaparece**: la página se recarga (fíjate en el `#` al final de la dirección).
- **Pregunta:** ¿qué le preguntaríais a Copilot? Deja que propongan el prompt y escríbelo como lo digan. Si hace falta, ayúdales:

```
Al pulsar Enviar, el mensaje aparece y desaparece enseguida. En la consola no hay errores. ¿Por qué puede pasar? Dame solo una pista.
```

- **Resultado probable** 🎲: que el botón dentro de un formulario envía el formulario y recarga la página.
- **Arreglo:** añade `type="button"` al botón de Enviar. Ya está en el enunciado del proyecto: enséñalo en el paso 5 de `proyecto.md`.

**Lo que se llevan: primero la consola; después, a Copilot le pides pistas, no soluciones.**

---

## Bloque 5 — Entender código con `/explain` (~3 min)

**Paso 9 · Explicación línea a línea**

Selecciona el bucle `for` del bloque B y escribe:

```
/explain Explícame línea a línea este bucle. Estoy empezando con JavaScript.
```

- **Comentario:** es exactamente lo que tendrán que hacer en la presentación: explicar una función línea a línea. Que la lean en voz alta y comprueben si dice algo que no coincide con los apuntes.
- Si da tiempo, haz la prueba de «¿qué pasa si quito esta línea?»: borra `elementos += …`, guarda y mira la lista vacía. Deshazlo con `Ctrl` + `Z`.

**Lo que se llevan: si Copilot te lo explica y tú no lo sabrías explicar después, no lo uses.**

---

## Bloque 6 — Revisar antes de entregar (~3 min)

**Paso 10 · Revisión contra la rúbrica** 🎲

Con `js/inicio.js` abierto, escribe en el chat (el `#` añade el archivo a la pregunta):

```
Revisa #inicio.js e #index.html. La función proponer() debe validar el formulario también en casos límite: campos vacíos y números fuera de rango. Dime qué casos no están controlados, sin escribir el código corregido.
```

- **Resultado probable:** detecta que con el campo de páginas **vacío** o con un número **negativo** se acepta la propuesta.
- **Compruébalo en el navegador:** título «Marianela» y páginas vacías → sale «Gracias…». Con −20, también.
- **Comentario:** esto es lo que separa el Notable del Sobresaliente en «JavaScript: funcionalidades». Corrígelo en directo, explicando cada parte:

```js
} else if (!(paginas >= 1 && paginas <= 500)) {
  document.getElementById("mensaje").innerHTML = "Escribe un número de páginas entre 1 y 500.";
}
```

> Si alguien pregunta por qué no `paginas < 1 || paginas > 500`: con un campo vacío `Number("")` da 0 y las dos formas lo rechazan. La forma con `!` además rechaza `NaN`. No hace falta profundizar más.

**Lo que se llevan: pídele que revise contra la lista de comprobación del enunciado.**

---

## Bloque 7 — Lo que no se hace (~1 min)

Abre el selector de modo del chat y enséñalo:

- **Ask:** el que usamos. Responde, no toca archivos.
- **Agent:** crea y modifica archivos por su cuenta. **No se usa en el proyecto.** Si al corregir el proyecto aparece código que no sabes explicar, te preguntaré por él en la presentación.

---

## Bloque 8 — *Commit* y apartado de IA del README (~2 min)

**Paso 11 · Mensaje de *commit* con Copilot**

En el panel **Source Control**, pulsa el icono de estrellitas ✨ de la caja del mensaje: Copilot propone un mensaje a partir de los cambios.

- **Comentario:** léelo y ajústalo si hace falta (en español y concreto, por ejemplo «Corrige el id de la lista y valida las páginas»). La rúbrica valora mensajes que describan el cambio.

**Paso 12 · El apartado «Uso de inteligencia artificial»**

Escribe en `proyecto-demo/README.md` (o en la pizarra) un ejemplo de lo que se espera:

```markdown
## Uso de inteligencia artificial

He usado GitHub Copilot en modo Ask para:

- Planificar las páginas del sitio: le pedí ideas sin código y elegí las que encajaban con mi tema.
- Depurar el error `Cannot set properties of null`: me dio una pista y vi que el `id` de la lista estaba mal escrito.
- Revisar la validación del formulario: me avisó de que aceptaba páginas vacías o negativas. Lo corregí yo con `!(paginas >= 1 && paginas <= 500)`.
```

- **Comentario:** fijaos en que cada punto dice **qué le pedí** y **qué hice yo**. Un «He usado Copilot para todo» no puntúa.

Haz *commit* y *push*.

---

## Actividad del alumnado (~20 min)

Proyecta [copilot.md → Actividad guiada](https://carloshercal.github.io/tic2/ut1-html-css-js/copilot.html#actividad-guiada--primeros-pasos-con-copilot). Prioridad, por si no da tiempo a todo:

1. **Imprescindible:** pasos 1 y 2 (activar Copilot y crear `.github/copilot-instructions.md` con su *commit* y *push*).
2. **Imprescindible:** paso 5 (plan de su sitio con un prompt bueno, apuntado en el borrador de `proyecto/README.md`).
3. Si da tiempo: pasos 3, 4 y 6.

Mientras trabajan, pasa por los puestos comprobando:

- Que han iniciado sesión con **la cuenta de GitHub de la entrega**.
- Que el selector de modo está en **Ask**.
- Que el archivo de instrucciones está en `.github/` de la **raíz** del repositorio.

## Si algo se tuerce en directo

- **Copilot no responde o pide iniciar sesión:** revisa la cuenta en el icono de perfil de VS Code (abajo a la izquierda). Si la red del aula lo bloquea, sigue con las capturas del ensayo y avisa al coordinador TIC.
- **La respuesta sale distinta de la del guion:** mejor. Léela con la clase y decide con ellos si es correcta, comprobándola en el navegador. Ese es el hábito que queremos.
- **La respuesta tiene un error:** aprovéchalo. «¿Veis por qué hay que comprobar siempre?».
- **Un alumno no tiene Copilot activo:** que siga la actividad con el compañero de al lado y lo active en casa. No bloquea el proyecto.
- **Te quedas sin cupo de chat:** el resto de la demo se puede contar con las capturas del ensayo.

---

## Anexo: archivos de partida

Carpeta `proyecto-demo/` en `demo-profesor`. **Tiene dos fallos a propósito** (bloque 4) y una validación incompleta (bloque 6). No los corrijas antes de clase.

### `index.html`

El botón de Enviar **no** lleva `type="button"`: es el fallo 2.

```html
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Club de lectura — Inicio</title>
  <link rel="stylesheet" href="css/estilos.css">
</head>
<body>
  <header>
    <h1>Club de lectura del instituto</h1>
    <nav>
      <a href="index.html">Inicio</a>
      <a href="libros.html">Libros</a>
      <a href="contacto.html">Contacto</a>
    </nav>
  </header>

  <main>
    <section>
      <h2>Libro del mes</h2>
      <p>Este mes leemos <strong>Marianela</strong>, de Benito Pérez Galdós.</p>
      <p>Ya somos <span id="socios">0</span> lectores.</p>
      <button type="button" onclick="apuntarme()">Me apunto</button>
    </section>

    <section>
      <h2>Próximas lecturas</h2>
      <ol id="libros"></ol>
    </section>

    <section>
      <h2>Propón un libro</h2>
      <form action="#" method="post">
        <p>
          <label for="titulo">Título:</label>
          <input type="text" id="titulo" name="titulo">
        </p>
        <p>
          <label for="paginas">Número de páginas:</label>
          <input type="number" id="paginas" name="paginas">
        </p>
        <button onclick="proponer()">Enviar</button>
      </form>
      <p id="mensaje"></p>
    </section>
  </main>

  <footer>
    <p>Club de lectura · TIC II · Curso 2026-27</p>
  </footer>

  <script src="js/inicio.js"></script>
</body>
</html>
```

> Las páginas `libros.html` y `contacto.html` no existen: la demo usa solo la portada. Si Copilot avisa de enlaces rotos en la revisión, tiene razón.

### `js/inicio.js`

El `id` `"lista-libros"` no existe en el HTML: es el fallo 1.

```js
// Club de lectura — JavaScript de la portada

// A. Contador de lectores apuntados
let socios = 0;

function apuntarme() {
  socios++;
  document.getElementById("socios").innerHTML = socios;
}

// B. Lista de próximas lecturas, generada a partir de un array
const lecturas = ["Marianela", "El Lazarillo de Tormes", "Platero y yo"];
let elementos = "";

for (let i = 0; i < lecturas.length; i++) {
  elementos += "<li>" + lecturas[i] + "</li>";
}

document.getElementById("lista-libros").innerHTML = elementos;

// C. Validar la propuesta de libro
function proponer() {
  let titulo = document.getElementById("titulo").value;
  let paginas = Number(document.getElementById("paginas").value);

  if (titulo === "") {
    document.getElementById("mensaje").innerHTML = "Escribe el título del libro.";
  } else if (paginas > 500) {
    document.getElementById("mensaje").innerHTML = "Es muy largo para un mes: busca uno de menos de 500 páginas.";
  } else {
    document.getElementById("mensaje").innerHTML = "Gracias. Propondremos «" + titulo + "» en la próxima reunión.";
  }
}
```

### `css/estilos.css`

Hoja mínima, solo para que se vea bien en el proyector.

```css
/* Club de lectura — hoja de la demo (mínima, para el proyector) */

/* ---------- General ---------- */
html {
  font-size: 20px;
}

body {
  margin: 0;
  font-family: Georgia, "Times New Roman", serif;
  color: #3e2723;
  background-color: #fff8e1;
}

/* ---------- Cabecera y menú ---------- */
header {
  padding: 20px;
  text-align: center;
  background-color: #6d4c41;
}

h1 {
  margin: 0;
  color: white;
}

nav a {
  margin: 0 10px;
  color: #ffe0b2;
  text-decoration: none;
}

nav a:hover {
  color: white;
}

/* ---------- Contenido ---------- */
main {
  width: 80%;
  margin: 0 auto;
}

section {
  margin: 20px 0;
  padding: 10px 20px;
  border-left: 6px solid #8d6e63;
  background-color: white;
}

#mensaje {
  font-weight: bold;
  color: #2e7d32;
}

/* ---------- Pie ---------- */
footer {
  padding: 10px;
  text-align: center;
  color: white;
  background-color: #4e342e;
}
```

## Resultado comprobado

| Momento | Qué se ve |
|---|---|
| Al abrir (con fallos) | Contador funciona. Lista de lecturas **vacía**. Consola: `Cannot set properties of null (setting 'innerHTML')`. Al enviar el formulario, la página se recarga (`index.html#`) y el mensaje desaparece. |
| Tras corregir el `id` y añadir `type="button"` | Consola limpia, lista con los tres libros y mensaje «Gracias. Propondremos «Marianela» en la próxima reunión.». |
| Validación original | Páginas vacías → «Gracias…» ❌ · −20 → «Gracias…» ❌ · título vacío → «Escribe el título del libro.» · 1300 → «Es muy largo…». |
| Validación corregida (bloque 6) | Páginas vacías, −20 y 1300 → «Escribe un número de páginas entre 1 y 500.» · título vacío → «Escribe el título del libro.». |
