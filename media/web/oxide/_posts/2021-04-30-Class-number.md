---
layout: post
title: "The class number formula"
tags: mathematics
comments: true
---
# Introduction
Factorisation is an essential idea in number theory. 
After learning the basics of abstract algebra, one learns that it's possible to factorise an element of any commutative ring, not just integers.
In an arbitrary ring however, a factorisation is not necessarily unique.

There is a theorem which relates unique factorisation in a ring to the value of a $\zeta$ function. 
It also helps in determining whether the ring has unique factorisation if you can calculate the value of that $\zeta$ function.[^approx]

I'll describe the rings, then the $\zeta$ function, and then the connection between them.

[^approx]: An exact value is not necessary, sometimes even an approximation suffices.

# Fields

Let $K = \mathbb{Q}(\sqrt{m} )$ where $m < 0$ is a square-free integer. 
It consists of numbers of the form $a+b\sqrt{m}$, where $a, b \in \mathbb{Q}$.
The field $K$ is called an *imaginary quadratic field*, since it is a degree 2 extension of $\mathbb{Q}$ given by $K = \mathbb{Q}[x]/(x^2 - m)$.

It also has a *ring of integers* $\mathcal{O}_K$, which is the analogue of $\mathbb{Z}$ for this field. 
In fact, $\mathcal{O}_K$ is the [integral closure](https://en.wikipedia.org/wiki/Integral_element#Integral_closure_in_algebraic_number_theory) of $\mathbb{Z}$ in $K$.

Unfortunately, the ring $\mathcal{O}_K$ is not always a unique factorisation domain.[^lame]
For example, in $\mathbb{Z}[\sqrt{-5}]$ we have $6 = 2 \cdot 3 = (1 + \sqrt{-5})(1 - \sqrt{-5})$.
The *class number* measures exactly how much unique factorisation fails in $\mathcal{O}_K$.[^classnumber]

[^lame]: If $\mathcal{O}_K$ were always a unique factorisation domain, then Fermat’s last theorem would have been proved almost 150 years earlier than it was! 
    In 1847, [Gabriel Lamé](https://en.wikipedia.org/wiki/Gabriel_Lam%C3%A9) gave a [wrong](https://math.stackexchange.com/q/953462) [proof](https://gallica.bnf.fr/ark:/12148/bpt6k29812/f310.item) that relied on $\mathbb{Z}[\zeta_n]$ being a unique factorisation domain, where $\zeta_n$ is a primitive $n$th root of unity.

[^classnumber]: It is the order of a certain group known as the [ideal class group](https://en.wikipedia.org/wiki/Ideal_class_group). 
    When the order is $1$, $\mathcal{O}_K$ is a unique factorisation domain.

Now, let 
\\[
N = \begin{cases} |m| & \text{if } m \equiv 1 \mod{4} \\\ 4|m| & \text{if } m \equiv 2,3\mod{4} \end{cases}
\\]

The number $N$ is known as the *discriminant* of the number field. 
We can define a group homomorphism $\chi : (\mathbb{Z}/N\mathbb{Z})^\times \to \{\pm 1\} $ as follows:
for any prime $p$ not dividing $m$, put $\chi(p) = \left( \frac{m}{p} \right) $
(This is the Legendre symbol, which outputs $1$ if  $m$ has a square root in  $\mathbb{F}_p$ and $-1$ otherwise).
Using [quadratic reciprocity](https://en.wikipedia.org/wiki/Quadratic_reciprocity), we can extend to all integers coprime to $m$.

# L functions
  We then form the series
  \\[
    L(s,\chi) = \sum_{n=1}^{\infty} \frac{\chi(n)}{n^s}.
  \\]
  where $\chi(n)$ is $\chi(n \mod N)$ if  $n$ is coprime to $N$, and $0$ otherwise. 
This type of series, which we can define for any homomorphism $\chi : (\mathbb{Z}/n\mathbb{Z})^\times \to \mathbb{C}^\times$,
is known as an $L$-function[^dirich], and is an extension of the Riemann $\zeta$ function.[^riemann]

[^dirich]: It’s a [Dirichlet $L$-function](https://en.wikipedia.org/wiki/Dirichlet_L-function) to be precise; there are many types of $L$-functions in number theory.

[^riemann]: The Riemann $\zeta$ function is an $L$-function with $N=2$, because $(\mathbb{Z}/2\mathbb{Z})^\times = \{1\}$ and the homomorphism must map $1$ to $1$.

For example, if $m = -1$, then $N=4$.
We have $\chi(1 \mod 4) = 1$ and $\chi(3 \mod 4) = -1$. 
So, \\[L(s,\chi) = 1 - \frac{1}{3^s} + \frac{1}{5^s} - \frac{1}{7^s} + \dots\\]
And in particular, \\[L(1,\chi) = 1 - \frac13 +\frac15 - \frac17 + \dots = \frac\pi4\\]

# The theorem 
  Here is the main theorem, called the class number formula for quadratic imaginary fields.
> For an imaginary quadratic field $K$, let $h_K$ be its class number and $w_K$ the number of roots of $1$ in $K$. Then:
\\[h_K = \frac{w_K}{2} L(0,\chi) = \frac{w_K \sqrt{N} }{2\pi} L(1,\chi).\\]

So, whether or not the ring of integers is a unique factorisation domain depends on the value of a certain $\zeta$ function. 


For example, let's again take $m = -1$, so  $K = \mathbb{Q}(\sqrt{-1} )$. 
The roots of unity in this field are $1, -1, \sqrt{-1}$, and $-\sqrt{-1}$, so $w_k = 4$.
Using the theorem, we get:
 \\[
   h_K = \frac{w_K \sqrt{N}}{2\pi} L(1,\chi) = \frac{4 \cdot 2}{2\pi} L(1,\chi) = \frac{4}{\pi} \cdot L(1,\chi)
\\]
Here $L(1,\chi) = 1 - \frac{1}{3} + \frac{1}{5} - \dots = \frac{\pi}{4}$, so $h_K = 1$.
Therefore $\mathcal{O}_K = \mathbb{Z}[\sqrt{-1}]$ is a principal ideal domain.
It is striking that we took a detour through analysis to prove an algebraic fact!

---
