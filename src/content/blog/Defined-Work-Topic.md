---
title: 'Kickoff: Choosing Our Cybersecurity Project'
description: 'Why this blog runs on Astro and the two cybersecurity themes we evaluated for our team project'
category: "Challenge 1"
pubDate: '2025-09-20'
heroImage: "../../images/blog/defined-work-topic.svg"
---
We’re launching our Master’s in AI team project blog to document our progress. We picked [**Astro**](https://astro.build/) to keep writing fast and the site fast, while leaving room for small changes in theme and functionality.

Our team’s cybersecurity theme was split across two candidate directions:
1. An **expert system for phishing-URL detection** that inspects both the URL and its landing page for suspicious behavior;

2. A **network intrusion detection/prevention system** focused on monitoring traffic, alerting on anomalies, and safely blocking attacks (e.g., DDoS or MitM attacks).

Below we summarize why Astro is our framework of choice and provide an overview of both the topics we considered and why we chosen our theme.

---

## Why use Astro for this blog?

When Prof. Carlos Ramos asked for a blog to record our work process, we wanted a simple framework which was basically a "document eater" with customizable themes and components and easy to deploy. Thankfully, our colleague Bruno Camarneiro knew just the right tool.

**Astro** is a JavaScript framework allows for seamless integration with UI frameworks, such has React, Vue, Angular and others, as well as deployment adapters such as GitHub Pages, AWS, Vercel, etc.

Most importantly, it accepts Markdown and MDX files as is which makes it extremely easy for making posts in our blog, since we can integrate the page with Hyperlinks, images, graphs, tables and code, all in the same document. Additionally, MDX lets us use Typescript with our markdown text, which we can use to further customize it. It also provides some performance qualities, but that is not our main concern with this blog.

All in all, **Astro** simplifies our work in logging our activities and maintain the website, since all its needed is a markdown file and the framework does all the heavy lifting.

---

## Considered topics for our Team Project

Choosing topics that involve Cybersecurity and Artificial Intelligence is not challenge, the problem lies on choosing a topic that is not only relatively simple (since we only have 8 weeks and not a lot of background knowledge in AI) but at the same time be useful and provide value. As such, we decided to use the knowledge we will gather throughout this 8 weeks to build an **expert system on phishing/URL.**

### First Topic - Phishing-URL Expert System

The main goal of this system is really simple, detect and alarm the user for phishing links/URLs. In order to accomplish this, the system would have to analyze domains and subdomains of a link, redirects, DOM of the webpage the links redirects to, obfuscated JS and other features in order to make it's prediction.

Finally, if times permits, we would like to incorporate this system within a browser extension, which allows an user to activate the system at will, at any webpage or while reading an email, providing inference in useful time.

---

### Second Topic — Network IDS/NIPS

Another proposed direction was to design a system that can automatically detect and mitigate malicious activity on a network: a **Network Intrusion Detection/Prevention System (NIDS/NIPS)**.

The idea is to observe inbound and outbound traffic (via packet capture or flow summaries), identify signs of attacks such as **DDoS**, **Man-in-the-Middle**, **spoofing**, **host/port scans**, etc, and then apply guarded responses (temporary rate limits, blocklists) with clear audit logs.

Given the **8-week** timeline, we concluded this topic to be way to complex for what we can deliver right now. To maximize explainability and time-to-value, we chose to prioritize the **Phishing/URL Expert System** for this group project, keeping the NIDS/NIPS track as future work once we have more time and experience for safe evaluation and hardening.

---
