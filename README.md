# Sean Doherty

I design and ship AI systems, and I have been doing the same job across two generations of the
technology.

The first time round it was conversational assistants on Artificial Solutions Teneo, Google
Dialogflow and Alexa, when the models were intent classifiers, the output was mediocre, and
nobody in the business was asking for any of it. Assistants for roadside assistance, job search,
rail and airline travel, hotels, wealth management, broadcast. The models have been replaced
underneath me twice since. The problem has not changed: find where automation genuinely helps,
build it, and get people to use it.

Twenty years of product and design before that, which is mostly why I map a process before I
touch it.

## What is running

**SoloBusinessAI** gives a small business owner a team of six named agents: a chief of staff, a
support rep, a technical investigator, an ad creative director, a social media manager and a
content writer. Customer intake runs across phone, chat and web, bilingually, with a human
escalation path. It started as eight professional verticals and now takes any small business,
whether it is already trading or starting from nothing. Live, taking payments.

Behind it sit twenty-four more agents that build, support and market the platform. Six of those
are a pipeline that stands up an entire new vertical from a single brief, and the last one is a
QA agent with the authority to refuse. A vertical is not live until its smoke test passes against
the real deployment.

**DXP Auditor** crawls a site and scores its digital experience across eighteen dimensions, one
agent each, because accessibility needs a real browser and axe-core, performance needs Lighthouse,
content quality needs a model reading actual copy, and security needs headers and TLS. Used
commercially to audit national insurance carriers.

**Cura Mirai** is a governance layer that sits around any model and does not trust its guardrails.
Deterministic policy evaluation, a one-way escalation ratchet, fail-closed on any model failure.
The first application is child safety.

**CrewRights AI** answers questions about a labour agreement and is built so that a confidently
wrong answer is harder to produce than no answer. It quotes only values that appear in the cited
clause, states plainly when the contract does not cover something, and shows its citations rather
than hiding them behind a disclosure.

Most of this is commercial and private. What is public here is a subset, and I am glad to walk
through any of it.

## The thing I keep finding

Four times now, in unrelated systems, I have found something reporting success while doing
nothing.

An accessibility suite ran on every push, printed its violations to the console, and passed,
because nobody had written the assertion. Sixteen of seventeen pages were failing WCAG AA on
colour contrast the whole time and CI stayed green. It surfaced only when someone went to put a
compliance claim in writing and the claim got checked.

A safety harness reported 100 percent detection and zero false positives. Both numbers were true
and both were useless, because it measured whether a signal was detected and never whether it
reached the person who needed it. Driving the real chain end to end found eighteen categories
being dropped silently in between, including a child disclosing abuse producing no output at all.

A scheduled research job ran every morning at six, exited zero, and stored nothing for seven
weeks after its data source closed its API. One `sys.exit(0)` on an empty result was the whole
bug. Windows reported success every day.

So: a green scorecard is not evidence, logging is not testing, and an exit code of zero means
nothing unless something has proven it can be non-zero. The only reliable defence is a check you
have watched go red.

## How I work

I write the instruction files that govern agent behaviour, decide what stays deterministic and
what is safe to hand to judgement, connect the tools and data each agent needs, and own the
evaluations that decide whether a change shipped or regressed.

Domain rules live in versioned data rather than in the code that reads them. In the audit system
that means policy packs that extend one another and cite the bulletin or statute behind every
regulatory claim, so pointing the engine at another jurisdiction is a file rather than a release.
In the governance layer it means the same shape carrying a clinical screening protocol. The
engine stays general and the knowledge is swapped.

I hide state from the model where a component must not be argued out of its job, and I keep the
questions put to it bounded for the same reason.

## Contact

[seanpauldoherty.com](https://seanpauldoherty.com) · [LinkedIn](https://linkedin.com/in/seanpauldoherty) · seanpauldoherty@gmail.com
