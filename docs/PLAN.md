# Project Plan

This document captures the full context and decisions for this project. It was developed through conversation between Max and an AI assistant.

## Background

Max is increasingly worried about AI. Living in New Zealand, there's only so much one person can do, but at minimum: send letters to NZ politicians expressing concern.

### Core Message (from Max)

The letter should convey:

1. The future of humanity is contingent on the details of the development & deployment of AI as a technology.
2. Anything at all that *you* can do to ensure multilateral coordination for AI safety and control, is something that should be at the top of your priorities as a member of parliament.
3. Ideally, some concrete information and action points for the MP in question.

### Tone

- **Extremely concerned** - this is not casual
- **Not dramatic** - no apocalyptic language, just serious
- **Short** - respect the reader's time

### The Donation Strategy

> "The donation hopefully ensures it gets read."

The donation is the key mechanism for ensuring attention. Physical letters are not required - email works if the donation is handled separately. However, physical letters make cash donations operationally easy.

**NZ donation rules:** Donating directly to individual MPs (not parties) is inconsistently possible. Some electorate MPs have public donation info, most don't. This requires per-MP research. See `docs/DONATION-RULES.md` for full legal research.

**Donor identity:** Max will use his real name on donations. This avoids anonymous-donation complications and is simpler. Anonymity would only be considered if there were a strong reason (e.g., if the act were somehow illegal but still worth doing).

## Target Selection

> "My goal is to focus on members that are *tangentially* involved - not people who have engaged with this a lot, but ideally people who have engaged with this a little."

Rationale: People already deep in AI policy have their views. People with *some* exposure might be more receptive to new framing.

> "I do *not* want to operate this at the level of parties... this should inform a cross-party consensus on New Zealand's position on this issue in multilateral forums."

## Data Requirements

For each of 123 MPs, we need:

### Tier 1 - Required to Act
- Name
- Contact method (email OR physical address)  
- Donation method (if available) OR fallback plan

### Tier 2 - Personalization
- Party, Electorate
- Select committee memberships
- AI involvement level (none / tangential / deep)

### Tier 3 - Nice to Have
- Voting history on conscience votes
- Detailed background

## Research Approach

### Phase A: Bulk Data Collection (1 agent, ~5 mins)

Scrape parliament.nz for all 123 MPs' basic info:
- https://www.parliament.nz/en/mps-and-wards/current-mps/

This gives us names, parties, electorates, contact info, select committees.

Output: `data/mps.json`

### Phase B: Per-MP Deep Research (parallel agents)

For each MP, research:
- Donation method (check their personal/electorate website)
- AI involvement (search hansard, news articles)
- Anything relevant for personalizing the letter

**Parallelism:** 3 agents at a time  
**Initial test:** 5 MPs to validate the approach

### Sources for Research

**Basic info:**
- https://www.parliament.nz/en/mps-and-wards/current-mps/

**AI involvement:**
- Parliament Hansard search
- News: stuff.co.nz, nzherald.co.nz, rnz.co.nz
- MP's own website/social media

**Donation info:**
- MP's personal/electorate website
- Electoral Commission rules

## Automation System

### Constraints
- Max has limited AI credits (GitHub Copilot premium requests)
- Credits reset daily
- Need bounded parallelism (3 agents)
- Agents must not interfere (separate directories, single browser tab each)
- Must handle rate limits gracefully

### Worker Setup
- Each worker is assigned ONE MP
- Works in isolation (own browser tab, own output file)
- Clear success/failure criteria
- Timeout after N minutes
- Writes findings to `data/research/{mp-slug}.json`

See `scripts/research-worker.md` for exact instructions.

## Phase 2: After Letters

Ideas for further action:

> - Gathering signatures in Wellington for an existing grassroots campaign. Presenting this to parliament?
> - Creating short YouTube videos on the fundamental arguments (especially from a micro-economic perspective, which is something I find extremely lacking in AI safety discourse)
> - Anything else that is within my power & energy.

See `docs/PHASE-2-IDEAS.md` for details.

## Technical Notes

### Credit Management
- GitHub Copilot premium requests: ~300/day (resets daily)
- Test with 5 MPs first to validate approach
- 3 parallel agents as good balance of speed vs. rate limits

### Avoiding Conflicts
- Each agent gets its own MP assignment
- Agents write to separate files (`data/research/{mp-slug}.json`)
- Agents do NOT modify `mps.json` (only read from it)
- Each agent opens only ONE browser tab

### Model Selection Notes

**GPT-5.2** is extremely capable for research and analysis, but has a recognizable, somewhat unpleasant writing style. When using GPT-5.2:
- Use it for research, planning, and critical review
- Do NOT leave its prose in final artifacts (letters, committed docs)
- Have another model (e.g., `grok-code-fast-1`) rewrite any user-facing text

### Running Agents via CLI

To run a research agent from the command line:
```bash
opencode run -m github-copilot-max/gpt-5.2 "Your prompt here"
```

Options:
- `-m provider/model` - specify the model
- `-c` or `-s session-id` - continue an existing session
- `--title "..."` - name the session
