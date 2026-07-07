---
company: Department for Business and Trade
context: dq-agent — independent data-quality contract-authoring toolkit (currently pitching at division level / Firebreak, not yet adopted)
tags:
  [
    genai-agent,
    llm-orchestration,
    security-by-design,
    data-quality,
    changing-and-improving,
    seeing-the-big-picture,
    leadership-initiative,
    human-in-the-loop,
  ]
source: https://github.com/JBarone90/dq-agent (public demo on main; the department's air-gapped Bedrock deployment is on branch feat/bedrock-proxy-adapter)
---

# AI

I identified a standing gap in the department: no standard process for building data-quality monitoring pipelines. Two causes stood out. First, there was no shared rule vocabulary or infrastructure — every team that wanted data quality checks built its own from scratch. Second, there's a structural gap between the people who understand a dataset (analysts, domain owners) and the people who know how to build and operate a monitoring pipeline (engineers), so getting from "we should check this" to a running pipeline routinely stalled.

I built an independent project, dq-agent, to address both causes, and I'm currently pitching it — first at division level, then at the department's quarterly Firebreak sessions, a cross-working slot for projects that don't sit inside any one team's roadmap.

The tool splits into two phases that never run at the same time. A deterministic layer defines quality rules as YAML "contracts" against a small, tested rule registry (checks like null rate, uniqueness, range, allowed values, regex match, freshness), executed with Polars, with connectors for both local CSV files and our Postgres estate, and full unit and integration test coverage. On top of that sits a scoping layer: a LangGraph agent that converses with a non-technical data owner, profiles their dataset, and proposes a contract in that same YAML format for the deterministic engine to run.

I deliberately narrowed the agent's tool access to match the department's data-handling requirements. It only ever sees a redacted profile of the data (aggregates and hints, never raw cell values) and can only select from the existing, validated rule registry rather than write novel code, so it's structurally impossible for the model to see sensitive values or introduce ungrounded logic into a pipeline. A human approval gate sits between a proposed contract and a usable one: the agent pauses and presents the draft rules in plain English alongside the full YAML, and only a human "approve" persists it. A schema snapshot is attached at approval time, so if the data later drifts, the engine refuses to run the now-stale contract rather than silently checking against outdated assumptions.

Because our production models run through an internal Bedrock proxy on an air-gapped network, I built a Bedrock-backed model adapter (Claude via the internal proxy) as a swap-in for the public repo's Gemini dev default, and moved the interface off the npm-based chat UI I'd used locally onto a terminal CLI and a Streamlit chat panel, both running entirely in-process without external package registries.

The project is at prototype/pitch stage, not adopted: the deterministic engine and profiler are complete and tested, the scoping agent and approval gate are a working demo, and I haven't yet had the division or Firebreak feedback that would tell me whether it gets picked up.
