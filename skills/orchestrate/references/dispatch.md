# Dispatch and resource ownership

Every lane needs a readable brief identifying:

- objective, issue/specification or direct-request acceptance;
- immutable accepted base, candidate when reviewing, branch, and worktree;
- authorized paths, hard boundaries, satisfied dependencies, and required gates;
- effective decision policy and applicable decisions, authorizations, and deferrals;
- mutable resource ownership and commit, merge, push, and release ownership;
- completion report and accessible source/evidence pointers.

Resolve missing ownership before work that depends on it. A lane brief carries
existing authority; it cannot broaden it. Pass relevant entries when a pointer
is unavailable in the receiving checkout or host. Keep the originating source
and any limits visible through further handoffs.

Unless the owner or lane brief selects another mode, launch local Claude Code
lanes with `--permission-mode auto` and local Codex lanes with
`--approve-for-me` in the workspace-write sandbox. Record overrides in the lane
brief. An unrestricted or full-filesystem mode requires advance owner approval
for that lane after stating the blocked operation, why the default cannot
complete it, the added scope and risk, and the safer alternatives considered.
Such approval does not expand repository scope or grant secrets, account,
deployment, signing, release, or destructive Git authority.

When transferring an effort to another host or colleague, follow
[shared handoff ownership](../../../instructions/records.md#handoffs-and-evidence).
A continuing worker lane retains its assigned scope; a full effort handoff
transfers completion ownership. Record who now owns acceptance/integration so
completion does not depend on the departed orchestrator. Sender tool failures
or host limitations do not become restrictions on the receiver.

Concurrent lanes must not contend for source, generated paths, project files,
or mutable external resources. Give shared files one writer. Separate generated
build output by lane; serialize simulators, devices, signing, archives, or
deployments when the project says they share mutable state. Use the project's
scheduler when it has one; a small effort can use an explicit single owner.

Retain source worktrees through corrections and acceptance. Release obsolete
generated output under project rules, preserving compact evidence. Before
cleaning up a process or directory, verify ownership and inactivity, resolve the
exact target, and ensure it is within the assigned boundary. A stale-looking
process name or directory is not enough evidence. The shared workflow grants no
authority to terminate unrelated processes or remove another lane's state.

When a requested local CLI is not found, check the platform command lookup,
configured package-manager shims, and a bounded set of normal user installation
locations. Verify a candidate with its version command before using it. Do not
scan the entire disk. Distinguish missing executable from authentication, model
availability, permissions, quota, or execution failure, then use the authorized
fallback. Read host-specific local instructions when the project provides them.

On Windows, explicitly test `%APPDATA%\npm\<command>.cmd`,
`%USERPROFILE%\.local\bin`, provider-specific local-bin directories, and
`%USERPROFILE%\scoop\shims`; package inventory can miss a runnable shim. On
macOS, include `~/.local/bin`, provider-specific local-bin directories,
`/opt/homebrew/bin`, and `/usr/local/bin`. A sandbox denial against a plausible
path is an access result, not proof the provider is absent. Discovery is complete
when the executable is version-verified or the bounded locations and failures
are recorded.

## Local Claude dispatch on macOS

Run a macOS-assigned lane from a macOS shell. Before dispatch, verify `uname -s`,
`claude --version`, `claude auth status`, `git rev-parse HEAD`, and
`claude agents --json --all`. Continue when the host is Darwin, the launching
context can authenticate, and the checkout matches the immutable base or
candidate. Read `CLAUDE.local.md` when present before diagnosing authentication
or shell-context failures; restricted automation may not see credentials held
in the login Keychain, and background sessions need write access under
`~/.claude`.

The lane brief owns model, effort, usage threshold, permission mode, and fallback
policy. Pass the complete dispatch contract and use full model IDs when version
matters. Capture the ID from `claude --bg`, monitor with
`claude agents --json --all`, and inspect with `claude logs <session-id>`.
Return blocked, failed, or stopped sessions to the orchestrator for adjudication.
Use `claude attach <session-id>` only for an interactive view; `--bg` and
`--print` are incompatible.
