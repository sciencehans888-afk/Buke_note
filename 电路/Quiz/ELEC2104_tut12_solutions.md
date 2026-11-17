# ELEC2104/9704 Tutorial 12 Solutions (2025)（ELEC2104/9704 第 12 次辅导课解答（2025））

## Introduction to Transfer Functions and Bode Plots（传递函数与 Bode 图简介）

In this tutorial, we introduce powerful frequency-domain analysis techniques that are essential for understanding how circuits respond to signals at different frequencies.
（本次辅导课介绍频域分析这一强有力的方法，它是理解电路如何响应不同频率信号的基础。）

These tools are fundamental in filter design, signal processing, control systems, and amplifier analysis.
（这些工具是滤波器设计、信号处理、控制系统与放大器分析的基础。）

---

### 1. What is a Transfer Function?（什么是传递函数？）

A transfer function is a mathematical representation that describes how a circuit transforms an input signal into an output signal.
（传递函数是一种数学表示，描述电路如何把输入信号变换为输出信号。）

For a linear circuit, the transfer function $T(s)$ is defined as:
（对线性电路，传递函数 $T(s)$ 定义为：）

$$
T(s) = \frac{V_o(s)}{V_i(s)} \tag{1}
$$

where $V_o(s)$ is the output voltage and $V_i(s)$ is the input voltage, both expressed in the complex frequency domain.
（其中 $V_o(s)$ 为输出电压，$V_i(s)$ 为输入电压，两者都在复频域中表示。）

**符号说明**：
- $T(s)$：传递函数，输出与输入之比
- $s$：复频率变量（拉普拉斯变量）
- $V_i(s)$、$V_o(s)$：输入、输出电压的 s 域表示

![](Pasted%20image%2020261117154618.png)
> 图1 Block diagram representation of a transfer function：$V_i(s)$ 经标注 $T(s)$ 的 Linear Circuit 得到 $V_o(s)$

Transfer functions are ubiquitous in engineering because they provide a complete characterization of a circuit's behavior across all frequencies.
（传递函数在工程中无处不在，因为它能完整刻画电路在所有频率下的行为。）

Once you know the transfer function, you can predict the output for any input signal—whether it's a pure sinusoid, a complex audio waveform, or a digital communication signal.
（一旦知道传递函数，就能预测任意输入信号下的输出——无论是纯正弦波、复杂的音频波形，还是数字通信信号。）

**Why are transfer functions so powerful?**（传递函数为何如此强大？）

- **Frequency-selective behavior:** Different circuits amplify or attenuate different frequency components (e.g. low-pass filter).
  （**频率选择特性：** 不同电路对不同频率分量进行放大或衰减（例如低通滤波器）。）
- **Filter design:** Whether you're designing a bass boost circuit, noise filter, or radio tuner, the transfer function tells you how to choose component values.
  （**滤波器设计：** 无论是设计低音增强电路、噪声滤波器还是收音机调谐器，传递函数都能告诉你如何选取元件参数。）
- **System analysis:** From audio equalizers to signal processing in medical devices, transfer functions provide insight into how signals are transformed.
  （**系统分析：** 从音频均衡器到医疗设备中的信号处理，传递函数都能揭示信号是如何被变换的。）
- **Predictive power:** Given any input $V_i(s)$, you can immediately compute the output as $V_o(s) = T(s) \cdot V_i(s)$ - no differential equations needed!
  （**预测能力：** 给定任意输入 $V_i(s)$，可立即算出输出 $V_o(s) = T(s) \cdot V_i(s)$——不需要列微分方程！）

---

### 2. The s-Domain and Why It's Useful（s 域及其用处）

The s-domain (or Laplace domain) is a mathematical framework where the complex variable $s$ represents complex frequency.
（s 域（或称拉普拉斯域）是一种数学框架，其中复变量 $s$ 表示复频率。）

We write:
（写作：）

$$
s = \sigma + j\omega \tag{2}
$$

where $\sigma$ represents exponential growth or decay, and $\omega$ represents angular frequency in radians per second.
（其中 $\sigma$ 表示指数增长或衰减，$\omega$ 表示角频率，单位为弧度每秒。）

**Why is the s-domain useful?**（s 域为何有用？）

- **Simplifies differential equations:** Time-domain differential equations become algebraic equations in the s-domain, making circuit analysis much easier.
  （**简化微分方程：** 时域微分方程在 s 域中变为代数方程，使电路分析容易得多。）
- **Handles complex impedances elegantly:** Capacitor impedance becomes $Z_C = 1/(sC)$ and inductor impedance becomes $Z_L = sL$.
  （**优雅地处理复阻抗：** 电容阻抗变为 $Z_C = 1/(sC)$，电感阻抗变为 $Z_L = sL$。）
- **Unified framework:** The s-domain handles transient responses, steady-state responses, and stability analysis all within one framework.
  （**统一框架：** s 域可在同一框架内处理瞬态响应、稳态响应与稳定性分析。）

For frequency analysis (also called steady-state sinusoidal analysis), we set $s = j\omega$, which means we're only looking at the purely oscillatory behavior without exponential growth or decay.
（做频率分析（也称稳态正弦分析）时，令 $s = j\omega$，即只考察纯粹的振荡行为，不含指数增长或衰减。）

This is what we focus on in this tutorial—analyzing how circuits respond to different frequencies.
（这正是本次辅导课的重点——分析电路如何响应不同频率。）

![](Pasted%20image%2020261117154635.png)
> 图2 The s-plane: for steady-state sinusoidal analysis, we evaluate $T(s)$ along the imaginary axis（复平面：虚轴 $j\omega$、$-j\omega_1$，实轴 $\sigma$，标注 $s = j\omega$ (steady-state)）

---

### 3. Poles, Zeros, and Low-Frequency Gain（极点、零点与低频增益）

Transfer functions can be written as ratios of polynomials:
（传递函数可写成多项式之比：）

$$
T(s) = A \cdot \frac{(s - z_1)(s - z_2) \cdots}{(s - p_1)(s - p_2) \cdots} \tag{3}
$$

- **Zeros** ($z_1, z_2, \ldots$): Values of $s$ that make the numerator zero, causing $T(s) = 0$.
  （**零点**（$z_1, z_2, \ldots$）：使分子为零、从而 $T(s) = 0$ 的 $s$ 值。）
- **Poles** ($p_1, p_2, \ldots$): Values of $s$ that make the denominator zero, causing $T(s) \to \infty$.
  （**极点**（$p_1, p_2, \ldots$）：使分母为零、从而 $T(s) \to \infty$ 的 $s$ 值。）
- **Low-frequency gain** ($A$): The gain of the transfer function as $\omega \to 0$ (or sometimes normalized to 1).
  （**低频增益**（$A$）：当 $\omega \to 0$ 时传递函数的增益（有时归一化为 1）。）

Poles and zeros are crucial because they determine the frequency response shape.
（极点与零点至关重要，因为它们决定了频率响应的形状。）

We'll see later in this tutorial how poles and zeros affect the slopes and features of Bode plots.
（本次辅导课后面会看到极点、零点如何影响 Bode 图的斜率与特征。）

**Try it yourself:** Consider the transfer function from our low-pass filter example:
（**自己试一试：** 考虑低通滤波器示例中的传递函数：）

$$
T(s) = \frac{1}{1 + \frac{s}{10,000}}
$$

What value of $s$ makes the denominator equal to zero?
（$s$ 取何值时分母为零？）

Substitute that value and see what happens to $T(s)$.
（把该值代入，观察 $T(s)$ 会发生什么。）

This is a pole! In this case, setting $1 + s/10,000 = 0$ gives $s = -10,000$, which makes $T(s) \to \infty$.
（这就是一个极点！此处令 $1 + s/10,000 = 0$ 得 $s = -10,000$，此时 $T(s) \to \infty$。）

This pole location at $s = -10,000$ (on the negative real axis) determines the circuit's cutoff frequency and time response characteristics.
（该极点位于 $s = -10,000$（负实轴上），决定了电路的截止频率与时间响应特性。）

![](Pasted%20image%2020261117154649.png)
> 图3 Poles (×) and zeros (◦) determine the transfer function behavior.（Pole-Zero Plot in s-plane：纵轴 Im(s)，横轴 Re(s)，两个 pole 标 ×，一个 zero 标 ◦）

---

### 4. Standard Bode Format（标准 Bode 形式）

The standard Bode format expresses the transfer function in a normalized form that makes it easy to identify key frequencies and gain.
（标准 Bode 形式把传递函数写成归一化形式，便于直接识别关键频率与增益。）

For a first-order low-pass filter, the standard form is:
（对一阶低通滤波器，标准形式为：）

$$
T(s) = \frac{A}{1 + \frac{s}{\omega_c}} \tag{4}
$$

where $A$ is the DC gain and $\omega_c$ is the cut-off angular frequency (also called the corner frequency or pole frequency).
（其中 $A$ 为直流增益，$\omega_c$ 为截止角频率（也称转折频率或极点频率）。）

For a first-order high-pass filter:
（对一阶高通滤波器：）

$$
T(s) = A \cdot \frac{\frac{s}{\omega_c}}{1 + \frac{s}{\omega_c}} \tag{5}
$$

Note that this can also be written as:
（注意它也可写成：）

$$
T(s) = A \cdot \frac{s}{s + \omega_c} \tag{6}
$$

Both forms are equivalent!
（两种形式等价！）

The first emphasizes the standard Bode format, while the second is more compact.
（前者突出标准 Bode 形式，后者更简洁。）

**Alternative Bode format - Inverted form:**（另一种 Bode 形式——倒置形式：）

You'll also see the transfer function written with $s$ in the denominator instead of the numerator:
（你还会看到把 $s$ 写在分母而不是分子中的传递函数写法：）

$$
T(s) = A \cdot \frac{1}{1 + \frac{\omega_c}{s}} \tag{7}
$$

This is called the inverted Bode form.
（这称为倒置 Bode 形式。）

Let's see how to convert between the two formats:
（下面看两种形式之间如何互换：）

**Converting from standard to inverted form:**（从标准形式化为倒置形式：）

Starting with the standard high-pass form: $T(s) = A \cdot \dfrac{s/\omega_c}{1 + s/\omega_c}$
（从标准高通形式出发：$T(s) = A \cdot \dfrac{s/\omega_c}{1 + s/\omega_c}$）

Multiply numerator and denominator by $\omega_c/s$:
（分子分母同乘 $\omega_c/s$：）

$$
T(s) = A \cdot \frac{\frac{s}{\omega_c} \cdot \frac{\omega_c}{s}}{\left(1 + \frac{s}{\omega_c}\right) \cdot \frac{\omega_c}{s}} = A \cdot \frac{1}{\frac{\omega_c}{s} + 1} = \frac{A}{1 + \frac{\omega_c}{s}} \tag{8}
$$

So both formats describe the same high-pass filter!
（可见两种形式描述的是同一个高通滤波器！）

The standard form $1 + s/\omega_c$ and inverted form $1 + \omega_c/s$ are just different ways of writing the same thing.
（标准形式 $1 + s/\omega_c$ 与倒置形式 $1 + \omega_c/s$ 只是同一表达的不同写法。）

**When to use each format:**（何时使用哪种形式：）

- Standard form $1 + s/\omega_c$: Emphasizes the pole/zero frequency directly
  （标准形式 $1 + s/\omega_c$：直接突出极点/零点频率）
- Inverted form $1 + \omega_c/s$: Useful for certain algebraic manipulations
  （倒置形式 $1 + \omega_c/s$：便于某些代数变形）

Both forms are used in this course, so it's important to recognize them and be able to convert between them.
（本课程两种形式都会用到，因此要能识别并相互转换。）

You'll see examples of each in the problems below!
（下面的题目中两种形式都会出现！）

**More complex example with multiple poles and zeros:**（含多个极点、零点的更复杂示例：）

For a transfer function with a zero at $\omega_z$, a pole at $\omega_{p1}$, and another pole at $\omega_{p2}$, the standard Bode format is:
（若传递函数在 $\omega_z$ 处有一个零点、在 $\omega_{p1}$ 与 $\omega_{p2}$ 处各有一个极点，则标准 Bode 形式为：）

$$
T(s) = A \cdot \frac{1 + \frac{s}{\omega_z}}{\left(1 + \frac{s}{\omega_{p1}}\right)\left(1 + \frac{s}{\omega_{p2}}\right)} \tag{9}
$$

where:
（其中：）

- $A$ is the low-frequency gain (DC gain)
  （$A$ 为低频增益（直流增益））
- $\omega_z$ is the zero frequency (causes +20 dB/decade slope)
  （$\omega_z$ 为零点频率（产生 +20 dB/十倍频的斜率））
- $\omega_{p1}$ and $\omega_{p2}$ are the pole frequencies (each causes $-20$ dB/decade slope)
  （$\omega_{p1}$、$\omega_{p2}$ 为极点频率（各产生 $-20$ dB/十倍频的斜率））

The advantage of this format is that you can directly read all the critical frequencies from the expression without additional calculation.
（这种形式的优点是无需额外计算，就能从表达式中直接读出所有关键频率。）

**Example: Simple RC Low-Pass Filter**（示例：简单 RC 低通滤波器）

![](Pasted%20image%2020261117154705.png)
> 图4 First-order RC low-pass filter with $T(s) = 1/(1+sRC)$：$R$ 串联于 $V_i(s)$ 与 $V_o(s)$ 之间，$C$ 由 $V_o(s)$ 端接地

---

### 5. Deriving Transfer Functions: The Power of s-Domain Analysis（推导传递函数：s 域分析的威力）

Now we'll see why the s-domain is so powerful by deriving the transfer functions for RC filters.
（下面通过推导 RC 滤波器的传递函数，来看 s 域为何如此强大。）

The key insight is that capacitors and inductors behave just like resistors in the s-domain, allowing us to use familiar circuit analysis techniques like the voltage divider formula!
（关键之处在于：在 s 域中电容和电感的行为与电阻类似，因此可以使用分压公式等熟悉的电路分析方法！）

**RC Low-Pass Filter Derivation**（RC 低通滤波器的推导）

Consider the RC low-pass filter shown above.
（考虑上面所示的 RC 低通滤波器。）

In the s-domain:
（在 s 域中：）

- Resistor impedance: $Z_R = R$
  （电阻阻抗：$Z_R = R$）
- Capacitor impedance: $Z_C = \dfrac{1}{sC}$
  （电容阻抗：$Z_C = \dfrac{1}{sC}$）

Notice how the capacitor has an impedance just like a resistor—it's frequency-dependent, but mathematically it's just another impedance!
（注意电容也像电阻一样具有阻抗——它随频率变化，但在数学上就是另一个阻抗！）

This is the magic of the s-domain.
（这正是 s 域的奇妙之处。）

**Using the voltage divider formula:**（使用分压公式：）

Since the resistor and capacitor form a voltage divider, we can immediately write:
（由于电阻与电容构成分压器，可直接写出：）

$$
T(s) = \frac{V_o(s)}{V_i(s)} = \frac{Z_C}{Z_R + Z_C} \tag{10}
$$

This is exactly the same formula you'd use for two resistors in series!
（这与两个电阻串联时所用的公式完全相同！）

Substituting the impedances:
（代入各阻抗：）

$$
T(s) = \frac{\frac{1}{sC}}{R + \frac{1}{sC}} \tag{11}
$$

To simplify, multiply numerator and denominator by $sC$:
（为化简，分子分母同乘 $sC$：）

$$
T(s) = \frac{1}{sRC + 1} = \frac{1}{1 + sRC} \tag{12}
$$

Now, let's define the cutoff angular frequency as:
（现在定义截止角频率为：）

$$
\omega_c = \frac{1}{RC} \tag{13}
$$

Writing $s = \dfrac{s}{\omega_c} \cdot \omega_c$ and factoring:
（把 $s$ 写成 $\dfrac{s}{\omega_c} \cdot \omega_c$ 并整理：）

$$
T(s) = \frac{1}{1 + s \cdot RC} = \frac{1}{1 + s/\omega_c} \tag{14}
$$

This is the standard Bode form for a first-order low-pass filter!
（这就是一阶低通滤波器的标准 Bode 形式！）

You can directly read the cutoff frequency $\omega_c = 1/RC$ from the denominator.
（可直接从分母读出截止频率 $\omega_c = 1/RC$。）

**RC High-Pass Filter Derivation**（RC 高通滤波器的推导）

Now consider swapping the resistor and capacitor positions:
（现在考虑把电阻与电容的位置互换：）

![](Pasted%20image%2020261117154720.png)
> 图5 First-order RC high-pass filter：$C$ 串联于 $V_i(s)$ 与 $V_o(s)$ 之间，$R$ 由 $V_o(s)$ 端接地

Using the voltage divider formula again:
（再次使用分压公式：）

$$
T(s) = \frac{V_o(s)}{V_i(s)} = \frac{Z_R}{Z_C + Z_R} = \frac{R}{\frac{1}{sC} + R} \tag{15}
$$

Multiply numerator and denominator by $sC$:
（分子分母同乘 $sC$：）

$$
T(s) = \frac{sRC}{1 + sRC} \tag{16}
$$

Using the same cutoff frequency $\omega_c = 1/RC$:
（利用相同的截止频率 $\omega_c = 1/RC$：）

$$
T(s) = \frac{s/\omega_c}{1 + s/\omega_c} \tag{17}
$$

This is the standard Bode form for a first-order high-pass filter!
（这就是一阶高通滤波器的标准 Bode 形式！）

Notice the numerator has an $s$ term, indicating this filter passes high frequencies.
（注意分子中含 $s$ 项，说明该滤波器通过高频。）

---

### Understanding the Magnitude Response: Why -3 dB?（理解幅频响应：为什么是 -3 dB？）

Now let's understand what happens at the cutoff frequency.
（下面理解截止频率处发生了什么。）

For steady-state sinusoidal analysis, we substitute $s = j\omega$:
（做稳态正弦分析时，代入 $s = j\omega$：）

$$
T(j\omega) = \frac{1}{1 + j\omega/\omega_c} \tag{18}
$$

To find the magnitude $|T(j\omega)|$, we need to find the length of this complex number.
（要求模 $|T(j\omega)|$，只需计算这个复数的长度。）

Here's the intuitive approach:
（直观思路如下：）

Think of the denominator as a complex number:
（把分母看作一个复数：）

$$
1 + j\frac{\omega}{\omega_c} = \text{real part} + j \cdot \text{imaginary part} \tag{19}
$$

The magnitude of a complex number $a + jb$ is $\sqrt{a^2 + b^2}$ (Pythagorean theorem!).
（复数 $a + jb$ 的模为 $\sqrt{a^2 + b^2}$（勾股定理！）。）

![](Pasted%20image%2020261117154734.png)
> 图6 Complex number magnitude using the Pythagorean theorem：复平面直角三角形，实边 $1$，虚边 $\omega/\omega_c$，斜边 $1 + j\omega/\omega_c$；At $\omega = \omega_c$: both sides = 1，$|1+j| = \sqrt{1^2+1^2} = \sqrt{2}$

Therefore:
（因此：）

$$
\left|1 + j\frac{\omega}{\omega_c}\right| = \sqrt{1^2 + \left(\frac{\omega}{\omega_c}\right)^2} = \sqrt{1 + \left(\frac{\omega}{\omega_c}\right)^2} \tag{20}
$$

Since the numerator is just 1, the magnitude of the transfer function is:
（由于分子为 1，传递函数的模为：）

$$
|T(j\omega)| = \frac{1}{\sqrt{1 + \left(\frac{\omega}{\omega_c}\right)^2}} \tag{21}
$$

This single equation tells us everything about the filter's behavior!
（仅凭这一个式子就能完整描述该滤波器的行为！）

**At low frequencies** ($\omega \ll \omega_c$):
（**低频时**（$\omega \ll \omega_c$）：）

$$
|T(j\omega)| \approx \frac{1}{\sqrt{1 + 0}} = 1 \quad \text{(signals pass through)} \tag{22}
$$

**At high frequencies** ($\omega \gg \omega_c$):
（**高频时**（$\omega \gg \omega_c$）：）

$$
|T(j\omega)| \approx \frac{1}{\sqrt{\left(\frac{\omega}{\omega_c}\right)^2}} = \frac{\omega_c}{\omega} \to 0 \quad \text{(signals are blocked)} \tag{23}
$$

**At the cutoff frequency** ($\omega = \omega_c$):
（**截止频率处**（$\omega = \omega_c$）：）

$$
|T(j\omega_c)| = \frac{1}{\sqrt{1 + \frac{\omega_c^2}{\omega_c^2}}} = \frac{1}{\sqrt{1 + 1}} = \frac{1}{\sqrt{2}} \approx 0.707 \tag{24}
$$

This is exactly where the -3 dB comes from!
（-3 dB 正是由此而来！）

Converting to decibels:
（换算成分贝：）

$$
20 \log_{10}\frac{1}{\sqrt{2}} = 20 \log_{10}(0.707) = -3.01 \approx -3\ \text{dB} \tag{25}
$$

![](Pasted%20image%2020261117154747.png)
> 图7 Magnitude response showing the -3 dB cutoff at $\omega = \omega_c$：$|T(j\omega)|$ 纵轴，$1.0$ 与 $0.707$（$\frac{1}{\sqrt{2}} \approx 70.7\%$，−3 dB point），横轴 $\omega/\omega_c$，标注 Passband 与 Stopband，$\omega_c$ 处转折

**The key insight:** At the cutoff frequency, the output voltage amplitude drops to $\frac{1}{\sqrt{2}} \approx 70.7\%$ of the input.
（**关键结论：** 在截止频率处，输出电压幅度降到输入的 $\frac{1}{\sqrt{2}} \approx 70.7\%$。）

This means the output power (which is proportional to voltage squared) drops to exactly half:
（这意味着输出功率（正比于电压的平方）恰好降为一半：）

$$
P_{out} = \left(\frac{1}{\sqrt{2}}\right)^2 \cdot P_{in} = \frac{1}{2} \cdot P_{in} = 50\% \text{ of input power} \tag{26}
$$

This is why $\omega_c$ is also called the half-power frequency!
（这就是 $\omega_c$ 又称半功率频率的原因！）

---

### 6. Understanding Decibels (dB)（理解分贝（dB））

Decibels provide a logarithmic scale for expressing ratios, which is particularly useful when dealing with signals that span many orders of magnitude.
（分贝用对数尺度表示比值，特别适合处理跨越多个数量级的信号。）

For power ratios:
（对功率比：）

$$
\text{Gain (dB)} = 10 \log_{10}\frac{P_{out}}{P_{in}} \tag{27}
$$

For voltage or current ratios:
（对电压或电流比：）

$$
\text{Gain (dB)} = 20 \log_{10}\frac{V_{out}}{V_{in}} \tag{28}
$$

**Why use 20 log10 for voltages?**（为什么电压用 20 log10？）

Since power is proportional to the square of voltage ($P \propto V^2$), we have:
（由于功率正比于电压的平方（$P \propto V^2$），有：）

$$
10 \log_{10}\frac{V_{out}^2}{V_{in}^2} = 10 \cdot 2 \log_{10}\frac{V_{out}}{V_{in}} = 20 \log_{10}\frac{V_{out}}{V_{in}} \tag{29}
$$

This ensures that voltage gain in dB matches power gain in dB for a given circuit.
（这样可保证同一电路的电压增益（dB）与功率增益（dB）一致。）

---

### 7. The Cut-Off Frequency and the -3 dB Point（截止频率与 -3 dB 点）

As we saw in the derivation above, the cut-off frequency $\omega_c$ (or $f_c$ in hertz) is defined as the frequency where the output voltage amplitude drops to $\frac{1}{\sqrt{2}} \approx 0.707$ (about 70.7%) of its maximum value.
（如前推导，截止频率 $\omega_c$（以赫兹表示时记作 $f_c$）定义为输出电压幅度降到其最大值的 $\frac{1}{\sqrt{2}} \approx 0.707$（约 70.7%）处的频率。）

**Summary: Why -3 dB?**（小结：为什么是 -3 dB？）

At the cut-off frequency:
（在截止频率处：）

$$
20 \log_{10}\frac{1}{\sqrt{2}} = 20 \log_{10}(0.707) = -3.01 \approx -3\ \text{dB} \tag{30}
$$

The -3 dB point is significant because:
（-3 dB 点之所以重要，是因为：）

- The output voltage amplitude is reduced by a factor of $\sqrt{2}$.
  （输出电压幅度降为原来的 $1/\sqrt{2}$。）
- The output **power** is reduced by half (50%), since $P \propto V^2$ and $\left(\frac{1}{\sqrt{2}}\right)^2 = \frac{1}{2}$.
  （输出**功率**减半（50%），因为 $P \propto V^2$ 且 $\left(\frac{1}{\sqrt{2}}\right)^2 = \frac{1}{2}$。）
- This marks the boundary between the passband (where signals pass through) and the stopband (where signals are attenuated).
  （它标出了通带（信号通过）与阻带（信号被衰减）的分界。）


![](Pasted%20image%2020261117154812.png)
> 图8 常用分贝参考值及其对应的幅值比（Key Decibel Values）：
>  $0$ dB: $|T| = 1$ (no change)
>   （幅值无变化）
>  $-3$ dB: $|T| = \frac{1}{\sqrt{2}} = 0.707$ (cutoff frequency)
>   （截止频率处）
>  $-6$ dB: $|T| = \frac{1}{2} = 0.5$
>  $-20$ dB: $|T| = \frac{1}{10} = 0.1$

---

### 8. Understanding -6 dB and -20 dB（理解 -6 dB 与 -20 dB）

- **-6 dB:** Corresponds to a voltage reduction by a factor of 2:
  （**-6 dB：** 对应电压降为 $1/2$：）

$$
20 \log_{10}\left(\frac{1}{2}\right) = -6.02 \approx -6\ \text{dB} \tag{31}
$$

This is the amount of attenuation per octave (frequency doubling) for a first-order filter beyond the cut-off frequency.
（这是一阶滤波器在截止频率以外每倍频程（频率加倍）的衰减量。）

- **-20 dB:** Corresponds to a voltage reduction by a factor of 10:
  （**-20 dB：** 对应电压降为 $1/10$：）

$$
20 \log_{10}\left(\frac{1}{10}\right) = -20\ \text{dB} \tag{32}
$$

This is the amount of attenuation per decade (10× frequency increase) for a first-order filter beyond the cut-off frequency.
（这是一阶滤波器在截止频率以外每十倍频程（频率增大 10 倍）的衰减量。）

These values describe the **roll-off rate** of the filter, which tells us how quickly the filter attenuates signals beyond the cut-off frequency.
（这些数值描述滤波器的**滚降速率**，即滤波器在截止频率以外衰减信号的速度。）

---

### 9. Converting Between Radians and Hertz（弧度与赫兹的换算）

Angular frequency $\omega$ (in radians per second) and cyclic frequency $f$ (in hertz) are related by:
（角频率 $\omega$（弧度每秒）与循环频率 $f$（赫兹）的关系为：）

$$
\omega = 2\pi f \quad \text{or} \quad f = \frac{\omega}{2\pi} \tag{33}
$$

One complete cycle corresponds to $2\pi$ radians, so when converting from rad/s to Hz, we divide by $2\pi$.
（一个完整周期对应 $2\pi$ 弧度，因此由 rad/s 换算为 Hz 时除以 $2\pi$。）

**Example:** If $\omega_c = 10,000$ rad/s, then:
（**示例：** 若 $\omega_c = 10,000$ rad/s，则：）

$$
f_c = \frac{10,000}{2\pi} \approx 1592\ \text{Hz} \tag{34}
$$

---

### 10. What is a Bode Plot?（什么是 Bode 图？）

A Bode plot is a graphical representation of a transfer function's frequency response.
（Bode 图是传递函数频率响应的图形表示。）

It consists of **two** separate plots:
（它由**两**幅独立的图组成：）

1. **Magnitude plot:** Shows the gain $|T(j\omega)|$ in decibels (dB) versus frequency
   （**幅频图：** 以分贝（dB）表示增益 $|T(j\omega)|$ 随频率的变化）
2. **Phase plot:** Shows the phase angle $\angle T(j\omega)$ in degrees versus frequency
   （**相频图：** 以度表示相角 $\angle T(j\omega)$ 随频率的变化）

Both plots use a logarithmic scale for the frequency axis (horizontal), while the magnitude is plotted in dB and the phase in degrees (both on linear vertical scales).
（两图的频率轴（横轴）都用对数刻度，而幅度以 dB、相位以度表示（两者的纵轴都是线性刻度）。）

**Why are Bode plots so useful?**（Bode 图为何如此有用？）

- **Easy to sketch:** Using straight-line approximations, you can quickly sketch Bode plots by hand with reasonable accuracy.
  （**易于作图：** 利用直线近似，可手工快速画出精度尚可的 Bode 图。）
- **Wide frequency range:** The logarithmic frequency scale allows you to see behavior from DC (0 Hz) to very high frequencies on a single plot.
  （**频率范围宽：** 对数频率轴可在同一张图上看到从直流（0 Hz）到极高频的行为。）
- **System identification:** You can identify poles, zeros, and filter types just by looking at the plot's shape.
  （**系统辨识：** 仅凭图形形状就能识别极点、零点与滤波器类型。）
- **Design tool:** Engineers use Bode plots to design filters, amplifiers, and control systems by visualizing how component changes affect frequency response.
  （**设计工具：** 工程师借助 Bode 图直观看到元件变化对频率响应的影响，从而设计滤波器、放大器与控制系统。）
- **Multiplicative to additive:** When cascading systems, gains multiply in linear scale but add in dB, making analysis much simpler.
  （**乘法变加法：** 级联系统时，增益在线性尺度上相乘，在 dB 尺度上相加，分析大大简化。）

Named after Hendrik Wade Bode, who developed this technique while working at Bell Labs in the 1930s, Bode plots have become the standard way to visualize frequency response in electrical engineering.
（Bode 图以 Hendrik Wade Bode 命名，他于 1930 年代在贝尔实验室工作期间提出了这一方法；如今它已成为电气工程中可视化频率响应的标准手段。）

![](Pasted%20image%2020261117154846.png)
> 图9 The two components of a Bode plot: magnitude (top) and phase (bottom)（上图 Magnitude Plot：$|T(j\omega)|$ in dB 对 Frequency (Hz)；下图 Phase Plot：$\angle T(j\omega)$ in degrees 对 Frequency (Hz)）

---

### 11. Logarithmic Scales for Bode Plots（Bode 图的对数刻度）

**Why do Bode plots use logarithmic scales for frequency?**（Bode 图为何对频率使用对数刻度？）

- Circuits often operate over many orders of magnitude (e.g., from 1 Hz to 1 MHz).
  （电路常工作在多个数量级的频率范围（例如 1 Hz 到 1 MHz）。）
- Logarithmic scales compress wide frequency ranges into manageable plots.
  （对数刻度把很宽的频率范围压缩到便于绘制的图上。）
- Multiplication becomes addition on a log scale, simplifying analysis.
  （在对数尺度上乘法变为加法，简化了分析。）

**Key terms:**（关键术语：）

- **Octave:** A doubling of frequency (e.g., from 1 kHz to 2 kHz, or from 10 kHz to 20 kHz).
  （**倍频程：** 频率加倍（例如 1 kHz 到 2 kHz，或 10 kHz 到 20 kHz）。）
- **Decade:** A 10× increase in frequency (e.g., from 100 Hz to 1 kHz, or from 1 kHz to 10 kHz).
  （**十倍频程：** 频率增大 10 倍（例如 100 Hz 到 1 kHz，或 1 kHz 到 10 kHz）。）
- **Decibel (dB):** The vertical axis unit for gain magnitude, expressing ratios logarithmically.
  （**分贝（dB）：** 增益幅度纵轴的单位，用对数表示比值。）

Since $2^{10} = 1024 \approx 10^3$, one decade is approximately 3.32 octaves.
（由于 $2^{10} = 1024 \approx 10^3$，一个十倍频程约等于 3.32 个倍频程。）

This explains why:
（这就解释了：）

$$
20\ \text{dB/decade} = \frac{20\ \text{dB}}{3.32\ \text{octaves}} \approx 6\ \text{dB/octave} \tag{35}
$$

![](Pasted%20image%2020261117155016.png)
> 图10 Octaves and decades on a logarithmic frequency scale（Logarithmic Frequency Scale：Decade = 10× frequency，Octave = 2× frequency；刻度 1、10、100、1k、10k，标注 1 decade、1 decade 与 octave）

---

### 12. Important Features of Bode Plots（Bode 图的重要特征）

**Key features to identify in Bode plots:**（在 Bode 图中要识别的关键特征：）

1. **Low-frequency gain:** The horizontal asymptote at low frequencies (the DC gain for low-pass filters).
   （**低频增益：** 低频段的水平渐近线（低通滤波器的直流增益）。）
2. **Corner frequencies:** Frequencies where the slope of the magnitude plot changes (corresponding to poles or zeros).
   （**转折频率：** 幅频图斜率发生变化的频率（对应极点或零点）。）
3. **Cut-off frequency:** The -3 dB point, marking the transition between passband and stopband.
   （**截止频率：** 即 -3 dB 点，标出通带与阻带的过渡。）
4. **Roll-off:** The slope of the magnitude plot in the stopband region (e.g., -20 dB/decade for first-order filters, -40 dB/decade for second-order).
   （**滚降：** 阻带区幅频图的斜率（例如一阶滤波器 -20 dB/十倍频，二阶 -40 dB/十倍频）。）
5. **Relationship to poles and zeros:**（**与极点、零点的关系：**）

   - Each pole causes the magnitude to decrease by 20 dB/decade and introduces up to $-90^\circ$ phase shift.
     （每个极点使幅度以 20 dB/十倍频下降，并引入最多 $-90^\circ$ 的相移。）
   - Each zero causes the magnitude to increase by 20 dB/decade and introduces up to $+90^\circ$ phase shift.
     （每个零点使幅度以 20 dB/十倍频上升，并引入最多 $+90^\circ$ 的相移。）

![](Pasted%20image%2020261117155031.png)
> 图11 Typical Bode plots for a first-order low-pass filter showing magnitude (top) and phase (bottom)（上图 Gain (dB)：0 dB 水平段，$\omega_c$ 处 −3 dB，其后 −20 dB/decade；下图 Phase (°)：$0^\circ$ 水平段，$\omega_c$ 处 −45°，渐近 −90°）

---

### 13. Why We Learn to Sketch Bode Plots（为什么要学手绘 Bode 图）

While software tools like MATLAB can generate exact Bode plots instantly, learning to sketch them by hand is valuable because:
（虽然 MATLAB 等软件能瞬间生成精确的 Bode 图，但学会手绘仍有价值，因为：）

- **Develops intuition:** Hand-sketching forces you to understand the relationship between circuit topology, transfer function, and frequency response.
  （**培养直觉：** 手绘迫使你理解电路拓扑、传递函数与频率响应之间的关系。）
- **Quick analysis:** You can rapidly estimate filter behavior without needing a computer.
  （**快速分析：** 无需计算机即可迅速估算滤波器行为。）
- **Design insight:** When designing filters, you can quickly see how changing component values affects the frequency response.
  （**设计洞察：** 设计滤波器时，可迅速看出改变元件值对频率响应的影响。）
- **Error checking:** Hand sketches help you verify that computer-generated plots are correct.
  （**检查错误：** 手绘图可用来核对软件生成的图是否正确。）
- **Communication:** Sketching allows you to quickly communicate design ideas to colleagues.
  （**沟通表达：** 草图可让你迅速向同事表达设计思路。）

In the next tutorial, you'll learn systematic techniques for sketching both magnitude and phase Bode plots using straight-line approximations, which provide excellent accuracy with minimal calculation.
（下次辅导课将学习用直线近似系统绘制幅频与相频 Bode 图的方法，它以极少的计算量获得很好的精度。）

Now that we've introduced these fundamental concepts, let's apply them to analyze some practical RC filter circuits!
（基本概念介绍完毕，下面用它们分析几个实际的 RC 滤波电路！）

---

## 1 Question 1（第 1 题）

![](Pasted%20image%2020261117155043.png)
> 图12 Q1 circuit diagram：$v_i$ 经 $1\ \mathrm{k\Omega}$ 电阻接至中间节点，$100\ \mathrm{nF}$ 电容由该节点接地，$v_o$ 取自节点与地之间

**(a)** Write down the transfer function, $T(s)$, of the low-pass filter shown in Fig. 1 above in a standard Bode format.
（**(a)** 写出上图中低通滤波器的传递函数 $T(s)$，用标准 Bode 形式表示。）

**(b)** Find the cut-off frequency (in hertz) of the low-pass filter by directly reading the value from the transfer function expressed in standard Bode format.
（**(b)** 由标准 Bode 形式的传递函数直接读出低通滤波器的截止频率（单位赫兹）。）

**(c)** Consider that $s = j\omega$.
（**(c)** 考虑 $s = j\omega$。）

We then have that:
（于是有：）

$$
|T(j\omega)|^2 = T(s)T(-s)\bigg|_{s=j\omega} = T(j\omega)T(-j\omega) = T(j\omega)T^*(j\omega) \tag{1}
$$

Write down the expression for $|T(j\omega)|$.
（写出 $|T(j\omega)|$ 的表达式。）

It is usually easiest to calculate $T(s)T(-s)$ and then substitute
（通常最简便的做法是先算出 $T(s)T(-s)$，再代入）

$$
\omega^2 = -s^2 \tag{2}
$$

**(d)** Start MATLAB and plot the magnitude of the transfer function using the following commands:
（**(d)** 启动 MATLAB，用以下命令画出传递函数的幅频特性：）

```matlab
>> omega = (0.1*10000:100:10*10000);
>> Tmag = 20*log10(sqrt(1./(1+omega.^2/10000^2)));
>> semilogx(omega,Tmag)
>> grid on
```

Add a title and axis labels using the `title`, `xlabel`, and `ylabel` commands.
（用 `title`、`xlabel`、`ylabel` 命令添加标题与坐标轴标签。）

Alternatively, also try:
（或者也可以试试：）

```matlab
>> omega = (0.1*10000:100:10*10000);
>> T = 1./(1+j*omega/10000);
>> figure; semilogx(omega,20*log10(abs(T)))
>> grid on
```

Now plot the phase of the transfer function using:
（再用下面的命令画相频特性：）

```matlab
>> omega = (0.1*10000:100:10*10000);
>> T = 1./(1+j*omega/10000);
>> figure; semilogx(omega,angle(T))
>> grid on
```

Please ensure that the above MATLAB commands, mathematics, and magnitude and phase plots make sense to you.
（请确保能理解上述 MATLAB 命令、其中的数学以及幅频、相频图形。）

**(e)** Transfer functions are ubiquitous in engineering, and MATLAB has a `bode` function to automatically create the Bode plot for you.
（**(e)** 传递函数在工程中无处不在，MATLAB 提供了 `bode` 函数可自动生成 Bode 图。）

The first step is to create a "transfer function" object.
（第一步是创建一个“传递函数”对象。）

The transfer function object is created by expressing the coefficients of the polynomial in $s$ for the numerator and denominator.
（该对象通过给出分子、分母中 $s$ 多项式的系数来创建。）

Please type `doc bode` in MATLAB for a description of the `bode` function and how to use it.
（请在 MATLAB 中输入 `doc bode`，查看 `bode` 函数的说明及用法。）

Create a Bode plot for the low-pass filter using the following MATLAB commands:
（用以下 MATLAB 命令为低通滤波器绘制 Bode 图：）

```matlab
>> g = tf([1],[1/10000 1]);
>> bode(g)
```

Type `g` at the MATLAB prompt and see what it returns.
（在 MATLAB 提示符下输入 `g`，看看它返回什么。）

**(f)** Use a Bode magnitude plot to help answer the questions below:
（**(f)** 借助 Bode 幅频图回答下列问题：）

**(i)** What is the magnitude of the transfer function in dB at the frequency of 10,000 rad/s? What does this mean?
（**(i)** 在 10,000 rad/s 处，传递函数的幅度为多少 dB？这意味着什么？）

**(ii)** It is said that a first-order low-pass filter has a 6 dB/octave or 20 dB/decade roll-off.
（**(ii)** 据说一阶低通滤波器的滚降为 6 dB/倍频程或 20 dB/十倍频。）

Compare the gain magnitude at 30,000 rad/s and at 60,000 rad/s.
（比较 30,000 rad/s 与 60,000 rad/s 处的增益幅度。）

Is it roughly a 6 dB difference?
（两者之差大约是 6 dB 吗？）

**(iii)** It is important to understand what a 6 dB/octave roll-off actually means.
（**(iii)** 理解 6 dB/倍频程滚降的确切含义很重要。）

What happens to the magnitude of the voltage output as the frequency doubles from 30,000 rad/s to 60,000 rad/s?
（当频率由 30,000 rad/s 加倍到 60,000 rad/s 时，输出电压幅度如何变化？）

Explain what a 20 dB/decade roll-off means and why it is the same as a 6 dB/octave roll-off.
（解释 20 dB/十倍频滚降的含义，以及它为何等同于 6 dB/倍频程滚降。）

### Solution:（解答：）

**符号说明**：
- $T(s)$：传递函数
- $s$：复频率变量，稳态正弦分析时取 $s=j\omega$
- $\omega$：角频率（rad/s）；$f$：频率（Hz），$\omega = 2\pi f$
- $|T(j\omega)|$：传递函数的模（幅度）；$\angle T(j\omega)$：相角
- $\omega_c$：截止角频率（即极点频率）
- $R$：电阻；$C$：电容；$Z_R$、$Z_C$：电阻、电容的复阻抗
- $\tau = RC$：电路时间常数

#### 1.1 Part A: Deriving the Transfer Function in Standard Bode Form（A 部分：推导标准 Bode 形式的传递函数）

---

>识别电路与阻抗

The circuit shows a resistor-capacitor (RC) low-pass filter.
（该电路是电阻-电容（RC）低通滤波器。）

To find the transfer function, we use the **voltage divider rule**, which works in the s-domain just as it does with resistors!
（求传递函数要用**分压定律**，它在 s 域中与在电阻网络中完全一样适用！）

**Step 1: Identify the impedances**（**第 1 步：确定各阻抗**）

From the circuit diagram, we have:
（由电路图可得：）

- Resistor: $R = 1000\ \Omega$ with impedance $Z_R = R = 1000\ \Omega$
  （电阻：$R = 1000\ \Omega$，阻抗 $Z_R = R = 1000\ \Omega$）
- Capacitor: $C = 100\ \mathrm{nF} = 100 \times 10^{-9}$ F with impedance $Z_C = \dfrac{1}{sC}$
  （电容：$C = 100\ \mathrm{nF} = 100 \times 10^{-9}$ F，阻抗 $Z_C = \dfrac{1}{sC}$）

Notice that the resistor impedance is simply its resistance value, while the capacitor has a frequency-dependent impedance.
（注意电阻的阻抗就是其阻值，而电容的阻抗随频率变化。）

This is the power of s-domain analysis—we can treat capacitors like generalized resistors!
（这正是 s 域分析的威力——可以把电容当作广义电阻来处理！）

---

>应用分压公式

**Step 2: Apply the voltage divider formula**（**第 2 步：应用分压公式**）

Since the output voltage is taken across the capacitor, and the resistor and capacitor are in series, we can write:
（由于输出电压取自电容两端，且电阻与电容串联，可写出：）

$$
T(s) = \frac{V_o(s)}{V_i(s)} = \frac{Z_C}{Z_R + Z_C} \tag{3}
$$

This is exactly the same formula you'd use for two resistors in a voltage divider!
（这与两个电阻构成分压器时所用的公式完全相同！）

---

>代入阻抗并化简

**Step 3: Substitute the impedances**（**第 3 步：代入阻抗**）

Substituting $Z_R = 1000\ \Omega$ and $Z_C = \dfrac{1}{sC} = \dfrac{1}{s(100 \times 10^{-9}\ \mathrm{F})}$:
（代入 $Z_R = 1000\ \Omega$ 与 $Z_C = \dfrac{1}{sC} = \dfrac{1}{s(100 \times 10^{-9}\ \mathrm{F})}$：）

$$
T(s) = \frac{\frac{1}{s(100 \times 10^{-9})}}{1000 + \frac{1}{s(100 \times 10^{-9})}} \tag{4}
$$

**Step 4: Simplify using the "flipping trick"**（**第 4 步：用“翻转技巧”化简**）

To get this into standard Bode form, we want to isolate $s$ in a clean way.
（为化为标准 Bode 形式，需要把 $s$ 干净地分离出来。）

Here's the key algebraic trick: multiply both the numerator and denominator by $s(100 \times 10^{-9})$ to eliminate the fraction within a fraction:
（关键的代数技巧是：分子分母同乘 $s(100 \times 10^{-9})$，消去繁分式：）

$$
T(s) = \frac{\frac{1}{s(100 \times 10^{-9})} \cdot s(100 \times 10^{-9})}{\left[1000 + \frac{1}{s(100 \times 10^{-9})}\right] \cdot s(100 \times 10^{-9})}
$$

$$
= \frac{1}{1000 \cdot s(100 \times 10^{-9}) + 1} = \frac{1}{1 + s(1000\ \Omega)(100 \times 10^{-9}\ \mathrm{F})} \tag{5}
$$

---

>求 $RC$ 与截止频率

**Step 5: Calculate the RC product**（**第 5 步：计算 RC 乘积**）

$$
RC = (1000\ \Omega)(100 \times 10^{-9}\ \mathrm{F}) = 1 \times 10^{-4}\ \mathrm{s} = 0.0001\ \mathrm{s} \tag{6}
$$

**Step 6: Extract the cutoff frequency**（**第 6 步：求截止频率**）

The standard Bode form requires us to write the denominator as $(1 + s/\omega_c)$.
（标准 Bode 形式要求把分母写成 $(1 + s/\omega_c)$。）

Currently we have $(1 + sRC)$.
（目前得到的是 $(1 + sRC)$。）

To match the standard form, we need:
（为与标准形式对应，需要：）

$$
sRC = \frac{s}{\omega_c} \quad \Rightarrow \quad \omega_c = \frac{1}{RC} \tag{7}
$$

Therefore:
（因此：）

$$
\omega_c = \frac{1}{RC} = \frac{1}{1 \times 10^{-4}\ \mathrm{s}} = 10,000\ \mathrm{rad/s} \tag{8}
$$

---

>化为标准形式、记录结果

**Step 7: Write in standard Bode form**（**第 7 步：写成标准 Bode 形式**）

Finally, substituting $\omega_c$ into equation (5):
（最后把 $\omega_c$ 代入式 (5)：）

$$
T(s) = \frac{1}{1 + \frac{s}{10,000\ \mathrm{rad/s}}} \tag{9}
$$

**Verification: Is this standard Bode form?**（**验证：这是标准 Bode 形式吗？**）

The general standard Bode form for a first-order low-pass filter is:
（一阶低通滤波器的通用标准 Bode 形式为：）

$$
T(s) = \frac{A}{1 + \frac{s}{\omega_c}} \tag{10}
$$

where $A$ is the DC gain and $\omega_c$ is the cutoff angular frequency.
（其中 $A$ 为直流增益，$\omega_c$ 为截止角频率。）

Comparing with our result in equation (9):
（与式 (9) 的结果对照：）

- DC gain: $A = 1$ (no amplification or attenuation at DC)
  （直流增益：$A = 1$（直流时既不放大也不衰减））
- Cutoff frequency: $\omega_c = 10,000$ rad/s (directly readable from the denominator!)
  （截止频率：$\omega_c = 10,000$ rad/s（可直接从分母读出！））

> [!note] 标准 Bode 形式的判读
> 低通：$T(s)=\dfrac{A}{1+s/\omega_c}$，分母中 $s$ 的系数倒数即 $\omega_c$，分子常数即直流增益 $A$。
> 高通：$T(s)=A\cdot\dfrac{s/\omega_c}{1+s/\omega_c}$，分子含 $s$ 项。

**How do we know this is a low-pass filter?**（**怎么知道这是低通滤波器？**）

We can tell this is a low-pass filter from the transfer function form:
（由传递函数的形式即可判断它是低通滤波器：）

- At low frequencies ($s \to 0$): $T(s) \to 1/(1+0) = 1$, so signals pass through
  （低频时（$s \to 0$）：$T(s) \to 1/(1+0) = 1$，信号通过）
- At high frequencies ($s \to \infty$): $T(s) \to 0$, so signals are blocked
  （高频时（$s \to \infty$）：$T(s) \to 0$，信号被阻挡）
- The numerator is constant (no $s$ term), while the denominator increases with $s$
  （分子为常数（不含 $s$ 项），而分母随 $s$ 增大）

This confirms the filter passes low frequencies and attenuates high frequencies—exactly what a low-pass filter does!
（这证实该滤波器通低频、衰高频——正是低通滤波器的作用！）

---

#### 1.2 Part B: Reading the Cutoff Frequency from Standard Bode Form（B 部分：由标准 Bode 形式直接读出截止频率）

One of the main advantages of expressing the transfer function in standard Bode form is that we can **directly read** the cutoff frequency without any calculation!
（把传递函数写成标准 Bode 形式的一大好处是：无需任何计算即可**直接读出**截止频率！）

From equation (9):
（由式 (9)：）

$$
T(s) = \frac{1}{1 + \frac{s}{10,000\ \mathrm{rad/s}}} \tag{11}
$$

The denominator has the form $(1 + s/\omega_c)$, so by inspection:
（分母具有 $(1 + s/\omega_c)$ 的形式，故直接看出：）

$$
\omega_c = 10,000\ \mathrm{rad/s} \tag{12}
$$

To convert to hertz (cycles per second), we use the relationship $\omega = 2\pi f$:
（换算为赫兹（每秒周期数）时，用关系式 $\omega = 2\pi f$：）

$$
f_c = \frac{\omega_c}{2\pi} = \frac{10,000\ \mathrm{rad/s}}{2\pi\ \mathrm{rad/cycle}} \approx 1591.55\ \mathrm{Hz} \tag{13}
$$

**Physical interpretation:** At this cutoff frequency, the output voltage amplitude drops to $\frac{1}{\sqrt{2}} \approx 0.707$ (or $-3$ dB) of the input voltage amplitude, and the output power drops to exactly half of the input power.
（**物理解释：** 在该截止频率处，输出电压幅度降到输入电压幅度的 $\frac{1}{\sqrt{2}} \approx 0.707$（即 $-3$ dB），输出功率恰好降为输入功率的一半。）

---

#### 1.3 Part C - Finding the Magnitude Response:（C 部分——求幅频响应）

---

>构造 $T(s)T(-s)$

To determine the magnitude of the transfer function, we start by forming the product $T(s)T(-s)$:
（为求传递函数的模，先构造乘积 $T(s)T(-s)$：）

$$
T(s)T(-s) = \frac{1}{(1 + s/10,000)(1 - s/10,000)} = \frac{1}{1 - \frac{s^2}{(10,000)^2}} \tag{14}
$$

---

>代入 $s=j\omega$

Next, we substitute $s = j\omega$ for steady-state sinusoidal analysis.
（接着做稳态正弦分析，代入 $s = j\omega$。）

Recall that the imaginary unit has the property $j^2 = -1$, so:
（注意虚数单位满足 $j^2 = -1$，故：）

$$
s^2 = (j\omega)^2 = j^2\omega^2 = -\omega^2 \tag{15}
$$

Therefore, substituting $s = j\omega$ and using $s^2 = -\omega^2$:
（因此代入 $s = j\omega$ 并利用 $s^2 = -\omega^2$：）

$$
T(s)T(-s)\bigg|_{s=j\omega} = \frac{1}{1 - \frac{-\omega^2}{(10,000)^2}} = \frac{1}{1 + \frac{\omega^2}{(10,000)^2}} \tag{16}
$$

This step shows why the $-s^2$ becomes $+\omega^2$: the negative sign from $-s^2$ combines with the $j^2 = -1$ to give a positive result!
（这一步说明了为何 $-s^2$ 变成 $+\omega^2$：$-s^2$ 的负号与 $j^2 = -1$ 相乘得到正号！）

---

>写出 $|T(j\omega)|$

Therefore, the squared magnitude of the transfer function is
（因此传递函数模的平方为）

$$
|T(j\omega)|^2 = \frac{1}{1 + \frac{\omega^2}{(10,000)^2}} \tag{17}
$$

Taking the square root, we find the magnitude response
（开平方即得幅频响应）

$$
|T(j\omega)| = \frac{1}{\sqrt{1 + \frac{\omega^2}{(10,000)^2}}} \tag{18}
$$

> [!warning] 分母不要漏掉平方
> 这里分母是 $1 + \omega^2/(10,000)^2$，而不是 $1 + \omega^2/10,000$。因为 $\omega_c = 10{,}000$，标准式中出现的是 $(\omega/\omega_c)^2 = \omega^2/(10{,}000)^2$。

This equation shows that at low frequencies ($\omega \ll \omega_c$), $|T(j\omega)| \approx 1$, meaning the signal passes with little attenuation.
（该式表明：低频时（$\omega \ll \omega_c$），$|T(j\omega)| \approx 1$，信号几乎无衰减地通过。）

At high frequencies ($\omega \gg \omega_c$), the denominator becomes large and $|T(j\omega)| \propto 1/\omega$, indicating that the output magnitude decreases with frequency.
（高频时（$\omega \gg \omega_c$），分母变大，$|T(j\omega)| \propto 1/\omega$，说明输出幅度随频率升高而下降。）

---

#### 1.4 Part D: Creating Bode Plots Using MATLAB（D 部分：用 MATLAB 绘制 Bode 图）

> [!info] MATLAB Online Access（MATLAB 在线访问）
> If you don't have MATLAB installed on your computer, you can use MATLAB Online for free with your university account!
> （如果电脑上没有安装 MATLAB，可用学校账号免费使用 MATLAB Online！）
>
> Simply visit: https://matlab.mathworks.com/ Log in with your university credentials to access a full MATLAB environment in your web browser.
> （访问 https://matlab.mathworks.com/ ，用学校账号登录，即可在浏览器中获得完整的 MATLAB 环境。）
>
> All the commands in this tutorial will work identically in MATLAB Online.
> （本次辅导课中的所有命令在 MATLAB Online 中效果完全相同。）

---

>运行 MATLAB 计算幅频

In this part, we'll create Bode plots by explicitly calculating the magnitude and phase from the transfer function.
（本部分通过显式计算传递函数的幅度与相位来绘制 Bode 图。）

**MATLAB Code (Method 1: Calculating magnitude manually):**（**MATLAB 代码（方法 1：手工计算幅度）：**）

```matlab
>> omega = (0.1*10000:100:10*10000);
>> Tmag = 20*log10(sqrt(1./(1+omega.^2/10000^2)));
>> semilogx(omega,Tmag)
>> grid on
```

Let's break down each command:
（逐条解释各命令：）

- `omega = (0.1*10000:100:10*10000)`: Creates a vector of frequency values from 1,000 to 100,000 rad/s in steps of 100.
  （`omega = (0.1*10000:100:10*10000)`：生成从 1,000 到 100,000 rad/s、步长 100 的频率向量。）

  This range covers frequencies well below and above the cutoff frequency.
  （该范围覆盖了远低于和远高于截止频率的频率。）
- `Tmag = 20*log10(sqrt(1./(1+omega.^2/10000^2)))`: Calculates the magnitude in dB.
  （`Tmag = 20*log10(sqrt(1./(1+omega.^2/10000^2)))`：计算以 dB 表示的幅度。）

  This implements the formula:
  （它实现的是公式：）

$$
|T(j\omega)|_{\mathrm{dB}} = 20 \log_{10}\frac{1}{\sqrt{1 + (\omega/\omega_c)^2}}
$$

The `.^` operator performs element-wise exponentiation, and `./` performs element-wise division.
（`.^` 运算符执行逐元素乘方，`./` 执行逐元素除法。）

- `semilogx(omega,Tmag)`: Plots magnitude vs frequency with a logarithmic frequency axis (required for Bode plots).
  （`semilogx(omega,Tmag)`：以对数频率轴绘制幅度-频率曲线（Bode 图必需）。）
- `grid on`: Enables grid lines for easier reading of values.
  （`grid on`：打开网格线，便于读数。）

---

>用复数运算复核

**MATLAB Code (Method 2: Using complex arithmetic):**（**MATLAB 代码（方法 2：用复数运算）：**）

```matlab
>> omega = (0.1*10000:100:10*10000);
>> T = 1./(1+j*omega/10000);
>> figure; semilogx(omega,20*log10(abs(T)))
>> grid on
```

This method evaluates $T(j\omega) = \dfrac{1}{1+j\omega/\omega_c}$ as a complex number, then uses `abs(T)` to find its magnitude.
（该方法把 $T(j\omega) = \dfrac{1}{1+j\omega/\omega_c}$ 作为复数计算，再用 `abs(T)` 求其模。）

This is often more intuitive as it directly uses the transfer function form.
（它直接使用传递函数形式，往往更直观。）

---

>画相频

**Phase Plot:**（**相频图：**）

```matlab
>> omega = (0.1*10000:100:10*10000);
>> T = 1./(1+j*omega/10000);
>> figure; semilogx(omega,angle(T)*180/pi)
>> grid on
```

The `angle(T)` function returns the phase in radians, which we convert to degrees by multiplying by $180/\pi$.
（`angle(T)` 返回以弧度表示的相位，乘以 $180/\pi$ 换算为度。）

![](Pasted%20image%2020261117155143.png)
> 图13 Bode plot created using manual calculation (Part D)：上图幅频特性在低频段为 0 dB，截止频率 10,000 rad/s 处 −3 dB，高频段滚降；下图相频特性由低频 $0^\circ$ 过渡到高频 $-90^\circ$

The magnitude plot shows the characteristic low-pass behavior: flat response at low frequencies (0 dB), $-3$ dB at the cutoff frequency (10,000 rad/s), and roll-off at high frequencies.
（幅频图呈现典型的低通特性：低频平坦（0 dB），截止频率（10,000 rad/s）处为 $-3$ dB，高频段滚降。）

The phase plot shows the phase shift ranging from $0^\circ$ at low frequencies to $-90^\circ$ at high frequencies.
（相频图显示相移从低频的 $0^\circ$ 变化到高频的 $-90^\circ$。）

---

#### 1.5 Part E: Using MATLAB's Built-in Bode Functions（E 部分：使用 MATLAB 内置 Bode 函数）

While Part D showed us how to manually calculate and plot the Bode diagram, MATLAB provides powerful built-in functions that make this much easier: `tf()` and `bode()`.
（D 部分演示了如何手工计算并绘制 Bode 图，而 MATLAB 提供了强大的内置函数 `tf()` 与 `bode()`，使这一过程容易得多。）

**The `tf()` Function:**（**`tf()` 函数：**）

The `tf()` function creates a transfer function object from the numerator and denominator polynomials in $s$.
（`tf()` 函数由分子、分母中 $s$ 的多项式创建传递函数对象。）

Our transfer function is:
（本题的传递函数为：）

$$
T(s) = \frac{1}{1 + \frac{s}{10,000}} = \frac{10,000}{s + 10,000}
$$

Written as a ratio of polynomials:
（写成多项式之比：）

$$
T(s) = \frac{1 \cdot s^0}{(1/10,000) \cdot s^1 + 1 \cdot s^0}
$$

The coefficients are:
（各系数为：）

- Numerator: `[1]` (just the constant 1)
  （分子：`[1]`（即常数 1））
- Denominator: `[1/10,000, 1]` (coefficient of $s$ and constant term)
  （分母：`[1/10,000, 1]`（$s$ 的系数与常数项））

**The `bode()` Function:**（**`bode()` 函数：**）

The `bode()` function automatically generates both magnitude and phase Bode plots from a transfer function object.
（`bode()` 函数可由传递函数对象自动生成幅频与相频 Bode 图。）

**MATLAB Code:**（**MATLAB 代码：**）

```matlab
>> g = tf([1],[1/10000 1]);
>> bode(g)
```

When you type `g` at the MATLAB prompt, it displays:
（在 MATLAB 提示符下输入 `g`，会显示：）

```text
Transfer function:
      10000
  -------------
  s + 10000
```

This confirms that MATLAB has correctly constructed our transfer function!
（这证实 MATLAB 正确构造了我们的传递函数！）

**Advantages of using `bode()`:**（**使用 `bode()` 的优点：**）

- Automatically handles the logarithmic frequency axis
  （自动处理对数频率轴）
- Provides proper scaling and axis labels
  （提供合适的刻度与坐标轴标签）
- Interactive cursor allows you to read exact values at any frequency
  （交互式游标可在任意频率处读精确数值）
- Works for transfer functions of any order
  （适用于任意阶的传递函数）

![](Pasted%20image%2020261117155223.png)
> 图14 Bode plot created using MATLAB's bode() function (Part E)：幅频与相频 Bode 图，与 Part D 手工计算结果一致

The plot created by `bode()` is identical to the one we made manually in Part D, but required much less code!
（`bode()` 生成的图与 D 部分手工绘制的结果一致，但代码少得多！）

This is the preferred method for creating Bode plots in practice.
（实际中这是绘制 Bode 图的首选方法。）

---

#### 1.6 Part F: Interpreting the Bode Magnitude Plot（F 部分：解读 Bode 幅频图）

---

>第 (i) 问：截止频率处的幅度

**(i) Magnitude at the cutoff frequency**（**(i) 截止频率处的幅度**）

At $\omega = 10,000$ rad/s (the cutoff frequency), the magnitude read from the Bode plot is $-3$ dB.
（在 $\omega = 10,000$ rad/s（截止频率）处，从 Bode 图读出的幅度为 $-3$ dB。）

$$
|T(j10,000)|_{\mathrm{dB}} = 20 \log_{10}\frac{1}{\sqrt{1 + 1^2}} = 20 \log_{10}\frac{1}{\sqrt{2}} = -3.01 \approx -3\ \text{dB}
$$

**What does this mean?**（**这意味着什么？**）

The -3 dB means the output voltage amplitude is $1/\sqrt{2} \approx 70.7\%$ of the input, and the output power is exactly 50% of the input power.
（-3 dB 表示输出电压幅度为输入的 $1/\sqrt{2} \approx 70.7\%$，输出功率恰为输入功率的 50%。）

This defines the cutoff point—the boundary between passband and stopband.
（这正是截止点的定义——通带与阻带的分界。）

---

>第 (ii) 问：30,000 与 60,000 rad/s 的增益比较

**(ii) Gain comparison at different frequencies**（**(ii) 不同频率下的增益比较**）

At $\omega = 30,000$ rad/s (3× the cutoff frequency):
（在 $\omega = 30,000$ rad/s（截止频率的 3 倍）处：）

$$
|T(j30,000)|_{\mathrm{dB}} = 20 \log_{10}\frac{1}{\sqrt{1 + (30,000/10,000)^2}} = 20 \log_{10}\frac{1}{\sqrt{1 + 9}} = 20 \log_{10}\frac{1}{\sqrt{10}} = 20 \log_{10}(0.316) = -10.0\ \text{dB} \tag{19}
$$

At $\omega = 60,000$ rad/s (6× the cutoff frequency):
（在 $\omega = 60,000$ rad/s（截止频率的 6 倍）处：）

$$
|T(j60,000)|_{\mathrm{dB}} = 20 \log_{10}\frac{1}{\sqrt{1 + (60,000/10,000)^2}} = 20 \log_{10}\frac{1}{\sqrt{1 + 36}} = 20 \log_{10}\frac{1}{\sqrt{37}} = 20 \log_{10}(0.164) = -15.7\ \text{dB} \tag{20}
$$

**Comparison:** Going from 30,000 to 60,000 rad/s (one octave doubling): the gain changes from $-10.0$ dB to $-15.7$ dB, a difference of approximately $5.7$ dB, which is close to the theoretical $-6$ dB per octave.
（**比较：** 从 30,000 到 60,000 rad/s（一个倍频程）：增益由 $-10.0$ dB 变为 $-15.7$ dB，相差约 $5.7$ dB，接近理论值每倍频程 $-6$ dB。）

---

>第 (iii) 问：滚降的物理含义

**(iii) What does 20 dB/decade (or 6 dB/octave) mean?**（**(iii) 20 dB/十倍频（或 6 dB/倍频程）是什么意思？**）

**What happens to voltage amplitude as frequency doubles?**（**频率加倍时电压幅度如何变化？**）

As the frequency doubles (one octave), the output voltage amplitude is cut in half:
（频率加倍（一个倍频程）时，输出电压幅度减半：）

- At 30,000 rad/s: $|T| = 1/\sqrt{10} \approx 0.316$ (31.6% of input)
  （30,000 rad/s 处：$|T| = 1/\sqrt{10} \approx 0.316$（输入的 31.6%））
- At 60,000 rad/s: $|T| = 1/\sqrt{37} \approx 0.164$ (16.4% of input)
  （60,000 rad/s 处：$|T| = 1/\sqrt{37} \approx 0.164$（输入的 16.4%））

The ratio $0.164/0.316 \approx 0.519 \approx 1/2$, confirming that voltage amplitude halves every octave.
（比值 $0.164/0.316 \approx 0.519 \approx 1/2$，证实电压幅度每个倍频程减半。）

**Why 6 dB/octave = 20 dB/decade?**（**为什么 6 dB/倍频程 = 20 dB/十倍频？**）

Let's understand this with concrete numbers:
（用具体数值来理解：）

**Octave:** Frequency doubles (e.g., 10,000 → 20,000 rad/s)
（**倍频程：** 频率加倍（例如 10,000 → 20,000 rad/s））

- Gain decreases by approximately $-6$ dB
  （增益下降约 $-6$ dB）
- Voltage amplitude is cut in half
  （电压幅度减半）

**Decade:** Frequency increases 10× (e.g., 10,000 → 100,000 rad/s)
（**十倍频程：** 频率增大 10 倍（例如 10,000 → 100,000 rad/s））

How many octaves in one decade?
（一个十倍频程包含多少个倍频程？）

$$
2^x = 10 \quad \Rightarrow \quad x = \log_2(10) = \frac{\ln(10)}{\ln(2)} = 3.322\ \text{octaves}
$$

Therefore:
（因此：）

$$
\text{Gain change per decade} = 3.322\ \text{octaves} \times (-6\ \text{dB/octave}) = -19.9 \approx -20\ \text{dB}
$$

**Numerical verification:**（**数值验证：**）

At $\omega = 10,000$ rad/s: $|T|_{\mathrm{dB}} = -3$ dB
（在 $\omega = 10,000$ rad/s：$|T|_{\mathrm{dB}} = -3$ dB）

At $\omega = 100,000$ rad/s (one decade higher):
（在 $\omega = 100,000$ rad/s（高一个十倍频程）：）

$$
|T(j100,000)|_{\mathrm{dB}} = 20 \log_{10}\left(\frac{1}{\sqrt{1 + (100,000/10,000)^2}}\right)
$$

$$
= 20 \log_{10}\left(\frac{1}{\sqrt{101}}\right) = -20.0\ \text{dB} \tag{21}
$$

Difference: $-20.0 - (-3.0) = -17$ dB (close to $-20$ dB for higher frequencies)
（差值：$-20.0 - (-3.0) = -17$ dB（在更高频率处接近 $-20$ dB））

**Summary:**（**小结：**）

- **6 dB/octave:** Voltage halves every time frequency doubles
  （**6 dB/倍频程：** 频率每加倍一次，电压减半）
- **20 dB/decade:** Voltage reduces to 1/10 every time frequency increases 10×
  （**20 dB/十倍频：** 频率每增大 10 倍，电压降为 1/10）
- **Both describe the same roll-off rate** because $10 \approx 2^{3.32}$
  （**两者描述同一滚降速率**，因为 $10 \approx 2^{3.32}$）
- This $-20$ dB/decade slope is characteristic of **first-order filters** (one reactive element)
  （该 $-20$ dB/十倍频的斜率是**一阶滤波器**（一个电抗元件）的特征）

---

## 2 Question 2（第 2 题）

![](Pasted%20image%2020261117155240.png)
> 图15 Q2 circuit diagram：$v_i$ 经 $5\ \mathrm{nF}$ 电容接至中间节点，$50\ \mathrm{k\Omega}$ 电阻由该节点接地，$v_o$ 取自节点与地之间

**(a)** Write down the transfer function, $T(s)$, of the high-pass filter shown above in a standard Bode format.
（**(a)** 写出上图高通滤波器的传递函数 $T(s)$，用标准 Bode 形式表示。）

**(b)** Find the cut-off frequency (in hertz) of the high-pass filter by directly reading the value from the transfer function expressed in standard Bode format.
（**(b)** 由标准 Bode 形式的传递函数直接读出高通滤波器的截止频率（单位赫兹）。）

**(c)** Use MATLAB to evaluate $T(j\omega)$ at 4000 rad/s, 800 rad/s, and 20000 rad/s in phasor form:
（**(c)** 用 MATLAB 在 4000 rad/s、800 rad/s 和 20000 rad/s 处把 $T(j\omega)$ 表示为相量形式：）

$$
T(j\omega) = |T(j\omega)| \angle \theta(\omega)
$$

**(d)** If the input voltage is
（**(d)** 若输入电压为）

$$
v_i(t) = 500 \cos(\omega t) \tag{1}
$$

write the steady-state expression for the output voltage $v_o(t)$ when $\omega = 4000$ rad/s, $\omega = 800$ rad/s, and $\omega = 20000$ rad/s.
（写出 $\omega = 4000$ rad/s、$\omega = 800$ rad/s 和 $\omega = 20000$ rad/s 时输出电压 $v_o(t)$ 的稳态表达式。）

### Solution:（解答：）

**符号说明**：
- $T(j\omega)$：正弦稳态下的传递函数（复数）
- $|T(j\omega)|$：幅度（增益）；$\theta(\omega)=\angle T(j\omega)$：相角
- $\omega_c$：截止角频率；$f_c$：截止频率（Hz）
- $R$：电阻；$C$：电容；$\tau = RC$：时间常数
- $v_i(t)$、$v_o(t)$：输入、输出电压的时域表达式
- 相量 $A\angle\theta$：幅度 $A$、相位 $\theta$ 的复数表示

#### 2.1 Part A: Deriving the High-Pass Filter Transfer Function（A 部分：推导高通滤波器的传递函数）

---

>识别电路与阻抗

The circuit shows a capacitor-resistor (CR) high-pass filter.
（该电路是电容-电阻（CR）高通滤波器。）

Notice that compared to the low-pass filter in Q1, the positions of the resistor and capacitor are swapped!
（注意与第 1 题的低通滤波器相比，电阻与电容的位置互换了！）

This simple change dramatically alters the filter's behavior.
（这一简单变化使滤波器行为发生根本改变。）

**Step 1: Identify the impedances**（**第 1 步：确定各阻抗**）

From the circuit diagram:
（由电路图：）

- Resistor: $R = 50\ \mathrm{k\Omega} = 50 \times 10^3\ \Omega$ with impedance $Z_R = R = 50 \times 10^3\ \Omega$
  （电阻：$R = 50\ \mathrm{k\Omega} = 50 \times 10^3\ \Omega$，阻抗 $Z_R = R = 50 \times 10^3\ \Omega$）
- Capacitor: $C = 5\ \mathrm{nF} = 5 \times 10^{-9}$ F with impedance $Z_C = \dfrac{1}{sC}$
  （电容：$C = 5\ \mathrm{nF} = 5 \times 10^{-9}$ F，阻抗 $Z_C = \dfrac{1}{sC}$）

---

>应用分压公式

**Step 2: Apply the voltage divider formula**（**第 2 步：应用分压公式**）

Since the output voltage is taken across the resistor (not the capacitor as in Q1), we write:
（由于输出电压取自电阻两端（而不是第 1 题中的电容），可写出：）

$$
T(s) = \frac{V_o(s)}{V_i(s)} = \frac{Z_R}{Z_C + Z_R} \tag{2}
$$

The key difference from Q1: the resistor is now in the numerator!
（与第 1 题的关键区别：电阻现在出现在分子中！）

---

>代入阻抗并化简

**Step 3: Substitute the impedances**（**第 3 步：代入阻抗**）

Substituting $Z_R = 50 \times 10^3\ \Omega$ and $Z_C = \dfrac{1}{sC} = \dfrac{1}{s(5 \times 10^{-9}\ \mathrm{F})}$:
（代入 $Z_R = 50 \times 10^3\ \Omega$ 与 $Z_C = \dfrac{1}{sC} = \dfrac{1}{s(5 \times 10^{-9}\ \mathrm{F})}$：）

$$
T(s) = \frac{50 \times 10^3}{50 \times 10^3 + \frac{1}{s(5 \times 10^{-9})}} \tag{3}
$$

**Step 4: Simplify using the algebraic trick**（**第 4 步：用代数技巧化简**）

Multiply both numerator and denominator by $s(5 \times 10^{-9})$:
（分子分母同乘 $s(5 \times 10^{-9})$：）

$$
T(s) = \frac{sRC}{sRC + 1} = \frac{sRC}{1 + sRC} \tag{4}
$$

---

>求 $RC$ 与截止频率

**Step 5: Calculate the RC product**（**第 5 步：计算 RC 乘积**）

$$
RC = (50 \times 10^3\ \Omega)(5 \times 10^{-9}\ \mathrm{F}) = 250 \times 10^{-6}\ \mathrm{s} = 2.5 \times 10^{-4}\ \mathrm{s} \tag{5}
$$

**Step 6: Convert to standard Bode form**（**第 6 步：化为标准 Bode 形式**）

The standard Bode form for a high-pass filter is:
（高通滤波器的标准 Bode 形式为：）

$$
T(s) = \frac{\frac{s}{\omega_c}}{1 + \frac{s}{\omega_c}} \tag{6}
$$

where $\omega_c$ is the cutoff frequency.
（其中 $\omega_c$ 为截止频率。）

Currently we have $T(s) = \dfrac{sRC}{1 + sRC}$.
（目前得到的是 $T(s) = \dfrac{sRC}{1 + sRC}$。）

To match the standard form, we need:
（为与标准形式对应，需要：）

$$
sRC = \frac{s}{\omega_c} \quad \Rightarrow \quad \omega_c = \frac{1}{RC} \tag{7}
$$

Therefore:
（因此：）

$$
\omega_c = \frac{1}{RC} = \frac{1}{2.5 \times 10^{-4}\ \mathrm{s}} = 4,000\ \mathrm{rad/s} \tag{8}
$$

---

>化为标准形式、记录结果

**Step 7: Write in standard Bode form**（**第 7 步：写成标准 Bode 形式**）

Substituting $\omega_c = 4,000$ rad/s:
（代入 $\omega_c = 4,000$ rad/s：）

$$
T(s) = \frac{\frac{s}{4,000\ \mathrm{rad/s}}}{1 + \frac{s}{4,000\ \mathrm{rad/s}}} \tag{9}
$$

**Verification: How do we know this is a high-pass filter?**（**验证：怎么知道这是高通滤波器？**）

From the transfer function form:
（由传递函数形式：）

- At low frequencies ($s \to 0$): $T(s) \to \frac{0}{1+0} = 0$, so low-frequency signals are blocked
  （低频时（$s \to 0$）：$T(s) \to \frac{0}{1+0} = 0$，低频信号被阻挡）
- At high frequencies ($s \to \infty$): $T(s) \to \frac{\infty}{\infty} = 1$ (using L'Hôpital's rule or dividing numerator and denominator by $s$), so high-frequency signals pass through
  （高频时（$s \to \infty$）：$T(s) \to \frac{\infty}{\infty} = 1$（可用洛必达法则，或分子分母同除 $s$），高频信号通过）
- The numerator has an $s$ term (increases with frequency), which is the signature of a high-pass filter
  （分子含 $s$ 项（随频率增大），这是高通滤波器的标志）

This confirms that the filter blocks low frequencies and passes high frequencies—exactly what a high-pass filter does!
（这证实该滤波器阻低频、通高频——正是高通滤波器的作用！）

> [!tip] Bonus: The RC Time Constant Method（附：RC 时间常数法）
> Notice that for simple first-order RC filters (whether low-pass or high-pass), the cutoff frequency can always be calculated directly from:
> （注意：对简单的一阶 RC 滤波器（无论低通还是高通），截止频率总可直接由下式计算：）
>
> $$
> \omega_c = \frac{1}{RC}
> $$
>
> This is a useful shortcut!
> （这是一个很有用的捷径！）
>
> The quantity $\tau = RC$ is called the time constant of the circuit.
> （量 $\tau = RC$ 称为电路的时间常数。）
>
> However, this simple relationship only works for first-order filters with a single resistor and single capacitor.
> （不过，这一简单关系只适用于只含一个电阻、一个电容的一阶滤波器。）
>
> For more complex filters, you must use the full voltage divider analysis to find the cutoff frequency from the transfer function.
> （对更复杂的滤波器，必须用完整的分压分析，从传递函数中求截止频率。）

---

#### 2.2 Part B（B 部分）

---

>由 $\omega_c$ 换算 $f_c$

The cut-off frequency is given as $\omega_c = 4000$ rad/s, which corresponds to a frequency in hertz:
（截止频率为 $\omega_c = 4000$ rad/s，对应的赫兹频率为：）

$$
f_c = \frac{\omega_c}{2\pi} = \frac{4000}{2\pi} = 636.62\ \mathrm{Hz} \tag{10}
$$

This is the frequency at which the output voltage magnitude falls to $\frac{1}{\sqrt{2}}$ (or $-3$ dB) of its maximum value.
（在该频率处，输出电压幅度降到其最大值的 $\frac{1}{\sqrt{2}}$（即 $-3$ dB）。）

---

#### 2.3 Part C: Evaluating the Transfer Function at Specific Frequencies（C 部分：在指定频率处计算传递函数）

**Why are we doing this calculation?**（**为什么要做这个计算？**）

This is a crucial step that bridges the gap between our theoretical transfer function and real-world circuit behavior!
（这一步很关键，它把理论传递函数与实际电路行为联系起来！）

Here's what we're accomplishing:
（我们要做的事情是：）

- We want to know: If we apply a sinusoidal input at a specific frequency, what will the output look like?
  （我们想知道：若在某一频率施加正弦输入，输出会是什么样？）
- The transfer function $T(j\omega)$ at a given frequency tells us two things:
  （给定频率处的传递函数 $T(j\omega)$ 告诉我们两件事：）
  - **Magnitude** $|T(j\omega)|$: By what factor the output amplitude is scaled compared to the input
    （**幅度** $|T(j\omega)|$：输出幅度相对输入被缩放的倍数）
  - **Phase** $\angle T(j\omega)$: How much the output is shifted in time relative to the input
    （**相位** $\angle T(j\omega)$：输出相对输入在时间上的偏移）
- This allows us to predict the circuit's response to any sinusoidal input—which is incredibly powerful because any signal can be decomposed into sinusoids (Fourier analysis)!
  （这样就能预测电路对任意正弦输入的响应——这非常强大，因为任何信号都可分解为一系列正弦波（傅里叶分析）！）

---

>相量表示

**Introduction to Phasor Notation**（**相量表示简介**）

In electrical engineering, we often represent sinusoidal signals as phasors—complex numbers that encode both amplitude and phase information:
（电气工程中常把正弦信号表示为相量——同时包含幅度与相位信息的复数：）

$$
A\angle\theta = Ae^{j\theta} = A(\cos\theta + j\sin\theta)
$$

where $A$ is the magnitude and $\theta$ is the phase angle.
（其中 $A$ 为幅度，$\theta$ 为相角。）

This notation is extremely useful because:
（这种表示非常有用，因为：）

- It compactly represents both amplitude and phase
  （可紧凑地同时表示幅度与相位）
- Complex arithmetic naturally handles phase shifts
  （复数运算自然处理相移）
- Multiplication/division of phasors corresponds to scaling and phase shifting
  （相量的乘除对应幅度的缩放与相位移动）

---

>运行 MATLAB

**MATLAB Code:**（**MATLAB 代码：**）

```matlab
>> omega = 4000;
>> T = 1/(1+4000/(j*omega));
>> abs(T)
>> angle(T)*180/pi
```

**Explanation of each line:**（**逐行说明：**）

- `omega = 4000`: Sets the frequency to 4000 rad/s (the cutoff frequency!)
  （`omega = 4000`：设定频率为 4000 rad/s（即截止频率！））
- `T = 1/(1+4000/(j*omega))`: Evaluates $T(j\omega) = \dfrac{s/\omega_c}{1+s/\omega_c}$, $s = j\omega$, as a complex number
  （`T = 1/(1+4000/(j*omega))`：把 $T(j\omega) = \dfrac{s/\omega_c}{1+s/\omega_c}$（$s = j\omega$）作为复数计算）
- `abs(T)`: Returns the magnitude $|T(j\omega)|$
  （`abs(T)`：返回模 $|T(j\omega)|$）
- `angle(T)*180/pi`: Returns the phase angle in degrees
  （`angle(T)*180/pi`：返回以度表示的相角）

---

>公式与在 $\omega=4000$ 处的解析计算

**Analytical Derivation:**（**解析推导：**）

Let's verify the MATLAB results by calculating them analytically.
（下面用解析计算来验证 MATLAB 结果。）

The transfer function is:
（传递函数为：）

$$
T(j\omega) = \frac{j\omega/4000}{1 + j\omega/4000} = \frac{j\omega}{4000 + j\omega}
$$

**At $\omega = 4000$ rad/s (cutoff frequency):**（**在 $\omega = 4000$ rad/s（截止频率）处：**）

$$
T(j4000) = \frac{j(4000)}{4000 + j(4000)} = \frac{j4000}{4000(1 + j)} = \frac{j}{1 + j} \tag{11}
$$

To find magnitude and phase, multiply by the complex conjugate:
（求幅度与相位时，乘以共轭复数：）

$$
T(j4000) = \frac{j}{1 + j} \cdot \frac{1 - j}{1 - j} = \frac{j(1 - j)}{(1 + j)(1 - j)} = \frac{j - j^2}{1 - j^2}
$$

$$
= \frac{j + 1}{1 + 1} = \frac{1 + j}{2} \tag{12}
$$

- Magnitude: $|T(j4000)| = \sqrt{(1/2)^2 + (1/2)^2} = \sqrt{1/4 + 1/4} = \sqrt{1/2} = \frac{1}{\sqrt{2}} \approx 0.7071$
  （幅度：$|T(j4000)| = \sqrt{(1/2)^2 + (1/2)^2} = \sqrt{1/4 + 1/4} = \sqrt{1/2} = \frac{1}{\sqrt{2}} \approx 0.7071$）
- Phase: $\angle T(j4000) = \arctan(1/1) = 45^\circ$
  （相位：$\angle T(j4000) = \arctan(1/1) = 45^\circ$）
- Result: $T(j4000) = 0.7071\angle 45^\circ$
  （结果：$T(j4000) = 0.7071\angle 45^\circ$）

---

>在 $\omega=800$ 处的计算

**At $\omega = 800$ rad/s (low frequency):**（**在 $\omega = 800$ rad/s（低频）处：**）

$$
T(j800) = \frac{j(800)}{4000 + j(800)} = \frac{j800}{4000 + j800} \tag{13}
$$

- Magnitude: $|T(j800)| = \dfrac{800}{\sqrt{4000^2 + 800^2}} = \dfrac{800}{\sqrt{16,640,000}} = \dfrac{800}{4078.3} \approx 0.1961$
  （幅度：$|T(j800)| = \dfrac{800}{\sqrt{4000^2 + 800^2}} = \dfrac{800}{\sqrt{16,640,000}} = \dfrac{800}{4078.3} \approx 0.1961$）
- Phase: $\angle T(j800) = 90^\circ - \arctan(800/4000) = 90^\circ - 11.31^\circ = 78.69^\circ$
  （相位：$\angle T(j800) = 90^\circ - \arctan(800/4000) = 90^\circ - 11.31^\circ = 78.69^\circ$）
- Result: $T(j800) = 0.1961\angle 78.69^\circ$
  （结果：$T(j800) = 0.1961\angle 78.69^\circ$）

---

>在 $\omega=20{,}000$ 处的计算

**At $\omega = 20,000$ rad/s (high frequency):**（**在 $\omega = 20,000$ rad/s（高频）处：**）

$$
T(j20,000) = \frac{j(20,000)}{4000 + j(20,000)} \tag{14}
$$

- Magnitude: $|T(j20,000)| = \dfrac{20,000}{\sqrt{4000^2 + 20,000^2}} = \dfrac{20,000}{\sqrt{416,000,000}} = \dfrac{20,000}{20,396} \approx 0.9806$
  （幅度：$|T(j20,000)| = \dfrac{20,000}{\sqrt{4000^2 + 20,000^2}} = \dfrac{20,000}{\sqrt{416,000,000}} = \dfrac{20,000}{20,396} \approx 0.9806$）
- Phase: $\angle T(j20,000) = 90^\circ - \arctan(20,000/4000) = 90^\circ - 78.69^\circ = 11.31^\circ$
  （相位：$\angle T(j20,000) = 90^\circ - \arctan(20,000/4000) = 90^\circ - 78.69^\circ = 11.31^\circ$）
- Result: $T(j20,000) = 0.9806\angle 11.31^\circ$
  （结果：$T(j20,000) = 0.9806\angle 11.31^\circ$）

---

>记录结果

**Summary of Results:**（**结果汇总：**）

$$
T(j4000) = 0.7071\angle 45^\circ \quad \text{(at cutoff: $-3$ dB)} \tag{15}
$$

$$
T(j800) = 0.1961\angle 78.69^\circ \quad \text{(low freq: attenuated)} \tag{16}
$$

$$
T(j20000) = 0.9806\angle 11.31^\circ \quad \text{(high freq: passes through)} \tag{17}
$$

**Interpreting the results:**（**结果解读：**）

These numbers confirm the high-pass filter behavior:
（这些数值证实了高通滤波器的行为：）

- Low frequency (800 rad/s): Gain is only 0.196 (≈20%)—most of the signal is blocked
  （低频（800 rad/s）：增益仅 0.196（≈20%）——大部分信号被阻挡）
- Cutoff frequency (4000 rad/s): Gain is 0.707 (≈71%)—the $-3$ dB point
  （截止频率（4000 rad/s）：增益 0.707（≈71%）——即 $-3$ dB 点）
- High frequency (20,000 rad/s): Gain is 0.981 (≈98%)—signal passes almost unchanged
  （高频（20,000 rad/s）：增益 0.981（≈98%）——信号几乎无变化地通过）

The phase shifts also decrease as frequency increases, which is characteristic of a high-pass filter.
（相移也随频率升高而减小，这是高通滤波器的特征。）

Now we'll use these results in Part D to find the actual time-domain output signals!
（下面在 D 部分用这些结果求出实际的时域输出信号！）

---

#### 2.4 Part D: Converting Back to Time-Domain Signals（D 部分：还原为时域信号）

This is where everything comes together!
（到这里各部分就汇合起来了！）

We're going to use our transfer function analysis from Part C to predict the actual output voltage waveforms in the time domain—the signals you would see on an oscilloscope.
（我们将用 C 部分的传递函数分析，预测时域中实际的输出电压波形——也就是示波器上看到的信号。）

**The Big Picture: Why Sinusoids are Special**（**整体思路：正弦波为何特殊**）

Here's something fascinating: sinusoidal signals are **the only signals** that maintain their shape when passed through a linear circuit—only their amplitude and phase change!
（有一个有趣的事实：正弦信号是**唯一**经过线性电路后仍保持形状的信号——改变的只有幅度与相位！）

This is why we analyze circuits using sinusoidal inputs:
（这正是我们用正弦输入分析电路的原因：）

- A sinusoidal input produces a sinusoidal output at the **same frequency**
  （正弦输入产生**同频率**的正弦输出）
- The output amplitude is scaled by the magnitude $|T(j\omega)|$
  （输出幅度按模 $|T(j\omega)|$ 缩放）
- The output is time-shifted according to the phase $\angle T(j\omega)$
  （输出按相位 $\angle T(j\omega)$ 在时间上偏移）
- Any complex signal can be broken down into sinusoids (Fourier analysis), so understanding sinusoidal response tells us everything!
  （任何复杂信号都可分解为正弦波（傅里叶分析），因此理解正弦响应就掌握了一切！）

---

>时域输出公式

**The Time-Domain Formula**（**时域公式**）

Given an input signal:
（给定输入信号：）

$$
v_i(t) = A_{in} \cos(\omega t)
$$

The steady-state output is:
（稳态输出为：）

$$
v_o(t) = |T(j\omega)| \cdot A_{in} \cos(\omega t + \angle T(j\omega))
$$

where:
（其中：）

- $|T(j\omega)|$ scales the input amplitude
  （$|T(j\omega)|$ 对输入幅度进行缩放）
- $\angle T(j\omega)$ shifts the waveform in time (phase shift)
  （$\angle T(j\omega)$ 使波形在时间上偏移（相移））

---

>在三个频率处写 $v_o(t)$

**Applying This to Our Problem**（**应用到本题**）

We have $v_i(t) = 500 \cos(\omega t)$ with $A_{in} = 500$ mV.
（本题 $v_i(t) = 500 \cos(\omega t)$，$A_{in} = 500$ mV。）

Using the results from Part C:
（利用 C 部分的结果：）

**At $\omega = 4000$ rad/s (cutoff frequency):**（**在 $\omega = 4000$ rad/s（截止频率）处：**）

From Part C: $T(j4000) = 0.7071\angle 45^\circ$
（由 C 部分：$T(j4000) = 0.7071\angle 45^\circ$）

$$
v_o(t) = (0.7071)(500) \cos(4000t + 45^\circ) = 353.55 \cos(4000t + 45^\circ)\ \mathrm{mV} \tag{18}
$$

Interpretation: The output amplitude is 353.55 mV (70.7% of input), and the output leads the input by $45^\circ$ (or about 196 µs at this frequency).
（解读：输出幅度为 353.55 mV（输入的 70.7%），输出超前输入 $45^\circ$（在该频率下约 196 µs）。）

---

**At $\omega = 800$ rad/s (low frequency):**（**在 $\omega = 800$ rad/s（低频）处：**）

From Part C: $T(j800) = 0.1961\angle 78.69^\circ$
（由 C 部分：$T(j800) = 0.1961\angle 78.69^\circ$）

$$
v_o(t) = (0.1961)(500) \cos(800t + 78.69^\circ) = 98.05 \cos(800t + 78.69^\circ)\ \mathrm{mV} \tag{19}
$$

Interpretation: The output amplitude is only 98.05 mV (19.6% of input)—the low-frequency signal is heavily attenuated!
（解读：输出幅度仅 98.05 mV（输入的 19.6%）——低频信号被大幅衰减！）

The phase lead is $78.69^\circ$.
（相位超前 $78.69^\circ$。）

---

**At $\omega = 20,000$ rad/s (high frequency):**（**在 $\omega = 20,000$ rad/s（高频）处：**）

From Part C: $T(j20,000) = 0.9806\angle 11.31^\circ$
（由 C 部分：$T(j20,000) = 0.9806\angle 11.31^\circ$）

$$
v_o(t) = (0.9806)(500) \cos(20000t + 11.31^\circ) = 490.3 \cos(20000t + 11.31^\circ)\ \mathrm{mV} \tag{20}
$$

Interpretation: The output amplitude is 490.3 mV (98.1% of input)—the high-frequency signal passes through almost unchanged!
（解读：输出幅度为 490.3 mV（输入的 98.1%）——高频信号几乎无变化地通过！）

The phase lead is only $11.31^\circ$.
（相位仅超前 $11.31^\circ$。）

---

>结果对比与结论

**How is the High-Pass Behavior Evident?**（**高通特性如何体现？**）

Looking at these three results side-by-side makes the high-pass filter behavior crystal clear:
（把三个结果并排比较，高通滤波器的特性一目了然：）

| 频率 Frequency | 输入幅值 Amplitude In | 输出幅值 Amplitude Out | 衰减 Attenuation |
|---|---|---|---|
| 800 rad/s（低频） | 500 mV | 98.1 mV | 80.4% 被阻挡 |
| 4000 rad/s（截止） | 500 mV | 353.6 mV | 29.3% 被阻挡 |
| 20,000 rad/s（高频） | 500 mV | 490.3 mV | 1.9% 被阻挡 |

The trend is unmistakable:
（趋势非常明显：）

- **Low frequencies are strongly attenuated** (only 19.6% passes through)
  （**低频被强烈衰减**（仅 19.6% 通过））
- **High frequencies pass almost unaffected** (98.1% passes through)
  （**高频几乎不受影响地通过**（98.1% 通过））
- **The cutoff frequency marks the transition** (70.7% passes, the $-3$ dB point)
  （**截止频率标出过渡点**（70.7% 通过，即 $-3$ dB 点））

This is precisely what we expect from a high-pass filter!
（这正是我们对高通滤波器的预期！）

The circuit acts like a frequency-dependent "gate" that opens wider as frequency increases.
（该电路就像一个随频率升高而开得更大的“闸门”。）

**Phase Behavior:**（**相位特性：**）

Notice also that the phase shift decreases from $78.69^\circ$ at low frequency to $11.31^\circ$ at high frequency, approaching $0^\circ$ asymptotically.
（另注意相移从低频的 $78.69^\circ$ 减小到高频的 $11.31^\circ$，并渐近趋于 $0^\circ$。）

This gradual phase transition is also characteristic of first-order high-pass filters.
（这种渐变的相位过渡也是一阶高通滤波器的特征。）

---

