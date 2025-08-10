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
El conjunto de datos (2156 archivos) está en un zip 

- Se guardaron datos preprocesados para ser cargados directamente en los archivos XXX e YYY
- Se guardaron los datos de los modelos entrenados,sus pesos y predicciones para optimizar la ejecución de la NB

**- DESCRIBIR LOS ARCHIVOS DE GITHUB**
