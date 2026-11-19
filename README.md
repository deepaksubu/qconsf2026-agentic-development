# Agentic Development for Senior Engineers

### *Own the edges. Delegate the middle.*

Talk at **QCon San Francisco 2026**

**Speakers:** Clinton Farleigh · Deepak Subramanian · Madhan Subramanian

📄 **Slides:** [`slides.pdf`](./slides.pdf)

---

## The one-line pitch

Code got cheap. Boundaries didn't. When an agent can write an implementation in minutes, a senior engineer's leverage moves from writing code to **choosing boundaries, owning interfaces, and deciding what gets reviewed**.

## What we covered

| # | Idea | Takeaway |
|---|------|----------|
| 1 | **Code got cheap. Boundaries didn't.** | Implementations, alternatives and rewrites are now cheap. Choosing boundaries, changing interfaces and integrating across teams are still expensive. |
| 2 | **Think in boxes** | Each box is one bounded solution (Planner, Executor, Result Cache). You own the *edge* (the contract). Agents explore the *interior*. Decompose before you prompt. |
| 3 | **Explore each box** | Close the box → fan out 3–5 agents → score at the edge with contract tests and benchmarks → keep one, delete the rest without regret. |
| 4 | **C4 diagrams are specs, not pictures** | Context, Container, Component and Code each narrow what an agent may decide. Code is the agent's job. |
| 5 | **Make the spec machine-readable** | One architecture-as-code source drives agent scope, CI dependency rules, and generated contract-test stubs. |
| 6 | **Contracts outlive implementations** | Types and schema, invariants, error semantics and budgets (p99 latency, cost per call) define the edge. Any implementation that passes is valid. |
| 7 | **Review the edges, not the diff** | Stop reviewing 2,000-line agent PRs for style. Review interface and schema changes, new cross-box dependencies, and changed invariants or budgets. |

## Example: a machine-readable spec

```text
container "Query Service" {
  planner  = component "Planner"
  executor = component "Executor"
  cache    = component "Result Cache"

  planner  -> executor "execute(Plan): Rows"
  executor -> cache    "get(Key): Rows?"
}
```

From this single source:

- **Agent scope:** each component becomes one bounded session.
- **Dependency rules:** CI fails if Planner calls Cache directly.
- **Contract tests:** every arrow generates a test stub.

## Three things to take home

1. **Decompose into boxes before you prompt.**
2. **Treat C4 as the spec your agents read.**
3. **Put review effort into contracts.**

---

## Let's talk

If you were at QCon SF, or you're working out how to bring agents into a large codebase without losing control of the architecture, we'd love to hear what's working for you. Find us on LinkedIn and let's compare notes.

- [Clinton Farleigh](https://www.linkedin.com/in/clintonfarleigh/)
- [Madhan Kumar](https://www.linkedin.com/in/psmadhankumar/)
- [Deepak Subramanian](https://www.linkedin.com/in/deepaksubu/)