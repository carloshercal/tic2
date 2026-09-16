---
title: UT1 — Prácticas de HTML5
---

# Prácticas de HTML5

Esta página recoge una serie de ejercicios prácticos para ir aplicando, poco a poco, todo lo visto en la página de [HTML5 — Estructura y contenido](html.md). Cada ejercicio se centra en un bloque de contenido concreto (estructura, texto, listas, imágenes, tablas...) y se apoya únicamente en HTML: todavía no usaremos CSS ni JavaScript, así que las páginas se verán "sin estilo" — eso llegará más adelante, en las siguientes UT.

El último ejercicio es un pequeño proyecto de síntesis que combina todo lo anterior, a modo de calentamiento antes del **proyecto web completo** que desarrollaréis con HTML, CSS y JavaScript al terminar esta unidad.

> Guarda cada ejercicio en un archivo `.html` independiente (por ejemplo `ejercicio1.html`, `ejercicio2.html`...) dentro de una misma carpeta de trabajo, y ábrelos con el navegador para comprobar el resultado. Usa un editor de código como Visual Studio Code.

## Ejercicio 1 — Esqueleto de un documento HTML5

**Contenido que practicas:** estructura básica del documento, elementos del `<head>`, comentarios.

Crea un documento HTML5 completo y válido con:

- La declaración `<!DOCTYPE html>` y el atributo `lang="es"` en `<html>`.
- Dentro del `<head>`: codificación de caracteres UTF-8, una `<meta name="description">` que describa la página en una frase, y un `<title>` con tu nombre y el texto "— Página personal".
- Un comentario justo antes del `<body>` indicando tu nombre y la fecha de hoy.
- Dentro del `<body>`, de momento solo un `<h1>` de bienvenida y un `<p>` breve presentándote.

## Ejercicio 2 — Etiquetas de texto y caracteres especiales

**Contenido que practicas:** etiquetas para fragmentos de texto, entidades HTML.

Amplía el párrafo de presentación del ejercicio 1 (o crea uno nuevo) contando algo sobre ti, y utiliza dentro del texto, al menos una vez cada una:

- `<strong>` para resaltar algo importante.
- `<em>` para enfatizar una palabra.
- `<mark>` para destacar un dato como si lo hubieras marcado con rotulador.
- `<abbr title="...">` con alguna sigla o abreviatura.
- Al menos dos entidades HTML de caracteres especiales (por ejemplo `&ntilde;`, `&aacute;` o `&euro;`), aunque tu texto no las necesite de forma natural — el objetivo es practicar la sintaxis.

## Ejercicio 3 — Organización semántica de una página de noticias

**Contenido que practicas:** `<header>`, `<nav>`, `<aside>`, `<section>`, `<article>`, `<footer>`.

Crea una página que simule el "periódico digital" de tu instituto, con esta estructura semántica (recuerda el diagrama de la sección "Organización semántica del `<body>`" en [html.md](html.md)):

- `<header>` con un `<h1>` con el nombre del periódico.
- `<nav>` con una lista (`<ul>`) de al menos 3 enlaces (aunque de momento no lleven a ningún sitio real, usa `href="#"`).
- `<section>` con al menos **dos** `<article>` dentro, cada uno con su propio título (`<h2>`) y un par de párrafos de una noticia inventada.
- `<aside>` con un `<blockquote>` de una frase o cita destacada.
- `<footer>` con el nombre del centro y un dato de contacto inventado.

## Ejercicio 4 — Listas

**Contenido que practicas:** `<ul>`, `<ol>` (con `start`, `reversed`, `type`), `<dl>`.

En una misma página:

- Crea una lista **no ordenada** con las asignaturas que cursas este año.
- Crea una lista **ordenada** con los pasos para publicar una página en GitHub Pages (mínimo 4 pasos), usando el atributo `reversed` para que se numere del último paso al primero.
- Crea una lista de **definiciones** (`<dl>`) con al menos 3 términos técnicos vistos en esta unidad (por ejemplo HTML, CSS, JavaScript) y su definición breve.

## Ejercicio 5 — Imágenes y enlaces

**Contenido que practicas:** `<img>`, `<a>`, atributo `target`.

Crea una pequeña "galería" con:

- Al menos 3 imágenes (`<img>`) con su `src`, un `alt` descriptivo en cada una, y `width`/`height` fijados.
- Debajo de cada imagen, un enlace que abra la imagen en una pestaña nueva (`target="_blank"`).
- Un enlace **interno** a otro de tus ejercicios (por ejemplo al del ejercicio 1).
- Un enlace `mailto:` a un correo inventado.
- Un enlace con el atributo `download` a un archivo (puede no existir realmente, es para practicar la sintaxis).

## Ejercicio 6 — Tablas

**Contenido que practicas:** `<table>`, `<caption>`, `<thead>`/`<tbody>`/`<tfoot>`, `<th>`/`<td>`, `rowspan`/`colspan`.

Construye la tabla de tu horario de clases de esta semana (o, si lo prefieres, una tabla de notas de una evaluación) con:

- Un `<caption>` con el título de la tabla.
- Un `<thead>` con la fila de cabeceras (`<th>`) — por ejemplo, los días de la semana.
- Un `<tbody>` con las filas de datos.
- Al menos una celda que use `rowspan` o `colspan` (por ejemplo, un recreo que ocupe todas las columnas, o una asignatura de dos horas seguidas).

## Ejercicio 7 — Multimedia

**Contenido que practicas:** `<video>`, `<audio>`, `<iframe>`.

Crea una página con:

- Un `<video>` con controles (`controls`), que ofrezca el mismo vídeo en dos formatos distintos mediante dos etiquetas `<source>` (los archivos pueden no existir realmente; el objetivo es la sintaxis).
- Un `<audio>` con controles.
- Un `<iframe>` que incruste un vídeo real de YouTube (usa la opción "Insertar" de YouTube para copiar la URL de tipo `embed`), con su `title` correspondiente.

## Ejercicio 8 — Formulario de inscripción

**Contenido que practicas:** `<form>`, `<input>` (varios `type`), `<label>`, `<textarea>`, `<select>`/`<option>`, `<fieldset>`/`<legend>`.

Crea un formulario de inscripción a una actividad extraescolar inventada, con:

- `<fieldset>` y `<legend>` agrupando los datos personales: nombre (`text`), correo (`email`), teléfono (`tel`) y fecha de nacimiento (`date`). Cada campo con su `<label for="...">` correctamente asociado.
- Un grupo de `<input type="radio">` para elegir turno (mañana / tarde), con uno marcado por defecto (`checked`).
- Un `<select>` con al menos 3 `<option>` para elegir la actividad.
- Un `<textarea>` para "observaciones", con `rows` y `cols`.
- Un `<input type="checkbox">` para aceptar las condiciones (obligatorio marcarlo, aunque la validación real la veremos más adelante).
- Un botón `submit` para enviar el formulario y uno `reset` para limpiarlo.

## Ejercicio 9 — Proyecto de síntesis: mi página web personal

**Contenido que practicas:** todo lo anterior, combinado en un sitio de varias páginas.

Este ejercicio es un pequeño ensayo del proyecto final de la unidad. Crea un mini-sitio de **3 páginas enlazadas entre sí** (`index.html`, `sobre-mi.html`, `contacto.html`) sobre un tema que te interese (un hobby, un deporte, una serie, un grupo de música...):

- Las tres páginas deben compartir la misma estructura semántica (`header` con `nav` que enlace a las tres páginas, y `footer`).
- `index.html`: portada con una breve introducción al tema y al menos una imagen.
- `sobre-mi.html`: por qué te interesa el tema, con una lista y alguna etiqueta de texto (`strong`, `em`...).
- `contacto.html`: un formulario sencillo de contacto (nombre, correo y mensaje).
- Al menos un enlace externo a una web real relacionada con el tema, abierto en pestaña nueva.

> Este mini-sitio es solo el punto de partida: cuando lleguemos a CSS y JavaScript, iremos dándole estilo y comportamiento a estas mismas páginas (o a una versión ampliada).

---

[⬅ Volver a UT1](index.md) · [Ir a HTML5](html.md) · [Ir a CSS](css.md) · [Ir a JavaScript](javascript.md) · [Ir a Publicación web avanzada](publicacion-web.md)
