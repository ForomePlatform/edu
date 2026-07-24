# Solution-graph example

`solution-graph.gv` is the Graphviz (DOT) source of Figure 1 of
*An Ontology-Based Approach to Optimizing Geometry Problem Sets for Skill
Development* ([arXiv:2509.02758](https://doi.org/10.48550/arXiv.2509.02758)).

It is the solution graph of a trapezoid-area problem
([problem 2034](https://zadachi.mccme.ru/2012/jndex.html#&task2034) in the
zadachi.mccme.ru database): a directed acyclic graph connecting the problem
statement to its solution through the skills required, with nodes drawn from
the catalogs in this repository.

## Legend

- **Ellipses** (yellow) — *facts* (`K…` catalog entries), e.g. Heron's formula.
- **Diamonds** (green) — *objects* (`O…` entries), e.g. parallelogram.
- **Rectangles** (light green) — *methods* (`M…` entries), e.g. the area method.
- The node with the **red border** is the target skill the problem is designed
  to exercise (here: *area of a trapezoid*).
- Distinct root-to-solution paths correspond to distinct solution strategies.

## Rendering

With [Graphviz](https://graphviz.org) installed:

```sh
dot -Tpdf solution-graph.gv -o solution-graph.pdf
dot -Tpng solution-graph.gv -o solution-graph.png
```
