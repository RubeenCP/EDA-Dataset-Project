# EDA-Dataset-Project
Este proyecto documenta el proceso completo de Análisis Exploratorio de Datos (EDA) sobre el conjunto de datos sintético Dirty Cafe Sales. 
El objetivo principal es aplicar un flujo de trabajo ordenado de ciencia de datos, desde la carga inicial y la exploración de la calidad, hasta la limpieza de datos y la generación de visualizaciones básicas.

El dataset fue seleccionado por su naturaleza intencionalmente "sucia" (contiene nulos, errores de formato, inconsistencias y duplicados), lo que permite demostrar habilidades sólidas en la corrección y preparación de datos antes de cualquier modelado avanzado.

## Herramientas Utilizadas
- Lenguaje: Python

- Manipulación de Datos: Pandas, NumPy

- Visualización: Matplotlib, Seaborn

## Fases del Análisis
El proceso se dividió en cuatro fases principales, detalladas en el notebook eda.ipynb:

- Carga y Estructura: Inspección de dimensiones, primeras filas, y detección inicial de tipos de datos incorrectos.

- Exploración de Calidad: Cálculo de valores nulos, identificación de duplicados y rangos anómalos.

- Limpieza y Normalización: Corrección justificada de tipos y tratamiento de inconsistencias.

- Visualización Básica: Generación de gráficos para describir las características del dataset limpio.

## Proceso de Limpieza y Justificación
La fase de limpieza fue crítica debido a la mala calidad inicial del dataset. Las principales acciones aplicadas fueron:

A. Corrección de Tipos de Datos
Las variables de cálculo (Quantity, Price Per Unit, Total Spent) se convirtieron a numéricos (float64), y Transaction Date a tipo de tiempo (datetime64). Esta acción expuso inmediatamente los errores de formato ('ERROR', strings) como valores nulos.

B. Tratamiento de Valores Nulos Críticos
- Eliminación: Se eliminaron 2107 filas que carecían de información fundamental en las variables clave (Item, Quantity, Total Spent, Transaction Date). Se justifica esta pérdida de datos para garantizar la integridad y coherencia de los cálculos de ventas.

- Imputación: Para las variables categóricas Location y Payment Method, los nulos y errores se unificaron en la categoría 'Desconocido'. Esto permitió conservar los registros para análisis de segmentación sin afectar los cálculos de ventas, ya que la falta de dato se convierte en una categoría analizable.

C. Normalización Categórica
Se aplicó la función .str.title() a las columnas categóricas (Item, Location, Payment Method) para asegurar la uniformidad en el conteo de categorías (ej., unificando 'cafe', 'CAFE' y 'Cafe' en 'Cafe').

## Hallazgos Clave de las Visualizaciones
- Distribución del Gasto (Histograma): La mayoría de las transacciones se concentran en un gasto total muy bajo, lo que es común en negocios de café.

- Productos Estrella (Gráfica de Barras): 'Coffee' y 'Tea' son, por amplio margen, los productos más vendidos en términos de volumen de transacciones.

- Tendencia Temporal (Gráfica de Líneas): El gasto total semanal se mantuvo relativamente estable a lo largo del periodo analizado, con fluctuaciones que merecerían un análisis más detallado de estacionalidad o eventos promocionales.
