# Data Dictionary

## Proyecto

**RetailPulse Analytics**

**Autor:** Kevin Yael Villalpando Martínez

**Versión:** 1.0

**Última actualización:** Agosto 2026

---

# Objetivo

Este diccionario de datos documenta la estructura del dataset **Sample Superstore**, describiendo el significado, tipo de dato y utilidad de cada una de las variables utilizadas durante el proyecto. Su propósito es facilitar la comprensión del conjunto de datos y asegurar un uso consistente de la información durante las etapas de análisis, limpieza y visualización.

---

# Diccionario de datos

| Variable      | Tipo de dato | Descripción                                                                      | Uso en el análisis                               |
| ------------- | ------------ | -------------------------------------------------------------------------------- | ------------------------------------------------ |
| Row ID        | Integer      | Identificador único de cada registro.                                            | Control de registros.                            |
| Order ID      | Texto        | Identificador único del pedido. Un mismo pedido puede contener varios productos. | Conteo de pedidos y análisis de ventas.          |
| Order Date    | Fecha        | Fecha en que el cliente realizó el pedido.                                       | Tendencias temporales y series de tiempo.        |
| Ship Date     | Fecha        | Fecha en que el pedido fue enviado.                                              | Análisis de tiempos de entrega.                  |
| Ship Mode     | Categórica   | Método de envío utilizado.                                                       | Comparación de desempeño logístico.              |
| Customer ID   | Texto        | Identificador único del cliente.                                                 | Análisis de clientes y recurrencia.              |
| Customer Name | Texto        | Nombre del cliente.                                                              | Identificación de clientes relevantes.           |
| Segment       | Categórica   | Segmento comercial del cliente (Consumer, Corporate, Home Office).               | Segmentación de clientes.                        |
| Country       | Categórica   | País donde se realizó la venta.                                                  | Análisis geográfico.                             |
| City          | Categórica   | Ciudad de la venta.                                                              | Análisis geográfico detallado.                   |
| State         | Categórica   | Estado donde se realizó la venta.                                                | Comparación regional.                            |
| Postal Code   | Entero       | Código postal del cliente.                                                       | Variable geográfica de apoyo.                    |
| Region        | Categórica   | Región comercial (East, West, Central, South).                                   | Comparación regional.                            |
| Product ID    | Texto        | Identificador único del producto.                                                | Análisis de productos.                           |
| Category      | Categórica   | Categoría principal del producto.                                                | Análisis de ventas por categoría.                |
| Sub-Category  | Categórica   | Subcategoría del producto.                                                       | Identificación de productos con mejor desempeño. |
| Product Name  | Texto        | Nombre comercial del producto.                                                   | Ranking de productos.                            |
| Sales         | Decimal      | Valor total de la venta.                                                         | KPI principal de ingresos.                       |
| Quantity      | Entero       | Número de unidades vendidas.                                                     | Volumen de ventas.                               |
| Discount      | Decimal      | Descuento aplicado a la venta.                                                   | Evaluación del impacto de promociones.           |
| Profit        | Decimal      | Utilidad obtenida por la venta.                                                  | KPI principal de rentabilidad.                   |

---

# Observaciones

* Las columnas **Order Date** y **Ship Date** deberán convertirse al tipo de dato `datetime`.
* Las variables **Country**, **City**, **State**, **Region**, **Category**, **Sub-Category**, **Segment** y **Ship Mode** podrán convertirse al tipo `category` para optimizar el uso de memoria y mejorar el rendimiento en los análisis.
* Las métricas principales del proyecto serán **Sales**, **Profit**, **Quantity** y **Discount**, ya que permitirán evaluar el desempeño comercial y la rentabilidad del negocio.
