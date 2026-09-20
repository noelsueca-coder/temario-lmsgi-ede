<div style="text-align: center;">

<img src="data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCA0MDAgNDAwIiB3aWR0aD0iMTgwIiBoZWlnaHQ9IjE4MCI+CiAgPGNpcmNsZSBjeD0iMjAwIiBjeT0iMjAwIiByPSIxNzAiIGZpbGw9IiNGMEZERkEiLz4KICA8Y2lyY2xlIGN4PSIyMDAiIGN5PSIyMDAiIHI9IjE3MCIgZmlsbD0ibm9uZSIgc3Ryb2tlPSIjOTlGNkU0IiBzdHJva2Utd2lkdGg9IjIiLz4KICA8dGV4dCB4PSIyMDAiIHk9IjI0OCIgZm9udC1mYW1pbHk9IidDb3VyaWVyIE5ldycsIENvdXJpZXIsIG1vbm9zcGFjZSIgZm9udC1zaXplPSIxNTAiIGZvbnQtd2VpZ2h0PSI3MDAiIGZpbGw9IiMwRjc2NkUiIHRleHQtYW5jaG9yPSJtaWRkbGUiPiZsdDsvJmd0OzwvdGV4dD4KPC9zdmc+Cg==" width="180" alt="Logotip LMSGI"/>

<h1>Unitat 1</h1>
<h2>Introducció als llenguatges de marques</h2>

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

1. Què és un llenguatge de marques? Característiques generals (CA 1a)
2. Avantatges dels llenguatges de marques (CA 1b)
3. Origen i classificació dels llenguatges de marques (CA 1c)
4. XML com a llenguatge de marques de propòsit general (CA 1d-1i)
   - 4.1 Àmbits d'aplicació
   - 4.2 Estructura i sintaxi
   - 4.3 Documents ben formats
   - 4.4 Espais de noms
5. Resum de la unitat
6. Per a saber-ne més

<div style="page-break-after: always;"></div>

**RA cobert:** RA1 — *Reconeix les característiques dels llenguatges de marques analitzant i interpretant fragments de codi* (CA 1a-1i)

> 💡 **Nota d'estudi**: en esta unitat hi ha poca "teoria per a memoritzar" i moltes idees que necessites entendre per a poder programar després. Si un concepte no queda clar a la primera, el pots repassar pel teu compte — l'important és que sàpies *reconéixer* un llenguatge de marques i *escriure* un XML correcte al final de la unitat.

---

## 1. Què és un llenguatge de marques? Característiques generals (CA 1a)

Un **llenguatge de marques** (*markup language*) servix per a **donar format o estructura a un text**, inserint dins del propi text uns senyals especials anomenats **marques** (o *etiquetes*), normalment tancades entre `<` i `>` i quasi sempre per parelles (obertura i tancament) — sense necessitat d'un llenguatge de programació.

Anem a veure-ho amb les mans abans que amb la definició.

**🧪 Pas a pas — El teu primer document marcat**

1. Crea una carpeta per a este mòdul (per exemple, `LMSGI`, dins la teua carpeta personal).
2. Obri un editor de text senzill — en LLiurex tens **Mousepad**, en el menú d'Aplicacions → Accessoris — i guarda ahí un arxiu nou anomenat `textos.txt`.
3. Escriu a dins exactament açò:
   ```
   <h1>Text gran</h1>
   <h3>Text xicotet</h3>
   ```
4. Guarda i torna a obrir-lo amb doble clic. És un arxiu de text normal: veus les marques tal com les has escrites.
5. Ara canvia el nom de l'arxiu a `textos.html` (clic dret → *Canviar nom* — canvia també l'extensió, no sols el nom) i obri'l amb el navegador: arrossegant-lo a una finestra de Firefox, o amb clic dret → *Obrir amb* → Firefox.

El contingut no ha canviat ni una lletra. El que ha canviat és **qui l'interpreta**: Mousepad t'ensenya el text literal; el navegador reconeix `<h1>` i `<h3>` com a marques i les convertix en un títol gran i un altre xicotet. Al programa que interpreta les marques per a presentar-les a un usuari final se l'anomena **user-agent** (navegadors, lectors de pantalla...), i el mateix document pot donar resultats molt diferents segons quin el processe. Un editor de codi com VS Code no és estrictament un user-agent — no està pensat per a "presentar" el document, sinó per a ajudar-te a escriure'l —, però és un tercer programa útil per a comparar com cadascun tracta les mateixes marques:

| Programa | Què fa amb les marques | És un user-agent? |
|---|---|---|
| **Navegador** (Firefox, Chrome...) | Les convertix en text renderitzat, taules, imatges en pantalla | Sí |
| **Lector de pantalla** | Les anuncia per veu per a persones amb discapacitat visual: "encapçalament nivell 2, Avantatges dels llenguatges de marques" | Sí |
| **Editor de codi** (VS Code...) | Ressalta la sintaxi en colors, plega blocs, mostra vista prèvia (com este mateix document en Markdown) | No, en sentit estricte — t'ajuda a escriure el document, no te'l "presenta" |

> 💡 **Els encapçalaments van de `<h1>` a `<h6>`** — no indiquen grandària de lletra, sinó **nivell d'importància** dins del document. Que `<h1>` es veja més gran és només l'estil que aplica el navegador *per defecte*; amb CSS (ho vorem en la UD4) es pot canviar la grandària sense tocar eixa jerarquia. El text "normal" no porta cap etiqueta d'encapçalament, s'escriu dins d'un paràgraf (`<p>`).

⚠️ **Important**: no confongues un llenguatge de marques (LM) amb un **llenguatge de programació** (LP). Un LM no té variables, bucles ni funcions — només descriu format o estructura. Quan un LM es combina amb un LP (per exemple HTML + JavaScript) diem que el document s'ha "programat", però l'HTML en si mateix no ho és.

**🧪 Exercici 1 — Tres programes, tres lectures**
Obri el teu `textos.html` amb un editor de codi, mostrant l'arxiu en brut (sense vista prèvia). Ja tens tres programes distints processant el mateix document marcat: Mousepad, el navegador i l'editor de codi — però només el navegador encaixa en el concepte estricte de *user-agent*. Explica amb les teues paraules què fa cadascun amb les mateixes marques, i què creus que passaria si, en lloc d'un navegador, el "obrira" un lector de pantalla.

---

### Característiques generals

Tot el que acabes de fer amb `textos.html` ja t'ha ensenyat dos de les característiques que definixen qualsevol llenguatge de marques — anem a posar-los nom, i a afegir les que falten:

- **Text pla**: acabes de comprovar-ho — Mousepad t'ensenya el codi tal com és, sense necessitar cap programa especial.
- **Independència**: també ho acabes de veure — el mateix `textos.html`, interpretat per Mousepad, el navegador i un editor de codi, dona tres resultats distints. El document no canvia; qui l'interpreta, sí.
- **Integració**: les marques van incrustades en el propi text del document, en un únic arxiu — no hi ha un arxiu de contingut per una banda i un altre de format per l'altra, sincronitzats a mà, com feien formats més antics.
- **Especialització**: no són només per a la web — hi ha llenguatges de marques per a matemàtiques (**MathML**), música (**MusicXML**), química (**CML**, per a molècules i reaccions) o síntesi de veu (**SSML**).
- **Flexibilitat**: es combinen fàcilment amb altres llenguatges sense deixar de ser ells mateixos — ho vorem en el punt 2, quan l'HTML incorpore JavaScript.

> 💡 Estes cinc són les que trobaràs citades en qualsevol manual sobre llenguatges de marques — no és una llista tancada ni una llei universal (hi ha excepcions, com el format binari **EXI**, que codifica XML perdent la propietat de "text pla"), però sí que són les que definixen la gran majoria.

Cadascuna d'estes característiques, quan aporta un benefici pràctic concret, es convertix en un **avantatge** — açò és exactament el que veuràs en el punt 2.

**🧪 Exercici 2 — Característiques, a examen**
Per a cadascun d'estos elements, indica quines de les 5 característiques (text pla, independència, integració, especialització, flexibilitat) complix i quines no, raonant la teua resposta:
- El teu propi `textos.html`.
- Una fotografia `.jpg`.
- Un arxiu `.docx`.

---

## 2. Avantatges dels llenguatges de marques (CA 1b)

Amb el teu `textos.html` acabat de crear ja pots comprovar en la pràctica quin avantatge concret porta cada característica del punt 1.

- **Text pla** — açò és el que fa possible: es poden llegir, escriure i editar amb qualsevol editor, sense programari específic ni llicències, com acabes de fer. Prova d'obrir amb Mousepad una imatge `.jpg` o un `.docx` qualsevol: il·legible, perquè és un binari i necessita el programa que l'ha generat per a poder llegir-se.

  Açò té una conseqüència que utilitzaràs tot el curs: en ser text, ferramentes com Git poden comparar dos versions línia a línia. Obri un terminal (clic dret sobre l'escriptori → *Obrir terminal ací*, o des del menú d'Aplicacions) i situa't a la teua carpeta:
  ```bash
  git init                        # inicia el repositori a la teua carpeta
  git add .
  git commit -m "Versió inicial"  # guarda una "fotografia" d'este estat
  # ...canvies <h1>Texto grande</h1> per <h1>Hola</h1> i guardes...
  git diff                        # compara l'estat actual amb l'últim commit
  ```
  ```diff
  - <h1>Texto grande</h1>
  + <h1>Hola</h1>
  ```
  Amb un binari, Git només podria dir "açò és distint", mai "què ha canviat" — i si dos persones l'editen alhora, no hi ha manera de combinar els dos canvis automàticament.

- **Independència** — este és el seu avantatge pràctic: el mateix HTML es veu en una columna en el mòbil i en diverses en l'ordinador, i en imprimir una pàgina molts llocs oculten el menú de navegació — l'HTML no canvia, només la interpretació de cada eixida. És la base de **separar contingut i presentació**:
  ```html
  <h1>Títol</h1>
  ```
  ```css
  h1 { color: blue; font-size: 3em; }
  @media print { h1 { color: black; font-size: 1.5em; } }
  ```
  Si barrejares el format dins del contingut (`<font size="7" color="blue">Títol</font>`), necessitaries una còpia distinta per a cada dispositiu.

- **Facilitat d'intercanvi** — conseqüència directa de ser text pla amb una sintaxi pública i documentada: qualsevol sistema el llig i l'escriu sense necessitar el programa original — un lector de feeds RSS de qualsevol fabricant llig el feed de qualsevol blog (tornaràs a veure un feed RSS en el punt 4.4); Word, LibreOffice i Google Docs obrin el mateix `.docx`.

- **Flexibilitat** — la que t'avançava en el punt 1: HTML incorpora JavaScript (`<script>`) per a donar comportament dinàmic, o un `<svg>` s'insereix directament dins d'una pàgina HTML.

**🧪 Exercici 3 — Comprova-ho amb les teues mans**
1. En el teu `textos.html`, canvia `<h3>Texto pequeño</h3>` per un altre text qualsevol i guarda.
2. Executa `git diff` (si encara no tens Git instal·lat, instal·la'l amb `sudo apt install git`, o compara a ull les dos versions). Veus exactament quina línia ha canviat i quina no?
3. Agafa qualsevol imatge que tingues a mà i obri-la amb Mousepad. Podries fer amb ella el mateix `git diff` línia a línia? Relaciona la teua resposta amb l'avantatge de "text pla".

---

## 3. Origen i classificació dels llenguatges de marques (CA 1c)

En els inicis de la informàtica cada aplicació utilitzava les seues pròpies marques, així que no hi havia manera d'intercanviar un document entre plataformes distintes. Per a resoldre-ho va aparéixer en els anys 80 un estàndard comú, **SGML** — no és un llenguatge amb etiquetes pròpies, sinó un **metallenguatge**: definix les regles per a crear altres llenguatges de marques. D'ahí naixen, per camins distints, els dos que utilitzaràs tot el curs:

- **XML** és un **subconjunt simplificat** de SGML: es va crear per a quedar-se amb l'essencial, amb una sintaxi molt més fàcil de processar.
- **HTML** és una **aplicació de SGML**, però mai ha sigut tan estricte: els navegadors sempre l'han interpretat de forma permissiva, "perdonant" errors que XML rebutjaria directament. Per això en la UD2 podràs deixar una etiqueta HTML mal tancada i el navegador l'arreglarà sol, mentre que en XML (apartat 4.3 d'esta unitat) el mateix error detin tot el document. Hui, l'HTML Living Standard definix les seues pròpies regles d'anàlisi i evolució, independents de SGML — la relació entre tots dos és sobretot històrica.

> 🕰️ Quasi ningú escriu SGML directament hui en dia — s'estudia només perquè explica *per què* XML i HTML són com són, no perquè hages d'utilitzar-lo.

A més d'XML i HTML hi ha altres formats amb què et creuaràs en el mòdul — no tots són estrictament llenguatges de marques, però convé ubicar-los:

| Llenguatge | Per a què servix | El utilitzaràs en este mòdul? |
|---|---|---|
| **HTML** | Estructurar pàgines web | Sí — des de la UD2 |
| **XML** | Intercanvi de dades estructurades | Sí — la resta d'esta unitat |
| **JSON** | Notació de dades lleugera, molt utilitzada en APIs web | Sí — més avant en el mòdul |
| **Markdown** | Marcatge lleuger per a notes i documentació tècnica | Es treballa a banda, en una pràctica independent |

> 🕰️ Fora d'esta taula hi ha més llenguatges de marques amb usos molt concrets (LaTeX per a documents científics, PostScript per a impressió, RTF...). No et fan falta per a este mòdul.

**Classificació.** Amb estos quatre llenguatges que ja coneixes pots veure com es classifica qualsevol llenguatge de marques segons el seu tipus de marca:

| Tipus | Què fa | En el que ja coneixes |
|---|---|---|
| **De presentació** | Només diu com es veu el text, no què és cada part | Markdown: `**negreta**` no diu si és un títol o un avís, només que es veja en negreta |
| **Descriptiu / estructural** | Diu què és cada dada, sense dir com es mostra | XML: `<titulo>El Quijote</titulo>` diu què és eixa dada, no si va gran o xicoteta |
| **Híbrid** | Barreja les dos coses | HTML: `<h1>` diu què és (un encapçalament) i a més el navegador decidix per defecte com es veu |

---

## 4. XML com a llenguatge de marques de propòsit general (CA 1d-1i)

La resta de la unitat se centra en **XML**, el llenguatge de marques de propòsit general que utilitzaràs durant tot el mòdul. Anem a veure'l en quatre passos: per a què servix i on s'utilitza, com s'escriu, quines regles ha de complir per a ser vàlid, i com evita que xoquen etiquetes d'orígens distints.

> ⭐ **XML és el protagonista d'esta unitat.** Tot el demés que apareix — SGML, HTML, JSON, Markdown, XHTML — ho fa com a antecedent històric, exemple de comparació o aplicació pràctica; l'objectiu final del RA1 és que reconegues i escrigues XML.

### 4.1 Àmbits d'aplicació (CA 1d, 1e)

Com més dispositius i sistemes distints existixen, més falta fa un estàndard comú per a intercanviar informació. Açò és el que resol l'**estandardització**: el procés de fixar normes perquè elements construïts de forma independent (per exemple, dos aplicacions d'empreses distintes) funcionen bé junts.

Les organitzacions que fixen estos estàndards són principalment el **W3C** (*World Wide Web Consortium*), **ISO** i la comunitat **Open Source**.

**XML** (*eXtensible Markup Language*) sorgix com el llenguatge de marques de **propòsit general**: un subconjunt de SGML pensat per a ser més senzill, amb sintaxi més estricta, i que servix per a *qualsevol* tipus d'informació estructurada, no sols per a la web. Les seues característiques principals són:

- És un **metallenguatge**: permet crear infinites etiquetes pròpies, adaptades a cada necessitat — és justament el que faràs en l'apartat següent, en construir el teu propi vocabulari amb etiquetes inventades per tu mateix. A diferència d'HTML, el conjunt d'etiquetes del qual és fix i el definix el WHATWG, en XML les etiquetes les decidixes tu segons el que necessites representar.
- És **estructurat**: organitza les dades com un arbre jeràrquic (ho vorem en l'apartat següent) sense pensar en com es presentaran — la mateixa separació de contingut i presentació que vam veure en el punt 2.
- És **validable**: es pot comprovar automàticament, abans de processar-lo, si un document complix una estructura definida (un DTD o un XML Schema) — útil, per exemple, per a rebutjar d'entrada un arxiu mal format que arriba d'un altre sistema, sense haver d'executar codi per a descobrir l'error.
- **No està limitat a la web**: s'utilitza en qualsevol tipus d'aplicació — arxius de configuració, els formats d'Office per dins (`.docx`, `.xlsx`), recursos d'apps Android, intercanvi de dades entre sistemes empresarials…

Alguns llenguatges construïts a partir d'XML:

| Llenguatge | Ús |
|---|---|
| SVG | Gràfics vectorials 2D |
| MathML | Fórmules matemàtiques |
| SMIL | Informació multimèdia |
| SSML | Síntesi de veu |

> 📡 **SVG, present en el teu dia a dia sense que ho notes**: cada icona, logo o il·lustració vectorial que veus en la web sol ser SVG — inclòs el logo `</>` de la portada d'esta mateixa unitat, fet exactament així. En ser XML, un navegador el pot inserir directament dins de l'HTML (com en la portada) i modificar-lo amb CSS o JavaScript igual que qualsevol altre element de la pàgina — cosa que una imatge de píxels (`.png`, `.jpg`) no permet. A més és independent de la resolució: el mateix arxiu es veu nítid tant en una icona xicoteta com ampliat a pantalla completa, perquè no està fet de píxels sinó de fórmules geomètriques.

**Icona de la portada, explicada línia a línia:**

```html
<!--
  viewBox="0 0 400 400"  → el llenç intern fa 400×400 unitats.
  width/height="180"     → la grandària final en pantalla. En ser vectorial,
                            podries posar 1800 i es vorria igual de nítid.
-->
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 400 400" width="180" height="180">

  <!-- Primer cercle: el reblit. Verd molt suau, sense vora. -->
  <circle cx="200" cy="200" r="170" fill="#F0FDFA"/>

  <!-- Segon cercle: el mateix cercle, però només el contorn
       (fill="none"), dibuixat damunt de l'anterior. Entre els dos
       donen l'efecte de "cercle amb vora". -->
  <circle cx="200" cy="200" r="170" fill="none" stroke="#99F6E4" stroke-width="2"/>

  <!-- El símbol "</>"  centrat (text-anchor="middle"), en verd
       fosc. Els símbols < i > van escrits com &lt; i &gt;:
       si es posaren literalment, el navegador els confondria
       amb l'inici d'una altra etiqueta. -->
  <text x="200" y="248" font-family="'Courier New', Courier, monospace" font-size="150" font-weight="700" fill="#0F766E" text-anchor="middle">&lt;/&gt;</text>

</svg>
```

**🧪 Exercici 4 — La teua pròpia icona SVG**
Parteix del codi SVG de dalt i modifica'l per a crear la teua pròpia icona: canvia el text, els colors (`fill`, `stroke`) o afig una segona forma (per exemple un `<rect>` o un segon `<circle>`). Guarda'l com a `.svg` i obri'l directament amb el navegador per a veure el resultat. Després, respon: sent una imatge, per què es pot editar amb un editor de text normal?

---

### 4.2 Estructura i sintaxi (CA 1f, 1g)

Un document XML s'organitza com un **arbre**: un únic **element arrel** que conté altres elements imbricats a dins.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<nota>
  <de>Pablo</de>
  <para>Eric</para>
  <encabezado>Recordatorio</encabezado>
  <cuerpo>Pablo, si no estudias, la IA no va a hacer que apruebes solo!</cuerpo>
</nota>
```

Elements de la sintaxi:

- **Declaració XML** (opcional però recomanada): `<?xml version="1.0" encoding="UTF-8"?>` — indica la versió d'XML i la codificació de caràcters utilitzada. Quasi sempre voràs esta mateixa declaració; només canviaria si utilitzares una altra codificació, per exemple `<?xml version="1.0" encoding="ISO-8859-1"?>` (una codificació més antiga, hui en desús davant d'UTF-8).
- **Element**: la unitat bàsica, formada per una etiqueta d'obertura i una de tancament. Exemples: `<de>Pablo</de>`, `<ciudad>Algemesí</ciudad>`, `<precio>19.99</precio>` — el contingut pot ser text, un número, o fins i tot altres elements imbricats.
- **Element arrel**: l'element que engloba tots els altres. Només pot haver-hi un per document. Ací és `<nota>`; com voràs de seguida en l'exemple del catàleg, serà `<catalogo>`; en un arxiu de configuració podria ser `<configuracion>` o `<settings>`.
- **Imbricació**: els elements poden contindre altres elements a dins, formant una jerarquia (arbre). Per exemple:

```xml
<alumno>
  <nombre>Claudia</nombre>
  <notas>
    <nota>7</nota>
    <nota>8.5</nota>
  </notas>
</alumno>
```

  Ací `<notas>` conté diversos `<nota>`, que al seu torn estan dins d'`<alumno>` — tres nivells d'imbricació.
- **Atributs**: informació addicional dins de la pròpia etiqueta d'obertura, en parells `nom="valor"`. Un element pot tindre diversos atributs alhora:

```xml
<persona edad="20" ciudad="Valencia">Claudia</persona>
<libro isbn="978-84-376-0494-7" idioma="es">El Quijote</libro>
```

- **Element buit**: un element sense contingut es pot escriure amb autotancament. Exemples: `<linea/>` en lloc de `<linea></linea>`, o `<separador tipo="doble"/>` — un element buit també pot portar atributs.

> 📡 **Seguix vigent**: encara que hui JSON guanye en les APIs web, esta mateixa estructura d'arbre és la que utilitzen a diari els arxius d'Office, els SVG i els feeds RSS.

**Construint un XML complet, pas a pas**

Tot el que hereta de SGML es compon de tres parts: una **declaració**, un **DTD** (*Document Type Definition*: quines etiquetes existixen i com es combinen) i una **instància** (les dades reals, amb l'estructura d'arbre que acabes de veure). Anem a construir-les juntes amb un catàleg de sèries:

```xml
<?xml version="1.0" encoding="UTF-8"?>

<!DOCTYPE catalogo [
  <!-- El catálogo debe contener una o más series (el signo + indica 1 o más) -->
  <!ELEMENT catalogo (serie+)>

  <!-- Cada serie debe tener estos 4 elementos obligatoriamente en este orden -->
  <!ELEMENT serie (titulo, estudio, episodios, estado)>

  <!-- Atributos obligatorios (#REQUIRED) para la etiqueta serie -->
  <!ATTLIST serie id CDATA #REQUIRED>
  <!ATTLIST serie formato CDATA #REQUIRED>

  <!-- Definición de los elementos que solo contienen texto normal (#PCDATA) -->
  <!ELEMENT titulo (#PCDATA)>
  <!ELEMENT estudio (#PCDATA)>
  <!ELEMENT episodios (#PCDATA)>
  <!ELEMENT estado (#PCDATA)>
]>

<catalogo>
  <serie id="ANM-001" formato="TV">
    <titulo>One Piece</titulo>
    <estudio>Toei Animation</estudio>
    <episodios>1120</episodios>
    <estado>En emisión</estado>
  </serie>

  <serie id="ANM-002" formato="TV">
    <titulo>Bleach</titulo>
    <estudio>Pierrot</estudio>
    <episodios>366</episodios>
    <estado>En emisión</estado>
  </serie>
</catalogo>
```

Per parts:

- **Declaració** (`<?xml version="1.0" encoding="UTF-8"?>`): sempre la primera línia, la mateixa que ja coneixes.
- **DTD** (dins de `<!DOCTYPE catalogo [ ... ]>`): les regles del vocabulari que acabes d'inventar-te.
  - `<!ELEMENT catalogo (serie+)>` — un `<catalogo>` conté una o més `<serie>` (el `+` significa "una o més vegades").
  - `<!ELEMENT serie (titulo, estudio, episodios, estado)>` — cada `<serie>` ha de tindre exactament eixos quatre elements, en eixe ordre.
  - `<!ATTLIST serie id CDATA #REQUIRED>` — `<serie>` ha de portar obligatòriament (`#REQUIRED`) un atribut `id` de tipus text (`CDATA`). El mateix per a `formato`.
  - `<!ELEMENT titulo (#PCDATA)>` — `<titulo>` només conté text normal (*Parsed Character Data*), res imbricat a dins.
  - Les línies que comencen per `<!--` i acaben en `-->` són comentaris: no formen part de les regles, són perquè qui llisca el DTD entenga per què és així.
- **Instància** (`<catalogo>...</catalogo>`): les dades reals, que han de complir totes les regles anteriors — dos elements `<serie>`, cadascun amb els seus quatre elements en ordre i els seus dos atributs.

> 💡 Si en la instància faltara un element obligatori, canviares l'ordre, o oblidares un atribut `#REQUIRED`, un processador XML que valide contra este DTD el rebutjaria — açò és justament la propietat de **validable** que has vist en l'apartat 4.1.

> ⚠️ **No memoritzes la sintaxi del DTD** — no és l'objectiu d'esta unitat. El que t'interessa és entendre *per a què servix* (definir i validar un vocabulari) i saber llegir-lo quan te'l troves; aprofundiràs en la validació amb XML Schema en la UD7 i en esquemes i vocabularis en la UD8.

**🧪 Exercici 5 — Fes el teu propi XML**
Tria un tema teu (una col·lecció de videojocs, la teua llista de sèries, els mòduls d'este curs...) i, seguint el mateix model del catàleg de sèries de dalt, escriu:
- la **declaració** XML,
- un **DTD** dins de `<!DOCTYPE ...[ ... ]>` amb almenys un `<!ELEMENT>` que utilitze `+` o una llista amb ordre fix, un `<!ATTLIST>` amb algun atribut `#REQUIRED`, i algun element `(#PCDATA)`,
- una **instància** amb almenys dos elements repetits que complisquen eixes regles.

**🧪 Exercici 6 — De taula a XML**
Convertix esta taula en un document XML, utilitzant `<discografia>` com a element arrel, un element `<disco>` per fila, un atribut per a l'any, i un element buit `<agotado/>` en els discs marcats com a esgotats. No oblides la declaració XML al principi.

| Títol | Any | Esgotat |
|---|---|---|
| Àlbum A | 2019 | No |
| Àlbum B | 2021 | Sí |
| Àlbum C | 2023 | No |

---

### 4.3 Documents XML ben formats (CA 1h)

Es diu que un document XML està **ben format** quan complix les regles sintàctiques bàsiques del llenguatge. Si no les complix, cap processador XML el podrà interpretar — donarà error directament, a diferència d'HTML, que molts navegadors "perdonen" encara que tinga errors.

Regles principals — amb què passa si no es complixen:

1. **Ha d'existir un únic element arrel** que continga tots els altres.

   ❌ Malament:
   ```xml
   <titulo>Curso</titulo>
   <modulo>LMSGI</modulo>
   ```
   Sense un element arrel comú, no hi ha un únic arbre que continga tot el document. El processador ni tan sols arriba a interpretar el contingut: dona error de "document sense element arrel" abans de llegir res més.

2. **Tota etiqueta que s'obri s'ha de tancar**: `<titulo>Texto</titulo>`, mai deixar-la oberta.

   ❌ Malament:
   ```xml
   <titulo>Curso
   ```
   En arribar al final del document sense trobar `</titulo>`, el processador llança un error d'"etiqueta sense tancar" (*unclosed tag*).

3. **La imbricació s'ha de respectar**: no es poden encreuar etiquetes. `<a><b></a></b>` està malament; `<a><b></b></a>` està bé.

   ❌ Malament: `<a><b></a></b>`
   El processador espera `</b>` (l'última etiqueta oberta) i es troba `</a>`: error d'"etiqueta de tancament inesperada" (*unexpected closing tag*).

4. **Els valors dels atributs sempre van entre cometes**: `edad="25"`, no `edad=25`.

   ❌ Malament:
   ```xml
   <persona edad=20 ciudad=Valencia>Claudia</persona>
   ```
   Sense cometes, el processador no sap on acaba el valor d'`edad` i on comença el següent atribut: error de sintaxi en analitzar els atributs.

5. **XML distingix majúscules de minúscules**: `<Titulo>` i `<titulo>` són etiquetes distintes, i una no tanca l'altra.

   ❌ Malament: `<Titulo>Curso</titulo>`
   Per a XML, `<Titulo>` i `</titulo>` són dos etiquetes diferents, així que la d'obertura mai queda tancada: el mateix error d'"etiqueta sense tancar" que en la regla 2.

6. Els elements buits s'han de tancar amb `/>` o amb la seua etiqueta de tancament: `<linea/>` o `<linea></linea>`.

   ❌ Malament: `<linea>`
   En no portar ni `/>` ni una etiqueta de tancament `</linea>`, el processador la tracta com una etiqueta oberta que mai es tanca: mateix error que en la regla 2.

En els sis casos el resultat és el mateix: el processador XML es detin amb un error i no genera cap document, sense intentar "endevinar" què volies dir — justament el contrari del que fa HTML.

> 🕰️ **L'intent històric d'aplicar açò a HTML**: a finals dels anys 90 es va crear **XHTML**, una versió d'HTML reescrita per a obligar a complir estes mateixes regles de bon format (tancar sempre `<br/>` o `<img/>`, atributs entre cometes, minúscules obligatòries). La idea era que les pàgines web es pogueren processar amb les mateixes ferramentes que XML. A la pràctica, **XHTML ha quedat en un segon pla**: HTML5 va absorbir part d'eixa disciplina sense exigir la sintaxi estricta, i hui XHTML quasi no s'utilitza en desenvolupament nou. Tot i això, entendre el bon format d'XML t'ajuda a escriure millor HTML.

**🧪 Exercici 7 — Ben format, de la teoria a la pràctica**

*Part A:* Escriu un document XML ben format que descriga 3 alumnes de la teua classe (nom, edat, mòdul preferit), aplicant les 6 regles d'este punt.

*Part B:* A partir del teu propi document de la Part A, crea una còpia "espatllada" introduint 3 o 4 errors deliberats de bon format (per exemple: canvia una etiqueta a majúscules, elimina un tancament, encreua la imbricació, lleva les cometes d'un atribut). Intercanvia-la amb un company, sense dir-li què has canviat, i que identifique a quina regla correspon cada error.

---

### 4.4 Espais de noms en XML (CA 1i)

Com que en XML qualsevol es pot inventar les seues pròpies etiquetes, és fàcil que dos vocabularis que vols combinar utilitzen la **mateixa etiqueta amb significats distints**, o que un d'ells necessite afegir informació que l'altre no contempla. Per exemple, un feed RSS (ja vist en el punt 2) només definix etiquetes genèriques (`<title>`, `<description>`...), però les apps de podcasts necessiten dades extra que l'RSS estàndard no té: durada de l'episodi, autor, categoria, portada...

Els **espais de noms** (*namespaces*) resolen este xoc, associant cada conjunt d'etiquetes a una URI que les identifica de forma única. Així, un feed pot barrejar el vocabulari estàndard de RSS amb el vocabulari propi de podcasts (definit originalment per Apple, amb prefix `itunes`, i adoptat també per Spotify i altres) sense que hi haja ambigüitat:

```xml
<rss version="2.0" xmlns:itunes="http://www.itunes.com/dtds/podcast-1.0.dtd">
  <channel>
    <title>Podcast de Informática</title>
    <itunes:author>Noel Marco</itunes:author>
    <item>
      <title>Episodio 1: Introducción a XML</title>
      <itunes:duration>32:15</itunes:duration>
    </item>
  </channel>
</rss>
```

- `xmlns:itunes="..."` definix un **prefix** (`itunes`) associat a una URI concreta.
- Les etiquetes sense prefix (`<title>`) són RSS estàndard: qualsevol lector de feeds les entén.
- Les etiquetes `itunes:algo` són el vocabulari afegit: un lector de feeds genèric que no les coneix les ignora sense trencar-se; una app de podcasts sí que les interpreta per a mostrar durada, autor, portada...
- La URI no és un enllaç que ningú visite ni ha d'"existir" com a pàgina — és només un identificador únic. Per convenció s'utilitza un domini del creador del vocabulari, per a evitar que dos persones trien el mateix prefix per casualitat.

> 📡 **Continua sent necessari hui**: els espais de noms s'utilitzen contínuament a la pràctica.
> - Quan inserixes un `<svg>` dins d'una pàgina HTML5, el navegador activa automàticament el namespace d'SVG en trobar eixa etiqueta (una regla especial de "contingut foraster" de l'estàndard HTML5) — no escrius el `xmlns` a mà, però el mecanisme que ho fa possible és este.
> - En feeds com el de dalt, per a combinar el vocabulari estàndard amb el de podcasts, imatges, geolocalització, etc. sense que les etiquetes xoquen.
> - Els propis arxius d'Office (`.docx`, `.xlsx`, `.pptx`) són, per dins, XML amb diversos espais de noms combinats (un per al text o les cel·les, un altre per a estils, un altre per a relacions entre arxius interns del paquet) — la mateixa idea que veus ací, a major escala.

**🧪 Exercici 8 — Amplia el feed de podcast**
Parteix de l'exemple de feed d'este punt i afig un segon espai de noms inventat per tu (per exemple `miapp`, amb una URI a la teua elecció) amb almenys dos etiquetes pròpies (per exemple `<miapp:valoracion>` o `<miapp:transcripcion>`). Declara l'`xmlns` corresponent i utilitza el prefix correctament. Després, explica què passaria si, en lloc d'un prefix distint, hagueres anomenat la teua etiqueta simplement `<title>`.

---

<div style="page-break-after: always;"></div>

## Resum de la unitat

**1. Què és un llenguatge de marques? Característiques generals** Un sistema de marques inserides en el propi text (entre `<` i `>`) que interpreta un *user-agent* — el mateix document pot donar resultats distints segons qui el processe. No és un llenguatge de programació. Cinc característiques generals: text pla, independència, integració, especialització i flexibilitat — trets habituals, no una llei tancada (hi ha excepcions, com el binari EXI).

**2. Avantatges dels llenguatges de marques** Cada característica del punt 1 porta un avantatge pràctic: text pla (editable sense programari específic, comparable línia a línia amb Git), independència (separació entre contingut i presentació), facilitat d'intercanvi entre sistemes distints, i flexibilitat per a combinar-se amb altres llenguatges.

**3. Origen i classificació** SGML (metallenguatge del qual naixen, per camins distints, XML i HTML) resol el problema que cada aplicació tinguera les seues pròpies marques. Els llenguatges de marques es classifiquen per tipus de marca (presentació / estructural / híbrida), vista amb els exemples ja coneguts (Markdown, XML, HTML).

**4. XML com a llenguatge de marques de propòsit general**
- *Àmbits d'aplicació*: XML és un metallenguatge, estructurat en arbre, validable i no limitat a la web. Llenguatges construïts sobre XML: SVG, MathML, SMIL, SSML.
- *Estructura i sintaxi*: declaració XML, element arrel únic, imbricació, atributs i elements buits — i construcció guiada d'un XML complet (declaració, DTD amb elements, atributs i `#PCDATA`, i instància) amb l'exemple del catàleg de sèries.
- *Documents ben formats*: sis regles sintàctiques obligatòries (arrel única, tancament d'etiquetes, imbricació correcta, atributs entre cometes, sensibilitat a majúscules, elements buits tancats). Si no es complixen, el processador dona error directament — a diferència d'HTML.
- *Espais de noms*: resolen els xocs d'etiquetes entre vocabularis distints, associant cadascun a una URI única mitjançant prefixos (`xmlns:prefijo="URI"`) — imprescindibles en combinar formats (SVG en HTML, feeds, arxius d'Office).

---

## 📚 Per a saber-ne més (opcional, no avaluable)

### Per a què et servirà l'XML d'esta unitat?

El que has vist ací (declaració, DTD, bon format, namespaces) és la base mínima — l'aprofundiment real arriba a partir de la **UD7** (validació amb XML Schema), **UD8** (esquemes i vocabularis), **UD9** (conversió amb XSLT) i **UD10** (emmagatzematge i consulta). No cal dominar-ho tot ja: de moment n'hi ha prou amb reconéixer un XML i saber si està ben format.

Dit açò, a data d'este curs (2026-2027) hi ha llocs molt concrets on et pots trobar XML treballant, més enllà d'un examen:

- **Factura electrònica**: Espanya va camí de fer obligatòria la factura electrònica entre empreses (Real Decreto 238/2026), i els formats admesos — Facturae, UBL, CII — són XML. Qualsevol empresa que facture a una altra, o a l'Administració, passa per ací.
- **Transferències bancàries**: l'estàndard internacional **ISO 20022**, que utilitzen els bancs (inclòs SEPA) per a transferències i liquidació de valors, és XML.
- **Documents d'Office**: `.docx`, `.xlsx`, `.pptx` són, per dins, XML comprimit — ho vam veure en l'apartat 4.1.
- **Feeds RSS/Atom**: els mateixos que vas construir en l'apartat 4.4 — podcasts, blogs, qualsevol "subscriu-te" d'una web.
- **Integració empresarial i sanitària**: moltes APIs tipus SOAP i l'estàndard **HL7** (historials clínics, sistemes hospitalaris) continuen en XML — sobretot en sistemes grans que porten anys funcionant i no se substituïxen d'un dia per a l'altre.
- **Ferramentes de desenvolupament**: projectes Java amb Maven (`pom.xml`), configuració d'Android — encara que en Android està canviant activament: els projectes nous utilitzen cada vegada més Jetpack Compose (codi Kotlin) en lloc d'XML per a les pantalles, així que ahí el pes d'XML està baixant.

> 💡 En resum: no és una tecnologia "del passat" que s'estudia per completesa — és la canonada silenciosa per la qual circula bona part de les dades entre empreses, bancs i administracions. No sempre es veu, però hi és.

### I l'HTML que només hem vist de passada?

Encara no has escrit una línia d'HTML "de veritat" — açò comença en la **UD2**, i s'aprofundix en formularis (UD3) i fulls d'estil (UD4-5). El poc que saps ara (que és una aplicació de SGML, permissiva amb els errors) és només el context que necessitaves per a entendre per què es comporta distint d'XML.

Sobre **XHTML** en concret (que voràs mencionat en la UD2, i amb més detall si estàs en ASIX): hui dia és pràcticament **teoria sense cas pràctic real** — va quedar en desús fa anys i cap projecte nou l'utilitza. S'explica perquè és l'exemple més clar d'aplicar les regles de "bon format" d'XML (ja vistes en l'apartat 4.3) a HTML, no perquè l'hages de necessitar en el treball.

- W3Schools: https://www.w3schools.com/
- HTML Living Standard (WHATWG): https://html.spec.whatwg.org/
</content>
</invoke>
