# ELEC2104/9704 Tutorial 9 Solutions (2025)

## Introduction to MOSFETs and Circuit Analysis（MOSFET 与电路分析简介）

### The MOSFET: A Voltage-Controlled Current Source（MOSFET：电压控制电流源）

The Metal-Oxide-Semiconductor Field-Effect Transistor (MOSFET) is the fundamental building block of modern electronics.（金属-氧化物-半导体场效应晶体管（MOSFET）是现代电子技术的基本器件。）

Unlike bipolar junction transistors (BJTs) which are current-controlled, MOSFETs are voltage-controlled devices - the gate voltage controls the drain current.（与电流控制的双极型晶体管（BJT）不同，MOSFET 是电压控制器件——栅极电压控制漏极电流。）

![](Pasted%20image%2020261114214602.png)
> 图1 MOSFET symbols showing both 4-terminal (with body) and 3-terminal configurations（图 1：MOSFET 符号，包括四端（带体）与三端两种形式）

> [!warning] Critical: Arrow Direction Confusion Between 4-Terminal and 3-Terminal Symbols（重要：四端与三端符号的箭头方向容易混淆）
>
> The arrow direction differs between 4-terminal and 3-terminal MOSFET symbols!（四端与三端 MOSFET 符号的箭头方向不同！）
>
> | Device（器件） | 4-Terminal Arrow（四端箭头） | 3-Terminal Arrow（三端箭头） |
> | --- | --- | --- |
> | NMOS | INTO body terminal（指向体端） | OUT OF source terminal（从源极向外） |
> | PMOS | OUT OF body terminal（从体端向外） | INTO source terminal（指向源极） |

### Understanding MOSFET Operation（理解 MOSFET 的工作）

#### The Physical Picture（物理图像）

When we apply a voltage to the gate (relative to the source), we create an electric field that attracts charge carriers to form a conductive channel between drain and source.（当在栅极（相对源极）加电压时，会产生电场，吸引载流子在漏极与源极之间形成导电沟道。）

This channel acts like a voltage-controlled resistor, allowing current to flow.（该沟道相当于一个电压控制电阻，允许电流通过。）

#### Key Parameters（主要参数）

- **Gate Current ($I_G = 0$):** is zero (in this course), as the gate is insulated by oxide.（**栅极电流（$I_G=0$）：** 本课程中为零，因为栅极被氧化物绝缘。）
- **Threshold Voltage ($V_{Th}$, $V_{TN}$ or $V_{TP}$):** Minimum gate voltage needed to form a channel（**阈值电压：** 形成沟道所需的最小栅极电压）
- **Transconductance Param. ($K_n$, $K_p$):** $K' = \mu C_{ox}$ ($\mu$ carrier mobility, $C_{ox}$ oxide capacitance)（**跨导参数：** $K'=\mu C_{ox}$（$\mu$ 为载流子迁移率，$C_{ox}$ 为氧化层电容））
- **Aspect Ratio ($W/L$):** Width-to-length ratio of the channel, controlling current capability（**宽长比：** 沟道宽度与长度之比，决定电流能力）
- **Channel Length Modulation ($\lambda$):** Accounts for slight dependence of $I_D$ on $V_{DS}$ in saturation（**沟道长度调制：** 描述饱和区 $I_D$ 对 $V_{DS}$ 的轻微依赖）

#### The Three Operating Regions（三个工作区）

A MOSFET's behavior changes dramatically depending on the applied voltages.（MOSFET 的特性随所加电压显著变化。）

Understanding these regions is crucial for circuit analysis.（理解这些工作区对电路分析至关重要。）

The Triode region is split into linear and non-linear parts.（三极管区又分为线性与非线性两部分。）

> [!info] MOSFET Operating Regions（MOSFET 工作区）
>
> 1. **Cutoff Region (NMOS: $V_{GS} < V_{TN}$)**（截止区）
>
>    - No channel formed, so acts like an open switch, $I_D = 0$ (device is OFF)（无沟道形成，相当于开路开关，$I_D=0$，器件截止）
>    - PMOS have negative $V_{GS}$ and $V_{TP}$, so the inequality is reversed: $V_{GS} > V_{TP}$（PMOS 的 $V_{GS}$ 与 $V_{TP}$ 均为负，故不等号反向：$V_{GS}>V_{TP}$）
>
> 2. **Triode Region (Linear) (NMOS: $V_{GS} > V_{TN}$ and $V_{DS} \ll 2(V_{GS} - V_{TN})$)（三极管区（线性））**
>
>    - Channel formed and continuous（沟道形成且连续）
>    - Current depends on both $V_{GS}$ and $V_{DS}$ linearly: $I_{D,\mathrm{tri}} = \mu_n C_{ox}\frac{W}{L}(V_{GS} - V_{TN})V_{DS}$（电流与 $V_{GS}$、$V_{DS}$ 均成线性关系）
>    - Acts like a voltage-controlled resistor: $R_{on} = \dfrac{1}{\mu_n C_{ox}\frac{W}{L}(V_{GS} - V_{TN})}$（相当于电压控制电阻）
>
> 3. **Triode Region (Non-linear) (NMOS: $V_{GS} > V_{TN}$ and $V_{DS} < V_{GS} - V_{TN}$)**（三极管区（非线性））
>
>    - The channel is still continuous but starts to pinch off near the drain（沟道仍连续，但在漏极附近开始夹断）
>    - Nonlinear dependence on $V_{GS}$, $V_{DS}$: $I_{D,\mathrm{tri}} = \frac{1}{2}\mu_n C_{ox}\frac{W}{L}\left[2(V_{GS} - V_{TN})V_{DS} - V_{DS}^2\right]$（对 $V_{GS}$、$V_{DS}$ 呈非线性关系）
>    - Acts like a voltage-controlled current source（相当于电压控制电流源）
>    - PMOS: negative voltages (so reversed inequalities) $V_{GS} < V_{TP}$ and $V_{DS} > V_{GS} - V_{TP}$（PMOS：电压为负，故不等号反向）
>
> 4. **Saturation Region (NMOS: $V_{GS} > V_{TN}$ and $V_{DS} \geq V_{GS} - V_{TN}$)**（饱和区）
>
>    - Channel pinched off near drain（漏极附近沟道夹断）
>    - Current mainly depends on $V_{GS}$: $I_{D,\mathrm{sat}} = \frac{1}{2}\mu_n C_{ox}\frac{W}{L}(V_{GS} - V_{TN})^2(1 + \lambda V_{DS})$（电流主要取决于 $V_{GS}$）
>    - Acts like a voltage-controlled current source（相当于电压控制电流源）
>    - PMOS: negative voltages (so reversed inequalities) $V_{GS} < V_{TP}$ and $V_{DS} \leq V_{GS} - V_{TP}$（PMOS：电压为负，故不等号反向）
>    - **Remember this one!**（记住这一条！）

**Don't confuse the BJT saturation region with the MOSFET saturation region!**（不要把 BJT 的饱和区与 MOSFET 的饱和区混淆！）

We use the MOSFET saturation region for amplification, while BJT saturation is for switching, not amplifying.（MOSFET 的饱和区用于放大，而 BJT 的饱和区用于开关，不用于放大。）

### Analyzing MOSFET Circuits: The Load Line Method（分析 MOSFET 电路：负载线法）

When we place a MOSFET in a circuit with resistors and voltage sources, we need a systematic way to find the operating point.（当把 MOSFET 与电阻、电压源接入电路时，需要一种系统的方法来确定工作点。）

This is where load line analysis becomes powerful.（这正是负载线分析发挥作用的地方。）

#### What is a Load Line?（什么是负载线？）

The load line represents the constraint imposed by the external circuit.（负载线表示外部电路施加的约束。）

It's called a "load" line because it typically represents the load (resistance) connected to the MOSFET.（称其为“负载”线，是因为它通常代表接在 MOSFET 上的负载（电阻）。）

Consider this fundamental circuit:（考虑下面这个基本电路：）

![](Pasted%20image%2020261114214619.png)
> 图2 Basic MOSFET circuit for load line analysis（图 2：用于负载线分析的基本 MOSFET 电路）

Applying Kirchhoff's Voltage Law (KVL) around the drain-source loop:（对漏源回路应用基尔霍夫电压定律（KVL）：）

$$
V_{DD} = I_D R_D + V_{DS} \tag{1}
$$

Rearranging to get the load line equation:（重排得到负载线方程：）

$$
I_D = \frac{V_{DD} - V_{DS}}{R_D} \tag{2}
$$

On the $I_D$ versus $V_D$ plot, this is a straight line with:（在 $I_D$–$V_D$ 图上，这是一条直线，其：）

- Y-intercept (when $V_{DS} = 0$): $I_D = \dfrac{V_{DD}}{R_D}$ (maximum possible current)（纵轴截距（$V_{DS}=0$ 时）：$I_D=\dfrac{V_{DD}}{R_D}$，即最大可能电流）
- X-intercept (when $I_D = 0$): $V_{DS} = V_{DD}$ (maximum possible voltage)（横轴截距（$I_D=0$ 时）：$V_{DS}=V_{DD}$，即最大可能电压）
- Slope: $-\dfrac{1}{R_D}$ (determined by load resistance)（斜率：$-\dfrac{1}{R_D}$，由负载电阻决定）

#### Graphical Solution: Where Device Meets Circuit（图解：器件特性与电路约束的交点）

The beauty of load line analysis is that it provides a visual solution.（负载线分析的优点在于给出直观的图解。）

The operating point (Q-point) is where the load line intersects the MOSFET characteristic curve.（工作点（Q 点）就是负载线与 MOSFET 特性曲线的交点。）

![](Pasted%20image%2020261114214635.png)
> 图3 Load line intersecting with MOSFET characteristics to find Q-point（图 3：负载线与 MOSFET 特性曲线相交求 Q 点）

### Solution Strategy（解题策略）

> [!tip] Systematic MOSFET Circuit Analysis（系统的 MOSFET 电路分析）
>
> **Step 1: Simplify the Circuit to get Load Line Equation**（第 1 步：化简电路，得到负载线方程）
>
> - Find Th&eacute;venin equivalents for bias networks if necessary (e.g. 4-Resistor Bias Network)（必要时求偏置网络的戴维南等效，例如四电阻偏置网络）
> - Identify circuit constraints (KVL, KCL). E.g., KVL loops involving $V_{DS}$ or $V_{GS}$.（确定电路约束（KVL、KCL），例如含 $V_{DS}$ 或 $V_{GS}$ 的 KVL 回路。）
> - Use $I_G = 0$ to simplify analysis.（利用 $I_G=0$ 简化分析。）
>
> **Step 2: Assume Operating Region to get MOSFET Equation**（第 2 步：假设工作区，写出对应的 MOSFET 方程）
>
> - For amplifiers: usually saturation (common in this course)（对放大器通常假设饱和区（本课程常见））
> - Write the corresponding $I_D$ equation for this region（写出该工作区对应的 $I_D$ 方程）
>
> **Step 3: Solve Load Line and MOSFET Equations Simultaneously**（第 3 步：联立求解负载线与 MOSFET 方程）
>
> - Combine MOSFET equation with circuit constraints (i.e. load line equation)（把 MOSFET 方程与电路约束（即负载线方程）联立）
> - Solve with the quadratic equation, keep the physically meaningful solution（用二次方程求解，保留有物理意义的解）
>   - Choose a solution that satisfies the region conditions in Step 4 (if there is one).（选择满足第 4 步工作区条件的解（若有）。）
>
> **Step 4: Verify Assumption**（第 4 步：验证假设）
>
> - Check region conditions:（检查工作区条件：）
>   - Saturation: $V_{GS} > V_{TN}$ and $V_{DS} > V_{GS} - V_{TN}$ (NMOS)（饱和区）
>   - Triode: $V_{GS} > V_{TN}$ and $V_{DS} < V_{GS} - V_{TN}$ (NMOS)（三极管区）
> - If wrong, return to Step 2 with new assumption（若不成立，换假设返回第 2 步）
>
> **Step 5: Find Q-Point**（第 5 步：求 Q 点）
>
> - Calculate final values to get $Q = (I_D, V_{DS})$, returning to circuit analysis if necessary.（计算最终数值，得到 $Q=(I_D,V_{DS})$，必要时回到电路分析。）
> - This is your DC operating point（这就是直流工作点）

### Advanced Topics（进阶内容）

#### Channel Length Modulation（沟道长度调制）

In saturation, the effective channel length decreases slightly with increasing $V_{DS}$, causing a small increase in current:（在饱和区，有效沟道长度随 $V_{DS}$ 增大而略微减小，使电流略有增加：）

$$
I_D = \frac{1}{2}\mu_n C_{ox}\frac{W}{L}(V_{GS} - V_{TN})^2(1 + \lambda V_{DS}) \tag{3}
$$

This makes the saturation curves slightly upward-sloping rather than perfectly flat.（这使饱和区曲线略微上翘，而不是完全水平。）
**Default:** For most problems, we ignore $\lambda$ (set $\lambda = 0$) unless specified otherwise.（**默认：** 多数问题中忽略 $\lambda$（取 $\lambda=0$），除非另有说明。）

#### Body Effect（体效应）

MOSFETs actually have a 4th terminal called the "Body", which is typically just connected to the source and so is not shown (see Q2).（MOSFET 实际上有第四个端子，称为“体”，通常直接与源极相连，因此图中不画出（见第 2 题）。）

However, when the source is not connected to the body (substrate), we must take the "Body Effect" into account, where the threshold voltage increases.（然而，当源极不与体（衬底）相连时，必须考虑“体效应”，此时阈值电压升高。）

For NMOS:（对 NMOS：）

$$
V_{TN} = V_{T0} + \gamma\sqrt{V_{SB} + 2\phi_F} - \sqrt{2\phi_F} \tag{4}
$$

For PMOS:（对 PMOS：）

$$
V_{TP} = V_{T0} - \gamma\sqrt{V_{BS} + 2\phi_F} - \sqrt{2\phi_F} \tag{5}
$$

**Note the negative sign before $\gamma$ for PMOS!**（注意 PMOS 式中 $\gamma$ 前为负号！）

This is because increasing $V_{BS}$ increases the magnitude of the threshold voltage (makes it more negative).（这是因为 $V_{BS}$ 增大时阈值电压的幅值增大（变得更负）。）

Where:（式中：）

- $V_{T0}$: Zero-bias threshold voltage（零偏阈值电压）
- $\gamma$: Body effect parameter（体效应参数）
- $V_{SB}$ / $V_{BS}$: Source-to-body voltage / body-to-source voltage（源-体电压 / 体-源电压）
- $2\phi_F$: Surface potential parameter ($2\Psi_F$ in the lectures)（表面势参数（课堂上记为 $2\Psi_F$））

This creates an implicit equation since $V_{SB} = I_D R_3$ in many circuits, requiring iterative solution.（由于许多电路中 $V_{SB}=I_D R_3$，这形成隐式方程，需要迭代求解。）

**Tip:** You can check the magnitude of the threshold voltage for either NMOS and PMOS, with a unified formula:（**提示：** 可用统一公式计算 NMOS 与 PMOS 的阈值电压幅值：）

$$
|V_{Th}| = |V_{T0}| + \gamma\sqrt{|V_{SB}| + 2\phi_F} - \sqrt{2\phi_F} \tag{6}
$$

Remember to make your answer for $|V_{Th}|$ negative if its PMOS (i.e. $V_{TP}$).（若为 PMOS，记得把 $|V_{Th}|$ 的答案取负（即 $V_{TP}$）。）

> [!warning] Threshold Voltage Notation（阈值电压符号说明）
>
> **Important:** Don't confuse MOSFET threshold voltages with BJT thermal voltage $V_T$!（**重要：** 不要把 MOSFET 的阈值电压与 BJT 的热电压 $V_T$ 混淆！）
>
> - $V_{TN}$ = NMOS threshold voltage (typically positive, e.g., +0.75 V)（NMOS 阈值电压，通常为正，如 +0.75 V）
> - $V_{TP}$ = PMOS threshold voltage (typically negative, e.g., -0.75 V)（PMOS 阈值电压，通常为负，如 -0.75 V）
> - $V_{Th}$ = MOSFET threshold voltage (generic symbol, either NMOS or PMOS)（MOSFET 阈值电压的通用符号，可表示 NMOS 或 PMOS）
> - $V_{Th0}$ or $V_{T0}$ = Zero-bias threshold voltage (when $V_{SB} = 0$ or $V_{BS} = 0$)（零偏阈值电压（$V_{SB}=0$ 或 $V_{BS}=0$ 时））
>
> **Note:** When there's no body effect, $V_{TN} = V_{T0}$ for NMOS and $V_{TP} = V_{T0}$ for PMOS.（**注：** 无体效应时，NMOS 的 $V_{TN}=V_{T0}$，PMOS 的 $V_{TP}=V_{T0}$。）

![](Pasted%20image%2020261114214702.png)****
> 图I-1（位于下框内，原书未编号）3 端 MOSFET 符号：NMOS（3-terminal，箭头由源极向外）与 PMOS（3-terminal，箭头指向源极）（图 I-1：三端 MOSFET 符号，NMOS 箭头由源极向外，PMOS 箭头指向源极）

> [!info] Three-Terminal Symbol Convention（三端符号约定）
>
> Whenever you see a 3-terminal MOSFET symbol (without an explicit body connection), it is implied that:（当看到三端 MOSFET 符号（未明确画出体端）时，隐含以下条件：）
>
> - The body is internally connected to the source（体在内部与源极相连）
> - Therefore, $V_{BS} = 0$ (for PMOS) or $V_{SB} = 0$ (for NMOS)（因此 PMOS 的 $V_{BS}=0$，NMOS 的 $V_{SB}=0$）
> - There is no body effect ($V_{TN}$ or $V_{TP}$ remains constant)（无体效应，$V_{TN}$ 或 $V_{TP}$ 保持不变）
> - This is the most common configuration in basic circuits（这是基本电路中最常见的接法）
>
> Only when you see the 4-terminal symbol with a separate body connection and $V_{SB} \neq 0$ (or $V_{BS} \neq 0$) and $\gamma \neq 0$, should you consider body effect!（只有当出现四端符号、体端单独连接且 $V_{SB}\neq0$（或 $V_{BS}\neq0$）、$\gamma\neq0$ 时，才需要考虑体效应！）

#### Effect of W/L Ratio（宽长比的影响）

The aspect ratio directly scales the current capability:（宽长比直接按比例决定电流能力：）

- Doubling $W/L$ doubles the saturation current（$W/L$ 加倍，饱和电流加倍）
- Allows designer to size transistors for required current（设计者可据此选择晶体管尺寸以获得所需电流）
- Trade-off: larger devices consume more area and have higher capacitance（代价：器件越大，占用面积越大、电容越大）

> [!tip] Design Insight（设计要点）
>
> In the tutorial problems, notice how changing $W/L$ from 6/1 to 12/1 (Question 4) shifts the Q-point along the load line.（在本辅导课的题目中，注意 $W/L$ 从 6/1 变为 12/1（第 4 题）时，Q 点沿负载线移动。）
>
> The load line stays fixed (determined by external resistors), but the MOSFET curves change, moving the intersection point.（负载线保持不变（由外部电阻决定），但 MOSFET 曲线改变，从而移动交点。）

### Connecting Theory to Practice（理论联系实际）

As you work through the tutorial problems, you'll see these concepts in action:（做本辅导课的题目时，会看到这些概念的实际应用：）

1. Question 1: Self-biased configuration with load line analysis（第 1 题：自偏置电路与负载线分析）
2. Question 2: PMOS with body effect（第 2 题：考虑体效应的 PMOS）
3. Question 3: Transmission gate (parallel NMOS/PMOS)（第 3 题：传输门（NMOS/PMOS 并联））
4. Questions 4-5: Four-resistor bias with varying parameters（第 4、5 题：参数变化的四电阻偏置）

Each problem reinforces the fundamental principle: the Q-point is where the device physics (MOSFET equations) meets the circuit constraints (load line).（每题都强化一个基本原则：Q 点是器件物理（MOSFET 方程）与电路约束（负载线）的交点。）

### Summary: The Big Picture（总结：整体思路）

MOSFETs are voltage-controlled devices that form the backbone of modern electronics.（MOSFET 是电压控制器件，是现代电子技术的基础。）

Understanding their operation requires:（理解其工作需要：）

- Recognizing the three operating regions and their equations（识别三个工作区及其方程）
- Using load line analysis to find the Q-point graphically（用负载线分析图解求 Q 点）
- Applying systematic solution strategies for different bias configurations（对不同偏置结构采用系统的求解策略）
- Accounting for second-order effects when precision matters（在需要精度时考虑二阶效应）

The load line method bridges the gap between device physics and circuit behavior, providing both mathematical rigor and intuitive understanding.（负载线法连接了器件物理与电路行为，兼有数学严谨性与直观性。）

Master this technique, and you'll have a powerful tool for analyzing and designing MOSFET circuits.（掌握这一方法，就有了分析和设计 MOSFET 电路的有力工具。）

## 1 Question 1（第 1 题）

(a) Find the drain current for the transistor if $\lambda = 0$.（(a) 若 $\lambda=0$，求该晶体管的漏极电流。）

(b) Repeat if the $W/L$ ratio is changed to 25/1.（(b) 若 $W/L$ 改为 25/1，重做。）

![](Pasted%20image%2020261114214715.png)
> 图Q1-1 题 1 电路：$+12$ V 经 $100$ k$\Omega$（$R_D$）接漏极，栅极与漏极短接（自偏置，$V_{GS}=V_{DS}$），源极接地；$W/L = 10/1$（图 Q1-1：第 1 题电路）

**Solution:**（**解答：**）

### 1.1 Part A（A 部分）

Note that $\lambda = 0$ means we are neglecting channel length modulation, simplifying our analysis by assuming the drain current is independent of $V_{DS}$ in saturation.（注意 $\lambda=0$ 表示忽略沟道长度调制，即假设饱和区漏极电流与 $V_{DS}$ 无关，从而简化分析。）

Looking at the circuit, we can identify this as an NMOS transistor (the arrow on the source points outward).（观察电路，可判断这是 NMOS 晶体管（源极上的箭头向外）。）

Another thing to note is that the gate is connected directly to the drain $D$, creating a self-biased configuration where $V_{GS} = V_{DS}$.（另需注意，栅极直接与漏极 $D$ 相连，构成 $V_{GS}=V_{DS}$ 的自偏置电路。）

This special configuration guarantees the transistor operates in saturation since:（该特殊接法保证晶体管工作在饱和区，因为：）

$$
V_{DS} = V_{GS} > V_{GS} - V_{TN} \quad (\text{always true as } V_{TN} \text{ is positive})
$$

For an NMOS in saturation with $\lambda = 0$, the drain current equation is:（对 $\lambda=0$ 的饱和区 NMOS，漏极电流方程为：）

$$
I_D = \frac{1}{2}\mu_n C_{ox}\left(\frac{W}{L}\right)(V_{GS} - V_{TN})^2 \tag{1}
$$

To find the load line equation, we apply KVL around the drain-source loop:（为求负载线方程，对漏源回路应用 KVL：）

$$
V_{DD} = I_D R_D + V_{DS}
$$

where $V_{DD} = +12$ V and $R_D = 100$ k$\Omega$.（其中 $V_{DD}=+12$ V，$R_D=100$ k$\Omega$。）

Solving for $I_D$ gives Ohm's law:（解出 $I_D$ 即得欧姆定律形式：）

$$
I_D = \frac{V_{DD} - V_{DS}}{R_D}
$$

Since the gate is connected to the drain in this circuit, we have $V_{DS} = V_{GS}$, therefore:（由于本电路栅极与漏极相连，故 $V_{DS}=V_{GS}$，因此：）

$$
I_D = \frac{12\ \text{V} - V_{DS}}{100\ \text{k}\Omega} = \frac{12\ \text{V} - V_{GS}}{100\ \text{k}\Omega} \tag{2}
$$

Equating equations (1) and (2), we can solve for $V_{GS}$:（令式 (1) 与 (2) 相等，即可解出 $V_{GS}$：）

$$
\frac{1}{2}(\mu_n C_{ox})\left(\frac{W}{L}\right)(V_{GS} - V_{TN})^2 = \frac{12\ \text{V} - V_{GS}}{100\ \text{k}\Omega} \tag{3}
$$

This reduces to（化简为）

$$
12.5V_{GS}^2 - 17.8V_{GS} - 4.97 = 0 \tag{4}
$$

The quadratic formula gives two solutions:（由二次公式得两个解：）

$$
V_{GS} = 0.2\ \text{V} \text{ or } 1.2\ \text{V} \tag{5}
$$

We need to check which solution is physically valid.（需要检验哪个解有物理意义。）

For the NMOS to be ON and in saturation:（NMOS 导通且处于饱和区需满足：）

- We need $V_{GS} > V_{TN} = +0.75$ V (transistor ON)（需 $V_{GS}>V_{TN}=+0.75$ V，晶体管导通）
- The solution $V_{GS} = 0.2$ V $< V_{TN}$ would put the transistor in cutoff (OFF)（$V_{GS}=0.2$ V $<V_{TN}$，会使晶体管进入截止区）
- Only the solution $V_{GS} = 1.2$ V $> V_{TN}$ is valid（只有 $V_{GS}=1.2$ V $>V_{TN}$ 的解有效）

Therefore, the operating point is $V_{GS} = 1.2$ V, giving:（因此工作点为 $V_{GS}=1.2$ V，于是：）

$$
I_D = \frac{12\ \text{V} - 1.2\ \text{V}}{100\ \text{k}\Omega} = \frac{10.8\ \text{V}}{100\ \text{k}\Omega} = 108\ \mu\text{A} \tag{6}
$$

### 1.2 Part B（B 部分）

Following the same procedure, we assume saturation.（按同样步骤，假设工作在饱和区。）

Starting from the load line equation (2) and using the new aspect ratio $W/L = 25/1$:（从负载线方程 (2) 出发，取新的宽长比 $W/L=25/1$：）

$$
\frac{1}{2}(\mu_n C_{ox})\left(\frac{25}{1}\right)(V_{GS} - V_{TN})^2 = \frac{12\ \text{V} - V_{GS}}{100\ \text{k}\Omega} \tag{7}
$$

Simplifying this quadratic equation, we can get（化简该二次方程，得）

$$
62.5V_{GS}^2 - 91.75V_{GS} + 11.16 = 0 \tag{8}
$$

Then the solutions are（解得）

$$
V_{GS} = 0.46\ \text{V} \text{ or } 1.046\ \text{V} \tag{9}
$$

Again checking validity:（再次检验有效性：）

- $V_{GS} = 0.46$ V $< V_{TN} = 0.75$ V (cutoff - invalid)（截止区，无效）
- $V_{GS} = 1.046$ V $> V_{TN}$ (saturation - valid)（饱和区，有效）

The operating point is $V_{GS} = 1.046$ V, giving:（工作点为 $V_{GS}=1.046$ V，于是：）

$$
I_D = \frac{12\ \text{V} - 1.046\ \text{V}}{100\ \text{k}\Omega} = \frac{10.954\ \text{V}}{100\ \text{k}\Omega} = 110\ \mu\text{A} \tag{10}
$$

Note that increasing $W/L$ from 6/1 to 25/1 increased the drain current slightly.（注意 $W/L$ 从 6/1 增至 25/1 后，漏极电流略有增大。）

## 2 Question 2（第 2 题）

A PMOS transistor is operating with $V_{BS} = 4$ V, $V_{GS} = -1.5$ V, and $V_{DS} = -4$ V.（一个 PMOS 晶体管工作在 $V_{BS}=4$ V、$V_{GS}=-1.5$ V、$V_{DS}=-4$ V。）

What is the region of operation and drain current in this device if $W/L = 25/1$?（若 $W/L=25/1$，该器件的工作区和漏极电流是多少？）

![](Pasted%20image%2020261114214731.png)
> 图Q2-1 PMOS 符号（手绘）：D 在上、S 在下、G 在左、B 在右侧（图 Q2-1：PMOS 符号）

**PMOS Sign Conventions:**（**PMOS 符号约定：**） For PMOS transistors, we use a different sign convention than NMOS:（对 PMOS，采用与 NMOS 不同的符号约定：）

- All voltages are typically negative relative to the source (which is usually at the highest potential),（所有电压相对源极通常为负（源极通常处于最高电位），）
- This is unlike BJT PNP transistors which use "flipped" subscripts (e.g., $V_{EB}$ instead of $V_{BE}$), MOSFETs maintain consistent subscript ordering (e.g., $V_{GS}$, $V_{DS}$) for both NMOS and PMOS.（这一点与 BJT 的 PNP 管不同：后者采用“翻转”的下标（如用 $V_{EB}$ 代替 $V_{BE}$），而 MOSFET 对 NMOS 与 PMOS 都保持相同的下标顺序（如 $V_{GS}$、$V_{DS}$）。）
- Exception: For body effect, we *can* use $V_{BS}$ (body-to-source) for PMOS (versus $V_{SB}$ for NMOS).（例外：讨论体效应时，PMOS 可用 $V_{BS}$（体到源），而 NMOS 用 $V_{SB}$。）

**Solution:**（**解答：**）

Since $V_{BS} = 4$ V $\neq 0$, the body cannot be short-circuited to the source and thus we must include the body effect.（由于 $V_{BS}=4$ V $\neq0$，体不能与源极短接，因此必须考虑体效应。）

The threshold voltage for the PMOS, $V_{TP}$ is:（PMOS 的阈值电压 $V_{TP}$ 为：）

$$
V_{TP} = V_{T0} - \gamma\left(\sqrt{V_{BS} + 2\phi_F} - \sqrt{2\phi_F}\right) \tag{1}
$$

Using the PMOS parameters from the tutorial parameter section (note that PMOS typically has different parameters than NMOS):（使用辅导课参数表中的 PMOS 参数（注意 PMOS 参数通常与 NMOS 不同）：）

- $V_{T0} = -0.75$ V (zero-bias threshold voltage for PMOS)（PMOS 的零偏阈值电压）
- $\gamma = 0.5\sqrt{\text{V}}$ (body effect parameter)（体效应参数）
- $2\phi_F = 0.6$ V (surface potential parameter, $2\Psi_F$ in the lectures)（表面势参数，课堂上记为 $2\Psi_F$）

With PMOS we deal with a lot of negatives!（PMOS 中会出现很多负号！）

Substituting these values:（代入这些数值：）

$$
V_{TP} = -0.75\ \text{V} - 0.5\sqrt{\text{V}}\left(\sqrt{4\ \text{V} + 0.6\ \text{V}} - \sqrt{0.6\ \text{V}}\right) = -1.44\ \text{V} \tag{2}
$$

Now we check the region of operation to select the proper drain current formula.（现在判断工作区，以选择正确的漏极电流公式。）

For PMOS:（对 PMOS：）

- **ON condition:** $V_{GS} < V_{TP}$ ($V_{GS}$ more negative than threshold)（**导通条件：** $V_{GS}<V_{TP}$，即 $V_{GS}$ 比阈值更负）
- **Triode region:** $V_{DS} > V_{GS} - V_{TP}$ ($V_{DS}$ less negative)（**三极管区：** $V_{DS}>V_{GS}-V_{TP}$，即 $V_{DS}$ 负得较少）
- **Saturation region:** $V_{DS} < V_{GS} - V_{TP}$ ($V_{DS}$ more negative)（**饱和区：** $V_{DS}<V_{GS}-V_{TP}$，即 $V_{DS}$ 更负）

Checking our values:（检验数值：）

$$
V_{GS} = -1.5\ \text{V} < V_{TP} = -1.44\ \text{V} \ \ \checkmark \text{(ON)} \tag{3}
$$

$$
V_{DS} = -4\ \text{V} < V_{GS} - V_{TP} = -1.5\ \text{V} - (-1.44\ \text{V}) = -0.06\ \text{V} \ \ \checkmark \text{(Saturation)} \tag{4}
$$

Therefore, the PMOS operates in the **saturation region**.（因此，该 PMOS 工作在**饱和区**。）

The saturation drain current formula for PMOS (without channel-length modulation effect $\lambda = 0$) is:（PMOS 的饱和区漏极电流公式（忽略沟道长度调制，$\lambda=0$）为：）

$$
I_D = \frac{1}{2}K_p'\left(\frac{W}{L}\right)(V_{GS} - V_{TP})^2 \tag{5}
$$

Substituting our values (note that $K_p' = \mu_p C_{ox}$ for PMOS):（代入数值（注意 PMOS 的 $K_p'=\mu_p C_{ox}$）：）

$$
I_D = \frac{1}{2}(40 \times 10^{-6}\ \text{A/V}^2)(25)[(-1.5\ \text{V}) - (-1.44\ \text{V})]^2 \tag{6}
$$

$$
= \frac{1}{2}(40 \times 10^{-6}\ \text{A/V}^2)(25)(-0.06\ \text{V})^2 \tag{7}
$$

$$
= 1.8\ \mu\text{A} \tag{8}
$$

## 3 Question 3（第 3 题）

What is the on-resistance and voltage $V_O$ for the parallel combination of the NMOS ($W/L = 10/1$) and PMOS ($W/L = 25/1$) transistors in a *transmission gate*?（在*传输门*中，NMOS（$W/L=10/1$）与 PMOS（$W/L=25/1$）并联时，导通电阻和电压 $V_O$ 是多少？）

(a) For $V_{IN} = 0$ V?（(a) 当 $V_{IN}=0$ V 时？）

(b) For $V_{IN} = 5$ V?（(b) 当 $V_{IN}=5$ V 时？）

![](Pasted%20image%2020261114214746.png)
> 图Q3-1 题 3 的传输门电路：上管为 PMOS（源极接 $+5$ V，栅极接 $+5$ V），下管为 NMOS（栅极接 $+5$ V，另一端接 $0$ V），两管漏极并联接 $V_{IN}$ 与 $V_O$（图 Q3-1：第 3 题传输门电路）

**Background:**（**背景：**） A transmission gate is a bidirectional switch that uses complementary NMOS and PMOS transistors in parallel.（传输门是一种双向开关，由互补的 NMOS 与 PMOS 并联构成。）

This configuration ensures good conduction for both high and low input voltages, overcoming the limitations of single transistor switches.（这种结构在高、低输入电压下都能良好导通，克服了单管开关的局限。）

**MOSFET On-Resistance:**（**MOSFET 导通电阻：**） When a MOSFET operates in the triode (linear) region with small $V_{DS}$, it behaves like a resistor.（当 MOSFET 在小 $V_{DS}$ 下工作于三极管（线性）区时，表现为电阻。）

The on-resistance $R_{on}$ is the small-signal resistance for small drain-source voltages:（导通电阻 $R_{on}$ 是小漏源电压下的小信号电阻：）

$$
R_{on} = \frac{1}{\mu_n C_{ox}\frac{W}{L}(V_{GS} - V_{TN})}
$$

> [!info] MOSFET Symmetry（MOSFET 的对称性）
>
> **Unlike BJTs, MOSFETs are symmetric devices!**（**与 BJT 不同，MOSFET 是对称器件！**） This means:（这意味着：）
>
> - The drain and source terminals are physically identical（漏极与源极在物理上完全相同）
> - You can swap drain and source, and the device works the same way（交换漏极与源极，器件仍以相同方式工作）
> - The terminal at higher potential (for NMOS) becomes the "drain" (PMOS is opposite)（对 NMOS，电位较高的一端作为“漏极”（PMOS 相反））
> - The terminal at lower potential (for NMOS) becomes the "source" (PMOS is opposite)（对 NMOS，电位较低的一端作为“源极”（PMOS 相反））
>
> **For transmission gate analysis:**（**传输门分析步骤：**）
>
> 1. **Step 1:** Identify which terminal is at higher/lower potential（**第 1 步：** 确定哪一端电位较高/较低）
> 2. **Step 2:** Assign drain/source based on voltage levels（**第 2 步：** 根据电位指定漏极/源极）
> 3. **Step 3:** Calculate $V_{GS}$ using the correct source terminal（**第 3 步：** 用正确的源极端计算 $V_{GS}$）
> 4. **Step 4:** Check if $V_{GS}$ meets the ON condition（**第 4 步：** 检查 $V_{GS}$ 是否满足导通条件）
>
> **Example:** If $V_{IN} = 0$ V and $V_{OUT} = 0$ V, both terminals are at same potential, so we can choose either as source for analysis.（**例：** 若 $V_{IN}=0$ V、$V_{OUT}=0$ V，两端电位相同，分析时任选一端作源极均可。）

**Solution:**（**解答：**）

**Part A（A 部分）**

Given $V_{IN} = 0$ V, let's analyze the gate voltages (assuming $V_O \approx V_{IN} = 0$ V for the transmission gate):（已知 $V_{IN}=0$ V，分析各管栅极电压（对传输门假设 $V_O\approx V_{IN}=0$ V）：）

- NMOS (top): $V_{GS} = V_G - V_S = 5\ \text{V} - 0\ \text{V} = 5\ \text{V} > V_{TN} = 0.75\ \text{V} \Rightarrow$ ON（NMOS（上管）：$V_{GS}=5$ V $>V_{TN}$，导通）
- PMOS (bottom): $V_{GS} = V_G - V_S = 0\ \text{V} - 0\ \text{V} = 0\ \text{V} > V_{TP} = -0.75\ \text{V} \Rightarrow$ OFF（PMOS（下管）：$V_{GS}=0$ V $>V_{TP}$，截止）

Therefore, only the NMOS is conducting, so the total resistance is:（因此只有 NMOS 导通，总电阻为：）

$$
R_{on} = R_{on,\mathrm{NMOS}} = \frac{1}{\mu_n C_{ox}\frac{W}{L}(V_{GS} - V_{TN})} \tag{1}
$$

Substituting values:（代入数值：）

$$
R_{on} = \frac{1}{(100 \times 10^{-6}\ \text{A/V}^2)(10/1)(5\ \text{V} - 0.75\ \text{V})} = \frac{1}{4.25 \times 10^{-3}\ \text{A/V}} = 235\ \Omega \tag{2}
$$

Since the transmission gate acts as a closed switch, $V_O = V_{IN} = 0$ V.（传输门相当于闭合开关，故 $V_O=V_{IN}=0$ V。）

**Part B（B 部分）**

Given $V_{IN} = 5$ V, let's analyze the gate voltages (assuming $V_{OUT} \approx V_{IN} = 5$ V):（已知 $V_{IN}=5$ V，分析各管栅极电压（假设 $V_{OUT}\approx V_{IN}=5$ V）：）

- NMOS (top): $V_{GS} = 5\ \text{V} - 5\ \text{V} = 0\ \text{V} < V_{TN} = 0.75\ \text{V} \Rightarrow$ OFF（NMOS（上管）：$V_{GS}=0$ V $<V_{TN}$，截止）
- PMOS (bottom): $V_{GS} = 0\ \text{V} - 5\ \text{V} = -5\ \text{V} < V_{TP} = -0.75\ \text{V} \Rightarrow$ ON（PMOS（下管）：$V_{GS}=-5$ V $<V_{TP}$，导通）

Therefore, only the PMOS is conducting, so the total resistance is:（因此只有 PMOS 导通，总电阻为：）

$$
R_{on} = R_{on,\mathrm{PMOS}} = \frac{1}{\mu_p C_{ox}\frac{W}{L}|V_{GS} - V_{TP}|} \tag{3}
$$

Substituting values:（代入数值：）

$$
R_{on} = \frac{1}{(40 \times 10^{-6}\ \text{A/V}^2)(25/1)|(-5\ \text{V}) - (-0.75\ \text{V})|} = \frac{1}{4.25 \times 10^{-3}\ \text{A/V}} = 235\ \Omega \tag{4}
$$

Since the transmission gate acts as a closed switch, $V_O = V_{IN} = 5$ V.（传输门相当于闭合开关，故 $V_O=V_{IN}=5$ V。）

Notice that both cases yield the same on-resistance of 235 $\Omega$.（注意两种情况得到相同的导通电阻 235 $\Omega$。）

This is by design - the NMOS and PMOS are sized to provide equal resistances, ensuring consistent performance regardless of the input voltage level.（这是有意设计的——NMOS 与 PMOS 的尺寸使二者电阻相等，从而保证不同输入电平时性能一致。）

This demonstrates the advantage of the transmission gate over single-transistor switches.（这体现了传输门相对于单管开关的优势。）

## 4 Question 4（第 4 题）

(a) Find the Q-point for the transistor for $R_1 = 100$ k$\Omega$, $R_2 = 220$ k$\Omega$, $R_3 = 24$ k$\Omega$, $R_4 = 12$ k$\Omega$, and $V_{DD} = 10$ V.（(a) 当 $R_1=100$ k$\Omega$、$R_2=220$ k$\Omega$、$R_3=24$ k$\Omega$、$R_4=12$ k$\Omega$、$V_{DD}=10$ V 时，求晶体管的 Q 点。）

Assume that $V_{TO} = 1$ V, $\gamma = 0$, and $W/L = 6/1$.（设 $V_{TO}=1$ V、$\gamma=0$、$W/L=6/1$。）

(b) Repeat for $W/L = 12/1$.（(b) 对 $W/L=12/1$ 重做。）

![](Pasted%20image%2020261114214828.png)
> 图Q4-1 题 4 的四电阻偏置电路：$V_{DD}$ 经 $R_2$ 与 $R_4$ 接漏极/栅极，$R_1$ 与 $R_3$ 下端接地，栅极取自 $R_1$、$R_2$ 分压点，源极接 $R_3$（图 Q4-1：第 4 题四电阻偏置电路）

**Solution:**（**解答：**）

This problem uses the four-resistor bias configuration discussed in the introduction.（本题使用引言中讨论的四电阻偏置结构。）

This biasing method provides excellent temperature stability and is widely used in practical MOSFET circuits.（该偏置方法温度稳定性好，广泛用于实际 MOSFET 电路。）

For a 4-resistor biased circuit, our first step is to convert the voltage divider (left part) to its Th&eacute;venin equivalent.（对四电阻偏置电路，第一步是把左侧分压部分化为戴维南等效。）

The equivalent circuit diagram is drawn below.（等效电路如下。）

![](Pasted%20image%2020261114214852.png)
> 图4 q4 equivalent circuit diagram（图 4：第 4 题等效电路）

The following formulas are derived in the lectures.（以下公式在课堂中已推导。）

The Thevenin resistance is（戴维南电阻为）

$$
R_{eq} = R_2 \parallel R_1 = 220\ \text{k}\Omega \parallel 100\ \text{k}\Omega = 68.75\ \text{k}\Omega \tag{1}
$$

The Thevenin voltage is（戴维南电压为）

$$
V_{th} = V_{DD} \cdot \frac{R_1}{R_2 + R_1} = 10\ \text{V} \cdot \frac{100\ \text{k}\Omega}{220\ \text{k}\Omega + 100\ \text{k}\Omega} = 3.125\ \text{V} \tag{2}
$$

Since $\gamma = 0$ (the body effect parameter), there is no body effect and the threshold voltage remains constant:（由于 $\gamma=0$（体效应参数），无体效应，阈值电压保持不变：）

$$
V_{TN} = V_{T0} = 1\ \text{V} \tag{3}
$$

Note that the transistor is NMOS because the arrow on the body points inward.（注意该晶体管为 NMOS，因为体端箭头指向内部。）

### 4.1 Part A（A 部分）

For MOSFETs, the Q-point is conventionally expressed as $(I_D, V_{DS})$, representing the DC drain current and drain-source voltage.（对 MOSFET，Q 点通常表示为 $(I_D,V_{DS})$，即直流漏极电流与漏源电压。）

We assume the NMOS operates in the saturation region.（假设 NMOS 工作在饱和区。）

This is a reasonable assumption for amplifier circuits where we want the transistor to act as a voltage-controlled current source rather than a resistor.（对放大器电路这是合理假设，因为希望晶体管作为电压控制电流源而非电阻。）

Applying KVL around the gate-source loop (through the Th&eacute;venin equivalent):（对栅源回路（经戴维南等效）应用 KVL：）

$$
V_{th} - I_G R_{eq} - V_{GS} - I_D R_3 = 0
$$

Note that $I_G = 0$ A, so the $I_G R_{eq}$ vanishes.（注意 $I_G=0$ A，故 $I_G R_{eq}$ 项为零。）

Rearranging:（重排得：）

$$
V_{th} = V_{GS} + I_D R_3 \tag{4}
$$

According to our saturation assumption, the drain current equation is:（根据饱和区假设，漏极电流方程为：）

$$
I_D = \frac{1}{2}\mu_n C_{ox}\left(\frac{W}{L}\right)(V_{GS} - V_{TN})^2 \tag{5}
$$

Substituting equation (5) into (4):（把式 (5) 代入 (4)：）

$$
V_{th} = V_{GS} + \left[\frac{1}{2}\mu_n C_{ox}\left(\frac{6}{1}\right)(V_{GS} - V_{TN})^2\right]R_3 \tag{6}
$$

Simplifying gives the quadratic equation:（化简得二次方程：）

$$
7.2V_{GS}^2 - 13.4V_{GS} + 4.08 = 0 \tag{7}
$$

Solving yields one solution that satisfies $V_{GS} > V_{TN}$:（解得满足 $V_{GS}>V_{TN}$ 的一个解：）

$$
V_{GS} = 1.49\ \text{V} \tag{8}
$$

Now the drain current is:（于是漏极电流为：）

$$
I_D = \frac{1}{2}(100 \times 10^{-6}\ \text{A/V}^2)(6)(1.49\ \text{V} - 1\ \text{V})^2 = 66.27\ \mu\text{A} \tag{9}
$$

To find $V_{DS}$, we need to determine the drain and source voltages separately using KVL:（为求 $V_{DS}$，需用 KVL 分别求漏极与源极电压：）

- Drain voltage: $V_D = V_{DD} - I_D R_4$ (voltage drop across $R_4$)（漏极电压：$V_D=V_{DD}-I_D R_4$，即 $R_4$ 上的压降）
- Source voltage: $V_S = I_D R_3$ (voltage drop across $R_3$ from ground)（源极电压：$V_S=I_D R_3$，即 $R_3$ 上对地的压降）

Therefore:（因此：）

$$
V_{DS} = V_D - V_S = \left[V_{DD} - I_D R_4\right] - \left[I_D R_3\right] \tag{10}
$$

Substituting values:（代入数值：）

$$
V_{DS} = 10\ \text{V} - (66.27\ \mu\text{A})(12\ \text{k}\Omega) - (66.27\ \mu\text{A})(24\ \text{k}\Omega) \tag{11}
$$

$$
= [10\ \text{V} - 0.795\ \text{V}] - [1.591\ \text{V}] = 7.62\ \text{V} \tag{12}
$$

Next, we check the operation region.（接着检查工作区。）

$$
V_{GS} > V_{TN}, \quad V_{GS} - V_{TN} < V_{DS} \Rightarrow \text{saturation is correct } \checkmark \tag{13}
$$

Finally, we write down the Q-point (quiescent or DC operating point):（最后写出 Q 点（静态或直流工作点）：）

$$
Q = (I_D, V_{DS}) = (66.27\ \mu\text{A}, 7.62\ \text{V}) \tag{14}
$$

### 4.2 Part B（B 部分）

![](Pasted%20image%2020261114214909.png)
> 图5 Q4 equivalent circuit diagram（图 5：第 4 题等效电路）

Now we repeat the analysis with $W/L = 12/1$ instead of 6/1.（现在把 $W/L$ 由 6/1 改为 12/1 重做分析。）

Again, we assume saturation operation.（仍假设工作在饱和区。）

The same KVL equation applies:（KVL 方程不变：）

$$
V_{th} = V_{GS} + I_D R_3 \tag{15}
$$

But now the drain current equation has the new aspect ratio:（但漏极电流方程改用新的宽长比：）

$$
I_D = \frac{1}{2}\mu_n C_{ox}\left(\frac{12}{1}\right)(V_{GS} - V_{TN})^2 \tag{16}
$$

Substituting the second equation into the first:（把第二式代入第一式：）

$$
V_{th} = V_{GS} + \left[\frac{1}{2}\mu_n C_{ox}\left(\frac{12}{1}\right)(V_{GS} - V_{TN})^2\right]R_3 \tag{17}
$$

Solving yields one solution that satisfies $V_{GS} > V_{TN}$:（解得满足 $V_{GS}>V_{TN}$ 的一个解：）

$$
V_{GS} = 1.35\ \text{V} \tag{18}
$$

Then the drain current is:（于是漏极电流为：）

$$
I_D = \frac{1}{2}(100 \times 10^{-6}\ \text{A/V}^2)(12)(1.35\ \text{V} - 1\ \text{V})^2 = 73.5\ \mu\text{A} \tag{19}
$$

The drain–source voltage calculation follows the same approach as Part A:（漏源电压的计算与 A 部分相同：）

$$
V_{DS} = V_D - V_S = \left[V_{DD} - I_D R_4\right] - \left[I_D R_3\right] \tag{20}
$$

Substituting values:（代入数值：）

$$
V_{DS} = 10\ \text{V} - (73.5\ \mu\text{A})(12\ \text{k}\Omega) - (73.5\ \mu\text{A})(24\ \text{k}\Omega) \tag{21}
$$

$$
= [10\ \text{V} - 0.882\ \text{V}] - [1.764\ \text{V}] = 7.35\ \text{V} \tag{22}
$$

Next, we check the operation region.（接着检查工作区。）

$$
V_{GS} > V_{TN}, \quad V_{GS} - V_{TN} < V_{DS} \Rightarrow \text{saturation is correct } \checkmark \tag{23}
$$

Finally, the Q-point for Part B is:（最后，B 部分的 Q 点为：）

$$
Q = (I_D, V_{DS}) = (73.5\ \mu\text{A}, 7.35\ \text{V}) \tag{24}
$$

**Comparison:**（**比较：**） Notice that doubling the $W/L$ ratio from 6/1 to 12/1 increased the drain current from 66.27 $\mu$A to 73.5 $\mu$A, while slightly reducing $V_{DS}$ from 7.62 V to 7.35 V.（注意 $W/L$ 由 6/1 加倍到 12/1 后，漏极电流由 66.27 μA 增至 73.5 μA，同时 $V_{DS}$ 由 7.62 V 略降至 7.35 V。）

This demonstrates how the aspect ratio affects the Q-point location along the load line.（这说明宽长比如何影响 Q 点在负载线上的位置。）

## 5 Question 5（第 5 题）

Find the Q-point for the transistor in the same four-resistor bias configuration as Question 4, with parameters: $R_1 = 100$ k$\Omega$, $R_2 = 220$ k$\Omega$, $R_3 = 24$ k$\Omega$, $R_4 = 12$ k$\Omega$, and $V_{DD} = 12$ V.（在与第 4 题相同的四电阻偏置电路中，参数为 $R_1=100$ k$\Omega$、$R_2=220$ k$\Omega$、$R_3=24$ k$\Omega$、$R_4=12$ k$\Omega$、$V_{DD}=12$ V，求晶体管的 Q 点。）

Assume that $V_{T0} = 1$ V, $\gamma = 0.6$ V$^{1/2}$, and $W/L = 5/1$.（设 $V_{T0}=1$ V、$\gamma=0.6$ V$^{1/2}$、$W/L=5/1$。）

**Solution:**（**解答：**）

**Key Difference from Question 4:**（**与第 4 题的关键区别：**） This problem is very similar to Question 4, but now includes the body effect ($\gamma \neq 0$ and $V_{SB} \neq 0$ V) and also uses different supply voltage and aspect ratio.（本题与第 4 题很相似，但需考虑体效应（$\gamma\neq0$ 且 $V_{SB}\neq0$ V），且电源电压与宽长比不同。）

The body effect makes the analysis more complex as the threshold voltage depends on the source voltage by $V_{TN} = V_{T0} + \gamma\left(\sqrt{V_{SB} + 2\phi_F} - \sqrt{2\phi_F}\right)$.（体效应使分析更复杂，因为阈值电压随源极电压变化：$V_{TN}=V_{T0}+\gamma\left(\sqrt{V_{SB}+2\phi_F}-\sqrt{2\phi_F}\right)$。）

Following the same approach as Question 4, we start by finding the Th&eacute;venin equivalent of the bias network:（按第 4 题的方法，先求偏置网络的戴维南等效：）

![](Pasted%20image%2020261114214923.png)
> 图6 q5 equivalent circuit diagram（图 6：第 5 题等效电路）

The Th&eacute;venin resistance (same calculation as Question 4):（戴维南电阻（与第 4 题相同）：）

$$
R_{th} = R_{eq} = R_1 \parallel R_2 = \frac{100\ \text{k}\Omega \times 220\ \text{k}\Omega}{100\ \text{k}\Omega + 220\ \text{k}\Omega} = 68.75\ \text{k}\Omega \tag{1}
$$

The Th&eacute;venin voltage (with the new supply voltage):（戴维南电压（使用新的电源电压）：）

$$
V_{th} = \frac{R_1}{R_1 + R_2}V_{DD} = \frac{100\ \text{k}\Omega}{320\ \text{k}\Omega} \times 12\ \text{V} = 3.75\ \text{V} \tag{2}
$$

The threshold voltage $V_{TN}$ including body effect is:（含体效应的阈值电压 $V_{TN}$ 为：）

$$
V_{TN} = V_{T0} + \gamma\left(\sqrt{V_{SB} + 2\phi_F} - \sqrt{2\phi_F}\right) \tag{3}
$$

Since $V_{SB} = V_S - V_B = I_D R_3 - 0 = I_D R_3$ (source above body), we have:（由于 $V_{SB}=V_S-V_B=I_D R_3-0=I_D R_3$（源极电位高于体），有：）

$$
V_{TN} = 1\ \text{V} + 0.6\sqrt{\text{V}}\left(\sqrt{I_D R_3 + 0.6\ \text{V}} - \sqrt{0.6\ \text{V}}\right) \tag{4}
$$

From KVL around the gate-source loop (through the Th&eacute;venin equivalent):（对栅源回路（经戴维南等效）应用 KVL：）

$$
V_{GS} = V_G - V_S = V_{th} - I_G R_{eq} - I_D R_3 = V_{th} - I_D R_3 \quad (\text{since } I_G = 0\ \text{A}) \tag{5}
$$

Assuming the NMOS operates in saturation, the drain current equation is:（假设 NMOS 工作在饱和区，漏极电流方程为：）

$$
I_D = \frac{1}{2}\mu_n C_{ox}\left(\frac{W}{L}\right)(V_{GS} - V_{TN})^2 \tag{6}
$$

This creates a system of implicit equations because $V_{TN}$ depends on $I_D$ through the body effect, and $I_D$ depends on $V_{TN}$ through the saturation equation.（这形成隐式方程组，因为 $V_{TN}$ 通过体效应依赖 $I_D$，而 $I_D$ 又通过饱和区方程依赖 $V_{TN}$。）

The problem becomes:（问题变为：）

Find $I_D$ and $V_{TN}$ such that:（求满足下式的 $I_D$ 与 $V_{TN}$：）

$$
V_{TN} = 1\ \text{V} + 0.6\sqrt{\text{V}}\sqrt{I_D \cdot 24\ \text{k}\Omega + 0.6\ \text{V}} - \sqrt{0.6\ \text{V}} \tag{7}
$$

$$
I_D = \frac{1}{2}(100 \times 10^{-6}\ \text{A/V}^2)(5)\left[(3.75\ \text{V} - I_D \cdot 24\ \text{k}\Omega) - V_{TN}\right]^2 \tag{8}
$$

This nonlinear system requires iterative solution (e.g., Newton's method).（该非线性方程组需迭代求解（如牛顿法）。）

The solution yields:（解得：）

$$
I_D = 73.1\ \mu\text{A} \tag{9}
$$

$$
V_{TN} = 1.46\ \text{V} \tag{10}
$$

The drain–source voltage is calculated as in previous problems:（漏源电压按前面各题的方法计算：）

$$
V_{DS} = V_D - V_S = \left[V_{DD} - I_D R_4\right] - \left[I_D R_3\right] \tag{11}
$$

$$
= 12\ \text{V} - (73.1\ \mu\text{A})(12\ \text{k}\Omega) - (73.1\ \mu\text{A})(24\ \text{k}\Omega) \tag{12}
$$

$$
= 12\ \text{V} - 0.877\ \text{V} - 1.754\ \text{V} = 9.37\ \text{V} \tag{13}
$$

Next, we verify our saturation assumption:（接着验证饱和区假设：）

- $V_{GS} = V_{th} - I_D R_3 = 3.75\ \text{V} - (73.1\ \mu\text{A})(24\ \text{k}\Omega) = 1.996\ \text{V}$
- $V_{GS} = 1.996\ \text{V} > V_{TN} = 1.46\ \text{V} \ \checkmark$ (transistor ON)（晶体管导通）
- $V_{GS} - V_{TN} = 0.536\ \text{V} < V_{DS} = 9.37\ \text{V} \ \checkmark$ (saturation confirmed)（确认饱和）

Finally, the Q-point is:（最后，Q 点为：）

$$
Q = (I_D, V_{DS}) = (73.1\ \mu\text{A}, 9.37\ \text{V}) \tag{14}
$$

**Body Effect Impact:**（**体效应的影响：**） Notice that the body effect increased the threshold voltage from 1 V to 1.46 V, reducing the effective gate drive and affecting the operating point compared to the idealized case in Question 4.（注意体效应使阈值电压由 1 V 升至 1.46 V，减小了有效栅极驱动，与第 4 题的理想情况相比改变了工作点。）

## 转换说明（非原文内容）

- 本文由 PDF 文本层与页面渲染图逐页核对后转录；公式一律改写为 LaTeX，`\tag` 沿用原文式号（引言部分 (1)–(6)、第 1 题 (1)–(10)、第 2 题 (1)–(8)、第 3 题 (1)–(4)、第 4 题 (1)–(24)、第 5 题 (1)–(14)）。
- 所有插图（MOSFET 符号、负载线图、传输门、各题等效电路）均以纯文本占位表示，未插入图像本体；原书有编号的图写作 `> 图1 …`，原书未编号的插图写作 `> 图Q1-1 …`、`> 图I-1 …`。
- 第 1 题 (4) 式“$12.5V_{GS}^2-17.8V_{GS}-4.97=0$”等二次方程系数原书即以近似值给出，照录；第 4 题 (7) 式的系数同样照录。
- 提示框（Operating Regions / Systematic MOSFET Circuit Analysis / Threshold Voltage Notation / MOSFET Symmetry 等）已改为 Obsidian callout 呈现：绿色框用 `[!tip]`，红色框用 `[!warning]`，蓝色框用 `[!info]`。
