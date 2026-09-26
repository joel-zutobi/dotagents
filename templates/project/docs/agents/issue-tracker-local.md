# Issue tracker: tracked Markdown

This project uses Git-tracked Markdown under `.scratch/` for work records.
No external issue service or pull request is required by this tracker. Publish
records with the work checkpoint when commit/push ownership is assigned.

## Layout and operations

- Use `.scratch/<effort>/map.md` as the effort record and entry point.
- For a decomposed effort, use `spec.md` and separate numbered tickets under
  `issues/<NN>-<slug>.md`. A small direct request needs only a short map entry.
- Record `Status`, `Claimed by`, and `Blocked by` near the top of each ticket.
- Read the map, specification when present, ticket, and relevant blockers before
  starting. An executable ticket identifies outcome, authorized scope, non-goals,
  acceptance criteria, verification, dependencies, and known external gates.
- Claim available work before dispatch. Append commands, results, candidate
  SHAs, findings, and dispositions under `## Comments`; preserve earlier history.
- Close satisfied work with its evidence and integrated candidate, clear the
  claim, and add a concise result pointer to the map. Update newly unblocked work.

Keep `Decisions so far` and `Authorizations and deferrals` sections in the map.
Follow `instructions/records.md` in the shared dotagents checkout for their
contents, authority boundaries, consolidation, and handoffs. That document owns
the shared recordkeeping rules; this file owns their project location.

## States and dependencies

Use `needs-triage`, `ready-for-agent`, `in-progress`, `in-review`, `blocked`,
`ready-for-human`, and `done`. Record any required platform gate explicitly in
the ticket rather than assuming code completion proves verification.

The ready frontier contains unclaimed `ready-for-agent` tickets with accepted,
completed dependencies. In a Light batch, one lane can begin an internal dependent
after recording its prerequisite's checked local checkpoint. External dependencies
must be accepted first; other lanes consume accepted checkpoints only. Preserve
each ticket's criteria/status and link shared batch evidence instead of copying it.

Human gates block dependent actions, not unrelated work. Delegated agent choices
are not automatically human gates. Keep explicit external authority and missing
evidence visible, even when provisional work is allowed.

## Skill translations

When a skill says publish, fetch, comment, claim, or resolve an issue, perform
the corresponding Markdown operation above. When it expects a tracked PR,
record the candidate, scope, review, and integration status in the map. Creating
a real hosted PR requires the project's workflow or explicit owner direction.

For wayfinding, the map and numbered children form the same graph. "Resolved"
maps to `done`; "claimed" means a nonempty `Claimed by` with `in-progress`.
Use dependencies and priority to choose work, not ticket number alone.

Keep findings in the current work only when they fit its scope and acceptance.
Record unrelated findings as separate follow-ups, starting uncertain ones at
`needs-triage`. A finding does not authorize an unrelated refactor.
