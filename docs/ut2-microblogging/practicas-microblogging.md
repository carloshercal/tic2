---
title: UT2 — Prácticas de microblogging
---

# Prácticas de microblogging

La práctica principal de la unidad es el **[Ejercicio 6 — Mi bitácora](#ejercicio-6)**: en ella aplicas todo lo que has visto en [Qué es el microblogging](microblogging.md) y [Escribir para microblogging](escribir-microblogging.md).

Los **ejercicios 1 a 5 son opcionales**. Sirven para repasar la teoría antes de ponerte con la bitácora o si quieres practicar más. Los ejercicios 3, 4 y 5 te vienen bien para preparar el hilo y la foto con licencia que pide el ejercicio 6.

> **Cómo entregar los ejercicios opcionales.** Escribe cada uno en un archivo Markdown (`.md`) con VS Code y guárdalo en la carpeta `ejercicios/` de tu repositorio de la bitácora, con el nombre que indica cada ejercicio. Después, haz `commit` y `push`.

---

## Ejercicio 1 — Anatomía de un post (opcional)

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

## Ejercicio 2 — Detecta los fallos (opcional)

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

## Ejercicio 3 — Cabe en 280 (opcional)

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

## Ejercicio 4 — Cuéntalo en un hilo (opcional)

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

## Ejercicio 5 — Una foto con licencia (opcional)

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

## Ejercicio 6 — Mi bitácora {#ejercicio-6}

**Objetivo:** publicar en tu bitácora contenidos breves de todos los tipos (texto, foto, cita, enlace, diálogo, vídeo y música), de forma clara, accesible y respetando los derechos de autor.

Antes de empezar, monta tu bitácora siguiendo [Montar tu bitácora](bitacora.md). Allí tienes también el código de cada tipo de post.

**Enunciado**

1. **Elige el tema** de tu bitácora: un deporte, un grupo de música, un videojuego, la cocina, tu pueblo, el huerto del instituto… Escríbelo en la cabecera, con un título y una descripción.
2. **Publica al menos un post de cada uno de los 7 tipos**, con su tipo indicado en `<span class="tipo">`:
   - **Texto:** una idea, un aviso o una opinión.
   - **Foto:** una foto **propia**, sin personas reconocibles, con su texto alternativo.
   - **Cita:** una frase con su autor (y la obra, si la tiene).
   - **Enlace:** una web o noticia con tu comentario, y un texto del enlace que diga adónde lleva.
   - **Diálogo:** una conversación corta, real o inventada.
   - **Vídeo:** un vídeo insertado con su código de insertar (YouTube: Compartir → Insertar).
   - **Música:** una canción insertada desde una plataforma de música o un audio propio.
3. **Publica una foto ajena con licencia.** Busca en [Wikimedia Commons](https://commons.wikimedia.org) una imagen con licencia Creative Commons o de dominio público. Descárgala en `img/` y publícala en un post de foto con:
   - su **texto alternativo**;
   - la **atribución** en el `<figcaption>`: título, autor, sitio y licencia, con enlace a la página de la imagen.
4. **Publica un hilo** de 3 o 4 posts seguidos sobre el mismo tema. Cumple las normas de los apuntes:
   - el primero anuncia que es un hilo (🧵);
   - todos van numerados (`1/3`, `2/3`…);
   - cada uno se entiende aunque se lea suelto.
5. **Revisa cada post** antes de publicarlo:
   - El texto tiene **280 caracteres como máximo**, sin contar las etiquetas HTML. Selecciona solo el texto en VS Code y mira la barra de estado.
   - Lleva de 1 a 3 **etiquetas**, con mayúscula inicial en cada palabra.
   - Una idea por post y lo importante al principio.
   - Ortografía cuidada.
6. **Comprueba tu bitácora entera**:
   - Los posts están en orden, del más reciente (arriba) al más antiguo.
   - Firmas con tu alias y no aparece ningún dato personal tuyo ni de otras personas.
   - Todas las imágenes tienen `alt`.
   - Ya no queda nada de la plantilla: ni `@tu_alias`, ni «Nombre visible», ni los posts de ejemplo.
7. Haz `commit` y `push` cada vez que termines un post, y comprueba que se ve en tu bitácora publicada.

**Resultado esperado:** una bitácora publicada en `https://iesviadelaplata-tic2-2026.github.io/ut2-microblogging-tuusuario/` con, como mínimo, 10 posts: uno de cada tipo, la foto con licencia y un hilo de 3 posts. Todos respetan el límite de 280 caracteres, usan bien las etiquetas y no contienen datos personales.

**Entrega:** tu repositorio de la bitácora (`index.html`, `css/estilos.css` e `img/`). En Teams entregarás el enlace a tu bitácora publicada. Qué más se entrega y cómo se evalúa: [Entrega y evaluación](evaluacion.md).

**Ampliación (opcional):**

- Adapta tus colores, tipografía y bordes en `css/estilos.css` para que la bitácora tenga un estilo propio y acorde con su tema.
- Publica un segundo hilo, o una versión de tu hilo para Mastodon (500 caracteres) con menos posts.
- Añade una **ficha** a la cabecera, como el perfil de una red social: una foto o dibujo que no sea tu cara, con su `alt`, y una frase de presentación.

---

[⬅ Volver a UT2](index.md) · [Qué es el microblogging](microblogging.md) · [Escribir para microblogging](escribir-microblogging.md) · [Montar tu bitácora](bitacora.md) · [Prácticas de microblogging](practicas-microblogging.md) · [Entrega y evaluación](evaluacion.md)