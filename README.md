📱 #Análisis ConnectaTel
*Segmentación y Comportamiento de Usuarios por Tipo de Plan*

📌 ##Descripción del Proyecto
Análisis exploratorio de datos (EDA) sobre la base de usuarios de ConnectaTel, una empresa de telecomunicaciones con dos planes disponibles: Básico y Premium. El objetivo es identificar patrones de uso, segmentar a los clientes por edad y nivel de actividad, y traducir los hallazgos en recomendaciones comerciales accionables.

🗂️ ##Estructura del Proyecto
analisis-connectatel/
│
├── data/
│   └── user_profile.csv          # Dataset original
│
├── notebooks/
│   └── connectatel_analysis.ipynb  # Notebook principal con el análisis completo
│
├── outputs/
│   └── visualizaciones/           # Gráficos generados durante el análisis
│
└── README.md

🧰 Tecnologías Utilizadas
HerramientaUsoPython 3.xLenguaje principalPandasManipulación y limpieza de datosMatplotlibVisualización de distribuciones y boxplotsNumPyCálculos estadísticos y segmentación

🔄 Proceso de Análisis
1. Carga y Exploración Inicial

Revisión de tipos de datos, valores nulos y duplicados
El dataset no presentó nulos ni duplicados relevantes, indicando buena calidad base

2. Estadísticas Descriptivas

Análisis de media, mediana, desviación estándar y rangos
cant_minutos_llamada mostró sesgo positivo (media > mediana), indicando una minoría de usuarios con llamadas muy extensas

3. Visualización Diagnóstica

Histogramas con KDE por tipo de plan para las 4 variables numéricas
Boxplots por plan para identificación visual de outliers

4. Identificación de Outliers — Método IQR
VariableLímite SuperiorOutliersage—❌ No presentacant_mensajes11.50✅ Hasta 17cant_llamadas10.50✅ Hasta 15cant_minutos_llamada61.86✅ Hasta ~160 min
5. Tratamiento de Outliers
Se aplicó winsorización en las tres variables con outliers. Los valores extremos representan usuarios reales con comportamiento intensivo —no errores de captura—, por lo que se optó por preservar todos los registros ajustando únicamente los valores fuera del límite superior.

Se descartó la eliminación de filas para evitar subrepresentar el segmento de usuarios más activos del dataset.

6. Segmentación de Usuarios
Por nivel de uso (basado en cant_llamadas y cant_mensajes):
SegmentoCriterio% de UsuariosBajo UsoLlamadas < 5 y Mensajes < 5~19%Uso MedioLlamadas < 10 y Mensajes < 10~74%Alto UsoResto de casos~7%
Por grupo de edad:
SegmentoRango% de UsuariosJoven< 30 años~19%Adulto30–60 años~50%Adulto Mayor> 60 años~30%

💡 Hallazgos Principales

El 74% de los usuarios son de Uso Medio, con un comportamiento consistente y predecible en ambos planes.
El segmento de Alto Uso (7%) concentra los outliers más extremos en llamadas y minutos, con consumo hasta 3x por encima de la mediana — probablemente subatendido por los planes actuales.
El segmento Adulto domina la base (~50%), seguido de Adulto Mayor (~30%), indicando una base de usuarios madura y potencialmente fiel.
Ambos planes muestran distribuciones de edad casi idénticas, lo que sugiere que la elección de plan no está siendo guiada por la edad sino por otros factores.


📋 Recomendaciones para ConnectaTel

Plan "Power User" — Crear una nueva oferta con minutos y mensajes ilimitados, orientada al segmento de Alto Uso que hoy supera consistentemente los límites de los planes existentes.
Campaña de Upselling — Dirigir esfuerzos comerciales al segmento de Uso Medio en plan Básico (el mayor volumen del dataset) con beneficios incrementales que justifiquen la migración a Premium.
Oferta Senior — Desarrollar un plan para Adultos Mayores con minutos incluidos e interfaz simplificada, aprovechando su peso en la base (~30%) y su potencial de fidelización.
Monitoreo del segmento Joven — Analizar si el bajo uso en usuarios jóvenes representa abandono temprano o un nicho a activar con planes de entrada más atractivos y flexibles.


👤 Autor
Santiago Álvarez
Data Analyst en formación | TripleTen Bootcamp
