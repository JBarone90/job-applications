---
company: Office for National Statistics
context: Weekly economic bulletin — Reproducible Analytical Pipeline (RAP) build
tags:
  [
    automation-rap,
    python-r,
    quality-assurance,
    change-management,
    team-leadership,
    communicating-and-influencing,
    managing-a-quality-service,
    changing-and-improving,
    developing-self-and-others,
  ]
---

# Pipeline and Communicating

At the ONS, a weekly economic bulletin covering real-time UK indicators was produced through error-prone Excel workflows. The bulletin tracked unofficial statistics introduced during the pandemic, when traditional metrics were too slow, spanning over fifteen datasets including banking transactions, job advertisements, shipping, and energy consumption. With tight publication deadlines and complex ad-hoc processes, quality assurance was difficult, creating both operational risk and stress within the team.

I led development of automated analytical pipelines (RAP) to replace existing manual workflows while maintaining the weekly publication schedule and ensuring analytical consistency.

I designed and developed a bespoke Python package featuring comprehensive documentation (Sphinx), unit and integration testing (pytest), and modular functions built on pandas and numpy. This enabled reusable yet flexible pipelines for diverse datasets. To enhance data quality, I introduced an R-based seasonal adjustment process using TRAMO-SEATS, improving trend extraction and interpretability. Implementation followed an incremental approach, with two data-science teams coordinating through GitLab for version control and peer review.

Initial resistance emerged from the production team, who lacked the technical skills to run and interpret code-based solutions under time pressure, and were, understandably, wary that automation might make their role redundant. I hadn't been asked to manage that relationship — I'd been commissioned to build the automation. But the project wouldn't have landed without it, so over several meetings I worked on building trust with the team directly, rather than just pushing the tooling through. I proposed Power BI as the front-end RAP tool partly because it kept them in a familiar interface, built a dashboard template connected to the secure SharePoint environment presenting standardised metrics, tables, and charts, and ran hands-on demos to show concretely that the system was taking repetitive work off their plate, not their jobs — freeing their time for the parts of the role they found more interesting anyway, like custom reporting and deeper analysis. I also directly supported several of them in picking up Power BI themselves, rather than leaving them to work it out alone.

Within nine months, data-processing time fell from days to minutes across all datasets, with a marked improvement in reliability and reproducibility. The production team built real capability in Power BI with my direct support, and adopted sustainable practices such as version control and automated testing, ensuring the bulletin's timely, high-quality delivery long after project completion.
