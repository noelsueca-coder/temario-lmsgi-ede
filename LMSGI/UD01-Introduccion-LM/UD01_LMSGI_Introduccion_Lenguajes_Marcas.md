<div style="text-align: center;">

<img src="data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCA0MDAgNDAwIiB3aWR0aD0iMTgwIiBoZWlnaHQ9IjE4MCI+CiAgPGNpcmNsZSBjeD0iMjAwIiBjeT0iMjAwIiByPSIxNzAiIGZpbGw9IiNGMEZERkEiLz4KICA8Y2lyY2xlIGN4PSIyMDAiIGN5PSIyMDAiIHI9IjE3MCIgZmlsbD0ibm9uZSIgc3Ryb2tlPSIjOTlGNkU0IiBzdHJva2Utd2lkdGg9IjIiLz4KICA8dGV4dCB4PSIyMDAiIHk9IjI0OCIgZm9udC1mYW1pbHk9IidDb3VyaWVyIE5ldycsIENvdXJpZXIsIG1vbm9zcGFjZSIgZm9udC1zaXplPSIxNTAiIGZvbnQtd2VpZ2h0PSI3MDAiIGZpbGw9IiMwRjc2NkUiIHRleHQtYW5jaG9yPSJtaWRkbGUiPiZsdDsvJmd0OzwvdGV4dD4KPC9zdmc+Cg==" width="180" alt="Logo LMSGI"/>

<h1>Unidad 1</h1>
<h2>Introducción a los lenguajes de marcas</h2>

<p>
<strong>Módulo:</strong> Llenguatges de Marques i Sistemes de Gestió d'Informació (LMSGI)<br>
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

1. ¿Qué es un lenguaje de marcas? Características generales (CA 1a)
2. Ventajas de los lenguajes de marcas (CA 1b)
3. Origen y clasificación de los lenguajes de marcas (CA 1c)
4. XML como lenguaje de marcas de propósito general (CA 1d-1i)
   - 4.1 Ámbitos de aplicación
   - 4.2 Estructura y sintaxis
   - 4.3 Documentos bien formados
   - 4.4 Espacios de nombres
5. Resumen de la unidad
6. Para saber más

<div style="page-break-after: always;"></div>

**RA cubierto:** RA1 — *Reconoce las características de los lenguajes de marcas analizando e interpretando fragmentos de código* (CA 1a-1i)

> 💡 **Nota de estudio**: en esta unidad hay poca "teoría para memorizar" y mucha idea que necesitas entender para poder programar después. Si un concepto no queda claro a la primera, puedes repasarlo por tu cuenta — lo importante es que sepas *reconocer* un lenguaje de marcas y *escribir* un XML correcto al final de la unidad.

---

## 1. ¿Qué es un lenguaje de marcas? Características generales (CA 1a)

Un **lenguaje de marcas** (*markup language*) sirve para **dar formato o estructura a un texto**, insertando dentro del propio texto unas señales especiales llamadas **marcas** (o *etiquetas*), normalmente encerradas entre `<` y `>` y casi siempre por parejas (apertura y cierre) — sin necesidad de un lenguaje de programación.

Vamos a verlo con las manos antes que con la definición.

**🧪 Paso a paso — Tu primer documento marcado**

1. Crea una carpeta para este módulo (por ejemplo, `LMSGI`, en tu carpeta personal).
2. Abre un editor de texto sencillo — en LLiurex tienes **Mousepad**, en el menú de Aplicaciones → Accesorios — y guarda ahí un archivo nuevo llamado `textos.txt`.
3. Escribe dentro exactamente esto:
   ```
   <h1>Texto grande</h1>
   <h3>Texto pequeño</h3>
   ```
4. Guarda y vuelve a abrirlo con doble clic. Es un archivo de texto normal: ves las marcas tal cual las escribiste.
5. Ahora cambia el nombre del archivo a `textos.html` (clic derecho → *Renombrar* — cambia también la extensión, no solo el nombre) y ábrelo con el navegador: arrastrándolo a una ventana de Firefox, o con clic derecho → *Abrir con* → Firefox.

El contenido no ha cambiado ni una letra. Lo que ha cambiado es **quién lo interpreta**: Mousepad te enseña el texto literal; el navegador reconoce `<h1>` y `<h3>` como marcas y las convierte en un título grande y uno pequeño. Al programa que interpreta las marcas para presentarlas a un usuario final se le llama **user-agent** (navegadores, lectores de pantalla...), y el mismo documento puede dar resultados muy distintos según cuál lo procese. Un editor de código como VS Code no es estrictamente un user-agent — no está pensado para "presentar" el documento, sino para ayudarte a escribirlo —, pero es un tercer programa útil para comparar cómo cada uno trata las mismas marcas:

| Programa | Qué hace con las marcas | ¿Es un user-agent? |
|---|---|---|
| **Navegador** (Firefox, Chrome...) | Las convierte en texto renderizado, tablas, imágenes en pantalla | Sí |
| **Lector de pantalla** | Las anuncia por voz para personas con discapacidad visual: "encabezado nivel 2, Ventajas de los lenguajes de marcas" | Sí |
| **Editor de código** (VS Code...) | Resalta la sintaxis en colores, pliega bloques, muestra vista previa (como este mismo documento en Markdown) | No, en sentido estricto — te ayuda a escribir el documento, no te lo "presenta" |

> 💡 **Los encabezados van de `<h1>` a `<h6>`** — no indican tamaño de letra, sino **nivel de importancia** dentro del documento. Que `<h1>` se vea más grande es solo el estilo que aplica el navegador *por defecto*; con CSS (lo veréis en la UD4) se puede cambiar el tamaño sin tocar esa jerarquía. El texto "normal" no lleva ninguna etiqueta de encabezado, se escribe dentro de un párrafo (`<p>`).

⚠️ **Importante**: no confundas un lenguaje de marcas (LM) con un **lenguaje de programación** (LP). Un LM no tiene variables, bucles ni funciones — solo describe formato o estructura. Cuando un LM se combina con un LP (por ejemplo HTML + JavaScript) decimos que el documento se ha "programado", pero el HTML en sí mismo no lo es.

**🧪 Ejercicio 1 — Tres programas, tres lecturas**
Abre tu `textos.html` con un editor de código, mostrando el archivo en bruto (sin vista previa). Ya tienes tres programas distintos procesando el mismo documento marcado: Mousepad, el navegador y el editor de código — pero solo el navegador encaja en el concepto estricto de *user-agent*. Explica con tus palabras qué hace cada uno con las mismas marcas, y qué crees que pasaría si en vez de un navegador lo "abriera" un lector de pantalla.

---

### Características generales

Todo lo que acabas de hacer con `textos.html` ya te ha enseñado dos de las características que definen a cualquier lenguaje de marcas — vamos a ponerles nombre, y a añadir las que faltan:

- **Texto plano**: lo acabas de comprobar — Mousepad te enseña el código tal cual, sin necesitar un programa especial.
- **Independencia**: también lo acabas de ver — el mismo `textos.html`, interpretado por Mousepad, el navegador y un editor de código, da tres resultados distintos. El documento no cambia; quien lo interpreta, sí.
- **Integración**: las marcas van incrustadas en el propio texto del documento, en un único archivo — no hay un archivo de contenido por un lado y otro de formato por otro, sincronizados a mano, como hacían formatos más antiguos.
- **Especialización**: no son solo para la web — hay lenguajes de marcas para matemáticas (**MathML**), música (**MusicXML**), química (**CML**, para moléculas y reacciones) o síntesis de voz (**SSML**).
- **Flexibilidad**: se combinan fácilmente con otros lenguajes sin dejar de ser ellos mismos — lo veréis en el punto 2, cuando HTML incorpore JavaScript.

> 💡 Estas cinco son las que veréis citadas en cualquier manual sobre lenguajes de marcas — no es una lista cerrada ni una ley universal (hay excepciones, como el formato binario **EXI**, que codifica XML perdiendo la propiedad de "texto plano"), pero sí son las que definen a la gran mayoría.

Cada una de estas características, cuando aporta un beneficio práctico concreto, se convierte en una **ventaja** — eso es exactamente lo que vais a ver en el punto 2.

**🧪 Ejercicio 2 — Características, a examen**
Para cada uno de estos elementos, indica cuáles de las 5 características (texto plano, independencia, integración, especialización, flexibilidad) cumple y cuáles no, razonando tu respuesta:
- Tu propio `textos.html`.
- Una fotografía `.jpg`.
- Un archivo `.docx`.

---

## 2. Ventajas de los lenguajes de marcas (CA 1b)

Con tu `textos.html` recién creado ya puedes comprobar en la práctica qué ventaja concreta trae cada característica del punto 1.

- **Texto plano** — esto es lo que hace posible: se pueden leer, escribir y editar con cualquier editor, sin software específico ni licencias, como acabas de hacer. Prueba a abrir con Mousepad una imagen `.jpg` o un `.docx` cualquiera: ilegible, porque es un binario y necesita el programa que lo generó para poder leerse.

  Esto tiene una consecuencia que vais a usar todo el curso: al ser texto, herramientas como Git pueden comparar dos versiones línea a línea. Abre una terminal (clic derecho sobre el escritorio → *Abrir terminal aquí*, o desde el menú de Aplicaciones) y sitúate en tu carpeta:
  ```bash
  git init                        # inicia el repositorio en tu carpeta
  git add .
  git commit -m "Versión inicial" # guarda una "fotografía" de este estado
  # ...cambias <h1>Texto grande</h1> por <h1>Hola</h1> y guardas...
  git diff                        # compara el estado actual con el último commit
  ```
  ```diff
  - <h1>Texto grande</h1>
  + <h1>Hola</h1>
  ```
  Con un binario, Git solo podría decir "esto es distinto", nunca "qué ha cambiado" — y si dos personas lo editan a la vez, no hay forma de combinar ambos cambios automáticamente.

- **Independencia** — esta es su ventaja práctica: el mismo HTML se ve en una columna en el móvil y en varias en el ordenador, y al imprimir una página muchos sitios ocultan el menú de navegación — el HTML no cambia, solo la interpretación de cada salida. Es la base de **separar contenido y presentación**:
  ```html
  <h1>Título</h1>
  ```
  ```css
  h1 { color: blue; font-size: 3em; }
  @media print { h1 { color: black; font-size: 1.5em; } }
  ```
  Si mezclaras el formato dentro del contenido (`<font size="7" color="blue">Título</font>`), necesitarías una copia distinta por cada dispositivo.

- **Facilidad de intercambio** — consecuencia directa de ser texto plano con una sintaxis pública y documentada: cualquier sistema lo lee y lo escribe sin necesitar el programa original — un lector de feeds RSS de cualquier fabricante lee el feed de cualquier blog (volveréis a ver un feed RSS en el punto 4.4); Word, LibreOffice y Google Docs abren el mismo `.docx`.

- **Flexibilidad** — la que os adelantaba en el punto 1: HTML incorpora JavaScript (`<script>`) para dar comportamiento dinámico, o un `<svg>` se inserta directamente dentro de una página HTML.

**🧪 Ejercicio 3 — Compruébalo con tus manos**
1. En tu `textos.html`, cambia `<h3>Texto pequeño</h3>` por otro texto cualquiera y guarda.
2. Ejecuta `git diff` (si aún no tienes Git instalado, instálalo con `sudo apt install git`, o compara a ojo las dos versiones). ¿Ves exactamente qué línea ha cambiado y cuál no?
3. Coge cualquier imagen que tengas a mano y ábrela con Mousepad. ¿Podrías hacer con ella el mismo `git diff` línea a línea? Relaciona tu respuesta con la ventaja de "texto plano".

---

## 3. Origen y clasificación de los lenguajes de marcas (CA 1c)

En los inicios de la informática cada aplicación usaba sus propias marcas, así que no había forma de intercambiar un documento entre plataformas distintas. Para resolverlo apareció en los años 80 un estándar común, **SGML** — no es un lenguaje con etiquetas propias, sino un **metalenguaje**: define las reglas para crear otros lenguajes de marcas. De ahí nacen, por caminos distintos, los dos que vais a usar todo el curso:

- **XML** es un **subconjunto simplificado** de SGML: se creó para quedarse con lo esencial, con una sintaxis mucho más fácil de procesar.
- **HTML** es una **aplicación de SGML**, pero nunca ha sido tan estricto: los navegadores siempre lo han interpretado de forma permisiva, "perdonando" errores que XML rechazaría directamente. Por eso en la UD2 podréis dejar una etiqueta HTML mal cerrada y el navegador la arreglará solo, mientras que en XML (apartado 4.3 de esta unidad) el mismo error detiene todo el documento. Hoy, el HTML Living Standard define sus propias reglas de análisis y evolución, independientes de SGML — la relación entre ambos es sobre todo histórica.

> 🕰️ Casi nadie escribe SGML directamente hoy en día — se estudia solo porque explica *por qué* XML y HTML son como son, no porque vayáis a usarlo.

Además de XML y HTML hay otros formatos con los que os cruzaréis en el módulo — no todos son estrictamente lenguajes de marcas, pero conviene ubicarlos:

| Lenguaje | Para qué sirve | ¿Lo usaréis en este módulo? |
|---|---|---|
| **HTML** | Estructurar páginas web | Sí — desde la UD2 |
| **XML** | Intercambio de datos estructurados | Sí — el resto de esta unidad |
| **JSON** | Notación de datos ligera, muy usada en APIs web | Sí — más adelante en el módulo |
| **Markdown** | Marcado ligero para notas y documentación técnica | Se trabaja aparte, en una práctica independiente |

> 🕰️ Fuera de esta tabla hay más lenguajes de marcas con usos muy concretos (LaTeX para documentos científicos, PostScript para impresión, RTF...). No os hacen falta para este módulo.

**Clasificación.** Con estos cuatro lenguajes que ya conocéis podéis ver cómo se clasifica cualquier lenguaje de marcas según su tipo de marca:

| Tipo | Qué hace | En lo que ya conocéis |
|---|---|---|
| **De presentación** | Solo dice cómo se ve el texto, no qué es cada parte | Markdown: `**negrita**` no dice si es un título o un aviso, solo que se vea en negrita |
| **Descriptivo / estructural** | Dice qué es cada dato, sin decir cómo se muestra | XML: `<titulo>El Quijote</titulo>` dice qué es ese dato, no si va grande o pequeño |
| **Híbrido** | Mezcla las dos cosas | HTML: `<h1>` dice qué es (un encabezado) y además el navegador decide por defecto cómo se ve |

---

## 4. XML como lenguaje de marcas de propósito general (CA 1d-1i)

El resto de la unidad se centra en **XML**, el lenguaje de marcas de propósito general que vais a usar durante todo el módulo. Vamos a verlo en cuatro pasos: para qué sirve y dónde se usa, cómo se escribe, qué reglas debe cumplir para ser válido, y cómo evita que choquen etiquetas de distintos orígenes.

> ⭐ **XML es el protagonista de esta unidad.** Todo lo demás que aparece — SGML, HTML, JSON, Markdown, XHTML — lo hace como antecedente histórico, ejemplo de comparación o aplicación práctica; el objetivo final del RA1 es que reconozcáis y escribáis XML.

### 4.1 Ámbitos de aplicación (CA 1d, 1e)

Cuantos más dispositivos y sistemas distintos existen, más falta hace un estándar común para intercambiar información. Esto es lo que resuelve la **estandarización**: el proceso de fijar normas para que elementos construidos de forma independiente (por ejemplo, dos aplicaciones de empresas distintas) funcionen bien juntos.

Las organizaciones que fijan estos estándares son principalmente el **W3C** (*World Wide Web Consortium*), **ISO** y la comunidad **Open Source**.

**XML** (*eXtensible Markup Language*) surge como el lenguaje de marcas de **propósito general**: un subconjunto de SGML pensado para ser más sencillo, con sintaxis más estricta, y que sirve para *cualquier* tipo de información estructurada, no solo para la web. Sus características principales son:

- Es un **metalenguaje**: permite crear infinitas etiquetas propias, adaptadas a cada necesidad — es justo lo que haréis en el apartado siguiente, al construir vuestro propio vocabulario con etiquetas inventadas por vosotros mismos. A diferencia de HTML, cuyo conjunto de etiquetas es fijo y lo define el WHATWG, en XML las etiquetas las decides tú según lo que necesites representar.
- Es **estructurado**: organiza los datos como un árbol jerárquico (lo veremos en el apartado siguiente) sin pensar en cómo se presentarán — la misma separación de contenido y presentación que vimos en el punto 2.
- Es **validable**: se puede comprobar automáticamente, antes de procesarlo, si un documento cumple una estructura definida (un DTD o un XML Schema) — útil, por ejemplo, para rechazar de entrada un archivo mal formado que llega de otro sistema, sin tener que ejecutar código para descubrir el error.
- **No está limitado a la web**: se usa en cualquier tipo de aplicación — archivos de configuración, los formatos de Office por dentro (`.docx`, `.xlsx`), recursos de apps Android, intercambio de datos entre sistemas empresariales…

Algunos lenguajes construidos a partir de XML:

| Lenguaje | Uso |
|---|---|
| SVG | Gráficos vectoriales 2D |
| MathML | Fórmulas matemáticas |
| SMIL | Información multimedia |
| SSML | Síntesis de voz |

> 📡 **SVG, presente en tu día a día sin que lo notes**: cada icono, logo o ilustración vectorial que ves en la web suele ser SVG — incluido el logo `</>` de la portada de esta misma unidad, hecho exactamente así. Al ser XML, un navegador puede insertarlo directamente dentro del HTML (como en la portada) y modificarlo con CSS o JavaScript igual que cualquier otro elemento de la página — algo que una imagen de píxeles (`.png`, `.jpg`) no permite. Además es independiente de la resolución: el mismo archivo se ve nítido tanto en un icono pequeño como ampliado a pantalla completa, porque no está hecho de píxeles sino de fórmulas geométricas.

**Icono de la portada, explicado línea a línea:**

```html
<!--
  viewBox="0 0 400 400"  → el lienzo interno mide 400×400 unidades.
  width/height="180"     → el tamaño final en pantalla. Al ser vectorial,
                            podrías poner 1800 y se vería igual de nítido.
-->
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 400 400" width="180" height="180">

  <!-- Primer círculo: el relleno. Verde muy suave, sin borde. -->
  <circle cx="200" cy="200" r="170" fill="#F0FDFA"/>

  <!-- Segundo círculo: el mismo círculo, pero solo el contorno
       (fill="none"), dibujado encima del anterior. Entre los dos
       dan el efecto de "círculo con borde". -->
  <circle cx="200" cy="200" r="170" fill="none" stroke="#99F6E4" stroke-width="2"/>

  <!-- El símbolo "</>"  centrado (text-anchor="middle"), en verde
       oscuro. Los símbolos < y > van escritos como &lt; y &gt;:
       si se pusieran literalmente, el navegador los confundiría
       con el inicio de otra etiqueta. -->
  <text x="200" y="248" font-family="'Courier New', Courier, monospace" font-size="150" font-weight="700" fill="#0F766E" text-anchor="middle">&lt;/&gt;</text>

</svg>
```

**🧪 Ejercicio 4 — Tu propio icono SVG**
Parte del código SVG de arriba y modifícalo para crear tu propio icono: cambia el texto, los colores (`fill`, `stroke`) o añade una segunda forma (por ejemplo un `<rect>` o un segundo `<circle>`). Guárdalo como `.svg` y ábrelo directamente con el navegador para ver el resultado. Después, responde: siendo una imagen, ¿por qué se puede editar con un editor de texto normal?

---

### 4.2 Estructura y sintaxis (CA 1f, 1g)

Un documento XML se organiza como un **árbol**: un único **elemento raíz** que contiene otros elementos anidados dentro.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<nota>
  <de>Pablo</de>
  <para>Eric</para>
  <encabezado>Recordatorio</encabezado>
  <cuerpo>Pablo, si no estudias, la IA no va a hacer que apruebes solo!</cuerpo>
</nota>
```

Elementos de la sintaxis:

- **Declaración XML** (opcional pero recomendada): `<?xml version="1.0" encoding="UTF-8"?>` — indica la versión de XML y la codificación de caracteres usada. Casi siempre verás esta misma declaración; solo cambiaría si usaras otra codificación, por ejemplo `<?xml version="1.0" encoding="ISO-8859-1"?>` (una codificación más antigua, hoy en desuso frente a UTF-8).
- **Elemento**: la unidad básica, formada por una etiqueta de apertura y una de cierre. Ejemplos: `<de>Pablo</de>`, `<ciudad>Algemesí</ciudad>`, `<precio>19.99</precio>` — el contenido puede ser texto, un número, o incluso otros elementos anidados.
- **Elemento raíz**: el elemento que engloba a todos los demás. Solo puede haber uno por documento. Aquí es `<nota>`; como veréis enseguida en el ejemplo del catálogo, será `<catalogo>`; en un archivo de configuración podría ser `<configuracion>` o `<settings>`.
- **Anidamiento**: los elementos pueden contener otros elementos dentro, formando una jerarquía (árbol). Por ejemplo:

```xml
<alumno>
  <nombre>Claudia</nombre>
  <notas>
    <nota>7</nota>
    <nota>8.5</nota>
  </notas>
</alumno>
```

  Aquí `<notas>` contiene varios `<nota>`, que a su vez están dentro de `<alumno>` — tres niveles de anidamiento.
- **Atributos**: información adicional dentro de la propia etiqueta de apertura, en pares `nombre="valor"`. Un elemento puede tener varios atributos a la vez:

```xml
<persona edad="20" ciudad="Valencia">Claudia</persona>
<libro isbn="978-84-376-0494-7" idioma="es">El Quijote</libro>
```

- **Elemento vacío**: un elemento sin contenido se puede escribir con autocierre. Ejemplos: `<linea/>` en vez de `<linea></linea>`, o `<separador tipo="doble"/>` — un elemento vacío también puede llevar atributos.

> 📡 **Sigue vigente**: aunque hoy JSON gane en las APIs web, esta misma estructura de árbol es la que usan a diario los archivos de Office, los SVG y los feeds RSS.

**Construyendo un XML completo, paso a paso**

Todo lo que hereda de SGML se compone de tres partes: una **declaración**, un **DTD** (*Document Type Definition*: qué etiquetas existen y cómo se combinan) y una **instancia** (los datos reales, con la estructura de árbol que acabas de ver). Vamos a construirlas juntas con un catálogo de series:

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

Por partes:

- **Declaración** (`<?xml version="1.0" encoding="UTF-8"?>`): siempre la primera línea, la misma que ya conoces.
- **DTD** (dentro de `<!DOCTYPE catalogo [ ... ]>`): las reglas del vocabulario que os acabáis de inventar.
  - `<!ELEMENT catalogo (serie+)>` — un `<catalogo>` contiene una o más `<serie>` (el `+` significa "una o más veces").
  - `<!ELEMENT serie (titulo, estudio, episodios, estado)>` — cada `<serie>` debe tener exactamente esos cuatro elementos, en ese orden.
  - `<!ATTLIST serie id CDATA #REQUIRED>` — `<serie>` debe llevar obligatoriamente (`#REQUIRED`) un atributo `id` de tipo texto (`CDATA`). Lo mismo para `formato`.
  - `<!ELEMENT titulo (#PCDATA)>` — `<titulo>` solo contiene texto normal (*Parsed Character Data*), nada anidado dentro.
  - Las líneas que empiezan por `<!--` y acaban en `-->` son comentarios: no forman parte de las reglas, son para que quien lea el DTD entienda por qué está así.
- **Instancia** (`<catalogo>...</catalogo>`): los datos reales, que tienen que cumplir todas las reglas anteriores — dos elementos `<serie>`, cada uno con sus cuatro elementos en orden y sus dos atributos.

> 💡 Si en la instancia faltara un elemento obligatorio, cambiarais el orden, u olvidarais un atributo `#REQUIRED`, un procesador XML que valide contra este DTD lo rechazaría — esto es justo la propiedad de **validable** que habéis visto en el apartado 4.1.

> ⚠️ **No memorices la sintaxis del DTD** — no es el objetivo de esta unidad. Lo que os interesa es entender *para qué sirve* (definir y validar un vocabulario) y saber leerlo cuando os lo encontréis; profundizaréis en la validación con XML Schema en la UD7 y en esquemas y vocabularios en la UD8.

**🧪 Ejercicio 5 — Haz tu propio XML**
Elige un tema tuyo (una colección de videojuegos, tu lista de series, los módulos de este curso...) y, siguiendo el mismo modelo del catálogo de series de arriba, escribe:
- la **declaración** XML,
- un **DTD** dentro de `<!DOCTYPE ...[ ... ]>` con al menos un `<!ELEMENT>` que use `+` o una lista con orden fijo, un `<!ATTLIST>` con algún atributo `#REQUIRED`, y algún elemento `(#PCDATA)`,
- una **instancia** con al menos dos elementos repetidos que cumplan esas reglas.

**🧪 Ejercicio 6 — De tabla a XML**
Convierte esta tabla en un documento XML, usando `<discografia>` como elemento raíz, un elemento `<disco>` por fila, un atributo para el año, y un elemento vacío `<agotado/>` en los discos marcados como agotados. No olvides la declaración XML al principio.

| Título | Año | Agotado |
|---|---|---|
| Álbum A | 2019 | No |
| Álbum B | 2021 | Sí |
| Álbum C | 2023 | No |

---

### 4.3 Documentos XML bien formados (CA 1h)

Se dice que un documento XML está **bien formado** cuando cumple las reglas sintácticas básicas del lenguaje. Si no las cumple, ningún procesador XML podrá interpretarlo — dará error directamente, a diferencia de HTML, que muchos navegadores "perdonan" aunque tenga errores.

Reglas principales — con qué pasa si no se cumplen:

1. **Debe existir un único elemento raíz** que contenga a todos los demás.

   ❌ Mal:
   ```xml
   <titulo>Curso</titulo>
   <modulo>LMSGI</modulo>
   ```
   Sin un elemento raíz común, no hay un único árbol que contenga todo el documento. El procesador ni siquiera llega a interpretar el contenido: da error de "documento sin elemento raíz" antes de leer nada más.

2. **Toda etiqueta que se abre debe cerrarse**: `<titulo>Texto</titulo>`, nunca dejarla abierta.

   ❌ Mal:
   ```xml
   <titulo>Curso
   ```
   Al llegar al final del documento sin encontrar `</titulo>`, el procesador lanza un error de "etiqueta sin cerrar" (*unclosed tag*).

3. **El anidamiento debe respetarse**: no se pueden cruzar etiquetas. `<a><b></a></b>` está mal; `<a><b></b></a>` está bien.

   ❌ Mal: `<a><b></a></b>`
   El procesador espera `</b>` (la última etiqueta abierta) y se encuentra `</a>`: error de "etiqueta de cierre inesperada" (*unexpected closing tag*).

4. **Los valores de los atributos siempre van entre comillas**: `edad="25"`, no `edad=25`.

   ❌ Mal:
   ```xml
   <persona edad=20 ciudad=Valencia>Claudia</persona>
   ```
   Sin comillas, el procesador no sabe dónde termina el valor de `edad` y dónde empieza el siguiente atributo: error de sintaxis al analizar los atributos.

5. **XML distingue mayúsculas de minúsculas**: `<Titulo>` y `<titulo>` son etiquetas distintas, y una no cierra a la otra.

   ❌ Mal: `<Titulo>Curso</titulo>`
   Para XML, `<Titulo>` y `</titulo>` son dos etiquetas diferentes, así que la de apertura nunca queda cerrada: el mismo error de "etiqueta sin cerrar" que en la regla 2.

6. Los elementos vacíos deben cerrarse con `/>` o con su etiqueta de cierre: `<linea/>` o `<linea></linea>`.

   ❌ Mal: `<linea>`
   Al no llevar ni `/>` ni una etiqueta de cierre `</linea>`, el procesador la trata como una etiqueta abierta que nunca se cierra: mismo error que en la regla 2.

En los seis casos el resultado es el mismo: el procesador XML se detiene con un error y no genera ningún documento, sin intentar "adivinar" qué querías decir — justo lo contrario de lo que hace HTML.

> 🕰️ **El intento histórico de aplicar esto a HTML**: a finales de los 90 se creó **XHTML**, una versión de HTML reescrita para obligar a cumplir estas mismas reglas de buen formado (cerrar siempre `<br/>` o `<img/>`, atributos entre comillas, minúsculas obligatorias). La idea era que las páginas web se pudieran procesar con las mismas herramientas que XML. En la práctica, **XHTML ha quedado en un segundo plano**: HTML5 absorbió parte de esa disciplina sin exigir la sintaxis estricta, y hoy XHTML apenas se usa en desarrollo nuevo. Aun así, entender el buen formado de XML te ayuda a escribir mejor HTML.

**🧪 Ejercicio 7 — Bien formado, de la teoría a la práctica**

*Parte A:* Escribe un documento XML bien formado que describa 3 alumnos de tu clase (nombre, edad, módulo favorito), aplicando las 6 reglas de este punto.

*Parte B:* A partir de tu propio documento de la Parte A, crea una copia "estropeada" introduciendo 3 o 4 errores deliberados de buen formado (por ejemplo: cambia una etiqueta a mayúsculas, elimina un cierre, cruza el anidamiento, quita las comillas de un atributo). Intercámbiala con un compañero, sin decirle qué has cambiado, y que identifique a qué regla corresponde cada error.

---

### 4.4 Espacios de nombres en XML (CA 1i)

Como en XML cualquiera puede inventarse sus propias etiquetas, es fácil que dos vocabularios que quieres combinar usen la **misma etiqueta con significados distintos**, o que uno de ellos necesite añadir información que el otro no contempla. Por ejemplo, un feed RSS (ya visto en el punto 2) solo define etiquetas genéricas (`<title>`, `<description>`...), pero las apps de podcasts necesitan datos extra que el RSS estándar no tiene: duración del episodio, autor, categoría, portada...

Los **espacios de nombres** (*namespaces*) resuelven este choque, asociando cada conjunto de etiquetas a una URI que las identifica de forma única. Así, un feed puede mezclar el vocabulario estándar de RSS con el vocabulario propio de podcasts (definido originalmente por Apple, con prefijo `itunes`, y adoptado también por Spotify y otros) sin que haya ambigüedad:

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

- `xmlns:itunes="..."` define un **prefijo** (`itunes`) asociado a una URI concreta.
- Las etiquetas sin prefijo (`<title>`) son RSS estándar: cualquier lector de feeds las entiende.
- Las etiquetas `itunes:algo` son el vocabulario añadido: un lector de feeds genérico que no las conoce las ignora sin romperse; una app de podcasts sí las interpreta para mostrar duración, autor, portada...
- La URI no es un enlace que nadie visite ni tiene que "existir" como página — es solo un identificador único. Por convención se usa un dominio del creador del vocabulario, para evitar que dos personas elijan el mismo prefijo por casualidad.

> 📡 **Sigue siendo necesario hoy**: los espacios de nombres se usan continuamente en la práctica.
> - Cuando insertas un `<svg>` dentro de una página HTML5, el navegador activa automáticamente el namespace de SVG en cuanto encuentra esa etiqueta (una regla especial de "contenido foráneo" del estándar HTML5) — no escribes el `xmlns` a mano, pero el mecanismo que lo hace posible es este.
> - En feeds como el de arriba, para combinar el vocabulario estándar con el de podcasts, imágenes, geolocalización, etc. sin que las etiquetas choquen.
> - Los propios archivos de Office (`.docx`, `.xlsx`, `.pptx`) son, por dentro, XML con varios espacios de nombres combinados (uno para el texto o las celdas, otro para estilos, otro para relaciones entre archivos internos del paquete) — la misma idea que ves aquí, a mayor escala.

**🧪 Ejercicio 8 — Amplía el feed de podcast**
Parte del ejemplo de feed de este punto y añade un segundo espacio de nombres inventado por ti (por ejemplo `miapp`, con una URI a tu elección) con al menos dos etiquetas propias (por ejemplo `<miapp:valoracion>` o `<miapp:transcripcion>`). Declara el `xmlns` correspondiente y usa el prefijo correctamente. Después, explica qué pasaría si, en lugar de un prefijo distinto, hubieras llamado a tu etiqueta simplemente `<title>`.

---

<div style="page-break-after: always;"></div>

## Resumen de la unidad

**1. ¿Qué es un lenguaje de marcas? Características generales** Un sistema de marcas insertadas en el propio texto (entre `<` y `>`) que interpreta un *user-agent* — el mismo documento puede dar resultados distintos según quién lo procese. No es un lenguaje de programación. Cinco características generales: texto plano, independencia, integración, especialización y flexibilidad — rasgos habituales, no una ley cerrada (hay excepciones, como el binario EXI).

**2. Ventajas de los lenguajes de marcas** Cada característica del punto 1 trae una ventaja práctica: texto plano (editable sin software específico, comparable línea a línea con Git), independencia (separación entre contenido y presentación), facilidad de intercambio entre sistemas distintos, y flexibilidad para combinarse con otros lenguajes.

**3. Origen y clasificación** SGML (metalenguaje del que nacen, por caminos distintos, XML y HTML) resuelve el problema de que cada aplicación tuviera sus propias marcas. Los lenguajes de marcas se clasifican por tipo de marca (presentación / estructural / híbrida), vista con los ejemplos ya conocidos (Markdown, XML, HTML).

**4. XML como lenguaje de marcas de propósito general**
- *Ámbitos de aplicación*: XML es un metalenguaje, estructurado en árbol, validable y no limitado a la web. Lenguajes construidos sobre XML: SVG, MathML, SMIL, SSML.
- *Estructura y sintaxis*: declaración XML, elemento raíz único, anidamiento, atributos y elementos vacíos — y construcción guiada de un XML completo (declaración, DTD con elementos, atributos y `#PCDATA`, e instancia) con el ejemplo del catálogo de series.
- *Documentos bien formados*: seis reglas sintácticas obligatorias (raíz única, cierre de etiquetas, anidamiento correcto, atributos entre comillas, sensibilidad a mayúsculas, elementos vacíos cerrados). Si no se cumplen, el procesador da error directamente — a diferencia de HTML.
- *Espacios de nombres*: resuelven los choques de etiquetas entre vocabularios distintos, asociando cada uno a una URI única mediante prefijos (`xmlns:prefijo="URI"`) — imprescindibles al combinar formatos (SVG en HTML, feeds, archivos de Office).

---

## 📚 Para saber más (opcional, no evaluable)

### ¿Para qué te va a servir el XML de esta unidad?

Lo que habéis visto aquí (declaración, DTD, bien formado, namespaces) es la base mínima — la profundización real llega a partir de la **UD7** (validación con XML Schema), **UD8** (esquemas y vocabularios), **UD9** (conversión con XSLT) y **UD10** (almacenamiento y consulta). No hace falta dominarlo todo ya: de momento basta con reconocer un XML y saber si está bien formado.

Dicho esto, a fecha de este curso (2026-2027) hay sitios muy concretos donde os podéis encontrar XML trabajando, más allá de un examen:

- **Factura electrónica**: España va camino de hacer obligatoria la factura electrónica entre empresas (Real Decreto 238/2026), y los formatos admitidos — Facturae, UBL, CII — son XML. Cualquier empresa que facture a otra, o a la Administración, pasa por aquí.
- **Transferencias bancarias**: el estándar internacional **ISO 20022**, que usan los bancos (incluido SEPA) para transferencias y liquidación de valores, es XML.
- **Documentos de Office**: `.docx`, `.xlsx`, `.pptx` son, por dentro, XML comprimido — lo vimos en el apartado 4.1.
- **Feeds RSS/Atom**: los mismos que construisteis en el apartado 4.4 — podcasts, blogs, cualquier "suscríbete" de una web.
- **Integración empresarial y sanitaria**: muchas APIs tipo SOAP y el estándar **HL7** (historiales clínicos, sistemas hospitalarios) siguen en XML — sobre todo en sistemas grandes que llevan años funcionando y no se sustituyen de un día para otro.
- **Herramientas de desarrollo**: proyectos Java con Maven (`pom.xml`), configuración de Android — aunque en Android está cambiando activamente: los proyectos nuevos usan cada vez más Jetpack Compose (código Kotlin) en vez de XML para las pantallas, así que ahí el peso de XML está bajando.

> 💡 En resumen: no es una tecnología "del pasado" que se estudia por completitud — es la tubería silenciosa por la que circula buena parte de los datos entre empresas, bancos y administraciones. No siempre se ve, pero está.

### ¿Y el HTML que solo hemos visto de pasada?

Todavía no habéis escrito una línea de HTML "de verdad" — eso empieza en la **UD2**, y se profundiza en formularios (UD3) y hojas de estilo (UD4-5). Lo poco que sabéis ahora (que es una aplicación de SGML, permisiva con los errores) es solo el contexto que necesitabais para entender por qué se comporta distinto a XML.

Sobre **XHTML** en concreto (que veréis con más detalle en la UD2): a día de hoy es prácticamente **teoría sin caso práctico real** — quedó en desuso hace años y ningún proyecto nuevo lo usa. Se explica porque es el ejemplo más claro de aplicar las reglas de "bien formado" de XML (ya vistas en el apartado 4.3) a HTML, no porque vayáis a necesitarlo en el trabajo.

- W3Schools: https://www.w3schools.com/
- HTML Living Standard (WHATWG): https://html.spec.whatwg.org/
