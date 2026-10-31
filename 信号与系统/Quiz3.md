# ELEC2302/9302 Signals and Systems — Quiz 3 practice questions, answers and feedback

ELEC2302/9302《信号与系统》——测验 3 练习题、答案与反馈

**How to use this question bank:**

don't work through the questions from beginning to end.（本题库使用方法  不要从头到尾按顺序做题。）

Start by doing one question from each group, identify the areas where you are less confident, and work on those first.（先从每个题组中各做一道题，找出掌握不够牢固的部分，再优先练习这些内容。）

The correct option is marked ✓.（正确选项标有 ✓。）

---

## 1. Question 1（第 1 题）^q1

### 1. The Laplace transform (week 8)（拉普拉斯变换，第 8 周）

Laplace transform: definition, ROC and table pairs（拉普拉斯变换：定义、收敛域与常用变换对）

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
> 见 11.1 收敛域与信号类型 与 7.2 常用变换对。
>
> - 和的变换只在每一项都收敛的地方存在，所以 ROC 取各项 ROC 的**交集**。
> - 两项都是因果信号，各自的 ROC 都是某条竖直线以右，交集仍是一条竖直线以右。
> - 增长项 $e^{t}$ 决定最右侧边界。

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

## 2. Question 2（第 2 题）^q2

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
> 见 11.1 收敛域与信号类型 与 7.2 常用变换对。
>
> - $e^{s_0t}H(t)$ 的 ROC 为 $\operatorname{Re}(s)>\operatorname{Re}(s_0)$。
> - 只有指数实部影响 $|u(t)e^{-\sigma t}|$ 的增减，虚部只让信号旋转。
> - ROC 的边界是竖直线，不是圆。

> [!example] 解答
> 这里 $s_0=-2+5j$。取 $s=\sigma+j\omega$：
> $$\left|u(t)e^{-st}\right|=\left|e^{(-2+5j-\sigma-j\omega)t}\right|
> =e^{(-2-\sigma)t}.$$
> 上式在 $t\to\infty$ 时衰减，当且仅当
> $$-2-\sigma<0\quad\Longrightarrow\quad\sigma>-2.$$
> 所以
> $$\operatorname{ROC}:\ \operatorname{Re}(s)>-2.$$
> 极点位于 $s=-2+5j$，ROC 在该极点实部的右侧。$|s|=\sqrt{(-2)^2+5^2}=\sqrt{29}$ 只是极点到原点的距离，与 ROC 边界无关。选 (b)。

---

## 3. Question 3（第 3 题）^q3

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
> 见 11.1 收敛域与信号类型 与 11.2 时移与阶跃延迟。
>
> - 先找出延迟后脉冲的支撑区间，再写成两个阶跃之差。
> - 使用 $\mathcal L\{H(t-\tau)\}=\dfrac{e^{-s\tau}}{s}$。
> - 时移因子 $e^{-s\tau}$ 中的 $\tau$ 是阶跃的起点。

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

## 4. Question 4（第 4 题）^q4

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
> 见 11.2 常用拉普拉斯变换的推导与核对（调制型乘积）与 7.2 常用变换对。
>
> - 先用积化和差把时域乘积化成同频余弦之和。
> - $\cos A\cos B=\dfrac12\left[\cos(A+B)+\cos(A-B)\right]$，两项之间是**加号**。
> - 变换是线性的，可以逐项查表相加；时域相乘不等于变换相乘。

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

## 5. Question 5（第 5 题）^q5

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
> 见 7.2 常用变换对 与 11.3 冲激响应与阶跃响应。
>
> - 冲激响应是传递函数的拉普拉斯逆变换。
> - $\mathcal L\{\delta(t)\}=1$，所以常数 $K$ 对应 $K\delta(t)$。
> - 静态增益系统同样有冲激响应，它就是加权冲激。

> [!example] 解答
> 由
> $$\delta(t)\longleftrightarrow 1$$
> 和线性性，
> $$5\longleftrightarrow 5\delta(t).$$
> 因此
> $$h(t)=5\delta(t).$$
> 校验：输入 $u(t)$ 时，
> $$y(t)=h(t)*u(t)=5\delta(t)*u(t)=5u(t),$$
> 正是纯增益系统。选 (d)。

---

## 6. Question 6（第 6 题）^q6

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
> 见 11.2 常用拉普拉斯变换的推导与核对（正弦与余弦）。
>
> - 取 $s_0=\pm4j$，分别查表。
> - 通分时使用 $(s-4j)(s+4j)=s^2-(4j)^2=s^2+16$。
> - 分子为 $\dfrac12\left[(s+4j)+(s-4j)\right]=s$。

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

## 7. Question 7（第 7 题）^q7

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
> 见 11.2 时移与阶跃延迟。
>
> - $e^{-s\tau}U(s)$ 表示整个信号延迟 $\tau$。
> - 单边拉普拉斯变换中，延迟必须让指数与阶跃**一起**平移。
> - 先认出 $\dfrac{1}{s+1}\leftrightarrow e^{-t}H(t)$，再整体延迟 $3$ s。

> [!example] 解答
> 已知
> $$\frac{1}{s+1}\longleftrightarrow e^{-t}H(t).$$
> 由时移性质，
> $$\frac{e^{-3s}}{s+1}\longleftrightarrow e^{-(t-3)}H(t-3).$$
> 检查其他选项：
> - (a) $e^{-(t+3)}H(t)=e^{-3}e^{-t}H(t)$，变换为 $\dfrac{e^{-3}}{s+1}$。
> - (c) $e^{-t}H(t-3)=e^{-3}e^{-(t-3)}H(t-3)$，多出常数 $e^{-3}$。
> - (d) $e^{-(t-3)}H(t)=e^{3}e^{-t}H(t)$，变换为 $\dfrac{e^{3}}{s+1}$。
>
> 选 (b)。

---

## 8. Question 8（第 8 题）^q8

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
> 见 11.3 冲激响应与阶跃响应。
>
> - 阶跃响应是冲激响应的积分，所以冲激响应是阶跃响应的导数。
> - $Y_{\text{step}}(s)=\dfrac{G(s)}{s}$，故 $G(s)=sY_{\text{step}}(s)$。
> - 阶跃响应在 $t=0$ 处为 $0$，求导不产生冲激。

> [!example] 解答
> 对 $t>0$ 求导：
> $$h(t)=\frac{d}{dt}\left(e^{-t}-e^{-2t}\right)H(t)
> =\left(-e^{-t}+2e^{-2t}\right)H(t).$$
> 因为 $y_{\text{step}}(0^+)=1-1=0$，阶跃响应连续，所以没有额外的冲激项。整理得
> $$h(t)=\left(2e^{-2t}-e^{-t}\right)H(t).$$
> 也可用变换校验：
> $$Y_{\text{step}}(s)=\frac{1}{s+1}-\frac{1}{s+2}
> =\frac{1}{(s+1)(s+2)},$$
> $$G(s)=sY_{\text{step}}(s)=\frac{s}{(s+1)(s+2)}
> =\frac{2}{s+2}-\frac{1}{s+1}.$$
> 反变换与上面一致。选 (b)。

---

## 9. Question 9（第 9 题）^q9

Let（令）

$$
y(t)=\left[e^{-t}H(t)\right]*\left[e^{-3t}H(t)\right].
$$

Use the Laplace transform to find $y(1)$.（用拉普拉斯变换求 $y(1)$。）

> [!success] Answer（答案）
> $y(1)=0.1590$

> [!abstract] 知识点讲解
> 见 7.3 性质（卷积）与 11.4 遮盖法求单实极点。
>
> - 时域卷积对应 $s$ 域相乘。
> - 得到 $Y(s)$ 后做部分分式，再逐项反变换。
> - 注意指数项要乘 $H(t)$。

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

## 10. Question 10（第 10 题）^q10

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
> 见 7.3 性质（$s$ 域移位）与 7.2 常用变换对。
>
> - 先查 $\sin(3t)H(t)\leftrightarrow\dfrac{3}{s^2+9}$。
> - 时域乘 $e^{2t}$，$s$ 域用 $s-2$ 替换 $s$：$F(s-2)$。
> - $(s-2)^2+9=s^2-4s+13$。

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

## 11. Question 11（第 11 题）^q11

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
> 见 11.2 积分与微分。
>
> - 从 $0$ 到 $t$ 的积分在 $s$ 域除以 $s$。
> - $\cos3tH(t)\leftrightarrow\dfrac{s}{s^2+9}$。
> - 也可以先积分得 $\frac13\sin3t$，再查表，结果相同。

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

## 12. Question 12（第 12 题）^q12

A signal $q(t)$, zero for $t<0$, has（某信号 $q(t)$ 在 $t<0$ 时为零，其拉普拉斯变换为）

$$
Q(s)=\frac{2-4e^{-2s}}{s+3}.
$$

Find $q(3)$.（求 $q(3)$。）

> [!success] Answer（答案）
> $q(3)=-0.1989$

> [!abstract] 知识点讲解
> 见 11.2 时移与阶跃延迟 与 11.4 有延迟因子的部分分式。
>
> - $e^{-2s}$ 把第二项整体延迟 $2$ s。
> - $q(t)$ 是两项因果指数之和，在 $t=3$ 时两项都已开启。
> - 注意第二项的指数是 $-3(t-2)$，不是 $-3t$。

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

## 13. Question 13（第 13 题）^q13

A system has transfer function（某系统的传递函数为）

$$
G(s)=k\left(1+\frac{1}{\tau_i s}\right),
\qquad k=2,\quad \tau_i=0.5\ \mathrm{s}.
$$

Its input is $u(t)=H(t)$. Using the integral property, find the output $y(t)$ at $t=3$ s.（输入为单位阶跃，利用积分性质求 $t=3$ s 时的输出 $y(3)$。）

> [!success] Answer（答案）
> $y(3)=14.00$

> [!abstract] 知识点讲解
> 见 11.2 积分与微分 与 11.3 拉普拉斯变换与系统。
>
> - $1/s$ 在时域对应一次积分。
> - 传递函数可拆成常数项与 $1/s$ 项，分别对应比例与斜坡。
> - 输出为 $Y(s)=G(s)U(s)$，不要漏掉输入本身的 $1/s$。

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

## 14. Question 14（第 14 题）^q14

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
> 见 11.3 解微分方程 与 7.3 性质（二阶微分）。
>
> - $\mathcal L\{\ddot y\}=s^2Y(s)-sy(0^-)-\dot y(0^-)$。
> - 本题没有输入，方程右边为零；初始条件移到右边成为常数。
> - 只有 $\dot y(0)$ 会产生右端常数，$s$ 乘的是 $y(0)$。

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

## 15. Question 15（第 15 题）^q15

Solve（求解）

$$
\ddot y+5\dot y+6y=6H(t),
\qquad y(0^-)=2,\quad \dot y(0^-)=-1.
$$

Give $y(1)$.（求 $y(1)$。）

> [!success] Answer（答案）
> $y(1)=1.221$

> [!abstract] 知识点讲解
> 见 11.3 用拉普拉斯变换解微分方程。
>
> - 把输入和初始条件一起变换。
> - $\mathcal L\{\ddot y\}=s^2Y-2s+1$，$\mathcal L\{5\dot y\}=5sY-10$。
> - 整理后做部分分式，再反变换。

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

## 16. Question 16（第 16 题）^q16

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
> 见 11.3 零输入响应与零状态响应。
>
> - 初始条件与输入同时进入 $Y(s)$。
> - 分母为 $(s+2)^2$，看似会出现 $te^{-2t}$，但分子恰好把瞬态项约掉。
> - 系统从平衡点出发，输入恰好维持这个平衡。

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

## 17. Question 17（第 17 题）^q17

A current source $u(t)=tH(t)$ A drives a capacitor $C=0.25$ F in parallel with an inductor $L=1$ H. Both start with zero energy. Find the maximum value of the voltage $y(t)$ across them for $t\ge0$, in volts.（电流源 $u(t)=tH(t)$ A 驱动并联的 $C=0.25$ F 与 $L=1$ H，初始储能为零。求 $t\ge0$ 时并联端电压 $y(t)$ 的最大值，单位为 V。）

> [!success] Answer（答案）
> $2.000$ V

> [!abstract] 知识点讲解
> 见 11.3 拉普拉斯变换与系统 与 7.3 性质（积分与卷积）。
>
> - 并联阻抗 $Z(s)=sL\parallel \dfrac{1}{sC}$。
> - 电流源 $tH(t)$ 的变换为 $1/s^2$。
> - 反变换后求余弦函数的最大值。

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

## 18. Question 18（第 18 题）^q18

Initial and final value theorems（初值定理与终值定理）

A system has（某系统的传递函数为）

$$
G(s)=\frac{120}{s^2+6s}.
$$

Use the final value theorem to find $\lim_{t\to\infty}h(t)$ for the impulse response $h(t)$.（用终值定理求冲激响应 $h(t)$ 的终值。）

> [!success] Answer（答案）
> $\displaystyle\lim_{t\to\infty}h(t)=20.00$

> [!abstract] 知识点讲解
> 见 11.3 初值和终值。
>
> - 冲激响应的变换就是 $G(s)$，所以要求 $\lim_{t\to\infty}h(t)$ 就对 $G(s)$ 用终值定理。
> - 先检查 $sG(s)$ 的极点是否全在开左半平面。
> - 条件是 $sG(s)$ 的全部极点在开左半平面，而不是 $G(s)$ 本身。

> [!example] 解答
> 计算
> $$sG(s)=\frac{120}{s+6}.$$
> 其唯一极点在 $s=-6$，属于开左半平面，终值定理适用。于是
> $$h(\infty)=\lim_{s\to0}sG(s)
> =\lim_{s\to0}\frac{120}{s+6}=\frac{120}{6}=20.00.$$
> 校验：$G(s)$ 的极点为 $s=0$ 与 $s=-6$，$h(t)$ 含常数项 $20$ 与衰减项，终值确实为 $20$。

---

## 19. Question 19（第 19 题）^q19

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
> 见 11.3 初值和终值。
>
> - $Y(s)=G(s)/s$，因此两个定理都用 $sY(s)=G(s)$。
> - 初值是 $G(s)$ 在 $s\to\infty$ 时的极限。
> - 终值是 $G(0)$。

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

## 20. Question 20（第 20 题）^q20

An RC lowpass with（某 RC 低通的传递函数为）

$$
G(s)=\frac{1}{2s+1}
$$

(time in seconds) is driven by the ramp $u(t)=tH(t)$ V, starting from rest. Find $\lim_{t\to\infty}\left[u(t)-y(t)\right]$ in volts.（时间单位为秒。系统由斜坡电压 $u(t)=tH(t)$ 驱动，初始状态为零。求稳态跟踪误差 $\lim_{t\to\infty}[u(t)-y(t)]$，单位为 V。）

> [!success] Answer（答案）
> $2.000$ V

> [!abstract] 知识点讲解
> 见 11.3 初值和终值 与 8.1 传递函数。
>
> - 误差 $E(s)=U(s)\left[1-G(s)\right]$。
> - 斜坡的变换为 $1/s^2$。
> - 对 $sE(s)$ 用终值定理前，先检查它的极点。

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

## 21. Question 21（第 21 题）^q21

For which one of these transfer functions does the final value theorem correctly give $\lim_{t\to\infty}h(t)$ for the impulse response?（下列哪个传递函数可以用终值定理正确求出冲激响应的终值？）

(a) $G(s)=\dfrac{12}{s-4}$（有右半平面极点）
(b) $G(s)=\dfrac{12}{s^2+4}$（有虚轴极点）
(c) $G(s)=\dfrac{12}{s^4+4}$（有右半平面极点）
(d) $G(s)=\dfrac{12}{s(s+4)}$ **✓**（$sG(s)$ 的极点全在开左半平面）

> [!success] Answer（答案）
> (d) $G(s)=\dfrac{12}{s(s+4)}$

> [!abstract] 知识点讲解
> 见 7.4 终值定理 与 11.3 初值和终值。
>
> - 终值定理成立的条件是 $sG(s)$ 的全部极点在开左半平面。
> - 不要只看 $G(s)$ 的极点：$G(s)$ 在原点有单极点时，$sG(s)$ 反而可能满足条件。
> - 右半平面极点或虚轴非零极点都会使极限不存在或定理失效。

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

### 2. System analysis with the Laplace transform (week 9)（用拉普拉斯变换分析系统，第 9 周）

Transfer functions, poles and stability（传递函数、极点与稳定性）

---

## 22. Question 22（第 22 题）^q22

Classify（对下列系统进行分类）

$$
G(s)=\frac{12}{s^2+4}.
$$

（原 PDF 文字层中分子丢失，依据反馈 $h(t)=6\sin2t\,H(t)$ 还原为 $12$。）

(a) BIBO stable but not exponentially stable（BIBO 稳定但非指数稳定）
(b) Marginally stable and not BIBO stable **✓**（临界稳定但不 BIBO 稳定）
(c) Unstable（不稳定）
(d) Exponentially stable（指数稳定）

> [!success] Answer（答案）
> (b) 临界稳定，但不 BIBO 稳定

> [!abstract] 知识点讲解
> 见 6.3 极点判据速查 与 11.6 二阶系统与稳定性的补充例题。
>
> - 极点 $\pm2j$ 是虚轴上的**单根**，所以临界稳定。
> - BIBO 稳定要求 $\int_0^\infty|h(t)|dt<\infty$，等幅正弦做不到。
> - 虚轴单极点不等于不稳定，也不等于 BIBO 稳定。

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

## 23. Question 23（第 23 题）^q23

A transfer function $G(s)$ has poles at $0$ and $-0.2\pm j$, with no pole–zero cancellation. Which description is correct?（某传递函数 $G(s)$ 的极点在 $0$ 和 $-0.2\pm j$，且没有零极点抵消。下列描述哪个正确？）

(a) Marginally stable, but not BIBO stable **✓**（临界稳定，但不 BIBO 稳定）
(b) Marginally stable and BIBO stable（临界稳定且 BIBO 稳定）
(c) Exponentially stable（指数稳定）
(d) Unstable（不稳定）

> [!success] Answer（答案）
> (a) 临界稳定，但不 BIBO 稳定

> [!abstract] 知识点讲解
> 见 6.3 极点判据速查 与 11.6 例 2（虚轴单极点与原点极点）。
>
> - 逐个检查极点：$-0.2\pm j$ 在开左半平面，$0$ 是虚轴上的单极点。
> - 极点在闭左半平面、虚轴极点为单根、且至少有一个虚轴极点，就是临界稳定。
> - 原点极点使 $h(t)$ 含非零常数项，绝对值积分发散。

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

## 24. Question 24（第 24 题）^q24

Which transfer function is marginally stable?（哪个传递函数是临界稳定的？）

(a) $\dfrac{s+2}{(s^2+4)(s+1)}$ **✓**
(b) $\dfrac{s-2}{(s+1)(s+3)}$
(c) $\dfrac{s+2}{s^2(s+3)}$
(d) $\dfrac{s+2}{(s^2+4)^2}$

> [!success] Answer（答案）
> (a) $\dfrac{s+2}{(s^2+4)(s+1)}$

> [!abstract] 知识点讲解
> 见 6.3 极点判据速查。
>
> - 临界稳定：全部极点在闭左半平面，虚轴极点都是单根，且至少有一个虚轴极点。
> - 虚轴上的重极点对应 $t\sin\omega_0t$ 型增长项，属不稳定。
> - 零点不影响稳定性。

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

## 25. Question 25（第 25 题）^q25

Classify（对下列系统进行分类）

$$
G(s)=\frac{1}{s^4+4}.
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
> 见 6.3 极点判据速查 与 11.6 例 4（四阶多项式的极点）。
>
> - 用提示把分母分解成两个二次因式，分别求根。
> - 系数符号不能用来判断四阶及以上系统的稳定性。
> - 只要有一个右半平面极点，系统就不稳定。

> [!example] 解答
> 分解：
> $$s^2+2s+2=0\quad\Longrightarrow\quad s=-1\pm j,$$
> $$s^2-2s+2=0\quad\Longrightarrow\quad s=1\pm j.$$
> 后一对极点的实部为 $+1$，位于右半平面，$h(t)$ 含 $e^{t}\cos t$ 型增长项，无界。
>
> 系数检查也提醒一遍：$s^4+4$ 的 $s^3,s^2,s$ 系数均为零，不能因「系数看起来不坏」就判稳定。选 (d)。

---

## 26. Question 26（第 26 题）^q26

For（对于）

$$
G(s)=\frac{1}{s^2+9}
$$

with zero initial conditions, which bounded input produces an unbounded output?（零初始条件下，哪个有界输入会产生无界输出？）

（原 PDF 文字层中分子丢失，依据反馈「$G$ 的极点在 $\pm3j$」还原为 $1$。）

(a) $\cos(3t)H(t)$ **✓**
(b) $H(t)$
(c) $\cos(9t)H(t)$
(d) $e^{-3t}H(t)$

> [!success] Answer（答案）
> (a) $\cos(3t)H(t)$

> [!abstract] 知识点讲解
> 见 11.6 例 5（共振输入）。
>
> - 系统极点在 $\pm3j$，输入极点也在 $\pm3j$ 时，$Y(s)$ 出现**二重极点**。
> - 二重极点对应 $t\sin3t$ 型项，幅度随时间线性增长。
> - 输入频率必须与系统自然频率相同才会共振，$\cos9t$ 不会。

> [!example] 解答
> 输入 $\cos3tH(t)$ 的变换为
> $$U(s)=\frac{s}{s^2+9}.$$
> 输出：
> $$Y(s)=\frac{1}{s^2+9}\cdot\frac{s}{s^2+9}
> =\frac{s}{(s^2+9)^2}.$$
> 查表（或由 $t\sin\omega_0t$ 的变换）：
> $$y(t)=\frac{t}{6}\sin3t\,H(t),$$
> 幅度随 $t$ 线性增长，无界。
>
> 其余输入：$H(t)$ 给出 $y=\frac19\left(1-\cos3t\right)$；$\cos9t$ 与系统极点不重合，响应有界；$e^{-3t}H(t)$ 的极点在 $-3$，响应衰减。选 (a)。

---

## 27. Question 27（第 27 题）^q27

Partial fractions and inverse transforms（部分分式与反变换）

Find the impulse response of（求下列系统的冲激响应）

$$
G(s)=\frac{s+2}{s(s+1)}
$$

at $t=1$ s.（在 $t=1$ s 处的值。）

> [!success] Answer（答案）
> $h(1)=1.632$

> [!abstract] 知识点讲解
> 见 11.4 遮盖法求单实极点。
>
> - 写成 $\dfrac{A}{s}+\dfrac{B}{s+1}$。
> - 遮盖法：$A=\left.\dfrac{s+2}{s+1}\right|_{s=0}$，$B=\left.\dfrac{s+2}{s}\right|_{s=-1}$。
> - 反变换后代入 $t=1$。

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

## 28. Question 28（第 28 题）^q28

Write（写成）

$$
Y(s)=\frac{6}{s^2(s+3)}
=\frac{A}{s}+\frac{B}{s^2}+\frac{C}{s+3}.
$$

Find $A$.（求 $A$。）

（原 PDF 文字层中分子丢失，依据反馈「$6=As(s+3)+B(s+3)+Cs^2$」还原为 $6$。）

> [!success] Answer（答案）
> $A=-0.6667$

> [!abstract] 知识点讲解
> 见 11.4 重极点。
>
> - $B$、$C$ 可以直接遮盖，$A$ 不能。
> - 二重极点情形，最高次项系数用遮盖法，其余系数比较分子系数。
> - 令 $A+C=0$ 是常用的快捷方法。

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

## 29. Question 29（第 29 题）^q29

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
> 见 11.4 重极点。
>
> - 分母 $(s+1)^2$ 是二重极点，展开为 $\dfrac{A}{s+1}+\dfrac{B}{(s+1)^2}$。
> - $\dfrac{1}{(s+1)^2}\longleftrightarrow te^{-t}H(t)$。
> - 真分式的反变换没有冲激。

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

## 30. Question 30（第 30 题）^q30

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
> 见 11.4 共轭复极点。
>
> - 实极点部分用遮盖法；复极点部分配成完全平方。
> - $\dfrac{s+a}{(s+a)^2+\omega_0^2}\leftrightarrow e^{-at}\cos\omega_0t$，$\dfrac{\omega_0}{(s+a)^2+\omega_0^2}\leftrightarrow e^{-at}\sin\omega_0t$。
> - 正弦系数等于常数分子除以 $\omega_0$。

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

## 31. Question 31（第 31 题）^q31

（原 PDF 文字层中分子丢失，依据反馈「覆盖 $s=-3.1$ 得 $\frac{-3.1+3}{-3.1+1}$」还原为 $s+3$。）

$$
G(s)=\frac{s+3}{(s+1)(s+3.1)}
$$

has a zero very close to a pole. Find the coefficient of $e^{-3.1t}$ in the impulse response $g(t)$.（该传递函数的零点非常靠近一个极点。求冲激响应中 $e^{-3.1t}$ 项的系数。）

> [!success] Answer（答案）
> $0.04762$

> [!abstract] 知识点讲解
> 见 11.6 例 6（零点靠近极点）。
>
> - 系数用遮盖法求：$A_{3.1}=\left.\dfrac{s+3}{s+1}\right|_{s=-3.1}$。
> - 零点越靠近极点，残留系数越小；完全重合时该项消失。
> - 数值很小时不要误以为是零。

> [!example] 解答
> 部分分式：
> $$G(s)=\frac{A}{s+1}+\frac{A_{3.1}}{s+3.1}.$$
> 遮盖 $s=-3.1$：
> $$A_{3.1}=\left.\frac{s+3}{s+1}\right|_{s=-3.1}
> =\frac{-0.1}{-2.1}=0.04762.$$
> 零点 $-3$ 与极点 $-3.1$ 只差 $0.1$，所以 $e^{-3.1t}$ 项的系数很小。

---

## 32. Question 32（第 32 题）^q32

Find $y(3)$ where（求 $y(3)$，已知）

$$
Y(s)=\frac{4e^{-s}}{(s+1)(s+3)}.
$$

> [!success] Answer（答案）
> $y(3)=0.2657$

> [!abstract] 知识点讲解
> 见 11.4 有延迟因子的部分分式。
>
> - 先对有理部分做部分分式，再整体延迟 $1$ s。
> - 延迟后每一项都带 $H(t-1)$。
> - $t=3$ 时两项都开启。

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

## 33. Question 33（第 33 题）^q33

（原 PDF 文字层中分子丢失，依据反馈「$Y=\frac{s+4}{(s+1)(s+2)^2}$」还原为 $s+4$。）

$$
G(s)=\frac{s+4}{s^2+3s+2}
$$

is driven by $u(t)=e^{-2t}H(t)$ with zero initial conditions. Find $y(1)$.（系统在零初始条件下由 $u(t)=e^{-2t}H(t)$ 驱动。求 $y(1)$。）

> [!success] Answer（答案）
> $y(1)=0.4270$

> [!abstract] 知识点讲解
> 见 11.5 例 1（系统极点与输入极点重合）。
>
> - 输入极点 $-2$ 与系统极点 $-2$ 重合，$Y(s)$ 出现二重极点。
> - 二重极点产生 $te^{-2t}$ 项。
> - 系数要分别用遮盖法与求导或比较系数求。

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

## 34. Question 34（第 34 题）^q34

（原 PDF 文字层中分子丢失，依据反馈「$Y=\frac{3}{s(s+1)(s+3)}$」还原为 $1$。）

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
> 见 11.4 遮盖法求单实极点 与 11.5 拉普拉斯变换与系统。
>
> - 先把输入合并成一个分数，再乘传递函数。
> - $U(s)=\frac1s-\frac1{s+3}=\frac{3}{s(s+3)}$。
> - 三阶分母、三个单实极点，全部用遮盖法。

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

## 35. Question 35（第 35 题）^q35

（原 PDF 文字层中分子丢失，依据反馈「$\frac{4}{s(s+2)^2}$」还原为每节 $\frac{2}{s+2}$。）

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
> 见 11.4 重极点 与 11.6 例 7（级联不是同阶 Butterworth）。
>
> - 级联传递函数相乘。
> - 单位阶跃使 $Y(s)$ 多一个 $1/s$ 极点。
> - 二重极点产生 $te^{-2t}$ 项。

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

## 36. Question 36（第 36 题）^q36

（原 PDF 文字层中分子丢失，依据反馈「$U=\frac{s^2+2s+4}{s(s+4)}$」还原为 $4$。）

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
> 见 11.5 例 3（由输出反求输入）与 12.4 由输出反求输入（假分式先做除法）。
>
> - $U(s)=\dfrac{Y(s)}{G(s)}$。
> - 若 $U(s)$ 是假分式，先做多项式除法，常数项对应 $\delta(t)$。
> - 分子中的 $s^2+2s+4$ 会约掉系统的复极点，输出不振荡。

> [!example] 解答
> 由 $y$ 求 $Y$：
> $$Y(s)=\frac1s-\frac{1}{s+4}=\frac{4}{s(s+4)}.$$
> 求输入变换：
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

## 37. Question 37（第 37 题）^q37

Zeros（零点）

$G(s)$ has poles at $-2$ and $-5$, a single zero at $-1$, and DC gain $3$. The input is $u(t)=e^{-t}H(t)$, starting from rest. What is $y(t)$?（$G(s)$ 的极点在 $-2$、$-5$，零点在 $-1$，直流增益为 $3$。系统在零初始状态下由 $u(t)=e^{-t}H(t)$ 驱动。求 $y(t)$。）

(a) $\left(e^{-2t}-e^{-5t}\right)H(t)$（增益取错，$k=3$ 而不是 $30$）
(b) $y(t)=0$, because the zero at $-1$ blocks $e^{-t}$（误以为零点会阻断整个输出）
(c) $10\left(e^{-2t}-e^{-5t}\right)H(t)$ **✓**（正确结果）
(d) $y(t)$ contains a nonzero $e^{-t}$ term as well as $e^{-2t}$ and $e^{-5t}$ terms（误以为输入极点没有被抵消）

> [!success] Answer（答案）
> (c) $y(t)=10\left(e^{-2t}-e^{-5t}\right)H(t)$

> [!abstract] 知识点讲解
> 见 11.5 例 2（零点抵消输入极点）。
>
> - 先由直流增益定系数：$G(0)=\dfrac{k}{2\cdot5}=3$，故 $k=30$。
> - 零点 $-1$ 与输入极点 $-1$ 抵消，输出不含 $e^{-t}$。
> - 但系统的两个自然模态仍被激励。

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

## 38. Question 38（第 38 题）^q38

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
> 见 4.4 Bode 图 与 8.1 传递函数。
>
> - 通分并因式分解，找出极点和零点。
> - 每个极点贡献 $-20$ dB/dec；每个零点贡献 $+20$ dB/dec。
> - 原点处的极点使低频斜率为 $-20$ dB/dec。

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

## 39. Question 39（第 39 题）^q39

A filter（某滤波器）

$$
G(s)=K\frac{s+z}{s+5}
$$

has DC gain $1$ and must have a high-frequency gain of $-30$ dB. Where must the zero be? Give $z$ in rad/s (the zero is at $s=-z$).（要求直流增益为 $1$，高频增益为 $-30$ dB。零点应放在哪里？给出 $z$，单位 rad/s。）

> [!success] Answer（答案）
> $z=158.1$ rad/s

> [!abstract] 知识点讲解
> 见 8.1 传递函数 与 4.4 Bode 图。
>
> - 直流增益 $G(0)$ 由低频极限得到。
> - 高频增益由 $s\to\infty$ 的比值决定，等于 $K$。
> - $-30$ dB 对应 $K=10^{-30/20}$。

> [!example] 解答
> 低频极限：
> $$G(0)=K\frac{z}{5}=1\quad\Longrightarrow\quad Kz=5.$$
> 高频极限：
> $$\lim_{s\to\infty}G(s)=K=10^{-30/20}=0.03162.$$
> 由 $Kz=5$：
> $$z=\frac{5}{K}=\frac{5}{0.03162}=158.1\ \mathrm{rad/s}.$$
> 检查：高频增益 $-20\log_{10}K=-20\log_{10}0.03162=30$ dB 的衰减，即 $-30$ dB。

---

## 40. Question 40（第 40 题）^q40

A 50 Hz hum notch filter is（50 Hz 工频陷波器为）

$$
G(s)=\frac{s^2+\omega_n^2}{s^2+2\zeta\omega_ns+\omega_n^2},
\qquad \omega_n=2\pi\cdot50\ \mathrm{rad/s},\quad \zeta=0.5.
$$

Find $\left|G(j\omega)\right|$ at 25 Hz.（求 25 Hz 处的幅值。）

> [!success] Answer（答案）
> $|G|=0.8321$

> [!abstract] 知识点讲解
> 见 11.7 例 7（Notch 滤波器）。
>
> - $25$ Hz 对应 $\omega=\omega_n/2$。
> - 分母的实部、虚部都按 $\omega_n^2$ 的倍数化简。
> - 分子的 $s^2+\omega_n^2$ 在 $s=j\omega$ 时等于 $\omega_n^2-\omega^2$。

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

## 41. Question 41（第 41 题）^q41

### 3. Filter design (week 10)（滤波器设计，第 10 周）

Filter specifications and first- and second-order filters（滤波器指标与一、二阶滤波器）

Why can an ideal lowpass filter $G(j\omega)=p_{2\omega_c}(\omega)$ not be built as a real-time circuit?（为什么理想低通滤波器 $G(j\omega)=p_{2\omega_c}(\omega)$ 无法用实时电路实现？）

(a) Its gain is infinite at $\omega_c$（在 $\omega_c$ 处增益无穷大）
(b) Its phase is not linear（相位不是线性的）
(c) Its impulse response $\sin(\omega_ct)/(\pi t)$ is nonzero for $t<0$, so it is noncausal **✓**（冲激响应为 $\sin(\omega_ct)/(\pi t)$，在 $t<0$ 时已非零，非因果）
(d) It has a pole in the right half plane（右半平面有极点）

> [!success] Answer（答案）
> (c) 冲激响应在 $t<0$ 时非零，非因果

> [!abstract] 知识点讲解
> 见 8.3 理想低通滤波器。
>
> - 实时系统必须因果：$h(t)=0$（$t<0$）。
> - 理想低通频谱是矩形，反变换得到 sinc 型冲激响应，延伸到 $t\to-\infty$。
> - 幅值是 $1$ 或 $0$，有界；相位为零，是线性的；它不是有理函数，没有极点。

> [!example] 解答
> 反变换：
> $$h(t)=\frac{1}{2\pi}\int_{-\omega_c}^{\omega_c}e^{j\omega t}d\omega
> =\frac{1}{2\pi}\cdot\frac{e^{j\omega_ct}-e^{-j\omega_ct}}{jt}
> =\frac{\sin\omega_ct}{\pi t}.$$
> 对任意 $t<0$，$h(t)$ 一般不恒为零，所以系统在输入加之前已有输出，非因果。
>
> 理想低通只能作为理论模型，实际电路只能用有理传递函数逼近它。选 (c)。

---

## 42. Question 42（第 42 题）^q42

At the $-3$ dB frequency of a first-order RC lowpass, compared with DC, the output（一阶 RC 低通在 $-3$ dB 频率处，与直流相比，输出）

(a) amplitude is $1/2$ and power is $1/4$（幅值 $1/2$、功率 $1/4$）
(b) amplitude is $1/\sqrt2$ and power is $1/2$ **✓**（幅值 $1/\sqrt2$、功率 $1/2$）
(c) amplitude and power are both $0.7$（幅值和功率都约为 $0.7$）
(d) amplitude is $1/2$ and power is $1/\sqrt2$（幅值 $1/2$、功率 $1/\sqrt2$）

> [!success] Answer（答案）
> (b) 幅值 $1/\sqrt2$，功率 $1/2$

> [!abstract] 知识点讲解
> 见 8.4 $-3$ dB 截止频率 与 4.4 Bode 图。
>
> - $-3$ dB 的幅值比例为 $1/\sqrt2\approx0.707$。
> - 功率与幅值平方成正比，所以功率比例为 $1/2$。
> - 幅值 $1/2$ 对应 $-6$ dB。

> [!example] 解答
> 分贝定义：
> $$20\log_{10}\left|G\right|=-3\quad\Longrightarrow\quad |G|=10^{-3/20}=0.7079\approx\frac{1}{\sqrt2}.$$
> 精确计算：
> $$20\log_{10}\frac{1}{\sqrt2}=-10\log_{10}2\approx-3.01\ \mathrm{dB}.$$
> 功率比例：
> $$|G|^2=\frac12.$$
> 选 (b)。

---

## 43. Question 43（第 43 题）^q43

Which transfer function is a bandpass filter?（哪个传递函数是带通滤波器？）

(a) $\dfrac{10s}{s^2+10s+100}$ **✓**
(b) $\dfrac{100}{s^2+10s+100}$
(c) $\dfrac{s^2+100}{s^2+10s+100}$
(d) $\dfrac{s^2}{s^2+10s+100}$

> [!success] Answer（答案）
> (a) $\dfrac{10s}{s^2+10s+100}$

> [!abstract] 知识点讲解
> 见 8.2 典型滤波器 与 10.6 传递函数与滤波器。
>
> - 看 $\omega=0$ 与 $\omega\to\infty$ 两端增益。
> - 带通：两端都为零，中间通。
> - 带阻：两端都非零，中间有一个零点。

> [!example] 解答
> 逐项检查两端增益：
>
> (a) $G(0)=0$；$s\to\infty$ 时分子分母同阶，$G\to0$。两端为零，中间在 $\omega=10$ 处
> $$|G(j10)|=\left|\frac{10\cdot10j}{-100+100j+100}\right|=1,$$
> 是带通。
>
> (b) $G(0)=1$，高频趋于 $0$：低通。
>
> (c) 分子零点 $\pm10j$，在 $10$ rad/s 处增益为零；两端增益为 $1$：带阻。
>
> (d) $G(0)=0$，高频趋于 $1$：高通。
>
> 选 (a)。

---

## 44. Question 44（第 44 题）^q44

Find the $-3$ dB frequency of the second-order lowpass（求二阶低通的 $-3$ dB 频率）

$$
G(s)=\frac{400}{s^2+20s+400},
$$

in rad/s.

> [!success] Answer（答案）
> $25.44$ rad/s

> [!abstract] 知识点讲解
> 见 11.7 例 2（二阶低通的截止频率）与 8.4 $-3$ dB 截止频率。
>
> - 与标准形式对照：$\omega_n^2=400$，$2\zeta\omega_n=20$。
> - 令 $x=(\omega/\omega_n)^2$，把 $|G|^2=1/2$ 化成 $x$ 的二次方程。
> - 二阶低通的 $-3$ dB 频率不等于 $\omega_n$。

> [!example] 解答
> 对照标准形式：
> $$\omega_n=20,\qquad \zeta=\frac{20}{2\omega_n}=0.5.$$
> 幅频平方：
> $$|G(j\omega)|^2=\frac{1}{\left(1-x\right)^2+\left(2\zeta\right)^2x},\qquad x=\left(\frac{\omega}{\omega_n}\right)^2.$$
> 代入 $\zeta=0.5$，即 $(2\zeta)^2=1$：
> $$|G|^2=\frac{1}{(1-x)^2+x}=\frac{1}{x^2-x+1}.$$
> 令 $|G|^2=1/2$：
> $$x^2-x+1=2\quad\Longrightarrow\quad x^2-x-1=0.$$
> 取正根：
> $$x=\frac{1+\sqrt5}{2}=1.618.$$
> 所以
> $$\omega_c=20\sqrt{1.618}=25.44\ \mathrm{rad/s}.$$

---

## 45. Question 45（第 45 题）^q45

A first-order highpass（一阶高通）

$$
G(s)=\frac{s}{s+\omega_c},
\qquad \omega_c=2\pi\cdot100\ \mathrm{rad/s}
$$

is used to suppress a 50 Hz hum. By how many dB is the 50 Hz hum attenuated? (Give a positive number.)（用来抑制 50 Hz 工频噪声。50 Hz 分量被衰减多少 dB？给正数。）

> [!success] Answer（答案）
> $6.990$ dB

> [!abstract] 知识点讲解
> 见 11.7 例 3（一阶高通的衰减）。
>
> - 把频率比化成 $f/f_c$，避免每步都带 $2\pi$。
> - $|G(j\omega)|=\dfrac{\omega/\omega_c}{\sqrt{1+(\omega/\omega_c)^2}}$。
> - 衰减量 $=-20\log_{10}|G|$。

> [!example] 解答
> 频率比：
> $$\frac{f}{f_c}=\frac{50}{100}=0.5.$$
> 幅值：
> $$|G|=\frac{0.5}{\sqrt{1+0.5^2}}=\frac{0.5}{\sqrt{1.25}}=0.4472.$$
> 衰减量：
> $$-20\log_{10}0.4472=6.990\ \mathrm{dB}.$$

---

## 46. Question 46（第 46 题）^q46

A first-order lowpass（一阶低通）

$$
G(s)=\frac{k}{s+a},
\qquad k,a>0
$$

must have DC gain $+12$ dB and a gain 3 dB below the DC gain at $f=1$ kHz. Find $k$ (units rad/s).（要求直流增益为 $+12$ dB，且在 $f=1$ kHz 处比直流增益低 3 dB。求 $k$，单位 rad/s。）

> [!success] Answer（答案）
> $k=2.501\times10^4$ rad/s

> [!abstract] 知识点讲解
> 见 11.7 例 4（由指标反求参数）。
>
> - 一阶低通的 $-3$ dB 频率等于极点频率，即 $\omega=a$。
> - 直流增益 $G(0)=k/a$。
> - $+12$ dB 对应 $10^{12/20}=3.981$。

> [!example] 解答
> $-3$ dB 点：
> $$a=2\pi\times1000=6283\ \mathrm{rad/s}.$$
> 直流增益：
> $$20\log_{10}\frac{k}{a}=12\quad\Longrightarrow\quad\frac{k}{a}=10^{0.6}=3.981.$$
> 所以
> $$k=3.981\times6283=2.501\times10^4\ \mathrm{rad/s}.$$

---

## 47. Question 47（第 47 题）^q47

Which transfer function is an exponentially stable allpass filter ($|G(j\omega)|=1$ for all $\omega$)?（哪个传递函数是指数稳定的全通滤波器，即对所有 $\omega$ 都有 $|G(j\omega)|=1$？）

(a) $\dfrac{s}{s+3}$（一阶高通）
(b) $\dfrac{3}{s+3}$（一阶低通）
(c) $\dfrac{s+3}{s-3}$（幅值为 $1$，但极点 $+3$ 不稳定）
(d) $\dfrac{s-3}{s+3}$ **✓**（极点 $-3$、零点 $+3$，指数稳定全通）

> [!success] Answer（答案）
> (d) $\dfrac{s-3}{s+3}$

> [!abstract] 知识点讲解
> 见 11.7 例 5（全通滤波器的相移）与 8.2 典型滤波器。
>
> - 全通：零点与极点关于虚轴对称，且成镜像。
> - 一阶全通形式为 $\dfrac{s-a}{s+a}$。
> - 指数稳定要求极点在开左半平面。

> [!example] 解答
> 检查 (d)：
> $$G(j\omega)=\frac{j\omega-3}{j\omega+3}.$$
> 取模：
> $$|G(j\omega)|=\frac{\left|j\omega-3\right|}{\left|j\omega+3\right|}
> =\frac{\sqrt{\omega^2+9}}{\sqrt{\omega^2+9}}=1.$$
> 极点 $s=-3$ 在开左半平面，系统指数稳定。
>
> 其余选项：$(a)$ 是 $G(0)=0$ 的高通；$(b)$ 是高频趋于 $0$ 的低通；$(c)$ 的极点 $+3$ 在右半平面，不稳定。选 (d)。

---

## 48. Question 48（第 48 题）^q48

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
> 见 11.7 例 5（全通滤波器的相移）与 4.1 正弦稳态的核心结论。
>
> - 正弦稳态：输出为 $|G(j\omega)|\cos(\omega t+\angle G(j\omega))$。
> - $G(j10)=\dfrac{10-10j}{10+10j}=-j$。
> - $-j$ 的相位是 $-90^\circ$，模为 $1$。

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

## 49. Question 49（第 49 题）^q49

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
> 见 11.7 例 6（延迟线）。
>
> - $G(j\omega)=e^{-j2\omega}$，模恒为 $1$。
> - 相位 $-2\omega$ 与频率成正比，称为线性相位。
> - 指数函数不是有理函数，没有极点。

> [!example] 解答
> 代入 $s=j\omega$：
> $$G(j\omega)=e^{-j2\omega}.$$
> 模：
> $$\left|e^{-j2\omega}\right|=1.$$
> 相位：
> $$\angle G(j\omega)=-2\omega.$$
> 幅度不变，只引入与频率成正比的相位延迟，相当于延迟 $2$ s，是全通系统。选 (b)。

---

## 50. Question 50（第 50 题）^q50

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
> 见 11.8 例 2（Butterworth 原型到高通）与 8.5 Butterworth 滤波器。
>
> - 低通到高通：$s\to\omega_c/s$。
> - 代入后分子分母同乘 $s^2$。
> - 中间项变为 $\omega_c\sqrt2$，常数项变为 $\omega_c^2$。

> [!example] 解答
> 代入 $s=50/s$：
> $$G_{HP}(s)=\frac{1}{\dfrac{2500}{s^2}+\dfrac{50\sqrt2}{s}+1}.$$
> 分子分母同乘 $s^2$：
> $$G_{HP}(s)=\frac{s^2}{s^2+50\sqrt2\,s+2500}.$$
> 计算系数：
> $$50\sqrt2=70.71,\qquad 50^2=2500.$$
> 选 (b)。

---

## 51. Question 51（第 51 题）^q51

In a two-way loudspeaker crossover, the tweeter (a $4\ \Omega$ resistor) is fed through a series capacitor $C$, giving the highpass（在二分频音箱中，高音单元（$4\ \Omega$ 电阻）串联电容 $C$，得到高通）

$$
G_H(s)=\frac{4Cs}{4Cs+1}.
$$

Find $C$ in $\mu$F so the $-3$ dB frequency is 3 kHz.（求使 $-3$ dB 频率为 3 kHz 的电容值，单位 $\mu$F。）

> [!success] Answer（答案）
> $C=13.26\ \mu$F

> [!abstract] 知识点讲解
> 见 8.4 $-3$ dB 截止频率 与 8.2 典型滤波器。
>
> - 一阶高通写成标准形式 $\dfrac{s}{s+\omega_c}$ 后，$\omega_c=1/(4C)$。
> - $-3$ dB 频率等于极点频率。
> - 由 $\omega_c=2\pi f_c$ 反解 $C$。

> [!example] 解答
> 整理为标准形式：
> $$G_H(s)=\frac{s}{s+\dfrac{1}{4C}}.$$
> 截止频率：
> $$\omega_c=\frac{1}{4C}.$$
> 令 $\omega_c=2\pi\times3000$：
> $$C=\frac{1}{4\cdot2\pi\cdot3000}.$$
> 计算：
> $$4\cdot2\pi\cdot3000=75398.2,$$
> $$C=\frac{1}{75398.2}=1.326\times10^{-5}\ \mathrm{F}=13.26\ \mu\mathrm{F}.$$

---

## 52. Question 52（第 52 题）^q52

A bandstop filter is built as the parallel sum of a first-order lowpass and a first-order highpass（带阻滤波器由一阶低通与一阶高通并联相加构成）：

$$
G(s)=\frac{10}{s+10}+\frac{s}{s+1000}.
$$

Find $|G(j100)|$.（求 $|G(j100)|$。）

> [!success] Answer（答案）
> $|G(j100)|=0.01980$

> [!abstract] 知识点讲解
> 见 8.2 典型滤波器 与 0.1 复数与相量。
>
> - 并联相加是**复数相加**，不是幅值相加。
> - 先把每一项有理化，写成 $a+jb$。
> - 虚部可能相互抵消，只剩实部。

> [!example] 解答
> 第一项：
> $$\frac{10}{10+100j}=\frac{10(10-100j)}{10^2+100^2}
> =\frac{100-1000j}{10100}=0.0099-0.0990j.$$
> 第二项：
> $$\frac{100j}{1000+100j}=\frac{100j(1000-100j)}{1000^2+100^2}
> =\frac{10000+100000j}{1010000}=0.0099+0.0990j.$$
> 相加，虚部抵消：
> $$G(j100)=0.0198.$$
> 所以
> $$|G(j100)|=0.01980.$$

---

## 53. Question 53（第 53 题）^q53

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
> 见 8.2 典型滤波器 与 0.1 复数与相量。
>
> - 同一分母的分式可以直接相加。
> - 并联相加是复数值相加，不是模相加。
> - 互补的低通与高通并联，幅值合起来恒为 $1$。

> [!example] 解答
> 通分相加：
> $$G(s)=\frac{\omega_c}{s+\omega_c}+\frac{s}{s+\omega_c}
> =\frac{s+\omega_c}{s+\omega_c}=1.$$
> 所以
> $$|G(j\omega)|=1\quad\text{对所有 }\omega.$$
> 校验 $\omega_c$ 处：
> $$G_L(j\omega_c)=\frac{\omega_c}{\omega_c+j\omega_c}=\frac{1}{1+j}=\frac{1-j}{2},$$
> $$G_H(j\omega_c)=\frac{j\omega_c}{\omega_c+j\omega_c}=\frac{j}{1+j}=\frac{1+j}{2},$$
> 两者相加为 $1$，不是 $\sqrt2$（那是把模相加的错误）。选 (d)。

---

## 54. Question 54（第 54 题）^q54

Butterworth filters and order selection（Butterworth 滤波器与阶数选择）

A second-order lowpass with no zeros has poles at $-10^4\pm j10^4$ rad/s and unit DC gain. It is a Butterworth filter. Find its $-3$ dB cutoff $\omega_c$ in rad/s.（某无零点的二阶低通极点在 $-10^4\pm j10^4$ rad/s，直流增益为 $1$，且为 Butterworth 滤波器。求其 $-3$ dB 截止频率 $\omega_c$，单位 rad/s。）

> [!success] Answer（答案）
> $\omega_c=1.414\times10^4$ rad/s

> [!abstract] 知识点讲解
> 见 11.8 例 4（由极点求二阶 Butterworth 的截止频率）与 8.5 Butterworth 滤波器。
>
> - 极点到原点的距离为 $\omega_n$。
> - 二阶 Butterworth 的阻尼比固定为 $\zeta=1/\sqrt2$。
> - Butterworth 的 $-3$ dB 频率等于 $\omega_n$。

> [!example] 解答
> 由极点求 $\omega_n$：
> $$\omega_n=\sqrt{(10^4)^2+(10^4)^2}=\sqrt2\times10^4.$$
> 验证阻尼比：
> $$\zeta=\frac{\left|\operatorname{Re}p\right|}{\omega_n}
> =\frac{10^4}{\sqrt2\times10^4}=\frac{1}{\sqrt2},$$
> 正是二阶 Butterworth 的特征。
>
> Butterworth 在 $\omega=\omega_n$ 处恰好 $-3$ dB，故
> $$\omega_c=\omega_n=\sqrt2\times10^4=1.414\times10^4\ \mathrm{rad/s}.$$

---

## 55. Question 55（第 55 题）^q55

A second-order Butterworth lowpass with $f_c=100$ Hz has transfer function（二阶 Butterworth 低通的截止频率为 $100$ Hz，传递函数为）

$$
\frac{\omega_c^2}{s^2+a\,s+\omega_c^2}.
$$

Find $a$ in rad/s.（求 $a$，单位 rad/s。）

> [!success] Answer（答案）
> $a=888.6$ rad/s

> [!abstract] 知识点讲解
> 见 11.8 例 3（二阶 Butterworth 的阻尼比）。
>
> - 二阶 Butterworth 分母为 $s^2+\sqrt2\,\omega_cs+\omega_c^2$。
> - 因此 $a=\sqrt2\,\omega_c$。
> - 注意 $\omega_c$ 要用 rad/s，不是 Hz。

> [!example] 解答
> 截止频率：
> $$\omega_c=2\pi\times100=628.3\ \mathrm{rad/s}.$$
> 二阶 Butterworth 分母的标准形式给出
> $$a=\sqrt2\,\omega_c=\sqrt2\times628.3=888.6\ \mathrm{rad/s}.$$

---

## 56. Question 56（第 56 题）^q56

A fifth-order Butterworth lowpass has $\omega_c=1000$ rad/s. Find the real part of the pole pair closest to the imaginary axis.（五阶 Butterworth 低通的 $\omega_c=1000$ rad/s。求最靠近虚轴的一对极点的实部。）

> [!success] Answer（答案）
> $-309.0$ rad/s

> [!abstract] 知识点讲解
> 见 11.8 例 5（高阶 Butterworth 的极点）。
>
> - $n$ 阶 Butterworth 的极点均匀分布在左半平面半径为 $\omega_c$ 的圆上。
> - 从正实轴量起，角度为 $90^\circ+\dfrac{180^\circ(2k+1)}{2n}$。
> - 最靠近虚轴的极点角度最接近 $90^\circ$。

> [!example] 解答
> 五阶的极点角度间隔为 $180^\circ/5=36^\circ$，左半平面内的五个角度为
> $$108^\circ,\ 144^\circ,\ 180^\circ,\ 216^\circ,\ 252^\circ.$$
> 最靠近虚轴的是 $108^\circ$ 与 $252^\circ$ 这一对（与 $90^\circ$ 相差 $18^\circ$）。实部：
> $$1000\cos108^\circ=1000\times(-0.3090)=-309.0\ \mathrm{rad/s}.$$

---

## 57. Question 57（第 57 题）^q57

A third-order Butterworth highpass filter with cutoff frequency 100 Hz is used to suppress a 50 Hz hum. By how many dB is the hum attenuated? (Give a positive number.)（三阶 Butterworth 高通截止频率为 100 Hz，用于抑制 50 Hz 工频噪声。50 Hz 分量被衰减多少 dB？给正数。）

> [!success] Answer（答案）
> $18.13$ dB

> [!abstract] 知识点讲解
> 见 11.8 例 6（Butterworth 衰减计算）。
>
> - $n$ 阶 Butterworth 高通：$|G|^2=\dfrac{1}{1+\left(f_c/f\right)^{2n}}$。
> - 这里 $f_c/f=2$，$2n=6$。
> - 衰减量 $=10\log_{10}\left[1+\left(f_c/f\right)^{2n}\right]$。

> [!example] 解答
> 幅频平方：
> $$|G|^2=\frac{1}{1+\left(\frac{100}{50}\right)^6}=\frac{1}{1+2^6}=\frac{1}{65}.$$
> 衰减量：
> $$-10\log_{10}\frac{1}{65}=10\log_{10}65=18.13\ \mathrm{dB}.$$

---

## 58. Question 58（第 58 题）^q58

Two identical second-order Butterworth lowpass sections, each with cutoff $\omega_c$, are cascaded. Which statement about the cascade is correct?（两个相同的二阶 Butterworth 低通节（各截止频率 $\omega_c$）级联。下列关于级联系统的说法哪个正确？）

(a) The gain at $\omega_c$ is $-6.02$ dB, and the cascade is a fourth-order Butterworth filter with cutoff $\omega_c$（增益对，但级联仍是四阶 Butterworth）
(b) The gain at $\omega_c$ is $-3.01$ dB, and the cascade is a fourth-order Butterworth filter with cutoff $\omega_c$（增益与阶数判断都错）
(c) The gain at $\omega_c$ is $-12.04$ dB, and the cascade is not a fourth-order Butterworth filter（增益重复计算了）
(d) The gain at $\omega_c$ is $-6.02$ dB, and the cascade is not a fourth-order Butterworth filter **✓**（增益 $-6.02$ dB，且级联不是四阶 Butterworth）

> [!success] Answer（答案）
> (d) $\omega_c$ 处增益 $-6.02$ dB，级联不是四阶 Butterworth

> [!abstract] 知识点讲解
> 见 11.8 例 7（级联不是同阶 Butterworth）。
>
> - 级联时增益相乘，$T$ 形同频叠加。
> - 每节在 $\omega_c$ 处为 $-3.01$ dB，两节共 $-6.02$ dB。
> - $n$ 阶 Butterworth 有 $n$ 个**互不相同**的极点；级联系统的极点是二重的。

> [!example] 解答
> 每节在 $\omega_c$ 处：
> $$|G_1(j\omega_c)|=\frac{1}{\sqrt2}.$$
> 级联增益：
> $$|G_1|^2=\frac12,\qquad 20\log_{10}\frac12=-6.02\ \mathrm{dB}.$$
> 极点结构：每节极点为 $\omega_c e^{\pm j135^\circ}$，级联后只是把这两个极点变成二重极点。四阶 Butterworth 的极点在 $112.5^\circ,157.5^\circ,202.5^\circ,247.5^\circ$，四个互不相同。所以增益相同不代表是四阶 Butterworth。选 (d)。

---

## 59. Question 59（第 59 题）^q59

A second-order Butterworth highpass has cutoff 6 kHz, so（二阶 Butterworth 高通的截止频率为 6 kHz，因此）

$$
|G(j\omega)|^2=\frac{1}{1+\left(\omega_c/\omega\right)^4}.
$$

At what frequency, in Hz, is its gain $-30$ dB?（在哪个频率处增益为 $-30$ dB？单位 Hz。）

> [!success] Answer（答案）
> $1067$ Hz

> [!abstract] 知识点讲解
> 见 11.8 例 6（Butterworth 衰减计算）。
>
> - 设衰减量等于 $30$ dB：$10\log_{10}\left[1+\left(f_c/f\right)^4\right]=30$。
> - 得到 $\left(f_c/f\right)^4=10^3-1=999$。
> - 再开四次方。

> [!example] 解答
> 由
> $$10\log_{10}\left[1+\left(\frac{f_c}{f}\right)^4\right]=30$$
> 得
> $$1+\left(\frac{f_c}{f}\right)^4=10^3\quad\Longrightarrow\quad\left(\frac{f_c}{f}\right)^4=999.$$
> 开四次方：
> $$\frac{f_c}{f}=999^{1/4}=5.623.$$
> 所以
> $$f=\frac{6000}{5.623}=1067\ \mathrm{Hz}.$$

---

## 60. Question 60（第 60 题）^q60

A fourth-order Butterworth lowpass must lose at most 1 dB at 1 kHz. What is the smallest cutoff frequency $f_c$ (the $-3$ dB frequency), in kHz?（四阶 Butterworth 低通在 1 kHz 处衰减不得超过 1 dB。求最小截止频率 $f_c$（$-3$ dB 频率），单位 kHz。）

> [!success] Answer（答案）
> $1.184$ kHz

> [!abstract] 知识点讲解
> 见 11.8 例 9（由通带指标求截止频率）。
>
> - $n$ 阶 Butterworth 低通：$|G|^2=\dfrac{1}{1+\left(f/f_c\right)^{2n}}$。
> - 通带指标给出不等式，解出 $f_c$ 的下界。
> - 这里 $2n=8$。

> [!example] 解答
> 要求
> $$10\log_{10}\left[1+\left(\frac{1}{f_c}\right)^8\right]\le1$$
> （$f$ 的单位取 kHz）。即
> $$\left(\frac{1}{f_c}\right)^8\le10^{0.1}-1=0.2589.$$
> 开八次方：
> $$\frac{1}{f_c}\le0.8446\quad\Longrightarrow\quad f_c\ge\frac{1}{0.8446}=1.184\ \mathrm{kHz}.$$
> 最小截止频率为 $1.184$ kHz。

---

## 61. Question 61（第 61 题）^q61

A Butterworth lowpass filter with cutoff frequency 2 kHz must attenuate a 6 kHz signal by at least 35 dB. Enter the smallest order $n$ that meets this.（Butterworth 低通截止频率为 2 kHz，要求在 6 kHz 处衰减至少 35 dB。求满足条件的最小阶数 $n$。）

> [!success] Answer（答案）
> $n=4$

> [!abstract] 知识点讲解
> 见 11.8 例 8（由衰减指标求阶数）。
>
> - 频率比 $6/2=3$。
> - 衰减量 $=10\log_{10}\left(1+3^{2n}\right)$。
> - 逐个试算 $n$，取刚好满足条件的最小值。

> [!example] 解答
> 频率比：
> $$\frac{f}{f_c}=\frac{6}{2}=3.$$
> 衰减量公式：
> $$A(n)=10\log_{10}\left(1+3^{2n}\right).$$
> 试算：
> $$A(3)=10\log_{10}\left(1+3^6\right)=10\log_{10}730=28.6\ \mathrm{dB},$$
> $$A(4)=10\log_{10}\left(1+3^8\right)=10\log_{10}6562=38.2\ \mathrm{dB}.$$
> $n=3$ 不够，$n=4$ 满足且为最小。所以 $n=4$。

---

## 62. Question 62（第 62 题）^q62

### 4. Modulation (week 11)（调制，第 11 周）

Amplitude modulation and demodulation（调幅与解调）

An antenna's length must be comparable to the wavelength $\lambda=c/f$ of the signal it transmits, with $c=3\times10^8$ m/s. Find the wavelength of a 3 kHz telephone audio signal sent directly as an electromagnetic wave, in km.（天线长度须与所发信号的波长 $\lambda=c/f$ 可比，$c=3\times10^8$ m/s。求 3 kHz 电话音频信号直接作为电磁波发送时的波长，单位 km。）

> [!success] Answer（答案）
> $100$ km

> [!abstract] 知识点讲解
> 见 11.9 例 1（波长与载波）。
>
> - $\lambda=c/f$。
> - 音频频率很低，波长极长，天线无法实现。
> - 这正是需要用高频载波进行调制的原因。

> [!example] 解答
> $$\lambda=\frac{c}{f}=\frac{3\times10^8}{3\times10^3}=10^5\ \mathrm{m}=100\ \mathrm{km}.$$
> 波长太长，天线长度要几十公里，因此基带音频必须先调制到高频载波上。

---

## 63. Question 63（第 63 题）^q63

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
> 见 11.9 例 2（DSB-SC 的频谱）与 9.1 调制的基本概念。
>
> - 对每一项用 $\cos a\cos b=\frac12\left[\cos(a-b)+\cos(a+b)\right]$。
> - 乘积频谱不含载波频率本身。
> - 振幅要乘上积化和差带来的 $\frac12$。

> [!example] 解答
> 第一项：
> $$2\cos1000t\cos10000t=\cos9000t+\cos11000t,$$
> 得到 $9000$ 与 $11\,000$ rad/s，振幅均为 $1$。
>
> 第二项：
> $$\cos2000t\cos10000t=\frac12\cos8000t+\frac12\cos12000t,$$
> 得到 $8000$ 与 $12\,000$ rad/s，振幅均为 $0.5$。
>
> 汇总：$8000(0.5)$，$9000(1)$，$11\,000(1)$，$12\,000(0.5)$。选 (c)。

---

## 64. Question 64（第 64 题）^q64

A speech scrambler multiplies $u(t)$, bandlimited to 15 kHz, by $2\cos(2\pi\cdot15\,000t)$ and passes the product through an ideal lowpass filter with cutoff 15 kHz and gain 1. A component $3\cos(2\pi\cdot4000t)$ of $u(t)$ appears in the scrambled output as（语音置乱器把带宽 15 kHz 的 $u(t)$ 乘以 $2\cos(2\pi\cdot15000t)$，再通过截止 15 kHz、增益 1 的理想低通。$u(t)$ 中的分量 $3\cos(2\pi\cdot4000t)$ 在置乱输出中变成）

(a) $3\cos(2\pi\cdot19\,000t)$（被低通滤掉的 19 kHz 项）
(b) $3\cos(2\pi\cdot4000t)$（原频率，没有发生搬移）
(c) $3\cos(2\pi\cdot11\,000t)$ **✓**（留在通带内的下边带分量）
(d) $1.5\cos(2\pi\cdot11\,000t)$（振幅忘了载波幅度 $2$ 的抵消）

> [!success] Answer（答案）
> (c) $3\cos(2\pi\cdot11\,000t)$

> [!abstract] 知识点讲解
> 见 11.9 例 3（单边带滤波）。
>
> - 积化和差得到 $15\pm4$ kHz 两个分量。
> - 低通滤掉超出 $15$ kHz 的上边带。
> - 载波幅度 $2$ 恰好抵消 $\frac12$，振幅保持 $3$。

> [!example] 解答
> 乘积：
> $$3\cos(2\pi\cdot4000t)\cdot2\cos(2\pi\cdot15000t)
> =3\cos(2\pi\cdot11000t)+3\cos(2\pi\cdot19000t).$$
> 低通保留 $11$ kHz（低于 $15$ kHz），滤掉 $19$ kHz。所以输出分量为
> $$3\cos(2\pi\cdot11\,000t).$$
> 选 (c)。

---

## 65. Question 65（第 65 题）^q65

Frequency division multiplexing（频分复用）

A radio band runs from 3.000 MHz to 3.400 MHz. Each telephone message has bandwidth 3.4 kHz and is sent by DSB-SC, with no guard bands and no overlap allowed. What is the largest number of channels that fit in the band?（某无线电频段从 3.000 MHz 到 3.400 MHz。每路电话带宽 3.4 kHz，用 DSB-SC 发送，不留保护间隔也不允许重叠。最多能容纳多少个信道？）

> [!success] Answer（答案）
> $58$

> [!abstract] 知识点讲解
> 见 11.9 例 4（FDM 信道数）与 9.4 频分复用。
>
> - 每个 DSB-SC 信道占用 $2W$ 带宽。
> - 总带宽除以单信道带宽后向下取整。
> - 不能四舍五入。

> [!example] 解答
> 单信道带宽：
> $$2W=2\times3.4=6.8\ \mathrm{kHz}.$$
> 频段宽度：
> $$400\ \mathrm{kHz}.$$
> 信道数：
> $$\left\lfloor\frac{400}{6.8}\right\rfloor=\left\lfloor58.8\right\rfloor=58.$$
> 第 $59$ 路需要额外 $0.8\times6.8=5.44$ kHz，超出频段，所以最多 $58$ 路。

---

## 66. Question 66（第 66 题）^q66

Four messages, each bandlimited to 3 kHz, are sent by DSB-SC on carriers $f_1<f_2<f_3<f_4$. The FDM spectrum must begin at 100 kHz, with 5 kHz guard bands between adjacent channels and no gaps otherwise. Find $f_4$ in kHz.（四路带宽均为 3 kHz 的消息用 DSB-SC 分别调制到载波 $f_1<f_2<f_3<f_4$。FDM 频谱须从 100 kHz 开始，相邻信道间留 5 kHz 保护间隔，其余不留空隙。求 $f_4$，单位 kHz。）

> [!success] Answer（答案）
> $136.0$ kHz

> [!abstract] 知识点讲解
> 见 11.9 例 5（FDM 载频安排）。
>
> - 每个 DSB-SC 信道宽 $2W=6$ kHz，以载频为中心。
> - 第一路的下边沿在 100 kHz，所以 $f_1=100+W$。
> - 相邻载频间隔为 $2W+$ 保护间隔。

> [!example] 解答
> 第一路载频：
> $$f_1=100+3=103\ \mathrm{kHz}.$$
> 相邻载频间隔：
> $$6+5=11\ \mathrm{kHz}.$$
> 第四路载频：
> $$f_4=103+3\times11=136.0\ \mathrm{kHz}.$$

---

## 67. Question 67（第 67 题）^q67

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
(c) 0 to 35 000 rad/s（误以为搬移后仍保留基带）
(d) 15 000 to 25 000 rad/s（只用 $u_1$ 的频段计算）

> [!success] Answer（答案）
> (a) 5000 到 35 000 rad/s

> [!abstract] 知识点讲解
> 见 11.9 例 6（多层调制）。
>
> - 先求内层信号 $b(t)$ 的频段，再整体搬移。
> - 调制把频段平移到 $\omega_c\pm$ 原频段。
> - 基带部分与已调部分相加，频段取并集。

> [!example] 解答
> $u_1$ 占据 $0$ 到 $5000$ rad/s。
>
> $u_2$ 调制到 $10\,000$ rad/s 两侧：$10\,000\pm5000$，即 $5000$ 到 $15\,000$ rad/s。
>
> 因此 $b(t)$ 的频段为并集：
> $$[0,5000]\cup[5000,15000]=[0,15000].$$
> 再乘 $2\cos20\,000t$，整体搬移到
> $$20\,000\pm15\,000,$$
> 即 $5000$ 到 $35\,000$ rad/s。选 (a)。

---

## 68. Question 68（第 68 题）^q68

Frequency and phase modulation, instantaneous frequency（调频、调相与瞬时频率）

The signal $y(t)=\cos(t^2)$ is a sinusoid with variable frequency, $y(t)=\cos(\omega(t)t)$ with $\omega(t)=t$. Find its instantaneous frequency at $t=5$ s, in rad/s.（信号 $y(t)=\cos(t^2)$ 是变频正弦，写成 $y(t)=\cos(\omega(t)t)$ 时 $\omega(t)=t$。求 $t=5$ s 时的瞬时角频率，单位 rad/s。）

> [!success] Answer（答案）
> $10$ rad/s

> [!abstract] 知识点讲解
> 见 9.5 瞬时频率 与 11.9 例 7（瞬时频率）。
>
> - 瞬时频率是**整个相位**的导数。
> - 不能把 $\omega(t)=t$ 直接当成瞬时频率。
> - $\theta(t)=t^2$，$\omega_i=2t$。

> [!example] 解答
> 相位：
> $$\theta(t)=t^2.$$
> 瞬时角频率：
> $$\omega_i(t)=\frac{d\theta}{dt}=2t.$$
> 代入 $t=5$：
> $$\omega_i(5)=10\ \mathrm{rad/s}.$$
> 注意 $t^2$ 的相位在 $t=5$ 处变化速度是 $10$，而不是 $\omega(t)=5$。

---

## 69. Question 69（第 69 题）^q69

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
> 见 9.6 PM 与 FM 与 11.9 例 8（PM 的频偏）。
>
> - PM 的瞬时频率为 $\omega_c+k\dot u(t)$。
> - 频偏是 $k\dot u$，与消息本身 $u$ 无关。
> - 换算：$\Delta f=\Delta\omega/(2\pi)$。

> [!example] 解答
> 斜坡导数：
> $$\dot u(t)=4000.$$
> 瞬时角频率：
> $$\omega_i=\omega_c+0.5\times4000=\omega_c+2000\ \mathrm{rad/s}.$$
> 换算成赫兹：
> $$\Delta f=\frac{2000}{2\pi}=318.3\ \mathrm{Hz}.$$

---

## 70. Question 70（第 70 题）^q70

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
> 见 9.6 PM 与 FM 与 11.9 例 9（FM 与 PM 的区别）。
>
> - FM 对消息积分：阶跃积分成斜坡，相位连续，频率跳变。
> - PM 直接乘消息：阶跃使相位跳变，导数在 $t>0$ 为零，频率不变。
> - 两者都只改变相位，不改变幅度。

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

## 71. Question 71（第 71 题）^q71

A message $u(t)$ with spectrum zero for $|\omega|>W$ (and no DC component) is sent by FM（某消息 $u(t)$ 的频谱在 $|\omega|>W$ 处为零，且无直流分量，用 FM 发送）：

$$
y(t)=\cos\left(\omega_ct+k\int_{-\infty}^{t}u(\tau)\,d\tau\right),\qquad \omega_c\gg W.
$$

For small but nonzero $k$, the spectrum of $y(t)$ consists of（当 $k$ 很小但不为零时，$y(t)$ 的频谱由什么组成？）

(a) lines at $\pm\omega_c$ plus sidebands in $\omega_c-W<|\omega|<\omega_c+W$, the same band as AM **✓**（$\pm\omega_c$ 处的谱线加上 $\omega_c-W<|\omega|<\omega_c+W$ 内的边带，与 AM 频段相同）
(b) components spread over a band much wider than $2W$ around $\pm\omega_c$（比 $2W$ 宽得多的频带）
(c) lines at $\pm\omega_c$ only（只有 $\pm\omega_c$ 谱线）
(d) the baseband spectrum $|\omega|<W$ plus lines at $\pm\omega_c$（基带频谱加上载波谱线）

> [!success] Answer（答案）
> (a) 载波谱线加与 AM 同带宽的边带

> [!abstract] 知识点讲解
> 见 9.7 窄带 FM 与宽带 FM 与 11.9 例 10（窄带 FM 的频谱）。
>
> - 小 $k$ 时展开 $\cos(\omega_ct+\theta)\approx\cos\omega_ct-\theta\sin\omega_ct$。
> - 第二项是 $\sin\omega_ct$ 被积分消息调幅，频带为 $\omega_c\pm W$。
> - 只有当 $k$ 很大时带宽才会明显超过 $2W$。

> [!example] 解答
> 记
> $$\theta(t)=k\int_{-\infty}^{t}u(\tau)d\tau.$$
> 小 $k$ 时一阶展开：
> $$y(t)\approx\cos\omega_ct-\theta(t)\sin\omega_ct.$$
> 第一项是载波；第二项是中心频率 $\omega_c$、带宽 $W$ 的 AM（下边带反向）。总频谱为
> $$\pm\omega_c\ \text{处的谱线}+\omega_c\pm W\ \text{的边带},$$
> 与 AM 相同。选 (a)。

---

> [!note] Source note（来源说明）
> Some questions are adapted from B. P. Lathi and R. A. Green, *Linear Systems and Signals*, 3rd ed. (chapters 4 and 7), from ELEC3004 Signals, Systems and Control at the University of Queensland (2017), and from S. Boyd, EE102 Introduction to Signals and Systems, Stanford University.（部分题目改编自 B. P. Lathi 和 R. A. Green《线性系统与信号》第三版第 4、7 章，昆士兰大学 ELEC3004《信号、系统与控制》课程（2017 年），以及斯坦福大学 S. Boyd 的 EE102《信号与系统导论》课程。）



