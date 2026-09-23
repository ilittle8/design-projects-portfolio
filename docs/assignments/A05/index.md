
$w_{\text{min, stress}} = d_A + 0.268\text{ in} = 1.109\text{ in} + 0.268\text{ in} = \mathbf{1.377\text{ in}}$

 

#### b. Axial Deflection Verification
Verifying total elongation along the link length $L_{\text{link}} = 4.00\text{ in}$ using $\delta = \frac{F L}{A_{\text{net}} E}$:

$A_{\text{stiff, req}} = \frac{F \cdot L_{\text{link}}}{E \cdot \delta_{\text{max}}} = \frac{670\text{ lbf} \times 4.00\text{ in}}{(10.0 \times 10^6\text{ psi}) \times 0.005\text{ in}} = 0.0536\text{ in}^2$

Since $A_{\text{net, req, stress}} (0.0670\text{ in}^2) > A_{\text{stiff, req}} (0.0536\text{ in}^2)$, tensile stress governs the minimum required cross-sectional area. 

* **Final Selected Link Dimensions:** Width $w = 1.50\text{ in}$, Thickness $t = 0.25\text{ in}$, Length $L = 4.00\text{ in}$.

 

### 2. Fit Selection for Feature A (Running / Sliding Fit)

#### a. Design Process & Citation
* **Fit Class Selected:** **RC 4** (Close Running Fit) per **ANSI B4.1-1967 (R1987)** / *Machinery’s Handbook* (ANSI/ASME Standard Limits and Fits, pp. 646–660).
* **Rationale:** RC 4 fits are intended for accurate location and free running at low speeds under moderate loads without binding.
* **Tolerances (Nominal Diameter $d_A = 1.109\text{ in}$, Range: 1.00 – 1.20 in):**
  * **Hole (Link):** Class H8 $\Rightarrow +0.0012\text{ in} / -0.0000\text{ in}$ $\rightarrow \mathbf{1.1090\text{ in} \text{ to } 1.1102\text{ in}}$
  * **Shaft (Feature A Pin):** Class f7 $\Rightarrow -0.0010\text{ in} / -0.0018\text{ in}$ $\rightarrow \mathbf{1.1072\text{ in} \text{ to } 1.1080\ in}$

#### b. Manufacturing Technique & Standard Tables
* **Manufacturing Process:** Precision Reaming or CNC Boring for the internal link hole; Precision Cylindrical Grinding or Turning for Feature A pin.
* **Standard Limits Table Used:** *ANSI B4.1 Table 1: Standard Running and Sliding Fits (RC 4)*.

 

### 3. Fit Selection for 1-Inch Shaft (Light Assembly Pressure)

#### a. Design Process & Citation
* **Fit Class Selected:** **FN 1** (Light Drive Fit) per **ANSI B4.1-1967 (R1987)** / *Machinery’s Handbook* (ANSI/ASME Standard Limits and Fits, pp. 646–660).
* **Rationale:** FN 1 fits require light assembly pressure, providing semi-permanent assembly suitable for light section dynamic force transmission without slipping.
* **Tolerances (Nominal Diameter $d = 1.000\text{ in}$, Range: 0.95 – 1.19 in):**
  * **Hole (Link):** Class H7 $\Rightarrow +0.0008\text{ in} / -0.0000\text{ in}$ $\rightarrow \mathbf{1.0000\text{ in} \text{ to } 1.0008\text{ in}}$
  * **Shaft:** Class p6 $\Rightarrow +0.0014\text{ in} / +0.0009\text{ in}$ $\rightarrow \mathbf{1.0009\text{ in} \text{ to } 1.0014\text{ in}}$

#### b. Manufacturing Technique & Standard Tables
* **Manufacturing Process:** Precision Reaming / Broaching for the link hole; Precision Grinding for the 1-inch shaft. Assembly requires a arbor press or light hydraulic press.
* **Standard Limits Table Used:** *ANSI B4.1 Table 9: Force and Shrink Fits (FN 1)*.

## Communicate

