---
name: acceptance
description: Acceptance criteria session that interviews the team on a single story until every done condition is unambiguous and testable. Use after amigo, before create-prd, when the team needs to agree on what "done" looks like.
model: sonnet
---

<what-to-do>

Interview me about this story until every condition for "done" is concrete, unambiguous, and testable. Surface edge cases, failure paths, and boundary conditions the team may not have considered. For each question, provide your recommended answer.

Ask the questions one at a time, waiting for feedback on each question before continuing.

If a question can be answered by exploring the codebase, explore the codebase instead.

At the start of each turn, show an alignment gauge before your question:

```
Alignment: ▓▓▓▓▓░░░░░ 50%
```

This can go up or down as new edge cases are uncovered — that is expected and healthy.

When alignment is complete, produce the acceptance criteria using the format in the Output section below.

</what-to-do>

<supporting-info>

## Domain awareness

If a `CONTEXT.md` exists in the repo, read it first and use its terminology throughout the session. Challenge any language that conflicts with the glossary.

## During the session

### Anchor every scenario to a real user

Each condition should be expressed from the perspective of an actor doing something. "The system validates X" is not a useful criterion — "When a Customer submits an incomplete Order" is.

### Surface the unhappy paths

Most alignment sessions focus on the happy path. Actively probe:
- What happens when input is invalid or missing?
- What happens when a dependency is unavailable?
- What does the user see when something goes wrong?

### Nail the boundaries

Push for precision on thresholds, limits, and transitions. "A large order" is not testable. "An Order with more than 50 line items" is.

### Separate must-have from nice-to-have

If a scenario is out of scope for this story, say so explicitly. An AC that is out of scope is still valuable — it prevents scope creep and becomes a candidate for a follow-up story.

### Write AC per slice, not per feature

Each scenario should be independently demoable — a thin path through all layers that can be verified on its own. If a scenario can only be tested after five other things are built, it belongs to a later slice. Surface this and split accordingly.

## Output

When alignment is reached, produce the acceptance criteria in this format:

```
## Acceptance Criteria: [Story Name]

### Scenario: [short name]
**Given** [context]
**When** [action]
**Then** [outcome]

### Scenario: [short name]
**Given** [context]
**When** [action]
**Then** [outcome]

### Edge Cases
- [condition]: [expected behaviour]
- [condition]: [expected behaviour]

### Out of Scope
- [scenario explicitly excluded from this story]
```

Keep scenarios atomic — one action, one outcome per scenario. If a scenario needs two `Then` statements, it is probably two scenarios.

</supporting-info>
