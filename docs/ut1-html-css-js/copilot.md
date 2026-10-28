---
title: UT1 — GitHub Copilot en VS Code
---

# GitHub Copilot en Visual Studio Code

**GitHub Copilot** es un asistente de programación con inteligencia artificial integrado en Visual Studio Code. Te propone código mientras escribes, te explica código o errores y responde a tus preguntas en un chat.

Úsalo como a un compañero que sabe mucho pero **a veces se equivoca con total seguridad**. La responsabilidad del código es tuya: si no lo entiendes, no lo uses.

## Qué plan usar

- **Copilot Free:** gratis con tu cuenta de GitHub. Incluye un número limitado de sugerencias de código (2.000 al mes) y de consultas en el chat. Es suficiente para el proyecto si lo usas con cabeza.
- **Copilot Student:** gratis para estudiantes verificados en GitHub Education, con más uso. La verificación puede tardar días y no hace falta para este proyecto.

Lo que escribes en el chat se envía a los servidores de GitHub: **no pegues datos personales**. Puedes revisar las opciones de privacidad en la configuración de Copilot de tu cuenta de GitHub.

## Activarlo en VS Code

1. Abre VS Code y la vista de chat con **Ctrl+Alt+I** (en Mac, **Ctrl+Cmd+I**), o con el icono de Copilot de la parte superior.
2. Inicia sesión con **la misma cuenta de GitHub** con la que entregas los ejercicios.
3. Si VS Code te lo pide, instala o activa la extensión **GitHub Copilot** y elige el plan **Free**.
4. Compruébalo: abre un `.html`, empieza a escribir y verás texto en gris. Eso es una sugerencia.

## Las tres formas de usarlo

### 1. Sugerencias mientras escribes

Copilot adivina lo que vas a escribir y te lo propone en gris (*ghost text*).

| Tecla | Qué hace |
|---|---|
| **Tab** | Acepta la sugerencia entera |
| **Esc** | La descarta |
| **Ctrl+→** (Mac: **Cmd+→**) | Acepta solo la siguiente palabra |

Un comentario claro ayuda a que la sugerencia sea buena:

```html
<!-- Lista no ordenada con tres lugares para visitar en mi localidad -->
```

> Acepta **palabra a palabra** en lugar de pulsar Tab a ciegas: así lees lo que entra en tu código.

### 2. El chat

En la vista de chat escribes preguntas en lenguaje natural. Abajo hay un selector de **modo**:

- **Ask** (preguntar): responde y te propone código, pero **no toca tus archivos**. Es el que usaremos.
- **Agent** (agente): crea y modifica archivos por su cuenta. **No lo uses en el proyecto**: no aprenderías y no podrías explicar el código.

Copilot responde mejor si sabe de qué código hablas. Abre el archivo o **selecciona** las líneas antes de preguntar. También puedes escribir `#` para añadir un archivo concreto a la pregunta.

Atajos útiles en el chat:

- `/explain`: explica el código seleccionado.
- `/fix`: propone cómo arreglar un error del código seleccionado.

```
/explain Explícame línea a línea esta función. Estoy empezando con JavaScript.
```

### 3. El chat en línea

Selecciona unas líneas y pulsa **Ctrl+I** (Mac: **Cmd+I**). Se abre una pequeña caja de chat sobre el propio código, útil para peticiones rápidas:

```
Añade comentarios en español que expliquen cada línea
```

Copilot te enseña el cambio y tú decides si lo **aceptas** o lo **descartas**.

## Cómo pedirle bien las cosas

Una buena petición (*prompt*) tiene cuatro partes:

1. **Contexto:** quién eres y qué sabes.
2. **Qué quieres:** concreto, una cosa cada vez.
3. **Límites:** qué puede usar y qué no.
4. **Formato:** explicación, pista o código.

| Petición pobre | Petición buena |
|---|---|
| hazme una web de baloncesto | Estoy en 2º de Bachillerato y hago una web sobre el club de baloncesto del instituto. Propón 3 páginas y qué contenido llevaría cada una. No escribas código. |
| no funciona | Al pulsar el botón «Enviar», la consola dice `Cannot set properties of null`. Te he seleccionado la función. Dime qué puede fallar, pero déjame corregirlo a mí. |
| haz un contador | Quiero un botón que sume 1 a un contador y lo muestre en un `span`. Usa solo `onclick`, `getElementById` e `innerHTML`. Explícamelo antes de darme el código. |

## Las instrucciones del repositorio

Puedes darle a Copilot unas instrucciones fijas que leerá en cada consulta del chat. Se escriben en el archivo `.github/copilot-instructions.md`, en la **raíz** de tu repositorio:

```
ut1-html-css-js-usuario/
├── .github/
│   └── copilot-instructions.md
├── ejercicios-html/
├── …
└── proyecto/
```

Contenido:

```markdown
# Instrucciones para Copilot

Soy estudiante de 2º de Bachillerato y estoy aprendiendo diseño web en TIC II.

- Responde siempre en español, de forma breve y clara.
- Antes de darme código, explícame la idea y, si puedes, dame una pista para que lo intente yo.
- Usa solo HTML5, CSS y JavaScript básicos, sin frameworks ni librerías externas.
- En HTML: sangría de 2 espacios, atributos en minúscula, lang="es" y alt en todas las imágenes.
- En CSS, usa solo: selectores (de etiqueta, clase, id, relación y atributo), pseudoclases de enlaces, colores, tipografía, texto, unidades, modelo de caja y position. No uses flexbox, grid ni media queries.
- En JavaScript, usa solo: let, const, arrays, operadores, if/else, while, do...while, for, funciones, onclick, document.getElementById(), innerHTML, .value, Number(), alert(), confirm(), prompt() y console.log(). No uses addEventListener, querySelector, funciones flecha ni plantillas de texto.
- Comenta el código en español.
```

Así, Copilot te propondrá código con lo que hemos visto en clase y no con cosas que no sabrías explicar.

## Reglas de uso en el proyecto

| Sí puedes | No puedes |
|---|---|
| Pedirle que te explique código o un error. | Usar el modo **Agent** para crear o modificar archivos. |
| Pedirle pistas para resolver algo tú. | Pegar en tu proyecto código que no entiendes. |
| Pedirle ideas de contenido o de diseño. | Usar elementos que no hemos visto en clase. |
| Pedirle que revise tu código y te diga qué mejorar. | Pedirle textos enteros y presentarlos como tuyos. |

Además, es **obligatorio**:

- Contar en el apartado «Uso de inteligencia artificial» del README para qué lo has usado.
- Poder explicar **cualquier línea** de tu proyecto en la presentación.

---

## Actividad guiada — Primeros pasos con Copilot

**Objetivo:** activar Copilot, configurarlo para la asignatura y usarlo para entender código, depurar un error y planificar el proyecto.

**Duración:** unos 25 minutos (sesión del 10/11).

**Pasos:**

1. Activa Copilot en VS Code e inicia sesión con tu cuenta de GitHub, siguiendo el apartado «Activarlo en VS Code».
2. En la raíz de tu repositorio, crea la carpeta `.github` y dentro el archivo `copilot-instructions.md` con el contenido del apartado anterior. Haz *commit* y *push*.
3. Abre `ejercicios-js/ej10-me-gusta/js/script.js`, selecciona la función `restar()` y pide en el chat (modo **Ask**): `/explain`. Compara su explicación con lo que tú sabes. ¿Ha dicho algo que no sea cierto?
4. Provoca un error a propósito: en `index.html` de ese ejercicio, cambia `onclick="sumar()"` por `onclick="sumarr()"`. Pulsa el botón y mira la consola (F12). Copia el error en el chat y pide: «Dame una pista de qué falla, sin darme la solución». Corrígelo tú.
5. Pide ideas para tu proyecto: «Voy a hacer un sitio web sobre *(tu tema)*. Propón 3 páginas y qué contenido llevaría cada una. No escribas código». Elige lo que te guste y apúntalo en un borrador de `proyecto/README.md`.
6. En el `index.html` de tu proyecto, escribe un comentario HTML que describa una lista y espera la sugerencia. Acéptala palabra a palabra y decide si te la quedas.

**Resultado esperado:** Copilot activo en tu VS Code, el archivo de instrucciones subido a GitHub, el error del paso 4 corregido por ti y un primer plan de las páginas de tu sitio en el README.

**Entrega:** no se entrega aparte. El archivo `.github/copilot-instructions.md` y el borrador de `proyecto/README.md` quedan en tu repositorio.

**Ampliación opcional:** pregúntale a Copilot «¿Qué le falta a mi página para ser accesible?» con tu `index.html` abierto. Comprueba si sus consejos tienen sentido con lo que sabes de `alt`, `label` y jerarquía de títulos.

---

## Errores frecuentes

- **Aceptar con Tab sin leer.** La sugerencia puede tener rutas, `id` o nombres de función que no existen en tu código. Lee siempre antes de aceptar.
- **Código con cosas que no hemos visto** (`addEventListener`, `querySelector`, flexbox…). Pídele que lo rehaga solo con lo visto en clase, o revisa tu archivo de instrucciones.
- **Creerse todo lo que dice.** Comprueba cada cambio en el navegador y en la consola (F12). Si la explicación no cuadra con los apuntes, fíate de los apuntes y pregunta al profesor.
- **Usar el modo Agent sin darte cuenta.** Mira el selector de modo antes de escribir: tiene que poner **Ask**.
- **Las instrucciones no se aplican.** El archivo debe llamarse exactamente `copilot-instructions.md` y estar en `.github/`, en la raíz del repositorio, no dentro de `proyecto/`.
- **El chat no responde o pide iniciar sesión.** No has iniciado sesión o lo has hecho con otra cuenta. Revisa la cuenta en el icono de perfil de VS Code.
- **Quedarse sin consultas a mitad del proyecto.** El plan gratuito tiene un límite mensual. No gastes el chat en lo que puedes mirar en los apuntes.
- **Pegar datos personales en el chat.** Nunca escribas contraseñas, teléfonos ni datos de otras personas.

---

[⬅ Volver a UT1](index.md) · [Ir a Instalación de VS Code](instalacion-vscode.md) · [Ir a HTML5](html.md) · [Ir a Prácticas de HTML5](practicas-html.md) · [Ir a Subir tus ejercicios a GitHub](github.md) · [Ir a CSS](css.md) · [Ir a Prácticas de CSS](practicas-css.md) · [Ir a JavaScript](javascript.md) · [Ir a Prácticas de JavaScript](practicas-js.md) · [Ir a Publicación web avanzada](publicacion-web.md) · [Ir a Proyecto final](proyecto.md)
