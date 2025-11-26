---
title: "Week 2:First Meeting with the Cybersecurity Expert: Key Insights on Phishing Detection"
description: "Documenting the meeting with our cybersecurity expert, Daniel Marques, and the key insights we gathered to guide our project."
category: "Challenge 1"
pubDate: '2025-10-03'
heroImage: "../../images/blog/expert-meeting.svg"
---

On **2 October 2025**, we held our first working session with **David Marques**, cybersecurity expert at Grupo Nabeiro, to discuss the foundations of our academic project on **phishing detection through URL analysis**.

The meeting was essential to validate our project’s scope, refine detection criteria, and gather insights from real-world practices.

---

## Project Presentation

Our team presented the project’s objectives and limitations:

- **Scope:** build a rule-based model to detect phishing URLs.
- **Goal:** design a tool that, given a URL, outputs whether it is likely phishing, supported by technical explanations.
- **Constraints:** academic context limits us to rule-based and visual analysis approaches, without advanced machine learning.

---

## Expert Contributions

David shared **practical techniques and indicators** used in professional environments to strengthen phishing detection, including:

- **Domain age and origin:** recently created or disposable domains are a red flag.
- **Redirection chains:** multiple hops often hide malicious intent.
- **Encrypted parameters in URLs:** a common evasion technique.
- **IPs in URLs:** rarer today but still relevant.
- **Use of alternative alphabets (e.g., Cyrillic):** often employed to mimic legitimate domains.
- **HTTPS certificates:** no longer a strong indicator, as free SSL is widely used by attackers.

He also emphasized that **static rules alone are insufficient**, recommending integration of additional tools and evolving detection methods.

---

## Tools and Professional Practices

David introduced us to **tools and platforms widely used in the industry**, such as:

- Microsoft Defender for Office
- VirusTotal
- MX Toolbox
- Cisco Talos

He explained how these solutions complement each other to validate domains, analyze reputations, and detect threats.

---

## Data Sharing and Next Steps

One of the most valuable outcomes of the meeting was David’s **commitment to share anonymized examples of benign and phishing URLs**, which will allow us to:

- Test and validate our detection rules.
- Benchmark our tool against real-world scenarios.

Additionally, David offered to share **metrics from phishing simulation campaigns** carried out within his organization, showing how they evaluate user awareness and tailor training.

---

## Conclusion

This meeting represented a turning point in our project:

- We validated our scope and constraints.
- We gained access to professional detection criteria.
- We secured real-world data to support our development and testing.

With David’s ongoing support, we are now better equipped to move from **theoretical design** to **practical implementation** of our phishing detection tool.

---

👉 **Next week’s focus:** integrating the expert’s feedback into our detection rules and preparing the first prototype of the tool.
