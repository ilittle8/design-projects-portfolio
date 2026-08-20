# A1 – [Create Portfolio]

## Objective

### 1. Analyze Portfolio

## Analyze

### Task A: Reviewing Portfolios

#### Review 1: Jackson Hanish Portfolio

* **Navigability:** The repository is structured logically, utilizing dedicated folders for system diagrams, code, and CAD models. Headers and a descriptive table of contents guide the reader through the subassemblies sequentially, allowing rapid retrieval of specific sub-system documentation.
* **Reproducibility:** The documentation includes bill-of-materials tables with part numbers, hardware schematics, and raw CAD files. An external reader can fully recreate the assembly and re-run software scripts without missing component dependencies.
* **Evidence of Reasoning:** Design selections are justified through structural calculation data and load comparisons rather than intuition. However, the author occasionally uses vague spatial descriptions, such as stating components were mounted at "smaller angles," without specifying the exact angular offset in degrees or referencing a geometric datum.
* **Tone:** The writing maintains an objective, formal engineering register appropriate for peer review. The technical descriptions avoid colloquial language, subjective claims, and informal shorthand.

#### Review 2: ZachIq Portfolio

* **Navigability:** The main landing page provides a high-level overview, but navigating into deeper subsystems requires searching through flat folder hierarchies without internal markdown links. Finding specific CAD revisions or bill-of-materials files requires extra manual effort.
* **Reproducibility:** Software setup instructions are partially documented. While main execution scripts are included, the documentation omits specific library version dependencies and pin-out wiring schematics, preventing full hardware replication without initial trial-and-error troubleshooting.
* **Evidence of Reasoning:** Trade-offs between component cost, weight, and material strength are explicitly quantified using comparative matrix tables and finite element analysis (FEA) stress plots.
* **Tone:** The primary documentation adheres to standard corporate communication norms and technical rigor. However, the internal code comments shift to an informal register, using conversational remarks and subjective notes that depart from standard documentation practices.

### Task B: Product Analysis

#### Analyzing Hex Key / Allen Wrench ([US Patent US20160271766A1](https://patents.google.com/patent/US20160271766A1/en))

* **Primary Function:** Transmits manual rotational torque applied by the user into pure clamping preload within an internal hexagonal socket fastener while preventing fastener head cam-out or drive-wall deformation.
* **Governing Mechanical Model:** Torsional shear stress in a prismatic bar subjected to uniform torsion (Coulomb Torsion Model):
  $$\tau_{max} = \frac{T \cdot r}{J}$$
  * **Variables:** 
    * $\tau_{max}$: Maximum torsional shear stress occurring along the midpoints of the outer flat hexagonal faces ($Pa$)
    * $T$: Applied input torque along the drive axis ($N\cdot m$)
    * $r$: Inscribed radius from the center axis to the flat face midpoint ($m$), where $r = \frac{W}{2}$
    * $J$: Polar moment of inertia for a regular hexagonal cross-section ($m^4$), defined as $J \approx 0.133 \cdot W^4$ (where $W$ is width across flats)
  * **Validating Assumption:** The key material operates within its linear elastic regime Hooke's Law ($\tau = G \cdot \gamma$) under homogenous material properties, neglecting stress concentration effects at the $90^\circ$ elbow bend.
* **Component Geometry & Function:**
<img width="4284" height="5712" alt="IMG_5051" src="https://github.com/user-attachments/assets/655670d7-308e-4c80-b10c-6a156f9b0ab4" />

  * **Single-Piece Hexagonal L-Rod:** Features a constant 6-sided cross-section bent at a $90^\circ$ angle. The six flat driving faces provide broad surface contact against the fastener socket, spreading driving forces to minimize stress concentration. The $90^\circ$ elbow geometry provides dual leverage options: the long leg maximizes moment arm length for high torque output, while the short leg allows rapid engagement in confined spaces.
* **Patent Research & Alternatives:**
  * **Patent Details:** US Patent US20160271766A1 (Inventors: Sheng-In Lin et al.).
  * **Alternative Design Solutions:** 
    1. *Torx / Star Drive Key:* Utilizes a 6-lobed head geometry with a $15^\circ$ drive angle to further reduce radial stress and eliminate cam-out forces.
    2. *Flathead / Slotted Screwdriver:* Relies on a single flat blade engaged in a straight channel, which provides low surface area contact and is susceptible to lateral slip under torque.
  * **Engineered Design Decision:** The patent defines specific geometric leg-length ratios ($0.3L_2 \le L_1 \le 0.5L_2$, where $L_1$ is the short leg and $L_2$ is the long leg). This design decision ensures the short leg is long enough ($\ge 50\text{ mm}$) for adequate manual grip while maintaining sufficient leverage length on the primary arm.





## Decide


## Communicate

