# ELEC2104/9704 Tutorial 7 Solutions (2025)

## Motivation: BJT Amplifiers（动机：BJT 放大器）

In this course, we're particularly interested in using BJTs as **amplifiers**.（本课程特别关注把 BJT 用作**放大器**。） 

BJTs excel as amplifiers due to their exponential $I_C = I_S e^{V_{BE}/V_T}$ relationship, providing high transconductance ($g_m = I_C/V_T$).（BJT 适合做放大器，是因为其指数关系 $I_C=I_Se^{V_{BE}/V_T}$ 有较高的跨导（$g_m=I_C/V_T$）。） 

That is, small changes in base-emitter voltage $V_{BE}$ lead to large changes in collector current $I_C$.（也就是说，基极-发射极电压 $V_{BE}$ 的微小变化会引起集电极电流 $I_C$ 的很大变化。）

### Small Signal Inputs vs. Large Signal Inputs（小信号输入与大信号输入）

**小信号输入（small-signal input）：** 幅度足够小、使晶体管始终工作在 Q 点附近近似线性区的输入信号。通常满足 $|v_{be}|\ll V_T$（$V_T\approx26$ mV，工程上常取几 mV 以内）。此时 $I_C$–$V_{BE}$ 曲线在 Q 点附近可近似为切线，$i_c=g_mv_{be}$，可用线性小信号模型分析，输出无明显失真。

**符号约定（notation）：** 大写符号 $V_{BE}$、$I_C$、$I_B$ 表示直流（静态）量；小写符号 $v_{be}$、$i_c$、$i_b$ 表示交流小信号量；小写字母配合大写下标（如 $v_{BE}$、$i_C$）表示瞬时总量，即

$$
v_{BE}=V_{BE}+v_{be},\qquad i_C=I_C+i_c
$$

因此判据 $|v_{be}|\ll V_T$ 指的是**交流信号的幅度**远小于热电压，而不是直流偏置 $V_{BE}$（约 0.7 V）小于 $V_T$。

**大信号输入（large-signal input）：** 幅度较大、使晶体管在特性曲线的较大范围内摆动（甚至进入截止区或饱和区）的输入信号。此时线性近似不再成立，必须使用指数关系 $I_C=I_Se^{V_{BE}/V_T}$ 或分段模型（理想二极管模型、恒压降模型等）分析，并考虑输出波形的失真。

小信号与大信号之间没有绝对的电压界限，取决于允许的失真程度：一般认为 $|v_{be}|$ 在几 mV 量级时可作小信号处理；接近或超过 $V_T$ 时，非线性失真已不可忽略。

**However**, the very property that makes BJTs good amplifiers (the exponential relationship) also creates a challenge: distortion!（**然而**，正是让 BJT 成为好放大器的这一特性（指数关系）也带来了一个难题：失真！）

The $I_C$-$V_{BE}$ curve is highly nonlinear, as shown in Figure 1.（$I_C$–$V_{BE}$ 曲线高度非线性，如图 1 所示。）

Large input signals cause the transistor to operate over a wide range of this curve, leading to distortion in the output signal (see in blue).（大输入信号使晶体管在这条曲线的很大范围内工作，导致输出信号失真（见图中的蓝色部分）。）

![](Pasted%20image%2020261114214042.png)
> 图1 BJT nonlinearity: Large signals experience distortion due to the exponential $I_C$-$V_{BE}$ relationship, while small signals remain in the approximately linear region around the Q-point.（图 1：BJT 的非线性——大信号因指数型 $I_C$–$V_{BE}$ 关系而失真，小信号则保持在 Q 点附近的近似线性区。）

**Small signal inputs** (see in green) keep the transistor operating near a specific point on the curve, called the **Quiescent point (Q-point)**.（**小信号输入**（见绿色）使晶体管工作在曲线上某个特定点附近，该点称为**静态工作点（Q 点）**。）

Around this point, we can approximate the exponential curve as a straight line (the tangent with slope = $g_m$), allowing for *linear amplification without distortion*.（在该点附近，可把指数曲线近似为一条直线（斜率为 $g_m$ 的切线），从而实现*无失真的线性放大*。）

**Q-point location** - We deliberately position the Q-point on the $I_C$-$V_{BE}$ characteristic curve by selecting an appropriate DC collector current $I_{C,Q}$.（**Q 点的位置的选择**——选取合适的直流集电极电流 $I_{C,Q}$，人为地把 Q 点设在 $I_C$–$V_{BE}$ 特性曲线上。）


This choice involves trade-offs:（这一选择需要权衡：）

- **Higher** $I_{C,Q}$ → Higher $g_m$ → Better gain, but more power consumption（**较高的** $I_{C,Q}$ → 较大的 $g_m$ → 增益更好，但功耗更大）
- **Lower** $I_{C,Q}$ → Lower power, but reduced gain and bandwidth（**较低的** $I_{C,Q}$ → 功耗更小，但增益和带宽下降）

As Figure 1 demonstrates, the Q-point acts as the "center" of our linear approximation.（如图 1 所示，Q 点充当线性近似的“中心”。）

The tangent line (slope = $g_m$) at the Q-point defines how small signals are amplified without distortion.（Q 点处的切线（斜率 $=g_m$）决定了小信号如何被无失真地放大。）

To set this Q-point, we use a special circuit topology called a **Biasing network**.（为设置该 Q 点，需要一种称为**偏置网络**的特殊电路结构。）

We will see examples of these circuits in Q1 and Q2.（第 1、2 题将给出这类电路的例子。）

### Small Signal Analysis（小信号分析）

The distinction between small signals and large signals for BJTs leads us to a powerful technique for analyzing BJT amplifier circuits: **Small-signal analysis**!（BJT 中小信号与大信号的区分，引出了分析 BJT 放大器电路的一种有力方法：**小信号分析**！）

This technique is based on **linearization around the Q-point**.（该方法基于**在 Q 点附近线性化**。）

Mathematically, we approximate the nonlinear exponential curve $I_C = I_S e^{V_{BE}/V_T}$ with its first-order Taylor expansion around the Q-point:（数学上，用该指数曲线在 Q 点的一阶泰勒展开作近似：）

$$
I_C \approx I_{C,Q} + g_m \cdot (V_{BE} - V_{BE,Q})
$$

where $g_m = \left.\dfrac{\mathrm{d}I_C}{\mathrm{d}V_{BE}}\right|_Q = \dfrac{I_{C,Q}}{V_T}$ is the transconductance (slope of the tangent line in Figure 1).（式中 $g_m=\left.\dfrac{\mathrm{d}I_C}{\mathrm{d}V_{BE}}\right|_Q=\dfrac{I_{C,Q}}{V_T}$ 为跨导（图 1 中切线的斜率）。）

This linear approximation is *only valid for small signals* because higher-order terms in the Taylor series become significant for large deviations from the Q-point.（该线性近似*仅对小信号成立*，因为偏离 Q 点较大时，泰勒级数的高阶项会变得显著。）

The beauty: this transforms complex nonlinear circuit analysis into straightforward linear circuit analysis using familiar techniques like Ohm's law and voltage dividers!（其妙处在于：它把复杂的非线性电路分析转化为简单的线性电路分析，可用欧姆定律、分压等熟悉方法。）

This linearization enables us to create the **hybrid-$\pi$ small-signal model**—a linear equivalent circuit that replaces the nonlinear BJT for small-signal analysis:（这种线性化使我们能够建立 **hybrid-$\pi$ 小信号模型**——一种用于小信号分析的线性等效电路，用来替代非线性 BJT：）

![](Pasted%20image%2020261114214103.png)
> 图2 Hybrid-$\pi$ small-signal model: The linear equivalent circuit that replaces the nonlinear BJT for small-signal analysis. All parameters depend on the Q-point!（图 2：hybrid-$\pi$ 小信号模型——用于小信号分析的线性等效电路，替代非线性 BJT。所有参数都依赖于 Q 点！）

### Small Signal Analysis vs. Large Signal Analysis（小信号分析与大信号分析）

In this course, we approach BJT amplifier analysis by following two sequential analysis techniques:（本课程按以下两个先后步骤分析 BJT 放大器：）

1. **Large-Signal (DC) Analysis**: First, we find the DC operating point (yet another name for the Q-point) in the absence of any AC signals.（**大信号（直流）分析**：首先，在没有交流信号的情况下求直流工作点（Q 点的另一种叫法）。） This tells us where the transistor is "sitting" when no signal is applied.（它告诉我们无信号时晶体管“停留”在何处。） Here, "DC" means constant (time-invariant) voltages and currents.（这里“直流”指恒定（不随时间变化）的电压和电流。）
2. **Small-Signal (AC) Analysis**: Second, we study how the circuit responds to small AC signals *superimposed* onto the DC operating point.（**小信号（交流）分析**：其次，研究电路对*叠加*在直流工作点上的小交流信号的响应。） Here, "AC" refers to **any time-varying signal** (not just sinusoidal!) that is small enough to remain in the linear region around the Q-point, e.g. square waves, triangular waves, audio signals, etc.（这里“交流”指**任何随时间变化的信号**（不限于正弦波！），只要它足够小、仍处于 Q 点附近的线性区，例如方波、三角波、音频信号等。）

### Notation Convention（符号约定）

Throughout this course, we use a consistent notation to distinguish DC and AC quantities:（本课程采用统一的符号约定区分直流量与交流量：）

- **Capital letters** for DC (large-signal) quantities: $V_C$, $I_B$, $V_{BE}$, $I_C$, etc.（**大写字母**表示直流（大信号）量：$V_C$、$I_B$、$V_{BE}$、$I_C$ 等。）
- **Lowercase letters** for AC (small-signal) quantities: $v_c$, $i_b$, $v_{be}$, $i_c$, etc.（**小写字母**表示交流（小信号）量：$v_c$、$i_b$、$v_{be}$、$i_c$ 等。）

### Q-Point: Bridging Between Large and Small（Q 点：连接大信号与小信号）

The crucial connection between these two analysis steps is that **we need to know $I_C$ (the DC collector current) to build our small-signal model**.（这两步分析之间的关键联系是：**必须知道 $I_C$（直流集电极电流）才能建立小信号模型**。）

The transconductance $g_m = I_C/V_T$ is the fundamental parameter that determines how the BJT amplifies signals.（跨导 $g_m=I_C/V_T$ 是决定 BJT 放大能力的基本参数。）

Without knowing the DC operating point, we cannot determine the small-signal behavior!（不知道直流工作点，就无法确定小信号行为！）

This is why we must perform large-signal analysis first.（这就是必须先做大信号分析的原因。）

Note that the Q-point $Q = (I_C, V_{CE})$ is expressed with the collector current $I_C$ and the collector-emitter voltage $V_{CE}$.（注意，Q 点 $Q=(I_C,V_{CE})$ 用集电极电流 $I_C$ 和集电极-发射极电压 $V_{CE}$ 表示。）

Only $I_C$ directly influences the small-signal parameters like $g_m$, $r_\pi$, and $r_o$.（只有 $I_C$ 直接影响 $g_m$、$r_\pi$、$r_o$ 等小信号参数。）

The voltage $V_{CE}$ is primarily used to verify that the BJT is operating in the forward active region (i.e. $V_{CE} > V_{BE}$ for npn BJTs).（$V_{CE}$ 主要用于检验 BJT 是否工作在放大区（对 npn 管即 $V_{CE}>V_{BE}$）。）

Also, **note that the $V_{BE}$ voltage is not part of the Q-point**, but knowing the Q-point guarantees knowing $V_{BE}$.（另外，**注意 $V_{BE}$ 不属于 Q 点**，但知道 Q 点就必然知道 $V_{BE}$。）

### BJT Analysis Procedure（BJT 分析步骤）

The standard procedure for analyzing BJT amplifier circuits focuses on finding the two key quantities: collector current $I_C$ and collector-emitter voltage $V_{CE}$.（分析 BJT 放大器电路的标准步骤，重点是求两个关键量：集电极电流 $I_C$ 和集电极-发射极电压 $V_{CE}$。）

Assume forward active region, then:（先假设工作在放大区，然后：）

**Step 1: Large-Signal (DC) Analysis**（第 1 步：大信号（直流）分析）

1. Find $I_C$ and $V_{CE}$ using standard circuit analysis techniques (may need Thevenin equivalence).（用标准电路分析方法求 $I_C$ 和 $V_{CE}$（可能需要戴维南等效）。）

   - Use KCL/KVL to write equations for the circuit (typically 2x KVL loop equations).（用 KCL/KVL 列方程（通常为 2 个 KVL 回路方程）。）
   - Use the exponential relationship to relate $V_{BE}$ to $I_C$: $V_{BE} = V_T \ln(I_C/I_S)$ (no Early Effect).（用指数关系联系 $V_{BE}$ 与 $I_C$：$V_{BE}=V_T\ln(I_C/I_S)$（不计厄利效应）。）
   - If you end up with equation terms of $I_B$, use $I_C = \beta_0 I_B$ to express these in terms of $I_C$.（若方程中出现 $I_B$，用 $I_C=\beta_0I_B$ 化为 $I_C$。）
   - For terms of $I_E$, use $I_E = I_C + I_B = I_C(1 + 1/\beta_0)$ to express in terms of $I_C$.（出现 $I_E$ 时，用 $I_E=I_C+I_B=I_C(1+1/\beta_0)$ 化为 $I_C$。）

2. **Verify the forward active assumption:** Check that $V_{BE,\mathrm{on}} \leq V_{BE} \leq V_{CE}$（**验证放大区假设：** 检查 $V_{BE,\mathrm{on}}\leq V_{BE}\leq V_{CE}$）

3. Record Q-point: $Q = (I_C, V_{CE})$（记录 Q 点：$Q=(I_C,V_{CE})$）

**Step 2: Small-Signal (AC) Analysis**（第 2 步：小信号（交流）分析）

1. Calculate small-signal parameters from Q-point:（由 Q 点计算小信号参数：）

$$
g_m = \frac{I_C}{V_T} \tag{1}
$$

$$
r_\pi = \frac{\beta_0}{g_m} \tag{2}
$$

$$
r_o = \frac{V_A}{I_C} \tag{3}
$$

2. Replace the BJT circuit symbol with the linearised hybrid-$\pi$ model within the circuit diagram.（在电路图中用线性化 hybrid-$\pi$ 模型替代 BJT 符号。）

3. Set all DC independent sources to zero (current sources become open circuits, voltage sources become short circuits).（把所有直流独立源置零（电流源开路、电压源短路）。）

4. Analyze the resulting circuit diagram using standard linear circuit analysis techniques.（用标准线性电路分析方法分析所得电路。）

   - If the amplifier is a common-emitter topology (as in most questions), you should find that (with collector resistor $R_C$ and load resistor $R_L$):（若为共射组态（多数题目如此），应得到（集电极电阻 $R_C$、负载电阻 $R_L$）：）

$$
R_{in} = r_\pi \tag{4}
$$

$$
R_{out} = r_o \parallel R_C \tag{5}
$$

$$
A_v = -g_m \cdot (R_C \parallel r_o \parallel R_L) \tag{6}
$$

   - More on amplifier topologies and parameters in the following tutorials!（更多放大电路组态与参数见后续辅导课！）

In this course, you'll rarely encounter problems where the BJT operates in saturation or cutoff (but it is still possible) — we focus on the amplifying region!（本课程很少遇到 BJT 工作在饱和或截止区的问题（但仍有可能）——我们聚焦放大区！）

> [!warning] Critical Assumption: Forward Active Region Only!（关键假设：仅适用于放大区！）
>
> **IMPORTANT:** Both small-signal and large-signal analysis techniques we use in this course are **only valid in the forward active region** of the BJT!（**重要：** 本课程使用的小信号与大信号分析方法，**只在 BJT 的放大区**成立！）
>
> The exponential relationship $I_C = I_S e^{V_{BE}/V_T}$ is not a universal law—it's simply a mathematical approximation that models a BJT operating in forward active mode.（指数关系 $I_C=I_Se^{V_{BE}/V_T}$ 不是普遍规律，而只是描述放大区 BJT 的数学近似。）
>
> Outside this region (cutoff, saturation), the relationship breaks down completely.（在该区域之外（截止、饱和），这一关系完全失效。）
>
> **Check** as a *rule of thumb* that your calculated voltages satisfy $V_C > V_B > V_E$ (npn) or $V_E > V_B > V_C$ (pnp).（作为*经验法则*，检查算出的电压是否满足 $V_C>V_B>V_E$（npn）或 $V_E>V_B>V_C$（pnp）。）

### BJT Non-Ideal Behavior: Early Effect（BJT 的非理想特性：厄利效应）

In our previous analysis, we assumed the ideal BJT relationship $I_C = I_S e^{V_{BE}/V_T}$, where the collector current depends only on the base-emitter voltage $V_{BE}$.（前面的分析假设了理想 BJT 关系 $I_C=I_Se^{V_{BE}/V_T}$，即集电极电流只取决于基极-发射极电压 $V_{BE}$。）

However, real BJTs exhibit a non-ideal phenomenon called the **Early Effect**, where the collector current also depends on the collector-emitter voltage $V_{CE}$.（然而，实际 BJT 存在一种称为**厄利效应**的非理想现象：集电极电流还依赖于集电极-发射极电压 $V_{CE}$。）

#### Early Effect in Large-Signal (DC) Analysis（厄利效应在大信号（直流）分析中的表现）

Early Effect is described in the mathematical model by including a $V_{CE}$ term:（在数学模型中通过引入 $V_{CE}$ 项来描述厄利效应：）

$$
I_C = I_S e^{V_{BE}/V_T}\left(1 + \frac{V_{CE}}{V_A}\right)
$$

where $V_A$ is the Early voltage.（式中 $V_A$ 为厄利电压。）

This equation shows that:（该式表明：）

- Higher $V_{CE}$ ⇒ higher $I_C$ (for fixed $V_{BE}$)（$V_{CE}$ 越高 ⇒ $I_C$ 越大（固定 $V_{BE}$ 时））
- When $V_A \rightarrow \infty$ (infinite Early voltage), we recover the ideal model.（当 $V_A\to\infty$（厄利电压无穷大）时，回到理想模型。）

The Early Effect also affects the current gain:（厄利效应也会影响电流增益：）

$$
\beta_F = \beta_{F0}\left(1 + \frac{V_{CE}}{V_A}\right)
$$

where $\beta_{F0}$ is the zero-bias current gain.（式中 $\beta_{F0}$ 为零偏电流增益。）

#### Early Effect in Small-Signal (AC) Models（厄利效应在小信号（交流）模型中的表现）

In small-signal analysis, the Early Effect manifests as a **finite output resistance $r_o$** in the hybrid-$\pi$ model.（在小信号分析中，厄利效应表现为 hybrid-$\pi$ 模型中的**有限输出电阻 $r_o$**。）

Recall from Figure 2 that we include this resistance between collector and emitter.（回顾图 2，该电阻接在集电极与发射极之间。）

This resistance is given (approximated) by:（该电阻（近似）为：）

$$
r_o = \frac{V_A}{I_C}
$$

Infinite Early voltage ($V_A \rightarrow \infty$) gives infinite output resistance (ideal current source).（厄利电压无穷大（$V_A\to\infty$）对应输出电阻无穷大（理想电流源）。）

Questions will assume $V_A = \infty$, an infinite Early voltage (i.e. no Early Effect), unless otherwise specified.（除非另有说明，题目均假设 $V_A=\infty$，即厄利电压无穷大、忽略厄利效应。）

## 1 Question 1 Solution（第 1 题解答）

### 1.1 Part A（A 部分）

Determine the operating point and the small-signal model of $Q_1$ for each of the circuits shown below.（求下列各电路中 $Q_1$ 的工作点与小信号模型。）

Assume $I_S = 8 \times 10^{-16}$ A, $V_T = 26$ mV, $\beta = 100$, $V_A = \infty$.（假设 $I_S=8\times10^{-16}$ A、$V_T=26$ mV、$\beta=100$、$V_A=\infty$。）

![](Pasted%20image%2020261114214130.png)
> 图Q1-1 题 1(a)(b)(c) 三个电路（（a）$R_C=50\ \Omega$，$V_{CC}=2.5$ V，基极接 0.8 V 电压源；（b）$R_C=1$ k$\Omega$，$V_{CC}=2.5$ V，基极接 10 µA 电流源；（c）$R_C=1$ k$\Omega$，$V_{CC}=2.5$ V，基极与集电极短接）

*Recall the typical steps for large-signal analysis of a BJT circuit:*（回顾 BJT 电路大信号分析的典型步骤：）

1. Find $I_C$ and $V_{CE}$ using standard circuit analysis techniques (may need Thevenin equivalence).（用标准电路分析方法求 $I_C$ 和 $V_{CE}$（可能需要戴维南等效）。）

   - Use KCL/KVL to write equations for the circuit (typically 2x KVL loop equations).（用 KCL/KVL 列方程（通常为 2 个 KVL 回路方程）。）
   - Use the non-linear $I_C$-$V_{BE}$ relationship to relate $V_{BE}$ to $I_C$ (no Early Effect!).（用非线性 $I_C$–$V_{BE}$ 关系联系 $V_{BE}$ 与 $I_C$（不计厄利效应！）。）
   - If you end up with equation terms of $I_B$, use $I_C = \beta_0 I_B$ to express these in terms of $I_C$.（若方程中出现 $I_B$，用 $I_C=\beta_0I_B$ 化为 $I_C$。）
   - For terms of $I_E$, use $I_E = I_C + I_B = I_C(1 + 1/\beta_0)$ to express in terms of $I_C$.（出现 $I_E$ 时，用 $I_E=I_C+I_B=I_C(1+1/\beta_0)$ 化为 $I_C$。）

2. **Verify the forward active assumption:** Check that $V_{BE,\mathrm{on}} \leq V_{BE} \leq V_{CE}$（**验证放大区假设：** 检查 $V_{BE,\mathrm{on}}\leq V_{BE}\leq V_{CE}$）

3. Record Q-point: $Q = (I_C, V_{CE})$（记录 Q 点：$Q=(I_C,V_{CE})$）

**Note that $V_A = \infty$ in this question, so Early Effect does not apply!**（注意本题 $V_A=\infty$，因此不考虑厄利效应！）

**Large-signal analysis:**（**大信号分析：**）

In this circuit diagram, we notice that the BJT base is *directly* connected to a voltage source of 0.8 V.（观察电路图可知，BJT 基极*直接*接到 0.8 V 电压源。）

This is generous - we can directly derive $V_{BE}$ which (without Early Effect) means we have $I_C$ ✓✓（这很方便——可直接得到 $V_{BE}$；在不计厄利效应时，也就得到 $I_C$ ✓✓）

$V_E$ is connected to ground, so $V_E = 0$ V:（$V_E$ 接地，故 $V_E=0$ V：）

$$
V_{BE} = V_B - V_E = 0.8\ \text{V} - 0\ \text{V} = 0.8\ \text{V} \tag{1}
$$

Using the relationship between $I_C$ and $V_{BE}$ (no Early Effect) and the known $V_{BE}$, we can determine:（利用 $I_C$ 与 $V_{BE}$ 的关系（不计厄利效应）及已知的 $V_{BE}$，可得：）

$$
I_C = I_S \cdot \exp\left(\frac{V_{BE}}{V_T}\right) = (8 \times 10^{-16}\ \text{A})\exp\left(\frac{0.8\ \text{V}}{0.026\ \text{V}}\right) = 18.5\ \text{mA}
$$

**Finding $V_{CE}$:** Using a KVL loop through $R_C$ and the collector (or just Ohm's law):（**求 $V_{CE}$：** 对 $R_C$ 和集电极取 KVL 回路（或直接用欧姆定律）：）

$$
V_C = V_{CC} - I_C R_C = 2.5\ \text{V} - (0.0185\ \text{A}) \cdot (50\ \Omega) = 1.58\ \text{V} \tag{2}
$$

Then, we can determine $V_{CE}$.（于是可求 $V_{CE}$。）

$$
V_{CE} = V_C - V_E = 1.58\ \text{V} - 0\ \text{V} = 1.58\ \text{V} \tag{3}
$$

Sanity check for forward active region: $V_{BE,\mathrm{on}} \leq V_{BE} \leq V_{CE}$.（放大区合理性检查：$V_{BE,\mathrm{on}}\leq V_{BE}\leq V_{CE}$。）

Assuming $V_{BE,\mathrm{on}}$ is around 0.6 - 0.7 V, we have $0.7\ \text{V} \leq 0.8\ \text{V} \leq 1.58\ \text{V}$ ✓✓（取 $V_{BE,\mathrm{on}}$ 约 0.6–0.7 V，则有 $0.7\ \text{V}\leq0.8\ \text{V}\leq1.58\ \text{V}$ ✓✓）

Therefore, the Q-point of the BJT is:（因此，BJT 的 Q 点为：）

$$
Q = (I_C, V_{CE}) = (18.5\ \text{mA}, 1.58\ \text{V})
$$

**Remark:** Note that in this case, we did not need to use Thevenin equivalence or write 2x KVL equations because the circuit is simple in that $V_{BE}$ was effectively given.（**备注：** 本例中无需戴维南等效或列两个 KVL 方程，因为电路简单，$V_{BE}$ 实际上已直接给出。）

**Small-signal analysis:**（**小信号分析：**）

According to the given current gain $\beta = 100$ and the thermal voltage $V_T = 0.026$ V, (and $V_A = \infty \Rightarrow$ no Early Effect) we can determine the following small signal parameters:（由已知电流增益 $\beta=100$、热电压 $V_T=0.026$ V（且 $V_A=\infty$，无厄利效应），可求以下小信号参数：）

$$
g_m = \frac{I_C}{V_T} = \frac{0.0185\ \text{A}}{0.026\ \text{V}} = 0.71\ \text{S} \tag{4}
$$

$$
r_\pi = \frac{\beta}{g_m} = \frac{100}{0.71\ \text{S}} = 141\ \Omega \tag{5}
$$

$$
r_o = \frac{V_A}{I_C} = \frac{\infty}{I_C} = \infty \tag{6}
$$

Finally, we draw the small signal model:（最后画出小信号模型：）

![](Pasted%20image%2020261114214149.png)
> 图Q1-2 题 1(a) 的小信号模型：$g_m = 0.71$ S，$r_\pi = 141\ \Omega$，$r_o = \infty$

Note that an infinite resistance is equivalent to an open circuit.（注意无穷大电阻等效于开路。）

Thus, here, $r_o$ can be omitted as it is infinite:（因此这里 $r_o$ 可省略：）

![](Pasted%20image%2020261114214203.png)
> 图Q1-3 题 1(a) 的小信号模型（$r_o$ 已开路）：$g_m = 0.71$ S，$r_\pi = 141\ \Omega$

> [!warning] Important: KVL Loops with Ground Nodes（重要：含接地节点的 KVL 回路）
>
> In circuit analysis with ground nodes, KVL loops don't look like visible "circles" anymore!（在含接地节点的电路分析中，KVL 回路不再像可见的“圆圈”！）
>
> The ground node acts as a common reference point that completes the loop implicitly.（接地节点充当公共参考点，隐含地闭合了回路。）
>
> **Example from Part A:**（**A 部分的例子：**）
>
> - The KVL loop goes: $V_{CC} \rightarrow R_C \rightarrow$ Collector $\rightarrow$ Emitter $\rightarrow$ GND $\rightarrow V_{CC}$（KVL 回路为：$V_{CC}\rightarrow R_C\rightarrow$ 集电极 $\rightarrow$ 发射极 $\rightarrow$ GND $\rightarrow V_{CC}$）
> - But we write it as: $V_{CC} - I_C R_C - V_{CE} = 0$, or simply $V_C = V_{CC} - I_C R_C$（但写成：$V_{CC}-I_C R_C-V_{CE}=0$，或简写为 $V_C=V_{CC}-I_C R_C$）
> - The ground connection "closes" the loop even though it's not drawn as a wire（即使未画成导线，接地连接也“闭合”了回路）
>
> **Key insight:** Every voltage source connected to ground has an implicit return path through ground.（**关键点：** 每个接地的电压源都通过地有隐含的回流路径。）
>
> This is why we can write $V_C = V_{CC} - I_C R_C$ without explicitly showing the complete loop — the ground node provides the reference that makes this equation valid.（这就是为什么不必画出完整回路也能写 $V_C=V_{CC}-I_C R_C$——接地节点提供了使该式成立的参考。）

### 1.2 Part B（B 部分）

Determine the operating point and the small-signal model of $Q_1$ for each of the circuits shown below.（求下列各电路中 $Q_1$ 的工作点与小信号模型。）

Assume $I_S = 8 \times 10^{-16}$ A, $V_T = 26$ mV, $\beta = 100$, $V_A = \infty$.（假设 $I_S=8\times10^{-16}$ A、$V_T=26$ mV、$\beta=100$、$V_A=\infty$。）

![](Pasted%20image%2020261114214218.png)
> 图Q1-1（原书在 Part B 处重复排版）题 1(a)(b)(c) 三个电路

*Recall the typical steps for large-signal analysis of a BJT circuit:*（回顾 BJT 电路大信号分析的典型步骤：）

1. Find $I_C$ and $V_{CE}$ using standard circuit analysis techniques (may need Thevenin equivalence).（用标准电路分析方法求 $I_C$ 和 $V_{CE}$（可能需要戴维南等效）。）

   - Use KCL/KVL to write equations for the circuit (typically 2x KVL loop equations).（用 KCL/KVL 列方程（通常为 2 个 KVL 回路方程）。）
   - Use the non-linear $I_C$-$V_{BE}$ relationship to relate $V_{BE}$ to $I_C$ (no Early Effect!).（用非线性 $I_C$–$V_{BE}$ 关系联系 $V_{BE}$ 与 $I_C$（不计厄利效应！）。）
   - If you end up with equation terms of $I_B$, use $I_C = \beta_0 I_B$ to express these in terms of $I_C$.（若方程中出现 $I_B$，用 $I_C=\beta_0I_B$ 化为 $I_C$。）
   - For terms of $I_E$, use $I_E = I_C + I_B = I_C(1 + 1/\beta_0)$ to express in terms of $I_C$.（出现 $I_E$ 时，用 $I_E=I_C+I_B=I_C(1+1/\beta_0)$ 化为 $I_C$。）

2. **Verify the forward active assumption:** Check that $V_{BE,\mathrm{on}} \leq V_{BE} \leq V_{CE}$（**验证放大区假设：** 检查 $V_{BE,\mathrm{on}}\leq V_{BE}\leq V_{CE}$）

3. Record Q-point: $Q = (I_C, V_{CE})$（记录 Q 点：$Q=(I_C,V_{CE})$）

**Note that $V_A = \infty$ in this question, so Early Effect does not apply!**（注意本题 $V_A=\infty$，因此不考虑厄利效应！）

**Large-Signal Analysis**（**大信号分析**）

From the circuit diagram, a current source provides the base current $I_B$ directly.（由电路图可知，电流源直接提供基极电流 $I_B$。）

As in Part A, we can directly determine $I_C$ without KVL, this time using the current gain.（与 A 部分类似，无需 KVL，这次利用电流增益即可直接求出 $I_C$。）

$$
I_B = 10\ \mu\text{A} \tag{7}
$$

Using the known current gain $\beta = 100$, the collector current $I_C$ is determined:（用已知电流增益 $\beta=100$，可得集电极电流 $I_C$：）

$$
I_C = \beta I_B = 100 \cdot (10 \times 10^{-6}\ \text{A}) = 1\ \text{mA} \tag{8}
$$

**Finding $V_{CE}$:** We can use KVL through the collector to determine the collector-emitter voltage $V_{CE}$:（**求 $V_{CE}$：** 对集电极取 KVL 回路，可求集电极-发射极电压 $V_{CE}$：）

$$
V_{CE} = V_{CC} - I_C R_C = 2.5\ \text{V} - (10^{-3}\ \text{A}) \cdot (1000\ \Omega) = 1.5\ \text{V} \tag{9}
$$

Therefore, the Q-point of the BJT is:（因此，BJT 的 Q 点为：）

$$
Q = (I_C, V_{CE}) = (1\ \text{mA}, 1.5\ \text{V}) \tag{10}
$$

Now, we need to find $V_{BE}$ to verify the forward active assumption.（现在需要求 $V_{BE}$ 以验证放大区假设。）

Using the $I_C$-$V_{BE}$ relationship and the known $I_C$, we can determine $V_{BE}$:（利用 $I_C$–$V_{BE}$ 关系及已知 $I_C$，可得 $V_{BE}$：）

$$
V_{BE} = V_T \ln\left(\frac{I_C}{I_S}\right) = (0.026\ \text{V}) \ln\left(\frac{10^{-3}\ \text{A}}{8 \times 10^{-16}\ \text{A}}\right) = 0.724\ \text{V} \quad [V_{BE,\mathrm{on}} \leq V_{BE} \leq V_{CE}\ ✓✓] \tag{11}
$$

**Small-Signal Analysis**（**小信号分析**）

The transconductance is calculated as:（跨导为：）

$$
g_m = \frac{I_C}{V_T} = \frac{10^{-3}\ \text{A}}{0.026\ \text{V}} = 0.0385\ \text{S} \tag{12}
$$

The $\pi$-resistance is:（$\pi$ 型电阻为：）

$$
r_\pi = \frac{\beta}{g_m} = \frac{100}{0.0385\ \text{S}} = 2600\ \Omega \tag{13}
$$

The Early voltage resistance is:（厄利电压对应的电阻为：）

$$
r_o = \frac{V_A}{I_C} = \frac{\infty}{I_C} = \infty \tag{14}
$$

### 1.3 Part C（C 部分）

Determine the operating point and the small-signal model of $Q_1$ for each of the circuits shown below.（求下列各电路中 $Q_1$ 的工作点与小信号模型。）

Assume $I_S = 8 \times 10^{-16}$ A, $V_T = 26$ mV, $\beta = 100$, $V_A = \infty$.（假设 $I_S=8\times10^{-16}$ A、$V_T=26$ mV、$\beta=100$、$V_A=\infty$。）

![](Pasted%20image%2020261114214229.png)
> 图Q1-1（原书在 Part C 处重复排版）题 1(a)(b)(c) 三个电路

*Recall the typical steps for large-signal analysis of a BJT circuit:*（回顾 BJT 电路大信号分析的典型步骤：）

1. Find $I_C$ and $V_{CE}$ using standard circuit analysis techniques (may need Thevenin equivalence).（用标准电路分析方法求 $I_C$ 和 $V_{CE}$（可能需要戴维南等效）。）

   - Use KCL/KVL to write equations for the circuit (typically 2x KVL loop equations).（用 KCL/KVL 列方程（通常为 2 个 KVL 回路方程）。）
   - Use the non-linear $I_C$-$V_{BE}$ relationship to relate $V_{BE}$ to $I_C$ (no Early Effect!).（用非线性 $I_C$–$V_{BE}$ 关系联系 $V_{BE}$ 与 $I_C$（不计厄利效应！）。）
   - If you end up with equation terms of $I_B$, use $I_C = \beta_0 I_B$ to express these in terms of $I_C$.（若方程中出现 $I_B$，用 $I_C=\beta_0I_B$ 化为 $I_C$。）
   - For terms of $I_E$, use $I_E = I_C + I_B = I_C(1 + 1/\beta_0)$ to express in terms of $I_C$.（出现 $I_E$ 时，用 $I_E=I_C+I_B=I_C(1+1/\beta_0)$ 化为 $I_C$。）

2. **Verify the forward active assumption:** Check that $V_{BE,\mathrm{on}} \leq V_{BE} \leq V_{CE}$（**验证放大区假设：** 检查 $V_{BE,\mathrm{on}}\leq V_{BE}\leq V_{CE}$）

3. Record Q-point: $Q = (I_C, V_{CE})$（记录 Q 点：$Q=(I_C,V_{CE})$）

**Note that $V_A = \infty$ in this question, so Early Effect does not apply!**（注意本题 $V_A=\infty$，因此不考虑厄利效应！）

**Large-Signal Analysis**（**大信号分析**）

Unfortunately, for this circuit, we cannot directly determine $I_C$ or $V_{BE}$ from the circuit as we have not been given a convenient voltage/current source this time, so we need to write 2x KVL or KCL equations and use the BJT $I_C$-$V_{BE}$ relationship to solve for $I_C$.（可惜本题没有直接给出方便的电压源或电流源，无法直接从电路读出 $I_C$ 或 $V_{BE}$，因此需要列两个 KVL 或 KCL 方程，并结合 BJT 的 $I_C$–$V_{BE}$ 关系求解 $I_C$。）

The first thing that stands out is the base and collector of the BJT are tied together.（最显眼的是 BJT 的基极与集电极短接在一起。）

This means 3 things:（这带来三点：）

- The voltages at these nodes are equal: $V_B = V_C \Rightarrow V_{BE} = V_{CE}$（两节点电压相等：$V_B=V_C\Rightarrow V_{BE}=V_{CE}$）
- Therefore, the BJT is "self-biased" - the BJT is in the active region as long as $V_{BE} > V_{BE,\mathrm{on}}$.（因此 BJT 处于“自偏置”状态——只要 $V_{BE}>V_{BE,\mathrm{on}}$，就工作在放大区。）
- By KCL, the current flowing through resistor $R_C$ is simply the emitter current $I_E = I_C + I_B$.（由 KCL，流过 $R_C$ 的电流就是发射极电流 $I_E=I_C+I_B$。）

You should know that the emitter current equals the sum of the collector current and the base current:（发射极电流等于集电极电流与基极电流之和：）

$$
I_E = I_C + I_B = I_C\left(1 + \frac{1}{\beta}\right) \tag{15}
$$

Here, we have expressed $I_E$ in terms of $I_C$ using the current gain, $I_B = I_C/\beta$（这里利用电流增益 $I_B=I_C/\beta$ 把 $I_E$ 用 $I_C$ 表示）

Using KVL through the collector resistor $R_C$ (or more simply, Ohm's law), we can write down another expression for $I_E$:（对集电极电阻 $R_C$ 取 KVL（或直接用欧姆定律），可写出 $I_E$ 的另一表达式：）

$$
V_{CC} - I_{R_C}R_C = V_{CE} \quad \Rightarrow \quad I_{R_C} = \frac{V_{CC} - V_{CE}}{R_C} \tag{16}
$$

Note that $I_{R_C} = I_E$, as by KCL at the collector node, $I_{R_C} = I_C + I_B = I_E$, so we now have:（注意 $I_{R_C}=I_E$：由集电极节点的 KCL，$I_{R_C}=I_C+I_B=I_E$，于是有：）

$$
I_E = \frac{V_{CC} - V_{CE}}{R_C} \tag{17}
$$

Combining these two expressions for $I_E$, we get the following:（合并 $I_E$ 的两个表达式，得：）

$$
I_C\left(1 + \frac{1}{\beta}\right) = \frac{V_{CC} - V_{CE}}{R_C} \tag{18}
$$

We still need to express $I_C$ in terms of known quantities.（还需把 $I_C$ 用已知量表示。）

Recall, as mentioned earlier, that since the base and collector are tied together, $V_{BE} = V_{CE}$.（回顾前面所述，基极与集电极短接，故 $V_{BE}=V_{CE}$。）

We can use the BJT $I_C$-$V_{BE}$ relationship to express $V_{CE} = V_{BE}$ in terms of $I_C$:（利用 BJT 的 $I_C$–$V_{BE}$ 关系，把 $V_{CE}=V_{BE}$ 用 $I_C$ 表示：）

$$
I_C\left(1 + \frac{1}{\beta}\right) = \frac{V_{CC} - V_{BE}}{R_C}
$$

$$
V_{BE} = V_T \ln\left(\frac{I_C}{I_S}\right)
$$

$$
I_C = \frac{\beta}{1 + \beta} \cdot \frac{V_{CC} - V_T \ln\left(\frac{I_C}{I_S}\right)}{R_C} \tag{19}
$$

The above implicit equation cannot be solved analytically for $I_C$.（上述隐式方程无法解析求解 $I_C$。）

We can instead use numerical methods, such as the Newton Iteration Method.（可改用数值方法，例如牛顿迭代法。）

#### Newton Iteration Method（牛顿迭代法）

Define the function for iteration:（定义迭代函数：）

$$
\frac{\beta}{1 + \beta} \cdot \frac{V_{CC} - V_T \ln\left(\frac{I_C}{I_S}\right)}{R_C} - I_C = 0 \tag{20}
$$

$$
f(I_C) = \frac{\beta}{1 + \beta} \cdot \frac{V_{CC} - V_T \ln\left(\frac{I_C}{I_S}\right)}{R_C} - I_C \tag{21}
$$

The derivative is（其导数为）

$$
f'(I_C) = -\frac{\beta}{1 + \beta} \cdot \frac{V_T}{R_C \cdot I_C} - 1 \tag{22}
$$

Then the Newton update rule is（牛顿迭代公式为）

$$
I_C^{(n+1)} = I_C^{(n)} - \frac{f\left(I_C^{(n)}\right)}{f'\left(I_C^{(n)}\right)} \tag{23}
$$

Substituting the given values ($\beta = 100$, $V_{CC} = 2.5$ V, $R_C = 1000\ \Omega$, $V_T = 0.026$ V, $I_S = 8 \times 10^{-16}$ A):（代入已知值（$\beta=100$、$V_{CC}=2.5$ V、$R_C=1000\ \Omega$、$V_T=0.026$ V、$I_S=8\times10^{-16}$ A）：）

$$
f(I_C) = \frac{100}{101} \cdot \frac{2.5 - 0.026 \ln\left(\frac{I_C}{8 \times 10^{-16}}\right)}{1000} - I_C \tag{24}
$$

Starting with an initial guess $I_C^{(0)} = 1$ mA:（取初值 $I_C^{(0)}=1$ mA：）

| Iteration（迭代次数） | $I_C^{(n)}$ (mA) | $f\left(I_C^{(n)}\right)$ | $f'\left(I_C^{(n)}\right)$ |
| --- | --- | --- | --- |
| 0 | 1.000 | $7.58 \times 10^{-4}$ | -1.026 |
| 1 | 1.739 | $4.78 \times 10^{-6}$ | -1.015 |
| 2 | 1.744 | $9.43 \times 10^{-11}$ | -1.015 |
| 3 | 1.744 |  |  |

Using this method, the collector current converges to（用该方法，集电极电流收敛于）

$$
I_C \approx 1.74\ \text{mA} \tag{25}
$$

The collector–emitter voltage equals the base–emitter voltage, hence（集电极-发射极电压等于基极-发射极电压，故）

$$
V_{CE} = V_{BE} = V_T \ln\left(\frac{I_C}{I_S}\right) = (0.026\ \text{V}) \ln\left(\frac{1.74 \times 10^{-3}\ \text{A}}{8 \times 10^{-16}\ \text{A}}\right) = 0.739\ \text{V} \quad [V_{BE,\mathrm{on}} \leq V_{BE} \leq V_{CE},\ \text{self-biased}\ ✓✓] \tag{26}
$$

Thus, the Q-point is（因此，Q 点为）

$$
Q = (I_C, V_{CE}) = (1.74\ \text{mA}, 0.739\ \text{V}) \tag{27}
$$

#### Small-Signal Parameters（小信号参数）

The transconductance is（跨导为）

$$
g_m = \frac{I_C}{V_T} = \frac{1.74 \times 10^{-3}\ \text{A}}{0.026\ \text{V}} = 66.92\ \text{mS} \tag{28}
$$

The $\pi$-resistance is（$\pi$ 型电阻为）

$$
r_\pi = \frac{\beta}{g_m} = \frac{100}{0.06692\ \text{S}} \approx 1494\ \Omega \tag{29}
$$

Since $V_A = \infty$, the early-effect resistance is（由于 $V_A=\infty$，厄利效应电阻为）

$$
r_o = \infty \tag{30}
$$

> [!tip] Simpler Iteration Method (Gauss-Seidel Method)（更简单的迭代法（高斯-赛德尔法））
>
> For BJT circuits where the transistor is on, there's a simpler iteration method that often converges without derivatives!（对于晶体管导通的 BJT 电路，有一种更简单的迭代法，通常无需导数即可收敛！）
>
> **The Method:** Rearrange the equation to isolate $I_C$ on the left side:（**方法：** 把方程变形，将 $I_C$ 孤立在左边：）
>
> $$
> I_C = \frac{\beta}{1 + \beta} \cdot \frac{V_{CC} - V_T \ln(I_C/I_S)}{R_C}
> $$
>
> Then iteratively compute:（然后迭代计算：）
>
> $$
> I_C^{(n+1)} = \frac{\beta}{1 + \beta} \cdot \frac{V_{CC} - V_T \ln\left(I_C^{(n)}/I_S\right)}{R_C}
> $$
>
> **Calculator Technique:**（**计算器操作：**）
>
> 1. Enter initial guess: 1E-3 (for 1 mA)（输入初值 1E-3（即 1 mA））
> 2. Type the formula using ANS for $I_C^{(n)}$:（用 ANS 代表 $I_C^{(n)}$ 输入公式：）
>
>    `(100/101)*(2.5-0.026*ln(ANS/8E-16))/1000`
>
> 3. Press `=` repeatedly until the value converges（反复按 `=` 直到数值收敛）
>
> **Example for Part C:**（**C 部分的例子：**）
>
> | Press =（按 = 次数） | Display (mA)（显示值，mA） |
> | --- | --- |
> | Initial（初值） | 1.000 |
> | 1st（第 1 次） | 1.758 |
> | 2nd（第 2 次） | 1.744 |
> | 3rd（第 3 次） | 1.744 |
>
> **Warning:** This method may not converge if the initial guess is too far from the solution or if the BJT is near cutoff.（**注意：** 若初值离解太远，或 BJT 接近截止，该方法可能不收敛。）

## 2 Question 2（第 2 题）

(a) Find the Q-point for the circuit in Fig. a.（求图 a 电路的 Q 点。）

Assume that $\beta_F = 50$ and $V_{BE} = 0.7$ V.（假设 $\beta_F=50$、$V_{BE}=0.7$ V。）

(b) Repeat the calculation if all the resistor values are decreased by a factor of 5.（若所有电阻值都减小为 1/5，重做计算。）

(c) Repeat if all the resistor values are increased by a factor of 5.（若所有电阻值都增大为 5 倍，重做计算。）

(d) Find the Q-point in part (a) using the numerical iteration method if $I_S = 0.5$ fA and $V_T = 25.8$ mV.（若 $I_S=0.5$ fA、$V_T=25.8$ mV，用数值迭代法求 (a) 中的 Q 点。）

(e) Repeat for $V_A = 60$ V.（对 $V_A=60$ V 重做。）

![](Pasted%20image%2020261114214300.png)
> 图Q2-1 题 2(a) 的四电阻偏置电路（"+10 V"接 $68$ k$\Omega$／$43$ k$\Omega$，基极接 $68$ k$\Omega$ 与 $36$ k$\Omega$ 分压中点，发射极接 $33$ k$\Omega$ 到地）

**Solution:**（**解答：**）

This circuit is a "8"-shaped **4-Resistor Bias Network** BJT circuit.（该电路是“8”字形的**四电阻偏置网络** BJT 电路。）

This is a well known configuration, featured in the lecture.（这是课上介绍过的经典结构。）

You should memorise this, or draw it on your formula sheet!（应当记住它，或画在公式表上！）

We must simplify the left-hand-side part of the circuit using Thevenin equivalence (see lecture).（需用戴维南等效化简电路左侧部分（见课件）。）

The equivalent voltage source can be determined by finding the open-circuit voltage at the base node:（等效电压源可由基极节点的开路电压求出：）

$$
V_{eq} = 10 \cdot \left(\frac{36\ \text{k}\Omega}{36\ \text{k}\Omega + 68\ \text{k}\Omega}\right) = 3.46\ \text{V} \tag{1}
$$

The equivalent resistance can be determined by:（等效电阻为：）

$$
R_{eq} = 36\ \text{k}\Omega \parallel 68\ \text{k}\Omega = 23.54\ \text{k}\Omega \tag{2}
$$

![](Pasted%20image%2020261114214312.png)
> 图3 Q2.Thevenin equivalent circuit（图 3：第 2 题的戴维南等效电路）

### 2.1 Part A（A 部分）

Applying KVL in the base loop, we get the following equation.（在基极回路中应用 KVL，得：）

$$
V_{eq} - I_B R_{eq} - V_{BE} - I_E \cdot 33\,000 = 0 \tag{3}
$$

The correlation between the emitter current and the base current is given by:（发射极电流与基极电流的关系为：）

$$
I_E = (1 + \beta_F)I_B \tag{4}
$$

Substituting (2) into (1), we get the following equation, where $V_{BE} = 0.7$V, given by the question.（把 (4) 代入 (3)，并取题目给出的 $V_{BE}=0.7$ V，得：）

$$
V_{eq} - I_B R_{eq} - V_{BE} - (1 + \beta_F)I_B \times 33\,000 = 0 \tag{5}
$$

Rearranging the equation, we can solve the base current.（重排方程即可解出基极电流。）

$$
I_B = \frac{V_{eq} - V_{BE}}{R_{eq} + (1 + \beta_F) \times 33\,000} I_B = 1.62\ \mu\text{A} \tag{6}
$$

The collector current and the emitter current are then determined using the current gain $\beta_F = 50$.（再用电流增益 $\beta_F=50$ 求集电极电流与发射极电流。）

$$
I_C = \beta_F I_B = 50 \times 1.62\ \mu\text{A} = 80.87\ \mu\text{A} \tag{7}
$$

$$
I_E = (1 + \beta_F)I_B = 51 \times 1.62\ \mu\text{A} = 82.48\ \mu\text{A} \tag{8}
$$

According to Ohm's Law and basic KVL, we can get the expressions for the collector voltage and emitter voltage, where The collector–emitter voltage:（由欧姆定律与基本 KVL，可得集电极电压与发射极电压表达式，进而求集电极-发射极电压：）

$$
V_C = V_{CC} - I_C \cdot 43\,000 \tag{9}
$$

$$
V_E = I_E \cdot 33\,000 \tag{10}
$$

Thus we can get the voltage drop between the collector and the emitter.（于是得到集电极与发射极之间的压降。）

$$
V_{CE} = V_C - V_E = [V_{CC} - (43\,000 \cdot I_C)] - (33\,000 \cdot I_E) = 3.8\ \text{V} \tag{11}
$$

Therefore, the operating point (Q-point) is:（因此，工作点（Q 点）为：）

$$
Q : (I_C, V_{CE}) = (80.87\ \mu\text{A}, 3.8\ \text{V}) \tag{12}
$$

### 2.2 Part B（B 部分）

From the voltage divider, the Thevenin equivalent voltage is given as:（由分压关系，戴维南等效电压为：）

$$
V_{eq} = 3.46\ \text{V} \tag{13}
$$

The Thevenin resistance is the parallel combination of 7.2 k$\Omega$ and 13.6 k$\Omega$:（戴维南电阻为 7.2 k$\Omega$ 与 13.6 k$\Omega$ 的并联：）

$$
R_{eq} = 7.2\ \text{k}\Omega \parallel 13.6\ \text{k}\Omega = 4.71\ \text{k}\Omega \tag{14}
$$

The base current can be expressed as:（基极电流可表示为：）

$$
I_B = \frac{V_{eq} - V_{BE}}{R_{eq} + (1 + \beta_F) \cdot 3300} \tag{15}
$$

Substituting the given values ($V_{BE} = 0.7$ V, $\beta_F = 50$), we obtain:（代入已知值（$V_{BE}=0.7$ V、$\beta_F=50$），得：）

$$
I_B = \frac{3.46 - 0.7}{4710 + 51 \times 330} = 8.10\ \mu\text{A} \tag{16}
$$

The collector current and emitter current are then calculated:（于是可算集电极电流与发射极电流：）

$$
I_C = \beta_F I_B = 50 \times 8.10\ \mu\text{A} = 404.6\ \mu\text{A} \tag{17}
$$

$$
I_E = (1 + \beta_F)I_B = 51 \times 8.10\ \mu\text{A} = 412.7\ \mu\text{A} \tag{18}
$$

Next, we determine the collector–emitter voltage:（接着求集电极-发射极电压：）

$$
V_{CE} = [10 - (8.6\ \text{k}\Omega \cdot I_C)] - (6.6\ \text{k}\Omega \cdot I_E) = 3.8\ \text{V} \tag{19}
$$

Therefore, the operating point (Q-point) is:（因此，工作点（Q 点）为：）

$$
Q : (I_C, V_{CE}) = (405\ \mu\text{A}, 3.8\ \text{V}) \tag{20}
$$

### 2.3 Part C（C 部分）

From the voltage divider, the Thevenin equivalent voltage is the same as before:（由分压关系，戴维南等效电压与前面相同：）

$$
V_{eq} = 3.46\ \text{V} \tag{21}
$$

The Thevenin resistance is the parallel combination of 180 k$\Omega$ and 340 k$\Omega$:（戴维南电阻为 180 k$\Omega$ 与 340 k$\Omega$ 的并联：）

$$
R_{eq} = 180\ \text{k}\Omega \parallel 340\ \text{k}\Omega = 117.7\ \text{k}\Omega \tag{22}
$$

The base current is then:（基极电流为：）

$$
I_B = \frac{V_{eq} - V_{BE}}{R_{eq} + (1 + \beta_F) \cdot 3300 \cdot 5} \tag{23}
$$

Substituting the given values ($V_{BE} = 0.7$ V, $\beta_F = 50$), we obtain:（代入已知值（$V_{BE}=0.7$ V、$\beta_F=50$），得：）

$$
I_B = \frac{3.46 - 0.7}{117700 + 51 \times 16500} = 0.32\ \mu\text{A} \tag{24}
$$

The collector current and emitter current are then determined:（于是求集电极电流与发射极电流：）

$$
I_C = \beta_F I_B = 50 \times 0.32\ \mu\text{A} = 16.2\ \mu\text{A} \tag{25}
$$

$$
I_E = (1 + \beta_F)I_B = 51 \times 0.32\ \mu\text{A} = 16.5\ \mu\text{A} \tag{26}
$$

The collector–emitter voltage is:（集电极-发射极电压为：）

$$
V_{CE} = 3.8\ \text{V} \tag{27}
$$

Therefore, the operating point (Q-point) is:（因此，工作点（Q 点）为：）

$$
Q : (I_C, V_{CE}) = (16.2\ \mu\text{A}, 3.8\ \text{V}) \tag{28}
$$

### 2.4 Part D（D 部分）

The base–emitter voltage is modeled using the following equation:（基极-发射极电压用下式建模：）

$$
V_{BE} = V_T \cdot \ln\left(\frac{I_C}{I_S} + 1\right) = 0.0258 \cdot \ln\left(2 \times 10^{15} I_C + 1\right) \tag{29}
$$

The collector current can also be expressed using the KVL method:（集电极电流也可由 KVL 方法表示：）

$$
I_C = \frac{V_{eq} - V_{BE}}{R_{eq} + (1 + \beta_F)R_E} \cdot \beta_F \tag{30}
$$

Substituting the known values, we can get the expression of $V_{BE}$ as a function of $I_C$:（代入已知值，可得 $V_{BE}$ 关于 $I_C$ 的表达式：）

$$
I_C = \frac{3.46 - V_{BE}}{170.654\ \text{k}\Omega} \cdot 50 = \frac{3.46 - V_{BE}}{34130} \tag{31}
$$

$$
V_{BE} = 3.46 - 34130 I_C \tag{32}
$$

To solve the non-linear equations (29) and (32), we construct the following function.（为求解非线性方程 (29) 与 (32)，构造如下函数。）

We want to find the optimal value of $I_C$ to make $f(I_C) = 0$（求使 $f(I_C)=0$ 的 $I_C$）

$$
f(I_C) = V_{BE@(eq.29)} - V_{BE@(eq.32)} = 34130 I_C + 0.0258 \ln\left(2 \times 10^{15} I_C + 1\right) - 3.46 \tag{33}
$$

The derivative of the function is:（该函数的导数为：）

$$
f'(I_C) = 34130 + \frac{0.0258 \cdot 2 \times 10^{15}}{2 \times 10^{15} I_C + 1} \tag{34}
$$

Using the Newton's iteration method:（用牛顿迭代法：）

$$
I_{C,\text{new}} = I_{C,\text{old}} - \frac{f(I_{C,\text{old}})}{f'(I_{C,\text{old}})} \tag{35}
$$

After iteration, the solution converges to:（迭代后收敛于：）

$$
I_C = 81.8\ \mu\text{A}, \quad V_{CE} = 3.79\ \text{V} \tag{36}
$$

Therefore, the operating point (Q-point) is:（因此，工作点（Q 点）为：）

$$
Q : (I_C, V_{CE}) = (81.8\ \mu\text{A}, 3.79\ \text{V}) \tag{37}
$$

### 2.5 Part E（E 部分）

Including the Early effect, the forward current gain is expressed as:（计入厄利效应后，正向电流增益为：）

$$
\beta_F = \beta_{F0}\left(1 + \frac{V_{CE}}{V_A}\right) = 50 \cdot \left(1 + \frac{V_{CE}}{60}\right) \tag{38}
$$

The collector–emitter voltage drop can be written below using KVL.（用 KVL 可写出集电极-发射极压降。）

$$
V_{CE} = (V_{CC} - I_C R_C) - I_E R_E \tag{39}
$$

Since $I_C = \beta_F I_B$ and $I_E = (1 + \beta_F)I_B$, we can rewrite the equation (38) to be:（由于 $I_C=\beta_FI_B$、$I_E=(1+\beta_F)I_B$，可把式 (40) 改写为：）

$$
V_{CE} = V_{CC} - \left[I_B \cdot \beta_F\right]R_C - \left[I_B \cdot (\beta_F + 1)\right]R_E \tag{40}
$$

Meanwhile, the base loop KVL gives:（同时，基极回路的 KVL 给出：）

$$
V_{eq} - R_{eq}I_B - V_{BE} - \left[I_B \cdot (\beta_F + 1)\right]R_E = 0 \tag{41}
$$

Equations (39) and (40) are solved simultaneously.（联立求解式 (39) 与 (40)。）

The numerical results are:（数值结果为：）

$$
V_{CE} = 3.44\ \text{V}, \quad I_B = 0.81\ \mu\text{A}, \quad I_C = 85.5\ \mu\text{A} \tag{42}
$$

Therefore, the operating point (Q-point) is:（因此，工作点（Q 点）为：）

$$
Q : (I_C, V_{CE}) = (85.5\ \mu\text{A}, 3.44\ \text{V}) \tag{43}
$$

## 3 Question 3（第 3 题）

An npn transistor is operating in the forward-active region with a base current of 3 $\mu$A.（一个 npn 晶体管工作在放大区，基极电流为 3 $\mu$A。）

It is found that $I_C = 240$ $\mu$A for $V_{CE} = 5$ V and $I_C = 265$ $\mu$A for $V_{CE} = 10$ V.（测得 $V_{CE}=5$ V 时 $I_C=240$ $\mu$A，$V_{CE}=10$ V 时 $I_C=265$ $\mu$A。）

What are the values of $\beta_{F0}$ and $V_A$ for this transistor?（求该晶体管的 $\beta_{F0}$ 与 $V_A$。）

**Solution:**（**解答：**）

We define the following parameters:（定义以下参数：）

$$
I_B = \text{Base current} = 3\ \mu\text{A} = 3 \times 10^{-6}\ \text{A} \tag{1}
$$

$$
\beta_F = \text{Forward common-emitter current gain} \tag{2}
$$

$$
\beta_{F0} = \text{Forward common-emitter current gain at } V_{CE} = 0 \tag{3}
$$

$$
V_A = \text{Early voltage} \tag{4}
$$

$$
V_{CE} = \text{Collector--emitter voltage} \tag{5}
$$

$$
I_C = \text{Collector current} \tag{6}
$$

We have the equation that describes how $V_{CE}$ affects $I_C$（描述 $V_{CE}$ 如何影响 $I_C$ 的方程为）

$$
I_C = \beta_F I_B = \left[\beta_{F0}\left(1 + \frac{V_{CE}}{V_A}\right)\right]I_B \tag{7}
$$

Taking the two sets of values of $V_{CE}$ and $I_C$ into (5), we can get the equation set.（把两组 $V_{CE}$、$I_C$ 值代入 (7)，得方程组。）

$$
240\ \mu\text{A} = \beta_{F0}\left(1 + \frac{5}{V_A}\right)(3\ \mu\text{A}) \tag{8}
$$

$$
265\ \mu\text{A} = \beta_{F0}\left(1 + \frac{10}{V_A}\right)(3\ \mu\text{A}) \tag{9}
$$

Solving (6) and (7), we get（解 (8)、(9)，得）

$$
\beta_{F0} = 71.7, \quad V_A = 43\ \text{V}. \tag{10}
$$

## 转换说明（非原文内容）

- 本文由 PDF 文本层与页面渲染图逐页核对后转录；公式一律改写为 LaTeX，`\tag` 沿用原文的式号（原文在第 1、2、3 题内各自从 (1) 重新编号）。
- 所有插图（含手绘的等效电路、小信号模型、器件符号）一律以纯文本占位表示，未插入图像本体；原书有编号的图写作 `> 图1 …`，原书未编号的插图写作 `> 图Q1-1 …` 这样的题号式编号。
- 提示框（Key Insight / Important / Critical Assumption / Simpler Iteration Method 等）改用 Obsidian callout 呈现：Critical Assumption 与 Important 用 `[!warning]`，Simpler Iteration Method 用 `[!tip]`，框内保留原有粗体小标题。
- 原文个别笔误照录未改：第 2 题 (6) 式末尾多写了一个 `I_B =`；第 2 题 (5) 式处写“Substituting (2) into (1)”，按上下文应为 (4) 代入 (3)；第 3 题写“Taking the two sets of values … into (5)”“Solving (6) and (7)”，按上下文应为 (7)/(8)(9)。
- 原书页眉统一为“ELEC2104/9704 Tutorial 7 Solutions (2025)”，只在文首保留一次。
