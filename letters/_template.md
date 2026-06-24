# Letter Template

## Format

- **Front page:** Main letter
- **Back page:** Supplementary info if needed
- **Output:** PDF for print / mail workflow
- **Paper:** Nice quality, professional look

---

## Constraint Notes

<!--
Use this file as a commented scaffold.

The assistant should not draft the main letter prose here unless Max explicitly asks.

Allowed contributions in this file:
- comments that explain what a section must do
- placeholders for Max to fill in
- structural notes
- reminders about what to avoid

Not allowed by default:
- polished letter paragraphs presented as final copy
-->

<!--
How to use this file:
- read the top-level constraint notes first
- then write each section using the short inline reminders near that section
- if a section is trying to do too many jobs at once, split it rather than hiding the confusion in prose
-->

### Purpose

<!--
What this letter is trying to do:
- get treated as a serious informational intervention
- push the reader toward the bigger-picture view of AI
- make a small but real ask
- leave a useful next step if they want to follow up

What not to do:
- sound like a stunt
- sound like a generic awareness blast
- sound like a demand for a favour
-->

### Audience

<!--
Keep both audiences in mind:
- staffer who triages and summarizes correspondence
- MP who may read either the summary or the letter itself

Practical implication:
- the letter should survive skimming
- the through-line should be easy to summarize accurately
- the most important point should not depend on the final paragraph to become clear
-->

### Credibility

<!--
The credibility burden is high.
Signal seriousness without leaning on status.
Point outward to credible people, groups, events, and resources where useful.

Questions to keep asking:
- why should they keep reading?
- why should a staffer pass this on instead of binning it?
- what in the wording shows informed concern rather than self-importance?
-->

### Tone

<!--
Serious, concise, and not gratuitously alarmist.
The reader should feel that Max takes this very seriously without reading him as unstable or melodramatic.

What to preserve:
- existential-risk concern is allowed
- emotional temperature should still feel controlled
- tidy presentation is part of the tone signal
-->

### Structure

<!--
The order should serve the reader journey, not just the writer's intuitive sequence.

Likely jobs the structure needs to cover:
- credible hook
- bigger-picture concern
- why this matters in New Zealand
- why this matters to this MP
- outward pointers / follow-up path
- closing ask
-->

### Reader Journey

<!--
Plan what the reader should think or feel after each section.
The hook, the reason to keep reading, the bigger-picture frame, and the ask all need to land in sequence.

Useful test:
- after paragraph 1: worth continuing
- after paragraph 2: this is bigger and faster-moving than I thought
- after paragraph 3 or 4: this matters in NZ and is not just abstract global discourse
- by the end: I know what this person wants me to keep in mind or do next
-->

### Skimmability

<!--
Assume rushed reading.
Sections should still make sense if the reader is scanning.

Practical implication:
- clear topic sentence energy in each section
- do not bury the main point in clause 4 of a long paragraph
-->

### Personal Relevance

<!--
MP-specific material should help the issue feel relevant without straining for a weak connection.

Prefer:
- responsibilities
- portfolio / committee / public priorities
- electorate relevance where real

Avoid:
- fake intimacy
- hobby-horse connections that feel bolted on

Dynamic paragraph rule of thumb:
- use one factual hook
- make one relevance bridge to AI / long-term governance / international coordination
- end with one small ask or reason this MP should keep the issue live

If the hook feels weak, use a lighter paragraph rather than over-explaining it.
-->

### Signposting

<!--
The letter may need explicit signals about where it is going, but they should not make it dull.

Use signposting when it reduces cognitive load.
Avoid sounding like an essay outline.
-->

---

## FRONT PAGE

Dear {Honorific} {Name},

[Opening sentence / opening paragraph written by Max]

<!--
Opening paragraph:
- hook credibly
- signal seriousness quickly
- make clear why this letter is worth continuing with
- no mention of money

This is doing Purpose + Credibility + Tone.

Questions:
- why this letter?
- why now?
- why should this reader keep going?
-->

[Bigger-picture concern paragraph written by Max]

<!--
Core concern section:
- introduce the bigger-picture concern
- preserve seriousness without overshooting into theatrics
- keep the issue legible to a rushed non-expert reader

This is doing Purpose + Tone + Reader Journey.

Questions:
- what is the actual concern?
- what makes it severe enough to matter politically?
- what makes it fast-moving enough not to defer?
-->

[New Zealand framing paragraph written by Max]

<!--
NZ framing section:
- connect the bigger picture to New Zealand's interests
- make clear this is not only abstract global-risk discourse
- keep the "keep the future human" line available if it works in the actual prose

This is doing Purpose + Structure + Audience.

Questions:
- why does this matter in New Zealand specifically?
- what does the bigger picture change about NZ's situation?
-->

[MP-specific paragraph written later]

<!--
Personalized section:
- connect the issue to this MP's responsibilities, context, or priorities
- do not strain the connection
- this dynamic section will be developed iteratively from reviewed examples

This is doing Personal Relevance + Audience.

Possible grounding:
- electorate relevance
- ministerial role
- spokesperson portfolio
- committee work
- background / previous public comments

Personalization types:
- special relationship: Greg O'Connor / Scott Willis only; do not generate these as ordinary mail merge copy
- explicit AI/tech evidence: mention only if the evidence still seems relevant and non-forced when drafting
- committee / portfolio relevance: use responsibilities rather than pretending the MP has already engaged with AI
- default: keep this short; a weak personalized paragraph is worse than a clean general letter

Special cases:
- Greg O'Connor: actual electorate MP
- Scott Willis: personal connection, likely not the normal template
See `data/SPECIAL-NOTES.md`.
-->

[Pointers to other people / groups / resources paragraph written by Max]

<!--
Outward-pointing section:
- avoid making Max the main authority
- point toward other NZ people, groups, events, or resources
- this may mention the links page / website if that exists by send time

This is doing Credibility + Signposting.

Potential categories only, not mandated inclusions:
- Christchurch AI Safety Conference
- Good Ancestors New Zealand if it exists by then
- other credible NZ-specific pointers
-->

[Ask / close paragraph written by Max]

<!--
Closing ask section:
- keep the ask real, even if it is not a very strong ask
- preserve openness to rapid change before the election
- make the follow-up path legible if the reader wants one

This is doing Purpose + Reader Journey + Signposting.

Likely ingredients:
- keep an open mind
- treat AI as more severe / more fast-moving than they currently might
- support NZ engagement in international coordination / AI control measures
-->

Yours sincerely,

Max Oakes
{Address}
{Email}

---

## BACK PAGE

### Resources

[Resource list or links block]

<!--
Only include resources that survive later review.
This may instead point to a links page / website.

Selection criteria:
- credible
- useful to a rushed political reader
- not too dependent on Max's personal authority
-->

### About Me

[Optional about-me section written by Max]

<!--
This section should support credibility without turning into a status play.
It should stay consistent with the "concerned citizen with some expertise" stance.

Question:
- what does the reader need to know about Max for the letter to land, and what is unnecessary?
-->

---

## Personalization Tiers

<!--
This section is a planning note, not final letter copy.

Potential use:
- special: known personal connection; not normal template output
- heavy: unusually important MPs / difficult edge cases
- medium: role, portfolio, committee, or AI/tech-adjacent evidence
- light: minimal personalization where the connection is weak

This is for workflow only. It should not leak into the visible letter.

See `docs/SEND-SCOPE.md` when deciding which tiers belong in the first batch.
-->

## Checklist Per Letter

- [ ] Correct honorific
- [ ] Opening hooks credibly
- [ ] Bigger-picture concern is legible without melodrama
- [ ] New Zealand framing is present and clear
- [ ] Personalized section reviewed
- [ ] Outward pointers are credible and not over-relied on
- [ ] Ask is real and visible
- [ ] No factual errors about their role
- [ ] Main page fits the intended layout
- [ ] Supporting page or links are ready if referenced
- [ ] Output artifact generated when needed
