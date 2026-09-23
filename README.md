# Manejo de Datos con Python

## Inteligencia Artificial Aplicada --- Semana 05

Este repositorio contiene el material práctico de la **Semana 05** del
curso **Inteligencia Artificial Aplicada**, orientado al manejo de datos
con Python mediante la librería **pandas**.

La práctica utiliza el dataset `riesgo_crediticio.xlsx`, que contiene
información de clientes evaluados para el otorgamiento de un crédito. El
objetivo es aprender a cargar, explorar, seleccionar, filtrar y resumir
datos mediante un `DataFrame`.

## Objetivos

Al finalizar la práctica, el estudiante podrá:

-   Importar librerías para el manejo y análisis de datos.
-   Cargar archivos Excel en un DataFrame de pandas.
-   Explorar la estructura y contenido de un dataset.
-   Seleccionar filas y columnas.
-   Aplicar filtros mediante operadores de comparación y operadores
    lógicos.
-   Crear tablas de frecuencias y tablas resumen.
-   Agrupar datos con `groupby()`.
-   Construir tablas cruzadas con `pd.crosstab()`.

## Dataset

El archivo `riesgo_crediticio.xlsx` contiene información relacionada con
la evaluación crediticia de clientes.

Entre sus variables se encuentran:

-   `cliente_id`
-   `edad`
-   `ingreso_mensual`
-   `antiguedad_laboral_anios`
-   `deuda_mensual`
-   `atrasos_ultimos_12_meses`
-   `monto_solicitado`
-   `plazo_meses`
-   `riesgo`

El análisis busca explorar la relación entre las características
financieras de los clientes y su nivel de riesgo crediticio.

## Contenido de la práctica

### 1. Importación de librerías y carga del dataset

``` python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

df = pd.read_excel("riesgo_crediticio.xlsx")
```

### 2. Exploración inicial

Se utilizan comandos básicos para conocer la estructura del DataFrame:

``` python
df.head(10)
df.tail(10)
df.sample(10)
df.shape
df.columns
df.dtypes
df.info()
df.nunique()
```

También se revisan los valores únicos de variables específicas:

``` python
df["riesgo"].unique()
df["plazo_meses"].unique()
```

### 3. Selección de filas y columnas

Ejemplos:

``` python
df[["cliente_id", "riesgo"]].head(3)

df[10:15][["cliente_id", "edad"]]

df[0:20:2][["cliente_id", "ingreso_mensual", "riesgo"]]

df[20:31][["cliente_id", "edad", "monto_solicitado"]]

df[["cliente_id", "monto_solicitado"]].tail(5)
```

### 4. Filtrado con condiciones

Se aplican operadores de comparación y operadores lógicos para
seleccionar registros que cumplen determinadas condiciones.

``` python
df[df["antiguedad_laboral_anios"] == 20]

df[df["edad"] > 62]

df[(df["atrasos_ultimos_12_meses"] == 2) |
   (df["atrasos_ultimos_12_meses"] == 4)]

df[(df["riesgo"] == "Alto") &
   (df["atrasos_ultimos_12_meses"] > 2)]

df[df["ingreso_mensual"] < 1500]

df[df["monto_solicitado"] > 19000]
```

### 5. Tablas de frecuencia

``` python
df["riesgo"].value_counts()

df["plazo_meses"].value_counts()
```

### 6. Tablas resumen

Promedios agrupados por nivel de riesgo:

``` python
df.groupby("riesgo")[
    ["ingreso_mensual", "monto_solicitado", "deuda_mensual"]
].mean()
```

Valores máximos agrupados por riesgo:

``` python
df.groupby("riesgo")[
    ["monto_solicitado", "ingreso_mensual"]
].max()
```

### 7. Tablas cruzadas

``` python
pd.crosstab(df["riesgo"], df["plazo_meses"])

pd.crosstab(df["riesgo"], df["atrasos_ultimos_12_meses"])
```

## Archivos del repositorio

``` text
.
├── Cuaderno Manejo de Datos con Pyhton.ipynb
├── riesgo_crediticio.xlsx
├── Comandos_Manejo_de_Datos_con_Python.pdf
└── README.md
```

-   **Cuaderno Manejo de Datos con Pyhton.ipynb**: notebook con el
    desarrollo de los ejercicios.
-   **riesgo_crediticio.xlsx**: dataset utilizado en la práctica.
-   **Comandos_Manejo_de_Datos_con_Python.pdf**: material de apoyo con
    los principales comandos.
-   **README.md**: descripción del repositorio.

## Herramientas utilizadas

-   Python
-   Jupyter Notebook
-   pandas
-   matplotlib
-   seaborn

## Relación con los ODS

El dataset se vincula principalmente con el **ODS 8: Trabajo decente y
crecimiento económico**, debido a su relación con el acceso al crédito y
los servicios financieros.

También puede relacionarse con el **ODS 10: Reducción de las
desigualdades**, considerando que el análisis responsable de datos puede
contribuir a evaluaciones crediticias más transparentes y menos
subjetivas.

## Actividad

La guía propone ejercicios de:

1.  Importación de librerías y carga de datos.
2.  Exploración inicial del DataFrame.
3.  Selección de filas y columnas.
4.  Filtrado mediante condiciones.
5.  Creación e interpretación de tablas de frecuencia.
6.  Creación de tablas resumen.
7.  Elaboración de tablas cruzadas.

------------------------------------------------------------------------

**Facultad de Ingeniería**\
**Asignatura:** Inteligencia Artificial Aplicada\
**Periodo académico:** 2026-2\
**Semana:** 05
