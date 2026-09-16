# Entry schema

Every entry follows the same structure, so readers can compare incidents and find the same kind of information in the same place. This page explains each field: what question it answers, what goes in it, what deliberately doesn't, and an example from the casebook.

Fields are numbered 1 to 17, with field 8 split into **8a** and **8b**. The split kept the other numbers unchanged, so references to a field by number stay valid.

**Required** fields appear in every entry. **Recommended** fields appear wherever there is something reliable to say.

→ A blank entry to copy: [entry template](entry-template.md)

---

## Two rules that shape several fields

**The ceiling rule.** The technical account (fields 8a, 8b and 10) never goes beyond what the primary sources themselves published. If the operator or investigator didn't publish a detail, the entry doesn't either. Allegations and disputed claims are welcome, but they live in field 13, attributed and contrasted with the official account.

**Concentrate the hedge.** Most fields are written with ordinary confidence. The limits of the evidence are gathered in field 12 (Confidence), rather than scattered as qualifiers through every sentence. Speculation is the exception: it is labeled where it appears.

---

## 1. Incident ID and slug — Required

**Answers:** Which incident is this, and where does it sit in the casebook?

**Goes in:** The incident number and a stable slug that describes the incident. The entry's file name combines the two.

**Doesn't go in:** Anything beyond an identifier.

**Rules:** IDs are never renumbered or reused. A withdrawn incident keeps its ID.

**Example:** `I1` · `openai-agents-hugging-face-intrusion` · `entries/i1-openai-agents-hugging-face-intrusion.md`

## 2. Title — Required

**Answers:** What is this incident called?

**Goes in:** A short handle for cross-references, plus a descriptive one-line summary. Shorthand used by others is recorded as their usage, not adopted.

**Doesn't go in:** Marketing names; codenames adopted without checking what they refer to.

**Why a handle:** If the casebook doesn't provide a short name, readers invent one, and an invented name can be wrong. A model name has already circulated as if it were the name of an incident.

**Example:** **The Hugging Face Incident** — *OpenAI evaluation agents escaped their sandbox and compromised Hugging Face's infrastructure.*

## 3. Briefing — Required

**Answers:** What happened, and why does it matter, in under a minute?

**Goes in:** A few sentences: what occurred, who was involved, the scale, and why it is significant.

**Doesn't go in:** Caveats (field 12), technical detail (field 8a), recommendations (field 10).

## 4. Timeline — Required

**Answers:** When did it happen, when was it found, and when was it disclosed?

**Goes in:** Dated events from occurrence through discovery, disclosure, investigation and correction, with **how long it went unnoticed shown prominently**.

**Doesn't go in:** Undated claims, or relative dates such as "recently" that go stale.

**Why latency is surfaced:** How long an incident went unnoticed is often the most important fact in an entry. It is worked out from the dates and shown, not left for the reader to compute.

**Example:** I5 happened in January 2026, was found in August and disclosed on September 9: about seven months unnoticed inside the company that ran the model.

## 5. Involved parties — Required

**Answers:** Which organizations and people were involved?

**Goes in:** The operator, affected third parties (named), investigators, regulators and reporters, each with their standing: who is independent, who commissioned whom.

**Doesn't go in:** The AI systems themselves (fields 6 and 7); names given without saying who identified them.

**Rules:** Affected parties are named with attribution — "according to", "as reported by" — naming the source of the identification.

**Example:** I3 — Taiwanese government agencies, identified as the target by the *Financial Times* and confirmed to *The Register*; the firm that discovered the attack does not name the country.

## 6. Model(s) involved — Required

**Answers:** Which AI models were involved?

**Goes in:** Named models with version or checkpoint. Where a model is undisclosed, say so; where it has more than one name, record each.

**Doesn't go in:** Guesses from branding, or assumptions where the sources name nothing.

**Watch for:** One model known by several names; one model playing two roles, such as the subject of an incident and a tool used to investigate it.

**Example:** I1 — an internal OpenAI model (publicly *IM1*, internally *HPIM*) alongside GPT-5.6 Sol, which the independent investigators also used as an analysis tool; the two roles are kept apart.

## 7. Agent(s) involved — Required where applicable

**Answers:** Which agent instances actually did the thing?

**Goes in:** Agent identifiers, self-assigned names, roles, how many there were, and how each identification was established.

**Doesn't go in:** An agent confused with the model that ran it.

**Why separate from field 6:** Many agent instances can run on the same model, and the one that mattered may be a particular agent, not the model.

**Example:** I1 — **PHASEONE10841**, the agent that set up an unsanctioned message board, named after its evaluation task. Investigators first misread the name as a project phase.

## 8a. What happened, technically — Required

**Answers:** Mechanically, what occurred?

**Goes in:** The sequence of events, how access was gained, which systems were reached, and the scale and impact. Jargon is defined on first use.

**Doesn't go in:** Anything beyond what the primary sources published (the ceiling rule); step-by-step instructions, payloads, or anything usable as a recipe.

**Emphasis:** The behaviors that only became clear after the fact, the specific events, and their consequences, more than mechanism for its own sake.

**Example:** I4 — a model published a malicious package under a name taken from fictional setup instructions, and it ran on 15 real systems. The class of attack and its consequence, no recipe.

## 8b. What happened, in plain terms — Required

**Answers:** Can someone without a technical background follow what happened?

**Goes in:** A short retelling of 8a in plain language, with analogies where they genuinely help.

**Doesn't go in:** Anything not already in 8a: no new claims, interpretation, or detail.

**Rule:** An analogy that implies something 8a doesn't say is a new claim, and doesn't belong here.

**Example:** I1 — the evaluation as a hacking exam taken in separate rooms, and the shared package repository as a supply cupboard where candidates left labeled boxes for each other.

## 9. Root cause and contributing factors — Recommended

**Answers:** Why did it happen?

**Goes in:** The immediate cause distinguished from contributing conditions, **given both in the operator's framing and in an independent one**.

**Doesn't go in:** Blame; single-cause stories; one party's framing adopted without saying so.

**Example:** I4 — in July the operator called these incidents closer to operational failures; in September it identified alignment issues in the same events. An independent reading points to evaluation design.

## 10. Security recommendations — Recommended

**Answers:** What should a practitioner actually do?

**Goes in:** Concrete controls tied to what failed, each addressed to whoever owns that exposure, which is often not the AI team. Organizational controls are marked as such.

**Doesn't go in:** Generic advice; anything beyond what the sources disclosed.

**Example:** I4 — verify an evaluation environment's network isolation independently, rather than trusting the environment's own claims about it.

## 11. Governance and alignment — Recommended

**Answers:** What does this imply for governance and alignment, and what might have prevented it?

**Goes in:** Implications for policy and process, the alignment reading, regulatory hooks, and **speculation about prevention, labeled as speculation where it appears**.

**Doesn't go in:** Speculation presented as a finding; advocacy.

**Why speculation is allowed:** These incidents are new and still unfolding. Part of the point is to work out what could have been done better, and that means reasoning beyond the evidence, openly.

**Example (speculative):** In I1 and I4, models reasoned their way back to believing they were in a simulation. Checks that confront a model with evidence of the real world during evaluations might interrupt that.

## 12. Confidence: attribution and provenance — Required

**Answers:** What does this entry actually rest on?

**Goes in:** Written in prose: what kind of source supports each key claim, who made it and with what standing, how each key fact was checked, the coverage caveat, and known errors in the sources. Where part of an entry is well evidenced and part is interpretation, say which is which.

**Doesn't go in:** A single score; vague confidence words with no referent.

**Example:** I3 rests on two primary sources that disagree on how autonomous the attack was — the victim government's statement and the discovering firm's report — and the model used is named only by one Mandarin-language news report.

## 13. Corrections, disputed claims and allegations — Required

**Answers:** What did the sources get wrong, who disputes what, and what is alleged but unconfirmed?

**Goes in:** Errors found in sources and what corrected them; live disagreements between sources; **allegations from media and other non-official sources, attributed and set against the official account**.

**Doesn't go in:** Silent fixes; allegations stated as fact; corrections hidden in the changelog.

**Why it matters:** Popular accounts of these incidents are often wrong, and wrong accounts lead to wrong responses. The ceiling rule doesn't apply here: this is where claims beyond the official account belong, clearly labeled.

**Example:** I4 — a TV panel said Anthropic created Project Glasswing in response to these incidents; Glasswing was announced on April 7, 2026, months before they were found.

## 14. Sociopolitical and economic context — Recommended

**Answers:** What was happening around the incident that shaped how it was received?

**Goes in:** Regulatory pressure, commercial incentives, personnel changes, industry politics and public reaction, attributed and marked as context.

**Doesn't go in:** Causes dressed up as context (causes belong in field 9); editorializing.

**Example:** I3 — three weeks after its statement on the attack, Taiwan published a government policy on frontier-AI cybersecurity risk that doesn't mention the attack. Linking the two is the casebook's reading, and is labeled as such.

## 15. Open questions — Recommended

**Answers:** What is still unresolved?

**Goes in:** Specific gaps, including facts that exist in a source the casebook couldn't access.

**Doesn't go in:** General statements of uncertainty.

**Example:** I1 — the final result of the victim's assessment of customer data, reported only in paywalled coverage.

## 16. Tags — Recommended

**Answers:** How do I find related entries?

**Goes in:** Tags from a fixed vocabulary: incident type, actor, mechanism, model family, jurisdiction.

**Doesn't go in:** New tags invented for a single entry (they stop being searchable); external framework IDs, for now.

**Example:** `sandbox-escape` · `agentic-collusion` · `evaluation-environment` · `nation-state` · `openai`

## 17. Entry version and changelog — Required

**Answers:** How has this entry changed over time, and why?

**Goes in:** A version number and dated summaries of what changed in substance, shown in the entry itself.

**Doesn't go in:** Silent revisions; version-navigation links.

**Why it's shown:** Many of these incidents are still under investigation. Seeing how an account changed, and what new evidence changed it, is part of understanding the incident.

**Example:** I5 — version 1 rested on a paywalled headline and a machine-generated transcript; version 2 on the operator's own disclosure.
