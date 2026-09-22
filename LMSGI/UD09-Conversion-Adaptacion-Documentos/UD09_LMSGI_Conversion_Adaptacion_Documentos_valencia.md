<div style="text-align: center;">

<img src="data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCA0MDAgNDAwIiB3aWR0aD0iMTgwIiBoZWlnaHQ9IjE4MCI+CiAgPGNpcmNsZSBjeD0iMjAwIiBjeT0iMjAwIiByPSIxNzAiIGZpbGw9IiNGMEZERkEiLz4KICA8Y2lyY2xlIGN4PSIyMDAiIGN5PSIyMDAiIHI9IjE3MCIgZmlsbD0ibm9uZSIgc3Ryb2tlPSIjOTlGNkU0IiBzdHJva2Utd2lkdGg9IjIiLz4KICA8cmVjdCB4PSI5MCIgeT0iMTMwIiB3aWR0aD0iOTAiIGhlaWdodD0iMTIwIiByeD0iOCIgZmlsbD0ibm9uZSIgc3Ryb2tlPSIjMEY3NjZFIiBzdHJva2Utd2lkdGg9IjEwIi8+CiAgPHJlY3QgeD0iMjIwIiB5PSIxNTAiIHdpZHRoPSI5MCIgaGVpZ2h0PSIxMjAiIHJ4PSI4IiBmaWxsPSIjMEY3NjZFIiBvcGFjaXR5PSIwLjE1IiBzdHJva2U9IiMwRjc2NkUiIHN0cm9rZS13aWR0aD0iMTAiLz4KICA8cGF0aCBkPSJNIDE4NSAxOTAgTCAyMTUgMTkwIiBzdHJva2U9IiMwRjc2NkUiIHN0cm9rZS13aWR0aD0iOSIgc3Ryb2tlLWxpbmVjYXA9InJvdW5kIi8+CiAgPHBhdGggZD0iTSAyMDUgMTc4IEwgMjE5IDE5MCBMIDIwNSAyMDIiIGZpbGw9Im5vbmUiIHN0cm9rZT0iIzBGNzY2RSIgc3Ryb2tlLXdpZHRoPSI4IiBzdHJva2UtbGluZWNhcD0icm91bmQiIHN0cm9rZS1saW5lam9pbj0icm91bmQiLz4KPC9zdmc+Cg==" width="180" alt="Logotip LMSGI"/>

<h1>Unitat 9</h1>
<h2>Conversió i adaptació de documents per a l'intercanvi d'informació</h2>

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

1. Per què transformar documents: de XML a una altra cosa
2. XPath: localitzar informació dins d'un arbre XML
3. Estructura d'un full d'estil XSLT
4. Plantilles: xsl:template i xsl:apply-templates
5. Iterar i filtrar: xsl:for-each, xsl:if, xsl:choose
6. Aplicar la transformació i depurar
7. Repte de classe
8. Resum de la unitat
9. Per a saber-ne més

<div style="page-break-after: always;"></div>

**RA cobert:** RA5 (ASIX, CA 5a-5h) / RA5 (DAW, CA 5a-5g) — *realitza conversions sobre documents XML* / *realitza conversions sobre documents per a l'intercanvi d'informació, utilitzant tècniques, llenguatges i ferramentes de processament*

> 💡 **Nota d'estudi**: en la UD8 vau aprendre a **validar** que un XML complix una estructura (XSD). Esta unitat va un pas més enllà: aprendre a **transformar** un XML en una altra cosa — un altre XML, HTML, text pla — de forma automàtica, sense tocar el document original ni escriure un programa des de zero. La ferramenta per a açò és **XSLT**, i per a assenyalar quina part del document volem transformar en cada moment, usem **XPath**.

**🗺️ XPath vs. XSLT, d'un colp d'ull:**

| | XPath | XSLT |
|---|---|---|
| Què és | Llenguatge per a **assenyalar** una part de l'arbre XML | Llenguatge per a **transformar** un XML en un altre document |
| S'assembla a | Una ruta d'arxius (`/carpeta/arxiu`) | Una plantilla que s'omplin amb dades |
| S'usa... | ...dins de XSLT, en cada `select="..."` | ...per a embolicar i organitzar eixes rutes XPath |

XPath no transforma res per si sol: és la "brúixola" que usa XSLT per a saber on mirar en cada pas de la transformació.

---

## 1. Per què transformar documents: de XML a una altra cosa

Una mateixa dada en XML quasi mai es consumix tal qual. El catàleg de sèries que vau construir en la UD1 i vau validar en la UD8 pot necessitar eixir, segons qui el consumisca, en formes molt distintes:

- Com una **pàgina HTML** llegible, per a mostrar-la en un navegador.
- Com un **XML distint**, amb una altra estructura, per a enviar-lo a un sistema que espera un format concret.
- Com **text pla**, per a un informe o un log.

Reescriure el document a mà cada vegada que canvia el catàleg no és viable. **XSLT** (*eXtensible Stylesheet Language Transformations*) és un llenguatge — ell mateix escrit en XML — que descriu **regles de transformació**: "quan troba un element així, genera açò altre". Un processador XSLT aplica eixes regles a l'XML d'entrada i genera el document d'eixida.

> 🕰️ **Què seguix vigent i què està canviant**: XSLT té dos versions amb adopció real, 1.0 (1999) i 2.0/3.0 (més potents, amb més funcions). La majoria de ferramentes de línia de comandes disponibles en Linux (com `xsltproc`, que usarem ací) implementen **XSLT 1.0** — suficient per a tot el que vureu en esta unitat. En l'àmbit de desenvolupament web modern, XSLT ha perdut terreny davant de transformar les dades directament amb JavaScript (per exemple, convertint JSON amb codi) — però seguix sent l'estàndard en sistemes documentals, editorials i d'intercanvi B2B on l'XML és el format d'origen i no es pot evitar.

**🧪 Exercici 1 — Identifica una necessitat de conversió**
Penseu en el catàleg de sèries XML de les unitats anteriors. Escriviu dos frases: una descrivint un escenari real on algú necessitaria veure'l com HTML (qui, i per a què?), i una altra descrivint un escenari on algú necessitaria exportar-lo a un XML amb **una altra** estructura distinta (per exemple, agrupat per gènere en compte d'una llista plana).

---

## 2. XPath: localitzar informació dins d'un arbre XML

Abans de transformar, cal poder **assenyalar** una part concreta de l'arbre XML. Per a això existix **XPath** — un llenguatge de rutes, paregut a les rutes d'un sistema d'arxius, però per a navegar per elements i atributs XML.

Partint d'este XML:

```xml
<catalogo>
  <serie id="s1">
    <titulo>Breaking Bad</titulo>
    <anio>2008</anio>
    <valoracion>9.5</valoracion>
  </serie>
  <serie id="s2">
    <titulo>The Wire</titulo>
    <anio>2002</anio>
    <valoracion>9.3</valoracion>
  </serie>
</catalogo>
```

Algunes rutes XPath bàsiques:

| Expressió XPath | Selecciona |
|---|---|
| `/catalogo` | L'element arrel `catalogo` |
| `/catalogo/serie` | Tots els elements `serie`, fills directes de `catalogo` |
| `//titulo` | Tots els elements `titulo`, estiguen on estiguen en l'arbre |
| `/catalogo/serie[1]` | Només la **primera** `serie` (XPath comença a comptar en 1, no en 0) |
| `/catalogo/serie/@id` | L'atribut `id` de cada `serie` |
| `//serie[anio > 2005]` | Les `serie` el fill `anio` de les quals siga major que 2005 |
| `//serie[@id='s1']/titulo` | El `titulo` de la `serie` amb atribut `id="s1"` |

`.` es referix al node actual, `..` al node pare, i `text()` al contingut de text d'un element — els usareu dins de les plantilles XSLT en el punt següent.

**🧪 Exercici 2 — Practicar XPath**
Sobre l'XML de dalt (guardeu-lo com `catalogo.xml`), escriviu a mà les expressions XPath que seleccionarien: (a) el `titulo` de la segona sèrie, (b) totes les `valoracion` majors que 9.4, (c) l'atribut `id` de la sèrie titulada "The Wire". Comproveu les vostres respostes amb un avaluador XPath en línia com [www.freeformatter.com/xpath-tester.html](https://www.freeformatter.com/xpath-tester.html) (enganxeu l'XML i proveu cada expressió).

---

## 3. Estructura d'un full d'estil XSLT

Un full XSLT és un document `.xsl` (o `.xslt`), que és també XML:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform">

  <xsl:output method="html" encoding="UTF-8" indent="yes"/>

  <xsl:template match="/">
    <!-- ací va la transformació -->
  </xsl:template>

</xsl:stylesheet>
```

- `xsl:stylesheet` és l'arrel de tot full XSLT, amb el namespace estàndard `http://www.w3.org/1999/XSL/Transform`.
- `xsl:output` declara el format d'eixida: `html`, `xml` o `text`. Ací generem HTML.
- `xsl:template match="/"` és la **plantilla arrel**: es dispara quan el processador arriba a l'arrel del document d'entrada (el punt de partida de tota transformació).

Per a aplicar el full des del terminal en LliureX, usem `xsltproc` (ve instal·lat o s'instal·la amb `sudo apt install xsltproc`):

```bash
xsltproc catalogo.xsl catalogo.xml > catalogo.html
```

**🧪 Exercici 3 — Esquelet que genera HTML fixe**
Creeu `catalogo.xsl` amb l'esquelet de dalt, i dins de `xsl:template match="/"` escriviu HTML fixe (`<html><body><h1>Mi catálogo</h1></body></html>`, sense usar encara cap dada de l'XML). Executeu `xsltproc` i comproveu que `catalogo.html` es genera correctament i s'obri bé en Firefox.

---

## 4. Plantilles: xsl:template i xsl:apply-templates

El punt anterior generava HTML fixe — útil per a comprovar el mecanisme, però no usa l'XML d'entrada. Per a **extraure** dades de l'XML, XSLT oferix dos peces clau:

- **`xsl:value-of select="..."`** — inserix el valor d'una expressió XPath com a text.
- **`xsl:apply-templates select="..."`** — li diu al processador "busca una plantilla que sàpia tractar estos nodes, i aplica-la a cadascun".

```xml
<xsl:template match="/">
  <html>
    <body>
      <h1>Catálogo de series</h1>
      <xsl:apply-templates select="/catalogo/serie"/>
    </body>
  </html>
</xsl:template>

<xsl:template match="serie">
  <p>
    <strong><xsl:value-of select="titulo"/></strong>
    (<xsl:value-of select="anio"/>) — Valoración: <xsl:value-of select="valoracion"/>
  </p>
</xsl:template>
```

Ací hi ha **dos** plantilles: l'arrel genera l'esquelet HTML i delega en `xsl:apply-templates` la part repetitiva; la segona plantilla, `match="serie"`, es dispara automàticament **una vegada per cada** element `serie` que li arribe, i decidix com pintar-lo. Separar la lògica en diverses plantilles és la forma "correcta" d'escriure XSLT, en compte de ficar tota la transformació en una única plantilla arrel.

**🧪 Exercici 4 — Dos plantilles**
Reescriviu `catalogo.xsl` amb les dos plantilles de dalt (`match="/"` i `match="serie"`), aplicades al vostre `catalogo.xml` amb 2-3 sèries. Genereu l'HTML amb `xsltproc` i comproveu que apareix un paràgraf per cada sèrie, amb el seu títol, any i valoració extrets correctament de l'XML.

---

## 5. Iterar i filtrar: xsl:for-each, xsl:if, xsl:choose

`xsl:apply-templates` no és l'única forma de repetir contingut. **`xsl:for-each`** itera directament sobre un conjunt de nodes, sense necessitat d'una plantilla a banda — útil quan la lògica és simple i no val la pena separar-la:

**🗺️ `xsl:apply-templates` vs. `xsl:for-each`, d'un colp d'ull:**

| | `xsl:apply-templates` | `xsl:for-each` |
|---|---|---|
| Què fa | Delega en una altra plantilla (`match="..."`) per cada node | Repetix el mateix bloc de codi, sense plantilla a banda |
| Quan usar-lo | Lògica complexa, o reutilitzable en diversos llocs | Lògica simple, ús puntual |
| Organització | Separa responsabilitats en diverses plantilles xicotetes | Tot el codi junt, en un únic bloc |

Els dos recorren un conjunt de nodes — la diferència està en **on viu la lògica** de cadascun, no en quins nodes seleccionen.

```xml
<table>
  <xsl:for-each select="/catalogo/serie">
    <tr>
      <td><xsl:value-of select="titulo"/></td>
      <td><xsl:value-of select="anio"/></td>
    </tr>
  </xsl:for-each>
</table>
```

Per a lògica condicional, XSLT oferix **`xsl:if`** (una sola condició, sense alternativa) i **`xsl:choose`** (equivalent a un `if / elif / else`):

```xml
<xsl:if test="valoracion &gt; 9">
  <span> ⭐ Muy recomendada</span>
</xsl:if>

<xsl:choose>
  <xsl:when test="valoracion &gt; 9">
    <span>⭐⭐⭐</span>
  </xsl:when>
  <xsl:when test="valoracion &gt; 7">
    <span>⭐⭐</span>
  </xsl:when>
  <xsl:otherwise>
    <span>⭐</span>
  </xsl:otherwise>
</xsl:choose>
```

> ⚠️ Dins d'un atribut XML, els símbols `<` i `>` no es poden escriure literalment — per això `test="valoracion &gt; 9"` usa l'entitat `&gt;` en compte de `>` (i `&lt;` per a `<`). És la mateixa regla d'escapament que ja vau usar amb entitats XML en unitats anteriors.

**Plantilla de partida** (completeu els buits `___`):

```xml
<table>
  <xsl:for-each select="___">
    <tr>
      <td><xsl:value-of select="___"/></td>
      <td><xsl:value-of select="___"/></td>
      <td>
        <xsl:if test="valoracion &gt; ___">⭐ Recomendada</xsl:if>
      </td>
    </tr>
  </xsl:for-each>
</table>
```

**🧪 Exercici 5 — Taula amb valoració destacada**
Completeu la plantilla de dalt i substituïu amb ella la llista de paràgrafs de l'Exercici 4: una taula HTML (`xsl:for-each` sobre `serie`, amb columnes títol, any i valoració) amb una columna extra que mostre "⭐ Recomendada" només si la valoració és major que 9, usant `xsl:if`.

---

## 6. Aplicar la transformació i depurar

A més de `xsltproc` en el terminal, hi ha ferramentes gràfiques útils per a depurar un full XSLT pas a pas mentres l'escriviu:

| Ferramenta | Per a què servix |
|---|---|
| `xsltproc` (terminal, LliureX) | Aplicar la transformació des de la línia de comandes, la que usareu en els exercicis |
| [www.freeformatter.com/xsl-transformer.html](https://www.freeformatter.com/xsl-transformer.html) | Provar XML + XSLT en línia i veure el resultat i els errors a l'instant, sense instal·lar res |
| Firefox (amb `<?xml-stylesheet?>`) | Enllaçant el full XSLT directament des de l'XML, el navegador aplica la transformació en obrir l'arxiu |

Perquè Firefox aplique la transformació automàticament en obrir l'XML, s'afegix esta línia de processament just després de la declaració XML:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<?xml-stylesheet type="text/xsl" href="catalogo.xsl"?>
<catalogo>
  ...
</catalogo>
```

Quan alguna cosa falla, `xsltproc` assenyala **línia i columna** de l'error, igual que `xmllint` — el mateix hàbit de llegir el missatge d'error de la UD7 i la UD8 aplica ací: no ignorar-lo, i localitzar la línia exacta abans de tocar res més.

**🧪 Exercici 6 — Enllaçar i depurar**
Afegiu la línia `<?xml-stylesheet?>` al vostre `catalogo.xml` apuntant a `catalogo.xsl`, i obriu l'XML directament amb Firefox — ha de mostrar-se ja transformat en HTML. Després, introduïu deliberadament un error en `catalogo.xsl` (per exemple, una etiqueta `xsl:template` sense tancar) i executeu `xsltproc catalogo.xsl catalogo.xml`: copieu el missatge d'error exacte i expliqueu en una frase què indica sobre on està el problema.

---

## 7. Repte de classe

Retomeu el domini propi que vau triar en el repte de la UD8 (o proposeu-ne un altre) i genereu, a partir del vostre XML, un document HTML amb `xsltproc` que use almenys:

1. **Dos plantilles separades** (`xsl:template match="/"` + `xsl:apply-templates` cap a una segona plantilla).
2. Una **taula** construïda amb `xsl:for-each`.
3. Una **condició** (`xsl:if` o `xsl:choose`) que destaque alguna dada segons el seu valor.

> 📋 No cal memoritzar la sintaxi exacta d'XPath ni d'XSLT — tindreu sempre a mà la taula d'expressions XPath i la llista d'elements `xsl:` vistos en la unitat.

---

## Resum de la unitat

1. **XSLT** transforma un XML d'entrada en un altre document (HTML, un altre XML, text) aplicant regles de transformació descrites també en XML.
2. **XPath** és el llenguatge de rutes que permet assenyalar quina part de l'arbre XML es vol llegir o transformar (`/catalogo/serie`, `//titulo`, `@id`, amb condicions entre claudàtors).
3. Un full `.xsl` té com a arrel `xsl:stylesheet`, declara el format d'eixida amb `xsl:output`, i definix la seua lògica en una o diverses `xsl:template`; s'aplica en LliureX amb `xsltproc`.
4. `xsl:value-of` extrau un valor com a text; `xsl:apply-templates` delega en la plantilla adequada per a cada node — la forma habitual d'organitzar una transformació en diverses peces.
5. `xsl:for-each` itera directament sobre un conjunt de nodes; `xsl:if` i `xsl:choose`/`xsl:when`/`xsl:otherwise` afigen lògica condicional (amb `&gt;`/`&lt;` en compte de `>`/`<` dins d'atributs).
6. La transformació es pot llançar des del terminal (`xsltproc`), depurar amb ferramentes en línia, o enllaçar directament des de l'XML amb `<?xml-stylesheet?>` perquè el navegador l'aplique en obrir l'arxiu.

---

## 📚 Per a saber-ne més (opcional, no avaluable)

XSLT 2.0 i 3.0 afigen funcions molt més potents (agrupació amb `xsl:for-each-group`, generació de diversos arxius d'eixida a la vegada amb `xsl:result-document`...), però requerixen un processador distint de `xsltproc` (que només suporta 1.0) — per exemple Saxon, disponible també per a Linux. Si en el futur treballeu amb transformacions complexes de veritat (per exemple, generant un llibre complet en PDF a partir d'XML editorial), és on vos les trobareu.

- Especificació oficial de XSLT 1.0 (W3C): [www.w3.org/TR/xslt-10](https://www.w3.org/TR/xslt-10/)
- Especificació oficial de XPath 1.0 (W3C): [www.w3.org/TR/xpath-10](https://www.w3.org/TR/xpath-10/)
- Tutorial interactiu de XSLT: [www.w3schools.com/xml/xsl_intro.asp](https://www.w3schools.com/xml/xsl_intro.asp)
- Provador de XSLT en línia: [www.freeformatter.com/xsl-transformer.html](https://www.freeformatter.com/xsl-transformer.html)
</content>
