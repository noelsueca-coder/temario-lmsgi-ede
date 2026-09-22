<div style="text-align: center;">

<img src="data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCA0MDAgNDAwIiB3aWR0aD0iMTgwIiBoZWlnaHQ9IjE4MCI+CiAgPGNpcmNsZSBjeD0iMjAwIiBjeT0iMjAwIiByPSIxNzAiIGZpbGw9IiNGMEZERkEiLz4KICA8Y2lyY2xlIGN4PSIyMDAiIGN5PSIyMDAiIHI9IjE3MCIgZmlsbD0ibm9uZSIgc3Ryb2tlPSIjOTlGNkU0IiBzdHJva2Utd2lkdGg9IjIiLz4KICA8cGF0aCBkPSJNIDEzMCAxMzAgTCAyNzAgMTMwIEwgMjcwIDIwMCBMIDIyMCAyMDAgTCAyMjAgMjcwIEwgMTMwIDI3MCBaIiBmaWxsPSJub25lIiBzdHJva2U9IiMwRjc2NkUiIHN0cm9rZS13aWR0aD0iMTAiIHN0cm9rZS1saW5lam9pbj0icm91bmQiLz4KICA8bGluZSB4MT0iMTUwIiB5MT0iMTYwIiB4Mj0iMjUwIiB5Mj0iMTYwIiBzdHJva2U9IiMwRjc2NkUiIHN0cm9rZS13aWR0aD0iNyIgc3Ryb2tlLWxpbmVjYXA9InJvdW5kIiBvcGFjaXR5PSIwLjUiLz4KICA8bGluZSB4MT0iMTUwIiB5MT0iMjMwIiB4Mj0iMTk1IiB5Mj0iMjMwIiBzdHJva2U9IiMwRjc2NkUiIHN0cm9rZS13aWR0aD0iNyIgc3Ryb2tlLWxpbmVjYXA9InJvdW5kIiBvcGFjaXR5PSIwLjUiLz4KICA8cGF0aCBkPSJNIDI0NSAyMzUgTCAyNTggMjQ4IEwgMjgyIDIyMCIgZmlsbD0ibm9uZSIgc3Ryb2tlPSIjMEY3NjZFIiBzdHJva2Utd2lkdGg9IjkiIHN0cm9rZS1saW5lY2FwPSJyb3VuZCIgc3Ryb2tlLWxpbmVqb2luPSJyb3VuZCIvPgo8L3N2Zz4K" width="180" alt="Logotip LMSGI"/>

<h1>Unitat 8</h1>
<h2>Definició d'esquemes i vocabularis en llenguatges de marques</h2>

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

1. De DTD a XML Schema: per què necessitem alguna cosa més
2. Estructura d'un document XSD i el seu vincle amb l'XML
3. Tipus simples: les dades bàsiques i les seues restriccions
4. Tipus complexos: elements amb estructura
5. Compositors i cardinalitat: sequence, choice, all, minOccurs, maxOccurs
6. Atributs en XSD
7. Tipus reutilitzables i grups
8. Validar un document contra el seu esquema
9. Repte de classe
10. Resum de la unitat
11. Per a saber-ne més

<div style="page-break-after: always;"></div>

**RA cobert:** RA4 (ASIX, CA 4a-4h) / RA4 (DAW, CA 4a-4g) — *establix mecanismes de validació per a documents XML* / *establix mecanismes de validació de documents per a l'intercanvi d'informació, utilitzant mètodes per a definir la seua sintaxi i estructura*

> 💡 **Nota d'estudi**: en la UD1 vau construir a mà un DTD (`<!ELEMENT>`, `<!ATTLIST>`, `#PCDATA`, `#REQUIRED`) i en la UD7 vau aprendre a validar un XML contra un esquema amb `xmllint --schema`. Esta unitat tanca el cercle: veureu **per què** el sector va deixar d'usar DTD com a primera opció, i aprendreu a escriure esquemes **XML Schema (XSD)** — hui l'estàndard real per a descriure i validar l'estructura d'un document XML.

**🗺️ Mapa del bloc — de quines peces es compon un XSD:**

```
xs:schema (arrel)
 └─ xs:element (allò que pot aparéixer en l'XML)
     ├─ xs:simpleType   → dada sense fills/atributs (text amb tipus + restricció)
     └─ xs:complexType  → element amb estructura
         ├─ compositor: xs:sequence / xs:choice / xs:all
         ├─ xs:element (fills, amb minOccurs/maxOccurs)
         └─ xs:attribute (use="required"/"optional", default="...")
```
Cada punt d'esta unitat afig una peça a este mapa — torneu-hi si vos perdeu.

---

## 1. De DTD a XML Schema: per què necessitem alguna cosa més

El DTD que vau construir en la UD1 funciona, però té límits que es noten de seguida en qualsevol projecte real:

| Limitació del DTD | Conseqüència |
|---|---|
| No té tipus de dades | `<precio>abc</precio>` és tan vàlid com `<precio>19.99</precio>` — un DTD no distingix text de número |
| Sintaxi pròpia, no XML | Un DTD no es pot processar amb les mateixes ferramentes que processen XML (no té etiquetes, atributs ni namespaces) |
| Namespaces mal suportats | No hi ha manera neta de dir "este DTD aplica només a elements d'este namespace" |
| Reutilització pobra | No es pot definir un tipus una vegada i reutilitzar-lo en diversos elements sense repetir la definició |

**XML Schema (XSD)**, publicat pel W3C en 2001, resol els quatre punts: és XML ell mateix (s'escriu amb etiquetes `<xs:...>`), té un sistema de tipus (text, número enter, decimal, data, booleà...), suporta namespaces de forma nativa, i permet definir tipus reutilitzables.

> 🕰️ **Què seguix vigent i què està canviant**: el DTD **no ha desaparegut** — seguix vigent en formats heretats i en casos on n'hi ha prou amb validar estructura sense tipus (per exemple, algunes DTD d'HTML antigues). Però per a qualsevol intercanvi de dades seriós entre sistemes (facturació electrònica, configuració d'aplicacions, APIs basades en XML) l'estàndard de facto hui és **XSD**. Existix una tercera alternativa, **RELAX NG**, més simple i expressiva que XSD en alguns aspectes, però amb molta menys adopció industrial — la mencionem perquè sapieu que existix, no cal aprofundir-hi.

**🧪 Exercici 1 — Troba els buits del DTD**
Retomeu el DTD del catàleg de sèries que vau construir en la UD1. Escriviu una instància XML que **complisca** eixe DTD (etiquetes i orde correctes) però que tinga clarament una dada mal escrita que el DTD no puga detectar — per exemple, un any d'estrena com `"mil novecientos noventa"` en compte d'un número, o una valoració fora de rang com `15` sobre una escala d'1 a 10. Anoteu en una frase per què el DTD no ho rebutja.

---

## 2. Estructura d'un document XSD i el seu vincle amb l'XML

Un esquema XSD és un arxiu `.xsd`, que és al seu torn un document XML. Comencem pel seu esquelet mínim:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">

  <xs:element name="catalogo">
    <!-- ací definim què pot contindre <catalogo> -->
  </xs:element>

</xs:schema>
```

- `xs:schema` és l'element arrel de **tot** esquema XSD: declara el namespace estàndard de XML Schema (`http://www.w3.org/2001/XMLSchema`), amb el prefix `xs` per convenció.
- `xs:element` declara un element que pot aparéixer en l'XML validat — ací, l'element arrel `<catalogo>`.

Perquè un XML es valide contra este esquema, cal **associar-lo** explícitament. La forma habitual és amb `xsi:schemaLocation` en l'element arrel de l'XML:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<catalogo xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
          xsi:noNamespaceSchemaLocation="catalogo.xsd">
  <!-- contingut -->
</catalogo>
```

`xsi:noNamespaceSchemaLocation` s'usa quan l'esquema no definix un namespace propi per a les dades (com en el nostre cas). Si l'esquema sí que definix un namespace de destinació (`targetNamespace`), s'usa `xsi:schemaLocation` amb el parell namespace–arxiu. Amb esta associació feta, ja podeu validar amb la ferramenta que vau aprendre en la UD7:

```bash
xmllint --noout --schema catalogo.xsd catalogo.xml
```

**🧪 Exercici 2 — Esquelet mínim**
Creeu `catalogo.xsd` amb l'esquelet de dalt (element arrel `catalogo`, sense contingut definit encara) i `catalogo.xml` amb l'associació `xsi:noNamespaceSchemaLocation`. Valideu amb `xmllint`: com que `<xs:element name="catalogo">` no definix encara cap contingut permés, qualsevol cosa que fiqueu dins de `<catalogo>` donarà error — comproveu-ho i anoteu el missatge exacte que retorna `xmllint`.

---

## 3. Tipus simples: les dades bàsiques i les seues restriccions

Un **tipus simple** descriu una dada que no té fills ni atributs — només text, però amb un tipus de dada concret. XSD porta tipus predefinits:

| Tipus XSD | Exemple de valor vàlid |
|---|---|
| `xs:string` | `"Breaking Bad"` |
| `xs:integer` | `2008` |
| `xs:decimal` | `9.5` |
| `xs:boolean` | `true` |
| `xs:date` | `2008-01-20` |

```xml
<xs:element name="titulo" type="xs:string"/>
<xs:element name="anio" type="xs:integer"/>
<xs:element name="valoracion" type="xs:decimal"/>
```

Quan un tipus predefinit no és suficient, es pot **restringir** amb `xs:restriction`, creant un tipus simple propi. Açò és el que resol el problema de l'Exercici 1: forçar que `valoracion` estiga entre 1 i 10.

```xml
<xs:element name="valoracion">
  <xs:simpleType>
    <xs:restriction base="xs:decimal">
      <xs:minInclusive value="1"/>
      <xs:maxInclusive value="10"/>
    </xs:restriction>
  </xs:simpleType>
</xs:element>
```

Estes restriccions s'anomenen **facets** (facetes). Les més habituals:

| Faceta | Per a què servix |
|---|---|
| `xs:minInclusive` / `xs:maxInclusive` | Rang numèric, límits inclosos |
| `xs:minLength` / `xs:maxLength` | Longitud mínima/màxima d'un text |
| `xs:pattern` | Expressió regular que el valor ha de complir |
| `xs:enumeration` | Llista tancada de valors permesos |

```xml
<xs:element name="genero">
  <xs:simpleType>
    <xs:restriction base="xs:string">
      <xs:enumeration value="drama"/>
      <xs:enumeration value="comedia"/>
      <xs:enumeration value="thriller"/>
    </xs:restriction>
  </xs:simpleType>
</xs:element>
```

**🧪 Exercici 3 — Restringir tipus**
Afegiu al vostre `catalogo.xsd` una declaració de `<anio>` restringida a `xs:integer` amb `xs:minInclusive` en `1900` (no pot haver-hi una sèrie estrenada abans), i una declaració de `<valoracion>` com en l'exemple (1 a 10). Valideu de nou el `catalogo.xml` de l'Exercici 1: l'error de l'any o la valoració fora de rang, que el DTD no detectava, ara sí que ha d'aparéixer.

---

## 4. Tipus complexos: elements amb estructura

Un element amb **fills** o **atributs** necessita un **tipus complex** (`xs:complexType`). És el que resol per fi l'element arrel `<catalogo>` de l'Exercici 2:

```xml
<xs:element name="catalogo">
  <xs:complexType>
    <xs:sequence>
      <xs:element name="serie" type="SerieType" maxOccurs="unbounded"/>
    </xs:sequence>
  </xs:complexType>
</xs:element>

<xs:complexType name="SerieType">
  <xs:sequence>
    <xs:element name="titulo" type="xs:string"/>
    <xs:element name="anio" type="xs:integer"/>
    <xs:element name="valoracion" type="xs:decimal"/>
  </xs:sequence>
</xs:complexType>
```

Dos formes de declarar un tipus complex:

- **Anònim**, definit dins del propi `xs:element` (com el `catalogo` de dalt) — només es pot usar ahí.
- **Nomenat**, amb `name="SerieType"` fora de qualsevol element (com `SerieType`) — es pot **reutilitzar** en qualsevol `xs:element type="SerieType"`, tantes vegades com calga. Açò és justament el que el DTD no permetia fer bé.

**Plantilla de partida** (completeu els buits `___`):

```xml
<xs:element name="catalogo">
  <xs:complexType>
    <xs:sequence>
      <xs:element name="serie" type="___" maxOccurs="___"/>
    </xs:sequence>
  </xs:complexType>
</xs:element>

<xs:complexType name="SerieType">
  <xs:sequence>
    <xs:element name="titulo" type="___"/>
    <xs:element name="anio">
      <!-- enganxeu ací la restricció de l'Exercici 3 -->
    </xs:element>
    <xs:element name="valoracion" type="___"/>
  </xs:sequence>
</xs:complexType>
```

**🧪 Exercici 4 — El tipus complex complet**
Completeu la plantilla de dalt (amb `SerieType` nomenat, incloent-hi les restriccions d'`anio` i `valoracion` de l'Exercici 3 dins d'ell) i substituïu amb ella el `<xs:element name="catalogo">` buit de l'Exercici 2. Valideu `catalogo.xml` amb dos o tres sèries — ha de passar sense errors si les dades són correctes.

---

## 5. Compositors i cardinalitat: sequence, choice, all, minOccurs, maxOccurs

`xs:sequence` (usat a dalt) exigix que els fills apareguen **en eixe orde exacte**. Hi ha dos compositors més:

| Compositor | Comportament |
|---|---|
| `xs:sequence` | Els elements fills han d'aparéixer en l'orde declarat |
| `xs:choice` | Ha d'aparéixer **exactament un** dels elements llistats (no diversos, no cap) |
| `xs:all` | Tots els elements han d'aparéixer, però **en qualsevol orde**; en XSD 1.0 cadascun només pot aparéixer una vegada |

```xml
<xs:complexType name="ContactoType">
  <xs:choice>
    <xs:element name="email" type="xs:string"/>
    <xs:element name="telefono" type="xs:string"/>
  </xs:choice>
</xs:complexType>
```

Per defecte, cada element fill ha d'aparéixer **exactament una vegada**. Amb `minOccurs` i `maxOccurs` es controla quantes vegades:

```xml
<xs:element name="serie" type="SerieType" minOccurs="0" maxOccurs="unbounded"/>
<xs:element name="temporada" type="xs:integer" minOccurs="1" maxOccurs="1"/>
<xs:element name="etiqueta" type="xs:string" minOccurs="0" maxOccurs="5"/>
```

- `minOccurs="0"` fa que l'element siga **opcional**.
- `maxOccurs="unbounded"` permet repetir-lo tantes vegades com calga (és el que ja vau usar per a `serie` en l'Exercici 4, sense saber encara el nom de l'atribut).
- Qualsevol número concret (`maxOccurs="5"`) posa un topall.

**🧪 Exercici 5 — Cardinalitat i elecció**
Ampliau `SerieType` amb un element opcional `<plataforma>` (0 o 1 vegada — no totes les sèries heu d'anotar necessàriament on es veuen) i amb un `xs:choice` que obligue a triar **o bé** `<enCurso/>` **o bé** `<finalizada/>` (elements buits, sense contingut, que només indiquen un estat). Proveu amb una instància que incloga els dos alhora i comproveu que `xmllint` la rebutja.

---

## 6. Atributs en XSD

Els atributs es declaren amb `xs:attribute`, sempre **després** dels elements fills dins d'un `xs:complexType`:

```xml
<xs:complexType name="SerieType">
  <xs:sequence>
    <xs:element name="titulo" type="xs:string"/>
    <xs:element name="anio" type="xs:integer"/>
  </xs:sequence>
  <xs:attribute name="id" type="xs:string" use="required"/>
  <xs:attribute name="idioma" type="xs:string" use="optional" default="es"/>
</xs:complexType>
```

- `use="required"` — equival al `#REQUIRED` del DTD: l'atribut és obligatori.
- `use="optional"` (valor per defecte si s'omet `use`) — l'atribut pot faltar.
- `default="es"` — si l'atribut no apareix en l'XML, s'assumix este valor.

Un atribut també pot portar restriccions, igual que un element simple:

```xml
<xs:attribute name="idioma" use="optional" default="es">
  <xs:simpleType>
    <xs:restriction base="xs:string">
      <xs:enumeration value="es"/>
      <xs:enumeration value="en"/>
      <xs:enumeration value="ca"/>
    </xs:restriction>
  </xs:simpleType>
</xs:attribute>
```

**🧪 Exercici 6 — Atributs obligatoris i amb valor per defecte**
Afegiu a `SerieType` un atribut `id` de tipus `xs:string`, obligatori, i un atribut `idioma` opcional restringit a `"es"`, `"en"` o `"ca"`, amb valor per defecte `"es"`. Valideu una instància que **no** incloga `idioma` (ha de passar, assumint `"es"`) i una altra que use un valor fora de la llista, com `"fr"` (ha de fallar).

---

## 7. Tipus reutilitzables i grups

Quan la mateixa restricció es repetix en diversos llocs (per exemple, `valoracion` d'1 a 10 podria aplicar-se a sèries **i** a pel·lícules si ampliàreu el catàleg), convé extraure un **tipus simple nomenat** en compte de repetir-lo:

```xml
<xs:simpleType name="ValoracionType">
  <xs:restriction base="xs:decimal">
    <xs:minInclusive value="1"/>
    <xs:maxInclusive value="10"/>
  </xs:restriction>
</xs:simpleType>

<xs:element name="valoracion" type="ValoracionType"/>
```

De la mateixa manera, si un grup d'elements es repetix en diversos tipus complexos, es pot extraure amb `xs:group`:

```xml
<xs:group name="DatosBasicosGroup">
  <xs:sequence>
    <xs:element name="titulo" type="xs:string"/>
    <xs:element name="anio" type="xs:integer"/>
  </xs:sequence>
</xs:group>

<xs:complexType name="SerieType">
  <xs:sequence>
    <xs:group ref="DatosBasicosGroup"/>
    <xs:element name="valoracion" type="ValoracionType"/>
  </xs:sequence>
</xs:complexType>
```

Extraure tipus i grups reutilitzables no és només una qüestió d'estil: és el que, en la CA d'esta unitat, s'anomena **documentar les descripcions** — un esquema amb tipus nomenats i ben organitzats és molt més fàcil de llegir, mantindre i reutilitzar en un altre projecte que un amb tot definit en línia.

**🧪 Exercici 7 — Extraure un tipus reutilitzable**
Extraeu `ValoracionType` com a tipus simple nomenat (a partir de l'Exercici 3) i useu-lo en la declaració de `valoracion` dins de `SerieType`. Afegiu un comentari XML (`<!-- ... -->`) just abans de cada tipus nomenat del vostre esquema explicant en una frase per a què servix — és la forma més simple de "documentar les descripcions".

---

## 8. Validar un document contra el seu esquema

Ja vau validar amb `xmllint --schema` en la UD7 i ho heu usat en cada exercici d'esta unitat — ací tanquem el flux complet de treball, de principi a fi:

```bash
# 1. Comprovar que l'XML està ben format (sintaxi XML correcta)
xmllint --noout catalogo.xml

# 2. Validar l'XML contra l'esquema XSD
xmllint --noout --schema catalogo.xsd catalogo.xml
```

Un document pot estar **ben format** (sintaxi XML correcta: etiquetes tancades, un únic element arrel...) i encara així **no ser vàlid** contra un esquema concret (per exemple, li falta un element obligatori, o un atribut té un valor fora de rang). Són dos comprovacions distintes, i `xmllint` les fa per separat segons quines opcions li passeu.

A més de `xmllint`, existixen validadors XSD amb interfície web, útils per a depurar ràpid sense terminal — per exemple el de [freeformatter.com/xml-validator-xsd.html](https://www.freeformatter.com/xml-validator-xsd.html), on enganxeu l'XML i l'XSD i vos assenyala l'error amb línia i columna, igual que fa `xmllint` en la terminal.

**🧪 Exercici 8 — L'esquema complet, validat de principi a fi**
Amb tot el construït en els exercicis anteriors, tingueu llest un `catalogo.xsd` complet (tipus nomenats, grup reutilitzable, atributs, cardinalitat) i un `catalogo.xml` amb almenys 3 sèries que el complisquen. Executeu les dos validacions de dalt i comproveu que les dos passen sense errors. Després, modifiqueu l'XML introduint **tres** errors distints alhora (un de tipus, un de cardinalitat, un d'atribut obligatori absent) i anoteu els tres missatges d'error que retorna `xmllint`.

---

## 9. Repte de classe

Trieu un domini propi (distint del catàleg de sèries) i construïu, de principi a fi:

1. Un document XML amb almenys **5 registres** i **2 nivells d'imbricació**.
2. Un XSD que el valide, amb almenys: un tipus simple restringit, un tipus complex reutilitzable, un compositor amb cardinalitat (`minOccurs`/`maxOccurs`), i un atribut obligatori.
3. Demostració amb `xmllint`: una instància correcta que passa, i una altra amb **2 errors deliberats** que falla.

Dos idees de domini — trieu la que més vos interesse, o proposeu-ne una altra:

- **Perfil ASIX** — un arxiu de configuració d'un servei multimèdia en xarxa (perfils de streaming: nom, port, protocol, còdec, bitrate).
- **Perfil DAW** — un dashboard de finances personals (moviments: data, categoria, import, tipus).

> 📋 No cal memoritzar la sintaxi exacta de cada faceta o compositor — en el repte (i en el test) tindreu sempre a mà una xuleta amb la llista d'elements `xs:` vistos en la unitat. El que s'avalua és que sapieu **quan usar cada peça**, no que la recordeu de memòria.

---

## Resum de la unitat

1. El **DTD** no té tipus de dades, no és XML, i suporta mal namespaces i reutilització — d'ací que l'estàndard actual per a validar documents XML siga **XML Schema (XSD)**, publicat pel W3C, que sí que resol els quatre punts.
2. Un esquema XSD és un document `.xsd` amb arrel `xs:schema`; s'associa a un XML amb `xsi:noNamespaceSchemaLocation` (o `xsi:schemaLocation` si hi ha `targetNamespace`) i es valida amb `xmllint --noout --schema`.
3. Els **tipus simples** (`xs:string`, `xs:integer`, `xs:decimal`...) descriuen dades sense fills ni atributs, i es poden restringir amb `xs:restriction` i facetes (`minInclusive`, `pattern`, `enumeration`...).
4. Els **tipus complexos** (`xs:complexType`) descriuen elements amb fills i/o atributs; poden ser anònims (ús únic) o nomenats (reutilitzables en diversos elements).
5. Els **compositors** `sequence`, `choice` i `all` controlen orde i elecció dels fills; `minOccurs`/`maxOccurs` controlen quantes vegades pot (o ha de) aparéixer cadascun.
6. Els **atributs** es declaren amb `xs:attribute`, amb `use="required"`/`"optional"` i, opcionalment, `default`.
7. Extraure **tipus i grups reutilitzables** (`xs:simpleType`, `xs:complexType`, `xs:group` nomenats) evita repetir definicions i és la forma pràctica de documentar un esquema.
8. El flux de validació separa dos comprovacions distintes: que l'XML estiga **ben format** i que siga **vàlid** contra un esquema concret.

---

## 📚 Per a saber-ne més (opcional, no avaluable)

XSD no és l'única forma de descriure esquemes hui en dia: en el món de les APIs modernes, l'equivalent per a **JSON** (que ja coneixeu de la UD7) és **JSON Schema** — mateix objectiu (tipus, restriccions, validació automàtica), sintaxi molt distinta, pensada per a JSON en compte d'XML. Si en el futur treballeu amb APIs REST que documenten el seu format de dades, és molt probable que vos trobeu amb JSON Schema en compte d'XSD.

- Especificació oficial de XML Schema (W3C): [www.w3.org/XML/Schema](https://www.w3.org/XML/Schema)
- Tutorial interactiu d'XSD: [www.w3schools.com/xml/schema_intro.asp](https://www.w3schools.com/xml/schema_intro.asp)
- Validador XSD en línia: [www.freeformatter.com/xml-validator-xsd.html](https://www.freeformatter.com/xml-validator-xsd.html)
- JSON Schema (per a quan treballeu amb APIs): [json-schema.org](https://json-schema.org/)
</content>
</invoke>
