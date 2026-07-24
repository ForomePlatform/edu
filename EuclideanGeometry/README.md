# The Euclidean Geometry Ontology — Catalogs

This directory contains the annotation vocabularies (catalogs) of an ontology
for Euclidean geometry problems and their solutions, and a worked example of a
*solution graph* built from them.

The ontology was developed in 1991–1996 by R.K. Gordin, M. Bouzinier,
S. Trifonov, and I.F. Sharygin, and has since been used to annotate thousands
of geometry problems, most of which are publicly accessible in the problem
database at [zadachi.mccme.ru](https://zadachi.mccme.ru) (~16,000 problems).
It also served as a foundation for R.K. Gordin's book *Eto dolzhen znat'
kazhdyi matshkol'nik* ("Every student must know this", MCCME, 2003).

The ontology and its pedagogical applications are described in:

> M. Bouzinier, S. Trifonov, M. Chen, T. Venkatesh, L. Rifkin.
> *An Ontology-Based Approach to Optimizing Geometry Problem Sets for Skill
> Development.* [arXiv:2509.02758](https://doi.org/10.48550/arXiv.2509.02758)
> (submitted to the International Journal of Mathematical Education in Science
> and Technology). These catalogs are the data referenced in the article's
> Supplementary Note 1 and Data Availability statement.

## Structure of the ontology

Solving a geometry problem is modeled with three classes of *skills*:

- **Facts** (codes `K…`) — axioms, theorems, lemmas, and other provable
  statements of Euclidean geometry (e.g., *the sum of the interior angles of a
  triangle is 180°*).
- **Objects** (codes `O…`) — figures and concepts given in problem statements
  or constructed during solving (e.g., *right triangle*, *nine-point circle*).
- **Methods** (codes `M…`) — specific techniques and strategies applied to
  reach a solution (e.g., *the area method*, *dropping a perpendicular*).

Solutions are represented as **solution graphs**: directed acyclic graphs
whose nodes are facts, objects, and methods, encoding the skill dependencies
of each solution path (see `examples/`).

## Catalog files

| File | Language | Entries |
|---|---|---|
| `catalogs/english/facts_table_english.md` | English | 219 facts |
| `catalogs/english/objects_table_english.md` | English | 143 objects |
| `catalogs/english/methods_table_english.md` | English | 97 methods |
| `catalogs/russian/facts_table_russian.md` | Russian | 219 facts |
| `catalogs/russian/objects_table_russian.md` | Russian | 143 objects |
| `catalogs/russian/methods_table_russian.md` | Russian | 97 methods |
| `catalogs/translations/translations.md` | EN ↔ RU | translation tables for topics and statements |

The English and Russian catalogs are row-aligned: entry *N* of an English
table is the translation of entry *N* of the corresponding Russian table, and
shared codes (`K…`, `O…`, `M…`) identify the same entry across languages.

Column conventions:

- **Id / Code** — stable identifiers of an entry (facts additionally carry a
  numeric row `Id`).
- **Topic** (facts) — thematic grouping, e.g. *Facts related to parallel
  lines*.
- **Statement / Object / Description** — the entry itself.
- **As a Problem** — links to problems in the
  [zadachi.mccme.ru](https://zadachi.mccme.ru) database that exercise the
  entry, when such a problem exists.

## Example: a solution graph

`examples/solution-graph.gv` is the Graphviz source of Figure 1 of the
article: the solution graph of a trapezoid-area problem
([problem 2034](https://zadachi.mccme.ru/2012/jndex.html#&task2034)), with
nodes drawn from these catalogs. See `examples/README.md` for the legend and
rendering instructions.

## Provenance and credits

The catalogs were created in 1991–1996 by R.K. Gordin, M. Bouzinier, and
S. Trifonov, with a major intellectual contribution by I.F. Sharygin, and have
been curated since. The English translations were prepared in 2025–2026 by the
authors of the article above.

## License

The catalogs and all other content in this directory are licensed under
[CC BY 4.0](../LICENSE-CONTENT.md). Please attribute by citing the article
and the dataset (see [`CITATION.cff`](../CITATION.cff)).
