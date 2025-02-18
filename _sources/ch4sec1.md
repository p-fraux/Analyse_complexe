## Définition et propriétés
$\newcommand{\R}{\mathbb{R}}$
$\newcommand{\Q}{\mathbb{Q}}$
$\newcommand{\N}{\mathbb{N}}$
$\newcommand{\C}{\mathbb{C}}$
$\newcommand{\Z}{\mathbb{Z}}$

::::{prf:definition}
Soit $(u_n)_{n\in\Z}$ une suite de nombres complexe. On définit _la transformée en Z_ de $u$, évalué en $z$ comme la série de Laurent

$$U(z)=TZ(u)[z]:=\sum_{n=-\infty}^{+\infty} u_n z^{-n}$$

On appelle _région de convergence_ l’ensemble des nombres complexes $z$ tels que la série $TZ(u)[z]$ converge.

```{prf:remark} Vocabulaire
:class: dropdown
La transformée que nous venons de définir est également appelée transformée en Z _bilatère_. Lorsqu'on impose en plus que $u$ soit causale (_i.e._ que $u_n=0$ si $n<0$), on parle de transformée en Z _unilatère_.
```

```{prf:proposition} Région de convergence
:class: dropdown
Pour $(u_n)_{n\in\Z}$ une suite, il existe $R^-_u$ et $R^+_u$ tel que la région de convergence absolue soit contenue dans l'anneau $A(R^-_u,R^+_u)$

$$A(R^-_u,R^+_u):=\{z | 0\leq R^-_u<|z|<R^+_u\leq +\infty\}$$

:::{prf:proof}
Il s'agit d'une application directe du critère de Cauchy, qui dit que si $\lim\limits_{n\to +\infty}\sqrt[n]{|z|}$, alors $\sum u_n$ converge absolument.
:::
```

::::

:::{prf:example}
 Si l'on considère $(u_n)=(1_{n\geq 0})$, alors $TZ(u)[z]=\sum_{n=0}^{+\infty}z^{-n}$ converge pour $|z|>1$.
:::

### Propriétées usuelles
Notons $u$ et $v$ deux suites numériques, on note $U=TZ(u)$ et $V=TZ(v)$

$$\begin{array}{|c|c|c|c|}
\hline \text{Suite} & \text{Transformée en Z} & \text{anneau de convergence contient}&\text{Nom de l'opération}\\
    \hline 
a u+b v&a U+b V&A\left(\max(R^−_u,R^-_v),\min(R^+_u,R^+_v)\right)&\text{Linéarité}\\
\hline 
n\mapsto u(n-n_0)&z\mapsto z^{-n_0}U (z )&A(R^−_u,R^+_u)&\text{Translation}\\
\hline 
n\mapsto k^n u(n)&z\mapsto U (\frac{z}{k} )&A(k\times R^−_u,k\times R^+_u)&\text{Changement d'échelle}\\
\hline 
n\mapsto n u(n)&z\mapsto -z\frac{d}{dz}U [z]&A(R^−_u,R^+_u)&\text{Dérivation}\\
\hline 
n\mapsto\sum_{k=-\infty}^{+\infty} u_kv_{n-k}&z\mapsto U(z)V(z)&A(R^−_u,R^+_u)\cap A(R^−_v,R^+_v)&\text{Produit et convolution}\\
\hline 
\end{array}
$$

:::{dropdown} Démonstration
Il s'agit soit de manipuler la définition, en utilisant pour les deux dernière la convergence normale sur les compacts de l'anneau de convergence.

A chaque fois, le domaine proposé nous assure que les calculs qui suivent sont corrects. On se donne $z$ dans ce domaine à chaque fois.

-   La linéarité se montre comme suit :

$$TZ(n\mapsto au_n + bv_n)[z] = \sum_{n=-\infty}^{+\infty}(au_n + bv_n)z^{-n}=a\sum_{n=-\infty}^{+\infty}u_nz^{-n}+ b\sum_{n=-\infty}^{+\infty}v_nz^{-n}=aU(z ) + bV(z ).$$

- La translation revient aussi à la définition

$$TZ (n\mapsto u_{n-n_0})[z] =\sum_{n=-{infty}}^{+\infty} u_{n-n_0}z^{-(n-n_0)-n_0}=z^{-n_0}\sum_{k=-{infty}}^{+\infty} u_kz^{-k}=z^{-n_0}U(z).$$
- Le changement d'echelle est encore similaire :

$$TZ (n\mapsto k^nu_n)[z] =\sum_{n=-\infty}^{+\infty}k^nu_nz^{-n}=U(\frac{z}{k}).$$

- En dérivant termes à termes, ce qui est justifié par le choix du domaine,

$$-z\frac{d}{dz}TZ(u)[z]=-z\sum_{n=-\infty}^{+\infty} u_n(-nz^{-n-1})=\sum_{n=-\infty}^{+\infty} nu_nz^{-n-1}=TZ (n\mapsto nu_n)[z]$$

- En faisant le produit de Cauchy des deux séries, on trouve 

$$U(z)V(z)=\sum_{p=-\infty}^{+\infty}u_pz^{-p}\sum_{q=-\infty}^{+\infty}v_qz^{-q}=\sum_{p,q\in \Z^2} u_pv_{q}z^{-p-q}$$
$$=\sum_{n=-\infty}^{+\infty}\sum_{p+q=n} u_pv_q z^{-n} = TZ \left(\sum_{k=-\infty}^{+\infty} u_kv_{n-k}\right)[z]$$
:::


### Formule d'inversion


::::{prf:theorem}
La transformée en Z est inversible, et pour $u$ une suite, son inverse est défini par :

$$(u_n) =\left(\frac{1}{2i\pi}\int_{C^+}U(z)z^{n-1} dz\right)$$

où $C^+$ est un contour fermé, inclus **dans l’anneau de convergence absolue** et faisant un seul "tour" (typiquement un cercle), parcouru dans le sens direct

```{prf:proof}
Le théorème des résidus nous donne directement que 

$$\frac{1}{2i\pi}\int_{C^+}z^{n-k-1}dz = \left\{\begin{matrix}
        1&\text{ si} k=n,\\
        0&\text{sinon.}
    \end{matrix}\right.$$

Le fait de se placer dans l'anneau de convergence permet de justifier l'interversion dans le calcul suivant :

$$\frac{1}{2i\pi}\int_{C^+}U(z)z^{n-1} dz=\frac{1}{2i\pi}\int_{C^+}\sum_{k=-\infty}^{+\infty}u(n)z^{n-1-k} dz$$
$$= \sum_{k=-\infty}^{+\infty}\frac{1}{2i\pi}\int_{C^+}u(k)z^{n-1-k} dz=\sum_{k=-\infty}^{+\infty}u(k)\frac{1}{2i\pi}\int_{C^+}z^{n-1-k} d=u_n$$

```

```{prf:remark}
 Comme pour la transformée de Laplace, il peut être pertinent de vérifier que l'on ne retrouve pas la transformée en Z à inverser dans les tables avant de se lancer dans les calculs.
 ```
::::