<div style="text-align: center;">

<img src="data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCA0MDAgNDAwIiB3aWR0aD0iMTgwIiBoZWlnaHQ9IjE4MCI+CiAgPGNpcmNsZSBjeD0iMjAwIiBjeT0iMjAwIiByPSIxNzAiIGZpbGw9IiNGMEZERkEiLz4KICA8Y2lyY2xlIGN4PSIyMDAiIGN5PSIyMDAiIHI9IjE3MCIgZmlsbD0ibm9uZSIgc3Ryb2tlPSIjOTlGNkU0IiBzdHJva2Utd2lkdGg9IjIiLz4KICA8dGV4dCB4PSIyMDAiIHk9IjI0OCIgZm9udC1mYW1pbHk9IidDb3VyaWVyIE5ldycsIENvdXJpZXIsIG1vbm9zcGFjZSIgZm9udC1zaXplPSIxNTAiIGZvbnQtd2VpZ2h0PSI3MDAiIGZpbGw9IiMwRjc2NkUiIHRleHQtYW5jaG9yPSJtaWRkbGUiPiZndDtfPC90ZXh0Pgo8L3N2Zz4K" width="180" alt="Logotip EDE"/>

<h1>Unitat 1</h1>
<h2>Desenvolupament de software</h2>

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

1. El programa i els components del sistema (CA 1a)
2. El cicle de vida del software: fases del desenvolupament (CA 1b)
3. Codi font, codi objecte i codi executable (CA 1c)
4. Codi intermedi i màquines virtuals (CA 1d)
5. Classificació dels llenguatges de programació (CA 1e)
6. Eines del desenvolupament de software (CA 1f)
7. Repte de classe
8. Resum de la unitat
9. Per a saber-ne més

<div style="page-break-after: always;"></div>

**RA cobert:** RA1 (CA 1a-1f) — Reconeix els elements i les eines que intervenen en el desenvolupament d'un programa informàtic, analitzant les característiques i les fases en què actuen fins a arribar a la seua posada en funcionament.

> ⚠️ **Nota de programació**: el CA 1g (metodologies àgils de desenvolupament de software) **no** es treballa en esta unitat — està assignat a la UP6 (Gestió de projectes informàtics), on l'alumnat ja coneix el cicle de vida i les fases que es presenten ací. El RA1 complet queda programat igualment: 1a-1f ací, 1g en la UP6.

> 💡 **Nota d'estudi**: esta unitat dona el vocabulari i els conceptes que usaràs durant tot el curs — quan en UD2 instal·les un IDE o en UD3 faces el teu primer commit, estaràs usant "eines de desenvolupament" tal com es classifiquen ací.

> 💻 **Com treballar els exercicis d'esta unitat**: crea en VS Codium una carpeta `UD01_ElTeuNom` — l'anirem usant en tots els exercicis de la unitat. Quan un exercici demane codi, crea'l com a fitxer (`.py`, `.java`, `.c`...) dins d'eixa carpeta i executa'l des de la terminal integrada de VS Codium (`Terminal → Nova terminal`). Quan demane raonar, classificar o redactar, escriu la resposta en un fitxer Markdown (`exerciciN.md`) dins de la mateixa carpeta, en compte de en paper. Així, des del primer dia, treballes dins de l'editor que usaràs durant tot el cicle — instal·lar-lo i configurar-lo a fons (i comparar-lo amb altres IDE) es veu en la UP2; ací simplement li anem agafant el tranquillo.

> 🐍 **Per què a vegades canviem de llenguatge**: en esta unitat, Python és el llenguatge de treball habitual per als exercicis (el mateix que usaràs en Programació). Quan algun exercici use Java, C o SQL en el seu lloc, és perquè eixe llenguatge concret és qui millor il·lustra el concepte d'eixe punt (compilació nativa, codi intermedi i màquina virtual, paradigma declaratiu) — no cal que aprengues la seua sintaxi a fons, només que seguisques l'exemple pas a pas i entengues la idea que demostra.

## 🎯 Conceptes clau

En acabar esta unitat sabràs:
- Distingir programa, software (per forma i per funció) i explicar com interactuen memòria, processador i perifèrics quan un programa s'executa.
- Reconèixer les fases del cicle de vida del software (model en cascada) i què produïx cadascuna, junt amb les seues alternatives.
- Diferenciar codi font, objecte, intermedi i executable, i classificar llenguatges de programació i eines de desenvolupament segons la fase a què donen suport.

---

## 1. El programa i els components del sistema (CA 1a)

### 1.1. Informàtica, software i programa

La **informàtica** és el tractament automàtic de la informació per mitjà d'un dispositiu. Tota eixa informació es representa internament en **binari** (seqüències de 0 i 1): la unitat mínima és el **bit**, i 8 bits formen un **byte**.

Estes unitats reapareixen tot el curs — la grandària d'un fitxer, la capacitat d'una base de dades, quant ocupa una imatge que puges a un dashboard — així que convé tindre-les clares des d'ara:

| Unitat | Equival a |
|---|---|
| 1 byte | 8 bits |
| 1 KB (kilobyte) | 1024 bytes |
| 1 MB (megabyte) | 1024 KB |
| 1 GB (gigabyte) | 1024 MB |

> 📡 **Canviant activament**: formalment, 1 KB (kilobyte, sistema internacional) són 1000 bytes, i és el **KiB** (kibibyte) qui val 1024 — la distinció existix des de 1998 (norma IEC 80000-13), però quasi ningú la respecta fora de la documentació tècnica més formal. Per això un disc anunciat com "1 TB" mostra menys espai de l'esperat en el teu sistema operatiu: el fabricant compta en base 1000, el sistema operatiu en base 1024. En esta unitat, com en la majoria de contextos de memòria RAM, seguim la convenció més habitual (1024) per simplicitat.

**🧪 Exercici 1 — Unitats d'informació amb un cas real**
Un dashboard de finances personals guarda cada transacció com una fila d'uns 200 bytes en una base de dades. En VS Codium, crea `exercici1.py` dins de la teua carpeta `UD01` i escriu un script que calcule i mostre per terminal (amb `print`): (a) quants KB ocuparà la base de dades d'un usuari que registra 15 transaccions al dia durant un any; (b) quants MB ocuparia si l'aplicació tinguera 10.000 usuaris fent el mateix. Executa l'script des de la terminal integrada (`python exercici1.py`) i afig, com a comentari al final del fitxer, si et sorprén el resultat i per què.

El **software** és la part intangible d'un sistema informàtic: el conjunt d'instruccions que li diuen al hardware què fer. Dins del software convé distingir diversos nivells:

| Terme | Què és | Exemple |
|---|---|---|
| **Programa** | Conjunt d'instruccions executables que realitzen una tasca determinada | Una funció que suma dos números (una peça de codi; encara no és, per si sola, una aplicació) |
| **Biblioteca** | Fitxer que empaqueta programes ja escrits, reutilitzables des d'un altre codi | Un fitxer `.dll`, un paquet `pip` |
| **Aplicació** | Un o diversos programes (amb o sense biblioteques) orientats a una tasca de l'usuari final | Adobe Photoshop |
| **Suite** | Diverses aplicacions independents distribuïdes juntes | LibreOffice, MS Office |

⚠️ **Important**: el sistema operatiu no encaixa en una sola d'estes categories — és, a la pràctica, una suite de programes, biblioteques i aplicacions que gestionen la resta del sistema.

**🧪 Exercici 2 — Vocabulari tècnic correcte**
Corregeix esta frase perquè siga tècnicament precisa (identifica els 4 termes mal usats i explica per què). Escriu la teua resposta en `exercici2.md`, dins de la teua carpeta `UD01`:

> "Al meu ordinador tinc programes com LibreOffice Writer o Adobe Photoshop, que en essència envien ordres al processador. El primer forma part d'una biblioteca anomenada LibreOffice, i el segon usa internament diverses suites on té guardades funcions de disseny gràfic. Tots dos han sigut codificats per programadors experts."

**Un altre eix de classificació: software de sistema vs. software d'aplicació.** La taula anterior distingeix *quina forma té* el software (programa/biblioteca/aplicació/suite); esta altra distingeix *per a què serveix*, i és igual de necessària — un controlador, per exemple, és una biblioteca (per la seua forma) que pertany al software de sistema (per la seua funció):

| Tipus | Funció | Exemples |
|---|---|---|
| **Software de sistema** | Gestiona el hardware i dona la base sobre la qual corre tota la resta | Sistema operatiu, controladors (*drivers*), firmware (BIOS/UEFI), utilitats del sistema |
| **Software d'aplicació** | Resol tasques concretes de l'usuari final, recolzant-se en el software de sistema | Navegador, editor de codi, un dashboard que tu programes |

**🧪 Exercici 3 — Software de sistema o d'aplicació**
Obri la terminal integrada de VS Codium i executa `apt list --installed | less` (prem `q` per a eixir) per a veure els paquets instal·lats en el teu LliureX — o el gestor d'aplicacions del mòbil, si prefereixes eixa font. Tria'n 6: 3 que consideres software de sistema i 3 que consideres software d'aplicació. En `exercici3.md`, per a cadascun justifica en una frase per què l'has classificat així, i digues a més si per la seua forma és un programa, una biblioteca, una aplicació o una suite.

### 1.2. Com un programa usa el hardware: memòria, processador i perifèrics

Quan un programa s'executa, no ho fa en el buit: necessita recolzar-se en tres components del sistema.

```
   PERIFÈRICS                MEMÒRIA (RAM)             PROCESSADOR (CPU)
 (entrada / eixida)      instruccions + dades        executa el programa
┌──────────────────┐    ┌──────────────────────┐    ┌───────────────────┐
│ teclat, ratolí,   │───▶│  el programa es      │◀──▶│ cicle:            │
│ xarxa, sensors... │    │  carrega ací abans    │    │  1. FETCH  (busca)│
│                   │◀───│  d'executar-se        │    │  2. DECODE (llig) │
│ pantalla, disc,   │    │                       │    │  3. EXECUTE (fa)  │
│ impressora...     │    └──────────────────────┘    └───────────────────┘
└──────────────────┘
```

- **Memòria (RAM)**: mentre un programa s'executa, tant les seues instruccions com les dades que maneja viuen en memòria principal. En tancar-lo, eixe contingut es perd (és memòria *volàtil*) — per això les dades que volem conservar cal guardar-les en un perifèric d'emmagatzematge (disc).
- **Processador (CPU)**: executa el programa repetint l'anomenat **cicle d'instrucció**: *fetch* (busca la instrucció següent en memòria), *decode* (la interpreta) i *execute* (la realitza, usant els seus registres interns i la unitat aritmeticològica).
- **Perifèrics**: són la via d'entrada i eixida del programa amb l'exterior. D'**entrada** (teclat, ratolí, xarxa, sensors) el programa rep dades; d'**eixida** (pantalla, impressora, altaveus) o d'**emmagatzematge** (disc, xarxa) el programa retorna o persisteix resultats.

**No tota la memòria és RAM.** La RAM és la que més s'usa mentre el programa corre, però convé distingir-la d'altres dos tipus:

| Tipus | Volàtil? | Què guarda | Exemples |
|---|---|---|---|
| **RAM** | Sí (es perd en apagar) | Instruccions i dades del programa en execució | Memòria de l'ordinador |
| **ROM / firmware** | No | Instruccions bàsiques d'arrancada, gravades de fàbrica | BIOS/UEFI |
| **Emmagatzematge secundari** | No | Dades i programes de forma permanent | Disc dur, SSD, emmagatzematge en xarxa |

> 📡 **Vigent**: la majoria de processadors actuals incorporen a més una memòria **cau**, molt més ràpida que la RAM però molt xicoteta, que guarda les dades i instruccions d'ús més freqüent per a evitar viatges constants a la RAM. És una de les raons per què dos CPU amb la mateixa velocitat de rellotge poden rendir de forma molt distinta.

**Els perifèrics tampoc són només "entrada" o "eixida".** Alguns dispositius complixen les dues funcions alhora:

| Tipus | Funció | Exemples |
|---|---|---|
| **Entrada** | El programa rep dades de l'exterior | Teclat, ratolí, micròfon |
| **Eixida** | El programa envia resultats a l'exterior | Pantalla, altaveus, impressora |
| **Entrada/eixida** | Complix ambdues funcions | Pantalla tàctil, targeta de xarxa, disc extern |

> 💡 **Activitat ràpida (5 min)**: obri una terminal i executa `htop` (instal·la'l abans amb `sudo apt install htop` si no el tens; si no tens permisos d'administrador o connexió a internet, usa en el seu lloc el *Monitor del sistema* gràfic ja instal·lat en LliureX — la mateixa informació, sense necessitar res nou). Busca: quanta RAM està usant el navegador en este moment? Quin procés usa més CPU? Relaciona el que veus amb el cicle fetch-decode-execute i amb la volatilitat de la RAM — si forces el tancament d'un procés sense guardar, què es perd i per què?

> 📡 **Per què importa hui**: quan més avant programem, per exemple, un dashboard de finances personals, esta relació es veu literalment: les dades que l'usuari teclegia entren per un perifèric d'entrada, es guarden temporalment en variables (memòria RAM) mentre el programa calcula, i el resultat final es persisteix en una base de dades en disc (emmagatzematge secundari) — sense este esquema, "guardar" i "mostrar en pantalla" són només paraules soltes.

**🧪 Exercici 4 — Memòria, processador i perifèrics en un cas real**
En `exercici4.py`, escriu un programa que demane un nom per teclat (`input()`) i mostre en pantalla una salutació (`print()`). Executa'l en la terminal integrada. Després, en `exercici4.md`, identifica sobre el teu propi codi: quin perifèric intervé en l'entrada, quin perifèric intervé en l'eixida, i en quina línia la dada `nom` passa per la memòria RAM i en quina línia el processador executa cada instrucció.

### 1.3. Programar vs. desenvolupar software

**Programar** és, en essència, codificar instruccions perquè un dispositiu es comporte d'una manera concreta. **Desenvolupar software** és bastant més: inclou analitzar, dissenyar, provar, documentar i mantindre, a més de codificar. Per això en este mòdul parlarem de **desenvolupador** en compte de "programador" — la codificació és només una de les fases (ho veiem en el punt 2).

**De la idea a la solució.** Fins i tot abans d'arribar a les fases formals del punt 2, resoldre qualsevol problema de programació — per xicotet que siga — seguix en miniatura el mateix esquelet:

1. **Entendre el problema**: què es demana exactament? (sovint no està tan clar com pareix — ho veurem en el punt 2, fase d'Anàlisi)
2. **Dissenyar una solució**: pensar el "com" en termes generals, sense escriure codi encara (a vegades amb pseudocodi o un diagrama)
3. **Implementar-la**: traduir eixa solució a un llenguatge de programació concret — açò és, estrictament, "programar"
4. **Comprovar-la**: verificar que funciona i que fa el que havia de fer

> 🕰️ Este procés de 4 passos és el mateix esquelet, en miniatura, que el cicle de vida del software complet que ve a continuació — anàlisi, disseny, codificació i proves no són idees exclusives de projectes grans: apareixen fins i tot en resoldre un exercici xicotet.

---

## 2. El cicle de vida del software: fases del desenvolupament (CA 1b)

Tot desenvolupament de software recorre, amb més o menys rigor, un conjunt d'etapes conegut com **cicle de vida del software**. El model més clàssic —i el que usarem com a referència per a entendre cada fase— és el **model en cascada**: cada fase es recolza en l'anterior i genera una documentació pròpia, sense començar la següent fins a tancar l'actual.

### 2.1. Anàlisi

Es recullen i documenten els requisits del client. És una comunicació **bilateral**: el client poques vegades sap expressar amb precisió tècnica el que necessita, així que l'analista ha d'indagar, no només prendre nota. Les tècniques més habituals són l'**entrevista**, el **qüestionari**, l'**observació** del procés actual i la revisió de documentació ja existent.

Els requisits recollits es dividixen en dos tipus, i confondre'ls és un dels errors més comuns en començar:

| Tipus | Què descriu | Exemple (dashboard de finances personals) |
|---|---|---|
| **Funcional** | Què ha de *fer* el sistema — una acció o funció concreta | "L'usuari pot registrar una despesa indicant import, data i categoria" |
| **No funcional** | Com s'ha de *comportar* el sistema en fer-ho — rendiment, seguretat, usabilitat, disponibilitat... | "El llistat de despeses ha de carregar en menys de 2 segons"; "les dades es xifren en trànsit" |

Tot açò es recull en l'**ERS (Especificació de Requisits de Software)**, junt a un primer esboç de les entitats del sistema (diagrama E/R o de classes preliminar).

> 🕰️ **Què seguix vigent i què és ja història**: durant dècades, l'estàndard de referència per a redactar una ERS va ser **IEEE 830** (1998) — hui retirat. El substituïx **ISO/IEC/IEEE 29148**, la norma vigent per a especificar requisits de software. El contingut de fons (què és un requisit funcional o no funcional) a penes ha canviat; el que canvia és l'estàndard formal que regula com documentar-lo.

### 2.2. Disseny

| Diagrama UML | Què mostra | En esta unitat |
|---|---|---|
| De casos d'ús | Què pot fer cada tipus d'usuari | Només es reconeix que existix |
| De seqüència | En quin ordre es comuniquen els components | Només es reconeix que existix |
| De classes | Quines entitats existixen, amb els seus atributs, mètodes i relacions | S'aprofundix — es retoma en la UD4 |

Es definix el funcionament del sistema **sense entrar encara en el codi**, a dos nivells:

- **Disseny arquitectònic**: la visió global — en quins mòduls o capes s'organitza el sistema i quina tecnologia usa cadascun (per exemple, separar un dashboard de finances en una capa d'interfície, una de lògica de negoci i una d'accés a la base de dades).
- **Disseny detallat**: dins de cada mòdul, com es resol internament — quines estructures de dades i quins algorismes usa cada funció, encara en diagrames o pseudocodi, no en codi real.

La notació estàndard vigent per a representar estos dissenys és **UML** (*Unified Modeling Language*), amb distints diagrames segons el que es vulga mostrar: **de casos d'ús** (què pot fer cada tipus d'usuari), **de seqüència** (en quin ordre es comuniquen els components) i **de classes** (quines entitats existixen i com es relacionen) — este últim modela l'estructura del software: classes, atributs, mètodes i relacions entre objectes. En esta unitat n'hi ha prou amb reconèixer que existixen i per a què servix cadascun a grans trets; aprofundim només en el de classes (vegeu l'avís següent), que retrobareu amb més detall en la UD4 (anàlisi i disseny).

⚠️ **Un diagrama de classes no és el mateix que el disseny d'una base de dades.** Estan relacionats — moltes vegades les classes d'un diagrama UML acaben inspirant les taules de la base de dades, sobretot si s'usa un ORM — però són dos models distints, amb regles distintes: el diagrama de classes descriu objectes amb atributs i comportament; el disseny d'una base de dades relacional usa el seu propi model, l'**entitat-relació** (entitats, atributs, claus i cardinalitats), del qual eixirien les taules *Usuari*, *Transacció* i *Categoria* del dashboard de finances. No els confongues, encara que en un projecte real acaben assemblant-se.

Tot este treball de disseny queda recollit en el **quadern de càrrega**: el document tècnic, consensuat amb el client, que servix de base per a començar a programar.

### 2.3. Codificació

Es traduïx el quadern de càrrega al llenguatge de programació triat. "Codi font comentat" no significa només afegir comentaris: implica seguir unes mínimes bones pràctiques perquè qualsevol altra persona (o tu mateix, mesos després) puga entendre'l:

- **Noms significatius**: `calcularTotalGastos()` en compte de `f1()`.
- **Comentaris que expliquen el perquè**, no el què — el codi ja diu *què* fa; el comentari ha d'aportar el motiu quan no siga obvi.
- **Convencions d'estil** consistents, normalment les que marca el mateix llenguatge o l'equip (per exemple, PEP 8 en Python).

📡 **Per què importa hui**: és en esta fase on entra de forma natural el **control de versions** (Git) — cada avanç de codi es registra com un canvi amb el seu propi historial. Ho veurem en detall en la UP3, però l'hàbit de comentar i nomenar bé comença ací, abans de tocar Git.

### 2.4. Proves

Es comprova que el software no té errors i que fa el que havia de fer — idealment ho prova algú distint de qui va programar, perquè a qui ha escrit el codi li costa més veure els seus propis errors (coneix el camí que "hauria de" funcionar i tendix a provar només eixe).

**Segons quant es coneix del codi:**

| Tipus | Com es prova | Es fixa en... |
|---|---|---|
| **Caixa negra** | Sense mirar el codi intern — només es donen entrades i es comprova si l'eixida és l'esperada | La funcionalitat, des de fora |
| **Caixa blanca** | Coneixent l'estructura interna del codi | Es recolza en eixa estructura per a dissenyar els casos de prova — cobertura de sentències, de condicions o de camins possibles, segons el rigor que calga |

**Segons quina part del sistema es prova** — de menor a major abast:

| Nivell | Què es prova |
|---|---|
| Proves unitàries | Una funció o mòdul per separat, de forma aïllada |
| Proves d'integració | Diversos mòduls treballant junts |
| Proves de sistema | L'aplicació completa, de principi a fi |
| Proves d'acceptació | El mateix client comprova que es complix el pactat en l'Anàlisi |

### 2.5. Documentació

Ací s'elabora la **documentació d'usuari** — distinta de la documentació **tècnica** que ja s'ha anat generant en fases anteriors (ERS, quadern de càrrega, codi comentat): manual d'instal·lació, manual d'ús, preguntes freqüents...

> 📡 **Canviant ara mateix**: el manual d'usuari extens en PDF està perdent pes davant de l'ajuda contextual integrada en la mateixa aplicació — tutorials interactius la primera vegada que s'obri, tooltips junt a cada opció, un assistent que guia pas a pas. La documentació no ha desaparegut: s'ha mogut dins del mateix producte.

### 2.6. Explotació

El software s'instal·la en l'entorn real d'ús. Si substituïx una versió anterior, existixen diverses estratègies d'implantació, cadascuna amb un compromís distint entre risc i velocitat:

| Estratègia | En què consistix |
|---|---|
| **Directa** | Se substituïx la versió anterior de colp, per a tots els usuaris alhora |
| **En paral·lel** | Ambdues versions conviuen durant un temps, per a comparar i donar seguretat |
| **Pilot** | S'implanta primer en un grup reduït d'usuaris abans de generalitzar |
| **Per fases** | Es desplega mòdul a mòdul, no tot el sistema d'una vegada |

> 📡 **Canviant activament**: en desenvolupament web, este concepte es tradueix hui en el **desplegament** (*deployment*) del codi a un servidor, cada vegada més automatitzat per mitjà de pràctiques de **CI/CD** (integració i desplegament continus) — ho veurem amb detall en unitats posteriors, però la idea de fons (portar el software de l'entorn de desenvolupament al real, amb algun grau de gradualitat o seguretat) és la mateixa que en explotació.

### 2.7. Manteniment

S'actua sobre el software ja en producció. Es distingixen quatre tipus, i no tots signifiquen "hi ha un error":

| Tipus | Què resol | Exemple |
|---|---|---|
| **Correctiu** | Corregir errors detectats en producció | "Es corregix una fallada en iniciar sessió" |
| **Evolutiu** | Afegir funcionalitat nova que el client no va demanar al principi | "S'afig un mode fosc" |
| **Adaptatiu** | Adaptar-se a canvis de l'entorn, no del mateix software | "S'adapta a la nova versió d'Android" |
| **Perfectiu** | Millorar sense canviar la funcionalitat visible | "S'optimitza el temps d'arrancada" |

Si el manteniment implica una ampliació important, sol ser necessari revisar fases anteriors — Anàlisi i Disseny inclosos.

> 💡 Fixa't en el registre d'actualitzacions de qualsevol app que uses: quasi cada entrada encaixa en un d'estos quatre tipus. És justament el que et demanarà el repte de classe d'esta unitat.

---

**Qui intervé en cada fase?** Els rols no són compartiments estancs — la mateixa persona pot cobrir diversos:

| Rol | Fases en què participa |
|---|---|
| Analista de sistemes | Anàlisi |
| Dissenyador de software | Disseny |
| Analista programador ("desenvolupador") | Disseny i Codificació |
| Programador | Codificació |
| Arquitecte de software | Anàlisi, Disseny, Documentació i Explotació |

### La cascada és l'única forma d'organitzar-ho?

No. El model en cascada és lineal i rígid — si en Proves apareix una fallada de Disseny, cal tornar arrere diverses fases. Existixen alternatives clàssiques que organitzen estes mateixes fases d'una altra manera:

| Model | Idea central |
|---|---|
| **Iteratiu-incremental** | El software es construïx i entrega en increments successius, cadascun afegint funcionalitat sobre l'anterior |
| **En espiral** (Boehm) | Combina iteració amb una anàlisi de riscos explícita en cada volta, abans de seguir avançant |
| **De prototipatge** | Es construïx prompte una versió reduïda i funcional per a validar-la amb el client abans de desenvolupar el sistema complet |

> 📡 **Actualitat**: hui, la gran majoria d'equips de desenvolupament no usa cascada ni estos models clàssics com a forma habitual de treballar, sinó **metodologies àgils** (Scrum, Kanban...) — segons l'informe *State of Agile* de Digital.ai, al voltant del 71% de les organitzacions declara usar-les en el seu cicle de desenvolupament. La cascada seguix sent útil com a model de referència per a entendre quines fases existixen i què produïx cadascuna (que és l'objectiu d'este punt), i encara s'usa en projectes amb requisits molt tancats o molt regulats — però no és representativa de com treballa hui la majoria d'equips. Com funcionen les metodologies àgils en concret es veu en detall en la UP6 (CA 1g).

**🧪 Exercicis de la fase**

**Exercici 5 — Fases del cicle de vida aplicades**
Un client et demana una aplicació de gestió de despeses personals. En `exercici5.md`, redacta breument (2-3 línies per fase) què faries en cadascuna de les 7 fases del cicle de vida per a eixe projecte concret.

**Exercici 6 — Requisits funcionals o no funcionals**
Per a la mateixa aplicació de despeses personals, en `exercici6.md` classifica estos 6 requisits en funcionals o no funcionals, justificant cadascun en una frase: (1) "l'usuari pot exportar les seues despeses a PDF"; (2) "l'aplicació ha de funcionar sense connexió a internet"; (3) "es poden crear categories personalitzades"; (4) "cap usuari pot veure les dades d'un altre"; (5) "l'històric d'un any ha de carregar en menys de 3 segons"; (6) "es pot iniciar sessió amb Google".

**Exercici 7 — Classifica el manteniment**
Busca el registre de canvis (*changelog* o "novetats d'esta versió") d'una app que tingues instal·lada i tria 4 entrades distintes. En `exercici7.md`, classifica cadascuna com a manteniment correctiu, evolutiu, adaptatiu o perfectiu, i justifica-ho.

---

## 3. Codi font, codi objecte i codi executable (CA 1c)

Un dispositiu només entén **codi màquina** (binari). Com que ningú programa directament en binari, escrivim en un llenguatge de programació i deixem que unes eines ho tradueixquen — però eixe camí no és idèntic en tots els llenguatges:

```
Model de compilació directa (C, C++...):
codi font      ──(compilador)──▶  codi objecte   ──(+ biblioteques, enllaçador)──▶  codi executable natiu
   (.c)                             (.o)                                             (específic del SO)

Model de codi intermedi (Java...):
codi font      ──(compilador)──▶  codi intermedi / bytecode  ──(màquina virtual, punt 4)──▶  s'executa
   (.java)                          (.class)
```

- **Codi font**: el conjunt d'instruccions que escriu el desenvolupador, en un fitxer de text (`.java`, `.py`, `.c`...).
- **Codi objecte**: resultat de compilar el codi font en el model de compilació directa. Encara no és executable per si sol — li falta enllaçar-se amb biblioteques i amb les particularitats del sistema de destinació.
- **Codi intermedi** (o *bytecode*): resultat de compilar el codi font en llenguatges com Java, pensat per a no dependre d'un processador concret. **No és sinònim de codi objecte**: no s'enllaça per a donar un executable natiu — l'executa una màquina virtual (ho veiem en el punt 4). En Java és el fitxer `.class`.
- **Codi executable**: en el model de compilació directa, s'obté en afegir al codi objecte les funcions de biblioteques usades i les particularitats del sistema operatiu de destinació (procés normalment realitzat per un *enllaçador*). És el que el dispositiu interpreta directament.

⚠️ **Codi objecte i codi intermedi no són el mateix**, encara que tots dos siguen un pas a mig camí abans que el programa corra: l'objecte s'enllaça per a donar un executable natiu; l'intermedi l'interpreta una màquina virtual, sense passar per un enllaçador tradicional. És justament la frontera entre este punt (CA 1c) i el següent (CA 1d).

⚠️ Un mateix codi font pot necessitar generar **executables distints** segons el sistema operatiu de destinació (Windows, Linux, macOS), encara que el codi font no canvie — açò s'aplica al model de compilació directa.

**L'enllaçador fa alguna cosa més que "ajuntar" fitxers** (de nou, en el model de compilació directa — en Java és la màquina virtual qui resol les classes en temps d'execució, punt 4). Decidix a més *com* s'incorporen les biblioteques a l'executable final:

- **Enllaçat estàtic**: el codi de la biblioteca es copia dins del mateix executable. El fitxer final és més gran, però no depén de res extern per a funcionar.
- **Enllaçat dinàmic**: l'executable només guarda una referència a la biblioteca, que es carrega per separat en temps d'execució (els `.dll` en Windows, els `.so` en Linux). Diversos programes poden compartir una mateixa còpia de la biblioteca en memòria, i actualitzar-la no obliga a recompilar cada programa que la usa.

**L'esquema no es veu igual en tots els llenguatges.** Font → objecte → executable és més visible en un llenguatge compilat; en un d'interpretat, el mateix terme "executable" no s'aplica de la mateixa forma:

| Llenguatge | Codi font | Codi objecte / intermedi | Codi executable |
|---|---|---|---|
| C (compilat) | `programa.c` | Intern al procés de compilació, no es guarda com a fitxer a part | `programa.exe` / binari natiu |
| Java (híbrid) | `Programa.java` | `Programa.class` (bytecode) | No hi ha un executable natiu — l'interpreta la JVM (punt 4) |
| Python (interpretat) | `programa.py` | `__pycache__/programa.cpython-3XX.pyc` (bytecode en memòria cau, automàtic) | No es genera — l'intèrpret executa eixe bytecode compilat internament, sense generar un executable natiu a banda |

> 💡 Retomarem esta taula en el punt 5, en classificar els llenguatges segons com s'executen — és la mateixa idea vista des de l'altre costat.

**A la pràctica, amb ordes reals:**

```
# C: compilació + enllaçat en un sol pas
$ gcc programa.c -o programa
$ ./programa

# Java: compilació a bytecode, i execució sobre la JVM (punt 4)
$ javac HolaMundo.java      # genera HolaMundo.class (codi intermedi, no codi objecte)
$ java HolaMundo            # la JVM executa el bytecode (interpretant-lo o compilant-lo amb JIT)

# Python: compila a bytecode internament (ho guarda en __pycache__) i ho executa
$ python programa.py        # no genera un executable natiu a banda — ho processa la seua pròpia màquina virtual
```

> 📡 **Canviant activament: la frontera es difumina.** Motors com V8 (el que usen Chrome i Node.js) ja no només interpreten JavaScript línia a línia: compilen sobre la marxa, mentre el programa s'executa, les parts de codi que més es repetixen — s'anomena compilació **JIT** (*just-in-time*). En sentit contrari, eines com GraalVM permeten compilar bytecode Java directament a un executable natiu (`native-image`), sense necessitar una JVM en l'equip final. La classificació compilat/interpretat/híbrid del punt 5 seguix sent útil per a entendre la idea de fons, però cada vegada hi ha més llenguatges que mesclen les tres estratègies.

> 🧯 **Pla B si no pots instal·lar el JDK**: usa un compilador Java en línia (per exemple, jdoodle.com/online-java-compiler) per a completar l'exercici sense instal·lar res localment — el que s'avalua és que entengues el procés font → bytecode → execució, no la instal·lació en si. Si disposes de la VM portàtil del cicle, el JDK ja ve preinstal·lat ahí: és el lloc ideal per a tindre'l llest per endavant.

**🧪 Exercici 8 — De codi font a executable**
Esta és l'única vegada en la unitat que usem Java per a un exercici de codi: és el llenguatge que millor il·lustra el model de codi intermedi — no cal que li agafes el gust a la seua sintaxi. Instal·la un JDK si no el tens, i en la teua carpeta `UD01` crea `HolaMundo.java` amb un programa que imprimisca el teu nom. Compila'l des de la terminal integrada amb `javac HolaMundo.java`. Localitza en l'explorador de fitxers de VS Codium el fitxer `.class` generat i executa'l amb `java HolaMundo`. En `exercici8.md`, explica amb les teues paraules què representa cadascun dels tres fitxers/moments (font, codi intermedi, execució) en este procés.

**🧪 Exercici 9 — L'esquema en distints llenguatges**
Crea `exercici9.py` amb qualsevol instrucció senzilla (per exemple, un `print`) i executa'l una vegada des de la terminal integrada. Localitza en l'explorador de fitxers de VS Codium la carpeta `__pycache__` que es genera al costat i el fitxer `.pyc` que conté. Recolzant-te en la taula anterior i en el que acabes de veure, en `exercici9.md` explica amb les teues paraules per què en Python no té sentit parlar de "codi executable" de la mateixa forma que en C, i quin paper juga eixe `.pyc`.

**🧪 Exercici 10 — Compilat vs. interpretat, cronòmetre en mà**
Usem C només per a esta comparació puntual — no cal escriure'l ni dominar-lo, només compilar-lo, executar-lo i mesurar-lo. En la teua carpeta `UD01`, crea `exercici10.c` amb este codi ja escrit:

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

Ara escriu tu mateix, en `exercici10.py`, la versió equivalent en Python (un bucle que sume els números de l'1 al 10 milions — este sí en el llenguatge que ja coneixes). Des de la terminal integrada, compila i executa la versió en C (`gcc exercici10.c -o exercici10 && ./exercici10`); executa directament la versió en Python. Cronometra ambdues amb `time` (`time ./exercici10` i `time python exercici10.py`). En `exercici10.md`, arreplega els temps i explica la diferència segons el vist en este punt.

---

## 4. Codi intermedi i màquines virtuals (CA 1d)

Segons com es tracte el codi, un executable pot ser:

- **Portable**: funciona en diverses plataformes sense recompilar (p. ex., un `.jar` de Java, perquè usa *bytecode* no lligat a un processador concret).
- **No portable**: pensat per a una plataforma concreta (p. ex., un executable compilat en C per a Windows).

Alguns llenguatges, com Java, resolen la portabilitat amb una **màquina virtual**: una aplicació que emula un sistema (o part d'ell) dins del sistema operatiu real.

| Tipus de màquina virtual | Què fa | Exemples |
|---|---|---|
| **De sistema** | Simula un ordinador complet (arquitectura + SO) dins d'un altre | VirtualBox, VMware |
| **De procés** | Executa el codi intermedi (bytecode) d'un llenguatge concret, independitzant-lo del hardware real | JVM (Java Virtual Machine) |

La **JVM** executa el *bytecode* que genera el compilador de Java (els fitxers `.class`) — interpretant-lo instrucció a instrucció o, en les parts que més es repetixen, compilant-lo sobre la marxa (JIT, com vam veure en el punt 3) —, traduint-lo en ambdós casos a les instruccions del hardware concret on s'executa. Per això el mateix `.class` corre en Windows, Linux o macOS sense recompilar, sempre que hi haja una JVM instal·lada: "*write once, run anywhere*".

> 🕰️ **Per què existix la JVM**: a mitjans dels anys 90 cada sistema operatiu tenia el seu propi format d'executable, i distribuir un programa per a diverses plataformes obligava a compilar-lo i mantindre'l per separat per a cadascuna. Sun Microsystems va dissenyar Java (1995) amb la JVM com a peça central per a resoldre justament eixe problema: compilar una sola vegada a bytecode i deixar que la màquina virtual s'encarregue d'adaptar-se al sistema real. La necessitat que va resoldre seguix vigent — és la mateixa raó de fons per la qual hui existixen els contenidors i WebAssembly, que veiem a continuació.

**El pipeline complet, de principi a fi:**

```
Programa.java  ──(javac, compilador)──▶  Programa.class (bytecode)
Programa.class ──(java, s'executa sobre la JVM)──▶  el programa corre
```

> 📡 **Seguix vigent**: el model de màquina virtual de procés no és exclusiu de Java — Python (amb el seu intèrpret i bytecode `.pyc`) i .NET (CLR) funcionen sobre una idea molt semblant.

> 📡 **Canviant activament: contenidors**. Una màquina virtual de sistema emula un ordinador complet amb el seu propi sistema operatiu — aïlla molt, però és "pesada". Una alternativa moderna i més lleugera són els **contenidors** (Docker és el més conegut): en compte d'emular tot el hardware, comparteixen el nucli del sistema operatiu amfitrió i només aïllen l'aplicació i les seues dependències. Els veurem amb detall en la UP2, entorns de desenvolupament — de moment basta amb saber que "aïllar un programa de la resta del sistema" no sempre passa per una màquina virtual completa.

> 📡 **Canviant activament: WebAssembly (Wasm)**. És l'evolució més recent de la mateixa idea de "bytecode portable", però pensada per al navegador: un format que permet executar codi escrit en C, C++, Rust o fins i tot Java dins d'una pàgina web, a una velocitat pròxima a la nativa — alguna cosa que JavaScript per si sol no oferix. No substituïx JavaScript, el complementa en les parts d'una aplicació web que necessiten més rendiment (edició d'imatge o vídeo en el mateix navegador, videojocs, càlcul intensiu). En el desenvolupament web actual és on més està creixent esta idea de "màquina virtual de procés".

**🧪 Exercici 11 — JVM i WebAssembly, dues màquines virtuals de procés**
Torna a llegir l'avís sobre WebAssembly d'este punt — no cal buscar res més. En `exercici11.md`, respon amb les teues pròpies paraules: (1) en què s'assemblen la JVM i WebAssembly com a màquines virtuals de procés? (2) on s'usa cadascuna, i per què WebAssembly no substituïx JavaScript sinó que el complementa?

---

## 5. Classificació dels llenguatges de programació (CA 1e)

No hi ha una única forma de classificar els llenguatges; estes són les més habituals.

**Segons com s'executen:**

| Tipus | Com funciona | Exemples | On s'usen més |
|---|---|---|---|
| **Compilats** | El codi font es tradueix sencer, d'una vegada, a un executable | C, C++, Pascal | Software d'escriptori (execució ràpida, fitxers més pesats) |
| **Interpretats** | Un intèrpret executa el codi sense generar un executable natiu — molts (com Python) compilen abans internament a un bytecode que després processen (punt 3) | Python, PHP, JavaScript | Entorns web i scripting (menys recursos, més lents) |
| **Híbrids / virtuals** | Es compilen a codi intermedi (bytecode), que després interpreta una màquina virtual | Java, C# (en part) | Aplicacions que han de córrer en diverses plataformes sense recompilar |

> 💡 Esta classificació és la primera aproximació més útil per a començar, però no és una etiqueta rígida i excloent: com vam veure en el punt 3, la frontera entre compilat i interpretat cada vegada és més difusa (motors JIT com V8, eines com GraalVM...). Servix per a entendre el model *dominant* de cada llenguatge, no per a encasellar-lo.

**Segons el nivell d'abstracció** (com més s'assemblen al llenguatge natural enfront del llenguatge màquina):

| Nivell | Característica | Exemples |
|---|---|---|
| **Baix nivell** | Instruccions molt pròximes al hardware, accés directe a registres | Ensamblador |
| **Nivell mitjà** | Permet accedir a memòria i registres, però amb una sintaxi més llegible | C |
| **Alt nivell** | Sintaxi pròxima al llenguatge humà, abstrau els detalls del hardware | Python, Java, PHP |

**Segons el paradigma de programació** (la forma de plantejar la solució):

| Paradigma | Idea central | Exemple de llenguatge |
|---|---|---|
| **Imperatiu / procedimental** | Es descriu *pas a pas* com fer alguna cosa | C |
| **Orientat a objectes** | Es modela el problema com a objectes que interactuen | Java |
| **Funcional** | Es programa component funcions, evitant l'estat mutable | Haskell (i, parcialment, JavaScript o Python) |
| **Declaratiu** | Es descriu *què* es vol obtindre, no *com* obtindre-ho | SQL |

**Un mateix problema, dos paradigmes.** La diferència entre imperatiu i declaratiu es nota millor en codi que en definicions — per a "quedar-se amb els números parells d'una llista":

```python
# Imperatiu: es descriu pas a pas el "com"
parells = []
for n in numeros:
    if n % 2 == 0:
        parells.append(n)
```

```sql
-- Declaratiu: es descriu el "què", sense dir com recórrer-ho
SELECT * FROM numeros WHERE n % 2 = 0;
```

**A la pràctica, pocs llenguatges són "purs".** La taula de paradigmes classifica segons la idea *dominant* de cada llenguatge, no una etiqueta única i excloent: Python i JavaScript són fonamentalment imperatius i orientats a objectes, però incorporen funcions d'estil funcional (`map`, `filter`) sense cap problema; SQL és declaratiu, però molts motors permeten afegir lògica imperativa (procediments emmagatzemats en PL/SQL, T-SQL...). És habitual que un mateix llenguatge combine diversos paradigmes segons el que convinga en cada part del codi.

Finalment, en el context d'aplicacions web és habitual distingir entre **front-end** (la part visible, que corre en el navegador de l'usuari: HTML, CSS, JavaScript) i **back-end** (la lògica no visible, que corre en un servidor: Java, Python, PHP, SQL...). Qui domina còmodament ambdues parts es coneix com a **desenvolupador full-stack** — un dels perfils més demandats en desenvolupament web hui, i el que anirem treballant progressivament al llarg d'este cicle.

> 📡 **Actualitat**: la popularitat dels llenguatges canvia amb el temps. L'**índex TIOBE** (`tiobe.com/tiobe-index`) és una de les referències més consultades per a veure quins llenguatges estan en auge o en declivi — però és una fotografia mensual, no una veritat fixa: convé consultar-lo actualitzat en compte de memoritzar un rànquing.

**🧪 Exercici 12 — Classifica estos llenguatges**
En `exercici12.md`, per a Python, Java, C i JavaScript, indica en una taula Markdown: tipus d'execució (compilat/interpretat/híbrid), nivell d'abstracció i paradigma principal. Justifica cada resposta en una frase.

**🧪 Exercici 13 — El mateix problema, dos paradigmes**
Per al dashboard de finances personals, planteja la tasca "obtindre els usuaris que han gastat més de 100 € este mes". En `exercici13.md`, escriu una solució imperativa en pseudocodi (amb un bucle i una condició); en `exercici13.sql`, la solució declarativa (una sola consulta `SELECT` — no cal executar-la encara, només que la sintaxi siga correcta). En `exercici13.md`, compara ambdues: quina descriu el "com" i quina el "què"?

---

## 6. Eines del desenvolupament de software (CA 1f)

A més del llenguatge, un desenvolupador es recolza en eines que donen suport a cada fase del cicle de vida. Esta unitat només les **classifica**; aprofundirem en diverses d'elles en unitats posteriors.

### 6.1. Editor de codi / IDE

Un editor de text simple (el Bloc de notes) també pot escriure codi, però un **IDE** (*Integrated Development Environment*) afig eines integrades per a tot el cicle de codificació: autocompletat, ressaltat de sintaxi, detecció d'errors mentre escrius i depuració incorporada. Exemples: Visual Studio Code, Eclipse, IntelliJ. **Es treballa en detall en la UP2.**

### 6.2. Compilador / intèrpret

Tradueix codi font a codi objecte, intermedi o executable, o l'executa per mitjà d'un intèrpret o màquina virtual — és l'eina que materialitza tot el vist en els punts 3 i 5 d'esta unitat. Exemples: `javac`/`java`, el mateix intèrpret de Python, GCC. **UP1-UP2.**

### 6.3. Control de versions

Registra l'historial de canvis del codi i permet que diverses persones treballen sobre el mateix projecte sense sobreescriure's — ja ho vam avançar en el punt 2.3, en parlar de la fase de Codificació. Exemples: Git, GitHub. **UP3.**

```
$ git init
$ git add cambios.py
$ git commit -m "Primer commit"
```

### 6.4. Depuració i proves

Permet executar el programa pas a pas, inspeccionar el valor de les variables en cada moment, i automatitzar les comprovacions vistes en el punt 2.4 (proves unitàries, d'integració...) en compte de repetir-les a mà cada vegada. Exemples: el depurador integrat de l'IDE, JUnit. **UP5.**

### 6.5. Gestió de dependències i construcció del projecte

Instal·la biblioteques externes (retomant el concepte de biblioteca del punt 1.1) sense haver de descarregar-les i integrar-les a mà, i automatitza passos repetitius com compilar, executar proves o empaquetar el projecte. Exemples: `pip`, Maven, npm. **UP2.**

En Python, abans d'instal·lar res és habitual aïllar les dependències de cada projecte en un **entorn virtual** (`venv`): una còpia local de l'intèrpret i les seues biblioteques, independent de la instal·lació global del sistema i de la d'altres projectes — així el projecte A pot usar una versió d'una biblioteca i el projecte B una altra distinta, sense que xoquen entre si.

```
$ python -m venv .venv                    # crea l'entorn virtual en la carpeta .venv
$ source .venv/bin/activate               # l'activa (Linux/Mac); en Windows: .venv\Scripts\activate
(.venv) $ pip install matplotlib          # instal·la la biblioteca només dins d'este entorn
(.venv) $ pip freeze > requirements.txt   # registra les dependències del projecte
```

> 📡 **Un pas més: contenidors**. Un entorn virtual aïlla les dependències de Python, però no la resta del sistema (versió del sistema operatiu, altres programes instal·lats...). Quan eixe aïllament cal portar-lo també ahí — per exemple, perquè l'aplicació corra igual en qualsevol ordinador o servidor —, s'usa un **contenidor** (Docker és el més conegut), que ja vam veure com a concepte en el punt 4. És la mateixa idea de fons que un `venv`, però un nivell més avall — amb base i pràctica real ho treballarem en la UP2.

### 6.6. Anàlisi i documentació de codi

Revisa automàticament la qualitat del codi (codi duplicat, mal estil, possibles vulnerabilitats) i genera documentació tècnica a partir dels mateixos comentaris del codi font. Exemples: SonarQube, Javadoc. **UP7.**

> 📡 **Canviant activament: assistents de codi amb IA**. Eines com GitHub Copilot, o l'autocompletat intel·ligent ja integrat en molts IDEs actuals, suggerixen codi mentre escrius recolzant-se en models de llenguatge. No són una categoria nova: s'integren dins de l'editor/IDE (6.1). Estan canviant com s'escriu codi dia a dia, però continuen fent falta els mateixos fonaments d'esta unitat per a revisar i entendre el que suggerixen — no per a copiar-ho sense més.

> 💡 Exemple integrador: si més avant desenvolupem un **dashboard de finances personals** en Python amb una base de dades SQLite, usaríem com a mínim: un IDE (VS Code) per a escriure el codi, Git/GitHub per al control de versions, `pip` per a instal·lar biblioteques (per exemple, per a generar gràfics) i `pytest` per a provar que els càlculs són correctes. Cadascuna d'eixes eines cobrix una funcionalitat distinta dins del desenvolupament.

**🧪 Exercici 14 — Eines per a un projecte**
Per al projecte de "dashboard de finances personals" del punt 6, en `exercici14.md` indica quina eina de cada categoria de la taula usaries i per què, encara que hui no sàpies usar-les encara (busca-ho si cal).

**🧪 Exercici 15 — Instal·la i prova una eina**
Tria una categoria de la taula anterior amb una eina que no conegues encara (per exemple, un linter d'anàlisi de codi o un gestor de dependències distint al vist en classe) i instal·la-la en el teu equip. Prova-la des de la terminal integrada de VS Codium sobre algun dels fitxers que ja tens en la teua carpeta `UD01`. En `exercici15.md`, documenta en 4-5 línies: quin problema resol, quina orde vas usar per a instal·lar-la, i el resultat d'haver-la executat.

---

## 🎯 Repte de classe

Tria una aplicació que uses habitualment al mòbil (una app de missatgeria, de banca, de transport...). Investiga primer quines tecnologies té documentades públicament (la seua web de desenvolupadors, ofertes d'ocupació de l'empresa...); quan no troves res verificable, formula una hipòtesi raonada i digues-ho explícitament com a tal — distingir "ho sé", "ho he trobat documentat" i "ho estic deduint" és una habilitat tan important com el contingut tècnic. En VS Codium, crea `repte.md` dins de la teua carpeta `UD01` amb una fitxa que incloga:

1. Una hipòtesi raonada sobre quin(s) llenguatge(s) de programació es van usar per a la seua part visible i per a la seua lògica interna (front-end/back-end), amb almenys un argument tècnic de per què.
2. Una hipòtesi sobre si l'executable que corre al teu mòbil és compilat, interpretat o híbrid (justifica-ho amb el que sàpies d'Android/iOS i les màquines virtuals vistes en el punt 4).
3. Un esquema de les 7 fases del cicle de vida aplicat a eixa app: quins requisits creus que es van recollir en l'Anàlisi, i quin tipus de Manteniment rep (busca el seu historial d'actualitzacions en la botiga d'aplicacions com a pista).

**Plantilla orientativa per a `repte.md`** (pots seguir-la tal qual o adaptar-la):

```markdown
# Repte — [nom de l'app]

## 1. Llenguatges probables
- Front-end: ...
- Back-end: ...
- Argument tècnic: ...

## 2. Compilat, interpretat o híbrid
- Hipòtesi: ...
- Justificació (Android/iOS, màquines virtuals del punt 4): ...

## 3. Cicle de vida aplicat
- Requisits que creus que es van recollir en l'Anàlisi: ...
- Tipus de manteniment que rep, segons l'historial d'actualitzacions: ...
```

*Variació avaluable*: es pot demanar per parelles, comparant dos apps de la mateixa categoria (per exemple, dos apps bancàries) perquè l'alumnat contraste hipòtesis distintes.

---

<div style="page-break-after: always;"></div>

## Resum de la unitat

**1. El programa i els components del sistema** El software es classifica per la seua forma (programa, biblioteca, aplicació, suite) i per la seua funció (software de sistema vs. d'aplicació). Un programa en execució es recolza en memòria (RAM, volàtil), processador (cicle fetch-decode-execute) i perifèrics (entrada, eixida o ambdues) — programar és només la fase de codificació dins de desenvolupar software, que a més analitza, dissenya, prova, documenta i manté.

**2. El cicle de vida del software** Model en cascada, en 7 fases: anàlisi (requisits funcionals/no funcionals), disseny (arquitectònic i detallat, UML), codificació (bones pràctiques), proves (caixa negra/blanca, nivells), documentació d'usuari, explotació (estratègies d'implantació) i manteniment (correctiu, evolutiu, adaptatiu, perfectiu) — cada fase genera la seua pròpia documentació i amb rols que poden solapar-se. La cascada és el model de referència per a entendre les fases, però hui la majoria d'equips usa metodologies àgils (CA 1g, es veuen en la UP6); altres models clàssics (iteratiu-incremental, en espiral, prototipatge) sí que formen part d'esta unitat.

**3. Codi font, objecte i executable** En compilació directa (C), el codi font es compila a codi objecte i este s'enllaça (de forma estàtica o dinàmica) amb biblioteques i particularitats del SO per a donar l'executable natiu final; en el model de codi intermedi (Java), el font compila a bytecode i és una màquina virtual, no un enllaçador, qui l'executa — codi objecte i codi intermedi no són sinònims, encara que tots dos siguen un pas a mig camí. L'esquema es veu distint segons el llenguatge siga compilat, híbrid o interpretat, i pot necessitar executables distints segons la plataforma de destinació. La frontera compilat/interpretat ja no és tan taxativa: motors JIT com V8 compilen JavaScript sobre la marxa, i eines com GraalVM compilen bytecode Java a executable natiu.

**4. Codi intermedi i màquines virtuals** Les màquines virtuals (de sistema o de procés) permeten portabilitat: la JVM executa el mateix bytecode `.class` en qualsevol sistema operatiu, la idea darrere de "write once, run anywhere" — Python i .NET seguixen un plantejament semblant, i va nàixer per a resoldre la manca de portabilitat entre sistemes operatius dels anys 90. Els contenidors (Docker) i WebAssembly (bytecode portable per al navegador) són evolucions més recents de la mateixa idea.

**5. Classificació dels llenguatges** Es classifiquen segons com s'executen (compilats, interpretats, híbrids), el seu nivell d'abstracció (baix, mitjà, alt) i el seu paradigma dominant (imperatiu, orientat a objectes, funcional, declaratiu — la majoria combina diversos, i un mateix problema es resol de forma distinta en cada paradigma) — a més de la distinció front-end/back-end, i el perfil full-stack que domina ambdues.

**6. Eines del desenvolupament de software** IDE, compiladors/intèrprets, control de versions, depuració i proves, gestió de dependències, i anàlisi/documentació de codi — cada categoria dona suport a una fase distinta del cicle de vida del punt 2, amb ordes i exemples reals (Git, pip, venv) que es treballaran en detall a partir de la UP2, on entraran també els contenidors (Docker); els assistents de codi amb IA són la novetat més activa dins de l'editor/IDE, sense substituir els fonaments d'esta unitat.

---

## 📚 Per a saber-ne més (opcional, no avaluable)

- Índex TIOBE (popularitat de llenguatges, actualitzat mensualment): https://www.tiobe.com/tiobe-index/
- Documentació oficial de la JVM: https://docs.oracle.com/javase/specs/

### 🧭 Per què et servirà això de veritat

- En una entrevista tècnica és habitual que et pregunten per què triaries un llenguatge compilat o interpretat per a un projecte — respondre amb seguretat (rendiment enfront de rapidesa de desenvolupament, portabilitat...) és molt més creïble si entens el perquè, no només el nom.
- En entrar en una empresa "heretaràs" un projecte que seguix algun model de cicle de vida (probablement àgil, però amb restes de cascada en la documentació) — saber reconèixer en quina fase està t'ajuda a entendre què s'espera de tu des del primer dia.
- Justificar per què documentes el teu codi, per què uses control de versions o per què una empresa exigix passar un analitzador de codi abans de fusionar un canvi no és "burocràcia": és justament el que un responsable tècnic avalua durant un període de prova.
