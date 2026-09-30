---
title: UT1 — CSS
---

# CSS — Estilos y maquetación

**CSS** (*Cascading Style Sheets*, hojas de estilo en cascada) es el lenguaje que define **cómo se ve** una página HTML: colores, tipografías, tamaños, márgenes, posición de los elementos, etc. Mientras que HTML aporta la estructura y el contenido, CSS aporta la presentación visual, permitiendo aplicar estilos a uno o varios documentos HTML de forma masiva. La versión actual es **CSS3**.

Con HTML y CSS se busca la **separación de presentación y contenido**. Ventajas de trabajar así:

- Si hay que hacer cambios visuales, se hacen en un solo lugar, sin tener que editar todos los documentos HTML.
- Se reduce la duplicación de estilos en diferentes partes del sitio.
- Es más fácil crear versiones distintas de presentación para otros dispositivos (tablets, smartphones...).

## Sintaxis de una regla CSS

Una **hoja de estilos** es un conjunto de **reglas**. Cada regla tiene esta forma:

```css
selector {
  propiedad: valor;
  propiedad: valor;
}
```

- El **selector** indica a qué elemento o elementos de la página se aplica el estilo.
- La **propiedad** es una de las características que ofrece CSS para actuar sobre el selector.
- El **valor** determina el comportamiento concreto de esa propiedad.
- Los **comentarios** se escriben entre `/*` y `*/`. El navegador los ignora.

```css
/* Párrafos en azul marino y a 16 píxeles */
p {
  color: navy;
  font-size: 16px;
}
```

## Formas de aplicar CSS

Existen tres formas de incluir CSS en un documento HTML:

1. **CSS externo**: archivo `.css` independiente, enlazado desde el `<head>` con la etiqueta `<link>`. Es la forma **recomendada**: separa por completo contenido y presentación y permite reutilizar el mismo archivo en varias páginas.
   - `rel="stylesheet"`: indica que el recurso enlazado es una hoja de estilos.
   - `href`: ruta del archivo CSS.

   ```html
   <link rel="stylesheet" href="css/estilos.css">
   ```

2. **CSS interno**: los estilos se escriben dentro del `<head>`, entre etiquetas `<style>`. Útil cuando el estilo solo afecta a una página; si hay que cambiar varias páginas, obliga a editarlas una a una.

   ```html
   <head>
     <style>
       h1 { color: orange; }
     </style>
   </head>
   ```

3. **CSS en línea** (*inline*): el estilo se escribe en la propia etiqueta con el atributo `style`. Es la forma **menos adecuada**, porque mezcla contenido y presentación y es difícil de mantener.

   ```html
   <p>¡Hola <span style="color: #ff0000;">mundo</span>!</p>
   ```

### Prioridad

Si varias formas modifican la misma propiedad del mismo elemento:

1. **El estilo en línea prevalece siempre.**
2. Entre el **interno** y el **externo** gana **el que aparezca más abajo** en el `<head>`. Lo habitual es poner primero el `<link>` y después el `<style>`, así que normalmente gana el interno:

```html
<head>
  <link rel="stylesheet" href="css/estilos.css"> <!-- h1 { color: blue; } -->
  <style>
    h1 { color: orange; } /* Gana este: está después */
  </style>
</head>
```

## Cascada y herencia

Son dos ideas distintas:

- **Cascada**: si dos reglas asignan la misma propiedad al mismo elemento, gana la que está **más abajo**… salvo que la otra sea **más específica**. De menos a más específico: etiqueta (`p`) → clase (`.aviso`) → id (`#portada`) → estilo en línea.

  ```css
  p { color: black; }
  p { color: green; }       /* Gana: está después */
  .aviso { color: red; }    /* Un <p class="aviso"> sale rojo: la clase es más específica */
  ```

- **Herencia**: algunas propiedades pasan del elemento padre a sus hijos. Se heredan las de **texto** (`color`, `font-family`, `font-size`, `text-align`...), pero **no** las de caja (`border`, `margin`, `padding`, `background-color`...).

  ```css
  body { color: green; } /* Todo el texto sale verde, salvo que se indique otra cosa */
  ```

## Selectores básicos

| Selector | Ejemplo | Se aplica a... |
|---|---|---|
| Universal | `* { color: blue; }` | Todos los elementos de la página |
| De tipo (etiqueta) | `p { color: blue; }` | Todos los `<p>` |
| De clase | `.destacado { color: red; }` | Elementos con `class="destacado"` (puede repetirse) |
| De id | `#portada { color: blue; }` | El elemento con `id="portada"` (único en la página) |
| Unión (agrupado) | `ul, ol { color: #00ff00; }` | Todos los `<ul>` **y** todos los `<ol>` |

```html
<h1 class="destacado">Título destacado</h1>
<p>Este es un párrafo normal.</p>
<p class="destacado">Este párrafo está destacado en rojo.</p>
<p id="portada">Este párrafo es único y sale en azul.</p>
```

Un elemento puede tener **varias clases a la vez**, separadas por espacios. Recibe los estilos de todas ellas:

```html
<p class="destacado grande">Rojo y con letra grande</p>
```

```css
.destacado { color: red; }
.grande { font-size: 24px; }
```

## Selectores de relación

Sirven para seleccionar elementos según **dónde están** respecto a otros.

| Selector | Ejemplo | Se aplica a... |
|---|---|---|
| Descendiente (espacio) | `p span` | Los `<span>` que están **dentro** de un `<p>`, a cualquier nivel |
| Hijo directo (`>`) | `p > span` | Los `<span>` que son **hijos directos** de un `<p>` |
| Hermano adyacente (`+`) | `h1 + h2` | El `<h2>` que va **justo después** de un `<h1>` |
| Hermanos en general (`~`) | `h1 ~ pre` | Todos los `<pre>` que van **después** de un `<h1>`, con el mismo padre |

Diferencia entre descendiente e hijo directo:

```html
<p>
  <span>texto 1</span>
  <br>
  <i><span>texto 2</span></i>
</p>
```

- Con `p span { color: blue; }` salen azules **texto 1 y texto 2**.
- Con `p > span { color: blue; }` sale azul **solo texto 1**: el segundo `<span>` es hijo de `<i>`, no de `<p>`.

Hermano adyacente:

```css
h2 { color: green; }
h1 + h2 { color: red; }
```

```html
<h1>Mi instituto</h1>
<h2>Horario</h2>    <!-- Rojo: va justo después del h1 -->
<h3>Mañana</h3>
<h2>Profesorado</h2> <!-- Verde: no va justo después de un h1 -->
```

## Combinación de selectores

Los selectores se pueden **encadenar** para afinar más:

```css
span.verde { color: green; }        /* Solo los <span> con class="verde" */
.aviso .especial { font-weight: bold; } /* class="especial" dentro de class="aviso" */
ul#menu-principal li.destacado a { color: orange; }
/* Enlaces dentro de un <li class="destacado"> de la lista <ul id="menu-principal"> */
```

> Ojo con el espacio: `span.verde` (sin espacio) es «un span que tiene la clase verde»; `span .verde` (con espacio) es «algo con clase verde **dentro** de un span».

## Selectores de atributo

Seleccionan elementos según sus atributos y los valores de esos atributos.

| Selector | Se aplica a... |
|---|---|
| `[atributo]` | Elementos que tienen ese atributo, sea cual sea su valor |
| `[atributo="valor"]` | Elementos cuyo atributo vale exactamente `valor` |
| `[atributo~="valor"]` | Elementos cuyo atributo contiene `valor` entre sus palabras separadas por espacios |

```css
a[target] { font-style: italic; }          /* Enlaces con atributo target */
a[href="index.html"] { font-weight: bold; } /* Enlace exacto a la portada */
p[class~="aviso"] { color: red; }           /* <p class="aviso grande"> también cuenta */
```

## Pseudoclases

Seleccionan elementos según el **estado** en el que se encuentran. Se escriben con dos puntos (`:`) pegados al selector.

| Pseudoclase | Se aplica cuando... |
|---|---|
| `:link` | El enlace aún no se ha visitado |
| `:visited` | El enlace ya se ha visitado |
| `:hover` | El ratón está encima del elemento |
| `:active` | Se está pulsando el elemento |
| `:lang(en)` | El elemento está en el idioma indicado (atributo `lang`) |

```html
<p>Visita <a href="#">este enlace</a> y pasa el ratón por encima.</p>
```

```css
a:link { color: blue; }
a:visited { color: purple; }
a:hover { color: red; }     /* Cambia de color al pasar el ratón */
a:active { color: orange; }
```

> Con enlaces, respeta el orden **`:link` → `:visited` → `:hover` → `:active`**. Si `:hover` va antes, `:visited` lo sobrescribe y el efecto no se ve en los enlaces visitados.

## `div` y `span`

Son contenedores **genéricos**, sin significado propio, que se usan como «ganchos» para aplicar estilos:

- `<div>` (bloque): agrupa contenido formando una caja o sección.
- `<span>` (en línea): aplica un estilo a una parte de un texto sin crear un salto de línea.

```html
<div id="carniceria">
  <p>Lista de la <span class="verde">compra</span></p>
</div>
```

> Antes de usar `<div>`, comprueba si existe una etiqueta **semántica** adecuada (`header`, `nav`, `main`, `section`, `article`, `footer`...). Usa `div` solo cuando ninguna encaje.

## Colores y fondos

- `color`: color del texto.
- `background-color`: color de fondo.
- `background-image`: imagen de fondo.

```css
body {
  color: #333333;
  background-color: #f5f5dc;
  background-image: url("../img/fondo.png");
}
```

Cualquier propiedad que admita un color se puede escribir de varias formas:

| Formato | Ejemplo (rojo) |
|---|---|
| Palabra clave predefinida | `red` |
| RGB | `rgb(255, 0, 0)` |
| RGB con canal alfa (transparencia) | `rgba(255, 0, 0, 0.25)` |
| Hexadecimal | `#ff0000` |
| Hexadecimal con canal alfa | `#ff000040` |
| HSL (tono, saturación, luminosidad) | `hsl(0, 100%, 50%)` |
| HSL con canal alfa | `hsla(0, 100%, 50%, 0.25)` |

> En HSL, una luminosidad del `100%` da siempre **blanco** y una del `0%`, **negro**. El color «puro» está en el `50%`.

## Tipografía

| Propiedad | Valores | Significado |
|---|---|---|
| `font-family` | *nombre de la fuente* | Tipografía a utilizar |
| `font-size` | *tamaño* | Tamaño de la fuente |
| `font-style` | `normal` \| `italic` \| `oblique` | Estilo (cursiva) |
| `font-weight` | `normal` \| `bold` \| `100` a `900` | Peso o grosor de la letra |

```css
h1 {
  font-family: Verdana, Arial, sans-serif;
  font-size: 32px;
  font-weight: bold;
  font-style: italic;
}
```

En `font-family` se ponen varias fuentes separadas por comas: si la primera no está instalada, se usa la siguiente. Conviene terminar siempre con una **familia genérica**:

| Familia | Significado | Ejemplos |
|---|---|---|
| `serif` | Con serifa | Times New Roman, Georgia |
| `sans-serif` | Sin serifa | Arial, Verdana, Tahoma |
| `cursive` | Manuscrita | Comic Sans MS, Brush Script MT |
| `fantasy` | Decorativa | Impact, Papyrus |
| `monospace` | Monoespaciada | Courier New, Consolas |

`font-size` admite un tamaño concreto (`18px`, `1.5rem`...) o palabras clave: `xx-small` \| `x-small` \| `small` \| `medium` \| `large` \| `x-large` \| `xx-large` (absolutas) o `smaller` \| `larger` (relativas al padre).

## Texto

| Propiedad | Valores | Significado |
|---|---|---|
| `text-align` | `left` \| `center` \| `right` \| `justify` | Alineación del texto |
| `text-decoration` | `none` \| `underline` \| `line-through` | Subrayado, tachado... (`none` quita el subrayado de los enlaces) |
| `text-indent` | *tamaño* | Sangría de la primera línea |

```css
p {
  text-align: justify;
  text-indent: 2em;
}

a {
  text-decoration: none;
}
```

## Unidades de medida

**Absolutas**: medida fija, que no depende de nada más.

| Unidad | Significado | Medida aproximada |
|---|---|---|
| `px` | Píxeles | 1px ≈ 0.26mm |
| `pt` | Puntos | 1pt ≈ 0.35mm |
| `mm` | Milímetros | 1mm |
| `cm` | Centímetros | 1cm = 10mm |
| `in` | Pulgadas | 1in = 25.4mm |
| `pc` | Picas | 1pc ≈ 4.23mm |

**Relativas**: dependen de otro valor (la fuente, el padre, la ventana...). Son las preferibles para diseños adaptables (*responsive*).

| Unidad | Relativa a... |
|---|---|
| `%` | El valor de esa misma propiedad en el elemento padre |
| `em` | El tamaño de fuente del elemento (en `font-size`, el del padre) |
| `rem` | El tamaño de fuente del elemento raíz (`<html>`) |
| `ex` | La altura de la letra «x» de la fuente (≈ 0.5em) |
| `ch` | El ancho del carácter «0» de la fuente |
| `vw` / `vh` | El 1 % del ancho / alto de la ventana del navegador |

```css
html { font-size: 16px; }
h1 { font-size: 2rem; }  /* 32px */
main { width: 80%; }     /* 80 % del ancho del padre */
```

## El modelo de caja (*box model*)

Todo elemento HTML se representa como una caja rectangular formada, de dentro hacia fuera, por:

1. **content**: el contenido en sí (texto, imagen...).
2. **padding** (relleno): espacio interior entre el contenido y el borde.
3. **border** (borde): el borde de la caja.
4. **margin** (margen): espacio exterior entre la caja y los elementos vecinos.

![Esquema del modelo de caja: cuatro rectángulos concéntricos. De fuera hacia dentro: margin (naranja, espacio exterior transparente), border (gris oscuro, la línea que rodea la caja), padding (verde, espacio interior que sí toma el color de fondo) y content (azul, el contenido, de tamaño width × height).](../img/css-modelo-caja.svg)

```css
div {
  width: 300px;
  padding: 10px;
  border: 2px solid black;
  margin: 20px auto; /* 20px arriba y abajo; auto a los lados centra la caja */
}
```

- **Márgenes**: `margin-top`, `margin-right`, `margin-bottom`, `margin-left`. Valor: un tamaño o `auto`.
- **Relleno**: `padding-top`, `padding-right`, `padding-bottom`, `padding-left`. Valor: un tamaño (por defecto `0`).
- **Bordes**: `border-color`, `border-width` (`thin` \| `medium` \| `thick` o un tamaño) y `border-style` (`none`, `solid`, `dashed`, `dotted`...). También por lados: `border-top`, `border-right`...

```css
.tarjeta {
  border-bottom: 3px dashed orange; /* grosor, estilo y color en una sola línea */
}
```

### Ejemplo guiado: la tarjeta del club

Vamos a construir una tarjeta para anunciar el club de baloncesto del instituto y a identificar en ella cada capa del modelo de caja. La tarjeta va dentro de un contenedor con borde discontinuo gris, para que se vea dónde empieza el margen.

```html
<div class="contenedor">
  <article class="tarjeta">
    <h2>Club de baloncesto</h2>
    <p>Entrenamos martes y jueves a las 17:00 en el pabellón del instituto. ¡Te esperamos!</p>
  </article>
</div>
```

```css
.contenedor {
  border: 2px dashed gray;    /* Solo sirve para ver dónde acaba el margen */
}

.tarjeta {
  width: 260px;               /* content: ancho del contenido */
  padding: 20px;              /* padding: 20px por los 4 lados */
  border: 4px solid #1e88e5;  /* border: 4px, línea continua, azul */
  margin: 30px;               /* margin: 30px por los 4 lados */
  background-color: #e3f2fd;  /* El fondo llena content y padding, no el margin */
}
```

<div class="resultado" markdown="0">
<div style="border: 2px dashed gray;">
  <article style="width: 260px; padding: 20px; border: 4px solid #1e88e5; margin: 30px; background-color: #e3f2fd; color: #0d2a45;">
    <h2 style="margin: 0 0 8px 0; font-size: 1.3em;">Club de baloncesto</h2>
    <p style="margin: 0;">Entrenamos martes y jueves a las 17:00 en el pabellón del instituto. ¡Te esperamos!</p>
  </article>
</div>
</div>

Fíjate en el resultado:

- **content**: el texto ocupa una franja de 260px de ancho.
- **padding**: los 20px de separación entre el texto y la línea azul. Tienen el mismo fondo azul claro que el contenido.
- **border**: la línea azul de 4px.
- **margin**: el hueco de 30px entre la línea azul y la línea discontinua gris. **No** tiene color de fondo.

¿Cuánto ocupa la tarjeta en horizontal?

| Parte | Cálculo | Píxeles |
|---|---|---|
| content | `width` | 260 |
| padding | 20 + 20 | 40 |
| border | 4 + 4 | 8 |
| **Caja visible** (hasta el borde) | 260 + 40 + 8 | **308** |
| margin | 30 + 30 | 60 |
| **Espacio total ocupado** | 308 + 60 | **368** |

> **Compruébalo tú:** abre la página con Live Server, pulsa **F12**, selecciona la tarjeta con el inspector y busca la pestaña **Calculado** (*Computed*). El navegador dibuja este mismo esquema de cajas con los valores reales. Prueba a cambiar `padding` o `margin` y observa qué capa crece.

## Posicionamiento

La propiedad `position` controla cómo se sitúa un elemento en la página:

- `static`: posición normal, en el orden en que aparece en el HTML (valor por defecto).
- `relative`: se desplaza respecto a su posición normal con `top`, `right`, `bottom`, `left`, pero sigue ocupando su hueco original.
- `absolute`: se coloca con `top`, `right`, `bottom`, `left` respecto a su primer antecesor posicionado (con `position` distinto de `static`) o, si no hay ninguno, respecto a la página. Sale del flujo normal.
- `fixed`: se coloca respecto a la ventana del navegador y permanece fijo aunque se haga scroll.

```css
.caja {
  position: absolute;
  top: 50px;
  left: 100px;
}
```

## Errores frecuentes

- **Olvidar el `;` o la `}`**: la propiedad siguiente (o todo el resto del archivo) deja de funcionar.
- **Poner el punto o la almohadilla en el HTML**: se escribe `class="rojo"` e `id="portada"`, no `class=".rojo"`. El `.` y el `#` van solo en el CSS.
- **Repetir un mismo `id`** en varios elementos. Si el estilo se va a repetir, usa una clase.
- **Ruta del `<link>` mal escrita**: si la hoja está en `css/estilos.css`, el `href` debe coincidir exactamente (mayúsculas incluidas).
- **Olvidar la unidad**: `font-size: 16` no funciona; hay que escribir `16px`. Solo el `0` puede ir sin unidad.
- **Pensar que `width` es el ancho total de la caja**: solo es el del contenido. El `padding` y el `border` se suman a ese ancho, así que la caja se ve más grande de lo esperado.
- **Confundir `span.verde` con `span .verde`**: el espacio cambia el significado del selector.
- **Esperar que una propiedad «no haga caso»**: probablemente otra regla más específica o escrita más abajo la está sobrescribiendo. Revísalo con el inspector del navegador (F12).
- **Desordenar las pseudoclases de los enlaces**: el orden correcto es `:link`, `:visited`, `:hover`, `:active`.
- **Abusar del atributo `style`** en lugar de usar una hoja externa.

> ¿Listo para practicar? Ve a las [Prácticas de CSS](practicas-css.md).

---

[⬅ Volver a UT1](index.md) · [Ir a Instalación de VS Code](instalacion-vscode.md) · [Ir a HTML5](html.md) · [Ir a Prácticas de HTML5](practicas-html.md) · [Ir a Subir tus ejercicios a GitHub](github.md) · [Ir a Prácticas de CSS](practicas-css.md) · [Ir a JavaScript](javascript.md) · [Ir a Publicación web avanzada](publicacion-web.md)