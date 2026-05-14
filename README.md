<div align="center">

<img alt="LOGO" src="https://github.com/R2S-ver/Study-Electronics-Fundamentals/blob/main/assets/images/Banner 2.png" width="256" height="256" />
  
# Personal studylogbook of electronic fundamentals
[English](https://github.com/R2S-ver/Study-Electronics-Fundamentals/blob/main/README.md) | [中文](https://github.com/R2S-ver/Study-Electronics-Fundamentals/blob/Chinese/README.md)

Welcome to my learning repository! 
This project documents my self-study journey in the world of electricity and hardware. I am starting from the very basics of electrical safety and slowly diving into component-level circuit design. 
Currently, this repository focuses on **hardware fundamentals** and **analog electronics**, without involving microcontrollers (like Arduino) or digital logic programming yet.

To better internalize these concepts and understand their practical applications, I have included real-world examples and case studies for each component. This "theory + application" approach helps me review more effectively and bridges the gap between textbook knowledge and actual engineering practice.

*The images used in this repository are for educational and self-study purposes only. If you are the copyright owner of any image used here and would like it removed, please contact me.*

> **⚠️ Note on Regional Standards:** The electrical safety analysis and examples documented here are based on my local usage scenario in **The Netherlands (Europe)**. Voltage standards, electrical panel structures, protective mechanisms and safety regulations (like NEN 1010) vary significantly by country. Be aware of your local regulations when working with electricity.

</div>

# **Table of Contents**
- [Electrical safety at home](#electrical-safety) <br>
  1\. [Introduction & Project Scope](#1-introduction--project-scope) <br>
  2\. [Protective Mechanisms in the Household Electrical System](#2-protective-mechanisms-in-the-household-electrical-system) <br>
  3\. [Potential Risks in Household Power Usage](#3-potential-risks-in-household-power-usage) <br>
  4\. [Practical Research](#practical-research) <br>
  5\. [References](#refs-electrical) <br>
- [Voltage and current](#voltage-and-current) <br>
  1\. [Macroscopic Explanation](#1-macroscopic-explanation) <br>
  2\. [Microscopic Essence](#2-microscopic-essence) <br>
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
#### 🟩Circuit Breakers: 1P vs. 2
