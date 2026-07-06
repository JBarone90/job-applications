---
company: Department for Business and Trade (leading), with DfT and ONS
context: World's first public sector Bill of Lading-AIS vessel-tracking linkage
tags:
  [
    team-leadership,
    cross-government-collaboration,
    working-together,
    communicating-and-influencing,
    making-effective-decisions,
    leadership,
    stepping-up,
    inclusion,
    delegation-by-expertise,
    reflective-practice,
    wellbeing,
    data-quality,
  ]
---

## People management

Supporting and motivating a team to deliver excellence and derive fulfilment from their roles.

I led the technical supervision of 8 analysts and data scientists across three government organisations (DBT, DfT, ONS) to deliver an experimental publication linking UK Bill of Lading data with AIS vessel-tracking information. Each analyst worked within their own departmental structure — this was cross-government technical coordination, not formal line management — and I set direction and provided support across the distributed team. I structured the project around each department's comparative strength rather than running every workstream the same way: DBT owned the shipping data and built the deepest understanding of it, ONS brought its expertise in the AIS tracking system, and DfT supplied the maritime traffic knowledge that helped interpret some of the findings. I set this division of labour, along with a phased timeline and expected outcomes per stage, out in a project roadmap at the outset.

Technically, a crossing was detected from each ship's AIS position data: a vessel counts as having transited a passage when its track intersects both an entry and an exit polygon around it (sourced from DfT, widened for passages like Suez to guarantee a genuine intersection), applied across six critical straits — Dover, Suez, Bab-Al Mandab, Hormuz, Cape of Good Hope, and Taiwan. Linking that to Bill of Lading shipping-instruction data let us follow containerised cargo near real-time, not just ship movements. It proved out in practice: during the early-2024 Middle East disruption, the method picked up a 68% drop in cargo-ship crossings through Bab-Al Mandab, matched by a rise in traffic diverting around the Cape of Good Hope.

Day to day, I chaired weekly coordination meetings with documented actions to prevent duplication, tracked via Kanban boards, and ran separate technical sessions for deeper methodological discussion so policy colleagues weren't overwhelmed while analysts kept room to brainstorm complex problems. I reviewed code directly on GitLab, and ran one-to-ones alongside the group sessions specifically as a channel for anything someone wouldn't raise in the wider meeting. For non-technical colleagues in particular, I also restructured the shared catch-ups to lead with a plain-language summary before any technical detail, rather than assuming everyone could follow a discussion pitched at the analysts.

A few months before the scheduled publication date, we found data quality issues serious enough that ONS — the statistical body and the report's direct publisher — was concerned about the reputational risk of releasing low-quality data under its name. This was the one real point of friction in the project: ONS's institutional caution against the pressure the wider team felt to deliver on schedule. Rather than treat it as a standoff, I redirected effort toward extensive conversations with the data provider to get an accurate picture of the issues, and used that evidence to put forward a middle option rather than a full go/no-go choice. One data source turned out to be too uncertain to include; the trade-off I recommended was to delay the full publication while still releasing a smaller, high-confidence subset of key straits rather than holding everything back. I put that recommendation forward. ONS and the senior stakeholders made the actual sign-off, and it's what we published on.

To recognise the team's effort through that period, I nominated our work for the Analysis in Government Awards, and later presented the approach directly to Swedish government colleagues exploring something similar — both concrete forms of visibility for people whose day-to-day reporting line sat elsewhere.

Partway through the project, the G7 who would normally have sat above me in this work left the role early. I informally picked up some of the coordination and escalation that would have gone through them, referring certain matters directly to our G6 instead — there was no formal acting arrangement, I simply absorbed it into how I was already running the project.

**What worked, and what I'd change:** dividing work by each department's comparative expertise, rather than trying to standardise everyone's role, was the right call — it's why DBT, ONS, and DfT could each contribute at the depth they did. The clearest miss was timing: we didn't get a proper data quality pipeline in place until relatively late, which is exactly why the quality issues surfaced close to the deadline rather than early enough to resolve without schedule pressure. If I ran this again, that pipeline would be one of the first things built, not a mid-project addition.
