# Data Understanding

## Proyecto

**RetailPulse Analytics**

**Autor:** Kevin Yael Villalpando Martínez

**Rol:** Data Analyst Junior

**Versión:** 1.0

**Fecha:** Agosto 2026

---

# Objetivo

El propósito de esta etapa es comprender la estructura, contenido y calidad del conjunto de datos antes de iniciar el proceso de limpieza y transformación. Este análisis permite identificar posibles problemas de calidad, validar los tipos de datos y conocer las características generales de la información para garantizar que el análisis posterior se base en datos confiables.

---

# 1. Descripción general del dataset

El conjunto de datos utilizado corresponde al archivo **Sample Superstore**, el cual contiene información histórica de ventas de una empresa del sector retail.

Cada registro representa una **línea de detalle de una orden de venta**, lo que significa que un mismo pedido (`Order ID`) puede aparecer en varias filas cuando incluye más de un producto.

El dataset integra información relacionada con clientes, productos, ventas, descuentos, utilidad, ubicación geográfica y logística de envío, permitiendo analizar el desempeño comercial desde diferentes perspectivas.

---

# 2. Dimensiones del dataset

| Característica      | Valor |
| ------------------- | ----: |
| Número de registros | 9,994 |
| Número de variables |    21 |

El volumen de información es suficiente para realizar un análisis exploratorio representativo y construir indicadores de desempeño para el negocio.

---

# 3. Estructura de las variables

Durante la exploración inicial se identificaron tres tipos principales de variables:

### Variables categóricas

* Ship Mode
* Customer ID
* Customer Name
* Segment
* Country
* City
* State
* Region
* Product ID
* Category
* Sub-Category
* Product Name

Estas variables permitirán segmentar el análisis por clientes, regiones, categorías y productos.

### Variables numéricas

* Sales
* Quantity
* Discount
* Profit
* Postal Code
* Row ID

Estas variables representan las principales métricas comerciales utilizadas para evaluar el desempeño del negocio.

### Variables de fecha

* Order Date
* Ship Date

Inicialmente estas columnas se encontraban almacenadas como texto, por lo que fueron identificadas para su conversión al tipo `datetime`, facilitando el análisis temporal.

---

# 4. Calidad de los datos

Se realizó una revisión inicial para evaluar la calidad del conjunto de datos.

## Valores nulos

Se verificó la existencia de valores faltantes mediante la función `isnull().sum()`.

**Resultado:**

No se identificaron valores nulos en ninguna de las variables del dataset.

Esto indica que no será necesario aplicar técnicas de imputación durante la etapa de limpieza.

---

## Registros duplicados

Se evaluó la existencia de registros duplicados mediante la función `duplicated()`.

En caso de encontrarse registros repetidos, será necesario determinar si corresponden a errores de captura o si representan transacciones válidas dentro del proceso de negocio.

---

## Tipos de datos

Los tipos de datos son consistentes con la naturaleza de la mayoría de las variables.

No obstante, se identificó la necesidad de convertir las columnas **Order Date** y **Ship Date** al tipo `datetime` para permitir análisis cronológicos.

Asimismo, variables categóricas como **Category**, **Sub-Category**, **Region**, **State**, **City**, **Country**, **Segment** y **Ship Mode** podrán convertirse al tipo `category` para optimizar el uso de memoria y mejorar el rendimiento del análisis.

---

# 5. Estadística descriptiva

Se calcularon estadísticas descriptivas para las principales variables numéricas.

Las variables analizadas fueron:

* Sales
* Profit
* Quantity
* Discount

Este análisis permitió conocer medidas de tendencia central, dispersión y valores extremos que servirán como referencia para identificar posibles anomalías durante la etapa de preparación de datos.

---

# 6. Distribución de las variables

Se construyeron histogramas para evaluar la distribución de las principales variables numéricas.

Los resultados muestran que:

* **Sales** presenta una distribución asimétrica hacia la derecha, indicando la existencia de pocas ventas de gran magnitud y un elevado número de ventas pequeñas.
* **Profit** contiene valores positivos y negativos, lo que evidencia la existencia de transacciones con pérdidas.
* **Discount** concentra gran parte de sus observaciones en valores bajos, aunque existen descuentos elevados que podrían afectar la rentabilidad.
* **Quantity** presenta una distribución discreta, predominando pedidos con pocas unidades.

---

# 7. Identificación de valores atípicos

Se utilizaron diagramas de caja (boxplots) para identificar posibles valores atípicos.

Se observaron outliers principalmente en:

* Sales
* Profit

Estos valores no necesariamente representan errores de captura, ya que podrían corresponder a ventas de alto valor o pedidos excepcionales.

Su tratamiento será evaluado durante la etapa de limpieza de datos.

---

# 8. Hallazgos principales

Durante la exploración inicial se identificaron los siguientes aspectos relevantes:

* El dataset contiene información suficiente para realizar análisis comerciales y financieros.
* No se detectaron valores nulos.
* Existen variables de fecha que requieren conversión al tipo `datetime`.
* Las variables categóricas pueden optimizarse utilizando el tipo `category`.
* Se identificaron valores atípicos en las variables **Sales** y **Profit**, los cuales deberán analizarse antes de decidir su tratamiento.
* La presencia de utilidades negativas sugiere que existen productos o pedidos que generan pérdidas para la empresa.
* Los descuentos elevados podrían estar relacionados con la disminución de la rentabilidad, por lo que será necesario evaluar esta relación en etapas posteriores.

---

# 9. Conclusiones

La exploración inicial permitió comprender la estructura y calidad del conjunto de datos.

En términos generales, el dataset presenta una buena calidad, ya que no se identificaron valores faltantes y la estructura de las variables es consistente con el contexto del negocio.

No obstante, antes de continuar con el análisis será necesario realizar actividades de preparación de datos, incluyendo la conversión de tipos de datos, la optimización de variables categóricas y la evaluación de valores atípicos.

Los hallazgos obtenidos durante esta etapa servirán como base para el **Sprint 3 – Data Cleaning & Data Preparation**, donde se preparará el conjunto de datos para el análisis exploratorio avanzado y la construcción del dashboard ejecutivo.
