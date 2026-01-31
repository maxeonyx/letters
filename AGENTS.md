# Letters to NZ Parliament - AI Safety

This project sends personalized letters (with donations) to New Zealand MPs expressing concern about AI safety and the need for multilateral coordination.

**If you're an AI assistant starting fresh, read this file first, then `docs/PLAN.md`.**

## Project Goal

Send letters to ~120 NZ MPs that:
1. Express *extreme concern* (but not dramatic) about AI's impact on humanity's future
2. Urge prioritization of multilateral coordination on AI safety
3. Include a donation to ensure the letter gets read
4. Provide concrete, personalized action points where possible

## Key Design Decisions

- **Non-partisan**: Target individual MPs, not parties. This should inform cross-party consensus.
- **Target tangentially-involved MPs**: Not people who are already deep in AI policy, but people who have touched on it or related tech issues.
- **Donation is key**: The donation ensures attention. Physical letter is optional; email is fine if donation is handled separately.

## Directory Structure

```
letters/
├── AGENTS.md              # You are here
├── README.md              # Human-readable overview
├── data/
│   ├── mps.json           # Master list of all MPs (source of truth)
│   └── research/          # Per-MP research files
│       └── {mp-slug}.md   # One file per MP
├── letters/
│   ├── _template.md       # Letter template
│   └── drafts/            # Per-MP letter drafts
├── scripts/
│   └── research-worker.md # Instructions for research agents
└── docs/
    ├── PLAN.md            # Full project plan and context
    ├── DONATION-RULES.md  # NZ electoral donation research
    └── PHASE-2-IDEAS.md   # Post-letters action ideas
```

## Information Priority (for research)

**Tier 1 - Required to send:**
- Name
- Contact method (email or physical address)
- Donation method (or fallback: cash in envelope)

**Tier 2 - Needed for personalization:**
- Party, Electorate
- Select committee memberships
- AI involvement level (none / tangential / deep)

**Tier 3 - Nice to have:**
- Voting history on conscience votes
- Detailed background on tech positions

## Research Approach

1. **Phase A**: Bulk-scrape parliament.nz for all MPs' basic info → `data/mps.json`
2. **Phase B**: Parallel agents do per-MP deep research (donation method, AI involvement)

See `scripts/research-worker.md` for agent instructions.

## For Research Agents

If you've been assigned to research a specific MP:
1. Read `scripts/research-worker.md` for your exact task
2. Write your findings to `data/research/{mp-slug}.md`
3. Follow the template exactly
4. Do NOT modify `mps.json` or other MPs' files

## Current Status

- [ ] Phase A: Bulk data collection
- [ ] Phase B: Per-MP research (0/120)
- [ ] Letter drafting
- [ ] Sending
