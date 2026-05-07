# Análisis de Hotspots: Burger Master Bogotá 2022
Identificación de zonas de concentración gastronómica mediante Gaussian Mixture Models (GMM) y Kernel Density Estimation (KDE).

---

## Problema

El Burger Master es uno de los eventos gastronómicos más grandes de Colombia. En 2022, **63 restaurantes participaron con 116 sedes en Bogotá**. La pregunta es concreta: ¿dónde se concentra la oferta? ¿Existen zonas claramente diferenciadas con alta densidad de restaurantes?

---

## Resultados clave

- Se identificaron **5 zonas geográficas diferenciadas** en Bogotá mediante GMM.
- El **corredor oriental (Chapinero–Teusaquillo)** es la zona de mayor densidad de restaurantes participantes.
- **Chía** emerge como un grupo geográficamente aislado del resto de la ciudad.
- KDE y GMM coinciden en los hotspots principales, confirmando la robustez del análisis.
- El análisis habilita segmentación de comunicaciones y estrategias de marketing por zona geográfica.

---

## Metodología

| Método | Tipo | Qué entrega | Cuándo usarlo |
|---|---|---|---|
| **GMM** | Paramétrico | Etiquetas de cluster + probabilidades de pertenencia | Segmentar zonas y asignar cada sede a un grupo |
| **KDE** | No paramétrico | Superficie continua de densidad espacial | Identificar intensidad y gradientes de concentración |

**Selección de parámetros GMM:** barrido de k = 1–12 componentes × 4 tipos de covarianza (`full`, `tied`, `diag`, `spherical`). Criterio de selección: BIC mínimo → **k = 5, covarianza full**.

**Selección de ancho de banda KDE:** validación cruzada de máxima verosimilitud (`cv_ml` de `statsmodels`).

---

## Estructura del proyecto

```
kde_gmm_burguer-master/
├── data/
│   └── burger_master.xlsx      # Dataset: 137 sedes georreferenciadas
├── kde_gmm_burguer_master.ipynb
├── requirements.txt
├── .gitignore
└── README.md
```

---

## Cómo ejecutar

```bash
# 1. Clonar el repositorio
git clone https://github.com/jabondanoaraoz/kde-gmm-burguer-master.git
cd kde-gmm-burguer-master

# 2. Instalar dependencias
pip install -r requirements.txt

# 3. Abrir el notebook
jupyter notebook kde_gmm_burguer_master.ipynb
```

---

## Stack tecnológico

| Librería | Rol |
|---|---|
| `pandas` / `numpy` | Manipulación y transformación de datos |
| `scikit-learn` | GMM (`GaussianMixture`), selección de hiperparámetros |
| `statsmodels` | KDE bivariado con selección de bandwidth por `cv_ml` |
| `folium` | Mapas interactivos con popups y capas |
| `geopandas` / `osmnx` / `shapely` | Datos y geometrías geoespaciales |
| `matplotlib` / `seaborn` | Visualizaciones estáticas (elipses de covarianza, contornos) |
| `branca` | Escalas de color para mapas Folium |

---

## Contexto Académico

Este proyecto fue desarrollado como parte del programa de **Maestría en Inteligencia Analítica de Datos (MIAD)** de la Universidad de los Andes, Colombia.

---

## Autor

**Joaquín Abondano Araoz** - Data Analytics · AI & Automation · Strategic Planning

[Website](https://joaquinabondano.com) · [LinkedIn](https://linkedin.com/in/joaquin-abondano) · [GitHub](https://github.com/jabondanoaraoz)
