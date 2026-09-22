<div style="text-align: center;">

<img src="data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCA0MDAgNDAwIiB3aWR0aD0iMTgwIiBoZWlnaHQ9IjE4MCI+CiAgPGNpcmNsZSBjeD0iMjAwIiBjeT0iMjAwIiByPSIxNzAiIGZpbGw9IiNGMEZERkEiLz4KICA8Y2lyY2xlIGN4PSIyMDAiIGN5PSIyMDAiIHI9IjE3MCIgZmlsbD0ibm9uZSIgc3Ryb2tlPSIjOTlGNkU0IiBzdHJva2Utd2lkdGg9IjIiLz4KICA8cGF0aCBkPSJNIDEzMCAxMzAgTCAyNzAgMTMwIEwgMjcwIDIwMCBMIDIyMCAyMDAgTCAyMjAgMjcwIEwgMTMwIDI3MCBaIiBmaWxsPSJub25lIiBzdHJva2U9IiMwRjc2NkUiIHN0cm9rZS13aWR0aD0iMTAiIHN0cm9rZS1saW5lam9pbj0icm91bmQiLz4KICA8bGluZSB4MT0iMTUwIiB5MT0iMTYwIiB4Mj0iMjUwIiB5Mj0iMTYwIiBzdHJva2U9IiMwRjc2NkUiIHN0cm9rZS13aWR0aD0iNyIgc3Ryb2tlLWxpbmVjYXA9InJvdW5kIiBvcGFjaXR5PSIwLjUiLz4KICA8bGluZSB4MT0iMTUwIiB5MT0iMjMwIiB4Mj0iMTk1IiB5Mj0iMjMwIiBzdHJva2U9IiMwRjc2NkUiIHN0cm9rZS13aWR0aD0iNyIgc3Ryb2tlLWxpbmVjYXA9InJvdW5kIiBvcGFjaXR5PSIwLjUiLz4KICA8cGF0aCBkPSJNIDI0NSAyMzUgTCAyNTggMjQ4IEwgMjgyIDIyMCIgZmlsbD0ibm9uZSIgc3Ryb2tlPSIjMEY3NjZFIiBzdHJva2Utd2lkdGg9IjkiIHN0cm9rZS1saW5lY2FwPSJyb3VuZCIgc3Ryb2tlLWxpbmVqb2luPSJyb3VuZCIvPgo8L3N2Zz4K" width="180" alt="Logo LMSGI"/>

<h1>Unidad 8</h1>
<h2>Definición de esquemas y vocabularios en lenguajes de marcas</h2>

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

1. De DTD a XML Schema: por qué necesitamos algo más
2. Estructura de un documento XSD y su vínculo con el XML
3. Tipos simples: los datos básicos y sus restricciones
4. Tipos complejos: elementos con estructura
5. Compositores y cardinalidad: sequence, choice, all, minOccurs, maxOccurs
6. Atributos en XSD
7. Tipos reutilizables y grupos
8. Validar un documento contra su esquema
9. Reto de clase
10. Resumen de la unidad
11. Para saber más

<div style="page-break-after: always;"></div>

**RA cubierto:** RA4 (ASIX, CA 4a-4h) / RA4 (DAW, CA 4a-4g) — *establece mecanismos de validación para documentos XML* / *establece mecanismos de validación de documentos para el intercambio de información, utilizando métodos para definir su sintaxis y estructura*

> 💡 **Nota de estudio**: en la UD1 construisteis a mano un DTD (`<!ELEMENT>`, `<!ATTLIST>`, `#PCDATA`, `#REQUIRED`) y en la UD7 aprendisteis a validar un XML contra un esquema con `xmllint --schema`. Esta unidad cierra el círculo: veréis **por qué** el sector dejó de usar DTD como primera opción, y aprenderéis a escribir esquemas **XML Schema (XSD)** — hoy el estándar real para describir y validar la estructura de un documento XML.

**🗺️ Mapa del bloque — de qué piezas se compone un XSD:**

```
xs:schema (raíz)
 └─ xs:element (lo que puede aparecer en el XML)
     ├─ xs:simpleType   → dato sin hijos/atributos (texto con tipo + restricción)
     └─ xs:complexType  → elemento con estructura
         ├─ compositor: xs:sequence / xs:choice / xs:all
         ├─ xs:element (hijos, con minOccurs/maxOccurs)
         └─ xs:attribute (use="required"/"optional", default="...")
```
Cada punto de esta unidad añade una pieza a este mapa — volved a él si os perdéis.

---

## 1. De DTD a XML Schema: por qué necesitamos algo más

El DTD que construisteis en la UD1 funciona, pero tiene límites que se notan enseguida en cualquier proyecto real:

| Limitación del DTD | Consecuencia |
|---|---|
| No tiene tipos de datos | `<precio>abc</precio>` es tan válido como `<precio>19.99</precio>` — un DTD no distingue texto de número |
| Sintaxis propia, no XML | Un DTD no se puede procesar con las mismas herramientas que procesan XML (no tiene etiquetas, atributos ni namespaces) |
| Namespaces mal soportados | No hay forma limpia de decir "este DTD aplica solo a elementos de este namespace" |
| Reutilización pobre | No se puede definir un tipo una vez y reutilizarlo en varios elementos sin repetir la definición |

**XML Schema (XSD)**, publicado por el W3C en 2001, resuelve los cuatro puntos: es XML él mismo (se escribe con etiquetas `<xs:...>`), tiene un sistema de tipos (texto, número entero, decimal, fecha, booleano...), soporta namespaces de forma nativa, y permite definir tipos reutilizables.

> 🕰️ **Qué sigue vigente y qué está cambiando**: el DTD **no ha desaparecido** — sigue vigente en formatos heredados y en casos donde basta con validar estructura sin tipos (por ejemplo, algunas DTD de HTML antiguas). Pero para cualquier intercambio de datos serio entre sistemas (facturación electrónica, configuración de aplicaciones, APIs basadas en XML) el estándar de facto hoy es **XSD**. Existe una tercera alternativa, **RELAX NG**, más simple y expresiva que XSD en algunos aspectos, pero con muchísima menos adopción industrial — la mencionamos para que sepáis que existe, no hace falta profundizar en ella.

**🧪 Ejercicio 1 — Encuentra los huecos del DTD**
Retomad el DTD del catálogo de series que construisteis en la UD1. Escribid una instancia XML que **cumpla** ese DTD (etiquetas y orden correctos) pero que tenga claramente un dato mal escrito que el DTD no puede detectar — por ejemplo, un año de estreno como `"mil novecientos noventa"` en lugar de un número, o una valoración fuera de rango como `15` sobre una escala de 1 a 10. Anotad en una frase por qué el DTD no lo rechaza.

---

## 2. Estructura de un documento XSD y su vínculo con el XML

Un esquema XSD es un archivo `.xsd`, que es a su vez un documento XML. Empezamos por su esqueleto mínimo:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">

  <xs:element name="catalogo">
    <!-- aquí definimos qué puede contener <catalogo> -->
  </xs:element>

</xs:schema>
```

- `xs:schema` es el elemento raíz de **todo** esquema XSD: declara el namespace estándar de XML Schema (`http://www.w3.org/2001/XMLSchema`), con el prefijo `xs` por convención.
- `xs:element` declara un elemento que puede aparecer en el XML validado — aquí, el elemento raíz `<catalogo>`.

Para que un XML se valide contra este esquema, hay que **asociarlo** explícitamente. La forma habitual es con `xsi:schemaLocation` en el elemento raíz del XML:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<catalogo xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
          xsi:noNamespaceSchemaLocation="catalogo.xsd">
  <!-- contenido -->
</catalogo>
```

`xsi:noNamespaceSchemaLocation` se usa cuando el esquema no define un namespace propio para los datos (como en nuestro caso). Si el esquema sí define un namespace de destino (`targetNamespace`), se usa `xsi:schemaLocation` con el par namespace–archivo. Con esta asociación hecha, ya podéis validar con la herramienta que aprendisteis en la UD7:

```bash
xmllint --noout --schema catalogo.xsd catalogo.xml
```

**🧪 Ejercicio 2 — Esqueleto mínimo**
Cread `catalogo.xsd` con el esqueleto de arriba (elemento raíz `catalogo`, sin contenido definido todavía) y `catalogo.xml` con la asociación `xsi:noNamespaceSchemaLocation`. Validad con `xmllint`: como `<xs:element name="catalogo">` no define aún ningún contenido permitido, cualquier cosa que metáis dentro de `<catalogo>` dará error — comprobadlo y anotad el mensaje exacto que devuelve `xmllint`.

---

## 3. Tipos simples: los datos básicos y sus restricciones

Un **tipo simple** describe un dato que no tiene hijos ni atributos — solo texto, pero con un tipo de dato concreto. XSD trae tipos predefinidos:

| Tipo XSD | Ejemplo de valor válido |
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

Cuando un tipo predefinido no basta, se puede **restringir** con `xs:restriction`, creando un tipo simple propio. Esto es lo que resuelve el problema del Ejercicio 1: forzar que `valoracion` esté entre 1 y 10.

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

Estas restricciones se llaman **facets** (facetas). Las más habituales:

| Faceta | Para qué sirve |
|---|---|
| `xs:minInclusive` / `xs:maxInclusive` | Rango numérico, límites incluidos |
| `xs:minLength` / `xs:maxLength` | Longitud mínima/máxima de un texto |
| `xs:pattern` | Expresión regular que el valor debe cumplir |
| `xs:enumeration` | Lista cerrada de valores permitidos |

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

**🧪 Ejercicio 3 — Restringir tipos**
Añadid a vuestro `catalogo.xsd` una declaración de `<anio>` restringida a `xs:integer` con `xs:minInclusive` en `1900` (no puede haber una serie estrenada antes), y una declaración de `<valoracion>` como en el ejemplo (1 a 10). Validad de nuevo el `catalogo.xml` del Ejercicio 1: el error del año o la valoración fuera de rango, que el DTD no detectaba, ahora sí debe aparecer.

---

## 4. Tipos complejos: elementos con estructura

Un elemento con **hijos** o **atributos** necesita un **tipo complejo** (`xs:complexType`). Es lo que resuelve por fin el elemento raíz `<catalogo>` del Ejercicio 2:

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

Dos formas de declarar un tipo complejo:

- **Anónimo**, definido dentro del propio `xs:element` (como el `catalogo` de arriba) — solo se puede usar ahí.
- **Nombrado**, con `name="SerieType"` fuera de cualquier elemento (como `SerieType`) — se puede **reutilizar** en cualquier `xs:element type="SerieType"`, tantas veces como haga falta. Esto es justo lo que el DTD no permitía hacer bien.

**Plantilla de partida** (completad los huecos `___`):

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
      <!-- pegad aquí la restricción del Ejercicio 3 -->
    </xs:element>
    <xs:element name="valoracion" type="___"/>
  </xs:sequence>
</xs:complexType>
```

**🧪 Ejercicio 4 — El tipo complejo completo**
Completad la plantilla de arriba (con `SerieType` nombrado, incluyendo las restricciones de `anio` y `valoracion` del Ejercicio 3 dentro de él) y sustituid con ella el `<xs:element name="catalogo">` vacío del Ejercicio 2. Validad `catalogo.xml` con dos o tres series — debe pasar sin errores si los datos son correctos.

---

## 5. Compositores y cardinalidad: sequence, choice, all, minOccurs, maxOccurs

`xs:sequence` (usado arriba) exige que los hijos aparezcan **en ese orden exacto**. Hay dos compositores más:

| Compositor | Comportamiento |
|---|---|
| `xs:sequence` | Los elementos hijos deben aparecer en el orden declarado |
| `xs:choice` | Debe aparecer **exactamente uno** de los elementos listados (no varios, no ninguno) |
| `xs:all` | Todos los elementos deben aparecer, pero **en cualquier orden**; en XSD 1.0 cada uno solo puede aparecer una vez |

```xml
<xs:complexType name="ContactoType">
  <xs:choice>
    <xs:element name="email" type="xs:string"/>
    <xs:element name="telefono" type="xs:string"/>
  </xs:choice>
</xs:complexType>
```

Por defecto, cada elemento hijo debe aparecer **exactamente una vez**. Con `minOccurs` y `maxOccurs` se controla cuántas veces:

```xml
<xs:element name="serie" type="SerieType" minOccurs="0" maxOccurs="unbounded"/>
<xs:element name="temporada" type="xs:integer" minOccurs="1" maxOccurs="1"/>
<xs:element name="etiqueta" type="xs:string" minOccurs="0" maxOccurs="5"/>
```

- `minOccurs="0"` hace el elemento **opcional**.
- `maxOccurs="unbounded"` permite repetirlo tantas veces como haga falta (es lo que ya usasteis para `serie` en el Ejercicio 4, sin saber aún el nombre del atributo).
- Cualquier número concreto (`maxOccurs="5"`) pone un tope.

**🧪 Ejercicio 5 — Cardinalidad y elección**
Ampliad `SerieType` con un elemento opcional `<plataforma>` (0 o 1 vez — no todas las series tenéis por qué anotar dónde se ven) y con un `xs:choice` que obligue a elegir **o bien** `<enCurso/>` **o bien** `<finalizada/>` (elementos vacíos, sin contenido, que solo indican un estado). Probad con una instancia que incluya ambos a la vez y comprobad que `xmllint` la rechaza.

---

## 6. Atributos en XSD

Los atributos se declaran con `xs:attribute`, siempre **después** de los elementos hijos dentro de un `xs:complexType`:

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

- `use="required"` — equivale al `#REQUIRED` del DTD: el atributo es obligatorio.
- `use="optional"` (valor por defecto si se omite `use`) — el atributo puede faltar.
- `default="es"` — si el atributo no aparece en el XML, se asume este valor.

Un atributo también puede llevar restricciones, igual que un elemento simple:

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

**🧪 Ejercicio 6 — Atributos obligatorios y con valor por defecto**
Añadid a `SerieType` un atributo `id` de tipo `xs:string`, obligatorio, y un atributo `idioma` opcional restringido a `"es"`, `"en"` o `"ca"`, con valor por defecto `"es"`. Validad una instancia que **no** incluya `idioma` (debe pasar, asumiendo `"es"`) y otra que use un valor fuera de la lista, como `"fr"` (debe fallar).

---

## 7. Tipos reutilizables y grupos

Cuando la misma restricción se repite en varios sitios (por ejemplo, `valoracion` de 1 a 10 podría aplicarse a series **y** a películas si ampliarais el catálogo), conviene extraer un **tipo simple nombrado** en vez de repetirlo:

```xml
<xs:simpleType name="ValoracionType">
  <xs:restriction base="xs:decimal">
    <xs:minInclusive value="1"/>
    <xs:maxInclusive value="10"/>
  </xs:restriction>
</xs:simpleType>

<xs:element name="valoracion" type="ValoracionType"/>
```

Del mismo modo, si un grupo de elementos se repite en varios tipos complejos, se puede extraer con `xs:group`:

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

Extraer tipos y grupos reutilizables no es solo una cuestión de estilo: es lo que, en la CA de esta unidad, se llama **documentar las descripciones** — un esquema con tipos nombrados y bien organizados es mucho más fácil de leer, mantener y reutilizar en otro proyecto que uno con todo definido en línea.

**🧪 Ejercicio 7 — Extraer un tipo reutilizable**
Extraed `ValoracionType` como tipo simple nombrado (a partir del Ejercicio 3) y usadlo en la declaración de `valoracion` dentro de `SerieType`. Añadid un comentario XML (`<!-- ... -->`) justo antes de cada tipo nombrado de vuestro esquema explicando en una frase para qué sirve — es la forma más simple de "documentar las descripciones".

---

## 8. Validar un documento contra su esquema

Ya validasteis con `xmllint --schema` en la UD7 y lo habéis usado en cada ejercicio de esta unidad — aquí cerramos el flujo completo de trabajo, de principio a fin:

```bash
# 1. Comprobar que el XML está bien formado (sintaxis XML correcta)
xmllint --noout catalogo.xml

# 2. Validar el XML contra el esquema XSD
xmllint --noout --schema catalogo.xsd catalogo.xml
```

Un documento puede estar **bien formado** (sintaxis XML correcta: etiquetas cerradas, un único elemento raíz...) y aun así **no ser válido** contra un esquema concreto (por ejemplo, le falta un elemento obligatorio, o un atributo tiene un valor fuera de rango). Son dos comprobaciones distintas, y `xmllint` las hace por separado según qué opciones le pasáis.

Además de `xmllint`, existen validadores XSD con interfaz web, útiles para depurar rápido sin terminal — por ejemplo el de [freeformatter.com/xml-validator-xsd.html](https://www.freeformatter.com/xml-validator-xsd.html), donde pegáis el XML y el XSD y os señala el error con línea y columna, igual que hace `xmllint` en la terminal.

**🧪 Ejercicio 8 — El esquema completo, validado de principio a fin**
Con todo lo construido en los ejercicios anteriores, tened listo un `catalogo.xsd` completo (tipos nombrados, grupo reutilizable, atributos, cardinalidad) y un `catalogo.xml` con al menos 3 series que lo cumplan. Ejecutad las dos validaciones de arriba y comprobad que ambas pasan sin errores. Después, modificad el XML introduciendo **tres** errores distintos a la vez (uno de tipo, uno de cardinalidad, uno de atributo obligatorio ausente) y anotad los tres mensajes de error que devuelve `xmllint`.

---

## 9. Reto de clase

Elegid un dominio propio (distinto del catálogo de series) y construid, de principio a fin:

1. Un documento XML con al menos **5 registros** y **2 niveles de anidamiento**.
2. Un XSD que lo valide, con al menos: un tipo simple restringido, un tipo complejo reutilizable, un compositor con cardinalidad (`minOccurs`/`maxOccurs`), y un atributo obligatorio.
3. Demostración con `xmllint`: una instancia correcta que pasa, y otra con **2 errores deliberados** que falla.

Dos ideas de dominio — elegid la que más os interese, o proponed otro:

- **Perfil ASIX** — un archivo de configuración de un servicio multimedia en red (perfiles de streaming: nombre, puerto, protocolo, códec, bitrate).
- **Perfil DAW** — un dashboard de finanzas personales (movimientos: fecha, categoría, importe, tipo).

> 📋 No hace falta memorizar la sintaxis exacta de cada faceta o compositor — en el reto (y en el test) tendréis siempre a mano una chuleta con la lista de elementos `xs:` vistos en la unidad. Lo que se evalúa es que sepáis **cuándo usar cada pieza**, no que la recordéis de memoria.

---

## Resumen de la unidad

1. El **DTD** no tiene tipos de datos, no es XML, y soporta mal namespaces y reutilización — de ahí que el estándar actual para validar documentos XML sea **XML Schema (XSD)**, publicado por el W3C, que sí resuelve los cuatro puntos.
2. Un esquema XSD es un documento `.xsd` con raíz `xs:schema`; se asocia a un XML con `xsi:noNamespaceSchemaLocation` (o `xsi:schemaLocation` si hay `targetNamespace`) y se valida con `xmllint --noout --schema`.
3. Los **tipos simples** (`xs:string`, `xs:integer`, `xs:decimal`...) describen datos sin hijos ni atributos, y se pueden restringir con `xs:restriction` y facetas (`minInclusive`, `pattern`, `enumeration`...).
4. Los **tipos complejos** (`xs:complexType`) describen elementos con hijos y/o atributos; pueden ser anónimos (uso único) o nombrados (reutilizables en varios elementos).
5. Los **compositores** `sequence`, `choice` y `all` controlan orden y elección de los hijos; `minOccurs`/`maxOccurs` controlan cuántas veces puede (o debe) aparecer cada uno.
6. Los **atributos** se declaran con `xs:attribute`, con `use="required"`/`"optional"` y, opcionalmente, `default`.
7. Extraer **tipos y grupos reutilizables** (`xs:simpleType`, `xs:complexType`, `xs:group` nombrados) evita repetir definiciones y es la forma práctica de documentar un esquema.
8. El flujo de validación separa dos comprobaciones distintas: que el XML esté **bien formado** y que sea **válido** contra un esquema concreto.

---

## 📚 Para saber más (opcional, no evaluable)

XSD no es la única forma de describir esquemas hoy en día: en el mundo de las APIs modernas, el equivalente para **JSON** (que ya conocéis de la UD7) es **JSON Schema** — mismo objetivo (tipos, restricciones, validación automática), sintaxis muy distinta, pensada para JSON en lugar de XML. Si en el futuro trabajáis con APIs REST que documentan su formato de datos, es muy probable que os encontréis con JSON Schema en vez de XSD.

- Especificación oficial de XML Schema (W3C): [www.w3.org/XML/Schema](https://www.w3.org/XML/Schema)
- Tutorial interactivo de XSD: [www.w3schools.com/xml/schema_intro.asp](https://www.w3schools.com/xml/schema_intro.asp)
- Validador XSD online: [www.freeformatter.com/xml-validator-xsd.html](https://www.freeformatter.com/xml-validator-xsd.html)
- JSON Schema (para cuando trabajéis con APIs): [json-schema.org](https://json-schema.org/)
