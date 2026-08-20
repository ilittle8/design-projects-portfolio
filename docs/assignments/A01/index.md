# A1 – [Create Portfolio]

## Objective

### 1. Analyze Portfolio

## Analyze

#### Analyzing Jackson Hanish's portfolio (https://instructure.charlotte.edu/eportfolios/4882/home/about-me)
  Jackson Hanish's portfolio is very well organized. Each element is accessible in an average of ~10 seconds max. While his description allows the reader to get a functional and usable understanding of the work he did, his use of language would benefit from an increased level of specificity.  Particularly, in assignment 2, he says "... two design concepts were considered. The first consisted of eight total members with smaller angles forming multiple triangular sections. The second used four primary members and a top cross beam to carry the applied loads". When he says 'smaller angles', I, the reader, am immediately confused, thinking to myself: "Smaller in reference to *what?*". After some closer reading, I am able to imply that the angles in his first configuration are smaller than his second configuration, but this is not made clear. Fortunately, his use of language does not stop his work from being reproducible. He not only presents why he makes design choices, but also reveals his governing equations, statics calculations, and results within a coherent and properly dimensioned manner. Due to his excellent presentation of information, his results are completely reproducible without any intervention from Jackson Hanish himself. In his introduction, discussion, and results he maintains a professional tone that I believe any employer would find no issue with.

#### Analyzing ZachIq's portfolio (https://github.com/Zachlq/Professional_Portfolio/tree/main).
  One part of ZachIq's portfolio I was impressed with is how simple it is. All elements are easily accessible and, at first glance, easily understood. I am quite confident that his work can be easily accessed in under 60 seconds as a result of the intuitive structure of his portfolio. To review his methods, I viewed his pipeline named "Medium". The results given were easily reproducible, as he attached functional and runnable python code directly to his description of his pipeline. However, the process itself is not easily reproducible. His code lacks comments of any kind, making it very difficult to understand the functions of each block of his code. Overall, viewing the work as results and process combined, his work should be considered reproducible, but only with assistance from the creator. Unfortunately, his listing does not show his decision making process in writing the code, only the final results of his project. It is hard to gather any information about why one function was chosen over another or how the API interacts with his code. ZachIq's use of language has a sharp turn from overly casual to fairly professional between his 'README' and his project descriptions. For example, his 'README' file for his portfolio features his dog as well as phrases like "Don't be --evil-- boring"; the tone of his project contents lends to a "business casual" impression, though. In these project descriptions, he uses proper english and is clear and concise, but typically uses phrases like "I've" instead of "I have", and other common shortenings of language. This specific use of language generally acceptable within the workplace, though.

#### Analyzing Hexagonal L-Key / Allen Wrench ([US Patent US2081515A](https://patents.google.com/patent/US2081515A/en))
* **Primary Function:** Transmits manual input torque from the user's hand to a hexagonal socket fastener, generating pure axial clamping preload while preventing fastener head cam-out or cross-sectional stripping.
* **Governing Mechanical Model:** Torsional shear stress in a prismatic bar under pure torsion (Coulomb torsion theory):
  $$\tau_{max} = \frac{T \cdot r}{J}$$
  * **Variables:** 
    * $\tau_{max}$: Maximum torsional shear stress occurring at the midpoints of the flat hexagonal faces ($Pa$)
    * $T$: Manual torque applied to the long handle arm ($N\cdot m$)
    * $r$: Inscribed radius (half of the distance across flat faces, $W/2$) ($m$)
    * $J$: Polar moment of inertia for a hexagonal cross-section ($m^4$), where $J \approx 0.133 \cdot W^4$ (with $W$ as width across flats)
  * **Validating Assumption:** The material operates strictly within its elastic deformation regime Hooke's Law ($\tau = G \cdot \gamma$), assuming uniform material homogeneity along the bent rod without significant stress concentration failure at the elbow.
* **Component Geometry & Function:**
  *(Note: Embed your component photo here)*
  * **Single-Piece Hexagonal L-Rod:** Features a constant 6-sided cross-section bent at a right angle ($90^\circ$). The 6-point geometry creates broad surface contact against the fastener socket, maximizing torque transfer. The $90^\circ$ elbow configuration provides two distinct leverage options: the long arm yields higher mechanical advantage (torque leverage), while the short arm allows high-speed rotation in tight spatial clearances.
* **Patent Research & Alternatives:**
  * **Patent Details:** US Patent US2081515A (Inventor: William G. Allen).
  * **Alternative Design Solutions:** 
    1. *Torx / Star Key (Internal Lobular Drive):* Uses a 6-pointed star geometry with $15^\circ$ drive angles to reduce radial stress concentration and eliminate cam-out.
    2. *Flathead / Slotted Screwdriver:* Relies on a single flat blade in a straight slot, prone to sliding out under high torque.
  * **Engineered Design Decision:** The decision to utilize a constant hexagonal cross-section along a simple $90^\circ$ bent wire rod allows cold-drawing manufacturing from high-tensile alloy steel without expensive machining, while offering dual-lever arm options from a single part.


## Decide


## Communicate

