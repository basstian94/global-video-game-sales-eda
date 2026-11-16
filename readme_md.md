# Análisis Exploratorio de Datos: Mercado Global de Videojuegos (Hasta 2016)
# Exploratory Data Analysis: Global Video Game Market (Up to 2016)

---

## Descripción del Proyecto / Project Overview

Este proyecto presenta un Análisis Exploratorio de Datos (EDA) y pruebas de hipótesis estadísticas sobre el mercado global de videojuegos con registros históricos hasta 2016. El objetivo principal consiste en identificar patrones de rendimiento comercial, diferencias culturales por región, correlación con reseñas especializadas y dinámicas de transición generacional de hardware para fundamentar decisiones estratégicas de desarrollo y distribución.

This project presents an Exploratory Data Analysis (EDA) and statistical hypothesis testing on the global video game market using historical records up to 2016. The primary objective is to identify commercial performance patterns, regional cultural differences, correlations with specialized reviews, and hardware generational transition dynamics to support strategic development and distribution decisions.

---

## Estructura del Repositorio / Repository Structure

Para garantizar la correcta ejecución del código y la lectura de archivos tanto en entornos Windows como macOS sin necesidad de modificar rutas manualmente, el repositorio mantiene la siguiente jerarquía estricta:

To ensure proper code execution and file reading across both Windows and macOS environments without manual path modifications, the repository enforces the following strict directory hierarchy:

```text
proyecto-videojuegos-eda/
│
├── data/
│   └── games.csv               # Conjunto de datos principal / Main dataset
│
├── notebooks/
│   └── analisis_ventas.ipynb   # Notebook de Jupyter con el análisis / Jupyter Notebook with full analysis
│
├── .gitignore                  # Exclusiones de control de versiones / Version control exclusions
├── requirements.txt            # Dependencias y librerías / Dependencies and libraries
└── README.md                   # Documentación del proyecto / Project documentation
```

---

## Convenciones de Rutas y Compatibilidad (Windows / macOS)
## Path Conventions & Cross-Platform Compatibility (Windows / macOS)

Para evitar errores de tipo `FileNotFoundError` al clonar o ejecutar el proyecto en distintos sistemas operativos, se deben respetar las siguientes normas técnicas:

To prevent `FileNotFoundError` exceptions when cloning or executing the project across different operating systems, the following technical guidelines must be observed:

1. **Ubicación relativa obligatoria / Mandatory relative location:** El archivo de datos (`games.csv`) debe permanecer dentro de la carpeta `data/`, y el archivo de código (`.ipynb`) dentro de la carpeta `notebooks/`. No se deben mover los archivos a la raíz ni renombrar los directorios. / The data file (`games.csv`) must remain inside the `data/` directory, and the code file (`.ipynb`) inside the `notebooks/` directory. Do not move files to the root directory or rename folders.
2. **Directorio de trabajo / Working directory:** Al abrir el notebook desde Jupyter Lab, Jupyter Notebook o VS Code, el directorio de trabajo activo debe ser la carpeta `notebooks/`. / When opening the notebook via Jupyter Lab, Jupyter Notebook, or VS Code, the active working directory must be the `notebooks/` folder.
3. **Lectura agnóstica al sistema operativo / OS-agnostic file reading:** En el código del notebook, la carga de datos utiliza rutas relativas estándar con barra inclinada (`/`) o el módulo `pathlib` (`../data/games.csv`), lo cual es interpretado de forma nativa tanto por Windows (`\`) como por macOS/Linux (`/`). Nunca utilice rutas absolutas locales (ej. `C:\Users\...` o `/Users/...`). / Within the notebook code, data ingestion uses standard forward-slash relative paths (`/`) or the `pathlib` module (`../data/games.csv`), which is natively resolved by both Windows (`\`) and macOS/Linux (`/`). Never use local absolute paths (e.g., `C:\Users\...` or `/Users/...`).

---

## Hallazgos Principales / Key Findings

### 1. Dinámica de Plataformas y Transición Generacional / Platform Dynamics & Generational Turnover
* **Asimetría estadística y tendencia central:** La distribución de ventas exhibe un marcado sesgo positivo impulsado por títulos de éxito masivo (*outliers*). Esto invalida a la media aritmética como indicador representativo y establece a la **mediana** como la métrica adecuada para evaluar el rendimiento central (~$250,000 USD en las 4 plataformas líderes). / Sales distribution exhibits a pronounced right-skew driven by blockbuster titles (outliers). This invalidates the arithmetic mean as a representative indicator and establishes the **median** as the appropriate metric to evaluate central performance (~$250,000 USD across the top 4 platforms).
* **Canibalización generacional:** Las franquicias principales migran rápidamente hacia las consolas de última generación (**PS4** y **Xbox One**), reduciendo de forma abrupta el volumen de ventas de las plataformas predecesoras. / Flagship franchises rapidly migrate toward current-generation consoles (**PS4** and **Xbox One**), sharply reducing sales volumes on predecessor platforms.

### 2. Diferencias Culturales por Región / Regional Cultural Differences
* **Mercados occidentales (Norteamérica y Europa):** Predominio de consolas de sobremesa y liderazgo de los géneros de **Acción**, ***Shooters*** y **Deportes**, respaldados por ecosistemas multijugador en línea y clasificaciones ESRB **M (Mature)** y **E (Everyone)**. / Dominance of home consoles and leadership of **Action**, **Shooters**, and **Sports** genres, supported by online multiplayer ecosystems and ESRB **M (Mature)** and **E (Everyone)** ratings.
* **Mercado japonés:** Comportamiento diferenciado caracterizado por la alta adopción de consolas portátiles (**Nintendo 3DS**, **PS Vita**), liderazgo absoluto del género **Role-Playing (RPG)** y preferencia por fabricantes locales, lo que explica la baja penetración de plataformas como Xbox. / Distinct market behavior characterized by high adoption of handheld consoles (**Nintendo 3DS**, **PS Vita**), undisputed leadership of the **Role-Playing (RPG)** genre, and preference for domestic manufacturers, explaining the minimal penetration of platforms such as Xbox.

### 3. Correlación entre Calificaciones y Ventas / Correlation Between Scores & Sales
* **Análisis en PS4:** Se observa una correlación positiva moderada entre la puntuación de la crítica especializada y las ventas ($r = 0.4019$), mientras que la correlación entre la puntuación de los usuarios y las ventas es prácticamente nula ($r = -0.0431$). Entre ambas métricas de evaluación existe una concordancia moderada-alta ($r = 0.5464$). / A moderate positive correlation is observed between critic scores and unit sales ($r = 0.4019$), whereas the correlation between user scores and sales is virtually zero ($r = -0.0431$). Both rating metrics share a moderate-to-strong positive correlation ($r = 0.5464$).

### 4. Pruebas de Hipótesis Estadísticas ($\alpha = 0.05$) / Statistical Hypothesis Testing ($\alpha = 0.05$)
* **Xbox One vs. PC (Calificaciones de usuarios):** Mediante una prueba *t de Student* bilateral para muestras independientes, **no se rechaza** $H_0$ ($p > 0.05$). No existe evidencia estadística de diferencia entre las calificaciones promedio de ambas plataformas. / Using a two-tailed independent samples *t-test*, we **fail to reject** $H_0$ ($p > 0.05$). There is no statistical evidence of a difference between the average user ratings of both platforms.
* **Acción vs. Deportes (Calificaciones de usuarios):** Se **rechaza** $H_0$ ($p < 0.05$), confirmando que las valoraciones promedio de los usuarios presentan diferencias estadísticamente significativas entre ambos géneros. / We **reject** $H_0$ ($p < 0.05$), confirming that average user ratings exhibit statistically significant differences between both genres.

---

## Recomendaciones Estratégicas / Strategic Recommendations

1. **Asignación de recursos de desarrollo:** Priorizar el desarrollo y lanzamiento en las consolas de última generación dentro de la ventana temporal analizada (**PS4** y **Xbox One**), donde se concentra la mayor tracción comercial. / Prioritize development and release efforts on current-generation consoles within the analyzed timeframe (**PS4** and **Xbox One**), where commercial traction is concentrated.
2. **Estrategia de distribución regional:** Adaptar el catálogo según el perfil cultural del mercado objetivo (Acción/*Shooters* en Occidente; RPGs y formatos portátiles en Japón), evitando inversiones de distribución desproporcionadas para ecosistemas sin arraigo local. / Tailor the product portfolio to the cultural profile of the target market (Action/Shooters in Western markets; RPGs and handheld formats in Japan), avoiding disproportionate distribution investments for ecosystems lacking local adoption.
3. **Gestión de calidad y recepción:** Enfocar esfuerzos en el cumplimiento de estándares técnicos y narrativos valorados por la crítica especializada, dada su correlación positiva con el volumen de ventas. / Focus efforts on meeting technical and narrative standards valued by specialized critics, given their positive correlation with sales volume.

---

## Requisitos Técnicos / Technical Requirements

* Python 3.8 o superior / Python 3.8 or higher
* `pandas`
* `numpy`
* `matplotlib`
* `seaborn`
* `scipy`
* `jupyter`

