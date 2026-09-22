<div style="text-align: center;">

<img src="data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCA0MDAgNDAwIiB3aWR0aD0iMTgwIiBoZWlnaHQ9IjE4MCI+CiAgPGNpcmNsZSBjeD0iMjAwIiBjeT0iMjAwIiByPSIxNzAiIGZpbGw9IiNGMEZERkEiLz4KICA8Y2lyY2xlIGN4PSIyMDAiIGN5PSIyMDAiIHI9IjE3MCIgZmlsbD0ibm9uZSIgc3Ryb2tlPSIjOTlGNkU0IiBzdHJva2Utd2lkdGg9IjIiLz4KICA8dGV4dCB4PSIyMDAiIHk9IjI0OCIgZm9udC1mYW1pbHk9IidDb3VyaWVyIE5ldycsIENvdXJpZXIsIG1vbm9zcGFjZSIgZm9udC1zaXplPSIxNTAiIGZvbnQtd2VpZ2h0PSI3MDAiIGZpbGw9IiMwRjc2NkUiIHRleHQtYW5jaG9yPSJtaWRkbGUiPiZndDtfPC90ZXh0Pgo8L3N2Zz4K" width="180" alt="Logo EDE"/>

<h1>Unidad 2</h1>
<h2>Entornos de desarrollo</h2>

<p>
<strong>Módulo:</strong> Entorns de Desenvolupament (EDE)<br>
<strong>Ciclo formativo:</strong> 1º DAW (Desarrollo de Aplicaciones Web)<br>
<strong>Curso:</strong> 2026-2027
</p>

<p>
<strong>Docente:</strong> Noel Marco Biendicho<br>
<strong>Centro:</strong> IES Sant Vicent Ferrer — Algemesí
</p>

</div>

<div style="page-break-after: always;"></div>

## Índice

1. El entorno de desarrollo: instalación y primeros pasos (CA 2a)
2. Personalización, automatización y actualización del entorno (CA 2b, 2c, 2d)
3. Generación de ejecutables en diferentes entornos (CA 2e, 2f)
4. Comparación de entornos de desarrollo (CA 2g)
5. Reto de clase
6. Resumen de la unidad
7. Para saber más

<div style="page-break-after: always;"></div>

**RA cubierto:** RA2 (CA 2a-2g) — Evalúa entornos integrados de desarrollo, analizando sus características para editar código fuente y generar ejecutables.

> 💡 **Nota de estudio**: en UD1 clasificamos las herramientas de desarrollo por encima (IDE, compilador, control de versiones...); esta unidad se mete de lleno en una sola de esas categorías — el IDE — para instalarlo, configurarlo a fondo y compararlo con alternativas. VS Codium, que ya usas desde UD1, deja de ser "la carpeta donde escribo código" y pasa a ser un entorno que sabes instalar, personalizar y evaluar con criterio.

> 💻 **Cómo trabajar los ejercicios de esta unidad**: sigue usando tu carpeta `UD02_TuNombre` en VS Codium. Cuando un ejercicio pida instalar, configurar o comparar, documenta el proceso en un archivo Markdown (`ejercicioN.md`) — capturas de pantalla incluidas si tu profesor lo pide — en vez de solo "hacerlo y ya".

## 🎯 Conceptos clave

Al terminar esta unidad sabrás:
- Instalar, personalizar y actualizar un entorno de desarrollo, distinguiendo software propietario de software libre.
- Generar ejecutables a partir del mismo código fuente en distintos lenguajes y en distintos entornos, dentro y fuera de tu equipo.
- Comparar entornos de desarrollo con criterio técnico (no solo "cuál me gusta más"), identificando qué tienen en común y qué los distingue.

---

## 1. El entorno de desarrollo: instalación y primeros pasos (CA 2a)

### 1.1. Qué aporta un IDE (repaso rápido de UD1)

En UD1 (punto 7.1) ya vimos que un **IDE** (*Integrated Development Environment*) añade sobre un editor de texto simple: autocompletado, resaltado de sintaxis, detección de errores mientras escribes y depuración incorporada. Esta unidad no repite esa teoría — la pone en práctica: instalar, configurar y sacarle partido a uno de verdad.

| Sin IDE (editor de texto simple) | Con IDE |
|---|---|
| Sin avisos hasta ejecutar el programa | Errores marcados mientras escribes |
| Copiar/pegar nombres de variables y funciones | Autocompletado, "ir a la definición" |
| Ejecutar y depurar desde una terminal aparte | Ejecución y depuración integradas |
| Cero ayuda con el formato del código | Formateo automático, resaltado de sintaxis |

### 1.2. Software propietario y software libre: el mismo IDE, dos caminos

**Propietario** significa que el fabricante controla el código fuente y las condiciones de uso (aunque el programa sea gratuito); **libre** significa que el código es público y cualquiera puede modificarlo y redistribuirlo, bajo una licencia que lo garantiza. No son sinónimos de "de pago" y "gratis": hay software propietario gratuito, y software libre que se vende como servicio.

El ejemplo más cercano lo tienes ya instalado en tu equipo:

| | **Visual Studio Code** | **VS Codium** |
|---|---|---|
| Código fuente | El mismo (proyecto `code-oss`, código abierto) | El mismo (proyecto `code-oss`, código abierto) |
| Compilación final | La hace Microsoft, y añade telemetría y branding propietario antes de distribuirla | La hace la comunidad, sin telemetría ni marcas de Microsoft |
| Licencia del binario final | Propietaria (EULA de Microsoft) | Libre (MIT) |
| Extensiones desde Marketplace de Microsoft | Sí | No directamente (usa Open VSX, un catálogo alternativo) |

⚠️ **El caso más instructivo posible**: no son "dos programas distintos que compiten" — es el mismo código fuente, compilado de dos formas distintas, con dos licencias distintas como resultado. Por eso llevas desde UD1 usando la versión libre sin perder ninguna función esencial.

**🧪 Ejercicio 1 — Verifica y documenta tu instalación**
Abre VS Codium y comprueba la versión instalada (`Ayuda → Acerca de`, o `Help → About`). En `ejercicio1.md`, dentro de tu carpeta `UD02`, indica: (a) la versión exacta que tienes; (b) si tu instalación usa el Marketplace de Microsoft o Open VSX para las extensiones (compruébalo abriendo la pestaña de Extensiones y mirando de dónde se instalan); (c) con tus palabras, por qué VS Code y VS Codium comparten código pero no licencia.

### 1.3. Uso básico y edición de programas

Antes de personalizar nada, conviene dominar lo básico: crear y organizar una **carpeta de proyecto** (*workspace*), moverse entre archivos con el explorador lateral y con el atajo de "ir a archivo" (`Ctrl+P`), y usar la terminal integrada sin salir del IDE — todo esto ya lo vienes haciendo desde UD1 sin nombrarlo como tal.

Lo nuevo en esta unidad es mirarlo desde el otro lado: no solo usar el IDE, sino **decidir con criterio** cómo lo instalas, lo configuras y lo comparas — que es exactamente lo que viene a continuación.

> 🧯 **Plan B si la instalación falla en clase**: si tu equipo no tiene VS Codium instalado y no puedes instalarlo (falta de permisos, sin conexión), usa **vscode.dev** (la versión de VS Code que corre entera en el navegador, sin instalar nada) para seguir el resto de la unidad — es el mismo editor, con menos funciones de sistema (no ejecuta código directamente), pero suficiente para los ejercicios de personalización. Si dispones de la VM portátil del ciclo, VS Codium ya viene preinstalado ahí.

---

## 2. Personalización, automatización y actualización del entorno (CA 2b, 2c, 2d)

### 2.1. Módulos y extensiones

Un IDE recién instalado hace poco más que un editor de texto avanzado — su verdadero potencial llega con **extensiones**: módulos que añaden soporte para un lenguaje, un formateador, un linter, temas visuales, o integración con herramientas externas.

```
Extensiones que probablemente ya tienes activas desde UD1:
- Python (soporte de lenguaje, IntelliSense, depurador)
- Code Runner (ejecutar un archivo con un solo botón)
```

| Acción | Cómo se hace en VS Codium |
|---|---|
| Instalar una extensión | Panel de Extensiones (`Ctrl+Shift+X`) → buscar → Instalar |
| Ver qué tienes instalado | Mismo panel, pestaña "Instaladas" |
| Eliminar una extensión | Botón de engranaje sobre la extensión → Desinstalar |
| Deshabilitar sin desinstalar | Botón de engranaje → Deshabilitar (útil para aislar si una extensión da problemas) |

### 2.2. Personalización visual y de estilo de codificación

Más allá de las extensiones, el propio IDE se adapta a cómo trabajas:

- **Tema**: combinación de colores del editor (oscuro, claro, alto contraste). `Ctrl+K Ctrl+T` en VS Codium.
- **Estilo de codificación**: tamaño de la sangría (espacios vs tabulaciones), longitud de línea, formateo automático al guardar — configurable por lenguaje, no solo de forma global.
- **Atajos de teclado**: personalizables uno a uno o por perfiles completos (por ejemplo, imitando los atajos de otro editor).

```json
// settings.json — un fragmento típico de configuración personal
{
    "editor.tabSize": 4,
    "editor.formatOnSave": true,
    "workbench.colorTheme": "Default Dark Modern",
    "files.autoSave": "afterDelay"
}
```

> 📡 **Por qué importa hoy**: cuando trabajes en equipo (control de versiones, UP3), un estilo de codificación compartido entre el equipo evita que cada `commit` cambie cientos de líneas solo por diferencias de indentación — muchos proyectos reales fijan esta configuración en un archivo compartido (`.editorconfig`) para que no dependa de la configuración personal de cada desarrollador.

### 2.3. Automatización con tareas y fragmentos de código

Un IDE también automatiza lo repetitivo:

| Herramienta | Qué automatiza | Ejemplo |
|---|---|---|
| **Tareas** (*tasks*) | Ejecutar un comando o secuencia de comandos con un atajo, en vez de escribirlos a mano cada vez | Compilar y ejecutar con una sola acción |
| **Fragmentos** (*snippets*) | Insertar bloques de código repetitivos a partir de un atajo de texto | Escribir `for` + Tab genera la estructura completa de un bucle |
| **Extensiones de formateo** | Reordenar y limpiar el código automáticamente según unas reglas | Black (Python), Prettier (JavaScript) |

**🧪 Ejercicio 2 — Personaliza tu entorno**
En `ejercicio2.md`: (a) cambia el tema de color de tu VS Codium y anota cuál has elegido; (b) instala una extensión que no tuvieras (por ejemplo, un formateador para el lenguaje que más uses); (c) crea un fragmento de código propio (busca en la documentación de VS Codium "user snippets") para una estructura que repitas a menudo (por ejemplo, la cabecera de un script Python) y pega su definición JSON.

### 2.4. Actualización del propio entorno

El IDE y sus extensiones no son estáticos: reciben actualizaciones que corrigen errores, añaden funciones o parchean vulnerabilidades. Gestionar esto también forma parte de administrar tu entorno:

| Qué se actualiza | Dónde se gestiona en VS Codium |
|---|---|
| El propio editor | `Ayuda → Buscar actualizaciones` (o notificación automática al abrir) |
| Extensiones individuales | Panel de Extensiones — un punto azul indica que hay una versión nueva |
| Actualización automática | Configurable por extensión (`extensions.autoUpdate` en `settings.json`) |

⚠️ **Actualizar no siempre es gratis**: una extensión que se actualiza puede cambiar de comportamiento o dejar de ser compatible con una versión antigua del IDE — en un proyecto real en producción, muchos equipos fijan las versiones de sus herramientas (no solo de las librerías del proyecto) para evitar sorpresas justo antes de una entrega.

**🧪 Ejercicio 3 — Gestiona las actualizaciones**
En `ejercicio3.md`: comprueba si tu VS Codium tiene actualizaciones pendientes (del propio editor o de alguna extensión). Documenta qué encontraste y, si actualizas algo, qué cambió (nº de versión antes/después). Si no hay nada pendiente, explica dónde has comprobado que no lo hay y por qué desactivar la actualización automática de una extensión puede ser, a veces, una decisión razonada y no un descuido.

---

## 3. Generación de ejecutables en diferentes entornos (CA 2e, 2f)

En UD1 (punto 4) vimos qué es un ejecutable y cómo se obtiene. Ahora comprobamos algo distinto: **el mismo IDE puede generar ejecutables en varios lenguajes**, y **el mismo código fuente puede ejecutarse desde entornos completamente distintos**.

### 3.1. Un mismo entorno, distintos lenguajes

VS Codium no "sabe" ejecutar código por sí solo — delega en el compilador o intérprete de cada lenguaje (GCC, `javac`, el intérprete de Python...) que ya instalaste en UD1. Lo que aporta el IDE es una interfaz común para lanzarlos todos sin salir del editor.

```
UD01: gcc programa.c -o programa          (desde la terminal, a mano)
UD02: mismo comando, lanzado con un botón/atajo desde el IDE — misma herramienta, menos fricción
```

**🧪 Ejercicio 4 — Un mismo entorno, tres lenguajes**
Retoma (o vuelve a crear) un script sencillo en Python, uno en C y uno en Java (pueden ser los de UD1). Configura y usa, dentro de VS Codium, una forma de ejecutar cada uno con un solo botón o atajo (la extensión Code Runner, o una tarea propia). En `ejercicio4.md`, indica qué configuraste para cada lenguaje y qué tuvo que instalarse o ajustarse aparte del propio IDE para que funcionara.

### 3.2. Un mismo código, distintos entornos

A la inversa: el mismo archivo `.py` puede ejecutarse desde VS Codium en tu equipo, desde una terminal sin IDE, o desde un entorno que no está ni instalado en tu máquina — un **IDE online**, que ejecuta el código en un servidor remoto y te devuelve el resultado en el navegador.

| Entorno | Dónde se ejecuta el código | Necesita instalación |
|---|---|---|
| VS Codium (local) | En tu equipo | Sí — el IDE y el intérprete/compilador |
| Terminal, sin IDE | En tu equipo | Solo el intérprete/compilador, no el IDE |
| IDE online (p. ej. vscode.dev, replit.com) | En un servidor remoto | No — basta un navegador |

**🧪 Ejercicio 5 — El mismo script, tres formas de ejecutarlo**
Usa un script Python sencillo (puede ser el de la memoria/RAM de UD1, ejercicio 4). Ejecútalo: (a) desde VS Codium con el botón de ejecutar; (b) desde la terminal integrada, escribiendo tú mismo el comando (`python ejercicio4.py`); (c) pegando el mismo código en un IDE online (por ejemplo, replit.com o vscode.dev) y ejecutándolo ahí. En `ejercicio5.md`, indica qué cambia entre los tres (qué necesitaste tener instalado en cada caso, y qué tan rápido fue arrancar cada uno).

---

## 4. Comparación de entornos de desarrollo (CA 2g)

Evaluar un entorno no es decir "me gusta" o "no me gusta" — es identificar, con criterio, qué características comparte con otros y cuáles son propias de cada uno.

| Característica | VS Codium (local) | IDE online (vscode.dev / replit.com) |
|---|---|---|
| Instalación | Necesaria, una vez | Ninguna — solo un navegador |
| Funciona sin conexión a internet | Sí | No (o muy limitado) |
| Rendimiento con proyectos grandes | Depende del equipo, normalmente mejor | Depende del servidor remoto y de tu conexión |
| Extensiones disponibles | Catálogo completo (Open VSX / Marketplace) | Habitualmente más limitado |
| Acceso desde cualquier equipo sin configurar nada | No (hay que instalarlo primero) | Sí |
| Ejecuta código directamente | Sí, con el compilador/intérprete instalado | Depende del servicio — muchos sí lo permiten |

> 📡 **Por qué importa hoy**: cuando más adelante trabajes en el **dashboard de finanzas personales** con control de versiones (UP3), es habitual alternar entre tu entorno local (para el día a día) y un entorno online (para revisar o hacer un cambio rápido desde un equipo que no es el tuyo, sin instalar nada). Saber qué se gana y qué se pierde al cambiar de entorno es, literalmente, lo que evalúa este RA.

**🧪 Ejercicio 6 — Ficha comparativa de dos entornos**
En `ejercicio6.md`, completa una tabla Markdown (como la anterior, pero con tus propias columnas) comparando VS Codium con el IDE online que hayas probado en el ejercicio 5. Añade una conclusión de 2-3 líneas: ¿en qué situación usarías cada uno?

---

## 🎯 Reto de clase

Vas a evaluar un tercer entorno de desarrollo — uno que no hayas usado en los ejercicios anteriores — aplicado al proyecto del **dashboard de finanzas personales**. Puede ser un IDE distinto instalado localmente (por ejemplo, Thonny, PyCharm Community, o cualquier otro que tengas acceso a instalar) o un segundo IDE online distinto al del ejercicio 5.

En VS Codium, crea `repte.md` dentro de tu carpeta `UD02` con una ficha que incluya:

1. **Instalación** (CA 2a): ¿es propietario o libre? ¿Qué tuviste que hacer para tenerlo disponible (instalar, o simplemente abrir una web)?
2. **Personalización** (CA 2b, 2c, 2d): ¿qué se puede personalizar (temas, extensiones, atajos)? ¿Cómo se gestionan sus actualizaciones?
3. **Generación de ejecutables** (CA 2e, 2f): prueba a ejecutar en él el mismo script Python que usaste en el ejercicio 5. ¿Funciona igual? ¿Qué tuviste que ajustar?
4. **Comparación final** (CA 2g): una tabla comparando este tercer entorno con VS Codium — al menos 4 características.

**Plantilla orientativa para `repte.md`:**

```markdown
# Reto — [nombre del entorno evaluado]

## 1. Instalación
- ¿Propietario o libre?: ...
- Qué tuviste que hacer: ...

## 2. Personalización
- Qué se puede personalizar: ...
- Cómo se actualiza: ...

## 3. Generación de ejecutables
- ¿Funcionó el mismo script?: ...
- Qué tuviste que ajustar: ...

## 4. Comparación con VS Codium
| Característica | VS Codium | [entorno evaluado] |
|---|---|---|
| ... | ... | ... |
```

*Variación evaluable*: se puede pedir que cada alumno evalúe un entorno distinto y luego se pongan en común las fichas en clase, construyendo entre todos una comparativa más amplia que la de cualquier ficha individual.

---

<div style="page-break-after: always;"></div>

## Resumen de la unidad

**1. El entorno de desarrollo: instalación y primeros pasos** Un IDE añade sobre un editor de texto simple autocompletado, detección de errores y depuración integrada. Software propietario y libre no equivalen a "de pago" y "gratis" — VS Code y VS Codium son el mismo código fuente compilado y licenciado de dos formas distintas, el ejemplo más directo de esta distinción.

**2. Personalización, automatización y actualización del entorno** Módulos y extensiones amplían lo que el IDE sabe hacer; temas, estilo de codificación y atajos lo adaptan a cómo trabajas; tareas y fragmentos automatizan lo repetitivo. El propio entorno también se actualiza — editor y extensiones por separado — y esa gestión forma parte de administrarlo, no es un detalle menor.

**3. Generación de ejecutables en diferentes entornos** El mismo IDE ejecuta distintos lenguajes delegando en el compilador o intérprete de cada uno; el mismo código fuente puede ejecutarse desde tu equipo, desde una terminal sin IDE, o desde un entorno online que no necesita instalación pero sí conexión.

**4. Comparación de entornos de desarrollo** Evaluar un entorno es identificar qué comparte con otros (instalación, personalización, ejecución) y qué le es propio (rendimiento, disponibilidad sin conexión, catálogo de extensiones) — la base con la que se construye el Reto de clase de esta unidad.

---

## 📚 Para saber más (opcional, no evaluable)

- Documentación oficial de VS Code: https://code.visualstudio.com/docs
- Open VSX Registry (catálogo de extensiones de VS Codium): https://open-vsx.org/
- vscode.dev (VS Code en el navegador, sin instalar nada): https://vscode.dev/

### 🧭 Por qué te va a servir esto de verdad

- En tu primer trabajo probablemente no elijas tú el IDE del equipo — pero sí lo vas a instalar, personalizar y mantener actualizado tú mismo, y saber hacerlo con criterio (y no solo "a base de tutoriales de YouTube") ahorra horas.
- Cuando cambies de equipo, de sistema operativo, o tengas que trabajar puntualmente desde un portátil que no es el tuyo, saber moverte entre un entorno local y uno online sin perder productividad es una habilidad que se nota.
- Justificar por qué tu equipo usa una herramienta libre en vez de una propietaria (o al revés) con argumentos técnicos, no solo de coste, es exactamente el tipo de decisión que un responsable técnico junior empieza a tomar pronto.
