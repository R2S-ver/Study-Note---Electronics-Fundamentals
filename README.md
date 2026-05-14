<div align="center">

<img alt="LOGO" src="https://github.com/R2S-ver/Study-Electronics-Fundamentals/blob/main/assets/images/Banner 3.png" style="max-width: 100; height: auto;" width="256" />

# Personal studylogbook of electronic fundamentals
🌐Language: [English](https://github.com/R2S-ver/Study-Electronics-Fundamentals/blob/main/README.md) | [中文](https://github.com/R2S-ver/Study-Electronics-Fundamentals/blob/Chinese/README.md)

Welcome to my learning repository! 
This project documents my self-study journey in the world of electricity and hardware. I am starting from the very basics of electrical safety and slowly diving into component-level circuit design. 
Currently, this repository focuses on **hardware fundamentals** and **analog electronics**, without involving microcontrollers (like Arduino) or digital logic programming yet.

To better internalize these concepts and understand their practical applications, I have included real-world examples and case studies for each component. This "theory + application" approach helps me review more effectively and bridges the gap between textbook knowledge and actual engineering practice.

*The images used in this repository are for educational and self-study purposes only. If you are the copyright owner of any image used here and would like it removed, please contact me.*

>  **⚠️ Note on Regional Standards & AI Optimization:** The electrical safety analysis and examples documented here are based on my local usage scenario in **The Netherlands (Europe)**. Voltage standards, electrical panel structures, protective mechanisms and safety regulations (like NEN 1010) vary significantly by country. Be aware of your local regulations when working with electricity. *Additionally, to ensure the precision of technical phrasing and professional terminology, AI assistance was utilized to optimize and refine this documentation.*

</div>

# **Table of Contents**
- [Electrical safety at home](#electrical-safety) <br>
  1\. [Introduction & Project Scope](#1-introduction--project-scope) <br>
  2\. [Protective Mechanisms in the Household Electrical System](#2-protective-mechanisms-in-the-household-electrical-system) <br>
  3\. [Potential Risks in Household Power Usage](#3-potential-risks-in-household-power-usage) <br>
  4\. [Practical Research](#practical-research) <br>
  5\. [References](#refs-electrical) <br>
- [Voltage and current](#voltage-and-current) <br>
  1\. [Simple Explaination](#1-simple-explaination) <br>
  2\. [Complex Explaination](#2-complex-explaination) <br>
  3\. [Kirchhoff’s Laws](#3-kirchhoffs-laws) <br>
- [Basic electrical components](#basic-electrical-components) <br>
  1\. [Resistor](#Resistor) <br>
     &nbsp;&nbsp; 1.1\. Voltage Dropping <br>
     &nbsp;&nbsp; 1.2\. Voltage Comparator <br>
  2\. [Capacitor](#Capacitor) <br>
  3\. [Conductor](#Conductor) <br>
     &nbsp;&nbsp; 3.1\. Low-pass and High-pass Filter <br>
  4\. [Diode](#Diode) <br>
     &nbsp;&nbsp; 4.1\. Rectifier Bridge <br>
  5\. [Transistor](#Transistor) <br>
  6\. [Mosfet](#Mosfet) <br>
  7\. [Linear and Switching Power Supply](#Linear-and-Switching-Power-Supply) <br>
     &nbsp;&nbsp; 7.1\. SMPS analysis <br>
  8\. [Practical skills](#practical-skills) <br>
  9\. [References](#refs-components) <br>
----------------------------

<details id="electrical-safety" open><summary>
  
## 🟪Electrical safety
</summary>
    <details id="1-introduction--project-scope"><summary>
      
### 🟦1. Introduction & Project Scope
</summary>
<img alt="1" src="https://github.com/R2S-ver/Study-Electronics-Fundamentals/blob/main/assets/images/1.png" width="512" height="512" /> <br>
This section focuses on electrical safety at home, specifically in my personal workspace (my bedroom) and the equipment used within it. <br>

**Goals of this study:**
- Systematically map the power distribution structure and usage patterns.
- Identify potential safety risks.
- Identify the main energy-consuming devices.
- Design safe, reliable, and feasible solutions for energy savings.
    </details>
    <details id="2-protective-mechanisms-in-the-household-electrical-system"><summary>
### 🟦2. Protective Mechanisms in the Household Electrical System
</summary>

In Dutch homes, the distribution board (groepenkast) is located in the meter cupboard. The structure must comply with the **NEN 1010** safety regulations. 
The power enters through the grid connection and passes through the following main safety components:

* **Main Fuse & Main Switch:** For total system shutdown.
* **Residual Current Device:** Protects against electrocution by detecting leakage currents.
* **Circuit Breakers :** Distributes the installation into groups. Heavy consumers (like induction cooktops) get a separate 1-phase or 3-phase group with higher capacity and dedicated protection.
* **Grounding:** Provides a safe path for fault currents.

<img alt="2" src="https://github.com/R2S-ver/Study-Electronics-Fundamentals/blob/main/assets/images/2.png" width="512" height="512" /> <br>
#### 🟩Circuit Breakers: 1P vs. 2P
* **1P Breaker:** Interrupts the circuit, but the appliance remains connected to the grid via the neutral wire (N).
* **2P / 1P+N Breaker:** Interrupts **both** conductors (Phase and Neutral). 
* **Why is full isolation important?** With a 1P breaker, the neutral remains connected. In the event of a fault or incorrect wiring, the appliance could still carry voltage. A 2P breaker ensures complete electrical isolation and a safer shutdown.
<img alt="4" src="https://github.com/R2S-ver/Study-Electronics-Fundamentals/blob/main/assets/images/4.png" width="512" height="512" /> <br>
#### 🟩Trip Characteristics
Circuit breakers protect against overload and short circuits by automatically switching off. The trip characteristic determines how fast the breaker reacts to a current spike (e.g., when turning on a device).
* Common types: **B, C, D, K, Z, and MA**.
* The difference lies in the current value at which the breaker trips magnetically, expressed as a multiple of the nominal current (In). (e.g., C-curves are better for devices with higher inrush currents). <br>
<img alt="3" src="https://github.com/R2S-ver/Study-Electronics-Fundamentals/blob/main/assets/images/3.png" width="512" height="512" /> <br>
    </details>
    <details id="3-potential-risks-in-household-power-usage"><summary>
### 🟦3. Potential Risks in Household Power Usage
</summary>

<img alt="5" src="https://github.com/R2S-ver/Study-Electronics-Fundamentals/blob/main/assets/images/5.png" width="512" height="512" /> <br>
Hard VS Stranded wire(Different application scenario's)  <br>
<img alt="6" src="https://github.com/R2S-ver/Study-Electronics-Fundamentals/blob/main/assets/images/6.png" width="512" height="512" /> <br>
#### 🟩3.1. Cable Sizing (Cross sectional area in mm^2)
The diameter (cross-section) of a cable determines the maximum current it can safely carry. Thicker cables = lower resistance = higher current capacity.<br>
*Key factors influencing cable choice:*<br>
3.1.1.  **Material:** Copper, Aluminum, or CCA (Copper Clad Aluminum).<br>
3.1.2.  **Core type:** Solid vs. stranded wire (influences skin effect and contact surface).<br>
3.1.3.  **Length:** Longer cables have higher resistance and voltage drop.<br>
3.1.4.  **Ambient Temperature:** Heat is harder to dissipate in high temperatures.<br>
3.1.5.  **Cable Density:** Number of cables packed together in a conduit (heat buildup).<br>
3.1.6.  **Short-circuit Current:** Ability to withstand heat during a short circuit.<br>
<img alt="7" src="https://github.com/R2S-ver/Study-Electronics-Fundamentals/blob/main/assets/images/7.png" width="512" height="512" /> <br>
#### 🟩3.2. Cord Defects
A damaged cable can lead to short circuits, electric shocks, or fire.
* Damage to the outer jacket.
* Color changes due to overheating.
* Excessive bending or pinching.
* Aging/brittle insulation material.

#### 🟩3.3. Operating Environment
Extra caution is required in damp or wet environments.
* Is the device properly grounded?
* Does the IP rating meet the standard for the area?
* Is an RCD present?
* Location of the appliance and potential corrosion of contact points.

#### 🟩3.4. Overload, Overvoltage and Short Circuits
* **Simultaneous Use:** Running multiple high-wattage devices on one group (max. 10A/16A).
* **Long-term Heavy Load:** Leads to overheating of cables.
* **Daisy-Chaining:** Plugging power strips into other power strips (major overload risk).
* **Poor Contacts:** High contact resistance causes heat.
* **Limited Heat Dissipation:** Especially dangerous when using coiled cable reels (always unroll them completely to prevent overheating).
* **Lack of Surge Protection:** Vulnerability to voltage spikes (Overspanningsbeveiliging).
    </details>
    <details id="practical-research"><summary>
### 🟦4. Practical research
</summary>

<img alt="8" src="https://github.com/R2S-ver/Study-Electronics-Fundamentals/blob/main/assets/images/8.png" width="1024" height="1024" /> <br>
During this research, I'm doing a research into the electrical infrastructure of my workplace, focusing on safety and operational reliability. 
Based on this analysis, I made a detailed topology schema of the workspace.
The core objective of this project is to understand electrical topology mapping and perform risk assessments. To ensure clarity—especially since many specialized tools lack standardized electrical symbols; I use icons to improve recognizability.
#### 🟩Potential risks and Optimization Plan
<img alt="9" src="https://github.com/R2S-ver/Study-Electronics-Fundamentals/blob/main/assets/images/9.png" width="768" height="768" /> <br>
**4.1. Welding Machine Grounding** The welding machine is currently ungrounded. This poses a significant safety risk and must be connected directly to the main grounding system of the distribution board (meterkast).<br>
**4.2. Inrush Current (Current Peaks)** The inrush current of the welding machine is too high (20-30A) for the current circuit. The device needs to be moved to a different group/circuit equipped with a heavier-duty circuit breaker and adequate overload protection.<br>
**4.3. Trip Characteristics** For the welding equipment, a circuit breaker with a C or D-curve characteristic should be used. These are specifically designed to handle high starting currents and peak loads without tripping prematurely.<br>
<img alt="10" src="https://github.com/R2S-ver/Study-Electronics-Fundamentals/blob/main/assets/images/10.png" width="768" height="768" /> <br>
**4.4. Eliminating Daisy-Chaining** Connecting power strips in series (daisy-chaining) increases contact resistance, leading to heat buildup and fire hazards. The setup must be converted from a "tree structure" to a star topology. Furthermore, a high-quality 16A power strip with an extra-long lead should be used instead of multiple interconnected strips.<br>
**4.5. Voltage Dips & EMI** Heavy consumers, such as the compressor and angle grinder, cause voltage dips and Electromagnetic Interference (EMI). This disrupts sensitive electronics like PCs and monitors. The solution is to place heavy machinery on a separate circuit or physically disconnect sensitive electronics during heavy work.<br>
<img alt="11" src="https://github.com/R2S-ver/Study-Electronics-Fundamentals/blob/main/assets/images/11.png" width="768" height="768" /> <br>
**4.6. Travel Adapters** The contact surfaces of travel adapters are often too small for high-current applications. To improve safety, current plugs should be replaced with standard European plugs or industrial-grade power strips with high load capacities.<br>
**4.7. Zoning & Circuit Distribution** The workshop will be divided into a "Machining Zone" and an "Office Zone," each connected to separate circuits (e.g., 16A per group). Where possible, wiring should be upgraded from 2.5mm² to 4mm² or 6mm². Additionally, an RCD (Residual Current Device) should be installed, and consumer-grade power strips replaced with professional PDUs (Power Distribution Units). <br>
<img alt="12" src="https://github.com/R2S-ver/Study-Electronics-Fundamentals/blob/main/assets/images/12.png" width="768" height="768" /> <br>
**4.8. Direct Connection** Secondary power strips should be eliminated. Critical equipment, such as PCs and monitors, must be plugged directly into wall sockets. Heavy tools like the compressor should be grouped onto their own dedicated circuit. <br>
**4.9. Prevention & Warning Labels** Safety signage will be applied to the workspace. This includes prohibitions on simultaneously starting multiple heavy machines (to prevent overload) and a ban on using coiled extension cords (to prevent induction-based heat buildup). <br>
<img alt="13" src="https://github.com/R2S-ver/Study-Electronics-Fundamentals/blob/main/assets/images/13.png" width="768" height="768" /> <br>
<img alt="14" src="https://github.com/R2S-ver/Study-Electronics-Fundamentals/blob/main/assets/images/14.png" width="512" height="512" /> <br>
#### 🟩Conclusion
The result of this research is the identification of nine critical risk factors, ranging from missing grounds on heavy machinery to fire hazards caused by 'daisy-chaining'.
This analysis has led to a concrete optimization plan to transform the workshop into a safe, professional environment. The research proves that the current installation is not equipped for the simultaneous use of industrial tools and sensitive electronics. Moving from a serial 'tree structure' to a parallel 'star topology' and separating circuits are essential steps to guarantee fire safety and operational stability.
#### 🟩Reflection
Analyzing the installation and formulating concrete improvements has significantly increased my awareness of electrical safety. I have become much more alert to how equipment is used in my daily environment. This research has not only provided me with technical skills but also fostered a critical, observant attitude toward potential risks within the physical infrastructure of my work place. <br>
<img alt="16" src="https://github.com/R2S-ver/Study-Electronics-Fundamentals/blob/main/assets/images/16.png" width="768" height="768" /> <br>
↑New Work Zone <br>
#### 🟩Optimization
To mitigate the risks identified in my research, I have implemented a physical separation of equipment to minimize interference and balance the electrical load: <br>
* **Office Zone:** All sensitive electronic devices, including my PC and monitors, are now consolidated in a dedicated office area(bedroom). This zone is isolated from heavy-duty machinery to prevent hardware damage caused by Electromagnetic Interference (EMI) and voltage dips. <br>
* **Work Zone:** Industrial equipment and processing powertools have been moved to a separate room. By isolating the heavy power loads (such as the welding machine and air compressor) from the delicate electronics; significantly reducing the risk of circuit overloads and improved the overall stability of the infrastructure. <br>
#### [>Back to the Table of Contents<](#electrical-safety)
</details>
<details id="refs-electrical"><summary>
  
### 🟦5. Refs Electrical
</summary>

1. [How does the connection of a meter box to the main fuse work?](https://saelektroexperts.nl/en/meterkast-problemen/hoe-werkt-de-aansluiting-van-een-meterkast-op-de-hoofdzekering/)
2. https://www.drixes-elektricien.nl/groepenkast/overzicht
3. https://texasgateway.org/resource/68-electrical-safety-systems-and-devices
4. https://www.mall99.co.ke/types-of-electrical-wires-and-cables/
5. https://viox.com/cable-size-types-mm-awg-bs-conversion-guide/
6. https://electronics.stackexchange.com/questions/688210/what-is-the-purpose-of-neutral-disconnect-in-a-circuit-breaker
7. https://www.se.com/nl/nl/faqs/FA277439/
8. https://mens-en-gezondheid.infonu.nl/leven/166505-veilig-elektriciteitsgebruik-en-eerste-hulp-bij-elektrocutie.html
9. https://www.elektramat.nl/kennisbank/aderdikte/
10. https://builder-calc.com/nl/elektronica/kabeldoorsnedecalculator-op-basis-van-vermogen-en-stroom-online-berekening.html
11. https://mens-en-gezondheid.infonu.nl/leven/166505-veilig-elektriciteitsgebruik-en-eerste-hulp-bij-elektrocutie.html
12. https://www.livios.be/nl/artikel/63803/elektriciteit-in-de-badkamer-wat-kan-en-wat-niet/
13. https://www.vanlieshoutelektra.nl/nieuws/zo-voorkomt-u-overbelasting-op-tijdelijke-installaties/
    </details>
</details> 

#### [>Back to the Table of Contents<](#electrical-safety)
----------------------------


<details id="voltage-and-current" open><summary>  

## 🟪Voltage and Current
</summary>

<details id="1-simple-explaination"><summary> 
                 
### 🟦1. Simple Explaination
</summary>

To build an intuitive understanding, let's use a water pipe analogy:
* **Voltage (V):** Equivalent to **water pressure**. It is the potential energy difference that pushes electric charges through a circuit.
* **Current (I):** Equivalent to **water flow rate (velocity)**. It is the actual movement of electric charges inside the conductor.
* **Resistance (R):** Equivalent to **pipe thickness**. A narrower pipe provides greater resistance to the flow of water.

> **Ohm's Law:** $V = I \times R$
</details>

<details id="2-complex-explaination"><summary>

### 🟦2. Complex Explaination
</summary>

When we flip a switch, the light bulb turns on instantly. Do electrons rush from the battery to the bulb at the speed of light? **Not at all.**

#### 🟩2.1. "Snail-paced" Electrons vs. "Light-speed" Energy Propagation
Inside metallic conductors (like copper wires), it is packed with free electrons, forming what is known as an **"electron sea"**.
* **Drift Velocity:** When a circuit is powered, electrons move forward under the drive of electric field forces. However, because they constantly collide with the crystalline lattice of copper atoms, their net movement speed is incredibly slow—typically only **a few micrometers to millimeters per second** (slower than a snail).
* **Establishment of the Electromagnetic Field:** If electrons move so slowly, why does the light bulb turn on instantly? Because what truly transmits energy is not the electrons themselves, but the **electromagnetic field**. The moment the switch is closed, an electric field is established around the wire at **nearly the speed of light** (approx. $3 \times 10^8 \text{ m/s}$).
* **The Physical Reality:** Free electrons already exist throughout the entire wire. Once the electric field is established, all electrons along the line receive the command of the electric field force ($F = qE$) at almost the same instant and start moving together. This is like a long queue of tightly packed people—if the person at the back gets pushed, the person at the very front moves instantly, without needing to wait for the last person to physically run to the front.

#### 🟩2.2. The Essence of Voltage: Space Accumulation of Electric Field Force
In physics, the essence of voltage is the **electrical potential difference**.
The role of a battery or power source is to forcefully separate positive and negative charges using chemical or magnetic energy, thereby creating an **electric field** in space. As a battery discharges, its voltage drops from high to low, and charging reverses this process. Therefore, measuring a battery's voltage can help determine its state (though this does not apply perfectly to all battery types). When an electron moves through an electric field, the field force does work on it. Voltage is defined as the work done by the electric field force per unit charge as it moves between two points:

$$V = \int_{A}^{B} \vec{E} \cdot d\vec{l}$$

Thus, voltage is not some invisible gas pressure, but rather the **spatial accumulation of an "invisible push" exerted by the electric field on electric charges**.
</details>

<details id="3-kirchhoffs-laws"><summary>
    
### 🟦3. Kirchhoff’s Laws
</summary>

These two laws are not just tools for circuit analysis; they are specific manifestations of the universe's fundamental physical laws—**conservation of charge** and **conservation of energy**—within an electrical circuit.

#### 🟩3.1. Kirchhoff’s Current Law (KCL) — Why Electrons Cannot Pile Up Out of Nowhere
* **Macroscopic Formula:** $\sum I_{in} = \sum I_{out}$
* **Microscopic Physics:** Electrons carry negative charges. According to **Coulomb's Law**, there is an immensely powerful repulsive force between like charges. If more electrons flow into a specific junction (node) than flow out, negative charge would rapidly accumulate at that node.
* **Self-Regulating Mechanism:** The moment negative charge begins to accumulate at a node, the powerful repulsive force it generates instantly "pushes away" incoming electrons behind it while "speeding up" the outgoing electrons ahead. This microscopic self-balancing process finishes within a few nanoseconds. Consequently, under steady-state conditions, **no node can hold excess net charge**; whatever current goes in must come out.

#### 🟩3.2. Kirchhoff’s Voltage Law (KVL) — Why a Full Loop Must Equal Zero
* **Macroscopic Formula:** $\sum V = 0$
* **Microscopic Physics:** In electrostatics or low-frequency circuits, the electric field is a **conservative field (an electrostatic field is irrotational)**. This means the work done by the electric field force depends only on the starting and ending positions, completely independent of the path taken. If you take a charge from a point, move it around a complete loop in the circuit (experiencing voltage boosts from sources and drops from resistors), and return to the starting point, the net work done by the electric field force must be exactly zero:

$$\oint \vec{E} \cdot d\vec{l} = 0$$

* **Energy Conservation Analogy:** A power source acts like a "charge elevator," consuming chemical energy to lift electrons from a lower potential to a higher potential (gaining electrical potential energy). As electrons flow through a resistor, the potential energy gained in the elevator is entirely converted into **thermal energy** or **light energy** through collisions with the atomic lattice. By the time the electron returns to the negative terminal of the battery, its energy is precisely depleted. Energy cannot be created out of nothing, nor can it vanish; this is the ultimate truth behind KVL.
  </details>
</details> 

#### [>Back to the Table of Contents<](#voltage-and-current)
----------------------------



<details id="basic-electrical-components" open><summary>

## 🟪Basic electrical components
</summary>
      <details id="Resistor"><summary>
        
### 🟦Resistor
</summary>

<img alt="19" src="https://github.com/R2S-ver/Study-Electronics-Fundamentals/blob/main/assets/images/19.png" width="1024" height="1024" /> <br>

#### What is a resistor?
A resistor is a passive electronic component designed to create resistance in the flow of electric current. In a circuit, it acts like a "bump" for electrons. Its primary jobs are to limit the amount of current going through(to keep components like LEDs from burning out) and to divide voltage (as seen in your comparator circuit).


<img alt="18" src="https://github.com/R2S-ver/Study-Electronics-Fundamentals/blob/main/assets/images/18.jpg" width="768" height="768" /> <br>

While there are many types, the most common one you’ll encounter in hobbyist electronics (like those used in Tinkercad) is the Carbon Film Resistor. <br>
**1. The Ceramic Core** <br>
  At the center is a solid rod made of high-grade ceramic (an insulator). This acts as the structural base and does not conduct electricity. <br>
**2. The Carbon Film Layer** <br>
  A thin layer of pure carbon is deposited around the ceramic rod. This film is the resistive material that electrons must travel through. <br>
**3. The Helical Groove** <br>
    Shorter, wider spiral path = Lower resistance <br>
    Longer, thinner spiral path = Higher resistance <br>
This effectively turns the film into a long, coiled "wire" of carbon. <br>
**4. End Caps and Leads** <br>
Metal end caps are pressed onto both sides of the rod. Tinned copper "leads" (the legs you plug into a breadboard) are welded to these caps to connect the resistor to the rest of the circuit. <br>
<img alt="21" src="https://github.com/R2S-ver/Study-Electronics-Fundamentals/blob/main/assets/images/21.png" width="346" height="537" /> <br>
**5. Protective Coating & Color Bands** <br>
Finally, the entire body is coated in an insulating lacquer or epoxy to protect it from moisture and heat. The colored stripes are painted on to indicate the resistance value and tolerance. <br>
<img alt="17" src="https://github.com/R2S-ver/Study-Electronics-Fundamentals/blob/main/assets/images/17.png" width="768" height="768" /> <br>
↑ Limit the ampere VS led broke by too much ampere going through
#### Theory: Voltage Division Principle
In a series circuit with multiple resistors, the voltage drop is proportional to the resistance. If the resistance increases, the voltage across it increases as well (R↑ = V↑).
**Calculating the Series Resistor (Voltage Drop)**
Scenario: An LED operates at 3V and draws 13.5mA (0.0135A) of current with a 5V power source
V_drop = V_source - V_LED = 2V
R = V_drop / I
R = 2V / 0.0135A = 148.15 ohms (**150 ohm resistor**)

##### LED as Resistance?
An LED(Light-emitting diode) cannot be treated as a fixed ohmic resistor because it is a non-linear component. While a standard resistor follows Ohm's law (where current is directly proportional to voltage), an LED is a diode with a non-linear current-voltage curve.

#### Pracical electrical schematic case - Voltage Comparator
<img alt="23" src="https://github.com/R2S-ver/Study-Electronics-Fundamentals/blob/main/assets/images/23.png" width="1024" height="1024" /> <br>
<img alt="22" src="https://github.com/R2S-ver/Study-Electronics-Fundamentals/blob/main/assets/images/22.png" width="1024" height="1024" /> <br>

#### Conclusion
<img alt="20" src="https://github.com/R2S-ver/Study-Electronics-Fundamentals/blob/main/assets/images/20.png" width="1024" height="1024" /> <br>

</details>
<details id="Capacitor"><summary>
  
### 🟦Capacitor
</summary>

<img alt="27" src="https://github.com/R2S-ver/Study-Electronics-Fundamentals/blob/main/assets/images/27.png" width="1024" height="1024" /> <br>
<img alt="28" src="https://github.com/R2S-ver/Study-Electronics-Fundamentals/blob/main/assets/images/28.png" width="1024" height="1024" /> <br>

</details>
     <details id="Conductor"><summary>
      
### 🟦Conductor
</summary>

<img alt="29" src="https://github.com/R2S-ver/Study-Electronics-Fundamentals/blob/main/assets/images/29.png" width="1024" height="1024" /> <br>

  #### Pracical electrical schematic case - Rectifier Bridge
  <img alt="24" src="https://github.com/R2S-ver/Study-Electronics-Fundamentals/blob/main/assets/images/24.png" width="1024" height="1024" /> <br>
  <img alt="25" src="https://github.com/R2S-ver/Study-Electronics-Fundamentals/blob/main/assets/images/25.png" width="1024" height="1024" /> <br>
  
</details>
     <details id="Diode"><summary>
        
### 🟦Diode
</summary>

<img alt="30" src="https://github.com/R2S-ver/Study-Electronics-Fundamentals/blob/main/assets/images/30.png" width="1024" height="1024" /> <br>

  #### Pracical electrical schematic case - Rectifier Bridge
  
<img alt="26" src="https://github.com/R2S-ver/Study-Electronics-Fundamentals/blob/main/assets/images/26.png" width="1024" height="1024" /> <br>

</details>
     <details id="Transistor"><summary>
        
### 🟦Transistor
</summary>
        uPCOMING
</details>
     <details id="Mosfet"><summary>
        
### 🟦Mosfet
</summary>
        UPCOMING
</details>
     <details id="Linear-and-Switching-Power-Supply"><summary>
        
### 🟦Linear and Switching Power Supply
</summary>

<img alt="31" src="https://github.com/R2S-ver/Study-Electronics-Fundamentals/blob/main/assets/images/31.png" width="1024" height="1024" /> <br>

#### Pracical electrical schematic case - 230V - 12V Switching Power Supply 
<img alt="32" src="https://github.com/R2S-ver/Study-Electronics-Fundamentals/blob/main/assets/images/32.png" width="1024" height="1024" /> <br>
<img alt="33" src="https://github.com/R2S-ver/Study-Electronics-Fundamentals/blob/main/assets/images/33.png" width="1024" height="1024" /> <br>
<img alt="34" src="https://github.com/R2S-ver/Study-Electronics-Fundamentals/blob/main/assets/images/34.png" width="1024" height="1024" /> <br>

</details>
    <details id="practical-skills"><summary>
      
### 🟦Practical skills
</summary>
<img alt="35" src="https://github.com/R2S-ver/Study-Electronics-Fundamentals/blob/main/assets/images/35.png" width="1024" height="1024" /> <br>
</details>
     <details id="refs-components"><summary>

### 🟦Refs Components
</summary>

1. [Led weerstand calculator](https://www.budgetronics.eu/nl/led-weerstand-calculator/c-7)
2. [Resistor Heat Calculator](https://a2zcalculators.com/science-and-engineering-calculators/resistor-heat-calculator)
3. [Pull-up and Pull-down Resistors](https://www.circuitbasics.com/pull-up-and-pull-down-resistors/)
4. [Voltage comparator LM393 data sheet | TI.com](https://www.ti.com/product/LM393#features)
5. [How to Build a Voltage Comparator Circuit Using an LM393](https://www.learningaboutelectronics.com/Articles/LM393-voltage-comparator-circuit.php)
6. [LC filter calculator](https://www.omnicalculator.com/physics/lc-filter)
7. [Voltage and Current Explained](https://www.ariat-tech.com/blog/comprehensive-overview-of-voltage-and-current.html)
8. [25 Types of Capacitors & their Uses (Explained in detail)](https://www.etechnophiles.com/types-of-capacitors/)
9. [Linear Regulated Power Supply Block Diagram & Circuit Diagram](https://www.hackatronic.com/linear-regulated-power-supply-block-diagram-circuit-diagram/)
10. [How to Build a Linear Power Supply](https://www.circuitbasics.com/linear-power-supplies/)
11. [Power Supply Basics – Part 1: Unregulated Linear and Regulated Linear](https://mcitransformer.com/power-supply-basics-part-1-unregulated-linear-regulated-linear/)
12. [The role of power management in today’s electronic devices](https://uk.farnell.com/the-role-of-power-management-in-electronic-devices)
13. [Linear regulator](https://en.wikipedia.org/wiki/Linear_regulator)
14. [Isolated vs Non-Isolated Power Supplies: The Right Choice Without Fail](https://resources.altium.com/p/isolated-vs-non-isolated-power-supplies-right-choice-without-fail)
15. [Gallium Nitride Power Devices in Power Electronics Applications: State of Art and Perspectives](https://www.mdpi.com/1996-1073/16/9/3894)
16. [Using a high-frequency switching regulator without a linear regulator to power a data-converter system](https://www.ti.com/lit/an/slyt756/slyt756.pdf?ts=1774571562348)
17. [How mobile phone charger works ? | SMPS Switch mode power supply](https://www.youtube.com/watch?v=F2dCS5qOE8A)
18. [Modular AC line EMI filters explained](https://passive-components.eu/modular-ac-line-emi-filters-explained/)
19. [Bridge Rectifier With Capacitor Filter: Circuit Diagram and Explain Step by Step](https://www.voltagelab.com/bridge-rectifier-with-capacitor-filter/)
20. [Understanding of Carbon Film Resistors](https://www.utmel.com/blog/categories/resistor/understanding-of-carbon-film-resistors)
21. [Resistor Color Codes: What Do the Color Bands Mean?](https://www.te.com/en/products/passive-components/resistors/intersection/resistor-color-codes.html)
  </details>
  
  #### [>Back to the Table of Contents<](#basic-electrical-components)
</details>
