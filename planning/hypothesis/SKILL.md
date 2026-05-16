---
name: hypothesis
description: Hypothesis framing session that interviews the team on a feature until the user, value, signal, and riskiest assumption are all concrete. Use before amigo, when the team needs to agree on why they are building something before deciding what to build.
---

<what-to-do>

Interview me about this feature until we can state a precise, testable hypothesis. Probe the user, the expected behaviour, the reason we believe it, the signal that will confirm or refute it, and the riskiest assumption underneath it all. For each question, provide your recommended answer.

Ask the questions one at a time, waiting for feedback on each question before continuing.

At the start of each turn, show an alignment gauge before your question:

```
Alignment: ▓▓▓▓▓░░░░░ 50%
```

This can go up or down as assumptions are uncovered — that is expected and healthy.

When alignment is complete, produce the hypothesis card using the format in the Output section below.

</what-to-do>

<supporting-info>

## During the session

### Start with the user, not the feature

The first question should always establish who specifically benefits and why. "Users" is not an answer. "First-time customers who abandon checkout before payment" is.

### Separate belief from fact

Challenge statements that sound like facts but are actually assumptions. "Users want X" is a belief. "Our support logs show 40 requests for X in the last month" is evidence. Name the difference explicitly.

### Find the riskiest assumption

Every hypothesis rests on a stack of assumptions. The riskiest is the one that, if wrong, makes the entire feature pointless. Surface it early — it determines what the smallest experiment should be.

### Define the signal precisely

"We'll know it worked" is not a signal. Push for a specific, observable, measurable outcome with a timeframe. "A 10% reduction in checkout abandonment within 30 days of release" is a signal.

### Identify the smallest experiment

The first vertical slice should directly test the riskiest assumption with the least possible build. If the experiment can be done without code, say so.

## Output

When alignment is reached, produce the hypothesis card in this format:

```
## Hypothesis: [Feature Name]

**We believe** [specific user or segment]
**will** [take this action or experience this value]
**because** [insight or reason we believe this]

**We'll know we're right when** [specific, measurable signal with timeframe]

**Riskiest assumption:** [the one thing that, if wrong, invalidates the hypothesis]

**Smallest experiment:** [the thinnest slice or test that directly challenges the riskiest assumption]
```

</supporting-info>
