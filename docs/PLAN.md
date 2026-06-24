# Project Plan

This plan is about getting the project from its current state to a clean, testable, sendable letter campaign.

The research phase is complete. The current work is rebaselining the project around the updated direction in `VISION.md`, then driving it through drafting, validation, production, and sending.

## Current Situation

What already exists:

- A complete MP dataset in `data/mps.json`
- Research records for 121 MPs in `data/research/`
- Special handling notes for Greg O'Connor and Scott Willis in `data/SPECIAL-NOTES.md`
- An existing letter scaffold, support pages, and research data that need to stay aligned with the current direction

What has changed:

- The repo has been rebaselined away from the old money-centered strategy
- The letters now need to be informational, concise, and serious
- The focus is international coordination, AI control measures, and Max's framework for thinking about New Zealand's national interest in an increasingly automated world
- The letters should not present Max as the expert; they should point toward other people, groups, events, and resources in New Zealand

## End State

The project is ready for Max to continue, test to completion, and send the letters.

That means:

- The repo consistently reflects the new direction
- The letter requirements are clear enough to judge drafts against
- The letter template is strong enough to trial with real readers
- Supporting resources and links are ready
- The production workflow is ready: printing, envelopes, addressing, postage / freepost, batching, and tracking
- The sending process can be run without ad hoc decisions at the last minute

## Process Stages

### Stage 1: Rebaseline the project

Purpose: remove the old project story and make the repo internally consistent.

Input:

- The updated direction in `VISION.md`
- Existing docs and templates that may drift away from the current direction over time

Output:

- Root docs, planning docs, and letter materials all point in the same direction
- Obsolete or misleading material is either rewritten, parked clearly as historical, or deleted

Key risks if skipped:

- Future work keeps pulling in stale framing by accident
- Drafts and decisions are judged against contradictory goals

### Stage 2: Define the letter requirements and evaluation criteria

Purpose: decide what a good letter must do before trying to polish wording.

Input:

- Rebaselined project docs
- Max's current goals, constraints, and concerns

Output:

- A concrete set of letter requirements
- A clear statement of the ask
- A clear statement of what must be preserved in tone and framing
- A lightweight evaluation rubric for deciding whether a draft is actually good enough to send

Key questions to settle in this stage:

- What is the primary ask?
- What is the minimum viable ask if the stronger wording feels forced?
- How should existential risk be present without making the letter feel melodramatic?
- How should the New Zealand economic / national-interest framing appear?
- How explicitly should the letter say "keep an open mind" given that AI may change substantially by election day?
- How strongly should the letter point MPs toward external people and organisations rather than toward Max?

Key risks if skipped:

- Endless drafting without agreement on what success looks like
- Good-sounding prose that does not serve the actual goals

### Stage 3: Validate the strategy against paths to impact

Purpose: confirm that sending these letters still looks worthwhile and non-disruptive.

Input:

- Letter requirements
- Max's stated paths to impact

Output:

- A clear view of why the project is worth doing
- A list of failure modes to avoid
- A decision on what the letters are realistically trying to achieve

What this stage needs to answer:

- Does the current letter concept plausibly help with any of the three paths to impact?
- Could the letters interfere with, confuse, or undermine other people working on AI safety in New Zealand?
- What kinds of tone, claims, or asks would reduce the chance of impact?
- What kinds of links or supporting resources increase the chance that an MP or staffer actually does something useful next?

Loop:

- If the strategy looks weak or misaligned, go back to Stage 2 and revise the requirements before further drafting

### Stage 4: Build the content package

Purpose: create the materials the letters rely on.

Input:

- Stable requirements and strategy

Output:

- A strong base letter template
- Personalization guidance that matches the new strategy
- A links page / website with credible supporting resources
- A short list of NZ-specific references to include or mention, if appropriate

Work inside this stage:

- Redraft `letters/_template.md`
- Decide what belongs in the main letter vs a back page vs the links page
- Decide whether the links page is primarily explanatory, resource-oriented, or both
- Confirm whether Christchurch AI Safety Conference and Good Ancestors New Zealand should be included, and how
- Rework any public-facing pages so they match the new framing

Loop:

- Drafts from this stage are reviewed against the Stage 2 rubric and the Stage 3 impact check

### Stage 5: Test the message with humans

Purpose: find out whether the letters actually land the way Max wants.

Input:

- A candidate letter package

Output:

- Feedback on clarity, tone, credibility, emotional temperature, and likely impact
- A list of revisions grounded in reader response rather than speculation

What should be tested:

- Does the letter feel serious but not overblown?
- Is the ask clear enough?
- Does the New Zealand framing make sense to a non-expert?
- Does the letter sound like informed concern rather than self-importance?
- Does the use of external resources increase credibility?

Loop:

- Feedback from real readers may send us back to Stage 2 or Stage 4

### Stage 6: Prepare operations for physical sending

Purpose: make sure the campaign is operationally real, not just rhetorically ready.

Input:

- A stable content package
- Existing MP contact data

Output:

- A print specification
- A chosen print provider or printing method
- Envelope and paper decisions
- Addressing and postage rules confirmed
- A send workflow and tracking method

Questions this stage needs to answer:

- Where should the letters be printed?
- What paper stock and print quality are good enough?
- How should double-sided printing be set up?
- What envelopes should be used?
- Which addresses are the right destination for each MP?
- Which letters can use freepost and which cannot?
- What tracking file do we use to record print status, packed status, sent status, and any replies?

Key risks if skipped:

- The final week becomes a scramble of printing and postage decisions
- Good letters are delayed or sent inconsistently

### Stage 7: Run a small end-to-end pilot

Purpose: test the whole process before committing to the full batch.

Input:

- Final candidate materials
- Operational workflow

Output:

- Confidence that the full campaign can be executed cleanly
- Any last operational or wording fixes discovered by real use

Possible pilot scope:

- Print a few sample letters
- Check print quality, paper feel, duplex layout, envelope fit, and addressing
- Optionally send a very small batch if that makes sense

Loop:

- If the pilot exposes issues, return to Stage 4 or Stage 6 as needed

### Stage 8: Final production and sending

Purpose: execute the campaign cleanly.

Input:

- Approved letter package
- Approved operations workflow
- Successful pilot

Output:

- Letters printed, packed, addressed, and sent
- Sending status recorded
- Any responses or follow-up opportunities captured

## Work Plan

The concrete steps to get the project sorted out are:

1. Review and refine the current letter requirements in a form we can judge drafts against.
2. Define the impact model and failure modes so we know what the letters are trying to achieve.
3. Plan the commented-template approach: decide what kinds of comments, placeholders, and section constraints the template should contain, without writing the letter copy itself.
4. Build or revise the links website and supporting resources.
5. Gather outside feedback on representative draft letters.
6. Research and decide the print / envelope / postage workflow.
7. Create a send-tracking system.
8. Run a small end-to-end pilot.
9. Prepare the full batch for sending.

## Near-Term Send Push

Max's 2026-06-24 near-term goal: "I'd like to keep it going and sent these letters within a couple of weeks."

This means the near-term work should bias toward a sendable package and an executable physical workflow, not more open-ended research.

Immediate work:

1. Finalize the copy template enough for Max to write and review the main prose.
2. Finalize dynamic content for special MPs, starting with Greg O'Connor and Scott Willis from `data/SPECIAL-NOTES.md`.
3. Decide whether to send all 123 letters or a smaller prioritized batch. Use `docs/SEND-SCOPE.md` for the current decision gate and first-batch shape.
4. If sending a smaller batch, pick the batch based on plausible path to impact, not only ease of personalization.
5. Find and choose a printing option for high-quality letterhead / paper, duplex printing, and professional output.
6. Confirm envelopes, stamps, and freepost rules, especially which letters can be sent to Parliament by freepost and which need ordinary postage.
7. Maintain `data/send-tracker.csv` as the print/send tracker before production starts.
8. Run a small end-to-end print/mail pilot before committing to the full or prioritized batch.

Scope note:

- Max said: "Also - I'm open to not doing all 120+"
- A smaller batch is acceptable if it increases quality, reduces operational drag, or makes the campaign more likely to actually get sent within the current timeline.

Operational notes found 2026-06-24:

- NZ Post Standard Mail for domestic letters: medium letters are currently $2.90 / 1 KiwiStamp, large letters are $4.20, oversize letters are $5.50; standard delivery estimate is 3 working days. Source: https://www.nzpost.co.nz/personal/sending-in-nz/letters
- Parliament's contact page was blocked by browser verification from this environment, but DuckDuckGo snippets for the Parliament page say: "If you want to send a letter to all members of Parliament, send us 121 copies of your letter in one envelope. Include a covering note asking for a copy to be distributed to each MP." This needs manual confirmation because the repo source-of-truth says there are 123 MPs.
- Search snippets from the official NZ Parliament Facebook account quote the individual freepost format as: `[MP name]`, `FreePost Parliament`, `Private Bag 18888`, `Parliament Buildings`, `Wellington 6160`. Confirm before relying on it for production.
- Printing candidates worth checking first: Rieger's Print, Wellington CBD, 04 473 1444, print@riegers.co.nz, https://www.riegers.co.nz/; Hotprint, Wellington CBD, 04 499 6588, sales@hotprint.nz, https://hotprint.nz/services/business_stationary/.
- Other possible print options: About Print, https://www.aboutprint.co.nz/; Warehouse Stationery / WS Print for convenience if bespoke local printing is not needed.

## Dependencies

- Steps 1 and 2 should happen before serious redrafting.
- Step 3 depends on Steps 1 and 2.
- The actual commented template edits should stay constrained by the no-letter-copy rule unless Max asks otherwise.
- Step 4 depends on Step 3 enough to know what the links page is for.
- Step 5 depends on having something real to react to from Steps 3 and 4.
- Steps 6 and 7 can partly proceed in parallel once the high-level direction is stable.
- Step 8 depends on Steps 3 through 7.
- Step 9 depends on a successful pilot.

## Done Criteria

This plan is complete when:

- A fresh agent can read the repo and understand the current project direction without being misled by obsolete docs
- Max has a letter package that has been reviewed against explicit requirements and tested with real readers
- The physical sending workflow has been rehearsed enough that the remaining work is mostly execution
