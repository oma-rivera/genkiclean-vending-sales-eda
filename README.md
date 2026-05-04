<img width="1384" height="670" alt="Captura de pantalla 2026-05-04 a la(s) 1 48 13 p m" src="https://github.com/user-attachments/assets/fae0d28d-837f-45c9-a6f3-f94bdd04e0c8" />


# GenkiClean Vending Sales EDA

## Descripción del proyecto

Este proyecto presenta un Análisis Exploratorio de Datos, o EDA, aplicado a las ventas diarias de una máquina vending de productos de limpieza GenkiClean ubicada en la Ciudad de México.

El objetivo fue analizar el comportamiento de ventas, validar la calidad de los datos, identificar outliers, clasificarlos con lógica de negocio y evaluar cómo cambia la interpretación del negocio antes y después del tratamiento de datos.

El análisis fue desarrollado como proyecto de portafolio utilizando Python, Pandas, NumPy, Matplotlib, Seaborn y Jupyter Notebook.

---

## Contexto de negocio

GenkiClean opera máquinas vending que venden productos de limpieza por litro.

Para este análisis, la máquina tiene las siguientes características:

- Ubicación: CDMX
- Método de pago: efectivo
- Venta: por litro completo
- Capacidad de tanque: 100 litros por producto
- Productos disponibles: 7
- Objetivo de venta mensual: aproximadamente $25,000 MXN

Los productos analizados fueron:

1. Desengrasante
2. Detergente líquido para ropa
3. Detergente líquido para ropa blanca
4. Multiusos
5. Suavizante
6. Lavatrastes
7. Detergente líquido ropa oscura

---

## Problema de negocio

El dataset contenía valores válidos, valores extremos y errores intencionales.

La pregunta principal fue:

> ¿Cómo cambia la interpretación del desempeño de ventas de una máquina vending después de limpiar datos, validar reglas de negocio y tratar outliers?

El análisis siguió este ciclo:

1. Visión general
2. Estadísticas descriptivas
3. Visualización diagnóstica
4. Identificación formal de outliers
5. Clasificación y tratamiento de outliers: Drop, Keep o Cap
6. Estadísticas post-tratamiento
7. Conclusión ejecutiva

---

## Dataset

El dataset original contiene:

- 376 registros
- 46 columnas originales
- 365 fechas válidas
- 1 fecha inválida
- 11 registros marcados con problemas de calidad
- 0 registros duplicados

Después de crear variables auxiliares para validación y tratamiento, el notebook trabaja con 57 columnas.

---

## Variables principales

Algunas de las variables utilizadas en el análisis fueron:

- `date`
- `year_month`
- `machine_id`
- `machine_model`
- `city`
- `payment_method`
- `total_liters_sold`
- `total_gross_sales_mxn`
- `cash_received_mxn`
- `change_given_mxn`
- `estimated_tickets`
- `avg_ticket_mxn`
- `stockout_flag`
- `stockout_minutes_total`
- Litros vendidos por producto
- Ingresos por producto
- Inventario final por producto

---

## Metodología

### 1. Carga de datos

El archivo fue cargado desde Google Sheets usando una URL de exportación CSV y `pd.read_csv()`.

### 2. Validación inicial

Se revisaron:

- Dimensiones del dataset
- Tipos de datos
- Valores nulos
- Registros duplicados
- Fechas inválidas
- Reglas de negocio
- Consistencia de efectivo
- Consistencia entre ingresos reportados y ventas calculadas por producto

### 3. Estadísticas descriptivas

Se calcularon métricas para:

- Litros vendidos
- Venta bruta diaria
- Efectivo recibido
- Cambio entregado
- Tickets estimados
- Ticket promedio
- Minutos de stockout
- Temperatura en CDMX

### 4. Visualización diagnóstica

Se utilizaron visualizaciones con Seaborn para revisar:

- Distribución de ventas diarias
- Boxplot de ventas
- Ventas mensuales contra objetivo
- Relación entre litros vendidos y venta bruta
- Venta promedio por día de la semana

### 5. Identificación formal de outliers

Los outliers fueron detectados con el método IQR:

- Límite inferior = Q1 - 1.5 × IQR
- Límite superior = Q3 + 1.5 × IQR

### 6. Tratamiento de outliers

Los outliers fueron clasificados con lógica de negocio:

| Decisión | Criterio |
|---|---|
| Drop | Valores imposibles o inconsistentes |
| Keep | Valores extremos pero válidos |
| Cap | Valores extremos posibles tratados mediante winsorización |

---

## Visualizaciones clave

### Distribución de ventas diarias

![Distribución de ventas diarias](images/sales_distribution.png)

### Boxplot de ventas diarias

![Boxplot de ventas diarias](images/sales_boxplot.png)

### Ventas mensuales vs objetivo

![Ventas mensuales vs objetivo](images/monthly_sales_vs_target.png)

### Relación entre litros vendidos y venta bruta

![Relación litros vs venta](images/liters_vs_sales.png)

### Boxplot antes vs después del tratamiento

![Boxplot antes vs después](images/boxplot_before_after.png)

### Ventas mensuales tratadas vs objetivo

![Ventas mensuales tratadas vs objetivo](images/monthly_sales_treated_vs_target.png)

---

## Hallazgos principales

### 1. El dataset original estaba afectado por valores extremos

Antes del tratamiento, la venta diaria promedio era de $907.39 MXN, pero existían registros extremos cercanos a $10,000 y $20,000 MXN.

Estos valores inflaban el promedio y distorsionaban la interpretación del desempeño mensual.

### 2. La mediana era más estable que la media

La mediana inicial de venta diaria fue de $815.00 MXN, mientras que la media era de $907.39 MXN.

Esta diferencia indicaba sesgo a la derecha provocado por valores atípicos.

### 3. Las visualizaciones confirmaron la presencia de outliers

El histograma mostró una concentración de ventas en rangos normales y una cola larga hacia la derecha.

El boxplot confirmó valores extremos relevantes que requerían análisis formal.

### 4. La lógica de negocio fue necesaria para clasificar outliers

No todos los outliers fueron eliminados automáticamente.

El análisis separó valores imposibles, valores extremos válidos y valores posibles pero demasiado influyentes.

### 5. El dataset limpio quedó más estable

Después del tratamiento, el dataset quedó con 369 registros.

La venta diaria promedio tratada fue de $831.60 MXN y la mediana fue de $815.00 MXN.

La cercanía entre media y mediana indica que la distribución quedó más estable después de limpiar y tratar los datos.

### 6. El máximo diario se redujo significativamente

La venta máxima pasó de $20,000.00 MXN antes del tratamiento a $1,965.00 MXN después del tratamiento.

Esto representa una reducción del 90.18% en el valor máximo observado.

---

## Resultados finales

| Métrica | Resultado |
|---|---:|
| Registros originales | 376 |
| Registros después del tratamiento | 369 |
| Venta total original | $341,179 MXN |
| Venta total tratada | $306,860 MXN |
| Venta diaria promedio original | $907.39 MXN |
| Venta diaria promedio tratada | $831.60 MXN |
| Mediana diaria tratada | $815.00 MXN |
| Venta máxima original | $20,000.00 MXN |
| Venta máxima tratada | $1,965.00 MXN |
| Litros totales tratados | 13,869 L |
| Litros promedio por día | 37.59 L |
| Ticket promedio tratado | $41.37 MXN |
| Venta mensual promedio tratada | $25,571.67 MXN |

---

## Recomendaciones de negocio

1. Validar automáticamente que la venta bruta coincida con los litros vendidos por producto.
2. Revisar la consistencia entre venta bruta, efectivo recibido y cambio entregado.
3. Aplicar detección de outliers antes de evaluar desempeño mensual.
4. No eliminar outliers automáticamente; primero deben clasificarse con lógica de negocio.
5. Monitorear venta diaria, litros vendidos, tickets estimados y ticket promedio como KPIs operativos.
6. Evaluar el desempeño mensual contra el objetivo de $25,000 MXN usando datos limpios.

---

## Herramientas utilizadas

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Jupyter Notebook
- Google Sheets
- GitHub

---

## Estructura del repositorio

```text
genkiclean-vending-sales-eda/
│
├── README.md
│
├── notebooks/
│   └── vending_sales_analysis.ipynb
│
├── data/
│   ├── raw/
│   │   └── genkiclean_vending_daily_sales_raw.csv
│   └── processed/
│       └── genkiclean_vending_daily_sales_clean.csv
│
├── images/
│   ├── sales_distribution.png
│   ├── sales_boxplot.png
│   ├── monthly_sales_vs_target.png
│   ├── liters_vs_sales.png
│   ├── boxplot_before_after.png
│   └── monthly_sales_treated_vs_target.png
│
└── reports/
    └── executive_summary.md
