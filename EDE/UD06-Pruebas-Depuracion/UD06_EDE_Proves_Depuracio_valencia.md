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

1. Planificació i tipus de proves (CA 3a, 3c)
2. Casos de prova i proves de codi (CA 3b)
3. Proves unitàries, automatització i depuració (CA 3f, 3g, 3d, 3e)
4. Documentació d'incidències (CA 3h)
5. Dobles de prova (CA 3i)
6. Repte de classe
7. Resum de la unitat
8. Per a saber-ne més

<div style="page-break-after: always;"></div>

**RA cobert:** RA3 (CA 3a-3i) — Verifica el funcionament de programes, dissenyant i realitzant proves.

> 💻 **Com treballar els exercicis d'esta unitat**: continua en la teua carpeta `UD06_ElTeuNom` dins del repositori del tauler de finances. Usaràs `pytest` com a ferramenta de proves — ja tens el pipeline de CI d'UD3 preparat per a executar-les automàticament en cada `push`.

## 🎯 Conceptes clau

En acabar esta unitat sabràs:
- Planificar i dissenyar proves de codi (funcionals, estructurals, de regressió) identificant casos de prova, cobriment, valors límit i classes d'equivalència.
- Escriure proves unitàries automatitzades i usar el depurador de l'IDE per a localitzar l'origen d'una fallada quan una prova no passa.
- Documentar incidències amb la informació necessària perquè una altra persona puga reproduir-les, i usar dobles de prova per a aïllar el component que s'està provant.

---

## 1. Planificació i tipus de proves (CA 3a, 3c)

### 1.1. Per què planificar abans de provar "a veure què ix"

Provar codi sense pla és executar el programa i mirar si "sembla que funciona". Planificar significa decidir, abans d'escriure una sola prova, **què** es comprovarà i **com se sabrà** que el resultat és correcte.

### 1.2. Tipus de proves

> 🗺️ **Mapa visual — tipus de prova**

| Tipus | Què comprova | Exemple en el dashboard |
|---|---|---|
| **Funcional** | Que una funcionalitat fa el que ha de fer, des de fora (sense mirar el codi intern) | Registrar una despesa guarda correctament l'import i la data |
| **Estructural** | Que el codi s'executa correctament per dins (branques, condicions) | Que ambdós branques de l'`if` de categorització automàtica s'executen almenys una vegada |
| **De regressió** | Que un canvi nou no ha trencat alguna cosa que abans funcionava | En afegir pressupostos (UD4), les proves d'UD1-UD3 del dashboard continuen passant |

### 1.3. Ferramentes de depuració i prova que oferix l'entorn

El mateix IDE no és només un editor: porta integrades ferramentes per a provar i depurar sense eixir d'ell — executar proves amb un clic, veure el seu resultat en un panell dedicat, i arrancar el depurador sobre qualsevol línia de codi. En els punts 3.2 i 3.3 d'esta unitat les usaràs en detall sobre proves unitàries reals.

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

## 3. Proves unitàries, automatització i depuració (CA 3f, 3g, 3d, 3e)

### 3.1. Proves unitàries amb pytest

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

### 3.2. Depuració: punts de ruptura i seguiment pas a pas

Quan una prova **falla** i no és evident per què, el depurador de l'IDE (`▶️ Debug`, no `▶️ Run`) permet:

- Col·locar un **punt de ruptura** (*breakpoint*) en la línia on alguna cosa no quadra — l'execució es detén justament ací.
- **Avançar pas a pas** (*step over* / *step into*) per a veure exactament què fa el programa línia a línia.

| Acció del depurador | Què fa |
|---|---|
| Breakpoint | Pausa l'execució en eixa línia exacta |
| Step over | Executa la línia actual i passa a la següent, sense entrar en les funcions que crida |
| Step into | Entra dins de la funció que s'està cridant, línia a línia |
| Continue | Reprén l'execució normal fins al següent breakpoint |

**🧪 Exercici 3 — Trobar una fallada amb el depurador**
Se't lliurarà una funció del dashboard amb un error subtil (per exemple, en el càlcul d'un pressupost) i una prova que falla en executar-la. En `exercici3.md`, documenta: on vas col·locar el breakpoint, què vas veure en avançar pas a pas, i en quina línia exacta estava l'error.

### 3.3. Depuració: inspeccionar i modificar en temps d'execució

Amb l'execució pausada en un breakpoint, el panell de **variables** del depurador mostra el valor de cada variable en eixe moment exacte — i en molts IDE també permet **modificar-lo** allí mateix, sense parar i reescriure codi, per a comprovar a l'instant si un valor distint hauria evitat la fallada.

> ⚠️ **Pla B si el depurador de l'IDE falla o no està disponible**: la depuració per `print()` continua funcionant sempre, en qualsevol entorn, sense cap extensió: intercala `print(variable)` en els punts que vulgues inspeccionar. És menys còmode que un depurador visual, però mai falla — bona idea tindre-ho present també en la VM portàtil, on pot ser que el depurador gràfic no estiga configurat.

### 3.4. Proves automàtiques

Ja vas veure en UD3 com un pipeline de CI (GitHub Actions) executa les proves automàticament en cada `push`. Eixa és exactament la forma de convertir les proves unitàries d'este punt en **proves automàtiques**: no depenen que algú se'n recorde d'executar-les a mà.

**🧪 Exercici 4 — Proves unitàries en el pipeline**
Afig almenys 4 proves unitàries noves (usant les tècniques del punt 2) a `test_dashboard.py` i comprova que el teu pipeline de CI d'UD3 les executa correctament en el següent `push`. Documenta en `exercici4.md` el resultat.

---

## 4. Documentació d'incidències (CA 3h)

Una incidència mal documentada ("no funciona") no és reproduïble per ningú més. Una incidència ben documentada inclou:

| Camp | Exemple |
|---|---|
| **Passos per a reproduir** | 1. Crear pressupost de 100€ en "Oci". 2. Registrar despesa de 100.01€ |
| **Resultat esperat** | Hauria de mostrar avís de pressupost superat |
| **Resultat obtingut** | No mostra cap avís |
| **Entorn** | Python 3.12, branca `feature-pressupostos`, commit `a3f21e0` |

**🧪 Exercici 5 — Documentar una incidència real**
Provoca deliberadament una fallada en el teu dashboard (o usa'n una de real que hages trobat). En `exercici5.md`, documenta-la amb els 4 camps de la taula anterior, de forma que una altra persona poguera reproduir-la sense preguntar-te res més.

---

## 5. Dobles de prova (CA 3i)

Quan una classe depén d'una altra que és lenta, costa diners (una API externa) o encara no existix, se substituïx per un **doble de prova** que simula el seu comportament.

> 🗺️ **Mapa visual — tipus de doble de prova**

| Tipus | Què fa | Exemple en el dashboard |
|---|---|---|
| **Dummy** | Es passa com a paràmetre però mai s'usa de veritat | Un `Usuari` buit que només cal perquè compile una crida |
| **Stub** | Retorna sempre una resposta fixa, predefinida | Simular la resposta del banc sense connectar-se de veritat a la seua API |
| **Mock** | Com l'stub, però a més comprova que se'l va cridar correctament | Verificar que `exportar_pdf()` va ser cridat exactament una vegada |

**🧪 Exercici 6 — Un stub per al banc**
El dashboard importa moviments des d'un `Sistema bancari` extern (UD5). En `exercici6.py`, crea un stub que simule eixa importació retornant sempre una llista fixa de 3 transaccions, sense connectar-se a cap servei real. Escriu una prova unitària que use eixe stub.

---

## 🎯 Repte de classe

Deixaràs completament provada la funcionalitat de **pressupostos per categoria** (UD4-UD5) del tauler de finances personals.

En la teua carpeta `UD06`, crea `test_pressupost.py` i `repte.md` amb:

1. **Casos de prova dissenyats** (CA 3b): almenys 4 casos de prova per a la comprovació de pressupost superat, incloent-hi un valor límit.
2. **Proves unitàries automàtiques** (CA 3f, 3g): implementades en `test_pressupost.py` i verificades en el teu pipeline de CI.
3. **Una fallada real depurada** (CA 3d, 3e): introduïx deliberadament un error menut en el codi de pressupostos, localitza'l amb el depurador (breakpoint + inspecció de variables) i documenta el procés.
4. **Incidència documentada** (CA 3h): la incidència de la fallada anterior, amb els 4 camps del punt 4.
5. **Un doble de prova** (CA 3i): si la teua comprovació de pressupost depén d'una altra classe (per exemple, `Categoria` o `Usuari`), substituïx-la per un stub en almenys una prova.

**Plantilla orientativa per a `repte.md`:**

```markdown
# Repte — Pressupostos provats d'extrem a extrem

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
- Línia de l'error: ___

## 4. Incidència documentada
- Passos per a reproduir: ___
- Resultat esperat / obtingut: ___
- Entorn: ___

## 5. Doble de prova
- Classe substituïda: ___
- Tipus de doble usat: ___
```

*Variació avaluable*: qui ho preferisca pot aplicar este mateix repte a la funcionalitat d'exportació (PDF/CSV) en compte dels pressupostos, sempre que cobrisca els 5 punts anteriors.

---

<div style="page-break-after: always;"></div>

## Resum de la unitat

**1. Planificació i tipus de proves** Planificar abans de provar significa decidir què es comprova i com se sabrà que és correcte; les proves poden ser funcionals, estructurals o de regressió, i el mateix IDE oferix ferramentes integrades per a executar-les i depurar-les.

**2. Casos de prova i proves de codi** Un cas de prova documenta entrada, acció i resultat esperat; cobriment, valors límit i classes d'equivalència ajuden a dissenyar casos de prova eficaços sense repetir el redundant.

**3. Proves unitàries, automatització i depuració** Les proves unitàries comproven funcions aïllades i s'automatitzen amb el pipeline de CI d'UD3; quan una prova falla, el depurador permet pausar l'execució (breakpoints), avançar pas a pas i inspeccionar (o modificar) variables en temps d'execució — amb `print()` com a alternativa que mai falla.

**4. Documentació d'incidències** Una incidència reproduïble per una altra persona documenta passos, resultat esperat, resultat obtingut i entorn.

**5. Dobles de prova** Dummy, stub i mock substituïxen una dependència lenta, costosa o inexistent per a poder provar un component de forma aïllada.

---

## 📚 Per a saber-ne més (opcional, no avaluable)

- Documentació oficial de pytest: https://docs.pytest.org/
- Depuració en VS Code: https://code.visualstudio.com/docs/editor/debugging
- Martin Fowler — *Mocks Aren't Stubs* (dobles de prova, article clàssic): https://martinfowler.com/articles/mocksArentStubs.html

### 🧭 Per què et servirà açò de veritat

Escriure codi que "funciona a la primera" no és realista en cap projecte real — el que marca la diferència és la rapidesa amb què localitzes i confirmes que alguna cosa està trencada, i esta unitat és exactament el conjunt de ferramentes (proves, depurador, dobles) amb què es fa açò tots els dies en qualsevol equip de desenvolupament.
