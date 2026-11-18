# Motor Selection, Bracket Design, and Coupler Selection - Isaiah Little

## Motor Bracket CAD Files below:

### Solidworks Part File:

https://github.com/ilittle8/design-projects-portfolio/blob/main/docs/assignments/a11/A11%20Motor%20Bracket%20(Remake).SLDPRT

### STEP File:

https://github.com/ilittle8/design-projects-portfolio/blob/main/docs/assignments/a11/A11%20Motor%20Bracket%20(Remake).STEP

## 1. Project Overview

The objective of this project is to design a motorized leadscrew system for a tensile tester. The system uses two leadscrews to produce controlled linear motion of the crosshead.

The design uses one stepper gearmotor per leadscrew. Each motor independently drives one screw, allowing the system to provide the required motion while distributing the torque demand between two motors.

The primary design considerations documented here are the leadscrew geometry, required rotational speed, operating torque, and motor torque-speed performance.

## 2. Leadscrew Geometry

The selected leadscrew is a single-start Acme screw with a nominal diameter of $1/4$ inch and $20$ threads per inch.

For a single-start screw, the lead is equal to the thread pitch:

$$
L = \frac{1}{20}\text{ in/rev}
$$

Converting the lead to millimeters:

$$
L = \frac{25.4}{20}
$$

$$
\boxed{L = 1.27\text{ mm/rev}}
$$

Therefore, one complete revolution of the leadscrew produces $1.27$ mm of linear travel.

## 3. Leadscrew Operating Torque

The calculated operating torque required to drive one leadscrew is:

$$
\boxed{T_{\text{operating}} = 0.635\text{ N}\cdot\text{m}}
$$

Because the design uses two independent motors, each motor is responsible for supplying the operating torque of one leadscrew.

The total operating torque across both screws is:

$$
T_{\text{total}} = 2T_{\text{operating}}
$$

$$
T_{\text{total}} = 2(0.635)
$$

$$
\boxed{T_{\text{total}} = 1.27\text{ N}\cdot\text{m}}
$$

A design factor of safety of $4$ is used to establish the required motor torque.

For each motor:

$$
T_{\text{design}} = 4T_{\text{operating}}
$$

$$
T_{\text{design}} = 4(0.635)
$$

$$
\boxed{T_{\text{design}} = 2.54\text{ N}\cdot\text{m}}
$$

Thus, each motor must provide at least $2.54\text{ N}\cdot\text{m}$ under the relevant operating conditions.

## 4. Motor Selection

The selected motor candidate is the McMaster-Carr NEMA 23 stepper gearmotor, part number 4801N14.

### McMaster Carr Link (CAD FILES CAN BE FOUND IN LINK):
https://www.mcmaster.com/4801N14/

The design uses one motor per leadscrew. Consequently, the motor must independently satisfy the torque and rotational-speed requirements of a single screw.

### 4.1 Required Motor Speed

The assignment specifies a crosshead linear velocity range of $1$ to $50\text{ mm/min}$.

The relationship between linear velocity and screw rotational speed is:

$$
n = \frac{v}{L}
$$

where:

- $n$ is the rotational speed in RPM.
- $v$ is the crosshead linear velocity in mm/min.
- $L$ is the leadscrew lead in mm/rev.

At the minimum crosshead velocity:

$$
n_{\min} = \frac{1}{1.27}
$$

$$
\boxed{n_{\min} = 0.79\text{ RPM}}
$$

At the maximum crosshead velocity:

$$
n_{\max} = \frac{50}{1.27}
$$

$$
\boxed{n_{\max} = 39.37\text{ RPM}}
$$

Therefore, each motor must operate over an approximate speed range of:

$$
\boxed{0.79\text{–}39.37\text{ RPM}}
$$

### 4.2 Torque-Speed Curve Evaluation

The motor's torque-speed curve was evaluated using the manufacturer's published performance data. The referenced curve specifies operation at $24\text{ V DC}$ and $2.2\text{ A}$ using half-stepping.

At approximately $40\text{ RPM}$, the curve indicates an available torque of roughly $700\text{ oz}\cdot\text{in}$.

Converting this value to SI units:

$$
1\text{ oz}\cdot\text{in} = 0.0070616\text{ N}\cdot\text{m}
$$

$$
T_{\text{available}} = 700(0.0070616)
$$

$$
\boxed{T_{\text{available}} \approx 4.94\text{ N}\cdot\text{m}}
$$

The available torque is compared with the required design torque for one motor:

$$
4.94\text{ N}\cdot\text{m} > 2.54\text{ N}\cdot\text{m}
$$

The estimated available torque at the maximum required operating speed exceeds the design torque requirement.

The ratio of estimated available torque to operating torque is:

$$
\frac{T_{\text{available}}}{T_{\text{operating}}} = \frac{4.94}{0.635} 
$$

$$
\boxed{\frac{T_{\text{available}}}{T_{\text{operating}}}\approx 7.78}
$$

This comparison indicates that the motor candidate has sufficient estimated torque capacity at approximately the maximum required screw speed, based on the manufacturer's torque-speed curve.

## 5. Motor Selection Summary

The selected design uses two NEMA 23 stepper gearmotors, with one motor driving each leadscrew.

<img width="1050" height="811" alt="image" src="https://github.com/user-attachments/assets/13ddc33e-5d81-4014-808f-88b20b8ae267" />


The calculated requirements for each motor are:

- Operating torque: $0.635\text{ N}\cdot\text{m}$
- Design torque, using a factor of safety of $4$: $2.54\text{ N}\cdot\text{m}$
- Required rotational speed: $0.79$ – $39.37\text{ RPM}$
- Estimated available torque near $40\text{ RPM}$: $4.94\text{ N}\cdot\text{m}$

<img width="1045" height="773" alt="image" src="https://github.com/user-attachments/assets/3d7df07f-5f37-4ea5-845e-2b41d151fd31" />


Based on the approximate torque-speed curve reading, the selected motor candidate exceeds the calculated design torque requirement at the maximum required operating speed.


## 6. Task 2 — Motor Mount Design

### Knowns

| Parameter | Value |
|---|---:|
| Mount configuration | Adapter plate mounted between the motor bracket and tester frame |
| Motor mounting bracket | Supplied with the selected motor |
| Plate width | 2.90 in |
| Plate length | 2.90 in |
| Selected plate thickness | 0.125 in (1/8 in) |
| Plate material | AISI 1018 cold-drawn steel |
| Assumed material yield strength | 53,700 psi |
| Motor-side mounting pattern | 1.95 in × 1.95 in |
| Motor bracket hole diameter | 0.217 in |
| Frame-side mounting pattern | 2.65 in × 2.65 in |
| Frame-side fastener diameter | 0.250 in |
| Number of motor-side mounting locations | 4 |
| Number of frame-side mounting locations | 4 |
| Operating torque per motor | 5.62 lb·in |
| Frame-side bolt-pattern radius | 1.874 in |
| Calculated frame-side force per fastener | 0.750 lbf |
| Allowable bearing stress | 13,425 psi |
| Calculated minimum plate thickness | 0.000224 in |
| Selected plate thickness compared with calculated minimum | 0.125 in |

### Unknowns

| Parameter | Information Needed |
|---|---|
| Motor-side fasteners | Final fastener diameter, thread size, and length |
| Motor-side tapped holes | Required thread engagement and available plate thickness for tapping |
| Frame-side fasteners | Final bolt length, grade, and thread engagement |
| Frame material | Exact material and properties of the tester frame |
| Plate attachment | Final details of how the plate is secured to the frame |
| Alignment | Final verification that the motor output shaft is aligned with the leadscrew |
| Structural validation | Further verification of the plate, fasteners, and complete torque load path |


### 6.1 Mounting Plate Design

I designed a horizontal steel adapter plate to connect the motor's existing mounting bracket to the top of the tensile tester frame. The adapter plate provides four mounting locations for the motor bracket and four additional mounting locations for attachment to the frame.
<img width="743" height="962" alt="image" src="https://github.com/user-attachments/assets/555e6371-8495-4a90-9fd5-a275b322631e" />

The selected plate dimensions are:

- Plate width: $2.90$ in
- Plate length: $2.90$ in
- Selected material: AISI 1018 cold-drawn steel
- Selected plate thickness: $0.125$ in ($1/8$ in)

The assumed yield strength of AISI 1018 cold-drawn steel is:

$$
S_y=53,700\text{ psi}
$$

### 6.2 Bearing Stress Analysis

I evaluated the bearing stress at the frame-side mounting holes to determine the minimum required plate thickness.

The allowable bearing stress is calculated using the required factor of safety of 4:

$$
\sigma_{b,\text{allow}}=\frac{S_y}{N}
$$

$$
\sigma_{b,\text{allow}}=\frac{53,700}{4}
$$

$$
\boxed{\sigma_{b,\text{allow}}=13,425\text{ psi}}
$$

The operating torque per motor is:

$$
T=0.635\text{ N}\cdot\text{m}
$$

Converting to pound-inches:

$$
T=0.635(8.8507)
$$

$$
T=5.62\text{ lb}\cdot\text{in}
$$

The outer frame mounting pattern consists of four holes arranged in a square with a center-to-center spacing of 2.65 in.

The radius from the center of the bolt pattern to each mounting hole is:

$$
r_f=\sqrt{\left(\frac{2.65}{2}\right)^2+
\left(\frac{2.65}{2}\right)^2}
$$

$$
\boxed{r_f=1.874\text{ in}}
$$

Assuming equal torque distribution among the four mounting fasteners, the force per fastener is:

$$
F_f=\frac{T}{4r_f}
$$

$$
F_f=\frac{5.62}{4(1.874)}
$$

$$
\boxed{F_f=0.750\text{ lbf}}
$$

The bearing stress relationship is:

$$
\sigma_b=\frac{F}{td}
$$

Rearranging to solve for the minimum plate thickness:

$$
t_{\min}=\frac{F}{d\sigma_{b,\text{allow}}}
$$

Using a $0.250$ in frame-side fastener diameter:

$$
t_{\min}=\frac{0.750}{(0.250)(13,425)}
$$

$$
\boxed{t_{\min}=0.000224\text{ in}}
$$

### 6.3 Final Plate Thickness Selection

Based on the bearing-stress calculation, the minimum required plate thickness is approximately $0.000224$ in.

I selected a final plate thickness of:

$$
\boxed{t_{\text{selected}}=0.125\text{ in}}
$$

The selected thickness is substantially greater than the calculated minimum bearing thickness. I chose a standard $1/8$ in steel plate as a practical thickness for the motor adapter.

The calculated minimum is based specifically on the frame-side bearing-stress model and equal distribution of the motor's operating torque among the four frame mounting fasteners. The selected thickness is therefore a preliminary design selection rather than a complete verification of every possible plate failure mode.

### 6.4 CAD Drawing

### Frame-Side Mounting Holes

I designed the adapter plate with four tapped 10-32 holes to secure it to the frame. The holes are arranged in a square pattern with a center-to-center spacing of 2.40 in in both directions. This updated pattern replaces my previous 2.65 in spacing and 1/4 in fastener selection. I did this in order to make sure all the holes fit into my 2.9 inch bracket length and width.

<img width="950" height="792" alt="image" src="https://github.com/user-attachments/assets/4241f902-8a71-44e1-be51-c8cf3da11a57" />

## 6. Task 2 — Motor Mount Design REVISION

### Knowns

| Parameter | Value |
|---|---:|
| Mount configuration | Custom motor bracket mounted between the motor and tester frame |
| Bracket width | 2.90 in |
| Bracket length | 2.90 in |
| Bracket overall height | 1.71875 in |
| Central coupling bore diameter | 1.078125 in |
| Inner motor-side holes | Four tapped blind holes |
| Inner tapped-hole depth | 0.859375 in |
| Outer frame-side holes | Four tapped through-holes |
| Plate/bracket material | AISI 1018 cold-drawn steel (previously selected; verify for revised part) |
| Assumed material yield strength | 53,700 psi |
| Motor-side mounting pattern | 1.95 in × 1.95 in (verify against current CAD) |
| Motor bracket hole diameter | 0.217 in (existing motor-bracket interface dimension) |
| Frame-side mounting pattern | 2.40 in × 2.40 in |
| Frame-side thread | 10-32 tapped through-holes |
| Number of inner motor-side mounting locations | 4 |
| Number of outer frame-side mounting locations | 4 |

### Unknowns

| Parameter | Information Needed |
|---|---|
| Motor-side fasteners | Final fastener diameter, thread size, and length for the four inner tapped holes |
| Inner blind-hole engagement | Verify that 0.859375 in of tapped depth provides sufficient thread engagement |
| Frame-side fasteners | Final 10-32 fastener length, grade, and engagement |
| Coupling clearance | Verify the actual coupling outside diameter and whether additional clearance is needed around the 1.078125 in bore |
| Coupling installation | Verify that both hubs and the spider can be installed and rotate without contacting the bracket |
| Frame material | Exact material and properties of the tester frame |
| Alignment | Verify that the motor output shaft, coupling, and leadscrew are properly aligned |
| Structural validation | Verify the revised bracket, tapped holes, fasteners, and complete torque load path using the final CAD geometry |

### 6.1 Revised Motor Bracket Design

I redesigned the motor bracket to accommodate the McMaster-Carr L050 spider coupling. The revised geometry provides a central opening for the coupling and separate mounting locations for attaching the motor and the bracket to the tensile tester frame.

The updated bracket has an overall height of **1.71875 in**. I selected this dimension to match the full assembled height of the L050 spider coupling.

I also added a central through-hole with a diameter of **1.078125 in**. This opening is sized to match the outside diameter of the coupling so that the coupling can occupy the center of the bracket without interfering with its rotation. The actual coupling dimensions should be checked against the supplier drawing, and the bore clearance should be verified before manufacturing.

The revised bracket uses two separate sets of tapped holes:

- **Inner motor-mounting holes:** I added four tapped blind holes to secure the motor to the bracket. Each hole has a tapped depth equal to one-half of the bracket's overall height.

$$
d_{\text{inner}}=\frac{1.71875}{2}
$$

$$
\boxed{d_{\text{inner}}=0.859375\text{ in}}
$$

- **Outer frame-mounting holes:** I added four tapped holes that extend completely through the bracket. These holes secure the bracket to the tensile tester frame.

The inner holes are used exclusively to attach the motor, while the outer holes are used to attach the bracket to the frame. Separating these mounting locations allows the motor and coupling to be positioned within the bracket while maintaining a separate frame attachment.

The existing material selection is AISI 1018 cold-drawn steel, with an assumed yield strength of:

$$
S_y=53,700\text{ psi}
$$

The material selection and assumed yield strength must be verified for the revised bracket before completing the final structural analysis.


### 6.2 Revised Bracket Geometry and Mounting Arrangement

The final bracket geometry incorporates the following dimensions:

| Feature | Dimension |
|---|---:|
| Overall bracket height | 1.71875 in |
| Central through-hole diameter | 1.078125 in |
| Inner tapped-hole depth | 0.859375 in |
| Frame-side mounting pattern | 2.40 in × 2.40 in |
| Frame-side thread | 10-32 |
| Number of inner tapped holes | 4 |
| Number of outer tapped through-holes | 4 |

The center opening accommodates the L050 coupling, while the inner and outer tapped holes provide the two separate mounting interfaces.

The four outer frame-side holes are arranged in a square pattern with a center-to-center spacing of 2.40 in in both directions. This pattern replaces my previous 2.65 in spacing and 1/4 in fastener selection. I selected the 2.40 in pattern to keep the mounting holes within the 2.90 in bracket length and width.

The four inner tapped blind holes secure the motor to the bracket. Their tapped depth is 0.859375 in, which is half of the bracket's overall height.

<img width="710" height="506" alt="image" src="https://github.com/user-attachments/assets/c1b1e081-ebb6-478b-9bd1-45f9dc671cf7" />


### 6.3 Structural Analysis and Verification

The previous bearing-stress calculation used the older 2.65 in frame-side mounting pattern and a 0.250 in fastener diameter. Those assumptions no longer represent the revised bracket geometry.

Therefore, the previous calculated minimum thickness of 0.000224 in should not be treated as a verified result for the updated design.

The revised bracket requires a new structural analysis that accounts for its actual geometry, including:

- The 1.71875 in overall height.
- The 1.078125 in central coupling opening.
- The four inner tapped blind holes.
- The four outer tapped through-holes.
- The final fastener dimensions and thread engagement.
- The actual material properties.

The inner blind holes must provide sufficient thread engagement to secure the motor without breaking through the bracket. The outer through-tapped holes must provide adequate engagement with the selected frame fasteners.

The central opening also removes material from the bracket, so its effect on the bracket's strength and stiffness must be considered. The bracket should be checked for bearing, shear, bending, and deflection as appropriate to the actual loading and attachment arrangement.

The revised CAD geometry will be used for the updated calculations rather than relying on the previous mounting-plate analysis.

## Task 3 — Coupler Selection and Torsional Analysis

### 1. Coupler Selection

<img width="2388" height="1668" alt="38711" src="https://github.com/user-attachments/assets/9428dbdf-8c5b-45ad-a9b2-01ab5acd3a0f" />

#### Known and Unknown Variables

**Known variables**

| Variable | Description | Value |
|---|---|---:|
| $T_{op}$ | Operating torque per motor | 0.635 N·m |
| $N$ | Design factor of safety | 4 |
| $T_d$ | Design torque per coupling | 2.54 N·m |
| $T_d$ | Design torque per coupling, converted | 22.48 in·lbf |
| Hub trade size | Coupling size | L050 |
| Motor-side nominal bore | Hub 6408K11 | 16 mm |
| Leadscrew-side nominal bore | Hub 6408K92 | 1/4 in (6.35 mm) |
| Spider material | Spider 6408K91 | Hytrel |
| Hub material | Hubs 6408K11 and 6408K92 | Iron |
| Spider maximum torque | McMaster catalog value | 50 in·lbf |
| Maximum catalog speed | L050 spider | 18,000 RPM |

**Unknown variables and required verification**

- Confirm that the keyed 16 mm motor-side hub can securely retain the motor's D-shaped output shaft.
- Confirm the motor shaft engagement length and set-screw location.
- Confirm that the 1/4 in hub bore and set screw securely fit the actual leadscrew end.
- Verify the complete coupling dimensions and hub cross-sections using the supplier drawings.
- Verify that the coupling's catalog torque and speed limits are suitable for the actual operating duty and service conditions.
- Confirm that the motor and leadscrew are aligned within the coupling's published misalignment limits.

I changed the coupling selection from a one-piece NBK jaw coupling to a **McMaster-Carr L050 spider coupling**. A spider coupling consists of two metal hubs with a flexible center element (the spider) between them. The spider transmits torque while allowing a limited amount of angular and parallel misalignment.

The selected L050 assembly uses the following three components:

| Component | McMaster-Carr Part Number | Description | Material / Shaft Interface |
|---|---|---|---|
| Motor-side hub | [6408K11](https://www.mcmaster.com/6408K11-6413K119/) | L050 keyed hub, 16 mm bore | Iron; keyed bore |
| Leadscrew-side hub | [6408K92](https://www.mcmaster.com/6408K92-6408K111/) | L050 hub, 1/4 in bore | Iron; set-screw shaft mount |
| Flexible spider | [6408K91](https://www.mcmaster.com/6408K91/) | L050 spider | Hytrel |


The two hubs must have the same L050 coupling trade size as the spider. McMaster identifies the 6408K11 hub as a keyed 16 mm option and the 6408K92 hub as an iron set-screw hub available with a 1/4 in bore. The selected spider is the L050 Hytrel version.

**Important fit verification:** The motor output shaft is 16 mm in diameter and has a D-shaped profile. Although the selected motor-side hub has a 16 mm bore, McMaster lists it as a keyed hub. A keyed bore is not automatically a confirmed match for a D-shaped shaft. The shaft must be checked against the hub drawing, and the set-screw/retention arrangement must be verified before ordering or manufacturing. The 1/4 in leadscrew-side bore also needs to be checked against the actual leadscrew end.

### 2. Coupling Specifications

| Specification | Selected L050 Spider Coupling |
|---|---:|
| Manufacturer / supplier | McMaster-Carr |
| Coupling type | L050 spider (jaw) coupling |
| Motor-side hub | 6408K11 |
| Leadscrew-side hub | 6408K92 |
| Spider | 6408K91 |
| Hub material | Iron |
| Spider material | Hytrel |
| Motor-side nominal bore | 16 mm |
| Leadscrew-side nominal bore | 1/4 in (6.35 mm) |
| Maximum catalog torque for selected spider | 50 in·lbf |
| Maximum catalog speed | 18,000 RPM |
| Catalog parallel misalignment capability | 0.015 in |
| Catalog angular misalignment capability | 0.5° |

<img width="724" height="554" alt="image" src="https://github.com/user-attachments/assets/6fbdb7e9-d73b-4462-bc3c-3a25f51e00ca" />

<img width="749" height="493" alt="image" src="https://github.com/user-attachments/assets/bcfd0c28-ad29-430c-9fcf-85c321f0432d" />

<img width="710" height="547" alt="image" src="https://github.com/user-attachments/assets/22213e33-a531-4367-b74c-4bd55ed638af" />


McMaster describes Hytrel as a relatively stiff spider material that provides direct torque transfer and less vibration damping than softer spider materials. The spider coupling's flexible center accommodates limited misalignment; it does not eliminate the need to align the motor and leadscrew carefully.

### 3. Design Torque and Catalog Capacity Check

Each motor drives one leadscrew, so each coupling transmits the torque from one motor.

The operating torque per motor is:

$$
T_{op}=0.635\text{ N}\cdot\text{m}
$$

Using the design factor of safety of 4:

$$
T_d=4T_{op}
$$

$$
T_d=4(0.635)
$$

$$
\boxed{T_d=2.54\text{ N}\cdot\text{m}}
$$

Converting the design torque to pound-inches:

$$
T_d=2.54(8.8507)
$$

$$
\boxed{T_d\approx22.48\text{ in}\cdot\text{lbf}}
$$

The selected L050 Hytrel spider has a published maximum torque of 50 in·lbf. The ratio of the catalog maximum torque to the required design torque is:

$$
\text{Torque Ratio}=\frac{50}{22.48}
$$

$$
\boxed{\text{Torque Ratio}\approx2.22}
$$

The published maximum torque is greater than the calculated design torque. This is a preliminary catalog-capacity check; the manufacturer's maximum torque value should not be treated as a substitute for checking the complete coupling's service conditions, duty cycle, and shaft retention.

### 4. Torsional Loading and Analysis

Each coupling transmits the design torque from one motor to one leadscrew:

$$
\boxed{T_d=2.54\text{ N}\cdot\text{m}}
$$

The torque is transferred from the motor shaft into the motor-side iron hub, through the Hytrel spider, into the leadscrew-side iron hub, and finally into the leadscrew.

The coupling components do not have the same geometry as the previously considered NBK MJC-30-WH coupling. Therefore, the earlier calculations based on a 30 mm outside diameter, 16 mm and 6.35 mm hub bores, and A2017 aluminum hubs do **not** describe this L050 coupling and should not be used as its hub stress results.

A numerical torsional shear-stress calculation for the iron hubs requires the actual hub cross-sectional dimensions from the McMaster/manufacturer drawings. Those dimensions have not yet been verified. The spider's published maximum torque provides a separate catalog-level capacity check, but it does not replace a detailed stress analysis of the hubs or verification of the shaft-to-hub connections.



### 5. Coupler Selection Summary

The updated design uses two iron L050 hubs and one Hytrel spider. The motor-side hub has a nominal 16 mm bore, and the leadscrew-side hub has a nominal 1/4 in bore. The selected spider has a published maximum torque of 50 in·lbf, compared with the required design torque of approximately 22.48 in·lbf.

The catalog torque check is promising, but the coupling is not yet a confirmed drop-in fit because the motor-side hub is listed as keyed while the motor shaft is D-shaped. That shaft-retention detail must be resolved before the coupling is finalized.

McMaster-Carr component links:

- Motor-side hub: https://www.mcmaster.com/6408K11-6413K119/
- Leadscrew-side hub: https://www.mcmaster.com/6408K92-6408K111/
- Hytrel spider: https://www.mcmaster.com/6408K91/
- Spider coupling catalog: https://www.mcmaster.com/products/spider-couplings/

## Lessons Learned

Throughout this design process, I learned the importance of translating the requirements of a mechanical system into practical component selections and design decisions. Selecting a motor required more than checking its rated torque; I also had to consider the required operating speed and verify that sufficient torque was available across the entire operating range.

I also learned that designing mounting hardware requires careful attention to hole patterns, fastener dimensions, alignment, and load transfer. The motor already included a mounting bracket, so I designed an adapter plate to connect that bracket to the frame rather than unnecessarily redesigning the motor mount itself. I also recognized the importance of distinguishing between a clearance-hole diameter and the actual fastener diameter.

For the coupler, I learned that compatibility involves more than matching shaft diameters. I needed to consider the hub bores, shaft-retention method, spider material, torque capacity, and allowable misalignment. The updated design uses two iron L050 hubs with a Hytrel spider. I also learned that a catalog bore diameter alone does not prove compatibility with a D-shaped motor shaft; the hub's keyed geometry and retention method must be checked against the actual shaft.

Finally, I learned that engineering calculations must be tied to the actual geometry and assumptions of the design. A calculated minimum thickness is not automatically the same as a sensible manufacturing thickness. I chose a 1/8-inch adapter plate, recognizing that practical considerations such as rigidity, fabrication, and fastener engagement also matter when finalizing a design.




