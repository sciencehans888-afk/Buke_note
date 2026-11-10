# ELEC2104/9704 Tutorial 4 Solutions (2025)

## 1 Question 1（第 1 题）

A diode has $I_S = 10^{-16}$ A and $n = 1$.（一个二极管 $I_S = 10^{-16}$ A，$n = 1$。）

- (a) What is the diode current if the diode voltage is 0.675 V?（若二极管电压为 0.675 V，二极管电流是多少？）
- (b) What will be the diode voltage if the current increases by a factor of 3?（若电流增大到原来的 3 倍，二极管电压将是多少？）

Solution:（**解答：**）

For a diode, we have the equation below that describes the correlation between the diode voltage ($V_D$) and the diode current ($I_D$).（对于二极管，有下面的方程描述二极管电压（$V_D$）与二极管电流（$I_D$）之间的关系。）

$$
I_D = I_S\left[\exp\left(\frac{V_D}{nV_T}\right)-1\right] \tag{1}
$$

Where:（式中：）

- $n$ is the ideality factor, which accounts for carrier recombination in the depletion region. For an ideal diode, $n = 1$, while real diodes typically have $1 < n < 2$. We almost always assume $n = 1$ in this course.（$n$ 为理想因子，用来描述耗尽区中的载流子复合。理想二极管 $n=1$，实际二极管通常 $1<n<2$。本课程几乎总取 $n=1$。）
- $I_S$ is the saturation current (also called reverse saturation current).（$I_S$ 为饱和电流（也称反向饱和电流）。）
- $V_T = \dfrac{kT}{q}$ is the thermal voltage.（$V_T=\dfrac{kT}{q}$ 为热电压。）

![](Pasted%20image%2020261110143450.png)
> 图1 Diode I-V characteristic showing the exponential relationship in forward bias and the small leakage current ($-I_S$) in reverse bias. In forward bias where $V_D \gg V_T$, the exponential term dominates and $I_D \approx I_S e^{V_D/V_T}$.（图 1：二极管 I-V 特性，正偏时呈指数关系，反偏时有很小的漏电流（$-I_S$）。当 $V_D \gg V_T$ 时指数项占主导，$I_D \approx I_S e^{V_D/V_T}$。）

### 1.1 Part A: What is the diode current if the diode voltage is 0.675 V?（A 部分：若二极管电压为 0.675 V，二极管电流是多少？）

The values for the ideality factor and saturation current are given in the question:（题目给出了理想因子和饱和电流的数值：）

$$
n = 1 \tag{2}
$$

$$
I_S = 10^{-16}\,\mathrm{A} \tag{3}
$$

Since no temperature is given, we need to assume room temperature. The thermal voltage is given by:（由于题目未给温度，需要假设为室温。热电压为：）

$$
V_T = \frac{kT}{q} = \frac{(1.38 \times 10^{-23}\ \mathrm{J/K}) \cdot T}{1.602 \times 10^{-19}\ \mathrm{C}} \tag{4}
$$

Note that the Boltzmann constant $k$ and the elementary charge $q$ are fundamental physical constants.（注意玻尔兹曼常数 $k$ 和基本电荷 $q$ 都是基本物理常数。）

**Room Temperature Conventions（室温约定）**

Different sources use different room temperatures:（不同资料采用的室温不同：）

- $T = 293.15$ K (20°C): $V_T = 0.025$ V $= 25$ mV（$T=293.15$ K（20°C）：$V_T=0.025$ V $=25$ mV）
- $T = 300$ K (26.85°C): $V_T = 0.026$ V $= 26$ mV（$T=300$ K（26.85°C）：$V_T=0.026$ V $=26$ mV）

In exams, the temperature or thermal voltage should be provided. Note that it may be given implicitly in some other quantity. If neither is specified, you may use either 25 mV or 26 mV.（考试中会给出温度或热电压。注意它也可能隐含在某个其他量中。若两者都未给出，25 mV 或 26 mV 均可使用。）

Here we'll use $T = 293.15$ K:（这里取 $T=293.15$ K：）

$$
V_T = 0.025\ \mathrm{V} \tag{5}
$$

Taking (3), (2), and (5) into (1), the diode current is determined:（把 (3)、(2)、(5) 代入 (1)，即可确定二极管电流：）

$$
I_D = I_S\left[\exp\left(\frac{V_D}{nV_T}\right)-1\right] = \left(10^{-16}\ \mathrm{A}\right)\left[\exp\left(\frac{0.675\ \mathrm{V}}{0.025\ \mathrm{V}}\right)-1\right] = 5.32 \times 10^{-5}\ \mathrm{A} = 53.2\ \mathrm{\mu A} \tag{6}
$$

If we had used $T = 300$ K ($V_T = 0.026$ V), the result would be:（若采用 $T=300$ K（$V_T=0.026$ V），结果为：）

$$
I_D \approx 1.8 \times 10^{-5}\ \mathrm{A} = 18.83\ \mathrm{\mu A} \tag{7}
$$

### 1.2 Part B: What will be the diode voltage if the current increases by a factor of 3?（B 部分：若电流增大到原来的 3 倍，二极管电压将是多少？）

If the current increases by a factor of 3, the new current is:（若电流增大到原来的 3 倍，新电流为：）

$$
I_{D,\mathrm{new}} = 3I_D = 3 \cdot \left(5.32 \times 10^{-5}\ \mathrm{A}\right) = 1.60 \times 10^{-4}\ \mathrm{A} \tag{8}
$$

From (1), we can rearrange the equation to derive an expression about the new diode voltage (try to memorise this equation for $V_D$ in terms of $I_D$ as it is important):（由 (1) 可以整理出关于新二极管电压的表达式（这个用 $I_D$ 表示 $V_D$ 的式子很重要，建议记住）：）

$$
V_{D,\mathrm{new}} = nV_T\ln\left(\frac{I_{D,\mathrm{new}}}{I_S}+1\right) \tag{9}
$$

Taking (3), (2), (5) and (8) into (9), we can solve the new diode voltage.（把 (3)、(2)、(5)、(8) 代入 (9)，即可求出新的二极管电压。）

$$
V_{D,\mathrm{new}} = V_T\ln\left(\frac{I_{D,\mathrm{new}}}{I_S}+1\right) = (0.025)\ln\left(\frac{1.60 \times 10^{-4}}{10^{-16}}+1\right) = 0.702\ \mathrm{V} \tag{10}
$$

Note that above we used the $V_T = 25$ mV value for thermal voltage. For $V_T = 26$ mV:（注意上面热电压取的是 $V_T=25$ mV。若取 $V_T=26$ mV：）

$$
V_{D,\mathrm{new}} = 0.731\ \mathrm{V} \tag{11}
$$

**Note that you may have encountered rounding errors on this question. To reduce rounding errors, use the memory function in your calculator to save intermediate results.**（**注意：本题可能出现舍入误差。为减小误差，可用计算器的存储功能保存中间结果。**）

## 2 Question 2（第 2 题）

A diode is operating with $i_D = 2$ mA and $v_D = 0.82$ V.（一二极管工作在 $i_D=2$ mA、$v_D=0.82$ V。）

- (a) What is $I_S$ if $n = 1$?（若 $n=1$，$I_S$ 是多少？）
- (b) What is the diode current for $v_D = -5$ V?（当 $v_D=-5$ V 时，二极管电流是多少？）

Solution:（**解答：**）

### 2.1 Part 1: What is $I_S$ if $n = 1$?（第 1 部分：若 $n=1$，$I_S$ 是多少？）

For a diode, we have the equation below that describes the correlation between the diode voltage ($V_D$) and the diode current ($I_D$).（对于二极管，有下面的方程描述二极管电压（$V_D$）与二极管电流（$I_D$）之间的关系。）

$$
I_D = I_S\left[\exp\left(\frac{V_D}{nV_T}\right)-1\right] \tag{1}
$$

Note how that the ideality factor ($n$) is often omitted, in which case $n = 1$ is implied.（注意理想因子（$n$）常被省略，此时隐含 $n=1$。）

For the given set of diode voltage ($V_D$), diode current ($I_D$), ideality factor ($n$) and the assumption that the temperature is 20°C (which sets the thermal voltage $V_T$), we have the following:（对于给定的二极管电压（$V_D$）、二极管电流（$I_D$）、理想因子（$n$），以及温度取 20°C（由此确定热电压 $V_T$）的假设，有：）

$$
V_D = 0.82\,\mathrm{V} \tag{2}
$$

$$
I_D = 2\,\mathrm{mA} \tag{3}
$$

$$
n = 1 \tag{4}
$$

$$
V_T = 0.025\,\mathrm{V} \tag{5}
$$

Rearranging (1), we can derive an expression for the saturation current ($I_S$), where:（整理 (1)，可得饱和电流（$I_S$）的表达式：）

$$
I_S = \frac{I_D}{\exp\left(\dfrac{V_D}{nV_T}\right)-1} \tag{6}
$$

Taking (2), (3), (4), and (5) into (6), we can determine $I_S$.（把 (2)、(3)、(4)、(5) 代入 (6)，即可确定 $I_S$。）

$$
I_S = \frac{I_D}{\exp\left(\dfrac{V_D}{nV_T}\right)-1} = \frac{2 \times 10^{-3}\ \mathrm{A}}{\exp\left(\dfrac{0.82}{1 \times 0.025}\right)-1} = 1.14 \times 10^{-17}\ \mathrm{A} \tag{7}
$$

If $V_T = 26$ mV is used, the answer is $I_S = 4.02 \times 10^{-17}$ A.（若取 $V_T=26$ mV，答案为 $I_S=4.02\times10^{-17}$ A。）

### 2.2 Part 2: What is the diode current for $v_D$ = -5 V?（第 2 部分：当 $v_D=-5$ V 时，二极管电流是多少？）

A diode acts as a one-way valve for current – it allows current to flow easily in the forward direction (positive voltage) but blocks current in the reverse direction (negative voltage). When reverse biased ($V_D < 0$), only a tiny leakage current flows, approximately equal to $-I_S$. Let's verify this. Taking the known $n$, $V_D$, $I_S$ into (1), the diode current is determined:（二极管像单向阀：正偏（正电压）时电流容易通过，反偏（负电压）时阻断电流。反偏（$V_D<0$）时只有很小的漏电流，约等于 $-I_S$。下面验证这一点。把已知的 $n$、$V_D$、$I_S$ 代入 (1)，即可确定二极管电流：）

$$
I_D' = I_S\left[\exp\left(\frac{V_D'}{nV_T}\right)-1\right] = \left(1.14 \times 10^{-17}\right)\left[\exp\left(\frac{-5}{0.025}\right)-1\right] = -1.14 \times 10^{-17}\ \mathrm{A} \approx -I_S \tag{8}
$$

This confirms that in reverse bias, the diode current saturates at $-I_S$ (the reverse saturation current), which is typically on the order of $10^{-17}$ to $10^{-15}$ A – negligible for many practical circuits.（这验证了反偏时二极管电流饱和于 $-I_S$（反向饱和电流），其量级通常为 $10^{-17}$ 至 $10^{-15}$ A，对多数实际电路可忽略。）

**Permittivity of Silicon** $\varepsilon_s = \varepsilon_r \cdot \varepsilon_0$（**硅的介电常数** $\varepsilon_s = \varepsilon_r \cdot \varepsilon_0$）

The permittivity of a material is expressed as:（材料的介电常数表示为：）

$$
\varepsilon = \varepsilon_r \cdot \varepsilon_0
$$

where:（式中：）

- $\varepsilon_r$ is the relative permittivity (dielectric constant). For silicon: $\varepsilon_r = 11.7$ (commonly used in lectures). Despite the *constant* in "dielectric constant", it can vary depending on material properties and more!（$\varepsilon_r$ 为相对介电常数（介电常数）。硅：$\varepsilon_r=11.7$（课堂上常用）。尽管名称里有“常数”，它仍会随材料性质等因素变化！）
- $\varepsilon_0$ is the permittivity of free space $= 8.85 \times 10^{-14}$ F/cm（$\varepsilon_0$ 为真空介电常数 $=8.85\times10^{-14}$ F/cm）

This gives us $\varepsilon_{\mathrm{Si}} = \varepsilon_r \cdot \varepsilon_0 = 11.7 \cdot 8.85 \times 10^{-14} = 1.035 \times 10^{-12}$ F/cm（于是 $\varepsilon_{\mathrm{Si}} = \varepsilon_r \cdot \varepsilon_0 = 11.7 \cdot 8.85 \times 10^{-14} = 1.035 \times 10^{-12}$ F/cm。）

**Note:** The course table of constants uses $\varepsilon_r = 11.9$ for silicon, which would give $\varepsilon_{\mathrm{Si}} = 1.053 \times 10^{-12}$ F/cm（**注：** 课程常数表取硅的 $\varepsilon_r=11.9$，对应 $\varepsilon_{\mathrm{Si}}=1.053\times10^{-12}$ F/cm。）

**Permittivity and Capacitance（介电常数与电容）**

对于平行板电容器，电容为

$$
C=\frac{\varepsilon S}{d}=\frac{\varepsilon_0\varepsilon_r S}{d}
$$

式中 $S$ 为极板面积，$d$ 为极板间距，$\varepsilon=\varepsilon_0\varepsilon_r$ 为介电常数。

PN 结的耗尽区相当于平行板电容器：P区/N区 是两块“极板”，耗尽区是“介质”，极板间距就是耗尽宽度。因此结电容为

$$
C=\frac{\varepsilon_s A}{W}\qquad\left(\text{单位面积电容：}C_j=\frac{\varepsilon_s}{W}\right)
$$

式中 $A$ 为结面积，$W$ 为耗尽宽度。

反偏时耗尽宽度随电压增大，电容随之减小：

$$
C=\frac{C_0}{\sqrt{1+\dfrac{V_R}{\phi_i}}}
$$

式中 $C_0$ 为零偏电容，$\phi_i$ 为内建电势。


## 3 Question 3（第 3 题）

A square $pn$ junction diode is 5 mm on a side. The $p$-type side has a doping concentration of $10^{19}$/cm$^3$ and the $n$-type side has a doping concentration of $10^{16}$/cm$^3$.（一个正方形 pn 结二极管边长为 5 mm。p 型一侧掺杂浓度为 $10^{19}$/cm$^3$，n 型一侧为 $10^{16}$/cm$^3$。）

- (a) What is the **zero-bias capacitance** of the diode?（二极管的零偏电容是多少？）
- (b) What is the capacitance at a reverse bias of 4 V?（反向偏置 4 V 时的电容是多少？）

Solution:（**解答：**）

![](Pasted%20image%2020261110143514.png)
> 图2 Junction capacitance in a pn diode. The depletion region acts as a parallel-plate capacitor with the neutral regions forming the plates. The capacitance per unit area $C_{j0}$ depends on the permittivity $\varepsilon_s$ and depletion width $w_{d0}$. The depletion width can be derived from the doping concentrations ($N_A$ and $N_D$) and the built-in voltage $V_{bi}$.（图 2：pn 二极管中的结电容。耗尽区相当于平行板电容器，中性区构成两个极板。单位面积电容 $C_{j0}$ 取决于介电常数 $\varepsilon_s$ 与耗尽宽度 $w_{d0}$；耗尽宽度可由掺杂浓度（$N_A$、$N_D$）和内建电压 $V_{bi}$ 求出。）

Firstly, let's list the known parameters.（首先列出已知参数。）

$$
\text{Permittivity of Si:}\quad \varepsilon_{\mathrm{Si}} = 11.7\,\varepsilon_0 = 11.7 \times 8.85 \times 10^{-14} = 1.035 \times 10^{-12}\ \mathrm{F/cm} \tag{1}
$$

$$
\text{Elementary charge:}\quad q = 1.602 \times 10^{-19}\ \mathrm{C} \tag{2}
$$

$$
\text{Side length of the square junction:}\quad l = 5\ \mathrm{mm} = 0.5\ \mathrm{cm} \tag{3}
$$

$$
\text{Donor density:}\quad N_D = 10^{16}\ \mathrm{cm^{-3}} \tag{4}
$$

$$
\text{Acceptor density:}\quad N_A = 10^{19}\ \mathrm{cm^{-3}} \tag{5}
$$

### 3.1 Part A: What is the zero-bias capacitance of the diode?（A 部分：二极管的零偏电容是多少？）

**零偏电容**（zero-bias capacitance）：指 PN 结在未加任何外加电压（$V_R=0$，处于平衡态）时，耗尽区所呈现的电容。此时耗尽宽度为 $W_{d0}$，电容为

$$
C_0=\frac{\varepsilon_s A}{W_{d0}},\qquad C_{j0}=\frac{\varepsilon_s}{W_{d0}}
$$

式中：
- $C_0$：零偏时二极管的总电容（F）；
- $C_{j0}$：零偏时单位面积的结电容（F/cm²）；
- $A$：结面积（cm² 或 m²）；
- $W_{d0}$：零偏时的耗尽宽度（cm 或 m）；
- $\varepsilon_s$：硅的介电常数，$\varepsilon_s=\varepsilon_r\varepsilon_0$；
- $\varepsilon_r$：硅的相对介电常数，约 11.7；
- $\varepsilon_0$：真空介电常数，$8.854\times10^{-12}$ F/m（即 $8.854\times10^{-14}$ F/cm）；
- $V_R$：加在结上的反向偏置电压（V），零偏时 $V_R=0$。

The total zero-bias capacitance of the diode has the formula below, where $A$ is the junction area, $C_{j0}$ is the junction capacitance per unit area, and $W_{d0}$ is the zero-bias depletion width. Units are denoted in square brackets for clarity.（二极管零偏时的总电容按下式计算，其中 $A$ 为结面积，$C_{j0}$ 为**单位面积结电容**，$W_{d0}$ 为**零偏耗尽宽度**。为清楚起见，单位写在方括号内。）

in square brackets for clarity.（为清楚起见，单位写在方括号内。）

$$
C_0\ [\mathrm{F}] = C_{j0}\ [\mathrm{F/cm^2}] \cdot A\ [\mathrm{cm^2}] = \left(\frac{\varepsilon_s}{W_{d0}}\right) \cdot A\ [\mathrm{F}] \tag{6}
$$

Note again that here $A$ is the area of the juncition cross-section and since the side length of the square junction is given, we can determine this area:（再次注意，$A$ 是结横截面积；由于给出正方形结的边长，可求出该面积：）

$$
A = l \times l = (0.5\ \mathrm{cm})(0.5\ \mathrm{cm}) = 0.25\ \mathrm{cm^2} \tag{7}
$$

>在tu3中，我们有四个公式关于内建电压，这几个公式可以用来求耗尽区的宽度、最大场强等

$$
V_{bi} = \frac{1}{2} E_{\max} W \tag{1}
$$

$$
V_{bi} = \frac{1}{2} \frac{q N_A}{\varepsilon_s} x_p^2 + \frac{1}{2} \frac{q N_D}{\varepsilon_s} x_n^2 \tag{2}
$$

$$
V_{bi} = \frac{1}{2} \frac{q}{\varepsilon_s} \frac{N_A N_D}{N_A + N_D} W^2 \tag{3}
$$

$$
V_{bi} = \frac{1}{q} (E_{i,p} - E_{i,n}) = \frac{k_B T}{q} \ln \left( \frac{N_A N_D}{n_i^2} \right) \tag{4}
$$

The depletion width has the formula below.（耗尽宽度公式如下。）

$$
W_{d0} = \sqrt{\frac{2\varepsilon_s}{q}\left(\frac{1}{N_A}+\frac{1}{N_D}\right)\phi_i} \tag{8}
$$

It is good practice to mark which quantities are still unknown. Here, the built-in voltage $\phi_i$ (can also be denoted as $V_{bi}$) is unknown. Fortunately, we have sufficient parameters to determine $\phi_i$ using the formula presented in Lecture 4:（最好标出哪些量仍未知。这里内建电压 $\phi_i$（也可记为 $V_{bi}$）未知。所幸有足够参数，可用第 4 讲给出的公式求出 $\phi_i$：）

$$
\phi_i = V_T\ln\left(\frac{N_AN_D}{n_i^2}\right) \tag{9}
$$

Using assumptions for the thermal voltage ($V_T$) and the intrinsic carrier density of silicon ($n_i$), and the given values of doping concentrations from the question ($N_A$ and $N_D$), the value of the built-in voltage is:（取热电压（$V_T$）和硅本征载流子浓度（$n_i$）的假定值，并代入题目给出的掺杂浓度（$N_A$、$N_D$），可得内建电压：）

$$
\phi_i = (0.025\ \mathrm{V})\ln\left(\frac{(10^{19}\ \mathrm{cm^{-3}}) \cdot (10^{16}\ \mathrm{cm^{-3}})}{(10^{10}\ \mathrm{cm^{-3}})^2}\right) = 0.863\ \mathrm{V} \tag{10}
$$

Or $\phi_i = 0.898$ V, if the thermal voltage is $V_T = 26$ mA.（若热电压取 $V_T=26$ mA，则 $\phi_i=0.898$ V。）

Now, taking (10) into (8), the depletion width is determined.（现在把 (10) 代入 (8)，即可确定耗尽宽度。）

$$
W_{d0} = \sqrt{\frac{2\varepsilon_{\mathrm{Si}}}{q}\left(\frac{1}{N_A}+\frac{1}{N_D}\right)\phi_i} \tag{11}
$$

$$
= \sqrt{\left(\frac{2 \cdot 1.035 \times 10^{-12}\ \mathrm{F/cm}}{1.602 \times 10^{-19}\ \mathrm{C}}\right)\left(\frac{1}{10^{19}\ \mathrm{cm^{-3}}}+\frac{1}{10^{16}\ \mathrm{cm^{-3}}}\right)(0.863\ \mathrm{V})} \tag{12}
$$

$$
W_{d0} = \sqrt{1.119 \times 10^{-9}\ \mathrm{cm^2}} = 3.34 \times 10^{-5}\ \mathrm{cm} = 0.334\ \mathrm{\mu m}. \tag{13}
$$

Or $\phi_i = 0.341$ V, if the thermal voltage is $V_T = 26$ mA.（若热电压取 $V_T=26$ mA，则 $\phi_i=0.341$ V。）

**Dimensional Analysis Tip（量纲分析技巧）**

When working with semiconductor equations, always perform "unit algebra" as a sanity check:（处理半导体方程时，应始终做一次“**单位运算**”作为合理性检查：）

- Remember that $1\ \mathrm{F} = 1\ \mathrm{C/V}$ (Farads = Coulombs per Volt)（记住 $1\ \mathrm{F}=1\ \mathrm{C/V}$（法拉 = 库仑每伏特））
- Example, for the depletion width formula:（例如，对耗尽宽度公式：）

$$
\sqrt{\frac{[\mathrm{F/cm}]}{[\mathrm{C}]} \cdot [\mathrm{cm^3}] \cdot [\mathrm{V}]} = \sqrt{\frac{[\mathrm{C/V}] \cdot [\mathrm{cm^2}] \cdot [\mathrm{V}]}{[\mathrm{C}]}} = \sqrt{[\mathrm{cm^2}]} = [\mathrm{cm}]
$$

- This confirms our formula gives the correct units for distance!（这验证了公式给出的是正确的长度单位！）

> 注：对于物理单位来说，我们要把它看成一个可以算的量，这样无论对什么式子，我们都可以通过计算得到运算单位。

Taking (1), (7), and (13) into (6), the zero-bias capacitance is determined:（把 (1)、(7)、(13) 代入 (6)，即可确定零偏电容：）

$$
C_{j0} = \frac{\varepsilon_{\mathrm{Si}}}{W_{d0}} = \frac{1.035 \times 10^{-12}\ \mathrm{F/cm}}{3.34 \times 10^{-5}\ \mathrm{cm}} = 3.0974 \times 10^{-8}\ \mathrm{F/cm^2} \tag{14}
$$

The total capacitance across the junction cross-section area is then:（结横截面上的总电容则为：）

$$
C_0 = C_{j0} \cdot A = \left(3.0974 \times 10^{-8}\ \mathrm{F/cm^2}\right)(0.25\ \mathrm{cm^2}) = 7.7435 \times 10^{-9}\ \mathrm{F} = 7.74\ \mathrm{nF}. \tag{15}
$$

Or $C_{j0} = 3.0369 \times 10^{-8}$ F/cm$^2$ and $C_0 = 7.59$ nF if the thermal voltage is $V_T = 26$ mA.（若热电压取 $V_T=26$ mA，则 $C_{j0}=3.0369\times10^{-8}$ F/cm$^2$，$C_0=7.59$ nF。）

Alternatively, we can directly use the formula for junction capacitance per unit area by substituting the depletion width expression:（也可把耗尽宽度表达式代入，直接使用单位面积结电容公式：）

$$
C_{j0} = \sqrt{\frac{\varepsilon_s q}{2} \cdot \frac{N_AN_D}{N_A+N_D} \cdot \frac{1}{\phi_i}}\ \ \mathrm{F/cm^2} \tag{16}
$$

This combined formula is useful when you need to find capacitance directly from doping concentrations without explicitly calculating the depletion width first.（当希望由掺杂浓度直接求电容、而不先显式算出耗尽宽度时，这个合成公式很方便。）

### 3.2 Part B: What is the capacitance at a reverse bias of 4 V?（B 部分：反向偏置 4 V 时的电容是多少？）

For the pn junction with reverse bias $V_R$, the capacitance has the given formula, based on the zero-bias capacitance:（对加反向偏置 $V_R$ 的 pn 结，电容由零偏电容按给定公式计算：）

$$
C' = \frac{C_0}{\sqrt{1+\dfrac{V_R}{\phi_i}}} \tag{17}
$$

Taking (10), (15) and $V_R = 4$ V, the new capacitance with reverse bias is:（把 (10)、(15) 与 $V_R=4$ V 代入，可得反偏下的新电容：）

$$
C' = \frac{C_0}{\sqrt{1+\dfrac{V_R}{\phi_i}}} = \frac{7.7435\ \mathrm{nF}}{\sqrt{1+\dfrac{4\ \mathrm{V}}{0.863\ \mathrm{V}}}} = 3.263\ \mathrm{nF} \tag{18}
$$

Or $C' = 3.251$ nF if the thermal voltage is $V_T = 26$ mA.（若热电压取 $V_T=26$ mA，则 $C'=3.251$ nF。）

**Common Assumptions in Semiconductor Problems（半导体问题的常用假设）**

- **Thermal voltage:**（**热电压：**）
  - $T = 293.15$ K (20°C): $V_T = 25$ mV（$T=293.15$ K（20 °C）：$V_T=25$ mV）
  - $T = 300$ K (26.85°C): $V_T = 26$ mV（$T=300$ K（26.85 °C）：$V_T=26$ mV）
- **Intrinsic carrier concentration (Si):**（**本征载流子浓度（硅）：**）
  - Textbook approximation: $n_i = 10^{10}$ cm$^{-3}$（教材近似值：$n_i=10^{10}$ cm$^{-3}$）
  - Course table value: $n_i = 9.65 \times 10^{9}$ cm$^{-3}$（课程表取值：$n_i=9.65\times10^{9}$ cm$^{-3}$）
- **Relative permittivity of Si:**（**硅的相对介电常数：**）
  - Lecture/textbook: $\varepsilon_r = 11.7$（课堂/教材：$\varepsilon_r=11.7$）
  - Course table: $\varepsilon_r = 11.9$（课程表：$\varepsilon_r=11.9$）

In exams, use the values provided in the question, followed by the course table of constants (if not provided in the question).（考试时优先用题目给出的值；若题目未给，再用课程常数表。）

## 4 Question 4（第 4 题）

Consider a $pn$ junction in forward bias and assume $V_T = 26$ mV.（考虑正偏的 pn 结，假设 $V_T=26$ mV。）

1. To obtain a current of 1 mA with a voltage of 750 mV, how should $I_S$ be chosen?（要在 750 mV 下得到 1 mA 电流，$I_S$ 应取多少？）
2. If the diode cross-section area is now doubled, what voltage yields a current of 1 mA?（若二极管横截面积加倍，要得到 1 mA 电流需要多大电压？）

### 4.1 Part A: To obtain a current of 1 mA with a voltage of 750 mV, how should $I_S$ be chosen?（A 部分：要在 750 mV 下得到 1 mA 电流，$I_S$ 应取多少？）

For a diode, we have the equation below that describes the correlation between the diode voltage ($V_D$) and the diode current ($I_D$). Note that the ideality factor ($n$) is usually omitted when it equals one.（对于二极管，有下面的方程描述二极管电压（$V_D$）与电流（$I_D$）的关系。注意当理想因子（$n$）等于 1 时通常省略。）

$$
I_D = I_S\left[\exp\left(\frac{V_D}{V_T}\right)-1\right] \tag{1}
$$

With the given diode voltage ($V_D$) and the diode current ($I_D$), we can simply solve (1) to get the required saturation current $I_S$ :（用给定的二极管电压（$V_D$）和电流（$I_D$），直接解 (1) 即可得到所需的饱和电流 $I_S$：）

$$
I_S = \frac{I_D}{\exp\left(\dfrac{V_D}{V_T}\right)-1} = \frac{1 \times 10^{-3}\ \mathrm{A}}{\exp\left(\dfrac{0.75\ \mathrm{V}}{0.026\ \mathrm{V}}\right)-1} = 2.97 \times 10^{-16}\ \mathrm{A} \tag{2}
$$

Note that the thermal voltage ($V_T$) was given in this particular question.（注意本题已给出热电压（$V_T$）。）

### 4.2 Part B: If the diode cross-section area is now doubled, what voltage yields a current of 1 mA?（B 部分：若二极管横截面积加倍，要得到 1 mA 电流需要多大电压？）

As a physical property of a specific diode, the saturation current $I_S$ is determined by（作为特定二极管的物理属性，饱和电流 $I_S$ 由下式决定）

$$
I_S = A\,q\,n_i^2\left(\frac{D_n}{N_AL_n}+\frac{D_p}{N_DL_p}\right) \tag{3}
$$

式中：
- $I_S$：反向饱和电流（A）；
- $A$：二极管的横截面积（cm²）；
- $q$：电子电荷，$1.602\times10^{-19}$ C；
- $n_i$：本征载流子浓度（cm⁻³）；
- $D_n$、$D_p$：电子、空穴的扩散系数（diffusion coefficient），表示单位浓度梯度下产生多大扩散电流的比例系数（$J=qD\,\mathrm{d}n/\mathrm{d}x$）。它由材料和温度决定，不随浓度梯度改变；单位 cm²/s；可由爱因斯坦关系 $D=\mu k_BT/q$ 与迁移率联系；
- $L_n$、$L_p$：电子、空穴的扩散长度（diffusion length），表示少数载流子在复合前平均能扩散的距离，$L=\sqrt{D\tau}$（$\tau$ 为少子寿命），单位 cm；
- $N_A$、$N_D$：p 区受主浓度、n 区施主浓度（cm⁻³）。

From (3), we can see the proportional correlation between $I_S$ and the cross-section area $A$. So, if $A$ is doubled, $I_S$ will be doubled as a result. Let this doubled saturation current be $I_S'$:（由 (3) 可见 $I_S$ 与横截面积 $A$ 成正比。因此若 $A$ 加倍，$I_S$ 也随之加倍。记加倍后的饱和电流为 $I_S'$：）

$$
I_S' = 2I_S = 5.94 \times 10^{-16}\ \mathrm{A} \tag{4}
$$

由于题目是要求，求二极管电压，所以代入新的值，就可以算出电压了
$$
I_D = I_S\left[\exp\left(\frac{V_D}{V_T}\right)-1\right] 
$$

Now, we have the new saturation current $I_S'$. With the diode current unchanged, we can determine the new diode voltage, $V_D'$ :（现在已有新的饱和电流 $I_S'$。保持二极管电流不变，即可确定新的二极管电压 $V_D'$：）

$$
V_D' = V_T\ln\left(\frac{I_D}{I_S'}+1\right) \tag{5}
$$

$$
= (0.026\ \mathrm{V})\ln\left(\frac{1 \times 10^{-3}\ \mathrm{A}}{5.94 \times 10^{-16}\ \mathrm{A}}+1\right) = 0.732\ \mathrm{V} \tag{6}
$$

**The Ideal Diode Model（理想二极管模型）**

The ideal diode model is a simplified approximation that makes diode circuit analysis much easier:（理想二极管模型是一种简化近似，可使二极管电路分析容易得多：）

**Key Assumptions:（关键假设：）**

- When forward biased ($V_D > 0$): The diode acts as a **short circuit** (closed switch)（正偏（$V_D>0$）时：二极管相当于**短路**（闭合开关））
  - $V_D = 0$ V (no voltage drop across the diode)（$V_D=0$ V（二极管上无压降））
  - $I_D > 0$ A (current flows freely)（$I_D>0$ A（电流自由通过））
- When reverse biased ($V_D < 0$): The diode acts as an **open circuit** (open switch)（反偏（$V_D<0$）时：二极管相当于**开路**（断开开关））
  - $I_D = 0$ A (no current flows)（$I_D=0$ A（无电流））
  - $V_D < 0$ V (diode sustains reverse voltage)（$V_D<0$ V（二极管承受反向电压））

![](Pasted%20image%2020261110143544.png)
> 图 The ideal diode model I-V characteristic and circuit equivalents.（图：理想二极管模型的 I-V 特性及等效电路。）

## 5 Question 5（第 5 题）

Find the Q-point for the diodes in the circuits in Figure 3 using the ideal diode model.（用理想二极管模型求图 3 各电路中二极管的 Q 点。）

![](Pasted%20image%2020261110143603.png)
> 图3 Q5 circuit diagram（图 3：第 5 题电路图。）

**Notes for Q5:（第 5 题说明：）**

- The Q-point (operating point) of a diode is defined as $(V_D, I_D)$, that is, the voltage across and current through the diode, respectively.（二极管的 Q 点（工作点）定义为 $(V_D, I_D)$，即二极管两端的电压与通过它的电流。）
- To remember the polarity of the voltage ($V_D$) of a diode (which way is positive/negative), remember that the arrow-like symbol of the diode "points" to the negative side of $V_D$.（记住二极管电压（$V_D$）的极性（哪边为正、哪边为负）：二极管的箭头状符号“指向”$V_D$ 的负端。）
- For the ideal model:（对理想模型：）
  - ON state $\rightarrow$ ($V_D = 0$ V, $I_D > 0$ A)（导通状态 $\rightarrow$（$V_D=0$ V，$I_D>0$ A））
  - OFF state $\rightarrow$ ($V_D < 0$ V, $I_D = 0$ A)（截止状态 $\rightarrow$（$V_D<0$ V，$I_D=0$ A））

<p align="center">— Analysis strategy for multiple diodes —</p>（— 多二极管的分析策略 —）

**Step 0: Label the diodes** in the circuit diagram, including the direction of $V_D$ of each (polarity).（**第 0 步：标注二极管**，包括每个二极管 $V_D$ 的方向（极性）。）

**Step 1: Make an assumption** by guessing ON/OFF for each diode. Some tricks include:（**第 1 步：作假设**，猜测每个二极管导通/截止。一些技巧：）

- Inspect the circuit - if the diode's positive $V_D$ is connected to the highest voltage in the circuit, it must be ON.（观察电路——若二极管 $V_D$ 的正端接在电路中最高电压处，它必定导通。）
- If the diode's *negative* $V_D$ is connected to the lowest voltage in the circuit (i.e. ground), it must be ON.（若二极管 $V_D$ 的*负*端接在电路中最低电压处（即地），它必定导通。）

**Step 2: Simplify the circuit（第 2 步：简化电路）**

- Replace ON diodes with short circuits (i.e. wires, this sets $V_D = 0$ V).（把导通的二极管替换为短路（即导线，使 $V_D=0$ V）。）
- Replace OFF diodes with open circuits (this sets $I_D = 0$ A).（把截止的二极管替换为开路（使 $I_D=0$ A）。）

**Step 3: Solve for the Q-points**, which means find $V_D$ (for OFF diodes) or find $I_D$ (for ON diodes) for each and every diode in the circuit.（**第 3 步：求解 Q 点**，即对电路中每个二极管求出 $V_D$（截止管）或 $I_D$（导通管）。）

- This means you have to use circuit analysis on the simplified circuit from the previous step.（这意味着要对上一步简化后的电路做电路分析。）
- Typically, this involves using KVL and KCL as you would on a standard circuit.（通常就是像分析标准电路那样使用 KVL 和 KCL。）

>**KCL（基尔霍夫电流定律，Kirchhoff's Current Law）**：流入任一节点的电流之和等于流出该节点的电流之和，即节点处电流的代数和为零，$\sum I=0$。本质是电荷守恒——电荷不会在节点上堆积。

>**KVL（基尔霍夫电压定律，Kirchhoff's Voltage Law）**：沿任一闭合回路，各段电压降的代数和为零，$\sum V=0$。本质是能量守恒——绕行一圈回到原点，电势不会凭空变化。

**Step 4: Check the assumptions** made:（**第 4 步：检查假设**：）

- If any of the diodes that were assumed ON has $I_D < 0$, then the assumption was incorrect.（若某个假设导通的二极管出现 $I_D<0$，则假设不正确。）
- If any of the diodes that were assumed OFF has $V_D > 0$, then the assumption was incorrect.（若某个假设截止的二极管出现 $V_D>0$，则假设不正确。）

**Repeat:** If any assumptions were incorrect, start a new trial from Step 1 with corrected assumptions.（**重复：** 若假设有误，修正假设后从第 1 步重新开始。）

- On the next trial, flip one (or more) of the diodes that were incorrect from ON to OFF (or vice vice versa).（下一次尝试时，把出错的二极管中的一个或多个由导通改为截止（或反之）。）

The following solutions demonstrate this strategy.（下面的解答演示这一策略。）

Solution:（**解答：**）

### 5.1 Part A（A 部分）

**Step 0: Label Diodes**（**第 0 步：标注二极管**）
See Figure 4, which has diodes and node voltages labelled, as referenced in the text below.（见图 4，图中已标注二极管与节点电压，下文将引用。）

![](Pasted%20image%2020261110143626.png)
> 图4 Part A circuit diagram（图 4：A 部分电路图）

<p align="center">— Trial 1 —</p>（— 第 1 次尝试 —）

**Step 1: Make an assumption**（**第 1 步：作假设**）
We assume that all diodes $D_1$, $D_2$, and $D_3$ are ON.（假设所有二极管 $D_1$、$D_2$、$D_3$ 均导通。）

**Step 2: Simplify the circuit**（**第 2 步：简化电路**）
With all diodes ON (short circuits), node $A$ is shorted to the $+5$ V voltage source, and node $B$ is shorted to the $0$ V voltage source (ground). These short circuits force the voltages at nodes $A$ and $B$ to be:（所有二极管导通（短路）时，节点 $A$ 被短接到 $+5$ V 电源，节点 $B$ 被短接到 $0$ V 电源（地）。这些短接迫使节点 $A$、$B$ 的电压为：）

$$
V_A = 5\ \mathrm{V}, \qquad V_B = 0\ \mathrm{V}.
$$

**Step 3: Solve for the Q-points**（**第 3 步：求解 Q 点**）
According to Ohm's law, the currents through the resistors are determined using the values $V_A = 5$ V and $V_B = 0$ V found in the simplification step:（根据欧姆定律，利用简化步骤中得到的 $V_A=5$ V、$V_B=0$ V 求各电阻电流：）

$$
I_1 = \frac{10\ \mathrm{V}-V_A}{8.2\ \mathrm{k\Omega}} = \frac{10\ \mathrm{V}-5\ \mathrm{V}}{8.2\ \mathrm{k\Omega}} = 0.61\ \mathrm{mA} \tag{1}
$$

$$
I_4 = \frac{V_A-V_B}{12\ \mathrm{k\Omega}} = \frac{5\ \mathrm{V}-0\ \mathrm{V}}{12\ \mathrm{k\Omega}} = 0.42\ \mathrm{mA} \tag{2}
$$

$$
I_5 = \frac{V_B-(-5\ \mathrm{V})}{10\ \mathrm{k\Omega}} = \frac{0\ \mathrm{V}-(-5\ \mathrm{V})}{10\ \mathrm{k\Omega}} = 0.5\ \mathrm{mA} \tag{3}
$$

正常来说，Using KCL at node A: $I_1+I_2 = I_4$, therefore:（在节点 A 使用 KCL：$I_1+I_2=I_4$，因此：）

$$
I_2 = I_4 - I_1 = 0.42\ \mathrm{mA} - 0.61\ \mathrm{mA} = -0.19\ \mathrm{mA} < 0 \Rightarrow D_2\ \text{not ON!}
$$

For $D_1$, we have $I_1 = 0.61\ \mathrm{mA} > 0$, which would confirm $D_1$ is ON.（对 $D_1$，$I_1=0.61$ mA $>0$，说明 $D_1$ 导通。）
For $D_3$, using KCL at node B: $I_3+I_4 = I_5$, therefore:（对 $D_3$，在节点 B 使用 KCL：$I_3+I_4=I_5$，因此：）

$$
I_3 = I_5 - I_4 = 0.5\ \mathrm{mA} - 0.42\ \mathrm{mA} = 0.08\ \mathrm{mA} > 0 \Rightarrow D_3\ \text{ON}
$$

**Step 4: Check the assumptions**（**第 4 步：检查假设**）
We found that $D_2$ has a negative current $I_2$ through it, which means that $D_2$ cannot be ON. We proceed to try another guess with $D_2$ set to OFF.（我们发现 $D_2$ 中的电流 $I_2$ 为负，说明 $D_2$ 不可能导通。下面把 $D_2$ 设为截止再试。）

<p align="center">— Trial 2 —</p>（— 第 2 次尝试 —）

![](Pasted%20image%2020261110143641.png)
> 图（同图4）Part A circuit diagram（图（同图 4）：A 部分电路图）

**Step 1: Make an assumption**（**第 1 步：作假设**）
Now, assume $D_1$ and $D_3$ are ON, $D_2$ is OFF.（现在假设 $D_1$、$D_3$ 导通，$D_2$ 截止。）
**Step 2: Simplify the circuit**（**第 2 步：简化电路**）
With $D_3$ ON (short circuits), node $B$ is shorted to the $0$ V voltage (i.e. ground), so $V_B = 0$ V. With $D_2$ OFF (open circuit), we have $I_2 = 0$ A. We must determine $V_A$ through circuit analysis.（$D_3$ 导通（短路）时，节点 $B$ 被短接到 $0$ V（地），故 $V_B=0$ V。$D_2$ 截止（开路），故 $I_2=0$ A。还需通过电路分析求 $V_A$。）
**Step 3: Solve for the Q-points**（**第 3 步：求解 Q 点**）
Since $D_2$ is OFF (open circuit) with $I_2 = 0$ A, the $8.2$ k$\Omega$ and $12$ k$\Omega$ resistors are in series:（由于 $D_2$ 截止（开路），$I_2=0$ A，$8.2$ k$\Omega$ 与 $12$ k$\Omega$ 电阻串联：）

$$
I_1 = I_4 = \frac{10\ \mathrm{V}-0\ \mathrm{V}}{(8.2+12)\ \mathrm{k\Omega}} = \frac{10\ \mathrm{V}}{20.2\ \mathrm{k\Omega}} = 0.495\ \mathrm{mA} \Rightarrow D_1\ \text{ON} \tag{4}
$$

$$
I_5 = \frac{0\ \mathrm{V}-(-5\ \mathrm{V})}{10\ \mathrm{k\Omega}} = 0.5\ \mathrm{mA} \tag{5}
$$

$$
I_3 = I_5 - I_4 = 0.5\ \mathrm{mA} - 0.495\ \mathrm{mA} = 0.005\ \mathrm{mA} \Rightarrow D_3\ \text{ON} \tag{6}
$$

Note that because $I_2$ is zero, then $I_1 = I_4$ and we can also treat the $8.2$ k$\Omega$ and $12$ k$\Omega$ resistors as an equivalent series resistor (we cannot do this when $I_2$ is nonzero).（注意由于 $I_2$ 为零，有 $I_1=I_4$，也可把 $8.2$ k$\Omega$ 与 $12$ k$\Omega$ 电阻看作等效串联电阻（$I_2$ 不为零时不能这样做）。）

To find the voltage across $D_2$, we need $V_A$:（为求 $D_2$ 两端电压，需要先求 $V_A$：）

$$
V_{D_2} = 5\ \mathrm{V} - V_A \tag{7}
$$

Using Ohm's law:（由欧姆定律：）

$$
\begin{aligned}
V_A &= 10\ \mathrm{V} - I_1 \cdot 8.2\ \mathrm{k\Omega} \\
&= 10\ \mathrm{V} - 0.495\ \mathrm{mA} \cdot 8.2\ \mathrm{k\Omega} \\
&= 10\ \mathrm{V} - 4.06\ \mathrm{V} = 5.941\ \mathrm{V}
\end{aligned} \tag{8}
$$

Now we can find the voltage across the OFF diode:（现在可求截止二极管两端的电压：）

$$
V_{D_2} = 5\ \mathrm{V} - V_A = 5\ \mathrm{V} - 5.941\ \mathrm{V} = -0.941\ \mathrm{V} < 0 \Rightarrow D_2\ \text{OFF} \tag{9}
$$

**Step 4: Check the assumptions**（**第 4 步：检查假设**）
All assumptions are consistent: $D_1$ is ON with $I_{D_1} = 0.495\ \mathrm{mA} > 0$, $D_2$ is OFF with $V_{D_2} = -0.941\ \mathrm{V} < 0$ and $D_3$ is ON with $I_{D_3} = 0.005\ \mathrm{mA} > 0$. The assumptions from Trial 2 are correct! The final Q-points are:（所有假设自洽：$D_1$ 导通且 $I_{D_1}=0.495$ mA $>0$，$D_2$ 截止且 $V_{D_2}=-0.941$ V $<0$，$D_3$ 导通且 $I_{D_3}=0.005$ mA $>0$。第 2 次尝试的假设正确！最终 Q 点为：）

$$
\begin{aligned}
Q_{D_1} &= (I_{D_1} = 0.495\ \mathrm{mA},\ V_{D_1} = 0\ \mathrm{V}) \Rightarrow \text{ON} \\
Q_{D_2} &= (I_{D_2} = 0\ \mathrm{A},\ V_{D_2} = -0.941\ \mathrm{V}) \Rightarrow \text{OFF} \\
Q_{D_3} &= (I_{D_3} = 0.005\ \mathrm{mA},\ V_{D_3} = 0\ \mathrm{V}) \Rightarrow \text{ON}
\end{aligned}
$$

### 5.2 Part B（B 部分）

**Step 0: Label Diodes**（**第 0 步：标注二极管**）
See Figure 5, which has diodes and node voltages labelled, as referenced in the text below.（见图 5，图中已标注二极管与节点电压，下文将引用。）

![](Pasted%20image%2020261110143659.png)
> 图5 Part B circuit diagram（图 5：B 部分电路图）

<p align="center">— Trial 1 —</p>（— 第 1 次尝试 —）

**Step 1: Make an assumption**（**第 1 步：作假设**）
We assume that all diodes $D_1$, $D_2$, and $D_3$ are ON.（假设所有二极管 $D_1$、$D_2$、$D_3$ 均导通。）
**Step 2: Simplify the circuit**（**第 2 步：简化电路**）
With all diodes ON (short circuits), node $A$ is shorted to the $+5$ V voltage source, and node $B$ is shorted to the $0$ V voltage (ground). These short circuits force the voltages at nodes $A$ and $B$ to be:（所有二极管导通（短路）时，节点 $A$ 被短接到 $+5$ V 电源，节点 $B$ 被短接到 $0$ V（地）。这些短接迫使节点 $A$、$B$ 的电压为：）

$$
V_A = 5\ \mathrm{V}, \qquad V_B = 0\ \mathrm{V}.
$$

**Step 3: Solve for the Q-points**（**第 3 步：求解 Q 点**）
According to Ohm's law, the currents through the resistors are determined using the values $V_A = 5$ V and $V_B = 0$ V found in the simplification step:（根据欧姆定律，利用简化步骤中得到的 $V_A=5$ V、$V_B=0$ V 求各电阻电流：）

$$
I_1 = \frac{10\ \mathrm{V}-V_A}{3.3\ \mathrm{k\Omega}} = \frac{10\ \mathrm{V}-5\ \mathrm{V}}{3.3\ \mathrm{k\Omega}} = 1.52\ \mathrm{mA} \Rightarrow D_1\ \text{ON} \tag{10}
$$

$$
I_4 = \frac{V_A-V_B}{6.8\ \mathrm{k\Omega}} = \frac{5\ \mathrm{V}-0\ \mathrm{V}}{6.8\ \mathrm{k\Omega}} = 0.74\ \mathrm{mA} \tag{11}
$$

$$
I_5 = \frac{V_B-(-5\ \mathrm{V})}{2.4\ \mathrm{k\Omega}} = \frac{0\ \mathrm{V}-(-5\ \mathrm{V})}{2.4\ \mathrm{k\Omega}} = 2.08\ \mathrm{mA} \tag{12}
$$

Using KCL at node B: $I_3+I_4 = I_5$, therefore:（在节点 B 使用 KCL：$I_3+I_4=I_5$，因此：）

$$
I_3 = I_5 - I_4 = 2.08\ \mathrm{mA} - 0.74\ \mathrm{mA} = 1.34\ \mathrm{mA} > 0 \Rightarrow D_3\ \text{ON}
$$

Using KCL at node A: $I_1+I_2 = I_4$, therefore:（在节点 A 使用 KCL：$I_1+I_2=I_4$，因此：）

$$
I_2 = I_4 - I_1 = 0.74\ \mathrm{mA} - 1.52\ \mathrm{mA} = -0.78\ \mathrm{mA} < 0 \Rightarrow D_2\ \text{not ON!}
$$

**Step 4: Check the assumptions**（**第 4 步：检查假设**）
We found that $D_2$ has a negative current $I_2$ through it, which means that $D_2$ cannot be ON. We proceed to try another guess with $D_2$ set to OFF:（我们发现 $D_2$ 中的电流 $I_2$ 为负，说明 $D_2$ 不可能导通。下面把 $D_2$ 设为截止再试：）

<p align="center">— Trial 2 —</p>（— 第 2 次尝试 —）

![](Pasted%20image%2020261110143716.png)
> 图（同图5）Part B circuit diagram（图（同图 5）：B 部分电路图）

**Step 1: Make an assumption**（**第 1 步：作假设**）
Now, assume $D_1$ and $D_3$ are ON, while $D_2$ is OFF.（现在假设 $D_1$、$D_3$ 导通，$D_2$ 截止。）
**Step 2: Simplify the circuit**（**第 2 步：简化电路**）
With $D_1$ and $D_3$ ON (short circuits), node $A$ is shorted to the $+5$ V voltage source, so $V_A = 5$ V, and node $B$ is shorted to the $0$ V voltage (ground), so $V_B = 0$ V. With $D_2$ OFF (open circuit), we have $I_2 = 0$ A.（$D_1$、$D_3$ 导通（短路）时，节点 $A$ 被短接到 $+5$ V 电源，故 $V_A=5$ V；节点 $B$ 被短接到 $0$ V（地），故 $V_B=0$ V。$D_2$ 截止（开路），故 $I_2=0$ A。）
**Step 3: Solve for the Q-points**（**第 3 步：求解 Q 点**）
Since $D_2$ is OFF (open circuit) with $I_2 = 0$ A, the $3.3$ k$\Omega$ and $6.8$ k$\Omega$ resistors are in series:（由于 $D_2$ 截止（开路），$I_2=0$ A，$3.3$ k$\Omega$ 与 $6.8$ k$\Omega$ 电阻串联：）

$$
I_1 = I_4 = \frac{10\ \mathrm{V}-0\ \mathrm{V}}{(3.3+6.8)\ \mathrm{k\Omega}} = \frac{10\ \mathrm{V}}{10.1\ \mathrm{k\Omega}} = 0.99\ \mathrm{mA} \Rightarrow D_1\ \text{ON} \tag{13}
$$

$$
I_5 = \frac{0\ \mathrm{V}-(-5\ \mathrm{V})}{2.4\ \mathrm{k\Omega}} = 2.08\ \mathrm{mA} \tag{14}
$$

$$
I_3 = I_5 - I_4 = 2.08\ \mathrm{mA} - 0.99\ \mathrm{mA} = 1.09\ \mathrm{mA} \Rightarrow D_3\ \text{ON} \tag{15}
$$

Note that we can treat the $3.3$ k$\Omega$ and $6.8$ k$\Omega$ resistors as in series because $I_2$ is zero (we cannot do this when $I_2$ is nonzero).（注意由于 $I_2$ 为零，可把 $3.3$ k$\Omega$ 与 $6.8$ k$\Omega$ 电阻看作串联（$I_2$ 不为零时不能这样做）。）
To find the voltage across $D_2$, we need $V_A$. Using Ohm's law:（为求 $D_2$ 两端电压，需要先求 $V_A$。由欧姆定律：）

$$
\begin{aligned}
V_A &= 10\ \mathrm{V} - I_1 \cdot 3.3\ \mathrm{k\Omega} \\
&= 10\ \mathrm{V} - 0.99\ \mathrm{mA} \cdot 3.3\ \mathrm{k\Omega} \\
&= 10\ \mathrm{V} - 3.27\ \mathrm{V} = 6.73\ \mathrm{V}
\end{aligned} \tag{16}
$$

Now we can find the voltage across the OFF diode:（现在可求截止二极管两端的电压：）

$$
V_{D_2} = 5\ \mathrm{V} - V_A = 5\ \mathrm{V} - 6.73\ \mathrm{V} = -1.73\ \mathrm{V} < 0 \Rightarrow D_2\ \text{OFF} \tag{17}
$$

**Step 4: Check the assumptions**（**第 4 步：检查假设**）
All assumptions are consistent: $D_1$ is ON with $I_{D_1} = 0.99\ \mathrm{mA} > 0$, $D_2$ is OFF with $V_{D_2} = -1.73\ \mathrm{V} < 0$ and $D_3$ is ON with $I_{D_3} = 1.09\ \mathrm{mA} > 0$. The assumptions from Trial 2 are correct! The final Q-points are:（所有假设自洽：$D_1$ 导通且 $I_{D_1}=0.99$ mA $>0$，$D_2$ 截止且 $V_{D_2}=-1.73$ V $<0$，$D_3$ 导通且 $I_{D_3}=1.09$ mA $>0$。第 2 次尝试的假设正确！最终 Q 点为：）

$$
\begin{aligned}
Q_{D_1} &= (I_{D_1} = 0.99\ \mathrm{mA},\ V_{D_1} = 0\ \mathrm{V}) \Rightarrow \text{ON} \\
Q_{D_2} &= (I_{D_2} = 0\ \mathrm{A},\ V_{D_2} = -1.73\ \mathrm{V}) \Rightarrow \text{OFF} \\
Q_{D_3} &= (I_{D_3} = 1.09\ \mathrm{mA},\ V_{D_3} = 0\ \mathrm{V}) \Rightarrow \text{ON}
\end{aligned}
$$

### 5.3 Part C（C 部分）

**Step 0: Label Diodes**（**第 0 步：标注二极管**）
See Figure 6, which has diodes and node voltages labelled, as referenced in the text below.（见图 6，图中已标注二极管与节点电压，下文将引用。）

![](Pasted%20image%2020261110143732.png)
> 图6 Part C circuit diagram（图 6：C 部分电路图）

<p align="center">— Trial 1 —</p>（— 第 1 次尝试 —）

**Step 1: Make an assumption**（**第 1 步：作假设**）
We assume that all diodes $D_1$, $D_2$, and $D_3$ are ON.（假设所有二极管 $D_1$、$D_2$、$D_3$ 均导通。）
**Step 2: Simplify the circuit**（**第 2 步：简化电路**）
With all diodes ON (short circuits), node $A$ is shorted to the $0$ V voltage (ground), and node $B$ is shorted to the $+5$ V voltage source. These short circuits force the voltages at nodes $A$ and $B$ to be:（所有二极管导通（短路）时，节点 $A$ 被短接到 $0$ V（地），节点 $B$ 被短接到 $+5$ V 电源。这些短接迫使节点 $A$、$B$ 的电压为：）

$$
V_A = 0\ \mathrm{V}, \qquad V_B = 5\ \mathrm{V}.
$$

**Step 3: Solve for the Q-points**（**第 3 步：求解 Q 点**）
According to Ohm's law, the three currents through the resistors are determined using the values $V_A = 0$ V and $V_B = 5$ V found in the simplification step:（根据欧姆定律，利用简化步骤中得到的 $V_A=0$ V、$V_B=5$ V 求三个电阻电流：）

$$
I_3 = \frac{12\ \mathrm{V}-V_B}{4.7\ \mathrm{k\Omega}} = \frac{12\ \mathrm{V}-5\ \mathrm{V}}{4.7\ \mathrm{k\Omega}} = 1.49\ \mathrm{mA} \tag{18}
$$

$$
I_4 = \frac{V_B-V_A}{4.7\ \mathrm{k\Omega}} = \frac{5\ \mathrm{V}-0\ \mathrm{V}}{4.7\ \mathrm{k\Omega}} = 1.06\ \mathrm{mA} \tag{19}
$$

$$
I_5 = \frac{V_A-(-5\ \mathrm{V})}{4.7\ \mathrm{k\Omega}} = \frac{0\ \mathrm{V}-(-5\ \mathrm{V})}{4.7\ \mathrm{k\Omega}} = 1.06\ \mathrm{mA} \tag{20}
$$

Using KCL at node A: $I_1+I_4 = I_5$, therefore:（在节点 A 使用 KCL：$I_1+I_4=I_5$，因此：）

$$
I_1 = I_5 - I_4 = 1.06\ \mathrm{mA} - 1.06\ \mathrm{mA} = 0\ \mathrm{mA} \Rightarrow D_1\ \text{not ON!}
$$

Using KCL at node B: $I_2+I_3 = I_4$, therefore:（在节点 B 使用 KCL：$I_2+I_3=I_4$，因此：）

$$
I_2 = I_4 - I_3 = 1.06\ \mathrm{mA} - 1.49\ \mathrm{mA} = -0.43\ \mathrm{mA} < 0 \Rightarrow D_2\ \text{not ON!}
$$

For $D_3$, we have $I_3 = 1.49\ \mathrm{mA} > 0$, which confirms $D_3$ is ON.（对 $D_3$，$I_3=1.49$ mA $>0$，说明 $D_3$ 导通。）
**Step 4: Check the assumptions**（**第 4 步：检查假设**）
We found that $D_1$ has zero current (borderline case) and $D_2$ has negative current. Since we assumed both were ON, this is impossible. We need to try another guess with $D_1$ and $D_2$ set to OFF.（我们发现 $D_1$ 电流为零（临界情况），$D_2$ 电流为负。既然假设二者都导通，这不可能成立。需要把 $D_1$、$D_2$ 设为截止再试。）

<p align="center">— Trial 2 —</p>（— 第 2 次尝试 —）

![](Pasted%20image%2020261110143746.png)
> 图（同图6）Part C circuit diagram（图（同图 6）：C 部分电路图）

**Step 1: Make an assumption**（**第 1 步：作假设**）
Now, assume $D_1$ and $D_2$ are OFF, while $D_3$ is ON.（现在假设 $D_1$、$D_2$ 截止，$D_3$ 导通。）
**Step 2: Simplify the circuit**（**第 2 步：简化电路**）
With $D_1$ and $D_2$ OFF (open circuits), we have $I_1 = 0$ A and $I_2 = 0$ A. With $D_3$ ON (short circuit), we have $V_{D_3} = 0$ V. We must determine both $V_A$ and $V_B$ through circuit analysis.（$D_1$、$D_2$ 截止（开路），故 $I_1=0$ A、$I_2=0$ A。$D_3$ 导通（短路），故 $V_{D_3}=0$ V。还需通过电路分析求 $V_A$ 与 $V_B$。）
**Step 3: Solve for the Q-points**（**第 3 步：求解 Q 点**）
Since $D_1$ and $D_2$ are OFF (open circuits) and $D_3$ is ON, all the current must flow through the series path from 12 V through the three 4.7 k$\Omega$ resistors to $-5$ V:（由于 $D_1$、$D_2$ 截止（开路），$D_3$ 导通，全部电流只能经由从 12 V 到 $-5$ V、由三个 4.7 k$\Omega$ 电阻构成的串联路径流动：）

$$
\begin{aligned}
I_5 = I_4 = I_3 &= \frac{12\ \mathrm{V}-(-5\ \mathrm{V})}{4.7\ \mathrm{k\Omega}+4.7\ \mathrm{k\Omega}+4.7\ \mathrm{k\Omega}} \\
&= \frac{17\ \mathrm{V}}{14.1\ \mathrm{k\Omega}} = 1.21\ \mathrm{mA} \Rightarrow D_3\ \text{ON}
\end{aligned} \tag{21}
$$

To find the voltages across $D_1$ and $D_2$, we need to determine $V_A$ and $V_B$. Using Ohm's law from the left (rearranged for $V_A$):（为求 $D_1$、$D_2$ 两端电压，需先确定 $V_A$、$V_B$。从左侧用欧姆定律（整理出 $V_A$）：）

$$
\begin{aligned}
V_A &= -5\ \mathrm{V} + I_5 \cdot 4.7\ \mathrm{k\Omega} \\
&= -5\ \mathrm{V} + 1.21\ \mathrm{mA} \cdot 4.7\ \mathrm{k\Omega} \\
&= -5\ \mathrm{V} + 5.67\ \mathrm{V} = 0.67\ \mathrm{V}
\end{aligned} \tag{22}
$$

And from the right (rearranged for $V_B$):（再从右侧（整理出 $V_B$）：）

$$
\begin{aligned}
V_B &= 12\ \mathrm{V} - I_3 \cdot 4.7\ \mathrm{k\Omega} \\
&= 12\ \mathrm{V} - 1.21\ \mathrm{mA} \cdot 4.7\ \mathrm{k\Omega} \\
&= 12\ \mathrm{V} - 5.67\ \mathrm{V} = 6.33\ \mathrm{V}
\end{aligned} \tag{23}
$$

Now we can find the voltages across the OFF diodes:（现在可求截止二极管两端的电压：）

$$
V_{D_1} = 0\ \mathrm{V} - V_A = 0\ \mathrm{V} - 0.67\ \mathrm{V} = -0.67\ \mathrm{V} < 0 \Rightarrow D_1\ \text{OFF} \tag{24}
$$

$$
V_{D_2} = 5\ \mathrm{V} - V_B = 5\ \mathrm{V} - 6.33\ \mathrm{V} = -1.33\ \mathrm{V} < 0 \Rightarrow D_2\ \text{OFF} \tag{25}
$$

**Step 4: Check the assumptions**（**第 4 步：检查假设**）
All assumptions are consistent: $D_1$ is OFF with $V_{D_1} = -0.67\ \mathrm{V} < 0$, $D_2$ is OFF with $V_{D_2} = -1.33\ \mathrm{V} < 0$ and $D_3$ is ON with $I_{D_3} = 1.21\ \mathrm{mA} > 0$. The final Q-points are:（所有假设自洽：$D_1$ 截止且 $V_{D_1}=-0.67$ V $<0$，$D_2$ 截止且 $V_{D_2}=-1.33$ V $<0$，$D_3$ 导通且 $I_{D_3}=1.21$ mA $>0$。最终 Q 点为：）

$$
\begin{aligned}
Q_{D_1} &= (I_{D_1} = 0\ \mathrm{A},\ V_{D_1} = -0.67\ \mathrm{V}) \Rightarrow \text{OFF} \\
Q_{D_2} &= (I_{D_2} = 0\ \mathrm{A},\ V_{D_2} = -1.33\ \mathrm{V}) \Rightarrow \text{OFF} \\
Q_{D_3} &= (I_{D_3} = 1.21\ \mathrm{mA},\ V_{D_3} = 0\ \mathrm{V}) \Rightarrow \text{ON}
\end{aligned}
$$

### 5.4 Part D（D 部分）

**Step 0: Label Diodes**（**第 0 步：标注二极管**）
See Figure 7, which has diodes and node voltages labelled, as referenced in the text below.（见图 7，图中已标注二极管与节点电压，下文将引用。）

![](Pasted%20image%2020261110205510.png)
> 图7 Part D circuit diagram（图 7：D 部分电路图）

<p align="center">— Trial 1 —</p>（— 第 1 次尝试 —）

**Step 1: Make an assumption**（**第 1 步：作假设**）
We assume that all diodes $D_1$, $D_2$, and $D_3$ are ON.（假设所有二极管 $D_1$、$D_2$、$D_3$ 均导通。）
**Step 2: Simplify the circuit**（**第 2 步：简化电路**）
With all diodes ON (short circuits), node $A$ is shorted to the $0$ V voltage (ground), and node $B$ is shorted to the $2$ V voltage source. These short circuits force the voltages at nodes $A$ and $B$ to be:（所有二极管导通（短路）时，节点 $A$ 被短接到 $0$ V（地），节点 $B$ 被短接到 $2$ V 电源。这些短接迫使节点 $A$、$B$ 的电压为：）

$$
V_A = 0\ \mathrm{V}, \qquad V_B = 2\ \mathrm{V}.
$$

**Step 3: Solve for the Q-points**（**第 3 步：求解 Q 点**）
According to Ohm's law, the currents through the resistors are determined using the values $V_A = 0$ V and $V_B = 2$ V found in the simplification step:（根据欧姆定律，利用简化步骤中得到的 $V_A=0$ V、$V_B=2$ V 求各电阻电流：）

$$
I_1 = \frac{V_A-(-10\ \mathrm{V})}{8.2\ \mathrm{k\Omega}} = \frac{0\ \mathrm{V}-(-10\ \mathrm{V})}{8.2\ \mathrm{k\Omega}} = 1.220\ \mathrm{mA} \Rightarrow D_1\ \text{ON} \tag{26}
$$

$$
I_4 = \frac{V_B-V_A}{12\ \mathrm{k\Omega}} = \frac{2\ \mathrm{V}-0\ \mathrm{V}}{12\ \mathrm{k\Omega}} = 0.167\ \mathrm{mA} \tag{27}
$$

$$
I_5 = \frac{(-5\ \mathrm{V})-V_B}{10\ \mathrm{k\Omega}} = \frac{(-5\ \mathrm{V})-2\ \mathrm{V}}{10\ \mathrm{k\Omega}} = -0.7\ \mathrm{mA} \tag{28}
$$

Note that $I_5$ represents the current flowing from right to left through the $10$ k$\Omega$ resistor. Since we got a negative value, the current actually flows from left to right (from node $B$ toward $-5$ V).（注意 $I_5$ 表示从右向左流过 $10$ k$\Omega$ 电阻的电流。由于结果为负，实际电流从左向右（由节点 $B$ 流向 $-5$ V）。）
Using KCL at node A: $I_2+I_4 = I_1$, therefore:（在节点 A 使用 KCL：$I_2+I_4=I_1$，因此：）

$$
I_2 = I_1 - I_4 = 1.220\ \mathrm{mA} - 0.167\ \mathrm{mA} = 1.053\ \mathrm{mA} > 0 \Rightarrow D_2\ \text{ON}
$$

Using KCL at node B: $I_4 = I_3+I_5$, therefore:（在节点 B 使用 KCL：$I_4=I_3+I_5$，因此：）

$$
I_3 = I_4 - I_5 = 0.167\ \mathrm{mA} - (-0.7\ \mathrm{mA}) = 0.867\ \mathrm{mA} > 0 \Rightarrow D_3\ \text{ON}
$$

**Step 4: Check the assumptions**（**第 4 步：检查假设**）
All three diode currents are positive: $I_{D_1} = 1.220\ \mathrm{mA} > 0$, $I_{D_2} = 1.053\ \mathrm{mA} > 0$ and $I_{D_3} = 0.867\ \mathrm{mA} > 0$. All assumptions are consistent. This is a case where all three diodes are indeed ON in the final solution. The final Q-points are:（三个二极管电流均为正：$I_{D_1}=1.220$ mA $>0$，$I_{D_2}=1.053$ mA $>0$，$I_{D_3}=0.867$ mA $>0$。所有假设自洽。本例最终解中三个二极管确实都导通。最终 Q 点为：）

$$
\begin{aligned}
Q_{D_1} &= (I_{D_1} = 1.22\ \mathrm{mA},\ V_{D_1} = 0\ \mathrm{V}) \Rightarrow \text{ON} \\
Q_{D_2} &= (I_{D_2} = 1.05\ \mathrm{mA},\ V_{D_2} = 0\ \mathrm{V}) \Rightarrow \text{ON} \\
Q_{D_3} &= (I_{D_3} = 0.867\ \mathrm{mA},\ V_{D_3} = 0\ \mathrm{V}) \Rightarrow \text{ON}
\end{aligned}
$$

---
