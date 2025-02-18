## Fonctions complexes usuelles
$\newcommand{\R}{\mathbb{R}}$
$\newcommand{\Q}{\mathbb{Q}}$
$\newcommand{\N}{\mathbb{N}}$
$\newcommand{\C}{\mathbb{C}}$
$\newcommand{\Z}{\mathbb{Z}}$

### Applications algébriques

Que ce soit grâce à la nature géométrique du plan complexe ou au fait que ce soit un corps, il est possible de définir de nombreuses applications élémentaires, correspondantes aux opérations élémentaires. Sans nous attarder dessus, rappelons la définition des plus courantes :

$$\begin{array}{|c|c|c|c|}
        \hline 
        \text{Application} & \text{Ensemble}& \text{Nom transformation} & \text{Paramètre} \\
        \text{géométriques}&\text{de définition} & \text{géométrique associé}&\\
        \hline 
        z\mapsto z+a & \C& \text{Translation} & a\in \C\\
         \hline 
         z\mapsto e^{i\theta}z & \C& \text{Rotation} & \theta\in \R\\
         \hline 
         z\mapsto rz & \C& \text{Dilatation} & r\in \R\\
         \hline 
         z\mapsto az+b & \C& \text{Similitude} & (a,b)\in \C^2\\
         \hline 
         z\mapsto \frac{1}{z} & \C\backslash\{0\}& \text{Inversion} & \\
         \hline          
         z\mapsto \frac{az+b}{cz+d} & \C\backslash\{-\frac{c}{d}\}& \text{Homographie} & (a,b,c,d)\in \C^4\\
         \hline 
\end{array}
    $$
    
$$\begin{array}{|c|c|c|c|}
        \hline 
        \text{Application} & \text{Ensemble}& \text{Nom l'application} & \text{Paramètre} \\
        \text{algébriques}&\text{de définition} & &\\
        \hline 
        z\mapsto a & \C& \text{Constante} & a\in \C\\
        \hline 
        z\mapsto az+b & \C& \text{Affine} & (a,b)\in \C^2\\
         \hline 
         z\mapsto az^2+bz+c & \C& \text{Quadratique} & (a,b,c)\in \C^3\\
         \hline 
         z\mapsto \sum_{k=0}^n a_k z^k & \C& \text{Polynomiale, noté } \C[X] & (a_k)\in \C^n\\
         \hline 
         z\mapsto \frac{P(z)}{Q(z)} & \C\backslash\{z\in \C|Q(z)=0\}& \text{Fraction rationnelle} & (P,Q)\in \C[X]^2\\
         \hline 
    \end{array}$$
    
### Séries entières

::::{prf:definition} Série entière
:label: Serie_entiere
On appelle _série entière_ (au point $a\in \C$) toute fonction $f$ de la forme :

$$f :z\mapsto\sum_{n=0}^{\infty} a_n (z-a)^n$$

en tout point en lequel $f$ est bien posée et pour une certaine suite $a_n\in \C$.

Si cette relation n'est vraie que sur un ouvert $\Omega\ni a$, on dira que f est _développable en série entière sur_ $\Omega$. Lorsque cela est le cas, la suite des $a_n$ est unique.
    
:::{prf:example}
:class: dropdown
- Les polynômes sont des séries entières, pour lesquelles $a_n$ est nul à partir d'un certain rang.
- Peut-être plus intéressant, la fonction $z\mapsto \frac{1}{1-z}$ est développable en série entière sur $B(0,1)$ en 0. Rappelons que pour $z\neq 1$,

$$\sum_{k=1}^n z^k=\frac{1-z^{n+1}}{1-z}.$$

Prenons un $z$ tel que $|z|<1$ et notons qu'alors

$$\frac{1-z^{n+1}}{1-z}\underset{n\to \infty}{\to} \frac{1}{1-z}$$

(Pour $|z|\geq1$, la série diverge, puisque le terme général ne tend pas vers 0).
:::

 Soit $(a_n)\in \C^\N$ une suite de nombres complexes.
 
 On appelle _rayon de convergence_ de la série associé le nombre $R$ définit par

$$R:=\sup\left\{r\geq0, \sum a_n r^n \text{ converge}\right\}$$

On appelle _disque de convergence de la série entière en $a$_ le disque $B(a,R)$.
    
:::{prf:theorem} Caractérisation de la convergence
:class: dropdown
Soit $(a_n)\in \C^\N$ une suite de nombres complexes.

On pose 

$$\frac{1}{R_0}=\limsup\limits_n |a_n|^{1/n}.$$

Alors le rayon de convergence de la série associé à $(a_n)$ est $R_0$.  

Plus précisément, pour tout $a$, la série entière ${\displaystyle \sum_{n=0}^\infty a_n(z-a)^n}$ :
- converge absolument pour $z\in B(a,R_0)$,
- diverge pour $|z-a|>R_0$,
- converge normalement sur tous compacts de $B(a,R_0)$.
```{prf:proof}
Pour montrer que $R_0$ est bien le rayon de convergence, il suffit de montrer les trois points du théorème. 

Quitte à translater en posant $w=z-a$, on peut supposer pour la démonstration que $a=0$.

Considérons $r<R_0$ et $r<R<R_0$. Alors comme $\frac{1}{R}>\frac{1}{R_0}$, alors par définition de la limite supérieur, $|a_n|^{1/n} <\frac{1}{R}$ à partir d'un certain rang, et donc que $a_n<\frac{1}{R^n}$ à partir d'un certain rang. Soit alors $z\in B(0,r)$, on vérifie que
    $|a_n z^n|=O(\frac{r^n}{R^n})$. Par théorème de comparaison, la série entière converge absolument, et même normalement sur $\overline{B}(0,r)$, ce qui prouve les points 1 et 3.
    
Maintenant, soit $z$ tel que $|z|>R_0$ et considérons. Comme précédemment, $|a_n|>\frac{1}{|z|^{n}}$ à partir d'un certain rang, et donc $|a_nz^n|>1$ à partir d'un certain rang. Ainsi, la série entière diverge grossièrement, ce qui prouve le point 2. 
```

```{prf:remark}
Pour $|z|=R$, on ne peut rien dire en général. Ainsi, malgré le fait que les trois séries suivantes aient un rayon de convergence égal à 1, on a que :
- $\sum z^n$ diverge quand $|z|=1$,
- $\sum \frac{z^n}{n}$ diverge pour $z=1$ et converge pour $z=-1$ (par critère des séries alternées),
- $\sum \frac{z^n}{n^2}$ converge absolument en $|z|=1$.
```
:::




::::

```{exercise}
:label: serie_entiere
:class: dropdown
Determiner le rayone de convergence de la série entière $\sum (\frac{n+1}{n})^{n^2} z^n$.

:::{admonition} Solution 
:class: dropdown
Comme $|a_n|^{1/n}=(\frac{n+1}{n})^n=(1+\frac{1}{n})^n\to e$, le théorème précédent nous assure que le rayon de convergence de la série entière est égale à $e^{-1}$.
:::

```

Dans le cadre des séries entières, si $\lim\limits_{n\to \infty} |\frac{u_{n+1}}{u_n}|=L$ existe, alors le rayon de convergence de la série est $R=\frac{1}{L}$ (critère de convergence des séries de D'Alembert).



::::{prf:proposition}
:class: dropdown
:label: proposition_serie_entiere
Considérons deux fonctions développables en série entières $f(z)=\sum_{n=0}^\infty a_n(z-a)^n$ et $g(z)=\sum_{n=0}^\infty b_n(z-b)^n$ de rayon de convergence respectif $R_1$ et $R_2$ strictement positif. Alors
- Si $a=b=z_0$, alors $f+g$ est développable en série entière avec $(f+g)(z)=\sum_{n=0}^\infty (a_n+b_n)(z-z_0)^n$ et un rayon de convergence $R\geq \min(R_1,R_2)$.
- Si $a=b=z_0$, alors $f\times g$ est développable en série entière avec $(f\times g)(z)=\sum_{n=0}^\infty\left(\sum_{k=0}^n a_kb_{n-k}\right)(z-z_0)^n$ et un rayon de convergence $R\geq \min(R_1,R_2)$.
- Si $a=g(b)$, alors $f\circ g$ est développable en série entière avec un rayon de convergence strictement positif.

:::{prf:proof}
- Pour le premier point, il s'agit de la convergence de la somme de série. 
- Pour le deuxième, il s'agit du produit de Cauchy de deux séries, les séries entières convergeant absolument sur le disque ouvert de convergence.
- Supposons que $R_1,R_2>0$ pour le dernier point. Comme $g(b)=a$, on peut sans perte de généralité supposer que $a=b=0$ et $g(0)=0$. En travaillant dans $[0,+\infty]$, on a avec le théorème de Tonelli que

$$\sum_{n=0}^\infty |a_n|\left(\sum_{i=0}^\infty |b_i|\times |z|^i\right)^n  = \sum_{n=0}^{+\infty}|a_n| \sum_{i_1,...,i_n \in \N} \prod_{k=1}^n |b_{i_k}z^{i_k}| $$
$$= \sum_{p=0}^{+\infty} \left(\sum_{\underset{i_1+...+i_n=p}{n, i_1,...,i_n}}|a_n|\prod_k |b_{i_k}|\right)|z|^p $$
(comme $b_0=0$, la somme intérieure est en fait une somme finie).

Or, $R_2>0$ implique que la série $\sum_{i=1}^\infty b_iz^i$ est normalement convergente dans le disque $B(0,\frac{R_2}{2})$ et donc que la fonction $z\mapsto \sum_{i=1}^{+\infty} |b_i|z^i$ soit continue comme limite uniforme de fonctions continues (car polynomiale). 

En particulier, il existe $r<R_2$ tel que  $(\sum_{i=0}^\infty |b_i|\times r^i=\sum_{i=1}^{+\infty} |b_i|r^i<R_1$. Pour un tel $r$, les quantités considérées ci-dessus sont toutes finies. Le théorème de Fubini permet alors de conclure (en refaisant le même calcul) que $f\circ g$ est développable en série entières, avec

$$ f\circ g(z) = \sum_{p=0}^{+\infty} \left(\sum_{\underset{i_1+...+i_n=p}{n, i_1,...,i_n}}a_n\prod_k b_{i_k}\right)z^p.$$
    
:::
::::

```{exercise}
:label: serie_entiere_fraction
:class: dropdown
Soient $P,Q \in \C[X]$ deux polynômes, et soit $z_0$ tel que $Q(z_0)=a\neq 0$. Alors la fonction rationnelle $z\mapsto \frac{P(z)}{Q(z)}$ est développable en série entière.

:::{admonition} Solution 
:class: dropdown
Par produit, il suffit de montrer que $z\mapsto \frac{1}{Q(z)}=\frac{1}{a+(Q(z)-a)}=\frac{1}{a}\frac{1}{1-(a-Q(z))/a}$ est développable en série entière. Ceci est vrai par composition de la fonction $z\mapsto \frac{1}{1-z}$ avec un polynôme s'annulant en $z_0$.
:::

```

```{exercise}
:label: partition
:class: dropdown
Le but de cet exercice est de démontrer qu'il n'existe aucune partition non triviale de $\N$ formée de suites arithmétiques de raison différentes, c'est-à-dire qu'il n'existe pas de partition (union disjointe) de la forme 

$$\N=S_1\bigsqcup S_2\bigsqcup \cdots \bigsqcup S_m,$$

avec $m\geq 2$, $S_j:=\{a_j+k d_j, k\geq 0\}$ où $a_1,...,a_n\in \N$ et $1<d_1<d_2<\cdots<d_m$ entiers.

a) Par l'absurde, supposons qu'une telle partition existe. En déduire que pour tout $|z|<1$, on aurait

$$\frac{1}{1-z}=\frac{z^{a_1}}{1-z^{d_1}}+\frac{z^{a_2}}{1-z^{d_2}}+\cdots +\frac{z^{a_m}}{1-z^{d_m}}$$

:::{admonition} Solution a)
:class: dropdown
Si une telle partition existait, l'on aurait

$$\frac{1}{1-z}=\sum_{i=0}^{+\infty} z^{i}=\sum_{j=0}^m\sum_{i\in S_j}z^i $$

Car pour une série qui converge absolument, l'ordre de sommation n'importe pas

$$\frac{1}{1-z}=\sum_{j=1}^m\sum_{k=0}^{+\infty}z^{a_j}(z^{d_j})^k.$$
:::

b) Conclure à une absurdité à l'aide d'une suite $(z_n)\subset D(0,1)$ telle que $z_n \to e^{\frac{2i\pi}{d_m}}$.

:::{admonition} Solution b)
:class: dropdown
Comme suggéré dans l'énoncé, on prend une telle suite (par exemple $z_n\left(1-\frac{1}{n}\right)e^{\frac{2i\pi}{d_m}}$). Alors, $\frac{1}{1-z_n}\to \frac{1}{1-e^{\frac{2i\pi}{d_m}}}$, et également

$$\forall j\neq m, \frac{{z_n}^{a_k}}{1-{z_n}^{d_k}}\to \frac{e^{\frac{2i\pi a_k}{d_m}}}{1-e^{\frac{2i\pi d_k}{d_m}}}.$$

En revanche, $|\frac{{z_n}^{a_m}}{1-{z_n}^{d_m}}|\to +\infty$. Ce qui est donc une absurdité au vu des règles sur les limites. 
:::
```

    
### Exponentielle complexe et fonction trigonométrique

::::{prf:definition}
 La série entière 
 
 $$f : z \mapsto \sum_{n=0}^{+\infty} \frac{z^n}{n!}$$

a un rayon de convergence infini. On l'appelle exponentielle complexe. On note $exp(z)$ ou $e^z$ son image.

On définit également le cosinus, sinus, cosinus hyperbolique et sinus hyperbolique par :

$$\cos(z)=\frac{e^{iz}+e^{-iz}}{2},\qquad \sin(z)=\frac{e^{iz}-e^{-iz}}{2i},$$
$$\cosh(z)=\frac{e^{z}+e^{-z}}{2},\qquad \sinh(z)=\frac{e^{z}-e^{-z}}{2}.$$

:::{prf:proposition} Formule de passage
:class: dropdown
Un retour à la définition permet de montrer que

$$\left\{\begin{matrix}
    \cos(iz)=\cosh(z)\\ \sin(iz)=i\sinh(z)\\
    \tan(iz)=i\tanh(z)
\end{matrix}\right. \qquad\text{ et }\qquad \left\{\begin{matrix}
    \cosh(iz)=\cos(z)\\ \sinh(iz)=i\sin(z)\\
    \tanh(iz)=i\tan(z)
\end{matrix}\right. $$
:::
::::

```{exercise}
:class: dropdown
:label: annulation_cosinus

Résoudre dans $\C$ les équations 

$$(1) : \cos(z)=2 \qquad (2) : \cosh(z)=0$$ 

Comparer les résultats aux mêmes équations dans $\R$.

:::{admonition} Solution 
:class: dropdown
On revient à la définition du cosinus complexe :

$$\cos(z)=2\iff \frac{e^{iz}+e^{-iz}}{2}=2\iff e^{iz}+e^{-iz}-4=0,$$
$$\iff e^{2iz}+1-4e^{iz}=0,\iff Y^2-4Y+1=0 \qquad \text{ où }Y=e^{iz}.$$

Or les solutions de cette équation quadratiques sont : $Y_±=\frac{4±\sqrt{12}}{2}=2±\sqrt{3}$.
Donc

$$\cos(z)=2\iff e^{iz}=2+\sqrt{3} \text{ ou } e^{iz}=2+\sqrt{3},$$
$$\iff \exists k\in \Z, iz=\ln(2+\sqrt{3}) +2ik\pi \text{ ou } iz=\ln(2+\sqrt{3}) +2ik\pi,$$
$$\iff z\in \{2k\pi+i\ln(2±\sqrt{3}), k\in \Z\}.$$

Pour la deuxième équation, on écrit pour $z\in \C$ que

$$\cosh(z)=0\iff \frac{e^{z}+e^{-z}}{2}=0 \iff e^{z}=-e^{-z},$$
$$\iff e^{2z}=-1=e^{i\pi}\iff \exists k \in \Z, z=i\left(\frac{\pi}{2}+k\pi\right).$$

On remarque que, contrairement à $\R$, ces deux équations ont des solutions complexes.
:::

```

::::{prf:proposition} Propriétés de l'exponentielle
:class: dropdown
- Pour $x\in \R$, la fonction exponentielle définie par sa série entière coïncide avec la fonction exponentielle réelle. En particulier, $f(0)=1$.
- Pour $(z_1,z_2)\in \C^2$, l'application exponentielle vérifie $e^{z_1+z_2}=e^{z_1}e^{z_2}$.
- Pour $z\in \C$, $e^{-z}=\frac{1}{e^z}$.
- Pour $y\in \R$, $e^{iy}\in \mathbb{U}$, et en particulier $e^{x+iy}=\cos(y)e^x+i\sin(y)e^x$ est une décomposition polaire.

:::{prf:proof}
- Les résultats de dérivation sous le signe $\sum$ que nous reverrons en {ref}`série et dérivation` et rappelé en {ref}`annexe_derivation_sous_integrale` montrent que 
        $f'(x)=\sum_{i=0}^{+\infty}\frac{1}{n!} nz^{n-1} = f(z)$.

Comme de plus $f(0) = 1+\sum_{i=1}^{+\infty}\frac{0^n}{n!}=1$, l'application associée à la série entière vérifie les mêmes conditions en 0 et la même équation différentielle que l'exponentielle réelle. D'après le théorème de Cauchy sur les équations différentielles ordinaires, ces deux fonctions coïncident donc.
- Ce deuxième résultat découle directement du produit de Cauchy de deux séries :

$$e^{z_1}e^{z_2}= \left(\sum_{i=0}^{+\infty} \frac{z_1^n}{n!}\right)\left(\sum_{i=0}^{+\infty} \frac{z_2^n}{n!}\right)= \sum_{k=0}^{+\infty} \sum_{n+m=k}\frac{z_1^n}{n!}\frac{z_2^m}{m!},$$
$$=\sum_{k=0}^{+\infty} \sum_{n+m=k}\frac{1}{k!}\frac{k!}{n!m!}z_1^nz_2^m$$
$$=\sum_{k=0}^{+\infty}\frac{1}{k!} \sum_{n=0}^k\begin{pmatrix}
                k\\n
            \end{pmatrix}z_1^nz_2^{k-n}=\sum_{k=0}^{+\infty} \frac{(z_1+z_2)^k}{k!}.$$
- On déduit directement les derniers points du précédent à l'aide du fait que $f(0)=1$ :

$$e^ze^{-z}=e^{z-z}=e^0=1.$$

Comme pour $y\in \R$,
        $\frac{1}{e^{iy}}=e^{-iy}=\overline{e^{iy}},$
        on a bien que $|e^{iy}|^2=\overline{e^{iy}}e^{iy}=1.$

:::
::::

::::{prf:proposition} Noyeau de l'exponentielle
:class: dropdown
Le noyau du morphisme de groupe défini par la fonction exponentielle vérifie :

$$\{z\in \C| e^z=1\} = \{2i k \pi, k\in \Z\}$$
    
:::{prf:proof}
L'inclusion réciproque est évidente. Soit $z\in \C$ tel que $e^z=1$.

En passant par la partie réelle et la partie imaginaire, et en utilisant que $|e^z|=1$, on trouve avec la propriété précédente que $Re(z)=0$, puis que $\cos(Im(z))=1$ et $\sin(Im(z))=0$, ce qui montre que $Im(z)\in 2\pi\Z$. Tout ceci permet de conclure que $z\in  \{2i k \pi, k\in \Z\}$, ce qu'il fallait démontrer.  
:::

::::

### Détermination de l'argument, fonctions associé et fonctions multiformes

Une fonction multiforme est la relaxation de la définition d'applications, où l'on ne demande plus nécessairement que l'image d'un point soit unique. 

```{image} multiforme.png
:name: fig_multiforme
:width: 400px
:align: center
```

::::{prf:definition}
La fonction “argument d’un nombre complexe”, noté $arg$, est une fonction multiforme de $\C^*$ dans $\R$ telle que

$$\forall z\in \C^*, z=|z|e^{i arg(z)}.$$

où l'on a notée abusivement $e^{i arg(z)}$ pour l'image par l'application $w\mapsto e^{iw}$ de n'importe quel élément dans l'image de $z$ par $arg$.


Cette définition utilise de manière implicite que l'exponentielle complexe est surjective de $\C$ dans $\C^*$. Une preuve de cette propriété est donnée ici : {ref}`annexe_surjectivite_exponentielle`

On appelle détermination de rang $k$ de droite de coupure $\R_+$ l'application $arg_k : z\in \C\backslash \R_+\mapsto \theta \in ]2k\pi,2(k+1)\pi[$ qui à un nombre complexe $z$ qui n'est pas dans la demi-droite des réels positifs l'unique valeur $\theta\in ]2k\pi,2(k+1)\pi[$ telle que $z=e^{i\theta}$.

Plus généralement, pour tout angle $\alpha$, on appelle détermination de rang $k$ d'angle de coupure $\alpha$ la détermination de l'angle à valeur dans $]\alpha+2k\pi,\alpha+2(k+1)\pi[$, noté $arg_{k\alpha}$. Sa droite de coupure est alors $D_\alpha$ la demi-droite passant par l'origine et faisant un angle $\alpha$ avec $\R_+$.
    
::::




```{figure} Argument_principal.png
:name: fig_Determination_argument
:width: 500px
:align: center

Représentation graphique de la détermination de rang $k$ de droite de coupure $\R_+$
```

```{figure} Argument_2.png
:name: fig_Determination_argument_2
:width: 500px
:align: center

Représentation graphique de la détermination de rang $k$ de droite de coupure $D_\alpha$
```

:::{prf:remark}
:class: dropdown
- On appelle droite de coupure la droite $D_\alpha$.
- Il est possible à partir d'une détermination de donner une unique valeur de l'argument sur $\C^*$. Une telle fonction ne sera alors plus continue (pour s'en convaincre, approcher l'angle de coupure par le "bord inférieur" et par "bord supérieur".
- Le point O origine de la coupure est appelée point de branchement ou point de ramification. Il est vain de chercher à lui attribuer un argument, puisqu'il n'appartient pas à l'image de l'exponentielle complexe.
- La représentation de la coupure en pointillé dans les figures {ref}`fig_Determination_argument` et {ref}`fig_Determination_argument_2` propose une stratégie de contournement de la droite de coupure lorsque l'on construira des contours d'intégration dans {ref}`Cauchy`.
- Lorsque l'on manipulera des chemins fermés entourant le point de branchement, cela reviendra à un changement de détermination (changement de spire du ressort). 
- On appelle $arg_{k,-\pi}$ la détermination principale de l'argument et on le note $Arg$. Si $x=Re(z)$ et $y=Im(z)$, alors pour $z\notin \R_-$, on a $Arg(z)=2\arctan\left(\frac{y}{x+\sqrt{x^2+y^2}}\right) \in]-\pi,\pi[$.
:::


:::{prf:definition}
- On appelle détermination de rang k de la _puissance_ $\frac{1}{n}$ l'application $ z\in C\backslash D_\alpha \mapsto |z|^{1/n} e^{\frac{i}{n}arg_{k,\alpha}(z)}$. Par composition, cela permet de définir des fonctions puissances rationnelles, puis par continuité de l'exponetielle de définir des fonctions puissances réelles.
- On appelle détermination de rang k du _logarithme_ l'application $\log_{k,\alpha} z\in C\backslash D_\alpha \mapsto \ln(|z|) +i arg_{k,\alpha}(z)$.
- On appelle détermination de rang k de la fonction _puissance_ complexe l'application $ z\in C\backslash D_\alpha \mapsto e^{\beta arg_{k,\alpha}(z)}$ pour $\beta \in \C$.

:::