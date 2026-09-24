<div style="text-align: center;">

<img src="data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCA0MDAgNDAwIiB3aWR0aD0iMTgwIiBoZWlnaHQ9IjE4MCI+CiAgPGNpcmNsZSBjeD0iMjAwIiBjeT0iMjAwIiByPSIxNzAiIGZpbGw9IiNGMEZERkEiLz4KICA8Y2lyY2xlIGN4PSIyMDAiIGN5PSIyMDAiIHI9IjE3MCIgZmlsbD0ibm9uZSIgc3Ryb2tlPSIjOTlGNkU0IiBzdHJva2Utd2lkdGg9IjIiLz4KICA8dGV4dCB4PSIyMDAiIHk9IjI0OCIgZm9udC1mYW1pbHk9IidDb3VyaWVyIE5ldycsIENvdXJpZXIsIG1vbm9zcGFjZSIgZm9udC1zaXplPSIxNTAiIGZvbnQtd2VpZ2h0PSI3MDAiIGZpbGw9IiMwRjc2NkUiIHRleHQtYW5jaG9yPSJtaWRkbGUiPiZndDtfPC90ZXh0Pgo8L3N2Zz4K" width="180" alt="Logotip EDE"/>

<h1>Unitat 6</h1>
<h2>Proves i depuració</h2>

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

1. Planificació i tipus de proves (CA 3a)
2. Casos de prova i proves de codi (CA 3b)
3. Proves unitàries, automatització i depuració (CA 3c, 3d, 3e, 3f, 3g)
4. Repte de classe
5. Resum de la unitat
6. Per a saber-ne més

<div style="page-break-after: always;"></div>

**RA cobert:** RA3 (CA 3a-3g) — Verifica el funcionament de programes, dissenyant i realitzant proves.

> 📌 **Nota**: enguany eixiu de pràctiques a l'empresa el 26/04, així que esta unitat se centra en les CA que es poden treballar i demostrar a fons a l'aula amb el temps disponible. La documentació d'incidències (CA 3h) i els dobles de prova (CA 3i) — també part de RA3 — es treballen i s'avaluen durant la teua formació en l'empresa.

> 💻 **Com treballar els exercicis d'esta unitat**: continua en la teua carpeta `UD06_ElTeuNom` dins del repositori del tauler de finances. Usaràs `pytest` com a ferramenta de proves — ja tens el pipeline de CI d'UD3 preparat per a executar-les automàticament en cada `push`.

## 🎯 Conceptes clau

En acabar esta unitat sabràs:
- Planificar i dissenyar proves de codi (funcionals, estructurals, de regressió) identificant casos de prova, cobriment, valors límit i classes d'equivalència.
- Escriure proves unitàries automatitzades i usar el depurador de l'IDE per a localitzar l'origen d'una fallada quan una prova no passa.
- Integrar proves i depuració en un mateix flux de treball: escriure una prova, veure-la fallar, depurar la causa i comprovar que el pipeline de CI la valida.

---

## 1. Planificació i tipus de proves (CA 3a)

### 1.1. Per què planificar abans de provar "a veure què ix"

Provar codi sense pla és executar el programa i mirar si "sembla que funciona". Planificar significa decidir, abans d'escriure una sola prova, **què** es comprovarà i **com se sabrà** que el resultat és correcte.

### 1.2. Tipus de proves

> 🗺️ **Mapa visual — tipus de prova**

| Tipus | Què comprova | Exemple en el dashboard |
|---|---|---|
| **Funcional** | Que una funcionalitat fa el que ha de fer, des de fora (sense mirar el codi intern) | Registrar una despesa guarda correctament l'import i la data |
| **Estructural** | Que el codi s'executa correctament per dins (branques, condicions) | Que ambdós branques de l'`if` de categorització automàtica s'executen almenys una vegada |
| **De regressió** | Que un canvi nou no ha trencat alguna cosa que abans funcionava | En afegir pressupostos (UD4), les proves d'UD1-UD3 del dashboard continuen passant |

**🧪 Exercici 1 — Classificar proves del dashboard**
En `exercici1.md`, descriu 3 proves distintes que aplicaries al tauler de finances — una funcional, una estructural i una de regressió — indicant què comprovaria cadascuna exactament.

---

## 2. Casos de prova i proves de codi (CA 3b)

### 2.1. Procediments i casos de prova

Un **cas de prova** documenta: quina entrada s'usa, què es fa amb ella i quin resultat s'espera. Sense açò, "provar" es reduïx a executar i mirar a ull.

| Camp | Exemple |
|---|---|
| Entrada | `Transaccio(import_=-45.20, categoria="Alimentació")` |
| Acció | Cridar a `es_despesa()` |
| Resultat esperat | `True` |

### 2.2. Cobriment, valors límit i classes d'equivalència

> 🗺️ **Mapa visual — tècniques de disseny de casos de prova**

| Tècnica | Què resol | Exemple en el dashboard |
|---|---|---|
| **Cobriment** | Quin percentatge del codi han executat les meues proves? | S'ha provat tant la branca "hi ha categoria guardada" com "no n'hi ha"? |
| **Valors límit** | Els errors s'amaguen en les vores, no en el centre | Provar un pressupost amb despesa = 0, = límit exacte, i = límit+0.01 |
| **Classes d'equivalència** | Agrupar entrades que haurien de comportar-se igual, per a no repetir proves redundants | Tots els imports negatius són "despesa"; no cal provar -1, -50 i -1000 per separat |

> 🧾 **No cal memoritzar de memòria cada nom tècnic**: tindràs la chuleta amb les tres tècniques i el seu propòsit. S'avalua que sàpies **aplicar-les** en dissenyar un cas de prova, no que recites la seua definició exacta.

**🧪 Exercici 2 — Casos de prova amb valors límit**
En `exercici2.md`, dissenya 4 casos de prova per a la funció que comprova si un pressupost s'ha superat, usant almenys un valor límit (just en el límit) i aplicant classes d'equivalència per a no repetir casos redundants.

---

## 3. Proves unitàries, automatització i depuració (CA 3c, 3d, 3e, 3f, 3g)

### 3.1. Proves unitàries amb pytest (CA 3f)

Una **prova unitària** comprova una única funció o mètode de forma aïllada.

```python
# test_transaccio.py
from dashboard import Transaccio

def test_es_despesa_amb_import_negatiu():
    t = Transaccio(-45.20, "Alimentació", "2027-01-10")
    assert t.es_despesa() == True

def test_es_despesa_amb_import_positiu():
    t = Transaccio(1500.00, "Nòmina", "2027-01-01")
    assert t.es_despesa() == False
```

> 🧾 **No cal memoritzar la sintaxi de pytest**: tindràs la chuleta amb `assert`, com anomenar funcions de prova i com executar-les. S'avalua que la prova comprove el correcte amb la lògica correcta, no que recordes la sintaxi exacta sense consultar-la.

**🧪 Exercici 3 — Proves unitàries del dashboard**
En `test_dashboard.py`, escriu almenys 4 proves unitàries noves (usant les tècniques del punt 2) per a funcions del dashboard que encara no tinguen prova. Documenta en `exercici3.md` el resultat d'executar-les.

### 3.2. Ferramentes de depuració de l'entorn i punts de ruptura (CA 3c, 3d)

El mateix IDE no és només un editor: porta integrades ferramentes per a provar i depurar sense eixir d'ell — executar proves amb un clic, veure el seu resultat en un panell dedicat, i arrancar el **depurador** sobre qualsevol línia de codi.

Quan una prova **falla** i no és evident per què, el depurador (`▶️ Debug`, no `▶️ Run`) permet:

- Col·locar un **punt de ruptura** (*breakpoint*) en la línia on alguna cosa no quadra — l'execució es detén justament ací.
- **Avançar pas a pas** (*step over* / *step into*) per a veure exactament què fa el programa línia a línia.

| Acció del depurador | Què fa |
|---|---|
| Breakpoint | Pausa l'execució en eixa línia exacta |
| Step over | Executa la línia actual i passa a la següent, sense entrar en les funcions que crida |
| Step into | Entra dins de la funció que s'està cridant, línia a línia |
| Continue | Reprén l'execució normal fins al següent breakpoint |

**🧪 Exercici 4 — Trobar una fallada amb el depurador**
Se't lliurarà una funció del dashboard amb un error subtil (per exemple, en el càlcul d'un pressupost) i una prova que falla en executar-la. En `exercici4.md`, documenta: on vas col·locar el breakpoint, què vas veure en avançar pas a pas, i en quina línia exacta estava l'error.

### 3.3. Inspeccionar i modificar en temps d'execució (CA 3e)

Amb l'execució pausada en un breakpoint, el panell de **variables** del depurador mostra el valor de cada variable en eixe moment exacte — i en molts IDE també permet **modificar-lo** allí mateix, sense parar i reescriure codi, per a comprovar a l'instant si un valor distint hauria evitat la fallada.

> ⚠️ **Pla B si el depurador de l'IDE falla o no està disponible**: la depuració per `print()` continua funcionant sempre, en qualsevol entorn, sense cap extensió: intercala `print(variable)` en els punts que vulgues inspeccionar. És menys còmode que un depurador visual, però mai falla — bona idea tindre-ho present també en la VM portàtil, on pot ser que el depurador gràfic no estiga configurat.

### 3.4. Proves automàtiques (CA 3g)

Ja vas veure en UD3 com un pipeline de CI (GitHub Actions) executa les proves automàticament en cada `push`. Eixa és exactament la forma de convertir les proves unitàries d'este punt en **proves automàtiques**: no depenen que algú se'n recorde d'executar-les a mà.

**🧪 Exercici 5 — De la prova al pipeline, passant pel depurador**
Este exercici integra tot el punt 3: (1) escriu una prova unitària nova per a una funció del dashboard que **encara tinga un error** (introduïx-ne un tu mateix/a si cal); (2) executa-la i comprova que falla; (3) usa el depurador (breakpoint + inspecció de variables) per a localitzar la causa exacta; (4) corregeix el codi; (5) fes `push` i comprova en la pestanya *Actions* de GitHub que el pipeline de CI ara passa en verd. Documenta els 5 passos en `exercici5.md`.

---

## 🎯 Repte de classe

Deixaràs provada i depurada d'extrem a extrem la funcionalitat de **pressupostos per categoria** (UD4-UD5) del tauler de finances personals.

En la teua carpeta `UD06`, crea `test_pressupost.py` i `repte.md` amb:

1. **Casos de prova dissenyats** (CA 3b): almenys 4 casos de prova per a la comprovació de pressupost superat, incloent-hi un valor límit.
2. **Proves unitàries automàtiques** (CA 3f, 3g): implementades en `test_pressupost.py` i verificades en el teu pipeline de CI.
3. **Una fallada real depurada** (CA 3c, 3d, 3e): introduïx deliberadament un error menut en el codi de pressupostos, localitza'l amb el depurador (breakpoint + inspecció de variables) i documenta el procés pas a pas.

**Plantilla orientativa per a `repte.md`:**

```markdown
# Repte — Pressupostos provats i depurats

## 1. Casos de prova
| Entrada | Acció | Resultat esperat |
|---|---|---|
| ___ | ___ | ___ |

## 2. Proves automàtiques
- Fitxer: test_pressupost.py
- Resultat en CI: ___

## 3. Depuració d'una fallada real
- Breakpoint col·locat en: ___
- Què va mostrar la inspecció de variables: ___
- Línia de l'error i correcció aplicada: ___
```

*Variació avaluable*: qui ho preferisca pot aplicar este mateix repte a la funcionalitat d'exportació (PDF/CSV) en compte dels pressupostos, sempre que cobrisca els 3 punts anteriors.

---

<div style="page-break-after: always;"></div>

## Resum de la unitat

**1. Planificació i tipus de proves** Planificar abans de provar significa decidir què es comprova i com se sabrà que és correcte; les proves poden ser funcionals, estructurals o de regressió.

**2. Casos de prova i proves de codi** Un cas de prova documenta entrada, acció i resultat esperat; cobriment, valors límit i classes d'equivalència ajuden a dissenyar casos de prova eficaços sense repetir el redundant.

**3. Proves unitàries, automatització i depuració** Les proves unitàries comproven funcions aïllades i s'automatitzen amb el pipeline de CI d'UD3; el mateix entorn oferix ferramentes de depuració — breakpoints, avanç pas a pas i inspecció (o modificació) de variables en temps d'execució — amb `print()` com a alternativa que mai falla.

**I el que continua en l'empresa**: documentar incidències de forma reproduïble (CA 3h) i usar dobles de prova per a aïllar components (CA 3i) són la continuació natural del que has aprés ací — les treballaràs i demostraràs durant la teua formació en l'empresa.

---

## 📚 Per a saber-ne més (opcional, no avaluable)

- Documentació oficial de pytest: https://docs.pytest.org/
- Depuració en VS Code: https://code.visualstudio.com/docs/editor/debugging
- Martin Fowler — *Mocks Aren't Stubs* (dobles de prova, article clàssic, útil per a quan ho veges en empresa): https://martinfowler.com/articles/mocksArentStubs.html

### 🧭 Per què et servirà açò de veritat

Escriure codi que "funciona a la primera" no és realista en cap projecte real — el que marca la diferència és la rapidesa amb què localitzes i confirmes que alguna cosa està trencada, i esta unitat és exactament el conjunt de ferramentes (proves, depurador, CI) amb què es fa açò tots els dies en qualsevol equip de desenvolupament.
