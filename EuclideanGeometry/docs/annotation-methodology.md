# Annotating geometry problems with the ontology — methodology manual

*Draft prepared 2026-07-24 from the article (arXiv:2509.02758), its
Supplementary Note 1, the original tooling (`tex2gv.py`), and the annotated
corpus. Items marked ⚠ are inferred from the data and await the authors'
confirmation.*

This manual describes how a geometry problem is annotated in the ontology
whose vocabularies are published in [`../catalogs/`](../catalogs/): what the
codes mean, how a solution graph is constructed, and what the per-problem
attributes express. It is written for teachers and researchers who want to
read the annotations, extend them, or annotate new problems consistently.

## 1. The three vocabularies

Solving a problem is modeled as deploying three kinds of *skills*:

- **Facts** (`K` codes) — axioms, theorems, lemmas, formulas: provable
  statements a solver invokes. Example: `K3` — the exterior-angle theorem.
- **Objects** (`O` codes) — figures and configurations given in the problem
  or constructed while solving. Example: `O2` — a right triangle.
- **Methods** (`M` codes) — techniques and strategies. Example: `M1` —
  solving geometric problems using equations.

A *method* is a well-defined technique; a *skill* in the pedagogical sense is
broader — recognizing when to apply a method, recalling the relevant facts,
identifying the pertinent objects, and combining them. The annotation tracks
skills at the granularity of these three vocabularies.

## 2. The code numbering scheme

Base entries are numbered sequentially within each vocabulary (`K1…`,
`O1…`, `M1…`). Two structured extensions:

- **Sub-facts.** A fact closely related to base fact *N* — a special case,
  refinement, or companion statement — is numbered `1000·v + N`, where *v* is
  the sub-item index. In the catalogs these appear with Id `N.a`, `N.b`, …
  Example: `K7` *criteria and properties of a parallelogram* has sub-facts
  `K1007` (rectangle), `K2007` (rhombus), `K3007` (square). `K1000` (Id 0)
  is the parallel postulate. The same convention appears among the special
  objects (`O1025` and up).
- **Stereometry offset.** The published catalogs cover *plane* geometry.
  The annotated corpus also contains ~2,700 solid-geometry problems whose
  graphs use a parallel vocabulary offset by **+10000** (e.g. `K10034`
  *criterion for a line perpendicular to a plane*, `O10006`
  *perpendicular to a plane*, `M10008` *"consider a cross-section"*), with
  the same sub-item convention on top. The stereometry catalogs (121 facts,
  173 objects, 36 methods) are not yet published in this repository;
  publishing them is planned as a later release.

One historical alias: the corpus refers to *parallel lines* as `O1000`;
early exports of the object table numbered it `O0`. `O1000` is canonical.

## 3. Solution graphs

A **solution graph** is a directed acyclic graph from a `Start` node (the
problem statement) to a `Done` node (the solution). Interior nodes are
catalog codes. Every directed path from Start to Done is a complete solution
strategy; distinct paths are genuinely different solutions.

Construction rules:

1. **Main chain.** List the skills of the primary solution in the order a
   solver needs them: recognize objects, apply methods, invoke facts. This
   ordered list, `Start → s₁ → s₂ → … → sₙ → Done`, is the main chain.
2. **Alternative paths.** Additional solutions are encoded by listing their
   extra nodes after the main chain and wiring them with explicit edges that
   branch off (and rejoin) the main chain. In the archival format (§5) the
   extra nodes follow an `@A` marker and the edges are given as `@R` chains.
3. **Key skills.** Nodes may carry a `K` flag (rendered with a red border in
   the examples): the skills the problem is *designed to exercise* — the
   target of Criteria 2–3 of problem selection in the article (the skill
   must be essential, with no reasonable way around it).
4. **Complexity.** 1 = a single chain; 2 = one alternative branch; 3 = more
   than one. (Computed exactly this way by the original converter.)

Good problem design, per the article: every path uses only skills the
student already has, the target skill appears on every path (no shortcuts
around it), or failing that, the target skill makes the solution markedly
simpler on its path.

Worked examples with rendered graphs: [`../examples/`](../examples/).

## 4. Per-problem attributes

Besides the graph, each problem carries attribute annotations. They fall
into two families that match Supplementary Note 1 of the article. Counts
below are over the 10,957-problem corpus.

**Graded attributes** (marker carries a value; proposed scale ⚠:
**2 = Yes, 1 = Perhaps, marker absent = No**, anchored on canonical cases
such as problem 1 — the inscribed-angle theorem — carrying `KEY 2`):

| Marker | Attribute (Supplement §Attributes) | In corpus |
|---|---|---|
| `KEY` | Key problem | 2,919 |
| `SYNT` | Synthetic problem | 8,849 |
| `TECH` | Technical problem | 9,662 |
| `KRASOTA` | Aesthetically pleasant problem | 4,234 |
| `STUD` | Educational problem | 9,547 |
| `OLIMP` | Competition problem | 3,632 |
| `OFORM` | Formal problem (*оформление*: hard to write up formally) | 1,117 |
| `SLON` | Cumbersome problem | 508 |
| `IMP` | Important problem | 8,053 |
| `RES` | ⚠ rare, semantics to be confirmed | 12 |

**Type flags** (marker present with no value = Yes; the Supplement's
"attributes determining problem type and answer form"):

| Marker | Type | In corpus |
|---|---|---|
| `CALC` | Computational problem | 6,624 |
| `PRV` | Geometric proof problem (site label: «Задача на доказательство») | 4,596 |
| `BLD` | Geometric construction (*построение*) | 557 |
| `LOCUS` | Locus problem | 210 |
| `MINMAX` | Finding maximum or minimum | 346 |
| `RAZR` | Cutting geometric figures (*разрезание*) | 25 |
| `GNER` | Geometric inequalities | 495 |

(`PRV` = proof is author-confirmed and matches the public database, which
displays the attribute as «Задача на доказательство»; empirically, 211 of a
250-problem random sample of `PRV`-flagged problems begin with "Докажите…".)

**Difficulty** (`@C DIFF n`, in a few files `@!DIFF n`): the 1–40 scale of
the article — 1–10 basic school tasks; 11–20 competitions and advanced
classes; 21–30 Olympiad-level; 31–40 very difficult.

**Cross-links.** A problem carries up to five kinds of link to other
problems. Three are *displayed by the public database* and were mapped
field-for-field against its machine record (`texts.js`):

| Marker | Meaning | Links (corpus) |
|---|---|---|
| `@S` | *Descendants* — problems whose solutions build on this one (site: «Задачи-потомки») | 4,457 |
| `@P` | *Ancestors / prerequisites* — the problems this one builds on (site record field 9; ~27% also appear as "см. задачу" citations in the solution prose) | 15,638 |
| `@B` | *Analogous problems* — 73% symmetric (if X lists Y, Y lists X), i.e. a mutual "similar problem" relation (site record field 10) | 10,023 |

Two more are *internal editorial layers, not shown on the public site* and
point into small, stable, curated pools of problems — best understood as
**references to a catalog of "reference problems" (опорные задачи) that is
not part of this repository**:

| Marker | Target pool | Links | Notes |
|---|---|---|---|
| `@W` | 434 problems, concentrated in the low "foundational" numbers (#300–999) | 16,183 | ⚠ the reference-problem(s) a solution reduces to; catalog not published |
| `@Y` | 81 problems forming one contiguous themed block (#1935–2019) | 6,359 | ⚠ pointer into a themed reference section; catalog not published |

Provenance links: source-book references and, where known, the problem's
author.

## 5. The archival annotation format

The corpus stores one TeX file per problem. All annotation lines start with
`@`; everything else is prose (statement, solution) and is ignored by the
tooling. Reference: `tex2gv.py` in the corpus repository.

| Marker | Content |
|---|---|
| `%Задача номер N; id=M` | header comment: problem number and database id |
| `@T…` | problem statement follows |
| `@?S`, `@?A`, `@?C`, `@?U` | solution, answer, hint/comment, corollary follow |
| `@C SR <code> <page>` | source-book reference (codes resolve via the sources catalog) |
| `@C AV <code>` | problem-author reference (codes resolve via the authors catalog) |
| `@C DIFF <n>` | difficulty |
| `@!KEY/@!KRASOTA/@!STUD/@!IMP/@!PRV [v]` | attributes |
| `@G` | solution-graph section begins |
| `@O n [K]`, `@M n [K]`, `@K n [K]` | graph nodes, in main-chain order; trailing `K` = key skill |
| `@A` | end of main chain; extra nodes for alternative paths follow |
| `@R f₁ t₁ t₁ t₂ …` | alternative-path edge chain (1-based node indices; `U` = Start, `R` = Done) |
| `@S n` | descendant link («Задачи-потомки»; site record field 11) |
| `@P n` | ancestor / prerequisite link (site record field 9) |
| `@B n` | analogous-problem link, mostly symmetric (site record field 10) |
| `@W n` | internal link into the reference-problem catalog (⚠ not on site) |
| `@Y n` | internal link into a themed reference block (⚠ not on site) |

Additional markers seen in the corpus but outside the scope of this manual:
`@H` (a superscript/typographic marker inside prose), `@F`, `@U` and a few
one-off control codes. The five link markers above plus the graph and
attribute markers cover the machine-readable annotation layer.

The public, text-free export of this layer (one JSON record per problem) is
produced by the corpus repository's extraction tooling; ontology codes in it
resolve against the catalogs published here.

## 6. Annotating a new problem — checklist

1. Solve the problem; identify every distinct solution worth encoding.
2. For the primary solution, list objects recognized, methods applied, and
   facts invoked, in order — the main chain. Prefer existing catalog
   entries; propose a new entry only when nothing fits (new sub-facts take
   the `1000·v + N` code of their base fact).
3. Encode alternative solutions as branches; mark the key skills.
4. Assign difficulty (1–40) and the applicable attributes.
5. Record provenance (source, author) and links to similar problems.
6. Reference the problem by its database URL — do not copy statement text
   into public artifacts (see the repository's licensing/copyright notes).
