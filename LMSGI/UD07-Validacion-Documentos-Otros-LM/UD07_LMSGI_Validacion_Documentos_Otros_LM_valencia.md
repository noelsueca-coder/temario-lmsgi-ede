<div style="text-align: center;">

<img src="data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCA0MDAgNDAwIiB3aWR0aD0iMTgwIiBoZWlnaHQ9IjE4MCI+CiAgPGNpcmNsZSBjeD0iMjAwIiBjeT0iMjAwIiByPSIxNzAiIGZpbGw9IiNGMEZERkEiLz4KICA8Y2lyY2xlIGN4PSIyMDAiIGN5PSIyMDAiIHI9IjE3MCIgZmlsbD0ibm9uZSIgc3Ryb2tlPSIjOTlGNkU0IiBzdHJva2Utd2lkdGg9IjIiLz4KICA8cmVjdCB4PSIxMTUiIHk9IjkwIiB3aWR0aD0iMTcwIiBoZWlnaHQ9IjIyMCIgcng9IjEyIiBmaWxsPSJub25lIiBzdHJva2U9IiMwRjc2NkUiIHN0cm9rZS13aWR0aD0iMTAiLz4KICA8bGluZSB4MT0iMTQ1IiB5MT0iMTQwIiB4Mj0iMjU1IiB5Mj0iMTQwIiBzdHJva2U9IiMwRjc2NkUiIHN0cm9rZS13aWR0aD0iOSIgc3Ryb2tlLWxpbmVjYXA9InJvdW5kIi8+CiAgPGxpbmUgeDE9IjE0NSIgeTE9IjE3NSIgeDI9IjI1NSIgeTI9IjE3NSIgc3Ryb2tlPSIjMEY3NjZFIiBzdHJva2Utd2lkdGg9IjkiIHN0cm9rZS1saW5lY2FwPSJyb3VuZCIgb3BhY2l0eT0iMC41NSIvPgogIDxsaW5lIHgxPSIxNDUiIHkxPSIyMTAiIHgyPSIyMjAiIHkyPSIyMTAiIHN0cm9rZT0iIzBGNzY2RSIgc3Ryb2tlLXdpZHRoPSI5IiBzdHJva2UtbGluZWNhcD0icm91bmQiIG9wYWNpdHk9IjAuNTUiLz4KICA8Y2lyY2xlIGN4PSIyNzAiIGN5PSIyNTUiIHI9IjQ2IiBmaWxsPSIjRjBGREZBIiBzdHJva2U9IiMwRjc2NkUiIHN0cm9rZS13aWR0aD0iMTAiLz4KICA8cGF0aCBkPSJNIDI1MCAyNTUgTCAyNjQgMjcwIEwgMjkyIDIzOCIgZmlsbD0ibm9uZSIgc3Ryb2tlPSIjMEY3NjZFIiBzdHJva2Utd2lkdGg9IjEwIiBzdHJva2UtbGluZWNhcD0icm91bmQiIHN0cm9rZS1saW5lam9pbj0icm91bmQiLz4KPC9zdmc+Cg==" width="180" alt="Logotip LMSGI"/>

<h1>Unitat 7</h1>
<h2>Validació de documents i altres llenguatges de marques</h2>

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

1. Sindicació de continguts: què és un canal RSS
2. Tecnologia i estructura d'un canal RSS/Atom
3. Validar documents XML
4. Validar documents HTML
5. Validar fulls d'estil CSS
6. JSON: sintaxi i validació
7. YAML: sintaxi
8. Resum de la unitat
9. Per a saber-ne més

<div style="page-break-after: always;"></div>

**RA cobert:** RA3 (ASIX, CA 3a-3g) / RA2 (DAW, CA 2h-2j) — *genera canals de continguts analitzant i utilitzant tecnologies de sindicació* / *utilitza llenguatges de marques per a la transmissió i presentació d'informació a través de la web*

> 💡 **Nota d'estudi**: en la UD1 ja vas vore de passada un feed RSS amb espais de noms, i una taula comparant XML/HTML/JSON/Markdown. Esta unitat retoma eixe fil i el tanca: aprofundim en la sindicació de continguts, i aprenem per fi a escriure JSON i YAML correctament, no només a reconéixer-los. També aprens a **validar** cadascun d'estos llenguatges — comprovar automàticament si un document complix les regles de la seua pròpia sintaxi, sense haver de revisar-lo a ull.

---

## 1. Sindicació de continguts: què és un canal RSS

Quan seguixes un pòdcast, un blog o un canal de notícies sense haver de visitar la pàgina cada dia per a vore si hi ha alguna cosa nova, hi ha una tecnologia concreta fent açò possible: la **sindicació de continguts**. Un lloc publica un arxiu especial, el **canal** (o *feed*), que s'actualitza cada vegada que hi ha contingut nou — i el teu lector de feeds (o la teua app de pòdcasts) revisa eixe arxiu periòdicament per a avisar-te, sense que hages d'anar tu a comprovar-ho.

El format més usat per a açò és **RSS** (*Really Simple Syndication*) — que, com ja saps des de la UD1, és XML: un vocabulari concret amb etiquetes com `<channel>`, `<item>`, `<title>`, pensat específicament per a descriure una llista de continguts publicats en orde cronològic.

> 🕰️ **Què seguix vigent i què no**: RSS va nàixer en 1999 i va tindre la seua època daurada amb els lectors de feeds d'escriptori (Google Reader, tancat en 2013, va ser el més popular). Hui el seu paper principal s'ha desplaçat als **pòdcasts** — cada episodi nou d'un pòdcast es distribuïx quasi sempre mitjançant un feed RSS, encara que l'app que uses per a escoltar-lo no ho mostre com a tal. **Atom** és una alternativa a RSS creada en 2005 per a corregir algunes ambigüitats de la seua especificació original — tècnicament més neta, però hui és molt menys comuna: la immensa majoria de pòdcasts i blogs que encara publiquen un feed usen RSS. Queda't amb la idea: **Atom existix per a entendre el concepte general; en la pràctica, RSS és el que us trobareu.**

**🧪 Exercici 1 — Troba un feed real**
Busca un pòdcast o blog que seguisques (o qualsevol que t'interesse) i localitza el seu feed RSS: prova a afegir `/feed`, `/rss` o `/feed.xml` a l'URL principal, o busca en la web "nom del pòdcast + RSS feed". Obri'l amb Firefox (pot ser que es mostre com a XML en brut, o que el navegador el redirigisca a text pla) i identifica almenys 3 etiquetes `<item>` distintes, cadascuna amb el seu `<title>`.

---

## 2. Tecnologia i estructura d'un canal RSS/Atom

Retomem el feed de la UD1, esta vegada fixant-nos en la seua estructura completa, no només en els namespaces:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<rss version="2.0">
  <channel>
    <title>Podcast de Informática</title>
    <link>https://misitioweb.es/podcast</link>
    <description>Un pódcast semanal sobre desarrollo y sistemas</description>
    <language>es-es</language>

    <item>
      <title>Episodio 1: Introducción a XML</title>
      <link>https://misitioweb.es/podcast/episodio-1</link>
      <description>En este episodio hablamos de los fundamentos de XML.</description>
      <pubDate>Mon, 15 Sep 2026 08:00:00 +0200</pubDate>
      <guid>https://misitioweb.es/podcast/episodio-1</guid>
    </item>
  </channel>
</rss>
```

- `<channel>`: l'element arrel de contingut — descriu el canal en si (títol, enllaç, descripció, idioma).
- `<item>`: cada contingut individual publicat (un episodi, un article) — pot haver-hi tants com es vulga, cadascun amb el seu propi `<title>`, `<link>` i `<description>`.
- `<pubDate>`: la data de publicació, en un format concret (RFC 822) — és el que usa el lector de feeds per a saber què és nou des de l'última vegada que el va consultar.
- `<guid>` (*globally unique identifier*): un identificador únic d'eixe `<item>` — normalment la seua pròpia URL — perquè el lector de feeds sàpia que, encara que el contingut canvie lleugerament, seguix sent "el mateix episodi" i no el mostre com a nou dos vegades.

**Estructura equivalent en Atom** (mateix contingut, vocabulari distint):

```xml
<?xml version="1.0" encoding="UTF-8"?>
<feed xmlns="http://www.w3.org/2005/Atom">
  <title>Podcast de Informática</title>
  <link href="https://misitioweb.es/podcast"/>
  <updated>2026-09-15T08:00:00+02:00</updated>

  <entry>
    <title>Episodio 1: Introducción a XML</title>
    <link href="https://misitioweb.es/podcast/episodio-1"/>
    <id>https://misitioweb.es/podcast/episodio-1</id>
    <updated>2026-09-15T08:00:00+02:00</updated>
    <summary>En este episodio hablamos de los fundamentos de XML.</summary>
  </entry>
</feed>
```

La correspondència és quasi directa: `<channel>` ↔ `<feed>`, `<item>` ↔ `<entry>`, `<pubDate>` ↔ `<updated>` (encara que Atom usa el format de data ISO 8601 que ja coneixes de XML Schema en unitats següents, no el format RFC 822 de RSS).

**🧪 Exercici 2 — Construïx el teu propi canal**
Crea un feed RSS per a un blog inventat, amb un `<channel>` complet (títol, link, description) i almenys 3 `<item>` distints, cadascun amb títol, enllaç, descripció, data de publicació (`<pubDate>`) i `<guid>`. Afig a més un espai de noms personalitzat (com en la UD1) amb almenys una etiqueta pròpia en cada `<item>` — per exemple, una categoria o un temps de lectura estimat.

---

## 3. Validar documents XML

Ja saps des de la UD1 què significa que un XML estiga **ben format**. **Validar** és un pas més enllà: comprovar que, a més de ben format, el document complix una estructura concreta i esperada — el vocabulari correcte, els elements en l'orde correcte, els tipus de dada correctes. Un document pot estar perfectament ben format i encara així no ser vàlid segons un vocabulari concret (per exemple, un RSS ben format però sense l'etiqueta `<channel>` obligatòria).

Per a validar cal comparar el document contra una **definició** de la seua estructura — un DTD (ja vist en la UD1) o un **XML Schema** (el voràs en profunditat en la UD8). Hui validem; construir els teus propis esquemes ho aprendràs més avant — no cal que en domines la sintaxi encara. Per ara, n'hi ha prou que sàpies que existixen **validadors** que fan eixa comprovació automàticament:

```bash
# Amb xmllint (ve instal·lat en la majoria de distribucions Linux, inclòs LliureX)
$ xmllint --noout miarchivo.xml
# Sense eixida = el document està ben format
# Amb un DTD o Schema:
$ xmllint --noout --schema esquema.xsd miarchivo.xml
```

`xmllint --noout` comprova només el bon format (sense generar cap eixida si tot està bé); afegint `--schema` compara a més contra un XML Schema i avisa de qualsevol discrepància amb l'estructura esperada.

**🧪 Exercici 3 — Valida el teu propi feed**
Guarda el feed RSS de l'Exercici 2 com a `feed.xml` i valida el seu bon format amb `xmllint --noout feed.xml` des del terminal de LliureX (instal·la `libxml2-utils` amb `sudo apt install libxml2-utils` si l'orde no existix). Trenca deliberadament una etiqueta (lleva un tancament) i torna a executar l'orde — anota el missatge d'error exacte que dóna `xmllint`.

---

## 4. Validar documents HTML

Un HTML pot "funcionar" en el navegador —que el mostre sense errors visibles— i encara així tindre errors de sintaxi que el navegador simplement perdona, com ja vas vore en la UD1 en comparar el comportament de XML i HTML davant etiquetes mal tancades. Validar un HTML és comprovar que complix realment l'especificació oficial, més enllà del que el navegador estiga disposat a tolerar.

El validador de referència és el del mateix **W3C**: [validator.w3.org](https://validator.w3.org) — permet validar per URL, pujant un arxiu, o enganxant el codi directament. Assenyala errors (etiquetes sense tancar, atributs mal escrits, anidament incorrecte) i avisos (pràctiques desaconsellades que no trenquen la pàgina, però no són ideals).

```html
<!-- Exemple amb errors deliberats -->
<img src="foto.jpg">
<p>Texto sin cerrar
<div><span>Anidamiento cruzado</div></span>
```

Este HTML es veuria en el navegador sense queixar-se (el navegador "endevina" el que volies dir), però el validador assenyalaria: falta l'atribut `alt` en `<img>` (accessibilitat), el `<p>` mai es tanca, i el `<span>` es tanca després que el seu pare `<div>`, creuant l'anidament — exactament el mateix tipus d'error que ja vas identificar en XML en la UD1, només que ací el navegador no atura res.

**🧪 Exercici 4 — Valida un HTML propi**
Agafa qualsevol HTML que hages escrit en unitats anteriors (per exemple, de la UD3) i passa'l pel validador del W3C, enganxant el codi directament. Anota quants errors i avisos dóna, corregix almenys 3 d'ells, i torna a validar fins que el resultat siga "Document checking completed. No errors or warnings to show."

---

## 5. Validar fulls d'estil CSS

El mateix W3C manté també un validador específic per a CSS: [jigsaw.w3.org/css-validator](https://jigsaw.w3.org/css-validator/) — detecta propietats mal escrites, valors incorrectes per a una propietat concreta, o sintaxi invàlida (una clau sense tancar, un punt i coma oblidat).

```css
/* Exemple amb errors deliberats */
.tarjeta {
  colorr: teal;              /* propietat mal escrita */
  padding: 10pixels;         /* unitat invàlida */
  border-radius: 8px
}
```

Ací el validador assenyalaria `colorr` com una propietat desconeguda (probable error tipogràfic de `color`), `10pixels` com un valor no reconegut (la unitat correcta és `px`), i avisaria que falta el punt i coma després de `8px`.

⚠️ **Per què importa validar CSS encara que "es veja bé"**: un navegador ignora silenciosament qualsevol declaració que no entén (com `colorr: teal;`) i seguix aplicant la resta de la regla sense avisar de res — el resultat visual pot semblar correcte per pura casualitat (per exemple, si eixe color no era crític), ocultant un error que sí donarà problemes en un altre navegador més estricte o en una regla més complexa.

**🧪 Exercici 5 — Valida el teu CSS**
Agafa l'`estilos.css` de la UD4 o la UD5 i passa'l pel validador CSS del W3C. Si no dóna cap error (és habitual, si has seguit bé la sintaxi), introduïx deliberadament 2 errors típics (una propietat mal escrita i una unitat invàlida) i comprova que el validador els detecta correctament.

---

> 🧭 **A partir d'ací, formats complementaris**: els punts 1-5 (sindicació i validació de XML/HTML/CSS) són el nucli d'esta unitat. JSON i YAML són formats igual d'útils en la pràctica, però no els dediques més temps del necessari — no són el centre d'esta UP. Perquè no se't barregen entre si:
>
> | Format | Ús principal |
> |---|---|
> | JSON | Intercanvi de dades en APIs |
> | YAML | Arxius de configuració |

## 6. JSON: sintaxi i validació

**JSON** (*JavaScript Object Notation*) és el format d'intercanvi de dades més usat hui en APIs web — ja el vas vore mencionat en la UD1, ara aprens a escriure'l. A diferència de XML, no és un llenguatge de marques (no té etiquetes d'obertura/tancament): és una notació basada en parells clau-valor, presa de la sintaxi d'objectes de JavaScript (d'ahí el nom), encara que hui s'usa de forma independent del llenguatge.

```json
{
  "titulo": "One Piece",
  "estudio": "Toei Animation",
  "episodios": 1120,
  "enEmision": true,
  "generos": ["aventura", "fantasía", "shonen"],
  "clasificacion": null
}
```

**Regles de sintaxi, totes obligatòries** (a diferència de XML, JSON no té cap element opcional en la seua gramàtica bàsica):

| Regla | Detall |
|---|---|
| Claus sempre entre cometes dobles | `"titulo"`, mai `titulo` ni `'titulo'` |
| Valors de text entre cometes dobles | `"One Piece"` |
| Nombres sense cometes | `1120`, no `"1120"` |
| Booleans sense cometes | `true` / `false` (en minúscules) |
| Absència de valor | `null` |
| Llistes entre claudàtors | `["aventura", "fantasía"]` |
| Objectes entre claus | `{ "titulo": "...", ... }` |
| Sense coma després de l'últim element | Un error molt comú en editar a mà |

⚠️ **L'error més habitual**: deixar una coma després de l'últim element d'una llista o objecte (*trailing comma*). A diferència de JavaScript, on de vegades es tolera, en JSON estricte és un error de sintaxi que invalida tot el document — cap parser JSON estàndard l'accepta.

**Validar JSON**: en ser una gramàtica molt més simple que XML (sense DTD ni Schema propis), n'hi ha prou amb comprovar que la sintaxi és correcta. Es pot fer en línia (`jsonlint.com`) o des del terminal:

```bash
$ python3 -m json.tool miarchivo.json
# Si és vàlid, el torna a imprimir formatat
# Si no ho és, assenyala la línia i columna exactes de l'error
```

**🧪 Exercici 6 — De XML a JSON**
Convertix el catàleg de sèries de la UD1 (el de `<catalogo>` amb diverses `<serie>`) a JSON: una llista d'objectes, cadascun amb `titulo`, `estudio`, `episodios` (com a número, no com a text) i `enEmision` (com a booleà). Valida'l amb `python3 -m json.tool` i corregix qualsevol error de sintaxi que aparega.

---

## 7. YAML: sintaxi

**YAML** (*YAML Ain't Markup Language* — un acrònim recursiu, a propòsit) és un altre format d'intercanvi de dades, pensat per a ser més llegible per humans que JSON: usa la indentació (els espais al principi de línia) per a marcar l'estructura, en compte de claus i claudàtors.

```yaml
titulo: One Piece
estudio: Toei Animation
episodios: 1120
enEmision: true
generos:
  - aventura
  - fantasía
  - shonen
clasificacion: null
```

Este YAML representa exactament les mateixes dades que el JSON del punt 6 — fixa't que no cal ni una cometa, ni una clau, ni una coma. Les regles bàsiques:

| Element | Sintaxi |
|---|---|
| Parell clau-valor | `clave: valor`, amb un espai després dels dos punts |
| Llista | Cada element en la seua pròpia línia, precedit de `- ` (guió i espai) |
| Anidament | Es marca amb **indentació** (espais, mai tabuladors) — com més espais, més profund |
| Comentari | `# així`, igual que en Python |

```yaml
serie:
  titulo: One Piece
  estudio: Toei Animation
  temporadas:
    - numero: 1
      episodios: 61
    - numero: 2
      episodios: 55
```

⚠️ **La indentació no és cosmètica, és sintaxi**: a diferència d'HTML o XML, on la indentació només ajuda a llegir el codi però no afecta el resultat, en YAML **un espai de més o de menys canvia l'estructura del document** — és la font d'errors més comuna per a qui comença amb YAML, i també la seua major crítica.

> 📡 **Per què importa hui**: YAML és el format estàndard dels arxius de configuració en ferramentes de desenvolupament actuals — Docker Compose, GitHub Actions, Kubernetes, i molts frameworks l'usen per als seus arxius de configuració, precisament per ser més llegible que XML o JSON per a arxius que edita una persona a mà.

**🧪 Exercici 7 — De JSON a YAML**
Convertix a mà el JSON de l'Exercici 6 (el teu catàleg de sèries) a YAML, respectant la indentació. Després, valida que la indentació és correcta amb un validador en línia (`yamllint.com`) — introduïx deliberadament un error d'indentació (lleva o afig un espai en una línia) i comprova que ho detecta.

---

## 🎯 Repte de classe

Tria un tema teu (una col·lecció, un catàleg, una llista de tasques...) i representa'l en **els quatre formats** vistos en esta unitat i en la UD1: un feed RSS (amb almenys 2 `<item>`), el mateix contingut en XML "propi" (les teues pròpies etiquetes, com en la UD1), en JSON i en YAML. Valida els tres primers amb les ferramentes vistes en els punts 3, 4 (o 5, si prefereixes representar-ho com a CSS d'una pàgina que ho mostre) i 6-7. Per a acabar, escriu un breu informe (5-6 línies) comparant els quatre formats: quin t'ha resultat més ràpid d'escriure, quin més fàcil de llegir, i quin triaries per a cadascun d'estos casos: una API web, un arxiu de configuració, i una nota personal.

---

<div style="page-break-after: always;"></div>

## Resum de la unitat

**1. Sindicació de continguts** Un canal (*feed*) permet que un lector s'assabente de contingut nou sense visitar la web — el format més usat és RSS, hui sobretot per a pòdcasts; Atom és la seua alternativa tècnicament més neta però molt menys estesa.

**2. Tecnologia i estructura de RSS/Atom** `<channel>`/`<item>` en RSS equivalen a `<feed>`/`<entry>` en Atom; `<pubDate>`/`<updated>` marquen quan hi ha contingut nou, i `<guid>`/`<id>` eviten que un mateix contingut es mostre com a nou dos vegades.

**3. Validar XML** Més enllà del bon format (UD1), validar comprova que el document complix una estructura concreta definida en un DTD o Schema — ferramentes com `xmllint` ho fan des del terminal.

**4. Validar HTML** El validador del W3C detecta errors que el navegador perdona silenciosament (etiquetes sense tancar, anidament creuat, atributs obligatoris absents).

**5. Validar CSS** El validador CSS del W3C detecta propietats mal escrites o valors invàlids que el navegador, de nou, ignora sense avisar en compte de donar error.

**6. JSON** Notació de parells clau-valor sense etiquetes, amb regles de sintaxi estrictes i sense excepcions (cometes dobles obligatòries, sense coma final) — es valida amb ferramentes com `json.tool` de Python.

**7. YAML** Format de configuració llegible per humans, basat en indentació en compte de claus o claudàtors — la indentació és sintaxi, no només estètica, i és la font d'error més comuna.

---

## 📚 Per a saber-ne més (opcional, no avaluable)

> 📡 **Actualitat**: encara que XML seguix sent el format dels feeds RSS/Atom, en la resta de la web JSON domina clarament sobre XML per a l'intercanvi de dades entre sistemes (APIs REST) per ser més lleuger i més simple de generar i llegir des de codi — és la raó per la qual XML tot just s'usa hui per a nova integració d'APIs web, encara que seguisca sent imprescindible en els formats i sectors vistos en la UD1 (Office, facturació electrònica, SEPA...).

- Validador d'HTML del W3C: https://validator.w3.org/
- Validador de CSS del W3C: https://jigsaw.w3.org/css-validator/
- Especificació oficial de JSON: https://www.json.org/json-es.html
- Especificació de YAML: https://yaml.org/spec/
