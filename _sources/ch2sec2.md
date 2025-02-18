
## Théorème de Cauchy et conséquences
$\newcommand{\R}{\mathbb{R}}$
$\newcommand{\Q}{\mathbb{Q}}$
$\newcommand{\N}{\mathbb{N}}$
$\newcommand{\C}{\mathbb{C}}$
$\newcommand{\Z}{\mathbb{Z}}$

(cauchy)=
### Théorème de Cauchy

::::{prf:theorem}
Soient $f$ une fonction holomorphe sur un ouvert $\Omega$ de $\C$ non vide et $D\subset\Omega$ un domaine simplement connexe

:::{margin}
pour nous il s'agira d'un ouvert "sans trou" intérieur
:::
de contour $C$. Alors

$$\int_C f(z)dz=0$$

La propriété reste vrai si $f$ est holomorphe sur $D\backslash \{z_0\}$ et continu en $z_0$.

```{prf:proof}

La preuve élémentaire est relativement longue et utilise un découpage du domaine en triangle (on pourra par exemple aller voir {cite}`rudin1998analyse` pour les détails). Nous utiliserons le résultat plus avancé qu'est le théorème de Green Riemann, mais il n'est pas nécessaire à la preuve. Rappelons que ce théorème énonce que si $C^+$ est le parcours de $C$ dans le sens direct, alors 

$$\int_{C^+} Adx+bdy=\int\int_D\left(\frac{\partial B}{\partial x}-\frac{\partial A}{\partial y}\right)dxdy.$$

Or maintenant, nous avions vu que l'on pouvait réécrire 

$$\int_{C^+} f(z)dz = \int_{C^+} Pdx-Qdy + i\int_{C^+} Qdx+Pdy$$

Finalement, la caractérisation des fonction $\C$-dérivable (conditions de Cauchy) énoncés dans le théorème {prf:ref}`conditioncauchy` nous donne que 

$$\left\{\begin{matrix}
            \frac{\partial P}{\partial x}&=\frac{\partial Q}{\partial y}\\
            \frac{\partial P}{\partial y}&=-\frac{\partial Q}{\partial x}
        \end{matrix}\right.$$

En combinant ces trois résultats, nous avons bien démontré le théorème.
```

::::


:::{prf:axiom} A propos du sens de parcours 
On définit le sens de parcours direct.
Pour cela, on prend le vecteur normal $\vec{n}$ pointant vers l'intérieur du domaine. Puis on trouve un vecteur tangent $\vec{\tau}$ à la courbe $C$ qui vérifie $\langle \vec{\tau},\vec{n}\rangle ={\bf +} \frac{\pi}{2}$, et l'on parcours la courbe en suivant l'orientation indiqué par ce vecteur.
:::

::::{prf:corollary} Généralisation aux ensembles avec $n-1$ trous
:class: dropdown
Soient $f$ une fonction holomorphe sur un ouvert $\Omega$ de $\C$ non vide et $D\subset\Omega$ un domaine $n$-connexe de contour extérieur $C_1^+$ et de contours intérieurs $C_i^-$. Alors

$$\int_C f(z)dz=\int_{C_1^+}f(z)dz +\int_{C_2^-}f(z)dz+\cdots+\int_{C_n^-}f(z)dz =0.$$

:::{prf:proof}
Sans rentrer dans les détails techniques, l'idée de la preuve consiste à suivre un contour parcourant $C_1$, puis une "orbite de transfert" $\gamma$ jusqu'à $C_2$, parcourir $C_2$ dans le sens indirect, avant de parcourir $\gamma$ dans le sens inverse (puis prendre autant "d'orbite de transfert" que de trous). Nous aurons alors un contour d'un ensemble simplement connexe puisque nous aurons relié les trous à l'exterieur, sur lequel nous pourrons appliquer le théorème de Cauchy, avant de remarquer que les contribution des transferts se compensent. Visuellement, on suit un parcours de la forme suivante :

```{image} Cauchy_gen.png
:alt: fig:Cauchy_gen
:width: 300px
:align: center
```
:::
::::

Une conséquance du théorème de Cauchy est qu'une fonction holomorphe admet une primitive au sens complexe. Nous verrons dans la section {ref}`DSE_fonction_holomorphes` de manière surprenante qu'il s'agit en fait d'une équivalence.

::::{prf:corollary} Généralisation aux ensembles avec $n-1$ trous
:class: dropdown
Soit f holomorphe sur un domaine simplement connexe D.

Alors il existe $F$ une fonction holomorphe sur $D$ qui est une primitive de $f$, c'est-à-dire vérifiant 

$$\forall z\in D, F'(z)=f(z).$$

:::{prf:proof}
Soient deux points $a$ et $b$ de $D$. Sous les hypothèses, nous allons pouvoir définir $\int_a^b f(z)dz$.\newline En effet, soient $\gamma_1,\gamma_2$ deux chemins inclus dans $D$ d’origine $a$ et d’extrémité $b$. Alors si l'on parcours $\gamma_1$ suivi du parcours dans le sens inverse de $\gamma_2$, nous aurons un lacet (donc le parcours d'un contour). D'après le théorème de Cauchy, l'intégrale sera alors nulle. Avec la propriété reliant juxtapositions de chemins et intégrales, nous obtenons donc que 

$$\int_{\gamma_1}f(z)dz=\int_{\gamma_2}f(z)dz$$

Nous définissons donc $\int_a^b f(z)dz$ comme la valeur commune des intégrales de $f$ le long d'un chemin reliant $a$ à $b$.

Fixons $u_0\in D$ et posons

$$F :w\in D \mapsto \int_{u_0}^w f(z)dz$$

Montrons que F convient. Donnons nous $w\in D$, et $\gamma$ un chemin quelquonque de $u_0$ à $w$ (qui existe bien puisqu'un ouvert connexe est connexe par arc). Comme $D$ est ouvert, il existe un rayon $r>0$ tel que $B(w,r)\subset D$. Notons pour $h\in B(w,r)$ le chemin $\gamma_h : t\in [0,1]\mapsto w+th$. Toujours avec la propriété même propriété de juxtaposition, pour montrer que $F'(w)=f(w)$ il nous suffit de montrer que $\frac{1}{h}\int_{\gamma_h}f(z)dz \to f(w)$.

Or, $\int_{\gamma_h}f(z)dz=\int_0^1 f(w+th)hdt$ et $ \int_0^1 f(w+th)dt\to f(w)$ (par convergence dominée par exemple). 

Ainsi, en regroupant les arguments, nous avons bien que $F'(w)=f(w)$.
:::
::::




(DSE_fonction_holomorphes)=
### Développement en série entière des fonctions holomorphes (H.P.)

::::{prf:proposition} Formule intégrale de Cauchy
:label: proposition_Cauchy_integral
:class: dropdown
Soit $U\subset \C$ un ouvert et $f\in \mathcal{H}(U)$ une fonction holomorphe. Soit $\overline{B(a,r)}\subset U$ un disque fermé inclu dans $U$ de bord $C$.

Alors 

$$\forall z\in B(a,r), f(z)=\frac{1}{2i\pi}\int_C\frac{f(w)}{z-w}dw.$$
    
:::{prf:proof}
On se fixe dans toute la preuve $z\in B(a,r)$. 

On pose $g:w\mapsto \frac{f(z)-f(w)}{z-w}$. Il est immédiat que $g$ est holomorphe sur $U\backslash\{z\}$ et continu en z. D'après le théorème de Cauchy,

$$0=\int_C g(w)dw= \int_C \frac{f(z)}{z-w} dw - \int_C \frac{f(w)}{z-w}dw,$$
$$= f(z)\int_C \frac{1}{z-w} dw - \int_C \frac{f(w)}{z-w}dw$$

Or 

$$\int_C \frac{1}{z-w}dw = \int_0^{2\pi} \frac{1}{z-a-re^{i\theta}}re^{i\theta}d\theta,$$
$$= \int_0^{2\pi} -\frac{1}{1-\frac{z-a}{re^{i\theta}}}d\theta= \int_0^{2\pi} -\sum_{k=0}^{+\infty}\left(\frac{z-a}{re^{i\theta}}\right)^kd\theta,$$
$$= -\sum_{k=0}^{+\infty}\int_0^{2\pi} -\left(\frac{z-a}{r}\right)^k e^{-ik\theta}d\theta= -\sum_{k=0}^{+\infty}\left(\frac{z-a}{r}\right)^k \int_0^{2\pi} e^{-ik\theta}d\theta,$$
$$= 2i\pi +\sum_{k=1}^{+\infty} 0$$

**Remarque :** l'interversion dans les calculs est justifié par le théorème de Fubini, car $[0,2\pi]$ est borné, et  puisque $|z-a|<r$, on aura que $\sum |\frac{z-a}{r}|^k<+\infty $.

Donc finalement,

$$2i\pi f(z) = \int_C \frac{f(w)}{z-w}dw $$
:::
::::

::::{prf:corollary} Développement en série entière
:class: dropdown
Soit $f$ une fonction holomorphe, alors $f$ est développable en série entière au voisinage de tout point intérieur.

:::{prf:proof}
Il s'agit comme dans la preuve de développer en série entière $\frac{1}{z-w}$ dans $\int_C\frac{f(w)}{z-w}dw$, puis de justifier l'interversion avec le théorème de Fubini-Tonelli (en majorant localement $f$ par une constante par exemple).
:::
::::

:::{prf:remark}
Ceci prouve que toute fonction holomorphe est analytique (donc infiniment dérivable). En particulier, l'équivalence énoncée dans la section précédente en découle, puisque si $f$ a une primitive $F$, alors $F$ est holomorphe, et donc admet une dérivée seconde.
:::

### Développement en série de Laurent

::::{prf:proposition} Développement de Laurent sur les anneaux
:label: proposition_Laurent
Soit $f$ holomorphe sur un anneau $A(z_0,r,R)$, alors il existe $(a_n, b_n)$ tels que 

$$\forall z\in A(z_0,r,R), f(z)=\sum_{k=1}^{+\infty}\frac{b_k}{(z-z_0)^k} +\sum_{k=0}^{+\infty}a_k(z-z_0)^k$$

et ces coefficients sont uniques, déterminé (pour n'importe quel cercle inscrit dans la couronne) par 
    $a_n=\frac{1}{2i\pi}\int_C \frac{f(z)}{(z-a)^{n+1}}dz$ et $b_n=\frac{1}{2i\pi}\int_C f(z)(z-a)^{n-1}dz$.
:::{prf:proof}
On pose $g:w\mapsto \frac{f(z)-f(w)}{z-w}$. 

En notant $C_r$ et $C_R$ les cercle entourant l'anneau, on a d'après la généralisation du théorème de Cauchy que 

$$0=\int_{C_R^+}g(z)dz +\int_{C_r^-}g(z)dz = 2i\pi f(z) - \int_{C_R^+}\frac{f(w)}{z-w}dw + 0- \int_{C_r^-}\frac{f(w)}{z-w}dw$$

Car $w\mapsto \frac{1}{z-w}$ est holomorphe sur $B(z_0,r)$

$$0=2i\pi f(z) - \sum_{k=0}^{+\infty} \tilde{a_n} (z-z_0)^n - \sum_{k=0}^{+\infty}\frac{\tilde{b_n}}{(z-z_0)^n}.$$

Pour montrer la caractérisation, il s'agit d'effectuer une inversion série-intégrale, par convergence dominée par exemple. En effet, pour $C$ un cercle centré en l'origine, 

$$\int_C z^ndz=\int_0^{2\pi}e^{in\theta}ie^{i\theta}d\theta = \left\{\begin{matrix}0&\text{ si } n\neq -1\\
        2i\pi &\text{ si } n=-1
    \end{matrix}\right.$$
:::
::::



````{exercise}
:label: exer_residu_c
 A l'aide du contour suivant, calculer $I=\int_0^{+\infty} e^{ix^2}dx$. En déduire la valeur de l'intégrale impropre $\int_{0}^{+\infty}\sin(x^2)dx$.

:::{image} Residu_c.png
:alt: fig:Residu_c
:width: 300px
:align: center
:::

:::{admonition} Solution 
:class: dropdown
 
 Comme $z\mapsto e^{iz^2}$ est holomorphe comme composition de fonction holomorphe, et que le contour proposé entoure un domaine simplement connexe, nous pouvons applique le théorème de Cauchy :

$$\int_{\gamma_1\cup\gamma_2\cup\gamma_3} e^{iz^2}dz =0$$

Par définition de l'intégrale impropre, et en prenant comme paramétrisation $\gamma_1 : t\in [0,R]\mapsto t$, nous avons immédiatement que

$$\int_{\gamma_1} e^{iz^2}dz = \int_0^Re^{it^2}dt \to \int_0^{+\infty} e^{it^2}dt.$$

Le traitement du chemin $\gamma_2$ est plus complexe, puisque les lemmes de Jordan ne suffisent pas. Nous aurons besoin du fait suivant :

**Fait :** $\forall u\in[0,\frac{\pi}{2}], \sin(u)\geq \frac{2u}{\pi}$.

Ce fait est immédiat en remarquant que la fonction sinus est concave sur l'intervalle considéré, et donc au-dessus de ses cordes.

Maintenant, calculons avec la paramétrisation $\gamma_2 : \theta\in[0,\frac{\pi}{4}]\mapsto Re^{i\theta}$ :

$$\left|\int_{\gamma_2}e^{iz^2}dz\right|= \left|\int_0^{\frac{\pi}{4}} e^{iR^2e^{2i\theta}} iRe^{i\theta}d\theta\right|,$$
$$\leq \int_0^{\frac{\pi}{4}} \left|e^{iR^2\cos(2\theta) -R^2\sin(2\theta)} \right|Rd\theta= \int_0^{\frac{\pi}{4}}Re^{-R^2\sin(2\theta)}d\theta,$$
$$\leq \int_0^{\frac{\pi}{4}}Re^{-R^2\frac{4\theta}{\pi}}d\theta$$

d'après le fait précédent,
$$\left|\int_{\gamma_2}e^{iz^2}dz\right|=\left[-\frac{\pi}{4R} e^{-\frac{4R^2}{\pi}\theta}\right]_0^{\frac{\pi}{4}}\leq  \frac{\pi}{4R} \to 0. $$

Enfin, pour $\gamma_3 : t\in [0,R]\mapsto (R-t)e^{i\frac{\pi}{4}}$, on trouve

$$\int_{\gamma_3}e^{iz^2}dz=-\int_0^R e^{-(1-t)^2}e^{i\frac{\pi}{4}}dt = -e^{i\frac{\pi}{4}}\int_0^R e^{-t^2}dt ,$$
$$\to -e^{i\frac{\pi}{4}}\int_0^{+\infty} e^{-t^2}dt = -\frac{\sqrt{\pi}}{2}e^{i\frac{\pi}{4}}.$$

Donc finalement 

$$\int_{0}^{+\infty} e^{ix^2}dx = \frac{\sqrt{\pi}}{2}e^{i\frac{\pi}{4}} $$

Pour l'intégrale impropre, il suffit alors de prendre la partie imaginaire :

$$\int_{0}^{+\infty} \sin(x^2)dx =\frac{\sqrt{2\pi}}{4} $$
:::

````

````{exercise}
:label: exer_residu_f

Soit $a>0$. À l'aide du rectangle de sommets $\{±R,±R +i\frac{a}{2}\}$, calculer $\int_{-\infty}^{+\infty} e^{-x^2}\cos(ax)$.

:::{admonition} Solution 
:class: dropdown
On pose $g : z\mapsto e^{-z^2+iaz}$. Le théorème de Cauchy nous annonce que 

$$0=\int_{-R}^{R} e^{-x^2+iax}dx + \int_0^{\frac{a}{2}} e^{-(R+it)^2+iaR-at}idt + \int_{R}^{-R}e^{-(x+i\frac{a}{2})^2+iax-\frac{a^2}{2}}dx+\int_{\frac{a}{2}}^0e^{-(-R+it)^2-iaR-at}idt$$

Par convergence dominée (dominé par $t\mapsto e^{t^2}$ continue), il est immédiat que

$$\int_0^{\frac{a}{2}} e^{-(R+it)^2+iaR-at}idt\to 0,$$

$$ \int_{\frac{a}{2}}^0e^{-(-R+it)^2-iaR-at}idt \to 0.$$

Maintenant, 
    
$$\int_{R}^{-R}e^{-(x+i\frac{a}{2})^2+iax-\frac{a^2}{2}}dx=-\int_{-R}^Re^{-x^2-\frac{a^2}{4}-\frac{a^2}{2}}dx=-e^{-\frac{3a^2}{4}}\int_{-R}^{R}e^{-x^2}dx\to-\sqrt{\pi}e^{-\frac{3a^2}{4}}$$

Donc finalement,

$$\int_{-\infty}^{+\infty} e^{-x^2}\cos(ax)=Re\left(\int_{-\infty}^{+\infty} g(x)dx\right)=Re(\sqrt{\pi}e^{-\frac{3a^2}{4}})=\sqrt{\pi}e^{-\frac{3a^2}{4}} $$
:::

````