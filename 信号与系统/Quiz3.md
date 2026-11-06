# ELEC2302/9302 Signals and Systems — Quiz 3 practice questions, answers and feedback

ELEC2302/9302《信号与系统》——测验 3 练习题、答案与反馈

**How to use this question bank:**

don't work through the questions from beginning to end.（本题库使用方法  不要从头到尾按顺序做题。）

Start by doing one question from each group, identify the areas where you are less confident, and work on those first.（先从每个题组中各做一道题，找出掌握不够牢固的部分，再优先练习这些内容。）

The correct option is marked ✓.（正确选项标有 ✓。）

---

## 1. The Laplace transform (week 8)（拉普拉斯变换，第 8 周）

Laplace transform: definition, ROC and table pairs（拉普拉斯变换：定义、收敛域与常用变换对）

---

### 1. Question 1（第 1 题）^q1

The signal（已知信号）

$$
u(t)=\left(3e^{-4t}-2e^{t}\right)H(t)
$$

What is the region of convergence of its Laplace transform?（求其拉普拉斯变换的收敛域。）

(a) $\operatorname{Re}(s)>1$ **✓**（收敛域为 $\operatorname{Re}(s)>1$）
(b) $-4<\operatorname{Re}(s)<1$（带状收敛域，是双边信号的情形）
(c) $\operatorname{Re}(s)>0$（只有阶跃 $H(t)$ 的收敛域）
(d) $\operatorname{Re}(s)>-4$（只有衰减项 $3e^{-4t}H(t)$ 的收敛域）

> [!success] Answer（答案）
> (a) $\operatorname{Re}(s)>1$

> [!abstract] 知识点讲解
> 见 [[信号与系统/Quiz对应知识点.md|Quiz对应知识点]] 7.1 定义与收敛域 与 7.2 常用变换对。
>
> - **单边指数变换对**：$\mathcal L\{e^{s_0t}H(t)\}=\dfrac{1}{s-s_0}$，收敛域 $\operatorname{Re}s>\operatorname{Re}s_0$。
> - **线性**：$\mathcal L\{a u_1+b u_2\}=aU_1(s)+bU_2(s)$，和的 ROC 至少包含各 ROC 的交集。
> - **因果信号的 ROC**：右边信号的 ROC 位于最右极点右侧，即 $\operatorname{Re}s>\max_i\operatorname{Re}p_i$。
> - **交集判据**：每一项都收敛，和才收敛；本题两个 ROC 的交集由最右边界 $\operatorname{Re}s>1$ 决定。

> [!example] 解答
> 逐项查表：
> $$\mathcal L\left\{3e^{-4t}H(t)\right\}=\frac{3}{s+4},\qquad \operatorname{Re}(s)>-4,$$
> $$\mathcal L\left\{2e^{t}H(t)\right\}=\frac{2}{s-1},\qquad \operatorname{Re}(s)>1.$$
> 由线性性，
> $$U(s)=\frac{3}{s+4}-\frac{2}{s-1}.$$
> 两个 ROC 的交集：
> $$\{\operatorname{Re}(s)>-4\}\cap\{\operatorname{Re}(s)>1\}=\{\operatorname{Re}(s)>1\}.$$
> 选项 (b) 的带状 ROC 属于双边信号；选项 (c)(d) 只考虑了其中一项，均不完整。选 (a)。

---

### 2. Question 2（第 2 题）^q2

The signal（已知信号）

$$
u(t)=e^{(-2+5j)t}H(t)
$$

has Laplace transform（的拉普拉斯变换为）

$$
U(s)=\frac{1}{s+2-5j}.
$$

What is its region of convergence?（求其收敛域。）

(a) $\operatorname{Re}(s)>5$（用虚部 $5$ 作为边界）
(b) $\operatorname{Re}(s)>-2$ **✓**（收敛域为 $\operatorname{Re}(s)>-2$）
(c) $|s|>\sqrt{29}$（以极点的模为半径的圆外区域）
(d) $\operatorname{Re}(s)>2$（把极点实部的符号弄反）

> [!success] Answer（答案）
> (b) $\operatorname{Re}(s)>-2$

> [!abstract] 知识点讲解
> 见 [[信号与系统/Quiz对应知识点.md|Quiz对应知识点]] 7.1 定义与收敛域 与 7.2 常用变换对。
>
> - **指数信号变换对**：$\mathcal L\{e^{s_0t}H(t)\}=\dfrac{1}{s-s_0}$，ROC 为 $\operatorname{Re}s>\operatorname{Re}s_0$。
> - **绝对收敛条件**：$U(s)$ 存在要求 $\displaystyle\int_0^\infty\left|e^{s_0t}e^{-\sigma t}\right|dt=\int_0^\infty e^{(\operatorname{Re}s_0-\sigma)t}dt<\infty$。
> - **虚部不影响 ROC**：$e^{j\operatorname{Im}(s_0)t}$ 的模恒为 $1$，只改变相位、不改变大小；ROC 边界是竖直线 $\sigma=\operatorname{Re}s_0$，不是圆。

> [!example] 解答
> 这里 $s_0=-2+5j$。取 $s=\sigma+j\omega$，先合并指数：
> $$u(t)e^{-st}=e^{(-2+5j)t}e^{-(\sigma+j\omega)t}
> =e^{[(-2-\sigma)+j(5-\omega)]t}.$$
> 取模时把实部和虚部分开：
> $$\begin{aligned}
> \left|u(t)e^{-st}\right|
> &=\left|e^{(-2-\sigma)t}\right|\cdot\left|e^{j(5-\omega)t}\right|\\
> &=e^{(-2-\sigma)t}\cdot1\\
> &=e^{(-2-\sigma)t}.
> \end{aligned}$$
> 
> 上式在 $t\to\infty$ 时衰减，当且仅当
> $$-2-\sigma<0\quad\Longrightarrow\quad\sigma>-2.$$
> 所以
> $$\operatorname{ROC}:\ \operatorname{Re}(s)>-2.$$
> 极点位于 $s=-2+5j$，ROC 在该极点实部的右侧。$|s|=\sqrt{(-2)^2+5^2}=\sqrt{29}$ 只是极点到原点的距离，与 ROC 边界无关。选 (b)。

---

### 3. Question 3（第 3 题）^q3

The centered pulse $p_2(t)$ is delayed by $3$ s, giving（中心在原点的宽 $2$ 脉冲 $p_2(t)$ 延迟 $3$ s，得到）

$$
u(t)=p_2(t-3).
$$

What is $U(s)$?（求 $U(s)$。）

(a) $\dfrac{e^{-s}-e^{-5s}}{s}$（脉冲落在 $1<t<5$，宽度为 $4$）
(b) $\dfrac{e^{-3s}\left(1-e^{-2s}\right)}{s}$（脉冲落在 $3<t<5$，起点在 $t=3$）
(c) $\dfrac{e^{-4s}-e^{-2s}}{s}$（脉冲符号相反）
(d) $\dfrac{e^{-2s}-e^{-4s}}{s}$ **✓**（正确的延迟脉冲变换）

> [!success] Answer（答案）
> (d) $\dfrac{e^{-2s}-e^{-4s}}{s}$

> [!abstract] 知识点讲解
> 见 [[信号与系统/Quiz对应知识点.md|Quiz对应知识点]] 7.1 定义与收敛域 与 7.3 性质（时移与阶跃延迟）。
>
> - **矩形脉冲表示**：中心在原点、宽为 $\tau$ 的脉冲 $p_\tau(t)=H\left(t+\dfrac{\tau}{2}\right)-H\left(t-\dfrac{\tau}{2}\right)$。
> - **阶跃变换对**：$\mathcal L\{H(t-\tau)\}=\dfrac{e^{-s\tau}}{s}$，$\operatorname{Re}s>0$。
> - **时移性质**：$\mathcal L\{u(t-\tau)H(t-\tau)\}=e^{-s\tau}U(s)$，延迟因子 $e^{-s\tau}$ 中的 $\tau$ 是信号起点。
> - **线性**：两个阶跃之差逐个变换后相减。

> [!example] 解答
> $p_2(t)$ 在 $|t|<1$ 内为 $1$。延迟 $3$ s 后，$p_2(t-3)$ 在
> $$|t-3|<1\quad\Longrightarrow\quad 2<t<4$$
> 内为 $1$，因此
> $$u(t)=H(t-2)-H(t-4).$$
> 逐项变换：
> $$U(s)=\frac{e^{-2s}}{s}-\frac{e^{-4s}}{s}
> =\frac{e^{-2s}-e^{-4s}}{s}.$$
> 选 (d)。

---

### 4. Question 4（第 4 题）^q4

What is the Laplace transform of（求下列信号的拉普拉斯变换）

$$
u(t)=\cos(3t)\cos(t)H(t)\ ?
$$

(a) $\dfrac12\left(\dfrac{s}{s^2+9}+\dfrac{s}{s^2+1}\right)$（把两个余弦原样相加，没有使用积化和差）
(b) $\dfrac{s^2}{(s^2+9)(s^2+1)}$（把两个变换直接相乘）
(c) $\dfrac12\left(\dfrac{s}{s^2+16}+\dfrac{s}{s^2+4}\right)$ **✓**（正确的积化和差结果）
(d) $\dfrac12\left(\dfrac{s}{s^2+16}-\dfrac{s}{s^2+4}\right)$（积化和差用了减号）

> [!success] Answer（答案）
> (c) $\dfrac12\left(\dfrac{s}{s^2+16}+\dfrac{s}{s^2+4}\right)$

> [!abstract] 知识点讲解
> 见 [[信号与系统/Quiz对应知识点.md|Quiz对应知识点]] 7.2 常用变换对（乘积信号的变换）。
>
> - **积化和差**：$\cos A\cos B=\dfrac12\left[\cos(A+B)+\cos(A-B)\right]$，两项之间是**加号**。
> - **余弦变换对**：$\mathcal L\{\cos\omega_0t\,H(t)\}=\dfrac{s}{s^2+\omega_0^2}$，$\operatorname{Re}s>0$。
> - **线性**：时域相加对应 $s$ 域相加，可逐项查表。
> - **易错点**：时域相乘 $\cos3t\cos t$ **不等于**变换相乘；后者对应时域卷积。

> [!example] 解答
> 积化和差：
> $$\cos3t\cos t=\frac12\left[\cos(3t+t)+\cos(3t-t)\right]
> =\frac12\left(\cos4t+\cos2t\right).$$
> 乘以 $H(t)$ 后逐项变换：
> $$\mathcal L\{\cos4t\,H(t)\}=\frac{s}{s^2+16},\qquad
> \mathcal L\{\cos2t\,H(t)\}=\frac{s}{s^2+4}.$$
> 所以
> $$U(s)=\frac12\left(\frac{s}{s^2+16}+\frac{s}{s^2+4}\right).$$
> 选 (c)。

---

### 5. Question 5（第 5 题）^q5

A system has transfer function（某系统的传递函数为）

$$
G(s)=5\quad\text{(a constant).}
$$

What is its impulse response $h(t)$?（求其冲激响应 $h(t)$。）

(a) $5H(t)$（把常数变换误当成 $5/s$）
(b) It has no impulse response because it is not a dynamic system.（不是动态系统，所以没有冲激响应）
(c) $5$ for all $t$（在所有时刻都等于 $5$）
(d) $5\delta(t)$ **✓**（冲激响应为 $5\delta(t)$）

> [!success] Answer（答案）
> (d) $h(t)=5\delta(t)$

> [!abstract] 知识点讲解
> 见 [[信号与系统/Quiz对应知识点.md|Quiz对应知识点]] 7.2 常用变换对 与 8.1 冲激响应与阶跃响应。
>
> - **冲激变换对**：$\mathcal L\{\delta(t)\}=1$，ROC 为整个 $s$ 平面。
> - **冲激响应的定义**：$G(s)=\mathcal L\{h(t)\}$，即 $h(t)=\mathcal L^{-1}\{G(s)\}$。
> - **线性**：$\mathcal L\{K\delta(t)\}=K$，所以常数 $G(s)=K$ 对应 $h(t)=K\delta(t)$。
> - **静态系统**：$y=h*u=K\delta*u=Ku$，纯增益系统同样有冲激响应。

> [!example] 解答
> **已知。** 传递函数为常数
> $$G(s)=5\qquad\text{（与 }s\text{ 无关）}.$$
>
> **求。** 冲激响应 $h(t)$，即满足 $G(s)=\mathcal L\{h\}(s)$ 的 $h(t)$。
>
> **解法一：用变换对直接反变换。**
> 拉普拉斯变换的冲激变换对为
> $$\mathcal L\{\delta(t)\}=\int_{0^-}^{\infty}\delta(t)e^{-st}dt=e^{-s\cdot0}=1,\qquad\text{ROC 为整个 }s\text{ 平面}.$$
> 由线性性，$K\delta(t)\leftrightarrow K\cdot1=K$。取 $K=5$：
> $$5\delta(t)\longleftrightarrow 5.$$
> 因此
> $$h(t)=\mathcal L^{-1}\{5\}=5\delta(t).$$
>
> **解法二：从 $h(t)$ 与 $G(s)$ 的定义核对。**
> 冲激响应定义为输入 $u(t)=\delta(t)$ 时的零状态输出。对 $G(s)=5$，输出变换为
> $$Y(s)=G(s)U(s)=5\cdot1=5.$$
> 反变换得
> $$y(t)=5\delta(t),$$
> 所以 $h(t)=5\delta(t)$。
>
> **校验：用卷积验证它确实是该系统。** 对任意输入 $u(t)$，
> $$\begin{aligned}
> y(t)&=h(t)*u(t)\\
> &=\int_{-\infty}^{\infty}5\delta(\tau)u(t-\tau)d\tau\\
> &=5u(t)\quad(\text{筛选性质：}\delta(\tau)\text{ 只在 }\tau=0\text{ 取值}).
> \end{aligned}$$
> 即输出等于输入的 $5$ 倍，与 $Y(s)=5U(s)$ 一致，说明 $h(t)=5\delta(t)$ 正确。
>
> **为什么其他选项不对。**
> - (a) $5H(t)$ 的变换是 $5/s$，对应 $G(s)=5/s$（一个积分器），不是 $G(s)=5$。
> - (b) 纯增益系统虽然不含储能元件，但仍是有定义的 LTI 系统，输入冲激时同样有输出 $5\delta(t)$。
> - (c) $h(t)$ 是冲激响应的波形，由变换对得到的是 $5\delta(t)$，而不是对所有 $t$ 恒为 $5$；后者在变换域里对应的是别的东西。
>
> 选 (d)。

---

### 6. Question 6（第 6 题）^q6

Write（写出）

$$
\cos(4t)H(t)=\frac12e^{4jt}H(t)+\frac12e^{-4jt}H(t)
$$

and use linearity with（并利用线性性和）

$$
\mathcal L\left\{e^{s_0t}H(t)\right\}=\frac{1}{s-s_0}.
$$

The result is（结果为）

(a) $\dfrac{4}{s^2+16}$（这是 $\sin(4t)H(t)$ 的变换）
(b) $\dfrac{1}{s^2+16}$（分子应为 $s$，不是 $1$）
(c) $\dfrac{s}{s^2+16}$ **✓**（正确结果）
(d) $\dfrac{s}{s^2-16}$（分母符号错误）

> [!success] Answer（答案）
> (c) $\dfrac{s}{s^2+16}$

> [!abstract] 知识点讲解
> 见 [[信号与系统/Quiz对应知识点.md|Quiz对应知识点]] 7.2 常用变换对。
>
> - **欧拉公式**：$\cos\theta=\dfrac{e^{j\theta}+e^{-j\theta}}{2}$，把余弦拆成两个复指数。
> - **复指数变换对**：$\mathcal L\{e^{s_0t}H(t)\}=\dfrac{1}{s-s_0}$，取 $s_0=\pm4j$。
> - **线性与通分**：$\dfrac12\left(\dfrac{1}{s-4j}+\dfrac{1}{s+4j}\right)$，分母用 $(s-4j)(s+4j)=s^2+16$。
> - **结果**：$\mathcal L\{\cos4t\,H(t)\}=\dfrac{s}{s^2+16}$。

> [!example] 解答
> 逐项变换：
> $$\mathcal L\left\{e^{4jt}H(t)\right\}=\frac{1}{s-4j},\qquad
> \mathcal L\left\{e^{-4jt}H(t)\right\}=\frac{1}{s+4j}.$$
> 由线性性，
> $$U(s)=\frac12\left(\frac{1}{s-4j}+\frac{1}{s+4j}\right).$$
> 通分：
> $$U(s)=\frac12\cdot\frac{(s+4j)+(s-4j)}{(s-4j)(s+4j)}
> =\frac12\cdot\frac{2s}{s^2+16}
> =\frac{s}{s^2+16}.$$
> 选 (c)。

---

### 7. Question 7（第 7 题）^q7

Laplace transform properties（拉普拉斯变换的性质）

Which signal has Laplace transform（哪个信号的拉普拉斯变换为）

$$
\frac{e^{-3s}}{s+1}\ ?
$$

(a) $e^{-(t+3)}H(t)$（只是把指数衰减了一个常数因子）
(b) $e^{-(t-3)}H(t-3)$ **✓**（整个信号延迟 $3$ s）
(c) $e^{-t}H(t-3)$（只延迟了阶跃，指数没有同步延迟）
(d) $e^{-(t-3)}H(t)$（只移动了指数，阶跃没有延迟）

> [!success] Answer（答案）
> (b) $e^{-(t-3)}H(t-3)$

> [!abstract] 知识点讲解
> 见 [[信号与系统/Quiz对应知识点.md|Quiz对应知识点]] 7.3 性质（时移与阶跃延迟）。
>
> - **时移性质（单边）**：若 $u(t)\leftrightarrow U(s)$，则 $u(t-\tau)H(t-\tau)\leftrightarrow e^{-s\tau}U(s)$。
> - **逆用**：频谱乘以 $e^{-s\tau}$，等价于整个波形延迟 $\tau$。
> - **基本变换对**：$\dfrac{1}{s+1}\leftrightarrow e^{-t}H(t)$。
> - **注意**：延迟必须让指数与阶跃**一起**平移，只移动其中一个会多出常数因子。

> [!example] 解答
> 已知变换对
> $$\frac{1}{s+1}\longleftrightarrow e^{-t}H(t).$$
> 由时移性质 $u(t-3)H(t-3)\leftrightarrow e^{-3s}U(s)$，得
> $$\frac{e^{-3s}}{s+1}\longleftrightarrow e^{-(t-3)}H(t-3).$$
> 检查其他选项：
> - (a) $e^{-(t+3)}H(t)=e^{-3}e^{-t}H(t)$，变换为 $\dfrac{e^{-3}}{s+1}$。
> - (c) $e^{-t}H(t-3)=e^{-3}e^{-(t-3)}H(t-3)$，变换为 $\dfrac{e^{-3}e^{-3s}}{s+1}$，多出常数 $e^{-3}$。
> - (d) $e^{-(t-3)}H(t)=e^{3}e^{-t}H(t)$，变换为 $\dfrac{e^{3}}{s+1}$。
>
> 选 (b)。

---

### 8. Question 8（第 8 题）^q8

An LTI system, initially at rest, has step response（某 LTI 系统零初始状态下的阶跃响应为）

$$
y_{\text{step}}(t)=\left(e^{-t}-e^{-2t}\right)H(t).
$$

What is its impulse response $h(t)$?（求其冲激响应 $h(t)$。）

(a) $\left(\frac12-e^{-t}+\frac12e^{-2t}\right)H(t)$（这是阶跃响应的积分）
(b) $\left(2e^{-2t}-e^{-t}\right)H(t)$ **✓**（正确的导数）
(c) $\left(e^{-t}-e^{-2t}\right)H(t)$（把阶跃响应当成了冲激响应）
(d) $\left(e^{-t}-2e^{-2t}\right)H(t)$（导数的符号弄反）

> [!success] Answer（答案）
> (b) $h(t)=\left(2e^{-2t}-e^{-t}\right)H(t)$

> [!abstract] 知识点讲解
> 见 [[信号与系统/Quiz对应知识点.md|Quiz对应知识点]] 8.1 冲激响应与阶跃响应。
>
> - **为什么能求导得到**：冲激是阶跃的导数（广义函数意义下 $\delta(t)=\dfrac{d}{dt}H(t)$）。
> - **推导**：阶跃响应记为 $s(t)=h(t)*H(t)$。两边对 $t$ 求导，并利用「卷积与求导可交换」：
>   $$s'(t)=h(t)*H'(t)=h(t)*\delta(t)=h(t).$$
>   所以 $h(t)=\dfrac{d}{dt}s(t)$。
> - **求导时的注意点**：$s(t)=f(t)H(t)$ 求导要用乘积法则
>   $$s'(t)=f'(t)H(t)+f(t)\delta(t).$$
>   若 $f(0)\ne0$，会额外产生 $f(0)\delta(t)$；本题 $f(0)=e^0-e^0=0$，冲激项消失。
> - **s 域同一条关系**：$Y_{\text{step}}(s)=\dfrac{G(s)}{s}$，即 $G(s)=sY_{\text{step}}(s)$。

> [!example] 解答
> 阶跃响应为
> $$y_{\text{step}}(t)=\left(e^{-t}-e^{-2t}\right)H(t).$$
> 按乘积法则求导，令 $f(t)=e^{-t}-e^{-2t}$：
> $$\begin{aligned}
> h(t)=\frac{d}{dt}\left[f(t)H(t)\right]
> &=f'(t)H(t)+f(t)\delta(t)\\
> &=\left(-e^{-t}+2e^{-2t}\right)H(t)+\underbrace{(1-1)}_{f(0)}\,\delta(t)\\
> &=\left(2e^{-2t}-e^{-t}\right)H(t).
> \end{aligned}$$
> 因为 $f(0)=1-1=0$，冲激项为零，所以阶跃响应是连续的、没有跳变。
>
> 用变换校验：
> $$Y_{\text{step}}(s)=\frac{1}{s+1}-\frac{1}{s+2}
> =\frac{1}{(s+1)(s+2)},$$
> $$G(s)=sY_{\text{step}}(s)=\frac{s}{(s+1)(s+2)}
> =\frac{2}{s+2}-\frac{1}{s+1},$$
> 反变换得
> $$h(t)=\left(2e^{-2t}-e^{-t}\right)H(t),$$
> 与求导结果一致。选 (b)。

---

### 9. Question 9（第 9 题）^q9

Let（令）

$$
y(t)=\left[e^{-t}H(t)\right]*\left[e^{-3t}H(t)\right].
$$

Use the Laplace transform to find $y(1)$.（用拉普拉斯变换求 $y(1)$。）

> [!success] Answer（答案）
> $y(1)=0.1590$

> [!abstract] 知识点讲解
> 见 [[信号与系统/Quiz对应知识点.md|Quiz对应知识点]] 7.3 性质（卷积）与 7.5 部分分式分解（遮盖法求单实极点）。
>
> - **卷积定理**：$y=u*v\Rightarrow Y(s)=U(s)V(s)$，即时域卷积对应 $s$ 域相乘。
> - **变换对**：$e^{-at}H(t)\leftrightarrow\dfrac{1}{s+a}$，本题 $U(s)=\dfrac1{s+1}$，$V(s)=\dfrac1{s+3}$。
> - **部分分式（遮盖法）**：$\dfrac{1}{(s+1)(s+3)}=\dfrac{A}{s+1}+\dfrac{B}{s+3}$，其中 $A=\left.\dfrac{1}{s+3}\right|_{s=-1}$、$B=\left.\dfrac{1}{s+1}\right|_{s=-3}$。
> - **反变换**：逐项用 $\dfrac{1}{s+a}\leftrightarrow e^{-at}H(t)$。

> [!example] 解答
> 时域卷积对应变换相乘：
> $$Y(s)=\frac{1}{s+1}\cdot\frac{1}{s+3}
> =\frac{1}{(s+1)(s+3)}.$$
> 部分分式：
> $$Y(s)=\frac12\cdot\frac{1}{s+1}-\frac12\cdot\frac{1}{s+3}.$$
> 反变换：
> $$y(t)=\frac12\left(e^{-t}-e^{-3t}\right)H(t).$$
> 代入 $t=1$：
> $$y(1)=\frac12\left(e^{-1}-e^{-3}\right)
> =\frac12(0.36788-0.04979)=0.1590.$$

---

### 10. Question 10（第 10 题）^q10

What is the Laplace transform of（求下列信号的拉普拉斯变换）

$$
u(t)=e^{2t}\sin(3t)H(t)\ ?
$$

(a) $\dfrac{1}{s^2-4s+7}$（常数项把 $\omega^2$ 误写成 $\omega$）
(b) $\dfrac{3}{s^2-4s+13}$ **✓**（正确结果）
(c) $\dfrac{3}{s^2+4s+13}$（频移方向反了，对应 $e^{-2t}\sin3t$）
(d) $\dfrac{s-2}{s^2-4s+13}$（这是 $e^{2t}\cos3t$ 的变换）

> [!success] Answer（答案）
> (b) $\dfrac{3}{s^2-4s+13}$

> [!abstract] 知识点讲解
> 见 [[信号与系统/Quiz对应知识点.md|Quiz对应知识点]] 7.3 性质（$s$ 域移位）与 7.2 常用变换对。
>
> - **正弦变换对**：$\mathcal L\{\sin\omega_0t\,H(t)\}=\dfrac{\omega_0}{s^2+\omega_0^2}$，本题 $\omega_0=3$。
> - **$s$ 域移位**：$\mathcal L\{e^{at}f(t)\}=F(s-a)$，即把 $F(s)$ 中的 $s$ 全部换成 $s-a$。
> - **展开**：$(s-2)^2+9=s^2-4s+13$；也可由分母根 $2\pm3j$（验证：$2^2+3^2=13$、$-2\cdot2=-4$）直接校验。
> - **易混**：$e^{-2t}\sin3t$ 对应的是把 $s$ 换成 $s+2$。

> [!example] 解答
> 基础变换对：
> $$\sin(3t)H(t)\longleftrightarrow\frac{3}{s^2+9}.$$
> 由 $s$ 域移位，
> $$e^{2t}\sin(3t)H(t)\longleftrightarrow\frac{3}{(s-2)^2+9}.$$
> 展开分母：
> $$(s-2)^2+9=s^2-4s+4+9=s^2-4s+13.$$
> 所以
> $$U(s)=\frac{3}{s^2-4s+13}.$$
> 选 (b)。

---

### 11. Question 11（第 11 题）^q11

What is the Laplace transform of（求下列信号的拉普拉斯变换）

$$
y(t)=\int_0^t \cos(3\tau)\,d\tau,\qquad t\ge0\ ?
$$

(a) $\dfrac{1}{s^2+9}$ **✓**（正确结果）
(b) $\dfrac{3}{s^2+9}$（这是 $\sin3t$ 的变换，漏掉了积分系数）
(c) $\dfrac{1}{s(s^2+9)}$（多除了一次 $s$）
(d) $\dfrac{s^2}{s^2+9}$（把积分当成微分，乘以 $s$）

> [!success] Answer（答案）
> (a) $\dfrac{1}{s^2+9}$

> [!abstract] 知识点讲解
> 见 [[信号与系统/Quiz对应知识点.md|Quiz对应知识点]] 7.3 性质（微分与积分）。
>
> - **积分性质**：$\mathcal L\left\{\displaystyle\int_0^t f(\tau)\,d\tau\right\}=\dfrac{F(s)}{s}$，即从 $0$ 起积分对应除以 $s$。
> - **余弦变换对**：$\cos3t\,H(t)\leftrightarrow\dfrac{s}{s^2+9}$。
> - **正弦变换对**（校验用）：$\sin3t\,H(t)\leftrightarrow\dfrac{3}{s^2+9}$。
> - **易错**：积分是除以 $s$，微分是乘 $s$；本题的 $s$ 恰好与分子的 $s$ 约掉。

> [!example] 解答
> 先求被积函数的变换：
> $$\mathcal L\{\cos3t\,H(t)\}=\frac{s}{s^2+9}.$$
> 由积分性质，
> $$Y(s)=\frac{1}{s}\cdot\frac{s}{s^2+9}=\frac{1}{s^2+9}.$$
> 校验：直接积分
> $$\int_0^t\cos3\tau\,d\tau=\frac13\sin3t,$$
> 其变换为
> $$\frac13\cdot\frac{3}{s^2+9}=\frac{1}{s^2+9}.$$
> 选 (a)。

---

### 12. Question 12（第 12 题）^q12

A signal $q(t)$, zero for $t<0$, has（某信号 $q(t)$ 在 $t<0$ 时为零，其拉普拉斯变换为）

$$
Q(s)=\frac{2-4e^{-2s}}{s+3}.
$$

Find $q(3)$.（求 $q(3)$。）

> [!success] Answer（答案）
> $q(3)=-0.1989$

> [!abstract] 知识点讲解
> 见 [[信号与系统/Quiz对应知识点.md|Quiz对应知识点]] 7.3 性质（时移与阶跃延迟） 与 7.5 部分分式分解（有延迟因子的部分分式）。
>
> - **时移性质**：$e^{-s\tau}F(s)\leftrightarrow f(t-\tau)H(t-\tau)$，延迟因子让整个波形平移。
> - **变换对**：$\dfrac{1}{s+a}\leftrightarrow e^{-at}H(t)$。
> - **延迟项**：$e^{-2s}\dfrac{1}{s+3}\leftrightarrow e^{-3(t-2)}H(t-2)$，指数与阶跃**同步**延迟。
> - **分段信号**：每个延迟项只在自身起点之后非零，求某时刻值先判断各项是否已开启。

> [!example] 解答
> 拆成两项：
> $$Q(s)=\frac{2}{s+3}-4e^{-2s}\frac{1}{s+3}.$$
> 分别反变换：
> $$\frac{2}{s+3}\longleftrightarrow 2e^{-3t}H(t),$$
> $$e^{-2s}\frac{1}{s+3}\longleftrightarrow e^{-3(t-2)}H(t-2).$$
> 所以
> $$q(t)=2e^{-3t}H(t)-4e^{-3(t-2)}H(t-2).$$
> 当 $t=3$ 时两项都非零：
> $$q(3)=2e^{-9}-4e^{-3}
> =2(1.2341\times10^{-4})-4(0.049787)
> =-0.1989.$$

---

### 13. Question 13（第 13 题）^q13

A system has transfer function（某系统的传递函数为）

$$
G(s)=k\left(1+\frac{1}{\tau_i s}\right),
\qquad k=2,\quad \tau_i=0.5\ \mathrm{s}.
$$

Its input is $u(t)=H(t)$. Using the integral property, find the output $y(t)$ at $t=3$ s.（输入为单位阶跃，利用积分性质求 $t=3$ s 时的输出 $y(3)$。）

> [!success] Answer（答案）
> $y(3)=14.00$

> [!abstract] 知识点讲解
> 见 [[信号与系统/Quiz对应知识点.md|Quiz对应知识点]] 7.3 性质（微分与积分） 与 8.1 冲激响应与阶跃响应。
>
> - **传递函数关系**：$Y(s)=G(s)U(s)$，输入输出都要变换，不要漏掉输入本身的 $1/s$。
> - **积分与斜坡变换对**：$\dfrac1s\leftrightarrow H(t)$，$\dfrac{1}{s^2}\leftrightarrow tH(t)$。
> - **积分性质**：$1/s$ 相当于一次积分。
> - **分解**：$G(s)=2+\dfrac{4}{s}$ 对应「比例环节 + 积分环节」的并联。

> [!example] 解答
> 代入参数：
> $$G(s)=2\left(1+\frac{1}{0.5s}\right)=2+\frac{4}{s}.$$
> 输入 $U(s)=1/s$，所以
> $$Y(s)=G(s)U(s)=\frac{2}{s}+\frac{4}{s^2}.$$
> 逐项反变换：
> $$\frac1s\longleftrightarrow H(t),\qquad \frac{1}{s^2}\longleftrightarrow tH(t).$$
> 因此
> $$y(t)=(2+4t)H(t).$$
> 代入 $t=3$：
> $$y(3)=2+4(3)=14.00.$$

---

### 14. Question 14（第 14 题）^q14

Solving differential equations with initial conditions（带初始条件的微分方程求解）

$y(t)$ satisfies（$y(t)$ 满足）

$$
\ddot y+16y=0\qquad(t\ge0),
$$

with（初始条件为）

$$
y(0)=0,\qquad \dot y(0)=2.
$$

What is $Y(s)$?（求 $Y(s)$。）

(a) $\dfrac{2}{s(s^2+16)}$（把零输入问题当成了阶跃输入）
(b) $\dfrac{-2}{s^2+16}$（初始条件项的符号弄反）
(c) $\dfrac{2}{s^2+16}$ **✓**（正确结果）
(d) $\dfrac{2s}{s^2+16}$（把 $s$ 乘到了错误的初始条件上）

> [!success] Answer（答案）
> (c) $Y(s)=\dfrac{2}{s^2+16}$

> [!abstract] 知识点讲解
> 见 [[信号与系统/Quiz对应知识点.md|Quiz对应知识点]] 7.8 用拉普拉斯变换解微分方程 与 7.3 性质（二阶微分）。
>
> - **二阶微分性质**：$\mathcal L\{\ddot y\}=s^2Y(s)-sy(0^-)-\dot y(0^-)$。
> - **一阶微分性质**：$\mathcal L\{\dot y\}=sY(s)-y(0^-)$。
> - **零输入问题**：没有输入项，方程右端为零，初始条件作为常数移到右端。
> - **本题**：$y(0)=0$ 使 $s$ 项消失，只剩 $\dot y(0)=2$ 产生的常数。

> [!example] 解答
> 对方程两边取拉普拉斯变换：
> $$\left[s^2Y(s)-sy(0)-\dot y(0)\right]+16Y(s)=0.$$
> 代入 $y(0)=0$、$\dot y(0)=2$：
> $$s^2Y(s)-2+16Y(s)=0,$$
> $$(s^2+16)Y(s)=2.$$
> 所以
> $$Y(s)=\frac{2}{s^2+16}.$$
> 对应时域解 $y(t)=\frac12\sin4t\,H(t)$。选 (c)。

---

### 15. Question 15（第 15 题）^q15

Solve（求解）

$$
\ddot y+5\dot y+6y=6H(t),
\qquad y(0^-)=2,\quad \dot y(0^-)=-1.
$$

Give $y(1)$.（求 $y(1)$。）

> [!success] Answer（答案）
> $y(1)=1.221$

> [!abstract] 知识点讲解
> 见 [[信号与系统/Quiz对应知识点.md|Quiz对应知识点]] 7.8 用拉普拉斯变换解微分方程。
>
> - **微分性质**：$\mathcal L\{\ddot y\}=s^2Y-sy(0^-)-\dot y(0^-)$，$\mathcal L\{\dot y\}=sY-y(0^-)$。
> - **输入项**：$H(t)\leftrightarrow\dfrac1s$。
> - **解题流程**：变换 → 代数整理 → 把初值项移到右端 → 部分分式 → 反变换。
> - **遮盖法**：$\dfrac{N(s)}{(s+2)(s+3)}$ 中 $e^{-2t}$ 的系数为 $\left.\dfrac{N(s)}{s+3}\right|_{s=-2}$。

> [!example] 解答
> 逐项变换：
> $$\mathcal L\{\ddot y\}=s^2Y-2s+1,$$
> $$\mathcal L\{5\dot y\}=5(sY-2)=5sY-10,$$
> $$\mathcal L\{6H(t)\}=\frac6s.$$
> 代入方程：
> $$(s^2+5s+6)Y-2s-9=\frac6s.$$
> 把初始条件项移到右边：
> $$(s^2+5s+6)Y=\frac6s+2s+9.$$
> 通分：
> $$Y(s)=\frac{2s^2+9s+6}{s(s+2)(s+3)}.$$
> 部分分式：
> $$Y(s)=\frac1s+\frac{2}{s+2}-\frac{1}{s+3}.$$
> 反变换：
> $$y(t)=1+2e^{-2t}-e^{-3t}\qquad(t\ge0).$$
> 代入 $t=1$：
> $$y(1)=1+2e^{-2}-e^{-3}
> =1+0.27067-0.04979=1.221.$$

---

### 16. Question 16（第 16 题）^q16

Solve（求解）

$$
\ddot y+4\dot y+4y=2H(t),
\qquad y(0^-)=0.5,\quad \dot y(0^-)=0.
$$

For $t\ge0$（当 $t\ge0$ 时），

$$
y(t)=?
$$

(a) $0.5+0.5e^{-2t}+te^{-2t}$（把零输入响应叠加到终值上）
(b) $0.5-0.5e^{-2t}-te^{-2t}$（只保留了零状态响应）
(c) $0.5$ **✓**（零输入与零状态恰好抵消瞬态）
(d) $0.5e^{-2t}+te^{-2t}$（只保留了零输入响应）

> [!success] Answer（答案）
> (c) $y(t)=0.5$

> [!abstract] 知识点讲解
> 见 [[信号与系统/Quiz对应知识点.md|Quiz对应知识点]] 7.8 零输入响应与零状态响应。
>
> - **微分性质**：$\mathcal L\{\ddot y\}=s^2Y-sy(0^-)-\dot y(0^-)$，$\mathcal L\{\dot y\}=sY-y(0^-)$。
> - **响应分解**：$Y(s)=Y_{\text{zi}}(s)+Y_{\text{zs}}(s)$，初值与输入同时进入 $Y(s)$。
> - **重极点变换对**：$\dfrac{1}{(s+2)^2}\leftrightarrow te^{-2t}H(t)$。
> - **约分现象**：若分子恰好含 $(s+2)^2$，瞬态项整体消失，只剩常数项。

> [!example] 解答
> 逐项变换：
> $$\mathcal L\{\ddot y\}=s^2Y-0.5s,\qquad
> \mathcal L\{4\dot y\}=4sY-2,\qquad
> \mathcal L\{4y\}=4Y.$$
> 代入方程：
> $$(s+2)^2Y-0.5s-2=\frac2s.$$
> 整理：
> $$(s+2)^2Y=\frac2s+0.5s+2
> =\frac{2+0.5s^2+2s}{s}
> =\frac{0.5(s+2)^2}{s}.$$
> 两边约去 $(s+2)^2$：
> $$Y(s)=\frac{0.5}{s}.$$
> 反变换：
> $$y(t)=0.5H(t).$$
> 选 (c)。

---

### 17. Question 17（第 17 题）^q17

A current source $u(t)=tH(t)$ A drives a capacitor $C=0.25$ F in parallel with an inductor $L=1$ H. Both start with zero energy. Find the maximum value of the voltage $y(t)$ across them for $t\ge0$, in volts.（电流源 $u(t)=tH(t)$ A 驱动并联的 $C=0.25$ F 与 $L=1$ H，初始储能为零。求 $t\ge0$ 时并联端电压 $y(t)$ 的最大值，单位为 V。）

> [!success] Answer（答案）
> $2.000$ V

> [!abstract] 知识点讲解
> 见 [[信号与系统/Quiz对应知识点.md|Quiz对应知识点]] 8.1 冲激响应与阶跃响应 与 7.3 性质（积分与卷积）。
>
> - **并联阻抗**：$Z(s)=\dfrac{Z_LZ_C}{Z_L+Z_C}$，$Z_L=sL$，$Z_C=\dfrac{1}{sC}$，故 $Z(s)=\dfrac{sL}{s^2LC+1}$。
> - **斜坡变换对**：$tH(t)\leftrightarrow\dfrac{1}{s^2}$。
> - **电压关系**：$Y(s)=Z(s)U(s)$，阻抗与电流变换相乘。
> - **反变换变换对**：$\dfrac1s\leftrightarrow H(t)$，$\dfrac{s}{s^2+\omega_0^2}\leftrightarrow\cos\omega_0t\,H(t)$。

> [!example] 解答
> 并联阻抗：
> $$Z(s)=\frac{sL\cdot \frac{1}{sC}}{sL+\frac{1}{sC}}
> =\frac{sL}{s^2LC+1}.$$
> 代入 $L=1$、$C=0.25$：
> $$Z(s)=\frac{s}{0.25s^2+1}=\frac{4s}{s^2+4}.$$
> 电流源变换：
> $$U(s)=\mathcal L\{tH(t)\}=\frac{1}{s^2}.$$
> 电压：
> $$Y(s)=U(s)Z(s)=\frac{1}{s^2}\cdot\frac{4s}{s^2+4}
> =\frac{4}{s(s^2+4)}.$$
> 部分分式：
> $$Y(s)=\frac1s-\frac{s}{s^2+4}.$$
> 反变换：
> $$y(t)=\left(1-\cos2t\right)H(t).$$
> 最大值为
> $$y_{\max}=1-(-1)=2.000\ \mathrm{V}.$$

---

### 18. Question 18（第 18 题）^q18

Initial and final value theorems（初值定理与终值定理）

A system has（某系统的传递函数为）

$$
G(s)=\frac{120}{s^2+6s}.
$$

Use the final value theorem to find $\lim_{t\to\infty}h(t)$ for the impulse response $h(t)$.（用终值定理求冲激响应 $h(t)$ 的终值。）

> [!success] Answer（答案）
> $\displaystyle\lim_{t\to\infty}h(t)=20.00$

> [!abstract] 知识点讲解
> 见 [[信号与系统/Quiz对应知识点.md|Quiz对应知识点]] 7.4 初值定理与终值定理。
>
> - **终值定理**：若 $sF(s)$ 的全部极点在开左半平面，则 $\displaystyle\lim_{t\to\infty}f(t)=\lim_{s\to0}sF(s)$。
> - **冲激响应**：$h(t)\leftrightarrow G(s)$，故 $h(\infty)=\displaystyle\lim_{s\to0}sG(s)$。
> - **适用条件**：检查的是 $sF(s)$ 的极点，不是 $F(s)$ 本身。
> - **失效情形**：虚轴或右半平面极点使终值不存在，定理不能使用。

> [!example] 解答
> 计算
> $$sG(s)=\frac{120}{s+6}.$$
> 其唯一极点在 $s=-6$，属于开左半平面，终值定理适用。于是
> $$h(\infty)=\lim_{s\to0}sG(s)
> =\lim_{s\to0}\frac{120}{s+6}=\frac{120}{6}=20.00.$$
> 校验：$G(s)$ 的极点为 $s=0$ 与 $s=-6$，$h(t)$ 含常数项 $20$ 与衰减项，终值确实为 $20$。

---

### 19. Question 19（第 19 题）^q19

The system（系统）

$$
G(s)=\frac{s+1}{s+10}
$$

is driven by a unit step $u(t)=H(t)$ from rest. What are $y(0^+)$ and $\lim_{t\to\infty}y(t)$?（系统在零初始状态下由单位阶跃驱动。求 $y(0^+)$ 与 $\lim_{t\to\infty}y(t)$。）

(a) $y(0^+)=0,\ y(\infty)=0.1$（初值取成了终值）
(b) $y(0^+)=0.1,\ y(\infty)=1$（把初值与终值对调）
(c) $y(0^+)=1,\ y(\infty)=0$（误以为终值由零点决定）
(d) $y(0^+)=1,\ y(\infty)=0.1$ **✓**（正确的初值与终值）

> [!success] Answer（答案）
> (d) $y(0^+)=1,\quad y(\infty)=0.1$

> [!abstract] 知识点讲解
> 见 [[信号与系统/Quiz对应知识点.md|Quiz对应知识点]] 7.4 初值定理与终值定理。
>
> - **初值定理**：$\displaystyle y(0^+)=\lim_{s\to\infty}sY(s)$（$Y(s)$ 为真分式时成立）。
> - **终值定理**：$sY(s)$ 的极点全在开左半平面时，$\displaystyle y(\infty)=\lim_{s\to0}sY(s)$。
> - **阶跃响应**：$Y(s)=\dfrac{G(s)}{s}$，故 $sY(s)=G(s)$，于是 $y(0^+)=G(\infty)$、$y(\infty)=G(0)$。
> - **直流增益**：终值等于 $G(0)$。

> [!example] 解答
> 阶跃响应满足
> $$Y(s)=\frac{G(s)}{s}=\frac{s+1}{s(s+10)}.$$
> 于是
> $$sY(s)=G(s)=\frac{s+1}{s+10}.$$
> 初值：
> $$y(0^+)=\lim_{s\to\infty}\frac{s+1}{s+10}=1.$$
> 终值：$sY(s)$ 的极点在 $s=-10$，满足终值定理条件，
> $$y(\infty)=\lim_{s\to0}\frac{s+1}{s+10}=\frac{1}{10}=0.1.$$
> 分子分母同阶，所以阶跃刚加上时输出直接跳到 $1$，最终稳定在直流增益 $0.1$。选 (d)。

---

### 20. Question 20（第 20 题）^q20

An RC lowpass with（某 RC 低通的传递函数为）

$$
G(s)=\frac{1}{2s+1}
$$

(time in seconds) is driven by the ramp $u(t)=tH(t)$ V, starting from rest. Find $\lim_{t\to\infty}\left[u(t)-y(t)\right]$ in volts.（时间单位为秒。系统由斜坡电压 $u(t)=tH(t)$ 驱动，初始状态为零。求稳态跟踪误差 $\lim_{t\to\infty}[u(t)-y(t)]$，单位为 V。）

> [!success] Answer（答案）
> $2.000$ V

> [!abstract] 知识点讲解
> 见 [[信号与系统/Quiz对应知识点.md|Quiz对应知识点]] 7.4 初值定理与终值定理 与 8.1 传递函数。
>
> - **误差信号**：$e=u-y$，$Y(s)=G(s)U(s)$，故 $E(s)=U(s)\left[1-G(s)\right]$。
> - **斜坡变换对**：$tH(t)\leftrightarrow\dfrac1{s^2}$。
> - **终值定理**：$e(\infty)=\displaystyle\lim_{s\to0}sE(s)$，前提是 $sE(s)$ 的极点全在开左半平面。
> - **一阶低通**：$\dfrac{1}{2s+1}$ 对斜坡输入有恒定稳态误差，数值等于时间常数 $2$。

> [!example] 解答
> 输入变换：
> $$U(s)=\mathcal L\{tH(t)\}=\frac{1}{s^2}.$$
> 误差变换：
> $$E(s)=U(s)\left[1-G(s)\right]
> =\frac{1}{s^2}\left(1-\frac{1}{2s+1}\right)
> =\frac{1}{s^2}\cdot\frac{2s}{2s+1}
> =\frac{2}{s(2s+1)}.$$
> 检查终值定理条件：
> $$sE(s)=\frac{2}{2s+1},$$
> 唯一极点在 $s=-1/2$，满足条件。于是
> $$e(\infty)=\lim_{s\to0}sE(s)=\frac{2}{1}=2.000\ \mathrm{V}.$$
> 一阶低通对斜坡输入存在恒定的稳态误差。

---

### 21. Question 21（第 21 题）^q21

For which one of these transfer functions does the final value theorem correctly give $\lim_{t\to\infty}h(t)$ for the impulse response?（下列哪个传递函数可以用终值定理正确求出冲激响应的终值？）

(a) $G(s)=\dfrac{12}{s-4}$（有右半平面极点）
(b) $G(s)=\dfrac{12}{s^2+4}$（有虚轴极点）
(c) $G(s)=\dfrac{12}{s^4+4}$（有右半平面极点）
(d) $G(s)=\dfrac{12}{s(s+4)}$ **✓**（$sG(s)$ 的极点全在开左半平面）

> [!success] Answer（答案）
> (d) $G(s)=\dfrac{12}{s(s+4)}$

> [!abstract] 知识点讲解
> 见 [[信号与系统/Quiz对应知识点.md|Quiz对应知识点]] 7.4 初值定理与终值定理。
>
> - **终值定理**：$\displaystyle\lim_{t\to\infty}h(t)=\lim_{s\to0}sG(s)$，要求 $sG(s)$ 的所有极点在开左半平面（$\operatorname{Re}<0$）。
> - **原点单极点可用**：$G(s)=\dfrac{N(s)}{s(s+a)}$ 时 $sG(s)=\dfrac{N(s)}{s+a}$，极点可移到左半平面。
> - **右半平面极点**：$h(t)$ 指数增长，终值发散，定理失效。
> - **虚轴非零极点**：$h(t)$ 持续振荡，极限不存在，定理失效。

> [!example] 解答
> 逐项检查：
>
> (a) $sG(s)=\dfrac{12s}{s-4}$ 在 $s=4$ 有极点，且
> $$h(t)=12e^{4t}H(t)$$
> 无界，终值定理失效。
>
> (b) $sG(s)=\dfrac{12s}{s^2+4}$ 在 $s=\pm2j$ 有极点，
> $$h(t)=6\sin(2t)H(t)$$
> 振荡，没有极限。
>
> (c) $s^4+4=(s^2+2s+2)(s^2-2s+2)$，极点为 $-1\pm j$ 与 $1\pm j$，含有右半平面极点，$h(t)$ 无界。
>
> (d) 
> $$sG(s)=\frac{12}{s+4},$$
> 唯一极点在 $s=-4$，满足条件，因此
> $$h(\infty)=\lim_{s\to0}\frac{12}{s+4}=\frac{12}{4}=3.$$
>
> 选 (d)。

---

## 2. System analysis with the Laplace transform (week 9)（用拉普拉斯变换分析系统，第 9 周）

Transfer functions, poles and stability（传递函数、极点与稳定性）

---

### 22. Question 22（第 22 题）^q22

Classify（对下列系统进行分类）

$$
G(s)=\frac{12}{s^2+4}.
$$

(a) BIBO stable but not exponentially stable（BIBO 稳定但非指数稳定）
(b) Marginally stable and not BIBO stable **✓**（临界稳定但不 BIBO 稳定）
(c) Unstable（不稳定）
(d) Exponentially stable（指数稳定）

> [!success] Answer（答案）
> (b) 临界稳定，但不 BIBO 稳定

> [!abstract] 知识点讲解
> 见 [[信号与系统/Quiz对应知识点.md|Quiz对应知识点]] 6.3 极点判据速查 与 6.7 稳定性补充例题。
>
> - **极点判据**：全部极点在开左半平面 ⇔ 指数稳定；虚轴单极点且其余在左半平面 → 临界稳定。
> - **BIBO 稳定条件**：$\displaystyle\int_0^\infty|h(t)|dt<\infty$。
> - **正弦冲激响应**：$h(t)=A\sin\omega_0t\,H(t)$ 有界但绝对不可积，$\displaystyle\int_0^\infty|\sin\omega_0t|dt=\infty$。
> - **结论**：临界稳定 ≠ BIBO 稳定。

> [!example] 解答
> 极点为 $s=\pm2j$，位于虚轴且互不相同，其他极点没有。冲激响应为
> $$h(t)=6\sin2t\,H(t),$$
> 有界，因此系统临界稳定。
>
> 绝对值积分：
> $$\int_0^\infty\left|6\sin2t\right|dt=\infty,$$
> 因为 $|\sin2t|$ 每个周期正面积恒定，积分随周期数线性增长。所以不 BIBO 稳定。
>
> 选 (b)。

---

### 23. Question 23（第 23 题）^q23

A transfer function $G(s)$ has poles at $0$ and $-0.2\pm j$, with no pole–zero cancellation. Which description is correct?（某传递函数 $G(s)$ 的极点在 $0$ 和 $-0.2\pm j$，且没有零极点抵消。下列描述哪个正确？）

(a) Marginally stable, but not BIBO stable **✓**（临界稳定，但不 BIBO 稳定）
(b) Marginally stable and BIBO stable（临界稳定且 BIBO 稳定）
(c) Exponentially stable（指数稳定）
(d) Unstable（不稳定）

> [!success] Answer（答案）
> (a) 临界稳定，但不 BIBO 稳定

> [!abstract] 知识点讲解
> 见 [[信号与系统/Quiz对应知识点.md|Quiz对应知识点]] 6.3 极点判据速查 与 6.7 例 1（虚轴单极点与原点极点）。
>
> - **临界稳定判据**：全部极点在闭左半平面（$\operatorname{Re}s\le0$），虚轴极点均为单根，且至少有一个虚轴极点。
> - **极点贡献**：$s=0$ 的单极点对应 $h(t)$ 中的常数项 $C H(t)$；$-0.2\pm j$ 对应衰减振荡 $e^{-0.2t}\cos t$。
> - **BIBO 条件**：常数项 $C\neq0$ 使 $\displaystyle\int_0^\infty|h(t)|dt$ 发散。
> - **结论**：临界稳定但不 BIBO 稳定。

> [!example] 解答
> 冲激响应由各极点对应的模态叠加：
> $$h(t)=A e^{-0.2t}\cos t+B e^{-0.2t}\sin t+C H(t).$$
> 前两项衰减到零，常数项 $C\neq0$ 一直存在，所以 $h(t)$ 有界但不趋于零，系统临界稳定。
>
> 绝对值积分：上述两个衰减项都可积，常数项留下来：
> $$\int_0^\infty|h(t)|dt\ge \int_T^\infty|h(t)|dt.$$
> 取足够大的 $T$，使两个衰减项的绝对值都小于 $|C|/2$，则 $t>T$ 时 $|h(t)|\ge|C|/2$，所以
> $$\int_T^\infty|h(t)|dt\ge \frac{|C|}{2}(t-T)\to\infty.$$
> 不 BIBO 稳定。选 (a)。

---

### 24. Question 24（第 24 题）^q24

Which transfer function is marginally stable?（哪个传递函数是临界稳定的？）

(a) $\dfrac{s+2}{(s^2+4)(s+1)}$ **✓**
(b) $\dfrac{s-2}{(s+1)(s+3)}$
(c) $\dfrac{s+2}{s^2(s+3)}$
(d) $\dfrac{s+2}{(s^2+4)^2}$

> [!success] Answer（答案）
> (a) $\dfrac{s+2}{(s^2+4)(s+1)}$

> [!abstract] 知识点讲解
> 见 [[信号与系统/Quiz对应知识点.md|Quiz对应知识点]] 6.3 极点判据速查。
>
> - **临界稳定判据**：闭左半平面 + 虚轴单根 + 至少一个虚轴极点。
> - **重极点**：$(s^2+\omega_0^2)^2$ 对应 $t\sin\omega_0t$、$t\cos\omega_0t$，增长项 ⇒ 不稳定。
> - **原点重极点**：$s^2$ 对应 $tH(t)$，无界 ⇒ 不稳定。
> - **零点作用**：只改变幅度和相位，不改变稳定性分类。

> [!example] 解答
> 逐项求极点：
>
> (a) 极点为 $s=\pm2j$（单根）和 $s=-1$。$\pm2j$ 在虚轴上且为单根，$-1$ 在开左半平面，临界稳定。
>
> (b) 极点为 $s=-1,-3$，全在开左半平面，指数稳定。零点 $+2$ 不改变稳定性。
>
> (c) 极点为 $s=0$（二重）和 $s=-3$。原点二重极点使 $h(t)$ 含 $t$ 项，不稳定。
>
> (d) 极点为 $s=\pm2j$（二重）。二重虚轴极点使 $h(t)$ 含 $t\sin2t$ 项，不稳定。
>
> 选 (a)。

---

### 25. Question 25（第 25 题）^q25

Classify（对下列系统进行分类）

$$
G(s)=\frac{12}{s^4+4}.
$$

Hint（提示）：

$$
s^4+4=\left(s^2+2s+2\right)\left(s^2-2s+2\right).
$$

(a) Exponentially stable, since all denominator coefficients are positive（因为分母系数全为正，所以指数稳定）
(b) BIBO stable but not exponentially stable（BIBO 稳定但非指数稳定）
(c) Marginally stable, with poles on the imaginary axis like $s^2+4$（像 $s^2+4$ 一样有虚轴极点，临界稳定）
(d) Unstable **✓**（不稳定）

> [!success] Answer（答案）
> (d) 不稳定

> [!abstract] 知识点讲解
> 见 [[信号与系统/Quiz对应知识点.md|Quiz对应知识点]] 6.3 极点判据速查 与 6.7 例 3（四阶多项式的极点）。
>
> - **分解技巧**：$s^4+4=\left(s^2+2s+2\right)\left(s^2-2s+2\right)$。
> - **求根**：$s^2+2s+2=0\Rightarrow s=-1\pm j$；$s^2-2s+2=0\Rightarrow s=1\pm j$。
> - **分子作用**：$12$ 只缩放冲激响应的幅度，不改变极点位置与稳定性分类。
> - **不稳定判据**：只要有一个极点在右半平面（$\operatorname{Re}s>0$），系统不稳定。
> - **劳斯判据提示**：系数全正只是必要条件；缺项（$s^3,s^2,s$ 系数为零）时不可判稳。

> [!example] 解答
> 分解：
> $$s^2+2s+2=0\quad\Longrightarrow\quad s=-1\pm j,$$
> $$s^2-2s+2=0\quad\Longrightarrow\quad s=1\pm j.$$
> 后一对极点的实部为 $+1$，位于右半平面，$h(t)$ 含 $e^{t}\cos t$ 型增长项，无界。
>
> 系数检查也提醒一遍：$s^4+4$ 的 $s^3,s^2,s$ 系数均为零，不能因「系数看起来不坏」就判稳定。选 (d)。

---

### 26. Question 26（第 26 题）^q26

For（对于）

$$
G(s)=\frac{1}{s^2+9}
$$

with zero initial conditions, which bounded input produces an unbounded output?（零初始条件下，哪个有界输入会产生无界输出？）

(a) $\cos(3t)H(t)$ **✓**
(b) $H(t)$
(c) $\cos(9t)H(t)$
(d) $e^{-3t}H(t)$

> [!success] Answer（答案）
> (a) $\cos(3t)H(t)$

> [!abstract] 知识点讲解
> 见 [[信号与系统/Quiz对应知识点.md|Quiz对应知识点]] 6.7 例 4（共振输入）。
>
> - **共振条件**：输入极点与系统极点重合，$Y(s)$ 出现**二重极点**。
> - **二重极点响应**：$\dfrac{1}{(s^2+\omega_0^2)^2}$ 型极点产生 $t\sin\omega_0t$、$t\cos\omega_0t$。
> - **输入变换**：$\cos\omega_0t\,H(t)\leftrightarrow\dfrac{s}{s^2+\omega_0^2}$。
> - **有界输入**：$|G(j\omega)|$ 有界不等于 BIBO 稳定；$\cos3t$ 与系统自然频率相同才共振。

> [!example] 解答
> 系统 $G(s)=\dfrac{1}{s^2+9}$ 的极点在虚轴上 $s=\pm j3$，冲激响应为
>
> $$h(t)=\frac13\sin(3t)\,H(t).$$
>
> 逐个选项把 $Y(s)=G(s)U(s)$ 展开成部分分式，再反变换。
>
> **(a) $u(t)=\cos(3t)H(t)$**
>
> $$U(s)=\frac{s}{s^2+9},$$
>
> $$Y(s)=\frac{1}{s^2+9}\cdot\frac{s}{s^2+9}=\frac{s}{(s^2+9)^2}.$$
>
> 输入极点与系统极点完全重合，分母出现二重极点。由
>
> $$\mathcal L\{t\sin\omega_0t\}=\frac{2\omega_0s}{(s^2+\omega_0^2)^2},$$
>
> 取 $\omega_0=3$ 得
>
> $$y(t)=\frac{t}{6}\sin(3t)\,H(t).$$
>
> 幅度随 $t$ 线性增长，无界。
>
> **(b) $u(t)=H(t)$**
>
> $$U(s)=\frac1s,$$
>
> $$Y(s)=\frac{1}{s(s^2+9)}=\frac19\left(\frac1s-\frac{s}{s^2+9}\right).$$
>
> 反变换：
>
> $$y(t)=\frac19\left(1-\cos(3t)\right)H(t).$$
>
> $0\le y(t)\le\dfrac29$，有界。输入极点 $s=0$ 与系统极点 $\pm j3$ 不重合，没有二重极点。
>
> **(c) $u(t)=\cos(9t)H(t)$**
>
> $$U(s)=\frac{s}{s^2+81},$$
>
> $$Y(s)=\frac{s}{(s^2+9)(s^2+81)}
> =\frac{1}{72}\left(\frac{s}{s^2+9}-\frac{s}{s^2+81}\right).$$
>
> 反变换：
>
> $$y(t)=\frac{1}{72}\left(\cos(3t)-\cos(9t)\right)H(t).$$
>
> $|y(t)|\le\dfrac{1}{36}$，有界。输入频率 $9$ 与系统自然频率 $3$ 不同，不发生共振。
>
> **(d) $u(t)=e^{-3t}H(t)$**
>
> $$U(s)=\frac{1}{s+3},$$
>
> $$Y(s)=\frac{1}{(s+3)(s^2+9)}
> =\frac{1}{18}\left(\frac{1}{s+3}-\frac{s}{s^2+9}+\frac{3}{s^2+9}\right).$$
>
> 反变换：
>
> $$y(t)=\frac{1}{18}\left(e^{-3t}-\cos(3t)+\sin(3t)\right)H(t).$$
>
> $|y(t)|\le\dfrac{1}{18}(1+1+1)=\dfrac16$，有界。输入极点在 $s=-3$，远离虚轴。
>
> **归纳**：只有 (a) 让输入的极点与系统极点 $\pm j3$ 重合，$Y(s)$ 出现 $(s^2+9)^2$ 的二重极点，时域多出因子 $t$，所以输出无界。其余三种输入的极点都不与 $\pm j3$ 重合，系统的虚轴单极点只产生有界的等幅振荡。选 (a)。

---

### 27. Question 27（第 27 题）^q27

Partial fractions and inverse transforms（部分分式与反变换）

Find the impulse response of（求下列系统的冲激响应）

$$
G(s)=\frac{s+2}{s(s+1)}
$$

at $t=1$ s.（在 $t=1$ s 处的值。）

> [!success] Answer（答案）
> $h(1)=1.632$

> [!abstract] 知识点讲解
> 见 [[信号与系统/Quiz对应知识点.md|Quiz对应知识点]] 7.5 部分分式分解（遮盖法求单实极点）。
>
> - **部分分式**：$G(s)=\dfrac{A}{s}+\dfrac{B}{s+1}$。
> - **遮盖法（留数）**：$A=\left.\dfrac{s+2}{s+1}\right|_{s=0}$，$B=\left.\dfrac{s+2}{s}\right|_{s=-1}$，等于 $s$ 乘 $G(s)$ 在对应极点处的值。
> - **变换对**：$\dfrac1s\leftrightarrow H(t)$，$\dfrac{1}{s+1}\leftrightarrow e^{-t}H(t)$。
> - **冲激响应**：$h(t)\leftrightarrow G(s)$，直接对它做反变换。

> [!example] 解答
> 部分分式：
> $$G(s)=\frac{A}{s}+\frac{B}{s+1}.$$
> 遮盖法：
> $$A=\left.\frac{s+2}{s+1}\right|_{s=0}=\frac21=2,$$
> $$B=\left.\frac{s+2}{s}\right|_{s=-1}=\frac{1}{-1}=-1.$$
> 所以
> $$h(t)=\left(2-e^{-t}\right)H(t).$$
> 代入 $t=1$：
> $$h(1)=2-e^{-1}=2-0.36788=1.632.$$

---

### 28. Question 28（第 28 题）^q28

Write（写成）

$$
Y(s)=\frac{6}{s^2(s+3)}
=\frac{A}{s}+\frac{B}{s^2}+\frac{C}{s+3}.
$$

Find $A$.（求 $A$。）

> [!success] Answer（答案）
> $A=-0.6667$

> [!abstract] 知识点讲解
> 见 [[信号与系统/Quiz对应知识点.md|Quiz对应知识点]] 7.5 部分分式分解（重极点）。
>
> - **重极点展开**：$\dfrac{6}{s^2(s+3)}=\dfrac{A}{s}+\dfrac{B}{s^2}+\dfrac{C}{s+3}$。
> - **遮盖法可求**：$B=\left.\dfrac{6}{s+3}\right|_{s=0}$，$C=\left.\dfrac{6}{s^2}\right|_{s=-3}$。
> - **比较系数求 $A$**：通分得 $6=As(s+3)+B(s+3)+Cs^2$，右边 $s^2$ 系数为 $A+C$，左边无 $s^2$ 项，故 $A+C=0$。
> - **反变换**：$\dfrac{1}{s^2}\leftrightarrow tH(t)$，$\dfrac{1}{s+3}\leftrightarrow e^{-3t}H(t)$。

> [!example] 解答
> 遮盖法先求 $B$、$C$：
> $$B=\left.\frac{6}{s+3}\right|_{s=0}=2,$$
> $$C=\left.\frac{6}{s^2}\right|_{s=-3}=\frac69=\frac23.$$
> 比较分子：
> $$6=As(s+3)+B(s+3)+Cs^2.$$
> 展开后 $s^2$ 的系数为 $A+C$，左边没有 $s^2$ 项，所以
> $$A+C=0\quad\Longrightarrow\quad A=-\frac23=-0.6667.$$
> 校验：取 $s=1$，
> $$-\frac23+2+\frac23\cdot\frac14=1.5=\frac{6}{1\cdot4},$$
> 一致。

---

### 29. Question 29（第 29 题）^q29

What is the inverse Laplace transform of（求下列信号的反变换）

$$
Y(s)=\frac{2s+5}{s^2+2s+1}\ ?
$$

(a) $2\delta(t)+3te^{-t}H(t)$（误以为分子可能与分母同阶而产生冲激）
(b) $(2+3t)e^{-t}H(t)$ **✓**（正确结果）
(c) $(3+2t)e^{-t}H(t)$（$A$、$B$ 的位置对调）
(d) $(2+5t)e^{-t}H(t)$（把 $B$ 错误地取成分子在 $s=0$ 处的值）

> [!success] Answer（答案）
> (b) $(2+3t)e^{-t}H(t)$

> [!abstract] 知识点讲解
> 见 [[信号与系统/Quiz对应知识点.md|Quiz对应知识点]] 7.5 部分分式分解（重极点）。
>
> - **重极点展开**：$\dfrac{2s+5}{(s+1)^2}=\dfrac{A}{s+1}+\dfrac{B}{(s+1)^2}$。
> - **遮盖法求最高次项系数**：$B=\left.(2s+5)\right|_{s=-1}=3$。
> - **重极点变换对**：$\dfrac{1}{(s+1)^2}\leftrightarrow te^{-t}H(t)$，$\dfrac{1}{s+1}\leftrightarrow e^{-t}H(t)$。
> - **真分式判据**：分子次数低于分母次数 ⇒ 反变换中无 $\delta(t)$。

> [!example] 解答
> 分母配方：
> $$s^2+2s+1=(s+1)^2.$$
> 拆项：
> $$Y(s)=\frac{A}{s+1}+\frac{B}{(s+1)^2}.$$
> 遮盖法求 $B$：
> $$B=\left.(2s+5)\right|_{s=-1}=3.$$
> 通分比较分子：
> $$2s+5=A(s+1)+3=As+(A+3).$$
> $$A=2.$$
> 所以
> $$Y(s)=\frac{2}{s+1}+\frac{3}{(s+1)^2}.$$
> 反变换：
> $$y(t)=2e^{-t}H(t)+3te^{-t}H(t)=(2+3t)e^{-t}H(t).$$
> 分子次数低于分母，没有冲激项。选 (b)。

---

### 30. Question 30（第 30 题）^q30

The inverse transform of（下列信号的反变换具有形式）

$$
Y(s)=\frac{3s+1}{(s+1)(s^2+2s+5)}
$$

has the form（形如）

$$
y(t)=Ae^{-t}+e^{-t}\left(B\cos2t+C\sin2t\right),\qquad t\ge0.
$$

Find $C$.（求 $C$。）

> [!success] Answer（答案）
> $C=1.5$

> [!abstract] 知识点讲解
> 见 [[信号与系统/Quiz对应知识点.md|Quiz对应知识点]] 7.5 部分分式分解（共轭复极点）。
>
> - **复极点配方**：$s^2+2s+5=(s+1)^2+4$，即极点 $-1\pm2j$：衰减率 $\alpha=1$、振荡角频率 $\omega_0=2$。
> - **变换对**：$\dfrac{s+a}{(s+a)^2+\omega_0^2}\leftrightarrow e^{-at}\cos\omega_0t$，$\dfrac{\omega_0}{(s+a)^2+\omega_0^2}\leftrightarrow e^{-at}\sin\omega_0t$。
> - **系数关系**：把分子写成 $D(s+a)+E$ 后，$\cos$ 项系数为 $D$，$\sin$ 项系数为 $\dfrac{E}{\omega_0}$。本题 $0.5s+3.5=0.5(s+1)+3$：$\cos$ 系数 $0.5$，$\sin$ 系数 $\dfrac{3}{2}=1.5$。
> - **求待定系数**：实极点用遮盖法，剩余部分通分比较分子系数。

> [!example] 解答
> 遮盖法求实极点系数：
> $$A=\left.\frac{3s+1}{s^2+2s+5}\right|_{s=-1}=\frac{-2}{4}=-0.5.$$
> 令剩余部分为 $\dfrac{Ds+E}{(s+1)^2+4}$，通分比较分子：
> $$3s+1=A(s^2+2s+5)+(Ds+E)(s+1).$$
> 比较 $s^2$ 系数：$0=A+D$，得 $D=0.5$。
>
> 比较 $s^0$ 系数：$1=5A+E$，即 $1=-2.5+E$，得 $E=3.5$。
>
> 所以
> $$Y(s)=-\frac{0.5}{s+1}+\frac{0.5s+3.5}{(s+1)^2+4}.$$
> 拆复极点部分：
> $$\frac{0.5s+3.5}{(s+1)^2+4}
> =0.5\cdot\frac{s+1}{(s+1)^2+4}+1.5\cdot\frac{2}{(s+1)^2+4}.$$
> 对照形式
> $$y(t)=-0.5e^{-t}+0.5e^{-t}\cos2t+1.5e^{-t}\sin2t,$$
> 得 $C=1.5$。

---

### 31. Question 31（第 31 题）^q31

$$
G(s)=\frac{s+3}{(s+1)(s+3.1)}
$$

has a zero very close to a pole. Find the coefficient of $e^{-3.1t}$ in the impulse response $g(t)$.（该传递函数的零点非常靠近一个极点。求冲激响应中 $e^{-3.1t}$ 项的系数。）

> [!success] Answer（答案）
> $0.04762$

> [!abstract] 知识点讲解
> 见 [[信号与系统/Quiz对应知识点.md|Quiz对应知识点]] 6.7 例 5（零点靠近极点）。
>
> - **遮盖法**：$e^{-3.1t}$ 的系数为 $A_{3.1}=\left.\dfrac{s+3}{s+1}\right|_{s=-3.1}$。
> - **零点-极点距离**：零点 $z$ 与极点 $p$ 的距离 $|z-p|$ 决定该模态的残留幅度。
> - **极限情形**：$z=p$ 时零点与极点完全抵消，该模态消失；$|z-p|$ 很小时系数很小但不为零。
> - **判别**：系数非常小 ≠ 系数为零。

> [!example] 解答
> 部分分式：
> $$G(s)=\frac{A}{s+1}+\frac{A_{3.1}}{s+3.1}.$$
> 遮盖 $s=-3.1$：
> $$A_{3.1}=\left.\frac{s+3}{s+1}\right|_{s=-3.1}
> =\frac{-0.1}{-2.1}=0.04762.$$
> 零点 $-3$ 与极点 $-3.1$ 只差 $0.1$，所以 $e^{-3.1t}$ 项的系数很小。

---

### 32. Question 32（第 32 题）^q32

Find $y(3)$ where（求 $y(3)$，已知）

$$
Y(s)=\frac{4e^{-s}}{(s+1)(s+3)}.
$$

> [!success] Answer（答案）
> $y(3)=0.2657$

> [!abstract] 知识点讲解
> 见 [[信号与系统/Quiz对应知识点.md|Quiz对应知识点]] 7.5 部分分式分解（有延迟因子的部分分式）。
>
> - **时移性质**：$e^{-s\tau}F(s)\leftrightarrow f(t-\tau)H(t-\tau)$。
> - **处理顺序**：先对有理部分 $F(s)$ 做部分分式、反变换得 $f(t)$，再整体延迟 $\tau$。
> - **部分分式**：$\dfrac{4}{(s+1)(s+3)}=\dfrac{2}{s+1}-\dfrac{2}{s+3}$。
> - **阶跃因子**：延迟后每一项都带 $H(t-1)$，$t=3$ 时两项都已开启。

> [!example] 解答
> 有理部分：
> $$\frac{4}{(s+1)(s+3)}=\frac{2}{s+1}-\frac{2}{s+3}.$$
> 乘上延迟因子：
> $$Y(s)=e^{-s}\left(\frac{2}{s+1}-\frac{2}{s+3}\right).$$
> 反变换：
> $$y(t)=\left[2e^{-(t-1)}-2e^{-3(t-1)}\right]H(t-1).$$
> 代入 $t=3$：
> $$y(3)=2\left(e^{-2}-e^{-6}\right)
> =2(0.13534-0.002479)=0.2657.$$

---

### 33. Question 33（第 33 题）^q33

$$
G(s)=\frac{s+4}{s^2+3s+2}
$$

is driven by $u(t)=e^{-2t}H(t)$ with zero initial conditions. Find $y(1)$.（系统在零初始条件下由 $u(t)=e^{-2t}H(t)$ 驱动。求 $y(1)$。）

> [!success] Answer（答案）
> $y(1)=0.4270$

> [!abstract] 知识点讲解
> 见 [[信号与系统/Quiz对应知识点.md|Quiz对应知识点]] 7.9 例 1（系统极点与输入极点重合）。
>
> - **输出变换**：$Y(s)=G(s)U(s)$，输入极点与系统极点重合时出现重极点。
> - **重极点响应**：重极点 $s=-2$ 对应 $te^{-2t}$ 项。
> - **部分分式**：展开为 $\dfrac{A}{s+1}+\dfrac{B}{s+2}+\dfrac{C}{(s+2)^2}$。
> - **求系数**：$A$、$C$ 用遮盖法 $\left.\dfrac{s+4}{(s+2)^2}\right|_{s=-1}$、$\left.\dfrac{s+4}{s+1}\right|_{s=-2}$；$B$ 比较 $s^2$ 系数。

> [!example] 解答
> 系统分母分解：
> $$s^2+3s+2=(s+1)(s+2).$$
> 输入变换：
> $$U(s)=\frac{1}{s+2}.$$
> 输出：
> $$Y(s)=\frac{s+4}{(s+1)(s+2)^2}.$$
> 部分分式：
> $$Y(s)=\frac{A}{s+1}+\frac{B}{s+2}+\frac{C}{(s+2)^2}.$$
> 遮盖法：
> $$A=\left.\frac{s+4}{(s+2)^2}\right|_{s=-1}=\frac{3}{1}=3,$$
> $$C=\left.\frac{s+4}{s+1}\right|_{s=-2}=\frac{2}{-1}=-2.$$
> 比较 $s^2$ 系数（左边为 $0$）：
> $$0=A+B\quad\Longrightarrow\quad B=-3.$$
> 反变换：
> $$y(t)=3e^{-t}-3e^{-2t}-2te^{-2t}\qquad(t\ge0).$$
> 代入 $t=1$：
> $$y(1)=3e^{-1}-3e^{-2}-2e^{-2}=0.4270.$$

---

### 34. Question 34（第 34 题）^q34

An RC lowpass with（某 RC 低通的传递函数为）

$$
G(s)=\frac{1}{s+1}
$$

starts from rest and is driven by（零初始状态下由下列输入驱动）

$$
u(t)=\left(1-e^{-3t}\right)H(t)\ \mathrm{V}.
$$

Find $y(1)$ in volts.（求 $y(1)$，单位为 V。）

> [!success] Answer（答案）
> $y(1)=0.4731$ V

> [!abstract] 知识点讲解
> 见 [[信号与系统/Quiz对应知识点.md|Quiz对应知识点]] 7.5 部分分式分解（遮盖法） 与 7.9 系统分析典型例题。
>
> - **输入合并**：$U(s)=\dfrac1s-\dfrac1{s+3}=\dfrac{3}{s(s+3)}$，先合并成一个分数再乘 $G(s)$。
> - **输出变换**：$Y(s)=G(s)U(s)=\dfrac{3}{s(s+1)(s+3)}$。
> - **遮盖法**：$A=\left.\dfrac{3}{(s+1)(s+3)}\right|_{s=0}=1$，$B=\left.\dfrac{3}{s(s+3)}\right|_{s=-1}=-\dfrac32$，$C=\left.\dfrac{3}{s(s+1)}\right|_{s=-3}=\dfrac12$。
> - **反变换**：$\dfrac1s\leftrightarrow H(t)$，$\dfrac{1}{s+a}\leftrightarrow e^{-at}H(t)$。

> [!example] 解答
> 输入变换：
> $$U(s)=\frac1s-\frac{1}{s+3}
> =\frac{3}{s(s+3)}.$$
> 输出：
> $$Y(s)=\frac{3}{s(s+1)(s+3)}.$$
> 部分分式：
> $$Y(s)=\frac{A}{s}+\frac{B}{s+1}+\frac{C}{s+3}.$$
> 遮盖法：
> $$A=\left.\frac{3}{(s+1)(s+3)}\right|_{s=0}=1,$$
> $$B=\left.\frac{3}{s(s+3)}\right|_{s=-1}=\frac{3}{-1\cdot2}=-\frac32,$$
> $$C=\left.\frac{3}{s(s+1)}\right|_{s=-3}=\frac{3}{-3\cdot(-2)}=\frac12.$$
> 反变换：
> $$y(t)=1-\frac32e^{-t}+\frac12e^{-3t}\qquad(t\ge0).$$
> 代入 $t=1$：
> $$y(1)=1-1.5(0.36788)+0.5(0.04979)=0.4731\ \mathrm{V}.$$

---

### 35. Question 35（第 35 题）^q35

Two identical RC sections, each with transfer function（两个相同的 RC 节，每节传递函数为）

$$
\frac{2}{s+2},
$$

are connected through an ideal unity-gain buffer, so the overall transfer function is（通过理想单位增益缓冲器级联，总传递函数为）

$$
\frac{4}{(s+2)^2}.
$$

A unit step is applied from rest. Find the output at $t=1$ s.（零初始状态下加上单位阶跃，求 $t=1$ s 时的输出。）

> [!success] Answer（答案）
> $y(1)=0.5940$

> [!abstract] 知识点讲解
> 见 [[信号与系统/Quiz对应知识点.md|Quiz对应知识点]] 7.5 部分分式分解（重极点） 与 8.5 级联不是高阶 Butterworth。
>
> - **级联性质**：$G=G_1G_2$，传递函数相乘。
> - **阶跃响应**：$Y(s)=\dfrac{G(s)}{s}$，多一个原点极点。
> - **重极点变换对**：$\dfrac{1}{(s+2)^2}\leftrightarrow te^{-2t}H(t)$。
> - **求系数**：$A=\left.\dfrac{4}{(s+2)^2}\right|_{s=0}$，$C=\left.\dfrac{4}{s}\right|_{s=-2}$，$B$ 比较 $s^2$ 系数。

> [!example] 解答
> 输出：
> $$Y(s)=\frac{4}{s(s+2)^2}
> =\frac{A}{s}+\frac{B}{s+2}+\frac{C}{(s+2)^2}.$$
> 遮盖法：
> $$A=\left.\frac{4}{(s+2)^2}\right|_{s=0}=1,$$
> $$C=\left.\frac{4}{s}\right|_{s=-2}=-2.$$
> 比较 $s^2$ 系数：
> $$0=A+B\quad\Longrightarrow\quad B=-1.$$
> 反变换：
> $$y(t)=1-e^{-2t}-2te^{-2t}\qquad(t\ge0).$$
> 代入 $t=1$：
> $$y(1)=1-e^{-2}-2e^{-2}=1-3e^{-2}=1-0.40601=0.5940.$$

---

### 36. Question 36（第 36 题）^q36

A series RLC circuit ($L=1$ H, $C=0.25$ F, $R=2\ \Omega$, output across $C$, starting from rest) has（串联 RLC 电路，$L=1$ H、$C=0.25$ F、$R=2\ \Omega$，输出取自电容两端，零初始状态）

$$
G(s)=\frac{4}{s^2+2s+4}.
$$

Which input $u(t)$ makes the output exactly（哪个输入能使输出恰好为）

$$
y(t)=\left(1-e^{-4t}\right)H(t)\ ?
$$

(a) $u(t)=\delta(t)+\left(1-3e^{-4t}\right)H(t)$ **✓**
(b) $u(t)=\left(1-3e^{-4t}\right)H(t)$（漏掉了多项式除法产生的冲激）
(c) No such input exists, because the circuit is underdamped（欠阻尼电路，不存在这样的输入）
(d) $u(t)=\left(1-e^{-4t}\right)H(t)$（误以为 $G=1$）

> [!success] Answer（答案）
> (a) $u(t)=\delta(t)+\left(1-3e^{-4t}\right)H(t)$

> [!abstract] 知识点讲解
> 见 [[信号与系统/Quiz对应知识点.md|Quiz对应知识点]] 7.9 例 3（由输出反求输入）（假分式先做除法）。
>
> - **反求关系**：$U(s)=\dfrac{Y(s)}{G(s)}$。
> - **假分式除法**：分子次数 ≥ 分母次数时，先做多项式除法；**常数项**对应 $\delta(t)$。
> - **部分分式**：真分式部分用遮盖法展开。
> - **零极点抵消**：反求输入时 $U(s)=\dfrac{Y(s)}{G(s)}$，其分子 $s^2+2s+4$ 恰为 $G(s)$ 的分母，与系统的复极点相消，因此给定的 $y(t)$ 不含振荡模态。

> [!example] 解答
> 由 $y$ 求 $Y$：
> $$Y(s)=\frac1s-\frac{1}{s+4}=\frac{4}{s(s+4)}.$$> 求输入变换：
> $$U(s)=\frac{Y(s)}{G(s)}
> =\frac{4}{s(s+4)}\cdot\frac{s^2+2s+4}{4}
> =\frac{s^2+2s+4}{s(s+4)}.$$
> 分子次数等于分母次数，做除法：
> $$U(s)=1+\frac{s^2+2s+4-s(s+4)}{s(s+4)}
> =1+\frac{-2s+4}{s(s+4)}.$$
> 真分式部分：
> $$\frac{-2s+4}{s(s+4)}=\frac{1}{s}-\frac{3}{s+4}.$$
> 反变换：
> $$u(t)=\delta(t)+\left(1-3e^{-4t}\right)H(t).$$
> 常数项 $1$ 是冲激，不能省略。选 (a)。

---

### 37. Question 37（第 37 题）^q37

Zeros（零点）

$G(s)$ has poles at $-2$ and $-5$, a single zero at $-1$, and DC gain $3$. The input is $u(t)=e^{-t}H(t)$, starting from rest. What is $y(t)$?（$G(s)$ 的极点在 $-2$、$-5$，零点在 $-1$，直流增益为 $3$。系统在零初始状态下由 $u(t)=e^{-t}H(t)$ 驱动。求 $y(t)$。）

(a) $\left(e^{-2t}-e^{-5t}\right)H(t)$（增益取错，$k=3$ 而不是 $30$）
(b) $y(t)=0$, because the zero at $-1$ blocks $e^{-t}$（误以为零点会阻断整个输出）
(c) $10\left(e^{-2t}-e^{-5t}\right)H(t)$ **✓**（正确结果）
(d) $y(t)$ contains a nonzero $e^{-t}$ term as well as $e^{-2t}$ and $e^{-5t}$ terms（误以为输入极点没有被抵消）

> [!success] Answer（答案）
> (c) $y(t)=10\left(e^{-2t}-e^{-5t}\right)H(t)$

> [!abstract] 知识点讲解
> 见 [[信号与系统/Quiz对应知识点.md|Quiz对应知识点]] 7.9 例 2（零点抵消输入极点）。
>
> - **一般形式**：$G(s)=\dfrac{k(s+1)}{(s+2)(s+5)}$（极点、零点、待定增益）。
> - **直流增益**：$G(0)=\dfrac{k}{2\cdot5}$，由 $G(0)=3$ 定出 $k$。
> - **零点抵消输入极点**：输入极点 $s=-1$ 被零点 $s=-1$ 约掉，$Y(s)$ 不含 $\dfrac{1}{s+1}$ 项。
> - **系统模态**：$-2$、$-5$ 两个极点仍被激励，输出含 $e^{-2t}$、$e^{-5t}$。

> [!example] 解答
> 一般形式：
> $$G(s)=\frac{k(s+1)}{(s+2)(s+5)}.$$
> 由 $G(0)=3$：
> $$\frac{k}{10}=3\quad\Longrightarrow\quad k=30.$$
> 输出：
> $$Y(s)=\frac{30(s+1)}{(s+2)(s+5)}\cdot\frac{1}{s+1}
> =\frac{30}{(s+2)(s+5)}.$$
> 部分分式：
> $$Y(s)=\frac{10}{s+2}-\frac{10}{s+5}.$$
> 反变换：
> $$y(t)=10\left(e^{-2t}-e^{-5t}\right)H(t).$$
> 零点只消除了 $e^{-t}$ 这一项，系统模态 $e^{-2t}$、$e^{-5t}$ 仍然存在。选 (c)。

---

### 38. Question 38（第 38 题）^q38

$$
G(s)=1+\frac{1}{s}+0.25s.
$$

Which describes the straight-line Bode magnitude?（其渐近 Bode 幅频图如何描述？）

(a) 0 dB/decade below 2 rad/s, then +40 dB/decade（误以为原点处没有极点）
(b) −20 dB/decade below 2 rad/s, then +20 dB/decade **✓**
(c) −20 dB/decade below 2 rad/s, then +40 dB/decade（漏掉原点极点在高频段的贡献）
(d) −20 dB/decade below 2 rad/s, then 0 dB/decade（漏掉二重零点）

> [!success] Answer（答案）
> (b) 2 rad/s 以下为 $-20$ dB/decade，之后为 $+20$ dB/decade

> [!abstract] 知识点讲解
> 见 [[信号与系统/Quiz对应知识点.md|Quiz对应知识点]] 4.4 Bode 图 与 8.1 传递函数。
>
> - **Bode 斜率规则**：每个极点贡献 $-20$ dB/decade，每个零点贡献 $+20$ dB/decade，重数叠加。
> - **原点极点**：$1/s$ 的极点在原点，使低频段为 $-20$ dB/decade。
> - **转折频率**：由各极零点到原点的距离 $|p|$、$|z|$ 给出（一阶因子在 $\omega=|p|$ 或 $|z|$ 处转折；二阶共轭极点对的转折频率为 $\omega_n=|p|$）。
> - **通分**：$G(s)=\dfrac{(s+2)^2}{4s}$，一个原点极点、一个二重零点。

> [!example] 解答
> 通分：
> $$G(s)=\frac{4s+s^2+4}{4s}=\frac{s^2+4s+4}{4s}
> =\frac{(s+2)^2}{4s}.$$
> 极零点分布：
> - $s=0$ 处一个极点；
> - $s=-2$ 处一个**二重零点**。
>
> 低频段：只看到原点极点，斜率 $-20$ dB/dec。
>
> 经过 $\omega=2$：二重零点使斜率增加 $2\times20=40$ dB/dec，变为
> $$-20+40=+20\ \mathrm{dB/dec}.$$
> 选 (b)。

---

### 39. Question 39（第 39 题）^q39

A filter（某滤波器）

$$
G(s)=K\frac{s+z}{s+5}
$$

has DC gain $1$ and must have a high-frequency gain of $-30$ dB. Where must the zero be? Give $z$ in rad/s (the zero is at $s=-z$).（要求直流增益为 $1$，高频增益为 $-30$ dB。零点应放在哪里？给出 $z$，单位 rad/s。）

> [!success] Answer（答案）
> $z=158.1$ rad/s

> [!abstract] 知识点讲解
> 见 [[信号与系统/Quiz对应知识点.md|Quiz对应知识点]] 8.1 传递函数 与 4.4 Bode 图。
>
> - **直流增益**：$G(0)=\displaystyle\lim_{s\to0}K\dfrac{z}{5}$。
> - **高频增益**：$\displaystyle\lim_{s\to\infty}G(s)=K$（同阶时等于系数比）。
> - **dB 换算**：$-30$ dB 对应 $K=10^{-30/20}$。
> - **零点位置**：$s=-z$，$z$ 同时决定转折频率与低频到高频的抬升量。

> [!example] 解答
> 低频极限：
> $$G(0)=K\frac{z}{5}=1\quad\Longrightarrow\quad Kz=5.$$
> 高频极限：
> $$\lim_{s\to\infty}G(s)=K=10^{-30/20}=0.03162.$$
> 由 $Kz=5$：
> $$z=\frac{5}{K}=\frac{5}{0.03162}=158.1\ \mathrm{rad/s}.$$
> 检查：高频增益 $-20\log_{10}K=-20\log_{10}0.03162=30$ dB 的衰减，即 $-30$ dB。

---

### 40. Question 40（第 40 题）^q40

A 50 Hz hum notch filter is（50 Hz 工频陷波器为）

$$
G(s)=\frac{s^2+\omega_n^2}{s^2+2\zeta\omega_ns+\omega_n^2},
\qquad \omega_n=2\pi\cdot50\ \mathrm{rad/s},\quad \zeta=0.5.
$$

Find $\left|G(j\omega)\right|$ at 25 Hz.（求 25 Hz 处的幅值。）

> [!success] Answer（答案）
> $|G|=0.8321$

> [!abstract] 知识点讲解
> 见 [[信号与系统/Quiz对应知识点.md|Quiz对应知识点]] 8.9 互补滤波器与并联相加（Notch 滤波器）。
>
> - **陷波器形式**：$G(s)=\dfrac{s^2+\omega_n^2}{s^2+2\zeta\omega_ns+\omega_n^2}$，在 $\omega=\omega_n$ 处 $|G|=0$。
> - **分母模**：$|s^2+2\zeta\omega_ns+\omega_n^2|_{s=j\omega}=\left(\omega_n^2-\omega^2\right)+j2\zeta\omega_n\omega$。
> - **归一化**：把 $\omega=\omega_n/2$ 代入，分子分母都化为 $\omega_n^2$ 的倍数，便于约分。
> - **比率换算**：$25$ Hz 对应 $\omega=\dfrac{1}{2}\omega_n$。

> [!example] 解答
> 取 $\omega=\omega_n/2$，即 $\omega^2=\omega_n^2/4$。分子：
> $$(j\omega)^2+\omega_n^2=\omega_n^2-\omega^2=\frac34\omega_n^2.$$
> 分母的实部同样为 $\frac34\omega_n^2$，虚部为
> $$2\zeta\omega_n(j\omega)=j2\zeta\frac{\omega_n^2}{2}=j\zeta\omega_n^2=j0.5\omega_n^2.$$
> 所以
> $$G(j\omega_n/2)=\frac{0.75\omega_n^2}{0.75\omega_n^2+j0.5\omega_n^2}
> =\frac{0.75}{0.75+j0.5}.$$
> 取模：
> $$|G|=\frac{0.75}{\sqrt{0.75^2+0.5^2}}
> =\frac{0.75}{\sqrt{0.8125}}=0.8321.$$

---

## 3. Filter design (week 10)（滤波器设计，第 10 周）

Filter specifications and first- and second-order filters（滤波器指标与一、二阶滤波器）

---

### 41. Question 41（第 41 题）^q41

Why can an ideal lowpass filter $G(j\omega)=p_{2\omega_c}(\omega)$ not be built as a real-time circuit?（为什么理想低通滤波器 $G(j\omega)=p_{2\omega_c}(\omega)$ 无法用实时电路实现？）

(a) Its gain is infinite at $\omega_c$（在 $\omega_c$ 处增益无穷大）
(b) Its phase is not linear（相位不是线性的）
(c) Its impulse response $\sin(\omega_ct)/(\pi t)$ is nonzero for $t<0$, so it is noncausal **✓**（冲激响应为 $\sin(\omega_ct)/(\pi t)$，在 $t<0$ 时已非零，非因果）
(d) It has a pole in the right half plane（右半平面有极点）

> [!success] Answer（答案）
> (c) 冲激响应在 $t<0$ 时非零，非因果

> [!abstract] 知识点讲解
> 见 [[信号与系统/Quiz对应知识点.md|Quiz对应知识点]] 8.3 理想低通滤波器。
>
> - **因果性判据**：实时系统的冲激响应必须满足 $h(t)=0$（$t<0$）。
> - **理想低通频响**：$G(j\omega)=p_{2\omega_c}(\omega)$，截止频率 $\omega_c$。
> - **求冲激响应**：冲激响应 $h(t)$ 是频响 $G(j\omega)$ 的傅里叶反变换，$\mathcal F^{-1}\{p_{2\omega_c}(\omega)\}=\dfrac{\sin\omega_ct}{\pi t}$，由傅里叶变换对 $\dfrac{\sin Wt}{\pi t}\leftrightarrow p_{2W}(\omega)$ 取 $W=\omega_c$。
> - **性质**：幅值有界（$0$ 或 $1$），相位为零（线性），非有理函数，无极点；但冲激响应向 $t<0$ 延伸，非因果。

> [!example] 解答
> 判断因果性要看冲激响应 $h(t)$，而 $h(t)$ 是频响 $G(j\omega)$ 的傅里叶反变换：
> $$h(t)=\mathcal F^{-1}\{G(j\omega)\}=\frac{1}{2\pi}\int_{-\infty}^{\infty}G(j\omega)e^{j\omega t}\,d\omega.$$
> 这里 $G(j\omega)=p_{2\omega_c}(\omega)$ 是矩形窗：$|\omega|<\omega_c$ 时等于 $1$，其余频率等于 $0$。所以无限区间的积分只剩 $[-\omega_c,\omega_c]$ 这一段：
> $$h(t)=\frac{1}{2\pi}\int_{-\omega_c}^{\omega_c}1\cdot e^{j\omega t}\,d\omega.$$
> 对 $\omega$ 积分（$t$ 当作常数）：
> $$\int e^{j\omega t}\,d\omega=\frac{e^{j\omega t}}{jt},$$
> 代入上下限：
> $$h(t)=\frac{1}{2\pi}\cdot\frac{e^{j\omega_ct}-e^{-j\omega_ct}}{jt}.$$
> 再用欧拉公式 $\sin a=\dfrac{e^{ja}-e^{-ja}}{2j}$，把 $a=\omega_ct$ 代入：
> $$h(t)=\frac{1}{2\pi}\cdot\frac{2j\sin\omega_ct}{jt}
> =\frac{\sin\omega_ct}{\pi t}.$$
> 对任意 $t<0$，$h(t)$ 一般不恒为零，所以系统在输入加之前已有输出，非因果。
>
> 理想低通只能作为理论模型，实际电路只能用有理传递函数逼近它。选 (c)。

---

### 42. Question 42（第 42 题）^q42

At the $-3$ dB frequency of a first-order RC lowpass, compared with DC, the output（一阶 RC 低通在 $-3$ dB 频率处，与直流相比，输出）

(a) amplitude is $1/2$ and power is $1/4$（幅值 $1/2$、功率 $1/4$）
(b) amplitude is $1/\sqrt2$ and power is $1/2$ **✓**（幅值 $1/\sqrt2$、功率 $1/2$）
(c) amplitude and power are both $0.7$（幅值和功率都约为 $0.7$）
(d) amplitude is $1/2$ and power is $1/\sqrt2$（幅值 $1/2$、功率 $1/\sqrt2$）

> [!success] Answer（答案）
> (b) 幅值 $1/\sqrt2$，功率 $1/2$

> [!abstract] 知识点讲解
> 见 [[信号与系统/Quiz对应知识点.md|Quiz对应知识点]] 8.4 $-3$ dB 截止频率 与 4.4 Bode 图。
>
> - **dB 定义**：$20\log_{10}|G|$，$-3$ dB $\iff|G|=10^{-3/20}=\dfrac{1}{\sqrt2}$。
> - **精确换算**：$20\log_{10}\dfrac{1}{\sqrt2}=-10\log_{10}2\approx-3.01$ dB。
> - **功率比例**：功率 $\propto|G|^2$，$|G|^2=\dfrac12$ 对应功率减半。
> - **对照**：$|G|=\dfrac12$ 对应 $-6$ dB。


> [!example] 解答
> 一阶 RC 低通的直流增益为 $1$，「与直流相比」就是比较 $\omega=0$ 与 $\omega=\omega_c$ 两处的幅值。一阶低通的幅频为
> $$|G(j\omega)|=\frac{1}{\sqrt{1+\left(\omega/\omega_c\right)^2}}.$$
> 在 $\omega=\omega_c$ 处：
> $$|G(j\omega_c)|=\frac{1}{\sqrt{1+1}}=\frac{1}{\sqrt2}.$$
> 所以幅值降到直流的 $1/\sqrt2$，不是 $1/2$。
>
> 分贝的定义是
> $$A_{\mathrm{dB}}=20\log_{10}|G|.$$
> 截止频率处：
> $$20\log_{10}\frac{1}{\sqrt2}
> =20\log_{10}\left(2^{-1/2}\right)
> =-10\log_{10}2
> \approx-3.01\ \mathrm{dB}.$$
> 这就是「$-3$ dB 频率」这个名称的来源。
>
> 电阻上的功率 $P=U^2/(2R)$，在输入相同的条件下 $P\propto|G|^2$。所以
> $$\frac{P_c}{P_0}=|G(j\omega_c)|^2=\left(\frac{1}{\sqrt2}\right)^2=\frac12.$$
> 功率降到直流时的一半。
>
> (a) 把幅值说成 $1/2$，那样是 $-6$ dB，功率会变成 $1/4$；(c) 把幅值和功率都写成 $0.7$，但功率比应为 $0.5$；(d) 幅值写成 $1/2$，也不对。选 (b)。

---

### 43. Question 43（第 43 题）^q43

Which transfer function is a bandpass filter?（哪个传递函数是带通滤波器？）

(a) $\dfrac{10s}{s^2+10s+100}$ **✓**
(b) $\dfrac{100}{s^2+10s+100}$
(c) $\dfrac{s^2+100}{s^2+10s+100}$
(d) $\dfrac{s^2}{s^2+10s+100}$

> [!success] Answer（答案）
> (a) $\dfrac{10s}{s^2+10s+100}$

> [!abstract] 知识点讲解
> 见 [[信号与系统/Quiz对应知识点.md|Quiz对应知识点]] 8.2 典型滤波器 与 10.6 传递函数与滤波器。
>
> - **滤波器分类判据**：看 $\omega=0$ 与 $\omega\to\infty$ 两端增益。
> - **低通**：$G(0)\ne0$、$G(\infty)=0$；**高通**：$G(0)=0$、$G(\infty)\ne0$。
> - **带通**：两端都为零，中间通；**带阻**：两端都非零，中间有零点。
> - **分子阶数**：分子含 $s$ 因子 ⇒ $G(0)=0$；分子分母同阶 ⇒ 高频有限非零。

> [!example] 解答
> **判据**：低通看 $G(0)\ne0$、$G(j\infty)=0$；高通看 $G(0)=0$、$G(j\infty)\ne0$；带通看两端都为 $0$、中间有峰值；带阻看两端都不为 $0$、中间有零点。四个选项的分母相同，都是 $s^2+10s+100$，区别只在分子。
>
> **逐项代入两端。**
>
> (a) $G(s)=\dfrac{10s}{s^2+10s+100}$：
> $$G(0)=\frac{0}{100}=0,\qquad G(j\infty)=0\ (\text{分子一次、分母二次}),$$
> 两端都为零，是带通。再看中间 $\omega=10$ 处（$\omega_n=\sqrt{100}=10$）：
> $$G(j10)=\frac{10\cdot j10}{(j10)^2+10\cdot j10+100}
> =\frac{j100}{-100+j100+100}=\frac{j100}{j100}=1,$$
> 中间增益为 $1$，确实是带通。
>
> (b) $G(s)=\dfrac{100}{s^2+10s+100}$：
> $$G(0)=\frac{100}{100}=1,\qquad G(j\infty)=0,$$
> 低频通、高频阻，是低通。
>
> (c) $G(s)=\dfrac{s^2+100}{s^2+10s+100}$：
> $$G(0)=\frac{100}{100}=1,\qquad G(j\infty)=1,$$
> 两端都为 $1$，中间 $\omega=10$ 处分母为 $j100$、分子为 $0$，是带阻（陷波）。
>
> (d) $G(s)=\dfrac{s^2}{s^2+10s+100}$：
> $$G(0)=\frac{0}{100}=0,\qquad G(j\infty)=1,$$
> 低频阻、高频通，是高通。
>
> 只有 (a) 两端为零，选 (a)。

---

### 44. Question 44（第 44 题）^q44

Find the $-3$ dB frequency of the second-order lowpass（求二阶低通的 $-3$ dB 频率）

$$
G(s)=\frac{400}{s^2+20s+400},
$$

in rad/s.

> [!success] Answer（答案）
> $25.44$ rad/s

> [!abstract] 知识点讲解
> 见 [[信号与系统/Quiz对应知识点.md|Quiz对应知识点]] 5.6 二阶低通的 $-3$ dB 频率。
>
> - **二阶标准形**：$G(s)=\dfrac{\omega_n^2}{s^2+2\zeta\omega_ns+\omega_n^2}$。
> - **幅频平方**：$|G(j\omega)|^2=\dfrac{1}{(1-x)^2+(2\zeta)^2x}$，其中 $x=\left(\dfrac{\omega}{\omega_n}\right)^2$。
> - **半功率条件**：$|G|^2=\dfrac12$，化为 $x$ 的二次方程后取正根。
> - **截止频率**：$\omega_c=\omega_n\sqrt{x}$，一般不等于 $\omega_n$。

> [!example] 解答
> 与标准形
> $$G(s)=\frac{\omega_n^2}{s^2+2\zeta\omega_ns+\omega_n^2}$$
> 对照：常数项 $400=\omega_n^2$，所以 $\omega_n=20$；一次项 $20=2\zeta\omega_n$，所以
> $$\zeta=\frac{20}{2\times20}=0.5.$$
>
> 代入 $s=j\omega$：
> $$G(j\omega)=\frac{400}{(j\omega)^2+20j\omega+400}
> =\frac{400}{400-\omega^2+j20\omega}.$$
> 分部取模。分子模为 $400$；分母模的平方为
> $$\left(400-\omega^2\right)^2+\left(20\omega\right)^2.$$
> 所以
> $$|G(j\omega)|^2=\frac{400^2}{\left(400-\omega^2\right)^2+\left(20\omega\right)^2}.$$
>
> 上下同除以 $400^2=160000$。定义 $x=(\omega/20)^2=\omega^2/400$：
> $$\left(\frac{400-\omega^2}{400}\right)^2=(1-x)^2,
> \qquad
> \left(\frac{20\omega}{400}\right)^2=\left(\frac{\omega}{20}\right)^2=x,$$
> 于是
> $$|G(j\omega)|^2=\frac{1}{(1-x)^2+x}=\frac{1}{x^2-x+1}.$$
>
> $-3$ dB 即 $|G|^2=1/2$：
> $$\frac{1}{x^2-x+1}=\frac12\quad\Longrightarrow\quad x^2-x+1=2
> \quad\Longrightarrow\quad x^2-x-1=0.$$
> 求根公式：
> $$x=\frac{1\pm\sqrt{1+4}}{2}=\frac{1\pm\sqrt5}{2}.$$
> $x$ 必须为正，取加号：
> $$x=\frac{1+\sqrt5}{2}=1.618.$$
>
> $$\omega_c=\omega_n\sqrt{x}=20\sqrt{1.618}=20\times1.272=25.44\ \mathrm{rad/s}.$$
> 注意 $\omega_c\ne\omega_n$：一阶时二者相等，二阶开始与 $\zeta$ 有关，本题 $\zeta=0.5$ 时截止频率被抬到 $\omega_n$ 之上。

---

### 45. Question 45（第 45 题）^q45

A first-order highpass（一阶高通）

$$
G(s)=\frac{s}{s+\omega_c},
\qquad \omega_c=2\pi\cdot100\ \mathrm{rad/s}
$$

is used to suppress a 50 Hz hum. By how many dB is the 50 Hz hum attenuated? (Give a positive number.)（用来抑制 50 Hz 工频噪声。50 Hz 分量被衰减多少 dB？给正数。）

> [!success] Answer（答案）
> $6.990$ dB

> [!abstract] 知识点讲解
> 见 [[信号与系统/Quiz对应知识点.md|Quiz对应知识点]] 8.6 例 4（一阶高通在低频的衰减）。
>
> - **一阶高通**：$G(s)=\dfrac{s}{s+\omega_c}$，幅频 $|G(j\omega)|=\dfrac{\omega/\omega_c}{\sqrt{1+(\omega/\omega_c)^2}}$。
> - **频率比**：用 $f/f_c=\omega/\omega_c$ 计算，两边的 $2\pi$ 约掉。
> - **衰减量**：$A=-20\log_{10}|G|$ dB。
> - **低频渐近**：$\omega\ll\omega_c$ 时 $|G|\approx\omega/\omega_c$，按每十倍频程 $20$ dB 上升。

> [!example] 解答
> 把 $s=j\omega$ 代入：
> $$G(j\omega)=\frac{j\omega}{j\omega+\omega_c}.$$
> 分子模为 $\omega$，分母模为 $\sqrt{\omega^2+\omega_c^2}$，所以
> $$|G(j\omega)|=\frac{\omega}{\sqrt{\omega^2+\omega_c^2}}
> =\frac{\omega/\omega_c}{\sqrt{1+\left(\omega/\omega_c\right)^2}}.$$
>
> 截止频率 $100$ Hz，信号 $50$ Hz，两边的 $2\pi$ 在比值中约掉：
> $$\frac{f}{f_c}=\frac{50}{100}=0.5\quad\Longrightarrow\quad\frac{\omega}{\omega_c}=0.5.$$
>
> $$|G|=\frac{0.5}{\sqrt{1+0.5^2}}=\frac{1/2}{\sqrt{5/4}}=\frac{1/2}{\sqrt5/2}=\frac{1}{\sqrt5}=0.4472.$$
>
> 衰减量定义为 $A=-20\log_{10}|G|$ 且取正数：
> $$A=-20\log_{10}\frac{1}{\sqrt5}=20\log_{10}\sqrt5=10\log_{10}5=6.990\ \mathrm{dB}.$$
> 直观检查：$\omega\ll\omega_c$ 时 $|G|\approx\omega/\omega_c=0.5$，对应约 $-6$ dB；精确值 $0.447$ 略小，对应 $6.99$ dB，两者量级一致。

---

### 46. Question 46（第 46 题）^q46

A first-order lowpass（一阶低通）

$$
G(s)=\frac{k}{s+a},
\qquad k,a>0
$$

must have DC gain $+12$ dB and a gain 3 dB below the DC gain at $f=1$ kHz. Find $k$ (units rad/s).（要求直流增益为 $+12$ dB，且在 $f=1$ kHz 处比直流增益低 3 dB。求 $k$，单位 rad/s。）

> [!success] Answer（答案）
> $k=2.501\times10^4$ rad/s

> [!abstract] 知识点讲解
> 见 [[信号与系统/Quiz对应知识点.md|Quiz对应知识点]] 8.8 由指标反求参数。
>
> - **一阶低通标准形**：$G(s)=\dfrac{k}{s+a}$。
> - **直流增益**：$G(0)=\dfrac{k}{a}$。
> - **$-3$ dB 频率**：由 $|G(j\omega_c)|=\dfrac{|G(0)|}{\sqrt2}$ 得 $\omega_c=a$。
> - **dB 定义**：$A_{\mathrm{dB}}=20\log_{10}|G|$，反解得 $|G|=10^{A_{\mathrm{dB}}/20}$。
> - **角频率换算**：$\omega_c=2\pi f_c$。
> - **反求参数**：先由 $\dfrac{k}{a}=10^{A_{\mathrm{dB}}/20}$ 得 $k/a$，再由 $a=\omega_c$ 得 $k=a\cdot10^{A_{\mathrm{dB}}/20}$。

> [!example] 解答
> 直流就是 $s=0$：
> $$G(0)=\frac{k}{a}.$$
> $+12$ dB 的含义是 $20\log_{10}\dfrac{k}{a}=12$，即
> $$\frac{k}{a}=10^{12/20}=10^{0.6}=3.981.$$
>
> 一阶低通
> $$|G(j\omega)|=\frac{k}{\sqrt{\omega^2+a^2}}.$$
> 根据题目条件，比直流低 $3$ dB 的点就是 $|G(j\omega)|=|G(0)|/\sqrt2$ 的点，条件化为
> $$\frac{k}{\sqrt{\omega^2+a^2}}=\frac{k/a}{\sqrt2}
> \quad\Longrightarrow\quad\sqrt{\omega^2+a^2}=\sqrt2\,a
> \quad\Longrightarrow\quad\omega=a.$$
> 根据 $-3$ dB 的定义，比直流增益小3db位置的频率就是截止频率；且对照关于低通滤波器的一般公式也可以发现 $\omega_c=a$。题给 $f_c=1$ kHz：
> $$a=2\pi\times1000=6283\ \mathrm{rad/s}.$$
>
> $$k=3.981\times6283=2.501\times10^4\ \mathrm{rad/s}.$$
> 两个条件分别定出 $a$（决定转折频率）和 $k/a$（决定整体高度），$k$ 就是二者相乘。

---

### 47. Question 47（第 47 题）^q47

Which transfer function is an exponentially stable allpass filter ($|G(j\omega)|=1$ for all $\omega$)?（哪个传递函数是指数稳定的全通滤波器，即对所有 $\omega$ 都有 $|G(j\omega)|=1$？）

(a) $\dfrac{s}{s+3}$（一阶高通）
(b) $\dfrac{3}{s+3}$（一阶低通）
(c) $\dfrac{s+3}{s-3}$（幅值为 $1$，但极点 $+3$ 不稳定）
(d) $\dfrac{s-3}{s+3}$ **✓**（极点 $-3$、零点 $+3$，指数稳定全通）

> [!success] Answer（答案）
> (d) $\dfrac{s-3}{s+3}$

> [!abstract] 知识点讲解
> 见 [[信号与系统/Quiz对应知识点.md|Quiz对应知识点]] 8.2 典型滤波器（全通在某一频率的相位）。
>
> - **一阶全通标准形**：$G(s)=\dfrac{s-a}{s+a}$。
> - **幅频**：$|G(j\omega)|=\dfrac{|j\omega-a|}{|j\omega+a|}=1$。
> - **极点**：$s=-a$。
> - **稳定条件**：$\operatorname{Re}p<0$，即 $a>0$。
> - **判定**：$|G(j\omega)|\equiv1$ 且所有极点在开左半平面。

> [!example] 解答
> 先明确两个条件：「全通」指对所有 $\omega$ 都有 $|G(j\omega)|=1$；「指数稳定」指所有极点的实部小于 $0$（在开左半平面）。四个选项要同时满足这两条。
>
> 逐项检查。
>
> (a) $G(s)=\dfrac{s}{s+3}$：分子模为 $\omega$，分母模为 $\sqrt{\omega^2+9}$，
> $$|G(j\omega)|=\frac{\omega}{\sqrt{\omega^2+9}},$$
> 在 $\omega=3$ 处为 $\dfrac{3}{\sqrt{18}}=\dfrac{1}{\sqrt2}\ne1$，不是全通。它其实是高通：$G(0)=0$、$G(j\infty)=1$。
>
> (b) $G(s)=\dfrac{3}{s+3}$：
> $$|G(j\omega)|=\frac{3}{\sqrt{\omega^2+9}},$$
> $\omega=0$ 时为 $1$，$\omega\to\infty$ 时为 $0$，是低通，不是全通。
>
> (c) $G(s)=\dfrac{s+3}{s-3}$：模确实为 $1$，
> $$|G(j3)|=\frac{|3+j3|}{|-3+j3|}=\frac{3\sqrt2}{3\sqrt2}=1,$$
> 但它的极点是 $s=3$，在右半平面，系统不稳定，不满足第二条。
>
> (d) $G(s)=\dfrac{s-3}{s+3}$：极点为 $s=-3$，在左半平面，指数稳定。再看模：
> $$|G(j\omega)|=\frac{|j\omega-3|}{|j\omega+3|}
> =\frac{\sqrt{\omega^2+9}}{\sqrt{\omega^2+9}}=1,$$
> 对任意 $\omega$ 成立（分子分母只是 $j\omega$ 的符号不同，模一样），是全通。
>
> 只有 (d) 同时满足全通与稳定，选 (d)。

---

### 48. Question 48（第 48 题）^q48

The allpass filter（全通滤波器）

$$
G(s)=\frac{10-s}{s+10}
$$

is driven by the input $u(t)=\cos(10t)$, applied for all time. The output is（输入为全时间存在的 $u(t)=\cos(10t)$。输出为）

(a) $-\cos(10t)$（用了高频相位 $-180^\circ$）
(b) $\cos(10t)$（相位错当成 $0$）
(c) $\sin(10t)$ **✓**（正确结果）
(d) $-\sin(10t)$（把 $-90^\circ$ 的相移符号弄错）

> [!success] Answer（答案）
> (c) $\sin(10t)$

> [!abstract] 知识点讲解
> 见 [[信号与系统/Quiz对应知识点.md|Quiz对应知识点]] 8.2 典型滤波器（全通在某一频率的相位） 与 4.1 正弦稳态的核心结论。
>
> - **正弦稳态**：$u=A\cos\omega t$ 时 $y=A|G(j\omega)|\cos\left(\omega t+\angle G(j\omega)\right)$。
> - **全通特性**：$|G(j\omega)|=1$，只改变相位。
> - **复数计算**：分子分母同乘共轭，写成 $x+jy$ 后取模和辐角。
> - **相位移动**：$\cos(\theta-90^\circ)=\sin\theta$。

> [!example] 解答
> 代入 $\omega=10$：
> $$G(j10)=\frac{10-10j}{10+10j}.$$
> 化简：分子、分母分别提取 $10$，
> $$G(j10)=\frac{1-j}{1+j}=\frac{(1-j)^2}{(1+j)(1-j)}
> =\frac{1-2j+j^2}{2}=\frac{-2j}{2}=-j.$$
> 模为 $1$，相位为 $-90^\circ$。输出：
> $$y(t)=|G(j10)|\cos\left(10t+\angle G(j10)\right)
> =\cos\left(10t-90^\circ\right)=\sin10t.$$
> 选 (c)。

---

### 49. Question 49（第 49 题）^q49

The system（系统）

$$
y(t)=u(t-2)
$$

has transfer function $G(s)=e^{-2s}$. Which describes its frequency response?（其传递函数为 $G(s)=e^{-2s}$。其频率响应如何描述？）

(a) It has a pole at $s=-2$, so $|G|$ falls at $-20$ dB/decade above 2 rad/s（误以为有极点）
(b) $|G(j\omega)|=1$ and $\angle G(j\omega)=-2\omega$ rad: an allpass **✓**（幅值恒为 $1$，相位为 $-2\omega$，是全通系统）
(c) $|G(j\omega)|=e^{-2\omega}$: a lowpass（误把 $j$ 当成 $1$）
(d) $|G(j\omega)|=1$ and $\angle G(j\omega)=-2$ rad at all $\omega$（误以为相位恒定）

> [!success] Answer（答案）
> (b) $|G(j\omega)|=1$，$\angle G(j\omega)=-2\omega$ rad，是全通系统

> [!abstract] 知识点讲解
> 见 [[信号与系统/Quiz对应知识点.md|Quiz对应知识点]] 8.2 典型滤波器（延迟线）。
>
> - **时移**：$y(t)=u(t-T)$ 的传递函数 $G(s)=e^{-sT}$。
> - **频率响应**：$G(j\omega)=e^{-j\omega T}=1\angle(-\omega T)$。
> - **幅频**：$|G(j\omega)|=1$。
> - **相频**：$\angle G(j\omega)=-\omega T$，与频率成正比。
> - **极点**：$e^{-sT}$ 不是有理函数，没有极点。

> [!example] 解答
> 代入 $s=j\omega$：
> $$G(j\omega)=e^{-j2\omega}.$$
> 模：
> $$\left|e^{-j2\omega}\right|=1.$$
> 相位：
> $$\angle G(j\omega)=-2\omega.$$
> 幅度不变，只引入与频率成正比的相位延迟，相当于延迟 $2$ s，是全通系统。选 (b)。

---

### 50. Question 50（第 50 题）^q50

Lowpass to highpass, bandpass and bandstop（低通到高通、带通与带阻的变换）

The normalized Butterworth prototype（归一化 Butterworth 低通原型）

$$
G_{LP}(s)=\frac{1}{s^2+\sqrt2\,s+1}
$$

has cutoff $1$ rad/s. Replacing $s$ by $50/s$ gives（截止频率为 $1$ rad/s。把 $s$ 换成 $50/s$ 后得到）

(a) $\dfrac{s^2}{s^2+1.414s+2500}$（中间项没有随 $50$ 缩放）
(b) $\dfrac{s^2}{s^2+70.71s+2500}$ **✓**
(c) $\dfrac{s^2}{s^2+70.71s+50}$（常数项应为 $50^2$）
(d) $\dfrac{2500}{s^2+70.71s+2500}$（这是截止频率 $50$ rad/s 的低通）

> [!success] Answer（答案）
> (b) $\dfrac{s^2}{s^2+70.71s+2500}$

> [!abstract] 知识点讲解
> 见 [[信号与系统/Quiz对应知识点.md|Quiz对应知识点]] 8.7 例 2（Butterworth 原型到高通） 与 8.5 Butterworth 滤波器。
>
> - **二阶 Butterworth 低通原型**：$G_{LP}(s)=\dfrac{1}{s^2+\sqrt2\,s+1}$，$\omega_c=1$。
> - **低通到高通变换**：把原型中的 $s$ 换成 $\dfrac{\omega_c}{s}$。
> - **分母展开**：$1+\dfrac{\sqrt2\,\omega_c}{s}+\dfrac{\omega_c^2}{s^2}$。
> - **整理**：分子分母同乘 $s^2$，得 $\dfrac{s^2}{s^2+\sqrt2\,\omega_cs+\omega_c^2}$。

> [!example] 解答
> 低通原型 $G_{LP}(s)$ 是把 $s$ 换成 $\dfrac{\omega_c}{s}$ 得到高通的：
> $$G_{HP}(s)=G_{LP}\!\left(\frac{\omega_c}{s}\right),\qquad \omega_c=50.$$
>
> 原型
> $$G_{LP}(s)=\frac{1}{s^2+\sqrt2\,s+1}.$$
> 分母两项分别替换：
> $$s^2\ \longrightarrow\ \left(\frac{50}{s}\right)^2=\frac{2500}{s^2},
> \qquad
> \sqrt2\,s\ \longrightarrow\ \sqrt2\cdot\frac{50}{s}=\frac{50\sqrt2}{s},$$
> 所以
> $$G_{HP}(s)=\frac{1}{\dfrac{2500}{s^2}+\dfrac{50\sqrt2}{s}+1}.$$
>
> $$G_{HP}(s)=\frac{s^2}{s^2+50\sqrt2\,s+2500}.$$
> 注意常数项 $50^2$ 来自 $s^2$ 那一项，这也是 (c) 写成 $50$ 的错误所在。
>
> $$50\sqrt2=70.71,\qquad 50^2=2500.$$
>
> $s\to0$ 时分子 $s^2\to0$，$G\to0$；$s\to\infty$ 时分子分母同阶，$G\to1$。低频阻、高频通，确实是高通。另外 (a) 的中间项没有跟着 $50$ 缩放，(d) 分子是 $2500$，那是截止频率 $50$ rad/s 的低通而不是高通。选 (b)。

---

### 51. Question 51（第 51 题）^q51

In a two-way loudspeaker crossover, the tweeter (a $4\ \Omega$ resistor) is fed through a series capacitor $C$, giving the highpass
（在二分频音箱中，高音单元（$4\ \Omega$ 电阻）串联电容 $C$，得到高通）

$$
G_H(s)=\frac{4Cs}{4Cs+1}.
$$

Find $C$ in $\mu$F so the $-3$ dB frequency is 3 kHz.（求使 $-3$ dB 频率为 3 kHz 的电容值，单位 $\mu$F。）

> [!success] Answer（答案）
> $C=13.26\ \mu$F

> [!abstract] 知识点讲解
> 见 [[信号与系统/Quiz对应知识点.md|Quiz对应知识点]] 8.4 $-3$ dB 截止频率 与 8.2 典型滤波器。
>
> - **一阶高通标准形**：$G_H(s)=\dfrac{s}{s+\omega_c}$。
> - **截止频率**：$\omega_c$ 就是极点的绝对值。
> - **角频率换算**：$\omega_c=2\pi f_c$。
> - **反解电容**：在 $RC$ 高通中 $\omega_c=\dfrac{1}{RC}$，所以 $C=\dfrac{1}{R\omega_c}$。

> [!example] 解答
> 分子分母同除以 $4C$：
> $$G_H(s)=\frac{s}{s+\dfrac{1}{4C}}.$$
> 与一阶高通标准形 $\dfrac{s}{s+\omega_c}$ 对照，读出
> $$\omega_c=\frac{1}{4C}.$$
>
> 幅频为
> $$|G_H(j\omega)|=\frac{\omega}{\sqrt{\omega^2+\omega_c^2}},$$
> 在 $\omega=\omega_c$ 处等于 $\dfrac{1}{\sqrt2}$，而 $\omega\to\infty$ 时趋于 $1$，所以 $-3$ dB 频率正是 $\omega_c$。
>
> $f_c=3$ kHz，先换成角频率：
> $$\omega_c=2\pi\times3000=18849.6\ \mathrm{rad/s}.$$
> 由 $\omega_c=\dfrac{1}{4C}$：
> $$C=\frac{1}{4\omega_c}=\frac{1}{4\times18849.6}=\frac{1}{75398.2}.$$
>
> $$C=1.326\times10^{-5}\ \mathrm{F}=13.26\ \mu\mathrm{F}.$$
> （$1\ \mu\mathrm{F}=10^{-6}\ \mathrm{F}$。）

---

### 52. Question 52（第 52 题）^q52

A bandstop filter is built as the parallel sum of a first-order lowpass and a first-order highpass（带阻滤波器由一阶低通与一阶高通并联相加构成）：

$$
G(s)=\frac{10}{s+10}+\frac{s}{s+1000}.
$$

Find $|G(j100)|$.（求 $|G(j100)|$。）

> [!success] Answer（答案）
> $|G(j100)|=0.01980$

> [!abstract] 知识点讲解
> 见 [[信号与系统/Quiz对应知识点.md|Quiz对应知识点]] 8.2 典型滤波器 与 0.1 复数与相量。
>
> - **并联（相加）**：$G=G_1+G_2$，先分别化成 $x+jy$ 再相加。
> - **有理化**：$\dfrac{a}{b+jc}=\dfrac{a(b-jc)}{b^2+c^2}$。
> - **分成实部虚部**：$\dfrac{a}{b+jc}=\dfrac{ab}{b^2+c^2}-j\dfrac{ac}{b^2+c^2}$。
> - **取模**：$|G|=\sqrt{\operatorname{Re}^2G+\operatorname{Im}^2G}$。


> [!example] 解答
> 先把两项各自约掉公因子，让数字变小。
>
> 第一项，分子分母同除以 $10$：
> $$\frac{10}{j100+10}=\frac{1}{1+j10}.$$
> 第二项，分子分母同除以 $100$：
> $$\frac{j100}{j100+1000}=\frac{j}{10+j}.$$
>
> 再分别有理化：
> $$\frac{1}{1+j10}=\frac{1-j10}{(1+j10)(1-j10)}=\frac{1-j10}{1+100}=\frac{1-j10}{101},$$
> $$\frac{j}{10+j}=\frac{j(10-j)}{(10+j)(10-j)}=\frac{10j-j^2}{100+1}=\frac{1+10j}{101}.$$
>
> 相加，虚部正好抵消：
> $$G(j100)=\frac{1-j10}{101}+\frac{1+10j}{101}=\frac{2}{101}=0.019802.$$
> 和为实数，所以
> $$|G(j100)|=0.01980.$$
>

---

### 53. Question 53（第 53 题）^q53

A first-order lowpass（一阶低通）

$$
G_L(s)=\frac{\omega_c}{s+\omega_c}
$$

and a first-order highpass（和一阶高通）

$$
G_H(s)=\frac{s}{s+\omega_c}
$$

with the same cutoff are connected in parallel and summed, $G=G_L+G_H$. What is $G$?（两者截止频率相同，并联相加，$G=G_L+G_H$。$G$ 是什么？）

(a) A bandstop filter with a notch at $\omega_c$（在 $\omega_c$ 处有陷波的带阻滤波器）
(b) A bandpass filter centered at $\omega_c$（中心在 $\omega_c$ 的带通滤波器）
(c) $|G(j\omega_c)|=\sqrt2$, with unit gain elsewhere（$\omega_c$ 处增益为 $\sqrt2$，其余为 $1$）
(d) $G(s)=1$: every frequency passes unchanged **✓**（$G(s)=1$，所有频率原样通过）

> [!success] Answer（答案）
> (d) $G(s)=1$

> [!abstract] 知识点讲解
> 见 [[信号与系统/Quiz对应知识点.md|Quiz对应知识点]] 8.2 典型滤波器 与 0.1 复数与相量。
>
> - **并联（相加）**：$G=G_L+G_H$。
> - **通分**：$\dfrac{\omega_c}{s+\omega_c}+\dfrac{s}{s+\omega_c}=\dfrac{s+\omega_c}{s+\omega_c}$。
> - **约分**：$G(s)=1$。
> - **全通**：$|G(j\omega)|=|1|=1$，所有频率原样通过。

> [!example] 解答
> 两项分母相同，都是 $s+\omega_c$：
> $$G(s)=\frac{\omega_c}{s+\omega_c}+\frac{s}{s+\omega_c}
> =\frac{\omega_c+s}{s+\omega_c}=1.$$
> 分子恰好等于分母，所以 $G(s)=1$，与 $\omega_c$ 取多少无关。
>
> $G(s)=1$ 不含 $s$，代入 $s=j\omega$ 仍是 $1$：
> $$|G(j\omega)|=1\quad\text{对所有 }\omega.$$
> 这就是「所有频率原样通过」，即全通（而且这里连相位都不改变）。
>
> $$G_L(j\omega_c)=\frac{\omega_c}{\omega_c+j\omega_c}=\frac{1}{1+j}
> =\frac{1-j}{(1+j)(1-j)}=\frac{1-j}{2},$$
> $$G_H(j\omega_c)=\frac{j\omega_c}{\omega_c+j\omega_c}=\frac{j}{1+j}
> =\frac{j(1-j)}{2}=\frac{j-j^2}{2}=\frac{1+j}{2}.$$
> 两者相加：
> $$G_L(j\omega_c)+G_H(j\omega_c)=\frac{1-j}{2}+\frac{1+j}{2}=\frac{2}{2}=1.$$
> 各自的模都是
> $$|G_L(j\omega_c)|=|G_H(j\omega_c)|=\frac{1}{\sqrt2},$$
> 模相加等于 $\sqrt2$——这正是选项 (c) 犯的错：并联是**复数相加**，不是模相加，虚部抵消后得到 $1$ 而不是 $\sqrt2$。
>
> (a) 要形成陷波，分子必须含 $s^2+\omega_c^2$ 这样的零点，而这里两项相加把分子凑成了分母；(b) 带通要求低频和高频两端都趋于零，这里两端都是 $1$。所以选 (d)。

---

### 54. Question 54（第 54 题）^q54

Butterworth filters and order selection（Butterworth 滤波器与阶数选择）

A second-order lowpass with no zeros has poles at $-10^4\pm j10^4$ rad/s and unit DC gain. It is a Butterworth filter. Find its $-3$ dB cutoff $\omega_c$ in rad/s.

（某无零点的二阶低通极点在 $-10^4\pm j10^4$ rad/s，直流增益为 $1$，且为 Butterworth 滤波器。求其 $-3$ dB 截止频率 $\omega_c$，单位 rad/s。）

> [!success] Answer（答案）
> $\omega_c=1.414\times10^4$ rad/s

> [!abstract] 知识点讲解
> 见 [[信号与系统/Quiz对应知识点.md|Quiz对应知识点]] 8.7 例 3（由极点求二阶 Butterworth 的截止频率） 与 8.5 Butterworth 滤波器。
>
> - **二阶 Butterworth 极点**：$s=\omega_c e^{\pm j135^\circ}$。
> - **极点到原点距离**：$\omega_n=|p|=\sqrt{\operatorname{Re}^2p+\operatorname{Im}^2p}$。
> - **阻尼比**：$\zeta=\dfrac{\left|\operatorname{Re}p\right|}{\omega_n}$。
> - **Butterworth 条件**：$\zeta=\dfrac{1}{\sqrt2}$。
> - **截止频率**：$\omega_c=\omega_n$。

> [!example] 解答
> 无零点、极点为 $p_{1,2}=-10^4\pm j10^4$，所以分母为
> $$(s-p_1)(s-p_2)
> =(s+10^4-j10^4)(s+10^4+j10^4)
> =(s+10^4)^2+(10^4)^2
> =s^2+2\times10^4s+2\times10^8.$$
> 直流增益为 $1$，即 $G(0)=1$，所以分子等于常数项：
> $$G(s)=\frac{2\times10^8}{s^2+2\times10^4s+2\times10^8}.$$
>
> 与标准形 $s^2+2\zeta\omega_ns+\omega_n^2$ 对照：
> $$\omega_n^2=2\times10^8
> \quad\Longrightarrow\quad
> \omega_n=\sqrt2\times10^4\ \mathrm{rad/s},$$
> $$2\zeta\omega_n=2\times10^4
> \quad\Longrightarrow\quad
> \zeta=\frac{2\times10^4}{2\times\sqrt2\times10^4}=\frac{1}{\sqrt2}.$$
> 这与二阶 Butterworth 的 $\zeta=1/\sqrt2$ 相符，说明题目给的极点确实自洽。（几何上极点到原点的距离 $\sqrt{(10^4)^2+(10^4)^2}=\sqrt2\times10^4$，也直接给出 $\omega_n$。）
>
> 一般二阶低通的 $-3$ dB 频率不等于 $\omega_n$（第 44 题 $\zeta=0.5$ 时是 $1.272\omega_n$）；但 Butterworth 恰好把 $\zeta$ 取成 $1/\sqrt2$，使 $\omega=\omega_n$ 时
> $$|G(j\omega_n)|^2=\frac{\omega_n^4}{(\omega_n^2-\omega_n^2)^2+(2\zeta\omega_n^2)^2}
> =\frac{\omega_n^4}{2\omega_n^4}=\frac12,$$
> 正好 $-3$ dB。所以
> $$\omega_c=\omega_n=\sqrt2\times10^4=1.414\times10^4\ \mathrm{rad/s}.$$

---

### 55. Question 55（第 55 题）^q55

A second-order Butterworth lowpass with $f_c=100$ Hz has transfer function（二阶 Butterworth 低通的截止频率为 $100$ Hz，传递函数为）

$$
\frac{\omega_c^2}{s^2+a\,s+\omega_c^2}.
$$

Find $a$ in rad/s.（求 $a$，单位 rad/s。）

> [!success] Answer（答案）
> $a=888.6$ rad/s

> [!abstract] 知识点讲解
> 见 [[信号与系统/Quiz对应知识点.md|Quiz对应知识点]] 8.5 二阶 Butterworth 的特征。
>
> - **二阶 Butterworth 分母**：$s^2+\sqrt2\,\omega_cs+\omega_c^2$。
> - **系数对照**：一次项系数 $a=\sqrt2\,\omega_c$。
> - **常数项**：$\omega_c^2$。
> - **角频率换算**：$\omega_c=2\pi f_c$。
> - **阻尼比**：$a=2\zeta\omega_c\Rightarrow\zeta=\dfrac{1}{\sqrt2}$。

> [!example] 解答
> $$f_c=100\ \mathrm{Hz}\quad\Longrightarrow\quad\omega_c=2\pi\times100=628.3\ \mathrm{rad/s}.$$
> 题目里的 $a$ 是分母一次项的系数，和 $\omega_c$ 一样以 rad/s 为单位，所以必须用角频率而不是 $100$。
>
> $$s^2+\sqrt2\,\omega_cs+\omega_c^2.$$
> 题给分母是 $s^2+a\,s+\omega_c^2$，常数项已经对上了，剩下一项逐系数对照：
> $$a=\sqrt2\,\omega_c.$$
>
> $$a=\sqrt2\times628.3=1.414\times628.3=888.6\ \mathrm{rad/s}.$$
> 也可以用阻尼比核对：$a=2\zeta\omega_c$，而 $\zeta=1/\sqrt2$，得 $a=2\cdot\dfrac{1}{\sqrt2}\omega_c=\sqrt2\,\omega_c$，与上面一致。

---

### 56. Question 56（第 56 题）^q56

A fifth-order Butterworth lowpass has $\omega_c=1000$ rad/s. Find the real part of the pole pair closest to the imaginary axis.（五阶 Butterworth 低通的 $\omega_c=1000$ rad/s。求最靠近虚轴的一对极点的实部。）

> [!success] Answer（答案）
> $-309.0$ rad/s

> [!abstract] 知识点讲解
> 见 [[信号与系统/Quiz对应知识点.md|Quiz对应知识点]] 8.5 极点圆。
>
> - **极点分布**：$n$ 阶 Butterworth 的极点均在半径 $\omega_c$ 的圆上，且位于左半平面。
> - **角度公式**：$\theta_k=90^\circ+\dfrac{180^\circ(2k+1)}{2n}$，$k=0,1,\dots,n-1$。
> - **坐标**：$p_k=\omega_c e^{j\theta_k}=\omega_c\cos\theta_k+j\omega_c\sin\theta_k$。
> - **实部**：$\operatorname{Re}p_k=\omega_c\cos\theta_k$。

> [!example] 解答
> 极点按角度
> $$\theta_k=90^\circ+\frac{180^\circ(2k+1)}{2n},\qquad k=0,1,\dots,n-1$$
> 均匀分布。本题 $n=5$，相邻极点的角度间隔为
> $$\frac{360^\circ}{2n}=\frac{360^\circ}{10}=36^\circ,$$
> 并且这些角度关于实轴对称（它们在右半平面的「搭档」被舍去，只留左半平面那 $n$ 个）。左半平面内的五个角度就是
> $$108^\circ,\ 144^\circ,\ 180^\circ,\ 216^\circ,\ 252^\circ.$$
> （$k=0,1,2,3,4$ 逐个代入：$90^\circ+18^\circ=108^\circ$，$90^\circ+54^\circ=144^\circ$，$90^\circ+90^\circ=180^\circ$，$90^\circ+126^\circ=216^\circ$，$90^\circ+162^\circ=252^\circ$。其中 $180^\circ$ 落在负实轴上，是一个实极点，其余四个两两共轭。）
>
> 极点在半径 $\omega_c=1000$ 的圆上，实部为 $\omega_c\cos\theta$。离虚轴最近 = 实部绝对值最小 = $\theta$ 最接近 $90^\circ$ 或 $270^\circ$。在五个角度中，$108^\circ$ 距 $90^\circ$ 只差 $18^\circ$，是最接近的；$144^\circ$ 距 $90^\circ$ 差 $54^\circ$，更远。与它对称的是 $252^\circ$（$=360^\circ-108^\circ$）。
>
> $$\operatorname{Re}p=\omega_c\cos108^\circ=1000\times(-0.3090)=-309.0\ \mathrm{rad/s}.$$
> 负号表示在左半平面，这是理所应当的。最靠近虚轴意味着衰减最慢、对稳定性最不利的那一对极点，所以这类题常考这一对。
>
> 注意：题目只问「实部」，答案是 $-309.0$；若问虚部则是 $\pm1000\sin108^\circ=\pm951.1$ rad/s，别把两者混淆。

---

### 57. Question 57（第 57 题）^q57

A third-order Butterworth highpass filter with cutoff frequency 100 Hz is used to suppress a 50 Hz hum. By how many dB is the hum attenuated? (Give a positive number.)（三阶 Butterworth 高通截止频率为 100 Hz，用于抑制 50 Hz 工频噪声。50 Hz 分量被衰减多少 dB？给正数。）

> [!success] Answer（答案）
> $18.13$ dB

> [!abstract] 知识点讲解
> 见 [[信号与系统/Quiz对应知识点.md|Quiz对应知识点]] 8.5 阶数与衰减。
>
> - **$n$ 阶 Butterworth 高通幅频平方**：$|G|^2=\dfrac{1}{1+\left(\dfrac{f_c}{f}\right)^{2n}}$。
> - **衰减量**：$A=10\log_{10}\left[1+\left(\dfrac{f_c}{f}\right)^{2n}\right]$。
> - **换算**：$10\log_{10}|G|^2=20\log_{10}|G|$。

> [!example] 解答
> $n$ 阶 Butterworth 低通是
> $$|G|^2=\frac{1}{1+\left(\omega/\omega_c\right)^{2n}},$$
> 把 $\omega$ 换成 $\omega_c^2/\omega$（低通到高通的频率变换）就得到高通：
> $$|G|^2=\frac{1}{1+\left(\dfrac{\omega_c}{\omega}\right)^{2n}}.$$
> 用频率表示（$\omega=2\pi f$，$2\pi$ 约掉）：
> $$|G|^2=\frac{1}{1+\left(\dfrac{f_c}{f}\right)^{2n}}.$$
>
> $f_c=100$ Hz、$f=50$ Hz、$n=3$，所以
> $$\frac{f_c}{f}=\frac{100}{50}=2,\qquad 2n=6,$$
> $$|G|^2=\frac{1}{1+2^6}=\frac{1}{1+64}=\frac{1}{65}.$$
>
> 增益为
> $$20\log_{10}|G|=10\log_{10}|G|^2=10\log_{10}\frac{1}{65}=-18.13\ \mathrm{dB}.$$
> 衰减量取正数：
> $$A=18.13\ \mathrm{dB}.$$
> 也可以直接算 $10\log_{10}65$：$\log_{10}65=\log_{10}6.5+\log_{10}10=0.8129+1=1.8129$，乘 $10$ 得 $18.13$。
>
> 检查量级：$n=3$ 阶在截止频率以下的渐近斜率为每十倍频程 $60$ dB，折合每倍频程 $60\log_{10}2=18.06$ dB；$50$ Hz 正好比 $100$ Hz 低一个倍频程，估算为 $18$ dB，与精确值 $18.13$ dB 吻合。

---

### 58. Question 58（第 58 题）^q58

Two identical second-order Butterworth lowpass sections, each with cutoff $\omega_c$, are cascaded. Which statement about the cascade is correct?（两个相同的二阶 Butterworth 低通节（各截止频率 $\omega_c$）级联。下列关于级联系统的说法哪个正确？）

(a) The gain at $\omega_c$ is $-6.02$ dB, and the cascade is a fourth-order Butterworth filter with cutoff $\omega_c$（增益对，但级联仍是四阶 Butterworth）
(b) The gain at $\omega_c$ is $-3.01$ dB, and the cascade is a fourth-order Butterworth filter with cutoff $\omega_c$（增益与阶数判断都错）
(c) The gain at $\omega_c$ is $-12.04$ dB, and the cascade is not a fourth-order Butterworth filter（增益重复计算了）
(d) The gain at $\omega_c$ is $-6.02$ dB, and the cascade is not a fourth-order Butterworth filter **✓**（增益 $-6.02$ dB，且级联不是四阶 Butterworth）

> [!success] Answer（答案）
> (d) $\omega_c$ 处增益 $-6.02$ dB，级联不是四阶 Butterworth

> [!abstract] 知识点讲解
> 见 [[信号与系统/Quiz对应知识点.md|Quiz对应知识点]] 8.5 级联不是高阶 Butterworth。
>
> - **级联**：$G(s)=G_1(s)G_2(s)$。
> - **幅频**：$|G(j\omega)|=|G_1(j\omega)|\cdot|G_2(j\omega)|$。
> - **dB**：$20\log_{10}|G|=20\log_{10}|G_1|+20\log_{10}|G_2|$。
> - **Butterworth 幅频平方**：$|G(j\omega)|^2=\dfrac{1}{1+\left(\omega/\omega_c\right)^{2n}}$。
> - **极点角度**：$\theta_k=90^\circ+\dfrac{180^\circ(2k+1)}{2n}$。

> [!example] 解答
> 每一节是二阶 Butterworth 低通，在截止频率处的幅频为
> $$|G_1(j\omega_c)|=\frac{\omega_c^2}{\sqrt{\left(\omega_c^2-\omega_c^2\right)^2+\left(\sqrt2\,\omega_c\cdot\omega_c\right)^2}}
> =\frac{\omega_c^2}{\sqrt2\,\omega_c^2}=\frac{1}{\sqrt2}.$$
> 两级级联时幅频相乘：
> $$|G(j\omega_c)|=|G_1(j\omega_c)|\cdot|G_2(j\omega_c)|=\frac{1}{\sqrt2}\cdot\frac{1}{\sqrt2}=\frac12.$$
> 换成 dB：
> $$20\log_{10}\frac12=-20\log_{10}2=-6.02\ \mathrm{dB}.$$
> 也可以这样算：一节是 $-20\log_{10}\sqrt2=-3.01$ dB，两节相加得 $-6.02$ dB。所以 (b)、(c) 的增益数值就已经错了。
>
> 「$n$ 阶 Butterworth」指的是幅频平方满足
> $$|G(j\omega)|^2=\frac{1}{1+\left(\omega/\omega_c\right)^{2n}}$$
> 并且极点在左半平面圆上按等角度分布的那一个特定滤波器。级联系统的幅频是两节平方相乘：
> $$|G_{\text{casc}}|^2=\left(|G_1|^2\right)^2
> =\left[\frac{1}{1+\left(\omega/\omega_c\right)^4}\right]^2
> \ne\frac{1}{1+\left(\omega/\omega_c\right)^8}.$$
> 所以它的幅频形状本身就不是四阶 Butterworth。
>
> 二阶 Butterworth 的两个极点在
> $$\theta=90^\circ+\frac{180^\circ(2k+1)}{4},\quad k=0,1
> \quad\Longrightarrow\quad 135^\circ,\ 225^\circ,$$
> 即 $\omega_c e^{\pm j135^\circ}$。级联后这两个极点各自变成**二重极点**（左上、左下各两个）。
> 而真正的四阶 Butterworth 极点在
> $$\theta=90^\circ+\frac{180^\circ(2k+1)}{8},\quad k=0,1,2,3
> \quad\Longrightarrow\quad 112.5^\circ,\ 157.5^\circ,\ 202.5^\circ,\ 247.5^\circ,$$
> 四个角度互不相同，每个极点都是单极点。极点位置不同，两者不是同一个滤波器。
>
> 所以级联在 $\omega_c$ 处为 $-6.02$ dB，且不是四阶 Butterworth。选 (d)。

---

### 59. Question 59（第 59 题）^q59

A second-order Butterworth highpass has cutoff 6 kHz, so（二阶 Butterworth 高通的截止频率为 6 kHz，因此）

$$
|G(j\omega)|^2=\frac{1}{1+\left(\omega_c/\omega\right)^4}.
$$

At what frequency, in Hz, is its gain $-30$ dB?（在哪个频率处增益为 $-30$ dB？单位 Hz。）

> [!success] Answer（答案）
> $1067$ Hz

> [!abstract] 知识点讲解
> 见 [[信号与系统/Quiz对应知识点.md|Quiz对应知识点]] 8.5 阶数与衰减。
>
> - **二阶 Butterworth 高通幅频平方**：$|G|^2=\dfrac{1}{1+\left(\dfrac{f_c}{f}\right)^{4}}$。
> - **幅度分贝**：$A_{\mathrm{dB}}=20\log_{10}|G|$。
> - **平方关系**：$10\log_{10}|G|^2=20\log_{10}|G|$。
> - **反解**：$1+\left(\dfrac{f_c}{f}\right)^{4}=10^{A/10}$。

> [!example] 解答
> 幅度的分贝定义是
> $$A_{\mathrm{dB}}=20\log_{10}|G|.$$
> 令其等于 $-30$：
> $$20\log_{10}|G|=-30
> \quad\Longrightarrow\quad
> \log_{10}|G|=-1.5
> \quad\Longrightarrow\quad
> |G|=10^{-1.5}.$$
> 两边平方：
> $$|G|^2=10^{-3}=\frac{1}{1000}.$$
> （等价地，$|G|^2$ 的分贝是 $10\log_{10}|G|^2$，令其为 $-30$ 也直接得到 $|G|^2=10^{-3}$，两种算法一致。）
>
> 二阶 Butterworth 高通（$n=2$，$2n=4$）：
> $$|G|^2=\frac{1}{1+\left(\dfrac{f_c}{f}\right)^4}=\frac{1}{1000}.$$
> 两边取倒数：
> $$1+\left(\frac{f_c}{f}\right)^4=1000
> \quad\Longrightarrow\quad
> \left(\frac{f_c}{f}\right)^4=999.$$
>
> 用平方根算两次：
> $$999^{1/2}=31.607,\qquad 31.607^{1/2}=5.623,$$
> 所以
> $$\frac{f_c}{f}=999^{1/4}=5.623.$$
>
> $f_c=6$ kHz：
> $$f=\frac{f_c}{5.623}=\frac{6000}{5.623}=1067\ \mathrm{Hz}.$$
> 这个频率远低于截止频率（$1067\ll6000$），落在阻带里，所以衰减很大，符合 $30$ dB 的量级。

---

### 60. Question 60（第 60 题）^q60

A fourth-order Butterworth lowpass must lose at most 1 dB at 1 kHz. What is the smallest cutoff frequency $f_c$ (the $-3$ dB frequency), in kHz?（四阶 Butterworth 低通在 1 kHz 处衰减不得超过 1 dB。求最小截止频率 $f_c$（$-3$ dB 频率），单位 kHz。）

> [!success] Answer（答案）
> $1.184$ kHz

> [!abstract] 知识点讲解
> 见 [[信号与系统/Quiz对应知识点.md|Quiz对应知识点]] 8.5 由通带指标定截止频率。
>
> - **$n$ 阶 Butterworth 低通幅频平方**：$|G|^2=\dfrac{1}{1+\left(\dfrac{f}{f_c}\right)^{2n}}$。
> - **通带衰减**：$A=10\log_{10}\left[1+\left(\dfrac{f}{f_c}\right)^{2n}\right]$。
> - **通带指标**：$A\le A_p$。
> - **解不等式**：$\left(\dfrac{f}{f_c}\right)^{2n}\le10^{A_p/10}-1$。

> [!example] 解答
> $n$ 阶 Butterworth 低通
> $$|G|^2=\frac{1}{1+\left(\dfrac{f}{f_c}\right)^{2n}}.$$
> 「衰减 $A$ dB」指增益降到 $10^{-A/20}$，即
> $$|G|^2=10^{-A/10}
> \quad\Longrightarrow\quad
> 1+\left(\frac{f}{f_c}\right)^{2n}=10^{A/10}
> \quad\Longrightarrow\quad
> A=10\log_{10}\left[1+\left(\frac{f}{f_c}\right)^{2n}\right].$$
>
> $f=1$ kHz、$f_c$ 待求、$n=4$：
> $$10\log_{10}\left[1+\left(\frac{1}{f_c}\right)^8\right]\le1.$$
> 这里 $f$ 和 $f_c$ 都以 kHz 为单位，比值无量纲，单位一致即可。
>
> $$1+\left(\frac{1}{f_c}\right)^8\le10^{0.1}=1.2589
> \quad\Longrightarrow\quad
> \left(\frac{1}{f_c}\right)^8\le0.2589.$$
> 开八次方（两边都是正数）：
> $$\frac{1}{f_c}\le0.2589^{1/8}.$$
> 用对数算这个开方：
> $$\log_{10}0.2589=-0.5868,\qquad \frac{-0.5868}{8}=-0.07335,$$
> $$0.2589^{1/8}=10^{-0.07335}=0.8446,$$
> 所以
> $$\frac{1}{f_c}\le0.8446\quad\Longrightarrow\quad f_c\ge\frac{1}{0.8446}=1.184\ \mathrm{kHz}.$$
>
> 要求是「至多衰减 1 dB」，$f_c$ 越大越宽松，所以最小截止频率就是边界值
> $$f_c^{\min}=1.184\ \mathrm{kHz}.$$
> 直观理解：要保证 1 kHz 处几乎不衰减，截止频率不能压得太低；如果取 $f_c=1$ kHz，1 kHz 正好在截止点，会衰减 $3$ dB，超过 $1$ dB 的限制。

---

### 61. Question 61（第 61 题）^q61

A Butterworth lowpass filter with cutoff frequency 2 kHz must attenuate a 6 kHz signal by at least 35 dB. Enter the smallest order $n$ that meets this.（Butterworth 低通截止频率为 2 kHz，要求在 6 kHz 处衰减至少 35 dB。求满足条件的最小阶数 $n$。）

> [!success] Answer（答案）
> $n=4$

> [!abstract] 知识点讲解
> 见 [[信号与系统/Quiz对应知识点.md|Quiz对应知识点]] 8.5 阶数与衰减。
>
> - **阻带衰减**：$A=10\log_{10}\left[1+\left(\dfrac{f}{f_c}\right)^{2n}\right]$。
> - **频率比**：$\dfrac{f}{f_c}$ 为常数，记作 $r$。
> - **阶数求解**：$A(n)=10\log_{10}\left(1+r^{2n}\right)$，$A(n)$ 随 $n$ 单调增加。

> [!example] 解答
> $f=6$ kHz，$f_c=2$ kHz：
> $$\frac{f}{f_c}=\frac{6}{2}=3.$$
> 6 kHz 已经在通带之外（$f>f_c$），所以会有衰减。
>
> $$A(n)=10\log_{10}\left[1+\left(\frac{f}{f_c}\right)^{2n}\right]
> =10\log_{10}\left(1+3^{2n}\right).$$
> 阶数 $n$ 越高，$3^{2n}$ 越大，衰减越多，所以 $A(n)$ 随 $n$ 单调增加；从 $n=1$ 开始逐阶试算，第一个满足 $A(n)\ge35$ 的就是答案。
>
> - $n=1$：$A=10\log_{10}(1+3^2)=10\log_{10}10=10$ dB，不够；
> - $n=2$：$A=10\log_{10}(1+3^4)=10\log_{10}82=19.1$ dB，不够；
> - $n=3$：$3^6=729$，$A=10\log_{10}730=28.6$ dB，不够；
> - $n=4$：$3^8=6561$，$A=10\log_{10}6562=38.2$ dB，够了。
>
> $n=3$ 只有 $28.6$ dB，小于 $35$ dB；$n=4$ 为 $38.2$ dB，满足。$A(n)$ 单调，所以 $n\ge4$ 都满足，最小的就是 $n=4$。（题目要衰减至少 $35$ dB，刚好 $38.2$ 略有余量是正常的，因为阶数只能取整数。）
>
> 速算方法：高频近似下 $A\approx 10\log_{10}3^{2n}=20n\log_{10}3=9.54n$ dB，令 $9.54n\ge35$ 得 $n\ge3.67$，向上取整为 $4$。

---

## 4. Modulation (week 11)（调制，第 11 周）

Amplitude/frequency/phase modulation, FDM and instantaneous frequency（调幅、调频、调相、频分复用与瞬时频率）

---

### 62. Question 62（第 62 题）^q62

An antenna's length must be comparable to the wavelength $\lambda=c/f$ of the signal it transmits, with $c=3\times10^8$ m/s. Find the wavelength of a 3 kHz telephone audio signal sent directly as an electromagnetic wave, in km.（天线长度须与所发信号的波长 $\lambda=c/f$ 可比，$c=3\times10^8$ m/s。求 3 kHz 电话音频信号直接作为电磁波发送时的波长，单位 km。）

> [!success] Answer（答案）
> $100$ km

> [!abstract] 知识点讲解
> 见 [[信号与系统/Quiz对应知识点.md|Quiz对应知识点]] 9.1 调制的基本概念 与 9.7 例 5（波长与载波）。
>
> - **波长**：$\lambda=\dfrac{c}{f}$。
> - **电磁波速度**：$c=3\times10^8$ m/s。
> - **频率**：$f$ 的单位是 Hz。
> - **天线长度**：需与 $\lambda$ 相当，$f$ 越低所需天线越长。

> [!example] 解答
> $$\lambda=\frac{c}{f}=\frac{3\times10^8}{3\times10^3}=10^5\ \mathrm{m}=100\ \mathrm{km}.$$
> 波长太长，天线长度要几十公里，因此音频信号必须先调制到高频载波上。

---

### 63. Question 63（第 63 题）^q63

The message（消息信号）

$$
u(t)=2\cos(1000t)+\cos(2000t)
$$

is transmitted as（被调制成）

$$
y(t)=u(t)\cos(10\,000t).
$$

Which list gives the positive frequencies (rad/s) in $y(t)$ with the amplitudes of the corresponding cosines?（下列哪个列表给出 $y(t)$ 中的正频率及其对应余弦的振幅？）

(a) 8000 (1), 9000 (2), 11 000 (2), 12 000 (1)（漏掉了积化和差的 $\frac12$）
(b) 1000 (2), 2000 (1), 10 000 (1)（这是 $u(t)+\cos10000t$ 的频谱）
(c) 8000 (0.5), 9000 (1), 11 000 (1), 12 000 (0.5) **✓**
(d) 10 000 (1), 11 000 (1), 12 000 (0.5)（漏掉了下边带的一部分）

> [!success] Answer（答案）
> (c) 8000 (0.5), 9000 (1), 11 000 (1), 12 000 (0.5)

> [!abstract] 知识点讲解
> 见 [[信号与系统/Quiz对应知识点.md|Quiz对应知识点]] 9.1 调制的基本概念（DSB-SC 频谱） 与 9.7 例 6（DSB-SC 的频谱）。
>
> - **「正频率」是什么**：把信号写成余弦之和 $\sum A_k\cos(\omega_kt+\varphi_k)$，每个 $\omega_k>0$ 就是一个正频率分量（$\omega=2\pi f$ 是角频率，单位 rad/s；$f$ 是普通频率，单位 Hz）。题目问的「正频率及其振幅」就是把这组 $\omega_k>0$ 和对应的 $A_k$ 列出来。
> - **负频率不用管**：傅里叶变换里每个余弦也有 $\omega_k<0$ 的镜像分量（如 $\cos9000t=\frac12e^{j9000t}+\frac12e^{-j9000t}$），但题目只要求正频率。
> - **积化和差**：$\cos a\cos b=\dfrac12\left[\cos(a-b)+\cos(a+b)\right]$，每项产生上下两个边带。
> - **DSB-SC**：$y(t)=u(t)\cos\omega_ct$，频谱是 $u$ 的频谱搬到 $\omega_c$ 两侧，每份乘 $\frac12$；载波本身被抑制，所以 $\omega_c=10\,000$ 处没有谱线。
> - **确定正频率**：调制前 $u$ 有 $1000$、$2000$ 两个正频率；调制后每个变成 $10\,000\pm$ 它，即 $9000/11\,000$ 与 $8000/12\,000$，全部为正。
> - **确定振幅**：$2\cos1000t$ 一项不产生 $\frac12$（$2\times\frac12=1$）；$\cos2000t$ 一项振幅为 $1\times\frac12=0.5$。

> [!example] 解答
> 把 $u(t)$ 写成各分量。
> $$u(t)=2\cos(1000t)+\cos(2000t),$$
> 两个正频率 $1000$、$2000$ rad/s，振幅分别为 $2$、$1$。
>
> 逐项乘载波，用积化和差。
>
> 第一项（振幅 $2$）：
> $$2\cos1000t\cos10000t=2\cdot\frac12\left[\cos(10000-1000)t+\cos(10000+1000)t\right]
> =\cos9000t+\cos11000t,$$
> 得到正频率 $9000$ 与 $11\,000$ rad/s，振幅均为 $1$。
>
> 第二项（振幅 $1$）：
> $$\cos2000t\cos10000t=\frac12\left[\cos(10000-2000)t+\cos(10000+2000)t\right]
> =\frac12\cos8000t+\frac12\cos12000t,$$
> 得到正频率 $8000$ 与 $12\,000$ rad/s，振幅均为 $0.5$。
>
> 汇总（正频率，单位 rad/s）。
>
> | 正频率 | 振幅 | 来源 |
> |---|---|---|
> | $8000$ | $0.5$ | 下边带：$10000-2000$ |
> | $9000$ | $1$ | 下边带：$10000-1000$ |
> | $11\,000$ | $1$ | 上边带：$10000+1000$ |
> | $12\,000$ | $0.5$ | 上边带：$10000+2000$ |
>
> 载频 $10\,000$ 处没有分量（DSB-SC 抑制载波）。选 (c)。

---

### 64. Question 64（第 64 题）^q64

A speech scrambler multiplies $u(t)$, bandlimited to 15 kHz, by $2\cos(2\pi\cdot15\,000t)$ and passes the product through an ideal lowpass filter with cutoff 15 kHz and gain 1. A component $3\cos(2\pi\cdot4000t)$ of $u(t)$ appears in the scrambled output as（语音置乱器把带宽 15 kHz 的 $u(t)$ 乘以 $2\cos(2\pi\cdot15000t)$，再通过截止 15 kHz、增益 1 的理想低通。$u(t)$ 中的分量 $3\cos(2\pi\cdot4000t)$ 在置乱输出中变成）

(a) $3\cos(2\pi\cdot19\,000t)$（被低通滤掉的 19 kHz 项）
(b) $3\cos(2\pi\cdot4000t)$（原频率，没有发生搬移）
(c) $3\cos(2\pi\cdot11\,000t)$ **✓**（留在通带内的下边带分量）
(d) $1.5\cos(2\pi\cdot11\,000t)$（振幅忘了载波幅度 $2$ 的抵消）

> [!success] Answer（答案）
> (c) $3\cos(2\pi\cdot11\,000t)$

> [!abstract] 知识点讲解
> 见 [[信号与系统/Quiz对应知识点.md|Quiz对应知识点]] 9.1 调制的基本概念（乘载波搬移频谱） 与 9.7 例 7（单边带滤波）。
>
> - **乘载波 = 频谱搬移**：乘 $2\cos\omega_ct$ 后，每个频率分量 $f$ 变成 $\omega_c-f$ 与 $\omega_c+f$，幅度不变（$2$ 抵消 $\frac12$）。
> - **低通筛选**：本题载频 $15$ kHz、低通截止也是 $15$ kHz，只有下边带 $15-4=11$ kHz 留在通带内。
> - **单边带（SSB）**：滤掉一个边带，带宽减半，这就是单边带调制。

> [!example] 解答
> 乘积：
> $$3\cos(2\pi\cdot4000t)\cdot2\cos(2\pi\cdot15000t)
> =3\cos(2\pi\cdot11000t)+3\cos(2\pi\cdot19000t).$$
> 低通保留 $11$ kHz（低于 $15$ kHz），滤掉 $19$ kHz。所以输出分量为
> $$3\cos(2\pi\cdot11\,000t).$$
> 选 (c)。

---

### 65. Question 65（第 65 题）^q65

Frequency division multiplexing（频分复用）

A radio band runs from 3.000 MHz to 3.400 MHz. Each telephone message has bandwidth 3.4 kHz and is sent by DSB-SC, with no guard bands and no overlap allowed. What is the largest number of channels that fit in the band?（某无线电频段从 3.000 MHz 到 3.400 MHz。每路电话带宽 3.4 kHz，用 DSB-SC 发送，不留保护间隔也不允许重叠。最多能容纳多少个信道？）

> [!success] Answer（答案）
> $58$

> [!abstract] 知识点讲解
> 见 [[信号与系统/Quiz对应知识点.md|Quiz对应知识点]] 9.4 频分复用 与 9.7 例 8（FDM 信道数）。
>
> - **每个 DSB-SC 信道占 $2W$**：$W$ 是消息带宽（单边），本题 $2W=6.8$ kHz。
> - **N 路首尾相接**：总带宽 $N\cdot2W$，所以 $N=\left\lfloor\dfrac{B_{\text{band}}}{2W}\right\rfloor$（向下取整）。
> - **不能四舍五入**：多出来的 $0.8$ 个信道放不下，只能舍去。

> [!example] 解答
> 单信道带宽：
> $$2W=2\times3.4=6.8\ \mathrm{kHz}.$$
> 频段宽度：
> $$400\ \mathrm{kHz}.$$
> 信道数：
> $$\left\lfloor\frac{400}{6.8}\right\rfloor=\left\lfloor58.8\right\rfloor=58.$$
> 第 $59$ 路需要额外 $0.8\times6.8=5.44$ kHz，超出频段，所以最多 $58$ 路。

---

### 66. Question 66（第 66 题）^q66

Four messages, each bandlimited to 3 kHz, are sent by DSB-SC on carriers $f_1<f_2<f_3<f_4$. The FDM spectrum must begin at 100 kHz, with 5 kHz guard bands between adjacent channels and no gaps otherwise. Find $f_4$ in kHz.（四路带宽均为 3 kHz 的消息用 DSB-SC 分别调制到载波 $f_1<f_2<f_3<f_4$。FDM 频谱须从 100 kHz 开始，相邻信道间留 5 kHz 保护间隔，其余不留空隙。求 $f_4$，单位 kHz。）

> [!success] Answer（答案）
> $136.0$ kHz

> [!abstract] 知识点讲解
> 见 [[信号与系统/Quiz对应知识点.md|Quiz对应知识点]] 9.4 频分复用（含保护间隔的载频安排） 与 9.7 例 9（FDM 载频安排）。
>
> - **DSB-SC 频谱以载频为中心**：第 $i$ 路占 $[f_i-W,\,f_i+W]$。
> - **第一路起点**：$f_1-W=100$ kHz $\Rightarrow f_1=100+W$。
> - **相邻载频间隔**：$2W+g$，$g$ 是保护间隔；本题 $6+5=11$ kHz。
> - **等差排列**：$f_k=f_1+(k-1)(2W+g)$。

> [!example] 解答
> **题意**：$W=3$ kHz，保护间隔 $g=5$ kHz，每路 DSB-SC 占 $2W=6$ kHz（载频两侧各 $3$ kHz）。
>
> **第一路载频。** 频带从 $100$ kHz 开始，第一路的下边沿必须在 $100$ kHz：
> $$f_1-W=100\ \Rightarrow\ f_1=100+3=103\ \mathrm{kHz}.$$
> 第一路占 $[100,\,106]$ kHz。
>
> **相邻载频间隔。** 设相邻两路载频为 $f_i$、$f_{i+1}$，载频之间的距离要同时容纳：
> - 第 $i$ 路的上半段：从 $f_i$ 到 $f_i+W$，宽 $3$ kHz；
> - 保护间隔 $g$：宽 $5$ kHz；
> - 第 $i+1$ 路的下半段：从 $f_{i+1}-W$ 到 $f_{i+1}$，宽 $3$ kHz。
>
> 三者首尾相接，所以
> $$f_{i+1}-f_i=\underbrace{W}_{3}+\underbrace{g}_{5}+\underbrace{W}_{3}=2W+g=6+5=11\ \mathrm{kHz}.$$
> 其中的「$6$」就是 $2W=2\times3$（一路信号本身占的宽度），「$5$」是保护间隔。
>
> 检查：第一路占 $[100,106]$，空 $5$ kHz 保护间隔 $[106,111]$，第二路以 $114$ 为载频、占 $[111,117]$，恰好衔接。
>
> **第四路载频。** 从 $f_1$ 到 $f_4$ 共跨 $3$ 个间隔：
> $$f_4=f_1+3\times(2W+g)=103+3\times11=136.0\ \mathrm{kHz}.$$
> 第四路占 $[133,\,139]$ kHz，最后一路上边沿为 $139$ kHz。

---

### 67. Question 67（第 67 题）^q67

Two messages $u_1(t)$ and $u_2(t)$ are each bandlimited to 5000 rad/s. The signal（两路消息 $u_1(t)$、$u_2(t)$ 带宽均为 5000 rad/s。构造信号）

$$
b(t)=u_1(t)+u_2(t)\cdot2\cos(10\,000t)
$$

is formed and then transmitted as（再发送为）

$$
c(t)=b(t)\cdot2\cos(20\,000t).
$$

Which band of positive frequencies does $c(t)$ occupy?（$c(t)$ 占据哪个正频率频段？）

(a) 5000 to 35 000 rad/s **✓**
(b) 10 000 to 30 000 rad/s（只搬移了内层载频）
(c) 0 to 35 000 rad/s（误以为搬移后仍保留原来的低频分量）
(d) 15 000 to 25 000 rad/s（只用 $u_1$ 的频段计算）

> [!success] Answer（答案）
> (a) 5000 到 35 000 rad/s

> [!abstract] 知识点讲解
> 见 [[信号与系统/Quiz对应知识点.md|Quiz对应知识点]] 9.1 调制的基本概念（频谱搬移、多层调制） 与 9.7 例 10（多层调制）。
>
> - **乘载波 = 把整个频谱搬到 $\omega_c$ 两侧**：乘 $2\cos\omega_ct$ 后频段变成 $[\omega_c-W_b,\ \omega_c+W_b]$（$W_b$ 是调制前信号的最高频率）。
> - **相加 = 频谱取并集**：先算内层 $b(t)$ 占多大频段，再整体外搬。
> - **先内后外**：$b(t)$ 占 $[0,15\,000]$，所以 $c(t)$ 占 $20\,000\pm15\,000$。

> [!example] 解答
> 先明确「正频率频段」在问什么。 实信号的负频率总是正频率的镜像，所以只需追踪 $\omega>0$ 这一半；下面的每一步都只记正频率范围。
>
> $u_1,u_2$ 各自占多宽。 「带宽 5000 rad/s」说明这两个基带信号的正频率都落在
> $$[0,\,5000]\ \mathrm{rad/s},$$
> 负频率各有一份镜像 $[-5000,0]$（频谱关于 $\omega=0$ 共轭对称）。
>
> $u_2$ 乘 $2\cos(10\,000t)$ 后搬到哪。 把载波展开：
> $$2\cos(10\,000t)=e^{j10\,000t}+e^{-j10\,000t}.$$
> 乘 $e^{j10\,000t}$ 把频谱右移 $10\,000$，乘 $e^{-j10\,000t}$ 把频谱左移 $10\,000$——相当于把 $u_2$ 的频谱复制两份，分别贴在 $\pm10\,000$ 两侧。只看正频率，取右移的那份，把 $u_2$ 的整段 $[-5000,5000]$ 平移 $10\,000$：
> $$[-5000,5000]+10\,000=[5000,\,15\,000].$$
> 拆开看：下边带 $[5000,10\,000]$，上边带 $[10\,000,15\,000]$，合起来 $[5000,15\,000]$。乘 $2$ 抵消了积化和差的 $\frac12$，所以各分量的幅度不变。
>
> $b(t)=u_1+$（调制后的 $u_2$）。 时域相加，频谱相加，所以两个信号占的频段取**并集**：
> $$b:\underbrace{[0,5000]}_{u_1\ \text{原样}}\cup\underbrace{[5000,15\,000]}_{u_2\ \text{调制后}}=[0,15\,000]\quad(\omega>0).$$
> 两段恰好在 $5000$ 处首尾相接，中间没有空隙。关键点：$u_1$ **没有乘载波**，仍留在基带 $[0,5000]$，这一步最容易漏。加上负频率半边，$b$ 的完整频谱占 $[-15\,000,\,15\,000]$。
>
> $c(t)=b(t)\cdot2\cos(20\,000t)$。 同样展开：
> $$2\cos(20\,000t)=e^{j20\,000t}+e^{-j20\,000t}.$$
> - 乘 $e^{j20\,000t}$：$b$ 的频谱右移 $20\,000$。把 $b$ 的完整频段 $[-15\,000,15\,000]$ 平移：
> $$[-15\,000,15\,000]+20\,000=[5000,\,35\,000].$$
> 这段全部是正频率。
> - 乘 $e^{-j20\,000t}$：$b$ 的频谱左移 $20\,000$，
> $$[-15\,000,15\,000]-20\,000=[-35\,000,-5000],$$
> 这段全部是负频率，只是正频率的镜像，不贡献新的正频率。
>
> 因此 $c(t)$ 的正频率频段为
> $$[5000,\,35\,000]\ \mathrm{rad/s}.$$
>
> **换个做法：先把 $c(t)$ 展开，再逐项搬，行不行？** 可以，而且结果一样。把 $c(t)$ 完全展开：
> $$c(t)=b(t)\cdot2\cos20\,000t
> =2u_1(t)\cos20\,000t+4u_2(t)\cos10\,000t\cos20\,000t.$$
> 对第二项用积化和差 $2\cos A\cos B=\cos(A+B)+\cos(A-B)$：
> $$4u_2\cos10\,000t\cos20\,000t
> =2u_2\cos10\,000t+2u_2\cos30\,000t,$$
> 所以
> $$c(t)=2u_1\cos20\,000t+2u_2\cos10\,000t+2u_2\cos30\,000t.$$
> 现在三项各自是一个「基带信号 × 一个载波」，逐项搬：
>
> | 项 | 基带占据（正频率） | 载频 | 搬移后（正频率） |
> |---|---|---|---|
> | $2u_1\cos20\,000t$ | $[0,5000]$ | $20\,000$ | $[15\,000,25\,000]$ |
> | $2u_2\cos10\,000t$ | $[0,5000]$ | $10\,000$ | $[5000,15\,000]$ |
> | $2u_2\cos30\,000t$ | $[0,5000]$ | $30\,000$ | $[25\,000,35\,000]$ |
>
> 三段首尾相接，取并集仍得 $[5000,\,35\,000]$，和逐层搬移的答案一致。
>
> **那为什么还推荐「逐层搬」？**
> - 逐层搬和完全展开本质是同一件事：乘一次载波就是把频谱平移一次；逐层只是把两次平移分开做，不容易漏项。
> - 本题 $u_1,u_2$ 没有给出具体表达式，只有带宽。直接写 $c(t)$ 后仍然看不出频段，还是得把每个「乘载波」翻译成一次平移。
> - 展开时系数容易错：$b$ 里 $u_2$ 前面的 $2$ 和外载波的 $2$ 相乘得到 $4$，积化和差后变成 $2$；稍不留神就会写成 $1$ 或 $4$。逐层处理时每一步只乘一个 $2$，还能检查「乘 $2$ 抵消 $\frac12$」。
> - 展开后必须记住：**只有乘了载波的那一项才搬**。$u_1$ 只乘了 $20\,000$ 的载波，所以它搬到 $[15\,000,25\,000]$，绝不能因为式子里出现 $10\,000$ 就把它也挪到 $10\,000$ 附近。
>
> **逐项检验四个选项。**
> - **(a) $5000$ 到 $35\,000$**：正确，以上推导的结果。
> - **(b) $10\,000$ 到 $30\,000$**：把外层载频 $20\,000$ 当作中心、只搬了内层 $10\,000\pm5000$，漏掉了 $u_1$，也漏掉了搬移时应该用整个 $b$ 的宽度 $15\,000$。
> - **(c) $0$ 到 $35\,000$**：误以为乘载波后原来的基带 $[0,5000]$ 还留在原处；实际上 $u_1$ 被外载波搬到了 $[15\,000,25\,000]$，$u_2$ 的最低下边带也在 $5000$，低频段是空的。
> - **(d) $15\,000$ 到 $25\,000$**：只取了 $u_1$ 被搬到的那一段，漏掉了另外两项。
>
> 选 (a)。

---

### 68. Question 68（第 68 题）^q68

Frequency and phase modulation, instantaneous frequency（调频、调相与瞬时频率）

The signal $y(t)=\cos(t^2)$ is a sinusoid with variable frequency, $y(t)=\cos(\omega(t)t)$ with $\omega(t)=t$. Find its instantaneous frequency at $t=5$ s, in rad/s.（信号 $y(t)=\cos(t^2)$ 是变频正弦，写成 $y(t)=\cos(\omega(t)t)$ 时 $\omega(t)=t$。求 $t=5$ s 时的瞬时角频率，单位 rad/s。）

> [!success] Answer（答案）
> $10$ rad/s

> [!abstract] 知识点讲解
> 见 [[信号与系统/Quiz对应知识点.md|Quiz对应知识点]] 9.5 瞬时频率与 PM、FM 与 9.7 例 11（瞬时频率）。
>
> - **瞬时角频率定义**：$\omega_i(t)=\dfrac{d\theta(t)}{dt}$，其中 $\theta(t)$ 是**整个**瞬时相位。
> - **常见误区**：不要把 $\cos(\omega(t)t)$ 里的 $\omega(t)$ 当成瞬时频率；要看相位表达式 $t^2$，再求导。
> - **相位与频率的关系**：频率是相位的导数，相位是频率的积分。
> - **本题**：$\theta(t)=t^2\Rightarrow\omega_i(t)=2t$。

> [!example] 解答
> 相位：
> $$\theta(t)=t^2.$$
> 瞬时角频率：
> $$\omega_i(t)=\frac{d\theta}{dt}=2t.$$
> 代入 $t=5$：
> $$\omega_i(5)=10\ \mathrm{rad/s}.$$
> 注意 $t^2$ 的相位在 $t=5$ 处变化速度是 $10$，而不是 $\omega(t)=5$。

---

### 69. Question 69（第 69 题）^q69

A PM transmitter sends（某 PM 发射机发送）

$$
y(t)=\cos\left(\omega_ct+ku(t)\right),\qquad k=0.5\ \mathrm{rad/V}.
$$

Over $0\le t\le1$ ms the message is a ramp（在 $0\le t\le1$ ms 内消息为斜坡）

$$
u(t)=4000t\ \mathrm{V}.
$$

By how many Hz is the instantaneous frequency shifted from the carrier during the ramp?（斜坡期间瞬时频率相对载波偏移多少 Hz？）

> [!success] Answer（答案）
> $318.3$ Hz

> [!abstract] 知识点讲解
> 见 [[信号与系统/Quiz对应知识点.md|Quiz对应知识点]] 9.5 瞬时频率与 PM、FM（PM 部分） 与 9.7 例 12（PM 的频偏）。
>
> - **PM 信号**：$y(t)=\cos\left(\omega_ct+ku(t)\right)$。
> - **PM 的瞬时频率**：$\omega_i=\dfrac{d}{dt}\left[\omega_ct+ku(t)\right]=\omega_c+k\dot u(t)$。
> - **频偏只由导数决定**：斜坡 $u=At$ 的导数恒为 $A$，所以整段斜坡频率偏移恒定，与 $u$ 自己有多大无关。
> - **角频率换算频率**：$\Delta f=\dfrac{\Delta\omega}{2\pi}$。

> [!example] 解答
> 斜坡导数：
> $$\dot u(t)=4000.$$
> 瞬时角频率：
> $$\omega_i=\omega_c+0.5\times4000=\omega_c+2000\ \mathrm{rad/s}.$$
> 换算成赫兹：
> $$\Delta f=\frac{2000}{2\pi}=318.3\ \mathrm{Hz}.$$

---

### 70. Question 70（第 70 题）^q70

The message $u(t)=H(t)$ is sent once by FM（消息 $u(t)=H(t)$，一次用 FM 发送）

$$
y=\cos\left(\omega_ct+k\int_{-\infty}^{t}u\right),
$$

and once by PM（一次用 PM 发送）

$$
y=\cos\left(\omega_ct+ku(t)\right).
$$

Which description of the two signals for $t>0$ is correct?（下列对 $t>0$ 时两个信号的描述哪个正确？）

(a) Both have frequency $\omega_c+k$ for $t>0$（两者的频率都是 $\omega_c+k$）
(b) Both multiply the carrier amplitude by $1+k$ for $t>0$（两者的载波幅度都乘以 $1+k$）
(c) FM: the frequency jumps to $\omega_c+k$ with continuous phase. PM: the phase jumps by $k$ at $t=0$ and the frequency is $\omega_c$ again for $t>0$. **✓**（FM 频率跳到 $\omega_c+k$ 且相位连续；PM 在 $t=0$ 相位跳变 $k$，之后频率回到 $\omega_c$）
(d) FM: the phase jumps by $k$ at $t=0$. PM: the frequency jumps to $\omega_c+k$.（把 FM 与 PM 对调）

> [!success] Answer（答案）
> (c) FM 相位连续、频率为 $\omega_c+k$；PM 相位跳变、频率回到 $\omega_c$

> [!abstract] 知识点讲解
> 见 [[信号与系统/Quiz对应知识点.md|Quiz对应知识点]] 9.5 瞬时频率与 PM、FM 与 9.7 例 13（FM 与 PM 的区别）。
>
> - **FM 的相位是消息的积分**：$y=\cos\left(\omega_ct+k\displaystyle\int_{-\infty}^{t}u(\tau)d\tau\right)$，所以瞬时频率 $\omega_i=\omega_c+ku(t)$。
> - **PM 的相位直接是消息**：$y=\cos\left(\omega_ct+ku(t)\right)$，所以瞬时频率 $\omega_i=\omega_c+k\dot u(t)$。
> - **阶跃输入的两面**：FM 相位连续、频率跳到 $\omega_c+k$；PM 相位在 $t=0$ 跳 $k$，之后 $\dot u=0$，频率回到 $\omega_c$。

> [!example] 解答
> FM：$t>0$ 时
> $$\int_{-\infty}^{t}H(\tau)d\tau=t,$$
> $$\theta_{\mathrm{FM}}(t)=\omega_ct+kt.$$
> 相位在 $t=0$ 连续（积分为零），瞬时频率
> $$\omega_i=\omega_c+k.$$
>
> PM：$t>0$ 时
> $$\theta_{\mathrm{PM}}(t)=\omega_ct+k.$$
> $t=0$ 处相位从 $\omega_ct$ 跳到 $\omega_ct+k$，跳变量为 $k$；$t>0$ 时导数为 $\omega_c$，频率回到载波频率。选 (c)。

---

### 71. Question 71（第 71 题）^q71

A message $u(t)$ with spectrum zero for $|\omega|>W$ (and no DC component) is sent by FM（某消息 $u(t)$ 的频谱在 $|\omega|>W$ 处为零，且无直流分量，用 FM 发送）：

$$
y(t)=\cos\left(\omega_ct+k\int_{-\infty}^{t}u(\tau)\,d\tau\right),\qquad \omega_c\gg W.
$$

For small but nonzero $k$, the spectrum of $y(t)$ consists of（当 $k$ 很小但不为零时，$y(t)$ 的频谱由什么组成？）

(a) lines at $\pm\omega_c$ plus sidebands in $\omega_c-W<|\omega|<\omega_c+W$, the same band as AM **✓**（$\pm\omega_c$ 处的谱线加上 $\omega_c-W<|\omega|<\omega_c+W$ 内的边带，与 AM 频段相同）
(b) components spread over a band much wider than $2W$ around $\pm\omega_c$（比 $2W$ 宽得多的频带）
(c) lines at $\pm\omega_c$ only（只有 $\pm\omega_c$ 谱线）
(d) the baseband spectrum $|\omega|<W$ plus lines at $\pm\omega_c$（原来的低频频谱加上载波谱线）

> [!success] Answer（答案）
> (a) 载波谱线加与 AM 同带宽的边带

> [!abstract] 知识点讲解
> 见 [[信号与系统/Quiz对应知识点.md|Quiz对应知识点]] 9.6 窄带 FM 与宽带 FM 与 9.7 例 14（窄带 FM 的频谱）。
>
> - **窄带 FM 的条件**：调制指数 $\beta=\dfrac{\Delta f}{W}\ll1$，等价于 $k$ 很小、相位摆动 $k\displaystyle\int u$ 很小。
> - **小角度展开**：$\cos(\omega_ct+\theta)\approx\cos\omega_ct-\theta\sin\omega_ct$。
> - **频谱组成**：$\pm\omega_c$ 的载波谱线 + $\omega_c\pm W$ 内的一对边带，带宽 $2W$，与 AM 相同（边带相位不同）。
> - **什么时候变宽**：只有 $\beta\gg1$ 时才用 Carson 公式 $B\approx2(\Delta f+W)$。

> [!example] 解答
> **目标。** $k$ 很小但不为零时，问 $y(t)$ 的频谱落在哪些频率上。
>
> 把相位拆成「载波相位 + 小扰动」。 记
> $$\theta(t)=k\int_{-\infty}^{t}u(\tau)d\tau,$$
> 则
> $$y(t)=\cos\left(\omega_ct+\theta(t)\right).$$
> $k$ 很小，所以 $\theta(t)$ 的幅度很小（$|\theta|\ll1$ rad）。这正是「窄带」的含义：相位只被轻轻推了一下，不会绕圈。
>
> 小角度展开。 用 $\cos(A+B)=\cos A\cos B-\sin A\sin B$。因为 $|B|=|\theta|\ll1$，有 $\cos\theta\approx1$、$\sin\theta\approx\theta$，所以
> $$y(t)\approx\cos\omega_ct\cdot1-\sin\omega_ct\cdot\theta(t)
> =\underbrace{\cos\omega_ct}_{\text{载波}}-\underbrace{\theta(t)\sin\omega_ct}_{\text{边带}}.$$
> 这一步把「频率被调制」变成了「两项相加」：一项是纯载波，另一项是基带信号 $\theta$ 乘载波。
>
> $\theta(t)$ 的频带有多宽。 $\theta=k\int u$。积分在频域是乘 $\dfrac{1}{j\omega}$，只改变各频率的幅度和相位，**不产生新频率**。$u$ 的频谱在 $|\omega|>W$ 处为零，所以 $\theta$ 的频谱也只在 $|\omega|\le W$ 内。
> 另外 $u$ 无直流 ⇒ $U(0)=0$ ⇒ 积分后 $\theta$ 也没有直流分量（没有常数项）。
>
> 两项各自的频谱。
> - 第一项 $\cos\omega_ct$：两根谱线，位于 $\omega=\pm\omega_c$。
> - 第二项 $-\theta(t)\sin\omega_ct$：这是一个**带宽 $W$、无直流的基带信号乘载波**。乘载波就是把 $\theta$ 的频谱复制到 $\pm\omega_c$ 两侧，占据
> $$\omega_c-W<|\omega|<\omega_c+W.$$
> 因为 $\theta$ 没有直流，所以这一项在 $\omega=\pm\omega_c$ 处**不产生**额外谱线，只形成上、下边带。（与 AM 的差别：$\sin$ 载波使下边带相位反相，但占据的频段相同。）
>
> 合并。 总频谱为
> $$\underbrace{\pm\omega_c\ \text{处的载波谱线}}_{\text{第一项}}+\underbrace{\omega_c-W<|\omega|<\omega_c+W\ \text{内的边带}}_{\text{第二项}}.$$
> 正频率部分从 $\omega_c-W$ 到 $\omega_c+W$，宽 $2W$，与 AM 完全相同。选 (a)。
>
> **为什么其他选项不对。**
> - **(b) 比 $2W$ 宽得多**：那是 $\beta\gg1$ 的宽带 FM。小 $k$ 时更高次的边带幅度正比于 $k^2,k^3,\dots$，可以忽略，所以带宽没有变宽。
> - **(c) 只有载波谱线**：$\theta$ 虽然没有直流，但有交流成分（$u$ 的各频率都在），所以边带一定存在。
> - **(d) 原来的低频频谱 + 载波谱线**：调制把基带频谱**搬到** $\pm\omega_c$ 附近，不是把它原样留在低频再叠上载波；低频处没有分量。

---

> [!note] Source note（来源说明）
> Some questions are adapted from B. P. Lathi and R. A. Green, *Linear Systems and Signals*, 3rd ed. (chapters 4 and 7), from ELEC3004 Signals, Systems and Control at the University of Queensland (2017), and from S. Boyd, EE102 Introduction to Signals and Systems, Stanford University.（部分题目改编自 B. P. Lathi 和 R. A. Green《线性系统与信号》第三版第 4、7 章，昆士兰大学 ELEC3004《信号、系统与控制》课程（2017 年），以及斯坦福大学 S. Boyd 的 EE102《信号与系统导论》课程。）
