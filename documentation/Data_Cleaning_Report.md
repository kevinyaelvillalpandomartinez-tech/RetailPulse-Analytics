# Data Cleaning Report
## RetailPulse Analytics

### Sprint 3 — Data Cleaning & Data Preparation

## 1. Objetivo

El objetivo de este sprint fue limpiar, validar y preparar el dataset de RetailPulse para garantizar que la información utilizada en los análisis posteriores sea consistente, confiable y adecuada para su utilización en Python, SQL y Power BI.

El dataset original contiene 9,994 líneas de venta y 21 variables. Después del proceso de preparación, el dataset final conserva las 9,994 observaciones y contiene 26 variables.

No fue necesario eliminar registros durante el proceso de limpieza, ya que no se identificaron duplicados completos, valores nulos ni registros que incumplieran las principales reglas de negocio establecidas.

## 2. Fuente de datos

El proceso de limpieza se realizó utilizando el dataset original almacenado en:

`data/raw/Sample - Superstore.csv`

El archivo original se mantuvo sin modificaciones con el objetivo de preservar la fuente de datos y garantizar la reproducibilidad del proceso.

Todas las transformaciones fueron realizadas sobre una copia de trabajo denominada `df_clean`.

El dataset procesado fue exportado posteriormente a:

`data/processed/superstore_clean.csv`

## 3. Transformaciones realizadas

### 3.1 Conversión de fechas

Las variables `Order Date` y `Ship Date` fueron convertidas de texto a formato `datetime`.

Esta transformación permite realizar operaciones temporales, calcular tiempos de envío y generar variables derivadas para el análisis por año, mes y trimestre.

### 3.2 Optimización de variables categóricas

Se evaluó la cardinalidad de las variables de texto y se convirtieron al tipo `category` las siguientes columnas:

- Ship Mode
- Segment
- Country
- City
- State
- Region
- Category
- Sub-Category

El consumo de memoria del DataFrame se redujo aproximadamente de **9.2 MB a 4.3 MB**, equivalente a una reducción cercana al **53 %** durante el procesamiento en Pandas.

Las variables `Customer ID`, `Customer Name`, `Product ID` y `Product Name` se conservaron como texto debido a su función como identificadores o a su mayor cardinalidad.

## 4. Validación de reglas de negocio

Se implementaron controles de calidad para verificar la consistencia lógica de los datos.

| Regla de validación | Registros inconsistentes | Resultado |
|---|---:|---|
| Sales > 0 | 0 | Aprobado |
| Quantity > 0 | 0 | Aprobado |
| 0 ≤ Discount ≤ 1 | 0 | Aprobado |
| Ship Date ≥ Order Date | 0 | Aprobado |
| Shipping Days ≥ 0 | 0 | Aprobado |
| Valores nulos | 0 | Aprobado |
| Filas completamente duplicadas | 0 | Aprobado |

No se identificaron registros que requirieran eliminación o corrección de acuerdo con las reglas anteriores.

## 5. Tratamiento de pérdidas y valores extremos

Se identificaron **1,871 líneas de venta con `Profit < 0`**, equivalentes aproximadamente al **18.7 % de los registros**.

Estos valores no fueron considerados automáticamente errores de calidad, ya que pueden representar operaciones comerciales reales en las que los costos asociados superaron los ingresos obtenidos.

Al revisar las transacciones con mayores pérdidas se observaron descuentos elevados y una presencia recurrente de subcategorías como `Machines`, `Binders` y `Tables`.

Los valores extremos de `Profit` fueron conservados debido a que son comercialmente plausibles y pueden contener información relevante sobre la rentabilidad del negocio.

Se plantea como hipótesis para el análisis exploratorio posterior que los descuentos elevados podrían estar relacionados con una reducción de la rentabilidad. Esta relación deberá validarse utilizando el conjunto completo de datos.

## 6. Validación de identificadores y granularidad

Se verificaron los principales identificadores del dataset.

| Métrica | Resultado |
|---|---:|
| Líneas de venta | 9,994 |
| Row ID únicos | 9,994 |
| Order ID únicos | 5,009 |
| Customer ID únicos | 793 |
| Product ID únicos | 1,862 |
| Product Name únicos | 1,850 |

Los resultados confirman que el dataset se encuentra a nivel de **línea de pedido**.

Una misma orden puede contener múltiples productos, por lo que la repetición de `Order ID` no representa duplicidad.

Asimismo, se identificó que algunos nombres de producto están asociados con múltiples `Product ID`. Debido a que no se dispone de un catálogo maestro que permita determinar si corresponden a diferentes SKU, variantes o inconsistencias de codificación, los identificadores originales fueron conservados.

Para futuros indicadores deberá distinguirse entre líneas de venta, pedidos únicos, clientes únicos y productos únicos.


## 7. Feature Engineering

Se crearon cinco variables derivadas para facilitar los análisis posteriores:

| Variable | Descripción |
|---|---|
| Shipping Days | Días transcurridos entre la realización del pedido y su envío |
| Order Year | Año en que se realizó el pedido |
| Order Month | Número del mes del pedido (1–12) |
| Order Month Name | Nombre del mes |
| Order Quarter | Trimestre del pedido (1–4) |

La variable `Shipping Days` presenta valores entre **0 y 7 días**, con un promedio aproximado de **3.96 días** y una mediana de **4 días**.

Las variables temporales permitirán analizar posteriormente tendencias, estacionalidad y comportamiento de ventas por periodo.

## 8. Resultado final

Después del proceso de limpieza, validación y preparación, el dataset final presenta:

- **9,994 registros**
- **26 variables**
- **0 valores nulos**
- **0 filas completamente duplicadas**
- **0 ventas iguales o menores a cero**
- **0 cantidades iguales o menores a cero**
- **0 descuentos fuera del rango permitido**
- **0 inconsistencias entre las fechas de pedido y envío**
- **0 tiempos de envío negativos**

El dataset procesado fue exportado correctamente a:

`data/processed/superstore_clean.csv`

Posteriormente se realizó una prueba de lectura del archivo exportado, confirmando una dimensión de **9,994 filas × 26 columnas** y la ausencia de valores nulos.

El dataset queda preparado para las siguientes etapas de análisis exploratorio, consultas SQL y visualización en Power BI.