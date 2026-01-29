# 📱 ConnectaTel - Análisis de Telecomunicaciones

<div align="center">
  
![ConnectaTel Logo](https://img.shields.io/badge/ConnectaTel-Telecom_Analysis-blue)
![Python](https://img.shields.io/badge/Python-3.9%2B-green)
![Pandas](https://img.shields.io/badge/Pandas-Data_Analysis-orange)
![Status](https://img.shields.io/badge/Status-Completed-success)

**Análisis de comportamiento de clientes y optimización de planes de telecomunicaciones**

</div>

## 🎯 **Objetivo del Proyecto**

Analizar el comportamiento de uso de los clientes de ConnectaTel para:
- Identificar segmentos de clientes por edad y nivel de uso
- Detectar patrones de uso extremo y oportunidades de optimización
- Proponer mejoras en los planes actuales basadas en datos reales
- Crear estrategias de segmentación para marketing y retención

## 📊 **Datasets Utilizados**

El proyecto utiliza tres fuentes de datos principales:

### 1. **plans.csv** (2 registros, 8 columnas)
Catálogo de planes con características y precios:
- `plan_name`: Nombre del plan (Basico, Premium)
- `messages_included`: Mensajes incluidos mensuales
- `gb_per_month`: GB de datos incluidos
- `minutes_included`: Minutos de llamada incluidos
- `usd_monthly_pay`: Pago mensual en USD
- `usd_per_gb`: Costo por GB extra
- `usd_per_message`: Costo por mensaje extra
- `usd_per_minute`: Costo por minuto extra

### 2. **users_latam.csv** (4,000 registros, 8 columnas)
Información de clientes en México y Colombia:
- `user_id`: Identificador único del usuario
- `first_name`, `last_name`: Nombre del cliente
- `age`: Edad del cliente
- `city`: Ciudad de residencia
- `reg_date`: Fecha de registro
- `plan`: Plan contratado (Basico, Premium)
- `churn_date`: Fecha de baja (si aplica)

### 3. **usage.csv** (40,000 registros, 6 columnas)
Registros de uso real de los servicios:
- `id`: Identificador del registro
- `user_id`: Usuario asociado
- `type`: Tipo de uso (call, text)
- `date`: Fecha del uso
- `duration`: Duración de llamada (minutos)
- `length`: Longitud de mensaje (caracteres)

## 🔄 **Etapas del Análisis**

### **Paso 1: Carga y Exploración**
- Carga de los tres datasets
- Exploración inicial de estructura y tipos de datos
- Identificación de problemas básicos de calidad

### **Paso 2: Identificación de Problemas de Calidad**
- Detección de valores nulos y cálculo de porcentajes
- Identificación de sentinels (-999, "?") en datos numéricos y categóricos
- Validación de fechas y años fuera de rango
- Confirmación de estructura de datos (MAR en usage)

### **Paso 3: Limpieza Básica de Datos**
- Corrección de sentinels en edad (-999 → mediana)
- Imputación de valores faltantes en ciudad
- Eliminación de fechas imposibles (año 2026)
- Tratamiento de anomalías en registros de uso

### **Paso 4: Estadísticas de Uso por Usuario**
- Agregación de métricas de uso por usuario
- Cálculo de: cantidad de mensajes, llamadas y minutos totales
- Combinación con datos demográficos de usuarios
- Análisis estadístico descriptivo

### **Paso 5: Visualización y Detección de Outliers**
- Histogramas por plan para variables clave
- Boxplots para detección visual de outliers
- Cálculo de límites IQR para outliers matemáticos
- Decisiones sobre tratamiento de valores extremos

### **Paso 6: Segmentación de Clientes**
- Segmentación por nivel de uso (Bajo, Medio, Alto)
- Segmentación por edad (Joven, Adulto, Adulto Mayor)
- Visualización de distribuciones segmentadas
- Análisis cruzado de segmentos

### **Paso 7: Insight Ejecutivo**
- Traducción de hallazgos técnicos a lenguaje de negocio
- Identificación de segmentos de valor
- Recomendaciones estratégicas para optimización de planes
- Propuestas de nuevas ofertas segmentadas

## 🚀 **Cómo Ejecutar el Proyecto**

### **Opción 1: Google Colab (Recomendado)**
1. Abre Google Colab: [colab.research.google.com](https://colab.research.google.com)
2. Sube el notebook `ConnectaTel_Analysis.ipynb`
3. Sube los datasets en la carpeta `/datasets/`
4. Ejecuta todas las celdas en orden (Runtime → Run all)

### **Opción 2: Entorno Local**
```bash
# 1. Clona o descarga el proyecto
git clone [repo-url]

# 2. Crea entorno virtual
python -m venv venv

# 3. Activa entorno virtual
# Windows:
venv\Scripts\activate
# Mac/Linux:
source venv/bin/activate

# 4. Instala dependencias
pip install pandas numpy matplotlib seaborn jupyter

# 5. Ejecuta Jupyter
jupyter notebook