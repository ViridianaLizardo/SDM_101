# Modelado de Distribución de Especies en R

**Autora:** Dra. Viridiana Lizardo  
**Nivel:** Intermedio (requiere R básico y familiaridad con datos ecológicos)  
**Especie de ejemplo:** *Didelphis virginiana* (tlacuache norteño)

---

## ¿De qué trata este curso?

Tutorial paso a paso para construir un modelo de distribución de especies (SDM) con R, desde la descarga de datos hasta la generación de mapas de idoneidad con MaxEnt. Todo el código es reproducible y está diseñado para que puedas adaptarlo a la especie de tu interés.

---



## Contenido

| Paso | Tema | Notebook | Slides |
|------|------|----------|--------|
| Intro | Conceptos y flujo de trabajo | — | [Clase Nichos agosto 2024.pptx](Clase%20Nichos%20agosto%202024.pptx) |
| 01 | Descarga, limpieza y preparación de datos de presencia | [paso01.Rmd](paso01.Rmd) | [slides paso 01](docs/slides-paso-01.html) |
| 02 | Selección de variables climáticas y recorte de capas | [paso02.Rmd](paso02.Rmd) | — *(próximamente)* |
| 03 | Modelado con MaxEnt usando SDMTune | [paso03.Rmd](paso03.Rmd) | [slides paso 03](docs/slides-paso-03.html) |

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

El Paso 01 descarga datos directamente desde [GBIF](https://www.gbif.org/), lo que requiere una cuenta gratuita. Una vez registrada, guarda tus credenciales en `.Renviron` para no escribirlas en el script:

```r
usethis::edit_r_environ()

# Agrega estas líneas y guarda el archivo:
GBIF_USER  = "tu_usuario"
GBIF_PWD   = "tu_contraseña"
GBIF_EMAIL = "tu_correo@ejemplo.com"
```

Si no puedes conectarte a GBIF en el momento, la carpeta `data/` incluye un archivo de descarga de ejemplo (`0044111-260519110011954.zip`) con los registros de *D. virginiana* para que puedas seguir el tutorial sin conexión.

---

## Estructura del repositorio

```
SDM_101/
├── README.md
├── SDM_crash_course.Rproj
├── paso01.Rmd                        # Notebook: datos de presencia
├── paso02.Rmd                        # Notebook: variables climáticas
├── paso03.Rmd                        # Notebook: modelado con MaxEnt
├── slides_paso01.Rmd                 # Slides ioslides: paso 01
├── slides_paso03.Rmd                 # Slides ioslides: paso 03
├── scrollable_slides.css             # CSS para slides
├── citations.txt                     # Referencias bibliográficas
├── 0044111-260519110011954.zip   # Descarga GBIF de ejemplo
├── data/
│   ├── training.csv                  # Generado en paso01
│   └── testing.csv                   # Generado en paso01
├── images/
│   └── (imágenes usadas en los notebooks)
└── docs/                             # HTMLs renderizados — GitHub Pages
    ├── index.html                    # Página de bienvenida
    ├── intro.pdf                     # clase de introducción
    ├── intro.pptx
    ├── paso01.nb.html
    ├── paso02.nb.html
    ├── paso03.nb.html
    ├── slides-paso-01.html
    └── slides-paso-03.html

```

> **Nota:** Las carpetas `data/` y `layers/` se generan al ejecutar los notebooks. 
Están incluidas en el repositorio en caso de que haya problemas de hardware o internet. 
Las capas climáticas recortadas se generan al ejecutar el Paso 02, pero igual se incluyen.

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
