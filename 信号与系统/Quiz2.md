# ELEC2302/9302 Signals and Systems — Quiz 2 practice questions, answers and feedback

ELEC2302/9302《信号与系统》——测验 2 练习题、答案与反馈

**How to use this question bank:** 

don't work through the questions from beginning to end.（本题库使用方法  不要从头到尾按顺序做题。）

Start by doing one question from each group, identify the areas where you are less confident, and work on those first.（先从每个题组中各做一道题，找出掌握不够牢固的部分，再优先练习这些内容。）

The correct option is marked ✓.（正确选项标有 ✓。）

---

## 1. Question 1（第 1 题）｜PDF p. 1 ^q1

### 1. Fourier series (week 4)（傅里叶级数，第 4 周）

Fundamental frequency of a sum of sinusoids（多个正弦分量之和的基波频率）

A signal is given by（给定如下信号：）

$$
u(t)=\cos\left(\frac{2}{3}t+\frac{\pi}{6}\right)+\sin\left(\frac{4}{5}t+\frac{\pi}{4}\right)
$$

Is $u(t)$ periodic, and if so what is its fundamental frequency $\omega_0$?（判断该信号是否具有周期性；如果是，求其基波角频率。）

(a) Periodic, $\omega_0=\frac{1}{15}\ \mathrm{rad/s}$（周期信号，基频为 $\frac{1}{15}\ \mathrm{rad/s}$）
(b) Periodic, $\omega_0=\frac{4}{5}\ \mathrm{rad/s}$ (the larger of the two frequencies)（周期信号，基频为 $\frac{4}{5}\ \mathrm{rad/s}$，即两个频率中较大的那个）
(c) Not periodic, because $\frac{2}{3}$ and $\frac{4}{5}$ are not integers（非周期信号，因为 $\frac{2}{3}$ 和 $\frac{4}{5}$ 都不是整数）
(d) Periodic, $\omega_0=\frac{2}{15}\ \mathrm{rad/s}$ **✓**（周期信号，基频为 $\frac{2}{15}\ \mathrm{rad/s}$）

> [!success] Answer（答案）
> (d) $\omega_0=\frac{2}{15}\ \mathrm{rad/s}$

> [!abstract] 知识点讲解
> 见 1.5 多个正弦叠加的周期与基频。
>
> - **周期条件**：各分量频率之比均为有理数，即 $\omega_i/\omega_j\in\mathbb{Q}$，信号才有公共周期。
> - **基频**：把各频率通分到同一分母，对分子取最大公约数，$\omega_0=\dfrac{\gcd(\text{各分子})}{\text{公共分母}}$。
> - **基波周期**：$T_0=\dfrac{2\pi}{\omega_0}$。

> [!example] 解答
> 写出非零角频率：$\omega_1=\frac{2}{3}$，$\omega_2=\frac{4}{5}$。
>
> 通分。分母最小公倍数为 $15$：
> $$\omega_1=\frac{10}{15},\qquad \omega_2=\frac{12}{15}.$$
>
> 分子取最大公约数：$\gcd(10,12)=2$，所以
> $$\omega_0=\frac{2}{15}\ \mathrm{rad/s}.$$
>
> 求基波周期：
> $$T_0=\frac{2\pi}{\omega_0}=15\pi.$$
>
> 校验频率比：
> $$\frac{2/3}{4/5}=\frac{5}{6}\in\mathbb{Q},$$
> 周期存在；两个分量分别是基频的 $5$ 次与 $6$ 次谐波。
>
> 选 (d)。


---

1 Some questions are adapted from B. P. Lathi and R. A. Green, *Linear Systems and Signals*, 3rd ed. (chapters 2, 4, 6 and 7), from ELEC3004 Signals, Systems and Control at the University of Queensland (2013 and 2017), and from S. Boyd, EE102 Introduction to Signals and Systems, Stanford University.（部分题目改编自 B. P. Lathi 和 R. A. Green《线性系统与信号》第三版第 2、4、6、7 章，昆士兰大学 ELEC3004《信号、系统与控制》课程（2013 年及 2017 年），以及斯坦福大学 S. Boyd 的 EE102《信号与系统导论》课程。）

---

## 2. Question 2（第 2 题）｜PDF p. 1 ^q2

A signal is given by（给定如下信号：）

$$
u(t)=2+7\cos\left(\frac{1}{2}t+\theta_1\right)+3\cos\left(\frac{2}{3}t+\theta_2\right)+5\cos\left(\frac{7}{6}t+\theta_3\right)
$$

Find its fundamental frequency $\omega_0$, in $\mathrm{rad/s}$.（求其基波角频率，单位为 rad/s。）

> [!success] Answer（答案）
> $\omega_0=0.1667\ \mathrm{rad/s}$（即 $\frac{1}{6}$）

> [!abstract] 知识点讲解
> 见 1.5 多个正弦叠加的周期与基频，例 2。
>
> - **常数项**：$\omega=0$，即 $0\cdot\omega_0$，对任何 $\omega_0$ 都成立，不参与求基频。
> - **基频**：$\omega_0=\dfrac{\gcd(\omega_1,\omega_2,\omega_3)}{\text{通分后的公共分母}}$。
> - **基波周期**：$T_0=\dfrac{2\pi}{\omega_0}$。

> [!example] 解答
> 非零角频率：$\frac{1}{2}$、$\frac{2}{3}$、$\frac{7}{6}$。
>
> 通分到分母 $6$：
> $$\frac{1}{2}=\frac{3}{6},\qquad \frac{2}{3}=\frac{4}{6},\qquad \frac{7}{6}=\frac{7}{6}.$$
>
> 分子最大公约数：
> $$\gcd(3,4,7)=1.$$
>
> 基频：
> $$\omega_0=\frac{1}{6}=0.1667\ \mathrm{rad/s}.$$
>
> 周期：
> $$T_0=\frac{2\pi}{1/6}=12\pi.$$
>
> 常数 $2$ 只抬高波形，不影响周期。


---

## 3. Question 3（第 3 题）｜PDF p. 1 ^q3

A signal is given by

$$
u(t)=\cos(3t)+\sin(\sqrt{5}\,t).
$$

Is $u(t)$ periodic?（判断 $u(t)$ 是否为周期信号。）

(a) Yes, periodic with $\omega_0=3\ \mathrm{rad/s}$, the smaller of the two frequencies（是，周期信号，基频为 $3\ \mathrm{rad/s}$，即两个频率中较小的那个）
(b) Yes – any sum of two sinusoids is periodic（是，任意两个正弦信号之和都是周期信号）
(c) Yes, periodic with $\omega_0=\sqrt{5}-3\ \mathrm{rad/s}$（是，基频为 $\sqrt{5}-3\ \mathrm{rad/s}$）
(d) No – a sum of two sinusoids is periodic only if the ratio of their frequencies is rational, and $\frac{3}{\sqrt{5}}$ is irrational **✓**（否，只有两个频率之比为有理数时其和才有周期性，而 $\frac{3}{\sqrt{5}}$ 为无理数）

> [!success] Answer（答案）
> (d) 非周期

> [!abstract] 知识点讲解
> 见 1.5 多个正弦叠加的周期与基频。
>
> - **周期判据**：$u(t)=\cos\omega_1t+\sin\omega_2t$ 为周期信号 $\iff \dfrac{\omega_1}{\omega_2}\in\mathbb{Q}$。
> - **公共周期**：存在 $T$ 使 $\omega_1T=2\pi m$、$\omega_2T=2\pi n$，即 $\dfrac{\omega_1}{\omega_2}=\dfrac mn$（$m,n$ 为整数）。
> - **基频**：若有周期，$\omega_0=\gcd(\omega_1,\omega_2)$；若频率比无理，基频不存在。

> [!example] 解答
> 两频率为 $3$ 与 $\sqrt5$，比值
> $$\frac{3}{\sqrt5}\notin\mathbb{Q}.$$
>
> 反证。若存在公共周期 $T$，须同时满足
> $$3T=2\pi m,\qquad \sqrt5\,T=2\pi n.$$
>
> 两式相除：
> $$\frac{3}{\sqrt5}=\frac{m}{n},$$
> 左端无理、右端有理，矛盾。
>
> 故无公共周期，非周期。
>
> 排除干扰：$\sqrt5-3$ 是拍频且为负；「任意两正弦之和皆周期」错误。选 (d)。


---

## 4. Question 4（第 4 题）｜PDF p. 2 ^q4

A periodic signal $u(t)$ of period $T$ satisfies $u(t-T/2)=-u(t)$. Which of its Fourier coefficients $c_k$ must be zero?（周期为 $T$ 的信号满足半周期平移后变号的条件；它的哪些傅里叶系数 $c_k$ 必须为零？）

$$
u(t-T/2)=-u(t)
$$

(a) Only $c_0$（只有直流系数 $c_0$）
(b) $c_k$ for every even $k$ (including $c_0$) **✓**（所有偶数序号 $k$ 的系数 $c_k$，包括 $c_0$）
(c) $c_k$ for every odd $k$（所有奇数序号 $k$ 的系数 $c_k$）
(d) None – the condition only affects the phase of $c_k$, not which ones vanish（没有任何系数必然为零；该条件只影响系数相位，不影响其是否消失）

> [!success] Answer（答案）
> (b) 所有偶数 $k$（含 $c_0$）的系数为零

> [!abstract] 知识点讲解
> 见 2.6 对称性 与 2.2 复指数形式。
>
> - **复指数系数**：$c_k=\dfrac1T\displaystyle\int_0^T u(t)e^{-jk\omega_0t}dt$。
> - **时移性质**：$u(t-t_0)$ 的系数为 $e^{-jk\omega_0t_0}c_k$；取 $t_0=\dfrac T2$ 得 $e^{-jk\pi}c_k=(-1)^kc_k$。
> - **半波反对称**：$u(t-T/2)=-u(t)\Rightarrow (-1)^kc_k=-c_k\Rightarrow\big[1+(-1)^k\big]c_k=0$，故 $k$ 偶（含 $0$）时 $c_k=0$。

> [!example] 解答
> 系数定义：
> $$c_k=\frac{1}{T}\int_0^T u(t)e^{-jk\omega_0t}\,dt.$$
>
> 拆成两段：
> $$c_k=\frac{1}{T}\left[\int_0^{T/2}+\int_{T/2}^{T}\right]u(t)e^{-jk\omega_0t}dt.$$
>
> 第二段令 $t=\tau+\frac{T}{2}$：
> $$\int_{T/2}^{T}=\int_0^{T/2}u\left(\tau+\frac{T}{2}\right)e^{-jk\omega_0\tau}e^{-jk\pi}d\tau.$$
>
> 用 $u(\tau+\frac{T}{2})=-u(\tau)$ 与 $e^{-jk\pi}=(-1)^k$：
> $$\int_{T/2}^{T}=-(-1)^k\int_0^{T/2}u(\tau)e^{-jk\omega_0\tau}d\tau.$$
>
> 合并：
> $$c_k=\frac{1-(-1)^k}{T}\int_0^{T/2}u(\tau)e^{-jk\omega_0\tau}d\tau.$$
>
> $k$ 偶（含 $0$）时系数因子为零，$c_k=0$；$k$ 奇时因子为 $2/T$。选 (b)。


---

## 5. Question 5（第 5 题）｜PDF p. 2 ^q5

The sawtooth wave $u(t)=2At/T$ for $|t|<T/2$ (period $T$) has which of the following properties?（周期 $T$ 内的锯齿波具有下面哪种性质？）

$$
u(t)=\frac{2At}{T},\qquad |t|<\frac{T}{2}
$$

(a) $b_k=0$ for all $k$; every $c_k$ is purely real（所有正弦系数 $b_k$ 均为零，所有复系数 $c_k$ 都为实数）
(b) $a_k=0$ for all $k$ and $c_0=0$; every $c_k$ is purely imaginary **✓**（所有余弦系数 $a_k$ 均为零且 $c_0$ 为零，所有复系数 $c_k$ 都为纯虚数）
(c) Only the odd-indexed $c_k$ are nonzero, as for a square wave satisfying $u(t-T/2)=-u(t)$（仅奇数序号的 $c_k$ 非零，类似满足半波反对称条件的方波）
(d) $c_0=A$, the peak value of the ramp（$c_0$ 等于斜坡的峰值 $A$）

> [!success] Answer（答案）
> (b) 全部 $a_k=0$、$c_0=0$，所有 $c_k$ 为纯虚数

> [!abstract] 知识点讲解
> 见 2.6 对称性 与 2.3 三角形式与系数换算。
>
> - **复系数定义**：$c_k=\dfrac1T\displaystyle\int_T u(t)e^{-jk\omega_0t}dt$，$c_0$ 为信号平均值。
> - **三角换算**：$a_k=2\operatorname{Re}c_k$，$b_k=-2\operatorname{Im}c_k$，$a_0=c_0$。
> - **奇函数**：$u(-t)=-u(t)\Rightarrow a_0=a_k=0$；由 $c_k=\dfrac{a_k-jb_k}{2}$，$a_k=0$ 时 $c_k=-j\dfrac{b_k}{2}$，为纯虚数。

> [!example] 解答
> 判断奇偶性：
> $$u(-t)=-\frac{2At}{T}=-u(t),$$
> 为奇函数。
> 余弦系数：
> $$a_k=\frac{2}{T}\int_{-T/2}^{T/2}u(t)\cos k\omega_0t\,dt,$$
> 被积函数为奇函数，积分为零，故 $a_k=0$。
>
> 直流为平均值，奇函数在对称区间平均为零：$c_0=0$。
>
> 直接积分：
> $$c_k=\frac{2A}{T^2}\int_{-T/2}^{T/2}t\,e^{-jk\omega_0t}dt.$$
> 实部被积函数 $t\cos k\omega_0t$ 为奇函数，积分为零，只剩
> $$c_k=-j\frac{2A}{T^2}\int_{-T/2}^{T/2}t\sin k\omega_0t\,dt.$$
>
> 分部积分 $\int t\sin at\,dt=\frac{\sin at}{a^2}-\frac{t\cos at}{a}$，取 $a=k\omega_0=\frac{2k\pi}{T}$，边界项 $\sin k\pi=0$，得
> $$c_k=\frac{jA(-1)^k}{k\pi}\quad(k\ne0).$$
>
> 结果为纯虚数。选 (b)。


---

## 6. Question 6（第 6 题）｜PDF p. 3 ^q6

A periodic signal is $u(t)=1$ for $|t|<\pi/2$ and $0$ for $\pi/2<|t|<\pi$, repeated with period $2\pi$: an even square pulse train with 50% duty cycle. Once its DC component is removed, which coefficients remain nonzero?（周期为 $2\pi$ 的偶对称 50% 占空比方波，去除直流后还有哪些非零系数？）

$$
u(t)=\begin{cases}1,&|t|<\pi/2\\0,&\pi/2<|t|<\pi\end{cases},\qquad T=2\pi
$$

(a) Only the odd-indexed $b_k$（只有奇数序号的正弦系数 $b_k$）
(b) All $a_k$, $k\ge1$, decaying as $1/k$（所有 $k\ge1$ 的余弦系数 $a_k$，且按 $1/k$ 衰减）
(c) Only $a_2,a_4,a_6,\dots$（只有 $a_2,a_4,a_6$ 等偶次系数）
(d) Only the odd-indexed $a_k$ – the signal is even, and once the DC offset is removed it satisfies $u(t-T/2)=-u(t)$, which kills every even harmonic **✓**（只有奇数序号的余弦系数 $a_k$；信号为偶函数，去除直流后具有半波反对称性，从而全部偶次谐波消失）


> [!success] Answer（答案）
> (d) 只有奇次 $a_k$ 非零

> [!abstract] 知识点讲解
> 见 2.6 对称性 与 2.9 典型周期波形的傅里叶系数。
>
> - **偶函数**：$u(-t)=u(t)\Rightarrow b_k=0$，只剩余弦项 $a_k\cos k\omega_0t$。
> - **半波反对称**：$\tilde u(t-T/2)=-\tilde u(t)\Rightarrow$ 偶数 $k$ 的 $c_k=0$（含 $c_0$）。
> - **三角与复系数换算**：$a_k=2c_k$（$k\ge1$），$a_0=c_0$。
> - **脉冲串系数**：$c_k=Ad\operatorname{sinc}(kd)$；$d=\dfrac{\tau}{T}=\dfrac12$ 时 $c_k=\dfrac12\operatorname{sinc}\dfrac k2$，$k\ge2$ 的偶数项为零。

> [!example] 解答
> 偶对称 $u(-t)=u(t)$，正弦项为零：$b_k=0$。
>
> 直流：
> $$c_0=\frac{1}{2\pi}\int_{-\pi/2}^{\pi/2}1\,dt=\frac{1}{2}.$$
>
> 去掉直流，$\tilde u=u-\frac12$ 取值 $\pm\frac12$，满足
> $$\tilde u\left(t-\frac{T}{2}\right)=-\tilde u(t).$$
>
> 半波反对称使偶次系数为零，只留奇次。
>
> 计算奇次余弦系数：
> $$a_k=\frac{2}{\pi}\int_0^{\pi/2}\cos kt\,dt=\frac{2}{\pi k}\sin\frac{k\pi}{2},$$
> 对奇数 $k$ 化为
> $$a_k=\frac{2}{\pi}\cdot\frac{(-1)^{(k-1)/2}}{k}.$$
>
> 如 $a_1=\frac{2}{\pi}$、$a_3=-\frac{2}{3\pi}$。选 (d)。

---

## 7. Question 7（第 7 题）｜PDF p. 3 ^q7

An even, bipolar square wave ($+A$ for $|t|<T/4$, $-A$ for $T/4<|t|<T/2$) has amplitude $A=6$. Find $c_5$, to 4 significant figures.（给定幅值 $A=6$ 的偶对称双极性方波，求 $c_5$，保留四位有效数字。）


$$
A=6,\qquad c_5=?
$$

> [!success] Answer（答案）
> $c_5=0.7639$

> [!abstract] 知识点讲解
> 见 2.9 典型周期波形的傅里叶系数。
>
> - **偶对称双极方波**：$c_k=A\operatorname{sinc}\left(\dfrac k2\right)$（$k$ 奇），$c_k=0$（$k$ 偶），$c_0=0$。
> - **sinc 定义**：$\operatorname{sinc}x=\dfrac{\sin\pi x}{\pi x}$，故 $c_k=\dfrac{A\sin(k\pi/2)}{k\pi/2}$。
> - **奇次谐波幅度**：$c_k=\dfrac{2A}{\pi k}(-1)^{(k-1)/2}$（$k$ 奇），按 $\dfrac1k$ 衰减。

> [!example] 解答
> 一个周期内：
> $$u(t)=\begin{cases}+A,&|t|<\frac{T}{4}\\-A,&\frac{T}{4}<|t|<\frac{T}{2}\end{cases}$$
> 正电平占 $|t|<T/4$，长度 $T/2$，正好是整个周期的一半。
>
> 记 $p_{T/2}(t)$ 为「宽 $T/2$、中心在原点、高度为 $1$ 的矩形脉冲」。则
> $$2A\,p_{T/2}(t)=\begin{cases}2A,&|t|<\frac{T}{4}\\0,&\frac{T}{4}<|t|<\frac{T}{2}\end{cases}$$
> 每点都减去 $A$：
> $$2A\,p_{T/2}(t)-A=\begin{cases}+A,&|t|<\frac{T}{4}\\-A,&\frac{T}{4}<|t|<\frac{T}{2}\end{cases}$$
> 恰好等于 $u(t)$，所以
> $$u(t)=2A\,p_{T/2}(t)-A.$$
>
> 高 $1$、宽 $\tau$、周期 $T$ 的矩形脉冲串，系数为
> $$c_k=\frac{\tau}{T}\operatorname{sinc}\left(k\frac{\tau}{T}\right).$$
> 本题 $\tau=\frac{T}{2}$，占空比 $\frac{\tau}{T}=\frac12$，代入：
> $$c_k^{(p)}=\frac12\operatorname{sinc}\left(\frac{k}{2}\right).$$
>
> 时域乘 $2A$，频域系数也乘 $2A$：
> $$2A\cdot c_k^{(p)}=2A\cdot\frac12\operatorname{sinc}\left(\frac{k}{2}\right)=A\operatorname{sinc}\left(\frac{k}{2}\right).$$
>
> 常数 $-A$ 只影响 $c_0$，不影响任何 $k\ne0$ 的系数：
> $$c_0=\underbrace{2A\cdot\frac12}_{A}-\,A=0,$$
> $$c_k=A\operatorname{sinc}\left(\frac{k}{2}\right)\quad(k\ne0).$$
> 这与「双极性信号平均值为零」一致。
>
> 展开 sinc：
> $$A\operatorname{sinc}\left(\frac{k}{2}\right)=A\cdot\frac{\sin\left(\frac{k\pi}{2}\right)}{\frac{k\pi}{2}},$$
> $\sin\frac{k\pi}{2}$ 在 $k$ 为偶数时等于 $0$（$k=2,4,6\dots$ 分别对应 $\sin\pi,\sin2\pi,\dots$），所以只剩奇次谐波。
>
> > $$c_5=A\cdot\frac{\sin\left(\frac{5\pi}{2}\right)}{\frac{5\pi}{2}}=6\cdot\frac{\sin\left(\frac{5\pi}{2}\right)}{\frac{5\pi}{2}}.$$
>
> 把 $5\pi/2$ 拆成 $2\pi+\frac{\pi}{2}$：
> $$\sin\left(2\pi+\frac{\pi}{2}\right)=\sin\frac{\pi}{2}=1.$$
>
> > $$c_5=6\cdot\frac{1}{2.5\pi}=\frac{6}{7.85398}=0.76394.$$
> 也可写成 $\dfrac{12}{5\pi}$。
>
> 取四位有效数字：
> $$c_5=0.7639.$$


---

## 8. Question 8（第 8 题）｜PDF p. 3 ^q8

A full-wave rectified sine $u(t)=A|\sin(\omega_0 t)|$ has amplitude $A=7$. Find $c_3$, to 4 significant figures.（幅值 $A=7$ 的全波整流正弦，求 $c_3$，保留四位有效数字；公式表中记作 $A\lvert\sin(\omega_0t)\rvert$。）


$$
u(t)=7\left|\sin(\omega_0 t)\right|,\qquad c_3=?
$$

> [!success] Answer（答案）
> $c_3=-0.1273$

> [!abstract] 知识点讲解
> 见 2.9 典型周期波形的傅里叶系数 与 1.4 周期信号的常见运算。
>
> - **公式表（全波整流正弦 $A\lvert\sin(\omega_0t)\rvert$）**：$c_k=\dfrac{2A}{\pi(1-4k^2)}$，周期 $T=\dfrac{\pi}{\omega_0}$，只有直流和偶次谐波。
> - **复系数直接用公式表值**，不必再除以 $2$；对应的实余弦系数是 $a_k=2c_k=\dfrac{4A}{\pi(1-4k^2)}$。
> - **直流**：$c_0=\dfrac{2A}{\pi}$。

> [!example] 解答
> 按公式表的记号，输入写成 $u(t)=A\lvert\sin(\omega_0t)\rvert$。整流后周期减半：
> $$T=\frac{\pi}{\omega_0},\qquad \text{基频}=\frac{2\pi}{T}=2\omega_0.$$
>
> 在一个半周期 $0\le t<\frac{\pi}{\omega_0}$ 内 $u=A\sin(\omega_0t)$，代入系数定义（$T$ 为整流后的周期）：
> $$c_k=\frac{\omega_0}{\pi}\int_0^{\pi/\omega_0}A\sin(\omega_0t)e^{-j2k\omega_0t}dt.$$
>
> 换元 $x=\omega_0t$：
> $$c_k=\frac{A}{\pi}\int_0^{\pi}\sin x\,e^{-j2kx}dx.$$
>
> 积分：
> $$\int_0^\pi\sin x\,e^{-j2kx}dx=\frac{1+e^{-j2k\pi}}{1-4k^2}=\frac{2}{1-4k^2}.$$
> 于是
> $$c_k=\frac{2A}{\pi(1-4k^2)},$$
> 与公式表该行一致。代入 $A=7$、$k=3$：
> $$c_3=\frac{14}{\pi(1-36)}=-\frac{2}{5\pi}=-0.12732.$$
>
> 四位有效数字 $-0.1273$。


---

## 9. Question 9（第 9 题）｜PDF p. 3 ^q9

A pulse train $u(t)=A p_\tau(t)$ (period $T$, duty cycle $d=\tau/T=1/3$) has Fourier coefficients $c_k=Ad\operatorname{sinc}(kd)$. For which smallest positive integer $k$ does $c_k=0$?（给定占空比为 $1/3$ 的脉冲列，求使 $c_k$ 首次为零的最小正整数 $k$。）

$$
c_k=Ad\operatorname{sinc}(kd),\qquad d=\frac{1}{3}
$$

(a) $k=2$（$k=2$）
(b) $c_k$ is never zero when $d=1/3$（当占空比为 $1/3$ 时，$c_k$ 永不为零）
(c) $k=3$ **✓**（$k=3$）
(d) $k=1$（$k=1$）

> [!success] Answer（答案）
> (c) $k=3$

> [!abstract] 知识点讲解
> 见 2.9 典型周期波形的傅里叶系数。
>
> - **sinc 定义**：$\operatorname{sinc}x=\dfrac{\sin\pi x}{\pi x}$，零点在 $x=\pm1,\pm2,\dots$。
> - **脉冲串系数**：$c_k=Ad\operatorname{sinc}(kd)$。
> - **零点条件**：$c_k=0\iff kd\in\mathbb{Z}\setminus\{0\}$，首个正整数 $k=\dfrac1d$。

> [!example] 解答
> 零点条件：
> $$\operatorname{sinc}(kd)=0\iff kd\in\{1,2,\dots\}.$$
>
> 最小正整数解：
> $$k=\frac{1}{d}.$$
>
> 代入 $d=\frac13$：$k=3$。
>
> 验证：$\operatorname{sinc}(1)=0$；$k=1,2$ 时 $kd=\frac13,\frac23$，非零。
>
> $k=2$ 属占空比 $1/2$ 的情形。选 (c)。

---

## 10. Question 10（第 10 题）｜PDF p. 4 ^q10

A periodic signal $u(t)$ with period $T$ equals $+8$ for a quarter of each period and $-2$ for the remaining three-quarters. Find $c_0$.（求给定分段常值周期信号的直流系数 $c_0$。）


$$
u(t)=\begin{cases}8,&\text{占周期 }1/4\\-2,&\text{占周期 }3/4\end{cases}
$$

> [!success] Answer（答案）
> $c_0=0.5$

> [!abstract] 知识点讲解
> 见 2.2 复指数形式 与 2.8 Parseval 定理。
>
> - **直流系数**：$c_0=\dfrac1T\displaystyle\int_T u(t)dt$，即一个周期内的平均值。
> - **分段常值**：$c_0=\displaystyle\sum_i u_i\dfrac{T_i}{T}$，按各段时长占比加权。

> [!example] 解答
> 定义：
> $$c_0=\frac1T\int_T u(t)\,dt.$$
>
> 按分段把积分拆开。取一个周期 $0\le t<T$：$0<t<T/4$ 时 $u=8$，$T/4<t<T$ 时 $u=-2$：
> $$\begin{aligned}
> c_0&=\frac1T\left[\int_0^{T/4}8\,dt+\int_{T/4}^{T}(-2)\,dt\right]\\
> &=\frac1T\left[8\cdot\frac{T}{4}+(-2)\cdot\left(T-\frac{T}{4}\right)\right]
> =\frac1T\left[8\cdot\frac{T}{4}+(-2)\cdot\frac{3T}{4}\right]\\
> &=\frac{T}{T}\left[8\cdot\frac14+(-2)\cdot\frac34\right]
> =8\cdot\frac14+(-2)\cdot\frac34.
> \end{aligned}$$
> 化简时分子分母的 $T$ 约掉，所以结果只依赖时间占比、与 $T$ 的具体取值无关。
>
> 计算：
> $$c_0=8\cdot\frac14+(-2)\cdot\frac34=2-1.5=0.5.$$
>
> 与 $T$ 无关。


---

## 11. Question 11（第 11 题）｜PDF p. 4 ^q11

A signal $u(t)$ has period $T=2$ and is defined on one period by $u(t)=1$ for $0<t<1$ and $u(t)=-1$ for $1<t<2$ (repeating). Its complex Fourier coefficient $c_0$ is:（该信号的复傅里叶系数 $c_0$ 为多少？）

$$
T=2,\qquad u(t)=\begin{cases}1,&0<t<1\\-1,&1<t<2\end{cases}
$$

(a) $c_0=-1$（$c_0=-1$）
(b) $c_0=0.5$（$c_0=0.5$）
(c) $c_0=0$ **✓**（$c_0=0$）
(d) $c_0=1$（$c_0=1$）

> [!success] Answer（答案）
> (c) $c_0=0$

> [!abstract] 知识点讲解
> 见 2.2 复指数形式 与 2.3 三角形式与系数换算。
>
> - **直流系数**：$c_0=\dfrac1T\displaystyle\int_0^T u(t)dt$，公式表也记作 $a_0=c_0$。
> - **奇函数**：$u(t)$ 满足 $u(-t)=-u(t)$（一个周期内正负两段等长且反号），公式表给出 $a_0=a_k=0$，故 $c_0=0$。
> - **正负抵消**：$\displaystyle\int_0^T u\,dt=1-1=0$，与对称性结论一致。

> [!example] 解答
> 定义：
> $$c_0=\frac{1}{T}\int_0^T u\,dt,\qquad T=2.$$
>
> 分段：
> $$c_0=\frac12\left[\int_0^1(+1)dt+\int_1^2(-1)dt\right].$$
>
> 两个积分分别为 $1$ 与 $-1$。
>
> 求和：
> $$c_0=\frac12(1-1)=0.$$
>
> 只积前半段会误得 $0.5$。选 (c)。


---

## 12. Question 12（第 12 题）｜PDF p. 4 ^q12

A signal of period $1$ equals $1/\sqrt{d}$ on $0\le t<d$ and $0$ on the rest of each period, where $0<d<1$. For $d=0.01$, find $c_0$.（当 $d=0.01$ 时求 $c_0$。）

$$
T=1,\qquad u(t)=\begin{cases}1/\sqrt{d},&0\le t<d\\0,&d\le t<1\end{cases},\qquad d=0.01
$$

(a) $0.01$
(b) $0.1$ **✓**
(c) $10$
(d) $1$

> [!success] Answer（答案）
> (b) $0.1$

> [!abstract] 知识点讲解
> 见 2.2 复指数形式。
>
> - **直流系数**：$c_0=\dfrac1T\displaystyle\int_T u(t)dt=\dfrac{\text{一个周期的面积}}{T}$。
> - **矩形面积**：$S=\text{高}\times\text{宽}=\dfrac{1}{\sqrt d}\cdot d=\sqrt d$，$T=1$ 时 $c_0=S$。

> [!example] 解答
> 面积：
> $$S=\frac{1}{\sqrt d}\cdot d=\sqrt d.$$
>
> $T=1$：
> $$c_0=\frac{S}{T}=\sqrt d.$$
>
> 代入 $d=0.01$：
> $$c_0=0.1.$$
>
> 选 (b)。

---

## 13. Question 13（第 13 题）｜PDF p. 5 ^q13

In the exponential Fourier series

$$u(t)=\sum_{k=-\infty}^{\infty}c_ke^{jk\omega_0t}$$

of a real signal, the term with index $k=-3$ is best interpreted as:

（实信号的复指数傅里叶级数中，$k=-3$ 项应如何理解？）

(a) The complex conjugate of $c_2$（$c_2$ 的复共轭）
(b) A genuinely negative-frequency oscillation, physically distinct from the $k=+3$ component（一个真实的负频率振荡，在物理上与 $k=+3$ 的分量不同）
(c) One half of the real sinusoidal component at frequency $3\omega_0$, which pairs with the $k=+3$ term to form $2|c_3|\cos(3\omega_0t+\arg c_3)$ **✓**（频率为 $3\omega_0$ 的实正弦分量的一半；它与 $k=+3$ 项配对形成 $2|c_3|\cos(3\omega_0t+\arg c_3)$）
(d) A numerical artefact that can be discarded without changing $u(t)$（一种可删除而不影响信号的数值伪影）

> [!success] Answer（答案）
> (c) 频率 $3\omega_0$ 处实正弦分量的一半

> [!abstract] 知识点讲解
> 见 2.5 双边谱与负频率。
>
> - **共轭对称**：实信号满足 $c_{-k}=\overline{c_k}$。
> - **正负频率合成**：$c_ke^{jk\omega_0t}+c_{-k}e^{-jk\omega_0t}=2|c_k|\cos(k\omega_0t+\angle c_k)$。
> - **单项份额**：$c_ke^{jk\omega_0t}=\dfrac12\cdot2|c_k|\cos\theta+j|c_k|\sin\theta$（$\theta=k\omega_0t+\angle c_k$），故一对 $\pm k$ 项各占实余弦的一半，虚部互相抵消。

> [!example] 解答
> 由「实信号」推出共轭对称。$u(t)$ 为实数，所以 $u(t)=\overline{u(t)}$。对级数整体取共轭：
> $$\overline{u(t)}=\sum_{k=-\infty}^{\infty}\overline{c_k}\,\overline{e^{jk\omega_0t}}=\sum_{k=-\infty}^{\infty}\overline{c_k}\,e^{-jk\omega_0t}.$$
> 换指标，令 $m=-k$（$k$ 取遍所有整数，$m$ 也取遍所有整数）：
> $$\overline{u(t)}=\sum_{m=-\infty}^{\infty}\overline{c_{-m}}\,e^{jm\omega_0t}.$$
> 另一方面 $\overline{u(t)}=u(t)=\sum_m c_m e^{jm\omega_0t}$。两个级数表示同一个信号，同一谐波 $e^{jm\omega_0t}$ 的系数必须相等（复指数基的正交性保证系数唯一），所以
> $$c_m=\overline{c_{-m}}\quad\text{对任意 }m,\qquad\text{即 } c_{-k}=\overline{c_k}.$$
>
> 写出 $k=\pm3$ 两项。$k=3$ 项是 $c_3e^{j3\omega_0t}$；$k=-3$ 项是 $c_{-3}e^{-j3\omega_0t}$，用前面得到的共轭对称关系换成 $c_{-3}=\overline{c_3}$：
> $$c_{-3}e^{-j3\omega_0t}=\overline{c_3}\,e^{-j3\omega_0t}.$$
> 两项相加：
> $$c_3e^{j3\omega_0t}+c_{-3}e^{-j3\omega_0t}=c_3e^{j3\omega_0t}+\overline{c_3}e^{-j3\omega_0t}.$$
>
> 把两项合成实余弦。记 $z=c_3e^{j3\omega_0t}$，则第二项正好是 $z$ 的共轭：
> $$\overline{z}=\overline{c_3}\cdot\overline{e^{j3\omega_0t}}=\overline{c_3}\,e^{-j3\omega_0t}.$$
> 用 $z+\overline{z}=2\operatorname{Re}z$：
> $$\begin{aligned}
> c_3e^{j3\omega_0t}+\overline{c_3}e^{-j3\omega_0t}
> &=z+\overline{z}
> =2\operatorname{Re}\left(c_3e^{j3\omega_0t}\right)\\
> &=2\operatorname{Re}\left(|c_3|e^{j\angle c_3}\cdot e^{j3\omega_0t}\right)
> =2|c_3|\operatorname{Re}\left(e^{j(3\omega_0t+\angle c_3)}\right)\\
> &=2|c_3|\cos\left(3\omega_0t+\angle c_3\right).
> \end{aligned}$$
> 这里把 $c_3$ 写成极坐标形式 $c_3=|c_3|e^{j\angle c_3}$，再用 $\operatorname{Re}\left(e^{j\theta}\right)=\cos\theta$ 合并。合并后的振幅 $2|c_3|$ 是单个复系数模的两倍。
ight)=\cos	heta$ 合并。合并后的振幅 $2|c_3|$ 是单个复系数模的两倍。
>
> 看每一项在这条实余弦里的份额。先回到单项本身，用欧拉公式把它拆成实部与虚部。记 $\theta=3\omega_0t+\angle c_3$，由 $c_3=|c_3|e^{j\angle c_3}$ 得
> $$c_3e^{j3\omega_0t}=|c_3|e^{j\theta}=|c_3|\left(\cos\theta+j\sin\theta\right)=|c_3|\cos\theta+j|c_3|\sin\theta.$$
> 共轭项同理，指数上的符号变成负号：
> $$\overline{c_3}e^{-j3\omega_0t}=|c_3|e^{-j\theta}=|c_3|\left(\cos\theta-j\sin\theta\right)=|c_3|\cos\theta-j|c_3|\sin\theta.$$
> 两式相加，虚部抵消、实部加倍，正好回到上面的 $2|c_3|\cos	heta$。
>
> 为了和上面的合振幅 $2|c_3|$ 对照，再把单项实部 $|c_3|\cos\theta$ 改写成 $\frac12\cdot 2|c_3|\cos\theta$（纯粹是 $|c_3|=\frac12\cdot 2|c_3|$ 的恒等变形），得到
> $$c_3e^{j3\omega_0t}=\frac{1}{2}\cdot 2|c_3|\cos\theta+j|c_3|\sin\theta,$$
> $$\overline{c_3}e^{-j3\omega_0t}=\frac{1}{2}\cdot 2|c_3|\cos\theta-j|c_3|\sin\theta.$$
>
> 只看删掉 $k=-3$ 项的后果。若删掉 $k=-3$ 项，这对 $\pm3\omega_0$ 分量只剩 $c_3e^{j3\omega_0t}$，也就是只留下刚才拆分中的
> $$\frac{1}{2}\cdot 2|c_3|\cos(3\omega_0t+\angle c_3)+j|c_3|\sin(3\omega_0t+\angle c_3).$$
> 它是复指数振荡，不再是实余弦：虚部原本靠 $k=-3$ 抵消，现在暴露出来；实余弦部分也只剩一半，幅度从 $2|c_3|$ 变为 $|c_3|$。所以 $k=-3$ 项不能随意丢。选 (c)。

---

## 14. Question 14（第 14 题）｜PDF p. 5 ^q14

A periodic signal's complex Fourier coefficient is $c_1=2-3j$. Using the convention $\left(a_k=2\operatorname{Re}c_k,\ b_k=-2\operatorname{Im}c_k\right)$, the pair $(a_1,b_1)$ is:（按照给定的余弦、正弦系数约定，求 $(a_1,b_1)$。）

$$
c_1=2-3j,\qquad a_1=2\operatorname{Re}c_1,\quad b_1=-2\operatorname{Im}c_1
$$

(a) $(-6,4)$
(b) $(2,-3)$
(c) $(4,6)$ **✓**
(d) $(4,-6)$

> [!success] Answer（答案）
> (c) $(4,6)$

> [!abstract] 知识点讲解
> 见 2.3 三角形式与系数换算。
>
> - **三角系数**：$a_k=2\operatorname{Re}c_k$，$b_k=-2\operatorname{Im}c_k$，$a_0=c_0$。
> - **反算复系数**：$c_k=\dfrac{a_k-jb_k}{2}$。
> - **负号来源**：$\sin$ 项写成复指数时系数为 $\dfrac1{2j}$，而 $\dfrac1j=-j$，故 $b_k$ 前带负号。

> [!example] 解答
> $c_1=2-3j$，故 $\operatorname{Re}c_1=2$，$\operatorname{Im}c_1=-3$。
>
> $a_1=2(2)=4$。
>
> $b_1=-2(-3)=6$。
>
> 反算校验：$\frac{4-6j}{2}=2-3j$。
>
> 选 (c)。


---

## 15. Question 15（第 15 题）｜PDF p. 5 ^q15

The sine–cosine Fourier series of a periodic signal $u(t)$ contains the term $3\cos(2\omega_0t)+4\sin(2\omega_0t)$ (i.e. $a_2=3$, $b_2=4$). Find $|c_2|$.（求 $|c_2|$。）


$$
3\cos(2\omega_0t)+4\sin(2\omega_0t),\qquad |c_2|=?
$$

> [!success] Answer（答案）
> $|c_2|=2.500$

> [!abstract] 知识点讲解
> 见 2.3 三角形式与系数换算。
>
> - **复系数**：$c_k=\dfrac{a_k-jb_k}{2}$。
> - **模**：$|c_k|=\dfrac12\sqrt{a_k^2+b_k^2}$，即三角形式幅度的一半。

> [!example] 解答
> 取模：
> $$|c_k|=\frac12\left|a_k-jb_k\right|=\frac12\sqrt{a_k^2+b_k^2}.$$
>
> 代入 $a_2=3$、$b_2=4$：
> $$|c_2|=\frac12\sqrt{9+16}=\frac52.$$
>
> 结果 $2.500$。


---

## 16. Question 16（第 16 题）｜PDF p. 5 ^q16

A periodic signal is

$$u(t)=2+6\cos(300t)+8\sin(500t).$$

Which set of Fourier coefficients describes it?（下面哪一组傅里叶系数描述该信号？）

(a) $\omega_0=100\ \mathrm{rad/s}$, $c_0=2$, $c_1=c_{-1}=3$, $c_2=-4j$, $c_{-2}=4j$, all others zero（基频为 $100$，直流系数为 $2$，非零系数位于 $\pm1$、$\pm2$ 次，其余为零）
(b) $\omega_0=100\ \mathrm{rad/s}$, $c_0=2$, $c_3=c_{-3}=3$, $c_5=4j$, $c_{-5}=-4j$, all others zero（基频为 $100$，直流系数为 $2$，非零系数位于 $\pm3$、$\pm5$ 次，但第 5 次虚部符号相反）
(c) $\omega_0=100\ \mathrm{rad/s}$, $c_0=2$, $c_3=c_{-3}=3$, $c_5=-4j$, $c_{-5}=4j$, all others zero **✓**（基频为 $100$，直流系数为 $2$，且 $\pm3$ 次余弦系数为 $3$、第 $\pm5$ 次系数分别为 $-4j$ 与 $4j$，其余为零）
(d) $\omega_0=100\ \mathrm{rad/s}$, $c_0=2$, $c_3=c_{-3}=6$, $c_5=-8j$, $c_{-5}=8j$, all others zero（与前一组相比，把谐波系数幅值错误地加倍）

> [!success] Answer（答案）
> (c)

> [!abstract] 知识点讲解
> 见 1.5 多个正弦叠加的周期与基频 与 2.3 三角形式与系数换算。
>
> - **基频**：$\omega_0=\gcd(\omega_1,\omega_2,\dots)$，谐波序号 $k=\dfrac{\omega}{\omega_0}$。
> - **三角系数**：$u=a_0+\sum_k(a_k\cos k\omega_0t+b_k\sin k\omega_0t)$，余弦幅度给 $a_k$，正弦幅度给 $b_k$，常数项 $a_0=2c_0$。
> - **复系数换算**：$c_k=\dfrac{a_k-jb_k}{2}$，$c_{-k}=\overline{c_k}$。

> [!example] 解答
> $\omega_0=\gcd(300,500)=100\ \mathrm{rad/s}$。
>
> 把信号写成标准的三角级数形式，逐项对照：
> $$u(t)=\underbrace{2}_{\text{常数}}+\underbrace{6}_{a_3}\cos(3\omega_0t)+\underbrace{8}_{b_5}\sin(5\omega_0t).$$
> 所以 $k_1=3$，$k_2=5$；对应系数
> $$a_3=6,\quad b_3=0,\qquad a_5=0,\quad b_5=8,$$
> 其余 $a_k=b_k=0$。
>
> 直流项。标准形式的常数项是 $\frac{a_0}{2}$，与 $2$ 对照得 $a_0=4$；而
> $$c_0=\frac{a_0-jb_0}{2}=\frac{4-j\cdot0}{2}=\frac{4}{2}=2,$$
> 与「$c_0$ 是平均值」一致。
>
> $k=3$。直接代入 $c_k=\frac{a_k-jb_k}{2}$：
> $$c_3=\frac{a_3-jb_3}{2}=\frac{6-j\cdot0}{2}=\frac{6}{2}=3.$$
> 负序号用实信号的共轭对称 $c_{-k}=\overline{c_k}$，等价于 $c_{-k}=\frac{a_k+jb_k}{2}$：
> $$c_{-3}=\overline{c_3}=\frac{a_3+jb_3}{2}=\frac{6+j\cdot0}{2}=\frac{6}{2}=3.$$
> 校验：$2|c_3|=2\cdot3=6$，正好是余弦项的幅度 $a_3=6$。
>
> $k=5$。注意余弦项不存在（$a_5=0$），只有正弦项（$b_5=8$）：
> $$c_5=\frac{a_5-jb_5}{2}=\frac{0-j\cdot8}{2}=\frac{-8j}{2}=-4j,$$
> $$c_{-5}=\overline{c_5}=\frac{a_5+jb_5}{2}=\frac{0+j\cdot8}{2}=\frac{8j}{2}=4j.$$
> 校验：$2|c_5|=2\cdot4=8$，正好是正弦项的幅度 $b_5=8$；$j$ 前的负号来自 $b_k$ 前的 $-j$，写成时域即
> $$c_5e^{j5\omega_0t}+c_{-5}e^{-j5\omega_0t}=-4je^{j5\omega_0t}+4je^{-j5\omega_0t}=8\sin(5\omega_0t).$$
>
> 其余为零。选 (c)。

---

## 17. Question 17（第 17 题）｜PDF p. 6 ^q17

Parseval's theorem for a periodic signal $u(t)$ states that its average power is:（周期信号的帕塞瓦尔定理如何表示平均功率？）

$$
P=\frac{1}{T}\int_0^T|u(t)|^2\,dt
$$

(a) $\displaystyle\int_{-\infty}^{\infty}|c_k|\,d\omega$（对频率积分的系数模长）
(b) $|c_0|^2$ alone（仅直流系数模的平方）
(c) $\displaystyle\sum_{k=-\infty}^{\infty}c_k$（所有傅里叶系数直接求和）
(d) $\displaystyle\sum_{k=-\infty}^{\infty}|c_k|^2$ **✓**（所有正负序号傅里叶系数模的平方之和）

> [!success] Answer（答案）
> (d) $\displaystyle\sum_{k=-\infty}^{\infty}|c_k|^2$

> [!abstract] 知识点讲解
> 见 2.8 Parseval 定理。
>
> - **平均功率**：$P=\dfrac1T\displaystyle\int_0^T|u(t)|^2dt$。
> - **Parseval（周期）**：$P=\displaystyle\sum_{k=-\infty}^{\infty}|c_k|^2$，负频率项同样计入。

> [!example] 解答
> $P=\frac1T\int_T|u|^2dt$。
>
> 代入 $u=\sum_kc_ke^{jk\omega_0t}$。
>
> 交叉项积分为零，只剩 $|c_k|^2$：
> $$P=\sum_{k=-\infty}^{\infty}|c_k|^2.$$
>
> 实信号中第 $k$ 次谐波功率 $2|c_k|^2$，直流功率 $|c_0|^2$。
>
> 对频率积分是能量公式；直接把 $c_k$ 相加得 $u(0)$。选 (d)。


---

## 18. Question 18（第 18 题）｜PDF p. 6 ^q18

An odd, bipolar square wave of amplitude $A=1$ (period $T$, so $|u(t)|=1$ always) has（奇对称双极性方波，幅度 $A=1$，周期为 $T$，因此始终满足 $|u(t)|=1$；它的复系数为）

$$c_k=-\frac{2j}{\pi k}\qquad(k\ \text{odd}),$$

zero otherwise. What percentage of its total average power is carried by the fundamental component alone ($k=\pm1$)? Give your answer to 4 significant figures.（其余情况为零。基波分量（即仅 $k=\pm1$ 两项）占总平均功率的百分之几？答案保留四位有效数字。）


$$
A=1,\qquad c_k=-\frac{2j}{\pi k}\quad(k\text{ 为奇数})
$$

> [!success] Answer（答案）
> 基波占 $81.06\%$

> [!abstract] 知识点讲解
> 见 2.8 Parseval 定理 与 2.9 典型周期波形的傅里叶系数。
>
> - **Parseval**：$P=\sum_k|c_k|^2$；实信号第 $k$ 次谐波（$\pm k$ 一对）功率为 $2|c_k|^2$。
> - **总功率**：$|u|=A$ 时 $P=A^2$；本题 $A=1$，$P=1$。
> - **基波系数**：奇对称方波 $c_{\pm1}=\mp\dfrac{2j}{\pi}$，$|c_1|=\dfrac2\pi$。

> [!example] 解答
> 总功率：
> $$P=\frac1T\int_T1\,dt=1.$$
>
> $|c_1|=\frac{2}{\pi}$。
>
> 基波功率：
> $$P_1=2|c_1|^2=\frac{8}{\pi^2}.$$
>
> 占比 $\frac{8}{\pi^2}=0.81057$。
>
> $81.06\%$。


---

## 19. Question 19（第 19 题）｜PDF p. 6 ^q19

A rectangular pulse train $A p_\tau(t)$ of period $T$ has duty cycle $d=\tau/T=0.25$.（周期为 $T$ 的矩形脉冲串 $A p_\tau(t)$ 占空比为 $d=\tau/T=0.25$。）What fraction of its total average power is carried by the DC term $c_0$ alone?（其总平均功率中，仅由直流项 $c_0$ 承担的比例是多少？）


$$
d=\frac{\tau}{T}=0.25,\qquad \frac{P_{\mathrm{DC}}}{P_{\mathrm{total}}}=?
$$

> [!success] Answer（答案）
> $\dfrac{P_{\mathrm{DC}}}{P_{\mathrm{total}}}=0.25$

> [!abstract] 知识点讲解
> 见 2.8 Parseval 定理 与 2.9 典型周期波形的傅里叶系数。
>
> - **Parseval**：$P=\sum_k|c_k|^2$。
> - **直流系数**：脉冲串 $c_0=Ad$。
> - **总功率**：$P=\dfrac1T\displaystyle\int_T|u|^2dt=A^2d$，直流功率 $P_{\text{DC}}=|c_0|^2=A^2d^2$。

> [!example] 解答
> 写出总平均功率的定义：
> $$P_{\text{total}}=\frac{1}{T}\int_T|u(t)|^2\,dt.$$
>
> 代入波形。一个周期内，$u(t)=A$ 只占长度 $\tau$ 的区间 $|t|<\tau/2$，其余为零；在这些区间上 $|u|^2=A^2$，所以积分只在这个长度 $\tau$ 上非零：
> $$\begin{aligned}
> P_{\text{total}}
> &=\frac{1}{T}\int_{-\tau/2}^{\tau/2}A^2\,dt
> =\frac{A^2}{T}\int_{-\tau/2}^{\tau/2}1\,dt\\
> &=\frac{A^2}{T}\cdot\tau
> =A^2\cdot\frac{\tau}{T}
> =A^2d.
> \end{aligned}$$
> 中间用到矩形区间长度为 $\tau$（从 $-\tau/2$ 到 $\tau/2$），最后一步用 $d=\tau/T$。
>
> 求 $c_0$。由定义，$c_0$ 是信号在一个周期内的平均值：
> $$c_0=\frac{1}{T}\int_T u(t)\,dt.$$
> 同样只在长度 $\tau$ 的区间上 $u=A$：
> $$\begin{aligned}
> c_0
> &=\frac{1}{T}\int_{-\tau/2}^{\tau/2}A\,dt
> =\frac{A}{T}\cdot\tau
> =A\cdot\frac{\tau}{T}
> =Ad.
> \end{aligned}$$
>
> 求直流功率。按 Parseval 定理，周期信号的平均功率等于各次复系数模平方之和：
> $$P_{\text{total}}=\sum_{k=-\infty}^{\infty}|c_k|^2.$$
> 直流项 $k=0$ 单独一项就是 $|c_0|^2$，所以
> $$P_{\text{DC}}=|c_0|^2=(Ad)^2=A^2d^2.$$
> 对比前面算出的总功率，$P_{\text{total}}=A^2d$，两者只在 $d$ 的幂次上不同，这正说明「直流只占一部分」。
>
> 求比值：
> $$\frac{P_{\text{DC}}}{P_{\text{total}}}=\frac{A^2d^2}{A^2d}=d=\frac{\tau}{T}=0.25.$$
> $A^2$ 和 $d$ 分别约掉，结果只剩占空比 $d$，与幅度 $A$ 和周期具体数值都无关。


---

## 20. Question 20（第 20 题）｜PDF p. 7 ^q20

A square wave $u(t)$ has period $T=2\pi$, with $u(t)=+1$ for $0<t<\pi$ and $u(t)=-1$ for $\pi<t<2\pi$.（方波 $u(t)$ 的周期为 $T=2\pi$：$0<t<\pi$ 时 $u(t)=+1$，$\pi<t<2\pi$ 时 $u(t)=-1$。）It is approximated by a single complex sinusoid at the fundamental frequency, $u(t)\approx c\,e^{jt}$, with the complex constant $c$ chosen to minimise $\left\|u-c\,e^{jt}\right\|_P^2$.（用基频处的单个复正弦 $u(t)\approx c\,e^{jt}$ 逼近它，复常数 $c$ 取为使均方周期误差 $\left\|u-c\,e^{jt}\right\|_P^2$ 最小的值。）Find $c$.（求 $c$。）


$$
T=2\pi,\quad u(t)=\begin{cases}1,&0<t<\pi\\-1,&\pi<t<2\pi\end{cases},\quad u\approx c\,e^{jt}
$$

> [!success] Answer（答案）
> $c=-0.6366j$

> [!abstract] 知识点讲解
> 见 2.7 正交投影与最佳逼近。
>
> - **内积**：$\langle u,v\rangle_P=\dfrac1T\displaystyle\int_T u(t)v^*(t)dt$。
> - **最佳投影系数**：$c=\dfrac{\langle u,\phi\rangle_P}{\langle\phi,\phi\rangle_P}$，使 $\|u-c\phi\|_P^2$ 最小。
> - **本题**：$\phi=e^{jt}$，$\langle\phi,\phi\rangle_P=1$，故 $c=\langle u,e^{jt}\rangle_P=c_1$。

> [!example] 解答
> 写出投影：
> $$c=\frac{\langle u,e^{jt}\rangle_P}{\langle e^{jt},e^{jt}\rangle_P}.$$
>
> 分母：
> $$\langle e^{jt},e^{jt}\rangle_P=\frac1{2\pi}\int_0^{2\pi}1\,dt=1.$$
>
> 分子：
> $$c=\frac1{2\pi}\left[\int_0^{\pi}e^{-jt}dt-\int_{\pi}^{2\pi}e^{-jt}dt\right].$$
>
> 用 $\int e^{-jt}dt=je^{-jt}$，第一段：
> $$\int_0^\pi e^{-jt}dt=j\left(e^{-j\pi}-1\right)=j(-1-1)=-2j.$$
>
> 第二段：
> $$\int_\pi^{2\pi}e^{-jt}dt=j\left(e^{-j2\pi}-e^{-j\pi}\right)=j(1+1)=2j.$$
>
> 代入：
> $$c=\frac1{2\pi}\left[(-2j)-(2j)\right]=\frac{-4j}{2\pi}=-\frac{2j}{\pi}=-0.6366j.$$
>
> 校验：方波为奇函数，$a_1=0$；$b_1=\frac{4}{\pi}$，于是 $c_1=\frac{0-j\cdot4/\pi}{2}=-\frac{2j}{\pi}$，一致。


---

## 21. Question 21（第 21 题）｜PDF p. 7 ^q21

A real $T$-periodic signal $u(t)$ is approximated by $c\,\phi(t)$, with the real constant $c$ chosen to minimise $\|u-c\phi\|_P^2$.（实周期信号 $u(t)$（周期 $T$）用 $c\,\phi(t)$ 逼近，实常数 $c$ 取为使 $\|u-c\phi\|_P^2$ 最小的值。）At that optimal $c$, the error signal $e(t)=u(t)-c\phi(t)$ satisfies:（在该最优 $c$ 处，误差信号 $e(t)=u(t)-c\phi(t)$ 满足什么条件？）

$$
\min_c\|u-c\phi\|_P^2,\qquad e=u-c\phi
$$

(a) $e(t)=0$ for every $t$（误差信号在所有时刻都等于零）
(b) $\langle e,\phi\rangle_P=0$: the error is orthogonal to $\phi$ **✓**（误差信号与投影基函数正交）
(c) $\|e\|_P=\|u\|_P$（误差的范数与原信号范数相等）
(d) $\langle e,u\rangle_P=0$: the error is orthogonal to $u$（误差信号与原信号正交）

> [!success] Answer（答案）
> (b) 误差与 $\phi$ 正交：$\langle e,\phi\rangle_P=0$

> [!abstract] 知识点讲解
> 见 2.7 正交投影与最佳逼近。
>
> - **误差范数**：$\|u-c\phi\|_P^2=\|u\|_P^2-2c\langle u,\phi\rangle_P+c^2\|\phi\|_P^2$。
> - **最优系数**：$c=\dfrac{\langle u,\phi\rangle_P}{\langle\phi,\phi\rangle_P}$。
> - **正交投影**：最优时 $\langle e,\phi\rangle_P=\langle u,\phi\rangle_P-c\|\phi\|_P^2=0$。

> [!example] 解答
> 展开误差范数：
> $$\|u-c\phi\|_P^2=\|u\|_P^2-2c\langle u,\phi\rangle_P+c^2\|\phi\|_P^2.$$
> （题设 $u,\phi$ 为实信号，内积为实数，不需要取实部。）
>
> 对 $c$ 求导并令导数为零：
> $$-2\langle u,\phi\rangle_P+2c\|\phi\|_P^2=0.$$
>
> 解出最优系数：
> $$c=\frac{\langle u,\phi\rangle_P}{\|\phi\|_P^2}.$$
>
> 计算残差与 $\phi$ 的内积：
> $$\langle u-c\phi,\phi\rangle_P=\langle u,\phi\rangle_P-c\|\phi\|_P^2.$$
>
> 代入上面解出的 $c$，右端为零，所以
> $$\langle e,\phi\rangle_P=0.$$
>
> 排除其他选项：
> - (c) 由 $\|e\|_P^2=\|u\|_P^2-c^2\|\phi\|_P^2$，只有 $c=0$ 时两个范数才相等；
> - (d) $\langle e,u\rangle_P=\langle e,e+c\phi\rangle_P=\|e\|_P^2$，只有 $e\equiv0$ 时才为零。
>
> 选 (b)。

---

## 22. Question 22（第 22 题）｜PDF p. 7 ^q22

Two real $T$-periodic signals $u(t)$ and $y(t)$ are orthogonal, $\langle u,y\rangle_P=0$.（两个实的 $T$ 周期信号 $u(t)$、$y(t)$ 正交，即 $\langle u,y\rangle_P=0$。）Let $z(t)=u(t)+y(t)$. The average power $P(z)$ equals:（令 $z(t)=u(t)+y(t)$，其平均功率 $P(z)$ 等于多少？）

$$
\langle u,y\rangle_P=0,\qquad z=u+y
$$

(a) $P(u)-P(y)$（两信号功率之差）
(b) $P(u)\,P(y)$（两信号功率之积）
(c) $P(u)+P(y)$ **✓**（两信号功率之和）
(d) $\left(\sqrt{P(u)}+\sqrt{P(y)}\right)^2$（两个信号有效值相加后再平方）


### 2. Fourier transform (week 5)（傅里叶变换，第 5 周）

Existence of the transform, and symmetry for real, even and odd signals（傅里叶变换的存在性以及实信号、偶信号、奇信号的对称性）

> [!success] Answer（答案）
> (c) $P(u)+P(y)$

> [!abstract] 知识点讲解
> 见 2.8 Parseval 定理 与 2.7 正交投影与最佳逼近。
>
> - **范数与功率**：$P(x)=\|x\|_P^2=\langle x,x\rangle_P$。
> - **内积展开**：$\langle u+y,u+y\rangle_P=\|u\|^2+\|y\|^2+2\operatorname{Re}\langle u,y\rangle_P$。
> - **正交**：$\langle u,y\rangle_P=0$ 时交叉项为零，$P(u+y)=P(u)+P(y)$。

> [!example] 解答
> 按定义展开：
> $$P(z)=\langle u+y,u+y\rangle_P.$$
>
> 用内积的双线性：
> $$P(z)=P(u)+P(y)+2\operatorname{Re}\langle u,y\rangle_P.$$
>
> 由正交性 $\langle u,y\rangle_P=0$，交叉项消失：
> $$P(z)=P(u)+P(y).$$
>
> 检查干扰项 (d)：
> $$\left(\sqrt{P(u)}+\sqrt{P(y)}\right)^2=P(u)+P(y)+2\sqrt{P(u)P(y)},$$
> 多出一个正交叉项，只适合同相相加（$y=\alpha u$，$\alpha>0$），不适用于正交信号。
>
> 选 (c)。

---

## 23. Question 23（第 23 题）｜PDF p. 8 ^q23

Which of the following signals does not possess a Fourier transform, not even one containing impulses?（下列信号中，哪一个即使允许冲激项也不存在傅里叶变换？）

$$
\cos(5t),\qquad H(t),\qquad 1,\qquad e^{2t}H(t)
$$

(a) $\cos(5t)$
(b) $H(t)$
(c) $1$
(d) $e^{2t}H(t)$ **✓**（随时间指数增长的信号 $e^{2t}H(t)$）

> [!success] Answer（答案）
> (d) $e^{2t}H(t)$

> [!abstract] 知识点讲解
> 见 3.3 存在性。
>
> - **存在判据（充分）**：$\displaystyle\int_{-\infty}^{\infty}|u(t)|dt<\infty$（绝对可积）$\Rightarrow U(j\omega)$ 存在且连续。
> - **广义变换**：不绝对可积但至多多项式增长时允许含冲激，如 $\cos\omega_0t\leftrightarrow\pi[\delta(\omega-\omega_0)+\delta(\omega+\omega_0)]$、$H(t)\leftrightarrow\dfrac1{j\omega}+\pi\delta(\omega)$、$1\leftrightarrow2\pi\delta(\omega)$。
> - **不存在**：$|u(t)|$ 增长快于任何多项式（如 $e^{2t}$）时，$\displaystyle\int_0^\infty e^{(2-j\omega)t}dt$ 对任何 $\omega$ 发散，连广义变换也没有。
> - **拉普拉斯对照**：$e^{2t}H(t)\leftrightarrow\dfrac1{s-2}$（$\operatorname{Re}s>2$），收敛域不含虚轴，故 $U(j\omega)=U(s)\big|_{s=j\omega}$ 不适用。

> [!example] 解答
> **一、判据是什么。** 判断傅里叶变换是否存在，分三个层次：
>
> 1. **古典意义**：若 $u(t)$ 绝对可积，
>    $$\int_{-\infty}^{\infty}|u(t)|dt<\infty,$$
>    则 $U(j\omega)=\int u(t)e^{-j\omega t}dt$ 对每个 $\omega$ 都收敛，且 $U(j\omega)$ 连续。这是充分条件，不是必要条件。
> 2. **广义意义**：绝对可积不满足时，看增长速度。若 $u(t)$ 至多多项式增长，即存在常数 $C$、$N$ 使
>    $$|u(t)|\le C(1+|t|)^N,$$
>    则 $u$ 是**缓增分布**，存在广义傅里叶变换，频谱中允许出现 $\delta(\omega)$ 及其导数。常数、正弦、阶跃、周期信号都属于这一层。
> 3. **指数增长**：若 $|u(t)|$ 比任何多项式增长得都快（如 $e^{2t}$），$u$ 不是缓增分布，连广义傅里叶变换都不存在。这类信号要用拉普拉斯变换处理。
>
> **二、广义变换是什么。** 对 $1$、$H(t)$、$\cos5t$ 这些信号，积分 $\int u(t)e^{-j\omega t}dt$ 不收敛，不能直接算。广义变换不直接对 $u$ 积分，而是把 $u$ 看成分布（广义函数），用它对“测试函数”的作用来定义：
> $$\langle U,\phi\rangle=\langle u,\hat\phi\rangle,\qquad
> \hat\phi(\omega)=\int_{-\infty}^{\infty}\phi(t)e^{-j\omega t}dt,$$
> 其中 $\phi$ 取速降的测试函数（如 $e^{-t^2}$ 一类），它的变换 $\hat\phi$ 也速降，所以右边积分一定收敛。这样定义出的 $U$ 可以含冲激：例如 $1\leftrightarrow2\pi\delta(\omega)$ 的意思是，对每个测试函数 $\phi$，
> $$\int_{-\infty}^{\infty}1\cdot\hat\phi(\omega)\,d\omega=2\pi\phi(0),$$
> 而右端正是 $2\pi\delta(\omega)$ 与 $\phi$ 配对的结果 $\langle2\pi\delta,\phi\rangle=2\pi\phi(0)$。实际计算中，等价的做法是给信号乘衰减因子再取极限，例如
> $$\cos5t=\lim_{a\to0^+}e^{-a|t|}\cos5t,$$
> 先算右边这个绝对可积信号的普通频谱，再令 $a\to0^+$，极限中出现两根冲激。
>
> **三、逐项判定。**
>
> (a) $\cos5t$：有界（$|\cos5t|\le1$），多项式增长，存在广义变换：
> $$\cos5t\leftrightarrow\pi\left[\delta(\omega-5)+\delta(\omega+5)\right].$$
>
> (b) $H(t)$：有界（取 $0$ 或 $1$），多项式增长，存在广义变换：
> $$H(t)\leftrightarrow\pi\delta(\omega)+\frac{1}{j\omega}.$$
>
> (c) $1$：常数，多项式增长，存在广义变换：
> $$1\leftrightarrow2\pi\delta(\omega).$$
>
> (d) $e^{2t}H(t)$：写出变换积分
> $$\int_0^\infty e^{2t}e^{-j\omega t}dt=\int_0^\infty e^{(2-j\omega)t}dt.$$
> 被积函数的模为
> $$\left|e^{(2-j\omega)t}\right|=e^{2t}\to\infty\quad(t\to\infty),$$
> 与 $\omega$ 无关，所以对任何 $\omega$ 积分都发散。$e^{2t}$ 的增长快于任何多项式，不是缓增分布，连广义变换（含冲激）也不存在。
>
> **四、常见陷阱：不能把 $1/(j\omega-2)$ 当答案。** 形式上积分似乎可以写成 $\frac{1}{j\omega-2}$，但原函数公式只在指数衰减时成立，即要求 $\operatorname{Re}s>2$。用拉普拉斯变换看得很清楚：
> $$e^{2t}H(t)\longleftrightarrow\frac{1}{s-2},\qquad \operatorname{Re}s>2.$$
> 傅里叶变换相当于在 $s=j\omega$ 处取值，而虚轴 $\operatorname{Re}s=0$ 不在收敛域 $\operatorname{Re}s>2$ 内。$\frac{1}{j\omega-2}$ 只是解析延拓，不对应任何收敛积分，也不对应一个分布的傅里叶变换。只有收敛域包含虚轴时（如 $e^{-at}H(t)$，$a>0$，收敛域 $\operatorname{Re}s>-a$），才能用 $G(j\omega)=G(s)\big|_{s=j\omega}$。
>
> 所以选 (d)。

---

## 24. Question 24（第 24 题）｜PDF p. 8 ^q24

$u(t)$ is real and odd, i.e. $u(-t)=-u(t)$.（$u(t)$ 为实奇信号，即 $u(-t)=-u(t)$。）Which statement about $U(j\omega)$ must be true?（关于其傅里叶变换 $U(j\omega)$，哪一项必然成立？）

$$
u(-t)=-u(t),\qquad u(t)\in\mathbb{R}
$$

(a) $U(j\omega)$ is real and an odd function of $\omega$（频谱为实数且关于频率为奇函数）
(b) $U(j\omega)$ is purely imaginary and an odd function of $\omega$ **✓**（频谱为纯虚数且关于频率为奇函数）
(c) $U(j\omega)$ is purely imaginary and an even function of $\omega$（频谱为纯虚数且关于频率为偶函数）
(d) $U(j\omega)$ is real and an even function of $\omega$（频谱为实数且关于频率为偶函数）

> [!success] Answer（答案）
> (b) 纯虚，且关于 $\omega$ 为奇函数

> [!abstract] 知识点讲解
> 见 3.6 对称性。
>
> - **定义展开**：$U(j\omega)=\displaystyle\int_{-\infty}^{\infty}u(t)\left[\cos\omega t-j\sin\omega t\right]dt$。
> - **奇偶积分**：$u$ 奇 × $\cos$ 偶 → 奇函数，积分为零；$u$ 奇 × $\sin$ 奇 → 偶函数，保留。
> - **结果**：$U(j\omega)=-2j\displaystyle\int_0^\infty u(t)\sin\omega t\,dt$，为纯虚数；又 $U(-j\omega)=-U(j\omega)$，为奇函数。

> [!example] 解答
> 展开定义：
> $$U(j\omega)=\int_{-\infty}^{\infty}u(t)\left[\cos\omega t-j\sin\omega t\right]dt.$$
>
> 分析第一项：$u$ 为奇函数、$\cos\omega t$ 为偶函数，乘积为奇函数，在对称区间积分为零：
> $$\int u(t)\cos\omega t\,dt=0.$$
>
> 分析第二项：$u$ 奇、$\sin$ 奇，乘积为偶函数：
> $$U(j\omega)=-j\int u(t)\sin\omega t\,dt=-2j\int_0^\infty u(t)\sin\omega t\,dt.$$
>
> 积分为实数，乘 $-2j$ 后为纯虚数。
>
> 再令 $\omega\to-\omega$：
> $$\sin(-\omega t)=-\sin\omega t\Rightarrow U(-j\omega)=-U(j\omega),$$
> 关于 $\omega$ 为奇函数。
>
> 选 (b)。

---

## 25. Question 25（第 25 题）｜PDF p. 8 ^q25

$u(t)$ is real.（$u(t)$ 为实信号。）Which statement about its spectrum is always true?（关于其频谱，哪一项总是成立？）

$$
u(t)\in\mathbb{R},\qquad U(-j\omega)=U(j\omega)^{*}
$$

(a) Both $|U(j\omega)|$ and $\arg U(j\omega)$ are odd（频谱幅值和相位都是奇函数）
(b) Both $|U(j\omega)|$ and $\arg U(j\omega)$ are even（频谱幅值和相位都是偶函数）
(c) $|U(j\omega)|$ is even and $\arg U(j\omega)$ is odd **✓**（频谱幅值是偶函数，相位是奇函数）
(d) $|U(j\omega)|$ is odd and $\arg U(j\omega)$ is even（频谱幅值是奇函数，相位是偶函数）

> [!success] Answer（答案）
> (c) 幅值为偶函数，相位为奇函数

> [!abstract] 知识点讲解
> 见 3.6 对称性。
>
> - **共轭对称**：实信号 $U(-j\omega)=U^*(j\omega)$。
> - **模**：$|U(-j\omega)|=|U^*(j\omega)|=|U(j\omega)|$，为偶函数。
> - **相位**：$\arg U(-j\omega)=-\arg U(j\omega)$，为奇函数。

> [!example] 解答
> 写出共轭对称：
> $$U(-j\omega)=U^*(j\omega).$$
>
> 两边取模：
> $$\left|U(-j\omega)\right|=\left|U^*(j\omega)\right|=\left|U(j\omega)\right|,$$
> 所以幅值是偶函数。
>
> 两边取相位：
> $$\arg U(-j\omega)=-\arg U(j\omega)\pmod{2\pi},$$
> 所以相位是奇函数。
>
> 排除其他选项：(a) 说模为奇函数，但模恒非负，除非恒为零，不可能是奇函数；(b)(d) 把两个对称性配反。
>
> 选 (c)。

---

## 26. Question 26（第 26 题）｜PDF p. 9 ^q26

$u(t)=3e^{-2t}H(t)-2e^{-5t}H(t)$.（已知该信号。）Find $U(0)$.（求 $U(0)$。）


$$
u(t)=3e^{-2t}H(t)-2e^{-5t}H(t)
$$

> [!success] Answer（答案）
> $U(0)=1.1$

> [!abstract] 知识点讲解
> 见 3.7 面积定理 与 3.4 常用变换对。
>
> - **变换对**：$e^{-at}H(t)\leftrightarrow\dfrac1{a+j\omega}$。
> - **线性**：$au_1+bu_2\leftrightarrow aU_1+bU_2$。
> - **面积定理**：$U(0)=\displaystyle\int_{-\infty}^{\infty}u(t)dt$。

> [!example] 解答
> 逐项求变换：
> $$3e^{-2t}H(t)\leftrightarrow\frac{3}{2+j\omega},\qquad2e^{-5t}H(t)\leftrightarrow\frac{2}{5+j\omega}.$$
>
> 由线性性相减：
> $$U(j\omega)=\frac{3}{2+j\omega}-\frac{2}{5+j\omega}.$$
>
> 令 $\omega=0$：
> $$U(0)=\frac{3}{2}-\frac{2}{5}=1.5-0.4=1.1.$$
>
> 用面积定理解释：$\omega=0$ 相当于求信号的时间积分，
> $$\int_0^\infty\left(3e^{-2t}-2e^{-5t}\right)dt=\frac32-\frac25=1.1,$$
> 与结果一致。

---

## 27. Question 27（第 27 题）｜PDF p. 9 ^q27

$U(j\omega)=4$ for $|\omega|<1$ and $0$ otherwise (i.e. $U(j\omega)=4p_2(\omega)$).（$|\omega|<1$ 时 $U(j\omega)=4$，其余为 $0$，即 $U(j\omega)=4p_2(\omega)$。）Find $u(0)$.（求 $u(0)$。）


$$
U(j\omega)=\begin{cases}4,&|\omega|<1\\0,&\text{otherwise}\end{cases}
$$

> [!success] Answer（答案）
> $u(0)=\frac{4}{\pi}=1.2732$

> [!abstract] 知识点讲解
> 见 3.7 面积定理 与 3.2 定义。
>
> - **逆变换**：$u(t)=\dfrac1{2\pi}\displaystyle\int_{-\infty}^{\infty}U(j\omega)e^{j\omega t}d\omega$；令 $t=0$ 得 $u(0)=\dfrac1{2\pi}\displaystyle\int U(j\omega)d\omega$。
> - **矩形频谱面积**：$U=4$（$|\omega|<1$），面积 $=4\times2=8$。

> [!example] 解答
> 写出逆变换在 $t=0$ 的值：
> $$u(0)=\frac{1}{2\pi}\int_{-\infty}^{\infty}U(j\omega)e^{j\omega\cdot0}d\omega=\frac{1}{2\pi}\int_{-\infty}^{\infty}U(j\omega)d\omega.$$
>
> 计算频谱面积：高度 $4$，宽度从 $-1$ 到 $1$ 共 $2$，
> $$S=4\times2=8.$$
>
> 除以 $2\pi$：
> $$u(0)=\frac{8}{2\pi}=\frac{4}{\pi}=1.2732.$$

---

## 28. Question 28（第 28 题）｜PDF p. 9 ^q28

Evaluate $\displaystyle\int_{-\infty}^{\infty}\operatorname{sinc}(t)\,dt$.（计算 $\operatorname{sinc}(t)$ 在整个时间轴上的积分。）


$$
\int_{-\infty}^{\infty}\operatorname{sinc}(t)\,dt
$$

> [!success] Answer（答案）
> $1$

> [!abstract] 知识点讲解
> 见 3.4 常用变换对 与 3.7 面积定理。
>
> - **sinc 变换对**：$\dfrac{\sin Wt}{\pi t}\leftrightarrow p_{2W}(\omega)$；$\operatorname{sinc}t=\dfrac{\sin\pi t}{\pi t}$ 对应 $W=\pi$。
> - **面积定理**：$\displaystyle\int_{-\infty}^{\infty}u(t)dt=U(0)$。

> [!example] 解答
> 匹配参数：由 $\operatorname{sinc}(t)=\frac{\sin\pi t}{\pi t}$ 得 $W=\pi$。
>
> 写出变换：
> $$\operatorname{sinc}(t)\leftrightarrow p_{2\pi}(\omega).$$
>
> 用面积定理：
> $$\int_{-\infty}^{\infty}\operatorname{sinc}(t)dt=U(0)=p_{2\pi}(0).$$
>
> $\omega=0$ 落在截止频率 $|\omega|<\pi$ 之内，故 $p_{2\pi}(0)=1$。
>
> 结论：积分为 $1$。

---

## 29. Question 29（第 29 题）｜PDF p. 9 ^q29

What is the Fourier transform of $u(t)=\delta(t-5)$?（求延迟冲激 $u(t)=\delta(t-5)$ 的傅里叶变换。）

$$
u(t)=\delta(t-5)
$$

(a) $e^{-j5\omega}$ **✓**
(b) $5e^{-j\omega}$
(c) $\delta(\omega-5)$（频移冲激 $\delta(\omega-5)$）
(d) $e^{j5\omega}$

> [!success] Answer（答案）
> (a) $e^{-j5\omega}$

> [!abstract] 知识点讲解
> 见 3.4 常用变换对 与 3.5 时移性质。
>
> - **时移冲激**：$\delta(t-t_0)\leftrightarrow e^{-j\omega t_0}$。
> - **筛选性质**：$\displaystyle\int_{-\infty}^{\infty}\delta(t-t_0)\varphi(t)dt=\varphi(t_0)$。

> [!example] 解答
> 写定义：
> $$U(j\omega)=\int_{-\infty}^{\infty}\delta(t-5)e^{-j\omega t}dt.$$
>
> 用筛选性质，把被积函数中的 $t$ 取为 $5$：
> $$U(j\omega)=e^{-j5\omega}.$$
>
> 检查易错点：$5$ 应在指数内（$-j5\omega$），不能写成振幅系数 $5e^{-j\omega}$。
>
> 选 (a)。

---

## 30. Question 30（第 30 题）｜PDF p. 9 ^q30

What is the Fourier transform of the constant signal $u(t)=1$, and why is the weight $2\pi$ (not $1$) attached to the impulse?（常数信号 $u(t)=1$ 的傅里叶变换是什么？冲激前的权重为何是 $2\pi$ 而不是 $1$？）

$$
u(t)=1
$$

(a) $U(j\omega)=2\pi\delta(\omega)$, because $u(t)$ is synthesised from $u(t)=\dfrac{1}{2\pi}\int U(j\omega)e^{j\omega t}d\omega$, so a single exponential of amplitude $1$ needs an impulse of area $2\pi$ **✓**（频谱为 $2\pi\delta(\omega)$，因为逆变换包含 $\frac{1}{2\pi}$，需要面积为 $2\pi$ 的冲激才能合成幅值为 $1$ 的常数）
(b) $U(j\omega)=\delta(\omega)$, because $u(t)=1=e^{j0\cdot t}$ needs an impulse of unit strength（频谱为 $\delta(\omega)$，因为幅值为 $1$ 的零频指数只需要单位强度冲激）
(c) $U(j\omega)=\delta(\omega)/2\pi$
(d) $U(j\omega)=2\pi\delta(\omega)$, because $\int_{-\infty}^{\infty}1\,dt=2\pi$（频谱为 $2\pi\delta(\omega)$，理由是全时间积分 $1$ 的结果为 $2\pi$）

> [!success] Answer（答案）
> (a) $U(j\omega)=2\pi\delta(\omega)$

> [!abstract] 知识点讲解
> 见 3.4 常用变换对 与 3.2 定义。
>
> - **变换对**：$1\leftrightarrow2\pi\delta(\omega)$。
> - **逆变换**：$u(t)=\dfrac1{2\pi}\displaystyle\int U(j\omega)e^{j\omega t}d\omega$，冲激权重必须抵消 $\dfrac1{2\pi}$。
> - **周期 FT 校验**：$c_0=1$，$U(j\omega)=2\pi c_0\delta(\omega)=2\pi\delta(\omega)$。

> [!example] 解答
> 把候选答案代回逆变换检验：
> $$u(t)=\frac{1}{2\pi}\int2\pi\delta(\omega)e^{j\omega t}d\omega.$$
>
> 用筛选性质：
> $$u(t)=\frac{1}{2\pi}\cdot2\pi\cdot e^{0}=1.$$
>
> 结果与原信号一致，说明权重 $2\pi$ 正确。
>
> 检查其他选项：权重 $1$ 会得 $\frac{1}{2\pi}$，权重 $\frac{1}{2\pi}$ 会得 $\frac{1}{(2\pi)^2}$。
>
> (d) 的结果正确但理由错误：$\int_{-\infty}^{\infty}1\,dt$ 发散，不等于 $2\pi$。选 (a)。

---

## 31. Question 31（第 31 题）｜PDF p. 10 ^q31

What is the Fourier transform of $u(t)=\operatorname{sinc}(t)$?（求 $u(t)=\operatorname{sinc}(t)$ 的傅里叶变换。）

$$
u(t)=\operatorname{sinc}(t)=\frac{\sin(\pi t)}{\pi t}
$$

(a) $U(j\omega)=\operatorname{sinc}(\omega)$（频谱仍是 $\operatorname{sinc}(\omega)$）
(b) $U(j\omega)=p_{\pi}(\omega)$（频谱为宽度 $\pi$ 的矩形函数）
(c) $U(j\omega)=p_{2\pi}(\omega)$, i.e. $1$ for $|\omega|<\pi$ and $0$ otherwise **✓**（频谱为宽度 $2\pi$ 的矩形函数，在 $|\omega|<\pi$ 时为 $1$，其余为 $0$）
(d) $U(j\omega)=\pi p_{2\pi}(\omega)$（频谱为 $\pi$ 倍的宽度 $2\pi$ 矩形函数）

> [!success] Answer（答案）
> (c) $U(j\omega)=p_{2\pi}(\omega)$

> [!abstract] 知识点讲解
> 见 3.4 常用变换对。
>
> - **sinc 变换对**：$\dfrac{\sin Wt}{\pi t}\leftrightarrow p_{2W}(\omega)$。
> - **本题**：$\operatorname{sinc}t=\dfrac{\sin\pi t}{\pi t}$，$W=\pi$，故 $U(j\omega)=p_{2\pi}(\omega)$。

> [!example] 解答
> 写成标准形式：
> $$\operatorname{sinc}(t)=\frac{\sin\pi t}{\pi t}\Rightarrow W=\pi.$$
>
> 套变换对：
> $$\frac{\sin Wt}{\pi t}\leftrightarrow p_{2W}(\omega)\Rightarrow U(j\omega)=p_{2\pi}(\omega).$$
>
> 展开：
> $$U(j\omega)=\begin{cases}1,&|\omega|<\pi\\0,&|\omega|>\pi\end{cases}$$
>
> 检查高度：归一化 sinc 已把 $\pi$ 除进分母，门高为 $1$，不是 $\pi$。
>
> 选 (c)。

---

## 32. Question 32（第 32 题）｜PDF p. 10 ^q32

$u(t)=p_6(t)$ (a pulse of width $6$, centred at the origin).（$u(t)=p_6(t)$，即宽为 $6$、以原点为中心的矩形脉冲。）What is $U(j\omega)$?（其频谱 $U(j\omega)$ 是什么？）

$$
u(t)=p_6(t)
$$

(a) $6\operatorname{sinc}\left(\dfrac{\omega}{2\pi}\right)$（幅值为 $6$、但自变量缩放不足的 sinc 函数）
(b) $6\operatorname{sinc}\left(\dfrac{3\omega}{\pi}\right)$ **✓**（幅值为 $6$、自变量为 $\frac{3\omega}{\pi}$ 的 sinc 函数）
(c) $\dfrac{1}{6}\operatorname{sinc}\left(\dfrac{3\omega}{\pi}\right)$（幅值为 $1/6$、自变量为 $\frac{3\omega}{\pi}$ 的 sinc 函数）
(d) $6\operatorname{sinc}\left(\dfrac{\omega}{3\pi}\right)$（幅值为 $6$、自变量为 $\frac{\omega}{3\pi}$ 的 sinc 函数）


> [!success] Answer（答案）
> (b) $6\operatorname{sinc}\left(\frac{3\omega}{\pi}\right)$

> [!abstract] 知识点讲解
> 见 3.4 常用变换对。
>
> - **$p_\tau(t)$ 的定义**：宽度为 $\tau$、以原点为中心的矩形脉冲，
>   $$p_\tau(t)=\begin{cases}1,&\lvert t\rvert<\tau/2,\\0,&\lvert t\rvert>\tau/2,\end{cases}$$
>   这里的 $\tau$ 就是**脉宽**（脉冲持续的时间长度），高为 $1$，与 $t=0$ 对称，面积等于 $\tau$。
> - **矩形变换对**：$p_\tau(t)\leftrightarrow\tau\operatorname{sinc}\left(\dfrac{\omega\tau}{2\pi}\right)$，其中 $\tau$ 同时决定频谱零点位置 $\omega=\pm\dfrac{2\pi}{\tau}$。
> - **本题**：$u(t)=p_6(t)$，脉宽 $\tau=6$，代入得 $U(j\omega)=6\operatorname{sinc}\left(\dfrac{3\omega}{\pi}\right)$。

> [!example] 解答
> 代 $\tau=6$：
> $$U(j\omega)=6\operatorname{sinc}\left(\frac{6\omega}{2\pi}\right).$$
>
> 约分：
> $$\frac{6}{2\pi}=\frac{3}{\pi}.$$
>
> 所以
> $$U(j\omega)=6\operatorname{sinc}\left(\frac{3\omega}{\pi}\right).$$
>
> 校验：$U(0)=6$，等于脉冲面积 $1\times6$。选 (b)。

---

## 33. Question 33（第 33 题）｜PDF p. 10 ^q33

$u(t)=p_{0.5}(t)$ (a pulse of width $0.5$) （$u(t)=p_{0.5}(t)$，宽为 $0.5$ 的脉冲） pdf中题目不全没法做

$$
u(t)=p_{0.5}(t)
$$

> [!success] Answer（答案）
> 首个正零点 $\omega=4\pi=12.566\ \mathrm{rad/s}$

> [!abstract] 知识点讲解
> 见 3.4 常用变换对。
>
> - **矩形变换对**：$p_\tau(t)\leftrightarrow\tau\operatorname{sinc}\left(\dfrac{\omega\tau}{2\pi}\right)$，$\tau$ 为**脉宽**（脉冲持续时间）。
> - **零点**：$\operatorname{sinc}x=0\iff x=\pm1,\pm2,\dots$，首个正零点由 $\dfrac{\omega\tau}{2\pi}=1$ 得 $\omega=\dfrac{2\pi}{\tau}$。脉宽越窄，零点越远、频谱越宽。

> [!example] 解答
> 代 $\tau=0.5$：
> $$U(j\omega)=0.5\operatorname{sinc}\left(\frac{0.5\omega}{2\pi}\right)=0.5\operatorname{sinc}\left(\frac{\omega}{4\pi}\right).$$
>
> 令 sinc 的自变量等于 $1$：
> $$\frac{\omega}{4\pi}=1.$$
>
> 解出：
> $$\omega=4\pi=12.566\ \mathrm{rad/s}.$$
>
> 用通用公式校验：
> $$\omega=\frac{2\pi}{\tau}=\frac{2\pi}{0.5}=4\pi,$$
> 一致。

---

## 34. Question 34（第 34 题）｜PDF p. 11 ^q34

$u(t)=p_4(t)$.（已知矩形脉冲 $u(t)=p_4(t)$。）

Evaluate $U(j\pi/4)$.（求 $\omega=\pi/4$ 处的 $U(j\omega)$。）


$$
u(t)=p_4(t),\qquad U(j\pi/4)=?
$$

> [!success] Answer（答案）
> $U(j\pi/4)=\frac{8}{\pi}=2.5465$

> [!abstract] 知识点讲解
> 见 3.4 常用变换对。
>
> - **矩形变换对**：$p_\tau(t)\leftrightarrow\tau\operatorname{sinc}\left(\dfrac{\omega\tau}{2\pi}\right)$。
> - **sinc 特殊值**：$\operatorname{sinc}\dfrac12=\dfrac{\sin(\pi/2)}{\pi/2}=\dfrac2\pi$。

> [!example] 解答
> 写频谱：
> $$U(j\omega)=4\operatorname{sinc}\left(\frac{4\omega}{2\pi}\right)=4\operatorname{sinc}\left(\frac{2\omega}{\pi}\right).$$
>
> 代入 $\omega=\frac{\pi}{4}$：
> $$\frac{2\omega}{\pi}=\frac{2}{\pi}\cdot\frac{\pi}{4}=\frac12.$$
>
> 算 sinc：
> $$\operatorname{sinc}\left(\frac12\right)=\frac{\sin(\pi/2)}{\pi/2}=\frac{1}{\pi/2}=\frac{2}{\pi}.$$
>
> 相乘：
> $$U(j\pi/4)=4\cdot\frac{2}{\pi}=\frac{8}{\pi}=2.5465.$$

---

## 35. Question 35（第 35 题）｜PDF p. 11 ^q35

A rectangular pulse train has amplitude $A=1$ and pulse width $\tau=1\ \mathrm{s}$, and repeats with period $T$:（矩形脉冲串的幅度为 $A=1$、脉宽为 $\tau=1\ \mathrm{s}$，按周期 $T$ 重复：）

$$u_T(t)=\sum_{m\in\mathbb{Z}}p_1(t-mT).$$

Four signals are built this way, differing only in the period: (i) $T=2.5\ \mathrm{s}$ (ii) $T=5\ \mathrm{s}$ (iii) $T=10\ \mathrm{s}$ (iv) the single pulse $p_1(t)$, which is not periodic.（四个信号都由同一脉冲构成，仅周期不同：(i) $T=2.5\ \mathrm{s}$，(ii) $T=5\ \mathrm{s}$，(iii) $T=10\ \mathrm{s}$，(iv) 单个非周期脉冲 $p_1(t)$。）

Each plot below shows the spectrum of one of these signals against $\omega$: the lines $Tc_k$ at $\omega=k\omega_0$ for the three periodic signals, and $U(j\omega)$ for the single pulse.（下面每幅图以 $\omega$ 为横轴画出其中一个信号的频谱：三个周期信号画的是 $\omega=k\omega_0$ 处的谱线 $Tc_k$，单脉冲画的是 $U(j\omega)$。）

The grey curve on each plot is $\operatorname{sinc}(\omega/2\pi)$. Match each of the four signals to its plot.（每幅图中的灰色曲线为 $\operatorname{sinc}(\omega/2\pi)$。请把四个信号与各自的图匹配。）

$$
u_T(t)=\sum_{m\in\mathbb{Z}}p_1(t-mT),\qquad T\in\{2.5,\ 5,\ 10\}
$$

![[Pasted image 20261101091625.png]]

> [!success] Answer（答案）
> (i) C　(ii) A　(iii) D　(iv) B

> [!abstract] 知识点讲解
> 见 2.4 频谱与谱线 与 2.9 典型周期波形的傅里叶系数（2.11 节末尾有「频谱和谱线到底画什么」）。
>
> - **频谱的坐标系**：横坐标是角频率 $\omega$（单位 rad/s）；纵坐标在幅度谱中是谱线（或曲线）的幅度，即 $|c_k|$ 或 $\left|U(j\omega)\right|$，在相位谱中是相角 $\angle c_k$ 或 $\arg U(j\omega)$（单位 rad 或 $^\circ$）。题中画的 $Tc_k$ 谱线，纵坐标就是该归一化傅里叶系数的模 $\lvert Tc_k\rvert$。
> - **周期信号画谱线**：谱线（spectral line，也称线谱分量）只出现在第 $k$ 次谐波 $\omega=k\omega_0$ 处，每根是从横轴竖起的线段，高度为该次谐波的复傅里叶系数之模，相邻谱线间隔 $\omega_0=\dfrac{2\pi}{T}$。
> - **非周期信号画连续曲线**：$U(j\omega)$ 对所有 $\omega$ 有值，画成连续谱（continuous spectrum），没有离散谱线。
> - **脉冲串系数**：$c_k=Ad\operatorname{sinc}(kd)$，本题 $A=1$、$\tau=1$、$d=\dfrac1T$。
> - **为什么画 $Tc_k$ 而不是 $c_k$**：同一个脉冲以不同周期重复时，$c_k=Ad\operatorname{sinc}(kd)$ 随 $T$ 变化（$d=1/T$），谱线高度不同，四幅图无法直接比较。乘 $T$ 后
>   $$Tc_k=T\cdot\frac1T\operatorname{sinc}\left(\frac kT\right)=\operatorname{sinc}\left(\frac kT\right),$$
>   只与 $\dfrac kT=\dfrac{\omega_k}{2\pi}$ 有关，**与周期 $T$ 无关**：同一个脉冲串无论周期取多少，谱线的包络高度都相同，四幅图才能真正比较「谱线密度」这一个差别。
> - **为什么能落在灰色曲线上**：灰色曲线是单脉冲 $p_1(t)$ 的连续频谱 $\operatorname{sinc}\left(\dfrac{\omega}{2\pi}\right)$。由于 $Tc_k=\operatorname{sinc}\left(\dfrac{\omega_k}{2\pi}\right)$，每条谱线的顶端正好是这条连续谱在 $\omega_k$ 处的取值，所以所有谱线顶端都落在灰色包络上；$T\to\infty$ 时谱线间隔趋于 0，离散谱线就连续成这条曲线。
> - **单脉冲**：$p_1(t)\leftrightarrow\operatorname{sinc}\left(\dfrac{\omega}{2\pi}\right)$，就是那条灰色曲线本身，只有曲线、没有竖线。


> [!example] 解答
> 分别求三个周期的谱线间隔：
> $$T=2.5:\ \omega_0=\frac{2\pi}{2.5}=2.513,$$
> $$T=5:\ \omega_0=\frac{2\pi}{5}=1.257,$$
> $$T=10:\ \omega_0=\frac{2\pi}{10}=0.628.$$
>
> 间隔最大（谱线最稀）对应 (i)，即 C。
>
> 间隔居中对应 (ii)，即 A。
>
> 间隔最小（谱线最密）对应 (iii)，即 D。
>
> 单脉冲没有周期，不存在离散谱线，频谱就是包络
> $$U(j\omega)=\operatorname{sinc}\left(\frac{\omega}{2\pi}\right),$$
> 对应 (iv)，即 B。


---

## 36. Question 36（第 36 题）｜PDF p. 12 ^q36

$u(t)=e^{-3t}H(t)$.（已知该信号。）Evaluate $|U(j4)|$.（求 $|U(j4)|$。）


$$
u(t)=e^{-3t}H(t),\qquad |U(j4)|=?
$$

> [!success] Answer（答案）
> $|U(j4)|=0.2$

> [!abstract] 知识点讲解
> 见 3.4 常用变换对。
>
> - **变换对**：$e^{-at}H(t)\leftrightarrow\dfrac1{a+j\omega}$，本题 $a=3$。
> - **取模**：$|U(j\omega)|=\dfrac1{\sqrt{a^2+\omega^2}}$。

> [!example] 解答
> 取 $a=3$：
> $$U(j\omega)=\frac{1}{3+j\omega}.$$
>
> 代入 $\omega=4$：
> $$U(j4)=\frac{1}{3+4j}.$$
>
> 取模：
> $$|U(j4)|=\frac{1}{\sqrt{3^2+4^2}}=\frac{1}{5}=0.2.$$

---

## 37. Question 37（第 37 题）｜PDF p. 12 ^q37

$u(t)=e^{-a|t|}$ has Fourier transform $U(j\omega)=\dfrac{2a}{a^2+\omega^2}$.（$u(t)=e^{-a|t|}$ 的傅里叶变换为 $U(j\omega)=\dfrac{2a}{a^2+\omega^2}$。）

For $a=5000\ \mathrm{s^{-1}}$, find $|U(j\omega)|$ at $\omega=a=5000\ \mathrm{rad/s}$.（取 $a=5000\ \mathrm{s^{-1}}$，求 $\omega=a=5000\ \mathrm{rad/s}$ 处的 $|U(j\omega)|$。）


$$
u(t)=e^{-a|t|},\qquad U(j\omega)=\frac{2a}{a^2+\omega^2},\qquad a=5000,\ \omega=a
$$

> [!success] Answer（答案）
> $|U(ja)|=2.00000\times10^{-4}$

> [!abstract] 知识点讲解
> 见 3.4 常用变换对。
>
> - **变换对**：$e^{-a|t|}\leftrightarrow\dfrac{2a}{a^2+\omega^2}$。
> - **代入 $\omega=a$**：$U(ja)=\dfrac{2a}{a^2+a^2}=\dfrac1a$。

> [!example] 解答
> 代入 $\omega=a$：
> $$|U(ja)|=\frac{2a}{a^2+a^2}=\frac{2a}{2a^2}=\frac{1}{a}.$$
>
> 代入 $a=5000$：
> $$\frac{1}{5000}=2.00000\times10^{-4}.$$
>
> 与零频值比较：
> $$|U(j0)|=\frac{2a}{a^2}=\frac{2}{a}=\frac{2}{5000},$$
> 结果恰为峰值的一半。

---

## 38. Question 38（第 38 题）｜PDF p. 12 ^q38

A system has $G(j\omega)=\dfrac{1}{3+j\omega}$.（某系统的频率响应为 $G(j\omega)=\dfrac{1}{3+j\omega}$。）

Find the phase of $G(j4)$ in degrees.（求 $G(j4)$ 的相位，单位为度。）


$$
G(j\omega)=\frac{1}{3+j\omega},\qquad \arg G(j4)=?
$$

> [!success] Answer（答案）
> $\arg G(j4)=-53.1301^\circ$

> [!abstract] 知识点讲解
> 见 4.2 计算步骤 与 3.4 常用变换对。
>
> - **变换对**：$e^{-at}H(t)\leftrightarrow\dfrac1{a+j\omega}$，$G(j\omega)=\dfrac1{3+j\omega}$。
> - **相位**：$\arg\dfrac1z=-\arg z$，$\arg(a+bj)=\arctan\dfrac ba$。

> [!example] 解答
> 代入 $\omega=4$：
> $$G(j4)=\frac{1}{3+4j}.$$
>
> 取相位：
> $$\arg G(j4)=0-\arg(3+4j).$$
>
> $\arg(3+4j)=\arctan\frac43=53.1301^\circ$。
>
> 故
> $$\arg G(j4)=-53.1301^\circ.$$


---

## 39. Question 39（第 39 题）｜PDF p. 12 ^q39

$u(t)=p_2(t)$. Compare $U(j\omega)$ with the transform of the delayed pulse $u(t-5)$.（$u(t)=p_2(t)$。比较其频谱 $U(j\omega)$ 与延迟脉冲 $u(t-5)$ 的频谱。）

Which statement is correct?（哪一项正确？）

$$
u(t)=p_2(t),\qquad y(t)=u(t-5)
$$

(a) $|U(j\omega)|$ gains an extra term $-5\omega$; the phase is unchanged（幅度谱额外增加 $-5\omega$，相位不变）
(b) Neither the magnitude nor the phase spectrum changes（幅度谱与相位谱均不变）
(c) $|U(j\omega)|$ is unchanged; the phase gains an extra term $-5\omega$ **✓**（幅度谱不变，相位额外增加 $-5\omega$）
(d) The whole spectrum is multiplied by $e^{-j5\omega}$, changing both magnitude and phase（整个频谱乘以 $e^{-j5\omega}$，从而幅值和相位都会改变）

> [!success] Answer（答案）
> (c) 幅值不变，相位增加 $-5\omega$

> [!abstract] 知识点讲解
> 见 3.5 时移性质。
>
> - **时移性质**：$u(t-t_0)\leftrightarrow e^{-j\omega t_0}U(j\omega)$。
> - **模与相位**：$|e^{-j\omega t_0}|=1$，$\arg\left(e^{-j\omega t_0}\right)=-\omega t_0$。

> [!example] 解答
> 写出延迟信号：
> $$y(t)=u(t-5)\leftrightarrow Y(j\omega)=e^{-j5\omega}U(j\omega).$$
>
> 取模：
> $$|Y(j\omega)|=\left|e^{-j5\omega}\right||U(j\omega)|=|U(j\omega)|,$$
> 幅值不变。
>
> 取相位：
> $$\arg Y(j\omega)=\arg U(j\omega)-5\omega,$$
> 增加 $-5\omega$。
>
> 排除 (d)：模因子为 $1$，不影响幅度。选 (c)。


---

## 40. Question 40（第 40 题）｜PDF p. 12 ^q40

$u(t)$ has spectrum $U(j\omega)$. The signal is compressed in time by a factor of $3$, giving $u(3t)$.（$u(t)$ 的频谱为 $U(j\omega)$。把信号在时间上压缩为原来的三分之一，得到 $u(3t)$。）

How do the width and the peak height of the spectrum change?（频谱的宽度与峰值高度如何变化？）

$$
y(t)=u(3t)
$$

(a) The spectrum compresses by a factor of $3$ in $\omega$ and its height scales by $3$（频谱在频率轴上压缩三倍，峰值扩大三倍）
(b) Both the width and the height scale by $3$（频谱宽度和峰值均扩大三倍）
(c) The spectrum expands by a factor of $3$ in $\omega$ and its height scales by $1/3$ **✓**（频谱在频率轴上展宽三倍，峰值变为三分之一）
(d) The spectrum expands by a factor of $3$ in $\omega$ and its height is unchanged（频谱展宽三倍，峰值不变）

> [!success] Answer（答案）
> (c) 频谱展宽三倍，峰值变为 $\frac13$

> [!abstract] 知识点讲解
> 见 3.5 尺度性质。
>
> - **尺度性质**：$u(at)\leftrightarrow\dfrac1{|a|}U\left(j\dfrac{\omega}{a}\right)$，本题 $a=3$。


> [!example] 解答
> 取 $a=3$：
> $$u(3t)\leftrightarrow\frac{1}{3}U\left(j\frac{\omega}{3}\right).$$
>
> 识别展宽：自变量变为 $\omega/3$，原来的频率点 $\omega_0$ 移到 $3\omega_0$，频谱展宽 $3$ 倍。
>
> 识别高度：系数 $\frac13$ 作用在全部取值上，峰值降为原来的 $\frac13$。
> 
>$\omega\to\dfrac{\omega}{3}$ 使频谱展宽 $3$ 倍；系数 $\dfrac13$ 使峰值降为原来的三分之一。
> 
> 选 (c)。

---

## 41. Question 41（第 41 题）｜PDF p. 13 ^q41

Let $y(t)=p_4(2t-4)$.（令 $y(t)=p_4(2t-4)$。）Using the time-shift and time-scaling properties together with the pair $p_\tau(t)\leftrightarrow\tau\operatorname{sinc}\!\left(\dfrac{\omega\tau}{2\pi}\right)$, evaluate $Y(j\omega)$ at $\omega=\pi/2$.（结合时移性质、尺度性质以及变换对 $p_\tau(t)\leftrightarrow\tau\operatorname{sinc}\!\left(\dfrac{\omega\tau}{2\pi}\right)$，求 $\omega=\pi/2$ 处的 $Y(j\omega)$。）


$$
y(t)=p_4(2t-4),\qquad Y(j\pi/2)=?
$$

> [!success] Answer（答案）
> $Y(j\pi/2)=-1.2732$

> [!abstract] 知识点讲解
> 见 3.5 尺度与时移 与 3.4 矩形脉冲。
>
> - **矩形变换对**：$p_\tau(t)\leftrightarrow\tau\operatorname{sinc}\left(\dfrac{\omega\tau}{2\pi}\right)$。
> - **尺度性质**：$u(at)\leftrightarrow\dfrac1{|a|}U\left(j\dfrac{\omega}{a}\right)$。
> - **时移性质**：$u(t-t_0)\leftrightarrow e^{-j\omega t_0}U(j\omega)$。
> - **配方**：$p_4(2t-4)=p_4\big(2(t-2)\big)$，先取 $a=2$，再取 $t_0=2$。

> [!example] 解答
> 配方：
> $$p_4(2t-4)=p_4\left(2(t-2)\right).$$
>
> 对 $p_4(2t)$ 用尺度性质：$a=2$，
> $$p_4(2t)\leftrightarrow\frac{1}{2}\cdot4\operatorname{sinc}\left(\frac{4\cdot\omega/2}{2\pi}\right)=2\operatorname{sinc}\left(\frac{\omega}{\pi}\right).$$
>
> 加入延迟 $t_0=2$：
> $$Y(j\omega)=2\operatorname{sinc}\left(\frac{\omega}{\pi}\right)e^{-j2\omega}.$$
>
> 代入 $\omega=\frac{\pi}{2}$：
> $$\frac{\omega}{\pi}=\frac12,\qquad \operatorname{sinc}\left(\frac12\right)=\frac{2}{\pi}.$$
>
> 求值：
> $$Y(j\pi/2)=2\cdot\frac{2}{\pi}\cdot e^{-j\pi}=-\frac{4}{\pi}=-1.2732.$$


---

## 42. Question 42（第 42 题）｜PDF p. 13 ^q42

The width-$\tau$ triangle $1-|t|/\tau$ $(|t|<\tau)$ has transform $\tau\operatorname{sinc}^2\!\left(\dfrac{\omega\tau}{2\pi}\right)$.（宽为 $\tau$ 的三角形 $1-|t|/\tau$（$|t|<\tau$）的变换为 $\tau\operatorname{sinc}^2\!\left(\dfrac{\omega\tau}{2\pi}\right)$。）

Applying the duality property to this pair, what kind of function of $\omega$ is the Fourier transform of a time-domain signal shaped like $\operatorname{sinc}^2(t/\tau)$?（对这一对应用对偶性质，形如 $\operatorname{sinc}^2(t/\tau)$ 的时域信号，其傅里叶变换在频域是什么形状？）

$$
\left(1-\frac{|t|}{\tau}\right)_{|t|<\tau}\ \longleftrightarrow\ \tau\operatorname{sinc}^2\!\left(\frac{\omega\tau}{2\pi}\right)
$$

(a) A rectangular pulse in $\omega$（频域中的矩形脉冲）
(b) A triangular function of $\omega$ **✓**（频域中的三角函数）
(c) Another $\operatorname{sinc}^2$-shaped function of $\omega$（频域中的另一个 $\operatorname{sinc}^2$ 函数）
(d) A train of impulses in $\omega$（频域中的冲激列）

> [!success] Answer（答案）
> (b) 频域三角形

> [!abstract] 知识点讲解
> 见 3.5 对偶性质 与 3.4 常用变换对。
>
> - **三角形变换对**：$\left(1-\dfrac{|t|}{\tau}\right)_{\lvert t\rvert<\tau}\leftrightarrow\tau\operatorname{sinc}^2\left(\dfrac{\omega\tau}{2\pi}\right)$。
> - **对偶性质**：$U(jt)\leftrightarrow2\pi u(-\omega)$。
> - **对偶后右端**：$2\pi\Lambda(-\omega/\tau)=2\pi\Lambda(\omega/\tau)$（$\Lambda$ 为偶函数），频域仍为三角形。

> [!example] 解答
> 已知：
> $$\Lambda(t/\tau)\leftrightarrow\tau\operatorname{sinc}^2\left(\frac{\omega\tau}{2\pi}\right).$$
>
> 把右端当作时域函数，左端当作频谱，用对偶：
> $$\tau\operatorname{sinc}^2\left(\frac{t\tau}{2\pi}\right)\leftrightarrow2\pi\Lambda(-\omega/\tau).$$
>
> 变量代换后，左端为 $\operatorname{sinc}^2(t/\tau)$ 形状，右端为三角形 $\Lambda(\omega)$ 形状。
>
> 因 $\Lambda$ 为偶函数，$\Lambda(-\omega/\tau)=\Lambda(\omega/\tau)$，结果仍是三角形。
>
> 选 (b)。


---

## 43. Question 43（第 43 题）｜PDF p. 13 ^q43

What is the Fourier transform of $u(t)=\dfrac{2a}{t^2+a^2}$, where $a>0$?（其中 $a>0$。求 $u(t)=\dfrac{2a}{t^2+a^2}$ 的傅里叶变换。）

$$
u(t)=\frac{2a}{t^2+a^2},\qquad a>0
$$

(a) $2\pi e^{-a|\omega|}$ **✓**
(b) $e^{-a|\omega|}$
(c) $\dfrac{2a}{a^2+\omega^2}$
(d) $2\pi e^{-a\omega}$ (for all $\omega$)（对于全部频率取 $2\pi e^{-a\omega}$，没有绝对值）

> [!success] Answer（答案）
> (a) $2\pi e^{-a|\omega|}$

> [!abstract] 知识点讲解
> 见 3.5 对偶性质 与 3.4 常用变换对。
>
> - **变换对**：$e^{-a|t|}\leftrightarrow\dfrac{2a}{a^2+\omega^2}$。
> - **对偶性质**：$U(jt)\leftrightarrow2\pi u(-\omega)$。
> - **代入**：$\dfrac{2a}{a^2+t^2}\leftrightarrow2\pi e^{-a|-\omega|}=2\pi e^{-a|\omega|}$。

> [!example] 解答
> 从已知对开始：
> $$e^{-a|t|}\leftrightarrow\frac{2a}{a^2+\omega^2}.$$
>
> 应用对偶性质， $U(jt)\leftrightarrow2\pi u(-\omega)$，其中 $U(j\omega)=\frac{2a}{a^2+\omega^2}$：
> $$\frac{2a}{a^2+t^2}\leftrightarrow2\pi e^{-a|-\omega|}=2\pi e^{-a|\omega|}.$$
>
> 选 (a)。


---

## 44. Question 44（第 44 题）｜PDF p. 14 ^q44

Given that $u(t)\leftrightarrow U(j\omega)$, which of the following correctly states the duality property of the Fourier transform?（已知 $u(t)\leftrightarrow U(j\omega)$，下列哪一项正确表述了傅里叶变换的对偶性质？）

(a) $U(jt)\leftrightarrow 2\pi u(\omega)$（对偶变换结果为 $2\pi u(\omega)$）
(b) $U(jt)\leftrightarrow 2\pi u(-\omega)$ **✓**（对偶变换结果为 $2\pi u(-\omega)$）
(c) $U(jt)\leftrightarrow u(-\omega)$（对偶变换结果为 $u(-\omega)$，缺少 $2\pi$）
(d) $U(-jt)\leftrightarrow 2\pi u(-\omega)$（对 $U(-jt)$ 作变换的结果错误地写为 $2\pi u(-\omega)$）

> [!success] Answer（答案）
> (b) $U(jt)\leftrightarrow2\pi u(-\omega)$

> [!abstract] 知识点讲解
> 见 3.5 对偶性质。
>
> - **对偶性质**：$u(t)\leftrightarrow U(j\omega)\ \Rightarrow\ U(jt)\leftrightarrow2\pi u(-\omega)$。
> - **$2\pi$ 来源**：逆变换中的 $\dfrac1{2\pi}$，对偶后移到正变换一侧。
> - **负号**：右端是 $u(-\omega)$，频率反转不可省略。


---

## 45. Question 45（第 45 题）｜PDF p. 14 ^q45

Which Fourier-transform property converts convolution in time into a product in frequency?（什么性质把时域卷积转换为频域乘积？）

$$
(h*u)(t)
$$

(a) The differentiation property: $\dfrac{d}{dt}u(t)\leftrightarrow j\omega U(j\omega)$（微分性质：时域求导相当于频域乘以 $j\omega$）
(b) The convolution property: $h(t)*u(t)\leftrightarrow G(j\omega)U(j\omega)$ **✓**（卷积性质：时域卷积变为频域乘积）
(c) The duality property: $U(jt)\leftrightarrow 2\pi u(-\omega)$（对偶性质：交换时域与频域并进行翻转）
(d) The multiplication property: $u_1(t)u_2(t)\leftrightarrow\dfrac{1}{2\pi}(U_1*U_2)(j\omega)$（相乘性质：时域乘积变为频域中带 $\frac{1}{2\pi}$ 系数的卷积）

> [!success] Answer（答案）
> (b) 卷积性质

> [!abstract] 知识点讲解
> 见 3.5 各条性质。四个选项对应四条不同性质：
>
> - **微分**：$\dfrac{d}{dt}u(t)\longleftrightarrow j\omega U(j\omega)$（时域求导 = 频域乘 $j\omega$）
> - **卷积**：$(u_1*u_2)(t)\longleftrightarrow U_1(j\omega)U_2(j\omega)$（时域卷积 = 频域乘积）✓
> - **对偶**：$U(jt)\longleftrightarrow2\pi u(-\omega)$（时频互换，右端取负号并乘 $2\pi$）
> - **相乘**：$u_1(t)u_2(t)\longleftrightarrow\dfrac{1}{2\pi}(U_1*U_2)(j\omega)$（时域相乘 = 频域卷积除以 $2\pi$）
>
> 题干问的是「时域卷积 → 频域乘积」，只有卷积性质符合。



---

## 46. Question 46（第 46 题）｜PDF p. 14 ^q46

Which property converts a product of two time signals into a (scaled) convolution of their transforms?（什么性质把两个时域信号的乘积转换为变换的带系数卷积？）

$$
u_1(t)u_2(t)
$$

(a) The convolution property: $h(t)*u(t)\leftrightarrow G(j\omega)U(j\omega)$（卷积性质：时域卷积转成频域乘积）
(b) The integration property: $\displaystyle\int_{-\infty}^{t}u(\varsigma)\,d\varsigma\leftrightarrow\frac{U(j\omega)}{j\omega}+\pi U(0)\delta(\omega)$（积分性质：时域累积积分对应频域除以 $j\omega$ 并加入冲激项）
(c) The multiplication property: $u_1(t)u_2(t)\leftrightarrow\dfrac{1}{2\pi}(U_1*U_2)(j\omega)$ **✓**（相乘性质：时域两信号相乘对应频域卷积再除以 $2\pi$）
(d) The scaling property: $u(at)\leftrightarrow\dfrac{1}{|a|}U(j\omega/a)$（尺度变换性质：时域伸缩对应频域反向伸缩）

> [!success] Answer（答案）
> (c) 相乘性质

> [!abstract] 知识点讲解
> 见 3.5 各条性质。四个选项对应四条不同性质：
>
> - **卷积**：$(u_1*u_2)(t)\longleftrightarrow U_1(j\omega)U_2(j\omega)$（时域卷积 = 频域乘积）
> - **积分**：$\displaystyle\int_{-\infty}^{t}u(\varsigma)d\varsigma\longleftrightarrow\frac{U(j\omega)}{j\omega}+\pi U(0)\delta(\omega)$（时域积分 = 频域除以 $j\omega$，再加直流冲激项）
> - **相乘**：$u_1(t)u_2(t)\longleftrightarrow\dfrac{1}{2\pi}(U_1*U_2)(j\omega)$（时域相乘 = 频域卷积除以 $2\pi$）✓
> - **尺度**：$u(at)\longleftrightarrow\dfrac{1}{|a|}U\left(j\dfrac{\omega}{a}\right)$（时域压缩 = 频谱展宽并降幅，反之亦然）
>
> 题干问的是「时域乘积 → 频域卷积」，只有相乘性质符合；它与卷积性质互为对偶，系数 $\frac{1}{2\pi}$ 来自逆变换。



---

## 47. Question 47（第 47 题）｜PDF p. 15 ^q47

What is the Fourier transform of $\dfrac{d}{dt}\cos(\omega_0t)$?（求 $\cos(\omega_0t)$ 的时间导数的傅里叶变换。）

$$
\frac{d}{dt}\cos(\omega_0t)
$$

(a) $j\omega_0\pi\left[\delta(\omega-\omega_0)+\delta(\omega+\omega_0)\right]$（两个冲激均取同号的虚系数）
(b) $j\pi\omega_0\left[\delta(\omega-\omega_0)-\delta(\omega+\omega_0)\right]$ **✓**（两个冲激取相反符号的虚系数，且包含 $\omega_0$ 因子）
(c) $-j\pi\left[\delta(\omega-\omega_0)-\delta(\omega+\omega_0)\right]$（冲激符号形式错误并且缺少 $\omega_0$ 因子）
(d) $\pi\left[\delta(\omega-\omega_0)+\delta(\omega+\omega_0)\right]$（原余弦信号本身的频谱，没有体现微分）

> [!success] Answer（答案）
> (b) $j\pi\omega_0\left[\delta(\omega-\omega_0)-\delta(\omega+\omega_0)\right]$

> [!abstract] 知识点讲解
> 见 3.5 微分性质 与 3.4 常用变换对。
>
> - **微分性质**：$\dfrac{d}{dt}u(t)\longleftrightarrow j\omega U(j\omega)$，即求导一次乘 $j\omega$ 一次。
> - **常用变换对**（3.4 表）：$\cos\omega_0t\leftrightarrow\pi\left[\delta(\omega-\omega_0)+\delta(\omega+\omega_0)\right]$。
> - **冲激的筛选性质（乘冲激取值）**：对任意在 $\omega_0$ 处连续的函数 $f$，
>   $$\int_{-\infty}^{\infty}f(\omega)\,\delta(\omega-\omega_0)\,d\omega=f(\omega_0)
>   \quad\Longleftrightarrow\quad
>   f(\omega)\,\delta(\omega-\omega_0)=f(\omega_0)\,\delta(\omega-\omega_0).$$
>   直观理解：$\delta(\omega-\omega_0)$ 只在 $\omega=\omega_0$ 这一点非零，乘在它前面的 $f(\omega)$ 只在这一点被「取值」，其余地方的 $f(\omega)$ 都乘了零、不起作用。


> [!example] 解答
> 由 3.4 表，
> $$X(j\omega)=\mathcal{F}\{\cos\omega_0t\}=\pi\left[\delta(\omega-\omega_0)+\delta(\omega+\omega_0)\right].$$
>
> 用微分性质，乘以 $j\omega$：
> $$\begin{aligned}
> \mathcal{F}\left\{\frac{d}{dt}\cos\omega_0t\right\}
> &=j\omega X(j\omega)\\
> &=j\pi\left[\omega\,\delta(\omega-\omega_0)+\omega\,\delta(\omega+\omega_0)\right]\\
> &=j\pi\left[\omega_0\,\delta(\omega-\omega_0)-\omega_0\,\delta(\omega+\omega_0)\right]\\
> &=j\pi\omega_0\left[\delta(\omega-\omega_0)-\delta(\omega+\omega_0)\right].
> \end{aligned}$$
>
> 第二行到第三行，用的是**冲激的筛选性质**：$\delta(\omega-\omega_0)$ 只在 $\omega=\omega_0$ 处非零，前面的因子 $\omega$ 在该点取 $\omega_0$，即 $\omega\delta(\omega-\omega_0)=\omega_0\delta(\omega-\omega_0)$；后一根冲激在 $\omega=-\omega_0$，取 $-\omega_0$，所以两处符号相反。
>
> 选 (b)。也可先求导再查表：$\frac{d}{dt}\cos\omega_0t=-\omega_0\sin\omega_0t$，而 $\sin\omega_0t\leftrightarrow\frac{\pi}{j}[\delta(\omega-\omega_0)-\delta(\omega+\omega_0)]$，乘 $-\omega_0$ 得同一结果。

---

## 48. Question 48（第 48 题）｜PDF p. 15 ^q48

What is the Fourier transform of $\dfrac{d}{dt}\left[H(t)e^{-3t}\right]$?（求 $H(t)e^{-3t}$ 的导数的傅里叶变换。）

$$
\frac{d}{dt}\left[H(t)e^{-3t}\right]
$$

(a) $-\dfrac{3}{3+j\omega}$（只保留对指数项求导所得的分量，忽略阶跃处的冲激）
(b) $1$（只保留阶跃函数求导的冲激项）
(c) $\dfrac{j\omega}{(3+j\omega)^2}$（分母平方的频域表达式）
(d) $\dfrac{j\omega}{3+j\omega}$ **✓**（正确的微分频谱 $\frac{j\omega}{3+j\omega}$）

> [!success] Answer（答案）
> (d) $\frac{j\omega}{3+j\omega}$

> [!abstract] 知识点讲解
> 见 3.5 微分性质 与 3.4 常用变换对。
>
> - **微分性质**：$\dfrac{d}{dt}u(t)\longleftrightarrow j\omega U(j\omega)$。
> - **变换对**：$e^{-3t}H(t)\leftrightarrow\dfrac1{3+j\omega}$，$\delta(t)\leftrightarrow1$。
> - **直接求导校验**：$\dfrac{d}{dt}\left[e^{-3t}H(t)\right]=\delta(t)-3e^{-3t}H(t)\longleftrightarrow1-\dfrac3{3+j\omega}$。

> [!example] 解答
> 已知 $H(t)e^{-3t}\leftrightarrow\frac{1}{3+j\omega}$。
>
> 用微分性质：
> $$\frac{d}{dt}\left[H(t)e^{-3t}\right]\leftrightarrow j\omega\cdot\frac{1}{3+j\omega}.$$
>
> 化简：
> $$\frac{j\omega}{3+j\omega}.$$
>
> 用直接求导校验：
> $$\frac{d}{dt}\left[H(t)e^{-3t}\right]=\delta(t)-3e^{-3t}H(t).$$
>
> 逐项变换：
> $$1-\frac{3}{3+j\omega}=\frac{3+j\omega-3}{3+j\omega}=\frac{j\omega}{3+j\omega},$$
> 一致。选 (d)。

---

## 49. Question 49（第 49 题）｜PDF p. 15 ^q49

A signal $u(t)$ has Fourier transform $U(j\omega)$, and it is known that $U(j5)=2-3j$.（信号 $u(t)$ 的傅里叶变换为 $U(j\omega)$，已知 $U(j5)=2-3j$。）Let $y(t)=\dfrac{du}{dt}$. Evaluate $Y(j5)$.（令 $y(t)=\dfrac{du}{dt}$，求 $Y(j5)$。）


$$
U(j5)=2-3j,\qquad y(t)=\frac{du}{dt}
$$

> [!success] Answer（答案）
> $Y(j5)=15+10j$

> [!abstract] 知识点讲解
> 见 3.5 微分性质。
>
> - **微分性质**：$y=\dfrac{du}{dt}\Rightarrow Y(j\omega)=j\omega U(j\omega)$。
> - **复数乘法**：$j^2=-1$。

> [!example] 解答
> 写出关系：
> $$Y(j\omega)=j\omega U(j\omega).$$
>
> 代入 $\omega=5$：
> $$Y(j5)=j5\cdot U(j5).$$
>
> 代入 $U(j5)=2-3j$：
> $$Y(j5)=5j(2-3j)=10j-15j^2.$$
>
> 用 $j^2=-1$：
> $$10j+15=15+10j.$$


---

## 50. Question 50（第 50 题）｜PDF p. 16 ^q50

$u(t)$ is periodic with period $T$, fundamental frequency $\omega_0=2\pi/T$, and Fourier series coefficients $c_k$.（$u(t)$ 为周期信号，周期 $T$，基频 $\omega_0=2\pi/T$，傅里叶级数系数为 $c_k$。）What does $U(j\omega)$ look like?（其傅里叶变换 $U(j\omega)$ 在频域是什么形式？）

$$
u(t)=\sum_{k=-\infty}^{\infty}c_ke^{jk\omega_0t}
$$

(a) $\displaystyle U(j\omega)=2\pi\sum_{k=-\infty}^{\infty}c_k\delta(\omega-k\omega_0)$ **✓**（每个谐波位置有权重为 $2\pi c_k$ 的冲激）
(b) $\displaystyle U(j\omega)=\frac{1}{T}\sum_{k=-\infty}^{\infty}\delta(\omega-k\omega_0)$（所有谐波冲激具有相同的权重 $1/T$）
(c) $\displaystyle U(j\omega)=\sum_{k=-\infty}^{\infty}c_ke^{jk\omega_0t}$（这是时域傅里叶级数表达式，而非频域表达式）
(d) $\displaystyle U(j\omega)=\sum_{k=-\infty}^{\infty}c_k\delta(\omega-k\omega_0)$（脉冲位置和 $c_k$ 正确，但缺少 $2\pi$ 因子）

> [!success] Answer（答案）
> (a) $2\pi\displaystyle\sum_kc_k\delta(\omega-k\omega_0)$

> [!abstract] 知识点讲解
> 见 2.11 周期信号的傅里叶变换 与 3.8 周期信号的傅里叶变换。
>
> - **复指数变换对**：$e^{jk\omega_0t}\leftrightarrow2\pi\delta(\omega-k\omega_0)$。
> - **线性**：$\displaystyle\sum_kc_ke^{jk\omega_0t}\leftrightarrow2\pi\sum_kc_k\delta(\omega-k\omega_0)$。
> - **周期信号的 FT**：冲激位于 $\omega=k\omega_0$，权重为 $2\pi c_k$。

> [!example] 解答
> 写出傅里叶级数：
> $$u(t)=\sum_kc_ke^{jk\omega_0t}.$$
>
> 由线性性逐项变换：
> $$U(j\omega)=\sum_kc_k\cdot2\pi\delta(\omega-k\omega_0).$$
>
> 提出常数 $2\pi$：
> $$U(j\omega)=2\pi\sum_kc_k\delta(\omega-k\omega_0).$$
>
> 检查其他选项：(d) 少 $2\pi$；(c) 是时域表达式；(b) 丢失系数 $c_k$。选 (a)。


---

## 51. Question 51（第 51 题）｜PDF p. 16 ^q51

$u(t)=5+4\cos(3t)-2\sin(3t)$ is periodic with fundamental frequency $\omega_0=3\ \mathrm{rad/s}$.（$u(t)=5+4\cos(3t)-2\sin(3t)$ 为周期信号，基频 $\omega_0=3\ \mathrm{rad/s}$。）Writing $U(j\omega)$ as a sum of weighted impulses, find the complex weight of the impulse located at $\omega=3$.（把 $U(j\omega)$ 写成带权冲激之和，求位于 $\omega=3$ 处冲激的复权重。）


$$
u(t)=5+4\cos(3t)-2\sin(3t)
$$

> [!success] Answer（答案）
> 位于 $\omega=3$ 的冲激权重为 $12.566+6.283j$

> [!abstract] 知识点讲解
> 见 2.11 周期信号的傅里叶变换 与 2.3 系数换算。
>
> - **三角到复系数**：$c_k=\dfrac{a_k-jb_k}{2}$。
> - **周期信号的 FT**：$U(j\omega)=2\pi\displaystyle\sum_kc_k\delta(\omega-k\omega_0)$，位于 $\omega=k\omega_0$ 的冲激权重为 $2\pi c_k$。

> [!example] 解答
> 读出三角系数：$a_1=4$，$b_1=-2$。
>
> 求复系数：
> $$c_1=\frac{a_1-jb_1}{2}=\frac{4+2j}{2}=2+j.$$
>
> 冲激权重：
> $$2\pi c_1=2\pi(2+j)=4\pi+2\pi j.$$
>
> 数值：
> $$4\pi=12.5664,\qquad 2\pi=6.2832,$$
> 故权重约为 $12.566+6.283j$。


---

## 52. Question 52（第 52 题）｜PDF p. 16 ^q52

A periodic, real-valued signal $u(t)$ has Fourier transform（周期实值信号 $u(t)$ 的傅里叶变换为）

$$U(j\omega)=2\pi\left[3\delta(\omega)+(1-2j)\delta(\omega-5)+(1+2j)\delta(\omega+5)\right].$$

Find $u(0)$.（给定实周期信号的冲激频谱，求 $u(0)$。）

> [!success] Answer（答案）
> $u(0)=5$

> [!abstract] 知识点讲解
> 见 2.11 周期信号的傅里叶变换。
>
> - **周期信号的 FT**：$U(j\omega)=2\pi\displaystyle\sum_kc_k\delta(\omega-k\omega_0)$，权重除以 $2\pi$ 即得 $c_k$。
> - **合成式**：$u(t)=\displaystyle\sum_kc_ke^{jk\omega_0t}$，令 $t=0$ 得 $u(0)=\displaystyle\sum_kc_k$。

> [!example] 解答
> 读出 $c_k$：整体除以 $2\pi$，
> $$c_0=3,\qquad c_1=1-2j,\qquad c_{-1}=1+2j.$$
>
> 写出合成式：
> $$u(t)=\sum_kc_ke^{jk\cdot5t}.$$
>
> 令 $t=0$，各指数项为 $1$：
> $$u(0)=c_0+c_1+c_{-1}.$$
>
> 求和：
> $$u(0)=3+(1-2j)+(1+2j)=5.$$


---

## 53. Question 53（第 53 题）｜PDF p. 16 ^q53

Which of the following correctly states Parseval's theorem for the Fourier transform?（哪一项正确陈述连续时间傅里叶变换的帕塞瓦尔定理？）

$$
E=\int_{-\infty}^{\infty}|u(t)|^2\,dt
$$

(a) $\displaystyle\int_{-\infty}^{\infty}|u(t)|^2\,dt=\frac{1}{2\pi}\int_{-\infty}^{\infty}|U(j\omega)|^2\,d\omega$ **✓**（时域总能量等于频域模平方积分的 $\frac{1}{2\pi}$）
(b) $\displaystyle\int_{-\infty}^{\infty}|u(t)|^2\,dt=\int_{-\infty}^{\infty}|U(j\omega)|^2\,d\omega$（时域能量直接等于频域模平方积分，缺少归一化系数）
(c) $\displaystyle\int_{-\infty}^{\infty}u(t)\,dt=\frac{1}{2\pi}\int_{-\infty}^{\infty}U(j\omega)\,d\omega$（把信号面积与频谱面积相等，实际并非能量等式）
(d) $\displaystyle\int_{-\infty}^{\infty}|u(t)|^2\,dt=\frac{1}{\pi}\int_{-\infty}^{\infty}|U(j\omega)|^2\,d\omega$（频域积分乘 $\frac{1}{\pi}$，系数错误）

> [!success] Answer（答案）
> (a) $\displaystyle\int|u(t)|^2dt=\frac{1}{2\pi}\int|U(j\omega)|^2d\omega$

> [!abstract] 知识点讲解
> 见 3.9 Parseval 定理（能量形式）。
>
> - **能量 Parseval**：$E=\displaystyle\int_{-\infty}^{\infty}|u(t)|^2dt=\dfrac1{2\pi}\displaystyle\int_{-\infty}^{\infty}|U(j\omega)|^2d\omega$。
> - **系数**：$\dfrac1{2\pi}$ 来自逆变换，不是 $\dfrac1\pi$。

> [!example] 解答
> 时域能量：
> $$E=\int|u(t)|^2dt.$$
>
> 用逆变换代入并交换积分次序，正交性给出
> $$E=\frac{1}{2\pi}\int|U(j\omega)|^2d\omega.$$
>
> 对照选项：(b) 缺 $\frac{1}{2\pi}$；(c) 混入面积定理；(d) 系数为 $\frac{1}{\pi}$。选 (a)。


---

## 54. Question 54（第 54 题）｜PDF p. 17 ^q54

Find the energy of $u(t)=\dfrac{\sin(3t)}{\pi t}$.（求 $u(t)=\dfrac{\sin(3t)}{\pi t}$ 的能量。）


$$
u(t)=\frac{\sin(3t)}{\pi t}
$$

> [!success] Answer（答案）
> $E=0.9549$

> [!abstract] 知识点讲解
> 见 3.9 Parseval 定理（能量形式） 与 3.4 常用变换对。
>
> - **sinc 变换对**：$\dfrac{\sin Wt}{\pi t}\leftrightarrow p_{2W}(\omega)$，$W=3$ 时 $U(j\omega)=p_6(\omega)$。
> - **能量 Parseval**：$E=\dfrac1{2\pi}\displaystyle\int|U(j\omega)|^2d\omega=\dfrac1{2\pi}\int_{-3}^{3}1\,d\omega$。

> [!example] 解答
> 识别变换对：
> $$u(t)=\frac{\sin3t}{\pi t}\leftrightarrow U(j\omega)=p_6(\omega),$$
> 即 $|\omega|<3$ 内为 $1$。
>
> 套用能量 Parseval：
> $$E=\frac{1}{2\pi}\int_{-\infty}^{\infty}|U(j\omega)|^2d\omega.$$
>
> 代入矩形频谱：
> $$E=\frac{1}{2\pi}\int_{-3}^{3}1\,d\omega=\frac{6}{2\pi}.$$
>
> 化简：
> $$E=\frac{3}{\pi}=0.9549.$$


---

### 3. Frequency response (week 6)（频率响应，第 6 周）

Evaluating and using $G(j\omega)$（计算与使用频率响应 $G(j\omega)$）

---

## 55. Question 55（第 55 题）｜PDF p. 17 ^q55

A system has（某系统的频率响应为）

$$G(j\omega)=\frac{j\omega+2}{(j\omega)^2+5(j\omega)+4}.$$

Find the steady-state response to the input $u(t)=5\cos(2t+30^\circ)$.（求系统对输入 $u(t)=5\cos(2t+30^\circ)$ 的稳态响应。）


$$
G(j\omega)=\frac{j\omega+2}{(j\omega)^2+5j\omega+4},\qquad u(t)=5\cos(2t+30^\circ)
$$

> [!success] Answer（答案）
> 幅值 $1.41421$，相位 $-15.0000^\circ$

> [!abstract] 知识点讲解
> 见 4.1 正弦稳态的核心结论 与 4.2 计算步骤。
>
> - **频率响应**：$G(j\omega)=\dfrac{N(j\omega)}{D(j\omega)}$，把 $j\omega$ 当复数代入，$(j\omega)^2=-\omega^2$。
> - **正弦稳态**：$y_{ss}(t)=A|G(j\omega)|\cos\left(\omega t+\varphi+\angle G(j\omega)\right)$。
> - **模与相位**：$|a+bj|=\sqrt{a^2+b^2}$，$\angle(a+bj)=\arctan\dfrac ba$（按象限修正）。

> [!example] 解答
> 输入角频率 $\omega=2$，代入 $j\omega=2j$：
> $$G(j2)=\frac{2j+2}{(2j)^2+5(2j)+4}.$$
>
> 算分母：$(2j)^2=-4$，故
> $$-4+10j+4=10j.$$
>
> 化简：
> $$G(j2)=\frac{2+2j}{10j}=\frac{2+2j}{10j}\cdot\frac{-j}{-j}=\frac{(2+2j)(-j)}{10}=\frac{2-2j+2}{10}=0.2-0.2j.$$
>
> 求模与相位：
> $$|G(j2)|=\sqrt{0.2^2+(-0.2)^2}=\sqrt{0.08}=0.28284,$$
> $$\angle G(j2)=\arctan\frac{-0.2}{0.2}=-45^\circ.$$
>
> 输出幅度：
> $$5\times0.28284=1.41421.$$
>
> 输出相位：
> $$30^\circ-45^\circ=-15^\circ.$$
>
> 所以
> $$y_{ss}(t)=1.41421\cos(2t-15^\circ).$$


---

## 56. Question 56（第 56 题）｜PDF p. 17 ^q56

A system has（某系统的频率响应为）

$$G(j\omega)=\frac{j\omega+0.1}{j\omega+5}.$$

Its steady-state response to $u(t)=\cos(10t-50^\circ)$ is $y(t)=$（求系统对输入 $u(t)=\cos(10t-50^\circ)$ 的稳态响应 $y(t)$。）

$$
G(j\omega)=\frac{j\omega+0.1}{j\omega+5},\qquad u(t)=\cos(10t-50^\circ)
$$

(a) $0.372\cos(10t-24.0^\circ)$（输出幅值为 $0.372$，相位为 $-24^\circ$）
(b) $0.894\cos(10t-24.0^\circ)$ **✓**（输出幅值为 $0.894$，相位为 $-24^\circ$）
(c) $1.00\cos(10t-50.0^\circ)$（输出幅值为 $1$，相位为 $-50^\circ$）
(d) $0.894\cos(10t-76.0^\circ)$（输出幅值为 $0.894$，相位为 $-76^\circ$）

> [!success] Answer（答案）
> (b) $0.894\cos(10t-24.0^\circ)$

> [!abstract] 知识点讲解
> 见 4.1 正弦稳态的核心结论 与 4.2 计算步骤。
>
> - **正弦稳态**：$y_{ss}(t)=A|G(j\omega)|\cos\left(\omega t+\varphi+\angle G(j\omega)\right)$。
> - **商的模与相位**：$\left|\dfrac{z_1}{z_2}\right|=\dfrac{|z_1|}{|z_2|}$，$\arg\dfrac{z_1}{z_2}=\arg z_1-\arg z_2$。
> - **代入频率**：只代输入频率 $\omega=10$。

> [!example] 解答
> 代 $\omega=10$：
> $$G(j10)=\frac{0.1+10j}{5+10j}.$$
>
> 求模：
> $$|G(j10)|=\frac{\sqrt{0.1^2+10^2}}{\sqrt{5^2+10^2}}=\frac{\sqrt{100.01}}{\sqrt{125}}=\frac{10.0005}{11.1803}=0.8944.$$
>
> 求相位：
> $$\angle G(j10)=\arctan\frac{10}{0.1}-\arctan\frac{10}{5}=89.43^\circ-63.43^\circ=26.0^\circ.$$
>
> 输出幅度等于输入幅度 $1$ 乘 $|G|$：$0.894$。
>
> 输出相位：
> $$-50^\circ+26^\circ=-24^\circ.$$
>
> 选 (b)。干扰项 $0.372$ 是 $|G(j2)|$，代错了频率。


---

## 57. Question 57（第 57 题）｜PDF p. 18 ^q57

A vehicle's height $h$ and road height $r$ are related by（车辆高度 $h$ 与路面高度 $r$ 的关系为）

$$m\ddot{h}=-k(h-r)-b(\dot{h}-\dot{r})$$

with $m=1$, $k=2$, $b=3$ (SI units).（其中 $m=1$、$k=2$、$b=3$，均采用国际单位制。）For a sinusoidal road profile $r(t)=\cos(2t)$, the vehicle height reaches steady state. Find its RMS value.（当路面起伏为正弦 $r(t)=\cos(2t)$ 时，车辆高度进入稳态。求其有效值。）


$$
m\ddot{h}=-k(h-r)-b(\dot{h}-\dot{r}),\quad m=1,\ k=2,\ b=3,\ r(t)=\cos2t
$$

> [!success] Answer（答案）
> $h_{\mathrm{RMS}}=0.707107$

> [!abstract] 知识点讲解
> 见 4.3 直流输入与 RMS。
>
> - **微分方程到频率响应**：$m\ddot h+b\dot h+kh=b\dot r+kr\Rightarrow G(j\omega)=\dfrac{k+bj\omega}{k-m\omega^2+bj\omega}$。
> - **正弦稳态**：输出峰值 $=|G(j\omega)|\times$ 输入峰值，频率不变。
> - **RMS**：正弦 $B\cos(\omega t+\theta)$ 的 $X_{\text{RMS}}=\dfrac{B}{\sqrt2}$，平均功率 $P=\dfrac{B^2}{2}$。

> [!example] 解答
> 把方程整理成输出 $h$、输入 $r$ 的形式：
> $$m\ddot h+b\dot h+kh=br'+kr.$$
>
> 两边做傅里叶变换（设零初值），得
> $$(m(j\omega)^2+bj\omega+k)H(j\omega)=(bj\omega+k)R(j\omega).$$
>
> 传递函数：
> $$G(j\omega)=\frac{k+bj\omega}{k-m\omega^2+bj\omega}.$$
>
> 代入 $m=1$、$k=2$、$b=3$：
> $$G(j\omega)=\frac{2+3j\omega}{2-\omega^2+3j\omega}.$$
>
> 取 $\omega=2$：
> $$G(j2)=\frac{2+6j}{2-4+6j}=\frac{2+6j}{-2+6j}.$$
>
> 求模：分子分母模相同，
> $$|2+6j|=\sqrt{4+36}=\sqrt{40},\qquad |-2+6j|=\sqrt{4+36}=\sqrt{40},$$
> 故 $|G(j2)|=1$。
>
> 输出峰值等于输入峰值 $1$，RMS：
> $$h_{\text{RMS}}=\frac{1}{\sqrt2}=0.707107.$$


---

## 58. Question 58（第 58 题）｜PDF p. 18 ^q58

A system has（某系统的频率响应为）

$$G(j\omega)=\frac{2(j\omega)^2+4}{(j\omega)^2+4(j\omega)+4}.$$

Find $|G(j2)|$ and $\arg G(j2)$.（求 $|G(j2)|$ 与 $\arg G(j2)$。）


$$
G(j\omega)=\frac{2(j\omega)^2+4}{(j\omega)^2+4j\omega+4}
$$

> [!success] Answer（答案）
> $|G(j2)|=0.500000$，$\arg G(j2)=90.0000^\circ$

> [!abstract] 知识点讲解
> 见 4.2 计算步骤。
>
> - **频率响应**：$G(j\omega)$ 中 $(j\omega)^2=-\omega^2$，$(j\omega)^3=-j\omega^3$。
> - **模与相位**：$|a+bj|=\sqrt{a^2+b^2}$，$\arg(a+bj)=\arctan\dfrac ba$。

> [!example] 解答
> 代 $\omega=2$：
> $$G(j2)=\frac{2(2j)^2+4}{(2j)^2+4(2j)+4}.$$
>
> 用 $(2j)^2=-4$：分子 $2(-4)+4=-4$。
>
> 分母：
> $$-4+8j+4=8j.$$
>
> 化简：
> $$G(j2)=\frac{-4}{8j}=\frac{-4}{8j}\cdot\frac{-j}{-j}=\frac{4j}{8}=0.5j.$$
>
> 模与相位：
> $$|G(j2)|=0.5,\qquad \arg G(j2)=90^\circ.$$


---

## 59. Question 59（第 59 题）｜PDF p. 18 ^q59

A system has（某系统的频率响应为）

$$G(j\omega)=\frac{300}{j\omega+4}.$$

Find the phase of $G(j4)$ in degrees.（求 $G(j4)$ 的相位，单位为度。）


$$
G(j\omega)=\frac{300}{j\omega+4}
$$

> [!success] Answer（答案）
> $\arg G(j4)=-45.0000^\circ$

> [!abstract] 知识点讲解
> 见 4.2 计算步骤。
>
> - **相位**：$\arg\dfrac{z_1}{z_2}=\arg z_1-\arg z_2$。
> - **正实数与复数**：$\arg 300=0$，$\arg(4+4j)=\arctan1=45^\circ$。

> [!example] 解答
> 代 $\omega=4$：
> $$G(j4)=\frac{300}{4+4j}.$$
>
> 分子为正实数，相位为零。
>
> 分母相位：
> $$\arg(4+4j)=\arctan\frac44=45^\circ.$$
>
> 相除等于相位相减：
> $$\arg G(j4)=0-45^\circ=-45.0000^\circ.$$


---

## 60. Question 60（第 60 题）｜PDF p. 18 ^q60

A river's height $y(t)$ (in feet) responds to rainfall rate $u(t)$ (in/hr) via（河流水位 $y(t)$（单位：英尺）与降雨率 $u(t)$（单位：英寸/小时）之间的关系为）

$$G(j\omega)=\frac{10}{(9j\omega+1)(16j\omega+1)},$$

with time in hours. Find $|G(j\omega)|$ at $\omega=1/12\ \mathrm{rad/hr}$.（时间单位为小时。求 $\omega=1/12\ \mathrm{rad/hr}$ 处的 $|G(j\omega)|$。）


$$
G(j\omega)=\frac{10}{(9j\omega+1)(16j\omega+1)},\qquad \omega=\frac{1}{12}
$$

> [!success] Answer（答案）
> $|G(j\omega)|=4.8$

> [!abstract] 知识点讲解
> 见 4.2 计算步骤。
>
> - **乘积的模**：$|z_1z_2|=|z_1||z_2|$，$\left|\dfrac{z_1}{z_2}\right|=\dfrac{|z_1|}{|z_2|}$。
> - **一阶因子**：$|1+ja|=\sqrt{1+a^2}$。

> [!example] 解答
> 代 $\omega=\frac{1}{12}$：
> $$9j\omega=9j\cdot\frac1{12}=\frac34j,\qquad 16j\omega=16j\cdot\frac1{12}=\frac43j.$$
>
> 两个因式：
> $$1+\frac34j,\qquad 1+\frac43j.$$
>
> 求模：
> $$\left|1+\frac34j\right|=\sqrt{1+\frac{9}{16}}=\frac54,$$
> $$\left|1+\frac43j\right|=\sqrt{1+\frac{16}{9}}=\frac53.$$
>
> 相乘：
> $$|G|=\frac{10}{\frac54\cdot\frac53}=\frac{10}{\frac{25}{12}}=\frac{120}{25}=4.8.$$


---

## 61. Question 61（第 61 题）｜PDF p. 18 ^q61

A system obeys $\ddot{y}+3\dot{y}+2y=u$, so（某系统服从 $\ddot{y}+3\dot{y}+2y=u$，因此）

$$G(j\omega)=\frac{1}{(j\omega+1)(j\omega+2)}.$$

Find the steady-state output for the constant input $u(t)=1$.（常值输入 $u(t)=1$ 时求稳态输出。）


$$
\ddot{y}+3\dot{y}+2y=u,\qquad u(t)=1
$$

> [!success] Answer（答案）
> $y_{ss}=0.500000$

> [!abstract] 知识点讲解
> 见 4.3 直流输入与 RMS。
>
> - **由微分方程求频率响应**：$(j\omega)^2Y+3j\omega Y+2Y=U\Rightarrow G(j\omega)=\dfrac1{(j\omega+1)(j\omega+2)}$。
> - **直流增益**：常数输入 $u=A$ 的稳态输出 $y_{ss}=A\,G(0)$，$G(0)$ 即 $\omega=0$ 代入。

> [!example] 解答
> 从微分方程求 $G(j\omega)$：两边变换得
> $$\left[(j\omega)^2+3j\omega+2\right]Y(j\omega)=U(j\omega),$$
> $$G(j\omega)=\frac{1}{(j\omega+1)(j\omega+2)}.$$
>
> 取 $\omega=0$：
> $$G(0)=\frac{1}{1\cdot2}=\frac12.$$
>
> 输入 $u=1$，稳态输出：
> $$y_{ss}=G(0)\cdot1=0.5.$$


---

## 62. Question 62（第 62 题）｜PDF p. 18 ^q62

A full-wave rectified sine $u(t)=|\sin t|$ (period $T=\pi$, $\omega_0=2$) drives a first-order lowpass filter with（全波整流正弦 $u(t)=|\sin t|$（周期 $T=\pi$，$\omega_0=2$）驱动一个一阶低通滤波器）

$$G(j\omega)=\frac{1}{1+3j\omega}.$$

Find the DC component of the output $y(t)$.（求输出 $y(t)$ 的直流分量。）


$$
u(t)=|\sin t|,\qquad G(j\omega)=\frac{1}{1+3j\omega}
$$

> [!success] Answer（答案）
> $y_{\mathrm{DC}}=0.636620$

> [!abstract] 知识点讲解
> 见 4.1 正弦稳态的核心结论 与 4.7 系统对周期信号的作用。
>
> - **系统对谐波的作用**：$d_k=c_kG(jk\omega_0)$（由 $Y=GU$ 与周期信号的 FT 得出）。
> - **直流系数**：$c_0=\dfrac1T\displaystyle\int_Tu(t)dt$；$d_0=c_0G(0)$。
> - **直流增益**：$G(j\omega)=\dfrac1{1+3j\omega}$，$G(0)=1$。

> [!example] 解答
> 输入直流系数：
> $$c_0=\frac{1}{T}\int_0^Tu\,dt=\frac{1}{\pi}\int_0^{\pi}\sin t\,dt.$$
>
> 算积分：
> $$\int_0^\pi\sin t\,dt=\left[-\cos t\right]_0^\pi=1-(-1)=2.$$
>
> 所以
> $$c_0=\frac{2}{\pi}.$$
>
> 直流增益：
> $$G(0)=\frac{1}{1+0}=1.$$
>
> 输出直流：
> $$d_0=c_0G(0)=\frac{2}{\pi}=0.636620.$$


---

## 63. Question 63（第 63 题）｜PDF p. 18 ^q63

A system has impulse response $h(t)=3e^{-6t}H(t)$, so（某系统的冲激响应为 $h(t)=3e^{-6t}H(t)$，因此）

$$G(j\omega)=\frac{3}{j\omega+6}.$$

What is the steady-state output when the input is the constant signal $u(t)=4$ for all $t$?（输入为恒定的 $u(t)=4$ 时，稳态输出是多少？）

$$
h(t)=3e^{-6t}H(t),\qquad u(t)=4
$$

(a) $y=0.500$（输出常值为 $0.500$）
(b) $y=8.00$（输出常值为 $8.00$）
(c) $y=12.0$（输出常值为 $12.0$）
(d) $y=2.00$ **✓**（输出常值为 $2.00$）

> [!success] Answer（答案）
> (d) $y=2.00$

> [!abstract] 知识点讲解
> 见 4.3 直流输入与 RMS 与 4.6 冲激响应与频率响应。
>
> - **冲激响应与频率响应**：$h(t)\leftrightarrow G(j\omega)$；$G(0)=\displaystyle\int_{-\infty}^{\infty}h(t)dt$。
> - **直流输入**：$u=A$ 时 $y_{ss}=A\,G(0)$。
> - **变换对**：$3e^{-6t}H(t)\leftrightarrow\dfrac3{6+j\omega}$。

> [!example] 解答
> 写传递函数：
> $$G(j\omega)=\frac{3}{j\omega+6}.$$
>
> 取直流增益：
> $$G(0)=\frac{3}{6}=0.5.$$
>
> 用冲激响应校验：
> $$\int_0^\infty3e^{-6t}dt=\frac{3}{6}=0.5.$$
>
> 输入为常数 $4$，稳态输出：
> $$y=4\times0.5=2.00.$$
>
> 选 (d)。


---

## 64. Question 64（第 64 题）｜PDF p. 19 ^q64

The straight-line (asymptotic) Bode magnitude plot of a first-order system is flat at $12\ \mathrm{dB}$ for $\omega<200\ \mathrm{rad/s}$ and falls at $-20\ \mathrm{dB/decade}$ for $\omega>200\ \mathrm{rad/s}$, with its corner at $\omega=200\ \mathrm{rad/s}$.（一阶系统的渐近波特幅频图在 $\omega<200\ \mathrm{rad/s}$ 时为 $12\ \mathrm{dB}$ 的水平线，$\omega>200\ \mathrm{rad/s}$ 后以 $-20\ \mathrm{dB/decade}$ 下降，转折点在 $\omega=200\ \mathrm{rad/s}$。）Reading off that plot, what is $20\log_{10}|G(j2000)|$?（按图读取，$20\log_{10}|G(j2000)|$ 等于多少？）


$$
12\ \mathrm{dB}\ (\omega<200),\qquad -20\ \mathrm{dB/decade}\ (\omega>200)
$$

> [!success] Answer（答案）
> $20\log_{10}|G(j2000)|=-8.00000\ \mathrm{dB}$

> [!abstract] 知识点讲解
> 见 4.4 Bode 图。
>
> - **一阶低通渐近幅频**：$\omega\gg\omega_c$ 时每 decade 下降 $20$ dB，即 $|G|\approx\dfrac{|G(0)|}{\omega/\omega_c}$。
> - **转折频率**：$\omega_c=200$；一个 decade 为频率乘 $10$。
> - **dB 定义**：$20\log_{10}|G|$，dB 值可按斜率线性外推。

> [!example] 解答
> 判断转折频率：$\omega_c=200\ \mathrm{rad/s}$。
>
> 求跨越的 decade 数：
> $$\log_{10}\frac{2000}{200}=\log_{10}10=1.$$
>
> 一个 decade 的下降量：$20$ dB。
>
> 从平台值外推：
> $$12-20=-8\ \mathrm{dB}.$$
>
> 结果 $-8.00000$ dB。


---

## 65. Question 65（第 65 题）｜PDF p. 19 ^q65

The straight-line (asymptotic) Bode phase plot of a system with a single real pole at $\omega_c=1000\ \mathrm{rad/s}$ is $0^\circ$ for $\omega\le\omega_c/10$, a straight segment of slope $-45^\circ$ per decade from $\omega_c/10$ to $10\omega_c$, and $-90^\circ$ for $\omega\ge10\omega_c$.（某系统在 $\omega_c=1000\ \mathrm{rad/s}$ 处有一个实极点。其渐近波特相频图在 $\omega\le\omega_c/10$ 时为 $0^\circ$，从 $\omega_c/10$ 到 $10\omega_c$ 是斜率为 $-45^\circ$/decade 的直线段，$\omega\ge10\omega_c$ 后为 $-90^\circ$。）Reading off that plot, what is the phase at $\omega=10{,}000\ \mathrm{rad/s}$?（按图读取，$\omega=10{,}000\ \mathrm{rad/s}$ 处的相位是多少？）

$$
\omega_c=1000\ \mathrm{rad/s},\qquad \omega=10{,}000\ \mathrm{rad/s}
$$

(a) $-90^\circ$ **✓**（渐近相位为 $-90^\circ$）
(b) $-84.29^\circ$（相位为 $-84.29^\circ$，这是精确值而非渐近值）
(c) $0^\circ$（相位为 $0^\circ$）
(d) $-45^\circ$（相位为 $-45^\circ$）

> [!success] Answer（答案）
> (a) $-90^\circ$

> [!abstract] 知识点讲解
> 见 4.4 Bode 图 中一阶极点的相位渐近线。
>
> - **渐近相频**：$\omega\le\dfrac{\omega_c}{10}$ 为 $0^\circ$；$\dfrac{\omega_c}{10}\le\omega\le10\omega_c$ 每 decade 降 $45^\circ$；$\omega\ge10\omega_c$ 为 $-90^\circ$。
> - **精确相位**（对照）：$\arg\dfrac1{1+j\omega/\omega_c}=-\arctan\dfrac{\omega}{\omega_c}$。

> [!example] 解答
> 求渐近线的两个端点：
> $$\frac{\omega_c}{10}=\frac{1000}{10}=100,\qquad 10\omega_c=10000.$$
>
> 判断 $\omega=10000$ 的位置：恰在右端点。
>
> 该点渐近值：
> $$-90^\circ.$$
>
> 识别干扰项：$-84.29^\circ=\arctan(-10)$ 是精确相位，不是渐近值。选 (a)。


---

## 66. Question 66（第 66 题）｜PDF p. 19 ^q66


A system has impulse response $h(t)=e^{-at}H(t)$ with $a=3$, so $G(j\omega)=1/(a+j\omega)$ … [truncated in source]（一个系统的冲激响应为 $h(t)=e^{-at}H(t)$，其中 $a=3$，因此频率响应为 $G(j\omega)=1/(a+j\omega)$；后续原文截断。根据反馈推断，题目要求求 $-3\ \mathrm{dB}$ 截止频率。）


$$
h(t)=e^{-3t}H(t),\qquad \omega_{-3\mathrm{dB}}=?
$$

> [!success] Answer（答案）
> $\omega_{-3\mathrm{dB}}=3.00000\ \mathrm{rad/s}$

> [!abstract] 知识点讲解
> 见 4.5 截止频率。
>
> - **一阶幅频**：$|G(j\omega)|=\dfrac1{\sqrt{a^2+\omega^2}}$，$|G(0)|=\dfrac1a$。
> - **$-3$ dB 定义**：$\dfrac{|G(j\omega_{-3\text{dB}})|}{|G(0)|}=\dfrac1{\sqrt2}$，即半功率点。

> [!example] 解答
> 写频率响应：
> $$G(j\omega)=\frac{1}{3+j\omega}.$$
>
> 模与直流值：
> $$|G(j\omega)|=\frac{1}{\sqrt{9+\omega^2}},\qquad |G(0)|=\frac13.$$
>
> 列方程：
> $$\frac{|G(j\omega)|}{|G(0)|}=\frac{3}{\sqrt{9+\omega^2}}=\frac{1}{\sqrt2}.$$
>
> 平方：
> $$\frac{9}{9+\omega^2}=\frac12\Rightarrow 18=9+\omega^2\Rightarrow \omega^2=9.$$
>
> 取正根：
> $$\omega=3\ \mathrm{rad/s}.$$


---

## 67. Question 67（第 67 题）｜PDF p. 20 ^q67

Four systems:（下列四个系统：）

(i) $G(j\omega)=\dfrac{1}{1+j\omega/10}$

(ii) $G(j\omega)=\dfrac{10^4}{(j\omega)^2+10(j\omega)+10^4}$

(iii) $G(j\omega)=\dfrac{100}{(j\omega)^2+20(j\omega)+100}$

(iv) $G(j\omega)=\dfrac{1}{1+j\omega/10}\cdot\dfrac{10^4}{(j\omega)^2+10(j\omega)+10^4}$

Their Bode magnitude diagrams, in some order, are below. Match each system to its diagram.（它们的波特幅频图按某种顺序列在下方，请把每个系统与对应的图匹配。）

$$
G_1=\frac{1}{1+j\omega/10},\qquad G_2=\frac{10^4}{(j\omega)^2+10j\omega+10^4}
$$

![[Pasted image 20261031132109.png]]

> [!success] Answer（答案）
> (i) B　(ii) D　(iii) A　(iv) C

> [!abstract] 知识点讲解
> 见 4.4 Bode 图 与 5.3 共振。
>
> - **一阶因子**：$\dfrac1{1+j\omega/\omega_c}$，高频斜率 $-20$ dB/decade。
> - **二阶标准形**：$\dfrac{\omega_n^2}{(j\omega)^2+2\zeta\omega_n(j\omega)+\omega_n^2}$，高频斜率 $-40$ dB/decade；$\zeta<\dfrac1{\sqrt2}$ 才有谐振峰。
> - **读数**：由分母一次项系数 $2\zeta\omega_n$ 与常数项 $\omega_n^2$ 求 $\omega_n$、$\zeta$。

> [!example] 解答
> 数极点定斜率：
> - (i) 一个极点，末端 $-20$ dB/decade。
> - (ii)(iii) 两个极点，末端 $-40$ dB/decade。
> - (iv) 三个极点，末端 $-60$ dB/decade。
>
> (iv) 末端 $-60$，对应 C。
>
> 区分 (ii) 与 (iii)：把分母写成标准形式。
> $$(ii):\ (j\omega)^2+10j\omega+10^4\Rightarrow \omega_n=100,\ 2\zeta\omega_n=10\Rightarrow\zeta=0.05.$$
> $$(iii):\ (j\omega)^2+20j\omega+100\Rightarrow \omega_n=10,\ 2\zeta\omega_n=20\Rightarrow\zeta=1.$$
>
> $\zeta=0.05<0.707$ 有尖峰，(ii) 对应 D。
>
> $\zeta=1$ 无峰，(iii) 对应 A。
>
> (i) 只剩 $-20$ dB/decade，对应 B。


---

## 68. Question 68（第 68 题）｜PDF p. 21 ^q68

A system has（某系统的频率响应为）

$$G(j\omega)=\frac{4}{j\omega+2}.$$

Find its impulse response $h(t)$.（求该系统的冲激响应 $h(t)$。）


$$
G(j\omega)=\frac{4}{j\omega+2}
$$

> [!success] Answer（答案）
> $h(t)=4e^{-2t}H(t)$

> [!abstract] 知识点讲解
> 见 4.6 冲激响应与频率响应 与 3.4 常用变换对。
>
> - **变换对**：$\dfrac1{a+j\omega}\leftrightarrow e^{-at}H(t)$。
> - **线性**：$\dfrac{A}{a+j\omega}\leftrightarrow Ae^{-at}H(t)$；单边指数必须带 $H(t)$。

> [!example] 解答
> 改写：
> $$G(j\omega)=4\cdot\frac{1}{2+j\omega}.$$
>
> 查表：
> $$\frac{1}{2+j\omega}\leftrightarrow e^{-2t}H(t).$$
>
> 乘常数 $4$：
> $$h(t)=4e^{-2t}H(t).$$
>
> 校验 $h(0^+)=4$，而 $G(j\infty)=0$；又 $\int h\,dt=G(0)=2$，与 $\frac{4}{2}=2$ 一致。


---

## 69. Question 69（第 69 题）｜PDF p. 21 ^q69

A first-order system with impulse response $h_1(t)=2e^{-5t}H(t)$ is connected in cascade with an ideal delay of $3$ seconds (impulse response $\delta(t-3)$). Find the impulse response $h(t)$ of the overall cascade system.（求一阶系统与三秒理想延迟级联后的整体冲激响应。）


$$
h_1(t)=2e^{-5t}H(t),\qquad h_2(t)=\delta(t-3)
$$

> [!success] Answer（答案）
> $h(t)=2e^{-5(t-3)}H(t-3)$

> [!abstract] 知识点讲解
> 见 4.6 冲激响应与频率响应 中的级联性质。
>
> - **级联**：$h=h_1*h_2$；时域卷积对应频域乘积 $G=G_1G_2$。
> - **与冲激卷积**：$h_1(t)*\delta(t-t_0)=h_1(t-t_0)$，频域乘 $e^{-j\omega t_0}$。
> - **延迟指数**：$e^{-a(t-t_0)}H(t-t_0)$，指数和阶跃一起平移。

> [!example] 解答
> 级联卷积：
> $$h(t)=h_1(t)*h_2(t)=2e^{-5t}H(t)*\delta(t-3).$$
>
> 用延迟性质：
> $$h(t)=2e^{-5(t-3)}H(t-3).$$
>
> 检查常见错误写法 $2e^{-5t}H(t-3)$：它在 $t=3$ 处取值为 $2e^{-15}$，比正确值小 $e^{-15}$ 倍。
>
> 也可频域验证：
> $$G(j\omega)=\frac{2}{5+j\omega}e^{-j3\omega}.$$


---

## 70. Question 70（第 70 题）｜PDF p. 21 ^q70

A system has（某系统的频率响应为）

$$G(j\omega)=\frac{3}{j\omega+1}+\frac{2}{j\omega+4}.$$

What is its impulse response $h(t)$?（求该系统的冲激响应 $h(t)$。）

$$
G(j\omega)=\frac{3}{j\omega+1}+\frac{2}{j\omega+4}
$$

(a) $h(t)=5e^{-5t}H(t)$（两个衰减项错误地合并为 $5e^{-5t}H(t)$）
(b) $h(t)=3e^{-4t}H(t)+2e^{-t}H(t)$（衰减速率与对应系数错误配对）
(c) $h(t)=3e^{-t}H(t)-2e^{-4t}H(t)$（第二项符号为负）
(d) $h(t)=3e^{-t}H(t)+2e^{-4t}H(t)$ **✓**（两个指数衰减分量均为正且各自速率正确）

> [!success] Answer（答案）
> (d) $3e^{-t}H(t)+2e^{-4t}H(t)$

> [!abstract] 知识点讲解
> 见 4.6 冲激响应与频率响应。
>
> - **变换对**：$\dfrac1{a+j\omega}\leftrightarrow e^{-at}H(t)$。
> - **线性**：频域相加对应时域相加，不同极点不能合并成单一指数。

> [!example] 解答
> 拆成两项：
> $$G(j\omega)=\frac{3}{1+j\omega}+\frac{2}{4+j\omega}.$$
>
> 逐项反变换：
> $$\frac{3}{1+j\omega}\leftrightarrow3e^{-t}H(t),$$
> $$\frac{2}{4+j\omega}\leftrightarrow2e^{-4t}H(t).$$
>
> 相加：
> $$h(t)=3e^{-t}H(t)+2e^{-4t}H(t).$$
>
> 检查错误选项：(a) 把两个极点误合并为 $e^{-5t}$；(b) 幅度与极点配错；(c) 第二项符号错。选 (d)。


---

## 71. Question 71（第 71 题）｜PDF p. 21 ^q71

A system has impulse response $h(t)=4e^{-3t}\sin(5t)H(t)$.（某系统的冲激响应为 $h(t)=4e^{-3t}\sin(5t)H(t)$。）Its transfer function $G(j\omega)$ is:（其传递函数 $G(j\omega)$ 是：）

$$
h(t)=4e^{-3t}\sin(5t)H(t)
$$

(a) $\dfrac{4}{(3+j\omega)^2+25}$（分子只有 $4$，缺少振荡频率 $5$）
(b) $\dfrac{20}{(5+j\omega)^2+9}$（把衰减常数 $3$ 与振荡频率 $5$ 的位置弄反）
(c) $\dfrac{4(3+j\omega)}{(3+j\omega)^2+25}$（这是阻尼余弦而非阻尼正弦对应的形式）
(d) $\dfrac{20}{(3+j\omega)^2+25}$ **✓**（正确表达式，分子为 $20$，分母为 $(3+j\omega)^2+25$）

> [!success] Answer（答案）
> (d) $\dfrac{20}{(3+j\omega)^2+25}$

> [!abstract] 知识点讲解
> 见 4.6 冲激响应与频率响应 与 7.2 常用变换对。
>
> - **阻尼正弦对**：$e^{-at}\sin(\omega_0t)H(t)\leftrightarrow\dfrac{\omega_0}{(a+j\omega)^2+\omega_0^2}$。
> - **阻尼余弦对**：$e^{-at}\cos(\omega_0t)H(t)\leftrightarrow\dfrac{a+j\omega}{(a+j\omega)^2+\omega_0^2}$。
> - **线性**：乘幅值只改分子。

> [!example] 解答
> 读出参数：$a=3$，$\omega_0=5$，幅度 $4$。
>
> 套公式：
> $$e^{-3t}\sin5t\,H(t)\leftrightarrow\frac{5}{(3+j\omega)^2+25}.$$
>
> 乘幅度 $4$：
> $$G(j\omega)=\frac{20}{(3+j\omega)^2+25}.$$
>
> 校验 $G(0)$：$\frac{20}{9+25}=\frac{20}{34}$；又 $G(0)=\int h\,dt=\int_0^\infty4e^{-3t}\sin5t\,dt=4\cdot\frac{5}{34}=\frac{20}{34}$，一致。


---

### 4. Second order systems and stability (weeks 6–7)（二阶系统与稳定性，第 6—7 周）

Damping and resonance in second order systems（二阶系统的阻尼与谐振）

---

## 72. Question 72（第 72 题）｜PDF p. 22 ^q72

Which damping ratio makes a second-order system（哪个阻尼比使下面这个二阶系统达到临界阻尼）

$$G(j\omega)=\frac{K\omega_n^2}{(j\omega)^2+2\zeta\omega_n(j\omega)+\omega_n^2}$$

critically damped?（哪一阻尼比使该系统达到临界阻尼？）

(a) $\zeta=1.5$（阻尼比为 $1.5$）
(b) $\zeta=0$（阻尼比为 $0$）
(c) $\zeta=1.0$ **✓**（阻尼比为 $1.0$）
(d) $\zeta=0.4$（阻尼比为 $0.4$）

> [!success] Answer（答案）
> (c) $\zeta=1.0$

> [!abstract] 知识点讲解
> 见 5.2 极点与阻尼。
>
> - **二阶标准形**：$G(j\omega)=\dfrac{K\omega_n^2}{(j\omega)^2+2\zeta\omega_n(j\omega)+\omega_n^2}$，极点满足 $s^2+2\zeta\omega_ns+\omega_n^2=0$。
> - **判别式**：$\Delta=4\omega_n^2(\zeta^2-1)$。
> - **分类**：$\zeta>1$ 过阻尼（两实极点）；$\zeta=1$ 临界阻尼（重极点 $-\omega_n$）；$0<\zeta<1$ 欠阻尼（共轭复极点）。

> [!example] 解答
> 写出特征方程：
> $$s^2+2\zeta\omega_ns+\omega_n^2=0.$$
>
> 求判别式：
> $$\Delta=(2\zeta\omega_n)^2-4\omega_n^2=4\omega_n^2(\zeta^2-1).$$
>
> 临界阻尼要求 $\Delta=0$：
> $$\zeta^2-1=0\Rightarrow \zeta=\pm1.$$
>
> 取 $\zeta>0$ 的物理解：$\zeta=1$，两极点重合于 $-\omega_n$。
>
> 选 (c)。


---

## 73. Question 73（第 73 题）｜PDF p. 22 ^q73

A second-order system in the standard form $(j\omega)^2+2\zeta\omega_n(j\omega)+\omega_n^2$ has its two poles at $-10^4\pm j10^4\ \mathrm{rad/s}$.（标准形式为 $(j\omega)^2+2\zeta\omega_n(j\omega)+\omega_n^2$ 的二阶系统，两个极点位于 $-10^4\pm j10^4\ \mathrm{rad/s}$。）What is $\zeta$?（求阻尼比 $\zeta$。）

$$
p_{1,2}=-10^4\pm j10^4
$$

(a) $0.5$（阻尼比为 $0.5$）
(b) $1$（阻尼比为 $1$）
(c) $0.707$ **✓**（阻尼比约为 $0.707$）
(d) $1.414$（阻尼比约为 $1.414$）

> [!success] Answer（答案）
> (c) $0.707$

> [!abstract] 知识点讲解
> 见 5.2 极点与阻尼。
>
> - **极点表示**：$p=-\zeta\omega_n\pm j\omega_n\sqrt{1-\zeta^2}$。
> - **自然频率**：$\omega_n=|p|=\sqrt{(\Re p)^2+(\Im p)^2}$。
> - **阻尼比**：$\zeta=\dfrac{|\Re p|}{\omega_n}$。

> [!example] 解答
> 极点 $p=-10^4\pm j10^4$。
>
> 求自然频率：
> $$\omega_n=|p|=\sqrt{(10^4)^2+(10^4)^2}=10^4\sqrt2.$$
>
> 求实部绝对值：$|\operatorname{Re}p|=10^4$。
>
> 求阻尼比：
> $$\zeta=\frac{10^4}{10^4\sqrt2}=\frac{1}{\sqrt2}=0.707.$$
>
> 选 (c)。


---

## 74. Question 74（第 74 题）｜PDF p. 23 ^q74

A second-order system has $\zeta=0.8$. Does $|G(j\omega)|$ have a resonant peak at a nonzero frequency?（阻尼比 $\zeta=0.8$ 时，是否存在非零频率谐振峰？）

$$
\zeta=0.8
$$

(a) No, because $\zeta=0.8>\dfrac{1}{\sqrt{2}}\approx0.7071$ **✓**（不会，因为 $0.8$ 大于 $\frac{1}{\sqrt2}$ 约 $0.7071$）
(b) It cannot be determined without knowing $K$（不知道增益 $K$ 就无法确定）
(c) Yes, at $\omega_r=\omega_n\sqrt{1-2(0.8)^2}$（会，谐振频率由给出的根式计算）
(d) Yes, because any $\zeta<1$ (underdamped) gives a resonant peak（会，因为所有阻尼比小于 $1$ 的欠阻尼系统都有谐振峰）

> [!success] Answer（答案）
> (a) 不出现，因为 $\zeta=0.8>\frac{1}{\sqrt2}\approx0.7071$

> [!abstract] 知识点讲解
> 见 5.3 共振。
>
> - **谐振频率**：$\omega_r=\omega_n\sqrt{1-2\zeta^2}$，仅当 $\zeta<\dfrac1{\sqrt2}$ 时有非零实解。
> - **峰值**：$|G(j\omega_r)|=\dfrac{|K|}{2\zeta\sqrt{1-\zeta^2}}$。
> - **判别**：$1-2(0.8)^2=-0.28<0$，无共振峰。

> [!example] 解答
> 写出幅频平方：
> $$|G(j\omega)|^2=\frac{K^2\omega_n^4}{(\omega_n^2-\omega^2)^2+(2\zeta\omega_n\omega)^2}.$$
>
> 对 $\omega^2$ 求极值，可得峰值频率
> $$\omega_r=\omega_n\sqrt{1-2\zeta^2}.$$
>
> 要求根号内为正：
> $$1-2\zeta^2>0\Rightarrow \zeta<\frac{1}{\sqrt2}.$$
>
> 代入 $\zeta=0.8$：
> $$1-2(0.8)^2=1-1.28=-0.28<0,$$
> 不存在实的 $\omega_r$。
>
> 说明幅值从 $|G(j0)|$ 单调下降，选 (a)。


---

## 75. Question 75（第 75 题）｜PDF p. 23 ^q75

A series RLC circuit is driven by $u(t)$, with the output $y(t)$ taken across the capacitor, so（串联 RLC 电路由 $u(t)$ 驱动，输出 $y(t)$ 取自电容两端，因此）

$$LC\ddot{y}+RC\dot{y}+y=u.$$

Here $R=200\ \Omega$, $L=0.5\ \mathrm{H}$ and $C=2\ \mu\mathrm{F}$.（其中 $R=200\ \Omega$，$L=0.5\ \mathrm{H}$，$C=2\ \mu\mathrm{F}$。）Does $|G(j\omega)|$ have a resonant peak? If so, find $\omega_r$ and the peak value $|G(j\omega_r)|$ in dB.（$|G(j\omega)|$ 是否存在谐振峰？若存在，求谐振频率 $\omega_r$ 及峰值 $|G(j\omega_r)|$ 的分贝值。）


$$
LC\ddot{y}+RC\dot{y}+y=u,\qquad R=200\ \Omega,\ L=0.5\ \mathrm{H},\ C=2\ \mu\mathrm{F}
$$

> [!success] Answer（答案）
> $\omega_r=959.166\ \mathrm{rad/s}$，$|G(j\omega_r)|=2.55155$，即 $8.13609\ \mathrm{dB}$

> [!abstract] 知识点讲解
> 见 5.3 共振 与 5.2 RLC 电路的 $\omega_n$、$\zeta$。
>
> - **二阶标准形**：$G=\dfrac{K\omega_n^2}{(j\omega)^2+2\zeta\omega_n(j\omega)+\omega_n^2}$；RLC 取电容电压时 $\omega_n=\dfrac1{\sqrt{LC}}$，$\zeta=\dfrac R2\sqrt{\dfrac CL}$。
> - **谐振**：$\omega_r=\omega_n\sqrt{1-2\zeta^2}$，$M_r=\dfrac{|K|}{2\zeta\sqrt{1-\zeta^2}}$，条件 $\zeta<\dfrac1{\sqrt2}$。
> - **分贝值**：$20\lg M_r$。

> [!example] 解答
> 变换微分方程：
> $$\left[LC(j\omega)^2+RC(j\omega)+1\right]Y=U,$$
> $$G(j\omega)=\frac{1}{LC(j\omega)^2+RCj\omega+1}.$$
>
> 与标准形式对比，分母乘 $\frac{1}{LC}$：
> $$\omega_n^2=\frac{1}{LC}\Rightarrow \omega_n=\frac{1}{\sqrt{LC}}.$$
>
> 代入数值：$L=0.5$，$C=2\times10^{-6}$，
> $$LC=10^{-6}\Rightarrow \omega_n=1000\ \mathrm{rad/s}.$$
>
> 比较一次项：
> $$\frac{RC}{LC}=2\zeta\omega_n\Rightarrow \zeta=\frac{R}{2}\sqrt{\frac{C}{L}}.$$
>
> 代入数值：
> $$\sqrt{\frac{C}{L}}=\sqrt{\frac{2\times10^{-6}}{0.5}}=2\times10^{-3},$$
> $$\zeta=\frac{200}{2}\times2\times10^{-3}=0.2.$$
>
> 判断有峰：$0.2<0.7071$，有峰。
>
> 共振频率：
> $$\omega_r=1000\sqrt{1-2(0.04)}=1000\sqrt{0.92}=959.166.$$
>
> 峰值：
> $$M_r=\frac{1}{2(0.2)\sqrt{1-0.04}}=\frac{1}{0.4\times0.9798}=2.55155.$$
>
> 分贝：
> $$20\lg2.55155=8.13609\ \mathrm{dB}.$$


---

## 76. Question 76（第 76 题）｜PDF p. 23 ^q76

A designer wants a sharp resonant peak near $\omega_0=5\ \mathrm{rad/s}$, using a pair of complex conjugate poles at $-\alpha\pm j5$.（设计者希望在一对共轭复极点 $-\alpha\pm j5$ 下，于 $\omega_0=5\ \mathrm{rad/s}$ 附近得到尖锐的谐振峰。）Which choice of $\alpha$ gives the sharpest, highest resonant peak?（$\alpha$ 取哪个值时，谐振峰最尖锐、最高？）

$$
p_{1,2}=-\alpha\pm5j
$$

(a) $\alpha=2$（$\alpha=2$）
(b) $\alpha=0.5$（$\alpha=0.5$）
(c) $\alpha=0.05$ **✓**（$\alpha=0.05$）
(d) $\alpha=5$（$\alpha=5$）

> [!success] Answer（答案）
> (c) $\alpha=0.05$

> [!abstract] 知识点讲解
> 见 5.3 共振。
>
> - **极点与阻尼**：$p=-\alpha\pm j5\Rightarrow\omega_n=\sqrt{\alpha^2+25}$，$\zeta=\dfrac{\alpha}{\omega_n}$。
> - **峰值**：$M_r=\dfrac1{2\zeta\sqrt{1-\zeta^2}}$，$\zeta$ 越小峰越高越尖；$\zeta\ge\dfrac1{\sqrt2}$ 无峰。

> [!example] 解答
> 求 $\omega_n$：
> $$\omega_n=\sqrt{\alpha^2+5^2}=\sqrt{\alpha^2+25}.$$
>
> 求 $\zeta$：
> $$\zeta=\frac{\alpha}{\sqrt{\alpha^2+25}}.$$
>
> 判断峰高随 $\alpha$ 的变化：$\alpha$ 减小，$\zeta$ 减小，$M_r=\frac{1}{2\zeta\sqrt{1-\zeta^2}}$ 增大。
>
> 逐个比较：
> - $\alpha=2$：$\zeta=0.371$，$M_r=1.45$。
> - $\alpha=0.5$：$\zeta=0.0995$，$M_r=5.05$。
> - $\alpha=0.05$：$\zeta=0.0100$，$M_r=50.0$。
> - $\alpha=5$：$\zeta=0.707$，无峰。
>
> 峰最尖的是 $\alpha=0.05$，选 (c)。


---

## 77. Question 77（第 77 题）｜PDF p. 24 ^q77

An LTI system has（某 LTI 系统的传递函数为）

$$G(j\omega)=\frac{(j\omega)^2+j\omega+1}{(j\omega+2)\left((j\omega)^2+4\right)}.$$

Classify the system.（对该系统进行稳定性分类。）

(a) Marginally stable: no pole in the right half plane, and the poles on the imaginary axis are distinct **✓**（临界稳定：右半平面无极点，虚轴上的极点互不重合）
(b) Unstable: no pole in the right half plane, but a repeated pole on the imaginary axis（不稳定：右半平面无极点，但虚轴上存在重极点）
(c) Unstable: at least one pole satisfies $\operatorname{Re}p>0$（不稳定：至少有一个极点实部大于零）
(d) Stable: every pole satisfies $\operatorname{Re}p<0$（稳定：所有极点实部小于零）

> [!success] Answer（答案）
> (a) 临界稳定：右半平面无极点，虚轴极点互异

> [!abstract] 知识点讲解
> 见 6.1 三种稳定性 与 6.3 极点判据速查。
>
> - **极点判据**：极点全在左半平面 → 指数稳定；虚轴上有单根且其余在左半平面 → 临界稳定；虚轴有重根或右半平面有极点 → 不稳定。
> - **时域表现**：虚轴单极点对应常数或等幅振荡项，有界但不趋于零。

> [!example] 解答
> 分解分母：
> $$(j\omega+2)\left((j\omega)^2+4\right)=0\Rightarrow s=-2,\ s=\pm2j.$$
>
> 检查分子是否抵消极点：分子 $(j\omega)^2+j\omega+1$ 在 $s=-2$、$s=\pm2j$ 处均不为零，无抵消。
>
> 检查右半平面：三个极点实部为 $-2$、$0$、$0$，无右半平面极点。
>
> 检查虚轴：$\pm2j$ 都是单根，互不相同。
>
> 分类：临界稳定。选 (a)。


---

## 78. Question 78（第 78 题）｜PDF p. 24 ^q78

An LTI system has（某 LTI 系统的传递函数为）

$$G(j\omega)=\frac{(j\omega)^2+2(j\omega)+8}{(j\omega+1)\left((j\omega)^2+4\right)^2}.$$

Classify the system.（对该系统进行稳定性分类。）

(a) Unstable: at least one pole satisfies $\operatorname{Re}p>0$（不稳定：至少一个极点位于右半平面）
(b) Unstable: no pole in the right half plane, but a repeated pole on the imaginary axis **✓**（不稳定：右半平面无极点，但虚轴上有重极点）
(c) Marginally stable: no pole in the right half plane, and the poles on the imaginary axis are distinct（临界稳定：右半平面无极点，虚轴上极点互异）
(d) Stable: every pole satisfies $\operatorname{Re}p<0$（稳定：所有极点实部小于零）

> [!success] Answer（答案）
> (b) 不稳定：右半平面无极点，但虚轴上有重极点

> [!abstract] 知识点讲解
> 见 6.1 三种稳定性。
>
> - **极点判据**：虚轴上的重极点 → 不稳定。
> - **时域表现**：二重极点 $\pm j\omega_0$ 产生 $t\cos\omega_0t$、$t\sin\omega_0t$，幅度随 $t$ 增长。

> [!example] 解答
> 分解分母：
> $$(j\omega+1)\left((j\omega)^2+4\right)^2=0\Rightarrow s=-1,\ s=\pm2j\ (\text{各二重}).$$
>
> 检查右半平面：无。
>
> 检查虚轴：$\pm2j$ 为二重根。
>
> 判断响应：重根对应
> $$t\cos2t,\quad t\sin2t,$$
> 幅度随 $t$ 增长，无界。
>
> 判为不稳定，选 (b)。


---

## 79. Question 79（第 79 题）｜PDF p. 24 ^q79

Four LTI systems are given by their transfer functions. Which one is BIBO stable?（四个 LTI 系统中哪一个满足 BIBO 稳定性？）

(a) $G(j\omega)=\dfrac{j\omega+7}{(j\omega+1)\left((j\omega)^2-4(j\omega)+9\right)}$（第一个传递函数，含右半平面极点）
(b) $G(j\omega)=\dfrac{1}{j\omega-3}$（第二个传递函数，极点为正实数 $3$）
(c) $G(j\omega)=\dfrac{2(j\omega)+3}{(j\omega+1)(j\omega+2)}$ **✓**（第三个传递函数，极点均位于左半平面）
(d) $G(j\omega)=\dfrac{3}{j\omega(j\omega+2)}$（第四个传递函数，含原点极点）

> [!success] Answer（答案）
> (c)

> [!abstract] 知识点讲解
> 见 6.2 BIBO 稳定。
>
> - **BIBO 判据**（真有理 $G$）：所有极点实部严格小于零。
> - **等价条件**：$\displaystyle\int_{-\infty}^{\infty}|h(t)|dt<\infty$。
> - **虚轴单极点**：对应常数或等幅振荡，不绝对可积，故不 BIBO。

> [!example] 解答
> (a) 的二次因子：
> $$s^2-4s+9=0\Rightarrow s=2\pm j2.236,$$
> 实部为正，不稳定。
>
> (b) 的极点：
> $$s-3=0\Rightarrow s=3>0,$$
> 不稳定。
>
> (c) 的极点：
> $$s=-1,\ s=-2,$$
> 都在左半平面，BIBO 稳定。
>
> (d) 的极点：
> $$s=0,\ s=-2,$$
> 原点极点为虚轴单根，不 BIBO 稳定；有界输入 $H(t)$ 产生斜坡输出。
>
> 选 (c)。


---

## 80. Question 80（第 80 题）｜PDF p. 25 ^q80

A first-order system obeys $\tau\dot{y}=-y+\beta u$ with $\tau=-4\ \mathrm{s}$.（一阶系统服从 $\tau\dot{y}=-y+\beta u$，其中 $\tau=-4\ \mathrm{s}$。）Classify its stability.（判断其稳定性。）

$$
\tau\dot{y}=-y+\beta u,\qquad \tau=-4\ \mathrm{s}
$$

(a) Marginally stable（临界稳定）
(b) Stable and BIBO stable（稳定且 BIBO 稳定）
(c) Cannot be determined without knowing $\beta$（没有 $\beta$ 的数值无法判断）
(d) Unstable **✓**（不稳定）

> [!success] Answer（答案）
> (d) 不稳定

> [!abstract] 知识点讲解
> 见 6.3 极点判据速查。
>
> - **一阶系统**：$\tau\dot y=-y+\beta u\Rightarrow G(j\omega)=\dfrac{\beta}{1+j\omega\tau}$，极点 $s=-\dfrac1{\tau}$。
> - **稳定判据**：$\Re s<0\iff\tau>0$；$\tau<0$ 时极点在右半平面，不稳定。
> - **分子 $\beta$**：只改增益，不改极点位置。

> [!example] 解答
> 写特征方程：
> $$\tau s+1=0.$$
>
> 解极点：
> $$s=-\frac{1}{\tau}.$$
>
> 代入 $\tau=-4$：
> $$s=-\frac{1}{-4}=0.25>0.$$
>
> 自然响应含 $e^{0.25t}$，随时间发散。
>
> 检查 $\beta$：它只改变受迫项比例，不改变极点位置。
>
> 结论不稳定，选 (d)。


---

## 81. Question 81（第 81 题）｜PDF p. 25 ^q81

For the second-order system（对于二阶系统）

$$G(j\omega)=\frac{K\omega_n^2}{(j\omega)^2+2\zeta\omega_n(j\omega)+\omega_n^2}$$

with $\omega_n=5\ \mathrm{rad/s}$ fixed, for which value of $\zeta$ is the unforced response *not* bounded as $t\to\infty$?（固定 $\omega_n=5\ \mathrm{rad/s}$，$\zeta$ 取哪个值时，无输入响应在 $t\to\infty$ 时无界？）

$$
\omega_n=5,\qquad \zeta\in\{1,\ -0.1,\ 0.3,\ 2\}
$$

(a) $\zeta=1$（$\zeta=1$）
(b) $\zeta=-0.1$ **✓**（$\zeta=-0.1$）
(c) $\zeta=0.3$（$\zeta=0.3$）
(d) $\zeta=2$（$\zeta=2$）

> [!success] Answer（答案）
> (b) $\zeta=-0.1$

> [!abstract] 知识点讲解
> 见 5.2 极点与阻尼 与 6.1 三种稳定性。
>
> - **二阶极点**：$p=-\zeta\omega_n\pm j\omega_n\sqrt{1-\zeta^2}$，实部为 $-\zeta\omega_n$。
> - **无界条件**：实部为正，即 $\zeta<0$（$\omega_n>0$）；$\zeta\ge0$ 时响应有界或衰减。

> [!example] 解答
> 对每个 $\zeta$ 算实部 $-\zeta\omega_n$，$\omega_n=5$：
> - $\zeta=1$：$-5$，衰减。
> - $\zeta=-0.1$：$+0.5$，增长。
> - $\zeta=0.3$：$-1.5$，衰减。
> - $\zeta=2$：$-10$，衰减。
>
> 只有 $\zeta=-0.1$ 使实部为正。
>
> 求极点：
> $$p=0.5\pm j5\sqrt{1-(-0.1)^2}=0.5\pm j4.975,$$
> 振幅按 $e^{0.5t}$ 增长。
>
> 选 (b)。


---

## 82. Question 82（第 82 题）｜PDF p. 25 ^q82

For $a\ddot{y}+b\dot{y}+cy=0$ with $a,b,c>0$, which is always true of the solution $y(t)$ as $t\to\infty$?（对于 $a\ddot{y}+b\dot{y}+cy=0$，$a,b,c>0$，关于 $t\to\infty$ 时的解 $y(t)$，哪一项总是成立？）

$$
a\ddot{y}+b\dot{y}+cy=0,\qquad a,b,c>0
$$

(a) $y(t)$ can grow without bound for some positive choices of $a,b,c$（对某些正的 $a,b,c$，解可能无界增长）
(b) $y(t)$ stays bounded but does not necessarily decay to zero（解始终有界，但不一定趋于零）
(c) $y(t)\to0$, regardless of the relative sizes of $a,b,c$ **✓**（无论 $a,b,c$ 的相对大小如何，解都趋于零）
(d) $y(t)\to0$ only if $b^2\ge4ac$ (overdamped or critically damped)（只有 $b^2\ge4ac$ 时，解才趋于零）

> [!success] Answer（答案）
> (c) 无论 $a,b,c$ 的相对大小，均有 $y(t)\to0$

> [!abstract] 知识点讲解
> 见 6.3 极点判据速查 例 4。
>
> - **特征根**：$as^2+bs+c=0\Rightarrow s_{1,2}=\dfrac{-b\pm\sqrt{b^2-4ac}}{2a}$。
> - **实根**：$b^2\ge4ac$ 时两根为负实数（因 $a,b,c>0$ 且 $\sqrt{b^2-4ac}<b$）。
> - **复根**：实部 $-\dfrac b{2a}<0$，振荡衰减。两种情形都有 $y(t)\to0$。

> [!example] 解答
> 写特征根：
> $$s_{1,2}=\frac{-b\pm\sqrt{b^2-4ac}}{2a}.$$
>
> 判别式 $\ge0$ 的情形：因 $ac>0$，$\sqrt{b^2-4ac}<b$，故
> $$-b+\sqrt{b^2-4ac}<0,\qquad -b-\sqrt{b^2-4ac}<0,$$
> 两根均为负实数。
>
> 判别式 $<0$ 的情形：两根共轭，实部
> $$-\frac{b}{2a}<0.$$
>
> 两种情形都有 $y(t)\to0$。
>
> 排除 (d)：复根同样衰减，条件不只是 $b^2\ge4ac$。选 (c)。


---

## 83. Question 83（第 83 题）｜PDF p. 26 ^q83

A system has impulse response $h(t)=3e^{-2t}H(t)$.（某系统的冲激响应为 $h(t)=3e^{-2t}H(t)$。）Compute $\displaystyle\int_{-\infty}^{\infty}|h(t)|\,dt$ and state whether the system is BIBO stable.（计算 $\displaystyle\int_{-\infty}^{\infty}|h(t)|\,dt$，并判断系统是否 BIBO 稳定。）


$$
h(t)=3e^{-2t}H(t)
$$

> [!success] Answer（答案）
> $\displaystyle\int_{-\infty}^{\infty}|h(t)|dt=1.50000$，系统 BIBO 稳定

> [!abstract] 知识点讲解
> 见 6.2 BIBO 稳定。
>
> - **BIBO 充要条件**：$\displaystyle\int_{-\infty}^{\infty}|h(t)|dt<\infty$。
> - **单边指数积分**：$\displaystyle\int_0^\infty Ae^{-at}dt=\dfrac Aa$。

> [!example] 解答
> 由于 $h(t)=3e^{-2t}H(t)$ 在 $t\ge0$ 非负，绝对值可去掉：
> $$\int_{-\infty}^{\infty}|h|dt=\int_0^\infty3e^{-2t}dt.$$
>
> 积分：
> $$\int_0^\infty3e^{-2t}dt=3\left[-\frac{e^{-2t}}{2}\right]_0^\infty=3\cdot\frac12=\frac32.$$
>
> 结果 $1.50000<\infty$。
>
> 判据成立，BIBO 稳定。


---

## 84. Question 84（第 84 题）｜PDF p. 26 ^q84

A system has impulse response $h(t)=H(t)$ (an ideal integrator).（某系统的冲激响应为 $h(t)=H(t)$，即理想积分器。）Classify its pole, its stability, and its BIBO stability.（判断其极点位置、稳定性与 BIBO 稳定性。）

$$
h(t)=H(t)
$$

(a) Pole at $j\omega=0$; marginally stable; BIBO stable（原点极点、临界稳定、BIBO 稳定）
(b) Pole at $j\omega=-1$; stable; BIBO stable（$-1$ 处极点、稳定、BIBO 稳定）
(c) Pole at $j\omega=0$; marginally stable; BIBO unstable **✓**（原点极点、临界稳定、BIBO 不稳定）
(d) No finite poles; the output depends only on the present value of the input（没有有限极点，输出只取决于当前输入）

> [!success] Answer（答案）
> (c) 原点极点；临界稳定；不 BIBO

> [!abstract] 知识点讲解
> 见 6.4 积分器与临界稳定。
>
> - **阶跃变换对**：$H(t)\leftrightarrow\dfrac1{j\omega}+\pi\delta(\omega)$，极点在 $s=0$（虚轴）。
> - **稳定判据**：$h$ 有界但不趋于零 → 临界稳定；$\displaystyle\int|h(t)|dt=\infty$ → 不 BIBO。
> - **反例**：有界输入 $H(t)$ 产生斜坡输出 $tH(t)$。

> [!example] 解答
> 求传递函数：$\mathcal{F}\{H(t)\}=\frac{1}{j\omega}+\pi\delta(\omega)$，极点在 $\omega=0$。
>
> 判断自然响应：$h(t)=H(t)$ 有界，但不趋零，故临界稳定。
>
> 检查绝对可积：
> $$\int_0^\infty1\,dt=\infty,$$
> 不满足 BIBO 条件。
>
> 举例说明：有界输入 $H(t)$ 得到斜坡输出 $tH(t)$，无界。
>
> 选 (c)。


---

## 85. Question 85（第 85 题）｜PDF p. 26 ^q85

Two systems have impulse responses（两个系统的冲激响应分别为）

$$h_A(t)=300e^{-4t}H(t),\qquad h_B(t)=300e^{4t}H(t).$$

Which system is BIBO stable and has a frequency response $G(j\omega)$ that exists (that is, its Fourier transform converges)?（哪个系统既 BIBO 稳定，其频率响应 $G(j\omega)$ 又存在（即傅里叶变换收敛）？）

(a) neither（两个系统都不符合）
(b) A only **✓**（只有系统 A 符合）
(c) both A and B（系统 A 和 B 都符合）
(d) B only（只有系统 B 符合）

> [!success] Answer（答案）
> (b) 只有系统 A

> [!abstract] 知识点讲解
> 见 6.2 BIBO 稳定 与 3.3 存在性。
>
> - **BIBO 充要条件**：$\displaystyle\int_{-\infty}^{\infty}|h(t)|dt<\infty$。
> - **变换对**：$e^{-at}H(t)\leftrightarrow\dfrac1{a+j\omega}$（$a>0$）；$e^{4t}H(t)$ 的收敛域 $\operatorname{Re}s>4$ 不含虚轴，$G(j\omega)$ 不存在。

> [!example] 解答
> 算 A 的绝对值积分：
> $$\int_0^\infty300e^{-4t}dt=300\cdot\frac14=75<\infty,$$
> A 为 BIBO 稳定。
>
> 算 B 的绝对值积分：
> $$\int_0^\infty300e^{4t}dt\to\infty,$$
> B 不 BIBO 稳定。
>
> 判断频率响应：A 的 $G_A(j\omega)=\frac{300}{4+j\omega}$ 存在；B 的积分发散，通常傅里叶变换不存在。
>
> 选 (b)。


