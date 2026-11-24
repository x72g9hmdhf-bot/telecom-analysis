# 📱 Análisis de Clientes — ConnectaTel

Proyecto del Sprint 7 del Bootcamp de Análisis de Datos de TripleTen.

## 🎯 Objetivo

Evaluar el comportamiento de los clientes de **ConnectaTel**, una empresa de telecomunicaciones en Latinoamérica, con datos registrados hasta 2024. El análisis busca:

- Limpiar y validar la calidad de los datos.
- Construir un perfil estadístico de uso por cliente.
- Detectar comportamientos atípicos (outliers).
- Segmentar a los clientes por edad y nivel de uso.
- Proponer mejoras a la oferta de planes.

## 📂 Datasets

| Archivo | Filas | Descripción |
|---|---|---|
| `plans.csv` | 2 | Planes actuales (Básico y Premium): precio mensual, minutos, mensajes y GB incluidos, y costo por excedente. |
| `users_latam.csv` | 4,000 | Clientes: edad, ciudad, fecha de registro, plan y fecha de cancelación (churn). |
| `usage.csv` | 40,000 | Eventos de uso en 2024: llamadas (duración) y mensajes (longitud). |

## 🧩 Etapas del análisis

1. **Carga y exploración:** estructura, tipos de datos y vista general de los tres datasets.
2. **Calidad de datos:** detección de nulos, valores centinela (`-999` en edad, `"?"` en ciudad) y fechas fuera de rango (registros con año 2026).
3. **Limpieza:**
   - Edad `-999` → mediana (47 años).
   - Ciudad `"?"` → `pd.NA`.
   - Fechas futuras → `NaT`.
   - Nulos en `duration` y `length` se conservan: son MAR (dependen del tipo de evento).
4. **Métricas por usuario:** total de mensajes, llamadas y minutos por cliente, unidos a la tabla de usuarios (`user_profile`).
5. **Distribuciones y outliers:** histogramas por plan, boxplots y límites con el método IQR.
6. **Segmentación:**
   - Por uso: Bajo, Medio y Alto.
   - Por edad: Joven (<30), Adulto (30–59) y Adulto mayor (60+).
7. **Insight ejecutivo:** conclusiones y recomendaciones para stakeholders.

## 📊 Hallazgos principales

- **Calidad de datos:** 14.1% de clientes sin ciudad, 1.4% con edad inválida y 1% con fecha de registro imposible.
- **Segmentos de uso:** 73.6% uso medio, 19.4% bajo uso y 7.0% alto uso.
- **Segmentos de edad:** 50.4% adultos, 30.6% adultos mayores y 19.0% jóvenes.
- **El consumo no varía por edad ni por plan:** los clientes Premium (35%) usan lo mismo que los Básico, aunque pagan más del doble.
- **El consumo real está muy por debajo de lo que incluyen los planes**, incluso en el Básico.
- **11.7% de los clientes cancelaron** (466 registros con `churn_date`).

## 💡 Recomendaciones

- Redefinir el valor del plan Premium con beneficios que sí se usen (datos, apps, roaming).
- Crear un plan de entrada más económico para clientes de bajo uso.
- Lanzar una campaña de upgrade dirigida a clientes de alto uso en plan Básico.
- Segmentar la oferta por uso real, no por edad.
- Analizar el churn por plan y nivel de uso.
- Mejorar la captura de datos (ciudad obligatoria, validación de edad y fechas, registro de consumo de GB).

## 🛠️ Herramientas

- Python 3
- pandas, NumPy
- matplotlib, seaborn
- Jupyter Notebook / Google Colab



## 🔁 Reproducibilidad

- Ejecuta el notebook **de arriba hacia abajo** (*Restart & Run All*). Las celdas de limpieza modifican los DataFrames en memoria, así que correrlas fuera de orden puede dar resultados distintos.
- Los datasets no incluyen información de consumo de datos móviles (GB), por lo que el análisis de uso se limita a llamadas y mensajes.

## 📁 Estructura del repositorio

```
├── S7_Version-Estudiante-Project-ConnectaTel.ipynb
└── README.md
```

## 👤 Autor

Francisco Javier Muñiz Hernández
