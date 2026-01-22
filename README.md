# Finanzas — Valuación de Opciones Americanas (Binomial y Longstaff–Schwartz)

Proyecto en **Python + Quarto** para valuar **opciones Americanas**:
- **Árbol binomial** (1 activo y aproximación de portafolio con \(\sigma_P\))
- **Longstaff–Schwartz (LS)** por Monte Carlo (1 activo y **portafolio** \(P=wS_1+(1-w)S_2\))

Incluye descarga de datos con **yfinance**, estimación de \(\mu,\sigma,\rho\) desde históricos y visualización del **histograma de ejercicio**.

---

## Estructura del proyecto


---

## Requisitos
- Python 3.10+ (recomendado)
- Paquetes:
  - `numpy`, `pandas`, `matplotlib`
  - `yfinance`
  - `scikit-learn`
  - `quarto` (si quieres renderizar el `.qmd`)

Instalación rápida:
```bash
pip install numpy pandas matplotlib yfinance scikit-learn
```

## Ver el sitio 

- Finanzas interactivo: https://1enrique9.github.io/Proyecto_SS/finanzas_interactivo.html