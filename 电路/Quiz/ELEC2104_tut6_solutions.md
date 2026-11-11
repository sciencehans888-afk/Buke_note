# ELEC2104/9704 Tutorial 6 Solutions (2025)

For any BJT circuit analysis question, the first step is label all BJT voltages and currents and with correct polarities/directions.（对于任何 BJT 电路分析题，第一步都是标出所有 BJT 电压与电流，并标对极性/方向。） For NPN transistors, the arrow points *outward* from the emitter, indicating conventional current flow direction.（对于 NPN 晶体管，箭头从发射极指向*外*，表示常规电流的流动方向。） For PNP transistors, the arrow points *inward* to the emitter, with opposite current directions.（对于 PNP 晶体管，箭头指向发射极*内部*，电流方向相反。）

![](Pasted%20image%2020261111234834.png)
> 图1 NPN and PNP BJT symbols with proper voltage and current labeling conventions（图 1：NPN 与 PNP BJT 符号，以及正确的电压、电流标注约定）

**Technique to establish the correct BJT current directions and voltage polarities**（确定 BJT 电流方向与电压极性的技巧）

Observe the arrow direction in the BJT circuit symbol.（观察 BJT 电路符号中的箭头方向。） 

This arrow indicates the emitter $E$ terminal and the direction of current flow for the emitter current $I_E$.（这个箭头指示发射极 $E$ 端以及发射极电流 $I_E$ 的流动方向。）

The remaining currents $I_C$ and $I_B$ have the opposite direction.（其余电流 $I_C$ 与 $I_B$ 的方向相反。） For example, if $I_E$ points outward (NPN), then $I_C$ and $I_B$ point inward.（例如，若 $I_E$ 向外（NPN），则 $I_C$ 与 $I_B$ 向内。） 

The BJT voltage directions are given by these current directions, as the current arrows point from the positive (+) to the negative (-) of their corresponding voltages.（BJT 的电压方向由这些电流方向确定，因为电流箭头从对应电压的正（+）端指向负（−）端。）

> [!tip] Essential BJT Equations for Circuit Analysis（BJT 电路分析的基本方程）
> **Fundamental BJT equations you'll use repeatedly in this course:**（本课程中会反复用到的基本 BJT 方程：）
>
> **1. Exponential I-V Relationship:**（1. 指数型 I–V 关系：）
>
> $$
> I_C = I_S\left[\exp\left(\frac{V_{BE}}{V_T}\right)-1\right] \approx I_S\exp\left(\frac{V_{BE}}{V_T}\right) \quad \text{when } V_{BE} \gg V_T
> $$
>
> This describes the non-linear, exponential relationship between collector current and base-emitter voltage.（这描述了集电极电流与基极-发射极电压之间的非线性指数关系。） 
> Small changes in $V_{BE}$ cause large changes in $I_C$.（$V_{BE}$ 的微小变化会引起 $I_C$ 的很大变化。）
>
> **2. Current Relationships:**（2. 电流关系：）
>
> $$
> I_E = I_C + I_B \quad \text{and} \quad I_C = \beta I_B \quad \text{where } \beta \text{ is the current gain (typically 100-200)}
> $$
>
> **3. Small-Signal Parameters (for AC analysis):**（3. 小信号参数（用于交流分析）：）
>
> $$
> g_m = \frac{I_C}{V_T}\ \ (\text{transconductance}) \quad \text{and} \quad r_\pi = \frac{\beta}{g_m}\ \ (\text{input resistance})
> $$
>
> These linearized parameters are crucial for analysing BJT amplifiers (next tutorial).（这些线性化参数对分析 BJT 放大器（下次课）至关重要。）

## 1 Question 1（第 1 题）

In the circuit below, it is observed that the collector currents of $Q_1$ and $Q_2$ are equal if $V_{BE1} - V_{BE2}$ = 20 mV.（在下述电路中，可以观察到当 $V_{BE1}-V_{BE2}=20$ mV 时，$Q_1$ 与 $Q_2$ 的集电极电流相等。） 

Determine the ratio of transistor cross-section areas if the other device parameters are identical.（若其他器件参数相同，求两晶体管横截面积之比。）

Assume $V_T$ = 26 mV.（假设 $V_T=26$ mV。）

![](Pasted%20image%2020261111234845.png)
> 图2 Q1 circuit diagram（图 2：第 1 题电路图）

Solution:（**解答：**）

For a BJT, (in this course) the correlation between the voltage drop between base and emitter ($V_{BE}$) and the collector current ($I_C$) is modelled by the exponential relation given by:（对于 BJT，本课程中基极与发射极之间的压降 $V_{BE}$ 与集电极电流 $I_C$ 的关系用如下指数关系描述：）

$$
I_C = I_S\left[\exp\left(\frac{V_{BE}}{V_T}\right)-1\right] \approx I_S\exp\left(\frac{V_{BE}}{V_T}\right) \tag{1}
$$

The following formula for BJT saturation current was presented in the lecture:（课上给出了 BJT 饱和电流的如下公式：）

$$
I_S = \frac{AqD_n n_i^2}{N_A W_B} \tag{2}
$$

Taking (1) into (2), we find that $I_C$ is proportional to the transistor cross-section area $A$, so $I_C \propto A$.（把 (1) 代入 (2) 可得 $I_C$ 正比于晶体管横截面积 $A$，即 $I_C\propto A$。）

$$
I_C = \left(\frac{AqD_n n_i^2}{N_A W_B}\right)\exp\left(\frac{V_{BE}}{V_T}\right). \tag{3}
$$

Since $I_{C1} = I_{C2}$, we have:（由于 $I_{C1}=I_{C2}$，有：）

$$
\frac{A_1 q D_n n_i^2}{N_A W_B}\exp\left(\frac{V_{BE1}}{V_T}\right) = \frac{A_2 q D_n n_i^2}{N_A W_B}\exp\left(\frac{V_{BE2}}{V_T}\right). \tag{4}
$$


Note the subscripts for $A_1$, $V_{BE1}$ and $A_2$, $V_{BE2}$ denoting quantities for transistors $Q_1$ and $Q_2$, respectively.（注意 $A_1$、$V_{BE1}$ 与 $A_2$、$V_{BE2}$ 的下标分别表示 $Q_1$ 与 $Q_2$ 的量。）

The question states that all other device parameters are identical.（题目说明其他器件参数均相同。）

From (4), we can derive the ratio of the two cross-section areas, note that the identical parameters cancelled out:（由 (4) 可导出两横截面积之比，注意相同参数已约去：）

$$
A_1\exp\left(\frac{V_{BE1}}{V_T}\right) = A_2\exp\left(\frac{V_{BE2}}{V_T}\right). \tag{5}
$$

$$
\frac{A_2}{A_1} = \frac{\exp\left(\frac{V_{BE1}}{V_T}\right)}{\exp\left(\frac{V_{BE2}}{V_T}\right)} = \exp\left(\frac{V_{BE1} - V_{BE2}}{V_T}\right). \tag{6}
$$

Substituting $V_{BE1} - V_{BE2} = 20\ \mathrm{mV}$ and $V_T = 26\ \mathrm{mV}$, we get the value of the ratio.（代入 $V_{BE1}-V_{BE2}=20$ mV 与 $V_T=26$ mV，即得比值。）

$$
\frac{A_2}{A_1} = \exp\left(\frac{0.020}{0.026}\right) \approx 2.158. \tag{7}
$$

Or:（或：）

$$
\frac{A_1}{A_2} = \exp\left(\frac{-0.020}{0.026}\right) \approx 0.463. \tag{8}
$$

## 2 Question 2（第 2 题）

Consider the circuit below.（考虑下图电路。） Assume $V_T$ = 26 mV.（假设 $V_T=26$ mV。）

- (a) If $I_{S1} = 2I_{S2} = 5 \times 10^{-16}$ A, determine $V_B$ such that $I_X$ = 1.2 mA.（若 $I_{S1}=2I_{S2}=5\times10^{-16}$ A，求使 $I_X=1.2$ mA 的 $V_B$。）
- (b) What value of $R_C$ places the transistors at the edge of the active mode?（$R_C$ 取多大时，晶体管处于放大区的边缘？）

![](Pasted%20image%2020261111234858.png)
> 图3 Q2 circuit diagram（图 3：第 2 题电路图）

### 2.1 Part A: If $I_{S1} = 2I_{S2} = 5 \times 10^{-16}$ A, determine $V_B$ such that $I_X = 1.2$ mA（A 部分：若 $I_{S1}=2I_{S2}=5\times10^{-16}$ A，求使 $I_X=1.2$ mA 的 $V_B$）

From the circuit diagram, we immediately notice that the two BJTs share a base voltage ($V_B$) and a collector voltage ($V_C$).（由电路图可见，两个 BJT 共用基极电压 $V_B$ 与集电极电压 $V_C$。） 

They also have the same emitter voltage ($V_E$) since both emitters are connected to ground.（由于两发射极都接地，它们的发射极电压 $V_E$ 也相同。） Therefore, we write $V_{BE1} = V_{BE2} = V_B$.（因此可写 $V_{BE1}=V_{BE2}=V_B$。）

Next, we write an expression for $I_X$ using KCL on the shared collector node:（接下来，在共用的集电极节点上用 KCL 写出 $I_X$ 的表达式：）

$$
I_X = I_{C1} + I_{C2} = I_{S1}\exp\left(\frac{V_{BE1}}{V_T}\right) + I_{S2}\exp\left(\frac{V_{BE2}}{V_T}\right) \tag{1}
$$

The question gives the following information:（题目给出以下信息：）

$$
\begin{aligned}
&I_{S1} = 2I_{S2} = 5 \times 10^{-16}\ \mathrm{A}, \\
&I_X = 1.2\ \mathrm{mA}, \\
&V_T = 26\ \mathrm{mV}.
\end{aligned} \tag{2}
$$

Using the above, we can solve for $V_B$ by substituting $I_{S2} = \frac{1}{2}I_{S1}$ and $V_{BE1} = V_{BE2} = V_B$:（利用上述信息，代入 $I_{S2}=\frac12I_{S1}$ 与 $V_{BE1}=V_{BE2}=V_B$，即可解出 $V_B$：）

$$
I_X = I_{S1}\exp\left(\frac{V_B}{V_T}\right) + \tfrac{1}{2}I_{S1}\exp\left(\frac{V_B}{V_T}\right) \tag{3}
$$

$$
1.2 \times 10^{-3}\ \mathrm{A} = \left(1 + \tfrac{1}{2}\right)(5 \times 10^{-16}\ \mathrm{A})\exp\left(\frac{V_B}{0.026\ \mathrm{V}}\right) \tag{4}
$$

$$
1.6 \times 10^{12} = \exp\left(\frac{V_B}{0.026\ \mathrm{V}}\right) \tag{5}
$$

$$
V_B = \ln\left(1.6 \times 10^{12}\right)(0.026\ \mathrm{V}) = 0.731\ \mathrm{V} \tag{6}
$$

**Answer:** $V_B = 0.731$ V（**答案：** $V_B=0.731$ V）
*A more detailed, step-by-step walkthrough of this solution is provided in Section 2.3 below.*（本解答更详细的逐步推导见下文 2.3 节。）

> [!warning] Important Note: $V_{BE}$ vs $V_B$（重要提示：$V_{BE}$ 与 $V_B$ 的区别）
> Be careful to distinguish between $V_{BE}$ (base-emitter voltage) and $V_B$ (base voltage with respect to ground).（注意区分 $V_{BE}$（基极-发射极电压）与 $V_B$（基极对地电压）。）
> In this circuit, since both emitters are connected to ground (0V), we have $V_{BE} = V_B - V_E = V_B - 0 = V_B$.（本电路中，由于两发射极都接地（0 V），有 $V_{BE}=V_B-V_E=V_B-0=V_B$。）
> However, if there were a resistor between the emitter and ground, then $V_E \neq 0$ and $V_{BE} = V_B - V_E \neq V_B$.（然而，如果发射极与地之间有电阻，则 $V_E\neq0$，$V_{BE}=V_B-V_E\neq V_B$。） This is a common source of confusion in BJT circuit analysis.（这是 BJT 电路分析中常见的混淆来源。）

> [!info] BJT Operating Regions (NPN)（BJT 的工作区（NPN））
> ![](Pasted%20image%2020261111234914.png)
> 图4 BJT operating regions as a function of $V_{BE}$ and $V_{BC}$ voltages (NPN)（图 4：BJT 工作区随 $V_{BE}$、$V_{BC}$ 电压的变化（NPN））
>
> The figure above shows the four operating regions of a BJT transistor based on the base-emitter ($V_{BE}$) and base-collector ($V_{BC}$) junction voltages.（上图给出 BJT 根据基极-发射极（$V_{BE}$）与基极-集电极（$V_{BC}$）结电压划分的四个工作区。） 
> The table below provides detailed conditions for each region:（下表列出各工作区的详细条件：）
>
> | Region（工作区） | Voltage Relationships (NPN)（电压关系（NPN）） |
> |---|---|
> | Cut-off（截止区） | $V_E > V_B$ and $V_C > V_B$<br>Both junctions reverse-biased（两个结均反偏） |
> | Forward Active<br>(very common)（放大区（很常用）） | $V_C > V_B > V_E$<br>BE forward, BC reverse（BE 正偏，BC 反偏） |
> | Saturation（饱和区） | $V_E < V_B$ and $V_C < V_B$<br>Both junctions forward-biased（两个结均正偏） |
> | Reverse Active<br>(rarely used)（反向放大区（很少用）） | $V_C < V_B < V_E$<br>BE reverse, BC forward（BE 反偏，BC 正偏） |
>
> *For PNP transistors, simply flip the directions of these inequalities.*（对 PNP 晶体管，只需把上述不等号方向全部翻转。）
>
> **Key insight for Q2 Part B:**（第 2 题 B 部分的关键点：）
>
> - The boundary between Forward Active and Saturation occurs when $V_{BC} = 0$, which means $V_C = V_B$, that is, the x-axis intercept in Fig 4.（放大区与饱和区的边界出现在 $V_{BC}=0$ 处，即 $V_C=V_B$，也就是图 4 中横轴的截距。）
> - At this point, the BC junction is about to become forward-biased（此时 BC 结即将变为正偏）
> - This is the "edge of active mode" condition we need to find $R_C$（这就是求 $R_C$ 所需的“放大区边缘”条件）

### 2.2 Part B: What value of $R_C$ places the transistors at the edge of the active mode?（B 部分：$R_C$ 取多大时晶体管处于放大区边缘？）

![](Pasted%20image%2020261111234929.png)
> 图5 Q2 circuit diagram（图 5：第 2 题电路图）

To find the value of $R_C$ that places the transistors at the edge of active mode, we need to determine when the transistors are about to enter saturation.（要找出使晶体管处于放大区边缘的 $R_C$，需要确定晶体管在何时即将进入饱和区。）

**Step 1: Identify the boundary condition**（第 1 步：确定边界条件）
At the boundary between forward-active and saturation regions, the base-collector junction is about to become forward-biased.（在放大区与饱和区的边界上，基极-集电极结即将变为正偏。） 

This occurs when:（此时满足：）

$$
V_C = V_B \quad \text{(edge of saturation condition)} \tag{7}
$$

**Step 2: Apply Ohm's law across $R_C$**（第 2 步：对 $R_C$ 应用欧姆定律）
The current $I_X$ flows through resistor $R_C$, creating a voltage drop from $V_{CC}$ to $V_C$:（电流 $I_X$ 流过电阻 $R_C$，在 $V_{CC}$ 到 $V_C$ 之间产生压降：）

$$
I_X = \frac{V_{CC} - V_C}{R_C} \tag{8}
$$

**Step 3: Substitute the boundary condition**（第 3 步：代入边界条件）
Since we want $V_C = V_B$ at the edge of active mode, we substitute:（由于放大区边缘要求 $V_C=V_B$，代入得：）

$$
I_X = \frac{V_{CC} - V_B}{R_C} \tag{9}
$$

**Step 4: Solve for $R_C$**（第 4 步：解出 $R_C$）
Rearranging (9) to isolate $R_C$:（重排 (9) 以解出 $R_C$：）

$$
R_C = \frac{V_{CC} - V_B}{I_X} \tag{10}
$$

**Step 5: Substitute known values**（第 5 步：代入已知值）
From Part A, we found $V_B = 0.731$ V.（由 A 部分已求得 $V_B=0.731$ V。） Using the given values:（使用已知值：）

- $V_{CC} = 2.5$ V (from circuit diagram)（由电路图得）
- $V_B = 0.731$ V (calculated in Part A)（A 部分算出）
- $I_X = 1.2$ mA (given)（题目给出）

$$
R_C = \frac{2.5\ \mathrm{V} - 0.731\ \mathrm{V}}{1.2 \times 10^{-3}\ \mathrm{A}} = \frac{1.769\ \mathrm{V}}{1.2 \times 10^{-3}\ \mathrm{A}} = 1474.17\ \Omega \tag{11}
$$

**Answer:** $R_C = 1.47$ k$\Omega$ places both transistors at the edge of active mode ($V_C = V_B$).（**答案：** $R_C=1.47$ kΩ，此时两晶体管均处于放大区边缘（$V_C=V_B$）。）

### 2.3 Part A: Detailed Walkthrough（A 部分：详细推导）

**Here we revisit Q2.a using systematic problem-solving techniques.**（这里用系统化的解题方法重新推导 Q2(a)。）

**Variable Inventory** Create an inventory of known vs unknown variables to prevent getting lost in complex problems.（**变量清单**：列出已知量与未知量，避免在复杂问题中迷失。）
**Known variables:**（已知量：）

- $I_{S1} = 5 \times 10^{-16}$ A (given)（题目给出）
- $I_{S2} = \frac{1}{2}I_{S1} = 2.5 \times 10^{-16}$ A (from given relationship)（由给定关系得到）
- $I_X = 1.2$ mA (given)（题目给出）
- $V_{CC} = 2.5$ V (from circuit diagram)（由电路图得）
- $V_T = 26$ mV (thermal voltage at room temperature)（室温热电压）
- $V_{E1} = V_{E2} = 0$ V (emitters connected to ground)（发射极接地）

**Target variable:**（目标变量：）

- $V_B = V_{BE1} = V_{BE2}$ (what we're solving for)（待求量）

**Circuit Analysis Strategy** Now let's solve systematically using the *"build-up"* approach:（**电路分析策略**：下面用“逐步构建”法系统求解：）

1. Start by listing the question's given quantities and noting the target variable/s to solve for（先列出题目已知量，并明确待求变量）
2. Identify circuit relationships (KCL, KVL, component laws) to build a *mathematical model* of the circuit（找出电路关系（KCL、KVL、元件定律），建立电路的*数学模型*）
3. Count the number of unknown variables in these relationships and mark the variables that are known.（清点这些关系中的未知量个数，并标出已知量。）
4. Look for ways to substitute and reduce the number of unknowns - are there circuit relationships you haven't described mathematically yet?（寻找代入化简、减少未知量的方法——是否还有电路关系没有写成数学式？）
5. Substitute numerical values only at the end when you have the target variable/s in terms of known values.（最后一步才代数值，此时待求量应已表示为已知量的函数。）

**Key insight:** If you get stuck, you may be missing a circuit feature from the math, or a given value from the question.（**关键提示：** 如果卡住了，可能是数学模型中漏掉了某个电路特征，或漏用了题目给出的某个值。） Ask yourself: *"What circuit relationships haven't I captured in equations yet?"*（问自己：“还有哪些电路关系没有写进方程？”）

![](Pasted%20image%2020261111234944.png)
> 图6 Q2 circuit diagram（图 6：第 2 题电路图）

We start with $I_X = 1.2$ mA (given) and ask: *"How does this current relate to other circuit elements?"*（从已知的 $I_X=1.2$ mA 出发，并问：“这个电流与其他电路元件是什么关系？”）

**Circuit observation:** From Fig 6, current $I_X$ flows into *both* BJT collector terminals at their shared connection.（**电路观察：** 由图 6，电流 $I_X$ 在共用连接处流入*两个* BJT 的集电极。）

**Mathematical translation:** This is a classic KCL application! At the shared collector node:（**数学翻译：** 这是典型的 KCL 应用！在共用集电极节点：）

$$
\boxed{\text{Current in = Current out}} \Rightarrow \boxed{I_X = I_{C1} + I_{C2}}
$$

*Note:* Don't assume $I_X = I_{C1} = I_{C2}$. They are different currents related by KCL.（*注意：* 不要假设 $I_X=I_{C1}=I_{C2}$，它们是由 KCL 联系的不同电流。）
Using KCL at the shared collector node (blue = known, red = unknown):（在共用集电极节点使用 KCL（蓝色为已知量，红色为未知量）：）

$$
I_X = I_{C1} + I_{C2} \tag{12}
$$

Note that we are trying to find either $V_B$, $V_{BE1}$ or $V_{BE2}$ for this question (they are all equal).（注意本题要求的是 $V_B$、$V_{BE1}$ 或 $V_{BE2}$ 中的任意一个（三者相等）。） 

Currently, $I_{C1}$ and $I_{C2}$ are unknown, but for BJTs, the collector currents $I_{C1}$ and $I_{C2}$ can easily be related to $V_{BE1}$ and $V_{BE2}$ using the exponential $I_C$ relation:（目前 $I_{C1}$、$I_{C2}$ 未知，但 BJT 的集电极电流可以用指数型 $I_C$ 关系与 $V_{BE1}$、$V_{BE2}$ 联系起来：）

$$
I_C = I_S\left[\exp\left(\frac{V_{BE}}{V_T}\right)-1\right] \tag{13}
$$

Substituting the above (13) into our expression for $I_X$ in (12) gives us a more direct relation between known variables and the variables we are solving for:（把上面的 (13) 代入 (12) 中 $I_X$ 的表达式，可得到已知量与待求量之间更直接的关系：）

$$
I_X = I_{S1}\left[\exp\left(\frac{V_{BE1}}{V_T}\right)-1\right] + I_{S2}\left[\exp\left(\frac{V_{BE2}}{V_T}\right)-1\right] \tag{14}
$$

Expect to make this substitution for many (but not all) BJT circuits, as making this substitution describes the non-linear behaviour of the BJT in the circuit, capturing this behaviour into the math.（许多（但并非全部）BJT 电路都需要做这一步代入，因为它把 BJT 的非线性特性写进了数学模型。）

**Counting Unknowns:** Looking at the color-coding in (14), we initially have two red unknowns: $V_{BE1}$ and $V_{BE2}$.（**清点未知量：** 看 (14) 的颜色标记，最初有两个红色未知量 $V_{BE1}$ 与 $V_{BE2}$。） 

However, from our circuit analysis, we know that $V_{BE1} = V_{BE2} = V_B$ (both emitters grounded).（但由电路分析可知 $V_{BE1}=V_{BE2}=V_B$（两发射极均接地）。） This reduces our problem to just one unknown, which means we can solve it!（于是问题只剩一个未知量，可以求解了！）

$$
I_X = I_{S1}\left[\exp\left(\frac{V_B}{V_T}\right)-1\right] + \tfrac{1}{2}I_{S1}\left[\exp\left(\frac{V_B}{V_T}\right)-1\right] \tag{15}
$$

In the above, we used $V_B = V_{BE1} = V_{BE2}$ and $I_{S2} = \frac{1}{2}I_{S1}$.（上式中用了 $V_B=V_{BE1}=V_{BE2}$ 与 $I_{S2}=\frac12I_{S1}$。） It is helpful to simplify the expression now and leave substituting values until the end:（先化简表达式、最后再代数值会更有帮助：）

$$
\begin{aligned}
I_X &= I_{S1}\left(1+\tfrac{1}{2}\right)\left[\exp\left(\frac{V_B}{V_T}\right)-1\right] \\
\exp\left(\frac{V_B}{V_T}\right) - 1 &= \frac{I_X}{I_{S1}\left(1+\tfrac{1}{2}\right)} \\
\exp\left(\frac{V_B}{V_T}\right) &= \frac{I_X}{I_{S1}\left(1+\tfrac{1}{2}\right)} + 1 \\
\frac{V_B}{V_T} &= \ln\left(\frac{I_X}{I_{S1}\left(1+\tfrac{1}{2}\right)}+1\right) \\
V_B &= V_T\ln\left(\frac{I_X}{I_{S1}\left(1+\tfrac{1}{2}\right)}+1\right)
\end{aligned} \tag{16}
$$

Substituting the known values from the question gives:（代入题目给出的已知值：）

$$
\begin{aligned}
V_B &= (0.026\ \mathrm{V})\ln\left(\frac{1.2\ \mathrm{mA}}{(5 \times 10^{-16}\ \mathrm{A})\left(1+\tfrac{1}{2}\right)}+1\right) \\
V_B &= 0.731\ \mathrm{V}
\end{aligned} \tag{17}
$$

> [!tip] Engineering Approximation Tip（工程近似技巧）
> **About the "-1" term in the BJT equation:**（关于 BJT 方程中的“-1”项：）
> Notice we used $I_C = I_S[\exp(V_{BE}/V_T)-1]$ throughout this section.（注意本节一直使用 $I_C=I_S[\exp(V_{BE}/V_T)-1]$。） 
> 
> However, when the transistor is "on" (forward-biased with $V_{BE} \approx 0.7$ V), the exponential term becomes very large:（然而，当晶体管“导通”（正偏，$V_{BE}\approx0.7$ V）时，指数项会非常大：）
>
> $$
> \exp\left(\frac{0.7\ \mathrm{V}}{0.026\ \mathrm{V}}\right) = \exp(26.9) \approx 4.9 \times 10^{11}
> $$
>
> In this case, subtracting 1 from such a large number is negligible:（在这种情况下，从这么大的数中减去 1 可以忽略：）
>
> $$
> 4.9 \times 10^{11} - 1 \approx 4.9 \times 10^{11}
> $$
>
> **Practical rule:** When $V_{BE} \gg V_T$ (transistor clearly "on"), we can use the simplified form:（**实用规则：** 当 $V_{BE}\gg V_T$（晶体管明显导通）时，可用简化式：）
>
> $$
> I_C \approx I_S\exp\left(\frac{V_{BE}}{V_T}\right)
> $$
>
> **Try it yourself:** Re-calculate this problem using the simplified equation without the "-1" term.（**自己试一下：** 用去掉“-1”项的简化式重算本题。） 
> 
> You should get the same answer within rounding precision!（在舍入精度内应得到相同答案！） 
> 
> This approximation is commonly used in practical BJT circuit analysis.（实际 BJT 电路分析中常采用这一近似。）

## 3 Question 3（第 3 题）

Consider the circuit below, assuming $\beta$ = 100, $V_T$ = 26 mV, and $I_S = 7 \times 10^{-16}$ A.（考虑下图电路，假设 $\beta=100$、$V_T=26$ mV、$I_S=7\times10^{-16}$ A。） If $R_1 = 10$ k$\Omega$, determine $V_S$ such that $I_C$ = 1 mA.（若 $R_1=10$ kΩ，求使 $I_C=1$ mA 的 $V_S$。）

![](Pasted%20image%2020261111234958.png)
> 图7 Q3 circuit diagram（图 7：第 3 题电路图）

Solution:（**解答：**）

Key to solving this question is relating the source voltage $V_S$ to the transistor using Ohm's Law on $R_1$ (see (5)) and finding both $I_B$ and $V_B$ through the standard BJT formulae, given $I_C$ = 1 mA.（本题的关键是：对 $R_1$ 用欧姆定律把源电压 $V_S$ 与晶体管联系起来（见 (5)），并在给定 $I_C=1$ mA 的条件下用标准 BJT 公式求出 $I_B$ 与 $V_B$。）

From the BJT current relationships, the base current $I_B$ can be written using the collector $I_C$ and the current gain term $\beta$:（由 BJT 电流关系，基极电流 $I_B$ 可用集电极电流 $I_C$ 与电流增益 $\beta$ 表示：）

$$
I_B = \frac{I_C}{\beta} = \frac{1 \times 10^{-3}\ \mathrm{A}}{100} = 1 \times 10^{-5}\ \mathrm{A}. \tag{1}
$$

For a BJT, the correlation between the voltage drop between base and emitter ($V_{BE}$) and the collector current ($I_C$) is:（对于 BJT，基极-发射极压降 $V_{BE}$ 与集电极电流 $I_C$ 的关系为：）

$$
I_C = I_S\left[\exp\left(\frac{V_{BE}}{V_T}\right)-1\right]. \tag{2}
$$

Rearranging (2) (and assuming $V_{BE} \gg V_T$ to omit the $-1$ term), we can get the expression of $V_{BE}$:（重排 (2)（并假设 $V_{BE}\gg V_T$，略去 $-1$ 项），可得 $V_{BE}$ 的表达式：）

$$
V_{BE} = V_T\ln\left(\frac{I_C}{I_S}\right). \tag{3}
$$

Substituting the values of $I_C$, $I_S$ and $V_T$, the value of $V_{BE}$ is determined:（代入 $I_C$、$I_S$、$V_T$ 的数值，即可确定 $V_{BE}$：）

$$
V_{BE} = (0.026\ \mathrm{V}) \cdot \ln\left(\frac{1 \times 10^{-3}\ \mathrm{A}}{7 \times 10^{-16}\ \mathrm{A}}\right) = 0.728\ \mathrm{V}. \tag{4}
$$

Next, applying Ohm's Law to the $R_1$ base resistor, we get:（接下来对基极电阻 $R_1$ 应用欧姆定律，得：）

$$
\frac{V_S - V_B}{R_1} = I_B \tag{5}
$$

As $V_E = 0$ V (emitter connected to ground), $V_{BE} = V_B - V_E = V_B$.（由于 $V_E=0$ V（发射极接地），有 $V_{BE}=V_B-V_E=V_B$。）
Rearranging (5) and substituting $V_B = V_{BE}$ and numerical values, we can determine $V_S$:（重排 (5)，代入 $V_B=V_{BE}$ 及数值，即可求出 $V_S$：）

$$
\begin{aligned}
V_S &= V_{BE} + I_B \cdot R_1 \\
&= 0.728\ \mathrm{V} + (1 \times 10^{-5}\ \mathrm{A})(1 \times 10^{4}\ \Omega) \\
&= 0.828\ \mathrm{V}.
\end{aligned} \tag{6}
$$

## 4 Question 4（第 4 题）

What is the transconductance of an npn transistor operating at 350 K and a collector current of（工作在 350 K、集电极电流为以下值的 npn 晶体管，其跨导是多少：）

- (a) 10 $\mathrm{\mu A}$，
- (b) 100 $\mathrm{\mu A}$，
- (c) 1 mA，
- (d) 10 mA？

- (e) Repeat for a pnp transistor.（对 pnp 晶体管重复上述计算。）

Solution:（**解答：**）

In a BJT, the transconductance $g_m$ is used to describe the sensitivity of the collector current $I_C$ to changes in the base-emitter voltage $V_{BE}$.（在 BJT 中，跨导 $g_m$ 用于描述集电极电流 $I_C$ 对基极-发射极电压 $V_{BE}$ 变化的敏感程度。） It is defined as:（其定义为：）

$$
g_m = \frac{I_C}{V_T} \tag{1}
$$

The thermal voltage at $T = 350$ K is:（$T=350$ K 时的热电压为：）

$$
V_T = \frac{kT}{q} = \frac{(1.38 \times 10^{-23}\ \mathrm{J/K})(350\ \mathrm{K})}{1.6 \times 10^{-19}\ \mathrm{C}} = 0.0302\ \mathrm{V} \tag{2}
$$

### 4.1 Part A（A 部分）

Taking $I_C = 10\ \mathrm{\mu A}$ and substituting into (1):（取 $I_C=10$ μA 代入 (1)：）

$$
g_m = \frac{10^{-5}}{0.0302} = 0.33\ \mathrm{mS}. \tag{3}
$$

### 4.2 Part B（B 部分）

For $I_C = 100\ \mathrm{\mu A}$,（取 $I_C=100$ μA，）

$$
g_m = \frac{10^{-4}}{0.0302} = 3.31\ \mathrm{mS}. \tag{4}
$$

### 4.3 Part C（C 部分）

For $I_C = 1$ mA,（取 $I_C=1$ mA，）

$$
g_m = \frac{10^{-3}}{0.0302} = 33.1\ \mathrm{mS}. \tag{5}
$$

### 4.4 Part D（D 部分）

For $I_C = 10$ mA,（取 $I_C=10$ mA，）

$$
g_m = \frac{10^{-2}}{0.0302} = 331\ \mathrm{mS}. \tag{6}
$$

### 4.5 Part E（E 部分）

The values of $g_m$ are identical for both npn and pnp transistors, since (1) depends only on the collector current $I_C$ and the thermal voltage $V_T$, and not on transistor polarity.（npn 与 pnp 晶体管的 $g_m$ 相同，因为 (1) 只取决于集电极电流 $I_C$ 与热电压 $V_T$，与晶体管极性无关。）

---

## 转换说明（非原文内容）

- **转换方式**：源 PDF 由 LaTeX + pdfTeX-1.40.26 生成，10 页，带完整文本层（21 270 字符）。正文句子、段落归属、列表层级用 `page.get_text("text", sort=True)` 校对；公式一律不取文本（分式、根号、上下标在文本层会被拆成碎片），改用 2 倍渲染页图（1224×1584）逐页读图重建，写成 LaTeX。
- **公式编号**：沿用原 PDF 编号，每道题从 (1) 重新开始；正文里的 “Taking (1) into (2)”、“Rearranging (9)”、“From (14), we can solve…” 等交叉引用保持原样。
- **公式分组**：原 PDF 中一组多行的推导（如 Q2 的 (16) 五步化简式、(17) 两行代入式、Q3 的 (6) 三行数值代入式、Part A 的三个已知量 (2)）各按一整组编号，此处用 `aligned` 写一个 `$$` 块、只在块末写一次 `\tag`。
- **插图**：按约定一律只写纯文本占位 `> 图N 图名`（图 1–7），不插入图片文件。其中图 3、图 5、图 6 在原 PDF 中引用的是同一张位图（xref=33，Q2 电路图重复放置三次），仍按原图注分别编号为 3、5、6，未合并、未改号。图 1（NPN/PNP 符号）与图 4（工作区象限图）在原 PDF 中分别是矢量绘图与位图，均只给占位。
- **彩色提示框**：原 PDF 有 4 个带底色的框——第 1 页 “Essential BJT Equations for Circuit Analysis”（绿）、第 4 页 “Important Note: $V_{BE}$ vs $V_B$”（红）与 “BJT Operating Regions (NPN)”（蓝）、第 8 页 “Engineering Approximation Tip”（绿）。现改用 Obsidian callout 表示：绿色框用 `[!tip]`，红色框用 `[!warning]`，蓝色框用 `[!info]`；框内内容（含公式与表格）整体缩进在 callout 中。
- **彩色公式**：第 7 页起 Q2 Part A 详细推导里，原 PDF 用蓝/红两种颜色区分“已知量/未知量”（如 (14)(15)(16)(17) 中的 $I_{S1}$、$V_{BE1}$、$V_B$ 等），Markdown 无法保留字体颜色，只保留文字说明 “(blue = known, red = unknown)”，公式本身按原式照录。第 7 页顶部 “Current in = Current out ⇒ $I_X = I_{C1}+I_{C2}$” 两个方框用 `\boxed{}` 还原。
- **表格**：第 4 页 “Region / Voltage Relationships (NPN)” 四行工作区条件表在原 PDF 中是排版表格（非图片），已转成 Markdown 表格，单元格内的两行文字用 `<br>` 分行。
- **原文照录**：正文句子、数值、单位一律按原 PDF 照抄，未作订正。两点纯排版差异需要说明——
  - 原文的撇号用的是弯引号（如 “you’ll”、“Ohm’s law”、“BJT’s”），Markdown 中统一排成直引号（'），文字本身未改。
  - 第 5 页 Answer 一行经 6 倍放大核对为 “$R_C = 1.47$ k$\Omega$ places both transistors at the edge of active mode ($V_C = V_B$)”，$\mathrm{k\Omega}$ 与 places 之间确有一个空格（文本层曾把它抽成 “kΩplaces”，此处以渲染图为准）。
