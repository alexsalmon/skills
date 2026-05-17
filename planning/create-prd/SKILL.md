---
name: create-prd
description: Turn the current conversation context into a PRD and publish it to the project issue tracker. Use when user wants to create a PRD from the current context.
---

This skill takes the current conversation context and codebase understanding and produces a PRD. Do NOT interview the user — just synthesize what you already know.

Before writing the PRD, check for a `.skills-config.md` file at the project root. If it exists, read the tracker URL and label vocabulary from it. If it does not exist, ask the user for:
- Issue tracker URL or type (e.g. GitHub Issues, Linear, Jira)
- The label to apply to ready issues (e.g. `ready-for-agent`, `ready`, `triage`)

If you asked the user inline, offer to save their answers to `.skills-config.md` at the repo root so subsequent skills (e.g. `/create-issues`) can read it directly.

## Process

1. Explore the repo to understand the current state of the codebase, **only if you haven't already done so this session**. Use the project's domain glossary vocabulary throughout the PRD, and respect any ADRs in the area you're touching.

2. Sketch out the major modules you will need to build or modify to complete the implementation. Actively look for opportunities to extract deep modules that can be tested in isolation.

A deep module (as opposed to a shallow module) is one which encapsulates a lot of functionality in a simple, testable interface which rarely changes.

Check with the user that these modules match their expectations. Check with the user which modules they want tests written for.

3. Write the PRD using the template below, then publish it to the project issue tracker. Apply the configured ready label from `.skills-config.md` — no need for additional triage.

<prd-template>

## Problem Statement

The problem that the user is facing, from the user's perspective.

## Solution

The solution to the problem, from the user's perspective.

## User Stories

A LONG, numbered list of user stories. Each user story should be in the format of:

1. As an <actor>, I want a <feature>, so that <benefit>

<user-story-example>
1. As a mobile bank customer, I want to see balance on my accounts, so that I can make better informed decisions about my spending
</user-story-example>

This list of user stories should be extremely extensive and cover all aspects of the feature.

If an `acceptance` session was run prior to this PRD, include the Given/When/Then acceptance criteria inline beneath each relevant user story.

Order user stories so the thinnest end-to-end slice comes first — the story that delivers the earliest demoable value and validates the core assumption before the rest is built.

## Implementation Decisions

A list of implementation decisions that were made. This can include:

- The modules that will be built/modified
- The interfaces of those modules that will be modified
- Technical clarifications from the developer
- Architectural decisions
- Schema changes
- API contracts
- Specific interactions

Do NOT include specific file paths or code snippets. They may end up being outdated very quickly.

Exception: if a prototype produced a snippet that encodes a decision more precisely than prose can (state machine, reducer, schema, type shape), inline it within the relevant decision and note briefly that it came from a prototype. Trim to the decision-rich parts — not a working demo, just the important bits.

## Testing Decisions

A list of testing decisions that were made. Include:

- A description of what makes a good test (only test external behavior, not implementation details)
- Which modules will be tested
- Prior art for the tests (i.e. similar types of tests in the codebase)

## Proposed Slice Order

A numbered list of vertical slices in delivery order. Each slice should be a thin end-to-end path that is demoable on its own. The first slice must validate the core assumption before the rest is built.

For each slice:
- **Slice N: [name]** — one sentence describing the end-to-end behaviour delivered
- **Depends on:** slice numbers that must ship first (or "none")
- **Validates:** what assumption or risk this slice de-risks

This section is the direct input to `/create-issues` — keep it precise.

## Out of Scope

A description of the things that are out of scope for this PRD.

## Further Notes

Any further notes about the feature.

</prd-template>
