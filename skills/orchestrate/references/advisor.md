# Advisor staffing

Use only when the owner selects `with advisor` or otherwise requests an advisor.
Keep Light/Thorough, decision policy, and review shape unchanged.

Resolve lead, coding, and advisor models using [model selection](models.md).
Prefer an economical capable lead and coders, with a stronger advisor only where
current evidence supports that role and the owner's cost constraints allow it.
Explicit pairings win. No provider or model is permanently the strongest.
Record actual model identities and effort settings, including a current root
that differs from a requested pairing. Do not claim to switch a running model.

Start one advisor lazily when any of these occurs:

- material architecture, security, or requirements uncertainty remains;
- two meaningful hypotheses for the same failure were tested and rejected;
- review exposes a tradeoff the lead cannot resolve from accepted intent and evidence.

Reuse that advisor through related questions and corrections. Routine builds,
navigation, and status updates do not trigger it. Replace it only when unavailable
or its context is unrelated or unusable, with a compact handoff.

Send the decision, relevant evidence and failed hypotheses, constraints, the
lead's proposed answer and main risk, and one bounded question whose answer
changes the next action. Record the brief question, adjudicated decision, and
outcome in the effort tracker; keep full transcripts in the agent session.

Advice does not replace implementation ownership, independent review, tests,
acceptance, or external-action authority. If the requested advisor is unavailable,
follow an authorized fallback. Otherwise report the limitation and continue work
that does not require it; ask only when a necessary choice remains unresolved.
Do not invent model identifiers, spending caps, or free/cached usage.
