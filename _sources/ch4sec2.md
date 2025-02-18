## Exemples d'applications
$\newcommand{\R}{\mathbb{R}}$
$\newcommand{\Q}{\mathbb{Q}}$
$\newcommand{\N}{\mathbb{N}}$
$\newcommand{\C}{\mathbb{C}}$
$\newcommand{\Z}{\mathbb{Z}}$

### Équations récurrentes

La transformée en Z est particulièrement utile dans la résolution d'équation récurrente linéaire. La méthode est toujours la même, nous allons la voit sur un exemple.

:::{admonition} Méthode de résolution (example) :
:class: tip
Considérons pour $|a|<1$ l'équation de récurrence

$$y(n)-ay(n-1)=x(n),$$

avec comme entrée du système 

$$x(n)=b^n1_{n\geq0},\qquad \text{ avec }|b|<1$$

On cherche alors à déterminer la transformée en Z de l'entrée du système, tout d'abord en l'exprimant en fonction de la transformée en Z de l'entrée.

```{admonition} Solution 
:class: dropdown
On peut utiliser les propriétés de la transformée en Z pour écrire

$$TZ(b^n1_{n\geq0})[z]=TZ(1_{n\geq0})[\frac{z}{b}]=\frac{1}{1-\frac{1}{\frac{z}{b}}}=\frac{1}{1-\frac{b}{z}}$$

avec comme domaine de convergence $|z|>|a|$.
```

On recherche ensuite la réponse impulsionnelle du système, c'est-à-dire la suite $\left(h(n)\right)$ telle que pour toute entrée de système $e$, l'on ait $y(n) = e(n) ∗ h(n)$.

```{admonition} Solution 
:class: dropdown
Après transformée en Z, cela revient à trouver H tel que $TZ(y)[z]=TZ(e)[z]H[z]$. Prenons la transformée en Z de l'équation de récurrence avec comme entrée $e$ et utilisons la linéarité et le fait que $TZ(y(n-1))[z]=z^{-1}TZ(y)[z]$, on trouve que

$$TZ(y)-az^{-1}TZ(y)=TZ(e).$$

Ceci se réécrit

$$TZ(y)=TZ(e)\frac{1}{1-\frac{a}{z}}.$$
```
On trouve alors $y$ soit en calculant le produit de convolution (solution numérique), soit en inversant la transformée en Z de $y$ (solution théorique).

```{admonition} Solution 
:class: dropdown
Ici, en supposant $a\neq b$, nous aurons 

$$TZ(y)=\frac{1}{(1-\frac{a}{z})(1-\frac{b}{z})}=\frac{1}{(1-\frac{b}{a})(1-\frac{a}{z})}+\frac{1}{(1-\frac{a}{b})(1-\frac{b}{z})}$$

Et donc 

$$y(n)=\left(\frac{a^n}{(1-\frac{b}{a})}+\frac{b^n}{(1-\frac{a}{b})}\right) 1_{n\geq 0}$$
est une solution de l'équation récurrente linéaire.
```

Il est conseillé à la fin des calculs que l'on obtient bien une solution pour éviter les erreurs de calculs.
:::

### Traitement numérique du signal

Ce point de vue sera creusé plus particulièrement dans le cours éponyme (signal radar, signal numérisé,etc).

Soit $f^*$ qui est issue d'une suite d'impulsion espacée uniformément (d'espacement temporel $T$), mais d'amplitude variable.

En notant $\delta$ une impulsion d'amplitude ayant une intégrale 1 et de durée négligeable on s'intéresse en fait à une fonction  

:::{sidenote}
mathématiquement la limite au sens des distributions de $\delta_W : t\mapsto\frac{1}{W}$ si $0\leq t\leq W$ et 0 sinon
::: 


$$f^*(t)=\sum_{n=0}^{+\infty} f(t)\delta(t-nT) =f(t)Imp(t).$$

Si les calculs sont légaux, nous aurons alors

$$TL(f^*)(p)=\int_0^{+\infty} f(t)Imp(t)e^{-pt}dt$$
$$=\sum_{n=0}^{+\infty}\int_0^{+\infty} f(t)\delta(t+nT)e^{-pt}dt$$

Car $\delta$ est de durée négligeable.

$$=\sum_{n=0}^{+\infty}f(nT)e^{-pnT}$$ 



$$TL(f^*)(p)=TZ(f(nT))[e^{pT}]$$

On voit donc naturellement apparaitre la transformée en Z évalué en $z=e^{pT}$ (le nom de la transformée vient en fait de ce changement de variable !).

