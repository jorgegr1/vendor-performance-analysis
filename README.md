# Análisis del Rendimiento de Proveedores

Proyecto de análisis de datos end-to-end centrado en la rentabilidad de proveedores, la concentración de compras, la rotación de inventario, la estrategia de precios y el rendimiento de ventas.

El proyecto combina **Python, SQL, análisis exploratorio de datos, contraste estadístico y Power BI** para identificar oportunidades de mejora en la rentabilidad y en la eficiencia operativa.

## Objetivos del proyecto

El análisis busca responder a las siguientes preguntas de negocio:

- ¿Qué marcas presentan ventas bajas pero márgenes de beneficio altos y podrían beneficiarse de ajustes promocionales o de precios?
- ¿Qué proveedores y marcas presentan el mejor rendimiento en ventas?
- ¿Qué proveedores contribuyen en mayor medida al volumen total de compras?
- ¿Qué grado de dependencia existe respecto a los principales proveedores?
- ¿Comprar en grandes cantidades reduce el precio unitario?
- ¿Qué proveedores presentan una baja rotación de inventario y posible exceso de stock?
- ¿Cuánto capital está inmovilizado en inventario no vendido?
- ¿Existen diferencias significativas en los márgenes de beneficio entre proveedores de alto y bajo rendimiento?

## Estructura del repositorio

```text
vendor-performance-analysis/
│
├── README.md
├── requirements.txt
├── .gitignore
│
├── data/
│   └── Archivos CSV
│
├── img/
│   └── Gráficos y figuras utilizados en el informe final
│
├── notebooks/
│   ├── exploratory_data_analysis.ipynb
│   └── vendor_performance_analysis.ipynb
│
├── output/
│   ├── Informe_Rendimiento_Proveedores.pdf
│   └── vendor_sales_summary.csv
│
├── powerbi/
│   └── vendor_performance_dashboard.pbix
│
└── src/
    ├── ingestion_db.py
    ├── get_vendor_summary.py
    └── generate_report.py
```

## Flujo de trabajo

1. Los archivos CSV se cargan en una base de datos relacional.
2. La información de proveedores, compras, ventas, precios y costes de transporte se combina en una tabla agregada.
3. Se limpian inconsistencias y se filtran registros no válidos.
4. Se realiza un análisis exploratorio sobre variables numéricas y categóricas.
5. Se calculan distintos KPI y métricas de negocio, entre ellos:
   - `GrossProfit`
   - `ProfitMargin`
   - `StockTurnover`
   - `SalesToPurchaseRatio`
6. Se analizan proveedores y marcas desde la perspectiva de rentabilidad, compras, ventas e inventario.
7. Se aplican técnicas de inferencia estadística para comparar grupos de proveedores.
8. Los resultados se presentan mediante Power BI y un informe PDF generado automáticamente.

## Principales resultados

Entre los principales hallazgos obtenidos durante el análisis destacan:

- Se identificaron **198 marcas** con ventas relativamente bajas y márgenes de beneficio elevados, lo que las convierte en candidatas a acciones promocionales o ajustes de precios.
- Los **10 principales proveedores concentran aproximadamente el 65,69 % del total de compras**, lo que evidencia una elevada concentración del aprovisionamiento.
- Los pedidos de gran volumen alcanzan un precio unitario medio de aproximadamente **10,78 $**, alrededor de un **72 % inferior** al de los pedidos pequeños dentro de los datos analizados.
- Se identificaron aproximadamente **2,71 millones de dólares de capital inmovilizado** en inventario no vendido.
- Los proveedores con menor rendimiento en ventas presentan, en promedio, márgenes de beneficio superiores a los proveedores con mayor volumen de ventas.
- Una prueba t de Welch para dos muestras independientes mostró una diferencia estadísticamente significativa entre los márgenes medios de ambos grupos.

## Tecnologías utilizadas

- Python
- Pandas
- NumPy
- SQL
- Matplotlib
- Seaborn
- SciPy
- Power BI
- ReportLab
- Jupyter Notebook

## Instalación

Clona el repositorio:

```bash
git clone https://github.com/jorgegr1/vendor-performance-analysis.git
cd vendor-performance-analysis
```

Crea y activa un entorno virtual.

### Windows

```bash
python -m venv .venv
.venv\Scripts\activate
```

### macOS / Linux

```bash
python3 -m venv .venv
source .venv/bin/activate
```

Instala las dependencias:

```bash
pip install -r requirements.txt
```

## Uso

### 1. Cargar los CSV en la base de datos

```bash
python src/ingestion_db.py
```

### 2. Generar la tabla resumen de proveedores

```bash
python src/get_vendor_summary.py
```

### 3. Ejecutar los notebooks

Abre los notebooks de la carpeta `notebooks/` con Jupyter Notebook o Visual Studio Code.

## Dashboard de Power BI

El dashboard de Power BI se encuentra en:

```text
powerbi/vendor_performance_dashboard.pbix
```

Permite explorar de forma interactiva el rendimiento de proveedores, la rentabilidad, la concentración de compras y diferentes métricas de inventario.

## Informe final

El informe completo del análisis se encuentra en:

```text
output/Informe_Rendimiento_Proveedores.pdf
```

## Consideraciones

- Algunos datasets, al ser de gran tamaño. superan los límites de GitHub. Por ello, no serán incluidos.
- No deben subirse credenciales, contraseñas, claves API ni archivos `.env`.
- El orden de ejecución puede requerir pequeños ajustes dependiendo de los nombres finales utilizados en `src/` y `notebooks/`.

## Autor

Jorge Gamonal Rodríguez

Estudiante de Ciencia e Ingeniería de datos en Uniovi
