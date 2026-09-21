<div style="text-align: center;">

<img src="data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCA0MDAgNDAwIiB3aWR0aD0iMTgwIiBoZWlnaHQ9IjE4MCI+CiAgPGNpcmNsZSBjeD0iMjAwIiBjeT0iMjAwIiByPSIxNzAiIGZpbGw9IiNGMEZERkEiLz4KICA8Y2lyY2xlIGN4PSIyMDAiIGN5PSIyMDAiIHI9IjE3MCIgZmlsbD0ibm9uZSIgc3Ryb2tlPSIjOTlGNkU0IiBzdHJva2Utd2lkdGg9IjIiLz4KICA8cmVjdCB4PSI5MCIgeT0iMTUwIiB3aWR0aD0iOTAiIGhlaWdodD0iMTMwIiByeD0iMTAiIGZpbGw9Im5vbmUiIHN0cm9rZT0iIzBGNzY2RSIgc3Ryb2tlLXdpZHRoPSIxMCIvPgogIDxyZWN0IHg9IjIyMCIgeT0iMTEwIiB3aWR0aD0iOTAiIGhlaWdodD0iMTcwIiByeD0iMTAiIGZpbGw9IiMwRjc2NkUiIG9wYWNpdHk9IjAuMTUiIHN0cm9rZT0iIzBGNzY2RSIgc3Ryb2tlLXdpZHRoPSIxMCIvPgogIDxwYXRoIGQ9Ik0gMTk1IDE3NSBMIDIyNSAxNzUiIHN0cm9rZT0iIzBGNzY2RSIgc3Ryb2tlLXdpZHRoPSI4IiBzdHJva2UtbGluZWNhcD0icm91bmQiLz4KICA8cGF0aCBkPSJNIDIxOCAxNjggTCAyMzAgMTc1IEwgMjE4IDE4MiIgZmlsbD0ibm9uZSIgc3Ryb2tlPSIjMEY3NjZFIiBzdHJva2Utd2lkdGg9IjYiIHN0cm9rZS1saW5lY2FwPSJyb3VuZCIgc3Ryb2tlLWxpbmVqb2luPSJyb3VuZCIvPgogIDxwYXRoIGQ9Ik0gMTk1IDIzNSBMIDIyNSAyMzUiIHN0cm9rZT0iIzBGNzY2RSIgc3Ryb2tlLXdpZHRoPSI4IiBzdHJva2UtbGluZWNhcD0icm91bmQiLz4KICA8cGF0aCBkPSJNIDIxOCAyMjggTCAyMzAgMjM1IEwgMjE4IDI0MiIgZmlsbD0ibm9uZSIgc3Ryb2tlPSIjMEY3NjZFIiBzdHJva2Utd2lkdGg9IjYiIHN0cm9rZS1saW5lY2FwPSJyb3VuZCIgc3Ryb2tlLWxpbmVqb2luPSJyb3VuZCIvPgo8L3N2Zz4K" width="180" alt="Logo LMSGI"/>

<h1>Unidad 5</h1>
<h2>Hojas de estilo II: CSS avanzado</h2>

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

1. Layout con Flexbox
2. Transiciones y transformaciones
3. Layout con Grid
4. Diseño responsive: media queries
5. Frameworks CSS: introducción a Bootstrap
6. El sistema de rejilla de Bootstrap: contenedores y breakpoints
7. Utilidades Flex y Grid de Bootstrap
8. Componentes de Bootstrap: Cards, Carousel, NavBar
9. Resumen de la unidad
10. Para saber más

<div style="page-break-after: always;"></div>

**RA cubierto:** RA2 — *Utiliza lenguajes de marcas para la transmisión y presentación de información a través de la web, analizando la estructura de los documentos e identificando sus elementos*

⚠️ **Nota de alineación curricular**: esta unidad cubre un único bloque de contenido de la programación (layout con Flexbox y Grid, transiciones, diseño responsive, e introducción a Bootstrap: rejilla, utilidades y componentes), pero el código de CA con el que se identifica ese bloque **no es el mismo en ambos ciclos** — y, a diferencia de otras unidades, aquí cada ciclo lo cubre con un único CA, no con un rango: en **ASIX (RD 1629/2009)** es **CA 2f**, y en **DAW (RD 405/2023)** es **CA 2e**. Como la programación no desglosa ese bloque punto a punto, esta unidad no reparte CA por apartado — toda ella queda cubierta bajo el CA correspondiente a cada ciclo, indicado aquí una sola vez.

> 💡 **Nota de estudio**: esta es la unidad más larga del módulo (18 horas) porque reúne dos cosas distintas: primero **Flexbox y Grid**, los dos sistemas de maquetación nativos de CSS con los que se construye cualquier diseño moderno; después **Bootstrap**, un framework que empaqueta esos mismos conceptos en clases ya hechas para ir más rápido. Aprender primero el CSS "de verdad" hace que entiendas *qué* hace Bootstrap por debajo, en vez de copiar clases sin saber por qué funcionan.

---

## 1. Layout con Flexbox

Hasta la UD4 has dado estilo a elementos ya colocados por el flujo normal del HTML (uno debajo de otro). **Flexbox** (*Flexible Box Layout*) es el primer sistema que te deja **controlar la disposición**: alinear elementos en fila o columna, repartir el espacio sobre entre ellos, centrar cosas que antes eran un dolor de cabeza centrar.

Para activar Flexbox, se aplica `display: flex` al elemento **contenedor** — sus hijos directos (los *flex items*) pasan a comportarse según las reglas de Flexbox:

```css
.contenedor {
  display: flex;
}
```

```html
<div class="contenedor">
  <div class="item">1</div>
  <div class="item">2</div>
  <div class="item">3</div>
</div>
```

Sin más CSS que ese `display: flex`, los tres `<div class="item">` ya se colocan en fila, uno junto a otro, en vez de uno debajo de otro como harían por defecto. A partir de ahí, unas pocas propiedades controlan casi todo el resto:

| Propiedad | Va en... | Qué controla |
|---|---|---|
| `flex-direction` | El contenedor | Dirección: `row` (fila, por defecto), `column` (columna) |
| `justify-content` | El contenedor | Reparto en el eje principal: `flex-start`, `center`, `space-between`, `space-around` |
| `align-items` | El contenedor | Alineación en el eje cruzado: `flex-start`, `center`, `stretch` |
| `gap` | El contenedor | Espacio entre los items, sin necesitar márgenes manuales |
| `flex-wrap` | El contenedor | Si los items pasan a la siguiente línea (`wrap`) cuando no caben, o se comprimen (`nowrap`, por defecto) |
| `flex-grow` | Cada item | Cuánto crece ese item para ocupar el espacio sobrante, respecto a sus hermanos |

```css
.barra-navegacion {
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 16px;
  padding: 12px 24px;
}
```

Con esto, una barra de navegación típica (logo a la izquierda, enlaces a la derecha) se resuelve en 4 líneas, sin una sola posición calculada a mano.

> 📡 **Por qué importa hoy**: prácticamente cualquier barra de navegación, fila de tarjetas o formulario alineado horizontalmente que veas en la web actual usa Flexbox por debajo — es, junto con Grid (punto 3), el estándar de maquetación desde hace más de una década, y las técnicas antiguas basadas en `float` que aún encontrarás en tutoriales viejos están en desuso.

**🧪 Ejercicio 1 — Una barra de navegación con Flexbox**
Crea un HTML con una barra (`<nav>`) que contenga un logo (un `<span>` o `<img>`) a la izquierda y tres enlaces (`<a>`) a la derecha, todos en la misma línea y separados uniformemente. Usa `display: flex`, `justify-content` y `gap`. Después, cambia `flex-direction` a `column` y observa qué pasa con `justify-content` — ¿sigue repartiendo en horizontal o ha cambiado de eje?

**🧪 Ejercicio 2 — Tarjetas con `flex-grow`**
Crea tres `<div class="tarjeta">` dentro de un contenedor `display: flex`. Dale a la primera tarjeta `flex-grow: 2` y a las otras dos `flex-grow: 1`. Observa cómo se reparte el espacio disponible y explica con tus palabras qué representa ese número.

---

## 2. Transiciones y transformaciones

Ya viste en la UD4 que una pseudoclase como `:hover` cambia el estilo de un elemento al instante. Con **transiciones**, ese cambio deja de ser instantáneo y pasa a ser una animación suave — sin necesitar ni una línea de JavaScript.

```css
.boton {
  background-color: teal;
  transform: scale(1);
  transition: background-color 0.3s ease, transform 0.3s ease;
}

.boton:hover {
  background-color: #0f766e;
  transform: scale(1.05);
}
```

- **`transition`**: indica qué propiedades animar (`background-color`, `transform`), durante cuánto tiempo (`0.3s`) y con qué ritmo (`ease`: empieza y termina más lento que en el medio). Va en el estado **inicial** del elemento, no en el `:hover`.
- **`transform`**: cambia la apariencia geométrica del elemento sin afectar al resto de la página (a diferencia de cambiar `width` o `margin`, que sí desplaza a los elementos vecinos). Las funciones más habituales:

| Función | Qué hace | Ejemplo |
|---|---|---|
| `scale(n)` | Escala el tamaño | `scale(1.1)` → 10% más grande |
| `rotate(deg)` | Rota el elemento | `rotate(5deg)` |
| `translateX(px)` / `translateY(px)` | Desplaza el elemento, sin afectar al flujo del resto de la página | `translateY(-4px)` |

```css
.tarjeta {
  transition: transform 0.2s ease, box-shadow 0.2s ease;
}

.tarjeta:hover {
  transform: translateY(-4px);
  box-shadow: 0 8px 16px rgba(0, 0, 0, 0.15);
}
```

Este patrón (tarjeta que "se levanta" ligeramente al pasar el ratón) es uno de los más usados en interfaces modernas — parece sofisticado, pero son solo 4 líneas de CSS.

> 📡 **Sigue vigente**: `transition` cubre el 90% de los casos de "algo cambia suavemente al interactuar". Para animaciones más complejas (que se repiten solas, con varios pasos) existe `@keyframes` y la propiedad `animation` — no entra en esta unidad, pero conviene saber que existe si algún día necesitas algo más elaborado que una transición simple.

**🧪 Ejercicio 3 — Botón con transición**
Retoma el botón del Ejercicio 7 de la UD4 (el que cambiaba de color con `:hover`) y añádele una `transition` para que el cambio de color sea suave (0.3 segundos) en vez de instantáneo. Añade además un `transform: scale(1.05)` en el `:hover`.

---

## 3. Layout con Grid

Flexbox organiza elementos en **una dimensión** (una fila, o una columna). **CSS Grid** organiza en **dos dimensiones a la vez** (filas y columnas simultáneamente) — es el sistema adecuado cuando piensas el diseño como una rejilla completa, no como una simple fila de elementos.

```css
.rejilla {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 16px;
}
```

```html
<div class="rejilla">
  <div class="celda">1</div>
  <div class="celda">2</div>
  <div class="celda">3</div>
  <div class="celda">4</div>
</div>
```

- `display: grid` activa la rejilla en el contenedor.
- `grid-template-columns: repeat(3, 1fr)` crea 3 columnas de igual ancho (`1fr` = una "fracción" del espacio disponible — 3 columnas de `1fr` se reparten el ancho a partes iguales).
- Los elementos se van colocando automáticamente celda a celda, y al llegar a la cuarta celda (que no cabe en la primera fila de 3 columnas), Grid crea una segunda fila sin que tengas que indicarlo.

**Columnas de ancho distinto y filas responsivas**, sin escribir un solo número fijo:

```css
.panel {
  display: grid;
  grid-template-columns: 200px 1fr;
  grid-template-rows: auto 1fr;
  gap: 16px;
  min-height: 100vh;
}
```

Aquí la primera columna es fija (200px, típico de un menú lateral) y la segunda ocupa todo el resto del ancho (`1fr`) — el patrón exacto de un panel de administración o de un dashboard con menú lateral y contenido principal.

> 💡 **¿Flexbox o Grid?** No compiten entre sí, se complementan: Grid para la estructura general de la página (menú lateral + contenido, cabecera + cuerpo + pie), y Flexbox para organizar elementos dentro de cada una de esas zonas (los botones de una barra, las tarjetas dentro del área de contenido). Es habitual, y correcto, anidar un `display: flex` dentro de una celda de un `display: grid`.

**🧪 Ejercicio 4 — Panel con menú lateral**
Construye un HTML con un `<div class="panel">` que contenga un `<nav>` (menú lateral) y un `<main>` (contenido). Con CSS Grid, haz que el menú ocupe una columna fija de 220px y el contenido ocupe el resto del ancho disponible. Añade dentro del `<main>` una rejilla de tarjetas (`display: grid`, `grid-template-columns: repeat(3, 1fr)`) con 6 tarjetas.

---

## 4. Diseño responsive: media queries

Un diseño **responsive** (adaptable) se ve bien tanto en un móvil como en un ordenador de escritorio, sin necesitar dos webs distintas. La herramienta clave son las **media queries**: bloques de CSS que solo se aplican si se cumple una condición sobre el dispositivo, casi siempre el ancho de la ventana.

```css
.rejilla {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 16px;
}

@media (max-width: 768px) {
  .rejilla {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (max-width: 480px) {
  .rejilla {
    grid-template-columns: 1fr;
  }
}
```

- `@media (max-width: 768px)` significa "aplica este bloque de reglas solo cuando la ventana mide 768 píxeles de ancho o menos".
- Aquí la rejilla pasa de 3 columnas a 2 en tablet, y a 1 sola columna en móvil — el mismo HTML, sin tocarlo, se reorganiza según el espacio disponible.

Los anchos de referencia donde cambia el diseño (768px, 480px...) se llaman **breakpoints**, y conviene pensarlos de "grande a pequeño" (*mobile-first* sería justo al revés: escribir primero el CSS para móvil y usar `min-width` para ir añadiendo columnas a medida que crece la pantalla — es el enfoque que verás en Bootstrap, en el punto 6).

**🧪 Ejercicio 5 — Rejilla responsive**
Retoma la rejilla de tarjetas del Ejercicio 4 y añade dos media queries: una para que pase a 2 columnas por debajo de 768px, y otra para que pase a 1 columna por debajo de 480px. Comprueba el resultado achicando la ventana del navegador poco a poco (o con las herramientas de desarrollador de Firefox, en modo "vista adaptable").

---

## 5. Frameworks CSS: introducción a Bootstrap

> ⚠️ **Hasta aquí, CSS nativo**: los puntos 1-4 (Flexbox, transiciones, Grid, responsive) son CSS puro, el que entiende cualquier navegador sin depender de nada externo. A partir de aquí entra **Bootstrap**, un framework que reutiliza exactamente esos mismos conceptos empaquetados en clases ya hechas. No son piezas nuevas y distintas — es la misma caja de herramientas, envuelta para ir más rápido.

Todo lo visto en los puntos 1-4 (Flexbox, Grid, media queries) es CSS "puro" — funciona en cualquier navegador sin depender de nada externo, y es fundamental entenderlo. Pero escribir desde cero el layout responsive de un proyecto grande, botón a botón y tarjeta a tarjeta, es lento y repetitivo. Un **framework CSS** resuelve esto ofreciendo un conjunto de clases ya hechas, probadas y coherentes entre sí, para no reinventar cada componente desde cero.

**Bootstrap** es el framework CSS más extendido — creado originalmente en Twitter (2011) para unificar el estilo entre sus propios equipos internos, y liberado después como proyecto de código abierto. En esencia, es exactamente lo que has aprendido en los puntos 1-4 (Flexbox, Grid, media queries, transiciones), pero ya escrito y empaquetado en clases que aplicas directamente en el HTML.

```html
<!-- Sin Bootstrap: tú escribes el CSS -->
<button class="mi-boton">Guardar</button>
<style>
  .mi-boton {
    background-color: #0d6efd;
    color: white;
    padding: 8px 16px;
    border-radius: 4px;
    border: none;
  }
</style>

<!-- Con Bootstrap: la clase ya trae el CSS hecho -->
<button class="btn btn-primary">Guardar</button>
```

⚠️ **Un framework no sustituye lo aprendido, lo aprovecha**: cuando escribes `class="btn btn-primary"`, por debajo hay literalmente reglas CSS con selectores de clase, propiedades y valores — las mismas piezas de la UD4 y de este punto. Saber CSS "de verdad" es lo que te permite, por ejemplo, entender por qué un botón de Bootstrap no se ve como esperabas cuando lo combinas con tu propio CSS, y corregirlo con conocimiento en vez de a prueba y error.

> 📡 **Actualidad**: Bootstrap 5 (la versión que usaremos) eliminó la dependencia de jQuery que tenían las versiones anteriores — hoy funciona con JavaScript nativo del navegador. Sigue siendo, junto con Tailwind CSS (un enfoque distinto, de utilidades más pequeñas), uno de los frameworks CSS más usados en proyectos reales, especialmente para paneles de administración y prototipos rápidos.

---

## 6. El sistema de rejilla de Bootstrap: contenedores y breakpoints

Para usar Bootstrap sin instalar nada, basta con enlazar su CSS (y, para algunos componentes interactivos, su JavaScript) desde un **CDN** (*Content Delivery Network*, una red de servidores que sirve el archivo ya preparado, sin que tengas que descargarlo tú):

```html
<head>
  <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css" rel="stylesheet">
</head>
<body>
  <!-- tu contenido -->
  <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/js/bootstrap.bundle.min.js"></script>
</body>
```

El sistema de rejilla de Bootstrap se construye con tres niveles anidados, siempre en este orden:

```html
<div class="container">
  <div class="row">
    <div class="col">Columna 1</div>
    <div class="col">Columna 2</div>
    <div class="col">Columna 3</div>
  </div>
</div>
```

- **`.container`**: el contenedor exterior, con un ancho máximo y márgenes automáticos a los lados (`.container-fluid` en vez de `.container` ocupa el 100% del ancho, sin límite).
- **`.row`**: una fila — por debajo es, literalmente, un `display: flex` con `flex-wrap: wrap`, la misma propiedad del punto 1.
- **`.col`**: cada columna dentro de la fila. Sin número, todas las `.col` se reparten el ancho a partes iguales (igual que el `flex-grow: 1` repartido del Ejercicio 2). Con número (`.col-4`), ocupa esa proporción de las 12 columnas totales en las que se divide siempre una fila de Bootstrap:

```html
<div class="row">
  <div class="col-8">Contenido principal (8 de 12)</div>
  <div class="col-4">Barra lateral (4 de 12)</div>
</div>
```

**Breakpoints**: Bootstrap trae media queries ya definidas, y las aplicas añadiendo un infijo al nombre de la clase, siguiendo el enfoque *mobile-first* que se comentaba en el punto 4:

| Clase | Se aplica a partir de... |
|---|---|
| `.col-*` | Cualquier tamaño (por defecto) |
| `.col-md-*` | Pantallas medianas en adelante (≥768px) |
| `.col-lg-*` | Pantallas grandes en adelante (≥992px) |

```html
<div class="col-12 col-md-6 col-lg-4">
  Ocupa el 100% en móvil, la mitad en tablet, y un tercio en escritorio
</div>
```

**🧪 Ejercicio 6 — Tu primera rejilla Bootstrap**
Enlaza Bootstrap por CDN en un HTML nuevo. Crea un `.container` con una `.row` de 3 columnas iguales (`.col`), cada una con un poco de texto y un fondo de color distinto (puedes usar tu propio CSS junto a Bootstrap, no hay problema). Después, cambia las columnas a `.col-12 .col-md-4` y comprueba en el navegador (achicando la ventana) que en móvil se apilan una debajo de otra y en pantalla mediana o mayor vuelven a estar en fila.

---

## 7. Utilidades Flex y Grid de Bootstrap

Además del sistema de rejilla del punto 6, Bootstrap trae clases sueltas de **utilidad** que aplican directamente propiedades de Flexbox y Grid vistas en los puntos 1 y 3, sin escribir CSS propio:

| Clase Bootstrap | Equivale a... |
|---|---|
| `d-flex` | `display: flex` |
| `justify-content-between` | `justify-content: space-between` |
| `align-items-center` | `align-items: center` |
| `gap-3` | `gap` (con un valor predefinido de la escala de espaciado de Bootstrap) |
| `flex-column` | `flex-direction: column` |

```html
<nav class="d-flex justify-content-between align-items-center gap-3 p-3">
  <span class="fw-bold">Mi Web</span>
  <div class="d-flex gap-2">
    <a href="#">Inicio</a>
    <a href="#">Sobre mí</a>
    <a href="#">Contacto</a>
  </div>
</nav>
```

Fíjate en que esta barra de navegación es, literalmente, el Ejercicio 1 de esta misma unidad — pero en vez de escribir tu propio `.barra-navegacion { display: flex; ... }`, aplicas clases ya hechas directamente sobre el HTML. Es más rápido de escribir, a costa de tener el HTML algo más cargado de clases (un intercambio muy habitual en el trabajo con frameworks).

**🧪 Ejercicio 7 — La barra de navegación, ahora con Bootstrap**
Reconstruye la barra de navegación del Ejercicio 1 usando únicamente clases de utilidad de Bootstrap (`d-flex`, `justify-content-between`, `align-items-center`, `gap-*`), sin escribir ni una línea de CSS propio. Compara el resultado visual con tu versión original — ¿es idéntico, parecido, o hay diferencias? ¿A qué crees que se deben?

---

## 8. Componentes de Bootstrap: Cards, Carousel, NavBar

Además de la rejilla y las utilidades, Bootstrap trae **componentes completos**: bloques de HTML con clases ya pensadas para un caso de uso concreto, con su comportamiento interactivo incluido cuando hace falta JavaScript.

**Card** (tarjeta) — el bloque de contenido más usado en dashboards, catálogos y listados:

```html
<div class="card" style="width: 18rem;">
  <div class="card-body">
    <h5 class="card-title">Gasto de este mes</h5>
    <p class="card-text">342,50 €</p>
    <a href="#" class="btn btn-primary">Ver detalle</a>
  </div>
</div>
```

**NavBar** — una barra de navegación completa, con soporte integrado para colapsarse en un menú hamburguesa en móvil (esto sí necesita el JavaScript de Bootstrap enlazado, como en el punto 6):

```html
<nav class="navbar navbar-expand-lg navbar-light bg-light">
  <div class="container-fluid">
    <a class="navbar-brand" href="#">Mi Dashboard</a>
    <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#menu">
      <span class="navbar-toggler-icon"></span>
    </button>
    <div class="collapse navbar-collapse" id="menu">
      <ul class="navbar-nav">
        <li class="nav-item"><a class="nav-link" href="#">Resumen</a></li>
        <li class="nav-item"><a class="nav-link" href="#">Gastos</a></li>
        <li class="nav-item"><a class="nav-link" href="#">Ajustes</a></li>
      </ul>
    </div>
  </div>
</nav>
```

**Carousel** — un carrusel de imágenes o contenido que rota automáticamente, también con JavaScript de Bootstrap. De los tres componentes de este punto es el que menos verás en proyectos reales (paneles de administración, dashboards, ERPs): se incluye como ejemplo de componente interactivo con JavaScript ya integrado, no porque sea de los más usados — Card y NavBar sí lo son:

```html
<div id="miCarrusel" class="carousel slide" data-bs-ride="carousel">
  <div class="carousel-inner">
    <div class="carousel-item active">
      <div class="d-block w-100 bg-secondary" style="height: 200px;"></div>
    </div>
    <div class="carousel-item">
      <div class="d-block w-100 bg-info" style="height: 200px;"></div>
    </div>
  </div>
</div>
```

> 💡 **Cómo encontrar más componentes**: Bootstrap tiene docenas de componentes documentados (alertas, modales, acordeones, formularios con validación visual...). No hace falta memorizarlos: la documentación oficial (enlazada en "Para saber más") trae el código listo para copiar y adaptar de cada uno — la habilidad real no es recordar la sintaxis exacta, sino saber qué clases cambian qué (gracias a lo aprendido en los puntos 1-4) para adaptarlos a tu propio diseño.

**🧪 Ejercicio 8 — Dashboard con Cards**
Construye una rejilla (`.row` con `.col-md-4`) de 3 `Card` de Bootstrap, simulando un panel de resumen de gastos: cada tarjeta con un título (una categoría: "Alimentación", "Transporte", "Ocio"), una cantidad, y un botón `btn btn-primary` o `btn btn-outline-secondary`. Añade encima una `NavBar` de Bootstrap con al menos 3 enlaces.

---

## 🎯 Reto de clase

Construye una página de una sola pantalla que combine todo lo visto en la unidad: una `NavBar` de Bootstrap arriba, un `container` con una rejilla de `Card` (al menos 4, usando `col-12 col-md-6 col-lg-3` para que se adapten de 1 a 4 columnas según el ancho de pantalla), y al menos una transición CSS propia (por ejemplo, que las tarjetas "se levanten" al pasar el ratón, como en el punto 2). El tema es libre: un panel de gastos, un catálogo de productos, un resumen de servidores... pero tiene que verse bien tanto en móvil como en escritorio.

*Variación evaluable*: pedir que, además, añadan una sección construida con CSS Grid puro (sin clases de Bootstrap) en algún punto de la página, para comprobar que distinguen cuándo usar el framework y cuándo el CSS nativo les basta.

---

<div style="page-break-after: always;"></div>

## Resumen de la unidad

**1. Layout con Flexbox** `display: flex` en un contenedor organiza sus hijos en una dimensión (fila o columna); `justify-content`, `align-items`, `gap` y `flex-grow` controlan el reparto del espacio.

**2. Transiciones y transformaciones** `transition` anima un cambio de estado de forma suave en vez de instantánea; `transform` (`scale`, `rotate`, `translate`) cambia la apariencia geométrica sin afectar al flujo del resto de la página.

**3. Layout con Grid** `display: grid` organiza en dos dimensiones a la vez (filas y columnas), con `grid-template-columns` definiendo el número y ancho de columnas — se complementa con Flexbox, no compite con él.

**4. Diseño responsive** Las media queries (`@media (max-width: ...)`) aplican reglas CSS solo según el ancho de la ventana, permitiendo que el mismo HTML se reorganice en móvil, tablet y escritorio.

**5. Frameworks CSS: Bootstrap** Empaqueta Flexbox, Grid, media queries y transiciones en clases ya hechas — no sustituye el CSS aprendido, lo aprovecha por debajo.

**6. Sistema de rejilla de Bootstrap** `.container` → `.row` → `.col` (con infijos `-md-`, `-lg-` para breakpoints), sobre un sistema de 12 columnas y enfoque mobile-first.

**7. Utilidades Flex y Grid de Bootstrap** Clases sueltas (`d-flex`, `justify-content-between`, `gap-*`...) que aplican directamente propiedades CSS ya conocidas, sin escribir CSS propio.

**8. Componentes de Bootstrap** Cards, NavBar y Carousel — bloques de HTML con clases y, cuando hace falta, JavaScript ya integrado para un caso de uso concreto.

---

## 📚 Para saber más (opcional, no evaluable)

> 📡 **Actualidad**: además de Bootstrap, cada vez es más común el enfoque *utility-first* de frameworks como Tailwind CSS, donde en vez de componentes completos (`btn btn-primary`) se combinan clases muy pequeñas y específicas (`px-4 py-2 bg-blue-600 rounded`) directamente en el HTML. Ambos enfoques conviven hoy en proyectos reales; Bootstrap sigue siendo el más extendido para paneles de administración y prototipos rápidos por su curva de aprendizaje más suave.

- Documentación oficial de Bootstrap 5: https://getbootstrap.com/docs/5.3/
- Guía completa de Flexbox (CSS-Tricks, muy visual): https://css-tricks.com/snippets/css/a-guide-to-flexbox/
- Guía completa de Grid (CSS-Tricks): https://css-tricks.com/snippets/css/complete-guide-grid/
