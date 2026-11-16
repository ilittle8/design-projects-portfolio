# MEGR Leadscrew Tensile Tester — Design Documentation

## 1. Project Overview

The objective of this project is to design a leadscrew-driven tensile tester capable of applying a controlled tensile load to a specimen. The design uses two parallel Acme leadscrews to move the crosshead.

The documented design work includes the selection of the leadscrew and nut materials, mounting hardware, preliminary fastener analysis, operating torque calculations, and motor selection.

The system uses two motors, with one motor independently driving each leadscrew.

---

## 2. Leadscrew and Nut Selection

### 2.1 Material Selection

An AISI 1020 cold-drawn steel leadscrew was selected with a bronze Acme nut. This material combination was chosen to reduce wear and the likelihood of galling compared with a dry steel-on-steel sliding interface.

The selected thread specification is $1/4$-20 Acme.

### 2.2 Nut Selection

The selected component is the Roton bronze Acme threaded mount nut, part number **91734**.

| Specification | Selection |
|---|---|
| Manufacturer | Roton |
| Part number | 91734 |
| Material | Bronze |
| Internal thread | $1/4$-20 Acme |
| External mounting thread | 0.563-18 UNF |

### 2.3 Mounting Flange Selection

The selected mounting flange is the Roton steel mounting flange, part number **89837**.

| Specification | Dimension |
|---|---:|
| Center thread | 0.563-18 UNF |
| Outside diameter | 1.600 in |
| Thickness | 0.410 in |
| Number of mounting holes | 4 |
| Mounting-hole diameter | 0.266 in |
| Bolt-circle diameter | 1.125 in |

The steel flange is mounted to the underside of the crosshead and provides the mounting interface for the bronze threaded nut.

---

## 3. Flange-to-Crosshead Fastener Analysis

Four $1/4$-20 UNC SAE Grade 5 bolts were selected to attach the mounting flange to the crosshead.

### 3.1 Load Distribution

The preliminary analysis assumes an axial load of $1000\text{ N}$ acting on one flange. The load is distributed equally among the four mounting bolts.

The force carried by each bolt is:

$$
F_{\text{bolt}}=\frac{F_{\text{total}}}{n}
$$

Substituting:

$$
F_{\text{bolt}}=\frac{1000}{4}
$$

$$
\boxed{F_{\text{bolt}}=250\text{ N}}
$$

Converting to pounds-force:

$$
F_{\text{bolt}}=250(0.22481)
$$

$$
\boxed{F_{\text{bolt}}=56.20\text{ lbf}}
$$

### 3.2 Bolt Tensile Stress

The tensile stress area for a $1/4$-20 UNC bolt is:

$$
A_t=0.0318\text{ in}^2
$$

The tensile stress is calculated using:

$$
\sigma_t=\frac{F}{A_t}
$$

Substituting:

$$
\sigma_t=\frac{56.20}{0.0318}
$$

$$
\boxed{\sigma_t\approx1767\text{ psi}}
$$

Using an assumed Grade 5 bolt yield strength of $92,000\text{ psi}$, the factor of safety is:

$$
SF=\frac{S_y}{\sigma_t}
$$

$$
SF=\frac{92000}{1767}
$$

$$
\boxed{SF\approx52.1}
$$

This calculation evaluates the direct tensile stress in each bolt under the assumed equal load distribution.

### 3.3 Preliminary Thread Engagement Analysis

A preliminary crosshead thread-stripping calculation was performed using an assumed crosshead steel tensile strength of $420\text{ MPa}$.

The estimated thread shear strength was calculated as:

$$
S_{su}=0.5S_{ut}
$$

$$
S_{su}=0.5(420)
$$

$$
\boxed{S_{su}=210\text{ MPa}}
$$

The internal thread shear area was modeled using:

$$
A_{\text{int}}=0.539L_e
$$

where $L_e$ is the engagement length in inches.

For a target safety factor of 4, the theoretical engagement length was estimated as:

$$
\boxed{L_e\approx0.0137\text{ in}}
$$

Because this theoretical engagement length is shorter than one thread pitch, a practical full-thread engagement length of $0.250\text{ in}$ ($6.35\text{ mm}$) was proposed.

The estimated factor of safety at this engagement length was approximately:

$$
\boxed{SF\approx73}
$$

These results are based on the assumed crosshead material properties and the preliminary thread-stripping model.

---

## 4. Leadscrew Operating Torque

The operating torque calculated for one selected $1/4$-20 leadscrew was:

$$
\boxed{T_{\text{screw}}=0.635\text{ N}\cdot\text{m}}
$$

Because the tensile tester uses two leadscrews, the combined operating torque is:

$$
T_{\text{total}}=2T_{\text{screw}}
$$

Substituting:

$$
T_{\text{total}}=2(0.635)
$$

$$
\boxed{T_{\text{total}}=1.27\text{ N}\cdot\text{m}}
$$

The motor configuration uses one motor per leadscrew. Therefore, each motor is sized for the individual operating torque of $0.635\text{ N}\cdot\text{m}$.

---

## 5. Motor Selection

### 5.1 Motor Type Selection

Three motor configurations were considered: DC motors, stepper motors, and geared motors.

A stepper gearmotor was selected because it combines the incremental positioning capability of a stepper motor with the increased output torque and reduced rotational speed provided by a gearbox.

The selected motor candidate is the **McMaster-Carr 4801N14 NEMA 23 stepper gearmotor**.

Two identical motors are used in the design, with each motor independently driving one leadscrew.

### 5.2 Motor Operating Requirements

The preliminary operating requirements for each motor are:

| Parameter | Value |
|---|---:|
| Operating torque | $0.635\text{ N}\cdot\text{m}$ |
| Design safety factor | 4 |
| Required design torque | $2.54\text{ N}\cdot\text{m}$ |
| Minimum screw speed | $0.79\text{ RPM}$ |
| Maximum screw speed | $39.37\text{ RPM}$ |
| Number of motors | 2 |
| Leadscrews per motor | 1 |

The required design torque is calculated using:

$$
T_{\text{design}}=SF(T_{\text{operating}})
$$

Substituting:

$$
T_{\text{design}}=4(0.635)
$$

$$
\boxed{T_{\text{design}}=2.54\text{ N}\cdot\text{m}}
$$

### 5.3 Leadscrew Speed Calculation

The selected leadscrew is a single-start $1/4$-20 Acme screw. Its lead is:

$$
L=\frac{25.4}{20}
$$

$$
\boxed{L=1.27\text{ mm/rev}}
$$

The rotational speed is determined from the required linear crosshead speed:

$$
N=\frac{v}{L}
$$

where:

- $N$ = rotational speed in RPM.
- $v$ = linear crosshead speed in mm/min.
- $L$ = leadscrew lead in mm/rev.

Using a preliminary linear speed range of $1$ to $50\text{ mm/min}$:

**Minimum rotational speed:**

$$
N_{\min}=\frac{1}{1.27}
$$

$$
\boxed{N_{\min}=0.787\text{ RPM}}
$$

**Maximum rotational speed:**

$$
N_{\max}=\frac{50}{1.27}
$$

$$
\boxed{N_{\max}=39.37\text{ RPM}}
$$

### 5.4 Motor Torque-Speed Curve Evaluation

The McMaster-Carr torque-speed chart for part 4801N14 was evaluated to determine whether the motor could supply the required torque throughout the operating speed range.

The manufacturer's chart specifies the following operating conditions:

| Parameter | Value |
|---|---:|
| Supply voltage | 24 V DC |
| Current | 2.2 A |
| Stepping configuration | Half-stepping |

At approximately $40\text{ RPM}$, the torque-speed curve indicates an available torque of approximately $700\text{ oz}\cdot\text{in}$.

The torque conversion is:

$$
1\text{ oz}\cdot\text{in}
=0.0070616\text{ N}\cdot\text{m}
$$

Therefore:

$$
T_{\text{available}}=700(0.0070616)
$$

$$
\boxed{T_{\text{available}}\approx4.94\text{ N}\cdot\text{m}}
$$

### 5.5 Motor Factor of Safety Verification

The available factor of safety at approximately $40\text{ RPM}$ is calculated by comparing the available motor torque with the operating torque required by one leadscrew.

$$
SF_{\text{available}}
=\frac{T_{\text{available}}}{T_{\text{operating}}}
$$

Substituting:

$$
SF_{\text{available}}=\frac{4.94}{0.635}
$$

$$
\boxed{SF_{\text{available}}\approx7.78}
$$

The required design torque is:

$$
T_{\text{design}}=2.54\text{ N}\cdot\text{m}
$$

Comparing the available torque with the required design torque:

$$
4.94\text{ N}\cdot\text{m}
>
2.54\text{ N}\cdot\text{m}
$$

The motor therefore satisfies the preliminary torque requirement at the maximum calculated leadscrew speed, based on the approximate torque read from the manufacturer's curve.

### 5.6 Motor Selection Result

The selected preliminary motor is the McMaster-Carr **4801N14 NEMA 23 stepper gearmotor**.

The motor was selected because its torque-speed curve indicates sufficient output torque at the maximum calculated leadscrew speed. Its geared configuration also provides the low rotational speeds and increased torque needed for the tensile tester.

The final preliminary motor configuration consists of:

- Motor: McMaster-Carr 4801N14
- Motor type: NEMA 23 stepper gearmotor
- Quantity: 2
- Configuration: One motor per leadscrew

This configuration allows each motor to independently provide the torque and rotational speed required by its respective leadscrew.
