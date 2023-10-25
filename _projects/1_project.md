---
layout: page
title: RMiniZinc
description: An Interface to MiniZinc in R
img: assets/img/GSoC-Vertical.png
importance: 1
category: work
---

Constraint optimization, or constraint programming, is the name given to identifying feasible solutions out of a very large set of candidates, where the problem can be modeled in terms of arbitrary constraints. <a href="https://www.minizinc.org/">MiniZinc</a> is a free and open-source constraint modeling language. Constraint satisfaction and discrete optimization problems can be formulated in a high-level modeling language. Models are compiled into an intermediate representation that is understood by a wide range of solvers. MiniZinc itself provides several solvers, for instance <a href="https://www.gecode.org/">GeCode</a>. R users can use the package to solve constraint programming problems without using MiniZinc directly, modify existing MiniZinc models and also create their own models. Please refer to the Github <a href="https://github.com/acharaakshit/RMiniZinc">repository</a> or the <a href="https://rviews.rstudio.com/2021/02/15/r-interface-for-minizinc/">blog</a> to get started. The package is available on <a href="https://cran.r-project.org/web/packages/rminizinc/index.html">CRAN</a>.
