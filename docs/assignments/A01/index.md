# A1 – Create Portfolio

## Objectives

### 1. Analyze
### 2. Decide
### 3. Communicate

## Analyze

### Task A: Portfolio Analysis

<img width="863" height="413" alt="image" src="https://github.com/user-attachments/assets/6c597177-a0ea-42ac-bbd1-2305b5123a1c" />


#### Review 1: ([Jackson Hanish's Portfolio](https://instructure.charlotte.edu/eportfolios/4882/home/about-me))

- Jackson Hanish's portfolio is very well organized. Each element is accessible in an average of ~10 seconds max. While his description allows the reader to get a functional and usable understanding of the work he did, his use of language would benefit from an increased level of specificity.  I

- In assignment 2, he says "... two design concepts were considered. The first consisted of eight total members with smaller angles forming multiple triangular sections. The second used four primary members and a top cross beam to carry the applied loads". When he says 'smaller angles', I, the reader, am immediately confused, thinking to myself: "Smaller in reference to *what?*". After some closer reading, I am able to imply that the angles in his first configuration are smaller than his second configuration, but this is not made clear. 

- Fortunately, his use of language does not stop his work from being reproducible. He not only presents why he makes design choices, but also reveals his governing equations, statics calculations, and results within a coherent and properly dimensioned manner. 

- Due to his excellent presentation of information, his results are completely reproducible without any intervention from Jackson Hanish himself. In his introduction, discussion, and results he maintains a professional tone that I believe any employer would find no issue with.


#### Review 2: ([ZachIq's Portfolio](https://github.com/Zachlq/Professional_Portfolio))

- One part of ZachIq's portfolio I was impressed with is how simple it is. All elements are easily accessible and, at first glance, easily understood. I am quite confident that his work can be easily accessed in under 60 seconds as a result of the intuitive structure of his portfolio. 

- To review his methods, I viewed his pipeline named "Medium". The results given were easily reproducible, as he attached functional and runnable python code directly to his description of his pipeline. However, the process itself is not easily reproducible. His code lacks comments of any kind, making it very difficult to understand the functions of each block of his code. 

- Overall, viewing the work as results and process combined, his work should be considered reproducible, but only with assistance from the creator. Unfortunately, his listing does not show his decision making process in writing the code, only the final results of his project. It is hard to gather any information about why one function was chosen over another or how the API interacts with his code. 

- ZachIq's use of language has a sharp turn from overly casual to fairly professional between his 'README' and his project descriptions. For example, his 'README' file for his portfolio features his dog as well as phrases like "Don't be --evil-- boring"; the tone of his project contents lends to a "business casual" impression, though. In these project descriptions, he uses proper english and is clear and concise, but typically uses phrases like "I've" instead of "I have", and other common shortenings of language. This specific use of language generally acceptable within the workplace, though.


### Task B: Product Analysis

<img width="880" height="641" alt="image" src="https://github.com/user-attachments/assets/42f29f05-6a07-4132-95bd-34a568ab52b4" />


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

<img width="576" height="790" alt="image" src="https://github.com/user-attachments/assets/61055c4a-a778-4710-8990-b1650d4ce71a" />


1. **Homepage identity:** A visitor must immediately understand engineering fundamentals in order to correctly interpret the content of this portfolio. The nested structure of this portfolio's documents is helpful for the reader, as each folder title accurately describes the contained contents in 1-2 words. This allows for easy navigation of the portfolio's contents.
   
3. **One Intentional Customization:** I customized the homepage on GitHub (the README.md file) to have a red title and I deleted the local preview instructions. Since my portfolio is a professional document, I want to remove any information that is not relevant to the reader/intended audience. I also chose to make the title a different font and color from the rest of the text in order for the reader to be able to more quickly identify and understand what they are looking at.

4. **Your Documentation Standard:** Every assignment will contain enough information for another engineer to be able to understand my work with minimal questions as to what the assignment is and how I came to my conclusion(s).

## Communicate

<img width="580" height="610" alt="image" src="https://github.com/user-attachments/assets/2e5d43dc-e256-4b71-95e4-82101b4a7e24" />

Please refer to [About Me] to see my work.


