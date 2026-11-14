# ELEC2104/9704 Tutorial 8 Solutions (2025)

## 1 Question 1（第 1 题）

Find the Q-point for the circuit in the figure below for（求下图电路的 Q 点，分别取：）

(a) $\beta_F = 40$

(b) $\beta_F = 120$

(c) $\beta_F = 250$

(d) $\beta_F = \infty$

(e) Find the Q-point in part (a) using the numerical iteration method if $I_S = 0.5$ fA and $V_T = 25.8$ mV.（若 $I_S=0.5$ fA、$V_T=25.8$ mV，用数值迭代法求 (a) 中的 Q 点。）

(f) Find the Q-point in part (c) using the numerical iteration method if $I_S = 0.5$ fA and $V_T = 25.8$ mV.（若 $I_S=0.5$ fA、$V_T=25.8$ mV，用数值迭代法求 (c) 中的 Q 点。）

![](Pasted%20image%2020261114214358.png)
> 图Q1-1 题 1 电路：$+9$ V（$V_{CC}$）经 $1.5$ k$\Omega$（$R_C$）到集电极，集电极再经 $10$ k$\Omega$（$R_B$）接基极，发射极接地；电流 $I_X$ 由 $R_C$ 流入集电极节点，$I_C$ 流入集电极，$I_B$ 由基极流出，$I_E$ 由发射极流出

**Solution:**（**解答：**）

First, we write the emitter current as the sum of base and collector currents.（首先，把发射极电流写成基极电流与集电极电流之和。）

Also, from KCL, we notice $I_X$ is also the sum of base and collector currents.（另外，由 KCL 可知 $I_X$ 也是基极电流与集电极电流之和。）

$$
I_X = I_E = I_B + I_C \tag{1}
$$

Applying KVL around the loop including voltage source $V_{CC}$, collector resistor $R_C = 1.5$ k$\Omega$, base resistor $R_B = 10$ k$\Omega$, and base-emitter $V_{BE}$, we can write the equation:（对包含电源 $V_{CC}$、集电极电阻 $R_C=1.5$ kΩ、基极电阻 $R_B=10$ kΩ 和基极-发射极 $V_{BE}$ 的回路应用 KVL，可得：）

$$
V_{CC} - 1500 I_X - 10\,000 I_B - V_{BE} = 0 \tag{2}
$$

From the property of BJT, we can relate collector current to base current using current gain:（由 BJT 的特性，可用电流增益把集电极电流与基极电流联系起来：）

$$
I_C = \beta_F I_B \tag{3}
$$

Then, we substitute $I_X = I_B + I_C = (1 + \beta_F)I_B$ into the KVL equation, we can solve for the base current.（然后把 $I_X=I_B+I_C=(1+\beta_F)I_B$ 代入 KVL 方程，可解出基极电流。）

$$
V_{CC} - 1500(1 + \beta_F)I_B - 10\,000 I_B - V_{BE} = 0 \tag{4}
$$

$$
I_B = \frac{V_{CC} - V_{BE}}{1500(1 + \beta_F) + 10\,000} \tag{5}
$$

Finally, we write the expression for the collector current is a function of the using the current gain.（最后，用电流增益写出集电极电流的表达式。）

We can find the collector current is a function of $\beta_F$, which is useful for part A, B, C, D.（可以看出集电极电流是 $\beta_F$ 的函数，这对 A、B、C、D 部分都适用。）

$$
I_C = \beta_F I_B = \frac{\beta(V_{CC} - V_{BE})}{1500(1 + \beta_F) + 10\,000} \tag{6}
$$

### 1.1 Part A（A 部分）

Substitute $\beta_F = 40$ into the collector current expression:（把 $\beta_F=40$ 代入集电极电流表达式：）

$$
I_C = \frac{\beta_F(V_{CC} - V_{BE})}{1500(1 + \beta_F) + 10\,000} = \frac{40(9 - 0.7)}{1500(1 + 40) + 10\,000} = 4.64\ \text{mA} \tag{7}
$$

Next, compute the collector–emitter voltage.（接下来计算集电极-发射极电压。）

Since $V_E = 0$, we have:（由于 $V_E=0$，有：）

$$
V_{CE} = V_C - V_E = V_C = 9 - 1500 I_X\left(1 + \frac{1}{\beta_F}\right) = 1.87\ \text{V} \tag{8}
$$

Where we used KVL to get $V_C = V_{CC} - 1.5$ k$\Omega \cdot I_X$ and (1) and (3) give $I_X = I_E = I_C\left(1 + \frac{1}{\beta_F}\right)$.（其中用 KVL 得 $V_C=V_{CC}-1.5$ kΩ$\cdot I_X$，并由 (1)、(3) 得 $I_X=I_E=I_C\left(1+\frac{1}{\beta_F}\right)$。）

Therefore, the Q-point of the transistor is:（因此，该晶体管的 Q 点为：）

$$
Q = (I_C, V_{CE}) = (4.64\ \text{mA}, 1.87\ \text{V}) \tag{9}
$$

### 1.2 Part B（B 部分）

Take $\beta_F = 120$.（取 $\beta_F=120$。）

The collector current is（集电极电流为）

$$
I_C = \frac{\beta_F(V_{CC} - V_{BE})}{1500(1 + \beta_F) + 10\,000} = \frac{120(9 - 0.7)}{1500(1 + 120) + 10\,000} = 5.2\ \text{mA} \tag{10}
$$

The collector–emitter voltage is（集电极-发射极电压为）

$$
V_{CE} = 9 - 1500 I_C\left(1 + \frac{1}{\beta_F}\right) - 0 = 1.14\ \text{V} \tag{11}
$$

Thus, the Q-point is（因此，Q 点为）

$$
Q = (I_C, V_{CE}) = (5.2\ \text{mA}, 1.14\ \text{V}) \tag{12}
$$

### 1.3 Part C（C 部分）

Take $\beta_F = 250$.（取 $\beta_F=250$。）

The collector current is（集电极电流为）

$$
I_C = \frac{250(9 - 0.7)}{1500(1 + 250) + 10\,000} = 5.37\ \text{mA} \tag{13}
$$

The collector–emitter voltage is（集电极-发射极电压为）

$$
V_{CE} = 9 - 1500 I_C\left(1 + \frac{1}{\beta_F}\right) - 0 = 0.91\ \text{V} \tag{14}
$$

Thus, the Q-point is（因此，Q 点为）

$$
Q = (I_C, V_{CE}) = (5.37\ \text{mA}, 0.91\ \text{V}) \tag{15}
$$

### 1.4 Part D（D 部分）

Take $\beta_F = \infty$.（取 $\beta_F=\infty$。）

Then（于是）

$$
I_C = \frac{\infty(9 - 0.7)}{1500(1 + \infty) + 10\,000} = \frac{9 - 0.7}{1500} = 5.53\ \text{mA} \tag{16}
$$

The collector–emitter voltage is（集电极-发射极电压为）

$$
V_{CE} = 9 - 1500 I_C\left(1 + \frac{1}{\infty}\right) - 0 = 0.705\ \text{V} \tag{17}
$$

Thus, the Q-point is（因此，Q 点为）

$$
Q = (I_C, V_{CE}) = (5.53\ \text{mA}, 0.705\ \text{V}) \tag{18}
$$

### 1.5 Part E（E 部分）

The collector current is expressed by the exponential model:（集电极电流用指数模型表示：）

$$
I_C = I_S \exp\left(\frac{V_{BE}}{V_T}\right) \tag{19}
$$

Thus, the first expression for $V_{BE}$ is（由此得到 $V_{BE}$ 的第一个表达式：）

$$
V_{BE1} = V_T \ln\left(\frac{I_C}{I_S}\right) \tag{20}
$$

Apply KVL to the circuit, we get the second expression for $V_{BE}$ is（对电路应用 KVL，得到 $V_{BE}$ 的第二个表达式：）

$$
V_{BE2} = 9 - 1500 \times (I_C + I_B) - 10\,000 \times (I_B) = 9 - 1500\left(1 + \frac{1}{\beta_F}\right)I_C - 10\,000\frac{I_C}{\beta_F} \tag{21}
$$

Now we construct the function（构造函数）

$$
f(I_C) = V_{BE1} - V_{BE2} = V_T \ln\left(\frac{I_C}{I_S}\right) - \left[9 - 1500\left(1 + \frac{1}{\beta_F}\right)I_C - 10\,000\frac{I_C}{\beta_F}\right] \tag{22}
$$

The derivative of the function is（该函数的导数为）

$$
f'(I_C) = \frac{V_T}{I_C} + 1500\left(1 + \frac{1}{\beta_F}\right) + 10\,000 \cdot \frac{1}{\beta_F} \tag{23}
$$

Newton's iteration formula is（牛顿迭代公式为）

$$
I_C^{(n+1)} = I_C^{(n)} - \frac{f\left(I_C^{(n)}\right)}{f'\left(I_C^{(n)}\right)} \tag{24}
$$

For $\beta_F = 40$, after several iterations, we can solve（对 $\beta_F=40$，经若干次迭代可解得）

$$
I_C \approx 4.60\ \text{mA} \tag{25}
$$

Thus, the Q-point is（因此，Q 点为）

$$
Q = (I_C, V_{CE}) = (4.6\ \text{mA}, 1.92\ \text{V}) \tag{26}
$$

### 1.6 Part F（F 部分）

Using the same working procedure as part E, we take $\beta_F = 250$, we iterate the equation (45) for several iterations than we can get（采用与 E 部分相同的步骤，取 $\beta_F=250$，对方程 (45) 迭代若干次可得）

$$
I_C \approx 5.32\ \text{mA} \tag{27}
$$

Thus, the Q-point is（因此，Q 点为）

$$
Q = (I_C, V_{CE}) = (5.32\ \text{mA}, 0.987\ \text{V}) \tag{28}
$$

## 2 Question 2（第 2 题）

Design the bias circuit in the figure below to give a Q-point of $I_C = 10$ mA and $V_{EC} = 3$ V if the transistor current gain $\beta_F = 60$.（设计下图偏置电路，使晶体管电流增益 $\beta_F=60$ 时 Q 点为 $I_C=10$ mA、$V_{EC}=3$ V。）

What is the Q-point if the current gain of the transistor is actually 40?（若晶体管电流增益实际为 40，Q 点是多少？）

![](Pasted%20image%2020261114214416.png)
> 图Q2-1 题 2 的 PNP 偏置电路：$+5$ V 接发射极（$I_E$ 流入），集电极经 $R_B$ 回到基极（$I_B$ 由基极流出），集电极节点经 $I_X$ 流入 $R_C$，$R_C$ 下端接 $-5$ V

**Solution:**（**解答：**）

### 2.1 Part A（A 部分）

**Note that PNP type BJT! The current directions and voltage polarities are flipped (vs. NPN BJT).**（**注意这是 PNP 型 BJT！电流方向与电压极性与 NPN 相反。**）

The base current is obtained from the given collector current using $I_C = 10$ mA and $\beta_F = 60$:（由给定集电极电流 $I_C=10$ mA、$\beta_F=60$ 求基极电流：）

$$
I_B = \frac{I_C}{\beta_F} = \frac{10\ \text{mA}}{60} = 0.167\ \text{mA} \tag{1}
$$

The emitter-collector (PNP) voltage is specified as $V_{EC} = 3$ V.（PNP 管的发射极-集电极电压给定为 $V_{EC}=3$ V。）

Ohm's Law across the resistor $R_C$ gives (note the negative voltage source $V_{CC} = -5$ V):（对电阻 $R_C$ 应用欧姆定律（注意电源为负电压 $V_{CC}=-5$ V）：）

$$
\frac{V_C - (-5\ \text{V})}{R_C} = I_X
$$

$$
R_C = \frac{V_C + 5\ \text{V}}{I_X} \tag{2}
$$

By KVL, $V_C = 5\ \text{V} - V_{EC}$, which includes $V_{EE} = +5$ V, the voltage source at the top of the circuit.（由 KVL，$V_C=5\ \text{V}-V_{EC}$，其中已计入电路顶部的电源 $V_{EE}=+5$ V。）

Since the question states $V_{EC} = 3$ V, we then have $V_C = 5\ \text{V} - 3\ \text{V} = 2$ V.（由于题目给定 $V_{EC}=3$ V，于是 $V_C=5-3=2$ V。）

Thus, our expression for $R_C$ becomes:（因此 $R_C$ 的表达式变为：）

$$
R_C = \frac{2\ \text{V} + 5\ \text{V}}{I_X} = \frac{7\ \text{V}}{I_X} \tag{3}
$$

Now, by KCL, $I_X = I_C + I_B$, which are all known quantities.（再由 KCL，$I_X=I_C+I_B$，各量均已知。）

Thus, we can solve for $R_C$:（因此可解出 $R_C$：）

$$
R_C = \frac{7\ \text{V}}{(0.01 + 0.000167)\ \text{A}} = 688.5\ \Omega \tag{4}
$$

Since this is design task, we need to pick a existing resistor value in real life, so we choose $R_C = 680\ \Omega$.（由于这是设计任务，需选取实际存在的电阻值，故取 $R_C=680\ \Omega$。）

To choose the base resistor, make the assumption that the BJT is on, so $V_{EB} \approx 0.7$ V.（选择基极电阻时，假设 BJT 导通，即 $V_{EB}\approx0.7$ V。）

Using Ohm's Law and the fact from KVL that $V_{BC} = V_{EC} - V_{EB}$:（利用欧姆定律及由 KVL 得到的 $V_{BC}=V_{EC}-V_{EB}$：）

$$
R_B = \frac{V_{BC}}{I_B}
$$

$$
= \frac{V_{EC} - V_{EB}}{I_B} \tag{5}
$$

$$
= \frac{3\ \text{V} - 0.7\ \text{V}}{0.167\ \text{mA}}
$$

$$
= 13.77\ \text{k}\Omega
$$

Again, since this is design task, we need to pick a existing resistor value in real life, so we choose $R_B = 14\ \Omega$.（同样是设计任务，需选取实际电阻值，故取 $R_B=14\ \Omega$。）

### 2.2 Part B（B 部分）

Now we apply the design choices $R_B = 14$ k$\Omega$, $R_C = 680\ \Omega$, and take $\beta_F = 40$.（现在采用设计值 $R_B=14$ kΩ、$R_C=680$ $\Omega$，并取 $\beta_F=40$。）

Applying KVL from the top $+5$ V voltage source, through the base $V_{EB}$ and base resistor $R_B$, down through the $R_C$ resistor to the bottom negative voltage source $-5$ V:（从顶部 $+5$ V 电源出发，经基极 $V_{EB}$、基极电阻 $R_B$，再经 $R_C$ 到底部 $-5$ V 电源，应用 KVL：）

$$
5\ \text{V} - V_{EB} - R_B I_B - R_C I_X - (-5\ \text{V}) = 0 \tag{6}
$$

Note the $V_{EB}$ voltage polarity for the PNP.（注意 PNP 管 $V_{EB}$ 的极性。）

Also note that (KCL) $I_X = I_B + I_C = (1 + \beta_F)I_B$.（另由 KCL，$I_X=I_B+I_C=(1+\beta_F)I_B$。）

Substituting $V_{BE} \approx 0.7$ V, we solve for base current:（代入 $V_{BE}\approx0.7$ V，解出基极电流：）

$$
5\ \text{V} - 0.7\ \text{V} - 14\ \text{k}\Omega I_B - 680\ \Omega(1 + 40)I_B + 5\ \text{V} = 0
$$

$$
(41\,880\ \Omega)I_B = 9.3\ \text{V} \tag{7}
$$

$$
I_B = 222.1\ \mu\text{A}
$$

Then, we determine the collector current.（然后确定集电极电流。）

$$
I_C = \beta_F I_B = 40 \cdot 222.1\ \mu\text{A} = 8.88\ \text{mA} \tag{8}
$$

Next, we can determine the collector–emitter voltage using（接下来可求集电极-发射极电压，使用）

$$
V_{EC} = V_E - V_C = 5\ \text{V} - \left[R_C(1 + \beta_F)I_B + (-5)\right] = 3.81\ \text{V} \tag{9}
$$

Where in the above we used KVL ($V_C - R_C I_X = -5$ V) and KCL ($I_X = I_B + I_C = (1 + \beta_F)I_B$).（其中用到 KVL（$V_C-R_CI_X=-5$ V）和 KCL（$I_X=I_B+I_C=(1+\beta_F)I_B$）。）

Therefore, the Q-point is（因此，Q 点为）

$$
Q = (I_C, V_{EC}) = (8.88\ \text{mA}, 3.81\ \text{V}) \tag{10}
$$

## 3 Question 3（第 3 题）

Design the Common-Emitter amplification stage of Fig. 5.161 for a power budget of 1 mW and a voltage gain of 20.（为图 5.161 的共射放大级设计电路，要求功耗预算 1 mW、电压增益 20。）

Assume $\beta = 100$, $V_T = 26$ mV, and $I_s = 6 \times 10^{-16}$ A.（假设 $\beta=100$、$V_T=26$ mV、$I_s=6\times10^{-16}$ A。）

![](Pasted%20image%2020261114214432.png)
> 图Q3-1 题 3 的共射放大电路（Fig. 5.161）：$V_{CC} = 2.5$ V 经 $R_B$ 接基极、经 $R_C$ 接集电极，$V_{in}$ 接基极，$V_{out}$ 取自集电极，$Q_1$ 发射极接地

**Solution:**（**解答：**）

The total power dissipated is written below.（总功耗如下式。）

Since $I_B$ is very small compared to $I_C$, we ignore $I_B$.（由于 $I_B$ 远小于 $I_C$，可忽略 $I_B$。）

$$
P = V_{CC} \cdot I_{\text{total}} = V_{CC} \cdot (I_B + I_C) \approx V_{CC} \cdot I_C \tag{1}
$$

Thus, rearranging (1), we can solve the collector current.（因此重排 (1)，可解出集电极电流。）

$$
I_C = \frac{P}{V_{CC}} = \frac{1\ \text{mW}}{2.5\ \text{V}} = 0.4\ \text{mA} \tag{2}
$$

For the voltage gain, we start from drawing the small signal circuit diagram.（求电压增益，先画小信号等效电路。）

Since the early effect is not mentioned, $r_o$ is $\infty$.（题目未提厄利效应，故 $r_o=\infty$。）

![](Pasted%20image%2020261114214511.png)
> 图Q3-2 题 3 的小信号等效电路（手绘）：B–E 间为 $r_\pi$（$v_\pi$ 标示于 $r_\pi$ 上，B 端接 $V_{in}$），C–E 间为 $g_mv_\pi$ 受控源与 $r_o$，$R_C$ 接在 C 与地之间，$V_{out}$ 取自集电极

According to the circuit diagram, we can write the expression for the voltage gain $A_v$.（根据电路图，可写出电压增益 $A_v$ 的表达式。）

$$
A_V = \frac{v_{out}}{v_{in}} = \frac{-g_m v_\pi R_C}{v_\pi} = -g_m R_C = -\frac{I_C}{V_T}R_C \tag{3}
$$

Since $A_v$, $I_C$ and $V_T$, we can rearrange (3) and solve for $R_C$:（已知 $A_v$、$I_C$、$V_T$，重排 (3) 可解出 $R_C$：）

$$
R_C = \left|\frac{A_V V_T}{I_C}\right| = \left|\frac{-20 \cdot 0.026}{0.4 \times 10^{-3}}\right| = 1300\ \Omega \tag{4}
$$

For the design problem, $R_C = 1300\ \Omega$ is possible.（设计上取 $R_C=1300\ \Omega$ 是可行的。）

Now applying KVL at the input loop, we can write（现在对输入回路应用 KVL，可得）

$$
V_{CC} - I_B R_B - V_{BE} = 0 \tag{5}
$$

Since $I_B = I_C/\beta_F$ and $V_{BE} = V_T \ln(I_C/I_S)$, this gives:（由于 $I_B=I_C/\beta_F$、$V_{BE}=V_T\ln(I_C/I_S)$，于是：）

$$
V_{CC} - \frac{I_C}{\beta_F}R_B - V_T \ln\left(\frac{I_C}{I_S}\right) = 0 \tag{6}
$$

Substitute $V_{CC} = 2.5$ V, $V_T = 0.026$ V, $I_C = 0.4$ mA, and $I_S = 6 \times 10^{-16}$ A:（代入 $V_{CC}=2.5$ V、$V_T=0.026$ V、$I_C=0.4$ mA、$I_S=6\times10^{-16}$ A：）

$$
2.5 - \frac{I_C}{\beta_F}R_B - (0.026)\ln\left(\frac{I_C}{6 \times 10^{-16}}\right) = 0 \tag{7}
$$

Solving for $R_B$ gives（解出 $R_B$ 得）

$$
R_B = 448\ \text{k}\Omega \tag{8}
$$

For the design problem, $R_B = 448$ k$\Omega$ is possible.（设计上取 $R_B=448$ kΩ 是可行的。）

## 4 Question 4（第 4 题）

Find the region of operation and drain current in an NMOS transistor with $\mu_n C_{ox} = 200$ $\mu$A/V$^2$, $W/L = 10/1$, and $V_{TN} = 0.75$ V for:（求下列条件下 NMOS 晶体管的工作区与漏极电流，已知 $\mu_nC_{ox}=200$ μA/V²、$W/L=10/1$、$V_{TN}=0.75$ V：）

(a) $V_{GS} = 2$ V and $V_{DS} = 2.5$ V,（$V_{GS}=2$ V、$V_{DS}=2.5$ V；）

(b) $V_{GS} = 2$ V and $V_{DS} = 0.2$ V,（$V_{GS}=2$ V、$V_{DS}=0.2$ V；）

(c) $V_{GS} = 0$ V and $V_{DS} = 4$ V.（$V_{GS}=0$ V、$V_{DS}=4$ V。）

(d) Repeat parts (a)–(c) for $\mu_n C_{ox} = 300$ $\mu$A/V$^2$.（对 $\mu_nC_{ox}=300$ μA/V² 重复 (a)~(c)。）

![](Pasted%20image%2020261114214523.png)
> 图Q4-1 题 4 的 NMOS 符号（手绘）：G 为栅极、D 为漏极、S 为源极

**Solution:**（**解答：**）

The typical working procedure to solve an MOSFET problem is（求解 MOSFET 问题的一般步骤为）

1. Check operating region.（判断工作区。）
2. Calculate $I_D$ based on the region.（根据工作区计算 $I_D$。）

### 4.1 Part A（A 部分）

**Step 1. check the operating region**（**第 1 步：判断工作区**）

According to the calculation below, we can find that the NMOS operates in the saturation region.（由下列计算可知，该 NMOS 工作在饱和区。）

$$
V_{GS} - V_{TN} = 2 - 0.75 = 1.25\ \text{V} < V_{DS} = 2.5\ \text{V}
$$

**Step 2. Calculate $I_D$ based on the region.**（**第 2 步：按工作区计算 $I_D$。**）

Next we apply the formula for the saturation $I_D$.（接着代入饱和区 $I_D$ 公式。）

$$
I_D = \frac{1}{2}(\mu_n C_{ox})\left(\frac{W}{L}\right)(V_{GS} - V_{TN})^2 = \frac{1}{2}(200 \times 10^{-6})\left(\frac{10}{1}\right)(2 - 0.75)^2 = 1.56\ \text{mA} \tag{1}
$$

### 4.2 Part B（B 部分）

**Step 1. Check the operating region**（**第 1 步：判断工作区**）

We compare $V_{GS} - V_{TN}$ with $V_{DS}$:（将 $V_{GS}-V_{TN}$ 与 $V_{DS}$ 比较：）

$$
V_{GS} - V_{TN} = 1.25\ \text{V} > V_{DS} = 0.2\ \text{V}
$$

Therefore, the NMOS operates in the triode (linear) region.（因此，该 NMOS 工作在可变电阻区（线性区）。）

**Step 2. Calculate $I_D$ based on the region.**（**第 2 步：按工作区计算 $I_D$。**）

For the linear region, the drain current is（线性区的漏极电流为）

$$
I_D = (\mu_n C_{ox})\frac{W}{L}\left[\left(V_{GS} - V_{TN} - \frac{V_{DS}}{2}\right)V_{DS}\right] \tag{2}
$$

Substituting values:（代入数值：）

$$
I_D = (200 \times 10^{-6})\frac{10}{1}\left(2 - 0.75 - \frac{0.2}{2}\right)(0.2) = 0.46\ \text{mA}
$$

### 4.3 Part C（C 部分）

**Step 1. Check the operating region**（**第 1 步：判断工作区**）

We evaluate the gate-to-source condition:（考察栅源电压条件：）

$$
V_{GS} - V_{TN} = 0 - 0.75 = -0.75 < 0
$$

Thus, the NMOS is in the cutoff region.（因此该 NMOS 处于截止区。）

**Step 2. Calculate $I_D$ based on the region.**（**第 2 步：按工作区计算 $I_D$。**）

Since the device is in cutoff,（由于器件处于截止区，）

$$
I_D = 0 \tag{3}
$$

### 4.4 Part D（D 部分）

Here we consider the same NMOS configuration, but with a different mobility–oxide capacitance product ($\mu_n C_{ox}$).（这里保持 NMOS 结构不变，仅改变迁移率-氧化层电容乘积 $\mu_nC_{ox}$。）

The operating region remains the same as in parts (a)–(c), but the drain current $I_D$ will scale with ($\mu_n C_{ox}$).（工作区与 (a)~(c) 相同，但漏极电流 $I_D$ 将随 $\mu_nC_{ox}$ 成比例变化。）

**(a) Saturation Region**（(a) 饱和区）

$$
I_D \propto (\mu_n C_{ox})
$$

$$
I_D = \frac{300}{200}(1.56\ \text{mA}) = 2.34\ \text{mA} \tag{4}
$$

**(b) Triode / Linear Region**（(b) 可变电阻区／线性区）

$$
I_D \propto (\mu_n C_{ox})
$$

$$
I_D = \frac{300}{200}(0.46\ \text{mA}) = 0.96\ \text{mA} \tag{5}
$$

**(c) Cutoff Region**（(c) 截止区）

Since $V_{GS} < V_{TN}$,（由于 $V_{GS}<V_{TN}$，）

$$
I_D = 0 \tag{6}
$$

## 转换说明（非原文内容）

- 本文由 PDF 文本层与页面渲染图逐页核对后转录；公式一律改写为 LaTeX，`\tag` 沿用原文式号（第 1 题 (1)–(28)、第 2 题 (1)–(10)、第 3 题 (1)–(8)、第 4 题 (1)–(6)）。
- 所有电路图、小信号等效电路、NMOS 符号均以纯文本占位表示，未插入图像本体；原书未编号的插图统一写作 `> 图Q1-1 …` 这样的题号式编号。
- 原文笔误照录未改：第 1 题 Part F 写“we iterate the equation (45)”，该式实际为式 (24)（原文式号最多到 (28)）；第 2 题末尾“so we choose $R_B = 14\ \Omega$”，按前文计算值 13.77 kΩ 应为 14 kΩ。
- 第 4 题 Part A 的饱和电流表达式原书写作 $\frac{1}{2}(\mu_nC_{ox})(W/L)(V_{GS}-V_{TN})^2$，与正文其他处一致。
