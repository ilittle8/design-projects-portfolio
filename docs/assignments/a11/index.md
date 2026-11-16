# A11 – Motor Selection

## Objective


## Analyze


## Decide
_Reference your concept selection (Pugh matrix) here. How does this design follow from that decision?_

## Communicate

# MEGR Leadscrew Tensile Tester — Design Documentation

## 1. Project Overview

The objective of this project is to design a leadscrew-driven tensile tester capable of applying a controlled tensile load to a specimen. The system uses two parallel Acme leadscrews to move the crosshead.

The design work completed so far includes:

- Selection of the leadscrew and nut materials.
- Selection of the threaded mount nut and mounting flange.
- Preliminary flange-to-crosshead fastener calculations.
- Calculation of the operating torque required by each leadscrew.
- Preliminary selection of the stepper gearmotor.

The design uses **one motor per leadscrew**, meaning two identical motors will drive the assembly.

---

## 2. Leadscrew and Nut Selection

### 2.1 Material Selection

The selected leadscrew material is AISI 1020 cold-drawn steel. A bronze nut was selected to reduce the likelihood of wear and galling compared with a dry steel-on-steel sliding interface.

The selected combination is:

- Leadscrew: AISI 1020 cold-drawn steel.
- Nut: Bronze.
- Thread type: Acme.
- Thread size: 1/4-20 Acme.

The exact bronze alloy must still be verified against the manufacturer's material specifications.

### 2.2 Nut Selection

The selected component is the Roton bronze Acme threaded mount nut:

- Part number: 91734.
- Internal thread: 1/4-20 Acme.
- External mounting thread: 0.563-18 UNF.

### 2.3 Mounting Flange Selection

The selected mounting flange is the Roton steel mounting flange:

- Part number: 89837.
- Center thread: 0.563-18 UNF.
- Outside diameter: 1.600 in.
- Thickness: 0.410 in.
- Number of mounting holes: 4.
- Mounting-hole diameter: 0.266 in.
- Bolt-circle diameter: 1.125 in.

The flange is mounted to the underside of the crosshead.

---

## 3. Flange-to-Crosshead Fastener Analysis

Four 1/4-20 UNC SAE Grade 5 bolts were selected for attaching each flange to the crosshead.

### 3.1 Load Distribution

The preliminary analysis assumes that one flange experiences an axial load of 1000 N.

Assuming equal load distribution among the four bolts:

\[
F_{\text{bolt}}=\frac{F_{\text{total}}}{n}
\]

\[
F_{\text{bolt}}=\frac{1000}{4}
\]

\[
\boxed{F_{\text{bolt}}=250\text{ N}}
\]

### 3.2 Bolt Tensile Stress

The tensile stress area of a 1/4-20 UNC bolt is:

\[
A_t=0.0318\text{ in}^2
\]

The tensile stress is:

\[
\sigma_t=\frac{F}{A_t}
\]

Using the force converted to pounds:

\[
F=250(0.22481)=56.20\text{ lbf}
\]

\[
\sigma_t=\frac{56.20}{0.0318}
\]

\[
\boxed{\sigma_t\approx1767\text{ psi}}
\]

Using an assumed Grade 5 bolt yield strength of 92 ksi:

\[
SF=\frac{S_y}{\sigma_t}
\]

\[
SF=\frac{92000}{1767}
\]

\[
\boxed{SF\approx52.1}
\]

This is a preliminary direct-tension check. It does not independently verify flange bending, prying, preload, or unequal bolt loading.

### 3.3 Preliminary Thread Engagement

A preliminary crosshead thread-stripping calculation was performed using the following assumptions:

- Crosshead material tensile strength: 420 MPa.
- Estimated thread shear strength:

\[
S_{su}=0.5S_{ut}
\]

\[
S_{su}=0.5(420)=210\text{ MPa}
\]

The estimated internal thread shear area was modeled as:

\[
A_{\text{int}}=0.539L_e
\]

where \(L_e\) is the engagement length in inches.

For a target safety factor of 4, the theoretical required engagement was estimated as:

\[
L_e\approx0.0137\text{ in}
\]

Because this is shorter than one thread pitch, a practical preliminary full-thread engagement target of:

\[
\boxed{L_e=0.250\text{ in}=6.35\text{ mm}}
\]

was proposed.

The estimated safety factor at this engagement was approximately 73 under the assumed model. This is not a verified final result because the actual crosshead material and thickness have not yet been established.

---

## 4. Leadscrew Operating Torque

The preliminary operating torque calculation for the selected 1/4-20 leadscrew resulted in:

\[
\boxed{T_{\text{screw}}=0.635\text{ N}\cdot\text{m}}
\]

This value represents the operating torque required by one leadscrew.

Since the design uses one motor per leadscrew, each motor must independently provide the required torque.

The total operating torque for both screws is:

\[
T_{\text{total}}=2T_{\text{screw}}
\]

\[
T_{\text{total}}=2(0.635)
\]

\[
\boxed{T_{\text{total}}=1.27\text{ N}\cdot\text{m}}
\]

However, the individual motor sizing requirement is based on 0.635 N·m per motor rather than the combined torque.

---

## 5. Motor Selection — Task 1

### 5.1 Motor Type Selection

Three motor configurations were considered:

- DC motor.
- Stepper motor.
- Geared motor.

A stepper gearmotor was selected as the preferred configuration because it combines the positioning capability of a stepper motor with the increased output torque and reduced output speed provided by a gearbox.

The selected candidate is:

**McMaster-Carr Part Number: 4801N14**

This is a NEMA 23 stepper gearmotor.

Two identical motors will be used, with one motor driving each leadscrew.

### 5.2 Motor Operating Requirements

The preliminary motor requirements are:

| Parameter | Requirement |
|---|---:|
| Operating torque per motor | 0.635 N·m |
| Design safety factor | 4 |
| Required design torque per motor | 2.54 N·m |
| Minimum screw speed | 0.79 RPM |
| Maximum screw speed | 39.37 RPM |
| Number of motors | 2 |
| Leadscrews per motor | 1 |

The required design torque is calculated using:

\[
T_{\text{design}}=SF(T_{\text{operating}})
\]

\[
T_{\text{design}}=4(0.635)
\]

\[
\boxed{T_{\text{design}}=2.54\text{ N}\cdot\text{m}}
\]

### 5.3 Preliminary Screw Speed Calculation

For a single-start 1/4-20 leadscrew, the lead is:

\[
L=\frac{25.4}{20}
\]

\[
\boxed{L=1.27\text{ mm/rev}}
\]

The rotational speed is determined by:

\[
N=\frac{v}{L}
\]

where:

- \(N\) = rotational speed in RPM.
- \(v\) = linear crosshead speed in mm/min.
- \(L\) = leadscrew lead in mm/rev.

Using the preliminary assumed linear speed range of 1–50 mm/min:

**Minimum rotational speed:**

\[
N_{\min}=\frac{1}{1.27}
\]

\[
\boxed{N_{\min}=0.787\text{ RPM}}
\]

**Maximum rotational speed:**

\[
N_{\max}=\frac{50}{1.27}
\]

\[
\boxed{N_{\max}=39.37\text{ RPM}}
\]

These linear speed limits must be confirmed against the assignment requirements.

### 5.4 Torque-Speed Curve Evaluation

The McMaster-Carr torque-speed chart for part 4801N14 was evaluated to determine whether the motor could meet the required operating torque at the maximum screw speed.

The chart specifies the following test conditions:

- Supply voltage: 24 V DC.
- Current: 2.2 A.
- Stepping configuration: Half-stepping.

At approximately 40 RPM, the torque-speed curve indicates an available torque of approximately 700 oz·in.

Converting this torque into N·m:

\[
1\text{ oz}\cdot\text{in}=0.0070616\text{ N}\cdot\text{m}
\]

\[
T_{\text{available}}=700(0.0070616)
\]

\[
\boxed{T_{\text{available}}\approx4.94\text{ N}\cdot\text{m}}
\]

### 5.5 Motor Safety Factor Verification

The available safety factor at approximately 40 RPM is:

\[
SF_{\text{available}}=
\frac{T_{\text{available}}}{T_{\text{operating}}}
\]

\[
SF_{\text{available}}=
\frac{4.94}{0.635}
\]

\[
\boxed{SF_{\text{available}}\approx7.78}
\]

The required design safety factor is 4.

Comparing the available torque against the required design torque:

\[
4.94\text{ N}\cdot\text{m}
>
2.54\text{ N}\cdot\text{m}
\]

Therefore, based on the approximate torque-speed curve reading, the 4801N14 satisfies the preliminary torque requirement at the maximum calculated screw speed.

This evaluation uses the torque shown on the manufacturer's gearmotor curve. The graph's exact output measurement conditions and continuous-duty limits should be confirmed before finalizing the selection.

### 5.6 Preliminary Motor Selection Result

The McMaster-Carr 4801N14 stepper gearmotor is the preliminary motor selection.

The motor was selected because:

1. It provides sufficient torque at the required maximum screw speed according to the supplied torque-speed curve.
2. Its geared configuration is suitable for the low rotational speeds required by the leadscrews.
3. Its stepper-motor configuration allows controlled incremental rotation.
4. Using one motor per leadscrew reduces the torque requirement imposed on each motor.

The preliminary selection is:

\[
\boxed{\text{Quantity: 2 McMaster-Carr 4801N14 motors}}
\]

---

## 6. Remaining Work and Verification

The following items remain before the design can be considered finalized.

### Motor and Drive System

- [ ] Confirm the motor's continuous-duty torque rating.
- [ ] Verify torque availability at the minimum operating speed.
- [ ] Confirm gearbox output torque and speed ratings.
- [ ] Select compatible stepper drivers and power supplies.
- [ ] Determine how the two motors will be synchronized.
- [ ] Verify that both motors maintain the required crosshead motion under load.

### Motor Mount Design — Task 2

- [ ] Obtain the motor's mounting dimensions.
- [ ] Determine mounting-hole locations and sizes.
- [ ] Design the motor mounting brackets.
- [ ] Calculate bracket thickness.
- [ ] Check bearing stress and mounting fasteners.
- [ ] Verify bracket stiffness and alignment with the leadscrews.

### Coupler Design — Task 3

- [ ] Determine the motor output-shaft dimensions.
- [ ] Determine the leadscrew shaft dimensions.
- [ ] Select an appropriate shaft coupling.
- [ ] Calculate torsional shear stress.
- [ ] Verify the coupling against the required safety factor of 4.

### Existing Assembly Verification

- [ ] Confirm the exact bronze alloy.
- [ ] Verify the nut-to-flange threaded engagement.
- [ ] Confirm the crosshead material and thickness.
- [ ] Recheck thread stripping using actual material properties.
- [ ] Evaluate flange bending and bearing stresses.
- [ ] Verify the complete tensile load path.

---

## 7. Current Design Status

| Design component | Status |
|---|---|
| Leadscrew material selection | Preliminary selection made |
| Bronze nut selection | Selected |
| Steel mounting flange selection | Selected |
| Flange fastener analysis | Preliminary calculation completed |
| Nut thread analysis | Preliminary calculation completed |
| Operating torque calculation | Completed provisionally |
| Motor type selection | Preliminary selection made |
| Motor torque-speed verification | Preliminary check passed |
| Motor mounting bracket | Not yet completed |
| Coupler design | Not yet completed |

**Documentation note:** Calculations marked preliminary rely on assumptions that still need verification against the assignment specifications, manufacturer data, and final component geometry. The motor selection is not yet a completed hardware installation or final design approval.
