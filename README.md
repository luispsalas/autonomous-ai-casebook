# Autonomous AI Casebook

*In-depth reconstructions of incidents where an AI system's autonomy was central to real-world security harm, built from primary sources.*

> **Status: private draft for review.** The structure and reference pages are in place; entries are being added.

---

## Why this exists

AI systems now take actions on their own: they run tasks, use tools and coordinate with each other. When that goes wrong, public understanding forms quickly and from fragments: broadcasts, posts and commentary, much of which later turns out to be wrong. This casebook reconstructs a small number of incidents carefully, separates what was established from what was alleged, and asks what could have prevented them.

## What this is, and what it isn't

**It is** a set of in-depth, sourced case studies, each revised as investigations continue.

**It isn't** a complete list of AI incidents. For broad coverage, see the [AI Incident Database](https://incidentdatabase.ai/) and the [OECD AI Incidents Monitor](https://oecd.ai/en/incidents); this casebook draws on both.

## What counts as an incident

An incident is included when an AI system was involved, **its autonomy was central to the harm** (it took the harmful action itself, or the harm came about through its autonomous behavior), the consequence was security-relevant and reached something real, and there is enough evidence. **Whether anyone intended it doesn't matter.** Any organization's systems qualify, not just AI labs.

Not included: a person using AI as a tool (for example, AI-written phishing), or attacks where the AI is only the thing stolen (for example, stolen model weights).

→ The full test, with worked examples: [Inclusion criteria](docs/inclusion-criteria.md)

## Coverage is incomplete: read this first

No list of AI incidents is complete, this one included. Public registries record what gets reported; incidents that stay inside a company, are covered only in languages other than English, or happen where few people report on AI are routinely missed. One incident in this casebook went unnoticed for about seven months **inside the company that ran the model**, and surfaced only while that company was preparing material for an outside reviewer. **If an incident isn't here, that is not evidence it didn't happen.**

**Reading beyond English.** To narrow that gap, the casebook also reads reporting in other languages, starting with Mandarin and French. The reason is practical: the people closest to an incident often speak first, and in their own language. When Taiwan's government systems were attacked, its own statement was issued in Mandarin and described human hackers assisted by AI agents, while much English coverage led with the discovering firm's description of a near-autonomous attack. Reading both is what lets an entry show that difference, and some details appeared only in local-language reporting.

**What this doesn't fix.** Reading other languages narrows the gap; it doesn't close it. The tools used to find sources favor English-language, widely indexed sites, and in some countries much security reporting circulates on platforms that search engines don't reach, so finding nothing in a language is weak evidence. Most coverage in other languages repeats English reporting, and is treated as repetition, not as independent confirmation. Quotations stay in their original language. Where the source publishes its own official translation, as Taiwan's government does, the casebook uses it; any other translation is marked as the casebook's own, and dates are recorded as the source gives them: Taiwan's official documents, for example, count years in the Republic of China calendar, where 115 is 2026.

## Where the material comes from

Most cases rest on companies' own disclosures and on independent evaluators' reports. That means coverage leans toward organizations that **choose** to publish. A company with no incidents here may simply be one that hasn't disclosed any, and this casebook cannot tell those two apart.

## How to read an entry

Each entry has a short name and a one-line description, a briefing you can read in under a minute, a timeline that includes how long the incident went unnoticed, the organizations, models and agents involved, what happened (told once technically and once in plain terms), its causes from more than one perspective, recommendations, a Confidence section, corrections, context and open questions.

**Tiers:** *Full* entries rest on at least one primary source; *Provisional* entries rely on secondary sources for now and say so.

→ Every field explained: [Entry schema](docs/schema.md)

## How to read Confidence and sources

Sources are not interchangeable. A company's own disclosure, an independent investigation, a news report and a machine-generated transcript each support different things. Every entry's Confidence section explains what its claims rest on and how they were checked. Speculation is labeled as speculation where it appears. Sources in languages other than English are labeled with their language, and a detail that appears only in one language's press is flagged as single-sourced.

→ Source types, statuses and archiving: [How sources are handled](docs/sources.md)

## Corrections, allegations and myths

Well-known accounts of these incidents are often wrong. This casebook sets official accounts beside what was reported and alleged, attributes each claim, and states errors in its sources openly instead of dropping them quietly. For example, the name of an AI model has circulated as if it were the name of an incident.

## Entries change over time

Many of these incidents are still under investigation. Entries are revised when new primary sources appear, and every revision is recorded and shown in the entry, so you can see how the account changed and why.

## What we don't publish

We don't publish technical detail beyond what the original sources themselves published, and nothing that works as a how-to. We don't republish third-party articles, broadcasts or transcripts; we quote briefly, attribute and link. Organizations affected by an incident are named with attribution to the source that identified them.

## Current entries

| Entry | Tier | Last revised |
|---|---|---|
| [I1 · The Hugging Face Incident](entries/i1-openai-agents-hugging-face-intrusion.md) — *draft for review* | Full | September 16, 2026 |

*Only published entries will be listed here. While the repository is private, entries under review are listed and marked as drafts.*

## Contributing and reporting corrections

Found an error or a better source? [Open an issue](CONTRIBUTING.md) with a link to the source. Primary sources (company disclosures, investigation reports, regulatory filings) carry the most weight. Reports and commentary are welcome too and are recorded as what they are. Pull requests aren't accepted: every change is made after review against the sourcing standard.

## Authorship

*An Authorship Meter declaration describing how this casebook was made, by a human working with AI models, will be linked here once it has been assessed.*

## License

The written content is licensed under **[Creative Commons Attribution 4.0 International (CC BY 4.0)](LICENSE)**: you may share and adapt it, including commercially, as long as you credit the casebook. Any code added to the repository will be licensed under the **MIT License**.

## Related

For explanations of the concepts behind these incidents, see the [Applied AI Concepts wiki](https://github.com/luispsalas/applied-ai-concepts).
