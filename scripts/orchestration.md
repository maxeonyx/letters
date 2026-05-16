# Research Orchestration

This file is only for follow-up MP research. The main research phase is complete.

## Use Case

Use the `researcher` subagent only when a later drafting pass needs more factual grounding for a subset of MPs.

Typical reasons:

- confirm a postal address before sending
- strengthen AI involvement evidence
- improve personalization notes for a difficult MP

## Batch Prompt Shape

```text
Research these MPs:
1. slug-one (Full Name)
2. slug-two (Full Name)

For each MP, confirm the best postal address, then check for AI/tech-adjacent involvement, then add any useful personalization notes.
Update data/research/{slug}.json as you go.
```

## What Counts As Done

- the postal address is confirmed or explicitly marked not found
- AI involvement has been checked
- any useful personalization note has been recorded

## Important Constraint

Do not send follow-up researchers back into the old money-centered workflow. That is no longer part of the active project.
