# ⚽🔬 Stratum Quantum Predictor v3.5 — FIFA World Cup 2026

**by Sebastián Espinoza C. | [Stratum AI](https://getstratum.cl) | sebaespinozac@gmail.com**

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/sebaespinozac-dev/stratum-quantum-wc2026/blob/main/stratum_quantum_wc2026_v2.ipynb)

---

## ¿Qué es esto?

Un modelo híbrido **cuántico-clásico** que predice el ganador del **Mundial FIFA 2026** (USA/Canada/México).

Combina:
- **28 variables** por selección (Elo, xG, xGA, plantel UCL, forma, historia, altitud, etc.)
- **Circuito cuántico de 4 qubits** (ZZFeatureMap + entrelazamiento) vía Qiskit
- **IBM Quantum real hardware** (QPU Eagle) o AerSimulator con noise model Eagle
- **Monte Carlo × 1000 torneos** completos (fase de grupos → R32 → Final)

## Resultados actuales (1000 simulaciones)

| # | Selección | Campeón% |
|---|-----------|----------|
| 🥇 | Argentina | ~17% |
| 🥈 | France | ~16% |
| 🥉 | Spain | ~14% |
| 4 | Brazil | ~12% |

*Resultados varían levemente por aleatoriedad cuántica en cada ejecución.*

## Arquitectura del modelo

```
28 Variables por selección
├── Rendimiento: Elo, xG, xGA, FIFA rank, forma 5/10, GD
├── Plantel: lesionados, valor plantilla, edad, caps, descanso
├── UCL: % top5 ligas, jugadores UCL, % del campeón (PSG bicampeón)
├── Individual: goleador y portero disponibles
├── Historia: títulos WC, campeón defensor, mundiales, mejor resultado
├── Contexto: localía, temperatura, humedad, altitud, odds
└── H2H: historial directo
         ↓
 Quantum Strength Score (MinMaxScaler → pesos → normalizado 0-100)
         ↓
 Circuito 4 qubits: RY(s1)⊗RY(s2)⊗RY(gap)⊗RY(phase) + CNOT entrelazado
         ↓
 IBM QPU real (token) o AerSimulator Eagle noise model
         ↓
 Monte Carlo × 1000 torneos completos (bracket oficial M73→M104)
```

## Grupos oficiales FIFA 2026

Sorteo: 5 dic 2025, Washington DC

| Grupo | Equipos |
|-------|---------|
| A | México, South Africa, South Korea, Czechia |
| B | Canada, Bosnia, Qatar, Switzerland |
| C | Brazil, Morocco, Haiti, Scotland |
| D | USA, Paraguay, Australia, Turkey |
| E | Germany, Curaçao, Ivory Coast, Ecuador |
| F | Netherlands, Japan, Sweden, Tunisia |
| G | Belgium, Egypt, Iran, New Zealand |
| H | Spain, Cape Verde, Saudi Arabia, Uruguay |
| I | France, Senegal, Iraq, Norway |
| J | Argentina, Algeria, Austria, Jordan |
| K | Portugal, DR Congo, Uzbekistan, Colombia |
| L | England, Croatia, Ghana, Panama |

## Cómo correrlo

### Google Colab (recomendado)
1. Click en el badge **Open in Colab** arriba
2. `Entorno de ejecución → Ejecutar todo`
3. Esperar ~3-5 min para el Monte Carlo

### IBM Quantum real hardware
La Celda 2 se conecta automáticamente al backend menos ocupado con `least_busy()`.  
- `verbose=True` en `qpredict()` → corre en QPU real (2048 shots)
- El Monte Carlo ×1000 siempre usa Statevector local (cola demasiado lenta)

### Local
```bash
python -m venv qenv
source qenv/bin/activate
pip install qiskit qiskit-aer qiskit-ibm-runtime scikit-learn pandas numpy matplotlib seaborn
jupyter notebook stratum_quantum_wc2026_v2.ipynb
```

## Outputs generados

- `stratum_quantum_wc2026_v35_PRESS.png` — Dashboard 6 paneles para prensa
- `stratum_quantum_wc2026_v35_groups_radar.png` — Potencia por grupo + radar top 8
- `stratum_quantum_wc2026_v3_predictions.csv` — CSV con todas las probabilidades

## Changelog

### v3.5 (2026-06-02)
- **Fix**: Salah movido a Egypt; Palmer agregado a England
- Adams T (USA) vs Adams C (Scotland) desambiguados
- Planteles completos: Egypt (Salah + Marmoush), Senegal (Diallo PSG), Japan
- Nueva visualización: dificultad por grupo + radar fortalezas top 8

### v3.2–v3.3
- Fix bug crítico `qpredict`: marginals qubit-0/qubit-1 en lugar de qubit-3
- Germany calibrado: Elo 1975, form5 0.76
- IBM Quantum real hardware integration (SamplerV2 + least_busy)

### v3.0–v3.1
- Equipos y grupos FIFA 2026 oficiales (sorteo Washington DC 5 dic 2025)
- 48 selecciones, 28 variables, bracket R32 oficial (M73–M104)
- UCL Champion PSG bicampeón 2024-25 & 2025-26

## Autor

**Sebastián Espinoza C.**  
Founder @ [Stratum AI](https://getstratum.cl) · [EcoAves](https://ecoaves.cl)  
sebaespinozac@gmail.com · GitHub: [@sebaespinozac-dev](https://github.com/sebaespinozac-dev)
