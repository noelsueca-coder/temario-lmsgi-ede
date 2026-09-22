<div style="text-align: center;">

<img src="data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCA0MDAgNDAwIiB3aWR0aD0iMTgwIiBoZWlnaHQ9IjE4MCI+CiAgPGNpcmNsZSBjeD0iMjAwIiBjeT0iMjAwIiByPSIxNzAiIGZpbGw9IiNGMEZERkEiLz4KICA8Y2lyY2xlIGN4PSIyMDAiIGN5PSIyMDAiIHI9IjE3MCIgZmlsbD0ibm9uZSIgc3Ryb2tlPSIjOTlGNkU0IiBzdHJva2Utd2lkdGg9IjIiLz4KICA8Y2lyY2xlIGN4PSIyMDAiIGN5PSIxMzAiIHI9IjI0IiBmaWxsPSJub25lIiBzdHJva2U9IiMwRjc2NkUiIHN0cm9rZS13aWR0aD0iOSIvPgogIDxjaXJjbGUgY3g9IjE0MCIgY3k9IjI1MCIgcj0iMjQiIGZpbGw9Im5vbmUiIHN0cm9rZT0iIzBGNzY2RSIgc3Ryb2tlLXdpZHRoPSI5IiBvcGFjaXR5PSIwLjc1Ii8+CiAgPGNpcmNsZSBjeD0iMjYwIiBjeT0iMjUwIiByPSIyNCIgZmlsbD0ibm9uZSIgc3Ryb2tlPSIjMEY3NjZFIiBzdHJva2Utd2lkdGg9IjkiIG9wYWNpdHk9IjAuNzUiLz4KICA8bGluZSB4MT0iMjAwIiB5MT0iMTU0IiB4Mj0iMTQwIiB5Mj0iMjI2IiBzdHJva2U9IiMwRjc2NkUiIHN0cm9rZS13aWR0aD0iOCIvPgogIDxsaW5lIHgxPSIyMDAiIHkxPSIxNTQiIHgyPSIyNjAiIHkyPSIyMjYiIHN0cm9rZT0iIzBGNzY2RSIgc3Ryb2tlLXdpZHRoPSI4Ii8+CiAgPGxpbmUgeDE9IjE0MCIgeTE9IjI1MCIgeDI9IjI2MCIgeTI9IjI1MCIgc3Ryb2tlPSIjMEY3NjZFIiBzdHJva2Utd2lkdGg9IjgiIG9wYWNpdHk9IjAuNSIvPgo8L3N2Zz4K" width="180" alt="Logo LMSGI"/>

<h1>Unidad 6</h1>
<h2>Manipulación de documentos web</h2>

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

1. Qué es JavaScript y dónde se ejecuta
2. Variables, tipos de datos y literales
3. Operadores y conversiones entre tipos
4. Decisiones: estructuras condicionales
5. Bucles: repetir instrucciones
6. Integrar JavaScript en un documento HTML
7. El DOM: seleccionar y acceder a elementos
8. Crear y modificar elementos
9. Eliminar elementos
10. Manipular estilos desde JavaScript
11. Resumen de la unidad
12. Para saber más

<div style="page-break-after: always;"></div>

**RA cubierto:** RA2 (ASIX, CA 2f) / RA3 (DAW, CA 3a-3f) — *utiliza lenguajes de marcas para la transmisión y presentación de información a través de la web* / *accede y manipula documentos web utilizando lenguajes de script de cliente*

> 💡 **Nota de estudio**: esta unidad tiene dos mitades bien diferenciadas. En la primera (puntos 1-5) aprendes **JavaScript como lenguaje**: variables, tipos, operadores, condiciones y bucles — sin tocar todavía ni una etiqueta HTML. En la segunda (puntos 6-10) usas ese mismo JavaScript para **manipular el HTML que ya conoces**: seleccionar, crear, modificar y eliminar elementos de una página. Si algún concepto de la primera mitad ya te suena de otras asignaturas, puedes ir más rápido — pero no te saltes el punto 6 en adelante, es donde JavaScript se conecta con todo lo visto en LMSGI hasta ahora.

---

## 1. Qué es JavaScript y dónde se ejecuta

Todo lo que has escrito hasta ahora en este módulo es **declarativo**: HTML describe qué es cada cosa, CSS describe cómo se ve. Ninguno de los dos tiene variables, bucles ni decisiones — no son lenguajes de programación, como ya se dejó claro en la UD1. **JavaScript** sí lo es: es el lenguaje de programación que se ejecuta en el navegador y permite que una página **reaccione y cambie** después de haberse cargado, sin necesitar recargarla.

```
HTML  → qué es cada cosa (estructura)
CSS   → cómo se ve (presentación)
JS    → qué pasa cuando algo ocurre (comportamiento)
```

Un ejemplo que ya conoces sin saberlo: cuando pasas el ratón sobre un botón y cambia de color con `:hover` (UD4), eso es CSS puro, sin JavaScript. Pero si al **hacer clic** en ese botón aparece un mensaje, se valida un formulario, o se añade una fila a una tabla sin recargar la página — eso solo lo hace JavaScript.

JavaScript se ejecuta directamente en el navegador de quien visita la página (por eso se le llama **lenguaje de script de cliente**), sin necesitar instalar nada ni compilar nada — el propio navegador incluye el intérprete que lee y ejecuta el código línea a línea.

> 🕰️ **Un nombre engañoso**: pese al nombre, JavaScript no tiene relación técnica con el lenguaje de programación Java — se llamó así en 1995 por una decisión de marketing de Netscape, cuando Java estaba de moda. Son dos lenguajes completamente distintos, con sintaxis, usos y ejecución diferentes.

**🧪 Ejercicio 1 — HTML, CSS o JavaScript**
Para cada uno de estos comportamientos de una web, indica si depende de HTML, de CSS o de JavaScript, razonando tu respuesta: (a) un título se ve en negrita; (b) al escribir en un campo de formulario vacío y pulsar "Enviar", aparece un mensaje de error sin recargar la página; (c) un párrafo contiene una lista de tres elementos; (d) un menú lateral se despliega al hacer clic en un botón.

---

## 2. Variables, tipos de datos y literales

Una **variable** guarda un valor con un nombre, para poder usarlo y cambiarlo más adelante. En JavaScript moderno se declaran con `let` (si el valor va a cambiar) o `const` (si no va a cambiar nunca):

```javascript
let nombre = "Marta";
let edad = 16;
const modulo = "LMSGI";

edad = 17; // "let" permite reasignar
// modulo = "EDE"; // esto daría error: "const" no se puede reasignar
```

Un **literal** es el valor escrito directamente en el código (`"Marta"`, `16`) — la forma más simple de dato, sin necesitar cálculos ni variables previas.

**Tipos de datos básicos:**

| Tipo | Qué guarda | Ejemplo |
|---|---|---|
| `Number` | Números, enteros o decimales, sin distinción de tipo | `16`, `3.5`, `-2` |
| `String` | Texto, entre comillas simples, dobles o invertidas | `"Marta"`, `'LMSGI'`, `` `plantilla` `` |
| `Boolean` | Verdadero o falso | `true`, `false` |
| `undefined` | Una variable declarada pero sin valor asignado | `let x;` |
| `null` | Ausencia de valor, asignada explícitamente | `let x = null;` |

```javascript
console.log(typeof 16);        // "number"
console.log(typeof "Marta");   // "string"
console.log(typeof true);      // "boolean"
```

`console.log()` es la forma más básica de ver un resultado sin necesitar todavía HTML — imprime el valor en la **consola** del navegador (en Firefox: menú → Más herramientas → Herramientas de desarrollo web → pestaña Consola, o la tecla `F12`).

⚠️ **Ámbito de una variable**: dónde es "visible" esa variable dentro del código. Una variable declarada con `let`/`const` dentro de un bloque `{ }` (por ejemplo, dentro de un bucle o una condición) solo existe dentro de ese bloque — fuera de él, no se puede usar. Lo verás en la práctica en los puntos 4 y 5, al trabajar con condiciones y bucles.

**🧪 Ejercicio 2 — Variables de tu propia clase**
Abre la consola de Firefox y declara 4 variables: tu nombre (`String`), tu edad (`Number`), si estás matriculado en el módulo (`Boolean`) y una variable sin valor asignado todavía (`undefined`). Usa `console.log(typeof ...)` con cada una para comprobar su tipo, y anota el resultado.

---

## 3. Operadores y conversiones entre tipos

**Operadores aritméticos**: `+`, `-`, `*`, `/`, `%` (resto de una división). **Operadores de comparación**: `===` (igual estricto, compara valor **y** tipo — el que debes usar casi siempre), `!==` (distinto estricto), `<`, `>`, `<=`, `>=`. **Operadores lógicos**: `&&` (Y), `||` (O), `!` (NO).

```javascript
let a = 10;
let b = "10";

console.log(a === b);   // false — mismo valor, pero distinto tipo (Number vs String)
console.log(a == b);    // true  — "==" convierte el tipo antes de comparar, por eso da igual
```

⚠️ **`===` frente a `==`**: `==` compara el valor tras convertir automáticamente los tipos, lo que puede dar resultados poco intuitivos (`"10" == 10` es `true`). `===` compara valor **y** tipo sin convertir nada. Usa siempre `===`, salvo que tengas una razón concreta para lo contrario — es una de las fuentes de errores más comunes en JavaScript para quien empieza.

**Conversión de tipos**: a veces necesitas convertir explícitamente, por ejemplo, un texto leído de un formulario a número para poder operar con él:

```javascript
let texto = "25";
let numero = Number(texto);      // 25 (tipo Number)
console.log(numero + 5);         // 30

let n = 42;
let cadena = String(n);          // "42" (tipo String)
console.log(cadena + "5");       // "425" (concatenación de texto, no suma)
```

> 📡 **Por qué importa hoy**: cuando leas el valor de un `<input>` con JavaScript (lo verás en el punto 7), ese valor **siempre** llega como `String`, aunque el usuario haya escrito solo números — `Number(...)` es el paso que necesitarás casi siempre antes de hacer cualquier cálculo con datos de un formulario.

**🧪 Ejercicio 3 — El error clásico de sumar texto**
En la consola, declara `let a = "5"` y `let b = "3"`. Calcula `a + b` y anota qué obtienes — ¿una suma numérica o una concatenación de texto? Corrígelo usando `Number()` para que el resultado sea realmente `8`. Explica con tus palabras por qué ocurre esto.

---

## 4. Decisiones: estructuras condicionales

La estructura `if / else` ejecuta un bloque de código solo si se cumple una condición:

```javascript
let edad = 16;

if (edad >= 18) {
  console.log("Eres mayor de edad");
} else {
  console.log("Eres menor de edad");
}
```

Con varias condiciones encadenadas, `else if`:

```javascript
let nota = 6;

if (nota >= 9) {
  console.log("Sobresaliente");
} else if (nota >= 7) {
  console.log("Notable");
} else if (nota >= 5) {
  console.log("Aprobado");
} else {
  console.log("Suspenso");
}
```

Cuando hay muchos valores concretos que comparar contra una misma variable, `switch` suele ser más legible que una cadena larga de `else if`:

```javascript
let dia = "lunes";

switch (dia) {
  case "sabado":
  case "domingo":
    console.log("Fin de semana");
    break;
  default:
    console.log("Día laborable");
}
```

⚠️ **El `break` no es opcional**: sin él, la ejecución "cae" al siguiente `case` aunque no coincida — un error muy común al empezar con `switch`.

**🧪 Ejercicio 4 — Calificador de notas**
Escribe una función (puedes usar `if/else if` o `switch`, a tu elección) que, dada una variable `nota` con un número del 0 al 10, muestre por consola: "Sobresaliente" (9-10), "Notable" (7-8), "Bien" (6), "Aprobado" (5), "Suspenso" (0-4). Pruébala con al menos 4 valores distintos.

---

## 5. Bucles: repetir instrucciones

Un **bucle** repite un bloque de código mientras se cumpla una condición, sin tener que copiarlo a mano.

```javascript
// for: cuando sabes de antemano cuántas veces repetir
for (let i = 1; i <= 5; i++) {
  console.log("Repetición número " + i);
}
```

- `let i = 1`: valor inicial del contador.
- `i <= 5`: condición — el bucle sigue mientras sea `true`.
- `i++`: qué le pasa al contador en cada vuelta (equivale a `i = i + 1`).

```javascript
// while: cuando no sabes de antemano cuántas veces, depende de una condición
let intentos = 0;
let acertado = false;

while (!acertado && intentos < 3) {
  intentos++;
  console.log("Intento número " + intentos);
  // aquí iría la comprobación real que decide "acertado"
}
```

**Recorrer una lista de valores** (un *array*, la estructura para guardar varios valores bajo un mismo nombre) es uno de los usos más habituales de `for`:

```javascript
let modulos = ["LMSGI", "EDE", "Programación"];

for (let i = 0; i < modulos.length; i++) {
  console.log(modulos[i]);
}
```

`modulos.length` da el número de elementos del array, y `modulos[i]` accede al elemento en la posición `i` (recuerda: las posiciones empiezan en `0`, no en `1`).

**🧪 Ejercicio 5 — Suma de una lista**
Declara un array `let precios = [12.50, 8.90, 25.00, 3.40];` y, con un bucle `for`, calcula la suma total de sus elementos, guardándola en una variable `total` y mostrándola por consola al final del bucle (no en cada vuelta).

---

> 🔀 **Hasta aquí, JavaScript como lenguaje**: los puntos 1-5 son JavaScript puro, sin tocar ni una etiqueta HTML — y por muchas variables, condiciones y bucles que hayas escrito, **no estás aprendiendo a programar aplicaciones**: es lo justo para poder hacer lo que viene a partir de aquí. A partir de este punto, JavaScript entra en contacto con el HTML que ya conoces de otras unidades: primero lo integras en un documento (punto 6), y luego lo usas para leer y modificar ese documento — el DOM (puntos 7-10). Esta es la parte que hace que esta unidad sea LMSGI, y no una unidad de Programación.

## 6. Integrar JavaScript en un documento HTML

Igual que CSS (UD4), JavaScript se puede incluir de tres formas, con el mismo criterio de cuándo usar cada una:

| Forma | Cómo se escribe | Cuándo se usa |
|---|---|---|
| **En línea** | Atributo `onclick`, `onchange`... dentro de la etiqueta | Casi nunca en código real |
| **Interno** | Bloque `<script>` dentro del HTML | Pruebas rápidas, páginas aisladas |
| **Externo** | Archivo `.js` aparte, enlazado con `<script src="...">` | La forma normal de trabajar |

```html
<!-- index.html -->
<body>
  <h1>Mi página</h1>
  <script src="script.js"></script>
</body>
```
```javascript
// script.js
console.log("El script se ha cargado");
```

⚠️ **Dónde va el `<script>`**: casi siempre justo antes de cerrar `</body>`, no dentro de `<head>`. Si el `<script>` va en el `<head>`, se ejecuta antes de que el navegador haya construido el HTML que viene después, y cualquier intento de acceder a un elemento (punto 7) fallaría porque ese elemento todavía no existe.

**🧪 Ejercicio 6 — Tu primer script externo**
Crea `index.html` con un `<h1>` cualquiera y un archivo `script.js` enlazado justo antes de `</body>`. En el `.js`, escribe un `console.log()` con un mensaje. Ábrelo con Firefox y comprueba en la consola de desarrollador que el mensaje aparece. Después, mueve el `<script>` al `<head>` y explica qué diferencia notas (si alguna) en este caso tan simple, y por qué esa diferencia sí importaría en cuanto el script intente tocar el HTML.

---

## 7. El DOM: seleccionar y acceder a elementos

El **DOM** (*Document Object Model*) es la representación en memoria del HTML que JavaScript puede leer y modificar — cuando el navegador carga una página, convierte el HTML (texto) en una estructura de objetos organizados en árbol (el mismo tipo de estructura en árbol que ya viste con XML en la UD1). JavaScript no toca el archivo `.html` original: modifica esa representación en memoria, y el navegador redibuja la página al instante.

**Seleccionar elementos**, de más específico a más general:

```javascript
// Por id (siempre un único elemento, recuerda que el id es único)
const titulo = document.getElementById("titulo-principal");

// Por selector CSS (el mismo tipo de selector que ya conoces de la UD4) — devuelve el PRIMERO que coincide
const primerParrafo = document.querySelector("p");
const primeraTarjeta = document.querySelector(".tarjeta");

// Por selector CSS — devuelve TODOS los que coinciden, como una lista
const todasLasTarjetas = document.querySelectorAll(".tarjeta");
```

```html
<h1 id="titulo-principal">Panel de gastos</h1>
<p class="tarjeta">Alimentación</p>
<p class="tarjeta">Transporte</p>
```
```javascript
const titulo = document.getElementById("titulo-principal");
console.log(titulo.textContent);   // "Panel de gastos"

const tarjetas = document.querySelectorAll(".tarjeta");
console.log(tarjetas.length);      // 2
```

- `.textContent` lee (o escribe) el texto contenido dentro de un elemento.
- `document.querySelectorAll(...)` devuelve una lista (técnicamente un `NodeList`) que se puede recorrer con un bucle `for`, exactamente igual que un array del punto 5.

**🧪 Ejercicio 7 — Selecciona y muestra**
Crea un HTML con un `<h1 id="titulo">`, y una lista `<ul>` de 4 `<li class="modulo">` con el nombre de módulos que estés cursando. Con JavaScript, selecciona el `<h1>` por `id` y muéstralo por consola con `.textContent`; después selecciona todos los `<li class="modulo">` con `querySelectorAll` y, con un bucle `for`, muestra por consola el texto de cada uno.

---

## 8. Crear y modificar elementos

Además de leer, JavaScript puede **crear elementos nuevos** que no existían en el HTML original, y añadirlos al documento:

```javascript
// 1. Crear el elemento (todavía no está en la página)
const nuevoParrafo = document.createElement("p");

// 2. Darle contenido
nuevoParrafo.textContent = "Este párrafo lo ha creado JavaScript";
nuevoParrafo.classList.add("tarjeta");

// 3. Añadirlo al documento, dentro de otro elemento ya existente
const contenedor = document.getElementById("lista-gastos");
contenedor.appendChild(nuevoParrafo);
```

- `document.createElement("p")` crea el elemento en memoria, pero **no lo muestra** todavía — hasta que no se añade con `appendChild`, no aparece en la página.
- `.classList.add(...)` añade una clase CSS al elemento (existe también `.classList.remove(...)` y `.classList.toggle(...)`, que la quita si está y la pone si no está — muy usado para menús desplegables y modo oscuro).
- `.appendChild(...)` inserta el elemento nuevo como el último hijo del elemento sobre el que se llama.

**Modificar un elemento que ya existe** es más simple — solo hace falta seleccionarlo y cambiar sus propiedades:

```javascript
const titulo = document.getElementById("titulo-principal");
titulo.textContent = "Panel de gastos — actualizado";
titulo.style.color = "teal";
```

`.style.propiedad` cambia directamente una propiedad CSS del elemento, en el mismo formato que ya conoces — lo vemos con más detalle en el punto 10.

**🧪 Ejercicio 8 — Añadir gastos dinámicamente**
Sobre el HTML del Ejercicio 7 (o uno nuevo, con un `<div id="lista-gastos">` vacío), escribe un script que cree tres párrafos nuevos con `createElement`, les dé un texto distinto cada uno (por ejemplo, "Alimentación: 45€", "Transporte: 20€", "Ocio: 15€"), y los añada uno a uno dentro de `lista-gastos` con `appendChild`. Comprueba que aparecen en el navegador aunque no estuvieran escritos en el HTML original.

---

## 9. Eliminar elementos

```javascript
const elemento = document.getElementById("aviso-temporal");
elemento.remove();
```

`.remove()` quita el elemento del DOM directamente — es el método moderno y el que debes usar. Si el elemento no existe (por ejemplo, si `getElementById` no encontró nada y devolvió `null`), intentar llamar a `.remove()` sobre `null` daría un error — por eso es buena práctica comprobar antes:

```javascript
const elemento = document.getElementById("aviso-temporal");

if (elemento) {
  elemento.remove();
}
```

**Eliminar todos los elementos de una clase**, combinando lo visto en el punto 7 con un bucle:

```javascript
const avisos = document.querySelectorAll(".aviso");

avisos.forEach(function (aviso) {
  aviso.remove();
});
```

`.forEach(...)` es otra forma de recorrer una lista (alternativa al `for` del punto 5), pensada específicamente para "hacer algo con cada elemento" — aquí, eliminarlo uno a uno.

**🧪 Ejercicio 9 — Botón "Vaciar lista"**
Sobre el Ejercicio 8, añade un `<button id="vaciar">Vaciar lista</button>` en el HTML, y un `onclick` (puedes usar `document.getElementById("vaciar").onclick = function() {...}`) que, al pulsarlo, elimine todos los párrafos `.tarjeta` de `lista-gastos` con `querySelectorAll` + `.forEach` + `.remove()`.

---

## 10. Manipular estilos desde JavaScript

Ya has usado `.style.propiedad` en el punto 8 para cambiar una propiedad CSS puntual. Hay dos formas de tocar estilos desde JavaScript, y no son intercambiables:

| Forma | Qué hace | Cuándo usarla |
|---|---|---|
| `elemento.style.propiedad = "valor"` | Aplica un estilo **en línea**, directamente sobre ese elemento | Un cambio puntual, calculado en tiempo de ejecución (por ejemplo, una posición) |
| `elemento.classList.toggle("clase")` | Añade o quita una **clase** definida en tu CSS | Cambios de estado con un diseño ya preparado (activo/inactivo, abierto/cerrado, tema oscuro) |

```css
/* estilos.css */
.alerta {
  background-color: #fee2e2;
  border: 2px solid #dc2626;
}
```
```javascript
const tarjeta = document.querySelector(".tarjeta");

// Opción A: estilo en línea, propiedad a propiedad
tarjeta.style.backgroundColor = "#fee2e2";
tarjeta.style.border = "2px solid #dc2626";

// Opción B: activar una clase ya definida en el CSS (más mantenible)
tarjeta.classList.toggle("alerta");
```

⚠️ **Por qué la opción B suele ser mejor práctica**: con `classList.toggle`, todo el diseño (colores, bordes, tipografía) sigue viviendo en el archivo `.css`, donde corresponde — JavaScript solo decide **cuándo** aplicarlo, no **cómo** se ve. Mezclar demasiados `.style.propiedad` sueltos por el código JavaScript hace que, para cambiar un color, tengas que buscarlo en dos sitios distintos en vez de uno solo.

> 📡 **Por qué importa hoy**: esto es exactamente el mecanismo detrás de un interruptor de tema claro/oscuro — un botón que hace `document.documentElement.classList.toggle("tema-oscuro")`, y el resto lo resuelven las variables CSS que ya conoces de la UD4 (`:root { --color-fondo: white; } .tema-oscuro { --color-fondo: black; }`) — JavaScript decide el "cuándo", CSS decide el "cómo".

**🧪 Ejercicio 10 — Interruptor de aviso**
Añade un botón `<button id="alternar">Marcar como urgente</button>` junto a una tarjeta `<div class="tarjeta">Revisar presupuesto</div>`. Define en tu CSS una clase `.urgente` (fondo rojo claro, borde rojo). Con JavaScript, haz que al pulsar el botón se alterne (`classList.toggle`) la clase `.urgente` en la tarjeta — cada clic la activa si estaba desactivada, y la desactiva si estaba activada.

---

## 🎯 Reto de clase

Construye un pequeño gestor de tareas en una sola página: un `<input>` de texto, un botón "Añadir", y una lista vacía `<ul id="lista-tareas">`. Con JavaScript: (1) al pulsar "Añadir", crea un nuevo `<li>` con el texto del `<input>` y añádelo a la lista (usa lo visto en los puntos 7 y 8); (2) cada `<li>` debe tener también un botón "Completada" que, al pulsarlo, alterne una clase `.completada` (por ejemplo, texto tachado con `text-decoration: line-through` en tu CSS) sobre ese `<li>` en concreto; (3) cada `<li>` debe tener un botón "Eliminar" que lo quite de la lista (punto 9). Vacía el `<input>` después de añadir cada tarea.

*Variación evaluable*: pedir que, antes de añadir una tarea, se compruebe con un `if` que el `<input>` no esté vacío, y si lo está, se muestre un aviso en pantalla (creado dinámicamente con `createElement`) en vez de añadir una tarea sin texto.

---

<div style="page-break-after: always;"></div>

## Resumen de la unidad

**1. Qué es JavaScript** El lenguaje de programación que se ejecuta en el navegador y da comportamiento a una página ya cargada — HTML es estructura, CSS es presentación, JavaScript es comportamiento.

**2. Variables, tipos y literales** `let` (reasignable) y `const` (fijo); tipos básicos `Number`, `String`, `Boolean`, `undefined`, `null`; `typeof` para comprobar el tipo de un valor.

**3. Operadores y conversión de tipos** `===`/`!==` comparan valor y tipo (a diferencia de `==`/`!=`); `Number(...)` y `String(...)` convierten explícitamente entre tipos — imprescindible con datos leídos de formularios, que siempre llegan como texto.

**4. Decisiones** `if/else if/else` para condiciones; `switch` cuando hay muchos valores concretos que comparar contra la misma variable, sin olvidar el `break`.

**5. Bucles** `for` cuando se sabe de antemano cuántas repeticiones hacen falta (muy usado para recorrer arrays con `.length` y `[i]`); `while` cuando depende de una condición que se comprueba en cada vuelta.

**6. Integrar JavaScript en HTML** En línea, interno o externo (recomendado) — el `<script>` va justo antes de `</body>`, para que el HTML ya exista cuando el script intente acceder a él.

**7. El DOM: seleccionar elementos** El navegador convierte el HTML en una estructura en árbol que JavaScript puede leer y modificar — `getElementById`, `querySelector` (uno) y `querySelectorAll` (varios) son las formas básicas de seleccionar.

**8. Crear y modificar elementos** `createElement` + `.textContent`/`.classList.add` + `appendChild` para añadir elementos nuevos que no estaban en el HTML original; cambiar `.textContent` o `.style` de un elemento ya existente para modificarlo.

**9. Eliminar elementos** `.remove()` sobre el elemento seleccionado, comprobando antes que no sea `null`; `.forEach()` combinado con `querySelectorAll` para eliminar varios elementos a la vez.

**10. Manipular estilos desde JavaScript** `.style.propiedad` para un cambio puntual en línea; `.classList.toggle("clase")` para activar/desactivar un estilo ya definido en CSS — generalmente la práctica más mantenible, porque el diseño sigue viviendo en el `.css`.

---

## 📚 Para saber más (opcional, no evaluable)

Lo visto aquí es el fundamento de JavaScript y de la manipulación básica del DOM — con esto ya puedes construir interfaces que reaccionan sin recargar la página, la base de cualquier aplicación web moderna.

> 📡 **Actualidad**: además de manipular el DOM "a mano" como en esta unidad, hoy es muy habitual usar librerías o frameworks (React, Vue, Svelte...) que gestionan automáticamente cuándo y cómo actualizar el HTML a partir de los datos de la aplicación. No sustituyen lo aprendido aquí — por debajo siguen usando exactamente estos mismos mecanismos del DOM — pero cambian la forma de escribirlo, pensando en "datos que cambian" en vez de en "elementos que se crean y se borran a mano".

- Referencia completa de JavaScript (MDN, en español): https://developer.mozilla.org/es/docs/Web/JavaScript
- Manipulación del DOM (MDN): https://developer.mozilla.org/es/docs/Web/API/Document_Object_Model/Introduction
