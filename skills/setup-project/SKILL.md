---
name: setup-project
description: Set up a new project to use dotagents shared instructions and orchestration, creating small project-specific pointers and settings. Use when adopting dotagents in a new repo or explicitly migrating an existing project's agent workflow.
---

# Set up a project

Use this skill from the complete dotagents checkout, alongside `instructions/`
and `templates/`. The target is the user's project, not the dotagents repository.
Read [the shared base](../../instructions/base.md) and use its decision policy.
This setup does not grant Git publication, release, account, or spending authority.

## Inspect before writing

Read the target's agent files, worktree status, build manifests/scripts, tracker
and platform docs. Preserve unrelated edits. Determine its real source boundaries,
verification commands and required hosts, shared resources, release gates, and
current owner decisions. Infer inspectable facts rather than asking the owner
to recite them. Ask only for choices that remain consequential or are reserved
under the effective decision policy.

If an existing project has its own internal orchestration, leave it intact
unless adoption/migration of that project is explicitly requested. Do not
replace it merely because the shared skill is installed. An already-configured
project should have its pointers/settings updated in place, not duplicated.

## Connect the shared installation

Verify this installation contains `instructions/base.md` and
`skills/orchestrate/SKILL.md`. Use one installation for the shared workflow.
The template resolves it through `DOTAGENTS_ROOT`, the installed shared skill's
location, or the conventional `~/.agents` checkout. `DOTAGENTS_ROOT` is a path
convention for these instructions, not a built-in agent setting or an installer.
Do not write a machine-specific absolute path into portable project files.

The host must discover the skills from its supported user skill location or
an explicit installation link. A project pointer makes the shared documents
readable; it does not automatically register skills in the host's selector.
Report missing discovery separately. Do not rewrite global agent configuration,
move directories, install a second copy, or repair existing links without scope
to do so. The repository README describes the existing shared installation.

## Write the project's small adapter

Start from these templates and fill them from the inspected project:

- [AGENTS.md](../../templates/project/AGENTS.md): shared-base pointer, project
  settings/tracker pointers, and ownership of the adopted workflow.
- [project.md](../../templates/project/docs/agents/project.md): only real project
  differences, including decision policy and any model-research overrides.
- [issue-tracker.md](../../templates/project/docs/agents/issue-tracker.md): local
  Markdown starter when the project has no existing tracker convention.

Preserve an existing tracker. When none is configured and no owner preference
exists, use the Git-tracked Markdown starter; it needs no external account.
Record that choice. For an existing tracker, keep its operations and identify
where durable decisions, authorizations, and evidence belong. Do not require
`.scratch` for projects that use another durable tracker.

Replace template fields with facts, source pointers, explicit "not applicable",
or a clear unknown to resolve before the affected operation. Do not invent
commands, gates, grants, or owner deferrals. Check that a proposed local tracker
path is not ignored; if it is, choose an appropriate tracked path and update the
adapter instead of force-adding ignored material.

Merge the small adapter into an existing `AGENTS.md` without deleting unrelated
instructions. For a new project, create it. If Claude Code support is wanted,
add `@AGENTS.md` to a new `CLAUDE.md` or integrate the import into the existing
file while preserving its content and avoiding contradictory duplicated rules.
Do not copy the shared base or orchestration skill into the project.

## Verify and report

Resolve the shared base and every project pointer from the target working
directory. Check templates have been filled, tracker records can be durable,
and project gates remain intact. Exercise the routing on a simple implementation
request and a human-led orchestration request. Verify repeat setup would update
the existing adapter rather than add another copy.

Report the files changed, important inferred defaults, missing host discovery
or required project facts, and how to start: `Orchestrate Light`, `Orchestrate
Thorough`, optionally `with advisor` or `with human decisions`. Leave commits
and pushes to the Git ownership assigned by the task.
