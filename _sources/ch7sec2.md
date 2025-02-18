
(annexe_surjectivite_exponentielle)=
## Surjectivité de l’exponentielle complexe
$\newcommand{\R}{\mathbb{R}}$
$\newcommand{\Q}{\mathbb{Q}}$
$\newcommand{\N}{\mathbb{N}}$
$\newcommand{\C}{\mathbb{C}}$
$\newcommand{\Z}{\mathbb{Z}}$

:::::{prf:theorem}
L'exponentielle complexe $exp : \C \to \C^*$ est une application surjective.

::::{prf:proof}
Cette démonstration repose principalement sur le lemme suivant : 
```{prf:lemma}
:class: dropdown
Soit $g: t\in [a,b] \to\C^*$ une application réelle de classe $C^1$ avec $a<b$, alors il existe une application $h :t\in [a,b] \to\C $ telle que $g=e^h$.
:::{prf:proof}
Donnons-nous une telle application $g$, et supposons sans perte de généralité que $g(a)=1$. Posons alors l'application $f : t\mapsto \frac{g'(t)}{g(t)}$ et $h:t\mapsto \int_a^t f(x)dx$. Nous voulons montrer que h convient. 
D'abord, comme f est une application continue, h est bien défini et dérivable. Considérons maintenant $k : t\mapsto g(t)e^{-h(t)}$, qui est dérivable comme produit et composition de fonctions dérivables. Sa dérivée vérifie pour $t\in [a,b]$

$$k'(t)=g'(t)e^{-h(t)} - h'(t)g(t)e^{-h(t)}=g'(t)e^{-h(t)}-g'(t)e^{-h(t)}=0.$$

Ainsi, comme la dérivée de $k$ s'annule sur l'intervalle $[a,b]$, $k$ est constant égal à $g(a)e^0=1$. D'où l'égalité $g=e^h$.
:::
```
Pour conclure la preuve de la propriété, il ne nous reste plus qu'à remarquer que $\C^*$ est connexe par arc $C^1$, et donc pour tout $z\in \C^*$, il existe $g:[0,1]\to \C^*$ continuement dérivable tel que $g(0)=1$ et $g(1)=z$. Alors, l'application $h$ fournit par le lemme vérifie que $e^{h(1)}=g(1)=z$, ce qui montre bien que l'exponentielle est surjective.
::::

:::::
