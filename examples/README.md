# Examples

A reusable library of full, unabridged achievement write-ups — the raw material behind the compressed `cv/experience.tex` bullets and the source material for personal statements and behavioural (STAR) answers. Unlike `applications/`, this lives permanently on `main`: it's master content, not per-application output.

## Convention

One file per story, named `<company-or-context-slug>.md`, with frontmatter tagging which criteria/behaviours it evidences:

```
---
company: <employer>
context: <one-line project context>
tags: [tag-one, tag-two, ...]
---

<full write-up, in your own words, unedited>
```

Tags aren't a fixed taxonomy — use whatever a future application is likely to search for (e.g. `team-leadership`, `communicating-and-influencing`, `cloud-databricks`, `changing-and-improving`). When drafting a personal statement or a Civil Service Behaviour answer, search these files for matching tags before asking for a new story — most JD criteria and Behaviours will already have a real example on file here.

## Relationship to other content

- `cv/experience.tex` — compressed bullets distilled from these examples, always present on `main`.
- `applications/<company>-<role>/` — per-application drafts (personal statements, behaviours) adapted from these examples for a specific JD, not persisted on `main`.
- These files are the connective tissue between the two: richer than a CV bullet, more general than a tailored answer.
