---
title: UT2 — Montar tu bitácora
---

# Montar tu bitácora

Tu **bitácora** es un microblog personal: una página web con tus posts, del más reciente al más antiguo. La harás con HTML y CSS, como en la UT1, y se publicará en Internet con **GitHub Pages** cada vez que hagas `push`.

## Antes de empezar: tu bitácora es pública

El repositorio y la web publicada los puede ver **cualquier persona**. Por eso:

- Firma con un **alias**, nunca con tu nombre y apellidos.
- No publiques **datos personales** tuyos ni de otras personas.
- No publiques **fotos de otras personas** sin su permiso.
- Usa solo contenidos **propios** o con una **licencia que lo permita**, y cita al autor y la licencia.

Repasa [Escribir para microblogging](escribir-microblogging.md) si tienes dudas.

## 1. Acepta la invitación

Recibirás un correo de GitHub con una invitación al repositorio `ut2-microblogging-tuusuario`. Acéptala antes de seguir, igual que hiciste en la UT1 ([Subir tus ejercicios a GitHub](../ut1-html-css-js/github.md)).

## 2. Oculta tu correo electrónico

En un repositorio público, cada `commit` muestra el correo de quien lo hizo. GitHub te da un correo privado para usar en su lugar:

1. En GitHub, entra en tu foto de perfil → **Settings** → **Emails**.
2. Marca **Keep my email addresses private**.
3. Debajo aparece tu correo privado, con esta forma: `12345678+tuusuario@users.noreply.github.com`. Cópialo.
4. Cuando hayas clonado el repositorio (paso 3), abre la terminal de VS Code dentro de él y escribe:

```bash
git config user.email "12345678+tuusuario@users.noreply.github.com"
```

> ⚠️ Ese correo es **solo un ejemplo**. Escribe **el tuyo**, el que copiaste en Settings → Emails: el número y el usuario son distintos para cada persona.

Este correo solo se aplica a este repositorio, así que no afecta a otros usuarios del ordenador del aula.

## 3. Clona el repositorio y ábrelo

Clónalo en VS Code como en la UT1 y ábrelo con **Live Server**. Verás una bitácora de ejemplo con tres posts. Esta es su estructura:

```text
index.html           ← tu bitácora
css/estilos.css      ← estilos
img/                 ← tus imágenes
ejercicios/          ← ejercicios opcionales de las prácticas
README.md
```

## 4. Personaliza la cabecera y los colores

En `index.html`, cambia el lema, el título y la descripción de la cabecera, y escribe tu alias en el pie de la página:

```html
<header class="cabecera">
  <span class="lema">Bitácora de TIC II</span>
  <h1>Diario de una corredora</h1>
  <p>Entrenamientos, carreras y todo lo que aprendo corriendo.</p>
</header>
```

Para cambiar los colores, abre `css/estilos.css`. Al principio tienes la lista de colores de la plantilla y para qué se usa cada uno. Busca cada código con **Ctrl+F** y cámbialo por otro de la [carta de colores](https://htmlcolorcodes.com/color-chart/).

## 5. Así es un post

Cada post es un `<article class="post">` con tres partes: cabecera (autor, alias, fecha y tipo de post), contenido y pie (interacciones). El post más reciente va **arriba**.

```html
<article class="post">
  <header class="post-cabecera">
    <h2>Diario de una corredora</h2>
    <p class="meta">
      @corre_lola · <time datetime="2026-11-26">26 nov.</time>
      <span class="tipo">Texto</span>
    </p>
  </header>
  <p>Hoy, primer entrenamiento con lluvia: 8 km y ni una queja 💪 <a class="etiqueta" href="#">#Running</a></p>
  <footer class="post-pie">
    <p>💬 0 · 🔁 0 · ❤️ 0</p>
  </footer>
</article>
```

Para publicar un post nuevo, copia un `<article>` entero, pégalo **encima** del primero y cambia el contenido, la fecha y el tipo.

## 6. Escribe tu primer post y publícalo

1. Borra los posts de ejemplo y escribe un post de **Texto** que presente tu bitácora.
2. Haz `commit` y `push`.
3. Espera uno o dos minutos y abre tu bitácora publicada:

```text
https://iesviadelaplata-tic2-2026.github.io/ut2-microblogging-tuusuario/
```

4. Sigue con el [Ejercicio 6 — Mi bitácora](practicas-microblogging.md#ejercicio-6): publicar un post de cada tipo, un hilo y una foto con licencia.

## Tipos de post

Estos son los fragmentos de contenido para cada tipo de post. Van entre la cabecera y el pie del `<article>`, y en la cabecera cambia la etiqueta `<span class="tipo">`.

**Foto.** Va en un `<figure>`: la imagen, el tipo de post (que flota sobre la foto) y un `<figcaption>` con el autor y la licencia. Con foto, el `<span class="tipo">` va dentro del `<figure>` y no en la cabecera.

```html
<figure class="post-imagen">
  <img src="img/pista.jpg" alt="Pista de atletismo vacía al amanecer, con niebla">
  <span class="tipo">Foto</span>
  <figcaption>Foto propia.</figcaption>
</figure>
<p>Así estaba la pista a las 8:00. <a class="etiqueta" href="#">#Atletismo</a></p>
```

**Cita.** Un `<blockquote>` con la frase y, en su `<footer>`, el autor y la obra en `<cite>`.

```html
<blockquote>
  <p>«Caminante, no hay camino, se hace camino al andar».</p>
  <footer>— Antonio Machado, <cite>Campos de Castilla</cite></footer>
</blockquote>
<p>Mi frase para los días de cuesta. <a class="etiqueta" href="#">#Motivación</a></p>
```

**Enlace.** Un comentario tuyo y el enlace, con un texto que diga adónde lleva.

```html
<p>Calendario de carreras populares de la provincia para este invierno 👉 <a href="https://ejemplo.org/carreras">ver calendario</a> <a class="etiqueta" href="#">#Running</a></p>
```

**Diálogo.** Cada intervención en un párrafo, con el nombre en `<strong>`, dentro de un `<div class="dialogo">`.

```html
<div class="dialogo">
  <p><strong>Yo:</strong> ¿Cuántos kilómetros hacemos hoy?</p>
  <p><strong>Entrenadora:</strong> Diez. Y los dos últimos, rápidos.</p>
  <p><strong>Yo:</strong> 😅</p>
</div>
```

**Vídeo.** Un `<iframe>` con el código de insertar de la plataforma (en YouTube: Compartir → Insertar), o un `<video>` si el vídeo es tuyo.

```html
<iframe src="https://www.youtube.com/embed/CODIGO-DEL-VIDEO" title="Resumen de la carrera popular"></iframe>
<p>Resumen de la carrera del domingo. <a class="etiqueta" href="#">#Running</a></p>
```

**Música.** Un `<iframe>` con el código de insertar de la plataforma de música, o un `<audio>` si el audio es tuyo.

```html
<audio src="audio/mi-cancion.mp3" controls></audio>
<p>La canción que más escucho corriendo esta semana 🎧 <a class="etiqueta" href="#">#MúsicaParaCorrer</a></p>
```

## Errores frecuentes

- **Hacer el primer `push` sin configurar el correo privado.** Tu correo real queda en ese `commit`. Configúralo antes, en el paso 2.
- **Esperar ver los cambios publicados al instante.** GitHub Pages tarda uno o dos minutos; recarga la página pasado ese tiempo.
- **Mirar la web publicada para saber si el código funciona.** Mientras trabajas, usa Live Server. La web publicada solo muestra lo que has subido con `push`.
- **Pegar el post nuevo debajo de los demás.** En un microblog, lo más reciente va arriba.
- **Olvidar cambiar el tipo de post** o dejar el `@tu_alias` de la plantilla.
- **Rutas de imagen que funcionan en tu ordenador pero no en GitHub.** GitHub distingue mayúsculas y minúsculas: `img/Pista.JPG` y `img/pista.jpg` son archivos distintos.
- **Imágenes sin `alt`**, o con el nombre del archivo como texto alternativo.

---

[⬅ Volver a UT2](index.md) · [Qué es el microblogging](microblogging.md) · [Escribir para microblogging](escribir-microblogging.md) · [Montar tu bitácora](bitacora.md) · [Prácticas de microblogging](practicas-microblogging.md)