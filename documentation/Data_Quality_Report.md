# Data Quality Report

## Proyecto

**RetailPulse Analytics**

**Autor:** Kevin Yael Villalpando Martínez

**Rol:** Data Analyst Junior

**Fecha:** Agosto 2026

---

# Objetivo

Evaluar la calidad del conjunto de datos para identificar posibles problemas que puedan afectar el análisis y definir las acciones necesarias durante la etapa de limpieza y preparación de datos.

---

# Resumen del dataset

| Métrica               |      Resultado |
| --------------------- | -------------: |
| Registros             |          9,994 |
| Variables             |             21 |
| Valores nulos         | No encontrados |
| Variables de fecha    |              2 |
| Variables numéricas   |              6 |
| Variables categóricas |             13 |

---

# Validaciones realizadas

## 1. Integridad de los datos

**Resultado:** ✅ Aprobado

No se identificaron valores nulos en las columnas del dataset.

**Acción requerida:** Ninguna.

---

## 2. Tipos de datos

**Resultado:** ⚠ Requiere ajuste

Las columnas **Order Date** y **Ship Date** fueron importadas como texto y deberán convertirse al tipo `datetime`.

Las variables categóricas podrán convertirse al tipo `category` para optimizar el uso de memoria.

**Acciones:**

* Convertir `Order Date` a `datetime`.
* Convertir `Ship Date` a `datetime`.
* Convertir variables categóricas a `category`.

---

## 3. Registros duplicados

**Resultado:** Revisado

Se evaluó la existencia de registros duplicados mediante `duplicated()`.

Los registros identificados deberán analizarse para determinar si representan errores de captura o múltiples líneas válidas de una misma orden.

**Acción requerida:** Validar antes de eliminar cualquier registro.

---

## 4. Valores atípicos

**Resultado:** Detectados

Los diagramas de caja muestran valores atípicos principalmente en:

* Sales
* Profit

Estos registros podrían corresponder a ventas de alto valor y no necesariamente representan errores.

**Acción requerida:** Analizar su impacto antes de decidir si deben eliminarse o mantenerse.

---

## 5. Distribución de variables

Las distribuciones muestran que:

* Sales presenta una distribución sesgada hacia la derecha.
* Profit contiene valores negativos.
* Discount presenta una concentración importante en valores bajos.
* Quantity corresponde a una variable discreta con pocos valores posibles.

---

# Riesgos identificados

| Riesgo                        | Impacto |
| ----------------------------- | ------- |
| Fechas almacenadas como texto | Alto    |
| Posibles registros duplicados | Medio   |
| Outliers en Sales y Profit    | Medio   |
| Descuentos elevados           | Alto    |

---

# Recomendaciones para el Sprint 3

Durante la etapa de limpieza de datos se recomienda:

1. Convertir variables de fecha al tipo `datetime`.
2. Optimizar las variables categóricas utilizando el tipo `category`.
3. Revisar los registros duplicados antes de eliminarlos.
4. Analizar el comportamiento de los valores atípicos.
5. Validar que las métricas comerciales sean consistentes después de la transformación de datos.

---

# Conclusión

El conjunto de datos presenta una buena calidad general y es adecuado para continuar con el análisis.

Los principales ajustes requeridos corresponden a la conversión de tipos de datos y la evaluación de valores atípicos. No se identificaron problemas críticos que impidan continuar con el proyecto.
