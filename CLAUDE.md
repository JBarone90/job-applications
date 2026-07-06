# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this repo is

Tooling for Jacopo Barone's job applications:
- A XeLaTeX CV built with the [Awesome-CV](https://github.com/posquit0/Awesome-CV) class (`awesome-cv.cls`). Single-column layout, one page, targeting Data Science and Neuroscience roles.
- UK civil service Success Profile applications (personal statements, behavioural/STAR answers), drafted per application — see [Civil service Success Profile applications](#civil-service-success-profile-applications) below.
- `examples/` — a permanent library of full, unabridged achievement write-ups that both the CV bullets and the Success Profile content are distilled from.

## Building

**Locally (requires Docker):**
```powershell
docker compose run --rm latex
```
This runs `xelatex Jacopo_cv.tex` twice inside `texlive/texlive:latest-full` and writes `Jacopo_cv.pdf`. Use this command directly — `build.ps1` has encoding issues.

**CI:** GitHub Actions (`.github/workflows/build.yml`) builds on every push/PR to `main` using `xu-cheng/latex-action@v3` with XeLaTeX and uploads the PDF as an artifact named `Jacopo_CV` (retained 30 days).

## File layout

| File/Dir | Purpose |
|---|---|
| `Jacopo_cv.tex` | Root document — personal info, packages, two-column structure |
| `cv/experience.tex` | Work history (`\cvsection{Experience}`) |
| `cv/skills.tex` | Skills table (`\cvsection{Skills}`) |
| `cv/education.tex` | Education (`\cvsection{Education}`) |
| `cv/publications.tex` | Publications (currently not included in the main doc) |
| `awesome-cv.cls` | Upstream class file — avoid editing |
| `fonts/` | Bundled fonts referenced via `\fontdir[fonts/]` |
| `logos/` | Institution/company logos used in entries |
| `references.bib` | BibTeX entries (biblatex wiring is commented out) |
| `examples/` | Permanent library of full achievement write-ups, tagged by criteria/behaviour — source material for CV bullets, personal statements, and behavioural answers |
| `reference/` | External reference material (e.g. the Civil Service Behaviours framework) |
| `applications/<company>-<role>/` | Per-application drafted output (personal statements, behavioural answers) — not persisted on `main` |

## Writing rule

**Always run `/writing-coach` immediately after producing or editing any prose** — CV content (`cv/summary.tex`, `cv/experience.tex`), behavioural answers (`applications/*/behaviours.md`), or the README. This is automatic orchestration, not a step the user needs to request: whether the text was written directly or drafted by `/jd-parser` → `/civil-service-behaviours`, chain straight into `/writing-coach` before presenting the draft, not just before committing. Do not commit prose changes without a writing-coach pass first.

## Content integrity

- **Never fabricate** — do not invent metrics, achievements, tools, or responsibilities Jacopo did not perform. Reframing and emphasising real work is encouraged; crossing into fiction is not.
- Adapt existing bullet text creatively (stronger verbs, sharper framing, JD-mirrored language) but only if the underlying claim remains true.
- If a JD requires a skill or experience genuinely absent from the CV, flag the gap explicitly rather than papering over it.
- This applies equally to behavioural (STAR) answers: a real example reframed to fit a behaviour's language is fine; an invented situation or result is not.

## ATS compatibility

This CV must remain parseable by Applicant Tracking Systems. Always maintain:
- Single-column layout (no `paracol` or multi-column environments for content)
- Real text for all CV content — no text embedded in images or graphics
- Standard section headings (Experience, Education, Skills, etc.)
- No text boxes, headers/footers carrying substantive content, or decorative tables

**If the user requests a design change that would break ATS readability** (e.g. two-column layout, graphical skill bars, infographic elements), warn them before implementing and suggest an ATS-safe alternative.

## Application workflow

`main` is the **master branch** — all content available (all bullets, publications, BSc, full education). Never strip content from main; only add.

### Branching strategy (keep the repo clean)

Use a single reusable `draft` branch for active tailoring. The full history is preserved via tags, not branches.

```
# Start a new application
git checkout main && git checkout -b draft

# Tailor the CV files (and draft applications/<company>-<role>/behaviours.md for government roles), then commit
git add cv/summary.tex cv/experience.tex applications/  # (and any other modified files)
git commit -m "chore: tailor for <company> <role>"

# Tag the tailored commit (while still on draft, before switching back)
git tag -a sent/<company>-<role-slug>-<YYYY-MM> -m "applied <date>"

# Return to main and delete the branch
# The tag preserves the tailored commit permanently — main is untouched
git checkout main && git branch -d draft
```

The branch list stays clean (`main` only). The tag points to the tailored commit directly, not to the branch, so deleting `draft` does not affect it. Run `git checkout sent/<company>-<role-slug>-<YYYY-MM>` at any point to inspect or rebuild the exact PDF that was submitted.

### Tailoring steps
1. **Profile summary** (`cv/summary.tex`) — rewrite to mirror the JD's language; this is the highest-leverage change
2. **Bullet selection** — comment in/out bullets in `cv/experience.tex` to match what the role values
3. **Position title** (`Jacopo_cv.tex`) — adjust `\position{}` if the framing differs (e.g. "Computational Neuroscientist" for research roles)
4. **Section order** — for research/academic roles, move education before experience and restore `\input{cv/publications.tex}`
5. **Page budget** — one page for industry; two pages acceptable for academic/research roles
6. Build and review: `docker compose run --rm latex`

### How to present a job description

Paste the JD using this format so keywords and priorities can be extracted cleanly:

```
Role: <title>
Company: <name>
Type: industry | academic | government
---
<full JD text or bullet-point requirements>
---
Notes: <any angle you want to emphasise, optional>
```

### When given a job description
- Extract the 5–8 most distinctive keywords/phrases from the JD
- Check each against the current profile summary and active bullets
- Rewrite the profile summary first, then swap bullets to match
- Prefer the JD's exact phrasing over synonyms where natural
- Flag any genuine skill gaps rather than obscuring them

### Toggleable content
| Content | File | How to restore |
|---|---|---|
| Publications | `Jacopo_cv.tex` | Uncomment `\input{cv/publications.tex}` |
| BSc entry | `cv/education.tex` | Uncomment the `\cvedu{BSc…}` block |
| 3rd bullet per role | `cv/experience.tex` | Uncomment the `% \item {…}` lines |
| Great Expectations bullet (DBT) | `cv/experience.tex` | Uncomment |
| SLURM/HPC bullet (PhD) | `cv/experience.tex` | Uncomment |

## Civil service Success Profile applications

For UK government roles assessed against Success Profiles, tailoring means drafting new content per application rather than selecting from existing content — there's no single master version, since each vacancy asks for a different mix of essential criteria, personal statement word limits, and behaviours at different levels.

- **`examples/`** — the first place to look for real supporting material. Full, unabridged achievement write-ups tagged by criteria/behaviour (see `examples/README.md`), reusable across applications. Search here before asking Jacopo for a new story — most essential criteria and behaviours already have a genuine example on file.
- **`reference/civil-service-behaviours.md`** — framework text fetched from the live gov.uk page, trimmed to the HEO/SEO and Grade 7/Grade 6 tiers (Jacopo's realistic application range — SEO up to Grade 6). Consult this for exact behaviour definitions and level indicators rather than relying on general knowledge of the framework. If a JD asks for a grade outside that range, flag it — don't improvise. See `reference/README.md` for provenance and how to refresh it.
- **`applications/<company>-<role>/`** — per-application drafted output: `personal-statement.md` (essential-criteria statement, one section per criterion, respecting the JD's stated word limit) and/or `behaviours.md` (STAR-format behaviour answers). Created on that application's `draft` branch, committed alongside the CV tailoring, and preserved via the same `sent/*` tag. Neither persists on `main` after the branch is deleted (see `applications/README.md`) — this mirrors how a tailored `cv/summary.tex` is only "current" for the branch it was written on.
- Many sifts require an **anonymous** CV/statement (no name or identifying details). The `Jacopo_cv.tex` header (`\name`, email, GitHub, LinkedIn) is not anonymous — tailor the CV content first as the source of truth, then extract and anonymise it separately for portal submission rather than trying to strip identity from the LaTeX template itself.
- **`/civil-service-behaviours`** — the agent that drafts STAR-format behaviour answers. Run it after `/jd-parser` has identified the role's required behaviours (JD `Type: government`). It reads `examples/`, `reference/civil-service-behaviours.md`, and `cv/experience.tex`/`cv/education.tex`, and will flag rather than paper over any behaviour with no genuine supporting example. Personal statements are drafted directly (same as CV prose), also grounded in `examples/`.
- Respect whatever word/character limit the JD states for each behaviour or personal statement — these vary by vacancy, never assume a default.
- Run `/writing-coach` on `personal-statement.md`/`behaviours.md` before submitting, same as CV prose.

## Authoring conventions

- Each section lives in its own file under `cv/` and is pulled in via `\input{}` from the root.
- Unused content (alternative bullet points, commented-out sections) is kept as `% …` comments rather than deleted, so variants can be restored easily.
- The `\jobstyle{}` + inner `itemize` pattern is used in experience entries to get bullet-indented sub-items inside `cventries`.
- `\columnratio{0.6,0.4}` and `\setlength{\columnsep}{1cm}` control the two-column split and gap — tweak these in `Jacopo_cv.tex` to rebalance the layout.
- The biblatex/`references.bib` pipeline is fully wired but commented out; uncomment the three lines in the bibliography config block and `\input{cv/publications.tex}` to re-enable it.
