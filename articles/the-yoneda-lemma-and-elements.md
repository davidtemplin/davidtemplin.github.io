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

For each object $X$ of a category $\mathcal{C}$, we seek to define the elements
$E(X)$ of $X$, i.e. we seek an appropriate *functor*. The first property means
that $E(X) \cong E(Y)$ if and only if $X \cong Y$ (i.e. by the [principle of
equivalence](https://ncatlab.org/nlab/show/principle+of+equivalence), objects
should only be determined *up to isomorphism*).

Consider the following theorem:

For any full and faithful functor $F : \mathcal{C} \rightarrow \mathcal{D}$, $F
A \cong FB$ if and only if $A \cong B$ for all objects $A$ and $B$ of $
\mathcal{C}$.

Proof:

Suppose $FA \cong FB$. Then there exist morphisms $i : FA \rightarrow FB$ and
$i^- : FB \rightarrow FA$ such that $i \circ i^- = 1_{FB}$ and $i^- \circ i =
1_{FA}$. Since $F$ is full, there exist morphisms $j : A \rightarrow B$ and $j^-
: B \rightarrow A$ such that $Fj = i$ and $Fj^- = i^-$. Since $F(j \circ j^-)
= Fj \circ Fj^- = i \circ i^- = 1_{FA}$, $F1_A = 1_{FA}$ and $F$ is faithful, $
j \circ j^ = 1_A$. Likewise, $j^- \circ j = 1_B$, and so $A \cong B$. A similar
argument shows that $FA \cong FB$ if $A \cong B$.
