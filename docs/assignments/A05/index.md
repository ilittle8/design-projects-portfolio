# A5 – Bracket Design

## Objective
My primary objective in this project is to perform a comprehensive structural analysis and detailed design of a mounting bracket capable of supporting a static horizontal load applied symmetrically through a polyester strap assembly. I am determining the critical dimensions across five interconnected structural features, labeled Features A through E, by applying core principles of strength of materials to evaluate both strength and stiffness requirements. 

To achieve a complete design, I am conducting structural stress analyses across all features by tracing reaction forces sequentially to establish the minimum geometric dimensions needed to prevent material yielding under a specified safety factor of 4. Alongside the strength evaluations, I am performing stiffness analyses to define the minimum required dimensions that limit elastic deformation to a maximum threshold of 0.005 inches per feature. A key aspect of my approach involves mapping feature interdependencies and reaction forces, ensuring that equilibrium is preserved as reaction loads at upstream support boundaries transition into applied forces for downstream components. Ultimately, I am comparing the sizing results from both stress and stiffness constraints to identify the governing failure mode for each feature, which directly informs the final nominal geometry used in my CAD models.

## Analyze
### Stress Analysis
#### Feature A: Stress Analysis & Structural Sizing

I designed Feature A as the pin that held the strap assembly. In my model, I treated Feature A as a simple cantilever beam that was fixed at one end (where it connected to Feature B) and pulled down by a force at the free end.

To start off, I chose a force of $F = 670\text{ lbf}$, which fit in the required range of $500\text{ lbf}$ to $800\text{ lbf}$. I used a factor of safety of $SF = 4.0$. I picked Aluminum 6061-T6 for the material, which had a yield strength of $\sigma_y = 40,000\text{ psi}$ ($40\text{ ksi}$) and a stiffness modulus of $E = 10.0 \times 10^6\text{ psi}$. Dividing the yield strength by the safety factor gave my maximum allowed stress: $\sigma_{\text{allow}} = \frac{40,000\text{ psi}}{4} = 10,000\text{ psi}$. Based on the size of the strap and general clearance, I set the length of Feature A to $L = 2.00\text{ in}$.

My goal for this section was to find the maximum reaction moment $M_{\text{max}}$ at the base, the required section modulus $Z_{\text{req}}$ to prevent yielding, and the smallest pin radius $r_{\text{stress}}$ and diameter $d_{\text{stress}}$ I could safely use. I also calculated the reaction forces at the base ($R_{y,A}$ and $M_A$), since those passed directly into Feature B as its main load.

To keep the math clean, I made a few standard assumptions. I assumed Feature A acted like an ideal cantilever beam fixed firmly to Feature B. I modeled the full $670\text{ lbf}$ force as a point load right at the end of the pin ($x = L$). I treated the aluminum as uniform and elastic, and per the assignment rules, I assumed direct shear failure was not going to govern. I also assumed Feature A stayed a solid cylinder across its whole $2.00\text{-inch}$ length, and I ignored stress concentrations at the base joint for this basic sizing check.

Using simple statics, the vertical reaction force at the base had to equal the load going down: $\sum F_y = 0 \implies R_y - F = 0$, so $R_y = 670\text{ lbf}$. The maximum bending moment happened right at the wall ($x = 0$) and equaled the force times the length: $\sum M_{\text{base}} = 0 \implies M_{\text{max}} - F \cdot L = 0$, which gave $M_{\text{max}} = 670\text{ lbf} \times 2.00\text{ in} = 1,340\text{ lb}\cdot\text{in}$.

To figure out how thick the pin needed to be, I used the bending stress equation $\sigma_{\text{max}} = \frac{M_{\text{max}}}{Z}$. Setting the maximum stress equal to my allowed stress of $10,000\text{ psi}$ allowed me to solve for section modulus: $Z_{\text{req}} = \frac{M_{\text{max}}}{\sigma_{\text{allow}}} = \frac{1,340\text{ lb}\cdot\text{in}}{10,000\text{ psi}} = 0.1340\text{ in}^3$. For a round bar, the section modulus formula is $Z = \frac{\pi r^3}{4}$. Setting that equal to my required section modulus gave $\frac{\pi r^3}{4} = 0.1340\text{ in}^3$. Solving for the radius gave $r_{\text{stress}} = \left( \frac{4 \times 0.1340}{\pi} \right)^{1/3} \approx 0.5546\text{ in}$. Multiplying by two gave a minimum required diameter of $d_{\text{stress}} = \mathbf{1.109\text{ in}}$.

So, to keep Feature A from bending or yielding under load, the pin needed to be at least $1.109\text{ inches}$ thick. The reactions at the support—a $670\text{ lbf}$ vertical force and a $1,340\text{ lb}\cdot\text{in}$ moment—were then carried over to Feature B.

#### Feature B: Stress Analysis & Structural Sizing

Next up, I designed Feature B, which was the vertical bar connecting the pin (Feature A) to the main T-beam assembly. Following Appendix D in the assignment, I modeled Feature B as a bar in pure axial tension, pulled by the load coming from Feature A.

To keep everything consistent, I carried over my parameters from Feature A. I used the static force of $F = 670\text{ lbf}$ and a safety factor of $SF = 4.0$. Sticking with Aluminum 6061-T6, my material properties were a yield strength of $\sigma_y = 40,000\text{ psi}$ ($40\text{ ksi}$) and an elastic modulus of $E = 10.0 \times 10^6\text{ psi}$. Dividing yield strength by the safety factor gave my allowed tensile stress: $\sigma_{\text{allow}} = \frac{40,000\text{ psi}}{4} = 10,000\text{ psi}$. Based on the layout and strap clearance, I set the length of Feature B to $L_B = 3.00\text{ in}$.

My goal for Feature B was to find the internal tensile force $P_B$, the required cross-sectional area $A_{\text{req}}$ to avoid yielding, and the minimum thickness $t_{\text{stress}}$ I needed for the bar. I also calculated the reaction force at the top end, which transferred into Feature C as its main load.

Instead of going with a standard square bar, I decided to give Feature B a rectangular cross-section with a width equal to Feature A's diameter ($w_B = d_A = 1.109\text{ in}$). I chose this for two reasons: matching the width to Feature A made the joint flush and easier to CAD and machine, and spreading the load over a wider width allowed me to use a thinner piece of stock while keeping it structurally sound.

To keep the model simple, I made a few assumptions. I assumed Feature B acted as a straight bar pulled in pure vertical tension. I treated the load from Feature A as a static axial force of $P = 670\text{ lbf}$. Per the assignment guidelines, I ignored direct shear and buckling for this normal stress pass. I also assumed uniform material properties throughout and ignored stress concentrations at the joint for this initial pass.

Using statics along the vertical direction, $\sum F_y = 0 \implies R_{y,B} - P = 0$, so the internal tensile load was $P_B = 670\text{ lbf}$.

To find the minimum required thickness, I used the axial stress equation $\sigma = \frac{P}{A}$. Setting stress to my allowed value of $10,000\text{ psi}$ gave the required area: $A_{\text{req}} = \frac{670\text{ lbf}}{10,000\text{ psi}} = 0.0670\text{ in}^2$. Since area for a rectangle is $A = w_B \cdot t$, I plugged in my width of $1.109\text{ in}$ to solve for thickness: $t_{\text{stress}} = \frac{0.0670\text{ in}^2}{1.109\text{ in}} \approx \mathbf{0.0604\text{ in}}$.

In summary, with a width of $1.109\text{ in}$, Feature B only needed a thickness of $0.0604\text{ in}$ to handle the tensile stress without yielding. To keep the force path going, I transferred the $670\text{ lbf}$ tensile reaction force directly into Feature C as a center point load.

#### Feature C: Stress Analysis & Structural Sizing

Moving on to Feature C, I designed the bottom horizontal flange of the T-beam assembly. Per the assignment guidelines in Appendix D, I modeled Feature C as a simply supported beam with a central concentrated point load transferred directly from Feature B.

To keep my calculations consistent, I carried forward my parameters from the previous sections. I used the reaction force from Feature B as my central point load, $P_C = 670\text{ lbf}$, and kept my factor of safety at $SF = 4.0$. Sticking with Aluminum 6061-T6, the material properties remained a yield strength of $\sigma_y = 40,000\text{ psi}$ ($40\text{ ksi}$) and an elastic modulus of $E = 10.0 \times 10^6\text{ psi}$. Dividing the yield strength by the safety factor gave my allowable bending stress: $\sigma_{\text{allow}} = \frac{40,000\text{ psi}}{4} = 10,000\text{ psi}$. Based on the overall bracket geometry and span between the vertical web walls, I set the total span length of Feature C to $L_C = 4.00\text{ in}$.

My main goals for Feature C were to find the reaction forces at the two end supports ($R_1$ and $R_2$), the maximum internal bending moment $M_{\text{max}}$ occurring at mid-span, the required section modulus $Z_{\text{req}}$ to prevent yielding, and the minimum required flange thickness $t_{\text{stress}}$. I also needed to calculate the reaction forces at the outer supports to transfer downstream into Feature D.

For Feature C's cross-section, I gave it a rectangular profile with a width set equal to Feature B's width ($w_C = w_B = 1.109\text{ in}$). This maintained a uniform width along the entire bottom connection path, making it cleaner to model in CAD and easier to machine from standard flat stock.

To keep the analytical model clean, I made a few standard assumptions. I assumed Feature C acted as an ideal simply supported beam with simple pin/roller supports at its outer ends ($x = 0$ and $x = L_C$). I modeled the load transferred from Feature B as a static point load applied exactly at the midpoint ($x = \frac{L_C}{2} = 2.00\text{ in}$). I assumed the material was linear, elastic, isotropic, and homogeneous throughout, and per assignment rules, I assumed direct shear failure was non-governing. I also assumed Feature C maintained a constant rectangular cross-section across its span, and I ignored local stress concentrations at the load application point.

Using statics for a symmetric, simply supported beam, the reaction forces at each support split the load equally: $R_1 = R_2 = \frac{P_C}{2} = \frac{670\text{ lbf}}{2} = 335\text{ lbf}$. The maximum internal bending moment occurred directly under the central load ($x = \frac{L_C}{2}$) and equaled $M_{\text{max}} = \frac{P_C \cdot L_C}{4} = \frac{670\text{ lbf} \times 4.00\text{ in}}{4} = 670\text{ lb}\cdot\text{in}$.

To figure out the required thickness, I used the bending stress formula $\sigma = \frac{M_{\text{max}}}{Z}$. Setting the maximum bending stress equal to my allowed stress of $10,000\text{ psi}$ gave the required section modulus: $Z_{\text{req}} = \frac{M_{\text{max}}}{\sigma_{\text{allow}}} = \frac{670\text{ lb}\cdot\text{in}}{10,000\text{ psi}} = 0.0670\text{ in}^3$. For a solid rectangular cross-section, section modulus is defined as $Z = \frac{w_C \cdot t^2}{6}$. Setting my geometric section modulus equal to $Z_{\text{req}}$ gave $\frac{1.109 \cdot t^2}{6} = 0.0670\text{ in}^3$. Rearranging to solve for thickness yielded $t^2 = \frac{6 \times 0.0670}{1.109} \approx 0.3625\text{ in}^2$, which gave a minimum required thickness of $t_{\text{stress}} = \sqrt{0.3625} \approx \mathbf{0.602\text{ in}}$.

In summary, with a width of $1.109\text{ in}$ and a span of $4.00\text{ in}$, Feature C needed a minimum flange thickness of $0.602\text{ in}$ to handle the central bending moment without yielding. To keep the force path continuous, the reaction forces at each end support ($335\text{ lbf}$ each) will be transferred directly into Feature D.
## Decide


## Communicate

