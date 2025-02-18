## Manipuler la transformée de Laplace
$\newcommand{\R}{\mathbb{R}}$
$\newcommand{\Q}{\mathbb{Q}}$
$\newcommand{\N}{\mathbb{N}}$
$\newcommand{\C}{\mathbb{C}}$
$\newcommand{\Z}{\mathbb{Z}}$
$\newcommand{\red}{\color{red}}$


:::::::{tabs}

::::{tab} Propriétées
Notons $f$ et $g$ deux fonctions transformable, on note $F=TL(f)$ et $G=TL(g)$

$$\begin{array}{|c|c|c|c|}
\hline \text{Fonction} & \text{Transformée de Laplace} & \text{Abscisse de convergence (en général)}&\text{Nom}\\
    \hline 
\lambda f+\mu g&\lambda F+\mu G&x_{c}\leq \sup(x_{c}(f),x_{c}(g))&\text{Linéarité}\\
\hline 
f'&p\mapsto pF(p)-f(0^+)&x_{c}(f)&\text{Dérivation causale}\\
\hline 
t\mapsto (-1)^nt^nf(t)&\frac{d^n}{dp^n}F&x_{c}(f)&\text{Dérivation en fréquence}\\
\hline 
t\mapsto \int_0^tf(u)du&p\mapsto\frac{F[p]}{p}&\sup(0,x_{c}(f))&\text{Transformée d'une primitive}\\
\hline 
t\mapsto \frac{f(t)}{t}&p\mapsto\int_p^{+\infty} TL(f)[u]du&x_{c}(f)&\text{Primitive d'une transformée}\\
\hline 
t\mapsto f(t-a)Heav(t-a)&p\mapsto e^{-ap}F[p]&x_{c}(f)&\text{Translation de l'espace}\\
\hline 
t\mapsto e^{at}f(t)&p\mapsto F[p-a]&x_{c}(f)+Re(a)&\text{Translation des phases}\\
\hline 
t\mapsto f(\frac{t}{k})&p\mapsto kF[kp]&\frac{x_{c}(f)}{k}&\text{Similitude}\\
\hline 
t\mapsto \int_{0}^{{\red t}} f(u)g({\red t}-u) du&FG&x_{c}\leq \sup(x_{c}(f),x_{c}(g))&\text{Convolution}\\
\hline 
t\mapsto \sum_{n={\red 1}}^{+\infty}a_n\frac{t^n}{n!}&p\mapsto\sum_{n={\red 1}}^{+\infty}\frac{a_n}{p^n}&&\text{Série entière et transformée}\\
\hline 
\end{array}
$$

On a aussi le Théorème des valeurs initiales :

$$\lim\limits_{t\to 0^+}f(t)=\lim\limits_{p\to +\infty}pF(p)$$

et le Théorème des valeurs finales

 $$\lim\limits_{t\to +\infty}f(t)=\lim\limits_{p\to 0}pF(p)$$
 
::::

::::{tab} Fonctions usuelles

$$\begin{array}{|c|c|c|}
    \hline \text{Fonction} & \text{Transformée de Laplace de }f\times Heav & \text{Abscisse de convergence}\\
    \hline 
    Heav&\frac{1}{p}&x_c=0\\
    \hline
    e^{at}, a\in \C&\frac{1}{p-a}&x_c=Re(a)\\
    \hline
    e^{iwt}, w\in \R&\frac{1}{p-iw}&x_c=0\\
    \hline
    \cosh(at), a\in \C&\frac{p}{p^2-a^2}&x_c=\sup(Re(-a),Re(a))\\
    \hline
    \sinh(at), a\in \C&\frac{a}{p^2-a^2}&x_c=\sup(Re(-a),Re(a))\\
    \hline
    \cos(wt), w\in \R&\frac{p}{p^2+w^2}&x_c=0\\
        \hline
    \sin(wt), w\in \R&\frac{w}{p^2+w^2}&x_c=0\\
        \hline
    t&\frac{1}{p^2}&x_c=0\\
    \hline
    t^n&\frac{n!}{p^{n+1}}&x_c=0\\
    \hline
    t^a, a\in \R&\frac{\Gamma(a+1)}{p^{a+1}}&x_c=0\\
    \hline 
    \end{array}$$

::::

:::::::


````{exercise}
:label: exer_transformation_usuelles
Retrouver les transformées usuelles à l'aides des propriétées.


:::{admonition} Fonction Heaviside (par Calcul)
:class: dropdown
Pour $x<0$, il est immédiat que $Heav(t)e^{-x_0t}\underset{t\to +\infty}\to +\infty$.

En particulier, l'intégrale généralisée diverge grossièrement. De plus, comme pour $x_0>0$, $t\mapsto e^{-x_0t}$ est d'intégrale généralisée convergente. Donc l'abscisse de convergence (simple et absolu) de la fonction $Heav$ est $0$.

Maintenant, prenons $p\in \C$ tel que $Re(p)>0$. Alors

$$TL(Heav)[p]=\int_0^{+\infty} Heav(t) e^{-pt}dt = \left[-\frac{1}{p}e^{-pt}\right]_0^{+\infty}=-0+\frac{1}{p}.$$

:::

:::{admonition} Fonction $t\mapsto t$ et $t\mapsto t^n$
:class: dropdown
On cherche à calculer la transformée de Laplace de $t\mapsto t$. 

$$TL(t)[p]=-TL\left((-t) Heav(t)\right)[p]=-\frac{d}{dp}TL(Heav)[p]=\frac{1}{p^2}.$$

De la même façon, on aura que 

$$TL(t^n)[p]=\frac{n!}{p^{n+1}}.$$

:::

:::{admonition} Fonction $t\mapsto t^\alpha$
:class: dropdown
On cherche à calculer la transformée de Laplace de $t\mapsto t^\alpha$ pour $\alpha \in \R_+$. Pour cela, on écrit 

$$\frac{TL(t^\alpha)[p]}{p}=TL(t\mapsto \int_0^tu^\alpha du)[p] $$
$$=TL(\frac{t^{\alpha+1}}{\alpha+1})[p]=-\frac{1}{\alpha+1}\frac{d}{dp}TL(t^\alpha)[p]$$

Ainsi, $TL(t^{\alpha})$ est solution sur $]x_c,+\infty[$ de l'équation différentielle 

$$y'(p)=-\frac{1}{(\alpha+1)p}y(p).$$

Donc il existe une constante $c$ telle que 

$$TL(t^\alpha)[p]=\frac{C}{p^{\alpha+1}}$$

En regardant en $p=1$, on trouve que 

$$C=TL(t^\alpha)[p]=\int_0^{+\infty} e^{-t}t^{\alpha}dt =: \Gamma(\alpha+1).$$

Ainsi, 

$$ TL(t^\alpha)[p]=\frac{\Gamma(\alpha+1)}{p^{\alpha+1}}.$$

(On peut en fait montrer que cette formule se généralise à $\alpha \in \R$).
:::

:::{admonition} Fonctions $t\mapsto e^{ta}$ et trigonométriques
:class: dropdown
On cherche à calculer la transformée de Laplace de $t\mapsto e^{ta}$, mais également des fonctions trigonométriques. Pour cela, on écrit :

$$TL(e^{ta})[p]=TL(e^{ta}Heav(t))[p]=TL(Heav)[p-a]=\frac{1}{p-a}$$

Ainsi, $TL(e^{iwt})[p]=\frac{1}{p-iw}$, et par linéarité, 

$$2TL(\cosh(wt))[p]=TL(e^{wt}+e^{-wt})[p]=\frac{1}{p-w}+\frac{1}{p+w}=\frac{2p}{p^2-w^2}.$$

De la même manière, on montre que :

$$TL(\cosh(wt))[p]=\frac{p}{p^2-w^2};\qquad TL(\sinh(wt))[p]=\frac{w}{p^2-w^2};$$
$$TL(\cos(wt))[p]=\frac{p}{p^2+w^2};\qquad TL(\sin(wt))[p]=\frac{w}{p^2+w^2}.$$
:::

Calculer la transformée de Laplace de $t\mapsto \frac{\sin(tw)}{t}$ de deux manières (avec une série entière et avec une des propriétés).

:::{admonition} Fonction $t\mapsto \frac{\sin(tw)}{t}$
:class: dropdown
Tout d'abord, à l'aide d'une série entière.

Le fait que $\sin(x)=\sum_{n=0}^{+\infty}\frac{(-1)^nx^{2n+1}}{(2n+1)!}$ permet d'écrire

$$TL(\frac{\sin(wt)}{t})[p]=TL(\sum_{n=0}^{+\infty}\frac{(-1)^nw^{2n+1}t^{2n}}{(2n+1)!})[p], $$
$$=\sum_{n=0}^{+\infty}\frac{(-1)^nw^{2n+1}}{p^{2n+1}(2n+1)}=Arctan(\frac{w}{p}).$$

Ensuite, une deuxième méthode consiste à remarquer que 

$$TL(\sin(wt))[p]=\frac{w}{p^2+w^2},$$

puis à utiliser les propriétés de la transformée de Laplace pour obtenir 

$$ TL\left(\frac{\sin(wt)}{t}\right)[p]=\int_p^{+\infty}\frac{w}{q^2+w^2}dq=[Arctan(\frac{q}{w})]_p^{+\infty}=\frac{\pi}{2}-Arctan(\frac{p}{w})=Arctan(\frac{w}{p}).$$

:::

Calculer la transformée de Laplace de $p \mapsto \frac{1}{(p+1)(p-2)}$
:::{admonition} Solution
:class: dropdown
On décompose la fraction en éléments simples, _ie_ on cherche $\alpha$ et $\beta$ tels que

$$\frac{1}{(p+1)(p-2)}=\frac{\alpha}{p+1}+\frac{\beta}{p-2} .$$

On trouve par la méthode de notre choix (système linéaire ou calcul de $\lim\limits_{p\to p_0}(p-p_0)F(p)$) que $\alpha=-\frac{1}{3}$ et $\beta=\frac{1}{3}$.

Donc l'inverse est 

$$f:t\mapsto -\frac{1}{3}e^{-t}Heav(t)+\frac{1}{3}e^{2t}Heav(t).$$

:::

Calculer la transformée de Laplace de $p\mapsto -\frac{1}{(p-2)^2}$
:::{admonition} Solution
:class: dropdown
Posons $G(p)=\frac{-1}{(p-2)^2}$ et $F(p)=\frac{1}{p-2}$. Alors $F'=G$.

Or,

$$TL^{-1}(F)[t]= e^{-2t}Heav(t).$$

Donc par les propriétés de la transformée de Laplace, on en déduit que

$$TL^{-1}(G)[t]=(-t)e^{2t}Heav(t).$$

:::

Calculer la transformée de Laplace de $p \mapsto \frac{5p+10}{p^2+3p-4}$
:::{admonition} Solution
:class: dropdown
Le dénominateur se factorise en $(p+4)(p-1)$. On décompose la fraction en éléments simples en l'écrivant sous la forme

$$\frac{\alpha}{p+4}+\frac{\beta}{p-1}$$

On trouve alors $\alpha=2$ et $\beta=3$.

Donc l'inverse est 

$$f:t\mapsto 2e^{-4t}Heav(t)+3e^{t}Heav(t).$$

:::
Calculer la transformée de Laplace de $p\mapsto \frac{p-7}{p^2-14p+50}$
:::{admonition} Solution
:class: dropdown
Le discriminant du trinôme du second degré au dénominateur est négatif, donc il n'admet pas de racines. On le met sous forme canonique $ p^2-14p+50=(p-7)^2+1$. Donc

$$TL^{-1}\left(\frac{p-7}{(p-7)^2+1}\right)[t]=e^{7t}TL^{-1}\left(\frac{p}{p^2+1}\right)[t] = e^{7t}\cos(t)Heav(t).$$

:::
Calculer la transformée de Laplace de $p \mapsto \frac{p}{p^2-6p+13}$
:::{admonition} Solution
:class: dropdown

Le discriminant du trinôme du second degré au dénominateur est négatif, donc il n'admet pas de racines. On le met sous forme canonique en écrivant $p^2-6p+13=(p-3)^2+4$. 

Ainsi,

$$\frac{p}{p^2-6p+13}=\frac{p}{(p-3)^2+4}=\frac{p-3}{(p-3)^2+2^2}+\frac{3}{2}\frac{2}{(p-3)^2+2^2}$$


On trouve que l'original recherché est la fonction

$$t\mapsto e^{3t}\cos(2t)Heav(t)+\frac{3}{2}e^{3t}\sin(2t)Heav(t)$$
:::

Calculer la transformée de Laplace de $p\mapsto \frac{e^{-2p}}{p+3}$
:::{admonition} Solution
:class: dropdown
A l'aide du théorème du retard, on trouve que

$$TL^{-1}\left(\frac{e^{-2p}}{p+3}\right)[t]=TL^{-1}\left(\frac{1}{p+3}\right)[t-2]=e^{3(t-2)}Heav(t-2)$$   
:::
````