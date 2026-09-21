<div style="text-align: center;">

<img src="data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCA0MDAgNDAwIiB3aWR0aD0iMTgwIiBoZWlnaHQ9IjE4MCI+CiAgPGNpcmNsZSBjeD0iMjAwIiBjeT0iMjAwIiByPSIxNzAiIGZpbGw9IiNGMEZERkEiLz4KICA8Y2lyY2xlIGN4PSIyMDAiIGN5PSIyMDAiIHI9IjE3MCIgZmlsbD0ibm9uZSIgc3Ryb2tlPSIjOTlGNkU0IiBzdHJva2Utd2lkdGg9IjIiLz4KICA8Y2lyY2xlIGN4PSIyMDAiIGN5PSIyMDAiIHI9IjExMCIgZmlsbD0ibm9uZSIgc3Ryb2tlPSIjMEY3NjZFIiBzdHJva2Utd2lkdGg9IjE0Ii8+CiAgPGVsbGlwc2UgY3g9IjIwMCIgY3k9IjIwMCIgcng9IjQ1IiByeT0iMTEwIiBmaWxsPSJub25lIiBzdHJva2U9IiMwRjc2NkUiIHN0cm9rZS13aWR0aD0iMTAiLz4KICA8bGluZSB4MT0iOTAiIHkxPSIyMDAiIHgyPSIzMTAiIHkyPSIyMDAiIHN0cm9rZT0iIzBGNzY2RSIgc3Ryb2tlLXdpZHRoPSIxMCIvPgogIDxwYXRoIGQ9Ik0gMTEwIDE0NSBRIDIwMCAxNzUgMjkwIDE0NSIgZmlsbD0ibm9uZSIgc3Ryb2tlPSIjMEY3NjZFIiBzdHJva2Utd2lkdGg9IjgiLz4KICA8cGF0aCBkPSJNIDExMCAyNTUgUSAyMDAgMjI1IDI5MCAyNTUiIGZpbGw9Im5vbmUiIHN0cm9rZT0iIzBGNzY2RSIgc3Ryb2tlLXdpZHRoPSI4Ii8+Cjwvc3ZnPgo=" width="180" alt="Logo UD2 LMSGI — globo terráqueo"/>

<h1>Unidad 2</h1>
<h2>Utilización de los lenguajes de marcas en la Web</h2>

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

1. HTML en el panorama de la Web: clasificación y evolución (CA 2a)
   - 1.1 Los lenguajes de marcas de la Web
   - 1.2 La evolución de las versiones de HTML
2. Estructura de un documento HTML (CA 2b)
3. Etiquetas y atributos principales: construyendo una página completa (CA 2c)
   - 3.1 Texto, listas y enlaces
   - 3.2 Tablas
   - 3.3 Imágenes y contenedores genéricos
4. XHTML: sintaxis estricta y conversión (CA 2d)
5. Formularios básicos: elementos y tipos de campo

6. Resumen de la unidad
7. Para saber más

<div style="page-break-after: always;"></div>

**RA cubierto:** RA2 — *Utiliza lenguajes de marcas para la transmisión y presentación de información a través de la Web, analizando la estructura de los documentos e identificando sus elementos* (CA 2a-2e)

> 💡 **Nota de estudio**: esta unidad es más corta que la UD1 (en torno a 6-7 horas lectivas frente a las 12 de la UD1) porque es sobre todo práctica — vais a escribir bastante HTML de verdad. La teoría es breve a propósito; el aprendizaje real viene de teclear, guardar y abrir en el navegador. A partir de aquí, cuando un ejemplo pida "ábrelo en Firefox", hazlo de verdad — HTML se aprende viendo el resultado, no solo leyendo el código.

---

## 1. HTML en el panorama de la Web: clasificación y evolución (CA 2a)

### 1.1 Los lenguajes de marcas de la Web

En la UD1 vimos que **HTML** es una *aplicación de SGML* — a diferencia de XML, que es un metalenguaje con el que tú defines tus propias etiquetas, HTML tiene un vocabulario de etiquetas **fijo**, definido por un estándar, pensado específicamente para estructurar páginas web. Esa relación con SGML es sobre todo histórica: hoy el HTML Living Standard define sus propias reglas de análisis y evolución, independientes de SGML.

No es el único lenguaje de marcas relacionado con la Web, aunque sí el más importante:

| Lenguaje | Qué es | ¿Dónde lo veréis en este módulo? |
|---|---|---|
| **HTML** | Estructura y contenido de una página web | Esta unidad y las siguientes |
| **XHTML** | Reformulación de HTML con sintaxis XML estricta | Punto 4 |
| **CSS** | Presentación visual (colores, tamaños, disposición) | UD4 y UD5 |
| **SVG** | Gráficos vectoriales — ya lo visteis en la UD1 (el logo `</>` de la portada de aquella unidad) | Se puede incrustar directamente en HTML |

> 📡 **Recordatorio de la UD1 (apartado 4.1)**: desde 2019 el W3C cedió la autoridad del estándar HTML al **WHATWG**, que lo mantiene como *Living Standard* — un documento único que se actualiza continuamente, sin cerrarse nunca en un número de versión. "HTML5" es hoy más una etiqueta de marketing que una versión formal cerrada. Esto es clave para entender el siguiente apartado.

Los navegadores no son los únicos programas que leen HTML: un lector de pantalla anuncia el contenido por voz, un buscador lo rastrea para indexarlo, un framework de *testing* automatizado lo recorre para hacer clic en botones... todos ellos son *user-agents* distintos interpretando el mismo documento marcado, exactamente como vimos en la UD1 (apartado 1).

---

### 1.2 La evolución de las versiones de HTML

Antes de escribir HTML conviene saber, en dos frases, de dónde viene, porque todavía os vais a encontrar código antiguo con marcas de una época distinta: entre 1995 y 2014 fue una sucesión de **versiones cerradas y numeradas** (HTML 2.0 a HTML5), con un intento a medio camino de reescribirlo con la sintaxis estricta de XML — **XHTML** (2000-2001, ved el punto 4) — que quedó en desuso hace años. Desde 2019 el WHATWG lo mantiene como el **Living Standard** que ya conocéis de la UD1: un documento único que se actualiza sin cerrarse nunca en un número de versión.

En resumen: hoy "HTML5" ya no describe una versión cerrada, sino que es la forma coloquial de referirse al estándar vivo actual.

> 🕰️ **Por qué esto importa en la práctica**: si alguna vez abrís código HTML muy antiguo y veis un `<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01//EN" "http://www.w3.org/TR/html4/strict.dtd">`, no os asustéis — es un DOCTYPE de la época en la que HTML citaba literalmente un DTD externo (el mismo concepto de DTD que construisteis paso a paso en la UD1, apartado 4.2, con el catálogo de series). HTML5 simplificó esto radicalmente: ya no depende de ningún DTD, así que su DOCTYPE es solo `<!DOCTYPE html>`, como veréis en el punto 2.

---

## 2. Estructura de un documento HTML (CA 2b)

Vamos a verlo con las manos antes que con la teoría.

**🧪 Paso a paso — Tu primer documento HTML**

1. En tu carpeta `LMSGI` (la que creasteis en la UD1), crea una nueva carpeta `UD02`.
2. Abre VS Code sobre esa carpeta (`Aplicaciones → Programación → VS Code`, o desde una terminal con `code UD02`) y crea un archivo nuevo llamado `index.html`.
3. Escribe exactamente esto:

```html
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <title>Mi primera página</title>
</head>
<body>
  <h1>Hola mundo</h1>
  <p>Este es mi primer documento HTML de la UD2.</p>
</body>
</html>
```

4. Guarda (`Ctrl+S`) y ábrelo con Firefox: clic derecho sobre `index.html` en el explorador de archivos de VS Code → *Reveal in Files* → doble clic, o arrastrando el archivo a una ventana de Firefox ya abierta.
5. Fíjate en dos sitios distintos: la **pestaña** del navegador y el **cuerpo** de la página. ¿Qué texto aparece en cada uno?

Ya tenéis el esqueleto que va a tener todo documento HTML que escribáis. Por partes:

- **`<!DOCTYPE html>`**: le dice al navegador que interprete la página en modo estándar HTML5 (frente al "quirks mode" que se activa si falta). No es una etiqueta con cierre, es una declaración.
- **`<html lang="es">`**: el elemento raíz — como el elemento raíz único que visteis en XML en la UD1, solo puede haber uno. El atributo `lang` indica el idioma principal del documento (accesibilidad y buscadores).
- **`<head>`**: metainformación que **no se muestra** en la página — título de pestaña, codificación, enlaces a hojas de estilo (UD4), metadatos para buscadores...
  - **`<meta charset="UTF-8">`**: declara la codificación de caracteres, igual que hacía `encoding="UTF-8"` en la declaración XML de la UD1 — es lo que permite que tildes, `ç` y `ñ` se vean bien en cualquier sistema.
  - **`<title>`**: el texto que aparece en la pestaña del navegador. No confundir con `<h1>`, que es un titular visible **dentro** de la página — es el error más típico al empezar.
- **`<body>`**: todo el contenido visible de la página.

⚠️ **Importante**: a diferencia de XML (UD1, apartado 4.3), HTML **no exige** que todo esté siempre bien cerrado o en minúsculas para funcionar — el navegador "perdona" muchos errores. Pero eso no significa que esté bien escribir HTML descuidado: un documento HTML bien formado es más fácil de mantener, se comporta igual en todos los navegadores y es imprescindible si en el punto 4 queréis convertirlo a XHTML.

**🧪 Ejercicio 1 — Comprueba qué hace cada línea**

Sobre tu propio `index.html`: cambia el `<title>` por tu nombre y el `<h1>` por un saludo, guarda y recarga Firefox — confirma que el cambio de `<title>` solo se ve en la pestaña y el de `<h1>` solo en la página. Después, borra la línea `<meta charset="UTF-8">`, guarda y recarga: si tu documento tiene alguna tilde o `ñ`, ¿qué le pasa? Vuelve a añadir la línea y comprueba que se arregla.

---

## 3. Etiquetas y atributos principales: construyendo una página completa (CA 2c)

En la UD1 ya usasteis `<h1>`-`<h6>` y `<p>`. Vamos a ampliar `index.html` paso a paso, añadiendo bloque a bloque el resto de etiquetas con las que se construye la mayoría de páginas web reales — al final tendrás una página completa, no fragmentos sueltos.

### 3.1 Texto, listas y enlaces

Añade esto dentro de tu `<body>`, debajo del `<p>` que ya tenías:

```html
<h2>Mis módulos</h2>
<ul>
  <li>LMSGI</li>
  <li>Bases de Datos</li>
  <li>Programación</li>
</ul>

<h2>Pasos para hoy</h2>
<ol>
  <li>Abrir VS Code</li>
  <li>Escribir el HTML</li>
  <li>Guardar y abrir en Firefox</li>
</ol>

<p>Más información en la <a href="https://www.iessvf.es" target="_blank">web del centro</a>.</p>
```

- `<ul>` (*unordered list*) para listas sin orden importante (con viñetas); `<ol>` (*ordered list*) cuando el orden importa (numerada automáticamente). Cada elemento va dentro de un `<li>` (*list item*).
- `<a href="...">`: un enlace **absoluto** (`https://...`) apunta a cualquier sitio de Internet; un enlace **relativo** (por ejemplo `ficha-alumno.html`, que usaréis en el punto 3.3) apunta a un archivo dentro de vuestro propio proyecto — más recomendable mientras trabajáis en local, porque no depende de que el otro sitio exista. `target="_blank"` abre el enlace en una pestaña nueva.

Guarda y recarga Firefox — comprueba que se ven las dos listas y que el enlace funciona.

---

### 3.2 Tablas

Recuperando el ejemplo de la discografía de la UD1 (apartado 4.2, ejercicio 6, donde lo hicisteis en XML), así se vería la misma información en HTML. Añade esto a continuación:

```html
<h2>Discografía</h2>
<table>
  <thead>
    <tr>
      <th>Título</th>
      <th>Año</th>
      <th>Agotado</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Álbum A</td>
      <td>2019</td>
      <td>No</td>
    </tr>
    <tr>
      <td>Álbum B</td>
      <td>2021</td>
      <td>Sí</td>
    </tr>
  </tbody>
</table>
```

`<table>` contiene filas `<tr>` (*table row*); `<th>` (*table header*) son las celdas de cabecera y `<td>` (*table data*) las celdas normales. `<thead>`/`<tbody>` son opcionales pero recomendables: separan semánticamente la cabecera del cuerpo de datos.

> 💡 Fíjate en el paralelismo con la UD1: en XML decidíais vosotros las etiquetas (`<disco>`, `<agotado/>`, apartado 4.2); en HTML las etiquetas de tabla ya existen y están fijadas por el estándar — es la diferencia entre un lenguaje de marcas de propósito general (XML) y uno de propósito específico para la Web (HTML) que vimos en el punto 1.1.

---

### 3.3 Imágenes y contenedores genéricos

Por último, añade una imagen y un bloque agrupado:

```html
<img src="logo.png" alt="Logotipo del IES Sant Vicent Ferrer">

<div class="tarjeta">
  <span id="destacado">Texto destacado</span> dentro de un párrafo normal.
</div>
```

- `src` indica la ruta del archivo (relativa o absoluta, igual que en los enlaces); `alt` es un texto alternativo — **obligatorio por accesibilidad**: es lo que anuncia un lector de pantalla (¿recordáis los *user-agents* de la UD1, apartado 1?) y lo que se muestra si la imagen no carga.
- `<div>` agrupa contenido en bloque (ocupa toda la anchura disponible); `<span>` agrupa contenido en línea (solo lo que envuelve). Por sí solos no significan nada — son "cajas" genéricas que cobran sentido con CSS (UD4) o JavaScript.
- **Atributos comunes** a casi cualquier etiqueta: `id` (identificador único en la página, no se puede repetir), `class` (etiqueta reutilizable para agrupar varios elementos), `title` (texto que aparece como *tooltip* al pasar el ratón).

Si no tienes ninguna imagen a mano, no pasa nada: guarda cualquier `.png`/`.jpg` en la misma carpeta que `index.html` con el nombre `logo.png`, o cambia el `src` por el nombre del archivo que tengas.

**🧪 Ejercicio 2 — Ficha web de un alumno**

Ahora, por tu cuenta y en un archivo nuevo `ficha-alumno.html` (con el esqueleto completo del punto 2), crea la ficha web de un alumno — puedes reutilizar a Claudia de la UD1 o inventar tus propios datos:
1. Un `<h1>` con el nombre del alumno.
2. Una lista `<ul>` con sus módulos favoritos.
3. Una tabla con sus notas (mínimo 3 filas, columnas: módulo y nota).
4. Un enlace a la web del centro.
5. Una imagen cualquiera, con su `alt` describiéndola de verdad (no "imagen1.jpg").

Comprueba el resultado en Firefox antes de continuar — lo necesitarás para el ejercicio siguiente.

---

## 4. XHTML: sintaxis estricta y conversión (CA 2d)

En la UD1 (apartado 4.3, nota histórica) ya adelantamos que a finales de los 90 se creó **XHTML**: una reformulación de HTML obligada a cumplir las mismas reglas de "buen formado" que vimos para XML. Hoy es prácticamente teoría sin caso práctico real — quedó en desuso hace años y ningún proyecto nuevo lo usa —, pero es el ejemplo más claro para ver qué significa que un HTML se pueda procesar con las mismas garantías que un XML: interesa cuando una aplicación necesita extraer datos automáticamente de páginas web sin sorpresas de etiquetas mal cerradas a mitad de proceso, el mismo razonamiento que sustenta lo que veréis en las UD 8 y 9 (esquemas y conversión de documentos).

| Regla | HTML (permisivo) | XHTML (estricto, como XML) |
|---|---|---|
| Cierre de etiquetas | `<li>Café` (se puede dejar sin cerrar) | `<li>Café</li>` — cierre obligatorio, como en la UD1 |
| Elementos vacíos | `<br>`, `<img src="foto.jpg">` | `<br/>`, `<img src="foto.jpg"/>` — autocierre obligatorio |
| Mayúsculas/minúsculas | `<P>`, `<p>`, `<DIV>` son equivalentes | Todo en minúsculas: `<p>`, `<div>` — recordad, XML distingue mayúsculas de minúsculas |
| Atributos | `<input disabled>`, `<td width=100>` se toleran | `<input disabled="disabled"/>`, `<td width="100">` — valor explícito y comillas obligatorias, igual que en XML |

En otras palabras: **todo documento XHTML es también un documento XML bien formado** (las 6 reglas de la UD1, apartado 4.3) — por eso se puede abrir directamente con un analizador XML, algo que un HTML corriente, al permitir errores, no garantiza. Ejemplo de conversión:

```html
<!-- HTML -->
<img src="logo.png">
<input type="checkbox" checked>
<P>Texto en mayúsculas de etiqueta</P>

<!-- XHTML -->
<img src="logo.png" alt="Logo" />
<input type="checkbox" checked="checked" />
<p>Texto en mayúsculas de etiqueta</p>
```

**🧪 Ejercicio 3 — Aplica las diferencias**

Sobre 3-4 líneas de tu `ficha-alumno.html` (no hace falta convertir todo el documento), aplica las diferencias de la tabla anterior: busca un elemento vacío (por ejemplo `<img>`) y ciérralo con autocierre (`/>`), y revisa que no te quede ninguna etiqueta en mayúsculas ni ningún atributo sin comillas.

---

## 5. Formularios básicos: elementos y tipos de campo

Esto es solo el vocabulario básico de formularios — no hace falta dominarlo todavía, lo ampliaremos con validación y envío de datos en la **UD3**.

Un formulario recoge datos del usuario para enviarlos a algún sitio (un servidor, por ejemplo):

```html
<form>
  <label for="nombre">Nombre:</label>
  <input type="text" id="nombre" name="nombre"><br>

  <label for="email">Correo:</label>
  <input type="email" id="email" name="email"><br>

  <label for="edad">Edad:</label>
  <input type="number" id="edad" name="edad"><br>

  <input type="checkbox" id="acepto" name="acepto">
  <label for="acepto">Acepto las condiciones</label><br>

  <input type="submit" value="Enviar">
</form>
```

- **`<form>`**: envuelve todo el formulario.
- **`<label for="...">`**: asocia un texto a un campo por su `id` — importante para accesibilidad (un lector de pantalla anuncia la etiqueta al enfocar el campo) y para que al hacer clic en el texto se active el campo.
- **`<input>`**: el campo en sí; el atributo `type` decide qué se puede escribir: `text` (texto libre), `email`, `number`, `checkbox` (casilla), `radio` (opción única entre varias) — HTML5 valida el formato básico de algunos tipos automáticamente, pero de eso hablaremos con detalle en la UD3.
- **`name`**: el identificador con el que viajará el dato al enviarse — no lo desarrollaremos hasta que veáis el envío de datos en la UD3.

**🧪 Ejercicio 4 — Formulario de inscripción**

Crea `inscripcion.html` con un formulario que recoja: nombre (texto), correo (email), edad (número), módulo preferido (elige entre `radio` con 2-3 opciones), y un botón de envío. Cada campo debe tener su `<label>` correctamente asociado con `for`/`id`.

---

## Resumen de la unidad

**1. HTML en el panorama de la Web** *(CA 2a)* HTML es una aplicación de SGML con vocabulario fijo, pensada específicamente para la Web, junto a XHTML, CSS y SVG. Evolución: de HTML 2-4.01 (versiones cerradas) a XHTML (sintaxis estricta) a HTML5 y, desde 2019, al Living Standard del WHATWG — sin versiones cerradas.

**2. Estructura de un documento HTML** *(CA 2b)* `<!DOCTYPE html>`, `<html>` como raíz única, `<head>` (metainformación) y `<body>` (contenido visible) — el esqueleto que tendrá todo documento HTML que escribáis.

**3. Etiquetas y atributos principales** *(CA 2c)* Listas (`<ul>`/`<ol>`/`<li>`), enlaces (`<a href>`), tablas (`<table>`/`<tr>`/`<th>`/`<td>`), imágenes (`<img src alt>`) y contenedores genéricos (`<div>`/`<span>`) con sus atributos comunes (`id`, `class`, `title`) — todo construido sobre una única página, `index.html`, que fuisteis ampliando bloque a bloque.

**4. XHTML** *(CA 2d)* Reformulación de HTML con sintaxis XML estricta: cierre obligatorio, minúsculas, comillas, autocierre. Su valor real está en garantizar documentos procesables de forma fiable con herramientas XML en sistemas de gestión de información — no en su uso real en producción, que es prácticamente nulo hoy.

**5. Formularios básicos** *(adelanto de UD3)* `<form>`, `<label for>`, `<input type="...">` — vocabulario mínimo; la validación y el envío de datos se tratan en la UD3.

---

## 📚 Para saber más (opcional, no evaluable)

### ¿Para qué te va a servir el HTML de esta unidad?

Lo que habéis visto aquí (estructura, etiquetas, atributos) es la base mínima con la que se escribe cualquier página web — la profundización real llega a partir de la **UD3** (formularios avanzados y validación), **UD4-5** (hojas de estilo, CSS) y **UD6** (manipulación de documentos web con JavaScript). No hace falta dominarlo todo ya: de momento basta con reconocer la estructura de un HTML y ser capaz de escribir uno correcto vosotros mismos.

A fecha de este curso (2026-2027), conviene saber que el ecosistema alrededor de HTML sigue cambiando activamente en varios frentes:

- **Accesibilidad, cada vez más exigida por ley**: la normativa europea de accesibilidad digital (Directiva (UE) 2019/882, trasladada a España por el Real Decreto 1112/2018 y su desarrollo posterior) obliga a que buena parte de las webs de administraciones y empresas cumplan criterios **WCAG**. El `alt` de las imágenes que habéis usado en el punto 3.3, o el `<label for>` de los formularios del punto 5, no son un capricho — son exactamente el tipo de detalle que se audita.
- **Elementos semánticos**: HTML5 incorporó etiquetas como `<header>`, `<nav>`, `<main>`, `<article>` o `<footer>`, que describen el significado de cada bloque en vez de usar siempre `<div>`. No las hemos usado todavía (las veréis con más detalle al trabajar con CSS en la UD4-5), pero son la forma recomendada hoy de estructurar una página real.
- **Los tres motores de navegador**: prácticamente todo lo que veis en pantalla lo renderiza uno de tres motores — Blink (Chrome, Edge, Opera y la mayoría de navegadores basados en Chromium), WebKit (Safari) o Gecko (Firefox, el que usáis en el aula). Cuando una página se ve distinta según el navegador, casi siempre es una diferencia entre estos tres motores interpretando el mismo HTML.

### ¿Y el XHTML del punto 4?

Si te preguntas por qué dedicamos un punto entero a algo "que ya no se usa": no es que estéis perdiendo el tiempo, es que sigue siendo el ejemplo más claro para entender qué significa que un documento sea procesable de forma fiable — el mismo razonamiento que vais a necesitar en la UD7 (validación de documentos), solo que allí se aplica directamente sobre HTML y XML, sin pasar por XHTML como paso intermedio.

- MDN Web Docs — Referencia HTML: https://developer.mozilla.org/es/docs/Web/HTML
- HTML Living Standard (WHATWG): https://html.spec.whatwg.org/
- W3C — Recomendación XHTML 1.0: https://www.w3.org/TR/xhtml1/
