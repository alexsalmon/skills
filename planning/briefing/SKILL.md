---
name: briefing
description: Produces a compact briefing document for an AFK agent taking on a specific slice. Use after create-prd or create-issues, immediately before handing work to a coding agent. Do NOT interview the user — synthesise from the current context.
---

Do NOT interview the user. Synthesise a tight briefing document from the current conversation context — the PRD, acceptance criteria, slice definition, CONTEXT.md, and any ADRs.

The goal is to give an AFK agent exactly what it needs to execute the slice correctly, and nothing more. Brevity is correctness — a bloated briefing causes drift.

## Process

1. Identify the specific slice being handed off. If ambiguous, ask the user which slice before proceeding.

2. Read `CONTEXT.md` if it exists. Read any ADRs relevant to the slice's area.

3. Produce the briefing using the template below.

<briefing-template>

## Task

One paragraph. What the agent must build — described as end-to-end behaviour, not layer-by-layer implementation. Reference the slice name and parent PRD issue if available.

## What done looks like

The acceptance criteria for this slice, verbatim from the `/acceptance` session if one was run. If not, derive the done conditions from the PRD.

- [ ] Criterion 1
- [ ] Criterion 2
- [ ] Criterion 3

## What to know

Key context the agent needs that is not obvious from the code:

- Relevant terms from `CONTEXT.md` (name and one-line definition only)
- ADRs that apply to this area (decision and reason, one line each)
- Any constraints, compliance requirements, or non-obvious dependencies

Keep this section short. If something is visible in the code, omit it.

## What not to touch

Explicit list of files, modules, or behaviours the agent must leave unchanged. Be specific.

- [module or file]: [why it must not change]

If nothing is off-limits, write "None — but stay within the scope of this slice."

## How to verify

The steps a human would follow to confirm the slice is working before raising a PR. Should be runnable in under 5 minutes.

1. [step]
2. [step]

</briefing-template>
