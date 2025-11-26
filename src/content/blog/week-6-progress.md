---
title: "Week 6: Rule Engines, Drools, and Prolog Refinements"
description: "Deepening our reasoning layer by prototyping Drools decision tables and refining Prolog rules for phishing detection"
category: "Challenge 1"
pubDate: 2025-10-25
heroImage: "../../images/blog/week-6-progress.svg"
---

## Week 6 Overview

This week revolved around **knowledge-based reasoning**. After consolidating our preliminary findings in Week 5, we shifted attention to building the rule engine layer that powers our **React front end**, where users paste a URL to see whether it is likely phishing. The agenda focused on two complementary technologies in the backend: **Drools** for business-friendly decision logic and **Prolog** for declarative inference.

## Drools Experiments

We started translating our cybersecurity heuristics into Drools artifacts:

- Modeled the first **decision table** covering indicators such as domain age, WHOIS privacy flags, URL length, and mismatched redirects.
- Captured the output actions as “risk levels” that the React UI can display instantly to the user.
- Set up a lightweight **Kogito-based playground** to run incremental tests directly from VS Code.
- Documented a repeatable approach for importing CSV-driven rules, making it easier for non-developers to tweak thresholds later.

### Key insights

1. **Salience management** is essential: overlapping rules needed explicit priorities to avoid contradictory risk labels.
2. **Fact modeling** must remain minimal: we refactored our `UrlContext` object so the same structure feeds both Drools sessions and future ML features.
3. **Unit tests** around corner cases (e.g., data URIs, unicode spoofing, excessive subdomains) caught multiple misfires early.

## Prolog Rule Refinement

In parallel, we revisited the Prolog prototype that previously encoded phishing red flags for URLs. This week’s work:

- Rewrote predicates to separate *evidence gathering* from *risk inference*, improving readability.
- Added **confidence weights** so multiple weak signals can accumulate into a medium-risk classification.
- Implemented recursive rules for link traversal analysis, letting us reason about nested redirects.
- Created a bridge script that exports Prolog conclusions to JSON, which Drools can ingest as supplemental facts before the front end renders the verdict.

### Challenges addressed

- **Variable naming collisions** had caused silent failures; we introduced scoped helper predicates.
- **Performance**: large URL batches slowed naive backtracking, so we memoized common lookups (e.g., known-good domains and CDN endpoints).
- **Consistency**: aligned taxonomy with Drools outputs so “Medium Risk” means the same thing across engines and the React UI.

## Integration Strategy

To keep both rule systems in sync we designed a “reasoning pipeline”:

1. **Prolog** evaluates structural and lexical URL cues, exporting intermediate facts.
2. **Drools** combines those facts with business policies and user-specific thresholds.
3. Results feed our React front-end via a REST stub that we plan to formalize next sprint.

We also drafted an **evaluation checklist** that includes:

- Coverage of top phishing patterns from the ENISA threat landscape reports.
- Regression scenarios for legitimate services (banking portals, SaaS dashboards, educational platforms) to avoid false positives.
- Hooks for future hybrid approaches where ML predictions become additional facts.

## Next Steps

- Connect the Drools service to our React/Node stack for end-to-end smoke tests.
- Automate Prolog regression suites using SWI-Prolog’s built-in testing framework.
- Gather feedback from our cybersecurity advisor to validate rule interpretability.
- Start drafting documentation for classmates so they can understand and critique our reasoning layer during the next checkpoint.

---

*Week 6 showcased how symbolic AI complements our ML plans. By refining Drools and Prolog rules in tandem, we’re building a transparent defense layer that we can explain, audit, and iterate quickly.*
