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

## Tiers

| Tier | Requires | What it means for readers |
|---|---|---|
| **Full** | Meets the test, plus **at least one primary source**: the operator's disclosure, an evaluator's or investigator's report, a victim's statement, or a regulatory filing | The core account rests on someone with first-hand knowledge |
| **Provisional** | Meets the test, **secondary sources only** | Published, but clearly marked, with the missing evidence named |
| **Adjacent** | Fails the test, but is useful context | Referred to from entries, not written up as one |
| **Out of scope** | Fails the test, no contextual value | Not included |

An entry can move between tiers. Incidents often start as Provisional and become Full when a primary source appears; the entry's changelog records the move.

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
| **I3** — Taiwan's government systems attacked with an open-source multi-agent AI framework | **Disputed** | Full, autonomy disputed | Deliberate misuse, included because intent doesn't decide. The firm that found the attack, working from the attackers' own files, describes it as near-autonomous; Taiwan's government describes human hackers assisted by AI agents, which on its own would read as tool use. Included on the discoverer's evidence, with the government's account shown alongside |
| **I4** — Anthropic evaluation incidents A–C | Yes: models attacked real systems while believing they were in a simulation | Full | Autonomous, unintended, disclosed by the operator |
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
