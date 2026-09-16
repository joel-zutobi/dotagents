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
