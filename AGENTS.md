# Letters to NZ Parliament - AI

This project is about preparing personalized letters to New Zealand MPs about AI, with a focus on international coordination, New Zealand's long-term interests, and keeping the future human.

**If you're an AI assistant starting fresh, read this file first.**

## Current Task

The repo has been rebaselined around the current direction in `VISION.md`.

The active work is now the letter package itself:

- keep the strategy consistent with `VISION.md`
- keep the main letter prose unwritten by the assistant unless Max explicitly asks otherwise
- treat `letters/_template.md` as a commented scaffold, not finished copy

## Read First

Read these files in this order:

1. `VISION.md` for the current direction, constraints, and reviewed wording from Max
2. `docs/PLAN.md` for the staged plan from here to sending
3. `letters/_template.md` when working on the template structure or comments

## MP Count

**There are 123 MPs in NZ Parliament.** Don't get confused by the data structure:

- `data/mps.json` has 121 object entries + 2 string entries = 123 total
- The 2 strings are special cases (Greg O'Connor, Scott Willis) with personal connections to Max
- `data/research/` has 121 JSON files (the 2 special cases are in `data/SPECIAL-NOTES.md`)

## Project Goal

Prepare letters to all 123 NZ MPs that:

1. express serious concern about AI's impact on humanity's future without slipping into unnecessary alarmism
2. urge attention to international coordination and AI control measures
3. frame the issue in New Zealand terms, including the importance of keeping the future human
4. point toward other people, groups, events, and resources in New Zealand rather than leaning on Max's authority
5. can later be personalized where useful without straining weak connections

## Key Design Decisions

- **Non-partisan:** target individual MPs, not parties
- **Serious and concise:** the letters should be readable by staffers and MPs under time pressure
- **Concerned-citizen voice:** Max is not trying to win by status
- **Template first:** the assistant may help with comments, structure, and later MP-specific dynamic sections, but should not draft the main letter prose unless asked

## Directory Structure

```text
letters/
├── AGENTS.md              # You are here
├── README.md              # Human-facing project overview
├── VISION.md              # Current direction and reviewed requirements
├── data/
│   ├── mps.json           # Master list of all MPs (source of truth, read-only)
│   ├── SPECIAL-NOTES.md   # Greg O'Connor & Scott Willis (personal connections)
│   └── research/          # Per-MP research JSON files
│       ├── _schema.json   # Research file schema
│       ├── _template.md   # Research note template
│       └── {mp-slug}.json # One file per MP (121 total)
├── docs/
│   ├── CRITICAL-REVIEW.md # Current risks and gaps in the project
│   ├── PHASE-2-IDEAS.md   # Later ideas after the letter campaign
│   ├── PLAN.md            # Full project plan and context
│   ├── index.html         # Placeholder support/resources page
│   └── why.html           # Placeholder public explainer page
├── letters/
│   └── _template.md       # Commented letter scaffold
└── scripts/
    ├── research-worker.md # Follow-up research guidance if more MP research is needed
    └── orchestration.md   # Follow-up research coordination notes
```

## Research Status

The main MP research pass is complete.

What the research data is for now:

- postal addresses
- AI involvement / tech-adjacent evidence
- personalization notes

If more research is needed, use the research files to enrich those areas rather than reopening the old project framing.

## Special Cases

Two MPs in `mps.json` are **strings instead of objects**. This is intentional.

- **Greg O'Connor** - Max's actual MP
- **Scott Willis** - Family friend

See `data/SPECIAL-NOTES.md` for their data. Scripts that assume every entry is a normal object should fail on these entries.

## Phase Status

- [x] Phase A: Bulk data collection
- [x] Phase B: Per-MP research
- [x] Phase C: Repo rebaseline around the new direction
- [ ] Phase D: Commented template and support package
- [ ] Phase E: Drafting, testing, printing, and sending
