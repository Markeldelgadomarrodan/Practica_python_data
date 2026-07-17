# DataProject EDA con Python

## Descripción

Este repositorio contiene un análisis exploratorio de datos (EDA) realizado con Python sobre campañas de marketing directo de una institución bancaria portuguesa. El objetivo es estudiar qué características de los clientes y de las llamadas se relacionan con la suscripción de un depósito bancario.

El proyecto utiliza dos fuentes de datos:

- `bank-additional.csv`: información de campañas, llamadas, variables económicas y resultado de contratación.
- `customer-details.xlsx`: información demográfica y de comportamiento de clientes, distribuida en tres hojas correspondientes a 2012, 2013 y 2014.

## Objetivo del análisis

Realizar un análisis exploratorio que incluya:

- Transformación y limpieza de datos.
- Análisis descriptivo.
- Visualización de patrones relevantes.
- Unión de datasets mediante el identificador del cliente.
- Obtención de conclusiones justificadas con datos.

## Estructura del proyecto

```text
DataProjectEDA/
├── data/
│   ├── raw/
│   │   ├── bank-additional.csv
│   │   └── customer-details.xlsx
│   └── processed/
│       ├── bank_clean.csv
│       ├── customer_details_clean.csv
│       ├── bank_customer_merged.csv
│       └── tablas resumen del análisis
├── images/
│   └── gráficos generados durante el EDA
├── notebooks/
│   └── DataProject_EDA.ipynb
├── reports/
│   └── Informe_EDA_Banco.docx
├── README.md
└── requirements.txt
```

## Tecnologías utilizadas

- Python
- Pandas
- NumPy
- Matplotlib
- OpenPyXL
- Jupyter Notebook
- Visual Studio Code

## Instalación y ejecución

1. Clonar o descargar el repositorio.
2. Crear un entorno virtual, si se desea:

```bash
python -m venv venv
```

3. Activar el entorno virtual:

```bash
# Windows
venv\Scripts\activate

# macOS / Linux
source venv/bin/activate
```

4. Instalar dependencias:

```bash
pip install -r requirements.txt
```

5. Abrir el notebook:

```bash
jupyter notebook notebooks/DataProject_EDA.ipynb
```

También puede abrirse desde Visual Studio Code con la extensión de Jupyter instalada.

## Limpieza y transformación realizada

Durante el proyecto se han realizado los siguientes pasos:

- Eliminación de columnas índice innecesarias como `Unnamed: 0`.
- Unión de las tres hojas del Excel en un único dataframe.
- Creación de la columna `customer_year` para identificar el año de cada hoja.
- Conversión de variables con coma decimal a formato numérico.
- Conversión de fechas en español a formato `datetime`.
- Normalización de variables categóricas.
- Tratamiento de valores ausentes en variables categóricas mediante la categoría `unknown`.
- Creación de variables nuevas:
  - `subscribed`
  - `call_duration_min`
  - `previously_contacted`
  - `days_since_previous_contact`
  - `age_group`
  - `income_group`
  - `total_children`
- Unión del CSV y el Excel mediante `id_`.

## Resultados principales

- El dataset principal contiene **43,000 registros**.
- El Excel de clientes contiene **43,170 registros**.
- Tras la unión, se obtienen **43,000 registros** completos para el análisis principal.
- La tasa general de conversión es del **11.27%**.
- Los clientes que contrataron el depósito tuvieron llamadas claramente más largas: media de **551.62 segundos**, frente a **220.43 segundos** en los que no contrataron.
- La campaña anterior tiene un peso relevante: cuando el resultado anterior fue `success`, la conversión supera claramente a los demás grupos.
- El contacto por teléfono móvil/celular muestra mejor conversión que el contacto telefónico tradicional.
- Las variables de ingresos y visitas web tienen una relación débil con la contratación en comparación con la duración de llamada, el resultado anterior y algunas variables de contexto económico.

## Conclusiones

El análisis muestra que la suscripción del depósito no depende únicamente del perfil demográfico del cliente. Los factores más relevantes son el comportamiento durante la campaña, especialmente la duración de la llamada, el historial de contactos previos y el resultado de campañas anteriores. También se observan diferencias importantes por profesión y edad, destacando segmentos como estudiantes, jubilados y mayores de 60 años.

Por tanto, una estrategia comercial más eficiente debería priorizar clientes con antecedentes positivos en campañas anteriores, optimizar la calidad de las llamadas y revisar los segmentos con mayor probabilidad de conversión antes de aumentar indiscriminadamente el número de contactos.

## Autor

Proyecto de análisis exploratorio de datos realizado para el módulo **Python for Data**.
