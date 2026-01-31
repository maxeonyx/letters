# Research Worker Instructions

**Note:** This file is detailed reference for the `researcher` subagent. The agent has its own instructions in `~/.config/opencode/agents/researcher.md`. This file provides additional context on priorities and JSON schema.

---

## Your Assignment

You have been assigned a batch of MPs. For each MP, you will update their research file at:
```
data/research/{mp-slug}.json
```

The file already exists with a pending status. Your job is to fill in the fields.

## Priority Order

Work through MPs in this order of priority for EACH MP before moving to the next priority:

### Priority 1: Postal Address (do this for ALL MPs first)
Find their electorate office or other postal address for physical letters.

**Where to look:**
1. Their parliament page (usually has contact details)
2. Their party bio page 
3. Their personal/electorate website
4. Google: `"{MP name}" electorate office address site:nz`

**Update the file:**
```json
"postalAddress": {
  "status": "found",  // or "not-found" if genuinely unavailable
  "value": "123 Main St, Wellington 6011",
  "source": "https://example.nz/contact",
  "notes": "Electorate office, open Mon-Fri 9-5"
}
```

### Priority 2: Donation Method (do this for ALL MPs second)
Find how to donate directly to this MP (not their party).

**Where to look:**
1. Their personal website "Support" or "Donate" page
2. Their electorate campaign site
3. Google: `"{MP name}" donate OR donation site:nz`

**Important:** Read `docs/DONATION-RULES.md` for legal context. We're looking for:
- Bank account for direct deposit
- Online donation form
- Or confirmation that no public method exists

Most MPs will NOT have a public donation method. That's expected - record "not-found" after checking.

**Update the file:**
```json
"donationMethod": {
  "status": "found",  // or "not-found"
  "method": "bank-transfer",  // bank-transfer | website | party-channel | none-found
  "url": null,
  "bankAccount": "12-3456-7890123-00",
  "details": "Reference: [Your Name]",
  "notes": "Found on electorate campaign page"
}
```

### Priority 3: AI Involvement (quick scan only - don't spend long on this)
Has this MP spoken about AI, technology regulation, or related topics?

**Quick checks only:**
1. Search their parliament page for keywords: AI, artificial intelligence, technology, digital
2. Quick Google: `"{MP name}" AI OR "artificial intelligence" site:parliament.nz`
3. Check their spokesperson roles (in mps.json) - are they spokesperson for tech/innovation/digital?

**Level definitions:**
- `none`: Searched but found nothing AI-related
- `tangential`: Mentioned AI/tech in passing, or has a tech-adjacent portfolio
- `deep`: Actively engaged (speeches about AI, tech committee member, etc.)

**Update the file:**
```json
"aiInvolvement": {
  "status": "checked",
  "level": "tangential",
  "evidence": [
    {
      "type": "committee",
      "summary": "Member of Economic Development, Science and Innovation Committee",
      "url": null,
      "date": null
    }
  ],
  "notes": "Has science portfolio but no direct AI statements found"
}
```

### Priority 4: Personalization Notes (only if something obvious)
If you notice something useful for writing a compelling letter, note it:
- Former occupation (teacher, business owner, etc.)
- Relevant committee memberships
- Known positions on related issues

```json
"personalizationNotes": "Former software developer - could frame AI as industry insider issue. On Justice Committee - could frame as governance/regulation angle."
```

## How to Update Files

Read the current file, update the relevant fields, write it back. Example:

```javascript
// Read current
const data = JSON.parse(fs.readFileSync('data/research/chloe-swarbrick.json', 'utf8'));

// Update fields
data.researchStatus = 'in-progress';
data.lastUpdated = new Date().toISOString();
data.postalAddress = {
  status: 'found',
  value: '123 Example St, Auckland 1010',
  source: 'https://greens.org.nz/chloe_swarbrick',
  notes: null
};
data.sourcesChecked.push({
  source: 'https://greens.org.nz/chloe_swarbrick',
  checked: true,
  foundUseful: true,
  notes: 'Found postal address'
});

// Write back
fs.writeFileSync('data/research/chloe-swarbrick.json', JSON.stringify(data, null, 2));
```

**Always update `lastUpdated` when you modify a file.**

## Status Values

Set `researchStatus` as you work:
- `pending`: Not started (initial state)
- `in-progress`: Currently working on this MP
- `done`: All priorities checked
- `partial`: Started but didn't finish (use if you run out of time)

## When You're Done

1. Ensure all files have been updated with findings (even if "not-found")
2. Set `researchStatus` to `done` for completed MPs, `partial` for incomplete
3. Your work is saved in the files - no final report needed

## Error Handling

- If a website is blocked or times out, note it in `sourcesChecked` and move on
- If you hit rate limits, stop gracefully - your incremental saves mean nothing is lost
- If you run out of time, that's fine - set incomplete MPs to `partial` status

## Reference Links

- Parliament MP pages: `https://www3.parliament.nz/en/mps-and-electorates/members-of-parliament/{slug}/`
- Master MP data: `data/mps.json` (read-only, contains emails, parties, committees, etc.)
- Donation rules: `docs/DONATION-RULES.md`
- Research schema: `data/research/_schema.json`
