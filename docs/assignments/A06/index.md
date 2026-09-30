# A6 - Parametric Bracket & Linkage Design

## Objective

In this project, my primary objective was to transition my analytical calculations from Assignment 5 into a fully parametric 3D CAD model and complete engineering drawing set using PTC Creo Parametric. Building upon my strength and stiffness sizing for Features A through E, I modeled the bracket dynamically using CAD relations and parameters to automatically control geometry based on underlying mechanics equations. Additionally, I designed a connecting link that mates directly with the Feature A pin, establishing appropriate ANSI/ASME limits and fits to ensure part-to-part compatibility, proper assembly function, and accurate draft manufacturing callouts.

All CAD part files and drawing packages are available for download here: 

<img width="1280" height="764" alt="Screenshot 2026-09-30 170402" src="https://github.com/user-attachments/assets/b0784a32-f790-4b89-8002-7e4d2b9a1abe" />


## Parametric Design

I mapped each dimension from my prior stress and stiffness analyses into global parameters within PTC Creo Parametric, driving the 3D geometry using explicit mathematical relations rather than static hardcoded values.

<img width="1280" height="764" alt="Screenshot 2026-09-30 170506" src="https://github.com/user-attachments/assets/73147e4e-064b-4e94-95ff-ab7ef044b0bc" />



### CAD Parameter Setup & Relations

To automate design updates, I defined global parameters for material properties ($\sigma_y = 40,000\text{ psi}$, $E = 10.0 \times 10^6\text{ psi}$), safety factor ($SF = 4.0$), applied force ($F = 670\text{ lbf}$), and feature span lengths.

```ptc_creo
/* --- GLOBAL DESIGN PARAMETERS --- */
FORCE = 670.0               /* Applied strap load in lbf */
SF = 4.0                    /* Safety Factor */
SIGMA_Y = 40000.0           /* Material Yield Strength in psi */
E_MOD = 10000000.0          /* Elastic Modulus in psi */
DELTA_MAX = 0.005           /* Maximum allowable deflection in inches */

/* --- DERIVED ALLOWABLE STRESS --- */
SIGMA_ALLOW = SIGMA_Y / SF  /* Working stress = 10,000 psi */

/* --- FEATURE A: PIN DIAMETER (BENDING GOVERNED) --- */
L_A = 2.00
M_A = FORCE * L_A
Z_A_REQ = M_A / SIGMA_ALLOW
D_A = pow(((32.0 * Z_A_REQ) / pi), (1.0 / 3.0))

/* --- SHARED EXTRUSION WIDTH LINKAGE --- */
WIDTH = D_A                 /* Feature A diameter sets overall bracket width */

/* --- FEATURE B: TENSILE BAR THICKNESS (TENSILE STRESS GOVERNED) --- */
L_B = 3.00
P_B = FORCE
A_B_REQ = P_B / SIGMA_ALLOW
T_B = A_B_REQ / WIDTH

/* --- FEATURE C: FLANGE THICKNESS (BENDING STRESS GOVERNED) --- */
L_C = 4.00
M_C = (FORCE * L_C) / 4.0
Z_C_REQ = M_C / SIGMA_ALLOW
T_C = sqrt((6.0 * Z_C_REQ) / WIDTH)

/* --- FEATURE D: WEB WALL THICKNESS (COMPRESSIVE STRESS GOVERNED) --- */
L_D = 3.00
P_D = FORCE / 2.0
A_D_REQ = P_D / SIGMA_ALLOW
T_D = A_D_REQ / WIDTH

/* --- FEATURE E: TOP LIP THICKNESS (BEARING STRESS GOVERNED) --- */
L_E = 0.50
P_E = FORCE / 2.0
A_E_REQ = P_E / SIGMA_ALLOW
T_E = A_E_REQ / WIDTH

/* --- BINDING PARAMETERS TO MODEL DIMENSIONS --- */
d63 = D_A       /* Pin Diameter = 1.109 in */
d5  = WIDTH     /* Extrusion Width = 1.109 in */
d1  = T_B       /* Tension Bar Thickness = 0.0604 in */
d2  = T_C       /* Flange Thickness = 0.602 in */
d3  = T_D       /* Web Wall Thickness = 0.0302 in */
d4  = T_E       /* Top Lip Thickness = 0.0302 in */

```

### Parametric CAD Dimension Table

| Parameter / Feature | Analytical Governing Equation | Driving Variable | Calculated / CAD Model Dimension |
| --- | --- | --- | --- |
| **Feature A Diameter** | $d_A = \left(\frac{32 \cdot M}{\pi \cdot \sigma_{\text{allow}}}\right)^{1/3}$ | `d63` | **1.109 in** |
| **Bracket Extrusion Width** | $w = d_A$ | `d5` | **1.109 in** |
| **Feature B Thickness** | $t_B = \frac{P_B}{\sigma_{\text{allow}} \cdot w}$ | `d1` | **0.0604 in**|
| **Feature C Thickness** | $t_C = \sqrt{\frac{6 \cdot M_C}{w \cdot \sigma_{\text{allow}}}}$ | `d2` | **0.602 in** |
| **Feature D Wall Thickness** | $t_D = \frac{P_D}{\sigma_{\text{allow}} \cdot w}$ | `d3` | **0.0302 in** |
| **Feature E Lip Thickness** | $t_E = \frac{P_E}{\sigma_{\text{allow}} \cdot w}$ | `d4` | **0.0302 in** |

---

## Engineering Drawings & Tolerancing

I generated multi-view engineering drawings for both the primary bracket assembly and the connecting link in PTC Creo Parametric, adhering strictly to ASME Y14.5 standards and third-angle projection conventions.


[AO6 Drawing.pdf](https://github.com/user-attachments/files/32878415/AO6.Drawing.pdf)
[Linkage AO6.pdf](https://github.com/user-attachments/files/32879197/Linkage.AO6.pdf)

### Bracket Drawing Specifications

* **Projection:** Third Angle Projection
* **Standard Tolerance Block:**
* `X.X` $\pm .02$
* `X.XX` $\pm .01$
* `X.XXX` $\pm .005$


* **Critical Sliding Fits (T-Beam Interface):**
* Three sliding fit interfaces guide the bracket over the rigid T-beam structure.
* Internal channel clearance gap: $1.108\text{ in} {}_{-0.000}^{+0.005}\text{ in}$ to maintain precision alignment while preventing dynamic binding.


### Linkage Design & CAD Modeling

I modeled a connecting link to transmit the horizontal force ($F = 670\text{ lbf}$) from the external strap to the Feature A pin.

<img width="1280" height="764" alt="Screenshot 2026-09-30 181646" src="https://github.com/user-attachments/assets/c90766b3-8775-45af-afe2-a56e31369f1a" />


* **Link Width ($w$):** $1.50\text{ in}$ (Net width across critical hole section $w_{\text{min}} = 1.377\text{ in}$)[
* **Link Thickness ($t$):** $0.25\text{ in}$ (Standard plate stock)
* **Center-to-Center Length ($L$):** $4.00\text{ in}$
* **Feature A Pin Interface Fit:** ANSI RC 4 (Close Running Fit) for $d_A = 1.109\text{ in}$.
* **Hole Callout (Link):** $\varnothing 1.1090\text{ in} {}_{-0.0000}^{+0.0012}\text{ in}$ (Class H8)
* **Shaft Callout (Pin):** $\varnothing 1.1080\text{ in} {}_{-0.0018}^{-0.0010}\text{ in}$ (Class f7)


* **Shaft 2 Interface Fit:** ANSI FN 1 (Light Press / Force Fit) for $d = 1.000\text{ in}$.
* **Hole Callout:** $\varnothing 1.0000\text{ in} {}_{-0.0000}^{+0.0008}\text{ in}$
* **Shaft Callout:** $\varnothing 1.0012\text{ in} {}_{-0.0000}^{+0.0006}\text{ in}$

<img width="1280" height="764" alt="Screenshot 2026-09-30 181745" src="https://github.com/user-attachments/assets/7b9c8a15-c2c5-45d2-ae61-e7fa00cbea74" />


---

## Reflections & Lessons Learned

### Actual Time Investment

* **Parametric Model & Relations Setup:** 2.5 hours
* **Linkage Modeling & ANSI Fit Selection:** 1.5 hours
* **Multi-View Drawings & GD&T Setup:** 2.0 hours
* **Total Time:** **6.0 hours**

### 1. Parametric Equation Integration & Model Response

I used the flexural stress equation for a circular cantilever beam, $d = \left(\frac{32 M}{\pi \sigma_{\text{allow}}}\right)^{1/3}$, directly within Creo's Relations editor to drive the parameter `D_A` (`d63`), which represents Feature A's pin diameter. Rather than manually inputting the calculated $1.109\text{ in}$ nominal value, I bound `D_A` directly to the applied load parameter `FORCE` ($670\text{ lbf}$) and safety factor `SF` ($4.0$). When I tested increasing the applied force from $670\text{ lbf}$ to $800\text{ lbf}$ during initial verification, the parameter `D_A` expanded automatically upon model regeneration (`Ctrl + G`). Because overall extrusion width `WIDTH` (`d5`) was linked to `D_A`, downstream thicknesses for Features B, C, D, and E dynamically adjusted without requiring manual sketch edits or manual rework.

### 2. Functional Tolerancing & Cost vs. Manufacturability

* **Tighter Tolerance Class (`X.XXX` $\pm .005$ / ANSI Fits):** I applied tight tolerances to the internal channel dimensions mating with the T-beam  and the Feature A pin hole . These represent critical functional surfaces where excessive play causes dynamic binding, misalignment, or fatigue failure under oscillating strap loads.
* **Looser Tolerance Class (`X.X` $\pm .02$ / `X.XX` $\pm .01$):** I applied looser tolerances to non-critical external boundary dimensions, such as the total overall length of the upper flanges
* **Manufacturing Impact:** Applying the tightest tolerance ($\pm .005\text{ in}$ or precision reaming) across non-critical outer edges exponentially increases fabrication costs. It forces machinists to use slow finish passes, precision grinding equipment, and frequent tool changes instead of high-speed rough milling. This dramatically increases scrap rates without providing any functional benefit to assembly performance.

### 3. Part-to-Part Compatibility & GD&T Communication

Designing the link and bracket interface demonstrated how dimensioning and tolerancing communicate functional design intent. Specifying an RC 4 fit ensures that the link can rotate freely around the Feature A pin during strap angle changes without binding, while maintaining a sufficiently tight clearance to avoid localized point-impact loading. GD&T callouts act as an unambiguous language between the design engineer and the machine shop, ensuring parts manufactured in separate facilities assemble seamlessly without manual post-machining or custom fitting

# CAD model Downloads
https://github.com/ilittle8/design-projects-portfolio/blob/main/docs/assignments/A06/a05a06.prt.3
