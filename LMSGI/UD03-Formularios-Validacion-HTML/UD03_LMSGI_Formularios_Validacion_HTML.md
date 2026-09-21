<div style="text-align: center;">

<img src="data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCA0MDAgNDAwIiB3aWR0aD0iMTgwIiBoZWlnaHQ9IjE4MCI+CiAgPGNpcmNsZSBjeD0iMjAwIiBjeT0iMjAwIiByPSIxNzAiIGZpbGw9IiNGMEZERkEiLz4KICA8Y2lyY2xlIGN4PSIyMDAiIGN5PSIyMDAiIHI9IjE3MCIgZmlsbD0ibm9uZSIgc3Ryb2tlPSIjOTlGNkU0IiBzdHJva2Utd2lkdGg9IjIiLz4KICA8cmVjdCB4PSIxMjAiIHk9Ijk1IiB3aWR0aD0iMTYwIiBoZWlnaHQ9IjIxMCIgcng9IjEwIiBmaWxsPSJub25lIiBzdHJva2U9IiMwRjc2NkUiIHN0cm9rZS13aWR0aD0iMTAiLz4KICA8cmVjdCB4PSIxNjUiIHk9IjgwIiB3aWR0aD0iNzAiIGhlaWdodD0iMjYiIHJ4PSI2IiBmaWxsPSIjRjBGREZBIiBzdHJva2U9IiMwRjc2NkUiIHN0cm9rZS13aWR0aD0iOCIvPgogIDxwYXRoIGQ9Ik0gMTUwIDE0NSBMIDE2MiAxNTcgTCAxODUgMTMwIiBmaWxsPSJub25lIiBzdHJva2U9IiMwRjc2NkUiIHN0cm9rZS13aWR0aD0iOCIgc3Ryb2tlLWxpbmVjYXA9InJvdW5kIiBzdHJva2UtbGluZWpvaW49InJvdW5kIi8+CiAgPGxpbmUgeDE9IjIwMCIgeTE9IjE0MyIgeDI9IjI1MiIgeTI9IjE0MyIgc3Ryb2tlPSIjMEY3NjZFIiBzdHJva2Utd2lkdGg9IjgiIHN0cm9rZS1saW5lY2FwPSJyb3VuZCIvPgogIDxwYXRoIGQ9Ik0gMTUwIDE5NSBMIDE2MiAyMDcgTCAxODUgMTgwIiBmaWxsPSJub25lIiBzdHJva2U9IiMwRjc2NkUiIHN0cm9rZS13aWR0aD0iOCIgc3Ryb2tlLWxpbmVjYXA9InJvdW5kIiBzdHJva2UtbGluZWpvaW49InJvdW5kIi8+CiAgPGxpbmUgeDE9IjIwMCIgeTE9IjE5MyIgeDI9IjI1MiIgeTI9IjE5MyIgc3Ryb2tlPSIjMEY3NjZFIiBzdHJva2Utd2lkdGg9IjgiIHN0cm9rZS1saW5lY2FwPSJyb3VuZCIvPgogIDxwYXRoIGQ9Ik0gMTUwIDI0NSBMIDE2MiAyNTcgTCAxODUgMjMwIiBmaWxsPSJub25lIiBzdHJva2U9IiMwRjc2NkUiIHN0cm9rZS13aWR0aD0iOCIgc3Ryb2tlLWxpbmVjYXA9InJvdW5kIiBzdHJva2UtbGluZWpvaW49InJvdW5kIi8+CiAgPGxpbmUgeDE9IjIwMCIgeTE9IjI0MyIgeDI9IjI1MiIgeTI9IjI0MyIgc3Ryb2tlPSIjMEY3NjZFIiBzdHJva2Utd2lkdGg9IjgiIHN0cm9rZS1saW5lY2FwPSJyb3VuZCIvPgo8L3N2Zz4K" width="180" alt="Logo LMSGI"/>

<h1>Unidad 3</h1>
<h2>Formularios avanzados y validación en HTML</h2>

<p>
<strong>Módulo:</strong> Llenguatges de Marques i Sistemes de Gestió d'Informació (LMSGI)<br>
<strong>Ciclo formativo:</strong> 1r ASIX (Administración de Sistemas Informáticos en Red) · 1r DAW (Desarrollo de Aplicaciones Web)<br>
<strong>Curso:</strong> 2026-2027
</p>

<p>
<strong>Docente:</strong> Noel Marco Biendicho<br>
<strong>Centro:</strong> IES Sant Vicent Ferrer — Algemesí
</p>

</div>

<div style="page-break-after: always;"></div>

## Índice

1. De los formularios básicos a los avanzados
   - 1.1 Repaso rápido: `<form>`, `<label>`, `<input>`
   - 1.2 Agrupar y organizar: `<fieldset>` y `<legend>`
2. Tipos de campo y controles de HTML5
3. Validación nativa de formularios
   - 3.1 Restricciones básicas: obligatoriedad, longitud y rango
   - 3.2 Patrones con expresiones regulares
   - 3.3 El estado de validación, a la espera de CSS
4. Envío de datos: `method` y `action`
5. Elementos semánticos de HTML5
6. Resumen de la unidad
7. Para saber más

<div style="page-break-after: always;"></div>

**RA cubierto:** RA2 — *Utiliza lenguajes de marcas para la transmisión y presentación de información a través de la Web, analizando la estructura de los documentos e identificando sus elementos* (CA 2b, 2c)

> 💡 **Nota de estudio**: en la UD2 ya escribisteis un formulario básico (`<form>`, `<label>`, un puñado de `<input>`) a modo de adelanto. Esta unidad retoma justo ahí: los mismos formularios, pero con todo el vocabulario de campos que ofrece HTML5, validación automática sin escribir una línea de JavaScript, y las etiquetas que dan significado a cada bloque de una página. Como en la UD2, es una unidad sobre todo práctica — la teoría es la mínima para que sepáis *por qué* funciona cada cosa.

---

## 1. De los formularios básicos a los avanzados

### 1.1 Repaso rápido: `<form>`, `<label>`, `<input>` (CA 2b, 2c)

**🧪 Paso a paso — Retoma tu formulario de la UD2**

1. Abre la carpeta `LMSGI/UD02` (o donde guardaras `inscripcion.html` en el ejercicio 4 de la UD2). Si no lo tienes a mano, crea uno nuevo con este contenido de partida:

   ```html
   <!DOCTYPE html>
   <html lang="es">
   <head>
     <meta charset="UTF-8">
     <title>Inscripción</title>
   </head>
   <body>
     <form>
       <label for="nombre">Nombre:</label>
       <input type="text" id="nombre" name="nombre"><br>

       <label for="email">Correo:</label>
       <input type="email" id="email" name="email"><br>

       <input type="submit" value="Enviar">
     </form>
   </body>
   </html>
   ```

2. Copia esta carpeta completa a una nueva, `LMSGI/UD03`, y trabaja a partir de ahí durante toda la unidad.

Recuerda lo que ya sabéis de la UD2: `<form>` envuelve todo el formulario; `<label for="...">` asocia un texto a un campo por su `id` (accesibilidad y clic en el texto); `<input>` es el campo en sí, y su atributo `type` decide qué se puede escribir. Lo que **no** vimos en detalle fue `name`, y ahora sí toca: es el identificador con el que viaja cada dato al enviarse — lo usaréis en el punto 4.

⚠️ **Error típico**: confundir `<label>` con el `placeholder` de un `<input>` (lo veréis en el punto 2). El `<label>` es el nombre permanente del campo — sigue visible aunque escribas dentro —, mientras que el `placeholder` es un texto de ayuda que **desaparece** en cuanto empiezas a escribir. Un formulario solo con `placeholder` y sin `<label>` es un problema de accesibilidad: un lector de pantalla no tiene nada que anunciar al enfocar el campo.

---

### 1.2 Agrupar y organizar: `<fieldset>` y `<legend>` (CA 2c)

Un formulario con muchos campos es más fácil de entender si se divide en bloques con sentido. Para eso existen `<fieldset>` (la agrupación) y `<legend>` (su título):

```html
<form>
  <fieldset>
    <legend>Datos personales</legend>

    <label for="nombre">Nombre:</label>
    <input type="text" id="nombre" name="nombre"><br>

    <label for="email">Correo:</label>
    <input type="email" id="email" name="email"><br>
  </fieldset>

  <fieldset>
    <legend>Preferencias</legend>

    <label for="modulo">Módulo favorito:</label>
    <input type="text" id="modulo" name="modulo"><br>
  </fieldset>

  <input type="submit" value="Enviar">
</form>
```

Por defecto el navegador dibuja un marco alrededor de cada `<fieldset>` con el texto de `<legend>` incrustado en el borde superior — puramente visual, sin necesidad de CSS. `<fieldset>` es un elemento de bloque más, como los `<div>` que ya conocéis de la UD2, solo que pensado específicamente para agrupar campos de formulario.

**🧪 Ejercicio 1 — Organiza tu inscripción**

Sobre tu `inscripcion.html` de la UD2 (ya copiado a `UD03`): agrupa los campos en al menos dos `<fieldset>` con su `<legend>` correspondiente (por ejemplo "Datos personales" y "Preferencias del curso"). Guarda y comprueba en Firefox que aparecen los dos marcos con su título.

---

## 2. Tipos de campo y controles de HTML5 (CA 2c)

En la UD2 solo usasteis `type="text"`, `type="email"`, `type="number"` y `type="checkbox"`. HTML5 amplió mucho esta lista — cada tipo no es solo una etiqueta distinta: cambia el **teclado o control que ofrece el navegador**, y en varios casos activa una validación básica automática (lo veréis en detalle en el punto 3).

| `type` | Qué ofrece el navegador | Ejemplo de uso |
|---|---|---|
| `text` | Caja de texto libre (el que ya conocéis) | Nombre, dirección |
| `email` | Teclado con `@` en móvil; exige un formato tipo correo | Correo electrónico |
| `password` | Oculta los caracteres al escribir | Contraseñas |
| `number` | Flechas para subir/bajar; teclado numérico en móvil | Edad, cantidad |
| `tel` | Teclado numérico en móvil (no valida formato, varía por país) | Teléfono |
| `url` | Exige un formato tipo `https://...` | Página web personal |
| `date` | Selector de calendario nativo | Fecha de nacimiento |
| `time` | Selector de hora nativo | Hora de una cita |
| `color` | Selector de color nativo (paleta del sistema operativo) | Elegir un color favorito |
| `range` | Control deslizante entre un mínimo y un máximo | Valorar del 1 al 10 |
| `search` | Como `text`, pero con una "x" para borrar el contenido | Buscador interno |
| `file` | Botón para seleccionar un archivo del equipo | Subir una foto |
| `hidden` | No se muestra — envía un valor fijo sin que el usuario lo vea | Un identificador interno |

> 📡 **Sigue vigente y muy usado hoy**: antes de HTML5, todo esto había que "simularlo" con JavaScript (un selector de fecha hecho a mano, validar un email con una expresión regular escrita por el programador...). Que el propio navegador lo resuelva de fábrica —gratis, accesible y con el mismo aspecto nativo del sistema operativo del usuario— es una de las mejoras más usadas de HTML5 en el desarrollo web real.

**Otros controles, más allá de `<input>`:**

- **`<textarea>`**: para texto largo de varias líneas — un `<input type="text">` solo admite una línea. Se controla el tamaño con `rows` (filas) y `cols` (columnas), y el texto va **entre** las etiquetas, no en un atributo `value`:
  ```html
  <label for="comentario">Comentario:</label><br>
  <textarea id="comentario" name="comentario" rows="5" cols="40">Escribe aquí...</textarea>
  ```
- **`<select>` / `<option>`**: una lista desplegable con opciones cerradas — a diferencia del `radio` que ya conocéis de la UD2 (donde se ven todas las opciones a la vez), aquí solo se ve una hasta que el usuario despliega la lista. Útil cuando hay muchas opciones:
  ```html
  <label for="modulo">Módulo favorito:</label>
  <select id="modulo" name="modulo">
    <option value="lmsgi">LMSGI</option>
    <option value="bd">Bases de Datos</option>
    <option value="prog">Programación</option>
  </select>
  ```
  El atributo `value` de cada `<option>` es lo que se envía realmente; el texto entre `<option>` y `</option>` es solo lo que ve el usuario — igual que pasaba con el `id`/etiqueta visible en otros elementos.
- **`<datalist>`**: una lista de sugerencias para un `<input>` normal — a medio camino entre texto libre y `<select>`, el usuario puede escribir lo que quiera o elegir una de las sugerencias:
  ```html
  <label for="ciudad">Ciudad:</label>
  <input type="text" id="ciudad" name="ciudad" list="ciudades">
  <datalist id="ciudades">
    <option value="Algemesí">
    <option value="Valencia">
    <option value="Alzira">
  </datalist>
  ```
  El `<input>` se conecta al `<datalist>` por el atributo `list`, que apunta al `id` del `<datalist>` — el mismo mecanismo de `for`/`id` que ya usáis con `<label>`.

**🧪 Ejercicio 2 — Explora los tipos de campo**

En tu `inscripcion.html`, dentro del `fieldset` de "Preferencias" (o uno nuevo), añade:
1. Un campo `type="date"` para la fecha de nacimiento.
2. Un campo `type="range"` con una etiqueta que pida valorar el módulo del 1 al 10.
3. Un `<select>` con al menos 3 `<option>` para elegir el módulo favorito (sustituyendo al campo de texto libre que teníais).
4. Un `<textarea>` de 4 filas para "comentarios adicionales".

Guarda y ábrelo en Firefox. Haz clic en el campo de fecha y en el de rango: fíjate en que el navegador dibuja un control completo (calendario, deslizador) sin que hayáis escrito nada de JavaScript.

---

## 3. Validación nativa de formularios (CA 2c)

### 3.1 Restricciones básicas: obligatoriedad, longitud y rango

HTML5 permite que el propio navegador compruebe si los datos son correctos **antes** de enviar el formulario, sin necesitar JavaScript. Se hace añadiendo atributos al `<input>`:

| Atributo | Qué hace | Ejemplo |
|---|---|---|
| `required` | El campo no puede quedar vacío | `<input type="text" required>` |
| `minlength` / `maxlength` | Longitud mínima/máxima de caracteres (texto) | `<input type="text" minlength="3" maxlength="20">` |
| `min` / `max` | Valor mínimo/máximo (números, fechas, rangos) | `<input type="number" min="0" max="120">` |
| `step` | El incremento permitido en campos numéricos | `<input type="number" step="5">` (solo múltiplos de 5) |
| `placeholder` | Texto de ayuda que desaparece al escribir (⚠️ visto en el punto 1: nunca sustituye a `<label>`) | `<input type="text" placeholder="Ej: Ana">` |
| `readonly` | Se puede ver y seleccionar, pero no editar | `<input type="text" value="Fijo" readonly>` |
| `disabled` | El campo queda inactivo y **no se envía** con el formulario | `<input type="text" disabled>` |

Pruébalo:

```html
<label for="nombre">Nombre:</label>
<input type="text" id="nombre" name="nombre" required minlength="2" maxlength="30"><br>

<label for="edad">Edad:</label>
<input type="number" id="edad" name="edad" min="14" max="99" required><br>
```

Si ahora pulsas "Enviar" dejando el nombre vacío, o escribiendo una edad de 200, el navegador **bloquea el envío** y muestra un mensaje automático señalando el campo — sin que hayáis escrito una sola línea de código para ese mensaje.

⚠️ **Importante — no es una medida de seguridad**: esta validación se ejecuta en el propio navegador del usuario, así que puede saltarse fácilmente (basta con desactivar JavaScript de ciertas formas, editar el HTML con las herramientas de desarrollador, o enviar la petición directamente sin pasar por el formulario). Sirve para dar una respuesta inmediata y cómoda al usuario que se equivoca sin querer, **nunca** para proteger un sistema: la validación real y fiable siempre debe repetirse en el servidor que recibe los datos, algo que queda fuera del alcance de este módulo.

**🧪 Ejercicio 3 — Restricciones a tu formulario**

Añade a tu `inscripcion.html`: `required` al nombre y al correo, `minlength="2"` al nombre, y `min`/`max` razonables al campo de fecha de nacimiento o de valoración (`range`) que creaste en el ejercicio 2. Comprueba en Firefox que el formulario no se envía si dejas el nombre vacío, y que el mensaje de error aparece señalando exactamente ese campo.

---

### 3.2 Patrones con expresiones regulares (CA 2c)

Cuando `required`, `min`/`max` o `minlength` no bastan para describir un formato concreto (por ejemplo, un código postal de 5 cifras, o un DNI con letra), se usa el atributo `pattern` con una **expresión regular**:

```html
<label for="cp">Código postal:</label>
<input type="text" id="cp" name="cp" pattern="[0-9]{5}" title="5 dígitos, por ejemplo 46680">
```

- `[0-9]{5}` significa "exactamente 5 caracteres, cada uno un dígito del 0 al 9".
- El atributo `title` no es decorativo aquí: muchos navegadores lo muestran dentro del mensaje de error automático cuando el patrón no coincide — es la forma de explicar al usuario *qué* formato se espera.

> 💡 Las expresiones regulares (*regex*) son un lenguaje en sí mismo para describir patrones de texto, con su propia sintaxis (`[0-9]` un dígito, `{5}` exactamente 5 veces, `+` una o más veces, `?` opcional...). No es contenido de esta unidad dominarlas a fondo — de momento basta con reconocer y adaptar patrones sencillos como el del ejemplo. Podéis apoyaros en la referencia de patrones de MDN (enlace al final de la unidad) para copiar y adaptar expresiones ya hechas, en vez de escribirlas de cero.

**🧪 Ejercicio 4 — Un patrón para tu formulario**

Añade un campo nuevo a tu `inscripcion.html` para un "código de alumno" con el patrón `[A-Z]{2}[0-9]{4}` (dos letras mayúsculas seguidas de 4 dígitos, por ejemplo `AS1234`). Añade un `title` explicando el formato esperado, y comprueba en Firefox qué pasa si escribes `as12` o `AS12345`.

---

### 3.3 El estado de validación, a la espera de CSS

Cuando un campo cumple sus restricciones, el navegador lo marca internamente como **válido**; si no las cumple, como **inválido** — es lo que consulta para decidir si bloquea el envío. Este estado también se puede usar para dar estilo visual al campo, con los selectores CSS `:valid` y `:invalid`:

```css
input:invalid {
  border: 2px solid red;
}
input:valid {
  border: 2px solid green;
}
```

> 🕰️ **De momento, solo un adelanto**: no habéis visto todavía selectores CSS (llegan en la UD4), así que no hace falta que apliquéis este código ahora — solo que sepáis que existe y que la validación de este punto 3 no es solo funcional, también se puede *ver*. Lo retomaréis en la UD4 al estudiar las pseudoclases.

---

## 4. Envío de datos: `method` y `action` (CA 2b)

Hasta ahora vuestros formularios no enviaban los datos a ningún sitio real. El destino y la forma de envío se controlan con dos atributos del propio `<form>`:

```html
<form action="/procesar-inscripcion" method="post">
  ...
</form>
```

- **`action`**: la URL (recordad el concepto de la UD1 — absoluta o relativa, igual que en los enlaces `<a href>` de la UD2) del recurso que recibirá los datos. Si se omite, el formulario se envía a la propia página actual.
- **`method`**: cómo viajan los datos. Los dos valores más habituales:

| `method` | Cómo viajan los datos | Cuándo se usa |
|---|---|---|
| `GET` | Van añadidos a la URL, visibles, como una *query string* (`?nombre=Ana&edad=20`) | Búsquedas, filtros — datos que tiene sentido ver en la URL o guardar como marcador |
| `POST` | Van "ocultos" en el cuerpo de la petición, no aparecen en la URL | Formularios con datos sensibles o extensos — inscripciones, contraseñas, subir archivos |

**🧪 Paso a paso — Compruébalo con tus propios ojos**

1. En tu `inscripcion.html`, pon `method="get"` en el `<form>` (sin `action`, o con `action=""`).
2. Rellena el formulario y pulsa "Enviar". Fíjate en la barra de direcciones de Firefox: verás algo como `.../inscripcion.html?nombre=Ana&edad=20&modulo=lmsgi...`
3. Cambia ahora a `method="post"` y repite el envío. ¿Qué diferencia ves en la barra de direcciones esta vez?

⚠️ Ni con `GET` ni con `POST` llega a existir todavía un "proceso servidor" real que reciba y guarde esos datos — eso requeriría un programa del lado del servidor (PHP, Node, Python...), que queda fuera del contenido de este módulo. Lo que habéis comprobado con el paso a paso es únicamente **cómo viajan** los datos, no qué se hace con ellos al llegar.

**🧪 Ejercicio 5 — GET o POST, razonado**

Para cada uno de estos formularios, indica si usarías `GET` o `POST` y justifica tu respuesta con lo visto en la tabla: (a) un buscador de productos en una tienda online, (b) un formulario de cambio de contraseña, (c) un formulario para filtrar una tabla de alumnos por módulo.

---

## 5. Elementos semánticos de HTML5 (CA 2c)

En la UD2 ya construisteis páginas con `<div>` y `<span>` — contenedores genéricos que no dicen nada sobre *qué es* cada bloque, solo que existe. HTML5 añadió un conjunto de etiquetas que sí lo dicen: los **elementos semánticos**.

```html
<body>
  <header>
    <h1>Mi página de módulos</h1>
    <nav>
      <a href="#inicio">Inicio</a>
      <a href="#contacto">Contacto</a>
    </nav>
  </header>

  <main>
    <article>
      <h2>LMSGI</h2>
      <p>Llenguatges de Marques i Sistemes de Gestió d'Informació.</p>
    </article>

    <aside>
      <p>¿Sabías que HTML5 añadió más de una docena de tipos de <code>&lt;input&gt;</code>?</p>
    </aside>
  </main>

  <footer>
    <address>Contacto: noel@iessvf.es</address>
  </footer>
</body>
```

| Etiqueta | Para qué sirve |
|---|---|
| `<header>` | Cabecera de la página o de una sección — logo, título, navegación principal |
| `<nav>` | Un bloque de enlaces de navegación |
| `<main>` | El contenido principal de la página — solo puede haber uno por documento |
| `<article>` | Una pieza de contenido independiente, que tendría sentido por sí sola (una noticia, un post) |
| `<section>` | Una sección temática dentro de un documento o `<article>`, normalmente con su propio título |
| `<aside>` | Contenido relacionado pero secundario — una barra lateral, una nota destacada |
| `<footer>` | Pie de página o de sección — datos de contacto, licencia, enlaces relacionados |
| `<address>` | Información de contacto del autor — el navegador suele mostrarla en cursiva |

> 📡 **Por qué esto no es solo estética**: en la UD2 (apartado "Para saber más") ya adelantamos que la normativa europea de accesibilidad digital (Directiva (UE) 2019/882) obliga a buena parte de las webs de administraciones y empresas a cumplir criterios WCAG. Usar `<nav>` en vez de un `<div class="nav">` no cambia nada visualmente por defecto, pero sí para un lector de pantalla: anuncia "navegación" en vez de una caja genérica sin significado, exactamente el mismo tipo de detalle que el `alt` de las imágenes o el `<label for>` de los formularios que ya conocéis. También ayuda a que los buscadores entiendan mejor la estructura de la página al indexarla.

⚠️ **No sustituyen a `<div>`/`<span>`, los complementan**: seguid usando `<div>` y `<span>` para agrupar contenido que no encaja en ninguna de estas categorías con significado propio — no hace falta forzar un `<section>` donde solo hace falta una caja para aplicar estilos.

**🧪 Ejercicio 6 — Semantiza tu ficha de alumno**

Recupera `ficha-alumno.html` de la UD2 (ejercicio 2). Reestructúralo usando elementos semánticos: un `<header>` con el nombre del alumno, un `<main>` que contenga la lista de módulos y la tabla de notas, y un `<footer>` con un enlace a la web del centro. El contenido no cambia — solo las etiquetas que lo envuelven.

---

## 🎯 Reto de clase — Ficha de inscripción completa

Con todo lo visto en esta unidad, crea un archivo nuevo `inscripcion-final.html` que combine:

1. **Estructura semántica**: `<header>` con un título, `<main>` con el formulario, `<footer>` con un enlace de vuelta a `ficha-alumno.html`.
2. **Formulario organizado** en al menos dos `<fieldset>` con `<legend>` ("Datos personales" y "Preferencias", por ejemplo).
3. **Al menos 6 tipos de campo distintos** entre `type="text"`, `email`, `date`, `range`, `<select>`, `<textarea>` y `<datalist>`.
4. **Validación nativa**: `required` en al menos dos campos, un `pattern` con expresión regular en uno de ellos (con su `title` explicativo), y un `min`/`max` razonable en el de tipo numérico o rango.
5. **Envío de datos**: decide tú, justificando tu elección por escrito en un comentario HTML al principio del archivo, si usarás `method="get"` o `method="post"` para este formulario en concreto.

Compruébalo en Firefox: que el envío se bloquee si falta un campo obligatorio o si el patrón no coincide, y que cada `fieldset` se vea agrupado visualmente.

---

## Resumen de la unidad

**1. De los formularios básicos a los avanzados** *(CA 2b, 2c)* Repaso de `<form>`, `<label for>` e `<input>` de la UD2, con el atributo `name` ya explicado. Agrupación de campos con `<fieldset>` y `<legend>`.

**2. Tipos de campo y controles de HTML5** *(CA 2c)* Más de una docena de tipos de `<input>` (`email`, `date`, `range`, `color`...) que activan controles nativos del navegador sin JavaScript. `<textarea>` para texto largo, `<select>`/`<option>` para listas cerradas, `<datalist>` para sugerencias sobre un campo libre.

**3. Validación nativa de formularios** *(CA 2c)* Restricciones declarativas (`required`, `minlength`/`maxlength`, `min`/`max`, `step`) y patrones con expresiones regulares (`pattern` + `title`) que bloquean el envío y muestran un mensaje automático — validación cómoda para el usuario, nunca una medida de seguridad real. Los estados `:valid`/`:invalid` quedan adelantados para la UD4.

**4. Envío de datos** *(CA 2b)* `action` (destino) y `method` (`GET`, visible en la URL; `POST`, oculto en el cuerpo) del `<form>` — sin necesidad todavía de un proceso servidor real que los reciba.

**5. Elementos semánticos de HTML5** *(CA 2c)* `<header>`, `<nav>`, `<main>`, `<article>`, `<section>`, `<aside>`, `<footer>`, `<address>` — dan significado a cada bloque de la página, más allá de lo que hacía un `<div>` genérico, con impacto directo en accesibilidad y en cómo indexan la página los buscadores.

---

## 📚 Para saber más (opcional, no evaluable)

### ¿Para qué te va a servir lo de esta unidad?

Lo que habéis visto aquí (campos avanzados, validación nativa, semántica) es la base de cualquier formulario web real. La validación real y segura de estos datos —la que de verdad protege un sistema— la veréis con JavaScript en la **UD6** (manipulación de documentos web), y las pseudoclases `:valid`/`:invalid` del punto 3.3 se retoman en la **UD4**, al estudiar selectores CSS.

A fecha de este curso (2026-2027), conviene saber:

- **La validación nativa sigue ganando terreno**: cada versión de los navegadores añade nuevos tipos de `<input>` y atributos de validación, reduciendo la necesidad de JavaScript para casos sencillos — es una tendencia activa, no un estándar cerrado desde hace años.
- **Accesibilidad, cada vez más exigida por ley**: como ya se apuntó en la UD2, la normativa europea (Directiva (UE) 2019/882) obliga a auditar criterios WCAG en webs de administraciones y empresas — un `<label for>` bien asociado o un `<nav>` en vez de un `<div>` son exactamente el tipo de detalle auditado, y los habéis usado ya en esta unidad.
- **Frameworks de formularios**: en proyectos grandes (sobre todo con JavaScript, que veréis en la UD6) es habitual apoyarse en librerías que gestionan la validación y el envío de formularios de forma más avanzada — pero todas ellas parten exactamente de los atributos HTML nativos vistos aquí, no los sustituyen.

- MDN — Formularios HTML: https://developer.mozilla.org/es/docs/Learn/Forms
- MDN — Referencia de patrones de expresiones regulares: https://developer.mozilla.org/es/docs/Web/HTML/Attributes/pattern
- W3Schools — Tipos de `<input>`: https://www.w3schools.com/html/html_form_input_types.asp
