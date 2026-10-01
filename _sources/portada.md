# Entregable 1 · Predicción de la suscripción a depósitos a término

**Selección de la base de datos, análisis exploratorio e implementación del modelo base**

- **Autor:** Donny Torres
- **Programa:** Maestría en Analítica de Datos, Universidad del Norte (Barranquilla)
- **Asignatura:** Machine Learning
- **Fecha:** octubre de 2026
- **Conjunto de datos:** *Bank Marketing* con contexto social y económico (`bank-additional-full.csv`), UCI Machine Learning Repository: <https://archive.ics.uci.edu/dataset/222/bank+marketing> (licencia CC BY 4.0)

## Contenido

El proyecto predice, con la información disponible antes de la llamada, si un cliente contactado en una campaña de telemercadeo de un banco portugués suscribirá un depósito a término. Sigue la ruta A del enunciado (clasificación) con partición y validación cronológicas, porque las filas están ordenadas en el tiempo: describe y audita la base de datos, reserva el último 20 % de los registros como prueba antes de cualquier decisión, desarrolla el análisis exploratorio uni, bi y multivariado con la auditoría de fuga (incluida la fuga por `duration` y la fuga temporal por el orden cronológico de las filas) y compara una regresión logística dentro de un `Pipeline` contra un `DummyClassifier`, con validación temporal, intervalos de confianza *bootstrap* por bloques de día, calibración, curva de aprendizaje y el recorrido de la nota crítica del enunciado.

Los capítulos siguientes corresponden a las secciones del cuaderno ejecutado:

1. **Base de datos:** problema, justificación, fuente y licencia, diccionario, estructura, calidad y consideraciones éticas.
2. **Reserva del conjunto de prueba:** partición cronológica 80/20 (primer 80 % de los registros en orden temporal para entrenamiento y último 20 % para prueba).
3. **Análisis exploratorio de datos:** variable objetivo, análisis uni, bi y multivariado, auditoría de fuga, orden temporal y preprocesamiento.
4. **Modelo base:** regresión logística frente a la línea base trivial.
5. **Conclusiones y limitaciones.**
6. **Referencias.**

La entrega incluye la base de datos (`data/bank-additional-full.csv`), el archivo de dependencias (`requirements.txt`) y el cuaderno `Entregable 1 - Bank Marketing.ipynb`, que se ejecuta de principio a fin; los procedimientos aleatorios usan la semilla `SEED = 42`.
