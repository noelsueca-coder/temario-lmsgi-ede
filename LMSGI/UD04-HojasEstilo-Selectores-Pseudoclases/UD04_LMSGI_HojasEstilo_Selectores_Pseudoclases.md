<div style="text-align: center;">

<img src="data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCA0MDAgNDAwIiB3aWR0aD0iMTgwIiBoZWlnaHQ9IjE4MCI+CiAgPGNpcmNsZSBjeD0iMjAwIiBjeT0iMjAwIiByPSIxNzAiIGZpbGw9IiNGMEZERkEiLz4KICA8Y2lyY2xlIGN4PSIyMDAiIGN5PSIyMDAiIHI9IjE3MCIgZmlsbD0ibm9uZSIgc3Ryb2tlPSIjOTlGNkU0IiBzdHJva2Utd2lkdGg9IjIiLz4KICA8cmVjdCB4PSIxMDAiIHk9IjExMCIgd2lkdGg9IjkwIiBoZWlnaHQ9IjkwIiByeD0iOCIgZmlsbD0ibm9uZSIgc3Ryb2tlPSIjMEY3NjZFIiBzdHJva2Utd2lkdGg9IjEwIi8+CiAgPGNpcmNsZSBjeD0iMTQ1IiBjeT0iMTU1IiByPSI0NSIgZmlsbD0ibm9uZSIgc3Ryb2tlPSIjMEY3NjZFIiBzdHJva2Utd2lkdGg9IjEwIiBvcGFjaXR5PSIwLjQiLz4KICA8cmVjdCB4PSIyMTAiIHk9IjIwMCIgd2lkdGg9IjkwIiBoZWlnaHQ9IjkwIiByeD0iOCIgZmlsbD0iIzBGNzY2RSIgb3BhY2l0eT0iMC4xNSIvPgogIDxyZWN0IHg9IjIxMCIgeT0iMjAwIiB3aWR0aD0iOTAiIGhlaWdodD0iOTAiIHJ4PSI4IiBmaWxsPSJub25lIiBzdHJva2U9IiMwRjc2NkUiIHN0cm9rZS13aWR0aD0iMTAiLz4KICA8bGluZSB4MT0iMTgwIiB5MT0iMTcwIiB4Mj0iMjQwIiB5Mj0iMjMwIiBzdHJva2U9IiMwRjc2NkUiIHN0cm9rZS13aWR0aD0iNiIgc3Ryb2tlLWRhc2hhcnJheT0iMTAgOCIvPgo8L3N2Zz4K" width="180" alt="Logo LMSGI"/>

<h1>Unidad 4</h1>
<h2>Hojas de estilo. Selectores. Pseudoclases</h2>

<p>
<strong>Módulo:</strong> Lenguajes de Marcas y Sistemas de Gestión de Información (LMSGI)<br>
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

1. Separar contenido y presentación: qué es CSS
2. Vincular CSS a un HTML: en línea, interno y externo
3. Sintaxis básica: reglas, propiedades y valores
4. Selectores básicos: universal, tipo, clase, id
5. Combinación de selectores
6. Selectores de atributo
7. Pseudoclases y pseudoelementos
8. CSS dinámico: variables personalizadas
9. Resumen de la unidad
10. Para saber más

<div style="page-break-after: always;"></div>

**RA cubierto:** RA2 — *Utiliza lenguajes de marcas para la transmisión y presentación de información a través de la web, analizando la estructura de los documentos e identificando sus elementos*

⚠️ **Nota de alineación curricular**: esta unidad cubre un único bloque de contenido de la programación (hojas de estilo: aspectos básicos, propiedades, CSS dinámico, selectores, combinación de selectores, clases, atributos, pseudoclases/pseudoelementos), pero el código de CA con el que se identifica ese bloque **no es el mismo en ambos ciclos**: en **ASIX (RD 1629/2009)** es **CA 2g-2h**, y en **DAW (RD 405/2023)** es **CA 2f-2g**. Como la programación no desglosa ese bloque punto a punto, esta unidad no reparte CA por apartado — toda ella queda cubierta bajo el CA correspondiente a cada ciclo, indicado aquí una sola vez.

> 💡 **Nota de estudio**: en la UD1 y la UD2 ya viste que la independencia y la separación entre contenido y presentación son ventajas de los lenguajes de marcas. Esta unidad es donde esa idea se vuelve concreta: **CSS** es la herramienta que hace posible esa separación en la práctica. Todo lo que aprendas aquí se apoya directamente en el HTML que ya sabes escribir.

---

## 1. Separar contenido y presentación: qué es CSS

Hasta ahora, la única forma que has tenido de cambiar el aspecto de un HTML ha sido con el atributo `style` (algún ejemplo suelto en unidades anteriores) o dejando que el navegador aplique su estilo por defecto (`<h1>` grande, `<p>` normal...). Eso funciona, pero mezcla dos cosas que conviene mantener separadas: **qué es** el contenido (HTML) y **cómo se ve** (presentación).

**CSS** (*Cascading Style Sheets*, "hojas de estilo en cascada") es el lenguaje que resuelve esto: describe el aspecto visual de un documento marcado, sin tocar su contenido. Es un lenguaje declarativo, no un lenguaje de marcas — no tiene etiquetas `<...>`, sino **reglas** que dicen "a este elemento, aplícale este aspecto".

> 🕰️ **Por qué existe**: en los primeros años de la web (mediados de los 90), el único modo de dar color o tamaño a un texto era metiendo esa información dentro del propio HTML, etiqueta a etiqueta (`<font color="red" size="5">`). Si querías cambiar el color de todos los títulos de una web de 200 páginas, tenías que editar las 200 páginas una a una. El W3C publicó CSS en 1996 precisamente para separar ambas cosas: el HTML describe la estructura, CSS describe el aspecto, y cambiar un color de toda la web pasa a ser una única línea.

**Por qué importa separar esto, con un caso muy real:**

- Un único archivo CSS puede aplicarse a **decenas de páginas HTML** a la vez — cambias un color en un sitio y se actualiza en todo el sitio web.
- Un mismo HTML puede verse distinto según el dispositivo (móvil, ordenador, impresora) sin tocar el contenido — solo cambiando qué CSS se aplica.
- El HTML queda más limpio y fácil de mantener — sin atributos `style` repetidos por todas partes.

**🧪 Ejercicio 1 — Antes y después**
Escribe en Mousepad un HTML sencillo (un `<h1>`, dos `<p>` y una `<ul>` con 3 elementos) usando el atributo `style` para poner colores y tamaños directamente en cada etiqueta, como se hacía antes de CSS. Cuenta cuántas veces repites la palabra `style`. Guarda el archivo como `antes.html` — lo vamos a reescribir con CSS de verdad en el Ejercicio 2, para comparar.

---

## 2. Vincular CSS a un HTML: en línea, interno y externo

Hay tres formas de aplicar CSS a un documento, y no son intercambiables — cada una tiene su uso:

| Forma | Cómo se escribe | Cuándo se usa |
|---|---|---|
| **En línea** (*inline*) | Atributo `style` dentro de la propia etiqueta | Casi nunca en código real — solo pruebas rápidas o estilos generados dinámicamente por JavaScript |
| **Interno** | Bloque `<style>` dentro del `<head>` del HTML | Una página aislada, sin más páginas que compartan estilo |
| **Externo** | Archivo `.css` aparte, enlazado con `<link>` | La forma normal de trabajar — el mismo archivo `.css` sirve para todas las páginas del sitio |

**En línea** (la que evitamos a partir de ahora):
```html
<h1 style="color: teal; font-size: 32px;">Título</h1>
```

**Interno**:
```html
<head>
  <style>
    h1 {
      color: teal;
      font-size: 32px;
    }
  </style>
</head>
```

**Externo** — el que vas a usar en el resto de la unidad y del módulo:

```html
<!-- index.html -->
<head>
  <link rel="stylesheet" href="estilos.css">
</head>
```
```css
/* estilos.css */
h1 {
  color: teal;
  font-size: 32px;
}
```

⚠️ **Ruta del `href`**: es relativa a dónde está el HTML, igual que las rutas de imágenes que ya conoces. Si `estilos.css` está en la misma carpeta que `index.html`, basta con el nombre del archivo; si está en una subcarpeta `css/`, sería `href="css/estilos.css"`.

**🧪 Ejercicio 2 — De `style` a archivo externo**
Reescribe el `antes.html` del Ejercicio 1 en dos archivos: `index.html` (solo estructura, sin ningún atributo `style`) y `estilos.css` (todas las reglas de color y tamaño que antes estaban repetidas). Enlázalos con `<link>` y ábrelo con Firefox — debe verse exactamente igual que `antes.html`. Cuenta ahora cuántas veces aparece la palabra `style` en `index.html`.

---

## 3. Sintaxis básica: reglas, propiedades y valores

Una regla CSS tiene siempre la misma forma:

```css
selector {
  propiedad: valor;
  propiedad: valor;
}
```

```css
p {
  color: #1e293b;
  font-size: 16px;
  line-height: 1.5;
}
```

- **Selector** (`p`): a qué elemento o elementos se aplica la regla — lo vemos en detalle en los puntos 4-6.
- **Declaración** (`color: #1e293b;`): una pareja `propiedad: valor;`, siempre terminada en punto y coma.
- **Bloque de declaraciones** (todo lo que va entre `{` y `}`): el conjunto de declaraciones que se aplican a ese selector.

**Algunas propiedades habituales, para tener referencia desde ya:**

| Propiedad | Para qué sirve | Ejemplo de valor |
|---|---|---|
| `color` | Color del texto | `red`, `#ff0000`, `rgb(255, 0, 0)` |
| `background-color` | Color de fondo | `#f0fdfa` |
| `font-size` | Tamaño de letra | `16px`, `1.2em`, `1rem` |
| `font-weight` | Grosor de la letra | `normal`, `bold`, `700` |
| `text-align` | Alineación del texto | `left`, `center`, `right` |
| `margin` | Espacio fuera del elemento | `10px`, `10px 20px` |
| `padding` | Espacio dentro del elemento, antes del borde | `10px` |
| `border` | Borde del elemento | `1px solid #ccc` |

> 💡 **Los comentarios en CSS** se escriben `/* así */`, nunca con `//` ni con `<!-- -->` (eso es HTML/XML, no CSS — cada lenguaje tiene su propia sintaxis de comentario, como ya viste en la UD1).

**El nombre "cascada" no es casualidad.** Cuando varias reglas afectan al mismo elemento, CSS decide cuál gana siguiendo un orden de prioridad: primero la **especificidad** del selector (un id pesa más que una clase, y una clase pesa más que una etiqueta — lo verás con las clases y los id en el punto 4), y si hay empate, gana la **regla que aparece más abajo** en el archivo. Por eso el orden en que escribes las reglas dentro de un `.css` sí importa cuando hay conflicto.

**🧪 Ejercicio 3 — Encuentra el ganador**
Dado este CSS:
```css
p { color: blue; }
p { color: green; }
.aviso { color: red; }
```
y este HTML: `<p class="aviso">Texto de prueba</p>`, ¿de qué color se verá el texto? Razona tu respuesta aplicando lo que acabas de leer sobre la cascada (sin usar aún el concepto de "clase" del punto 4 — de momento fíate de que `.aviso` selecciona ese párrafo).

---

## 4. Selectores básicos: universal, tipo, clase, id

El **selector** decide a qué parte del HTML se aplica una regla. Estos cuatro son la base de todo lo demás:

| Selector | Sintaxis | Selecciona | Especificidad |
|---|---|---|---|
| **Universal** | `*` | Todos los elementos del documento | La más baja |
| **De tipo** (o de etiqueta) | `p`, `h1`, `li` | Todos los elementos de esa etiqueta | Baja |
| **De clase** | `.nombre-clase` | Todos los elementos con `class="nombre-clase"` | Media |
| **De id** | `#nombre-id` | El único elemento con `id="nombre-id"` | Alta |

```html
<p class="destacado">Este párrafo tiene una clase.</p>
<p id="intro">Este párrafo tiene un id.</p>
```
```css
* {
  margin: 0;
  box-sizing: border-box;
}

p {
  line-height: 1.5;
}

.destacado {
  background-color: #fef3c7;
  font-weight: bold;
}

#intro {
  font-size: 20px;
}
```

⚠️ **Clase vs. id, la diferencia que importa**: un `id` debe ser **único** en todo el documento (no puede haber dos elementos con el mismo id); una `class` se puede repetir en tantos elementos como quieras, y un mismo elemento puede tener varias clases a la vez separadas por espacios: `class="destacado urgente"`.

> 📡 **Sigue vigente**: en la práctica moderna, las clases son con diferencia el selector más usado para dar estilo — el id se reserva casi siempre para otras cosas, como ser el destino de un enlace interno (`<a href="#intro">`) o ser localizado por JavaScript (`document.getElementById(...)`, lo verás en la UD6), no tanto para aplicar estilo directamente.

**🧪 Ejercicio 4 — Estilo para un panel de estado**
Crea un HTML con 4 elementos `<p>`: dos con `class="ok"`, uno con `class="alerta"`, y uno de ellos además con `id="principal"`. Escribe el CSS para que: todos los `<p>` tengan `padding: 8px` (selector de tipo), los de clase `ok` tengan fondo verde claro, el de clase `alerta` tenga fondo rojo claro, y el que tiene `id="principal"` tenga además el texto en negrita, sea de la clase que sea. Compruébalo en el navegador y explica qué regla gana en el elemento que tiene tanto `id="principal"` como una clase de color, y por qué.

---

## 5. Combinación de selectores

Los selectores básicos se pueden combinar para apuntar con más precisión, sin tener que añadir una clase a cada elemento:

| Combinador | Sintaxis | Selecciona |
|---|---|---|
| **Descendiente** | `article p` | Todos los `<p>` dentro de un `<article>`, a cualquier profundidad |
| **Hijo directo** | `article > p` | Solo los `<p>` que son hijos **directos** de un `<article>`, no los que están más anidados |
| **Hermano adyacente** | `h2 + p` | El `<p>` que va **justo después** de un `<h2>` |
| **Agrupación** | `h1, h2, h3` | Aplica la misma regla a varios selectores a la vez, evitando repetir el bloque |

```html
<article>
  <h2>Título</h2>
  <p>Primer párrafo, justo después del título.</p>
  <div>
    <p>Párrafo anidado dentro de un div.</p>
  </div>
</article>
```
```css
article p {
  color: #334155;
}

article > p {
  font-weight: bold;
}

h2 + p {
  font-style: italic;
}
```

Con este CSS: **ambos** `<p>` reciben el color gris oscuro (son descendientes de `article`, a cualquier nivel); solo el primer `<p>` recibe negrita (es hijo directo de `article`, el segundo está dentro de un `<div>` de por medio); y solo el primer `<p>` recibe además cursiva (es justo el siguiente elemento después del `<h2>`).

**🧪 Ejercicio 5 — Diferencia entre descendiente e hijo directo**
Parte del HTML de arriba y añade un segundo `<div>` con otro `<p>` dentro, anidado dos niveles (un `<div>` dentro de otro `<div>`, y el `<p>` dentro del más interno). Sin cambiar el CSS del ejemplo, predice por escrito qué reglas afectarán a este nuevo párrafo y cuáles no, y después compruébalo en el navegador.

---

## 6. Selectores de atributo

Permiten seleccionar elementos según los atributos que tengan, sin necesidad de una clase específica para ello — muy útil, por ejemplo, con formularios (los verás en detalle en la UD3, pero ya puedes empezar a darles estilo).

| Selector | Selecciona elementos que... |
|---|---|
| `[atributo]` | ...tienen ese atributo, sea cual sea su valor |
| `[atributo="valor"]` | ...tienen ese atributo con exactamente ese valor |
| `[atributo^="valor"]` | ...tienen ese atributo y su valor **empieza** por ese texto |
| `[atributo$="valor"]` | ...tienen ese atributo y su valor **termina** por ese texto |

```html
<input type="text" placeholder="Nombre">
<input type="email" placeholder="Correo">
<a href="https://ejemplo.com">Enlace externo</a>
<a href="/inicio">Enlace interno</a>
```
```css
[type="email"] {
  border-color: teal;
}

a[href^="https://"] {
  color: darkred;
}
```

Aquí el `<input>` de tipo `email` recibe un borde distinto, y solo el enlace que empieza por `https://` (el externo) recibe un color distinto — muy práctico para avisar visualmente de qué enlaces salen del sitio, sin tener que etiquetar cada uno a mano con una clase.

**🧪 Ejercicio 6 — Estilo por atributo**
Crea un formulario sencillo con tres `<input>`: uno `type="text"`, uno `type="email"` y uno `type="password"`. Con selectores de atributo (sin usar ninguna clase), dale a cada tipo un color de borde distinto.

---

## 7. Pseudoclases y pseudoelementos

Hasta ahora todos los selectores apuntan a elementos que ya están en el HTML tal cual. Las **pseudoclases** y los **pseudoelementos** van un paso más allá: seleccionan un elemento en un **estado concreto**, o una **parte** de un elemento que no tiene su propia etiqueta.

**Pseudoclases** (se escriben con `:`) — seleccionan un elemento según su estado o su posición:

| Pseudoclase | Selecciona |
|---|---|
| `:hover` | El elemento mientras el ratón está encima |
| `:focus` | El elemento mientras tiene el foco (por ejemplo, un `<input>` en el que estás escribiendo) |
| `:first-child` | El elemento que es el primer hijo de su padre |
| `:last-child` | El elemento que es el último hijo de su padre |
| `:nth-child(n)` | El elemento que ocupa la posición `n` entre sus hermanos |

**Pseudoelementos** (se escriben con `::`) — seleccionan una parte de un elemento que no existe como etiqueta propia:

| Pseudoelemento | Selecciona |
|---|---|
| `::first-letter` | La primera letra del contenido del elemento |
| `::before` | Permite insertar contenido generado justo antes del contenido del elemento |
| `::after` | Permite insertar contenido generado justo después del contenido del elemento |

```css
button {
  background-color: teal;
  color: white;
  border: none;
  padding: 8px 16px;
}

button:hover {
  background-color: #0f766e;
}

input:focus {
  border-color: teal;
  outline: none;
}

li:first-child {
  font-weight: bold;
}

p::first-letter {
  font-size: 200%;
}
```

⚠️ **Un solo `:` frente a dos `::`** no es un capricho de sintaxis: `:hover` es un *estado* del elemento (una pseudoclase), mientras que `::first-letter` es una *parte* generada del elemento (un pseudoelemento) que no puedes seleccionar de ninguna otra forma, porque no existe una etiqueta `<primera-letra>` en el HTML. Los navegadores actuales toleran `:before`/`:after` con un solo `:` por compatibilidad histórica, pero la sintaxis correcta y la que debes usar es con dos.

**🧪 Ejercicio 7 — Un botón que reacciona**
Crea un botón (`<button>`) con un estilo base (fondo de color, texto blanco, sin borde), y añade una regla `:hover` que cambie el fondo a un tono más oscuro, y una regla `:focus` que le añada un borde visible. Después, aplica `:first-child` a una lista `<ul>` de al menos 4 elementos para que el primero se vea distinto a los demás (por ejemplo, en negrita).

---

## 8. CSS dinámico: variables personalizadas

Cuando un mismo color o medida se repite muchas veces por todo un archivo CSS (el color corporativo de una web, el mismo radio de borde en todas las tarjetas...), cambiarlo a mano implica editar cada aparición una por una. Las **variables CSS** (formalmente, *custom properties*) resuelven esto: se declaran una vez y se reutilizan donde haga falta.

```css
:root {
  --color-principal: #0f766e;
  --color-fondo: #f0fdfa;
  --radio-borde: 8px;
}

.tarjeta {
  background-color: var(--color-fondo);
  border: 2px solid var(--color-principal);
  border-radius: var(--radio-borde);
  padding: 16px;
}

.boton {
  background-color: var(--color-principal);
  border-radius: var(--radio-borde);
}
```

- `:root` es un selector especial que apunta al elemento raíz del documento (equivalente, a efectos prácticos, a `<html>`) — es el lugar habitual donde declarar variables que quieres que estén disponibles en todo el archivo.
- Toda variable personalizada empieza por `--` (dos guiones).
- Se usa con la función `var(--nombre-variable)`, en cualquier declaración donde encajaría ese valor.

**Por qué se llama "dinámico"**: a diferencia de un valor fijo (`color: #0f766e;` repetido 20 veces), una variable se puede **cambiar en un único sitio** y todo lo que la usa se actualiza a la vez — cambia `--color-principal` en `:root` y todas las tarjetas y botones del ejemplo cambian de color sin tocar sus propias reglas. Es además la base técnica que hace posible, por ejemplo, un selector de tema claro/oscuro cambiando el valor de las variables según una clase en `<html>`.

> 📡 **Por qué importa hoy**: es exactamente el mecanismo que usarías para el color corporativo de un dashboard de finanzas personales que definimos una vez y reutilizamos en cada tarjeta de gasto, cada botón y cada gráfico — cambiar de marca o de tema visual se convierte en cambiar unas pocas líneas en `:root`, en vez de perseguir el mismo color por todo el archivo.

**🧪 Ejercicio 8 — Tema con variables**
Retoma el botón y las tarjetas de los ejercicios anteriores y sustituye todos los colores repetidos por variables declaradas en `:root` (al menos un color principal, un color de fondo y un radio de borde). Después, cambia solo el valor de las variables en `:root` y comprueba que el aspecto de todos los elementos cambia a la vez, sin tocar ninguna otra regla.

---

## 🎯 Reto de clase

Retoma cualquier HTML que hayas escrito en unidades anteriores (por ejemplo, el feed de podcast de la UD1, o un formulario de la UD3) y dale estilo completo con un archivo `estilos.css` externo, usando **al menos**: dos selectores de tipo, un selector de clase, un selector de id, un combinador (descendiente o hijo directo), una pseudoclase (`:hover` o `:focus`) y dos variables CSS personalizadas en `:root`. Nada de atributos `style` en el HTML.

*Variación evaluable*: pedir además que expliquen, para tres de las reglas que han escrito, qué especificidad tiene cada selector y por qué, si hubiera un conflicto entre dos de sus propias reglas, ganaría una sobre la otra.

---

<div style="page-break-after: always;"></div>

## Resumen de la unidad

**1. Separar contenido y presentación** CSS es el lenguaje declarativo que describe el aspecto visual de un documento marcado, separado de su contenido — nació en 1996 para evitar repetir el estilo etiqueta a etiqueta por todo un sitio.

**2. Vincular CSS a un HTML** Tres formas: en línea (atributo `style`, casi nunca se usa), interno (`<style>` en el `<head>`) y externo (archivo `.css` enlazado con `<link>`) — la forma normal de trabajar, porque un mismo archivo sirve para todas las páginas de un sitio.

**3. Sintaxis básica** Una regla es `selector { propiedad: valor; }`. Cuando varias reglas afectan al mismo elemento, gana la de mayor especificidad y, en empate, la que aparece más abajo en el archivo — el origen del nombre "cascada".

**4. Selectores básicos** Universal (`*`), de tipo (`p`), de clase (`.nombre`, reutilizable) y de id (`#nombre`, único en el documento) — con especificidad creciente en ese mismo orden.

**5. Combinación de selectores** Descendiente (`article p`), hijo directo (`article > p`), hermano adyacente (`h2 + p`) y agrupación (`h1, h2, h3`) para apuntar con precisión sin añadir clases a cada elemento.

**6. Selectores de atributo** `[atributo]`, `[atributo="valor"]`, `[atributo^="valor"]`, `[atributo$="valor"]` — muy útiles para dar estilo a formularios según el tipo de campo.

**7. Pseudoclases y pseudoelementos** Las pseudoclases (`:hover`, `:focus`, `:first-child`) seleccionan un estado o una posición; los pseudoelementos (`::first-letter`, `::before`, `::after`) seleccionan una parte generada del elemento que no tiene etiqueta propia.

**8. CSS dinámico: variables personalizadas** Declaradas en `:root` con `--nombre` y usadas con `var(--nombre)`, permiten cambiar un valor repetido por todo un archivo modificando una única línea.

---

## 📚 Para saber más (opcional, no evaluable)

Lo visto aquí es la base de selección y sintaxis de CSS — la UD5 profundiza en **layout** (Flex, Grid), **CSS responsive** y en el framework **Bootstrap**, que reutiliza exactamente estos mismos conceptos de selector, especificidad y cascada a mayor escala.

> 📡 **Actualidad**: las variables CSS (punto 8) llevan siendo compatibles en todos los navegadores modernos desde 2017 y hoy son la forma estándar de gestionar temas de color (claro/oscuro) sin necesidad de JavaScript ni de un preprocesador como Sass — algo que hace unos años sí hacía falta.

- Referencia completa de propiedades CSS (MDN): https://developer.mozilla.org/es/docs/Web/CSS/Reference
- Especificidad CSS explicada visualmente: https://developer.mozilla.org/es/docs/Web/CSS/Specificity
