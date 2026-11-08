# ELEC2104/9704 tutorial 3 (2025)

Before the tutorial, there is a small formula sheet for you.（在辅导课开始之前，这里给你准备了一份小的公式表。）

| Symbol                                      | Description                                                                                                                                                                                                     |
| ------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| $V_{bi}$ **or** $\phi_{bi}$ **or** $\phi_j$ | Built-in potential across the depletion region at zero applied bias (V).<br>（零外加偏压下跨耗尽区的内建电势（V）。）                                                                                                               |
| $E_{\max}$                                  | Maximum magnitude of the electric field at the metallurgical junction (V/m or V/µm).<br>（冶金结处的电场强度最大值（V/m 或 V/µm）。）                                                                                             |
| $W$                                         | Total depletion width, $W = x_p + x_n$ (m or µm).<br>（总耗尽宽度，$W = x_p + x_n$（m 或 µm）。）                                                                                                                           |
| $x_p$                                       | Portion of the depletion width extending into the p-type side (m or µm).（耗尽宽度延伸到 p 型一侧的部分（m 或 µm）。）                                                                                                             |
| $x_n$                                       | Portion of the depletion width extending into the n-type side (m or µm).（耗尽宽度延伸到 n 型一侧的部分（m 或 µm）。）                                                                                                             |
| $q$                                         | Elementary charge, $1.602 \times 10^{-19}$ C.<br>（基本电荷量，$1.602 \times 10^{-19}$ C。）                                                                                                                             |
| $N_A$                                       | Acceptor (p-type) doping concentration (cm⁻³ or m⁻³).<br>（受主（p 型）掺杂浓度（cm⁻³ 或 m⁻³）。）                                                                                                                             |
| $N_D$                                       | Donor (n-type) doping concentration (cm⁻³ or m⁻³).<br>（施主（n 型）掺杂浓度（cm⁻³ 或 m⁻³）。）                                                                                                                                |
| $\varepsilon_s$                             | Semiconductor permittivity ($\varepsilon_s = \varepsilon_r \varepsilon_0$; for Si, $\varepsilon_r \approx 11.7$).（半导体介电常数（$\varepsilon_s = \varepsilon_r \varepsilon_0$；对 Si 而言，$\varepsilon_r \approx 11.7$）。） |
| $\varepsilon_0$                             | Vacuum permittivity, $8.854 \times 10^{-12}$ F/m.<br>（真空介电常数，$8.854 \times 10^{-12}$ F/m。）                                                                                                                      |
| $k_B$                                       | Boltzmann constant, $1.380\ 649 \times 10^{-23}$ J/K $= 8.617\ 333 \times 10^{-5}$ eV/K.<br>（玻尔兹曼常数，$1.380\ 649 \times 10^{-23}$ J/K $= 8.617\ 333 \times 10^{-5}$ eV/K。）                                       |
| $T$                                         | Absolute temperature (K).<br>（绝对温度（K）。）                                                                                                                                                                         |
| $n_i$                                       | Intrinsic carrier concentration of the semiconductor (cm⁻³ or m⁻³); for Si at room temperature, $10^{10}$ cm⁻³. This value is given in the statements of Questions 1 and 2, and is reused in Question 3.<br>（半导体的本征载流子浓度（cm⁻³ 或 m⁻³）；室温下硅取 $10^{10}$ cm⁻³。该值在第 1、2 题的题干中给出，第 3 题沿用。）                 |
| $E_{i,p}$, $E_{i,n}$                        | Intrinsic Fermi levels in the p- and n-side quasi-neutral regions (eV); at equilibrium<br>（p 侧与 n 侧准中性区中的本征费米能级（eV）；在平衡态下）                                                                                      |

**补充：题干或解答中出现、但上表未列出的符号**

| Symbol | Description |
| --- | --- |
| $k_BT$ | Thermal energy at room temperature, $26$ meV.（室温热能量，26 meV；第 1、2 题给出。） |
| $E_F$ | Fermi level (eV).（费米能级。） |
| $E_C-E_i$ | Conduction-band edge to intrinsic Fermi level for Si at room temperature, $\approx0.56$ eV.（室温硅的导带底与本征费米能级之差。） |
| $q\phi_M$ | Metal work function; for gold, $5.1$ eV.（金属功函数；金的为 5.1 eV。） |
| $q\chi$ | Semiconductor electron affinity; for Si, $4.05$ eV.（半导体电子亲和势；硅的为 4.05 eV。） |
| $\phi_i$ | Built-in potential of a Schottky contact (V).（肖特基结的内建电势。） |
| $X_d$ | Depletion width on the semiconductor side of a Schottky contact (m or µm).（肖特基结半导体一侧的耗尽宽度。） |
| $V_T$ | Thermal voltage, $V_T=k_BT/q\approx0.025$ V.（热电压。） |
| $V_R$ | Reverse-bias voltage applied to the junction (V).（加在结上的反向偏置电压。） |
| $W_{d0}$, $W_d$ | Depletion width at zero bias and at reverse bias $V_R$ (m or µm).（零偏置和反偏 $V_R$ 下的耗尽宽度。） |

There are several formulas for the built-in voltage; you can pick any of them regarding the provided parameters that are known.
（内建电压有若干个公式；你可以根据已知的参数从中任选一个。）

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

## 1 Question 1

We have a p-type semiconductor with a dopant concentration $N_A = 10^{17}$ cm⁻³.（我们有一个掺杂浓度 $N_A = 10^{17}$ cm⁻³ 的 p 型半导体。）

Given the intrinsic carrier concentration $n_i = 10^{10}$ cm⁻³, $k_B T = 26$ meV, where is the Fermi level with respect to $E_i$?（已知本征载流子浓度 $n_i = 10^{10}$ cm⁻³、$k_B T = 26$ meV，费米能级相对于 $E_i$ 位于何处？）

**Solution:**（**解答：**）

For a p-type silicon, the acceptor density $N_A$ is much higher than the donor density $N_D$.（对于 p 型硅，受主浓度 $N_A$ 远高于施主浓度 $N_D$。）

Since $N_D$ is not given, we assume it is negligible, that is close to 0 cm⁻³.（由于未给出 $N_D$，我们假设它可忽略不计，即接近于 0 cm⁻³。）Then we can calculate the hole density $p$ by:（于是我们可以用下式计算空穴浓度 $p$：）

$$
p = N_A - N_D \approx N_A = 10^{17}\ \text{cm}^{-3} \tag{1}
$$

We have the formula to determine the hole density if the we have the intrinsic carrier density ($n_i$), the intrinsic potential ($E_i$) and the fermi level ($E_f$).（若已知本征载流子浓度（$n_i$）、本征电势（$E_i$）和费米能级（$E_f$），我们就有一个用于确定空穴浓度的公式。）

$$
p = n_i \exp \left( \frac{E_i - E_F}{k_B T} \right) \tag{2}
$$

Re-arrange equation (2), we can get（重排方程 (2)，我们可以得到）

$$
E_i - E_F = k_B T \ln \left( \frac{p}{n_i} \right) \tag{3}
$$

The thermal energy $k_B T$ and the intrinsic carrier density $n_i$ are given by the question as（题目给出的热能量 $k_B T$ 和本征载流子浓度 $n_i$ 为）

$$
k_B T = 0.026\ \text{eV}, \tag{4}
$$

$$
n_i = 10^{10}\ \text{cm}^{-3}. \tag{5}
$$

Now, we take equation (1),(2),(3) into (4), we can get（现在，我们把方程 (1)、(2)、(3) 代入 (4)，可以得到）

$$
E_i - E_F = k_B T \ln \frac{p}{n_i} = (0.026\ \text{eV}) \ln \frac{10^{17}}{10^{10}} \approx 0.42\ \text{eV}, \tag{6}
$$

Finally we find that the fermi level is 0.42 eV higher than $E_i$.（最终我们求得费米能级比 $E_i$ 高 0.42 eV。）

## 2 Question 2

A Schottky contact is formed by gold and n-type silicon.（肖特基接触由金和 n 型硅形成。）

The doping level of silicon is $N_D = 10^{16}$ cm⁻³.（硅的掺杂浓度为 $N_D = 10^{16}$ cm⁻³。）

Intrinsic carrier density of silicon is $10^{10}$ cm⁻³.（硅的本征载流子浓度为 $10^{10}$ cm⁻³。）

What is the Fermi level in silicon?（硅中的费米能级在哪里？）

We know gold has a work function $(q\phi_M) = 5.1$ eV.（我们知道金的功函数为 $(q\phi_M) = 5.1$ eV。）

Silicon has an electron affinity $(q\chi)$ of 4.05 eV, and a permittivity of $\varepsilon = 11.7\ \varepsilon_0$, where $\varepsilon_0 = 8.854 \times 10^{-12}$ F m⁻¹.（硅的电子亲和势 $(q\chi)$ 为 4.05 eV，介电常数为 $\varepsilon = 11.7\ \varepsilon_0$，其中 $\varepsilon_0 = 8.854 \times 10^{-12}$ F m⁻¹。）

**注：**

- **金属功函数 $q\phi_M$**：把一个电子从金属内部的费米能级 $E_{F,M}$ 拿到真空能级 $E_0$（真空中的静止自由电子:指完全脱离固体的电子）所需要的最小能量。
- **半导体电子亲和能 $q\chi$**：把一个电子从半导体的导带底 $E_C$ 拿到真空能级 $E_0$ 所需要的最小能量。硅的 $q\chi_{Si}=4.05$ eV。

两者的终点都是真空能级，区别只在起点：功函数从金属费米能级算起，电子亲和能从半导体导带底算起。

What is the depletion length in silicon?（硅中的耗尽长度是多少？）


**Solution:**（**解答：**）

Similar to Q1, since n-type silicon and the dopant density $N_D$ are given while the acceptor density $N_A$ is not mentioned, we will take the dopant density as the electron density.（与第 1 题类似，由于给出的是 n 型硅和施主浓度 $N_D$，而未提及受主浓度 $N_A$，我们将把施主浓度当作电子浓度。）

$$
n = N_D - N_A \approx N_D = 10^{16}\ \text{cm}^{-3} \tag{1}
$$

We have the formula to determine the electron density if the we have the intrinsic carrier density ($n_i$), the intrinsic potential ($E_i$) and the fermi level ($E_f$).（若已知本征载流子浓度（$n_i$）、本征电势（$E_i$）和费米能级（$E_f$），我们就有一个用于确定电子浓度的公式。）

$$
n = n_i \exp \left( \frac{E_F - E_i}{k_B T} \right) \tag{2}
$$

Re-arrange equation (2), we can get（重排方程 (2)，我们可以得到）

$$
E_F - E_i = k_B T \ln \left( \frac{n}{n_i} \right) \tag{3}
$$

The thermal energy $k_B T$ and the intrinsic carrier density $n_i$ are given by the question as（题目给出的热能量 $k_B T$ 和本征载流子浓度 $n_i$ 为）

$$
k_B T = 0.026\ \text{eV}, \tag{4}
$$

$$
n_i = 10^{10}\ \text{cm}^{-3}. \tag{5}
$$

Now, we take equation (1),(2),(3) into (4), we can get（现在，我们把方程 (1)、(2)、(3) 代入 (4)，可以得到）

$$
E_F - E_i = k_B T \ln \frac{n}{n_i} = (0.026\ \text{eV}) \ln \frac{10^{16}}{10^{10}} \approx 0.36\ \text{eV}, \tag{6}
$$

In a Schottky contact (Au on n-Si), we have the following physical property, where the built-in energy satisfies equation (7).（在肖特基接触（Au 接触 n-Si）中，具有如下物理性质，其中内建能量满足方程 (7)。）

The equation can be derive from corelation in figure 1.（该方程可由图 1 中的关系推导得出。）

$$
q\phi_i = q\phi_M - q\chi - (E_C - E_F), \tag{7}
$$

![](Pasted%20image%2020261108164720.png)

*Figure 1: Energy level in a Schottky contact*（图 1：肖特基接触中的能级）

Now, let's find the value of each parameter in equation (7).（现在，让我们求方程 (7) 中每个参数的数值。）

The physical properties of gold and silicon are provided in the question, as（金和硅的物理性质在题目中已给出，即）

$$
q\phi_M = 5.1\ \text{eV}, \qquad (\text{gold work function}) \tag{8}
$$

$$
q\chi_{Si} = 4.05\ \text{eV}, \qquad (\text{silicon electron affinity}) \tag{9}
$$

The energy difference between the conduction band and the Fermi level $E_C - E_F$ can be determined.（导带与费米能级之间的能量差 $E_C - E_F$ 可以求出。）、

Using $E_C - E_i = 0.56$ eV (the energy difference between the conduction band and the intrinsic Fermi level for Si at room temperature), we can obtain the built-in energy as（利用 $E_C - E_i = 0.56$ eV（室温下 Si 的导带与本征费米能级之间的能量差），我们可以得到内建能量为）

$$
E_C - E_F = (E_C - E_i) - (E_F - E_i) = 0.56\ \text{eV} - 0.36\ \text{eV} = 0.20\ \text{eV}. \tag{10}
$$

Taking (8),(9),(10) into (7), we will get（把 (8)、(9)、(11) 代入 (7)，我们将得到）

$$
\phi_i = 5.1 - 4.05 - 0.20 = 0.85\ \text{V}. \tag{11}
$$

**注（$\phi_i$ 与 $V_{bi}$、$\phi_B$ 的关系）：**

- $\phi_i$ 就是肖特基结的内建电势（built-in potential），与 PN 结中的 $V_{bi}$（$\phi_{bi}$、$\phi_j$）是同一类物理量，只是符号习惯不同。
- 从能量角度看，内建电势就是**接触前金和硅的费米能级差**：$q\phi_i=E_{F,Si}-E_{F,Au}$（取正值）。接触后两侧费米能级被拉平，这个差值就表现为半导体一侧的能带弯曲。

**注：** **题目错误**
- $q\phi_M = 5.1\ \text{eV}, \qquad (\text{gold work function}) \tag{8}$题目中是5.1，但是图里面是4.75

There is another expression for the built-in potential based on the depletion width $X_d$, the permittivity $\varepsilon$, and the donor density $N_D$:（还有另一个用耗尽宽度 $X_d$、介电常数 $\varepsilon$ 和施主浓度 $N_D$ 表示内建电势的表达式：）

<u>公式表里面是这个公式：</u>
$$
V_{bi}=\frac12\frac{qN_A}{\varepsilon_s}x_p^2+\frac12\frac{qN_D}{\varepsilon_s}x_n^2
$$
<u>由于这是个N型半导体，所以，受主的参杂浓度几乎为0，所以只有后面一项，</u>
$$
\phi_i = \frac{q N_D X_d^2}{2 \varepsilon_{Si}}. \tag{12}
$$

Rearranging (12), the depletion width is（重排 (12)，耗尽宽度为）

$$
X_d = \sqrt{\frac{2 \varepsilon_{Si} \phi_i}{q N_D}}. \tag{13}
$$

Last thing before the final result, we list all the material parameters below.（在得出最终结果之前的最后一步，我们把所有材料参数列在下面。）

$$
\varepsilon_{Si} = 11.7 \times \varepsilon_0 \tag{14}
$$

$$
\varepsilon_0 = 8.854 \times 10^{-12}\ \text{F/m} \tag{15}
$$

$$
N_D = 10^{16}\ \text{cm}^{-3} = 10^{22}\ \text{m}^{-3} \tag{16}
$$

Note: uncommonly, we use meter as the unit of length here, due to the unit of $\varepsilon_0$（注意：由于 $\varepsilon_0$ 的单位，此处不常见地采用米作为长度单位。）

Finally, we determine the depletion length.（最后，我们确定耗尽长度。）

$$
X_d = \sqrt{\frac{2 \varepsilon_{Si} \phi_i}{q N_D}} \approx \sqrt{\frac{2(11.7)(8.854 \times 10^{-12})(0.85)}{(1.602 \times 10^{-19})(10^{22})}} \approx 3.3 \times 10^{-7}\ \text{m} = 0.33\ \text{µm}.
$$

## 3 Question 3

A diode has a doping of $N_D = 10^{20}$ cm⁻³ on the n-type side and $N_A = 10^{18}$ cm⁻³ on the p-type side.（一个二极管 n 型一侧的掺杂为 $N_D = 10^{20}$ cm⁻³，p 型一侧的掺杂为 $N_A = 10^{18}$ cm⁻³。）

What are the values of the depletion width ($W_{d0}$) and built-in voltage ($\phi_j$)?（耗尽宽度（$W_{d0}$）和内建电压（$\phi_j$）的值是多少？）

What is the maximum electric field intensity?（最大电场强度是多少？）

What are the depletion widths $x_p$, $x_n$?（耗尽宽度 $x_p$、$x_n$ 分别是多少？）

What is the value of the depletion width ($W_d$) at a reverse bias of 5 V?（在 5 V 反向偏置下耗尽宽度（$W_d$）的值是多少？）At 25 V?（在 25 V 时呢？）

**Solution:**（**解答：**）

Firstly, let's organize all the parameters that are known.（首先，让我们整理所有已知参数。）

$$
N_D = 10^{20}\ \text{cm}^{-3} \qquad (\text{donor density at n-side}) \tag{1}
$$

$$
N_A = 10^{18}\ \text{cm}^{-3} \qquad (\text{acceptor density at p-side}) \tag{2}
$$

$$
n_i = 10^{10}\ \text{cm}^{-3} \qquad (\text{intrinsic carrier density；本征载流子浓度}) \tag{3}
$$

$$
V_T = \frac{k_B T}{q} = 0.025\ \text{V} \qquad (\text{thermal voltage at room temp.；室温热电压}) \tag{4}
$$

$$
\varepsilon_{Si} = \varepsilon_r \varepsilon_0 = 11.7 \times 8.854 \times 10^{-12} \approx 1.04 \times 10^{-10}\ \text{F/m} \qquad (\text{permittivity of Si；硅的介电常数}) \tag{5}
$$

$$
q = 1.602 \times 10^{-19}\ \text{C} \qquad (\text{elementary charge；基本电荷量}) \tag{6}
$$

**注：** 本题只给出了 $N_D$ 和 $N_A$，其余参数沿用前两题题干中的数值或由公式表算出：

- $n_i=10^{10}$ cm⁻³：来自第 1、2 题的题干（两题都给出该值），本题沿用，不能由公式表算出。严格公式为 $n_i=\sqrt{N_CN_V}\,e^{-E_g/(2k_BT)}$，其中 $N_C$、$N_V$ 为导带、价带的有效状态密度，$E_g$ 为禁带宽度，这三个量表中没有给出。
- $V_T$：可由表中参数算出，$V_T=\dfrac{k_BT}{q}=\dfrac{1.380\ 649\times10^{-23}\times300}{1.602\times10^{-19}}\approx0.0259$ V；也可由第 1、2 题给出的 $k_BT=26$ meV 直接换算为 0.026 V。本题取 0.025 V。
- $\varepsilon_{Si}$：与第 2 题给出的 $\varepsilon=11.7\varepsilon_0$、$\varepsilon_0=8.854\times10^{-12}$ F/m 相同，也可由表中的 $\varepsilon_r\varepsilon_0$ 算出，约 $1.04\times10^{-10}$ F/m。
- $q$：表中直接给出的基本物理常数。

We have a formula for the built-in voltage ($\phi_j$), whose parameters are only $N_D$, $N_A$, $n_i$, and $V_T$.（我们有一个用于内建电压（$\phi_j$）的公式，其参数只有 $N_D$、$N_A$、$n_i$ 和 $V_T$。）

**注：公式表里是这个公式**
$$
V_{bi}=\frac{k_BT}{q}\ln\frac{N_AN_D}{n_i^2}
$$

This formula is shown in equation (7).（该公式如方程 (7) 所示。）

$$
\phi_j = V_T \ln \left( \frac{N_A N_D}{n_i^2} \right) \tag{7}
$$

Taking (1),(2),(3),(4) into (7), we can determine the value of the built-in voltage of the pn junction.（把 (1)、(2)、(3)、(4) 代入 (7)，我们就能确定 pn 结内建电压的值。）

$$
\phi_j = V_T \ln \frac{N_A N_D}{n_i^2} = (0.025) \ln \frac{10^{18} \cdot 10^{20}}{(10^{10})^2} \approx 1.04\ \text{V}. \tag{8}
$$

Next, let's write down the formula for the pn junction depletion length ($W_{d0}$), where the parameters are $\varepsilon_{Si}$, $q$, $N_A$, $N_D$ and $\phi_j$.（接下来，让我们写出 pn 结耗尽长度（$W_{d0}$）的公式，其参数为 $\varepsilon_{Si}$、$q$、$N_A$、$N_D$ 和 $\phi_j$。）

$$
W_{d0} = \sqrt{\frac{2 \varepsilon_{Si}}{q} \left( \frac{1}{N_A} + \frac{1}{N_D} \right) \phi_j} \tag{9}
$$

**注：** 这里用的是公式表里这个公式的变形

$$
V_{bi}=\frac12\frac{q}{\varepsilon_s}\frac{N_AN_D}{N_A+N_D}W^2
$$


Take (1),(2),(6), (8) into (9), we can determined the depletion length.（把 (1)、(2)、(6)、(8) 代入 (9)，我们就能确定耗尽长度。）

Please pay as much attention as you can to the UNITs!（请尽可能注意单位！）

$$
\begin{aligned}
W_{d0} &= \sqrt{\frac{2 \varepsilon_{Si}}{q} \left( \frac{1}{N_A} + \frac{1}{N_D} \right) \phi_j} \\
&= \sqrt{\frac{2(11.7)(8.854 \times 10^{-14}\ \text{F/cm})}{1.602 \times 10^{-19}\ \text{C}} \left( \frac{1}{10^{18}\ \text{cm}^{-3}} + \frac{1}{10^{20}\ \text{cm}^{-3}} \right) (1.04\ \text{V})} \approx 0.0368\ \text{µm}.
\end{aligned}
\tag{10}
$$


To determine the maximum electric field intensity ($E_{\max}$), we will apply the equation below which describes the correlation between the built-in voltage and $E_{\max}$, where（为了确定最大电场强度（$E_{\max}$），我们将应用下面这个描述内建电压与 $E_{\max}$ 之间关系的方程，其中）

$$
V_{bi} = \frac{1}{2} E_{\max} W \tag{11}
$$

Rearranging (11) and take (8),(10) into it, we can determine the maximum electric field intensity as（重排 (11) 并把 (8)、(10) 代入其中，我们可以确定最大电场强度为）

$$
E_{\max} = \frac{2 \phi_j}{W_{d0}} = \frac{2(1.04)}{0.0368}\ \frac{\text{V}}{\text{µm}} \approx 56.52\ \frac{\text{V}}{\text{µm}}. \tag{12}
$$

At page 44 of the lecture slide, the formulas for the portion of the depletion width extended into p-side and n-side $x_p$, $x_n$ are provided as（在讲座幻灯片第 44 页，给出了耗尽宽度延伸到 p 侧和 n 侧的部分 $x_p$、$x_n$ 的公式，即）

$$
x_p = \frac{N_D}{N_A + N_D} W_{d0} \tag{13}
$$

$$
x_n = \frac{N_A}{N_A + N_D} W_{d0}. \tag{14}
$$

Taking the values of $N_A$, $N_D$ and $W_{d0}$ into (13) and (14), $x_p$ and $x_n$ are determined as（把 $N_A$、$N_D$ 和 $W_{d0}$ 的值代入 (13) 和 (14)，可确定 $x_p$ 和 $x_n$ 为）

$$
x_p = \frac{10^{20}}{10^{18} + 10^{20}} \times 0.0368\ \text{µm} \approx 0.0364\ \text{µm}, \tag{15}
$$

$$
x_n = \frac{10^{18}}{10^{18} + 10^{20}} \times 0.0368\ \text{µm} \approx 0.00036\ \text{µm}. \tag{16}
$$

Lastly, as shown in figure 2, for the pn junction with bias, we can determine the new built-in voltage using the formula in (17), where the bias $V_R$ is the only variable.（最后，如图 2 所示，对于加偏置的 pn 结，我们可以用 (17) 中的公式确定新的内建电压，其中偏置 $V_R$ 是唯一的变量。）

Note: Conventionally, we define the positive end of $V_R$ is connected to the n-side of the pn junction.（注意：按惯例，我们定义 $V_R$ 的正端连接到 pn 结的 n 侧。）

$$
W_d = W_{d0} \sqrt{1 + \frac{V_R}{\phi_j}} \tag{17}
$$

![](Pasted%20image%2020261108164745.png)

*Figure 2: pn junction with bias*（图 2：加偏置的 pn 结）

Using (17) with $V_R = 5$ V,（当 $V_R = 5$ V 时使用 (17)，）

$$
W_d(5\ \text{V}) = W_{d0} \sqrt{1 + \frac{V_R}{\phi_j}} = (0.0368\ \text{µm}) \sqrt{1 + \frac{5}{1.04}} \approx 0.0887\ \text{µm}.
$$

Using (17) with $V_R = 25$ V,（当 $V_R = 25$ V 时使用 (17)，）

$$
W_d(25\ \text{V}) = (0.0368\ \text{µm}) \sqrt{1 + \frac{25}{1.04}} \approx 0.184\ \text{µm}.
$$


---

# 对应知识点

## 名词解释

Built-in potential（$V_{bi}$，$\phi_j$，$\phi_{bi}$）：内建电势，平衡态下 PN 结耗尽区两侧的电势差，由掺杂浓度决定，约 0.6–1 V。

Fermi level（$E_F$）：费米能级，决定载流子浓度分布的参考能级。n 型中 $E_F$ 高于 $E_i$，p 型中 $E_F$ 低于 $E_i$。

Intrinsic Fermi level（$E_i$）：本征费米能级，近似位于禁带中央。

Intrinsic carrier concentration（$n_i$）：本征载流子浓度，未掺杂时电子与空穴的浓度，硅室温约 $10^{10}$ cm⁻³。

Donor（$N_D$）：施主，提供电子的掺杂原子，形成 n 型半导体。

Acceptor（$N_A$）：受主，提供空穴的掺杂原子，形成 p 型半导体。

Depletion region：耗尽区（空间电荷区），扩散后留下未中和离子、几乎没有自由载流子的区域。

Depletion approximation：耗尽近似，假设耗尽区内无自由载流子、边界突变，从而把泊松方程变成分段常数。

Depletion width（$W$，$x_p$，$x_n$）：耗尽宽度，$W=x_p+x_n$；$x_p$、$x_n$ 分别是延伸到 p 侧、n 侧的部分。

Maximum electric field（$E_{\max}$）：最大电场强度，出现在冶金结处，向两侧线性减小到零。

Thermal voltage（$V_T$）：热电压，$V_T=k_BT/q$，室温约 25 mV。

Work function（$q\phi_M$）：功函数，把电子从金属费米能级移到真空所需的能量。

Electron affinity（$q\chi$）：电子亲和势，把电子从半导体导带底移到真空所需的能量。

Schottky contact：肖特基接触，金属与半导体形成的整流接触，存在势垒 $\phi_i$。

Reverse bias（$V_R$）：反向偏置，使势垒升高、耗尽区变宽的偏置方式。

## 公式解释

$V_{bi}=\frac12 E_{\max}W$：电势差等于三角形电场的面积，由泊松方程积分得到。

$V_{bi}=\frac12\frac{qN_A}{\varepsilon_s}x_p^2+\frac12\frac{qN_D}{\varepsilon_s}x_n^2$：两侧耗尽区分别积分，各贡献一段抛物线电势。

$V_{bi}=\frac12\frac{q}{\varepsilon_s}\frac{N_AN_D}{N_A+N_D}W^2$：把 $x_p$、$x_n$ 用 $W$ 消去后的等价形式。

$V_{bi}=\frac1q(E_{i,p}-E_{i,n})=\frac{k_BT}{q}\ln\frac{N_AN_D}{n_i^2}$：平衡时费米能级对齐，两侧本征能级差就是内建电势，用掺杂浓度表示。

$p=n_i e^{(E_i-E_F)/k_BT}$：空穴浓度与费米能级的关系，$E_F$ 越低空穴越多，用于求 p 型半导体中的费米能级位置。

$E_i-E_F=k_BT\ln(p/n_i)$：上式反解，代入 $p\approx N_A$ 即可算出数。

$q\phi_i=q\phi_M-q\chi-(E_C-E_F)$：肖特基接触的能量关系，由图 1 的能带图直接读出。

$\phi_i=\frac{qN_DX_d^2}{2\varepsilon_{Si}}$：单边突变结中耗尽宽度与内建电势的关系，重排得 $X_d=\sqrt{\frac{2\varepsilon_{Si}\phi_i}{qN_D}}$。

$W_{d0}=\sqrt{\frac{2\varepsilon_{Si}}{q}\left(\frac1{N_A}+\frac1{N_D}\right)\phi_j}$：一般 PN 结的平衡耗尽宽度。

$x_p=\frac{N_D}{N_A+N_D}W_{d0}$，$x_n=\frac{N_A}{N_A+N_D}W_{d0}$：由电荷中性 $N_Ax_p=N_Dx_n$ 分配，轻掺杂一侧更宽。

$W_d=W_{d0}\sqrt{1+\frac{V_R}{\phi_j}}$：反偏时内建电势变为 $\phi_j+V_R$，耗尽宽度随之增大。

---
