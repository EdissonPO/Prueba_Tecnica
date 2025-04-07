# Predicción del Gasto por Categoría de Clientes

Este proyecto busca predecir el gasto mensual de los clientes por categoría (`mcc`) a partir de sus transacciones históricas, datos de tarjeta, comportamiento financiero y demográfico. Se construyen modelos de regresión a partir de datos reales agrupados por cliente, categoría y mes.

## 📁 Estructura del Proyecto

- `exploracion_y_tratamiento_datos.ipynb`: análisis exploratorio, transformación y limpieza de los datos originales.
- `entrenamientos_v1.ipynb`: entrenamiento de modelos a nivel transacción (regresión lineal, random forest, lightGBM).
- `entrenamientos_v2.ipynb`: entrenamiento de modelos sobre datos agregados por cliente, categoría y mes.

## 🎯 Objetivo

Predecir el gasto mensual (`amount`) de cada cliente en cada categoría (`mcc`) con el fin de entender patrones de consumo, detectar cambios de comportamiento y construir una base para sistemas de recomendación o alertas de gasto.

## 🧾 Datos Utilizados

- **Transacciones individuales** con variables como:
  - Fecha y hora de la transacción
  - Tipo de uso (chip, online, swipe)
  - Categoría (`mcc`), comercio, ciudad, ubicación
  - Monto (`amount`) y su versión transformada (`log_amount`)

- **Datos del cliente y tarjeta**:
  - Género, edad, ingresos, deuda, score crediticio
  - Información de la tarjeta y su tipo (crédito/débito)

## ⚙️ Preprocesamiento

- Eliminación de variables irrelevantes
- Agrupación de datos por cliente, categoría, año y mes
- Transformación logarítmica de montos (`log1p`)
- Agregación de features: medias, máximos, horas, frecuencias, etc.

## 🤖 Modelos Entrenados

- Regresión Lineal (baseline)
- Random Forest Regressor
- LightGBM Regressor
- Random Forest sobre datos agregados por `client_id`, `mcc`, año y mes

## 📊 Resultados (final)

| Modelo                     | MAE   | RMSE   | R² (log) |
|---------------------------|-------|--------|----------|
| Regresión Lineal          | ~37   | ~76    | 0.08     |
| Random Forest (transacción) | ~13   | ~34    | 0.87     |
| LightGBM (transacción)    | ~22   | ~48    | 0.69     |
| Random Forest (agrupado)  | ~80   | ~174   | 0.71     |

> ⚠️ En modelos sobre datos agrupados se eliminan columnas como `avg_transaction` para evitar sobreajuste.

## 🛠️ Requisitos

- Python 3.9+
- pandas, numpy
- scikit-learn
- lightgbm
- matplotlib (opcional para visualizaciones)

Instalación rápida:

```bash
pip install -r requirements.txt
```

## 🚀 Cómo Ejecutar

1. Abrir y ejecutar `exploracion_y_tratamiento_datos.ipynb`
2. Ejecutar modelos base en `entrenamientos_v1.ipynb`
3. Entrenar modelos agregados en `entrenamientos_v2.ipynb`
4. Evaluar métricas y exportar predicciones

---

Proyecto desarrollado por Edisson Penagos Ospina como parte de una prueba técnica.
