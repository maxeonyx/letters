# Research Worker Instructions

This file is for follow-up MP research only. The main research pass is already complete.

## Purpose

Use this only when a letter needs more factual grounding for one of these areas:

- postal address confirmation
- AI involvement / tech-adjacent evidence
- personalization notes for the MP-specific section

## What Not To Do

- Do not reopen the old money-centered strategy.
- Do not spend time looking for donation mechanisms.
- Do not rewrite `data/mps.json`.

## File To Update

Update:

```text
data/research/{mp-slug}.json
```

## Priority Order

### Priority 1: Postal Address

Confirm the best physical address for a letter.

### Priority 2: AI Involvement

Quickly check whether the MP has spoken about AI, technology regulation, digital policy, or adjacent topics.

### Priority 3: Personalization Notes

Only record hooks that help write a better letter without straining the connection.

Useful examples:

- relevant committee memberships
- ministerial or spokesperson roles
- former occupations
- previous public comments on technology, regulation, or related issues

## Status Values

- `pending`: not started
- `in-progress`: currently being worked on
- `done`: checked to the level needed
- `partial`: some useful work done, but incomplete

## Reference Files

- `VISION.md` for the current project direction
- `data/mps.json` for the base MP record
- `data/research/_schema.json` for the research structure
