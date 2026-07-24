# Solution-graph examples

Worked examples of **solution graphs**: directed acyclic graphs connecting a
problem to its solution through the skills — facts, objects, and methods —
required, with nodes drawn from the catalogs in this repository. The
methodology is described in
*An Ontology-Based Approach to Optimizing Geometry Problem Sets for Skill
Development* ([arXiv:2509.02758](https://doi.org/10.48550/arXiv.2509.02758)),
and the construction rules in
[`../docs/annotation-methodology.md`](../docs/annotation-methodology.md).

Each graph's Start node carries the problem's canonical URL in the public
database (`https://zadachi.mccme.ru/2012/#&task{number}`). Database problem
texts are not reproduced here; for the classical theorems below we state the
(long public-domain) result in our own words.

## Legend (all examples)

- **Ellipses** (yellow) — *facts* (`K…` entries), e.g. Pythagoras' theorem.
- **Diamonds** (green) — *objects* (`O…` entries), e.g. a right triangle.
- **Rectangles** (light green) — *methods* (`M…` entries), e.g. the area method.
- A **red border** marks the *key skills* the problem is designed to exercise.
- Every Start→Solution path is a complete solution strategy; branches are
  genuinely different solutions.

## The examples

| Files | Problem | Nodes / paths | Illustrates |
|---|---|---|---|
| `No00001-example.*` | [1](https://zadachi.mccme.ru/2012/#&task1) — the inscribed-angle theorem | 7, single chain | the simplest graph shape; a *problem-theorem* key problem (the corpus's most-referenced entry) |
| `No00005-example.*` | [5](https://zadachi.mccme.ru/2012/#&task5) — a chord through concentric circles | 8, one branch | alternative endings: a Pythagoras route and an intersecting-chords route |
| `No01204-example.*` | [1204](https://zadachi.mccme.ru/2012/#&task1204) — **Varignon's theorem** (1731) | 7, one branch | construct-and-derive vs. invoke-the-theorem |
| `No01622-example.*` | [1622](https://zadachi.mccme.ru/2012/#&task1622) — **Menelaus' theorem** (1st c. AD) | 9, three paths | a compact graph with three distinct strategies |
| `No02729-example.*` | [2729](https://zadachi.mccme.ru/2012/#&task2729) — **Pythagoras' theorem** | 14, three paths | three classical proofs in one graph: similar triangles, area decomposition, incircle areas |
| `No05044-example.*` | [5044](https://zadachi.mccme.ru/2012/#&task5044) — **the Euler line** (1765) | 17, three paths | a rich graph for an advanced classical result |
| `solution-graph.gv` | [2034](https://zadachi.mccme.ru/2012/#&task2034) — trapezoid area | 20, three paths | Figure 1 of the article |

## The classical results (stated in our own words)

- **Varignon (1731).** The midpoints of the sides of an arbitrary
  quadrilateral are the vertices of a parallelogram. The graph shows the
  constructive route — draw a diagonal, apply the midline theorem in each of
  the two triangles — beside the direct invocation of the theorem itself.
- **Menelaus (1st century AD).** A line crossing the sides (or their
  extensions) of a triangle cuts them in ratios whose product is −1; the
  converse is a collinearity criterion. Three strategies appear: an
  auxiliary parallel line with similar triangles, a route through Thales'
  proportional-segments theorem, and the direct citation.
- **Pythagoras.** In a right triangle the square of the hypotenuse equals
  the sum of the squares of the legs. The graph encodes three classical
  proofs side by side: mean proportionals from the altitude (similar
  triangles), decomposition of areas, and an incircle-area computation.
- **Euler (1765).** In every non-equilateral triangle the circumcenter, the
  centroid, and the orthocenter are collinear — the Euler line.

These four (plus the inscribed-angle theorem of example 1) are centuries-old
results; their statements are in the public domain everywhere, which is why
they serve as the repository's fully self-contained examples.

## Rendering

With [Graphviz](https://graphviz.org) installed:

```sh
dot -Tsvg No01204-example.gv -o No01204-example.svg
dot -Tpng No01204-example.gv -o No01204-example.png
```

The `.gv` sources carry the same `K/O/M` semantics as the machine-readable
corpus graphs; pre-rendered `.svg`/`.png` sit next to each source.
