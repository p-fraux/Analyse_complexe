(annexe_derivation_sous_integrale)=
##   Dérivation sous le signe intégral de fonctions holomorphes
$\newcommand{\R}{\mathbb{R}}$
$\newcommand{\Q}{\mathbb{Q}}$
$\newcommand{\N}{\mathbb{N}}$
$\newcommand{\C}{\mathbb{C}}$
$\newcommand{\Z}{\mathbb{Z}}$

Rappelons tout d'abord le théorème général de dérivation sous l'intégrale de Lebesgue pour les fonctions complexes :

::::{prf:proposition} Voir cours d'intégration

Soit $f :(z,x)\in \Omega\times X \mapsto f(z,x) \in\C$ où $\Omega$ est un ouvert de $\C$ et $(X,\mathcal{T},\mu)$ est un espace mesuré (Par exemple la mesure de Lebesgue, qui donnera un résultat sur l'intégrale de Riemann, ou encore la mesure de comptage qui donnera un résultat pour les séries fonctionnelles). On suppose

- _(mesurabilité et intégrabilité)_ Pour tous $z\in \Omega,$ la fonction $ x\in X\mapsto f(z,x)$ est mesurable et intégrable.
- _(dérivabilité)_ Pour presque tous $x\in X$, la fonction $z\mapsto f(z,x)$ est dérivable sur $\Omega$.
- _(domination)_ Pour tout $z_0\in \Omega$, il existe une boule ouverte $B(z_0,\rho)$ et une fonction $h\in L^1(X,\mu)$ intégrable telle que pour presque tout $x\in X$,

$$|\frac{\partial}{\partial z}f(z,x)|\leq h(x).$$

Alors $F : z\mapsto \int_X f(z,x)d\mu(x)$ existe, est dérivable de dérivée 

$$F'(z)=\int_X\frac{\partial}{\partial z}f(z,x)d\mu(x).$$
::::

Or, nous avons la formule intégrale de Cauchy {prf:ref}`proposition_Cauchy_integral` :

$$f\in \mathcal{H}(B(a,r+\epsilon)),\forall z\in B(a,r), f(z)=\frac{1}{2i\pi}\int_C\frac{f(w)}{z-w}dw.$$


Nous n'avons plus besoin de dominer la dérivée, mais uniquement la fonction ! (penser à des fonctions fortement oscillantes convergeant vers une fonction pour voir à quel point ceci peut sembler contre-intuitif). 

::::{prf:theorem}
Soit $f :(z,x)\in \Omega\times X \mapsto f(z,x) \C$ où $\Omega$ est un ouvert de $\C$ et $(X,\mathcal{T},\mu)$ est un espace mesuré. On suppose
- _(mesurabilité)_ Pour tout $z\in \Omega,$ la fonction $ x\in X\mapsto f(z,x)$ est mesurable.
- _(dérivabilité)_ Pour tout $x\in X$, la fonction $z\mapsto f(z,x)$ est holomorphe sur $\Omega$.
- _(domination)_ Pour tout $z_0\in \Omega$, il existe une boule ouverte $B(z_0,\rho)$ et une fonction $h\in L^1(X,\mu)$ intégrable telle que pour presque tout $x\in X$, et tous $z\in \overline{B(z_0,\rho)}$,

$$|f(z,x)|\leq h(x).$$

Alors $F : z\mapsto \int_X f(z,x)d\mu(x)$ existe, est dérivable de dérivées successives 

$$F^{(n)}(z)=\int_X\frac{\partial^n}{\partial z^n}f(z,x)d\mu(x).$$

:::{prf:proof}

Soit $z_0\in \Omega$, et $\rho$ et $h$ associé par la troisième hypothèse. Du fait de l'intégrabilité de $h$, $F$ est bien défini.

Soit $x\in X$ tel que $f(\cdot,x) $ soit holomorphe, et soient $z$ un élément de $B(z_0,\frac{\rho}{2})$. D'après la formule de Cauchy, nous aurons alors que

$$f(z,x)=\frac{1}{2i\pi}\int_{\partial \vec{B}(z_0,\rho)}\frac{f(w,x)}{w-z}dw.$$

Ainsi, pour $z\neq z'$ dans cette boule,

$$f(z,x)-f(z',x)=\frac{1}{2i\pi}\int_{\partial \vec{B}(z_0,\rho)}\frac{f(w,x)(z-z')}{(w-z)(w-z')}dw,$$

$$\frac{f(z,x)-f(z',x)}{z-z'}=\frac{1}{2i\pi}\int_{\partial \vec{B}(z_0,\rho)}\frac{f(w,x)}{(w-z)(w-z')}dw.$$

Or, comme $(z,z')\in B(z_0,\frac{\rho}{2})$, ils ne sont pas trop proches du bord, et donc $|\frac{f(w,x)}{(z-w)(z'-w)}|\leq \frac{4}{\rho^2}$

$$\left|\frac{f(z,x)-f(z',x)}{z-z'}\right|\leq \frac{4}{\rho}h(x) $$

Finalement par le théorème précédent, $F'$ existe et vaut 

$$F'(z)=\int_X \frac{\partial}{\partial z}f(z,x)d\mu(x).$$

Pour les ordres supérieurs, il s'agit de faire une récurrence en remarquant pour l'hérédité que l'on a montré que $|\frac{\partial}{\partial z}f(z,x)|\leq \frac{4}{\rho}h(x)$ sur $B(z_0,\frac{\rho}{2})$, ce qui permet de réutiliser le résultat que nous venons de montrer.


:::

::::





