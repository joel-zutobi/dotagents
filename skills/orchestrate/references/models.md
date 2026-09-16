# Model selection and freshness

Read when staffing an effort, resolving an unfamiliar requested model, or
recommending a model. Separate three questions: what the owner requested, what
the current tools can run, and what evidence supports a model for this role.

## Resolve the request and availability

Honor explicit model, provider, effort, budget, and fallback choices. Inspect
the model identifiers and settings exposed by the actual dispatch tool for each
effort. For CLI lanes, use documented local discovery and verify the selected
CLI. A provider's public catalog does not establish access through this tool,
account, subscription, or host. Keep availability separate from capability.

Resolve unfamiliar names against current official sources immediately when the
research policy below permits it, even if the general evidence is fresh. Under
`ask`, request that lookup; under `off`, use verified tool identifiers and state
any unresolved meaning without launching automatic research. An explicit request
to research overrides those project defaults. Preserve an explicitly requested version. For an
ambiguous family name, use the owner's established meaning or a documented tool
alias; ask if the unresolved interpretation would materially change the choice.
Never replace a requested model simply because it is absent from training memory.

## Refresh when selection needs it

Default model research is `on-demand`, with a 14-day maximum evidence age.
Projects may choose `ask` or `off`, or set a different interval. This is a
freshness rule evaluated during model selection, not a timer or scheduled job.

Read the user's shared local evidence cache. If the relevant provider/model
coverage is absent, older than the interval, or contradicted by a new release
or observed availability, refresh the relevant evidence before relying on it
for a new recommendation. An explicit available model can start while unrelated
research proceeds; do not hold up work for a ranking the owner did not request.

Use one economical research agent with browsing when delegation is permitted.
Assign a bounded question covering the relevant providers and roles, and keep
independent work moving. The lead can perform a small lookup itself when a
subagent would add more overhead. Under `on-demand`, this is ordinary authorized
research; under `ask`, obtain the owner's agreement before refreshing. Under
`off`, skip automatic source research and report stale or missing evidence rather
than representing it as current. Tool availability checks still apply.
Ask for additional authority only when the proposed work exceeds existing
permissions or cost constraints. Do not start paid benchmark workloads as part
of a documentation refresh.

Research official model catalogs, model cards/evaluations, pricing, and relevant
client documentation. Record source URLs, access dates, exact IDs and versions,
supported effort/settings, documented strengths, latency/cost tradeoffs, and
uncertainties. Distinguish provider claims from independent measurements and
task-specific judgment. Compare relevant roles, not one universal leaderboard.
API token prices are not a measurement of subscription cost or remaining quota.

Useful starting points include the providers' current model indexes:

- [OpenAI model guidance](https://learn.chatgpt.com/docs/models)
- [OpenAI API model catalog](https://platform.openai.com/docs/models)
- [Anthropic model catalog](https://platform.claude.com/docs/en/models/overview)

Follow their current links rather than assuming a remembered model name or
price. Other owner-selected providers use their equivalent official sources.

## Keep automatic state outside Git

Use one per-user cache across projects. Default to
`%LOCALAPPDATA%/dotagents/model-research/` on Windows and
`${XDG_CACHE_HOME:-$HOME/.cache}/dotagents/model-research/` on macOS/Linux.
Use a permitted user-local temporary/cache directory if that location is
unavailable, and state the location. Never put automatic check state in a
project, tracked dotagents files, or a secret-bearing agent configuration file.

A short `evidence.md` is enough: coverage, last successful research date for each
provider/model group, findings, source links, and uncertainties. Record a failed
attempt separately without advancing the successful date. If research fails,
retain the previous evidence, label it stale, avoid repeated identical attempts
in the same effort, and continue with explicit choices or an authorized fallback.
An orchestrator owns the refresh for its effort and passes the result to lanes;
each lane need not launch its own researcher.

Record the models actually selected and the evidence/date used in the project's
effort record for reproducibility. A new research result can inform future lane
selection. It does not change running agents or silently override an owner's
pairing. Report material new findings when they affect an upcoming decision;
unchanged cache maintenance needs no user notification.
