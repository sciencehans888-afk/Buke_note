# ELEC2104/9704 Tutorial 5 Solutions (2025)

## 1 Question 1（第 1 题）

Find the Q-point for the diode in the figure below using（用下图中的电路求二极管的 Q 点，分别采用：）

- (a) the ideal diode model,（理想二极管模型；）
- (b) the constant voltage drop model with $V_{on} = 0.6$ V,（导通电压 $V_{on}=0.6$ V 的恒压降模型；）
- (c) Discuss the results. Which answer do you feel is most correct?,（讨论这些结果。你认为哪个答案最正确？）
- (d) Use iterative analysis to find the actual Q-point if $I_S = 1$ fA and assume thermal voltage is 25 mV.（若 $I_S=1$ fA、热电压取 25 mV，用迭代分析法求实际的 Q 点。）

![](Pasted%20image%2020261110222106.png)
> 图1 Q1 circuit diagram（图 1：Q1 电路图）

Solution:（**解答：**）

First, let's simplify the circuit using Thévenin equivalent.（首先，我们用戴维南等效化简电路。） We'll apply the Thévenin theorem to both the left and right sides of the diode separately.（对二极管的左侧和右侧分别应用戴维南定理。）

**Thévenin's theorem（戴维南定理）**：任何线性含源二端网络，对外电路而言，都可以等效为一个电压源 $V_{th}$ 与一个电阻 $R_{th}$ 串联。（任何线性含源二端网络，对外电路而言，都可以等效为一个电压源 $V_{th}$ 与一个电阻 $R_{th}$ 串联。）

- **$V_{th}$（开路电压，open-circuit voltage）**：把外电路断开（端口开路）时，端口两端的电压；
- **$R_{th}$（戴维南电阻，Thévenin resistance）**：把网络内所有独立源置零（电压源短路、电流源开路）后，从端口看进去的等效电阻。

也可以由开路电压 $V_{oc}$ 与短路电流 $I_{sc}$ 求出：

$$
V_{th}=V_{oc},\qquad R_{th}=\frac{V_{oc}}{I_{sc}}
$$

注意：戴维南等效只保证**对外端口**的 $V$–$I$ 关系相同，等效电路内部的功率、电流分布与原电路并不相同。

**Step 1: Identify the portions to simplify**（第 1 步：确定需要化简的部分）

We'll find the Thévenin equivalent for the circuit to the left of the diode (looking from point $V_A$) and to the right of the diode (looking from point $V_B$).（求二极管左侧（从 $V_A$ 看进去）和右侧（从 $V_B$ 看进去）电路的戴维南等效。）

![](Pasted%20image%2020261110222120.png)
> 图2 Original circuit with sections to be replaced by Thévenin equivalents（图 2：原始电路，其中两段将用戴维南等效替代）

**Step 2: Finding Thévenin Equivalent for Left Side**（第 2 步：求左侧的戴维南等效）

To find the Thévenin equivalent for the left side (looking from point $V_A$):（求左侧（从 $V_A$ 看进去）的戴维南等效：）

**2a. Find $V_{th,left}$ (Open-circuit voltage at $V_A$):**（2a. 求 $V_{th,left}$（$V_A$ 处的开路电压）：）

Remove the diode (open circuit) and find the voltage at $V_A$ using voltage divider:（移去二极管（开路），用分压求 $V_A$ 处的电压：）

![](Pasted%20image%2020261110222137.png)
> 图3 Finding $V_{th,left}$ - voltage divider with 2 k$\Omega$ and 3 k$\Omega$（图 3：用 2 kΩ 与 3 kΩ 分压求 $V_{th,left}$）

Using voltage divider: $V_{th,left} = 3\ \mathrm{V} \times \dfrac{2\ \mathrm{k\Omega}}{3\ \mathrm{k\Omega}+2\ \mathrm{k\Omega}} = 3 \times \dfrac{2}{5} = 1.2\ \mathrm{V}$.（用分压公式：$V_{th,left} = 3\ \mathrm{V} \times \dfrac{2\ \mathrm{k\Omega}}{3\ \mathrm{k\Omega}+2\ \mathrm{k\Omega}} = 3 \times \dfrac{2}{5} = 1.2\ \mathrm{V}$。）

**2b. Find $R_{th,left}$ (Thévenin resistance looking into $V_A$):**（2b. 求 $R_{th,left}$（从 $V_A$ 看进去的戴维南电阻）：）

Replace voltage source with short circuit and find equivalent resistance:（把电压源置零（短路），求等效电阻：）

![](Pasted%20image%2020261110222149.png)
> 图4 Finding $R_{th,left} = 2$ k$\Omega \parallel 3$ k$\Omega$（图 4：求 $R_{th,left} = 2$ kΩ $\parallel 3$ kΩ）

When the voltage source is shorted, the top and bottom rails are at the same potential (both connected to ground through the short).（电压源短路后，上下两条导轨电位相同（都通过短路线接地）。） This means the $2$ k$\Omega$ and $3$ k$\Omega$ resistors are in parallel.（这意味着 2 kΩ 与 3 kΩ 电阻并联。） We can redraw this more clearly:（可以更清楚地重画如下：）

![](Pasted%20image%2020261110222210.png)
> 图5 Equivalent parallel resistor configuration after shorting the voltage source（图 5：电压源短路后的等效并联电阻结构）

$$
R_{th,left} = 2\ \mathrm{k\Omega} \parallel 3\ \mathrm{k\Omega} = \frac{2 \times 3}{2+3}\ \mathrm{k\Omega} = 1.2\ \mathrm{k\Omega}
$$

**Step 3: Finding Thévenin Equivalent for Right Side**（第 3 步：求右侧的戴维南等效）

Similarly for the right side (looking from point $V_B$):（右侧同理（从 $V_B$ 看进去）：）

**3a. Find $V_{th,right}$ (Open-circuit voltage at $V_B$):**（3a. 求 $V_{th,right}$（$V_B$ 处的开路电压）：）

![](Pasted%20image%2020261110222225.png)
> 图6 Finding $V_{th,right}$ - voltage divider with equal resistors（图 6：用两个相等电阻分压求 $V_{th,right}$）

Using voltage divider: $V_{th,right} = 3\ \mathrm{V} \times \dfrac{2\ \mathrm{k\Omega}}{2\ \mathrm{k\Omega}+2\ \mathrm{k\Omega}} = 3 \times \dfrac{1}{2} = 1.5\ \mathrm{V}$（用分压公式：$V_{th,right} = 3\ \mathrm{V} \times \dfrac{2\ \mathrm{k\Omega}}{2\ \mathrm{k\Omega}+2\ \mathrm{k\Omega}} = 3 \times \dfrac{1}{2} = 1.5\ \mathrm{V}$）

**3b. Find $R_{th,right}$ (Thévenin resistance looking into $V_B$):**（3b. 求 $R_{th,right}$（从 $V_B$ 看进去的戴维南电阻）：）

![](Pasted%20image%2020261110222235.png)
> 图7 Finding $R_{th,right} = 2$ k$\Omega \parallel 2$ k$\Omega$（图 7：求 $R_{th,right} = 2$ kΩ $\parallel 2$ kΩ）

When the voltage source is shorted, the top and bottom rails are at the same potential.（电压源短路后，上下两条导轨电位相同。） The two $2$ k$\Omega$ resistors are in parallel.（两个 2 kΩ 电阻并联。） We can redraw this more clearly:（可以更清楚地重画如下：）

![](Pasted%20image%2020261110222246.png)
> 图8 Equivalent parallel resistor configuration after shorting the voltage source（图 8：电压源短路后的等效并联电阻结构）

$$
R_{th,right} = 2\ \mathrm{k\Omega} \parallel 2\ \mathrm{k\Omega} = \frac{2 \times 2}{2+2}\ \mathrm{k\Omega} = 1\ \mathrm{k\Omega}
$$

**Step 4: First Simplified Circuit with Both Thévenin Equivalents**（第 4 步：两侧都换成戴维南等效后的第一次化简电路）

Now we can replace both sides with their Thévenin equivalents:（现在把两侧都替换为各自的戴维南等效：）

![](Pasted%20image%2020261110222300.png)
> 图9 Circuit with Thévenin equivalents on both sides（图 9：两侧均为戴维南等效的电路）

Where the values of the Thévenin voltage sources and the resistors come from the previous steps:（其中戴维南电压源和电阻的数值来自前面的步骤：）

$$
V_{th,left} = 3\ \mathrm{V} \times \frac{2\ \mathrm{k\Omega}}{3\ \mathrm{k\Omega}+2\ \mathrm{k\Omega}} = 1.2\ \mathrm{V} \tag{1}
$$

$$
V_{th,right} = 3\ \mathrm{V} \times \frac{2\ \mathrm{k\Omega}}{2\ \mathrm{k\Omega}+2\ \mathrm{k\Omega}} = 1.5\ \mathrm{V} \tag{2}
$$

$$
R_{th,left} = 2\ \mathrm{k\Omega} \parallel 3\ \mathrm{k\Omega} = 1.2\ \mathrm{k\Omega} \tag{3}
$$

$$
R_{th,right} = 2\ \mathrm{k\Omega} \parallel 2\ \mathrm{k\Omega} = 1\ \mathrm{k\Omega} \tag{4}
$$

**Step 5: Further Simplification - Combining Sources and Resistors**（第 5 步：进一步化简——合并电源与电阻）

We can further simplify by combining the voltage sources and resistors in series:（可以把电压源与电阻串联合并，进一步化简：）

![](Pasted%20image%2020261110222311.png)
> 图10 Final simplified circuit with combined Thévenin equivalent（图 10：合并戴维南等效后的最终化简电路）

The parameters are determined as:（参数确定为：）

$$
V_{th} = V_{th,right} - V_{th,left} = 0.3\ \mathrm{V} \tag{5}
$$

$$
R_{th} = R_{th,left} + R_{th,right} = 2.2\ \mathrm{k\Omega} \tag{6}
$$

### 1.1 Part A: Ideal Diode Model（A 部分：理想二极管模型）

**Rules in Ideal Diode Models:**（理想二极管模型的规则：）

$$
\begin{cases}
\text{ON: Diode in forward bias } (I_D > 0,\ V_D = 0) &:\ \ \text{diode} \approx \text{short circuit}, \\
\text{OFF: Diode in reverse bias } (I_D = 0,\ V_D < 0) &:\ \ \text{diode} \approx \text{open circuit}.
\end{cases}
$$

![](Pasted%20image%2020261110222323.png)
> 图11 Thévenin equivalent circuit（图 11：戴维南等效电路）

By inspecting the Thévenin equivalent circuit found in the steps above (see Figure 11), we can see that the voltage source tries to forward bias the diode (positive terminal connected to anode).（观察上面求得的戴维南等效电路（见图 11），可知电压源试图使二极管正向偏置（正端接阳极）。） Since this would result in forward current, we assume that the diode is ON.（由于这会产生正向电流，我们假设二极管导通（ON）。）

When the diode is ON in the ideal diode model, it acts as a short circuit ($V_D = 0$).（理想二极管模型中，二极管导通时相当于短路（$V_D = 0$）。） We can redraw the circuit with this assumption:（按此假设重画电路：）

![](Pasted%20image%2020261110222332.png)
> 图12 Thévenin equivalent circuit with ideal diode ON (shorted)（图 12：理想二极管导通（短路）时的戴维南等效电路）

Now we can calculate the current through the circuit using Ohm's law:（现在用欧姆定律计算电路中的电流：）

$$
I_D = \frac{V_{th}}{R_{th}} = \frac{0.3\ \mathrm{V}}{2.2\ \mathrm{k\Omega}} = 0.136\ \mathrm{mA} \tag{7}
$$

Since $I_D > 0$, our assumption that the diode is ON is correct.（由于 $I_D > 0$，假设二极管导通是正确的。） Therefore, the Q-point is:（因此 Q 点为：）

$$
(I_D, V_D) = (0.136\ \mathrm{mA},\ 0\ \mathrm{V}) \tag{8}
$$

### 1.2 Part B: Constant Voltage Drop Model（B 部分：恒压降模型）

**Rules in Constant Voltage Drop Model:**（恒压降模型的规则：）

$$
\begin{cases}
\text{ON: If } V_D \geq V_{D,on} &:\ \ V_D = V_{D,on},\ I_D > 0 \\
\text{OFF: If } V_D < V_{D,on} &:\ \ V_D < V_{D,on},\ I_D = 0
\end{cases}
$$

where $V_{D,on} = 0.6$ V is the turn-on voltage.（其中 $V_{D,on} = 0.6$ V 为导通电压。）

![](Pasted%20image%2020261110222345.png)
> 图13 Thévenin equivalent circuit for constant voltage drop analysis（图 13：恒压降分析用的戴维南等效电路）

To determine if the diode is ON or OFF, we use the "assume and verify" approach.（判断二极管导通还是截止，采用“假设—验证”法。） Since the available voltage (0.3V) is less than the turn-on voltage (0.6V), we start by assuming the diode is OFF.（由于可用电压（0.3 V）小于导通电压（0.6 V），先假设二极管截止。）

When the diode is OFF (open circuit), no current flows through the circuit, so the voltage across the diode equals the full Thévenin voltage:（二极管截止（开路）时电路中无电流，所以二极管两端电压等于完整的戴维南电压：）

![](Pasted%20image%2020261110222357.png)
> 图14 Circuit assuming diode is OFF (open circuit)（图 14：假设二极管截止（开路）时的电路）

Since $I_D = 0$ A (diode is OFF), by Ohm's law, the voltage drop across the resistor is:（由于 $I_D = 0$ A（二极管截止），由欧姆定律，电阻上的压降为：）

$$
V_R = I_D \times R_{th} = 0\ \mathrm{A} \times 2.2\ \mathrm{k\Omega} = 0\ \mathrm{V} \tag{9}
$$

Therefore: $V_D = V_{th} - V_R = 0.3\ \mathrm{V} - 0\ \mathrm{V} = 0.3\ \mathrm{V}$.（因此：$V_D = V_{th} - V_R = 0.3\ \mathrm{V} - 0\ \mathrm{V} = 0.3\ \mathrm{V}$。）
So, when the diode is OFF, we have $V_D = V_{th} = 0.3\ \mathrm{V}$.（所以二极管截止时 $V_D = V_{th} = 0.3\ \mathrm{V}$。）

Since $V_D = 0.3\ \mathrm{V} < V_{D,on} = 0.6\ \mathrm{V}$, our assumption is correct: the diode is OFF.（由于 $V_D = 0.3\ \mathrm{V} < V_{D,on} = 0.6\ \mathrm{V}$，假设正确：二极管截止。）
Therefore, the Q-point is:（因此 Q 点为：）

$$
(I_D, V_D) = (0\ \mathrm{A},\ 0.3\ \mathrm{V}) \tag{10}
$$

### 1.3 Part C: Which answer do you feel is most correct?（C 部分：你认为哪个答案最正确？）

To determine which model is more accurate, let's check our results using the exponential diode equation (which we know to be the most accurate) and compare with the two models above.（为了判断哪个模型更准确，用指数二极管方程（已知它最准确）检验结果，并与上面两个模型比较。）

The exponential diode equation is:（指数二极管方程为：）

$$
I_D = I_S\left[\exp\left(\frac{V_D}{V_T}\right)-1\right] \tag{11}
$$

Using typical values: $I_S = 10^{-15}$ A and $V_T = 25$ mV (room temperature).（取典型值：$I_S = 10^{-15}$ A，$V_T = 25$ mV（室温）。）

To test the validity of our Part B analysis, let's assume the diode voltage is $V_D = 0.3$ V (as predicted when the diode is OFF) and see what current the exponential model predicts:（为检验 B 部分的分析，假设二极管电压为 $V_D = 0.3$ V（即二极管截止时的预测值），看指数模型会给出多大电流：）

$$
I_D = 10^{-15}\left[\exp\left(\frac{0.3}{0.025}\right)-1\right] \tag{12}
$$

$$
I_D = 10^{-15}\left[\exp(12)-1\right] = 163\ \mathrm{pA} \tag{13}
$$

**单位说明（unit note）**：$\mathrm{pA}$ 表示皮安（picoampere），$1\ \mathrm{pA}=10^{-12}\ \mathrm{A}$。电流单位换算为

$$
1\ \mathrm{A}=10^{3}\ \mathrm{mA}=10^{6}\ \mathrm{\mu A}=10^{9}\ \mathrm{nA}=10^{12}\ \mathrm{pA}=10^{15}\ \mathrm{fA}
$$

本题 $I_S=1\ \mathrm{fA}=10^{-15}\ \mathrm{A}$，算得 $I_D=163\ \mathrm{pA}=1.63\times10^{-10}\ \mathrm{A}$，即约 $0.163\ \mathrm{nA}$。

Note: This is not the exact solution of the exponential for this given circuit (which requires iterative methods in Part D), but rather a check of what current would flow if $V_D = 0.3$ V.（注：这不是该电路指数方程的精确解（精确解需在 D 部分用迭代法），而只是检验若 $V_D = 0.3$ V 时会有多大电流。）

**Conclusion: The constant voltage drop model (Part B) is more correct.**（结论：恒压降模型（B 部分）更正确。）

The exponential model shows that at $V_D = 0.3$ V, the current is only 163 pA - essentially negligible for practical purposes.（指数模型表明，$V_D = 0.3$ V 时电流仅 163 pA，实际应用中基本可忽略。） This confirms that the diode is effectively OFF, supporting the Part B analysis that predicted zero current and 0.3V across the diode.（这证实二极管实际上处于截止状态，支持 B 部分得出的“电流为零、二极管两端 0.3 V”的结论。）

Next, in Part D, let's properly solve the exponential model for this circuit (without making the $V_D = 0.3$ V assumption) using an iterative method.（接下来在 D 部分，用迭代法正式求解该电路的指数模型（不预设 $V_D = 0.3$ V）。）

### 1.4 Part D: Use iterative analysis to find the actual Q-point（D 部分：用迭代分析求实际的 Q 点）

For the most accurate analysis, we use the full exponential diode model with $I_S = 1$ fA and $V_T = 25$ mV.（为得到最准确的分析结果，采用完整的指数二极管模型，$I_S = 1$ fA，$V_T = 25$ mV。）

![](Pasted%20image%2020261110222415.png)
> 图15 Thévenin equivalent circuit for iterative analysis（图 15：迭代分析用的戴维南等效电路）

**Step 1: Set up the system of equations**（第 1 步：建立方程组）

We have two constraints that must be satisfied simultaneously:（有两个必须同时满足的约束：）
**Diode equation:**（二极管方程：）

$$
I_D = I_S\left[\exp\left(\frac{V_D}{V_T}\right)-1\right] = 10^{-15}\left[\exp\left(\frac{V_D}{0.025}\right)-1\right] \tag{14}
$$

**Circuit equation (Ohm's law):**（电路方程（欧姆定律）：）

$$
I_D = \frac{V_{th}-V_D}{R_{th}} = \frac{0.3-V_D}{2200} \tag{15}
$$

**Step 2: Set up for Newton-Raphson iteration**（第 2 步：为牛顿–拉夫逊迭代做准备）

We choose to iterate on current $I_D$ rather than voltage $V_D$ because iterating on current gives better numerical convergence for small currents.（选择对电流 $I_D$ 迭代而非对电压 $V_D$ 迭代，因为小电流下对电流迭代的数值收敛更好。） From (14), we can solve for $V_D$ in terms of $I_D$:（由 (14) 可解出用 $I_D$ 表示的 $V_D$：）

$$
V_D = V_T\ln\left(\frac{I_D}{I_S}+1\right) = 0.025\ln\left(10^{15}I_D+1\right) \tag{16}
$$

From (15), we can also solve for $V_D$:（由 (15) 也可以解出 $V_D$：）

$$
V_D = V_{th} - R_{th}I_D = 0.3 - 2200I_D \tag{17}
$$

Since both expressions equal $V_D$, we set them equal:（两式都等于 $V_D$，令其相等：）

$$
0.025\ln\left(10^{15}I_D+1\right) = 0.3 - 2200I_D \tag{18}
$$

Rearranging to standard form $f(I_D) = 0$:（整理成标准形式 $f(I_D) = 0$：）

$$
0.025\ln\left(10^{15}I_D+1\right) - 0.3 + 2200I_D = 0 \tag{19}
$$

This gives us our Newton-Raphson function:（得到牛顿–拉夫逊函数：）

$$
f(I_D) = 0.025\ln\left(10^{15}I_D+1\right) + 2200I_D - 0.3 \tag{20}
$$

The derivative is:（其导数为：）

$$
f'(I_D) = \frac{0.025 \times 10^{15}}{10^{15}I_D+1} + 2200 \tag{21}
$$

**Step 3: Newton-Raphson iteration**（第 3 步：牛顿–拉夫逊迭代）

Starting with initial guess $I_{D0} = 10^{-15}$ A (i.e. the saturation current), we iterate:（以初值 $I_{D0} = 10^{-15}$ A（即饱和电流）开始迭代：）

$$
I_{D(n+1)} = I_{D(n)} - \frac{f(I_{D(n)})}{f'(I_{D(n)})} \tag{22}
$$

**前两次迭代的具体计算（first two iterations）**

第 0 次：$I_{D0}=10^{-15}$ A，于是 $1+10^{15}I_{D0}=2$。

$$
f(I_{D0}) = 0.025\ln 2 + 2200(10^{-15}) - 0.3 = 0.01733 - 0.3 = -0.28267
$$

$$
f'(I_{D0}) = \frac{0.025\times10^{15}}{2} + 2200 \approx 1.25\times10^{13}
$$

$$
I_{D1} = 10^{-15} - \frac{-0.28267}{1.25\times10^{13}} = 10^{-15} + 2.26\times10^{-14} = 2.36\times10^{-14}\ \mathrm{A}
$$

第 1 次：$1+10^{15}I_{D1}=24.61$。

$$
f(I_{D1}) = 0.025\ln 24.61 + 2200(2.36\times10^{-14}) - 0.3 = 0.08008 - 0.3 = -0.21992
$$

$$
f'(I_{D1}) = \frac{0.025\times10^{15}}{24.61} + 2200 \approx 1.016\times10^{12}
$$

$$
I_{D2} = 2.36\times10^{-14} - \frac{-0.21992}{1.016\times10^{12}} = 2.36\times10^{-14} + 2.17\times10^{-13} = 2.40\times10^{-13}\ \mathrm{A}
$$

后续各次迭代的数值如下：

| 迭代次数 $n$ | $I_{Dn}$ / A |
| --- | --- |
| 0 | $1.00\times10^{-15}$ |
| 1 | $2.36\times10^{-14}$ |
| 2 | $2.40\times10^{-13}$ |
| 3 | $1.81\times10^{-12}$ |
| 4 | $9.96\times10^{-12}$ |
| 5 | $3.78\times10^{-11}$ |
| 6 | $9.30\times10^{-11}$ |
| 7 | $1.45\times10^{-10}$ |
| 8 | $1.62\times10^{-10}$ |
| 9 | $1.63\times10^{-10}$ |

可见约 8–9 次迭代后收敛到 $1.63\times10^{-10}\ \mathrm{A}=163\ \mathrm{pA}$。前期每步电流大约增大 10 倍，是因为 $f(I_D)$ 中的对数项变化缓慢，而 $f'(I_D)$ 又主要由 $\dfrac{0.025\times10^{15}}{10^{15}I_D+1}$ 决定。

**Step 4: Results**（第 4 步：结果）

After convergence, we get:（收敛后得到：）

$$
I_D = 163\ \mathrm{pA} \tag{23}
$$

**Finding** $V_D$. Using (15) to find the corresponding voltage gives:（**求** $V_D$。用 (15) 求对应的电压：）

$$
V_D = 0.3 - 2200 \times 163 \times 10^{-12} = 0.3 - 3.586 \times 10^{-7} = 0.300\ \mathrm{V} \tag{24}
$$

Therefore, the accurate Q-point is:（因此准确的 Q 点为：）

$$
\boxed{(I_D, V_D) = (163\ \mathrm{pA},\ 0.300\ \mathrm{V})} \tag{25}
$$

This confirms our Part C conclusion that the diode is essentially OFF, with negligible current flow.（这证实了 C 部分的结论：二极管实际上截止，电流可忽略。）

**Comparison of results:**（结果比较：）

- **Part A (Ideal model):** $I_D = 0.136$ mA, $V_D = 0$ V（A 部分（理想模型）：$I_D = 0.136$ mA，$V_D = 0$ V）
- **Part B (Constant voltage drop):** $I_D = 0$ A, $V_D = 0.3$ V（B 部分（恒压降模型）：$I_D = 0$ A，$V_D = 0.3$ V）
- **Exponential model:** $I_D = 163$ pA, $V_D = 0.300$ V（指数模型：$I_D = 163$ pA，$V_D = 0.300$ V）

**Important: Loading the Circuit and why Thévenin Equivalent is Necessary**（重要：电路的加载效应，以及为什么必须用戴维南等效）

**Common Misconception:** Students often try to analyze this circuit without its Thévenin Equivalent by simply calculating $V_A$ and $V_B$ using voltage dividers, then finding $V_D = V_B - V_A$.（**常见误区：** 学生常试图不用戴维南等效，直接用分压算出 $V_A$ 和 $V_B$，再由 $V_D = V_B - V_A$ 分析电路。）

![](Pasted%20image%2020261110222437.png)
> 图16 The tempting but flawed voltage divider approach（图 16：看似诱人但错误的直接分压做法）

In this specific problem, this approach gives the correct answer (0.3V) because the diode is OFF with negligible current.（在本题中，由于二极管截止、电流可忽略，这种做法恰好给出正确答案（0.3 V）。） However, this is **an incorrect solution!**（然而，这是一个**错误的解法！**）

**The Critical Issue - Loading the circuit when the Diode is ON:**（关键问题——二极管导通时的电路加载）

- Assume a larger source voltage (e.g. 10 V) such that the diode turns ON（假设电源电压更大（如 10 V），使二极管导通）
- When ON, the diode conducts significant current $I_D$（导通时，二极管流过明显的电流 $I_D$）
- This current flows through both 3k$\Omega$/2k$\Omega$ and 2k$\Omega$/2k$\Omega$ resistor networks, causing:（该电流同时流过 3 kΩ/2 kΩ 与 2 kΩ/2 kΩ 两个电阻网络，导致：）
  - $V_A$ to increase from its open-circuit value (current flows left into the node from the diode)（$V_A$ 高于其开路值（电流从二极管向左流入该节点））
  - $V_B$ to decrease from its open-circuit value (current flows right out of the node to the diode)（$V_B$ 低于其开路值（电流从该节点向右流出到二极管））

Therefore, the resulting $V_D$ is *less* than the subtraction of the voltage divider-derived values of $V_B$ and $V_A$ due to the current.（因此，由于电流的存在，所得 $V_D$ 比直接用分压值相减得到的 $V_B - V_A$ *更小*。） This is called **loading** the circuit.（这称为电路的**加载**效应。）

- The voltage divider method **only gives the correct answer when no current flows**. I.e., the circuit is *unloaded*.（分压法**只有在没有电流流过时才给出正确答案**，即电路处于*未加载*状态。）

**Why Thévenin Equivalent Works:**（为什么戴维南等效有效：）

The Thévenin Voltage ($V_{th}$) captures the open-circuit voltage (what the voltage dividers give you) if no current were flowing into the diode, while the Thévenin Resistance ($R_{th}$) captures *how this voltage changes with current through the diode*.（戴维南电压 $V_{th}$ 表示若无电流流入二极管时的开路电压（即分压给出的值），而戴维南电阻 $R_{th}$ 表示*该电压如何随流过二极管的电流变化*。）

**Example to Illustrate the Problem:**（说明该问题的例子：）

Consider if this circuit had a 10 V source instead of 3 V:（假设该电路用 10 V 电源代替 3 V：）

- Voltage divider approach gives $V_A = 4$ V, $V_B = 5$ V, incorrectly suggesting $V_D = 1$ V（分压法给出 $V_A = 4$ V、$V_B = 5$ V，错误地暗示 $V_D = 1$ V）
- Actual answer: Diode turns ON with $V_D = 0.645$ V and $I_D = 161\ \mathrm{\mu A}$.（正确答案：二极管导通，$V_D = 0.645$ V，$I_D = 161$ μA。）

Try this example yourself by re-attempting Q1.d with a 10 V voltage source.（可用 10 V 电源重做 Q1.d，自行验证此例。）

**Contrast with MOSFET Circuits (Future Topic):** Later in this course, you'll see MOSFET (transistor) circuits where we **do** use voltage dividers directly.（**与 MOSFET 电路的对比（后续内容）：** 本课程后面会看到 MOSFET（晶体管）电路，那里**确实**直接使用分压。）

The key difference is that MOSFET gates draw **zero** DC current ($I_G = 0$), so they don't load the voltage divider.（关键区别在于 MOSFET 栅极的直流电流为**零**（$I_G = 0$），因此不会对分压电路产生加载。）

## 2 Question 2（第 2 题）

The full-wave rectifier in the figure below is operating at a frequency of 60 Hz, and the rms value of the transformer output voltage is 18 V.（下图中的全波整流器工作频率为 60 Hz，变压器输出电压的有效值为 18 V。）

- (a) What is the value of the dc output voltage if the diode voltage drop is 1 V?（若二极管压降为 1 V，直流输出电压是多少？）
- (b) What is the minimum value of $C$ required to maintain the ripple voltage to less than 0.25 V if $R = 0.5\ \Omega$?（若 $R = 0.5$ Ω，要把纹波电压维持在 0.25 V 以下，所需电容 $C$ 的最小值是多少？）
- (c) What is the PIV rating of the diode in this circuit?（该电路中二极管的 PIV 额定值是多少？）

![](Pasted%20image%2020261110222453.png)
> 图17 Q2 circuit diagram（图 17：Q2 电路图）

Solution:（**解答：**）

Looking at the circuit diagram, we can recognize that it is a full-wave rectifier with a center-tap transformer.（观察电路图可知，这是带中心抽头变压器的全波整流器。）

**Understanding Current Flow:**（理解电流路径：）

This rectifier operates by utilizing both half-cycles of the AC input through two separate conduction paths:（该整流器通过两条独立的导通路径，利用交流输入的正、负两个半周：）

- **Positive half-cycle of $v_I$:** The top terminal of the transformer secondary is positive. Current flows from the center-tap (ground), up through the load resistor $R$ (from bottom to top), through diode $D_1$ (which is forward-biased), to the top terminal of the transformer. During this time, diode $D_2$ is reverse-biased and blocks current flow.（**$v_I$ 正半周：** 变压器副边顶端为正。电流从中心抽头（地）出发，自下而上流过负载电阻 $R$，经正向偏置的二极管 $D_1$，到达变压器顶端。在此期间，二极管 $D_2$ 反偏，阻断电流。）
- **Negative half-cycle of $v_I$:** The bottom terminal of the transformer secondary is positive. Current flows from the center-tap (ground), up through the load resistor $R$ (from bottom to top, same direction as positive half-cycle), through diode $D_2$ (which is forward-biased), to the bottom terminal of the transformer. During this time, diode $D_1$ is reverse-biased.（**$v_I$ 负半周：** 变压器副边底端为正。电流从中心抽头（地）出发，自下而上流过负载电阻 $R$（方向与正半周相同），经正向偏置的二极管 $D_2$，到达变压器底端。在此期间，二极管 $D_1$ 反偏。）

**Key Insight:** 

Notice that in both half-cycles, current flows through the load resistor in the *same direction* (from ground upward through the resistor). This unusual diode orientation forces current to flow FROM ground TO the DC output node, making $V_{dc}$ negative relative to ground.
（**关键点：** 注意两个半周中，电流都以*同一方向*流过负载电阻（从地向上）。这种不寻常的二极管方向迫使电流从地流向直流输出节点，使 $V_{dc}$ 相对于地为负。）

**电容滤波全波整流的输出过程（capacitor-filtered full-wave rectifier）**

- **充电阶段**：每个半周中，当变压器副边电压高于电容电压一个二极管压降时，对应二极管导通，电源经二极管给电容充电，输出电压随输入正弦上升，最高达到 $V_p-V_{on}$，即接近峰值。
- **放电阶段**：输入越过峰值开始下降后，电容电压暂时高于输入电压，二极管反偏截止，电容只能通过负载 $R$ 放电，电压按指数规律 $v_O(t)\approx V_{\text{peak}}e^{-t/(RC)}$ 缓慢下降。
- **再次充电**：全波整流每隔半个周期就出现一个峰值；当下一个半周的输入电压重新超过电容电压时，二极管再次导通，把电容补回峰值附近。此后不断重复“充电—放电—再充电”。
- **波形特点**：充电时间很短（回路电阻小、时间常数小），放电时间很长（$RC$ 大），所以输出是紧贴峰值的小锯齿波，可分解为**直流分量 $V_{dc}$** 和**纹波 $v_r$**，即 $v_O(t)=V_{dc}+v_r(t)$。
- **纹波近似**：全波整流的纹波峰峰值为 $V_r\approx\dfrac{V_{dc}}{2fRC}\approx\dfrac{I_L}{2fC}$。$C$ 越大、$R$ 越大、频率越高，纹波越小；纹波很小时 $V_{dc}\approx V_p-V_{on}-\dfrac{V_r}{2}\approx V_p-V_{on}$。

式中：$V_p$ 为变压器副边的峰值电压（中心抽头到任一端），$V_p=\sqrt{2}V_{rms}$；$V_{on}$ 为二极管的导通压降（turn-on voltage，也叫门坎电压；恒压降模型中导通时 $V_D=V_{on}$，硅管典型 0.6–0.7 V，本题取 1 V）；$V_r$ 为纹波电压峰峰值；$f$ 为工作频率；$C$ 为滤波电容；$R$ 为负载电阻；$I_L$ 为负载电流。

**电容的初始电压（initial capacitor voltage）**：上电前 $v_C(0)=0$，之后每个峰值把电容往上补一点，经过若干个周期（由时间常数 $RC$ 决定）才升到 $V_p-V_{on}$ 附近；这期间充电电流很大，称为浪涌电流（inrush current）。二极管导通的条件始终是 $v_s>v_C+V_{on}$。本题求 $V_{dc}$ 时默认电路已进入稳态，即电容已充到峰值附近、纹波很小；初始电压只影响暂态过程（建立时间、浪涌电流），不影响稳态的平均直流电压。

### 2.1 Part A（A 部分）

To find the DC output voltage, we need to trace the current path and account for the diode voltage drop.（求直流输出电压，需要追踪电流路径并计入二极管压降。）

**Step 1: Determine peak voltage from given RMS voltage**（第 1 步：由给定有效值求峰值电压） The peak transformer secondary voltage (from center-tap to either end) is:（变压器副边（从中心抽头到任一端）的峰值电压为：）

$$
V_p = V_{rms} \times \sqrt{2} = 18\sqrt{2} = 25.46\ \mathrm{V}
$$

This is just a conversion from the given $V_{rms} = 18$ V RMS voltage to peak voltage of a sine wave (AC).（这只是把给定的有效值 $V_{rms} = 18$ V 换算成正弦波（交流）的峰值电压。）

**Step 2: Account for diode voltage drop**（第 2 步：计入二极管压降） During each half-cycle, current flows through exactly one diode before reaching the load. Therefore:（每个半周中，电流到达负载前恰好经过一个二极管。因此：）

$$
V_{dc,\mathrm{magnitude}} = V_p - V_{on} = 25.46 - 1 = 24.46\ \mathrm{V}
$$

**Step 3: Determine polarity**（第 3 步：确定极性） Looking at the circuit orientation and following the current flow:（观察电路方向并沿电流路径判断：）

- Current flows *from ground upward* to the $V_{dc}$ node（电流*从地向上*流向 $V_{dc}$ 节点）
- This means the $V_{dc}$ node is at a *lower potential* than ground（这意味着 $V_{dc}$ 节点电位*低于*地）
- Therefore: $V_{dc} = -24.46$ V（因此：$V_{dc} = -24.46$ V）

$$
V_{dc} = -(V_p - V_{on}) = -(25.46 - 1) = -24.46\ \mathrm{V} \tag{1}
$$

**Important Note:** This circuit produces a *negative* DC output voltage because of the diode orientations. In a typical rectifier, current flows from $V_{dc}$ to ground (positive output), but here the diodes are oriented to force current from ground toward the $V_{dc}$ node.
（**重要提示：** 由于二极管的接向，该电路产生*负*的直流输出电压。在典型整流器中，电流从 $V_{dc}$ 流向地（正输出），而这里的二极管接向迫使电流从地流向 $V_{dc}$ 节点。）

### 2.2 Part B（B 部分）

We will apply the formulas in the red box in the table below.（我们将使用下表红框中的公式。）

![](Pasted%20image%2020261110222512.png)
> 图18 Comparison of Rectifiers with Capacitive Filters（图 18：带电容滤波的整流器比较）

**表（从图 18 提取，comparison of rectifiers with capacitive filters）**

| 整流参数 | 半波整流 | 全波整流（中心抽头） | 全波桥式整流 |
| --- | --- | --- | --- |
| 滤波电容 | $C=\dfrac{V_P-V_{on}}{V_r}\cdot\dfrac{T}{R}$ | $C=\dfrac{V_P-V_{on}}{V_r}\cdot\dfrac{T}{2R}$ | $C=\dfrac{V_P-2V_{on}}{V_r}\cdot\dfrac{T}{2R}$ |
| 反向峰值电压 PIV | $2V_P$ | $2V_P$ | $V_P$ |
| 峰值二极管电流（$V_r$ 恒定） | 最大，$I_P$ | 减小，$I_P/2$ | 减小，$I_P/2$ |
| 浪涌电流 | 最大 | 减小（$\propto C$） | 减小（$\propto C$） |

式中：$V_P$ 为变压器副边峰值电压（$V_P=\sqrt{2}V_{rms}$）；$V_{on}$ 为单个二极管的导通压降；$V_r$ 为纹波电压峰峰值；$T$ 为工作周期（$T=1/f$）；$R$ 为负载电阻；$I_P$ 为峰值二极管电流；PIV（peak inverse voltage）为二极管承受的最大反向电压。

**纹波电压（ripple voltage，$V_r$）**：整流滤波后，输出直流电压上叠加的交流波动分量，通常用**峰峰值**表示，即一个周期内输出电压的最大值与最小值之差

$$
V_r=V_{O,\max}-V_{O,\min}
$$

它来自电容的充放电过程，与滤波电容 $C$、负载电流 $I_L$ 和工作频率 $f$ 有关：全波整流时 $V_r\approx\dfrac{I_L}{2fC}$，半波整流时 $V_r\approx\dfrac{I_L}{fC}$。$C$ 越大、$R$ 越大、频率越高，纹波越小；$V_r$ 相对于 $V_{dc}$ 的百分比称为纹波系数（ripple factor）。

Also, we can get the following parameters from the question.（此外，可从题目得到以下参数。）

$$
\begin{aligned}
&\text{Operation frequency: } f = 60\ \mathrm{Hz}, \\
&\text{Operation period: } T = 1/f = 1/60\ \text{sec}, \\
&\text{RMS transformer output: } V_{rms} = 18\ \mathrm{V}.
\end{aligned} \tag{2}
$$

We can determine the peak transformer output voltage by（可由下式确定变压器输出的峰值电压）

$$
V_p = V_{rms} \times \sqrt{2} = 18\sqrt{2}\ \mathrm{V}. \tag{3}
$$

Taking the formula of the required capacitance for the full-wave rectifier for voltage ripple $V_r = 0.25$ V and load resistance $R = 0.5\ \Omega$ (see Figure 18), we get:
（取全波整流器所需电容的公式，代入纹波电压 $V_r = 0.25$ V、负载电阻 $R = 0.5$ Ω（见图 18），得到：）

$$
C = \frac{V_p - V_{on}}{V_r} \cdot \frac{T}{2R} = \frac{18\sqrt{2}-1}{0.25} \cdot \frac{1/60}{2 \cdot 0.5} = 1.63\ \mathrm{F} \tag{4}
$$

### 2.3 Part C（C 部分）

Taking the formula of the required PIV for the full-wave rectifier, we can get（取全波整流器所需 PIV 的公式，可得）

$$
PIV \geq 2V_p = 2 \cdot 18\sqrt{2} = 50.91\ \mathrm{V} \tag{5}
$$

**PIV（peak inverse voltage，反向峰值电压）**：二极管在截止（反偏）期间所承受的最大反向电压。选管时必须保证二极管的允许反向电压（反向击穿电压 $V_{BR}$）不小于这个值，工程上通常再留一定裕量：

$$
V_{BR}\geq PIV
$$

不同整流电路中 PIV 不同：

- 半波整流、全波中心抽头整流：$PIV=2V_p$（截止管两端同时承受两个半绕组的峰值电压）；
- 全波桥式整流：$PIV=V_p$。

$V_p$ 为副边峰值电压（中心抽头到任一端）。本题 $PIV=2\times18\sqrt{2}\approx50.91$ V，故应选反向耐压不低于约 51 V 的二极管。

## 3 Question 3（第 3 题）

What are the dc output voltages $V_1$ and $V_2$ for the rectifier circuit in the figure below if $v_i = 40\sin 377t$ and $C = 20,000\ \mathrm{\mu F}$?（若 $v_i = 40\sin 377t$、$C = 20{,}000$ μF，下图整流电路的直流输出电压 $V_1$、$V_2$ 各是多少？）

![](Pasted%20image%2020261110222525.png)
> 图19 Q3 circuit diagram（图 19：Q3 电路图）


>看成两个Q2电路图合在一起

Solution:（**解答：**）

This circuit is a **dual-output center-tap rectifier** that produces both positive and negative DC voltages simultaneously.（该电路是**双输出中心抽头整流器**，可同时产生正、负直流电压。）

Let the top and bottom capacitors be denoted $C_1$ and $C_2$, repectively.（上、下两个电容分别记为 $C_1$ 和 $C_2$。）

**Positive half-cycle of $v_i$:**（$v_i$ 正半周：）

- Upper terminal: $+40$ V, Lower terminal: $-40$ V（**二次侧**上端 $+40$ V，**二次侧**下端 $-40$ V）
- $D_1$ forward-biased: Current flows via $C_1$ to ground, creating $V_1 > 0$（$D_1$ 正偏：电流经 $C_1$ 流向地，产生 $V_1 > 0$）
- $D_3$ forward-biased: Current flows from ground via $C_2$, creating $V_2 < 0$（$D_3$ 正偏：电流从地经 $C_2$ 流动，产生 $V_2 < 0$）
- $D_2$ and $D_4$ are reverse-biased (OFF)（$D_2$、$D_4$ 反偏（截止））

**Negative half-cycle of $v_i$:**（$v_i$ 负半周：）

- Upper terminal: $-40$ V, Lower terminal: $+40$ V（上端 $-40$ V，下端 $+40$ V）
- $D_2$ forward-biased: Current flows from ground via $C_2$, maintaining $V_2 < 0$（$D_2$ 正偏：电流从地经 $C_2$ 流动，维持 $V_2 < 0$）
- $D_4$ forward-biased: Current flows via $C_1$ to ground, maintaining $V_1 > 0$（$D_4$ 正偏：电流经 $C_1$ 流向地，维持 $V_1 > 0$）
- $D_1$ and $D_3$ are reverse-biased (OFF)（$D_1$、$D_3$ 反偏（截止））

From $v_i = 40\sin 377t$, we can extract:（由 $v_i = 40\sin 377t$ 可得：）

$$
\begin{aligned}
&\text{Operation frequency: } \omega = 377\ \mathrm{rad/s}, \\
&\text{Peak voltage: } V_p = 40\ \mathrm{V}
\end{aligned} \tag{1}
$$

For each output ($V_1$ and $V_2$), there is exactly one diode in the conduction path during each half-cycle. Using the diode turn-on voltage $V_{D,on} = 1$ V from Q2:（对每个输出（$V_1$ 和 $V_2$），每个半周的导电路径中都恰好有一个二极管。采用第 2 题中的二极管导通电压 $V_{D,on} = 1$ V：）

**Voltage Calculations:**（电压计算：）

$$
\begin{aligned}
V_1 &= V_p - V_{D,on} = 40 - 1 = 39\ \mathrm{V}, \\
V_2 &= -(V_p - V_{D,on}) = -(40 - 1) = -39\ \mathrm{V}.
\end{aligned} \tag{2}
$$

**Insights:**（要点：）

- $V_1$ is always positive because current always flows *from* $V_1$ *to* ground.（$V_1$ 恒为正，因为电流总是*从* $V_1$ *流向*地。）
- $V_2$ is always negative because current flows *from* ground *to* $V_2$.（$V_2$ 恒为负，因为电流总是*从*地*流向* $V_2$。）
- Both outputs are full-wave rectified, providing continuous DC with minimal ripple（两路输出均为全波整流，提供纹波很小的连续直流）
- The circuit effectively creates a dual-rail power supply ($+39$ V and $-39$ V)（该电路实际上构成双电源轨（$+39$ V 与 $-39$ V））

---