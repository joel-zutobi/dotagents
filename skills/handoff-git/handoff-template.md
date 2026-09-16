# Handoff outline

Use this outline when writing a transfer document. Replace prompts with facts,
omit irrelevant sections, and keep the next action near the top. The shared
recordkeeping document owns decision and authorization fields.

```markdown
# <Effort> handoff

Updated: <date>
Delivery: <prepared for publication / draft with concrete blockers>
Work state: <WIP / implemented / accepted, with limitations>
Handoff type: <full ownership transfer by default; if narrower, role and reason>
Continuation owner: <receiver owns completion; any explicit narrower role,
transferred acceptance/integration ownership, and sender's retained scope>

## Start here
<Outcome to complete, first useful action, acceptance criteria, and actual stop
conditions. The first action is not the limit of a full handoff.>
<Required reading in order, using repo paths or accessible tracker links.>

## Checkpoints and setup
| Repository | Clone URL | Fetchable branch/ref | Source commit | Purpose |
| --- | --- | --- | --- | --- |
| <project or required dependency such as dotagents> | <no credentials> | <ref> | <full SHA> | <why needed> |

<Primary source SHA excludes a later handoff-only commit; the starter prompt pins
the final published handoff commit. State the meaning of each recorded SHA.>
<Required host/toolchain, setup commands, skills and their resolution/installation,
account access and safe configuration sources, reproducible artifacts.>
<Sender-only limitations and work the destination can now perform. Commands are
suggested tactics unless a real project requirement makes them mandatory.>

## Decisions and authority
<Effective decision policy. Relevant owner/agent choices and rationale.>
<Applicable authorizations and deferrals with source, scope, environment, limits,
duration/end condition. Explicitly reserved or unresolved choices.>
<For each binding restriction, cite its actual source and applicability to the
receiver. Keep sender observations separate; do not invent tool bans or a required
return to the originating agent. Name real review/human gates when they apply.>
<Tracker pointer; include necessary excerpts if the receiver cannot read it.>

## Current work and evidence
<Completed work and remaining scope; important implementation context.>
<Checks, exact source SHAs, results, known failures, review dispositions,
accessible evidence, and remaining gates. Distinguish reused evidence.>
<Active lanes/processes/resources, transferred versus retained ownership,
excluded unrelated local work, and anything the receiver must recreate.>

## Publication and limitations
<Required changes/artifacts included; missing dependencies or receiver access
requirements. Any superseded handoff. Delivery does not imply acceptance.>
```

The committed document is prepared for publication. Remote verification happens
after its commit exists; the sender's final response reports that result with
the exact handoff SHA. Do not add an endless chain of verification-only commits.
