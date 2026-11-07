---
title: ELEC2302/9302 Signals and Systems — Quiz 2 practice questions, answers and feedback
course: ELEC2302/9302 Signals and Systems
tags:
  - 信号与系统
  - Quiz2
  - 习题
---

# ELEC2302/9302 Signals and Systems — Quiz 2 practice questions, answers and feedback[^1]

> [!info] How to use this question bank
> *don't* work through the questions from beginning to end. Start by doing one question from each group, identify the areas where you are less confident, and work on those first.

The correct option is marked ✓.

## 1. Fourier series (week 4)

### Fundamental frequency of a sum of sinusoids

**1.** A signal is given by

$$
u(t)=\cos\left(\frac{2}{3}t+\frac{\pi}{6}\right)+\sin\left(\frac{4}{5}t+\frac{\pi}{4}\right)
$$

Is $u(t)$ periodic, and if so what is its fundamental frequency $\omega_0$?

- (a) Periodic, $\omega_0 = 1/15$ rad/s
- (b) Periodic, $\omega_0 = 4/5$ rad/s (the larger of the two frequencies)
- (c) Not periodic, because $2/3$ and $4/5$ are not integers
- (d) Periodic, $\omega_0 = 2/15$ rad/s ✓

> [!note] Feedback
> Write both frequencies over a common denominator, $10/15$ and $12/15$, and take $\omega_0$ as their greatest common divisor.

- **(a)** $1/15$ rad/s does divide both frequencies, but so does $2/15$, so it is not the fundamental.
- **(b)** The $\cos(2t/3)$ term does not repeat over one period of $\sin(4t/5)$, so $4/5$ rad/s cannot be the fundamental.
- **(c)** The test is on the ratio $(2/3)/(4/5)=5/6$, which is rational, so $u(t)$ is periodic even though neither frequency is an integer.
- **(d)** Correct. The two components are the 5th and 6th harmonics of $2/15$ rad/s.

**2.** A signal is given by

$$
u(t)=2+7\cos\left(\frac{1}{2}t+\theta_1\right)+3\cos\left(\frac{2}{3}t+\theta_2\right)+5\cos\left(\frac{7}{6}t+\theta_3\right)
$$

Find its fundamental frequency $\omega_0$, in rad/s.

*Answer:* 0.1667 rad/s

> [!note] Feedback
> Put the three frequencies over a common denominator, $3/6$, $4/6$ and $7/6$, and take the greatest common divisor of the numerators. This gives $\omega_0 = 1/6 = 0.1667$ rad/s, with the constant term imposing no constraint.

**3.** A signal is given by $u(t)=\cos(3t)+\sin(\sqrt{5}\,t)$. Is $u(t)$ periodic?

- (a) Yes, periodic with $\omega_0 = 3$ rad/s, the smaller of the two frequencies
- (b) Yes – any sum of two sinusoids is periodic
- (c) Yes, periodic with $\omega_0 = \sqrt{5}-3$ rad/s
- (d) No – a sum of two sinusoids is periodic only if the ratio of their frequencies is rational, and $3/\sqrt{5}$ is irrational ✓

> [!note] Feedback
> A sum of two sinusoids is periodic only if the ratio of their frequencies is rational, and $3/\sqrt{5}$ is irrational.

- **(a)** No common period exists here, so no component frequency can serve as a fundamental.
- **(b)** A sum repeats only when one period $T$ holds a whole number of cycles of each component, which fails here.
- **(c)** The difference of two frequencies is a beat rate rather than a fundamental, and $\sqrt{5}-3$ is negative.
- **(d)** Correct. No $T$ satisfies both $3T = 2\pi m$ and $\sqrt{5}\,T = 2\pi n$ for integers $m$ and $n$.

### Fourier series coefficients

**4.** A periodic signal $u(t)$ of period $T$ satisfies $u(t-T/2)=-u(t)$. Which of its Fourier coefficients $c_k$ must be zero?

- (a) Only $c_0$
- (b) $c_k$ for every even $k$ (including $c_0$) ✓
- (c) $c_k$ for every odd $k$
- (d) None – the condition only affects the phase of $c_k$, not which ones vanish

> [!note] Feedback
> Substituting $u(t-T/2)=-u(t)$ into the analysis integral gives $c_k e^{-jk\pi}=-c_k$, that is $\left(1+(-1)^k\right)c_k=0$.

- **(a)** The same condition also forces $c_2$, $c_4$ and every other even coefficient to zero, not only the mean.
- **(b)** Correct. Even $k$ makes $(-1)^k=+1$, and $k=0$ is even.
- **(c)** Odd $k$ makes $(-1)^k=-1$, so the condition holds automatically and those coefficients survive.
- **(d)** A $\pm 1$ square wave satisfies this condition and has $c_0=c_2=0$, so coefficients really do vanish.

**5.** The sawtooth wave $u(t)=2At/T$ for $|t|<T/2$ (period $T$) has which of the following properties?

- (a) $b_k = 0$ for all $k$; every $c_k$ is purely real
- (b) $a_k = 0$ for all $k$ and $c_0 = 0$; every $c_k$ is purely imaginary ✓
- (c) Only the odd-indexed $c_k$ are nonzero, as for a square wave satisfying $u(t-T/2)=-u(t)$
- (d) $c_0 = A$, the peak value of the ramp

> [!note] Feedback
> The ramp $2At/T$ on $|t|<T/2$ is an odd function, so every cosine coefficient vanishes and $c_k = jA(-1)^k/(k\pi)$ is purely imaginary.

- **(a)** Real $c_k$ with $b_k=0$ describes an even signal, and the ramp is odd.
- **(b)** Correct. The mean over a period is zero as well, so $c_0=0$.
- **(c)** The sawtooth does not satisfy $u(t-T/2)=-u(t)$, and its even harmonics are nonzero, for instance $c_2 = 0.1592j$ when $A=1$.
- **(d)** $c_0$ is the average over one period, which is zero here, not the peak of the ramp.

**6.** A periodic signal is $u(t)=1$ for $|t|<\pi/2$ and $0$ for $\pi/2<|t|<\pi$, repeated with period $2\pi$: an even square pulse train with 50% duty cycle. Once its DC component is removed, which coefficients remain nonzero?

- (a) Only the odd-indexed $b_k$
- (b) All $a_k$, $k\ge 1$, decaying as $1/k$
- (c) Only $a_2, a_4, a_6, \dots$
- (d) Only the odd-indexed $a_k$ – the signal is even, and once the DC offset is removed it satisfies $u(t-T/2)=-u(t)$, which kills every even harmonic ✓

> [!note] Feedback
> Evenness kills every $b_k$, and subtracting the mean $1/2$ leaves a $\pm 1/2$ wave satisfying $u(t-T/2)=-u(t)$, which kills every even harmonic.

- **(a)** The pulse train is even, so $b_k=0$ for every $k$.
- **(b)** The $1/k$ envelope is right, but the even-indexed $a_k$ are zero, so only every second coefficient is present.
- **(c)** The even-indexed $a_k$ are the ones that vanish, leaving $a_1, a_3, a_5, \dots$
- **(d)** Correct. The survivors are $a_k = (2/\pi)(-1)^{(k-1)/2}/k$ for odd $k$.

**7.** An even, bipolar square wave ($+A$ for $|t|<T/4$, $-A$ for $T/4<|t|<T/2$) has amplitude $A=6$. Find $c_5$, to 4 significant figures.

*Answer:* 0.7639

> [!note] Feedback
> Write the bipolar wave over one period as $2A\,p_{T/2}(t)-A$, so $c_k = A\,\mathrm{sinc}(k/2)$ for $k\neq 0$. Then $c_5 = 6\,\mathrm{sinc}(5/2)=12/(5\pi)=0.7639$, in the units of $A$ and independent of $T$.

**8.** A full-wave rectified sine $u(t)=A|\sin(\omega_m t)|$ has amplitude $A=7$. Find $c_3$, to 4 significant figures.

*Answer:* −0.1273

> [!note] Feedback
> Rectifying halves the period to $\pi/\omega_m$, so $\omega_0 = 2\omega_m$ and
> $$c_k = \frac{\omega_m}{\pi}\int_0^{\pi/\omega_m} A\sin(\omega_m t)\,e^{-2jk\omega_m t}\,\mathrm{d}t = \frac{2A}{\pi(1-4k^2)}$$
> With $A=7$ and $k=3$ that is $14/(\pi(1-36))=-2/(5\pi)=-0.1273$, independent of $\omega_m$.

**9.** A pulse train $u(t)=A\,p_\tau(t)$ (period $T$, duty cycle $d=\tau/T=1/3$) has Fourier coefficients $c_k = Ad\,\mathrm{sinc}(kd)$. For which smallest positive integer $k$ does $c_k=0$?

- (a) $k=2$
- (b) $c_k$ is never zero when $d=1/3$
- (c) $k=3$ ✓
- (d) $k=1$

> [!note] Feedback
> The normalised sinc, $\sin(\pi x)/(\pi x)$, is zero when $x$ is a nonzero integer, so $c_k$ first vanishes when $kd=1$.

- **(a)** $k=2$ is the first null for a 50% duty cycle, not for $d=1/3$.
- **(b)** Here $\mathrm{sinc}(3\times\tfrac{1}{3})=\mathrm{sinc}(1)=0$, so $c_3$ does vanish.
- **(c)** Correct. The first null is at $k=1/d=3$.
- **(d)** Keep the duty-cycle factor in the argument and solve $k/3=1$, not $k=1$.

**10.** A periodic signal $u(t)$ with period $T$ equals $+8$ for a quarter of each period and $-2$ for the remaining three-quarters. Find $c_0$.

*Answer:* 0.5

> [!note] Feedback
> $c_0$ is the mean over one period, weighting each level by the fraction of the period it occupies: $\tfrac{1}{4}(+8)+\tfrac{3}{4}(-2)=2-1.5=0.5$, in the units of $u$ and independent of $T$.

**11.** A signal $u(t)$ has period $T=2$ and is defined on one period by $u(t)=1$ for $0<t<1$ and $u(t)=-1$ for $1<t<2$ (repeating). Its complex Fourier coefficient $c_0$ is:

- (a) $c_0=-1$
- (b) $c_0=0.5$
- (c) $c_0=0$ ✓
- (d) $c_0=1$

> [!note] Feedback
> $c_0$ is the mean over one period: $\tfrac{1}{2}\left[(+1)(1)+(-1)(1)\right]=0$.

- **(a)** $-1$ is the value taken on the second half-period, not the average of the two halves.
- **(b)** Integrating only over $0<t<1$ gives $0.5$, but $1<t<2$ contributes $-0.5$.
- **(c)** Correct. The signal spends equal time at $+1$ and $-1$.
- **(d)** $1$ is the average of $|u(t)|$, not of $u(t)$.

**12.** A signal of period $1$ equals $1/\sqrt{d}$ on $0\le t<d$ and $0$ on the rest of each period, where $0<d<1$. For $d=0.01$, find $c_0$.

- (a) 0.01
- (b) 0.1 ✓
- (c) 10
- (d) 1

> [!note] Feedback
> $c_0$ is height times width divided by the period: $(1/\sqrt{d})(d)/1=\sqrt{d}$.

- **(a)** $0.01$ is the duty cycle $d$, which would be the mean only if the pulse height were $1$.
- **(b)** Correct. $\sqrt{0.01}=0.1$.
- **(c)** $10$ is the pulse height $1/\sqrt{d}$, which comes from averaging over the pulse width instead of the period.
- **(d)** $1$ is the average power of this normalised pulse, not its mean value.

**13.** In the exponential Fourier series $u(t)=\sum_k c_k e^{jk\omega_0 t}$ of a real signal, the term with index $k=-3$ is best interpreted as:

- (a) The complex conjugate of $c_2$
- (b) A genuinely negative-frequency oscillation, physically distinct from the $k=+3$ component
- (c) One half of the real sinusoidal component at frequency $3\omega_0$, which pairs with the $k=+3$ term to form $2|c_3|\cos(3\omega_0 t + \arg c_3)$ ✓
- (d) A numerical artefact that can be discarded without changing $u(t)$

> [!note] Feedback
> For real $u(t)$ the coefficients satisfy $c_{-k}=\overline{c_k}$, so the $k=\pm 3$ terms are conjugate halves of a single real sinusoid.

- **(a)** Conjugate symmetry pairs index $-3$ with $+3$, so $c_{-3}=\overline{c_3}$, not $\overline{c_2}$.
- **(b)** Neither half is a signal on its own, and only their sum $2|c_3|\cos(3\omega_0 t+\arg c_3)$ is real.
- **(c)** Correct.
- **(d)** Dropping the $k=-3$ term leaves a complex signal with half the amplitude at $3\omega_0$.

**14.** A periodic signal’s complex Fourier coefficient is $c_1 = 2-3j$. Using the convention $\left(a_k = 2\operatorname{Re}c_k,\ b_k = -2\operatorname{Im}c_k\right)$, the pair $(a_1,b_1)$ is:

- (a) $(-6, 4)$
- (b) $(2, -3)$
- (c) $(4, 6)$ ✓
- (d) $(4, -6)$

> [!note] Feedback
> Apply $a_k = 2\operatorname{Re}c_k$ and $b_k = -2\operatorname{Im}c_k$ to $c_1 = 2-3j$.

- **(a)** Take $a_1$ from the real part and $b_1$ from the imaginary part, not the other way round.
- **(b)** Multiply by 2 and flip the sign of the imaginary part rather than reading $(a_1,b_1)$ straight off $c_1$.
- **(c)** Correct. $a_1 = 2(2)=4$ and $b_1 = -2(-3)=6$.
- **(d)** Keep the minus sign in $b_k = -2\operatorname{Im}c_k$, which makes $b_1$ positive here.

**15.** The sine–cosine Fourier series of a periodic signal $u(t)$ contains the term $3\cos(2\omega_0 t)+4\sin(2\omega_0 t)$ (i.e. $a_2=3$, $b_2=4$). Find $|c_2|$.

*Answer:* 2.500

> [!note] Feedback
> From $c_k = (a_k - jb_k)/2$, the magnitude is $|c_2| = \sqrt{a_2^2+b_2^2}/2 = \sqrt{9+16}/2 = 2.500$.

**16.** A periodic signal is

$$
u(t)=2+6\cos(300t)+8\sin(500t)
$$

Which set of Fourier coefficients describes it?

- (a) $\omega_0=100$ rad/s, $c_0=2$, $c_1=c_{-1}=3$, $c_2=-4j$, $c_{-2}=4j$, all others zero
- (b) $\omega_0=100$ rad/s, $c_0=2$, $c_3=c_{-3}=3$, $c_5=4j$, $c_{-5}=-4j$, all others zero
- (c) $\omega_0=100$ rad/s, $c_0=2$, $c_3=c_{-3}=3$, $c_5=-4j$, $c_{-5}=4j$, all others zero ✓
- (d) $\omega_0=100$ rad/s, $c_0=2$, $c_3=c_{-3}=6$, $c_5=-8j$, $c_{-5}=8j$, all others zero

> [!note] Feedback
> The fundamental is $\gcd(300,500)=100$ rad/s, so the harmonics are $k=3$ and $k=5$, with $c_{\pm 3}=a_3/2=3$ and $c_5=-jb_5/2=-4j$.

- **(a)** Index the harmonics by $k=\omega/\omega_0$, giving 3 and 5, not by the order in which the terms are written.
- **(b)** These coefficients encode $-8\sin(500t)$, because $1/j=-j$ puts the minus sign on $c_{+5}$.
- **(c)** Correct.
- **(d)** Halve both amplitudes, since $c_k=(a_k-jb_k)/2$.

### Parseval's theorem for periodic signals

**17.** Parseval’s theorem for a periodic signal $u(t)$ states that its average power is:

- (a) $\displaystyle \int_{-\infty}^{\infty} |c_k|\,\mathrm{d}\omega$
- (b) $|c_0|^2$ alone
- (c) $\displaystyle \sum_{k=-\infty}^{\infty} c_k$
- (d) $\displaystyle \sum_{k=-\infty}^{\infty} |c_k|^2$ ✓

> [!note] Feedback
> Average power is $\frac{1}{T}\int_0^T |u|^2\,\mathrm{d}t = \sum_k |c_k|^2$, a sum of squared magnitudes over all $k$, negative indices included.

- **(a)** A periodic signal has a discrete set of coefficients, so sum over $k$ and square the magnitudes.
- **(b)** $|c_0|^2$ is the power in the DC term alone and omits every harmonic.
- **(c)** Adding the coefficients themselves gives $u(0)$, a signal value rather than a power, and it need not be real.
- **(d)** Correct.

**18.** An odd, bipolar square wave of amplitude $A=1$ (period $T$, so $|u(t)|=1$ always) has $c_k=-2j/(\pi k)$ for odd $k$, zero otherwise. What percentage of its total average power is carried by the fundamental component alone ($k=\pm 1$)? Give your answer to 4 significant figures.

*Answer:* 81.06

> [!note] Feedback
> Parseval gives the total power as $\sum_k|c_k|^2$, and $|u(t)|=1$ at every instant makes that total $1$. The pair $k=\pm 1$ contributes $2|c_1|^2 = 2(2/\pi)^2 = 8/\pi^2 = 81.06\%$.

**19.** A rectangular pulse train $A\,p_\tau(t)$ of period $T$ has duty cycle $d=\tau/T=0.25$. What fraction of its total average power is carried by the DC term $c_0$ alone?

*Answer:* 0.25

> [!note] Feedback
> The total power is $\frac{1}{T}\int |u|^2\,\mathrm{d}t = A^2 d$ and the DC power is $|c_0|^2=(Ad)^2$, so the fraction is $d^2/d=d=0.25$, whatever $A$ and $T$ are.

### Signals as vectors, projection and orthogonality

**20.** A square wave $u(t)$ has period $T=2\pi$, with $u(t)=+1$ for $0<t<\pi$ and $u(t)=-1$ for $\pi<t<2\pi$. It is approximated by a single complex sinusoid at the fundamental frequency, $u(t)\approx c\,e^{jt}$, with the complex constant $c$ chosen to minimise $\|u-c\,e^{jt}\|_P^2$. Find $c$.

*Answer:* −0.6366j

> [!note] Feedback
> The best $c$ is the projection $\langle u,\phi_1\rangle_P$ of $u$ onto $\phi_1(t)=e^{jt}$, which is the Fourier coefficient $c_1$ itself. Integrating over one period gives $c_1=\tfrac{1}{2}(a_1-jb_1)=-2j/\pi=-0.6366j$.

**21.** A real $T$-periodic signal $u(t)$ is approximated by $c\,\phi(t)$, with the real constant $c$ chosen to minimise $\|u-c\phi\|_P^2$. At that optimal $c$, the error signal $e(t)=u(t)-c\phi(t)$ satisfies:

- (a) $e(t)=0$ for every $t$
- (b) $\langle e,\phi\rangle_P=0$: the error is orthogonal to $\phi$ ✓
- (c) $\|e\|_P=\|u\|_P$
- (d) $\langle e,u\rangle_P=0$: the error is orthogonal to $u$

> [!note] Feedback
> At the minimising $c=\langle u,\phi\rangle_P/\|\phi\|_P^2$ the residual obeys $\langle u-c\phi,\phi\rangle_P=\langle u,\phi\rangle_P-c\|\phi\|_P^2=0$.

- **(a)** A one-term approximation reproduces $u(t)$ exactly only when $u$ is already a multiple of $\phi$.
- **(b)** Correct. The residual is orthogonal to whatever was projected onto.
- **(c)** The projection removes power, since $\|e\|_P^2=\|u\|_P^2-c^2\|\phi\|_P^2$, which leaves $\|e\|_P=\|u\|_P$ only when $c=0$.
- **(d)** Here $\langle e,u\rangle_P=\|e\|_P^2$, which vanishes only when the error itself is zero.

**22.** Two real $T$-periodic signals $u(t)$ and $y(t)$ are orthogonal, $\langle u,y\rangle_P=0$. Let $z(t)=u(t)+y(t)$. The average power $P(z)$ equals:

- (a) $P(u)-P(y)$
- (b) $P(u)P(y)$
- (c) $P(u)+P(y)$ ✓
- (d) $\left(\sqrt{P(u)}+\sqrt{P(y)}\right)^2$

> [!note] Feedback
> Expanding gives $P(z)=P(u)+2\operatorname{Re}\langle u,y\rangle_P+P(y)$, and orthogonality removes the cross term.

- **(a)** The cross term is removed, not $P(y)$, and subtracting powers could make $P(z)$ negative.
- **(b)** The expansion contains no product of $P(u)$ and $P(y)$.
- **(c)** Correct.
- **(d)** Squaring the sum of the rms values restores a cross term, which fits $y=\alpha u$ with $\alpha>0$, not orthogonal signals.


## 2. Fourier transform (week 5)

### Existence of the transform, and symmetry for real, even and odd signals

**23.** Which of the following signals does **not** possess a Fourier transform, not even one containing impulses?

- (a) $\cos(5t)$
- (b) $H(t)$
- (c) $1$
- (d) $e^{2t}H(t)$ ✓

> [!note] Feedback
> A bounded signal always has a transform, using impulses where necessary, but a signal that grows without bound has none.

- **(a)** $\cos(5t)$ transforms to $\pi\delta(\omega-5)+\pi\delta(\omega+5)$.
- **(b)** $H(t)$ transforms to $\pi\delta(\omega)+1/(j\omega)$.
- **(c)** The constant $1$ transforms to $2\pi\delta(\omega)$.
- **(d)** Correct. $e^{2t}$ grows without bound, so $\int_0^\infty e^{(2-j\omega)t}\,\mathrm{d}t$ diverges at every $\omega$.

**24.** $u(t)$ is real and odd, i.e. $u(-t)=-u(t)$. Which statement about $U(j\omega)$ must be true?

- (a) $U(j\omega)$ is real and an odd function of $\omega$
- (b) $U(j\omega)$ is purely imaginary and an odd function of $\omega$ ✓
- (c) $U(j\omega)$ is purely imaginary and an even function of $\omega$
- (d) $U(j\omega)$ is real and an even function of $\omega$

> [!note] Feedback
> For real odd $u(t)$ the analysis integral collapses to $U(j\omega) = -2j\int_0^\infty u(t)\sin(\omega t)\,\mathrm{d}t$.

- **(a)** The factor $j$ in front of the sine integral leaves nothing real behind.
- **(b)** Correct. The factor $j$ makes it imaginary and $\sin(\omega t)$ makes it odd in $\omega$.
- **(c)** Replacing $\omega$ by $-\omega$ flips the sign of $\sin(\omega t)$, so $U(j\omega)$ is odd.
- **(d)** Real and even is the case that gives a real even transform, through a cosine integral.

**25.** $u(t)$ is real. Which statement about its spectrum is always true?

- (a) Both $|U(j\omega)|$ and $\arg U(j\omega)$ are odd
- (b) Both $|U(j\omega)|$ and $\arg U(j\omega)$ are even
- (c) $|U(j\omega)|$ is even and $\arg U(j\omega)$ is odd ✓
- (d) $|U(j\omega)|$ is odd and $\arg U(j\omega)$ is even

> [!note] Feedback
> For real $u(t)$, $U(-j\omega)=\overline{U(j\omega)}$, and conjugation keeps the magnitude and reverses the sign of the phase.

- **(a)** A magnitude is never negative, so it cannot be odd unless $U(j\omega)$ vanishes everywhere.
- **(b)** Conjugation reverses the sign of the phase, so $\arg U(j\omega)$ is odd.
- **(c)** Correct.
- **(d)** Attach the even symmetry to the magnitude and the odd symmetry to the phase.

### Area relations between $u$ and $U(j\omega)$

**26.** $u(t)=3e^{-2t}H(t)-2e^{-5t}H(t)$. Find $U(0)$.

*Answer:* 1.1

> [!note] Feedback
> Use $e^{-at}H(t)\rightsquigarrow 1/(a+j\omega)$ with linearity and set $\omega=0$, which is the same as taking $\int u(t)\,\mathrm{d}t$. That gives $3/2-2/5=1.1$.

**27.** $U(j\omega)=4$ for $|\omega|<1$ and $0$ otherwise (i.e. $U(j\omega)=4\,p_2(\omega)$). Find $u(0)$.

*Answer:* 1.2732

> [!note] Feedback
> The inverse transform at $t=0$ is $u(0)=\frac{1}{2\pi}\int U(j\omega)\,\mathrm{d}\omega$, the area under $U(j\omega)$ divided by $2\pi$. Here that is $(4\times 2)/2\pi = 4/\pi = 1.2732$.

**28.** Evaluate $\displaystyle\int_{-\infty}^{\infty}\mathrm{sinc}(t)\,\mathrm{d}t$.

*Answer:* 1

> [!note] Feedback
> The integral of a signal is its transform at $\omega=0$. With $\mathrm{sinc}(t)=\sin(\pi t)/(\pi t)$, the pair $\sin(Wt)/(\pi t)\rightsquigarrow p_{2W}(\omega)$ at $W=\pi$ gives $p_{2\pi}(0)=1$.

### Transforms of standard signals

**29.** What is the Fourier transform of $u(t)=\delta(t-5)$?

- (a) $e^{-j5\omega}$ ✓
- (b) $5e^{-j\omega}$
- (c) $\delta(\omega-5)$
- (d) $e^{j5\omega}$

> [!note] Feedback
> Sifting the analysis integral with $\delta(t-5)$ evaluates the kernel $e^{-j\omega t}$ at $t=5$.

- **(a)** Correct. The delay goes into the exponent with a minus sign.
- **(b)** Put the 5 in the exponent, not in front as an amplitude factor.
- **(c)** A delay in time gives a linear phase. Sliding an impulse along $\omega$ is what modulation does.
- **(d)** The analysis integral uses the kernel $e^{-j\omega t}$, so the exponent is $-j5\omega$.

**30.** What is the Fourier transform of the constant signal $u(t)=1$, and why is the weight $2\pi$ (not 1) attached to the impulse?

- (a) $U(j\omega)=2\pi\delta(\omega)$, because $u(t)$ is synthesised from $u(t)=\frac{1}{2\pi}\int U(j\omega)e^{j\omega t}\,\mathrm{d}\omega$, so a single exponential of amplitude 1 needs an impulse of area $2\pi$ ✓
- (b) $U(j\omega)=\delta(\omega)$, because $u(t)=1=e^{j0t}$ needs an impulse of unit strength
- (c) $U(j\omega)=\delta(\omega)/2\pi$
- (d) $U(j\omega)=2\pi\delta(\omega)$, because $\int_{-\infty}^{\infty}1\,\mathrm{d}t=2\pi$

> [!note] Feedback
> Test a candidate by putting it through the synthesis integral $u(t)=\frac{1}{2\pi}\int U(j\omega)e^{j\omega t}\,\mathrm{d}\omega$.

- **(a)** Correct. The area $2\pi$ cancels the $\frac{1}{2\pi}$ and returns $e^{j0t}=1$.
- **(b)** An impulse of area 1 synthesises the constant $1/2\pi$, not 1.
- **(c)** Putting the $\frac{1}{2\pi}$ on $U(j\omega)$ as well as in the synthesis integral gives $1/(2\pi)^2$.
- **(d)** The transform is right but the reason is not: $\int_{-\infty}^{\infty}1\,\mathrm{d}t$ diverges rather than equalling $2\pi$.

**31.** What is the Fourier transform of $u(t)=\mathrm{sinc}(t)$?

- (a) $U(j\omega)=\mathrm{sinc}(\omega)$
- (b) $U(j\omega)=p_\pi(\omega)$
- (c) $U(j\omega)=p_{2\pi}(\omega)$, i.e. 1 for $|\omega|<\pi$ and 0 otherwise ✓
- (d) $U(j\omega)=\pi\,p_{2\pi}(\omega)$

> [!note] Feedback
> Read $\mathrm{sinc}(t)$ as $\sin(\pi t)/(\pi t)$ and apply $\sin(Wt)/(\pi t)\rightsquigarrow p_{2W}(\omega)$ with $W=\pi$.

- **(a)** The pulse and the sinc are partners, so the transform of a sinc is a gate rather than another sinc.
- **(b)** The pair gives $p_{2W}(\omega)$, not $p_W(\omega)$, so the band edge sits at $\pi$ and not $\pi/2$.
- **(c)** Correct. Unit height, with the cut-off at $|\omega|=\pi$.
- **(d)** The $\pi$ is already in the denominator of the normalised sinc, so the gate has unit height.

**32.** $u(t)=p_6(t)$ (a pulse of width 6, centred at the origin). What is $U(j\omega)$?

- (a) $6\,\mathrm{sinc}\left(\dfrac{\omega}{2\pi}\right)$
- (b) $6\,\mathrm{sinc}\left(\dfrac{3\omega}{\pi}\right)$ ✓
- (c) $\dfrac{1}{6}\,\mathrm{sinc}\left(\dfrac{3\omega}{\pi}\right)$
- (d) $6\,\mathrm{sinc}\left(\dfrac{\omega}{3\pi}\right)$

> [!note] Feedback
> Apply $p_\tau(t)\rightsquigarrow \tau\,\mathrm{sinc}(\omega\tau/2\pi)$ with $\tau=6$: $6\,\mathrm{sinc}(6\omega/2\pi)=6\,\mathrm{sinc}(3\omega/\pi)$.

- **(a)** Scale the argument by $\tau$ as well as the height, otherwise the first zero lands at $2\pi$ instead of $\pi/3$.
- **(b)** Correct.
- **(c)** The height is the pulse area $\tau=6$, not $1/\tau$.
- **(d)** Multiply $\omega$ by $\tau/2\pi$ rather than dividing by it, otherwise the first zero moves out to $3\pi$.

**33.** $u(t)=p_{0.5}(t)$ (a pulse of width 0.5

> [!warning] 原 PDF 此处问题被截断
> 题干在 “a pulse of width 0.5” 之后中断，四个选项在原文中缺失，仅保留下方的 Feedback。以下照录原文的 Feedback。

> [!note] Feedback
> With $\tau=0.5$ the transform is $0.5\,\mathrm{sinc}(\omega/4\pi)$. The normalised sinc first vanishes when its argument reaches 1, so $\omega=4\pi=12.566$ rad/s.

**34.** $u(t)=p_4(t)$. Evaluate $U(j\pi/4)$.

*Answer:* 2.5465

> [!note] Feedback
> With $\tau=4$ the transform is $4\,\mathrm{sinc}(4\omega/2\pi)=4\,\mathrm{sinc}(2\omega/\pi)$. At $\omega=\pi/4$ that is $4\,\mathrm{sinc}(1/2)=4\times 2/\pi=2.5465$.

**35.** A rectangular pulse train has amplitude $A=1$ and pulse width $\tau=1$ s, and repeats with period $T$:

$$
u_T(t)=\sum_{m\in\mathbb{Z}}p_1(t-mT)
$$

Four signals are built this way, differing only in the period:

- (i) $T=2.5$ s
- (ii) $T=5$ s
- (iii) $T=10$ s
- (iv) the single pulse $p_1(t)$, which is not periodic

Each plot below shows the spectrum of one of these signals against $\omega$: the lines $Tc_k$ at $\omega=k\omega_0$ for the three periodic signals, and $U(j\omega)$ for the single pulse. The grey curve on each plot is $\mathrm{sinc}(\omega/2\pi)$. Match each of the four signals to its plot.

> 图1 图片

*Answer:* (i) C, (ii) A, (iii) D, (iv) B

> [!note] Feedback
> The lines sit at multiples of $\omega_0=2\pi/T$, so a longer period brings them closer together, while the envelope depends only on the pulse width $\tau$.

- **(i)** C. The spacing is $\omega_0=2\pi/2.5=2.51$ rad/s, the widest of the three.
- **(ii)** A. The spacing is $\omega_0=2\pi/5=1.26$ rad/s.
- **(iii)** D. The spacing is $\omega_0=2\pi/10=0.628$ rad/s, the narrowest of the three.
- **(iv)** B. With no period there are no lines to space, and the spectrum is the envelope itself, $U(j\omega)=\mathrm{sinc}(\omega/2\pi)$.

**36.** $u(t)=e^{-3t}H(t)$. Evaluate $|U(j4)|$.

*Answer:* 0.2

> [!note] Feedback
> Use $e^{-at}H(t)\rightsquigarrow 1/(a+j\omega)$ with $a=3$, so $|U(j4)|=1/\sqrt{3^2+4^2}=1/5=0.2$.

**37.** $u(t)=e^{-a|t|}$ has Fourier transform $U(j\omega)=\dfrac{2a}{a^2+\omega^2}$. For $a=5000\ \mathrm{s}^{-1}$, find $|U(j\omega)|$ at $\omega=a=5000$ rad/s.

*Answer:* $2.00000\times 10^{-4}$

> [!note] Feedback
> Substituting $\omega=a$ gives $2a/(2a^2)=1/a=1/5000=2.00000\times 10^{-4}$, exactly half the peak value $2/a$ at $\omega=0$.

**38.** A system has $G(j\omega)=\dfrac{1}{3+j\omega}$. Find the phase of $G(j4)$ in degrees.

*Answer:* −53.1301

> [!note] Feedback
> The phase of $1/(3+j\omega)$ is minus the phase of the denominator, so $\arg G(j4)=-\arctan(4/3)=-53.1301$ degrees.

### Properties of the Fourier transform

**39.** $u(t)=p_2(t)$. Compare $U(j\omega)$ with the transform of the delayed pulse $u(t-5)$. Which statement is correct?

- (a) $|U(j\omega)|$ gains an extra term $-5\omega$; the phase is unchanged
- (b) Neither the magnitude nor the phase spectrum changes
- (c) $|U(j\omega)|$ is unchanged; the phase gains an extra term $-5\omega$ ✓
- (d) The whole spectrum is multiplied by $e^{-j5\omega}$, changing both magnitude and phase

> [!note] Feedback
> A delay of 5 multiplies the spectrum by $e^{-j5\omega}$, a factor of unit modulus.

- **(a)** The linear term $-5\omega$ belongs in $\arg U(j\omega)$, not in the magnitude.
- **(b)** The spectrum itself does change, because multiplying by $e^{-j5\omega}$ turns the phase.
- **(c)** Correct.
- **(d)** Since $|e^{-j5\omega}|=1$, that factor leaves the magnitude untouched.

**40.** $u(t)$ has spectrum $U(j\omega)$. The signal is compressed in time by a factor of 3, giving $u(3t)$. How do the **width** and the **peak height** of the spectrum change?

- (a) The spectrum compresses by a factor of 3 in $\omega$ and its height scales by 3
- (b) Both the width and the height scale by 3
- (c) The spectrum expands by a factor of 3 in $\omega$ and its height scales by $1/3$ ✓
- (d) The spectrum expands by a factor of 3 in $\omega$ and its height is unchanged

> [!note] Feedback
> Time scaling gives $u(3t)\rightsquigarrow \frac{1}{3}U(j\omega/3)$, so the spectrum stretches by 3 along $\omega$ and every value shrinks by 3.

- **(a)** Compressing a signal in time spreads its spectrum out, and the height falls rather than rises.
- **(b)** Multiply the height by $1/|a|=1/3$, not by 3.
- **(c)** Correct.
- **(d)** The factor $1/|a|=1/3$ multiplies every value of the spectrum, the peak included.

**41.** Let $y(t)=p_4(2t-4)$. Using the time-shift and time-scaling properties together with the pair $p_\tau(t)\rightsquigarrow \tau\,\mathrm{sinc}(\omega\tau/2\pi)$, evaluate $Y(j\omega)$ at $\omega=\pi/2$.

*Answer:* −1.2732

> [!note] Feedback
> Write $p_4(2t-4)=p_4\big(2(t-2)\big)$, so scaling gives $2\,\mathrm{sinc}(\omega/\pi)$ and the shift gives $e^{-j2\omega}$. At $\omega=\pi/2$ this is $2(2/\pi)e^{-j\pi}=-1.2732$.

**42.** The width-$\tau$ triangle $1-|t|/\tau$ ($|t|<\tau$) has transform $\tau\,\mathrm{sinc}^2(\omega\tau/2\pi)$. Applying the duality property to this pair, what kind of function of $\omega$ is the Fourier transform of a **time-domain** signal shaped like $\mathrm{sinc}^2(t/\tau)$?

- (a) A rectangular pulse in $\omega$
- (b) A triangular function of $\omega$ ✓
- (c) Another $\mathrm{sinc}^2$-shaped function of $\omega$
- (d) A train of impulses in $\omega$

> [!note] Feedback
> Duality swaps the two halves of the triangle and $\mathrm{sinc}^2$ pair, and the triangle is even, so the reversal changes nothing.

- **(a)** A rectangular pulse pairs with a single sinc, one factor short of $\mathrm{sinc}^2$.
- **(b)** Correct. The transform is $\tau(1-\tau|\omega|/2\pi)$ for $|\omega|<2\pi/\tau$.
- **(c)** Duality hands back the other member of the pair, and $\mathrm{sinc}^2$ is paired with the triangle.
- **(d)** Impulse trains in $\omega$ come from periodic signals, not from duality.

**43.** What is the Fourier transform of $u(t)=\dfrac{2a}{t^2+a^2}$, where $a>0$?

- (a) $2\pi e^{-a|\omega|}$ ✓
- (b) $e^{-a|\omega|}$
- (c) $\dfrac{2a}{a^2+\omega^2}$
- (d) $2\pi e^{-a\omega}$ (for all $\omega$)

> [!note] Feedback
> Apply duality to $e^{-a|t|}\rightsquigarrow 2a/(a^2+\omega^2)$: feeding $2a/(a^2+t^2)$ back in as a time signal returns $2\pi e^{-a|\omega|}$.

- **(a)** Correct.
- **(b)** Duality brings in a factor $2\pi$, which is missing here.
- **(c)** This runs the $e^{-a|t|}$ pair forwards, treating $2a/(t^2+a^2)$ as its own transform.
- **(d)** Without the absolute value the result grows without bound for $\omega<0$.

**44.** Given that $u(t)\rightsquigarrow U(j\omega)$, which of the following correctly states the duality property of the Fourier transform?

- (a) $U(jt)\rightsquigarrow 2\pi u(\omega)$
- (b) $U(jt)\rightsquigarrow 2\pi u(-\omega)$ ✓
- (c) $U(jt)\rightsquigarrow u(-\omega)$
- (d) $U(-jt)\rightsquigarrow 2\pi u(-\omega)$

> [!note] Feedback
> Duality reads $U(jt)\rightsquigarrow 2\pi u(-\omega)$: feed the spectrum back in as a time function and you recover $2\pi$ times the reversed signal.

- **(a)** The right-hand side is time reversed, so it is $u(-\omega)$ and not $u(\omega)$.
- **(b)** Correct.
- **(c)** The factor $2\pi$ is missing from the right-hand side.
- **(d)** Reversing the argument on the left cancels the reversal on the right, giving $2\pi u(\omega)$.

**45.** Which Fourier-transform property converts **convolution in time** into a **product in frequency**?

- (a) The differentiation property: $\dfrac{\mathrm{d}}{\mathrm{d}t}u(t)\rightsquigarrow j\omega U(j\omega)$
- (b) The convolution property: $h(t)*u(t)\rightsquigarrow G(j\omega)U(j\omega)$ ✓
- (c) The duality property: $U(jt)\rightsquigarrow 2\pi u(-\omega)$
- (d) The multiplication property: $u_1(t)u_2(t)\rightsquigarrow \frac{1}{2\pi}(U_1*U_2)(j\omega)$

> [!note] Feedback
> Every statement offered here is a true Fourier property, so the test is which one performs the named mapping.

- **(a)** This turns $\dfrac{\mathrm{d}}{\mathrm{d}t}$ into multiplication by $j\omega$ and says nothing about a convolution.
- **(b)** Correct. A convolution in time becomes the product $G(j\omega)U(j\omega)$.
- **(c)** Duality swaps the roles of the two domains for a single signal, and does not combine two signals at all.
- **(d)** This runs the other way, taking a product in time to a convolution in frequency.

**46.** Which property converts a **product of two time signals** into a (scaled) **convolution of their transforms**?

- (a) The convolution property: $h(t)*u(t)\rightsquigarrow G(j\omega)U(j\omega)$
- (b) The integration property: $\int_{-\infty}^{t}u(s)\,\mathrm{d}s\rightsquigarrow U(j\omega)/j\omega+\pi U(0)\delta(\omega)$
- (c) The multiplication property: $u_1(t)u_2(t)\rightsquigarrow \frac{1}{2\pi}(U_1*U_2)(j\omega)$ ✓
- (d) The scaling property: $u(at)\rightsquigarrow \frac{1}{|a|}U(j\omega/a)$

> [!note] Feedback
> The multiplication property is the dual of the convolution theorem, and its $1/2\pi$ comes from the $\omega$-domain inverse transform.

- **(a)** This runs the other way, taking a convolution in time to a product in frequency.
- **(b)** This transforms the running integral of one signal, not the product of two.
- **(c)** Correct, with the factor $\frac{1}{2\pi}$ that the inverse transform forces.
- **(d)** Scaling stretches the time axis of a single signal, and its $1/|a|$ is not the $1/2\pi$ wanted here.

**47.** What is the Fourier transform of $\dfrac{\mathrm{d}}{\mathrm{d}t}\cos(\omega_0t)$?

- (a) $j\omega_0\pi\left[\delta(\omega-\omega_0)+\delta(\omega+\omega_0)\right]$
- (b) $j\pi\omega_0\left[\delta(\omega-\omega_0)-\delta(\omega+\omega_0)\right]$ ✓
- (c) $-j\pi\left[\delta(\omega-\omega_0)-\delta(\omega+\omega_0)\right]$
- (d) $\pi\left[\delta(\omega-\omega_0)+\delta(\omega+\omega_0)\right]$

> [!note] Feedback
> Multiply the transform of $\cos\omega_0t$ by $j\omega$, using $\omega\,\delta(\omega\pm\omega_0)=\mp\omega_0\,\delta(\omega\pm\omega_0)$.

- **(a)** The impulse at $\omega=-\omega_0$ picks up $-\omega_0$, so the two impulses must carry opposite signs.
- **(b)** Correct, equivalently the transform of $-\omega_0\sin\omega_0t$.
- **(c)** This is the transform of $\sin\omega_0t$ alone, missing the factor $-\omega_0$ in $\dfrac{\mathrm{d}}{\mathrm{d}t}\cos\omega_0t=-\omega_0\sin\omega_0t$.
- **(d)** This is the transform of $\cos\omega_0t$ itself, with the derivative never taken.

**48.** What is the Fourier transform of $\dfrac{\mathrm{d}}{\mathrm{d}t}\left[H(t)e^{-3t}\right]$?

- (a) $\dfrac{-3}{3+j\omega}$
- (b) $1$
- (c) $\dfrac{j\omega}{(3+j\omega)^2}$
- (d) $\dfrac{j\omega}{3+j\omega}$ ✓

> [!note] Feedback
> $H(t)e^{-3t}$ transforms to $1/(3+j\omega)$, and differentiating in time multiplies the transform by $j\omega$.

- **(a)** Differentiating the step also produces $\delta(t)$, whose transform 1 is missing here.
- **(b)** This keeps only the $\delta(t)$ from the step and drops the $-3e^{-3t}H(t)$ that comes with it.
- **(c)** The squared denominator is the transform of $te^{-3t}H(t)$, not of $H(t)e^{-3t}$.
- **(d)** Correct. $j\omega$ times $1/(3+j\omega)$.

**49.** A signal $u(t)$ has Fourier transform $U(j\omega)$, and it is known that $U(j5)=2-3j$. Let $y(t)=\dfrac{\mathrm{d}u}{\mathrm{d}t}$. Evaluate $Y(j5)$.

*Answer:* $15+10j$

> [!note] Feedback
> Differentiation gives $Y(j\omega)=j\omega U(j\omega)$ at every frequency, so $Y(j5)=j5(2-3j)=15+10j$.

### The transform of a periodic signal

**50.** $u(t)$ is periodic with period $T$, fundamental frequency $\omega_0=2\pi/T$, and Fourier series coefficients $c_k$. What does $U(j\omega)$ look like?

- (a) $U(j\omega)=2\pi\displaystyle\sum_{k=-\infty}^{\infty}c_k\,\delta(\omega-k\omega_0)$ ✓
- (b) $U(j\omega)=\dfrac{1}{T}\displaystyle\sum_{k=-\infty}^{\infty}\delta(\omega-k\omega_0)$
- (c) $U(j\omega)=\displaystyle\sum_{k=-\infty}^{\infty}c_k e^{jk\omega_0t}$
- (d) $U(j\omega)=\displaystyle\sum_{k=-\infty}^{\infty}c_k\,\delta(\omega-k\omega_0)$

> [!note] Feedback
> Transform the synthesis sum term by term, using $e^{jk\omega_0t}\rightsquigarrow 2\pi\delta(\omega-k\omega_0)$.

- **(a)** Correct. An impulse of weight $2\pi c_k$ sits at each harmonic $k\omega_0$.
- **(b)** The coefficients $c_k$ of $u$ have vanished, leaving impulses of equal weight at every harmonic.
- **(c)** This is a function of $t$, whereas $U(j\omega)$ must be a function of $\omega$.
- **(d)** The locations and the weights $c_k$ are right, but each impulse still needs its factor $2\pi$.

**51.** $u(t)=5+4\cos(3t)-2\sin(3t)$ is periodic with fundamental frequency $\omega_0=3$ rad/s. Writing $U(j\omega)$ as a sum of weighted impulses, find the complex weight of the impulse located at $\omega=3$.

*Answer:* $12.566+6.283j$

> [!note] Feedback
> From $a_1=4$ and $b_1=-2$, $c_1=\frac{1}{2}(a_1-jb_1)=2+j$. The impulse in $U(j\omega)=2\pi\sum_k c_k\delta(\omega-k\omega_0)$ carries weight $2\pi c_1=12.566+6.283j$, not $c_1$ itself.

**52.** A periodic, real-valued signal $u(t)$ has Fourier transform

$$
U(j\omega)=2\pi\left[3\,\delta(\omega)+(1-2j)\,\delta(\omega-5)+(1+2j)\,\delta(\omega+5)\right]
$$

Find $u(0)$.

*Answer:* 5

> [!note] Feedback
> Read the coefficients off the impulse weights, $c_0=3$, $c_1=1-2j$ and $c_{-1}=1+2j$. The synthesis sum at $t=0$ gives $u(0)=3+(1-2j)+(1+2j)=5$.

### Parseval's theorem and signal energy

**53.** Which of the following correctly states Parseval’s theorem for the Fourier transform?

- (a) $\displaystyle\int_{-\infty}^{\infty}|u(t)|^2\,\mathrm{d}t=\frac{1}{2\pi}\int_{-\infty}^{\infty}|U(j\omega)|^2\,\mathrm{d}\omega$ ✓
- (b) $\displaystyle\int_{-\infty}^{\infty}|u(t)|^2\,\mathrm{d}t=\int_{-\infty}^{\infty}|U(j\omega)|^2\,\mathrm{d}\omega$
- (c) $\displaystyle\int_{-\infty}^{\infty}u(t)\,\mathrm{d}t=\frac{1}{2\pi}\int_{-\infty}^{\infty}U(j\omega)\,\mathrm{d}\omega$
- (d) $\displaystyle\int_{-\infty}^{\infty}|u(t)|^2\,\mathrm{d}t=\frac{1}{\pi}\int_{-\infty}^{\infty}|U(j\omega)|^2\,\mathrm{d}\omega$

> [!note] Feedback
> Energy measured in the $\omega$ domain carries the same factor $\frac{1}{2\pi}$ as the inverse transform.

- **(a)** Correct. The two integrals differ by exactly the $2\pi$ of the inverse transform.
- **(b)** This is out by a factor of $2\pi$.
- **(c)** This equates $\int u\,\mathrm{d}t=U(j0)$ with $\frac{1}{2\pi}\int U\,\mathrm{d}\omega=u(0)$, and says nothing about energy.
- **(d)** Divide by $2\pi$, not $\pi$, because the integral already runs over the negative frequencies too.

**54.** Find the energy of $u(t)=\dfrac{\sin(3t)}{\pi t}$.

*Answer:* 0.9549

> [!note] Feedback
> The pair $\sin(Wt)/(\pi t)\rightsquigarrow p_{2W}(\omega)$ with $W=3$ makes $U(j\omega)=1$ for $|\omega|<3$ and zero elsewhere, so Parseval gives $E(u)=\frac{1}{2\pi}\int_{-3}^{3}1\,\mathrm{d}\omega=3/\pi=0.9549$.


## 3. Frequency response (week 6)

### Evaluating and using $G(j\omega)$

**55.** A system has $G(j\omega)=\dfrac{j\omega+2}{(j\omega)^2+5(j\omega)+4}$. Find the steady-state response to the input $u(t)=5\cos(2t+30^\circ)$.

*Answer:* amplitude 1.41421, phase −15.0000°

> [!note] Feedback
> Evaluate the frequency response at the input frequency: $G(j2)=(2+2j)/(10j)=0.2-0.2j$. Multiply the amplitude 5 by $|G|=0.28284$ and add $\arg G=-45^\circ$ to the input phase of $+30^\circ$.

**56.** A system has $G(j\omega)=\dfrac{j\omega+0.1}{j\omega+5}$. Its steady-state response to $u(t)=\cos(10t-50^\circ)$ is $y(t)=$

- (a) $0.372\cos(10t-24.0^\circ)$
- (b) $0.894\cos(10t-24.0^\circ)$ ✓
- (c) $1.00\cos(10t-50.0^\circ)$
- (d) $0.894\cos(10t-76.0^\circ)$

> [!note] Feedback
> Evaluate $G(j10)=(0.1+10j)/(5+10j)$, then scale the input amplitude by $|G|=0.894$ and add $\arg G=+26^\circ$ to the input phase.

- **(a)** This gain is $|G(j2)|$. Evaluate $G$ at the input frequency $\omega=10$ instead.
- **(b)** Correct. $-50^\circ+26^\circ=-24^\circ$.
- **(c)** This takes the gain as 1 and the phase shift as zero, which only holds in the limit $\omega\to\infty$.
- **(d)** Add $\arg G$ to the input phase rather than subtracting it.

**57.** A vehicle’s height $h$ and road height $r$ are related by $m\ddot{h}=-k(h-r)-b(\dot{h}-\dot{r})$ with $m=1$, $k=2$, $b=3$ (SI units). For a sinusoidal road profile $r(t)=\cos(2t)$, the vehicle height reaches steady state. Find its RMS value.

*Answer:* 0.707107

> [!note] Feedback
> The frequency response is $G(j\omega)=(k+bj\omega)/(k-m\omega^2+bj\omega)=(2+3j\omega)/(2-\omega^2+3j\omega)$. At $\omega=2$ numerator and denominator both have modulus $\sqrt{40}$, so the height is a unit-amplitude sinusoid with RMS value $1/\sqrt{2}=0.707107$.

**58.** A system has $G(j\omega)=\dfrac{2(j\omega)^2+4}{(j\omega)^2+4(j\omega)+4}$. Find $|G(j2)|$ and $\arg G(j2)$.

*Answer:* $|G(j2)|=0.500000$, $\arg G(j2)=90.0000^\circ$

> [!note] Feedback
> Substitute $j\omega=j2$, where $(j\omega)^2=-4$ makes the numerator $-4$ and the denominator $8j$. Then $G(j2)=-4/(8j)=0.5j$, of modulus 0.500000 and phase 90.0000°.

**59.** A system has $G(j\omega)=\dfrac{300}{j\omega+4}$. Find the phase of $G(j4)$ in degrees.

*Answer:* −45.0000

> [!note] Feedback
> The positive real gain 300 contributes no phase, so $\arg G(j4)=-\arg(4+j4)=-\arctan(4/4)=-45.0000^\circ$.

**60.** A river’s height $y(t)$ (in feet) responds to rainfall rate $u(t)$ (in/hr) via $G(j\omega)=\dfrac{10}{(9j\omega+1)(16j\omega+1)}$, with time in hours. Find $|G(j\omega)|$ at $\omega=1/12$ rad/hr.

*Answer:* 4.8

> [!note] Feedback
> At $\omega=1/12$ rad/hr the two factors are $1+\frac{3}{4}j$ and $1+\frac{4}{3}j$, with magnitudes $\frac{5}{4}$ and $\frac{5}{3}$, so $|G|=10/\left(\frac{5}{4}\times\frac{5}{3}\right)=4.8$ feet per inch per hour.

**61.** A system obeys $\ddot{y}+3\dot{y}+2y=u$, so $G(j\omega)=\dfrac{1}{(j\omega+1)(j\omega+2)}$. Find the steady-state output for the constant input $u(t)=1$.

*Answer:* 0.500000

> [!note] Feedback
> A constant input is the $\omega=0$ case, so the steady state is the DC gain $G(0)=1/(1\times 2)$ times the input, giving 0.500000.

**62.** A full-wave rectified sine $u(t)=|\sin t|$ (period $T=\pi$, $\omega_0=2$) drives a first-order lowpass filter with $G(j\omega)=\dfrac{1}{1+3j\omega}$. Find the DC component of the output $y(t)$.

*Answer:* 0.636620

> [!note] Feedback
> The DC term of the output is $G(0)c_0$, with $c_0=\frac{1}{\pi}\int_0^{\pi}\sin t\,\mathrm{d}t=2/\pi$ and $G(0)=1$. The filter leaves it untouched, so the DC component is 0.636620.

**63.** A system has impulse response $h(t)=3e^{-6t}H(t)$, so $G(j\omega)=\dfrac{3}{j\omega+6}$. What is the steady-state output when the input is the constant signal $u(t)=4$ for all $t$?

- (a) $y=0.500$
- (b) $y=8.00$
- (c) $y=12.0$
- (d) $y=2.00$ ✓

> [!note] Feedback
> A constant input sees only the DC gain $G(0)=\int h\,\mathrm{d}t=3/6=0.5$, and the output is that gain times the input.

- **(a)** This is the DC gain on its own, not yet multiplied by the input value 4.
- **(b)** This inverts the gain, using $6/3$ in place of $3/6$.
- **(c)** This takes the numerator 3 as the gain and ignores the pole at $-6$.
- **(d)** Correct. $4\times 0.5=2.00$.

### Bode diagrams

**64.** The straight-line (asymptotic) Bode magnitude plot of a first-order system is flat at 12 dB for $\omega<200$ rad/s and falls at $-20$ dB/decade for $\omega>200$ rad/s, with its corner at $\omega=200$ rad/s. Reading off that plot, what is $20\log_{10}|G(j2000)|$?

*Answer:* −8.00000

> [!note] Feedback
> $\omega=2000$ is exactly one decade past the corner at 200 rad/s, and the asymptote falls 20 dB over that decade, so it reaches $12-20=-8.00000$ dB.

**65.** The straight-line (asymptotic) Bode phase plot of a system with a single real pole at $\omega_c=1000$ rad/s is $0^\circ$ for $\omega\le\omega_c/10$, a straight segment of slope $-45^\circ$ per decade from $\omega_c/10$ to $10\omega_c$, and $-90^\circ$ for $\omega\ge 10\omega_c$. Reading off that plot, what is the phase at $\omega=10{,}000$ rad/s?

- (a) $-90^\circ$ ✓
- (b) $-84.29^\circ$
- (c) $0^\circ$
- (d) $-45^\circ$

> [!note] Feedback
> The sloped segment leaves $0^\circ$ at $\omega_c/10=100$ rad/s and falls $45^\circ$ per decade, reaching $-90^\circ$ at $10\omega_c$.

- **(a)** Correct. At $\omega=10{,}000$ rad/s the straight-line plot has reached its $-90^\circ$ asymptote.
- **(b)** This is the exact phase $\arctan(-10)$ of the true curve, not the straight-line value the question asks you to read off.
- **(c)** The $0^\circ$ segment stops at 100 rad/s, two decades below $10{,}000$ rad/s.
- **(d)** $-45^\circ$ is the value at the corner $\omega_c=1000$ rad/s, in the middle of the sloped segment.

**66.** A system has impulse response $h(t)=e^{-at}H(t)$ with $a=3$, so $G(j\omega)=1/\ldots$

> [!warning] 原 PDF 此处问题被截断
> 题干在 “so $G(j\omega)=1/\ldots$” 处中断（分式的分母与后续设问在原文中缺失），仅保留下方 Feedback。以下照录原文的 Feedback。

> [!note] Feedback
> Here $|G(j\omega)|=1/\sqrt{a^2+\omega^2}$ and $|G(j0)|=1/a$, so $a/\sqrt{a^2+\omega^2}=1/\sqrt{2}$ forces $\omega=a=3.00000$ rad/s. The half-power point of a first-order pole always sits at the pole frequency.

**67.** Four systems:

$$
\begin{aligned}
\text{(i)}\quad & G(j\omega)=\frac{1}{1+j\omega/10}\\[4pt]
\text{(ii)}\quad & G(j\omega)=\frac{10^4}{(j\omega)^2+10(j\omega)+10^4}\\[4pt]
\text{(iii)}\quad & G(j\omega)=\frac{100}{(j\omega)^2+20(j\omega)+100}\\[4pt]
\text{(iv)}\quad & G(j\omega)=\frac{1}{1+j\omega/10}\cdot\frac{10^4}{(j\omega)^2+10(j\omega)+10^4}
\end{aligned}
$$

Their Bode magnitude diagrams, in some order, are below. Match each system to its diagram.

> 图2 图片

*Answer:* (i) B, (ii) D, (iii) A, (iv) C

> [!note] Feedback
> Sort the panels by high-frequency slope, $-20$ dB/decade for each pole, then split the two $-40$ dB/decade panels by whether a peak appears.

- **(i)** B. One pole, so the break is at 10 rad/s and the slope past it is $-20$ dB/decade.
- **(ii)** D. Here $\omega_n=100$ rad/s and $\zeta=0.05$, which puts a 20 dB peak at 100 rad/s and $-40$ dB/decade beyond it.
- **(iii)** A. Here $\omega_n=10$ rad/s and $\zeta=1$, so the magnitude is $-6$ dB at the break, falls at $-40$ dB/decade, and has no peak.
- **(iv)** C. The decibel curves of (i) and (ii) add, giving $-20$ dB/decade from 10 rad/s, a peak pulled back to about 0 dB at 100 rad/s, and $-60$ dB/decade after it.

### Moving between the impulse response and $G(j\omega)$

**68.** A system has $G(j\omega)=\dfrac{4}{j\omega+2}$. Find its impulse response $h(t)$.

*Answer:* $h(t)=4e^{-2t}H(t)$

> [!note] Feedback
> Match $1/(a+j\omega)$ to $e^{-at}H(t)$ with $a=2$, and carry the gain 4 through by linearity. The pair is one-sided, so the step $H(t)$ belongs in the answer.

**69.** A first-order system with impulse response $h_1(t)=2e^{-5t}H(t)$ is connected in cascade with an ideal delay of 3 seconds (impulse response $\delta(t-3)$). Find the impulse response $h(t)$ of the overall cascade system.

*Answer:* $h(t)=2e^{-5(t-3)}H(t-3)$

> [!note] Feedback
> A cascade convolves the two impulse responses, and convolving with $\delta(t-3)$ delays by 3 s, so $h(t)=h_1(t-3)$. Shift the exponent and the step together, since $2e^{-5t}H(t-3)$ is wrong by a factor $e^{-15}$.

**70.** A system has $G(j\omega)=\dfrac{3}{j\omega+1}+\dfrac{2}{j\omega+4}$. What is its impulse response $h(t)$?

- (a) $h(t)=5e^{-5t}H(t)$
- (b) $h(t)=3e^{-4t}H(t)+2e^{-t}H(t)$
- (c) $h(t)=3e^{-t}H(t)-2e^{-4t}H(t)$
- (d) $h(t)=3e^{-t}H(t)+2e^{-4t}H(t)$ ✓

> [!note] Feedback
> Invert term by term with $1/(a+j\omega)\to e^{-at}H(t)$, where the numerator sets the amplitude and the pole sets the decay rate.

- **(a)** A sum of two poles keeps both decay rates $e^{-t}$ and $e^{-4t}$ instead of merging into a single rate $e^{-5t}$.
- **(b)** The amplitudes sit on the wrong exponentials. Put 3 with the pole at $-1$ and 2 with the pole at $-4$.
- **(c)** The two terms of $G(j\omega)$ are added, so the second one keeps its plus sign.
- **(d)** Correct. $3/(j\omega+1)$ gives $3e^{-t}H(t)$ and $2/(j\omega+4)$ gives $2e^{-4t}H(t)$.

**71.** A system has impulse response

$$
h(t)=4e^{-3t}\sin(5t)\,H(t)
$$

Its transfer function $G(j\omega)$ is:

- (a) $\dfrac{4}{(3+j\omega)^2+25}$
- (b) $\dfrac{20}{(5+j\omega)^2+9}$
- (c) $\dfrac{4(3+j\omega)}{(3+j\omega)^2+25}$
- (d) $\dfrac{20}{(3+j\omega)^2+25}$ ✓

> [!note] Feedback
> The damped-sine pair is $e^{-at}\sin(\omega_0t)H(t)\to \omega_0/((a+j\omega)^2+\omega_0^2)$, so the numerator carries the factor $\omega_0$.

- **(a)** The numerator needs the factor $\omega_0=5$ as well as the amplitude, giving 20 rather than 4.
- **(b)** Read $a=3$ as the decay rate and $\omega_0=5$ as the oscillation frequency, which puts $(3+j\omega)^2+25$ in the denominator.
- **(c)** The numerator $(a+j\omega)$ comes from the damped-cosine pair, and $h(t)$ contains a sine.
- **(d)** Correct. $4\times 5=20$ over $(3+j\omega)^2+25$.


## 4. Second order systems and stability (weeks 6–7)

### Damping and resonance in second order systems

**72.** Which damping ratio makes a second-order system $G(j\omega)=\dfrac{K\omega_n^2}{(j\omega)^2+2\zeta\omega_n(j\omega)+\omega_n^2}$ critically damped?

- (a) $\zeta=1.5$
- (b) $\zeta=0$
- (c) $\zeta=1.0$ ✓
- (d) $\zeta=0.4$

> [!note] Feedback
> Critical damping is $\zeta=1$, where the discriminant vanishes and the two poles coincide at $-\omega_n$.

- **(a)** $\zeta=1.5$ gives two distinct real poles, which is overdamped.
- **(b)** $\zeta=0$ puts both poles on the imaginary axis and the response oscillates forever.
- **(c)** Correct. The repeated real pole at $-\omega_n$ is the boundary between overdamped and underdamped.
- **(d)** $\zeta=0.4$ gives complex poles and a decaying oscillation, which is underdamped.

**73.** A second-order system in the standard form $(j\omega)^2+2\zeta\omega_n(j\omega)+\omega_n^2$ has its two poles at $-10^4\pm j10^4$ rad/s. What is $\zeta$?

- (a) 0.5
- (b) 1
- (c) 0.707 ✓
- (d) 1.414

> [!note] Feedback
> Take $\omega_n$ as the distance of the pole from the origin and $\zeta=|\operatorname{Re}p|/\omega_n$, so equal real and imaginary parts give $\zeta=\cos 45^\circ$.

- **(a)** Use the pole magnitude $\sqrt{2}\times 10^4$ rad/s for $\omega_n$, not twice the real part.
- **(b)** Critical damping needs a zero imaginary part, and these poles have $\operatorname{Im}p=\pm 10^4$ rad/s.
- **(c)** Correct. $\omega_n=1.4142\times 10^4$ rad/s and $\zeta=10^4/(1.4142\times 10^4)=1/\sqrt{2}$.
- **(d)** Divide $|\operatorname{Re}p|$ by $\omega_n$ rather than the other way round, since $\zeta>1$ would mean real poles.

**74.** A second-order system has $\zeta=0.8$. Does $|G(j\omega)|$ have a resonant peak at a nonzero frequency?

- (a) No, because $\zeta=0.8>1/\sqrt{2}\approx 0.7071$ ✓
- (b) It cannot be determined without knowing $K$
- (c) Yes, at $\omega_r=\omega_n\sqrt{1-2(0.8)^2}$
- (d) Yes, because any $\zeta<1$ (underdamped) gives a resonant peak

> [!note] Feedback
> A second-order magnitude peaks at a non-zero frequency only when $\zeta<1/\sqrt{2}\approx 0.7071$.

- **(a)** Correct. With $\zeta=0.8$ the magnitude falls monotonically from $|G(j0)|=|K|$.
- **(b)** $K$ scales $|G(j\omega)|$ by the same factor at every frequency, so it can neither create nor remove a peak.
- **(c)** The radicand $1-2(0.8)^2=-0.28$ is negative, so this $\omega_r$ is not a real frequency.
- **(d)** Underdamped only means $\zeta<1$, and the band $0.7071\le\zeta<1$ has complex poles but no peak.

**75.** A series RLC circuit is driven by $u(t)$, with the output $y(t)$ taken across the capacitor, so $LC\ddot{y}+RC\dot{y}+y=u$. Here $R=200\ \Omega$, $L=0.5$ H and $C=2\ \mu$F. Does $|G(j\omega)|$ have a resonant peak? If so, find $\omega_r$ and the peak value $|G(j\omega_r)|$ in dB.

*Answer:* Yes, a peak exists, at $\omega_r=959.166$ rad/s with $|G(j\omega_r)|=2.55155$, that is 8.13609 dB

> [!note] Feedback
> In standard form $\omega_n=1/\sqrt{LC}=1000$ rad/s and $\zeta=\frac{R}{2}\sqrt{C/L}=0.2$, which is below $1/\sqrt{2}$, so a peak exists. Then $\omega_r=\omega_n\sqrt{1-2\zeta^2}=959.166$ rad/s and $|G(j\omega_r)|=1/(2\zeta\sqrt{1-\zeta^2})=2.55155$, or 8.13609 dB.

**76.** A designer wants a sharp resonant peak near $\omega_0=5$ rad/s, using a pair of complex conjugate poles at $-\alpha\pm j5$. Which choice of $\alpha$ gives the sharpest, highest resonant peak?

- (a) $\alpha=2$
- (b) $\alpha=0.5$
- (c) $\alpha=0.05$ ✓
- (d) $\alpha=5$

> [!note] Feedback
> Poles at $-\alpha\pm j5$ give $\omega_n=\sqrt{\alpha^2+25}$ and $\zeta=\alpha/\omega_n$, and the peak $1/(2\zeta\sqrt{1-\zeta^2})$ grows as $\alpha$ shrinks.

- **(a)** $\alpha=2$ gives $\zeta=0.371$ and a peak only 1.45 times the DC gain.
- **(b)** $\alpha=0.5$ gives $\zeta=0.0995$ and a peak 5.05 times the DC gain, ten times below what $\alpha=0.05$ delivers.
- **(c)** Correct. $\zeta=0.0100$ gives a peak 50.0 times the DC gain, at $\omega_r=4.99975$ rad/s.
- **(d)** Moving the pole away from the imaginary axis damps it, and $\alpha=5$ gives $\zeta=1/\sqrt{2}$ exactly, so there is no peak at all.

### Stability from the poles

**77.** An LTI system has $G(j\omega)=\dfrac{(j\omega)^2+j\omega+1}{(j\omega+2)\left((j\omega)^2+4\right)}$. Classify the system.

- (a) Marginally stable: no pole in the right half plane, and the poles on the imaginary axis are distinct ✓
- (b) Unstable: no pole in the right half plane, but a repeated pole on the imaginary axis
- (c) Unstable: at least one pole satisfies $\operatorname{Re}p>0$
- (d) Stable: every pole satisfies $\operatorname{Re}p<0$

> [!note] Feedback
> The denominator factors to poles at $-2$, $+j2$ and $-j2$, all simple, and the numerator cancels none of them.

- **(a)** Correct. The mode from $\pm j2$ oscillates at constant amplitude, so $h$ stays bounded without decaying.
- **(b)** $(j\omega)^2+4$ supplies two distinct poles $+j2$ and $-j2$, not one double pole.
- **(c)** Both $\pm j2$ have zero real part and the remaining pole is at $-2$, so nothing sits in the right half plane.
- **(d)** The poles at $\pm j2$ do not satisfy $\operatorname{Re}p<0$, so $h$ never decays to zero.

**78.** An LTI system has $G(j\omega)=\dfrac{(j\omega)^2+2(j\omega)+8}{(j\omega+1)\left((j\omega)^2+4\right)^2}$. Classify the system.

- (a) Unstable: at least one pole satisfies $\operatorname{Re}p>0$
- (b) Unstable: no pole in the right half plane, but a repeated pole on the imaginary axis ✓
- (c) Marginally stable: no pole in the right half plane, and the poles on the imaginary axis are distinct
- (d) Stable: every pole satisfies $\operatorname{Re}p<0$

> [!note] Feedback
> Squaring $\left((j\omega)^2+4\right)$ makes $\pm j2$ a double pole, and a repeated imaginary-axis pole produces modes that grow like $t\cos 2t$.

- **(a)** The poles are $-1$ and the double pair at $\pm j2$, all with $\operatorname{Re}p\le 0$.
- **(b)** Correct. The growing $t\cos 2t$ mode makes the system unstable without any right-half-plane pole.
- **(c)** The squared factor repeats $\pm j2$, so the poles on the imaginary axis are not distinct here.
- **(d)** The poles at $\pm j2$ lie on the imaginary axis, not in the left half plane.

**79.** Four LTI systems are given by their transfer functions. Which one is BIBO stable?

- (a) $G(j\omega)=\dfrac{j\omega+7}{(j\omega+1)\left((j\omega)^2-4(j\omega)+9\right)}$
- (b) $G(j\omega)=\dfrac{1}{j\omega-3}$
- (c) $G(j\omega)=\dfrac{2(j\omega)+3}{(j\omega+1)(j\omega+2)}$ ✓
- (d) $G(j\omega)=\dfrac{3}{j\omega(j\omega+2)}$

> [!note] Feedback
> A proper rational $G$ is BIBO stable exactly when every pole satisfies $\operatorname{Re}p<0$, so factor each denominator and check.

- **(a)** The factor $(j\omega)^2-4(j\omega)+9$ has roots $2\pm j2.236$, a pair in the right half plane.
- **(b)** The pole of $1/(j\omega-3)$ is at $+3$, not at $-3$.
- **(c)** Correct. The poles are $-1$ and $-2$, both strictly in the left half plane.
- **(d)** A pole at the origin is not harmless, and the bounded input $H(t)$ here drives an output that grows without bound.

**80.** A first-order system obeys $\tau\dot{y}=-y+\beta u$ with $\tau=-4$ s. Classify its stability.

- (a) Marginally stable
- (b) Stable and BIBO stable
- (c) Cannot be determined without knowing $\beta$
- (d) Unstable ✓

> [!note] Feedback
> For $\tau\dot{y}=-y+\beta u$ the pole sits at $-1/\tau$, so $\tau=-4$ s puts it at $+0.25$.

- **(a)** Marginal stability needs the pole on the imaginary axis, which a finite negative $\tau$ never gives.
- **(b)** Keep the sign of $\tau$ when inverting it. $-1/(-4)=+0.25$, not $-0.25$.
- **(c)** $\beta$ scales the forced response only, and the natural mode $e^{t/4}$ grows for every $\beta$.
- **(d)** Correct. The natural mode $e^{t/4}$ grows without bound.

**81.** For the second-order system $G(j\omega)=\dfrac{K\omega_n^2}{(j\omega)^2+2\zeta\omega_n(j\omega)+\omega_n^2}$ with $\omega_n=5$ rad/s fixed, for which value of $\zeta$ is the unforced response *not* bounded as $t\to\infty$?

- (a) $\zeta=1$
- (b) $\zeta=-0.1$ ✓
- (c) $\zeta=0.3$
- (d) $\zeta=2$

> [!note] Feedback
> The poles have real part $-\zeta\omega_n$, so the unforced response grows without bound exactly when $\zeta<0$.

- **(a)** $\zeta=1$ repeats the pole at $-5$, and the $te^{-5t}$ mode still decays.
- **(b)** Correct. The poles are $0.5\pm j4.975$, giving an oscillation of growing amplitude.
- **(c)** $\zeta=0.3$ puts the poles at $-1.5\pm j4.770$, so the oscillation decays.
- **(d)** $\zeta=2$ gives real poles at $-18.66$ and $-1.34$, and both modes decay.

**82.** For $a\ddot{y}+b\dot{y}+cy=0$ with $a,b,c>0$, which is always true of the solution $y(t)$ as $t\to\infty$?

- (a) $y(t)$ can grow without bound for some positive choices of $a,b,c$
- (b) $y(t)$ stays bounded but does not necessarily decay to zero
- (c) $y(t)\to 0$, regardless of the relative sizes of $a,b,c$ ✓
- (d) $y(t)\to 0$ only if $b^2\ge 4ac$ (overdamped or critically damped)

> [!note] Feedback
> For a second-order equation, all three coefficients strictly positive is enough to put both characteristic roots in the left half plane.

- **(a)** Growth would need a root with positive real part, which positive $b/a$ and $c/a$ rule out.
- **(b)** A bounded response that never decays needs $b=0$, and $b>0$ here.
- **(c)** Correct. Real roots satisfy $\sqrt{b^2-4ac}<b$, and complex roots have real part $-b/2a<0$.
- **(d)** Complex roots decay as well, since their real part is $-b/2a$ whatever the sign of $b^2-4ac$.

### BIBO stability from the impulse response

**83.** A system has impulse response $h(t)=3e^{-2t}H(t)$. Compute $\int_{-\infty}^{\infty}|h(t)|\,\mathrm{d}t$ and state whether the system is BIBO stable.

*Answer:* 1.50000, and the system is BIBO stable

> [!note] Feedback
> Since $h$ is one-sided and non-negative, $\int_{-\infty}^{\infty}|h|\,\mathrm{d}t=\int_0^{\infty}3e^{-2t}\,\mathrm{d}t=3/2=1.50000$. A finite $\int|h|$ is the BIBO condition, so this system is BIBO stable.

**84.** A system has impulse response $h(t)=H(t)$ (an ideal integrator). Classify its pole, its stability, and its BIBO stability.

- (a) Pole at $j\omega=0$; marginally stable; BIBO stable
- (b) Pole at $j\omega=-1$; stable; BIBO stable
- (c) Pole at $j\omega=0$; marginally stable; BIBO unstable ✓
- (d) No finite poles; the output depends only on the present value of the input

> [!note] Feedback
> The step transforms to $\pi\delta(\omega)+1/(j\omega)$, a single pole at the origin, and $\int_0^\infty 1\,\mathrm{d}t$ diverges.

- **(a)** The pole and the classification are right, but a divergent $\int|h|$ means the system is not BIBO stable.
- **(b)** A pole at $-1$ belongs to $e^{-t}H(t)$, and $h(t)=H(t)$ never decays.
- **(c)** Correct. $|h|=1$ is bounded but does not decay, and the bounded input $H(t)$ gives the unbounded ramp $y(t)=tH(t)$.
- **(d)** An integrator depends on the whole past of the input and has a pole at the origin.

**85.** Two systems have impulse responses $h_A(t)=300\,e^{-4t}H(t)$ and $h_B(t)=300\,e^{4t}H(t)$. Which system is BIBO stable and has a frequency response $G(j\omega)$ that exists (that is, its Fourier transform converges)?

- (a) neither
- (b) $A$ only ✓
- (c) both $A$ and $B$
- (d) $B$ only

> [!note] Feedback
> Test absolute integrability: $\int|h_A|\,\mathrm{d}t=300/4=75$ is finite, while $\int|h_B|\,\mathrm{d}t$ diverges because $e^{4t}$ grows without bound.

- **(a)** A decaying one-sided exponential is absolutely integrable, and $h_A$ is one.
- **(b)** Correct. $G_A(j\omega)=300/(4+j\omega)$ exists and $A$ is BIBO stable.
- **(c)** System $B$ gives a finite integral only over a finite window, and it diverges as the upper limit goes to infinity.
- **(d)** $e^{4t}$ grows and $e^{-4t}$ decays, so $A$ is the stable one.

[^1]: Some questions are adapted from B. P. Lathi and R. A. Green, *Linear Systems and Signals*, 3rd ed. (chapters 2, 4, 6 and 7), from ELEC3004 *Signals, Systems and Control* at the University of Queensland (2013 and 2017), and from S. Boyd, EE102 *Introduction to Signals and Systems*, Stanford University.
