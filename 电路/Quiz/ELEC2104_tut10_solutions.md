# ELEC2104/9704 Tutorial 10 Solutions (2025)（教程 10 解答（2025））

---

In MOSFET problems, unless otherwise stated, assume $\mu_n C_{ox} = 200\ \mu\text{A/V}^2$, $\mu_p C_{ox} = 100\ \mu\text{A/V}^2$, $\lambda = 0$, and $V_{TN} = 0.4$ V and $V_{TP} = -0.4$ V.
（在 MOSFET 题目中，除另有说明外，均取 $\mu_nC_{ox}=200\ \mu\text{A/V}^2$、$\mu_pC_{ox}=100\ \mu\text{A/V}^2$、$\lambda=0$，以及 $V_{TN}=0.4$ V、$V_{TP}=-0.4$ V。）

> [!note] 全局参数约定
> 以上是整套题目的默认工艺参数。某题若另行给出 $\mu_nC_{ox}$、$\mu_pC_{ox}$、$V_{TN}$ 或 $V_{TP}$，则以该题给出的值为准（如第 1 题的 $250\ \mu\text{A/V}^2$、$V_{TN}=0.7$ V，第 4 题的 $40\ \mu\text{A/V}^2$、$V_{TP}=-0.75$ V）。

---

>回顾一下tu9中的公式

截止区**：$v_{GS}<V_{TN}$，没有沟道，$i_D=0$。

**可变电阻区**：$v_{GS}>V_{TN}$ 且 $v_{DS}<v_{GS}-V_{TN}$，沟道连续。当 $v_{DS}\ll2(v_{GS}-V_{TN})$ 时，$v_{DS}^2$ 项可忽略，电流与 $v_{DS}$ 成正比：

$$i_D=\mu_nC_{ox}\frac{W}{L}(v_{GS}-V_{TN})v_{DS}$$

此时器件等效为一个电阻：

$$R_{on}=\frac{1}{\mu_nC_{ox}\frac{W}{L}(v_{GS}-V_{TN})}$$

不作近似时的完整表达式：

$$i_D=\frac{1}{2}\mu_nC_{ox}\frac{W}{L}\left[2(v_{GS}-V_{TN})v_{DS}-v_{DS}^2\right]$$

**恒流区（饱和区）**：$v_{DS}\ge v_{GS}-V_{TN}$，漏端夹断：

$$i_D=\frac{1}{2}\mu_nC_{ox}\frac{W}{L}(v_{GS}-V_{TN})^2(1+\lambda v_{DS})$$

当 $\lambda=0$ 时，$i_D$ 与 $v_{DS}$ 无关，器件等效为电压控制电流源。

---

## 1 Question 1（第 1 题）

Calculate the transconductance for an NMOS transistor for $V_{GS} = 2$ V and $3.3$ V, with $V_{DS} = 3.3$ V, if $W = 20\ \mu\text{m}$, $L = 1\ \mu\text{m}$, $V_{TN} = 0.7$ V, and $\mu_n C_{ox} = 250\ \mu\text{A/V}^2$. Check the saturation region assumption.
（若 $W=20\ \mu\text{m}$、$L=1\ \mu\text{m}$、$V_{TN}=0.7$ V、$\mu_nC_{ox}=250\ \mu\text{A/V}^2$，求 NMOS 在 $V_{GS}=2$ V 与 $3.3$ V、$V_{DS}=3.3$ V 时的跨导。并检验饱和区假设。）

**Solution:**（**解答：**）

Given parameters:
（已知参数：）

$$
\mu_n C_{ox} = 250\ \mu\text{A/V}^2, \quad \frac{W}{L} = \frac{20\ \mu\text{m}}{1\ \mu\text{m}}, \quad V_{TN} = 0.7\ \text{V}, \quad V_{DS} = 3.3\ \text{V} \tag{1}
$$

We are to find the transconductance $g_m$ for two cases of $V_{GS}$.
（下面分别对两种 $V_{GS}$ 求跨导 $g_m$。）

**符号说明**：
- $g_m$：跨导，描述 $V_{GS}$ 对 $I_D$ 的控制能力，单位 S
- $\mu_nC_{ox}$：NMOS 的工艺导电因子
- $W/L$：沟道宽长比
- $V_{GS}-V_{TN}$：过驱动电压（overdrive voltage）
- $V_{TN}$：NMOS 阈值电压
- $V_{DS}$：漏源电压

> [!note] 饱和区判别式与跨导推导（NMOS）
> 器件导通需 $V_{GS}>V_{TN}$；工作于饱和区需 $V_{DS}>V_{GS}-V_{TN}$。
>
> 跨导定义为饱和区电流对 $V_{GS}$ 的偏导（固定 $V_{DS}$）：
>
> $$g_m=\frac{\partial I_D}{\partial V_{GS}}$$
>
> 代入饱和区电流
>
> $$I_D=\frac{1}{2}\mu_nC_{ox}\frac{W}{L}(V_{GS}-V_{TN})^2(1+\lambda V_{DS})$$
>
> 求导得
>
> $$g_m=\mu_nC_{ox}\frac{W}{L}(V_{GS}-V_{TN})(1+\lambda V_{DS})$$
>
> 本课程取 $\lambda=0$，于是
>
> $$g_m=\mu_nC_{ox}\frac{W}{L}(V_{GS}-V_{TN})=\sqrt{2\mu_nC_{ox}\frac{W}{L}I_D}=\frac{2I_D}{V_{GS}-V_{TN}}$$

---

**1) For $V_{GS} = 2$ V:**（**1）当 $V_{GS}=2$ V 时：**）

---

>判断工作区

Since $V_{GS} > V_{TN}$, the transistor is ON. The overdrive voltage is:
（由于 $V_{GS}>V_{TN}$，晶体管导通。过驱动电压为：）

$$
V_{GS} - V_{TN} = 2 - 0.7 = 1.3\ \text{V} \tag{2}
$$

Because
（因为）

$$
V_{DS} = 3.3\ \text{V} > V_{GS} - V_{TN} = 1.3\ \text{V} \tag{3}
$$

the transistor operates in the saturation region.
（晶体管工作在饱和区。）

---

>求$g_m$（$V_{GS}=2$ V）

The transconductance is given by:
（跨导由下式给出：）

$$
g_m = \mu_n C_{ox}\frac{W}{L}(V_{GS} - V_{TN}) \tag{4}
$$

Substituting the given values:
（代入给定值：）

$$
g_m = (250\ \mu\text{A/V}^2) \times \frac{20}{1} \times (2 - 0.7) \tag{5}
$$

Hence,
（因此，）

$$
g_m = 0.0065\ \text{S} = 6.5\ \text{mS} \tag{6}
$$

---

**2) For $V_{GS} = 3.3$ V:**（**2）当 $V_{GS}=3.3$ V 时：**）

---

>判断工作区

Similarly,
（同理，）

$$
V_{GS} - V_{TN} = 3.3 - 0.7 = 2.6\ \text{V} \tag{7}
$$

Since $V_{DS} = 3.3$ V $> 2.6$ V, the transistor remains in the saturation region.
（由于 $V_{DS}=3.3$ V $>2.6$ V，晶体管仍工作在饱和区。）

---

>求$g_m$（$V_{GS}=3.3$ V）

Now,
（于是，可以继续用饱和区的跨导公式）

$$
g_m = (250\ \mu\text{A/V}^2) \times \frac{20}{1} \times (3.3 - 0.7) \tag{8}
$$

Thus,
（因此，）

$$
g_m = 0.013\ \text{S} = 13\ \text{mS} \tag{9}
$$

---

>记录结果

**Conclusion:**（**结论：**）

- At $V_{GS} = 2$ V, the MOSFET operates in the saturation region with $g_m = 6.5$ mS.
  （当 $V_{GS}=2$ V 时，MOSFET 工作在饱和区，$g_m=6.5$ mS。）
- At $V_{GS} = 3.3$ V, it remains in the saturation region with $g_m = 13$ mS.
  （当 $V_{GS}=3.3$ V 时，仍工作在饱和区，$g_m=13$ mS。）

As expected, increasing $V_{GS}$ increases the overdrive voltage $(V_{GS} - V_{TN})$ and hence the transconductance $g_m$.
（如预期，增大 $V_{GS}$ 会增大过驱动电压 $(V_{GS}-V_{TN})$，从而增大跨导 $g_m$。）

> [!tip] 结论
> 饱和区中 $g_m$ 与过驱动电压成正比，因此 $V_{GS}$ 从 $2$ V 升到 $3.3$ V 时，$g_m$ 由 $6.5$ mS 翻倍到 $13$ mS（过驱动电压恰好翻倍）。

> [!note] 增大 $g_m$ 意味着什么
> 直接理解：$g_m=\dfrac{\Delta I_D}{\Delta V_{GS}}$。$g_m$ 越大，**同样的输入电压变化能产生更大的电流变化**。
>
> - 对放大器：同样的 $v_{gs}$ 得到更大的 $i_d=g_mv_{gs}$，再乘上负载就是更大的输出电压，所以增益更高。
> - 对带电容的节点：同样的 $v_{gs}$ 能提供更大的充放电电流，所以速度更快。
> - 代价：要得到更大的 $g_m$，只能提高过驱动 $V_{OV}=V_{GS}-V_{TN}$ 或加大 $W/L$。


---

## 2 Question 2（第 2 题）

(a) Find the Q-point for the transistor in the circuit in Fig. P4.111(a) if $V_{DD} = +12$ V.
（(a) 若 $V_{DD}=+12$ V，求图 P4.111(a) 中晶体管的 Q 点。）

(b) Repeat for the circuit in Fig. P4.111(b).
（(b) 对图 P4.111(b) 的电路重做。）

![](Pasted%20image%2020261117153917.png)
> 图Q2-1 Fig. P4.111：(a) 自偏置 NMOS，漏极经 $100$ k$\Omega$ 接 $V_{DD}$，栅极与漏极短接，源极接地，$W/L = 20/1$；(b) 漏极经 $330$ k$\Omega$ 接 $V_{DD}$，栅极与漏极之间接 $10$ M$\Omega$，源极接地，$W/L = 20/1$

**Solution:**（**解答：**）

**符号说明**：
- $V_{DD}$：电源电压
- $V_G$、$V_D$：栅极、漏极对地电压
- $I_D$：漏极电流
- $V_{GS}=V_G-V_S$：栅源电压（源极接地时 $V_S=0$）
- $V_{DS}=V_D-V_S$：漏源电压
- Q 点：静态工作点 $(I_D, V_{DS})$

### 2.1 Part A（A 部分）

Given the gate and the drain are connected,
（已知栅极与漏极相连，）

$$
V_G = V_D \Rightarrow V_{GS} = V_{DS}
$$

---

>判断工作区

To ensure saturation, the condition is:
（为确保工作在饱和区，条件为：）

$$
V_{GS} - V_{TN} < V_{DS} \tag{1}
$$

Assume $V_{GS} > V_{TN}$ so that the NMOS is in the **saturation region**.

>由于$V_G = V_D \Rightarrow V_{GS} = V_{DS}$，只要$V_{GS}$大于$V_{TN}$就一定满足饱和区的条件，使 NMOS 工作在**饱和区**

For the given circuit,
（对给定电路，）

$$
V_{GS} = V_{DD} - I_D(100\ \text{k}\Omega) \tag{2}
$$

and
（以及）

$$
I_D = \frac{1}{2}\mu_n C_{ox}\frac{W}{L}(V_{GS} - V_{TN})^2 \tag{3}
$$

---

>求$V_{GS}$

Substituting $V_{DD} = 12$ V, $\mu_n C_{ox} = 200\ \mu\text{A/V}^2$, $W/L = 20$, and $V_{TN} = 0.4$ V:
（代入 $V_{DD}=12$ V、$\mu_nC_{ox}=200\ \mu\text{A/V}^2$、$W/L=20$、$V_{TN}=0.4$ V：）

$$
V_{GS} = 12 - 100000 I_D \tag{4}
$$

Substitute into Eq. (3):
（代入式 (3)：）

$$
I_D = \frac{1}{2}(200\ \mu)(20)(V_{GS} - 0.4)^2 \tag{5}
$$

Simplifying:
（化简得：）

$$
200V_{GS}^2 - 159V_{GS} + 20 = 0 \tag{6}
$$

Solving Eq. (6) for $V_{GS}$ gives:
（解式 (6) 求 $V_{GS}$，得：）

$$
V_{GS1} = 0.64\ \text{V}, \quad V_{GS2} = 0.15\ \text{V} \tag{7}
$$

Since $V_{GS2} < V_{TN}$, that solution is invalid (transistor OFF). Hence, $V_{GS} = 0.64$ V.
（由于 $V_{GS2}<V_{TN}$，该解无效（晶体管截止）。故取 $V_{GS}=0.64$ V。）

> [!warning] 二次方程两个根的取舍
> 二极管连接（栅漏短接）本质上是二次方程，通常有两个数学解；只有满足 $V_{GS}>V_{TN}$ 的根对应器件导通。本题 $V_{GS2}=0.15\ \text{V}<0.4\ \text{V}$，应舍去。

---

>求$I_D$

Now calculate the drain current:
（现在计算漏极电流：）

$$
I_D = \frac{1}{2}(200\ \mu)(20)(0.64 - 0.4)^2 = 0.11\ \text{mA} \tag{8}
$$

---

>验证饱和区

The drain-source voltage is:
（漏源电压为：）

$$
V_{DS} = V_{GS} = 0.64\ \text{V} \tag{9}
$$

Since $V_{GS} - V_{TN} = 0.24$ V $< V_{DS}$, the device is indeed in saturation.
（由于 $V_{GS}-V_{TN}=0.24$ V $<V_{DS}$，器件确实工作在饱和区。）

---

>记录Q点

**Q-point:** $(I_D, V_{DS}) = (0.11\ \text{mA}, 0.64\ \text{V})$
（**Q 点：** $(I_D, V_{DS}) = (0.11\ \text{mA}, 0.64\ \text{V})$）

---

### 2.2 Part B（B 部分）

Since no current enters the gate,
（由于栅极无电流流入，）

$$
I_G = 0 \tag{10}
$$

Therefore, there is no voltage drop between the gate and the drain.
（因此栅极与漏极之间没有电压降。）

$$
V_D = V_G \Rightarrow V_{DS} = V_{GS} \tag{11}
$$

---

>判断工作区

To ensure saturation:
（为确保饱和：）

$$
V_{GS} - V_{TN} < V_{DS} \tag{12}
$$

Assume $V_{GS} > V_{TN}$ so that the NMOS is operating in the saturation region. The circuit relationship is:
（假设 $V_{GS}>V_{TN}$，使 NMOS 工作在饱和区。电路关系为：）

$$
V_{GS} = 12 - 320000 I_D \tag{13}
$$

The drain current in saturation is given by:
（饱和区漏极电流为：）

$$
I_D = \frac{1}{2}(200\ \mu\text{A/V}^2)\frac{20}{1}(V_{GS} - 0.4)^2 \tag{14}
$$

---

>求$V_{GS}$

Substituting Eq. (13) into Eq. (14), we obtain:
（把式 (13) 代入式 (14)，得：）

$$
660V_{GS}^2 - 527V_{GS} + 93.6 = 0 \tag{15}
$$

Solving Eq. (15):
（解式 (15)：）

$$
V_{GS1} = 0.53\ \text{V}, \quad V_{GS2} = 0.26\ \text{V} \tag{16}
$$

For $V_{GS2} = 0.26$ V, $V_{GS} < V_{TN}$, hence transistor is OFF. Thus, valid solution is:
（对 $V_{GS2}=0.26$ V，有 $V_{GS}<V_{TN}$，故晶体管截止。因此有效解为：）

$$
V_{GS} = V_{DS} = 0.53\ \text{V} \tag{17}
$$

---

>求$I_D$

Now calculate the drain current:
（现在计算漏极电流：）

$$
I_D = \frac{1}{2}(200\ \mu)(20)(0.53 - 0.4)^2 = 0.035\ \text{mA} \tag{18}
$$

---

>验证饱和区

Check for saturation:
（检验饱和区：）

$$
V_{GS} - V_{TN} = 0.13\ \text{V} < V_{DS} = 0.53\ \text{V} \Rightarrow \text{Saturation region confirmed.} \tag{19}
$$

---

>记录Q点

Hence, the operating point (Q-point) is:
（因此，工作点（Q 点）为：）

$$
\text{Q-point: } (I_D, V_{DS}) = (0.035\ \text{mA}, 0.53\ \text{V}) \tag{20}
$$

---

## 3 Question 3（第 3 题）

Find the current $I$ in Fig. P4.135 assuming that $\gamma = 0$ and $W/L = 40/1$ for each transistor.
（设 $\gamma=0$、每个晶体管 $W/L=40/1$，求图 P4.135 中的电流 $I$。）

![](Pasted%20image%2020261117153941.png)
> 图Q3-1 Fig. P4.135：三个相同 MOSFET 串联于 $+15$ V 与地之间，各管栅极与自身漏极短接（二极管连接），电流 $I$ 自上而下

**Solution:**（**解答：**）

The three MOSFETs in the circuit are connected in series. We can simplify the circuit diagram as below.
（电路中三个 MOSFET 串联，可将电路图化简如下。）

![](Pasted%20image%2020261117153958.png)
> 图Q3-2 原书手绘化简图：$15$ V 自上而下依次串联 $M_1$、$M_2$、$M_3$，下端接地

Given $\gamma = 0$, there is no body effect.
（由于 $\gamma=0$，不存在体效应。）

**Analysis:**（**分析：**）

**符号说明**：
- $V_{TP}$：PMOS 阈值电压（负值）
- $\mu_pC_{ox}$：PMOS 的工艺导电因子
- $\gamma$：体效应参数（$\gamma=0$ 表示无体效应）
- $I_{D1}$、$I_{D2}$、$I_{D3}$：三个管各自的漏极电流

---

>判断工作区

Since all three PMOS transistors are identical:
（由于三个 PMOS 晶体管完全相同：）

$$
V_{GS} = -\left(\frac{15}{3}\right) = -5\ \text{V} \tag{1}
$$

Because they are connected in series:
（因为它们串联：）

$$
I_{D1} = I_{D2} = I_{D3} = I_D \tag{2}
$$

> [!note] 为什么每个管子分到 $5$ V
> 三个相同的二极管连接 PMOS 串联，$15$ V 平均分配在三个栅源结上，故每管 $|V_{GS}|=5$ V、$V_{GS}=-5$ V；又因串联，各管电流相同。

---

>求$I_D$

The drain current for each PMOS in saturation is:
（每个 PMOS 在饱和区的漏极电流为：）

$$
I_D = \frac{1}{2}\mu_p C_{ox}\frac{W}{L}(V_{GS} - V_{TP})^2 \tag{3}
$$

Substitute the given values:
（代入给定值：）

$$
I_D = \frac{1}{2}(100\ \mu\text{A/V}^2)\frac{40}{1}[(-5) - (-0.4)]^2 \tag{4}
$$

Simplifying:
（化简得：）

$$
I_D = 0.042\ \text{A} \tag{5}
$$

---

>记录结果

**Conclusion:**（**结论：**）

Each PMOS device carries a drain current of
（每个 PMOS 器件的漏极电流为）

$$
I_D = 42\ \text{mA} \tag{6}
$$

under the assumption of $\gamma = 0$ (no body effect) and identical transistors connected in series.
（这是在 $\gamma=0$（无体效应）且各管相同、串联的条件下得到的。）

---

## 4 Question 4（第 4 题）

(a) Find the Q-point for the transistor in Fig. P4.138 if $R = 50$ k$\Omega$. Assume that $\gamma = 0$ and $W/L = 20/1$.
（(a) 若 $R=50$ k$\Omega$，设 $\gamma=0$、$W/L=20/1$，求图 P4.138 中晶体管的 Q 点。）

(b) What is the permissible range of values for $R$ if the transistor is to remain in the saturation region?
（(b) 若晶体管要保持工作在饱和区，$R$ 的允许取值范围是多少？）

![](Pasted%20image%2020261117154011.png)
> 图Q4-1 Fig. P4.138：PMOS 电路，$+15$ V 经 $100$ k$\Omega$ 接源极，漏极经 $R$ 接地；栅极由 $510$ k$\Omega$（上）与 $510$ k$\Omega$（下）分压取得

**Solution:**（**解答：**）

For a four-resistor-biased circuit, we need to convert the gate part into the Thevenin equivalent.
（对四电阻偏置电路，需要把栅极部分化为戴维南等效。）

![](Pasted%20image%2020261117154024.png)
> 图Q4-2 原书手绘 Q4 Thevenin equivalent circuit diagram：$15$ V 经 $100$ K 接 PMOS 源极 $S$，漏极 $D$ 经 $R$ 接地；栅极经 $R_{eq}$ 接 $V_{th}$ 等效源到地，旁注 "pmos"

**符号说明**：
- $V_{th}$：栅极分压网络的戴维南等效电压（本题 $V_{th}=7.5$ V）
- $R_{eq}$：栅极分压网络的戴维南等效电阻
- $V_S$、$V_D$、$V_G$：源极、漏极、栅极对地电压
- $V_{GS}=V_G-V_S$：栅源电压
- $V_{DS}=V_D-V_S$：漏源电压（PMOS 中通常为负）
- $V_{TP}$：PMOS 阈值电压（负值）

> [!warning] 本题沿用原解参数
> 原解使用 $\mu_pC_{ox}=40\ \mu\text{A/V}^2$、$V_{TP}=-0.75$ V，与卷首统一假设（$100\ \mu\text{A/V}^2$、$-0.4$ V）不同。为保持与原书解答一致，以下计算全部沿用原解参数。

### 4.1 Part A（A 部分）

We start by assuming that the PMOS transistor is operating in the saturation region.
（首先假设 PMOS 晶体管工作在饱和区。）

---

>列方程（饱和区假设）

The gate-source voltage is determined by the biasing network:
（栅源电压由偏置网络确定：）

$$
V_{th} = 15 - I_D(100\ \text{k}\Omega) + V_{GS} \tag{1}
$$

The drain current equation in the saturation region is:
（饱和区漏极电流方程为：）

$$
I_D = \frac{1}{2}(40\ \mu\text{A/V}^2)\frac{20}{1}(V_{GS} - (-0.75))^2 \tag{2}
$$

---

>求$V_{GS}$、$I_D$

Solving Eq. (1) and Eq. (2) simultaneously gives:
（联立式 (1) 与式 (2) 求解，得：）

$$
V_{GS} = -1.15\ \text{V} \tag{3}
$$

$$
I_D = 63.5\ \mu\text{A} \tag{4}
$$

---

>验证饱和区

To verify that the device indeed operates in the saturation region, we calculate voltages at each terminal.
（为验证器件确实工作在饱和区，计算各端电压。）

The source voltage is:
（源极电压为：）

$$
V_S = V_G - V_{GS} = 7.5 - (-1.15) = 8.65\ \text{V} \tag{5}
$$

The drain voltage is obtained from the drain resistor:
（漏极电压由漏极电阻求得：）

$$
V_D = I_D R = (63.5\ \mu\text{A})(50\ \text{k}\Omega) = 3.175\ \text{V} \tag{6}
$$

Thus,
（于是，）

$$
V_{DS} = V_D - V_S = 3.175 - 8.65 = -5.48\ \text{V} \tag{7}
$$

For a PMOS in saturation:
（PMOS 处于饱和区时应满足：）

$$
V_{DS} < V_{GS} - V_{TP} \tag{8}
$$

Substituting:
（代入：）

$$
-5.48 < -1.15 - (-0.75) = -0.4
$$

which satisfies the condition, confirming that the PMOS operates in the **saturation region**.
（条件成立，确认 PMOS 工作在**饱和区**。）

---

>记录Q点

Therefore, the Q-point is:
（因此，Q 点为：）

$$
\text{Q-point: } (I_D, V_{DS}) = (63.5\ \mu\text{A}, -5.48\ \text{V}) \tag{9}
$$

---

### 4.2 Part B（B 部分）

For the transistor to remain in saturation, we must have:
（要使晶体管保持饱和，必须满足：）

$$
V_{DS} \leq V_{GS} - V_{TP} \tag{10}
$$

---

>求$R$的取值范围

Substitute expressions for $V_{DS}$ and $V_{GS}$:
（代入 $V_{DS}$ 与 $V_{GS}$ 的表达式：）

$$
-[15 - (100\ \text{k}\Omega + R)I_D] \leq V_{GS} - V_{TP} \tag{11}
$$

Substitute numerical values:
（代入数值：）

$$
-[15 - (100\ \text{k}\Omega + R)(63.5\ \mu\text{A})] \leq -1.15 - (-0.75) \tag{12}
$$

Simplifying:
（化简得：）

$$
R \leq 129.72\ \text{k}\Omega \tag{13}
$$

> [!tip] 结果解读
> $R$ 越小，漏极电位越低、$|V_{DS}|$ 越大，越容易保持饱和；$R$ 超过上限后，PMOS 会进入三极管区（可变电阻区）。

---

## 5 Question 5（第 5 题）

The self-biased stage in Fig. 1 must be designed for a drain current of 1 mA. If $M_1$ is to provide a transconductance of $1/(100\ \Omega)$, calculate the required value of $R_D$.
（图 1 的自偏置级需设计为漏极电流 $1$ mA。若要求 $M_1$ 的跨导为 $1/(100\ \Omega)$，求所需的 $R_D$。）

![](Pasted%20image%2020261117154053.png)
> 图1 Q4 circuit diagram：自偏置 NMOS $M_1$，$V_{DD} = 1.8$ V 经 $R_D$ 接漏极，$R_G$ 跨接于栅极与漏极之间，源极接地

**Solution:**（**解答：**）

**符号说明**：
- $g_m$：跨导，本题要求 $g_m=1/(100\ \Omega)=10$ mS
- $I_D$：漏极电流，要求 $1$ mA
- $V_{GS}$：栅源电压
- $V_{TN}$：NMOS 阈值电压，取 $0.4$ V
- $R_D$：漏极电阻

The transistor operates in the saturation region where $V_{DS} = V_{GS}$. By designing the circuit to achieve the desired $g_m$ with $I_D = 1$ mA and $V_{TN} = 0.4$ V, we can solve for the gate-source voltage $V_{GS}$ and then determine the required drain resistor $R_D$.
（晶体管工作在饱和区，且 $V_{DS}=V_{GS}$。按 $I_D=1$ mA、$V_{TN}=0.4$ V 设计出所需 $g_m$，即可解出栅源电压 $V_{GS}$，再确定所需漏极电阻 $R_D$。）

> [!note] 自偏置级的两个约束
> 栅漏经 $R_G$ 相连且栅极无电流，故 $V_G=V_D$，于是 $V_{DS}=V_{GS}$；饱和区要求 $V_{GS}>V_{TN}$ 且 $V_{DS}>V_{GS}-V_{TN}$，在 $V_{DS}=V_{GS}$ 时后者自动满足（只要 $V_{TN}>0$）。

---

>求$V_{GS}$

The transconductance is defined as:
（跨导定义为：）

$$
g_m = \frac{2I_D}{V_{GS} - V_{TN}} \tag{1}
$$

Substitute the given values $I_D = 1$ mA and $V_{TN} = 0.4$ V:
（代入给定值 $I_D=1$ mA、$V_{TN}=0.4$ V：）

$$
g_m = \frac{2 \times 0.001}{V_{GS} - 0.4} = \frac{1}{100} \tag{2}
$$

Solving for $V_{GS}$:
（解出 $V_{GS}$：）

$$
V_{GS} = 0.6\ \text{V} \tag{3}
$$

---

>求$R_D$

Since in saturation $V_{DS} = V_{GS}$, we have:
（由于饱和区中 $V_{DS}=V_{GS}$，有：）

$$
V_{DD} - I_D R_D = V_{DS} = V_{GS} \tag{4}
$$

Substitute $V_{DD} = 1.8$ V, $I_D = 1$ mA, and $V_{GS} = 0.6$ V:
（代入 $V_{DD}=1.8$ V、$I_D=1$ mA、$V_{GS}=0.6$ V：）

$$
1.8 - (0.001)R_D = 0.6 \tag{5}
$$

Hence, the required drain resistance is:
（因此，所需漏极电阻为：）

$$
R_D = 1.2\ \text{k}\Omega \tag{6}
$$

---
