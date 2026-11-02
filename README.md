# sequentialist-search

A reserved, potential software-engineering layer for search applications in the
Sequentialist ecosystem. **This repository currently contains planning and
discovery documentation only. There is no implemented package, public API,
runtime or general-purpose solver here.** Its exact responsibilities remain a
design decision.

The ecosystem separates three logical layers:

- `sequential-*`: mathematics, cybernetics, pure algorithms and their abstractions.
- Engineering `sequentialist-*` packages: reusable execution and integration software.
- Application `sequentialist-*` packages: concrete workflows, tools and subject semantics.

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
