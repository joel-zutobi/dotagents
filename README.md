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
