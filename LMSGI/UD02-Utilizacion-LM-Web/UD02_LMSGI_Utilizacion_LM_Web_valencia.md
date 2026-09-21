<div style="text-align: center;">

<img src="data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCA0MDAgNDAwIiB3aWR0aD0iMTgwIiBoZWlnaHQ9IjE4MCI+CiAgPGNpcmNsZSBjeD0iMjAwIiBjeT0iMjAwIiByPSIxNzAiIGZpbGw9IiNGMEZERkEiLz4KICA8Y2lyY2xlIGN4PSIyMDAiIGN5PSIyMDAiIHI9IjE3MCIgZmlsbD0ibm9uZSIgc3Ryb2tlPSIjOTlGNkU0IiBzdHJva2Utd2lkdGg9IjIiLz4KICA8Y2lyY2xlIGN4PSIyMDAiIGN5PSIyMDAiIHI9IjExMCIgZmlsbD0ibm9uZSIgc3Ryb2tlPSIjMEY3NjZFIiBzdHJva2Utd2lkdGg9IjE0Ii8+CiAgPGVsbGlwc2UgY3g9IjIwMCIgY3k9IjIwMCIgcng9IjQ1IiByeT0iMTEwIiBmaWxsPSJub25lIiBzdHJva2U9IiMwRjc2NkUiIHN0cm9rZS13aWR0aD0iMTAiLz4KICA8bGluZSB4MT0iOTAiIHkxPSIyMDAiIHgyPSIzMTAiIHkyPSIyMDAiIHN0cm9rZT0iIzBGNzY2RSIgc3Ryb2tlLXdpZHRoPSIxMCIvPgogIDxwYXRoIGQ9Ik0gMTEwIDE0NSBRIDIwMCAxNzUgMjkwIDE0NSIgZmlsbD0ibm9uZSIgc3Ryb2tlPSIjMEY3NjZFIiBzdHJva2Utd2lkdGg9IjgiLz4KICA8cGF0aCBkPSJNIDExMCAyNTUgUSAyMDAgMjI1IDI5MCAyNTUiIGZpbGw9Im5vbmUiIHN0cm9rZT0iIzBGNzY2RSIgc3Ryb2tlLXdpZHRoPSI4Ii8+Cjwvc3ZnPgo=" width="180" alt="Logotip UD2 LMSGI — globus terraqüi"/>

<h1>Unitat 2</h1>
<h2>Utilització dels llenguatges de marques en la Web</h2>

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

1. HTML en el panorama de la Web: classificació i evolució (CA 2a)
   - 1.1 Els llenguatges de marques de la Web
   - 1.2 L'evolució de les versions d'HTML
2. Estructura d'un document HTML (CA 2b)
3. Etiquetes i atributs principals: construint una pàgina completa (CA 2c)
   - 3.1 Text, llistes i enllaços
   - 3.2 Taules
   - 3.3 Imatges i contenidors genèrics
4. XHTML: sintaxi estricta i conversió (CA 2d)
5. Formularis bàsics: elements i tipus de camp

6. Resum de la unitat
7. Per a saber-ne més

<div style="page-break-after: always;"></div>

**RA cobert:** RA2 — *Utilitza llenguatges de marques per a la transmissió i presentació d'informació a través de la Web, analitzant l'estructura dels documents i identificant els seus elements* (CA 2a-2e)

> 💡 **Nota d'estudi**: esta unitat és més curta que la UD1 (al voltant de 6-7 hores lectives enfront de les 12 de la UD1) perquè és sobretot pràctica — anireu a escriure prou HTML de veritat. La teoria és breu a propòsit; l'aprenentatge real ve de teclejar, guardar i obrir en el navegador. A partir d'ací, quan un exemple demane "obri'l en Firefox", féu-ho de veritat — l'HTML s'aprén veient el resultat, no només llegint el codi.

---

## 1. HTML en el panorama de la Web: classificació i evolució (CA 2a)

### 1.1 Els llenguatges de marques de la Web

En la UD1 vam veure que **HTML** és una *aplicació de SGML* — a diferència de XML, que és un metallenguatge amb el qual tu defineixes les teues pròpies etiquetes, HTML té un vocabulari d'etiquetes **fix**, definit per un estàndard, pensat específicament per a estructurar pàgines web. Eixa relació amb SGML és sobretot històrica: hui l'HTML Living Standard definix les seues pròpies regles d'anàlisi i evolució, independents de SGML.

No és l'únic llenguatge de marques relacionat amb la Web, encara que sí el més important:

| Llenguatge | Què és | On el vorem en este mòdul? |
|---|---|---|
| **HTML** | Estructura i contingut d'una pàgina web | Esta unitat i les següents |
| **XHTML** | Reformulació d'HTML amb sintaxi XML estricta | Punt 4 |
| **CSS** | Presentació visual (colors, mides, disposició) | UD4 i UD5 |
| **SVG** | Gràfics vectorials — ja el vau veure en la UD1 (el logo `</>` de la portada d'aquella unitat) | Es pot incrustar directament en HTML |

> 📡 **Recordatori de la UD1 (apartat 4.1)**: des de 2019 el W3C va cedir l'autoritat de l'estàndard HTML al **WHATWG**, que el manté com a *Living Standard* — un document únic que s'actualitza contínuament, sense tancar-se mai en un número de versió. "HTML5" és hui més una etiqueta de màrqueting que una versió formal tancada. Açò és clau per a entendre l'apartat següent.

Els navegadors no són els únics programes que llegeixen HTML: un lector de pantalla anuncia el contingut en veu alta, un cercador el rastreja per a indexar-lo, un framework de *testing* automatitzat el recorre per a fer clic en botons... tots ells són *user-agents* distints interpretant el mateix document marcat, exactament com vam veure en la UD1 (apartat 1).

---

### 1.2 L'evolució de les versions d'HTML

Abans d'escriure HTML convé saber, en dos frases, d'on ve, perquè encara us trobareu codi antic amb marques d'una època distinta: entre 1995 i 2014 va ser una successió de **versions tancades i numerades** (HTML 2.0 a HTML5), amb un intent a mig camí de reescriure'l amb la sintaxi estricta d'XML — **XHTML** (2000-2001, vegeu el punt 4) — que va quedar en desús fa anys. Des de 2019 el WHATWG el manté com el **Living Standard** que ja coneixeu de la UD1: un document únic que s'actualitza sense tancar-se mai en un número de versió.

En resum: hui "HTML5" ja no descriu una versió tancada, sinó que és la forma col·loquial de referir-se a l'estàndard viu actual.

> 🕰️ **Per què açò importa en la pràctica**: si mai obriu codi HTML molt antic i veeu un `<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01//EN" "http://www.w3.org/TR/html4/strict.dtd">`, no us espanteu — és un DOCTYPE de l'època en què HTML citava literalment un DTD extern (el mateix concepte de DTD que vau construir pas a pas en la UD1, apartat 4.2, amb el catàleg de sèries). HTML5 va simplificar açò radicalment: ja no depén de cap DTD, així que el seu DOCTYPE és només `<!DOCTYPE html>`, com veureu en el punt 2.

---

## 2. Estructura d'un document HTML (CA 2b)

Anem a veure-ho amb les mans abans que amb la teoria.

**🧪 Pas a pas — El teu primer document HTML**

1. En la teua carpeta `LMSGI` (la que vau crear en la UD1), crea una carpeta nova `UD02`.
2. Obri VS Code sobre eixa carpeta (`Aplicacions → Programació → VS Code`, o des d'un terminal amb `code UD02`) i crea un arxiu nou anomenat `index.html`.
3. Escriu exactament açò:

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

4. Guarda (`Ctrl+S`) i obri'l amb Firefox: clic dret sobre `index.html` en l'explorador d'arxius de VS Code → *Reveal in Files* → doble clic, o arrossegant l'arxiu a una finestra de Firefox ja oberta.
5. Fixa't en dos llocs distints: la **pestanya** del navegador i el **cos** de la pàgina. Quin text apareix en cadascun?

Ja teniu l'esquelet que tindrà tot document HTML que escriviu. Per parts:

- **`<!DOCTYPE html>`**: li diu al navegador que interprete la pàgina en mode estàndard HTML5 (enfront del "quirks mode" que s'activa si falta). No és una etiqueta amb tancament, és una declaració.
- **`<html lang="es">`**: l'element arrel — com l'element arrel únic que vau veure en XML en la UD1, només pot haver-hi un. L'atribut `lang` indica l'idioma principal del document (accessibilitat i cercadors).
- **`<head>`**: metainformació que **no es mostra** en la pàgina — títol de pestanya, codificació, enllaços a fulls d'estil (UD4), metadades per a cercadors...
  - **`<meta charset="UTF-8">`**: declara la codificació de caràcters, igual que feia `encoding="UTF-8"` en la declaració XML de la UD1 — és el que permet que els accents, `ç` i `ñ` es vegen bé en qualsevol sistema.
  - **`<title>`**: el text que apareix en la pestanya del navegador. No confondre amb `<h1>`, que és un titular visible **dins** de la pàgina — és l'error més típic quan es comença.
- **`<body>`**: tot el contingut visible de la pàgina.

⚠️ **Important**: a diferència d'XML (UD1, apartat 4.3), HTML **no exigeix** que tot estiga sempre ben tancat o en minúscules per a funcionar — el navegador "perdona" molts errors. Però açò no significa que estiga bé escriure HTML descuidat: un document HTML ben format és més fàcil de mantindre, es comporta igual en tots els navegadors i és imprescindible si en el punt 4 voleu convertir-lo a XHTML.

**🧪 Exercici 1 — Comprova què fa cada línia**

Sobre el teu propi `index.html`: canvia el `<title>` pel teu nom i el `<h1>` per una salutació, guarda i recarrega Firefox — confirma que el canvi de `<title>` només es veu en la pestanya i el de `<h1>` només en la pàgina. Després, esborra la línia `<meta charset="UTF-8">`, guarda i recarrega: si el teu document té algun accent o `ñ`, què li passa? Torna a afegir la línia i comprova que s'arregla.

---

## 3. Etiquetes i atributs principals: construint una pàgina completa (CA 2c)

En la UD1 ja vau usar `<h1>`-`<h6>` i `<p>`. Anem a ampliar `index.html` pas a pas, afegint bloc a bloc la resta d'etiquetes amb què es construeix la majoria de pàgines web reals — al final tindràs una pàgina completa, no fragments solts.

### 3.1 Text, llistes i enllaços

Afig açò dins del teu `<body>`, davall del `<p>` que ja tenies:

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

- `<ul>` (*unordered list*) per a llistes sense ordre important (amb pics); `<ol>` (*ordered list*) quan l'ordre importa (numerada automàticament). Cada element va dins d'un `<li>` (*list item*).
- `<a href="...">`: un enllaç **absolut** (`https://...`) apunta a qualsevol lloc d'Internet; un enllaç **relatiu** (per exemple `ficha-alumno.html`, que usareu en el punt 3.3) apunta a un arxiu dins del vostre propi projecte — més recomanable mentre treballeu en local, perquè no depén que l'altre lloc existisca. `target="_blank"` obri l'enllaç en una pestanya nova.

Guarda i recarrega Firefox — comprova que es veuen les dos llistes i que l'enllaç funciona.

---

### 3.2 Taules

Recuperant l'exemple de la discografia de la UD1 (apartat 4.2, exercici 6, on el vau fer en XML), així es vorà la mateixa informació en HTML. Afig açò a continuació:

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

`<table>` conté files `<tr>` (*table row*); `<th>` (*table header*) són les cel·les de capçalera i `<td>` (*table data*) les cel·les normals. `<thead>`/`<tbody>` són opcionals però recomanables: separen semànticament la capçalera del cos de dades.

> 💡 Fixa't en el paral·lelisme amb la UD1: en XML decidíeu vosaltres les etiquetes (`<disco>`, `<agotado/>`, apartat 4.2); en HTML les etiquetes de taula ja existeixen i estan fixades per l'estàndard — és la diferència entre un llenguatge de marques de propòsit general (XML) i un de propòsit específic per a la Web (HTML) que vam veure en el punt 1.1.

---

### 3.3 Imatges i contenidors genèrics

Finalment, afig una imatge i un bloc agrupat:

```html
<img src="logo.png" alt="Logotipo del IES Sant Vicent Ferrer">

<div class="tarjeta">
  <span id="destacado">Texto destacado</span> dentro de un párrafo normal.
</div>
```

- `src` indica la ruta de l'arxiu (relativa o absoluta, igual que en els enllaços); `alt` és un text alternatiu — **obligatori per accessibilitat**: és el que anuncia un lector de pantalla (recordeu els *user-agents* de la UD1, apartat 1?) i el que es mostra si la imatge no carrega.
- `<div>` agrupa contingut en bloc (ocupa tota l'amplària disponible); `<span>` agrupa contingut en línia (només el que envolta). Per si sols no signifiquen res — són "caixes" genèriques que prenen sentit amb CSS (UD4) o JavaScript.
- **Atributs comuns** a quasi qualsevol etiqueta: `id` (identificador únic en la pàgina, no es pot repetir), `class` (etiqueta reutilitzable per a agrupar diversos elements), `title` (text que apareix com a *tooltip* en passar el ratolí).

Si no tens cap imatge a mà, no passa res: guarda qualsevol `.png`/`.jpg` en la mateixa carpeta que `index.html` amb el nom `logo.png`, o canvia l'`src` pel nom de l'arxiu que tingues.

**🧪 Exercici 2 — Fitxa web d'un alumne**

Ara, pel teu compte i en un arxiu nou `ficha-alumno.html` (amb l'esquelet complet del punt 2), crea la fitxa web d'un alumne — pots reutilitzar la Claudia de la UD1 o inventar les teues pròpies dades:
1. Un `<h1>` amb el nom de l'alumne.
2. Una llista `<ul>` amb els seus mòduls preferits.
3. Una taula amb les seues notes (mínim 3 files, columnes: mòdul i nota).
4. Un enllaç a la web del centre.
5. Una imatge qualsevol, amb el seu `alt` descrivint-la de veritat (no "imagen1.jpg").

Comprova el resultat en Firefox abans de continuar — el necessitaràs per a l'exercici següent.

---

## 4. XHTML: sintaxi estricta i conversió (CA 2d)

En la UD1 (apartat 4.3, nota històrica) ja vam avançar que a finals dels anys 90 es va crear **XHTML**: una reformulació d'HTML obligada a complir les mateixes regles de "bon format" que vam veure per a XML. Hui és pràcticament teoria sense cas pràctic real — va quedar en desús fa anys i cap projecte nou l'utilitza —, però és l'exemple més clar per a veure què significa que un HTML es puga processar amb les mateixes garanties que un XML: interessa quan una aplicació necessita extraure dades automàticament de pàgines web sense sorpreses d'etiquetes mal tancades a mig procés, el mateix raonament que sustenta el que veureu en les UD 8 i 9 (esquemes i conversió de documents).

| Regla | HTML (permissiu) | XHTML (estricte, com XML) |
|---|---|---|
| Tancament d'etiquetes | `<li>Café` (es pot deixar sense tancar) | `<li>Café</li>` — tancament obligatori, com en la UD1 |
| Elements buits | `<br>`, `<img src="foto.jpg">` | `<br/>`, `<img src="foto.jpg"/>` — autotancament obligatori |
| Majúscules/minúscules | `<P>`, `<p>`, `<DIV>` són equivalents | Tot en minúscules: `<p>`, `<div>` — recordeu, XML distingeix majúscules de minúscules |
| Atributs | `<input disabled>`, `<td width=100>` es toleren | `<input disabled="disabled"/>`, `<td width="100">` — valor explícit i cometes obligatòries, igual que en XML |

En altres paraules: **tot document XHTML és també un document XML ben format** (les 6 regles de la UD1, apartat 4.3) — per això es pot obrir directament amb un analitzador XML, cosa que un HTML corrent, en permetre errors, no garanteix. Exemple de conversió:

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

**🧪 Exercici 3 — Aplica les diferències**

Sobre 3-4 línies de la teua `ficha-alumno.html` (no cal convertir tot el document), aplica les diferències de la taula anterior: busca un element buit (per exemple `<img>`) i tanca'l amb autotancament (`/>`), i revisa que no et quede cap etiqueta en majúscules ni cap atribut sense cometes.

---

## 5. Formularis bàsics: elements i tipus de camp

Açò és només el vocabulari bàsic de formularis — no cal dominar-lo encara, l'ampliarem amb validació i enviament de dades en la **UD3**.

Un formulari arreplega dades de l'usuari per a enviar-les a algun lloc (un servidor, per exemple):

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

- **`<form>`**: envolta tot el formulari.
- **`<label for="...">`**: associa un text a un camp pel seu `id` — important per accessibilitat (un lector de pantalla anuncia l'etiqueta en enfocar el camp) i perquè en fer clic en el text s'active el camp.
- **`<input>`**: el camp en si; l'atribut `type` decideix què es pot escriure: `text` (text lliure), `email`, `number`, `checkbox` (casella), `radio` (opció única entre diverses) — HTML5 valida el format bàsic d'alguns tipus automàticament, però d'això en parlarem amb detall en la UD3.
- **`name`**: l'identificador amb què viatjarà la dada en enviar-se — no ho desenvoluparem fins que veeu l'enviament de dades en la UD3.

**🧪 Exercici 4 — Formulari d'inscripció**

Crea `inscripcion.html` amb un formulari que arreplegue: nom (text), correu (email), edat (número), mòdul preferit (tria entre `radio` amb 2-3 opcions), i un botó d'enviament. Cada camp ha de tindre la seua `<label>` correctament associada amb `for`/`id`.

---

## Resum de la unitat

**1. HTML en el panorama de la Web** *(CA 2a)* HTML és una aplicació de SGML amb vocabulari fix, pensada específicament per a la Web, junt amb XHTML, CSS i SVG. Evolució: d'HTML 2-4.01 (versions tancades) a XHTML (sintaxi estricta) a HTML5 i, des de 2019, al Living Standard del WHATWG — sense versions tancades.

**2. Estructura d'un document HTML** *(CA 2b)* `<!DOCTYPE html>`, `<html>` com a arrel única, `<head>` (metainformació) i `<body>` (contingut visible) — l'esquelet que tindrà tot document HTML que escriviu.

**3. Etiquetes i atributs principals** *(CA 2c)* Llistes (`<ul>`/`<ol>`/`<li>`), enllaços (`<a href>`), taules (`<table>`/`<tr>`/`<th>`/`<td>`), imatges (`<img src alt>`) i contenidors genèrics (`<div>`/`<span>`) amb els seus atributs comuns (`id`, `class`, `title`) — tot construït sobre una única pàgina, `index.html`, que vau anar ampliant bloc a bloc.

**4. XHTML** *(CA 2d)* Reformulació d'HTML amb sintaxi XML estricta: tancament obligatori, minúscules, cometes, autotancament. El seu valor real està a garantir documents processables de forma fiable amb eines XML en sistemes de gestió d'informació — no en el seu ús real en producció, que és pràcticament nul hui.

**5. Formularis bàsics** *(avanç de UD3)* `<form>`, `<label for>`, `<input type="...">` — vocabulari mínim; la validació i l'enviament de dades es tracten en la UD3.

---

## 📚 Per a saber-ne més (opcional, no avaluable)

### Per a què et servirà l'HTML d'esta unitat?

El que heu vist ací (estructura, etiquetes, atributs) és la base mínima amb què s'escriu qualsevol pàgina web — l'aprofundiment real arriba a partir de la **UD3** (formularis avançats i validació), **UD4-5** (fulls d'estil, CSS) i **UD6** (manipulació de documents web amb JavaScript). No cal dominar-ho tot ja: de moment n'hi ha prou amb reconéixer l'estructura d'un HTML i ser capaços d'escriure'n un de correcte vosaltres mateixos.

A data d'este curs (2026-2027), convé saber que l'ecosistema al voltant d'HTML continua canviant activament en diversos fronts:

- **Accessibilitat, cada vegada més exigida per llei**: la normativa europea d'accessibilitat digital (Directiva (UE) 2019/882, traslladada a Espanya pel Reial Decret 1112/2018 i el seu desenvolupament posterior) obliga que bona part de les webs d'administracions i empreses complisquen criteris **WCAG**. L'`alt` de les imatges que heu usat en el punt 3.3, o el `<label for>` dels formularis del punt 5, no són un capritx — són exactament el tipus de detall que s'audita.
- **Elements semàntics**: HTML5 va incorporar etiquetes com `<header>`, `<nav>`, `<main>`, `<article>` o `<footer>`, que descriuen el significat de cada bloc en compte d'usar sempre `<div>`. No les hem usat encara (les veureu amb més detall en treballar amb CSS en la UD4-5), però són la forma recomanada hui d'estructurar una pàgina real.
- **Els tres motors de navegador**: pràcticament tot el que veeu en pantalla el renderitza un de tres motors — Blink (Chrome, Edge, Opera i la majoria de navegadors basats en Chromium), WebKit (Safari) o Gecko (Firefox, el que useu a l'aula). Quan una pàgina es veu distinta segons el navegador, quasi sempre és una diferència entre estos tres motors interpretant el mateix HTML.

### I l'XHTML del punt 4?

Si et preguntes per què dediquem un punt sencer a alguna cosa "que ja no s'usa": no és que estigueu perdent el temps, és que continua sent l'exemple més clar per a entendre què significa que un document siga processable de forma fiable — el mateix raonament que necessitareu en la UD7 (validació de documents), només que allà s'aplica directament sobre HTML i XML, sense passar per XHTML com a pas intermedi.

- MDN Web Docs — Referència HTML: https://developer.mozilla.org/es/docs/Web/HTML
- HTML Living Standard (WHATWG): https://html.spec.whatwg.org/
- W3C — Recomanació XHTML 1.0: https://www.w3.org/TR/xhtml1/
</content>
