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

Definition: We will write $$\widehat{\mathcal{C}}$$ for $$\mathbf{Set}^{\mathcal{C}^{\mathrm{op}}}$$.

Definition: We will write $$y$$ for the Yoneda Functor $$y : \mathcal{C} \rightarrow \widehat{\mathcal{C}}$$
defined as $$yX = \mathrm{Hom}(-,X)$$ for objects $$X$$ and $$yf = \mathrm{Hom}(-,f)$$ for arrows $$f$$.

Next, consider the following theorem:

The functor $$\mathrm{Hom}_{\mathcal{C}}(-,X)$$ is full and faithful for any locally small
category $$\mathcal{C}$$ and object $$X$$ of $$\mathcal{C}$$.

Proof:

Let $$\theta : \mathrm{Hom}(-,X) \rightarrow \mathrm{Hom}(-,Y)$$ be any arrow (i.e. a natural transformation) in 
$$\widehat{\mathcal{C}}$$. Then $$\theta_X(1_X) : X \rightarrow Y$$, and, for any object $$A$$ of $$\mathcal{C}$$ and arrow 
$$h : A \rightarrow X$$:

$$
\begin{align}
y(\theta_X(1_X))_A(h) & = \mathrm{Hom}(A,\theta_X(1_X))(h) && \textrm{(by definition of $y$)} \\
& = \theta_X(1_X) \circ h && \textrm{(by definition of $\mathrm{Hom}(A,\theta_X(1_X))$)} \\
& = (\mathrm{Hom}(h,Y) \circ \theta_X)(1_X) && \textrm{(by definition of $\mathrm{Hom}(h,Y)$)} \\
& = (\theta_A \circ \mathrm{Hom}(h,X)(1_X) && \textrm{(by naturality of $\theta$)} \\
& = \theta_A(h) && \textrm{(by definition of $\mathrm{Hom}(h,X)$)}
\end{align}
$$

$$
\begin{xy}
\xymatrix {
A \ar[d]^h & \mathrm{Hom}(A,X) \ar[r]^{\theta_A} & \mathrm{Hom}(A,Y) \\
X & \mathrm{Hom}(X,X) \ar[r]_{\theta_X} \ar[u]^{Hom(h,X)} & \mathrm{Hom}(X,Y) \ar[u]_{\mathrm{Hom}(h,Y)}
}
\end{xy}
$$

Thus, $$y(\theta_X(1_X))_A = \theta_A$$, and $$y(\theta_X(1_X)) = \theta$$, so $$y$$ is full. Now, suppose
that $$yf = yf'$$ for arrows $$f : X \rightarrow Y$$ and $$f' : X \rightarrow Y$$ of $$\mathcal{C}$$. Then,
$$(yf)_X(1_X) = (yf')_X(1_X)$$ and thus $$f \circ 1_X = f' \circ 1_X$$ and $$f = f'$$, so $y$ is faithful.

Since the functor $$y$$ is full and faithful, it follows that $$yX \cong yY$$ if and only if $$X \cong Y$$
for any objects $$X$$ and $$Y$$. Therefore, an arrow $$A \rightarrow X$$ has the interpretation as an element
of the object $$X$$.

Now, what does it mean for an object $$X$$ to be the "sum" of its elements? In category theory, the general
interpretation of "sum" is a _colimit_ of an appropriate diagram. For any object $$X$$, the _slice category_
$$\mathcal{C}/X$$ may be understood as a (concrete) _category of elements_ of $$X$$. There is a functor
$$D : \mathcal{C}/X \rightarrow \mathcal{C}$$ defined as $$Df = \mathrm{dom}(f)$$ for any object $$f$$ of
$$\mathcal{C}/X$$ (and hence arrow of $$\mathcal{C}$$) and $$Dg = g$$ for any arrow $$g$$ of $$\mathcal{C}/X$$.
$$X$$ will then be a colimit of the diagram $$D$$.

Proof: 

For any object $$f$$ of $$\mathcal{C}/X$$, define $$\psi_f : Df \rightarrow X$$ as $$f$$ itself. For any arrow
$$g : f \rightarrow f'$$ in $$\mathcal{C}/X$$, $$\phi_{f'} \circ Dg = f' \circ g = f$$ by definition of $$\mathcal{C}/X$$.
Thus, $$(X, \phi)$$ comprises a co-cone. Suppose there is another co-cone $$(Y,\psi)$$. Since $$1_X$$ is an object of
$$\mathcal{C}/X$$, $$D1_X = \mathrm{dom}(1_X) = X$$, and since $$(Y,\psi)$$ is a co-cone, there is an arrow $$\psi_{1_X} : D1_X \rightarrow Y$$,
i.e. an arrow $$\psi : X \rightarrow Y$$. Furthermore, since $$(Y,\psi)$$ is a co-cone, it is the case that $$\psi_{1_X} \circ \phi_f = \psi_f$$
and $$\psi_{1_X} \circ \phi_{f'} = \psi_{f'}$$. Thus, $$(X,\phi)$$ is a colimit.

$$
\begin{xy}
\xymatrix {
A \ar[d]_f \ar[rr]^g & & B \ar[d]^{f'} \\ 
& X & \\
}
\end{xy}
$$

$$
\begin{xy}
\xymatrix {
Df = A \ar[ddr]_{\psi_f} \ar[dr]_{\phi_f = f} \ar[r]^{Dg = g} & & B = Df' \ar[dl]^{f = \phi_{f'}} \ar[ddl]^{\psi_{f'}} \\
& X \ar[d]^{\phi_{1_X}} & \\
& Y &
}
\end{xy}
$$
