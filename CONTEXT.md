# Teho

Evidence-led work redesign. Teho observes how a team actually works for a fixed engagement period, then produces a costed map and a ranked portfolio of changes for the sponsor to decide on.

## Language

### Engagement

**Engagement**:
A fixed-scope, fixed-fee piece of work with one sponsor, one team, and one business question. Six working weeks: Week 1 scope, Weeks 2–5 observe, Week 6 readout.

**Sponsor**:
The business leader who buys the engagement and receives the readout. The decision-maker, not the observed worker.
_Avoid_: Client, buyer, customer

**Observed team**:
The team whose work is being evidenced during the engagement.

**Observed employee**:
An individual on the observed team whose work contributes evidence. Distinct from the **Sponsor**.
_Avoid_: User (ambiguous — the **Sponsor** is also a user of Teho's output)

### Evidence

**Evidence channel**:
A source of signal about how an **Observed employee** actually spends time (e.g. calendar, browser activity, comms metadata, interviews). Each channel is bounded in scope and time.

**Observation phase**:
Weeks 2–5 of the **Engagement** — the only window in which **Evidence channels** are active.

**Readout**:
The Week 6 deliverable for the **Sponsor**: the **Work Profile Map**, ranked portfolio, and three priced moves on page one.

### Output

**Work Profile Map**:
A breakdown of where the **Observed team**'s time and cost concentrate, grouped into bands: Judgement, Execution, Coordination, Overhead, Burden.

**Recoverable capacity**:
The share of the **Observed team**'s time that the **Work Profile Map** identifies as addressable through redesign, automation, or AI.

**Low-value load**:
The share of the **Observed team**'s time spent in Coordination, Overhead, and Burden bands.

**Priority value**:
The £ value of the top-ranked moves named on page one of the **Readout**.

**Pulse**:
A quarterly post-engagement check-in. Out of scope for v1 of browser awareness.

## Relationships

- An **Engagement** has one **Sponsor**, one **Observed team**, and many **Observed employees**
- An **Engagement** contains one **Observation phase** which activates one or more **Evidence channels**
- Browser awareness is one **Evidence channel** among several; it does not run outside the **Observation phase**
- The **Readout** synthesises all **Evidence channels** into one **Work Profile Map**

## Example dialogue

> **PM:** "Should the browser observer keep running after the **Engagement** ends so we have fresh data for **Pulse**?"
> **Domain expert:** "No — **Evidence channels** are bounded to the **Observation phase**. Pulse uses a different, lighter mechanism. Anything else would change the consent conversation we had with the **Observed employee** in Week 1."

## Flagged ambiguities

- "User" was used to mean both the **Sponsor** and the **Observed employee** in the initial brief — resolved: these are distinct concepts and almost every UX decision differs between them.
- "Browser awareness" (technical) vs "page context" (internal) vs user-facing copy (TBD, but not "monitoring" or "tracking") — three audiences, three vocabularies. Resolved by keeping **Evidence channel** as the canonical internal term.
