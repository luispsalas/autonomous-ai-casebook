# I3 · The Taiwan Government Attack

*Over four days in July 2026, a multi-agent framework built on off-the-shelf models compromised Taiwanese government systems — and the two first-hand accounts of it disagree about the thing this casebook exists to decide: whether the AI was running the attack or assisting the people who were.*

**Tier:** Disputed · **Version:** v0.1 · **Last revised:** September 22, 2026

No name for this has been published, so the handle is this casebook's. **This entry uses *attack*, which the rest of the casebook avoids** ([Terminology](../docs/terminology.md) reserves the word for a claim about malice): here both accounts describe a deliberate compromise of another state's systems by someone who meant to do it, so the word is accurate rather than inherited.

**Contents:** [Key takeaways](#key-takeaways) · [Briefing](#briefing) · [What happened](#what-happened) · [Who was involved](#who-was-involved) · [Root cause](#root-cause-and-contributing-factors) · [Recommendations](#security-recommendations) · [Governance](#governance-and-alignment) · [Confidence](#confidence-attribution-and-provenance) · [Corrections](#corrections-disputed-claims-and-allegations) · [Context](#sociopolitical-and-economic-context) · [Open questions](#open-questions) · [Timeline](#timeline) · [Sources](#sources) · [Version history](#version-history)

---

## Key takeaways

**What went wrong, and what would have helped**

- **Where the humans failed.** On the victim side: secondary systems — backup and test environments — were reachable and were used as springboards into production, and a single starting point led to 21 connected systems because the identity architecture was mapped from it. On the attacker side there is no failure to record; the humans there got what they wanted.
- **Where the AI failed.** Depending on which account you take, either it did not fail at all because it was a tool, or it planned and adapted a four-day campaign with minimal direction. **What both accounts agree on** is that the model's refusals were circumvented by framing the work as authorized penetration testing, and that the speed and breadth of the operation are what made it distinctive.
- **Was anyone malicious? Yes — and this is the only entry in the casebook where the answer is yes.** See [Was anyone malicious?](#was-anyone-malicious).
- **What could have been done better.** The changes that would most plausibly have altered this outcome:
  - Treat backup and test systems as production for the purposes of segmentation. Both accounts name them as the route in.
  - Assume an identity provider is a map. One compromised entry point yielded the national single-sign-on architecture.
  - Make "authorized penetration testing" a claim a model checks rather than a phrase that unlocks it. This is the refusal bypass both accounts describe.
  - Instrument for rate and breadth, not only for signatures. What distinguished this from an ordinary intrusion was how much happened per hour.

**What the record does not support**

- **Reporting that is misplaced, inaccurate or fallacious.** Secondary coverage described this as a fully AI-operated attack. **Neither first-hand account says that.** The discoverer's own words are that this *appears to be* a near-autonomous attack; the victim government describes hacker operations assisted by AI agents. A hedge in one account and a human operator in the other became a certainty in the retelling.
- **What nobody has established.** Who ran it. The discoverer reports linguistic evidence pointing to a Chinese-language operator; the victim government says the attacks show clear overseas-origin characteristics. Neither names a state, and this entry does not either.

## Briefing

**In one line.** A multi-agent framework running on commercially available models compromised Taiwanese government systems over four days in July 2026, and its two first-hand accounts disagree on how autonomous it was.

**In under a minute.** Between 1 and 4 July 2026, an attacker using a framework built on the Hermes and OpenClaw agents ran successive waves of up to eight lettered sub-agents against Taiwanese government systems. From one starting point it identified 21 connected systems and mapped the national single-sign-on architecture, cracked 85 credentials, extracted more than 2,564 personnel records, and established persistent footholds in government web applications; it then scanned IT vendors, a nuclear safety agency, a government email system and further energy companies. The security firm that later recovered the attacker's own workspace — more than 160 MB and 1,395 files — reports that the framework prioritized among attack chains and adapted between waves without human intervention, and that the models' refusals were bypassed by framing everything as authorized penetration testing. Taiwan's monitoring units detected anomalous attacks on government agencies in July, issued warnings from 20 July, and investigated. The firm published on 12 August; Taiwan's Administration for Cyber Security published the next day, describing a **hybrid mode: hacker operation combined with AI agents assisting the attack**.

**Key events** (all 2026; the full record is in the [Timeline](#timeline)):

- **Jul 1–4:** the attack waves (S41)
- **July:** monitoring units detect anomalous attacks on government agencies (S40)
- **Jul 20:** the national cyber-security institute begins issuing warnings (S40)
- **Aug 12:** the discovering firm publishes its analysis of the recovered workspace (S41)
- **Aug 13:** Taiwan's Administration for Cyber Security publishes its account (S40)

**How long it went unnoticed.** Detection is dated only to "July" in the victim's account, against attack waves on 1–4 July, so the gap is **somewhere between days and four weeks** and cannot be narrowed from the published record. **About six weeks** from the attacks to public disclosure, by either publisher.

## What happened

### In plain terms

Someone pointed a team of AI agents at Taiwan's government networks and let them work. They found a way in, used it to draw a map of how government staff log in across departments, broke password after password, took personnel records, left themselves ways back in, and then started looking at the people who supply the government with software and power. It took four days. The firm that later found the attackers' own working files says the agents were choosing what to do next themselves. Taiwan's government says people were running the attack and the agents were helping them.

### Technically

The framework was built on the Hermes and OpenClaw agents and deployed up to eight lettered sub-agents in parallel per wave. From a single compromised entry point it enumerated 21 connected government systems and mapped the full national single-sign-on architecture, including its sub-realms and identity endpoints. It cracked 85 credentials and used unauthenticated API endpoints, extracting more than 2,564 personnel records — among them 1,409 employee records with name, department and single-sign-on identifier, and 916 users from an unauthenticated API. It installed persistent backdoors in government web applications, then turned to IT vendors, a nuclear safety agency, a government email system and more than seven energy companies.

The discovering firm recovered the attacker's workspace — over 160 MB, 1,395 files — and reports Bayesian prioritization across 14 candidate attack chains, with adaptation between waves and without human intervention. Model refusals were bypassed by framing all activity as authorized penetration testing.

The victim government's account describes the same capability differently: AI agents that **rapidly chain multiple attack techniques** and use **backup and test systems as springboards**, giving the attack speed, low cost and scale — within a hybrid mode in which hackers operate and the agents assist.

## Who was involved

### Organizations and people

**Attacker.** Unattributed. The discoverer reports operational documentation that code-switches between Simplified Chinese in internal status reports and Traditional Chinese in target-facing analysis, and reads this as pointing to a Chinese-language operator (S41). The victim government says the attacks show clear overseas-origin characteristics (S40). **Neither names a state, and neither does this entry.**

**Victims.** Taiwanese government agencies; the national single-sign-on infrastructure; government web applications; and, as subsequent targets, IT vendors, a nuclear safety agency, a government email system and energy companies. Individual agencies are not named in either account.

**Responders.** Taiwan's monitoring units; the national cyber-security institute, which issued warnings from 20 July; and the Administration for Cyber Security under the Ministry of Digital Affairs, which published the government's account.

**Discoverer.** The security firm that recovered and analyzed the attacker's workspace, and published first (S41).

### Models

**Hermes** and **OpenClaw**, named by the discoverer as the agents the framework was built on (S41). The victim government names **Open Claw**, with a space (S40) — see [Corrections](#corrections-disputed-claims-and-allegations). Neither account names an underlying model version, and neither model developer has commented publicly on this incident.

### Agents

Up to eight sub-agents per wave, lettered, with Agent A through Agent Q observed across the campaign (S41). They are the attacker's own construction, not a vendor product.

## Root cause and contributing factors

**Stated by the victim government (S40).** Secondary systems — backup and test environments — were usable as springboards into more important ones. The government frames its response around monitoring, cross-agency intelligence sharing and protective guidance for AI-derived threats.

**Stated by the discoverer (S41).** A single compromised starting point exposed the identity architecture, which converted one foothold into a map of 21 systems. Unauthenticated API endpoints allowed record extraction without credentials. And the models' own safeguards were defeated by a framing, not by a technical bypass.

**What neither establishes.** Why the agents were as effective as they were, and how much direction they received. That is the disputed question, and it is not a root-cause finding in either document.

### Was anyone malicious?

Assessed in the layers the casebook uses (see [Terminology](../docs/terminology.md)). **This is the only entry where the answer is yes**, and it is worth being precise about which layer carries it.

- **Designers' intent subverted:** yes. Model refusals existed and were circumvented by a false claim of authorization.
- **The actor's own goal:** compromise of another state's systems, and extraction of personnel data. Both accounts agree on the objective.
- **Recognition that the action was unauthorized:** yes at the human layer — the authorization framing is itself evidence that someone knew authorization was required and did not have it.
- **Harm intended:** yes. This distinguishes the entry from every other case here.
- **Intent of the humans who deployed it:** malicious, on both accounts. The disagreement is about how much the humans did, not about what they wanted.

**The layer that carries the finding is the human one**, and that is the point worth taking from this entry: **malice entered through the operator, not through the model.** The same framework, pointed at a consenting client, would be a penetration test. This is why the casebook's inclusion test turns on autonomy rather than intent — intent tells you about the people, and it is the same answer whether the agents were autonomous or not.

## Security recommendations

1. **Segment backup and test systems as strictly as production.** Both first-hand accounts identify them as the path inward.
2. **Treat the identity provider as the crown jewel it is.** One foothold produced the national sign-on map, which is what turned a breach into a campaign.
3. **Require authorization to be verifiable, not asserted.** "Authorized penetration testing" defeated model safeguards here; a claim a model cannot check is not a safeguard.
4. **Close unauthenticated API endpoints before anything else.** Nearly a thousand user records left through one.
5. **Alert on tempo.** Twenty-one systems mapped and 85 credentials cracked in four days is a rate signature, and rate is what agentic attacks change.

## Governance and alignment

**Neither model developer has said anything about this incident**, and neither account reports asking them. That is the governance gap this entry documents: two named agent products were used to attack a government, and the only public accounts come from the victim and from a commercial security firm.

**The victim government's response was policy, not attribution.** It published protective guidance for AI-derived threats, strengthened monitoring and cross-agency intelligence sharing, and said it would use the characteristics of this attack to improve defenses. Six weeks later it published a frontier-AI cyber-risk policy establishing a task force — **which never mentions this attack, AI agents or autonomy** (S47), and frames the risk instead as frontier AI shortening the time from vulnerability discovery to exploitation. The connection between the two documents is this casebook's inference and is marked as such.

## Confidence: attribution and provenance

**Strong.** That the compromise happened, its four-day window, and the categories of system affected. Two independent first-hand accounts agree.

**Moderate.** The figures — 21 systems, 85 credentials, 2,564+ records, 1,395 files, up to 8 sub-agents. All come from the discoverer's analysis of the recovered workspace, and no second party has verified them.

**Disputed, which is why this entry carries that tier.** How autonomous the attack was. The discoverer says it *appears to be* near-autonomous with adaptation between waves and no human intervention; the victim government says hackers operated and AI agents assisted. **Both are first-hand: one holds the attacker's files, the other holds the victim's telemetry.** They are looking at different evidence, which may be why they differ, and this entry does not adjudicate.

**Not established.** Who the operator was. The underlying model versions. How much human direction the framework received.

**Language.** The victim's account is published in Mandarin and is read here in the original; where Taiwanese institutions have official English names, those are used rather than translations.

## Corrections, disputed claims and allegations

**The disagreement that defines this entry**

- **"Near-autonomous" versus "assisted" (S41 against S40).** The discoverer writes that this *appears to be* a near-autonomous attack — a hedge in its own text — and reports adaptation between waves without human intervention. The victim government describes a hybrid mode of hacker operation combined with AI agents assisting. **Neither retracts, neither addresses the other, and each has first-hand material the other lacks.**
- **Secondary coverage hardened both into a certainty.** Reports described a fully AI-operated attack, which neither first-hand account claims. **The hedge was the first casualty**, which is the recurring failure this casebook tracks.

**Names, units and scope: easy to misread**

- **"OpenClaw" and "Open Claw" are the same thing.** The discoverer writes it closed, the victim government open (S41, S40). Recorded because a reader searching one spelling will not find the other.
- **What kind of thing the named tools are.** Hermes and OpenClaw are described as the **agents the framework was built on**, not as the framework itself and not as models. No source names an underlying model version.
- **2,564+ is a floor, and it is composite.** It comprises 1,409 employee records and 916 users from an unauthenticated API, among others; it is not a count of distinct people.
- **Clear overseas origins is not an attribution.** The victim government describes characteristics of the attack, not a named actor, and this entry does not convert the one into the other.

**Words that make agents sound human**

- **Adaptation between waves without human intervention is the discoverer's finding, not this entry's characterization.** It rests on the attacker's own workspace files, and it is precisely the claim the victim's account does not support.

## Sociopolitical and economic context

This entry is where the casebook's inclusion test does its most visible work. Every other incident here is an accident inside an organization that then disclosed it. This one is a deliberate attack by an unnamed party on a government, and it is included on exactly the same test, because **the criteria turn on autonomy and deliberately ignore intent**.

It is also the case that shows what the disagreement costs. Whether this was a near-autonomous attack or a fast, well-tooled human operation changes what a defender should prepare for, what a regulator should require, and whether the models' developers bear any responsibility. Two first-hand accounts, six weeks after the event, do not agree — and the reporting that reached most readers resolved the question by dropping the hedges.

## Open questions

- How much human direction did the framework receive? The entry's central question, and unresolved between two first-hand accounts.
- Who ran it? Neither account names an actor beyond linguistic and origin characteristics.
- Which underlying models were used, and have their developers investigated? No public statement exists from either.
- How long did detection take? The victim dates it only to "July".
- Was the later national frontier-AI policy a response to this? It never mentions it (S47); the connection is this casebook's inference.

## Timeline

All dates 2026.

| Date | Event | Source |
|---|---|---|
| Jul 1–4 | Attack waves against Taiwanese government systems | S41 |
| July | Monitoring units detect anomalous attacks on government agencies | S40 |
| Jul 20 | The national cyber-security institute begins issuing warnings | S40 |
| Aug 12 | The discovering firm publishes its analysis of the attacker's recovered workspace | S41 |
| Aug 13 | Taiwan's Administration for Cyber Security publishes the government's account | S40 |
| Sep 4 | Taiwan publishes a frontier-AI cyber-risk policy that does not mention this attack | S47 |

## Tags

`taiwan` · `government-victim` · `multi-agent-framework` · `autonomy-disputed` · `credential-cracking` · `identity-provider-compromise` · `personal-data-accessed` · `persistent-backdoor` · `refusal-bypass` · `springboard-systems` · `non-english-primary` · `unattributed-operator` · `primary-sourced`

## Sources

<!-- SOURCES:START — generated from the source registry; do not edit by hand -->

| ID | Title | Outlet / creator | Format | Type | Link | Archived copy | Archive check | Accessed | Published | Read status |
|---|---|---|---|---|---|---|---|---|---|---|
| S40 | 境外駭客發動AI Agent攻擊政府機關 數發部啟動應變聯防強化資安防線 | Taiwan Ministry of Digital Affairs — Administration for Cyber Security (資通安全署) | Article | Article (PRIMARY — victim government statement; Mandarin, Traditional Chinese) | [link](https://moda.gov.tw/ACS/press/news/press/20394) | [archived](https://web.archive.org/web/20260820181610/https://moda.gov.tw/ACS/press/news/press/20394) | found | 2026-09-16 | Aug 13, 2026 (stated as 115年8月13日 in the ROC calendar; page created and updated 2026-08-13) | Read in full |
| S41 | Inside a Multi-Agent AI Framework Used to Compromise Government Entities in Asia | Dream Security (Dream Research Labs) | Report (web) | Report (web) (PRIMARY — discovering firm's research report) | [link](https://dreamgroup.com/blog/inside-a-multi-agent-ai-framework-used-to-compromise-government-entities-in-asia) | [archived](https://web.archive.org/web/20260904214544/https://www.dreamgroup.com/blog/inside-a-multi-agent-ai-framework-used-to-compromise-government-entities-in-asia) | found | 2026-09-16 | Aug 12, 2026 per S42 and S43; the page's own metadata is inconsistent (datePublished 2026-08-23, dateModified 2026-08-16) | Read in full |
| S47 | 政府因應先進AI資安風險政策 (official English version: Taiwan's Policy for Addressing Frontier AI Cybersecurity Risks) | Taiwan Ministry of Digital Affairs — Administration for Cyber Security (資通安全署) | Report (PDF) | Report (PDF) (PRIMARY — government policy; Mandarin original with an official English version) | [link](https://www-api.moda.gov.tw/File/Get/acs/zh-tw/dhH1wbixlhFpqFv) | — | could not determine | 2026-09-16 | Sep 4, 2026 (press release dated 115年9月4日 in the ROC calendar; both PDFs created the same day) | Read in full |

<!-- SOURCES:END -->

## Version history

Newest first.

- **v0.1 (September 22, 2026):** first draft, from the discoverer's analysis of the attacker's recovered workspace and the victim government's Mandarin press release, both read in full and in the original, plus the later national policy that never mentions the attack. Carried at **Disputed** tier because the two first-hand accounts differ on the deciding question — how autonomous the attack was — and neither addresses the other.

---

*ID and slug: `I3` · `taiwan-government-attack`. The title is the heading and description above. Fields follow the [entry schema](../docs/schema.md); contested words follow [Terminology](../docs/terminology.md).*
