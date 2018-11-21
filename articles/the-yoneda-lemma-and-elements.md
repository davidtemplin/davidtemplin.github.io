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

The functor $$y$$ is full and faithful for any locally small
category $$\mathcal{C}$$.

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
i.e. an arrow $$\psi_{1_X} : X \rightarrow Y$$. Furthermore, since $$(Y,\psi)$$ is a co-cone, it is the case that $$\psi_{1_X} \circ \phi_f = \psi_f$$
and $$\psi_{1_X} \circ \phi_{f'} = \psi_{f'}$$. Thus, $$(X,\phi)$$ is a colimit.

$$
\begin{xy}
\xymatrix {
A \ar[dr]_f \ar[rr]^g & & B \ar[dl]^{f'} \\ 
& X & \\
}
\end{xy}
$$

$$
\begin{xy}
\xymatrix {
Df = A \ar@/_/[ddr]_{\psi_f} \ar[dr]_{\phi_f = f} \ar[rr]^{Dg = g} & & B = Df' \ar[dl]^{f = \phi_{f'}} \ar@/^/[ddl]^{\psi_{f'}} \\
& X = D1_X \ar[d]^{\psi_{1_X}} & \\
& Y &
}
\end{xy}
$$

So, for any object $$X$$ in a category $$\mathcal{C}$$, $$X$$ is completely determined by its (functor of) elements $$yX$$ and
it is the "sum" (colimit) of its (canonical diagram $$D$$ of its category $$\mathcal{C}/X$$ of) elements, where an element is
merely an arrow $$f : A \rightarrow X$$ for some object $$A$$ of $$\mathcal{C}$$, i.e. $$\mathrm{cod}(f) = X$$.

Definition: For objects $$A$$ and $$X$$ of a category $$\mathcal{C}$$, the arrows in $$Hom_{\mathcal{C}}(A,X)$$ are called
the $$A$$-elements of $$X$$.

For each object $$X$$ of a category $$\mathcal{C}$$, the functor $yX = \mathrm{Hom}_{\mathcal{C}}(-,X)$ describes $$X$$ as a
*structured set* of its elements; essentially, each object $$A$$ is replaced by the set of $$A$$-elements of $$X$$. But then,
the functor $$yX$$ must encode a colimit, since we can recover the slice category from it up to isomorphism as follows: define
a category $$El_{\mathrm{Hom}(-,X)}$$ with pairs $$(A,f)$$ consisting of an object $$A$$ of $$\mathcal{C}$$ and an arrow
$$f \in \mathrm{Hom}_{\mathcal{C}}(A,X)$$ as its objects and pairs $$(g,(A,a))$$ as arrows between $$(A,f)$$ and $$(B,f')$$ whenever $$\mathrm{Hom}(g,X)(f') = f$$
for some arrow $$g$$ of $$\mathcal{C}$$. Thus, composing the canonical diagram $$D : \mathcal{C}/X \rightarrow \mathcal{C}$$ with the 
isomorphism $$I : El_{\mathrm{Hom}(-,X)} \rightarrow \mathcal{C}/X$$, we obtain a diagram $$D \circ I$$ such that $$X$$ is (the vertex of)
a colimit of this diagram. Thus, the functors $$yX$$ encode colimits as well as describe the elements of $$X$$. Another way to say the same thing
is that $$yX$$ describes (a category isomorphic to) the slice category as a *concrete category* since it is a faithful functor to $$\mathbf{Set}$$,
and hence it deescribes a colimit which is $$X$$. Thus, the category $$El_{yX}$$ "unwinds" the *actual* elements of the sets $$yXA = \mathrm{Hom}(A,X)$$
into a category, which can then be "wound" together again. Thus, in our analysis of elements, there is a link between the *abstract* elements
and *concrete* elements. This process yields a method for representing categories as sets.

Definition: a set-valued functor $$F : \mathcal{C}^{\mathrm{op}} \rightarrow \mathbf{Set}$$ is *representable* if
$$F \cong \mathrm{Hom}_{\mathcal{C}}(-,X)$$ for some object $$X$$ of $$\mathcal{C}$$.

But, there is no reason to restrict our attention to the functors $$yX$$; what about *arbitrary* set-valued functors?
The definition of the category of elements still makes sense for arbitrary set-valued functors:

Definition: For any functor $$F : \mathcal{C}^{\mathrm{op}} \rightarrow \mathbf{Set}$$, the *category of elements* of $$F$$ is defined as follows:
* Objects: pairs $$(A,a)$$ consisting of an object $$A$$ of $$\mathcal{C}$$ and an element $$a \in FA$$
* Arrows: pairs $$(g, (A,a)) : (A,a) \rightarrow (B,b)$$ whenever $$(Fg)(b) = a$$ for some arrow $$g$$ of $$\mathcal{C}$$

Arbitrary set-valued functors *still* describe a diagram; the category $$\mathcal{C}$$ might not have any colimit of the diagram, however. Such functors
describe *hypothetical* colimits. Since $$y$$ is an *embedding*, each representable functor $$yX$$ also describes a colimit in $$\widehat{C}$$, of which $$yX$$ is the vertex.
It is natural to ask whether this is the case for non-representable functors as well; the answer is "yes".

In many categories, objects are completely determined by some subset of arrows; in any category, all arrows into an object are *sufficient*
to determine the object, but may not be *necessary*. For instance, in $$\mathbf{Set}$$, the arrows from any terminal object (i.e. singleton set) $$1 = \{*\}$$
are sufficient to determine an object (i.e. set) $$X$$ in the sense that $$\mathrm{Hom}(1,X) \cong X$$; in fact, this is one of the defining characteristics
of the category $$\mathbf{Set}$$.

TODO: talk about separators and demonstrate that the class of representable functors is a separating class.

Thus, the arrows $$yA \rightarrow F$$ and the elements $$a \in FA$$ can both be construed as elements of $$F$$. It is natural to ask, therefore,
whether these two notions of element coincide; the answer is "yes", and this is precisely the statement of the Yoneda Lemma:

Theorem (Yoneda): For any locally small category $$\mathcal{C}$$ and object $$A$$ in $$\mathcal{C}$$, $$\mathrm{Hom}_{\widehat{\mathcal{C}}}(yA,F) \cong FA$$,
and this isomorphism is moreover natural in both $$A$$ and $$F$$.

Proof: forthcoming

Theorem: Every functor $$F : \mathcal{C}^{\mathrm{op}} \rightarrow \mathbf{Set}$$ is a colimit of representable functors. More precisely, $$(F,\phi)$$ is a colimit
of the diagram $$D : \mathrm{El}_F \rightarrow \widehat{\mathcal{C}}$$ defined as follows:

* $$D(A,a) = yA$$ for objects $$(A,a)$$
* $$D(g,(A,a)) = fg$$ for arrows $$(g,(A,a))$$

where, for each object $$(A,a)$$ of $$\mathrm{El}_F$$, $$\phi_{(A,a)} : D(A,a) \rightarrow F$$ is defined such that $$\phi_{(A,a),X}(h) = (Fh)(a)$$ for an arrow $$h : X \rightarrow A$$.

Proof: First, observe that $$\phi_{(B,b)} \circ D(g,(A,a)) = \phi_{(A,a)}$$ for any objects $$(A,a)$$ and $$(B,b)$$ and arrow $$(g,(A,a)) : (A,a) \rightarrow (B,b)$$ of $$\mathrm{El}_F$$,
i.e. that for any object $$X$$ and arrow $$h : X \rightarrow A$$ of $$\mathcal{C}$$:

$$
\begin{xy}
\xymatrix {
(A,a) \ar[dd]^{(g,(A,a))} & yA = D(A,a) \ar@/_/[ddr]_{\psi_{(A,a)}} \ar[dr]_{\phi_{(A,a)}} \ar[rr]^{D(g,(A,a))} & & D(B,b) = yB \ar[dl]^{\phi_{(B,b)}} \ar@/^/[ddl]^{\psi_{(B,b)}} \\
& & F \ar@{.>}[d]^{\exists ! \alpha} & \\
(B,b) & & G &
}
\end{xy}
$$

$$
\begin{align}
(\phi_{(B,b)} \circ yg)_X(h) & = (\phi_X \circ yg_X)(h) && \textrm{natural transformation composition} \\
& = (\phi_{(B,b),X} \circ \mathrm{Hom}_{\mathcal{C}}(-,g)_X)(h) && \textrm{definition of $yg$} \\
& = \phi_{(B,b),X}(\mathrm{Hom}_{\mathcal{C}}(-,g)_X(h)) && \textrm{function composition} \\
& = \phi_{(B,b),X}(g \circ h) && \textrm{definition of $\mathrm{Hom}_{\mathcal{C}}(-,g)_X$} \\
& = F(g \circ h)(b) && \textrm{definition of $\phi_{(B,b),X}$} \\
& = (Fh \circ Fg)(b) && \textrm{contravariant functoriality of $F$} \\
& = (Fh)((Fg)(b)) && \textrm{function composition} \\
& = (Fh)(a) && \textrm{definition of arrows of $\mathrm{El}_F$} \\
& = \phi_{(A,a),X}(h) && \textrm{by definition of $\phi_{(A,a),X}$}
\end{align}
$$

Next, suppose that there is another co-cone $$(G, \psi)$$ and define a natural transformation $$\alpha : F \rightarrow G$$ such that $$\alpha_X(x) = \psi_{(X,x),X}(1_X)$$ for any object $$X$$ of $$\mathcal{C}$$ and observe that
$$\alpha \circ \phi_{(A,a)} = \psi_{(A,a)}$$, i.e. that for any object $$X$$ and arrow $$h : X \rightarrow A$$ of $$\mathcal{C}$$, $$(\alpha \circ \phi_{(A,a)})_X(h) = \psi_{(A,a),X}(h)$$:

$$
\begin{align}
(\alpha \circ \phi_{(A,a)})_X(h) & = (\alpha_X \circ \phi_{(A,a),X})(h) && \textrm{natural transformation composition} \\
& = \alpha_X(\phi_{(A,a),X}(h)) && \textrm{function composition} \\
& = \alpha_X((Fh)(a)) && \textrm{definition of $\phi_{(A,a),X}$} \\
& = \psi_{(X,(Fh)(a)),X}(1_X) && \textrm{definition of $\alpha_X$} \\
& = (\psi_{(A,a)} \circ yh)_X(1_X) && \textrm{since $(G, \psi)$ is a co-cone and $(h,(X,(Fh)(a))) : (X,(Fh)(x)) \rightarrow (A,a)$} \\
& = (\psi_{(A,a),X} \circ yh_X)(1_X) && \textrm{natural transformation composition} \\
& = (\psi_{(A,a),X} \circ \mathrm{Hom}_{\mathcal{C}}(-,h)_X)(1_X) && \textrm{definition of $yh$} \\
& = \psi_{(A,a),X}(\mathrm{Hom}_{\mathcal{C}}(-,h)_X(1_X)) && \textrm{function composition} \\
& = \psi_{(A,a),X}(h) && \textrm{definition of $\mathrm{Hom}(-,h)_X$}
\end{align}
$$

Finally, suppose that there is another natural transformation $$\beta : F \rightarrow G$$ such that $$\beta \circ \phi_{(A,a)} = \psi_{(A,a)}$$ for any $$(A,a)$$, and observe that $$\alpha = \beta$$,
i.e. that $$\alpha_X(x) = \beta_X(x)$$ for any object $$X$$ and element $$x \in FX$$:

$$
\begin{align}
\alpha_X(x) & = \psi_{(X,x),X}(1_X) && \textrm{definition of $\alpha_X$} \\
& = (\beta \circ \phi_{(X,x)})_X(1_X) && \textrm{by assumption} \\
& = (\beta_X \circ \phi_{(X,x),X})(1_X) && \textrm{natural transformation composition} \\
& = \beta_X((F1_X)(x)) && \textrm{definition of $\phi_{(X,x),X}$} \\
& = \beta_X(1_{FX}(x)) && \textrm{functoriality of $F$} \\
& = \beta_X(x) && \textrm{identity arrow}
\end{align}
$$
