## Formule d'inversion
$\newcommand{\R}{\mathbb{R}}$
$\newcommand{\Q}{\mathbb{Q}}$
$\newcommand{\N}{\mathbb{N}}$
$\newcommand{\C}{\mathbb{C}}$
$\newcommand{\Z}{\mathbb{Z}}$
$\newcommand{\red}{\color{red}}$

::::{prf:theorem}
Soit $f$ absolument transformable et $F$ sa transformée de Laplace.

Alors pour tout $x_0>x_{ca}$, si l'on note $D^\uparrow(x)$ la droite verticale au-dessus de $x$, nous aurons (sous réserve d'intégrabilité) que

$$f(t)Heav(t)=\frac{1}{2i\pi}\int_{D^\uparrow(x_0)}F(z)e^{{\red +}zt}dz = \int_{-\infty}^{+\infty}F(x_0+iy)\frac{e^{(x_0+iy)t}}{2\pi}dy.$$

(On parle de contour de Bromwich pour désigner une telle droite d'intégration)

```{figure} Bromwich.png
---
:alt: fig:Bromwich
:width: 200px
:align: center
---

Le contour de Bromwich
```

:::{prf:proof}

Rappelons pour la preuve le résultat fondamental de la théorie de Fourier.

Si $x :t \mapsto x(t)$ est une fonction intégrable de transformée de fourrier $X(\nu)=TF(x)(\nu)=\int_{-\infty}^{+\infty} x(t)e^{-i\nu t}dt$ également intégrable, alors

$$ x(t)= \int_{-\infty}^{+\infty}X(\nu)\frac{e^{i\nu t}}{2\pi}d\nu.$$

On remarque que 

$$F(x_0+iy)=\int_{0}^{+\infty}x(t)e^{-x_0t}e^{-iyt} dt=TF(x(t)Heav(t)e^{x_0t})[y].$$

On applique alors la théorie de Fourier continue pour obtenir que

$$ f(t)Heav(t) e^{-x_0t}=\int_{-\infty}^{+\infty} F(x_0+iy)\frac{e^{iyt}}{2\pi}dy.$$

Nous avons retrouvé le terme de droite de la proposition (en multipliant par $e^{x_0t}$), et celui du milieu découle directement d'une paramétrisation de la droite $D^\uparrow(x_0)$. 
:::

```{prf:remark}
:class: dropdown
Il peut sembler étonnant que la formule d'inversion ne dépend pas de la droite considérée du moment qu'elle se situe à droite de l'abscisse de convergence absolue. Mais il s'agit d'une conséquence facile du théorème de Cauchy sur des rectangles de plus en plus allongé verticalement appliqué à la transformée.
```
::::

:::{admonition} Méthode générale pour inverser la transformée :
:class: tip
Deux cas présentent dans la plupart des cas. 
- Soit on reconnait directement la transformée de Laplace d'une fonction présente dans une table, et dans ce cas il n'y a pas de travail supplémentaire puisque si $TL(f)=g$, alors $TL^{-1}(g)=f$.
- Sinon, on commence par déterminer l'abscisse de convergence, puis on choisit une suite de contour dont un morceau converge vers le contour de Bromwich, les autres étant soit facile à calculer, soit ayant une convergence vers 0 facile à démontrer (par exemple avec les lemmes de Jordan). 

Dans des exercices de première année l'on vous donnera les contours à considerer.
:::


::::{exercise}
:label: exer_transformation_racine
Chercher l'inverse de la transformée de Laplace de la fonction $p\mapsto \frac{1}{\sqrt{p}}$ (avec la détermination principale de droite de coupure $\R_-$). On utilisera le contour ci-dessous et l'on admettra que l'intégrale sur les morceaux $A-B$ et $C-D$ converge vers 0.

```{image} domaine_racine.png
:alt: fig:domaine_racine
:width: 300px
:align: center
```

:::{admonition} Solution
:class: dropdown
On souhaite calculer $\lim\limits_{R\to +\infty} \int_{\gamma_1} \frac{e^{pt}}{\sqrt{p}}dp$ pour $t>0$. Pour cela, nous allons utiliser le théorème des résidus (ou celui de Cauchy vu qu'il n'y a pas de résidus).

Remarquons d'abord que pour $p$ dans l'image de $\gamma_2$ ou de $\gamma_6$, $|\frac{1}{\sqrt{p}}|=\frac{1}{\sqrt{R}}$. Comme cette majoration est uniforme et tend vers 0, que $t>0$ et que nous intégrons sur des parties de $C_R^g$, nous avons d'après le deuxième lemme de Jordan que

$$\lim\limits_{R\to +\infty} \int_{\gamma_2}\frac{e^{pt}}{\sqrt{p}}dp+\int_{\gamma_6}\frac{e^{pt}}{\sqrt{p}}dp =0.$$

De plus, pour $p$ dans l'image de $\gamma_4$, nous avons $|p\frac{e^{pt}}{\sqrt{p}}|\leq \sqrt{\epsilon} e^{\epsilon t}$. Comme cette majoration est uniforme et tend vers 0, nous avons d'après le premier lemme de Jordan que 

$$\lim\limits_{\epsilon\to 0} \int_{\gamma_4}\frac{e^{pt}}{\sqrt{p}}dp=0.$$

Enfin, calculons directement :

$$\int_{\gamma_3} \frac{e^{pt}}{\sqrt{p}}dp =\int_{-\sqrt{R^2-\epsilon^2}}^0 \frac{e^{(u+i\epsilon)t}}{i\sqrt{u+i\epsilon}} du$$
$$\underset{\R\to \infty,\epsilon \to 0}{\to} -i\int_0^{+\infty} \frac{e^{-tw}}{\sqrt{w}}dw= -i\frac{2}{\sqrt{t}}\int _0^{+\infty} e^{-x^2}dx$$
$$=\frac{-i\sqrt{\pi}}{\sqrt{t}}$$

De la même manière, on montre que 

$$\int_{\gamma_5} \frac{e^{pt}}{\sqrt{p}}dp =\int_0^{-\sqrt{R^2-\epsilon^2}} \frac{e^{(u-i\epsilon)t}}{{\red{-}}i\sqrt{u-i\epsilon}} du$$
$$\underset{\R\to \infty,\epsilon \to 0}{\to} \frac{-i\sqrt{\pi}}{\sqrt{t}}$$


Le théorème des résidus nous affirme que 

$$\int_{\gamma_1\cup A-B \cup \gamma_2\cup...\cup C-D}\frac{e^{pt}}{\sqrt{p}}dp = 2i\pi \sum_{z_j \in Dom} Res(\frac{e^{pt}}{\sqrt{p}},z_j) =0.$$

Donc en passant à la limite en $R$ et en $\epsilon$, on trouve finalement que 
$\int_{\gamma_1}\frac{e^{pt}}{\sqrt{p}}dp \to \frac{2i\sqrt{\pi}}{\sqrt{t}}$.
    
Finalement,

$$f(t) = \frac{1}{2i\pi} \int_{D^\uparrow}\frac{e^{pt}}{\sqrt{p}}dp = \frac{1}{\sqrt{\pi t}}.$$
    
:::
::::

::::{exercise}
:label: exer_transformation_gen
 Déterminer la transformée de Laplace inverse de la fonction $$ F : p \mapsto \frac{1}{(p^2+1)^2}$$ à l'aide du contour de Bromwich.
 
```{image} domaine_gen.png
:alt: fig:domaine_gen
:width: 300px
:align: center
```
:::{admonition} Solution
:class: dropdown
La fonction $F$ a pour singularités isolées les points  $±i$. En particulier, son abscisse de convergence est $0$.Le contour est bien pertinent

Remarquons d'abord que pour $|z|=R$,
$|F(z)|\leq \frac{1}{(R^2-1)^2}$. Comme cette majoration est uniforme et tend vers 0, nous avons par le second lemme de Jordan (on intègre sur $C_R^g$ et $t>0$) que 

$$\int_{\gamma_3}F(p)e^{tp}dp \to 0.$$

Maintenant, il est immédiat que

$$\int_{\gamma_{2}}F(p)e^{tp}dp=\int_1^0\frac{e^{itR+tu}}{((R+iu)^2+1)^2} du \to 0$$

et 

$$ \int_{\gamma_{4}}F(p)e^{tp}dp=\int_0^1\frac{e^{itR+tu}}{((R+iu)^2+1)^2} du \to 0$$

Calculons les résidus de $F$. Comme il s'agit de pôles d'ordre 2, 

$$Res(F(p)e^{tp},i)=\frac{d}{dp}\left[(p-i)^2F(p)e^{tp}\right]_{|p=i} =\frac{d}{dp}\left[\frac{e^{tp}}{(p+i)^2}\right]_{|p=i} =\frac{(2i)^2te^{it}-2(2i)e^{it}}{(2i)^3} =\frac{1-it}{2}e^{it}$$

$$Res(F(p)e^{tp},-i)=\frac{d}{dp}\left[\frac{e^{tp}}{(p-i)^2}\right]_{|p=-i} =\frac{(-2i)^2te^{-it}-2(-2i)e^{-it}}{(-2i)^3} =\frac{1+it}{2}e^{-it}$$

Le théorème des résidus nous donne alors que 

$$\int_{\gamma_1\cup\gamma_2\cup\gamma_3\cup\gamma_4}F(p)e^{pt}dp=2i\pi\left(Res(F(p)e^{tp},i)\!\phantom{\int}\!+\phantom{\int}\!Res(F(p)e^{tp},-i)\right)=2i\pi\left(\cos(t)\!\phantom{\int}\!+\phantom{\int}\!t\sin(t)\right).$$
Finalement, en passant à la limite en $R\to +\infty$, on trouve que

$$f(t)=\frac{1}{2i\pi}\int_{D^\uparrow}F(p)e^{pt} = \cos(t)+t\sin(t)$$
    
:::

::::


::::{exercise}
:label: exer_transformation_tanh
On considère la fonction " dent de scie" défini par 

$$\forall t\in \R, f(t)=f(t+1),$$

$$\forall t\in[0,1], f(t)=\frac{1}{2}-t.$$

Montrer que sa transformée de Laplace est 

$$TL(f)[p]=-\frac{1}{p^2}+\frac{1}{2p}\frac{1+e^{-p}}{1-e^{-p}}.$$

Inversement, calculer par la formule d'inversion une autre expression de $f$. à l'aide du contours suivant pour $R\in 2\pi\N+\pi$
 
```{image} domaine_gen.png
:alt: fig:domaine_gen
:width: 300px
:align: center
```
:::{admonition} Solution
:class: dropdown
Directement par le calcul, pour $Re(p)>0$

$$TL(f)[p]&=\int_0^{+\infty}f(t)e^{-pt}dt=\sum_{n=0}^{+\infty} \int_{n}^{n+1}f(t)e^{-pt}dt$$

En découpant sur des intérvalles de la taille de la période de $f$,

$$TL(f)[p]=\sum_{n=0}^{+\infty} \int_{0}^{1}f(t+n)e^{-p(t+n)}dt$$

On translate pour utiliser la périodicité et l'expression de $f$,

$$TL(f)[p]=\sum_{n=0}^{+\infty} e^{-pn}\int_{0}^{1}f(t)e^{-pt}dt=\sum_{n=0}^{+\infty} e^{-pn}\int_{0}^{1}\left(\frac{1}{2}-t\right)e^{-pt}dt$$
$$=\sum_{n=0}^{+\infty} e^{-pn}\left[\frac{e^{-pt}}{-2p}+(\frac{te^{-pt}}{p}+\frac{e^{-pt}}{p^2})\right]_0^1=\sum_{n=0}^{+\infty} e^{-pn}\left(\frac{e^{-p}}{-2p}+(\frac{e^{-p}}{p}+\frac{e^{-p}}{p^2})+\frac{1}{2p}-\frac{1}{p^2}\right),$$
$$=\sum_{n=0}^{+\infty} e^{-pn}\left(\frac{e^{-p}+1}{2p}+\frac{e^{-p}-1}{p^2}\right)=\frac{e^{-p}+1}{2p(1-e^{-p})} - \frac{1}{p^2}$$
(La première somme étant géométrique, et la deuxième téléscopique.)

Réciproquement, on pose 

$$F: p \mapsto -\frac{1}{p^2}+\frac{1}{2p}\frac{1+e^{-p}}{1-e^{-p}}$$
    
Remarquons tout d'abord que les singularités sont $\{0\}\cup 2i\pi\Z$ (puisque les zéros de $1-e^{-p}$ sont exactement $2i\pi \Z$. En particulier, son abscisse de convergence est $0=\sup\left(Re(p.s.i.)\right)$. On se donne alors $D^{\uparrow}$ la droite verticale d'abscisse $1$ (par exemple) et $t>0$, et l'on cherche à calculer 

$$\int_{D^{\uparrow}} F(p)e^{pt}.$$

On utilise alors le contour donnée.

Remarquons que sur $\gamma_3$, $|F(p)|=|-\frac{1}{p^2}+\frac{1+e^p}{p(1-e^{p}}|\leq\frac{1}{R^2}+\frac{2}{R|1-e^{p}|}$. Il nous faut alors pour appliquer le lemme de Jordan minorer uniformément $|1-e^{-p}|$. Une inégalité triangulaire ne suffit clairement pas, car minorant par 0 sur l'axe imaginaire. 

_Écrivons alors $p=(2k+1)\pi e^{i\theta}$, et soyons plus précis dans les calculs_

$$|1-e^{p}|^2=|1-e^{(2k+1)\pi \cos(\theta)+i\sin(\theta)}|^2$$
$$=|1-e^{(2k+1)\pi \cos(\theta)}\cos((2k+1)\pi\sin(\theta)) +i e^{(2k+1)\pi \cos(\theta)}\sin(-(2k+1)\pi\sin(\theta))|^2$$
$$=\left(1-e^{(2k+1)\pi \cos(\theta)}\cos((2k+1)\pi\sin(\theta))\right)^2+\left(e^{(2k+1)\pi \cos(\theta)}\sin((2k+1)\pi\sin(\theta))\right)^2$$
$$\geq \left(1-e^{(2k+1)\pi \cos(\theta)}\cos((2k+1)\pi\sin(\theta))\right)^2$$

_On se rend alors compte que dans l'expression exacte, nous avons deux termes en compétition : l'exponentielle qui peut devenir très proche de 1, et le terme en $\cos\left((2k+1)\pi\sin(\theta)\right)$ qui peut devenir négatif. L'idée est de faire une disjonction de cas suivant l'importance de $\cos(\theta)$._

_On se donne $\delta_k$ que l'on se fixera plus tard, et l'on fait deux cas en utilisant que dans le domaine considéré les angles ont des cosinus négatifs._

_**Cas 1 :** $\cos(\theta)\leq -\delta_k$._

_Ce cas est le plus simple, car il suffit de retomber sur l'inégalité trangulaire :_

$$|1-e^{p}|\geq 1-|e^{p}|= 1-e^{(2k+1)\pi \cos(\theta}\geq 1-e^{-(2k+1)\delta_k}$$

Ceci nous donne une première condition sur $\delta_k$. Il faudra le choisir de telle manière que $(2k+1)\delta_k>c>0$.

_**Cas 2 :** $\cos(\theta)^2\leq \delta_k^2$._

_On veut alors donner une condition sur $\delta_k$ qui assure que $\cos\left((2k+1)\pi\sin(\theta)\right)$ soit négatif._

_Nous avons pour cela que $1\geq \sin(\theta)^2\geq 1-\delta_k^2$, et donc que_

$$ (2k+1)\pi\geq (2k+1)\pi |\sin(\theta)|\geq (2k+1)\pi\sqrt{1-\delta_k^2}$$

_On choisit alors $\delta_k$ de telle manière que $(2k+1)\pi\sqrt{1-\delta^2}\geq (2k+\frac{1}{2})\pi$, par exemple $\delta_k^2=1-(\frac{4k+1}{4k+2})^2$, qui vérifie également que $\left((2k+1)\delta_k\right)^2=(2k+1)^2-(2k+\frac{1}{2})^2=2k+\frac{3}{4}$._

_Dans ce cas, par décroissance de $\cos$ sur $[(2k+\frac{1}{2})\pi;(2k+1)\pi]$, on trouve bien que_

$$\cos\left((2k+1)\pi\sin(\theta)\right)\leq \cos((2k+\frac{1}{2})\pi)=0.$$

_Ceci nous assure finalement que_

$$|1-e^{p}|^2\geq \left(1-e^{(2k+1)\pi \cos(\theta)}\cos((2k+1)\pi\sin(\theta))\right)^2\geq 1$$

_Comme dans les deux cas, $|1-e^{p}|$ est minoré, nous avons bien que $\sup\limits_{\gamma_3}|F(p)|\to 0$._

Munie de cette majoration, nous pouvons utiliser le deuxième lemme de Jordan pour conclure que 

$$\int_{\gamma_3} F(p)e^{pt}dp \to 0.$$

En fait, un raisonnement similaire permet de conclure que 

$$\int_{\gamma_2} F(p)e^{pt}dp \to 0 ,$$
$$\int_{\gamma_4} F(p)e^{pt}dp \to 0 .$$
Calculons à présent les résidus. Seul le deuxième terme de la somme est pertinent, $p\mapsto\frac{1}{p^2}$ n'ayant aucun résidu. Remarquons pour le calcul que les singularités en $2i\pi \Z\backslash\{0\}$ sont des pôles simples pour obtenir
$$Res(F(p)e^{pt},2i\pi k)=\frac{1+e^{-2i\pi k}}{2(2i\pi k) (-e^{-2i\pi k})} e^{2i\pi k t}=-\frac{e^{2i\pi k t}}{2i\pi k }.$$
Pour le résidu en 0, on fait un développement asymptotique :
$$\frac{1}{2p}\frac{1+e^{-p}}{1-e^{-p}}=\frac{1}{2p}(2-p+o(p))\frac{1}{p-\frac{p^2}{2}+o(p^2)} = \frac{1}{2p^2}(2-p+o(p))(1-\frac{p}{2}+o(p))=\frac{1}{p^2}-\frac{1}{p} +o(\frac{1}{p}).$$
On en déduit donc que $$Res(F(p)e^{pt},0)=1.$$
Finalement, grâce au théorème des résidus, on sait que 
$$\frac{1}{2i\pi}\int_{D^\uparrow}F(p)e^{pt}dp=\lim_{k\to +\infty}1+\sum_{\underset{k\neq 0}{k=-n}}^nRes(F(p)e^{pt},2i\pi k).$$
Ce qui nous donne l'expression
$$f(t)=1-\sum_{k=1}^{+\infty}\frac{1}{\pi k}\frac{e^{2i\pi k t}-e^{-2i\pi k t}}{2i}=1-\sum_{k=1}^{+\infty}\frac{\sin(2\pi k t)}{\pi k}.$$
\underline{Remarque :} On reconnait là une série de Fourier. 
:::

::::