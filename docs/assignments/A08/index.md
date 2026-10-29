# A8 – Gears

**Course:** MEGR 2156 / MEGR 2157 — Design Methodology & CAD  
**Project:** Two-Shaft Spur Gearbox Enclosure, Shaft Sizing, and Bearing Analysis  
**Software Used:** PTC Creo Parametric, McMaster-Carr CAD Integration  
**CAD FILE LINKED HERE: https://github.com/ilittle8/design-projects-portfolio/blob/main/docs/assignments/A08/gearbox.asm.zip**

---

## 1. Project Specifications & Requirements

### 1.1 Operating Requirements
* **Output Speed ($N_{\text{out}}$):** $1100\text{ RPM}$
* **Output Torque ($T_{\text{out}}$):** $1.25\text{ in}\cdot\text{lbf}$
* **Gear Ratio:** $24:9$ ($2.667:1$)
* **Input Shaft Diameter ($d_{\text{in}}$):** $\varnothing 0.125\text{ in}$ ($\frac{1}{8}\text{"}$)
* **Output Shaft Diameter ($d_{\text{out}}$):** $\varnothing 0.250\text{ in}$ ($\frac{1}{4}\text{"}$)
* **Shaft Lengths ($L_{\text{shaft}}$):** $1.00\text{ in}$ each
* **Shaft Material:** AISI 1018 Cold Drawn Steel ($\tau_y = 31,000\text{ psi}$, $\sigma_y = 54,000\text{ psi}$)
* **Shaft-to-Gear Interface:** Interference press fit through hub
* **Shaft-to-Housing Interface:** Running sliding fit ($RC4$) in sleeve bearings

### 1.2 Selected Off-the-Shelf Components
* **Pinion Gear (18T, 48 DP):** McMaster-Carr `#7880K19` (Brass, $20^\circ$ Pressure Angle, $\varnothing 0.375\text{"}\text{ PD}$, $\varnothing 0.125\text{"}\text{ Bore}$)
* **Output Driven Gear (48T, 48 DP):** McMaster-Carr `#7880K24` (Brass, $20^\circ$ Pressure Angle, $\varnothing 1.000\text{"}\text{ PD}$, $\varnothing 0.250\text{"}\text{ Bore}$)
* **Input Shaft Journal Bearings:** McMaster-Carr `#2610T1` Series (Acetal, $\varnothing 0.125\text{"}\text{ ID} \times \varnothing 0.250\text{"}\text{ OD} \times 0.250\text{"}\text{ Length}$)
* **Output Shaft Journal Bearings:** McMaster-Carr `#2610T1` Series (Acetal, $\varnothing 0.250\text{"}\text{ ID} \times \varnothing 0.375\text{"}\text{ OD} \times 0.250\text{"}\text{ Length}$)

---

## 2. Shaft Design & Torsional Stress Analysis

### 2.1 Input Shaft Analysis (Power Transmission Shaft)

#### Knowns & Unknowns
* **Knowns:**
  * Output Torque $T_{\text{out}} = 1.25\text{ in}\cdot\text{lbf}$
  * Output Speed $N_{\text{out}} = 1100\text{ RPM}$
  * Gear Ratio $N_2 / N_1 = 24/9 = 48/18 = 2.6667$
  * Input Shaft Diameter $d_{\text{in}} = 0.125\text{ in}$
  * Shaft Length $L_{\text{in}} = 1.00\text{ in}$
  * Material Yield Shear Strength $\tau_y = 31,000\text{ psi}$ (AISI 1018 Steel)
  * Target Factor of Safety $SF = 2.0$
  * Fit Type = Interference Press Fit
  * Radial Force Moment = $0$ (small enough to be ignored)
* **Unknowns:**
  * Input Torque $T_{\text{in}}$
  * Input Speed $N_{\text{in}}$
  * Torsional Shear Stress $\tau_{\text{in}}$
  * Allowable Shear Stress $\tau_{\text{allow}}$
  * Actual Factor of Safety $SF_{\text{actual}}$
  * Minimum Shaft Diameter $d_{\text{min}}$

#### Free Body Diagram (FBD) Model
<img width="635" height="233" alt="image" src="https://github.com/user-attachments/assets/104a5bd6-29bb-47eb-95f9-bd57eafe0110" />

#### Algebraic & Governing Equations
$$N_{\text{in}} = N_{\text{out}} \cdot \left(\frac{N_2}{N_1}\right) = N_{\text{out}} \cdot \left(\frac{24}{9}\right)$$

$$T_{\text{in}} = T_{\text{out}} \cdot \left(\frac{N_1}{N_2}\right) = T_{\text{out}} \cdot \left(\frac{9}{24}\right)$$

$$\tau_{\text{in}} = \frac{T_{\text{in}} \cdot r}{J} = \frac{T_{\text{in}} \cdot (d_{\text{in}}/2)}{\frac{\pi d_{\text{in}}^4}{32}} = \frac{16 T_{\text{in}}}{\pi d_{\text{in}}^3}$$

$$\tau_{\text{allow}} = \frac{\tau_y}{SF}$$

$$SF_{\text{actual}} = \frac{\tau_y}{\tau_{\text{in}}}$$

#### Numerical Calculation
$$N_{\text{in}} = 1100\text{ RPM} \cdot \left(\frac{24}{9}\right) = \mathbf{2933.33\text{ RPM}}$$

$$T_{\text{in}} = 1.25\text{ in}\cdot\text{lbf} \cdot \left(\frac{9}{24}\right) = \mathbf{0.46875\text{ in}\cdot\text{lbf}}$$

$$\tau_{\text{in}} = \frac{16(0.46875\text{ in}\cdot\text{lbf})}{\pi (0.125\text{ in})^3} = \frac{7.5}{0.0061359} \approx \mathbf{1222.31\text{ psi}}$$

$$\tau_{\text{allow}} = \frac{31,000\text{ psi}}{2.0} = \mathbf{15,500\text{ psi}}$$

$$SF_{\text{actual}} = \frac{31,000\text{ psi}}{1222.31\text{ psi}} \approx \mathbf{25.36}$$

#### Sufficiency Verdict
Since $SF_{\text{actual}} = 25.36 \gg 2.0$ (and $\tau_{\text{in}} = 1222.31\text{ psi} \ll \tau_{\text{allow}} = 15,500\text{ psi}$), the input shaft diameter of $\varnothing 0.125\text{ in}$ is **fully sufficient** for strength under pure torsion. No diameter modification is required.

---

### 2.2 Output Shaft Analysis (Short Shaft)

#### Knowns & Unknowns
* **Knowns:**
  * Output Torque $T_{\text{out}} = 1.25\text{ in}\cdot\text{lbf}$
  * Output Speed $N_{\text{out}} = 1100\text{ RPM}$
  * Output Shaft Diameter $d_{\text{out}} = 0.250\text{ in}$
  * Shaft Length $L_{\text{out}} = 1.00\text{ in}$
  * Material Yield Shear Strength $\tau_y = 31,000\text{ psi}$ (AISI 1018 Steel)
  * Target Factor of Safety $SF = 2.0$
  * Fit Type = Interference Press Fit
  * Radial Force Moment = $0$
* **Unknowns:**
  * Torsional Shear Stress $\tau_{\text{out}}$
  * Allowable Shear Stress $\tau_{\text{allow}}$
  * Actual Factor of Safety $SF_{\text{actual}}$
  * Minimum Shaft Diameter $d_{\text{min}}$

#### Free Body Diagram (FBD) Model
<img width="590" height="178" alt="image" src="https://github.com/user-attachments/assets/4d24687b-5f5f-4882-a4af-010261b24076" />

#### Algebraic & Governing Equations
$$\tau_{\text{out}} = \frac{T_{\text{out}} \cdot r}{J} = \frac{16 T_{\text{out}}}{\pi d_{\text{out}}^3}$$

$$SF_{\text{actual}} = \frac{\tau_y}{\tau_{\text{out}}}$$

#### Numerical Calculation
$$\tau_{\text{out}} = \frac{16(1.25\text{ in}\cdot\text{lbf})}{\pi (0.250\text{ in})^3} = \frac{20}{0.049087} \approx \mathbf{407.44\text{ psi}}$$

$$\tau_{\text{allow}} = \frac{31,000\text{ psi}}{2.0} = \mathbf{15,500\text{ psi}}$$

$$SF_{\text{actual}} = \frac{31,000\text{ psi}}{407.44\text{ psi}} \approx \mathbf{76.08}$$

#### Sufficiency Verdict
Since $SF_{\text{actual}} = 76.08 \gg 2.0$ (and $\tau_{\text{out}} = 407.44\text{ psi} \ll \tau_{\text{allow}} = 15,500\text{ psi}$), the output shaft diameter of $\varnothing 0.250\text{ in}$ is **fully sufficient** for strength under pure torsion. No diameter modification is required.

---

## 3. Journal Bearing Sizing & PV Analysis

### 3.1 Bearing Load & Pressure-Velocity ($PV$) Analysis

#### Knowns & Unknowns
* **Knowns:**
  * Pinion Pitch Radius $r_{p1} = 0.1875\text{ in}$ (Pitch Dia $D_{p1} = 0.375\text{ in}$)
  * Gear Pitch Radius $r_{p2} = 0.5000\text{ in}$ (Pitch Dia $D_{p2} = 1.000\text{ in}$)
  * Gear Pressure Angle $\phi = 20^\circ$
  * Input Torque $T_{\text{in}} = 0.46875\text{ in}\cdot\text{lbf}$
  * Bearing Length $L = 0.250\text{ in}$
  * Input Shaft Speed $N_{\text{in}} = 2933.33\text{ RPM}$
  * Output Shaft Speed $N_{\text{out}} = 1100\text{ RPM}$
* **Unknowns:**
  * Tangential Mesh Force $F_t$
  * Total Normal Mesh Force $F_{\text{total}}$
  * Bearing Reaction Force $F_{\text{bearing}}$ (2 bearings per shaft)
  * Projected Bearing Area $A_{\text{proj}}$
  * Bearing Operating Pressure $P$
  * Surface Sliding Velocity $V$
  * Operating Pressure-Velocity Factor $PV$
  * Bearing Material Selection

#### Force & Bearing Reaction FBD Model
<img width="596" height="329" alt="image" src="https://github.com/user-attachments/assets/4f9d3d6e-967a-4cd0-952c-cef95c5af9e7" />

#### Algebraic & Governing Equations
$$F_t = \frac{T_{\text{in}}}{r_{p1}}$$

$$F_{\text{total}} = \frac{F_t}{\cos(\phi)} = \frac{F_t}{\cos(20^\circ)}$$

$$F_{\text{bearing}} = \frac{F_{\text{total}}}{2}$$

$$A_{\text{proj}} = d \cdot L$$

$$P = \frac{F_{\text{bearing}}}{A_{\text{proj}}}$$

$$V = \frac{\pi \cdot d \cdot N}{12} \quad \left[\text{ft/min}\right]$$

$$PV = P \cdot V \quad \left[\text{psi}\cdot\frac{\text{ft}}{\text{min}}\right]$$

#### Numerical Calculation

1. **Gear Mesh Reaction Forces:**
   $$F_t = \frac{0.46875\text{ in}\cdot\text{lbf}}{0.1875\text{ in}} = \mathbf{1.25\text{ lbf}}$$
   $$F_{\text{total}} = \frac{1.25\text{ lbf}}{\cos(20^\circ)} = \frac{1.25}{0.93969} \approx \mathbf{1.33\text{ lbf}}$$
   $$F_{\text{bearing}} = \frac{1.33\text{ lbf}}{2} = \mathbf{0.665\text{ lbf per bearing}}$$

2. **Input Shaft Journal Bearing ($\varnothing 0.125\text{ in} \times 0.250\text{ in}$):**
   $$A_{\text{proj, in}} = 0.125\text{ in} \times 0.250\text{ in} = \mathbf{0.03125\text{ in}^2}$$
   $$P_{\text{in}} = \frac{0.665\text{ lbf}}{0.03125\text{ in}^2} = \mathbf{21.28\text{ psi}}$$
   $$V_{\text{in}} = \frac{\pi (0.125\text{ in}) (2933.33\text{ RPM})}{12} \approx \mathbf{95.99\text{ ft/min}}$$
   $$PV_{\text{in}} = 21.28\text{ psi} \times 95.99\text{ ft/min} \approx \mathbf{2042.7\text{ psi}\cdot\text{ft/min}}$$

3. **Output Shaft Journal Bearing ($\varnothing 0.250\text{ in} \times 0.250\text{ in}$):**
   $$A_{\text{proj, out}} = 0.250\text{ in} \times 0.250\text{ in} = \mathbf{0.06250\text{ in}^2}$$
   $$P_{\text{out}} = \frac{0.665\text{ lbf}}{0.06250\text{ in}^2} = \mathbf{10.64\text{ psi}}$$
   $$V_{\text{out}} = \frac{\pi (0.250\text{ in}) (1100\text{ RPM})}{12} \approx \mathbf{71.99\text{ ft/min}}$$
   $$PV_{\text{out}} = 10.64\text{ psi} \times 71.99\text{ ft/min} \approx \mathbf{766.0\text{ psi}\cdot\text{ft/min}}$$

#### Material Selection Verdict
Standard unlubricated Acetal (Delrin) sleeve bearings possess a continuous limit of $PV_{\text{limit}} = 3000\text{ psi}\cdot\text{ft/min}$. Since the peak operating value ($PV_{\text{in}} = 2042.7\text{ psi}\cdot\text{ft/min}$) is safely below $3000\text{ psi}\cdot\text{ft/min}$, **Acetal resin** is selected as the self-lubricating bearing material.

---

### 3.2 Bearing Wall Thickness Stress Analysis

#### Knowns & Unknowns
* **Knowns:**
  * Internal Radius $r_i = d_{\text{in}} / 2 = 0.0625\text{ in}$
  * Internal Operating Pressure $P = 21.28\text{ psi}$
  * Yield Tensile Strength of Acetal $\sigma_y = 9500\text{ psi}$
  * Target Factor of Safety $SF = 2.0$
  * Allowable Tensile Stress $\sigma_{\text{allow}} = \sigma_y / SF = 4750\text{ psi}$
* **Unknowns:**
  * Minimum Outer Radius $r_{o,\text{min}}$
  * Minimum Wall Thickness $t_{\text{min}}$

#### FBD & Stress Distribution Model

#### Thick-Wall Pressure Vessel Equations
$$\sigma_{\text{allow}} = P \cdot \left(\frac{r_i^2 + r_o^2}{r_o^2 - r_i^2}\right)$$

$$r_{o,\text{min}} = r_i \cdot \sqrt{\frac{\sigma_{\text{allow}} + P}{\sigma_{\text{allow}} - P}}$$

$$t_{\text{min}} = r_{o,\text{min}} - r_i = r_i \cdot \left(\sqrt{\frac{\sigma_{\text{allow}} + P}{\sigma_{\text{allow}} - P}} - 1\right)$$

#### Numerical Calculation
$$t_{\text{min}} = 0.0625\text{ in} \cdot \left(\sqrt{\frac{4750 + 21.28}{4750 - 21.28}} - 1\right) = 0.0625 \cdot \left(\sqrt{\frac{4771.28}{4728.72}} - 1\right)$$

$$t_{\text{min}} = 0.0625 \cdot (\sqrt{1.0089998} - 1) = 0.0625 \cdot (1.0044898 - 1) \approx \mathbf{0.00028\text{ in}}$$

#### Design Conclusion & Off-the-Shelf Selection
The theoretical minimum wall thickness of $0.00028\text{ in}$ is unrealistically thin for manufacturing. Standard commercial off-the-shelf Acetal sleeve bearings with standard wall thicknesses ($t = 0.0625\text{ in}$) were selected from McMaster-Carr:
1. **Input Journal Bearing:** McMaster-Carr `#2610T1` Series ($\varnothing 0.125\text{"}\text{ ID} \times \varnothing 0.250\text{"}\text{ OD} \times 0.250\text{"}\text{ Length}$, Plain Acetal Sleeve)
2. **Output Journal Bearing:** McMaster-Carr `#2610T1` Series ($\varnothing 0.250\text{"}\text{ ID} \times \varnothing 0.375\text{"}\text{ OD} \times 0.250\text{"}\text{ Length}$, Plain Acetal Sleeve)
<img width="438" height="281" alt="image" src="https://github.com/user-attachments/assets/057ec7dd-160e-4e53-9d85-11fd58554c2d" />

---

## 4. Gearbox Housing & Parametric CAD Architecture

### 4.1 Housing Concept & Fastening Strategy
The gearbox housing consists of a two-piece horizontally split enclosure (Lower Base and Upper Cover) divided directly along the shaft centerlines. 

<img width="612" height="428" alt="image" src="https://github.com/user-attachments/assets/ee3e4514-4f78-4c95-ab72-8b8385e45d28" />

I deviated from the snap fit and decided to go with a press fit when it came time to CAD.

* **Interlocking Alignment:** A $0.040\text{ in}$ tongue-and-groove lip runs continuously around the split line to react all gear mesh shear loads and ensure bore concentricity.
* **Fastening:** Fastened securely via press-fit locating pins and corner fasteners/clamps.
* **Clearance Teardrop Cavity:** The internal gear cavity maintains a $0.0625\text{ in}$ ($1/16\text{"}$) radial gap around the addendum circles of both meshing gears.

### 4.2 Creo Master Relations Table
The complete Creo Parametric model is driven top-down using the following global relations:

```pro
/* Master Parameters */
P_D = 48.0
N_PINION = 18
N_GEAR = 48
WALL_THICKNESS = 0.125
GEAR_CLEARANCE = 0.0625

/* Kinematic Relations */
D_P_PINION = N_PINION / P_D
D_P_GEAR = N_GEAR / P_D
CENTER_DISTANCE = (D_P_PINION + D_P_GEAR) / 2.0

/* Addendum Outer Diameters */
D_O_PINION = (N_PINION + 2.0) / P_D
D_O_GEAR = (N_GEAR + 2.0) / P_D

/* Internal Teardrop Cavity Diameters */
PINION_CAVITY_DIA = D_O_PINION + (2.0 * GEAR_CLEARANCE)
GEAR_CAVITY_DIA = D_O_GEAR + (2.0 * GEAR_CLEARANCE)
```
<img width="526" height="398" alt="image" src="https://github.com/user-attachments/assets/a1f9493f-9ea9-4874-a750-10671481cfce" />
<img width="1280" height="764" alt="image" src="https://github.com/user-attachments/assets/83ec7bb6-06b6-48b5-8c06-bc1e25b0a70f" />

### Time Tracking Summary
I don't know how much time I spent on this... maybe 8 hours?

### Critical Lessons Learned & Corrected Mistakes
I learned that not having enough time to complete your assignments in the way you want to is a very bad thing.
