## Lien avec la transformée de Laplace
$\newcommand{\R}{\mathbb{R}}$
$\newcommand{\Q}{\mathbb{Q}}$
$\newcommand{\N}{\mathbb{N}}$
$\newcommand{\C}{\mathbb{C}}$
$\newcommand{\Z}{\mathbb{Z}}$



::::{prf:proposition}
Soit $x(t)$ un signal causal, et $X(z)$ la transformée
en Z du signal échantillonné  avec une période $T$ : 

$$X(z)=\sum_{n=0}^{+\infty} x(nT)z^{-n}.$$

Alors, sous réserve de décroissance suffisante de $x$, on a l'expression suivante :

$$X(z)=\sum Res\left(\frac{TL(x)[p]}{1-e^{pT}z^{-1}}\right)$$
:::{prf:proof}
L'expression de la transformée de Laplace inverse de $x$ nous dit que

$$x(t)=\frac{1}{2i\pi} \int_{D^\uparrow}TL(x)[p]e^{pt}dp$$

Donc en revenant à la définition, et pour $|z|>e^{Re(p_0)T}$ ($p_0\in D^\uparrow$ quelconque),

$$X(z)=\sum_{n=0}^{+\infty} x(nT)z^{-n}=\sum_{n=0}^{+\infty}\left[\frac{1}{2i\pi} \int_{D^\uparrow}TL(x)[p]e^{npT}dp\right]z^{-n}$$
$$=\frac{1}{2i\pi} \int_{D^\uparrow}TL(x)[p]\sum_{n=0}^{+\infty}\left(e^{pT}z^{-1}\right)^ndp$$


Comme $|z^{−1}e^{pT}|< 1$, on trouve donc 

$$X(z)= \frac{1}{2i\pi} \int_{D^\uparrow}\frac{TL(x)[p]}{1-e^{pT}z^{-1}}dp=\sum Res\left(\frac{TL(x)[p]}{1-e^{pT}z^{-1}}\right)$$

:::

::::