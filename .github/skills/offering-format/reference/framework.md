# The delivery framework

Five stages, four of them core. An offering declares only the ones it uses, but the ones it
declares always appear in this order, so a reader meets the same spine every time.

The stage list is a closed vocabulary. The titles below are exact, and they are single words:
an earlier framework split these five into eight, and those longer titles are rejected rather
than accepted as aliases.

Default anchors are a starting point, not a rule. Each stage's `Timing` field belongs to the
offering, because a shared default is an anchor nobody chose.

---

## 1. Engage — `T-90d → T-30d` (core)

Position the offering with the people who can fund and staff it, qualify the engagement
**out** early if it does not fit, and turn the interest that survives into a joint commitment:
named participants, locked dates, and target outcomes with baselines.

This stage carries a gate that is easy to omit: a real business problem and a named sponsor.
An engagement that should have stopped here usually fails at Prepare instead, after the cost
has been incurred. Qualification and commitment are one stage because they are settled with
the same sponsor in the same set of conversations; splitting them only creates a handover that
nobody performs.

The test of the second half is whether someone could later check whether the engagement
delivered what was promised. If the outcomes and their baselines are not written down, it
cannot.

Good content: the pitch, the qualification questions, the explicit disqualifiers, the outcome
charter, the participant roster, the agreed dates.

## 2. Scope — `T-30d → T-21d` (optional)

Tailor the agenda, challenges, and scenarios to the outcomes committed in stage 1.

Distinct from logistics, and genuinely irrelevant for fixed-curriculum training — mark it
`Not applicable` with that reason rather than deleting it, so the decision is visible.

Good content: challenge selection, archetype or scenario picks, the tailored agenda.

## 3. Prepare — `T-30d → T-7d` (core)

Two parallel tracks with different owners and different lead times:

- **Participant readiness** — comms, pre-reads, prerequisites, skilling.
- **Environment readiness** — golden tickets, subscriptions, quota and capacity, RBAC,
  model deployments, network access.

Quota and capacity requests for AI workloads are a `T-30d` item, not a `T-7d` item.
Collapsing both tracks into one undifferentiated block is what makes them get started late.

Good content: the joining instructions, the environment readiness checklist, who owns each.

## 4. Execute — `T-7d → D+n` (core)

A dry run on the environment participants will **actually** use and an explicit go/no-go
decision while there is still time to fix what it finds, then the delivery days themselves,
with evidence of progress captured as it happens rather than reconstructed afterwards.

Most delivery failures are catchable at the dry run. It sits here rather than in a stage of
its own because the check belongs to the person running the days, not to a stage that closes
before they start. Skipping it is a choice worth recording.

Good content: the dry-run script, the go/no-go criteria, the fallback plan, the run-of-show,
facilitator notes, the daily rhythm, how evidence is captured.

## 5. Wrap — `D0 → T+90d` (core)

One stage on two clocks. Close-out has a hard deadline measured in hours: outcomes and demos
captured **while people are still in the room**, feedback collected, and the environment
deprovisioned. Value realization then runs for the next quarter: commitments tracked, next
steps progressed, consumption or opportunity movement recorded — plus the internal
retrospective that feeds fixes back into this catalog.

Deprovisioning is a cost and security obligation. An offering that leaves it implicit leaves
subscriptions running and access granted.

Both halves work from the same commitment list and the same owner, so they are one stage with
a long tail rather than two. Without the retro loop the offerings never mature, which is why
this stage is core rather than optional.

Good content: the demo capture format, the survey, the deprovisioning checklist, the
commitment tracker, the 30/60/90 checkpoints, the retro template.

---

## Retired stage titles

The framework was previously eight stages. Their titles are not accepted as headings, but the
validator names the stage that absorbed each one, so a page written against the old framework
can be migrated from the error message:

| Retired title | Now part of |
| --- | --- |
| Discover & Qualify | 1. Engage |
| Engage & Commit | 1. Engage |
| Scope & Design | 2. Scope |
| Readiness / Go–No-Go | 4. Execute |
| Wrap & Close-out | 5. Wrap |
| Follow-up & Value realization | 5. Wrap |

---

## What is deliberately not a stage

Roles and RACI, risks, compliance and legal (NDA, data handling, credit terms), cost and
funding model, accessibility and language. These are cross-cutting: they belong in the
offering's front matter or inside the individual stages, not as another box on the timeline.
