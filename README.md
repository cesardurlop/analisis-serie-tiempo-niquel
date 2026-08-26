
# Análisis de serie de tiempo del precio del níquel

Este repositorio contiene el análisis de la serie de tiempo mensual del precio del níquel correspondiente al periodo de enero de 2015 a diciembre de 2024.

El objetivo es estudiar el comportamiento temporal de la serie, identificar la presencia de tendencia y estacionalidad, evaluar su estacionariedad y comparar distintos modelos de pronóstico para estimar los precios mensuales de 2025.

## Datos

La base de datos contiene 120 observaciones mensuales correspondientes al periodo:

- Inicio: enero de 2015
- Fin: diciembre de 2024
- Frecuencia: mensual
- Variable analizada: precio del níquel

El archivo utilizado es:

`niquel.xlsx`

El archivo debe contener las siguientes columnas:

- `Fecha`
- `Precio`

## Metodología

El análisis se realiza mediante las siguientes etapas:

1. Visualización de la serie temporal.
2. Verificación de meses faltantes.
3. Descomposición STL con periodo de 12 meses.
4. Cálculo de la fuerza de tendencia y estacionalidad.
5. Prueba de Dickey-Fuller aumentada (ADF) sobre la serie original.
6. Aplicación de primera diferencia.
7. Prueba ADF sobre la serie diferenciada.
8. Análisis de las funciones ACF y PACF.
9. Comparación de modelos de pronóstico.
10. Evaluación mediante MAE, RMSE y MAPE.
11. Selección del modelo con menor RMSE.
12. Ajuste del modelo seleccionado utilizando toda la serie.
13. Pronóstico mensual para enero-diciembre de 2025.

## Modelos evaluados

Se comparan los siguientes modelos:

- ARIMA(1,1,0)
- ARIMA(0,1,1)
- ARIMA(1,1,1)
- Holt con tendencia amortiguada

Los modelos ARIMA se seleccionaron considerando el comportamiento de la serie después de aplicar la primera diferencia y el análisis de las funciones ACF y PACF.

El método de Holt con tendencia amortiguada se incorpora como modelo externo de comparación.

## Validación

Para evaluar la capacidad predictiva de los modelos se utilizan los últimos 24 meses de la serie como conjunto de prueba.

De esta forma:

- Entrenamiento: enero de 2015 a diciembre de 2022.
- Prueba: enero de 2023 a diciembre de 2024.

Los modelos se comparan mediante:

- MAE: Error Absoluto Medio.
- RMSE: Raíz del Error Cuadrático Medio.
- MAPE: Error Porcentual Absoluto Medio.

Para los modelos ARIMA también se reportan:

- AIC
- BIC

El modelo con menor RMSE en el periodo de prueba se selecciona como modelo principal.

## Pronóstico 2025

Una vez seleccionado el modelo con mejor desempeño, se vuelve a ajustar utilizando las 120 observaciones disponibles entre enero de 2015 y diciembre de 2024.

Posteriormente se generan pronósticos mensuales para los 12 meses de 2025.

## Estructura del repositorio

```text
.
├── README.md
├── requirements.txt
├── .gitignore
├── analisis_niquel.py
├── niquel.xlsx
├── graficas/
└── resultados/
