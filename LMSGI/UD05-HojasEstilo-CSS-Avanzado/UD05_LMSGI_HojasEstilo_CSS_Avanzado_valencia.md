<div style="text-align: center;">

<img src="data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCA0MDAgNDAwIiB3aWR0aD0iMTgwIiBoZWlnaHQ9IjE4MCI+CiAgPGNpcmNsZSBjeD0iMjAwIiBjeT0iMjAwIiByPSIxNzAiIGZpbGw9IiNGMEZERkEiLz4KICA8Y2lyY2xlIGN4PSIyMDAiIGN5PSIyMDAiIHI9IjE3MCIgZmlsbD0ibm9uZSIgc3Ryb2tlPSIjOTlGNkU0IiBzdHJva2Utd2lkdGg9IjIiLz4KICA8cmVjdCB4PSI5MCIgeT0iMTUwIiB3aWR0aD0iOTAiIGhlaWdodD0iMTMwIiByeD0iMTAiIGZpbGw9Im5vbmUiIHN0cm9rZT0iIzBGNzY2RSIgc3Ryb2tlLXdpZHRoPSIxMCIvPgogIDxyZWN0IHg9IjIyMCIgeT0iMTEwIiB3aWR0aD0iOTAiIGhlaWdodD0iMTcwIiByeD0iMTAiIGZpbGw9IiMwRjc2NkUiIG9wYWNpdHk9IjAuMTUiIHN0cm9rZT0iIzBGNzY2RSIgc3Ryb2tlLXdpZHRoPSIxMCIvPgogIDxwYXRoIGQ9Ik0gMTk1IDE3NSBMIDIyNSAxNzUiIHN0cm9rZT0iIzBGNzY2RSIgc3Ryb2tlLXdpZHRoPSI4IiBzdHJva2UtbGluZWNhcD0icm91bmQiLz4KICA8cGF0aCBkPSJNIDIxOCAxNjggTCAyMzAgMTc1IEwgMjE4IDE4MiIgZmlsbD0ibm9uZSIgc3Ryb2tlPSIjMEY3NjZFIiBzdHJva2Utd2lkdGg9IjYiIHN0cm9rZS1saW5lY2FwPSJyb3VuZCIgc3Ryb2tlLWxpbmVqb2luPSJyb3VuZCIvPgogIDxwYXRoIGQ9Ik0gMTk1IDIzNSBMIDIyNSAyMzUiIHN0cm9rZT0iIzBGNzY2RSIgc3Ryb2tlLXdpZHRoPSI4IiBzdHJva2UtbGluZWNhcD0icm91bmQiLz4KICA8cGF0aCBkPSJNIDIxOCAyMjggTCAyMzAgMjM1IEwgMjE4IDI0MiIgZmlsbD0ibm9uZSIgc3Ryb2tlPSIjMEY3NjZFIiBzdHJva2Utd2lkdGg9IjYiIHN0cm9rZS1saW5lY2FwPSJyb3VuZCIgc3Ryb2tlLWxpbmVqb2luPSJyb3VuZCIvPgo8L3N2Zz4K" width="180" alt="Logotip LMSGI"/>

<h1>Unitat 5</h1>
<h2>Fulls d'estil II: CSS avançat</h2>

<p>
<strong>Mòdul:</strong> Llenguatges de Marques i Sistemes de Gestió d'Informació (LMSGI)<br>
<strong>Cicle formatiu:</strong> 1r ASIX (Administració de Sistemes Informàtics en Xarxa) · 1r DAW (Desenvolupament d'Aplicacions Web)<br>
<strong>Curs:</strong> 2026-2027
</p>

<p>
<strong>Docent:</strong> Noel Marco Biendicho<br>
<strong>Centre:</strong> IES Sant Vicent Ferrer — Algemesí
</p>

</div>

<div style="page-break-after: always;"></div>

## Índex

1. Layout amb Flexbox
2. Transicions i transformacions
3. Layout amb Grid
4. Disseny responsive: media queries
5. Frameworks CSS: introducció a Bootstrap
6. El sistema de rejilla de Bootstrap: contenidors i breakpoints
7. Utilitats Flex i Grid de Bootstrap
8. Components de Bootstrap: Cards, Carousel, NavBar
9. Resum de la unitat
10. Per a saber-ne més

<div style="page-break-after: always;"></div>

**RA cobert:** RA2 — *Utilitza llenguatges de marques per a la transmissió i presentació d'informació a través de la web, analitzant l'estructura dels documents i identificant els seus elements*

⚠️ **Nota d'alineació curricular**: esta unitat cobrix un únic bloc de contingut de la programació (layout amb Flexbox i Grid, transicions, disseny responsive, i introducció a Bootstrap: rejilla, utilitats i components), però el codi de CA amb què s'identifica eixe bloc **no és el mateix en ambdós cicles** — i, a diferència d'altres unitats, ací cada cicle el cobrix amb un únic CA, no amb un rang: en **ASIX (RD 1629/2009)** és **CA 2f**, i en **DAW (RD 405/2023)** és **CA 2e**. Com que la programació no desglossa eixe bloc punt per punt, esta unitat no reparteix CA per apartat — tota ella queda coberta baix el CA corresponent a cada cicle, indicat ací una sola vegada.

> 💡 **Nota d'estudi**: esta és la unitat més llarga del mòdul (18 hores) perquè reunix dos coses distintes: primer **Flexbox i Grid**, els dos sistemes de maquetació natius de CSS amb els quals es construix qualsevol disseny modern; després **Bootstrap**, un framework que empaqueta eixos mateixos conceptes en classes ja fetes per a anar més ràpid. Aprendre primer el CSS "de veres" fa que entengues *què* fa Bootstrap per davall, en lloc de copiar classes sense saber per què funcionen.

---

## 1. Layout amb Flexbox

Fins a la UD4 has donat estil a elements ja col·locats pel flux normal de l'HTML (un davall de l'altre). **Flexbox** (*Flexible Box Layout*) és el primer sistema que et deixa **controlar la disposició**: alinear elements en fila o columna, repartir l'espai entre ells, centrar coses que abans eren un mal de cap de centrar.

Per a activar Flexbox, s'aplica `display: flex` a l'element **contenidor** — els seus fills directes (els *flex items*) passen a comportar-se segons les regles de Flexbox:

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

Sense més CSS que eixe `display: flex`, els tres `<div class="item">` ja es col·loquen en fila, un al costat de l'altre, en lloc d'un davall de l'altre com farien per defecte. A partir d'ací, unes poques propietats controlen quasi tota la resta:

| Propietat | Va en... | Què controla |
|---|---|---|
| `flex-direction` | El contenidor | Direcció: `row` (fila, per defecte), `column` (columna) |
| `justify-content` | El contenidor | Repartiment en l'eix principal: `flex-start`, `center`, `space-between`, `space-around` |
| `align-items` | El contenidor | Alineació en l'eix creuat: `flex-start`, `center`, `stretch` |
| `gap` | El contenidor | Espai entre els items, sense necessitar marges manuals |
| `flex-wrap` | El contenidor | Si els items passen a la línia següent (`wrap`) quan no caben, o es comprimixen (`nowrap`, per defecte) |
| `flex-grow` | Cada item | Quant creix eixe item per a ocupar l'espai sobrant, respecte als seus germans |

```css
.barra-navegacion {
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 16px;
  padding: 12px 24px;
}
```

Amb açò, una barra de navegació típica (logo a l'esquerra, enllaços a la dreta) es resol en 4 línies, sense una sola posició calculada a mà.

> 📡 **Per què importa hui**: pràcticament qualsevol barra de navegació, fila de targetes o formulari alineat horitzontalment que veges en la web actual utilitza Flexbox per davall — és, junt amb Grid (punt 3), l'estàndard de maquetació des de fa més d'una dècada, i les tècniques antigues basades en `float` que encara trobaràs en tutorials vells estan en desús.

**🧪 Exercici 1 — Una barra de navegació amb Flexbox**
Crea un HTML amb una barra (`<nav>`) que continga un logo (un `<span>` o `<img>`) a l'esquerra i tres enllaços (`<a>`) a la dreta, tots en la mateixa línia i separats uniformement. Utilitza `display: flex`, `justify-content` i `gap`. Després, canvia `flex-direction` a `column` i observa què passa amb `justify-content` — segueix repartint en horitzontal o ha canviat d'eix?

**🧪 Exercici 2 — Targetes amb `flex-grow`**
Crea tres `<div class="tarjeta">` dins d'un contenidor `display: flex`. Dona-li a la primera targeta `flex-grow: 2` i a les altres dos `flex-grow: 1`. Observa com es reparteix l'espai disponible i explica amb les teues paraules què representa eixe número.

---

## 2. Transicions i transformacions

Ja vas vore en la UD4 que una pseudoclasse com `:hover` canvia l'estil d'un element a l'instant. Amb **transicions**, eixe canvi deixa de ser instantani i passa a ser una animació suau — sense necessitar ni una línia de JavaScript.

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

- **`transition`**: indica quines propietats animar (`background-color`, `transform`), durant quant de temps (`0.3s`) i amb quin ritme (`ease`: comença i acaba més lent que enmig). Va en l'estat **inicial** de l'element, no en el `:hover`.
- **`transform`**: canvia l'aparença geomètrica de l'element sense afectar la resta de la pàgina (a diferència de canviar `width` o `margin`, que sí que desplaça als elements veïns). Les funcions més habituals:

| Funció | Què fa | Exemple |
|---|---|---|
| `scale(n)` | Escala la grandària | `scale(1.1)` → 10% més gran |
| `rotate(deg)` | Rota l'element | `rotate(5deg)` |
| `translateX(px)` / `translateY(px)` | Desplaça l'element, sense afectar el flux de la resta de la pàgina | `translateY(-4px)` |

```css
.tarjeta {
  transition: transform 0.2s ease, box-shadow 0.2s ease;
}

.tarjeta:hover {
  transform: translateY(-4px);
  box-shadow: 0 8px 16px rgba(0, 0, 0, 0.15);
}
```

Este patró (targeta que "s'alça" lleugerament en passar el ratolí) és un dels més usats en interfícies modernes — pareix sofisticat, però són només 4 línies de CSS.

> 📡 **Seguix vigent**: `transition` cobrix el 90% dels casos de "alguna cosa canvia suaument en interactuar". Per a animacions més complexes (que es repetixen soles, amb diversos passos) existix `@keyframes` i la propietat `animation` — no entra en esta unitat, però convé saber que existix per si algun dia necessites alguna cosa més elaborada que una transició simple.

**🧪 Exercici 3 — Botó amb transició**
Retoma el botó de l'Exercici 7 de la UD4 (el que canviava de color amb `:hover`) i afig-li una `transition` perquè el canvi de color siga suau (0,3 segons) en lloc d'instantani. Afig a més un `transform: scale(1.05)` en el `:hover`.

---

## 3. Layout amb Grid

Flexbox organitza elements en **una dimensió** (una fila, o una columna). **CSS Grid** organitza en **dos dimensions alhora** (files i columnes simultàniament) — és el sistema adequat quan penses el disseny com una rejilla completa, no com una simple fila d'elements.

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

- `display: grid` activa la rejilla en el contenidor.
- `grid-template-columns: repeat(3, 1fr)` crea 3 columnes d'igual amplària (`1fr` = una "fracció" de l'espai disponible — 3 columnes d'`1fr` es reparteixen l'amplària a parts iguals).
- Els elements es van col·locant automàticament cel·la a cel·la, i en arribar a la quarta cel·la (que no cap en la primera fila de 3 columnes), Grid crea una segona fila sense que ho hages d'indicar.

**Columnes d'amplària distinta i files responsives**, sense escriure un sol número fix:

```css
.panel {
  display: grid;
  grid-template-columns: 200px 1fr;
  grid-template-rows: auto 1fr;
  gap: 16px;
  min-height: 100vh;
}
```

Ací la primera columna és fixa (200px, típic d'un menú lateral) i la segona ocupa tota la resta de l'amplària (`1fr`) — el patró exacte d'un panell d'administració o d'un dashboard amb menú lateral i contingut principal.

> 💡 **Flexbox o Grid?** No competixen entre si, es complementen: Grid per a l'estructura general de la pàgina (menú lateral + contingut, capçalera + cos + peu), i Flexbox per a organitzar elements dins de cadascuna d'eixes zones (els botons d'una barra, les targetes dins de l'àrea de contingut). És habitual, i correcte, imbricar un `display: flex` dins d'una cel·la d'un `display: grid`.

**🧪 Exercici 4 — Panell amb menú lateral**
Construix un HTML amb un `<div class="panel">` que continga un `<nav>` (menú lateral) i un `<main>` (contingut). Amb CSS Grid, fes que el menú ocupe una columna fixa de 220px i el contingut ocupe la resta de l'amplària disponible. Afig dins del `<main>` una rejilla de targetes (`display: grid`, `grid-template-columns: repeat(3, 1fr)`) amb 6 targetes.

---

## 4. Disseny responsive: media queries

Un disseny **responsive** (adaptable) es veu bé tant en un mòbil com en un ordinador d'escriptori, sense necessitar dos webs distintes. La ferramenta clau són les **media queries**: blocs de CSS que només s'apliquen si es complix una condició sobre el dispositiu, quasi sempre l'amplària de la finestra.

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

- `@media (max-width: 768px)` significa "aplica este bloc de regles només quan la finestra mesura 768 píxels d'amplària o menys".
- Ací la rejilla passa de 3 columnes a 2 en tauleta, i a 1 sola columna en mòbil — el mateix HTML, sense tocar-lo, es reorganitza segons l'espai disponible.

Les amplàries de referència on canvia el disseny (768px, 480px...) s'anomenen **breakpoints**, i convé pensar-los de "gran a xicotet" (*mobile-first* seria justament al revés: escriure primer el CSS per a mòbil i utilitzar `min-width` per a anar afegint columnes a mesura que creix la pantalla — és l'enfocament que voràs en Bootstrap, en el punt 6).

**🧪 Exercici 5 — Rejilla responsive**
Retoma la rejilla de targetes de l'Exercici 4 i afig dos media queries: una perquè passe a 2 columnes per davall de 768px, i una altra perquè passe a 1 columna per davall de 480px. Comprova el resultat encongint la finestra del navegador a poc a poc (o amb les ferramentes de desenvolupador de Firefox, en mode "vista adaptable").

---

## 5. Frameworks CSS: introducció a Bootstrap

> ⚠️ **Fins ací, CSS natiu**: els punts 1-4 (Flexbox, transicions, Grid, responsive) són CSS pur, el que entén qualsevol navegador sense dependre de res extern. A partir d'ací entra **Bootstrap**, un framework que reutilitza exactament eixos mateixos conceptes empaquetats en classes ja fetes. No són peces noves i distintes — és la mateixa caixa d'ferramentes, embolicada per a anar més ràpid.

Tot el que s'ha vist en els punts 1-4 (Flexbox, Grid, media queries) és CSS "pur" — funciona en qualsevol navegador sense dependre de res extern, i és fonamental entendre'l. Però escriure des de zero el layout responsive d'un projecte gran, botó a botó i targeta a targeta, és lent i repetitiu. Un **framework CSS** resol açò oferint un conjunt de classes ja fetes, provades i coherents entre si, per a no reinventar cada component des de zero.

**Bootstrap** és el framework CSS més estés — creat originalment en Twitter (2011) per a unificar l'estil entre els seus propis equips interns, i alliberat després com a projecte de codi obert. En essència, és exactament el que has aprés en els punts 1-4 (Flexbox, Grid, media queries, transicions), però ja escrit i empaquetat en classes que apliques directament en l'HTML.

```html
<!-- Sense Bootstrap: tu escrius el CSS -->
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

<!-- Amb Bootstrap: la classe ja porta el CSS fet -->
<button class="btn btn-primary">Guardar</button>
```

⚠️ **Un framework no substituïx el que s'ha aprés, l'aprofita**: quan escrius `class="btn btn-primary"`, per davall hi ha literalment regles CSS amb selectors de classe, propietats i valors — les mateixes peces de la UD4 i d'este punt. Saber CSS "de veres" és el que et permet, per exemple, entendre per què un botó de Bootstrap no es veu com esperaves quan el combines amb el teu propi CSS, i corregir-ho amb coneixement en lloc d'a prova i error.

> 📡 **Actualitat**: Bootstrap 5 (la versió que utilitzarem) va eliminar la dependència de jQuery que tenien les versions anteriors — hui funciona amb JavaScript natiu del navegador. Seguix sent, junt amb Tailwind CSS (un enfocament distint, d'utilitats més xicotetes), un dels frameworks CSS més usats en projectes reals, especialment per a panells d'administració i prototips ràpids.

---

## 6. El sistema de rejilla de Bootstrap: contenidors i breakpoints

Per a utilitzar Bootstrap sense instal·lar res, n'hi ha prou amb enllaçar el seu CSS (i, per a alguns components interactius, el seu JavaScript) des d'un **CDN** (*Content Delivery Network*, una xarxa de servidors que servix l'arxiu ja preparat, sense que l'hages de descarregar tu):

```html
<head>
  <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css" rel="stylesheet">
</head>
<body>
  <!-- el teu contingut -->
  <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/js/bootstrap.bundle.min.js"></script>
</body>
```

El sistema de rejilla de Bootstrap es construïx amb tres nivells imbricats, sempre en este ordre:

```html
<div class="container">
  <div class="row">
    <div class="col">Columna 1</div>
    <div class="col">Columna 2</div>
    <div class="col">Columna 3</div>
  </div>
</div>
```

- **`.container`**: el contenidor exterior, amb una amplària màxima i marges automàtics als costats (`.container-fluid` en lloc de `.container` ocupa el 100% de l'amplària, sense límit).
- **`.row`**: una fila — per davall és, literalment, un `display: flex` amb `flex-wrap: wrap`, la mateixa propietat del punt 1.
- **`.col`**: cada columna dins de la fila. Sense número, totes les `.col` es reparteixen l'amplària a parts iguals (igual que el `flex-grow: 1` repartit de l'Exercici 2). Amb número (`.col-4`), ocupa eixa proporció de les 12 columnes totals en què es dividix sempre una fila de Bootstrap:

```html
<div class="row">
  <div class="col-8">Contenido principal (8 de 12)</div>
  <div class="col-4">Barra lateral (4 de 12)</div>
</div>
```

**Breakpoints**: Bootstrap porta media queries ja definides, i les apliques afegint un infix al nom de la classe, seguint l'enfocament *mobile-first* que es comentava en el punt 4:

| Classe | S'aplica a partir de... |
|---|---|
| `.col-*` | Qualsevol grandària (per defecte) |
| `.col-md-*` | Pantalles mitjanes en avant (≥768px) |
| `.col-lg-*` | Pantalles grans en avant (≥992px) |

```html
<div class="col-12 col-md-6 col-lg-4">
  Ocupa el 100% en móvil, la mitad en tablet, y un tercio en escritorio
</div>
```

**🧪 Exercici 6 — La teua primera rejilla Bootstrap**
Enllaça Bootstrap per CDN en un HTML nou. Crea un `.container` amb una `.row` de 3 columnes iguals (`.col`), cadascuna amb un poc de text i un fons de color distint (pots utilitzar el teu propi CSS junt amb Bootstrap, no hi ha problema). Després, canvia les columnes a `.col-12 .col-md-4` i comprova en el navegador (encongint la finestra) que en mòbil s'apilen una davall de l'altra i en pantalla mitjana o major tornen a estar en fila.

---

## 7. Utilitats Flex i Grid de Bootstrap

A més del sistema de rejilla del punt 6, Bootstrap porta classes soltes d'**utilitat** que apliquen directament propietats de Flexbox i Grid vistes en els punts 1 i 3, sense escriure CSS propi:

| Classe Bootstrap | Equival a... |
|---|---|
| `d-flex` | `display: flex` |
| `justify-content-between` | `justify-content: space-between` |
| `align-items-center` | `align-items: center` |
| `gap-3` | `gap` (amb un valor predefinit de l'escala d'espaiat de Bootstrap) |
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

Fixa't que esta barra de navegació és, literalment, l'Exercici 1 d'esta mateixa unitat — però en lloc d'escriure la teua pròpia `.barra-navegacion { display: flex; ... }`, apliques classes ja fetes directament sobre l'HTML. És més ràpid d'escriure, a costa de tindre l'HTML una miqueta més carregat de classes (un intercanvi molt habitual en el treball amb frameworks).

**🧪 Exercici 7 — La barra de navegació, ara amb Bootstrap**
Reconstruïx la barra de navegació de l'Exercici 1 utilitzant únicament classes d'utilitat de Bootstrap (`d-flex`, `justify-content-between`, `align-items-center`, `gap-*`), sense escriure ni una línia de CSS propi. Compara el resultat visual amb la teua versió original — és idèntic, semblant, o hi ha diferències? A què creus que es deuen?

---

## 8. Components de Bootstrap: Cards, Carousel, NavBar

A més de la rejilla i les utilitats, Bootstrap porta **components complets**: blocs d'HTML amb classes ja pensades per a un cas d'ús concret, amb el seu comportament interactiu inclòs quan fa falta JavaScript.

**Card** (targeta) — el bloc de contingut més usat en dashboards, catàlegs i llistats:

```html
<div class="card" style="width: 18rem;">
  <div class="card-body">
    <h5 class="card-title">Gasto de este mes</h5>
    <p class="card-text">342,50 €</p>
    <a href="#" class="btn btn-primary">Ver detalle</a>
  </div>
</div>
```

**NavBar** — una barra de navegació completa, amb suport integrat per a col·lapsar-se en un menú hamburguesa en mòbil (açò sí que necessita el JavaScript de Bootstrap enllaçat, com en el punt 6):

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

**Carousel** — un carrusel d'imatges o contingut que rota automàticament, també amb JavaScript de Bootstrap. Dels tres components d'este punt és el que menys veuràs en projectes reals (panells d'administració, dashboards, ERPs): s'inclou com a exemple de component interactiu amb JavaScript ja integrat, no perquè siga dels més usats — Card i NavBar sí que ho són:

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

> 💡 **Com trobar més components**: Bootstrap té dotzenes de components documentats (alertes, modals, acordions, formularis amb validació visual...). No fa falta memoritzar-los: la documentació oficial (enllaçada en "Per a saber-ne més") porta el codi llest per a copiar i adaptar de cadascun — l'habilitat real no és recordar la sintaxi exacta, sinó saber quines classes canvien què (gràcies al que s'ha aprés en els punts 1-4) per a adaptar-los al teu propi disseny.

**🧪 Exercici 8 — Dashboard amb Cards**
Construix una rejilla (`.row` amb `.col-md-4`) de 3 `Card` de Bootstrap, simulant un panell de resum de despeses: cada targeta amb un títol (una categoria: "Alimentación", "Transporte", "Ocio"), una quantitat, i un botó `btn btn-primary` o `btn btn-outline-secondary`. Afig damunt una `NavBar` de Bootstrap amb almenys 3 enllaços.

---

## 🎯 Repte de classe

Construix una pàgina d'una sola pantalla que combine tot el que s'ha vist en la unitat: una `NavBar` de Bootstrap a dalt, un `container` amb una rejilla de `Card` (almenys 4, utilitzant `col-12 col-md-6 col-lg-3` perquè s'adapten d'1 a 4 columnes segons l'amplària de pantalla), i almenys una transició CSS pròpia (per exemple, que les targetes "s'alcen" en passar el ratolí, com en el punt 2). El tema és lliure: un panell de despeses, un catàleg de productes, un resum de servidors... però ha de vore's bé tant en mòbil com en escriptori.

*Variació avaluable*: demanar que, a més, afigen una secció construïda amb CSS Grid pur (sense classes de Bootstrap) en algun punt de la pàgina, per a comprovar que distingixen quan utilitzar el framework i quan el CSS natiu els basta.

---

<div style="page-break-after: always;"></div>

## Resum de la unitat

**1. Layout amb Flexbox** `display: flex` en un contenidor organitza els seus fills en una dimensió (fila o columna); `justify-content`, `align-items`, `gap` i `flex-grow` controlen el repartiment de l'espai.

**2. Transicions i transformacions** `transition` anima un canvi d'estat de forma suau en lloc d'instantània; `transform` (`scale`, `rotate`, `translate`) canvia l'aparença geomètrica sense afectar el flux de la resta de la pàgina.

**3. Layout amb Grid** `display: grid` organitza en dos dimensions alhora (files i columnes), amb `grid-template-columns` definint el nombre i amplària de columnes — es complementa amb Flexbox, no competix amb ell.

**4. Disseny responsive** Les media queries (`@media (max-width: ...)`) apliquen regles CSS només segons l'amplària de la finestra, permetent que el mateix HTML es reorganitze en mòbil, tauleta i escriptori.

**5. Frameworks CSS: Bootstrap** Empaqueta Flexbox, Grid, media queries i transicions en classes ja fetes — no substituïx el CSS aprés, l'aprofita per davall.

**6. Sistema de rejilla de Bootstrap** `.container` → `.row` → `.col` (amb infixos `-md-`, `-lg-` per a breakpoints), sobre un sistema de 12 columnes i enfocament mobile-first.

**7. Utilitats Flex i Grid de Bootstrap** Classes soltes (`d-flex`, `justify-content-between`, `gap-*`...) que apliquen directament propietats CSS ja conegudes, sense escriure CSS propi.

**8. Components de Bootstrap** Cards, NavBar i Carousel — blocs d'HTML amb classes i, quan fa falta, JavaScript ja integrat per a un cas d'ús concret.

---

## 📚 Per a saber-ne més (opcional, no avaluable)

> 📡 **Actualitat**: a més de Bootstrap, cada vegada és més comú l'enfocament *utility-first* de frameworks com Tailwind CSS, on en lloc de components complets (`btn btn-primary`) es combinen classes molt xicotetes i específiques (`px-4 py-2 bg-blue-600 rounded`) directament en l'HTML. Ambdós enfocaments conviuen hui en projectes reals; Bootstrap seguix sent el més estés per a panells d'administració i prototips ràpids per la seua corba d'aprenentatge més suau.

- Documentació oficial de Bootstrap 5: https://getbootstrap.com/docs/5.3/
- Guia completa de Flexbox (CSS-Tricks, molt visual): https://css-tricks.com/snippets/css/a-guide-to-flexbox/
- Guia completa de Grid (CSS-Tricks): https://css-tricks.com/snippets/css/complete-guide-grid/
