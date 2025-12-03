---
title: "Week 7: Chrome Extension and Submission Sprint"
description: "Porting our phishing URL checker into a Chrome extension while preparing all November 2 deliverables"
category: "Challenge 1"
pubDate: 2025-11-01
heroImage: "../../images/blog/week-7-progress.svg"
---

## Week 7 Overview

With the reasoning layer stable, Week 7 focused on **meeting the early-November deliverables** and expanding our reach through a **Chrome extension** that mirrors the React web client. The calendar was intense—work report, article, and pitch submissions are all due on **2 November at 23:59**, so every task this week was scoped around that deadline.

## Chrome Extension Prototype

We built a lightweight extension so users can classify URLs without leaving the browser:

- Replicated the React UI workflow inside a popup using the same shared components.
- Leveraged the background script to call our Drools/Prolog service, ensuring HTTPS-only requests and graceful fallbacks when offline.
- Added context-menu support so users can right-click a link and send it to the classifier instantly.
- Documented installation steps for classmates so they can try it before Demo Day.

### Technical takeaways

1. **State reuse worked** thanks to an internal library that exposes the URL validation hooks used by both the website and the extension.
2. **Performance profiling** showed the rule-engine round trip averages 320 ms, which meets our UX target.
3. **Security hardening** included CSP updates and strict permission requests (`activeTab` + custom API endpoint only).

## Deliverables Countdown

Alongside coding, we tackled the submission queue required by the discipline:

- Finalized the **work deliverable** and the **article** for Moodle (both due 2 November).
- Drafted the **pitch script** and recording plan so we can upload the video to both UC spaces before the same deadline.
- Created a checklist for the **Challenges4Teams (ENGCIA) submission**, outlining the ZIP (COD-TEAM-10.zip) and the PDF report (REL-TEAM-10.pdf).
- Reserved time to rehearse for the **course event** and align messaging across the website, extension, and documentation.

## Risk Mitigation

- **Packaging risks**: automated a GitHub Action that zips the latest tagged release to avoid last-minute packaging mistakes.
- **Scope creep**: kept the extension features identical to the website to minimize regression risk.
- **Documentation debt**: paired every new feature with README updates so the submission bundle stays consistent.

## Next Steps

- Conduct end-to-end tests covering both the React app and the Chrome extension.
- Freeze copy for the Moodle submissions and schedule final peer review on 2 November morning.
- Record the pitch demo and verify audio levels ahead of the upload window.
- Begin assembling the evidence for Monday’s implementation presentations (3 November) and the Demo Day pitch on 4 November.

---

*Week 7 was all about parallel execution—shipping the extension, polishing content, and ensuring every required asset will be ready for the early-November deadlines.*
