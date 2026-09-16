---
name: orchestrate
description: Coordinate implementation in projects that use the dotagents workflow, including Light or Thorough orchestration, persistent coding lanes, UI iteration, and optional advisors. Follow an existing project-owned orchestration workflow when one is configured instead.
---

# Orchestrate

## Resolve the project's workflow

Read the project's agent instructions first. If they select a project-owned
orchestration skill or another workflow, read and follow that workflow instead
of this one. Do not migrate the project or merge competing process defaults.

For dotagents projects, read the [shared base](../../instructions/base.md) and
the project's settings and tracker protocol. This skill ships with the complete
dotagents checkout; keep its `instructions/` dependency accessible. If it is
missing, use an accessible copy explicitly named by the project or report the
missing dependency rather than inventing its contents.

Inspect the accepted base, active lanes, worktree, and existing evidence. Reuse
the effort record. Choose and briefly state the mode, decision policy, review
shape, useful lanes, and verification plan. Record reasons once. A small
correction needs a short batch entry, not a fresh planning exercise.

## Select mode and staffing

| Mode | Choose when | Working shape |
| --- | --- | --- |
| Light | Approved design, understood fix, or established pattern with intact contracts. | Batch connected changes, run focused checks, accept a coherent candidate. |
| Thorough | Uncertain architecture or cross-system contracts; significant migration, consent, destructive data, financial, or shared-resource risk. | Investigate the uncertainty, establish contracts and failure checks, implement verified increments. |

Choose automatically when unspecified. `Orchestrate Light` or `Orchestration
Light` selects Light; `Orchestrate Thorough`, `Orchestration Thorough`, or
`standard orchestration` selects Thorough. File and ticket counts do not select
the mode. Isolate risky portions rather than escalating an entire mixed effort.

`with human decisions` selects the shared base's human-led decision policy with
either mode. Natural-language policy overrides work too. `with advisor` selects
the [advisor profile](references/advisor.md), independently of mode, decision
policy, and review shape. These options can be combined.

Before selecting or recommending models, read [model selection and freshness](references/models.md).
Honor explicit model, effort, budget, and fallback instructions. A configured
pairing is a preference to resolve against actual available tools, not proof a
running agent changed model.

For presentation work in Light or an explicit UI iteration request, read the
[UI iteration profile](references/ui-iteration.md). Keep functional checks for
any behavior changed along with presentation.

## Choose reviews independently

Honor explicit combined, dual, or waived-review instructions and project gates.
Otherwise choose per coherent batch:

| Shape | Use when | Coverage |
| --- | --- | --- |
| Orchestrator acceptance | Documentation, mechanical or presentation-only work with clear evidence, or an explicit waiver. | Check scope, result, and visual evidence where relevant. Do not call this independent review. |
| Combined review | Bounded behavior or implementation changes need independent review. | One non-author checks both specification and engineering standards. |
| Dual review | Distinct high-impact risks warrant separate perspectives, or the owner/project requires it. | Two non-authors cover distinct scopes on the same candidate. |

Thorough does not automatically require dual review. Final integration does not
automatically trigger fresh reviewers. Reviewers inspect a pinned candidate and
report concrete findings with the requirement, reachable scenario, impact, and
supporting evidence. They reuse valid native results instead of repeating builds.
Adjudicate under the shared base before assigning corrections.

Return accepted findings to the same coder, retain its branch and worktree, and
recheck affected scope. Broaden review only when changes invalidate coverage or
expose an uncovered risk. Waiving review does not waive relevant tests or visual
acceptance. If an independent reviewer cannot run, report that gap honestly.

## Reuse lanes and respect dependencies

Organize lanes by connected flow, subsystem, or dependency chain. Keep the same
coder, worktree, branch, caches, and build root through related tickets and
corrections. Add lanes only when they can make useful independent progress within
the host's worker limit and permitted delegation. Replace lanes only when their
availability, expertise, or context no longer fits the work.

Read [dispatch and resource ownership](references/dispatch.md) before dispatching.
The orchestrator selects work, adjudicates results, and owns acceptance and
integration. A merger performs assigned mechanics only. Reviewers remain
independent of authors; keep review and release roles explicit in the record.

Treat tickets as a dependency graph. In Light, one lane may batch connected
dependent tickets after recording each prerequisite's checked local checkpoint.
External dependencies must already be accepted. Other lanes consume accepted
checkpoints only. Preserve each ticket's acceptance and status; close only
satisfied tickets and then recalculate the frontier.

## Verify coherent candidates

Record affected behavior/screens, existing evidence and source SHA, intended
checks/builds with their purposes, and acceptance owner. Finish a coherent
source pass before building. Build counts are estimates, not limits that excuse
unresolved failures. Use the project's commands, required hosts, and scheduler.

Reuse compatible builds and installed applications across checks. Repeat checks
only for changed source that invalidates evidence, a failure needing diagnosis,
an uncovered required configuration, or an explicit gate. Preserve the original
SHA of reused evidence and explain applicability. Repeated failure without new
evidence calls for bounded diagnosis, not identical retries.

Separate release artifacts from development verification when the platform
requires it. Reuse release-configuration coverage when project rules allow.
Keep unavailable credentials, physical-device checks, provider evidence, and
release gates visible. A successful build alone does not prove the requested
behavior or design was delivered.

## Accept, integrate, and report

Accept the exact candidate against the agreed outcome and chosen checks/review.
Integrate only within assigned Git ownership. Inspect integration changes and
uncovered risks while reusing valid prior coverage. Close completed work in the
configured tracker; create or update a real PR only when that workflow calls for
one and its publication is authorized.

Use the shared base's progress and completion rules. Preserve decisions,
authorizations, evidence, lane state, unresolved gates, and next action in the
effort record. Dispatch a release only within explicit release authority and
verify its actual stages separately. Clean up only owned resources after they
are no longer needed for corrections, review, or integration.

## Work with imported skills

Use imported skills for their specific techniques and evidence, keeping their
source files unchanged. In projects that adopt this workflow, the project
instructions assign orchestration ownership here: mode, batching, lane reuse,
review shape, finding disposition, verification reuse, and Git operations.

When the owner invokes `implement-spec`, read its spec and ticket graph, then
execute through the selected workflow. Per-ticket worktrees, unconditional PR
creation, a blanket final review cycle, and fixing every reviewer comment do not
override that project's adopted process. Apply the same boundary when invoking
`implement` or `code-review`; retain their substantive checks. An explicit owner
request to use an imported workflow unchanged takes precedence.
