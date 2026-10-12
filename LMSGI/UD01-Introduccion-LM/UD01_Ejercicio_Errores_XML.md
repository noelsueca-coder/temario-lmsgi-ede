# Ejercicio extra — Encuentra los errores del catálogo

**Antes de ver el punto 4.4.** El siguiente documento XML describe un catálogo de videojuegos: tiene su declaración y su instancia. El documento **no está bien formado**: contiene varios errores.

**Repaso rápido de las 6 reglas (punto 4.3):**

| # | Regla | Ejemplo de error |
|---|---|---|
| 1 | Un único elemento raíz | Algo "suelto" fuera de la raíz |
| 2 | Toda etiqueta abierta se cierra | `<titulo>Curso` |
| 3 | El anidamiento no se cruza | `<a><b></a></b>` |
| 4 | Atributos siempre entre comillas | `edad=20` |
| 5 | Mayúsculas y minúsculas distinguen | `<Titulo>...</titulo>` |
| 6 | Elementos vacíos se cierran con `/>` o etiqueta de cierre | `<linea>` sin más |

**Qué tienes que hacer:** En un documento aparte, crea una tabla con 2 columnas y por cada error que encuentres, apunta el nº de línea, qué está mal, y a cuál de las 6 reglas corresponde. Puedes añadir una tercera columna de aclaraciones si lo consideras.

---

```xml
<?xml version="1.0" encoding="UTF-8"?>

<nota>Recuerda actualizar este catálogo cada mes</nota>

<catalogo>

  <juego id="VJ-001" plataforma="PC">
    <titulo>Hollow Knight</titulo>
    <estudio>Team Cherry</estudio>
    <año>2017</año>
    <genero>Metroidvania</genero>
    <estado>Terminado</estado>
  </juego>

  <juego id="VJ-002" plataforma=PC>
    <titulo>Celeste</titulo>
    <estudio>Maddy Makes Games</estudio>
    <año>2018</año>
    <genero>Plataformas</genero>
    <estado>Terminado</estado>
  </juego>

  <juego id="VJ-003" plataforma="PS5">
    <titulo>Hades</titulo>
    <estudio>Supergiant Games</estudio>
    <año>2020</año>
    <genero>Roguelike
    <estado>Terminado</estado>
  </juego>

  <juego id="VJ-004" plataforma="PC">
    <Titulo>Stardew Valley</titulo>
    <estudio>ConcernedApe</estudio>
    <año>2016</año>
    <genero>Simulación</genero>
    <estado>Pausado</estado>
  </juego>

  <juego id="VJ-005" plataforma="PC">
    <titulo>Portal 2</titulo>
    <estudio>Valve</estudio>
    <año>2011</año>
    <genero>Puzle<estado>Terminado</genero></estado>
  </juego>

  <juego id="VJ-006" plataforma="Switch">
    <titulo>Undertale</titulo>
    <estudio>Toby Fox</estudio>
    <año>2015</año>
    <genero>RPG</genero>
    <estado>Terminado</estado>
  </juego>

  <juego id="VJ-007" plataforma="PC">
    <titulo>Outer Wilds</titulo>
    <estudio>Mobius Digital</estudio>
    <año>2019</año>
    <genero>Exploración</genero>
    <estado>Terminado</estado>
    <favorito>
  </juego>

  <juego id=VJ-008 plataforma="PC">
    <titulo>Disco Elysium</titulo>
    <estudio>ZA/UM</estudio>
    <año>2019</año>
    <genero>RPG narrativo</genero>
    <estado>En curso</estado>
  </juego>

  <juego id="VJ-009" plataforma="PC">
    <titulo>Return of the Obra Dinn</titulo>
    <estudio>Lucas Pope
    <año>2018</año>
    <genero>Misterio</genero>
    <estado>Terminado</estado>
  </juego>

  <juego id="VJ-010" plataforma="Switch">
    <titulo>Inside</titulo>
    <estudio>Playdead</estudio>
    <año>2016</año>
    <genero>Plataformas</genero>
    <ESTADO>Terminado</estado>
  </juego>

  <juego id="VJ-011" plataforma="PC">
    <titulo>Katana Zero<estudio></titulo>Devolver Digital</estudio>
    <año>2019</año>
    <genero>Acción</genero>
    <estado>Terminado</estado>
  </juego>

  <juego id="VJ-012" plataforma="Xbox">
    <titulo>Cuphead</titulo>
    <estudio>Studio MDHR</estudio>
    <año>2017</año>
    <genero>Plataformas</genero>
    <estado>Pausado</estado>
    <favorito>
  </juego>

  <juego id="VJ-013" plataforma=Switch>
    <titulo>Hyper Light Drifter</titulo>
    <estudio>Heart Machine</estudio>
    <año>2016</año>
    <genero>Acción</genero>
    <estado>Terminado</estado>
  </juego>

  <juego id="VJ-014" plataforma="PC">
    <titulo>Firewatch</titulo>
    <estudio>Campo Santo</estudio>
    <año>2016</año>
    <genero>Aventura</genero>
    <estado>Terminado</estado>
  </juego>

  <juego id="VJ-015" plataforma="PC">
    <titulo>Dead Cells</titulo>
    <estudio>Motion Twin</estudio>
    <año>2018
    <genero>Roguelike</genero>
    <estado>En curso</estado>
  </juego>

  <juego id="VJ-016" plataforma="PC">
    <titulo>Her Story</titulo>
    <Estudio>Sam Barlow</estudio>
    <año>2015</año>
    <genero>Misterio</genero>
    <estado>Terminado</estado>
  </juego>

  <juego id="VJ-017" plataforma="PC">
    <titulo>Baba Is You</titulo>
    <estudio>Hempuli</estudio>
    <año>2019<genero></año>Puzle</genero>
    <estado>Terminado</estado>
  </juego>

  <juego id="VJ-018" plataforma="PC">
    <titulo>Subnautica</titulo>
    <estudio>Unknown Worlds</estudio>
    <año>2018</año>
    <genero>Supervivencia</genero>
    <estado>Pausado</estado>
    <favorito>
  </juego>

  <juego id=VJ-019 plataforma="PC">
    <titulo>Papers, Please</titulo>
    <estudio>3909 LLC</estudio>
    <año>2013</año>
    <genero>Simulación</genero>
    <estado>Terminado</estado>
  </juego>

  <juego id="VJ-020" plataforma="PC">
    <titulo>Gris
    <estudio>Nomada Studio</estudio>
    <año>2018</año>
    <genero>Plataformas</genero>
    <estado>Terminado</estado>
  </juego>

  <juego id="VJ-021" plataforma="PC">
    <titulo>Inscryption</titulo>
    <estudio>Daniel Mullins Games</estudio>
    <año>2021</año>
    <GENERO>Cartas / Terror</genero>
    <estado>En curso</estado>
  </juego>

  <juego id="VJ-022" plataforma=PS4>
    <titulo>What Remains of Edith Finch</titulo>
    <estudio>Giant Sparrow</estudio>
    <año>2017</año>
    <genero>Narrativo</genero>
    <estado>Terminado</estado>
  </juego>

  <juego id="VJ-023" plataforma="PC">
    <titulo>Slay the Spire</titulo>
    <estudio>Mega Crit</estudio>
    <año>2019</año>
    <genero>Roguelike / Cartas</genero>
    <estado>En curso</estado>
    <favorito>
  </juego>

  <juego id="VJ-024" plataforma="PC">
    <titulo>Oxenfree</titulo>
    <estudio>Night School Studio</estudio>
    <año>2016</año>
    <genero>Aventura</genero>
    <estado>Terminado</estado>
  </juego>

</catalogo>

<juego id="VJ-025" plataforma="PC">
  <titulo>Spelunky 2</titulo>
  <estudio>Mossmouth</estudio>
  <año>2020</año>
  <genero>Roguelike</genero>
  <estado>Terminado</estado>
</juego>
```
