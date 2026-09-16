# Durable effort records

Use the record named by the project's tracker protocol, such as an existing
issue, effort map, or tracked document. Conversation memory alone is insufficient.
Keep one shared effort record; lanes can link their own evidence and handoffs.
For a small request, a short batch entry is enough.

## Decisions so far

Record the effective decision policy and significant choices affecting product
behavior, architecture, cost, scope, or later work. Include the date, whether
the owner or agent decided, the reason, and the practical consequence. Skip
ordinary coding details. Put lasting project policy in its permanent document
and link it from the effort record, keeping one authoritative current statement.

## Authorizations and deferrals

Record the owner's instruction or a precise source reference, the permitted or
deferred action, scope and environment, limits, and duration or end condition.
Store no secret values. When duration is unstated, retain the original task
scope; neither a handoff boundary nor indefinite authority may be invented.
Owner deferrals apply until their end condition or a superseding instruction.

Read these entries at start and resume. Update changed decisions or authority,
mark superseded entries, and preserve previous entries and the reason in the
record's comment history. During parallel work, the orchestrator owns the shared
record; lanes report changes for consolidation instead of racing to edit it.

## Handoffs and evidence

Include the objective, effective decision policy, applicable decisions and
authority, branch/worktree, exact candidate, retained lane and resource state,
completed checks, remaining gates, and next action. Prefer accessible record
pointers. If the receiver cannot read a record yet, include the relevant entries
until the checkpoint is available. Never assume local temporary paths exist on
another host.

Default an unspecified handoff to full ownership transfer of the agreed task.
The writing agent infers the handoff type from the user's request and actual work.
Choose a narrower role when that intent or an existing responsibility calls for
it, such as an independent review or one delegated verification step, and record
the concrete reason. Do not narrow the assignment merely because another agent
will execute it, the sender cannot perform it, or a cautious template suggests it.
No extra question is needed just to select the default.

The receiver owns completing the transferred outcome, including implementation,
diagnosis, corrections, and required verification within the existing authority.
A first suggested action is a starting point, not the entire assignment. Transfer
the relevant acceptance/integration role when it belongs to the handed-off effort;
do not leave the departed sender as a required approver. Keep an explicitly
assigned independent review or human gate intact. Full ownership concerns the
agreed task; it does not expand its scope or external-action permissions.

Write the handoff around the outcome and relevant knowledge: established facts,
reasoning behind decisions, attempts and their results, unresolved questions,
useful evidence, and what done means. Distinguish facts from hypotheses. Let the
receiver choose and revise tactics instead of prescribing an unnecessarily rigid
sequence of steps or making the sender's suggestions into acceptance criteria.

Separate binding restrictions from sender observations and suggested tactics.
Carry a restriction only with its actual owner instruction, applicable project
rule, or enforced permission source and scope. A sender's missing CLI, unsupported
OS, failed command, or temporary sandbox limit is diagnostic context, not a ban on
the receiving host. The receiver inspects its own tools and may use available CLI,
shell, APIs, browser tools, builds, and tests within actual permissions. Commands
and approaches in the handoff may be adapted to the host while preserving the
outcome and acceptance criteria.

Do not invent read-only, no-CLI, no-fix, or return-to-author requirements. Read the
recorded transfer as the ownership assignment; ask the owner only about a concrete
authority gap, conflicting active ownership, or a reserved decision. The receiving
agent reports completion to the user or assigned recipient and need not reconnect
with the sender. If an older handoff contains an unsupported restriction, inspect
its source and scope rather than automatically turning it into a new approval gate.

Preserve commands, results, source commits, artifact locations, review findings,
and dispositions. Evidence reused from another commit retains its original SHA
and an explanation of why it applies. Distinguish implementation, acceptance,
upload, processing, and distribution when those stages exist.

Publish records using the project's tracker and assigned authority. For a Git
tracker, commit and push them with an authorized work checkpoint. A local-only
record is not yet available to another checkout or machine; make that limit
explicit in the handoff. If Git publication is not authorized, leave it pending
and pass the necessary context through the authorized handoff channel.

For a handoff to another computer or colleague that needs a Git checkpoint and a
short starter prompt, use [handoff-git](../skills/handoff-git/SKILL.md). It owns
publication, dependency reachability, and receiving-host setup; this document
continues to own the content and scope of durable records.
