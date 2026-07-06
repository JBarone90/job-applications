---
company: Office for National Statistics
context: Weekly economic bulletin — Reproducible Analytical Pipeline (RAP) build
tags: [automation-rap, python-r, quality-assurance, change-management, team-leadership, communicating-and-influencing, managing-a-quality-service, changing-and-improving]
---

At the ONS, a weekly economic bulletin covering real-time UK indicators was produced through error-prone Excel workflows. The bulletin tracked unofficial statistics introduced during the pandemic, when traditional metrics were too slow, spanning over fifteen datasets including banking transactions, job advertisements, shipping, and energy consumption. With tight publication deadlines and complex ad-hoc processes, quality assurance was difficult, creating both operational risk and stress within the team.

I was tasked with leading the development of automated analytical pipelines (RAP) to replace existing manual workflows while maintaining the weekly publication schedule and ensuring analytical consistency.

I designed and developed a bespoke Python package featuring comprehensive documentation (Sphinx), robust testing (pytest), and modular functions built on pandas and numpy. This enabled reusable yet flexible pipelines for diverse datasets. To enhance data quality, I introduced an R-based seasonal adjustment process using TRAMO-SEATS, improving trend extraction and interpretability. Implementation followed an incremental approach, with two data-science teams coordinating through GitLab for version control and peer review.

Initial resistance emerged from the production team, who lacked technical skills to run and interpret code-based solutions under time pressure. Through several meetings, I recognised their concerns and I proposed Power BI as the front-end RAP tool. I built a dashboard template connected to the secure SharePoint environment, presenting standardised metrics, tables, and charts. Through hands-on demos and discussions, I reassured colleagues that the new system would streamline their work and free up capacity for bespoke analysis and upskilling.

Within nine months, data-processing time fell from days to minutes across all datasets, with a marked improvement in reliability and reproducibility. The production team acquired new analytical skills, particularly in Power BI, and adopted sustainable practices such as version control and automated testing, ensuring the bulletin's timely, high-quality delivery long after project completion.
