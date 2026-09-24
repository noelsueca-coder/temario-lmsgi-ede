<div style="text-align: center;">

<img src="data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCA0MDAgNDAwIiB3aWR0aD0iMTgwIiBoZWlnaHQ9IjE4MCI+CiAgPGNpcmNsZSBjeD0iMjAwIiBjeT0iMjAwIiByPSIxNzAiIGZpbGw9IiNGMEZERkEiLz4KICA8Y2lyY2xlIGN4PSIyMDAiIGN5PSIyMDAiIHI9IjE3MCIgZmlsbD0ibm9uZSIgc3Ryb2tlPSIjOTlGNkU0IiBzdHJva2Utd2lkdGg9IjIiLz4KICA8dGV4dCB4PSIyMDAiIHk9IjI0OCIgZm9udC1mYW1pbHk9IidDb3VyaWVyIE5ldycsIENvdXJpZXIsIG1vbm9zcGFjZSIgZm9udC1zaXplPSIxNTAiIGZvbnQtd2VpZ2h0PSI3MDAiIGZpbGw9IiMwRjc2NkUiIHRleHQtYW5jaG9yPSJtaWRkbGUiPiZndDtfPC90ZXh0Pgo8L3N2Zz4K" width="180" alt="Logotip EDE"/>

<h1>Unitat 3</h1>
<h2>Control de versions</h2>

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

1. Fonaments del control de versions (CA 4f)
2. Repositoris remots i treball col·laboratiu (CA 4h)
3. Integració contínua (CA 4i)
4. Repte de classe
5. Resum de la unitat
6. Per a saber-ne més

<div style="page-break-after: always;"></div>

**RA cobert:** RA4 (CA 4f, 4h, 4i) — Optimitza codi usant les eines disponibles en l'entorn de desenvolupament (control de versions, repositoris remots i integració contínua).

> 💡 **Nota d'estudi**: esta unitat no cobreix tot el RA4 — només les lletres 4f, 4h i 4i. La resta de lletres de RA4 (refactorització, anàlisi de codi, documentació de classes...) pertanyen a una altra unitat de programació que es treballa íntegrament a l'empresa. Ací ens centrem només en control de versions, repositoris remots i integració contínua.

> 💻 **Com treballar els exercicis d'esta unitat**: seguix usant la teua carpeta `UD03_ElTeuNom`, però esta vegada converteix-la en un repositori Git real des del primer exercici. Continuaràs treballant sobre el projecte del **tauler de finances personals** que vas arrancar en UD1 i vas configurar en UD2 — a partir d'ara, cada canvi que faces sobre ell queda registrat amb control de versions.

## 🎯 Conceptes clau

En acabar esta unitat sabràs:
- Usar Git per a registrar l'historial d'un projecte: commits, branques i fusions, incloent-hi la resolució de conflictes.
- Treballar amb un repositori remot (GitHub) de forma col·laborativa: clonar, sincronitzar canvis i revisar codi mitjançant Pull Requests.
- Configurar un pipeline bàsic d'integració contínua que execute proves automàticament cada vegada que es puja codi.

---

## 1. Fonaments del control de versions (CA 4f)

### 1.1. Quin problema resol

> 📜 **Història útil, ja no s'usa així**: abans de Git (2005), el més habitual eren sistemes de control de versions **centralitzats** (CVS, Subversion/SVN): un únic servidor guardava l'historial, i sense connexió a ell no podies ni consultar versions antigues. Git és **distribuït**: cada còpia del repositori conté l'historial complet. Açò continua sent la raó tècnica per la qual Git funciona sense connexió i per la qual GitHub és "només" un dels molts llocs on allotjar una còpia remota, no l'únic lloc on existix l'historial.

Sense control de versions, "guardar versions" d'un projecte es convertix en açò:

```
dashboard_final.py
dashboard_final_v2.py
dashboard_final_v2_BO.py
dashboard_final_v2_BO_de_veritat.py
```

Amb Git, existix un únic fitxer, i el seu historial complet de canvis viu en una carpeta oculta (`.git`) dins del mateix projecte.

### 1.2. Estructura de Git: les tres zones

| Zona | Què conté | Comanda típica per a passar a la següent |
|---|---|---|
| **Directori de treball** | Els fitxers tal com els veus i edites | `git add` |
| **Àrea de preparació (staging / índex)** | Els canvis marcats per al pròxim commit | `git commit` |
| **Repositori (`.git`)** | L'historial de commits ja guardat | `git push` (cap a un remot) |

Cada **commit** és una fotografia del projecte en un moment donat, amb un missatge que explica què va canviar i per què. `HEAD` és un punter que indica "on estàs ara" dins d'eixe historial.

### 1.3. Branques i fusió (branches i merge)

Una **branca** (*branch*) és una línia de desenvolupament independent. `main` (o `master`) sol ser la branca principal; es creen branques noves per a provar coses sense tocar el codi que ja funciona.

```
main:     A---B---C-------F
                    \     /
feature:             D---E
```

En acabar el treball en una branca, es **fusiona** (*merge*) de nou. Si les dos branques van canviar les mateixes línies del mateix fitxer, Git no pot decidir per tu: apareix un **conflicte de fusió**, que es resol a mà triant (o combinant) quina versió es queda.

> 🗺️ **Mapa visual — d'un canvi a un commit fusionat**

| Pas | Zona | Comanda |
|---|---|---|
| 1. Edites un fitxer | Directori de treball | — |
| 2. Marques el canvi | Àrea de preparació | `git add fitxer` |
| 3. Confirmes el canvi | Repositori local | `git commit -m "missatge"` |
| 4. Guardes el treball en una línia a banda | Branca nova | `git branch`, `git checkout` (o `git switch`) |
| 5. Incorpores eixa línia a `main` | Fusió | `git merge nom-branca` |

### 1.4. Git integrat en l'IDE

Des d'UD1 uses VS Codium; el seu panell **Control del codi font** (icona de branca en la barra lateral) fa visualment el mateix que les comandes de dalt: fitxers modificats en taronja, botó "+" per a passar-los a preparació, camp de text i ✓ per al commit, i un historial gràfic de branques amb extensions com *GitLens*.

> 🧾 **No cal memoritzar les comandes de memòria**: tindràs una chuleta amb les comandes de Git vistes en esta unitat (`add`, `commit`, `branch`, `checkout`/`switch`, `merge`, `clone`, `push`, `pull`, `fetch`). El que s'avalua és que sàpies **quan** usar cadascuna — en l'IDE o per terminal, el flux de fons és el mateix.

**🧪 Exercici 1 — Primer repositori del dashboard**
En la teua carpeta del tauler de finances (UD1-UD2), executa `git init`. Fes almenys 3 commits amb missatges descriptius (per exemple: afegir estructura inicial, afegir funció de càlcul de saldo, afegir validació de dades). Documenta en `exercici1.md` el resultat de `git log --oneline`.

**🧪 Exercici 2 — Branca, canvi i fusió amb conflicte**
Crea una branca `feature-categories`. En ella, modifica la mateixa línia d'un fitxer que també vas a modificar (de forma distinta) en `main`. Fusiona `feature-categories` en `main` i resol el conflicte que apareixerà. En `exercici2.md`, enganxa el fragment de conflicte tal com el va mostrar Git (amb les marques `<<<<<<<`, `=======`, `>>>>>>>`) i explica en dos línies què vas triar i per què.

---

## 2. Repositoris remots i treball col·laboratiu (CA 4h)

### 2.1. Repositoris remots

Un repositori local viu només en el teu equip. Un **repositori remot** (GitHub, GitLab...) és una còpia allotjada en un servidor que permet compartir-lo, fer-ne còpia de seguretat i treballar en equip.

| Operació | Sentit | Comanda |
|---|---|---|
| **Clonar** | Remot → nova còpia local completa | `git clone url` |
| **Pujar** | Local → remot | `git push` |
| **Descarregar i fusionar** | Remot → local | `git pull` |
| **Descarregar sense fusionar** | Remot → local (només consultar) | `git fetch` |

**🧪 Exercici 3 — Del repositori local a GitHub**
Crea un repositori buit a GitHub i connecta el teu repositori local del dashboard com a remot (`git remote add origin ...`). Puja el teu historial (`git push`). Clona el repositori en una altra carpeta distinta del teu equip per a comprovar que l'historial complet arriba intacte. Captura en `exercici3.md` l'URL del repositori.

### 2.2. Fluxos de treball col·laboratius

En equip no es treballa directament sobre `main`: el flux habitual és

1. Cada persona crea la seua pròpia branca per a la funcionalitat en què treballa (`feature/nom-funcionalitat`).
2. Puja la seua branca al remot (`git push origin feature/...`).
3. Obri una **Pull Request** (PR): una proposta de fusió d'eixa branca cap a `main`, visible i comentable per la resta de l'equip.
4. Algú més **revisa el codi** (*code review*): comenta, demana canvis o aprova.
5. Només llavors es fusiona la PR en `main`.

> 📡 **Per què importa hui**: és exactament així com incorporaràs més avant (UD4-UD6) els diagrames i les proves del tauler de finances — cada millora entra en `main` a través d'una Pull Request revisada, mai directament.

**🧪 Exercici 4 — Simular un flux de Pull Request**
Crea una branca `feature-informe-mensual` amb un canvi menut i funcional sobre el dashboard. Puja-la i obri una Pull Request a GitHub (si treballes en parella, demana al teu company/a que la revise i comente; si treballes sol/a, deixa almenys un comentari d'autorevisió assenyalant algo a millorar). Fusiona la PR des de la mateixa interfície de GitHub. En `exercici4.md`, enllaça la PR ja tancada.

### 2.3. Pla B: quan el remot falla

GitHub pot estar caigut, l'aula es pot quedar sense xarxa, o el teu compte pot tindre un problema puntual de permisos. Cap d'eixes situacions t'impedix continuar treballant:

- Continua fent `commit` en local amb normalitat — l'historial no depén de la xarxa.
- Quan torne la connexió, un únic `git push` sincronitza tot allò acumulat.
- Si vas a treballar fora de l'aula sense garantia de xarxa (per exemple, en la VM portàtil), configura Git una sola vegada (`git config --global user.name/email`) i ja tens control de versions disponible sense dependre de GitHub en cap moment.

---

## 3. Integració contínua (CA 4i)

### 3.1. Què és i què resol

La **integració contínua (CI)** executa automàticament, en un servidor i no en el teu equip, tasques com instal·lar dependències i executar les proves del projecte cada vegada que puges codi. L'objectiu: detectar com més prompte millor si un canvi ha trencat alguna cosa, sense dependre que algú se'n recorde d'executar les proves a mà.

> ⚠️ **Què NO és esta unitat**: la CI encara no inclou el **desplegament** automàtic de l'aplicació (això és *Continuous Deployment*, CD) — ací només automatitzem la verificació del codi, no la seua publicació.

### 3.2. Un pipeline bàsic amb GitHub Actions

GitHub Actions definix el pipeline en un fitxer YAML dins de `.github/workflows/`:

```yaml
name: Proves del dashboard
on: [push]
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: Instal·lar dependències
        run: pip install -r requirements.txt
      - name: Executar proves
        run: pytest
```

Cada `push` a GitHub dispara este flux automàticament; el resultat (✅ o ❌) apareix junt al commit i en qualsevol Pull Request oberta.

> 🧾 **No cal memoritzar la sintaxi YAML**: tindràs disponible esta plantilla com a chuleta. El que s'avalua és que entengues què fa cada bloc (`on`, `jobs`, `steps`) i en quin moment del flux de treball es dispara, no que l'escrigues de memòria des de zero.

### 3.3. Pla B: quan el pipeline al núvol falla

GitHub Actions té quotes d'ús gratuïtes que es poden esgotar, i de vegades un workflow queda mal configurat o no s'executa. Abans de dependre'n a classe, tingues sempre a mà un script equivalent que pugues executar tu mateix en local:

```bash
#!/bin/bash
# run-tests.sh — mateix contingut que el job de CI, executat a mà
pip install -r requirements.txt
pytest
```

Així, si el pipeline al núvol falla, `./run-tests.sh` demostra exactament el mateix sense dependre de cap servei extern. Tin este script preparat també en la teua VM portàtil.

**🧪 Exercici 5 — Pipeline de CI per al dashboard**
Afig el fitxer `.github/workflows/tests.yml` (amb el contingut del punt 3.2, adaptat al teu projecte) al repositori del dashboard. Fes un commit i comprova en la pestanya *Actions* de GitHub que s'executa. Si encara no tens proves automàtiques, afig almenys una funció senzilla amb una prova mínima (`assert`) perquè el pipeline tinga alguna cosa real a executar. Documenta en `exercici5.md` una captura del resultat (✅ o ❌) i, si alguna cosa va fallar, com ho vas solucionar.

---

## 🎯 Repte de classe

Deixaràs el repositori del **tauler de finances personals** organitzat amb un flux de treball col·laboratiu complet i funcionant d'extrem a extrem.

En el repositori ja creat en l'Exercici 3, crea `repte.md` amb:

1. **Historial net** (CA 4f): almenys 2 branques de funcionalitat distintes, cadascuna fusionada en `main` mitjançant la seua pròpia Pull Request (pots reutilitzar les dels exercicis 2 i 4 si ja ho complixen, o crear-ne de noves).
2. **Col·laboració documentada** (CA 4h): enllaça les Pull Requests fusionades i explica en 3-4 línies què va revisar (o què s'hauria revisat) en cadascuna abans de fusionar-la.
3. **CI funcionant** (CA 4i): captura de la pestanya *Actions* mostrant que el pipeline es va executar correctament sobre l'última fusió.
4. **Pla B aplicat**: descriu breument què faries si, el dia del lliurament, GitHub estiguera caigut — quina evidència podries mostrar només amb el teu repositori local.

**Plantilla orientativa per a `repte.md`:**

```markdown
# Repte — Flux de treball del tauler de finances

## 1. Historial i branques
- Branca 1: ___ → fusionada en main mitjançant PR: ___
- Branca 2: ___ → fusionada en main mitjançant PR: ___

## 2. Col·laboració
- PR 1 (enllaç): ___ — què es va revisar: ___
- PR 2 (enllaç): ___ — què es va revisar: ___

## 3. Integració contínua
- Captura o enllaç al resultat d'Actions: ___

## 4. Pla B sense connexió
- Evidència disponible en local si GitHub no estiguera disponible: ___
```

*Variació avaluable*: si dos alumnes treballen en parella sobre el mateix repositori, la Pull Request d'un ha d'estar revisada i comentada per l'altre — la col·laboració real substituïx l'autorevisió simulada de l'exercici 4.

---

<div style="page-break-after: always;"></div>

## Resum de la unitat

**1. Fonaments del control de versions** Git registra l'historial d'un projecte en tres zones (directori de treball, preparació, repositori) mitjançant commits; les branques permeten desenvolupar en paral·lel, i fusionar-les pot generar conflictes que es resolen a mà. L'IDE fa visualment el mateix que les comandes de terminal.

**2. Repositoris remots i treball col·laboratiu** Un repositori remot (GitHub) permet clonar, pujar i descarregar l'historial compartit. En equip, el canvi es proposa mitjançant una Pull Request revisable abans de fusionar-se en `main` — mai es treballa directament sobre la branca principal. Si el remot falla, el treball local no s'interromp.

**3. Integració contínua** Un pipeline de CI (per exemple, GitHub Actions) executa automàticament les proves del projecte en cada `push`, detectant errors abans que arriben més lluny. Encara no inclou el desplegament automàtic. Si el pipeline al núvol falla, un script local equivalent demostra el mateix.

---

## 📚 Per a saber-ne més (opcional, no avaluable)

- Documentació oficial de Git: https://git-scm.com/doc
- GitHub Docs — Pull Requests: https://docs.github.com/es/pull-requests
- GitHub Actions — documentació: https://docs.github.com/es/actions
- *Pro Git* (llibre complet, gratuït): https://git-scm.com/book/es/v2

### 🧭 Per què et servirà açò de veritat

Cap lloc de treball de desenvolupament actual funciona sense control de versions ni sense algun tipus d'integració contínua — és, junt amb el mateix llenguatge de programació, l'eina que usaràs tots els dies de la teua vida professional, en qualsevol empresa i amb qualsevol stack tecnològic.
