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

**SoloBusinessAI** is a production multi-agent platform for small businesses. It began as eight
named verticals and now serves **any small business, whether already trading or starting from
nothing**. Every owner gets a team of six named agents to work alongside: a chief of staff, a
support rep, a technical investigator, an ad creative director, a social media manager and a
content writer. Customer intake runs across chat, phone and web, with bilingual journeys and
human escalation. Live, taking payments, with real customers.

Behind the product sits a second layer: **twenty-four agents that build, support and market the
platform itself**, across four families. One of them is a six-agent pipeline that stands up an
entire new vertical from a single brief, and will not call it live until the QA agent's smoke
test passes against the real deployment.

**DXP Auditor** is a multi-agent system that crawls a website and scores its digital experience
across **eighteen dimensions**: accessibility, performance, security, SEO, content quality,
journey coverage, taxonomy, personalisation and more. Each agent owns one dimension and returns
findings in a common shape, so adding a nineteenth is one file. Used commercially to audit
national insurance carriers, and inside SoloBusinessAI to read a new customer's existing site
during onboarding.

**Cura Mirai** is a model-agnostic governance layer that sits around any LLM and refuses to
trust the model's own guardrails. Deterministic policy evaluation, a one-way escalation ratchet
with irreversibility floors, and fail-closed behaviour on any model failure. The first
application is child safety.

**FloraLoop** is a two-sided marketplace for surplus and rescued flowers. Escrow with pickup
confirmation, ZIP-and-radius search, live in two cities.

Most of this is commercial and private. What is public here is a subset, and I am glad to walk
through any of it in detail.

## How I work

**I do not write production code.** I design agent behaviour, write and revise the instruction
files that govern it, connect the tools and data each agent needs, and own the evaluations that
decide whether a change shipped or regressed. That is a deliberate position, not a limitation.

### Evals are the part most people skip

Three times now, in independent systems, I have found tests that reported success while checking
nothing. It is the most useful thing I can tell you about how I think.

**An accessibility suite that logged instead of asserting.** It ran on every push, printed axe
violations to the console, and passed. Sixteen of seventeen pages were failing WCAG AA on colour
contrast the entire time and CI was green. It surfaced only when someone went to write "WCAG AA
compliant" in public and the claim got checked. The comment now sitting above the assertion
reads: *logging is not testing.*

**A safety harness reporting 100 percent detection and zero false positives**, both true and
both irrelevant. It measured whether a signal was *detected*, never whether it was *surfaced* to
the person who needed it. Driving the real chain end to end found eighteen categories being
silently dropped between the two, including a child disclosing abuse. The fix was an invariant:
policy may decide an alert's priority and wording, but may never decide whether a detected
signal is recorded at all. It is pinned by a coverage test proven to fail when it should.

A green scorecard is not evidence. Knowing what your suite does not measure is the job.

### Context engineering is scoping, not prompt tricks

What the model can see, what it must never see, what stays deterministic and what is safe to
delegate to judgement. In the governance layer above, the escalation state is deliberately
hidden from the model and the model is only ever asked bounded questions, because a component
that can be argued with is not a safety control.

### Ontology work belongs in data, not in code

Both the audit system and the governance layer keep their rules in **versioned, source-cited
policy packs** rather than in the agents. Packs extend one another, so a platform or a
jurisdiction adds to a base layer rather than restating it, and every regulatory claim cites the
bulletin or statute it came from. Pointing the same engine at a different jurisdiction becomes a
matter of swapping a file.

### Sometimes the finding is that nobody can see you

A set of marketing sites were React single-page apps with a client-side language toggle on one
URL. **AI answer engines execute no JavaScript**, so GPTBot, ClaudeBot and PerplexityBot were
all being served an empty `<div id="root">`. The sites were invisible to them. I rebuilt one as
statically rendered pages with separate crawlable URLs per language, and chose that particular
site as the pilot because its Spanish already had full key parity, which isolated the rendering
migration from any translation work. Prove the architecture on a clean case, then replicate.

## Contact

[seanpauldoherty.com](https://seanpauldoherty.com) · [LinkedIn](https://linkedin.com/in/seanpauldoherty) · seanpauldoherty@gmail.com
