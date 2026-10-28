# Proyecto final UT1 — Material del profesor

Material interno para `recursos/ut1-html-css-js/`. El enunciado público está en `docs/ut1-html-css-js/proyecto.md` y los apuntes de Copilot en `docs/ut1-html-css-js/copilot.md`.

## Encaje en la programación

| Criterio | Peso | Instrumento y agente en la PD | Cómo lo cubre este proyecto |
|---|---|---|---|
| **1.1** Generar sitios web… HTML, CSS y JavaScript, depurando errores, integrando widgets externos, optimizando la experiencia de usuario… | 2 | Proyecto · Heteroevaluación | Partes A, B y C (80 %), evaluadas por el profesor; parte D (20 %), coevaluación. |
| **1.4** Insertar geolocalizaciones en webs HTML… | 2 | Proyecto · Autoevaluación | Solo como ampliación opcional («¿Dónde estoy?»). |

**Dos puntos que decidir:**

1. **Coevaluación (20 %).** La PD asigna al 1.1 la heteroevaluación, y con un 20 % la coevaluación ya pesa tanto como tu nota de la presentación. Conviene recoger en la PD (o en acta de departamento) que el criterio 1.1 combina heteroevaluación y coevaluación. La regla de la PD actúa de salvaguarda: si la media de los compañeros se aleja 2 puntos o más de tu nota de la presentación, esa parte pasa a ser heteroevaluada.
2. **Criterio 1.4.** Si quieres que este proyecto sea también el instrumento del 1.4, convierte la ampliación 1 en requisito y añade una autoevaluación breve en Forms (¿funciona?, ¿pide permiso?, ¿qué pasa si se deniega?).

## Calendario y efecto en la temporalización

| Fecha | Sesión | Contenido |
|---|---|---|
| Jue 29/10 | — | Última sesión de JavaScript (Ej. 10 — Me gusta). |
| Mar 3/11 | margen | Terminar ejercicios de JS. Últimos 15 min: presentar el proyecto. |
| Mié 4 – vie 6/11 | — | Widgets, FTP y geolocalización (`publicacion-web.md`). |
| Mar 10/11 | 1 | Copilot (actividad guiada, 25 min) + plan del sitio y esqueleto HTML. |
| Mié 11/11 | 2 | Desarrollo: HTML y CSS. |
| Jue 12/11 | 3 | Desarrollo: CSS y JavaScript. |
| Vie 13/11 | 4 | Desarrollo: JS y README. Sorteo del orden de presentación. |
| Lun 16/11, 23:59 | — | Entrega. |
| Mar 17/11 | 5 | Presentaciones (3 alumnos) + coevaluación. |
| Mié 18/11 | 6 | Presentaciones (2 alumnos) + coevaluación + devolución en grupo. |

**Efecto:** la temporalización revisada daba 3 sesiones al proyecto (10-12/11) y empezaba la UT2 el 13/11. Con 6 sesiones, la UT2 empieza el **jueves 19/11**: son 3 sesiones más. Propuesta para compensarlas:

- Usar las **2 sesiones de margen** del 10-11/12.
- Quitar **1 sesión a la UT2** (de 8 a 7), como ya preveía la nota de la temporalización.

Con eso: UT2 del 19/11 al 1/12 (7 sesiones) y UT3 del 2/12 al 11/12 (6 sesiones, con el 8/12 festivo). No queda margen antes de la 1.ª evaluación.

## Guion para presentar el proyecto (mar 3/11, 15 min)

1. **Qué y por qué** (2 min): un sitio de 3 páginas sobre un tema libre, para demostrar lo aprendido. 80 % de la nota de la UT1.
2. **Requisitos** (5 min): recorrer los pasos 3, 4 y 5 del enunciado. Insistir en las funcionalidades A, B y C.
3. **Evaluación** (4 min): tabla de pesos y las rúbricas A y C. Explicar que en la presentación pueden pedirles un cambio en directo.
4. **Copilot** (2 min): se explicará el 10/11; adelantar la regla de oro: «si no lo sabes explicar, no es tuyo».
5. **Tarea para casa** (2 min): elegir tema y escribirlo en Teams antes del 10/11.

## Hoja de calificación (una por alumno)

Nota de cada indicador de 0 a 10, según el nivel de la rúbrica. Nota ponderada = nota × peso.

| Parte | Indicador | Peso en el proyecto | Nota (0-10) | Ponderada |
|---|---|---|---|---|
| A | Estructura y semántica HTML | 7,5 % | | |
| A | Elementos obligatorios HTML | 7,5 % | | |
| A | CSS: hoja externa y selectores | 7,5 % | | |
| A | CSS: modelo de caja, unidades y `position` | 5 % | | |
| A | Diseño y experiencia de usuario | 5 % | | |
| A | JavaScript: funcionalidades | 12,5 % | | |
| A | JavaScript: calidad y depuración | 2,5 % | | |
| A | Organización y entrega | 2,5 % | | |
| B | Descripción y páginas | 4 % | | |
| B | Funcionalidades JavaScript | 3 % | | |
| B | Recursos, licencias y uso de IA | 2 % | | |
| B | Formato Markdown | 1 % | | |
| C | Presentación del sitio y demostración | 6 % | | |
| C | Explicación del código | 8 % | | |
| C | Respuesta a preguntas | 4 % | | |
| C | Comunicación y tiempo | 2 % | | |
| D | Coevaluación (media de Forms) | 20 % | | |
| | **Nota del proyecto** | **100 %** | | **Σ** |

Los pesos de esta tabla son el peso del indicador dentro de su parte multiplicado por el peso de la parte (por ejemplo, 15 % × 50 % = 7,5 %). La nota del proyecto entra con un 80 % en la UT1.

**Regla de la PD para D:** si |media de coevaluación − nota del profesor en C| ≥ 2, en la fila D se pone la nota del profesor en C.

## Lista de comprobación para corregir

1. Clonar o descargar el repositorio y abrir `proyecto/index.html` con Live Server.
2. Recorrer el menú en todas las páginas: ¿hay enlaces rotos?, ¿el menú es igual?
3. Abrir la consola (F12) en **cada** página: debe estar limpia.
4. Probar las funcionalidades con casos límite:
   - formulario vacío, solo espacios y números fuera de rango;
   - letras en un campo numérico, si lo hay;
   - el contador o botón pulsado muchas veces.
5. Validar cada página en [validator.w3.org](https://validator.w3.org/#validate_by_upload) (subiendo el archivo).
6. Buscar `style="` en el proyecto (Ctrl+Shift+F en VS Code). El enunciado pide pasar a la hoja el `style` del `<iframe>`; si se ha quedado ahí, es un detalle menor.
7. Buscar elementos no vistos que delaten código copiado: `addEventListener`, `querySelector`, `=>`, `` ` `` (plantillas), `display: flex`, `grid`, `@media`.
8. Revisar el historial de *commits* en GitHub: varios *commits* repartidos por las sesiones, frente a uno solo enorme el último día.
9. Comprobar `.github/copilot-instructions.md` y el apartado de IA del README.

Si el punto 7 o el 8 levantan sospechas, no penalizar directamente: preguntar por ese código en la presentación.

## Preguntas para la presentación

Para comprobar la autoría sin agobiar. Elegir una o dos según el proyecto:

- «¿Qué pasa si quito esta línea?» (señalando un `i++`, un `+=` o un `Number()`).
- «Añade un elemento más al array y enséñame que aparece en la página.»
- «Cambia el color de los enlaces del menú al pasar el ratón.»
- «¿Por qué el botón del formulario es `type="button"`?»
- «Si escribo solo espacios en el nombre, ¿qué pasa? ¿Cómo lo arreglarías?»
- «¿Dónde se ve el modelo de caja en esta tarjeta? Enséñamelo con F12.»
- «¿Qué le pediste a Copilot y qué cambiaste de lo que te dio?»

## Coevaluación con Microsoft Forms

**Configuración:**

- Un único formulario para las dos sesiones, compartido en Teams.
- En *Configuración*: solo personas de la organización y **registrar el nombre** (hace falta para aplicar la regla de la PD y evitar que alguien se evalúe a sí mismo). Los resultados no se comparten con el alumnado.
- Cada alumno lo envía una vez por compañero, justo después de cada presentación (4 envíos por alumno).
- Con 5 alumnos el anonimato es limitado: avisar de que el profesor ve las respuestas, pero los compañeros no.

**Preguntas:**

1. ¿A quién evalúas? *(desplegable con los 5 nombres; obligatoria)*
2. Se entiende de qué trata la web. *(Insuficiente / Suficiente / Notable / Sobresaliente)*
3. La web funciona y se ve bien. *(ídem)*
4. Explica cómo ha hecho su código. *(ídem)*
5. Comunicación y tiempo. *(ídem)*
6. ¿Qué es lo que más te ha gustado? *(texto corto; obligatoria)*
7. ¿Qué le recomendarías mejorar? *(texto corto; obligatoria)*

En las preguntas 2 a 5, copiar en la descripción el texto de los cuatro niveles de la rúbrica D para que lo tengan delante.

**Cálculo:** exportar a Excel, convertir (Insuficiente 3; Suficiente 5,5; Notable 7,5; Sobresaliente 9,5), descartar las autoevaluaciones si las hay y hacer la media por alumno evaluado. Las preguntas 6 y 7 sirven para la devolución del 18/11.

---

## Solución de referencia comentada

No hay una solución única: el tema es libre. Este ejemplo muestra **qué cuenta como cumplido** en las funcionalidades A, B y C y en la ampliación de geolocalización, con un tema de ejemplo («Rutas por mi comarca»). Sirve también para enseñarlo en clase si alguien se atasca.

### A. Botón que cambia la página — `index.html` + `js/inicio.js`

```html
<section>
  <h2>¿Te apuntas a la próxima ruta?</h2>
  <p>Ya somos <span id="apuntados">0</span> personas.</p>
  <button type="button" onclick="apuntarme()">Me apunto</button>
  <p id="aviso"></p>
</section>

<script src="js/inicio.js"></script>
```

```js
// Número de personas apuntadas. Va fuera de la función para que
// conserve su valor entre clic y clic.
let apuntados = 0;
const MAXIMO = 10;

// Suma una persona si queda sitio y actualiza la página
function apuntarme() {
  if (apuntados < MAXIMO) {
    apuntados++;
    document.getElementById("apuntados").innerHTML = apuntados;
  }

  // Cuando se llena el grupo, se avisa en la página (no con alert)
  if (apuntados === MAXIMO) {
    document.getElementById("aviso").innerHTML = "¡Grupo completo!";
  }
}
```

**Qué mirar:** variable global, función llamada con `onclick`, condicional y resultado en la página. El límite máximo es lo que lo lleva a Sobresaliente (caso límite controlado).

### B. Array recorrido con `for` — `rutas.html` + `js/rutas.js`

```html
<table>
  <caption>Próximas rutas</caption>
  <thead>
    <tr>
      <th>Ruta</th>
      <th>Distancia (km)</th>
    </tr>
  </thead>
  <tbody id="cuerpo-tabla"></tbody>
</table>
<p id="total-km"></p>

<script src="js/rutas.js"></script>
```

```js
// Dos arrays paralelos: la posición i de uno corresponde a la del otro
const rutas = ["Las Arribes", "Peña de Francia", "Sierra de Béjar"];
const distancias = [12, 9, 15];

let filas = "";    // Aquí se va construyendo el HTML de las filas
let totalKm = 0;   // Acumulador de kilómetros

// Una vuelta por ruta: de 0 hasta length - 1
for (let i = 0; i < rutas.length; i++) {
  filas += "<tr><td>" + rutas[i] + "</td><td>" + distancias[i] + "</td></tr>";
  totalKm += distancias[i];
}

// Se escribe una sola vez, al terminar el bucle
document.getElementById("cuerpo-tabla").innerHTML = filas;
document.getElementById("total-km").innerHTML = "En total: " + totalKm + " km.";
```

**Qué mirar:** el bucle usa `length` (añadir una ruta no obliga a tocar el `for`) y el contenido sale en la página. Este archivo solo se enlaza en `rutas.html`: si se enlazara en otra página, daría `Cannot set properties of null`.

### C. Validación del formulario — `contacto.html` + `js/contacto.js`

```html
<form action="#" method="post">
  <fieldset>
    <legend>Apúntate a una ruta</legend>
    <p>
      <label for="nombre">Nombre:</label>
      <input type="text" id="nombre" name="nombre">
    </p>
    <p>
      <label for="ruta">Ruta:</label>
      <select id="ruta" name="ruta">
        <option value="">Elige una ruta</option>
        <option value="Las Arribes">Las Arribes</option>
        <option value="Peña de Francia">Peña de Francia</option>
      </select>
    </p>
    <p>
      <label for="personas">Número de personas:</label>
      <input type="number" id="personas" name="personas">
    </p>
    <button type="button" onclick="validar()">Enviar</button>
  </fieldset>
</form>
<p id="mensaje"></p>

<script src="js/contacto.js"></script>
```

```js
// Comprueba los datos del formulario y responde en la página
function validar() {
  let nombre = document.getElementById("nombre").value;
  let ruta = document.getElementById("ruta").value;
  // .value siempre es texto: se convierte para poder comparar
  let personas = Number(document.getElementById("personas").value);

  if (nombre === "" || ruta === "") {
    document.getElementById("mensaje").innerHTML = "Escribe tu nombre y elige una ruta.";
  } else if (!(personas >= 1 && personas <= 5)) {
    // Se escribe así, y no como "personas < 1 || personas > 5",
    // porque si el campo tiene algo que no es un número, Number() da NaN
    // y cualquier comparación con NaN es false: esta forma también lo rechaza.
    document.getElementById("mensaje").innerHTML = "Podéis apuntaros de 1 a 5 personas.";
  } else {
    document.getElementById("mensaje").innerHTML = "Gracias, " + nombre + ". Te esperamos en " + ruta + ".";
  }
}
```

**Qué mirar:** `type="button"`, lectura con `.value`, conversión con `Number()`, `else if` y operadores lógicos. Un campo numérico vacío da `Number("") = 0`, que también se rechaza. Controlar el caso `NaN` es de Sobresaliente; no exigirlo para Notable.

### Ampliación: «¿Dónde estoy?» (criterio 1.4)

```html
<button type="button" onclick="dondeEstoy()">¿Dónde estoy?</button>
<p id="posicion"></p>
```

```js
// Pide la ubicación al navegador (siempre pregunta antes al usuario)
function dondeEstoy() {
  if (navigator.geolocation) {
    navigator.geolocation.getCurrentPosition(mostrarPosicion, mostrarError);
  } else {
    document.getElementById("posicion").innerHTML = "Tu navegador no permite la geolocalización.";
  }
}

// Se ejecuta si se obtiene la ubicación
function mostrarPosicion(posicion) {
  let lat = posicion.coords.latitude;
  let lon = posicion.coords.longitude;
  document.getElementById("posicion").innerHTML = "Latitud: " + lat + " · Longitud: " + lon;
}

// Se ejecuta si falla, por ejemplo si el usuario no da permiso
function mostrarError(error) {
  document.getElementById("posicion").innerHTML = "No se pudo obtener la ubicación: " + error.message;
}
```

**Qué mirar:** funciona con Live Server porque es `localhost`; abriendo el archivo directamente puede fallar. Debe tratar el caso de permiso denegado.