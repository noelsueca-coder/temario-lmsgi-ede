<div style="text-align: center;">

<img src="data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCA0MDAgNDAwIiB3aWR0aD0iMTgwIiBoZWlnaHQ9IjE4MCI+CiAgPGNpcmNsZSBjeD0iMjAwIiBjeT0iMjAwIiByPSIxNzAiIGZpbGw9IiNGMEZERkEiLz4KICA8Y2lyY2xlIGN4PSIyMDAiIGN5PSIyMDAiIHI9IjE3MCIgZmlsbD0ibm9uZSIgc3Ryb2tlPSIjOTlGNkU0IiBzdHJva2Utd2lkdGg9IjIiLz4KICA8dGV4dCB4PSIyMDAiIHk9IjI0OCIgZm9udC1mYW1pbHk9IidDb3VyaWVyIE5ldycsIENvdXJpZXIsIG1vbm9zcGFjZSIgZm9udC1zaXplPSIxNTAiIGZvbnQtd2VpZ2h0PSI3MDAiIGZpbGw9IiMwRjc2NkUiIHRleHQtYW5jaG9yPSJtaWRkbGUiPiZndDtfPC90ZXh0Pgo8L3N2Zz4K" width="180" alt="Logo EDE"/>

<h1>Unidad 3</h1>
<h2>Control de versiones</h2>

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

1. Fundamentos del control de versiones (CA 4f)
2. Repositorios remotos y trabajo colaborativo (CA 4h)
3. Integración continua (CA 4i)
4. Reto de clase
5. Resumen de la unidad
6. Para saber más

<div style="page-break-after: always;"></div>

**RA cubierto:** RA4 (CA 4f, 4h, 4i) — Optimitza codi usant les eines disponibles en l'entorn de desenvolupament (control de versions, repositoris remots i integració contínua).

> 💡 **Nota de estudio**: esta unidad no cubre todo RA4 — solo las letras 4f, 4h y 4i. El resto de letras de RA4 (refactorización, análisis de código, documentación de clases...) pertenecen a otra unidad de programación que se trabaja íntegramente en empresa. Aquí nos centramos solo en control de versiones, repositorios remotos e integración continua.

> 💻 **Cómo trabajar los ejercicios de esta unidad**: sigue usando tu carpeta `UD03_TuNombre`, pero esta vez conviértela en un repositorio Git real desde el primer ejercicio. Vas a seguir trabajando sobre el proyecto del **dashboard de finanzas personales** que arrancaste en UD1 y configuraste en UD2 — a partir de ahora, cada cambio que hagas sobre él queda registrado con control de versiones.

## 🎯 Conceptos clave

Al terminar esta unidad sabrás:
- Usar Git para registrar el historial de un proyecto: commits, ramas y fusiones, incluida la resolución de conflictos.
- Trabajar con un repositorio remoto (GitHub) de forma colaborativa: clonar, sincronizar cambios y revisar código mediante Pull Requests.
- Configurar un pipeline básico de integración continua que ejecute pruebas automáticamente cada vez que se sube código.

---

## 1. Fundamentos del control de versiones (CA 4f)

### 1.1. Qué problema resuelve

> 📜 **Historia útil, ya no se usa así**: antes de Git (2005), lo habitual eran sistemas de control de versiones **centralizados** (CVS, Subversion/SVN): un único servidor guardaba el historial, y sin conexión a él no podías ni consultar versiones antiguas. Git es **distribuido**: cada copia del repositorio contiene el historial completo. Esto sigue siendo la razón técnica por la que Git funciona sin conexión y por la que GitHub es "solo" uno de los muchos sitios donde alojar una copia remota, no el único lugar donde existe el historial.

Sin control de versiones, "guardar versiones" de un proyecto se convierte en esto:

```
dashboard_final.py
dashboard_final_v2.py
dashboard_final_v2_BUENO.py
dashboard_final_v2_BUENO_de_verdad.py
```

Con Git, existe un único archivo, y su historial completo de cambios vive en una carpeta oculta (`.git`) dentro del propio proyecto.

### 1.2. Estructura de Git: las tres zonas

| Zona | Qué contiene | Comando típico para pasar a la siguiente |
|---|---|---|
| **Directorio de trabajo** | Los archivos tal cual los ves y editas | `git add` |
| **Área de preparación (staging / índice)** | Los cambios marcados para el próximo commit | `git commit` |
| **Repositorio (`.git`)** | El historial de commits ya guardado | `git push` (hacia un remoto) |

Cada **commit** es una fotografía del proyecto en un momento dado, con un mensaje que explica qué cambió y por qué. `HEAD` es un puntero que indica "dónde estás ahora" dentro de ese historial.

### 1.3. Ramas y fusión (branches y merge)

Una **rama** (*branch*) es una línea de desarrollo independiente. `main` (o `master`) suele ser la rama principal; se crean ramas nuevas para probar cosas sin tocar el código que ya funciona.

```
main:     A---B---C-------F
                    \     /
feature:             D---E
```

Al terminar el trabajo en una rama, se **fusiona** (*merge*) de vuelta. Si ambas ramas cambiaron las mismas líneas del mismo archivo, Git no puede decidir por ti: aparece un **conflicto de fusión**, que se resuelve a mano eligiendo (o combinando) qué versión se queda.

> 🗺️ **Mapa visual — de un cambio a un commit fusionado**

| Paso | Zona | Comando |
|---|---|---|
| 1. Editas un archivo | Directorio de trabajo | — |
| 2. Marcas el cambio | Área de preparación | `git add archivo` |
| 3. Confirmas el cambio | Repositorio local | `git commit -m "mensaje"` |
| 4. Guardas el trabajo en una línea aparte | Rama nueva | `git branch`, `git checkout` (o `git switch`) |
| 5. Incorporas esa línea a `main` | Fusión | `git merge nombre-rama` |

### 1.4. Git integrado en el IDE

Desde UD1 usas VS Codium; su panel **Control de código fuente** (icono de rama en la barra lateral) hace visualmente lo mismo que los comandos de arriba: archivos modificados en naranja, botón "+" para pasarlos a preparación, campo de texto y ✓ para el commit, y un historial gráfico de ramas con extensiones como *GitLens*.

> 🧾 **No hace falta memorizar los comandos de memoria**: tendrás una chuleta con los comandos de Git vistos en esta unidad (`add`, `commit`, `branch`, `checkout`/`switch`, `merge`, `clone`, `push`, `pull`, `fetch`). Lo que se evalúa es que sepas **cuándo** usar cada uno — en el IDE o por terminal, el flujo de fondo es el mismo.

**🧪 Ejercicio 1 — Primer repositorio del dashboard**
En tu carpeta del dashboard de finanzas (UD1-UD2), ejecuta `git init`. Haz al menos 3 commits con mensajes descriptivos (por ejemplo: añadir estructura inicial, añadir función de cálculo de saldo, añadir validación de datos). Documenta en `ejercicio1.md` el resultado de `git log --oneline`.

**🧪 Ejercicio 2 — Rama, cambio y fusión con conflicto**
Crea una rama `feature-categorias`. En ella, modifica la misma línea de un archivo que también vas a modificar (de forma distinta) en `main`. Fusiona `feature-categorias` en `main` y resuelve el conflicto que aparecerá. En `ejercicio2.md`, pega el fragmento de conflicto tal cual lo mostró Git (con las marcas `<<<<<<<`, `=======`, `>>>>>>>`) y explica en dos líneas qué elegiste y por qué.

---

## 2. Repositorios remotos y trabajo colaborativo (CA 4h)

### 2.1. Repositorios remotos

Un repositorio local vive solo en tu equipo. Un **repositorio remoto** (GitHub, GitLab...) es una copia alojada en un servidor que permite compartirlo, respaldarlo y trabajar en equipo.

| Operación | Sentido | Comando |
|---|---|---|
| **Clonar** | Remoto → nueva copia local completa | `git clone url` |
| **Subir** | Local → remoto | `git push` |
| **Descargar y fusionar** | Remoto → local | `git pull` |
| **Descargar sin fusionar** | Remoto → local (solo consultar) | `git fetch` |

**🧪 Ejercicio 3 — Del repositorio local a GitHub**
Crea un repositorio vacío en GitHub y conecta tu repositorio local del dashboard como remoto (`git remote add origin ...`). Sube tu historial (`git push`). Clona el repositorio en otra carpeta distinta de tu equipo para comprobar que el historial completo llega intacto. Captura en `ejercicio3.md` la URL del repositorio.

### 2.2. Flujos de trabajo colaborativos

En equipo no se trabaja directamente sobre `main`: el flujo habitual es

1. Cada persona crea su propia rama para la funcionalidad en la que trabaja (`feature/nombre-funcionalidad`).
2. Sube su rama al remoto (`git push origin feature/...`).
3. Abre una **Pull Request** (PR): una propuesta de fusión de esa rama hacia `main`, visible y comentable por el resto del equipo.
4. Alguien más **revisa el código** (*code review*): comenta, pide cambios o aprueba.
5. Solo entonces se fusiona la PR en `main`.

> 📡 **Por qué importa hoy**: es exactamente así como vas a incorporar más adelante (UD4-UD6) los diagramas y las pruebas del dashboard de finanzas — cada mejora entra en `main` a través de una Pull Request revisada, nunca directamente.

**🧪 Ejercicio 4 — Simular un flujo de Pull Request**
Crea una rama `feature-informe-mensual` con un cambio pequeño y funcional sobre el dashboard. Súbela y abre una Pull Request en GitHub (si trabajas en pareja, pide a tu compañero/a que la revise y comente; si trabajas solo/a, deja al menos un comentario de autorrevisión señalando algo a mejorar). Fusiona la PR desde la propia interfaz de GitHub. En `ejercicio4.md`, enlaza la PR ya cerrada.

### 2.3. Plan B: cuando el remoto falla

GitHub puede estar caído, el aula puede quedarse sin red, o tu cuenta puede tener un problema puntual de permisos. Ninguna de esas situaciones te impide seguir trabajando:

- Sigue haciendo `commit` en local con normalidad — el historial no depende de la red.
- En cuanto vuelva la conexión, un único `git push` sincroniza todo lo acumulado.
- Si vas a trabajar fuera del aula sin garantía de red (por ejemplo, en la VM portátil), configura Git una sola vez (`git config --global user.name/email`) y ya tienes control de versiones disponible sin depender de GitHub en ningún momento.

---

## 3. Integración continua (CA 4i)

### 3.1. Qué es y qué resuelve

La **integración continua (CI)** ejecuta automáticamente, en un servidor y no en tu equipo, tareas como instalar dependencias y correr las pruebas del proyecto cada vez que subes código. El objetivo: detectar cuanto antes si un cambio ha roto algo, sin depender de que alguien se acuerde de ejecutar las pruebas a mano.

> ⚠️ **Qué NO es esta unidad**: CI no incluye todavía el **despliegue** automático de la aplicación (eso es *Continuous Deployment*, CD) — aquí solo automatizamos la verificación del código, no su publicación.

### 3.2. Un pipeline básico con GitHub Actions

GitHub Actions define el pipeline en un archivo YAML dentro de `.github/workflows/`:

```yaml
name: Tests del dashboard
on: [push]
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: Instalar dependencias
        run: pip install -r requirements.txt
      - name: Ejecutar pruebas
        run: pytest
```

Cada `push` a GitHub dispara este flujo automáticamente; el resultado (✅ o ❌) aparece junto al commit y en cualquier Pull Request abierta.

> 🧾 **No hace falta memorizar la sintaxis YAML**: tendrás disponible esta plantilla como chuleta. Lo que se evalúa es que entiendas qué hace cada bloque (`on`, `jobs`, `steps`) y en qué momento del flujo de trabajo se dispara, no que la escribas de memoria desde cero.

### 3.3. Plan B: cuando el pipeline en la nube falla

GitHub Actions tiene cuotas de uso gratuitas que se pueden agotar, y a veces un workflow queda mal configurado o no se ejecuta. Antes de depender de él en clase, ten siempre a mano un script equivalente que puedas ejecutar tú mismo en local:

```bash
#!/bin/bash
# run-tests.sh — mismo contenido que el job de CI, ejecutado a mano
pip install -r requirements.txt
pytest
```

Así, si el pipeline en la nube falla, `./run-tests.sh` demuestra exactamente lo mismo sin depender de ningún servicio externo. Ten este script preparado también en tu VM portátil.

**🧪 Ejercicio 5 — Pipeline de CI para el dashboard**
Añade el archivo `.github/workflows/tests.yml` (con el contenido del punto 3.2, adaptado a tu proyecto) al repositorio del dashboard. Haz un commit y comprueba en la pestaña *Actions* de GitHub que se ejecuta. Si no tienes pruebas automáticas todavía, añade al menos una función sencilla con una prueba mínima (`assert`) para que el pipeline tenga algo real que ejecutar. Documenta en `ejercicio5.md` una captura del resultado (✅ o ❌) y, si algo falló, cómo lo solucionaste.

---

## 🎯 Reto de clase

Vas a dejar el repositorio del **dashboard de finanzas personales** organizado con un flujo de trabajo colaborativo completo y funcionando de extremo a extremo.

En el repositorio ya creado en el Ejercicio 3, crea `reto.md` con:

1. **Historial limpio** (CA 4f): al menos 2 ramas de funcionalidad distintas, cada una fusionada en `main` mediante su propia Pull Request (puedes reutilizar las de los ejercicios 2 y 4 si ya cumplen esto, o crear nuevas).
2. **Colaboración documentada** (CA 4h): enlaza las Pull Requests fusionadas y explica en 3-4 líneas qué revisó (o qué se habría revisado) en cada una antes de fusionarla.
3. **CI funcionando** (CA 4i): captura de la pestaña *Actions* mostrando que el pipeline se ejecutó correctamente sobre la última fusión.
4. **Plan B aplicado**: describe brevemente qué harías si, el día de la entrega, GitHub estuviera caído — qué evidencia podrías mostrar solo con tu repositorio local.

**Plantilla orientativa para `reto.md`:**

```markdown
# Reto — Flujo de trabajo del dashboard de finanzas

## 1. Historial y ramas
- Rama 1: ___ → fusionada en main mediante PR: ___
- Rama 2: ___ → fusionada en main mediante PR: ___

## 2. Colaboración
- PR 1 (enlace): ___ — qué se revisó: ___
- PR 2 (enlace): ___ — qué se revisó: ___

## 3. Integración continua
- Captura o enlace al resultado de Actions: ___

## 4. Plan B sin conexión
- Evidencia disponible en local si GitHub no estuviera disponible: ___
```

*Variación evaluable*: si dos alumnos trabajan en pareja sobre el mismo repositorio, la Pull Request de uno debe estar revisada y comentada por el otro — la colaboración real sustituye a la autorrevisión simulada del ejercicio 4.

---

<div style="page-break-after: always;"></div>

## Resumen de la unidad

**1. Fundamentos del control de versiones** Git registra el historial de un proyecto en tres zonas (directorio de trabajo, preparación, repositorio) mediante commits; las ramas permiten desarrollar en paralelo, y fusionarlas puede generar conflictos que se resuelven a mano. El IDE hace lo mismo visualmente que los comandos de terminal.

**2. Repositorios remotos y trabajo colaborativo** Un repositorio remoto (GitHub) permite clonar, subir y descargar el historial compartido. En equipo, el cambio se propone mediante una Pull Request revisable antes de fusionarse en `main` — nunca se trabaja directamente sobre la rama principal. Si el remoto falla, el trabajo local no se interrumpe.

**3. Integración continua** Un pipeline de CI (por ejemplo, GitHub Actions) ejecuta automáticamente las pruebas del proyecto en cada `push`, detectando errores antes de que lleguen más lejos. No incluye todavía el despliegue automático. Si el pipeline en la nube falla, un script local equivalente demuestra lo mismo.

---

## 📚 Para saber más (opcional, no evaluable)

- Documentación oficial de Git: https://git-scm.com/doc
- GitHub Docs — Pull Requests: https://docs.github.com/es/pull-requests
- GitHub Actions — documentación: https://docs.github.com/es/actions
- *Pro Git* (libro completo, gratuito): https://git-scm.com/book/es/v2

### 🧭 Por qué te va a servir esto de verdad

Ningún puesto de desarrollo actual funciona sin control de versiones ni sin algún tipo de integración continua — es, junto con el propio lenguaje de programación, la herramienta que vas a usar todos los días de tu vida profesional, en cualquier empresa y con cualquier stack tecnológico.
