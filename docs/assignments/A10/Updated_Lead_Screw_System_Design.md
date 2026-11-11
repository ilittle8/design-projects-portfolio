# Lead Screw System Design — Part 1



## Project Overview



This document records my design process for the lead-screw system and its mounting components for the tensile tester assignment. I am documenting my calculations, design decisions, assumptions, and changes throughout the project rather than presenting only the final design.



The tensile tester uses **two identical lead screws** to move the crosshead and apply a maximum tensile force of **2 kN** to the test specimen.



> **Project scope:** This document records the lead-screw calculations, bronze nut selection and internal-thread analysis, steel flange selection, and preliminary flange-to-crosshead bolted-joint calculations.



---



## 1. Design Requirements and Initial Known Values



| Parameter | Symbol | Value |

|---|---|---:|

| Maximum specimen tensile force | FT | 2,000 N |

| Number of identical lead screws | ns | 2 |

| Factor of safety | N | 4 |

| Required crosshead speed | v | 1–50 mm/min |

| Minimum lead-screw length | — | 18 in |

| Selected screw material for calculations | — | AISI 1020 cold-drawn steel |



I selected **AISI 1020 cold-drawn steel** as the material for my initial strength calculations. I used an assumed yield strength of Sy=350MPa.



This yield strength should be verified against a material datasheet or an approved material-property source before treating it as a confirmed property of the purchased screw.



I assumed that the tensile load would be shared equally between the two identical lead screws:



$$

F_s=\frac{F_T}{n_s}

$$



$$

F_s=\frac{2000}{2}

$$



$$

\boxed{F_s=1000\text{ N per screw}}

$$



This equal-load-sharing assumption requires the two screws to be properly aligned and driven synchronously.



---



## 2. Minimum Screw Diameter from Axial Stress



I first calculated the minimum required screw diameter using the axial normal-stress relationship:



$$

\sigma=\frac{F}{A}

$$



The cross-sectional area of a solid circular shaft is:



$$

A=\frac{\pi d^2}{4}

$$



For a factor of safety of 4, I calculated the allowable stress as:



$$

\sigma\_{\text{allow}}=\frac{S_y}{N}

$$



Substituting:



$$

\sigma\_{\text{allow}}=\frac{350}{4}

$$



$$

\boxed{\sigma\_{\text{allow}}=87.5\text{ MPa}}

$$



Solving the axial-stress equation for diameter:



$$

d\_{\min}=\sqrt{\frac{4F_s}{\pi\sigma\_{\text{allow}}}}

$$



Substituting the load carried by one screw:



$$

d\_{\min}=

\sqrt{\frac{4(1000)}

{\pi(87.5\times10^6)}}

$$



$$

\boxed{d\_{\min}=0.003815\text{ m}=3.815\text{ mm}}

$$



This is the theoretical minimum diameter based on axial stress alone.



For a threaded screw, the **minor (root) diameter** is the relevant nominal diameter for this check because it represents the smallest cross-section. Manufacturing tolerances and other possible failure modes must also be considered.



---



## 3. Lead Selection and Rotational Speed



My initial goal was to use a relatively small lead so that the crosshead displacement per revolution would be small. I wanted finer positioning while applying tension to the specimen.



I initially considered a lead of 1mm/rev. However, when I found an available commercial screw with a lead of 0.05in/rev, I accepted changing the design lead to match the actual component.



Converting the lead:



$$

L=0.05(25.4)

$$



$$

\boxed{L=1.27\text{ mm/rev}}

$$



The relationship between crosshead linear speed and screw rotational speed is:



$$

v=nL

$$



Solving for rotational speed:



$$

n=\frac{v}{L}

$$



At the minimum crosshead speed:



$$

n\_{\min}=\frac{1}{1.27}

$$



$$

\boxed{n\_{\min}=0.787\text{ RPM}}

$$



At the maximum crosshead speed:



$$

n\_{\max}=\frac{50}{1.27}

$$



$$

\boxed{n\_{\max}=39.37\text{ RPM}}

$$



Therefore, the required rotational speed range is:



$$

\boxed{n=0.787\text{ to }39.37\text{ RPM}}

$$



Both screws must rotate synchronously at the same speed to keep the crosshead level.



A smaller lead improves displacement resolution per revolution, but it does not automatically guarantee positioning accuracy. Backlash, thread tolerances, bearing play, structural stiffness, motor control resolution, and load-cell feedback also affect positioning and force control.



---



## 4. Thread Type and Nut Material Decisions



I chose an **Acme-style power-screw thread** because it is a common thread form used in power-transmission applications.



For a standard Acme thread, the included thread angle is 29. Therefore, the half-angle is:



$$

\alpha=\frac{29^\circ}{2}

$$



$$

\boxed{\alpha=14.5^\circ}

$$



I initially considered using a steel nut but changed the nut material to **bronze**.



I chose bronze because a steel screw and bronze nut combination is commonly used in sliding power-screw applications. The material pairing can reduce the likelihood of galling compared with dry steel-on-steel contact.



I also decided to use **lubricated screw/nut contact**.



For my preliminary torque calculation, I assumed:



$$

\boxed{\mu=0.15}

$$



This is an assumed coefficient of friction, not a verified value for the exact bronze alloy, lubricant, surface finish, and operating conditions. The final design should identify the lubrication condition and cite an appropriate friction-data source.



---



## 5. First Candidate: Roton 3/16–20 Stub Acme Screw



My first candidate was the Roton 3/16–20 Stub Acme steel lead screw, part **62240**.



[Roton 3/16–20 Stub Acme Steel Lead Screw]\(https\://www\.roton.com/product/stub-acme-lead-screw-3-16-20-rh-steel/)



The dimensions I recorded from the product information were:



| Parameter | Value |

|---|---:|

| Major diameter | 0.188 in = 4.775 mm |

| Minor diameter | 0.151 in = 3.835 mm |

| Lead | 0.050 in/rev = 1.27 mm/rev |



The nominal minor diameter exceeded my calculated minimum:



$$

3.835\text{ mm}>3.815\text{ mm}

$$



However, the margin was very small:



$$

3.835-3.815=0.020\text{ mm}

$$



More importantly, I found that the bronze nut's published operating load rating was below the load required per screw.



The required load per screw was:



$$

F_s=1000\text{ N}

$$



Converting to pounds-force:



$$

F_s=\frac{1000}{4.44822}

$$



$$

\boxed{F_s\approx224.8\text{ lbf}}

$$



The published operating load rating I identified for the bronze nut was 75 lbf.



Because the screw and nut assembly would move while applying tension, I decided not to use this first candidate.



This was an important design lesson: checking only the screw's diameter was not enough. I also needed to check the operating load rating of the nut.



---



## 6. Selected Candidate: Roton 1/4–20 Acme Steel Screw



I then selected the larger Roton 1/4–20 Acme steel screw, part **60758**.



[Roton 1/4–20 Acme Steel Screw — Part 60758]\(https\://www\.roton.com/product/acme-steel-screw-right-60758/)



The manufacturer information I recorded for this candidate was:



| Parameter | Value |

|---|---:|

| Thread | 1/4–20 Acme |

| Major diameter | 0.250 in = 6.350 mm |

| Minor diameter | 0.175 in = 4.445 mm |

| Lead | 0.050 in/rev = 1.270 mm/rev |

| Bronze-nut static load rating | 1,000 lbf |

| Bronze-nut operating load rating | 300 lbf |

| Forward-drive efficiency | 32% |

| Drive torque ratio | 0.025 in·lbf/lbf |



### 6.1 Minor Diameter Check



My calculated minimum diameter was:



$$

d\_{\min}=3.815\text{ mm}

$$



The selected screw's nominal minor diameter is:



$$

d\_{\text{minor}}=4.445\text{ mm}

$$



Therefore:



$$

4.445\text{ mm}>3.815\text{ mm}

$$



The nominal minor diameter exceeds the calculated minimum by:



$$

4.445-3.815=0.630\text{ mm}

$$



This candidate provides a larger nominal diameter margin than my first selection.



### 6.2 Bronze Nut Operating Load Check



The load per screw is:



$$

F_s=1000\text{ N}

$$



Converting to pounds-force:



$$

F_s=\frac{1000}{4.44822}

$$



$$

F_s\approx224.8\text{ lbf}

$$



Using the operating load rating recorded from Roton's engineering data:



$$

224.8\text{ lbf}<300\text{ lbf}

$$



Therefore, the required load per nut is below the published operating load rating I identified for this candidate.



This comparison assumes that the rating applies to the exact compatible bronze nut and the intended operating conditions. I still need to confirm the exact nut part number and the manufacturer's rating conditions.



### 6.3 Material Verification



Roton identifies the screw as steel. I selected AISI 1020 cold-drawn steel for my calculations, but I have not yet verified that part 60758 is specifically manufactured from AISI 1020 cold-drawn steel.



I should not claim that the purchased screw has this exact material grade until the manufacturer confirms it.



---



## 7. Final Lead-Screw Torque Calculation

The torque calculation determines the rotational torque required to raise the tensile load.

The load is shared equally between the two screws:

$$
F_s=\frac{F_T}{n_s}=\frac{2000}{2}=1000\text{ N}
$$

For an Acme screw raising a load, the torque per screw is:

$$
T_s=
\frac{F_s d_m}{2}
\left(
\frac{L+\pi\mu d_m\sec\alpha}
{\pi d_m-\mu L\sec\alpha}
\right)
$$

Where:

- \(F_s\) = axial load carried by one screw
- \(d_m\) = mean thread diameter of the selected screw
- \(L\) = lead
- \(\mu\) = assumed thread friction coefficient
- \(\alpha\) = Acme thread half-angle

I used a lubricated bronze-on-steel thread contact assumption and an estimated coefficient of friction of:

$$
\mu=0.15
$$

The Acme thread half-angle is:

$$
\alpha=14.5^\circ
$$

I completed the mean-diameter determination and torque derivation for the selected 1/4–20 screw. The final calculated torque is:

$$
\boxed{T_s=0.635\text{ N}\cdot\text{m per screw}}
$$

For two screws:

$$
T_{\text{total}}=2T_s
$$

$$
\boxed{T_{\text{total}}=1.27\text{ N}\cdot\text{m}}
$$

This is the calculated operating torque for the assumed load and friction condition. The drive system may require additional margin for acceleration, friction variation, misalignment, and other operating effects; those effects are separate from the calculated steady raising torque.

**Correction to the earlier draft:** The 4.305 mm mean diameter recorded in my initial handwritten calculation belonged to the first 3/16-inch candidate. It is not the mean diameter for the selected 1/4-inch screw and is not reused in the final torque result.

---

## 8. Bronze Nut Selection and Internal Thread-Bearing Bending Analysis

After selecting the 1/4–20 Acme screw, I selected a compatible bronze threaded mount nut:

- **Manufacturer:** Roton
- **Part number:** 91734
- **Description:** Right-hand bronze Acme threaded mount nut
- **Internal thread:** 1/4–20 Acme
- **External mounting thread:** 0.563–18 UNF

[Roton Bronze Threaded Mount Nut — Part 91734](https://www.roton.com/product/acme-bronze-threaded-mount-nut-right-91734/)

I selected bronze for the nut because bronze is commonly paired with steel in sliding power-screw applications and can reduce the likelihood of galling compared with steel-on-steel sliding contact.

### 8.1 Known values and assumptions

| Parameter | Symbol | Value |
|---|---|---:|
| Load carried by one nut | \(F\) | 1,000 N |
| Acme thread pitch | \(p\) | 0.050 in = 1.27 mm |
| Assumed full thread engagement | \(L_e\) | 0.625 in = 15.875 mm |
| Mean thread diameter | \(d_m\) | 0.225 in = 5.715 mm |
| Effective thread height | \(h\) | 0.025 in = 0.635 mm |
| Effective thread-root thickness | \(b\) | 0.018535 in = 0.4710 mm |
| Assumed bronze yield strength | \(S_y\) | 20,000 psi = 137.9 MPa |
| Bronze material assumption | — | CDA 932 / SAE 660 |

The bronze alloy and its yield strength are assumptions taken from the material information used for this preliminary calculation. The exact alloy and property should be confirmed against the supplier's material certification or an approved material datasheet.

I assumed the full 0.625 in of nut length was engaged with the screw. This is an analysis assumption and should be checked against the actual component drawing.

### 8.2 Number of engaged threads

The number of engaged threads is:

$$
n=\frac{L_e}{p}
$$

$$
n=\frac{0.625}{0.050}
$$

$$
\boxed{n=12.5\text{ threads}}
$$

Assuming equal load sharing between engaged threads:

$$
F_{\text{thread}}=\frac{F}{n}
$$

$$
F_{\text{thread}}=\frac{1000}{12.5}
$$

$$
\boxed{F_{\text{thread}}=80\text{ N}}
$$

### 8.3 Thread-bearing bending model

I modeled an individual internal nut thread as a small cantilever fixed at its root. The axial load transferred through the thread flank creates a bending moment at the thread root.

Using the simplified thread-bearing bending relationship from my calculation:

$$
\boxed{
\sigma_b=
\frac{3Fh}{\pi d_m n b^2}
}
$$

Substituting the values in consistent SI units:

$$
\sigma_b=
\frac{3(1000)(0.000635)}
{\pi(0.005715)(12.5)(0.0004710)^2}
$$

$$
\boxed{\sigma_b=38.3\text{ MPa}}
$$

### 8.4 Factor of safety

The factor of safety against yielding in the bronze internal threads is:

$$
SF=\frac{S_y}{\sigma_b}
$$

$$
SF=\frac{137.9}{38.3}
$$

$$
\boxed{SF=3.60}
$$

The calculated factor of safety is 3.60 under the full-engagement and equal-load-sharing assumptions. I accepted this result for the preliminary nut selection. The result should not be interpreted as a check of every possible nut failure mode; it is specifically the simplified internal-thread bearing-bending check.

---

## 9. Steel Mounting Flange Selection

I selected a steel mounting flange with an internal thread matching the bronze nut's external mounting thread.

- **Manufacturer:** Roton
- **Part number:** 89837
- **Description:** Steel mounting flange
- **Center thread:** 0.563–18 UNF

The flange's internal mounting thread mates with the nut's external 0.563–18 UNF thread.

[Roton Mounting Flange — Part 89837](https://www.roton.com/)

### 9.1 Flange dimensions recorded from the component drawing

| Parameter | Symbol | Value |
|---|---|---:|
| Outside diameter | \(D_o\) | 1.600 in |
| Center mounting thread | — | 0.563–18 UNF |
| Number of mounting holes | \(n_b\) | 4 |
| Mounting-hole diameter | \(d_h\) | 0.266 in |
| Bolt-circle diameter | \(D_{BC}\) | 1.125 in |
| Flange thickness | \(t_f\) | 0.410 in |
| Side set-screw thread | — | 5-40 |
| Flange material | — | Steel |

The 5-40 side feature is recorded from the drawing; its intended function and whether it is needed in the final assembly should be confirmed.

### 9.2 Mounting arrangement

I decided to mount the flange on the **underside of the moving crosshead**. Four bolts pass through the flange's clearance holes and engage tapped holes in the steel crosshead.

The load path is:

1. The specimen applies a tensile reaction to the crosshead.
2. The crosshead transfers load through the four mounting bolts.
3. The bolts retain the steel flange against the underside of the crosshead.
4. The flange retains the bronze nut through the matching 0.563–18 UNF mounting threads.

The nut-to-flange threaded interface and the flange-to-crosshead bolted interface are separate connections and require separate checks.

---

## 10. Flange-to-Crosshead Bolt Selection and Tensile Stress

I selected four **1/4–20 UNC SAE Grade 5 bolts** for the flange-to-crosshead connection.

The flange mounting holes are 0.266 in in diameter. A 0.250 in nominal bolt diameter provides:

$$
c_d=0.266-0.250
$$

$$
\boxed{c_d=0.016\text{ in diametral clearance}}
$$

### 10.1 Free-body diagram and bolt loading

One flange carries the load from one leadscrew/nut assembly:

$$
F_{\text{flange}}=1000\text{ N}
$$

For the preliminary free-body diagram, I assumed the four bolts share the axial load equally:

$$
\sum F_y=0
$$

$$
F_{\text{flange}}-R_1-R_2-R_3-R_4=0
$$

With equal bolt reactions:

$$
R_1=R_2=R_3=R_4=R_b
$$

$$
1000-4R_b=0
$$

$$
\boxed{R_b=250\text{ N per bolt}}
$$

This equal-load assumption is a preliminary idealization. Actual bolt loads can differ because of flange and crosshead stiffness, bolt preload, contact conditions, and possible prying.

### 10.2 Tensile stress in each bolt

For a 1/4–20 UNC bolt, I used a tensile stress area of:

$$
A_t=0.0318\text{ in}^2
$$

The force per bolt in pounds-force is:

$$
F_b=\frac{250}{4.44822}
$$

$$
F_b=56.20\text{ lbf}
$$

The direct tensile stress is:

$$
\sigma_b=\frac{F_b}{A_t}
$$

$$
\sigma_b=\frac{56.20}{0.0318}
$$

$$
\boxed{\sigma_b=1767\text{ psi}=12.18\text{ MPa}}
$$

### 10.3 Bolt factor of safety

For the selected SAE Grade 5 bolt, I used a minimum yield strength of 92 ksi:

$$
S_y=92,000\text{ psi}
$$

The factor of safety against direct tensile yielding is:

$$
SF_{\text{bolt}}=\frac{S_y}{\sigma_b}
$$

$$
SF_{\text{bolt}}=\frac{92,000}{1767}
$$

$$
\boxed{SF_{\text{bolt}}=52.1}
$$

This result checks direct tensile stress in the bolt shank/thread tensile area under the equal-load assumption. It does not by itself verify bolt fatigue, preload, prying, flange bending, or the tapped crosshead threads.

---

## 11. Preliminary Internal Thread-Stripping Check for the Crosshead

The four Grade 5 bolts pass through the flange and thread into tapped holes in the steel crosshead. Since the crosshead thickness and exact steel grade have not yet been selected, I worked backward to estimate a minimum thread engagement length.

This is a **preliminary sizing calculation**, not a final verification of the crosshead. The crosshead material strength is an assumption and must be replaced with the actual selected material property.

### 11.1 Known values and assumptions

| Parameter | Symbol | Value |
|---|---|---:|
| Load per bolt | \(F_b\) | 250 N = 56.20 lbf |
| Bolt thread | — | 1/4–20 UNC |
| Assumed crosshead tensile strength | \(S_{ut}\) | 420 MPa |
| Estimated thread shear strength | \(S_{su}\) | \(0.5S_{ut}=210\) MPa |
| Estimated thread shear strength in psi | \(S_{su}\) | 30,458 psi |
| Target factor of safety | \(SF\) | 4 |
| Internal thread stripping area approximation | \(A_{\text{int}}\) | \(0.539L_e\), with \(L_e\) in inches |

I used an assumed steel tensile strength of 420 MPa and estimated shear strength as one-half of that value. These are preliminary assumptions, not confirmed crosshead properties.

### 11.2 Solve for required engagement length

The estimated internal thread stripping capacity is:

$$
F_{\text{strip}}=S_{su}A_{\text{int}}
$$

The factor of safety is:

$$
SF=\frac{S_{su}A_{\text{int}}}{F_b}
$$

Using the area approximation:

$$
SF=\frac{S_{su}(0.539L_e)}{F_b}
$$

Solving symbolically for engagement length:

$$
\boxed{
L_e=\frac{SF\cdot F_b}{0.539S_{su}}
}
$$

Substituting the assumed material strength and the load per bolt:

$$
L_e=
\frac{4(56.20)}
{0.539(30,458)}
$$

$$
\boxed{L_e=0.0137\text{ in}=0.348\text{ mm}}
$$

This theoretical result is less than one 1/4–20 thread pitch (0.050 in), so it is not a sensible practical engagement specification by itself.

### 11.3 Preliminary engagement selection

I selected a preliminary full thread engagement length equal to one nominal bolt diameter:

$$
L_e=d=0.250\text{ in}=6.35\text{ mm}
$$

For a 20-thread-per-inch bolt, this corresponds to:

$$
n=\frac{0.250}{0.050}=5\text{ thread pitches}
$$

The estimated factor of safety at this engagement length is:

$$
SF=
\frac{(30,458)(0.539)(0.250)}{56.20}
$$

$$
\boxed{SF_{\text{thread stripping}}\approx73.0}
$$

I therefore used **0.250 in (6.35 mm) of full thread engagement** as the preliminary design target for each tapped hole.

The crosshead thickness has not yet been selected. It must provide at least this much usable full thread engagement. A blind tapped hole also needs additional depth for the drill point and incomplete threads, so the required drilled-hole depth will be greater than the full engagement length.

**Important limitation:** The estimated stripping area and shear-strength relationship must be checked against the course method or an accepted fastener-design reference before treating the factor of safety as final. The assumed crosshead tensile strength must also be replaced with the actual material property. This calculation does not account for bolt preload, flange prying, or unequal bolt loading.

---

## 12. Current Design Record

| Design item | Current selection/status |
|---|---|
| Maximum specimen tensile load | 2,000 N |
| Number of lead screws | 2 |
| Load per screw/nut/flange assembly | 1,000 N |
| Lead screw | Roton part 60758 |
| Lead-screw thread | 1/4–20 Acme, right-hand |
| Lead-screw major diameter | 0.250 in = 6.350 mm |
| Lead-screw minor diameter | 0.175 in = 4.445 mm |
| Lead | 0.050 in/rev = 1.270 mm/rev |
| Nut | Roton part 91734, bronze |
| Nut internal thread | 1/4–20 Acme |
| Nut external mounting thread | 0.563–18 UNF |
| Nut thread-bearing bending stress | 38.3 MPa |
| Nut thread-bearing bending factor of safety | 3.60 |
| Flange | Roton part 89837, steel |
| Flange center thread | 0.563–18 UNF |
| Flange mounting holes | 4 × 0.266 in |
| Flange bolt circle | 1.125 in |
| Flange thickness | 0.410 in |
| Flange mounting arrangement | Underside of crosshead |
| Mounting bolts | 4 × 1/4–20 UNC SAE Grade 5 |
| Load per mounting bolt | 250 N |
| Direct bolt tensile stress | 12.18 MPa |
| Bolt tensile-yield factor of safety | 52.1 |
| Preliminary crosshead thread engagement | 0.250 in = 6.35 mm |
| Estimated crosshead internal-thread stripping SF | 73.0, based on assumed material properties and area model |
| Crosshead material and thickness | Not yet selected |
| Final calculated operating torque | 1.27 N·m total; 0.635 N·m per screw |
| Required screw speed range | 0.787–39.37 RPM |

---

## 13. Remaining Checks Before Finalizing the Assembly

- [ ] Confirm the exact bronze alloy and yield strength for Roton nut part 91734.
- [ ] Confirm that the assumed 0.625 in Acme thread engagement matches the actual nut drawing.
- [ ] Confirm the manufacturer's operating-load rating and conditions for the selected screw/nut combination.
- [ ] Confirm the selected screw's actual steel grade and condition.
- [ ] Confirm the final torque calculation's mean diameter and friction assumptions against the selected screw and lubrication condition.
- [ ] Confirm the actual nut-to-flange 0.563–18 UNF thread engagement length.
- [ ] Verify the internal and external thread strength of the nut-to-flange mounting connection.
- [ ] Select the crosshead steel grade and use its actual tensile/yield properties.
- [ ] Select the crosshead thickness so that the tapped holes provide the required usable thread engagement.
- [ ] Verify the internal thread-stripping calculation using the course-approved or reference-standard method.
- [ ] Check flange bending and bearing stresses.
- [ ] Revisit bolt loading for preload, flange prying, and nonuniform load distribution.
- [ ] Verify the selected screw's available length is at least 18 in.
- [ ] Check screw buckling, alignment, bearing support, and synchronization as appropriate to the complete design.

---

## 14. Design Decisions and Lessons Learned

1. I began by calculating a minimum screw diameter from axial stress using a factor of safety of 4.
2. I selected Acme threads because they are common in power-screw applications.
3. I changed the design lead to 1.27 mm/rev to match an available commercial screw.
4. I chose a bronze nut and lubricated contact rather than dry steel-on-steel contact.
5. My first screw candidate passed the nominal diameter check but did not meet the published bronze-nut operating-load rating.
6. I selected a larger 1/4–20 screw after checking its minor diameter and the bronze-nut operating-load rating.
7. I selected Roton bronze nut part 91734 and checked its internal Acme threads for thread-bearing bending stress.
8. I calculated a 3.60 factor of safety for the bronze nut's internal thread-bearing bending model, assuming full thread engagement.
9. I selected Roton steel flange part 89837 because its 0.563–18 UNF mounting thread matches the nut's external mounting thread.
10. I decided to mount the flange underneath the crosshead using four bolts.
11. I selected four 1/4–20 UNC SAE Grade 5 bolts and calculated the direct tensile stress using an equal-load-sharing assumption.
12. I estimated a preliminary crosshead thread engagement target of 0.250 in because the theoretical stripping calculation produced an impractically short engagement length.
13. I learned that the screw, nut, flange, bolts, and crosshead must be checked as a connected load path. A high safety factor for one interface does not automatically verify the entire assembly.

---

*This document records my current design process, calculations, component choices, and assumptions. Values based on assumed material properties or idealized load sharing are identified as preliminary and must be verified before finalizing the design.*
