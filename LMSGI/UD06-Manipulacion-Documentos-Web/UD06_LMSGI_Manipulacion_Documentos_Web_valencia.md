<div style="text-align: center;">

<img src="data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCA0MDAgNDAwIiB3aWR0aD0iMTgwIiBoZWlnaHQ9IjE4MCI+CiAgPGNpcmNsZSBjeD0iMjAwIiBjeT0iMjAwIiByPSIxNzAiIGZpbGw9IiNGMEZERkEiLz4KICA8Y2lyY2xlIGN4PSIyMDAiIGN5PSIyMDAiIHI9IjE3MCIgZmlsbD0ibm9uZSIgc3Ryb2tlPSIjOTlGNkU0IiBzdHJva2Utd2lkdGg9IjIiLz4KICA8Y2lyY2xlIGN4PSIyMDAiIGN5PSIxMzAiIHI9IjI0IiBmaWxsPSJub25lIiBzdHJva2U9IiMwRjc2NkUiIHN0cm9rZS13aWR0aD0iOSIvPgogIDxjaXJjbGUgY3g9IjE0MCIgY3k9IjI1MCIgcj0iMjQiIGZpbGw9Im5vbmUiIHN0cm9rZT0iIzBGNzY2RSIgc3Ryb2tlLXdpZHRoPSI5IiBvcGFjaXR5PSIwLjc1Ii8+CiAgPGNpcmNsZSBjeD0iMjYwIiBjeT0iMjUwIiByPSIyNCIgZmlsbD0ibm9uZSIgc3Ryb2tlPSIjMEY3NjZFIiBzdHJva2Utd2lkdGg9IjkiIG9wYWNpdHk9IjAuNzUiLz4KICA8bGluZSB4MT0iMjAwIiB5MT0iMTU0IiB4Mj0iMTQwIiB5Mj0iMjI2IiBzdHJva2U9IiMwRjc2NkUiIHN0cm9rZS13aWR0aD0iOCIvPgogIDxsaW5lIHgxPSIyMDAiIHkxPSIxNTQiIHgyPSIyNjAiIHkyPSIyMjYiIHN0cm9rZT0iIzBGNzY2RSIgc3Ryb2tlLXdpZHRoPSI4Ii8+CiAgPGxpbmUgeDE9IjE0MCIgeTE9IjI1MCIgeDI9IjI2MCIgeTI9IjI1MCIgc3Ryb2tlPSIjMEY3NjZFIiBzdHJva2Utd2lkdGg9IjgiIG9wYWNpdHk9IjAuNSIvPgo8L3N2Zz4K" width="180" alt="Logotip LMSGI"/>

<h1>Unitat 6</h1>
<h2>Manipulació de documents web</h2>

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

1. Què és JavaScript i on s'executa
2. Variables, tipus de dades i literals
3. Operadors i conversions entre tipus
4. Decisions: estructures condicionals
5. Bucles: repetir instruccions
6. Integrar JavaScript en un document HTML
7. El DOM: seleccionar i accedir a elements
8. Crear i modificar elements
9. Eliminar elements
10. Manipular estils des de JavaScript
11. Resum de la unitat
12. Per a saber-ne més

<div style="page-break-after: always;"></div>

**RA cobert:** RA2 (ASIX, CA 2f) / RA3 (DAW, CA 3a-3f) — *utilitza llenguatges de marques per a la transmissió i presentació d'informació a través de la web* / *accedix i manipula documents web utilitzant llenguatges de script de client*

> 💡 **Nota d'estudi**: esta unitat té dos meitats ben diferenciades. En la primera (punts 1-5) aprens **JavaScript com a llenguatge**: variables, tipus, operadors, condicions i bucles — sense tocar encara ni una etiqueta HTML. En la segona (punts 6-10) uses eixe mateix JavaScript per a **manipular l'HTML que ja coneixes**: seleccionar, crear, modificar i eliminar elements d'una pàgina. Si algun concepte de la primera meitat ja et sona d'altres assignatures, pots anar més ràpid — però no et salte el punt 6 en avant, és on JavaScript es connecta amb tot el vist en LMSGI fins ara.

---

## 1. Què és JavaScript i on s'executa

Tot el que has escrit fins ara en este mòdul és **declaratiu**: HTML descriu què és cada cosa, CSS descriu com es veu. Cap dels dos té variables, bucles ni decisions — no són llenguatges de programació, com ja es va deixar clar en la UD1. **JavaScript** sí que ho és: és el llenguatge de programació que s'executa en el navegador i permet que una pàgina **reaccione i canvie** després d'haver-se carregat, sense necessitar recarregar-la.

```
HTML  → què és cada cosa (estructura)
CSS   → com es veu (presentació)
JS    → què passa quan alguna cosa ocorre (comportament)
```

Un exemple que ja coneixes sense saber-ho: quan passes el ratolí sobre un botó i canvia de color amb `:hover` (UD4), açò és CSS pur, sense JavaScript. Però si en **fer clic** en eixe botó apareix un missatge, es valida un formulari, o s'afig una fila a una taula sense recarregar la pàgina — açò només ho fa JavaScript.

JavaScript s'executa directament en el navegador de qui visita la pàgina (per això se li diu **llenguatge de script de client**), sense necessitar instal·lar res ni compilar res — el mateix navegador inclou l'intèrpret que llig i executa el codi línia a línia.

> 🕰️ **Un nom enganyós**: malgrat el nom, JavaScript no té relació tècnica amb el llenguatge de programació Java — es va nomenar així en 1995 per una decisió de màrqueting de Netscape, quan Java estava de moda. Són dos llenguatges completament distints, amb sintaxi, usos i execució diferents.

**🧪 Exercici 1 — HTML, CSS o JavaScript**
Per a cadascun d'estos comportaments d'una web, indica si depén d'HTML, de CSS o de JavaScript, raonant la teua resposta: (a) un títol es veu en negreta; (b) en escriure en un camp de formulari buit i prémer "Enviar", apareix un missatge d'error sense recarregar la pàgina; (c) un paràgraf conté una llista de tres elements; (d) un menú lateral es desplega en fer clic en un botó.

---

## 2. Variables, tipus de dades i literals

Una **variable** guarda un valor amb un nom, per a poder usar-lo i canviar-lo més avant. En JavaScript modern es declaren amb `let` (si el valor va a canviar) o `const` (si no va a canviar mai):

```javascript
let nombre = "Marta";
let edad = 16;
const modulo = "LMSGI";

edad = 17; // "let" permet reassignar
// modulo = "EDE"; // açò donaria error: "const" no es pot reassignar
```

Un **literal** és el valor escrit directament en el codi (`"Marta"`, `16`) — la forma més simple de dada, sense necessitar càlculs ni variables prèvies.

**Tipus de dades bàsics:**

| Tipus | Què guarda | Exemple |
|---|---|---|
| `Number` | Nombres, enters o decimals, sense distinció de tipus | `16`, `3.5`, `-2` |
| `String` | Text, entre cometes simples, dobles o invertides | `"Marta"`, `'LMSGI'`, `` `plantilla` `` |
| `Boolean` | Vertader o fals | `true`, `false` |
| `undefined` | Una variable declarada però sense valor assignat | `let x;` |
| `null` | Absència de valor, assignada explícitament | `let x = null;` |

```javascript
console.log(typeof 16);        // "number"
console.log(typeof "Marta");   // "string"
console.log(typeof true);      // "boolean"
```

`console.log()` és la forma més bàsica de vore un resultat sense necessitar encara HTML — imprimix el valor en la **consola** del navegador (en Firefox: menú → Més ferramentes → Ferramentes de desenvolupament web → pestanya Consola, o la tecla `F12`).

⚠️ **Àmbit d'una variable**: on és "visible" eixa variable dins del codi. Una variable declarada amb `let`/`const` dins d'un bloc `{ }` (per exemple, dins d'un bucle o una condició) només existix dins d'eixe bloc — fora d'ell, no es pot usar. Ho voràs en la pràctica en els punts 4 i 5, en treballar amb condicions i bucles.

**🧪 Exercici 2 — Variables de la teua pròpia classe**
Obri la consola de Firefox i declara 4 variables: el teu nom (`String`), la teua edat (`Number`), si estàs matriculat en el mòdul (`Boolean`) i una variable sense valor assignat encara (`undefined`). Usa `console.log(typeof ...)` amb cadascuna per a comprovar el seu tipus, i anota el resultat.

---

## 3. Operadors i conversions entre tipus

**Operadors aritmètics**: `+`, `-`, `*`, `/`, `%` (resta d'una divisió). **Operadors de comparació**: `===` (igual estricte, compara valor **i** tipus — el que has d'usar quasi sempre), `!==` (distint estricte), `<`, `>`, `<=`, `>=`. **Operadors lògics**: `&&` (I), `||` (O), `!` (NO).

```javascript
let a = 10;
let b = "10";

console.log(a === b);   // false — mateix valor, però distint tipus (Number vs String)
console.log(a == b);    // true  — "==" convertix el tipus abans de comparar, per això dóna igual
```

⚠️ **`===` enfront de `==`**: `==` compara el valor després de convertir automàticament els tipus, la qual cosa pot donar resultats poc intuïtius (`"10" == 10` és `true`). `===` compara valor **i** tipus sense convertir res. Usa sempre `===`, tret que tingues una raó concreta per al contrari — és una de les fonts d'errors més comunes en JavaScript per a qui comença.

**Conversió de tipus**: de vegades necessites convertir explícitament, per exemple, un text llegit d'un formulari a nombre per a poder operar amb ell:

```javascript
let texto = "25";
let numero = Number(texto);      // 25 (tipus Number)
console.log(numero + 5);         // 30

let n = 42;
let cadena = String(n);          // "42" (tipus String)
console.log(cadena + "5");       // "425" (concatenació de text, no suma)
```

> 📡 **Per què importa hui**: quan llegisques el valor d'un `<input>` amb JavaScript (ho voràs en el punt 7), eixe valor **sempre** arriba com a `String`, encara que l'usuari haja escrit només nombres — `Number(...)` és el pas que necessitaràs quasi sempre abans de fer qualsevol càlcul amb dades d'un formulari.

**🧪 Exercici 3 — L'error clàssic de sumar text**
En la consola, declara `let a = "5"` i `let b = "3"`. Calcula `a + b` i anota què obtens — una suma numèrica o una concatenació de text? Corrigix-ho usant `Number()` perquè el resultat siga realment `8`. Explica amb les teues paraules per què ocorre açò.

---

## 4. Decisions: estructures condicionals

L'estructura `if / else` executa un bloc de codi només si es complix una condició:

```javascript
let edad = 16;

if (edad >= 18) {
  console.log("Ets major d'edat");
} else {
  console.log("Ets menor d'edat");
}
```

Amb diverses condicions encadenades, `else if`:

```javascript
let nota = 6;

if (nota >= 9) {
  console.log("Excel·lent");
} else if (nota >= 7) {
  console.log("Notable");
} else if (nota >= 5) {
  console.log("Aprovat");
} else {
  console.log("Suspés");
}
```

Quan hi ha molts valors concrets a comparar contra una mateixa variable, `switch` sol ser més llegible que una cadena llarga de `else if`:

```javascript
let dia = "lunes";

switch (dia) {
  case "sabado":
  case "domingo":
    console.log("Cap de setmana");
    break;
  default:
    console.log("Dia laborable");
}
```

⚠️ **El `break` no és opcional**: sense ell, l'execució "cau" al `case` següent encara que no coincidisca — un error molt comú en començar amb `switch`.

**🧪 Exercici 4 — Qualificador de notes**
Escriu una funció (pots usar `if/else if` o `switch`, a la teua elecció) que, donada una variable `nota` amb un nombre del 0 al 10, mostre per consola: "Excel·lent" (9-10), "Notable" (7-8), "Bé" (6), "Aprovat" (5), "Suspés" (0-4). Prova-la amb almenys 4 valors distints.

---

## 5. Bucles: repetir instruccions

Un **bucle** repetix un bloc de codi mentre es complisca una condició, sense haver de copiar-lo a mà.

```javascript
// for: quan saps per endavant quantes vegades repetir
for (let i = 1; i <= 5; i++) {
  console.log("Repetición número " + i);
}
```

- `let i = 1`: valor inicial del comptador.
- `i <= 5`: condició — el bucle seguix mentre siga `true`.
- `i++`: què li passa al comptador en cada volta (equival a `i = i + 1`).

```javascript
// while: quan no saps per endavant quantes vegades, depén d'una condició
let intentos = 0;
let acertado = false;

while (!acertado && intentos < 3) {
  intentos++;
  console.log("Intento número " + intentos);
  // ací aniria la comprovació real que decidix "acertado"
}
```

**Recórrer una llista de valors** (un *array*, l'estructura per a guardar diversos valors davall un mateix nom) és un dels usos més habituals de `for`:

```javascript
let modulos = ["LMSGI", "EDE", "Programación"];

for (let i = 0; i < modulos.length; i++) {
  console.log(modulos[i]);
}
```

`modulos.length` dóna el nombre d'elements de l'array, i `modulos[i]` accedix a l'element en la posició `i` (recorda: les posicions comencen en `0`, no en `1`).

**🧪 Exercici 5 — Suma d'una llista**
Declara un array `let precios = [12.50, 8.90, 25.00, 3.40];` i, amb un bucle `for`, calcula la suma total dels seus elements, guardant-la en una variable `total` i mostrant-la per consola al final del bucle (no en cada volta).

---

> 🔀 **Fins ací, JavaScript com a llenguatge**: els punts 1-5 són JavaScript pur, sense tocar ni una etiqueta HTML — i per moltes variables, condicions i bucles que hages escrit, **no estàs aprenent a programar aplicacions**: és el just per a poder fer el que ve a partir d'ací. A partir d'este punt, JavaScript entra en contacte amb l'HTML que ja coneixes d'altres unitats: primer l'integres en un document (punt 6), i després l'uses per a llegir i modificar eixe document — el DOM (punts 7-10). Esta és la part que fa que esta unitat siga LMSGI, i no una unitat de Programació.

## 6. Integrar JavaScript en un document HTML

Igual que CSS (UD4), JavaScript es pot incloure de tres formes, amb el mateix criteri de quan usar cadascuna:

| Forma | Com s'escriu | Quan s'usa |
|---|---|---|
| **En línia** | Atribut `onclick`, `onchange`... dins de l'etiqueta | Quasi mai en codi real |
| **Intern** | Bloc `<script>` dins de l'HTML | Proves ràpides, pàgines aïllades |
| **Extern** | Arxiu `.js` a banda, enllaçat amb `<script src="...">` | La forma normal de treballar |

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

⚠️ **On va el `<script>`**: quasi sempre just abans de tancar `</body>`, no dins de `<head>`. Si el `<script>` va en el `<head>`, s'executa abans que el navegador haja construït l'HTML que ve després, i qualsevol intent d'accedir a un element (punt 7) fallaria perquè eixe element encara no existix.

**🧪 Exercici 6 — El teu primer script extern**
Crea `index.html` amb un `<h1>` qualsevol i un arxiu `script.js` enllaçat just abans de `</body>`. En el `.js`, escriu un `console.log()` amb un missatge. Obri'l amb Firefox i comprova en la consola de desenvolupador que el missatge apareix. Després, mou el `<script>` al `<head>` i explica quina diferència notes (si alguna) en este cas tan simple, i per què eixa diferència sí que importaria en el moment en què l'script intente tocar l'HTML.

---

## 7. El DOM: seleccionar i accedir a elements

El **DOM** (*Document Object Model*) és la representació en memòria de l'HTML que JavaScript pot llegir i modificar — quan el navegador carrega una pàgina, convertix l'HTML (text) en una estructura d'objectes organitzats en arbre (el mateix tipus d'estructura en arbre que ja vas vore amb XML en la UD1). JavaScript no toca l'arxiu `.html` original: modifica eixa representació en memòria, i el navegador redibuixa la pàgina a l'instant.

**Seleccionar elements**, de més específic a més general:

```javascript
// Per id (sempre un únic element, recorda que l'id és únic)
const titulo = document.getElementById("titulo-principal");

// Per selector CSS (el mateix tipus de selector que ja coneixes de la UD4) — retorna el PRIMER que coincidix
const primerParrafo = document.querySelector("p");
const primeraTarjeta = document.querySelector(".tarjeta");

// Per selector CSS — retorna TOTS els que coincidixen, com una llista
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

- `.textContent` llig (o escriu) el text contingut dins d'un element.
- `document.querySelectorAll(...)` retorna una llista (tècnicament un `NodeList`) que es pot recórrer amb un bucle `for`, exactament igual que un array del punt 5.

**🧪 Exercici 7 — Selecciona i mostra**
Crea un HTML amb un `<h1 id="titulo">`, i una llista `<ul>` de 4 `<li class="modulo">` amb el nom de mòduls que estigues cursant. Amb JavaScript, selecciona l'`<h1>` per `id` i mostra'l per consola amb `.textContent`; després selecciona tots els `<li class="modulo">` amb `querySelectorAll` i, amb un bucle `for`, mostra per consola el text de cadascun.

---

## 8. Crear i modificar elements

A més de llegir, JavaScript pot **crear elements nous** que no existien en l'HTML original, i afegir-los al document:

```javascript
// 1. Crear l'element (encara no està en la pàgina)
const nuevoParrafo = document.createElement("p");

// 2. Donar-li contingut
nuevoParrafo.textContent = "Este párrafo lo ha creado JavaScript";
nuevoParrafo.classList.add("tarjeta");

// 3. Afegir-lo al document, dins d'un altre element ja existent
const contenedor = document.getElementById("lista-gastos");
contenedor.appendChild(nuevoParrafo);
```

- `document.createElement("p")` crea l'element en memòria, però **no el mostra** encara — fins que no s'afig amb `appendChild`, no apareix en la pàgina.
- `.classList.add(...)` afig una classe CSS a l'element (existix també `.classList.remove(...)` i `.classList.toggle(...)`, que la lleva si està i la posa si no està — molt usat per a menús desplegables i mode fosc).
- `.appendChild(...)` insereix l'element nou com l'últim fill de l'element sobre el qual es crida.

**Modificar un element que ja existix** és més simple — només cal seleccionar-lo i canviar les seues propietats:

```javascript
const titulo = document.getElementById("titulo-principal");
titulo.textContent = "Panel de gastos — actualizado";
titulo.style.color = "teal";
```

`.style.propiedad` canvia directament una propietat CSS de l'element, en el mateix format que ja coneixes — ho veiem amb més detall en el punt 10.

**🧪 Exercici 8 — Afegir despeses dinàmicament**
Sobre l'HTML de l'Exercici 7 (o un de nou, amb un `<div id="lista-gastos">` buit), escriu un script que cree tres paràgrafs nous amb `createElement`, els done un text distint a cadascun (per exemple, "Alimentación: 45€", "Transporte: 20€", "Ocio: 15€"), i els afig un a un dins de `lista-gastos` amb `appendChild`. Comprova que apareixen en el navegador encara que no estigueren escrits en l'HTML original.

---

## 9. Eliminar elements

```javascript
const elemento = document.getElementById("aviso-temporal");
elemento.remove();
```

`.remove()` lleva l'element del DOM directament — és el mètode modern i el que has d'usar. Si l'element no existix (per exemple, si `getElementById` no va trobar res i va retornar `null`), intentar cridar a `.remove()` sobre `null` donaria un error — per això és bona pràctica comprovar abans:

```javascript
const elemento = document.getElementById("aviso-temporal");

if (elemento) {
  elemento.remove();
}
```

**Eliminar tots els elements d'una classe**, combinant el vist en el punt 7 amb un bucle:

```javascript
const avisos = document.querySelectorAll(".aviso");

avisos.forEach(function (aviso) {
  aviso.remove();
});
```

`.forEach(...)` és una altra forma de recórrer una llista (alternativa al `for` del punt 5), pensada específicament per a "fer alguna cosa amb cada element" — ací, eliminar-lo un a un.

**🧪 Exercici 9 — Botó "Buidar llista"**
Sobre l'Exercici 8, afig un `<button id="vaciar">Vaciar lista</button>` en l'HTML, i un `onclick` (pots usar `document.getElementById("vaciar").onclick = function() {...}`) que, en prémer-lo, elimine tots els paràgrafs `.tarjeta` de `lista-gastos` amb `querySelectorAll` + `.forEach` + `.remove()`.

---

## 10. Manipular estils des de JavaScript

Ja has usat `.style.propiedad` en el punt 8 per a canviar una propietat CSS puntual. Hi ha dos formes de tocar estils des de JavaScript, i no són intercanviables:

| Forma | Què fa | Quan usar-la |
|---|---|---|
| `elemento.style.propiedad = "valor"` | Aplica un estil **en línia**, directament sobre eixe element | Un canvi puntual, calculat en temps d'execució (per exemple, una posició) |
| `elemento.classList.toggle("clase")` | Afig o lleva una **classe** definida en el teu CSS | Canvis d'estat amb un disseny ja preparat (actiu/inactiu, obert/tancat, tema fosc) |

```css
/* estilos.css */
.alerta {
  background-color: #fee2e2;
  border: 2px solid #dc2626;
}
```
```javascript
const tarjeta = document.querySelector(".tarjeta");

// Opció A: estil en línia, propietat a propietat
tarjeta.style.backgroundColor = "#fee2e2";
tarjeta.style.border = "2px solid #dc2626";

// Opció B: activar una classe ja definida en el CSS (més mantenible)
tarjeta.classList.toggle("alerta");
```

⚠️ **Per què l'opció B sol ser millor pràctica**: amb `classList.toggle`, tot el disseny (colors, vores, tipografia) seguix vivint en l'arxiu `.css`, on correspon — JavaScript només decidix **quan** aplicar-ho, no **com** es veu. Mesclar massa `.style.propiedad` solts pel codi JavaScript fa que, per a canviar un color, hages de buscar-lo en dos llocs distints en lloc d'un sol.

> 📡 **Per què importa hui**: açò és exactament el mecanisme darrere d'un interruptor de tema clar/fosc — un botó que fa `document.documentElement.classList.toggle("tema-oscuro")`, i la resta ho resolen les variables CSS que ja coneixes de la UD4 (`:root { --color-fondo: white; } .tema-oscuro { --color-fondo: black; }`) — JavaScript decidix el "quan", CSS decidix el "com".

**🧪 Exercici 10 — Interruptor d'avís**
Afig un botó `<button id="alternar">Marcar como urgente</button>` junt a una targeta `<div class="tarjeta">Revisar presupuesto</div>`. Definix en el teu CSS una classe `.urgente` (fons roig clar, vora roja). Amb JavaScript, fes que en prémer el botó s'alterne (`classList.toggle`) la classe `.urgente` en la targeta — cada clic l'activa si estava desactivada, i la desactiva si estava activada.

---

## 🎯 Repte de classe

Construïx un xicotet gestor de tasques en una sola pàgina: un `<input>` de text, un botó "Añadir", i una llista buida `<ul id="lista-tareas">`. Amb JavaScript: (1) en prémer "Añadir", crea un nou `<li>` amb el text de l'`<input>` i afig-lo a la llista (usa el vist en els punts 7 i 8); (2) cada `<li>` ha de tindre també un botó "Completada" que, en prémer-lo, alterne una classe `.completada` (per exemple, text ratllat amb `text-decoration: line-through` en el teu CSS) sobre eixe `<li>` en concret; (3) cada `<li>` ha de tindre un botó "Eliminar" que el lleve de la llista (punt 9). Buida l'`<input>` després d'afegir cada tasca.

*Variació avaluable*: demanar que, abans d'afegir una tasca, es comprove amb un `if` que l'`<input>` no estiga buit, i si ho està, es mostre un avís en pantalla (creat dinàmicament amb `createElement`) en lloc d'afegir una tasca sense text.

---

<div style="page-break-after: always;"></div>

## Resum de la unitat

**1. Què és JavaScript** El llenguatge de programació que s'executa en el navegador i dóna comportament a una pàgina ja carregada — HTML és estructura, CSS és presentació, JavaScript és comportament.

**2. Variables, tipus i literals** `let` (reassignable) i `const` (fix); tipus bàsics `Number`, `String`, `Boolean`, `undefined`, `null`; `typeof` per a comprovar el tipus d'un valor.

**3. Operadors i conversió de tipus** `===`/`!==` comparen valor i tipus (a diferència de `==`/`!=`); `Number(...)` i `String(...)` convertixen explícitament entre tipus — imprescindible amb dades llegides de formularis, que sempre arriben com a text.

**4. Decisions** `if/else if/else` per a condicions; `switch` quan hi ha molts valors concrets a comparar contra la mateixa variable, sense oblidar el `break`.

**5. Bucles** `for` quan se sap per endavant quantes repeticions calen (molt usat per a recórrer arrays amb `.length` i `[i]`); `while` quan depén d'una condició que es comprova en cada volta.

**6. Integrar JavaScript en HTML** En línia, intern o extern (recomanat) — el `<script>` va just abans de `</body>`, perquè l'HTML ja existisca quan l'script intente accedir-hi.

**7. El DOM: seleccionar elements** El navegador convertix l'HTML en una estructura en arbre que JavaScript pot llegir i modificar — `getElementById`, `querySelector` (un) i `querySelectorAll` (diversos) són les formes bàsiques de seleccionar.

**8. Crear i modificar elements** `createElement` + `.textContent`/`.classList.add` + `appendChild` per a afegir elements nous que no estaven en l'HTML original; canviar `.textContent` o `.style` d'un element ja existent per a modificar-lo.

**9. Eliminar elements** `.remove()` sobre l'element seleccionat, comprovant abans que no siga `null`; `.forEach()` combinat amb `querySelectorAll` per a eliminar diversos elements alhora.

**10. Manipular estils des de JavaScript** `.style.propiedad` per a un canvi puntual en línia; `.classList.toggle("clase")` per a activar/desactivar un estil ja definit en CSS — generalment la pràctica més mantenible, perquè el disseny seguix vivint en el `.css`.

---

## 📚 Per a saber-ne més (opcional, no avaluable)

El vist ací és el fonament de JavaScript i de la manipulació bàsica del DOM — amb açò ja pots construir interfícies que reaccionen sense recarregar la pàgina, la base de qualsevol aplicació web moderna.

> 📡 **Actualitat**: a més de manipular el DOM "a mà" com en esta unitat, hui és molt habitual usar llibreries o frameworks (React, Vue, Svelte...) que gestionen automàticament quan i com actualitzar l'HTML a partir de les dades de l'aplicació. No substituïxen l'apres ací — per davall seguixen usant exactament estos mateixos mecanismes del DOM — però canvien la forma d'escriure-ho, pensant en "dades que canvien" en lloc de en "elements que es creen i s'esborren a mà".

- Referència completa de JavaScript (MDN, en espanyol): https://developer.mozilla.org/es/docs/Web/JavaScript
- Manipulació del DOM (MDN): https://developer.mozilla.org/es/docs/Web/API/Document_Object_Model/Introduction
</content>
