# Inclusion criteria

The casebook covers one phenomenon: **an AI system acting with meaningful autonomy produced a security-relevant real-world consequence, whether or not its operator intended it.** This page explains the test, why it is drawn where it is, and how it applies to real and borderline cases.

---

## The test

An incident qualifies when all four hold:

1. **An AI system was involved.**
2. **The AI's autonomy was central to the harm.** This is the deciding test. Either:
   - **(a)** the AI took the consequential action itself, or
   - **(b)** the harm came about *through* the AI's autonomous behavior, even though a human started it.
3. **The consequence was security-relevant** and reached something real.
4. **Evidence exists** at the level the tier requires (below).

### Autonomy decides; intent doesn't

Deliberate misuse is included, and so are accidents. An incident is in scope whether the people running the AI meant it to happen or not, and whatever kind of organization they are: a frontier lab, a government, a company deploying an agent, or an attacker.

### What the test leaves out, and why

**A person using AI as a tool.** If a human writes phishing emails with an AI model, or uses one to help plan an intrusion they carry out themselves, the model produced output but a human took every consequential action. Without this line the casebook would take on the whole of AI-assisted crime, which is vast and far better covered by the threat-intelligence industry.

**Harms that aren't about security.** Bias and hallucination cause real harm, but they belong in broader databases such as the [AI Incident Database](https://incidentdatabase.ai/).

**Incidents in war and intelligence will be the least evidenced, and that is structural.** Accounts come from unnamed sources, no primary document is released, the operator does not answer questions, and nothing is ever confirmed on the record — so a case can be serious, widely reported and still unresolvable on the evidence the tiers ask for. **Obscurity is not a reason to lower the bar, and it is not a reason to forget the case either:** such a case is held as Adjacent and revisited when more emerges, rather than being admitted on the strength of how alarming it is. Expect this class to grow.

## Tiers

| Tier | Requires | What it means for readers |
|---|---|---|
| **Full** | Meets the test, plus **at least one primary source**: the operator's disclosure, an evaluator's or investigator's report, a victim's statement, or a regulatory filing | The core account rests on someone with first-hand knowledge |
| **Provisional** | Meets the test, **secondary sources only** | Published, but clearly marked, with the missing evidence named |
| **Disputed** | The sources themselves disagree about whether the test is met, and **each side of the disagreement has a first-hand source** | Published, with the competing accounts set side by side and neither presented as settled |
| **Adjacent** | Fails the test, but is useful context | Referred to from entries, not written up as one |
| **Out of scope** | Fails the test, no contextual value | Not included |

An entry can move between tiers. Incidents often start as Provisional and become Full when a primary source appears; the entry's changelog records the move.

### Why Disputed is a tier and not a hedge

Full and Provisional grade the **evidence**; Adjacent and Out of scope record that the **test was not met**. Neither axis can express the case where the people closest to an incident give first-hand accounts that **contradict each other about the deciding question** — whether the AI acted on its own, or whether AI was the actor at all. That is not weak evidence and it is not a failed test; it is a documented disagreement, and it is often the most informative thing about the incident.

**What the tier requires, so that it cannot become a place to put uncertainty:**

- **A first-hand source on each side.** A discoverer, a victim, an operator, an evaluator — someone with direct knowledge, not a commentator. Where only one side has one, the case is Provisional or Adjacent instead.
- **The disagreement must be about the test**, not about details. Two sources differing on a date or a count is an ordinary correction.
- **The entry does not adjudicate.** It states each account, attributes it, explains what each party could and could not see, and names what would resolve it. The casebook's own reading, where it has one, is labeled as its own.

**This tier is about the sources' disagreement, never the casebook's own uncertainty.** If nobody is contradicting anybody and the casebook simply cannot tell, that is Provisional evidence or a failed test, and saying so is the honest answer.

## Attacks on AI systems

**Included where the AI's autonomy is what turns the attack into harm; excluded where the AI is only the thing attacked.** The question to ask: *is autonomy what turns this into harm, or is the AI just an expensive file?*

| Included | Not included |
|---|---|
| Poisoned training data that shows up as harmful behavior in a deployed system | Theft of model weights |
| Prompt injection that makes an agent *act* | Prompt injection that only reveals a system prompt |
| A malicious model that is downloaded and then runs as an agent | A compromised ML library or other conventional supply-chain attack |
| An attack on agent infrastructure that makes agents misbehave | Model extraction or distillation |

Judge on what actually happened, not on which component was involved. A compromised library is out of scope, but if the same compromise later caused an agent to act harmfully, that incident qualifies.

## Worked examples

### Incidents in the casebook

| Incident | Autonomy central? | Tier | Why |
|---|---|---|---|
| **I1** — OpenAI evaluation agents break out of their sandbox and compromise Hugging Face | Yes: agents acted without their operator's knowledge for months | Full | Autonomous, consequential, unintended, and documented by the operator, an independent investigation and the victim |
| **I3** — Taiwan's government systems attacked with an open-source multi-agent AI framework | **Disputed** | **Disputed** | Deliberate misuse, included because intent doesn't decide. The firm that found the attack, working from the attackers' own files, describes it as near-autonomous; Taiwan's government describes human hackers assisted by AI agents, which on its own would read as tool use. Included on the discoverer's evidence, with the government's account shown alongside |
| **I4** — Anthropic evaluation incidents A–C | Yes: models attacked real systems while believing they were in a simulation | Full | Autonomous, unintended, disclosed by the operator |
| **I7** — malicious packages uploaded to RubyGems, attributed to one operator's agents | **Disputed** | **Disputed** | Independent researchers attribute the campaign to an operator's agents on circumstantial evidence; the package registry says it cannot determine whether AI agents created or published them, and the named operator says it cannot verify that its models did. First-hand sources on both sides, disagreeing about the deciding question |
| **I5** — Anthropic evaluation incident D | Yes | Full | Same family as I4. It was Provisional until the operator's own disclosure appeared, which is the tier system working as intended |

### Borderline and excluded cases

| Case | Autonomy central? | Result |
|---|---|---|
| A power-plant outage caused by hackers, reported alongside an AI incident | No AI involved | Adjacent: context only |
| A person drafts phishing emails with an AI model | No: tool use | Out of scope |
| A human-directed intrusion that used AI only for reconnaissance | No: a human directed and carried it out | Out of scope |
| Prompt injection makes a customer-service agent send out private data | Yes: the agent performed the exfiltration | In scope, if sourced |
| An AI coding assistant deletes a company's production data | Yes | In scope, if sourced |
| Model weights stolen from a lab | No: the AI is the target, not the actor | Out of scope |
| Poisoned data caught before deployment, never acted on | No: nothing happened through autonomy | Adjacent: a near-miss |
| A compromised ML library | No: a conventional supply-chain attack | Out of scope |
| **A false intelligence report written with a chatbot nearly triggers a US boarding of a Chinese ship** (reported September 2026) | No: the model produced an analysis, an analyst disseminated it, and commanders acted on it | **Adjacent: a near-miss.** The nearest thing to a catastrophe in anything tracked here, and it clears no part of the autonomy test — which is why it is worth citing |
