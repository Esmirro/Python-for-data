# EDA - Campaña de Marketing Bancario

Análisis exploratorio de un dataset de campañas de marketing telefónico de un banco portugués. El objetivo es entender qué características tienen los clientes que acaban contratando un depósito a plazo.

---

## Estructura del proyecto

```
eda_banco/
├── data/
│   ├── raw/               → archivos originales sin tocar
│   └── processed/         → datos limpios y gráficos generados
├── notebooks/
│   └── eda_banco.ipynb    → notebook con todo el análisis
└── README.md
```

---

## Cómo ejecutarlo

Instalar las dependencias:
```bash
pip install pandas numpy matplotlib seaborn openpyxl jupyter
```

Abrir el notebook desde VS Code o con:
```bash
jupyter notebook notebooks/eda_banco.ipynb
```

Ejecutar las celdas en orden con `Shift + Enter`.

---

## Los datos

Se trabaja con dos fuentes:

- **`bank-additional.csv`**: 43.000 registros con información de cada llamada (edad, ocupación, duración, resultado...) y variables macroeconómicas del momento del contacto.
- **`customer-details.xlsx`**: datos demográficos de clientes divididos en tres hojas por año (2012, 2013, 2014). Se unen en un único DataFrame durante el análisis.

---

## Qué se hace en el notebook

**Limpieza**: el CSV tenía columnas numéricas guardadas como texto con coma decimal, fechas en español sin parsear y bastantes valores nulos. Se corrigió todo antes de analizar nada.

**Análisis descriptivo**: estadísticas generales, tasas de conversión por ocupación y mes, correlaciones entre variables económicas y análisis de la duración de las llamadas.

**Visualizaciones**: 8 gráficos exportados en `data/processed/` — distribución de la variable objetivo, edad, ocupación, duración de llamadas, correlaciones, mes de contacto, ingresos y visitas web.

---

## Conclusiones principales

La tasa de conversión global es del **~11%**, lo que significa que el dataset está bastante desbalanceado.

Lo que más se relaciona con que un cliente suscriba:
- **Duración de la llamada**: los que suscriben hablan casi el doble. Tiene sentido pero no sirve como predictor porque solo se sabe al final de la llamada.
- **Resultado de campañas anteriores**: si ya contrató algo antes, es mucho más probable que vuelva a hacerlo.
- **Mes de contacto**: marzo, septiembre y octubre funcionan mejor. Mayo tiene muchas llamadas pero pocos resultados.
- **Ocupación**: estudiantes y jubilados convierten más que la media.
- **Número de intentos**: llamar más de 3 veces al mismo cliente casi nunca funciona.

Las variables macroeconómicas (`euribor3m`, `emp.var.rate`, `nr.employed`) están tan correlacionadas entre sí que prácticamente miden lo mismo. En un modelo futuro habría que quedarse solo con una.

---

## Herramientas

Python 3 · Pandas · Matplotlib · Seaborn · VS Code
