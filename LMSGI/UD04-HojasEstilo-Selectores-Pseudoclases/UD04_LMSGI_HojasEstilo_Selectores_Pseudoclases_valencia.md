<div style="text-align: center;">

<img src="data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCA0MDAgNDAwIiB3aWR0aD0iMTgwIiBoZWlnaHQ9IjE4MCI+CiAgPGNpcmNsZSBjeD0iMjAwIiBjeT0iMjAwIiByPSIxNzAiIGZpbGw9IiNGMEZERkEiLz4KICA8Y2lyY2xlIGN4PSIyMDAiIGN5PSIyMDAiIHI9IjE3MCIgZmlsbD0ibm9uZSIgc3Ryb2tlPSIjOTlGNkU0IiBzdHJva2Utd2lkdGg9IjIiLz4KICA8cmVjdCB4PSIxMDAiIHk9IjExMCIgd2lkdGg9IjkwIiBoZWlnaHQ9IjkwIiByeD0iOCIgZmlsbD0ibm9uZSIgc3Ryb2tlPSIjMEY3NjZFIiBzdHJva2Utd2lkdGg9IjEwIi8+CiAgPGNpcmNsZSBjeD0iMTQ1IiBjeT0iMTU1IiByPSI0NSIgZmlsbD0ibm9uZSIgc3Ryb2tlPSIjMEY3NjZFIiBzdHJva2Utd2lkdGg9IjEwIiBvcGFjaXR5PSIwLjQiLz4KICA8cmVjdCB4PSIyMTAiIHk9IjIwMCIgd2lkdGg9IjkwIiBoZWlnaHQ9IjkwIiByeD0iOCIgZmlsbD0iIzBGNzY2RSIgb3BhY2l0eT0iMC4xNSIvPgogIDxyZWN0IHg9IjIxMCIgeT0iMjAwIiB3aWR0aD0iOTAiIGhlaWdodD0iOTAiIHJ4PSI4IiBmaWxsPSJub25lIiBzdHJva2U9IiMwRjc2NkUiIHN0cm9rZS13aWR0aD0iMTAiLz4KICA8bGluZSB4MT0iMTgwIiB5MT0iMTcwIiB4Mj0iMjQwIiB5Mj0iMjMwIiBzdHJva2U9IiMwRjc2NkUiIHN0cm9rZS13aWR0aD0iNiIgc3Ryb2tlLWRhc2hhcnJheT0iMTAgOCIvPgo8L3N2Zz4K" width="180" alt="Logotip LMSGI"/>

<h1>Unitat 4</h1>
<h2>Fulls d'estil. Selectors. Pseudoclasses</h2>

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

1. Separar contingut i presentació: què és CSS
2. Vincular CSS a un HTML: en línia, intern i extern
3. Sintaxi bàsica: regles, propietats i valors
4. Selectors bàsics: universal, tipus, classe, id
5. Combinació de selectors
6. Selectors d'atribut
7. Pseudoclasses i pseudoelements
8. CSS dinàmic: variables personalitzades
9. Resum de la unitat
10. Per a saber-ne més

<div style="page-break-after: always;"></div>

**RA cobert:** RA2 — *Utilitza llenguatges de marques per a la transmissió i presentació d'informació a través de la web, analitzant l'estructura dels documents i identificant els seus elements*

⚠️ **Nota d'alineació curricular**: esta unitat cobrix un únic bloc de contingut de la programació (fulls d'estil: aspectes bàsics, propietats, CSS dinàmic, selectors, combinació de selectors, classes, atributs, pseudoclasses/pseudoelements), però el codi de CA amb què s'identifica eixe bloc **no és el mateix en ambdós cicles**: en **ASIX (RD 1629/2009)** és **CA 2g-2h**, i en **DAW (RD 405/2023)** és **CA 2f-2g**. Com que la programació no desglossa eixe bloc punt per punt, esta unitat no reparteix CA per apartat — tota ella queda coberta baix el CA corresponent a cada cicle, indicat ací una sola vegada.

> 💡 **Nota d'estudi**: en la UD1 i la UD2 ja vas veure que la independència i la separació entre contingut i presentació són avantatges dels llenguatges de marques. Esta unitat és on eixa idea es fa concreta: **CSS** és la ferramenta que fa possible eixa separació en la pràctica. Tot el que apregues ací es recolza directament en l'HTML que ja saps escriure.

---

## 1. Separar contingut i presentació: què és CSS

Fins ara, l'única manera que has tingut de canviar l'aspecte d'un HTML ha sigut amb l'atribut `style` (algun exemple solt en unitats anteriors) o deixant que el navegador aplique el seu estil per defecte (`<h1>` gran, `<p>` normal...). Açò funciona, però barreja dos coses que convé mantindre separades: **què és** el contingut (HTML) i **com es veu** (presentació).

**CSS** (*Cascading Style Sheets*, "fulls d'estil en cascada") és el llenguatge que resol açò: descriu l'aspecte visual d'un document marcat, sense tocar el seu contingut. És un llenguatge declaratiu, no un llenguatge de marques — no té etiquetes `<...>`, sinó **regles** que diuen "a este element, aplica-li este aspecte".

> 🕰️ **Per què existix**: en els primers anys de la web (mitjans dels 90), l'única manera de donar color o grandària a un text era ficant eixa informació dins del propi HTML, etiqueta a etiqueta (`<font color="red" size="5">`). Si volies canviar el color de tots els títols d'una web de 200 pàgines, havies d'editar les 200 pàgines una a una. El W3C va publicar CSS en 1996 precisament per a separar les dos coses: l'HTML descriu l'estructura, CSS descriu l'aspecte, i canviar un color de tota la web passa a ser una única línia.

**Per què importa separar açò, amb un cas molt real:**

- Un únic arxiu CSS pot aplicar-se a **desenes de pàgines HTML** alhora — canvies un color en un lloc i s'actualitza en tot el lloc web.
- Un mateix HTML pot vore's distint segons el dispositiu (mòbil, ordinador, impressora) sense tocar el contingut — només canviant quin CSS s'aplica.
- L'HTML queda més net i fàcil de mantindre — sense atributs `style` repetits per tot arreu.

**🧪 Exercici 1 — Abans i després**
Escriu en Mousepad un HTML senzill (un `<h1>`, dos `<p>` i una `<ul>` amb 3 elements) utilitzant l'atribut `style` per a posar colors i grandàries directament en cada etiqueta, com es feia abans de CSS. Compta quantes vegades repeteixes la paraula `style`. Guarda l'arxiu com `antes.html` — el reescriurem amb CSS de veres en l'Exercici 2, per a comparar.

---

## 2. Vincular CSS a un HTML: en línia, intern i extern

Hi ha tres maneres d'aplicar CSS a un document, i no són intercanviables — cadascuna té el seu ús:

| Forma | Com s'escriu | Quan s'utilitza |
|---|---|---|
| **En línia** (*inline*) | Atribut `style` dins de la pròpia etiqueta | Quasi mai en codi real — només proves ràpides o estils generats dinàmicament per JavaScript |
| **Intern** | Bloc `<style>` dins del `<head>` de l'HTML | Una pàgina aïllada, sense més pàgines que compartisquen estil |
| **Extern** | Arxiu `.css` a banda, enllaçat amb `<link>` | La manera normal de treballar — el mateix arxiu `.css` servix per a totes les pàgines del lloc |

**En línia** (la que evitem a partir d'ara):
```html
<h1 style="color: teal; font-size: 32px;">Título</h1>
```

**Intern**:
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

**Extern** — el que utilitzaràs en la resta de la unitat i del mòdul:

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

⚠️ **Ruta del `href`**: és relativa a on està l'HTML, igual que les rutes d'imatges que ja coneixes. Si `estilos.css` està en la mateixa carpeta que `index.html`, n'hi ha prou amb el nom de l'arxiu; si està en una subcarpeta `css/`, seria `href="css/estilos.css"`.

**🧪 Exercici 2 — De `style` a arxiu extern**
Reescriu el `antes.html` de l'Exercici 1 en dos arxius: `index.html` (només estructura, sense cap atribut `style`) i `estilos.css` (totes les regles de color i grandària que abans estaven repetides). Enllaça'ls amb `<link>` i obri'l amb Firefox — ha de vore's exactament igual que `antes.html`. Compta ara quantes vegades apareix la paraula `style` en `index.html`.

---

## 3. Sintaxi bàsica: regles, propietats i valors

Una regla CSS té sempre la mateixa forma:

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

- **Selector** (`p`): a quin element o elements s'aplica la regla — ho veiem en detall en els punts 4-6.
- **Declaració** (`color: #1e293b;`): una parella `propietat: valor;`, sempre acabada en punt i coma.
- **Bloc de declaracions** (tot el que va entre `{` i `}`): el conjunt de declaracions que s'apliquen a eixe selector.

**Algunes propietats habituals, per a tindre referència des d'ara:**

| Propietat | Per a què servix | Exemple de valor |
|---|---|---|
| `color` | Color del text | `red`, `#ff0000`, `rgb(255, 0, 0)` |
| `background-color` | Color de fons | `#f0fdfa` |
| `font-size` | Grandària de lletra | `16px`, `1.2em`, `1rem` |
| `font-weight` | Gruix de la lletra | `normal`, `bold`, `700` |
| `text-align` | Alineació del text | `left`, `center`, `right` |
| `margin` | Espai fora de l'element | `10px`, `10px 20px` |
| `padding` | Espai dins de l'element, abans de la vora | `10px` |
| `border` | Vora de l'element | `1px solid #ccc` |

> 💡 **Els comentaris en CSS** s'escriuen `/* així */`, mai amb `//` ni amb `<!-- -->` (açò és HTML/XML, no CSS — cada llenguatge té la seua pròpia sintaxi de comentari, com ja vas veure en la UD1).

**El nom "cascada" no és casualitat.** Quan diverses regles afecten el mateix element, CSS decidix quina guanya seguint un ordre de prioritat: primer l'**especificitat** del selector (un id pesa més que una classe, i una classe pesa més que una etiqueta — ho veuràs amb les classes i els id en el punt 4), i si hi ha empat, guanya la **regla que apareix més avall** en l'arxiu. Per això l'ordre en què escrius les regles dins d'un `.css` sí que importa quan hi ha conflicte.

**🧪 Exercici 3 — Troba el guanyador**
Donat este CSS:
```css
p { color: blue; }
p { color: green; }
.aviso { color: red; }
```
i este HTML: `<p class="aviso">Texto de prueba</p>`, de quin color es veurà el text? Raona la teua resposta aplicant el que acabes de llegir sobre la cascada (sense utilitzar encara el concepte de "classe" del punt 4 — de moment fia't que `.aviso` selecciona eixe paràgraf).

---

## 4. Selectors bàsics: universal, tipus, classe, id

El **selector** decidix a quina part de l'HTML s'aplica una regla. Estos quatre són la base de tota la resta:

| Selector | Sintaxi | Selecciona | Especificitat |
|---|---|---|---|
| **Universal** | `*` | Tots els elements del document | La més baixa |
| **De tipus** (o d'etiqueta) | `p`, `h1`, `li` | Tots els elements d'eixa etiqueta | Baixa |
| **De classe** | `.nombre-clase` | Tots els elements amb `class="nombre-clase"` | Mitjana |
| **D'id** | `#nombre-id` | L'únic element amb `id="nombre-id"` | Alta |

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

⚠️ **Classe vs. id, la diferència que importa**: un `id` ha de ser **únic** en tot el document (no pot haver-hi dos elements amb el mateix id); una `class` es pot repetir en tants elements com vulgues, i un mateix element pot tindre diverses classes alhora separades per espais: `class="destacado urgente"`.

> 📡 **Seguix vigent**: en la pràctica moderna, les classes són amb diferència el selector més utilitzat per a donar estil — l'id es reserva quasi sempre per a altres coses, com ser el destí d'un enllaç intern (`<a href="#intro">`) o ser localitzat per JavaScript (`document.getElementById(...)`, ho veuràs en la UD6), no tant per a aplicar estil directament.

**🧪 Exercici 4 — Estil per a un panell d'estat**
Crea un HTML amb 4 elements `<p>`: dos amb `class="ok"`, un amb `class="alerta"`, i un d'ells a més amb `id="principal"`. Escriu el CSS perquè: tots els `<p>` tinguen `padding: 8px` (selector de tipus), els de classe `ok` tinguen fons verd clar, el de classe `alerta` tinga fons roig clar, i el que té `id="principal"` tinga a més el text en negreta, siga de la classe que siga. Comprova-ho en el navegador i explica quina regla guanya en l'element que té tant `id="principal"` com una classe de color, i per què.

---

## 5. Combinació de selectors

Els selectors bàsics es poden combinar per a apuntar amb més precisió, sense haver d'afegir una classe a cada element:

| Combinador | Sintaxi | Selecciona |
|---|---|---|
| **Descendent** | `article p` | Tots els `<p>` dins d'un `<article>`, a qualsevol profunditat |
| **Fill directe** | `article > p` | Només els `<p>` que són fills **directes** d'un `<article>`, no els que estan més imbricats |
| **Germà adjacent** | `h2 + p` | El `<p>` que va **just després** d'un `<h2>` |
| **Agrupació** | `h1, h2, h3` | Aplica la mateixa regla a diversos selectors alhora, evitant repetir el bloc |

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

Amb este CSS: **ambdós** `<p>` reben el color gris fosc (són descendents d'`article`, a qualsevol nivell); només el primer `<p>` rep negreta (és fill directe d'`article`, el segon està dins d'un `<div>` pel mig); i només el primer `<p>` rep a més cursiva (és just el següent element després de l'`<h2>`).

**🧪 Exercici 5 — Diferència entre descendent i fill directe**
Parteix de l'HTML de dalt i afig un segon `<div>` amb un altre `<p>` dins, imbricat dos nivells (un `<div>` dins d'un altre `<div>`, i el `<p>` dins del més intern). Sense canviar el CSS de l'exemple, prediu per escrit quines regles afectaran este nou paràgraf i quines no, i després comprova-ho en el navegador.

---

## 6. Selectors d'atribut

Permeten seleccionar elements segons els atributs que tinguen, sense necessitat d'una classe específica per a això — molt útil, per exemple, amb formularis (els veuràs en detall en la UD3, però ja pots començar a donar-los estil).

| Selector | Selecciona elements que... |
|---|---|
| `[atributo]` | ...tenen eixe atribut, siga quin siga el seu valor |
| `[atributo="valor"]` | ...tenen eixe atribut amb exactament eixe valor |
| `[atributo^="valor"]` | ...tenen eixe atribut i el seu valor **comença** per eixe text |
| `[atributo$="valor"]` | ...tenen eixe atribut i el seu valor **acaba** per eixe text |

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

Ací l'`<input>` de tipus `email` rep una vora distinta, i només l'enllaç que comença per `https://` (l'extern) rep un color distint — molt pràctic per a avisar visualment de quins enllaços ixen del lloc, sense haver d'etiquetar cadascun a mà amb una classe.

**🧪 Exercici 6 — Estil per atribut**
Crea un formulari senzill amb tres `<input>`: un `type="text"`, un `type="email"` i un `type="password"`. Amb selectors d'atribut (sense utilitzar cap classe), dona a cada tipus un color de vora distint.

---

## 7. Pseudoclasses i pseudoelements

Fins ara tots els selectors apunten a elements que ja estan en l'HTML tal com són. Les **pseudoclasses** i els **pseudoelements** van un pas més enllà: seleccionen un element en un **estat concret**, o una **part** d'un element que no té la seua pròpia etiqueta.

**Pseudoclasses** (s'escriuen amb `:`) — seleccionen un element segons el seu estat o la seua posició:

| Pseudoclasse | Selecciona |
|---|---|
| `:hover` | L'element mentre el ratolí està damunt |
| `:focus` | L'element mentre té el focus (per exemple, un `<input>` en el qual estàs escrivint) |
| `:first-child` | L'element que és el primer fill del seu pare |
| `:last-child` | L'element que és l'últim fill del seu pare |
| `:nth-child(n)` | L'element que ocupa la posició `n` entre els seus germans |

**Pseudoelements** (s'escriuen amb `::`) — seleccionen una part d'un element que no existix com a etiqueta pròpia:

| Pseudoelement | Selecciona |
|---|---|
| `::first-letter` | La primera lletra del contingut de l'element |
| `::before` | Permet inserir contingut generat just abans del contingut de l'element |
| `::after` | Permet inserir contingut generat just després del contingut de l'element |

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

⚠️ **Un sol `:` enfront de dos `::`** no és un caprici de sintaxi: `:hover` és un *estat* de l'element (una pseudoclasse), mentre que `::first-letter` és una *part* generada de l'element (un pseudoelement) que no pots seleccionar de cap altra manera, perquè no existix una etiqueta `<primera-letra>` en l'HTML. Els navegadors actuals toleren `:before`/`:after` amb un sol `:` per compatibilitat històrica, però la sintaxi correcta i la que has d'utilitzar és amb dos.

**🧪 Exercici 7 — Un botó que reacciona**
Crea un botó (`<button>`) amb un estil base (fons de color, text blanc, sense vora), i afig una regla `:hover` que canvie el fons a un to més fosc, i una regla `:focus` que li afija una vora visible. Després, aplica `:first-child` a una llista `<ul>` d'almenys 4 elements perquè el primer es veja distint dels altres (per exemple, en negreta).

---

## 8. CSS dinàmic: variables personalitzades

Quan un mateix color o mesura es repetix moltes vegades per tot un arxiu CSS (el color corporatiu d'una web, el mateix radi de vora en totes les targetes...), canviar-lo a mà implica editar cada aparició una per una. Les **variables CSS** (formalment, *custom properties*) resolen açò: es declaren una vegada i es reutilitzen on faça falta.

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

- `:root` és un selector especial que apunta a l'element arrel del document (equivalent, a efectes pràctics, a `<html>`) — és el lloc habitual on declarar variables que vols que estiguen disponibles en tot l'arxiu.
- Tota variable personalitzada comença per `--` (dos guions).
- S'utilitza amb la funció `var(--nombre-variable)`, en qualsevol declaració on encaixara eixe valor.

**Per què s'anomena "dinàmic"**: a diferència d'un valor fix (`color: #0f766e;` repetit 20 vegades), una variable es pot **canviar en un únic lloc** i tot el que la utilitza s'actualitza alhora — canvia `--color-principal` en `:root` i totes les targetes i botons de l'exemple canvien de color sense tocar les seues pròpies regles. És a més la base tècnica que fa possible, per exemple, un selector de tema clar/fosc canviant el valor de les variables segons una classe en `<html>`.

> 📡 **Per què importa hui**: és exactament el mecanisme que utilitzaries per al color corporatiu d'un dashboard de finances personals que definim una vegada i reutilitzem en cada targeta de despesa, cada botó i cada gràfic — canviar de marca o de tema visual es convertix en canviar unes poques línies en `:root`, en lloc de perseguir el mateix color per tot l'arxiu.

**🧪 Exercici 8 — Tema amb variables**
Retoma el botó i les targetes dels exercicis anteriors i substituïx tots els colors repetits per variables declarades en `:root` (almenys un color principal, un color de fons i un radi de vora). Després, canvia només el valor de les variables en `:root` i comprova que l'aspecte de tots els elements canvia alhora, sense tocar cap altra regla.

---

## 🎯 Repte de classe

Retoma qualsevol HTML que hages escrit en unitats anteriors (per exemple, el feed de podcast de la UD1, o un formulari de la UD3) i dona-li estil complet amb un arxiu `estilos.css` extern, utilitzant **almenys**: dos selectors de tipus, un selector de classe, un selector d'id, un combinador (descendent o fill directe), una pseudoclasse (`:hover` o `:focus`) i dos variables CSS personalitzades en `:root`. Res d'atributs `style` en l'HTML.

*Variació avaluable*: demanar a més que expliquen, per a tres de les regles que han escrit, quina especificitat té cada selector i per què, si hi haguera un conflicte entre dos de les seues pròpies regles, guanyaria una sobre l'altra.

---

<div style="page-break-after: always;"></div>

## Resum de la unitat

**1. Separar contingut i presentació** CSS és el llenguatge declaratiu que descriu l'aspecte visual d'un document marcat, separat del seu contingut — va nàixer en 1996 per a evitar repetir l'estil etiqueta a etiqueta per tot un lloc.

**2. Vincular CSS a un HTML** Tres maneres: en línia (atribut `style`, quasi mai s'utilitza), intern (`<style>` en el `<head>`) i extern (arxiu `.css` enllaçat amb `<link>`) — la manera normal de treballar, perquè un mateix arxiu servix per a totes les pàgines d'un lloc.

**3. Sintaxi bàsica** Una regla és `selector { propietat: valor; }`. Quan diverses regles afecten el mateix element, guanya la de major especificitat i, en empat, la que apareix més avall en l'arxiu — l'origen del nom "cascada".

**4. Selectors bàsics** Universal (`*`), de tipus (`p`), de classe (`.nombre`, reutilitzable) i d'id (`#nombre`, únic en el document) — amb especificitat creixent en eixe mateix ordre.

**5. Combinació de selectors** Descendent (`article p`), fill directe (`article > p`), germà adjacent (`h2 + p`) i agrupació (`h1, h2, h3`) per a apuntar amb precisió sense afegir classes a cada element.

**6. Selectors d'atribut** `[atributo]`, `[atributo="valor"]`, `[atributo^="valor"]`, `[atributo$="valor"]` — molt útils per a donar estil a formularis segons el tipus de camp.

**7. Pseudoclasses i pseudoelements** Les pseudoclasses (`:hover`, `:focus`, `:first-child`) seleccionen un estat o una posició; els pseudoelements (`::first-letter`, `::before`, `::after`) seleccionen una part generada de l'element que no té etiqueta pròpia.

**8. CSS dinàmic: variables personalitzades** Declarades en `:root` amb `--nombre` i utilitzades amb `var(--nombre)`, permeten canviar un valor repetit per tot un arxiu modificant una única línia.

---

## 📚 Per a saber-ne més (opcional, no avaluable)

El que s'ha vist ací és la base de selecció i sintaxi de CSS — la UD5 aprofundix en **layout** (Flex, Grid), **CSS responsive** i en el framework **Bootstrap**, que reutilitza exactament estos mateixos conceptes de selector, especificitat i cascada a major escala.

> 📡 **Actualitat**: les variables CSS (punt 8) porten sent compatibles en tots els navegadors moderns des de 2017 i hui són la manera estàndard de gestionar temes de color (clar/fosc) sense necessitat de JavaScript ni d'un preprocessador com Sass — cosa que fa uns anys sí que feia falta.

- Referència completa de propietats CSS (MDN): https://developer.mozilla.org/es/docs/Web/CSS/Reference
- Especificitat CSS explicada visualment: https://developer.mozilla.org/es/docs/Web/CSS/Specificity
