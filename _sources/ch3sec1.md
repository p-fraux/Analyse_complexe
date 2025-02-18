## Définition, domaine de validité et propriétée fondamentale
$\newcommand{\R}{\mathbb{R}}$
$\newcommand{\Q}{\mathbb{Q}}$
$\newcommand{\N}{\mathbb{N}}$
$\newcommand{\C}{\mathbb{C}}$
$\newcommand{\Z}{\mathbb{Z}}$


### Fonctions transformables

::::{prf:definition}
On dit qu'une fonction $f$ est _transformable_ si elle est localement intégrable et s'il existe $x_0\in \R$ tel que l'intégrale généralisée de $g:t\mapsto e^{-x_0t}f(t)$ converge.

Pour $f$ une fonction transformable et pour $p\in \C$ tel que cela est un sens (_i.e._ il y ait convergence), on appelle transformé de Laplace de $f$ en p la valeur

$$F(p)=TL(f)[p] := \int_0^{+\infty} e^{-pt}f(t)dt.$$

Lorsque cela a du sens, on dira que $TL(f)[p]$ existe.

```{prf:proposition} Domaine de convergence
:class: dropdown
:label: convergence
Soient $f$ une fonction transformable et $p_0\in \C$. 

Si $TL(f)[p_0]$ existe, alors pour tout $p\in \C$ tel que $Re(p)>Re(p_0)$, $TL(f)[p]$ existe.

:::{prf:proof}
Comme $TL(f)[p]$ existe, on peut poser $G:x\mapsto \int_{x}^{+\infty}e^{-p_0 t}f(t)dt$.

Maintenant, à l'aide de la généralisation de l'intégration par partie, 
$\int e^{-pt}f(t)$ converge si 
$[e^{(p_0-p)t}G(t)]$ et $\int e^{(p_0-p)t}G(t)$ convergent. 

Or $G$ est une fonction bornée, donc pour $Re(p)>Re(p_0)$, ces deux termes convergent. 
:::

```
**Conséquence :** $\{x \in \R, F(p)\text{ existe } \}$ admet une borne inférieure dans $\R\cup\{-\infty\}$. On l'appelle _abscisse de convergence simple_ de $F$ (ou de $TL(f)$). On la note $x_c$.

```{prf:proposition} Domaine de convergence absolue
:class: dropdown
:label: convergence_absolue
On dit que $TL(f)$ converge absolument en $p_0$ si $\int_0^{+\infty} |e^{-p_0t}f(t)|dt <+\infty$. Lorsque cela est le cas,  $TL(f)[p_0]$ existe.

Si $TL(f)$ converge absolument en $p_0$, alors pour tout $p\in \C$ tel que $Re(p)>Re(p_0)$, $TL(f)[p]$ converge absolument.

:::{prf:proof}
L'existence de la transformée est une conséquence de la construction de l'intégrale de Lebesgue.

Le résultat est alors immédiat puisque pour $Re(p)>Re(p_0)$, on a que $|e^{(p_0-p)t}|\leq 1$.
:::

```

**Conséquence :** Encore une fois $\{x \in \R, F(p)\text{ converge absolument } \}$ admet une borne inférieure. On l'appelle _abscisse de convergence absolue_ de $F$ (ou de $TL(f)$) et on la note $x_{ca}$.

::::


::::{prf:example}
Considérons la fonction $Heav : t \mapsto \left\{\begin{matrix}
    0&\text{ si } t<0\\1&\text{ sinon.}
\end{matrix}\right.$. On cherche à donner les abscisses de convergence et la valeur de la transformée lorsque celle-ci existe.

:::{admonition} Solution 
:class: dropdown
Remarquons d'abord que puisque $Heav$ est à valeur positive, l'abscisse de convergence simple et l'abscisse de convergence absolues sont identiques.

Pour $x<0$, il est immédiat que $Heav(t)e^{-x_0t}\underset{t\to +\infty}\to +\infty$.

En particulier, l'intégrale généralisée diverge grossièrement. De plus, comme pour $x_0>0$, $t\mapsto e^{-x_0t}$ est d'intégrale généralisée convergente. Donc l'abscisse de convergence (simple et absolu) de la fonction $Heav$ est $0$.

Maintenant, prenons $p\in \C$ tel que $Re(p)>0$. Alors

$$TL(Heav)[p]=\int_0^{+\infty} Heav(t) e^{-pt}dt = \left[-\frac{1}{p}e^{-pt}\right]_0^{+\infty}=-0+\frac{1}{p}.$$

:::

::::


::::{prf:example}
Soit $k>0$, et considérons la fonction $f : t \mapsto e^{kt}e^{ie^{kt}}$. On cherche à donner les abscisses de convergence simple et absolue.

:::{admonition} Solution 
:class: dropdown
Comme $|f(t)|=e^{kt}$, il est immédiat que $x_{ca}=k$
(car $e^{(k-k_0)t}$ est intégrable si et seulement si $k_0>k$).

Maintenant, considérons que 

$$\int_0^R e^{-pt}e^{kt}e^{ie^{kt}}dt=\left[e^{-pt}e^{ie^{kt}}\right]_0^R +p\int_{0}^R e^{-pt}e^{ie^{kt}}dt.$$

Alors comme le crochet converge et l'intégrande à droite est intégrable dès que $Re(p)>0$, nous aurons que $x_c=0$.

:::

::::

:::{prf:remark}
L'exemple précédent donne une idée de ce qui suffit pour avoir $x_c\neq x_{ca}$ : une fonction très fortement oscillante.
:::


````{exercise}
:label: exer_transformation_simple
Donner la transformée de Laplace de 

$$f:t\mapsto \left\{\begin{matrix}
        1&\text{si }1<t<2\\0&\text{sinon}
    \end{matrix}\right.$$



:::{admonition} Solution
:class: dropdown

On peut directement calculer l'intégrale. Soit $p\in \C$, avec $p\neq 0$

$$TL(f)[p]=\int_0^{+\infty} f(t)e^{-pt}dt =\int_1^2 e^{-pt}dt$$
$$=\left[\frac{e^{-pt}}{-p}\right]_1^2=\frac{e^{-p}-e^{-2p}}{p}$$
    
:::
````

### Théorèmes fondamentaux

::::{prf:theorem}
Soit $f$ une fonction continue par morceaux sur $\R_+$ et absolument transformable.

Alors $TL(f) : p\mapsto \int_0^{+\infty} e^{−pt}f (t)dt$ est holomorphe sur $]x_{ca} , +\infty[$ (et
 donc indéfiniment dérivable sur $]x_{ca} , +\infty[$) avec
 
 $$\frac{d^n}{dp^n}TL(f)[p]= \int_0^{+\infty}(-t)^ne^{-pt}f(t)dt.$$
:::{prf:proof}
L'holomorphie découle du théorème d'holomorphie sous le signe $\int$ (voir {ref}`annexe_derivation_sous_integrale`). La valeur des dérivées successives découle du même théorème, qui annonce que 

$$\frac{d^n}{dp^n}TL(f)[p]= \int_0^{+\infty}\frac{d^n}{dp^n}\left[e^{-pt}f(t)\right]dt.$$
:::
::::


::::{prf:theorem} Abscisse de convergence et singularitées de la transformée
Soit $F$ une fonction de la variable complexe $p$ holomorphe sur un ouvert maximal, qui est la transformée de Laplace d’une fonction $f\geq 0$. 

Alors F a une singularité (psi, point de branchement, barriere naturelle...) en le réel $x_c$ (voir {cite}`Laplace_Stieltjes`).


::::

**En pratique :**  Si $F$ n'a que des p.s.i. (notés $s_k$) et des points de ramification de (extrémité des demi-droites de coupures notées $r_j$) et est la transformée d'une fonction réelle positive, alors l'abscisse de convergence vérifie :
$$x_c(F) = \sup Re(s_k , r_j ).$$


:::{prf:example}
En admettant qu'il s'agisse bien de transformée de Laplace d’une fonction $f\geq 0$, on a pour $F(p)=\frac{1}{p(p-2)}$ que $x_c=2$ et pour $F(p)=\frac{1}{p+1}$ que $x_c=-1$.
:::