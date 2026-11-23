# letteredthm
A LaTeX package for theorem-like environments, such as hypotheses, with
lettered sub-numbering: 1, 2a, 2b, 3, ...

Usage
-----

Load the package anywhere in the preamble, before or after `cleveref` and
`hyperref`:
```latex
\usepackage{letteredthm}
```
The package needs nothing beyond the LaTeX kernel (November 2021 or later)
and works with `amsthm` or with the kernel's own `\newtheorem`.

#### `\NewLetteredTheorem{`*env*`}{`*name*`}{`*Singular*`}{`*Plural*`}`
Defines the theorem-like environment ***env***, headed ***Singular***, and the
commands `\start`***name*** and `\stop`***name***. ***Singular*** and
***Plural*** also give the names `cleveref` uses in references. The
environment takes the current theorem style:
```latex
\theoremstyle{definition}
\NewLetteredTheorem{hypothesis}{subhypotheses}{Hypothesis}{Hypotheses}
```

#### `\start`*name*`[`*label*`]` … `\stop`*name*
Outside a start/stop pair, each ***env*** takes the next number. Between them,
every ***env*** shares the next number and gets a letter. The commands add no
grouping or formatting, so any text, sections or floats can sit between the
lettered statements:
```latex
For these reasons, we expect $Y$ to increase in $X$. Hence:
\startsubhypotheses[hyp:1]
\begin{hypothesis}\label{hyp:1a}
  $Y$ increases in $X$.
\end{hypothesis}
Of course, we could make the same argument for $Z$. Hence:
\begin{hypothesis}\label{hyp:1b}
  $Y$ increases in $Z$.
\end{hypothesis}
\stopsubhypotheses
\begin{hypothesis}\label{hyp:2}
  ...
\end{hypothesis}
```
This gives Hypotheses 1a, 1b and 2. A new `\start`***name*** also closes any
open group, so groups can follow each other directly. The optional
***label*** refers to the whole group: `\ref{hyp:1}` prints "1".

With `cleveref`, `\cref{hyp:2,hyp:1b,hyp:1a}` prints "hypotheses 1a, 1b and
2": plain and lettered statements are sorted into one list. Names set with
`\crefname` or `\Crefname` take precedence.

See [letteredthm.pdf](letteredthm.pdf) for the full documentation.

---

Author: Gorkem Aksaray (<aksarayg@tcd.ie>)  
Version: 1.0.0 (2026-11-23)  
License: [LaTeX Project Public License v1.3c](https://www.latex-project.org/lppl.txt)
