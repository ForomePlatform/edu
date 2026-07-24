# Solution-graph examples

Worked examples of **solution graphs**: directed acyclic graphs connecting a
problem statement to its solution through the skills — facts, objects, and
methods — required, with nodes drawn from the catalogs in this repository.
The examples are described in
*An Ontology-Based Approach to Optimizing Geometry Problem Sets for Skill
Development* ([arXiv:2509.02758](https://doi.org/10.48550/arXiv.2509.02758)).

Problem statements are not reproduced here; every graph's Start node carries
the problem's canonical URL in the public database:
`https://zadachi.mccme.ru/2012/#&task{number}`.

## Legend (all examples)

- **Ellipses** (yellow) — *facts* (`K…` catalog entries), e.g. Pythagoras' theorem.
- **Diamonds** (green) — *objects* (`O…` entries), e.g. a right triangle.
- **Rectangles** (light green) — *methods* (`M…` entries), e.g. the area method.
- A **red border** marks the *key skills* the problem is designed to exercise.
- Every root-to-solution path is a complete solution strategy; branches are
  alternative solutions.

## The examples

| Files | Problem | Shape | Illustrates |
|---|---|---|---|
| `No00001-example.*` | [problem 1](https://zadachi.mccme.ru/2012/#&task1) — the inscribed-angle theorem | single chain, 7 nodes | the simplest graph (complexity 1): one solution path; a *problem-theorem* key problem (the corpus's most-referenced entry) |
| `No00005-example.*` | [problem 5](https://zadachi.mccme.ru/2012/#&task5) — chord through concentric circles | 8 nodes, one branch | alternative endings (complexity 2): a Pythagoras route and an intersecting-chords route to the same solution |
| `solution-graph.gv` | [problem 2034](https://zadachi.mccme.ru/2012/#&task2034) — trapezoid area | 20 nodes, three paths | a rich graph (complexity 3); this is Figure 1 of the article |

Each `*-example.gv` has pre-rendered `.svg` and `.png` next to it. The node
labels are the English catalog entries; the `.gv` sources carry the same
`K/O/M` code semantics as the machine-readable corpus graphs.

## Rendering

With [Graphviz](https://graphviz.org) installed:

```sh
dot -Tsvg No00001-example.gv -o No00001-example.svg
dot -Tpng No00001-example.gv -o No00001-example.png
```

## How these are made

A problem's annotation lists its graph as a sequence of catalog codes (the
main chain) plus optional alternative-path edges; labels come from the
English catalogs. See `../docs/annotation-methodology.md` for the full
construction rules and the annotation format.
