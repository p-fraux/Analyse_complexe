## Exemple d'application
$\newcommand{\R}{\mathbb{R}}$
$\newcommand{\Q}{\mathbb{Q}}$
$\newcommand{\N}{\mathbb{N}}$
$\newcommand{\C}{\mathbb{C}}$
$\newcommand{\Z}{\mathbb{Z}}$
### Equations différentielles

La transformée de Laplace permet de simplifier la résolution des équations différentielles linéaires à coefficients constants. Considérons ainsi l'équation 

$$\left\{\begin{matrix}
    y^{(n)}(t) + a_{n-1} y^{(n-1)}(t)&+ ....+ a_0y(t)= f(t)\\
    y(0)=b_0&\\
    y'(0)=b_1&\\
    \vdots&\\
    y^{(n-1)}(0)=b_{n-1}&
\end{matrix}\right.$$

Le raisonnement pour résoudre ce type de problème est toujours le même (il s'agit d'effectuer une analyse-synthèse en supposant que la solution est bien transformable, puis en le vérifiant à postériori). En effet, si $y$ solution et est transformable, on sait que 

$$ TL(y)[p]=Y[p],$$
$$ TL(y^{(k)})[p] = p^kY[p]-p^{k-1}y(0^+)-...-y^{(k-1)}(0^+).$$

Donc 

$$TL(\sum_{k=0}^n a_ky^{(k)})[p] = \sum_{k=0}^n a_k\left(p^kY[p]-\sum_{i=0}^{k-1}p^{k-1-i}y^{(i)}(0^+)\right)$$

où $a_n=1$

$$= \left(\sum_{k=0}^n a_kp^k\right) Y[p] - \sum_{k=0}^n\sum_{i=0}^{k-1}a_kb_i  p^{k-1-i} $$

Comme $y$ est solution, $y^{(i)}(0^+)=b_i$

$$TL(\sum_{k=0}^n a_ky^{(k)})[p] =H(p)Y[p] + P[p]$$


Avec $H$ et $P$ deux fonctions polynomiales. Comme $y $ est solution, $TL(\sum_{k=0}^n a_ky^{(k)}) = TL(f)$. Nous obtenons donc un problème algébrique beaucoup plus simple en $Y$ :

$$H(p)Y(p)=P(p)+TL(f).$$

Ceci se réecrit

$$ Y(p) = \frac{P}{H}[p] + \frac{1}{H(p)}\times TL(f)[p]$$

Nous avons alors deux termes à inverser. Commençons par la fraction rationnelle. En trouvant les racines complexe de $H$ avec leur multiplicité, nous savons que 

$$\frac{P}{H}[X]=\frac{P(X)}{\prod_{i=1}^r(X-p_i)^{k_i}}$$

où les $p_i$ sont les racines (distinctes) d’ordre $k_i$. Une fois trouvé les racines, nous pouvons effectuer une décomposition en élément simple. Il existe alors $(A_{i,k})$ tels que 

$$\frac{P}{H}[X]= \sum_{i=1}^r \left[\frac{A_{i,1}}{p-p_i}+\frac{A_{i,2}}{(p-p_i)^2}+...+\frac{A_{i,k_i}}{(p-p_i)^{k_i}}\right]$$

En utilisant alors les tables, nous avons directement que

$$TL^{-1}(\frac{P}{H})(t)=\sum_{i=1}^r e^{p_i t}\left[A_{i,1}+A_{i,2}t+...+A_{i,k_i}t^{k_i}\right]$$

Pour inverser le deuxième terme, nous appliquons la méthode ci-dessus pour trouver $h=TL^{-1}(\frac{1}{H})$. Nous aurons alors que

$$TL^{-1}(\frac{1}{H}\times F)[t] = \int_0^t f(u)h(t-u)du.$$

La solution finale du problème est donc

$$y(t)=\sum_{i=1}^r e^{p_i t}\left[A_{i,1}+A_{i,2}t+...+A_{i,k_i}t^{k_i}\right]+ \int_0^t f(u)h(t-u)du.$$

::::{exercise}
:label: exer_transformation_edo
 Résoudre l'équation différentielle

$$y''(t)+y'(t)-2y(t)=2e^{3t}$$

avec comme condition initiale $y(0)=2$ et $y'(0)=-1$.

:::{admonition} Solution
:class: dropdown
On passe dans le domaine de Laplace, où l'on a 

$$TL(y)=Y,\qquad TL(y')=pY-2\qquad TL(y'')=p^2Y-2p+1.$$

Donc l'équation devient

$$(p^2Y-2p+1)+(pY-2)-2Y=\frac{2}{p-3} $$

ou encore

$$Y=\left((\frac{2}{(p-3)}+2p+1\right)\frac{1}{p^2+p-2}$$

On effectue alors une décomposition en élément simple du membre de droite $\frac{2+2p^2-6p+p-3}{(p-3)(p^2+p-2)}=\frac{2p^2-5p-1}{(p-3)(p^2+p-2)}$.

On trouve

$$\frac{2p^2-5p-1}{(p-3)(p^2+p-2)}=\frac{1}{5}\frac{1}{p-3} +\frac{2}{3}\frac{1}{p-1} +\frac{17}{15} \frac{1}{p+2}.$$

Ceci nous donne donc la solution, la fonction

$$y(t)=\left(\frac{1}{5}e^{3t}+\frac{2}{3}e^{t}+\frac{17}{15}e^{-2t}\right)Heav(t)$$

    
:::

::::

### Equations aux dérivées partielles

La transformée de Laplace permet de réduire le nombre de variables dont les dérivées interviennent dans l'équation. \newline 
Pour illustrer ce propos, prenons le problème de la corde vibrante. Il s'agit d'un problème bidimensionnel à 2 dimensions (une d'espace et une de temps). Le problème peut s'écrire comme :

$$\left\{\begin{matrix}
    &\frac{\partial^2f}{\partial x^2}-c\frac{\partial^2f}{\partial t^2}=0\\
    \text{Conditions initiales} :&\\
    &f (x , 0) = \varphi(x)\\
    &\frac{\partial f }{\partial t}(x , 0) = \psi(x)\\
    \text{Conditions aux limites} :&\\
    &\lim\limits_{x\to +\infty}f (x , t) = 0\\
    &f(0 , t) = g(t)
\end{matrix}\right.$$
 
 Considerons alors la transformée de Laplace en temps :
 
 $$F(x,p)=\int_0^{+\infty}e^{-pt}f(x,t)dt$$
 
 Alors les propriétés de la transformée permettront d'écrire 
 
 $$TL(\frac{\partial^2}{\partial t^2}f)[p]=p^2F(x,p)-pf(x,0)-\frac{partial}{\partial t}f(x,0) =p^2F(x,p)-p\varphi(x)-\psi(x).$$
 
 De plus, en supposant que les interversions sont légales, on trouve que 

$$TL(\frac{\partial^2}{\partial x^2}f)[p]=\int_0^{+\infty}e^{-pt} \frac{\partial^2}{\partial x^2}f(x,t) dt,$$
$$= \frac{\partial^2}{\partial x^2}\int_0^{+\infty}e^{-pt} f(x,t) dt=\frac{\partial^2}{\partial x^2}F(x,p).$$


 Ce qui nous donne alors le problème équivalent 
 
 $$\frac{\partial^2}{\partial x^2}F(x,p) -\frac{p^2}{c^2} F(x,p)=p\varphi(x)+\psi(x)$$
 
 avec comme condition au limites $$\lim\limits_{x\to +\infty}F(x,p)=0,$$
 
 $$F(0,p)=TL(g).$$
 
 Nous nous sommes bien ramené à une équation différentielle à une seule variable, paramétré par $p$.


