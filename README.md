<div align="center">
  
<img alt="LOGO" src="https://github.com/R2S-ver/Study-Electronics-Fundamentals/blob/main/assets/images/Banner.png" width="256" height="256" />
  
# Personal studylogbook of electronic fundamentals
[English](https://github.com/R2S-ver/Study-Electronics-Fundamentals/blob/main/README.md) | [中文](https://github.com/R2S-ver/Study-Electronics-Fundamentals/blob/Chinese/README.md)


Welcome to my learning repository! 
This project documents my self-study journey in the world of electricity and hardware. I am starting from the very basics of electrical safety and slowly diving into component-level circuit design. 
Currently, this repository focuses on **hardware fundamentals** and **analog electronics**, without involving microcontrollers (like Arduino) or digital logic programming yet.

To better internalize these concepts and understand their practical applications, I have included real-world examples and case studies for each component. This "theory + application" approach helps me review more effectively and bridges the gap between textbook knowledge and actual engineering practice.

*The images used in this repository are for educational and self-study purposes only. If you are the copyright owner of any image used here and would like it removed, please contact me.*
</div>

# **Table of Contents**
- [Electrical safety](#electrical-safety)
- [Voltage and current](#voltage-and-current)
- [Basic electrical components](#basic-electrical-components)
----------------------------

<!-- 开始折叠内容 -->
## Electrical safety
<details> 
<summary> Click here to expand </summary> 

> **⚠️ Note on Regional Standards:** The electrical safety analysis and examples documented here are based on my local usage scenario in **The Netherlands (Europe)**. Voltage standards, electrical panel structures, protective mechanisms and safety regulations (like NEN 1010) vary significantly by country. Please be aware of your local regulations when working with electricity.

### 1. Introduction & Project Scope
<img alt="LOGO" src="https://github.com/R2S-ver/Study-Electronics-Fundamentals/blob/main/assets/images/Banner.png" width="256" height="256" /> <br>
This section focuses on electrical safety at home, specifically in my personal workspace (my room) and the equipment used within it. 
**Goals of this study:**
- Systematically map the power distribution structure and usage patterns.
- Identify potential safety risks.
- Identify the main energy-consuming devices.
- Design safe, reliable, and feasible solutions for energy savings.

### 2. Protective Mechanisms in the Household Electrical System
In Dutch homes, the distribution board (groepenkast) is located in the meter cupboard. The structure must comply with the **NEN 1010** safety regulations. 
The power enters through the grid connection and passes through the following main safety components:

* **Main Fuse & Main Switch (Hoofdschakelaar):** For total system shutdown.
* **Residual Current Device (Aardlekschakelaar - 30mA):** Protects against electrocution by detecting leakage currents.
* **Circuit Breakers (Installatieautomaten - typically 16A per group):** Distributes the installation into groups. Heavy consumers (like induction cooktops) get a separate 1-phase or 3-phase group with higher capacity and dedicated protection.
* **Grounding (Aarding):** Provides a safe path for fault currents.

#### Circuit Breakers: 1P vs. 2P (Isolation)
* **1P Breaker:** Interrupts the circuit, but the appliance remains connected to the grid via the neutral wire (N).
* **2P / 1P+N Breaker:** Interrupts **both** conductors (Phase and Neutral). 
* **Why is full isolation important?** With a 1P breaker, the neutral remains connected. In the event of a fault or incorrect wiring, the appliance could still carry voltage. A 2P breaker ensures complete electrical isolation and a safer shutdown.

#### Trip Characteristics (Uitschakelkarakteristieken)
Circuit breakers protect against overload and short circuits by automatically switching off. The trip characteristic determines how fast the breaker reacts to a current spike (e.g., when turning on a device).
* Common types: **B, C, D, K, Z, and MA**.
* The difference lies in the current value at which the breaker trips magnetically, expressed as a multiple of the nominal current (In). (e.g., C-curves are better for devices with higher inrush currents).

### 3. Potential Risks in Household Power Usage

#### A. Cable Sizing (Cross sectional area in mm^2)
The diameter (cross-section) of a cable determines the maximum current it can safely carry. Thicker cables = lower resistance = higher current capacity.
*Key factors influencing cable choice:*
1.  **Material:** Copper, Aluminum, or CCA (Copper Clad Aluminum).
2.  **Core type:** Solid vs. stranded wire (influences skin effect and contact surface).
3.  **Length:** Longer cables have higher resistance and voltage drop.
4.  **Ambient Temperature:** Heat is harder to dissipate in high temperatures.
5.  **Cable Density:** Number of cables packed together in a conduit (heat buildup).
6.  **Short-circuit Current:** Ability to withstand heat during a short circuit.

#### B. Cord Defects (Snoer defecten)
A damaged cable can lead to short circuits, electric shocks, or fire.
* Damage to the outer jacket.
* Color changes due to overheating.
* Excessive bending or pinching.
* Aging/brittle insulation material.

#### C. Operating Environment (Gebruiksomgeving)
Extra caution is required in damp or wet environments.
* Is the device properly grounded?
* Does the IP rating meet the standard for the area?
* Is an RCD present?
* Location of the appliance and potential corrosion of contact points.

#### D. Overload, Overvoltage, and Short Circuits
* **Simultaneous Use:** Running multiple high-wattage devices on one group (max. 10A/16A).
* **Long-term Heavy Load:** Leads to overheating of cables.
* **Daisy-Chaining:** Plugging power strips into other power strips (major overload risk).
* **Poor Contacts:** High contact resistance causes heat.
* **Limited Heat Dissipation:** Especially dangerous when using coiled cable reels (always unroll them completely to prevent overheating).
* **Lack of Surge Protection:** Vulnerability to voltage spikes (Overspanningsbeveiliging).

### References
1. https://saelektroexperts.nl/meterkast-problemen/hoe-werkt-de-aansluiting-van-een-meterkast-op-de-hoofdzekering/
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
</details> <!-- 结束折叠内容 -->


----------------------------
## Voltage and current

## Basic electrical components
sss
stest

## References
1
2
3
