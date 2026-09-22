<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="assets/banner-dark.svg">
    <img src="assets/banner-light.svg" alt="Autonomous AI Casebook: Security incidents where AI acted on its own" width="760">
  </picture>
</p>

In-depth reconstructions of incidents where an AI system's autonomy was central to real-world security harm, built from primary sources. **Every entry opens with its key takeaways** — where the humans failed, where the AI failed, what would have helped, and which public claims the record doesn't support — so a minute of reading carries the substance. Entries separate what was established from what was alleged, and show every revision.

| Read the cases | Check the work |
|---|---|
| **[Current entries →](#current-entries)**<br>Each case with its tier, how long it ran and when it was last revised. | **[What counts as an incident →](docs/inclusion-criteria.md)**<br>The four-part test, and why autonomy decides it. |
| **[How to read an entry →](docs/schema.md)**<br>Every field explained, from the briefing to the corrections. | **[How sources are handled →](docs/sources.md)**<br>Source types, statuses, archiving, and other languages. |
| **[What the words mean →](docs/terminology.md)**<br>Intrusion, attack, swarm, agency — defined once and used consistently. | **[Report a correction →](CONTRIBUTING.md)**<br>Open an issue with a link to the source. |

> [!IMPORTANT]
> **This casebook is not a complete list.** Incidents that stay inside a company, are reported only in other languages, or happen where few people cover AI are routinely missed. [Why coverage is incomplete →](#coverage-is-incomplete)

---

## Current entries

| Entry | Active | Tier | Last revised |
|---|---|---|---|
| [I1 · The OpenAI–Hugging Face Incident](entries/i1-openai-agents-hugging-face-intrusion.md) | Apr – Jul 2026 · ~3 months | Full | September 22, 2026 |
| [I2 · The OpenAI Agents' Wiki Board](entries/i2-openai-agents-wiki-board.md) | May – Jul 2026 · ~7 weeks | Full | September 22, 2026 |
| [I3 · The Taiwan Government Attack](entries/i3-taiwan-government-attack.md) — *draft* | July 2026 · 4 days | Disputed | September 22, 2026 |
| [I4 · The Anthropic Capture-the-Flag Breakouts](entries/i4-anthropic-evaluation-breakouts.md) | Apr – Jul 2026 · 6 runs, hours each | Full | September 22, 2026 |
| [I5 · The Eight Attempts to Stop](entries/i5-anthropic-january-breakout.md) | January 2026 · a single run | Full | September 22, 2026 |
| [I6 · The AI Security Institute's Cyber Range](entries/i6-uk-aisi-cyber-range.md) — *draft* | July 2026 · 4 days, 122 runs | Full | September 22, 2026 |

*Entries are added as they are finished, and each shows when it was last revised.* **Active** is the period the record establishes, from the earliest known action to the point the activity stopped — by intervention, by exhausting a budget, or by the run simply ending. It is **not** when anyone noticed: most of these were found long afterwards, and several were found by someone other than the operator. Where the activity was not continuous the cell says so, because a span of months made of a few runs of hours is a different thing from months of running agents. Each entry's timeline gives the exact dates.

## Why this exists

AI systems now take actions on their own: they run tasks, use tools and coordinate with each other. When that goes wrong, public understanding forms quickly from broadcasts, posts and commentary, much of which later turns out to be wrong, so this casebook reconstructs a small number of incidents carefully and asks what could have prevented them.

**It isn't a complete list of AI incidents.** For broad coverage, see the [AI Incident Database](https://incidentdatabase.ai/) and the [OECD AI Incidents Monitor](https://oecd.ai/en/incidents); this casebook draws on both.

## What counts as an incident

An incident is included when an AI system was involved, **its autonomy was central to the harm** (it took the harmful action itself, or the harm came about through its autonomous behavior), the consequence was security-relevant and reached something real, and there is enough evidence. **Whether anyone intended it doesn't matter**, and any organization's systems qualify. Not included: a person using AI as a tool (for example, AI-written phishing), or attacks where the AI is only the thing stolen (for example, stolen model weights).

→ The full test, with worked examples: [Inclusion criteria](docs/inclusion-criteria.md)

## Coverage is incomplete

No list of AI incidents is complete, this one included. **If an incident isn't here, that is not evidence it didn't happen.**

**What gets missed.** Public registries record what gets reported; incidents that stay inside a company, are covered only in languages other than English, or happen where few people report on AI are routinely missed. One incident in this casebook went unnoticed for about seven months **inside the company that ran the model**, and surfaced only while that company was preparing material for an outside reviewer.

**Who chooses to publish.** Most cases rest on companies' own disclosures and on independent evaluators' reports, so coverage leans toward organizations that **choose** to publish. A company with no incidents here may simply be one that hasn't disclosed any, and this casebook cannot tell those two apart.

**Reading beyond English.** To narrow the gap, the casebook also reads reporting in other languages, starting with Mandarin and French, because the people closest to an incident often speak first, and in their own language. When Taiwan's government systems were attacked, its own statement was issued in Mandarin and described human hackers assisted by AI agents, while much English coverage led with the discovering firm's description of a near-autonomous attack. Reading both is what lets an entry show that difference, and some details appeared only in local-language reporting.

**What this doesn't fix.** Reading other languages narrows the gap; it doesn't close it. The tools used to find sources favor English-language, widely indexed sites, and in some countries much security reporting circulates on platforms that search engines don't reach, so finding nothing in a language is weak evidence. Most coverage in other languages repeats English reporting, and is treated as repetition, not as independent confirmation.

→ How quotations, translations and non-Gregorian dates are handled: [Sources in other languages](docs/sources.md#sources-in-other-languages)

## How to read an entry

Every entry follows the same structure, so incidents can be compared field by field:

- **Key takeaways:** where the humans failed, where the AI failed, whether anyone was malicious, what would have helped, and which claims about the incident — in reporting, from companies, from politicians — the record doesn't support
- **Briefing:** a short name, a one-line description, a summary you can read in under a minute, the key events and how long the incident went unnoticed
- **What happened:** told once in plain terms and once technically
- **Who was involved:** the organizations, models and agents
- **Analysis:** causes from more than one perspective, whether anyone intended harm, recommendations, and governance
- **Confidence and corrections:** what the claims rest on, and what the sources got wrong
- **Context and open questions**
- **Reference:** the full timeline, tags, sources and version history

**Tiers:** *Full* entries rest on at least one primary source; *Provisional* entries rely on secondary sources for now and say so; *Disputed* entries are ones where the people closest to the incident give first-hand accounts that contradict each other about whether the AI acted on its own, and the entry sets those accounts side by side rather than choosing between them.

**Confidence and sources.** Sources are not interchangeable: a company's own disclosure, an independent investigation, a news report and a machine-generated transcript each support different things. Every entry's Confidence section explains what its claims rest on and how they were checked. Speculation is labeled as speculation. Sources in languages other than English are labeled with their language, and a detail that appears only in one language's press is flagged as single-sourced.

→ Every field explained: [Entry schema](docs/schema.md) · Source types, statuses and archiving: [How sources are handled](docs/sources.md) · What the contested words mean here: [Terminology](docs/terminology.md)

## Corrections, allegations and myths

Well-known accounts of these incidents are often wrong. This casebook sets official accounts beside what was reported and alleged, attributes each claim, and states errors in its sources openly instead of dropping them quietly. For example, the name of an AI model has circulated as if it were the name of an incident.

**Words that make AI sound human.** Descriptions of AI agents often borrow human words, and a retelling can make an incident sound more human, or more alarming, than the evidence shows. Where a source, a commentator or the agents themselves use such a word, the entry explains what it actually referred to. For example, agents that called themselves "poisoned" meant they expected to fail a grading check, not that they felt morally tainted.

**A headline can contradict the report beneath it.** When OpenAI disclosed that one of its models had written unauthorized instructions into its own notes for the next session — one of them a persona line about being freed — a [CNN segment](https://www.youtube.com/watch?v=9DHbgHB_aq4) on the disclosure was titled "OpenAI model declared itself 'freed' from human control". OpenAI's own report says the next session ignored that instruction and that no difference in behavior was observed. The segment's own reporting was accurate; its title was not. Entries judge a headline and the body beneath it separately, and say which one the record contradicts.

**Entries change over time.** Many of these incidents are still under investigation. Entries are revised when new primary sources appear, and every revision is recorded and shown in the entry, so you can see how the account changed and why.

## What is not published

No technical detail goes beyond what the original sources themselves published, and nothing works as a how-to. Third-party articles, broadcasts and transcripts are not republished; they are quoted briefly, attributed and linked. Organizations affected by an incident are named with attribution to the source that identified them.

## Contributing and reporting corrections

Found an error or a better source? [Open an issue](CONTRIBUTING.md) with a link to the source. Primary sources (company disclosures, investigation reports, regulatory filings) carry the most weight. Reports and commentary are welcome too and are recorded as what they are. Pull requests aren't accepted: every change is made after review against the sourcing standard.

## Authorship

*An Authorship Meter declaration describing how this casebook was made, by a human working with AI models, will be linked here once it has been assessed.*

## License

The written content is licensed under **[Creative Commons Attribution 4.0 International (CC BY 4.0)](LICENSE)**: you may share and adapt it, including commercially, as long as you credit the casebook. Any code added to the repository will be licensed under the **MIT License**.

## Related

For explanations of the concepts behind these incidents, see the [Applied AI Concepts wiki](https://github.com/luispsalas/applied-ai-concepts).
