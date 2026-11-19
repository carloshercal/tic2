---
title: UT2 — Qué es el microblogging
---

# Qué es el microblogging

El **microblogging** consiste en publicar **mensajes breves** (*posts*) que aparecen ordenados en el tiempo y que otras personas pueden leer, responder y compartir casi al instante. Es un blog en miniatura: en lugar de artículos largos, publicaciones cortas y frecuentes.

Sus rasgos principales:

- **Brevedad:** cada plataforma limita la longitud del texto.
- **Inmediatez:** se publica en segundos, desde el móvil o el ordenador.
- **Cronología:** las publicaciones se muestran en un *timeline* o *feed*, de la más reciente a la más antigua o según lo que decida el algoritmo de la plataforma.
- **Interacción:** se puede responder, compartir, citar o marcar como «me gusta».
- **Multimedia:** además de texto, un post puede llevar fotos, vídeo, audio, enlaces o encuestas.

> Ejemplo de post de la cuenta del instituto:
>
> 📢 El jueves 26 hay jornada de puertas abiertas en el IES. ¡Ven a conocer los ciclos y el Bachillerato! Más información en la web. #PuertasAbiertas

## Plataformas de microblogging

Hay varias plataformas, y cada una tiene sus propias normas, su público y sus límites. Estos son los límites de texto de las principales a noviembre de 2026; las plataformas los cambian a menudo, así que conviene comprobarlos en el propio editor de cada una:

| Plataforma | Límite de texto | Tipo | Formato del usuario |
|---|---|---|---|
| **X** (antes Twitter) | 280 caracteres (más con suscripción de pago) | Centralizada | `@usuario` |
| **Threads** (Meta) | 500 caracteres | Centralizada, conectada en parte al fediverso | `@usuario` |
| **Bluesky** | 300 caracteres | Descentralizada (protocolo AT) | `@usuario.bsky.social` |
| **Mastodon** | 500 caracteres por defecto (depende del servidor) | Federada (fediverso) | `@usuario@servidor` |

Otras redes, como Instagram, TikTok o LinkedIn, también permiten publicar mensajes cortos, pero su contenido principal es otro: imagen, vídeo o perfil profesional.

### Centralizadas y federadas

- **Centralizada:** una sola empresa controla los servidores, las normas y el algoritmo. Si la empresa cierra tu cuenta o cambia las reglas, no puedes llevarte tus seguidores a otra parte. Es el caso de X.
- **Federada:** hay muchos servidores independientes, llamados **instancias**, que se comunican con un protocolo común (**ActivityPub**). Una cuenta de un servidor puede seguir y responder a cuentas de otros. El conjunto de todos esos servidores se llama **fediverso**. Mastodon es el ejemplo más conocido.

Para distinguirlas, fíjate en el nombre de usuario. En Mastodon incluye el servidor, igual que una dirección de correo electrónico incluye el dominio:

```text
@club_baloncesto              → cuenta de una plataforma centralizada
@club_baloncesto@mastodon.social  → usuario «club_baloncesto» del servidor mastodon.social
```

## Anatomía de un post

Casi todas las plataformas comparten los mismos elementos:

| Elemento | Qué es | Ejemplo |
|---|---|---|
| **Autor** | Nombre visible, nombre de usuario (*handle*) y foto de perfil | IES Vía de la Plata · `@iesviadelaplata` |
| **Texto** | El mensaje, dentro del límite de la plataforma | «Mañana hay excursión…» |
| **Mención** | Nombre de usuario precedido de `@`. Avisa a esa cuenta | `@biblioteca_ies` |
| **Etiqueta** (*hashtag*) | Palabra precedida de `#`. Agrupa los posts sobre un tema | `#SemanaDeLaCiencia` |
| **Enlace** | Una URL. Muchas plataformas generan una tarjeta con vista previa | `https://…` |
| **Multimedia** | Imagen, vídeo, audio o GIF, con su **texto alternativo** | Foto del laboratorio |
| **Fecha y hora** | Cuándo se publicó | 20 nov. 2026, 9:15 |
| **Interacciones** | Responder, compartir (*repost*), citar y «me gusta» | 💬 3 · 🔁 12 · ❤️ 40 |

> Ejemplo con todos los elementos:
>
> **IES Vía de la Plata** `@iesviadelaplata` · 20 nov.
>
> 🔬 Hoy arranca la #SemanaDeLaCiencia con un taller de robótica preparado por 1.º de Bachillerato. Gracias a `@biblioteca_ies` por prestarnos el espacio. Programa completo 👉 https://…
>
> [Foto · texto alternativo: «Cuatro alumnos montan un robot sobre una mesa del laboratorio»]
>
> 💬 3 · 🔁 12 · ❤️ 40

### El texto alternativo

El **texto alternativo** describe una imagen para quien no puede verla, por ejemplo una persona ciega que usa un lector de pantalla. Las plataformas de microblogging tienen un campo para escribirlo al subir la foto. Es lo mismo que el atributo `alt` de HTML.

```text
❌ «foto»
❌ «IMG_2034.jpg»
✅ «Cuatro alumnos montan un robot sobre una mesa del laboratorio»
```

### Las etiquetas

Una etiqueta sirve para que tu post aparezca cuando alguien busca o sigue ese tema. Escríbela con la **inicial de cada palabra en mayúscula** (*CamelCase*): se lee mejor y los lectores de pantalla la pronuncian correctamente.

```text
❌ #semanadelaciencia
✅ #SemanaDeLaCiencia
```

## Tipos de contenido

En esta unidad vas a publicar contenidos breves de distintos tipos, que son los que recoge el currículo:

| Tipo | Ejemplo |
|---|---|
| **Texto** | Un aviso, una opinión o una reflexión breve |
| **Foto** | Una imagen del entrenamiento con su descripción |
| **Diálogo** | Una conversación corta, como una entrevista rápida a un compañero |
| **Enlace** | Una noticia o web interesante con un comentario tuyo |
| **Cita** | Una frase de un libro o de una persona, con su autor |
| **Vídeo** | Un clip corto insertado o enlazado |
| **Música** | Una canción recomendada desde una plataforma de música |

## Un post también es HTML

Cuando ves un post en el navegador, lo que tienes delante es HTML, CSS y JavaScript, lo mismo que has usado en la UT1. Un post encaja con la etiqueta semántica `<article>`, porque es un contenido independiente que tiene sentido por sí solo:

```html
<article class="post">
  <header>
    <h2>IES Vía de la Plata</h2>
    <p>@iesviadelaplata · <time datetime="2026-11-20T09:15">20 nov.</time></p>
  </header>
  <p>🔬 Hoy arranca la <a href="#">#SemanaDeLaCiencia</a> con un taller de robótica.</p>
  <img src="img/taller-robotica.jpg" alt="Cuatro alumnos montan un robot sobre una mesa del laboratorio">
  <footer>
    <p>💬 3 · 🔁 12 · ❤️ 40</p>
  </footer>
</article>
```

Esta estructura es la base de la **bitácora** que vas a construir en esta unidad: tu propio microblog, publicado en GitHub Pages.

## Errores frecuentes

- **Confundir mención y etiqueta.** `@` es para una cuenta y avisa a esa persona; `#` es para un tema y no avisa a nadie.
- **Llenar el post de etiquetas.** Con 1 a 3 etiquetas relevantes basta; más de eso parece *spam* y se lee peor.
- **Publicar imágenes sin texto alternativo**, o poner como alternativo el nombre del archivo.
- **Pensar que todas las plataformas cuentan igual.** Un texto que cabe en Mastodon (500) puede no caber en X (280) ni en Bluesky (300).
- **Escribir el nombre de usuario de Mastodon sin el servidor.** `@usuario` solo no basta para encontrar una cuenta del fediverso: hace falta `@usuario@servidor`.
- **Publicar datos personales**, como fotos de otras personas sin su permiso, tu dirección, tu horario o tu ubicación. Lo que se publica en Internet es difícil de borrar del todo.

---

[⬅ Volver a UT2](index.md) · [Qué es el microblogging](microblogging.md)
