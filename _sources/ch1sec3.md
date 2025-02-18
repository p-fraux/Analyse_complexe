
## Fonctions holomorphes
$\newcommand{\R}{\mathbb{R}}$
$\newcommand{\Q}{\mathbb{Q}}$
$\newcommand{\N}{\mathbb{N}}$
$\newcommand{\C}{\mathbb{C}}$
$\newcommand{\Z}{\mathbb{Z}}$

(série et dérivation)=
### Différentiabilité dans $\R^2$ et $\C$-dérivabilité


::::{prf:definition}
:label: definition_differentiable
Soit $\Omega\subset\R^2$ un ouvert et $P:\Omega\to \C$ une application.

On dit que $P$ est _différentiable_ en $(x_0,y_0)$ s'il existe $\Omega_1\subset\Omega-(x_0,y_0)$ un ouvert contenant  $(0,0)$, $A(x_0,y_0)$ et $B(x_0,y_0)$ deux complexes et $\epsilon : \R^2\to \C$ une fonction vérifiant $\lim\limits_{||(h,k)||\to 0}\epsilon(h,k)=0$ tels que

$$\forall (h,k)\in \Omega_1, P(x_0+h,y_0+k)= P(x_0,y_0) +A(x_0,y_0)h + B(x_0,y_0)k + ||(h,k)||\epsilon(h,k)$$

On dira abusivement qu'une fonction de la variable complexe : $f:\Omega\subset \C \to \C$ est différentiable en $(x_0,y_0)$ si la fonction induite sur $\R^2$ (en transformant un couple de réels en un complexe via la partie réelle et imaginaire) est différentiable.

Soit $f$ une fonction de la variable complexe définit sur un voisinage de $z_0\in \C$. On dira que f est dérivable au sens complexe en $z_0$ si le quotient $\frac{f(z)-f(z_0)}{z-z_0}$ admet une limite au sens complexe dans $\C$ en $z_0$. On notera alors cette limite $f'(z_0)$. 

:::{prf:remark}
:class: dropdown
Pour ces deux notions, nous avons la notion globale que différentiabilité et de dérivabilité lorsque l'on a la propriété en tous points.

Ces deux notions impliquent également la continuité de la fonction au niveau du point considéré (la démonstration de cette affirmation est laissé en exercice au lecteur rigoureux).
:::
::::

::::{prf:theorem} Condition de Cauchy-Riemann
:label: conditioncauchy
Soit $f$ une fonction de la variable complexe.

Si $f$ est dérivable en $z_0$, alors elle est différentiable en $z_0$.

:::{prf:proof}
Avec les notations de la définition, on vérifie que $A(z_0)=f'(z_0)$ et $B(z_0)=i f'(z_0)$ et $\epsilon(h,k) (h+ik)=f(z_0+h+ik)-f(z_0) - f'(z_0)(h+ik)$ convient en utilisant directement la définition de la dérivabilité.
:::


On note $P=Re(f)$ et $Q=Im(f)$.
Alors :

$$\begin{align*}
        f\text{ est dérivable en }z_0=x_0+iy_0&\iff& &P\text{ et } Q\text{ sont différentiable en } (x_0,y_0)\\
        &&\text{et}&\\
        &&&\left\{\begin{matrix}
            \frac{\partial P}{\partial x}(x_0,y_0)&=\frac{\partial Q}{\partial y}(x_0,y_0)\\
            \frac{\partial P}{\partial y}(x_0,y_0)&=-\frac{\partial Q}{\partial x}(x_0,y_0)
        \end{matrix}\right.
    \end{align*}$$

en particulier,si $f$ est dérivable au sens complexe,

$$f'(z_0)=\frac{\partial P}{\partial x}+i\frac{\partial Q}{\partial x},$$
$$f'(z_0)=\frac{\partial Q}{\partial y}-i\frac{\partial P}{\partial y}.$$

```{prf:example} Exemples et contre-exemples
:class: dropdown
- $f:z\mapsto z$ est dérivable. En effet, comme $\frac{z-z_0}{z-z_0}=1\to 1$, f est dérivable en tout point $z_0$.
- $f:z\mapsto z^2$ est dérivable. En effet, comme $\frac{z^2-z_0^2}{z-z_0}=z+z_0\to 2z_0$, f est dérivable en tout point $z_0$.
- $g:z\mapsto \overline{z}$ est différentiable mais n'est pas dérivable. La différentiabilité est immédiate, puisque pour $(x,y)\in \R^2$, $\overline{z+x-iy}=\overline{z}+x-iy$. Maintenant, pour montrer que g n'est pas dérivable, on peut remarquer que

$$\frac{\overline{z_0+x-iy}-\overline{z_0}}{x+iy}=\frac{x-iy}{x+iy}$$

et que ce quotient vaut $1$ si $y=0$ et $-1$ si $x=0$. Le quotient ne peut donc pas converger au vu de sa dépendance en la pente du chemin d'approche.
```

::::


### Espace des fonctions holomorphes

::::{prf:definition}
:label: definition_holomorphie
On appelle \emph{fonction holomorphe} sur un ouvert $\Omega$ de $\C$ une fonction qui est dérivable (au sens complexe) en tout point de $\Omega$.

On note $\mathcal{H}(\Omega)$ l'ensemble des fonctions holomorphes sur $\Omega$.

:::{prf:proposition}
:label: proposition_anneau_holomorphe
:class: dropdown
Soient $(f,g)\in \mathcal{H}(\Omega)^2$ et $(\lambda,\mu)\in \C^2$. Alors
- $\lambda f+\mu g\in\mathcal{H}(\Omega) $ et $(\lambda f+\mu g)'=\lambda f'+\mu g'$.
- $fg\in\mathcal{H}(\Omega) $ et $(fg)'=f'g+fg'$.
- Si $\forall z\in \Omega, g(z)\neq0$, alors $\frac{1}{g}\in \mathcal{H}(\Omega)$ et $(\frac{1}{g})'=\frac{g'}{g^2}$.

- Soit $f\in \mathcal{H}(\Omega)$ et $g\in \mathcal{H}(f(\Omega))$, alors $g\circ f \in \mathcal{H}(\Omega)$  et $(g\circ f)'=f'\times (g'\circ f)$.\newline
- Si $f$ est bijective de $\Omega$ sur $f (\Omega)$ , alors $f^{-1}\in \mathcal{H}(f(\Omega))$ et $(f^{-1})'=\frac{1}{f'\circ f^{-1}}$
:::

```{prf:example} Exemple des fonctions algébriques
:class: dropdown
On dérive formellement par rapport à $z$ comme pour les fonctions de la variable réelle par rapport à $x$.

$$(az)'=a,$$
$$(z^n)'=nz^{n-1}.$$
```
:::{prf:proposition}
:class: dropdown
:label: proposition_derive_SE
Soit $f(z)=\sum_{n=0}^{+\infty} a_n z^n$ une série entière de rayon de convergence $R$.
$f$ est une fonction holomorphe sur le disque ouvert $B(0,R)$, et sa dérivé est alors la série

$$f'(z)=\sum_{n=0}^{+\infty}na_n z^{n-1}.$$
```{prf:proof}
Il s'agit simplement d'appliquer le théorème de dérivation sous le signe intégral (voir le cours d'intégration, aussi appellé dérivation sous le symbole sommatoire) pour la mesure de comptage, sur tout disque fermé $\overline{B(0,r)}$ où $r<R$.

En effet, les fonctions $f_n : z\mapsto a_nz^n$ sont continues donc mesurables, leurs dérivées existent et sont uniformément bornées par $z\mapsto n|a_n| r^n$ (qui est sommable car $r<R$).
```
:::

```{prf:remark}
A l'aide de cette propriété, on prouve que

$$exp'(z)=exp(z),$$

$$\cos'(z)=-\sin(z),$$

$$\cosh'(z)=\sinh'(z)...$$
```

::::

```{exercise}
:label: derivee_log
:class: dropdown
a) Calculer la dérivée de la détermination de rang k et de droite de coupure $\R_+$ du logarithme complexe. 

:::{admonition} Solution a)
:class: dropdown
Soit $z_0\in \C\backslash \R_+$. Alors par définition, sur un voisinage de $z_0$, on a que $\exp(\log_k(z))=z$. On utilise alors la formule de la dérivée d'une fonction réciproque pour avoir que

$$\log_k'(z)=(f^{-1})'(z)=\frac{1}{f'(f^{-1}(z))}=\frac{1}{\exp(\log_k(z))}=\frac{1}{z}.$$

On remarquera que la constante additive dans le logarithme, dû à la détermination, a disparue.
:::

b) Calculer la dérivée d'une détermination d'une fonction puissance complexe. 

:::{admonition} Solution b)
:class: dropdown
On se donne $\alpha \in \C$ et on considère

$$f:z\mapsto \exp(\alpha\log_k(z)).$$

On obtient par dérivée des fonctions composées que 

$$f'(z)=\frac{\alpha}{z}f(z) = "\alpha z^{\alpha-1}".$$ 
:::

```

```{exercise}
:label: fonction_holomorphe
:class: dropdown
 L'application $g : x+iy \mapsto \frac{x}{x^2+y^2}-i\frac{y}{x^2+y^2} $ est-elle holomorphe (avec $(x,y)\in \R^2$) ? 

:::{admonition} Solution 
:class: dropdown
On remarque que $g(z)=\frac{\overline{z}}{|z|^2}=\frac{1}{z}$, qui est holomorphe, par propriété usuelles, sur $\C^*$.
:::

```