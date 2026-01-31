# Research Worker Instructions

You are a research agent assigned to gather information about ONE New Zealand MP.

## Your Assignment

You have been assigned a specific MP. Your job is to find:

1. **Donation method** - How can someone donate to this MP directly (not to their party)?
2. **AI involvement** - Has this MP spoken about AI, technology regulation, or related topics?

## Where to Look

### For donation info:
1. The MP's personal website (if they have one)
2. Their electorate office website
3. Their social media profiles
4. Google search: `"{MP name}" donate OR donation site:nz`

### For AI involvement:
1. Parliament Hansard: Search for speeches mentioning AI, artificial intelligence, technology
2. News search: `"{MP name}" AI OR "artificial intelligence" site:stuff.co.nz OR site:nzherald.co.nz OR site:rnz.co.nz`
3. Their select committee work (if on a relevant committee)

## Output Format

Write your findings to `data/research/{mp-slug}.md` using this exact format:

```markdown
# {MP Full Name}

## Basic Info
- **Party:** {from mps.json}
- **Electorate:** {from mps.json, or "List" if list MP}
- **Parliament page:** {url}

## Donation Method

{Describe what you found, or "No public donation method found"}

If found:
- **Method:** {bank transfer / website / other}
- **URL:** {if applicable}
- **Notes:** {any relevant details}

## AI Involvement

**Level:** {none / tangential / deep}

**Evidence:**
- {bullet points with links to speeches, articles, etc.}
- {or "No evidence found" if none}

## Personalization Notes

{Any observations useful for writing a personalized letter}
{e.g., "Member of Justice Committee - could frame AI as justice issue"}
{e.g., "Former tech entrepreneur - understands the industry"}

## Research Notes

- **Sources checked:** {list what you searched}
- **Confidence:** {high / medium / low}
- **Time spent:** {approximate}
```

## Constraints

- Use only ONE browser tab
- Do not modify any files except your assigned MP's research file
- Do not modify `mps.json`
- If you hit rate limits or errors, note them and stop gracefully
- Timeout: 10 minutes max per MP

## Success Criteria

Your research is complete when you have:
- [ ] Checked for donation method (found or confirmed not available)
- [ ] Searched for AI involvement (found evidence or confirmed none)
- [ ] Written findings to the correct file
- [ ] Followed the output format exactly
