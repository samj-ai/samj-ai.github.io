---
layout: default
title: Chapter 0 - Introduction
nav_order: 1
parent: Category Theory
---

# Chapter 0
**Examples of universal properties**

This chapter introduces the idea of universal mapping property (UMP) through a handful of examples:
- groups: $G$
- rings
- vector spaces
- topological spaces
$$
\begin{CD}
A @>f>> B @>g>> C \\
@VhVV @VkVV @VmVV \\
D @>j>> E @>l>> F
\end{CD}
$$
## Exercises:
- 0.10. The indiscrete topology $I(S)$ on the set $\ S$ has only open $\emptyset$ and $S$. In order to guarantee a continuous function, preimages of all open sets must be open; therefore we ought to expect universal maps *into* $I(S)$. Indeed, given $f: X \longrightarrow S$, the map $X \longrightarrow I(S)$ is continuous, since the preimage of S is X. In more evocative language, maps into a point are all continuous. In a diagram:
<script type="text/tikz">
\begin{tikzcd}
S \arrow[r, "i"] & B \arrow[u, "\bar{f}"] \\
& \arrow[ul, "f"', dashed] X
\end{tikzcd}
</script>