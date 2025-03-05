---
layout: default
title: Test
nav_order: 1
---

# Math Test

Simple inline math: $x^2 + y^2 = z^2$

Display math:
$$
\begin{aligned}
a &= b + c \\
  &= d + e
\end{aligned}
$$

<script type="text/tikz">
  \begin{tikzpicture}
    \node (A) at (0,0) {$A$};
    \node (B) at (2,0) {$B$};
    \draw[->] (A) -- (B) node[midway,above] {$f$};
  \end{tikzpicture}
</script>

<!-- <script type="text/tikz">
\begin{tikzcd}
  X \arrow[dr, "h", dashed] \\
  A \arrow[u, "f"] \arrow[rr, "g"'] && Y
\end{tikzcd}
</script> -->

<script type="text/tikz">
\begin{tikzcd}
A \arrow[r, "f"] \arrow[dr, "h"', dashed] & B \arrow[d, "g"] \\
& C
\end{tikzcd}
</script>