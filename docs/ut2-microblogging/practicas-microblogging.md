---
title: UT2 — Prácticas de microblogging
---

# Prácticas de microblogging

Los ejercicios están ordenados por dificultad. Los ejercicios 1 y 2 corresponden a [Qué es el microblogging](microblogging.md), y los ejercicios 3 a 5, a [Escribir para microblogging](escribir-microblogging.md).

> **Cómo entregar estos ejercicios.** Escribe cada uno en un archivo Markdown (`.md`) con VS Code. Cuando tengas tu repositorio de la bitácora, guárdalos en la carpeta `ejercicios/` con el nombre que indica cada ejercicio, y haz `commit` y `push`.

---

## Ejercicio 1 — Anatomía de un post

**Objetivo:** reconocer los elementos de un post y deducir por el nombre de usuario si la plataforma es centralizada o federada.

Estos son tres posts de cuentas inventadas:

> **Post A** · **Biblioteca del IES** `@biblioteca_ies` · 24 nov.
>
> 📚 Nuevo club de lectura: primera reunión el martes 1/12 en el recreo. Este mes leemos «Marianela», de Benito Pérez Galdós. Organizamos con `@dpto_lengua`. ¡Apúntate! #ClubDeLectura
>
> [Foto · texto alternativo: «Mesa de la biblioteca con seis ejemplares de Marianela apilados»]
>
> 💬 2 · 🔁 5 · ❤️ 18

> **Post B** · **Club de Atletismo** `@atletismo@deporte.social` · 22 nov.
>
> 🏃 Resultados del cross escolar: 3 medallas para el club en categoría juvenil. Clasificación completa 👉 https://ejemplo.org/cross #CrossEscolar #Atletismo
>
> 💬 4 · 🔁 9 · ⭐ 31

> **Post C** · **Banda del instituto** `@banda-ies.bsky.social` · 20 nov.
>
> 🎶 Ya podéis escuchar nuestra versión del himno del instituto, grabada en el aula de música. ¿Qué os parece?
>
> [Vídeo · texto alternativo: «Cinco alumnos tocan guitarra, bajo, batería y teclado en el aula de música»]
>
> 💬 12 · 🔁 3 · ❤️ 45

**Enunciado**

1. Crea el archivo `ej01-anatomia-post.md`.
2. Copia esta tabla y complétala con los tres posts. Si un post no tiene alguno de los elementos, escribe «—».

   ```markdown
   | Elemento | Post A | Post B | Post C |
   |---|---|---|---|
   | Nombre visible | | | |
   | Nombre de usuario | | | |
   | Menciones | | | |
   | Etiquetas | | | |
   | Enlace | | | |
   | Multimedia | | | |
   | Fecha | | | |
   ```

3. Debajo de la tabla, indica en qué plataforma crees que se ha publicado cada post y si es centralizada, federada o descentralizada. Justifícalo con el nombre de usuario.
4. Explica con tus palabras la diferencia entre `@dpto_lengua` y `#ClubDeLectura` en el post A.

**Resultado esperado:** un archivo Markdown con la tabla completa y dos apartados breves con las respuestas de los pasos 3 y 4.

**Entrega:** `ejercicios/ej01-anatomia-post.md`

---

## Ejercicio 2 — Detecta los fallos

**Objetivo:** identificar los errores más habituales al publicar y corregirlos.

Cada uno de estos posts tiene al menos un fallo:

> **Post 1**
>
> hoy entrenamiento del equipo de fútbol sala!! #futbol #futbolsala #deporte #entreno #instituto #equipo #recreo #viernes #motivacion

> **Post 2**
>
> Mirad qué foto más buena de Lucía dormida en el autobús de la excursión 😂😂
>
> [Foto · texto alternativo: «IMG_4521.jpg»]

> **Post 3**
>
> Recordad: mañana examen de Historia a 1.ª hora, el viernes se entrega el trabajo de Física, el lunes no hay clase y la semana que viene empiezan las inscripciones del torneo de ajedrez.

> **Post 4**
>
> ¡Ya en casa! Si alguien quiere el libro de Química que me sobra, estoy en la calle Mayor 14, 2.º B, toda la tarde 📚

**Enunciado**

1. Crea el archivo `ej02-detecta-fallos.md`.
2. Para cada post, escribe qué fallos tiene. Relaciónalos con lo que has visto en los apuntes: etiquetas, texto alternativo, una idea por post, privacidad…
3. Reescribe cada post corregido. Si el post no debería publicarse de ninguna forma, explica por qué y propón una alternativa.

**Resultado esperado:** para cada uno de los cuatro posts, una lista con sus fallos y la versión corregida.

**Entrega:** `ejercicios/ej02-detecta-fallos.md`

**Ampliación (opcional):** busca en Mastodon o Bluesky la cuenta pública de una institución o de un club. Puedes ver sus posts sin crearte una cuenta. Elige tres posts y analiza si cumplen las buenas prácticas de los apuntes. Escribe solo el nombre de la cuenta y tu análisis; no copies fotos de personas.

---

## Ejercicio 3 — Cabe en 280

**Objetivo:** resumir un aviso largo respetando el límite de caracteres de cada plataforma.

Este es el aviso que el departamento de Música quiere publicar:

> Estimados alumnos y alumnas: desde el departamento de Música nos complace informaros de que, como todos los años, vamos a celebrar el concierto de Navidad del instituto. Este año tendrá lugar el viernes 18 de diciembre a las 12:00 en el salón de actos, y en él participarán el coro, la banda del instituto y todos aquellos alumnos que quieran actuar en solitario o en grupo. Si queréis participar, tenéis que apuntaros en el departamento de Música antes del viernes 4 de diciembre, indicando el nombre del grupo, los participantes y la canción que vais a interpretar. ¡Os esperamos a todos!

**Enunciado**

1. Crea el archivo `ej03-cabe-en-280.md`.
2. Escribe una versión del aviso para **X**, de **280 caracteres como máximo**. Pon lo más importante al principio: qué, cuándo, dónde y cómo apuntarse.
3. Escribe una versión para **Mastodon**, de **500 caracteres como máximo**. Puedes añadir más detalle, pero sigue siendo un post breve.
4. Añade una etiqueta adecuada a cada versión, escrita con mayúscula inicial en cada palabra.
5. Debajo de cada versión, indica cuántos caracteres tiene. Usa la barra de estado de VS Code al seleccionar el texto.

**Resultado esperado:** dos versiones del aviso, con su número de caracteres, que respetan los límites de X y de Mastodon y no pierden ningún dato esencial.

**Entrega:** `ejercicios/ej03-cabe-en-280.md`

---

## Ejercicio 4 — Cuéntalo en un hilo

**Objetivo:** escribir un hilo bien estructurado sobre un tema cercano.

**Enunciado**

1. Crea el archivo `ej04-hilo.md`.
2. Elige un tema: la crónica de un partido, un concierto al que has ido, una excursión, una receta o una recomendación de una serie o un videojuego. Puede ser inventado.
3. Escribe un hilo de **4 o 5 posts** de **280 caracteres como máximo** cada uno. Debe cumplir estas condiciones:
   - El primer post engancha y anuncia que es un hilo (🧵).
   - Todos los posts están numerados (`1/4`, `2/4`…).
   - Cada post se entiende aunque se lea suelto.
   - El último post cierra el tema o enlaza a más información.
4. Revisa que no aparezcan datos personales tuyos ni de otras personas.

**Resultado esperado:** un hilo de 4 o 5 posts numerados que se lee bien de principio a fin y en el que cada post funciona por sí solo.

**Entrega:** `ejercicios/ej04-hilo.md`

**Ampliación (opcional):** adapta el hilo a **Bluesky**, donde el límite es de 300 caracteres, y a **Mastodon**, donde es de 500. ¿Cambia el número de posts? Explica qué has tenido que modificar.

---

## Ejercicio 5 — Una foto con licencia

**Objetivo:** publicar una imagen ajena de forma legal y accesible.

**Enunciado**

1. Crea el archivo `ej05-foto-con-licencia.md`.
2. Busca en [Wikimedia Commons](https://commons.wikimedia.org) una imagen relacionada con una de tus aficiones: un deporte, un instrumento musical, un paisaje de tu provincia…
3. Comprueba en la página de la imagen quién es su autor y qué licencia tiene. Elige una imagen con licencia Creative Commons o de dominio público.
4. Escribe un post de 280 caracteres como máximo que use esa imagen. Incluye:
   - El texto del post.
   - El **texto alternativo** de la imagen.
   - La **atribución**: título, autor, sitio web y licencia.
   - El enlace a la página de la imagen.
5. Explica qué significa cada parte de la licencia de tu imagen (BY, SA…) y qué te obliga a hacer.

**Resultado esperado:** un post con imagen que respeta la licencia, cita correctamente al autor y tiene un texto alternativo que describe la imagen.

**Entrega:** `ejercicios/ej05-foto-con-licencia.md`

**Ampliación (opcional):** busca una imagen con licencia **CC BY-NC** y explica si podrías usarla en el post de una academia de música que cobra por sus clases.

---

[⬅ Volver a UT2](index.md) · [Qué es el microblogging](microblogging.md) · [Escribir para microblogging](escribir-microblogging.md) · [Prácticas de microblogging](practicas-microblogging.md)
