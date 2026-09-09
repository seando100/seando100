# Sean Doherty

I build AI systems hands-on, after twenty years leading product and design.

I have been working on AI adoption across two generations of the technology. I built
conversational assistants on Artificial Solutions Teneo, Google Dialogflow and Alexa when the
models were intent classifiers, the output was mediocre and nobody in the business was asking
for it. Today I design and ship multi-agent systems on frontier models through my own
consultancy, SPD Digital Consulting. The technology has been replaced underneath me twice. The
problem has not changed: find where automation genuinely helps, build it, and get people to
use it.

## What I have shipped

**SoloBusinessAI**, a production multi-agent platform for small businesses across eight
verticals. Coordinated agents handle customer intake across chat, phone and web, launch sites,
create marketing and complete recurring work, with bilingual journeys and human escalation.
Live, taking payments, with real customers.

**Cura Mirai**, a model-agnostic governance layer that sits around any LLM and refuses to trust
the model's own guardrails. Deterministic policy evaluation, a one-way escalation ratchet with
irreversibility floors, and fail-closed behaviour on any model failure. The first application is
child safety.

**FloraLoop**, a two-sided marketplace for surplus and rescued flowers. Escrow with pickup
confirmation, ZIP-and-radius search, live in two cities.

Most of this is commercial and private. What is public here is a subset. I am glad to walk
through any of it in detail.

## How I work

**I do not write production code.** I design agent behaviour, write and revise the instruction
files that govern it, connect the tools and data each agent needs, and own the evaluations that
decide whether a change shipped or regressed. That is a deliberate position, not a limitation.

**Evals are the part most people skip.** A worked example from my own product, because it is
the most useful thing I can tell you about how I think: a safety test harness reported 100
percent detection and zero false positives, and both numbers were true and irrelevant. It
measured whether a signal was *detected*, never whether it was *surfaced* to the person who
needed it. Driving the real chain end to end found eighteen categories being silently dropped
between the two, including a child disclosing abuse. The fix was an invariant, that policy may
decide the priority and the wording of an alert but may never decide whether a detected signal
is recorded at all, pinned by a coverage test proven to fail when it should. A green scorecard
is not evidence. Knowing what your suite does not measure is the job.

**Context engineering is scoping, not prompt tricks.** What the model can see, what it must
never see, what stays deterministic and what is safe to delegate to judgement. In the system
above, the governance state is deliberately hidden from the model and the model is only ever
asked bounded questions, because a component that can be argued with is not a safety control.

## Contact

[seanpauldoherty.com](https://seanpauldoherty.com) · [LinkedIn](https://linkedin.com/in/seanpauldoherty) · seanpauldoherty@gmail.com
