# Previsión de la Demanda para Gestión de Inventarios

Trabajo Final de Máster — Máster en Ciencia de Datos (UOC)  
Autor: Gerard  
Curso: 2025–2026

---

## Descripción del proyecto

Este trabajo desarrolla un sistema de previsión de la demanda diaria para un distribuidor de recambios de automoción con un catálogo de 861 productos activos. Se aplica la metodología CRISP-DM comparando cinco familias de modelos — desde benchmarks estadísticos clásicos hasta ensembles por stacking — y se cuantifica el impacto económico de la mejora en precisión sobre el dimensionamiento del stock de seguridad.

El proyecto está estructurado en tres notebooks independientes que siguen el flujo natural del ciclo CRISP-DM.

---

## Estructura del repositorio

```

```
---

## Datos de entrada



---

## Requisitos



---

## Orden de ejecución

Los notebooks deben ejecutarse en orden secuencial, ya que cada uno consume los ficheros exportados por el anterior.

**1. `1_TFM_preparacion_datos.ipynb`**  
Carga los datos originales, realiza la limpieza, el tratamiento de outliers, la reconstrucción de ventas en períodos de rotura de stock, el análisis ACF/PACF, el clustering de productos y la ingeniería de características.  
Genera: `data/processed/df_final.parquet`

**2. `2_TFM_modelado.ipynb`**  
Entrena y compara los modelos de previsión: Seasonal Naïve, Holt-Winters, Random Forest (base y optimizado), XGBoost (base y optimizado) y Stacking (v1 y v2). Realiza la validación walk-forward, el análisis de importancia de características y el análisis de residuos.  
Genera: `data/results/resultados_modelos.csv`, `data/results/rmse_escenarios.csv`

**3. `3_TFM_stock.ipynb`**  
Calcula el stock de seguridad y el coste de mantenimiento para los dos escenarios (Seasonal Naïve vs. modelo ganador) y cuantifica el ahorro económico a nivel de producto y de catálogo.  

---

## Resultados principales

| Clúster | Modelo ganador | Mejora RMSE vs Seasonal Naïve |
|---------|---------------|-------------------------------|
| 0 | Random Forest optimizado | 28,5% |
| 1 | Random Forest optimizado | 30,0% |
| 2 | Holt-Winters | 57,2% |

La mejora media del 29,8% en RMSE se traduce en una reducción de **4.331 unidades** de stock de seguridad y un ahorro anual estimado de **43.770€** aplicando una tasa de coste de mantenimiento del 20% anual.

---

## Metodología

El proyecto sigue la metodología **CRISP-DM** (Cross-Industry Standard Process for Data Mining) en sus seis etapas: comprensión del negocio, comprensión de los datos, preparación de los datos, modelado, evaluación y despliegue.
