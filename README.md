# Segmentación Financiera de Clientes con K-Means y PCA

## Objetivo del Proyecto

El objetivo de este proyecto es analizar el comportamiento de compra de una base de clientes de retail para identificar segmentos de alto valor. Utilizando técnicas de Aprendizaje No Supervisado, transformamos datos transaccionales y demográficos brutos en estrategias de marketing accionables, optimizando el Retorno de Inversión (ROI) de futuras campañas publicitarias.

## Metodología Analítica

El proyecto se desarrolló en dos fases principales utilizando Python:

**1. Análisis Exploratorio y Limpieza (EDA):**

* Identificación y tratamiento de valores nulos.
* Eliminación de valores atípicos (Outliers) en la variable de ingresos utilizando el método del Rango Intercuartílico (IQR).
* *Feature Engineering:* Creación de nuevas métricas financieras consolidadas, como el Gasto Total (`Total_Spent`).

**2. Modelado de Clustering y Optimización:**

* **Estandarización:** Se aplicó Z-Score (`StandardScaler`) para asegurar que todas las variables numéricas tuvieran el mismo peso en el cálculo de distancias.
* **Feature Selection Financiero:** Durante las iteraciones del modelo, se detectó que la inclusión de variables categóricas (como estado civil y educación) generaba la "Maldición de la Dimensionalidad", aislando micro-grupos sin valor comercial. Se aplicó un enfoque **RFM (Recencia, Frecuencia, Valor Monetario)**, restringiendo el modelo estrictamente a variables continuas de impacto financiero.
* **Algoritmo:** K-Means configurado estrictamente con $k=3$ para obtener una segmentación altamente interpretable para la gerencia.
* **Reducción de Dimensionalidad:** Uso de PCA (Análisis de Componentes Principales) para comprimir el hiperespacio a 2D y visualizar las fronteras de los clústeres.

## Resultados y Estrategia de Negocio

El modelo segmentó exitosamente a la base de clientes en tres perfiles financieros distintos. A continuación, se detalla el análisis de cada clúster y la estrategia comercial recomendada:

### Clúster 2: Clientes Premium (Alto Valor)

* **Perfil:** Representan el segmento con mayor poder adquisitivo (Ingresos promedio: ~$73.8k) y el gasto más alto de la tienda (Gasto promedio: ~$1,298). Edad promedio de 58 años.
* **Estrategia Comercial:** No son sensibles al precio. La estrategia debe enfocarse en la retención a través de estatus. Se recomienda ofrecer acceso anticipado a productos exclusivos, servicios de *concierge* y programas de lealtad basados en experiencias VIP, no en descuentos.

### Clúster 0: Clientes Conservadores (Valor Medio)

* **Perfil:** Segmento estable con ingresos medios (~$49.9k) y un gasto moderado (~$445). Es el grupo de mayor edad promedio (63 años).
* **Estrategia Comercial:** Excelentes candidatos para campañas de *Cross-selling* (venta cruzada). Se recomienda recomendarles productos complementarios a sus compras habituales y enfocar la comunicación en la calidad, durabilidad y el servicio al cliente tradicional.

### Clúster 1: Cazadores de Ofertas (Sensibles al Precio)

* **Perfil:** Es el segmento más masivo, pero con los ingresos más bajos (~$33.4k) y el menor nivel de gasto (~$128). Tienen la edad promedio más joven (50 años).
* **Estrategia Comercial:** Altamente motivados por el ahorro. Este segmento debe ser el objetivo principal de las campañas de liquidación de inventario, cupones agresivos y promociones de 2x1.

## Tecnologías y Librerías Utilizadas

* **Python 3**
* **Pandas & NumPy:** Manipulación de datos y álgebra lineal.
* **Scikit-Learn:** Preprocesamiento (`StandardScaler`), Modelado (`KMeans`) y Reducción de Dimensionalidad (`PCA`).
* **Matplotlib & Seaborn:** Visualización de datos (Boxplots, Scatter Plots).

## Cómo reproducir este proyecto

1. Clonar el repositorio.
2. Instalar las dependencias (`pip install pandas numpy scikit-learn matplotlib seaborn`).
3. Explorar la libreta `sandbox.ipynb`:** Revisar la investigación preliminar, pruebas de concepto y la justificación técnica detrás de las decisiones de optimización del modelo
4. Ejecutar la libreta `1_eda_and_cleaning.ipynb` para procesar los datos brutos.
5. Ejecutar la libreta `02_clustering_model.ipynb` para entrenar el modelo y generar las visualizaciones.

---