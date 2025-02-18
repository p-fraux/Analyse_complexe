## Les fonctions harmoniques (H.P.)
$\newcommand{\R}{\mathbb{R}}$
$\newcommand{\Q}{\mathbb{Q}}$
$\newcommand{\N}{\mathbb{N}}$
$\newcommand{\C}{\mathbb{C}}$
$\newcommand{\Z}{\mathbb{Z}}$

Les zéros du Laplacien bi-dimensionnel, c'est-à-dire les solutions de l'équation
$$\Delta\psi:=\frac{\partial^2\psi}{\partial x^2}+\frac{\partial^2\psi}{\partial y^2} =0,$$
 sont omniprésentes dans les modélisations physiques. Le potentiel électrostatique dans le vide est solution de cette équation, tout comme le potentiel magnétique scalaire. Pour des modèles idéaux, certains problèmes de flux en hydrodynamiques correspondent à cette équation. On  retrouve encore ces solutions lorsqu'on cherche le déplacement d'une membrane lorsqu'on déforme le bord depuis une boucle plate. Au vu de leur prédominance, il est naturel de chercher à mieux les comprendre.
 
 :::{prf:definition}
  On dit qu'une fonction $\phi$ est _harmonique_ sur un domaine $D\subset \R^2$ si elle est de classe $C^2$ et qu'en tout point de $D$ elle vérifie

$$\frac{\partial^2\phi}{\partial x^2}+\frac{\partial^2\phi}{\partial y^2} =0 .$$
 :::
 
 
 ::::{prf:proposition} 

 Soit $\Omega$ un ouvert et $f\in \mathcal{H}(\Omega)$. Alors $Re(f)$ et $Im(f)$ sont harmoniques.
 
Réciproquement, si $u$ est une fonction harmonique sur un ouvert simplement connexe, elle est la partie réelle d'une fonction holomorphe.

:::{prf:proof}
Il s'agit d'une application des formules de Cauchy-Riemann avec l'existence d'une primitive complexe pour les fonctions holomorphes.

Plus précisément, si $f\in \mathcal{H}(\Omega)$, alors $f$ est infiniment dérivable, avec $f'=\frac{\partial f}{\partial x}=-i\frac{\partial f}{\partial y}$. En dérivant deux fois, on obtient bien que $f$ est holomorphe. En particulier, il en est de même pour ses parties réelles et imaginaires.

Réciproquement, soit $u$ est une fonction harmonique sur un ouvert simplement connexe. posons alors $g=\frac{\partial u}{\partial x}-i\frac{\partial u}{\partial y}$.

Par définition des fonctions harmoniques, $g$ est différentiable, avec 

$$ \frac{\partial g}{\partial y}=\frac{\partial^2 u}{\partial y\partial x}-i\frac{\partial^2 u}{\partial y^2}=\frac{\partial^2 u}{\partial x\partial y}+i\frac{\partial^2 u}{\partial x^2} =i\frac{\partial }{\partial x}\left(-i\frac{\partial u}{\partial y}+\frac{\partial u}{\partial x} \right) = i\frac{\partial g}{\partial x}$$

Donc $g$ vérifie les équations de Cauchy-Riemann, et est donc holomorphe. Comme on est sur un ouvert simplement connexe, il existe donc une primitive de $g$, que l'on notera $f$.

On pose $P=Re(f)$ et $Q=Im(f)$. Comme $\frac{\partial P}{\partial x}-i\frac{\partial P}{\partial y}=f'=g =\frac{\partial u}{\partial x}-i\frac{\partial u}{\partial y} $.

Donc $ \frac{\partial P}{\partial x}=\frac{\partial u}{\partial x}$ et $ \frac{\partial P}{\partial y}=\frac{\partial u}{\partial y}$, ce qui implique par connexité du domaine que 
    $P=u+Cste$.

Donc finalement, $u=Re(f-Cste)$.
    
:::
::::


Cette propriété a deux conséquences étonnantes :

 ::::{prf:proposition}
- Si $u$ est harmonique, alors elle est de classe $C^{\infty}$
- Si $u$ est harmonique, alors elle vérifie la propriété de la moyenne

$$\forall a\in \Omega,\forall 0\leq r<d(a,\Omega^c), \quad u(a)=\frac{1}{2\pi}\int_0^{2\pi} u(a+re^{i\theta})d\theta$$

::::
