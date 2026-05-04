# Executive Summary — GenkiClean Vending Sales EDA

## Contexto

Este proyecto analiza las ventas diarias de una máquina vending de productos de limpieza GenkiClean ubicada en CDMX.

La máquina vende productos por litro, acepta únicamente efectivo y tiene siete productos disponibles con tanques de 100 litros por producto.

El objetivo mensual esperado de venta es aproximadamente $25,000 MXN.

## Objetivo

El objetivo del análisis fue evaluar el comportamiento diario de ventas, identificar problemas de calidad de datos, detectar outliers y aplicar una estrategia de tratamiento basada en reglas estadísticas y lógica de negocio.

## Metodología

El análisis siguió siete etapas:

1. Visión general del dataset.
2. Estadísticas descriptivas.
3. Visualización diagnóstica.
4. Identificación formal de outliers con IQR.
5. Clasificación de outliers como Drop, Keep o Cap.
6. Estadísticas post-tratamiento.
7. Conclusión ejecutiva.

## Principales hallazgos

El dataset original contenía 376 registros. Durante la revisión inicial se identificaron 11 registros con problemas de calidad, incluyendo una fecha inválida, ventas negativas, inconsistencias de efectivo y valores extremadamente altos.

Antes del tratamiento, la venta diaria promedio era de $907.39 MXN. Sin embargo, esta métrica estaba influenciada por valores extremos cercanos a $10,000 y $20,000 MXN.

Después del tratamiento, el dataset quedó con 369 registros. La venta diaria promedio tratada fue de $831.60 MXN y la mediana fue de $815.00 MXN.

La venta máxima diaria pasó de $20,000.00 MXN a $1,965.00 MXN, reduciendo el impacto de valores extremos sobre la interpretación del negocio.

La venta mensual promedio tratada fue de $25,571.67 MXN, muy cercana al objetivo operativo de $25,000 MXN mensuales.

## Recomendaciones

1. Validar automáticamente los ingresos reportados contra los litros vendidos por producto.
2. Revisar diferencias entre efectivo recibido, cambio entregado y venta bruta.
3. Detectar outliers con métodos estadísticos, pero tratarlos con reglas de negocio.
4. Eliminar valores imposibles.
5. Conservar valores extremos válidos.
6. Aplicar winsorización cuando un valor sea posible pero demasiado influyente.
7. Evaluar el desempeño mensual únicamente después de limpiar y tratar los datos.

## Conclusión

El proyecto demuestra cómo un proceso estructurado de EDA puede mejorar la confiabilidad de las métricas comerciales.

Al limpiar los datos y tratar los outliers adecuadamente, la operación de la máquina vending puede evaluarse con mayor precisión y con menor riesgo de tomar decisiones basadas en valores distorsionados.
