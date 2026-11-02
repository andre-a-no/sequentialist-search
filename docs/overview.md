# sequentialist-search: planning overview

English · [Русский](overview.ru.md)

## Current status

This is a planning-only repository. It has no source package, installation
procedure, public API, command-line tool, running service or executable examples.
References to `sequentialist-search` in earlier `sequential-search` architectural
decisions describe an intended wrapper, not proof that such a wrapper exists.

The exact responsibility of this repository is still open. A separate engineering
package should be justified by repeated application needs, rather than by a name
or by duplicating existing libraries.

## Potential role

The Sequentialist ecosystem distinguishes mathematical/cybernetic methods from
software engineering and application software. A future `sequentialist-search`
could connect search algorithms to reusable application workflows: obtaining
inputs, invoking subject-specific expansions or validators, recording task
progress and presenting outcomes through existing engineering infrastructure.

These are design candidates. No runtime, adapter or persistence capability is
implemented or promised by the current repository.

## Planned use cases

- **Information retrieval:** coordinate source acquisition and result validation
  around a search task while preserving source provenance.
- **Reasoning and proof construction:** connect domain-specific inference rules
  and checking tools to a search algorithm, keeping assumptions and unresolved
  obligations visible. This does not imply an implemented olympiad solver.
- **Diagnostic search:** connect candidate causes, proposed measurements and
  subject constraints to a search workflow. The domain package would own the
  meaning and admissibility of each measurement and conclusion.
- **Resumable application work:** integrate search-state envelopes with the
  existing durable task machinery when this is justified by concrete tasks.

All four are planned examples for evaluating the package boundary. They are not
current features, and they do not require every domain application to depend on
this repository.

## Candidate inputs and outputs

The following describe concepts for discussion, not data schemas or callable APIs.

Possible inputs:

- A goal, known facts or observations, and explicit assumptions.
- Domain-owned expansion functions, constraints and result validators.
- A selected algorithm from `sequential-search` and declared resource limits.
- Application adapters for sources, tools, durable execution and reporting.

Possible outputs:

- A candidate or validated result with its provenance and assumptions.
- Open goals and missing premises when a result remains conditional.
- Recorded resource consumption and an explicit stop reason.
- Search-state data suitable for an agreed engineering persistence adapter.

An answer's validity, a search algorithm's completeness and statistical error
control are separate claims. A wrapper cannot infer any of them merely by
executing a search or converting a tool score into a number.

## Package boundaries

| Package | Responsibility |
|---|---|
| `sequential-search` | Mathematical search methods, algorithmic state and search abstractions; inspect that repository for actual supported capabilities |
| `sequentialist-search` | Reserved potential engineering integration layer; responsibility and APIs still under design |
| `sequentialist-agentic` | Agent/tool and LLM integrations; not a mandatory dependency for all search applications |
| `sequentialist-core` | Existing reusable application execution, storage, journal, audit and reporting infrastructure |
| Domain packages | Subject-specific goals, facts, rules, observations, constraints and validation |

General applicability alone does not make code mathematical. An operational
queue or service remains engineering even when many applications can use it.
Conversely, a pure search algorithm does not belong here simply because its
first example concerns documents or proofs.

## FAQ

**Can I install or run this library now?**

No implemented library or installation workflow is provided by this repository.
Consult the mathematical `sequential-search` repository for its current code.

**Is this another name for `sequential-search`?**

No. `sequential-search` owns mathematical/cybernetic search methods. This name is
reserved for a possible engineering layer whose exact scope is unresolved.

**Does it require LLMs?**

No such requirement is proposed. Deterministic tools and explicit rule systems
are valid application inputs. Agent and LLM integration belongs to `agentic`.

**Does it replace `sequentialist-core`?**

No. Durable execution, journal and audit should reuse the existing infrastructure
through an explicit integration if this package is implemented.

**Must clinical, industrial or other applications depend on it?**

No. They may use `sequential-search` directly. A common wrapper is justified only
when it removes demonstrated engineering duplication without hiding subject rules.

## Next design decisions

1. Identify repeated engineering needs in at least two concrete search applications.
2. Separate those needs from mathematical methods and existing core responsibilities.
3. Decide whether a standalone package is warranted and define a bounded first scope.
4. Specify integration contracts and executable acceptance cases before advertising APIs.

This document does not commit to a package version, dependency graph,
implementation schedule or new service architecture.
