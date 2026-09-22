<div style="text-align: center;">

<img src="data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCA0MDAgNDAwIiB3aWR0aD0iMTgwIiBoZWlnaHQ9IjE4MCI+CiAgPGNpcmNsZSBjeD0iMjAwIiBjeT0iMjAwIiByPSIxNzAiIGZpbGw9IiNGMEZERkEiLz4KICA8Y2lyY2xlIGN4PSIyMDAiIGN5PSIyMDAiIHI9IjE3MCIgZmlsbD0ibm9uZSIgc3Ryb2tlPSIjOTlGNkU0IiBzdHJva2Utd2lkdGg9IjIiLz4KICA8cmVjdCB4PSIxMTUiIHk9IjkwIiB3aWR0aD0iMTcwIiBoZWlnaHQ9IjIyMCIgcng9IjEyIiBmaWxsPSJub25lIiBzdHJva2U9IiMwRjc2NkUiIHN0cm9rZS13aWR0aD0iMTAiLz4KICA8bGluZSB4MT0iMTQ1IiB5MT0iMTQwIiB4Mj0iMjU1IiB5Mj0iMTQwIiBzdHJva2U9IiMwRjc2NkUiIHN0cm9rZS13aWR0aD0iOSIgc3Ryb2tlLWxpbmVjYXA9InJvdW5kIi8+CiAgPGxpbmUgeDE9IjE0NSIgeTE9IjE3NSIgeDI9IjI1NSIgeTI9IjE3NSIgc3Ryb2tlPSIjMEY3NjZFIiBzdHJva2Utd2lkdGg9IjkiIHN0cm9rZS1saW5lY2FwPSJyb3VuZCIgb3BhY2l0eT0iMC41NSIvPgogIDxsaW5lIHgxPSIxNDUiIHkxPSIyMTAiIHgyPSIyMjAiIHkyPSIyMTAiIHN0cm9rZT0iIzBGNzY2RSIgc3Ryb2tlLXdpZHRoPSI5IiBzdHJva2UtbGluZWNhcD0icm91bmQiIG9wYWNpdHk9IjAuNTUiLz4KICA8Y2lyY2xlIGN4PSIyNzAiIGN5PSIyNTUiIHI9IjQ2IiBmaWxsPSIjRjBGREZBIiBzdHJva2U9IiMwRjc2NkUiIHN0cm9rZS13aWR0aD0iMTAiLz4KICA8cGF0aCBkPSJNIDI1MCAyNTUgTCAyNjQgMjcwIEwgMjkyIDIzOCIgZmlsbD0ibm9uZSIgc3Ryb2tlPSIjMEY3NjZFIiBzdHJva2Utd2lkdGg9IjEwIiBzdHJva2UtbGluZWNhcD0icm91bmQiIHN0cm9rZS1saW5lam9pbj0icm91bmQiLz4KPC9zdmc+Cg==" width="180" alt="Logo LMSGI"/>

<h1>Unidad 7</h1>
<h2>Validación de documentos y otros lenguajes de marcas</h2>

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

1. Sindicación de contenidos: qué es un canal RSS
2. Tecnología y estructura de un canal RSS/Atom
3. Validar documentos XML
4. Validar documentos HTML
5. Validar hojas de estilo CSS
6. JSON: sintaxis y validación
7. YAML: sintaxis
8. Resumen de la unidad
9. Para saber más

<div style="page-break-after: always;"></div>

**RA cubierto:** RA3 (ASIX, CA 3a-3g) / RA2 (DAW, CA 2h-2j) — *genera canales de contenidos analizando y utilizando tecnologías de sindicación* / *utiliza lenguajes de marcas para la transmisión y presentación de información a través de la web*

> 💡 **Nota de estudio**: en la UD1 ya viste de pasada un feed RSS con espacios de nombres, y una tabla comparando XML/HTML/JSON/Markdown. Esta unidad retoma ese hilo y lo cierra: profundizamos en la sindicación de contenidos, y aprendemos por fin a escribir JSON y YAML correctamente, no solo a reconocerlos. También aprendes a **validar** cada uno de estos lenguajes — comprobar automáticamente si un documento cumple las reglas de su propia sintaxis, sin tener que revisarlo a ojo.

---

## 1. Sindicación de contenidos: qué es un canal RSS

Cuando sigues un pódcast, un blog o un canal de noticias sin tener que visitar la página cada día para ver si hay algo nuevo, hay una tecnología concreta haciendo eso posible: la **sindicación de contenidos**. Un sitio publica un archivo especial, el **canal** (o *feed*), que se actualiza cada vez que hay contenido nuevo — y tu lector de feeds (o tu app de pódcasts) revisa ese archivo periódicamente para avisarte, sin que tengas que ir tú a comprobarlo.

El formato más usado para esto es **RSS** (*Really Simple Syndication*) — que, como ya sabes desde la UD1, es XML: un vocabulario concreto con etiquetas como `<channel>`, `<item>`, `<title>`, pensado específicamente para describir una lista de contenidos publicados en orden cronológico.

> 🕰️ **Qué sigue vigente y qué no**: RSS nació en 1999 y tuvo su época dorada con los lectores de feeds de escritorio (Google Reader, cerrado en 2013, fue el más popular). Hoy su papel principal se ha desplazado a los **pódcasts** — cada episodio nuevo de un pódcast se distribuye casi siempre mediante un feed RSS, aunque la app que usas para escucharlo no lo muestre como tal. **Atom** es una alternativa a RSS creada en 2005 para corregir algunas ambigüedades de su especificación original — técnicamente más limpia, pero hoy es mucho menos común: la inmensa mayoría de pódcasts y blogs que aún publican un feed usan RSS. Quédate con la idea: **Atom existe para entender el concepto general; en la práctica, RSS es lo que os vais a encontrar.**

**🧪 Ejercicio 1 — Encuentra un feed real**
Busca un pódcast o blog que sigas (o cualquiera que te interese) y localiza su feed RSS: prueba a añadir `/feed`, `/rss` o `/feed.xml` a la URL principal, o busca en la web "nombre del pódcast + RSS feed". Ábrelo con Firefox (puede que se muestre como XML en bruto, o que el navegador lo redirija a texto plano) e identifica al menos 3 etiquetas `<item>` distintas, cada una con su `<title>`.

---

## 2. Tecnología y estructura de un canal RSS/Atom

Retomamos el feed de la UD1, esta vez fijándonos en su estructura completa, no solo en los namespaces:

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

- `<channel>`: el elemento raíz de contenido — describe el canal en sí (título, enlace, descripción, idioma).
- `<item>`: cada contenido individual publicado (un episodio, un artículo) — puede haber tantos como se quiera, cada uno con su propio `<title>`, `<link>` y `<description>`.
- `<pubDate>`: la fecha de publicación, en un formato concreto (RFC 822) — es lo que usa el lector de feeds para saber qué es nuevo desde la última vez que lo consultó.
- `<guid>` (*globally unique identifier*): un identificador único de ese `<item>` — normalmente su propia URL — para que el lector de feeds sepa que, aunque el contenido cambie ligeramente, sigue siendo "el mismo episodio" y no lo muestre como nuevo dos veces.

**Estructura equivalente en Atom** (mismo contenido, vocabulario distinto):

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

La correspondencia es casi directa: `<channel>` ↔ `<feed>`, `<item>` ↔ `<entry>`, `<pubDate>` ↔ `<updated>` (aunque Atom usa el formato de fecha ISO 8601 que ya conoces de XML Schema en unidades siguientes, no el formato RFC 822 de RSS).

**🧪 Ejercicio 2 — Construye tu propio canal**
Crea un feed RSS para un blog inventado, con un `<channel>` completo (título, link, description) y al menos 3 `<item>` distintos, cada uno con título, enlace, descripción, fecha de publicación (`<pubDate>`) y `<guid>`. Añade además un espacio de nombres personalizado (como en la UD1) con al menos una etiqueta propia en cada `<item>` — por ejemplo, una categoría o un tiempo de lectura estimado.

---

## 3. Validar documentos XML

Ya sabes desde la UD1 qué significa que un XML esté **bien formado**. **Validar** es un paso más allá: comprobar que, además de bien formado, el documento cumple una estructura concreta y esperada — el vocabulario correcto, los elementos en el orden correcto, los tipos de dato correctos. Un documento puede estar perfectamente bien formado y aun así no ser válido según un vocabulario concreto (por ejemplo, un RSS bien formado pero sin la etiqueta `<channel>` obligatoria).

Para validar hace falta comparar el documento contra una **definición** de su estructura — un DTD (ya visto en la UD1) o un **XML Schema** (lo verás en profundidad en la UD8). Hoy validamos; construir tus propios esquemas lo aprenderás más adelante — no hace falta que domines su sintaxis todavía. Por ahora, basta con que sepas que existen **validadores** que hacen esa comprobación automáticamente:

```bash
# Con xmllint (viene instalado en la mayoría de distribuciones Linux, incluido LliureX)
$ xmllint --noout miarchivo.xml
# Sin salida = el documento está bien formado
# Con un DTD o Schema:
$ xmllint --noout --schema esquema.xsd miarchivo.xml
```

`xmllint --noout` comprueba solo el buen formado (sin generar ninguna salida si todo está bien); añadiendo `--schema` compara además contra un XML Schema y avisa de cualquier discrepancia con la estructura esperada.

**🧪 Ejercicio 3 — Valida tu propio feed**
Guarda el feed RSS del Ejercicio 2 como `feed.xml` y valida su buen formado con `xmllint --noout feed.xml` desde la terminal de LliureX (instala `libxml2-utils` con `sudo apt install libxml2-utils` si el comando no existe). Rompe deliberadamente una etiqueta (quita un cierre) y vuelve a ejecutar el comando — anota el mensaje de error exacto que da `xmllint`.

---

## 4. Validar documentos HTML

Un HTML puede "funcionar" en el navegador —que lo muestre sin errores visibles— y aun así tener errores de sintaxis que el navegador simplemente perdona, como ya viste en la UD1 al comparar el comportamiento de XML y HTML ante etiquetas mal cerradas. Validar un HTML es comprobar que cumple realmente la especificación oficial, más allá de lo que el navegador esté dispuesto a tolerar.

El validador de referencia es el del propio **W3C**: [validator.w3.org](https://validator.w3.org) — permite validar por URL, subiendo un archivo, o pegando el código directamente. Señala errores (etiquetas sin cerrar, atributos mal escritos, anidamiento incorrecto) y avisos (prácticas desaconsejadas que no rompen la página, pero no son ideales).

```html
<!-- Ejemplo con errores deliberados -->
<img src="foto.jpg">
<p>Texto sin cerrar
<div><span>Anidamiento cruzado</div></span>
```

Este HTML se vería en el navegador sin quejarse (el navegador "adivina" lo que querías decir), pero el validador señalaría: falta el atributo `alt` en `<img>` (accesibilidad), el `<p>` nunca se cierra, y el `<span>` se cierra después que su padre `<div>`, cruzando el anidamiento — exactamente el mismo tipo de error que ya identificaste en XML en la UD1, solo que aquí el navegador no detiene nada.

**🧪 Ejercicio 4 — Valida un HTML propio**
Coge cualquier HTML que hayas escrito en unidades anteriores (por ejemplo, de la UD3) y pásalo por el validador del W3C, pegando el código directamente. Anota cuántos errores y avisos da, corrige al menos 3 de ellos, y vuelve a validar hasta que el resultado sea "Document checking completed. No errors or warnings to show."

---

## 5. Validar hojas de estilo CSS

El mismo W3C mantiene también un validador específico para CSS: [jigsaw.w3.org/css-validator](https://jigsaw.w3.org/css-validator/) — detecta propiedades mal escritas, valores incorrectos para una propiedad concreta, o sintaxis inválida (una llave sin cerrar, un punto y coma olvidado).

```css
/* Ejemplo con errores deliberados */
.tarjeta {
  colorr: teal;              /* propiedad mal escrita */
  padding: 10pixels;         /* unidad inválida */
  border-radius: 8px
}
```

Aquí el validador señalaría `colorr` como una propiedad desconocida (probable error tipográfico de `color`), `10pixels` como un valor no reconocido (la unidad correcta es `px`), y avisaría de que falta el punto y coma tras `8px`.

⚠️ **Por qué importa validar CSS aunque "se vea bien"**: un navegador ignora silenciosamente cualquier declaración que no entiende (como `colorr: teal;`) y sigue aplicando el resto de la regla sin avisar de nada — el resultado visual puede parecer correcto por pura casualidad (por ejemplo, si ese color no era crítico), ocultando un error que sí dará problemas en otro navegador más estricto o en una regla más compleja.

**🧪 Ejercicio 5 — Valida tu CSS**
Coge el `estilos.css` de la UD4 o la UD5 y pásalo por el validador CSS del W3C. Si no da ningún error (es habitual, si has seguido bien la sintaxis), introduce deliberadamente 2 errores típicos (una propiedad mal escrita y una unidad inválida) y comprueba que el validador los detecta correctamente.

---

> 🧭 **A partir de aquí, formatos complementarios**: los puntos 1-5 (sindicación y validación de XML/HTML/CSS) son el núcleo de esta unidad. JSON y YAML son formatos igual de útiles en la práctica, pero no les dediques más tiempo del necesario — no son el centro de esta UP. Para que no se te mezclen entre sí:
>
> | Formato | Uso principal |
> |---|---|
> | JSON | Intercambio de datos en APIs |
> | YAML | Archivos de configuración |

## 6. JSON: sintaxis y validación

**JSON** (*JavaScript Object Notation*) es el formato de intercambio de datos más usado hoy en APIs web — ya lo viste mencionado en la UD1, ahora aprendes a escribirlo. A diferencia de XML, no es un lenguaje de marcas (no tiene etiquetas de apertura/cierre): es una notación basada en pares clave-valor, tomada de la sintaxis de objetos de JavaScript (de ahí el nombre), aunque hoy se usa de forma independiente del lenguaje.

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

**Reglas de sintaxis, todas obligatorias** (a diferencia de XML, JSON no tiene ningún elemento opcional en su gramática básica):

| Regla | Detalle |
|---|---|
| Claves siempre entre comillas dobles | `"titulo"`, nunca `titulo` ni `'titulo'` |
| Valores de texto entre comillas dobles | `"One Piece"` |
| Números sin comillas | `1120`, no `"1120"` |
| Booleanos sin comillas | `true` / `false` (en minúsculas) |
| Ausencia de valor | `null` |
| Listas entre corchetes | `["aventura", "fantasía"]` |
| Objetos entre llaves | `{ "titulo": "...", ... }` |
| Sin coma después del último elemento | Un error muy común al editar a mano |

⚠️ **El error más habitual**: dejar una coma después del último elemento de una lista u objeto (*trailing comma*). A diferencia de JavaScript, donde a veces se tolera, en JSON estricto es un error de sintaxis que invalida todo el documento — ningún parser JSON estándar lo acepta.

**Validar JSON**: al ser una gramática mucho más simple que XML (sin DTD ni Schema propios), basta con comprobar que la sintaxis es correcta. Se puede hacer en línea (`jsonlint.com`) o desde la terminal:

```bash
$ python3 -m json.tool miarchivo.json
# Si es válido, lo vuelve a imprimir formateado
# Si no lo es, señala la línea y columna exactas del error
```

**🧪 Ejercicio 6 — De XML a JSON**
Convierte el catálogo de series de la UD1 (el de `<catalogo>` con varias `<serie>`) a JSON: una lista de objetos, cada uno con `titulo`, `estudio`, `episodios` (como número, no como texto) y `enEmision` (como booleano). Valídalo con `python3 -m json.tool` y corrige cualquier error de sintaxis que aparezca.

---

## 7. YAML: sintaxis

**YAML** (*YAML Ain't Markup Language* — un acrónimo recursivo, a propósito) es otro formato de intercambio de datos, pensado para ser más legible por humanos que JSON: usa la indentación (los espacios al principio de línea) para marcar la estructura, en vez de llaves y corchetes.

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

Este YAML representa exactamente los mismos datos que el JSON del punto 6 — fíjate en que no hace falta ni una comilla, ni una llave, ni una coma. Las reglas básicas:

| Elemento | Sintaxis |
|---|---|
| Par clave-valor | `clave: valor`, con un espacio después de los dos puntos |
| Lista | Cada elemento en su propia línea, precedido de `- ` (guion y espacio) |
| Anidamiento | Se marca con **indentación** (espacios, nunca tabuladores) — cuantos más espacios, más profundo |
| Comentario | `# así`, igual que en Python |

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

⚠️ **La indentación no es cosmética, es sintaxis**: a diferencia de HTML o XML, donde la indentación solo ayuda a leer el código pero no afecta al resultado, en YAML **un espacio de más o de menos cambia la estructura del documento** — es la fuente de errores más común para quien empieza con YAML, y también su mayor crítica.

> 📡 **Por qué importa hoy**: YAML es el formato estándar de los archivos de configuración en herramientas de desarrollo actuales — Docker Compose, GitHub Actions, Kubernetes, y muchos frameworks lo usan para sus archivos de configuración, precisamente por ser más legible que XML o JSON para archivos que edita una persona a mano.

**🧪 Ejercicio 7 — De JSON a YAML**
Convierte a mano el JSON del Ejercicio 6 (tu catálogo de series) a YAML, respetando la indentación. Después, valida que la indentación es correcta con un validador en línea (`yamllint.com`) — introduce deliberadamente un error de indentación (quita o añade un espacio en una línea) y comprueba que lo detecta.

---

## 🎯 Reto de clase

Elige un tema tuyo (una colección, un catálogo, una lista de tareas...) y represéntalo en **los cuatro formatos** vistos en esta unidad y en la UD1: un feed RSS (con al menos 2 `<item>`), el mismo contenido en XML "propio" (tus propias etiquetas, como en la UD1), en JSON y en YAML. Valida los tres primeros con las herramientas vistas en los puntos 3, 4 (o 5, si prefieres representarlo como CSS de una página que lo muestre) y 6-7. Para terminar, escribe un breve informe (5-6 líneas) comparando los cuatro formatos: cuál te ha resultado más rápido de escribir, cuál más fácil de leer, y cuál elegirías para cada uno de estos casos: una API web, un archivo de configuración, y una nota personal.

---

<div style="page-break-after: always;"></div>

## Resumen de la unidad

**1. Sindicación de contenidos** Un canal (*feed*) permite que un lector se entere de contenido nuevo sin visitar la web — el formato más usado es RSS, hoy sobre todo para pódcasts; Atom es su alternativa técnicamente más limpia pero mucho menos extendida.

**2. Tecnología y estructura de RSS/Atom** `<channel>`/`<item>` en RSS equivalen a `<feed>`/`<entry>` en Atom; `<pubDate>`/`<updated>` marcan cuándo hay contenido nuevo, y `<guid>`/`<id>` evitan que un mismo contenido se muestre como nuevo dos veces.

**3. Validar XML** Más allá del buen formado (UD1), validar comprueba que el documento cumple una estructura concreta definida en un DTD o Schema — herramientas como `xmllint` lo hacen desde la terminal.

**4. Validar HTML** El validador del W3C detecta errores que el navegador perdona silenciosamente (etiquetas sin cerrar, anidamiento cruzado, atributos obligatorios ausentes).

**5. Validar CSS** El validador CSS del W3C detecta propiedades mal escritas o valores inválidos que el navegador, de nuevo, ignora sin avisar en vez de dar error.

**6. JSON** Notación de pares clave-valor sin etiquetas, con reglas de sintaxis estrictas y sin excepciones (comillas dobles obligatorias, sin coma final) — se valida con herramientas como `json.tool` de Python.

**7. YAML** Formato de configuración legible por humanos, basado en indentación en vez de llaves o corchetes — la indentación es sintaxis, no solo estética, y es la fuente de error más común.

---

## 📚 Para saber más (opcional, no evaluable)

> 📡 **Actualidad**: aunque XML sigue siendo el formato de los feeds RSS/Atom, en el resto de la web JSON domina claramente sobre XML para el intercambio de datos entre sistemas (APIs REST) por ser más ligero y más simple de generar y leer desde código — es la razón por la que XML apenas se usa hoy para nueva integración de APIs web, aunque siga siendo imprescindible en los formatos y sectores vistos en la UD1 (Office, facturación electrónica, SEPA...).

- Validador de HTML del W3C: https://validator.w3.org/
- Validador de CSS del W3C: https://jigsaw.w3.org/css-validator/
- Especificación oficial de JSON: https://www.json.org/json-es.html
- Especificación de YAML: https://yaml.org/spec/
