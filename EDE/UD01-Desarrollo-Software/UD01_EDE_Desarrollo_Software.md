<div style="text-align: center;">

<img src="data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCA0MDAgNDAwIiB3aWR0aD0iMTgwIiBoZWlnaHQ9IjE4MCI+CiAgPGNpcmNsZSBjeD0iMjAwIiBjeT0iMjAwIiByPSIxNzAiIGZpbGw9IiNGMEZERkEiLz4KICA8Y2lyY2xlIGN4PSIyMDAiIGN5PSIyMDAiIHI9IjE3MCIgZmlsbD0ibm9uZSIgc3Ryb2tlPSIjOTlGNkU0IiBzdHJva2Utd2lkdGg9IjIiLz4KICA8dGV4dCB4PSIyMDAiIHk9IjI0OCIgZm9udC1mYW1pbHk9IidDb3VyaWVyIE5ldycsIENvdXJpZXIsIG1vbm9zcGFjZSIgZm9udC1zaXplPSIxNTAiIGZvbnQtd2VpZ2h0PSI3MDAiIGZpbGw9IiMwRjc2NkUiIHRleHQtYW5jaG9yPSJtaWRkbGUiPiZndDtfPC90ZXh0Pgo8L3N2Zz4K" width="180" alt="Logo EDE"/>

<h1>Unidad 1</h1>
<h2>Desarrollo de software</h2>

<p>
<strong>Módulo:</strong> Entorns de Desenvolupament (EDE)<br>
<strong>Ciclo formativo:</strong> 1r DAW (Desarrollo de Aplicaciones Web)<br>
<strong>Curso:</strong> 2026-2027
</p>

<p>
<strong>Docente:</strong> Noel Marco Biendicho<br>
<strong>Centro:</strong> IES Sant Vicent Ferrer — Algemesí
</p>

</div>

<div style="page-break-after: always;"></div>

## Índice

1. El programa y los componentes del sistema (CA 1a)
2. El ciclo de vida del software: el modelo clásico (CA 1b)
3. Metodologías ágiles de desarrollo (CA 1g)
4. Código fuente, código objeto y código ejecutable (CA 1c)
5. Código intermedio y máquinas virtuales (CA 1d)
6. Clasificación de los lenguajes de programación (CA 1e)
7. Herramientas del desarrollo de software (CA 1f)
8. Reto de clase
9. Resumen de la unidad
10. Para saber más

<div style="page-break-after: always;"></div>

**RA cubierto:** RA1 (CA 1a-1g) — Reconoce los elementos y herramientas que intervienen en el desarrollo de un programa informático, analizando sus características y las fases en que actúan hasta llegar a su puesta en funcionamiento.

> 💡 **Nota de estudio**: esta unidad da el vocabulario y los conceptos que usarás durante todo el curso — cuando en UD2 instales un IDE o en UD3 hagas tu primer commit, estarás usando "herramientas de desarrollo" tal como se clasifican aquí.

> 💻 **Cómo trabajar los ejercicios de esta unidad**: crea en VS Codium una carpeta `UD01_TuNombre` — la iremos usando en todos los ejercicios de la unidad. Cuando un ejercicio pida código, créalo como archivo (`.py`, `.java`, `.c`...) dentro de esa carpeta y ejecútalo desde la terminal integrada de VS Codium (`Terminal → Nueva terminal`). Cuando pida razonar, clasificar o redactar, escribe la respuesta en un archivo Markdown (`ejercicioN.md`) dentro de la misma carpeta, en vez de en papel. Así, desde el primer día, trabajas dentro del editor que usarás durante todo el ciclo — instalarlo y configurarlo a fondo (y compararlo con otros IDEs) se ve en la UP2; aquí simplemente le vamos cogiendo la mano.

> 🐍 **Por qué a veces cambiamos de lenguaje**: en esta unidad, Python es el lenguaje de trabajo habitual para los ejercicios (el mismo que usarás en Programación). Cuando algún ejercicio use Java, C o SQL en su lugar, es porque ese lenguaje concreto es quien mejor ilustra el concepto de ese punto (compilación nativa, código intermedio y máquina virtual, paradigma declarativo) — no hace falta que aprendas su sintaxis a fondo, solo que sigas el ejemplo paso a paso y entiendas la idea que demuestra.

## 🎯 Conceptos clave

Al terminar esta unidad sabrás:
- Distinguir programa, software (por forma y por función) y explicar cómo interactúan memoria, procesador y periféricos cuando un programa se ejecuta.
- Reconocer las fases del ciclo de vida del software (modelo clásico en cascada) y cuándo conviene aplicar en su lugar una metodología ágil (Scrum, Kanban).
- Diferenciar código fuente, objeto, intermedio y ejecutable, y clasificar lenguajes de programación y herramientas de desarrollo según la fase a la que dan soporte.

---

## 1. El programa y los componentes del sistema (CA 1a)

### 1.1. Informática, software y programa

La **informática** es el tratamiento automático de la información mediante un dispositivo. Toda esa información se representa internamente en **binario** (secuencias de 0 y 1): la unidad mínima es el **bit**, y 8 bits forman un **byte**.

Estas unidades reaparecen todo el curso — el tamaño de un archivo, la capacidad de una base de datos, cuánto ocupa una imagen que subes a un dashboard — así que conviene tenerlas claras desde ya:

| Unidad | Equivale a |
|---|---|
| 1 byte | 8 bits |
| 1 KB (kilobyte) | 1024 bytes |
| 1 MB (megabyte) | 1024 KB |
| 1 GB (gigabyte) | 1024 MB |

> 📡 **Cambiando activamente**: formalmente, 1 KB (kilobyte, sistema internacional) son 1000 bytes, y es el **KiB** (kibibyte) quien vale 1024 — la distinción existe desde 1998 (norma IEC 80000-13), pero casi nadie la respeta fuera de la documentación técnica más formal. Por eso un disco anunciado como "1 TB" muestra menos espacio del esperado en tu sistema operativo: el fabricante cuenta en base 1000, el sistema operativo en base 1024. En esta unidad, como en la mayoría de contextos de memoria RAM, seguimos la convención más habitual (1024) por simplicidad.

**🧪 Ejercicio 1 — Unidades de información con un caso real**
Un dashboard de finanzas personales guarda cada transacción como una fila de unos 200 bytes en una base de datos. En VS Codium, crea `ejercicio1.py` dentro de tu carpeta `UD01` y escribe un script que calcule y muestre por terminal (con `print`): (a) cuántos KB ocupará la base de datos de un usuario que registra 15 transacciones al día durante un año; (b) cuántos MB ocuparía si la aplicación tuviera 10.000 usuarios haciendo lo mismo. Ejecuta el script desde la terminal integrada (`python ejercicio1.py`) y añade, como comentario al final del archivo, si te sorprende el resultado y por qué.

El **software** es la parte intangible de un sistema informático: el conjunto de instrucciones que le dicen al hardware qué hacer. Dentro del software conviene distinguir varios niveles:

| Término | Qué es | Ejemplo |
|---|---|---|
| **Programa** | Conjunto de instrucciones ejecutables que realizan una tarea determinada | Una función que suma dos números (una pieza de código; no es todavía, por sí sola, una aplicación) |
| **Librería** | Archivo que empaqueta programas ya escritos, reutilizables desde otro código | Un archivo `.dll`, un paquete `pip` |
| **Aplicación** | Uno o varios programas (con o sin librerías) orientados a una tarea del usuario final | Adobe Photoshop |
| **Suite** | Varias aplicaciones independientes distribuidas juntas | LibreOffice, MS Office |

⚠️ **Importante**: el sistema operativo no encaja en una sola de estas categorías — es, en la práctica, una suite de programas, librerías y aplicaciones que gestionan el resto del sistema.

**🧪 Ejercicio 2 — Vocabulario técnico correcto**
Corrige esta frase para que sea técnicamente precisa (identifica los 4 términos mal usados y explica por qué). Escribe tu respuesta en `ejercicio2.md`, dentro de tu carpeta `UD01`:

> "En mi ordenador tengo programas como LibreOffice Writer o Adobe Photoshop, que en esencia envían órdenes al procesador. El primero forma parte de una librería llamada LibreOffice, y el segundo usa internamente varias suites donde tiene guardadas funciones de diseño gráfico. Ambos han sido codificados por programadores expertos."

**Otro eje de clasificación: software de sistema vs. software de aplicación.** La tabla anterior distingue *qué forma tiene* el software (programa/librería/aplicación/suite); esta otra distingue *para qué sirve*, y es igual de necesaria — un controlador, por ejemplo, es una librería (por su forma) que pertenece al software de sistema (por su función):

| Tipo | Función | Ejemplos |
|---|---|---|
| **Software de sistema** | Gestiona el hardware y da la base sobre la que corre todo lo demás | Sistema operativo, controladores (*drivers*), firmware (BIOS/UEFI), utilidades del sistema |
| **Software de aplicación** | Resuelve tareas concretas del usuario final, apoyándose en el software de sistema | Navegador, editor de código, un dashboard que tú programes |

**🧪 Ejercicio 3 — Software de sistema o de aplicación**
Abre la terminal integrada de VS Codium y ejecuta `apt list --installed | less` (pulsa `q` para salir) para ver los paquetes instalados en tu LliureX — o el gestor de aplicaciones del móvil, si prefieres esa fuente. Elige 6: 3 que consideres software de sistema y 3 que consideres software de aplicación. En `ejercicio3.md`, para cada uno justifica en una frase por qué lo has clasificado así, y di además si por su forma es un programa, una librería, una aplicación o una suite.

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

**No toda la memoria es RAM.** La RAM es la que más se usa mientras el programa corre, pero conviene distinguirla de otros dos tipos:

| Tipo | ¿Volátil? | Qué guarda | Ejemplos |
|---|---|---|---|
| **RAM** | Sí (se pierde al apagar) | Instrucciones y datos del programa en ejecución | Memoria del ordenador |
| **ROM / firmware** | No | Instrucciones básicas de arranque, grabadas de fábrica | BIOS/UEFI |
| **Almacenamiento secundario** | No | Datos y programas de forma permanente | Disco duro, SSD, almacenamiento en red |

> 📡 **Vigente**: la mayoría de procesadores actuales incorporan además una memoria **caché**, mucho más rápida que la RAM pero muy pequeña, que guarda los datos e instrucciones de uso más frecuente para evitar viajes constantes a la RAM. Es una de las razones por las que dos CPU con la misma velocidad de reloj pueden rendir de forma muy distinta.

**Los periféricos tampoco son solo "entrada" o "salida".** Algunos dispositivos cumplen las dos funciones a la vez:

| Tipo | Función | Ejemplos |
|---|---|---|
| **Entrada** | El programa recibe datos del exterior | Teclado, ratón, micrófono |
| **Salida** | El programa envía resultados al exterior | Pantalla, altavoces, impresora |
| **Entrada/salida** | Cumple ambas funciones | Pantalla táctil, tarjeta de red, disco externo |

> 💡 **Actividad rápida (5 min)**: abre una terminal y ejecuta `htop` (instálalo antes con `sudo apt install htop` si no lo tienes; si no tienes permisos de administrador o conexión a internet, usa en su lugar el *Monitor del sistema* gráfico ya instalado en LliureX — la misma información, sin necesitar nada nuevo). Busca: ¿cuánta RAM está usando el navegador ahora mismo? ¿Qué proceso usa más CPU? Relaciona lo que ves con el ciclo fetch-decode-execute y con la volatilidad de la RAM — si fuerzas el cierre de un proceso sin guardar, ¿qué se pierde y por qué?

> 📡 **Por qué importa hoy**: cuando más adelante programemos, por ejemplo, un dashboard de finanzas personales, esta relación se ve literalmente: los datos que el usuario teclea entran por un periférico de entrada, se guardan temporalmente en variables (memoria RAM) mientras el programa calcula, y el resultado final se persiste en una base de datos en disco (almacenamiento secundario) — sin este esquema, "guardar" y "mostrar en pantalla" son solo palabras sueltas.

**🧪 Ejercicio 4 — Memoria, procesador y periféricos en un caso real**
En `ejercicio4.py`, escribe un programa que pida un nombre por teclado (`input()`) y muestre en pantalla un saludo (`print()`). Ejecútalo en la terminal integrada. Después, en `ejercicio4.md`, identifica sobre tu propio código: qué periférico interviene en la entrada, qué periférico interviene en la salida, y en qué línea el dato `nombre` pasa por la memoria RAM y en qué línea el procesador ejecuta cada instrucción.

### 1.3. Programar vs. desarrollar software

**Programar** es, en esencia, codificar instrucciones para que un dispositivo se comporte de una manera concreta. **Desarrollar software** es bastante más: incluye analizar, diseñar, probar, documentar y mantener, además de codificar. Por eso en este módulo hablaremos de **desarrollador** en vez de "programador" — la codificación es solo una de las fases (lo vemos en el punto 2).

**De la idea a la solución.** Incluso antes de llegar a las fases formales del punto 2, resolver cualquier problema de programación — por pequeño que sea — sigue en miniatura el mismo esqueleto:

1. **Entender el problema**: ¿qué se pide exactamente? (a menudo no está tan claro como parece — lo veremos en el punto 2, fase de Análisis)
2. **Diseñar una solución**: pensar el "cómo" en términos generales, sin escribir código todavía (a veces con pseudocódigo o un diagrama)
3. **Implementarla**: traducir esa solución a un lenguaje de programación concreto — esto es, estrictamente, "programar"
4. **Comprobarla**: verificar que funciona y que hace lo que debía

> 🕰️ Este proceso de 4 pasos es el mismo esqueleto, en miniatura, que el ciclo de vida del software completo que viene a continuación — análisis, diseño, codificación y pruebas no son ideas exclusivas de proyectos grandes: aparecen incluso al resolver un ejercicio pequeño.

---

## 2. El ciclo de vida del software: el modelo clásico (CA 1b)

Todo desarrollo de software recorre, con más o menos rigor, un conjunto de etapas conocido como **ciclo de vida del software**. El modelo más clásico —y el que usaremos como referencia para entender cada fase— es el **modelo en cascada**: cada fase se apoya en la anterior y genera una documentación propia, sin empezar la siguiente hasta cerrar la actual.

### 2.1. Análisis

Se recogen y documentan los requisitos del cliente. Es una comunicación **bilateral**: el cliente rara vez sabe expresar con precisión técnica lo que necesita, así que el analista tiene que indagar, no solo tomar nota. Las técnicas más habituales son la **entrevista**, el **cuestionario**, la **observación** del proceso actual y la revisión de documentación ya existente.

Los requisitos recogidos se dividen en dos tipos, y confundirlos es uno de los errores más comunes al empezar:

| Tipo | Qué describe | Ejemplo (dashboard de finanzas personales) |
|---|---|---|
| **Funcional** | Qué debe *hacer* el sistema — una acción o función concreta | "El usuario puede registrar un gasto indicando importe, fecha y categoría" |
| **No funcional** | Cómo debe *comportarse* el sistema al hacerlo — rendimiento, seguridad, usabilidad, disponibilidad... | "El listado de gastos debe cargar en menos de 2 segundos"; "los datos se cifran en tránsito" |

Todo esto se recoge en la **ERS (Especificación de Requisitos de Software)**, junto a un primer boceto de las entidades del sistema (diagrama E/R o de clases preliminar).

> 🕰️ **Qué sigue vigente y qué es ya historia**: durante décadas, el estándar de referencia para redactar una ERS fue **IEEE 830** (1998) — hoy retirado. Lo sustituye **ISO/IEC/IEEE 29148**, la norma vigente para especificar requisitos de software. El contenido de fondo (qué es un requisito funcional o no funcional) apenas ha cambiado; lo que cambia es el estándar formal que regula cómo documentarlo.

### 2.2. Diseño

| Diagrama UML | Qué muestra | En esta unidad |
|---|---|---|
| De casos de uso | Qué puede hacer cada tipo de usuario | Solo se reconoce que existe |
| De secuencia | En qué orden se comunican los componentes | Solo se reconoce que existe |
| De clases | Qué entidades existen, con sus atributos, métodos y relaciones | Se profundiza — se retoma en la UD4 |

Se define el funcionamiento del sistema **sin entrar todavía en el código**, a dos niveles:

- **Diseño arquitectónico**: la visión global — en qué módulos o capas se organiza el sistema y qué tecnología usa cada uno (por ejemplo, separar un dashboard de finanzas en una capa de interfaz, una de lógica de negocio y una de acceso a la base de datos).
- **Diseño detallado**: dentro de cada módulo, cómo se resuelve internamente — qué estructuras de datos y qué algoritmos usa cada función, todavía en diagramas o pseudocódigo, no en código real.

La notación estándar vigente para representar estos diseños es **UML** (*Unified Modeling Language*), con distintos diagramas según lo que se quiera mostrar: **de casos de uso** (qué puede hacer cada tipo de usuario), **de secuencia** (en qué orden se comunican los componentes) y **de clases** (qué entidades existen y cómo se relacionan) — este último modela la estructura del software: clases, atributos, métodos y relaciones entre objetos. En esta unidad basta con reconocer que existen y para qué sirve cada uno a grandes rasgos; profundizamos solo en el de clases (ver el aviso siguiente), que retomaréis con más detalle en la UD4 (análisis y diseño).

⚠️ **Un diagrama de clases no es lo mismo que el diseño de una base de datos.** Están relacionados — muchas veces las clases de un diagrama UML acaban inspirando las tablas de la base de datos, sobre todo si se usa un ORM — pero son dos modelos distintos, con reglas distintas: el diagrama de clases describe objetos con atributos y comportamiento; el diseño de una base de datos relacional usa su propio modelo, el **entidad-relación** (entidades, atributos, claves y cardinalidades), del que saldrían las tablas *Usuario*, *Transacción* y *Categoría* del dashboard de finanzas. No los confundas, aunque en un proyecto real acaben pareciéndose.

Todo este trabajo de diseño queda recogido en el **cuaderno de carga**: el documento técnico, consensuado con el cliente, que sirve de base para empezar a programar.

### 2.3. Codificación

Se traduce el cuaderno de carga al lenguaje de programación elegido. "Código fuente comentado" no significa solo añadir comentarios: implica seguir unas mínimas buenas prácticas para que cualquier otra persona (o tú mismo, meses después) pueda entenderlo:

- **Nombres significativos**: `calcularTotalGastos()` en vez de `f1()`.
- **Comentarios que expliquen el porqué**, no el qué — el código ya dice *qué* hace; el comentario debe aportar el motivo cuando no sea obvio.
- **Convenciones de estilo** consistentes, normalmente las que marca el propio lenguaje o el equipo (por ejemplo, PEP 8 en Python).

📡 **Por qué importa hoy**: es en esta fase donde entra de forma natural el **control de versiones** (Git) — cada avance de código se registra como un cambio con su propio historial. Lo veremos en detalle en la UP3, pero el hábito de comentar y nombrar bien empieza aquí, antes de tocar Git.

### 2.4. Pruebas

Se comprueba que el software no tiene errores y que hace lo que debía — idealmente lo prueba alguien distinto de quien programó, porque a quien ha escrito el código le cuesta más ver sus propios fallos (conoce el camino que "debería" funcionar y tiende a probar solo ese).

**Según cuánto se conoce del código:**

| Tipo | Cómo se prueba | Se fija en... |
|---|---|---|
| **Caja negra** | Sin mirar el código interno — solo se dan entradas y se comprueba si la salida es la esperada | La funcionalidad, desde fuera |
| **Caja blanca** | Conociendo la estructura interna del código | Se apoya en esa estructura para diseñar los casos de prueba — cobertura de sentencias, de condiciones o de caminos posibles, según el rigor que se necesite |

**Según qué parte del sistema se prueba** — de menor a mayor alcance:

| Nivel | Qué se prueba |
|---|---|
| Pruebas unitarias | Una función o módulo por separado, de forma aislada |
| Pruebas de integración | Varios módulos trabajando juntos |
| Pruebas de sistema | La aplicación completa, de principio a fin |
| Pruebas de aceptación | El propio cliente comprueba que se cumple lo pactado en el Análisis |

### 2.5. Documentación

Aquí se elabora la **documentación de usuario** — distinta de la documentación **técnica** que ya se ha ido generando en fases anteriores (ERS, cuaderno de carga, código comentado): manual de instalación, manual de uso, preguntas frecuentes...

> 📡 **Cambiando ahora mismo**: el manual de usuario extenso en PDF está perdiendo peso frente a la ayuda contextual integrada en la propia aplicación — tutoriales interactivos la primera vez que se abre, tooltips junto a cada opción, un asistente que guía paso a paso. La documentación no ha desaparecido: se ha movido dentro del propio producto.

### 2.6. Explotación

El software se instala en el entorno real de uso. Si sustituye a una versión anterior, existen varias estrategias de implantación, cada una con un compromiso distinto entre riesgo y velocidad:

| Estrategia | En qué consiste |
|---|---|
| **Directa** | Se sustituye la versión anterior de golpe, para todos los usuarios a la vez |
| **En paralelo** | Ambas versiones conviven durante un tiempo, para comparar y dar seguridad |
| **Piloto** | Se implanta primero en un grupo reducido de usuarios antes de generalizar |
| **Por fases** | Se despliega módulo a módulo, no todo el sistema de una vez |

> 📡 **Cambiando activamente**: en desarrollo web, este concepto se traduce hoy en el **despliegue** (*deployment*) del código a un servidor, cada vez más automatizado mediante prácticas de **CI/CD** (integración y despliegue continuos) — lo veremos con detalle en unidades posteriores, pero la idea de fondo (llevar el software del entorno de desarrollo al real, con algún grado de gradualidad o seguridad) es la misma que en explotación.

### 2.7. Mantenimiento

Se actúa sobre el software ya en producción. Se distinguen cuatro tipos, y no todos significan "hay un error":

| Tipo | Qué resuelve | Ejemplo |
|---|---|---|
| **Correctivo** | Corregir errores detectados en producción | "Se corrige un fallo al iniciar sesión" |
| **Evolutivo** | Añadir funcionalidad nueva que el cliente no pidió al principio | "Se añade un modo oscuro" |
| **Adaptativo** | Adaptarse a cambios del entorno, no del propio software | "Se adapta a la nueva versión de Android" |
| **Perfectivo** | Mejorar sin cambiar la funcionalidad visible | "Se optimiza el tiempo de arranque" |

Si el mantenimiento implica una ampliación importante, suele ser necesario revisar fases anteriores — Análisis y Diseño incluidos.

> 💡 Fíjate en el registro de actualizaciones de cualquier app que uses: casi cada entrada encaja en uno de estos cuatro tipos. Es justo lo que te va a pedir el reto de clase de esta unidad.

---

**¿Quién interviene en cada fase?** Los roles no son compartimentos estancos — la misma persona puede cubrir varios:

| Rol | Fases en las que participa |
|---|---|
| Analista de sistemas | Análisis |
| Diseñador de software | Diseño |
| Analista programador ("desarrollador") | Diseño y Codificación |
| Programador | Codificación |
| Arquitecto de software | Análisis, Diseño, Documentación y Explotación |

### ¿Cascada es la única forma de organizarlo?

No. El modelo en cascada es lineal y rígido — si en Pruebas aparece un fallo de Diseño, hay que volver atrás varias fases. Existen alternativas clásicas que organizan estas mismas fases de otra manera:

| Modelo | Idea central |
|---|---|
| **Iterativo-incremental** | El software se construye y entrega en incrementos sucesivos, cada uno añadiendo funcionalidad sobre el anterior |
| **En espiral** (Boehm) | Combina iteración con un análisis de riesgos explícito en cada vuelta, antes de seguir avanzando |
| **De prototipado** | Se construye pronto una versión reducida y funcional para validarla con el cliente antes de desarrollar el sistema completo |

> 📡 **Actualidad**: hoy, la gran mayoría de equipos de desarrollo no usa cascada ni estos modelos clásicos como forma habitual de trabajar, sino **metodologías ágiles** (Scrum, Kanban...) — según el informe *State of Agile* de Digital.ai, alrededor del 71% de las organizaciones declara usarlas en su ciclo de desarrollo. La cascada sigue siendo útil como modelo de referencia para entender qué fases existen y qué produce cada una (que es el objetivo de este punto), y todavía se usa en proyectos con requisitos muy cerrados o muy regulados — pero no es representativa de cómo trabaja hoy la mayoría de equipos. Vemos cómo funcionan estas metodologías ágiles, sus técnicas y cuándo aplicarlas, en el punto siguiente.

**🧪 Ejercicios de la fase**

**Ejercicio 5 — Fases del ciclo de vida aplicadas**
Un cliente te pide una aplicación de gestión de gastos personales. En `ejercicio5.md`, redacta brevemente (2-3 líneas por fase) qué harías en cada una de las 7 fases del ciclo de vida para ese proyecto concreto.

**Ejercicio 6 — Requisitos funcionales o no funcionales**
Para la misma aplicación de gastos personales, en `ejercicio6.md` clasifica estos 6 requisitos en funcionales o no funcionales, justificando cada uno en una frase: (1) "el usuario puede exportar sus gastos a PDF"; (2) "la aplicación debe funcionar sin conexión a internet"; (3) "se pueden crear categorías personalizadas"; (4) "ningún usuario puede ver los datos de otro"; (5) "el histórico de un año debe cargar en menos de 3 segundos"; (6) "se puede iniciar sesión con Google".

**Ejercicio 7 — Clasifica el mantenimiento**
Busca el registro de cambios (*changelog* o "novedades de esta versión") de una app que tengas instalada y elige 4 entradas distintas. En `ejercicio7.md`, clasifica cada una como mantenimiento correctivo, evolutivo, adaptativo o perfectivo, y justifícalo.

---

## 3. Metodologías ágiles de desarrollo (CA 1g)

### 3.1. Por qué surgen: los límites de la cascada

| | Modelo clásico (cascada) | Metodologías ágiles |
|---|---|---|
| Requisitos | Se cierran al principio; cambiar algo a mitad de proyecto es costoso | Se esperan cambios; se revisan y ajustan en cada iteración |
| Entrega al cliente | Una sola vez, al final del proyecto | Parcial y frecuente — cada pocas semanas |
| Documentación | Extensa y formal (ERS, cuaderno de carga...) | La mínima necesaria; el software que funciona pesa más que el papel |
| Participación del cliente | Sobre todo en Análisis y en Pruebas de aceptación | En cada iteración, revisando lo entregado |

En 2001, un grupo de desarrolladores publicó el **Manifiesto Ágil**, con cuatro valores que resumen este cambio de enfoque: individuos e interacciones sobre procesos y herramientas; software funcionando sobre documentación exhaustiva; colaboración con el cliente sobre negociación contractual; responder al cambio sobre seguir un plan rígido. No dice que lo segundo de cada par no importe — dice que lo primero pesa más cuando hay que elegir.

### 3.2. Técnicas ágiles más usadas

| | Scrum | Kanban |
|---|---|---|
| Ritmo de trabajo | Por *sprints*: bloques cerrados de 1 a 4 semanas | Flujo continuo, sin bloques de tiempo fijos |
| Cómo se organiza el trabajo | *Product backlog* (lista priorizada de todo el proyecto) → *sprint backlog* (lo que entra en el sprint actual) | Tablero visual con columnas (p. ej. *To Do / Doing / Done*) |
| Roles | Product Owner, Scrum Master, equipo de desarrollo | No define roles fijos |
| Control del trabajo en curso | El sprint ya cerrado no cambia hasta la siguiente reunión de planificación | Límites de **WIP** (*work in progress*): un número máximo de tareas por columna, para no empezar más de lo que se puede terminar |
| Reuniones típicas | *Daily* (diaria, breve), *sprint review* (enseñar lo hecho) y *retrospectiva* (qué mejorar) | No exige reuniones fijas — el tablero es la referencia constante |

Ambas son técnicas, no recetas cerradas: muchos equipos mezclan ideas de las dos (por ejemplo, "Scrumban").

### 3.3. Cuándo usar cada modelo (escenarios de uso)

- **La cascada encaja mejor** cuando los requisitos están cerrados desde el principio y cambiarán poco (un contrato con alcance fijo), cuando la normativa exige documentación extensa antes de cada fase (software médico, aeroespacial, de control industrial), o cuando el cliente no puede o no quiere participar de forma continua durante el desarrollo.
- **Lo ágil encaja mejor** cuando los requisitos son susceptibles de cambiar sobre la marcha (un producto digital que se ajusta según el uso real), cuando interesa tener algo funcionando cuanto antes para recibir *feedback*, o cuando el equipo y el cliente pueden mantener contacto frecuente.

> 📡 **Por qué importa hoy**: el **dashboard de finanzas personales** que iremos construyendo a lo largo del curso es exactamente el segundo caso — iremos añadiendo funciones (registrar un gasto, crear categorías, ver un gráfico mensual...) en incrementos cortos, en vez de intentar cerrar todos los requisitos antes de escribir la primera línea de código.

**🧪 Ejercicio 8 — Cascada o ágil, y un primer tablero Kanban**
**Parte 1.** Para cada uno de estos dos proyectos, decide si encaja mejor con cascada o con metodologías ágiles y justifícalo en 1-2 líneas: (a) el software de control de un satélite, con requisitos cerrados por contrato y sujeto a certificación oficial antes de cada fase; (b) una app de recetas de cocina que un pequeño estudio quiere lanzar cuanto antes para ir mejorándola según lo que pidan los primeros usuarios. Escribe tu respuesta en `ejercicio8.md`.
**Parte 2.** En el mismo archivo, crea un tablero Kanban en formato tabla Markdown (columnas *To Do / Doing / Done*) para el dashboard de finanzas personales, repartiendo al menos 5 tareas entre las tres columnas (por ejemplo: "diseñar el formulario de nuevo gasto", "conectar con la base de datos", "gráfico de gastos por categoría"...).

---

## 4. Código fuente, código objeto y código ejecutable (CA 1c)

Un dispositivo solo entiende **código máquina** (binario). Como nadie programa directamente en binario, escribimos en un lenguaje de programación y dejamos que unas herramientas lo traduzcan — pero ese camino no es idéntico en todos los lenguajes:

```
Modelo de compilación directa (C, C++...):
código fuente  ──(compilador)──▶  código objeto  ──(+ librerías, enlazador)──▶  código ejecutable nativo
   (.c)                             (.o)                                          (específico del SO)

Modelo de código intermedio (Java...):
código fuente  ──(compilador)──▶  código intermedio / bytecode  ──(máquina virtual, punto 5)──▶  se ejecuta
   (.java)                          (.class)
```

- **Código fuente**: el conjunto de instrucciones que escribe el desarrollador, en un fichero de texto (`.java`, `.py`, `.c`...).
- **Código objeto**: resultado de compilar el código fuente en el modelo de compilación directa. Todavía no es ejecutable por sí solo — le falta enlazarse con librerías y con las particularidades del sistema de destino.
- **Código intermedio** (o *bytecode*): resultado de compilar el código fuente en lenguajes como Java, pensado para no depender de un procesador concreto. **No es sinónimo de código objeto**: no se enlaza para dar un ejecutable nativo — lo ejecuta una máquina virtual (lo vemos en el punto 5). En Java es el fichero `.class`.
- **Código ejecutable**: en el modelo de compilación directa, se obtiene al añadir al código objeto las funciones de librerías usadas y las particularidades del sistema operativo de destino (proceso normalmente realizado por un *enlazador*). Es lo que el dispositivo interpreta directamente.

⚠️ **Código objeto y código intermedio no son lo mismo**, aunque los dos sean un paso a medio camino antes de que el programa corra: el objeto se enlaza para dar un ejecutable nativo; el intermedio lo interpreta una máquina virtual, sin pasar por un enlazador tradicional. Es justo la frontera entre este punto (CA 1c) y el siguiente (CA 1d).

⚠️ Un mismo código fuente puede necesitar generar **ejecutables distintos** según el sistema operativo destino (Windows, Linux, macOS), aunque el código fuente no cambie — esto aplica al modelo de compilación directa.

**El enlazador hace algo más que "juntar" ficheros** (de nuevo, en el modelo de compilación directa — en Java es la máquina virtual quien resuelve las clases en tiempo de ejecución, punto 5). Decide además *cómo* se incorporan las librerías al ejecutable final:

- **Enlazado estático**: el código de la librería se copia dentro del propio ejecutable. El fichero final es más grande, pero no depende de nada externo para funcionar.
- **Enlazado dinámico**: el ejecutable solo guarda una referencia a la librería, que se carga por separado en tiempo de ejecución (los `.dll` en Windows, los `.so` en Linux). Varios programas pueden compartir una misma copia de la librería en memoria, y actualizarla no obliga a recompilar cada programa que la usa.

**El esquema no se ve igual en todos los lenguajes.** Fuente → objeto → ejecutable es más visible en un lenguaje compilado; en uno interpretado, el propio término "ejecutable" no aplica de la misma forma:

| Lenguaje | Código fuente | Código objeto / intermedio | Código ejecutable |
|---|---|---|---|
| C (compilado) | `programa.c` | Interno al proceso de compilación, no se guarda como archivo aparte | `programa.exe` / binario nativo |
| Java (híbrido) | `Programa.java` | `Programa.class` (bytecode) | No hay un ejecutable nativo — lo interpreta la JVM (punto 5) |
| Python (interpretado) | `programa.py` | `__pycache__/programa.cpython-3XX.pyc` (bytecode cacheado, automático) | No se genera — el intérprete ejecuta ese bytecode compilado internamente, sin generar un ejecutable nativo aparte |

> 💡 Retomaremos esta tabla en el punto 6, al clasificar los lenguajes según cómo se ejecutan — es la misma idea vista desde el otro lado.

**En la práctica, con comandos reales:**

```
# C: compilación + enlazado en un solo paso
$ gcc programa.c -o programa
$ ./programa

# Java: compilación a bytecode, y ejecución sobre la JVM (punto 5)
$ javac HolaMundo.java      # genera HolaMundo.class (código intermedio, no código objeto)
$ java HolaMundo            # la JVM ejecuta el bytecode (interpretándolo o compilándolo con JIT)

# Python: compila a bytecode internamente (lo cachea en __pycache__) y lo ejecuta
$ python programa.py        # no genera un ejecutable nativo aparte — lo procesa su propia máquina virtual
```

> 📡 **Cambiando activamente: la frontera se difumina.** Motores como V8 (el que usan Chrome y Node.js) ya no solo interpretan JavaScript línea a línea: compilan sobre la marcha, mientras el programa se ejecuta, las partes de código que más se repiten — se llama compilación **JIT** (*just-in-time*). En sentido contrario, herramientas como GraalVM permiten compilar bytecode Java directamente a un ejecutable nativo (`native-image`), sin necesitar una JVM en el equipo final. La clasificación compilado/interpretado/híbrido del punto 6 sigue siendo útil para entender la idea de fondo, pero cada vez hay más lenguajes que mezclan las tres estrategias.

> 🧯 **Plan B si no puedes instalar el JDK**: usa un compilador Java online (por ejemplo, jdoodle.com/online-java-compiler) para completar el ejercicio sin instalar nada localmente — lo que se evalúa es que entiendas el proceso fuente → bytecode → ejecución, no la instalación en sí. Si dispones de la VM portátil del ciclo, el JDK ya viene preinstalado ahí: es el sitio ideal para tenerlo listo de antemano.

**🧪 Ejercicio 9 — De código fuente a ejecutable**
Esta es la única vez en la unidad que usamos Java para un ejercicio de código: es el lenguaje que mejor ilustra el modelo de código intermedio — no hace falta que le cojas el gusto a su sintaxis. Instala un JDK si no lo tienes, y en tu carpeta `UD01` crea `HolaMundo.java` con un programa que imprima tu nombre. Compílalo desde la terminal integrada con `javac HolaMundo.java`. Localiza en el explorador de archivos de VS Codium el fichero `.class` generado y ejecútalo con `java HolaMundo`. En `ejercicio9.md`, explica con tus palabras qué representa cada uno de los tres ficheros/momentos (fuente, código intermedio, ejecución) en este proceso.

**🧪 Ejercicio 10 — El esquema en distintos lenguajes**
Crea `ejercicio10.py` con cualquier instrucción sencilla (por ejemplo, un `print`) y ejecútalo una vez desde la terminal integrada. Localiza en el explorador de archivos de VS Codium la carpeta `__pycache__` que se genera junto a él y el fichero `.pyc` que contiene. Apoyándote en la tabla anterior y en lo que acabas de ver, en `ejercicio10.md` explica con tus palabras por qué en Python no tiene sentido hablar de "código ejecutable" de la misma forma que en C, y qué papel juega ese `.pyc`.

**🧪 Ejercicio 11 — Compilado vs. interpretado, cronómetro en mano**
Usamos C solo para esta comparación puntual — no hace falta escribirlo ni dominarlo, solo compilarlo, ejecutarlo y medirlo. En tu carpeta `UD01`, crea `ejercicio11.c` con este código ya escrito:

```c
#include <stdio.h>
int main() {
    long long suma = 0;
    for (long long i = 1; i <= 10000000; i++) {
        suma += i;
    }
    printf("%lld\n", suma);
    return 0;
}
```

Ahora escribe tú mismo, en `ejercicio11.py`, la versión equivalente en Python (un bucle que sume los números del 1 al 10 millones — este sí en el lenguaje que ya conoces). Desde la terminal integrada, compila y ejecuta la versión en C (`gcc ejercicio11.c -o ejercicio11 && ./ejercicio11`); ejecuta directamente la versión en Python. Cronometra ambas con `time` (`time ./ejercicio11` y `time python ejercicio11.py`). En `ejercicio11.md`, recoge los tiempos y explica la diferencia según lo visto en este punto.

---

## 5. Código intermedio y máquinas virtuales (CA 1d)

Según cómo se trate el código, un ejecutable puede ser:

- **Portable**: funciona en varias plataformas sin recompilar (p. ej., un `.jar` de Java, porque usa *bytecode* no ligado a un procesador concreto).
- **No portable**: pensado para una plataforma concreta (p. ej., un ejecutable compilado en C para Windows).

Algunos lenguajes, como Java, resuelven la portabilidad con una **máquina virtual**: una aplicación que emula un sistema (o parte de él) dentro del sistema operativo real.

| Tipo de máquina virtual | Qué hace | Ejemplos |
|---|---|---|
| **De sistema** | Simula un ordenador completo (arquitectura + SO) dentro de otro | VirtualBox, VMware |
| **De proceso** | Ejecuta el código intermedio (bytecode) de un lenguaje concreto, independizándolo del hardware real | JVM (Java Virtual Machine) |

La **JVM** ejecuta el *bytecode* que genera el compilador de Java (los ficheros `.class`) — interpretándolo instrucción a instrucción o, en las partes que más se repiten, compilándolo sobre la marcha (JIT, como vimos en el punto 4) —, traduciéndolo en ambos casos a las instrucciones del hardware concreto donde se ejecuta. Por eso el mismo `.class` corre en Windows, Linux o macOS sin recompilar, siempre que haya una JVM instalada: "*write once, run anywhere*".

> 🕰️ **Por qué existe la JVM**: a mediados de los años 90 cada sistema operativo tenía su propio formato de ejecutable, y distribuir un programa para varias plataformas obligaba a compilarlo y mantenerlo por separado para cada una. Sun Microsystems diseñó Java (1995) con la JVM como pieza central para resolver justo ese problema: compilar una sola vez a bytecode y dejar que la máquina virtual se encargue de adaptarse al sistema real. La necesidad que resolvió sigue vigente — es la misma razón de fondo por la que hoy existen los contenedores y WebAssembly, que vemos a continuación.

**El pipeline completo, de principio a fin:**

```
Programa.java  ──(javac, compilador)──▶  Programa.class (bytecode)
Programa.class ──(java, se ejecuta sobre la JVM)──▶  el programa corre
```

> 📡 **Sigue vigente**: el modelo de máquina virtual de proceso no es exclusivo de Java — Python (con su intérprete y bytecode `.pyc`) y .NET (CLR) funcionan sobre una idea muy similar.

> 📡 **Cambiando activamente: contenedores**. Una máquina virtual de sistema emula un ordenador completo con su propio sistema operativo — aísla mucho, pero es "pesada". Una alternativa moderna y más ligera son los **contenedores** (Docker es el más conocido): en vez de emular todo el hardware, comparten el núcleo del sistema operativo anfitrión y solo aíslan la aplicación y sus dependencias. Los veremos con detalle en la UP2, entornos de desarrollo — de momento basta con saber que "aislar un programa del resto del sistema" no siempre pasa por una máquina virtual completa.

> 📡 **Cambiando activamente: WebAssembly (Wasm)**. Es la evolución más reciente de la misma idea de "bytecode portable", pero pensada para el navegador: un formato que permite ejecutar código escrito en C, C++, Rust o incluso Java dentro de una página web, a una velocidad cercana a la nativa — algo que JavaScript por sí solo no ofrece. No sustituye a JavaScript, lo complementa en las partes de una aplicación web que necesitan más rendimiento (edición de imagen o vídeo en el propio navegador, videojuegos, cálculo intensivo). En el desarrollo web actual es donde más está creciendo esta idea de "máquina virtual de proceso".

**🧪 Ejercicio 12 — JVM y WebAssembly, dos máquinas virtuales de proceso**
Vuelve a leer el aviso sobre WebAssembly de este punto — no hace falta buscar nada más. En `ejercicio12.md`, responde con tus propias palabras: (1) ¿en qué se parecen la JVM y WebAssembly como máquinas virtuales de proceso? (2) ¿dónde se usa cada una, y por qué WebAssembly no sustituye a JavaScript sino que lo complementa?

---

## 6. Clasificación de los lenguajes de programación (CA 1e)

No hay una única forma de clasificar los lenguajes; estas son las más habituales.

**Según cómo se ejecutan:**

| Tipo | Cómo funciona | Ejemplos | Dónde se usan más |
|---|---|---|---|
| **Compilados** | El código fuente se traduce entero, de una vez, a un ejecutable | C, C++, Pascal | Software de escritorio (ejecución rápida, ficheros más pesados) |
| **Interpretados** | Un intérprete ejecuta el código sin generar un ejecutable nativo — muchos (como Python) compilan antes internamente a un bytecode que después procesan (punto 4) | Python, PHP, JavaScript | Entornos web y scripting (menos recursos, más lentos) |
| **Híbridos / virtuales** | Se compilan a código intermedio (bytecode), que luego interpreta una máquina virtual | Java, C# (en parte) | Aplicaciones que deben correr en varias plataformas sin recompilar |

> 💡 Esta clasificación es la primera aproximación más útil para empezar, pero no es una etiqueta rígida y excluyente: como vimos en el punto 4, la frontera entre compilado e interpretado cada vez es más difusa (motores JIT como V8, herramientas como GraalVM...). Sirve para entender el modelo *dominante* de cada lenguaje, no para encasillarlo.

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

**Un mismo problema, dos paradigmas.** La diferencia entre imperativo y declarativo se nota mejor en código que en definiciones — para "quedarse con los números pares de una lista":

```python
# Imperativo: se describe paso a paso el "cómo"
pares = []
for n in numeros:
    if n % 2 == 0:
        pares.append(n)
```

```sql
-- Declarativo: se describe el "qué", sin decir cómo recorrerlo
SELECT * FROM numeros WHERE n % 2 = 0;
```

**En la práctica, pocos lenguajes son "puros".** La tabla de paradigmas clasifica según la idea *dominante* de cada lenguaje, no una etiqueta única y excluyente: Python y JavaScript son fundamentalmente imperativos y orientados a objetos, pero incorporan funciones de estilo funcional (`map`, `filter`) sin ningún problema; SQL es declarativo, pero muchos motores permiten añadir lógica imperativa (procedimientos almacenados en PL/SQL, T-SQL...). Es habitual que un mismo lenguaje combine varios paradigmas según lo que convenga en cada parte del código.

Por último, en el contexto de aplicaciones web es habitual distinguir entre **front-end** (la parte visible, que corre en el navegador del usuario: HTML, CSS, JavaScript) y **back-end** (la lógica no visible, que corre en un servidor: Java, Python, PHP, SQL...). Quien domina cómodamente ambas partes se conoce como **desarrollador full-stack** — uno de los perfiles más demandados en desarrollo web hoy, y el que iremos trabajando progresivamente a lo largo de este ciclo.

> 📡 **Actualidad**: la popularidad de los lenguajes cambia con el tiempo. El **índice TIOBE** (`tiobe.com/tiobe-index`) es una de las referencias más consultadas para ver qué lenguajes están en auge o en declive — pero es una fotografía mensual, no una verdad fija: conviene consultarlo actualizado en vez de memorizar un ranking.

**🧪 Ejercicio 13 — Clasifica estos lenguajes**
En `ejercicio13.md`, para Python, Java, C y JavaScript, indica en una tabla Markdown: tipo de ejecución (compilado/interpretado/híbrido), nivel de abstracción y paradigma principal. Justifica cada respuesta en una frase.

**🧪 Ejercicio 14 — El mismo problema, dos paradigmas**
Para el dashboard de finanzas personales, plantea la tarea "obtener los usuarios que han gastado más de 100 € este mes". En `ejercicio14.md`, escribe una solución imperativa en pseudocódigo (con un bucle y una condición); en `ejercicio14.sql`, la solución declarativa (una sola consulta `SELECT` — no hace falta ejecutarla todavía, solo que la sintaxis sea correcta). En `ejercicio14.md`, compara ambas: ¿cuál describe el "cómo" y cuál el "qué"?

---

## 7. Herramientas del desarrollo de software (CA 1f)

Además del lenguaje, un desarrollador se apoya en herramientas que dan soporte a cada fase del ciclo de vida. Esta unidad solo las **clasifica**; profundizaremos en varias de ellas en unidades posteriores.

### 7.1. Editor de código / IDE

Un editor de texto simple (el Bloc de notas) también puede escribir código, pero un **IDE** (*Integrated Development Environment*) añade herramientas integradas para todo el ciclo de codificación: autocompletado, resaltado de sintaxis, detección de errores mientras escribes y depuración incorporada. Ejemplos: Visual Studio Code, Eclipse, IntelliJ. **Se trabaja en detalle en la UP2.**

### 7.2. Compilador / intérprete

Traduce código fuente a código objeto, intermedio o ejecutable, o lo ejecuta mediante un intérprete o máquina virtual — es la herramienta que materializa todo lo visto en los puntos 4 y 6 de esta unidad. Ejemplos: `javac`/`java`, el propio intérprete de Python, GCC. **UP1-UP2.**

### 7.3. Control de versiones

Registra el historial de cambios del código y permite que varias personas trabajen sobre el mismo proyecto sin sobrescribirse — ya lo adelantamos en el punto 2.3, al hablar de la fase de Codificación. Ejemplos: Git, GitHub. **UP3.**

```
$ git init
$ git add cambios.py
$ git commit -m "Primer commit"
```

### 7.4. Depuración y pruebas

Permite ejecutar el programa paso a paso, inspeccionar el valor de las variables en cada momento, y automatizar las comprobaciones vistas en el punto 2.4 (pruebas unitarias, de integración...) en vez de repetirlas a mano cada vez. Ejemplos: el depurador integrado del IDE, JUnit. **UP5.**

### 7.5. Gestión de dependencias y construcción del proyecto

Instala librerías externas (retomando el concepto de librería del punto 1.1) sin tener que descargarlas e integrarlas a mano, y automatiza pasos repetitivos como compilar, ejecutar pruebas o empaquetar el proyecto. Ejemplos: `pip`, Maven, npm. **UP2.**

En Python, antes de instalar nada es habitual aislar las dependencias de cada proyecto en un **entorno virtual** (`venv`): una copia local del intérprete y sus librerías, independiente de la instalación global del sistema y de la de otros proyectos — así el proyecto A puede usar una versión de una librería y el proyecto B otra distinta, sin que choquen entre sí.

```
$ python -m venv .venv                    # crea el entorno virtual en la carpeta .venv
$ source .venv/bin/activate               # lo activa (Linux/Mac); en Windows: .venv\Scripts\activate
(.venv) $ pip install matplotlib          # instala la librería solo dentro de este entorno
(.venv) $ pip freeze > requirements.txt   # registra las dependencias del proyecto
```

> 📡 **Un paso más: contenedores**. Un entorno virtual aísla las dependencias de Python, pero no el resto del sistema (versión del sistema operativo, otros programas instalados...). Cuando ese aislamiento hay que llevarlo también ahí — por ejemplo, para que la aplicación corra igual en cualquier ordenador o servidor —, se usa un **contenedor** (Docker es el más conocido), que ya vimos como concepto en el punto 5. Es la misma idea de fondo que un `venv`, pero un nivel más abajo — con base y práctica real lo trabajaremos en la UP2.

### 7.6. Análisis y documentación de código

Revisa automáticamente la calidad del código (código duplicado, mal estilo, posibles vulnerabilidades) y genera documentación técnica a partir de los propios comentarios del código fuente. Ejemplos: SonarQube, Javadoc. **UP7.**

> 📡 **Cambiando activamente: asistentes de código con IA**. Herramientas como GitHub Copilot, o el autocompletado inteligente ya integrado en muchos IDEs actuales, sugieren código mientras escribes apoyándose en modelos de lenguaje. No son una categoría nueva: se integran dentro del editor/IDE (7.1). Están cambiando cómo se escribe código día a día, pero siguen haciendo falta los mismos fundamentos de esta unidad para revisar y entender lo que sugieren — no para copiarlo sin más.

> 💡 Ejemplo integrador: si más adelante desarrollamos un **dashboard de finanzas personales** en Python con una base de datos SQLite, usaríamos como mínimo: un IDE (VS Code) para escribir el código, Git/GitHub para el control de versiones, `pip` para instalar librerías (por ejemplo, para generar gráficos) y `pytest` para probar que los cálculos son correctos. Cada una de esas herramientas cubre una funcionalidad distinta dentro del desarrollo.

**🧪 Ejercicio 15 — Herramientas para un proyecto**
Para el proyecto de "dashboard de finanzas personales" del punto 7, en `ejercicio15.md` indica qué herramienta de cada categoría de la tabla usarías y por qué, aunque hoy no sepas usarlas todavía (búscalo si hace falta).

**🧪 Ejercicio 16 — Instala y prueba una herramienta**
Elige una categoría de la tabla anterior con una herramienta que no conozcas todavía (por ejemplo, un linter de análisis de código o un gestor de dependencias distinto al visto en clase) e instálala en tu equipo. Pruébala desde la terminal integrada de VS Codium sobre alguno de los ficheros que ya tienes en tu carpeta `UD01`. En `ejercicio16.md`, documenta en 4-5 líneas: qué problema resuelve, qué comando usaste para instalarla, y el resultado de haberla ejecutado.

---

## 🎯 Reto de clase

Elige una aplicación que uses habitualmente en el móvil (una app de mensajería, de banca, de transporte...). Investiga primero qué tecnologías tiene documentadas públicamente (su web de desarrolladores, ofertas de empleo de la empresa...); cuando no encuentres nada verificable, formula una hipótesis razonada y dilo explícitamente como tal — distinguir "lo sé", "lo he encontrado documentado" y "lo estoy deduciendo" es una habilidad tan importante como el contenido técnico. En VS Codium, crea `reto.md` dentro de tu carpeta `UD01` con una ficha que incluya:

1. Una hipótesis razonada sobre qué lenguaje(s) de programación se usaron para su parte visible y para su lógica interna (front-end/back-end), con al menos un argumento técnico de por qué.
2. Una hipótesis sobre si el ejecutable que corre en tu móvil es compilado, interpretado o híbrido (justifícalo con lo que sepas de Android/iOS y las máquinas virtuales vistas en el punto 5).
3. Un esquema de las 7 fases del ciclo de vida aplicado a esa app: qué requisitos crees que se recogieron en el Análisis, y qué tipo de Mantenimiento recibe (busca su historial de actualizaciones en la tienda de aplicaciones como pista).

**Plantilla orientativa para `reto.md`** (puedes seguirla tal cual o adaptarla):

```markdown
# Reto — [nombre de la app]

## 1. Lenguajes probables
- Front-end: ...
- Back-end: ...
- Argumento técnico: ...

## 2. Compilado, interpretado o híbrido
- Hipótesis: ...
- Justificación (Android/iOS, máquinas virtuales del punto 5): ...

## 3. Ciclo de vida aplicado
- Requisitos que crees que se recogieron en el Análisis: ...
- Tipo de mantenimiento que recibe, según el historial de actualizaciones: ...
```

*Variación evaluable*: se puede pedir por parejas, comparando dos apps de la misma categoría (por ejemplo, dos apps bancarias) para que el alumnado contraste hipótesis distintas.

---

<div style="page-break-after: always;"></div>

## Resumen de la unidad

**1. El programa y los componentes del sistema** El software se clasifica por su forma (programa, librería, aplicación, suite) y por su función (software de sistema vs. de aplicación). Un programa en ejecución se apoya en memoria (RAM, volátil), procesador (ciclo fetch-decode-execute) y periféricos (entrada, salida o ambas) — programar es solo la fase de codificación dentro de desarrollar software, que además analiza, diseña, prueba, documenta y mantiene.

**2. El ciclo de vida del software** Modelo en cascada, en 7 fases: análisis (requisitos funcionales/no funcionales), diseño (arquitectónico y detallado, UML), codificación (buenas prácticas), pruebas (caja negra/blanca, niveles), documentación de usuario, explotación (estrategias de implantación) y mantenimiento (correctivo, evolutivo, adaptativo, perfectivo) — cada fase genera su propia documentación y con roles que pueden solaparse. La cascada es el modelo de referencia para entender las fases, pero hoy la mayoría de equipos usa metodologías ágiles (ver punto 3); otros modelos clásicos (iterativo-incremental, en espiral, prototipado) sí forman parte de esta unidad.

**3. Metodologías ágiles de desarrollo** Surgen frente a las limitaciones de la cascada (documentación extensa, una sola entrega final, poco margen para el cambio) — el Manifiesto Ágil (2001) prioriza el software funcionando y la colaboración frecuente con el cliente. Scrum (sprints, roles, reuniones fijas) y Kanban (tablero visual, límites de WIP, flujo continuo) son sus dos técnicas más usadas; la cascada encaja mejor con requisitos cerrados o muy regulados, lo ágil con proyectos que evolucionan sobre la marcha — como el dashboard de finanzas personales de esta unidad.

**4. Código fuente, objeto y ejecutable** En compilación directa (C), el código fuente se compila a código objeto y este se enlaza (de forma estática o dinámica) con librerías y particularidades del SO para dar el ejecutable nativo final; en el modelo de código intermedio (Java), el fuente compila a bytecode y es una máquina virtual, no un enlazador, quien lo ejecuta — código objeto y código intermedio no son sinónimos, aunque ambos sean un paso a medio camino. El esquema se ve distinto según el lenguaje sea compilado, híbrido o interpretado, y puede necesitar ejecutables distintos según la plataforma destino. La frontera compilado/interpretado ya no es tan tajante: motores JIT como V8 compilan JavaScript sobre la marcha, y herramientas como GraalVM compilan bytecode Java a ejecutable nativo.

**5. Código intermedio y máquinas virtuales** Las máquinas virtuales (de sistema o de proceso) permiten portabilidad: la JVM ejecuta el mismo bytecode `.class` en cualquier sistema operativo, la idea detrás de "write once, run anywhere" — Python y .NET siguen un planteamiento similar, y nació para resolver la falta de portabilidad entre sistemas operativos de los años 90. Los contenedores (Docker) y WebAssembly (bytecode portable para el navegador) son evoluciones más recientes de la misma idea.

**6. Clasificación de los lenguajes** Se clasifican según cómo se ejecutan (compilados, interpretados, híbridos), su nivel de abstracción (bajo, medio, alto) y su paradigma dominante (imperativo, orientado a objetos, funcional, declarativo — la mayoría combina varios, y un mismo problema se resuelve de forma distinta en cada paradigma) — además de la distinción front-end/back-end, y el perfil full-stack que domina ambas.

**7. Herramientas del desarrollo de software** IDE, compiladores/intérpretes, control de versiones, depuración y pruebas, gestión de dependencias, y análisis/documentación de código — cada categoría da soporte a una fase distinta del ciclo de vida del punto 2, con comandos y ejemplos reales (Git, pip, venv) que se trabajarán en detalle a partir de la UP2, donde entrarán también los contenedores (Docker); los asistentes de código con IA son la novedad más activa dentro del editor/IDE, sin sustituir los fundamentos de esta unidad.

---

## 📚 Para saber más (opcional, no evaluable)

- Índice TIOBE (popularidad de lenguajes, actualizado mensualmente): https://www.tiobe.com/tiobe-index/
- Documentación oficial de la JVM: https://docs.oracle.com/javase/specs/

### 🧭 Por qué te va a servir esto de verdad

- En una entrevista técnica es habitual que te pregunten por qué elegirías un lenguaje compilado o interpretado para un proyecto — responder con seguridad (rendimiento frente a rapidez de desarrollo, portabilidad...) es mucho más creíble si entiendes el porqué, no solo el nombre.
- Al entrar en una empresa vas a "heredar" un proyecto que sigue algún modelo de ciclo de vida (probablemente ágil, pero con restos de cascada en la documentación) — saber reconocer en qué fase está te ayuda a entender qué se espera de ti desde el primer día.
- Justificar por qué documentas tu código, por qué usas control de versiones o por qué una empresa exige pasar un analizador de código antes de fusionar un cambio no es "burocracia": es justo lo que un responsable técnico evalúa durante un periodo de prueba.
