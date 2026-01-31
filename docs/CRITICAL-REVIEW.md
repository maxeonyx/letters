# Critical Review

## Still Relevant

1. (Critical) Donation/legal-compliance is basically unresearched, yet it's central to the strategy
- You state "The donation is the key mechanism for ensuring attention." (`docs/PLAN.md`) and "Cash in physical letter is operationally simple but may have reporting implications" (`docs/PLAN.md`), but the actual rules doc is a stub: "*To be filled in during research*" (`docs/DONATION-RULES.md`).
- Failure mode: you operationalize donations (possibly anonymous, possibly cash, possibly to individuals) before you know if it's legal/ethical/practically processable by MPs. You could end up sending money that cannot be accepted, triggers reporting obligations, or gets returned/ignored.
- Fix: make "donation method + legal pathway" a gated prerequisite before any sending. Define compliant fallback (e.g., donate to party via official channel + reference letter; or no donation; or donate to a non-partisan NGO) and when to use it.

2. (Critical) The "donate to individual MP" premise may be structurally wrong / not reliably actionable
- You acknowledge "Donating directly to individual MPs (not parties) is inconsistently possible." (`docs/PLAN.md`) and "Some electorate MPs have donation mechanisms… Many do not" (`docs/DONATION-RULES.md`).
- Failure mode: for many MPs there may be no legitimate "donate to this MP" mechanism; your Tier 1 requirement ("Donation method… or fallback") (`AGENTS.md`) becomes the dominant blocker for most MPs.
- Fix: explicitly decide what "donation" means: electorate campaign account? party donation earmarked? charity? and define a standardized, legally safe fallback that still meets your intent.
- Note: Current approach is $50 cash in letter. Check if this is legal/processable.

3. (Critical) High risk of perceived bribery / quid-pro-quo signaling in the letter template
- Failure mode: it reads like "I'm paying to be heard," which can trigger reputational/ethical alarms and make staff auto-bin it.
- Fix: decouple donation from request language.
- Status: Donation paragraph has been rewritten to be less transactional ("I ask nothing in return"). Review if this is sufficient.

4. (Critical) The plan stops before the hard part: sending workflow, tracking, and outcomes are undefined
- "Phase A… scrape… Output: `data/mps.json`" then "Phase B… research" (`docs/PLAN.md`), but there's no Phase C describing how you actually send, record status, handle bounces, follow-ups, or measure responses.
- Failure mode: you end up with 121 research files (123 MPs minus 2 special cases) and no controlled execution (duplicates, missed MPs, inconsistent contact methods, no audit trail).
- Fix: add a concrete "Send pipeline" spec: status fields, batching, who/what gets emailed vs posted, follow-up cadence, response logging, and a minimal tracking file (CSV/JSON).

5. (Major) Tiering is plausible, but Tier 1 is under-specified and not actually "required to send"
- Tier 1 says "Contact method (email or physical address)" and "Donation method (or fallback)" (`AGENTS.md` / `docs/PLAN.md`). But you don't define minimum viable contact info (parliament email? electorate office? contact form?), nor what a valid "fallback plan" is.
- Failure mode: workers fill "No public donation method found" and you still can't act because you haven't defined what to do next.
- Fix: define Tier 1 precisely (accepted contact channels + ranked preference + required fields) and define the fallback decision tree.

6. (Minor) Phase 2 ideas are fine as a parking lot, but they're not prioritized or connected to outcomes
- `docs/PHASE-2-IDEAS.md` is a brainstorm list with questions, but no criterion for choosing what to do next.
- Fix: add a simple prioritization rubric (impact/effort/fit) and link it to what you learn from MPs' responses.

## Addressed / No Longer Relevant

The following items have been removed because they are now addressed or no longer apply:

- ~~#4 Truthfulness problem: "constituent of your electorate"~~ - Fixed: template now only uses "constituent" for Greg O'Connor (actual MP), all others get standard opening
- ~~#11 Letter content too generic~~ - Fixed: letter has specific asks, named forums (Bletchley, Seoul, Paris, India, OECD, UN), clear framing, personalization hooks
- ~~#7 "3 agents parallel" not implemented~~ - Research phase complete
- ~~#8 Phase A underspecified~~ - Research phase complete, mps.json exists with 123 MPs
- ~~#9 AI involvement levels inconsistent~~ - Research phase complete
- ~~#10 "10 minutes max" unrealistic~~ - Research phase complete
- ~~#12 No "do this now" checklist~~ - AGENTS.md updated with research workflow
- ~~#13 Donation rules not connected to worker~~ - Research phase complete
