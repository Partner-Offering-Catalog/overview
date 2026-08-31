---
title: Authoring an offering
description: The front matter, stage blocks, and timing vocabulary the build validates on every run.
weight: 10
---

An offering page is read in two places: rendered on this site, and rendered by GitHub straight
from the repository. It is therefore ordinary Markdown with a small, fixed structure that the
build checks on every run, so a typo fails the build instead of quietly dropping a stage.

The fastest way to start is to copy
[`template/`](https://github.com/Partner-Offering-Catalog/overview/tree/main/template),
a working skeleton of everything below. It lives outside `content/`, so it is not published as
a page here: it exists only to be copied.

## Where an offering lives

Create a folder under `content/offerings/` and add a `README.md` to it. The folder name is the
URL, and the page joins the navigation, the breadcrumbs, and the overview table automatically —
there is nothing else to wire up.

Keep supporting Markdown next to the `README.md` that links to it. Decks, spreadsheets, images,
and other binaries go in an `assets/` folder inside the offering; `assets/` is published as-is
and is not scanned for pages.

## Front matter

```yaml
---
title: GitHub Copilot Hackathon for Developers
description: One sentence that works as a summary card and as a meta description.
weight: 30
type: In-Person
audience: [Customer developers, Engineering leads]
duration: 1 day on site
level: Intermediate
owner: Partner delivery lead
status: Published
updated: 2026-08-30
tags: [GitHub Copilot, Developer productivity]
---
```

| Field | Purpose |
| --- | --- |
| `title` | The page title, the navigation entry, and the first column of the overview table |
| `description` | Summary card text and the page lede |
| `weight` | Ordering within the catalog; lower sorts first |
| `type` | How the engagement is delivered: `In-Person` or `Virtual` |
| `audience` | Who the engagement is for |
| `duration` | How long the delivery itself takes |
| `level` | Assumed starting experience, shown on this page |
| `owner` | The accountable role for the offering, shown on this page |
| `status` | `Published`, or `Draft` for an offering that is not finished. `Template` also exists and keeps a page out of the overview table, but the skeleton now lives in `template/`, so an offering here should not use it |
| `updated` | The date the offering last changed, shown on this page |
| `tags` | Free-form labels shown under the page header |

Values are flat `key: value` pairs. A value written as a YAML flow sequence, such as
`audience: [Partner developers, Customer developers]`, is parsed as a list; quote an item that
contains a comma.

## Stage blocks

Everything above `## Delivery framework` is the pitch: what the offering is, who it is for, and
what a buyer gets. Everything below the stages is reference material, such as qualification
questions and explicit exclusions.

The stages themselves are `###` headings under a single `## Delivery framework` heading, in
framework order. Declare only the stages the offering actually uses.

```markdown
## Delivery framework

### Engage

- **Timing:** T-90d → T-30d
- **Owner:** Partner account lead
- **Purpose:** Qualify the engagement, then convert interest into a written commitment.

#### Entry criteria

- An identified sponsor who owns a delivery or productivity goal.

#### Activities

- Run the pitch conversation with the sponsor and the engineering lead together.
```

Use these headings exactly. The heading text is the stage name from the
[delivery framework](./framework.md), and it is the vocabulary the shared site template
validates against:

| # | Stage | Heading to use |
| --- | --- | --- |
| 1 | Engage | `### Engage` |
| 2 | Scope | `### Scope` |
| 3 | Prepare | `### Prepare` |
| 4 | Execute | `### Execute` |
| 5 | Wrap | `### Wrap` |

An earlier version of the framework split these five stages into eight, and the longer titles
it used — `Engage & Commit`, `Scope & Design`, `Wrap & Close-out`, and the three stages since
merged away — are rejected rather than accepted as aliases. The build names the stage that
absorbed each one, so a page written against the old framework can be migrated from the error
message.

### Stage fields

Bold-label bullets go directly beneath the stage heading, before any subsection:

| Field | Value |
| --- | --- |
| `**Timing:**` | A timing anchor, from the vocabulary below |
| `**Owner:**` | The one accountable role for this stage in this offering |
| `**Purpose:**` | One or two lines on why the stage exists here |
| `**Status:**` | `Not applicable — <reason>`, for a stage that deliberately does not apply |

### Stage subsections

`####` subsections inside a stage, in this order:

- `Entry criteria`
- `Activities`
- `Outputs`
- `Exit criteria`
- `Resources`

### Timing anchors

A single token or a `from → to` range, built from a fixed vocabulary:

| Token | Meaning |
| --- | --- |
| `T-90d`, `T-30d`, `T-6w` | Before delivery, in days (`d`), weeks (`w`), or months (`m`) |
| `D0` | Delivery day |
| `D+1`, `D+2` | Subsequent delivery days |
| `D+n` | The last delivery day, whenever that is |
| `T+7d`, `T+90d` | After delivery |

### Resources

A `Resources` subsection is a table with exactly these four columns:

```markdown
| Resource | Type | Audience | Link |
| --- | --- | --- | --- |
| Joining instructions | Email template | Participant | [joining-instructions.md](./joining-instructions.md) |
```

`Audience` must be one of `Internal`, `Partner`, `Customer`, `Participant`, or `Public`, so
material that must not be forwarded to a customer is marked as such at the point of use.

Links are ordinary repository-relative links. They are rewritten to published URLs at build
time, but only when the target file exists, so a typo stays visibly broken instead of becoming
a plausible wrong URL.

## Stages that do not apply

Declare the stage and say so, rather than leaving it out:

```markdown
### Scope

- **Status:** Not applicable — the curriculum is fixed and is not tailored per engagement.
```

A reader can then tell the difference between "we thought about this and it does not apply" and
"nobody has written this yet".

## What fails the build

- A `###` heading under `## Delivery framework` that is not one of the stage headings above.
- Stages declared out of framework order, or the same stage declared twice.
- A bold-label bullet that is not `Timing`, `Owner`, `Purpose`, or `Status`.
- A `####` subsection that is not one of the five listed above, or declared twice in one stage.
- A timing token outside the vocabulary above.
- A `Resources` table whose header is not the four columns above, or a row with an unknown
  audience.

Every error in a run is reported at once, so a page can be fixed in a single pass.
