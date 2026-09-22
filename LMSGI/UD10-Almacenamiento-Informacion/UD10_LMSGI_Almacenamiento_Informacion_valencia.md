<div style="text-align: center;">

<img src="data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCA0MDAgNDAwIiB3aWR0aD0iMTgwIiBoZWlnaHQ9IjE4MCI+CiAgPGNpcmNsZSBjeD0iMjAwIiBjeT0iMjAwIiByPSIxNzAiIGZpbGw9IiNGMEZERkEiLz4KICA8Y2lyY2xlIGN4PSIyMDAiIGN5PSIyMDAiIHI9IjE3MCIgZmlsbD0ibm9uZSIgc3Ryb2tlPSIjOTlGNkU0IiBzdHJva2Utd2lkdGg9IjIiLz4KICA8ZWxsaXBzZSBjeD0iMjAwIiBjeT0iMTMwIiByeD0iODAiIHJ5PSIyNiIgZmlsbD0ibm9uZSIgc3Ryb2tlPSIjMEY3NjZFIiBzdHJva2Utd2lkdGg9IjEwIi8+CiAgPHBhdGggZD0iTSAxMjAgMTMwIEwgMTIwIDI3MCBRIDEyMCAyOTYgMjAwIDI5NiBRIDI4MCAyOTYgMjgwIDI3MCBMIDI4MCAxMzAiIGZpbGw9Im5vbmUiIHN0cm9rZT0iIzBGNzY2RSIgc3Ryb2tlLXdpZHRoPSIxMCIvPgogIDxwYXRoIGQ9Ik0gMTIwIDIwMCBRIDEyMCAyMjYgMjAwIDIyNiBRIDI4MCAyMjYgMjgwIDIwMCIgZmlsbD0ibm9uZSIgc3Ryb2tlPSIjMEY3NjZFIiBzdHJva2Utd2lkdGg9IjgiIG9wYWNpdHk9IjAuNTUiLz4KPC9zdmc+Cg==" width="180" alt="Logotip LMSGI"/>

<h1>Unitat 10</h1>
<h2>Emmagatzematge d'informació</h2>

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

1. Panorama de l'emmagatzematge d'informació: on viu un XML?
2. Bases de dades relacionals aplicades a XML: guardar i generar
3. XPath i XQuery: consultar XML amb el seu propi llenguatge
4. Bases de dades XML natives: què són i quan usar-les
5. Posar en marxa una base de dades XML nativa
6. Importar i exportar entre formats
7. Repte de classe
8. Resum de la unitat
9. Per a saber-ne més

<div style="page-break-after: always;"></div>

**RA cobert:** RA6 (ASIX, CA 6a-6i) / RA6 (DAW, CA 6a-6i) — *gestiona informació en format XML* / *gestiona informació en formats d'intercanvi de dades, analitzant i utilitzant tecnologies d'emmagatzematge i llenguatges de consulta*

> 💡 **Nota d'estudi**: fins ara heu treballat amb XML com **arxius solts** (`catalogo.xml`, `feed.xml`...). Esta unitat tanca el mòdul responent a una pregunta distinta: quan el volum d'informació creix, **on** es guarda de forma duradora, i **com** es consulta sense haver d'obrir l'arxiu sencer cada vegada? Vureu dos enfocaments que conviuen en la pràctica: guardar XML **dins** d'una base de dades relacional que ja coneixeu, i bases de dades pensades **específicament** per a XML.

**🗺️ Mapa del bloc — tres formes de guardar allò que ja és (o va ser) XML:**

```
                         On viu la informació?
                                   │
        ┌──────────────────────────┼──────────────────────────┐
        │                          │                           │
  Arxiu XML solt          XML en BD relacional          BD XML nativa
  (feed, configuració)    (SQLite, columnes o            (BaseX, eXist-db)
                            text complet)                 arbre indexat
        │                          │                           │
     Punt 1                     Punt 2                    Punts 4-5
                        Punt 3 — XPath/XQuery (aplica als dos de la dreta)
                        Punt 6 — importar/exportar entre els tres enfocaments
```

---

## 1. Panorama de l'emmagatzematge d'informació: on viu un XML?

Un arxiu `.xml` solt funciona bé per a intercanviar un document puntual (un feed, una factura, una configuració). Però quan cal **buscar**, **indexar** o **actualitzar** informació XML de forma habitual, un arxiu de text pla es queda curt: no hi ha forma eficient de buscar sense llegir-lo sencer, ni de garantir que dos processos no el modifiquen a la vegada.

Existixen, a grans trets, tres formes de guardar informació que en algun moment és (o va ser) XML:

| Enfocament | Idea | Exemple típic |
|---|---|---|
| **Arxiu XML solt** | El propi `.xml` és l'emmagatzematge | Un feed RSS, un arxiu de configuració |
| **XML dins d'una base de dades relacional** | El XML es guarda com a text (o es descompon en taules) dins d'un SGBD relacional ja conegut | Una columna `TEXT` amb el XML complet, o una taula normalitzada generada a partir d'ell |
| **Base de dades XML nativa** | Un sistema gestor pensat des de zero per a emmagatzemar i consultar arbres XML, sense passar per taules | BaseX, eXist-db |

> 🕰️ **Què seguix vigent i què està canviant**: guardar XML dins d'un SGBD relacional (primera fila de l'enfocament intermedi) continua sent, de bon tros, l'opció més habitual en projectes reals — reaprofita tota la infraestructura relacional que ja coneixeu d'altres mòduls. Les bases de dades XML natives tenen un nínxol més específic (sistemes documentals grans, editorials, arxius legals) on de veres cal indexar i consultar estructura XML complexa de forma directa — no són l'opció per defecte per a un projecte xicotet.

**🧪 Exercici 1 — Triar l'enfocament correcte**
Per a cadascun d'estos tres escenaris, indiqueu quin dels tres enfocaments de la taula usaríeu i per què en una frase: (a) el feed RSS del vostre pòdcast favorit, (b) un arxiu de configuració `pom.xml` d'un projecte Java que quasi mai canvia, (c) un sistema documental d'un ajuntament amb 200.000 expedients en XML que cal poder buscar per múltiples criteris a la vegada.

---

## 2. Bases de dades relacionals aplicades a XML: guardar i generar

La forma més senzilla de guardar un XML en una base de dades relacional és ficar-lo sencer en una columna de text:

```sql
CREATE TABLE series (
  id INTEGER PRIMARY KEY,
  titulo TEXT NOT NULL,
  anio INTEGER,
  xml_completo TEXT
);
```

Però el més habitual —i el que de veres aprofita una base de dades relacional— és **descompondre** el XML en columnes normals, com faríeu amb qualsevol altra taula:

```sql
INSERT INTO series (titulo, anio, valoracion)
VALUES ('Breaking Bad', 2008, 9.5);
```

I, al revés, **generar** XML a partir de files ja emmagatzemades — cosa que necessitareu constantment si un sistema extern vos demana les dades en XML encara que vosaltres les tingueu en taules:

```sql
SELECT '<serie><titulo>' || titulo || '</titulo><anio>' || anio || '</anio></serie>'
FROM series;
```

SQLite (el SGBD lleuger que ja coneixeu d'altres mòduls, i el més pràctic per a treballar en LliureX sense instal·lar un servidor) no té funcions XML natives tan completes com PostgreSQL o SQL Server —motors pensats per a projectes més grans—, així que en projectes xicotets esta concatenació manual, o un script (Python, per exemple) que llija les files i construïsca el XML, és el camí habitual.

**🧪 Exercici 2 — De files a XML i de XML a files**
Creeu una base de dades SQLite (`catalogo.db`) amb la taula `series` de dalt, i inseriu les mateixes 3 sèries del catàleg XML d'unitats anteriors. Escriviu una consulta SQL que genere, per a cada fila, una cadena `<serie>...</serie>` com en l'exemple. Després, al revés: partint del XML original (`catalogo.xml`), escriviu les sentències `INSERT` necessàries per a bolcar les seues dades en la taula.

---

## 3. XPath i XQuery: consultar XML amb el seu propi llenguatge

Quan el XML es consulta **directament** (sense passar per SQL), s'usa **XPath** —que ja coneixeu de la UD9, per a localitzar nodes— i **XQuery**, un llenguatge de consulta complet per a XML, pensat per a casos que XPath per si sol no cobrix: construir nous documents a partir dels resultats, combinar dades de diverses fonts, ordenar, agrupar.

```xquery
for $serie in doc("catalogo.xml")/catalogo/serie
where $serie/valoracion > 9
order by $serie/anio
return
  <resultado>
    <titulo>{data($serie/titulo)}</titulo>
    <anio>{data($serie/anio)}</anio>
  </resultado>
```

Esta construcció s'anomena **FLWOR** (*for, let, where, order by, return* — es pronuncia "flower"): recorre nodes amb `for`, filtra amb `where`, ordena amb `order by`, i construïx el resultat amb `return`, usant claus `{ }` per a inserir el valor d'una expressió dins de XML literal. Si vos resulta familiar, és perquè és, conceptualment, molt paregut a una consulta SQL amb `SELECT ... WHERE ... ORDER BY`, però retornant XML en compte de files.

> 📋 No cal memoritzar tota la sintaxi de XQuery — n'hi ha prou amb reconéixer i adaptar esta plantilla FLWOR (`for` / `where` / `order by` / `return`) a les vostres pròpies dades.

**🧪 Exercici 3 — La teua primera consulta XQuery**
Sense executar-lo encara (ho fareu en el punt 5, amb una base de dades XML nativa instal·lada), adapteu a mà la plantilla FLWOR de dalt per a seleccionar les sèries de `catalogo.xml` estrenades després de 2005, ordenades per valoració de major a menor.

---

## 4. Bases de dades XML natives: què són i quan usar-les

Una **base de dades XML nativa** emmagatzema els documents **com a arbres XML**, no com a text ni com a files de taula — indexa la mateixa estructura (elements, atributs, jerarquia) perquè les consultes XPath/XQuery siguen ràpides fins i tot amb milers de documents.

Les dos més conegudes i amb bon suport en Linux:

| Sistema | Característiques |
|---|---|
| **BaseX** | Open source, escrit en Java, inclou interfície gràfica i línia de comandes, molt usat en docència per ser fàcil d'instal·lar |
| **eXist-db** | Open source, orientat a aplicacions web completes sobre XML, més complex de configurar |

Treballarem amb **BaseX** per la seua senzillesa d'instal·lació en LliureX i perquè la seua GUI permet veure l'arbre del document mentres s'escriu la consulta — molt útil per a aprendre.

**🧪 Exercici 4 — Comparar enfocaments**
Retomeu l'escenari (c) de l'Exercici 1 (el sistema documental de l'ajuntament). Escriviu dos o tres frases explicant per què, en este cas concret, una base de dades XML nativa com BaseX pot ser millor opció que descompondre-ho tot en taules relacionals — penseu en què passaria si l'estructura dels expedients no és sempre exactament igual entre uns i altres.

---

## 5. Posar en marxa una base de dades XML nativa

Instal·lació de BaseX en LliureX (requerix Java, normalment ja instal·lat):

```bash
# Descarregar i instal·lar BaseX
wget https://files.basex.org/releases/latest/BaseX.zip
unzip BaseX.zip -d ~/basex
~/basex/bin/basexgui
```

> 🛟 **Pla B si `BaseX` no s'instal·la a l'aula** (xarxa restringida, permisos, versió de Java): teniu preparada d'avantmà una còpia de BaseX ja funcionant en la imatge de la VM portàtil que ja useu per a altres pràctiques, per a no perdre la sessió completa per un problema d'instal·lació d'última hora. Com a alternativa d'urgència, tota consulta que ací use `db:open(...)` es pot adaptar directament amb `doc("catalogo.xml")` (com en l'Exercici 3), que no necessita cap instal·lació.

Des de la GUI: `Database → Create Database`, seleccioneu `catalogo.xml`, i BaseX l'indexa. Amb la base de dades creada, la pestanya de consulta permet executar XQuery directament sobre ella:

```xquery
for $serie in db:open("catalogo")/catalogo/serie
where $serie/valoracion > 9
order by $serie/anio
return $serie/titulo/text()
```

L'única diferència amb l'Exercici 3 és `db:open("catalogo")` en compte de `doc("catalogo.xml")` — la primera consulta una base de dades ja indexada pel seu nom, la segona obri un arxiu solt directament. Per a actualitzar informació dins d'una base de dades XML nativa, XQuery Update afig sentències com `insert node`, `delete node` i `replace node`:

```xquery
insert node <serie><titulo>Fargo</titulo><anio>2014</anio><valoracion>8.9</valoracion></serie>
into db:open("catalogo")/catalogo
```

**🧪 Exercici 5 — Consultar i actualitzar en BaseX**
Instal·leu BaseX, creeu la base de dades `catalogo` a partir del vostre `catalogo.xml`, i executeu la consulta de l'Exercici 3 adaptada amb `db:open()`. Després, inseriu una sèrie nova amb `insert node` com en l'exemple, i torneu a executar la consulta per a comprovar que apareix en els resultats si complix la condició del filtre.

---

## 6. Importar i exportar entre formats

En un projecte real, la informació quasi mai viu en un únic sistema durant tota la seua vida: naix en una base de dades relacional, s'exporta a XML per a enviar-la a un altre sistema, eixe sistema la torna transformada, i cal tornar a importar-la. Les ferramentes que ja coneixeu del mòdul encaixen ací, encadenades:

```bash
# Exportar una taula SQLite completa a XML (amb un script, o generant el XML per SQL com en el punt 2)
sqlite3 catalogo.db "SELECT titulo, anio, valoracion FROM series;" -header -csv > series.csv

# De CSV a XML: un script senzill en Python, o ferramentes dedicades
python3 -c "
import csv
with open('series.csv') as f:
    reader = csv.DictReader(f)
    print('<catalogo>')
    for fila in reader:
        print(f'  <serie><titulo>{fila[\"titulo\"]}</titulo><anio>{fila[\"anio\"]}</anio></serie>')
    print('</catalogo>')
" > series_generado.xml
```

I en direcció contrària, un XML rebut de fora es pot importar de nou a taules relacionals amb les sentències `INSERT` que ja vau construir en l'Exercici 2 — generades a mà per a aprendre el mecanisme, o amb un script que recorra el XML (per exemple, amb la llibreria `xml.etree.ElementTree` de Python) i genere els `INSERT` automàticament per a qualsevol nombre de registres.

**🧪 Exercici 6 — El cicle complet**
Partint de `catalogo.db` (Exercici 2), exporteu la taula `series` a CSV amb `sqlite3`, i després convertiu eixe CSV a un XML `series_generado.xml` amb un script com el de dalt (podeu adaptar-lo). Compareu `series_generado.xml` amb el `catalogo.xml` original: han de contindre la mateixa informació, encara que l'estructura d'etiquetes pot variar lleugerament.

---

## 7. Repte de classe

Partint del domini propi que vau triar en els reptes de la UD8/UD9 (o un de nou), completeu el cicle d'esta unitat:

1. Una **taula relacional** en SQLite amb almenys 5 files.
2. Una consulta SQL que **genere XML** a partir d'eixa taula.
3. Una **consulta FLWOR** (amb `doc()` o `db:open()`, segons tingueu BaseX disponible) que filtre i ordene eixes mateixes dades.

> 📋 No cal memoritzar la sintaxi exacta de XQuery ni de SQL — tindreu sempre a mà la xuleta de la unitat.

---

## Resum de la unitat

1. Un arxiu XML solt servix per a intercanvi puntual, però quan cal **buscar, indexar o actualitzar** informació de forma habitual, cal un sistema d'emmagatzematge: XML dins d'una base de dades relacional, o una base de dades XML nativa.
2. Guardar XML en un SGBD relacional es fa descomponent-lo en columnes normals (el més habitual) o guardant-lo sencer com a text; generar XML a partir de files es fa amb concatenació SQL o un script.
3. **XQuery** és un llenguatge de consulta complet per a XML, amb estructura **FLWOR** (`for`/`let`/`where`/`order by`/`return`), conceptualment paregut a una consulta SQL però retornant XML.
4. Una **base de dades XML nativa** (BaseX, eXist-db) emmagatzema i consulta els documents com a arbres, sense passar per taules — útil quan l'estructura és complexa o variable entre documents.
5. BaseX s'instal·la i s'usa fàcilment en LliureX; les seues consultes usen `db:open("nombre")` per a bases de dades ja creades, i XQuery Update (`insert node`, `delete node`, `replace node`) per a modificar contingut.
6. En un flux real, la informació es mou entre formats constantment (relacional → XML → CSV → XML...) — les ferramentes d'exportació/importació encadenen el que s'ha aprés en tot el mòdul.

---

## 📚 Per a saber-ne més (opcional, no avaluable)

El concepte de "base de dades que no usa taules relacionals" que heu vist ací per a XML (BaseX) és un cas particular d'una cosa més àmplia anomenada **bases de dades NoSQL** — sistemes que emmagatzemen documents JSON, grafs, parells clau-valor, etc., en compte de taules. Si en el futur treballeu amb MongoDB (documents JSON) o Neo4j (grafs), estareu aplicant la mateixa idea que ací: adaptar el sistema d'emmagatzematge a la forma natural de les dades, en compte de forçar-les sempre a files i columnes.

- Documentació oficial de BaseX: [docs.basex.org](https://docs.basex.org/)
- Especificació oficial de XQuery 3.1 (W3C): [www.w3.org/TR/xquery-31](https://www.w3.org/TR/xquery-31/)
- eXist-db, alternativa a BaseX: [exist-db.org](https://exist-db.org/)
- Introducció a bases de dades NoSQL: [www.mongodb.com/nosql-explained](https://www.mongodb.com/nosql-explained)