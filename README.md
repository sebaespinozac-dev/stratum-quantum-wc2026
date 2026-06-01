# ⚽🔬 Stratum Quantum Predictor — FIFA World Cup 2026

> Hybrid Quantum-Classical model for match prediction and bracket simulation
> by Sebastián Espinoza C. | Stratum AI | getstratum.cl

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/sebaespinozac-dev/stratum-quantum-wc2026/blob/main/stratum_quantum_wc2026_v2.ipynb)

## 🧠 What is this?
A hybrid quantum-classical model using IBM Qiskit to predict FIFA World Cup 2026 results. It analyzes 48 teams across 28 variables using a 6-qubit ZZFeatureMap circuit and runs 1000 Monte Carlo tournament simulations.

**UCL Champion:** PSG (back-to-back 2024-25 & 2025-26, defeated Arsenal 4-3 on penalties in Budapest)

## 📊 28 Variables
Elo Rating, xG, xGA, FIFA Rank, Key Injuries, Squad Value, Average Age, Caps, Rest Days, Form (5 & 10 games), H2H History, Striker Available, Goalkeeper Available, Goal Difference, Betting Odds, WC Experience, WC Titles, Defending Champion, Best WC Result, Qatar 2022 Stage, Top-5 League %, UCL Players, UCL Champion %, Home Advantage, Temperature, Humidity, Altitude, Tournament Phase.

## ⚡ Tech Stack
Qiskit · ZZFeatureMap · RealAmplitudes · Qiskit Aer · qiskit-machine-learning · pandas · numpy · matplotlib

## 🚀 Run it
Click the Colab badge above or run locally:
pip install qiskit qiskit-machine-learning qiskit-aer scikit-learn pandas numpy matplotlib seaborn

## 📬 Contact
Sebastián Espinoza C.
sebaespinozac@gmail.com | getstratum.cl
