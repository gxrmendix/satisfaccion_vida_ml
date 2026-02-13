# Construcción y Análisis de un Dataset de Satisfacción de Vida (2021–2025)

## Descripción del proyecto

Este proyecto tiene como objetivo la construcción y análisis de un dataset de satisfacción de vida para el periodo 2021–2025, integrando fuentes oficiales internacionales y aplicando técnicas de Machine Learning para evaluar la relación entre bienestar subjetivo y desarrollo económico.

El trabajo forma parte de una actividad académica del curso de Machine Learning, enfatizando:

- Construcción reproducible de datasets
- Integración de fuentes heterogéneas
- Buenas prácticas de limpieza y organización de datos
- Modelado predictivo
- Versionamiento y documentación en GitHub

---

## Fuentes de datos

Las variables utilizadas fueron:

| Variable | Fuente | Rol |
|----------|--------|------|
| GDP per capita | World Bank Open Data | Feature |
| Life satisfaction | OECD Better Life Index | Label |

Periodo analizado: **2021–2025**

---

## Construcción del Dataset

El proceso incluyó:

1. Carga de bases originales en formato CSV.
2. Filtrado del indicador *Life satisfaction* (OECD).
3. Selección de GDP per capita (World Bank).
4. Transformación del formato de datos económicos mediante `melt` para obtener estructura tipo panel (Country–Year).
5. Integración mediante `merge` por país y año.
6. Eliminación de valores faltantes.
7. Exportación del dataset final.

El dataset resultante contiene:

- `Country`
- `Year`
- `Life_satisfaction`
- `GDP_per_capita`
- `log_GDP` (transformación aplicada)

---

## Análisis exploratorio

Se realizaron:

- Visualización GDP vs Life Satisfaction
- Análisis de correlación
- Evolución temporal 2021–2025
- Identificación de países atípicos (outliers)

Hallazgos principales:

- Relación positiva entre PIB per cápita y satisfacción de vida.
- Evidencia de no linealidad en la relación.
- Existencia de países con bienestar mayor o menor al esperado dado su nivel de ingreso.

---

## Modelos implementados

Se probaron tres modelos:

1. **Regresión Lineal Simple**
2. **Modelo Log-Lineal**
3. **Random Forest Regressor**

Resultados aproximados:

| Modelo | R² | MSE |
|--------|----|-----|
| Lineal | ~0.40 | ~0.33 |
| Log-Lineal | Mejora moderada |
| Random Forest | Mejor ajuste |

Conclusión metodológica:

> El PIB explica parcialmente el bienestar subjetivo, pero la relación presenta no linealidades y existen factores adicionales no capturados por el ingreso.

---

## Estructura del Repositorio

satisfaccion_vida_ml/
│
├── data/
│ ├── OECD_DF_BLI_all.csv
│ ├── gdp-per-capita-worldbank.csv
│
├── notebooks/
│ └── analisis_satisfaccion.ipynb
│
├── dataset_satisfaccion_vida_2021_2025.csv
├── README.md
└── requirements.txt

---

## Reproducibilidad

Para reproducir el análisis:

```bash
pip install -r requirements.txt
```

Ejecutar el notebook:
notebooks/analisis_satisfaccion.ipynb

## Conclusiones generales:

1. El desarrollo económico está asociado positivamente con la satisfacción de vida.

2. El modelo lineal simple es insuficiente.

3. La transformación logarítmica mejora el ajuste.

4. Los modelos no paramétricos capturan mejor la relación.

5. Existen países estructuralmente más felices o menos felices de lo esperado.
