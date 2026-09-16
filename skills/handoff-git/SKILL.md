---
name: handoff-git
description: Prepare or resume a Git-published handoff for another computer, colleague, or fresh agent, with a detailed tracked document and a short starter prompt. Use when the receiver must continue without the current conversation or local files.
---

# Git handoff

Deliver a resumable work checkpoint and a short prompt. This skill owns transport
and resumption, not the project's implementation workflow. Read the project's
agent instructions and tracker, then [shared recordkeeping](../../instructions/records.md).
Preserve existing project decisions and authority. Keep imported `handoff` and
`claude-handoff` unchanged; their temporary-file or local-agent output does not
by itself reach another computer.

## Prepare the checkpoint

Inspect the actual branch, remotes, staged and unstaged changes, worktrees, active
lanes, and effort record. Identify the intended recipient's outcome and its
required code, instructions, evidence, and repositories. Select the handoff type
under shared recordkeeping: full ownership transfer by default, or a narrower
role justified by the user's intent or an existing responsibility. Infer this
from the request and current work; ask only for consequential missing information.

A request for a ready-to-resume handoff pushed to Git authorizes the necessary
task-scoped commits and normal pushes to the established authorized destination,
unless the owner limits that authority. Reuse existing grants without asking
again. Draft-only requests and requests to create or explain this skill do not
authorize publishing project work. A handoff request alone does not authorize
merging, releasing, changing access, force-pushing, or messaging a colleague;
separately granted authority for those actions remains effective within its scope.
If the destination or scope is ambiguous, prepare the document first and ask
only for the unresolved choice before publication.

Use the project's tracked handoff location when one exists. Otherwise prefer
`docs/agents/handoffs/<effort>.md`. A Git-tracked `.scratch/<effort>/handoff.md`
is suitable when the project uses tracked scratch records. Check ignore rules;
if scratch is ignored, use the tracked docs location instead. Keep one current
handoff per effort and let Git retain history. This is a transfer snapshot that
links the existing tracker, not a replacement issue/specification system.

Write the detailed document using [the handoff outline](handoff-template.md).
Include enough context to start without chat history. Link existing artifacts
instead of copying them, but include decision/authority excerpts when the receiver
cannot access their original record. Mark their source and any unresolved access.
Use repository-relative paths and portable setup commands. Name the outcome,
completion criteria, and first useful action, not merely a list of files to read.
Apply the shared recordkeeping rules for receiver ownership and restriction
provenance. Transfer the work to completion unless the owner requested a narrower
role. Describe sender-host limitations as observations and name which remaining
work the receiving host is expected to perform. Do not turn the sender's preferred
tools, command sequence, or lack of access into mandatory receiver restrictions.

## Make dependencies reachable

Include task-relevant source changes and safe required artifacts in the checkpoint.
Inspect staged changes and commit only owned paths or hunks; leave unrelated work
and another lane's changes intact. Never use a blanket add/commit, discard work,
or publish unrelated commits already on a branch to satisfy the handoff. If needed,
prepare an isolated handoff branch from the accepted base without rewriting the
owner's branch. Review the outgoing commits as well as the final diff.

Immediately before committing, inspect `git diff --cached --name-only` and the
staged diff. Adding owned files does not remove someone else's staged files.
When unrelated files are staged and the selected files are wholly owned, use
`git commit --only -- <owned-paths>` to commit those paths while preserving the
other staged entries. When ownership is mixed within a file, use an isolated
index or checkout for the selected hunks. Inspect the resulting commit's paths
and diff before pushing; do not rely on the preceding `git add` as proof of scope.

For every required repository, record its credential-free clone URL, fetchable
branch/ref, and exact source commit. Include the complete dotagents checkout when
its shared instructions or skills are required. Required local changes there
must be published within authority too, or explicitly reported as a blocker.
Do not replace a published version with a pointer to the sender's home directory.
The receiver can fetch a separate checkout if updating an existing one would
disturb other work. A path or environment variable alone does not install skills.

Regenerate dependencies, caches, and build output from documented commands where
possible. Never commit credentials, private customer data, or machine-local
configuration. For necessary artifacts unsuitable for Git, name an already
authorized shared location or an exact reproduction procedure. List required
accounts and approved configuration sources without secret values. Distinguish
an expected receiver login/setup step from missing source or inaccessible evidence.

Carry existing verification with its original source SHA and limits. Run checks
needed for the changed checkpoint; documentation-only transport does not require
repeating valid builds. A WIP handoff can be ready with known failures when the
next task is to address them. Delivery readiness is not implementation acceptance.
Record active lane/resource ownership and which work transfers; prevent both
sender and receiver from unknowingly continuing the same lane.

## Publish and return the short prompt

Commit and push the required work and handoff within the granted scope. Record
the source candidate SHA in the document. Put the final handoff commit SHA in the
starter prompt after committing; do not repeatedly amend a file to embed its own
commit hash. A separate source commit followed by a handoff-only commit is fine.

Verify the selected remote branch advertises the published commit, or a confirmed
descendant containing it, using `git ls-remote` plus the fetched ancestry when
needed. Check that the handoff and each required tracked file exist at that
published commit, not only in the working tree. Repeat for required repositories.
If the remote moved, inspect before retrying; never force-push over another person.
Successful local commits or a local tracking ref alone are not delivery proof.

When delivery is complete, return a copyable prompt of roughly 3-5 lines, normally
under 100 words. Include the primary repository URL, remote branch, full published
handoff SHA, document path, and instruction to read and continue. Put secondary
repositories and detailed setup in the document. For example:

```text
Continue the handoff in <repository URL>, branch <branch>, commit <full SHA>.
Fetch that commit into a safe checkout; preserve any existing local work.
Read AGENTS.md and <handoff path> at that commit, then take over and complete the recorded assignment.
```

Replace the example fields with verified values. If publication or required
dependency access is blocked, report the exact missing piece and label the handoff
not ready. Any starter text must be labelled draft, not presented as usable from
another computer. Do not send it to a colleague unless explicitly asked.

## Resume on the receiving computer

Read the starter coordinates, inspect existing local work, and fetch the pinned
commit from the named repository/ref. Use a safe separate checkout when needed;
do not reset or overwrite a colleague's changes. Read project instructions and
the handoff from that checkpoint before implementation. If a newer handoff exists,
inspect its supersession/ownership notes before choosing a different checkpoint.

Resolve the recorded repositories and shared skills at the stated versions,
prepare the current host using the documented setup, and read the effort record.
Carry effective decisions, permissions, deferrals, and known failures forward.
Grants tied to a person, account, host, or environment apply only within those
limits; a handoff does not transfer credentials or broaden permission. Preserve
explicit model choices and report unavailable tools instead of pretending that
the sender's runtime or live subagents moved with the Git files.

Read the recorded ownership transfer and inspect for conflicting active work;
this is not a request to obtain approval from the sender. Use this host's actual
capabilities to complete the transferred assignment, including fixing failures
and running verification. Follow the shared recordkeeping rules if old handoff
wording confuses source-host limitations with binding restrictions. Report to the
user or assigned recipient without requiring the original agent to return.
Record changed authority, invalid evidence, or missing dependencies and continue
independent work while resolving a real blocker.
