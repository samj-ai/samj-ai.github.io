---
layout: default
title: LaTeX Notes
nav_order: 1
has_children: true
---

# Category Theory Diagram Guide

## Simple Diagrams (using CD)
Best for basic commutative diagrams, renders quickly and works in VS Code preview.

### Basic Morphism
$$
\begin{CD}
A @>f>> B
\end{CD}
$$

### Composition
$$
\begin{CD}
A @>f>> B @>g>> C
\end{CD}
$$

### Square Diagram
$$
\begin{CD}
A @>f>> B \\
@VgVV @VhVV \\
C @>k>> D
\end{CD}
$$

### Simple Parallel Arrows
$$
\begin{CD}
A @>f>> B \\
A @>>g> B
\end{CD}
$$

## Complex Diagrams (using tikz-cd)
For diagrams needing dashed arrows, diagonal arrows, or special formatting.

### Universal Mapping Property
<script type="text/tikz">
\begin{tikzcd}
  & X \arrow[dr, "h", dashed] & \\
  A \arrow[ur, "f"] \arrow[rr, "g"'] && Y
\end{tikzcd}
</script>

### Pullback Square
<script type="text/tikz">
\begin{tikzcd}
P \arrow[r, "p_1"] \arrow[d, "p_2"'] & A \arrow[d, "f"] \\
B \arrow[r, "g"'] & C
\end{tikzcd}
</script>

### Parallel Arrows with Shift
<script type="text/tikz">
\begin{tikzcd}
A \arrow[r, "f", shift left=0.75ex] 
  \arrow[r, "g"', shift right=0.75ex] & B
\end{tikzcd}
</script>

### Triple Parallel Arrows
<script type="text/tikz">
\begin{tikzcd}
A \arrow[r, "f", shift left=1.5ex] 
  \arrow[r, "g"] 
  \arrow[r, "h"', shift right=1.5ex] & B
\end{tikzcd}
</script>

### Curved and Looped Arrows
<script type="text/tikz">
\begin{tikzcd}
A \arrow[r, "f"] \arrow[loop above, "α"] & B
\end{tikzcd}
</script>

## When to Use Each

Use CD environment (`\begin{CD}`) when:
- Drawing simple morphisms
- Creating basic commutative squares
- Need fast rendering and VS Code preview
- Diagrams only use horizontal and vertical arrows

Use tikz-cd (with `<script type="text/tikz">`) when:
- Need dashed or dotted arrows
- Want diagonal arrows
- Creating complex layouts
- Need to adjust arrow positioning
- Drawing loops or curved arrows
- Making parallel arrows with proper spacing

## Tips
1. For basic diagrams, start with CD syntax - it's lighter and renders faster
2. Switch to tikz-cd when you need more complex features
3. Remember tikz-cd diagrams won't show in VS Code preview - use local server to check them
4. The slight rendering delay for tikz diagrams is normal