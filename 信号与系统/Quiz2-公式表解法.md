# Quiz 2 — 按公式表求解

> 本题库对应的题目见 [[Quiz2]]。每题先列出**用到的公式表条目**，再代入计算，最后给答案。记号与公式表一致：$\operatorname{sinc}x=\dfrac{\sin\pi x}{\pi x}$，$c_k=\dfrac1T\displaystyle\int_0^T u(t)e^{-jk\omega_0t}dt$。

## 公式表速查（本文件反复使用）

- **FS 系数**：$c_k=\frac1T\int_T u e^{-jk\omega_0t}dt$，$u=\sum_kc_ke^{jk\omega_0t}$；三角系数 $a_k=2\Re c_k$，$b_k=-2\Im c_k$，$a_0=c_0$。
- **对称**：$u$ 实 → $c_{-k}=\overline{c_k}$；$u$ 偶 → $b_k=0$；$u$ 奇 → $a_0=a_k=0$。
- **时移**：$u(t-t_0)$ 的系数为 $e^{-jk\omega_0t_0}c_k$。
- **Parseval（周期）**：$P=\sum_k|c_k|^2$。
- **标准波形**：脉冲串 $c_k=Ad\operatorname{sinc}(kd)$；偶方波 $c_k=A\operatorname{sinc}(k/2)$（$k$ 奇）。
- **FT**：$U(j\omega)=\int u e^{-j\omega t}dt$，$u=\frac1{2\pi}\int U e^{j\omega t}d\omega$。
- **周期信号的 FT**：$U(j\omega)=2\pi\sum_kc_k\delta(\omega-k\omega_0)$。
- **常用对**：$\delta(t-t_0)\leftrightarrow e^{-j\omega t_0}$；$1\leftrightarrow2\pi\delta(\omega)$；$e^{-at}H(t)\leftrightarrow\frac1{a+j\omega}$；$e^{-a|t|}\leftrightarrow\frac{2a}{a^2+\omega^2}$；$p_\tau(t)\leftrightarrow\tau\operatorname{sinc}\left(\frac{\omega\tau}{2\pi}\right)$；$\frac{\sin Wt}{\pi t}\leftrightarrow p_{2W}(\omega)$；$e^{-at}\sin(\omega_0t)H(t)\leftrightarrow\frac{\omega_0}{(a+j\omega)^2+\omega_0^2}$。
- **性质**：时移 $e^{-j\omega t_0}$；尺度 $\frac1{|a|}U(j\omega/a)$；对偶 $U(jt)\leftrightarrow2\pi u(-\omega)$；微分 $j\omega U$；卷积→乘积；乘积→$\frac1{2\pi}U_1*U_2$。
- **能量 Parseval**：$E=\frac1{2\pi}\int|U|^2d\omega$。
- **二阶系统**：$G=\frac{K\omega_n^2}{(j\omega)^2+2\zeta\omega_n(j\omega)+\omega_n^2}$；$\omega_r=\omega_n\sqrt{1-2\zeta^2}$，$|G(j\omega_r)|=\frac{|K|}{2\zeta\sqrt{1-\zeta^2}}$，条件 $\zeta<\frac1{\sqrt2}$。
- **稳定**：极点全在左半平面 → 指数稳定、BIBO；虚轴单极点（其余在左半平面）→ 临界稳定但不 BIBO；虚轴重极点或右半平面极点 → 不稳定。

---

## 一、傅里叶级数（Q1–Q22）

**Q1** (d) $\omega_0=\frac{2}{15}$
> **公式表**：周期信号写成 $u=\sum c_ke^{jk\omega_0t}$，各频率必须是 $\omega_0$ 的整数倍。
> 通分 $\frac23=\frac{10}{15}$，$\frac45=\frac{12}{15}$，$\gcd(10,12)=2$：
> $$\omega_0=\frac{2}{15},\qquad T_0=\frac{2\pi}{\omega_0}=15\pi.$$

**Q2** $\omega_0=\frac16=0.1667$
> **公式表**：同上，常数项 $\omega=0$ 不参与。
> $\frac12=\frac36,\ \frac23=\frac46,\ \frac76=\frac76$，$\gcd(3,4,7)=1$：
> $$\omega_0=\frac16,\qquad T_0=12\pi.$$

**Q3** (d) 非周期
> 若周期为 $T$，须同时 $3T=2\pi m$、$\sqrt5T=2\pi n$，相除得 $\frac{3}{\sqrt5}=\frac mn\in\mathbb{Q}$，矛盾。频率比无理 → 非周期。

**Q4** (b) 偶数 $k$ 全为零
> **公式表**：时移性质（系数乘 $e^{-jk\omega_0t_0}$）。
> 令 $v(t)=u(t-T/2)$，则 $v$ 的系数为 $e^{-jk\omega_0T/2}c_k=e^{-jk\pi}c_k=(-1)^kc_k$。又 $v=-u$，系数为 $-c_k$，故
> $$(-1)^kc_k=-c_k\ \Rightarrow\ \big[(-1)^k+1\big]c_k=0,$$
> $k$ 偶（含 $0$）时 $c_k=0$。

**Q5** (b)
> **公式表**：$u$ 奇 → $a_0=a_k=0$；$a_k=2\Re c_k$，$b_k=-2\Im c_k$。
> $$c_k=\frac{a_k-jb_k}{2}=-\frac{j}{2}b_k$$
> 为纯虚数，且 $c_0=a_0=0$。

**Q6** (d)
> **公式表**：偶 → $b_k=0$；脉冲串 $c_k=Ad\operatorname{sinc}(kd)$。
> $A=1$，$d=\frac12$：$c_k=\frac12\operatorname{sinc}\frac k2$。去直流只改 $c_0$；$k\ge2$ 偶时 $\operatorname{sinc}\frac k2=\frac{\sin(k\pi/2)}{k\pi/2}=0$，只剩奇 $k$。偶信号 $a_k=2c_k$：
> $$a_k=\operatorname{sinc}\frac k2=\frac{2}{k\pi}\sin\frac{k\pi}{2}=\frac{2(-1)^{(k-1)/2}}{k\pi}\quad(k\ \text{奇}).$$

**Q7** $c_5=0.7639$
> **公式表**：偶方波 $c_k=A\operatorname{sinc}\frac k2$（$k$ 奇）。
> $$c_5=6\operatorname{sinc}\frac52=6\cdot\frac{\sin(5\pi/2)}{5\pi/2}=6\cdot\frac{1}{2.5\pi}=\frac{12}{5\pi}=0.76394.$$

**Q8** $c_3=-0.1273$
> **公式表**：全波整流正弦一行给出 $\dfrac{4A}{\pi(1-4k^2)}$。**注意**：该行数值等于余弦系数 $a_k$；复系数应为它的一半（$c_k=a_k/2$，因为 $b_k=0$），等价于 $c_k=\dfrac{2A}{\pi(1-4k^2)}$。
> $$a_3=\frac{4\cdot7}{\pi(1-36)}=-\frac{28}{35\pi},\qquad c_3=\frac{a_3}{2}=-\frac{14}{35\pi}=-\frac{2}{5\pi}=-0.12732.$$

**Q9** (c) $k=3$
> **公式表**：脉冲串 $c_k=Ad\operatorname{sinc}(kd)$。
> $\operatorname{sinc}(kd)=0\iff kd\in\mathbb{Z}\setminus\{0\}$，首个 $k=\frac1d=3$。

**Q10** $c_0=0.5$
> **公式表**：$c_0=\frac1T\int_Tu\,dt$。
> $$c_0=8\cdot\frac14+(-2)\cdot\frac34=2-1.5=0.5.$$

**Q11** (c) $c_0=0$
> $$c_0=\frac12\left[\int_0^1 1\,dt+\int_1^2(-1)\,dt\right]=\frac12(1-1)=0.$$

**Q12** (b) $c_0=0.1$
> **公式表**：$c_0=\frac1T\int_Tu\,dt$（面积/周期）。
> $$c_0=\frac{\frac{1}{\sqrt d}\cdot d}{1}=\sqrt d=\sqrt{0.01}=0.1.$$

**Q13** (c)
> **公式表**：$u$ 实 → $c_{-k}=\overline{c_k}$。
> $$c_3e^{j3\omega_0t}+c_{-3}e^{-j3\omega_0t}=2\Re\left(c_3e^{j3\omega_0t}\right)=2|c_3|\cos(3\omega_0t+\angle c_3).$$
> 因此 $k=-3$ 项只是这个实余弦的一半，不能单独丢弃。

**Q14** (c) $(4,6)$
> **公式表**：$a_k=2\Re c_k$，$b_k=-2\Im c_k$。
> $$a_1=2\cdot2=4,\qquad b_1=-2\cdot(-3)=6.$$

**Q15** $|c_2|=2.5$
> **公式表**：$c_k=\frac{a_k-jb_k}{2}$。
> $$|c_2|=\frac12\sqrt{a_2^2+b_2^2}=\frac12\sqrt{3^2+4^2}=\frac52.$$

**Q16** (c)
> **公式表**：$a_0=c_0$，$c_k=\frac{a_k-jb_k}{2}$，$c_{-k}=\overline{c_k}$。
> $\omega_0=\gcd(300,500)=100$，$u=2+6\cos(3\omega_0t)+8\sin(5\omega_0t)$，故 $c_0=2$，$a_3=6$，$b_5=8$：
> $$c_3=c_{-3}=\frac{6}{2}=3,\qquad c_5=\frac{0-j8}{2}=-4j,\qquad c_{-5}=4j.$$

**Q17** (d)
> **公式表**：周期 Parseval $P=\sum_k|c_k|^2$。负频率项同样计入。

**Q18** 基波占 $81.06\%$
> **公式表**：Parseval；$|u|=1$ → $P=1$。奇方波 $c_k=-\frac{2j}{\pi k}$。
> $$P_1=2|c_1|^2=2\cdot\frac{4}{\pi^2}=\frac{8}{\pi^2}=0.81057.$$

**Q19** $P_{\rm DC}/P_{\rm total}=0.25$
> **公式表**：Parseval；脉冲串 $c_0=Ad$。
> $$P_{\text{total}}=A^2d,\qquad P_{\text{DC}}=|c_0|^2=A^2d^2,\qquad \frac{P_{\text{DC}}}{P_{\text{total}}}=d=0.25.$$

**Q20** $c=-\frac{2j}{\pi}=-0.6366j$
> **公式表**：$c=\frac{\langle u,\phi\rangle}{\langle\phi,\phi\rangle}$，且 $\phi=e^{jt}$ 的范数平方为 $1$，所以 $c$ 就是 $c_1$。
> $$c_1=\frac1{2\pi}\left[\int_0^\pi e^{-jt}dt-\int_\pi^{2\pi}e^{-jt}dt\right]=\frac{1}{2\pi}\big[(-2j)-(2j)\big]=-\frac{2j}{\pi}.$$

**Q21** (b)
> **公式表**：最小均方误差的投影系数 $c=\frac{\langle u,\phi\rangle}{\langle\phi,\phi\rangle}$。
> $$\langle u-c\phi,\phi\rangle=\langle u,\phi\rangle-c\langle\phi,\phi\rangle=0.$$

**Q22** (c) $P(u)+P(y)$
> **公式表**：$P(x)=\|x\|^2=\langle x,x\rangle$，Parseval。
> $$P(u+y)=P(u)+P(y)+2\Re\langle u,y\rangle=P(u)+P(y).$$

---

## 二、傅里叶变换（Q23–Q54）

**Q23** (d) $e^{2t}H(t)$
> **公式表**：FT 定义 $U=\int u e^{-j\omega t}dt$。
> $$\int_0^\infty e^{(2-j\omega)t}dt,\qquad \left|e^{(2-j\omega)t}\right|=e^{2t}\to\infty,$$
> 对任何 $\omega$ 都发散；$e^{2t}$ 不是缓增分布，连含冲激的广义变换也没有。其余三个有界/多项式增长，广义变换存在：$\cos5t\leftrightarrow\pi[\delta(\omega-5)+\delta(\omega+5)]$，$H(t)\leftrightarrow\pi\delta(\omega)+\frac1{j\omega}$，$1\leftrightarrow2\pi\delta(\omega)$。

**Q24** (b)
> **公式表**：FT 定义与欧拉展开。
> $$U=\int u\cos\omega t\,dt-j\int u\sin\omega t\,dt.$$
> $u$ 奇 × $\cos$ 偶 → 奇，第一项为零；$u$ 奇 × $\sin$ 奇 → 偶，第二项为 $-j\times$ 实。故 $U$ 纯虚。代入 $-\omega$：$U(-j\omega)=-U(j\omega)$，为奇函数。

**Q25** (c)
> **公式表**：实信号共轭对称（由定义取共轭）。
> $$U(-j\omega)=U^*(j\omega)\ \Rightarrow\ |U(-j\omega)|=|U(j\omega)|,\quad \arg U(-j\omega)=-\arg U(j\omega).$$
> 模为偶函数、相位为奇函数；模非负不可能是奇函数，排除 (a)。

**Q26** $U(0)=1.1$
> **公式表**：$e^{-at}H(t)\leftrightarrow\frac1{a+j\omega}$，线性。
> $$U(j\omega)=\frac{3}{2+j\omega}-\frac{2}{5+j\omega},\qquad U(0)=\frac32-\frac25=1.1.$$

**Q27** $u(0)=\frac4\pi=1.2732$
> **公式表**：逆变换 $u(t)=\frac1{2\pi}\int Ue^{j\omega t}d\omega$。
> $$u(0)=\frac1{2\pi}\int U(j\omega)d\omega=\frac{1}{2\pi}\cdot(4\times2)=\frac4\pi.$$

**Q28** $\int\operatorname{sinc}(t)dt=1$
> **公式表**：$\frac{\sin Wt}{\pi t}\leftrightarrow p_{2W}(\omega)$，取 $W=\pi$：$\operatorname{sinc}(t)\leftrightarrow p_{2\pi}(\omega)$。
> 正变换在 $\omega=0$ 取值即信号面积：$\int\operatorname{sinc}(t)dt=U(0)=p_{2\pi}(0)=1$。

**Q29** (a) $e^{-j5\omega}$
> **公式表**：$\delta(t-t_0)\leftrightarrow e^{-j\omega t_0}$，取 $t_0=5$。

**Q30** (a) $2\pi\delta(\omega)$
> **公式表**：$1\leftrightarrow2\pi\delta(\omega)$（也可用周期 FT：$c_0=1$）。权重由逆变换的 $\frac1{2\pi}$ 决定：
> $$\frac1{2\pi}\int2\pi\delta(\omega)e^{j\omega t}d\omega=1.$$

**Q31** (c) $p_{2\pi}(\omega)$
> **公式表**：$\operatorname{sinc}(t)=\frac{\sin\pi t}{\pi t}\leftrightarrow p_{2\pi}(\omega)$，即 $|\omega|<\pi$ 时为 $1$、其余为 $0$。

**Q32** (b)
> **公式表**：$p_\tau(t)\leftrightarrow\tau\operatorname{sinc}\left(\frac{\omega\tau}{2\pi}\right)$，$\tau=6$。
> $$U=6\operatorname{sinc}\left(\frac{6\omega}{2\pi}\right)=6\operatorname{sinc}\left(\frac{3\omega}{\pi}\right).$$

**Q33** 首个正零点 $\omega=4\pi=12.566$
> **公式表**：同上，$\tau=0.5$。
> $$\frac{\omega\tau}{2\pi}=1\ \Rightarrow\ \omega=\frac{2\pi}{\tau}=4\pi.$$

**Q34** $U(j\pi/4)=\frac8\pi=2.5465$
> **公式表**：$p_4(t)\leftrightarrow4\operatorname{sinc}\left(\frac{2\omega}{\pi}\right)$。
> $$U(j\pi/4)=4\operatorname{sinc}\frac12=4\cdot\frac{\sin(\pi/2)}{\pi/2}=\frac8\pi.$$

**Q35** (i) C　(ii) A　(iii) D　(iv) B
> **公式表**：周期信号 $U=2\pi\sum c_k\delta(\omega-k\omega_0)$；脉冲串 $c_k=Ad\operatorname{sinc}(kd)$，$A=1,\tau=1,d=1/T$。
> $$c_k=\frac1T\operatorname{sinc}\frac kT,\qquad \omega_k=k\frac{2\pi}{T},\qquad Tc_k=\operatorname{sinc}\frac kT=\operatorname{sinc}\frac{\omega_k}{2\pi}.$$
> 所有谱线都落在同一条包络 $\operatorname{sinc}\frac{\omega}{2\pi}$ 上（包络只由脉宽决定）。谱线间隔 $\omega_0=\frac{2\pi}{T}$：$T=2.5\to2.513$（最稀，C）；$T=5\to1.257$（A）；$T=10\to0.628$（最密，D）；单脉冲无离散谱线，$U=p_1(\omega)=\operatorname{sinc}\frac{\omega}{2\pi}$（B）。

**Q36** $|U(j4)|=0.2$
> **公式表**：$e^{-3t}H(t)\leftrightarrow\frac1{3+j\omega}$。
> $$|U(j4)|=\frac1{|3+4j|}=\frac15=0.2.$$

**Q37** $2.00000\times10^{-4}$
> **公式表**：$e^{-a|t|}\leftrightarrow\frac{2a}{a^2+\omega^2}$。
> $$\omega=a:\quad |U(ja)|=\frac{2a}{a^2+a^2}=\frac1a=\frac1{5000}=2\times10^{-4}.$$

**Q38** $-53.1301^\circ$
> **公式表**：$G(j\omega)=\frac1{3+j\omega}$。
> $$\arg G(j4)=-\arg(3+4j)=-\arctan\frac43=-53.1301^\circ.$$

**Q39** (c)
> **公式表**：时移性质 $u(t-t_0)\leftrightarrow e^{-j\omega t_0}U(j\omega)$。
> $$|Y|=|e^{-j5\omega}||U|=|U|,\qquad \arg Y=\arg U-5\omega.$$

**Q40** (c)
> **公式表**：尺度性质 $u(at)\leftrightarrow\frac1{|a|}U\left(j\frac{\omega}{a}\right)$，$a=3$。
> $$u(3t)\leftrightarrow\frac13U\left(j\frac{\omega}{3}\right):$$
> 频谱展宽 $3$ 倍（$\omega\to\omega/3$ 的反向映射），峰值降为 $\frac13$。

**Q41** $Y(j\pi/2)=-\frac4\pi=-1.2732$
> **公式表**：尺度 $\frac1{|a|}U(j\omega/a)$、时移 $e^{-j\omega t_0}$、$p_\tau\leftrightarrow\tau\operatorname{sinc}\frac{\omega\tau}{2\pi}$。
> $$p_4(2t-4)=p_4\big(2(t-2)\big)\ \leftrightarrow\ \frac12\cdot4\operatorname{sinc}\left(\frac{\omega\cdot4/2}{2\pi}\right)e^{-j2\omega}=2\operatorname{sinc}\frac{\omega}{\pi}e^{-j2\omega}.$$
> $$\omega=\frac\pi2:\quad Y=2\cdot\frac{2}{\pi}\cdot e^{-j\pi}=-\frac4\pi.$$

**Q42** (b)
> **公式表**：对偶 $U(jt)\leftrightarrow2\pi u(-\omega)$；三角形 $\Lambda(t/\tau)\leftrightarrow\tau\operatorname{sinc}^2\left(\frac{\omega\tau}{2\pi}\right)$。
> 交换两域：$\tau\operatorname{sinc}^2\left(\frac{t\tau}{2\pi}\right)\leftrightarrow2\pi\Lambda(-\omega/\tau)$。因 $\Lambda$ 偶，频域仍为三角形。

**Q43** (a) $2\pi e^{-a|\omega|}$
> **公式表**：$e^{-a|t|}\leftrightarrow\frac{2a}{a^2+\omega^2}$，再对偶。
> $$\frac{2a}{a^2+t^2}\leftrightarrow2\pi e^{-a|-\omega|}=2\pi e^{-a|\omega|}.$$

**Q44** (b)
> **公式表**：对偶性质即 $U(jt)\leftrightarrow2\pi u(-\omega)$，因子 $2\pi$ 来自逆变换的 $\frac1{2\pi}$，并注意频率反转。

**Q45** (b) 卷积性质
> **公式表**：$(u*h)(t)\leftrightarrow U(j\omega)H(j\omega)$。

**Q46** (c) 相乘性质
> **公式表**：$u_1u_2\leftrightarrow\frac1{2\pi}U_1*U_2$。

**Q47** (b)
> **公式表**：$\cos\omega_0t\leftrightarrow\pi[\delta(\omega-\omega_0)+\delta(\omega+\omega_0)]$；微分乘 $j\omega$；$f(\omega)\delta(\omega\mp\omega_0)=f(\pm\omega_0)\delta(\omega\mp\omega_0)$。
> $$j\omega\pi[\delta(\omega-\omega_0)+\delta(\omega+\omega_0)]=j\pi\omega_0[\delta(\omega-\omega_0)-\delta(\omega+\omega_0)].$$

**Q48** (d)
> **公式表**：微分性质 $u'\leftrightarrow j\omega U$；$e^{-3t}H(t)\leftrightarrow\frac1{3+j\omega}$。
> $$j\omega\cdot\frac1{3+j\omega}=\frac{j\omega}{3+j\omega}.$$
> 校验：$u'=\delta(t)-3e^{-3t}H(t)\leftrightarrow1-\frac3{3+j\omega}=\frac{j\omega}{3+j\omega}$。

**Q49** $Y(j5)=15+10j$
> **公式表**：微分性质 $Y=j\omega U$。
> $$Y(j5)=j5(2-3j)=10j-15j^2=15+10j.$$

**Q50** (a)
> **公式表**：$e^{jk\omega_0t}\leftrightarrow2\pi\delta(\omega-k\omega_0)$，再由线性性：
> $$U=2\pi\sum_kc_k\delta(\omega-k\omega_0).$$

**Q51** $4\pi+2\pi j\approx12.566+6.283j$
> **公式表**：$c_k=\frac{a_k-jb_k}{2}$，冲激权重 $2\pi c_k$。
> $$a_1=4,\ b_1=-2\ \Rightarrow\ c_1=\frac{4+2j}{2}=2+j,$$
> $$\text{权重}=2\pi c_1=4\pi+2\pi j.$$

**Q52** $u(0)=5$
> **公式表**：周期 FT 的权重除以 $2\pi$ 得 $c_k$；$u(0)=\sum_kc_k$。
> $$c_0=3,\quad c_1=1-2j,\quad c_{-1}=1+2j,$$
> $$u(0)=3+(1-2j)+(1+2j)=5.$$

**Q53** (a)
> **公式表**：能量 Parseval
> $$E=\int|u(t)|^2dt=\frac1{2\pi}\int|U(j\omega)|^2d\omega.$$

**Q54** $E=\frac3\pi=0.9549$
> **公式表**：$\frac{\sin Wt}{\pi t}\leftrightarrow p_{2W}(\omega)$，$W=3$，故 $U=p_6(\omega)$；能量 Parseval。
> $$E=\frac1{2\pi}\int_{-3}^{3}1\,d\omega=\frac{6}{2\pi}=\frac3\pi.$$

---

## 三、频率响应（Q55–Q71）

> 公式表没有单列频率响应，但 $G(j\omega)$ 就是 $h(t)$ 的傅里叶变换；正弦稳态由 $y_{ss}=A|G(j\omega)|\cos(\omega t+\varphi+\angle G(j\omega))$ 给出。

**Q55** $y_{ss}=1.41421\cos(2t-15^\circ)$
> 输入 $\omega=2$：
> $$G(j2)=\frac{2+2j}{-4+10j+4}=\frac{2+2j}{10j}=0.2-0.2j,$$
> $$|G|=\sqrt{0.08}=0.28284,\qquad \angle G=-45^\circ,$$
> $$y_{ss}=5\cdot0.28284\cos(2t+30^\circ-45^\circ).$$

**Q56** (b) $0.894\cos(10t-24.0^\circ)$
> $$G(j10)=\frac{0.1+10j}{5+10j},\qquad |G|=\frac{\sqrt{100.01}}{\sqrt{125}}=0.8944,$$
> $$\angle G=\arctan\frac{10}{0.1}-\arctan\frac{10}{5}=89.43^\circ-63.43^\circ=26.0^\circ,$$
> 输出相位 $-50^\circ+26^\circ=-24^\circ$。

**Q57** $h_{\rm RMS}=0.707107$
> 由方程 $(m(j\omega)^2+bj\omega+k)H=(bj\omega+k)R$：
> $$G(j\omega)=\frac{k+bj\omega}{k-m\omega^2+bj\omega}=\frac{2+3j\omega}{2-\omega^2+3j\omega}.$$
> $\omega=2$：$G(j2)=\frac{2+6j}{-2+6j}$，分子分母模均为 $\sqrt{40}$，故 $|G|=1$。峰值 $=1$，$h_{\rm RMS}=\frac{1}{\sqrt2}$。

**Q58** $|G(j2)|=0.5$，$\arg=90^\circ$
> $$G(j2)=\frac{2(-4)+4}{-4+8j+4}=\frac{-4}{8j}=0.5j.$$

**Q59** $-45.0000^\circ$
> $$\arg\frac{300}{4+4j}=0-\arctan\frac44=-45^\circ.$$

**Q60** $|G|=4.8$
> $$|G|=\frac{10}{\left|1+\frac34j\right|\left|1+\frac43j\right|}=\frac{10}{\frac54\cdot\frac53}=\frac{120}{25}=4.8.$$

**Q61** $y_{ss}=0.5$
> **公式表**：常数输入取 $\omega=0$（$G(0)$ 为直流增益）。
> $$G(0)=\frac{1}{1\cdot2}=0.5,\qquad y_{ss}=0.5\cdot1.$$

**Q62** $y_{\rm DC}=0.636620$
> **公式表**：周期输入的输出系数 $d_k=c_kG(jk\omega_0)$（由 $U=2\pi\sum c_k\delta$ 与 $Y=GU$）。
> $$c_0=\frac1\pi\int_0^\pi\sin t\,dt=\frac2\pi,\qquad G(0)=1,$$
> $$d_0=c_0G(0)=\frac2\pi.$$

**Q63** (d) $y=2.00$
> **公式表**：$h(t)=3e^{-6t}H(t)\leftrightarrow G(j\omega)=\frac3{6+j\omega}$。
> $$G(0)=\frac36=0.5,\qquad y=4\cdot0.5=2.$$

**Q64** $-8.00000$ dB
> 一阶系统 $|G|\approx\frac{|G(0)|}{\sqrt{1+(\omega/\omega_c)^2}}$，$\omega\gg\omega_c$ 时每 decade 降 $20$ dB。$\frac{2000}{200}=10$ 恰为一个 decade：
> $$12-20\log_{10}10=-8\ \text{dB}.$$

**Q65** (a) $-90^\circ$
> 渐近相频：$\omega_c/10$ 处 $0^\circ$，$10\omega_c$ 处 $-90^\circ$。$\omega=10^4=10\omega_c$ 恰在右端点，读渐近值 $-90^\circ$（$-84.29^\circ$ 是精确值，不是渐近值）。

**Q66** $\omega_{-3\rm dB}=3$
> **公式表**：$G(j\omega)=\frac1{3+j\omega}$。
> $$\frac{|G(j\omega)|}{|G(0)|}=\frac{3}{\sqrt{9+\omega^2}}=\frac1{\sqrt2}\ \Rightarrow\ \omega^2=9\ \Rightarrow\ \omega=3.$$

**Q67** (i) B　(ii) D　(iii) A　(iv) C
> **公式表**：二阶标准形 $(j\omega)^2+2\zeta\omega_n(j\omega)+\omega_n^2$；$\zeta<\frac1{\sqrt2}$ 才有峰；每个极点贡献 $-20$ dB/decade。
> (ii) $\omega_n=100$，$2\zeta\omega_n=10\Rightarrow\zeta=0.05<0.707$：有尖峰，两个极点 → 末端 $-40$ dB/dec，对应 D。
> (iii) $\omega_n=10$，$2\zeta\omega_n=20\Rightarrow\zeta=1$：无峰，$-40$ dB/dec，对应 A。
> (i) 单极点 $-20$ dB/dec，无峰，对应 B。
> (iv) 一阶 × 二阶共三个极点，末端 $-60$ dB/dec，且含 (ii) 的尖峰，对应 C。

**Q68** $h(t)=4e^{-2t}H(t)$
> **公式表**：$\frac1{a+j\omega}\leftrightarrow e^{-at}H(t)$。
> $$G(j\omega)=4\cdot\frac1{2+j\omega}\ \leftrightarrow\ 4e^{-2t}H(t).$$

**Q69** $h(t)=2e^{-5(t-3)}H(t-3)$
> **公式表**：与 $\delta(t-t_0)$ 卷积即时移（$\delta(t-t_0)\leftrightarrow e^{-j\omega t_0}$，卷积→乘积）。
> $$h=2e^{-5t}H(t)*\delta(t-3)=2e^{-5(t-3)}H(t-3).$$

**Q70** (d)
> **公式表**：线性 + $\frac1{a+j\omega}\leftrightarrow e^{-at}H(t)$。
> $$\frac3{1+j\omega}\leftrightarrow3e^{-t}H(t),\qquad \frac2{4+j\omega}\leftrightarrow2e^{-4t}H(t).$$

**Q71** (d) $\frac{20}{(3+j\omega)^2+25}$
> **公式表**：$e^{-at}\sin(\omega_0t)H(t)\leftrightarrow\frac{\omega_0}{(a+j\omega)^2+\omega_0^2}$，$a=3,\omega_0=5$。
> $$4\cdot\frac{5}{(3+j\omega)^2+25}=\frac{20}{(3+j\omega)^2+25}.$$

---

## 四、二阶系统与稳定性（Q72–Q85）

**Q72** (c) $\zeta=1.0$
> **公式表**：特征方程 $(j\omega)^2+2\zeta\omega_n(j\omega)+\omega_n^2=0$，判别式 $\Delta=4\omega_n^2(\zeta^2-1)$。临界阻尼 $\Delta=0\Rightarrow\zeta=1$，两极点重合于 $-\omega_n$。

**Q73** (c) $0.707$
> 极点几何关系：$\omega_n=|p|$，$\zeta=\frac{|\Re p|}{\omega_n}$。
> $$|p|=\sqrt{(10^4)^2+(10^4)^2}=10^4\sqrt2,\qquad \zeta=\frac{10^4}{10^4\sqrt2}=\frac1{\sqrt2}.$$

**Q74** (a)
> **公式表**：$\omega_r=\omega_n\sqrt{1-2\zeta^2}$，需 $\zeta<\frac1{\sqrt2}$。
> $$1-2(0.8)^2=-0.28<0,$$
> 无实 $\omega_r$，幅频从 $|G(j0)|$ 单调下降。$K$ 只缩放高度，不影响峰的存在。

**Q75** $\omega_r=959.166$，$M_r=2.55155$（$8.13609$ dB）
> **公式表**：二阶标准形；RLC 取电容电压时 $\omega_n=\frac1{\sqrt{LC}}$，$\zeta=\frac R2\sqrt{\frac CL}$；$\omega_r=\omega_n\sqrt{1-2\zeta^2}$，$M_r=\frac{|K|}{2\zeta\sqrt{1-\zeta^2}}$。
> $$LC=0.5\cdot2\times10^{-6}=10^{-6}\ \Rightarrow\ \omega_n=1000,$$
> $$\zeta=\frac{200}{2}\sqrt{\frac{2\times10^{-6}}{0.5}}=100\cdot2\times10^{-3}=0.2<0.707\ (\text{有峰}),$$
> $$\omega_r=1000\sqrt{1-2(0.04)}=959.166,$$
> $$M_r=\frac{1}{2(0.2)\sqrt{1-0.04}}=2.55155,\qquad 20\lg M_r=8.13609\ \text{dB}.$$

**Q76** (c) $\alpha=0.05$
> 极点 $-\alpha\pm j5$：$\omega_n=\sqrt{\alpha^2+25}$，$\zeta=\frac{\alpha}{\sqrt{\alpha^2+25}}$。$\alpha$ 越小 $\zeta$ 越小，$M_r=\frac1{2\zeta\sqrt{1-\zeta^2}}$ 越大、峰越尖。
> $$\alpha=0.05:\ \zeta\approx0.01,\ M_r\approx50;\quad \alpha=5:\ \zeta=0.707,\ \text{无峰}.$$

**Q77** (a)
> **公式表**：极点全在左半平面 → 稳定；虚轴单根（其余左半平面）→ 临界稳定；虚轴重根 → 不稳定。
> 分母 $(s+2)(s^2+4)=0$：极点 $s=-2,\ \pm2j$。无右半平面极点；$\pm2j$ 为单根，互异；分子不抵消。$h$ 含 $e^{\pm j2t}$，有界但不趋于零 → 临界稳定。

**Q78** (b)
> 极点 $s=-1$，$\pm2j$（各二重）。无右半平面极点，但虚轴上有重根，$h$ 含 $t\cos2t,\ t\sin2t$，幅度随 $t$ 增长 → 不稳定。

**Q79** (c)
> **公式表**：BIBO（真有理）$\iff$ 所有极点实部严格小于零。
> (a) $s^2-4s+9=0\Rightarrow s=2\pm j\sqrt5$，右半平面；(b) $s=3>0$；(c) $s=-1,-2$，全在左半平面；(d) $s=0$（虚轴）与 $s=-2$。只有 (c) BIBO 稳定。

**Q80** (d)
> 特征方程 $\tau s+1=0\Rightarrow s=-\frac1\tau=-\frac1{-4}=0.25>0$，自然响应含 $e^{0.25t}$ → 不稳定；$\beta$ 只改幅度，不改极点。

**Q81** (b) $\zeta=-0.1$
> 极点实部 $-\zeta\omega_n$，$\omega_n=5$：
> $$\zeta=1\to-5,\quad -0.1\to+0.5,\quad 0.3\to-1.5,\quad 2\to-10.$$
> 只有 $\zeta=-0.1$ 使实部为正，$e^{0.5t}$ 增长、无界。

**Q82** (c)
> 特征方程 $as^2+bs+c=0$，$a,b,c>0$，两根
> $$s_{1,2}=\frac{-b\pm\sqrt{b^2-4ac}}{2a}.$$
> 实根时 $\sqrt{b^2-4ac}<b$，两根均负；复根时实部 $-\frac b{2a}<0$。两种情形均有 $y\to0$。

**Q83** $\int|h|dt=1.5$，BIBO 稳定
> **公式表**：BIBO 稳定的充要条件 $\int|h|dt<\infty$。
> $$\int_{-\infty}^{\infty}|h|dt=\int_0^\infty3e^{-2t}dt=\frac32<\infty.$$

**Q84** (c)
> **公式表**：$H(t)\leftrightarrow\pi\delta(\omega)+\frac1{j\omega}$；极点 $s=0$；$|h|\le1$ 但 $h\not\to0$ → 临界稳定；$\int_0^\infty|h|dt=\infty$ → 不 BIBO。有界输入 $H(t)$ 给出斜坡 $tH(t)$，无界。

**Q85** (b) 只有 A
> **公式表**：BIBO $\iff\int|h|dt<\infty$；频率响应存在要求 $\int h e^{-j\omega t}dt$ 收敛。
> $$A:\ \int_0^\infty300e^{-4t}dt=\frac{300}{4}=75<\infty,\quad G_A=\frac{300}{4+j\omega};$$
> $$B:\ \int_0^\infty300e^{4t}dt=\infty,$$
> 且 $e^{4t}$ 增长使傅里叶积分发散（收敛域 $\Re s>4$ 不含虚轴）。
