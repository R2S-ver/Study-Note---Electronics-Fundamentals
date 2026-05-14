<div align="center">

<img alt="LOGO" src="https://github.com/R2S-ver/Study-Electronics-Fundamentals/blob/main/assets/images/Banner 2.png" width="256" height="256"/>  <br>
  
# 电子基础知识个人学习日志  <br>

🌐其他语言: [English](https://github.com/R2S-ver/Study-Electronics-Fundamentals/blob/main/README.md) | [中文](https://github.com/R2S-ver/Study-Electronics-Fundamentals/blob/Chinese/README.md)

> **注：** 本记录中提供的配图均为英文，因为原版是用荷兰文编写的用于学校的教学，然后又写了英文的版本方便理解，在此保留英文版原图暂未做汉化处理。如果你有哪张图不懂可以QQ联系我，我讲解给你听。

欢迎来到我的学习仓库！这里记录了我自学电气基础和硬件知识的整个过程。我的学习路线是从最基础的电气安全和物理特性开始，逐步深入到元件级别的电路原理。 目前，本仓库的内容专注于纯硬件基础和模拟电子技术，暂未涉及单片机（如 Arduino）或数字逻辑编程。 我希望通过记录这些底层逻辑，打下扎实的硬件基础。 为了更好地内化这些概念并理解其实际应用，我在每个元器件中都加入了实际案例分析。 这种“理论 + 实践”相结合的方式不仅能帮助我更高效地复习，还能缩小课本知识与实际工程应用之间的差距。

*本记录中使用的图片仅供教育和自学用途。如果您是此处使用的任何图片的版权所有者，并希望将其删除，请与我联系。*

> **⚠️ 关于地区标准与 AI 优化的注意事项：** 此处记录的电气安全分析和示例基于我在**荷兰（欧洲）**的本地使用场景。电压标准、配电盘结构、保护机制和安全法规（如 NEN 1010）因国家/地区而异。在进行电气操作时，请务必了解您当地的法规。*此外，为确保专业术语和技术用词的准确性，本记录采用了 AI 辅助进行文本润色与语言优化。*

</div>

# **目录**
- [家庭用电安全](#electrical-safety) <br>
  1\. [简介与项目范围](#1-简介与项目范围) <br>
  2\. [家庭电气系统中的保护机制](#2-家庭电气系统中的保护机制) <br>
  3\. [家庭用电的潜在风险](#3-家庭用电的潜在风险) <br>
  4\. [实践研究](#4-实践研究) <br>
  5\. [参考资料](#5-电气参考资料) <br>
- [电压与电流 (Voltage and current)](#电压与电流) <br>
  1\. [简单宏观解释](#1-宏观解释) <br>
  2\. [进阶微观解释](#2-微观本质) <br>
  3\. [基尔霍夫电流与电压定律 (Kirchhoff’s Current and Voltage Law)](#3-基尔霍夫定律) <br>
- [基础电子元器件 (Basic electrical components)](#基础电子元器件) <br>
  1\. [电阻器 (Resistor)](#1-电阻器) <br>
     &nbsp;&nbsp; 1.1\. 降压 (Voltage Dropping) <br>
     &nbsp;&nbsp; 1.2\. 电压比较器 (Voltage Comparator) <br>
  2\. [电容器 (Capacitor)](#2-电容器) <br>
  3\. [电感器 (Conductor)](#3-电感器) <br>
     &nbsp;&nbsp; 3.1\. 低通与高通滤波器 (Low-pass and High-pass Filter) <br>
  4\. [二极管 (Diode)](#4-二极管) <br>
     &nbsp;&nbsp; 4.1\. 整流桥 (Rectifier Bridge) <br>
  5\. [晶体管 (Transistor)](#5-晶体管) <br>
  6\. [场效应管 (Mosfet)](#6-场效应管) <br>
  7\. [线性与开关电源 (Linear and Switching Power Supply)](#7-线性与开关电源) <br>
     &nbsp;&nbsp; 7.1\. 开关电源分析 (SMPS analysis) <br>
  8\. [实用技能](#8-实用技能) <br>
  9\. [参考资料](#9-元件参考资料) <br>
----------------------------

<!-- 开始折叠内容 -->
<details open><summary>

## 🟪电气安全 (Electrical safety)
</summary>
    <details><summary>

### 🟦1. 简介与项目范围
</summary>
<img alt="1" src="https://github.com/R2S-ver/Study-Electronics-Fundamentals/blob/main/assets/images/1.png" width="512" height="512" /> <br>
本节重点关注家庭用电安全，具体来说是我的个人工作空间（卧室）以及其中使用的设备。<br>

**本研究的目标：**
- 系统地绘制配电结构和使用模式。
- 识别潜在的安全风险。
- 识别主要的耗能设备。
- 设计安全、可靠且可行的节能方案。
    </details>
    <details><summary>

### 🟦2. 家庭电气系统中的保护机制
</summary>

在荷兰的家庭中，配电箱 (groepenkast) 位于电表柜中。其结构必须符合 **NEN 1010** 安全法规。
电力通过电网连接进入，并穿过以下主要的安全组件：

* **主保险丝和主开关 (Main Fuse & Main Switch)：** 用于系统全面断电。
* **漏电保护器 (Residual Current Device, RCD)：** 通过检测漏电流来防止触电。
* **断路器 (Circuit Breakers)：** 将电气安装划分为多个组。大功率耗电设备（如电磁炉）会使用容量更大且有专属保护的独立单相或三相组。
* **接地 (Grounding)：** 为故障电流提供安全路径。

<img alt="2" src="https://github.com/R2S-ver/Study-Electronics-Fundamentals/blob/main/assets/images/2.png" width="512" height="512" /> <br>
#### 🟩断路器：1P vs. 2P (Circuit Breakers: 1P vs. 2P)
* **1P 断路器：** 切断电路，但设备仍通过零线 (N) 连接到电网。
* **2P / 1P+N 断路器：** 同时切断**两根**导线（火线和零线）。 
* **为什么完全隔离很重要？** 使用 1P 断路器时，零线仍保持连接。在发生故障或接线错误的情况下，设备可能仍带有电压。2P 断路器可确保完全的电气隔离，断电更安全。
<img alt="4" src="https://github.com/R2S-ver/Study-Electronics-Fundamentals/blob/main/assets/images/4.png" width="512" height="512" /> <br>
#### 🟩脱扣特性
断路器通过自动断开来防止过载和短路。脱扣特性决定了断路器对电流尖峰（例如，在打开设备时）的反应速度。
* 常见类型：**B、C、D、K、Z 和 MA**。
* 区别在于断路器磁脱扣的电流值不同，通常表示为额定电流 (In) 的倍数。（例如，C 曲线更适合具有较高浪涌电流的设备）。 <br>
<img alt="3" src="https://github.com/R2S-ver/Study-Electronics-Fundamentals/blob/main/assets/images/3.png" width="512" height="512" /> <br>
    </details>
    <details><summary>

### 🟦3. 家庭用电的潜在风险
</summary>

<img alt="5" src="https://github.com/R2S-ver/Study-Electronics-Fundamentals/blob/main/assets/images/5.png" width="512" height="512" /> <br>
单股硬线 VS 多股软线（不同的应用场景）  <br>
<img alt="6" src="https://github.com/R2S-ver/Study-Electronics-Fundamentals/blob/main/assets/images/6.png" width="512" height="512" /> <br>
#### 🟩3.1. 电缆尺寸（横截面积 mm²）
电缆的直径（横截面积）决定了其可以安全承载的最大电流。电缆越粗 = 电阻越低 = 载流量越大。<br>
*影响电缆选择的关键因素：*<br>
3.1.1. **材质：** 铜、铝或 CCA（铜包铝）。<br>
3.1.2. **线芯类型：** 单股硬线与多股软线（影响趋肤效应和接触面积）。<br>
3.1.3. **长度：** 电缆越长，电阻和电压降越大。<br>
3.1.4. **环境温度：** 高温下热量更难散发。<br>
3.1.5. **电缆密度：** 挤在同一个管道中的电缆数量（导致热量积聚）。<br>
3.1.6. **短路电流：** 承受短路时产生的高温的能力。<br>
<img alt="7" src="https://github.com/R2S-ver/Study-Electronics-Fundamentals/blob/main/assets/images/7.png" width="512" height="512" /> <br>
#### 🟩3.2. 线缆缺陷
损坏的电缆可能导致短路、触电或火灾。
* 外护套损坏。
* 因过热导致的颜色改变。
* 过度弯曲或挤压。
* 绝缘材料老化/变脆。

#### 🟩3.3. 运行环境
在潮湿环境中需要格外小心。
* 设备是否正确接地？
* IP 防护等级是否符合该区域的标准？
* 是否安装了漏电保护器 (RCD)？
* 设备的位置及触点的潜在腐蚀风险。

#### 🟩3.4. 过载、过压与短路 (Overload, Overvoltage and Short Circuits)
* **同时使用：** 在同一组（最大 10A/16A）上运行多个大功率设备。
* **长期重载：** 导致电缆过热。
* **菊花链连接（串联排插）：** 将插线板插到另一个插线板上（严重的过载风险）。
* **接触不良：** 接触电阻过高引起发热。
* **散热受限：** 使用卷筒式电缆卷盘时尤其危险（务必将其完全展开以防止过热）。
* **缺乏电涌保护：** 容易受到电压尖峰的损害 (Overspanningsbeveiliging)。
    </details>
    <details><summary>

### 🟦4. 实践研究
</summary>

<img alt="8" src="https://github.com/R2S-ver/Study-Electronics-Fundamentals/blob/main/assets/images/8.png" width="1024" height="1024" /> <br>
在这项研究中，我正在对工作场所的电气基础设施进行调研，重点关注安全性和运行可靠性。
基于这一分析，我绘制了该工作空间的详细拓扑图。
本项目的核心目标是理解电气拓扑结构的绘制并进行风险评估。为了确保清晰度——尤其是由于许多专业工具缺乏标准化的电气符号；我使用图标来提高辨识度。

#### 🟩潜在风险与优化计划
<img alt="9" src="https://github.com/R2S-ver/Study-Electronics-Fundamentals/blob/main/assets/images/9.png" width="768" height="768" /> <br>
**4.1. 电焊机接地 (Welding Machine Grounding)** 目前的电焊机未接地。这构成了重大的安全风险，必须将其直接连接到配电箱 (meterkast) 的主接地系统。<br>
**4.2. 浪涌电流 (Inrush Current)** 电焊机的浪涌电流对当前电路来说太高了（20-30A）。需要将该设备移至配备了更大容量断路器和足够过载保护的其他组/电路上。<br>
**4.3. 脱扣特性 (Trip Characteristics)** 对于焊接设备，应使用具有 C 或 D 曲线特征的断路器。这些断路器专为处理高启动电流和峰值负载而设计，不会发生过早脱扣。<br>
<img alt="10" src="https://github.com/R2S-ver/Study-Electronics-Fundamentals/blob/main/assets/images/10.png" width="768" height="768" /> <br>
**4.4. 消除菊花链连接 (Eliminating Daisy-Chaining)** 将插线板串联（菊花链）会增加接触电阻，导致热量积聚和火灾隐患。该设置必须从“树状结构”转换为星型拓扑。此外，应使用带超长电线的高质量 16A 插线板，而不是多个互连的插线板。<br>
**4.5. 电压暂降与电磁干扰 (Voltage Dips & EMI)** 压缩机和角磨机等大功率设备会导致电压暂降和电磁干扰 (EMI)。这会干扰 PC 和显示器等敏感电子设备。解决方案是将重型机械放置在单独的电路上，或在进行重型工作时物理断开敏感电子设备的连接。<br>
<img alt="11" src="https://github.com/R2S-ver/Study-Electronics-Fundamentals/blob/main/assets/images/11.png" width="768" height="768" /> <br>
**4.6. 旅行转换插头 (Travel Adapters)** 旅行转换插头的接触面积通常太小，不适合大电流应用。为了提高安全性，应将当前的插头更换为标准的欧洲插头或具有高负载能力的工业级插线板。<br>
**4.7. 分区与电路分配 (Zoning & Circuit Distribution)** 车间将分为“加工区”和“办公区”，分别连接到不同的电路（例如，每组 16A）。在可能的情况下，布线应从 2.5mm² 升级到 4mm² 或 6mm²。此外，应安装漏电保护器 (RCD)，并将消费级插线板更换为专业的电源分配单元 (PDU)。 <br>
<img alt="12" src="https://github.com/R2S-ver/Study-Electronics-Fundamentals/blob/main/assets/images/12.png" width="768" height="768" /> <br>
**4.8. 直接连接 (Direct Connection)** 应消除次级插线板。关键设备（如 PC 和显示器）必须直接插在墙壁插座上。像压缩机这样的重型工具应分组到它们专属的独立电路上。 <br>
**4.9. 预防与警告标签 (Prevention & Warning Labels)** 工作空间将贴上安全标志。这包括禁止同时启动多台重型机器（以防止过载）以及禁止使用盘起的延长线（以防止感应积热）。 <br>
<img alt="13" src="https://github.com/R2S-ver/Study-Electronics-Fundamentals/blob/main/assets/images/13.png" width="768" height="768" /> <br>
<img alt="14" src="https://github.com/R2S-ver/Study-Electronics-Fundamentals/blob/main/assets/images/14.png" width="512" height="512" /> <br>
#### 🟩结论 (Conclusion)
本次研究的结果是识别出九个关键的风险因素，从重型机械缺少接地到“菊花链”连接引起的火灾隐患。
这项分析促成了一个具体的优化计划，以将车间转变为一个安全的专业环境。研究证明，当前的安装无法满足同时使用工业工具和敏感电子设备的需求。从串联的“树状结构”转向并联的“星型拓扑”并分离电路是保证消防安全和运行稳定性的必要步骤。
#### 🟩反思 (Reflection)
分析电气安装并制定具体的改进措施，大大提高了我的电气安全意识。我对日常环境中设备的使用方式变得更加警觉。这项研究不仅为我提供了技术技能，还培养了我对工作场所物理基础设施内潜在风险的批判性、观察性态度。 <br>
<img alt="16" src="https://github.com/R2S-ver/Study-Electronics-Fundamentals/blob/main/assets/images/16.png" width="768" height="768" /> <br>
↑新的工作区 <br>
#### 🟩优化 (Optimization)
为了降低研究中识别的风险，我实施了设备的物理隔离，以最大程度地减少干扰并平衡电气负载： <br>
* **办公区：** 所有敏感的电子设备，包括我的 PC 和显示器，现在都整合在一个专门的办公区域（卧室）。该区域与重型机械隔离，以防止电磁干扰 (EMI) 和电压暂降造成的硬件损坏。 <br>
* **工作区：** 工业设备和加工电动工具已移至单独的房间。通过将重型电力负载（如电焊机和空气压缩机）与精密的电子设备隔离开来；大大降低了电路过载的风险，并提高了基础设施的整体稳定性。 <br>
#### [>返回目录<](#Table-of-Contents)
</details>
<details><summary>

### 🟦5. 电气参考资料
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

#### [>返回目录<](#Table-of-Contents)
<!-- 结束折叠内容 -->

----------------------------


<!-- 开始折叠内容 -->
<details id="电压与电流" open> <summary>  

## 🟪电压与电流
</summary>

<details id="1-宏观解释"><summary> 
                 
### 🟦1. 宏观解释
</summary>

为了建立直观印象，这里使用水管来类比：
* **电压 (V)：** 相当于**水压**。它是推动电荷流过电路的势能差。
* **电流 (I)：** 相当于**水流速度（流量）**。它是电荷在导体中的实际移动。
* **电阻 (R)：** 相当于**水管的粗细**。水管越细，对水流的阻力就越大。

> **欧姆定律 (Ohm's Law):** $V = I \times R$
</details>

<details id="2-微观本质"><summary>

### 🟦2. 微观本质
</summary>

当我们按下开关时，灯泡瞬间就亮了。难道是电子以光速从电池冲到了灯泡吗？**并不是。**

#### 🟩2.1. 电子的“龟速”移动与能量的“光速”传播
在金属导体（如铜线）内部，充满了自由电子，它们就像一片**“电子海”**。
* **漂移速度 (Drift Velocity)：** 当电路通电时，电子在电场力驱动下向前移动。但由于它们会不断与铜原子的晶格发生碰撞，其净移动速度极其缓慢——通常只有**每秒几微米到几毫米**（比蜗牛还慢）。
* **电磁场的建立：** 既然电子动得这么慢，为什么灯泡能瞬间点亮？因为真正传递能量的不是电子本身，而是**电磁场**。闭合开关的瞬间，电场以**接近光速**（约 $3 \times 10^8 \text{ m/s}$）在导线周围建立起来。
* **物理真相：** 导线里的自由电子早就存在了。电场建立后，全线所有的电子几乎在同一瞬间接收到了电场力（$F = qE$）的指令，同时开始迈步。这就像一根排满人的长队，后面的人推一下，前面的人瞬间就会动，而不需要等最后一个人跑过来。
这里解释的比较模糊，推荐看B站相关的视频，动画演示通俗易懂

#### 🟩2.2. 电压的本质：电场力的空间累积
物理学中，电压的本质是**电势差**。
电池或者电源的作用，是通过化学能或磁能，将正负电荷强行分开，在空间中制造出一个**电场**。电池随着放点会从高电压跌到低电压，充电则是反过来。因此可以通过测量电池电压判断他的状态（部分类型电池不适用这个说法）当电子在电场中移动时，电场力会对它做功。电压就是单位电荷在两点之间移动时，电场力所做的功：

$$V = \int_{A}^{B} \vec{E} \cdot d\vec{l}$$

所以，电压并不是什么无形的气体压力，而是**电场对电荷的一种“无形推力”的空间累积**。
</details>

<details id="3-基尔霍夫定律"><summary>
    
### 🟦3. 基尔霍夫定律
</summary>

这两条定律不仅是电路分析的工具，更是宇宙基本物理定律——**电荷守恒**和**能量守恒**在电路中的具体体现。

#### 🟩3.1. 基尔霍夫电流定律 (KCL) —— 为什么电子不能凭空堆积？
* **宏观公式：** $\sum I_{in} = \sum I_{out}$
* **微观物理：** 电子带有负电荷。根据**库仑定律**，同性电荷之间存在极其恐怖的排斥力。如果在电路的某一个节点（Junction）上，流入的电子比流出的多，这个节点就会迅速积累负电荷。
* **自我调节机制：** 一旦节点积累了负电荷，它产生的强大排斥力就会立刻“推开”后面试图流入的电子，并“加速”前面流出的电子。这个微观的自平衡过程在几纳秒内就能完成。因此，在稳定状态下，**任何节点都无法容纳多余的净电荷**，进去多少电流，就必须出来多少电流。

#### 🟩3.2. 基尔霍夫电压定律 (KVL) —— 为什么绕一圈一定是零？
* **宏观公式：** $\sum V = 0$
* **微观物理：** 在静电学或低频电路中，电场是一个**保守场（静电场是无旋场）**。这意味着电场力做功只与始末位置有关，与路径无关。如果你把一个电荷带离一个点，绕着电路走了一圈（经历了电源的抬升和电阻的消耗）又回到了原点，电场力对它做的总功必然为零：

$$\oint \vec{E} \cdot d\vec{l} = 0$$

* **能量守恒类比：** 电源像一台“电荷电梯”，消耗化学能把电子从低电势搬运到高电势（获得了电势能）；当电子流经电阻时，它在电梯里获得的电势能通过与原子晶格的碰撞，全部转化为了**热能**或**光能**。当它回到电池负极时，能量刚好耗尽。能量不会凭空产生，也不会凭空消失，这就是 KVL 的终极真相。
  </details>
</details> 

#### [>返回目录<](#Table-of-Contents)
<!-- 结束折叠内容 -->

----------------------------



<!-- 开始折叠内容 -->
<details open><summary>

## 🟪基础电子元器件
</summary>
      <details><summary>
        
### 🟦1. 电阻器
</summary>

<img alt="19" src="https://github.com/R2S-ver/Study-Electronics-Fundamentals/blob/main/assets/images/19.png" width="1024" height="1024" /> <br>

#### 什么是电阻器?
电阻器是一种无源电子元件，旨在阻碍电流的流动。在电路中，它就像电子的“减速带”。它的主要工作是限制通过的电流量（以防止 LED 等元件烧毁）以及分压（如在您的比较器电路中所见）。


<img alt="18" src="https://github.com/R2S-ver/Study-Electronics-Fundamentals/blob/main/assets/images/18.jpg" width="768" height="768" /> <br>

虽然有很多种类，但在爱好者电子产品（如 Tinkercad 中使用的那些）中最常见的是碳膜电阻器。 <br>
**1. 陶瓷骨架 (The Ceramic Core)** <br>
  中心是一根由高级陶瓷（一种绝缘体）制成的实心棒。它充当结构基础，不导电。 <br>
**2. 碳膜层 (The Carbon Film Layer)** <br>
  一层纯碳薄膜沉积在陶瓷棒周围。这层薄膜就是电子必须穿过的电阻材料。 <br>
**3. 螺旋槽 (The Helical Groove)** <br>
    螺旋路径越短、越宽 = 电阻越低 <br>
    螺旋路径越长、越窄 = 电阻越高 <br>
这实际上将薄膜变成了一根细长盘绕的碳“线”。 <br>
**4. 端帽和引脚 (End Caps and Leads)** <br>
金属端帽压接在圆柱体的两端。镀锡铜“引脚”（插入面包板的腿）焊接到这些端帽上，以将电阻器连接到电路的其余部分。 <br>
<img alt="21" src="https://github.com/R2S-ver/Study-Electronics-Fundamentals/blob/main/assets/images/21.png" width="346" height="537" /> <br>
**5. 保护涂层与色环 (Protective Coating & Color Bands)** <br>
最后，整个本体涂覆绝缘漆或环氧树脂，以防止潮湿和受热。表面涂有彩色条纹，以指示电阻值和容差。 <br>
<img alt="17" src="https://github.com/R2S-ver/Study-Electronics-Fundamentals/blob/main/assets/images/17.png" width="768" height="768" /> <br>
↑ 限制电流 VS 因电流过大导致 LED 烧毁
#### 理论：分压原理
在有多个电阻器的串联电路中，电压降与电阻成正比。如果电阻增加，其两端的电压也会增加（R↑ = V↑）。
**计算串联电阻（电压降）**
场景：一个 LED 在 3V 电压下工作，使用 5V 电源时消耗 13.5mA (0.0135A) 的电流
V_drop = V_source - V_LED = 2V
R = V_drop / I
R = 2V / 0.0135A = 148.15 欧姆 (**即使用 150 欧姆电阻**)

##### LED 可以看作电阻吗?
LED（发光二极管）不能被当作固定的欧姆电阻，因为它是一个非线性元件。标准电阻器遵循欧姆定律（电流与电压成正比），而 LED 则是具有非线性电流-电压曲线的二极管。

#### 实用电气原理图案例 - 电压比较器
<img alt="23" src="https://github.com/R2S-ver/Study-Electronics-Fundamentals/blob/main/assets/images/23.png" width="1024" height="1024" /> <br>
<img alt="22" src="https://github.com/R2S-ver/Study-Electronics-Fundamentals/blob/main/assets/images/22.png" width="1024" height="1024" /> <br>

#### 结论
<img alt="20" src="https://github.com/R2S-ver/Study-Electronics-Fundamentals/blob/main/assets/images/20.png" width="1024" height="1024" /> <br>

</details>
<details><summary>

### 🟦2. 电容器
</summary>

<img alt="27" src="https://github.com/R2S-ver/Study-Electronics-Fundamentals/blob/main/assets/images/27.png" width="1024" height="1024" /> <br>
<img alt="28" src="https://github.com/R2S-ver/Study-Electronics-Fundamentals/blob/main/assets/images/28.png" width="1024" height="1024" /> <br>

</details>
     <details><summary>

### 🟦3. 电感器
</summary>

<img alt="29" src="https://github.com/R2S-ver/Study-Electronics-Fundamentals/blob/main/assets/images/29.png" width="1024" height="1024" /> <br>

  #### 实用电气原理图案例 - 整流桥 (Pracical electrical schematic case - Rectifier Bridge)
  <img alt="24" src="https://github.com/R2S-ver/Study-Electronics-Fundamentals/blob/main/assets/images/24.png" width="1024" height="1024" /> <br>
  <img alt="25" src="https://github.com/R2S-ver/Study-Electronics-Fundamentals/blob/main/assets/images/25.png" width="1024" height="1024" /> <br>
  
</details>
     <details><summary>

### 🟦4. 二极管
</summary>

<img alt="30" src="https://github.com/R2S-ver/Study-Electronics-Fundamentals/blob/main/assets/images/30.png" width="1024" height="1024" /> <br>

  #### 实用电气原理图案例 - 整流桥 (Pracical electrical schematic case - Rectifier Bridge)
<img alt="26" src="https://github.com/R2S-ver/Study-Electronics-Fundamentals/blob/main/assets/images/26.png" width="1024" height="1024" /> <br>

</details>
     <details><summary>

### 🟦5. 晶体管
</summary>
        正在搞
</details>
     <details><summary>

### 🟦6. 场效应管
</summary>
        正在搞
</details>
     <details><summary>

### 🟦7. 线性与开关电源
</summary>

<img alt="31" src="https://github.com/R2S-ver/Study-Electronics-Fundamentals/blob/main/assets/images/31.png" width="1024" height="1024" /> <br>

#### 实用电气原理图案例 - 230V 转 12V 开关电源
<img alt="32" src="https://github.com/R2S-ver/Study-Electronics-Fundamentals/blob/main/assets/images/32.png" width="1024" height="1024" /> <br>
<img alt="33" src="https://github.com/R2S-ver/Study-Electronics-Fundamentals/blob/main/assets/images/33.png" width="1024" height="1024" /> <br>
<img alt="34" src="https://github.com/R2S-ver/Study-Electronics-Fundamentals/blob/main/assets/images/34.png" width="1024" height="1024" /> <br>

</details>
    <details><summary>

### 🟦8. 实用技能
</summary>
<img alt="35" src="https://github.com/R2S-ver/Study-Electronics-Fundamentals/blob/main/assets/images/35.png" width="1024" height="1024" /> <br>
</details>
     <details><summary>

### 🟦9. 元件参考资料
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
  </details>
  
#### [>返回目录<](#Table-of-Contents)
<!-- 结束折叠内容 -->
