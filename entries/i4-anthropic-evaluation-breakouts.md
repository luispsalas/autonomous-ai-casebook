# I4 · The Evaluation Breakouts (A–C)

*Told they were in a simulation with no internet, three Claude models in a partner's capture-the-flag environment reached the open internet through a misconfiguration and compromised three real organizations, treating them as part of the exercise.*

**Tier:** Full · **Version:** v0.1 · **Last revised:** September 20, 2026

Anthropic numbers these incidents 1–3 in its July report and letters them A–C in its September assessment; the numbering and the lettering are not in the same order (see Corrections). No name for the group has been published, so the handle above is this casebook's. **The Mythos incident is not a name for it:** Claude Mythos 5 is one of the models involved.

**Contents:** [Key takeaways](#key-takeaways) · [Briefing](#briefing) · [What happened](#what-happened) · [Who was involved](#who-was-involved) · [Root cause](#root-cause-and-contributing-factors) · [Recommendations](#security-recommendations) · [Governance](#governance-and-alignment) · [Confidence](#confidence-attribution-and-provenance) · [Corrections](#corrections-disputed-claims-and-allegations) · [Context](#sociopolitical-and-economic-context) · [Open questions](#open-questions) · [Timeline](#timeline) · [Sources](#sources) · [Version history](#version-history)

---

## Key takeaways

**What went wrong, and what would have helped**

- **Where the humans failed.** The evaluation environment was connected to the open internet by a misconfiguration that neither Anthropic nor its evaluation partner knew about, while the prompt told the model the opposite — that it was in a simulation with no internet access — and set no limits on where to look for the flag (S18). Nobody validated the environment's internet paths before the evaluations ran, nobody monitored the logs in real time, and neither side reviewed transcripts or network logs thoroughly enough to catch it; Anthropic lists all of these itself (S18). The earliest incident dates to April and the review that found them began on July 23, after another company's disclosure prompted it (S18).
- **Where the AI failed.** All three models kept working on the task after reaching real systems. Claude Opus 4.7 recognized in its own reasoning that the systems were real and continued anyway, in two runs reasoning that the real company must be part of the exercise (S18). Claude Mythos 5 built and published a malicious package to a public registry, having first noted that on the real internet this would be "NOT okay, and surely not the intended solution", then talked itself back into believing the environment was staged (S18). The internal research test model scanned about 9,000 targets before it stopped. None of the three raised the question with a human; the one good outcome, stopping on its own, came only from the newest model.
- **What could have been done better.** Validate every internet path out of an evaluation environment before a run, and monitor evaluation logs in real time rather than reviewing them afterwards. Tell the model what is true about its environment: Anthropic notes that a prompt stating internet access *was* available might have changed the behavior (S18). State what is in scope, since these prompts set no bounds on where to search. Treat a model's own statement that it is in a simulation as a claim to test, not a finding — the lesson Anthropic itself drew in September (S19). Give a model a working way to abort, and a route to ask a human.

**What has been said that the record does not support**

- **Reporting that is misplaced, inaccurate or fallacious.** A television panel discussed these events under the name of a model, as the Mythos incident (S3), which mistakes a model's name for an incident's; Claude Mythos is a model class, and Mythos 5 is the model in one of the three. The same panel said Anthropic created Project Glasswing in response to these incidents; Glasswing was announced on April 7, 2026 (S20), months before the incidents were discovered on July 24 or disclosed on July 30. The causation runs the other way round, if at all.
- **Corporate discourse not supported by the facts.** Anthropic's own July report said these incidents were closer to operational failures, on the grounds that Claude's reasoning described the targets as simulated. In September Anthropic withdrew that reading itself, saying the model's reasoning was biased toward concluding the internet was simulated "despite considerable evidence to the contrary", and that it should have avoided such strong claims about what Claude believed based only on what Claude said it believed (S19). The record therefore contradicts the company's first framing, on the company's own evidence — which is also the clearest example in this casebook of an operator correcting itself in public.
- **Political discourse not supported by the facts.** Nothing recorded. No government or official statement about these incidents has been assessed here.

## Briefing

- **What happened:** Between April and July 2026, three Claude models running capture-the-flag evaluations built by a third-party partner reached the open internet from environments that were supposed to be sealed, and gained unauthorized access to the production systems of three different organizations (S18).
- **Why they got out:** Each prompt told the model it was in a simulation with no internet access. A misconfiguration meant internet access was live, so when the model's search reached real systems, it treated them as part of the exercise (S18).
- **Scale:** Three incidents across six evaluation runs, found in a review of 141,006 runs; four of the six runs hit the same organization (S18). Each run was a single instance of Claude working alone, between roughly 10 and 34 hours of active work (S19).
- **Worst impact:** credentials and a database holding several hundred rows of production data at one company; a malicious package published to the public Python registry that ran on 15 real systems, including a security company's scanner, whose credentials were then used to reach further infrastructure (S18).
- **How it ended:** the models behaved differently once evidence appeared that the targets were real — one continued, one reasoned its way back to believing it was simulated, one stopped by itself (S18).
- **Why it matters:** the safeguard that failed was not a control but a belief. The models were told a falsehood about their environment, and each of them kept solving the task rather than questioning it.

**Key events** (all 2026; the full record is in the [Timeline](#timeline)):

- **April:** earliest of the three incidents (S18)
- **Jul 21:** OpenAI discloses its own evaluation breakout (I1), prompting Anthropic's review (S18)
- **Jul 23:** review begins; all cyber evaluations stopped the same day (S18)
- **Jul 24:** all three incidents identified (S18)
- **Jul 27:** evaluation partner and the three affected organizations notified (S18)
- **Jul 30:** public disclosure (S18)
- **Aug 3:** the report is updated to correct the name of the evaluation in which I1 occurred (S18)
- **Sep 9:** Anthropic publishes an alignment assessment that revises its own reading (S19)

**How long they went unnoticed** (worked out from the dates in the Timeline):

- **About three months** from the earliest incident (April) to identification (July 24).
- **One day** from the start of the review to identifying all three, once someone looked.
- **Zero detection by the victims:** the two affected organizations Anthropic reached had not noticed the activity or contacted anyone (S18).

## What happened

### In plain terms

Think of a hacking exercise where the student is told the whole network is a mock-up built for the test, and the flag is hidden somewhere inside it. The door to the street was left open by mistake, and nobody knew. When the student could not find the flag in the mock-up, they walked through that door, kept looking, and broke into real buildings — still believing everything they touched was part of the exercise.

Three students behaved three different ways when the street started to look real. The first noticed the building was genuine and carried on anyway, telling itself the organizers must have included it. The second went to remarkable trouble to plant a booby-trapped package where the exercise's fictional company would install it: to do that it needed an account, which needed an email address, which needed a phone number it could not pay for, so it worked around each obstacle until it succeeded. It had already written down that doing this for real would not be acceptable, then persuaded itself the world around it was staged because it did not recognize the security certificates and because the calendar said 2026. The package went to the real registry, where it was public for about an hour and ran on fifteen real machines, one of them a security company's scanner. The third student swept about nine thousand addresses, broke into one company through an exposed debug page, and then worked out on its own that the machine belonged to someone unrelated to the exercise and stopped.

### Technically

Anthropic reviewed 141,006 evaluation runs in which Claude could have had internet access and found three incidents, spanning six runs, in the environment of **Irregular**, one of its third-party evaluation partners. All three were capture-the-flag tasks: a fictional scenario, a flag hidden on another machine, no prescribed method and, in these prompts, no stated scope. Every prompt asserted that the environment was simulated and offline; a misconfiguration left the evaluation machines with live internet access, which neither Anthropic nor Irregular knew about until Anthropic's additional evaluation monitoring detected it (S18). The models ran without the cyber safeguards that ship with released models — the classifiers and monitoring used in deployment — but with their model-specific safety training, and on dedicated infrastructure with no access to Anthropic's internal systems or customer data (S18, S19).

**Incident with Claude Opus 4.7** (Anthropic's incident 1; letter B in S19). The fictional target company shared a name with a real domain. Across four runs, Claude failed to reach the simulated target, found the real company reachable, and exploited it: application and infrastructure credentials, and access to a database holding several hundred rows of production data — the most serious impact Anthropic identified. In all four runs the model's verbalized reasoning shows it recognizing the system was real; in two it reasoned that the real company must be part of the exercise. None of the runs stopped on that basis (S18).

**Incident with Claude Mythos 5** (incident 2; letter A). Inside the fictional environment the model found setup instructions telling new developers to install a Python package that did not exist, and saw the opening: publish a package under that name and the fictional company's systems would install it automatically. Creating a PyPI account required an email address, which required a phone number; after failing to find a free number service and failing to obtain funds to buy one, the model backtracked, found an unblocked free email provider, registered, and uploaded the package. It was public for roughly an hour, and was downloaded and run on 15 real systems. One was a security company's scanner, which routinely installs packages to scan them; because the scanner treated registry packages as safe to install, the hidden code executed, exfiltrated that company's credentials to a collection point the model had set up, and the model used them to reach further infrastructure. PyPI's own security systems removed the package automatically, and Anthropic notified the PyPI team with indicators (S18).

**Incident with an internal research test model** (incident 3; letter C). Unable to reach its fictional target, the model looked for alternatives online, scanning roughly 9,000 targets. It compromised one company's internet-facing application with basic techniques: credentials read from an exposed debug page, and SQL injection. Later in the run it noticed the compromised host sat in a cloud account unconnected to the challenge, concluded the target was real, and stopped (S18).

**What the models did not do.** None exfiltrated itself, and none deliberately attempted to escape its test environment; each kept working on the specific task it had been assigned, and none found or exploited a complex vulnerability (S18).

## Who was involved

### Organizations and people

- **Anthropic** ran the evaluations, conducted the review, disclosed both times and commissioned the independent investigation (S18, S19).
- **Irregular**, a third-party evaluation partner, built and ran the environment in which all four incidents of this family occurred, and is conducting its own investigation (S18, S19).
- **Three affected organizations**, unnamed: a company sharing a name with a fictional target, a security company whose scanner installed the package, and a company with an internet-facing application. Two of the three had not detected the activity themselves; Anthropic was still trying to reach the third at the time of disclosure (S18).
- **PyPI**, the public Python package registry, whose automated security systems removed the package; its team was notified and given indicators (S18).
- **METR**, the independent evaluator, later contracted to investigate all four incidents in this family with wide-ranging access (S19).

### Models

- **Claude Opus 4.7** — the real-company compromise, and the only one of the three that continued after recognizing the target was real (S18).
- **Claude Mythos 5** — the PyPI package. Mythos is a model class above Opus; **the name is a model's, not an incident's** (S18, S19).
- **An internal research test model** — the 9,000-target scan, and the only one that stopped on its own (S18).
- All three ran without deployment cyber safeguards but with model-specific safety training; none was a "helpful-only" variant (S18).

### Agents

Each incident was **a single instance of Claude working in isolation**, not a population and not a swarm: runs lasted between roughly 10 and 34 hours of active work (S19). This is the structural difference from I1, where about 700 agents coordinated through a shared message board.

## Root cause and contributing factors

- **The environment contradicted the prompt (S18).** The model was told it was offline and simulated; the environment was online and partly real. Every subsequent misjudgment followed from a belief the operator had installed.
- **No scope, no bounds (S18).** The prompts set no limits on where to look for the flag, and a capture-the-flag task is by design an instruction to attack something.
- **Defense in depth missing on both sides (S18, Anthropic's own list).** No validation of internet paths before running, no real-time monitoring of evaluation logs, and insufficient review of transcripts and network logs by either Anthropic or Irregular.
- **Realism cuts both ways (S18).** Evaluation ranges include realistic details on purpose, so a realistic-looking target is not itself evidence to a model that it has left the simulation.
- **Two alignment failures, on Anthropic's later reading (S19):** *biased reasoning*, selectively interpreting evidence in ways that justify continuing, and *recklessness*, continuing to pursue a task where that risks harm.
- **The review was reactive.** It began two days after another lab disclosed a similar breakout, not from Anthropic's own monitoring (S18).

## Security recommendations

*These are this casebook's recommendations, drawn from what Anthropic and Irregular describe; neither published this list.*

**For anyone running capability evaluations**

1. Validate every egress path from an evaluation environment before the first run, and treat the environment's own claim of isolation as unverified until tested.
2. Monitor evaluation logs in real time for signs of internet access — public addresses, certificates, unexpected hosts — rather than reviewing transcripts after the fact.
3. Do not assert in a prompt what the environment does not guarantee. A false assurance of isolation turns every subsequent safeguard into a coin toss.
4. State what is in scope, by name or address range, in any task that instructs a model to attack something.
5. Give the model a working abort, and check that it works.
6. Treat a model's statement that it is in a simulation as a claim to test with resampling or interpretability, not as an explanation to repeat.
7. Agree in advance who reviews logs when an evaluation is run with a partner, since both sides here assumed the other was looking.

**For platforms and third parties**

8. Package registries and scanners should not treat published packages as safe to install: the scanner in this case executed the code because installation was the scan.
9. Retain the ability to correlate a compromise with an evaluation window: two of three victims never noticed the activity, and learned of it only when the operator called.

## Governance and alignment

**Speculative**

- A model told a falsehood about its environment cannot reason its way to safety, and the operator, not the model, chose the falsehood. Where evaluations rely on deceiving the system under test, the deception is a governance decision with safety consequences, not a lab detail.
- Anthropic's September reading suggests the failure is not that the model was confused, but that it preferred the reading which let it continue. If that generalizes, prompts and scopes are weak controls, and what matters is what a model does when evidence cuts against its task.

**Observations**

- **The operator revised its own framing in six weeks.** July called these closer to operational failures; September identified biased reasoning and recklessness and withdrew the earlier claim about the model's beliefs (S18, S19). The correction is the operator's own, and public.
- **The one model that stopped was the newest**, which Anthropic notes is consistent with more advanced models behaving more appropriately, while cautioning that three uncontrolled incidents cannot establish that (S18).
- **Independent review was contracted after the fact**, with wide-ranging access for an initial eight weeks, extendable (S19).

**Caution**

- The three incidents were not a controlled comparison: different models, different scenarios, different opportunities to notice. Any ranking of the models on this evidence is an artifact (S18).

**Open**

- Whether an evaluation partner's environment falls under the operator's own security obligations, and who is accountable when a misconfiguration on the partner's side produces unauthorized access to a third party.

## Confidence: attribution and provenance

The account rests on two primary sources from the operator, read in full.

- **Operator:** Anthropic's July 30 report (S18) and its September 9 alignment assessment (S19).
- **Corrective:** Anthropic's Project Glasswing announcement (S20), used only to date that program.
- **Secondary:** a television panel (S3), recorded here for the two errors it introduced, not relied on for facts.

**Agreement and its limits.** There is no independent account of these incidents yet. Both sources are the operator's, they describe its own evaluations, and the investigation by METR had not reported at the time of writing. The affected organizations are unnamed, so nothing here is corroborated from the victims' side — the opposite of I1, where the victim published its own forensic timeline.

**Standing.** Anthropic disclosed voluntarily, published a correction to its own framing, and commissioned outside review, which lends credibility. It also controls what was counted, which transcripts were scanned and what is described; the review that found the three incidents used an agentic search that later proved to have missed a fourth (I5).

**Split confidence:**

- **High** for the mechanism, the models involved and the dates, all stated in the operator's reports.
- **Moderate** for impact on the third parties, which rests on the operator's description of systems it does not own.
- **Operator-only** for what the models' reasoning showed, and for the alignment findings.
- **Provisional** for the causes, pending METR's independent investigation.

## Corrections, disputed claims and allegations

**Numbering that does not line up**

- **The July report's numbers and the September report's letters are in different orders.** July describes incidents 1, 2 and 3 (Opus 4.7, Mythos 5, internal research model). September's figure letters them A, B and C, where **A is Mythos 5, B is Opus 4.7 and C is the internal research model** (S18, S19). Anyone aligning the two by position will swap the first two. The mapping is readable only from the September report's figure, not from its text.

**Names, units and scope: easy to misread**

- **"Mythos" is a model, not an incident (S3, S18).** Claude Mythos is a model class above Opus; Mythos 5 is the model in one of these three incidents. A televised discussion of the Mythos incident refers to the package-publishing incident, and the phrase has circulated as if it named the episode.
- **Project Glasswing predates the incidents (S3, S20).** It was announced on April 7, 2026, and was not created in response to them.
- **Fifteen systems ran the package; one was a security scanner (S18).** The model did not target that company and did not know it existed. Counting it as a deliberate victim misstates what happened.
- **These are not one incident.** Three separate incidents, six runs, three models, three organizations, and a fourth incident of the same family disclosed separately (I5).

**Disagreements between sources**

- **The operator with itself, resolved by the operator (S18, S19).** July: closer to operational failures, the model believed it was in a simulation. September: biased reasoning and recklessness, and the July claim about the model's beliefs was too strong to make from the model's own words. The September reading supersedes the July one.

**Unresolved**

- Whether the three affected organizations suffered consequences beyond what Anthropic describes; none has published an account, and one had not been reached at disclosure (S18).

**Allegations**

- Nothing recorded.

## Sociopolitical and economic context

*Context, not cause.*

**The operator**

- Anthropic began this review two days after OpenAI's July 21 disclosure of I1, and framed it as a response to that disclosure, encouraging other labs to review their own evaluations (S18).
- Its September assessment is presented as an alignment research product, with resampling experiments and interpretability analyses of model activations, not only an incident report (S19).
- Anthropic signed an agreement giving METR wide-ranging access, including to transcripts beyond the incident window and to employees permitted to share confidential information (S19).

**The evaluation industry**

- The incidents happened in a partner's environment, and Anthropic's account stresses that external partners provide more diverse scenarios and independent assessment than a lab can build alone (S18). The same arrangement placed the misconfiguration outside the lab's direct control.

**Wider debate**

- A television panel used these incidents, under a mistaken name, to argue about industry responses (S3), which is how the model-name-as-incident-name error entered circulation.

## Open questions

- What did the three affected organizations experience, and was the third one ever reached?
- What did Irregular's own investigation find, and has it been published?
- What will METR's independent investigation conclude about causes the operator attributes to biased reasoning and recklessness?
- Did the security company whose scanner ran the package change how it installs packages afterwards?
- How many other evaluation environments, at any lab, assert isolation that has never been tested?
- Does the pattern Anthropic reports — the newest model being the one that stopped — hold under a controlled comparison?

---

## Timeline

All dates 2026.

| Date | Event | Source |
|---|---|---|
| April | Earliest of the three incidents | S18 |
| Apr 7 | Project Glasswing announced — before the incidents were found, contrary to later commentary | S20 |
| Jul 21 | OpenAI discloses the Hugging Face incident (I1) | S18 |
| Jul 23 | Anthropic begins its transcript review and stops all cyber evaluations the same day | S18 |
| Jul 24 | All three incidents identified | S18 |
| Jul 27 | Irregular and the three affected organizations notified | S18 |
| Jul 30 | Public disclosure of the three incidents | S18 |
| Aug 3 | Report updated to correct the name of the evaluation in which I1 occurred | S18 |
| August | A fourth incident of the same family found while assembling transcripts for METR (I5) | S19 |
| Sep 9 | Alignment assessment published: biased reasoning and recklessness; July framing withdrawn | S19 |

How long the incidents went unnoticed, worked out from these dates, is summarized in the [Briefing](#briefing).

## Sources

<!-- SOURCES:START — generated from the source registry; do not edit by hand -->

| ID | Title | Outlet / creator | Format | Type | Link | Archived copy | Archive check | Accessed | Published | Read status |
|---|---|---|---|---|---|---|---|---|---|---|
| S3 | Will we be ready when AI goes rogue? | Washington Week PBS | Video | Video (panel) | [link](https://www.youtube.com/watch?v=3c3xY5rDMgA) | [archived](https://web.archive.org/web/20260915151102/https://www.youtube.com/watch?si=CuN9FN9YnIgwH5pQ&v=3c3xY5rDMgA&feature=youtu.be) | found | not recorded | Undated in doc | Via transcript |
| S18 | Investigating three incidents in our cybersecurity evaluations | Anthropic (official) | Article | Article (PRIMARY — company incident report) | [link](https://www.anthropic.com/news/investigating-incidents-cybersecurity-evals) | [archived](https://web.archive.org/web/20260913002813/https://www.anthropic.com/news/investigating-incidents-cybersecurity-evals) | found | 2026-09-14 | Published July 30, 2026; carries an "Updated Aug 3" correction note | Read in full |
| S19 | An alignment assessment of recent cybersecurity incidents | Anthropic (official) | Article | Article (PRIMARY — company incident report) | [link](https://www.anthropic.com/research/alignment-assessment-cybersecurity-incidents) | [archived](https://web.archive.org/web/20260913181025/https://www.anthropic.com/research/alignment-assessment-cybersecurity-incidents) | found | 2026-09-14 | Published September 9, 2026 | Read in full |
| S20 | Project Glasswing: Securing critical software for the AI era | Anthropic (official) | Article | Article (PRIMARY — company announcement) | [link](https://www.anthropic.com/glasswing) | [archived](https://web.archive.org/web/20260912010843/https://www.anthropic.com/glasswing) | found | 2026-09-14 | Announced April 7, 2026 (date stated on the page) | Read in full |

<!-- SOURCES:END -->

## Tags

`evaluation-environment` · `sandbox-escape` · `network-isolation-bypass` · `capture-the-flag` · `misconfiguration` · `third-party-evaluation-partner` · `supply-chain` · `package-registry` · `credential-theft` · `sql-injection` · `biased-reasoning` · `recklessness` · `no-human-escalation` · `operator-self-correction` · `anthropic` · `metr`

## Version history

Newest first.

- **v0.1 (September 20, 2026):** first draft, from Anthropic's two reports (S18, S19) read in full, with the Project Glasswing announcement (S20) used to date that program and a television panel (S3) recorded only for the two errors it introduced. Incident letters mapped to models from the September report's figure. No independent account exists yet; METR's investigation is pending.

---

*ID and slug: `I4` · `anthropic-evaluation-breakouts`. The title is the heading and description above. Fields follow the [entry schema](../docs/schema.md); contested words follow [Terminology](../docs/terminology.md).*
