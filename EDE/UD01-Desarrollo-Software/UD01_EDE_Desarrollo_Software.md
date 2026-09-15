# UD01 — Desarrollo de software

**Módulo:** Entorns de Desenvolupament (EDE) — 1r DAW
**Docente:** Noel Marco Biendicho
**RA cubierto:** RA1 — *Reconoce los elementos y herramientas que intervienen en el desarrollo de un programa informático, analizando sus características y las fases en que actúan hasta llegar a su puesta en funcionamiento* (CA 1a-1f)

> ⚠️ **Nota de programación**: el CA 1g (metodologías ágiles de desarrollo de software) **no** se trabaja en esta unidad — está asignado a la UP6 (Gestión de proyectos informáticos), donde el alumnado ya conoce el ciclo de vida y las fases que se presentan aquí.

> 💡 **Nota de estudio**: esta unidad da el vocabulario y los conceptos que usarás durante todo el curso — cuando en UD2 instales un IDE o en UD3 hagas tu primer commit, estarás usando "herramientas de desarrollo" tal como se clasifican aquí. No hay apenas código; el objetivo es que sepas *de qué estamos hablando* antes de ponernos a programar.

---

## 1. El programa y los componentes del sistema (CA 1a)

### 1.1. Informática, software y programa

La **informática** es el tratamiento automático de la información mediante un dispositivo. Toda esa información se representa internamente en **binario** (secuencias de 0 y 1): la unidad mínima es el **bit**, y 8 bits forman un **byte**.

El **software** es la parte intangible de un sistema informático: el conjunto de instrucciones que le dicen al hardware qué hacer. Dentro del software conviene distinguir varios niveles:

| Término | Qué es | Ejemplo |
|---|---|---|
| **Programa** | Secuencia de instrucciones con una finalidad concreta, que devuelve un valor o realiza una función | Una función que suma dos números |
| **Librería** | Archivo que empaqueta programas ya escritos, reutilizables desde otro código | Un archivo `.dll`, un paquete `pip` |
| **Aplicación** | Uno o varios programas (con o sin librerías) orientados a una tarea del usuario final | Adobe Photoshop |
| **Suite** | Varias aplicaciones independientes distribuidas juntas | LibreOffice, MS Office |

⚠️ **Importante**: el sistema operativo no encaja en una sola de estas categorías — es, en la práctica, una suite de programas, librerías y aplicaciones que gestionan el resto del sistema.

### 1.2. Cómo un programa usa el hardware: memoria, procesador y periféricos

Cuando un programa se ejecuta, no lo hace en el vacío: necesita apoyarse en tres componentes del sistema.

```
   PERIFÉRICOS               MEMORIA (RAM)              PROCESADOR (CPU)
 (entrada / salida)      instrucciones + datos       ejecuta el programa
┌──────────────────┐    ┌──────────────────────┐    ┌───────────────────┐
│ teclado, ratón,   │───▶│  el programa se carga │◀──▶│ ciclo:            │
│ red, sensores...  │    │  aquí antes de        │    │  1. FETCH  (busca)│
│                   │◀───│  ejecutarse           │    │  2. DECODE (lee)  │
│ pantalla, disco,  │    │                       │    │  3. EXECUTE (hace)│
│ impresora...      │    └──────────────────────┘    └───────────────────┘
└──────────────────┘
```

- **Memoria (RAM)**: mientras un programa se ejecuta, tanto sus instrucciones como los datos que maneja viven en memoria principal. Al cerrarlo, ese contenido se pierde (es memoria *volátil*) — por eso los datos que queremos conservar hay que guardarlos en un periférico de almacenamiento (disco).
- **Procesador (CPU)**: ejecuta el programa repitiendo el llamado **ciclo de instrucción**: *fetch* (busca la siguiente instrucción en memoria), *decode* (la interpreta) y *execute* (la realiza, usando sus registros internos y la unidad aritmético-lógica).
- **Periféricos**: son la vía de entrada y salida del programa con el exterior. De **entrada** (teclado, ratón, red, sensores) el programa recibe datos; de **salida** (pantalla, impresora, altavoces) o de **almacenamiento** (disco, red) el programa devuelve o persiste resultados.

> 📡 **Por qué importa hoy**: cuando más adelante programemos, por ejemplo, un dashboard de finanzas personales, esta relación se ve literalmente: los datos que el usuario teclea entran por un periférico de entrada, se guardan temporalmente en variables (memoria RAM) mientras el programa calcula, y el resultado final se persiste en una base de datos en disco — sin este esquema, "guardar" y "mostrar en pantalla" son solo palabras sueltas.

### 1.3. Programar vs. desarrollar software

**Programar** es, en esencia, codificar instrucciones para que un dispositivo se comporte de una manera concreta. **Desarrollar software** es bastante más: incluye analizar, diseñar, probar, documentar y mantener, además de codificar. Por eso en este módulo hablaremos de **desarrollador** en vez de "programador" — la codificación es solo una de las fases (lo vemos en el punto 2).

---

## 2. El ciclo de vida del software: fases del desarrollo (CA 1b)

Todo desarrollo de software recorre, con más o menos rigor, un conjunto de etapas conocido como **ciclo de vida del software**. El modelo más clásico —y el que usaremos como referencia— es el **modelo en cascada**: cada fase se apoya en la anterior y genera una documentación propia.

| Fase | Qué ocurre | Documentación que genera |
|---|---|---|
| **1. Análisis** | Se recogen los requisitos del cliente (entrevista, comunicación **bilateral** — el cliente no siempre sabe expresar lo que necesita) | ERS (Especificación de Requisitos del Sistema), diagrama E/R o de clases |
| **2. Diseño** | Se define el funcionamiento global del sistema, sus recursos y estructuras de datos, sin entrar en el código | Diagramas de casos de uso / secuencia, **cuaderno de carga** |
| **3. Codificación** | Se traduce el cuaderno de carga al lenguaje de programación elegido | El propio código fuente comentado |
| **4. Pruebas** | Se comprueba que el software no tiene errores y hace lo que debe (idealmente, las hace alguien distinto de quien programó) | Registro de pruebas de caja blanca / caja negra |
| **5. Documentación** | Se elabora el manual de usuario final (distinto de la documentación técnica generada en las fases anteriores) | Manual de usuario |
| **6. Explotación** | El software se instala en el entorno real; si sustituye a una versión anterior, ambas pueden convivir durante la transición | Informe de instalación/puesta en marcha |
| **7. Mantenimiento** | Se corrigen errores que aparecen en producción y se añaden ampliaciones — si hay ampliación, suele haber que revisar fases anteriores | Registro de incidencias y cambios |

> 🕰️ **No es la única forma de organizarlo**: el modelo en cascada es lineal y rígido — si en la fase de Pruebas aparece un fallo de diseño, hay que volver atrás. Existen otros modelos de ciclo de vida (iterativo, incremental, en espiral...) que veremos en la UP6 junto con las **metodologías ágiles** (CA 1g), pensadas precisamente para adaptarse mejor al cambio.

**¿Quién interviene en cada fase?** Los roles no son compartimentos estancos — la misma persona puede cubrir varios:

| Rol | Fases en las que participa |
|---|---|
| Analista de sistemas | Análisis |
| Diseñador de software | Diseño |
| Analista programador ("desarrollador") | Diseño y Codificación |
| Programador | Codificación |
| Arquitecto de software | Análisis, Diseño, Documentación y Explotación |

---

## 3. Código fuente, código objeto y código ejecutable (CA 1c)

Un dispositivo solo entiende **código máquina** (binario). Como nadie programa directamente en binario, escribimos en un lenguaje de programación y dejamos que unas herramientas lo traduzcan:

```
código fuente  ──(compilador)──▶  código objeto  ──(+ librerías, enlazador)──▶  código ejecutable
   (.java)                         (.class)                                        (específico del SO)
```

- **Código fuente**: el conjunto de instrucciones que escribe el desarrollador, en un fichero de texto (`.java`, `.py`, `.c`...).
- **Código objeto** (o *código intermedio*, o *bytecode*): resultado de compilar el código fuente. Todavía no es directamente ejecutable por el hardware — en Java, por ejemplo, es el fichero `.class`.
- **Código ejecutable**: se obtiene al añadir al código objeto las funciones de librerías usadas y las particularidades del sistema operativo de destino (proceso normalmente realizado por un *enlazador*). Es lo que el dispositivo interpreta directamente.

⚠️ Un mismo código fuente puede necesitar generar **ejecutables distintos** según el sistema operativo destino (Windows, Linux, macOS), aunque el código fuente no cambie.

---

## 4. Código intermedio y máquinas virtuales (CA 1d)

Según cómo se trate el código, un ejecutable puede ser:

- **Portable**: funciona en varias plataformas sin recompilar (p. ej., un `.jar` de Java, porque usa *bytecode* no ligado a un procesador concreto).
- **No portable**: pensado para una plataforma concreta (p. ej., un ejecutable compilado en C para Windows).

Algunos lenguajes, como Java, resuelven la portabilidad con una **máquina virtual**: una aplicación que emula un sistema (o parte de él) dentro del sistema operativo real.

| Tipo de máquina virtual | Qué hace | Ejemplos |
|---|---|---|
| **De sistema** | Simula un ordenador completo (arquitectura + SO) dentro de otro | VirtualBox, VMware |
| **De proceso** | Ejecuta el código intermedio (bytecode) de un lenguaje concreto, independizándolo del hardware real | JVM (Java Virtual Machine) |

La **JVM** interpreta y ejecuta el *bytecode* que genera el compilador de Java (los ficheros `.class`), traduciéndolo sobre la marcha a las instrucciones del hardware concreto donde se ejecuta. Por eso el mismo `.class` corre en Windows, Linux o macOS sin recompilar, siempre que haya una JVM instalada: "*write once, run anywhere*".

> 📡 **Sigue vigente**: el modelo de máquina virtual de proceso no es exclusivo de Java — Python (con su intérprete y bytecode `.pyc`) y .NET (CLR) funcionan sobre una idea muy similar.

---

## 5. Clasificación de los lenguajes de programación (CA 1e)

No hay una única forma de clasificar los lenguajes; estas son las más habituales.

**Según cómo se ejecutan:**

| Tipo | Cómo funciona | Ejemplos | Dónde se usan más |
|---|---|---|---|
| **Compilados** | El código fuente se traduce entero, de una vez, a un ejecutable | C, C++, C#, Pascal | Software de escritorio (ejecución rápida, ficheros más pesados) |
| **Interpretados** | Un intérprete traduce y ejecuta el código línea a línea, sin generar ejecutable propio | Python, PHP, JavaScript | Entornos web y scripting (menos recursos, más lentos) |
| **Híbridos / virtuales** | Se compilan a código intermedio (bytecode), que luego interpreta una máquina virtual | Java, C# (en parte) | Aplicaciones que deben correr en varias plataformas sin recompilar |

**Según el nivel de abstracción** (cuánto se parecen al lenguaje natural frente al lenguaje máquina):

| Nivel | Característica | Ejemplos |
|---|---|---|
| **Bajo nivel** | Instrucciones muy cercanas al hardware, acceso directo a registros | Ensamblador |
| **Medio nivel** | Permite acceder a memoria y registros, pero con una sintaxis más legible | C |
| **Alto nivel** | Sintaxis cercana al lenguaje humano, abstrae los detalles del hardware | Python, Java, PHP |

**Según el paradigma de programación** (la forma de plantear la solución):

| Paradigma | Idea central | Ejemplo de lenguaje |
|---|---|---|
| **Imperativo / procedimental** | Se describe *paso a paso* cómo hacer algo | C |
| **Orientado a objetos** | Se modela el problema como objetos que interactúan | Java |
| **Funcional** | Se programa componiendo funciones, evitando el estado mutable | Haskell (y, parcialmente, JavaScript o Python) |
| **Declarativo** | Se describe *qué* se quiere obtener, no *cómo* obtenerlo | SQL |

Por último, en el contexto de aplicaciones web es habitual distinguir entre **front-end** (la parte visible, que corre en el navegador del usuario: HTML, CSS, JavaScript) y **back-end** (la lógica no visible, que corre en un servidor: Java, Python, PHP, SQL...).

> 📡 **Actualidad**: la popularidad de los lenguajes cambia con el tiempo. El **índice TIOBE** (`tiobe.com/tiobe-index`) es una de las referencias más consultadas para ver qué lenguajes están en auge o en declive — pero es una fotografía mensual, no una verdad fija: conviene consultarlo actualizado en vez de memorizar un ranking.

---

## 6. Herramientas del desarrollo de software (CA 1f)

Además del lenguaje, un desarrollador se apoya en herramientas que dan soporte a cada fase del ciclo de vida. Esta unidad solo las **clasifica**; profundizaremos en varias de ellas en unidades posteriores.

| Categoría | Funcionalidad que ofrece | Ejemplos | Se trabaja en detalle en |
|---|---|---|---|
| Editor de código / IDE | Escribir, navegar y depurar código con ayuda (autocompletado, resaltado de sintaxis...) | Visual Studio Code, Eclipse, IntelliJ | UP2 |
| Compilador / intérprete | Traducir código fuente a código objeto/ejecutable, o ejecutarlo línea a línea | `javac`/`java`, Python, GCC | UP1-UP2 |
| Control de versiones | Registrar el historial de cambios del código y permitir el trabajo en equipo | Git, GitHub | UP3 |
| Depuración y pruebas | Ejecutar el programa paso a paso, inspeccionar variables, automatizar comprobaciones | Debugger del IDE, JUnit | UP5 |
| Gestión de dependencias / build | Instalar librerías externas y automatizar la construcción del proyecto | `pip`, Maven, npm | UP2 |
| Análisis y documentación de código | Revisar la calidad del código y generar documentación a partir de él | SonarQube, Javadoc | UP7 |

> 💡 Ejemplo integrador: si más adelante desarrollamos un **dashboard de finanzas personales** en Python con una base de datos SQLite, usaríamos como mínimo: un IDE (VS Code) para escribir el código, Git/GitHub para el control de versiones, `pip` para instalar librerías (por ejemplo, para generar gráficos) y `pytest` para probar que los cálculos son correctos. Cada una de esas herramientas cubre una funcionalidad distinta dentro del desarrollo.

---

## 🧪 Ejercicios prácticos

**Ejercicio 1 — Vocabulario técnico correcto**
Corrige esta frase para que sea técnicamente precisa (identifica los 4 términos mal usados y explica por qué):

> "En mi ordenador tengo programas como LibreOffice Writer o Adobe Photoshop, que en esencia envían órdenes al procesador. El primero forma parte de una librería llamada LibreOffice, y el segundo usa internamente varias suites donde tiene guardadas funciones de diseño gráfico. Ambos han sido codificados por programadores expertos."

**Ejercicio 2 — Memoria, procesador y periféricos en un caso real**
Piensa en una aplicación sencilla que pida un nombre por teclado y muestre en pantalla un saludo. Identifica, para ese programa: qué periférico interviene en la entrada, qué periférico interviene en la salida, y en qué momento el dato "nombre" pasa por la memoria RAM y en qué momento el procesador ejecuta una instrucción.

**Ejercicio 3 — Fases del ciclo de vida aplicadas**
Un cliente te pide una aplicación de gestión de gastos personales. Redacta brevemente (2-3 líneas por fase) qué harías en cada una de las 7 fases del ciclo de vida para ese proyecto concreto.

**Ejercicio 4 — De código fuente a ejecutable**
Instala un JDK, escribe un programa `HolaMundo.java` que imprima tu nombre, y compílalo con `javac HolaMundo.java`. Localiza el fichero `.class` generado y ejecútalo con `java HolaMundo`. Explica, con tus palabras, qué representa cada uno de los tres ficheros/momentos (fuente, objeto, ejecución) en este proceso.

**Ejercicio 5 — Clasifica estos lenguajes**
Para Python, Java, C y JavaScript, indica: tipo de ejecución (compilado/interpretado/híbrido), nivel de abstracción y paradigma principal. Justifica cada respuesta en una frase.

**Ejercicio 6 — Herramientas para un proyecto**
Para el proyecto de "dashboard de finanzas personales" del punto 6, indica qué herramienta de cada categoría de la tabla usarías y por qué, aunque hoy no sepas usarlas todavía (búscalo si hace falta).

---

## 🎯 Reto de clase

Elige una aplicación que uses habitualmente en el móvil (una app de mensajería, de banca, de transporte...) y elabora una ficha de una página que incluya:

1. Una hipótesis razonada sobre qué lenguaje(s) de programación se usaron para su parte visible y para su lógica interna (front-end/back-end), con al menos un argumento técnico de por qué.
2. Una hipótesis sobre si el ejecutable que corre en tu móvil es compilado, interpretado o híbrido (justifícalo con lo que sepas de Android/iOS y las máquinas virtuales vistas en el punto 4).
3. Un esquema de las 7 fases del ciclo de vida aplicado a esa app: qué requisitos crees que se recogieron en el Análisis, y qué tipo de Mantenimiento recibe (busca su historial de actualizaciones en la tienda de aplicaciones como pista).

*Variación evaluable*: se puede pedir por parejas, comparando dos apps de la misma categoría (por ejemplo, dos apps bancarias) para que el alumnado contraste hipótesis distintas.

---

## 📚 Para saber más (opcional, no evaluable)

- Índice TIOBE (popularidad de lenguajes, actualizado mensualmente): https://www.tiobe.com/tiobe-index/
- Documentación oficial de la JVM: https://docs.oracle.com/javase/specs/
