# Research Orchestration

How to coordinate parallel research of MPs using the `researcher` subagent.

## Overview

- 121 MPs to research
- Use the `researcher` subagent via Task tool
- Launch 5-10 agents in parallel for speed
- Each agent takes ~20 minutes for 3-5 MPs

## Launching Research Agents

Use the Task tool with `subagent_type="researcher"`. Launch multiple in parallel:

```
Task(subagent_type="researcher", description="Research batch 1", prompt="
Research these MPs:
1. steve-abel (Steve Abel)
2. ginny-andersen (Ginny Andersen)
3. miles-anderson (Miles Anderson)

Find postal addresses first for ALL MPs, then donation methods.
Update data/research/{slug}.json immediately after each finding.
")
```

**Launch 5-10 of these simultaneously** with different MP batches.

## Check Current Progress

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

## Get Next Batch of MPs

```bash
node -e "
const fs = require('fs');
const files = fs.readdirSync('data/research').filter(f => f.endsWith('.json') && !f.startsWith('_'));

const pending = [];
for (const f of files) {
  const d = JSON.parse(fs.readFileSync('data/research/' + f, 'utf8'));
  if (d.researchStatus === 'pending' || d.researchStatus === 'partial') {
    pending.push(d.slug + ' (' + d.name + ')');
  }
}

// Show next 30 (for 5-10 parallel agents)
console.log('Next 30 pending MPs:');
pending.slice(0, 30).forEach((mp, i) => console.log((i+1) + '. ' + mp));
"
```

## Batch Size Recommendations

| Parallel agents | MPs per agent | Total per round | Time estimate |
|-----------------|---------------|-----------------|---------------|
| 5 | 5 | 25 | ~20 min |
| 10 | 3 | 30 | ~20 min |

With 121 MPs, you need ~4-5 rounds of 5-10 parallel agents.

## Summarize Findings

```bash
node -e "
const fs = require('fs');
const files = fs.readdirSync('data/research').filter(f => f.endsWith('.json') && !f.startsWith('_'));

let postalFound = 0, donationFound = 0, aiChecked = 0;

for (const f of files) {
  const d = JSON.parse(fs.readFileSync('data/research/' + f, 'utf8'));
  if (d.postalAddress?.status === 'found') postalFound++;
  if (d.donationMethod?.status === 'found') donationFound++;
  if (d.aiInvolvement?.status === 'checked') aiChecked++;
}

console.log('Postal addresses found:', postalFound, '/ 121');
console.log('Donation methods found:', donationFound, '/ 121');
console.log('AI involvement checked:', aiChecked, '/ 121');
"
```

## After Research Completes

### Clean up any interrupted agents

```bash
node -e "
const fs = require('fs');
const files = fs.readdirSync('data/research').filter(f => f.endsWith('.json') && !f.startsWith('_'));

for (const f of files) {
  const d = JSON.parse(fs.readFileSync('data/research/' + f, 'utf8'));
  if (d.researchStatus === 'in-progress') {
    d.researchStatus = 'partial';
    fs.writeFileSync('data/research/' + f, JSON.stringify(d, null, 2));
    console.log('Marked as partial:', d.slug);
  }
}
"
```

### Commit progress

```bash
git add data/research/*.json
git commit -m "research: batch complete - X MPs researched"
git push
```

## Troubleshooting

**Agent reports "Browser tools unavailable":**
- This is expected if browser isn't connected via CDP
- The researcher agent is designed to stop and report this
- Try restarting opencode with browser connection

**Agent times out or gets cut off:**
- No data is lost - incremental writes save everything found so far
- Run the cleanup script above to mark as `partial`
- Re-run that MP in the next batch

**Parliament.nz blocks requests:**
- WebFetch is blocked by Radware firewall
- Browser tools should work (connects through real browser)
- If browser also fails, that MP needs manual research
