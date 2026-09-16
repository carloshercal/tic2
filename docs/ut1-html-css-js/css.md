---
title: UT1 — CSS
---

# CSS — Estilos y maquetación

**CSS** (*Cascading Style Sheets*, hojas de estilo en cascada) es el lenguaje que define **cómo se ve** una página HTML: colores, tipografías, tamaños, márgenes, posición de los elementos, etc. Mientras que HTML aporta la estructura y el contenido, CSS aporta la presentación visual, permitiendo aplicar estilos a uno o varios documentos HTML de forma masiva.

Con HTML y CSS se busca la **separación de presentación y contenido**. Ventajas de trabajar así:

- Si hay que hacer cambios visuales, se hacen en un solo lugar, sin tener que editar todos los documentos HTML.
- Se reduce la duplicación de estilos en diferentes partes del sitio.
- Es más fácil crear versiones distintas de presentación para otros dispositivos (tablets, smartphones...).

## Sintaxis de una regla CSS

```css
selector {
  propiedad: valor;
  propiedad: valor;
}
```

- El **selector** indica a qué elemento o elementos de la página se aplica el estilo.
- La **propiedad** es una de las características que ofrece CSS para actuar sobre el selector.
- El **valor** determina el comportamiento concreto de esa propiedad.

```css
p {
  color: navy;
  font-size: 16px;
}
```

## Formas de aplicar CSS

Existen tres formas de incluir contenido CSS en un documento HTML, que se aplican por orden de prioridad (de menor a mayor):

1. **CSS externo**: archivo `.css` independiente que contiene los estilos, enlazado desde la cabecera del HTML con la etiqueta `<link>`. Es la forma recomendada, porque separa contenido y presentación y permite reutilizar el mismo archivo en varias páginas.

   ```html
   <link rel="stylesheet" type="text/css" href="index.css" />
   ```

2. **CSS interno**: los estilos se añaden directamente en la cabecera del HTML, entre las etiquetas `<style>`.

   ```html
   <head>
     <style type="text/css">
       div { background: #04eb41; }
     </style>
   </head>
   ```

3. **CSS embebido** (*inline*): se aplican estilos directamente en las propias etiquetas, mediante el atributo `style`. Es la opción de mayor prioridad, pero **no es recomendable** por su difícil mantenimiento (mezcla contenido y presentación).

   ```html
   <p>¡Hola <span style="color:#FF0000">mundo</span>!</p>
   ```

## Herencia CSS

Las propiedades CSS se aplican desde arriba hacia abajo, sobrescribiendo las propiedades anteriores que se repitan. Además, algunas propiedades CSS se **heredan** desde los elementos padres a los elementos hijos, modificando el valor que tienen por defecto. Por ejemplo, la propiedad `color` hereda de los padres a los hijos:

```css
body { color: green; /* Todo el texto del body será verde, salvo que se indique lo contrario */ }
```

## Selectores

- **Selector de elementos**: la forma más básica; se indica el elemento al que queremos aplicarle los estilos. Ej.: `strong { color: red; }`
- **Selector por ID (único)**: todos los elementos HTML pueden tener un atributo `id` con un valor concreto, que debe ser único en todo el documento. Se define con almohadilla. Ej.: `#saludo { background-color: blue; }` → `<div id="saludo">`
- **Selector por clases**: el atributo `class`, a diferencia de `id`, puede repetirse en más de un elemento del documento; es muy útil para aplicar el mismo estilo a elementos distintos. Se define con un punto. Ej.: `.estandar { background-color: green; }` → `<p class="estandar">`
- **Selector universal**: `* { ... }` aplica a todos los elementos de la página.
- **Selector descendiente**: `div p { ... }` aplica a los `<p>` que están dentro de un `<div>`.
- **Selector agrupado**: `h1, h2, h3 { ... }` aplica el mismo estilo a varios selectores a la vez.

## `div` y `span`

CSS suele apoyarse en los contenedores genéricos de HTML para estructurar y estilizar la página:

- `<div>` (bloque): agrupa secciones completas — cabeceras, menús, columnas...
- `<span>` (en línea): aplica un estilo a una parte concreta de un texto sin crear un salto de línea.

## Colores

La propiedad `color` cambia el color del texto de un elemento, y `background-color` el color de fondo. Todas las propiedades CSS que admiten un color se pueden indicar de varias formas:

| Formato | Ejemplo |
|---|---|
| Palabra clave predefinida | `red` |
| Esquema RGB | `rgb(255, 0, 0)` |
| Esquema RGB con canal alfa (transparencia) | `rgba(255, 0, 0, 0.25)` |
| Esquema RGB hexadecimal | `#ff0000` |
| Esquema RGB hexadecimal con canal alfa | `#ff000040` |
| Esquema HSL (tono, saturación, brillo) | `hsl(0, 100%, 100%)` |
| Esquema HSL con canal alfa | `hsla(0, 100%, 100%, 0.25)` |

## Tipografía

Las propiedades básicas para trabajar con cualquier tipografía son:

| Propiedad | Valor | Significado |
|---|---|---|
| `font-family` | *nombre de la fuente* | Indica el nombre de la tipografía a utilizar |
| `font-size` | *tamaño* | Indica el tamaño de la fuente |
| `font-style` | `normal` \| `italic` \| `oblique` | Indica el estilo de la fuente |
| `font-weight` | *peso* | Indica el peso (grosor) de la fuente |

`font-family` admite además palabras clave de familias tipográficas seguras, por si la fuente indicada no está disponible en el dispositivo:

| Familia | Significado | Ejemplos |
|---|---|---|
| `serif` | Tipografía con serifa | Times New Roman, Georgia |
| `sans-serif` | Tipografía sin serifa | Arial, Verdana, Tahoma |
| `cursive` | Tipografía en cursiva | Sanvito, Corsiva |
| `fantasy` | Tipografía decorativa | Critter, Cottonwood |
| `monospace` | Tipografía monoespaciada | Courier, Courier New |

`font-size` puede indicarse con un tamaño específico (por ejemplo `18px`), o con palabras clave: `xx-small` \| `x-small` \| `small` \| `medium` \| `large` \| `x-large` \| `xx-large` (tamaño absoluto predefinido) o `smaller` \| `larger` (tamaño relativo al elemento padre).

## Alineación y variaciones de texto

| Propiedad | Valor | Significado |
|---|---|---|
| `text-align` | `left` \| `center` \| `right` \| `justify` | Justificación del texto |
| `text-justify` | `auto` \| `inter-word` \| `inter-character` \| `none` | Método de justificación del texto |
| `text-overflow` | `clip` \| `ellipsis` \| *texto* | Comportamiento cuando el texto no cabe (p. ej. con puntos suspensivos «...») |
| `text-decoration` | `none` \| `underline` \| `line-through` | Decoración del texto (subrayado, tachado...) |

## Unidades de medida

**Unidades absolutas**: son un tipo de medida fija que no cambia, y no depende de ningún otro factor.

| Unidad | Significado | Medida aproximada |
|---|---|---|
| `in` | Pulgadas | 1in = 25.4mm |
| `cm` | Centímetros | 1cm = 10mm |
| `pc` | Picas | 1pc = 4.23mm |
| `mm` | Milímetros | 1mm = 1mm |
| `pt` | Puntos | 1pt = 0.35mm |
| `px` | Píxeles | 1px = 0.26mm |

**Unidades relativas**: son un tipo de medida más flexible, que depende de algún otro factor (resolución, densidad de pantalla, tamaño del elemento padre...). Son las preferibles para diseños adaptables (*responsive*).

| Unidad | Significado | Medida aproximada |
|---|---|---|
| `em` | «M» | 1em = tamaño de la fuente del elemento padre |
| `ex` | «X» | 1ex ≈ mitad del tamaño de la fuente |
| `ch` | «zero width» | 1ch = ancho del carácter «0» |
| `rem` | «root M» | 1rem = tamaño de la fuente raíz del documento |
| `%` | Porcentaje | Relativo al elemento contenedor (herencia) |
| `vw` / `vh` | *viewport width/height* | Porcentaje del ancho/alto de la ventana del navegador |

## El modelo de caja (*box model*)

Todo elemento HTML se representa como una caja rectangular formada, de dentro hacia fuera, por:

1. **content**: el contenido en sí (texto, imagen...).
2. **padding** (espaciado): espacio interior entre el contenido y el borde.
3. **border** (borde): el borde de la caja.
4. **margin** (margen): espacio exterior entre la caja y los elementos vecinos.

```css
div {
  width: 300px;
  padding: 10px;
  border: 2px solid black;
  margin: 20px;
}
```

- **Márgenes** (`margin`): espacio entre el borde del elemento y los elementos externos (`margin-top`, `margin-right`, `margin-bottom`, `margin-left`; valor `auto` o un tamaño).
- **Espaciados** (`padding`): espacio entre el borde del elemento y su propio contenido (`padding-top`, `padding-right`, `padding-bottom`, `padding-left`; por defecto `0`, o un tamaño).
- **Bordes** (`border`): `border-color` (color del borde), `border-width` (`thin` \| `medium` \| `thick`, o un tamaño concreto) y `border-style` (`none` u otro estilo de borde, como `solid`, `dashed`, `dotted`).

## Posicionamiento

La propiedad `position` controla cómo se sitúa un elemento en la página:

- `static`: posición normal, la que le corresponde en el flujo del documento (valor por defecto).
- `relative`: se desplaza respecto a su posición normal, usando `top`, `right`, `bottom`, `left`, pero sigue ocupando su espacio original.
- `absolute`: se posiciona respecto a su antecesor posicionado más cercano (o respecto a la página si no hay ninguno), y se saca del flujo normal.
- `fixed`: se posiciona respecto a la ventana del navegador y permanece fijo aunque se haga scroll.

```css
.caja {
  position: absolute;
  top: 50px;
  left: 100px;
}
```

---

[⬅ Volver a UT1](index.md) · [Ir a HTML5](html.md) · [Ir a Prácticas de HTML5](practicas-html.md) · [Ir a JavaScript](javascript.md) · [Ir a Publicación web avanzada](publicacion-web.md)