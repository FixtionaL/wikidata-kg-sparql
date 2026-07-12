# Wikidata Knowledge Graph Querying with SPARQL

**COMP6256 — Knowledge Graphs for AI Systems | University of Southampton**

A collection of 10 SPARQL queries implementing structured knowledge retrieval patterns over the Wikidata knowledge graph. Covers multi-hop property path traversal, subgraph aggregation, negation logic, and missing-data detection across real-world Wikidata entities.

---

## Query Tasks

| # | Task | Key Technique |
|---|------|---------------|
| 1 | Lonely Countries — sovereign states with exactly one border neighbour | GROUP BY + HAVING |
| 2 | Academic Lineage — doctoral students of Turing's advisees | Property path (P184/P184) |
| 3 | EGOT Gap — Academy Award winners without a Golden Globe | FILTER NOT EXISTS + subclass expansion |
| 4 | Scientific Gender Gap — Nobel Physics winners by gender | GROUP BY + VALUES |
| 5 | Polyglot Cinema — films with 4+ original languages | COUNT DISTINCT + HAVING |
| 6 | Political Education — heads of government with doctorates | Multi-condition subquery join |
| 7 | 27 Club — musical groups with 3+ pre-2000 member deaths | Group-member traversal + date filter |
| 8 | Chemical Composition — oxygen compounds without carbon | REGEX on chemical formula literals |
| 9 | Data Consistency Audit — humans with death date but no birth date | OPTIONAL + FILTER(!BOUND()) |
| 10 | Modern Metropolis — cities >1M population in post-1950 countries | Multi-entity filter with inception date |

---

## Running the Queries

All queries run on the public [Wikidata Query Service](https://query.wikidata.org/) — no setup required.

1. Open [query.wikidata.org](https://query.wikidata.org/)
2. Paste the contents of any `.rq` file into the editor
3. Press **Run** (or `Ctrl+Enter`)

> **Note on Task 9:** The aggregate count times out on the public WDQS endpoint due to the scale of the human entity class. Query logic has been verified correct using a preview LIMIT query — see `task9.rq` comments for details.

---

## Repository Structure

```
/queries
  task1.rq
  task2.rq
  task3.rq
  task4.rq
  task5.rq
  task6.rq
  task7.rq
  task8.rq
  task9.rq
  task10.rq
report.pdf
README.md
```

---

## SPARQL Techniques Demonstrated

- **Nested subqueries** for multi-step aggregation before outer counting
- **Property path syntax** (`wdt:P184/wdt:P184`) for transitive and multi-hop traversal
- **FILTER NOT EXISTS** and **OPTIONAL + FILTER(!BOUND())** for negation and missing-data detection
- **VALUES** blocks for controlled entity enumeration
- **GROUP BY / HAVING** for conditional aggregation over graph entities
- **REGEX** pattern matching on literal values (chemical formula strings)
- **Subclass expansion** (`wdt:P279*`) to capture hierarchical category membership

---

## Academic Context

Developed as coursework for COMP6256 — Knowledge Graphs for AI Systems, University of Southampton, 2025–26. All queries are original work submitted for academic assessment.
