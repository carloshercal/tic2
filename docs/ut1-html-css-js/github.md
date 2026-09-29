---
title: UT1 — Subir tus ejercicios a GitHub
---

# Subir tus ejercicios a GitHub

A partir de ahora, los ejercicios de HTML no se entregan copiando archivos: se **suben a un repositorio de GitHub**, propio de cada alumno, dentro de la organización de la asignatura. Así el profesor puede ver tu progreso y corregir directamente sobre tu código.

Esta guía usa la interfaz de VS Code (panel **Source Control**), pero cada paso incluye también el comando de **Git** equivalente, por si prefieres o necesitas usar la terminal.

## 1. Antes de empezar

1. Si todavía no tienes cuenta de GitHub, créala en [github.com](https://github.com/join). Usa un nombre de usuario razonable (tu nombre o algo reconocible), porque va a quedar asociado a tu trabajo durante el curso.
2. Comunica tu **usuario de GitHub** a tu profesor por el canal que os indique (Teams). Con ese dato se te creará un repositorio privado, ya preparado, dentro de la organización de la asignatura.
3. En cuanto se te añada como colaborador, GitHub te enviará un aviso (correo o notificación en github.com). Entra en ese enlace, o directamente en la URL de tu repositorio, y pulsa el botón **Accept invitation** que aparece arriba del todo. **Sin este paso no podrás clonar el repositorio**, aunque ya exista.
4. Tu repositorio sigue siempre este patrón de nombre, por si quieres localizarlo tú mismo sin esperar a que te pasen el enlace:
   ```
   https://github.com/iesviadelaplata-tic2-2026/ut1-html-css-js-TU-USUARIO
   ```
   (sustituye `TU-USUARIO` por tu usuario de GitHub, en minúsculas).

> No crees tú el repositorio: se te crea desde una plantilla ya organizada, con la estructura de carpetas y el `.gitignore` correctos. Tú solo tienes que clonarlo y empezar a trabajar en él.

> **Solo si vas a usar la terminal** (si solo usas el panel Source Control de VS Code, no lo necesitas): Git debe conocer tu nombre y correo para firmar tus commits. Se configura una sola vez, la primera vez que uses Git en tu ordenador:
> ```bash
> git config --global user.name "Tu Nombre"
> git config --global user.email "tu-correo@ejemplo.com"
> ```

## 2. Clonar tu repositorio en VS Code

1. Abre VS Code y pulsa el icono de **Source Control** en la barra lateral (o `Ctrl + Shift + G`).
2. Pulsa **Clone Repository** → **Clone from GitHub**.
3. La primera vez, VS Code te pedirá iniciar sesión: se abrirá el navegador para que autorices el acceso con tu cuenta de GitHub. Acepta.
4. Busca o pega la URL de tu repositorio (tiene esta forma: `https://github.com/iesviadelaplata-tic2-2026/ut1-html-css-js-tu-usuario`).
5. Elige, en tu ordenador, la carpeta donde quieres guardarlo (por ejemplo, dentro de tu carpeta de la asignatura).
6. Cuando termine, pulsa **Open** para abrir esa carpeta como espacio de trabajo.

A partir de aquí, esta carpeta clonada es donde vas a hacer todos los ejercicios de esta unidad — sustituye a la carpeta local que usabas hasta ahora.

**Equivalente en terminal:** abre un terminal (en VS Code, `Ctrl + ñ`), sitúate en la carpeta donde quieras guardar el repositorio y ejecuta:

```bash
git clone https://github.com/iesviadelaplata-tic2-2026/ut1-html-css-js-tu-usuario.git
```

Esto crea una carpeta nueva con el nombre del repositorio (`ut1-html-css-js-tu-usuario`) y descarga dentro todo su contenido. Entra en ella y ábrela en VS Code:

```bash
cd ut1-html-css-js-tu-usuario
code .
```

## 3. El flujo de trabajo: guardar cambios en GitHub

Cada vez que termines un ejercicio (o avances algo importante en él), repite estos cuatro pasos:

1. **Guarda** el archivo (`Ctrl + S`) como siempre.
2. Abre el panel **Source Control** (`Ctrl + Shift + G`). Verás listados los archivos que has creado o modificado.
3. Pasa el ratón sobre "Changes" y pulsa el icono **+** (o **Stage All Changes**) para preparar esos cambios.
4. Escribe un **mensaje de commit** breve y descriptivo en el cuadro de texto de arriba (por ejemplo: `Ejercicio 3: estructura semántica`) y pulsa el botón **✓ Commit**.
5. Pulsa **Sync Changes** (el icono con las dos flechas, o el botón que aparece tras el commit) para **subir** (`push`) el cambio a GitHub.

```
guardar → stage (+) → commit (✓ con mensaje) → sync / push (↑↓)
```

**Equivalente en terminal:** los mismos cuatro pasos, con comandos de Git:

```bash
git add .
git commit -m "Ejercicio 3: estructura semántica"
git push
```

- `git add .` prepara (*stage*) todos los archivos nuevos o modificados de la carpeta actual — es el equivalente al botón **+**.
- `git commit -m "..."` guarda esos cambios en el historial local, con el mensaje entre comillas — equivale al botón **✓ Commit**.
- `git push` sube los commits guardados en tu ordenador al repositorio de GitHub — equivale a **Sync Changes**.

> **Haz commit por ejercicio, no todo junto al final.** Cada commit queda registrado con fecha y hora en el historial: es la forma en la que tu profesor ve cómo has ido avanzando, no solo el resultado final.

## 4. Comprobar que se ha subido bien

Entra en la URL de tu repositorio desde el navegador (`https://github.com/iesviadelaplata-tic2-2026/ut1-html-css-js-tu-usuario`) y comprueba:

- Que tus archivos aparecen en la lista, con la estructura de carpetas correcta.
- Que en la pestaña **Commits** aparece tu historial, con tus mensajes.

Si no ves tus últimos cambios, seguramente te falta el último paso (**Sync Changes** / `push`): el commit se guarda en tu ordenador, pero no llega a GitHub hasta que lo subes.

**Equivalente en terminal:** dos comandos útiles para comprobar el estado sin salir de VS Code:

```bash
git status
```

Te dice si tienes archivos sin guardar (*stage*) o commits pendientes de subir (`push`). Si todo está subido, responde `nothing to commit, working tree clean` y `Your branch is up to date with 'origin/main'`.

```bash
git log --oneline
```

Muestra el historial de commits, uno por línea, del más reciente al más antiguo — así puedes comprobar que tus mensajes y el orden de entrega son correctos.

## 5. Buenas prácticas

- Haz `commit` + `push` **al terminar cada ejercicio**, no lo dejes todo para el último día.
- Escribe mensajes de commit que digan **qué** has hecho («Ejercicio 5: galería de imágenes»), no «cambios» o «arreglos».
- No borres ni renombres la carpeta de ejercicios ya entregados sin avisar: el historial de commits es parte de la evaluación.
- Si algo no sube o te aparece un error, haz una captura de pantalla y consulta al profesor antes de intentar «arreglarlo» borrando y creando de nuevo la carpeta.

## Errores frecuentes

- **`fatal: repository not found` al clonar.** Todavía no has aceptado la invitación de colaborador (paso 1.3), o has escrito mal la URL. Revisa que copias la URL exacta de tu repositorio.
- **`Please tell me who you are` al hacer `git commit` desde la terminal.** Te falta configurar tu nombre y correo (ver el aviso al principio de la sección 1): ejecuta los dos comandos `git config --global ...` y repite el commit.
- **`git push` da un error de permisos o pide usuario y contraseña que no funcionan.** GitHub ya no acepta la contraseña de tu cuenta para esto. Usa el inicio de sesión de VS Code (paso 2.3), que gestiona la autenticación por ti; si trabajas por terminal, pide ayuda al profesor para configurar la autenticación.
- **Los cambios no aparecen en github.com aunque has hecho commit.** Te falta el último paso: **Sync Changes** en VS Code, o `git push` en la terminal. El commit por sí solo solo se guarda en tu ordenador.
- **Aparece un archivo o carpeta que no debería subirse** (como `node_modules` o archivos del sistema). No lo añadas a mano: comprueba que el `.gitignore` de la plantilla sigue en su sitio y no lo has borrado.

## Checklist final

- [ ] Cuenta de GitHub creada y usuario compartido con el profesor
- [ ] Repositorio clonado en VS Code con *Clone Repository*
- [ ] Al menos un `commit` + `push` realizado y comprobado en github.com
- [ ] Un commit por ejercicio, con mensajes descriptivos

---

[⬅ Volver a UT1](index.md) · [Ir a Instalación de VS Code](instalacion-vscode.md) · [Ir a HTML5](html.md) · [Ir a Prácticas de HTML5](practicas-html.md) · [Ir a CSS](css.md) · [Ir a JavaScript](javascript.md) · [Ir a Publicación web avanzada](publicacion-web.md)