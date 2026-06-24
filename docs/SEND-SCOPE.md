# Send Scope

This doc is for choosing what gets sent first. It should stay practical: the goal is to get a good version sent within Max's current couple-of-weeks window, not to keep reopening broad research.

## Current Recommendation

Use a two-path decision:

1. If Parliament bulk distribution can be confirmed quickly, send the all-MP version through that path and handle Greg O'Connor / Scott Willis separately.
2. If bulk distribution is unclear, slow, or weird, send a smaller high-quality first batch and leave the rest as follow-up.

This keeps the all-MP ambition alive without letting the unclear operational path block the campaign.

## Decision Gate

Before final production, confirm:

- whether Parliament will distribute one enclosed copy to each MP from a single package
- whether the required number is 121, 123, or something else
- whether individually addressed `FreePost Parliament` mail is still accepted in the format recorded in `docs/PLAN.md`
- whether non-Parliament office letters need ordinary postage

If this cannot be confirmed quickly, do not wait on it. Use the first-batch path.

## First-Batch Shape

A smaller first batch should be chosen by plausible path to impact, not just ease of personalization.

Suggested first batch size: 20-30 letters.

Use `data/send-tracker.csv` to mark final scope and production status. The initial tags are only a starting point.

Include:

- the two special cases, handled separately from the normal template
- party leaders and high-office MPs where the letter is likely to matter as a signal
- MPs with explicit AI/tech-adjacent evidence in current research
- Economic Development, Science and Innovation committee members
- a small number of MPs whose portfolios or public priorities make a clean relevance bridge

## Special Cases

These should not be normal mail-merge outputs.

- Greg O'Connor: actual electorate MP; use a more personal constituent tone and consider a normal postal letter even if the all-MP path is used.
- Scott Willis: family friend; likely direct/personal communication rather than the formal template.

## Current Local-Data Candidates

AI/tech-adjacent evidence in current research:

- Gerry Brownlee
- Reuben Davidson
- Matt Doocey
- Francisco Hernandez
- Melissa Lee
- Laura McClure
- Parmjeet Parmar
- Shane Reti
- Cushla Tangaere-Manuel
- Megan Woods

Economic Development, Science and Innovation committee in current `mps.json`:

- Hamish Campbell
- Reuben Davidson
- Parmjeet Parmar
- Cushla Tangaere-Manuel
- Vanessa Weenink
- Arena Williams
- David Wilson

High-office / cross-party signal candidates to confirm:

- Christopher Luxon
- David Seymour
- Winston Peters
- Chris Hipkins
- Chlöe Swarbrick
- Debbie Ngarewa-Packer
- Rawiri Waititi

This is not yet the final list. It is a factual starting set from the local data plus obvious political-signalling roles that should be confirmed before production. Before producing letters, remove duplicates and check whether any current ministers with directly relevant portfolios are missing from the scraped data.

## Pilot

Before printing the first batch, run a tiny pilot:

- Greg O'Connor as the constituent letter
- one high-office / party-leader letter
- one AI/tech-evidence letter
- one EDSI committee letter
- one default-low-personalization letter

The pilot should prove the template, dynamic paragraph, print layout, envelope/address workflow, and postage/freepost assumptions.
