# Critical Review

1. (Critical) Donation/legal-compliance is basically unresearched, yet it’s central to the strategy
- You state “The donation is the key mechanism for ensuring attention.” (`docs/PLAN.md`) and “Cash in physical letter is operationally simple but may have reporting implications” (`docs/PLAN.md`), but the actual rules doc is a stub: “*To be filled in during research*” (`docs/DONATION-RULES.md`).
- Failure mode: you operationalize donations (possibly anonymous, possibly cash, possibly to individuals) before you know if it’s legal/ethical/practically processable by MPs. You could end up sending money that cannot be accepted, triggers reporting obligations, or gets returned/ignored.
- Fix: make “donation method + legal pathway” a gated prerequisite before any sending. Define compliant fallback (e.g., donate to party via official channel + reference letter; or no donation; or donate to a non-partisan NGO) and when to use it.

2. (Critical) The “donate to individual MP” premise may be structurally wrong / not reliably actionable
- You acknowledge “Donating directly to individual MPs (not parties) is inconsistently possible.” (`docs/PLAN.md`) and “Some electorate MPs have donation mechanisms… Many do not” (`docs/DONATION-RULES.md`).
- Failure mode: for many MPs there may be no legitimate “donate to this MP” mechanism; your Tier 1 requirement (“Donation method… or fallback”) (`AGENTS.md`) becomes the dominant blocker for most MPs.
- Fix: explicitly decide what “donation” means: electorate campaign account? party donation earmarked? charity? and define a standardized, legally safe fallback that still meets your intent.

3. (Critical) High risk of perceived bribery / quid-pro-quo signaling in the letter template
- You state “The donation is the key mechanism for ensuring attention.” (`docs/PLAN.md`) and include in the template: “I have enclosed a small donation… as a token of the seriousness with which I view this issue.” (`letters/_template.md`)
- Failure mode: it reads like “I’m paying to be heard,” which can trigger reputational/ethical alarms and make staff auto-bin it.
- Fix: decouple donation from request language. If you donate, phrase it as general democratic support (or remove it entirely from the letter and keep it as a separate administrative action).

4. (Critical) Truthfulness problem: “constituent of your electorate” cannot apply to 120 MPs
- Template offers “{constituent of your electorate / New Zealand citizen}” (`letters/_template.md`), but there’s no rule for when to use which.
- Failure mode: accidentally misrepresenting being a constituent is a credibility-killer (and easy for staff to detect).
- Fix: make “NZ citizen” the default, only use “constituent” when the electorate matches Max’s actual electorate (and document how to determine that).

5. (Critical) The plan stops before the hard part: sending workflow, tracking, and outcomes are undefined
- “Phase A… scrape… Output: `data/mps.json`” then “Phase B… research” (`docs/PLAN.md`), but there’s no Phase C describing how you actually send, record status, handle bounces, follow-ups, or measure responses.
- Failure mode: you end up with 120 research files and no controlled execution (duplicates, missed MPs, inconsistent contact methods, no audit trail).
- Fix: add a concrete “Send pipeline” spec: status fields, batching, who/what gets emailed vs posted, follow-up cadence, response logging, and a minimal tracking file (CSV/JSON).

6. (Major) Tiering is plausible, but Tier 1 is under-specified and not actually “required to send”
- Tier 1 says “Contact method (email or physical address)” and “Donation method (or fallback)” (`AGENTS.md` / `docs/PLAN.md`). But you don’t define minimum viable contact info (parliament email? electorate office? contact form?), nor what a valid “fallback plan” is.
- Failure mode: workers fill “No public donation method found” and you still can’t act because you haven’t defined what to do next.
- Fix: define Tier 1 precisely (accepted contact channels + ranked preference + required fields) and define the fallback decision tree.

7. (Major) “3 agents parallel” is asserted, not implemented, and the constraints don’t map cleanly to your tool reality
- You require “bounded parallelism (3 agents)” and “Agents must not interfere (separate directories, single browser tab each)” (`docs/PLAN.md`).
- Research worker says “Use only ONE browser tab” (`scripts/research-worker.md`) but provides no mechanism to enforce this, and no guidance on whether to use browser automation vs static fetch.
- Failure mode: inconsistent browsing, conflicting edits, duplicated MP assignments, or agents silently violating constraints.
- Fix: define orchestration: how MPs are assigned/locked, how to resume, what happens on timeout, and how “one tab” is interpreted in practice.

8. (Major) Phase A “bulk scrape” is underspecified (schema, freshness, validation)
- You say “Scrape parliament.nz… basic info… Output: `data/mps.json`” (`docs/PLAN.md`) but provide no schema, no “last updated,” no validation checks, no slugging rules, no handling of list vs electorate MPs beyond a parenthetical.
- Failure mode: downstream research files don’t match the canonical MP list; slugs drift; committees change; contact info breaks.
- Fix: document `mps.json` schema + slug generation + a validation step (counts should equal current MPs; required fields present).

9. (Major) The research worker instructions invite shallow/false negatives and inconsistent “AI involvement level”
- You ask for “AI involvement… spoken about AI, technology regulation, or related topics?” (`scripts/research-worker.md`) and a coarse “Level: {none / tangential / deep}” without definitions.
- Failure mode: different agents label the same evidence differently; “none” becomes “didn’t find in 10 minutes,” not “likely none.”
- Fix: define levels with concrete criteria and require recording search queries + at least N sources checked before “none.”

10. (Major) “10 minutes max per MP” is likely unrealistic for donation + hansard + news verification
- Timeout is “10 minutes max per MP” (`scripts/research-worker.md`).
- Failure mode: rushed, low-confidence outputs; lots of “No evidence found” that are really “ran out of time.”
- Fix: split tasks (donation vs AI involvement) or allow a longer first pass, then a shorter second pass; or set minimum search steps before stopping.

11. (Major) Letter content is not yet likely to be effective (too generic + big claim + unclear ask)
- Template: “The future of humanity is contingent…” and “This is not hyperbole…” (`letters/_template.md`) plus placeholders for personalization/ask.
- Failure mode: reads like a form letter with high-stakes rhetoric and no crisp, MP-specific action; staff may ignore without a concrete request.
- Fix: standardize 2–3 specific asks with “pick one based on role,” and tighten evidence framing (one credible NZ-relevant hook, one international coordination hook, one actionable request).

12. (Minor) Repo discoverability: entry points are fine, but there’s no “do this now” checklist for a fresh agent
- `AGENTS.md` says “read this file first, then `docs/PLAN.md`” and points to `scripts/research-worker.md`, which is good, but there’s no explicit “start here: run Phase A / create mp slugs / pick first 5 MPs” execution checklist.
- Fix: add a short “First run” section in `AGENTS.md` (exact next command(s), expected outputs, where to put artifacts).

13. (Minor) Cross-references don’t connect donation rules to worker behavior
- Worker doc never references `docs/DONATION-RULES.md`, even though donation compliance is the biggest risk.
- Fix: add a “Before marking donation found” checklist (what constitutes valid/public method; what not to do).

14. (Minor) Phase 2 ideas are fine as a parking lot, but they’re not prioritized or connected to outcomes
- `docs/PHASE-2-IDEAS.md` is a brainstorm list with questions, but no criterion for choosing what to do next.
- Fix: add a simple prioritization rubric (impact/effort/fit) and link it to what you learn from MPs’ responses.
