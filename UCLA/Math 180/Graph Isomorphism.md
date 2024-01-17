---
id: Graph Isomorphism
aliases: []
tags:
  - Math180
---

- Two graphs $G = (V, E, \varphi)$ and $G' = (V', E', \varphi')$ are
  _isomorphic_ if:
  - There exists a bijection $\theta\colon V\to V'$
  - There exists a bijection $\eta\colon E\to E'$
  - $\varphi'(\eta(e)) = \{\theta(u), \theta(v)\}$ for all $e = \{u, v\}\in E$
