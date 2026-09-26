# Issue tracker: GitHub Issues

Work is tracked in GitHub Issues on `<owner>/<repo>`. Use the `gh` CLI; it infers
the repository from `git remote -v` inside a clone. Ticket state lives on GitHub:
do not commit status, claims, review logs, or evidence records to Git. Keep
durable knowledge in the tree instead, such as specifications under `<docs path>`.

## Operations

- Create: `gh issue create --title "..." --body-file - --label <state>`.
- Read: `gh issue view <n> --comments`, plus labels, milestone, parent, and blockers.
- List: `gh issue list --state open --json number,title,labels,milestone,assignees`
  with `--label`, `--milestone`, or `--search` filters.
- Comment: `gh issue comment <n> --body-file -`.
- Close: `gh issue close <n> --reason completed --comment "..."`, or
  `--reason "not planned"` for dropped, superseded, or merged work (name it).

Issues and pull requests share one number space; resolve a bare `#42` with
`gh pr view 42`, falling back to `gh issue view 42`.

## Records

A decomposed effort has one parent issue labelled `wayfinder:map` with its
tickets as GitHub sub-issues. Its body holds the outcome, specification link,
`Decisions so far`, and `Authorizations and deferrals`. Edit the body to keep them
current and preserve superseded entries in a comment. A small direct request
needs a single issue. Follow `instructions/records.md` in the shared dotagents
checkout for their contents, authority boundaries, consolidation, and handoffs.
That document owns the shared recordkeeping rules; this file owns their location.

Read the map, specification, issue, and relevant blockers before starting. An
executable issue identifies outcome, authorized scope, non-goals, acceptance
criteria as a task list, verification, dependencies, and known external gates.

## States and dependencies

Use one state label per open issue: `needs-triage`, `needs-info`,
`ready-for-agent`, `ready-for-human`, `blocked`, or `wontfix`. Add
`<project-specific gate labels>` when the project has them. GitHub represents
the rest: an assignee means claimed, an open pull request naming the issue means
in review, and closing as completed means done. Use milestones for timing:
`<release milestone>` for release blockers and `Later` for deliberate deferrals.

Record blocking with native issue dependencies: `gh api --method POST
repos/<owner>/<repo>/issues/<blocked>/dependencies/blocked_by -F issue_id=<id>`,
where `<id>` is the blocker's database id from `gh api
repos/<owner>/<repo>/issues/<blocker> --jq .id`. The ready frontier contains open,
unassigned `ready-for-agent` issues with no open blockers. In a Light batch, one
lane can begin an internal dependent after recording its prerequisite's checked
local checkpoint in the map. External dependencies must close first. Preserve each
issue's criteria and state, and link shared batch evidence instead of copying it.

Human gates block dependent actions, not unrelated work. Delegated agent choices
are not automatically human gates. Keep explicit external authority and missing
evidence visible, even when provisional work is allowed.

## Skill translations

- Publish: create an issue, or a `wayfinder:map` parent with sub-issues.
- Fetch: `gh issue view <n> --comments` with its map, specification, and blockers.
- Claim: re-read the issue, then `gh issue edit <n> --add-assignee @me` and
  comment with the lane name, before dispatch.
- Comment or record evidence: comment on the issue or pull request with base and
  candidate SHAs, commands and results, findings, and dispositions. Never edit
  away earlier history.
- Resolve: close with the answer, evidence, and integrated commit, then add a
  result pointer to the map and update newly unblocked issues.
- Pull request: `gh pr create` against `<default branch>`, naming the issue.
- PRs as a triage surface: no.

Keep findings in the current issue only when they fit its scope and acceptance.
Open unrelated findings as separate issues, starting uncertain ones at
`needs-triage`. A finding does not authorize an unrelated refactor.
