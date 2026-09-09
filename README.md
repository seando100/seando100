# Sean Doherty

Twenty years at the intersection of human understanding and technology, designing digital
experiences across entertainment, gaming, travel, retail, financial services, insurance,
healthcare, public services and automotive. The last eight on conversational, voice and
intelligent systems. The last two building them hands-on.

I believe the best technology disappears into the experience, that AI should amplify empathy
rather than replace it, and that innovation is measured by outcomes rather than novelty.

I have been doing the same job across two generations of this technology. The first time round it
was assistants on Artificial Solutions Teneo, Google Dialogflow and Alexa, when the models were
intent classifiers, the output was mediocre and nobody in the business was asking. Roadside
assistance, job search, rail and airline travel, hotels, wealth management, broadcast. The models
have been replaced underneath me twice since. The problem has not changed: find where automation
genuinely helps, build it, and get people to use it.

## What is running

**SoloBusinessAI** gives a small business owner a team of six named agents: a chief of staff, a
support rep, a technical investigator, an ad creative director, a social media manager and a
content writer. Intake runs across phone, chat and web, bilingually, with human escalation. It
started as eight professional verticals and now takes any small business, trading or starting from
nothing. Live, taking payments.

The platform runs on a workforce of twenty-four agents across four families: a spin-up pipeline,
support, marketing and corporate. Six of them are the pipeline that stands up an entire vertical
from a single brief, and the last agent in it is QA, with the authority to refuse.

**Cura Mirai** is a governance kernel that sits around any model and does not trust its guardrails.
Patent pending.

**DXP Auditor** crawls a site and scores its digital experience across eighteen dimensions, one
agent each, because accessibility needs a real browser and axe-core, performance needs Lighthouse,
content quality needs a model reading actual copy, and security needs headers and TLS.

**CrewRights AI** answers questions about a labour agreement, built so a confidently wrong answer
is harder to produce than no answer.

Most of this is commercial and private. What is public here is a subset.

## How I architect these

The Cura Mirai kernel is the clearest example, because the constraint was severe: it governs a
model's behaviour and it cannot itself be a model. It is deterministic, auditable and
model-agnostic by construction.

Its modules separate along the lines of the decisions being made, not along the data:

| Module | Responsibility |
|---|---|
| Signal detector | Recognises indicators, with pluggable strategies |
| Signal accumulator | Holds history so a pattern is distinguishable from an incident |
| Policy registry | Loads packs, rules and their inheritance |
| Policy evaluator | Decides what a set of signals licenses |
| Escalation state machine | A one-way ratchet with irreversibility floors |
| Consent enforcer | Gates everything on what was actually agreed |
| Audit logger | Hash-chained, so the record cannot be quietly rewritten |
| Jurisdiction resolver | Selects the rules that apply here |
| Reasoning commissioner | Commissions bounded questions to a model and nothing more |

Two properties matter more than the module list. **Governance state is hidden from the model**, and
the model is only ever asked bounded questions, because a component that can be argued with is not
a safety control. And **any model failure resolves to maximum safety** rather than to silence.

The kernel runs on FastAPI and Pydantic and deliberately nothing else. No vendor SDK, raw HTTPS, so
it stays portable across providers rather than inheriting whichever one it was written against.

## Taxonomy and ontology, and how they meet

These get used interchangeably and they are not the same thing. Getting the distinction right is
most of what makes a domain system extensible.

**The taxonomy names what can happen.** In Cura Mirai it runs across three axes rather than one
list, because the mitigations differ. Axis A is the child's own indicators: self-harm, low mood,
disordered eating, substance use, radicalisation, isolation, functional decline. Axis B is harm
from others toward them: grooming, bullying, abuse, sextortion, neglect, coercion, exploitation.
Axis C is risk in the system's own output, because a product that can cause harm has to appear in
its own taxonomy. Axis C is openly the thinnest, and it is recorded as such rather than quietly
omitted.

**The ontology declares what follows.** A policy pack carries far more than a rule list: a
jurisdiction path, an authority tier, an instrument type, a pedigree, age bands, what it inherits,
its source, a clarification protocol, and its crisis resources. Its indicators each bind to a
taxonomy category and carry their own authority, source citation, guardrail and severity. Its rules
carry a condition, the action triggered, and their detector dependencies.

So the join is explicit. The taxonomy supplies the nouns. The ontology says what each noun means
here, on whose authority, for which ages, under which jurisdiction, and what it licenses the system
to do. Adding a jurisdiction is a file. Adding an authority is a field. Neither is a release.

One field in that structure matters more than it looks: `pedigree`. It records whether a pack was
authored by a domain expert or extracted from source material. Most of them say `extracted`, which
is a limitation the packs state about themselves rather than a claim they make.

The same shape carries entirely different domains. In the audit system it holds web standards
extended by platform rules, extended again by jurisdictional insurance regulation, where every
regulatory claim cites the bulletin or statute behind it. Same engine, swapped knowledge.

## What twenty years of design brings to this

Research first. Accessibility by default. Privacy by design. Measure everything. Technology
disappears. Ship, learn, repeat.

Those are not slogans I picked up recently. They are why I map a process before I choose a tool,
why the accessibility suite existed at all before anyone asked for it, and why the first question
in an onboarding flow I built asks whether someone already has a business, because an existing
operation and a standing start are not the same current state and cannot share a map.

I have also built the apparatus around innovation rather than only doing it: a pipeline running
from technology backlog through opportunity screening, concept development, rapid prototyping and
subject-matter review to a decision to scale or retire, with a cross-functional expert panel
reviewing each concept and delivery teams sized to the stage. Making innovation repeatable is a
different discipline from being innovative, and organisations usually need the first one.

Original research I have authored includes conversational AI design patterns for trust-sensitive
and regulated environments, AI-driven experience personalisation, character-based digital
assistants, and connected journeys across physical, mobile and virtual touchpoints.

## What I check for now

Three times, in unrelated systems, I have found something reporting success while doing nothing.

An accessibility suite ran on every push, printed its violations to the console and passed, because
nobody had written the assertion. Sixteen of seventeen pages were failing WCAG AA on colour
contrast the whole time and CI stayed green. It surfaced only when someone went to put a compliance
claim in writing and the claim got checked.

A safety harness reported 100 percent detection and zero false positives. Both true, both useless,
because it measured whether a signal was detected and never whether it reached the person who
needed it. Eighteen categories were being dropped silently in between, including a child disclosing
abuse producing no output at all.

A scheduled research job ran every morning at six, exited zero and stored nothing for seven weeks
after its data source closed its API. One `sys.exit(0)` on an empty result was the entire bug.

So a green scorecard is not evidence, logging is not testing, and an exit code of zero means
nothing until something has proven it can be non-zero. The only defence I trust is a check I have
watched go red.

## Contact

[seanpauldoherty.com](https://seanpauldoherty.com) · [LinkedIn](https://linkedin.com/in/seanpauldoherty) · seanpauldoherty@gmail.com
