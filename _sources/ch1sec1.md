## Analyse dans le plan complexe
$\newcommand{\R}{\mathbb{R}}$
$\newcommand{\Q}{\mathbb{Q}}$
$\newcommand{\N}{\mathbb{N}}$
$\newcommand{\C}{\mathbb{C}}$

### Rappels : Introduction et construction du corps des nombres complexes


:::{prf:definition}

On appelle _ensemble des nombres complexe_ l'ensemble $\C=\R^2$ muni des deux opérations 

$$(x_1,y_1)+(x_2,y_2)=(x_1+x_2,y_1+y_2)$$

$$(x_1,y_1)(x_2,y_2)=(x_1x_2-y_1y_2,x_1y_2+x_2y_1)$$

La première est appelé l'addition et la deuxième la multiplication.
:::


:::{prf:proposition}
:class: dropdown
 L'ensemble $\C$ munit des deux opérations décrites ci-dessus est un corps. Plus précisément, pour tous $(z,z_1,z_2,z_3)\in \C^4$, on a que

- Les deux opérations sont associatives : $z_1+(z_2+z_3) =(z_1+z_2)+z_3 $ et $z_1(z_2z_3) =(z_1z_2)z_3 $
- Les deux opérations sont commutatives : $z_1+z_2=z_2+z_1$ et $z_1z_2=z_2z_1$
- La multiplication est distributive sur l'addition : $z_1(z_2+z_3)=z_1z_2+z_1z_3$.
- L'addition admet un élément neutre $(0,0)$ et tout nombre complexe $z=(x,y)$ admet un opposé $-z=(-x,-y)$.
- La multiplication admet un élément neutre $(1,0)$ et tout nombre complexe non nul $z=(x,y)$ admet un inverse $z^{-1}=(\frac{x}{x^{2}+y^2},\frac{-y}{x^2+y^2})$.
:::




:::{prf:definition}
Soit $z=x+iy\in\C$ un nombre complexe, où l'on a écrit $x=Re(z)$ et $y=Im(z)$.
- Nous appellerons _conjugué_ de $z$ le nombre complexe $\overline{z}:=x-iy$.
- Nous appellerons _module_ de $z$ le nombre réel positif ou nul $|{z}|:=\sqrt{x^2+y^2}=(z\overline{z})^{1/2}$.
:::

::::{prf:proposition}
:label: Propriete-Module
:class: dropdown
Considérons $(z,w,z_1,z_2,z_3)\in \C^5$. Alors
- $Re(z)=\frac{z+\overline{z}}{2}$ et $Im(z)=\frac{z-\overline{z}}{2}$.
- Si $z\neq 0$, alors $z^{-1}=\frac{\overline{z}}{|z|^2}$.
- $|wz|=|w|\cdot|z|$.
- $|z_1+z_2|\leq |z_1|+|z_2|$ (première inégalité triangulaire).
- $|\ |z_1|-|z_2|\ |\leq |z_1-z_2|$ (deuxième inégalité triangulaire).
- $| z_1-z_2|\leq |z_1-z_3|+|z_3-z_2|$.


```{prf:proof}
Les vérifications sont laissées au lecteur. Pour la première inégalité triangulaire, l'on pourra commencer par montrer que
    
$$ (|z_1|+|z_2|)^2-|z_1+z_2|^2=2\left(|z_1\overline{z_2}|-Re(z_1\overline{z_2})\right) $$


```
::::



::::{prf:remark} Représentation graphique essentielle
:class: dropdown

 La construction que nous avons choisie permet d'insister sur le caractère géométrique des nombres complexe. Si l'on considère un plan, muni d’un repère orthonormal direct $(O; \vec{u}, \vec{v})$, il est possible d'associer à chaque point du plan un nombre complexe _via_ ses coordonnées $M(x,y)\mapsto x+iy$. Comme on le voit sur la figure {ref}`fig_Nb-complexe_representation` cela rendra naturelle l'introduction d'une deuxième représentation, correspondant à représenter un point par ses coordonnées polaires.
 
 
 ```{figure} representation.png
:name: fig_Nb-complexe_representation
:width: 600px
:align: center
Représentation des nombres complexes
```

En nous appuyant sur cette interprétation graphique des nombres complexes, on peut écrire $z=r\left(\cos(\theta)+i\sin(\theta)\right)$ où $\theta$ est l'angle entre le demi-axe des réels positifs et la demi-droite partant de $0$ et passant par $z$. On vérifie facilement qu'alors $r=|z|$. On dira alors que $\theta$ est _**un** argument_ de z, et on le note abusivement $\theta=arg(z)$ (abusivement, car $\theta$ n'est déterminé par $z$ qu'à un multiple entier de $2\pi$ près).

Les formules trigonométriques d'addition nous donnent, si $z_k=r_k\left(\cos(\theta_k)+i \sin(\theta_k)\right)$, que

$$z_1z_2=r_1r_2\left(\cos(\theta_1+\theta_2) +i \sin(\theta_1+\theta_2)\right)$$

Cette relation est en fait l'expression d'une formulation exponentielle. Nous verrons dans la section suivante l'existence d'une fonction exponentielle complexe $z\mapsto e^z$, ayant les mêmes propriétés que l'exponentielle réelle. Par exemple, pour tous $(z,w)\in \C^2$, l'on obtiendra que $e^{z+w}=e^ze^w$. De plus, pour $y\in \R$, l'on aura que

$$e^{iy}=\cos(y)+i\sin(y).$$

On pourra alors se servir de cette intuition pour résoudre des équations impliquant des puissances d'un nombre complexe de la forme $z^n=w$ pour $w\in \C$.

```{prf:remark} Lien entre les deux systèmes de coordonnées :
Si les fonctions cosinus et sinus permettent de passer de manière univoque de l'argument et du module aux parties réelles et imaginaire d'un nombre complexe, le passage inverse est plus ardu, du fait de la multiplicité d'arguments potentiels. Une solution possible (aux dépens de la propriété de continuité que nous définirons prochainement) est de choisir un représentant particulier. Nous avons ainsi la fonction Argument principal définit pour $z\in \C$ par

$$Arg(z) = \left\{\begin{matrix}
\pi & \text{ si } z\in \R^*_-\\
    2\arctan\left(\frac{Im(z)}{Re(z)+|z|^2}\right) & \text{ sinon.}
\end{matrix} \right.$$
```
::::


```{admonition} Représentation des fonctions complexes de la variable complexe :
:class:tip

La représentation des nombres complexe comme partie réelle et partie imaginaire invite pour chaque fonction

$$f:\left\{\begin{matrix}\C&\to&\C\\z=x+iy&\mapsto&f(z)=P(x,y) +iQ(x,y)
\end{matrix}\right.$$ 

à définir par isomorphisme une nouvelle fonction

$$F:\left\{\begin{matrix}\R^2&\to&\R^2\\(x,y)&\mapsto&\left(P(x,y),Q(x,y)\right).
\end{matrix}\right. $$
```

```{exercise}
:label: ecriture_exponentielle
:class: dropdown

Écrire les nombres suivant sous forme $z=re^{i\theta}$ :

$$2+2\sqrt{3} i\quad ; \quad -5+5i\quad ; \quad -\sqrt{6}-\sqrt{2}i\quad ; \quad -3i.$$
:::{admonition} Solution 
:class: dropdown
On commence par calculer le module à chaque fois, puis l'argument.

On trouve alors 

$$2+2\sqrt{3} i=4e^{i\frac{\pi}{3}} ; \quad -5+5i=5\sqrt{2} e^{i\frac{3\pi}{4}} ; \quad -\sqrt{6}-\sqrt{2}i= 2\sqrt{2} e^{-i\frac{\pi}{6}}; \quad -3i=3e^{-\frac{\pi}{2}}.$$
:::

```

```{exercise}
:label: simplification
:class: dropdown
Donner une expression simplifiée de $\frac{(1+i)^9}{(1-i)^7}$.

:::{admonition} Solution 
:class: dropdown
On écrit $1+i=\sqrt{2}e^{i\frac{\pi}{4}}$ et  $1-i=\sqrt{2}e^{-i\frac{\pi}{4}}$, ce qui nous permet directement d'obtenir que :

$$\frac{(1+i)^9}{(1-i)^7}=\sqrt{2}^{9-7} e^{i\frac{\pi}{4}(9-(-7))} = 2e^{4i\pi}=2.$$
:::

```
```{exercise}
:label: equation_cercle
:class: dropdown
Démontrer que l'équation de tout cercle et de toutes droites dans $\C$ est de la forme

$$\alpha |z|^2+\beta z+\overline{\beta}\overline{z}+\gamma =0,$$

pour des nombres $(\alpha,\gamma)\in \R^2$ et $\beta\in \C$ propre à la droite/cercle.

:::{admonition} Solution 
:class: dropdown
Un cercle admet une équation de la forme $|z-z_0|=R$ pour $z_0\in \C$ et $R\in \R$. Celle-ci se réécrit

$$|z-z_0|=R \iff |z-z_0|^2=R^2 \iff (z-z_0)(\overline{z-z_0})=R^2,$$
$$\iff z\overline{z} -z\overline{z_0}-z_0\overline{z} +|z_0|^2- R^2 =0,$$

qui est bien de la forme demandée.

Une droite admet une équation de la forme $aRe(z)+bIm(z)+c=0$ pour $(a,b,c)\in \R^2$. Celle-ci se réécrit, en posant $x:=Re(z)$ et $y=Im(z)$, comme

$$aRe(z)+bIm(z)+c=0 \iff ax+by+c=0\iff Re(ax+by)+c=0,$$
$$\iff Re\left(ax+by+(ay-bx)i\right)+c=0\iff \frac{a-ib}{2}z+\frac{a+ib}{2}\overline{z}+c=0,$$

qui est bien de la forme demandée.
:::

```

```{exercise}
:label: geometrie_cercle
:class: dropdown
Représenter graphiquement l'ensemble des $z\in \C$ tels que $|\frac{z-3}{z+3}|=2$, puis l'ensemble des $z$ tels que $|\frac{z-3}{z+3}|<2$

:::{admonition} Solution 
:class: dropdown
Soit $z\in \C$, on raisonne par équivalence :

$$|\frac{z-3}{z+3}|=2\iff |z-3|^2-4|z+3|^2=0\iff (z-3)(\overline{z}-3) - 4(z+3)(\overline{z}+3)=0 $$
$$\iff -3|z|^2-15z-15 \overline{z}-27=0\iff |z|^2+5z+5\overline{z}+9=0$$
$$\iff |z+5|^2=25-9 \iff |z+5|=4$$

où l'on a utilisé les calculs de l'exercice précédents pour la dernière ligne. On reconnait alors l'équation d'un cercle de centre $-5$ et de rayon $4$.

Pour la deuxième moitié de la question, l'on reprend les calculs avec une inégalité.

On aboutit alors à 

$$ |\frac{z-3}{z+3}|<2\iff |z+5|>4.$$

Il s'agit alors du complementaire du disque.
:::

```

### Topologie dans le plan complexe et notion de convergence

::::{prf:definition} Limites et propriétés usuelles
:class: dropdown
 Soit $(z_n)\in \C^\N$, $z_\infty\in \C$, $f: \C\to \C$ et $l\in \C$.
 
On dit que $(z_n)$ converge vers $z_\infty$, noté $\lim\limits_{n\to \infty} z_n=z_\infty$ ou encore $z_n\underset{n\to \infty}{\to} z_\infty$, si 

$$\forall \epsilon>0,\exists N_0, \forall n>N_0, |z_n-z_\infty|<\epsilon.$$
    

On dit que $f$ admet une limite en $z_0$ si

$$\forall \epsilon>0,\exists \eta>0, \forall z\in \C, |z-z_0|\leq \eta \Rightarrow |f(z)-l|\leq \epsilon.$$

On le note alors $\lim\limits_{z\to z_0} f(z)=l$ ou encore $f(z)\underset{z\to z_0}{\to} l$.


Enfin, on dira que $f$ est continue en $z_0$ si $\lim\limits_{z\to z_0} f(z)=f(z_0)$.

```{prf:proposition}
La limite (d'une suite ou d'une fonction), si elle existe, est unique.

L'opération "prendre la limite" est stable par somme, produit et composition (lorsque cela est possible).

Si $z_0=(x_0,y_0)$, alors $f$ continue en $z_0$ est équivalent à ce que $(x,y)\mapsto P(x,y)$ et $(x,y)\mapsto Q(x,y)$ soient continues en $(x_0,y_0)$.

Comme la topologie est métrique, pour montrer que $\lim\limits_{z\to z_0} f(z)=l$, il suffit de montrer que pour toute suite $z_n\to z_0$ l'on a que $f(z_n)\to l$.
```
```{danger}
Pour une fonction de deux variables P, la continuité par rapport à chaque variable en un point ne suffit pas pour obtenir la continuité vu comme une fonction de deux variables :

$$\left\{\begin{matrix}
    x\mapsto P(x,y_0)& \text{ continue en }x_0\\
    y\mapsto P(x_0,y)& \text{ continue en }y_0\\
\end{matrix}\right.\not\Rightarrow (x,y)\mapsto P(x,y)\text{ continue en }(x_0,y_0)$$
```
::::

::::{prf:definition} Ouverts, Fermés, Anneaux, Ensembles connexes et Domaines

Soient $z_0\in \C$ et $(r,R)\in \R^*_+$. On appelle 
- _disque ouvert_ de centre $z_0$ et de rayon $r$ l'ensemble $B(z_0,r):=\{z\in \C, |z-z_0|<r\}$.
- _disque fermé_ de centre $z_0$ et de rayon $r$ l'ensemble $\overline{B}(z_0,r):=\{z\in \C, |z-z_0|\leq r\}$.
- _disque pointé_ de centre $z_0$ et de rayon $r$ l'ensemble $\{z\in \C, 0<|z-z_0|<r\}$.
 - _anneau_ de centre $z_0$, de rayon intérieur $r$ et de rayon extérieur $R$ l'ensemble défini par $A(z_0,r,R):=\{z\in \C, r<|z-z_0|<R\}$.

On rappelle que pour un espace métrique, on appelle ouvert tout ensemble qui peut s'écrire comme une union quelconque de disques ouverts.

- Ensemble _connexe_ tout ensemble $\Omega \subset \C$ tel que les seuls ensembles ouvert et fermé dans $\Omega$ sont $\emptyset$ et $\Omega$.
- Ensemble _simplement connexe_ tout ensemble qui peut se "déformer" continument (au sens de l'homotopie, H.P.) en un seul point.
- _Domaine_ tout ouvert $\Omega$ connexe.

:::{prf:remark}
:class: dropdown
La définition d'un domaine est là pour assurer qu'il y ait toujours, pour deux points de l'ensemble, une suite de segment reliant les deux points, ou encore pour assurer qu'il soit possible de découper l'ensemble en petits triangles tous reliés. Ceci permettra ensuite de construire des primitives (opération non triviale pour des fonctions à valeur complexes), et de montrer des propriétés intégrales sur les fonctions dérivables (théorème de Cauchy).
:::
::::



::::{prf:example}
:label: ensemble_connexe
:class: dropdown
Intuitivement, un ensemble connexe est un ensemble en un seul morceau, et un ensemble simplement connexe est un ensemble en un seul morceau sans trou ou saut infinitésimal.



```{figure} connexe_1.png
:alt: fig_connexe_1
:width: 400px
:align: center

Ensembles connexes non simplement connexe (graphe de $x\in \R_+\to \sin(\frac{1}{x})$ réuni avec $\{0\}\times [0,1]$)
```

```{figure} connexe_2.png
:alt: fig_connexe_2
:width: 400px
:align: center

Ensembles connexes non simplement connexe (un anneau)
```

```{figure} connexe_3.png
:alt: fig_connexe_3
:width: 400px
:align: center

Ensembles connexes simplement connexe
```

```{figure} connexe_4.png
:alt: fig_connexe_4
:width: 400px
:align: center

Ensembles connexes simplement connexe
```

::::

### Convergence fonctionnelle

Rappelons quelques critères de convergence absolue de séries de nombres, qui nous permettrons d'obtenir des convergences de séries de fonctions.

::::{prf:proposition} Convergence de séries numériques
:class: dropdown
 On rappelle qu'on dit qu'une série $\sum a_n$ de terme général $(a_n)$ _converge_ si la suite des sommes partielles $(\sum_{k=0}^n a_k)$ converge (et on appelle la limite _limite de la série_, noté $\sum_{n=0}^\infty a_n$). On dit que la série $\sum a_n$ _converge absolument_ si la série  $\sum |a_n|$ de terme général $(|a_n|)$ _converge_ (et on peut montrer que ceci implique la convergence de la série $\sum a_n$).
 
On considère $(u_n)$ et $(v_n)$ deux suites de nombres complexes.

- (Théorème de comparaison) Si $|u_n|=O(|v_n|)$ et que $\sum |v_n|$ converge, alors $\sum u_n$ est absolument convergente. 

-  Si $|u_n|=O(|v_n|)$ et que $\sum |u_n|$ diverge, alors $\sum |v_n|$ diverge.  

- Si $u_n\sim v_n$, alors $\sum |v_n|$ et $\sum |u_n|$  sont de même nature.

- (Critère de D'Alambert) Si $u_n$ ne s'annule pas à partir d'un certain rang et que $\limsup\limits_n |\frac{u_{n+1}}{u_n}| = L<1$, alors $\sum u_n$ est absolument convergente.

- (Critère de Cauchy - **Fondamental pour les séries entières**)
_On rappelle que pour les suites de nombres réels $(a_n) \in \R^\N$, les nombres_

$$\limsup\limits_n a_n := \lim\limits_{n\to \infty} \sup\limits_{k\geq n} a_n = \inf\limits_{n\in \N} \sup\limits_{k\geq n} a_n,$$
$$\liminf\limits_n a_n := \lim\limits_{n\to \infty} \inf\limits_{k\geq n} a_n = \sup\limits_{n\in \N} \inf\limits_{k\geq n} a_n$$

_existent toujours, et valent la limite des $a_n$ lorsque cette dernière existe._

Si $\limsup\limits_n|u_n|^{\frac{1}{n}} <1$, alors $\sum u_n$ est absolument convergente.

:::{prf:proof}
- Ce résultat est une transcription du principe que pour une suite croissante, la convergence est équivalente à une majoration.

-  Supposons que $u_n$ ne s'annule pas à partir d'un certain rang et que $\limsup\limits_n |\frac{u_{n+1}}{u_n}| = L<1$. Prenons alors $L<\lambda<1$, alors pour un certain rang N, $\sup\limits_{k\geq N}|\frac{u_{n+1}}{u_n}| \leq \lambda$. Ainsi, pour tout $k\geq N$, $|\frac{u_{k+1}}{u_k}| \leq \lambda$ et donc $\forall k\geq N, |u_k|\leq \lambda^{k-N}u_N$. Par comparaison (le point précédent) avec la série géométrique, $\sum u_n$ converge absolument.

- Il s'agit de faire un raisonnement très similaire au précédent pour obtenir une majoration par une série géométrique.
:::

::::


::::{prf:definition}

Soit $X\subset \C$ un ensemble, $f_n : X \to \C$ et $f:X\to \C$ des fonctions.

On dit que $(f_n)$ _converge simplement_ vers f si $\forall z\in X, f_n(z)\underset{n\to \infty}{\to}f(z)$.


On dit que $(f_n)$ _converge uniformément_ vers f si $\sup\limits_{z\in X}|f_n(z)-f(z)|\underset{n\to \infty}{\to}0$.

On remarquera que la convergence uniforme implique la convergence simple, mais que l'inverse n'est pas vrai en général.
:::{prf:proposition}
:class: dropdown
- Si $X$ est un espace topologique, et que $(f_n)$ est une suite de fonction continue qui converge **uniformément** vers une fonction f, alors f est continue.
- (**convergence dominé**) Si $f_n : X\subset \R \to \C$ sont des fonctions mesurables (par exemple continue) converge simplement et qu'il existe $h$ intégrable tel que presque partout, $|f_n(z)|\leq h(z)$, alors 

$$\int_X f_n(x)dx \to \int_X f(x)dx.$$
Les hypothèses sont vérifiées en particulier si les $f_n$ sont continues, convergent uniformément et que $X=[a,b]$ est un segment de $\R$.
- Si $\Omega$ est un ouvert de $\C$ et que $f_n, f : \Omega \to \C$ sont des fonctions définies sur $\Omega$. Alors nous avons l'équivalence suivante 

$$f_n \text{ converge uniformement sur tout compact }K\text{ de } \Omega$$
$$\iff$$
$$f_n \text{ converge uniformement sur toute boule ferm\'e } \overline{B}(a,r)\subset\Omega$$
```{prf:proof}
- La continuité de f est un résultat classique, qui se résout bien avec un raisonnement de type epsilon-delta.
- Il s'agit d'un résultat vu dans le cours d'intégration. Pour le cas particulier, on pourra montrer que les fonctions sont uniformément bornées.
- Il s'agit d'un résultat classique de manipulation de compact. Un sens est évident puisque les boules fermées sont compactes. La réciproque s'obtient en recouvrant le compact $K$ par une union finie de boules fermées incluse dans $\Omega$.
```
:::

Soit $f_n : X\to \C$ une suite de fonction.
- On dit que $\sum f_n$ _converge (simplement)_ si pour tout $z\in X$,  $\sum f_n(z)$ converge. 
- On dit que $\sum f_n$ _converge absolument_ si pour tout $z\in X$,  $\sum f_n(z)$ converge absolument.
- On dit que $\sum f_n$ _converge uniformément_ si la suite des sommes partielles converge uniformément. 
- On dit que $\sum f_n$ _converge normalement_ si la série des normes $\sum ||f_n||_\infty$ converge.

La convergence normale est le type de convergence le plus fort, et si $\sum f_n$ converge normalement, alors elle converge uniformément.
    
:::{prf:example}
:class: dropdown
Montrons la convergence normale sur tous compacts de la boule $\Omega =B(0,1)$ des séries $z\mapsto \sum z^n$ et $z\mapsto\sum n^a z^n$.

Prenons $r<1$, et considérons le compact $K=\overline{B}(0,r)$ (tout compact de $\Omega$ est inclut dans une telle boule). Alors, pour $f_n(z)=z^n$, on a que $||f_n(z)||_\infty =r^n$. Comme la série $\sum r^n$ converge, la série $\sum f_n$ converge normalement. 

Pour $f_n(z)=n^az^n$, nous allons utiliser le critère de D'Alembert. Encore une fois, sur $K=\overline{B}(0,r)$, on a que $||f_n||_\infty = n^ar^n=: u_n$. Comme

$$\lim\limits_{n}\frac{u_{n+1}}{u_n}=\lim\limits_{n}\left(\frac{n+1)}{n}\right)^a r=r<1,$$

la série $\sum f_n$ converge normalement sur tous compacts.
:::
::::