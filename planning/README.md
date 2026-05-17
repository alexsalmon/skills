# Planning skills

## Principles

**Vertical slices over horizontal layers.** Every slice delivers a thin but complete end-to-end path. The first slice validates the core assumption before the rest is built.

**Alignment before code.** The planning flow exists to surface assumptions, sharpen language, and reach shared understanding — before an agent writes a single line.

**Token efficiency.** The flow is designed to stay under 100k tokens. Codebase exploration happens once in `/amigo` and carries forward. `/create-issues` and `/briefing` can be run in a fresh context with just the PRD as input.

---

## Workflow

The skills form a pipeline. Run them in order, in a single conversation, up to and including `/create-prd`. After that, the PRD is the artifact — subsequent skills can be run in a fresh context.

```
/hypothesis → /amigo → /acceptance → /create-prd → /create-issues → /briefing → [agent]
```

### Session 1 — Align

Run these skills together in one conversation. Context accumulates and each step feeds the next.

| Step | Skill | Required | Depends on |
|---|---|---|---|
| 1 | [`/hypothesis`](./hypothesis/) | Optional | — |
| 2 | [`/amigo`](./amigo/) | **Yes** | Benefits from `/hypothesis` output |
| 3 | [`/acceptance`](./acceptance/) | Optional | Expects a story or plan from `/amigo` |
| 4 | [`/create-prd`](./create-prd/) | **Yes** | Synthesises from the full session |

`/hypothesis` can be skipped if the "why" is already clear and agreed. `/acceptance` can be skipped if done conditions are simple and surfaced clearly during `/amigo`.

### Session 2 — Ship

These skills work from the PRD alone and can be run in a fresh conversation to keep token usage low. Pass the PRD issue or its contents as input.

| Step | Skill | Required | Depends on |
|---|---|---|---|
| 5 | [`/create-issues`](./create-issues/) | **Yes** | PRD from step 4 |
| 6 | [`/briefing`](./briefing/) | Optional | A specific slice from `/create-issues` |

`/briefing` is run once per slice, immediately before handing off to a coding agent. Skip it if the slice is simple enough to hand off directly from the issue.

---

## Configuration

`/create-prd` and `/create-issues` read tracker settings from a `.skills-config.md` file at the repo root. If the file is missing, the skill will ask inline and offer to create it.

```md
# Skills Config

tracker: github
tracker_url: https://github.com/org/repo
ready_label: ready-for-agent
```

| Key | Description |
|---|---|
| `tracker` | `github`, `linear`, or `jira` |
| `tracker_url` | Base URL for the issue tracker |
| `ready_label` | Label applied to issues that are ready for an AFK agent |

---

## Skills

| Skill | What it does |
|---|---|
| [`/hypothesis`](./hypothesis/) | Frames a feature as a testable hypothesis before any planning begins. Interviews to sharpen the user, the signal, the riskiest assumption, and the smallest experiment. |
| [`/amigo`](./amigo/) | Three amigos alignment session. Challenges the plan against the domain model, sharpens terminology, and updates `CONTEXT.md` and ADRs inline. |
| [`/acceptance`](./acceptance/) | Locks down testable done conditions for a single story. Produces Given/When/Then acceptance criteria with explicit edge cases and out-of-scope list. |
| [`/create-prd`](./create-prd/) | Synthesises the conversation into a PRD and publishes it to the issue tracker. Includes a proposed slice order as direct input to `/create-issues`. |
| [`/create-issues`](./create-issues/) | Breaks the PRD into independently-grabbable vertical slice issues. Each slice cuts end-to-end through all layers and is demoable on its own. |
| [`/briefing`](./briefing/) | Produces a compact handoff document for an AFK agent taking on a specific slice — task, done conditions, what to know, what not to touch, how to verify. |
