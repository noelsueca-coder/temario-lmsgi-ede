<div style="text-align: center;">

<img src="data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCA0MDAgNDAwIiB3aWR0aD0iMTgwIiBoZWlnaHQ9IjE4MCI+CiAgPGNpcmNsZSBjeD0iMjAwIiBjeT0iMjAwIiByPSIxNzAiIGZpbGw9IiNGMEZERkEiLz4KICA8Y2lyY2xlIGN4PSIyMDAiIGN5PSIyMDAiIHI9IjE3MCIgZmlsbD0ibm9uZSIgc3Ryb2tlPSIjOTlGNkU0IiBzdHJva2Utd2lkdGg9IjIiLz4KICA8dGV4dCB4PSIyMDAiIHk9IjI0OCIgZm9udC1mYW1pbHk9IidDb3VyaWVyIE5ldycsIENvdXJpZXIsIG1vbm9zcGFjZSIgZm9udC1zaXplPSIxNTAiIGZvbnQtd2VpZ2h0PSI3MDAiIGZpbGw9IiMwRjc2NkUiIHRleHQtYW5jaG9yPSJtaWRkbGUiPiZndDtfPC90ZXh0Pgo8L3N2Zz4K" width="180" alt="Logo EDE"/>

<h1>Unidad 6</h1>
<h2>Pruebas y depuración</h2>

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

1. Planificación y tipos de pruebas (CA 3a)
2. Casos de prueba y pruebas de código (CA 3b)
3. Pruebas unitarias, automatización y depuración (CA 3c, 3d, 3e, 3f, 3g)
4. Reto de clase
5. Resumen de la unidad
6. Para saber más

<div style="page-break-after: always;"></div>

**RA cubierto:** RA3 (CA 3a-3g) — Verifica el funcionament de programes, dissenyant i realitzant proves.

> 📌 **Nota**: este curso salís de prácticas en empresa el 26/04, así que esta unidad se centra en las CA que se pueden trabajar y demostrar a fondo en el aula con el tiempo disponible. La documentación de incidencias (CA 3h) y los dobles de prueba (CA 3i) — también parte de RA3 — se trabajan y evalúan durante tu formación en la empresa.

> 💻 **Cómo trabajar los ejercicios de esta unidad**: sigue en tu carpeta `UD06_TuNombre` dentro del repositorio del dashboard de finanzas. Usarás `pytest` como herramienta de pruebas — ya tienes el pipeline de CI de UD3 preparado para ejecutarlas automáticamente en cada `push`.

## 🎯 Conceptos clave

Al terminar esta unidad sabrás:
- Planificar y diseñar pruebas de código (funcionales, estructurales, de regresión) identificando casos de prueba, cobertura, valores límite y clases de equivalencia.
- Escribir pruebas unitarias automatizadas y usar el depurador del IDE para localizar el origen de un fallo cuando una prueba no pasa.
- Integrar pruebas y depuración en un mismo flujo de trabajo: escribir una prueba, verla fallar, depurar la causa y comprobar que el pipeline de CI la valida.

---

## 1. Planificación y tipos de pruebas (CA 3a)

### 1.1. Por qué planificar antes de probar "a lo que salga"

Probar código sin plan es ejecutar el programa y mirar si "parece que funciona". Planificar significa decidir, antes de escribir una sola prueba, **qué** se va a comprobar y **cómo se sabrá** que el resultado es correcto.

### 1.2. Tipos de pruebas

> 🗺️ **Mapa visual — tipos de prueba**

| Tipo | Qué comprueba | Ejemplo en el dashboard |
|---|---|---|
| **Funcional** | Que una funcionalidad hace lo que debe, desde fuera (sin mirar el código interno) | Registrar un gasto guarda correctamente el importe y la fecha |
| **Estructural** | Que el código se ejecuta correctamente por dentro (ramas, condiciones) | Que ambas ramas del `if` de categorización automática se ejecutan al menos una vez |
| **De regresión** | Que un cambio nuevo no ha roto algo que antes funcionaba | Al añadir presupuestos (UD4), las pruebas de UD1-UD3 del dashboard siguen pasando |

**🧪 Ejercicio 1 — Clasificar pruebas del dashboard**
En `ejercicio1.md`, describe 3 pruebas distintas que aplicarías al dashboard de finanzas — una funcional, una estructural y una de regresión — indicando qué comprobaría cada una exactamente.

---

## 2. Casos de prueba y pruebas de código (CA 3b)

### 2.1. Procedimientos y casos de prueba

Un **caso de prueba** documenta: qué entrada se usa, qué se hace con ella y qué resultado se espera. Sin esto, "probar" se reduce a ejecutar y mirar a ojo.

| Campo | Ejemplo |
|---|---|
| Entrada | `Transaccion(importe=-45.20, categoria="Alimentación")` |
| Acción | Llamar a `es_gasto()` |
| Resultado esperado | `True` |

### 2.2. Cobertura, valores límite y clases de equivalencia

> 🗺️ **Mapa visual — técnicas de diseño de casos de prueba**

| Técnica | Qué resuelve | Ejemplo en el dashboard |
|---|---|---|
| **Cobertura** | ¿Qué porcentaje del código han ejecutado mis pruebas? | ¿Se ha probado tanto la rama "hay categoría guardada" como "no la hay"? |
| **Valores límite** | Los errores se esconden en los bordes, no en el centro | Probar un presupuesto con gasto = 0, = límite exacto, y = límite+0.01 |
| **Clases de equivalencia** | Agrupar entradas que deberían comportarse igual, para no repetir pruebas redundantes | Todos los importes negativos son "gasto"; no hace falta probar -1, -50 y -1000 por separado |

> 🧾 **No hace falta memorizar de memoria cada nombre técnico**: tendrás la chuleta con las tres técnicas y su propósito. Se evalúa que sepas **aplicarlas** al diseñar un caso de prueba, no que recites su definición exacta.

**🧪 Ejercicio 2 — Casos de prueba con valores límite**
En `ejercicio2.md`, diseña 4 casos de prueba para la función que comprueba si un presupuesto se ha superado, usando al menos un valor límite (justo en el límite) y aplicando clases de equivalencia para no repetir casos redundantes.

---

## 3. Pruebas unitarias, automatización y depuración (CA 3c, 3d, 3e, 3f, 3g)

### 3.1. Pruebas unitarias con pytest (CA 3f)

Una **prueba unitaria** comprueba una única función o método de forma aislada.

```python
# test_transaccion.py
from dashboard import Transaccion

def test_es_gasto_con_importe_negativo():
    t = Transaccion(-45.20, "Alimentación", "2027-01-10")
    assert t.es_gasto() == True

def test_es_gasto_con_importe_positivo():
    t = Transaccion(1500.00, "Nómina", "2027-01-01")
    assert t.es_gasto() == False
```

> 🧾 **No hace falta memorizar la sintaxis de pytest**: tendrás la chuleta con `assert`, cómo nombrar funciones de prueba y cómo ejecutarlas. Se evalúa que la prueba compruebe lo correcto con la lógica correcta, no que recuerdes la sintaxis exacta sin consultarla.

**🧪 Ejercicio 3 — Pruebas unitarias del dashboard**
En `test_dashboard.py`, escribe al menos 4 pruebas unitarias nuevas (usando las técnicas del punto 2) para funciones del dashboard que aún no tengan prueba. Documenta en `ejercicio3.md` el resultado de ejecutarlas.

### 3.2. Herramientas de depuración del entorno y puntos de ruptura (CA 3c, 3d)

El propio IDE no es solo un editor: trae integradas herramientas para probar y depurar sin salir de él — ejecutar pruebas con un clic, ver su resultado en un panel dedicado, y arrancar el **depurador** sobre cualquier línea de código.

Cuando una prueba **falla** y no es evidente por qué, el depurador (`▶️ Debug`, no `▶️ Run`) permite:

- Colocar un **punto de ruptura** (*breakpoint*) en la línea donde algo no cuadra — la ejecución se detiene justo ahí.
- **Avanzar paso a paso** (*step over* / *step into*) para ver exactamente qué hace el programa línea a línea.

| Acción del depurador | Qué hace |
|---|---|
| Breakpoint | Pausa la ejecución en esa línea exacta |
| Step over | Ejecuta la línea actual y pasa a la siguiente, sin entrar en las funciones que llama |
| Step into | Entra dentro de la función que se está llamando, línea a línea |
| Continue | Reanuda la ejecución normal hasta el siguiente breakpoint |

**🧪 Ejercicio 4 — Encontrar un fallo con el depurador**
Se te entregará una función del dashboard con un error sutil (por ejemplo, en el cálculo de un presupuesto) y una prueba que falla al ejecutarla. En `ejercicio4.md`, documenta: dónde colocaste el breakpoint, qué viste al avanzar paso a paso, y en qué línea exacta estaba el error.

### 3.3. Inspeccionar y modificar en tiempo de ejecución (CA 3e)

Con la ejecución pausada en un breakpoint, el panel de **variables** del depurador muestra el valor de cada variable en ese momento exacto — y en muchos IDEs también permite **modificarlo** ahí mismo, sin parar y reescribir código, para comprobar al instante si un valor distinto habría evitado el fallo.

> ⚠️ **Plan B si el depurador del IDE falla o no está disponible**: la depuración por `print()` sigue funcionando siempre, en cualquier entorno, sin ninguna extensión: intercala `print(variable)` en los puntos que quieras inspeccionar. Es menos cómodo que un depurador visual, pero nunca falla — buena idea tenerlo presente también en la VM portátil, donde puede que el depurador gráfico no esté configurado.

### 3.4. Pruebas automáticas (CA 3g)

Ya viste en UD3 cómo un pipeline de CI (GitHub Actions) ejecuta las pruebas automáticamente en cada `push`. Esa es exactamente la forma de convertir las pruebas unitarias de este punto en **pruebas automáticas**: no dependen de que alguien se acuerde de ejecutarlas a mano.

**🧪 Ejercicio 5 — De la prueba al pipeline, pasando por el depurador**
Este ejercicio integra todo el punto 3: (1) escribe una prueba unitaria nueva para una función del dashboard que **todavía tenga un error** (introduce uno tú mismo/a si hace falta); (2) ejecútala y comprueba que falla; (3) usa el depurador (breakpoint + inspección de variables) para localizar la causa exacta; (4) corrige el código; (5) haz `push` y comprueba en la pestaña *Actions* de GitHub que el pipeline de CI ahora pasa en verde. Documenta los 5 pasos en `ejercicio5.md`.

---

## 🎯 Reto de clase

Vas a dejar probada y depurada de extremo a extremo la funcionalidad de **presupuestos por categoría** (UD4-UD5) del dashboard de finanzas personales.

En tu carpeta `UD06`, crea `test_presupuesto.py` y `reto.md` con:

1. **Casos de prueba diseñados** (CA 3b): al menos 4 casos de prueba para la comprobación de presupuesto superado, incluyendo un valor límite.
2. **Pruebas unitarias automáticas** (CA 3f, 3g): implementadas en `test_presupuesto.py` y verificadas en tu pipeline de CI.
3. **Un fallo real depurado** (CA 3c, 3d, 3e): introduce deliberadamente un error pequeño en el código de presupuestos, localízalo con el depurador (breakpoint + inspección de variables) y documenta el proceso paso a paso.

**Plantilla orientativa para `reto.md`:**

```markdown
# Reto — Presupuestos probados y depurados

## 1. Casos de prueba
| Entrada | Acción | Resultado esperado |
|---|---|---|
| ___ | ___ | ___ |

## 2. Pruebas automáticas
- Archivo: test_presupuesto.py
- Resultado en CI: ___

## 3. Depuración de un fallo real
- Breakpoint colocado en: ___
- Qué mostró la inspección de variables: ___
- Línea del error y corrección aplicada: ___
```

*Variación evaluable*: quien lo prefiera puede aplicar este mismo reto a la funcionalidad de exportación (PDF/CSV) en vez de a los presupuestos, siempre que cubra los 3 puntos anteriores.

---

<div style="page-break-after: always;"></div>

## Resumen de la unidad

**1. Planificación y tipos de pruebas** Planificar antes de probar significa decidir qué se comprueba y cómo se sabrá que es correcto; las pruebas pueden ser funcionales, estructurales o de regresión.

**2. Casos de prueba y pruebas de código** Un caso de prueba documenta entrada, acción y resultado esperado; cobertura, valores límite y clases de equivalencia ayudan a diseñar casos de prueba eficaces sin repetir lo redundante.

**3. Pruebas unitarias, automatización y depuración** Las pruebas unitarias comprueban funciones aisladas y se automatizan con el pipeline de CI de UD3; el propio entorno ofrece herramientas de depuración — breakpoints, avance paso a paso e inspección (o modificación) de variables en tiempo de ejecución — con `print()` como alternativa que nunca falla.

**Y lo que continúa en la empresa**: documentar incidencias de forma reproducible (CA 3h) y usar dobles de prueba para aislar componentes (CA 3i) son la continuación natural de lo aprendido aquí — las trabajarás y demostrarás durante tu formación en la empresa.

---

## 📚 Para saber más (opcional, no evaluable)

- Documentación oficial de pytest: https://docs.pytest.org/
- Depuración en VS Code: https://code.visualstudio.com/docs/editor/debugging
- Martin Fowler — *Mocks Aren't Stubs* (dobles de prueba, artículo clásico, útil para cuando lo veas en empresa): https://martinfowler.com/articles/mocksArentStubs.html

### 🧭 Por qué te va a servir esto de verdad

Escribir código que "funciona a la primera" no es realista en ningún proyecto real — lo que marca la diferencia es la rapidez con la que localizas y confirmas que algo está roto, y esta unidad es exactamente el conjunto de herramientas (pruebas, depurador, CI) con el que se hace eso todos los días en cualquier equipo de desarrollo.
