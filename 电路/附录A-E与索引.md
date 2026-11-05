# 附录A 电路基本概念的引入

本附录从电磁场基本理论出发，建立电压、电流和功率等电路基本概念，介绍电压、电流的唯一性理论，引入KCL和KVL等电路基本定律，给出集总参数元件（$R$、$L$、$C$、$M$）的定义。期望读者能够理解电磁场理论与电路理论的内在联系，认识"场"与"路"二者的统一性。

## A1 电流

由于电路分析中研究的电流基本上都是在金属导体中流动，可以假设载流子的方向始终沿着导体，即如图A1.1所示。图中 $\mathrm{d}\boldsymbol{S}$ 表示导体中与电流方向垂直的一小块面积，$\boldsymbol{v}$ 为载流子速度，$e$ 为单位载流子电量，$n$ 为单位体积内载流子的数量。根据电流的定义（式（1.2.1））可知，在 $\mathrm{d}t$ 时间内通过 $\mathrm{d}\boldsymbol{S}$ 的电流 $\mathrm{d}i$ 为

$$\mathrm{d}i=\frac{\mathrm{d}q}{\mathrm{d}t}=\frac{en\,\mathrm{d}t(\boldsymbol{v}\cdot\mathrm{d}\boldsymbol{S})}{\mathrm{d}t}=en\boldsymbol{v}\cdot\mathrm{d}\boldsymbol{S}$$

此时定义电流密度为 $\boldsymbol{J}=en\boldsymbol{v}$，则有

$$\mathrm{d}i=\boldsymbol{J}\cdot\mathrm{d}\boldsymbol{S}$$

然后对上式进行积分，可知

$$i=\iint_{S}\boldsymbol{J}\cdot\mathrm{d}\boldsymbol{S} \tag{A1.1}$$

除了大小以外，电流的一个非常重要的性质就是方向。电流的方向定义为正载流子定向移动的方向，即与负载流子（如电子）移动相反的方向。

在电磁学中如果需要具体计算流过某个面 $S$ 的电流 $i$ 的数值，首先需要明确 $S$ 的法线方向。如果认为导体是笔直的，同时电荷在导体中的流动是均匀的，就可以用导体的横截面来计算电流 $i$。假设图A1.1中是正载流子。如果希望计算从左向右流动的电流，则 $\mathrm{d}\boldsymbol{S}$ 法线方向向右，考虑到 $\boldsymbol{J}$ 的方向即 $\boldsymbol{v}$ 的方向也向右，因此式（A1.1）可写为 $i=JS>0$，即实际上在导体中从左向右流动正的电流。

如果希望计算从右向左流动的电流，则 $\mathrm{d}\boldsymbol{S}$ 法线方向向左，而 $\boldsymbol{J}$ 的方向向右，因此式（A1.1）可写为 $i=-JS<0$，即实际上在导体中从右向左流动负的电流，等同于从左向右流动正的电流。

可见 $\mathrm{d}\boldsymbol{S}$ 法线方向的选取并不会影响最终电流 $i$ 计算的结果。因此要想计算 $i$ 必须先假设 $\mathrm{d}\boldsymbol{S}$ 法线方向（即希望计算的电流的方向）。这等同于电路分析中先假设电流 $i$ 的参考方向。

>图A1.1 电流

## A2 电压

静电场具有保守性，即静电场中电场强度的线积分仅取决于起点（$A$）和终点（$B$）的位置而与联接起点和终点的路径无关。

为了表征静电场中 $A$ 和 $B$ 两点之间的关系，引入了电位差的概念，用以表示电场力将正电荷（$\mathrm{d}q$）从 $A$ 移动到 $B$ 所做的功，即 $A$ 点与 $B$ 点间的电位差 $\varphi_A-\varphi_B$ 定义为

$$\varphi_A-\varphi_B=\frac{\mathrm{d}w_{AB}}{\mathrm{d}q}=\frac{\int_{A}^{B}\boldsymbol{F}\cdot\mathrm{d}\boldsymbol{l}}{\mathrm{d}q}=\frac{\int_{A}^{B}\mathrm{d}q\,\boldsymbol{E}\cdot\mathrm{d}\boldsymbol{l}}{\mathrm{d}q}=\int_{A}^{B}\boldsymbol{E}\cdot\mathrm{d}\boldsymbol{l} \tag{A2.1}$$

其中 $\mathrm{d}q$ 称为检验电荷。如果选择 $P$ 点为参考点，则可以定义 $A$ 点的电位为 $\varphi_A=\int_{A}^{P}\boldsymbol{E}\cdot\mathrm{d}\boldsymbol{l}$。在电磁学中，参考点的选择视方便而定，理论分析中一般将无穷远处选作参考点，实际分析中一般将大地选作参考点。

直流电源激励的电路是恒定电流场，场中 $A$、$B$ 两点的电压 $u_{AB}$ 表示为两点之间的电位差，即

$$u_{AB}=\varphi_A-\varphi_B=\int_{A}^{B}\boldsymbol{E}\cdot\mathrm{d}\boldsymbol{l} \tag{A2.2}$$

从式（A2.2）可以看出，$A$ 点和 $B$ 点之间的电压即从 $A$ 点到 $B$ 点电位降低的值（这个值可能为正，也可能为负），因此经常把电压也称作电位降，有时甚至用电压降来强调降落的含义。在电路中，参考点（也称为零电位点）的选取一般来说是任意的，不过特定的电路分析方法可能对参考点的选择有一定的要求[^1]。

类似于电流中的讨论，可知要想计算 $u$ 必须先假设 $\mathrm{d}\boldsymbol{l}$ 的方向（即希望计算的电压的方向）。这等同于电路分析中先假设电压 $u$ 的参考方向。

## A3 电功率

假设有正载流子在图A3.1所示的某电路元件中定向流动，电场强度 $\boldsymbol{E}$ 在电路元件中均匀分布，考察 $\mathrm{d}t$ 时间段中电场力对正电荷 $\mathrm{d}q$ 所做的功。设电场强度 $\boldsymbol{E}$ 的方向向右，则电量为 $\mathrm{d}q$ 的正电荷受到大小为 $\boldsymbol{F}$，方向向右的电场力。这个电场力使得正电荷向右流动，速度为 $\boldsymbol{v}$。

>图A3.1 电功率的推导

根据电场强度的定义可知 $\boldsymbol{F}=\mathrm{d}q\boldsymbol{E}$，在 $\mathrm{d}t$ 时间内电场力对正电荷做功为

$$\mathrm{d}w=Fv\,\mathrm{d}t=\mathrm{d}qEv\,\mathrm{d}t$$

根据功率的定义 $p=\mathrm{d}w/\mathrm{d}t$，可知

$$p=\mathrm{d}qEv=\frac{\mathrm{d}q}{\mathrm{d}t}Ev\,\mathrm{d}t$$

假设计算电流 $i$ 的 $\mathrm{d}\boldsymbol{S}$ 法线方向为从左向右，计算电压 $u$ 的 $\mathrm{d}\boldsymbol{l}$ 方向也为从左向右。根据电流的定义式（1.2.1）可知，上式中的 $\mathrm{d}q/\mathrm{d}t$ 即为流经电路元件的电流 $i(t)$。根据式（A2.2）可知，上式中 $Ev\,\mathrm{d}t$ 即为电路元件两端的电压 $u(t)$。因此有

$$p(t)=i(t)u(t) \tag{A3.1}$$

从图A3.1和式（A3.1）的推导过程可以看出，式（A3.1）表示了电压电流为关联参考方向时电场力对正电荷做功的功率，即电路元件吸收的电功率。

反之可得，如果电流和电压采用非关联的参考方向，则电路元件吸收的电功率为

$$p(t)=-i(t)u(t) \tag{A3.2}$$

由式（A3.1）和式（A3.2）可知，电功率和电流以及电压一样，也是随时间变化的量，称之为瞬时功率。

因为电路中存在电源，因此可能有元件发出电功率的情况。求元件发出的电功率可以有两种方法。第一种方法是利用式（A3.1）或式（A3.2）求元件吸收的功率，其相反数即为该元件发出电功率。第二种方法是采用与图A3.1类似的方法进行推导其他力使得单位正电荷克服电场力做的功，此时 $F$ 的正方向与 $E$ 的正方向相反。可以得出电流与电压采用关联参考方向时元件发出的电功率可用式（A3.2）计算，采用非关联参考方向时发出的电功率用式（A3.1）计算。两种方法均可采用。

## A4 电压和电流的唯一性

本节要讨论一个比较深入的问题，即在什么条件下电路元件能够用集总参数电路模型来表示。

仅讨论两接线端元件。对于如图A4.1所示的两接线端元件，用电路模型来表示其外特性意味着用式（1.2.1）和式（1.2.2）分别定义的流经元件的电流和接线端之间的电压必须满足两个条件：任意时刻流入接线端 $A$ 的电流等于流出接线端 $B$ 的电流（即接线端电流的唯一性），接线端之间的电压 $u_{AB}$ 唯一确定（即接线端电压的唯一性）。只有满足这两个条件之后，才能讨论接线端电流和电压的关系，从而得到其集总参数电路模型。

>图A4.1 能够用电路模型建模的电路元件

为了便于讨论，将电磁场中电流和电压的定义重写如下：

$$i=\iint_{S}\boldsymbol{J}\cdot\mathrm{d}\boldsymbol{S} \tag{A4.1}$$

$$u_{AB}=\int_{A}^{B}\boldsymbol{E}\cdot\mathrm{d}\boldsymbol{l} \tag{A4.2}$$

在恒定电流场中有环路定理

$$\oint_{L}\boldsymbol{E}\cdot\mathrm{d}\boldsymbol{l}=0 \tag{A4.3}$$

此外，根据恒定电流场的定义可知

$$\oiint_{S}\boldsymbol{J}\cdot\mathrm{d}\boldsymbol{S}=0 \tag{A4.4}$$

如果电路元件满足式（A4.3），则根据静电场的保守性可知 $u_{AB}$ 唯一确定。此外，如果电路元件满足式（A4.4），即在包围该电路元件的闭合曲面上对电流密度进行积分结果为零，可知从 $A$ 接线端流入的电流等于从 $B$ 接线端流出的电流。

如果电路元件满足式（A4.3）和式（A4.4），则其具有接线端电流和电压的唯一性。可是式（A4.3）和式（A4.4）是基于静电场和恒定电流场的公式，实际情况往往存在着电场和磁场相互耦合的现象。根据法拉第电磁感应定律和电流连续性方程有

$$\oint_{L}\boldsymbol{E}\cdot\mathrm{d}\boldsymbol{l}=-\frac{\mathrm{d}\varPhi}{\mathrm{d}t} \tag{A4.5}$$

$$\oiint_{S}\boldsymbol{J}\cdot\mathrm{d}\boldsymbol{S}=-\frac{\mathrm{d}q_{\mathrm{int}}}{\mathrm{d}t} \tag{A4.6}$$

其中 $\varPhi$ 表示磁通，$q_{\mathrm{int}}$ 表示闭合曲面内包含的电荷。因此实际情况中元件一般不再满足式（A4.3）和式（A4.4），从而很难实现电路模型要求的接线端电流和电压的唯一性。

虽然精确考察每个电路元件时式（A4.3）和式（A4.4）不再成立，但基于以下两个原因，可以建立具有唯一的接线端电流和电压的电路模型。首先，虽然变化的磁场将产生感应电动势，但如果磁场的变化率比起感兴趣的信号的电压幅值来说相差很远，则可以在精度许可的条件下将其忽略。同样，变化的电荷将产生电流，但如果电荷的变化率比起感兴趣的信号的电流幅值来说相差很远，则可以在精度许可的条件下将其忽略。这就是正文中提到过的抽象观点和工程观点的应用。

其次，可以通过改变积分路径、积分曲面（即改变电路元件的空间范围）来使电路元件满足式（A4.3）和式（A4.4）。比如，如果存在两个接近的线圈 $A$ 和 $B$，则对于线圈 $A$ 来说，存在线圈 $B$ 产生并与线圈 $A$ 交链的磁通（或磁链），因此式（A4.3）可能不成立。但如果将两个线圈之间相互交链的磁通（或磁链）进行合理的建模，还是可以将这两个线圈一起建模成互感的电路模型。

通过上述讨论得到的结论是：电路元件可建模为集总参数电路模型的两个条件是，选择元件的边界使得在包围元件的任意闭合路径上有

$$\frac{\mathrm{d}\varPhi}{\mathrm{d}t}=0 \tag{A4.7}$$

同时选择元件的边界，使得元件内部有

$$\frac{\mathrm{d}q_{\mathrm{int}}}{\mathrm{d}t}=0 \tag{A4.8}$$

结合1.6节的讨论可知，如果一个电路元件满足

1. 包围元件的任意闭合路径上有 $\dfrac{\mathrm{d}\varPhi}{\mathrm{d}t}=0$；
2. 包含元件的任意曲面内部有 $\dfrac{\mathrm{d}q_{\mathrm{int}}}{\mathrm{d}t}=0$；
3. 该元件的尺寸与电路中信号的波长相差很远。

则该元件可以建模成电路的集总参数模型。

将实际电路元件建模成集总参数模型后，再用理想导线[^2]将其相互联接起来，就构成了待分析的电路模型。类似于前面元件接线端电压和电流的唯一性，要使得电路中任意两点之间的电压唯一，任意支路上的电流唯一，通过类似的推导过程，可以得到集总参数电路的条件为

1. 电路中任意闭合路径上有 $\dfrac{\mathrm{d}\varPhi}{\mathrm{d}t}=0$；
2. 电路中任意闭合曲面内部有 $\dfrac{\mathrm{d}q_{\mathrm{int}}}{\mathrm{d}t}=0$；
3. 电路尺寸与电路中信号的波长相差很远。

值得指出的是，上面的条件（1）和条件（2）分别是分析动态电路时磁链守恒和电荷守恒的依据。

## A5 KCL

设电路满足A4节的集总参数条件，在某节点上有3条支路，实际电流密度方向 $\boldsymbol{J}_1$、$\boldsymbol{J}_2$ 和 $\boldsymbol{J}_3$ 分别如图A5.1所示。在该节点上画一个闭合曲面，曲面的正方向指向外部。

>图A5.1 KCL的推导

图A5.1所示的闭合曲面包围了一个节点，根据集总参数电路的条件，在该闭合曲面内部满足 $\dfrac{\mathrm{d}q_{\mathrm{int}}}{\mathrm{d}t}=0$，于是在该闭合曲面上对电流密度进行积分，有

$$\oiint_{S}\boldsymbol{J}\cdot\mathrm{d}\boldsymbol{S}=0 \tag{A5.1}$$

由于电流仅在支路中流动，因此式（A5.1）所示的面积分仅在3条支路的横截面上有非零值，再利用

$$i=\iint_{S}\boldsymbol{J}\cdot\mathrm{d}\boldsymbol{S}$$

根据A1节中对于电流方向的讨论可知 $i_1=J_1S_1$，$i_2=J_2S_2$，$i_3=-J_3S_3$，代入式（A5.1），就可以得到

$$i_1+i_2-i_3=0 \tag{A5.2}$$

注意，这里讨论的是实际电流满足式（A5.2）。

由于该节点是任意选取的，因此对集总参数电路中的任意节点，在任意时刻得到基尔霍夫电流定律（Kirchhoff current law，KCL）

$$\sum i=0 \tag{A5.3}$$

即流出任意节点的实际电流的代数和为零。

如果将式（A5.2）等号左边符号为负的电流移动到等号右边，则KCL可以写为

$$\sum_{\mathrm{out}} i=\sum_{\mathrm{in}} i \tag{A5.4}$$

即流出某节点的实际电流之和等于流入该节点的实际电流之和。式（A5.3）和式（A5.4）是等价的。

由于电流的参考方向是任意假设的，因此有必要讨论一下参考电流是否也满足式（A5.3）和式（A5.4）。设一个节点有 $k$ 条支路，在这些支路上的实际电流分别为 $i_1$、$i_2$、$\cdots$、$i_k$，对应的参考电流分别为 $i_1'$、$i_2'$、$\cdots$、$i_k'$。对于联接到该节点的第 $j$ 条支路电流来说，或者满足 $i_j=i_j'$，或者满足 $i_j=-i_j'$。在 $i_1$、$i_2$、$\cdots$、$i_k$ 中，不失一般性，设 $i_1$、$\cdots$、$i_l$ 为实际流出节点的电流，$i_{l+1}$、$\cdots$、$i_k$ 为实际流入该节点的电流。根据式（A5.4）可知

$$i_1+\cdots+i_l=i_{l+1}+\cdots+i_k$$

将参考电流代入上式并将符号为负的参考电流整理到等号的另一侧。这样得到的等式左边为流出该节点的参考电流，右边为流入该节点的参考电流。于是证明了参考电流也满足式（A5.3）和式（A5.4）。因此以后在应用KCL的时候不必指明实际电流还是参考电流。

## A6 KVL

类似于KCL，如果设电路满足A4节的集总参数条件，根据电路的某回路（不含独立电压源）选择一条闭合路径，路径的方向任意指定，如图A6.1所示。路径的方向和实际支路上电场强度的方向已标注于图中。

>图A6.1 KVL的推导

图A6.1所示的闭合路径包含了一个回路，根据集总参数电路的条件，在该闭合路径上应满足 $\dfrac{\mathrm{d}\varPhi}{\mathrm{d}t}=0$，于是在闭合路径上对电场强度进行线积分，有

$$\oint_{L}\boldsymbol{E}\cdot\mathrm{d}\boldsymbol{l}=0 \tag{A6.1}$$

由于在电路中电场强度与闭合路径方向一致，同时根据 $AB$ 两点间的电压定义

$$u_{AB}=\int_{A}^{B}\boldsymbol{E}\cdot\mathrm{d}\boldsymbol{l} \tag{A6.2}$$

可以得到

$$u_{PQ}-u_{RQ}+u_{RS}-u_{PS}=0$$

根据电压的定义有

$$u_{PQ}+u_{QR}+u_{RS}+u_{SP}=0$$

由于该回路是任意选取的，因此对集总参数电路中的任意回路，在任意时刻得到基尔霍夫电压定律，

$$\sum u=0 \tag{A6.3}$$

即电路中沿着任意回路实际的电压降的代数和为零。通过类似于基尔霍夫电流定律中的讨论可知，电路中沿着任意回路参考电压的代数和也为零。因此以后在应用KVL的时候不必指明实际电压还是参考电压。

在实际使用中，还存在另一种等效的KVL记忆方法。如果将式（A6.3）等号左边符号为负的电压移到等号右边，则KVL可以写为

$$\sum_{\mathrm{down}} u=\sum_{\mathrm{up}} u \tag{A6.4}$$

即任意回路中电压降的代数和等于电压升的代数和。

如果回路中存在独立电压源，结合式（1.3.14）所示电动势的定义，同样可得出式（A6.3）和式（A6.4）。

## A7 电阻

在第1章中通过电池与灯泡构成的手电筒电路介绍了从实际电路到物理模型，再到电路模型的抽象过程。其中讨论了灯泡中灯丝的电磁关系为

$$\boldsymbol{J}=\sigma\boldsymbol{E} \tag{A7.1}$$

其中 $\sigma$ 为电导率。这个关系对于一般的金属和电解液都是成立的。如果电路元件满足集总参数的要求和式（A7.1），则可以用电阻对其进行建模，宏观地描述导体中的载流子在电场力驱动下的定向运动能力。

现在有一根长度为 $L$，截面积为 $S$ 的均匀金属圆柱体在电路中作为电流的通路，如图A7.1所示。设该金属圆柱体满足A4节的集总参数条件，忽略边缘的电场效应，易知金属圆柱体中实际的电场方向向右。

>图A7.1 均匀金属圆柱体的电阻

为了便于讨论，将电磁场中电流和电压的定义重写如下：

$$i=\iint_{S}\boldsymbol{J}\cdot\mathrm{d}\boldsymbol{S} \tag{A7.2}$$

$$u_{AB}=\int_{A}^{B}\boldsymbol{E}\cdot\mathrm{d}\boldsymbol{l} \tag{A7.3}$$

假设计算电流 $i$ 的 $\mathrm{d}\boldsymbol{S}$ 法线方向为从左向右，计算电压 $u$ 的 $\mathrm{d}\boldsymbol{l}$ 方向也为从左向右，即电压电流为关联参考方向。因此有 $J=i/S$，$E=u/L$，将这两个式子代入式（A7.1），得到

$$u=\frac{L}{\sigma S}i \tag{A7.4}$$

将上式中的 $L/\sigma S$ 表示为电阻 $R$（resistance），就得到了金属圆柱体宏观上的性质，即

$$u=Ri \tag{A7.5}$$

式（A7.1）和式（A7.5）分别称为欧姆定律（Ohm's law）的微分形式和积分形式。

反之，如果电流和电压采用非关联的参考方向，则欧姆定律为

$$u=-Ri \tag{A7.6}$$

## A8 电容

对于两个互不相连的导体来说，如果平衡状态下它们带上等量异号电荷 $\pm q$，则在这两个导体之间的介质中存在电场，进而两个导体之间存在电压。如果电路元件满足集总参数的要求，则可以用电容对其进行建模，宏观地描述两个互不相连导体间电荷与电压的关系，其定义式为

$$C=\frac{q}{u} \tag{A8.1}$$

两导体间的电容只取决于导体的形状、尺寸以及导体间电介质的分布，与电量无关。

下面用图A8.1所示的平板电容器来说明（其中 $d$ 表示两平板间距离，$S$ 表示平板的面积）。忽略边缘效应，容易知道，静电平衡时所有电荷均匀分布在两平板的内表面上，两平板之间产生的均匀电场 $E$ 为 $\dfrac{\sigma}{\varepsilon_0\varepsilon_r}$[^3]，其中 $\sigma$ 为电荷面密度 $\left(\sigma=\dfrac{q}{S}\right)$，$\varepsilon_0$ 和 $\varepsilon_r$ 分别为真空中的介电常数和介质中的相对介电常数。由于场强均匀，上下平板间的电压为

$$u=Ed=\frac{d\sigma}{\varepsilon_0\varepsilon_r}$$

因此平板电容器的电容为

$$C=\frac{q}{u}=\frac{S\sigma}{\dfrac{d\sigma}{\varepsilon_0\varepsilon_r}}=\frac{\varepsilon_0\varepsilon_r S}{d} \tag{A8.2}$$

即图A8.1所示平板电容器的电容和平板面积成正比。式中 $S$ 为平板面积，$d$ 为平板间距离，$\varepsilon_0$ 为真空介电常数，$\varepsilon_r$ 为平板间介质的相对介电常数。

>图A8.1 平板电容器

结构比较复杂的两个导体之间的电容计算请参考电磁场有关书籍。

将电容元件放到电路中可能会产生电荷的流动。根据式（1.2.1）电流的定义，可知

$$i=\frac{\mathrm{d}q}{\mathrm{d}t}=\frac{\mathrm{d}Cu}{\mathrm{d}t}=C\frac{\mathrm{d}u}{\mathrm{d}t} \tag{A8.3}$$

式（A8.3）定义了电路中电容元件上的 $u$-$i$ 关系。

由于 $\pm q$ 电荷总是一起变化，从元件外部看有 $\dfrac{\mathrm{d}q_{\mathrm{int}}}{\mathrm{d}t}=0$。同时如果这两个导体的尺寸比加在它们上面的电磁波波长小很多，可以将两个导体及其之间的介质看做一个集总的电气元件，即该元件满足A4节中的3个条件。

## A9 电感（自感和互感）

根据电磁场的安培环路定理可知，在均匀介质恒定电流的磁场中，磁感应强度 $\boldsymbol{B}$ 沿任何闭合路径 $l$ 的线积分为

$$\oint_{L}\boldsymbol{B}\cdot\mathrm{d}\boldsymbol{l}=\mu_0\mu_r\sum i_{\mathrm{int}} \tag{A9.1}$$

其中 $\sum i_{\mathrm{int}}$ 表示穿过路径 $l$ 包围的面积的宏观电流代数和，$\mu_0$ 和 $\mu_r$ 分别为真空中的磁导率和介质中的相对磁导率。图A9.1表示了常用的线圈的电磁关系。

在获得磁感应强度后，根据磁通的定义 $\left(\varPhi=\iint_{S}\boldsymbol{B}\cdot\mathrm{d}\boldsymbol{S}\right)$ 和磁链的定义（$\varPsi=N\varPhi$，$N$ 为线圈匝数），可计算出由电流 $i$ 产生的磁链 $\varPsi$。如果电路元件满足集总参数的要求，则可以用电感对其进行建模，宏观地描述线圈中电流与磁链的关系，其定义式为

$$L=\frac{\varPsi}{i} \tag{A9.2}$$

>图A9.1 电感

如果经过线圈截面的磁链由线圈本身的电流产生，此时计算出的电感称作自感。线圈的自感只取决于线圈的几何形状、尺寸、匝数及其周围磁介质的分布，与电流无关。

对于如图A9.2所示的 $N$ 匝螺线管线圈来说，假设线圈产生的磁场强度在线圈包含的空间中均匀分布，而且不泄漏到线圈以外的空间中，磁场强度通路中均为线性介质，则有

$$L=\frac{\varPsi}{i}=\frac{N\varPhi}{i}=\frac{NSB}{i}=\frac{NS}{i}\mu_0\mu_r H=\frac{NS}{i}\mu_0\mu_r\frac{Ni}{l}=\mu_0\mu_r\frac{N^2S}{l} \tag{A9.3}$$

即图A9.2所示螺线管线圈的自感和线圈的匝数平方成正比。式中 $S$ 为线圈的截面积，$l$ 为磁路的长度，$N$ 为线圈匝数，$\mu_0$ 为真空磁导率，$\mu_r$ 为线圈包围介质的相对磁导率。

>图A9.2 螺线管线圈的电感

如果通过线圈截面的磁通发生变化，根据法拉第电磁感应定律，在图A9.1所示电动势参考方向下，有

$$e=-\frac{\mathrm{d}\varPsi}{\mathrm{d}t}=-L\frac{\mathrm{d}i}{\mathrm{d}t} \tag{A9.4}$$

如果线圈上定义的电压 $u$ 参考方向如图A9.1所示，即电压电流为关联参考方向，则

$$u=-e=L\frac{\mathrm{d}i}{\mathrm{d}t} \tag{A9.5}$$

式（A9.5）定义了电路中自感元件上的 $u$-$i$ 关系。

由于用式（A9.5）表示了自感元件上的 $u$-$i$ 关系，因此在包围自感元件的任意路径上有 $\dfrac{\mathrm{d}\varPhi}{\mathrm{d}t}=0$。如果线圈的尺寸比加在它们上面的电磁波波长小很多，可以将线圈及其之间的介质均看做一个集总的电气元件，即该元件满足A4节中的3个条件。

更为一般的情况是两个线圈之间有磁链的交链，如图A9.3所示。

>图A9.3 线圈间的互感

在 $N_1$ 匝线圈1中通有电流 $i_1$，产生的磁通为 $\varPhi_{11}$（表示线圈1产生，与线圈1交链的磁通）。该磁通有一部分未与 $N_2$ 匝线圈2交链，这部分漏磁通为 $\varPhi_{s1}$。其余磁通均与线圈2交链，称为 $\varPhi_{21}$（表示线圈1产生，与线圈2交链的磁通）。$\varPhi_{21}$ 会产生磁链 $\varPsi_{21}=N_2\varPhi_{21}$。根据电感的定义（式（A9.2）），可获得线圈1电流对线圈2磁链的互感 $M_{21}$ 为

$$M_{21}=\frac{\varPsi_{21}}{i_1} \tag{A9.6}$$

同理也可定义线圈2电流对线圈1磁链的互感 $M_{12}$ 为

$$M_{12}=\frac{\varPsi_{12}}{i_2} \tag{A9.7}$$

如果线圈周围的磁介质是线性的，则可由电磁场理论证明 $M_{12}=M_{21}$。两个线圈之间的互感只取决于两个线圈的几何形状、相对位置、匝数及其周围磁介质的分布，与电流无关。

对于如图A9.4所示的两个螺线管线圈来说，假设线圈产生的磁场强度在线圈包含的空间中均匀分布，而且不泄漏到线圈以外的空间中（即 $\varPhi_{11}=\varPhi_{21}=\varPhi$），两个线圈的尺寸完全一样，磁场强度通路中均为线性介质，则有

$$M_{21}=\frac{\varPsi_{21}}{i_1}=\frac{N_2\varPhi}{i_1}=\frac{N_2SB}{i_1}=\frac{N_2S}{i_1}\mu_0\mu_r H=\frac{N_2S}{i_1}\mu_0\mu_r\frac{N_1i_1}{l}=\mu_0\mu_r\frac{N_1N_2S}{l}=M_{12} \tag{A9.8}$$

即图A9.4所示螺线管线圈间互感和两个线圈的匝数乘积成正比，而且有 $M_{12}=M_{21}$。式中 $S$ 为线圈的截面积，$l$ 为磁路的长度，$N_1$ 和 $N_2$ 分别为两个线圈的匝数，$\mu_0$ 为真空磁导率，$\mu_r$ 为线圈包围介质的相对磁导率。

>图A9.4 螺线管线圈间的互感

如果由线圈1产生且通过线圈2截面的磁通发生变化，根据法拉第电磁感应定律，在图A9.3所示电动势参考方向下，有

$$e_{21}=-\frac{\mathrm{d}\varPsi_{21}}{\mathrm{d}t}=-M_{21}\frac{\mathrm{d}i_1}{\mathrm{d}t} \tag{A9.9}$$

如果线圈2上定义的电压 $u_{21}$ 参考方向如图A9.3所示，则

$$u_{21}=-e_{21}=M_{21}\frac{\mathrm{d}i_1}{\mathrm{d}t} \tag{A9.10}$$

同理可知

$$u_{12}=M_{12}\frac{\mathrm{d}i_2}{\mathrm{d}t} \tag{A9.11}$$

式（A9.10）和式（A9.11）定义了电路中互感线圈之间的 $u$-$i$ 关系。

由于用式（A9.10）和式（A9.11）表示了互感线圈之间的 $u$-$i$ 关系，因此在包围两个互感线圈的任意路径上有 $\dfrac{\mathrm{d}\varPhi}{\mathrm{d}t}=0$。如果线圈的尺寸比加在它们上面的电磁波波长小很多，可以将两个线圈及其之间的介质均看做集总的电气元件，即该元件满足A4节中的3个条件。

自感和互感统称为电感。

电压 $u$、电荷 $q$、磁链 $\varPsi$ 和电流 $i$ 这4个电路基本量和据此定义的电阻 $R$、电容 $C$ 和电感 $L$ 这3个电路基本模型之间的关系如图A9.5所示。

>图A9.5 电路基本量和电路基本模型间的关系

## 参考文献

[1] 江缉光. 电路原理. 北京：清华大学出版社，1997

[2] 邱关源. 电路. 第4版. 北京：高等教育出版社，1999

[3] 李瀚荪. 简明电路分析基础. 北京：高等教育出版社，2002

[4] 周守昌. 电路原理. 第2版. 北京：高等教育出版社，2004

[5] 张三慧. 大学物理学. 电磁学. 第2版. 北京：清华大学出版社，1999

[6] 赵凯华，陈熙谋. 电磁学. 第2版. 北京：高等教育出版社，1985

[7] 俞大光. 电工基础 上册. 修订本. 北京：人民教育出版社，1964

[8] 俞大光. 电工基础 下册. 修订本. 北京：人民教育出版社，1981

[9] 克鲁格. 电工原理. 第6版. 北京：人民教育出版社，1952

[10] 法肯伯尔格. 网络分析. 北京：科学出版社，1982

# 附录B 电路图论的基础知识及其在电路分析中的应用

本附录介绍电路图中树、树支、连支等概念，讨论电路的关联矩阵 $\boldsymbol{A}$、基本回路矩阵 $\boldsymbol{B_f}$、矩阵形式的KCL、KVL和支路 $u$-$i$ 约束关系，推导矩阵形式的节点电压法方程和回路电流法方程。

## B1 基本概念

2.4节中讨论了电路的支路、节点和回路这3个基本概念。本节在此基础上再介绍几个图论的概念，以便描述电路的联接方式。

在讨论电路图论的概念时，只对支路电压相互之间的关系和支路电流相互之间的关系感兴趣，而并不关心支路电压和支路电流之间的关系，即并不关心支路上的 $u$-$i$ 关系。于是在讨论图论的概念时往往忽略支路的元件，即仅用一根线段来表示一个支路。此时的电路图仅包括电路的节点和支路，称其为电路的图或电路的拓扑结构。图B1.1中（b）就是电路（a）的图。

下面先给出几个定义。

**图（graph）** 节点和支路的集合称作图。

**有向图（directed-graph）** 支路有方向的图称作有向图。如果在电路图中标注了所有支路电流的参考方向[^4]，则其对应的图是有向图。

**连通图（connected-graph）** 任意两节点之间都存在由支路构成的通路的图称作连通图。

**子图（sub-graph）** 如果图 $G'$ 的所有节点和支路都是图 $G$ 的节点和支路，则 $G'$ 是 $G$ 的子图。

**树（tree）** 如果图 $G$ 的一个子图满足下面3个条件，则被称为树 $T$：①是连通的；②包含 $G$ 的所有节点；③不包含回路。

每个图都有多种选取树的方法。图B1.2的（a）和（b）分别是图B1.1（b）的两棵树。

>图B1.1 电路和电路的图

**树支（tree branch）** 图 $G$ 中属于树 $T$ 的支路。

**连支（non-tree branch）** 图 $G$ 中不属于树 $T$ 的支路。

下面来构造一棵树。一开始只有节点（称为未完成节点），没有支路。第一次在任意两个节点之间添加1条支路，并将这两个节点称为已完成节点。第二条支路的一端是一个已完成节点，另一端必须是一个未完成节点（否则就会形成回路），联接完毕后该未完成节点成为已完成节点。如此进行下去，每次添加一条支路，将一个已完成节点和一个未完成节点联接起来。设图有 $n$ 个节点，则易知需要添加 $n-1$ 条支路才能最终构成一棵树。于是在有 $n$ 个节点、$b$ 条支路的图 $G$ 中，树支数量为 $n-1$，连支数量为 $b-n+1$。

>图B1.2 同一个图的两棵树

## B2 电路的矩阵

### B2.1 电路的关联矩阵 $\boldsymbol{A}$

将图B1.1重画为图B2.1，两者的不同之处在于，图B2.1（a）中标注了所有支路电流的参考方向，因此图B2.1（b）是有向图。图B2.1（b）中支路边的数字表示支路的编号，而节点边带括号的数字表示节点的编号。

>图B2.1 标注了支路电流参考方向的电路图及其对应的有向图

下面来研究图的支路与节点的关联情况，即哪些支路与哪些节点相连。不失一般性，设有向图有 $n$ 个节点，$b$ 条支路。容易知道，在有向图中任意一条支路与任意一个节点的关系只有3种：支路与节点相连，支路方向离开节点；支路与节点相连，支路方向指向节点；支路没有与节点联接在一起。因此，可以用一个 $n\times b$ 的矩阵来表示支路与节点的关联情况，其中的元素 $a_{ij}$ 定义为

$$a_{ij}=\begin{cases} 1 & \text{支路 } j \text{ 与节点 } i \text{ 相连，支路方向离开节点} \\ -1 & \text{支路 } j \text{ 与节点 } i \text{ 相连，支路方向指向节点} \\ 0 & \text{支路 } j \text{ 与节点 } i \text{ 不相连} \end{cases} \tag{B2.1}$$

对于图B2.1（b）所示的有向图，可以写出增广关联矩阵为

$$\boldsymbol{A}_a=\begin{matrix}\text{节}\\ \text{点}\end{matrix}\begin{bmatrix} & & & \text{支}\\\\ & & & \text{路}\\\\ 1&2&3&4&5&6\\\\ \end{bmatrix}\begin{bmatrix} 1&1&0&0&0&1\\\\ -1&0&-1&1&0&0\\\\ 0&-1&1&0&1&0\\\\ 0&0&0&-1&-1&-1 \end{bmatrix}\begin{matrix}(1)\\ (2)\\ (3)\\ (4)\end{matrix} \tag{B2.2}$$

观察图B2.1（b）对应的 $\boldsymbol{A}_a$ 矩阵可知，矩阵的行对应着有向图的节点，矩阵的列对应着有向图的支路。该矩阵 $\boldsymbol{A}_a$ 每列只有一个元素为1，一个元素为 $-1$，其余元素为零。其物理意义在于每条支路一定从一个节点出发，终止于另一个节点。此外，矩阵 $\boldsymbol{A}_a$ 每行中不等于零的元素数量大于或等于3。其物理意义在于每个节点起码有3条支路相连，这符合2.4节中关于电路节点的定义。

此外，根据式（B2.1）中矩阵元素的定义可知，将 $\boldsymbol{A}_a$ 矩阵的所有行向量相加得到一个 $b$ 维的零向量。这意味着矩阵 $\boldsymbol{A}_a$ 的行向量线性相关。也就是说，用 $n$ 个行向量来表示是冗余的。现在来讨论矩阵 $\boldsymbol{A}_a$ 线性无关的行向量数是多少，即矩阵 $\boldsymbol{A}_a$ 的秩是多少[^5]。参考文献[2]用消元法证明了矩阵 $\boldsymbol{A}_a$ 的秩为 $n-1$，感兴趣的读者可以参考。

可以从矩阵 $\boldsymbol{A}_a$ 中任意删除一行构成 $(n-1)\times b$ 维矩阵 $\boldsymbol{A}$，该矩阵的 $n-1$ 行线性无关，称矩阵 $\boldsymbol{A}$ 为有向图 $G$ 的关联矩阵（associate matrix）。结合2.4节的知识可知，删除的行对应参考节点。如果令节点4为参考节点，则删除式（B2.2）中的第4行，得到的关联矩阵为

$$\boldsymbol{A}=\begin{matrix}\text{节}\\ \text{点}\end{matrix}\begin{bmatrix} & & & \text{支}\\\\ & & & \text{路}\\\\ 1&2&3&4&5&6\\\\ \end{bmatrix}\begin{bmatrix} 1&1&0&0&0&1\\\\ -1&0&-1&1&0&0\\\\ 0&-1&1&0&1&0 \end{bmatrix}\begin{matrix}(1)\\ (2)\\ (3)\end{matrix} \tag{B2.3}$$

下面用图B2.1所示电路为例来讨论用关联矩阵表示的KCL和KVL。设支路电流为 $\boldsymbol{i}=[i_1,i_2,\cdots,i_6]^{\mathrm{T}}$，支路电压为 $\boldsymbol{u}=[u_1,u_2,\cdots,u_6]^{\mathrm{T}}$，节点电压为 $\boldsymbol{u}_n=[u_{n1},u_{n2},\cdots,u_{n4}]^{\mathrm{T}}$。

以流出节点的电流为正，可列写出4个KCL方程：

$$i_1+i_2+i_6=0$$

$$-i_1-i_3+i_4=0$$

$$-i_2+i_3+i_5=0$$

这对应着方程

$$\boldsymbol{A}_a\boldsymbol{i}=\boldsymbol{0}$$

由于矩阵 $\boldsymbol{A}_a$ 的秩为 $n-1$，删除参考节点（此时为节点4）的对应行，得到

$$\boldsymbol{A}\boldsymbol{i}=\boldsymbol{0} \tag{B2.4}$$

在图B2.1所示电路中，可列写6个KVL方程，即

$$u_1=u_{n1}-u_{n2}$$

$$u_2=u_{n1}-u_{n3}$$

$$u_3=-u_{n2}+u_{n3}$$

$$u_4=u_{n2}$$

$$u_5=u_{n3}$$

$$u_6=u_{n1}$$

这对应着方程

$$\boldsymbol{u}=\boldsymbol{A}^{\mathrm{T}}\boldsymbol{u}_n \tag{B2.5}$$

式（B2.4）和式（B2.5）分别表示了用关联矩阵 $\boldsymbol{A}$ 来表示的KCL和KVL。

根据前面的讨论可知，有向图 $G$ 的关联矩阵 $\boldsymbol{A}$ 的秩为 $n-1$，这对应着 $n$ 个节点、$b$ 条支路的电路中独立的KCL方程数量为 $n-1$ 个。

### B2.2 电路的基本回路矩阵 $\boldsymbol{B_f}$

2.4节介绍回路的概念，3.3节讨论回路电流。下面讨论给定电路的有向图和回路的选取方式后，如何用矩阵来表示回路方向与支路方向的关系。图B2.2中给出了有向图的独立回路 $l_1$、$l_2$ 和 $l_3$。

>图B2.2 有向图和回路

类似于关联矩阵 $\boldsymbol{A}$，也希望建立一个表示回路与支路关系的矩阵 $\boldsymbol{B}$。设有 $l$ 条回路使得每条支路都至少在一条回路中，则回路矩阵 $\boldsymbol{B}$ 有 $l\times b$ 个元素，每个元素的定义为

$$b_{ij}=\begin{cases} 1 & \text{支路 } j \text{ 包含在回路 } i \text{ 中，且两者方向一致} \\ -1 & \text{支路 } j \text{ 包含在回路 } i \text{ 中，且两者方向相反} \\ 0 & \text{支路 } j \text{ 不包含在回路 } i \text{ 中} \end{cases} \tag{B2.6}$$

于是在图B2.2所示的图中，矩阵 $\boldsymbol{B}$ 应表示为

$$\boldsymbol{B}=\begin{matrix} l_1\\ l_2\\ l_3 \end{matrix}\begin{bmatrix} -1&1&1&0&0&0\\ 0&0&-1&-1&1&0\\ -1&0&0&-1&0&1 \end{bmatrix} \tag{B2.7}$$

观察式（B2.7）可以发现，矩阵 $\boldsymbol{B}$ 不存在全为零的列向量，这对应着每条支路都至少被1个回路包含。此外，矩阵 $\boldsymbol{B}$ 每行至少有两个不等于零的元素，这对应着每个回路至少由两条支路组成。

类似于从矩阵 $\boldsymbol{A}_a$ 得到 $\boldsymbol{A}$ 的过程，也希望矩阵 $\boldsymbol{B}$ 的行向量线性无关。下面讨论利用树得到 $b-n+1$ 个线性无关回路的方法。

在图B2.1（b）所示有向图中指定一棵树。不失一般性，设为图B2.3所示。

对于 $n$ 个节点，$b$ 条支路的图 $G$，树支数量为 $n-1$，连支数量为 $b-n+1$。更重要的是，树本身不构成回路，但每添加1条连支，则该连支就会和一些树支产生一个新的回路，称之为单连支回路或基本回路。如果将该回路的方向与该连支的方向设为一致，就可以通过逐渐添加连支的办法得到 $b-n+1$ 个独立回路。这样得到的回路矩阵被称为基本回路矩阵（fundamental loop matrix）$\boldsymbol{B_f}$。

>图B2.3 图B2.1(b)所对应的一棵树

在图B2.3所示的树中，顺序添加连支2、5、6，可以得到基本回路矩阵 $\boldsymbol{B_f}$ 为

$$\boldsymbol{B_f}=\begin{matrix} l_1\\ l_2\\ l_3 \end{matrix}\begin{bmatrix} 1&0&0&-1&1&0\\ 0&1&0&0&-1&-1\\ 0&0&1&-1&0&-1 \end{bmatrix} \tag{B2.8}$$

式（B2.8）中，$l_2$、$l_5$ 和 $l_6$ 分别表示添加连支2、5、6构成的单连支回路。如果在基本回路矩阵的列中先写连支对应的支路，再写树支对应的支路（如式（B2.8）所示），则由于回路方向与连支方向一致，同时每个回路仅通过一条连支，因此表示连支与回路关系的分块矩阵是 $b-n+1$ 维的单位阵。于是可以将基本回路矩阵写为如下的分块矩阵形式：

$$\boldsymbol{B_f}=[\boldsymbol{B_l},\boldsymbol{B_t}] \tag{B2.9}$$

接下来讨论基本回路矩阵的秩。根据参考文献[3]的结论可知，阶梯矩阵的秩等于其非零行的行数。通过观察式（B2.8）可知，矩阵 $\boldsymbol{B_f}$ 是阶梯矩阵，其非零行的行数为 $b-n+1$。于是证明了通过一次添加一条连支的方法形成的矩阵 $\boldsymbol{B_f}$ 秩为 $b-n+1$，即所有行向量线性无关。

下面用图B2.2所示有向图为例，讨论用基本回路矩阵表示的KCL和KVL。设支路电流为 $\boldsymbol{i}=[i_1,i_2,\cdots,i_6]^{\mathrm{T}}$，支路电压为 $\boldsymbol{u}=[u_1,u_2,\cdots,u_6]^{\mathrm{T}}$，回路电流为 $\boldsymbol{i_l}=[i_{l1},i_{l2},i_{l3}]^{\mathrm{T}}$。

列写支路电流和回路电流的关系得

$$i_2=i_{l1}$$

$$i_5=i_{l2}$$

$$i_6=i_{l3}$$

$$i_1=-i_{l1}-i_{l3}$$

$$i_3=i_{l1}-i_{l2}$$

$$i_4=-i_{l2}-i_{l3}$$

每个回路电流对流经的任意节点都流入一次，流出一次，自动满足KCL，因此回路电流的线性组合也满足KCL。将上式整理，可得用基本回路矩阵表示的KCL，

$$\boldsymbol{i}=\boldsymbol{B_f}^{\mathrm{T}}\boldsymbol{i_l} \tag{B2.10}$$

将式（B2.9）代入式（B2.10），得

$$\boldsymbol{i_t}=\boldsymbol{B_t}^{\mathrm{T}}\boldsymbol{i_l} \tag{B2.11}$$

在单连支回路中应用KVL得到3个方程，即

$$u_2-u_1+u_3=0$$

$$u_5-u_3-u_4=0$$

$$u_6-u_1-u_4=0$$

这对应着方程

$$\boldsymbol{B_f}\boldsymbol{u}=\boldsymbol{0} \tag{B2.12}$$

将式（B2.9）代入式（B2.12），得

$$\boldsymbol{u_l}=-\boldsymbol{B_t}\boldsymbol{u_t} \tag{B2.13}$$

式（B2.10）（或式（B2.11））和式（B2.12）（或式（B2.13））分别表示了用基本回路矩阵来表示的KCL和KVL。

根据前面单连支回路的定义可知，在式（B2.12）（或式（B2.13））所示的KVL中，独立方程数为 $b-n+1$。这对应着 $n$ 个节点、$b$ 条支路的电路中独立的KVL方程数量为 $b-n+1$ 个。

## B3 支路电压、电流关系的矩阵形式

本节以电阻、独立电压源和独立电流源组成的电路为例说明支路电压、电流关系的矩阵形式。

在本节的讨论中定义如图B3.1所示的典型支路（typical branch）。图中 $R_k$ 为 $k$ 支路的电阻，$I_k$ 为 $k$ 支路的支路电流，$U_k$ 为 $k$ 支路的支路电压，$U_{Sk}$ 为 $k$ 支路的独立电压源，$I_{Sk}$ 为 $k$ 支路的独立电流源。将该典型支路抽象为一条支路，令其为 $k$ 支路。有向图中箭头所示方向即为支路 $k$ 的电压 $U_k$ 和电流$I_k$ 的关联参考方向。

>图B3.1 典型支路

对典型支路作如下规定：支路中必须包含电阻元件 $R_k$，至于独立电压源和独立电流源可有可无，若无独立电压源则 $U_{Sk}$ 为零，无独立电流源则 $I_{Sk}$ 为零。这样定义支路的目的是避免出现由纯独立电压源或纯独立电流源组成的支路，给下面要介绍的电路方程的列写提供方便。

将KCL、KVL和欧姆定律应用于图B3.1所示电路中，可得到 $k$ 支路电压、电流关系为

$$U_k=R_k(I_k+I_{Sk})-U_{Sk}=R_kI_k+R_kI_{Sk}-U_{Sk} \tag{B3.1}$$

或

$$I_k=G_kU_k+G_kU_{Sk}-I_{Sk} \tag{B3.2}$$

式中 $G_k$ 为 $k$ 支路的电导，

$$G_k=1/R_k$$

设电路中有 $b$ 条典型支路，则可以得到4个 $b$ 维列向量：支路电压向量 $\boldsymbol{U}=[U_1,\cdots,U_b]^{\mathrm{T}}$，支路电流向量 $\boldsymbol{I}=[I_1,\cdots,I_b]^{\mathrm{T}}$，支路独立电压源电压向量 $\boldsymbol{U_S}=[U_{S1},\cdots,U_{Sb}]^{\mathrm{T}}$ 和支路独立电流源电流向量 $\boldsymbol{I_S}=[I_{S1},\cdots,I_{Sb}]^{\mathrm{T}}$；两个 $b\times b$ 的对角矩阵：支路电阻矩阵 $\boldsymbol{R}=\mathrm{diag}[R_1,\cdots,R_b]$，支路电导矩阵 $\boldsymbol{G}=\mathrm{diag}[G_1,\cdots,G_b]$，其中 $\boldsymbol{G}=\boldsymbol{R}^{-1}$。

将 $b$ 条支路的电压、电流关系写成式（B3.1）形式，得到用支路电流表示支路电压的矩阵形式的约束方程为

$$\begin{bmatrix} U_1\\ U_2\\ \vdots\\ U_b \end{bmatrix}=\begin{bmatrix} R_1&0&\cdots&0\\ 0&R_2&\cdots&0\\ \vdots&\vdots&&\vdots\\ 0&0&\cdots&R_b \end{bmatrix}\begin{bmatrix} I_1\\ I_2\\ \vdots\\ I_b \end{bmatrix}+\begin{bmatrix} R_1&0&\cdots&0\\ 0&R_2&\cdots&0\\ \vdots&\vdots&&\vdots\\ 0&0&\cdots&R_b \end{bmatrix}\begin{bmatrix} I_{S1}\\ I_{S2}\\ \vdots\\ I_{Sb} \end{bmatrix}-\begin{bmatrix} U_{S1}\\ U_{S2}\\ \vdots\\ U_{Sb} \end{bmatrix} \tag{B3.3}$$

即

$$\boldsymbol{U}=\boldsymbol{R}\boldsymbol{I}+\boldsymbol{R}\boldsymbol{I_S}-\boldsymbol{U_S} \tag{B3.4}$$

将 $b$ 条支路的电压、电流关系写成式（B3.2）形式，得到用支路电压表示支路电流的矩阵形式的约束方程为

$$\begin{bmatrix} I_1\\ I_2\\ \vdots\\ I_b \end{bmatrix}=\begin{bmatrix} G_1&0&\cdots&0\\ 0&G_2&\cdots&0\\ \vdots&\vdots&&\vdots\\ 0&0&\cdots&G_b \end{bmatrix}\begin{bmatrix} U_1\\ U_2\\ \vdots\\ U_b \end{bmatrix}+\begin{bmatrix} G_1&0&\cdots&0\\ 0&G_2&\cdots&0\\ \vdots&\vdots&&\vdots\\ 0&0&\cdots&G_b \end{bmatrix}\begin{bmatrix} U_{S1}\\ U_{S2}\\ \vdots\\ U_{Sb} \end{bmatrix}-\begin{bmatrix} I_{S1}\\ I_{S2}\\ \vdots\\ I_{Sb} \end{bmatrix} \tag{B3.5}$$

即

$$\boldsymbol{I}=\boldsymbol{G}\boldsymbol{U}+\boldsymbol{G}\boldsymbol{U_S}-\boldsymbol{I_S} \tag{B3.6}$$

> [!example] **例 B3.1** 电路如图B3.2所示。写出矩阵形式的支路电压、电流关系。
>
> 解：将元件号设为支路号，原电路的有向图如图B3.3所示，图中箭头方向表示支路电压和支路电流的关联参考方向，旁边的数字表示支路编号。

>图B3.2 例B3.1图

>图B3.3 有向图

设支路电压向量为

$$\boldsymbol{U}=[U_1,U_2,U_3,U_4,U_5,U_6]^{\mathrm{T}}$$

支路电流向量为

$$\boldsymbol{I}=[I_1,I_2,I_3,I_4,I_5,I_6]^{\mathrm{T}}$$

根据电路结构和参数，写出支路电阻矩阵为

$$\boldsymbol{R}=\mathrm{diag}[R_1,R_2,R_3,R_4,R_5,R_6]$$

支路电导矩阵为

$$\boldsymbol{G}=\mathrm{diag}[1/R_1,1/R_2,1/R_3,1/R_4,1/R_5,1/R_6]$$

$$=\mathrm{diag}[G_1,G_2,G_3,G_4,G_5,G_6]$$

对照典型支路中各电压、电流的参考方向，得支路独立电压源电压向量

$$\boldsymbol{U_S}=[-U_{S1},0,0,0,U_{S5},-U_{S6}]^{\mathrm{T}}$$

支路独立电流源电流向量

$$\boldsymbol{I_S}=[0,0,0,0,-I_{S5},0]^{\mathrm{T}}$$

将以上各向量和矩阵代入式（B3.4）或式（B3.6），得矩阵形式的支路电压、电流关系为

$$+\begin{bmatrix} R_1&0&0&0&0&0\\ 0&R_2&0&0&0&0\\ 0&0&R_3&0&0&0\\ 0&0&0&R_4&0&0\\ 0&0&0&0&R_5&0\\ 0&0&0&0&0&R_6 \end{bmatrix}\begin{bmatrix} 0\\ 0\\ 0\\ 0\\ -I_{S5}\\ 0 \end{bmatrix}-\begin{bmatrix} -U_{S1}\\ 0\\ 0\\ 0\\ U_{S5}\\ -U_{S6} \end{bmatrix}$$

或

$$\begin{bmatrix} I_1\\ I_2\\ I_3\\ I_4\\ I_5\\ I_6 \end{bmatrix}=\begin{bmatrix} G_1&0&0&0&0&0\\ 0&G_2&0&0&0&0\\ 0&0&G_3&0&0&0\\ 0&0&0&G_4&0&0\\ 0&0&0&0&G_5&0\\ 0&0&0&0&0&G_6 \end{bmatrix}\begin{bmatrix} U_1\\ U_2\\ U_3\\ U_4\\ U_5\\ U_6 \end{bmatrix}$$

$$+\begin{bmatrix} G_1&0&0&0&0&0\\ 0&G_2&0&0&0&0\\ 0&0&G_3&0&0&0\\ 0&0&0&G_4&0&0\\ 0&0&0&0&G_5&0\\ 0&0&0&0&0&G_6 \end{bmatrix}\begin{bmatrix} -U_{S1}\\ 0\\ 0\\ 0\\ U_{S5}\\ -U_{S6} \end{bmatrix}-\begin{bmatrix} 0\\ 0\\ 0\\ 0\\ -I_{S5}\\ 0 \end{bmatrix}$$

需要指出，本节未涉及含受控源和互感元件电路中支路电压、电流关系的矩阵形式，对此感兴趣的读者可阅读参考文献[1]和[4]。

## B4 矩阵形式的节点方程

B3节推导了支路电压与支路电流关系的矩阵形式为

$$\boldsymbol{I}=\boldsymbol{G}\boldsymbol{U}+\boldsymbol{G}\boldsymbol{U_S}-\boldsymbol{I_S}$$

将上式等号两边分别左乘关联矩阵 $\boldsymbol{A}$，得

$$\boldsymbol{A}\boldsymbol{I}=\boldsymbol{A}(\boldsymbol{G}\boldsymbol{U}+\boldsymbol{G}\boldsymbol{U_S}-\boldsymbol{I_S})=\boldsymbol{A}\boldsymbol{G}\boldsymbol{U}+\boldsymbol{A}\boldsymbol{G}\boldsymbol{U_S}-\boldsymbol{A}\boldsymbol{I_S} \tag{B4.1}$$

由式（B2.4）表示的矩阵形式的KCL

$$\boldsymbol{A}\boldsymbol{I}=\boldsymbol{0}$$

可知，式（B4.1）等号右边项等于零，即

$$\boldsymbol{A}\boldsymbol{G}\boldsymbol{U}+\boldsymbol{A}\boldsymbol{G}\boldsymbol{U_S}-\boldsymbol{A}\boldsymbol{I_S}=\boldsymbol{0}$$

再将式（B2.5）表示的矩阵形式KVL

$$\boldsymbol{U}=\boldsymbol{A}^{\mathrm{T}}\boldsymbol{U}_n$$

代入上式，得

$$\boldsymbol{A}\boldsymbol{G}\boldsymbol{A}^{\mathrm{T}}\boldsymbol{U}_n+\boldsymbol{A}\boldsymbol{G}\boldsymbol{U_S}-\boldsymbol{A}\boldsymbol{I_S}=\boldsymbol{0}$$

由上式即得以节点电压为变量的矩阵形式方程（即矩阵形式的节点方程）：

$$\boldsymbol{A}\boldsymbol{G}\boldsymbol{A}^{\mathrm{T}}\boldsymbol{U}_n=\boldsymbol{G}_n\boldsymbol{U}_n=\boldsymbol{A}\boldsymbol{I_S}-\boldsymbol{A}\boldsymbol{G}\boldsymbol{U_S} \tag{B4.2}$$

其中 $\boldsymbol{G}_n=\boldsymbol{A}\boldsymbol{G}\boldsymbol{A}^{\mathrm{T}}$ 称为节点电导矩阵（node conductance matrix）。建立了节点方程，就可求出节点电压，由此可求得支路电压、电流和功率。

> [!example] **例 B4.1** 用节点电压法列写图B4.1所示电路矩阵形式的节点方程。
>
> 解：节点方程 $\boldsymbol{G}_n\boldsymbol{U}_n=\boldsymbol{A}\boldsymbol{I_S}-\boldsymbol{A}\boldsymbol{G}\boldsymbol{U_S}$ 的系统列写可以归纳为以下几步：
>
> （1）画出有向图，如图B4.2所示。图中方向表示原电路图中支路电压、电流的关联参考方向。

>图B4.1 例B4.1图

>图B4.2 有向图

（2）写关联矩阵

$$\boldsymbol{A}=\begin{bmatrix} 1&1&0&0&0&1\\ 0&-1&1&1&0&0\\ 0&0&-1&0&1&-1 \end{bmatrix}$$

（3）列支路电导矩阵

$$\boldsymbol{G}=\mathrm{diag}[2,0.5,2,0.2,1,1]$$

（4）列独立电压源和独立电流源列向量

$$\boldsymbol{U_S}=[-5,0,0,0,0,-3]^{\mathrm{T}}$$

$$\boldsymbol{I_S}=[0,-1,0,0,3,0]^{\mathrm{T}}$$

（5）将矩阵 $\boldsymbol{A}$、$\boldsymbol{G}$，列向量 $\boldsymbol{U_S}$、$\boldsymbol{I_S}$ 代入节点方程 $\boldsymbol{A}\boldsymbol{G}\boldsymbol{A}^{\mathrm{T}}\boldsymbol{U}_n=\boldsymbol{A}\boldsymbol{I_S}-\boldsymbol{A}\boldsymbol{G}\boldsymbol{U_S}$，得

$$\begin{bmatrix} 1&1&0&0&0&1\\ 0&-1&1&1&0&0\\ 0&0&-1&0&1&-1 \end{bmatrix}\begin{bmatrix} 2&0&0&0&0&0\\ 0&0.5&0&0&0&0\\ 0&0&2&0&0&0\\ 0&0&0&0.2&0&0\\ 0&0&0&0&1&0\\ 0&0&0&0&0&1 \end{bmatrix}\begin{bmatrix} 1&0&0\\ 1&-1&0\\ 0&1&-1\\ 0&1&0\\ 0&0&1\\ 1&0&-1 \end{bmatrix}\begin{bmatrix} U_{n1}\\ U_{n2}\\ U_{n3} \end{bmatrix}$$

$$=\begin{bmatrix} 1&1&0&0&0&1\\ 0&-1&1&1&0&0\\ 0&0&-1&0&1&-1 \end{bmatrix}\begin{bmatrix} 0\\ -1\\ 0\\ 0\\ 3\\ 0 \end{bmatrix}-\begin{bmatrix} 1&1&0&0&0&1\\ 0&-1&1&1&0&0\\ 0&0&-1&0&1&-1 \end{bmatrix}$$

$$\times\begin{bmatrix} 2&0&0&0&0&0\\ 0&0.5&0&0&0&0\\ 0&0&2&0&0&0\\ 0&0&0&0.2&0&0\\ 0&0&0&0&1&0\\ 0&0&0&0&0&1 \end{bmatrix}\begin{bmatrix} -5\\ 0\\ 0\\ 0\\ 0\\ -3 \end{bmatrix} \tag{B4.3}$$

式（B4.3）就是要列写的以节点电压为变量的矩阵形式的方程。矩阵运算由计算机程序来完成，注意到式中零元素很多，可以采用稀疏矩阵（sparse matrix）技术进行处理。实际应用中关联矩阵 $\boldsymbol{A}$、支路电导矩阵 $\boldsymbol{G}$、独立电压源列向量 $\boldsymbol{U_S}$、独立电流源列向量 $\boldsymbol{I_S}$ 并不需要手工列出后输入到计算机，只要输入电路图，其他的工作都由软件实现。

为验证正确性，不妨化简式（B4.3），得

$$\begin{bmatrix} 3.5&-0.5&-1\\ -0.5&2.7&-2\\ -1&-2&4 \end{bmatrix}\begin{bmatrix} U_{n1}\\ U_{n2}\\ U_{n3} \end{bmatrix}=\begin{bmatrix} 12\\ 1\\ 0 \end{bmatrix}$$

其结果与3.2节通过观察电路手工写出的方程是一致的。

对于支路数、节点数很大的电路，显然需要通过编写程序由计算机自动建立方程。节点电压法是普遍被采用的方法，常用的电路分析软件Spice即是基于节点电压法编写的。

当电路中出现在两个节点之间有纯独立电压源支路时，由于在纯独立电压源支路中的电阻为零，若采用前面介绍的方法列写节点方程，会遇到支路电导矩阵元素为无穷大的问题。这时需要对节点法进行一点修改，增加流经纯独立电压源支路的电流变量。这种方法称为改进节点法。此外，还可以将电路中全部支路电压、支路电流和独立节点电压作为待求量来求解电路，这种方法称为表格法。在表格法中建立系数矩阵的规则很简单，相当于填写一张表格，且通用性强，易于用计算机来完成，可用于求解大规模电路。该方法的另一优点是对支路元件无任何限定。

虽然与节点法、回路法相比较，表格法方程个数要多，但是方程组系数矩阵中的零元素较多，用计算机稀疏矩阵技术可以很方便地求解这类方程组。对改进节点法和表格法感兴趣的读者可阅读参考文献[1]和[4]。

## B5 矩阵形式的回路方程

回路电流法以 $(b-n+1)$ 个独立回路电流为待求变量来列写方程。这里取基本回路为独立回路。每个基本回路只含一个连支，所以取连支电流为包含该连支的基本回路中的回路电流，设其为未知变量。其他各支路电流都可由连支电流表示。

按照图B3.1定义的典型支路对给定的电路画出有向图 $G$。为列写电路的矩阵方程，在图 $G$ 中任选一树。设连支电流向量为 $\boldsymbol{I_l}$，支路电压向量为 $\boldsymbol{U}$，并形成基本回路矩阵 $\boldsymbol{B_f}$，支路电阻矩阵 $\boldsymbol{R}$，独立电压源列向量 $\boldsymbol{U_S}$，独立电流源列向量 $\boldsymbol{I_S}$。

将式（B2.12）表示的矩阵形式的KVL方程（$\boldsymbol{B_f}\boldsymbol{U}=\boldsymbol{0}$）代入支路电压、电流元件约束关系式（B3.4）（$\boldsymbol{U}=\boldsymbol{R}\boldsymbol{I}+\boldsymbol{R}\boldsymbol{I_S}-\boldsymbol{U_S}$），可得

$$\boldsymbol{B_f}\boldsymbol{U}=\boldsymbol{B_f}\boldsymbol{R}\boldsymbol{I}+\boldsymbol{B_f}\boldsymbol{R}\boldsymbol{I_S}-\boldsymbol{B_f}\boldsymbol{U_S}=\boldsymbol{0} \tag{B5.1}$$

将式（B2.10）表示的矩阵形式的KCL方程（$\boldsymbol{I}=\boldsymbol{B_f}^{\mathrm{T}}\boldsymbol{I_l}$）代入式（B5.1），得到以连支电流为变量的矩阵形式的回路电流方程：

$$\boldsymbol{B_f}\boldsymbol{R}\boldsymbol{B_f}^{\mathrm{T}}\boldsymbol{I_l}=\boldsymbol{B_f}\boldsymbol{U_S}-\boldsymbol{B_f}\boldsymbol{R}\boldsymbol{I_S} \tag{B5.2}$$

令式中

$$\boldsymbol{B_f}\boldsymbol{R}\boldsymbol{B_f}^{\mathrm{T}}=\boldsymbol{R_l}$$

称 $\boldsymbol{R_l}$ 为回路电阻矩阵（loop resistance matrix）。

> [!example] **例 B5.1** 用回路电流法列写图B5.1所示电路的矩阵方程。
>
> 解：选支路1、2、3为树支，单连支回路 $l_1$、$l_2$、$l_3$ 如图B5.2中虚线所示。待求连支电流向量为 $\boldsymbol{I_l}=[I_4,I_5,I_6]^{\mathrm{T}}$。

>图B5.1 例B5.1图

>图B5.2 有向图和回路选择

回路方程 $\boldsymbol{R_l}\boldsymbol{I_l}=\boldsymbol{B_f}\boldsymbol{U_S}-\boldsymbol{B_f}\boldsymbol{R}\boldsymbol{I_S}$ 的系统列写可归纳为如下几步：

（1）写出基本回路矩阵

$$\boldsymbol{B_f}=\begin{bmatrix} 1&1&0&1&0&0\\ 0&-1&1&0&1&0\\ 1&1&-1&0&0&1 \end{bmatrix}$$

回路阻抗矩阵

$$\boldsymbol{R_l}=\boldsymbol{B_f}\boldsymbol{R}\boldsymbol{B_f}^{\mathrm{T}}$$

（2）写出支路电阻矩阵

$$\boldsymbol{R}=\mathrm{diag}[R_1,R_2,R_3,R_4,R_5,R_6]^{\mathrm{T}}$$

（3）列支路独立电压源、独立电流源列向量

$$\boldsymbol{U_S}=[0,0,0,0,U_{S5},0]^{\mathrm{T}}$$

$$\boldsymbol{I_S}=[0,0,0,0,0,-I_{S6}]^{\mathrm{T}}$$

（4）将矩阵 $\boldsymbol{B_f}$、$\boldsymbol{R}$ 和向量 $\boldsymbol{U_S}$、$\boldsymbol{I_S}$ 代入式（B5.2），得

$$\begin{bmatrix} 1&1&0&1&0&0\\ 0&-1&1&0&1&0\\ 1&1&-1&0&0&1 \end{bmatrix}\begin{bmatrix} R_1&0&0&0&0&0\\ 0&R_2&0&0&0&0\\ 0&0&R_3&0&0&0\\ 0&0&0&R_4&0&0\\ 0&0&0&0&R_5&0\\ 0&0&0&0&0&R_6 \end{bmatrix}\begin{bmatrix} 1&0&1\\ 1&-1&1\\ 0&1&-1\\ 1&0&0\\ 0&1&0\\ 0&0&1 \end{bmatrix}\begin{bmatrix} I_4\\ I_5\\ I_6 \end{bmatrix}$$

$$=\begin{bmatrix} 1&1&0&1&0&0\\ 0&-1&1&0&1&0\\ 1&1&-1&0&0&1 \end{bmatrix}\begin{bmatrix} 0\\ 0\\ 0\\ 0\\ U_{S5}\\ 0 \end{bmatrix}-\begin{bmatrix} 1&1&0&1&0&0\\ 0&-1&1&0&1&0\\ 1&1&-1&0&0&1 \end{bmatrix}$$

$$\times\begin{bmatrix} R_1&0&0&0&0&0\\ 0&R_2&0&0&0&0\\ 0&0&R_3&0&0&0\\ 0&0&0&R_4&0&0\\ 0&0&0&0&R_5&0\\ 0&0&0&0&0&R_6 \end{bmatrix}\begin{bmatrix} 0\\ 0\\ 0\\ 0\\ 0\\ -I_{S6} \end{bmatrix} \tag{B5.3}$$

式（B5.3）就是要列写的以连支电流 $[I_4,I_5,I_6]^{\mathrm{T}}$ 为变量的矩阵形式的回路方程。为验证起见，不妨做矩阵相乘，得

$$\begin{bmatrix} R_1+R_2+R_4&-R_2&R_1+R_2\\ -R_2&R_5+R_2+R_3&-R_2-R_3\\ R_1+R_2&-R_2-R_3&R_1+R_2+R_3+R_6 \end{bmatrix}\begin{bmatrix} I_4\\ I_5\\ I_6 \end{bmatrix}=\begin{bmatrix} 0\\ U_{S5}\\ R_6I_{S6} \end{bmatrix}$$

其结果与3.3节通过观察电路手工列写的方程是一样的。

[^1]: 参见第3章的内容。
[^2]: 2.1节讨论理想导线的性质。
[^3]: 该式的获得请参考电磁场相关书籍，如参考文献[5,6]。
[^4]: 在电路的图论研究中，一般假设支路上电压和电流具有关联的参考方向。
[^5]: 2.4节中将讨论线性无关的KCL方程数量问题，该问题与矩阵 $\boldsymbol{A}_a$ 的秩的问题是等价的。

## 参考文献

[1] 江缉光. 电路原理. 北京: 清华大学出版社，1997

[2] 卢开澄，卢华明. 图论及其应用. 第 2 版. 北京: 清华大学出版社，1995

[3] 居余马，林翠琴. 线性代数简明教程. 北京: 清华大学出版社，2004

[4] 邱关源. 网络图论简介. 北京: 人民教育出版社，1978

# 附录C 常系数线性常微分方程的求解

本附录介绍常系数线性常微分方程的时域解法。

## C1 常系数线性常微分方程的形式和名词解释

$n$ 阶常系数线性常微分方程的标准形式为

$$y^{(n)} + a_1 y^{(n-1)} + \cdots + a_{n-1} y' + a_n y = f(t)$$

其中，$a_1$、$a_2$、$\cdots$、$a_n$ 是常数，$f(t)$ 为连续函数。

$n$ 阶常系数线性常微分方程的含有 $n$ 个独立的任意常数的解，叫做一般解（通解）。

常系数线性常微分方程不含任意常数的解，叫做特解。

把常系数线性常微分方程与初始条件合在一起叫做该微分方程的初值问题。初值问题的解是既满足该微分方程又满足初始条件的特解。

## C2 常系数齐次线性常微分方程的解法

$n$ 阶常系数齐次线性常微分方程的标准形式为

$$y^{(n)} + a_1 y^{(n-1)} + \cdots + a_{n-1} y' + a_n y = 0$$

其中 $a_1$、$a_2$、$\cdots$、$a_n$ 是常数，等号右端自由项为零。

其一般解的解法步骤如下。

（1）求常系数齐次线性常微分方程的特征方程（只要将常系数齐次线性常微分方程式中的 $y^{(k)}$ 换写成 $p^k$，$k=0,1,\cdots,n$，即得其特征方程）：

$$p^n + a_1 p^{n-1} + \cdots + a_{n-1} p + a_n = 0$$

（2）求特征方程的根（称为微分方程的特征根）。

（3）根据求得的特征方程的 $n$ 个特征根可得到微分方程的 $n$ 个线性无关的一般解。根的形式不同，解的形式也不同，这又可分为以下几种情况。

① 特征方程有 $n$ 个互异的实根 $p_1$、$p_2$、$\cdots$、$p_n$，则方程的解为 $y = c_1 \mathrm{e}^{p_1 t} + c_2 \mathrm{e}^{p_2 t} + \cdots + c_n \mathrm{e}^{p_n t}$。

> [!example] **例 C1** 求齐次微分方程 $y'' - 2y' - 3y = 0$ 的解。
>
> 解：特征方程 $p^2 - 2p - 3 = 0$，求出特征方程的根 $p_1 = -1$，$p_2 = 3$，则方程的解为 $y = c_1 \mathrm{e}^{3t} + c_2 \mathrm{e}^{-t}$。

② 特征方程有 $n$ 个实根，但存在重根（设 $p_0$ 是方程的 $k$ 重根），则方程的解为

$$y = (c_1 + c_2 t + \cdots + c_k t^{k-1}) \mathrm{e}^{p_0 t} + c_{k+1} \mathrm{e}^{p_{k+1} t} + \cdots + c_n \mathrm{e}^{p_n t}$$

> [!example] **例 C2** 求齐次微分方程 $y''' + 3y'' - 4y = 0$ 的解。
>
> 解：特征方程 $p^3 + 3p^2 - 4 = 0$，求出特征方程的根为
>
> $$p_1 = 1, \quad p_2 = p_3 = -2$$
>
> 方程的解为
>
> $$y = c_1 \mathrm{e}^{t} + c_2 \mathrm{e}^{-2t} + c_3 t \mathrm{e}^{-2t}$$

③ 特征方程的 $n$ 个特征根中存在复数根（举例说明）。

- 存在 1 对不重复的复数根 $a \pm \mathrm{j}\beta$，$n-2$ 个互异的实根，则方程的解为

$$y = c_1 \mathrm{e}^{at} \cos \beta t + c_2 \mathrm{e}^{at} \sin \beta t + c_3 \mathrm{e}^{p_3 t} + \cdots + c_n \mathrm{e}^{p_n t}$$

> [!example] **例 C3** 求齐次微分方程 $2y''' + 3y'' + 8y' - 5y = 0$ 的解。
>
> 解：特征方程 $2p^3 + 3p^2 + 8p - 5 = 0$，求出特征方程的根为
>
> $$p_1 = 1/2, \quad p_2 = -1 + \mathrm{j}2, \quad p_3 = -1 - \mathrm{j}2$$
>
> 方程的解为
>
> $$y = c_1 \mathrm{e}^{t/2} + c_2 \mathrm{e}^{-t} \cos 2t + c_3 \mathrm{e}^{-t} \sin 2t$$

- 存在 2 对重复的复数根 $a \pm \mathrm{j}\beta$，$n-4$ 个互异的实根，则方程的解为

$$y = c_1 \mathrm{e}^{at} \cos \beta t + c_2 \mathrm{e}^{at} \sin \beta t + c_3 t \mathrm{e}^{at} \cos \beta t + c_4 t \mathrm{e}^{at} \sin \beta t + c_5 \mathrm{e}^{p_5 t} + \cdots + c_n \mathrm{e}^{p_n t}$$

> [!example] **例 C4** 求齐次微分方程 $y^{(5)} + y^{(4)} + 4y^{(3)} + 4y^{(2)} + 4y' + 4y = 0$ 的解。
>
> 解：特征方程
>
> $$p^5 + p^4 + 4p^3 + 4p^2 + 4p + 4 = 0$$
>
> $$(p + 1)(p^2 + 2)^2 = 0$$
>
> 求出特征方程的根
>
> $$p_1 = -1, \quad p_2 = p_3 = +\mathrm{j}\sqrt{2}, \quad p_4 = p_5 = -\mathrm{j}\sqrt{2}$$
>
> 方程的解为
>
> $$y = c_1 \mathrm{e}^{-t} + c_2 \cos \sqrt{2}\, t + c_3 \sin \sqrt{2}\, t + t(c_4 \cos \sqrt{2}\, t + c_5 \sin \sqrt{2}\, t)$$

## C3 常系数非齐次线性常微分方程的解法

$n$ 阶常系数非齐次线性常微分方程的标准形式为

$$y^{(n)} + a_1 y^{(n-1)} + \cdots + a_{n-1} y' + a_n y = f(t)$$

其中 $a_1$、$a_2$、$\cdots$、$a_n$ 是常数，$f(t)$ 为连续函数。

解的形式为

$$y = \bar{y}(t) + Y(t)$$

其中，$\bar{y}(t)$ 是常系数齐次线性常微分方程 $y^{(n)} + a_1 y^{(n-1)} + \cdots + a_{n-1} y' + a_n y = 0$ 的通解；$Y(t)$ 是常系数非齐次线性常微分方程 $y^{(n)} + a_1 y^{(n-1)} + \cdots + a_{n-1} y' + a_n y = f(t)$ 的任意一个特解。

其初值问题的求解步骤如下：

第 1 步：求方程对应的常系数齐次线性常微分方程的通解（称作自由分量）；

第 2 步：求常系数非齐次线性常微分方程的任一个特解（称作强制分量）；

第 3 步：将自由分量与强制分量相加，得到常系数非齐次线性常微分方程的通解；

第 4 步：根据初始条件确定通解中的待定系数，从而得到满足方程初始条件的解。

可用待定系数法求常系数非齐次线性常微分方程的特解（强制分量）。其原理是：根据方程等式右端自由项 $f(t)$ 的函数类型，猜想它的特解是何种函数类型（包括常数），然后将其代入方程来确定所猜的函数中的系数。

> [!example] **例 C5** 求方程 $(3-t)y'' + (t-2)y' - y = t^2 - 6t + 6$ 的一个特解。
>
> 解：通过观察可知 $y = at^2 + bt + c$ 可能是上述方程的一个特解，将其代入方程得
>
> $$(3-t)(2a) + (t-2)(2at + b) - (at^2 + bt + c) = t^2 - 6t + 6$$
>
> $$at^2 - 6at + (6a - 2b - c) = t^2 - 6t + 6$$
>
> $$\Rightarrow a = 1, \quad c = -2b$$
>
> 取 $b = 0$，则 $c = 0$，于是 $y = t^2$ 是方程的一个特解。

表 C1 总结了一部分常见函数所对应的特解。

**表 C1 常见函数 $f(t)$ 所对应的特解函数类型**

| $f(t)$（自由项） | 特解的函数类型 |
| --- | --- |
| $C$（常数） | $C_1$（常数） |
| $\mathrm{e}^{at}$ | $C\mathrm{e}^{at}$<br>$a$ 不等于齐次方程特征方程的特征根 |
| $\sin at$、$\cos at$ | $C_1 \sin(at + C_2)$ 或 $C_1 \sin at + C_2 \cos at$<br>$\pm \mathrm{j}a$ 不等于齐次方程特征方程的特征根 |
| $t^k$ | $C_1 t^k + C_2 t^{k-1} + \cdots + C_k t + C_{k+1}$ |

求特解也可用常数变易法，感兴趣的读者可阅读参考文献 [1~4]。如果 $f(t)$ 为指数或者正余弦函数，同时其指数系数或正余弦系数等于齐次方程特征方程的特征根，则非齐次方程的特解也需要通过常数变易法来求得。

> [!example] **例 C6** 求初值问题 $y'' + 200y' + 2 \times 10^4 y = 2 \times 10^4$，$y(0) = 2$，$\left.\dfrac{\mathrm{d}y}{\mathrm{d}t}\right|_{t=0} = 0$ 的解。
>
> 解：（1）求齐次方程的通解。特征方程为
>
> $$p^2 + 200p + 20000 = 0$$
>
> 特征根为
>
> $$p_{1,2} = -100 \pm \mathrm{j}100$$
>
> 则齐次方程的通解为 $y(t) = C_1 \mathrm{e}^{-100t} \sin 100t + C_2 \mathrm{e}^{-100t} \cos 100t = K\mathrm{e}^{-100t} \sin(100t + \theta)$，其中$K$ 和 $\theta$ 为待定系数。

（2）求非齐次方程的一个特解。

通过观察易知，非齐次方程的一个特解为

$$y = 1$$

（3）非齐次方程的通解为

$$y(t) = 1 + K\mathrm{e}^{-100t} \sin(100t + \theta)$$

（4）由初值定积分常数。

$\dfrac{\mathrm{d}y}{\mathrm{d}t} = -100K\mathrm{e}^{-100t} \sin(100t + \theta) + 100K\mathrm{e}^{-100t} \cos(100t + \theta)$，根据 $y(0) = 2$，$\left.\dfrac{\mathrm{d}y}{\mathrm{d}t}\right|_{t=0} = 0$ 可知

$$\begin{cases} 1 + K\sin\theta = 2 \\ -100K\sin\theta + 100K\cos\theta = 0 \end{cases} \quad \Rightarrow \quad K = \sqrt{2}, \theta = 45^\circ$$

因此初值问题的解为

$$y(t) = 1 + \sqrt{2}\,\mathrm{e}^{-100t} \sin(100t + 45^\circ)$$

## 参考文献

[1] 郑钧. 线性系统分析. 北京: 科学出版社，1978

[2] 王高雄，周之铭，朱思铭，王寿松. 常微分方程. 第 2 版. 北京: 高等教育出版社，1983

[3] 居余马，葛严麟. 高等数学. 第 Ⅱ 卷. 北京: 清华大学出版社，1996

[4] 清华大学数学科学系《微积分》编写组. 微积分. 第 Ⅲ 卷. 北京: 清华大学出版社，2004

# 附录D 复数和正弦量

本附录介绍复数的两种表示方法、基本运算规律以及正弦量的三要素。

## D1 复数及其运算

设 $A$ 为一复数，$a$ 和 $b$ 分别是它的实部和虚部，则复数 $A$ 的代数形式（又称直角坐标形式）为

$$A = a + \mathrm{j}b$$

上式中，$\mathrm{j} = \sqrt{-1}$ 为虚数单位（在数学中常用 $\mathrm{i}$ 为虚数单位，但由于在电路中 $\mathrm{i}$ 用于表示电流，因此改用 $\mathrm{j}$）。复数的实部和虚部分别用下列符号表示：

$$\mathrm{Re}\,(A) = a, \quad \mathrm{Im}\,(A) = b$$

$\mathrm{Re}$ 和 $\mathrm{Im}$[^6] 可以理解为一种算子，复数经过它们的运算后分别得到该复数的实部和虚部。

一个复数在复平面上可以用一条从原点 $O$ 指向 $A$ 对应坐标点的有向线段来表示，如图 D1.1 所示。

>图D1.1 复数的图形表示

这条有向线段的长度称为复数 $A$ 的模，记做 $|A|$，模总是取正值。有向线段与实轴正方向的夹角称为复数 $A$ 的辐角，记做 $\theta$。辐角可以用弧度表示，也可以用角度表示。由图 D1.1 可以看出，复数 $A$ 还可以表示为

$$A = |A|\,(\cos\theta + \mathrm{j}\sin\theta) \tag{D1.1}$$

根据欧拉（Euler）公式：

$$\mathrm{e}^{\mathrm{j}\theta} = \cos\theta + \mathrm{j}\sin\theta$$

式（D1.1）可以进一步写成

$$A = |A|\,\mathrm{e}^{\mathrm{j}\theta} \tag{D1.2}$$

式（D1.1）称为复数 $A$ 的三角形式，式（D1.2）称为复数 $A$ 的指数形式。指数形式还可以改写为极坐标形式：

$$A = |A|\,\angle\theta$$

复数的直角坐标形式和极坐标形式之间可以互相转换。由上面的分析过程可以看出，若 $A = a + \mathrm{j}b = |A|\,\angle\theta$，则

$$a = |A|\cos\theta, \quad b = |A|\sin\theta$$

[^6]: Re 是 real part 的头两个字母，Im 是 imaginary part 的头两个字母。

$$|A| = \sqrt{a^2 + b^2}, \quad \theta = \arctan\left(\frac{b}{a}\right)$$

下面介绍有关复数的运算。

**1. 相等**

若两个复数的实部和虚部分别相等，则这两个复数相等。设 $A_1 = a_1 + \mathrm{j}b_1$，$A_2 = a_2 + \mathrm{j}b_2$，若

$$a_1 = a_2, \quad b_1 = b_2$$

则

$$A_1 = A_2$$

类似地，当两个复数用极坐标形式表示时，若它们的模相等，辐角相等，则这两个复数相等。设 $A_1 = |A_1|\,\angle\theta_1$，$A_2 = |A_2|\,\angle\theta_2$，若

$$|A_1| = |A_2|, \quad \theta_1 = \theta_2$$

则

$$A_1 = A_2$$

**2. 加减运算**

两个复数或多个复数的加减运算采用直角坐标形式比较容易进行，只需将它们的实部和虚部分别相加减即可。

设 $A_1 = a_1 + \mathrm{j}b_1$，$A_2 = a_2 + \mathrm{j}b_2$，则

$$A_1 \pm A_2 = (a_1 \pm a_2) + \mathrm{j}(b_1 \pm b_2)$$

若复数采用极坐标形式表示，应首先转换为直角坐标形式再进行加减运算。复数的加减运算还可以用复平面上的图形来表示，如图 D1.2 所示。这种运算在复平面上是符合平行四边形法则的。图 D1.2(a) 和图 (c) 采用的是平行四边形画法，而图 D1.2(b) 和图 (d) 采用的是三角形画法。

>图D1.2 复数加减运算的图形表示

**3. 乘法运算**

若复数采用直角坐标形式，设 $A_1 = a_1 + \mathrm{j}b_1$，$A_2 = a_2 + \mathrm{j}b_2$，则

$$\begin{aligned} A_1 A_2 &= (a_1 + \mathrm{j}b_1)(a_2 + \mathrm{j}b_2) \\ &= (a_1 a_2 - b_1 b_2) + \mathrm{j}(a_1 b_2 + a_2 b_1) \end{aligned}$$

在运算过程中用到了 $\mathrm{j}^2 = -1$ 这一关系。

若复数采用极坐标形式，设 $A_1 = |A_1|\,\angle\theta_1$，$A_2 = |A_2|\,\angle\theta_2$，则

$$\begin{aligned} A_1 A_2 &= |A_1|\,\mathrm{e}^{\mathrm{j}\theta_1}\,|A_2|\,\mathrm{e}^{\mathrm{j}\theta_2} \\ &= |A_1|\,|A_2|\,\mathrm{e}^{\mathrm{j}(\theta_1 + \theta_2)} = |A_1|\,|A_2|\,\angle(\theta_1 + \theta_2) \end{aligned}$$

即复数相乘，其结果等于它们的模相乘，辐角相加。

**4. 除法运算**

若复数采用直角坐标形式，设 $A_1 = a_1 + \mathrm{j}b_1$，$A_2 = a_2 + \mathrm{j}b_2$，则

$$\begin{aligned} \frac{A_1}{A_2} &= \frac{a_1 + \mathrm{j}b_1}{a_2 + \mathrm{j}b_2} = \frac{(a_1 + \mathrm{j}b_1)(a_2 - \mathrm{j}b_2)}{(a_2 + \mathrm{j}b_2)(a_2 - \mathrm{j}b_2)} \\ &= \frac{(a_1 a_2 + b_1 b_2) + \mathrm{j}(a_2 b_1 - a_1 b_2)}{a_2^2 + b_2^2} \\ &= \frac{a_1 a_2 + b_1 b_2}{a_2^2 + b_2^2} + \mathrm{j}\frac{a_2 b_1 - a_1 b_2}{a_2^2 + b_2^2} \end{aligned}$$

在运算过程中，为了使分母有理化，必须把分子、分母同乘以分母的共轭复数 $A_2^*$，它与分母实部相等，虚部相反。

若复数采用极坐标形式，设 $A_1 = |A_1|\,\angle\theta_1$，$A_2 = |A_2|\,\angle\theta_2$，则

$$\frac{A_1}{A_2} = \frac{|A_1|\,\mathrm{e}^{\mathrm{j}\theta_1}}{|A_2|\,\mathrm{e}^{\mathrm{j}\theta_2}} = \frac{|A_1|}{|A_2|}\,\mathrm{e}^{\mathrm{j}(\theta_1 - \theta_2)} = \frac{|A_1|}{|A_2|}\,\angle(\theta_1 - \theta_2)$$

即复数相除，其结果等于它们的模相除，辐角相减。由此也可以看出：复数的乘除运算采用极坐标形式更简便一些。

## D2 正弦量的三要素

设一个正弦电流的表达式为

$$i = I_m \sin(\omega t + \psi_i)$$

用图形表示如图 D2.1 所示。其中 $I_m$、$\omega$ 和 $\psi_i$ 三个常数称为正弦量的三要素。

$I_m$ 称为正弦量的幅值。正弦量是一个等幅振荡的、正负交替变化的周期函数，正弦量的幅值就是它在一个周期内达到的最大值。

>图D2.1 正弦电流波形

$\omega t + \psi_i$ 称为正弦量的相位，也即是正弦量随时间变化的角度。该角度对时间的变化率就称为正弦量的角频率 $\omega$，即角频率等于相位对时间的导数，它与正弦量的周期 $T$、频率 $f$ 间的关系为

$$\omega = 2\pi f = \frac{2\pi}{T}$$

角频率 $\omega$ 的单位是 rad/s，频率的单位是 Hz，周期的单位是 s。

$\psi_i$ 称为正弦量的初相位，即 $t = 0$ 时刻正弦量的相位。初相位与计时零点的选择有关，还与正弦量的参考方向选择有关。对于一个单独的正弦量，初相位是允许任意指定的；但对于同一个电路中的相关的正弦量，它们只能相对于一个共同的计时零点来确定各自的初相位。初相位的取值区间一般取为 $|\psi_i| \leqslant 180^\circ$。

正弦量的三要素是正弦量之间进行比较和区分的依据。

当两个正弦量频率相同时，它们的相位关系是不随时间变化的。设 $u$、$i$ 是两个相同频率的正弦量：

$$i = I_m \sin(\omega t + \psi_i)$$

$$u = U_m \sin(\omega t + \psi_u)$$

它们的相位差为

$$(\omega t + \psi_i) - (\omega t + \psi_u) = \psi_i - \psi_u$$

从上式可以看出，同频率的正弦量的相位差就等于它们初相位的差，是一个与时间无关的常数。

当 $\psi_i > \psi_u$ 时，称电流领先电压；当 $\psi_i = \psi_u$ 时，称电流、电压同相；当 $\psi_i < \psi_u$ 时，称电流落后电压；当 $|\psi_i - \psi_u| = 180^\circ$ 时，称电流、电压反相。相位差的取值区间为 $|\psi_i - \psi_u| \leqslant 180^\circ$。

# 附录E 傅里叶级数

周期信号都可以用一个周期函数来表示：

$$f(t) = f(t + kT) \quad k = 0, 1, 2, \cdots$$

上式中，$T$ 称为周期函数的周期。如果周期函数 $f(t)$ 满足狄里赫利条件，那么它就可以展开成一个收敛的傅里叶级数，即

$$\begin{aligned} f(t) &= a_0 + a_1 \cos(\omega_1 t) + b_1 \sin(\omega_1 t) + a_2 \cos(2\omega_1 t) + b_2 \sin(2\omega_1 t) + \cdots \\ &\quad + a_k \cos(k\omega_1 t) + b_k \sin(k\omega_1 t) + \cdots \\ &= a_0 + \sum_{k=1}^{\infty} \left[a_k \cos(k\omega_1 t) + b_k \sin(k\omega_1 t)\right] \end{aligned} \tag{E1}$$

这里所说的狄里赫利条件是：

1. $f(t)$ 在一个周期内只有有限个不连续点；
2. $f(t)$ 在一个周期内只有有限个极值；
3. $f(t)$ 在一个周期内绝对可积，即 $\displaystyle \int_0^T |f(t)|\,\mathrm{d}t$ 存在。

工程上遇到的周期函数一般都满足狄里赫利条件。

利用三角函数的和差变换，上式还可以写成另一种形式：

$$\begin{aligned} f(t) &= a_0 + \sum_{k=1}^{\infty} \left[a_k \cos(k\omega_1 t) + b_k \sin(k\omega_1 t)\right] \\ &= a_0 + \sum_{k=1}^{\infty} c_k \sin(k\omega_1 t + \varphi_k) \end{aligned} \tag{E2}$$

其中：

$$\left.\begin{aligned} a_0 &= \frac{1}{T}\int_0^T f(t)\,\mathrm{d}t \\ a_k &= \frac{2}{T}\int_0^T f(t)\cos(k\omega_1 t)\,\mathrm{d}t = \frac{2}{T}\int_{-\frac{T}{2}}^{\frac{T}{2}} f(t)\cos(k\omega_1 t)\,\mathrm{d}t \quad k = 1, 2, \cdots \\ b_k &= \frac{2}{T}\int_0^T f(t)\sin(k\omega_1 t)\,\mathrm{d}t = \frac{2}{T}\int_{-\frac{T}{2}}^{\frac{T}{2}} f(t)\sin(k\omega_1 t)\,\mathrm{d}t \quad k = 1, 2, \cdots \end{aligned}\right\} \tag{E3}$$

式（E1）与式（E2）中相应系数间的关系为

$$c_k = \sqrt{a_k^2 + b_k^2}$$

$$\varphi_k = \arctan\left(\frac{a_k}{b_k}\right)$$

$$a_k = c_k \sin\varphi_k$$

$$b_k = c_k \cos\varphi_k$$

式（E2）中，$a_0$ 称为周期函数的恒定分量（或直流分量），$c_1 \sin(\omega_1 t + \varphi_1)$ 称为周期函数的基波分量，它的周期和频率与原周期函数的周期和频率相同。其他的频率成分依次称为 2 次谐波、3 次谐波……

并不是每一个周期信号中都包含所有的频率成分，某些周期信号因其自身的某种对称性，当它分解为傅里叶级数时，会不含有某些频率成分。

如果周期函数是奇函数，即

$$f(-t) = -f(t)$$

则根据式（E3），有

$$\begin{aligned} a_k &= \frac{2}{T}\int_{-\frac{T}{2}}^{\frac{T}{2}} f(t)\cos(k\omega_1 t)\,\mathrm{d}t \\ &= \frac{2}{T}\int_{-\frac{T}{2}}^{0} f(t)\cos(k\omega_1 t)\,\mathrm{d}t + \frac{2}{T}\int_0^{\frac{T}{2}} f(t)\cos(k\omega_1 t)\,\mathrm{d}t \\ &= \frac{2}{T}\int_{-\frac{T}{2}}^{0} f(-t)\cos(-k\omega_1 t)\,\mathrm{d}(-t) + \frac{2}{T}\int_0^{\frac{T}{2}} f(t)\cos(k\omega_1 t)\,\mathrm{d}t \\ &= -\frac{2}{T}\int_0^{\frac{T}{2}} f(t)\cos(k\omega_1 t)\,\mathrm{d}t + \frac{2}{T}\int_0^{\frac{T}{2}} f(t)\cos(k\omega_1 t)\,\mathrm{d}t \\ &= 0 \end{aligned}$$

因此，在这类周期函数的傅里叶级数中不含有余弦分量。

类似地，若周期函数为偶函数，即

$$f(-t) = f(t)$$

则根据式（E3）可以得出：$b_k = 0$，即傅里叶级数中不含有正弦分量。

若周期函数半波奇对称，即

$$f\left(t + \frac{T}{2}\right) = -f(t)$$

则根据式（E3）可以得出：$a_{2k} = 0$，$b_{2k} = 0$，即傅里叶级数中不含有偶次分量。

需要指出，由于函数的奇、偶对称性质与计时起点有关，因此系数 $a_k$、$b_k$（$k = 1, 2, \cdots$）也与计时起点有关。因此，适当选择计时起点有时会使函数的分解简化。

傅里叶级数是一个无穷三角级数，因此把一个周期性非正弦函数分解为傅里叶级数后，从理论上讲，必须取无穷多项才能准确地代表原函数。但在实际计算过程中只能取有限项，这就产生了误差。截取项数的多少，需视实际精度要求而定。

# 部分习题答案

1.1 （1）$u = -(t-kT) + 2\mathrm{V}$，$i = t - kT\mathrm{A}$，$T = 2\mathrm{s}$，$kT < t < (k+1)T$，$k = 0, 1, \cdots$；（2）$1\mathrm{V}$，$1\mathrm{A}$；

　　（3）$1.15\mathrm{V}$，$1.15\mathrm{A}$；（4）$p_{\text{发}} = (t-kT)^2 - 2(t-kT)\mathrm{W}$，其中 $kT < t < (k+1)T$，$k = 0, 1, \cdots$；

　　（5）$p_{\text{发}} = 0.67\mathrm{W}$

1.2 $0.45U$，$0.707U$

1.3 $0.9U$，$U$

2.1 （1）$u_2 = 5\mathrm{V}$，$u_5 = -4\mathrm{V}$，$i_2 = 1\mathrm{A}$，$i_4 = -1\mathrm{A}$，$i_5 = 1\mathrm{A}$；（2）$2\mathrm{W}$，$-5\mathrm{W}$，$6\mathrm{W}$，$1\mathrm{W}$，$-4\mathrm{W}$

2.2 $0\mathrm{V}$，$-6\mathrm{V}$，$-5.4\mathrm{V}$，$-5.3\mathrm{V}$，$-5\mathrm{V}$，$-4.8\mathrm{V}$，$-0.8\mathrm{V}$，$-0.5\mathrm{V}$，$-5.3\mathrm{V}$，$-2.3\mathrm{V}$

2.3 （a）$-U_S \dfrac{R_L}{R_L + R_S}$，$\dfrac{U_S}{R_L + R_S}$；（b）$-I_S \dfrac{R_S}{R_L + R_S}$，$I_S \dfrac{R_L R_S}{R_L + R_S}$

2.6 （a）$-5\mathrm{V}$；（b）$7\mathrm{V}$

2.7 （a）$-8\mathrm{A}$；（b）$0\mathrm{V}$；（c）$2\mathrm{A}$，$36\mathrm{V}$；（d）$-2\mathrm{A}$，$5\mathrm{V}$，$9\mathrm{V}$

2.8 （a）$6\mathrm{A}$，$0.2\mathrm{A}$，$-2\mathrm{A}$，$-1.625\mathrm{A}$，$-7.625\mathrm{A}$；（b）$-9\mathrm{A}$，$9\mathrm{V}$，$35\mathrm{V}$

2.9 $30\mathrm{A}$

2.10 $-0.1\mathrm{A}$，$-1.6\mathrm{V}$

2.12 $1\mathrm{A}$

2.13 $1.2\mathrm{V}$，$3.6\mathrm{V}$，$1.2\mathrm{V}$

2.14 $0.5\mathrm{V}$

2.15 $2\mathrm{V}$，$-0.5\mathrm{A}$

2.16 （a）$2.88\Omega$，（b）$2.3\Omega$，（c）$2.31\Omega$

2.17 （a）$8\Omega$，（b）$3.75\Omega$

2.18 （a）$21\Omega$，（b）$2.21\Omega$

2.21 $-0.1\mathrm{A}$

2.22 $U_S \dfrac{R_2 R_3 - R_1 R_4}{(R_1 + R_2)(R_3 + R_4)}$

2.23 $2\mathrm{V}$

2.24 （1）$U = 2\mathrm{V}$，$U_1 = 1\mathrm{V}$；（2）$4\mathrm{W}$

2.25 $9.6\Omega$，$5.4\mathrm{W}$

2.26 $3\Omega$

2.27 $3.2\mathrm{A}$

2.29 $0.5\sin(100t)\mathrm{mA}$

2.30 $U_S \dfrac{R_1 + R_2}{R_3 R_2}$

2.31 （1）$U_S\left(1 + \dfrac{R_1}{R_2}\right)$；（2）$\infty$

2.32 $2(u_2 - u_1)$

2.33 （1）$-\dfrac{3}{16} = -0.1875$；（2）$12\mathrm{k}\Omega$

2.34 $4(u_2 - u_1)$

2.36 （a）$\begin{bmatrix} \dfrac{1}{R_1} + \dfrac{1}{R_2} & \dfrac{1}{R_1} \\[6pt] \dfrac{1}{R_1} & \dfrac{1}{R_1} + \dfrac{1}{R_3} \end{bmatrix}$；（b）$\begin{bmatrix} \dfrac{1}{R_1} + \dfrac{1}{R_2} & -\dfrac{1}{R_2} \\[6pt] -\dfrac{1}{R_2} & \dfrac{1}{R_1} + \dfrac{1}{R_2} \end{bmatrix}$

2.37 （a）$\begin{bmatrix} -1 & -2 \\ 13 & 15 \end{bmatrix}\Omega$；（b）$\begin{bmatrix} 4 & -3 \\ 3 & -1 \end{bmatrix}\Omega$

2.38 （1）$\begin{bmatrix} 1 & 1\Omega \\ 0.25\mathrm{S} & 1.25 \end{bmatrix}$；（2）$6\mathrm{V}$，$3.5\mathrm{A}$

2.41 两输入 NAND 门 $P_{\max} = \dfrac{U_S^2}{R_L + 2R_{\mathrm{ON}}}$，两输入 NOR 门 $P_{\max} = \dfrac{U_S^2}{R_L + 0.5R_{\mathrm{ON}}}$

3.1 $-1.5\mathrm{A}$，$1\mathrm{A}$，$0.5\mathrm{A}$

3.2 $48\mathrm{W}$，$0$

3.3 $0.1\mathrm{A}$，$0.2\mathrm{A}$，$0.1\mathrm{A}$，$0.2\mathrm{A}$，$0.3\mathrm{A}$，$0.1\mathrm{A}$

3.4 $12\mathrm{A}$

3.5 $40\mathrm{W}$，$936\mathrm{W}$

3.6 $6\mathrm{V}$，$4\mathrm{V}$

3.7 $5\mathrm{A}$，$5\mathrm{A}$

3.8 $2\mathrm{A}$，$6\mathrm{V}$

3.9 $-(R_2 R_3 + R_3 R_4 + R_4 R_2)/(R_1 R_4)$

3.10 $10.45\mathrm{A}$，$3.17\mathrm{A}$，$-1.31\mathrm{A}$，$523\mathrm{W}$

3.11 $-1\mathrm{A}$，$-9\mathrm{A}$，$16\mathrm{W}$

3.12 $22\mathrm{A}$

3.13 $18\mathrm{V}$

3.14 $-0.9\mathrm{A}$

3.15 $5\mathrm{V}$

3.16 $1.2\mathrm{A}$

3.17 $7u_1 + 14u_2$

3.18 $2\mathrm{A}$

3.19 $468\mathrm{W}$

3.20 $3\Omega$

3.21 $3\mathrm{V}$

3.22 $3\mathrm{A}$，$2\mathrm{A}$

3.23 $-0.4\mathrm{V}$

3.24 $6\mathrm{V}$

3.25 $3.5\Omega$，$0.875\mathrm{W}$

3.26 $-22.5\mathrm{V}$

3.27 $3\mathrm{V}$

3.28 $10\Omega$，$14.4\mathrm{W}$

3.29 $4\mathrm{V}$

3.30 $0.4\mathrm{A}$

3.31 $0.2\mathrm{A}$

3.32 $\begin{bmatrix} R_1 + R_3 + R_2(1 + gR_1) & R_3 \\ R_3 & R_3 + R_4 \end{bmatrix}$，互易二端口

3.33 $\begin{bmatrix} G_1 & g_1 \\ g_2 & G_2 - g_1 \end{bmatrix}$，非互易二端口

3.34 $0.8\mathrm{A}$

3.35 $0.25\mathrm{A}$

3.36 $2.5\mathrm{A}$

4.1 $P_{\text{吸}} = 114\mathrm{W}$，$P_{\text{发}} = 124\mathrm{W}$

4.2 （1）$i = 1\mathrm{A}$ 时 $R_S = 5\Omega$，$R_D = 11\Omega$；（2）$i = 2\mathrm{A}$ 时 $R_S = 14\Omega$，$R_D = 38\Omega$

4.3 （1）$0.5\mathrm{V}$；（2）$-1\mathrm{V}$

4.4 $0.267\mathrm{mA}$

4.6 $U_c - \beta\dfrac{R_c}{R_b}U_b$

4.7 $2 + 0.1\sin(10^3 t)\mathrm{A}$

4.15 $1\mathrm{V} < u_{\mathrm{GS}} < 2.90\mathrm{V}$

4.17 （1）恒流区；（2）$0.38\mathrm{V}$

4.18 （2）$0.55$

5.1 （a）$0\mathrm{V}$，$4\mathrm{A}$，$16\mathrm{V}$；（b）$2\mathrm{A}$，$-20\mathrm{V}$；（c）$7.5\mathrm{V}$，$-1.5\mathrm{A}$；

　　（d）$6\mathrm{V}$，$6\mathrm{V}$，$0\mathrm{V}$，$-0.5\mathrm{A}$；（e）$3.5\mathrm{A}$，$-1.5\mathrm{A}$；（f）$4\mathrm{A}$，$6\mathrm{A}$，$-18\mathrm{A}$，$-12\mathrm{V}$

5.2 （a）$44.19\mathrm{V}$，$20.85\mathrm{A}$；（b）$0.73\mathrm{A}$，$-0.069\mathrm{A}$，$3.47\mathrm{V}$

5.3 （a）$2\mathrm{A}$，$80\mathrm{V}$，$-32\mathrm{kA/s}$，$0\mathrm{V/s}$；

　　（b）$0.6\mathrm{A}$，$24\mathrm{V}$，$0.6\mathrm{V/s}$，$-24\mathrm{A/s}$

5.4 （a）$\tau = \dfrac{L}{2R}$；（b）$\tau = R_2 C$；（c）$\tau = (2R - r)C$；（d）$\tau = 2RC$

5.5 $u_C(t) = 20\mathrm{e}^{-0.8t}\mathrm{V} \quad t \geqslant 0$

5.6 $i_L(t) = -0.6\mathrm{e}^{-100t}\mathrm{A} \quad t \geqslant 0$

5.7 （1）$2.23\mu\mathrm{s}$；（2）$0.16\mu\mathrm{s}$

5.8 $u_1(t) = -4\mathrm{e}^{-13.86t}\mathrm{V} \quad t \geqslant 0$

5.9 $i(t) = -1.5\mathrm{e}^{-50t} + 15\mathrm{e}^{-200t} - 30\mathrm{mA} \quad t \geqslant 0$

5.10 （1）$u_C(t) = 78.66\sin(314t - 8.13^\circ) + 11.1\mathrm{e}^{-400t} \quad t \geqslant 0$

　　$i(t) = 2.47\sin(314t + 81.87^\circ) - 0.445\mathrm{e}^{-400t}\mathrm{A} \quad t \geqslant 0$；

　　（2）$38.13^\circ$，$u_C(t) = 78.66\sin(314t)\mathrm{V} \quad t \geqslant 0$

5.11 $u_C(t) = 48(1 - \mathrm{e}^{-312.5t})\mathrm{V} \quad t \geqslant 0$

5.12 $i_L(t) = 20(1 - \mathrm{e}^{-20000t})\mathrm{A} \quad t \geqslant 0$，$i_1(t) = 40 + 20\mathrm{e}^{-20000t}\mathrm{A} \quad t \geqslant 0$

5.13 $u_{Czi}(t) = \mathrm{e}^{-8000t}\mathrm{V} \quad t \geqslant 0$，$u_{Czs}(t) = -1.25(1 - \mathrm{e}^{-8000t})\mathrm{V} \quad t \geqslant 0\,(U_S = 5\mathrm{V})$，

　　$u_{Czs}(t) = -2.5(1 - \mathrm{e}^{-8000t})\mathrm{V} \quad t \geqslant 0\,(U_S = 10\mathrm{V})$，

　　$u_C(t) = -1.25 + 2.25\mathrm{e}^{-8000t}\mathrm{V} \quad t \geqslant 0\,(U_S = 5\mathrm{V})$，

　　$u_C(t) = -2.5 + 3.5\mathrm{e}^{-8000t}\mathrm{V} \quad t \geqslant 0\,(U_S = 10\mathrm{V})$

5.14 $i_L(t) = 0.889(1 - \mathrm{e}^{-225t})\varepsilon(t)\mathrm{A}$

5.15 $u_C(t) = 2(1 - \mathrm{e}^{-t})\varepsilon(t) - 3(1 - \mathrm{e}^{-(t-3)})\varepsilon(t-3) + (1 - \mathrm{e}^{-(t-5)})\varepsilon(t-5)\mathrm{V}$

$$= \begin{cases} 2(1-\mathrm{e}^{-t})\mathrm{V} & 0 < t \leqslant 3 \\ -1 + 58.26\mathrm{e}^{-t}\mathrm{V} & 3 \leqslant t \leqslant 5 \\ -90.15\mathrm{e}^{-t}\mathrm{V} & t \geqslant 5 \end{cases}$$

5.16 $u_o(t) = -10(1 - \mathrm{e}^{-10t})\varepsilon(t)\mathrm{V}$

5.17 $i_1(t) = \left[-1 + 4.47\sin(1000t + 3.43^\circ) - 1.27\mathrm{e}^{-2000t}\right]\varepsilon(t)\mathrm{A}$

　　$i_2(t) = \left[1 + 4.47\sin(1000t + 3.43^\circ) - 1.27\mathrm{e}^{-2000t}\right]\varepsilon(t)\mathrm{A}$

5.18 $u_C(t) = \begin{cases} 2 + 8\mathrm{e}^{-t}\mathrm{V} & 0 < t \leqslant 1 \\ 4 + 0.94\mathrm{e}^{-2(t-1)}\mathrm{V} & t \geqslant 1 \end{cases}$，$i_C(t) = \begin{cases} -2\mathrm{e}^{-t}\mathrm{V} & 0 < t < 1 \\ -0.47\mathrm{e}^{-2(t-1)}\mathrm{V} & t > 1 \end{cases}$

5.21 $i_L(t) = 1.6\mathrm{e}^{-16t}\varepsilon(t)\mathrm{A}$

5.22 $u_C(t) = 8\mathrm{e}^{-t}\varepsilon(t) + 4\varepsilon(-t)\mathrm{V}$，$i_C(t) = 0.8\delta(t) - 1.6\mathrm{e}^{-t}\varepsilon(t)\mathrm{A}$

5.23 $i_L(t) = (2.5 + 37.5\mathrm{e}^{-20t})\varepsilon(t)\mathrm{A}$

5.24 $u_{C2}(t) = \left[U_S - \dfrac{C_2 U_S}{C_1 + C_2}\mathrm{e}^{-\frac{t}{R(C_1 + C_2)}}\right]\varepsilon(t)$，$i(t) = \left[\dfrac{C_2 U_S}{(C_1 + C_2)R}\mathrm{e}^{-\frac{t}{R(C_1 + C_2)}}\right]\varepsilon(t)$

　　$i_{C1}(t) = -\dfrac{C_1 C_2 U_S}{C_1 + C_2}\delta(t) + \dfrac{C_1 C_2 U_S}{(C_1 + C_2)^2 R}\mathrm{e}^{-\frac{t}{R(C_1 + C_2)}}\varepsilon(t)$

　　$i_{C2}(t) = \dfrac{C_1 C_2 U_S}{C_1 + C_2}\delta(t) + \dfrac{C_2^2 U_S}{(C_1 + C_2)^2 R}\mathrm{e}^{-\frac{t}{R(C_1 + C_2)}}\varepsilon(t)$

5.25 $\tau = \dfrac{L_1 + L_2}{R_1 + R_2}$，

　　$i_1(t) = \left[\dfrac{U_S}{R_1 + R_2} + \left(\dfrac{L_1 U_S}{(L_1 + L_2)R_1} - \dfrac{U_S}{R_1 + R_2}\right)\mathrm{e}^{-\frac{t}{\tau}}\right]\varepsilon(t) + \dfrac{U_S}{R_1}\varepsilon(-t)$，

　　$i_2(t) = \left[\dfrac{U_S}{R_1 + R_2} + \left(\dfrac{L_1 U_S}{(L_1 + L_2)R_1} - \dfrac{U_S}{R_1 + R_2}\right)\mathrm{e}^{-\frac{t}{\tau}}\right]\varepsilon(t)$

5.26 $u_C(t) = 27.8\mathrm{e}^{-t} - 23.8\mathrm{e}^{-10t}\mathrm{V} \quad t \geqslant 0$

5.27 $i_L(t) = \begin{cases} 1 + \mathrm{e}^{-20t}\mathrm{A} & 0 < t \leqslant 1\mathrm{s} \\ \mathrm{e}^{-20(t-1)} + \mathrm{e}^{-20t}\mathrm{A} & t \geqslant 1\mathrm{s} \end{cases}$

5.28 （a）$\delta = 0.5$，$\omega = 3.12\mathrm{rad/s}$；（b）$\delta = 50$，$\omega = 1786\mathrm{rad/s}$

5.29 $u_C(t) = 15 + 18\mathrm{e}^{-6t} - 25\mathrm{e}^{-5t}\mathrm{V} \quad t \geqslant 0$，$i_2(t) = 1.5 + 4.5\mathrm{e}^{-6t} - 5\mathrm{e}^{-5t}\mathrm{A} \quad t \geqslant 0$

5.30 $50\Omega$，$58.8\mathrm{mH}$，$100\mu\mathrm{F}$，$i(t) = 5.88\mathrm{e}^{-100t}\sin 400t\mathrm{mA} \quad t \geqslant 0$

5.31 （1）$i_L(t) = 2.05\mathrm{e}^{-1.33t}\sin(1.49t + 29.3^\circ) - 1\mathrm{A} \quad t \geqslant 0$

　　（2）$i_L(t) = (1 + 2.67t)\mathrm{e}^{-1.33t} - 1\mathrm{A} \quad t \geqslant 0$

　　（3）$i_L(t) = 2.5\mathrm{e}^{-0.667t} - 1.5\mathrm{e}^{-2t} - 1\mathrm{A} \quad t \geqslant 0$

5.32 $u_C(t) = 20\mathrm{e}^{-2t} - 16\mathrm{e}^{-3t}\mathrm{V} \quad t \geqslant 0$

5.33 $u_C(t) = \begin{cases} 1.33 + 6\mathrm{e}^{-2t} - 3.33\mathrm{e}^{-3t}\mathrm{V} & 0 < t \leqslant 1\mathrm{s} \\ 35.56\mathrm{e}^{-2t} - 56.89\mathrm{e}^{-3t}\mathrm{V} & t \geqslant 1\mathrm{s} \end{cases}$

5.34 $\begin{bmatrix} \dot{u}_C \\ \dot{i}_L \end{bmatrix} = \begin{bmatrix} -0.25 & -1 \\ 31 & -6 \end{bmatrix}\begin{bmatrix} u_C \\ i_L \end{bmatrix} + \begin{bmatrix} 2.5 \\ -300 \end{bmatrix}$

5.35 $\begin{bmatrix} \dfrac{\mathrm{d}u_C}{\mathrm{d}t} \\[6pt] \dfrac{\mathrm{d}i_L}{\mathrm{d}t} \end{bmatrix} = \begin{bmatrix} -0.75 & 0 \\ 0 & -0.75 \end{bmatrix}\begin{bmatrix} u_C \\ i_L \end{bmatrix} + \begin{bmatrix} 0.5 \\ 0.25 \end{bmatrix}i_S$，

　　$\begin{bmatrix} u_1 \\ u_2 \\ u_3 \end{bmatrix} = \begin{bmatrix} 0.5 & -0.5 \\ 0 & -1.5 \\ -0.5 & -0.5 \end{bmatrix}\begin{bmatrix} u_C \\ i_L \end{bmatrix} + \begin{bmatrix} 0.5 \\ 0.5 \\ 0.5 \end{bmatrix}i_S$

6.3 $Z = 10 + \mathrm{j}31.4\Omega$，$Y = 9.2 \times 10^{-3} - 0.029\mathrm{S}$，$\cos\varphi = 0.30$（滞后）

6.4 （a）$4.47 + \mathrm{j}9.29\Omega$；（b）$\mathrm{j}1.5\Omega$；（c）$7 + \mathrm{j}4\Omega$

6.5 （1）$60\mathrm{V}$ 或 $30\mathrm{V}$；（2）$5\mathrm{V}$ 或 $11.76\mathrm{V}$，$30\mathrm{V}$ 或 $35.28\mathrm{V}$，$5.65\mathrm{V}$ 或 $13.23\mathrm{V}$

6.6 $\omega L = \dfrac{1}{\omega C} = R$

6.7 $2\mathrm{V}$

6.8 $i(t) = -1.828\mathrm{e}^{-10t}\mathrm{A} \quad t \geqslant 0$

6.9 $14\Omega$，$48\Omega$

6.10 （1）$f_0 = 53.08\mathrm{Hz}$ 时 $I_{\max} = 25\mathrm{A}$；（2）$23.96\mathrm{A}$，$\cos\varphi = 0.96$（超前），$2300\mathrm{W}$，$-670.6\mathrm{var}$，$2396\mathrm{VA}$，$(2300 - \mathrm{j}670.6)\mathrm{VA}$

6.11 $12\mathrm{A}$

6.12 （a）$\omega_1 = \dfrac{1}{\sqrt{L_1 C}}$，$\omega_2 = \sqrt{\dfrac{L_1 + L_2}{L_1 L_2 C}}$；（b）$\omega_1 = \dfrac{1}{\sqrt{LC_1}}$，$\omega_2 = \sqrt{\dfrac{1}{(C_1 + C_2)L}}$；

　　（c）$\omega_1 = \dfrac{1}{\sqrt{LC_1}}$，$\omega_2 = \sqrt{\dfrac{C_1 + C_2}{C_1 C_2 L}}$；（d）$\omega_1 = \dfrac{1}{\sqrt{L_2 C}}$，$\omega_2 = \sqrt{\dfrac{1}{(L_1 + L_2)C}}$

6.13 $8\Omega$，$4\mathrm{mH}$

6.14 $-\mathrm{j}1\mathrm{A}$

6.16 （a）、（b）、（c）电路均为 $(L^2 - M^2)/L$

6.18 （a）$30 + \mathrm{j}10\Omega$；（b）$1.2 + \mathrm{j}8.4\Omega$

6.19 $i(t) = 20\sin(20000t - 161^\circ)\mathrm{mA}$

6.20 （1）$0.496\mathrm{H}$；（2）$0.992$

6.21 $1\Omega$，$3\Omega$，$9\Omega$，$3\Omega$，$3\Omega$

6.22 $-9.6\Omega$，$15\Omega$

6.23 $217.1\mathrm{V}$，$11.55\Omega$，$23.1\Omega$

6.24 $7.5\Omega$，$12.99\Omega$，$-12.99\Omega$

6.25 $2\Omega$，$-1\Omega$

6.26 $120\mathrm{V}$，$0$

6.27 $7.5 - \mathrm{j}6.67\Omega$，$46.78\mathrm{W}$

6.28 （1）$1:2$；（2）$12.65\mathrm{V}$；（3）$15.8\mathrm{V}$

6.29 $7.143\Omega$，$1000\mathrm{W}$

6.30 电流源发出 $692.8\mathrm{VA}$，电压源发出 $-\mathrm{j}200\mathrm{VA}$

6.31 $1174.6\mu\mathrm{F}$，$\cos\varphi = 0.87$（滞后）

6.33 $6.47\angle -80.6^\circ\mathrm{A}$

6.34 （1）$5809\mathrm{W}$；（2）$2060\mathrm{W}$，$3733\mathrm{W}$

6.35 $38.52\angle -151.63^\circ\mathrm{A}$

6.36 $29.53 - \mathrm{j}32.45\Omega$

6.37 $24.13\angle -60^\circ\Omega$

6.39 $8.28\mathrm{V}$，$1.87\mathrm{A}$，$11.9\mathrm{W}$

6.41 $11.03\mathrm{A}$，$1187\mathrm{W}$

6.42 （1）$30\mathrm{V}$，$0.5 + 0.6\sin(\omega t - 90^\circ) + 0.4\sin(2\omega t - 45^\circ)\mathrm{A}$；（2）$15\mathrm{W}$

6.43 $-6 + 5.56\sin(2t + 11.3^\circ)\mathrm{A}$，$72\mathrm{W}$，$46.3\mathrm{W}$

6.44 （1）$10\Omega$，$4\mathrm{H}$，$33.3\mu\mathrm{F}$；（2）$1 + 0.5\sin(100t + 45^\circ)\mathrm{A}$

# 索引

$2b$ 法　39

$3\mathrm{dB}$ 频率　297

DC/DC 变换　220

EWB　44

$G$ 参数　69

$H$ 参数　77

KCL　37

KVL　38

$R$ 参数　72

Spice　44

$S$ 参数　78

$T$ 参数　75

$T$ 接电阻　74

$Y$ 参数　282

$Y$ 接电阻　47

$Z$ 参数　282

$\Delta$ 接电阻　47

$\Pi$ 接电阻　74

## B

半波整流　177

半功率频率　294

饱和电压　57

倍频　182

比例性质　116

变比　323

标准正弦形式　272

并联　45

并联限幅　178

并联谐振　301

病态电路　50，52

波形　12

不对称三相电路　344

不控全波整流　223

不控整流　177

## C

参考方向　5，6

参考节点　36，101

超节点　38

超网孔　114

充气二极管　156

冲激函数的强度　241

抽单相　340

抽象观点　11

抽样信号　13

初始条件，初始值　197

储能元件　192

传播延迟　209

串联　45

串联反接　316

串联顺接　316

串联限幅　177

串联谐振　301

磁耦合　312

## D

带宽　298

带通滤波器　289

带阻滤波器　289

戴维南等效电路　127

戴维南等效电阻　127

戴维南定理　127

单调谐滤波器　307

单位冲激函数　240

单位冲激响应　242

单位电流法，单位电压法　123

单位阶跃函数　238

单位阶跃响应　239

单位脉冲函数　241

单相等效电路　340

单向开关　176

导纳　280

导通　176

等效观点　12

低通滤波器　289

电导　27，281

电动势　6

电感　8，190

电感器　190

电工　1

电工程　1

电抗　280

电抗频率特性　302

电流　4

电流频率特性　290

电流谐振　302

电路　1

电路分析　4

电路理论　4

电路设计　4

电路图　11

电路原理　4

电路综合　4

电纳　281

电气对称二端口　71

电气工程　1

电气元件　1

电桥　43

电桥平衡　46

电容　8，187

电容器　187

电位　6

电压　5

电压比较器　64

电压跟随器　61

电压频率特性　290

电压谐振　301

电源等效变换　54

电子管　33

电子设计自动化　44

电阻　8，27，280

电阻电路　21

电阻器　29

电阻区　35

叠加定理　118

叠加性质　116

动态电路　21，192

动态电阻　171

动态元件　192

独立电流源　31

独立电压源　31

独立电源，独立源　31

端口　7

端钮，端子　7

端线　337

短路　28

短路电流　131，135

对称二端口　71

对称三相电路　339

对称三相电源　337

对称三相负载　339

对偶　146

对偶电路　146

对偶原理　148

## E

二端口的并联　81

二端口的串联　82

二端口的级联　80

二端口网络　8

二端网络　8

二极管　29，156

二阶动态电路，二阶电路　224

## F

反馈　59

反相比例放大器　61

反相加法器　62

反相器　86，87

反相输入端　56

反向饱和区　58

反向工程　78

反映阻抗　321

方均根　18

放大器　173

非　84

非关联参考方向　8

非时变电路　21

非时变元件　21

非线性电路　21，158

非线性元件　21

非周期信号　12

分贝　296

分布参数电路　23

分布参数模型　23

分段线性模型　162

分立元件　31

幅频特性　290

负电阻　63

负反馈　59

负序　337

负载，负荷　21

复功率　332

副边线圈，副边　320

## G

感抗　278

感纳　278

感性　280

高通滤波器　289

工程近似观点　12

工作点　161

功率表　329

功率因数　330

功率因数角　330

共源放大电路　176

关断　176

关联参考方向　8

广义节点　38

广义网孔　114

过渡过程　196

过阻尼　226

## H

恒定分量　349

恒流区　35

互电导　103

互电阻　111

互感　313

互易定理　140

互易二端口　71

缓冲器　86，88

换路　197

换路定律　198

回路　37

回路电流　109

回路电流法　110

回转器　287

混频　182

火线　337

或　84

或非门　86，89

或门　86，90

## J

积分电路　213

基本量　4

基本模型　9

基波分量　349

基尔霍夫电流定律　37

基尔霍夫电压定律　38

激励　21

集成电路　31

集总参数电路，集中参数电路　24

集总参数模型，集中参数模型　24

记忆元件　20

加流求压　49

加压求流　49

假设—检验　163

减法器　63

交流　14，268

交流电桥　286

接线端　7

节点　36

节点电压　36

节点电压法　101

结构对称二端口　71

截止　176

截止频率　294，298

截止区　35

金属氧化物半导体场效应晶体管（MOSFET）　34

晶体管　33

静态电路　21

静态电阻　171

矩阵指数　257

卷积积分　248

绝对平均值　14

## K

开关-电流源模型　36

开关-电阻-电容模型　190

开关-电阻模型　36

开环放大倍数　57

开路　29

开路电压　127

开通　176

可加性　21，116

空心变压器　320

跨导　176

## L

离散信号　13

理想变压器　323

理想导线　28

理想二极管　165

理想运算放大器　60

理想直流　14

理想直流独立电流源　32

理想直流独立电压源　31

立体电路　37

连续信号　13

临界阻尼　227

零输入线性　235

零输入响应　234

零线　338

零状态线性　236

零状态响应　235

流控电流源（CCCS）　33

流控电压源（CCVS）　33

漏极　35

滤波器　289

## M

模拟滤波器　289

模拟系统，模拟电路　83

模拟信号　13

## N

奈培　297

逆问题　4

逆序　337

诺顿定理　135

## O

欧姆定律　8，27，274，280

耦合系数　315

## P

偏置电压　169

频率响应　288

频域　271

品质因数　307，308

平衡电桥　46

平均功率　17，329

平均值　13

平面电路　37

## Q

齐次性　21，116

齐纳二极管　180

齐性定理　122

箝位　177

欠阻尼　227

强制响应，强制分量　202

桥式电路　43

去耦等效　318

全波整流　326

全耦合　315

全耦合变压器　323

全通滤波器　298

全响应　202

确定性信号　12

## R

容抗　276

容纳　276

容性　280

入端电导　70

入端电阻　73

## S

三极管　33

三相三线制　340

三相四线制　340

三要素法　206

筛分性质　242

栅极　35

上 $3\mathrm{dB}$ 频率　298

上截止频率　298

时变电路　21

时变元件　21

时不变电路　21

时不变元件　21

时间常数　202，204

时间域　271

时序逻辑电路　87

视在功率　330

受控电源，受控源　33

输出电阻　57

输出端　56

输出方程　252

输入电阻　57

数字滤波器　289

数字系统、数字电路　83

数字信号　13

衰减系数　227

顺序　337

瞬时功率　16

随机信号　12

隧道二极管　156

## T

特勒根定理　138

特征方程　201，225，257

替代定理　124

通频带　294，298，310

通用谐振频率特性　309

同名端　313

同相比例放大器　62

同相输入端　56

图解法　160

拓扑结构　37

## W

网孔，网格　37

网孔电流法　111

网络　7

网络函数　293

微分电路　213，295

稳态响应　238

稳压二极管　180

无功功率　330

无记忆元件　20

无损元件　330

无源电路　22

无源滤波器　289

无源元件　22

无阻尼　229

无阻尼振荡角频率　227

## X

系统　7

下 $3\mathrm{dB}$ 频率　298

下截止频率　298

限幅　177

线电流　338

线电压　338

线性电路　21

线性区　57

线性元件　21

相电流　338

相电压　338

相量　271

相频特性　290

相序　337

响应　21

小信号　168

小信号电路　170

谐波　349

谐波分析法　352

谐振　301

谐振电路　300

谐振频率　301

信号　12

虚短　61

虚断　61

虚拟回路　39

旋转因子　271

## Y

压控电流源（VCCS）　33

压控电压源（VCVC）　33

严格递增电阻　159

一端口网络　8

一阶动态电路，一阶电路　200

引入阻抗　321

有功功率　329

有效值　18

有源电路　22

有源滤波器　289

有源元件　22

有阻尼衰减振荡角频率　227

与　84

与非门　86，88

与门　86，89

原边线圈，原边　320

源　21

源极（S）　35

运算放大器　55

## Z

暂态响应　238

占空比　14

真值表　85

整流　177

正反馈　59

正方向　5

正问题　4

正弦交流　14

正弦量　269

正向饱和区　58

正序　337

支路　36

支路电流　36

支路电流法　100

支路电压　36

支路量　36

直觉法　206，230

直流　14

直流分量　349

直流斩波　220

滞回比较器　66

中点　337

中点位移　345

中点位移电压　345

中间抽头变压器　326

中线　338

中心频率　298

周期　13

周期信号　12

转移电导　34，70

转移电流比　34

转移电压比　33

转移电阻　33，73

状态变量　251

状态方程　251

自电导　103

自电阻　110

自由响应，自由分量　202

阻抗　279

阻抗角　205，279

阻抗频率特性　290

组合逻辑电路　87

最大功率传输　54，334
