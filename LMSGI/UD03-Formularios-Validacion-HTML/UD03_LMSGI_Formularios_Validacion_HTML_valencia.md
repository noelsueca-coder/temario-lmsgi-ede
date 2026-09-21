<div style="text-align: center;">

<img src="data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCA0MDAgNDAwIiB3aWR0aD0iMTgwIiBoZWlnaHQ9IjE4MCI+CiAgPGNpcmNsZSBjeD0iMjAwIiBjeT0iMjAwIiByPSIxNzAiIGZpbGw9IiNGMEZERkEiLz4KICA8Y2lyY2xlIGN4PSIyMDAiIGN5PSIyMDAiIHI9IjE3MCIgZmlsbD0ibm9uZSIgc3Ryb2tlPSIjOTlGNkU0IiBzdHJva2Utd2lkdGg9IjIiLz4KICA8cmVjdCB4PSIxMjAiIHk9Ijk1IiB3aWR0aD0iMTYwIiBoZWlnaHQ9IjIxMCIgcng9IjEwIiBmaWxsPSJub25lIiBzdHJva2U9IiMwRjc2NkUiIHN0cm9rZS13aWR0aD0iMTAiLz4KICA8cmVjdCB4PSIxNjUiIHk9IjgwIiB3aWR0aD0iNzAiIGhlaWdodD0iMjYiIHJ4PSI2IiBmaWxsPSIjRjBGREZBIiBzdHJva2U9IiMwRjc2NkUiIHN0cm9rZS13aWR0aD0iOCIvPgogIDxwYXRoIGQ9Ik0gMTUwIDE0NSBMIDE2MiAxNTcgTCAxODUgMTMwIiBmaWxsPSJub25lIiBzdHJva2U9IiMwRjc2NkUiIHN0cm9rZS13aWR0aD0iOCIgc3Ryb2tlLWxpbmVjYXA9InJvdW5kIiBzdHJva2UtbGluZWpvaW49InJvdW5kIi8+CiAgPGxpbmUgeDE9IjIwMCIgeTE9IjE0MyIgeDI9IjI1MiIgeTI9IjE0MyIgc3Ryb2tlPSIjMEY3NjZFIiBzdHJva2Utd2lkdGg9IjgiIHN0cm9rZS1saW5lY2FwPSJyb3VuZCIvPgogIDxwYXRoIGQ9Ik0gMTUwIDE5NSBMIDE2MiAyMDcgTCAxODUgMTgwIiBmaWxsPSJub25lIiBzdHJva2U9IiMwRjc2NkUiIHN0cm9rZS13aWR0aD0iOCIgc3Ryb2tlLWxpbmVjYXA9InJvdW5kIiBzdHJva2UtbGluZWpvaW49InJvdW5kIi8+CiAgPGxpbmUgeDE9IjIwMCIgeTE9IjE5MyIgeDI9IjI1MiIgeTI9IjE5MyIgc3Ryb2tlPSIjMEY3NjZFIiBzdHJva2Utd2lkdGg9IjgiIHN0cm9rZS1saW5lY2FwPSJyb3VuZCIvPgogIDxwYXRoIGQ9Ik0gMTUwIDI0NSBMIDE2MiAyNTcgTCAxODUgMjMwIiBmaWxsPSJub25lIiBzdHJva2U9IiMwRjc2NkUiIHN0cm9rZS13aWR0aD0iOCIgc3Ryb2tlLWxpbmVjYXA9InJvdW5kIiBzdHJva2UtbGluZWpvaW49InJvdW5kIi8+CiAgPGxpbmUgeDE9IjIwMCIgeTE9IjI0MyIgeDI9IjI1MiIgeTI9IjI0MyIgc3Ryb2tlPSIjMEY3NjZFIiBzdHJva2Utd2lkdGg9IjgiIHN0cm9rZS1saW5lY2FwPSJyb3VuZCIvPgo8L3N2Zz4K" width="180" alt="Logo LMSGI"/>

<h1>Unitat 3</h1>
<h2>Formularis avançats i validació en HTML</h2>

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

1. Dels formularis bàsics als avançats
   - 1.1 Repàs ràpid: `<form>`, `<label>`, `<input>`
   - 1.2 Agrupar i organitzar: `<fieldset>` i `<legend>`
2. Tipus de camp i controls d'HTML5
3. Validació nativa de formularis
   - 3.1 Restriccions bàsiques: obligatorietat, longitud i rang
   - 3.2 Patrons amb expressions regulars
   - 3.3 L'estat de validació, a l'espera de CSS
4. Enviament de dades: `method` i `action`
5. Elements semàntics d'HTML5
6. Resum de la unitat
7. Per a saber-ne més

<div style="page-break-after: always;"></div>

**RA cobert:** RA2 — *Utiliza lenguajes de marcas para la transmisión y presentación de información a través de la Web, analizando la estructura de los documentos e identificando sus elementos* (CA 2b, 2c)

> 💡 **Nota d'estudi**: en la UD2 ja vau escriure un formulari bàsic (`<form>`, `<label>`, un grapat d'`<input>`) a manera d'avanç. Aquesta unitat el retoma justament ací: els mateixos formularis, però amb tot el vocabulari de camps que oferix HTML5, validació automàtica sense escriure ni una línia de JavaScript, i les etiquetes que donen significat a cada bloc d'una pàgina. Com en la UD2, és una unitat sobretot pràctica — la teoria és la mínima perquè sapieu *per què* funciona cada cosa.

---

## 1. Dels formularis bàsics als avançats

### 1.1 Repàs ràpid: `<form>`, `<label>`, `<input>` (CA 2b, 2c)

**🧪 Pas a pas — Retoma el teu formulari de la UD2**

1. Obri la carpeta `LMSGI/UD02` (o on guardares `inscripcion.html` en l'exercici 4 de la UD2). Si no el tens a mà, crea'n un de nou amb aquest contingut de partida:

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

2. Copia aquesta carpeta completa a una de nova, `LMSGI/UD03`, i treballa a partir d'ací durant tota la unitat.

Recorda el que ja sabeu de la UD2: `<form>` embolica tot el formulari; `<label for="...">` associa un text a un camp pel seu `id` (accessibilitat i clic en el text); `<input>` és el camp en si, i el seu atribut `type` decidix què es pot escriure. El que **no** vam veure en detall va ser `name`, i ara sí que toca: és l'identificador amb què viatja cada dada en enviar-se — l'usareu en el punt 4.

⚠️ **Error típic**: confondre el `<label>` amb el `placeholder` d'un `<input>` (ho veureu en el punt 2). El `<label>` és el nom permanent del camp — seguix visible encara que escrigues dins —, mentre que el `placeholder` és un text d'ajuda que **desapareix** en el moment que comences a escriure. Un formulari només amb `placeholder` i sense `<label>` és un problema d'accessibilitat: un lector de pantalla no té res a anunciar en enfocar el camp.

---

### 1.2 Agrupar i organitzar: `<fieldset>` i `<legend>` (CA 2c)

Un formulari amb molts camps és més fàcil d'entendre si es divideix en blocs amb sentit. Per a això existixen `<fieldset>` (l'agrupació) i `<legend>` (el seu títol):

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

Per defecte el navegador dibuixa un marc al voltant de cada `<fieldset>` amb el text de `<legend>` incrustat en la vora superior — purament visual, sense necessitat de CSS. `<fieldset>` és un element de bloc més, com els `<div>` que ja coneixeu de la UD2, només que pensat específicament per a agrupar camps de formulari.

**🧪 Exercici 1 — Organitza la teua inscripció**

Sobre el teu `inscripcion.html` de la UD2 (ja copiat a `UD03`): agrupa els camps en almenys dos `<fieldset>` amb la seua `<legend>` corresponent (per exemple "Datos personales" i "Preferencias del curso"). Guarda i comprova en Firefox que apareixen els dos marcs amb el seu títol.

---

## 2. Tipus de camp i controls d'HTML5 (CA 2c)

En la UD2 només vau usar `type="text"`, `type="email"`, `type="number"` i `type="checkbox"`. HTML5 va ampliar molt aquesta llista — cada tipus no és només una etiqueta distinta: canvia el **teclat o control que oferix el navegador**, i en diversos casos activa una validació bàsica automàtica (ho veureu en detall en el punt 3).

| `type` | Què oferix el navegador | Exemple d'ús |
|---|---|---|
| `text` | Caixa de text lliure (la que ja coneixeu) | Nom, adreça |
| `email` | Teclat amb `@` en mòbil; exigix un format tipus correu | Correu electrònic |
| `password` | Oculta els caràcters en escriure | Contrasenyes |
| `number` | Fletxes per a pujar/baixar; teclat numèric en mòbil | Edat, quantitat |
| `tel` | Teclat numèric en mòbil (no valida format, varia per país) | Telèfon |
| `url` | Exigix un format tipus `https://...` | Pàgina web personal |
| `date` | Selector de calendari natiu | Data de naixement |
| `time` | Selector d'hora natiu | Hora d'una cita |
| `color` | Selector de color natiu (paleta del sistema operatiu) | Triar un color favorit |
| `range` | Control lliscant entre un mínim i un màxim | Valorar de l'1 al 10 |
| `search` | Com `text`, però amb una "x" per a esborrar el contingut | Buscador intern |
| `file` | Botó per a seleccionar un arxiu de l'equip | Pujar una foto |
| `hidden` | No es mostra — envia un valor fix sense que l'usuari el vega | Un identificador intern |

> 📡 **Seguix vigent i molt usat hui**: abans d'HTML5, tot açò calia "simular-ho" amb JavaScript (un selector de data fet a mà, validar un email amb una expressió regular escrita pel programador...). Que el mateix navegador ho resolga de fàbrica —gratis, accessible i amb el mateix aspecte natiu del sistema operatiu de l'usuari— és una de les millores més usades d'HTML5 en el desenvolupament web real.

**Altres controls, més enllà de `<input>`:**

- **`<textarea>`**: per a text llarg de diverses línies — un `<input type="text">` només admet una línia. Es controla la mida amb `rows` (files) i `cols` (columnes), i el text va **entre** les etiquetes, no en un atribut `value`:
  ```html
  <label for="comentario">Comentario:</label><br>
  <textarea id="comentario" name="comentario" rows="5" cols="40">Escribe aquí...</textarea>
  ```
- **`<select>` / `<option>`**: una llista desplegable amb opcions tancades — a diferència del `radio` que ja coneixeu de la UD2 (on es veuen totes les opcions alhora), ací només es veu una fins que l'usuari despleg la llista. Útil quan hi ha moltes opcions:
  ```html
  <label for="modulo">Módulo favorito:</label>
  <select id="modulo" name="modulo">
    <option value="lmsgi">LMSGI</option>
    <option value="bd">Bases de Datos</option>
    <option value="prog">Programación</option>
  </select>
  ```
  L'atribut `value` de cada `<option>` és el que s'envia realment; el text entre `<option>` i `</option>` és només el que veu l'usuari — igual que passava amb l'`id`/etiqueta visible en altres elements.
- **`<datalist>`**: una llista de suggeriments per a un `<input>` normal — a mig camí entre text lliure i `<select>`, l'usuari pot escriure el que vulga o triar un dels suggeriments:
  ```html
  <label for="ciudad">Ciudad:</label>
  <input type="text" id="ciudad" name="ciudad" list="ciudades">
  <datalist id="ciudades">
    <option value="Algemesí">
    <option value="Valencia">
    <option value="Alzira">
  </datalist>
  ```
  L'`<input>` es connecta al `<datalist>` per l'atribut `list`, que apunta a l'`id` del `<datalist>` — el mateix mecanisme de `for`/`id` que ja useu amb `<label>`.

**🧪 Exercici 2 — Explora els tipus de camp**

En el teu `inscripcion.html`, dins del `fieldset` de "Preferencias" (o un de nou), afig:
1. Un camp `type="date"` per a la data de naixement.
2. Un camp `type="range"` amb una etiqueta que demane valorar el mòdul de l'1 al 10.
3. Un `<select>` amb almenys 3 `<option>` per a triar el mòdul favorit (substituint el camp de text lliure que teníeu).
4. Un `<textarea>` de 4 files per a "comentaris addicionals".

Guarda i obri'l en Firefox. Fes clic en el camp de data i en el de rang: fixa't que el navegador dibuixa un control complet (calendari, lliscador) sense que hàgeu escrit res de JavaScript.

---

## 3. Validació nativa de formularis (CA 2c)

### 3.1 Restriccions bàsiques: obligatorietat, longitud i rang

HTML5 permet que el mateix navegador comprove si les dades són correctes **abans** d'enviar el formulari, sense necessitar JavaScript. Es fa afegint atributs a l'`<input>`:

| Atribut | Què fa | Exemple |
|---|---|---|
| `required` | El camp no pot quedar buit | `<input type="text" required>` |
| `minlength` / `maxlength` | Longitud mínima/màxima de caràcters (text) | `<input type="text" minlength="3" maxlength="20">` |
| `min` / `max` | Valor mínim/màxim (números, dates, rangs) | `<input type="number" min="0" max="120">` |
| `step` | L'increment permés en camps numèrics | `<input type="number" step="5">` (només múltiples de 5) |
| `placeholder` | Text d'ajuda que desapareix en escriure (⚠️ vist en el punt 1: mai no substituïx el `<label>`) | `<input type="text" placeholder="Ej: Ana">` |
| `readonly` | Es pot veure i seleccionar, però no editar | `<input type="text" value="Fijo" readonly>` |
| `disabled` | El camp queda inactiu i **no s'envia** amb el formulari | `<input type="text" disabled>` |

Prova-ho:

```html
<label for="nombre">Nombre:</label>
<input type="text" id="nombre" name="nombre" required minlength="2" maxlength="30"><br>

<label for="edad">Edad:</label>
<input type="number" id="edad" name="edad" min="14" max="99" required><br>
```

Si ara premeu "Enviar" deixant el nom buit, o escrivint una edat de 200, el navegador **bloqueja l'enviament** i mostra un missatge automàtic assenyalant el camp — sense que hàgeu escrit ni una línia de codi per a eixe missatge.

⚠️ **Important — no és una mesura de seguretat**: aquesta validació s'executa en el mateix navegador de l'usuari, així que es pot saltar fàcilment (n'hi ha prou amb desactivar JavaScript de certes maneres, editar l'HTML amb les eines de desenvolupador, o enviar la petició directament sense passar pel formulari). Servix per a donar una resposta immediata i còmoda a l'usuari que s'equivoca sense voler, **mai** per a protegir un sistema: la validació real i fiable sempre s'ha de repetir en el servidor que rep les dades, cosa que queda fora de l'abast d'aquest mòdul.

**🧪 Exercici 3 — Restriccions al teu formulari**

Afig al teu `inscripcion.html`: `required` al nom i al correu, `minlength="2"` al nom, i `min`/`max` raonables al camp de data de naixement o de valoració (`range`) que vas crear en l'exercici 2. Comprova en Firefox que el formulari no s'envia si deixes el nom buit, i que el missatge d'error apareix assenyalant exactament eixe camp.

---

### 3.2 Patrons amb expressions regulars (CA 2c)

Quan `required`, `min`/`max` o `minlength` no basten per a descriure un format concret (per exemple, un codi postal de 5 xifres, o un DNI amb lletra), s'usa l'atribut `pattern` amb una **expressió regular**:

```html
<label for="cp">Código postal:</label>
<input type="text" id="cp" name="cp" pattern="[0-9]{5}" title="5 dígitos, por ejemplo 46680">
```

- `[0-9]{5}` significa "exactament 5 caràcters, cadascun un dígit del 0 al 9".
- L'atribut `title` no és decoratiu ací: molts navegadors el mostren dins del missatge d'error automàtic quan el patró no coincidix — és la manera d'explicar a l'usuari *quin* format s'espera.

> 💡 Les expressions regulars (*regex*) són un llenguatge en si mateix per a descriure patrons de text, amb la seua pròpia sintaxi (`[0-9]` un dígit, `{5}` exactament 5 vegades, `+` una o més vegades, `?` opcional...). No és contingut d'aquesta unitat dominar-les a fons — de moment n'hi ha prou amb reconéixer i adaptar patrons senzills com el de l'exemple. Podeu recolzar-vos en la referència de patrons de MDN (enllaç al final de la unitat) per a copiar i adaptar expressions ja fetes, en compte d'escriure-les de zero.

**🧪 Exercici 4 — Un patró per al teu formulari**

Afig un camp nou al teu `inscripcion.html` per a un "código de alumno" amb el patró `[A-Z]{2}[0-9]{4}` (dues lletres majúscules seguides de 4 dígits, per exemple `AS1234`). Afig un `title` explicant el format esperat, i comprova en Firefox què passa si escrius `as12` o `AS12345`.

---

### 3.3 L'estat de validació, a l'espera de CSS

Quan un camp complix les seues restriccions, el navegador el marca internament com a **vàlid**; si no les complix, com a **invàlid** — és el que consulta per a decidir si bloqueja l'enviament. Aquest estat també es pot usar per a donar estil visual al camp, amb els selectors CSS `:valid` i `:invalid`:

```css
input:invalid {
  border: 2px solid red;
}
input:valid {
  border: 2px solid green;
}
```

> 🕰️ **De moment, només un avanç**: encara no heu vist selectors CSS (arriben en la UD4), així que no cal que apliqueu aquest codi ara — només que sapieu que existix i que la validació d'aquest punt 3 no és només funcional, també es pot *veure*. Ho retomareu en la UD4 en estudiar les pseudoclasses.

---

## 4. Enviament de dades: `method` i `action` (CA 2b)

Fins ara els vostres formularis no enviaven les dades a cap lloc real. La destinació i la forma d'enviament es controlen amb dos atributs del mateix `<form>`:

```html
<form action="/procesar-inscripcion" method="post">
  ...
</form>
```

- **`action`**: la URL (recordeu el concepte de la UD1 — absoluta o relativa, igual que en els enllaços `<a href>` de la UD2) del recurs que rebrà les dades. Si s'omet, el formulari s'envia a la mateixa pàgina actual.
- **`method`**: com viatgen les dades. Els dos valors més habituals:

| `method` | Com viatgen les dades | Quan s'usa |
|---|---|---|
| `GET` | Van afegits a la URL, visibles, com una *query string* (`?nombre=Ana&edad=20`) | Cerques, filtres — dades que té sentit veure en la URL o guardar com a marcador |
| `POST` | Van "ocults" en el cos de la petició, no apareixen en la URL | Formularis amb dades sensibles o extenses — inscripcions, contrasenyes, pujar arxius |

**🧪 Pas a pas — Comprova-ho amb els teus propis ulls**

1. En el teu `inscripcion.html`, posa `method="get"` en el `<form>` (sense `action`, o amb `action=""`).
2. Omple el formulari i prem "Enviar". Fixa't en la barra d'adreces de Firefox: voràs alguna cosa com `.../inscripcion.html?nombre=Ana&edad=20&modulo=lmsgi...`
3. Canvia ara a `method="post"` i repetix l'enviament. Quina diferència veus en la barra d'adreces aquesta vegada?

⚠️ Ni amb `GET` ni amb `POST` arriba a existir encara un "procés servidor" real que reba i guarde eixes dades — açò requeriria un programa del costat del servidor (PHP, Node, Python...), que queda fora del contingut d'aquest mòdul. El que heu comprovat amb el pas a pas és únicament **com viatgen** les dades, no què es fa amb elles en arribar.

**🧪 Exercici 5 — GET o POST, raonat**

Per a cadascun d'aquests formularis, indica si usaries `GET` o `POST` i justifica la teua resposta amb el vist en la taula: (a) un buscador de productes en una botiga online, (b) un formulari de canvi de contrasenya, (c) un formulari per a filtrar una taula d'alumnes per mòdul.

---

## 5. Elements semàntics d'HTML5 (CA 2c)

En la UD2 ja vau construir pàgines amb `<div>` i `<span>` — contenidors genèrics que no diuen res sobre *què és* cada bloc, només que existix. HTML5 va afegir un conjunt d'etiquetes que sí que ho diuen: els **elements semàntics**.

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

| Etiqueta | Per a què servix |
|---|---|
| `<header>` | Capçalera de la pàgina o d'una secció — logo, títol, navegació principal |
| `<nav>` | Un bloc d'enllaços de navegació |
| `<main>` | El contingut principal de la pàgina — només n'hi pot haver un per document |
| `<article>` | Una peça de contingut independent, que tindria sentit per si sola (una notícia, un post) |
| `<section>` | Una secció temàtica dins d'un document o `<article>`, normalment amb el seu propi títol |
| `<aside>` | Contingut relacionat però secundari — una barra lateral, una nota destacada |
| `<footer>` | Peu de pàgina o de secció — dades de contacte, llicència, enllaços relacionats |
| `<address>` | Informació de contacte de l'autor — el navegador sol mostrar-la en cursiva |

> 📡 **Per què açò no és només estètica**: en la UD2 (apartat "Per a saber-ne més") ja vam avançar que la normativa europea d'accessibilitat digital (Directiva (UE) 2019/882) obliga bona part de les webs d'administracions i empreses a complir criteris WCAG. Usar `<nav>` en compte d'un `<div class="nav">` no canvia res visualment per defecte, però sí per a un lector de pantalla: anuncia "navegació" en compte d'una caixa genèrica sense significat, exactament el mateix tipus de detall que l'`alt` de les imatges o el `<label for>` dels formularis que ja coneixeu. També ajuda que els buscadors entenguen millor l'estructura de la pàgina en indexar-la.

⚠️ **No substituïxen `<div>`/`<span>`, els complementen**: seguiu usant `<div>` i `<span>` per a agrupar contingut que no encaixa en cap d'aquestes categories amb significat propi — no cal forçar un `<section>` on només fa falta una caixa per a aplicar estils.

**🧪 Exercici 6 — Semantitza la teua fitxa d'alumne**

Recupera `ficha-alumno.html` de la UD2 (exercici 2). Reestructura'l usant elements semàntics: un `<header>` amb el nom de l'alumne, un `<main>` que continga la llista de mòduls i la taula de notes, i un `<footer>` amb un enllaç a la web del centre. El contingut no canvia — només les etiquetes que l'embolcallen.

---

## 🎯 Repte de classe — Fitxa d'inscripció completa

Amb tot el vist en aquesta unitat, crea un arxiu nou `inscripcion-final.html` que combine:

1. **Estructura semàntica**: `<header>` amb un títol, `<main>` amb el formulari, `<footer>` amb un enllaç de tornada a `ficha-alumno.html`.
2. **Formulari organitzat** en almenys dos `<fieldset>` amb `<legend>` ("Datos personales" i "Preferencias", per exemple).
3. **Almenys 6 tipus de camp distints** entre `type="text"`, `email`, `date`, `range`, `<select>`, `<textarea>` i `<datalist>`.
4. **Validació nativa**: `required` en almenys dos camps, un `pattern` amb expressió regular en un d'ells (amb el seu `title` explicatiu), i un `min`/`max` raonable en el de tipus numèric o rang.
5. **Enviament de dades**: decidix tu, justificant la teua elecció per escrit en un comentari HTML al principi de l'arxiu, si usaràs `method="get"` o `method="post"` per a aquest formulari en concret.

Comprova-ho en Firefox: que l'enviament es bloquege si falta un camp obligatori o si el patró no coincidix, i que cada `fieldset` es veja agrupat visualment.

---

## Resum de la unitat

**1. Dels formularis bàsics als avançats** *(CA 2b, 2c)* Repàs de `<form>`, `<label for>` i `<input>` de la UD2, amb l'atribut `name` ja explicat. Agrupació de camps amb `<fieldset>` i `<legend>`.

**2. Tipus de camp i controls d'HTML5** *(CA 2c)* Més d'una dotzena de tipus d'`<input>` (`email`, `date`, `range`, `color`...) que activen controls natius del navegador sense JavaScript. `<textarea>` per a text llarg, `<select>`/`<option>` per a llistes tancades, `<datalist>` per a suggeriments sobre un camp lliure.

**3. Validació nativa de formularis** *(CA 2c)* Restriccions declaratives (`required`, `minlength`/`maxlength`, `min`/`max`, `step`) i patrons amb expressions regulars (`pattern` + `title`) que bloquegen l'enviament i mostren un missatge automàtic — validació còmoda per a l'usuari, mai una mesura de seguretat real. Els estats `:valid`/`:invalid` queden avançats per a la UD4.

**4. Enviament de dades** *(CA 2b)* `action` (destinació) i `method` (`GET`, visible en la URL; `POST`, ocult en el cos) del `<form>` — sense necessitat encara d'un procés servidor real que les reba.

**5. Elements semàntics d'HTML5** *(CA 2c)* `<header>`, `<nav>`, `<main>`, `<article>`, `<section>`, `<aside>`, `<footer>`, `<address>` — donen significat a cada bloc de la pàgina, més enllà del que feia un `<div>` genèric, amb impacte directe en accessibilitat i en com indexen la pàgina els buscadors.

---

## 📚 Per a saber-ne més (opcional, no avaluable)

### Per a què et servirà el d'aquesta unitat?

El que heu vist ací (camps avançats, validació nativa, semàntica) és la base de qualsevol formulari web real. La validació real i segura d'aquestes dades —la que de veritat protegix un sistema— la veureu amb JavaScript en la **UD6** (manipulació de documents web), i les pseudoclasses `:valid`/`:invalid` del punt 3.3 es retomen en la **UD4**, en estudiar selectors CSS.

A data d'aquest curs (2026-2027), convé saber:

- **La validació nativa seguix guanyant terreny**: cada versió dels navegadors afig nous tipus d'`<input>` i atributs de validació, reduint la necessitat de JavaScript per a casos senzills — és una tendència activa, no un estàndard tancat des de fa anys.
- **Accessibilitat, cada vegada més exigida per llei**: com ja es va apuntar en la UD2, la normativa europea (Directiva (UE) 2019/882) obliga a auditar criteris WCAG en webs d'administracions i empreses — un `<label for>` ben associat o un `<nav>` en compte d'un `<div>` són exactament el tipus de detall auditat, i ja els heu usat en aquesta unitat.
- **Frameworks de formularis**: en projectes grans (sobretot amb JavaScript, que veureu en la UD6) és habitual recolzar-se en llibreries que gestionen la validació i l'enviament de formularis de manera més avançada — però totes elles parteixen exactament dels atributs HTML natius vistos ací, no els substituïxen.

- MDN — Formularis HTML: https://developer.mozilla.org/es/docs/Learn/Forms
- MDN — Referència de patrons d'expressions regulars: https://developer.mozilla.org/es/docs/Web/HTML/Attributes/pattern
- W3Schools — Tipus de `<input>`: https://www.w3schools.com/html/html_form_input_types.asp
</content>
