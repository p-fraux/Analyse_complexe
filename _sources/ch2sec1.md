## Intégrale curviligne

$\newcommand{\R}{\mathbb{R}}$
$\newcommand{\Q}{\mathbb{Q}}$
$\newcommand{\N}{\mathbb{N}}$
$\newcommand{\C}{\mathbb{C}}$
$\newcommand{\Z}{\mathbb{Z}}$

### Définition et généralités

::::{prf:definition}
:label: definition_chemin
On appelle _chemin_ de $\C$ l'image d'une application continue $\gamma : [a, b] \to \C$, $[a, b]$  étant un intervalle de $\R$, muni d'un sens de parcours. 

On appelle _lacet_ un chemin tel que $\gamma(a)=\gamma(b)$.

On dit qu'une application $\gamma : [a,b]\to \C$ est $C^1$ par morceaux s'il existe $a=t_1<t_2...<t_n=b$ tel que $\gamma$ soit de classe $C^1$ sur les intervals de la forme $[t_i,t_{i+1}]$.

Si pour un chemin, on peut trouver $\gamma$ qui soit $C^1$ par morceaux, on dira que _le chemin est $C^1$ par morceaux_.

```{figure} chemin.png
---
:alt: fig_chemins
:width: 200px
:align: center
---
Un chemin $C^1$ par morceaux
```

```{figure} lacet.png
---
:alt: fig_lacet
:width: 200px
:align: center
---
Un lacet $C^1$ par morceaux
```

```{prf:example} Exemple de chemin et leur paramétrisation :
:label: example_parametrisation
:class: dropdown
- Segment de droite parallèle à l’axe des abscisses,

$$x\in[x_1,x_2]\mapsto z=x+iy_0.$$

- Segment de droite parallèle à l’axe des ordonnées,

$$y\in[y_1,y_2]\mapsto z=x_0+iy.$$

- Segment de droite passant par l’origine,

$$\rho \in [\rho_1,\rho_2]\mapsto z=\rho e^{i\theta}.$$

- Arc de cercle de rayon $R_0$ et de centre $a$,

$$\theta\in [\theta_1,\theta_2]\mapsto a+R_0e^{i\theta}.$$
```




::::




::::{prf:definition}
:label: definition_integrale_curviligne
Soit $\gamma([a,b])$ un chemin $C^1$ par morceaux paramétré par $\gamma$, et $a=t_1<...<t_n=b$ la décomposition associée. Soit $f$ une fonction de la variable complexe continue, on appelle _intégrale curviligne_ de $f$ le long de $\gamma$ la valeur

$$\int_\gamma f(z)dz := \sum_{k=0}^{n-1}\int_{t_k}^{t_{k+1}} f(\gamma(t))\gamma'(t)dt$$

également noté

$$\int_\gamma f(z)dz =\int_{\gamma([a,b])} f(z)dz  $$

:::{prf:proposition} Reformulation (Intégrale de Stieltjes)
:class: dropdown
:label: proposition_Stieltjes
Soit $\gamma([a,b])$ un chemin $C^1$ par morceaux paramétré par $\gamma$ et $f$ une fonction continue. Alors l'intégrale curviligne de f sur le chemin défini par gamma peut s'écrire comme limite 

$$\int_\gamma f(z)dz= \lim\limits_{\sup|t_k-t_{k+1}|\underset{n}{\to}0, t_k\leq e_k\leq t_{k+1}}\sum_{k=0}^n f(\gamma(e_k))\left(\gamma(t_{k+1})-\gamma(t_k)\right).$$

On a donc une reformulation. On se donne une subdivision du chemin $\gamma([a,b])=\cup_{k=1}^n \hat{z_{k-1}z_k}$ et un point dans chaque morceau $\xi_k\in\hat{z_{k-1}z_k}$, comme dans le graphique qui suit.
```{image} Stieljes.png
:alt: fig_Stieljes
:width: 400px
:align: center
```
Avec les notations 

$$z_k =x_k+iy_k,$$
$$z_k −z_{k−1} = \Delta x_k +i\Delta y_k,$$
$$\xi_k =a_k+ib_k,$$
$$f(\xi_k) = P(a_k,b_k)+iQ(a_k,b_k),$$

on peut réecrire 

$$\int_\gamma f(z)dz=\lim\limits_{n\to \infty}\sum P(a_k,b_k)\Delta x_k-Q(a_k,b_k)\Delta y_k$$
$$+i\lim\limits_{n\to \infty}\sum P(a_k,b_k)\Delta y_k+Q(a_k,b_k)\Delta x_k=\int_\gamma Pdx-Qdy + i\int_\gamma Qdx+Pdy$$
:::

```{prf:proposition} propriétés de l'intégrale curviligne
:label: proposition_integrale_curviligne
:class: dropdown
- _(Linéarité)_ Soient $\gamma$ un chemmin, $f,g$ deux fonctions continues et $\lambda,\mu \in \C$ deux scalaires. Alors

$$\int_\gamma(\lambda f(z)+\mu g(z))dz = \lambda\int_\gamma f(z)dz +\mu \int_\gamma  g(z)dz.$$
- _(Intégrale d'une constante)_ Si $\gamma$ est une paramètrisation d'un chemin et $K$ est une constante, alors 

$$\int_\gamma Kdz=K\left(\gamma(b)-\gamma(a)\right)$$
- _(Sens de parcours)_ Si $\gamma_+$ est un chemin parcouru dans un sens et $\gamma_-$ le même chemin parcouru dans l'autre sens, alors pour $f$ une fonction continue,

$$\int_{\gamma_+}f(z)dz=-\int_{\gamma_-}f(z)dz$$
- _(Juxtaposition de deux chemins)_ Soient $\gamma_1 : [a,b]\to \C$ et $\gamma_2 : [b,c] \to \C$ deux chemins tels que $\gamma_1(b)=\gamma_2(b)$, et on note $\gamma_1\cup\gamma_2$ le chemin obtenue en juxtaposant ces deux chemins. On a alors que

$$\int_{\gamma_1\cup \gamma_2}f(z)dz=\int_{\gamma_1}f(z)dz+\int_{\gamma_2}f(z)dz$$
:::{prf:proof}
 Il s'agit à chaque fois de revenir à la définition.

La première propriété repose sur la linéarité du produit, la deuxième sur le théorème fondamental de l'analyse (aussi connue sous l'intégrale d'une dérivée), la troisième sur le fait qu'inverser un sens de parcours inverse la dérivé de la paramètrisation et enfin la quatrième sur la relation de Chasles.
:::
```

::::

```{prf:example} Exemple de calcul :
:label: example_calcul_integrale_curv
Notons $\mathbb{U}:=\{z\in \C, |z|=1\}$ et calculons $\int_{\mathbb{U}}\frac{1}{z}dz$.

Remarquons d'abord que $\theta\in [0,2\pi]\mapsto e^{i\theta}$ est une paramétrisation $C^1$ de $\mathbb{U}$. Donc

$$    \int_{\mathbb{U}}\frac{1}{z}dz = \int_0^{2\pi} \frac{1}{e^{i\theta}}(ie^{i\theta}) d\theta =\int_0^{2\pi} id\theta= 2i\pi.$$
```

### Lemmes de Jordan

::::{prf:lemma} $1^{er}$ lemme de Jordan
Soient $a\in \C$ un point, $r>0$ un rayon et $f$ une fonction continue.

Alors si l'on considère comme chemin $C_r(a)$ un arc du cercle centré en $a$ et de rayon $r$, et si \mbox{$\lim\limits_{r\to 0 (resp +\infty)}\sup\limits_{C_r(a)}|(z-a)f(z)|=0$}, alors

$$\lim\limits_{r\to 0 (resp +\infty)}\int_{C_r(a)}f(z)dz=0$$
:::{prf:proof}
Paramétrisons l'arc de cercle par $\gamma : \theta\in [\alpha,\beta] \mapsto a+re^{i\theta}$. Alors

$$\left|\int_{C_r(a)}f(z)dz\right|=\left|\int_{\alpha}^\beta f(a+re^{i\theta})rie^{i\theta}d\theta\right|,$$
$$\leq \int_{\alpha}^\beta |rf(a+re^{i\theta})|d\theta\leq (\beta-\alpha)\sup\limits_{C_r(a)}|(z-a)f(z)|.$$

Ce qui montre par encadrement la limite énoncé.
:::
::::


::::{prf:lemma} $2^{nd}$ lemme de Jordan
```{image} Jordan_hb.png
:alt: fig_Jordan_hb
:width: 300px
:align: center
```
```{image} Jordan_gd.png
:alt: fig_Jordan_gd
:width: 300px
:align: center
```

Soient $a\in \C$ un point, $r>0$ un rayon et $f$ une fonction continue.

Supposons $\lim\limits_{r\to +\infty}\sup\limits_{C_r(a)}|f(z)|=0$, alors

$$\lim\limits_{r\to +\infty}\int_{C_r(a)}e^{imz}f(z)dz=0\qquad \text{ pour }m>0 \text{ et } C_r\subset C_r^+,$$
$$\lim\limits_{r\to +\infty}\int_{C_r(a)}e^{imz}f(z)dz=0\qquad \text{ pour }m<0 \text{ et } C_r\subset C_r^-,$$
$$\lim\limits_{r\to +\infty}\int_{C_r(a)}e^{mz}f(z)dz=0\qquad \text{ pour }m<0 \text{ et } C_r\subset C_r^d,$$
$$\lim\limits_{r\to +\infty}\int_{C_r(a)}e^{mz}f(z)dz=0\qquad \text{ pour }m>0 \text{ et } C_r\subset C_r^g,$$

:::{prf:proof}
Quitte à effectuer une translation de l'espace, on peut supposer sans perte de généralité que $a=0$.

Calculons, pour $0\leq \alpha<\beta\leq \pi$ (cas $C_r\subset C_r^+$) et $m>0$ :

$$\left|\int_{C_r(a)}e^{imz}f(z)dz\right|=\left|\int_\alpha^\beta e^{imre^{i\theta}}f(re^{i\theta})ire^{i\theta}d\theta\right|,$$
$$\leq \sup\limits_{C_r}|f(z)| \int_\alpha^\beta re^{-mr\sin(\theta)}d\theta$$

Car $|e^{z}|=e^{Re(z)}),$

$$\left|\int_{C_r(a)}e^{imz}f(z)dz\right|\leq \sup\limits_{C_r}|f(z)| \int_0^\pi re^{-mr\sin(\theta)}d\theta,$$
$$\leq 2\sup\limits_{C_r}|f(z)| \int_0^{\frac{\pi}{2}} re^{-mr\sin(\theta)}d\theta,$$
$$\leq 2\sup\limits_{C_r}|f(z)| \int_0^{\frac{\pi}{2}} re^{-mr\frac{2\theta}{\pi}}d\theta $$

Car $\sin(\theta)\geq\frac{2\theta}{\pi}$ sur $[0,\frac{\pi}{2}]$,

$$\left|\int_{C_r(a)}e^{imz}f(z)dz\right|\leq \sup\limits_{C_r}|f(z)| \left[\frac{-\pi}{2m}e^{-mr\frac{2\theta}{\pi}} \right]_0^{\frac{\pi}{2}},$$
$$\leq \sup\limits_{C_r}|f(z)|\frac{\pi}{m}\left(1-e^{-mr}\right) \to 0.$$

Pour les trois autres cas, on peut soit refaire tout les calculs, soit se ramener à chaque fois par un changement de variable à la troisième ligne de ce calcul (les détails sont laissé au lecteur).
:::
::::

