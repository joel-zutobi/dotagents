# Shared agent instructions

Use this base in projects that opt into dotagents. Read the project's own agent
instructions and linked settings first. Explicit task instructions take
precedence over project defaults; project differences take precedence over this
base. Respect the host's permissions and higher-priority instructions throughout.
Existing projects with their own workflow keep it until the owner adopts this base.

## Start and resume

Inspect the worktree, governing files, assigned outcome, acceptance criteria,
and current effort record. The tree and runnable tools are the source of truth
for facts you can inspect. Preserve unrelated edits and existing work in progress.
Read recorded decisions, authorizations, and deferrals before repeating a question.
For a small direct request, the request and a short effort record can be enough;
do not invent a specification or ticket graph.

## Make decisions within authority

Decision policy defaults to `agent-led`. An explicit task instruction overrides
the project's setting. Natural-language instructions such as "ask me about
product decisions" or "make decisions and tell me afterwards" are sufficient;
preserve any narrower scope the owner gives.

- **Agent-led:** make reasonable product and architecture decisions within the
  agreed outcome, scope, and authority. Record significant choices and continue.
- **Human-led:** request meaningful product and architecture decisions with a
  recommendation and its consequence. Choose routine implementation details and
  continue independent authorized work while waiting.

Ask before exceeding authority, contradicting an explicit requirement, changing
the objective or scope, or making a consequential commitment that is not
reasonably reversible and is not already authorized. Decision policy is separate
from orchestration mode, staffing, and review shape. It grants no additional
spending, account, security-policy, signing, publishing, or release permission.

Use the project's durable effort record following [recordkeeping](records.md).
Carry applicable authorizations and deferrals into affected lanes and handoffs
with their source, scope, environment, limits, and duration. Reuse approval that
still applies. A new session or lane does not reset it or extend its boundaries.
Record changed or revoked authority before dependent work continues.

## Get approval before adding backward compatibility

Do not introduce backward compatibility without explicit human approval, even
in agent-led mode. This includes legacy adapters, fallback behavior for old
clients or data formats, and parallel old/new implementation paths. Do not infer
a requirement from hypothetical consumers or edge cases.

When compatibility appears necessary, identify the actual consumer or contract,
what would break, and the added complexity compared with a simpler alternative.
Recommend an approach and obtain approval before implementing the extra support.
Continue unaffected authorized work while waiting.

An explicit compatibility requirement or recorded approval already covering the
work satisfies this gate; carry it through lanes and handoffs without asking
again. Preserve existing required compatibility unless its removal is authorized.
Ordinary validation and error handling do not need this approval unless they add
support for legacy behavior.

## Keep implementation proportional

- Reuse before creating. Search for existing shared and platform-native
  components or helpers and inspect their callers. Reuse a suitable equivalent;
  extend it for a concrete requirement only when the shared abstraction remains
  coherent. Create a separate implementation when reuse would compromise
  behavior or maintainability, and record that reason. Keep unrelated
  consolidation outside the task.
- Prefer the smallest adequate implementation and follow existing patterns.
  Before adding custom infrastructure, explain why an existing tool or bounded
  manual fallback is insufficient. This explanation is not a new approval gate.
- Write user-facing copy for a user decision or consequence. Keep a helper,
  status, or error message when it helps the user act, understand the outcome,
  or recognize a material data, privacy, or payment effect. Keep routine backend
  cleanup and diagnostics out of product copy. Pending background work is a
  pending state unless it creates a real user-visible failure.
- Keep the patch within the agreed scope. Record unrelated findings separately.
- For testable behavior and regressions, establish a meaningful failing check,
  make it pass, and refactor while it stays green. Use visual evidence for
  presentation changes; avoid tests that merely restate decorative constants.
- Run focused checks, then the required project gates. Reuse evidence that still
  applies to the candidate and explain its applicability. New tickets, handoffs,
  status requests, and documentation edits alone do not justify repeated builds.
- Report failures and missing evidence. Preserve tests, diagnostics, and
  acceptance criteria rather than weakening them to obtain a pass.
- Keep credentials, private keys, signing material, customer content, and other
  sensitive data out of Git and ordinary logs or prompts. Follow the project's
  actual data-transfer and provider permissions.

## Adjudicate review findings

Review findings are evidence, not an automatic implementation queue. The
acceptance owner assigns each finding a disposition:

- **Accept:** concrete, correct, in scope, and worth correcting now.
- **Reject:** incorrect, unsupported, hypothetical, preference-only, or handled.
- **Defer:** valid but outside the current scope; link a follow-up.
- **Escalate:** needs a decision or authority reserved for the owner.

Fix concrete failures in normal operation, realistic multi-session collisions,
material security or data-loss paths, and direct acceptance violations. Concrete
test-reliability or maintenance failures can also qualify. Keep correction
complexity proportional to the practical benefit. Record or reject timing-perfect
edge cases, negligible-probability filesystem substitutions, speculative
hardening, unrelated refactors, and fixes whose complexity outweighs their value.

Give short reasons for rejected, deferred, and escalated findings. Reviewer
severity does not determine disposition. A review passes when no accepted
blocking findings remain, not when every comment has produced a patch.
Independent review still matters; use the selected review shape and owner overrides.

## Explain progress and finish the task

Lead updates with what changed for the user or what the evidence means. Explain
remaining work in the agreed scope and the next meaningful milestone or required
user action. When delayed, explain the practical impact and what will resolve it.
Use technical details when they help assessment. Avoid repeated unchanged updates,
unsupported percentages, and fixed templates that add no information.

Answer side questions briefly, then continue unaffected authorized work.
Discussion alone does not cancel, pause, or expand the task. Change direction
when the owner actually changes the objective.

Preserve branches and commits. Create branches, commits, worktrees, merges, or
pushes only within assigned Git ownership. Report the changed behavior and files,
checks and results, candidate commit when applicable, missing gates, and next
action if blocked. Summarize significant agent and owner decisions the owner may
want to revisit, with a pointer to the record. That recap adds no approval gate.
