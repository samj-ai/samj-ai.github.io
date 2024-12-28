---
layout: default
title: LaTeX Notes
nav_order: 1
has_children: true
---

# Category Theory Diagram Cheat Sheet

## Basic AMScd Diagrams

### Simple morphism
$$
\begin{CD}
A @>f>> B
\end{CD}
$$

### Composition diagram
$$
\begin{CD}
A @>f>> B @>g>> C
\end{CD}
$$

### Square diagram
$$
\begin{CD}
A @>f>> B \\
@VgVV @VhVV \\
C @>k>> D
\end{CD}
$$

### Parallel arrows (using spacing)
$$
\begin{CD}
A @>f>> B \\
A @>>g> B
\end{CD}
$$

### Identity morphism
$$
\begin{CD}
A @= A
\end{CD}
$$

## TikZ-CD Examples (for more complex diagrams)

Note: These won't render in AMScd but show what's possible with tikz-cd (using quiver.app):

### Dashed arrow (Universal Property)

$$
\begin{tikzcd}
& X \arrow[dr, "h", dashed] & \\
A \arrow[ur, "f"] \arrow[rr, "g"'] && Y
\end{tikzcd}
$$

$$
\begin{tikzcd}
& X \arrow[dr, "h", dashed] & \\
A \arrow[ur, "f"] \arrow[rr, "g"'] && Y
\end{tikzcd}
$$

### Diagonal arrows
$$
\begin{tikzcd}
A \arrow[r, "f"] \arrow[dr, "h"'] & B \arrow[d, "g"] \\
& C
\end{tikzcd}
$$

### Parallel arrows
$$
\begin{tikzcd}
A \arrow[r, "f", shift left=0.75ex] 
  \arrow[r, "g"', shift right=0.75ex] & B
\end{tikzcd}
$$

### Triple parallel arrows

$$
\begin{tikzcd}
A \arrow[r, "f", shift left=1.5ex] 
  \arrow[r, "g"] 
  \arrow[r, "h"', shift right=1.5ex] & B
\end{tikzcd}
$$$

### Curved arrows

$$
\begin{tikzcd}
A \arrow[r, "f"] \arrow[out=45, in=135, loop, "α"] & B
\end{tikzcd}
$$

## Common Categorical Constructions

### Product diagram
$$
\begin{CD}
P @>π_1>> A \\
@Vπ_2VV @. \\
B
\end{CD}
$$

### Pullback square

$$
\begin{tikzcd}
P \arrow[r, "p_1"] \arrow[d, "p_2"'] & A \arrow[d, "f"] \\
B \arrow[r, "g"'] & C
\end{tikzcd}
$$

### Pushout square
```latex
\begin{tikzcd}
A \arrow[r, "f"] \arrow[d, "g"'] & B \arrow[d, "i_1"] \\
C \arrow[r, "i_2"'] & P
\end{tikzcd}
```

### Adjunction unit/counit
```latex
\begin{tikzcd}
F(G(A)) \arrow[r, "ε_A"] & A \\
G(F(X)) & X \arrow[l, "η_X"']
\end{tikzcd}
```

Remember:
- AMScd is great for simple diagrams with horizontal and vertical arrows
- For diagonal arrows, dashed arrows, or more complex layouts, use tikz-cd (via quiver.app)
- The choice @= gives you an equals sign (identity morphism)
- Labels go between the arrow markers (>, <, V, A)
```

Would you like me to explain any of these constructions in more detail? I can also add more examples for specific categorical concepts you're working with!


# Category Theory Diagram Cheat Sheet

## Basic AMScd Diagrams

### Simple morphism
$$
\begin{CD}
A @>f>> B
\end{CD}
$$

### Composition diagram
$$
\begin{CD}
A @>f>> B @>g>> C
\end{CD}
$$

### Square diagram
$$
\begin{CD}
A @>f>> B \\
@VgVV @VhVV \\
C @>k>> D
\end{CD}
$$

### Parallel arrows (using spacing)
$$
\begin{CD}
A @>f>> B \\
A @>>g> B
\end{CD}
$$

### Identity morphism
$$
\begin{CD}
A @= A
\end{CD}
$$

## TikZ-CD Examples (for more complex diagrams)

Note: These won't render in AMScd but show what's possible with tikz-cd (using quiver.app):

### Dashed arrow (Universal Property)
```latex
\begin{tikzcd}
& X \arrow[dr, "h", dashed] & \\
A \arrow[ur, "f"] \arrow[rr, "g"'] && Y
\end{tikzcd}