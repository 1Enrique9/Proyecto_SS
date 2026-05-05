# Proyecto_SS

**Finanzas interactivo (HTML):** https://1enrique9.github.io/Proyecto_SS/finanzas_interactivo.html

Repositorio de notebooks y material interactivo de **finanzas computacionales** en Python. El proyecto combina:

- valuación de opciones americanas con **árbol binomial** y **Longstaff-Schwartz**;
- simulación Monte Carlo y Black-Scholes;
- análisis de bonos cuponados;
- limpieza de datos financieros con valores faltantes;
- modelación de series de tiempo financieras;
- cálculo de **VaR** y **CVaR** con varios métodos.

---

## Estructura del repositorio

- **`Notebooks/`**: notebooks base del proyecto individual de opciones americanas. Incluye la versión original y una versión corregida/refactorizada.
- **`Notas_Metodos/`**: notebooks de notas metodológicas. Cada archivo desarrolla un tema financiero o estadístico con explicación teórica, fórmulas y código en Python.
- **`docs/`**: versión Quarto del notebook principal de opciones americanas. Contiene el `.qmd`, el HTML renderizado y los assets necesarios para publicar en GitHub Pages.
- **`CNAME`**: configuración de dominio para GitHub Pages.
- **`README.md`**: descripción general del proyecto y de su estructura.

---

## Notebooks principales

### `Notebooks/ProyectoIndividual.ipynb`

Notebook original del proyecto de **Finanzas Computacionales**. Implementa la valuación de opciones call y put americanas usando:

- árbol binomial para un activo;
- árbol binomial para un portafolio de dos activos correlacionados;
- simulación de trayectorias tipo GBM;
- método de **Longstaff-Schwartz** para un activo;
- Longstaff-Schwartz para un portafolio de dos acciones.

### `Notebooks/Correcciones2.ipynb`

Versión corregida y más ordenada del notebook original. Centraliza la descarga de datos con `yfinance`, calcula estimadores financieros desde históricos y separa la lógica en funciones reutilizables:

- `get_close`, `returns_from_close`, `calcula_media`, `calcula_desv_est`, `calcula_correlacion`;
- `arbol_americano` y `arbol_americano_portafolio`;
- simulaciones individuales y correlacionadas;
- rutinas de ejercicio, estrategia y precio con Longstaff-Schwartz;
- histograma de fechas de ejercicio.

---

## Notas metodológicas

La carpeta **`Notas_Metodos/`** contiene notebooks pensados como apuntes explicativos. Además de código, incluyen contexto teórico, fórmulas y ejemplos.

### `Notas_Metodos/BlackSholes_en_opciones.ipynb`

Introduce el modelo de **Black-Scholes** para opciones europeas. Explica la valuación bajo neutralidad al riesgo, el movimiento browniano geométrico, la fórmula cerrada para calls y puts, sus supuestos y limitaciones. También conecta Black-Scholes con simulación Monte Carlo para valorar derivados.

Funciones principales:

- `N`: aproximación de la función de distribución normal estándar;
- `bs_call_price`: precio de una call europea;
- `bs_put_price`: precio de una put europea.

### `Notas_Metodos/SimulacionMonteCarlo.ipynb`

Desarrolla la teoría de **simulación Monte Carlo** y su relación con la valuación de derivados. Revisa la Ley de los Grandes Números, el Teorema Central del Límite, el estimador Monte Carlo, error estándar e intervalos de confianza. Incluye ejemplos para estimar esperanzas, probabilidades y analizar convergencia.

### `Notas_Metodos/Bonos.ipynb`

Explica la valuación de **bonos cuponados**. Incluye precio de un bono, factor de valor presente de una anualidad, prima/descuento, tabla de amortización, valor teórico entre fechas de cupón y conversión de tasas.

Funciones principales:

- `an_j`: factor de anualidad;
- `precio_bono`: precio teórico del bono;
- `tabla_amortizacion_bono`: schedule de amortización;
- `valores_teoricos_entre_cupones`: evolución del valor entre cupones;
- `nominal_a_efectiva` y `efectiva_a_nominal`: conversión de tasas.

### `Notas_Metodos/DatosFaltantes.ipynb`

Analiza valores faltantes en precios de acciones mexicanas descargadas con `yfinance`. Identifica rachas de `NaN`, fechas problemáticas y aplica estrategias de imputación:

- rachas cortas: promedio de los últimos valores observados;
- rachas largas: interpolación lineal;
- construcción de features financieras;
- división train/test respetando el orden temporal.

Este notebook genera el archivo **`Notas_Metodos/datoslimpos.csv`**, que contiene precios limpios de acciones mexicanas y sirve como insumo para otros notebooks.

Funciones principales:

- `find_nan_runs`;
- `fill_short`;
- `fill_long_linear`;
- `impute_series`.

### `Notas_Metodos/Series.ipynb`

Presenta rutinas de estimación, validación y pronóstico para **series de tiempo financieras**. Trabaja con precios, rendimientos, estacionariedad, autocorrelación y modelos:

- AR, MA, ARMA, ARIMA y SARIMA;
- ARCH, GARCH, EGARCH y GJR-GARCH;
- comparación por AIC/BIC;
- validación fuera de muestra;
- pronóstico con ARIMA y GARCH;
- comparación entre distribución normal y t-Student.

Funciones principales:

- `adf_test`;
- `plot_acf_pacf`;
- `train_test_split_time_series`;
- `comparar_arima`;
- `evaluar_pronostico`.

### `Notas_Metodos/VaRyCVaR.ipynb`

Calcula **Valor en Riesgo (VaR)** y **Valor en Riesgo Condicional (CVaR / Expected Shortfall)**. Usa como entrada `datoslimpos.csv` y compara métodos de estimación:

- histórico;
- paramétrico normal;
- paramétrico t-Student;
- EWMA;
- simulación Monte Carlo normal y t-Student;
- GARCH normal y GARCH t-Student;
- escalamiento a varios días;
- conversión a VaR monetario;
- visualizaciones comparativas.

Funciones principales:

- `preparar_rendimientos`;
- `var_cvar_historico`;
- `var_cvar_normal`;
- `var_cvar_t_student`;
- `var_cvar_ewma`;
- `var_cvar_monte_carlo_normal`;
- `var_cvar_monte_carlo_t`;
- `var_cvar_garch_normal`;
- `var_cvar_garch_t`;
- `comparar_metodos_var_cvar`;
- `escalar_var_cvar`;
- `convertir_a_monetario`;
- `graficar_var_cvar`.

### `Notas_Metodos/datoslimpos.csv`

Base de datos limpia generada desde `DatosFaltantes.ipynb`. Contiene precios históricos de acciones mexicanas `.MX` en formato tabular:

- columna `Date`;
- una columna por ticker;
- datos imputados y preparados para análisis posterior.

---

## Sitio Quarto

### `docs/finanzas_interactivo.qmd`

Fuente Quarto del notebook interactivo de finanzas. Documenta el flujo completo para valuar opciones americanas:

- descarga de precios con `yfinance`;
- cálculo de retornos, media, volatilidad y correlación;
- simulación de trayectorias;
- Longstaff-Schwartz para un activo;
- Longstaff-Schwartz para portafolio;
- árbol binomial americano;
- diagrama Mermaid con enlaces internos a las funciones;
- visualización del histograma de ejercicio.

### `docs/finanzas_interactivo.html`

HTML renderizado a partir del archivo `.qmd`. Es la versión publicada en GitHub Pages.

### `docs/finanzas_interactivo_files/`

Carpeta generada automáticamente por Quarto. Contiene imágenes, librerías de Bootstrap, scripts de Quarto, Mermaid y otros assets necesarios para que el HTML funcione correctamente.

---

## Árbol de carpetas

```text
.
├─ Notas_Metodos/
│  ├─ BlackSholes_en_opciones.ipynb   # Black-Scholes y valuación de opciones europeas
│  ├─ Bonos.ipynb                     # Bonos cuponados, amortización y tasas
│  ├─ DatosFaltantes.ipynb            # Limpieza e imputación de datos financieros
│  ├─ Series.ipynb                    # Modelos de series de tiempo financieras
│  ├─ SimulacionMonteCarlo.ipynb      # Teoría y ejemplos de Monte Carlo
│  ├─ VaRyCVaR.ipynb                  # VaR y CVaR con métodos históricos, paramétricos y GARCH
│  └─ datoslimpos.csv                 # Base limpia generada desde DatosFaltantes.ipynb
│
├─ Notebooks/
│  ├─ ProyectoIndividual.ipynb        # Notebook original del proyecto individual
│  └─ Correcciones2.ipynb             # Versión corregida/refactorizada
│
├─ docs/
│  ├─ finanzas_interactivo.qmd        # Fuente Quarto
│  ├─ finanzas_interactivo.html       # HTML publicado
│  └─ finanzas_interactivo_files/     # Assets generados por Quarto
│     ├─ figure-html/                 # Figuras/salidas de celdas
│     └─ libs/                        # Librerías estáticas
│
├─ CNAME                              # Configuración de dominio para GitHub Pages
└─ README.md
```

---

## Requisitos

- **Python 3.10+** recomendado.
- **Jupyter Notebook** o **JupyterLab** para abrir los `.ipynb`.
- **Quarto** para renderizar `docs/finanzas_interactivo.qmd`.

Paquetes principales de Python:

- `numpy`
- `pandas`
- `matplotlib`
- `yfinance`
- `scikit-learn`
- `scipy`
- `statsmodels`
- `arch`

Instalación sugerida:

```bash
pip install numpy pandas matplotlib yfinance scikit-learn scipy statsmodels arch
```

---

## Flujo recomendado

1. Revisar `Notebooks/Correcciones2.ipynb` o `docs/finanzas_interactivo.qmd` para el proyecto principal de opciones americanas.
2. Abrir los notebooks de `Notas_Metodos/` según el tema que se quiera estudiar.
3. Ejecutar primero `Notas_Metodos/DatosFaltantes.ipynb` si se necesita regenerar `datoslimpos.csv`.
4. Ejecutar `Notas_Metodos/VaRyCVaR.ipynb` desde la carpeta `Notas_Metodos/`, porque lee `datoslimpos.csv` con una ruta relativa.
5. Para actualizar el sitio, renderizar el archivo Quarto:

```bash
quarto render docs/finanzas_interactivo.qmd
```
