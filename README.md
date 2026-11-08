# sequentialist-search

A reserved, potential software-engineering layer for search applications in the
Sequentialist ecosystem. **This repository currently contains planning and
discovery documentation only. There is no implemented package, public API,
runtime or general-purpose solver here.** Its exact responsibilities remain a
design decision.

## Conceptual framework: the Sequentialist ecosystem

The ecosystem studies sequential decisions: observations arrive, evidence
changes, and a policy chooses whether to continue, act, wait or stop. It separates
three questions within the mathematical and cybernetic methods layer:

| Library | Central question | Responsibility |
|---|---|---|
| [sequential-analysis](https://github.com/andre-a-no/sequential-analysis) | What can we infer from the observations available so far? | Statistical tests, estimation, filtering, prediction and procedure-specific uncertainty guarantees. |
| [sequential-search](https://github.com/andre-a-no/sequential-search) | Which step should we explore next to reach an answer or a goal? | Search and reasoning over alternatives, experiments and rules, with explicit evidence, provenance and resource costs. |
| [sequential-games](https://github.com/andre-a-no/sequential-games) | How do participants pursue their own goals while their actions change a shared environment? | Interaction models for cooperation, competition and partially aligned interests, including asynchronous actions, local information and deliberate waiting. |

These are complementary responsibilities. A participant's policy can use search
to plan and statistical analysis to interpret observations; other participants
continue to act according to their own objectives. This describes how the
methods can be composed. Each package's implementation status is stated
separately below.

The naming convention expresses a further separation into three layers:

| Layer | Packages | Responsibility |
|---|---|---|
| Mathematical and cybernetic methods | `sequential-*`: analysis, search, games | Models, algorithms, explicit state and the assumptions under which a result holds. |
| Reusable engineering platform | `sequentialist-*`, including [core](https://github.com/andre-a-no/sequentialist-core) and [visuals](https://github.com/andre-a-no/sequentialist-visuals) | Durable application execution, storage, recovery, audit and presentation, according to each package's implemented scope. |
| Domain applications | `sequentialist-*`, including [ab](https://github.com/andre-a-no/sequentialist-ab), [quality](https://github.com/andre-a-no/sequentialist-quality), [monitor](https://github.com/andre-a-no/sequentialist-monitor), [clinical](https://github.com/andre-a-no/sequentialist-clinical) and [agentic](https://github.com/andre-a-no/sequentialist-agentic) | Subject-specific goals, workflows, adapters and user-facing decisions built from the methods and engineering components they need. |

Both the engineering platform and applications use the `sequentialist-*`
prefix. The platform is an open family of reusable packages; `core` currently
provides durable tasks built around `sequential-analysis` runs. This organization
does not imply that every combination already has an integration.

Across the ecosystem, state, information available to a decision, randomness,
costs and stopping reasons should be explicit. Evidence, resource expenditure
and real-world effects have separate meanings. Statistical validity, derivability
under supplied rules, properties of an interaction model and reliable execution
each require their own justification; a guarantee in one layer does not
automatically establish a guarantee in another.

### This package's role

**Layer: proposed reusable engineering package; planning only.**
The name is reserved for possible shared execution and integration around search
tasks. Mathematical search belongs to `sequential-search`, agent/tool workflows
to `sequentialist-agentic`, and existing durable task infrastructure to
`sequentialist-core`. Exact scope and APIs remain undecided; no implementation
or mandatory dependency for other applications is established.

[sequential-search](https://github.com/andre-a-no/sequential-search) owns the
mathematical search algorithms. A future `sequentialist-search` could provide
reusable engineering around search tasks if concrete applications demonstrate
that need. It should not duplicate the mathematics or the existing durable
execution infrastructure of
[sequentialist-core](https://github.com/andre-a-no/sequentialist-core).

Candidate applications include information retrieval, verified reasoning and
diagnostic search. These are **planned use cases**, not implemented capabilities.
LLMs are optional: [sequentialist-agentic](https://github.com/andre-a-no/sequentialist-agentic)
provides a separate place for agent/tool integrations. Domain packages can use
`sequential-search` directly without this proposed wrapper.

Read the overview and FAQ in [English](docs/overview.md) or
[Russian](docs/overview.ru.md) for candidate inputs/outputs,
package boundaries and unresolved design questions. The curated documentation
index is [llms.txt](llms.txt); contributor and assistant context is in
[AGENTS.md](AGENTS.md).
