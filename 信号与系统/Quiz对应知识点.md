# 信号与系统知识点笔记

> 配套练习：[[Quiz2]]、[[Quiz3]]。本笔记按课程内容的逻辑顺序整理：先讨论周期信号与基波频率，再建立傅里叶级数、傅里叶变换和频率响应，最后讨论二阶系统、稳定性、拉普拉斯变换、滤波器和调制。Quiz2、Quiz3 中每道题的「知识点讲解」会注明对应的小节编号和名称，可按编号在本笔记中查找。第 12 节专门补充 Quiz 3 涉及、但前面各节没有展开的内容：s 域电路阻抗、斜坡稳态误差、互补滤波器、全通与延迟线、分频器、Bode 斜率读法和增益指标反求。

## 符号约定

| 符号            | 含义                     |
| ------------- | ---------------------- |
| $u(t)$        | 输入信号，或一般信号             |
| $y(t)$        | 输出信号                   |
| $h(t)$        | 冲激响应                   |
| $G(j\omega)$  | 频率响应                   |
| $G(s)$        | 传递函数                   |
| $H(t)$        | 单位阶跃信号                 |
| $\delta(t)$   | 单位冲激信号                 |
| $p_\tau(t)$   | 宽度为 $\tau$（脉宽）、关于原点对称的矩形脉冲 |
| $c_k$         | 复指数傅里叶系数               |
| $a_0,a_k,b_k$ | 三角形式傅里叶系数              |
| $*$           | 卷积                     |
| ROC           | 收敛域                    |

本笔记采用归一化 sinc 函数

$$\operatorname{sinc}(x)=\frac{\sin(\pi x)}{\pi x}.$$

三角形式统一采用

$$u(t)=a_0+\sum_{k=1}^{\infty}\left(a_k\cos k\omega_0t+b_k\sin k\omega_0t\right),$$

因此 $a_0=c_0$。有些教材把常数项写成 $a_0/2$，两种约定的 $a_0$ 相差一倍，查表或代公式前要先确认使用的是哪一种。本笔记统一使用上式。

**与 Quiz 公式表保持一致。** 本笔记的记号、系数定义和常用公式均按 ELEC2302/9302 的 Quiz 2、Quiz 3 公式表书写：傅里叶基函数 $\phi_k(t)=e^{jk\omega_0t}$，系数写成内积 $c_k=\langle u,\phi_k\rangle_P$；频率响应记 $G(j\omega)$，传递函数记 $G(s)$；二阶系统用 $G(j\omega)=\dfrac{K\omega_n^2}{(j\omega)^2+2\zeta\omega_n(j\omega)+\omega_n^2}$ 与 $G(s)=\dfrac{K\omega_n^2}{s^2+2\zeta\omega_ns+\omega_n^2}$，且 $G(0)=K$；拉普拉斯变换记 $U(s)=\mathcal L\{u\}(s)$、$G(s)=\mathcal L\{h\}(s)$、$Y(s)=G(s)U(s)$。第 10 节是按公式表逐条整理的速查。

---

## 0 预备知识

### 0.1 复数与相量

设复数

$$z=x+jy,\qquad x,y\in\mathbb R,\quad j^2=-1.$$

它的模和辐角分别为

$$|z|=\sqrt{x^2+y^2},\qquad \theta=\arg z.$$

写成极坐标形式

$$z=|z|e^{j\theta}.$$

由欧拉公式

$$e^{j\theta}=\cos\theta+j\sin\theta,$$

可以得到

$$\cos\theta=\frac{e^{j\theta}+e^{-j\theta}}{2},\qquad \sin\theta=\frac{e^{j\theta}-e^{-j\theta}}{2j}.$$

这两个式子在傅里叶级数、傅里叶变换和频率响应中反复使用。

复数的加减法用直角坐标方便，乘除法用极坐标方便：

$$z_1z_2=|z_1||z_2|e^{j(\theta_1+\theta_2)},\qquad \frac{z_1}{z_2}=\frac{|z_1|}{|z_2|}e^{j(\theta_1-\theta_2)}.$$

因此两个复数相乘时，模相乘、辐角相加；相除时，模相除、辐角相减。

计算频率响应时，常要把分母化成 $a+jb$ 的形式。注意

$$\frac{1}{j}=-\frac1j=-j,\qquad \frac{1}{j\omega}=-j\frac1\omega.$$

辐角要结合象限判断。若 $z=x+jy$，则

$$\arg z=\begin{cases}
\arctan\left(\dfrac{y}{x}\right), & x>0,\\[6pt]
\arctan\left(\dfrac{y}{x}\right)+\pi, & x<0,\ y\ge0,\\[6pt]
\arctan\left(\dfrac{y}{x}\right)-\pi, & x<0,\ y<0,\\[6pt]
\dfrac{\pi}{2}, & x=0,\ y>0,\\[6pt]
-\dfrac{\pi}{2}, & x=0,\ y<0.
\end{cases}$$

只写 $\arctan(y/x)$ 容易把第二、第三象限的角弄错。

### 0.2 正弦信号的幅度、相位与有效值

正弦信号的一般形式为

$$x(t)=A\cos(\omega t+\varphi).$$

其中 $A>0$ 是峰值，$\omega$ 是角频率，$\varphi$ 是初相位。它也可以写成相量形式

$$x(t)=\operatorname{Re}\left\{Ae^{j\varphi}e^{j\omega t}\right\}.$$

相量 $Ae^{j\varphi}$ 只保留振幅和初相位，省略了 $e^{j\omega t}$ 这个共同因子。做正弦稳态分析时，各支路频率相同，因此可以只比较相量。

若

$$x(t)=a\cos\omega t+b\sin\omega t,$$

则合成后仍为同频率余弦：

$$x(t)=A\cos(\omega t+\varphi),$$

其中

$$A=\sqrt{a^2+b^2},\qquad \varphi=-\arctan\frac{b}{a}.$$

这两个公式可以自己推一遍。把右边的目标形式展开：

$$A\cos(\omega t+\varphi)=A\cos\varphi\cos\omega t-A\sin\varphi\sin\omega t.$$

与 $a\cos\omega t+b\sin\omega t$ 逐项对照，得到

$$a=A\cos\varphi,\qquad b=-A\sin\varphi.$$

两式相除：

$$\frac{b}{a}=-\frac{\sin\varphi}{\cos\varphi}=-\tan\varphi
\quad\Longrightarrow\quad \tan\varphi=-\frac{b}{a},$$

所以 $\varphi=-\arctan\dfrac{b}{a}$。

另一种更直观的记法：看 $(a,b)$ 这个点在坐标平面上的位置。$a$ 控制余弦项，$b$ 控制正弦项；正余弦合成后，相位角的符号与 $b$ 的符号相反。例如 $a>0,\ b<0$ 时，正弦项为负，$-b/a>0$，所以 $\varphi=\arctan(-b/a)$ 是正角，表示波形整体左移、相位超前。

若 $a$ 为负，直接套 $\arctan$ 只能得到主值，需要再按象限加减 $\pi$。这种情况用 $c_1=\dfrac{a-jb}{2}$ 然后取 $\angle c_1$ 更稳妥，因为复数的辐角定义本身已经处理了象限。

正弦信号的均方根值（RMS）为

$$X_{\mathrm{RMS}}=\frac{A}{\sqrt2}.$$

平均功率为

$$P=\frac{A^2}{2}.$$

直流信号 $x(t)=A$ 的 RMS 和平均功率都等于 $A$ 和 $A^2$。峰值与 RMS 不能混用：题目问功率或 RMS 时，正弦的幅值要先除以 $\sqrt2$。

### 0.3 信号的能量与平均功率

信号的能量定义为

$$E=\int_{-\infty}^{\infty}|u(t)|^2dt.$$

平均功率定义为

$$P=\lim_{T\to\infty}\frac{1}{T}\int_{-T/2}^{T/2}|u(t)|^2dt.$$

若 $0<E<\infty$，称为能量信号，此时 $P=0$。若 $0<P<\infty$，称为功率信号，此时 $E=\infty$。周期信号是典型的功率信号，它的平均功率可以在一个周期上计算：

$$P=\frac1{T}\int_{T}|u(t)|^2dt.$$

这两个概念在后面分别对应 Parseval 定理的两种形式：周期信号用平均功率，非周期能量信号用总能量。

---

## 1 周期信号与基波频率

### 1.1 周期信号的定义

若存在正数 $T$，使得对任意时间 $t$ 都有

$$u(t+T)=u(t),$$

则称 $u(t)$ 为周期信号。满足该条件的最小正数称为基波周期，记作 $T$。

基波周期对应的频率和角频率分别为

$$f_0=\frac{1}{T},\qquad \omega_0=\frac{2\pi}{T}.$$

常数信号对任意 $T$ 都满足周期性条件，没有最小正周期，通常不讨论它的基频。只在一个有限时间区间内取非零值的信号不可能是周期信号。

两个周期信号相加，结果不一定是周期信号。设两个信号的周期分别为 $T_1$ 和 $T_2$。若

$$\frac{T_1}{T_2}\in\mathbb Q,$$

则存在公共周期，和信号周期；公共周期的最小值等于 $T_1$ 和 $T_2$ 的最小公倍数。若周期比为无理数，则不存在公共周期。这个判据与下一节用角频率判断周期性的方法等价。

### 1.2 周期、频率与角频率

三个量的关系为

$$T=\frac{1}{f_0}=\frac{2\pi}{\omega_0},\qquad f_0=\frac{\omega_0}{2\pi}.$$

| 量 | 符号 | 单位 | 含义 |
|---|---|---|---|
| 周期 | $T$ | 秒 (s) | 波形重复一次所需时间 |
| 频率 | $f_0$ | 赫兹 (Hz) | 每秒重复的次数 |
| 角频率 | $\omega_0$ | 弧度每秒 (rad/s) | 每秒走过的相位 |

题目给的是 $T$、$f$ 还是 $\omega$，决定了最后一步要不要乘或除以 $2\pi$。频率与角频率之间相差 $2\pi$，这是周期计算中最常见的错误来源。

### 1.3 单个正弦信号的周期

对

$$x(t)=\cos(\omega t+\varphi),$$

周期为

$$T=\frac{2\pi}{|\omega|}.$$

振幅只改变波形的高低，初相位只把波形左右平移，都不影响周期。


例如：

- $\cos(3t)$ 的周期为 $2\pi/3$。
- $\sin(5t+\pi/4)$ 的周期为 $2\pi/5$。
- $\cos(0.2t)$ 的周期为 $2\pi/0.2=10\pi$。

对多个同频率正弦之和，周期仍为这个共同频率对应的周期。

### 1.4 周期信号的常见运算

判断运算后周期怎么变，只需要回答一个问题：**变换后的波形，隔多久原样重复一次？** 下面把常见运算分成四组。

#### 一、只平移、翻转或改变幅度：周期不变

| 运算 | 例子 | 周期 |
|---|---|---|
| 时移 $u(t-t_0)$ | 把波形左右挪一段 | 仍为 $T$ |
| 反转 $u(-t)$ | 把波形左右翻面 | 仍为 $T$ |
| 乘常数 $Au(t)$ | 把波形拉高或压低 | 仍为 $T$ |
| 加直流 $u(t)+B$ | 把波形整体上移或下移 | 仍为 $T$ |
| 以上组合 $Au(t-t_0)+B$ | 平移、缩放、上移一起做 | 仍为 $T$ |

原因很直接：这些操作都没有改变波形「多久重复一次」的节奏。例如 $u(t)=\cos 3t$ 的周期为 $2\pi/3$，那么 $5u(t-1)+2$ 的周期仍是 $2\pi/3$。

#### 二、时间尺度 $u(at)$：周期变为 $T/\lvert a\rvert$

时间乘上 $a$ 相当于把时间轴压缩或拉伸。

证明：令 $T'=T/\lvert a\rvert$，则

$$u\left(a\left(t+T'\right)\right)=u\left(at\pm T\right)=u(at),$$

所以 $T/\lvert a\rvert$ 确实是一个周期。

- $a>1$：时间被压缩，波形变化变快，周期变短。例如 $T=4$ 时，$u(2t)$ 的周期为 $2$。
- $0<a<1$：时间被拉伸，波形变化变慢，周期变长。例如 $T=4$ 时，$u(t/2)$ 的周期为 $8$。
- $a<0$：还附带时间反转，周期取绝对值。例如 $T=4$ 时，$u(-3t)$ 的周期为 $4/3$。

注意 $u(at)$ 是时间轴上的缩放，与乘常数 $Au(t)$ 不同：后者只改变幅度，不改变周期。

#### 三、多个周期信号相加或相乘

设 $u_1(t)$ 的周期为 $T_1$，$u_2(t)$ 的周期为 $T_2$。

要使组合后的信号还是周期信号，需要找到一个 $T$，满足：

$$T=mT_1=nT_2,\qquad m,n\text{ 为正整数}.$$

这要求 $T_1/T_2$ 为有理数。满足条件时，最小的公共周期是 $T_1$ 和 $T_2$ 的**最小公倍数**。

但要注意：最小公倍数只是「一定能保证两个分量都重复」的周期，它不一定是组合后的最终信号的基波周期。如果相加或相乘后波形出现了新的对称性，真正的基波周期可能比它小。


**例 1**　$u_1=\cos t$（$T_1=2\pi$），$u_2=\cos 2t$（$T_2=\pi$）。

最小公倍数为 $2\pi$。因为 $\cos(t+\pi)=-\cos t$，所以 $T=\pi$ 不是周期，$2\pi$ 就是基波周期。

**例 2**　$u_1=\sin t$，$u_2=\cos t$，两者周期都是 $2\pi$。

相加 $\sin t+\cos t=\sqrt2\cos(t-\pi/4)$，周期仍为 $2\pi$。

相乘

$$\sin t\cos t=\frac12\sin2t,$$

周期变成 $\pi$，是最小公倍数 $2\pi$ 的一半。两个因子各自的周期都是 $2\pi$，但乘积化简后只剩 $\sin 2t$，它的周期只有 $\pi$。

频率比为无理数时，和与积一般不是周期信号，例如 $\cos t+\cos(\sqrt2\,t)$。这个判据的完整讨论和多个正弦叠加求基频的步骤见 1.5 节。

所以做题时推荐的做法是：先把和或积**化简**（用积化和差、和差化积或三角恒等式），再直接读周期；不要一上来就套最小公倍数。

#### 四、平方与取绝对值：周期不会变长，可能变短

若 $u(t+T)=u(t)$，那么显然

$$u^2(t+T)=u^2(t),\qquad \lvert u(t+T)\rvert=\lvert u(t)\rvert.$$

所以原来的周期 $T$ 仍然是平方后的信号和绝对值信号的周期，基波周期只可能等于 $T$ 或比 $T$ 短（常见的是缩到 $T/2$），不会变长。

**会变短的例子**：

- $u(t)=\sin t$，周期 $2\pi$。由 $\sin^2t=\dfrac{1-\cos2t}{2}$，平方后的周期为 $\pi$。
- $u(t)=\sin t$，取绝对值 $\lvert\sin t\rvert$ 的周期为 $\pi$，这就是全波整流。
- 方波 $u(t)=\pm1$，周期 $T$。取绝对值后恒为 $1$，是常数，没有基波周期。

**不变短的例子**：$u(t)=1+\cos t$ 的周期为 $2\pi$，且始终非负。平方后

$$u^2(t)=\frac32+2\cos t+\frac12\cos2t,$$

展开后仍含 $\cos t$ 项，所以周期仍是 $2\pi$，没有缩到 $\pi$。

判断技巧：平方或取绝对值后，若波形把负半周翻到正半周，通常会出现「一半周期就重复」的情况；若原波形本身不再变号，周期往往保持不变。


### 1.5 多个正弦叠加的周期与基频

#### 周期存在的条件

设

$$u(t)=A_0+\sum_{i=1}^{N}A_i\cos(\omega_it+\varphi_i).$$

要让这个和成为周期信号，需要存在一个公共周期 $T$，使每个非零频率分量都同时完成整数个周期：

$$\omega_iT=2\pi n_i,\qquad n_i\in\mathbb Z.$$

把任意两个分量的条件相除，立刻得到

$$\frac{\omega_i}{\omega_j}=\frac{n_i}{n_j}\in\mathbb Q.$$

所以判断周期性的标准只有一条：**任意两个非零频率之比都是有理数**。只要有一对频率之比为无理数，就不存在公共周期，信号不是周期信号（有时称为准周期信号）。

直流项 $\omega=0$ 不参与这个条件，它只改变波形的上下位置，不影响周期。

#### 求基频的步骤

1. 列出所有非零角频率，直流项 $\omega=0$ 不参与计算。
2. 把所有频率写成整数或分数，并通分到相同的分母 $D$。
3. 对通分后的分子 $n_1,n_2,\dots,n_N$ 求最大公约数。
4. 基波角频率为

$$\omega_0=\frac{\gcd(n_1,n_2,\dots,n_N)}{D}.$$

5. 基波周期为

$$T=\frac{2\pi}{\omega_0}.$$

若所有频率本来就是整数，则 $D=1$，直接对整数求最大公约数。

#### 例题

**例 1（分数频率）**　$u(t)=\cos\left(\frac23t+\frac{\pi}{6}\right)+\sin\left(\frac45t+\frac{\pi}{4}\right)$。

非零频率为 $\frac23$ 和 $\frac45$。通分：

$$\frac23=\frac{10}{15},\qquad \frac45=\frac{12}{15}.$$

分子 $\gcd(10,12)=2$，所以

$$\omega_0=\frac{2}{15}\ \mathrm{rad/s},\qquad T=\frac{2\pi}{2/15}=15\pi.$$

频率比

$$\frac{2/3}{4/5}=\frac56$$

为有理数，信号确实周期。两个分量分别是基频的 $5$ 次和 $6$ 次谐波。

**例 2（三个频率加直流）**　$u(t)=2+7\cos\left(\frac12t+\theta_1\right)+3\cos\left(\frac23t+\theta_2\right)+5\cos\left(\frac76t+\theta_3\right)$。

直流项 $2$ 不影响周期。非零频率通分到分母 $6$：

$$\frac12=\frac36,\qquad \frac23=\frac46,\qquad \frac76=\frac76.$$

分子 $\gcd(3,4,7)=1$，所以

$$\omega_0=\frac16\ \mathrm{rad/s},\qquad T=12\pi.$$

**例 3（频率比无理，信号非周期）**　$u(t)=\cos(3t)+\sin(\sqrt5\,t)$。

频率比为

$$\frac{3}{\sqrt5},$$

是无理数。若存在公共周期 $T$，则需同时满足

$$3T=2\pi m,\qquad \sqrt5T=2\pi n,$$

两式相除得

$$\frac{3}{\sqrt5}=\frac mn,$$

左端无理、右端有理，矛盾。因此该信号不是周期信号。

**例 4（整数频率）**

- $u(t)=\cos(2t)+\cos(3t)$：$\gcd(2,3)=1$，所以 $\omega_0=1\ \mathrm{rad/s}$，$T=2\pi$。
- $u(t)=\sin(4t)+\cos(6t)$：$\gcd(4,6)=2$，所以 $\omega_0=2\ \mathrm{rad/s}$，$T=\pi$。两个分量分别是基频的 $2$ 次和 $3$ 次谐波。

如果信号不是直接由正弦相加得到，例如含平方、绝对值或乘积，先用 1.4 节的方法化简成若干正弦之和，再按本节的方法求基频。


---

## 2 傅里叶级数

### 2.1 基本思想与正交函数集

周期信号在每一个周期内重复，因此可以用一组同样以 $T$ 为周期的基本函数来表示。


#### 基函数与谐波

最方便的基本函数是复指数

$$\phi_k(t)=e^{jk\omega_0t},\qquad \omega_0=\frac{2\pi}{T},\quad k\in\mathbb Z.$$

这些函数的频率都是基频的整数倍。

频率为 $k\omega_0$ 的分量称为**第 $k$ 次谐波**：$k=\pm1$ 为基波，$|k|\ge2$ 为高次谐波，$k=0$ 为直流。

这组函数在周期平方可积函数空间中完备。工程中常见的方波、三角波、锯齿波和整流波都满足 Dirichlet 条件，可以展开为傅里叶级数。

Dirichlet 条件是一组**充分条件**，用来保证傅里叶级数在每个点都收敛到信号本身（间断点处收敛到左右极限的平均值）。它有三条：

**一、在一个周期内绝对可积。**

$$\int_T\lvert u(t)\rvert dt<\infty.$$

这条排除的是「面积无穷大」的尖峰。例如 $u(t)=1/t$（$t\ne0$）在原点附近面积发散，傅里叶系数会算成无穷大，级数没有意义。

**二、一个周期内极值点有限。** 极值点指局部最大值和最小值。这条排除的是「无限次来回振荡」的波形，例如

$$u(t)=\sin\frac1t$$

在原点附近振荡次数无限，傅里叶系数虽然可能收敛，但级数不保证在每个点都收敛到原值。

**三、一个周期内第一类间断点有限。** 

判断一个间断点属于哪一类，看它左右两侧的极限。

- **第一类间断点**：左右极限都存在且有限。例如方波的跳变沿，左侧趋于 $-A$，右侧趋于 $+A$，两个极限都是有限值；再比如 $u(t)=\sin t/t$ 在 $t=0$ 处，左右极限都等于 $1$。
- **第二类间断点**：至少有一侧的极限不存在或为无穷大。例如 $u(t)=1/\sqrt{\lvert t\rvert}$ 在 $t\to0$ 时趋向 $+\infty$，属于第二类。

Dirichlet 的第三条要求：一个周期内第一类间断点的个数有限。像 $u(t)=1/\sqrt{\lvert t\rvert}$ 这样的函数，虽然绝对可积（在 $[-1,1]$ 上的积分等于 $4$），但因为有第二类间断点，不满足 Dirichlet 条件，它的傅里叶级数在 $t=0$ 处不能收敛到有限值。这个例子说明：绝对可积只是 Dirichlet 条件的第一条，两者不能互相代替。


满足这三条时，傅里叶级数在每个点都收敛到确定的值。这里的「收敛」可以这样理解。

实际计算时，不可能把无穷多项一次加完，只能取前若干项求和，得到原信号的一个近似波形。取到第 $N$ 次谐波为止的部分和记作

$$u_N(t)=\sum_{k=-N}^{N}c_ke^{jk\omega_0t}.$$

$N=1$ 时只保留 $k=-1,0,1$ 三项，也就是直流和基波；$N$ 越大，加入的高次谐波越多，近似波形越接近原信号。「项数加到无穷」就是令 $N\to\infty$，看近似波形在这个极限下是否稳定到某个确定的值。

若每个固定点 $t$ 都有这个极限，就说级数在该点收敛，且

$$\lim_{N\to\infty}u_N(t)=u(t).$$

分两种点来看：

- **连续点**：极限值就是原信号在该点的值 $u(t)$。
- **跳变点**：左右极限不相等，极限值取两者的平均值。以方波为例，它在某点从 $-A$ 突然跳到 $+A$，跳变点的极限值为 $\dfrac{(-A)+(+A)}{2}=0$，正好落在跳变的正中间。

另外，在跳变附近，即使 $N$ 取得很大，近似波形 $u_N(t)$ 也会冲出原波形的范围，最大超出量约为跳变幅度的 $9\%$。增大 $N$ 只会让这段过冲变窄，不会让它变矮。这就是 Gibbs 现象，展开在 2.10 节。

工程中遇到的方波、三角波、锯齿波和整流波都满足这三条，平时做题不需要逐条检查。

### 2.2 复指数形式

周期为 $T$、基频为 $\omega_0=2\pi/T$ 的信号可以写成

$$u(t)=\sum_{k=-\infty}^{\infty}c_ke^{jk\omega_0t}.$$

系数由下式给出：

$$c_k=\frac{1}{T}\int_{0}^{T}u(t)e^{-jk\omega_0t}dt=\langle u,\phi_k\rangle_P,\qquad \phi_k(t)=e^{jk\omega_0t}.$$

积分区间可以取任意一个完整周期，例如 $[0,T]$ 或 $[-T/2,T/2]$。

几个基本性质：

- $c_0$ 是信号在一个周期内的平均值，也就是直流分量。
- $c_k$ 一般为复数。$|c_k|$ 是第 $k$ 次谐波的幅度，$\angle c_k$ 是它的相位。
- 对实信号，$c_{-k}=\overline{c_k}$。负频率项与正频率项成共轭对，合起来构成实余弦。
- 傅里叶系数描述的是信号的整体频率结构，与积分区间的起点无关。

其中 $c_0$ 可以直接在系数公式中令 $k=0$ 得到：

$$c_0=\frac{1}{T}\int_T u(t)\,dt.$$

**例**　$u(t)=\cos\omega_0t$。

由欧拉公式

$$\cos\omega_0t=\frac12e^{j\omega_0t}+\frac12e^{-j\omega_0t},$$

直接读出

$$c_1=c_{-1}=\frac12,$$

其余系数为零。

### 2.3 三角形式与系数换算

三角形式为

$$u(t)=a_0+\sum_{k=1}^{\infty}\left(a_k\cos k\omega_0t+b_k\sin k\omega_0t\right).$$

其中

$$a_0=c_0=\frac1{T}\int_{0}^{T}u(t)dt,$$

$$a_k=2\operatorname{Re}c_k=\frac{2}{T}\int_{0}^{T}u(t)\cos(k\omega_0t)\,dt,$$

$$b_k=-2\operatorname{Im}c_k=\frac{2}{T}\int_{0}^{T}u(t)\sin(k\omega_0t)\,dt.$$

#### 与复系数的换算

由欧拉公式

$$\cos k\omega_0t=\frac{e^{jk\omega_0t}+e^{-jk\omega_0t}}{2},\qquad \sin k\omega_0t=\frac{e^{jk\omega_0t}-e^{-jk\omega_0t}}{2j},$$

把三角形式按 $e^{jk\omega_0t}$ 和 $e^{-jk\omega_0t}$ 合并，得

$$c_k=\frac{a_k-jb_k}{2},\qquad c_{-k}=\frac{a_k+jb_k}{2}=\overline{c_k}\qquad(k\ge1).$$

反过来，

$$a_k=2\operatorname{Re}c_k,\qquad b_k=-2\operatorname{Im}c_k\qquad(k\ge1).$$

直流项满足

$$a_0=c_0.$$

注意 $a_0$ 不带因子 $2$，因为直流项在复指数形式中只有 $k=0$ 一项，没有正负频率配对。

#### 幅度相位形式

第 $k$ 次谐波可以写成

$$a_k\cos k\omega_0t+b_k\sin k\omega_0t=A_k\cos(k\omega_0t+\varphi_k),$$

其中

$$A_k=\sqrt{a_k^2+b_k^2}=2|c_k|,\qquad \varphi_k=-\arctan\frac{b_k}{a_k}.$$

$A_k$ 是单边幅度谱的谱线高度。双边幅度谱的谱线高度为 $|c_k|=A_k/2$。

**例**　$u(t)=5+4\cos3t-2\sin3t$。

按上面的约定，

$$a_0=5,\qquad a_1=4,\qquad b_1=-2.$$

先处理基波 $4\cos3t-2\sin3t$，把它合并成一条余弦。两个系数的平方和开根号就是合成后的幅度：

$$A_1=\sqrt{4^2+(-2)^2}=2\sqrt5.$$

把这个幅度提出来，剩下的部分就是某个角的余弦和正弦：

$$4\cos3t-2\sin3t=2\sqrt5\left(\frac{2}{\sqrt5}\cos3t-\frac{1}{\sqrt5}\sin3t\right),$$

也就是

$$\cos\varphi_1=\frac{2}{\sqrt5},\qquad \sin\varphi_1=\frac{1}{\sqrt5}.$$

因为它们都为正，$\varphi_1$ 在第一象限，由

$$\tan\varphi_1=\frac{1}{2}$$

得 $\varphi_1\approx26.57^\circ$。代回余弦的加法公式，

$$\cos(3t+26.57^\circ)=\frac{2}{\sqrt5}\cos3t-\frac{1}{\sqrt5}\sin3t,$$

于是

$$4\cos3t-2\sin3t=2\sqrt5\cos(3t+26.57^\circ).$$

对照系数可以直接读出基波幅度 $2\sqrt5$、初相位 $26.57^\circ$。

完整的信号为

$$u(t)=5+2\sqrt5\cos(3t+26.57^\circ).$$

有些教材把三角形式写成

$$u(t)=\frac{a_0}{2}+\sum_{k=1}^{\infty}\left(a_k\cos k\omega_0t+b_k\sin k\omega_0t\right).$$

在这种约定下 $a_0=2c_0$。两种写法只差常数项的定义，不能混用。

### 2.4 频谱与谱线

#### 频谱的定义

频谱用来描述一个信号由哪些频率成分组成，以及每个成分的幅度和相位。它通常画成两张图：

- **幅度谱**：横轴为频率 $\omega$，纵轴为该频率成分的幅度。
- **相位谱**：横轴为频率 $\omega$，纵轴为该频率成分的相位。

对周期为 $T$ 的信号，频率成分只出现在基频的整数倍处：

$$\omega=k\omega_0,\qquad \omega_0=\frac{2\pi}{T},\quad k=0,\pm1,\pm2,\dots$$

因此频谱是一组离散的竖线，称为**线谱**，每根竖线对应一个谐波。复指数形式下，第 $k$ 根谱线的位置是 $k\omega_0$，高度是 $|c_k|$，相位是 $\angle c_k$。

#### 画频谱的步骤

1. 确定周期 $T$ 和基频 $\omega_0=2\pi/T$，在横轴上标出谱线可能出现的位置 $k\omega_0$。
2. 用积分或查表求出复系数 $c_k$。
3. 计算每根谱线的幅度 $|c_k|$ 和相位 $\angle c_k$。对实信号，利用共轭对称只算 $k\ge0$，负频率按 $|c_{-k}|=|c_k|$、$\angle c_{-k}=-\angle c_k$ 补上。
4. 画双边谱：在每个 $\omega=k\omega_0$ 处画一条竖线，幅度谱的高度为 $|c_k|$，相位谱的高度为 $\angle c_k$；$k=0$ 处的谱线对应直流。
5. 若需要单边谱，保留 $\omega=0$ 处高度为 $|c_0|$ 的直流谱线，把 $k\ge1$ 的谱线高度改为 $2|c_k|$，相位仍为 $\angle c_k$，负频率部分不画。
6. 标注横纵轴的含义与单位，并检查实信号的双边谱是否满足幅度偶对称、相位奇对称。

**例**　$u(t)=5+4\cos3t-2\sin3t$。

周期为 $T=2\pi/3$，基频为 $\omega_0=3$，谱线只出现在 $\omega=0,\pm3$ 三处。由 2.3 节的计算，

$$c_0=5,\qquad c_1=2+j,\qquad c_{-1}=2-j.$$

三根谱线的幅度和相位为

$$|c_0|=5,\quad \angle c_0=0;\qquad |c_{\pm1}|=\sqrt5\approx2.236,\quad \angle c_1\approx26.57^\circ,\quad \angle c_{-1}\approx-26.57^\circ.$$

双边幅度谱在 $\omega=0$ 处有一条高度为 $5$ 的谱线，在 $\omega=\pm3$ 处各有一条高度约为 $2.236$ 的谱线，关于 $\omega=0$ 对称；

相位谱在 $\omega=0$ 处为 $0^\circ$，在 $\omega=3$ 处为 $+26.57^\circ$，在 $\omega=-3$ 处为 $-26.57^\circ$，关于 $\omega=0$ 奇对称。

若画单边幅度谱，则 $\omega=0$ 处高度为 $5$，$\omega=3$ 处高度为 $2\sqrt5\approx4.472$，相位为 $26.57^\circ$。

#### 基本规律

- 谱线位置为 $\omega=k\omega_0$，相邻谱线间隔为 $\omega_0=2\pi/T$。
- 双边谱在 $\pm\omega_0$ 处各有一条高度为 $|c_1|$ 的谱线。对 $\cos\omega_0t$，$|c_{\pm1}|=1/2$。
- 单边幅度谱把正负频率两条谱线合并，高度为 $2|c_1|=1$。
- 波形越平滑，高频分量衰减越快。方波的谱线按 $1/k$ 衰减，三角波按 $1/k^2$ 衰减。
- 周期 $T$ 越大，$\omega_0$ 越小，谱线越密。$T\to\infty$ 时，谱线间隔趋于零，离散谱过渡为连续谱。
- 周期信号的频谱是线谱，非周期信号的频谱是连续谱。这个区别是傅里叶级数与傅里叶变换的分界。

### 2.5 双边谱与负频率

对实信号，

$$c_{-k}=\overline{c_k}.$$

因此

$$|c_{-k}|=|c_k|,\qquad \angle c_{-k}=-\angle c_k.$$

双边幅度谱关于 $\omega=0$ 偶对称，双边相位谱关于 $\omega=0$ 奇对称。

正负频率两项合起来为

$$c_ke^{jk\omega_0t}+c_{-k}e^{-jk\omega_0t}=2|c_k|\cos(k\omega_0t+\angle c_k).$$

负频率是复指数表示中的配对项，不对应另一个独立的物理振动。计算第 $k$ 次谐波的平均功率时，要把 $k$ 与 $-k$ 两项相加：

$$P_k=|c_k|^2+|c_{-k}|^2=2|c_k|^2\qquad(k\ge1).$$

直流功率为 $|c_0|^2$。

**例**　某实信号的 $c_1=2-3j$。

由共轭对称，

$$c_{-1}=2+3j.$$

两项合成的实信号为

$$2|c_1|\cos(t+\angle c_1)=2\sqrt{13}\cos\left(t-\arctan\frac32\right).$$

其中 $|c_1|=\sqrt{13}$，$\angle c_1=-\arctan(3/2)$。

### 2.6 对称性

先写出三角形式的傅里叶级数：

$$u(t)=a_0+\sum_{k=1}^{\infty}\left(a_k\cos k\omega_0t+b_k\sin k\omega_0t\right).$$

等号右边有三种项：常数 $a_0$、余弦项 $a_k\cos k\omega_0t$、正弦项 $b_k\sin k\omega_0t$。其中常数和余弦项是偶函数，正弦项是奇函数。一个信号是偶函数还是奇函数，就决定了哪一类项必须从级数里去掉。

以下结论均针对实信号。

**公式表对照。** 把公式表中的性质、线性与时移与上面的对称性结论放在一起：

| 情形 | 系数关系 |
|---|---|
| $u$ 实 | $c_{-k}=\overline{c_k}$ |
| $u$ 偶 | $b_k=0$ |
| $u$ 奇 | $a_0=a_k=0$ |
| 线性 $\alpha u_1+\beta u_2$ | $\alpha c_{1,k}+\beta c_{2,k}$ |
| 时移 $u(t-t_0)$ | $e^{-jk\omega_0t_0}c_k$ |
| Parseval | $P(u)=\dfrac1T\displaystyle\int_0^T|u(t)|^2dt=\sum_{k=-\infty}^{\infty}|c_k|^2$ |

#### 偶函数

若 $u(-t)=u(t)$。右边唯一的奇函数部分是正弦项，它无法被常数项和余弦项抵消，所以每一项的系数都必须为零：

$$b_k=0\qquad(k\ge1).$$

偶信号的级数只剩常数和余弦项：

$$u(t)=a_0+\sum_{k=1}^{\infty}a_k\cos k\omega_0t.$$

换成复系数，由 $c_k=\dfrac{a_k-jb_k}{2}$ 且 $b_k=0$，得 $c_k=\dfrac{a_k}{2}$，为实数，并且 $c_{-k}=c_k$。

#### 奇函数

若 $u(-t)=-u(t)$。常数项和所有余弦项都是偶函数，必须全部去掉：

$$a_0=0,\qquad a_k=0\qquad(k\ge1).$$

奇信号的级数只剩正弦项：

$$u(t)=\sum_{k=1}^{\infty}b_k\sin k\omega_0t.$$

换成复系数，由 $c_k=\dfrac{a_k-jb_k}{2}$ 且 $a_k=0$，得 $c_k=\dfrac{-jb_k}{2}$，为纯虚数，并且 $c_{-k}=-c_k$。

从积分角度看，得到的结论完全一样：偶函数乘以正弦得到奇函数，在对称区间积分为零，所以 $b_k=0$；奇函数乘以余弦得到奇函数，积分为零，所以 $a_k=0$；常数项是奇函数在一个对称周期上的平均值，也为零。

#### 半波对称与半波反对称

半波对称指

$$u\left(t+\frac{T}{2}\right)=u(t).$$

半波反对称指

$$u\left(t+\frac{T}{2}\right)=-u(t).$$

两者都描述波形在半个周期后的重复或反相。把复系数积分拆成前后两半，可以统一得到

$$c_k=\frac{1\pm(-1)^k}{T}\int_0^{T/2}u(\tau)e^{-jk\omega_0\tau}d\tau,$$

其中正号对应半波对称，负号对应半波反对称。

- 半波对称：$1+(-1)^k$ 在 $k$ 为奇数时为零，所以只有偶次谐波，包括直流。
- 半波反对称：$1-(-1)^k$ 在 $k$ 为偶数时为零，所以只有奇次谐波，直流为零。

这里要区分两件事：半波反对称只说明偶次谐波为零，并不能推出余弦系数 $a_k$ 为零。若信号同时是奇函数，才有 $a_k=0$，只剩奇次正弦；若信号同时是偶函数，才有 $b_k=0$，只剩奇次余弦。一个半波反对称信号若既不是奇函数也不是偶函数，则奇次谐波中正弦和余弦项都可能存在。

例如，方波

$$u(t)=\begin{cases}A,&0<t<T/2,\\-A,&-T/2<t<0\end{cases}$$

同时是奇函数和半波反对称，因此只含奇次正弦项。

若把方波在时间上平移 $T/4$，它仍然是半波反对称，但不再是奇函数或偶函数，此时奇次谐波中会同时出现正弦和余弦项。

#### 对称性小结

| 时域性质 | 三角形式 | 复系数 |
|---|---|---|
| 偶函数 | $b_k=0$，只含余弦 | $c_k$ 为实数，$c_{-k}=c_k$ |
| 奇函数 | $a_k=0$，$a_0=0$，只含正弦 | $c_k$ 为纯虚数，$c_{-k}=-c_k$ |
| 半波对称 $u(t+T/2)=u(t)$ | 只含偶次谐波 | 奇数 $k$ 的 $c_k=0$ |
| 半波反对称 $u(t+T/2)=-u(t)$ | 只含奇次谐波 | 偶数 $k$ 的 $c_k=0$ |
| 偶函数 + 半波反对称 | 只含奇次余弦 | 偶数 $k$ 为零 |
| 奇函数 + 半波反对称 | 只含奇次正弦 | 偶数 $k$ 为零 |

#### 2.6.1 奇偶函数的运算规则

| 运算 | 结果 |
|---|---|
| 奇函数 ± 奇函数 | 奇函数 |
| 偶函数 ± 偶函数 | 偶函数 |
| 奇函数 ± 偶函数 | 一般既非奇也非偶 |
| 奇函数 × 奇函数 | 偶函数 |
| 偶函数 × 偶函数 | 偶函数 |
| 奇函数 × 偶函数 | 奇函数 |

这些规则用来判断被积函数的奇偶性。


#### 2.6.2 半波对称与半波反对称的推导

两种情况的推导思路相同：从复系数定义出发，把积分区间拆成前后两半，后半段换元，再代入各自的对称条件。

##### 半波反对称

设 $u(t+T/2)=-u(t)$。复系数为

$$c_k=\frac1T\int_0^Tu(t)e^{-jk\omega_0t}dt.$$

把积分区间拆成前后两半：

$$c_k=\frac1T\left[\int_0^{T/2}u(t)e^{-jk\omega_0t}dt+\int_{T/2}^{T}u(t)e^{-jk\omega_0t}dt\right].$$

后半段令 $t=\tau+T/2$，则 $dt=d\tau$，$\tau$ 从 $0$ 到 $T/2$，并利用 $u(\tau+T/2)=-u(\tau)$：

$$\begin{aligned}
\int_{T/2}^{T}u(t)e^{-jk\omega_0t}dt
&=\int_0^{T/2}u\left(\tau+\frac{T}{2}\right)e^{-jk\omega_0\left(\tau+\frac{T}{2}\right)}d\tau\\
&=\int_0^{T/2}\left[-u(\tau)\right]e^{-jk\omega_0\tau}\cdot(-1)^k d\tau\\
&=-(-1)^k\int_0^{T/2}u(\tau)e^{-jk\omega_0\tau}d\tau.
\end{aligned}$$

其中用到 $e^{-jk\omega_0T/2}=e^{-jk\pi}=(-1)^k$。代回 $c_k$：

$$c_k=\frac1T\left[1-(-1)^k\right]\int_0^{T/2}u(t)e^{-jk\omega_0t}dt.$$

因为

$$1-(-1)^k=\begin{cases}0,&k\text{ 为偶数},\\2,&k\text{ 为奇数},\end{cases}$$

所以偶数 $k$（包括直流 $k=0$）的系数为零，只剩奇次谐波。

##### 半波对称

设 $u(t+T/2)=u(t)$，推导过程相同，只是后半段代入的符号不同：

$$\begin{aligned}
\int_{T/2}^{T}u(t)e^{-jk\omega_0t}dt
&=\int_0^{T/2}u\left(\tau+\frac{T}{2}\right)e^{-jk\omega_0\left(\tau+\frac{T}{2}\right)}d\tau\\
&=\int_0^{T/2}u(\tau)e^{-jk\omega_0\tau}\cdot(-1)^k d\tau\\
&=(-1)^k\int_0^{T/2}u(\tau)e^{-jk\omega_0\tau}d\tau.
\end{aligned}$$

代回 $c_k$：

$$c_k=\frac1T\left[1+(-1)^k\right]\int_0^{T/2}u(t)e^{-jk\omega_0t}dt.$$

因为

$$1+(-1)^k=\begin{cases}2,&k\text{ 为偶数},\\0,&k\text{ 为奇数},\end{cases}$$

所以奇数 $k$ 的系数为零，只剩偶次谐波，直流分量一般不为零。

### 2.7 正交投影与最佳逼近

#### 内积与范数

把周期为 $T$ 的复信号看作向量，定义内积（公式表写法 $c_k=\langle u,\phi_k\rangle_P$ 中的 $\langle\cdot,\cdot\rangle_P$ 即此内积）

$$\langle u,v\rangle_P=\frac1{T}\int_{0}^{T}u(t)v^*(t)dt.$$

其中 $v^*$ 表示复共轭。内积的作用是衡量两个信号有多相似。为了看清这个定义，先从普通的向量点积说起。

三维向量 $\mathbf a=(a_1,a_2,a_3)$ 和 $\mathbf b=(b_1,b_2,b_3)$ 的点积为

$$\mathbf a\cdot\mathbf b=a_1b_1+a_2b_2+a_3b_3.$$

它把同一位置的两个分量相乘再相加，结果越大，两个向量的方向越接近。


令 $v=u$，自内积为

$$\langle u,u\rangle_P=\frac1T\int_T|u(t)|^2dt,$$

它非负，且 $\langle u,u\rangle_P=0$ 当且仅当 $u$ 在一个周期内几乎处处为零。

由这个内积诱导的范数为

$$\|u\|=\sqrt{\langle u,u\rangle_P}=\sqrt{\frac1T\int_T|u(t)|^2dt}.$$

$\|u\|$ 是信号向量的长度，它的平方

$$\|u\|^2=\langle u,u\rangle_P=\frac1T\int_T|u(t)|^2dt$$

就是前面我们所学习的信号的平均功率 $P$，即 $\|u\|$ 的平方是平均功率，$\|u\|$ 本身是功率的平方根（有效值）。所以后面统一使用范数记号：$\|u\|^2$ 表示总平均功率，$\|e\|^2$ 表示误差的平均功率，不要把它和能量 $\int|u|^2dt$ 混淆。


**例**　$u(t)=\cos t$，$v(t)=\cos t$，周期 $T=2\pi$。

$$\langle u,v\rangle_P=\frac1{2\pi}\int_0^{2\pi}\cos^2t\,dt=\frac12,$$

即 $\cos t$ 的平均功率为 $1/2$。若换成 $u(t)=\cos t$、$v(t)=\sin t$，

$$\langle u,v\rangle_P=\frac1{2\pi}\int_0^{2\pi}\cos t\sin t\,dt=0.$$

这说明两个信号没有共同成分。**内积为零时，称这两个信号正交**，对应向量几何里的「互相垂直」。

#### 用一个基函数逼近信号

内积衡量两个信号有多相似。这里回答一个自然的问题：如果只允许用某个波形 $\phi(t)$ 的倍数 $c\phi(t)$ 来近似 $u(t)$，$c$ 应取多少？

这件事有两个用途。

其一，它给出傅里叶系数的几何解释：$c_k$ 就是把信号投影到第 $k$ 个谐波上得到的最佳系数。

其二，它解释傅里叶级数为什么这样取系数。完整展开有无限多项，实际系统（信道、放大器、采样存储）只能保留有限个谐波，例如 $\omega_0$ 到 $N\omega_0$ 之间的部分。若保留的谐波集合为 $S$，近似写成

$$u(t)\approx\sum_{k\in S}c_k\phi_k(t),$$

则每一项的最佳系数仍然是各自的投影系数

$$c_k=\frac{\langle u,\phi_k\rangle_P}{\langle\phi_k,\phi_k\rangle_P}.$$

保留哪些谐波由带宽或指标决定，每个保留谐波的幅度和相位由投影决定，丢弃部分的总功率就是近似误差功率。

**几何图像：为什么最优时残差垂直于 $\phi$。**

先把「垂直」说清楚。两个信号的内积为零（$\langle e,\phi\rangle_P=0$）时称它们正交，它的几何含义就是「垂直」，这是普通向量点积为零即垂直在信号上的推广。

「残差」就是误差 $e=u-c\phi$，是近似值与原信号之间的差。

现在设想 $\phi$ 是平面上的一条直线，直线上每一点都形如 $c\phi$（$c$ 可以取任何实数）。信号 $u$ 是直线外的一个点；我们要从 $u$ 出发，找直线上离它最近的一点。

在平面几何里，最近点是**垂足**：从 $u$ 向直线作垂线，垂线与直线的交点。

垂足有两个性质：
- 它到 $u$ 的距离是所有点中最短的；
- 从 $u$ 连到垂足的线段，与直线垂直。

那在信号与系统中，我们怎么理解这个垂直的事情：

- $c\phi$ 的选取，就是“在直线上取一点”；
- 误差 $e=u-c\phi$ 就是从 $u$ 连到该点的“线段”；
- 最优的 $c\phi$ 就是垂足，此时 $e$ 与 $\phi$ 垂直，即 $\langle e,\phi\rangle_P=0$。

反过来也能看出为什么“垂直”就是最短：若 $e$ 与 $\phi$ 不垂直，那么把 $c$ 沿直线的方向稍微挪动一点，就能让 $u$ 到 $c\phi$ 的距离变短；只有在垂直时，沿直线移动的任何一小步都只会让距离变大（或不变）。所以垂直是距离最短的标志。

这也解释了勾股关系。垂足把 $u$ 分解成两个互相垂直的部分：投影 $c\phi$ 和残差 $e$。就像直角三角形的两条直角边一样，范数满足勾股定理：

$$\|u\|^2=\|c\phi\|^2+\|e\|^2.$$

这里的 $\|u\|^2$ 就是平均功率，所以总功率等于投影功率加误差功率。

**推导**。用 $c\phi$ 逼近 $u$ 所产生的误差定义为

$$e(t)=u(t)-c\phi(t).$$

误差范数的平方就是误差的平均功率：

$$\|e\|^2=\langle u-c\phi,u-c\phi\rangle_P.$$

展开：

$$\|e\|^2=\|u\|^2-2\operatorname{Re}\left(c^*\langle u,\phi\rangle_P\right)+|c|^2\|\phi\|^2.$$

记 $K=\langle u,\phi\rangle_P$，$M=\langle\phi,\phi\rangle_P$。对 $c$ 配方：

$$\|e\|^2=\|u\|^2-\frac{|K|^2}{M}+M\left|c-\frac{K}{M}\right|^2.$$

前两项与 $c$ 无关，第三项非负，因此最小值在

$$c=\frac{K}{M}=\frac{\langle u,\phi\rangle_P}{\langle\phi,\phi\rangle_P}$$

时取得。这个 $c$ 称为正交投影系数。

**最优时误差与基函数正交**。把 $c$ 代回：

$$\langle e,\phi\rangle_P=\langle u,\phi\rangle_P-c\langle\phi,\phi\rangle_P=K-cM=0.$$

这说明残差垂直于投影方向，垂足就是最优近似。

**功率的勾股关系**。因为 $\langle e,\phi\rangle_P=0$，

$$\|u\|^2=\|c\phi\|^2+\|e\|^2,$$

即总功率等于投影功率与误差功率之和。保留的谐波越多，误差功率越小。

**例**　用 $\phi(t)=\cos t$ 近似 $u(t)=\cos t+\frac12\cos2t$（周期 $T=2\pi$）。

内积按本节定义计算。$u$、$v$ 都是实信号，$v^*=v$，所以

$$\langle u,v\rangle_P=\frac1{T}\int_T u(t)v^*(t)dt=\frac1{2\pi}\int_0^{2\pi}u(t)v(t)\,dt.$$

**第一步：计算 $\langle u,\cos t\rangle_P$。** 把 $u$ 代入，利用内积的线性拆成两项：

$$
\begin{aligned}
\langle u,\cos t\rangle_P
&=\frac1{2\pi}\int_0^{2\pi}\left(\cos t+\frac12\cos2t\right)\cos t\,dt\\
&=\frac1{2\pi}\int_0^{2\pi}\cos^2t\,dt
+\frac1{2\pi}\int_0^{2\pi}\frac12\cos2t\cos t\,dt.
\end{aligned}
$$

第一项用降幂公式 $\cos^2t=\frac{1+\cos2t}{2}$：

$$\frac1{2\pi}\int_0^{2\pi}\cos^2t\,dt
=\frac1{2\pi}\int_0^{2\pi}\frac{1+\cos2t}{2}\,dt
=\frac1{2\pi}\left[\frac t2+\frac{\sin2t}{4}\right]_0^{2\pi}
=\frac1{2\pi}\cdot\pi=\frac12.$$

第二项用积化和差 $\cos2t\cos t=\frac12(\cos3t+\cos t)$：

$$\frac1{2\pi}\int_0^{2\pi}\frac12\cos2t\cos t\,dt
=\frac1{8\pi}\int_0^{2\pi}(\cos3t+\cos t)\,dt
=\frac1{8\pi}\left[\frac{\sin3t}{3}+\sin t\right]_0^{2\pi}=0.$$

因为 $\cos3t$ 和 $\cos t$ 在 $[0,2\pi]$ 上都包含整数个完整周期，积分均为零——这就是“不同频率的余弦正交”。所以

$$\langle u,\cos t\rangle_P=\frac12+0=\frac12.$$

**第二步：计算 $\langle\cos t,\cos t\rangle_P$。** 与上面第一项完全相同：

$$\langle\cos t,\cos t\rangle_P=\frac1{2\pi}\int_0^{2\pi}\cos^2t\,dt=\frac12.$$

因此

$$c=\frac{\langle u,\cos t\rangle_P}{\langle\cos t,\cos t\rangle_P}=\frac{1/2}{1/2}=1.$$

**紧凑写法。** 把 $u$ 的两项分开看：$\cos t$ 的系数是 $1$，$\cos2t$ 的系数是 $\frac12$，于是

$$\langle u,\cos t\rangle_P=1\cdot\langle\cos t,\cos t\rangle_P+\frac12\cdot\langle\cos2t,\cos t\rangle_P
=1\cdot\frac12+\frac12\cdot0=\frac12.$$

第二项因正交而消失，剩下的 $\frac12$ 正是 $\langle\cos t,\cos t\rangle_P$，这就是 $\frac12\cdot1$ 的来历。

近似结果为 $\cos t$，误差为 $e=\frac12\cos2t$，误差功率

$$\|e\|^2=\left\|\frac12\cos2t\right\|^2=\left(\frac12\right)^2\langle\cos2t,\cos2t\rangle_P=\frac14\cdot\frac12=\frac18.$$

总功率（交叉项 $\langle\cos t,\cos2t\rangle_P=0$，故可直接相加）

$$\|u\|^2=\|\cos t\|^2+\left\|\frac12\cos2t\right\|^2=\frac12+\frac18=\frac58,$$

投影功率

$$\|c\phi\|^2=1^2\cdot\frac12=\frac12.$$

两者相加等于总功率，与勾股关系一致。

**与傅里叶系数的关系**。把 $\phi$ 换成基函数 $\phi_k(t)=e^{jk\omega_0t}$，上式给出的 $c$ 就是傅里叶系数，见下一小节。

#### 傅里叶系数就是投影系数

取

$$\phi_k(t)=e^{jk\omega_0t}.$$

由正交性，

$$\langle\phi_k,\phi_m\rangle_P=\frac1{T}\int_{T}e^{j(k-m)\omega_0t}dt=\begin{cases}1,&k=m,\\0,&k\ne m.\end{cases}$$

每个基函数的范数平方为 $1$。因此 $u$ 在第 $k$ 个基函数上的投影系数为

$$c_k=\frac{\langle u,\phi_k\rangle_P}{\langle\phi_k,\phi_k\rangle_P}=\frac1{T}\int_{T}u(t)e^{-jk\omega_0t}dt,$$

正好是傅里叶系数的定义式。傅里叶级数展开就是把信号依次投影到各个谐波基函数上。

由于基函数两两正交，截断级数的各项功率之间没有交叉项，可以直接相加。这就是 Parseval 定理的来源。

### 2.8 Parseval 定理

周期信号的平均功率为

$$P=\frac1{T}\int_{T}|u(t)|^2dt=\sum_{k=-\infty}^{\infty}|c_k|^2.$$

时域计算与频域计算给出相同结果。对实信号，利用 $|c_{-k}|=|c_k|$，可以写成单边形式：

$$P=|c_0|^2+\sum_{k=1}^{\infty}2|c_k|^2.$$

其中 $|c_0|^2$ 是直流功率，$2|c_k|^2$ 是第 $k$ 次谐波的平均功率。

**例 1**　幅值为 $1$ 的方波，$|u(t)|=1$，总平均功率为

$$P=1.$$

奇对称方波的基波系数为 $c_1=-2j/\pi$，基波功率为

$$2|c_1|^2=2\cdot\frac{4}{\pi^2}=\frac{8}{\pi^2}\approx0.8106,$$

占总功率的 $81.06\%$。

**例 2**　占空比为 $d$、高度为 $A$ 的矩形脉冲串。

一个周期内脉冲宽度为 $\tau=dT$，总功率为

$$P=A^2d.$$

直流系数 $c_0=Ad$，直流功率为

$$|c_0|^2=A^2d^2.$$

直流功率占总功率的比例为 $d$。

### 2.9 典型周期波形的傅里叶系数

所有结果都来自同一个定义：

$$c_k=\frac1{T}\int_{T}u(t)e^{-jk\omega_0t}dt,\qquad \omega_0=\frac{2\pi}{T}.$$

计算时按以下顺序进行：

1. 确定周期 $T$ 和基频 $\omega_0$。
2. 写出一个周期内的分段表达式，选择方便的积分区间。
3. 先利用奇偶性、半波对称性判断哪些系数为零，减少积分。
4. 对剩余系数积分，按 $k$ 的奇偶化简。
5. 单独检查 $k=0$ 和分母为零的特殊 $k$。

#### 2.9.1 奇对称双极方波

波形：

$$u(t)=\begin{cases}A,&0<t<T/2,\\-A,&-T/2<t<0.\end{cases}$$

它是奇函数，所以 $a_k=0$，$c_0=0$，$c_k$ 为纯虚数。由奇函数的正弦系数公式，

$$b_k=\frac4{T}\int_0^{T/2}A\sin(k\omega_0t)dt.$$

计算积分：

$$\int_0^{T/2}\sin(k\omega_0t)dt=\frac{1-\cos(k\pi)}{k\omega_0}=\frac{1-(-1)^k}{k\omega_0}.$$

因此

$$b_k=\frac{4A}{T}\cdot\frac{1-(-1)^k}{k\omega_0}=\frac{2A\left[1-(-1)^k\right]}{\pi k}.$$

当 $k$ 为偶数时 $b_k=0$；当 $k$ 为奇数时

$$b_k=\frac{4A}{\pi k}.$$

由 $c_k=-jb_k/2$，得到

$$c_k=-\frac{2jA}{\pi k}\qquad(k\text{ 为奇数}),$$

偶数 $k$ 时 $c_k=0$。

对应的三角级数为

$$u(t)=\frac{4A}{\pi}\left(\sin\omega_0t+\frac13\sin3\omega_0t+\frac15\sin5\omega_0t+\cdots\right).$$

#### 2.9.2 偶对称双极方波

波形：

$$u(t)=\begin{cases}+A,&|t|<T/4,\\-A,&T/4<|t|<T/2.\end{cases}$$

它是偶函数，所以 $b_k=0$，$c_k$ 为实数，$c_0=0$。由偶函数的余弦系数公式，

$$c_k=\frac2{T}\int_0^{T/2}u(t)\cos(k\omega_0t)dt.$$

分段计算：

$$c_k=\frac{2A}{T}\left[\int_0^{T/4}\cos(k\omega_0t)dt-\int_{T/4}^{T/2}\cos(k\omega_0t)dt\right].$$

两个积分分别为

$$\int_0^{T/4}\cos(k\omega_0t)dt=\frac{\sin(k\pi/2)}{k\omega_0},$$

$$\int_{T/4}^{T/2}\cos(k\omega_0t)dt=\frac{\sin(k\pi)-\sin(k\pi/2)}{k\omega_0}=-\frac{\sin(k\pi/2)}{k\omega_0}.$$

因此

$$c_k=\frac{2A}{T}\cdot\frac{2\sin(k\pi/2)}{k\omega_0}
=\frac{4A}{T}\cdot\frac{T}{2\pi k}\sin\frac{k\pi}{2}
=A\operatorname{sinc}\left(\frac{k}{2}\right)\qquad(k\text{ 为奇数}).$$

$k$ 为偶数时 $\sin(k\pi/2)=0$，$c_k=0$，因此只有奇次谐波。前几项为

$$u(t)=\frac{4A}{\pi}\left(\cos\omega_0t-\frac13\cos3\omega_0t+\frac15\cos5\omega_0t-\cdots\right).$$

#### 2.9.3 矩形脉冲串

波形：在一个周期内

$$u(t)=A,\qquad |t|<\frac{\tau}{2},$$

其余为零。周期为 $T$，占空比

$$d=\frac{\tau}{T}.$$

系数为

$$c_k=\frac{A}{T}\int_{-\tau/2}^{\tau/2}e^{-jk\omega_0t}dt.$$

计算积分：

$$\int_{-\tau/2}^{\tau/2}e^{-jk\omega_0t}dt
=\frac{e^{jk\omega_0\tau/2}-e^{-jk\omega_0\tau/2}}{jk\omega_0}
=\frac{2\sin(k\omega_0\tau/2)}{k\omega_0}.$$

因此

$$c_k=\frac{2A}{Tk\omega_0}\sin\frac{k\omega_0\tau}{2}.$$

代入 $\omega_0=2\pi/T$ 和 $\tau=dT$：

$$c_k=\frac{A}{k\pi}\sin(k\pi d)=Ad\operatorname{sinc}(kd).$$

当 $k=0$ 时，利用 $\sin x/x\to1$，得

$$c_0=Ad.$$

矩形脉冲串的频谱包络为 sinc 形状，第一个零点出现在

$$kd=1\quad\Longrightarrow\quad k=\frac1d.$$

若 $d=1/3$，第一个零点在 $k=3$。

#### 2.9.4 半波整流

波形（记整流前正弦的频率为 $\omega_m$，基频为 $\omega_0$）：

$$u(t)=\begin{cases}A\sin\omega_mt,&0<t<\pi/\omega_m,\\0,&\text{其余}.\end{cases}$$

周期为

$$T=\frac{2\pi}{\omega_m},$$

基频为 $\omega_0=\dfrac{2\pi}{T}=\omega_m$。系数为

$$c_k=\frac{\omega_m}{2\pi}\int_0^{\pi/\omega_m}A\sin(\omega_mt)e^{-jk\omega_mt}dt.$$

令 $x=\omega_mt$，得

$$c_k=\frac{A}{2\pi}\int_0^\pi\sin x\,e^{-jkx}dx.$$

先计算积分。对 $k\ne\pm1$，用欧拉公式：

$$\int_0^\pi\sin x\,e^{-jkx}dx
=\frac1{2j}\left[\int_0^\pi e^{j(1-k)x}dx-\int_0^\pi e^{-j(1+k)x}dx\right].$$

两个积分分别为

$$\int_0^\pi e^{j(1-k)x}dx=\frac{(-1)^{1-k}-1}{j(1-k)},$$

$$\int_0^\pi e^{-j(1+k)x}dx=\frac{(-1)^{-(1+k)}-1}{-j(1+k)}.$$

合并后得到

$$\int_0^\pi\sin x\,e^{-jkx}dx=\frac{1+(-1)^k}{1-k^2}\qquad(k\ne\pm1).$$

因此

$$c_k=\frac{A\left[1+(-1)^k\right]}{2\pi(1-k^2)}\qquad(k\ne\pm1).$$

分类讨论：

- $k=0$：

$$c_0=\frac{A\cdot2}{2\pi}=\frac{A}{\pi}.$$

- $k$ 为偶数且 $k\ne0$：

$$c_k=\frac{A}{\pi(1-k^2)}.$$

- $k$ 为奇数且 $|k|\ge3$：

$$c_k=0.$$

$k=\pm1$ 时分母为零，需要单独计算。对 $k=1$，

$$\int_0^\pi\sin x\,e^{-jx}dx
=\int_0^\pi\sin x\cos x\,dx-j\int_0^\pi\sin^2x\,dx
=0-j\frac{\pi}{2}=-j\frac{\pi}{2}.$$

因此

$$c_1=\frac{A}{2\pi}\left(-j\frac{\pi}{2}\right)=-\frac{jA}{4}.$$

由共轭对称，

$$c_{-1}=+\frac{jA}{4}.$$

对应的基波正弦系数为

$$b_1=-2\operatorname{Im}c_1=-2\left(-\frac A4\right)=\frac A2.$$

半波整流的傅里叶级数只含直流、基波和偶次谐波：

$$u(t)=\frac{A}{\pi}+\frac A2\sin\omega_mt-\frac{2A}{\pi}\left(\frac{\cos2\omega_mt}{3}+\frac{\cos4\omega_mt}{15}+\cdots\right).$$

#### 2.9.5 全波整流

波形（公式表记作 $A\lvert\sin(\omega_0t)\rvert$，这里的 $\omega_0$ 是整流前正弦的频率）：

$$u(t)=A|\sin\omega_0t|.$$

周期为

$$T=\frac{\pi}{\omega_0},$$

整流后的基频为

$$\frac{2\pi}{T}=2\omega_0.$$

在一个周期 $0\le t<\pi/\omega_0$ 内，$\sin\omega_0t\ge0$，因此

$$c_k=\frac{\omega_0}{\pi}\int_0^{\pi/\omega_0}A\sin(\omega_0t)e^{-j2k\omega_0t}dt.$$

令 $x=\omega_0t$：

$$c_k=\frac{A}{\pi}\int_0^\pi\sin x\,e^{-j2kx}dx.$$

利用上一节的结果，把 $k$ 换成 $2k$：

$$\int_0^\pi\sin x\,e^{-j2kx}dx=\frac{1+(-1)^{2k}}{1-(2k)^2}=\frac{2}{1-4k^2}.$$

因此

$$c_k=\frac{2A}{\pi(1-4k^2)}.$$

直流分量为

$$c_0=\frac{2A}{\pi}.$$

对应的实余弦系数为 $a_0=c_0=\dfrac{2A}{\pi}$、$a_k=2c_k=\dfrac{4A}{\pi(1-4k^2)}$，三角级数为

$$u(t)=\frac{2A}{\pi}-\frac{4A}{3\pi}\cos2\omega_0t-\frac{4A}{15\pi}\cos4\omega_0t-\cdots.$$

全波整流只含直流和偶次谐波，基频为 $2\omega_0$。这与公式表中该行 $c_k=\dfrac{2A}{\pi(1-4k^2)}$ 完全一致。

#### 2.9.6 锯齿波

波形：

$$u(t)=\frac{2At}{T},\qquad |t|<\frac{T}{2}.$$

它是奇函数，所以 $c_0=0$，$c_k$ 为纯虚数。系数为

$$c_k=\frac{2A}{T^2}\int_{-T/2}^{T/2}t\,e^{-jk\omega_0t}dt.$$

记 $a=jk\omega_0$，用分部积分公式

$$\int te^{-at}dt=e^{-at}\left(-\frac{t}{a}-\frac{1}{a^2}\right).$$

代入上下限：

$$\int_{-T/2}^{T/2}te^{-at}dt
=e^{-aT/2}\left(-\frac{T}{2a}-\frac1{a^2}\right)
-e^{aT/2}\left(\frac{T}{2a}-\frac1{a^2}\right).$$

由于 $e^{\pm aT/2}=e^{\pm jk\pi}=(-1)^k$，两个 $1/a^2$ 项相消，得

$$\int_{-T/2}^{T/2}te^{-at}dt=(-1)^k\left(-\frac{T}{a}\right).$$

代回：

$$c_k=\frac{2A}{T^2}\cdot(-1)^k\left(-\frac{T}{jk\omega_0}\right)
=\frac{jA(-1)^k}{k\pi}.$$

前两个系数为

$$c_1=-\frac{jA}{\pi},\qquad c_2=+\frac{jA}{2\pi}.$$

对应的正弦系数为

$$b_k=-2\operatorname{Im}c_k=-\frac{2A(-1)^k}{k\pi}.$$

由于 $b_1=2A/\pi$，锯齿波的傅里叶级数为

$$u(t)=\frac{2A}{\pi}\left(\sin\omega_0t-\frac12\sin2\omega_0t+\frac13\sin3\omega_0t-\cdots\right).$$

#### 2.9.7 三角波

波形：

$$u(t)=A-\frac{4A}{T}|t|,\qquad |t|\le\frac{T}{2}.$$

在 $t=0$ 处 $u=A$，在 $t=\pm T/2$ 处 $u=-A$。它是偶函数，平均值为零，所以 $b_k=0$，$c_0=0$。系数为

$$c_k=\frac2{T}\int_0^{T/2}u(t)\cos(k\omega_0t)dt.$$

令 $x=\omega_0t=\frac{2\pi}{T}t$，则 $t=\frac{T}{2\pi}x$，$dt=\frac{T}{2\pi}dx$，且

$$u=A\left(1-\frac{2x}{\pi}\right).$$

代入：

$$c_k=\frac{A}{\pi}\int_0^\pi\left(1-\frac{2x}{\pi}\right)\cos(kx)dx.$$

拆成两个积分：

$$\int_0^\pi\cos(kx)dx=0\qquad(k\ge1),$$

$$\int_0^\pi x\cos(kx)dx=\left[\frac{x\sin kx}{k}+\frac{\cos kx}{k^2}\right]_0^\pi=\frac{(-1)^k-1}{k^2}.$$

因此

$$c_k=\frac{A}{\pi}\left[0-\frac2\pi\cdot\frac{(-1)^k-1}{k^2}\right]
=\frac{2A}{\pi^2}\cdot\frac{1-(-1)^k}{k^2}.$$

当 $k$ 为偶数时 $c_k=0$；当 $k$ 为奇数时

$$c_k=\frac{4A}{\pi^2k^2}.$$

余弦系数为 $a_k=2c_k=8A/(\pi^2k^2)$，所以

$$u(t)=\frac{8A}{\pi^2}\left(\cos\omega_0t+\frac19\cos3\omega_0t+\frac1{25}\cos5\omega_0t+\cdots\right).$$

#### 2.9.8 汇总表

下表统一使用 $\omega_0=2\pi/T$，$d=\tau/T$。$c_k$ 为复系数，实系数按 $a_k=2\operatorname{Re}c_k$、$b_k=-2\operatorname{Im}c_k$ 换算，直流项 $a_0=c_0$。

公式表列出的六种波形与本表的对应关系：

| 公式表中的信号 | 系数 |
|---|---|
| $\cos(\omega_0t)$ | $c_1=c_{-1}=\dfrac12$，其余为零 |
| $\sin(\omega_0t)$ | $c_1=-\dfrac j2$，$c_{-1}=\dfrac j2$，其余为零 |
| 偶对称方波 $+A$（$\lvert t\rvert<T/4$）、$-A$（$T/4<\lvert t\rvert<T/2$） | $c_k=A\operatorname{sinc}\left(\dfrac k2\right)$（$k$ 奇），$c_k=0$（$k$ 偶） |
| 脉冲串 $Ap_\tau(t)$，$d=\tau/T$ | $c_k=Ad\operatorname{sinc}(kd)$ |
| 三角波 $A(1-4\lvert t\rvert/T)$（$\lvert t\rvert\le T/2$） | $c_k=\dfrac{4A}{\pi^2k^2}$（$k$ 奇），$c_k=0$（$k$ 偶） |
| 全波整流正弦 $A\lvert\sin(\omega_0t)\rvert$（$T=\pi/\omega_0$） | $c_k=\dfrac{2A}{\pi(1-4k^2)}$ |

其余波形（锯齿波、半波整流、奇对称方波）是本笔记的补充，用于对照推导过程。

| 波形 | 时域表达式 | 周期 | 基频 | $c_0$ | $c_k$（$k\ne0$） | 实系数 |
|---|---|---|---|---|---|---|
| 奇对称双极方波 | $A$（$0<t<T/2$），$-A$（$-T/2<t<0$） | $T$ | $2\pi/T$ | $0$ | $k$ 奇：$-\dfrac{2jA}{\pi k}$；$k$ 偶：$0$ | $b_k=\dfrac{4A}{\pi k}$（$k$ 奇） |
| 偶对称双极方波 | $+A$（$\lvert t\rvert<T/4$），$-A$（$T/4<\lvert t\rvert<T/2$） | $T$ | $2\pi/T$ | $0$ | $k$ 奇：$A\operatorname{sinc}\left(\dfrac{k}{2}\right)$；$k$ 偶：$0$ | $a_k=\dfrac{4A}{\pi k}(-1)^{(k-1)/2}$（$k$ 奇） |
| 矩形脉冲串 | $Ap_\tau(t)$，$d=\tau/T$ | $T$ | $2\pi/T$ | $Ad$ | $Ad\operatorname{sinc}(kd)$ | $a_k=2Ad\operatorname{sinc}(kd)$ |
| 半波整流 | $A\sin\omega_0 t$（$0<t<\pi/\omega_0$），其余为零 | $2\pi/\omega_0$ | $\omega_0$ | $\dfrac{A}{\pi}$ | $k=\pm1$：$\mp\dfrac{jA}{4}$；$k$ 偶且 $k\ne0$：$\dfrac{A}{\pi(1-k^2)}$；其余奇次：$0$ | $b_1=\dfrac A2$；$a_k=\dfrac{2A}{\pi(1-k^2)}$（$k$ 偶） |
| 全波整流 | $A\lvert\sin\omega_0 t\rvert$ | $\pi/\omega_0$ | $2\omega_0$ | $\dfrac{2A}{\pi}$ | $\dfrac{2A}{\pi(1-4k^2)}$ | $a_k=\dfrac{4A}{\pi(1-4k^2)}$ |
| 锯齿波 | $2At/T$（$\lvert t\rvert<T/2$） | $T$ | $2\pi/T$ | $0$ | $\dfrac{jA(-1)^k}{k\pi}$ | $b_k=-\dfrac{2A(-1)^k}{k\pi}$ |
| 三角波 | $A(1-4\lvert t\rvert/T)$（$\lvert t\rvert\le T/2$） | $T$ | $2\pi/T$ | $0$ | $k$ 奇：$\dfrac{4A}{\pi^2k^2}$；$k$ 偶：$0$ | $a_k=\dfrac{8A}{\pi^2k^2}$（$k$ 奇），即 $a_k=2c_k$，与公式表 $c_k$ 一致 |

使用表格时注意：

1. 全波整流的周期是 $\pi/\omega_0$，基频是 $2\omega_0$，不能把整流前正弦的频率 $\omega_0$ 当作它的基频。
2. 半波整流的 $k=\pm1$ 要单独处理，不能代入 $\dfrac{A}{\pi(1-k^2)}$。
3. 表中的「奇次」「偶次」指谐波次数 $k$ 的奇偶，与波形本身的奇偶对称性无关。
4. 全波整流按公式表取 $c_k=\dfrac{2A}{\pi(1-4k^2)}$、$c_0=\dfrac{2A}{\pi}$。有些资料只列实余弦系数 $a_k=\dfrac{4A}{\pi(1-4k^2)}$，数值是 $c_k$ 的两倍，不要直接当成复系数使用。
5. 不同教材对三角形式常数项的定义可能不同。本表按 $a_0=c_0$ 换算；若使用 $a_0/2$ 的约定，直流项要相应乘 $2$。

### 2.10 收敛性与 Gibbs 现象

傅里叶级数的均方收敛对平方可积信号总成立：

$$\lim_{N\to\infty}\int_{T}\left|u(t)-\sum_{k=-N}^{N}c_ke^{jk\omega_0t}\right|^2dt=0.$$

逐点收敛需要 Dirichlet 条件。满足条件时：

- 在连续点，级数收敛于 $u(t)$。
- 在间断点 $t_0$，级数收敛于左右极限的平均值

$$\frac{u(t_0^+)+u(t_0^-)}{2}.$$

- 在跳变附近，截断级数出现过冲，过冲幅度约为跳变量的 $9\%$，不随截断阶数增大而消失。这种现象称为 Gibbs 现象。

均方误差最小与逐点过冲可以同时成立。增加项数会使总误差功率减小，但跳变处的过冲不会消失。

### 2.11 周期信号的傅里叶变换

周期信号不满足绝对可积，但可以在广义函数意义下求傅里叶变换。由

$$e^{jk\omega_0t}\longleftrightarrow 2\pi\delta(\omega-k\omega_0),$$

逐项变换得

$$U(j\omega)=2\pi\sum_{k=-\infty}^{\infty}c_k\delta(\omega-k\omega_0).$$

周期信号的频谱是一串冲激，冲激位于 $\omega=k\omega_0$，权重为 $2\pi c_k$。

这里有三组容易混淆的量：

| 表示方式 | 纵轴含义 | 用途 |
|---|---|---|
| 复系数 $c_k$ | 第 $k$ 次谐波的复幅度 | 傅里叶级数系数 |
| 冲激权重 $2\pi c_k$ | 傅里叶变换中冲激的面积 | 写成 $U(j\omega)$ 时的正式表达 |
| 归一化谱线 $Tc_k$ | 与连续频谱包络同量纲 | 比较离散谱线与包络 |

三者的关系为

$$2\pi c_k=\omega_0\,Tc_k,\qquad \omega_0=\frac{2\pi}{T}.$$

冲激权重除以谱线间隔 $\omega_0$，等于归一化谱线高度 $Tc_k$。做题时要先看清题目画的是哪一种谱。

$2\pi$ 因子的来源是逆变换前的 $1/(2\pi)$。把 $U(j\omega)$ 代回逆变换：

$$u(t)=\frac1{2\pi}\int_{-\infty}^{\infty}2\pi\sum_kc_k\delta(\omega-k\omega_0)e^{j\omega t}d\omega
=\sum_kc_ke^{jk\omega_0t},$$

正好回到傅里叶级数。若冲激权重漏掉 $2\pi$，逆变换结果会缩小 $2\pi$ 倍。

**例**　$u(t)=5+4\cos3t-2\sin3t$。

基频为 $\omega_0=3$。三角系数为

$$a_0=5,\qquad a_1=4,\qquad b_1=-2.$$

复系数为

$$c_0=5,\qquad c_1=\frac{4-j(-2)}{2}=2+j,\qquad c_{-1}=2-j.$$

冲激权重为

$$2\pi c_0=10\pi,$$

$$2\pi c_1=2\pi(2+j)=4\pi+2\pi j,$$

$$2\pi c_{-1}=4\pi-2\pi j.$$

因此

$$U(j\omega)=2\pi\left[5\delta(\omega)+(2+j)\delta(\omega-3)+(2-j)\delta(\omega+3)\right].$$

校验：$u(0)=5+4=9$，而 $c_0+c_1+c_{-1}=5+(2+j)+(2-j)=9$，一致。

### 2.12 傅里叶级数典型例题

**例 1（锯齿波的奇偶性）**　$u(t)=2At/T$，$|t|<T/2$。

该信号为奇函数，所以 $a_k=0$，$c_0=0$。由 2.9.6 节，

$$c_k=\frac{jA(-1)^k}{k\pi}\qquad(k\ne0).$$

系数为纯虚数，与奇函数的结论一致。

**例 2（偶对称方波的系数）**　$+A$ 占 $|t|<T/4$，$-A$ 占 $T/4<|t|<T/2$。

由 2.9.2 节，

$$c_k=A\frac{\sin(k\pi/2)}{k\pi/2}\qquad(k\ne0),\qquad c_0=0.$$

取 $A=6$，$k=5$：

$$c_5=6\cdot\frac{\sin(5\pi/2)}{5\pi/2}=6\cdot\frac{1}{5\pi/2}=\frac{12}{5\pi}\approx0.7639.$$

**例 3（占空比与谱线零点）**　矩形脉冲串的系数为

$$c_k=Ad\frac{\sin(k\pi d)}{k\pi d}.$$

当 $kd$ 为非零整数时，$\sin(k\pi d)=0$。第一个零点为

$$k=\frac1d.$$

若 $d=1/3$，第一个零点在 $k=3$；若 $d=1/2$，第一个零点在 $k=2$。

**例 4（直流系数）**

- 信号在 $1/4$ 周期取 $+8$，在 $3/4$ 周期取 $-2$：

$$c_0=\frac14\cdot8+\frac34\cdot(-2)=2-1.5=0.5.$$

- 周期为 $2$，前半周 $+1$，后半周 $-1$：

$$c_0=\frac12\left[(+1)\cdot1+(-1)\cdot1\right]=0.$$

- 周期为 $1$，脉冲宽度为 $d$，高度为 $1/\sqrt d$：

$$c_0=\frac11\cdot\frac1{\sqrt d}\cdot d=\sqrt d.$$

取 $d=0.01$，$c_0=0.1$。

**例 5（实信号的负频率配对）**　$c_1=2-3j$。

实信号满足 $c_{-1}=\overline{c_1}=2+3j$。两项合成的实信号为

$$2|c_1|\cos(t+\angle c_1)=2\sqrt{13}\cos\left(t-\arctan\frac32\right).$$

**例 6（Parseval 定理）**　幅值为 $1$ 的方波。

总功率为

$$P=\frac1{T}\int_{T}|u|^2dt=1.$$

基波功率为

$$2|c_1|^2=2\left(\frac2\pi\right)^2=\frac8{\pi^2}\approx0.8106.$$

基波占总功率的 $81.06\%$。

---

## 3 傅里叶变换

### 3.1 从傅里叶级数到傅里叶变换

周期信号的谱线间隔为

$$\omega_0=\frac{2\pi}{T}.$$

周期越大，谱线越密。把周期趋于无穷大，信号在一个周期内不再重复，变成非周期信号；谱线间隔趋于零，离散谱线连成连续频谱。傅里叶变换可以看作傅里叶级数在 $T\to\infty$ 时的极限。

设 $u(t)$ 只在某个有限区间内非零，把它看作周期 $T$ 的周期信号的片段。其傅里叶系数为

$$c_k=\frac1{T}\int_{-T/2}^{T/2}u(t)e^{-jk\omega_0t}dt.$$

当 $T$ 足够大时，积分近似为整个傅里叶变换在 $\omega=k\omega_0$ 处的值：

$$Tc_k\approx U(jk\omega_0).$$

因此 $c_k\approx U(jk\omega_0)/T$。谱线高度随 $1/T$ 趋于零，但相邻谱线间隔也趋于零，谱线连成连续的包络 $U(j\omega)$。

### 3.2 定义

傅里叶变换定义为

$$U(j\omega)=\int_{-\infty}^{\infty}u(t)e^{-j\omega t}dt.$$

逆变换为

$$u(t)=\frac1{2\pi}\int_{-\infty}^{\infty}U(j\omega)e^{j\omega t}d\omega.$$

正变换中没有 $1/(2\pi)$，逆变换中有 $1/(2\pi)$。这套约定决定了周期信号冲激谱中的 $2\pi$ 因子、Parseval 能量公式中的 $1/(2\pi)$，以及乘法性质中的 $1/(2\pi)$。

若改用频率 $f$ 表示，正变换和逆变换分别为

$$U(f)=\int_{-\infty}^{\infty}u(t)e^{-j2\pi ft}dt,\qquad
u(t)=\int_{-\infty}^{\infty}U(f)e^{j2\pi ft}df.$$

两套约定之间只差变量替换 $\omega=2\pi f$，公式中的 $2\pi$ 位置不同。做题时不要混用。

傅里叶变换与傅里叶级数的记号要区分：

- 周期信号用 $c_k$ 表示傅里叶级数系数。
- 非周期信号用 $U(j\omega)$ 表示傅里叶变换。
- 周期信号的傅里叶变换用冲激串表示，冲激权重为 $2\pi c_k$。

### 3.3 存在性

若 $u(t)$ 绝对可积，

$$\int_{-\infty}^{\infty}|u(t)|dt<\infty,$$

则傅里叶变换存在且连续。这是充分条件，不是必要条件。

常数、正弦、阶跃和周期信号不满足绝对可积，但可以在广义函数意义下写出含冲激的傅里叶变换。

**判据的三个层次**：

1. **古典意义（充分条件）**：绝对可积 $\int|u|dt<\infty$，变换存在且连续。
2. **广义意义**：若增长不过快，即存在常数 $C$、$N$ 使
   $$|u(t)|\le C(1+|t|)^N,$$
   则 $u$ 是**缓增分布**，存在含冲激（及其导数）的广义傅里叶变换。常数、正弦、阶跃、周期信号都属于这一层，它们增长有界或至多多项式增长。
3. **指数增长**：若 $|u(t)|$ 比任何多项式增长得都快，如 $e^{2t}H(t)$，则 $u$ 不是缓增分布，连广义变换也不存在，必须改用拉普拉斯变换。

**广义变换是什么**：不发散的积分不能用普通定义，改用“分布与测试函数的配对”来定义。取速降的测试函数 $\phi$，定义

$$\langle U,\phi\rangle=\langle u,\hat\phi\rangle=\int_{-\infty}^{\infty}u(t)\,\hat\phi(t)\,dt,\qquad
\hat\phi(\omega)=\int_{-\infty}^{\infty}\phi(t)e^{-j\omega t}dt.$$

由于 $\hat\phi$ 速降，而 $u$ 至多多项式增长，右边积分收敛，于是 $U$ 被唯一确定。这样得到的 $U$ 里允许出现 $\delta(\omega)$。例如 $1\leftrightarrow2\pi\delta(\omega)$ 的意思是：对每个测试函数 $\phi$，

$$\int_{-\infty}^{\infty}\hat\phi(\omega)\,d\omega
=2\pi\phi(0)
=\langle2\pi\delta,\phi\rangle,$$

即用 $\delta$ 的筛选性质对 $\phi$ 取值。实际做题时不必真的引入测试函数，等价的操作是“乘衰减因子再取极限”，例如

$$\cos5t=\lim_{a\to0^+}e^{-a|t|}\cos5t.$$

右边是绝对可积信号，先算它的普通频谱，再令 $a\to0^+$，极限中自然出现冲激。

**与拉普拉斯变换的关系**：只有收敛域包含虚轴时，才能用 $U(j\omega)=U(s)\big|_{s=j\omega}$。$e^{2t}H(t)$ 的收敛域为 $\operatorname{Re}s>2$，不含虚轴，所以形式上写出的 $\frac{1}{j\omega-2}$ 只是解析延拓，不是任何收敛积分的值，也不是一个分布的傅里叶变换。

单位阶跃信号定义为

$$H(t)=\begin{cases}1,&t>0,\\0,&t<0.\end{cases}$$

$t=0$ 处的取值不影响积分，通常取 $1/2$。它的作用是限制积分区间。例如 $e^{-3t}H(t)$ 在 $t<0$ 为零，因此绝对可积；$e^{-3t}$ 在 $t<0$ 时指数增长，不绝对可积。

**例**　$e^{2t}H(t)$ 没有傅里叶变换。

变换积分为

$$\int_0^\infty e^{2t}e^{-j\omega t}dt=\int_0^\infty e^{(2-j\omega)t}dt.$$

被积函数的模为 $e^{2t}$，在 $t\to\infty$ 时发散，因此对任何 $\omega$ 积分都不收敛。$e^{2t}$ 的增长快于任何多项式，不是缓增分布，所以连含冲激的广义变换也不存在；这类信号需要改用拉普拉斯变换。

### 3.4 常用变换对

| 时域 $u(t)$ | 频域 $U(j\omega)$ | 条件 |
|---|---|---|
| $\delta(t-t_0)$ | $e^{-j\omega t_0}$ | — |
| $1$ | $2\pi\delta(\omega)$ | 广义 |
| $e^{j\omega_0t}$ | $2\pi\delta(\omega-\omega_0)$ | 广义 |
| $\cos\omega_0t$ | $\pi\left[\delta(\omega-\omega_0)+\delta(\omega+\omega_0)\right]$ | 广义 |
| $\sin\omega_0t$ | $-j\pi\delta(\omega-\omega_0)+j\pi\delta(\omega+\omega_0)$ | 广义 |
| $H(t)$ | $\dfrac{1}{j\omega}+\pi\delta(\omega)$ | 广义 |
| $e^{-at}H(t)$ | $\dfrac{1}{a+j\omega}$ | $a>0$ |
| $e^{-a\lvert t\rvert}$ | $\dfrac{2a}{a^2+\omega^2}$ | $a>0$ |
| $p_\tau(t)$ | $\tau\operatorname{sinc}\left(\dfrac{\omega\tau}{2\pi}\right)$ | 宽度为 $\tau$ 的矩形 |
| $\dfrac{\sin Wt}{\pi t}$ | $p_{2W}(\omega)$ | — |
| $\dfrac{2a}{t^2+a^2}$ | $2\pi e^{-a\lvert\omega\rvert}$ | $a>0$ |
| $te^{-at}H(t)$ | $\dfrac{1}{(a+j\omega)^2}$ | $a>0$ |
| $\operatorname{sgn}(t)$ | $\dfrac{2}{j\omega}$ | 广义 |
| $1-\dfrac{\lvert t\rvert}{\tau}$（$\lvert t\rvert<\tau$） | $\tau\operatorname{sinc}^2\left(\dfrac{\omega\tau}{2\pi}\right)$ | — |

下面给出表中每个变换对的完整积分推导。每一步都写在同一个多行等式里；常数、正弦、阶跃、符号函数不绝对可积，相关结果按广义函数理解，推导中会用到两个标准极限：

$$\int_{-\infty}^{\infty}e^{-j\Omega t}dt=2\pi\delta(\Omega),\qquad
\lim_{\epsilon\to0^+}\frac{\epsilon}{\epsilon^2+\omega^2}=\pi\delta(\omega).$$

为便于复用前面的积分结果，推导次序与表中次序略有不同。

#### 冲激信号

$$\begin{aligned}
\delta(t-t_0)\longleftrightarrow U(j\omega)
&=\int_{-\infty}^{\infty}\delta(t-t_0)e^{-j\omega t}dt\\
&=\left.e^{-j\omega t}\right|_{t=t_0}\\
&=e^{-j\omega t_0}.
\end{aligned}$$

第一个等号用了筛选性质 $\int_{-\infty}^{\infty}\delta(t-t_0)\varphi(t)dt=\varphi(t_0)$。

令 $t_0=0$，得到 $\delta(t)\leftrightarrow1$。

#### 单边指数

$$\begin{aligned}
e^{-at}H(t)\longleftrightarrow U(j\omega)
&=\int_{-\infty}^{\infty}e^{-at}H(t)e^{-j\omega t}dt\\
&=\int_{0}^{\infty}e^{-(a+j\omega)t}dt\\
&=\left[\frac{e^{-(a+j\omega)t}}{-(a+j\omega)}\right]_{0}^{\infty}\\
&=\frac{1}{a+j\omega}\qquad(a>0),
\end{aligned}$$

因为 $|e^{-(a+j\omega)t}|=e^{-at}$，$a>0$ 时上限代入为零。

#### 双边指数

$$\begin{aligned}
e^{-a|t|}\longleftrightarrow U(j\omega)
&=\int_{-\infty}^{0}e^{at}e^{-j\omega t}dt+\int_{0}^{\infty}e^{-at}e^{-j\omega t}dt\\
&=\int_{-\infty}^{0}e^{(a-j\omega)t}dt+\int_{0}^{\infty}e^{-(a+j\omega)t}dt\\
&=\left[\frac{e^{(a-j\omega)t}}{a-j\omega}\right]_{-\infty}^{0}
+\left[\frac{e^{-(a+j\omega)t}}{-(a+j\omega)}\right]_{0}^{\infty}\\
&=\frac{1}{a-j\omega}+\frac{1}{a+j\omega}\\
&=\frac{(a+j\omega)+(a-j\omega)}{(a-j\omega)(a+j\omega)}\\
&=\frac{2a}{a^2+\omega^2}\qquad(a>0).
\end{aligned}$$

#### 常数

按定义直接计算时，被积函数 $e^{-j\omega t}$ 在 $t\to\pm\infty$ 处不衰减，这个积分要在广义函数意义下理解。常规做法是先把积分截断到有限区间，算出结果再让区间长度趋于无穷：

$$\begin{aligned}
1\longleftrightarrow U(j\omega)
&=\int_{-\infty}^{\infty}1\cdot e^{-j\omega t}dt
=\lim_{T\to\infty}\int_{-T/2}^{T/2}e^{-j\omega t}dt\\
&=\lim_{T\to\infty}\left[\frac{e^{-j\omega t}}{-j\omega}\right]_{-T/2}^{T/2}\\
&=\lim_{T\to\infty}\frac{e^{-j\omega T/2}-e^{j\omega T/2}}{-j\omega}\\
&=\lim_{T\to\infty}\frac{2\sin(\omega T/2)}{\omega}\\
&=2\pi\lim_{T\to\infty}\frac{\sin((T/2)\omega)}{\pi\omega}\\
&=2\pi\delta(\omega).
\end{aligned}$$

最后一步用标准极限 $\lim_{A\to\infty}\frac{\sin A\omega}{\pi\omega}=\delta(\omega)$。这也与矩形脉冲的变换一致：$\int_{-T/2}^{T/2}e^{-j\omega t}dt$ 正是 $p_T(t)$ 的频谱，是一个宽度为 $T$ 的 sinc；$T\to\infty$ 时，时域矩形变成常数，频域 sinc 越来越窄、越来越高，面积恒为 $2\pi$，极限就是冲激。

**验算（逆变换）**。把结果代回逆变换公式，积分是普通的筛选积分，可以精确算出：

$$\begin{aligned}
\frac1{2\pi}\int_{-\infty}^{\infty}2\pi\delta(\omega)e^{j\omega t}d\omega
&=\int_{-\infty}^{\infty}\delta(\omega)e^{j\omega t}d\omega\\
&=\left.e^{j\omega t}\right|_{\omega=0}\\
&=1,
\end{aligned}$$

与 $u(t)=1$ 一致。

**另一种算法：从双边指数取极限。** 对上式令 $a\to0^+$。

时域 $e^{-a|t|}\to1$；

频域中 $2a/(a^2+\omega^2)$ 在 $\omega\ne0$ 处趋于零，而它的面积 $\int_{-\infty}^{\infty}\frac{2a}{a^2+\omega^2}d\omega=2\pi$ 与 $a$ 无关，说明随 $a\to0^+$ 这些面积全部集中到原点，极限为 $2\pi\delta(\omega)$。

因此

$$\begin{aligned}
1\longleftrightarrow U(j\omega)
&=\lim_{a\to0^+}\frac{2a}{a^2+\omega^2}\\
&=2\pi\delta(\omega).
\end{aligned}$$

#### 复指数

$$\begin{aligned}
e^{j\omega_0t}\longleftrightarrow U(j\omega)
&=\int_{-\infty}^{\infty}e^{j\omega_0t}e^{-j\omega t}dt\\
&=\int_{-\infty}^{\infty}e^{-j(\omega-\omega_0)t}dt\\
&=2\pi\delta(\omega-\omega_0).
\end{aligned}$$

最后一个等号用 $\int e^{-j\Omega t}dt=2\pi\delta(\Omega)$，其中 $\Omega=\omega-\omega_0$。

#### 正弦与余弦

$$\begin{aligned}
\cos\omega_0t\longleftrightarrow U(j\omega)
&=\int_{-\infty}^{\infty}\frac12\left(e^{j\omega_0t}+e^{-j\omega_0t}\right)e^{-j\omega t}dt\\
&=\frac12\int_{-\infty}^{\infty}e^{-j(\omega-\omega_0)t}dt
+\frac12\int_{-\infty}^{\infty}e^{-j(\omega+\omega_0)t}dt\\
&=\frac12\cdot2\pi\delta(\omega-\omega_0)
+\frac12\cdot2\pi\delta(\omega+\omega_0)\\
&=\pi\left[\delta(\omega-\omega_0)+\delta(\omega+\omega_0)\right].
\end{aligned}$$

$$\begin{aligned}
\sin\omega_0t\longleftrightarrow U(j\omega)
&=\int_{-\infty}^{\infty}\frac{1}{2j}\left(e^{j\omega_0t}-e^{-j\omega_0t}\right)e^{-j\omega t}dt\\
&=\frac{1}{2j}\int_{-\infty}^{\infty}e^{-j(\omega-\omega_0)t}dt
-\frac{1}{2j}\int_{-\infty}^{\infty}e^{-j(\omega+\omega_0)t}dt\\
&=-j\pi\delta(\omega-\omega_0)+j\pi\delta(\omega+\omega_0)\\
&=-j\pi\left[\delta(\omega-\omega_0)-\delta(\omega+\omega_0)\right].
\end{aligned}$$

这里用了 $1/j=-j$。公式表把它排成 $\sin\omega_0t\leftrightarrow -j\pi\delta(\omega-\omega_0)+j\pi\delta(\omega+\omega_0)$，两者完全等价。

#### 单位阶跃

$$\begin{aligned}
H(t)\longleftrightarrow U(j\omega)
&=\int_{-\infty}^{\infty}H(t)e^{-j\omega t}dt
=\int_{0}^{\infty}e^{-j\omega t}dt\\
&=\lim_{\epsilon\to0^+}\int_{0}^{\infty}e^{-(\epsilon+j\omega)t}dt\\
&=\lim_{\epsilon\to0^+}\frac{1}{\epsilon+j\omega}\\
&=\lim_{\epsilon\to0^+}\left(\frac{\epsilon}{\epsilon^2+\omega^2}
-\frac{j\omega}{\epsilon^2+\omega^2}\right)\\
&=\pi\delta(\omega)+\frac{1}{j\omega}.
\end{aligned}$$

最后一步：第一项用标准极限 $\epsilon/(\epsilon^2+\omega^2)\to\pi\delta(\omega)$；第二项在 $\omega\ne0$ 时 $-\frac{j\omega}{\epsilon^2+\omega^2}\to-\frac{j}{\omega}=\frac{1}{j\omega}$。

#### 符号函数

$$\begin{aligned}
\operatorname{sgn}(t)\longleftrightarrow U(j\omega)
&=\int_{-\infty}^{\infty}\operatorname{sgn}(t)e^{-j\omega t}dt\\
&=\lim_{\epsilon\to0^+}\left[-\int_{-\infty}^{0}e^{(\epsilon-j\omega)t}dt
+\int_{0}^{\infty}e^{-(\epsilon+j\omega)t}dt\right]\\
&=\lim_{\epsilon\to0^+}\left[-\frac{1}{\epsilon-j\omega}
+\frac{1}{\epsilon+j\omega}\right]\\
&=-\frac{1}{-j\omega}+\frac{1}{j\omega}\\
&=\frac{2}{j\omega}.
\end{aligned}$$

#### 乘 $t$ 的指数信号

$$\begin{aligned}
te^{-at}H(t)\longleftrightarrow U(j\omega)
&=\int_{0}^{\infty}te^{-(a+j\omega)t}dt\\
&=\left[-\frac{t\,e^{-(a+j\omega)t}}{a+j\omega}\right]_{0}^{\infty}
+\frac{1}{a+j\omega}\int_{0}^{\infty}e^{-(a+j\omega)t}dt\\
&=0+\frac{1}{a+j\omega}\cdot\frac{1}{a+j\omega}\\
&=\frac{1}{(a+j\omega)^2}\qquad(a>0).
\end{aligned}$$

#### 矩形脉冲

高度为 $1$、脉宽为 $\tau$、关于原点对称的矩形脉冲为

$$p_\tau(t)=\begin{cases}1,&|t|<\tau/2,\\0,&|t|>\tau/2,\end{cases}$$

其中 $\tau$ 是**脉宽**：脉冲从 $t=-\tau/2$ 持续到 $t=\tau/2$，持续时间为 $\tau$，面积也是 $\tau$。若是脉冲串，同样的 $\tau$ 表示每个周期内脉冲的宽度，占空比则为 $d=\tau/T$。

$$\begin{aligned}
p_\tau(t)\longleftrightarrow P_\tau(j\omega)
&=\int_{-\tau/2}^{\tau/2}e^{-j\omega t}dt\\
&=\left[\frac{e^{-j\omega t}}{-j\omega}\right]_{-\tau/2}^{\tau/2}\\
&=\frac{e^{-j\omega\tau/2}-e^{j\omega\tau/2}}{-j\omega}\\
&=\frac{e^{j\omega\tau/2}-e^{-j\omega\tau/2}}{j\omega}\\
&=\frac{2j\sin(\omega\tau/2)}{j\omega}\\
&=\frac{2\sin(\omega\tau/2)}{\omega}\\
&=\tau\frac{\sin(\omega\tau/2)}{\omega\tau/2}
=\tau\operatorname{sinc}\left(\frac{\omega\tau}{2\pi}\right).
\end{aligned}$$

其中 $\operatorname{sinc}(x)=\sin(\pi x)/(\pi x)$ 是本笔记采用的归一化定义。$\omega=0$ 时按极限取值 $P_\tau(0)=\tau$，与脉冲面积一致。第一个零点出现在

$$\frac{\omega\tau}{2}=\pi\quad\Longrightarrow\quad\omega=\frac{2\pi}{\tau}.$$

时域脉冲越窄，频域零点越远，频谱越宽；时域脉冲越宽，频域越窄。这一对关系在滤波器和调制中经常用到。

#### sinc 脉冲

取矩形脉冲的 $\tau=2W$，再对结果应用对偶性质 $U(jt)\leftrightarrow2\pi u(-\omega)$：

$$\begin{aligned}
p_{2W}(t)\longleftrightarrow2W\operatorname{sinc}\left(\frac{\omega W}{\pi}\right)
&=\frac{2\sin(\omega W)}{\omega}\\
\Longrightarrow\quad\frac{2\sin(Wt)}{t}
&\longleftrightarrow2\pi p_{2W}(-\omega)=2\pi p_{2W}(\omega)\\
\Longrightarrow\quad\frac{\sin(Wt)}{\pi t}
&\longleftrightarrow p_{2W}(\omega).
\end{aligned}$$

最后一步是两边同除以 $2\pi$。即频域为宽 $2W$ 的矩形，时域为 sinc 形状。

#### 对偶指数

把双边指数的结果再用一次对偶性质：

$$\begin{aligned}
e^{-a|t|}&\longleftrightarrow\frac{2a}{a^2+\omega^2}\\
\Longrightarrow\quad\frac{2a}{a^2+t^2}
&\longleftrightarrow2\pi e^{-a|-\omega|}=2\pi e^{-a|\omega|}.
\end{aligned}$$

#### 三角脉冲

$$\begin{aligned}
\left(1-\frac{|t|}{\tau}\right)\quad(\lvert t\rvert<\tau)
&\longleftrightarrow U(j\omega)
=\int_{-\tau}^{\tau}\left(1-\frac{|t|}{\tau}\right)e^{-j\omega t}dt\\
&=2\int_{0}^{\tau}\left(1-\frac{t}{\tau}\right)\cos(\omega t)dt\\
&=2\int_{0}^{\tau}\cos(\omega t)dt
-\frac{2}{\tau}\int_{0}^{\tau}t\cos(\omega t)dt\\
&=\frac{2\sin(\omega\tau)}{\omega}
-\frac{2}{\tau}\left[\frac{t\sin(\omega t)}{\omega}
+\frac{\cos(\omega t)}{\omega^2}\right]_{0}^{\tau}\\
&=\frac{2\sin(\omega\tau)}{\omega}
-\frac{2\sin(\omega\tau)}{\omega}
-\frac{2(\cos(\omega\tau)-1)}{\tau\omega^2}\\
&=\frac{2(1-\cos(\omega\tau))}{\tau\omega^2}\\
&=\frac{4\sin^2(\omega\tau/2)}{\tau\omega^2}\\
&=\tau\left[\frac{\sin(\omega\tau/2)}{\omega\tau/2}\right]^2
=\tau\operatorname{sinc}^2\left(\frac{\omega\tau}{2\pi}\right).
\end{aligned}$$

第二个等号利用了被积函数为偶函数：$\int_{-\infty}^{\infty}$ 的积分等于 $[0,\tau]$ 上积分的两倍；$e^{-j\omega t}$ 的虚部 $-\sin(\omega t)$ 与偶函数相乘为奇函数，积分为零。

### 3.5 傅里叶变换的性质

| 性质 | 时域 | 频域 |
|---|---|---|
| 线性 | $au_1+bu_2$ | $aU_1+bU_2$ |
| 时移 | $u(t-t_0)$ | $e^{-j\omega t_0}U(j\omega)$ |
| 频移 | $e^{j\omega_0t}u(t)$ | $U(j(\omega-\omega_0))$ |
| 尺度 | $u(at)$ | $\dfrac{1}{\lvert a\rvert}U\left(j\dfrac{\omega}{a}\right)$ |
| 对偶 | $U(jt)$ | $2\pi u(-\omega)$ |
| 时域卷积 | $u_1(t)*u_2(t)$ | $U_1(j\omega)U_2(j\omega)$ |
| 调制 | $u(t)\cos\omega_0t$ | $\dfrac12U(j(\omega-\omega_0))+\dfrac12U(j(\omega+\omega_0))$ |
| 时域相乘 | $u_1(t)u_2(t)$ | $\dfrac1{2\pi}(U_1*U_2)(j\omega)$ |
| 时间反转 | $u(-t)$ | $U(-j\omega)$ |
| 乘 $t$ | $tu(t)$ | $j\dfrac{d}{d\omega}U(j\omega)$ |
| 微分 | $\dfrac{du}{dt}$ | $j\omega U(j\omega)$ |
| 积分 | $\displaystyle\int_{-\infty}^{t}u(\tau)d\tau$ | $\dfrac{U(j\omega)}{j\omega}+\pi U(0)\delta(\omega)$ |
| 共轭 | $u^*(t)$ | $U^*(-j\omega)$ |

#### 线性

$$au_1+bu_2\longleftrightarrow aU_1+bU_2.$$

**例** 已知 $p_2(t)\leftrightarrow2\operatorname{sinc}\left(\frac{\omega}{\pi}\right)$，$\delta(t-1)\leftrightarrow e^{-j\omega}$，则

$$2p_2(t)-3\delta(t-1)\longleftrightarrow4\operatorname{sinc}\left(\frac{\omega}{\pi}\right)-3e^{-j\omega}.$$

逐项变换、逐项乘系数即可，时域怎样组合，频域就怎样组合。

#### 时移

$$u(t-t_0)\longleftrightarrow e^{-j\omega t_0}U(j\omega).$$

时移不改变幅度谱，只给相位增加 $-\omega t_0$。

**例** 仍用 $p_2(t)\leftrightarrow2\operatorname{sinc}(\omega/\pi)$，把脉冲延后 $3$：

$$p_2(t-3)\longleftrightarrow2\operatorname{sinc}\left(\frac{\omega}{\pi}\right)e^{-j3\omega}.$$

$|U(j\omega)|$ 完全不变；相位多了 $-3\omega$，随频率线性增加。时域延后多少，相位就减多少倍的 $\omega$。

#### 频移

$$e^{j\omega_0t}u(t)\longleftrightarrow U(j(\omega-\omega_0)).$$

频移把整个频谱搬到 $\omega_0$ 附近。调制就是利用这条性质。

**例** 把 $p_2(t)$ 乘以 $e^{j5t}$：

$$e^{j5t}p_2(t)\longleftrightarrow2\operatorname{sinc}\left(\frac{\omega-5}{\pi}\right).$$

原来频谱中心在 $\omega=0$、零点在 $\pm\pi$；现在中心移到 $5$、零点移到 $5\pm\pi$，形状和高度不变。

#### 尺度

$$u(at)\longleftrightarrow\frac1{|a|}U\left(j\frac{\omega}{a}\right).$$

时间压缩（$|a|>1$）使频谱展宽，幅度降低；时间拉伸（$|a|<1$）使频谱变窄，幅度升高。若 $a<0$，还包含时间反转，频谱也要反转。

**例** 把 $p_2(t)$ 在时间上压成 $p_2(3t)$，$a=3$：

$$p_2(3t)\longleftrightarrow\frac13\cdot2\operatorname{sinc}\left(\frac{\omega}{3\pi}\right)=\frac23\operatorname{sinc}\left(\frac{\omega}{3\pi}\right).$$

零点从 $\pm\pi$ 移到 $\pm3\pi$：频谱展宽 $3$ 倍，峰值从 $2$ 降到 $\frac23$，仍是原来的三分之一。

#### 时间反转

$$u(-t)\longleftrightarrow U(-j\omega).$$

**例** $e^{-2t}H(t)\leftrightarrow\frac1{2+j\omega}$，把时间反转得到 $e^{2t}H(-t)$：

$$e^{2t}H(-t)\longleftrightarrow\frac1{2-j\omega}=U(-j\omega).$$

频谱左右翻转。若 $U(j\omega)$ 本身是偶函数（如实偶信号的频谱），反转后频谱不变。

#### 乘 $t$

$$tu(t)\longleftrightarrow j\frac{d}{d\omega}U(j\omega).$$

**例** $e^{-2t}H(t)\leftrightarrow\frac1{2+j\omega}$，乘上 $t$：

$$te^{-2t}H(t)\longleftrightarrow j\frac{d}{d\omega}\frac1{2+j\omega}=j\cdot\frac{-j}{(2+j\omega)^2}=\frac1{(2+j\omega)^2},$$

与 3.4 表中 $te^{-at}H(t)\leftrightarrow\frac1{(a+j\omega)^2}$ 一致。

#### 对偶

若

$$u(t)\longleftrightarrow U(j\omega),$$

则

$$U(jt)\longleftrightarrow2\pi u(-\omega).$$

对偶性质中的 $2\pi$ 和负号都要保留。它是从已知变换对推出新变换对的主要工具。

**例** 已知 $p_2(t)\longleftrightarrow2\operatorname{sinc}(\omega/\pi)=2\frac{\sin\omega}{\omega}$。把频谱表达式作为时间函数 $U(jt)=2\frac{\sin t}{t}$，对偶给出

$$2\frac{\sin t}{t}\longleftrightarrow2\pi p_2(-\omega)=2\pi p_2(\omega).$$

两边除以 $2$：

$$\frac{\sin t}{t}\longleftrightarrow\pi p_2(\omega),$$

即 $\frac{\sin t}{\pi t}\leftrightarrow p_2(\omega)$，正是 $\frac{\sin Wt}{\pi t}\leftrightarrow p_{2W}(\omega)$ 取 $W=1$。

#### 卷积

时域卷积对应频域相乘：

$$u_1(t)*u_2(t)\longleftrightarrow U_1(j\omega)U_2(j\omega).$$

这是 LTI 系统分析的核心。系统输出等于输入与冲激响应的卷积，频域中等于输入频谱乘以频率响应。

**例** $u_1=e^{-2t}H(t)$，$u_2=e^{-3t}H(t)$。频域相乘后做部分分式：

$$U_1U_2=\frac1{(2+j\omega)(3+j\omega)}=\frac1{2+j\omega}-\frac1{3+j\omega}.$$

逐项反变换：

$$u_1*u_2=\left(e^{-2t}-e^{-3t}\right)H(t).$$

直接按定义卷积验证：$t>0$ 时

$$\int_0^t e^{-2\tau}e^{-3(t-\tau)}d\tau=e^{-3t}\int_0^te^{\tau}d\tau=e^{-3t}\left(e^t-1\right)=e^{-2t}-e^{-3t}.$$

#### 相乘

时域相乘对应频域卷积：

$$u_1(t)u_2(t)\longleftrightarrow\frac1{2\pi}(U_1*U_2)(j\omega).$$

调制信号 $u(t)\cos\omega_ct$ 就是时域相乘，频域中把 $U(j\omega)$ 搬到 $\pm\omega_c$ 两侧。

**例** $p_2(t)\cos(10t)$，其中 $p_2(t)\leftrightarrow2\operatorname{sinc}(\omega/\pi)$。用调制形式：

$$\begin{aligned}
p_2(t)\cos10t
&\longleftrightarrow\frac12U(j(\omega-10))+\frac12U(j(\omega+10))\\
&=\operatorname{sinc}\left(\frac{\omega-10}{\pi}\right)+\operatorname{sinc}\left(\frac{\omega+10}{\pi}\right).
\end{aligned}$$

原来位于零频的 sinc 被搬到 $\pm10$ 两侧，形状和宽度不变。

#### 微分

$$u'(t)\longleftrightarrow j\omega U(j\omega).$$

若 $u(t)$ 含有跳变，求导会产生冲激，不能直接只写 $j\omega U$。例如

$$\frac{d}{dt}\left[e^{-3t}H(t)\right]=\delta(t)-3e^{-3t}H(t).$$

逐项变换：

$$1-\frac3{3+j\omega}=\frac{j\omega}{3+j\omega}.$$

这与直接对 $e^{-3t}H(t)$ 用微分性质得到的结果一致。若忽略 $\delta(t)$ 项，就会漏掉高频部分的正确表达。

#### 积分

$$\int_{-\infty}^{t}u(\tau)d\tau\longleftrightarrow\frac{U(j\omega)}{j\omega}+\pi U(0)\delta(\omega).$$

积分性质中的冲激项来自信号的直流分量。若 $U(0)=0$，即信号均值为零，冲激项消失。

**例** $u(t)=\delta(t)$，$U(j\omega)=1$，$U(0)=1\ne0$。积分得 $H(t)$，按公式

$$\int_{-\infty}^{t}\delta(\tau)d\tau=H(t)\longleftrightarrow\frac1{j\omega}+\pi\delta(\omega),$$

与表中 $H(t)$ 一行一致，冲激项正是 $U(0)=1$ 贡献的。若换成零均值信号 $u(t)=\cos t$，$U(0)=0$：

$$\int_{-\infty}^{t}\cos\tau\,d\tau=\sin t\longleftrightarrow -j\pi\delta(\omega-1)+j\pi\delta(\omega+1)=\frac{U(j\omega)}{j\omega},$$

冲激项消失，只剩除以 $j\omega$ 的部分。

#### 共轭

$$u^*(t)\longleftrightarrow U^*(-j\omega).$$

对实信号，$u^*(t)=u(t)$，因此 $U(j\omega)=U^*(-j\omega)$，即频谱共轭对称。

**例** $u(t)=e^{(-2+j3)t}H(t)$：

$$U(j\omega)=\frac1{2+j(\omega-3)}.$$

取共轭得 $u^*(t)=e^{(-2-j3)t}H(t)$，其变换为

$$\frac1{2+j(\omega+3)}.$$

另一方面

$$U^*(-j\omega)=\frac1{2-j(-3-\omega)}=\frac1{2+j(\omega+3)},$$

两者一致。对实信号这一步就退化为 $U(j\omega)=U^*(-j\omega)$：实部偶、虚部奇。

### 3.6 对称性

| 时域 | 频域 |
|---|---|
| $u(t)$ 为实信号 | $U(-j\omega)=U^*(j\omega)$，共轭对称 |
| 实信号 | $\lvert U(j\omega)\rvert$ 为偶函数，$\arg U(j\omega)$ 为奇函数 |
| 实偶信号 | $U(j\omega)$ 为实偶函数 |
| 实奇信号 | $U(j\omega)$ 为纯虚奇函数 |
| 虚信号 | $U(j\omega)$ 为奇函数，实部奇、虚部偶 |

实奇信号的推导：

$$U(j\omega)=\int_{-\infty}^{\infty}u(t)\left[\cos\omega t-j\sin\omega t\right]dt.$$

若 $u(t)$ 为奇函数，则 $u(t)\cos\omega t$ 为奇函数，积分为零；$u(t)\sin\omega t$ 为偶函数，积分保留：

$$U(j\omega)=-2j\int_0^\infty u(t)\sin\omega t\,dt.$$

因此 $U(j\omega)$ 为纯虚数。又因为 $\sin(-\omega t)=-\sin\omega t$，所以

$$U(-j\omega)=-U(j\omega),$$

即频谱关于 $\omega$ 为奇函数。

类似的推导可以得到其余几行。实偶信号的频谱为实偶函数，这一点在判断矩形脉冲、三角脉冲等偶信号的频谱时很有用。

### 3.7 面积定理

由傅里叶变换定义，令 $\omega=0$：

$$U(0)=\int_{-\infty}^{\infty}u(t)dt.$$

由逆变换，令 $t=0$：

$$u(0)=\frac1{2\pi}\int_{-\infty}^{\infty}U(j\omega)d\omega.$$

时域的总面积等于频域在原点的值；时域在原点的值等于频域总面积除以 $2\pi$。这两个关系可以用来快速检查变换结果。

**例 1**　$u(t)=3e^{-2t}H(t)-2e^{-5t}H(t)$。

$$U(0)=\frac32-\frac25=1.1.$$

**例 2**　$U(j\omega)=4$，$|\omega|<1$，其余为零。

$$u(0)=\frac1{2\pi}\cdot4\cdot2=\frac4\pi\approx1.2732.$$

### 3.8 周期信号的傅里叶变换

周期信号的傅里叶变换在 2.11 节已经得到：

$$U(j\omega)=2\pi\sum_{k=-\infty}^{\infty}c_k\delta(\omega-k\omega_0).$$

这里补充谱线图的表示方法和一个完整例子。

同一组傅里叶系数有三种表示：

1. 双边谱线：以 $|c_k|$ 为谱线高度，横轴为 $k\omega_0$。
2. 冲激频谱：以 $2\pi c_k$ 为冲激权重，写成 $U(j\omega)$。
3. 归一化谱线：以 $Tc_k$ 为高度，使离散谱线与连续频谱包络可以直接比较。

三者的关系为

$$2\pi c_k=Tc_k\cdot\omega_0.$$

归一化谱线高度 $Tc_k$ 在 $T\to\infty$ 时趋于连续频谱 $U(j\omega)$。

**例**　周期矩形脉冲串，周期 $T=2.5,5,10$，脉宽 $\tau=1$。

谱线间隔为

$$\omega_0=\frac{2\pi}{T}.$$

三个周期对应的间隔分别为

$$T=2.5:\ \omega_0=2.513,\qquad
T=5:\ \omega_0=1.257,\qquad
T=10:\ \omega_0=0.628\ \mathrm{rad/s}.$$

包络由单个脉冲的频谱决定：

$$U_{\text{env}}(j\omega)=\frac{\sin(\omega/2)}{\omega/2}.$$

包络形状与 $T$ 无关；$T$ 只影响谱线间隔。周期越大，谱线越密，谱线高度按 $1/T$ 降低。

### 3.9 Parseval 定理（能量形式）

对能量信号，

$$E=\int_{-\infty}^{\infty}|u(t)|^2dt=\frac1{2\pi}\int_{-\infty}^{\infty}|U(j\omega)|^2d\omega.$$

更一般地，两个信号的内积满足

$$\int_{-\infty}^{\infty}u(t)\overline{y(t)}dt=\frac1{2\pi}\int_{-\infty}^{\infty}U(j\omega)\overline{Y(j\omega)}d\omega.$$


频域能量密度为

$$\frac{|U(j\omega)|^2}{2\pi}.$$

**例**　$u(t)=\dfrac{\sin3t}{\pi t}$。

由变换对

$$\frac{\sin Wt}{\pi t}\longleftrightarrow p_{2W}(\omega),$$

取 $W=3$，频谱为 $|\omega|<3$ 内的 $1$。能量为

$$E=\frac1{2\pi}\int_{-3}^{3}1\,d\omega=\frac6{2\pi}=\frac3\pi\approx0.9549.$$

周期信号的能量为无穷大，不能使用能量 Parseval 定理。周期信号应使用平均功率形式：

$$P=\sum_k|c_k|^2.$$

### 3.10 傅里叶变换典型例题

**例 1（存在性）**　判断 $\cos5t$、$H(t)$、$1$、$e^{2t}H(t)$ 是否存在傅里叶变换。

$\cos5t$、$H(t)$、$1$ 不满足绝对可积，但可以用广义函数表示：

$$\cos5t\leftrightarrow\pi\left[\delta(\omega-5)+\delta(\omega+5)\right],$$

$$H(t)\leftrightarrow\pi\delta(\omega)+\frac1{j\omega},$$

$$1\leftrightarrow2\pi\delta(\omega).$$

$e^{2t}H(t)$ 的变换积分为

$$\int_0^\infty e^{(2-j\omega)t}dt,$$

因 $\operatorname{Re}(2-j\omega)=2>0$ 而发散，不存在傅里叶变换。

**例 2（实奇信号的频谱）**　$u(-t)=-u(t)$。

$$U(j\omega)=-2j\int_0^\infty u(t)\sin\omega t\,dt.$$

频谱为纯虚奇函数。

**例 3（面积定理）**

$u(t)=3e^{-2t}H(t)-2e^{-5t}H(t)$：

$$U(0)=\frac32-\frac25=1.1.$$

$U(j\omega)=4$，$|\omega|<1$：

$$u(0)=\frac4\pi\approx1.2732.$$

**例 4（矩形脉冲的频谱）**　$p_\tau(t)\leftrightarrow\tau\dfrac{\sin(\omega\tau/2)}{\omega\tau/2}$。

- $\tau=6$：

$$6\cdot\frac{\sin(3\omega)}{3\omega}=2\frac{\sin3\omega}{\omega}.$$

- $\tau=4$，$\omega=\pi/4$：

$$4\cdot\frac{\sin(\pi/2)}{\pi/2}=\frac8\pi\approx2.5465.$$

- $\tau=0.5$ 的第一个零点：

$$\frac{\omega\cdot0.5}{2}=\pi\quad\Longrightarrow\quad\omega=4\pi\approx12.566.$$

**例 5（尺度与时移）**　$y(t)=p_4(2t-4)$。

先做尺度：

$$p_4(2t)\longleftrightarrow\frac12\cdot4\frac{\sin(\omega\cdot4/2/2)}{\omega\cdot4/2/2}=2\frac{\sin\omega}{\omega}.$$

再做时移：

$$p_4(2(t-2))\longleftrightarrow2\frac{\sin\omega}{\omega}e^{-j2\omega}.$$

取 $\omega=\pi/2$：

$$Y(j\pi/2)=2\cdot\frac{2}{\pi}\cdot e^{-j\pi}=-\frac4\pi\approx-1.2732.$$

**例 6（对偶）**　已知

$$e^{-a|t|}\longleftrightarrow\frac{2a}{a^2+\omega^2}.$$

由对偶性质

$$U(jt)\longleftrightarrow2\pi u(-\omega),$$

得到

$$\frac{2a}{t^2+a^2}\longleftrightarrow2\pi e^{-a|\omega|}.$$

**例 7（卷积与相乘）**

$$u_1*u_2\longleftrightarrow U_1U_2,$$

$$u_1u_2\longleftrightarrow\frac1{2\pi}U_1*U_2.$$

时域卷积没有系数，时域相乘带 $1/(2\pi)$。

**例 8（微分含冲激）**　求 $\dfrac{d}{dt}\left[e^{-3t}H(t)\right]$ 的傅里叶变换。

$$\frac{d}{dt}\left[e^{-3t}H(t)\right]=\delta(t)-3e^{-3t}H(t).$$

变换为

$$1-\frac3{3+j\omega}=\frac{j\omega}{3+j\omega}.$$

**例 9（能量 Parseval）**　$u(t)=\dfrac{\sin3t}{\pi t}$。

$$E=\frac1{2\pi}\int_{-3}^{3}1\,d\omega=\frac3\pi\approx0.9549.$$

---

## 4 频率响应

### 4.1 正弦稳态的核心结论

LTI 系统指线性时不变系统：

**线性**要求同时满足叠加性与齐次性，即输入 $u_1\to y_1$、$u_2\to y_2$ 时，$\alpha u_1+\beta u_2\to\alpha y_1+\beta y_2$；**时不变**要求输入延迟多少，输出就延迟多少，即 $u(t)\to y(t)$ 时，$u(t-\tau)\to y(t-\tau)$。这两个

性质对任意输入都成立。

LTI 系统完全由冲激响应决定，原因在于任意输入都可以拆成延迟冲激的叠加。

把 $u(t)$ 在时间轴上切成宽度为 $\Delta\tau$ 的细条，第 $k$ 条位于 $t=\tau_k$、高度为 $u(\tau_k)$，宽度趋于零时它变成一个面积为 $u(\tau_k)\Delta\tau$ 的延迟冲激 $u(\tau_k)\Delta\tau\,\delta(t-\tau_k)$；把所有细条加起来并令 $\Delta\tau\to0$，求和变成积分：

$$u(t)=\int_{-\infty}^{\infty}u(\tau)\,\delta(t-\tau)\,d\tau.$$

这个式子说明，任意波形都只是「不同延迟的冲激」按 $u(\tau)$ 加权后的堆积。

对 LTI 系统，冲激输入产生 $h(t)$（定义），延迟 $\tau$ 的冲激产生 $h(t-\tau)$（时不变性），再按同样的权 $u(\tau)$ 叠加（线性性），输出就是

$$y(t)=\int_{-\infty}^{\infty}u(\tau)h(t-\tau)\,d\tau=(u*h)(t).$$

所以只要测出 $h(t)$ 这一个函数，任意输入的响应都由卷积给出，$h(t)$ 就完整刻画了系统。描述系统的频域特性也从 $h(t)$ 出发。

设 LTI 系统的冲激响应为 $h(t)$，频率响应为

$$G(j\omega)=\int_{-\infty}^{\infty}h(t)e^{-j\omega t}dt.$$

若系统稳定，$G(j\omega)$ 对全部实数 $\omega$ 有定义。

输入正弦

$$u(t)=A\cos(\omega t+\varphi)$$

时，稳态输出仍为同频率正弦：

$$y_{ss}(t)=A|G(j\omega)|\cos\left(\omega t+\varphi+\angle G(j\omega)\right).$$

系统对输入的作用只有两点：

- 幅度乘以 $|G(j\omega)|$。
- 相位加上 $\angle G(j\omega)$。

频率保持不变。

**为什么输出是这个结果：完整推导。**

**第一步：复指数是 LTI 系统的特征函数。** 设输入 $u(t)=e^{j\omega t}$，由卷积

$$y(t)=\int_{-\infty}^{\infty}h(\tau)e^{j\omega(t-\tau)}d\tau
=e^{j\omega t}\int_{-\infty}^{\infty}h(\tau)e^{-j\omega\tau}d\tau
=G(j\omega)e^{j\omega t}.$$

输入复指数，输出只是同一个复指数乘上一个与时间无关的复常数 $G(j\omega)$：频率不变、波形不变，只改变复幅度。

**第二步：把实余弦拆成两个共轭复指数。**

$$u(t)=A\cos(\omega t+\varphi)
=\frac A2e^{j(\omega t+\varphi)}+\frac A2e^{-j(\omega t+\varphi)}
=\frac A2e^{j\varphi}e^{j\omega t}+\frac A2e^{-j\varphi}e^{-j\omega t}.$$

**第三步：由线性性，两项分别乘各自的频率响应。** 第一项频率为 $\omega$，乘 $G(j\omega)$；第二项频率为 $-\omega$，乘 $G(-j\omega)$：

$$y(t)=\frac A2e^{j\varphi}G(j\omega)e^{j\omega t}
+\frac A2e^{-j\varphi}G(-j\omega)e^{-j\omega t}.$$

**第四步：用共轭对称把两项合并。** 冲激响应 $h(t)$ 是实信号，所以

$$G^*(j\omega)=\left(\int_{-\infty}^{\infty}h(t)e^{-j\omega t}dt\right)^*
=\int_{-\infty}^{\infty}h(t)e^{j\omega t}dt=G(-j\omega).$$

于是第二项正好是第一项的复共轭，两项相加等于第一项实部的两倍：

$$y(t)=2\operatorname{Re}\left\{\frac A2e^{j(\omega t+\varphi)}G(j\omega)\right\}.$$

**第五步：把 $G$ 写成极坐标形式。** 令 $G(j\omega)=|G(j\omega)|e^{j\angle G(j\omega)}$，则

$$\frac A2e^{j(\omega t+\varphi)}G(j\omega)
=\frac{A|G(j\omega)|}{2}e^{j\left(\omega t+\varphi+\angle G(j\omega)\right)}.$$

取实部再乘 $2$：

$$y(t)=A|G(j\omega)|\cos\left(\omega t+\varphi+\angle G(j\omega)\right).$$


输入幅度 $A$ 乘以模 $|G(j\omega)|$；输入相位 $\varphi$ 加上辐角 $\angle G(j\omega)$；

角频率 $\omega$ 原样保留。

下面 4.2 的例子中 $|G(j2)|=0.2828$、$\angle G(j2)=-45^\circ$，所以输入 $5\cos(2t+30^\circ)$ 的稳态输出为 $5\cdot0.2828\cos(2t+30^\circ-45^\circ)=1.414\cos(2t-15^\circ)$。

**为什么叫“稳态”。**

先看推导里对输入的假设：输入 $e^{j\omega t}$ 是从 $t=-\infty$ 起一直存在的。这意味着系统在无穷久以前就已经开始接受这个正弦，因“启动”产生的过渡过程早就消失，公式直接给出的是过渡结束后的那部分。

真实电路不是这样工作的：正弦总有一个接入时刻，比如 $t=0$ 时开关合上，输入实际是 $\cos(\omega t)H(t)$（$t<0$ 时为零，$t>0$ 时为正弦）。电路里可能有电容、电感这类储能元件，输出不能立刻跳到最终形状，因此总输出由两部分叠加：

$$y(t)=\underbrace{A|G(j\omega)|\cos\left(\omega t+\varphi+\angle G(j\omega)\right)}_{\text{与输入同频的强迫分量（稳态）}}
+\underbrace{\text{由系统极点决定的固有分量（暂态）}}_{\text{启动引起的过渡过程}}.$$

**从频谱看同一件事。** 余弦的频谱是两根冲激：

$$\cos(\omega_0t+\varphi)\longleftrightarrow\pi\left[e^{j\varphi}\delta(\omega-\omega_0)+e^{-j\varphi}\delta(\omega+\omega_0)\right]$$

（这里用 $\omega_0$ 表示输入频率，以免和变换变量 $\omega$ 混淆）。输出频谱 $Y(j\omega)=G(j\omega)U(j\omega)$ 仍然只有这两根冲激，位置不变，只是各自的复幅度分别被 $G(j\omega_0)$、$G(-j\omega_0)$ 加权。频率之所以不变，就是因为系统只能改变谱线的复幅度，不能移动谱线的位置。

### 4.2 计算步骤

已知 $G(j\omega)$ 和输入正弦时，按以下步骤计算稳态输出：

1. 从输入中读出角频率 $\omega$。只代这个 $\omega$，不要代振幅或其他频率。
2. 把 $j\omega$ 代入 $G(j\omega)$，计算复数 $G(j\omega)$。
3. 求模 $|G(j\omega)|$ 和辐角 $\angle G(j\omega)$。
4. 输出幅度等于输入幅度乘模，输出相位等于输入相位加辐角。

**例**　

$$G(j\omega)=\frac{j\omega+2}{(j\omega)^2+5j\omega+4},\qquad u(t)=5\cos(2t+30^\circ).$$

代入 $\omega=2$：

$$G(j2)=\frac{2+2j}{(2j)^2+5(2j)+4}
=\frac{2+2j}{-4+10j+4}
=\frac{2+2j}{10j}.$$

化简：

$$\frac{2+2j}{10j}=\frac{(2+2j)(-j)}{10}=\frac{2-2j+2}{10}=0.2-0.2j.$$

因此

$$|G(j2)|=\sqrt{0.2^2+0.2^2}=0.2828,$$

$$\angle G(j2)=-45^\circ.$$

稳态输出为

$$y_{ss}(t)=5\cdot0.2828\cos(2t+30^\circ-45^\circ)=1.414\cos(2t-15^\circ).$$

计算复数时，加减法用直角坐标，乘除法用极坐标。若分子或分母是多个因子的乘积，先把每个因子写成极坐标形式，再分别乘除模、加减辐角。

### 4.3 直流输入与 RMS

直流输入 $u(t)=A$ 相当于 $\omega=0$。稳定系统的稳态输出为

$$y_{ss}=A\,G(0).$$

$G(0)$ 称为直流增益。

多个正弦叠加时，分别计算每个频率的响应，再相加。LTI 系统是线性的，不同频率之间不会产生新的频率分量。

正弦信号的 RMS 和平均功率为

$$X_{\mathrm{RMS}}=\frac{Peak}{\sqrt2},\qquad P=\frac{Peak^2}{2},$$

其中 $Peak$ 是正弦的峰值。直流信号 $A$ 的 RMS 为 $A$，平均功率为 $A^2$。

**例**　车辆振动问题中输出峰值为 $1$，则 RMS 为

$$1/\sqrt2\approx0.7071.$$

**例**　输入 $u(t)=|\sin t|$，系统 $G(j\omega)=\dfrac1{1+3j\omega}$。

输入的直流系数为

$$c_0=\frac1\pi\int_0^\pi\sin t\,dt=\frac2\pi.$$

直流增益为 $G(0)=1$。输出直流分量为

$$G(0)c_0=\frac2\pi\approx0.6366.$$

### 4.4 Bode 图

Bode 图用两条曲线表示频率响应：

- 幅频图：纵轴为 $20\log_{10}|G(j\omega)|$，单位 dB；横轴为 $\log\omega$。
- 相频图：纵轴为相位，单位度；横轴为 $\log\omega$。

常用分贝换算：

$$20\log_{10}2\approx6.02\ \mathrm{dB},$$

$$20\log_{10}10=20\ \mathrm{dB},$$

$$20\log_{10}\frac1{\sqrt2}\approx-3.01\ \mathrm{dB}.$$

频率扩大十倍称为一个十倍频程（decade）。

#### 画图步骤

1. 把每个因子写成二阶标准形式。
2. 每个极点贡献 $-20$ dB/dec 的斜率，每个零点贡献 $+20$ dB/dec。
3. 在转折频率处把各段斜率相加。
4. 相位也按各因子叠加。
5. 用低频段和高频段的渐近线检查整体趋势。

渐近线与实际曲线要区分。一阶系统在转折频率处，渐近幅值为 $0$ dB，实际幅值为 $-3$ dB。题目说「读渐近线」时用直线近似，说「实际值」时代公式计算。

**例 1**　12 dB 平台，200 rad/s 后以 $-20$ dB/dec 下降。求 2000 rad/s 处的渐近幅值。

频率从 200 增加到 2000，是一个十倍频程。幅值下降 20 dB：

$$12-20=-8\ \mathrm{dB}.$$

**例 2**　单极点 $\omega_c=1000$，读相位渐近线在 $10000$ 处的值。

斜线段从 $\omega_c/10=100$ 开始，到 $10\omega_c=10000$ 结束，共两个十倍频程。每十倍频程下降 $45^\circ$，共下降 $90^\circ$，所以在 $10000$ 处相位渐近值为 $-90^\circ$。精确值为

$$\arctan(-10)\approx-84.29^\circ,$$

与渐近值有差别。

**例 3**　判断二阶系统的 Bode 图特征。

| 系统 | $\omega_n$ | $\zeta$ | 高频斜率 | 有无共振峰 |
|---|---|---|---|---|
| $\dfrac1{1+j\omega/10}$ | — | — | $-20$ dB/dec | 无 |
| $\dfrac{10^4}{(j\omega)^2+10j\omega+10^4}$ | 100 | 0.05 | $-40$ dB/dec | 有 |
| $\dfrac{100}{(j\omega)^2+20j\omega+100}$ | 10 | 1 | $-40$ dB/dec | 无 |
| 前两者级联 | — | — | $-60$ dB/dec | 有，但被压低 |

判断顺序：先数极点确定高频斜率，再看 $\zeta$ 是否小于 $1/\sqrt2$ 判断有无共振峰。

### 4.5 截止频率

$-3$ dB 截止频率定义为幅值降到直流幅值的 $1/\sqrt2$ 处的频率：

$$\frac{|G(j\omega_c)|}{|G(0)|}=\frac1{\sqrt2}.$$

此时功率降到直流功率的一半：

$$|G(j\omega_c)|^2=\frac{|G(0)|^2}{2}.$$

对一阶低通

$$G(j\omega)=\frac1{1+j\omega/\omega_c},$$

截止频率等于极点频率 $\omega_c$。按公式表的一阶形式

$$G(s)=\frac{K}{\tau s+1},$$

极点实部大小为 $1/\tau$，所以 $\omega_c=1/\tau$。它的阶跃响应在 $t=\tau$ 达到终值的 $63\%$，$10\%\to90\%$ 上升时间 $\approx2.2\tau$，$5\%$ 调节时间 $\approx3\tau$。

**例**　$h(t)=e^{-3t}H(t)$，$G(j\omega)=\dfrac1{3+j\omega}$。

$$|G(j\omega)|=\frac1{\sqrt{9+\omega^2}},\qquad |G(0)|=\frac13.$$

令

$$\frac{|G(j\omega)|}{|G(0)|}=\frac3{\sqrt{9+\omega^2}}=\frac1{\sqrt2}.$$

解得

$$9+\omega^2=18\quad\Longrightarrow\quad\omega=3\ \mathrm{rad/s}.$$

### 4.6 冲激响应与频率响应

冲激响应与频率响应是一对傅里叶变换：

$$h(t)\longleftrightarrow G(j\omega).$$

常用对应：

| $h(t)$ | $G(j\omega)$ |
|---|---|
| $Ae^{-at}H(t)$ | $\dfrac{A}{a+j\omega}$ |
| $\delta(t-t_0)$ | $e^{-j\omega t_0}$ |
| $Ae^{-at}\sin\omega_0t\,H(t)$ | $\dfrac{A\omega_0}{(a+j\omega)^2+\omega_0^2}$ |
| $Ae^{-at}\cos\omega_0t\,H(t)$ | $\dfrac{A(a+j\omega)}{(a+j\omega)^2+\omega_0^2}$ |

级联系统的冲激响应为卷积，频率响应为乘积：

$$h=h_1*h_2,\qquad G=G_1G_2.$$

与 $\delta(t-t_0)$ 卷积相当于把信号延迟 $t_0$：

$$h(t)*\delta(t-t_0)=h(t-t_0).$$

**例**　$G(j\omega)=\dfrac4{j\omega+2}$。

与 $\dfrac{A}{a+j\omega}$ 对照，$A=4$，$a=2$，所以

$$h(t)=4e^{-2t}H(t).$$

**例**　$G(j\omega)=\dfrac3{j\omega+1}+\dfrac2{j\omega+4}$。

逐项反变换：

$$h(t)=3e^{-t}H(t)+2e^{-4t}H(t).$$

**例**　$h_1(t)=2e^{-5t}H(t)$ 与 $\delta(t-3)$ 卷积。

$$h(t)=2e^{-5(t-3)}H(t-3).$$

**例**　$h(t)=4e^{-3t}\sin5t\,H(t)$。

由

$$e^{-at}\sin\omega_0t\,H(t)\longleftrightarrow\frac{\omega_0}{(a+j\omega)^2+\omega_0^2},$$

得

$$G(j\omega)=\frac{4\cdot5}{(3+j\omega)^2+25}=\frac{20}{(3+j\omega)^2+25}.$$

### 4.7 系统对周期信号的作用

设输入为周期信号

$$u(t)=\sum_{k=-\infty}^{\infty}c_ke^{jk\omega_0t}.$$

对稳定 LTI 系统，每个谐波的稳态响应为

$$c_kG(jk\omega_0)e^{jk\omega_0t}.$$

由线性性，输出为

$$y(t)=\sum_{k=-\infty}^{\infty}c_kG(jk\omega_0)e^{jk\omega_0t}.$$

因此输出仍是周期信号，基频不变，输出傅里叶系数为

$$d_k=c_kG(jk\omega_0).$$

系统对每个谐波分别做两件事：幅度乘以 $|G(jk\omega_0)|$，相位加上 $\angle G(jk\omega_0)$。直流分量通过 $G(0)$。

这个结论把傅里叶级数与频率响应连接起来。若系统的频率响应在某个谐波频率处很小，该谐波被抑制；若在某个频率处很大，该谐波被增强。滤波器的基本工作原理就是选择不同的 $G(j\omega)$。

**例**　输入 $u(t)=|\sin t|$，系统 $G(j\omega)=\dfrac1{1+3j\omega}$。

输入的基频为 $\omega_0=2$，直流系数为 $c_0=2/\pi$。输出直流为

$$d_0=c_0G(0)=\frac2\pi.$$

输入的一次谐波系数为

$$c_1=\frac{2}{\pi(1-4)}=-\frac{2}{3\pi}.$$

输出一次谐波系数为

$$d_1=c_1G(j2)=-\frac{2}{3\pi}\cdot\frac1{1+6j}.$$

输出的基频仍为 $2$，但一次谐波的幅度和相位都被系统改变。

### 4.8 频率响应典型例题

**例 1（正弦稳态）**　$G(j\omega)=\dfrac{j\omega+2}{(j\omega)^2+5j\omega+4}$，$u(t)=5\cos(2t+30^\circ)$。

$$G(j2)=0.2-0.2j,$$

$$|G(j2)|=0.2828,\qquad \angle G(j2)=-45^\circ.$$

$$y_{ss}(t)=1.414\cos(2t-15^\circ).$$

**例 2（直流增益）**　$h(t)=3e^{-6t}H(t)$，$u(t)=4$。

$$G(0)=\frac36=0.5,\qquad y_{ss}=4\cdot0.5=2.$$

**例 3（一阶截止）**　$h(t)=e^{-3t}H(t)$。

$$|G(j\omega)|=\frac1{\sqrt{9+\omega^2}},\qquad |G(0)|=\frac13.$$

$$\frac3{\sqrt{9+\omega^2}}=\frac1{\sqrt2}\quad\Longrightarrow\quad\omega=3\ \mathrm{rad/s}.$$

**例 4（Bode 渐近线）**　12 dB 平台，200 rad/s 后 $-20$ dB/dec。

200 到 2000 为一个十倍频程：

$$12-20=-8\ \mathrm{dB}.$$

**例 5（Bode 相位渐近线）**　单极点 $\omega_c=1000$。

斜线段从 100 到 10000，共两个十倍频程，每十倍频程下降 $45^\circ$，在 10000 处相位渐近值为 $-90^\circ$。

**例 6（冲激响应）**

- $G(j\omega)=\dfrac4{j\omega+2}$：

$$h(t)=4e^{-2t}H(t).$$

- $G(j\omega)=\dfrac3{j\omega+1}+\dfrac2{j\omega+4}$：

$$h(t)=3e^{-t}H(t)+2e^{-4t}H(t).$$

- $h_1(t)=2e^{-5t}H(t)$ 与 $\delta(t-3)$ 卷积：

$$h(t)=2e^{-5(t-3)}H(t-3).$$

- $h(t)=4e^{-3t}\sin5t\,H(t)$：

$$G(j\omega)=\frac{20}{(3+j\omega)^2+25}.$$

**例 7（输出直流分量）**　$u(t)=|\sin t|$，$G(j\omega)=\dfrac1{1+3j\omega}$。

$$c_0=\frac2\pi,\qquad G(0)=1,\qquad y_{0}=\frac2\pi\approx0.6366.$$

---

## 5 二阶系统

### 5.1 标准形式

二阶低通的标准形式为

$$G(j\omega)=\frac{K\omega_n^2}{(j\omega)^2+2\zeta\omega_n(j\omega)+\omega_n^2}.$$

把 $j\omega$ 换成 $s$，得到传递函数

$$G(s)=\frac{K\omega_n^2}{s^2+2\zeta\omega_ns+\omega_n^2}.$$

三个参数的含义：

- $\omega_n>0$：自然角频率，决定系统响应的快慢。
- $\zeta$：阻尼比，决定系统振荡的强弱。
- $K$：直流增益。令 $\omega=0$，得

$$G(0)=K.$$

特征方程为

$$s^2+2\zeta\omega_ns+\omega_n^2=0.$$

### 5.2 极点与阻尼

特征方程的根为

$$p_{1,2}=-\zeta\omega_n\pm\omega_n\sqrt{\zeta^2-1}.$$

当 $0<\zeta<1$ 时，根号内为负，极点为一对共轭复数：

$$p_{1,2}=-\zeta\omega_n\pm j\omega_n\sqrt{1-\zeta^2}.$$

| 阻尼比 | 名称 | 极点位置 | 自然响应 |
|---|---|---|---|
| $\zeta=0$ | 无阻尼 | 虚轴上一对共轭极点 $\pm j\omega_n$ | 等幅振荡 |
| $0<\zeta<1$ | 欠阻尼 | 左半平面共轭复极点 | 衰减振荡 |
| $\zeta=1$ | 临界阻尼 | 负实轴上的二重极点 $-\omega_n$ | 无振荡、无超调，衰减最快 |
| $\zeta>1$ | 过阻尼 | 负实轴上两个不同极点 | 无振荡，衰减较慢 |
| $\zeta<0$ | 负阻尼 | 右半平面 | 发散，不稳定 |

几何关系：

- 极点到原点的距离为 $\omega_n$：

$$|p|=\sqrt{(\zeta\omega_n)^2+\omega_n^2(1-\zeta^2)}=\omega_n.$$

- 阻尼比等于极点实部绝对值的相对大小：

$$\zeta=\frac{|\operatorname{Re}p|}{\omega_n}=\cos\theta,$$

其中 $\theta$ 是极点与负实轴的夹角。极点越靠近虚轴，$\theta$ 越接近 $90^\circ$，$\zeta$ 越小，振荡越强。

**例**　极点 $p_{1,2}=-10^4\pm j10^4$。

$$\omega_n=\sqrt{(10^4)^2+(10^4)^2}=\sqrt2\times10^4,$$

$$\zeta=\frac{10^4}{\sqrt2\times10^4}=\frac1{\sqrt2}\approx0.707.$$

### 5.3 共振

二阶低通的幅频特性为

$$|G(j\omega)|=\frac{K}{\sqrt{\left(1-\frac{\omega^2}{\omega_n^2}\right)^2+\left(2\zeta\frac{\omega}{\omega_n}\right)^2}}.$$

令 $x=\omega/\omega_n$，根号内的函数为

$$f(x)=(1-x^2)^2+4\zeta^2x^2.$$

对 $x^2$ 求导并令其为零：

$$\frac{df}{d(x^2)}=-2(1-x^2)+4\zeta^2=0
\quad\Longrightarrow\quad x^2=1-2\zeta^2.$$

因此共振频率为

$$\omega_r=\omega_n\sqrt{1-2\zeta^2}.$$

该频率为正实数的条件是

$$1-2\zeta^2>0\quad\Longrightarrow\quad0<\zeta<\frac1{\sqrt2}\approx0.7071.$$

若 $\zeta\ge1/\sqrt2$，幅频曲线没有非零频率的峰值，最大值在 $\omega=0$ 处。

把 $\omega_r$ 代回幅频表达式，得到共振峰处的幅值：

$$\left|G(j\omega_r)\right|=\frac{|K|}{2\zeta\sqrt{1-\zeta^2}}\qquad\left(\zeta<\frac1{\sqrt2}\right).$$

峰值相对于直流增益的倍数为（公式表写法 $\dfrac{|G(j\omega_r)|}{|K|}$）

$$M_r=\frac{|G(j\omega_r)|}{|K|}=\frac{1}{2\zeta\sqrt{1-\zeta^2}}.$$

分贝值为

$$20\log_{10}M_r.$$

几点结论：

- $\zeta$ 越小，$\omega_r$ 越接近 $\omega_n$，峰值越高。
- $\zeta\to0$ 时，$M_r\to\infty$。
- $\zeta=0.8$ 虽然属于欠阻尼，但 $0.8>1/\sqrt2$，没有共振峰。
- 增益 $K$ 只改变纵轴整体高度，不改变峰值是否存在。

**例**　RLC 串联电路，输出取电容电压。

回路方程给出

$$LC\frac{d^2y}{dt^2}+RC\frac{dy}{dt}+y=u(t).$$

对应传递函数

$$G(s)=\frac{1}{LCs^2+RCs+1}.$$

化为标准形式，分母除以 $LC$：

$$G(s)=\frac{\frac1{LC}}{s^2+\frac{R}{L}s+\frac1{LC}}.$$

与 $s^2+2\zeta\omega_ns+\omega_n^2$ 对照：

$$\omega_n=\frac1{\sqrt{LC}},\qquad 2\zeta\omega_n=\frac RL\quad\Longrightarrow\quad\zeta=\frac{R}{2}\sqrt{\frac CL}.$$

取 $R=200\ \Omega$，$L=0.5\ \mathrm H$，$C=2\ \mu\mathrm F$：

$$\omega_n=\frac1{\sqrt{0.5\times2\times10^{-6}}}=1000\ \mathrm{rad/s},$$

$$\zeta=\frac{200}{2}\sqrt{\frac{2\times10^{-6}}{0.5}}=100\cdot2\times10^{-3}=0.2.$$

由于 $0.2<1/\sqrt2$，存在共振峰：

$$\omega_r=1000\sqrt{1-2(0.2)^2}=1000\sqrt{0.92}\approx959.2\ \mathrm{rad/s},$$

$$M_r=\frac{1}{2(0.2)\sqrt{1-0.2^2}}=\frac{1}{0.4\sqrt{0.96}}\approx2.5516,$$

$$20\log_{10}M_r\approx8.14\ \mathrm{dB}.$$

### 5.4 时域指标

二阶系统

$$G(s)=\frac{K\omega_n^2}{s^2+2\zeta\omega_ns+\omega_n^2},\qquad 0<\zeta<1$$

的时域指标与频域参数是同一组参数的不同表现。

**公式表给的指标：**

- 阻尼自然频率（阻尼振荡频率）：

$$\omega_d=\omega_n\sqrt{1-\zeta^2}.$$

- $5\%$ 误差带下的调节时间（settling time）：

$$t_s\approx\frac{3}{\zeta\omega_n}.$$

- 共振峰（与幅频曲线同一公式）：

$$\frac{|G(j\omega_r)|}{|K|}=\frac{1}{2\zeta\sqrt{1-\zeta^2}},\qquad \omega_r=\omega_n\sqrt{1-2\zeta^2},\quad \zeta<\frac1{\sqrt2}.$$

**由标准二阶响应推出的指标：**

- 超调量：

$$M_p=e^{-\pi\zeta/\sqrt{1-\zeta^2}}.$$

- 峰值时间：

$$t_p=\frac{\pi}{\omega_d}.$$

$\zeta$ 控制振荡和超调，$\omega_n$ 控制响应速度。频域的共振峰与时域的超调都由 $\zeta$ 决定：$\zeta$ 越小，共振峰越高，超调也越大。

**公式表常用数值对照**（表中 $\zeta\le0.707$；$t_s$ 按 $3/(\zeta\omega_n)$ 计算）：

| $\zeta$ | 0.1 | 0.2 | 0.3 | 0.5 | 0.707 |
|---|---|---|---|---|---|
| 超调量 $M_p$ | $73\%$ | $53\%$ | $37\%$ | $16\%$ | $4.3\%$ |
| 共振峰 $\lvert G(j\omega_r)\rvert/\lvert K\rvert$ | $5.03$ | $2.55$ | $1.75$ | $1.15$ | $1.00$ |
| 共振峰高出直流的 dB 值 | $14.0$ | $8.1$ | $4.8$ | $1.2$ | $0$ |

### 5.5 二阶系统典型例题

**例 1（由极点求阻尼）**　$p_{1,2}=-10^4\pm j10^4$。

$$\omega_n=\sqrt{(10^4)^2+(10^4)^2}=\sqrt2\times10^4,$$

$$\zeta=\frac{10^4}{\sqrt2\times10^4}=\frac1{\sqrt2}\approx0.707.$$

**例 2（判断有无共振峰）**　$\zeta=0.8$。

判据为 $0<\zeta<1/\sqrt2\approx0.7071$。由于 $0.8>0.7071$，没有共振峰。代入公式也会得到

$$\omega_r=\omega_n\sqrt{1-2(0.8)^2}=\omega_n\sqrt{-0.28},$$

根号内为负，没有实数解。

**例 3（RLC 串联，取电容电压）**　$R=200\ \Omega$，$L=0.5\ \mathrm H$，$C=2\ \mu\mathrm F$。

$$\omega_n=1000\ \mathrm{rad/s},\qquad \zeta=0.2,$$

$$\omega_r=959.2\ \mathrm{rad/s},\qquad M_r=2.5516,\qquad 20\log_{10}M_r=8.14\ \mathrm{dB}.$$

**例 4（极点位置与峰高）**　极点 $-\alpha\pm j5$。

$$\omega_n=\sqrt{\alpha^2+25},\qquad \zeta=\frac{\alpha}{\omega_n}.$$

| $\alpha$ | $\zeta$ | $M_r$ |
|---|---|---|
| 5 | 0.707 | 无峰 |
| 2 | 0.371 | 1.45 |
| 0.5 | 0.0995 | 5.05 |
| 0.05 | 0.0100 | 50.0 |

极点越靠近虚轴，$\alpha$ 越小，$\zeta$ 越小，峰值越高。

---

## 6 稳定性

### 6.1 三种稳定性

对连续时间 LTI 系统，稳定性按冲激响应的行为定义：

- 指数稳定：存在 $M>0$ 和 $a>0$，使

$$|h(t)|\le Me^{-at}\qquad\forall t\ge0.$$

- 临界稳定（边际稳定）：存在 $M>0$，使

$$|h(t)|\le M\qquad\forall t\ge0,$$

且 $h(t)\not\to0$（$t\to\infty$）。

- BIBO 稳定：对任意有界输入 $\sup_{t\ge0}|u(t)|<\infty$，输出满足 $\sup_{t\ge0}|y(t)|<\infty$。

按极点位置分类：

| 类型 | 极点条件 | 自然响应 |
|---|---|---|
| 指数稳定 | 所有极点严格在左半平面，$\operatorname{Re}(p)<0$ | 所有模态衰减到零 |
| 临界稳定 | 没有右半平面极点，虚轴上的极点都是单根 | 有界，但不衰减 |
| 不稳定 | 有右半平面极点，或虚轴上有重极点 | 发散或增长 |

临界稳定的系统，自然响应有界，但不满足 BIBO 稳定。这个区别在 6.4 节用积分器说明。

### 6.2 BIBO 稳定

BIBO 稳定指对任意有界输入，输出都有界：

$$|u(t)|\le M_u<\infty\quad\forall t
\quad\Longrightarrow\quad|y(t)|\le M_y<\infty\quad\forall t.$$

连续时间 LTI 系统 BIBO 稳定的充要条件是冲激响应绝对可积：

$$\int_{-\infty}^{\infty}|h(t)|dt<\infty.$$

必要性：取有界输入 $u(t)=\operatorname{sgn}\left(h(-t)\right)$，输出在 $t=0$ 处的值为 $\int|h(\tau)|d\tau$，若积分发散则输出无界。

充分性：若输入满足 $|u(t)|\le M_u$，则

$$|y(t)|=\left|\int_{-\infty}^{\infty}h(\tau)u(t-\tau)d\tau\right|
\le M_u\int_{-\infty}^{\infty}|h(\tau)|d\tau,$$

输出有界。

对有理因果系统，冲激响应绝对可积等价于传递函数的所有极点严格位于左半平面。因果系统在虚轴上有单极点时，冲激响应含等幅振荡或常数项，不绝对可积，因此不 BIBO 稳定。

### 6.3 极点判据速查

| 极点情况 | 稳定性 |
|---|---|
| 全部在左半平面 | 渐近稳定，BIBO 稳定 |
| 虚轴上单根，其余在左半平面 | 临界稳定，不 BIBO 稳定 |
| 虚轴上有重根 | 不稳定 |
| 有右半平面极点 | 不稳定 |

**例 1**　

$$G(s)=\frac{s^2+s+1}{(s+2)(s^2+4)}.$$

极点为 $s=-2$ 和 $s=\pm2j$。虚轴上的两个极点都是单根，没有右半平面极点，因此系统临界稳定，但不 BIBO 稳定。冲激响应中含有 $e^{\pm j2t}$ 的等幅振荡项。

**例 2**　

$$G(s)=\frac{s^2+2s+8}{(s+1)(s^2+4)^2}.$$

极点为 $s=-1$ 和 $s=\pm2j$（二重）。虚轴上有重极点，冲激响应含 $t\cos2t$ 型项，随 $t\to\infty$ 幅度增长，因此不稳定。这个例子说明「没有右半平面极点」不足以判定稳定。

**例 3**　一阶系统

$$\tau\dot y=-y+\beta u,\qquad \tau=-4.$$

特征方程为

$$\tau s+1=0\quad\Longrightarrow\quad s=-\frac1\tau=\frac14>0.$$

极点在右半平面，自然响应含 $e^{t/4}$，发散。$\beta$ 只影响受迫响应的幅度，不改变极点位置。

**例 4**　二阶齐次方程

$$a\ddot y+b\dot y+cy=0,\qquad a,b,c>0.$$

特征方程为

$$as^2+bs+c=0.$$

两个根为

$$s_{1,2}=\frac{-b\pm\sqrt{b^2-4ac}}{2a}.$$

若判别式非负，则 $\sqrt{b^2-4ac}<b$，两根均为负实数；若判别式为负，则两个共轭复根的实部为 $-b/(2a)<0$。两种情况下都有 $y(t)\to0$。二阶系统系数全为正时稳定；三阶及以上不能只看系数符号，需要使用 Routh 判据。

### 6.4 积分器与临界稳定

理想积分器的冲激响应和传递函数为

$$h(t)=H(t),\qquad G(s)=\frac1s.$$

极点在 $s=0$，是虚轴上的单根。自然响应为常数，有界，按分类属于临界稳定。但

$$\int_{-\infty}^{\infty}|h(t)|dt=\int_0^\infty1\,dt=\infty,$$

不绝对可积，所以不 BIBO 稳定。输入单位阶跃时，输出为斜坡 $tH(t)$，无界。

这个例子说明临界稳定与 BIBO 稳定不是同一个概念。

### 6.5 零极点抵消

若输入信号的极点与系统的零点相同，输出表达式中会发生零极点抵消：

$$Y(s)=G(s)U(s).$$

例如

$$G(s)=\frac{s-a}{s-a}\cdot\frac1{s+2}.$$

约分后传递函数只剩 $1/(s+2)$，输入中的 $e^{at}$ 模态不出现在输出中。

但系统内部仍有 $s=a$ 这个模态。若 $a>0$，系统内部存在发散模态，只是从输入输出通道看不到。这种情况下，系统不是内部稳定的。

- 输入输出 BIBO 稳定性看约分后的传递函数极点。
- 内部稳定性看约分前的全部自然模态。

题目若只给出 $G(s)$，通常按未约分的极点判断系统稳定性；题目若强调零极点抵消，需要区分输入输出稳定和内部稳定。

### 6.6 稳定性典型例题

**例 1（虚轴单极点）**

$$G(s)=\frac{s^2+s+1}{(s+2)(s^2+4)}.$$

极点为 $-2$ 和 $\pm2j$，均为单根，没有右半平面极点，临界稳定但不 BIBO 稳定。

**例 2（虚轴重极点）**

$$G(s)=\frac{s^2+2s+8}{(s+1)(s^2+4)^2}.$$

极点为 $-1$ 和 $\pm2j$（二重），不稳定。

**例 3（BIBO 稳定判据）**　判断以下系统：

- $s^2-4s+9=0$ 的根为

$$s=\frac{4\pm\sqrt{16-36}}{2}=2\pm j2.236,$$

位于右半平面，不稳定。

- $\dfrac1{s-3}$ 的极点在 $s=3$，不稳定。
- $\dfrac{2s+3}{(s+1)(s+2)}$ 的极点在 $-1$ 和 $-2$，BIBO 稳定。
- $\dfrac3{s(s+2)}$ 在原点有极点，不 BIBO 稳定。

**例 4（冲激响应绝对可积）**

- $h(t)=3e^{-2t}H(t)$：

$$\int_0^\infty3e^{-2t}dt=\frac32<\infty,$$

BIBO 稳定。

- $h(t)=H(t)$：

$$\int_0^\infty1\,dt=\infty,$$

临界稳定但不 BIBO 稳定。

- $h_A(t)=300e^{-4t}H(t)$，$h_B(t)=300e^{4t}H(t)$：

$$\int|h_A|dt=\frac{300}4=75<\infty,\qquad\int|h_B|dt=\infty.$$

只有 $A$ 是 BIBO 稳定的，且

$$G_A(j\omega)=\frac{300}{4+j\omega}$$

存在。

---

## 7 拉普拉斯变换

### 7.1 定义与收敛域

公式表的拉普拉斯变换定义为

$$U(s)=\mathcal L\{u\}(s)=\int_{0^-}^{\infty}u(t)e^{-st}dt,\qquad s=\sigma+j\omega.$$

系统的输入、输出与传递函数满足

$$Y(s)=G(s)U(s),\qquad G(s)=\mathcal L\{h\}(s).$$

双边拉普拉斯变换的下限为 $-\infty$。积分下限写成 $0^-$ 是为了把 $t=0$ 处的冲激包含进来。

拉普拉斯变换比傅里叶变换多了一个实部 $\sigma$。指数因子 $e^{-\sigma t}$ 可以在傅里叶积分发散时把信号压住，因此傅里叶变换无法处理的指数增长信号可以用拉普拉斯变换处理。

**与傅里叶变换的关系**：若收敛域包含虚轴 $s=j\omega$，则

$$U(j\omega)=U(s)\big|_{s=j\omega}.$$

稳定系统的频率响应就是传递函数在虚轴上的取值。

#### 收敛域

收敛域（ROC）是使积分收敛的 $s$ 的集合。

| 信号类型 | ROC |
|---|---|
| 因果信号 $e^{-at}H(t)$ | $\operatorname{Re}(s)>-a$ |
| 反因果信号 $-e^{-at}H(-t)$ | $\operatorname{Re}(s)<-a$ |
| 双边信号 | 带状区域 |
| 有限时长信号 | 整个 $s$ 平面（可能去掉 $s=0$ 或无穷远） |
| 多个信号相加 | 各 ROC 的交集 |

ROC 内不能有极点。同一个 $U(s)$ 配上不同的 ROC，对应不同的时域信号。例如

$$\frac1{s+a}$$

在 $\operatorname{Re}(s)>-a$ 时对应 $e^{-at}H(t)$，在 $\operatorname{Re}(s)<-a$ 时对应 $-e^{-at}H(-t)$。只写 $U(s)$ 而不写 ROC，逆变换不唯一。

### 7.2 常用变换对

| $u(t)$ | $U(s)$ | ROC |
|---|---|---|
| $\delta(t)$ | $1$ | 整个 $s$ 平面 |
| $\delta(t-t_0)$（$t_0\ge0$） | $e^{-st_0}$ | 整个 $s$ 平面 |
| $H(t)$ | $\dfrac1s$ | $\operatorname{Re}(s)>0$ |
| $tH(t)$ | $\dfrac1{s^2}$ | $\operatorname{Re}(s)>0$ |
| $t^nH(t)$ | $\dfrac{n!}{s^{n+1}}$ | $\operatorname{Re}(s)>0$ |
| $e^{-at}H(t)$ | $\dfrac1{s+a}$ | $\operatorname{Re}(s)>-a$ |
| $te^{-at}H(t)$ | $\dfrac1{(s+a)^2}$ | $\operatorname{Re}(s)>-a$ |
| $t^ne^{-at}H(t)$ | $\dfrac{n!}{(s+a)^{n+1}}$ | $\operatorname{Re}(s)>-a$ |
| $\cos\omega_0t\,H(t)$ | $\dfrac{s}{s^2+\omega_0^2}$ | $\operatorname{Re}(s)>0$ |
| $\sin\omega_0t\,H(t)$ | $\dfrac{\omega_0}{s^2+\omega_0^2}$ | $\operatorname{Re}(s)>0$ |
| $e^{-at}\cos\omega_0t\,H(t)$ | $\dfrac{s+a}{(s+a)^2+\omega_0^2}$ | $\operatorname{Re}(s)>-a$ |
| $e^{-at}\sin\omega_0t\,H(t)$ | $\dfrac{\omega_0}{(s+a)^2+\omega_0^2}$ | $\operatorname{Re}(s)>-a$ |

余弦和正弦的变换可以由 $e^{-at}H(t)$ 配合 $s$ 域移位得到。例如

$$\cos\omega_0t=\frac12e^{j\omega_0t}+\frac12e^{-j\omega_0t}.$$

由 $s$ 域移位，

$$e^{j\omega_0t}H(t)\longleftrightarrow\frac1{s-j\omega_0},\qquad
e^{-j\omega_0t}H(t)\longleftrightarrow\frac1{s+j\omega_0}.$$

相加得

$$\cos\omega_0t\,H(t)\longleftrightarrow\frac12\left(\frac1{s-j\omega_0}+\frac1{s+j\omega_0}\right)=\frac{s}{s^2+\omega_0^2}.$$

同理可得正弦的变换。

### 7.3 性质

| 性质 | 时域 | $s$ 域 |
|---|---|---|
| 线性 | $\alpha u_1+\beta u_2$ | $\alpha U_1+\beta U_2$ |
| 时移 | $u(t-t_0)H(t-t_0)$，$t_0\ge0$ | $e^{-st_0}U(s)$ |
| $s$ 域移位 | $e^{-at}u(t)$ | $U(s+a)$ |
| 尺度 | $u(at)$，$a>0$ | $\dfrac1aU\left(\dfrac{s}{a}\right)$ |
| 卷积 | $(h*u)(t)$ | $H(s)U(s)$ |
| 一阶微分 | $\dfrac{d}{dt}u(t)$ | $sU(s)-u(0^-)$ |
| 二阶微分 | $\dfrac{d^2}{dt^2}u(t)$ | $s^2U(s)-su(0^-)-\dot u(0^-)$ |
| 积分 | $\displaystyle\int_{0^-}^{t}u(\varsigma)d\varsigma$ | $\dfrac{U(s)}{s}$ |
| 乘 $t$ | $tu(t)$ | $-\dfrac{dU(s)}{ds}$ |
| 调制 | $u(t)\cos(\omega_0t)$ | $\dfrac12U(s-j\omega_0)+\dfrac12U(s+j\omega_0)$ |

**时移**：单边拉普拉斯变换中，时间延迟必须连同阶跃一起延迟。$u(t-t_0)$ 若在 $t<0$ 时有值，单边变换会多出 $[0^-,t_0]$ 区间的贡献。

**$s$ 域移位**：时域乘 $e^{-at}$，$s$ 域用 $s+a$ 替换 $s$。

**微分**：初始条件通过 $u(0^-)$ 进入。求传递函数时令初始条件为零，才得到

$$Y(s)=G(s)U(s).$$

### 7.4 初值定理与终值定理

**初值定理**：

$$u(0^+)=\lim_{s\to\infty}sU(s).$$

**终值定理**：

$$\lim_{t\to\infty}u(t)=\lim_{s\to0}sU(s).$$

终值定理的使用前提是：$sU(s)$ 的极点全部位于开左半平面，等价地说，$U(s)$ 的极点全部位于左半平面，或在 $s=0$ 处最多有一个单极点。若 $U(s)$ 在虚轴上有非零极点，或在右半平面有极点，响应不会收敛到常数，终值定理失效。

**例**　$U(s)=\dfrac1{s(s+2)}$。

$$u(\infty)=\lim_{s\to0}sU(s)=\lim_{s\to0}\frac1{s+2}=\frac12.$$

$sU(s)=1/(s+2)$ 的极点在 $-2$，满足条件。

**反例**　$U(s)=\dfrac1{s^2+4}$。

$sU(s)=s/(s^2+4)$ 在 $\pm j2$ 有极点，终值定理不适用。时域响应为 $\frac12\sin2t$，不趋于常数。

### 7.5 部分分式分解

求逆变换的流程：

1. 确认 $Y(s)$ 为真分式。假分式先做多项式除法。
2. 分母因式分解，找出所有极点。
3. 按极点类型拆成部分分式。
4. 逐项查变换表。

#### 单实极点

$$\frac1{(s+1)(s+2)}=\frac{A}{s+1}+\frac{B}{s+2}.$$

用遮盖法求 $A$：两边乘 $(s+1)$，令 $s=-1$：

$$A=\left.\frac1{s+2}\right|_{s=-1}=1.$$

同理

$$B=\left.\frac1{s+1}\right|_{s=-2}=-1.$$

因此

$$y(t)=\left(e^{-t}-e^{-2t}\right)H(t).$$

#### 重极点

$$\frac1{(s+1)^2(s+2)}=\frac{A}{s+1}+\frac{B}{(s+1)^2}+\frac{C}{s+2}.$$

$C$ 可以用遮盖法：

$$C=\left.\frac1{(s+1)^2}\right|_{s=-2}=1.$$

$B$ 也可以用遮盖法：

$$B=\left.\frac1{s+2}\right|_{s=-1}=1.$$

$A$ 需要求导：

$$A=\left.\frac{d}{ds}\left[\frac1{s+2}\right]\right|_{s=-1}
=\left.-\frac1{(s+2)^2}\right|_{s=-1}=-1.$$

因此

$$Y(s)=-\frac1{s+1}+\frac1{(s+1)^2}+\frac1{s+2},$$

$$y(t)=\left(-e^{-t}+te^{-t}+e^{-2t}\right)H(t).$$

重极点对应 $te^{-t}$ 型项，不能只写一个指数项。

#### 共轭复极点

$$\frac{1}{s^2+2s+5}=\frac{1}{(s+1)^2+4}.$$

与

$$\frac{\omega_0}{(s+a)^2+\omega_0^2}\longleftrightarrow e^{-at}\sin\omega_0t\,H(t)$$

对照，$a=1$，$\omega_0=2$，因此

$$y(t)=\frac12e^{-t}\sin2t\,H(t).$$

若分子含 $s$ 项，可以拆成 $s+a$ 与常数两部分，分别对应余弦和正弦。

### 7.6 零极点抵消

若

$$Y(s)=\frac{N(s)}{D(s)}\cdot\frac1{s-p_u},$$

且输入极点 $p_u$ 与 $N(s)$ 的零点相同，则约分后输出中不出现 $e^{p_ut}$ 项。

例如

$$Y(s)=\frac{s-1}{(s-1)(s+2)}\cdot\frac1{s+3}=\frac1{(s+2)(s+3)}.$$

输入中的 $e^{-t}$ 项被系统零点抵消，输出只含 $e^{-2t}$ 和 $e^{-3t}$。

零极点抵消改变的是输入输出关系，不改变系统内部的自然模态。若被抵消的极点位于右半平面，系统内部仍然不稳定。

### 7.7 拉普拉斯变换典型例题

**例 1（部分分式与初值）**　$Y(s)=\dfrac{2s+3}{(s+1)(s+2)}$。

拆项：

$$Y(s)=\frac{A}{s+1}+\frac{B}{s+2},$$

$$A=\left.\frac{2s+3}{s+2}\right|_{s=-1}=\frac11=1,$$

$$B=\left.\frac{2s+3}{s+1}\right|_{s=-2}=\frac{-1}{-1}=1.$$

所以

$$y(t)=\left(e^{-t}+e^{-2t}\right)H(t).$$

初值校验：

$$y(0^+)=\lim_{s\to\infty}sY(s)
=\lim_{s\to\infty}\frac{2s^2+3s}{(s+1)(s+2)}=2.$$

直接代入 $y(0^+)=1+1=2$，一致。

终值：

$$y(\infty)=\lim_{s\to0}sY(s)=0,$$

与时域结果一致。

**例 2（重极点）**　$Y(s)=\dfrac1{(s+1)^2(s+2)}$。

由 7.5 节，

$$y(t)=\left(-e^{-t}+te^{-t}+e^{-2t}\right)H(t).$$

**例 3（共轭复极点）**　$Y(s)=\dfrac1{s^2+2s+5}$。

$$y(t)=\frac12e^{-t}\sin2t\,H(t).$$

**例 4（终值定理失效）**　$Y(s)=\dfrac1{s(s^2+4)}$。

$sY(s)=1/(s^2+4)$ 在 $\pm j2$ 有极点，终值定理不能使用。时域响应含等幅正弦项，不趋于常数。

---

## 8 传递函数与滤波器

### 8.1 传递函数

零初始条件下，传递函数定义为

$$G(s)=\frac{Y(s)}{U(s)}.$$

它与冲激响应的关系为

$$G(s)=\mathcal L\{h(t)\}.$$

- 分母的根是极点，决定自然响应的形式和稳定性。
- 分子的根是零点，决定哪些频率分量被抑制。
- 稳定系统令 $s=j\omega$，得到频率响应 $G(j\omega)$。

直流增益为 $G(0)$。高频增益为 $s\to\infty$ 时的极限，它决定系统对高频分量的放大或衰减。

### 8.2 典型滤波器

| 类型 | 通带 | 阻带 | 一阶形式 |
|---|---|---|---|
| 低通 | 低频 | 高频 | $\dfrac{\omega_c}{s+\omega_c}$ |
| 高通 | 高频 | 低频 | $\dfrac{s}{s+\omega_c}$ |
| 带通 | 中间频段 | 高低两端 | 低通与高通级联 |
| 带阻 | 高低两端 | 特定频段 | 分子在阻带中心频率处为零 |
| 全通 | 全部频率 | 无 | 幅值恒定，只改变相位 |

低通在 $\omega=0$ 处 $G(0)=1$，在高频趋于零。高通在 $\omega=0$ 处 $G(0)=0$，在高频趋于 $1$。

全通滤波器的幅值对所有频率为常数：

$$|G(j\omega)|=\text{常数}.$$

它的极点和零点关于虚轴对称。全通滤波器不改变幅度，只改变相位，常用于相位补偿。

滤波器的阶数等于分母的最高次数。阶数越高，过渡带越陡，但实现越复杂。

### 8.3 理想低通滤波器

理想低通的频率响应为

$$H(j\omega)=\begin{cases}1,&|\omega|<\omega_c,\\0,&|\omega|>\omega_c.\end{cases}$$

冲激响应为

$$h(t)=\frac{\sin\omega_ct}{\pi t}.$$

这个函数在 $t<0$ 时已经不为零，因此理想低通是非因果的，物理实时系统无法实现。实际滤波器只能逼近理想特性：通带允许一定起伏，阻带衰减有限，过渡带宽度非零。

### 8.4 $-3$ dB 截止频率

截止频率定义为幅值降到直流幅值的 $1/\sqrt2$ 处的频率：

$$|G(j\omega_c)|=\frac{|G(0)|}{\sqrt2}.$$

此时功率降到一半：

$$|G(j\omega_c)|^2=\frac{|G(0)|^2}{2}.$$

一阶低通的截止频率等于极点频率。二阶低通的截止频率与 $\omega_n$ 和 $\zeta$ 都有关，不能简单取 $\omega_n$。

### 8.5 Butterworth 滤波器

$n$ 阶 Butterworth 低通的幅频特性为

$$|G(j\omega)|^2=\frac1{1+\left(\dfrac{\omega}{\omega_c}\right)^{2n}}.$$

特点：

- 直流处最平坦。前 $2n-1$ 阶导数在 $\omega=0$ 处为零。
- 极点均匀分布在半径为 $\omega_c$ 的左半平面圆上。
- 高频段滚降速率为 $-20n$ dB/dec。
- 在 $\omega=\omega_c$ 处，幅度为 $1/\sqrt2$，即 $-3$ dB。

低通到高通的频率变换为

$$s\to\frac{\omega_c}{s}.$$

这个替换把低频映射到高频，把低通变成同截止频率的高通。若题目出现 $s\to50/s$，说明截止频率为 $\omega_c=50$，即原型低通的参考频率与目标频率的乘积为 $50$。

**公式表给出的阶次实现：**

$$|G(j\omega)|^2=\frac1{1+(\omega/\omega_c)^{2n}}.$$

- $n=1$：$G(s)=\dfrac{\omega_c}{s+\omega_c}$。
- $n=2$：$G(s)=\dfrac{\omega_c^2}{s^2+\sqrt2\,\omega_cs+\omega_c^2}$。
- $n=3$：$G(s)=\dfrac{\omega_c^3}{(s+\omega_c)(s^2+\omega_cs+\omega_c^2)}$。

一般形式（$\zeta_k=\sin\dfrac{(2k-1)\pi}{2n}$）：

$$n\ \text{偶}:\ G(s)=\prod_{k=1}^{n/2}\frac{\omega_c^2}{s^2+2\zeta_k\omega_cs+\omega_c^2},$$

$$n\ \text{奇}:\ G(s)=\frac{\omega_c}{s+\omega_c}\prod_{k=1}^{(n-1)/2}\frac{\omega_c^2}{s^2+2\zeta_k\omega_cs+\omega_c^2}.$$

每一对共轭极点按二阶标准形 $s^2+2\zeta_k\omega_cs+\omega_c^2$ 写出，对应 $\omega_n=\omega_c$、$\zeta_k=\sin\dfrac{(2k-1)\pi}{2n}$。二阶时 $\zeta_1=\sin45^\circ=1/\sqrt2$，正是 $\sqrt2\omega_cs$ 的来源。

### 8.6 滤波器典型例题

**例 1（判断滤波器类型）**　$G(s)=\dfrac{s}{s+10}$。

$G(0)=0$，高频时 $G\to1$，为高通滤波器，截止频率为 $10\ \mathrm{rad/s}$。

**例 2（Butterworth 滚降）**　三阶 Butterworth 低通。

高频段滚降速率为

$$-20\times3=-60\ \mathrm{dB/dec}.$$

在 $\omega=\omega_c$ 处，幅度为 $-3$ dB。

**例 3（一阶低通截止频率）**　$G(s)=\dfrac{100}{s+100}$。

$$|G(j\omega)|=\frac{100}{\sqrt{100^2+\omega^2}},\qquad|G(0)|=1.$$

令

$$\frac{100}{\sqrt{100^2+\omega^2}}=\frac1{\sqrt2},$$

解得 $\omega=100\ \mathrm{rad/s}$，即截止频率等于极点频率。

---

## 9 调制与频分复用

### 9.1 调制的基本概念

基带信号 $u(t)$ 的频谱集中在低频附近。要把信号通过无线信道传输，需要把频谱搬到较高的载波频率附近。这个过程称为调制，载波通常取

$$c(t)=\cos\omega_ct.$$

**公式表把调制分成四种：**

| 类型 | 公式 |
|---|---|
| AM（调幅，DSB-SC） | $y(t)=u(t)\cos(\omega_ct)$，$Y(j\omega)=\frac12U(j(\omega-\omega_c))+\frac12U(j(\omega+\omega_c))$ |
| 解调 | $z(t)=y(t)\cos(\omega_ct)=\frac12u(t)+\frac12u(t)\cos(2\omega_ct)$ |
| FM（调频） | $y(t)=\cos\left(\omega_ct+k\displaystyle\int_{-\infty}^{t}u(\tau)d\tau\right)$ |
| PM（调相） | $y(t)=\cos\left(\omega_ct+ku(t)\right)$ |

FM 与 PM 的调制灵敏度在公式表中统一记作 $k$，不区分 $k_f$、$k_p$；本笔记后面统一用 $k$。

按 AM 公式，调制后的信号为

$$y(t)=u(t)\cos\omega_ct.$$

由相乘性质，

$$Y(j\omega)=\frac1{2\pi}\left[U(j\omega)*\pi\delta(\omega-\omega_c)+\pi\delta(\omega+\omega_c)\right],$$

即

$$Y(j\omega)=\frac12\left[U(j(\omega-\omega_c))+U(j(\omega+\omega_c))\right].$$

基带频谱被搬到 $\pm\omega_c$ 两侧，每侧保留原带宽 $W$，总带宽为

$$B=2W.$$

这是双边带抑制载波（DSB-SC）调制。由于载波本身不传输，发射功率全部用于边带。

### 9.2 相干解调

接收端再乘一次同频同相的载波：

$$y(t)\cos\omega_ct=u(t)\cos^2\omega_ct
=\frac{u(t)}{2}+\frac{u(t)\cos2\omega_ct}{2}.$$

第一项是基带信号，第二项的频谱位于 $\pm2\omega_c$ 附近。用低通滤波器滤除第二项，得到

$$\frac12u(t).$$

再乘 $2$ 即可恢复原信号。相干解调要求接收端产生与发射端同频同相的载波。

### 9.3 带载波 AM

带载波调幅信号为

$$y(t)=\left[A+u(t)\right]\cos\omega_ct.$$

频谱中除了 $\pm\omega_c$ 两侧的边带，还有 $\pm\omega_c$ 处的载波冲激。可以用包络检波解调，电路简单，但载波本身不携带信息，功率利用率较低。

为避免过调制，要求

$$|u(t)|\le A.$$

### 9.4 频分复用

频分复用（FDM）把不同信道的信号调制到不同载波频率上，使各信道频谱占据不同频段，共用一条传输信道。

- 每个 DSB 信道占用带宽 $2W$。
- 相邻信道之间留保护间隔，防止频谱重叠。
- 接收端用带通滤波器选出目标信道，再解调。

广播电台、有线电视和载波电话系统都使用频分复用。

### 9.5 瞬时频率

角度调制信号可以写成

$$y(t)=\cos\theta(t).$$

瞬时角频率定义为相位的导数：

$$\omega_i(t)=\frac{d\theta(t)}{dt}.$$

瞬时频率是相位的导数，不能误写成相位除以时间。

### 9.6 PM 与 FM

**相位调制（PM）**：

$$y(t)=\cos\left(\omega_ct+ku(t)\right).$$

相位为

$$\theta(t)=\omega_ct+ku(t),$$

瞬时角频率为

$$\omega_i(t)=\omega_c+k\dot u(t).$$

**频率调制（FM）**：

$$y(t)=\cos\left(\omega_ct+k\int_{-\infty}^{t}u(\tau)d\tau\right).$$

相位为

$$\theta(t)=\omega_ct+k\int_{-\infty}^{t}u(\tau)d\tau,$$

瞬时角频率为

$$\omega_i(t)=\omega_c+ku(t).$$

对比：

- PM：相位随消息变化，瞬时频率随消息的导数变化。
- FM：相位随消息的积分变化，瞬时频率随消息本身变化。

### 9.7 窄带 FM 与宽带 FM

定义调制指数

$$\beta=\frac{\Delta f}{W},$$

其中 $\Delta f$ 是最大频偏，$W$ 是消息带宽。

**窄带 FM**（$\beta\ll1$）：带宽近似为

$$B\approx2W.$$

窄带 FM 的频谱形状与 AM 相似，但载波与边带的相位关系不同。

**宽带 FM**（$\beta\gg1$）：用 Carson 公式估算带宽：

$$B\approx2(\Delta f+W)=2W(1+\beta).$$

FM 的包络恒定，对幅度噪声不敏感；代价是占用带宽比 AM 宽。

### 9.8 调制典型例题

**例 1（DSB 带宽）**　$u(t)$ 的带宽为 $W=5\ \mathrm{kHz}$，载波为 $100\ \mathrm{kHz}$。

DSB-SC 频谱位于 $100\pm5\ \mathrm{kHz}$ 和 $-100\pm5\ \mathrm{kHz}$，总带宽为

$$B=2W=10\ \mathrm{kHz}.$$

**例 2（相干解调）**　接收信号为 $u(t)\cos\omega_ct$，本地载波为 $\cos\omega_ct$。

乘积为

$$u(t)\cos^2\omega_ct=\frac{u(t)}2+\frac{u(t)\cos2\omega_ct}{2}.$$

低通滤波后得到 $u(t)/2$。

**例 3（瞬时频率）**　$y(t)=\cos(1000t+5\sin10t)$。

相位为

$$\theta(t)=1000t+5\sin10t.$$

瞬时角频率为

$$\omega_i(t)=\frac{d\theta}{dt}=1000+50\cos10t.$$

载波角频率为 $1000\ \mathrm{rad/s}$，最大频偏为 $50\ \mathrm{rad/s}$。

**例 4（FM 带宽）**　$W=1\ \mathrm{kHz}$，$\Delta f=5\ \mathrm{kHz}$。

调制指数为

$$\beta=\frac{\Delta f}{W}=5.$$

由 Carson 公式，

$$B\approx2(\Delta f+W)=2(5+1)=12\ \mathrm{kHz}.$$

---

## 10 信号与系统常用公式与做题流程

### 10.1 傅里叶级数

周期为 $T$、基频为 $\omega_0=2\pi/T$ 的信号（$\phi_k(t)=e^{jk\omega_0t}$）：

$$u(t)=\sum_{k=-\infty}^{\infty}c_ke^{jk\omega_0t},\qquad c_k=\langle u,\phi_k\rangle_P=\frac1T\int_0^Tu(t)e^{-jk\omega_0t}dt.$$

三角形式：

$$u(t)=a_0+\sum_{k=1}^{\infty}\left(a_k\cos(k\omega_0t)+b_k\sin(k\omega_0t)\right),$$

$$a_0=c_0,\qquad a_k=2\operatorname{Re}c_k=\frac2T\int_0^Tu(t)\cos(k\omega_0t)dt,\qquad b_k=-2\operatorname{Im}c_k=\frac2T\int_0^Tu(t)\sin(k\omega_0t)dt.$$

性质：

| 性质 | 结论 |
|---|---|
| $u$ 实 | $c_{-k}=\overline{c_k}$ |
| $u$ 偶 | $b_k=0$ |
| $u$ 奇 | $a_0=a_k=0$ |
| 线性 $\alpha u_1+\beta u_2$ | 系数 $\alpha c_{1,k}+\beta c_{2,k}$ |
| 时移 $u(t-t_0)$ | 系数 $e^{-jk\omega_0t_0}c_k$ |
| Parseval | $P(u)=\dfrac1T\displaystyle\int_0^T|u(t)|^2dt=\sum_{k=-\infty}^{\infty}|c_k|^2$ |

公式表的常用波形：

| 波形 | 系数 |
|---|---|
| $\cos\omega_0t$ | $c_1=c_{-1}=\dfrac12$，其余为零 |
| $\sin\omega_0t$ | $c_1=-\dfrac j2$，$c_{-1}=\dfrac j2$，其余为零 |
| 偶对称方波 $+A$（$\lvert t\rvert<T/4$）、$-A$（$T/4<\lvert t\rvert<T/2$） | $c_k=A\operatorname{sinc}\left(\dfrac k2\right)$（$k$ 奇），$c_k=0$（$k$ 偶） |
| 脉冲串 $Ap_\tau(t)$，$d=\tau/T$ | $c_k=Ad\operatorname{sinc}(kd)$ |
| 三角波 $A(1-4\lvert t\rvert/T)$（$\lvert t\rvert\le T/2$） | $c_k=\dfrac{4A}{\pi^2k^2}$（$k$ 奇），$c_k=0$（$k$ 偶） |
| 全波整流正弦 $A\lvert\sin(\omega_0t)\rvert$，$T=\pi/\omega_0$ | $c_k=\dfrac{2A}{\pi(1-4k^2)}$ |

其中 $\operatorname{sinc}(x)=\dfrac{\sin(\pi x)}{\pi x}$。

### 10.2 傅里叶变换

$$U(j\omega)=\int_{-\infty}^{\infty}u(t)e^{-j\omega t}dt,\qquad u(t)=\frac1{2\pi}\int_{-\infty}^{\infty}U(j\omega)e^{j\omega t}d\omega.$$

周期信号：$U(j\omega)=2\pi\displaystyle\sum_{k=-\infty}^{\infty}c_k\delta(\omega-k\omega_0)$。

| 时域 $u(t)$ | 频域 $U(j\omega)$ | 时域 $u(t)$ | 频域 $U(j\omega)$ |
|---|---|---|---|
| $\delta(t)$ | $1$ | $p_\tau(t)$ | $\tau\operatorname{sinc}\left(\dfrac{\omega\tau}{2\pi}\right)$ |
| $\delta(t-t_0)$ | $e^{-j\omega t_0}$ | $\dfrac{\sin(Wt)}{\pi t}$ | $p_{2W}(\omega)$ |
| $1$ | $2\pi\delta(\omega)$ | $1-\dfrac{\lvert t\rvert}{\tau}$（$\lvert t\rvert<\tau$） | $\tau\operatorname{sinc}^2\left(\dfrac{\omega\tau}{2\pi}\right)$ |
| $e^{j\omega_0t}$ | $2\pi\delta(\omega-\omega_0)$ | $e^{-at}H(t)$（$a>0$） | $\dfrac1{a+j\omega}$ |
| $\cos(\omega_0t)$ | $\pi\delta(\omega-\omega_0)+\pi\delta(\omega+\omega_0)$ | $te^{-at}H(t)$ | $\dfrac1{(a+j\omega)^2}$ |
| $\sin(\omega_0t)$ | $-j\pi\delta(\omega-\omega_0)+j\pi\delta(\omega+\omega_0)$ | $e^{-a\lvert t\rvert}$ | $\dfrac{2a}{a^2+\omega^2}$ |
| $H(t)$ | $\pi\delta(\omega)+\dfrac1{j\omega}$ | $e^{-at}\cos(\omega_0t)H(t)$ | $\dfrac{a+j\omega}{(a+j\omega)^2+\omega_0^2}$ |
| $\operatorname{sgn}(t)$ | $\dfrac2{j\omega}$ | $e^{-at}\sin(\omega_0t)H(t)$ | $\dfrac{\omega_0}{(a+j\omega)^2+\omega_0^2}$ |

性质：

| 运算 | 时域 | 频域 |
|---|---|---|
| 线性 | $\alpha u_1+\beta u_2$ | $\alpha U_1+\beta U_2$ |
| 时移 | $u(t-t_0)$ | $e^{-j\omega t_0}U(j\omega)$ |
| 频移 | $e^{j\omega_0t}u(t)$ | $U(j(\omega-\omega_0))$ |
| 调制 | $u(t)\cos(\omega_0t)$ | $\dfrac12U(j(\omega-\omega_0))+\dfrac12U(j(\omega+\omega_0))$ |
| 尺度 | $u(at)$ | $\dfrac1{\lvert a\rvert}U\left(j\dfrac{\omega}{a}\right)$ |
| 反转 | $u(-t)$ | $U(-j\omega)$ |
| 微分 | $\dfrac{d}{dt}u(t)$ | $j\omega U(j\omega)$ |
| 积分 | $\displaystyle\int_{-\infty}^{t}u(\varsigma)d\varsigma$ | $\dfrac{U(j\omega)}{j\omega}+\pi U(0)\delta(\omega)$ |
| 乘 $t$ | $tu(t)$ | $j\dfrac{d}{d\omega}U(j\omega)$ |
| 卷积 | $(h*u)(t)$ | $H(j\omega)U(j\omega)$ |
| 相乘 | $u(t)y(t)$ | $\dfrac1{2\pi}(U*Y)(j\omega)$ |
| 对偶 | $U(jt)$ | $2\pi u(-\omega)$ |

Parseval：

$$\int_{-\infty}^{\infty}u(t)\overline{y(t)}dt=\frac1{2\pi}\int_{-\infty}^{\infty}U(j\omega)\overline{Y(j\omega)}d\omega,\qquad E(u)=\int_{-\infty}^{\infty}|u(t)|^2dt=\frac1{2\pi}\int_{-\infty}^{\infty}|U(j\omega)|^2d\omega.$$

### 10.3 拉普拉斯变换

$$U(s)=\mathcal L\{u\}(s)=\int_{0^-}^{\infty}u(t)e^{-st}dt,\qquad Y(s)=G(s)U(s),\qquad G(s)=\mathcal L\{h\}(s).$$

| 时域 $u(t)$ | $s$ 域 $U(s)$ | ROC |
|---|---|---|
| $\delta(t)$ | $1$ | 全平面 |
| $\delta(t-t_0)$（$t_0\ge0$） | $e^{-st_0}$ | 全平面 |
| $H(t)$ | $\dfrac1s$ | $\operatorname{Re}s>0$ |
| $tH(t)$ | $\dfrac1{s^2}$ | $\operatorname{Re}s>0$ |
| $t^nH(t)$ | $\dfrac{n!}{s^{n+1}}$ | $\operatorname{Re}s>0$ |
| $e^{-at}H(t)$ | $\dfrac{1}{s+a}$ | $\operatorname{Re}s>-a$ |
| $te^{-at}H(t)$ | $\dfrac{1}{(s+a)^2}$ | $\operatorname{Re}s>-a$ |
| $t^ne^{-at}H(t)$ | $\dfrac{n!}{(s+a)^{n+1}}$ | $\operatorname{Re}s>-a$ |
| $\cos(\omega_0t)H(t)$ | $\dfrac{s}{s^2+\omega_0^2}$ | $\operatorname{Re}s>0$ |
| $\sin(\omega_0t)H(t)$ | $\dfrac{\omega_0}{s^2+\omega_0^2}$ | $\operatorname{Re}s>0$ |
| $e^{-at}\cos(\omega_0t)H(t)$ | $\dfrac{s+a}{(s+a)^2+\omega_0^2}$ | $\operatorname{Re}s>-a$ |
| $e^{-at}\sin(\omega_0t)H(t)$ | $\dfrac{\omega_0}{(s+a)^2+\omega_0^2}$ | $\operatorname{Re}s>-a$ |

性质：

| 性质 | 时域 | $s$ 域 |
|---|---|---|
| 线性 | $\alpha u_1+\beta u_2$ | $\alpha U_1+\beta U_2$ |
| 时移 | $u(t-t_0)H(t-t_0)$，$t_0\ge0$ | $e^{-st_0}U(s)$ |
| $s$ 域移位 | $e^{-at}u(t)$ | $U(s+a)$ |
| 尺度 | $u(at)$，$a>0$ | $\dfrac1aU\left(\dfrac{s}{a}\right)$ |
| 乘 $t$ | $tu(t)$ | $-\dfrac{dU(s)}{ds}$ |
| 一阶微分 | $\dfrac{d}{dt}u(t)$ | $sU(s)-u(0^-)$ |
| 二阶微分 | $\dfrac{d^2}{dt^2}u(t)$ | $s^2U(s)-su(0^-)-\dot u(0^-)$ |
| 积分 | $\displaystyle\int_{0^-}^{t}u(\varsigma)d\varsigma$ | $\dfrac{U(s)}{s}$ |
| 卷积 | $(h*u)(t)$ | $H(s)U(s)$ |
| 调制 | $u(t)\cos(\omega_0t)$ | $\dfrac12U(s-j\omega_0)+\dfrac12U(s+j\omega_0)$ |

初值定理：$u(0^+)=\lim_{s\to\infty}sU(s)$。

终值定理：$\displaystyle\lim_{t\to\infty}u(t)=\lim_{s\to0}sU(s)$，前提是 $sU(s)$ 的全部极点位于开左半平面。

### 10.4 二阶系统

$$G(j\omega)=\frac{K\omega_n^2}{(j\omega)^2+2\zeta\omega_n(j\omega)+\omega_n^2},\qquad G(s)=\frac{K\omega_n^2}{s^2+2\zeta\omega_ns+\omega_n^2},\qquad G(0)=K.$$

- $\zeta>1$：过阻尼，两个不同实极点。
- $\zeta=1$：临界阻尼，重极点 $-\omega_n$。
- $\zeta<1$：欠阻尼，极点 $-\zeta\omega_n\pm j\omega_d$，$\omega_d=\omega_n\sqrt{1-\zeta^2}$。

共振频率与峰值（仅当 $\zeta<\dfrac1{\sqrt2}$）：

$$\omega_r=\omega_n\sqrt{1-2\zeta^2},\qquad \left|G(j\omega_r)\right|=\frac{|K|}{2\zeta\sqrt{1-\zeta^2}}.$$

时域：$M_p=e^{-\pi\zeta/\sqrt{1-\zeta^2}}$，$t_p=\pi/\omega_d$，$5\%$ 调节时间 $t_s\approx\dfrac{3}{\zeta\omega_n}$。

一阶系统 $G(s)=\dfrac{K}{\tau s+1}$：$t=\tau$ 达到终值的 $63\%$，$10\%\to90\%$ 上升时间 $\approx2.2\tau$，$5\%$ 调节时间 $\approx3\tau$。

### 10.5 稳定性

- 指数稳定：存在 $M>0$、$a>0$，使 $|h(t)|\le Me^{-at}$（$t\ge0$）。等价于全部极点位于开左半平面。
- 临界稳定：存在 $M>0$ 使 $|h(t)|\le M$（$t\ge0$），且 $h(t)\not\to0$（$t\to\infty$）。等价于极点在闭左半平面，虚轴上的极点都是单根，且至少有一个虚轴极点。
- BIBO 稳定：对任意有界输入 $\sup_{t\ge0}|u(t)|<\infty$，输出满足 $\sup_{t\ge0}|y(t)|<\infty$。充要条件是 $\int_{-\infty}^{\infty}|h(t)|dt<\infty$；有理因果系统等价于全部极点严格在左半平面。
- 虚轴上有重极点时，$h(t)$ 含 $t\cos\omega t$ 或 $t$ 型项，随时间增长，属于不稳定。

### 10.6 传递函数与滤波器

零初始条件下 $G(s)=Y(s)/U(s)$；稳定系统令 $s=j\omega$ 得频率响应。

| 滤波器 | $G(0)$ | 高频增益 | 典型形式 |
|---|---|---|---|
| 低通 | 有限，常取 $1$ | $0$ | $\dfrac{\omega_c}{s+\omega_c}$ |
| 高通 | $0$ | 有限 | $\dfrac{s}{s+\omega_c}$ |
| 带通 | $0$ | $0$ | 分子含 $s$，分母二阶 |
| 带阻 | 有限 | 有限 | 分子在目标频率处为零 |
| 全通 | 有限 | 与 $G(0)$ 同模 | 极点与零点关于虚轴对称 |

$-3$ dB 频率：$|G(j\omega_c)|=|G(0)|/\sqrt2$，即 $20\log_{10}|G(j\omega_c)|=20\log_{10}|G(0)|-3.01$。

Butterworth 低通：$|G(j\omega)|^2=\dfrac1{1+(\omega/\omega_c)^{2n}}$，高频滚降 $-20n$ dB/dec，$\omega=\omega_c$ 处为 $-3$ dB。

低通原型到高通：$s\to\omega_c/s$；到更低截止频率：$s\to s/\omega_c$。

### 10.7 调制

DSB-SC：$y(t)=u(t)\cos\omega_ct$，频谱搬移到 $\pm\omega_c$，占用带宽 $B=2W$。

相干解调：乘 $\cos\omega_ct$ 后得到 $\frac12u(t)+\frac12u(t)\cos2\omega_ct$，再低通滤波。

AM：$y(t)=[A+u(t)]\cos\omega_ct$，在 $\pm\omega_c$ 处多出载波冲激，可用包络检波。

FDM：每个 DSB 信道占 $2W$，信道间留保护间隔。

瞬时频率：$\omega_i(t)=\dfrac{d\theta(t)}{dt}$。

PM：$\theta(t)=\omega_ct+ku(t)$，$\omega_i=\omega_c+k\dot u(t)$。

FM：$\theta(t)=\omega_ct+k\int_{-\infty}^{t}u(\tau)d\tau$，$\omega_i=\omega_c+ku(t)$。

窄带 FM 带宽 $B\approx2W$；宽带 FM 用 Carson 公式 $B\approx2(\Delta f+W)=2W(1+\beta)$，其中 $\beta=\Delta f/W$。

### 10.8 做题流程

**求周期与基频**：列出非零角频率；分数通分到分母 $D$；对分子求 $\gcd$；$\omega_0=\gcd/D$，$T=2\pi/\omega_0$；检查频率比是否全为有理数。

**求傅里叶级数**：先判断奇偶性和半波对称性，确定哪些系数为零；再用积分或查表求系数；需要三角形式时按 $a_k=2\operatorname{Re}c_k$、$b_k=-2\operatorname{Im}c_k$ 换算；用 Parseval 检查功率。

**求傅里叶变换**：先查变换对，再用时移、尺度、频移、微分、卷积等性质；注意 $2\pi$ 和 $1/(2\pi)$ 的位置；用面积定理检查结果。

**求频率响应**：从输入读出角频率；把 $j\omega$ 代入 $G(j\omega)$ 算复数；求模和辐角；输出幅度乘模、相位加辐角；直流输入用 $G(0)$。

**用拉普拉斯变换求响应**：把初始条件一并变换，解出 $Y(s)$；做部分分式（假分式先做除法）；逐项查表反变换；需要时用初值、终值定理检查。

**判断稳定性**：求全部极点；检查右半平面极点；检查虚轴极点是否重根；需要 BIBO 判定时检查是否全部严格在左半平面。

## 11 拉普拉斯变换补充

### 11.1 收敛域与信号类型

同一个 $U(s)$ 配上不同的收敛域，对应不同的时域信号。这张表把常见情形集中列出，方便对照。

| 信号类型 | 例子 | ROC |
|---|---|---|
| 向右的有限长信号 | $H(t)-H(t-1)$ | 整个 $s$ 平面 |
| 向右的指数衰减 | $e^{-at}H(t)$ | $\operatorname{Re}s>-a$ |
| 向右的指数增长 | $e^{at}H(t)$（$a>0$） | $\operatorname{Re}s>a$ |
| 向左的指数信号 | $-e^{-at}H(-t)$ | $\operatorname{Re}s<-a$ |
| 双边指数 | $e^{-a|t|}$ | $-a<\operatorname{Re}s<a$ |
| 有限个极点相加 | 各项之和 | 各 ROC 的交集 |

ROC 边界总由极点所在的竖直线决定，ROC 内部不能有极点。因果信号的 ROC 是最右侧极点以右，反因果信号的 ROC 是最左侧极点以左。这与公式表一致：$e^{-at}H(t)\leftrightarrow\dfrac1{s+a}$ 要求 $\operatorname{Re}s>-a$，$e^{-at}H(-t)\leftrightarrow-\dfrac1{s+a}$ 要求 $\operatorname{Re}s<-a$。

**例**　$u(t)=3e^{-4t}H(t)-2e^{t}H(t)$。

第一项要求 $\operatorname{Re}s>-4$，第二项要求 $\operatorname{Re}s>1$。两项之和只在交集上收敛：

$$\operatorname{Re}s>1.$$

两个指数一项衰减、一项增长，增长的指数要求更大的实部才能压住，所以 ROC 由增长项决定。

**例**　$u(t)=e^{-2t}H(t)+e^{-5t}H(-t)$。

第一项要求 $\operatorname{Re}s>-2$，第二项是反因果信号，要求 $\operatorname{Re}s<-5$。

两个条件没有交集，所以这个信号不存在拉普拉斯变换，对应的 ROC 为空。

**例**　$u(t)=e^{(-2+5j)t}H(t)$。

指数的实部为 $-2$，虚部 $5j$ 只让信号旋转，不改变它的增长或衰减。判断收敛性只看实部：

$$|u(t)e^{-\sigma t}|=e^{(-2-\sigma)t},$$

当 $\sigma>-2$ 时衰减，所以 ROC 为 $\operatorname{Re}s>-2$。极点位于 $s=-2+5j$，ROC 是过该极点实部的竖直线以右。

**例**　$u(t)=p_2(t-3)$，即宽为 $2$、中心在 $t=3$ 的矩形脉冲。

脉冲在 $2<t<4$ 内为 $1$，写成阶跃之差：

$$u(t)=H(t-2)-H(t-4).$$

逐项变换：

$$U(s)=\frac{e^{-2s}-e^{-4s}}{s}.$$

有限长信号在 $s=0$ 处有可去奇点，在整个 $s$ 平面上收敛。

### 11.2 常用拉普拉斯变换的推导与核对

#### 阶跃与指数

阶跃：

$$H(t)\longleftrightarrow\int_0^\infty e^{-st}dt=\frac1s,\qquad\operatorname{Re}s>0.$$

单边指数：

$$e^{-at}H(t)\longleftrightarrow\int_0^\infty e^{-(s+a)t}dt=\frac1{s+a},\qquad\operatorname{Re}s>-a.$$

#### 正弦与余弦

由欧拉公式和 $s$ 域移位，

$$\cos\omega_0t\,H(t)=\frac12\left(e^{j\omega_0t}+e^{-j\omega_0t}\right)H(t)
\longleftrightarrow\frac12\left(\frac1{s-j\omega_0}+\frac1{s+j\omega_0}\right)=\frac{s}{s^2+\omega_0^2}.$$

同理，

$$\sin\omega_0t\,H(t)\longleftrightarrow\frac1{2j}\left(\frac1{s-j\omega_0}-\frac1{s+j\omega_0}\right)=\frac{\omega_0}{s^2+\omega_0^2}.$$

分母写成 $s^2+\omega_0^2$，是因为 $(s-j\omega_0)(s+j\omega_0)=s^2+\omega_0^2$。若写成 $s^2-\omega_0^2$，说明把 $\omega_0^2$ 前面的符号弄反了。

#### 乘 $t$ 与 $t^n$

由

$$\frac{d}{ds}\frac1{s+a}=-\frac1{(s+a)^2},$$

以及

$$te^{-at}H(t)\longleftrightarrow\frac1{(s+a)^2},$$

得到乘 $t$ 性质：

$$tu(t)\longleftrightarrow-\frac{dU(s)}{ds}.$$

重复使用 $n$ 次：

$$t^ne^{-at}H(t)\longleftrightarrow\frac{n!}{(s+a)^{n+1}}.$$

#### 调制型乘积

求 $\cos3t\cos t\,H(t)$ 这类乘积，先用积化和差把乘积化成两个同频余弦之和：

$$\cos3t\cos t=\frac12\cos4t+\frac12\cos2t.$$

逐项变换：

$$\cos3t\cos t\,H(t)\longleftrightarrow\frac12\cdot\frac{s}{s^2+16}+\frac12\cdot\frac{s}{s^2+4}.$$

注意不能把两个变换直接相乘。时域相乘对应的是 $s$ 域卷积，不是乘积。

#### 时移与阶跃延迟

若 $u(t)$ 的变换为 $U(s)$，则

$$u(t-\tau)H(t-\tau)\longleftrightarrow e^{-s\tau}U(s).$$

时移时阶跃也要一起延迟，否则 $u(t-\tau)$ 在 $t<0$ 时的取值会被截掉。

反过来，看到 $e^{-3s}/(s+1)$，应当认出这是 $e^{-t}H(t)$ 延迟 $3$：

$$e^{-(t-3)}H(t-3).$$

若误写成 $e^{-t}H(t-3)$，只延迟了阶跃没有延迟指数；若写成 $e^{-(t+3)}H(t)$，只把指数前移了，都不是原来的信号。

#### 积分与微分

在 $0$ 到 $t$ 上积分，$s$ 域除以 $s$：

$$\int_0^tu(\tau)d\tau\longleftrightarrow\frac{U(s)}{s}.$$

例如 $\cos3t\,H(t)$ 的变换为 $s/(s^2+9)$，积分后为

$$\int_0^t\cos3\tau\,d\tau=\frac13\sin3t\longleftrightarrow\frac{s}{s^2+9}\cdot\frac1s=\frac1{s^2+9}.$$

微分则乘 $s$ 并减去初始值：

$$\dot u(t)\longleftrightarrow sU(s)-u(0^-).$$

### 11.3 拉普拉斯变换与系统

#### 冲激响应与阶跃响应

$$G(s)=\mathcal L\{h(t)\}.$$

公式表把输入、输出与传递函数写成

$$Y(s)=G(s)U(s),\qquad G(s)=\mathcal L\{h\}(s),$$

因此单位阶跃输入 $U(s)=1/s$ 时 $Y(s)=G(s)/s$，即阶跃响应是冲激响应的积分：

$$y_{\text{step}}(t)=\int_0^th(\tau)d\tau,\qquad Y_{\text{step}}(s)=\frac{G(s)}{s}.$$

所以反过来，

$$h(t)=\frac{d}{dt}y_{\text{step}}(t).$$

若阶跃响应为 $(e^{-t}-e^{-2t})H(t)$，求导得冲激响应：

$$h(t)=\left(-e^{-t}+2e^{-2t}\right)H(t).$$

阶跃响应在 $t=0$ 处从零开始，没有冲激，所以求导只需对 $t>0$ 的表达式求导。

#### 用拉普拉斯变换解微分方程

含初始条件时，把各项一起变换。以

$$\ddot y+5\dot y+6y=6u(t),\qquad u(t)=H(t),\quad y(0^-)=2,\quad\dot y(0^-)=-1$$

为例。

逐项变换：

$$s^2Y-2s+1+5(sY-2)+6Y=\frac6s.$$

整理左边：

$$(s^2+5s+6)Y-2s-9=\frac6s.$$

把初始条件项移到右边：

$$(s^2+5s+6)Y=\frac6s+2s+9.$$

部分分式：

$$Y=\frac{2s^2+9s+6}{s(s+2)(s+3)}
=\frac1s+\frac{2}{s+2}-\frac1{s+3}.$$

反变换：

$$y(t)=1+2e^{-2t}-e^{-3t}\qquad(t\ge0).$$

代入 $t=1$：

$$y(1)=1+2e^{-2}-e^{-3}\approx1.221.$$

#### 零输入响应与零状态响应

线性系统可以分开处理：

$$Y(s)=\underbrace{\frac{\text{初始条件项}}{\text{特征多项式}}}_{Y_{zi}(s)}
+\underbrace{\frac{\text{输入项}}{\text{特征多项式}}}_{Y_{zs}(s)}.$$

零输入响应的形式由极点决定，系数由初始条件决定；零状态响应的形式由系统极点和输入极点共同决定。

若两者恰好抵消，输出可能只剩常数。例如

$$\ddot y+4\dot y+4y=2H(t),\qquad y(0^-)=0.5,\quad\dot y(0^-)=0,$$

变换后

$$(s+2)^2Y=\frac2s+0.5s+2=\frac{0.5(s+2)^2}{s},$$

所以 $Y=0.5/s$，输出为常数 $0.5$。系统从平衡点出发，输入正好维持这个平衡，瞬态项全部抵消。

#### 初值和终值

初值定理：

$$y(0^+)=\lim_{s\to\infty}sY(s).$$

终值定理：

$$y(\infty)=\lim_{s\to0}sY(s),$$

前提是 $sY(s)$ 的极点全部在开左半平面。

**例**　$G(s)=\dfrac{s+1}{s+10}$，输入为单位阶跃。

$$Y(s)=\frac{s+1}{s(s+10)},\qquad sY(s)=\frac{s+1}{s+10}.$$

初值：

$$y(0^+)=\lim_{s\to\infty}\frac{s+1}{s+10}=1.$$

终值：

$$y(\infty)=\lim_{s\to0}\frac{s+1}{s+10}=\frac1{10}.$$

阶跃刚加上时，电容来不及充电，输出跳到 $1$，这是分子分母同阶造成的直通；最终趋于直流增益 $G(0)=0.1$。

**例**　$G(s)=\dfrac{120}{s^2+6s}$，输入为冲激。

$$sG(s)=\frac{120}{s+6},$$

极点在 $-6$，满足终值定理。于是

$$h(\infty)=\lim_{s\to0}\frac{120}{s+6}=20.$$

**例（终值定理失效）**　$G(s)=\dfrac{3}{s^2+4}$ 的冲激响应为 $\frac32\sin2t$，没有极限。原因在于 $sG(s)=\dfrac{3s}{s^2+4}$ 在 $\pm2j$ 有极点，不满足终值定理的条件。此时直接代数计算会得到 $0$，这是错误结果。

### 11.4 部分分式

#### 遮盖法求单实极点

$$Y(s)=\frac{N(s)}{\prod_i(s-p_i)}.$$

对于单极点 $p_i$，两边乘以 $(s-p_i)$ 再令 $s=p_i$：

$$A_i=\left.(s-p_i)Y(s)\right|_{s=p_i}.$$

例如

$$\frac{s+2}{s(s+1)}=\frac{A}{s}+\frac{B}{s+1},$$

$$A=\left.\frac{s+2}{s+1}\right|_{s=0}=2,\qquad B=\left.\frac{s+2}{s}\right|_{s=-1}=-1.$$

反变换：

$$h(t)=\left(2-e^{-t}\right)H(t).$$

#### 重极点

$$Y(s)=\frac{1}{(s+1)^2(s+2)}=\frac{A}{s+1}+\frac{B}{(s+1)^2}+\frac{C}{s+2}.$$

$C$ 和 $B$ 可以直接遮盖：

$$C=\left.\frac1{(s+1)^2}\right|_{s=-2}=1,\qquad B=\left.\frac1{s+2}\right|_{s=-1}=1.$$

$A$ 需要求导：

$$A=\left.\frac{d}{ds}\frac1{s+2}\right|_{s=-1}=\left.-\frac1{(s+2)^2}\right|_{s=-1}=-1.$$

反变换：

$$y(t)=\left(-e^{-t}+te^{-t}+e^{-2t}\right)H(t).$$

重极点对应 $t^ne^{pt}$ 型项。若极点重数为 $m$，部分分式里要写出 $(s-p)^{-1}$ 到 $(s-p)^{-m}$ 的所有项。

#### 共轭复极点

$$Y(s)=\frac{3s+1}{(s+1)(s^2+2s+5)}.$$

先用遮盖法求实极点部分：

$$A=\left.\frac{3s+1}{s^2+2s+5}\right|_{s=-1}=\frac{-2}{4}=-0.5.$$

剩下的部分配成完全平方：

$$Y(s)=-\frac{0.5}{s+1}+\frac{0.5s+3.5}{(s+1)^2+4}.$$

再把分子拆成 $(s+a)$ 项和常数项：

$$\frac{0.5s+3.5}{(s+1)^2+4}
=0.5\frac{s+1}{(s+1)^2+4}+1.5\frac{2}{(s+1)^2+4}.$$

逐项反变换：

$$y(t)=-0.5e^{-t}+0.5e^{-t}\cos2t+1.5e^{-t}\sin2t\qquad(t\ge0).$$

这里 $1.5$ 这个系数来自常数项除以 $\omega_0=2$。

#### 有延迟因子的部分分式

$$Y(s)=\frac{4e^{-s}}{(s+1)(s+3)}.$$

先不管 $e^{-s}$，对有理部分分式：

$$\frac{4}{(s+1)(s+3)}=\frac{2}{s+1}-\frac{2}{s+3}.$$

再整体延迟 $1$：

$$y(t)=\left[2e^{-(t-1)}-2e^{-3(t-1)}\right]H(t-1).$$

延迟因子乘在整个信号上，所以每一项都延迟，阶跃也一起延迟。

### 11.5 系统分析典型例题

**例 1（系统极点与输入极点重合）**　$G(s)=\dfrac{s+4}{s^2+3s+2}$，输入 $u(t)=e^{-2t}H(t)$。

系统极点为 $-1,-2$，输入极点为 $-2$，与系统极点重合，所以 $Y(s)$ 中会出现二重极点：

$$Y(s)=\frac{s+4}{(s+1)(s+2)^2}
=\frac{3}{s+1}-\frac{3}{s+2}-\frac{2}{(s+2)^2}.$$

反变换：

$$y(t)=3e^{-t}-3e^{-2t}-2te^{-2t}\qquad(t\ge0).$$

二重极点对应 $te^{-2t}$ 项，这是共振在拉普拉斯域的表现。输入频率与系统自然频率相同时，响应会多出一个随时间线性增长的项。

**例 2（零点抵消输入极点）**　$G(s)$ 的极点在 $-2,-5$，零点在 $-1$，直流增益为 $3$，输入 $u(t)=e^{-t}H(t)$。

先定增益：

$$G(s)=\frac{k(s+1)}{(s+2)(s+5)},\qquad G(0)=\frac{k}{10}=3\quad\Longrightarrow\quad k=30.$$

于是

$$Y(s)=G(s)U(s)=\frac{30(s+1)}{(s+2)(s+5)}\cdot\frac1{s+1}
=\frac{30}{(s+2)(s+5)}.$$

零点把输入极点抵消了，输出中不含 $e^{-t}$ 项：

$$Y(s)=\frac{10}{s+2}-\frac{10}{s+5},\qquad y(t)=10\left(e^{-2t}-e^{-5t}\right)H(t).$$

这说明系统可以完全抑制某一个输入模态。

**例 3（由输出反求输入）**　$G(s)=\dfrac{4}{s^2+2s+4}$，希望输出为 $y(t)=\left(1-e^{-4t}\right)H(t)$，求输入。

先写出输出的变换：

$$Y(s)=\frac1s-\frac1{s+4}=\frac4{s(s+4)}.$$

由 $Y(s)=G(s)U(s)$ 解出输入：

$$U(s)=\frac{Y(s)}{G(s)}
=\frac{4}{s(s+4)}\cdot\frac{s^2+2s+4}{4}
=\frac{s^2+2s+4}{s(s+4)}.$$

分子次数等于分母次数，先做多项式除法：

$$U(s)=1+\frac{s^2+2s+4-s(s+4)}{s(s+4)}
=1+\frac{-2s+4}{s(s+4)}.$$

再对真分式部分分式：

$$\frac{-2s+4}{s(s+4)}=\frac{1}{s}-\frac{3}{s+4}.$$

反变换：

$$u(t)=\delta(t)+\left(1-3e^{-4t}\right)H(t).$$

这里的冲激来自 $U(s)$ 中的常数项，省略它会导致反变换出来的信号缺少一部分。

### 11.6 二阶系统与稳定性的补充例题

**例 1（由极点判断稳定类型）**　$G(s)=\dfrac{6}{s^2+4}$。

极点为 $\pm2j$，是虚轴上的单极点。冲激响应为

$$h(t)=3\sin2t\,H(t),$$

有界但不衰减，也不绝对可积。所以系统临界稳定，但不是 BIBO 稳定。

**例 2（虚轴单极点与原点极点）**　极点在 $0$ 和 $-0.2\pm j$。

$-0.2\pm j$ 在开左半平面，$0$ 是虚轴上的单极点，所以系统临界稳定。$h(t)$ 中含一个非零常数项，积分

$$\int_0^\infty|h(t)|dt$$

发散，因此不是 BIBO 稳定。

**例 3（判断临界稳定）**

- $\dfrac{s+2}{(s^2+4)(s+1)}$：极点为 $\pm2j$（单根）和 $-1$，临界稳定。
- $\dfrac{s-2}{(s+1)(s+3)}$：两个极点都在开左半平面，指数稳定；零点 $+2$ 不影响稳定性。
- $\dfrac{s+2}{s^2(s+3)}$：$s=0$ 是二重极点，$h(t)$ 含 $t$ 型项，不稳定。
- $\dfrac{s+2}{(s^2+4)^2}$：$\pm2j$ 是二重极点，$h(t)$ 含 $t\sin2t$，不稳定。

**例 4（四阶多项式的极点）**　$G(s)=\dfrac{1}{s^4+4}$。

利用 $s^4+4=(s^2+2s+2)(s^2-2s+2)$。两个二次因子的根分别为 $-1\pm j$ 和 $1\pm j$。后一对在右半平面，所以系统不稳定。

所有系数为正不代表稳定。这个例子中 $s^3$、$s^2$、$s$ 的系数都是零，只看系数符号会漏掉右半平面的极点。

**例 5（共振输入）**　$G(s)=\dfrac{1}{s^2+9}$，输入 $\cos3t\,H(t)$。

输入极点 $\pm3j$ 与系统极点重合：

$$Y(s)=\frac{s}{(s^2+9)^2},\qquad y(t)=\frac{t}{6}\sin3t\,H(t).$$

输出随时间增长，无界。输入振幅有界，输出却无界，这是因为系统不满足 BIBO 稳定（虚轴上单极点）。

**例 6（零点靠近极点）**　$G(s)=\dfrac{s+3}{(s+1)(s+3.1)}$。

零点 $-3$ 非常靠近极点 $-3.1$。求 $e^{-3.1t}$ 项的系数，用遮盖法：

$$A_{3.1}=\left.\frac{s+3}{s+1}\right|_{s=-3.1}
=\frac{-0.1}{-2.1}\approx0.04762.$$

零点越靠近极点，对应模态的系数越小。若零点与极点完全重合，该模态会被完全抵消。

### 11.7 频率响应与滤波器的补充

**例 1（一阶系统幅频曲线）**　$G(s)=\dfrac{1}{s+2}$。

$$|G(j\omega)|=\frac1{\sqrt{4+\omega^2}},\qquad G(0)=\frac12.$$

$-3$ dB 频率满足

$$\frac{|G(j\omega_c)|}{|G(0)|}=\frac{2}{\sqrt{4+\omega_c^2}}=\frac1{\sqrt2},$$

解得 $\omega_c=2$。一阶低通的截止频率等于极点频率。

**例 2（二阶低通的截止频率）**　$G(s)=\dfrac{400}{s^2+20s+400}$。

这里 $\omega_n=20$，$\zeta=0.5$。令 $x=(\omega/\omega_n)^2$，幅频平方为

$$|G|^2=\frac{1}{(1-x)^2+0.25x}.$$

令 $|G|^2=1/2$，数值求解得 $x\approx1.618$。于是

$$\omega_c=\omega_n\sqrt{x}=20\sqrt{1.618}\approx25.44\ \mathrm{rad/s}.$$

二阶低通的 $-3$ dB 频率与 $\omega_n$ 不同，不能直接取 $\omega_n$。

**例 3（一阶高通的衰减）**　$G(s)=\dfrac{s}{s+\omega_c}$，$\omega_c=2\pi\times100$，输入为 $50$ Hz。

$$\frac{\omega}{\omega_c}=\frac{50}{100}=0.5,\qquad |G|=\frac{0.5}{\sqrt{1+0.5^2}}=0.4472.$$

衰减量为

$$-20\log_{10}0.4472\approx6.99\ \mathrm{dB}.$$

**例 4（由指标反求参数）**　$G(s)=\dfrac{k}{s+a}$，要求直流增益 $+12$ dB，且在 $1$ kHz 处下降 $3$ dB。

$+12$ dB 对应

$$\frac{k}{a}=10^{12/20}=3.981.$$

$3$ dB 下降出现在 $\omega=a$，所以

$$a=2\pi\times1000=6283\ \mathrm{rad/s},\qquad k=3.981\times6283=2.501\times10^4.$$

**例 5（全通滤波器的相移）**　$G(s)=\dfrac{10-s}{s+10}$，输入 $\cos10t$。

$$G(j10)=\frac{10-10j}{10+10j}=-j.$$

模为 $1$，相位为 $-90^\circ$，所以输出为

$$y(t)=\cos(10t-90^\circ)=\sin10t.$$

全通滤波器不改变幅度，只改变相位。在 $\omega=10$ 处相位恰好为 $-90^\circ$。

**例 6（延迟线）**　$y(t)=u(t-2)$，$G(s)=e^{-2s}$。

$$G(j\omega)=e^{-j2\omega},\qquad |G(j\omega)|=1,\quad \angle G(j\omega)=-2\omega.$$

幅度恒定，相位与频率成线性关系，所以这是全通系统，相位延迟为 $2$ 秒。

**例 7（Notch 滤波器）**

$$G(s)=\frac{s^2+\omega_n^2}{s^2+2\zeta\omega_ns+\omega_n^2},\qquad \omega_n=2\pi\times50,\quad\zeta=0.5.$$

求 $25$ Hz 处的幅度。令 $\omega=\omega_n/2$：

$$G(j\omega_n/2)=\frac{0.75\omega_n^2}{0.75\omega_n^2+j0.5\omega_n^2}.$$

$$|G|=\frac{0.75}{\sqrt{0.75^2+0.5^2}}=\frac{0.75}{\sqrt{0.8125}}\approx0.8321.$$

在 $\omega=\omega_n$ 处分子为零，幅度为零，正好滤掉 $50$ Hz。

### 11.8 滤波器设计补充

**例 1（一阶低通到高通）**　$G(s)=\dfrac{1}{s+1}$ 是高通还是低通？换成 $s\to1/s$ 后是什么？

原式 $G(0)=1$、高频趋于 $0$，是低通。

做替换：

$$G\left(\frac1s\right)=\frac{1}{1/s+1}=\frac{s}{s+1}.$$

$G(0)=0$、高频趋于 $1$，是高通，截止频率仍为 $1\ \mathrm{rad/s}$。

**例 2（Butterworth 原型到高通）**　二阶 Butterworth 低通原型

$$G_{LP}(s)=\frac{1}{s^2+\sqrt2s+1}.$$

把 $s$ 换成 $50/s$：

$$G_{HP}(s)=\frac{1}{\dfrac{2500}{s^2}+\dfrac{50\sqrt2}{s}+1}
=\frac{s^2}{s^2+50\sqrt2s+2500}.$$

分子分母同乘 $s^2$ 得到分母中间项 $50\sqrt2\approx70.71$，常数项 $50^2=2500$。

**例 3（二阶 Butterworth 的阻尼比）**　二阶 Butterworth 分母

$$s^2+\sqrt2\omega_cs+\omega_c^2.$$

与标准形式 $s^2+2\zeta\omega_ns+\omega_n^2$ 对照：

$$\omega_n=\omega_c,\qquad 2\zeta\omega_n=\sqrt2\omega_c\quad\Longrightarrow\quad\zeta=\frac1{\sqrt2}.$$

所以 Butterworth 二阶系统的阻尼比固定为 $1/\sqrt2\approx0.7071$。这也是它没有共振峰的分界值。

**例 4（由极点求二阶 Butterworth 的截止频率）**　极点 $-10^4\pm j10^4$。

$$\omega_n=\sqrt{(10^4)^2+(10^4)^2}=\sqrt2\times10^4,\qquad
\zeta=\frac{10^4}{\sqrt2\times10^4}=\frac1{\sqrt2}.$$

这正好是二阶 Butterworth 的极点位置，所以 $\omega_c=\omega_n=\sqrt2\times10^4\approx1.414\times10^4\ \mathrm{rad/s}$。

**例 5（高阶 Butterworth 的极点）**　五阶 Butterworth 低通，$\omega_c=1000$。

五个极点在左半平面圆上均匀分布，角度为 $108^\circ,144^\circ,180^\circ,216^\circ,252^\circ$（从正实轴量起）。最靠近虚轴的极点在 $108^\circ$ 和 $252^\circ$，实部为

$$1000\cos108^\circ\approx-309.0.$$

**例 6（Butterworth 衰减计算）**　三阶 Butterworth 高通，$f_c=100$ Hz，输入 $50$ Hz。

高通幅频平方为

$$|G|^2=\frac{1}{1+(f_c/f)^6}.$$

$f_c/f=2$，所以

$$|G|^2=\frac1{1+64}=\frac1{65}.$$

衰减量：

$$-10\log_{10}\frac1{65}=10\log_{10}65\approx18.13\ \mathrm{dB}.$$

**例 7（级联不是同阶 Butterworth）**　两个相同的一阶低通 $\dfrac{\omega_c}{s+\omega_c}$ 级联。

$$G(s)=\left(\frac{\omega_c}{s+\omega_c}\right)^2.$$

在 $\omega=\omega_c$ 处，每节下降 $3.01$ dB，两节共下降 $6.02$ dB。级联后的极点是一个二重极点，与原二阶 Butterworth 的两个不同极点不同。所以增益相同不等于滤波器相同。

**例 8（由衰减指标求阶数）**　Butterworth 低通，$f_c=2$ kHz，要求在 $6$ kHz 处衰减至少 $35$ dB。

频率比为 $3$，衰减为

$$10\log_{10}\left(1+3^{2n}\right).$$

$n=3$ 时为 $28.6$ dB，$n=4$ 时为 $38.2$ dB，所以最小阶数为 $4$。

**例 9（由通带指标求截止频率）**　四阶 Butterworth 低通，在 $1$ kHz 处衰减不超过 $1$ dB。

$$10\log_{10}\left(1+\left(\frac{1000}{f_c}\right)^8\right)\le1.$$

$$\left(\frac{1000}{f_c}\right)^8\le10^{0.1}-1=0.2589,$$

$$\frac{1000}{f_c}\le0.8446\quad\Longrightarrow\quad f_c\ge1.184\ \mathrm{kHz}.$$

### 11.9 调制补充

**例 1（波长与载波）**　$3$ kHz 音频直接作为电磁波发送，$c=3\times10^8\ \mathrm{m/s}$。

$$\lambda=\frac{c}{f}=\frac{3\times10^8}{3\times10^3}=10^5\ \mathrm{m}=100\ \mathrm{km}.$$

波长太长，天线无法做这么长，所以需要把信号调制到高频载波上。

**例 2（DSB-SC 的频谱）**　$u(t)=2\cos1000t+\cos2000t$，载波 $\cos10000t$。

逐项使用 $\cos a\cos b=\frac12[\cos(a-b)+\cos(a+b)]$：

$$2\cos1000t\cos10000t=\cos9000t+\cos11000t,$$

$$\cos2000t\cos10000t=\frac12\cos8000t+\frac12\cos12000t.$$

正频率分量为

$$8000\ (0.5),\quad9000\ (1),\quad11000\ (1),\quad12000\ (0.5).$$

调制把每个频率搬到载波两侧，幅度减半，且不含载波本身。

**例 3（单边带滤波）**　$u(t)$ 带宽 $15$ kHz，乘 $2\cos(2\pi\cdot15000t)$ 后低通到 $15$ kHz。

输入一个 $4$ kHz 分量：

$$3\cos(2\pi\cdot4000t)\cdot2\cos(2\pi\cdot15000t)
=3\cos(2\pi\cdot11000t)+3\cos(2\pi\cdot19000t).$$

低通保留 $11$ kHz 项，滤掉 $19$ kHz 项。载波幅度 $2$ 恰好抵消积化和差的 $\frac12$，所以幅度仍为 $3$。

**例 4（FDM 信道数）**　频带 $3.000$ 到 $3.400$ MHz，每个 DSB-SC 信道 $2W=6.8$ kHz。

总带宽 $400$ kHz，信道数：

$$\left\lfloor\frac{400}{6.8}\right\rfloor=58.$$

**例 5（FDM 载频安排）**　四路 $3$ kHz 消息，DSB-SC，频带从 $100$ kHz 开始，相邻信道留 $5$ kHz 保护间隔。

每个信道占 $6$ kHz，相邻载频间隔为 $6+5=11$ kHz。第一个载频：

$$f_1=100+3=103\ \mathrm{kHz}.$$

第四个载频：

$$f_4=103+3\times11=136\ \mathrm{kHz}.$$

**例 6（多层调制）**　$u_1,u_2$ 带宽均为 $5000$ rad/s，先组成

$$b(t)=u_1(t)+u_2(t)\cdot2\cos10000t,$$

再发送

$$c(t)=b(t)\cdot2\cos20000t.$$

$u_1$ 占据 $0$ 到 $5000$；$u_2$ 调制后占据 $10000\pm5000$，即 $5000$ 到 $15000$。所以 $b(t)$ 占据 $0$ 到 $15000$。

再乘 $2\cos20000t$，频带搬到 $20000\pm15000$，即 $5000$ 到 $35000$。

**例 7（瞬时频率）**　$y(t)=\cos(t^2)$。

相位 $\theta(t)=t^2$，瞬时角频率：

$$\omega_i=\frac{d\theta}{dt}=2t.$$

$t=5$ s 时为 $10$ rad/s。

**例 8（PM 的频偏）**　$y(t)=\cos(\omega_ct+0.5u(t))$，$u(t)=4000t$。

瞬时频率：

$$\omega_i=\omega_c+0.5\times4000=\omega_c+2000.$$

频偏换算成赫兹：

$$\frac{2000}{2\pi}\approx318.3\ \mathrm{Hz}.$$

**例 9（FM 与 PM 的区别）**　输入 $u(t)=H(t)$。

FM 的相位为 $\omega_ct+k\int_{-\infty}^{t}u(\tau)d\tau$。$t>0$ 时积分等于 $t$，相位为 $\omega_ct+kt$，瞬时频率为 $\omega_c+k$，相位连续。

PM 的相位为 $\omega_ct+kH(t)$。$t>0$ 时相位为 $\omega_ct+k$，瞬时频率为 $\omega_c$，但相位在 $t=0$ 处跳变 $k$。

**例 10（窄带 FM 的频谱）**　$u(t)$ 带宽 $W$，无直流，FM 信号

$$y(t)=\cos\left(\omega_ct+k\int_{-\infty}^{t}u(\tau)d\tau\right).$$

$k$ 很小，展开：

$$y(t)\approx\cos\omega_ct-k\sin\omega_ct\int_{-\infty}^{t}u(\tau)d\tau.$$

第二项是 $\sin\omega_ct$ 被积分信号调幅，频带为 $\omega_c-W$ 到 $\omega_c+W$，与 AM 相同。只有 $k$ 很大时带宽才会明显超过 $2W$。

---

## 12 Quiz 3 补充：s 域电路与滤波器设计细节

本节补充 Quiz 3 用到、但第 7—11 节没有展开的内容。书写顺序与做题顺序一致：先讲 s 域电路怎么建模（阻抗、并联、电流源驱动），再讲系统指标（斜坡稳态误差、测量延迟、输入反求、零极点抵消），然后进入滤波器细节（互补相加、斜率读图、分频器、全通与延迟线），最后是 Butterworth 与调制的小细节。

### 12.1 s 域电路与阻抗

#### 三种元件的 s 域阻抗

把电容、电感的时域关系取拉普拉斯变换（零初始条件），可以得到它们与电阻同形式的「阻抗」：

$$Z_R=R,\qquad Z_L(s)=sL,\qquad Z_C(s)=\frac{1}{sC}.$$

- 电阻：电压电流同相，阻抗为常数。
- 电感：$\dfrac{v}{i}=sL$，频率越高阻抗越大，所以电感对高频「阻力大」，是低通元件。
- 电容：$\dfrac{v}{i}=\dfrac{1}{sC}$，频率越高阻抗越小，对高频「阻力小」，是高通元件。

若初始储能不为零，电容、电感的初始电压或电流会以 $1/s$ 项的形式出现，相当于额外的电源。题目写「初始储能为零」时，直接用上面三个阻抗即可。

#### 串联与并联

串联阻抗相加：

$$Z_{\text{series}}=Z_1+Z_2+\cdots$$

并联跟电阻一样：

$$Z_{\text{parallel}}=\frac{Z_1Z_2}{Z_1+Z_2}\qquad(\text{两个元件}),$$

多个元件时用倒数相加再取倒数。电感和电容并联是最常见的一种：

$$Z_{L\parallel C}=\frac{sL\cdot\dfrac{1}{sC}}{sL+\dfrac{1}{sC}}
=\frac{sL}{s^2LC+1}.$$

分母的 $s^2LC+1=0$ 给出 $s=\pm j\dfrac{1}{\sqrt{LC}}$，正好是谐振频率。电流源驱动并联 LC 时，端电压会以这个频率振荡。

**例**　$L=1$ H，$C=0.25$ F 的并联阻抗。

$$Z(s)=\frac{s}{0.25s^2+1}=\frac{4s}{s^2+4}.$$

#### 电流源驱动的并联电路

电路题常给「电流源 $u(t)$ 驱动某网络，求端电压」。按欧姆定律的 s 域形式：

$$Y(s)=U(s)Z(s).$$

注意输入是电流源，输出是电压，中间乘的是阻抗，不是传递函数 $G(s)$。但形式上仍是一个 LTI 关系：$Z(s)$ 就是「电流到电压」的传递函数。

**例**（Quiz 3 第 17 题）$u(t)=tH(t)$，$L=1$ H，$C=0.25$ F 并联，求端电压最大值。

$$U(s)=\frac{1}{s^2},\qquad Z(s)=\frac{4s}{s^2+4},$$

$$Y(s)=\frac{4}{s(s^2+4)}=\frac1s-\frac{s}{s^2+4},$$

$$y(t)=1-\cos2t\quad(t\ge0).$$

余弦的最小值为 $-1$，所以最大电压为 $1-(-1)=2$ V。这类题最后一步往往是「时域表达式的极值」，不要停在 $Y(s)$。

#### 串联 RLC 回顾

第 5.3 节从微分方程出发求过 RLC 的 $\omega_n$、$\zeta$。用阻抗重做一遍，可以更快：

输出取电容电压时，分压关系为

$$\frac{Y(s)}{U(s)}=\frac{Z_C}{Z_R+Z_L+Z_C}
=\frac{\dfrac{1}{sC}}{R+sL+\dfrac{1}{sC}}
=\frac{1}{LCs^2+RCs+1}.$$

与标准形式对照，分母乘以 $1/LC$ 的系数给出

$$\omega_n=\frac{1}{\sqrt{LC}},\qquad \zeta=\frac{R}{2}\sqrt{\frac{C}{L}}.$$

这与 5.3 节的结果一致。用阻抗法时记住：分压公式和纯电阻相同，只是每个「电阻」换成对应的阻抗。

### 12.2 斜坡（ramp）输入的稳态误差

#### 误差传递函数

控制系统常关心「输入与输出的差」。定义误差

$$e(t)=u(t)-y(t),$$

则

$$E(s)=U(s)-Y(s)=U(s)\left[1-G(s)\right].$$

这里使用了 $Y(s)=G(s)U(s)$，要求系统稳定且零初始条件。$1-G(s)$ 称为误差传递函数。

#### 终值定理求稳态误差

斜坡输入的变换为 $U(s)=\dfrac{1}{s^2}$。所以

$$E(s)=\frac{1}{s^2}\left[1-G(s)\right].$$

终值定理给出

$$e(\infty)=\lim_{s\to0}sE(s)=\lim_{s\to0}\frac{1-G(s)}{s},$$

前提是 $sE(s)$ 的全部极点在开左半平面。如果 $1-G(0)=0$，即直流增益为 $1$，上式是 $0/0$ 型，需要用洛必达法则或直接展开 $G(s)$ 的低频近似。

**例**（Quiz 3 第 20 题）$G(s)=\dfrac{1}{2s+1}$，$u(t)=tH(t)$。

$$E(s)=\frac{1}{s^2}\left(1-\frac{1}{2s+1}\right)
=\frac{2}{s(2s+1)}.$$

$$sE(s)=\frac{2}{2s+1},\qquad\text{极点在 }s=-\frac12.$$

终值：

$$e(\infty)=\frac{2}{1}=2\ \mathrm{V}.$$

一阶低通对斜坡输入始终有常数误差。直观理解：系统跟不上斜坡，落后固定的一段时间。误差 $2$ V 对应时间延迟 $\tau=2$ s（斜坡斜率 $1\ \mathrm{V/s}$），恰好等于系统的时间常数。

#### 一般情形与低频群延迟

一般地，只要系统稳定、$G(0)=1$，在 $s=0$ 附近把 $G(s)$ 展开：

$$G(s)\approx1+G'(0)s,$$

代入

$$E(s)\approx\frac{-G'(0)s}{s^2}=\frac{-G'(0)}{s},$$

反变换得

$$e(\infty)=-G'(0).$$

这个值恰好等于系统在零频的群延迟（12.10 节）。直观理解：输出落后输入一个固定时间，斜坡斜率乘上这个时间就是恒定误差。一阶低通的时间常数 $\tau$ 就是 $-G'(0)$，所以误差为 $\tau$。

若 $G(0)\neq1$，误差中含 $(1-G(0))/s$ 项，反变换为随时间增长的斜坡，稳态误差无界。若 $G$ 在原点有积分器（$G(s)$ 含 $1/s$ 因子），直流增益无穷大，斜坡误差可以为零或为常数，这时 $sE(s)$ 在 $s=0$ 的取值要用洛必达法则。

### 12.3 测量的延迟效应

系统相频特性对测量的影响，可以用两个简单结论概括。

#### 恒定增益系统

$G(s)=K$，$G(j\omega)=K$：幅值为 $K$，相位为 $0$。输出

$$y(t)=K\cos\omega t,$$

与输入同相，没有延迟。

#### 纯延迟系统

$G(s)=e^{-sT}$，$G(j\omega)=e^{-j\omega T}$：幅值为 $1$，相位为 $-\omega T$。输出

$$y(t)=\cos\left(\omega(t-T)\right),$$

相当于输入被推迟了 $T$ 秒。相位与频率的**斜率**就是延迟时间：

$$\tau_g=-\frac{d\angle G(j\omega)}{d\omega}=T.$$

这个量称为群延迟。线性相位对应恒定延迟，是「无失真传输」的条件之一。

#### 相位与测量

用相位差测量距离、速度或时间，本质是把「时间延迟」换成「相位延迟」。同一延迟对不同频率对应不同的相位：

$$\Delta\varphi=-\omega T.$$

所以：

- 单频测量：只能得到 $\bmod 2\pi$ 的相位，存在多值性（距离模糊）。
- 宽带测量：不同频率的相位斜率给出唯一的 $T$，这就是线性相位对测量的价值。

Quiz 3 第 49 题的延迟线 $e^{-2s}$ 正是这一原理的最简模型：$|G|=1$ 不损失信号，$\angle G=-2\omega$ 携带了 $2$ s 的延迟信息。

### 12.4 由输出反求输入

若已知期望输出 $y(t)$ 和系统 $G(s)$，求输入：

$$U(s)=\frac{Y(s)}{G(s)}.$$

步骤与 11.5 例 3 相同：

1. 求 $Y(s)$。
2. 除以 $G(s)$。
3. 若 $U(s)$ 是假分式（分子次数不低于分母），先做多项式除法。
4. 真分式部分做部分分式，逐项反变换。

**多项式除法的意义**：商中的常数项对应时域的 $\delta(t)$，$s$ 的一次项对应 $\delta'(t)$。这类冲激项在物理上代表「输入必须含冲激才能让输出瞬间跳变」。

**例**（Quiz 3 第 36 题）$G(s)=\dfrac{4}{s^2+2s+4}$，要求 $y(t)=\left(1-e^{-4t}\right)H(t)$。

$$Y(s)=\frac1s-\frac{1}{s+4}=\frac{4}{s(s+4)},$$

$$U(s)=\frac{Y(s)}{G(s)}=\frac{s^2+2s+4}{s(s+4)}
=1+\frac{-2s+4}{s(s+4)}.$$

假分式化为「常数 + 真分式」，常数 $1$ 就是 $\delta(t)$ 的拉普拉斯变换。继续部分分式：

$$\frac{-2s+4}{s(s+4)}=\frac1s-\frac{3}{s+4},$$

$$u(t)=\delta(t)+\left(1-3e^{-4t}\right)H(t).$$

校验：把 $u$ 代回 $G$ 计算输出，$s^2+2s+4$ 与分母的复极点约掉，输出只剩 $4/[s(s+4)]$，与题设一致。题目 (c) 说「欠阻尼电路不可能」正是忽略了这种零极点抵消。

### 12.5 输入极点与系统极点重合的二重极点

当输入极点恰好等于系统的某个极点时，$Y(s)=G(s)U(s)$ 中该极点变为二重，时域出现 $te^{pt}$ 项。这是 11.5 例 1 的一般情形，做题时要检查分子是否恰好有零点抵消它。

**例**（Quiz 3 第 33 题）$G(s)=\dfrac{s+4}{s^2+3s+2}$，$u(t)=e^{-2t}H(t)$。

$$Y(s)=\frac{s+4}{(s+1)(s+2)^2}.$$

输入极点 $-2$ 与系统极点 $-2$ 重合，$s=-2$ 是二重极点。部分分式：

$$Y(s)=\frac{3}{s+1}-\frac{3}{s+2}-\frac{2}{(s+2)^2},$$

$$y(t)=3e^{-t}-3e^{-2t}-2te^{-2t}\quad(t\ge0).$$

$te^{-2t}$ 项是「共振」在 s 域的表现：输入频率与系统自然频率相同，响应会多出一个随时间线性增长的包络。数值代入 $t=1$ 得 $y(1)=0.4270$。

### 12.6 零点靠近极点与零点抵消

#### 零点靠近极点

极点 $p$ 对应的模态系数，等于 $G(s)$ 去掉该极点因子后在 $s=p$ 处的值（遮盖法）。若分子有一个零点 $z$ 非常靠近 $p$，则这个值很小。

**例**（Quiz 3 第 31 题）$G(s)=\dfrac{s+3}{(s+1)(s+3.1)}$。

$$A_{3.1}=\left.\frac{s+3}{s+1}\right|_{s=-3.1}=\frac{-0.1}{-2.1}=0.04762.$$

零点 $-3$ 与极点 $-3.1$ 只差 $0.1$，$e^{-3.1t}$ 项几乎被消掉，冲激响应近似为只含 $e^{-t}$ 的慢模态。

#### 零点抵消输入极点

输入 $u(t)=e^{-t}H(t)$ 的极点在 $-1$。若 $G$ 的零点也在 $-1$，则

$$Y(s)=G(s)U(s)=\frac{k(s+1)}{(s+2)(s+5)}\cdot\frac{1}{s+1}=\frac{k}{(s+2)(s+5)}.$$

输出中**没有** $e^{-t}$ 项，但系统的自然模态 $e^{-2t}$、$e^{-5t}$ 仍然被激发（初始状态为零也会被输入「激励」出这些模态）。

**例**（Quiz 3 第 37 题）极点在 $-2,-5$，零点 $-1$，直流增益 $3$：

$$G(0)=\frac{k}{10}=3\quad\Longrightarrow\quad k=30,$$

$$y(t)=10\left(e^{-2t}-e^{-5t}\right)H(t).$$

#### 两个易错点

- 零点不能「阻断」整个输出，它只去掉一个模态。
- 直流增益用来定 $k$ 时，分母是各极点绝对值之积（这里 $2\times5=10$），分子是各零点绝对值之积（这里 $1$）。

### 12.7 互补滤波器与并联相加

#### 复数相加，不是模相加

两个系统并联，传递函数相加：

$$G(s)=G_1(s)+G_2(s).$$

求 $|G(j\omega)|$ 时，必须先把复数加完再取模。先取模再相加一般会得到错误结果：

$$|G_1+G_2|\neq|G_1|+|G_2|.$$

**例**（Quiz 3 第 52 题）$G(s)=\dfrac{10}{s+10}+\dfrac{s}{s+1000}$，求 $|G(j100)|$。

$$G_1(j100)=\frac{10}{10+100j}=0.0099-0.0990j,$$

$$G_2(j100)=\frac{100j}{1000+100j}=0.0099+0.0990j.$$

虚部恰好抵消：

$$G(j100)=0.0198,\qquad |G(j100)|=0.01980.$$

若错误地按模相加，会得 $0.0995+0.0995=0.199$，差一个数量级。带阻滤波器的「谷」正是靠两个分量的虚部相互抵消形成的。

#### 互补低通与高通

若

$$G_L(s)=\frac{\omega_c}{s+\omega_c},\qquad G_H(s)=\frac{s}{s+\omega_c},$$

则

$$G_L(s)+G_H(s)=\frac{s+\omega_c}{s+\omega_c}=1.$$

两条曲线互补：任何频率的能量必经过其一，幅值合起来恒为 $1$。注意这是**复数**相加为 $1$，但单独看 $|G_L|^2+|G_H|^2=1$ 也成立（因为两者相位差恒为 $90^\circ$）：

$$|G_L(j\omega)|^2=\frac{\omega_c^2}{\omega_c^2+\omega^2},\qquad
|G_H(j\omega)|^2=\frac{\omega^2}{\omega_c^2+\omega^2}.$$

这和功率互补（Linkwitz-Riley 分频的思想）有关。Quiz 3 第 53 题的错误选项 (c) 就是把 $\omega_c$ 处的模相加：正确做法是

$$G_L(j\omega_c)=\frac{1-j}{2},\qquad G_H(j\omega_c)=\frac{1+j}{2},$$

相加得 $1$，而不是 $\sqrt2$。

#### 带阻的并联构造

带阻可以这样搭：低通截止频率**低于**高通截止频率，并联相加。两者之间有一个交叉区，虚部在交叉区内相互抵消，形成陷波。Quiz 3 第 52 题的 $10$ rad/s 低通与 $1000$ rad/s 高通就是这种结构，陷波中心在几何平均附近。

### 12.8 读 Bode 斜率与由指标反求参数

#### 斜率由极零点个数决定

把 $G(s)$ 写成因式分解后的形式：

$$G(s)=K\frac{(s-z_1)\cdots(s-z_m)}{(s-p_1)\cdots(s-p_n)}.$$

对 Bode 幅频图的渐近线：

- 每个极点在超过其转折频率后贡献 $-20$ dB/dec。
- 每个零点在超过其转折频率后贡献 $+20$ dB/dec。
- 原点处的极点贡献 $-20$ dB/dec（对所有频率），原点处的零点贡献 $+20$ dB/dec。

**例**（Quiz 3 第 38 题）$G(s)=1+\dfrac1s+0.25s$。

通分：

$$G(s)=\frac{4s+s^2+4}{4s}=\frac{(s+2)^2}{4s}.$$

- 原点极点：低频斜率 $-20$ dB/dec。
- 二重零点在 $2$ rad/s：过 $2$ rad/s 后斜率加 $40$ dB/dec。

所以斜率从 $-20$ 变为 $+20$ dB/dec。选项里容易错的是「$-20$ 变 $0$」：那是只把二重零点当成一重；「$-20$ 变 $+40$」是忘了原点极点在高频依然存在。

#### 从左到右累加斜率

画渐近线的步骤：

1. 把 $G(s)$ 因式分解，标出所有极零点频率。
2. 从最低频开始：原点极点或零点决定初始斜率；若没有，初始斜率为 $0$。
3. 每经过一个极点，斜率减 $20$ dB/dec；每经过一个零点，斜率加 $20$ dB/dec。
4. 用某个已知点（如直流增益或高频增益）确定整条线的高度。

#### 由增益指标反求参数

先用低频极限定 $K$：

$$G(0)=K\frac{z_1\cdots z_m}{p_1\cdots p_n}.$$

再用高频极限定另一个关系。若分子分母同阶，

$$\lim_{s\to\infty}G(s)=K.$$

**例**（Quiz 3 第 39 题）$G(s)=K\dfrac{s+z}{s+5}$，直流增益 $1$，高频增益 $-30$ dB。

低频：

$$G(0)=K\frac{z}{5}=1.$$

高频：

$$K=10^{-30/20}=0.03162.$$

两式联立：

$$z=\frac{5}{K}=158.1\ \mathrm{rad/s}.$$

注意高频增益是 $K$ 而不是 $Kz/5$：高频时 $s$ 主导分子分母，$z$ 和 $5$ 都被忽略。

#### dB 换算速查

| 幅值比 | dB |
|---|---|
| $2$ | $+6.02$ |
| $10$ | $+20$ |
| $\sqrt2$ | $+3.01$ |
| $1/\sqrt2$ | $-3.01$ |
| $1/2$ | $-6.02$ |
| $1/10$ | $-20$ |
| $1/1000$ | $-60$ |

$a$ dB 对应幅值比 $10^{a/20}$。功率用 $10\log_{10}$，幅值用 $20\log_{10}$；滤波器题几乎都用幅值定义。

### 12.9 分频器与斜率

音箱二分频中，高音单元通过串联电容获得一阶高通：

$$G_H(s)=\frac{4Cs}{4Cs+1}.$$

标准化：

$$G_H(s)=\frac{s}{s+\dfrac{1}{4C}}.$$

截止频率

$$\omega_c=\frac{1}{4C}.$$

**例**（Quiz 3 第 51 题）要求 $f_c=3$ kHz：

$$C=\frac{1}{4\cdot2\pi\cdot3000}=13.26\ \mu\mathrm{F}.$$

数值上 $4C=1/\omega_c$，单位是秒；$C$ 算出来后乘 $10^6$ 换成 $\mu$F。分频器题常见的两个坑：

- 把 $4\Omega$ 当成 $4C$ 中的系数来源：系数 $4$ 来自阻值，若扬声器阻抗为 $8\ \Omega$，分频公式变为 $\omega_c=1/(8C)$。
- 把 $f_c$ 直接代入 $\omega_c$：必须先乘 $2\pi$。

#### 衰减量换算

一阶滤波器在频率比 $x=f/f_c$ 处的幅值：

- 低通：$|G|=\dfrac{1}{\sqrt{1+x^2}}$。
- 高通：$|G|=\dfrac{x}{\sqrt{1+x^2}}$。

衰减量用 $-20\log_{10}|G|$。例如高通在 $-3$ dB 频率的一半处（$x=0.5$）：

$$|G|=\frac{0.5}{\sqrt{1.25}}=0.4472,\qquad -20\log_{10}0.4472=6.99\ \mathrm{dB}.$$

### 12.10 全通与延迟线

#### 一阶全通的形式

$$G(s)=\frac{s-a}{s+a}.$$

零点在 $+a$，极点在 $-a$，关于虚轴对称。令 $s=j\omega$：

$$|G(j\omega)|=\frac{|j\omega-a|}{|j\omega+a|}=1\quad\text{对所有 }\omega.$$

若 $a>0$，极点在左半平面，系统指数稳定。若写成 $\dfrac{s+a}{s-a}$，幅值仍为 $1$，但极点在右半平面，不稳定。

一般地，$n$ 阶全通的零点与极点关于虚轴镜像对称：每个左半平面极点 $p_i$ 对应一个右半平面零点 $-p_i^*$。全通不改变幅频，只改变相频，用于相位补偿和延迟均衡。

#### 全通在某一频率的相位

**例**（Quiz 3 第 48 题）$G(s)=\dfrac{10-s}{s+10}$，输入 $\cos10t$。

$$G(j10)=\frac{10-10j}{10+10j}=-j.$$

模为 $1$，相位 $-90^\circ$，所以

$$y(t)=\cos(10t-90^\circ)=\sin10t.$$

这里 $\cos(\theta-90^\circ)=\sin\theta$，符号为正。若相位写成 $+90^\circ$，结果就会变成 $-\sin$，这是选项 (d) 的错误来源。

#### 延迟线

理想延迟 $T$：

$$G(s)=e^{-sT},\qquad G(j\omega)=e^{-j\omega T}.$$

- 幅值恒为 $1$，是全通。
- 相位 $-\omega T$，与频率成**线性**关系。
- 群延迟恒为 $T$。

延迟线无法用有限阶有理传递函数精确实现，但可以用全通级联或数字滤波器逼近。第 49 题把「全通」与「线性相位」两个概念合在一起考：幅值为 $1$ 且相位线性，说明是延迟，而不是普通有理全通。

#### 相位延迟与群延迟

对一般的频率响应，定义两种延迟：

$$\tau_p(\omega)=-\frac{\angle G(j\omega)}{\omega},\qquad
\tau_g(\omega)=-\frac{d\angle G(j\omega)}{d\omega}.$$

- 相位延迟：单频正弦的等效延迟，决定某条谱线的相位。
- 群延迟：包络或宽带信号的延迟，决定波形是否失真。

只有线性相位时两者相等且为常数。Bode 相位图上，一阶极点的相位从 $0^\circ$ 缓慢减到 $-90^\circ$，相位斜率不是常数，所以群延迟随频率变化，会造成相位失真。

### 12.11 二阶低通的 -3 dB 频率

第 8.4 节只给了一阶的规则「截止频率等于极点频率」。二阶低通要解方程。

#### 推导

二阶低通

$$G(s)=\frac{K\omega_n^2}{s^2+2\zeta\omega_ns+\omega_n^2}$$

的幅频平方为

$$|G|^2=\frac{K^2}{\left(1-x\right)^2+4\zeta^2x},\qquad x=\left(\frac{\omega}{\omega_n}\right)^2.$$

令 $|G|^2=K^2/2$：

$$\left(1-x\right)^2+4\zeta^2x=2.$$

展开：

$$x^2+\left(4\zeta^2-2\right)x-1=0.$$

取正根：

$$x=\frac{2-4\zeta^2+\sqrt{\left(4\zeta^2-2\right)^2+4}}{2}
=1-2\zeta^2+\sqrt{\left(1-2\zeta^2\right)^2+1}.$$

于是

$$\omega_c=\omega_n\sqrt{x}.$$

#### 两个例子

$\zeta=1/\sqrt2$（Butterworth）：$1-2\zeta^2=0$，$x=\sqrt{1}=1$，所以 $\omega_c=\omega_n$。这正是 Butterworth 的定义。

**例**（Quiz 3 第 44 题）$\omega_n=20$，$\zeta=0.5$：$4\zeta^2=1$，方程化为

$$x^2-x-1=0\quad\Longrightarrow\quad x=1.618,$$

$$\omega_c=20\sqrt{1.618}=25.44\ \mathrm{rad/s}.$$

$\zeta<1/\sqrt2$ 时 $x>1$，截止频率高于 $\omega_n$，同时存在共振峰（5.3 节）。$\zeta>1/\sqrt2$ 时 $x<1$，截止频率低于 $\omega_n$。二阶的 $-3$ dB 点不能用 $\omega_n$ 代替，这是与一阶最大的区别。

### 12.12 Butterworth 细节补充

#### 阶数与衰减

$n$ 阶 Butterworth 低通的幅频平方：

$$|G|^2=\frac{1}{1+\left(\frac{f}{f_c}\right)^{2n}}.$$

高通则把比值倒过来：

$$|G|^2=\frac{1}{1+\left(\frac{f_c}{f}\right)^{2n}}.$$

频带外的衰减量：

$$A=10\log_{10}\left[1+\left(\frac{f}{f_c}\right)^{2n}\right].$$

**例**（Quiz 3 第 61 题）$f_c=2$ kHz，要求 $6$ kHz 处衰减 $35$ dB。频率比 $3$，试算：

$$n=3:\ 10\log_{10}(1+3^6)=28.6\ \mathrm{dB},$$

$$n=4:\ 10\log_{10}(1+3^8)=38.2\ \mathrm{dB}.$$

最小阶数为 $4$。试算时代入的是 $2n$，不是 $n$：三阶指数为 $6$，四阶为 $8$，这是最容易出错的地方。

#### 由通带指标定截止频率

**例**（Quiz 3 第 60 题）四阶、$1$ kHz 处损失不超过 $1$ dB：

$$10\log_{10}\left[1+\left(\frac{1}{f_c}\right)^8\right]\le1,$$

$$\left(\frac{1}{f_c}\right)^8\le10^{0.1}-1=0.2589,$$

开八次方得 $1/f_c\le0.8446$，即 $f_c\ge1.184$ kHz。注意 $10^{0.1}-1$ 中的 $0.1$ 来自 $1\ \mathrm{dB}=10\times0.1$；如果先算 $|G|^2$ 再取分贝，容易把 $20$ 和 $10$ 两个系数混用。

#### 由衰减倒推频率

**例**（Quiz 3 第 59 题）二阶高通，$f_c=6$ kHz，要求 $-30$ dB：

$$10\log_{10}\left[1+\left(\frac{f_c}{f}\right)^4\right]=30
\quad\Longrightarrow\quad\left(\frac{f_c}{f}\right)^4=999.$$

$$f=\frac{6000}{999^{1/4}}=1067\ \mathrm{Hz}.$$

#### 极点圆

$n$ 阶 Butterworth 的极点在左半平面圆上均匀分布，半径为 $\omega_c$，角度（从正实轴量起）

$$\theta_k=90^\circ+\frac{180^\circ(2k+1)}{2n},\qquad k=0,1,\dots,n-1.$$

相邻极点相隔 $180^\circ/n$。最靠近虚轴的一对角度最接近 $90^\circ$。

**例**（Quiz 3 第 56 题）五阶，$\omega_c=1000$：

$$\theta=108^\circ,\ 144^\circ,\ 180^\circ,\ 216^\circ,\ 252^\circ.$$

最近的实部为 $1000\cos108^\circ=-309.0$ rad/s。角度用「起点 $90^\circ$、间隔 $36^\circ$」也可以直接数出来。

#### 二阶 Butterworth 的特征

二阶 Butterworth 分母固定为

$$s^2+\sqrt2\,\omega_cs+\omega_c^2,$$

所以

$$\omega_n=\omega_c,\qquad \zeta=\frac{1}{\sqrt2}.$$

由极点反推时（Quiz 3 第 54 题）：极点到原点的距离为 $\omega_n$，实部与 $\omega_n$ 之比为 $\zeta$。若得到 $\zeta=1/\sqrt2$，它必然是 Butterworth，且 $\omega_c=\omega_n$。

#### 级联不是高阶级联 Butterworth

两个相同的二阶 Butterworth 级联，得到的是

$$G(s)=\left[\frac{\omega_c^2}{s^2+\sqrt2\omega_cs+\omega_c^2}\right]^2,$$

极点是二重的，而四阶 Butterworth 的四个极点在 $112.5^\circ,157.5^\circ,202.5^\circ,247.5^\circ$，互不相同。两者在 $\omega_c$ 处的增益也不一样：级联为 $-6.02$ dB（两节各 $-3.01$ dB），真正的四阶 Butterworth 仍为 $-3.01$ dB。因此级联系统的 $-3$ dB 截止频率低于 $\omega_c$，过渡带也更深：在 $\omega=\sqrt2\omega_c$ 处，级联为 $1/(1+2x^4+x^8)$，四阶 Butterworth 为 $1/(1+x^8)$，前者衰减更多。Quiz 3 第 58 题正是考「增益不能单独说明是几阶 Butterworth，极点结构才决定滤波器类型」。

### 12.13 调制细节补充

#### 积化和差是解调/调制题的核心

$$\cos a\cos b=\frac12\left[\cos(a-b)+\cos(a+b)\right].$$

调制乘载波：频谱搬家，每边幅度乘 $\frac12$（载波幅度为 $2$ 时抵消）。

相干解调：再乘一次载波，产生基带项与 $2\omega_c$ 项，低通滤掉后者。

#### 单边带滤波

**例**（Quiz 3 第 64 题）载波 $2\cos(2\pi\cdot15000t)$，消息分量 $3\cos(2\pi\cdot4000t)$：

$$3\cos(2\pi\cdot4000t)\cdot2\cos(2\pi\cdot15000t)
=3\cos(2\pi\cdot11000t)+3\cos(2\pi\cdot19000t).$$

低通截止 $15$ kHz，保留 $11$ kHz，滤掉 $19$ kHz。载波幅度 $2$ 恰好抵消 $\frac12$，输出幅度仍为 $3$。

#### FDM 的两个计数公式

信道数（无保护间隔）：

$$N=\left\lfloor\frac{B_{\text{band}}}{2W}\right\rfloor.$$

载频安排（有保护间隔 $g$）：每路带宽 $2W$、相邻载频间隔 $2W+g$，第一路载频在频带下沿上方 $W$ 处：

$$f_1=f_{\text{low}}+W,\qquad f_k=f_1+(k-1)(2W+g).$$

**例**（Quiz 3 第 66 题）$W=3$ kHz，$g=5$ kHz，从 $100$ kHz 开始：

$$f_1=103,\qquad f_4=103+3\times11=136\ \mathrm{kHz}.$$

#### 多层调制

先把内层载波处理完，求出合成信号 $b(t)$ 的整个频段，再整体搬移。频段取各分量的并集：

$$b(t)=u_1(t)+u_2(t)\cdot2\cos(\omega_{c1}t).$$

$u_1$ 占 $[0,W]$，调制后的 $u_2$ 占 $[\omega_{c1}-W,\omega_{c1}+W]$，合并后 $b$ 占 $[0,\omega_{c1}+W]$。再乘 $2\cos\omega_{c2}t$，频段搬到 $\omega_{c2}\pm(\omega_{c1}+W)$。

**例**（Quiz 3 第 67 题）$W=5000$，$\omega_{c1}=10\,000$，$\omega_{c2}=20\,000$：$b$ 占 $0$ 到 $15\,000$，$c$ 占 $5000$ 到 $35\,000$ rad/s。

#### 瞬时频率、PM 与 FM

$$\omega_i(t)=\frac{d\theta(t)}{dt}.$$

- PM：$\theta=\omega_ct+ku(t)$，$\omega_i=\omega_c+k\dot u(t)$。
- FM：$\theta=\omega_ct+k\int_{-\infty}^{t}u(\tau)d\tau$，$\omega_i=\omega_c+ku(t)$。

阶跃消息 $u(t)=H(t)$ 的情形（Quiz 3 第 70 题）：

- FM：积分为 $t$（$t>0$），相位 $\omega_ct+kt$，相位连续，频率跳到 $\omega_c+k$。
- PM：相位 $\omega_ct+k$，在 $t=0$ 跳变 $k$，之后导数仍为 $\omega_c$，频率不变。

**例**（Quiz 3 第 69 题）PM，$k=0.5$ rad/V，$u=4000t$：

$$\omega_i=\omega_c+0.5\times4000=\omega_c+2000\ \mathrm{rad/s},$$

$$\Delta f=\frac{2000}{2\pi}=318.3\ \mathrm{Hz}.$$

#### 窄带 FM 的带宽

$k$ 小时

$$y\approx\cos\omega_ct-k\sin\omega_ct\int u,$$

第二项是 $\sin\omega_ct$ 被积分信号调幅，频带 $\omega_c\pm W$，与 AM 相同。调制指数

$$\beta=\frac{\Delta f}{W},$$

$\beta\ll1$ 为窄带 FM，$B\approx2W$；$\beta\gg1$ 用 Carson 公式 $B\approx2(\Delta f+W)$。

#### 波长的数量级

$$\lambda=\frac{c}{f}=\frac{3\times10^8}{f}.$$

$3$ kHz 音频对应 $100$ km，$100$ MHz 载波对应 $3$ m。天线尺寸与波长可比，这就是音频必须调制到高频的原因。

---

> [!tip] 学习建议
> 拉普拉斯变换的价值在于把微积分方程变成代数方程：微分对应乘 $s$，积分对应除 $s$，初始条件变成常数项，系统对输入的作用变成传递函数相乘。做题时先想清楚两件事：信号的极点和系统的极点分别在什么地方。信号的极点决定响应里有哪些项，系统的极点决定这些项是衰减、恒定还是增长。滤波器题则先看两端增益判断类型，再用 $-3$ dB 条件或 Bode 斜率定量；调制题的第一反应应该是积化和差与频谱搬移。
