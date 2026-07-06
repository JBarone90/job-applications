# Applications

Per-application drafted content that has no "master" version to maintain on `main` — unlike the CV, where `main` always holds the full content and a branch only selects/tailors from it.

## Convention

```text
applications/<company>-<role-slug>/personal-statement.md
applications/<company>-<role-slug>/behaviours.md
```

Not every application needs both — use whichever the JD's Success Profile stage actually asks for. Created on that application's `draft` branch alongside the CV tailoring commit, and preserved permanently via the same `sent/<company>-<role-slug>-<YYYY-MM>` tag. Once the branch is deleted, the folder disappears from `main` too — recover it with:

```bash
git checkout sent/<company>-<role-slug>-<YYYY-MM> -- applications/<company>-<role-slug>/
```

See the root `CLAUDE.md` for how `/civil-service-behaviours` drafts these files and the content integrity rule that governs them.
