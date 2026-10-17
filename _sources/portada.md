# Entregable 2 · Dashboard de Bank Marketing: informe del desarrollo

**Dashboard en Dash Plotly con tres pestañas e informe que interpreta cada uno de sus resultados**

- **Autor:** Donny Torres
- **Programa:** Maestría en Analítica de Datos, Universidad del Norte (Barranquilla)
- **Asignatura:** Machine Learning
- **Fecha:** octubre de 2026
- **Conjunto de datos:** *Bank Marketing* con contexto social y económico (`bank-additional-full.csv`), UCI Machine Learning Repository: <https://archive.ics.uci.edu/dataset/222/bank+marketing> (licencia CC BY 4.0)
- **Dashboard:** <https://bank-marketing-dashboard-dtorres.onrender.com> (el servicio gratuito se duerme tras 15 minutos sin visitas, así que la primera carga puede tardar cerca de dos minutos)

## Contenido

El dashboard presenta, en tres pestañas, el contexto del problema, la exploración de los datos y los modelos base para predecir si un cliente contactado en una campaña de telemercadeo de un banco portugués suscribirá un depósito a término. Este libro es el informe del desarrollo: interpreta cada resultado que aparece en el dashboard y reúne los detalles del análisis que el dashboard no muestra.

**Parte I. El dashboard y la interpretación de sus resultados.** Un capítulo por pestaña, con los resultados en el mismo orden en que aparecen y una interpretación de cada uno:

1. **Contexto del problema:** tamaño y depuración de la base, resultado de las llamadas, tasa de referencia, reparto entre entrenamiento y prueba, serie mensual y selector de año.
2. **EDA:** tasa de suscripción por categoría, datos sin informar, distribución de las variables numéricas, serie mensual y fuga de información de `duration`.
3. **Modelos base:** tarjetas de desempeño, métricas de los cuatro modelos (con y sin recalibración), curva ROC, matrices de confusión, cambio de prevalencia por mes, punto operativo y configuración del modelo.

**Parte II. Desarrollo completo.** Las secciones del cuaderno ejecutado (`Entregable 2 - Bank Marketing.ipynb`), con lo que el dashboard no muestra: diccionario de variables y calidad de los datos, reserva del conjunto de prueba, análisis uni, bi y multivariado, auditoría de fuga, componente temporal, preprocesamiento, búsqueda de hiperparámetros, intervalos de confianza, calibración y recalibración del intercepto, curva de aprendizaje, coeficientes y su estabilidad, diagnóstico temporal, comparación con modelos más flexibles, conclusiones y limitaciones. Un mapa al inicio de la parte indica dónde está cada detalle.

## Cambios respecto del primer entregable

Esta versión incorpora la retroalimentación del primer entregable. El componente temporal está completo (serie diaria, descomposición, estacionariedad, dependencia, cambios de régimen y deriva de concepto). La regularización se elige por pérdida logarítmica (`C = 0,01`), porque con `C = 100` los coeficientes eran inestables, y se mide su estabilidad. El cambio de prevalencia se corrige con una recalibración mensual del intercepto que usa solo los meses ya cerrados. Además, el modelo base se compara con modelos más flexibles en las mismas condiciones.

## Cómo leer las interpretaciones

Cada interpretación tiene tres párrafos y sigue el mismo orden: primero lo que muestra el resultado, con las cifras reales; luego lo que significa para el problema o para el modelo; y al final la decisión que se toma a partir de ello. Las cifras se calculan en la misma ejecución que genera el texto, de modo que coinciden con las salidas.

Las pestañas 1 y 2 del dashboard responden al selector de año; la pestaña 3 no, porque la prueba temporal debe permanecer fija. En este libro todas las cifras corresponden a la opción «Todos» del selector, salvo donde se indique un año.

## Reproducibilidad

La partición entrenamiento-prueba es cronológica y, por tanto, determinista; los procedimientos aleatorios usan la semilla `SEED = 42`. El dashboard y los capítulos de la Parte I usan el mismo módulo de código (`src/dashboard_bank_marketing.py`), y los capítulos de la Parte II son el cuaderno ejecutado, dividido por secciones.
