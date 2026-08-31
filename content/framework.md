---
title: Delivery framework
description: The five stages every offering is described against, from first conversation to realized value.
weight: 2
---

An offering is not a deck. It is a sequence of commitments that starts weeks before delivery
day and finishes weeks after it, and most failed engagements fail in the gaps between those
commitments rather than in the room on the day.

This framework names those gaps. Every offering in the catalog is described against the same
five stages so that a reader can compare two offerings, spot what an offering is missing, and
know who owns what and when.

## The stages

| # | Stage | Default anchor | Core | Purpose |
| --- | --- | --- | --- | --- |
| 1 | Engage | `T-90d → T-30d` | Core | Position the offering with the people who can fund and staff it, qualify the engagement out early if it does not fit, and turn the interest that survives into a written joint commitment: named participants, locked dates, and target outcomes with baselines. |
| 2 | Scope | `T-30d → T-21d` | Optional | Tailor the agenda, challenges, and scenarios to the committed outcomes. Skip for fixed-curriculum delivery. |
| 3 | Prepare | `T-30d → T-7d` | Core | Run participant readiness and environment readiness as two parallel tracks with different owners and different lead times. |
| 4 | Execute | `T-7d → D+n` | Core | Prove the environment works by using it, take an explicit go/no-go decision while there is still time to act on it, then deliver the engagement and capture evidence as it happens. |
| 5 | Wrap | `D0 → T+90d` | Core | Capture outcomes, demos, and feedback while participants are still in the room, deprovision the environment, then track the commitments until the value shows up in the team's normal work. |

Four stages are **core**: an offering that omits one is usually missing something rather than
deliberately skipping it. **Scope** is optional and genuinely does not apply to every offering —
it is real work for a hackathon and meaningless for fixed-curriculum training.

## Why five stages

Each stage is one clock with one accountable owner. The stages below were merged because
splitting them produced halves that nobody could own on their own:

- **Engage** carries positioning, qualification, and the commitment that follows. The
  qualification questions and the outcome charter are settled with the same sponsor in the same
  set of conversations, so separating them only creates a handover that nobody performs.
- **Execute** carries the dry run and the go/no-go decision as well as the delivery days.
  Readiness is where most delivery failures are still catchable, but the check belongs to the
  person running the days rather than to a stage of its own that closes before they start.
- **Wrap** carries close-out and value realization. Close-out has a hard deadline measured in
  hours: outcomes, demos, and feedback have to be captured while the participants are still in
  the room, and the environment has to be deprovisioned before it becomes a cost and a security
  liability. Value realization runs for the next quarter. Both work from the same commitment
  list and the same owner, so they are one stage with a long tail rather than two stages.

## Timing anchors

Every stage carries a timing anchor relative to delivery day, so an offering communicates
lead time rather than just sequence. Anchors use a fixed vocabulary:

| Token | Meaning |
| --- | --- |
| `T-90d`, `T-30d`, `T-6w` | Before delivery, in days (`d`), weeks (`w`), or months (`m`) |
| `D0` | Delivery day |
| `D+1`, `D+2` | Subsequent delivery days |
| `D+n` | The last delivery day, whenever that is |
| `T+7d`, `T+90d` | After delivery |

A stage may use a single token (`D0`) or a range (`T-30d → T-7d`). The build rejects anything
outside this vocabulary, so anchors stay comparable across offerings.

## What is deliberately not a stage

Roles and RACI, risks, compliance and legal (NDA, data handling, credit terms), the cost and
funding model, and accessibility and language are all cross-cutting. They apply to several
stages at once, so they belong in an offering's header or in a stage's own fields, not as
stages of their own. A "compliance stage" would only ever be a place where compliance is
forgotten for the other four.

## Stage content

Each stage declares the same shape, and every field is optional:

| Field | Purpose |
| --- | --- |
| Timing | The anchor, from the vocabulary above |
| Owner | The one accountable role for the stage |
| Purpose | One or two lines on why the stage exists for this offering |
| Entry criteria | What must be true before the stage starts |
| Activities | The work itself |
| Outputs | What the stage produces |
| Exit criteria | The definition of done, and the gate into the next stage |
| Resources | Decks, docs, templates, and repositories, each tagged with its audience |

Resources are audience-tagged (`Internal`, `Partner`, `Customer`, `Participant`, `Public`) so
that material which must not be forwarded to a customer is visibly marked as such at the point
of use, rather than in a convention that a delivery lead has to remember.

An offering declares only the stages it uses. A stage that genuinely does not apply should
still be declared, marked `Not applicable`, and given a reason: a reader can then tell the
difference between "we thought about this and it does not apply" and "nobody has written this
yet". See [authoring an offering](./offerings/authoring.md) for the exact syntax.
