# Modelado de Distribución de Especies en R

**Autora:** Dra. Viridiana Lizardo  
**Nivel:** Intermedio (requiere R básico y familiaridad con datos ecológicos)  
**Especie de ejemplo:** *Didelphis virginiana* (tlacuache norteño)

---

## ¿De qué trata este curso?

Tutorial paso a paso para construir un modelo de distribución de especies (SDM) con R, desde la descarga de datos hasta la generación de mapas de idoneidad con MaxEnt. Todo el código es reproducible y está diseñado para que puedas adaptarlo a la especie de tu interés.

---

## Contenido

| Paso | Tema | Descripción |
|------|------|-------------|
| 00 | Introducción | Presentación conceptual del flujo de trabajo (PowerPoint) |
| 01 | Datos de presencia | Descarga desde GBIF, limpieza con `CoordinateCleaner`, separación training/testing |
| 02 | Variables climáticas | Descarga de WorldClim, selección por multicolinearidad, recorte al área de entrenamiento |
| 03 | Modelado | Ajuste y evaluación de MaxEnt con `SDMTune` |

---

## Requisitos

### Software
- R ≥ 4.1
- RStudio (recomendado para los notebooks)

### Paquetes de R

```r
install.packages(c(
  "tidyverse",
  "sf",
  "terra",
  "tmap",
  "tmaptools",
  "rgbif",
  "CoordinateCleaner",
  "SDMtune"
))
```

### Credenciales de GBIF

El Paso 01 requiere una cuenta gratuita en [GBIF](https://www.gbif.org/). Una vez registrada, guarda tus credenciales en `.Renviron`:

```r
usethis::edit_r_environ()

# Agrega estas líneas:
GBIF_USER = "tu_usuario"
GBIF_PWD  = "tu_contraseña"
GBIF_EMAIL = "tu_correo@ejemplo.com"
```

---

## Estructura del repositorio

```
.
├── README.md
├── paso01.Rmd          # Notebook: datos de presencia
├── paso02.Rmd          # Notebook: variables climáticas
├── paso03.Rmd          # Notebook: modelado con MaxEnt
├── docs/             # Versiones en presentación de cada paso
│   ├── introduccion.pdf
│   ├── paso01_slides.Rmd
│   └── ...
├── data/               # Generada al correr los scripts
│   ├── training.csv
│   └── testing.csv
├── layers/             # Capas climáticas recortadas (generadas)
└── images/             # Imágenes usadas en los notebooks
```

> **Nota:** Las carpetas `data/` y `layers/` se generan al ejecutar los notebooks. Están incluidas en el repositorio en caso de que haya problemas de hardware o internet.

---

## Cómo usar este curso

1. Clona o descarga el repositorio.
2. Abre el proyecto `.Rproj` en RStudio.
3. Abre los archivos `.Rmd` en RStudio en orden (paso01 → paso02 → paso03).
4. Ejecuta los chunks secuencialmente. Cada notebook genera los archivos que necesita el siguiente.
5. Puedes cambiar la especie objetivo modificando el nombre científico en el Paso 01; el resto del flujo es compatible con cualquier especie en GBIF.

---

## Créditos y cita

Si usas este material para un curso o publicación, por favor cita este repositorio:

> Lizardo, V. (*año*). *Modelado de Distribución de Especies en R*. GitHub. [URL del repositorio]

---

## Licencia

[MIT](LICENSE) — libre para usar, modificar y redistribuir con atribución.
