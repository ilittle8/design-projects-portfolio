# A5 – Bracket Design

## Objective
My primary objective in this project is to perform a comprehensive structural analysis and detailed design of a mounting bracket capable of supporting a static horizontal load applied symmetrically through a polyester strap assembly. I am determining the critical dimensions across five interconnected structural features, labeled Features A through E, by applying core principles of strength of materials to evaluate both strength and stiffness requirements. The intended design is shown below:

<img width="382" height="345" alt="image" src="https://github.com/user-attachments/assets/9fa9c3e5-c1e2-4d57-892d-3b22d9cebb5e" />


To achieve a complete design, I am conducting structural stress analyses across all features by tracing reaction forces sequentially to establish the minimum geometric dimensions needed to prevent material yielding under a specified safety factor of 4. Alongside the strength evaluations, I am performing stiffness analyses to define the minimum required dimensions that limit elastic deformation to a maximum threshold of 0.005 inches per feature. A key aspect of my approach involves mapping feature interdependencies and reaction forces, ensuring that equilibrium is preserved as reaction loads at upstream support boundaries transition into applied forces for downstream components. Ultimately, I am comparing the sizing results from both stress and stiffness constraints to identify the governing failure mode for each feature, which directly informs the final nominal geometry used in my CAD models.

## Analyze
# Feature A: Stress & Stiffness Analysis

I designed Feature A as the pin that held the strap assembly. In my model, I treated Feature A as a solid circular cantilever beam fixed at its base connection with Feature B and subjected to a transverse point load at its free end.

To start off, I selected a static applied force of $F = 670\text{ lbf}$ (within the $500\text{ lbf}$ to $800\text{ lbf}$ range) and used a factor of safety of $SF = 4.0$. I chose Aluminum 6061-T6 for the material, which provided a yield strength of $\sigma_y = 40,000\text{ psi}$ ($40\text{ ksi}$) and an elastic modulus of $E = 10.0 \times 10^6\text{ psi}$. Dividing yield strength by the safety factor gave my allowable bending stress: $\sigma_{\text{allow}} = \frac{40,000\text{ psi}}{4} = 10,000\text{ psi}$. Based on strap width and mounting clearance, I set the pin length to $L_A = 2.00\text{ in}$. For stiffness, I established a maximum allowable deflection limit of $\delta_{\text{max}} = 0.005\text{ in}$.

My goal for Feature A was to calculate the base reaction force ($R_y = 670\text{ lbf}$) and maximum moment ($M_{\text{max}} = 1,340\text{ lb}\cdot\text{in}$), determine the stress-based minimum diameter $d_{\text{stress}}$, and calculate the stiffness-based minimum diameter $d_{\text{stiff}}$ based on tip deflection.

I assumed Feature A acted as an ideal cantilever beam fixed firmly to Feature B, with the force applied as a point load at $x = L_A$. I treated the material as linear, elastic, isotropic, and homogeneous, and assumed direct shear failure was non-governing.

## Bending Stress Analysis
The maximum bending moment occurred at the support wall ($x = 0$):
$M_{\text{max}} = F \cdot L_A = 670\text{ lbf} \times 2.00\text{ in} = 1,340\text{ lb}\cdot\text{in}$

Setting maximum bending stress equal to my allowable stress ($\sigma = \frac{M}{Z} = \sigma_{\text{allow}}$):
$Z_{\text{req}} = \frac{M_{\text{max}}}{\sigma_{\text{allow}}} = \frac{1,340\text{ lb}\cdot\text{in}}{10,000\text{ psi}} = 0.1340\text{ in}^3$

For a solid cylinder, $Z = \frac{\pi r^3}{4}$. Solving for required radius and diameter:
$r_{\text{stress}} = \left( \frac{4 \cdot Z_{\text{req}}}{\pi} \right)^{1/3} = \left( \frac{4 \times 0.1340}{\pi} \right)^{1/3} \approx 0.5546\text{ in}$
$d_{\text{stress}} = 2 \cdot r_{\text{stress}} = \mathbf{1.109\text{ in}}$

## Stiffness Analysis
The maximum end deflection for a cantilever beam under a point load is given by:
$\delta_{\text{max}} = \frac{F \cdot L_A^3}{3 E I}$

Setting deflection equal to my allowable limit $\delta_{\text{max}} = 0.005\text{ in}$ and solving for required moment of inertia $I_{\text{req}}$:
$I_{\text{req}} = \frac{F \cdot L_A^3}{3 E \cdot \delta_{\text{max}}} = \frac{670 \times (2.00)^3}{3 \times (10.0 \times 10^6) \times 0.005} = 0.03573\text{ in}^4$

For a solid circular cross-section, $I = \frac{\pi d^4}{64}$. Solving for required diameter:
$d_{\text{stiff}} = \left( \frac{64 \cdot I_{\text{req}}}{\pi} \right)^{1/4} = \left( \frac{64 \times 0.03573}{\pi} \right)^{1/4} \approx \mathbf{0.923\text{ in}}$

Comparing both analyses, the bending stress criteria governed ($1.109\text{ in} > 0.923\text{ in}$), so I selected a final pin diameter of **$d_A = 1.109\text{ in}$**.

 

# Feature B: Stress & Stiffness Analysis

Next, I designed Feature B, the vertical intermediate bar connecting the pin (Feature A) to the main T-beam assembly. Per Appendix D guidelines, I modeled Feature B as an axially loaded bar in pure vertical tension under the $670\text{ lbf}$ load transferred from Feature A.

I carried over my parameters: $F = 670\text{ lbf}$, $SF = 4.0$, Aluminum 6061-T6 ($\sigma_y = 40,000\text{ psi}$, $E = 10.0 \times 10^6\text{ psi}$), and $\sigma_{\text{allow}} = 10,000\text{ psi}$. I set the length of Feature B to $L_B = 3.00\text{ in}$ and set the axial elongation limit to $\delta_{\text{max}} = 0.005\text{ in}$.

To create a clean geometric transition, I selected a rectangular cross-section with width equal to Feature A's diameter ($w_B = d_A = 1.109\text{ in}$).

I assumed Feature B acted as a straight bar loaded in pure uniaxial vertical tension, neglecting bending moments and buckling modes per project guidelines.

## Normal Tensile Stress Analysis
Using vertical equilibrium, the internal tensile force was $P_B = 670\text{ lbf}$. The required area to prevent yield failure was:
$A_{\text{req}} = \frac{P_B}{\sigma_{\text{allow}}} = \frac{670\text{ lbf}}{10,000\text{ psi}} = 0.0670\text{ in}^2$

With fixed width $w_B = 1.109\text{ in}$, the stress-based minimum thickness was:
$t_{\text{stress}} = \frac{A_{\text{req}}}{w_B} = \frac{0.0670\text{ in}^2}{1.109\text{ in}} \approx \mathbf{0.0604\text{ in}}$

## Axial Stiffness Analysis
The total axial elongation of a uniform bar under tension is:
$\delta = \frac{P_B \cdot L_B}{A \cdot E}$

Setting elongation to my limit $\delta_{\text{max}} = 0.005\text{ in}$ and solving for required cross-sectional area:
$A_{\text{stiff}} = \frac{P_B \cdot L_B}{E \cdot \delta_{\text{max}}} = \frac{670\text{ lbf} \times 3.00\text{ in}}{(10.0 \times 10^6\text{ psi}) \times 0.005\text{ in}} = 0.0402\text{ in}^2$

Solving for stiffness-based thickness:
$t_{\text{stiff}} = \frac{A_{\text{stiff}}}{w_B} = \frac{0.0402\text{ in}^2}{1.109\text{ in}} \approx \mathbf{0.0362\text{ in}}$

Comparing both results, tensile stress governed ($0.0604\text{ in} > 0.0362\text{ in}$), requiring a minimum thickness of **$t_B = 0.0604\text{ in}$**.

 

# Feature C: Stress & Stiffness Analysis

Moving on to Feature C, I designed the bottom horizontal flange of the T-beam assembly. Per Appendix D, I modeled Feature C as a simply supported beam with a central point load $P_C = 670\text{ lbf}$ transferred directly from Feature B.

I carried forward $P_C = 670\text{ lbf}$, $SF = 4.0$, Aluminum 6061-T6 ($\sigma_{\text{allow}} = 10,000\text{ psi}$, $E = 10.0 \times 10^6\text{ psi}$), span length $L_C = 4.00\text{ in}$, and fixed cross-sectional width $w_C = 1.109\text{ in}$. My allowable mid-span deflection limit was set to $\delta_{\text{max}} = 0.005\text{ in}$.

I assumed Feature C acted as an ideal simply supported beam with simple end supports and a central static point load, neglecting direct shear.

## Bending Stress Analysis
The support reactions were $R_1 = R_2 = 335\text{ lbf}$. The maximum bending moment at mid-span was:
$M_{\text{max}} = \frac{P_C \cdot L_C}{4} = \frac{670\text{ lbf} \times 4.00\text{ in}}{4} = 670\text{ lb}\cdot\text{in}$

The required section modulus was:
$Z_{\text{req}} = \frac{M_{\text{max}}}{\sigma_{\text{allow}}} = \frac{670\text{ lb}\cdot\text{in}}{10,000\text{ psi}} = 0.00670\text{ in}^3 \rightarrow 0.0670\text{ in}^3$

For a rectangular section ($Z = \frac{w_C \cdot t^2}{6}$), solving for stress-based thickness yielded:
$t_{\text{stress}} = \sqrt{\frac{6 \cdot Z_{\text{req}}}{w_C}} = \sqrt{\frac{6 \times 0.0670}{1.109}} \approx \mathbf{0.602\text{ in}}$

## Bending Stiffness Analysis
The maximum center deflection for a simply supported beam under a central point load is:
$\delta_{\text{max}} = \frac{P_C \cdot L_C^3}{48 E I}$

Setting deflection to $0.005\text{ in}$ and solving for required moment of inertia $I_{\text{req}}$:
$I_{\text{req}} = \frac{P_C \cdot L_C^3}{48 E \cdot \delta_{\text{max}}} = \frac{670 \times (4.00)^3}{48 \times (10.0 \times 10^6) \times 0.005} = 0.01787\text{ in}^4$

For a rectangular section, $I = \frac{w_C \cdot t^3}{12}$. Solving for stiffness-based thickness:
$t_{\text{stiff}} = \left( \frac{12 \cdot I_{\text{req}}}{w_C} \right)^{1/3} = \left( \frac{12 \times 0.01787}{1.109} \right)^{1/3} \approx \mathbf{0.578\text{ in}}$

Comparing both, bending stress governed ($0.602\text{ in} > 0.578\text{ in}$), requiring a minimum flange thickness of **$t_C = 0.602\text{ in}$**.

 

# Feature D: Stress & Stiffness Analysis

Next, I analyzed Feature D, representing the vertical web walls supporting Feature C. Due to symmetry, the $670\text{ lbf}$ load split equally between the two walls, so each wall carried a compressive load of $P_D = 335\text{ lbf}$.

I carried over $P_D = 335\text{ lbf}$, $SF = 4.0$, Aluminum 6061-T6 ($\sigma_{\text{allow}} = 10,000\text{ psi}$, $E = 10.0 \times 10^6\text{ psi}$), wall height $L_D = 3.00\text{ in}$, and width $w_D = 1.109\text{ in}$. My allowable compressive shortening limit was $\delta_{\text{max}} = 0.005\text{ in}$.

I assumed Feature D acted as a straight bar loaded in pure vertical compression, neglecting buckling modes per project guidelines.

## Normal Compressive Stress Analysis
Equilibrium gave an internal compressive force of $P_D = 335\text{ lbf}$. The required area was:
$A_{\text{req}} = \frac{P_D}{\sigma_{\text{allow}}} = \frac{335\text{ lbf}}{10,000\text{ psi}} = 0.0335\text{ in}^2$

Solving for minimum stress-based wall thickness:
$t_{\text{stress}} = \frac{A_{\text{req}}}{w_D} = \frac{0.0335\text{ in}^2}{1.109\text{ in}} \approx \mathbf{0.0302\text{ in}}$

## Compressive Stiffness Analysis
The total compressive axial deflection is given by:
$\delta = \frac{P_D \cdot L_D}{A \cdot E}$

Setting deflection to $\delta_{\text{max}} = 0.005\text{ in}$ and solving for required area:
$A_{\text{stiff}} = \frac{P_D \cdot L_D}{E \cdot \delta_{\text{max}}} = \frac{335\text{ lbf} \times 3.00\text{ in}}{(10.0 \times 10^6\text{ psi}) \times 0.005\text{ in}} = 0.0201\text{ in}^2$

Solving for stiffness-based wall thickness:
$t_{\text{stiff}} = \frac{A_{\text{stiff}}}{w_D} = \frac{0.0201\text{ in}^2}{1.109\text{ in}} \approx \mathbf{0.0181\text{ in}}$

Comparing both results, compressive stress governed ($0.0302\text{ in} > 0.0181\text{ in}$), requiring a minimum wall thickness of **$t_D = 0.0302\text{ in}$**.


# Feature E: Stress & Stiffness Analysis

Finally, I analyzed Feature E, representing the top mounting flange connecting flush against the rigid body. I modeled Feature E as a contact surface subjected to direct bearing compression under $P_E = 335\text{ lbf}$ per side ($670\text{ lbf}$ total).

I carried over $P_E = 335\text{ lbf}$, $SF = 4.0$, Aluminum 6061-T6 ($\sigma_{\text{allow}} = 10,000\text{ psi}$, $E = 10.0 \times 10^6\text{ psi}$), and contact width $w_E = 1.109\text{ in}$. I set the maximum allowable compression strain/deflection limit across the joint thickness $L_E = 0.50\text{ in}$ to $\delta_{\text{max}} = 0.005\text{ in}$.

I assumed Feature E rested flush against the rigid support, transferring force in pure bearing compression.

## Bearing Stress Analysis
Equilibrium gave a compressive reaction force of $R_E = 335\text{ lbf}$ per side. The required contact area was:
$A_{\text{req}} = \frac{P_E}{\sigma_{\text{allow}}} = \frac{335\text{ lbf}}{10,000\text{ psi}} = 0.0335\text{ in}^2$

Solving for stress-based flange thickness:
$t_{\text{stress}} = \frac{A_{\text{req}}}{w_E} = \frac{0.0335\text{ in}^2}{1.109\text{ in}} \approx \mathbf{0.0302\text{ in}}$

## Compressive Stiffness Analysis
Treating compressive deflection across the contact interface length ($L_E = 0.50\text{ in}$ assumed lip length):
$\delta = \frac{P_E \cdot L_E}{A \cdot E}$

Solving for required area under $\delta_{\text{max}} = 0.005\text{ in}$:
$A_{\text{stiff}} = \frac{P_E \cdot L_E}{E \cdot \delta_{\text{max}}} = \frac{335\text{ lbf} \times 0.50\text{ in}}{(10.0 \times 10^6\text{ psi}) \times 0.005\text{ in}} = 0.00335\text{ in}^2$

Solving for stiffness-based thickness:
$t_{\text{stiff}} = \frac{A_{\text{stiff}}}{w_E} = \frac{0.00335\text{ in}^2}{1.109\text{ in}} \approx \mathbf{0.0030\text{ in}}$

Comparing both results, bearing stress governed ($0.0302\text{ in} > 0.0030\text{ in}$), requiring a minimum flange thickness of **$t_E = 0.0302\text{ in}$**.

# Generate Multiview Sketches
I ten created a multiview sketch for both designs and toleranced it.

## Decide

### 1. Governing Failure Mode Analysis
Across all five analyzed features, bending and tensile stress criteria consistently governed over deflection and stiffness criteria. 

* **Feature A (Pin Cantilever Bending):** Bending stress required a minimum diameter of $d_{\text{stress}} = 1.109\text{ in}$, whereas deflection constraints ($\delta_{\text{max}} = 0.005\text{ in}$) only required $d_{\text{stiff}} = 0.923\text{ in}$. Bending stress governed by a difference of $0.186\text{ in}$ ($\sim 20.1\%$ larger).
* **Feature C (Flange Bending):** Bending stress required a thickness of $t_{\text{stress}} = 0.602\text{ in}$, while deflection stiffness required $t_{\text{stiff}} = 0.578\text{ in}$. This was a **near-tie**, with stress governing by only $0.024\text{ in}$ ($\sim 4.15\%$). This close margin highlights that for relatively short, thick beam spans ($L_C = 4.00\text{ in}$ with high moment of inertia), flexural stiffness requirements closely track stress limits under tight displacement constraints.

 

### 2. Error Propagation & Downstream Traceability
A critical instance of parameter propagation occurred between **Feature A** and all subsequent components (**Features B through E**). 

* **Sequential Linkage:** The solved stress-governed diameter of Feature A ($d_A = 1.109\text{ in}$) was selected as the fixed nominal cross-sectional width ($w$) for Features B, C, D, and E to maintain visual geometric continuity and clean mounting transitions.
* **Impact of Upstream Catch:** An initial sizing check on Feature A ensured that $d_A$ was set to the larger stress requirement ($1.109\text{ in}$) rather than the stiffness requirement ($0.923\text{ in}$). Had the smaller $0.923\text{ in}$ diameter been carried downstream as width $w$, the required thickness values for downstream features would have increased across the board (e.g., Feature C stress thickness would have jumped from $0.602\text{ in}$ to $\approx 0.660\text{ in}$ to compensate for the narrower section modulus $Z$).

 

### 3. Assumption Sensitivity Analysis
* **Assumption Tested:** Ideal load distribution and negligible bending moments in **Feature B** (modeled as a pure uniaxial tension bar under $P_B = 670\text{ lbf}$).
* **Sensitivity & Impact:** In practice, because Feature A acts as a cantilever beam, the load transferred to Feature B creates an eccentric moment ($M = F \cdot L_A$) at the connection joint rather than pure tension. 
* **Dimension Change:** If joint bending were incorporated into Feature B instead of treating it purely in tension ($\sigma = P/A$), combined axial loading and bending stress ($\sigma_{\text{comb}} = \frac{P}{A} + \frac{M y}{I}$) would significantly increase the required thickness $t_B$ from the baseline calculated value of $0.0604\text{ in}$ to prevent localized combined yielding at the bracket transition corner.

## Linkage & Fits Analysis

### 1. Linkage Sizing & Stress/Stiffness Analysis

#### Knowns & Assumptions
In this analysis, I evaluated a pure tensile load of $F = 670\text{ lbf}$ pulling directly through the linkage component. I selected Aluminum 6061-T6 for the material ($\sigma_y = 40,000\text{ psi}$, $E = 10.0 \times 10^6\text{ psi}$) and applied a safety factor of $SF = 4.0$, which sets my maximum allowable working stress to $\sigma_{\text{allow}} = 10,000\text{ psi}$. For design limits, I set the maximum allowable elongation to $\delta_{\text{max}} = 0.005\text{ in}$. My key dimensions include a Feature A pin diameter of $d_A = 1.109\text{ in}$, a Shaft 2 diameter of $d_{\text{shaft}} = 1.000\text{ in}$, and a center-to-center link length of $L_{\text{link}} = 4.00\text{ in}$. Following standard preliminary design guidelines, I simplified section sizing by setting aside localized stress concentrations around the hole edges for now.

#### a. Stress Analysis at Critical Hole Sections
To determine the required width, I checked the most critical cross-section where the link is thinnest—across the hole diameter:

$A_{\text{net}} = (w - d) \cdot t$

Hole A ($d_A = 1.109\text{ in}$) is my governing section because removing this hole cuts away the most material across the width. Using my allowable stress limit:

$\sigma_{\text{allow}} = \frac{F}{A_{\text{net}}} = \frac{F}{(w - d_A) \cdot t}$

I calculated that I need a minimum net cross-sectional area of $A_{\text{net, req}} = \frac{670\text{ lbf}}{10,000\text{ psi}} = 0.0670\text{ in}^2$. Choosing a standard stock plate thickness of $t = 0.25\text{ in}$, I found I need an extra width beyond the hole of:

$w - d_A = \frac{0.0670\text{ in}^2}{0.25\text{ in}} = 0.268\text{ in}$

Adding this back to the hole size gives me a minimum stress-governed link width of $w_{\text{min, stress}} = 1.109\text{ in} + 0.268\text{ in} = \mathbf{1.377\text{ in}}$ to safely withstand pulling stresses.

#### b. Axial Deflection Verification
Next, I verified whether stretching along the length $L_{\text{link}} = 4.00\text{ in}$ would exceed my deflection limit using the axial stiffness formula:

$\delta = \frac{F \cdot L}{A_{\text{net}} \cdot E}$

Solving for the required stiffness area:

$A_{\text{stiff, req}} = \frac{670\text{ lbf} \times 4.00\text{ in}}{(10.0 \times 10^6\text{ psi}) \times 0.005\text{ in}} = 0.0536\text{ in}^2$

Because my strength requirement ($0.0670\text{ in}^2$) is larger than my stiffness requirement ($0.0536\text{ in}^2$), tensile stress governs the final design. To ensure a safe and practical margin, I selected final nominal link dimensions of **$w = 1.50\text{ in}$ wide**, **$t = 0.25\text{ in}$ thick**, and **$L = 4.00\text{ in}$ long**.

### 2. Fit Selection for Feature A (Running / Sliding Fit)

#### a. Design Process & Citation
I selected a Close Running Fit (**RC 4**) based on **ANSI B4.1-1967 (R1987)** standards from the *Machinery’s Handbook* (ANSI/ASME Standard Limits and Fits, pp. 646–660). I chose an RC 4 fit because it provides accurate location and allows smooth rotational motion at low speeds under moderate loads without binding. For my $d_A = 1.109\text{ in}$ nominal pin diameter (falling in the $1.00–1.20\text{ in}$ range), I specified a **Class H8** tolerance ($+0.0012\text{ in} / -0.0000\text{ in}$) for the link hole, giving an acceptable hole size of **$1.1090\text{ in}$ to $1.1102\text{ in}$**. For the Feature A pin shaft, I specified a **Class f7** tolerance ($-0.0010\text{ in} / -0.0018\text{ in}$), which sets the shaft size between **$1.1072\text{ in}$ and $1.1080\text{ in}$**.

#### b. Manufacturing Technique & Standard Tables
To achieve these precise fits during fabrication, I specified precision reaming or CNC boring for the internal link hole, and precision cylindrical grinding or turning for the Feature A pin. I pulled all dimensional limits directly from *ANSI B4.1 Table 1: Standard Running and Sliding Fits (RC 4)*.

### 3. Fit Selection for 1-Inch Shaft (Light Assembly Pressure)

#### a. Design Process & Citation
For the $d = 1.000\text{ in}$ Shaft 2, I selected a Light Drive Fit (**FN 1**) per **ANSI B4.1-1967 (R1987)** standards from the *Machinery’s Handbook* (ANSI/ASME Standard Limits and Fits, pp. 646–660). I chose FN 1 because it requires light press-fit force during assembly, creating a semi-permanent joint that reliably transmits dynamic force without slipping under load. I applied standard table limits for the $1.000\text{ in}$ nominal diameter range ($0.95–1.19\text{ in}$) to define the exact shaft and housing manufacturing tolerances.

## Communicate
