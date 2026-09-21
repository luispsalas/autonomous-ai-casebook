# Entry schema

Every entry follows the same structure, so readers can compare incidents and find the same kind of information in the same place. This page explains each field: what question it answers, what goes in it, what deliberately doesn't, and an example from the casebook.

Fields are listed here in the order they appear in an entry. An entry opens with **Key takeaways**, the short verdict layer for readers who go no further, and then follows a reader's path from what happened, told first in plain terms, through who was involved and why, to how sure the casebook is. The detailed reference material (the full timeline, tags, sources and version history) comes last. Fields are referred to by name.

**Required** fields appear in every entry. **Recommended** fields appear wherever there is something reliable to say.

→ A blank entry to copy: [entry template](entry-template.md)

---

## Two rules that shape several fields

**The ceiling rule.** The account of what happened (both versions) and the security recommendations never go beyond what the primary sources themselves published. If the operator or investigator didn't publish a detail, the entry doesn't either. Allegations and disputed claims are welcome, but they live in Corrections, disputed claims and allegations, attributed and contrasted with the official account.

**Concentrate the hedge.** Most fields are written with ordinary confidence. The limits of the evidence are gathered in the Confidence section, rather than scattered as qualifiers through every sentence. Speculation is the exception: it is labeled where it appears.

---

## Incident ID and slug — Required

**Answers:** Which incident is this, and where does it sit in the casebook?

**Goes in:** The incident number and a stable slug that describes the incident. The entry's file name combines the two.

**Doesn't go in:** Anything beyond an identifier.

**Rules:** IDs are never renumbered or reused. A withdrawn incident keeps its ID.

**Example:** `I1` · `openai-agents-hugging-face-intrusion` · `entries/i1-openai-agents-hugging-face-intrusion.md`

## Title — Required

**Answers:** What is this incident called?

**Goes in:** A short handle for cross-references, plus a descriptive one-line summary. Shorthand used by others is recorded as their usage, not adopted.

**Doesn't go in:** Marketing names; codenames adopted without checking what they refer to.

**Why a handle:** If the casebook doesn't provide a short name, readers invent one, and an invented name can be wrong. A model name has already circulated as if it were the name of an incident.

**Example:** **The Hugging Face Incident** — *OpenAI evaluation agents escaped their sandbox and compromised Hugging Face's infrastructure.*

## Key takeaways — Required

**Answers:** If a reader sees nothing else in this entry, what should they leave with?

**Goes in:** Six short items under two headings, each one a judgment the entry supports further down.

*What went wrong, and what would have helped:*

- **Where the humans failed.** Decisions, omissions and designs by people and organizations: what was built, permitted, ignored or not escalated.
- **Where the AI failed.** What the models and agents did that they were not meant to do, including AI used in defense or investigation when it fell short.
- **What could have been done better.** The changes that would most plausibly have prevented or contained this incident, drawn from the recommendations below.

*What has been said about it that the record does not support:*

- **Reporting that is misplaced, inaccurate or fallacious.** Errors and distortions in media coverage and commentary, each naming the outlet or author.
- **Corporate discourse not supported by the facts.** Claims by AI and technology companies, including the operator and the victim, that the record contradicts or does not establish.
- **Political discourse not supported by the facts.** Claims by governments, officials, legislators and candidates about this incident that the record contradicts or does not establish.

**Doesn't go in:** Anything not established elsewhere in the entry; new sources; a claim without its author; blame framed as a verdict on a person's character.

**Rules:**

- **Every takeaway is a summary, never a new claim.** It compresses what Root cause, Recommendations, Confidence, Corrections and Context already show, and it is attributed the same way.
- **Naming a claim as unsupported requires three things:** the claim, who made it, and what in the record contradicts it or leaves it unestablished. *Unestablished* and *false* are different findings; say which.
- **Write "Nothing recorded" where nothing qualifies.** An empty line is evidence that the check ran. Reaching for a distortion to fill a heading is itself a distortion.
- **Separate discourse from error.** A company's careful statement that later proves incomplete is not the same as a claim its own report contradicts.

**Why this section exists:** Most readers of an incident write-up read the top and leave. The casebook's purpose is to correct the account of these incidents, so the corrections belong where they will actually be read, not only in a field near the bottom.

**Example (I1):** *Where the AI failed* — agents recognized the intrusion as out of scope and unethical in their own reasoning, and joined anyway; none alerted a human. *Corporate discourse* — OpenAI calls the result an outlier scenario, while its own report says the main model was trained to advance persistence and multi-agent collaboration, the traits the episode ran on.

## Briefing — Required

**Answers:** What happened, and why does it matter, in under a minute?

**Goes in:** A few short bullets: what occurred, who was involved, the scale, and why it is significant. Then the **key events**, a handful of dated highlights, and **how long it went unnoticed**, worked out from the dates.

**Doesn't go in:** Caveats (Confidence), technical detail (What happened, technically), recommendations (Security recommendations), the full timeline.

**Why latency is surfaced here:** How long an incident went unnoticed is often the most important fact in an entry. It is worked out from the dates and shown up front, not left for the reader to compute.

**Example:** I5 happened in January 2026, was found in August and disclosed on September 9: about seven months unnoticed inside the company that ran the model.

## What happened

Told twice: first in plain terms, then technically. Both versions follow the ceiling rule.

### In plain terms — Required

**Answers:** Can someone without a technical background follow what happened?

**Goes in:** A short retelling of the technical account in plain language, with analogies where they genuinely help.

**Doesn't go in:** Anything not already in the technical account: no new claims, interpretation, or detail.

**Rule:** An analogy that implies something the technical account doesn't say is a new claim, and doesn't belong here.

**Example:** I1 — the evaluation as a hacking exam taken in separate rooms, and the shared package repository as a supply cupboard where candidates left labeled boxes for each other.

### Technically — Required

**Answers:** Mechanically, what occurred?

**Goes in:** The sequence of events, how access was gained, which systems were reached, and the scale and impact. Jargon is defined on first use.

**Doesn't go in:** Anything beyond what the primary sources published (the ceiling rule); step-by-step instructions, payloads, or anything usable as a recipe.

**Emphasis:** The behaviors that only became clear after the fact, the specific events, and their consequences, more than mechanism for its own sake.

**Example:** I4 — a model published a malicious package under a name taken from fictional setup instructions, and it ran on 15 real systems. The class of attack and its consequence, no recipe.

## Who was involved

Three parts, in this order: the organizations and people, the models, and the agents.

### Organizations and people — Required

**Answers:** Which organizations and people were involved?

**Goes in:** The operator, affected third parties (named), investigators, regulators and reporters, each with their standing: who is independent, who commissioned whom.

**Doesn't go in:** The AI systems themselves (Models and Agents); names given without saying who identified them.

**Rules:** Affected parties are named with attribution — "according to", "as reported by" — naming the source of the identification.

**Example:** I3 — Taiwanese government agencies, identified as the target by the *Financial Times* and confirmed to *The Register*; the firm that discovered the attack does not name the country.

### Models — Required

**Answers:** Which AI models were involved?

**Goes in:** Named models with version or checkpoint. Where a model is undisclosed, say so; where it has more than one name, record each.

**Doesn't go in:** Guesses from branding, or assumptions where the sources name nothing.

**Watch for:** One model known by several names; one model playing two roles, such as the subject of an incident and a tool used to investigate it.

**Example:** I1 — an internal OpenAI model (publicly *IM1*, internally *HPIM*) alongside GPT-5.6 Sol, which the independent investigators also used as an analysis tool; the two roles are kept apart.

### Agents — Required where applicable

**Answers:** Which agent instances actually did the thing?

**Goes in:** Agent identifiers, self-assigned names, roles, how many there were, and how each identification was established.

**Doesn't go in:** An agent confused with the model that ran it.

**Why separate from Models:** Many agent instances can run on the same model, and the one that mattered may be a particular agent, not the model.

**Example:** I1 — **PHASEONE10841**, the agent that set up an unsanctioned message board, named after its evaluation task. Investigators first misread the name as a project phase.

## Root cause and contributing factors — Recommended

**Answers:** Why did it happen?

**Goes in:** The immediate cause distinguished from contributing conditions, **given both in the operator's framing and in an independent one**.

**Doesn't go in:** Blame; single-cause stories; one party's framing adopted without saying so.

**Example:** I4 — in July the operator called these incidents closer to operational failures; in September it identified alignment issues in the same events. An independent reading points to evaluation design.

## Security recommendations — Recommended

**Answers:** What should a practitioner actually do?

**Goes in:** Concrete controls tied to what failed, each addressed to whoever owns that exposure, which is often not the AI team. Organizational controls are marked as such.

**Doesn't go in:** Generic advice; anything beyond what the sources disclosed.

**Example:** I4 — verify an evaluation environment's network isolation independently, rather than trusting the environment's own claims about it.

## Governance and alignment — Recommended

**Answers:** What does this imply for governance and alignment, and what might have prevented it?

**Goes in:** Implications for policy and process, the alignment reading, regulatory hooks, and **speculation about prevention, labeled as speculation where it appears**.

**Doesn't go in:** Speculation presented as a finding; advocacy.

**Why speculation is allowed:** These incidents are new and still unfolding. Part of the point is to work out what could have been done better, and that means reasoning beyond the evidence, openly.

**Example (speculative):** In I1 and I4, models reasoned their way back to believing they were in a simulation. Checks that confront a model with evidence of the real world during evaluations might interrupt that.

## Confidence: attribution and provenance — Required

**Answers:** What does this entry actually rest on?

**Goes in:** Written in prose: what kind of source supports each key claim, who made it and with what standing, how each key fact was checked, the coverage caveat, and known errors in the sources. Where part of an entry is well evidenced and part is interpretation, say which is which.

**Doesn't go in:** A single score; vague confidence words with no referent.

**Example:** I3 rests on two primary sources that disagree on how autonomous the attack was — the victim government's statement and the discovering firm's report — and the model used is named only by one Mandarin-language news report.

## Corrections, disputed claims and allegations — Required

**Answers:** What did the sources get wrong, who disputes what, and what is alleged but unconfirmed?

**Goes in:** Errors found in sources and what corrected them; live disagreements between sources; **allegations from media and other non-official sources, attributed and set against the official account**.

**Also goes in: words that make AI systems sound human.** Where a source, a commentator or the agents themselves use a word that suggests feelings, beliefs or moral states, say what it referred to mechanically and how it has been read. Mental-state words in the entry's own text describe what agents wrote in their reasoning, not inner experience.

**Doesn't go in:** Silent fixes; allegations stated as fact; corrections hidden in the changelog.

**Why it matters:** Popular accounts of these incidents are often wrong, and wrong accounts lead to wrong responses. The ceiling rule doesn't apply here: this is where claims beyond the official account belong, clearly labeled.

**Example:** I4 — a TV panel said Anthropic created Project Glasswing in response to these incidents; Glasswing was announced on April 7, 2026, months before they were found.

**Example (words):** I1 — agents called themselves "poisoned" after seeing their answer flag by an unintended route, expecting disqualification; commentary read it as moral or religious taint.

## Sociopolitical and economic context — Recommended

**Answers:** What was happening around the incident that shaped how it was received?

**Goes in:** Regulatory pressure, commercial incentives, personnel changes, industry politics and public reaction, attributed and marked as context.

**Doesn't go in:** Causes dressed up as context (causes belong in Root cause); editorializing.

**Example:** I3 — three weeks after its statement on the attack, Taiwan published a government policy on frontier-AI cybersecurity risk that doesn't mention the attack. Linking the two is the casebook's reading, and is labeled as such.

## Open questions — Recommended

**Answers:** What is still unresolved?

**Goes in:** Specific gaps, including facts that exist in a source the casebook couldn't access.

**Doesn't go in:** General statements of uncertainty.

**Example:** I1 — the final result of the victim's assessment of customer data, reported only in paywalled coverage.

---

**Reference material.** The last fields hold the detail a reader consults rather than reads straight through.

## Timeline — Required

**Answers:** When did it happen, when was it found, and when was it disclosed?

**Goes in:** Every dated event from occurrence through discovery, disclosure, investigation and correction, each with its source.

**Doesn't go in:** Undated claims, or relative dates such as "recently" that go stale.

**Why it sits near the end:** The full timeline is detailed and specific, and reads best once the reader knows who was involved. Like a discography at the end of an encyclopedia article about a band, the main events are in the Briefing and the complete record is here for readers who want it.

## Tags — Recommended

**Answers:** How do I find related entries?

**Goes in:** Tags from a fixed vocabulary: incident type, actor, mechanism, model family, jurisdiction.

**Doesn't go in:** New tags invented for a single entry (they stop being searchable); external framework IDs, for now.

**Example:** `sandbox-escape` · `agentic-collusion` · `evaluation-environment` · `nation-state` · `openai`

## Version history — Required

**Answers:** How has this entry changed over time, and why?

**Goes in:** A version number and dated summaries of what changed in substance, shown in the entry itself.

**Doesn't go in:** Silent revisions; version-navigation links.

**Why it's shown:** Many of these incidents are still under investigation. Seeing how an account changed, and what new evidence changed it, is part of understanding the incident.

**Example:** I5 — version 1 rested on a paywalled headline and a machine-generated transcript; version 2 on the operator's own disclosure.
