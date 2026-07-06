---
company: Department for Business and Trade
context: Self-service containerised shipping dashboard, working with DfT and ONS Data Science Campus
tags:
  [
    project-delivery,
    cloud-databricks,
    data-quality,
    accessibility,
    stakeholder-consultation,
    seeing-the-big-picture,
    changing-and-improving,
  ]
---

# Project management & Technical skill - Programming

Leading impactful data science projects from inception to production by setting a clear direction and delivering on milestones.

At DBT, I led development of a self-service containerised shipping dashboard that transformed how policy teams accessed critical trade data. Previously, my three-person team was the department's sole expert resource, creating bottlenecks when multiple ministers needed simultaneous insights.

I managed the full project lifecycle over one year, from stakeholder consultation through iterative development to deployment. Through meetings with DBT colleagues and external partners at DfT and ONS Data Science Campus, I gathered requirements and proposed building an MVP with continuous feedback cycles.

Development required building extensive data validation and preprocessing pipelines in Python. First, in Databricks, I developed a three-tier PySpark framework capturing metadata, rule-level results, and targeted JSON snapshots of failing rows for efficient debugging. Then, for the departmental platform, I built modular preprocessing using pandas with comprehensive type hinting, custom error handling, and a full pytest test suite. All code was version-controlled via GitLab with CI pipelines automating tests and formatting checks.

These pipelines revealed significant issues with data quality. Recognising this as critical, I temporarily shifted focus to data validation, comparing versions across years to identify drift (hypothesis testing), and documented findings for the data provider to address before continuing development.

For the dashboard interface, I used Streamlit for rapid prototyping, Postgres for data ingestion, and implemented caching and callback functions to optimise performance. I ensured accessibility through custom HTML/CSS with screen-reader features and colour-blind-safe palettes.

The dashboard now serves as a central asset for multi-team crisis response, substantially reducing analytical turnaround times and transforming data issue detection from months to immediate identification.
