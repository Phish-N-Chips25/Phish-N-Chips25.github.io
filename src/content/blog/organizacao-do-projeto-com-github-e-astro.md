---
title: 'Week 1: Project Organization with GitHub and Astro'
description: 'In this article, we explain how we structured collaboration for the Master’s in Artificial Intelligence Engineering at ISEP. We detail the chosen tools (GitHub, Astro, and GitHub Pages) and show how they support an asynchronous, collaborative workflow that can grow with our Cybersecurity project.'
category: "Challenge 1"
pubDate: '2025-09-22'
heroImage: "../../images/blog/organizacao-do-projeto-com-github-e-astro.svg"
---

## Team Collaboration and Documentation Structure: GitHub + Astro

As part of our Master’s in Artificial Intelligence Engineering at ISEP, our team needed a centralized and reliable way to collaborate.
Since each of us has different schedules and availabilities, asynchronous work was essential. We wanted a structure that naturally supports code collaboration, documentation, and communication for software developers.

## Centralizing Collaboration with GitHub

Our first decision was to create a **GitHub Organization**.
This gave us a single “home” for all repositories—from prototypes and experiments to more solid code and documentation.

Why we chose this:

- **Version control**: GitHub’s *branch* and *pull request* workflow helps us manage changes safely.
- **Shared ownership**: All team members are *owners* of the organization, preventing bottlenecks if someone is unavailable.
- **Transparency and accountability**: Through *commits* and *pull requests*, it’s always clear who contributed to each part of the project.
- **Future scalability**: GitHub also offers *Projects*, *Issues*, and *Discussions*, which we can use later for more structured asynchronous coordination.

## Why We Chose Astro

For the blog and documentation, we ended up choosing **Astro**.
It seemed the best balance between simplicity and flexibility:

- **Markdown-first**: Writing in Markdown is fast and avoids formatting worries.
- **Integration with React (and more)**: When needed, we can use React components (or even Vue, Svelte, Solid). This leaves the door open for interactive dashboards or visualizations related to our project.
- **Previous experience**: Some of us had already used Astro, which made the learning curve easier.
- **Performance**: As a static site generator, it ensures fast and lightweight pages.

In short: Astro lets us focus on content now, but remains flexible enough to grow with us.

## Selection Criteria and Best Practices

Before settling, we considered other alternatives:

- **Docusaurus**: Great for documentation, but felt too rigid. Astro gives us more freedom and easily integrates React and Vue, which may be useful.
- **WordPress (free version)**: We considered it, but quickly realized it wasn’t suitable. Collaboration between multiple authors is limited and we wouldn’t have the same flexibility for dynamic components.
- **Vercel**: Was on the table, but seemed “overkill” for now. GitHub Pages covers the essentials and keeps everything in the same ecosystem.

We also defined some best practices to maintain consistency and quality:

- **Branching model**: We use the *main branch* for production, with automatic *deployments* to GitHub Pages.
- **Pull requests**: Even blog articles go through *pull requests*, ensuring collaborative review before publishing.
- **Site organization**: At this initial stage, we have three sections:
  - **Homepage**: A brief introduction to the team and our topic (Cybersecurity).
  - **Blog**: Where we publish articles, starting with the first *deadline*.
  - **About**: A page with information about team members.

## Security and Access Control

Besides simplifying *deploys*, GitHub provides **out-of-the-box security mechanisms** that avoid building (and maintaining) a *backoffice* just to manage blog access. All content lives in repositories with **granular permissions**, auditable via *commits* and *pull requests*.

To further strengthen security, we configured **branch protection rules** on `main`:

- Changes only go in via *pull requests*, never direct *push*.
- **Two approvals** are required before any merge, including mandatory *Code Owner* reviews.
- Old approvals become invalid if new *commits* are made.
- Merge is only possible after **required status checks** (lint and build).
- All review conversations must be resolved.
- Only *maintainers* can push, and only if *checks* pass.
- Not even administrators can bypass these rules.

This setup brings us closer to **DevSecOps** best practices, ensuring **integrity, traceability, and accountability** in all contributions.

## Hosting on GitHub Pages

To keep things simple, we decided to host everything on **GitHub Pages**.
It’s free, reliable, and fits directly into our workflow:

- It’s in the same ecosystem as our code.
- *Deploys* are automatic from the `main` branch.
- We don’t need to manage extra infrastructure while focusing on academic work.

## Next Steps

Our current setup covers the essentials: centralized code, documentation, and blog.
Still, we left room to evolve:

- Create **interactive dashboards** within the site, related to our project.
- Generate **diagrams directly in Markdown** using tools like [Mermaid](https://github.com/remcohaszing/rehype-mermaid), allowing us to keep diagrams versioned as code.
- Use **Projects, Issues, and Discussions** for task management and planning.

## Conclusion

Choosing a GitHub Organization for code and **Astro + GitHub Pages** for documentation gives us a **lightweight workflow adapted to asynchronous work**.
It’s a simple solution that meets our current needs and has room to grow as the project evolves.
