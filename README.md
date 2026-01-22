# Proyecto_SS — Estructura del proyecto

**Finanzas interactivo (HTML):** https://1enrique9.github.io/Proyecto_SS/finanzas_interactivo.html

Proyecto en **Python + Quarto** para valuar **opciones Americanas**:
- **Árbol binomial** (1 activo y aproximación de portafolio con \(\sigma_P\))
- **Longstaff–Schwartz (LS)** por Monte Carlo (1 activo y **portafolio** \(P=wS_1+(1-w)S_2\))

Incluye descarga de datos con **yfinance**, estimación de \(\mu,\sigma,\rho\) desde históricos y visualización del **histograma de ejercicio**.

---

## Estructura del repositorio

- **`Notebooks/`**: notebooks de trabajo en Jupyter. Aquí está el notebook original del *Proyecto Individual* y las versiones con correcciones.
- **`docs/`**: todo lo generado para Quarto, incluyendo el `.qmd` fuente y el `.html` renderizado (más sus assets). Esta carpeta se usa para publicar en GitHub Pages.

---

## Árbol de carpetas

```text
.
├─ Notebooks/
│  ├─ ProyectoIndividual.ipynb      # Notebook original (proyecto individual)
│  └─ Correcciones2.ipynb           # Notebook con correcciones / refactor sobre el original
│
├─ docs/
│  ├─ finanzas_interactivo.qmd      # Fuente Quarto (texto + código + diagramas)
│  ├─ finanzas_interactivo.html     # Render HTML (publicado en Pages)
│  └─ finanzas_interactivo_files/   # Assets generados al renderizar
│     ├─ figure-html/               # Figuras/salidas de celdas (png)
│     └─ libs/                      # Librerías estáticas para el HTML (bootstrap/quarto, etc.)
│
├─ CNAME                            # Configuración de dominio (GitHub Pages, si aplica)
└─ README.md                       
```
---
## Requisitos 

- **Python 3.10+** (recomendado)
- Paquetes:
  - `numpy`, `pandas`, `matplotlib`
  - `yfinance`
  - `scikit-learn`
- **Quarto** (para renderizar el `.qmd`)

Instalación de dependencias en Python:
```bash
pip install numpy pandas matplotlib yfinance scikit-learn
```
