---
title: UT1 — Proyecto final
---

# Proyecto final de la UT1: mi sitio web

**Objetivo:** crear un sitio web de varias páginas sobre un tema que elijas, combinando todo lo visto en la unidad: HTML semántico, CSS y JavaScript. Además, lo documentarás en un `README.md` y lo presentarás en clase.

## Paso 1. Elige el tema

El tema es libre. Algunas ideas: tu grupo de música favorito, un deporte o un club, tu localidad (lugares, fiestas, rutas), una afición (fotografía, cocina, videojuegos, lectura) o una actividad del instituto.

- Puedes partir del mini-sitio del Ejercicio 9 de HTML o del Ejercicio 10 de CSS, siempre que lo amplíes hasta cumplir **todos** los requisitos.
- **Sin datos personales reales**: ni tuyos ni de otras personas (teléfonos, direcciones, fotos de gente que no ha dado permiso).
- **Imágenes:** propias o con licencia libre (por ejemplo, de Wikimedia Commons, Pixabay o Unsplash). Anota la fuente de cada una en el README.

## Paso 2. Organiza los archivos

Todo el proyecto va en la carpeta `proyecto/` de tu repositorio `ut1-html-css-js-usuario`:

```
proyecto/
├── README.md
├── index.html          ← portada
├── galeria.html        ← los nombres de las demás páginas dependen de tu tema
├── contacto.html
├── css/
│   └── estilos.css
├── js/
│   ├── inicio.js       ← un archivo JavaScript por página que lo necesite
│   └── contacto.js
└── img/
```

- Nombres de archivo en minúsculas, sin tildes ni espacios, separados por guiones (`mis-rutas.html`).
- Enlaza en cada página **solo** el archivo JavaScript que usa, al final del `<body>`.

## Paso 3. Requisitos de HTML

1. **Al menos 3 páginas** enlazadas entre sí.
2. Cada página con estructura válida: `<!DOCTYPE html>`, `lang="es"`, `charset` UTF-8, `viewport` y un `<title>` distinto.
3. **Estructura semántica** en todas las páginas: `<header>`, `<nav>`, `<main>` y `<footer>`. Usa `<section>` y `<article>` donde tenga sentido.
4. **El mismo menú** en todas las páginas, con enlaces relativos a las demás.
5. Un solo `<h1>` por página y títulos en orden (`h1` → `h2` → `h3`).
6. En el conjunto del sitio debe haber, como mínimo:
   - **3 imágenes** con `alt` descriptivo;
   - **1 lista** (`ul`, `ol` o `dl`);
   - **1 tabla** con `<caption>`, `<thead>` y `<th>`;
   - **1 formulario** con al menos 3 campos de tipos distintos, cada uno con su `<label for="...">`;
   - **1 widget externo** incrustado con `<iframe>` (un mapa, un vídeo…), como se explica en [Publicación web avanzada](publicacion-web.md);
   - **1 enlace externo** que se abra en una pestaña nueva.
7. Sangría de 2 espacios y atributos en minúscula.

## Paso 4. Requisitos de CSS

1. **Una sola hoja externa**, `css/estilos.css`, enlazada en todas las páginas. Nada de estilos en línea (`style="..."`) ni en `<style>`. Si el código del widget trae `style="border:0"`, pasa esa regla a tu hoja (`iframe { border: 0; }`).
2. **Paleta de colores** coherente (al menos 3 colores) y `font-family` terminada en una familia genérica.
3. **Selectores variados:** de etiqueta, de clase, de id, de relación (descendiente o hijo) y la pseudoclase `:hover` en los enlaces del menú.
4. **Modelo de caja:** `margin`, `padding` y `border` usados con intención (tarjetas, secciones, botones). Centra el contenido principal con `width` y `margin: 0 auto`.
5. **Unidades relativas** (`rem`, `em` o `%`) en algún tamaño de letra o ancho.
6. **Un uso de `position`**, por ejemplo un enlace «Volver arriba» fijo en una esquina:

```css
/* Enlace fijo en la esquina inferior derecha */
.volver-arriba {
  position: fixed;
  right: 20px;
  bottom: 20px;
  padding: 10px;
  background-color: #1e88e5;
  color: white;
}
```

7. La hoja organizada por bloques con comentarios (`/* Cabecera */`, `/* Menú */`…).

## Paso 5. Requisitos de JavaScript

Usa **solo lo visto en clase**: variables y constantes, arrays, operadores, `if`/`else`, bucles, funciones, `onclick`, `document.getElementById()`, `innerHTML`, `.value` y `Number()`.

Tu sitio debe tener **al menos estas tres funcionalidades**, relacionadas con tu tema:

| | Funcionalidad | Ejemplos |
|---|---|---|
| **A** | Un **botón** que llama a una función y cambia algo de la página sin recargarla. | Contador de «Me gusta», mostrar u ocultar un dato curioso, cambiar el texto de un aviso. |
| **B** | Un **array** recorrido con `for` que **genera contenido** en la página. | Lista de canciones, filas de una tabla de partidos, rutas de tu localidad. |
| **C** | **Comprobar datos con `if`/`else`**: validar el formulario y mostrar un mensaje en la página. | Avisar si falta un campo, si un número está fuera de rango o dar las gracias si todo está bien. |

Para que el botón del formulario no recargue la página, usa `type="button"` y lee los campos con `.value`:

```html
<button type="button" onclick="validar()">Enviar</button>
<p id="mensaje"></p>
```

```js
// Comprueba que el nombre no está vacío y muestra el resultado en la página
function validar() {
  let nombre = document.getElementById("nombre").value;

  if (nombre === "") {
    document.getElementById("mensaje").innerHTML = "Escribe tu nombre, por favor.";
  } else {
    document.getElementById("mensaje").innerHTML = "Gracias, " + nombre + ".";
  }
}
```

Además:

- Los resultados se muestran **en la página** con `innerHTML`. `alert()` solo como complemento.
- La consola (**F12**) no muestra **ningún error** en ninguna página.
- Nombres en *camelCase* y comentarios con `//` que expliquen qué hace cada parte.

## Paso 6. El README del proyecto

Crea `proyecto/README.md` con estos apartados. Copia la plantilla y sustituye lo que va entre `< >`:

```markdown
# <Título del sitio>

<Dos o tres frases: de qué trata el sitio y a quién va dirigido.>

## Páginas

| Archivo | Contenido |
|---|---|
| `index.html` | <Portada: …> |
| `<pagina>.html` | <…> |
| `<pagina>.html` | <…> |

## Cómo verlo

Abre `index.html` con la extensión Live Server de Visual Studio Code.

## Funcionalidades JavaScript

- **<Nombre de la funcionalidad>** (`<pagina>.html`, función `<nombreFuncion>()`): <qué hace y cómo se usa>.
- …

## Diseño

<Colores y tipografía elegidos, y por qué.>

## Recursos y licencias

- <Imagen o widget>: <fuente (enlace)> — <licencia>.

## Uso de inteligencia artificial

<Para qué has usado GitHub Copilot, un ejemplo de lo que le pediste y qué cambiaste tú. Si no lo has usado, indícalo.>

## Autor

<Tu nombre> · 2º de Bachillerato · TIC II · Curso 2026-2027
```

Lo justo de Markdown que necesitas:

| Escribes | Obtienes |
|---|---|
| `# Título`, `## Apartado` | Títulos de nivel 1 y 2 |
| `- elemento` | Lista con viñetas |
| `**texto**` | **Negrita** |
| `` `codigo` `` | `Código` |
| `[texto](https://…)` | Enlace |

Las tablas se escriben como la de «Páginas» de la plantilla: una fila por línea, columnas separadas por barras verticales y una segunda fila de guiones.

En GitHub, entra en la carpeta `proyecto/` de tu repositorio y comprueba que el README se ve bien.

## Paso 7. La presentación

Tienes **entre 6 y 8 minutos**, más hasta 3 minutos de preguntas. Presentas desde el ordenador del aula, con tu sitio abierto con Live Server y el código en VS Code. No hacen falta diapositivas.

1. **El tema** (1 min): de qué va tu sitio y por qué lo has elegido.
2. **Recorrido** (2 min): navega por las páginas y enseña el widget y el formulario.
3. **El código** (2-3 min): explica **una función de JavaScript** línea a línea y **una regla CSS** de la que estés satisfecho.
4. **Dificultades** (1 min): qué te costó, cómo lo resolviste y para qué te sirvió Copilot.

En las preguntas, el profesor puede pedirte un **cambio pequeño en directo** (por ejemplo, añadir un elemento al array o cambiar un color). Si el código es tuyo, te llevará un minuto.

## Coevaluación

Mientras presentan tus compañeros, valorarás su presentación con un formulario de Microsoft Forms que se abrirá en Teams. Usarás los criterios de la rúbrica de coevaluación (apartado D de la evaluación, más abajo) y escribirás algo que te haya gustado y algo que mejorarías.

- Valora la presentación, no a la persona. Sé concreto y respetuoso.
- Si la nota media de tus compañeros se aleja **2 puntos o más** de la que pone el profesor, esa parte la califica el profesor.

## Uso de GitHub Copilot

Puedes usar Copilot como ayuda, con estas reglas (más detalle en [GitHub Copilot en VS Code](copilot.md)):

- **Sí:** que te explique código o un error, que te dé pistas, que te sugiera ideas de contenido o que revise tu código.
- **No:** usar el modo **Agent** para que cree o modifique los archivos por ti, ni copiar código con elementos que no hemos visto en clase.
- **Obligatorio:** contar en el README cómo lo has usado y **poder explicar cualquier línea** de tu proyecto.

## Lista de comprobación

Antes de entregar, revisa:

- [ ] Las 3 páginas (o más) se abren y el menú lleva a todas.
- [ ] Todas tienen `header`, `nav`, `main`, `footer` y un solo `h1`.
- [ ] Hay 3 imágenes con `alt`, una lista, una tabla, un formulario, un widget y un enlace externo.
- [ ] Todas las páginas enlazan `css/estilos.css` y no hay `style="..."`.
- [ ] Las funcionalidades A, B y C funcionan, también con el formulario vacío.
- [ ] La consola (F12) no muestra errores en ninguna página.
- [ ] `proyecto/README.md` tiene todos los apartados y se ve bien en GitHub.
- [ ] Has hecho *commit* y *push* al menos una vez por sesión.

## Entrega

1. Haz *commit* y *push* de la carpeta `proyecto/` (repasa [Subir tus ejercicios a GitHub](github.md)).
2. Entra en tu repositorio en GitHub y comprueba que están todos los archivos y las imágenes.
3. Entrega el **enlace a tu repositorio** en la tarea del proyecto en Teams antes del **lunes 16/11 a las 23:59**.

Lo que se sube después de esa hora no se tiene en cuenta.

---

## Evaluación

El proyecto supone el 80 % de la nota de la UT1 y se reparte así:
 
| Parte | Quién evalúa | Peso en el proyecto | Peso en la UT1 |
|---|---|---|---|
| A. Sitio web | Profesor | 50 % | 40 % |
| B. README | Profesor | 10 % | 8 % |
| C. Presentación | Profesor | 20 % | 16 % |
| D. Coevaluación de la presentación | Compañeros | 20 % | 16 % |
| **Total** | | **100 %** | **80 %** |

Cada indicador se califica según la rúbrica: **Insuficiente** (0-4), **Suficiente** (5-6), **Notable** (7-8) y **Sobresaliente** (9-10).

### A. Sitio web (50 %)
 
| Indicador | Peso | Insuficiente | Suficiente | Notable | Sobresaliente |
|---|---|---|---|---|---|
| Estructura y semántica HTML | 15 % | Faltan páginas o la estructura básica. Apenas hay etiquetas semánticas o hay etiquetas sin cerrar. | 3 páginas con estructura válida y algunas etiquetas semánticas. Fallos en la jerarquía de títulos o en el anidado. | Todas las páginas tienen `header`, `nav`, `main` y `footer`, un solo `h1` y títulos en orden. Errores menores. | Lo anterior sin errores, con `section` y `article` bien usados, sangría de 2 espacios y código coherente entre páginas. |
| Elementos obligatorios HTML | 15 % | Faltan 3 o más elementos obligatorios. | Faltan 1 o 2 elementos, o varios están incompletos (imágenes sin `alt`, `label` sin `for`). | Están todos, con algún detalle mejorable (`alt` poco descriptivos, tabla sin `caption`). | Todos completos y bien usados: `alt` descriptivos, tabla con `caption` y `th`, cada campo con su `label` y widget integrado en el diseño. |
| CSS: hoja externa y selectores | 15 % | Sin hoja externa, con estilos en línea o con muy pocos estilos. | Hoja externa enlazada en todas las páginas, con selectores básicos (etiqueta y clase). | Selectores variados (clase, id, relación, `:hover`) y hoja comentada por bloques. | Selectores variados y bien elegidos, sin reglas repetidas ni estilos en línea, y hoja ordenada. |
| CSS: modelo de caja, unidades y `position` | 10 % | No usa `margin`, `padding` ni `border` con intención. | Usa el modelo de caja en algún elemento, con un resultado desigual. | Modelo de caja aplicado con criterio, contenido centrado, unidades relativas y un uso de `position`. | Lo anterior con un resultado limpio y equilibrado, y un `position` que aporta algo sin tapar contenido. |
| Diseño y experiencia de usuario | 10 % | Cuesta leer o navegar: poco contraste o enlaces rotos. | Se lee y se navega, pero el diseño cambia entre páginas. | Colores y tipografía coherentes en todo el sitio, buen contraste y navegación clara. | Diseño cuidado y personal, jerarquía visual clara, mensajes útiles al usuario y ningún enlace roto. |
| JavaScript: funcionalidades | 25 % | Menos de 2 funcionalidades, o no funcionan. | Las 3 funcionalidades funcionan en el caso básico, aunque alguna solo usa `alert()`. | Las funcionalidades A, B y C funcionan y muestran el resultado en la página. | Funcionan también en casos límite (campos vacíos, números fuera de rango), están integradas en el tema y hay alguna ampliación. |
| JavaScript: calidad y depuración | 5 % | Errores en la consola o código sin comentar. | Funciona, pero con algún error en la consola o pocos comentarios. | Sin errores en la consola, nombres claros en *camelCase* y comentarios. | Lo anterior, con código ordenado, funciones reutilizadas y comentarios que explican el porqué. |
| Organización y entrega | 5 % | Fuera de plazo, fuera de `proyecto/` o con rutas rotas. | En plazo, con algún nombre de archivo incorrecto o un único *commit* al final. | Estructura de carpetas correcta, nombres sin tildes ni espacios y varios *commits*. | Lo anterior, con al menos un *commit* por sesión y mensajes que describen el cambio. |
 
### B. README (10 %)
 
| Indicador | Peso | Insuficiente | Suficiente | Notable | Sobresaliente |
|---|---|---|---|---|---|
| Descripción y páginas | 40 % | No hay README o no explica de qué trata el sitio. | Explica el tema, pero la tabla de páginas está incompleta. | Descripción clara y tabla con todas las páginas. | Descripción clara y atractiva, tabla completa e instrucciones para verlo. |
| Funcionalidades JavaScript | 30 % | No las menciona. | Las enumera sin explicar qué hacen. | Explica qué hace cada una y en qué página está. | Indica además la función que la ejecuta y cómo probarla. |
| Recursos, licencias y uso de IA | 20 % | No cita fuentes ni el uso de IA. | Cita algunas fuentes o el uso de IA de forma vaga. | Cita la fuente de todas las imágenes y el widget, y describe el uso de IA. | Lo anterior con licencias y un ejemplo concreto de lo que pidió a Copilot y lo que cambió. |
| Formato Markdown | 10 % | Texto sin formato. | Usa algún título o lista. | Títulos, listas y tabla correctos. | Formato limpio y consistente; se ve perfectamente en GitHub. |
 
### C. Presentación (20 %)
 
| Indicador | Peso | Insuficiente | Suficiente | Notable | Sobresaliente |
|---|---|---|---|---|---|
| Presentación del sitio y demostración | 30 % | No muestra el sitio o falla durante la demostración. | Muestra el sitio, pero el recorrido es desordenado. | Recorrido ordenado que enseña las partes importantes. | Recorrido fluido que destaca lo mejor del sitio y lo relaciona con el tema. |
| Explicación del código | 40 % | No sabe explicar su código. | Explica qué hace la función, pero no cómo. | Explica la función y la regla CSS línea a línea. | Explicación precisa y con el vocabulario de la unidad; justifica sus decisiones. |
| Respuesta a preguntas | 20 % | No responde o no puede hacer el cambio pedido. | Responde con ayuda; hace el cambio con dificultad. | Responde correctamente y hace el cambio. | Responde con seguridad, hace el cambio enseguida y lo comprueba en el navegador. |
| Comunicación y tiempo | 10 % | Se sale mucho del tiempo o lee todo. | Se ajusta más o menos al tiempo; lee a menudo. | Se ajusta al tiempo y habla con claridad. | Se ajusta al tiempo, habla con claridad y mantiene la atención del público. |
 
### D. Coevaluación de la presentación (20 %)
 
La rellenan tus compañeros. Cada nivel equivale a: Insuficiente 3, Suficiente 5,5, Notable 7,5 y Sobresaliente 9,5. La nota es la media de todos los criterios y de todos los evaluadores.
 
| Criterio | Insuficiente | Suficiente | Notable | Sobresaliente |
|---|---|---|---|---|
| Se entiende de qué trata la web | No queda claro el tema. | Se entiende el tema, pero no para quién es. | Tema y público claros. | Tema y público claros, y me han dado ganas de visitarla. |
| La web funciona y se ve bien | Hay partes que fallan o no se ven. | Funciona, pero se ve descuidada. | Funciona y se ve ordenada. | Funciona sin fallos y el diseño es atractivo. |
| Explica cómo ha hecho su código | No explica el código. | Lo explica, pero no lo he entendido. | Lo he entendido casi todo. | Lo he entendido todo y podría hacerlo yo. |
| Comunicación y tiempo | Se sale mucho del tiempo o lee todo. | Lee a menudo. | Habla con claridad y en su tiempo. | Habla con claridad, en su tiempo y engancha. |
 
---
 
## Ampliaciones opcionales
 
Para quien vaya más rápido. Cuentan para el Sobresaliente del indicador «JavaScript: funcionalidades».
 
1. **¿Dónde estoy?** Un botón que muestra en la página tu latitud y longitud con la API de geolocalización (mira [Publicación web avanzada](publicacion-web.md)).
2. **Mini cuestionario** sobre tu tema: varias preguntas con `prompt()` o con campos del formulario, que cuentan los aciertos y muestran la puntuación.
3. **Dato aleatorio:** un botón que muestra un dato curioso al azar de un array, con `Math.floor(Math.random() * datos.length)`.
4. **Una cuarta página** con un segundo widget distinto del primero.
## Errores frecuentes
 
- **El formulario recarga la página y el mensaje desaparece.** El botón es de tipo `submit`. Usa `<button type="button" onclick="...">`.
- **`Cannot set properties of null` en una página.** Ese archivo JavaScript busca un `id` que no existe en esa página. Usa un archivo por página y enlaza en cada una solo el suyo.
- **La hoja de estilos no se aplica en una página.** Falta el `<link>` o la ruta está mal escrita. Cópialo igual en todas las páginas.
- **El menú cambia de una página a otra.** Copia el mismo `<header>` y `<nav>` en todas y revísalo tras cada cambio.
- **Las imágenes no se ven en GitHub.** El nombre del archivo no coincide exactamente, mayúsculas incluidas (`Foto.JPG` no es `foto.jpg`).
- **`5 + 3` da `53` al sumar campos del formulario.** `.value` siempre devuelve texto: conviértelo con `Number()`.
- **Copiar código de Copilot que no entiendes.** Si no sabes explicarlo en la presentación, no cuenta como tuyo. Pídele que te lo explique o que lo rehaga con lo visto en clase.
- **Dejarlo todo para el último día.** Haz *commit* y *push* al final de cada sesión: si algo se rompe, puedes volver atrás.
---
 
[⬅ Volver a UT1](index.md) · [Ir a Instalación de VS Code](instalacion-vscode.md) · [Ir a HTML5](html.md) · [Ir a Prácticas de HTML5](practicas-html.md) · [Ir a Subir tus ejercicios a GitHub](github.md) · [Ir a CSS](css.md) · [Ir a Prácticas de CSS](practicas-css.md) · [Ir a JavaScript](javascript.md) · [Ir a Prácticas de JavaScript](practicas-js.md) · [Ir a Publicación web avanzada](publicacion-web.md) · [Ir a GitHub Copilot en VS Code](copilot.md)