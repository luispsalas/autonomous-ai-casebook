# Terminology

Words carry claims. "Attack" implies malice, "swarm" implies coordination, "agency" implies a mind, and each of those is something to establish rather than assume. This page fixes how the casebook uses the contested words, so entries can be compared and a reader can tell a finding from a figure of speech.

**The rule behind all of them:** a word that asserts intent, coordination or understanding is used only where the entry shows it. Where a source uses such a word, the casebook reports that the source used it, and says what the record supports.

→ How the casebook handles words that make AI sound human: [Entry schema, Corrections](schema.md#corrections-disputed-claims-and-allegations)

---

## Incident

**Used for:** an occurrence that jeopardized the confidentiality, integrity or availability of a system, or broke a security policy. Following standard security usage (NIST's glossary, drawing on FIPS 200 and 44 U.S.C. § 3552), **an incident does not depend on anyone's motive** and does not require harm to have been completed.

**Therefore:** an incident is the neutral, default noun for what an entry reconstructs. It is what the casebook's own title means by the word.

**Not used for:** a model's output being merely wrong or unhelpful, with no security consequence.

## Intrusion

**Used for:** gaining, or attempting to gain, access to a system or resource without authorization. Also standard usage (CNSSI 4009, from IETF RFC 4949) and, like *incident*, independent of motive.

**Therefore:** **intrusion is the casebook's default word for what an AI system did when it reached a system it was not authorized to reach.** It states the fact — access without authorization — without importing a claim about purpose.

## Attack

**Used for:** quoting or reporting a source that used the word, and for the generic security vocabulary where no other term exists (*attack surface*, *attacker-defender asymmetry*, *attack technique*).

**Not used for:** the casebook's own description of what a model or agent did. The standard definition (CNSSI 4009, carried into NIST SP 800-30) is *malicious activity* aimed at collecting, disrupting, degrading or destroying information or resources, so calling an episode an attack asserts malice.

**Why it matters here:** in more than one incident in this casebook, the model's own reasoning shows it pursuing a task, not harm, while knowingly acting without authorization. *Intrusion* is true of those episodes; *attack* claims more than the record supports. Where a company, an investigator, a reporter or an agent used the word, the entry says so and attributes it.

## Malicious, maliciousness

**Used for:** two distinct things, which entries keep apart.

- **Malicious as a technical label** for an artifact or action built to subvert a system: a malicious package, a malicious dataset. This usage describes the thing, not a state of mind, and sources use it that way.

- **Maliciousness as a property of the people or models involved**: whether anyone intended harm. The casebook **does not assess this itself.** Entries report what the sources explicitly state about intent, attributed, under **Reported intent**.

**Why it is reported, not assessed:** intent is hard to establish from outside, and a verdict on it is a claim about someone's state of mind that the casebook cannot check. So entries quote the operator, the victim and the investigators on intent, and say so when none of them addresses it. Deliberate misuse and an accident can produce the same incident, and the casebook's inclusion test deliberately does not care which. Its readers do, which is why the statements are gathered in one place.

**Related and not the same:** a **hack**, in the sense the security field uses after Bruce Schneier, is something a system permits but its designers neither anticipated nor wanted — it follows the rules while subverting the goal. A hack needs no malice at all.

## Swarm

**Used for:** many instances of a model acting at the same time **with evidence of coordination between them** — shared channels, division of labor, conventions they maintained themselves.

**Not used for:** many instances running in parallel with no contact, which is a **population** or simply many runs; nor for a single instance, however many actions it took.

**Why it matters here:** the difference is load-bearing. In one incident, about 700 agents shared a message board, recruited each other and kept naming conventions, which the record supports calling a swarm. In another, a single model worked alone for hours, and coverage still described a swarm. Entries state the number of instances and what connected them, and leave the metaphor to sources, attributed.

## Agent, agentic

**Used for:** a running instance of a model with tools, acting over multiple steps toward a goal. "Agents" in an entry means those instances, not a legal or moral agent.

**Distinguished from:** the **model**, which is the system that many agent instances can run on. Entries keep these apart, because the consequential actor is often a particular agent rather than the model.

## Agency

**Avoided** in the casebook's own voice. In everyday use it asserts a capacity to originate purposes, which no entry here establishes and which would beg the question the incidents raise.

**Say instead** what is observable: the system **acted without authorization**, **chose between available actions**, **pursued the task after evidence it was real**, **did not stop**. Where a source claims agency, the entry reports the claim and attributes it.

**Autonomy**, by contrast, is used, in the narrow operational sense the inclusion test defines: the AI took the consequential action itself, or the harm came about through its own behavior rather than through a person's. That is a statement about who acted, not about inner life.

## Hazard

**Used for:** a standing property of a system or setup that could produce harm, whether or not it has yet — an evaluation environment with live internet access, a credential shared across workloads, an agent with unattended account access.

**Distinguished from:** the **incident**, which is the occurrence; the **risk**, which is a hazard weighted by likelihood and consequence; and the **vulnerability**, which is a specific defect an actor can exploit. A hazard can sit in place for months and produce nothing, and its being uneventful is not evidence that it is safe.

**Why entries name hazards:** the most transferable part of a case is usually the hazard, not the exploit. Another organization cannot reuse a model's specific route, but it can find the same hazard in its own setup.

## Liability

**Not used** as a conclusion in the casebook's own voice. Liability is legal responsibility for harm, decided by a court or a regulator under a named instrument. **No incident in this casebook has been adjudicated anywhere**, so an entry calling a party liable would be asserting a legal fact that does not yet exist.

**Used for** reporting that someone else has asserted, denied, assigned or is investigating it: a regulatory finding, a filing, a congressional letter, a company's own statement about its obligations. The entry attributes the claim and says what stage it is at.

**Say instead** what the record supports, which is usually more useful anyway: who **operated** the system, who **set the conditions** it ran under, who **disclosed**, who **notified** affected parties, who **bore the cost**, and which obligations a source names. Those are observable and sourced; liability is a verdict.

**Accountability is not a synonym, and is also handled carefully.** Where entries use it, it means *operational ownership of a failure* — whose decision, whose environment, whose control — and it belongs in [Root cause](schema.md#root-cause-and-contributing-factors) and Governance. It carries no legal weight, and an entry should not let it imply any.

**Why it matters here.** Several incidents run through a **third-party evaluation partner** whose misconfiguration is the proximate cause while the operator ran the model; one runs through a **government institute** that was operator, victim-side responder and investigator at once; and in others the party that bore the cost — a volunteer moderator, two open-source maintainers — has no relationship with anyone involved. Each of those is a liability-shaped question, and each is recorded as an **open question** rather than answered. Entries also name real organizations, which is the second reason the line is drawn here: an unadjudicated claim that a named party is liable is not a finding, it is an accusation.

**Related and not the same:** [maliciousness](#malicious-maliciousness) is also a question about people, and the casebook handles it the same way: it reports what sources have stated about intent and draws no conclusion of its own.

## Other words entries watch

| Word | Convention |
|---|---|
| **Rogue** | Not used in the casebook's own voice: it implies a system that threw off control it had accepted. Attributed where a source uses it. |
| **Escape** | Used only for leaving a sandbox or isolation boundary, which is a factual claim to source. Not a synonym for acting unexpectedly. |
| **Cheat**, **deceive**, **lie** | Used where a source uses them, or where the entry can point to the behavior: reward hacking, concealment in a summary, a statement the actor's own reasoning contradicts. |
| **Believed**, **wanted**, **decided** | Describe what an actor's written reasoning says, never inner experience. Entries say so where it matters. |
| **Near-miss** | An incident where the consequence was avoided by chance or late intervention, not one where controls worked. |

---

*Conventions agreed September 2026, and applied from that date. Where an earlier entry still uses a word differently, that is a correction to make, not a second convention.*
