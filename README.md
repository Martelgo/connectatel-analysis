# Análisis de uso de clientes · ConnectaTel (México y Colombia)

Proyecto 6 del bootcamp de Análisis de Datos de TripleTen (Sprint 7: análisis estadístico para detectar patrones y outliers).

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Martelgo/connectatel-analysis/blob/main/notebooks/connectatel_analysis.ipynb)

## 🎯 Objetivo

ConnectaTel es una empresa de telecomunicaciones con operaciones en México y Colombia. Quiere entender cómo usan realmente sus clientes las llamadas y los mensajes, detectar comportamientos atípicos y encontrar segmentos con necesidades distintas, para mejorar su oferta de planes.

Preguntas de negocio:

- ¿Qué segmentos de clientes usan más o menos llamadas y mensajes?
- ¿Qué usuarios presentan valores atípicos (posibles errores, fraude o comportamientos inusuales)?
- ¿Cómo varía el uso según la edad y el plan contratado?
- ¿Qué patrones ayudan a diseñar mejores planes?

## 📂 Datos

| Archivo | Contenido | Tamaño |
|---|---|---|
| `plans.csv` | Catálogo de planes: precio mensual, minutos, mensajes y GB incluidos, costo por excedente | 2 planes |
| `users_latam.csv` | Clientes: edad, ciudad, fecha de registro, plan y fecha de cancelación | 4,000 clientes |
| `usage.csv` | Eventos de uso: llamadas (duración) y mensajes (longitud), de enero a junio de 2024 | 40,000 eventos |

## 🔄 Etapas del análisis

1. **Carga y exploración** de la estructura de los tres datasets.
2. **Calidad de datos:** nulos, sentinels (`-999`, `"?"`, llamadas de 120 min, mensajes de 1,490 caracteres) y fechas imposibles (2026).
3. **Limpieza:** edad imputada con la mediana, sentinels convertidos a nulos, fechas futuras marcadas como nulas y verificación MAR de los nulos estructurales.
4. **Perfil por cliente:** total de mensajes, llamadas y minutos por usuario.
5. **Distribuciones y outliers:** histogramas por plan, boxplots y método IQR.
6. **Segmentación:** por nivel de uso y por edad, con cruces por plan, país, consumo del plan, ingreso y cancelación.
7. **Insight ejecutivo** con recomendaciones comerciales.

## 💡 Hallazgos principales

- El uso **no cambia por edad, plan ni país**: lo que distingue a los clientes es su propio nivel de uso (74% uso medio, 19% bajo, 7% alto).
- Los planes están **sobrados**: el cliente promedio usa ~4 minutos y ~1 mensaje al mes, menos del 4% de lo incluido en el plan Básico y menos del 1% del Premium.
- **Premium** es el 35% de los clientes activos y aporta el **52.9% del ingreso** por suscripción, con el mismo consumo que Básico.
- Los outliers de uso son clientes reales y moderados, sin señales de fraude; los valores imposibles eran sentinels de captura.
- La cancelación (~12%) es pareja entre segmentos.

## ▶️ Cómo abrirlo y reproducirlo

**Opción 1 · Google Colab**

1. Haz clic en el botón **Open in Colab** de arriba.
2. En la celda `# cargar archivos`, cambia la ruta `/datasets/` por la carpeta de datos de este repositorio:
   `https://raw.githubusercontent.com/Martelgo/connectatel-analysis/main/data/`
3. Menú **Entorno de ejecución → Ejecutar todas**.

**Opción 2 · Jupyter en tu computadora**

1. Descarga o clona este repositorio.
2. En la celda `# cargar archivos`, cambia `/datasets/` por `../data/`.
3. Ejecuta las celdas en orden.

Librerías: `pandas`, `numpy`, `matplotlib` y `seaborn`.

## 🗂️ Estructura del repositorio

```
connectatel-analysis/
├── README.md
├── notebooks/
│   └── connectatel_analysis.ipynb   ← análisis completo
└── data/
    ├── plans.csv
    ├── users_latam.csv
    └── usage.csv
```

## 👤 Autor

José Martín Quijano · Análisis de Datos (TripleTen)
