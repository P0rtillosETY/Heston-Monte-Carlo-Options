# Heston Monte Carlo Options 📈

Valuación de opciones europeas sobre acciones reales usando el modelo 
de volatilidad estocástica de Heston y simulación Monte Carlo.

Desarrollado como parte del programa **Haciendo Ciencia BUAP 2026**,
bajo la dirección del Dr. Hugo Adan Cruz Suárez.

---

## ¿Qué hace este proyecto?

Construye un sistema completo para valuar opciones financieras de tipo 
call y put sobre cualquier acción cotizada en bolsa. A diferencia del 
modelo clásico de Black-Scholes, que asume volatilidad constante, este 
proyecto implementa el modelo de Heston, donde la volatilidad también 
es aleatoria y evoluciona con el tiempo.

Una ventaja importante: **los notebooks se actualizan automáticamente** 
con los precios más recientes del mercado cada vez que se ejecutan y 
**los notebooks pueden usarse para otras acciones**.

---

## ¿Cómo funciona?

**Notebook 1 — EDA**
Se descargan 3 años de datos históricos de NVDA y GOOGL con yfinance.
Se calculan los rendimientos logarítmicos y se analizan sus estadísticas:
media, volatilidad, asimetría y curtosis. Se confirma que los rendimientos
no siguen una distribución normal, justificando el uso de Heston.

**Notebook 2 — Modelo de Heston**
Se calibran los parámetros κ, θ, α y ρ del modelo usando:
- Proxy de varianza: V̂_t = (Σ r²_diarios) × 52
- Regresión WLS con pesos w_t = 1/(V_t · h)
- Estimación de α desde residuos estandarizados
- Estimación de ρ como correlación entre ruidos del precio y la varianza

**Notebook 3 — Monte Carlo**
Se simulan 10,000 trayectorias de precio sobre un horizonte de 6 meses.
Se calculan los precios de opciones call y put para 5 strikes distintos.
Se verifica la consistencia mediante la paridad put-call.

---

## Tecnologías

- Python 3
- pandas, numpy, matplotlib
- scipy, statsmodels
- yfinance

---

## Acciones estudiadas

| Empresa | Ticker |
|---------|--------|
| NVIDIA Corporation | NVDA |
| Alphabet Inc. | GOOGL |

El modelo puede aplicarse a **cualquier acción cotizada en bolsa** 
simplemente cambiando el ticker en el Notebook 1.

---

## Autor

**Edgar Manuel Portillo Pérez**
Estudiante de Física — Facultad de Ciencias Físico Matemáticas, BUAP
Programa Haciendo Ciencia 2026
