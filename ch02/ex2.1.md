# 例2.1

式(2.1)の近似
<div align="center">
  <img src=
"https://render.githubusercontent.com/render/math?math=%5Cdisplaystyle+%5Cphi%5Csimeq%5Chat%7B%5Cphi%7D%3D%5Cpsi%2B%5Csum_%7Bm%3D1%7D%5EM+a_mN_m" 
alt="\phi\simeq\hat{\phi}=\psi+\sum_{m=1}^M a_mN_m">
</div>
を6項まで($M=6$)で考える．板の境界で変位$u$が0になることから，自明な関数$\psi=0$と，試験関数の集合$N_{lm}=\{\sin l\pi x\cdot\sin m\pi y;l,m=1,2,\cdots\}$を選択出来る．これより
<div align="center">
  <img src=
"https://render.githubusercontent.com/render/math?math=%5Cdisplaystyle+%5Chat%7Bu%7D%3D%5Csum_%7B%5Csubstack%7Bl%2Cm%3D1%5C%5Cl%2Bm%5Cle4%7D%7D%5E3+a_%7Blm%7D%5Csin+l%5Cpi+x%5Csin+m%5Cpi+y" 
alt="\hat{u}=\sum_{\substack{l,m=1\\l+m\le4}}^3 a_{lm}\sin l\pi x\sin m\pi y">
</div>
重み付き残差法を考えると，$W_{l'm'}$を重み関数として
<div align="center">
  <img src=
"https://render.githubusercontent.com/render/math?math=%5Cdisplaystyle+%5Cint_%5COmega+%28u-%5Chat%7Bu%7D%29W_%7Bl%27m%27%7Dd%5COmega%3D0" 
alt="\int_\Omega (u-\hat{u})W_{l'm'}d\Omega=0">
</div>
Galerkin法では$W_{l'm'}=N_{l'm'}$とするので
$$
\int_\Omega(u-\hat{u})\sin l'\pi x\sin m'\pi yd\Omega=0 \\
\int_\Omega \hat{u}\sin l'\pi x\sin m'\pi yd\Omega=\int_\Omega u\sin l'\pi x\sin m'\pi yd\Omega \\
\int_\Omega \sum_{\substack{l,m=1\\l+m\le4}}^3 a_{lm}\sin l\pi x\sin m\pi y\cdot\sin l'\pi x\sin m'\pi yd\Omega=\int_\Omega u\sin l'\pi x\sin m'\pi yd\Omega \\
$$
3角関数の直交性より，左辺を展開した各項が0とならないのは$l'=l$かつ$m'=m$のときに限る．つまり
$$
\int_\Omega a_{11}\sin^2\pi x\sin^2 \pi yd\Omega=\int_\Omega u\sin\pi x\sin\pi yd\Omega~~(l'=m'=1) \\
\int_\Omega a_{12}\sin^2\pi x\sin^2 2\pi yd\Omega=\int_\Omega u\sin\pi x\sin 2\pi yd\Omega~~(l'=1,m'=2) \\
\vdots
$$
このとき，$(l,m)=(1,1),(1,2),(2,1),(1,3),(2,2),(3,1)$に対し
$$
\int_\Omega \sin^2l\pi x\sin^2m \pi yd\Omega=\frac{1}{4}
$$
であるので，下記のように一般的に表せる．
$$
\int_\Omega a_{lm}\sin^2l\pi x\sin^2m \pi yd\Omega=\int_\Omega u\sin l\pi x\sin m\pi yd\Omega \\
\frac{1}{4}a_{lm}=\int_0^1\int_0^1 u\sin l\pi x\sin m\pi ydxdy \\
\therefore a_{lm}=4\int_0^1\int_0^1 u\sin l\pi x\sin m\pi ydxdy
$$

---

以下では，2次元の台形公式により$a_{lm}$を求める．例えば，$a_{22}$の場合
$$
\int_{0}^1\left(\int_0^1 u(x,y)\sin2\pi xdx\right)\sin2\pi ydy
$$
を計算するが，これは
$$
I'(y)=\int_0^1 u(x,y)\sin2\pi xdx \\
I=\int_0^1 I'(y)\sin 2\pi ydy
$$
と$x,y$の積分を別々に考えればよい．

まず$x$の積分についてのみ考え，$I'(y)$を求める．$y=0,1$では，$u=0$より明らかに$I'(0)=I'(1)=0$であるので，$y=\frac{1}{4},\frac{1}{2},\frac{3}{4}$について1次元の台形公式を用いて計算する．$y=\frac{1}{4}$において
$$
\begin{eqnarray}
I'\left(\frac{1}{4}\right)&=&\frac{1}{4}\times\left[\frac{1}{2}\left\{u\left(0,\frac{1}{4}\right)\sin(2\pi\cdot0)+u\left(1,\frac{1}{4}\right)\sin(2\pi\cdot1)\right\}\right. \\
&&+\left.\left\{u\left(\frac{1}{4},\frac{1}{4}\right)\sin(2\pi\cdot\frac{1}{4})+u\left(\frac{1}{2},\frac{1}{4}\right)\sin(2\pi\cdot\frac{1}{2})+u\left(\frac{3}{4},\frac{1}{4}\right)\sin(2\pi\cdot\frac{3}{4})\right\}\right] \\
&=&\frac{1}{4}\times\left[\frac{1}{2}\{0+0\}+\left\{\frac{1}{2}\cdot1+\frac{3}{4}\cdot0+\frac{1}{4}\cdot(-1)\right\}\right] \\
&=&\frac{1}{4}\times\frac{1}{4}=\frac{1}{16}
\end{eqnarray}
$$
ここで，式はじめの$\frac{1}{4}$は刻み幅，$\frac{1}{2}$の掛かっている項は端点での値，その他の項は中間の点での値である．同様に，$y=\frac{1}{2}$において
$$
\begin{eqnarray}
I'\left(\frac{1}{2}\right)&=&\frac{1}{4}\times\left[\frac{1}{2}\{0+0\}+\left\{1\cdot1+\frac{7}{4}\cdot0+\frac{1}{2}\cdot(-1)\right\}\right] \\
&=&\frac{1}{4}\times\frac{1}{2}=\frac{1}{8}
\end{eqnarray}
$$
$y=\frac{3}{4}$において
$$
\begin{eqnarray}
I'\left(\frac{3}{4}\right)&=&\frac{1}{4}\times\left[\frac{1}{2}\{0+0\}+\left\{\frac{3}{4}\cdot1+\frac{5}{4}\cdot0+\frac{1}{4}\cdot(-1)\right\}\right] \\
&=&\frac{1}{4}\times\frac{1}{2}=\frac{1}{8}
\end{eqnarray}
$$
次に$y$の積分について考える．1次元の台形公式を用いると
$$
\begin{eqnarray}
I&=&\frac{1}{4}\times\left[\frac{1}{2}\left\{I'(0)\sin(2\pi\cdot0)+I'(1)\sin(2\pi\cdot1)\right\}\right. \\
&&+\left.\left\{I'\left(\frac{1}{4}\right)\sin(2\pi\cdot\frac{1}{4})+I'\left(\frac{1}{2}\right)\sin(2\pi\cdot\frac{1}{2})+I'\left(\frac{3}{4}\right)\sin(2\pi\cdot\frac{3}{4})\right\}\right] \\
&=&\frac{1}{4}\times\left[\frac{1}{2}\{0+0\}+\left\{\frac{1}{16}\cdot1+\frac{1}{8}\cdot0+\frac{1}{8}\cdot(-1)\right\}\right] \\
&=&\frac{1}{4}\times\left(-\frac{1}{16}\right)
\end{eqnarray}
$$
したがって
$$
a_{22}=4\int_0^1\int_0^1 u\sin 2\pi x\sin 2\pi ydxdy=4I=-\frac{1}{16}=-0.0625\approx-0.063
$$
と求められる．

---

その他の係数についても計算してみよう．例えば$a_{12}$の場合
$$
I'(0)=I'(1)=0 \\
I'\left(\frac{1}{4}\right)=\frac{3+3\sqrt2}{16\sqrt2},I'\left(\frac{1}{2}\right)=\frac{6+7\sqrt2}{16\sqrt2},I'\left(\frac{1}{4}\right)=\frac{4+5\sqrt2}{16\sqrt2}
$$
であるので
$$
\begin{eqnarray}
I&=&\frac{1}{4}\times\left[\frac{1}{2}\left\{I'(0)\sin(2\pi\cdot0)+I'(1)\sin(2\pi\cdot1)\right\}\right. \\
&&+\left.\left\{I'\left(\frac{1}{4}\right)\sin(2\pi\cdot\frac{1}{4})+I'\left(\frac{1}{2}\right)\sin(2\pi\cdot\frac{1}{2})+I'\left(\frac{3}{4}\right)\sin(2\pi\cdot\frac{3}{4})\right\}\right] \\
&=&\frac{1}{4}\times\left[\frac{1}{2}\{0+0\}+\left\{\frac{3+3\sqrt2}{16\sqrt2}\cdot1+\frac{6+7\sqrt2}{16\sqrt2}\cdot0+\frac{4+5\sqrt2}{16\sqrt2}\cdot(-1)\right\}\right] \\
&=&\frac{1}{4}\times\frac{-1-2\sqrt2}{16\sqrt2}
\end{eqnarray}
$$
これより
$$
a_{12}=4I=\frac{-1-2\sqrt2}{16\sqrt2}\approx-0.169
$$
例えば$a_{11}$の場合，各$I'(y)$の値は$a_{12}$の場合と同じであるので
$$
\begin{eqnarray}
I&=&\frac{1}{4}\times\left[\frac{1}{2}\left\{I'(0)\sin(\pi\cdot0)+I'(1)\sin(\pi\cdot1)\right\}\right. \\
&&+\left.\left\{I'\left(\frac{1}{4}\right)\sin(\pi\cdot\frac{1}{4})+I'\left(\frac{1}{2}\right)\sin(\pi\cdot\frac{1}{2})+I'\left(\frac{3}{4}\right)\sin(\pi\cdot\frac{3}{4})\right\}\right] \\
&=&\frac{1}{4}\times\left[\frac{1}{2}\{0+0\}+\left\{\frac{3+3\sqrt2}{16\sqrt2}\cdot\frac{1}{\sqrt2}+\frac{6+7\sqrt2}{16\sqrt2}\cdot1+\frac{4+5\sqrt2}{16\sqrt2}\cdot\frac{1}{\sqrt2}\right\}\right] \\
&=&\frac{1}{4}\times\frac{21+14\sqrt2}{32}
\end{eqnarray}
$$
これより
$$
a_{11}=4I=\frac{21+14\sqrt2}{32}\approx1.275
$$
