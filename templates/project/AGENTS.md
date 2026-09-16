# Agent instructions

This project uses the dotagents shared workflow. Before acting, resolve the
dotagents checkout from `DOTAGENTS_ROOT` when set, otherwise from the installed
shared `orchestrate` skill's enclosing checkout, otherwise `~/.agents`. Expand
the home directory for the current host. Verify and read `instructions/base.md`
there; these path conventions do not register skills or load documents by themselves.
If unavailable, report the missing shared instructions and continue only work
that the project's existing instructions and task independently define.

Read [project settings](docs/agents/project.md) and the
[tracker protocol](docs/agents/issue-tracker.md). Explicit task instructions
override project defaults; project differences override the shared base.

For orchestration, multi-agent dispatch, or implementation of a specification,
read `skills/orchestrate/SKILL.md` in the same shared checkout. It owns mode,
batching, lane reuse, review shape, finding disposition, evidence reuse, and Git
ownership for this project. When using imported engineering skills such as
`implement-spec`, retain their substantive techniques while using this adopted
process instead of conflicting per-ticket or unconditional review/Git boilerplate.
An explicit owner request to use an imported workflow unchanged takes precedence.

Keep only project-specific rules here or in the linked project documents.
