<div style="text-align: center;">

<img src="data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCA0MDAgNDAwIiB3aWR0aD0iMTgwIiBoZWlnaHQ9IjE4MCI+CiAgPGNpcmNsZSBjeD0iMjAwIiBjeT0iMjAwIiByPSIxNzAiIGZpbGw9IiNGMEZERkEiLz4KICA8Y2lyY2xlIGN4PSIyMDAiIGN5PSIyMDAiIHI9IjE3MCIgZmlsbD0ibm9uZSIgc3Ryb2tlPSIjOTlGNkU0IiBzdHJva2Utd2lkdGg9IjIiLz4KICA8dGV4dCB4PSIyMDAiIHk9IjI0OCIgZm9udC1mYW1pbHk9IidDb3VyaWVyIE5ldycsIENvdXJpZXIsIG1vbm9zcGFjZSIgZm9udC1zaXplPSIxNTAiIGZvbnQtd2VpZ2h0PSI3MDAiIGZpbGw9IiMwRjc2NkUiIHRleHQtYW5jaG9yPSJtaWRkbGUiPiZndDtfPC90ZXh0Pgo8L3N2Zz4K" width="180" alt="Logotip EDE"/>

<h1>Unitat 2</h1>
<h2>Entorns de desenvolupament</h2>

<p>
<strong>Mòdul:</strong> Entorns de Desenvolupament (EDE)<br>
<strong>Cicle formatiu:</strong> 1r DAW (Desenvolupament d'Aplicacions Web)<br>
<strong>Curs:</strong> 2026-2027
</p>

<p>
<strong>Docent:</strong> Noel Marco Biendicho<br>
<strong>Centre:</strong> IES Sant Vicent Ferrer — Algemesí
</p>

</div>

<div style="page-break-after: always;"></div>

## Índex

1. L'entorn de desenvolupament: instal·lació i primers passos (CA 2a)
2. Personalització, automatització i actualització de l'entorn (CA 2b, 2c, 2d)
3. Generació d'executables en diferents entorns (CA 2e, 2f)
4. Comparació d'entorns de desenvolupament (CA 2g)
5. Repte de classe
6. Resum de la unitat
7. Per a saber-ne més

<div style="page-break-after: always;"></div>

**RA cobert:** RA2 (CA 2a-2g) — Avalua entorns integrats de desenvolupament, analitzant les seues característiques per a editar codi font i generar executables.

> 💡 **Nota d'estudi**: en UD1 vam classificar les eines de desenvolupament per damunt (IDE, compilador, control de versions...); esta unitat es fica de ple en una sola d'eixes categories — l'IDE — per a instal·lar-lo, configurar-lo a fons i comparar-lo amb alternatives. VS Codium, que ja uses des d'UD1, deixa de ser "la carpeta on escric codi" i passa a ser un entorn que saps instal·lar, personalitzar i avaluar amb criteri.

> 💻 **Com treballar els exercicis d'esta unitat**: seguix usant la teua carpeta `UD02_ElTeuNom` en VS Codium. Quan un exercici demane instal·lar, configurar o comparar, documenta el procés en un fitxer Markdown (`exerciciN.md`) — captures de pantalla incloses si el teu professor ho demana — en compte de només "fer-ho i prou".

## 🎯 Conceptes clau

En acabar esta unitat sabràs:
- Instal·lar, personalitzar i actualitzar un entorn de desenvolupament, distingint software propietari de software lliure.
- Generar executables a partir del mateix codi font en distints llenguatges i en distints entorns, dins i fora del teu equip.
- Comparar entorns de desenvolupament amb criteri tècnic (no només "quin m'agrada més"), identificant què tenen en comú i què els distingix.

---

## 1. L'entorn de desenvolupament: instal·lació i primers passos (CA 2a)

### 1.1. Què aporta un IDE (repàs ràpid d'UD1)

En UD1 (punt 7.1) ja vam veure que un **IDE** (*Integrated Development Environment*) afig sobre un editor de text simple: autocompletat, ressaltat de sintaxi, detecció d'errors mentre escrius i depuració incorporada. Esta unitat no repetix eixa teoria — la posa en pràctica: instal·lar, configurar i traure-li partit a un de veritat.

| Sense IDE (editor de text simple) | Amb IDE |
|---|---|
| Sense avisos fins a executar el programa | Errors marcats mentre escrius |
| Copiar/enganxar noms de variables i funcions | Autocompletat, "anar a la definició" |
| Executar i depurar des d'una terminal a banda | Execució i depuració integrades |
| Cap ajuda amb el format del codi | Formatatge automàtic, ressaltat de sintaxi |

### 1.2. Software propietari i software lliure: el mateix IDE, dos camins

**Propietari** significa que el fabricant controla el codi font i les condicions d'ús (encara que el programa siga gratuït); **lliure** significa que el codi és públic i qualsevol pot modificar-lo i redistribuir-lo, sota una llicència que ho garantix. No són sinònims de "de pagament" i "gratis": hi ha software propietari gratuït, i software lliure que es ven com a servei.

L'exemple més pròxim el tens ja instal·lat en el teu equip:

| | **Visual Studio Code** | **VS Codium** |
|---|---|---|
| Codi font | El mateix (projecte `code-oss`, codi obert) | El mateix (projecte `code-oss`, codi obert) |
| Compilació final | La fa Microsoft, i afig telemetria i marca pròpia propietària abans de distribuir-la | La fa la comunitat, sense telemetria ni marques de Microsoft |
| Llicència del binari final | Propietària (EULA de Microsoft) | Lliure (MIT) |
| Extensions des del Marketplace de Microsoft | Sí | No directament (usa Open VSX, un catàleg alternatiu) |

⚠️ **El cas més instructiu possible**: no són "dos programes distints que competixen" — és el mateix codi font, compilat de dos formes distintes, amb dos llicències distintes com a resultat. Per això portes des d'UD1 usant la versió lliure sense perdre cap funció essencial.

**🧪 Exercici 1 — Verifica i documenta la teua instal·lació**
Obri VS Codium i comprova la versió instal·lada (`Ajuda → Quant a`, o `Help → About`). En `exercici1.md`, dins de la teua carpeta `UD02`, indica: (a) la versió exacta que tens; (b) si la teua instal·lació usa el Marketplace de Microsoft o Open VSX per a les extensions (comprova-ho obrint la pestanya d'Extensions i mirant d'on s'instal·len); (c) amb les teues paraules, per què VS Code i VS Codium comparteixen codi però no llicència.

### 1.3. Ús bàsic i edició de programes

Abans de personalitzar res, convé dominar el bàsic: crear i organitzar una **carpeta de projecte** (*workspace*), moure's entre fitxers amb l'explorador lateral i amb la drecera d'"anar a fitxer" (`Ctrl+P`), i usar la terminal integrada sense eixir de l'IDE — tot açò ja ho vens fent des d'UD1 sense anomenar-ho com a tal.

El nou en esta unitat és mirar-ho des de l'altre costat: no només usar l'IDE, sinó **decidir amb criteri** com l'instal·les, el configures i el compares — que és exactament el que ve a continuació.

> 🧯 **Pla B si la instal·lació falla a classe**: si el teu equip no té VS Codium instal·lat i no pots instal·lar-lo (falta de permisos, sense connexió), usa **vscode.dev** (la versió de VS Code que corre sencera en el navegador, sense instal·lar res) per a seguir la resta de la unitat — és el mateix editor, amb menys funcions de sistema (no executa codi directament), però suficient per als exercicis de personalització. Si disposes de la VM portàtil del cicle, VS Codium ja ve preinstal·lat ahí.

---

## 2. Personalització, automatització i actualització de l'entorn (CA 2b, 2c, 2d)

### 2.1. Mòduls i extensions

Un IDE acabat d'instal·lar fa poc més que un editor de text avançat — el seu veritable potencial arriba amb **extensions**: mòduls que afigen suport per a un llenguatge, un formatador, un linter, temes visuals, o integració amb ferramentes externes.

```
Extensions que probablement ja tens actives des d'UD1:
- Python (suport de llenguatge, IntelliSense, depurador)
- Code Runner (executar un fitxer amb un sol botó)
```

| Acció | Com es fa en VS Codium |
|---|---|
| Instal·lar una extensió | Panell d'Extensions (`Ctrl+Shift+X`) → buscar → Instal·lar |
| Veure què tens instal·lat | Mateix panell, pestanya "Instal·lades" |
| Eliminar una extensió | Botó d'engranatge sobre l'extensió → Desinstal·lar |
| Deshabilitar sense desinstal·lar | Botó d'engranatge → Deshabilitar (útil per a aïllar si una extensió dona problemes) |

### 2.2. Personalització visual i d'estil de codificació

Més enllà de les extensions, el mateix IDE s'adapta a com treballes:

- **Tema**: combinació de colors de l'editor (fosc, clar, alt contrast). `Ctrl+K Ctrl+T` en VS Codium.
- **Estil de codificació**: grandària del sagnat (espais vs tabulacions), longitud de línia, formatatge automàtic en guardar — configurable per llenguatge, no només de forma global.
- **Dreceres de teclat**: personalitzables una a una o per perfils complets (per exemple, imitant les dreceres d'un altre editor).

```json
// settings.json — un fragment típic de configuració personal
{
    "editor.tabSize": 4,
    "editor.formatOnSave": true,
    "workbench.colorTheme": "Default Dark Modern",
    "files.autoSave": "afterDelay"
}
```

> 📡 **Per què importa hui**: quan més avant treballes en equip (control de versions, UP3), un estil de codificació compartit entre l'equip evita que cada `commit` canvie centenars de línies només per diferències d'indentació — molts projectes reals fixen esta configuració en un fitxer compartit (`.editorconfig`) perquè no depenga de la configuració personal de cada desenvolupador.

### 2.3. Automatització amb tasques i fragments de codi

Un IDE també automatitza el repetitiu:

| Ferramenta | Què automatitza | Exemple |
|---|---|---|
| **Tasques** (*tasks*) | Executar una orde o seqüència d'ordes amb una drecera, en compte d'escriure-les a mà cada vegada | Compilar i executar amb una sola acció |
| **Fragments** (*snippets*) | Inserir blocs de codi repetitius a partir d'una drecera de text | Escriure `for` + Tab genera l'estructura completa d'un bucle |
| **Extensions de formatatge** | Reordenar i netejar el codi automàticament segons unes regles | Black (Python), Prettier (JavaScript) |

**🧪 Exercici 2 — Personalitza el teu entorn**
En `exercici2.md`: (a) canvia el tema de color del teu VS Codium i anota quin has triat; (b) instal·la una extensió que no tingueres (per exemple, un formatador per al llenguatge que més uses); (c) crea un fragment de codi propi (busca en la documentació de VS Codium "user snippets") per a una estructura que repetisques sovint (per exemple, la capçalera d'un script Python) i enganxa la seua definició JSON.

### 2.4. Actualització del propi entorn

L'IDE i les seues extensions no són estàtics: reben actualitzacions que corregixen errors, afigen funcions o pedacen vulnerabilitats. Gestionar açò també forma part d'administrar el teu entorn:

| Què s'actualitza | On es gestiona en VS Codium |
|---|---|
| El propi editor | `Ajuda → Buscar actualitzacions` (o notificació automàtica en obrir) |
| Extensions individuals | Panell d'Extensions — un punt blau indica que hi ha una versió nova |
| Actualització automàtica | Configurable per extensió (`extensions.autoUpdate` en `settings.json`) |

⚠️ **Actualitzar no sempre és gratis**: una extensió que s'actualitza pot canviar de comportament o deixar de ser compatible amb una versió antiga de l'IDE — en un projecte real en producció, molts equips fixen les versions de les seues ferramentes (no només de les biblioteques del projecte) per a evitar sorpreses just abans d'una entrega.

**🧪 Exercici 3 — Gestiona les actualitzacions**
En `exercici3.md`: comprova si el teu VS Codium té actualitzacions pendents (del propi editor o d'alguna extensió). Documenta què has trobat i, si actualitzes alguna cosa, què va canviar (núm. de versió abans/després). Si no hi ha res pendent, explica on has comprovat que no n'hi ha i per què desactivar l'actualització automàtica d'una extensió pot ser, a vegades, una decisió raonada i no un descuit.

---

## 3. Generació d'executables en diferents entorns (CA 2e, 2f)

En UD1 (punt 4) vam veure què és un executable i com s'obté. Ara comprovem una cosa distinta: **el mateix IDE pot generar executables en diversos llenguatges**, i **el mateix codi font pot executar-se des d'entorns completament distints**.

### 3.1. Un mateix entorn, distints llenguatges

VS Codium no "sap" executar codi per si sol — delega en el compilador o intèrpret de cada llenguatge (GCC, `javac`, l'intèrpret de Python...) que ja vas instal·lar en UD1. El que aporta l'IDE és una interfície comuna per a llançar-los tots sense eixir de l'editor.

```
UD01: gcc programa.c -o programa          (des de la terminal, a mà)
UD02: mateixa orde, llançada amb un botó/drecera des de l'IDE — mateixa ferramenta, menys fricció
```

**🧪 Exercici 4 — Un mateix entorn, tres llenguatges**
Retoma (o torna a crear) un script senzill en Python, un en C i un en Java (poden ser els d'UD1). Configura i usa, dins de VS Codium, una forma d'executar cadascun amb un sol botó o drecera (l'extensió Code Runner, o una tasca pròpia). En `exercici4.md`, indica què vas configurar per a cada llenguatge i què va haver d'instal·lar-se o ajustar-se a banda del propi IDE perquè funcionara.

### 3.2. Un mateix codi, distints entorns

A l'inrevés: el mateix fitxer `.py` pot executar-se des de VS Codium en el teu equip, des d'una terminal sense IDE, o des d'un entorn que no està ni instal·lat en la teua màquina — un **IDE en línia**, que executa el codi en un servidor remot i et retorna el resultat en el navegador.

| Entorn | On s'executa el codi | Necessita instal·lació |
|---|---|---|
| VS Codium (local) | En el teu equip | Sí — l'IDE i l'intèrpret/compilador |
| Terminal, sense IDE | En el teu equip | Només l'intèrpret/compilador, no l'IDE |
| IDE en línia (p. ex. vscode.dev, replit.com) | En un servidor remot | No — basta un navegador |

**🧪 Exercici 5 — El mateix script, tres formes d'executar-lo**
Usa un script Python senzill (pot ser el de la memòria/RAM d'UD1, exercici 4). Executa'l: (a) des de VS Codium amb el botó d'executar; (b) des de la terminal integrada, escrivint tu mateix l'orde (`python exercici4.py`); (c) enganxant el mateix codi en un IDE en línia (per exemple, replit.com o vscode.dev) i executant-lo ahí. En `exercici5.md`, indica què canvia entre els tres (què vas necessitar tindre instal·lat en cada cas, i com de ràpid va ser arrancar cadascun).

---

## 4. Comparació d'entorns de desenvolupament (CA 2g)

Avaluar un entorn no és dir "m'agrada" o "no m'agrada" — és identificar, amb criteri, què comparteix amb altres i què és propi de cadascun.

| Característica | VS Codium (local) | IDE en línia (vscode.dev / replit.com) |
|---|---|---|
| Instal·lació | Necessària, una vegada | Cap — només un navegador |
| Funciona sense connexió a internet | Sí | No (o molt limitat) |
| Rendiment amb projectes grans | Depén de l'equip, normalment millor | Depén del servidor remot i de la teua connexió |
| Extensions disponibles | Catàleg complet (Open VSX / Marketplace) | Habitualment més limitat |
| Accés des de qualsevol equip sense configurar res | No (cal instal·lar-lo primer) | Sí |
| Executa codi directament | Sí, amb el compilador/intèrpret instal·lat | Depén del servei — molts sí que ho permeten |

> 📡 **Per què importa hui**: quan més avant treballes en el **dashboard de finances personals** amb control de versions (UP3), és habitual alternar entre el teu entorn local (per al dia a dia) i un entorn en línia (per a revisar o fer un canvi ràpid des d'un equip que no és el teu, sense instal·lar res). Saber què es guanya i què es perd en canviar d'entorn és, literalment, el que avalua este RA.

**🧪 Exercici 6 — Fitxa comparativa de dos entorns**
En `exercici6.md`, completa una taula Markdown (com l'anterior, però amb les teues pròpies columnes) comparant VS Codium amb l'IDE en línia que hages provat en l'exercici 5. Afig una conclusió de 2-3 línies: en quina situació usaries cadascun?

---

## 🎯 Repte de classe

Vas a avaluar un tercer entorn de desenvolupament — un que no hages usat en els exercicis anteriors — aplicat al projecte del **dashboard de finances personals**. Pot ser un IDE distint instal·lat localment (per exemple, Thonny, PyCharm Community, o qualsevol altre que tingues accés a instal·lar) o un segon IDE en línia distint al de l'exercici 5.

En VS Codium, crea `repte.md` dins de la teua carpeta `UD02` amb una fitxa que incloga:

1. **Instal·lació** (CA 2a): és propietari o lliure? Què vas haver de fer per a tindre'l disponible (instal·lar, o simplement obrir una web)?
2. **Personalització** (CA 2b, 2c, 2d): què es pot personalitzar (temes, extensions, dreceres)? Com es gestionen les seues actualitzacions?
3. **Generació d'executables** (CA 2e, 2f): prova a executar-hi el mateix script Python que vas usar en l'exercici 5. Funciona igual? Què vas haver d'ajustar?
4. **Comparació final** (CA 2g): una taula comparant este tercer entorn amb VS Codium — almenys 4 característiques.

**Plantilla orientativa per a `repte.md`:**

```markdown
# Repte — [nom de l'entorn avaluat]

## 1. Instal·lació
- Propietari o lliure?: ...
- Què vas haver de fer: ...

## 2. Personalització
- Què es pot personalitzar: ...
- Com s'actualitza: ...

## 3. Generació d'executables
- Va funcionar el mateix script?: ...
- Què vas haver d'ajustar: ...

## 4. Comparació amb VS Codium
| Característica | VS Codium | [entorn avaluat] |
|---|---|---|
| ... | ... | ... |
```

*Variació avaluable*: es pot demanar que cada alumne avalue un entorn distint i després es posen en comú les fitxes en classe, construint entre tots una comparativa més àmplia que la de qualsevol fitxa individual.

---

<div style="page-break-after: always;"></div>

## Resum de la unitat

**1. L'entorn de desenvolupament: instal·lació i primers passos** Un IDE afig sobre un editor de text simple autocompletat, detecció d'errors i depuració integrada. Software propietari i lliure no equivalen a "de pagament" i "gratis" — VS Code i VS Codium són el mateix codi font compilat i llicenciat de dos formes distintes, l'exemple més directe d'esta distinció.

**2. Personalització, automatització i actualització de l'entorn** Mòduls i extensions amplien el que l'IDE sap fer; temes, estil de codificació i dreceres l'adapten a com treballes; tasques i fragments automatitzen el repetitiu. El propi entorn també s'actualitza — editor i extensions per separat — i eixa gestió forma part d'administrar-lo, no és un detall menor.

**3. Generació d'executables en diferents entorns** El mateix IDE executa distints llenguatges delegant en el compilador o intèrpret de cadascun; el mateix codi font pot executar-se des del teu equip, des d'una terminal sense IDE, o des d'un entorn en línia que no necessita instal·lació però sí connexió.

**4. Comparació d'entorns de desenvolupament** Avaluar un entorn és identificar què comparteix amb altres (instal·lació, personalització, execució) i què li és propi (rendiment, disponibilitat sense connexió, catàleg d'extensions) — la base amb què es construïx el Repte de classe d'esta unitat.

---

## 📚 Per a saber-ne més (opcional, no avaluable)

- Documentació oficial de VS Code: https://code.visualstudio.com/docs
- Open VSX Registry (catàleg d'extensions de VS Codium): https://open-vsx.org/
- vscode.dev (VS Code en el navegador, sense instal·lar res): https://vscode.dev/

### 🧭 Per què et servirà això de veritat

- En el teu primer treball probablement no triaràs tu l'IDE de l'equip — però sí que l'instal·laràs, el personalitzaràs i el mantindràs actualitzat tu mateix, i saber fer-ho amb criteri (i no només "a base de tutorials de YouTube") estalvia hores.
- Quan canvies d'equip, de sistema operatiu, o hages de treballar puntualment des d'un portàtil que no és el teu, saber moure't entre un entorn local i un en línia sense perdre productivitat és una habilitat que es nota.
- Justificar per què el teu equip usa una ferramenta lliure en compte d'una propietària (o al revés) amb arguments tècnics, no només de cost, és exactament el tipus de decisió que un responsable tècnic júnior comença a prendre prompte.
