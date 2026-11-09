# A10 – Lead Screw Translating System

## Objective


## Analyze


## Decide
_Reference your concept selection (Pugh matrix) here. How does this design follow from that decision?_

## Communicate


# Lead Screw System Design — Part 1

## Project Overview

This document records my design process for the lead-screw portion of the tensile tester assignment. I am documenting my calculations, design decisions, assumptions, and changes throughout the project rather than presenting only the final design.

The tensile tester uses **two identical lead screws** to move the crosshead and apply a maximum tensile force of **2 kN** to the test specimen.

> **Project scope:** This document covers the lead-screw calculations and component selection. Nut/flange and crosshead design will be documented separately.

---

## 1. Design Requirements and Initial Known Values

| Parameter | Symbol | Value |
|---|---|---:|
| Maximum specimen tensile force | $F_T$ | 2,000 N |
| Number of identical lead screws | $n_s$ | 2 |
| Factor of safety | $N$ | 4 |
| Required crosshead speed | $v$ | 1–50 mm/min |
| Minimum lead-screw length | — | 18 in |
| Selected screw material for calculations | — | AISI 1020 cold-drawn steel |

I selected **AISI 1020 cold-drawn steel** as the material for my initial strength calculations. I used an assumed yield strength of $S_y=350\text{ MPa}$.

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
\sigma_{\text{allow}}=\frac{S_y}{N}
$$

Substituting:

$$
\sigma_{\text{allow}}=\frac{350}{4}
$$

$$
\boxed{\sigma_{\text{allow}}=87.5\text{ MPa}}
$$

Solving the axial-stress equation for diameter:

$$
d_{\min}=\sqrt{\frac{4F_s}{\pi\sigma_{\text{allow}}}}
$$

Substituting the load carried by one screw:

$$
d_{\min}=
\sqrt{\frac{4(1000)}
{\pi(87.5\times10^6)}}
$$

$$
\boxed{d_{\min}=0.003815\text{ m}=3.815\text{ mm}}
$$

This is the theoretical minimum diameter based on axial stress alone.

For a threaded screw, the **minor (root) diameter** is the relevant nominal diameter for this check because it represents the smallest cross-section. Manufacturing tolerances and other possible failure modes must also be considered.

---

## 3. Lead Selection and Rotational Speed

My initial goal was to use a relatively small lead so that the crosshead displacement per revolution would be small. I wanted finer positioning while applying tension to the specimen.

I initially considered a lead of $1\text{ mm/rev}$. However, when I found an available commercial screw with a lead of $0.05\text{ in/rev}$, I accepted changing the design lead to match the actual component.

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
n_{\min}=\frac{1}{1.27}
$$

$$
\boxed{n_{\min}=0.787\text{ RPM}}
$$

At the maximum crosshead speed:

$$
n_{\max}=\frac{50}{1.27}
$$

$$
\boxed{n_{\max}=39.37\text{ RPM}}
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

For a standard Acme thread, the included thread angle is $29^\circ$. Therefore, the half-angle is:

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

[Roton 3/16–20 Stub Acme Steel Lead Screw](https://www.roton.com/product/stub-acme-lead-screw-3-16-20-rh-steel/)

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

[Roton 1/4–20 Acme Steel Screw — Part 60758](https://www.roton.com/product/acme-steel-screw-right-60758/)

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
d_{\min}=3.815\text{ mm}
$$

The selected screw's nominal minor diameter is:

$$
d_{\text{minor}}=4.445\text{ mm}
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

## 7. Preliminary Torque Calculation

The torque calculation determines how much rotational torque is required to raise the tensile load.

The load is assumed to be shared equally between the two screws:

$$
F_s=1000\text{ N per screw}
$$

For an Acme screw raising a load, the torque per screw can be expressed as:

$$
T_s=
\frac{F_s d_m}{2}
\left(
\frac{L+\pi\mu d_m\sec\alpha}
{\pi d_m-\mu L\sec\alpha}
\right)
$$

Where:

- $F_s$ = axial load carried by one screw
- $d_m$ = mean or pitch diameter of the thread
- $L$ = lead
- $\mu$ = thread friction coefficient
- $\alpha$ = Acme thread half-angle

The total torque required for two identical screws is:

$$
T_{\text{total}}=2T_s
$$

### 7.1 Mean Diameter and Torque Status

In my handwritten notes, I estimated a mean diameter of 4.305 mm for the **first 3/16-inch candidate** by averaging its major and minor diameters.

That value does **not** apply to the selected 1/4-inch screw.

I have not yet established a manufacturer-provided pitch/mean diameter or completed a verified mean-diameter estimate for part 60758. Therefore, I should not reuse the earlier 4.305 mm value for the final screw.

### 7.2 Preliminary Manufacturer-Based Torque Estimate

Roton's recorded drive torque ratio for the selected candidate was:

$$
0.025\frac{\text{in}\cdot\text{lbf}}{\text{lbf}}
$$

Using this ratio as a preliminary estimate:

$$
T_s=(224.8)(0.025)
$$

$$
T_s=5.62\text{ in}\cdot\text{lbf}
$$

For two screws:

$$
T_{\text{total}}=2(5.62)
$$

$$
T_{\text{total}}=11.24\text{ in}\cdot\text{lbf}
$$

Converting to SI units:

$$
\boxed{T_{\text{total}}\approx1.27\text{ N}\cdot\text{m}}
$$

This is a manufacturer-ratio-based preliminary estimate. I need to confirm the conditions associated with Roton's torque ratio and whether it represents the same lubrication, nut, and loading conditions as my design.

### 7.3 Safety Factor Consideration

I applied the factor of safety of 4 in the axial-stress diameter calculation.

I did not multiply the required operating torque by 4 because the assignment asks for the torque needed to provide the specified 2 kN specimen tension.

A separate torque margin may be appropriate when sizing the motor or drive system, but it should not automatically be applied a second time to the required operating torque.

---

## 8. Current Design Record

| Design item | Current selection/status |
|---|---|
| Number of screws | Two identical screws |
| Screw material used for calculations | AISI 1020 cold-drawn steel (exact product grade unverified) |
| Screw manufacturer/product | Roton part 60758 |
| Thread style | Acme, 1/4–20 |
| Major diameter | 6.350 mm |
| Minor diameter | 4.445 mm |
| Lead | 1.270 mm/rev |
| Nut material | Bronze |
| Contact condition | Lubricated |
| Preliminary friction coefficient | $\mu=0.15$, assumed |
| Axial-stress minimum diameter | 3.815 mm |
| Calculated screw speed range | 0.787–39.37 RPM |
| Preliminary total operating torque | 1.27 N·m, based on manufacturer's torque ratio |

---

## 9. Remaining Checks Before Finalizing the Lead-Screw Design

- [ ] Confirm the exact compatible bronze nut part number for Roton screw 60758.
- [ ] Confirm that the 300 lbf operating load rating applies to that nut and the intended operating conditions.
- [ ] Confirm the screw's actual steel grade and condition with Roton if AISI 1020 cold-drawn steel is required.
- [ ] Confirm the manufacturer's torque-ratio definition and test conditions.
- [ ] Obtain the actual pitch/mean diameter or a manufacturer thread drawing for the selected screw.
- [ ] Complete and include the detailed lead-screw/nut free-body diagram.
- [ ] Verify that the selected screw's available length is at least 18 in.
- [ ] Check screw buckling, alignment, bearing support, and synchronization as appropriate to the complete design.

---

## 10. Design Decisions and Lessons Learned

1. I began by calculating a minimum screw diameter from axial stress and a factor of safety of 4.
2. I selected Acme threads because they are common in power-screw applications.
3. I changed the design lead to 1.27 mm/rev to match an available commercial screw.
4. I chose a bronze nut and lubricated contact rather than dry steel-on-steel contact.
5. My first screw candidate passed the nominal diameter check but did not meet the published bronze-nut operating load rating.
6. I selected a larger 1/4–20 screw after checking both its minor diameter and the bronze-nut operating load rating.
7. I learned that selecting a lead screw requires checking the screw and nut as a system, rather than checking only the screw diameter.

---

*This document records my current design process and identifies items that still require manufacturer verification. I will update it as I complete the remaining lead-screw checks and move on to the nut/flange and crosshead designs.*
