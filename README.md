# Kamus Tontémboan → Bahasa Indonesia

Diccionario y traductor interlineal **Tontémboan (Temboan, ISO `tnt`, Minahasa, Sulawesi Norte) → Bahasa Indonesia**,
generado a partir de los datos del proyecto de traducción bíblica en Paratext.

## Contenido

| Archivo | Qué es |
|---|---|
| `index.html` | Portada con acceso a las dos herramientas |
| `Kamus-Tontemboan-Indonesia.html` | Diccionario: 2.496 lemas principales, 74 términos de glosario, 633 nombres propios. Buscador + filtros por nivel A/B/C |
| `Interlinear-Tontemboan-Indonesia.html` | Interlineal bidireccional (5.124 entradas tnt→id / 3.329 id→tnt): glosa palabra por palabra + traducción aproximada. Funciona offline |

Ambas páginas son autocontenidas (HTML + CSS + JS + datos en un solo archivo, sin dependencias externas).

## Niveles de confianza

- **[A] verificado** — glosas del propio equipo de traducción (`Lexicon.xml` y el glosario del proyecto).
- **[B] conjetura alta** — la forma Tontémboan es el *rendering* oficial del equipo para un lema griego/hebreo
  (`TermRenderings.xml`); la glosa indonesia es el equivalente léxico estándar de ese lema.
- **[C] alineado por corpus** — derivado alineando el AT Tontémboan con la retrotraducción indonesia
  (6.128 versículos paralelos: GEN, JOS, JDG, RUT, 1–2SA, 1–2KI, EST, PSA) con IBM Model 1 (EM) + Dice.

Las entradas A/B confirmadas por el corpus llevan la marca ✓korpus.

## Nota

Es una herramienta de trabajo, no un diccionario normativo. Las entradas [B] y [C] son conjeturas
—de alta confianza, pero conjeturas— y deben verificarse con hablantes nativos.

## Regeneración

Los scripts de build viven en la carpeta del proyecto Paratext (`_kamus_build/`), fuera de este repositorio,
porque leen datos fuente que no se publican:

```
cd _kamus_build
PYTHONUTF8=1 python build_all.py      # diccionario (md, tsv, xlsx, html)
python make_interlinear.py            # interlineal
```

Luego se copian los dos HTML resultantes a este repositorio.

### Publicación automática

El script `_kamus_build\publish.ps1` hace todo lo anterior de una vez —reconstruye, copia,
hace commit y push— y el sitio se actualiza solo:

```powershell
.\publish.ps1                          # build completo + publicar
.\publish.ps1 -Message "arreglo glosa" # mensaje de commit propio
.\publish.ps1 -SkipBuild               # solo copiar y publicar
.\publish.ps1 -NoPush                  # commit sin subir
```

Cierra el `.xlsx` en Excel antes de ejecutarlo, o el build fallará.
