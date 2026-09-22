<div style="text-align: center;">

<img src="data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCA0MDAgNDAwIiB3aWR0aD0iMTgwIiBoZWlnaHQ9IjE4MCI+CiAgPGNpcmNsZSBjeD0iMjAwIiBjeT0iMjAwIiByPSIxNzAiIGZpbGw9IiNGMEZERkEiLz4KICA8Y2lyY2xlIGN4PSIyMDAiIGN5PSIyMDAiIHI9IjE3MCIgZmlsbD0ibm9uZSIgc3Ryb2tlPSIjOTlGNkU0IiBzdHJva2Utd2lkdGg9IjIiLz4KICA8cmVjdCB4PSI5MCIgeT0iMTMwIiB3aWR0aD0iOTAiIGhlaWdodD0iMTIwIiByeD0iOCIgZmlsbD0ibm9uZSIgc3Ryb2tlPSIjMEY3NjZFIiBzdHJva2Utd2lkdGg9IjEwIi8+CiAgPHJlY3QgeD0iMjIwIiB5PSIxNTAiIHdpZHRoPSI5MCIgaGVpZ2h0PSIxMjAiIHJ4PSI4IiBmaWxsPSIjMEY3NjZFIiBvcGFjaXR5PSIwLjE1IiBzdHJva2U9IiMwRjc2NkUiIHN0cm9rZS13aWR0aD0iMTAiLz4KICA8cGF0aCBkPSJNIDE4NSAxOTAgTCAyMTUgMTkwIiBzdHJva2U9IiMwRjc2NkUiIHN0cm9rZS13aWR0aD0iOSIgc3Ryb2tlLWxpbmVjYXA9InJvdW5kIi8+CiAgPHBhdGggZD0iTSAyMDUgMTc4IEwgMjE5IDE5MCBMIDIwNSAyMDIiIGZpbGw9Im5vbmUiIHN0cm9rZT0iIzBGNzY2RSIgc3Ryb2tlLXdpZHRoPSI4IiBzdHJva2UtbGluZWNhcD0icm91bmQiIHN0cm9rZS1saW5lam9pbj0icm91bmQiLz4KPC9zdmc+Cg==" width="180" alt="Logo LMSGI"/>

<h1>Unidad 9</h1>
<h2>Conversión y adaptación de documentos para el intercambio de información</h2>

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

1. Por qué transformar documentos: de XML a otra cosa
2. XPath: localizar información dentro de un árbol XML
3. Estructura de una hoja de estilo XSLT
4. Plantillas: xsl:template y xsl:apply-templates
5. Iterar y filtrar: xsl:for-each, xsl:if, xsl:choose
6. Aplicar la transformación y depurar
7. Reto de clase
8. Resumen de la unidad
9. Para saber más

<div style="page-break-after: always;"></div>

**RA cubierto:** RA5 (ASIX, CA 5a-5h) / RA5 (DAW, CA 5a-5g) — *realiza conversiones sobre documentos XML* / *realiza conversiones sobre documentos para el intercambio de información, utilizando técnicas, lenguajes y herramientas de procesamiento*

> 💡 **Nota de estudio**: en la UD8 aprendisteis a **validar** que un XML cumple una estructura (XSD). Esta unidad va un paso más allá: aprender a **transformar** un XML en otra cosa — otro XML, HTML, texto plano — de forma automática, sin tocar el documento original ni escribir un programa desde cero. La herramienta para esto es **XSLT**, y para señalar qué parte del documento queremos transformar en cada momento, usamos **XPath**.

**🗺️ XPath vs. XSLT, de un vistazo:**

| | XPath | XSLT |
|---|---|---|
| Qué es | Lenguaje para **señalar** una parte del árbol XML | Lenguaje para **transformar** un XML en otro documento |
| Se parece a | Una ruta de archivos (`/carpeta/archivo`) | Una plantilla que se rellena con datos |
| Se usa... | ...dentro de XSLT, en cada `select="..."` | ...para envolver y organizar esas rutas XPath |

XPath no transforma nada por sí solo: es la "brújula" que usa XSLT para saber dónde mirar en cada paso de la transformación.

---

## 1. Por qué transformar documentos: de XML a otra cosa

Un mismo dato en XML casi nunca se consume tal cual. El catálogo de series que construisteis en la UD1 y validasteis en la UD8 puede necesitar salir, según quién lo consuma, en formas muy distintas:

- Como una **página HTML** legible, para mostrarla en un navegador.
- Como un **XML distinto**, con otra estructura, para enviarlo a un sistema que espera un formato concreto.
- Como **texto plano**, para un informe o un log.

Reescribir el documento a mano cada vez que cambia el catálogo no es viable. **XSLT** (*eXtensible Stylesheet Language Transformations*) es un lenguaje — él mismo escrito en XML — que describe **reglas de transformación**: "cuando encuentres un elemento así, genera esto otro". Un procesador XSLT aplica esas reglas al XML de entrada y genera el documento de salida.

> 🕰️ **Qué sigue vigente y qué está cambiando**: XSLT tiene dos versiones con adopción real, 1.0 (1999) y 2.0/3.0 (más potentes, con más funciones). La mayoría de herramientas de línea de comandos disponibles en Linux (como `xsltproc`, que usaremos aquí) implementan **XSLT 1.0** — suficiente para todo lo que veréis en esta unidad. En el ámbito de desarrollo web moderno, XSLT ha perdido terreno frente a transformar los datos directamente con JavaScript (por ejemplo, convirtiendo JSON con código) — pero sigue siendo el estándar en sistemas documentales, editoriales y de intercambio B2B donde el XML es el formato de origen y no se puede evitar.

**🧪 Ejercicio 1 — Identifica una necesidad de conversión**
Pensad en el catálogo de series XML de las unidades anteriores. Escribid dos frases: una describiendo un escenario real donde alguien necesitaría verlo como HTML (¿quién, y para qué?), y otra describiendo un escenario donde alguien necesitaría exportarlo a un XML con **otra** estructura distinta (por ejemplo, agrupado por género en lugar de una lista plana).

---

## 2. XPath: localizar información dentro de un árbol XML

Antes de transformar, hace falta poder **señalar** una parte concreta del árbol XML. Para eso existe **XPath** — un lenguaje de rutas, parecido a las rutas de un sistema de archivos, pero para navegar por elementos y atributos XML.

Partiendo de este XML:

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

Algunas rutas XPath básicas:

| Expresión XPath | Selecciona |
|---|---|
| `/catalogo` | El elemento raíz `catalogo` |
| `/catalogo/serie` | Todos los elementos `serie`, hijos directos de `catalogo` |
| `//titulo` | Todos los elementos `titulo`, estén donde estén en el árbol |
| `/catalogo/serie[1]` | Solo la **primera** `serie` (XPath empieza a contar en 1, no en 0) |
| `/catalogo/serie/@id` | El atributo `id` de cada `serie` |
| `//serie[anio > 2005]` | Las `serie` cuyo hijo `anio` sea mayor que 2005 |
| `//serie[@id='s1']/titulo` | El `titulo` de la `serie` con atributo `id="s1"` |

`.` se refiere al nodo actual, `..` al nodo padre, y `text()` al contenido de texto de un elemento — los usaréis dentro de las plantillas XSLT en el punto siguiente.

**🧪 Ejercicio 2 — Practicar XPath**
Sobre el XML de arriba (guardadlo como `catalogo.xml`), escribid a mano las expresiones XPath que seleccionarían: (a) el `titulo` de la segunda serie, (b) todas las `valoracion` mayores que 9.4, (c) el atributo `id` de la serie titulada "The Wire". Comprobad vuestras respuestas con un evaluador XPath online como [www.freeformatter.com/xpath-tester.html](https://www.freeformatter.com/xpath-tester.html) (pegad el XML y probad cada expresión).

---

## 3. Estructura de una hoja de estilo XSLT

Una hoja XSLT es un documento `.xsl` (o `.xslt`), que es también XML:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform">

  <xsl:output method="html" encoding="UTF-8" indent="yes"/>

  <xsl:template match="/">
    <!-- aquí va la transformación -->
  </xsl:template>

</xsl:stylesheet>
```

- `xsl:stylesheet` es la raíz de toda hoja XSLT, con el namespace estándar `http://www.w3.org/1999/XSL/Transform`.
- `xsl:output` declara el formato de salida: `html`, `xml` o `text`. Aquí generamos HTML.
- `xsl:template match="/"` es la **plantilla raíz**: se dispara cuando el procesador llega a la raíz del documento de entrada (el punto de partida de toda transformación).

Para aplicar la hoja desde la terminal en LliureX, usamos `xsltproc` (viene instalado o se instala con `sudo apt install xsltproc`):

```bash
xsltproc catalogo.xsl catalogo.xml > catalogo.html
```

**🧪 Ejercicio 3 — Esqueleto que genera HTML fijo**
Cread `catalogo.xsl` con el esqueleto de arriba, y dentro de `xsl:template match="/"` escribid HTML fijo (`<html><body><h1>Mi catálogo</h1></body></html>`, sin usar aún ningún dato del XML). Ejecutad `xsltproc` y comprobad que `catalogo.html` se genera correctamente y se abre bien en Firefox.

---

## 4. Plantillas: xsl:template y xsl:apply-templates

El punto anterior generaba HTML fijo — útil para comprobar el mecanismo, pero no usa el XML de entrada. Para **extraer** datos del XML, XSLT ofrece dos piezas clave:

- **`xsl:value-of select="..."`** — inserta el valor de una expresión XPath como texto.
- **`xsl:apply-templates select="..."`** — le dice al procesador "busca una plantilla que sepa tratar estos nodos, y aplícala a cada uno".

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

Aquí hay **dos** plantillas: la raíz genera el esqueleto HTML y delega en `xsl:apply-templates` la parte repetitiva; la segunda plantilla, `match="serie"`, se dispara automáticamente **una vez por cada** elemento `serie` que le llegue, y decide cómo pintarlo. Separar la lógica en varias plantillas es la forma "correcta" de escribir XSLT, en vez de meter toda la transformación en una única plantilla raíz.

**🧪 Ejercicio 4 — Dos plantillas**
Reescribid `catalogo.xsl` con las dos plantillas de arriba (`match="/"` y `match="serie"`), aplicadas a vuestro `catalogo.xml` con 2-3 series. Generad el HTML con `xsltproc` y comprobad que aparece un párrafo por cada serie, con su título, año y valoración extraídos correctamente del XML.

---

## 5. Iterar y filtrar: xsl:for-each, xsl:if, xsl:choose

`xsl:apply-templates` no es la única forma de repetir contenido. **`xsl:for-each`** itera directamente sobre un conjunto de nodos, sin necesidad de una plantilla aparte — útil cuando la lógica es simple y no merece la pena separarla:

**🗺️ `xsl:apply-templates` vs. `xsl:for-each`, de un vistazo:**

| | `xsl:apply-templates` | `xsl:for-each` |
|---|---|---|
| Qué hace | Delega en otra plantilla (`match="..."`) por cada nodo | Repite el mismo bloque de código, sin plantilla aparte |
| Cuándo usarlo | Lógica compleja, o reutilizable en varios sitios | Lógica simple, uso puntual |
| Organización | Separa responsabilidades en varias plantillas pequeñas | Todo el código junto, en un único bloque |

Ambos recorren un conjunto de nodos — la diferencia está en **dónde vive la lógica** de cada uno, no en qué nodos seleccionan.

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

Para lógica condicional, XSLT ofrece **`xsl:if`** (una sola condición, sin alternativa) y **`xsl:choose`** (equivalente a un `if / elif / else`):

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

> ⚠️ Dentro de un atributo XML, los símbolos `<` y `>` no se pueden escribir literalmente — por eso `test="valoracion &gt; 9"` usa la entidad `&gt;` en lugar de `>` (y `&lt;` para `<`). Es la misma regla de escapado que ya usasteis con entidades XML en unidades anteriores.

**Plantilla de partida** (completad los huecos `___`):

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

**🧪 Ejercicio 5 — Tabla con valoración destacada**
Completad la plantilla de arriba y sustituid con ella la lista de párrafos del Ejercicio 4: una tabla HTML (`xsl:for-each` sobre `serie`, con columnas título, año y valoración) con una columna extra que muestre "⭐ Recomendada" solo si la valoración es mayor que 9, usando `xsl:if`.

---

## 6. Aplicar la transformación y depurar

Además de `xsltproc` en la terminal, hay herramientas gráficas útiles para depurar una hoja XSLT paso a paso mientras la escribís:

| Herramienta | Para qué sirve |
|---|---|
| `xsltproc` (terminal, LliureX) | Aplicar la transformación desde la línea de comandos, la que usaréis en los ejercicios |
| [www.freeformatter.com/xsl-transformer.html](https://www.freeformatter.com/xsl-transformer.html) | Probar XML + XSLT online y ver el resultado y los errores al momento, sin instalar nada |
| Firefox (con `<?xml-stylesheet?>`) | Enlazando la hoja XSLT directamente desde el XML, el navegador aplica la transformación al abrir el archivo |

Para que Firefox aplique la transformación automáticamente al abrir el XML, se añade esta línea de procesamiento justo tras la declaración XML:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<?xml-stylesheet type="text/xsl" href="catalogo.xsl"?>
<catalogo>
  ...
</catalogo>
```

Cuando algo falla, `xsltproc` señala **línea y columna** del error, igual que `xmllint` — el mismo hábito de leer el mensaje de error de la UD7 y la UD8 aplica aquí: no ignorarlo, y localizar la línea exacta antes de tocar nada más.

**🧪 Ejercicio 6 — Enlazar y depurar**
Añadid la línea `<?xml-stylesheet?>` a vuestro `catalogo.xml` apuntando a `catalogo.xsl`, y abrid el XML directamente con Firefox — debe mostrarse ya transformado en HTML. Después, introducid deliberadamente un error en `catalogo.xsl` (por ejemplo, una etiqueta `xsl:template` sin cerrar) y ejecutad `xsltproc catalogo.xsl catalogo.xml`: copiad el mensaje de error exacto y explicad en una frase qué indica sobre dónde está el problema.

---

## 7. Reto de clase

Retomad el dominio propio que elegisteis en el reto de la UD8 (o proponed otro) y generad, a partir de vuestro XML, un documento HTML con `xsltproc` que use al menos:

1. **Dos plantillas separadas** (`xsl:template match="/"` + `xsl:apply-templates` hacia una segunda plantilla).
2. Una **tabla** construida con `xsl:for-each`.
3. Una **condición** (`xsl:if` o `xsl:choose`) que destaque algún dato según su valor.

> 📋 No hace falta memorizar la sintaxis exacta de XPath ni de XSLT — tendréis siempre a mano la tabla de expresiones XPath y la lista de elementos `xsl:` vistos en la unidad.

---

## Resumen de la unidad

1. **XSLT** transforma un XML de entrada en otro documento (HTML, otro XML, texto) aplicando reglas de transformación descritas también en XML.
2. **XPath** es el lenguaje de rutas que permite señalar qué parte del árbol XML se quiere leer o transformar (`/catalogo/serie`, `//titulo`, `@id`, con condiciones entre corchetes).
3. Una hoja `.xsl` tiene como raíz `xsl:stylesheet`, declara el formato de salida con `xsl:output`, y define su lógica en una o varias `xsl:template`; se aplica en LliureX con `xsltproc`.
4. `xsl:value-of` extrae un valor como texto; `xsl:apply-templates` delega en la plantilla adecuada para cada nodo — la forma habitual de organizar una transformación en varias piezas.
5. `xsl:for-each` itera directamente sobre un conjunto de nodos; `xsl:if` y `xsl:choose`/`xsl:when`/`xsl:otherwise` añaden lógica condicional (con `&gt;`/`&lt;` en lugar de `>`/`<` dentro de atributos).
6. La transformación se puede lanzar desde terminal (`xsltproc`), depurar con herramientas online, o enlazar directamente desde el XML con `<?xml-stylesheet?>` para que el navegador la aplique al abrir el archivo.

---

## 📚 Para saber más (opcional, no evaluable)

XSLT 2.0 y 3.0 añaden funciones mucho más potentes (agrupación con `xsl:for-each-group`, generación de varios archivos de salida a la vez con `xsl:result-document`...), pero requieren un procesador distinto de `xsltproc` (que solo soporta 1.0) — por ejemplo Saxon, disponible también para Linux. Si en el futuro trabajáis con transformaciones complejas de verdad (por ejemplo, generando un libro completo en PDF a partir de XML editorial), es donde os las encontraréis.

- Especificación oficial de XSLT 1.0 (W3C): [www.w3.org/TR/xslt-10](https://www.w3.org/TR/xslt-10/)
- Especificación oficial de XPath 1.0 (W3C): [www.w3.org/TR/xpath-10](https://www.w3.org/TR/xpath-10/)
- Tutorial interactivo de XSLT: [www.w3schools.com/xml/xsl_intro.asp](https://www.w3schools.com/xml/xsl_intro.asp)
- Probador de XSLT online: [www.freeformatter.com/xsl-transformer.html](https://www.freeformatter.com/xsl-transformer.html)
