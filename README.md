**Mantenimiento Predictivo con IA para Rodamientos en Compresores.**

**Descripción General del Proyecto**

Este proyecto presenta el desarrollo y la evaluación de un modelo de Deep Learning para el mantenimiento predictivo, enfocado en la estimación del Tiempo Restante de Vida Útil (RUL) de rodamientos en maquinaria industrial crítica. El objetivo es anticipar fallas mecánicas analizando datos de vibración en tiempo real, permitiendo así una planificación proactiva del mantenimiento para minimizar las paradas de producción no planificadas.

Se realiza una comparativa entre dos arquitecturas de redes neuronales: una LSTM, como modelo base robusto, y un Transformer, como modelo de última generación, para determinar la solución más fiable y precisa para este caso de uso.

**Problema de Negocio**

Las paradas no planificadas debido a fallas inesperadas en componentes críticos, como los rodamientos, representan uno de los mayores costos ocultos en la industria. Estos eventos generan:

Pérdidas de producción directas.

Costos elevados por reparaciones de emergencia.

Riesgos de seguridad y daños en cadena a otros equipos.

Este proyecto aborda directamente este problema al transformar datos de sensores, que ya se recopilan, en un sistema de alerta temprana accionable.

**Dataset Utilizado**

El proyecto utiliza el reconocido dataset del IMS Bearing Data Center, proporcionado por la Universidad de Cincinnati y alojado por la NASA.

Subconjunto Utilizado: 1st_test

Descripción: Contiene datos de vibración de 4 rodamientos operados de forma continua a 2000 RPM hasta la falla. Los datos se registraron en 2,156 archivos, cada uno representando 1 segundo de mediciones.

Foco del Análisis: El estudio se centra en el Rodamiento 3, cuya degradación está documentada.

**Estructura de Archivos a utilizar**: 

Link a Dataset y archivos checkpoint para cargar y optimizar https://drive.google.com/drive/folders/17M7zb2sdt6eryOEmFFYmIhJyjIh2BRjr?usp=sharing **IMPORTANTE: DESCARGAR ARCHIVOS .NPY, JSON Y .PTH y adecuar las rutas en la carga de "checkpoint"**

A continuación se detallan los archivos clave generados y guardados en Google Drive, que permiten la reproducibilidad y el análisis del proyecto sin necesidad de re-ejecutar todos los pasos.

Datos de Orgien --> Carpeta 1st_TEST , con los 2156 archivos.

**1. Datos Preprocesados**
Estos archivos contienen los datos de origen después de la limpieza y transformación, listos para ser consumidos por los modelos.

*processed_data.npy*:

Contenido: Un único y gran array de NumPy que contiene los datos de vibración de todos los archivos del dataset, concatenados en orden cronológico.

Propósito: Sirve como la fuente de datos de entrada (X) para la creación de secuencias. Evita tener que leer y procesar los 2,156 archivos originales en cada sesión.

*processed_rul.npy*:

Contenido: Un array de NumPy del mismo tamaño que el anterior, donde cada punto de datos tiene su correspondiente etiqueta de Vida Útil Restante (RUL) normalizada entre 0 y 1.

Propósito: Contiene las etiquetas (y) que los modelos deben aprender a predecir.

**2. Artefactos del Modelo LSTM Benchmark**
Archivos relacionados con el entrenamiento y evaluación del modelo base.

*rul_lstm_model_reducido.pth*:

Contenido: Los pesos y sesgos (el "conocimiento") del modelo LSTM después de haber sido entrenado. No contiene la arquitectura, solo los parámetros aprendidos.

Propósito: Permite cargar el modelo entrenado para hacer predicciones futuras sin necesidad de volver a entrenarlo.

*training_history_reducido.json*:

Contenido: Un archivo de texto en formato JSON que almacena la pérdida (loss) de entrenamiento y validación de cada época del entrenamiento de la LSTM.

Propósito: Permite graficar y analizar la curva de aprendizaje del modelo para diagnosticar su rendimiento.

*predictions.npy y labels.npy:*

Contenido: Dos arrays de NumPy. predictions.npy contiene las predicciones de RUL que hizo el modelo LSTM sobre el conjunto de validación. labels.npy contiene los valores reales correspondientes.

Propósito: Permiten realizar una evaluación cuantitativa (cálculo de métricas como MAE y RMSE) y cualitativa (gráficos de dispersión) del rendimiento del modelo.

**3. Artefactos del Modelo Transformer**

Archivos relacionados con el entrenamiento y evaluación del modelo experimental.

*rul_transformer_model.pth:*

Contenido: Los pesos y sesgos aprendidos por el modelo Transformer.

Propósito: Guardar el estado del modelo Transformer entrenado para su posterior análisis y predicción.

*training_history_transformer.json:*

Contenido: El historial de pérdida de entrenamiento y validación para el modelo Transformer.

Propósito: Analizar la curva de aprendizaje y diagnosticar el sobreajuste que se observó.

*predictions_transformer.npy y labels_transformer.npy:*

Contenido: Las predicciones de RUL hechas por el modelo Transformer y sus correspondientes etiquetas reales.

Propósito: Evaluar cuantitativa y cualitativamente el rendimiento del Transformer y compararlo directamente con el de la LSTM.
