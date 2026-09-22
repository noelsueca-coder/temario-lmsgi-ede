<div style="text-align: center;">

<img src="data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCA0MDAgNDAwIiB3aWR0aD0iMTgwIiBoZWlnaHQ9IjE4MCI+CiAgPGNpcmNsZSBjeD0iMjAwIiBjeT0iMjAwIiByPSIxNzAiIGZpbGw9IiNGMEZERkEiLz4KICA8Y2lyY2xlIGN4PSIyMDAiIGN5PSIyMDAiIHI9IjE3MCIgZmlsbD0ibm9uZSIgc3Ryb2tlPSIjOTlGNkU0IiBzdHJva2Utd2lkdGg9IjIiLz4KICA8ZWxsaXBzZSBjeD0iMjAwIiBjeT0iMTMwIiByeD0iODAiIHJ5PSIyNiIgZmlsbD0ibm9uZSIgc3Ryb2tlPSIjMEY3NjZFIiBzdHJva2Utd2lkdGg9IjEwIi8+CiAgPHBhdGggZD0iTSAxMjAgMTMwIEwgMTIwIDI3MCBRIDEyMCAyOTYgMjAwIDI5NiBRIDI4MCAyOTYgMjgwIDI3MCBMIDI4MCAxMzAiIGZpbGw9Im5vbmUiIHN0cm9rZT0iIzBGNzY2RSIgc3Ryb2tlLXdpZHRoPSIxMCIvPgogIDxwYXRoIGQ9Ik0gMTIwIDIwMCBRIDEyMCAyMjYgMjAwIDIyNiBRIDI4MCAyMjYgMjgwIDIwMCIgZmlsbD0ibm9uZSIgc3Ryb2tlPSIjMEY3NjZFIiBzdHJva2Utd2lkdGg9IjgiIG9wYWNpdHk9IjAuNTUiLz4KPC9zdmc+Cg==" width="180" alt="Logo LMSGI"/>

<h1>Unidad 10</h1>
<h2>Almacenamiento de información</h2>

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

1. Panorama del almacenamiento de información: ¿dónde vive un XML?
2. Bases de datos relacionales aplicadas a XML: guardar y generar
3. XPath y XQuery: consultar XML con su propio lenguaje
4. Bases de datos XML nativas: qué son y cuándo usarlas
5. Poner en marcha una base de datos XML nativa
6. Importar y exportar entre formatos
7. Reto de clase
8. Resumen de la unidad
9. Para saber más

<div style="page-break-after: always;"></div>

**RA cubierto:** RA6 (ASIX, CA 6a-6i) / RA6 (DAW, CA 6a-6i) — *gestiona información en formato XML* / *gestiona información en formatos de intercambio de datos, analizando y utilizando tecnologías de almacenamiento y lenguajes de consulta*

> 💡 **Nota de estudio**: hasta ahora habéis trabajado con XML como **archivos sueltos** (`catalogo.xml`, `feed.xml`...). Esta unidad cierra el módulo respondiendo a una pregunta distinta: cuando el volumen de información crece, ¿**dónde** se guarda de forma duradera, y **cómo** se consulta sin tener que abrir el archivo entero cada vez? Veréis dos enfoques que conviven en la práctica: guardar XML **dentro** de una base de datos relacional que ya conocéis, y bases de datos pensadas **específicamente** para XML.

**🗺️ Mapa del bloque — tres formas de guardar lo que ya es (o fue) XML:**

```
                        ¿Dónde vive la información?
                                   │
        ┌──────────────────────────┼──────────────────────────┐
        │                          │                           │
  Archivo XML suelto      XML en BD relacional          BD XML nativa
  (feed, config)          (SQLite, columnas o            (BaseX, eXist-db)
                            texto completo)                árbol indexado
        │                          │                           │
     Punto 1                    Punto 2                   Puntos 4-5
                       Punto 3 — XPath/XQuery (aplica a los dos de la derecha)
                       Punto 6 — importar/exportar entre los tres enfoques
```

---

## 1. Panorama del almacenamiento de información: ¿dónde vive un XML?

Un archivo `.xml` suelto funciona bien para intercambiar un documento puntual (un feed, una factura, una configuración). Pero en cuanto necesitáis **buscar**, **indexar** o **actualizar** información XML de forma habitual, un archivo de texto plano se queda corto: no hay forma eficiente de buscar sin leerlo entero, ni de garantizar que dos procesos no lo modifiquen a la vez.

Existen, a grandes rasgos, tres formas de almacenar información que en algún momento es (o fue) XML:

| Enfoque | Idea | Ejemplo típico |
|---|---|---|
| **Archivo XML suelto** | El propio `.xml` es el almacén | Un feed RSS, un archivo de configuración |
| **XML dentro de una base de datos relacional** | El XML se guarda como texto (o se descompone en tablas) dentro de un SGBD relacional ya conocido | Una columna `TEXT` con el XML completo, o una tabla normalizada generada a partir de él |
| **Base de datos XML nativa** | Un sistema gestor pensado desde cero para almacenar y consultar árboles XML, sin pasar por tablas | BaseX, eXist-db |

> 🕰️ **Qué sigue vigente y qué está cambiando**: guardar XML dentro de un SGBD relacional (primera fila del enfoque intermedio) sigue siendo, con diferencia, la opción más habitual en proyectos reales — reutiliza toda la infraestructura relacional que ya conocéis de otros módulos. Las bases de datos XML nativas tienen un nicho más específico (sistemas documentales grandes, editoriales, archivos legales) donde de verdad se necesita indexar y consultar estructura XML compleja de forma directa — no son la opción por defecto para un proyecto pequeño.

**🧪 Ejercicio 1 — Elegir el enfoque correcto**
Para cada uno de estos tres escenarios, indicad cuál de los tres enfoques de la tabla usaríais y por qué en una frase: (a) el feed RSS de vuestro pódcast favorito, (b) un archivo de configuración `pom.xml` de un proyecto Java que no cambia casi nunca, (c) un sistema documental de un ayuntamiento con 200.000 expedientes en XML que hay que poder buscar por múltiples criterios a la vez.

---

## 2. Bases de datos relacionales aplicadas a XML: guardar y generar

La forma más sencilla de guardar un XML en una base de datos relacional es meterlo entero en una columna de texto:

```sql
CREATE TABLE series (
  id INTEGER PRIMARY KEY,
  titulo TEXT NOT NULL,
  anio INTEGER,
  xml_completo TEXT
);
```

Pero lo habitual —y lo que de verdad aprovecha una base de datos relacional— es **descomponer** el XML en columnas normales, como haríais con cualquier otra tabla:

```sql
INSERT INTO series (titulo, anio, valoracion)
VALUES ('Breaking Bad', 2008, 9.5);
```

Y, al revés, **generar** XML a partir de filas ya almacenadas — algo que necesitaréis constantemente si un sistema externo os pide los datos en XML aunque vosotros los tengáis en tablas:

```sql
SELECT '<serie><titulo>' || titulo || '</titulo><anio>' || anio || '</anio></serie>'
FROM series;
```

SQLite (el SGBD ligero que ya conocéis de otros módulos, y el más práctico para trabajar en LliureX sin instalar un servidor) no tiene funciones XML nativas tan completas como PostgreSQL o SQL Server —motores pensados para proyectos más grandes—, así que en proyectos pequeños esta concatenación manual, o un script (Python, por ejemplo) que lea las filas y construya el XML, es el camino habitual.

**🧪 Ejercicio 2 — De filas a XML y de XML a filas**
Cread una base de datos SQLite (`catalogo.db`) con la tabla `series` de arriba, e insertad las mismas 3 series del catálogo XML de unidades anteriores. Escribid una consulta SQL que genere, para cada fila, una cadena `<serie>...</serie>` como en el ejemplo. Después, al revés: partiendo del XML original (`catalogo.xml`), escribid las sentencias `INSERT` necesarias para volcar sus datos en la tabla.

---

## 3. XPath y XQuery: consultar XML con su propio lenguaje

Cuando el XML se consulta **directamente** (sin pasar por SQL), se usa **XPath** —que ya conocéis de la UD9, para localizar nodos— y **XQuery**, un lenguaje de consulta completo para XML, pensado para casos que XPath por sí solo no cubre: construir nuevos documentos a partir de los resultados, combinar datos de varias fuentes, ordenar, agrupar.

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

Esta construcción se llama **FLWOR** (*for, let, where, order by, return* — se pronuncia "flower"): recorre nodos con `for`, filtra con `where`, ordena con `order by`, y construye el resultado con `return`, usando llaves `{ }` para insertar el valor de una expresión dentro de XML literal. Si os resulta familiar, es porque es, conceptualmente, muy parecido a una consulta SQL con `SELECT ... WHERE ... ORDER BY`, pero devolviendo XML en lugar de filas.

> 📋 No hace falta memorizar toda la sintaxis de XQuery — con reconocer y adaptar esta plantilla FLWOR (`for` / `where` / `order by` / `return`) a vuestros propios datos es suficiente.

**🧪 Ejercicio 3 — Tu primera consulta XQuery**
Sin ejecutarlo todavía (lo haréis en el punto 5, con una base de datos XML nativa instalada), adaptad la plantilla FLWOR de arriba a mano para seleccionar las series de `catalogo.xml` estrenadas después de 2005, ordenadas por valoración de mayor a menor.

---

## 4. Bases de datos XML nativas: qué son y cuándo usarlas

Una **base de datos XML nativa** almacena los documentos **como árboles XML**, no como texto ni como filas de tabla — indexa la propia estructura (elementos, atributos, jerarquía) para que las consultas XPath/XQuery sean rápidas incluso con miles de documentos.

Las dos más conocidas y con buen soporte en Linux:

| Sistema | Características |
|---|---|
| **BaseX** | Open source, escrito en Java, incluye interfaz gráfica y línea de comandos, muy usado en docencia por ser fácil de instalar |
| **eXist-db** | Open source, orientado a aplicaciones web completas sobre XML, más complejo de configurar |

Trabajaremos con **BaseX** por su sencillez de instalación en LliureX y porque su GUI permite ver el árbol del documento mientras se escribe la consulta — muy útil para aprender.

**🧪 Ejercicio 4 — Comparar enfoques**
Retomad el escenario (c) del Ejercicio 1 (el sistema documental del ayuntamiento). Escribid dos o tres frases explicando por qué, en ese caso concreto, una base de datos XML nativa como BaseX puede ser mejor opción que descomponer todo en tablas relacionales — pensad en qué pasaría si la estructura de los expedientes no es siempre exactamente igual entre unos y otros.

---

## 5. Poner en marcha una base de datos XML nativa

Instalación de BaseX en LliureX (requiere Java, normalmente ya instalado):

```bash
# Descargar e instalar BaseX
wget https://files.basex.org/releases/latest/BaseX.zip
unzip BaseX.zip -d ~/basex
~/basex/bin/basexgui
```

> 🛟 **Plan B si `BaseX` no se instala en el aula** (red restringida, permisos, versión de Java): tened preparada de antemano una copia de BaseX ya funcionando en la imagen de la VM portátil que ya usáis para otras prácticas, para no perder la sesión completa por un problema de instalación de última hora. Como alternativa de urgencia, toda consulta que aquí use `db:open(...)` se puede adaptar directamente con `doc("catalogo.xml")` (como en el Ejercicio 3), que no necesita ninguna instalación.

Desde la GUI: `Database → Create Database`, seleccionáis `catalogo.xml`, y BaseX lo indexa. Con la base de datos creada, la pestaña de consulta permite ejecutar XQuery directamente sobre ella:

```xquery
for $serie in db:open("catalogo")/catalogo/serie
where $serie/valoracion > 9
order by $serie/anio
return $serie/titulo/text()
```

La única diferencia con el Ejercicio 3 es `db:open("catalogo")` en lugar de `doc("catalogo.xml")` — la primera consulta una base de datos ya indexada por su nombre, la segunda abre un archivo suelto directamente. Para actualizar información dentro de una base de datos XML nativa, XQuery Update añade sentencias como `insert node`, `delete node` y `replace node`:

```xquery
insert node <serie><titulo>Fargo</titulo><anio>2014</anio><valoracion>8.9</valoracion></serie>
into db:open("catalogo")/catalogo
```

**🧪 Ejercicio 5 — Consultar y actualizar en BaseX**
Instalad BaseX, creed la base de datos `catalogo` a partir de vuestro `catalogo.xml`, y ejecutad la consulta del Ejercicio 3 adaptada con `db:open()`. Después, insertad una serie nueva con `insert node` como en el ejemplo, y volved a ejecutar la consulta para comprobar que aparece en los resultados si cumple la condición del filtro.

---

## 6. Importar y exportar entre formatos

En un proyecto real, la información casi nunca vive en un único sistema durante toda su vida: nace en una base de datos relacional, se exporta a XML para enviarla a otro sistema, ese sistema la devuelve transformada, y hay que volver a importarla. Las herramientas que ya conocéis del módulo encajan aquí, encadenadas:

```bash
# Exportar una tabla SQLite completa a XML (con un script, o generando el XML por SQL como en el punto 2)
sqlite3 catalogo.db "SELECT titulo, anio, valoracion FROM series;" -header -csv > series.csv

# De CSV a XML: un script sencillo en Python, o herramientas dedicadas
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

Y en dirección contraria, un XML recibido de fuera se puede importar de vuelta a tablas relacionales con las sentencias `INSERT` que ya construisteis en el Ejercicio 2 — generadas a mano para aprender el mecanismo, o con un script que recorra el XML (por ejemplo, con la librería `xml.etree.ElementTree` de Python) y genere los `INSERT` automáticamente para cualquier número de registros.

**🧪 Ejercicio 6 — El ciclo completo**
Partiendo de `catalogo.db` (Ejercicio 2), exportad la tabla `series` a CSV con `sqlite3`, y después convertid ese CSV a un XML `series_generado.xml` con un script como el de arriba (podéis adaptarlo). Comparad `series_generado.xml` con el `catalogo.xml` original: deben contener la misma información, aunque la estructura de etiquetas puede variar ligeramente.

---

## 7. Reto de clase

Partiendo del dominio propio que elegisteis en los retos de la UD8/UD9 (o uno nuevo), completad el ciclo de esta unidad:

1. Una **tabla relacional** en SQLite con al menos 5 filas.
2. Una consulta SQL que **genere XML** a partir de esa tabla.
3. Una **consulta FLWOR** (con `doc()` o `db:open()`, según tengáis BaseX disponible) que filtre y ordene esos mismos datos.

> 📋 No hace falta memorizar la sintaxis exacta de XQuery ni de SQL — tendréis siempre a mano la chuleta de la unidad.

---

## Resumen de la unidad

1. Un archivo XML suelto sirve para intercambio puntual, pero cuando hay que **buscar, indexar o actualizar** información de forma habitual, hace falta un sistema de almacenamiento: XML dentro de una base de datos relacional, o una base de datos XML nativa.
2. Guardar XML en un SGBD relacional se hace descomponiéndolo en columnas normales (lo habitual) o guardándolo entero como texto; generar XML a partir de filas se hace con concatenación SQL o un script.
3. **XQuery** es un lenguaje de consulta completo para XML, con estructura **FLWOR** (`for`/`let`/`where`/`order by`/`return`), conceptualmente parecido a una consulta SQL pero devolviendo XML.
4. Una **base de datos XML nativa** (BaseX, eXist-db) almacena y consulta los documentos como árboles, sin pasar por tablas — útil cuando la estructura es compleja o variable entre documentos.
5. BaseX se instala y usa fácilmente en LliureX; sus consultas usan `db:open("nombre")` para bases de datos ya creadas, y XQuery Update (`insert node`, `delete node`, `replace node`) para modificar contenido.
6. En un flujo real, la información se mueve entre formatos constantemente (relacional → XML → CSV → XML...) — las herramientas de exportación/importación encadenan lo aprendido en todo el módulo.

---

## 📚 Para saber más (opcional, no evaluable)

El concepto de "base de datos que no usa tablas relacionales" que habéis visto aquí para XML (BaseX) es un caso particular de algo más amplio llamado **bases de datos NoSQL** — sistemas que almacenan documentos JSON, grafos, pares clave-valor, etc., en lugar de tablas. Si en el futuro trabajáis con MongoDB (documentos JSON) o Neo4j (grafos), estaréis aplicando la misma idea que aquí: adaptar el sistema de almacenamiento a la forma natural de los datos, en lugar de forzarlos siempre a filas y columnas.

- Documentación oficial de BaseX: [docs.basex.org](https://docs.basex.org/)
- Especificación oficial de XQuery 3.1 (W3C): [www.w3.org/TR/xquery-31](https://www.w3.org/TR/xquery-31/)
- eXist-db, alternativa a BaseX: [exist-db.org](https://exist-db.org/)
- Introducción a bases de datos NoSQL: [www.mongodb.com/nosql-explained](https://www.mongodb.com/nosql-explained)
