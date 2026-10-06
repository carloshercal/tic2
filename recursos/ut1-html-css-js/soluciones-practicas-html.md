# Soluciones — Prácticas de HTML5 (UT1)

> **Documento interno para el profesorado.** No se publica en el sitio de GitHub Pages (vive en `/recursos`, fuera de `/docs`); repártelo por Teams si quieres dar el código resuelto al alumnado, por ejemplo después de la corrección en clase. Enunciados en [`docs/ut1-html-css-js/practicas-html.md`](../../docs/ut1-html-css-js/practicas-html.md).

Estas son soluciones **de referencia**: hay más de una forma correcta de resolver cada ejercicio, y conviene aceptar variantes del alumnado siempre que cumplan los requisitos pedidos.

## Ejercicio 1 — Esqueleto de un documento HTML5

```html
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="description" content="Página personal de ejemplo para practicar la estructura básica de HTML5.">
  <title>Carlos — Página personal</title>
</head>
<body>
  <!-- Carlos Hernández - 16/09/2026 -->
  <h1>¡Bienvenido/a a mi página!</h1>
  <p>Hola, me llamo Carlos y esta es mi primera página web hecha con HTML5.</p>
</body>
</html>
```

## Ejercicio 2 — Etiquetas de texto y caracteres especiales

```html
<p>
  Me llamo Carlos y soy <strong>profesor de Inform&aacute;tica</strong> en un
  instituto de <em>Castilla y Le&oacute;n</em>. Este a&ntilde;o estoy dando
  clase de <mark>TIC II</mark>, una asignatura de 2&ordm; de Bachillerato.
  Trabajo con <abbr title="HyperText Markup Language">HTML</abbr> desde hace
  varios a&ntilde;os y me gusta mucho ense&ntilde;arlo.
</p>
```

(Entidades usadas: `&aacute;`, `&oacute;`, `&ntilde;`, `&ordm;`.)

## Ejercicio 3 — Organización semántica de una página de noticias

```html
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <title>El Diario del Instituto</title>
</head>
<body>
  <header>
    <h1>El Diario del Instituto</h1>
  </header>

  <nav>
    <ul>
      <li><a href="#">Portada</a></li>
      <li><a href="#">Deportes</a></li>
      <li><a href="#">Actividades</a></li>
    </ul>
  </nav>

  <aside>
    <blockquote>"La educación es el arma más poderosa para cambiar el mundo."</blockquote>
  </aside>

  <section>
    <article>
      <h2>El instituto estrena laboratorio de informática</h2>
      <p>Este curso se ha renovado por completo el aula de informática.</p>
      <p>Los nuevos equipos permitirán trabajar con las últimas herramientas.</p>
    </article>
    <article>
      <h2>Comienza el curso 2026/2027</h2>
      <p>El alumnado ha vuelto a las aulas con muchas ganas de aprender.</p>
      <p>Este año se incorporan nuevas asignaturas optativas.</p>
    </article>
  </section>

  <footer>
    <p>IES Ejemplo — Tel: 000 000 000</p>
  </footer>
</body>
</html>
```

## Ejercicio 4 — Listas

```html
<h2>Mis asignaturas</h2>
<ul>
  <li>TIC II</li>
  <li>Matemáticas</li>
  <li>Historia de España</li>
  <li>Inglés</li>
</ul>

<h2>Cómo publicar en GitHub Pages</h2>
<ol reversed>
  <li>Activar GitHub Pages en Settings → Pages</li>
  <li>Hacer <code>git push</code> al repositorio</li>
  <li>Crear el archivo <code>index.html</code> o <code>index.md</code></li>
  <li>Crear el repositorio en GitHub</li>
</ol>

<h2>Glosario</h2>
<dl>
  <dt>HTML</dt>
  <dd>Lenguaje de marcado que estructura el contenido de una página web.</dd>
  <dt>CSS</dt>
  <dd>Lenguaje que define el aspecto visual de una página web.</dd>
  <dt>JavaScript</dt>
  <dd>Lenguaje de programación que añade comportamiento dinámico a una página.</dd>
</dl>
```

## Ejercicio 5 — Imágenes y enlaces

```html
<figure>
  <img src="img/foto1.jpg" alt="Fachada del instituto" width="300" height="200">
  <p><a href="img/foto1.jpg" target="_blank">Ver imagen completa</a></p>
</figure>

<figure>
  <img src="img/foto2.jpg" alt="Patio del instituto" width="300" height="200">
  <p><a href="img/foto2.jpg" target="_blank">Ver imagen completa</a></p>
</figure>

<figure>
  <img src="img/foto3.jpg" alt="Aula de informática" width="300" height="200">
  <p><a href="img/foto3.jpg" target="_blank">Ver imagen completa</a></p>
</figure>

<p><a href="ejercicio1.html">Volver al ejercicio 1</a></p>
<p><a href="mailto:carlos@ejemplo.com">Escríbeme un correo</a></p>
<p><a href="apuntes.pdf" download>Descargar apuntes</a></p>
```

## Ejercicio 6 — Tablas

```html
<table border="1">
  <caption>Horario semanal</caption>
  <thead>
    <tr>
      <th>Hora</th><th>Lunes</th><th>Martes</th><th>Miércoles</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>8:30 - 9:25</td><td>TIC II</td><td>Matemáticas</td><td>TIC II</td>
    </tr>
    <tr>
      <td colspan="4">Recreo</td>
    </tr>
    <tr>
      <td>9:55 - 10:50</td><td rowspan="2">Inglés</td><td>Historia</td><td>Matemáticas</td>
    </tr>
    <tr>
      <td>10:50 - 11:45</td><td>Historia</td><td>TIC II</td>
    </tr>
  </tbody>
</table>
```

## Ejercicio 7 — Multimedia

```html
<video width="640" height="480" controls>
  <source src="video.mp4" type="video/mp4">
  <source src="video.ogg" type="video/ogg">
  Tu navegador no soporta la etiqueta video.
</video>

<audio controls>
  <source src="audio.mp3" type="audio/mpeg">
  <source src="audio.ogg" type="audio/ogg">
  Tu navegador no soporta el elemento audio.
</audio>

<iframe src="https://www.youtube.com/embed/dQw4w9WgXcQ"
        width="560" height="315"
        title="Vídeo de ejemplo insertado con iframe">
</iframe>
```

## Ejercicio 8 — Formulario de inscripción

```html
<form action="/inscripcion" method="post">
  <fieldset>
    <legend>Datos personales</legend>

    <label for="nombre">Nombre:</label>
    <input type="text" id="nombre" name="nombre"><br>

    <label for="correo">Correo:</label>
    <input type="email" id="correo" name="correo"><br>

    <label for="telefono">Teléfono:</label>
    <input type="tel" id="telefono" name="telefono"><br>

    <label for="nacimiento">Fecha de nacimiento:</label>
    <input type="date" id="nacimiento" name="nacimiento"><br>
  </fieldset>

  <fieldset>
    <legend>Turno</legend>
    <input type="radio" id="manana" name="turno" value="manana" checked>
    <label for="manana">Mañana</label>

    <input type="radio" id="tarde" name="turno" value="tarde">
    <label for="tarde">Tarde</label>
  </fieldset>

  <label for="actividad">Actividad:</label>
  <select id="actividad" name="actividad">
    <option value="robotica">Robótica</option>
    <option value="teatro">Teatro</option>
    <option value="deporte">Deporte</option>
  </select>

  <br><br>
  <label for="observaciones">Observaciones:</label><br>
  <textarea id="observaciones" name="observaciones" rows="4" cols="30"></textarea>

  <br><br>
  <input type="checkbox" id="condiciones" name="condiciones" required>
  <label for="condiciones">Acepto las condiciones</label>

  <br><br>
  <input type="submit" value="Inscribirme">
  <input type="reset" value="Borrar formulario">
</form>
```

## Ejercicio 9 — Proyecto de síntesis: mi página web personal

Solución de referencia orientativa (estructura compartida en las 3 páginas; aquí solo `index.html` completo, las otras dos siguen el mismo patrón de `header`/`nav`/`footer`):

```html
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <title>Mi afición: el ajedrez</title>
</head>
<body>
  <header>
    <h1>Todo sobre el ajedrez</h1>
    <nav>
      <ul>
        <li><a href="index.html">Inicio</a></li>
        <li><a href="sobre-mi.html">Sobre mí</a></li>
        <li><a href="contacto.html">Contacto</a></li>
      </ul>
    </nav>
  </header>

  <main>
    <p>El ajedrez es un juego de estrategia para dos personas que se practica desde hace siglos.</p>
    <img src="img/tablero.jpg" alt="Tablero de ajedrez" width="400" height="300">
    <p>Puedes aprender más en <a href="https://www.chess.com" target="_blank">chess.com</a>.</p>
  </main>

  <footer>
    <p>Página creada como práctica de HTML5 — TIC II</p>
  </footer>
</body>
</html>
```

`sobre-mi.html` reutiliza el mismo `header`/`nav`/`footer` y añade una lista de motivos + alguna etiqueta `<strong>`/`<em>` en el texto. `contacto.html` reutiliza el mismo `header`/`nav`/`footer` y añade el formulario de contacto (nombre, correo, mensaje) siguiendo el patrón del ejercicio 8.
