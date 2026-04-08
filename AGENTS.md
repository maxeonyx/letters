# Letters to NZ Parliament - AI Safety

This project sends personalized letters (with donations) to New Zealand MPs expressing concern about AI safety and the need for multilateral coordination.

**If you're an AI assistant starting fresh, read this file first.**

## Current Task: Phase C Letter Drafting

We're refining the letter template section by section.

## MP Count

**There are 123 MPs in NZ Parliament.** Don't get confused by the data structure:
- `data/mps.json` has 121 object entries + 2 string entries = 123 total
- The 2 strings are special cases (Greg O'Connor, Scott Willis) with personal connections to Max
- `data/research/` has 121 JSON files (the 2 special cases are in `data/SPECIAL-NOTES.md`)

---

## Research Phase (Complete) 

### How to Run Research

Use the `researcher` subagent via the Task tool. Launch **5-10 in parallel** for speed:

```
Task(subagent_type="researcher", description="Research MPs batch 1", prompt="
Research these MPs:
1. slug-one (Full Name)
2. slug-two (Full Name)
...

Find postal addresses first for ALL MPs, then donation methods.
Update data/research/{slug}.json immediately after each finding.
")
```

### Check Progress

```bash
node -e "
const fs = require('fs');
const files = fs.readdirSync('data/research').filter(f => f.endsWith('.json') && !f.startsWith('_'));
const stats = {pending: 0, 'in-progress': 0, done: 0, partial: 0};
for (const f of files) {
  const d = JSON.parse(fs.readFileSync('data/research/' + f, 'utf8'));
  stats[d.researchStatus] = (stats[d.researchStatus] || 0) + 1;
}
console.log(stats);
"
```

### Get Next Batch

```bash
node -e "
const fs = require('fs');
const files = fs.readdirSync('data/research').filter(f => f.endsWith('.json') && !f.startsWith('_'));
const pending = [];
for (const f of files) {
  const d = JSON.parse(fs.readFileSync('data/research/' + f, 'utf8'));
  if (d.researchStatus === 'pending') pending.push(d.slug + ' (' + d.name + ')');
}
console.log('Next 10:', pending.slice(0, 10).join('\\n'));
"
```

---

## Project Goal

Send letters to all 123 NZ MPs that:
1. Express *extreme concern* (but not dramatic) about AI's impact on humanity's future
2. Urge prioritization of multilateral coordination on AI safety
3. Include a donation to ensure the letter gets read
4. Provide concrete, personalized action points where possible

## Key Design Decisions

- **Non-partisan**: Target individual MPs, not parties. This should inform cross-party consensus.
- **Target tangentially-involved MPs**: Not people already deep in AI policy, but people who have touched on related tech issues.
- **Donation is key**: The donation ensures attention. Physical letter is optional; email is fine if donation is handled separately.

## Directory Structure

```
letters/
├── AGENTS.md              # You are here
├── data/
│   ├── mps.json           # Master list of all MPs (source of truth, read-only)
│   ├── SPECIAL-NOTES.md   # Greg O'Connor & Scott Willis (personal connections)
│   └── research/          # Per-MP research JSON files
│       ├── _schema.json   # JSON schema for research files
│       └── {mp-slug}.json # One file per MP (121 total)
├── scripts/
│   ├── research-worker.md # Detailed instructions for researcher agent
│   └── orchestration.md   # How to coordinate parallel research
├── letters/
│   └── _template.md       # Letter template
└── docs/
    ├── PLAN.md            # Full project plan and context
    ├── DONATION-RULES.md  # NZ electoral donation research (important!)
    └── CRITICAL-REVIEW.md # Known issues and risks
```

## Research Priority Order

For each MP, gather in this order (breadth-first across all MPs):

1. **Postal address** - Electorate office or parliament address
2. **Donation method** - Bank account, donation page, or confirm none exists
3. **AI involvement** - Quick scan for tech/AI statements (none/tangential/deep)
4. **Personalization notes** - Useful hooks for the letter

## Special Cases

Two MPs in `mps.json` are **strings instead of objects** - this is intentional. They have personal connections to Max:
- **Greg O'Connor** - Max's actual MP
- **Scott Willis** - Family friend

See `data/SPECIAL-NOTES.md` for their data. Scripts will crash on these entries, which is the point.

## Phase Status

- [x] Phase A: Bulk data collection (123 MPs scraped from parliament.nz)
- [x] Phase B: Per-MP research (121/121 done)
- [ ] Phase C: Letter drafting (current task — see header)
- [ ] Sending
