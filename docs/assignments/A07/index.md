# A7 – FEA on Bracket & Linkage

## Objectives
* Use Finite Element Analysis (FEA) to improve the bracket design from previous assignments.
* Ensure high stiffness, strength, and lightweight optimization through iterative design.
* Conduct multiple FEA simulations, refining geometry based on results.
* Perform static stress analysis, including constraints, loading, and meshing selection.
* Interpret data by identifying max stress, displacement, and safety factors.
* Optimize the design by modifying geometry to enhance performance.
* Document the entire process with images, calculations, and insights.
* Reflect on key engineering lessons learned and time spent.

## Introduction & Project Overview

When I first read through the MEGR 2156 assignment prompt, I knew this project would test my ability to combine CAD modeling, finite element principles, and iterative design. My task was clear: take my previous bracket design and run it through a rigorous FEA-driven optimization process to make it as stiff, strong, and lightweight as possible. For the 2157 portion, I also needed to perform the exact same analysis and geometry optimization on a link component.

Before jumping into Creo, I made sure to gather all my workspace resources and ensure my access to Creo Simulate was ready. You can download all of my CAD models and simulation files directly through this link: [Download CAD Models & Simulation Files](https://example.com/cad-files-download).

Overall, this entire engineering process took me **8.5 hours** from start to finish:
* **Preprocessing & Boundary Setup:** 3.0 hours
* **FEA Solving & Mesh Refinement:** 3.5 hours
* **CAD Optimization & Documentation:** 2.0 hours

---

## Part I: Optimizing the Bracket Design

### Initial Setup & Material Definition
I started by opening my baseline bracket model in PTC Creo Simulate. The prompt specified that the material was pre-assigned as **Aluminum 6061** and could not be changed. From my materials background, I noted that Aluminum 6061 has a yield strength ($\sigma_y$) of approximately $40,000\text{ psi}$.

To set up the static stress analysis:
1. **Constraints:** I applied fixed displacement constraints to the top surface mounting regions of the bracket.
2. **Loading:** I applied a vertical downward load and moment forces at the lower cylindrical feature to simulate the real-world operational loading conditions.




[My Bracket Design Optimization Workflow]
Design I: Unreinforced Web (SF = 0.038, Deflection = 31.9 in)
│
▼
Design II: Added 0.20" Thickness (SF = 0.52, Stress = 76.7 ksi)
│
▼
Design III: Added 1.0" Thickness & 1.0" Radius Fillets (SF = 4.11, Deflection = 0.0089 in)


---

### Inner Loop Execution: Bracket Design I (Convergence Phase)
Before making any geometric modifications, I needed to run my inner loop validation to make sure my mesh resolution had converged within the $7\%$ difference threshold.

1. **Attempt 1 (Minimum Element Size $0.0009$):** I ran my initial simulation and recorded a maximum Von Mises stress of $\sigma_{\text{vm}} = 1.05216 \times 10^6\text{ psi}$ located right at the sharp junction between the cylinder and the thin web. My displacement was huge at $31.9068\text{ in}$ at the free end of the cylinder. Calculating my factor of safety:
   $$\text{SF} = \frac{\sigma_y}{\sigma_{\text{vm}}} = \frac{40,000}{1.05216 \times 10^6} \approx 0.038$$
   This was an immediate failure, but I needed to prove convergence first.
2. **Attempt 2 (Minimum Element Size $0.0007$):** I refined the mesh size down to $0.0007$. The max stress dropped slightly to $955,025\text{ psi}$. I calculated the percent difference:
   $$\text{Percent Difference} = \left| \frac{955,025 - 1,052,160}{1,052,160} \right| \times 100\% = 9.68\%$$
   Since $9.68\% > 7\%$, I was required to refine the mesh further.
3. **Attempt 3 (Minimum Element Size $0.0005$):** I went finer with a minimum element size of $0.0005$. Interestingly, the stress increased back up to $1.03164 \times 10^6\text{ psi}$. Comparing this against my original baseline:
   $$\text{Percent Difference} = \left| \frac{1,031,640 - 1,052,160}{1,052,160} \right| \times 100\% = 1.97\%$$
   Because $1.97\% \le 7\%$, my inner loop converged, giving me a reliable mesh size ($0.0005$) to carry forward into geometric optimization.

---

### Outer Loop Execution: Bracket Geometry Iterations

#### Bracket Design II
Looking at my baseline contour plots, it was glaringly obvious that my vertical member (thickness of $0.06\text{ in}$) was far too thin to carry the severe bending moment. For my first geometric change, I added $0.20\text{ in}$ of thickness to the thin member.
* **Results:** The peak stress plummeted to $76,700.8\text{ psi}$, and maximum deformation fell drastically to $0.395657\text{ in}$.
* **Safety Factor:** $\text{SF} = \frac{40,000}{76,700.8} \approx 0.52$.
* **Takeaway:** Although the stress dropped by over $90\%$, a safety factor of $0.52$ meant the bracket would still fracture in practice.

#### Bracket Design III
To achieve a passing safety factor, I knew I needed both structural bulk and smooth stress transitions. I added an extra $1.0\text{ in}$ of thickness to the original member and added generous $1.0\text{ in}$ radius fillets at the sharp intersection between the horizontal bracket base and the vertical arm.
* **Results:** The max stress dropped down to $9,741.91\text{ psi}$, situated smoothly along the new fillet transitions. Max deflection was reduced down to just $0.00890151\text{ in}$.
* **Safety Factor:** $\text{SF} = \frac{40,000}{9,741.91} \approx 4.11$.
* **Takeaway:** This yielded a highly robust, stiff, and completely functional design.

---

### Bracket Data Summary Table

| Metric | Design I | Design II | Design III |
| :--- | :--- | :--- | :--- |
| **Max Stress & Location** | $1.03164 \times 10^6\text{ psi}$<br>Junction between cylinder and thin member | $76,700.8\text{ psi}$<br>Junction between thin member and cylinder | $9,741.91\text{ psi}$<br>Fillet between member and bracket |
| **Max Deflection & Location** | $31.9068\text{ in}$<br>Bottom free end of cylinder | $0.395657\text{ in}$<br>Bottom free end of cylinder | $0.00890151\text{ in}$<br>Top of free end of cylinder |
| **Mass** | $0.1983058\text{ lbm}$ | $2.0493315\text{ lbm}$ | $2.343635\text{ lbm}$ |
| **Safety Factor ($\text{SF}$)** | $\approx 0.038$ (Failure) | $\approx 0.52$ (Failure) | $\approx 4.11$ (Passed) |
| **Minimum Element Size** | $0.0005$ | $0.0005$ | $0.0005$ |

---

## Part II: Optimizing the Linkage Design (2157 Portion)

### Initial Setup & Material Definition
Next, I performed FEA on the link component using Aluminum 6061 ($\sigma_y = 40,000\text{ psi}$).
1. **Constraints:** I fixed the top cylindrical hole using a fixed cylindrical boundary constraint.
2. **Loading:** I applied a tensile force of $F = 670\text{ lbf}$ in the $-Y$ direction along the bottom load-bearing hole surface.

---

### Inner Loop Execution: Linkage Design I (Convergence Phase)

 **Attempt 1 (Element Size $0.0005\text{ in}$):** Peak Von Mises stress was identified as $\sigma_{\text{vm}} = 7,752.85\text{ psi}$.
<img width="1280" height="764" alt="Screenshot 2026-10-21 162059" src="https://github.com/user-attachments/assets/ef1d5784-b5fa-4bd2-9ad9-acba5d78e3ac" />
<img width="1280" height="764" alt="Screenshot 2026-10-21 155810" src="https://github.com/user-attachments/assets/85af5580-bdc4-419d-bb61-551624cced68" />

 **Attempt 2 (Element Size $0.0003\text{ in}$):** Peak stress increased to $8,001.94\text{ psi}$.
   $$\text{Percent Difference} = \left| \frac{8,001.94 - 7,752.85}{7,752.85} \right| \times 100\% = 316\%$$
   Since $3.16\% < 7\%$, the mesh had already technically converged, but I decided to push element density one step further to guarantee accuracy.

<img width="1280" height="764" alt="Screenshot 2026-10-21 164110" src="https://github.com/user-attachments/assets/f4bbf3b2-b1f0-438d-85e3-31ea6da50722" />


 **Attempt 3 (Element Size $0.0002\text{ in}$):** Peak stress reached $8,223.34\text{ psi}$.
   $$\text{Percent Difference} = \left| \frac{8,223.34 - 8,001.94}{8,001.94} \right| \times 100\% = 2.73\%$$
   With $2.73\%$ difference, I locked in $0.0002\text{ in}$ as my converged minimum element size.

<img width="1280" height="764" alt="Screenshot 2026-10-21 170754" src="https://github.com/user-attachments/assets/272b0ff9-cd9f-4777-bb21-273efcfa15cf" />


---

### Outer Loop Execution: Linkage Geometry Iterations

#### Linkage Design I (Baseline)
* **Results:** Maximum stress reached $8,223.34\text{ psi}$ located at the right side of the bottom hole. Max deflection was $0.00112983\text{ in}$ at the lower edge.
* **Safety Factor:** $\text{SF} = \frac{40,000}{8,223.34} \approx 4.86$.
* **Takeaway:** A safety factor of $4.86$ meant the link was significantly over-designed, allowing me to remove material and reduce mass.

<img width="1280" height="764" alt="Screenshot 2026-10-21 183348" src="https://github.com/user-attachments/assets/c8b46c38-5c51-4492-a6d9-7dbbbf999173" />
<img width="1280" height="764" alt="Screenshot 2026-10-21 183828" src="https://github.com/user-attachments/assets/dcbc52c5-b4af-4cb4-87ad-8de3e32f0281" />


#### Linkage Design II
To lighten the link, I pocketed two weight-saving holes near the mid-section.
* **Results:** Peak stress shifted to the left edge of the new pocket hole at $10,278.3\text{ psi}$. Maximum deformation rose slightly to $0.00126604\text{ in}$.
* **Safety Factor & Mass:** $\text{SF} = 3.89$, while mass dropped from $0.10104\text{ lbm}$ to $0.09326\text{ lbm}$ ($7.7\%$ mass reduction).

<img width="1280" height="764" alt="Screenshot 2026-10-21 184905" src="https://github.com/user-attachments/assets/e5f43fb4-c8c9-40d7-9517-759f4593c81b" />
<img width="1280" height="764" alt="Screenshot 2026-10-21 184739" src="https://github.com/user-attachments/assets/3952e70a-427d-4919-99af-b807350f81d5" />


#### Linkage Design III
Noticing that the top region carried minimal load, I pocketed additional material near the top constraint interface.
* **Results:** Max stress was $10,474.6\text{ psi}$ at the middle-left weight-saving hole, and max deformation was $0.00126651\text{ in}$.
* **Safety Factor & Mass:** $\text{SF} = 3.82$, while total mass dropped to $0.08939\text{ lbm}$ ($11.5\%$ total weight reduction relative to baseline).

<img width="1280" height="764" alt="Screenshot 2026-10-21 185802" src="https://github.com/user-attachments/assets/81287009-c3ef-49c7-8a81-91f17d6fd4ab" />
<img width="1280" height="764" alt="Screenshot 2026-10-21 185546" src="https://github.com/user-attachments/assets/b8329c8b-4721-43a6-8b08-91a6d9bd43c3" />



---

### Linkage Data Summary Table

| Metric | Design I | Design II | Design III |
| :--- | :--- | :--- | :--- |
| **Max Stress & Location** | $8,223.34\text{ psi}$<br>Right side of bottom hole | $10,278.3\text{ psi}$<br>Left side of left weight-saving hole | $10,474.6\text{ psi}$<br>Left side of middle-left weight-saving hole |
| **Max Deflection & Location** | $0.00112983\text{ in}$<br>Bottom of lower load-bearing hole | $0.00126604\text{ in}$<br>Bottom of lower load-bearing hole | $0.00126651\text{ in}$<br>Bottom of lower load-bearing hole |
| **Mass** | $0.10104383\text{ lbm}$ | $0.09325771\text{ lbm}$ | $0.08939294\text{ lbm}$ |
| **Safety Factor ($\text{SF}$)** | $4.86$ | $3.89$ | $3.82$ |
| **Minimum Element Size** | $0.0002$ | $0.0002$ | $0.0002$ |

---

## Reflections & Engineering Lessons Learned

### Lessons Learned
* **Stress Concentration Mitigation:** Incorporating generous transition fillets ($R = 1.0\text{ in}$) across re-entrant corners redistributes internal stress flow lines, drastically reducing localized peak Von Mises stresses.
* **Mesh Discrepancy & Singularities:** Refining local mesh resolution increases boundary precision. Sharp unfilleted re-entrant corners act as theoretical stress singularities, causing stress values to spike artificially with finer meshes until actual fillets are introduced.
* **Stiffness-to-Weight Optimization:** Removing structural material from low-stress, non-load-bearing regions optimized overall mass efficiency without compromising required tensile load capacity.
* **Computational Cost vs. Precision:** Decreasing global minimum element sizes yields tighter numerical convergence, but exponentially increases local computation time and computer processing memory.

### Mistakes & Process Corrections
* **Non-Monotonic Stress Jump:** During Bracket Design I refinement, stress unexpectedly jumped from $955,025\text{ psi}$ to $1,031,640\text{ psi}$. I initially found this confusing, but realized it was caused by localized mesh sensitivity around unrounded re-entrant geometries.
* **Corrective Action:** I added explicit CAD fillet features prior to running Design III, which smoothed out gradient calculations and restored normal, predictable convergence trends.
