
## Singularités et Théorème des résidus
$\newcommand{\R}{\mathbb{R}}$
$\newcommand{\Q}{\mathbb{Q}}$
$\newcommand{\N}{\mathbb{N}}$
$\newcommand{\C}{\mathbb{C}}$
$\newcommand{\Z}{\mathbb{Z}}$

### Théorème des résidus
::::{prf:definition} 
:label: psi
 Soit $f$ une fonction complexe, et $z_0\in \C$.

On dit que $z_0$ est un _point de singularité isolé_ (p.s.i.) de $f$ si il existe $R>0$ tel que $f$ est holomorphe sur le disque pointé $B(z_0,R)\backslash\{z_0\}$.

Lorsque $z_0$ est un p.s.i., on appelle _résidu de $f$ en $z_0$_ la quantité

$$Res(f,z_0):= \lim\limits_{r\to0}\frac{1}{2i\pi}\int_{c_r}f(z)dz.$$
::::


::::{prf:theorem} Développement de Laurent et résidus
Soit $f$ holomorphe sur $\Omega\backslash \cup_j\{z_j\}$, où $\Omega$ est un ouvert non vide de $\C$ et $\{z_j\}$ est un ensemble de points isolés (en particulier, $z_j$ sont des p.s.i. de $f$).

Enfin, soit $D \subset \Omega$ un domaine simplement connexe de contour $\partial D$ inclus dans $\Omega$. Alors

$$\int_{\partial D^+}f(z)dz=2i\pi \sum_{z_j\in D} Res(f,z_j).$$

:::{prf:remark}
:label: remark_psi
Si $z_0$ est un p.s.i. de $f$, alors  il existe $(a_n, b_n)$ tels que 

$$\forall z\in B(z_0,R)\backslash\{z_0\}, f(z)=\sum_{k=1}^{+\infty}\frac{b_k}{(z-z_0)^k} +\sum_{k=0}^{+\infty}a_k(z-z_0)^k.$$

Et l'on peut alors vérifier que $Res(f,z_0)=b_1$.
:::

::::



```{prf:definition}
:label: def_poles
On dit qu'un p.s.i. $z_0$ de $f$ est un pôle 
 d'ordre $p$ si la fonction $\varphi : z\mapsto (z-z_0)^pf(z)$ s'étend en une fonction holomorphe sur un voisinage de $z_0$, et que de plus $\varphi(z_0)\neq0$.
 
:::{admonition} Lien avec les résidus :
:class: dropdown
Considérons donc $z_0$ un pôle d'ordre $p$ de $f$. Sur un voisinage de $z_0$, on écrit un développement de Taylor de $\varphi$ :

$$\varphi(z)=\varphi(z_0)+...+\frac{(z-z_0)^{p-1}}{(p-1)!}\varphi^{(p-1)}(z_0)+O((z-z_0)^p).$$

Ce qui nous donne le développement asymptotique de f au voisinage de $z_0$ suivant :

$$f(z)=\frac{\varphi(z_0)}{(z-z_0)^p}+...+\frac{\varphi^{(p-1)}(z_0)}{(p-1)!(z-z_0)}+O(1).$$

Par unicité du développement de Laurent, nous trouvons donc que

$$Res(f,z_0)=\frac{\varphi^{(p-1)}(z_0)}{(p-1)!}=\frac{1}{(p-1)!}\frac{d^{p-1}}{dz^{p-1}}[(z-z_0)^pf(z)]_{|z=z_0}$$
:::
```





:::{admonition} Méthode de calcul de résidus :
:class: tip
- Pour $p>2$, il est souvent plus rapide de calculer un développement limité (voir toute la série de Laurent) que d'utiliser le point développé ci-dessus.
-  Pour $p=2$, nous aurons $Res(f,z_0)=\frac{d}{dz}[(z-z_0)^2f(z)]_{|z=z_0}$
- Pour $p=1$, nous pourrons utiliser $Res(f,z_0)=\lim\limits_{z\to z_0}(z-z_0)f(z)$. En fait, si l'on écrit $f(z)=\frac{g(z)}{h(z)}$ avec $g(z_0)\neq 0$, $h(z_0)=0$ et $h'(z_0)\neq0$, alors un simple développement limité de h montre qu'en fait,

$$Res(f,z_0)=\frac{g(z_0)}{h'(z_0)}$$
:::

```{exercise}
:label: exer_Residus_a
Déterminer les points de singularité isolé et les résidus de la fonction $f :z\mapsto \frac{1}{\sin(z)}$.

:::{admonition} Solution 
:class: dropdown
Tout d'abord, d'après les propriétés usuelles, $f$ est holomorphe là où $\sin(z)\neq 0$. Or, pour $z\in \C$

$$\sin(z)=0 \iff \frac{e^{iz} - e^{-iz}}{2i}=0\iff e^{iz}=e^{-iz}$$
$$\iff e^{2iz}=1\iff 2iz\in 2i\pi \Z&\iff z\in \pi \Z$$

Donc l'ensemble des points de singularité isolé de $f$ sont compris dans $\pi \Z$. Comme cet ensemble est clairement constitué de singularités et qu'il est discret (sans point d'accumulation), il s'agit bien de l'ensemble des points de singularité isolé.

Maintenant, pour $k\in \Z$, on a que $\sin(k\pi )=0$ et $\cos(k\pi)=(-1)^k$. Donc avec la caractérisation précédente pour $g=1$ et $h=\sin$, nous obtenons que

$$Res(f,k\pi)=\frac{1}{(-1)^k}=(-1)^k.$$
:::

```



### Exemples d'applications du théorème des résidus

::::{prf:example} Calcul d'une intégrale de la forme $I=\int_{-\infty}^{+\infty} g(x)dx$
:label:example_calcul_integral_a
Lorsqu'on peut trouver $f$ une fonction holomorphe égale à $g$ sur $\R$, le premier réflexe est de regarder si l'on peut prendre le contour constitué d’une partie rectiligne (souvent de la forme $[-R,R]$), qui donne $I$ à la limite, et de parties circulaires qui ferment le contour (où l'on espère pouvoir appliquer un des lemmes de Jordan).

Calculer ainsi

$$\int_{-\infty}^{+\infty} \frac{x^2+1}{x^4+1}dx.$$

:::{admonition} Solution 
:class: dropdown
On cherche par exemple à calculer 

$$\int_{-\infty}^{+\infty} \frac{x^2+1}{x^4+1}dx.$$

Commençons par remarquer que $f:z\mapsto \frac{z^2+1}{z^4+1}$ convient. Les points de singularités isolés de $f$ sont 

$$\left\{e^{i\frac{\pi}{4}},ie^{i\frac{\pi}{4}},-e^{i\frac{\pi}{4}},-ie^{i\frac{\pi}{4}} \right\}.$$

On choisit de prendre le contour $\gamma=\gamma_1\cup \gamma_2$ suivant :

```{image} Residu_a.png
:alt: fig:Residu_a
:width: 300px
:align: center
```

Les singularités dans le domaine sont alors $\left\{e^{i\frac{\pi}{4}},ie^{i\frac{\pi}{4}}\right\} .$ Calculons les résidus associés. Vu qu'il s'agit de pôles simples d'une fraction rationnelle, en posant $P:z\mapsto z^2+1$ et $Q:z\mapsto z^4+1$, nous aurons

$$Res(f,e^{i\frac{\pi}{4}})=\frac{P(e^{i\frac{\pi}{4}})}{Q'(e^{i\frac{\pi}{4}})}=\frac{i+1}{3e^{3i\frac{\pi}{4}}}=\frac{\sqrt{2}e^{i\frac{\pi}{4}}}{3ie^{i\frac{\pi}{4}}}=-i\frac{\sqrt{2}}{3}$$

et 

$$Res(f,ie^{i\frac{\pi}{4}})=\frac{-i+1}{-3i e^{3i\frac{\pi}{4}}}=\frac{-\sqrt{2}e^{3i\frac{\pi}{4}}}{-3i e^{3i\frac{\pi}{4}}}=-i\frac{\sqrt{2}}{3}.$$

Le théorème des résidus nous donne alors que 

$$ \int_{\gamma_1\cup\gamma_2}f(z)dz=2i\pi\left(Res(f,e^{i\frac{\pi}{4}})+Res(f,ie^{i\frac{\pi}{4}})\right) = \frac{2\pi\sqrt{2}}{3}.$$

Comme $f$ est intégrable sur $\R$, la convergence dominée nous montre que $\int_{\gamma_1}f(z)dz$ converge vers $I$.

Pour calculer la limite de $\int_{\gamma_2} f(z) dz$, nous allons chercher à utiliser le premier lemme de Jordan.
Remarquons que grâce aux inégalités triangulaires, pour $|z|=R$, nous aurons

$$|z^2+1|\leq R^2+1,$$
$$|z^4+1|\geq R^4-1$$

Ainsi, 
$\sup\limits_{\gamma_2}|zf(z)|\leq \frac{R(R^2+1)}{R^4-1}\to 0$.

Donc d'après le premier lemme de Jordan, $\int_{\gamma_2} f(z) dz\to 0$.

Finalement,

$$I=\frac{2\pi\sqrt{2}}{3}.$$

:::

::::



::::{prf:example} Calcul d'une intégrale de la forme $I=\int_{A} g(x)dx$, où g comprend une fonction multiforme.
:label:example_calcul_integral_b
On cherche alors une détermination qui permet d'atteindre tout A, ainsi qu'un domaine adapté.

Calculer ainsi  pour $a\in]0,1[$ l'intégrale 

$$J=\int_{0}^{+\infty} \frac{x^{a-1}}{1+x} dx.$$

:::{admonition} Solution 
:class: dropdown

On cherche par exemple à calculer pour $a\in]0,1[$ l'intégrale 

$$J=\int_{0}^{+\infty} \frac{x^{a-1}}{1+x} dx.$$

On choisit de travailler avec la détermination de rang $0$ et de droite de coupure $\R_+$ (le seul point de singularité de $f$ est alors $-1$). De plus, on choisit de travailler avec le domaine $\gamma=\gamma_1\cup\gamma_2\cup\gamma_3\cup\gamma_4$ suivant :

```{image} Residu_b.png
:alt: fig:Residu_b
:width: 300px
:align: center
```
où l'on note $R$ le rayon du cercle extérieur et $\epsilon$ le rayon du cercle intérieur. Le résidu de $f$ en $-1$ vaut

$$Res(f,-1)=\frac{e^{(0+i\pi)(a-1)}}{1}=-e^{i\pi a}$$

Le théorème des résidus nous affirme que 

$$2i\pi Res(f,-1)=\int_{\gamma_1\cup\gamma_2\cup\gamma_3\cup\gamma_4} f(z)dz=\int_{\gamma_1}f(z)dz+\int_{\gamma_2}f(z)dz+\int_{\gamma_3}f(z)dz+\int_{\gamma_4}f(z)dz.$$

Grace au théorème de convergence dominé (avec comme fontion dominante  $z\mapsto \frac{|z|^{a-1}}{0.5+|z|}$), nous avons que 

$$\lim\limits_{R\to \infty, \epsilon\to 0}\int_{\gamma_1}f(z)dz =\lim\limits_{R\to \infty, \epsilon\to 0}\int_{\epsilon}^R\frac{(x+i\epsilon)^{a-1}}{1+x+i\epsilon}dx = J,$$
$$\lim\limits_{R\to \infty, \epsilon\to 0}\int_{\gamma_3}f(z)dz=\lim\limits_{R\to \infty, \epsilon\to 0}\int_{0}^R\frac{(x-i\epsilon)^{a-1}}{1+x-i\epsilon} (-dx)  = -J e^{2i\pi(a-1)}.$$

où le terme $e^{2i\pi(a-1)}$ vient du choix de la détermination complexe.

Traitons maintenant le cas de $\gamma_2$ et de $\gamma_4$.

Remarquons d'abord que $|z^{a-1}|= |z|^{a-1}$, puis grâce aux inégalités triangulaires que 

$$\forall z\in \hat{\gamma_4}, |zf(z)|\leq \epsilon\frac{\epsilon^{a-1}}{1-\epsilon},$$
$$\forall z\in \hat{\gamma_2}, |zf(z)|\leq R\frac{R^{a-1}}{R-1}.$$

La limite nulle de ces deux majorations avec le premier lemme de Jordan que 

$$\lim\limits_{\epsilon\to 0}\int_{\gamma_4}f(z)dz =0,$$
$$\lim\limits_{R\to +\infty}\int_{\gamma_2}f(z)dz =0.$$

Nous avons donc obtenu que 

$$J-e^{2i\pi a}J=-2i\pi e^{i\pi a} $$

Finalement, 

$$J=\frac{-2i\pi}{e^{-i\pi a}-e^{i\pi a}}=\frac{\pi}{\sin(\pi a)}.$$

:::

::::


::::{prf:example} Calcul d'une intégrale trigonométrique, de la forme $I=\int_{0}^{2\pi} F(\cos(\theta),\sin(\theta))d\theta$, où F est une  fraction rationnelle.
:label:example_calcul_integral_c
On se ramène alors au calcul d’une intégrale sur le cercle unité, à l'aide des formules d'Euler exprimant cosinus et sinus comme des combinaisons d'exponentielles complexes.

Calculer ainsi

$$J=\int_{0}^{2\pi}\frac{d\theta}{5+3\sin(\theta)}.$$
:::{admonition} Solution 
:class: dropdown

On pose $z=e^{i\theta}$, et l'on a alors que

$$\frac{e^{-i\theta}}{5+3\sin(\theta)}=\frac{1/z}{5+\frac{3}{2i}(z-\frac{1}{z})}=\frac{1}{5z-\frac{3}{2}i(z^2-1)}.$$

Donc (en faisant attention à ne pas oublier la dérivée de la paramétrisation), 

$$ \int_{0}^{2\pi}\frac{d\theta}{5+3\sin(\theta)} = \frac{1}{i}\int_\mathbb{U} \frac{dz}{5z-\frac{3}{2}i(z^2-1)}$$

Les points de singularité isolée de $f:z\mapsto \frac{1}{5z-\frac{3}{2}i(z^2-1)}$ sont les zéros du polynôme de degré 2 au dénominateur. On les détermine :

$$\Delta = 25-9=16$$
$$z_±=\frac{-5±4}{3i}$$

Le seul point isolé situé dans le disque unité est alors $z_+=\frac{i}{3}$. 

$$Res(f,z_+)=\frac{1}{5-3iz_+}=\frac{1}{4}$$

Finalement, d'après le théorème des résidus,

$$\int_\mathbb{U} \frac{dz}{5z-\frac{3}{2}i(z^2-1)}=2i\pi \frac{1}{4}=\frac{i\pi}{2},$$

ce qui permet de conclure que 

$$ \int_{0}^{2\pi}\frac{d\theta}{5+3\sin(\theta)} =\frac{\pi}{2}.$$



:::

::::





````{exercise}
:label: exer_residu_d
A l'aide du contour suivant et du théorème des résidus, calculer  pour $n\geq 2$ l'intégrale $\int_{0}^{+\infty}\frac{1}{1+x^n}dx$.

:::{image} Residu_d.png
:alt: fig:Residu_d
:width: 300px
:align: center
:::

:::{admonition} Solution 
:class: dropdown
On pose $f : z\mapsto \frac{1}{1+z^n}$.

Si $|z|=R$, alors $|zf(z)|\leq \frac{R}{R^n-1}$. Comme cette majoration est uniforme, le premier lemme de Jordan nous donne que 

$$\int_{\gamma_2}\frac{1}{1+z^n} dz \underset{R\to +\infty}{\to} 0.$$

Nous avons directement que 

$$\int_{\gamma_1}\frac{1}{1+z^n} dz \underset{R\to +\infty}{\to}\int_{0}^{+\infty}\frac{1}{1+x^n}dx$$

Enfin, 

$$\int_{\gamma_3}\frac{1}{1+z^n} dz = \int_R^0\frac{1}{1+t^ne^{i2\pi}}e^{i\frac{2\pi}{n}}dt\underset{R\to +\infty}{\to}-e^{i\frac{2\pi}{n}}\int_{0}^{+\infty}\frac{1}{1+x^n}dx$$

Maintenant, la seule singularité de $f$ dans le domaine considéré est $e^{i\frac{\pi}{n}}$. Comme il s'agit d'un pôle simple, 

$$Res(f,e^{i\frac{\pi}{n}})=\frac{1}{ne^{i\frac{(n-1)\pi}{n}}}=-\frac{e^{i\frac{\pi}{n}}}{n}.$$

Le théorème des résidus permet alors de conclure que 

$$\int_{\gamma_1\cup \gamma_2\cup \gamma_3}\frac{1}{1+z^n} dz = 2i\pi \left(-\frac{e^{i\frac{\pi}{n}}}{n}\right). $$

En passant alors à la limite quand $R$ tend vers l'infini, on trouve

$$(1-e^{i\frac{2\pi}{n}})\int_{0}^{+\infty}\frac{1}{1+x^n}dx=\frac{-2i\pi e^{i\frac{\pi}{n}}}{n}.
$$

soit encore

$$\int_{0}^{+\infty}\frac{1}{1+x^n}dx= \frac{2i\pi e^{i\frac{\pi}{n}}}{n(e^{i\frac{2\pi}{n}}-1)}=\frac{\pi}{n\sin(\frac{\pi}{n})}$$
:::

````


````{exercise}
:label: exer_residu_e
 A l'aide du contour suivant et du théorème des résidus, calculer  pour $n\geq 2$ l'intégrale $\int_{0}^{+\infty}\frac{1}{1+x^n}dx$.

:::{image} Residu_e.png
:alt: fig:Residu_e
:width: 300px
:align: center
:::

:::{admonition} Solution 
:class: dropdown
On pose $f : z\mapsto \frac{1}{1+z^n}$.

Si $|z|=R$, alors $|zf(z)|\leq \frac{R}{R^n-1}$. Comme cette majoration est uniforme, le premier lemme de Jordan nous donne que 

$$\int_{\gamma_2}\frac{1}{1+z^n} dz \underset{R\to +\infty}{\to} 0.$$

Nous avons directement que 

$$\int_{\gamma_1}\frac{1}{1+z^n} dz \underset{R\to +\infty}{\to}\int_{0}^{+\infty}\frac{1}{1+x^n}dx$$

Enfin, 

$$\int_{\gamma_3}\frac{1}{1+z^n} dz = \int_R^0\frac{1}{1+t^ne^{i2\pi}}e^{i\frac{2\pi}{n}}dt\underset{R\to +\infty}{\to}-e^{i\frac{2\pi}{n}}\int_{0}^{+\infty}\frac{1}{1+x^n}dx$$

Maintenant, la seule singularité de $f$ dans le domaine considéré est $e^{i\frac{\pi}{n}}$. Comme il s'agit d'un pôle simple, 

$$Res(f,e^{i\frac{\pi}{n}})=\frac{1}{ne^{i\frac{(n-1)\pi}{n}}}=-\frac{e^{i\frac{\pi}{n}}}{n}.$$

Le théorème des résidus permet alors de conclure que 

$$\int_{\gamma_1\cup \gamma_2\cup \gamma_3}\frac{1}{1+z^n} dz = 2i\pi \left(-\frac{e^{i\frac{\pi}{n}}}{n}\right). $$

En passant alors à la limite quand $R$ tend vers l'infini, on trouve

$$(1-e^{i\frac{2\pi}{n}})\int_{0}^{+\infty}\frac{1}{1+x^n}dx=\frac{-2i\pi e^{i\frac{\pi}{n}}}{n}.
$$

soit encore

$$\int_{0}^{+\infty}\frac{1}{1+x^n}dx= \frac{2i\pi e^{i\frac{\pi}{n}}}{n(e^{i\frac{2\pi}{n}}-1)}=\frac{\pi}{n\sin(\frac{\pi}{n})}$$

:::

````





````{exercise}
:label: exer_residu_g
Déterminer avec le théorème des résidus la valeur de l'intégrale

$$\frac{1}{2i\pi}\int_{C_1^+} \frac{e^z-e^{-z}}{z^4}dz.$$

:::{admonition} Solution 
:class: dropdown
On reconnait l'intégrale sur un contour fermé autour d'un point de singularité. Nous allons donc utiliser le théorème des résidus. A priori, la singularité est un pôle d'ordre 4, nous allons donc effectuer le développement de Laurent. On sait que

$$e^{z}=\sum_{n=0}^{+\infty}\frac{z^n}{n!}.$$

On en déduit donc que 

$$\frac{e^{z}-e^{-z}}{z^4}=\sum_{\underset{n impair}{n=0}}^{+\infty} 2\frac{z^{n-4}}{n!}=2z^{-3}+2z^{-1}+\sum_{\underset{k impair}{k=0}}^{+\infty}2\frac{z^k}{(k+4)}$$

En particulier,

$$Res\left(\frac{e^{z}-e^{-z}}{z^4},0\right)=2.$$

Finalement, 

$$\frac{1}{2i\pi}\int_{C_1^+} \frac{e^z-e^{-z}}{z^4}dz=2.$$
:::

````



````{exercise}
:label: exer_residu_h
Pour $f : x\mapsto \frac{1}{\cosh(\pi x)}$, calculer la transformée de Fourier $\hat{f} : \xi \mapsto \int_\R f(t)e^{-2i\pi t\xi}dt$ en utilisant le contour délimité par le rectangle de sommets $±R$, $±R+2i$.

:::{admonition} Solution 
:class: dropdown
 Dans tout l'exercice, on se fixe $\xi$

On pose $g : z\mapsto \frac{e^{-2i\pi z\xi}}{\cosh(\pi z)}$. 

On commence par chercher les points de singularités isolés. Ils ont nécessairement situé en les points d'annulation du dénominateur. Or, pour $z\in \C$,

$$\cosh(\pi z)=0 \iff e^{\pi z}=-e^{-\pi z}$$
$$\iff e^{2\pi z}=-1\iff z\in \frac{i}{2} +i\Z$$

Maintenant, comme le numérateur ne s'annule pas en ces points, il s'agit bien de singularité. Au vu du contour choisi, le théorème des résidus affirme que

$$\int_{Rectangle}g(z)dz = 2i\pi \left(Res(g,\frac{i}{2}) + Res(g,\frac{3i}{2}\right).$$

Pour calculer ces résidus, nous remarquons qu'il s'agit de résidu sur des pôles simples, donc

$$Res(g,\frac{i}{2})=\frac{e^{+\pi\xi}}{\pi\sinh(i\frac{\pi}{2})}=\frac{e^{\pi\xi}}{\pi i\sin(\frac{\pi}{2})}=\frac{e^{\pi\xi}}{i \pi},$$

$$Res(g,\frac{3i}{2})=\frac{e^{+3\pi\xi}}{\pi\sinh(i\frac{3\pi}{2})}=\frac{e^{3\pi\xi}}{\pi i \sin(\frac{3\pi}{2})}=-\frac{e^{3\pi\xi}}{i\pi},$$

Maintenant,

$$\int_0^{2} \frac{e^{4\pi\xi -2i\pi R\xi}}{\cosh(\pi R+i\pi t)} idt \to 0,$$

$$\int_2^{0} \frac{e^{4\pi\xi +2i\pi R\xi}}{\cosh(-\pi R+i\pi t)} idt \to 0,$$

Et par périodicité de l'exponentielle complexe (et donc du cosinus hyperbolique),

$$\int_{R}^{-R}\frac{e^{2i\pi t\xi+4\pi\xi}}{\cosh(\pi t+2i\pi)} dt = - e^{4\pi\xi}\int_{-R}^{R}\frac{e^{2i\pi t\xi}}{\cosh(\pi t)} dt $$

Finalement, en passant à la limite, on obtient du théorème des résidus que

$$\hat{f}\left(1-e^{4\pi\xi}\right)=2i\pi\left(\frac{e^{\pi\xi}}{i\pi}-\frac{e^{3\pi\xi}}{i\pi}\right).$$

Donc 

$$\hat{f}(\xi)=2\frac{e^{\pi\xi}-e^{3\pi\xi}}{1-e^{4\pi\xi}}=2\frac{e^{-\pi\xi}-e^{\pi\xi}}{e^{-2\pi\xi}-e^{2\pi\xi}}=\frac{1}{\cosh(\xi)}$$
:::

````

````{exercise} (Examen 2024)} **Calcul de l'intégrale du sinus cardinal**
:label: exer_residu_i

On souhaite calculer l’intégrale définie par $ I=\int_0^{+\infty} \frac{\sin(x)}{x} dx.$

Soit $f(\cdot)$ qui possède un pôle en 0 et qui admet le développement de Laurent :

$$f(z)= \sum_{n=1}^{+\infty} \frac{b_n}{z^n} + \sum_{n=0}^{+\infty} a_nz^n,$$

Pour tout $z \in d(0,r)\backslash \{0\}$ où $d(0,r)$ désigne le disque de centre 0 et de rayon $r> 0$.

a)Lorsque z = 0 est un pôle simple (i.e., d’ordre 1), rappeler les valeurs des $b_n$ ($n \geq 1$) en fonction du résidu res$f(0)$ de la fonction f en 0.

:::{admonition} Solution a)
:class: dropdown
Avoir un pôle simple revient à ce que pour $n\geq 2$, on ait $b_n=0$. De plus,  $b_1= \text{res}f(0)$
:::

b) En déduire que  

$$\lim\limits_{\epsilon \to 0} \int_{\gamma_\epsilon} f(z)dz =i \pi \text{Res}( f, 0)$$

où $\gamma_\epsilon$ est le demi-cercle situé dans le demi-plan supérieur de centre 0 et de rayon $\epsilon$.

:::{admonition} Solution b)
:class: dropdown
Revenons à la définition d'une intégrale curviligne parcouru dans le sens trigonométrique, puis écrivons le développement de Laurent de notre fonction ayant un pôle simple :

$$\int_{\gamma_\epsilon} f(z)dz = \int_0^{\pi} f(\epsilon e^{i\theta}) \epsilon i e^{i\theta}d\theta,$$
$$=\int_0^\pi \left(\frac{b_1}{\epsilon e^{i\theta}} \epsilon i e^{i\theta} +  \sum_{n=0}^{+\infty} a_n(\epsilon e^{i\theta}))^n \epsilon i e^{i\theta} \right) d\theta$$
$$=i\pi b_1 + \epsilon \int_0^\pi  \sum_{n=0}^{+\infty} a_n(\epsilon e^{i\theta}))^n i e^{i\theta}  d\theta$$

Enfin, comme la série de Laurent admet un rayon de convergence supérieur à r, on a que la série $\sum_{n=0}^{+\infty} a_n(\epsilon e^{i\theta}))^n i e^{i\theta} $ est uniformément bornée en $\theta$ pour $\epsilon$ au voisinage de 0 _(par exemple par $\sum_{n=0}^{+\infty} |a_n| (\frac{r}{2})^n$)_. Donc à la limite :
 
 $$\lim\limits_{\epsilon \to 0} \int_{\gamma_\epsilon} f(z)dz =i \pi b_1=i\pi \text{res} f(0)$$
 
:::
c) Soit g(·) la fonction définie par $g(z) = \frac{e^{iz}}{z}$ . Montrer que

$$\lim\limits_{R\to +\infty}\int_{C_R}g(z)dz = 0$$ 

où $C_R$ est le demi-cercle situé dans le demi-plan supérieur de centre 0 et de rayon R.

:::{admonition} Solution c)
:class: dropdown
On va chercher à appliquer le deuxième lemme de Jordan. On cherche à intégrer $z\mapsto f(z)e^{i\times {\color{red}1}\times z}$ où f est l'inversion complexe, sur **le demi-cercle situé dans le demi-plan supérieur** de centre 0 et de rayon R. 

D'abord, l'on a bien **1**>0. Ensuite, 

$$\sup\limits_{z\in C_R}|f(z)| = \sup\limits_{z\in C_R}\frac{1}{|z|} = \frac{1}{R} \underset{R\to+\infty}{\to} 0$$

Donc nous avons toutes les hypothèses du lemme de Jordan, en pouvons en conclure la limite demandée.
:::

d) Appliquer le Théorème de Cauchy à la fonction g(·) le long du contour représenté ci dessous. A l’aide des résultats des
Questions précédentes, en déduire la valeur de l’intégrale I.

:::{image} Residu_i.png
:alt: fig:Residu_i
:width: 300px
:align: center
:::

:::{admonition} Solution d)
:class: dropdown
La fonction g est holomorphe dans le contour considéré, donc d'après le théorème de Cauchy, 

$$\int_{\gamma_1\cup C_R\cup \gamma_3\cup \gamma_\epsilon} g(z)dz =0.$$

Nous avons vu dans la question c que $\lim\limits_{R\to +\infty}\int_{C_R} g(z)dz =0$, et dans la question b que (_attention à l'orientation du chemin curviligne_) 

$$\lim\limits_{\epsilon\to 0}\int_ {\gamma_\epsilon} g(z)dz=-\lim\limits_{\epsilon\to 0}\int_ {-\gamma_\epsilon} g(z)dz = -i\pi \text{res}(g,0).$$

Et un rapide calcul donne que ce résidu vaut 1.

Enfin, 

$$\int_{\gamma_1} g(z)dz+\int_{\gamma_3} g(z)dz = \int_{-R}^{-\epsilon} \frac{e^{ix}}{x} dx +  \int_{\epsilon}^R \frac{e^{ix}}{x} dx ,$$
$$=  \int_{\epsilon}^R \frac{e^{ix}-e^{-ix}}{x}dx=2 i \int_{\epsilon}^R \frac{\sin(x)}{x}dx.$$

En passant à la limite en R et en $\epsilon$, on en déduit donc que 

$$I = \frac{\pi}{2}$$
:::


````