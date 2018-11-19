---
title: The Yoneda Lemma and Elements
layout: article
---

This page is under construction.

# Overview

In this article, I explain how the (contravariant) Yoneda Lemma can be
understood in terms of *elements* of a (contravariant) set-valued functor.
There are two prime notions of an element of a set-valued functor; the Yoneda
Lemma is precisely the statement that these two notions coincide.

# Introduction

What is an appropriate notion of an "element" of an object in a category? If we
adopt an *extensional* view of elements, then there are two key properties:

* Objects should be *completely determined* by their elements (cf. the Axiom of
Extensionality in set theory)
* Objects should be the "*sum*" of their elements (cf. the view of sets as the
totality of their elements in set theory)

For each object $$X$$ of a category $$\mathcal{C}$$, we seek to define the elements
$$E(X)$$ of $$X$$, i.e. we seek an appropriate *functor*. The first property means
that $$E(X) \cong E(Y)$$ if and only if $$X \cong Y$$ (i.e. by the [principle of
equivalence](https://ncatlab.org/nlab/show/principle+of+equivalence), objects
should only be determined *up to isomorphism*). For any (locally small) category,
the functor $$\mathrm{Hom}_{\mathcal{C}}(-,X)$$ is always defined, so we take this
functor for $$E$$.

Consider the following theorem:

For any full and faithful functor $$F : \mathcal{C} \rightarrow \mathcal{D}$$, $$F
A \cong FB$$ if and only if $$A \cong B$$ for all objects $$A$$ and $$B$$ of $$
\mathcal{C}$$.

Proof:

Suppose $$FA \cong FB$$. Then there exist morphisms $$i : FA \rightarrow FB$$ and
$$i^- : FB \rightarrow FA$$ such that $$i \circ i^- = 1_{FB}$$ and $$i^- \circ i = 1_{FA}$$. 
Since $$F$$ is full, there exist morphisms $$j : A \rightarrow B$$ and $$j^- : B \rightarrow A$$ 
such that $$Fj = i$$ and $$Fj^- = i^-$$. Since $$F(j \circ j^-) = Fj \circ Fj^- = i \circ i^- = 1_{FA}$$, 
$$F1_A = 1_{FA}$$, and $$F$$ is faithful, $$j \circ j^- = 1_A$$. Likewise, $$j^- \circ j = 1_B$$, 
and so $$A \cong B$$. A similar argument shows that $$FA \cong FB$$ if $$A \cong B$$.

Definition: We will write $$\hat{\mathcal{C}}$$ for $\mathbf{Set}^{\mathcal{C}^{\mathrm{op}}}$.

Definition: We will write $$y$$ for the Yoneda Functor $$y : \mathcal{C} \rightarrow \hat{\mathcal{C}}$$
defined as $$yX = \mathrm{Hom}(-,X)$$ for objects $$X$$ and $$yf = \mathrm{Hom}(-,f)$$ for arrows $$f$$.

Next, consider the following theorem:

The functor $$\mathrm{Hom}_{\mathcal{C}}(-,X)$$ is full and faithful for any locally small
category $$\mathcal{C}$$ and object $$X$$ of $$\mathcal{C}$$.

Proof:

Let $$\theta : \mathrm{Hom}(-,X) \rightarrow \mathrm{Hom}(-,Y)$$ be any arrow (i.e. a natural transformation) in 
$$\hat{\mathcal{C}}$$. Then $$\theta_X(1_X) : X \rightarrow Y$$, and, for any object $$A$$ of $$\mathcal{C}$$ and arrow 
$$h : A \rightarrow X$$:

$$
\begin{align}
 y(\theta_X(1_X))_A(h) &= \mathrm{Hom}(A,\theta_X(1_X))(h) \textrm{(by definition of $$y$$)} \\
 &= \theta_X(1_X) \circ h \textrm{(by definition of $$\mathrm{Hom}(A,\theta_X(1_X))$$)} \\
 &= (\mathrm{Hom}(h,Y) \circ \theta_X)(1_X) \textrm{(by definition of $$\mathrm{Hom}(h,Y)$$)} \\
 &= (\theta_A \circ \mathrm{Hom(h,X})(1_X) \textrm{(by naturality of $\theta$)} \\
 &= \theta_A(h) \textrm{(by definition of $$\mathrm{Hom(h,X)}$$)}
\end{align}
$$

$$
\begin{xy}
\xymatrix {
A \ar[d]^h & \mathrm{Hom}(A,X) \ar[r]^{\theta_A} & \mathrm{Hom}(A,Y) \\
X & \mathrm{Hom}(X,X) \ar[r]_{\theta_X} \ar[u]^{\Hom(h,X)} & \mathrm{Hom}(X,Y) \ar[u]_{\mathrm{Hom}(h,Y)}
}
\end{xy}
$$

Thus, $$y(\theta_X(1_X))_A = \theta_A$$, and $y(\theta_X(1_X)) = \theta$, so $$y$$ is full.
