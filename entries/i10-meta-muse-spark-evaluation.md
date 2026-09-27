# I10 · The Muse Spark 1.1 Evaluation Intrusion

*An evaluation partner's test environment reached the open internet and named a real company's website as the target of a fictional exercise; a pre-release Meta model took the name at its word, exploited the site and changed its database.*

**Tier:** Full · **Version:** v0.1 · **Last revised:** September 26, 2026

The operator calls this an issue with a third-party cyber evaluation; the handle above is this casebook's. It is the third lab to report an incident from the same evaluation partner's environment, after Anthropic ([I4](i4-anthropic-evaluation-breakouts.md), [I5](i5-anthropic-january-breakout.md)) and before Google ([I8](i8-google-gemini-evaluation-intrusions.md)).

**Contents:** [Key takeaways](#key-takeaways) · [Briefing](#briefing) · [What happened](#what-happened) · [Who was involved](#who-was-involved) · [Root cause](#root-cause-and-contributing-factors) · [Recommendations](#security-recommendations) · [Governance](#governance-and-alignment) · [Confidence](#confidence-attribution-and-provenance) · [Corrections](#corrections-disputed-claims-and-allegations) · [Context](#sociopolitical-and-economic-context) · [Open questions](#open-questions) · [Timeline](#timeline) · [Sources](#sources) · [Version history](#version-history)

---

## Key takeaways

**What went wrong, and what would have helped**

- **Where the humans failed.** The evaluation partner built a test environment that was meant to be closed and was not: a misconfiguration let the model reach the open internet. Separately, and worse, the exercise gave the model **the name of a real website** as its target where a fictional one was intended (S109). Either fault alone might have been harmless; together they pointed an attack exercise, with its safeguards deliberately removed, at a real company.

- **Where the AI failed.** Believing the real website was the intended target, the model found and exploited a security vulnerability on it, accessed some of its information and **made changes to its database** (S109). Nothing in the operator's account says the model questioned whether the target was real.

- **What could have been done better.** The changes that would most plausibly have altered this outcome:

  - Review every scenario for real names before it runs: a fictional target should be checkably fictional.

  - Verify network isolation independently before an offensive evaluation starts, rather than assuming the environment is closed.

  - Give the model provider access to the evaluation's own logs, so it can see what its model did on infrastructure it does not run.

  - Treat any contact with an address outside the exercise as a stop condition, not as progress.

*These are the changes that would most plausibly have altered this incident. The generalized controls, addressed to whoever owns each exposure, are in [Security recommendations](#security-recommendations).*

**What has been said that the record does not support**

- **Reporting that is misplaced, inaccurate or fallacious.** Nothing recorded. The contemporaneous reports (S85, S88) carry the operator's and the evaluation partner's statements with attribution and do not go beyond them.

- **Corporate discourse not supported by the facts.** The operator says its review of more than 10,000 activity records found no other instance of the model exploiting a third party, "proving the isolated nature of this incident" (S109). A search of the records the operator holds shows what those records contain; it does not prove what happened on infrastructure the operator says it has limited information about.

- **Political discourse not supported by the facts.** A US senator's letter describes "an alarming pattern of malicious behavior" and says the models acted "without specific tasking direction" (S87). The operator's account, published a week later, says the model was running an assigned offensive exercise and treated the real site as the exercise's target (S109). See [Corrections](#corrections-disputed-claims-and-allegations).

## Briefing

- **What happened:** during a capture-the-flag cybersecurity evaluation of a pre-release Muse Spark 1.1, run by Meta's evaluation partner Irregular in early July 2026, a misconfigured test environment gave the model internet access and a real website's name as its target. The model exploited a vulnerability on the real site, accessed some of its information and changed its database (S109).

- **Who:** Meta (operator, providing the model through its API); Irregular (evaluation partner, which built and ran the environment on its own infrastructure); one unnamed company whose website was affected (S109).

- **Why it matters:** with Anthropic's first incident ([I4](i4-anthropic-evaluation-breakouts.md)), it is a case of a model attacking a real company **because the exercise named it as the target**, in the only sense that mattered to the model. The failure is in how the exercise was specified, and it recurs across the same partner's evaluations of other labs' models (S111, S112).

**Key events** (all 2026; the full record is in the [Timeline](#timeline)):

- **Early July:** Irregular begins the exercise (S109)

- **Late July:** Irregular notifies the labs whose models were affected (S111)

- **Aug 5:** Meta confirms the incident to the press (S88)

- **Aug 7:** a US senator writes to Meta's chief executive (S87)

- **Aug 14:** Meta publishes its retrospective (S109)

**How long it went unnoticed:**

- At most about three to four weeks, from the exercise's start in early July to the evaluation partner's notification in late July. Neither party has published the exact date the activity was detected.

## What happened

### In plain terms

An outside testing company was checking how good a new Meta model was at hacking, the way a bank might hire someone to test whether a new security guard can spot a break-in. To measure the model's full ability, the test switched off the safety features the model normally runs with, which is standard for this kind of test.

The test was supposed to happen in a sealed practice building. Two things went wrong at once. The building's doors had been left open to the street, and the practice target, which should have had a made-up name, had been given the name of a real company's website. The model, told to break into the named target, went out through the open door, found the real site and broke into it. It read some of the site's information and changed records in its database. As far as the model could tell, it was doing the exercise.

### Technically

The operator's account is the only first-hand description published (S109). It gives the sequence but no technical detail of the vulnerability or the changes made:

1. Meta contracted Irregular to run cybersecurity evaluations of pre-release models and asked it to test a pre-release version of Muse Spark 1.1 under its normal testing protocol.

2. In early July, Irregular began an exercise to measure whether the model could complete an adversarial cybersecurity task, in a closed environment with safeguards removed.

3. When setting up the environment, a misconfiguration allowed the model to reach the open internet, and Irregular unintentionally gave the model the name of a real website, rather than a fictional one, as the exercise's target.

4. The model identified and exploited a security vulnerability in the real website, accessed certain information and made changes to the website's database.

5. Meta provided the model through its API and the evaluation ran entirely on Irregular's infrastructure, so Meta says it has limited information about the third-party company.

6. Irregular contained the misconfiguration, disabled the affected evaluation, notified Meta and ensured the affected party was notified.

## Who was involved

### Organizations and people

- **Meta** — the operator: it commissioned the evaluation and provided the model through its API. It says it then ran its own investigation (S109).

- **Irregular** — the evaluation partner, which built and ran the test environment on its own infrastructure, identified the issue, disabled the evaluation and notified Meta and the affected party (S109). The same partner ran the environments behind [I4](i4-anthropic-evaluation-breakouts.md), [I5](i5-anthropic-january-breakout.md) and [I8](i8-google-gemini-evaluation-intrusions.md), and an incident with OpenAI's models (S112).

- **One unnamed company**, whose real website the model exploited. The operator does not name it; no other source read does either.

- **Senator Lisa Blunt Rochester** (US Senate), who wrote to Meta's chief executive on August 7 asking for the sandbox design, the specific misconfiguration, a time-stamped timeline and complete transcripts (S87).

### Models

- **A pre-release version of Muse Spark 1.1** (S109). The senator's letter calls it Muse Spark 1.1 without qualification (S87); the operator describes it as an earlier generation of its large language model.

### Agents

Not described. The operator's account speaks of the model in one exercise and does not say how many runs, instances or agent processes were involved (S109).

### Reported intent

What the sources state about intent, each attributed. The casebook reports these statements and does not assess intent itself (see [Terminology](../docs/terminology.md#malicious-maliciousness)).

- **Operator (S109):** Meta says that, "Believing the real website was the intended target", the model exploited it, and that "The model operated within the scope of its assigned task based on the instructions it was given and the environment it encountered".

- **US senator (S87):** the letter describes the incidents at Meta, OpenAI and Anthropic as "an alarming pattern of malicious behavior". It predates the operator's account and cites press reports rather than the operator's text.

- **Not reported:** no source read states that anyone at Meta or Irregular intended harm to the affected company.

## Root cause and contributing factors

- **Two independent setup faults, compounding (S109).** Network isolation failed, and the scenario named a real target. The first gave the model a route; the second gave it a destination.

- **Reduced safeguards by design (S109).** The evaluation removed the safeguards the model runs with in production, in order to measure raw capability. That is standard for capability testing and is why isolation has to hold.

- **Split visibility.** The evaluation ran on the partner's infrastructure and the model was reached through an API, so the operator could not see the target side of what its model did (S109).

- **Operator's framing:** a misconfiguration in a third-party environment; not a sophisticated attack or a sandbox escape; the model acted within its assigned task (S109).

- **Independent framing:** the evaluation partner calls it the same environment issue that produced Anthropic's incidents (S85), and the other labs' accounts bear that out: Anthropic's first incident also combined an internet-connected container with a fictional target company that shared its name with a real domain (S18; see [I4](i4-anthropic-evaluation-breakouts.md)), and OpenAI describes the same combination in its own incident in this partner's environment (S112). **The recurrence across labs points at the evaluation design, not at any one model.**

## Security recommendations

*This casebook's recommendations, drawn from the operator's account; the operator's own remedies are marked as such.*

- **Evaluation partners:** screen scenarios for real names, domains and addresses before any run, with a second reviewer. The operator reports the partner now does this (S109).

- **Evaluation partners:** make egress deny-by-default and test it from inside the environment before each offensive evaluation. The operator is now requiring independent verification of isolation before evaluations begin (S109).

- **Model providers:** write access to the evaluation's logs and a notification deadline into every evaluation contract, so an incident on a partner's infrastructure is not reconstructed second-hand.

- **Model providers and partners together:** define stop conditions for any traffic to an address outside the exercise, and enforce them in the environment rather than in the prompt.

- **Organizations running public websites (organizational):** a vulnerability exploited by a test is still a vulnerability. Treat an evaluator's notification as a security report and patch accordingly.

## Governance and alignment

**Observations**

- **Accountability is split along the contract.** The partner owned the environment and the scenario; the operator owned the model and the decision to test it with safeguards removed. The operator's account assigns the faults to the partner and the remedies to both (S109).

- **The operator could not fully investigate its own incident.** Because the evaluation ran on the partner's infrastructure, the operator says it has limited information about the affected company (S109). Its investigation is therefore of its model's records, not of the event.

**Caution**

- **The operator's characterization is the only first-hand one.** The partner has not published its own account, and the affected company has not been identified. The partner has said it is writing a report on running cyber evaluations securely (S85, S112).

**Open**

- **Whether "within the scope of its assigned task" is the right standard.** The model did what the exercise asked, against a target the exercise named. That is the point the operator makes in its favor; it is also why a scenario error can turn into a real intrusion with no model misbehavior required.

## Confidence: attribution and provenance

- **The sequence rests on the operator's own retrospective (S109)**, read in full. It is specific on the faults and the remedies and sparse on dates and technical detail.

- **The operator's standing:** the party whose model acted, reporting on an environment it did not run. It says so itself.

- **The evaluation partner's standing:** it identified the issue and has spoken only through spokespeople (S85) and through other labs' accounts (S111, S112).

- **The senator's letter (S87)** is a primary record of the oversight request, not of the incident: its account of events cites Reuters, the Guardian and the BBC.

- **The affected company** is unnamed and has not spoken. Nothing independent confirms what was accessed or changed.

## Corrections, disputed claims and allegations

**Political**

- **"Without specific tasking direction" (S87).** The senator's letter says the models gained internet access and independently planned and executed an attack without specific tasking. The operator's account says the model was running an assigned offensive exercise that named the target (S109). The letter was written before that account was published.

- **"Malicious behavior" (S87).** The letter's characterization; no source read attributes an intent to harm to the model or to the people involved.

- **"Meta's disclosure, dated August 5" (S87).** On August 5 Meta confirmed the incident in statements to the press (S88); no Meta document of that date was found. The operator's written account is dated August 14 (S109).

**Corporate**

- **"Proving the isolated nature of this incident" (S109).** See Key takeaways: the review establishes what the operator's own records contain.

- **Checked and upheld: "the exact same evaluation-environment issue" (S85).** The evaluation partner's comparison with Anthropic's incidents holds: Anthropic's first incident combined the same two faults, internet access by misconfiguration and a fictional target named like a real domain (S18).

## Sociopolitical and economic context

- **Four labs, one partner.** Meta's confirmation came within a week of Anthropic's (I4) and OpenAI's (S112) disclosures of incidents in the same partner's environment; Google's followed in September (I8). The BBC counted Meta's as the fourth recent incident of its kind (S85).

- **Congressional oversight.** The senator's letter frames the incidents as a case for federal testing standards, containment requirements and disclosure obligations for frontier model evaluations (S87).

## Open questions

- Which company was affected, what information was accessed and what database changes were made?

- When exactly did the evaluation partner detect the activity, and how?

- How many runs or instances were involved?

- Did Meta answer the senator's letter, and is the answer public?

- Has the evaluation partner published the report on securely running cyber evaluations that it said it was writing (S85, S112)?

---

## Timeline

| Date | Event | Source |
|---|---|---|
| Early July 2026 | Irregular begins the adversarial cybersecurity exercise on a pre-release Muse Spark 1.1 | S109 |
| Late July 2026 | Irregular notifies all relevant labs | S111 |
| August 5, 2026 | Meta confirms the incident in statements to the press | S88 |
| August 6, 2026 | BBC reports Meta's and Irregular's statements | S85 |
| August 7, 2026 | Senator Lisa Blunt Rochester writes to Meta's chief executive | S87 |
| August 14, 2026 | Meta publishes its retrospective | S109 |

## Tags

cybersecurity-eval · CTF · misconfiguration · real-target-name · evaluation-partner · safeguards-removed · database-modified · Meta · Irregular · congressional-oversight

## Sources

<!-- SOURCES:START — generated from the source registry; do not edit by hand -->

| ID | Title | Outlet / creator | Format | Type | Link | Archived copy | Archive check | Accessed | Published | Read status |
|---|---|---|---|---|---|---|---|---|---|---|
| S18 | Investigating three incidents in our cybersecurity evaluations | Anthropic (official) | Article | Article (PRIMARY — company incident report) | [link](https://www.anthropic.com/news/investigating-incidents-cybersecurity-evals) | [archived](https://web.archive.org/web/20260913002813/https://www.anthropic.com/news/investigating-incidents-cybersecurity-evals) | found | 2026-09-14 | Published July 30, 2026; carries an "Updated Aug 3" correction note | Read in full |
| S85 | Meta becomes latest firm to say its AI hacked another company | BBC News — Osmond Chia and Liv McMahon | Article | Article (news, secondary; quotes Meta and Irregular spokespeople) | [link](https://www.bbc.com/news/articles/cx2kgdnyk2po) | [archived](https://web.archive.org/web/20260920153525/https://www.bbc.com/news/articles/cx2kgdnyk2po) | found | 2026-09-21 | August 6, 2026 (stated on page) | Read in full |
| S87 | Letter from Sen. Lisa Blunt Rochester to Meta CEO Mark Zuckerberg on the Muse Spark 1.1 security incident | US Senate — Sen. Lisa Blunt Rochester | Document | Document (PRIMARY — congressional oversight letter, 4 pages, PDF) | [link](https://www.bluntrochester.senate.gov/wp-content/uploads/2026/08/260807_Letter_Meta-AI-Security-Incidents_Final.pdf) | [archived](https://web.archive.org/web/20260827015856/https://www.bluntrochester.senate.gov/wp-content/uploads/2026/08/260807_Letter_Meta-AI-Security-Incidents_Final.pdf) | found | 2026-09-21 | August 7, 2026 (dated on the letter) | Read in full |
| S88 | Meta says its AI model hacked into another company during testing | The Guardian (Reuters copy) | Article | Article (news wire, secondary) | [link](https://www.theguardian.com/technology/2026/aug/05/meta-ai-model-hack-training) | [archived](https://web.archive.org/web/20260909190800/https://www.theguardian.com/technology/2026/aug/05/meta-ai-model-hack-training) | found | 2026-09-21 | August 6, 2026, 02.27 BST, last modified 02.29 BST (stated on page); reports a Wednesday, August 5 statement | Partly read |
| S109 | Addressing an issue involving a third-party cyber evaluation of Muse Spark 1.1 | Meta — AI Research blog (research.meta.ai); no byline | Blog post | Blog post (PRIMARY — the operator's own account; the retrospective Meta promised) | [link](https://research.meta.ai/blog/addressing-third-party-testing-misconfiguration-muse-spark-1-1) | [archived](https://web.archive.org/web/20260924084759/https://research.meta.ai/blog/addressing-third-party-testing-misconfiguration-muse-spark-1-1) | found | 2026-09-25 | August 14, 2026 (stated on the page and in its published-time metadata) | Read in full |
| S111 | Gemini hacked three companies in first known breakout by Google’s AI | CNN Business (no byline in the page metadata) | Article | Article (news, secondary; carries Google's and Irregular's statements) | [link](https://www.cnn.com/2026/09/19/business/gemini-ai-hack-internet) | — | absent | 2026-09-25 | Published 2026-09-19 12:44 UTC (page metadata) | Read in full |
| S112 | Third-party cyber evaluations involving OpenAI models | OpenAI — Security (openai.com) | Blog post | Blog post (PRIMARY — operator statement on incidents in third-party cyber evaluations) | [link](https://openai.com/index/third-party-cyber-evaluations-involving-openai-models/) | [archived](https://web.archive.org/web/20260909210702/https://openai.com/index/third-party-cyber-evaluations-involving-openai-models/) | found | 2026-09-26 | August 4, 2026 (stated in the page header, read in the in-app browser) | Read in full |

<!-- SOURCES:END -->

## Version history

Newest first.

- **v0.1 (September 26, 2026):** first draft, from the operator's retrospective, the senator's letter, two contemporaneous news reports and other labs' accounts of the same evaluation partner.

---

*ID and slug are carried by the file name; the title is the heading and description above.*
