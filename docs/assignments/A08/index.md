# A8 – Gears

# MEGR 2156 / MEGR 2157 Assignment: Gear Box Design Report

**Course:** MEGR 2156 / MEGR 2157 — Design Methodology & CAD  
**Project:** Two-Shaft Spur Gearbox Enclosure, Shaft Sizing, and Bearing Analysis  
**Software Used:** PTC Creo Parametric 9.0/10.0, McMaster-Carr CAD Integration  

---

## Executive Summary

This engineering report documents the parametric design, mechanical analysis, component selection, and CAD implementation of a compact two-shaft spur gearbox. The system provides a $2.667:1$ speed reduction ($24:9$ gear ratio) operating at an output speed of $1100\text{ RPM}$ and output torque of $1.25\text{ in}\cdot\text{lbf}$. 

All critical components—including the input and output shafts, self-lubricating Acetal journal bearings, and split housing enclosure—were analyzed for strength, pressure-velocity ($PV$) limits, and wall stress under worst-case operating conditions. The complete CAD assembly, parameter relations table, bill of materials (BOM), and ASME Y14.5 drawing suite are fully detailed in the sections below.

---

## 1. Project Specifications & Requirements

### 1.1 Operating Requirements
* **Output Speed ($N_{\text{out}}$):** $1100\text{ RPM}$[cite: 5]
* **Output Torque ($T_{\text{out}}$):** $1.25\text{ in}\cdot\text{lbf}$[cite: 5]
* **Gear Ratio:** $24:9$ ($2.667:1$)[cite: 5]
* **Input Shaft Diameter ($d_{\text{in}}$):** $\varnothing 0.125\text{ in}$ ($\frac{1}{8}\text{"}$)[cite: 5]
* **Output Shaft Diameter ($d_{\text{out}}$):** $\varnothing 0.250\text{ in}$ ($\frac{1}{4}\text{"}$)[cite: 5]
* **Shaft Lengths ($L_{\text{shaft}}$):** $1.00\text{ in}$ each[cite: 5]
* **Shaft Material:** AISI 1018 Cold Drawn Steel ($\tau_y = 31,000\text{ psi}$, $\sigma_y = 54,000\text{ psi}$)[cite: 5]
* **Shaft-to-Gear Interface:** Interference press fit through hub[cite: 5]
* **Shaft-to-Housing Interface:** Running sliding fit ($RC4$) in sleeve bearings[cite: 5]

### 1.2 Selected Off-the-Shelf Components
* **Pinion Gear (18T, 48 DP):** McMaster-Carr `#7880K19` (Brass, $20^\circ$ Pressure Angle, $\varnothing 0.375\text{"}\text{ PD}$, $\varnothing 0.125\text{"}\text{ Bore}$)[cite: 8, 12]
* **Output Driven Gear (48T, 48 DP):** McMaster-Carr `#7880K24` (Brass, $20^\circ$ Pressure Angle, $\varnothing 1.000\text{"}\text{ PD}$, $\varnothing 0.250\text{"}\text{ Bore}$)[cite: 8, 12]
* **Input Shaft Journal Bearings:** McMaster-Carr `#2610T1` Series (Acetal, $\varnothing 0.125\text{"}\text{ ID} \times \varnothing 0.250\text{"}\text{ OD} \times 0.250\text{"}\text{ Length}$)[cite: 8, 11]
* **Output Shaft Journal Bearings:** McMaster-Carr `#2610T1` Series (Acetal, $\varnothing 0.250\text{"}\text{ ID} \times \varnothing 0.375\text{"}\text{ OD} \times 0.250\text{"}\text{ Length}$)[cite: 8, 11]

---

## 2. Shaft Design & Torsional Stress Analysis

### 2.1 Input Shaft Analysis (Power Transmission Shaft)

#### Knowns & Unknowns[cite: 5]
* **Knowns:**
  * Output Torque $T_{\text{out}} = 1.25\text{ in}\cdot\text{lbf}$[cite: 5]
  * Output Speed $N_{\text{out}} = 1100\text{ RPM}$[cite: 5]
  * Gear Teeth Ratio $N_2 / N_1 = 24/9 = 48/18 = 2.6667$[cite: 5, 8]
  * Input Shaft Diameter $d_{\text{in}} = 0.125\text{ in}$[cite: 5, 6]
  * Shaft Length $L_{\text{in}} = 1.00\text{ in}$[cite: 5, 6]
  * Material Yield Shear Strength $\tau_y = 31,000\text{ psi}$ (AISI 1018 Steel)[cite: 5, 6]
  * Target Factor of Safety $SF = 2.0$[cite: 5, 6]
* **Unknowns:**
  * Input Torque $T_{\text{in}}$[cite: 5]
  * Input Speed $N_{\text{in}}$[cite: 5]
  * Torsional Shear Stress $\tau_{\text{in}}$[cite: 5]
  * Allowable Shear Stress $\tau_{\text{allow}}$[cite: 5]
  * Actual Factor of Safety $SF_{\text{actual}}$[cite: 5]

#### Free Body Diagram (FBD) Model[cite: 6]
