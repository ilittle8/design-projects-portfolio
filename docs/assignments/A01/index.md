# A1 – [Create Portfolio]

## Objective

### 1. Analyze Portfolio

## Analyze

#### Analyzing Jackson Hanish's portfolio (https://instructure.charlotte.edu/eportfolios/4882/home/about-me)
  Jackson Hanish's portfolio is very well organized. Each element is accessible in an average of ~10 seconds max. While his description allows the reader to get a functional and usable understanding of the work he did, his use of language would benefit from an increased level of specificity.  Particularly, in assignment 2, he says "... two design concepts were considered. The first consisted of eight total members with smaller angles forming multiple triangular sections. The second used four primary members and a top cross beam to carry the applied loads". When he says 'smaller angles', I, the reader, am immediately confused, thinking to myself: "Smaller in reference to *what?*". After some closer reading, I am able to imply that the angles in his first configuration are smaller than his second configuration, but this is not made clear. Fortunately, his use of language does not stop his work from being reproducible. He not only presents why he makes design choices, but also reveals his governing equations, statics calculations, and results within a coherent and properly dimensioned manner. Due to his excellent presentation of information, his results are completely reproducible without any intervention from Jackson Hanish himself. In his introduction, discussion, and results he maintains a professional tone that I believe any employer would find no issue with.

#### Analyzing ZachIq's portfolio (https://github.com/Zachlq/Professional_Portfolio/tree/main).
  One part of ZachIq's portfolio I was impressed with is how simple it is. All elements are easily accessible and, at first glance, easily understood. I am quite confident that his work can be easily accessed in under 60 seconds as a result of the intuitive structure of his portfolio. To review his methods, I viewed his pipeline named "Medium". The results given were easily reproducible, as he attached functional and runnable python code directly to his description of his pipeline. However, the process itself is not easily reproducible. His code lacks comments of any kind, making it very difficult to understand the functions of each block of his code. Overall, viewing the work as results and process combined, his work should be considered reproducible, but only with assistance from the creator. Unfortunately, his listing does not show his decision making process in writing the code, only the final results of his project. It is hard to gather any information about why one function was chosen over another or how the API interacts with his code. ZachIq's use of language has a sharp turn from overly casual to fairly professional between his 'README' and his project descriptions. For example, his 'README' file for his portfolio features his dog as well as phrases like "Don't be --evil-- boring"; the tone of his project contents lends to a "business casual" impression, though. In these project descriptions, he uses proper english and is clear and concise, but typically uses phrases like "I've" instead of "I have", and other common shortenings of language. This specific use of language generally acceptable within the workplace, though.

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
  *(Note: Embed your component photo here)*
  * **Single-Piece Hexagonal L-Rod:** Features a constant 6-sided cross-section bent at a $90^\circ$ angle. The six flat driving faces provide broad surface contact against the fastener socket, spreading driving forces to minimize stress concentration. The $90^\circ$ elbow geometry provides dual leverage options: the long leg maximizes moment arm length for high torque output, while the short leg allows rapid engagement in confined spaces.
* **Patent Research & Alternatives:**
  * **Patent Details:** US Patent US20160271766A1 (Inventors: Sheng-In Lin et al.).
  * **Alternative Design Solutions:** 
    1. *Torx / Star Drive Key:* Utilizes a 6-lobed head geometry with a $15^\circ$ drive angle to further reduce radial stress and eliminate cam-out forces.
    2. *Flathead / Slotted Screwdriver:* Relies on a single flat blade engaged in a straight channel, which provides low surface area contact and is susceptible to lateral slip under torque.
  * **Engineered Design Decision:** The patent defines specific geometric leg-length ratios ($0.3L_2 \le L_1 \le 0.5L_2$, where $L_1$ is the short leg and $L_2$ is the long leg). This design decision ensures the short leg is long enough ($\ge 50\text{ mm}$) for adequate manual grip while maintaining sufficient leverage length on the primary arm.

<img width="4284" height="5712" alt="IMG_5053" src="https://github.com/user-attachments/assets/b88dfa10-cc31-480a-b99f-9e51bfb0a586" />
<img width="4284" height="5712" alt="IMG_5051" src="https://github.com/user-attachments/assets/655670d7-308e-4c80-b10c-6a156f9b0ab4" />




## Decide


## Communicate

