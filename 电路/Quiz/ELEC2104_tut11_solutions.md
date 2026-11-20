# ELEC2104/9704 Tutorial 11 Solutions (2025)（ELEC2104/9704 第 11 次辅导课解答，2025）

## Motivation: MOSFET Amplifiers（引言：MOSFET 放大器）

In the Tutorial 7, we studied BJT amplifiers and their small-signal analysis. Now we turn to MOSFET amplifiers, which share many conceptual similarities with BJT amplifiers but with important differences in their physical behavior and mathematical models.
（在第 7 次辅导课中，我们学习了 BJT 放大器及其小信号分析。现在我们转向 MOSFET 放大器，它与 BJT 放大器在概念上有许多相似之处，但在物理行为和数学模型上存在重要差异。）

Like BJTs, MOSFETs excel as amplifiers due to their ability to convert small voltage changes at the input (gate-source voltage $V_{GS}$) into large current changes at the output (drain current $I_D$). However, while BJTs use an exponential relationship, MOSFETs use a quadratic relationship in saturation:
（与 BJT 一样，MOSFET 之所以适合做放大器，是因为它能将输入端（栅源电压 $V_{GS}$）的微小电压变化转换为输出端（漏极电流 $I_D$）的大电流变化。然而，**BJT 使用的是指数关系，而 MOSFET 在饱和区使用的是二次关系**：）

$$
I_D = \frac{1}{2}\mu_n C_{ox}\frac{W}{L}(V_{GS} - V_{TN})^2 \tag{1}
$$

### Small Signal Inputs vs. Large Signal Inputs（小信号输入与大信号输入）

Just as with BJTs, the property that makes MOSFETs good amplifiers (the nonlinear $I_D$-$V_{GS}$ relationship) also creates a challenge: distortion!
（正如 BJT 一样，使 MOSFET 成为良好放大器的特性（非线性的 $I_D$–$V_{GS}$ 关系）同时也带来了一个挑战：失真！）

The $I_D$-$V_{GS}$ curve is nonlinear (quadratic), as shown in Figure 1. Large input signals cause the transistor to operate over a wide range of this curve, leading to distortion in the output signal (see in blue).
（$I_D$–$V_{GS}$ 曲线是非线性的（二次的），如图 1 所示。大输入信号会使晶体管在这条曲线的很大范围内工作，从而导致输出信号失真（见蓝色部分）。）

![](Pasted%20image%2020261117154141.png)
> 图1 MOSFET nonlinearity: Large signals experience distortion due to the quadratic $I_D$-$V_{GS}$ relationship, while small signals remain in the approximately linear region around the Q-point.（$I_D$–$V_{GS}$ 曲线：Large signal input 对应 Distorted output，Small signal input 对应 Undistorted output；Q-point 处切线为 Linear approximation，slope = $g_m$）

Small signal inputs (see in green) keep the transistor operating near a specific point on the curve, called the Quiescent point (Q-point). Around this point, we can approximate the quadratic curve as a straight line (the tangent with slope = $g_m$, the transconductance), allowing for approximately linear amplification with insignificant levels of distortion.
（小信号输入（见绿色部分）使晶体管工作在曲线上某个特定点附近，该点称为静态工作点（Q 点）。在该点附近，我们可以把二次曲线近似为一条直线（斜率为 $g_m$ 的切线，$g_m$ 即跨导），从而获得失真很小的近似线性放大。）

**Q-point location** - We deliberately position the Q-point on the $I_D$-$V_{GS}$ characteristic curve by selecting an appropriate DC drain current $I_{D,Q}$. Note that the Q-point is formally defined as $Q = (I_D, V_{DS})$, but knowledge of these two quantities also determines $V_{GS}$ through the device equations.
（**Q 点位置** —— 我们通过选择合适的直流漏极电流 $I_{D,Q}$，有意地把 Q 点设置在 $I_D$–$V_{GS}$ 特性曲线上。注意 Q 点的正式定义是 $Q = (I_D, V_{DS})$，但知道这两个量后，也可以通过器件方程确定 $V_{GS}$。）

This choice involves trade-offs:
（这一选择涉及权衡：）

- Higher $I_{D,Q}$ → Higher $g_m$ → Better gain, but more power consumption
  （更高的 $I_{D,Q}$ → 更高的 $g_m$ → 更好的增益，但功耗更大）
- Lower $I_{D,Q}$ → Lower power, but reduced gain (and less bandwidth, a topic for ELEC3404/9404)
  （更低的 $I_{D,Q}$ → 更低功耗，但增益下降（带宽也更小，这是 ELEC3404/9404 的内容））

As Figure 1 demonstrates, the Q-point acts as the "center" of our linear approximation. The tangent line (slope = $g_m$) at the Q-point defines how small signals are amplified without distortion. To set this Q-point, we use a Biasing network. We will see examples of these circuits in Q1 and Q2.
（如图 1 所示，Q 点是我们线性近似的“中心”。Q 点处的切线（斜率 = $g_m$）定义了小信号如何被无失真地放大。为了设置这个 Q 点，我们使用偏置网络。我们将在第 1 题和第 2 题中看到这些电路的例子。）

### Small Signal Analysis (Saturation Region)（小信号分析：饱和区）

The distinction between small signals and large signals for MOSFETs leads us to the same powerful technique we used for BJTs: Small-signal analysis!
（MOSFET 中小信号与大信号的区别，引导我们采用与 BJT 相同的强大技术：小信号分析！）

This technique is based on linearization around the Q-point. Mathematically, we approximate the nonlinear quadratic curve with its first-order Taylor expansion around the Q-point:
（该技术基于在 Q 点附近的线性化。在数学上，我们用非线性二次曲线在 Q 点附近的一阶泰勒展开来近似它：）

$$
I_D = \frac{1}{2}\mu_n C_{ox}\frac{W}{L}(V_{GS} - V_{TN})^2 \xrightarrow{\text{Taylor expansion}} I_D \approx I_{D,Q} + g_m \cdot (V_{GS} - V_{GS,Q}) \tag{2}
$$

where $g_m$ is the transconductance at the Q-point (the slope of the tangent in Figure 1), which is given by:
（其中 $g_m$ 是 Q 点处的跨导（图 1 中切线的斜率），其表达式为：）

$$
g_m = \left.\frac{\partial I_D}{\partial V_{GS}}\right|_{\substack{Q\\ V_{DS}\ \text{fixed}}} = \mu_n C_{ox}\frac{W}{L}(V_{GS,Q} - V_{TN}) \tag{3}
$$

Note that $g_m$ is the derivative with respect to $V_{GS}$ (with $V_{DS}$ held constant).
（注意 $g_m$ 是对 $V_{GS}$ 的偏导（保持 $V_{DS}$ 不变））

This linear approximation is only valid for small signals because higher-order terms in the Taylor series become significant for large deviations from the Q-point. This transforms complex nonlinear circuit analysis into straightforward linear circuit analysis using familiar techniques like Ohm's law and voltage dividers!
（这种线性近似只对小信号有效，因为当偏离 Q 点较大时，泰勒级数中的高阶项会变得显著。这样就把复杂的非线性电路分析转化为使用欧姆定律和分压器等熟悉技巧的简单线性电路分析！）

This linearization enables us to create the MOSFET small-signal model—a linear equivalent circuit that replaces the nonlinear MOSFET for small-signal analysis:
（这种线性化使我们能够建立 MOSFET 小信号模型——一个用于小信号分析的线性等效电路，用来替代非线性的 MOSFET：）

![](Pasted%20image%2020261117154159.png)
> 图2 MOSFET small-signal hybrid-π model: The linear equivalent circuit that replaces the nonlinear MOSFET for small-signal analysis. All parameters depend on the Q-point!（端子 G、D、S；$v_{gs}$ 标 +/−；受控源 $g_m v_{gs}$；输出电阻 $r_o$，$r_o = 1/(\lambda I_D)$）


> [!note] 两个小信号参数怎么来的
> 因为 $I_D=f(V_{GS},V_{DS})$，在 Q 点做一阶展开：
>
> $$i_d\approx\underbrace{\left.\frac{\partial I_D}{\partial V_{GS}}\right|_Q}_{g_m}v_{gs}+\underbrace{\left.\frac{\partial I_D}{\partial V_{DS}}\right|_Q}_{1/r_o}v_{ds}=g_mv_{gs}+\frac{v_{ds}}{r_o}$$
>
> 两个偏导系数正好对应等效电路里的两个元件：
>
> - **对 $V_{GS}$ 求导 → $g_m$**：这一项电流由输入电压 $v_{gs}$ 控制，画成受控电流源 $g_mv_{gs}$（接在 D–S 之间）。
> - **对 $V_{DS}$ 求导 → $1/r_o$**：这一项电流由自身的端电压 $v_{ds}$ 决定，画成电阻 $r_o$ 并联在 D–S 之间。
> - 栅极 $i_g=0$，所以 G 端开路，模型里没有输入电阻。
>
> 由此得到两个参数（本课程 $\lambda=0$）：
>
> $$g_m=\mu_nC_{ox}\frac{W}{L}(V_{GS,Q}-V_{TN})$$
>
> $$r_o=\frac{1}{\lambda I_{D,Q}}\ (\lambda\neq0),\qquad r_o=\infty\ (\lambda=0)$$
>
> $g_m$ 的三种等价形式（形式 1：用 $V_{GS,Q}$；形式 2：用 $I_{D,Q}$；形式 3：用 $V_{GS,Q}$ 与 $I_{D,Q}$），每种都附有含 $\lambda$ 的版本，见下文三个 callout。

### MOSFET Non-Ideal Behavior: Channel-Length Modulation（MOSFET 非理想行为：沟道长度调制）

In the ideal MOSFET model, we assumed $I_D = \frac{1}{2}\mu_n C_{ox}\frac{W}{L}(V_{GS} - V_{TN})^2$, where drain current depends only on $V_{GS}$. However, real MOSFETs exhibit Channel-Length Modulation—the drain current also depends slightly on $V_{DS}$.
（在理想 MOSFET 模型中，我们假设 $I_D = \frac{1}{2}\mu_n C_{ox}\frac{W}{L}(V_{GS} - V_{TN})^2$，即漏极电流只取决于 $V_{GS}$。然而，实际 MOSFET 会表现出沟道长度调制——漏极电流也略微依赖于 $V_{DS}$。）

**Large-Signal (DC) Analysis:** Channel-length modulation is modeled by including a $V_{DS}$ term:
（**大信号（直流）分析：** 通过引入 $V_{DS}$ 项来建模沟道长度调制：）

$$
I_D = \frac{1}{2}\mu_n C_{ox}\frac{W}{L}(V_{GS} - V_{TN})^2(1 + \lambda V_{DS}) \tag{4}
$$

where $\lambda$ is the channel-length modulation parameter (units: V$^{-1}$). Higher $V_{DS}$ gives higher $I_D$ (for fixed $V_{GS}$). When $\lambda \to 0$, we recover the ideal model.
（其中 $\lambda$ 是沟道长度调制参数（单位：V$^{-1}$）。在 $V_{GS}$ 固定时，$V_{DS}$ 越高，$I_D$ 越大。当 $\lambda \to 0$ 时，回到理想模型。）

**Small-Signal (AC) Analysis:** Channel-length modulation manifests as a finite output resistance $r_o$ in the small-signal model (see Figure 2):
（**小信号（交流）分析：** 沟道长度调制在小信号模型中表现为有限的输出电阻 $r_o$（见图 2）：）

$$
r_o = \frac{1}{\lambda I_D} \tag{5}
$$

When $\lambda \to 0$, we get $r_o \to \infty$ (open circuit). Questions will assume $\lambda = 0$ unless otherwise specified.
（当 $\lambda \to 0$ 时，$r_o \to \infty$（开路）。除非另有说明，题目均假设 $\lambda = 0$。）

> [!note] 形式 1：用 $V_{GS,Q}$ 表示
> 基本形式（即前面的式 (3)，$\lambda=0$）：
>
> $$g_m=\mu_nC_{ox}\frac{W}{L}(V_{GS,Q}-V_{TN})$$
>
> 含 $\lambda$ 时，大信号方程变为
>
> $$I_D = \frac{1}{2}\mu_n C_{ox}\frac{W}{L}(V_{GS} - V_{TN})^2(1 + \lambda V_{DS}) \tag{9}$$
>
> 对 $V_{GS}$ 求导：
>
> $$g_m = \mu_n C_{ox}\frac{W}{L}(V_{GS,Q} - V_{TN})(1 + \lambda V_{DS,Q}) \tag{10}$$
>
> 比基本形式多一个因子 $(1+\lambda V_{DS,Q})$。
>


> [!note] 形式 2：用 $I_{D,Q}$ 表示
> 基本形式（$\lambda=0$）：由式 (1) 解出 $V_{GS,Q}-V_{TN}$，
>
> $$(V_{GS,Q} - V_{TN}) = \sqrt{\frac{2 I_{D,Q}}{\mu_n C_{ox}(W/L)}} \tag{6}$$
>
> 代入基本跨导式：
>
> $$g_m = \mu_n C_{ox}\frac{W}{L}\sqrt{\frac{I_{D,Q}}{\mu_n C_{ox}(W/L)}} = \sqrt{2\mu_n C_{ox}\frac{W}{L}I_{D,Q}} \tag{7}$$
>
> 这个形式把 $g_m$ 直接与 Q 点电流 $I_{D,Q}$ 联系起来，而 $I_{D,Q}$ 通常更容易由电路分析求出。
>
> 含 $\lambda$ 时：
>
> $$g_m = \sqrt{2\mu_n C_{ox}\frac{W}{L}I_{D,Q}}\sqrt{1 + \lambda V_{DS,Q}}$$

> [!note] 形式 3：用 $V_{GS,Q}$ 与 $I_{D,Q}$ 表示
> 基本形式（$\lambda=0$）：
>
> $$g_m = \mu_n C_{ox}\frac{W}{L}(V_{GS,Q} - V_{TN}) = \frac{2 I_{D,Q}}{V_{GS,Q} - V_{TN}} \tag{8}$$
>
> 含 $\lambda$ 时这个形式依然成立：$I_D$ 中已经包含 $(1+\lambda V_{DS,Q})$ 因子，而 $g_m=2I_{D,Q}/(V_{GS,Q}-V_{TN})$ 的比值不变。

### Key Differences: MOSFET vs. BJT Small-Signal Models（关键区别：MOSFET 与 BJT 小信号模型）

While the overall approach to small-signal analysis is identical for MOSFETs and BJTs, there are important differences:
（虽然 MOSFET 与 BJT 的小信号分析总体方法完全相同，但存在一些重要区别：）

**1. Gate current:** MOSFETs have negligible gate current ($i_g = 0$), so there is no input resistance like $r_\pi$ in BJTs. The gate appears as an open circuit in the small-signal model.
（**1. 栅极电流：** MOSFET 的栅极电流可忽略（$i_g=0$），因此不像 BJT 那样有 $r_\pi$ 这类输入电阻；小信号模型中栅极相当于开路。）

**2. Transconductance formulas:**（**2. 跨导公式：**）

| 器件     | 形式                 | 表达式                                                                | 适用条件                     |
| ------ | ------------------ | ------------------------------------------------------------------ | ------------------------ |
| BJT    | 基本                 | $g_m=\dfrac{I_C}{V_T}$                                             | $V_T\approx26$ mV        |
| MOSFET | 用 $V_{GS}$ 表示      | $g_m=\mu_nC_{ox}\dfrac{W}{L}(V_{GS,Q}-V_{TN})$                     | $\lambda=0$              |
| MOSFET | 用 $I_D$ 表示         | $g_m=\sqrt{2\mu_nC_{ox}\dfrac{W}{L}I_{D,Q}}$                       | $\lambda=0$              |
| MOSFET | 用 $V_{GS}$ 与 $I_D$ | $g_m=\dfrac{2I_{D,Q}}{V_{GS,Q}-V_{TN}}$                            | 该形式在 $\lambda\neq0$ 时仍成立 |
| MOSFET | 含 $\lambda$        | $g_m=\mu_nC_{ox}\dfrac{W}{L}(V_{GS,Q}-V_{TN})(1+\lambda V_{DS,Q})$ | 完整版                      |

**3. Output resistance formulas:**（**3. 输出电阻公式：**）

| 器件 | 表达式 | 说明 |
| --- | --- | --- |
| BJT | $r_o=\dfrac{V_A}{I_C}$ | 厄利电压 |
| MOSFET | $r_o=\dfrac{1}{\lambda I_{D,Q}}\approx\dfrac{V_A}{I_{D,Q}}$ | 沟道长度调制，$V_A=1/\lambda$ |

Despite these differences, the analysis procedure is identical: find the Q-point, calculate small-signal parameters, replace the transistor with its small-signal hybrid-π model, and analyze the linear circuit.
（尽管存在这些差异，分析步骤完全相同：求 Q 点、计算小信号参数、用混合 π 小信号模型替代晶体管，然后分析线性电路。）

### Small Signal Analysis vs. Large Signal Analysis（小信号分析与大信号分析）

Just as with BJTs, we approach MOSFET amplifier analysis using two sequential analysis techniques:
（与 BJT 一样，我们采用两种先后进行的分析技术来分析 MOSFET 放大器：）

1. **Large-Signal (DC) Analysis:** First, we find the DC operating point (Q-point) in the absence of any AC signals. This tells us where the transistor is "sitting" when no signal is applied.
   （**大信号（直流）分析：** 首先，在没有任何交流信号的情况下求直流工作点（Q 点）。它告诉我们晶体管在没有信号时“停留”在哪里。）

2. **Small-Signal (AC) Analysis:** Second, we study how the circuit responds to small AC signals superimposed onto the DC operating point.
   （**小信号（交流）分析：** 其次，研究电路对叠加在直流工作点上的小交流信号的响应。）

### Notation Convention（符号约定）

Throughout this course, we use a consistent notation to distinguish DC and AC quantities:
（在本课程中，我们使用统一的记号来区分直流量和交流量：）

- Capital letters for DC (large-signal) quantities: $V_D$, $I_D$, $V_{GS}$, etc.
  （大写字母表示直流（大信号）量：$V_D$、$I_D$、$V_{GS}$ 等。）
- Lowercase letters for AC (small-signal) quantities: $v_d$, $i_d$, $v_{gs}$, etc.
  （小写字母表示交流（小信号）量：$v_d$、$i_d$、$v_{gs}$ 等。）

### The Key Insight: Q-Point Determines Everything!（关键洞见：Q 点决定一切！）

The crucial connection between these two analysis steps is that we need to know $I_D$ (the DC drain current) to build our small-signal model. The transconductance $g_m = \sqrt{2\mu_n C_{ox}\frac{W}{L}I_D}$ is the fundamental parameter that determines how the MOSFET amplifies signals. Without knowing the DC operating point, we cannot determine the small-signal behavior! This is why we must perform large-signal analysis first.
（这两个分析步骤之间的关键联系在于：我们需要知道 $I_D$（直流漏极电流）才能建立小信号模型。跨导 $g_m = \sqrt{2\mu_n C_{ox}\frac{W}{L}I_D}$ 是决定 MOSFET 如何放大信号的基本参数。不知道直流工作点，就无法确定小信号行为！这就是我们必须先做大信号分析的原因。）

Note that the Q-point $Q = (I_D, V_{DS})$ is expressed with the drain current $I_D$ and the drain-source voltage $V_{DS}$. Only $I_D$ directly influences the small-signal parameters like $g_m$ and $r_o$. The voltage $V_{DS}$ is primarily used to verify that the MOSFET is operating in the saturation region (i.e. $V_{DS} > V_{GS} - V_{TN}$ for NMOS).
（注意 Q 点 $Q = (I_D, V_{DS})$ 由漏极电流 $I_D$ 和漏源电压 $V_{DS}$ 表示。只有 $I_D$ 直接影响 $g_m$ 和 $r_o$ 等小信号参数。电压 $V_{DS}$ 主要用于验证 MOSFET 工作在饱和区（即 NMOS 满足 $V_{DS} > V_{GS} - V_{TN}$）。）

### MOSFET Analysis Procedure（MOSFET 分析步骤）

The standard procedure for analyzing MOSFET amplifier circuits focuses on finding the two key quantities: drain current $I_D$ and drain-source voltage $V_{DS}$. Assume saturation region operation (almost always holds in tutorial questions for amplifier questions), then:
（分析 MOSFET 放大器电路的标准步骤集中在求两个关键量：漏极电流 $I_D$ 和漏源电压 $V_{DS}$。先假设工作在饱和区（在辅导课的放大器题目中几乎总是成立），然后：）

**Step 1: Large-Signal (DC) Analysis**（**第 1 步：大信号（直流）分析**）

1. Find $I_D$ and $V_{DS}$ using standard circuit analysis techniques.
   （用标准电路分析技术求 $I_D$ 和 $V_{DS}$。）

   - Use KCL/KVL to write equations for the circuit.
     （用 KCL/KVL 写出电路方程。）
   - Use the quadratic saturation relationship: $I_D = \frac{1}{2}\mu_n C_{ox}\frac{W}{L}(V_{GS} - V_{TN})^2$
     （使用饱和区二次关系：$I_D = \frac{1}{2}\mu_n C_{ox}\frac{W}{L}(V_{GS} - V_{TN})^2$）
   - If channel-length modulation is present ($\lambda \neq 0$): $I_D = \frac{1}{2}\mu_n C_{ox}\frac{W}{L}(V_{GS} - V_{TN})^2(1 + \lambda V_{DS})$
     （若存在沟道长度调制（$\lambda \neq 0$）：$I_D = \frac{1}{2}\mu_n C_{ox}\frac{W}{L}(V_{GS} - V_{TN})^2(1 + \lambda V_{DS})$）

2. Verify the saturation assumption
   （验证饱和区假设。）

3. Record Q-point: $Q = (I_D, V_{DS})$
   （记录 Q 点：$Q = (I_D, V_{DS})$。）

**Step 2: Small-Signal (AC) Analysis**（**第 2 步：小信号（交流）分析**）

1. Calculate small-signal parameters from Q-point:
   （由 Q 点计算小信号参数：）

$$
\text{transconductance } g_m = \sqrt{2\mu_n C_{ox}\frac{W}{L}I_D} \text{ (etc, you may need } \lambda) \tag{11}
$$

$$
\text{output resistance } r_o = \frac{1}{\lambda I_D} \tag{12}
$$

2. Replace the MOSFET circuit symbol with the linearized small-signal model within the circuit diagram. See Figure 2.
   （在电路图中用线性化小信号模型替代 MOSFET 符号。见图 2。）

![](Pasted%20image%2020261120090351.png)

3. Set all DC independent sources to zero (current sources become open circuits, voltage sources become short circuits).
   （将所有直流独立源置零（电流源变为开路，电压源变为短路）。）

4. Analyze the resulting circuit diagram using standard linear circuit analysis techniques.
   （用标准线性电路分析技术分析所得电路图。）

   - For a common-source amplifier (with drain resistor $R_D$ and load resistor $R_L$):
     （对于共源放大器（带漏极电阻 $R_D$ 和负载电阻 $R_L$）：）

$$
\text{input impedance } R_{in} = \infty \text{ (open circuit at gate)} \tag{13}
$$

$$
\text{output impedance } R_{out} = r_o \parallel R_D \tag{14}
$$

$$
\text{voltage gain } A_v = -g_m \cdot (R_D \parallel r_o \parallel R_L) \tag{15}
$$

> [!warning] Critical Assumption: Saturation Region Only!（关键假设：仅在饱和区！）
>
> IMPORTANT: Both small-signal and large-signal analysis techniques we use in this course are only valid in the saturation region of the MOSFET!
> （重要：本课程使用的小信号和大信号分析技术仅在 MOSFET 的饱和区有效！）
>
> The quadratic relationship $I_D = \frac{1}{2}\mu_n C_{ox}\frac{W}{L}(V_{GS} - V_{TN})^2$ is not a universal law—it's simply a mathematical approximation that models a MOSFET operating in saturation. Outside this region (cutoff, triode), the relationship breaks down completely.
> （二次关系 $I_D = \frac{1}{2}\mu_n C_{ox}\frac{W}{L}(V_{GS} - V_{TN})^2$ 并非普遍定律——它只是对工作在饱和区的 MOSFET 的数学近似。在该区域之外（截止区、三极管区），该关系完全失效。）

In MOSFET problems, unless otherwise stated, assume $\mu_n C_{ox} = 200\ \mu\text{A/V}^2$, $\mu_p C_{ox} = 100\ \mu\text{A/V}^2$, $\lambda = 0$, and $V_{TN} = 0.4$ V and $V_{TP} = -0.4$ V.
（在 MOSFET 题目中，除非另有说明，假设 $\mu_n C_{ox} = 200\ \mu\text{A/V}^2$、$\mu_p C_{ox} = 100\ \mu\text{A/V}^2$、$\lambda = 0$，且 $V_{TN} = 0.4$ V、$V_{TP} = -0.4$ V。）

---

## 1 Question 1（第 1 题）

We wish to design the stage in Fig. 2 for a voltage gain of 5 with $W/L \leq 20/0.18$. Determine the required value of $R_D$ if the power dissipation must not exceed 1 mW.
（我们希望按图 2 设计该电路级，使其电压增益为 5，且 $W/L \leq 20/0.18$。若功耗不得超过 1 mW，求所需的 $R_D$ 值。）

![](Pasted%20image%2020261117154226.png)
> 图Q1-1 Fig. 2：共源 NMOS $M_1$，$V_{DD} = 1.8$ V 经 $R_D$ 接漏极（$V_{out}$），$V_{in}$ 接栅极，源极接地

**Solution:**（**解答：**）

First, we draw the small signal circuit diagram.
（首先，画出小信号电路图。）

![](Pasted%20image%2020261117154236.png)
> 图Q1-2 Figure 3: Q1 small signal circuit diagram（手绘：G 端 $V_{in}$ 加 +/−，受控源 $g_m V_{in}$，漏极 D 经 $R_D$ 接地）

We are to design a MOSFET amplifier that provides a voltage gain of $A_v = 5$, while ensuring that the total power dissipation does not exceed 1 mW. The design constraints and the steps for determining the drain resistance $R_D$ are outlined below.
（我们要设计一个电压增益 $A_v = 5$ 的 MOSFET 放大器，同时保证总功耗不超过 1 mW。下面给出设计约束以及求漏极电阻 $R_D$ 的步骤。）

**符号说明**：
- $A_v$：电压增益（小信号输出电压与输入电压之比）
- $g_m$：MOSFET 的跨导
- $R_D$：漏极电阻
- $I_{DS}$：直流（静态）漏极电流
- $\mu_n C_{ox}$：NMOS 的工艺跨导参数
- $W/L$：晶体管的宽长比

---

>列设计方程

**Given design equations:**（**已知设计方程：**）

Voltage gain is first of all a ratio of voltages:
（电压增益首先就是两个电压之比：）

$$
A_v=\frac{v_{out}}{v_{in}}
$$

From the small-signal circuit, $v_{in}$ controls the current $i_d=g_mv_{in}$; this current flows through $R_D$, so
（由小信号电路，$v_{in}$ 控制电流 $i_d=g_mv_{in}$；该电流流过 $R_D$，所以：）

$$
v_{out}=-i_dR_D=-g_mR_D\,v_{in}
$$

Thus
（因此：）

$$
A_v=\frac{v_{out}}{v_{in}}=-g_mR_D
$$

and the design requires $|A_v|=5$:
（设计要求 $|A_v|=5$：）

$$
|A_v| = g_mR_D = 5 \tag{1}
$$

The power budget gives（功耗预算给出）：

$$
P = I_{DS} \cdot V_{DD} \leq 1\ \text{mW} \tag{2}
$$

> [!note] 默认 $r_o=\infty$
> 式 (1) 只保留 $R_D$，相当于取 $r_o\to\infty$。题目没有给出沟道长度调制参数，本课程默认 $\lambda=0$，因此不计 $r_o$。若计入，完整增益为
> $$A_v=-g_m\left(R_D\parallel r_o\right)$$
> 只有 $r_o\gg R_D$ 时才能近似成 $-g_mR_D$。

---

>求$I_{DS}$上限（功耗约束）

Next, we determine the maximum allowable drain current based on the power constraint.
（接下来，根据功耗约束确定最大允许漏极电流。）

From the power relation in Eq. (2), the drain current must satisfy:
（由式 (2) 的功率关系，漏极电流必须满足：）

$$
I_{DS} \leq \frac{10^{-3}}{1.8} = 0.56\ \text{mA} \tag{3}
$$

This value of $I_{DS}$ ensures that the total DC power consumed by the circuit does not exceed the specified 1 mW when the supply voltage is $V_{DD} = 1.8$ V.
（该 $I_{DS}$ 值保证在电源电压 $V_{DD} = 1.8$ V 时，电路消耗的总直流功率不超过给定的 1 mW。）

---

>求$g_m$

Next, we express the small-signal transconductance $g_m$ in terms of device parameters.
（接下来，用器件参数表示小信号跨导 $g_m$。）

For a MOSFET operating in the saturation region, the transconductance is related to the drain current by:
（对于工作在饱和区的 MOSFET，跨导与漏极电流的关系为：）

$$
g_m = \sqrt{2\mu_n C_{ox}\left(\frac{W}{L}\right)I_{DS}} \tag{4}
$$

where $\mu_n C_{ox}$ is the process transconductance parameter, and $W/L$ is the transistor aspect ratio.
（其中 $\mu_n C_{ox}$ 是工艺跨导参数，$W/L$ 是晶体管宽长比。）

---

>把$g_m$代入增益式

We now relate the transconductance to the desired voltage gain.
（现在把跨导与所需电压增益联系起来。）

From the small-signal gain expression in Eq. (1), the magnitude of the voltage gain is:
（由式 (1) 的小信号增益表达式，电压增益的幅值为：）

$$
A_v = g_m R_D \tag{5}
$$

Substituting Eq. (4) into Eq. (5) gives:
（将式 (4) 代入式 (5) 得：）

$$
A_v = R_D \sqrt{2\mu_n C_{ox}\left(\frac{W}{L}\right)I_{DS}} \tag{6}
$$

This relation directly connects the voltage gain to the drain resistance, process parameters, and bias current.
（该关系把电压增益直接与漏极电阻、工艺参数和偏置电流联系起来。）

---

>求$R_D$

Solving for $R_D$ gives the minimum resistance required to achieve the desired gain.
（解出 $R_D$，即得达到所需增益所需的最小电阻。）

Rearranging Eq. (6) for $R_D$:
（将式 (6) 整理成 $R_D$ 的表达式：）

$$
R_D = \frac{A_v}{\sqrt{2\mu_n C_{ox}\left(\frac{W}{L}\right)I_{DS}}} \tag{7}
$$

We now substitute the given numerical values to compute $R_D$.
（现在代入给定数值计算 $R_D$。）

Given:
（已知：）

$$
\mu_n C_{ox} = 200\ \mu\text{A/V}^2, \quad \frac{W}{L} = \frac{20}{0.18}, \quad I_{DS} \leq 0.56\ \text{mA}
$$

The design takes the maximum allowed current $I_{DS}=0.56\ \text{mA}$: a larger $I_{DS}$ gives a larger $g_m$ and therefore the smallest $R_D$ for the required gain.
（设计取允许的最大电流 $I_{DS}=0.56$ mA：$I_{DS}$ 越大，$g_m$ 越大，达到同样增益所需的 $R_D$ 越小。）

Substituting into Eq. (7):
（代入式 (7)：）

$$
R_D = \frac{5}{\sqrt{2(200 \times 10^{-6})\left(\frac{20}{0.18}\right)(0.56 \times 10^{-3})}} \tag{8}
$$

Evaluating the expression:
（计算该表达式：）

$$
R_D \geq \frac{5}{0.0497} = 100.6\ \Omega \tag{9}
$$

---

>设计结论

Finally, we state the design conclusion.
（最后给出设计结论。）

$$
R_D \geq 100\ \Omega \tag{10}
$$

This drain resistance ensures that the amplifier achieves the required voltage gain of 5 without exceeding the maximum allowed power dissipation of 1 mW. Choosing $R_D$ slightly higher than $100\ \Omega$ would provide design margin to account for process variations and non-idealities.
（该漏极电阻使放大器达到所需的电压增益 5，且不超过最大允许功耗 1 mW。选择略高于 $100\ \Omega$ 的 $R_D$ 可为工艺偏差和非理想因素留出设计裕量。）

> [!tip] 为什么这里取“大于等于”
> 增益要求 $A_v = g_mR_D$ 给出 $R_D$ 的下限，功耗约束给出 $I_{DS}$ 的上限；两者代换后得到的 $R_D \geq 100\ \Omega$ 是最小设计值。
> 
> 取 $I_{DS}$ 的允许上限（0.56 mA）时，所需 $R_D$ 最小；$R_D$ 再大一些不会违反功耗约束，且留出设计裕量。

---

## 2 Question 2（第 2 题）

In the circuit shown in Fig. 3, M2 serves as a current source. Design the stage for a voltage gain of 20 and a power budget of 2 mW. Assume $\lambda = 0.1$ V$^{-1}$ for both transistors and the maximum allowable level at the output is 1.5 V (i.e., M2 must remain in saturation if $V_{out} \leq 1.5$ V).
（在图 3 所示电路中，M2 用作电流源。为该级设计电压增益 20、功耗预算 2 mW。假设两个晶体管的 $\lambda = 0.1$ V$^{-1}$，输出端允许的最高电平为 1.5 V（即若 $V_{out} \leq 1.5$ V，M2 必须保持在饱和区）。）

![](Pasted%20image%2020261117154257.png)
> 图Q2-1 Fig. 3：CMOS 共源放大器，PMOS $M_2$ 在上（$V_{DD} = 1.8$ V，栅极接 $V_b$），漏极即 $V_{out}$；NMOS $M_1$ 在下（栅极 $V_{in}$，源极接地）

**Solution:**（**解答：**）

**Small signal circuit diagram** Given the large signal circuit setup, we can notice that:
（**小信号电路图** 给定大信号电路结构，我们可以注意到：）

**先明确器件类型：** 图中 **$M_2$ 是 PMOS，位于上方**（源极接 $V_{DD}=1.8$ V，栅极接偏置 $V_b$，漏极接 $V_{out}$）；**$M_1$ 是 NMOS，位于下方**（栅极接输入 $V_{in}$，源极接地）。

**小信号等效结果**

The small signal circuit diagram is shown below.
（小信号电路图如下所示。）

![](Pasted%20image%2020261117154307.png)
> 图Q2-2 Figure 4: Small signal circuit diagram（$r_{o2}$ 由电源接至 $V_{out}$；$g_m V_{in}$ 受控源与 $r_{o1}$ 并联于 $V_{out}$ 与地之间；$V_{in}$ 加在栅源之间）

- **M1（NMOS，放大管）** → 受控电流源 $g_mv_{in}$ 与 $r_{o1}$ 并联，栅极开路。
- **M2（PMOS，有源负载）** → 受控源为零，只剩一个电阻 $r_{o2}$（交流中接在 $V_{out}$ 与地之间）。

**为什么这样等效**

**M1 是放大管**

输入 $v_{in}$ 加在它的栅极 → $v_{gs1}=v_{in}$ 随信号变化 → 漏极电流 $i_d=g_{m1}v_{in}$ 随信号变化。

**M2 是有源负载**

它的栅极接固定偏置 $V_b$ → 小信号 $v_{gs2}=0$ → 受控源 $g_{m2}v_{gs2}=0$，对交流只剩输出电阻 $r_{o2}$；

直流上它提供偏置电流，是恒流源。又因 $V_{DD}$ 是直流电源、交流短路到地，$r_{o2}$ 表现为从 $V_{out}$ 到地。

**符号说明**：
- $\lambda$：沟道长度调制参数
- $r_{o1}$、$r_{o2}$：M1、M2 的小信号输出电阻
- $R_{out}$：放大器的输出电阻
- $g_m$：M1 的跨导
- $V_b$：M2 的栅极偏置电压
- $\mu_p C_{ox}$：PMOS 的工艺跨导参数

---

>由功耗预算求$I_D$

**Given:** The circuit in Fig. 3 shows a CMOS amplifier where $M_1$ is an NMOS transistor and $M_2$ is a PMOS transistor acting as a current source. The supply voltage is
（**已知：** 图 3 所示电路是一个 CMOS 放大器，其中 $M_1$ 是 NMOS 晶体管，$M_2$ 是作为电流源的 PMOS 晶体管。电源电压为）

$$
V_{DD} = 1.8\ \text{V} \tag{1}
$$

The power dissipation is given by
（功耗由下式给出：）

$$
P = I_D V_{DD} \tag{2}
$$

and since $P = 2$ mW,
（且 $P = 2$ mW，故）

$$
I_D = \frac{P}{V_{DD}} = \frac{2\ \text{mW}}{1.8\ \text{V}} = 1.11\ \text{mA} \tag{3}
$$

---

>求$r_o$

**Output Resistance:**（**输出电阻：**）

Given $\lambda = 0.1$ V$^{-1}$ for both transistors,
（已知两个晶体管的 $\lambda = 0.1$ V$^{-1}$，）

$$
r_{o1} = r_{o2} = \frac{1}{\lambda I_D} = \frac{1}{0.1 \times 1.11\ \text{mA}} = 9000\ \Omega \tag{4}
$$

---

>求$R_{out}$与$g_m$

**Voltage Gain:**（**电压增益：**）

>这里需要再画一下小信号等效电路

**画小信号等效电路的三步**

1. **独立直流源置零**：电压源短路、电流源开路。
2. **信号只保留增量**：总量拆成“直流 + 增量”，如 $v_{GS}=V_{GS,Q}+v_{gs}$，小信号只画 $v_{gs}$。
3. **器件换成小信号模型**：参数由 Q 点算出，$g_m=I_{D,Q}/V_T$ 等。

注意三点：Q 点不能丢（否则 $g_m=0$、没有增益）；受控源不能置零；耦合、旁路电容在交流通路中视为短路。

The small-signal voltage gain is
（小信号电压增益为）

$$
A_V = |-g_m R_{out}| = |-g_m(r_{o1} \parallel r_{o2})| \tag{5}
$$

Since $r_{o1} = r_{o2} = 9000\ \Omega$, the parallel combination is
（由于 $r_{o1} = r_{o2} = 9000\ \Omega$，并联组合为）

$$
r_{o1} \parallel r_{o2} = 4500\ \Omega \tag{6}
$$

To achieve a voltage gain of 20:
（要达到电压增益 20：）

$$
20 = g_m(9000 \parallel 9000) \Rightarrow 20 = g_m(4500) \tag{7}
$$

Hence,
（因此，）

$$
g_m = \frac{20}{4500} = 4.44\ \text{mS} \tag{8}
$$

---

>求$(W/L)_{M1}$、记录偏置

![](Pasted%20image%2020261120165426.png)

**For M1:** To keep M1 in saturation, the boundary condition is:
（**对于 M1：** 为使 M1 保持饱和，边界条件为：）

$$
V_{DS1} = V_{GS1} - V_{TN} \tag{9}
$$

Since the source is grounded and the drain is the output node,
（由于源极接地、漏极即输出节点，）

$$
V_{DS1} = V_{out}, \qquad V_{GS1} = V_{IN}
$$

Therefore
（因此）在恰好饱和的边界位置，有如下的关系

$$
V_{IN} = V_{out} + V_{TN} \tag{10}
$$

Using the MOSFET transconductance equation:
（使用 MOSFET 跨导方程：）

$$
g_m = \sqrt{2\mu_n C_{ox}\left(\frac{W}{L}\right)I_D} \tag{11}
$$

Substituting $g_m = 4.44$ mS, $\mu_n C_{ox} = 200\ \mu\text{A/V}^2$, and $I_D = 1.11$ mA:
（代入 $g_m = 4.44$ mS、$\mu_n C_{ox} = 200\ \mu\text{A/V}^2$ 和 $I_D = 1.11$ mA：）

$$
\left(\frac{W}{L}\right)_{M1} = \frac{(4.44 \times 10^{-3})^2}{2(200 \times 10^{-6})(1.11 \times 10^{-3})} = 27.75 \tag{12}
$$

---

>求$(W/L)_{M2}$

![](Pasted%20image%2020261120165611.png)

**For M2:** To remain in saturation for $V_{out} \leq 1.5$ V,
（**对于 M2：** 为使 $V_{out} \leq 1.5$ V 时仍处于饱和区，）

The saturation condition is:
（饱和条件为：）

$$
V_{SD2} \ge V_{SG2} - |V_{TP}|
$$

With $V_{SD2} = V_{DD} - V_{out}$ and $V_{SG2} = V_{DD} - V_b$:
（代入 $V_{SD2}=V_{DD}-V_{out}$、$V_{SG2}=V_{DD}-V_b$：）

$$
V_{DD} - V_{out} \ge V_{DD} - V_b - |V_{TP}|
$$

Cancelling $V_{DD}$ on both sides:
（两边消去 $V_{DD}$：）

$$
V_b \ge V_{out} - |V_{TP}|
$$

For $V_{out} \leq 1.5$ V and $|V_{TP}| = 0.4$ V:
（取 $V_{out}\leq1.5$ V、$|V_{TP}|=0.4$ V：）

$$
V_b \geq 1.5 - 0.4 = 1.1\ \text{V} \tag{13}
$$

Setting $V_b = 1.2$ V and $V_{out} = 1.5$ V, we apply:
（取 $V_b = 1.2$ V、$V_{out} = 1.5$ V，应用：）

$$
I_D = \frac{1}{2}\mu_p C_{ox}\left(\frac{W}{L}\right)_2(V_{SG2} - |V_{TP}|)^2(1 + \lambda V_{SD2}) \tag{14}
$$

Substituting $\mu_p C_{ox} = 100\ \mu\text{A/V}^2$, $V_{SG2} - |V_{TP}| = 0.6 - (-0.47) = 1.07$ V, $\lambda = 0.1$, and $V_{SD2} = 1.8 - 1.5 = 0.3$ V:
（代入 $\mu_p C_{ox} = 100\ \mu\text{A/V}^2$、$V_{SG2} - |V_{TP}| = 0.6 - (-0.47) = 1.07$ V、$\lambda = 0.1$ 和 $V_{SD2} = 1.8 - 1.5 = 0.3$ V：）

$$
1.11\ \text{mA} = \frac{1}{2}(100\ \mu)(W/L)_2(1.07)^2(1 + 0.1 \times 0.3) \tag{15}
$$

Solving,
（解得，）

$$
\left(\frac{W}{L}\right)_{M2} = 540 \tag{16}
$$

---

>记录Q点与设计结果

**Final Design Summary:**（**最终设计汇总：**）

$$
V_b = 1.1\ \text{V}, \quad V_{IN} = V_{out} + V_{TN}, \quad \left(\frac{W}{L}\right)_1 = 27.75, \quad \left(\frac{W}{L}\right)_2 = 540 \tag{17}
$$

$V_{IN}$ 由式 (10) 确定，其数值取决于最终选定的输出电平 $V_{out}$。
（$V_{IN}$ is fixed by Eq. (10); its value depends on the chosen output level $V_{out}$.）

---

## Ideal Operational Amplifier (Op-Amp) Circuit Analysis（理想运放电路分析）

Before we dive into the op-amp questions, let's review the fundamental principles and techniques for analyzing ideal op-amp circuits.
（在进入运放题目之前，我们先复习分析理想运放电路的基本原理与技巧。）

### The Golden Rules of Ideal Op-Amp Analysis（理想运放分析的黄金法则）

For an ideal op-amp in negative feedback configuration, we have two golden rules:
（对于处于负反馈配置的理想运放，有两条黄金法则：）

> [!note] Golden Rules of Ideal Op-Amps（理想运放的黄金法则）
>
> 1. **Zero input current:** No current flows into either input terminal
>    （**零输入电流：** 没有电流流入任一输入端子）
>
>    $$i_+ = i_- = 0\ \text{A}$$
>
> 2. **Equal input voltages:** The voltages at both input terminals are equal
>    （**输入电压相等：** 两个输入端子的电压相等）
>
>    $$v_+ = v_-$$
>
> **Important:** These rules only apply when the op-amp is in negative feedback and operating within its linear region (not saturated at $\pm V_{CC}$, always check that the output falls within this range).
> （**重要：** 这些法则只在运放处于负反馈且工作在线性区时适用（未在 $\pm V_{CC}$ 处饱和，务必检查输出是否落在该范围内）。）

### Systematic Analysis Strategy（系统分析策略）

When analyzing ideal op-amp circuits, follow this systematic approach:
（分析理想运放电路时，遵循以下系统化步骤：）

1. **Identify the configuration** - Recognise the topology (inverting, non-inverting, difference amplifier, etc.) if possible to quickly check your answer. Otherwise, proceed to the next steps.
   （**识别电路结构** —— 若可能，识别拓扑（反相、同相、差分放大器等），以便快速检验答案。否则继续后续步骤。）

2. **Always check negative feedback** - The golden rules only apply when the op-amp has negative feedback. Look for a connection from output back to the inverting input.
   （**始终检查负反馈** —— 黄金法则只在运放具有负反馈时适用。寻找从输出回到反相输入端的连接。）

3. **Apply Golden Rule #2:** $v_+ = v_-$ - This gives you one equation relating node voltages.
   （**应用黄金法则 #2：** $v_+ = v_-$ —— 这给出一个联系各节点电压的方程。）

4. **Check for voltage dividers** - When finding $v_+$ or $v_-$, sometimes part of the circuit is simply a voltage divider, which, if you recognise early on, can save time. Example: Q4.
   （**检查分压器** —— 求 $v_+$ 或 $v_-$ 时，有时电路的一部分就是分压器；若及早识别可节省时间。例如：第 4 题。）

5. **Apply KCL at the input nodes** - Write KCL at the $v_-$ node (and/or $v_+$ node if needed). This is usually the most effective approach because:
   （**在输入节点应用 KCL** —— 在 $v_-$ 节点（必要时也在 $v_+$ 节点）写 KCL。这通常是最有效的方法，因为：）

   - Golden Rule #1 ($i_+ = i_- = 0$) means currents must flow through passive components only
     （黄金法则 #1（$i_+ = i_- = 0$）意味着电流只能流经无源元件）
   - Input nodes typically connect to multiple resistors/impedances
     （输入节点通常连接多个电阻/阻抗）
   - You can use voltage dividers or write current equations
     （可以使用分压器或写电流方程）

6. **Do NOT write KCL for currents going into/out of the output node!** - The output node connects to the op-amp output, which can source/sink arbitrary current. KCL at the output node typically doesn't help.
   （**不要对流入/流出输出节点的电流写 KCL！** —— 输出节点连接运放输出端，它可以提供或吸收任意电流。对输出节点写 KCL 通常没有帮助。）

7. **Verify you're using both golden rules** - Your mathematical model should use:
   （**确认两条黄金法则都用上了** —— 你的数学模型应使用：）

   - $v_+ = v_-$ (Golden Rule #2)
     （$v_+ = v_-$（黄金法则 #2））
   - $i_+ = i_- = 0$ (Golden Rule #1, implicitly used in KCL at input nodes)
     （$i_+ = i_- = 0$（黄金法则 #1，在输入节点写 KCL 时隐含使用））

   If you're only using one rule, you're likely missing part of the circuit behavior!
   （如果只用了一条法则，你很可能漏掉了部分电路行为！）

8. **Solve the resulting equations** to find the desired voltages/currents. You may require additional KCL/KVL from other sections of the circuit. If finding the output voltage $v_o$, ensure it lies within the op-amp's output voltage range (e.g. $-V_{CC}$ to $+V_{CC}$) to confirm linear operation (otherwise you must "clip" it to that voltage).
   （**求解所得方程**，找出所需电压/电流。你可能需要电路其他部分的额外 KCL/KVL。若求输出电压 $v_o$，要确保它落在运放输出电压范围内（例如 $-V_{CC}$ 到 $+V_{CC}$），以确认线性工作（否则必须将其“削顶”到该电压）。）

---

## 3 Question 3（第 3 题）

The op amp in the circuit is ideal.
（电路中的运放是理想的。）

(a) What op amp circuit configuration is this?
（(a) 这是什么运放电路结构？）

(b) Calculate $v_o$.
（(b) 计算 $v_o$。）

![](Pasted%20image%2020261117154355.png)
> 图5 Enter Caption：同相放大器，同相端接 $3$ V 电压源，反相端经 $40$ k$\Omega$ 接地，$80$ k$\Omega$ 反馈电阻跨接输出与反相端，运放供电 $\pm 15$ V，输出 $v_o$

**Solution:**（**解答：**）

### 3.1 Part A（A 部分）

The given circuit is a **non-inverting amplifier**.
（给定电路是一个**同相放大器**。）

### 3.2 Part B（B 部分）

**符号说明**：
- $V^+$：同相输入端的电压
- $V^-$：反相输入端的电压
- $V_o$：输出电压（直流量记号）

---

>应用虚短：$V^-=V^+$

Since the op-amp is ideal, we have the golden rules, saying (1) the voltage at the two input pins are identical, and (2) there is no current flows into the two input pins.
（由于运放是理想的，我们使用黄金法则：(1) 两个输入引脚的电压相同；(2) 没有电流流入两个输入引脚。）

$$
V^- = V^+ = 3\ \text{V}.
$$

---

>反相端列节点方程

Applying the voltage divider rule at the inverting terminal,
（在反相端应用分压规则，）

> [!tip] 注意
> 原文称此处为“分压规则”，但所列方程实际上是反相端节点（$V^-$）的 KCL：流过 $80$ k$\Omega$ 的电流等于流过 $40$ k$\Omega$ 的电流。数值结果不受影响。

$$
\frac{V_o - V^-}{80\ \text{k}\Omega} = \frac{V^-}{40\ \text{k}\Omega}.
$$

Substituting $V^- = 3$ V,
（代入 $V^- = 3$ V，）

$$
\frac{V_o - 3}{80\ \text{k}\Omega} = \frac{3}{40\ \text{k}\Omega}.
$$

---

>求$V_o$并检验输出范围

Simplifying,
（化简，）

$$
V_o - 3 = 6 \Rightarrow V_o = 9\ \text{V}.
$$

Therefore, the output voltage is $V_o = 9$ V.
（因此，输出电压为 $V_o = 9$ V。）

> [!note] 检验
> $V_o = 9$ V 在运放供电范围 $\pm 15$ V 之内，运放工作在线性区，虚短假设成立。
> 
> 同时这也符合同相放大器增益 $1 + R_f/R_1 = 1 + 80/40 = 3$，即 $3\ \text{V} \times 3 = 9\ \text{V}$。

---

## 4 Question 4（第 4 题）

The circuit shown below is a difference amplifier. Determine the formula for $v_0$. Assume $R_a = 24$ k$\Omega$, $R_b = 75$ k$\Omega$, $R_c = 130$ k$\Omega$, and $R_d = 120$ k$\Omega$. The signal voltages $v_a$ and $v_b$ are 8 and 5 V, respectively, and $V_{CC} = \pm 20$ V.
（下图所示电路是差分放大器。求 $v_0$ 的公式。假设 $R_a = 24$ k$\Omega$、$R_b = 75$ k$\Omega$、$R_c = 130$ k$\Omega$、$R_d = 120$ k$\Omega$。信号电压 $v_a$ 和 $v_b$ 分别为 8 V 和 5 V，$V_{CC} = \pm 20$ V。）

(a) Find the value for $v_0$.
（(a) 求 $v_0$ 的值。）

(b) What is the resistance seen by the signal source $v_a$?
（(b) 信号源 $v_a$ 看到的电阻是多少？）

(c) What is the resistance seen by the signal source $v_b$?
（(c) 信号源 $v_b$ 看到的电阻是多少？）

![](Pasted%20image%2020261117154429.png)
> 图6 Q4 circuit diagram with annotations：差分放大器，$v_a$ 经 $R_a$ 接反相端，$R_b$ 为反馈电阻；$v_b$ 经 $R_c$ 接同相端，$R_d$ 由同相端接地；下附手绘标注版（$8$ V、$5$ V、$i_a$、$i_b$、$v_n$、$v_p$）

### 4.1 Part A（A 部分）

**符号说明**：
- $V^+$、$V^-$：同相端、反相端电压
- $V_o$：输出电压（题面写作 $v_0$，本文按解答原记号 $V_o$）
- $i_a$、$i_b$：流经 $R_a$、$R_c$ 的电流
- $R_{in,a}$、$R_{in,b}$：信号源 $v_a$、$v_b$ 看到的输入电阻

---

>虚短与节点电流

Applying the ideal op-amp conditions, we have
（应用理想运放条件，有）

$$
V^- = V^+ \tag{1}
$$

$$
\frac{V_o - V^-}{R_b} = \frac{V^- - V_a}{R_a} = -i_a \tag{2}
$$

$$
\frac{V_b - V^+}{R_c} = \frac{V^+}{R_d} = i_b \tag{3}
$$

---

>求$V^+$

The voltage at the non-inverting terminal can be found from the voltage divider:
（同相端电压可由分压器求得：）

$$
V^+ = \frac{5}{\left(\frac{R_c}{R_d} + 1\right)} = \frac{5}{\left(\frac{130}{120} + 1\right)} = 2.4\ \text{V} \tag{4}
$$

Thus, $V^- = V^+ = 2.4$ V.
（因此，$V^- = V^+ = 2.4$ V。）

---

>求$V_o$

The output voltage can be expressed as
（输出电压可表示为）

$$
V_o = V^- + R_b\frac{V^- - V_a}{R_a} \tag{5}
$$

Substituting the known values:
（代入已知值：）

$$
V_o = 2.4 + (75\ \text{k}\Omega)\frac{2.4 - 8}{24\ \text{k}\Omega} \tag{6}
$$

Evaluating gives
（计算得）

$$
V_o = 2.4 + 75 \times (-0.233) = -15.1\ \text{V} \tag{7}
$$

Hence, the output voltage is
（因此，输出电压为）

$$
V_o = -15.1\ \text{V} \tag{8}
$$

> [!note] 线性区检验
> $V_o = -15.1$ V 落在 $\pm 20$ V 供电范围内，运放未饱和，理想运放假设有效。

### 4.2 Part B（B 部分）

---

>求$i_a$

The current through $R_a$ is
（流过 $R_a$ 的电流为）

$$
i_a = \frac{V_a - V^-}{R_a} = \frac{8 - 2.4}{24\ \text{k}\Omega} = 0.233\ \text{mA} \tag{9}
$$

---

>求$R_{in,a}$

The input resistance seen by $V_a$ is
（$V_a$ 看到的输入电阻为）

$$
R_{in,a} = \frac{V_a}{i_a} = \frac{8}{0.233\ \text{mA}} = 34.3\ \text{k}\Omega \tag{10}
$$

### 4.3 Part C（C 部分）

---

>求$i_b$

The current through $R_c$ is
（流过 $R_c$ 的电流为）

$$
i_b = \frac{V_b - V^+}{R_c} = \frac{5 - 2.4}{130\ \text{k}\Omega} = 0.02\ \text{mA} \tag{11}
$$

---

>求$R_{in,b}$

The input resistance seen by $V_b$ is
（$V_b$ 看到的输入电阻为）

$$
R_{in,b} = \frac{V_b}{i_b} = \frac{5}{0.02\ \text{mA}} = 250\ \text{k}\Omega \tag{12}
$$

---

### Complex Impedances（复阻抗）

> [!info] Complex Impedances（复阻抗）
>
> Op-amp circuits often involve capacitors and inductors, which introduce frequency-dependent impedances. You can treat these similarly to resistors, but with impedances. Keep these points in mind:
> （运放电路常包含电容和电感，它们引入随频率变化的阻抗。可以像处理电阻那样处理它们，只是改用阻抗。请记住以下几点：）
>
> 1. **For impedance/admittance problems** - Remember:
>    （**对于阻抗/导纳问题** —— 记住：）
>
>    - Capacitor: impedance $Z_C(s) = \dfrac{1}{Cs}$, admittance $Y_C(s) = Cs$
>      （电容：阻抗 $Z_C(s) = \dfrac{1}{Cs}$，导纳 $Y_C(s) = Cs$）
>    - Inductor: $Z_L(s) = Ls$, $Y_L(s) = \dfrac{1}{Ls}$
>      （电感：$Z_L(s) = Ls$，$Y_L(s) = \dfrac{1}{Ls}$）
>    - Resistor: $Z_R(s) = R$, $Y_R(s) = \dfrac{1}{R}$
>      （电阻：$Z_R(s) = R$，$Y_R(s) = \dfrac{1}{R}$）
>
> 2. **Parallel combinations** - For parallel impedances:
>    （**并联组合** —— 对于并联阻抗：）
>
> $$
> Z_{parallel} = \frac{Z_1 Z_2}{Z_1 + Z_2} = \frac{1}{\frac{1}{Z_1} + \frac{1}{Z_2}}
> $$
>
> Sometimes it's easier to work with admittances: $Y_{parallel} = Y_1 + Y_2$
> （有时用导纳更方便：$Y_{parallel} = Y_1 + Y_2$）

---

## 5 Question 5（第 5 题）

Find the values of $R$, $L$ and $C$ to implement the admittance shown in the figure below. *Hint:* If an expression for an impedance or admittance does not look to be of a form which can be readily implemented, try inverting it.
（求使下图所示导纳得以实现的 $R$、$L$、$C$ 值。*提示：* 若某阻抗或导纳的表达式看起来不是可以直接实现的形式，尝试取其倒数。）

![](Pasted%20image%2020261117154456.png)
> 图7 Enter Caption：$R$ 串联 $L$ 与 $C$ 的并联组合；给定 $Y(s) = \dfrac{\frac{3}{2}\left(s^2 + \frac{3}{4}\right)}{s^2 + \frac{2}{3}s + \frac{3}{4}}$

**Solution:**（**解答：**）

**符号说明**：
- $Y(s)$：导纳（阻抗的倒数）
- $Z(s)$：阻抗
- $s$：复频率变量
- $R$、$L$、$C$：待求的电阻、电感、电容

---

>求$Z(s)$

Given: The impedance of a capacitor and an inductor are respectively
（已知：电容和电感的阻抗分别为）

$$
Z_C = \frac{1}{Cs} \tag{1}
$$

$$
Z_L = Ls \tag{2}
$$

and admittance is defined as the reciprocal of impedance:
（且导纳定义为阻抗的倒数：）

$$
Y(s) = \frac{1}{Z(s)} \tag{3}
$$

From the given admittance function:
（由给定导纳函数：）

$$
Z(s) = \frac{1}{Y(s)} = \frac{s^2 + \frac{2}{3}s + \frac{3}{4}}{\frac{3}{2}(s^2 + 4)} \tag{4}
$$

---

>部分分式展开

Simplifying,
（化简，）

$$
Z(s) = \frac{2}{3} + \frac{\frac{49s}{3}}{s^2 + 4} \tag{5}
$$

We can write this as
（可将其写成）

$$
Z(s) = R + (Z_C(s) \parallel Z_L(s)) \tag{6}
$$

---

>匹配常数项，求$R$

Comparing Eq. (5) with Eq. (6),
（比较式 (5) 与式 (6)，）

$$
R = \frac{2}{3}\ \Omega \tag{7}
$$

---

>求$L$、$C$

Now, for the parallel combination of $Z_C$ and $Z_L$:
（现在看 $Z_C$ 与 $Z_L$ 的并联组合：）

$$
Z_C(s) \parallel Z_L(s) = \frac{Z_C(s) Z_L(s)}{Z_C(s) + Z_L(s)} \tag{8}
$$

Substitute $Z_C = 1/(Cs)$ and $Z_L = Ls$ into Eq. (8):
（将 $Z_C = 1/(Cs)$、$Z_L = Ls$ 代入式 (8)：）

$$
Z_C(s) \parallel Z_L(s) = \frac{\frac{1}{Cs}(Ls)}{\frac{1}{Cs} + Ls} \tag{9}
$$

Simplify:
（化简：）

$$
Z_C(s) \parallel Z_L(s) = \frac{L/C \cdot s^2}{s^2 + \frac{1}{CL}} = \frac{\frac{49s}{3}}{s^2 + 4} \tag{10}
$$

Equating coefficients from Eq. (10):
（由式 (10) 比较系数：）

$$
\frac{L}{C} = \frac{4}{9} \tag{11}
$$

$$
\frac{1}{CL} = \frac{3}{4} \tag{12}
$$

From Eqs. (11) and (12), solving for $L$ and $C$ gives:
（由式 (11) 和 (12) 解 $L$ 和 $C$ 得：）

$$
C = \frac{9}{4} \tag{13}
$$

$$
L = \frac{16}{27} \tag{14}
$$

---

>最终结果

**Final Results:**（**最终结果：**）

$$
R = \frac{2}{3}\ \Omega, \quad C = \frac{9}{4}\ \text{F}, \quad L = \frac{16}{27}\ \text{H} \tag{15}
$$

---

## 6 Question 6（第 6 题）

What is the transfer function $A_v(s) = \dfrac{V_o(s)}{V_i(s)}$ for the circuit in Fig. P10.115? Draw a Bode plot for the transfer function.
（图 P10.115 中电路的传递函数 $A_v(s) = \dfrac{V_o(s)}{V_i(s)}$ 是什么？画出该传递函数的 Bode 图。）
![](Pasted%20image%2020261117154513.png)
> 图Q6-1 Fig. P10.115：反相运放电路，$v_i$ 经 $R_1$ 与 $C$ 并联支路接反相端，$R_2$ 为反馈电阻，同相端接地，输出 $v_o$

**Solution:**（**解答：**）

**符号说明**：
- $A_V(s)$：传递函数 $V_o(s)/V_i(s)$
- $R_1$：输入端电阻
- $R_2$：反馈电阻
- $Z_C$：电容 $C$ 的阻抗

---

>虚地与反相端 KCL

Given: The op-amp is ideal, so
（已知：运放是理想的，因此）

$$
V^- = V^+ = 0 \tag{1}
$$

Applying KCL at the inverting input node:
（在反相输入节点应用 KCL：）

$$
\frac{V_o - V^-}{R_2} = \frac{V^- - V_i}{Z_C \parallel R_1} \tag{2}
$$

Substitute $Z_C = 1/(Cs)$:
（代入 $Z_C = 1/(Cs)$：）

$$
\frac{V_o}{R_2} = -\frac{V_i}{\left(\frac{1}{Cs}\right) \parallel R_1} \tag{3}
$$

---

>化简$A_V(s)$

Simplifying Eq. (3) gives the voltage gain:
（化简式 (3) 得到电压增益：）

$$
A_V = \frac{V_o}{V_i} = -\frac{R_2}{R_1}(R_1 Cs + 1) \tag{4}
$$

We can also express it equivalently as:
（也可等价地写成：）

$$
A_V = -\frac{R_2}{R_1}\left(\frac{s}{\frac{1}{R_1 C}} + 1\right) \tag{5}
$$

---

>Bode 图

Assuming $R_2 > R_1$, the system exhibits a high-frequency gain increase due to the capacitor $C$. The frequency response (Bode magnitude plot) is represented as:
（假设 $R_2 > R_1$，由于电容 $C$，系统在高频段增益上升。频率响应（Bode 幅值图）表示为：）

$$
H(s) = 20 \log_{10}|A_V| \tag{6}
$$

**Final Expression:**（**最终表达式：**）

$$
A_V(s) = -\frac{R_2}{R_1}(1 + sR_1C) \tag{7}
$$

And the scratch Bode plot is below.
（草图 Bode 图如下。）

![](Pasted%20image%2020261117154528.png)
> 图8 Q6 Bode plot（手绘幅频特性：低频段电平 $20\log(R_2/R_1)$，转折频率 $1/(R_1C)$，高频段斜率 $20$ dB/dec）

> [!note] 传递函数的极点与零点
> 该传递函数在 $s = -1/(R_1C)$ 处有一个零点，没有有限极点；在 $\omega > 1/(R_1C)$ 后幅值以 $20$ dB/dec 上升。

---
