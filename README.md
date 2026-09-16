# dotagents

Versioned copy of `~/.agents` — my agent-agnostic home directory for AI coding
agent skills (Claude Code, OpenAI Codex, and compatible tools).

## Layout

- `skills/` — the installed skills, one folder per skill with a `SKILL.md`.
  Codex reads this directory natively (`$HOME/.agents/skills`). Claude Code
  reads `~/.claude/skills/`, which is wired to this directory (see below).
- `.skill-lock.json` — install manifest kept by the [skills CLI](https://skills.sh):
  upstream repo, path, content hash, and timestamps for each installed skill.
- `external/` — gitignored cache of upstream skill-source repo clones; the
  skills CLI recreates it on demand.

## Setting up a new machine

1. Clone this repo to the home directory:

   ```bash
   git clone https://github.com/joel-zutobi/dotagents.git ~/.agents
   ```

2. Codex now sees every skill automatically — nothing more to do.

3. For Claude Code, wire `~/.claude/skills/` to `~/.agents/skills/`:
   - Preferred (needs symlink rights; on Windows enable Developer Mode):
     create one symlink per skill folder, e.g. from `~/.claude/skills`:
     `ln -s ../../.agents/skills/<name> <name>` — or simply reinstall via the
     skills CLI, which creates the links itself.
   - Fallback without symlink rights: copy the folders instead
     (`cp -r ~/.agents/skills/* ~/.claude/skills/`) and re-copy after pulling
     updates.

## Updating skills

Use the skills CLI (`npx skills ...`) so `.skill-lock.json` stays accurate,
then commit and push the changes; pull on other machines.

## Shared workflow for new projects

This checkout also owns reusable working instructions and orchestration:

- [Shared base](instructions/base.md): decision policy, scoped authorizations,
  explanatory progress, proportional implementation, and review adjudication.
- [Orchestrate](skills/orchestrate/SKILL.md): Light and Thorough, persistent lanes,
  review selection, verification reuse, UI iteration, and optional advisors.
- [Set up a project](skills/setup-project/SKILL.md): create a small project adapter
  from [the templates](templates/project/AGENTS.md), using the project's real
  tracker, commands, resources, release gates, and owner decisions.

Keep the complete dotagents checkout available. These locally maintained skills
use `instructions/` and `templates/` from the same checkout; installing only their
skill folders is insufficient. The skills CLI remains the updater for imported
skills. Update this first-party workflow through dotagents itself, preserving
upstream skill files and their installation manifest.

In a new project, ask the agent to **use setup-project to adopt dotagents**.
The skill creates or updates `AGENTS.md`, `docs/agents/project.md`, and the tracker
adapter when needed. It can add a `CLAUDE.md` import when Claude Code support is
wanted. It infers facts from the project and asks only for consequential missing
choices. For an existing project, explicitly request adoption before replacing
its workflow.

The generated pointers locate the shared checkout through `DOTAGENTS_ROOT`, the
installed shared skill's location, or `~/.agents`. `DOTAGENTS_ROOT` is a convention
read by these instructions; it does not register skills in an agent application.
Use the host installation described above for discovery. Keep one shared skill
installation rather than copying it into every project. Shared instructions are
read from that checkout, so updating it affects opted-in projects on their next
read; project differences remain in the project's own files.

Start work with `Orchestrate Light` or `Orchestrate Thorough`. Add `with advisor`
or `with human decisions` when wanted. Agent-led decisions are the default.
The [model policy](skills/orchestrate/references/models.md) refreshes relevant
official evidence on demand after 14 days, or sooner for unfamiliar model names.
It preserves explicit choices and uses a per-user cache outside Git. This setup
does not install a scheduled task or switch running agents.

Imported skills, including Matt Pocock's `implement-spec`, stay unchanged.
Projects that adopt this workflow explicitly assign batching, lane reuse,
review shape, and Git ownership to orchestration when those skills are used.
Existing project-owned workflows, including Car Widget's internal setup, remain
authoritative until that project's owner chooses to migrate.

## Handoffs between computers or colleagues

Ask: "Use handoff-git to prepare a handoff for another computer" or "Prepare a
Git handoff for my colleague." The [handoff-git skill](skills/handoff-git/SKILL.md)
writes a detailed tracked handoff, publishes the required work within the granted
Git authority, verifies the remote checkpoint, and returns a short starter prompt.
The receiving agent reads that file and continues from the pinned commit.

The default location is `docs/agents/handoffs/<effort>.md`; a project that uses
Git-tracked `.scratch/` can keep it there instead. Ignored scratch and OS temporary
files are not delivery mechanisms. Required shared instructions, including
unpublished dotagents changes, must also be reachable by the receiver. Credentials
stay outside Git, with their approved setup sources named in the handoff.

This is separate from Matt Pocock's unchanged `handoff` and `claude-handoff`
skills, which create a local temporary document or start a local background agent.
Creating this skill does not publish any existing project work. When requesting an
actual handoff, established scoped publication authority carries forward; a
remaining destination or permission question is resolved before the relevant push.
