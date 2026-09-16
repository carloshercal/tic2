---
title: UT1 — Publicación web avanzada
---

# Publicación web avanzada: Widgets, FTP y Geolocalización

Una vez que una página está construida con HTML, CSS y JavaScript, quedan dos pasos para convertirla en un sitio web "de nivel avanzado": enriquecerla con componentes externos (**widgets**) y **publicarla** en un servidor al que cualquiera pueda acceder desde Internet. A esto se añade una funcionalidad muy habitual en la web actual: la **geolocalización** del usuario.

## Widgets

Un **widget** es un componente interactivo, desarrollado por terceros, que se incrusta dentro de una página web sin tener que programarlo desde cero: un mapa, un reproductor de vídeo, un botón para compartir en redes sociales, un chat de atención al cliente, la previsión del tiempo, un timeline de una red social, etc.

Los proveedores del servicio suelen entregar el widget en uno de estos dos formatos, que ya conoces de la página de [HTML5](html.md):

- Un fragmento de código `<iframe>` que carga el widget desde el servidor del proveedor.
- Un fragmento de código `<script>` que genera el widget dinámicamente con JavaScript.

```html
<!-- Widget de mapa mediante iframe -->
<iframe
  src="https://www.google.com/maps/embed?..."
  width="600" height="450"
  style="border:0"
  loading="lazy">
</iframe>

<!-- Widget de red social mediante script -->
<script async src="https://platform.twitter.com/widgets.js"></script>
```

Al integrar un widget externo conviene comprobar que no penaliza demasiado el tiempo de carga de la página (usar `loading="lazy"` cuando sea posible) y que no compromete la privacidad de quien visita la web (algunos widgets de redes sociales instalan cookies de seguimiento).

## Publicación en servidores remotos. FTP

Para que una página web sea accesible desde cualquier lugar es necesario **alojarla** (*hosting*) en un servidor web conectado permanentemente a Internet, y **transferir** hasta él los archivos que componen el sitio (HTML, CSS, JS, imágenes...).

**FTP** (*File Transfer Protocol*, protocolo de transferencia de archivos) es el protocolo clásico para subir archivos desde el ordenador local hasta un servidor remoto. Para usarlo hace falta:

- Un **servidor FTP** en el hosting, con una dirección (host), un puerto (21 por defecto) y unas credenciales (usuario y contraseña) que proporciona la empresa de alojamiento.
- Un **cliente FTP**: un programa que se conecta al servidor y permite arrastrar archivos entre el equipo local y el remoto. Los más habituales son **FileZilla**, **WinSCP** o **Cyberduck**.

Pasos habituales para publicar un sitio por FTP:

1. Conectar el cliente FTP al servidor con el host, usuario y contraseña facilitados por el hosting.
2. Navegar hasta la carpeta pública del servidor (habitualmente `public_html` o `www`).
3. Subir (*upload*) los archivos del sitio manteniendo la misma estructura de carpetas que en local.
4. Comprobar el resultado visitando el dominio del sitio en el navegador.

Por seguridad, hoy en día se recomienda usar **FTPS** o **SFTP** (variantes de FTP cifradas sobre SSL/TLS o SSH) en lugar del FTP tradicional, que envía usuario y contraseña sin cifrar.

> **Nota:** el sitio de esta propia asignatura, publicado con **GitHub Pages**, no usa FTP: la publicación se hace con `git push` a la rama `main`, y es GitHub quien construye y sirve el sitio automáticamente. FTP sigue siendo, no obstante, el método más habitual para publicar en un hosting "tradicional" (por ejemplo, en un dominio propio contratado a una empresa de hosting).

## Geolocalización

La **API de Geolocalización de HTML5** permite que una página web obtenga la ubicación geográfica de quien la visita (con su permiso explícito), para por ejemplo mostrarla en un mapa o personalizar contenido según la zona.

El acceso se realiza en JavaScript a través del objeto `navigator.geolocation`:

```js
if (navigator.geolocation) {
  navigator.geolocation.getCurrentPosition(mostrarPosicion, mostrarError);
} else {
  console.log("Tu navegador no soporta geolocalización.");
}

function mostrarPosicion(posicion) {
  const lat = posicion.coords.latitude;
  const lon = posicion.coords.longitude;
  console.log("Latitud: " + lat + ", Longitud: " + lon);
}

function mostrarError(error) {
  console.log("No se pudo obtener la ubicación: " + error.message);
}
```

- `getCurrentPosition(exito, error)`: pide la posición actual una sola vez. Recibe dos funciones: una que se ejecuta si se obtiene la ubicación (con las coordenadas) y otra si falla (por ejemplo, si el usuario deniega el permiso).
- `watchPosition(exito, error)`: como `getCurrentPosition`, pero sigue informando cada vez que la posición cambia (útil para aplicaciones de seguimiento en tiempo real).
- `posicion.coords.latitude` / `posicion.coords.longitude`: coordenadas obtenidas; también incluye `accuracy` (precisión, en metros).

Puntos importantes:

- El navegador **siempre pide permiso** al usuario antes de compartir su ubicación.
- Por motivos de seguridad y privacidad, la API de Geolocalización solo funciona en páginas servidas mediante **HTTPS** (o en `localhost` durante el desarrollo).
- Las coordenadas obtenidas se pueden usar, por ejemplo, para centrar un widget de mapa (como el `<iframe>` de Google Maps visto más arriba) en la posición del usuario.

---

[⬅ Volver a UT1](index.md) · [Ir a HTML5](html.md) · [Ir a Prácticas de HTML5](practicas-html.md) · [Ir a CSS](css.md) · [Ir a JavaScript](javascript.md)