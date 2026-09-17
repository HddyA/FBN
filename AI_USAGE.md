# AI_USAGE

This documents how AI was used to build the NovaLend Scrum Master Ops Kit. It also records where the AI output was generic or wrong for this situation, and how that was caught and fixed.

## 1. Tools used and what for

| Tool | Used for | Not used for |
|---|---|---|
| **Claude (Anthropic, claude.ai)** | Reading the 8 screenshots of the brief. Drafting all six artifacts, the stretch goals and the 22-slide PowerPoint. Drafting this file and the README. | Final decisions on dates, scope and owners. Every number and date was checked against the scenario before it stayed in. |
| **Python / a date check** | Confirming that every date in the plan falls on the weekday it claims (e.g. Thu 1 Oct 2026, Fri 30 Oct 2026). | — |
| *[Add any other tool you actually used, e.g. Copilot in PowerPoint for layout, or Notion AI]* | | |

## 2. Prompts given and what came back

### Prompt 1: generate the kit

> *[Attached: 8 screenshots of the take-home brief — scenario, required artifacts, hard constraints, AI usage requirement, deliverables, stretch goals, assessment criteria]*
>
> "ENSURE TO FOLLOW THE 'How you'll be assessed' ALSO I NEED YOUR ANSWER TO BE REAL AS POSSIBLE AND Prepare your response in MS PowerPoint."

**Why I prompted it this way:** I attached the whole brief instead of summarising it. That way the AI worked from the exact constraints, including the note that generic Scrum text will be marked down. I also pointed it at the assessment table so the output would be organised around what is scored.

**What came back:** a 22-slide `.pptx` containing:

- **6-week plan** — a real 2026 calendar, two 2-week sprints, a 1-week Sprint 3 and a hardening week; submission on 28 Oct with a 2-day buffer.
- **Capacity maths** — deducts Independence Day and a named engineer's leave.
- **Trade-offs** — an explicit protect / defer / cut breakdown (38 / 18 / 5 pts).
- **RAID log** — 13 entries.
- **Retro plan** — exact questions and tactics for dominant and quiet voices.
- **Comms plan** — with a full sample status update.
- **Ceremony redesign** — plus an hour-by-hour day across Lagos and Toronto.
- **Dependency map and escalation** — map, escalation ladder and script.
- **Definition of Done** — tightened for regulator-facing work.
- **Pushback slide** — six expected objections with answers.

**What I had to be careful about in that output:** the AI invented plausible details to make the kit feel real:

- team member names
- last-sprint figures (committed 34/32, delivered 21/19)
- a NovaWallet EM's name
- an InfoSec ticket number
- a CBN report scope (a loan-level extract with reconciliation)

None of these are in the brief. I kept them because they make the artifacts concrete. However, I labelled them as illustrative (slide 2 and README) and logged the report scope as assumption **A1** in the RAID log, so they aren't passed off as facts. In a real role, each would be verified on Day 1.

### Prompt 2: supporting files

> "Can you provide the README, and `AI_USAGE.md`"

**What came back:** `README.md` and a draft of this file. The README maps each artifact to its slides and to the assessment criterion it answers. It also includes the dependency map as Mermaid so it renders in the repo.

### Prompt 3: *[your targeted correction prompt]*

> *[Paste the follow-up prompt you gave after reviewing the deck, e.g. a request to change a date, tighten a status update, or fix something that read as generic.]*

**What came back:** *[Describe the change.]*

## 3. Where AI output was wrong or generic, and how it was caught

### Case 1: the burn-up chart misstated where the buffer is (plan artifact)

**What the AI drafted:** under the burn-up chart on slide 7, the first version of the caption read:

> "The gap between gold and navy lines in W5 is our buffer."

**Why it was wrong for this situation:** in Week 5 the gold line (committed scope, 38 pts) and the navy line (planned done, 38 pts) **meet**. There is no gap between them. The real buffer is between forecast capacity (45.5 pts) and planned done (38 pts), which is 7.5 pts. That buffer is the plan's main defence against the NovaWallet API slipping again. A caption pointing at the wrong lines would have undermined the one number I most need to defend live.

**How it was caught:** by reading the rendered chart against the underlying numbers, instead of trusting the caption.

**Fix:** the caption now reads:

> "At W5 the 7.5-pt gap between forecast capacity and planned done is the buffer."

**Lesson:** AI-written text *about* a chart can drift from the chart's data. Every claim about a visual needs checking against the numbers behind it.

### Case 2: *[your own catch]*

*[Add one correction you made from your own review. For example: a date that didn't match between slides, a RAID owner who shouldn't own that risk, a status-update line pitched at the wrong audience, or wording you would never say out loud in an escalation. Use the same format: what the AI drafted → why it was wrong for this team/deadline/history → how you noticed → what you changed.]*

## 4. Checks applied to every AI draft

These checks target the generic defaults the brief warns about. Each was applied before a slide was accepted.

| Check | What a generic draft tends to do | What this kit does instead |
|---|---|---|
| Does the plan respect the fixed 6-week deadline? | Proposes a standard 2-week cadence ending on deadline day | Shortens Sprint 3 to 1 week, freezes on 23 Oct, submits 28 Oct, keeps a 2-day buffer |
| Is capacity based on evidence? | Sizes sprints from past *commitments* or an ideal velocity | Uses *delivered* velocity (21, 19 pts) and deducts the holiday and approved leave |
| Do the dates exist? | Uses weekday names that don't match the year | Every date checked against the 2026 calendar |
| Does the timezone gap stay constant? | Ignores daylight saving | Confirmed Toronto stays on EDT until 1 Nov, so the 5h gap holds to the deadline |
| Does the contractor actually participate? | Says "contractor catches up async" | Moves every live ceremony into the 14:00–17:00 WAT overlap and walks through a real day |
| Right detail for the right audience? | Sends the same update, story points included, to everyone | Head of Digital Factory gets confidence and exposure; Compliance gets scope, risk and dates; engineering leads get the decision request |
| Could a lead act on the update without a meeting? | "Status: Amber, some risks" | Names who decides, the deadline, costed options and what happens if nobody answers |
| Does every RAID entry have a single owner and a date? | "Team" as owner, no due date | One named owner and date per entry |

## 5. Overall judgment on using AI here

- **What AI did well:** it moved fast. It produced a complete, consistent first version of six artifacts in one pass, and was strong at structure and at drafting realistic wording (the status update and escalation script).
- **Where it needed human judgment:**
  - checking that numbers stay consistent across slides and charts
  - deciding which invented details are acceptable and labelling them
  - making sure every claim is something I can defend under pushback
- **How to treat AI output:** as a first draft from a fast, confident colleague who hasn't met the team. It is useful, but nothing goes in front of stakeholders until it has been checked against the real team, deadline and history.
