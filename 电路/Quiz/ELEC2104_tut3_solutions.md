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
| $n_i$                                       | Intrinsic carrier concentration of the semiconductor (cm⁻³ or m⁻³).<br>（半导体的本征载流子浓度（cm⁻³ 或 m⁻³）。）                                                                                                               |
| $E_{i,p}$, $E_{i,n}$                        | Intrinsic Fermi levels in the p- and n-side quasi-neutral regions (eV); at equilibrium<br>（p 侧与 n 侧准中性区中的本征费米能级（eV）；在平衡态下）                                                                                      |

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

Taking (8),(9),(11) into (7), we will get（把 (8)、(9)、(11) 代入 (7)，我们将得到）

$$
\phi_i = 5.1 - 4.05 - 0.20 = 0.85\ \text{V}. \tag{11}
$$

There is another expression for the built-in potential based on the depletion width $X_d$, the permittivity $\varepsilon$, and the donor density $N_D$:（还有另一个用耗尽宽度 $X_d$、介电常数 $\varepsilon$ 和施主浓度 $N_D$ 表示内建电势的表达式：）

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
n_i = 10^{10}\ \text{cm}^{-3} \qquad (\text{intrinsic carrier density}) \tag{3}
$$

$$
V_T = 0.025\ \text{V} \qquad (\text{thermal voltage at room temp.}) \tag{4}
$$

$$
\varepsilon_{Si} = 11.7 \times \varepsilon_0 = 11.7 \times 8.854 \times 10^{-12}\ \text{F/m} \qquad (\text{permittivity of Si}) \tag{5}
$$

$$
q = 1.6 \times 10^{-19}\ \text{C} \qquad (\text{charge of a single electron}) \tag{6}
$$

We have a formula for the built-in voltage ($\phi_j$), whose parameters are only $N_D$, $N_A$, $n_i$, and $V_T$.（我们有一个用于内建电压（$\phi_j$）的公式，其参数只有 $N_D$、$N_A$、$n_i$ 和 $V_T$。）

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

# 知识点笔记

## 第 1 章 能带与两种载流子

孤立原子的电子只能占据特定能级。把大量原子排成晶体后，这些能级分裂并连成一条条“能带”。

- **价带（$E_V$）**：价电子所在的、基本被填满的带。
- **导带（$E_C$）**：价带之上、基本为空的带。
- **禁带宽度** $E_g=E_C-E_V$：价带顶到导带底的能量间隙，硅约 1.12 eV。

按 $E_g$ 区分材料：金属的带重叠、没有禁带；半导体 $E_g$ 约 1–3 eV；绝缘体 $E_g$ 很大（>5 eV）。

**本征激发**：温度不为零时，少量价电子获得能量跳到导带，同时在价带留下一个空位。这个空位叫**空穴**，行为上像一个带正电的粒子。

- 每次激发同时产生一个电子和一个空穴，所以 $n=p$；
- 电子在导带中导电，空穴在价带中导电，两者都是载流子。

硅在 300 K 的三个常用数：$E_g\approx1.12$ eV；$E_C-E_i\approx0.56$ eV；$n_i\approx10^{10}$ cm⁻³。

## 第 2 章 本征半导体与质量作用定律

未掺杂的纯净半导体叫**本征半导体**，电子和空穴浓度都等于**本征载流子浓度** $n_i$：

$$n=p=n_i$$

$n_i$ 强烈依赖温度，大致按 $n_i\propto T^{3/2}e^{-E_g/2k_BT}$ 变化，温度升高则指数式增长。

**质量作用定律**（平衡态下永远成立）：

$$np=n_i^2$$

掺杂会改变 $n$ 和 $p$，但乘积不变：一边多了，另一边必然少了。

**电中性条件**：整块材料宏观上不带电，正电荷总数等于负电荷总数。这是后面所有掺杂近似的出发点。

## 第 3 章 掺杂半导体：n 型与 p 型

**施主（$N_D$）**：五价原子（如磷），在硅晶格中多出一个电子，室温下容易电离到导带，贡献电子，形成 **n 型**半导体。

**受主（$N_A$）**：三价原子（如硼），少一个电子，接受价电子后留下空穴，形成 **p 型**半导体。

做两个常用假设——室温下**全电离**，且掺杂浓度远大于 $n_i$（**非本征**）——则：

- n 型：$n\approx N_D-N_A\approx N_D$，少子 $p=n_i^2/n$；
- p 型：$p\approx N_A-N_D\approx N_A$，少子 $n=n_i^2/p$。

**多子与少子**：n 型中电子是多子、空穴是少子；p 型反之。

不省略时的电中性式：$n+N_A^-=p+N_D^+$。

例：$N_D=10^{16}$ cm⁻³ 的硅，$n\approx10^{16}$ cm⁻³，$p\approx(10^{10})^2/10^{16}=10^{4}$ cm⁻³。

## 第 4 章 载流子统计与费米能级

**费米-狄拉克分布**描述能量为 $E$ 的状态被电子占据的概率：

$$f(E)=\frac{1}{1+e^{(E-E_F)/k_BT}}$$

$E_F$ 叫**费米能级**，是占据概率为 1/2 的位置。

当 $E$ 比 $E_F$ 高几个 $k_BT$ 时，可近似为**玻尔兹曼近似**：$f(E)\approx e^{-(E-E_F)/k_BT}$。普通半导体通常处在这个非简并状态。

用**本征费米能级 $E_i$** 表达载流子浓度（本材料最常用的形式）：

$$n=n_i e^{(E_F-E_i)/k_BT},\qquad p=n_i e^{(E_i-E_F)/k_BT}$$

读法：$E_F$ 高于 $E_i$ 越多，电子越多（n 型）；$E_F$ 低于 $E_i$ 越多，空穴越多（p 型）。

反解得到**定位费米能级的公式**：

$$E_F-E_i=k_BT\ln\frac{n}{n_i},\qquad E_i-E_F=k_BT\ln\frac{p}{n_i}$$

把多子浓度代进去：

- n 型：$E_F-E_i=k_BT\ln(N_D/n_i)$，$E_F$ 在 $E_i$ 上方；
- p 型：$E_i-E_F=k_BT\ln(N_A/n_i)$，$E_F$ 在 $E_i$ 下方。

**平衡态下的费米能级**：同一块材料内部 $E_F$ 处处水平；两块材料接触达到平衡后，整体只有一个 $E_F$。这是画 PN 结能带图的基础。

**热能量与热电压**：$k_BT\approx0.026$ eV（300 K），热电压 $V_T=k_BT/q\approx0.025$ V。题目通常直接给出这两个数。

对应文件第 1 题：$p\approx N_A=10^{17}$，$E_i-E_F=0.026\ln10^7\approx0.42$ eV，即 $E_F$ 在 $E_i$ 下方 0.42 eV（原文最后一句写成“higher”，方向是反的）。

## 第 5 章 PN 结是怎么形成的

把 p 型和 n 型半导体做在一起，交界处叫**冶金结**。形成过程分四步：

1. **扩散**：n 侧电子多，向 p 侧扩散；p 侧空穴多，向 n 侧扩散。
2. **留下空间电荷**：多子扩散走后，留下未中和的施主离子（n 侧正电）和受主离子（p 侧负电），形成**空间电荷区**，也叫**耗尽区**（这里几乎没有自由载流子）。
3. **建立电场**：空间电荷产生从 n 指向 p 的内建电场。
4. **达到平衡**：电场把载流子往回拉（漂移），当漂移等于扩散时净电流为零，结进入平衡。

平衡时能带弯曲，两侧费米能级对齐，弯曲量就是 $qV_{bi}$：

$$qV_{bi}=E_{i,p}-E_{i,n}$$

把第 4 章的两个表达式代入，得到**内建电势**：

$$V_{bi}=\frac{k_BT}{q}\ln\frac{N_AN_D}{n_i^2}$$

这就是文件公式表里的公式 (4)。内建电势完全由掺杂浓度和温度决定，典型值 0.6–1 V（第 3 题算出 1.04 V）。

## 第 6 章 耗尽区的电场与电势：泊松方程

这一章是整份材料的计算核心，只需要一条方程——**泊松方程**：

$$\frac{d^2\phi}{dx^2}=-\frac{\rho}{\varepsilon_s}$$

**电荷密度**（用**耗尽近似**：耗尽区内无自由载流子、边界突变）：

- n 侧（$0<x<x_n$）：$\rho=+qN_D$；
- p 侧（$-x_p<x<0$）：$\rho=-qN_A$；
- 耗尽区外：$\rho=0$。

**积分一次得电场**：边界处电场为零，冶金结处最大，

$$E_{\max}=\frac{qN_Dx_n}{\varepsilon_s}=\frac{qN_Ax_p}{\varepsilon_s}$$

电场沿 $x$ 呈三角形分布，从冶金结向两侧线性减小到零。

**电荷中性**：两侧空间电荷总量相等，

$$N_Ax_p=N_Dx_n$$

含义是掺杂少的一侧必须更宽，才能凑出同样的电荷面密度。第 3 题 $N_A$ 比 $N_D$ 小 100 倍，$x_p$ 就是 $x_n$ 的 100 倍。

**再积分一次得电势**：电势差等于三角形面积，

$$V_{bi}=\frac12E_{\max}W$$

由此还得一个常用关系：$E_{\max}=\dfrac{2V_{bi}}{W}$。

## 第 7 章 PN 结的四个核心公式

联立 $W=x_p+x_n$ 与 $N_Ax_p=N_Dx_n$，可解出两侧宽度：

$$x_p=\frac{N_D}{N_A+N_D}W,\qquad x_n=\frac{N_A}{N_A+N_D}W$$

代回电势表达式，得到**耗尽宽度**：

$$W=\sqrt{\frac{2\varepsilon_s}{q}\left(\frac1{N_A}+\frac1{N_D}\right)V_{bi}}$$

于是四个常用结果：

1. 内建电势：$V_{bi}=\dfrac{k_BT}{q}\ln\dfrac{N_AN_D}{n_i^2}$；
2. 耗尽宽度：$W=\sqrt{\dfrac{2\varepsilon_s}{q}\left(\dfrac1{N_A}+\dfrac1{N_D}\right)V_{bi}}$；
3. 两侧分配：$x_p$、$x_n$ 与各自掺杂浓度成反比；
4. 最大电场：$E_{\max}=\dfrac{2V_{bi}}{W}$。

**单边突变结（$p^+n$ 或 $n^+p$）**：重掺杂一侧宽度可忽略，公式简化为

$$W\approx\sqrt{\frac{2\varepsilon_sV_{bi}}{qN_{\text{轻}}}}\qquad\text{即}\qquad\phi_i=\frac{qNX_d^2}{2\varepsilon_s}$$

这就是第 2 题单边肖特基结使用的形式。

文件第 3 题就是这个流程：$V_{bi}=1.04$ V → $W=0.0368$ µm → $E_{\max}=56.5$ V/µm → 按比例分出 $x_p$、$x_n$。

## 第 8 章 加偏置的 PN 结

- **正向偏置**（p 侧接正）：势垒降低到 $V_{bi}-V_F$，耗尽区变窄，电流显著增大。
- **反向偏置**（n 侧接正）：势垒升高到 $V_{bi}+V_R$，耗尽区变宽，只有很小漏电流。

**符号惯例**：文件约定 $V_R$ 正端接 n 侧，所以 $V_R>0$ 表示反偏。

公式只需把耗尽宽度中的 $V_{bi}$ 换成 $V_{bi}+V_R$：

$$W_d=W_{d0}\sqrt{1+\frac{V_R}{\phi_j}}$$

**实际用途是结电容**：

$$C_j=\frac{\varepsilon_sA}{W_d}\propto\frac{1}{\sqrt{V_R+V_{bi}}}$$

测量 $1/C_j^2$ 对 $V_R$ 作图得到直线，由斜率可反推掺杂浓度，这是器件表征的经典方法。

文件第 3 题：5 V 时 $W_d=0.0887$ µm，25 V 时 $0.184$ µm——反偏越大，耗尽区越宽。

## 第 9 章 金属-半导体接触：肖特基结

**功函数 $q\phi_M$**：把电子从金属费米能级搬到真空所需的能量。
**电子亲和势 $q\chi$**：把电子从半导体导带底搬到真空所需的能量。

金属与 n 型硅接触后，电子从费米能级高的一侧流向另一侧，形成空间电荷和内建电场，直到 $E_F$ 拉平、半导体能带弯曲，从而出现**肖特基势垒**。

理想 n 型肖特基势垒高度为 $q\phi_B=q\phi_M-q\chi$。半导体一侧的内建电势还要扣掉导带底到费米能级的距离：

$$q\phi_i=q\phi_M-q\chi-(E_C-E_F)$$

其中 $E_C-E_F=(E_C-E_i)-(E_F-E_i)=0.56\ \text{eV}-(E_F-E_i)$，而 $E_F-E_i$ 由第 4 章的掺杂公式给出。

接触不整流的叫**欧姆接触**，整流的叫**肖特基接触**。本题默认理想肖特基：无界面态、无氧化层、势垒与电压无关。

耗尽宽度用第 7 章末尾的单边结公式，掺杂取硅的 $N_D$。

文件第 2 题：$E_F-E_i=0.36$ eV → $E_C-E_F=0.20$ eV → $\phi_i=5.1-4.05-0.20=0.85$ V → $X_d\approx0.33$ µm。

## 第 10 章 单位、数量级与计算技巧

**单位换算**（下面三组最容易错）：

- $1\ \text{cm}^{-3}=10^{6}\ \text{m}^{-3}$，所以 $10^{16}$ cm⁻³ $=10^{22}$ m⁻³；
- $\varepsilon_0=8.854\times10^{-12}$ F/m $=8.854\times10^{-14}$ F/cm；
- 能量与电势差一个 $q$：$E[\text{eV}]=q\cdot\phi[\text{V}]$，公式里遇到比值要除以 $q$；
- $1\ \text{µm}=10^{-6}$ m。

**对数心算**：$\ln(10^n)\approx2.303n$。

- $\ln10^7=16.1$，$0.026\times16.1\approx0.42$ eV；
- $\ln10^6=13.8$，$0.026\times13.8\approx0.36$ eV；
- 第 3 题 $\ln10^{18}=41.4$，$0.025\times41.4\approx1.04$ V。

**数量级检查**：

- 硅的耗尽宽度典型在 0.03–1 µm，算出毫米级说明单位没换；
- 硅中最大电场典型在 10–100 V/µm；
- 轻掺杂一侧的耗尽区一定比重掺杂一侧宽。

## 第 11 章 学习顺序与自测

建议顺序：第 1–3 章（材料基础）→ 第 4 章（载流子统计）→ 第 5–7 章（PN 结静电学，最花时间）→ 第 8 章（偏置）→ 第 9 章（肖特基）→ 第 10 章（计算）。前四章没弄懂之前，不要急着看耗尽宽度的推导。

自测题（能口算出来就说明掌握了）：

1. $N_A=10^{16}$ cm⁻³ 的硅，$E_F$ 相对 $E_i$ 在哪里？
2. 为什么轻掺杂一侧的耗尽区更宽？
3. 反偏电压增大时，$W$、$E_{\max}$、$C_j$ 各如何变化？
4. $N_D=10^{15}$ cm⁻³ 换成 m⁻³ 是多少？
5. 理想肖特基势垒 $\phi_B$ 与金属功函数是什么关系？
6. 若 $\varepsilon$ 用 F/m 而 $N$ 用 cm⁻³，算出的 $W$ 会差几个数量级？