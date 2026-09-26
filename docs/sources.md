# How sources are handled

Every entry rests on sources, and they don't all carry the same weight. This page explains how sources are classified, what each entry's source table tells you, and how the casebook keeps a record of what it actually read.

---

## Kinds of source

| Kind | Examples | Supports |
|---|---|---|
| **Primary** | The operator's or developer's disclosure; an independent investigation's report; a victim's statement; a regulatory filing | The core account of what happened |
| **Reporting** | News coverage that adds facts of its own, attributed to named sources | Detail, reactions, and claims the primary sources don't make |
| **Commentary** | Analysis, blog posts, community discussion | How the incident was understood, and allegations, always attributed |
| **Tertiary** | Encyclopedias, aggregators | Finding other sources; rarely cited for a fact |
| **Transcript** | A transcript of a broadcast or talk, including machine-generated captions | Leads to check. Machine captions are reliable for the gist and unreliable for names, so they are never quoted |

Being primary doesn't make a source right. Operators can understate what went wrong, investigators can misread evidence, and victims and discoverers can disagree. Where primary sources conflict, the entry shows both.

## What each entry's source table shows

Each source has an ID (for example `S41`) that stays the same everywhere it is cited. Entry source tables include these columns:

| Column | Meaning |
|---|---|
| **ID** | The source's permanent identifier |
| **Title** | As published. Where a title can't be shown exactly, the table says why |
| **Outlet / creator** | Who published it, and the author where one is named |
| **Format** | Article, blog post, report (PDF or web), video, podcast, transcript, forum post, web page, or encyclopedia |
| **Type** | What the source is: primary, news, commentary, and its language if not English |
| **Link** | Where it was published |
| **Archived copy** | A Wayback Machine capture, where one exists |
| **Archive check** | Whether an archived copy was found (see below) |
| **Accessed** | When the casebook last read or checked it |
| **Published** | The source's own date, as the source gives it |
| **Read status** | How much of it was actually read (see below) |

### Read status

| Status | Meaning |
|---|---|
| **Read in full** | The full text was read: from the page itself, its underlying source, an archived copy, or a copy supplied by someone with access |
| **Partly read** | Only part was read, such as the opening, or only the page's metadata behind a paywall |
| **Via transcript** | Known only through a transcript; the original was not watched or read |
| **Existence confirmed** | Title, author or date confirmed at the source, content not read |
| **Not retrieved** | Could not be fetched. The entry says why |
| **Retired** | The ID no longer refers to an active source; the entry points to its replacement |

A source marked anything other than *read in full* can still be cited, but only for what was actually read.

## Archiving

Web pages change and disappear, and company incident pages are revised as investigations continue. For each source, the casebook looks for a copy in the Wayback Machine and records one of three results:

- **Found** — a capture exists and is linked. It is the capture closest to when the casebook read the source, which is not always the exact version read.

- **Absent** — the lookup completed and found nothing.

- **Could not determine** — the lookup didn't finish (a rate limit, a refusal, an error). This is recorded separately from *absent*, because it isn't an answer.

## Identifiers never change meaning

A source ID refers to one source, permanently. If a source is replaced, the replacement gets a new ID and the old one is marked *retired*, so anything that cited the old ID still means what it meant.

## Sources in other languages

- **Quotations stay in their original language.** Where the publisher offers an official translation, the casebook uses it; any other translation is marked as the casebook's own.

- **Dates are recorded as the source gives them**, with the Gregorian date alongside. Taiwan's official documents, for example, count years in the Republic of China calendar, where 115 is 2026.

- **Repetition is not confirmation.** Much coverage in other languages restates English reporting and is recorded as such.

- **Single-language details are flagged.** A fact that appears only in one language's press is marked as single-sourced.

- **Absence is weak evidence.** Search tools favor English-language, widely indexed sites, so finding nothing in a language says little.
