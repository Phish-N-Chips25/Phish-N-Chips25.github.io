---
title: "Challenge 3 · Week 2: New Team Member and Project Definition"
description: "Welcoming Rynalde Gabriel Silva Serejo and defining our actual project — a cyber-physical surveillance system combining Windows log anomaly detection with face recognition."
category: "Challenge 3"
pubDate: 2026-03-08
heroImage: "../../images/blog/challenge-3-week-2.svg"
---

## Welcome, Rynalde

On **4 March 2026**, our team received a message that immediately brightened the week:

> *"Olá a todos,*
>
> *O meu nome é Rynalde Gabriel Silva Serejo e sou um estudante internacional do Brasil. Estou a participar num programa de dupla titulação e estarei a estudar no ISEP durante este semestre.*
>
> *Fui integrado na Equipa 10, na área de Cibersegurança, e gostaria de me apresentar e começar a integrar-me melhor no grupo, para poder colaborar e contribuir no desenvolvimento dos trabalhos da equipa.*
>
> *Tenho alguns conhecimentos em fundamentos de cibersegurança, adquiridos no Mesa Community College, no Arizona (Estados Unidos), e atualmente estudo Engenharia da Computação no Brasil.*
>
> *Caso exista algum grupo de WhatsApp ou outra plataforma que estejam a usar para comunicar e organizar o trabalho, agradecia que me pudessem adicionar.*
>
> *Obrigado e fico à disposição para ajudar no que for preciso.*
>
> *Cumprimentos"*

Rynalde is a **double-degree student** spending the semester at ISEP as part of an international exchange programme. He is currently pursuing a degree in **Computer Engineering in Brazil** and previously gained cybersecurity fundamentals at **Mesa Community College in Arizona, USA**. His background is an excellent fit, and his international perspective adds real value to the team dynamic.

## Defining the Project

Beyond the onboarding, this week was primarily a **project definition session**. Challenge 3 requires a joint scientific article for the two UCs, and agreeing on scope early is critical. After intense discussion, we converged on a clear and ambitious direction rooted in the IDS proposal chosen in Week 1.

### Cyber-Physical Surveillance System

Our project will build a **unified cyber-physical surveillance system** composed of two complementary and independently evaluated modules:

### Module 1 — Windows Endpoint Log Anomaly Detection

Traditional security architectures treat network intrusion detection and physical access control as separate problems. Our first module targets the **digital layer**: detecting suspicious or malicious activity within Windows hosts by analysing telemetry from **Sysmon** and **Event Tracing for Windows (ETW)** — high-fidelity sources recording process creation, network connections, file operations, and registry modifications.

Uniquely, we chose to compare **two fundamentally different detection approaches**:

- **Classical ML pipeline** — Isolation Forest (unsupervised, one-class) and a GRU autoencoder trained on normal-only data; both extract structured features from fixed log windows.
- **Dual Sentinel** — a fully LLM-native pipeline where **Phi-3 Mini** (a compact ~4B-parameter SLM by Microsoft) acts as a first-pass analyst and **Llama 3.2** (~8B parameters by Meta) acts as a judge that validates the analyst's findings and maps suspicious behaviour to **MITRE ATT&CK** techniques, generating natural-language explanations.

The comparison directly addresses a gap in the literature: statistical models score anomalies but provide no semantic insight, while LLMs offer interpretability but risk hallucination in security-critical settings.

### Module 2 — Physical Access Control via Face Recognition

The second module targets the **physical layer**: a camera-based face recognition pipeline for access control. We will compare two paradigms:

- **Closed-set approach** — deep convolutional models (FaceCNN and ResNet-50) trained end-to-end via ArcFace loss on VGGFace2, using a softmax head for identity classification.
- **Open-set approach** — InsightFace's pre-trained ArcFace model performing verification via cosine similarity against enrolled gallery centroids, supporting dynamic enrollment and natural rejection of unknown individuals without retraining.

### Dataset Selection

| Module | Dataset | Notes |
|---|---|---|
| Log anomaly detection | LMD-2023 | Real Sysmon logs with lateral movement scenarios |
| Log anomaly detection | AAU\_MalData | Additional malware telemetry traces |
| Log anomaly detection | ETW baseline | Normal operating condition logs collected locally |
| Face recognition | VGGFace2 | 15,236 images across 50 identities for training |

## Article Skeleton

We drafted the overall structure for the preliminary article (due 29 March):

- Title and authorship (6 authors: Arsénio Ferraz, Mário João, César Vieira, Gonçalo Jesus, Rui Soares, Rynalde Silva Serejo)
- Abstract
- Keywords
- Introduction — convergence of cyber and physical security, motivation for dual-module hybrid system
- Related Work — Windows telemetry, classical ML anomaly detection, LLMs in cybersecurity, LLM-as-judge, deep face recognition, open-set recognition
- System Architecture — classical pipeline, Dual Sentinel, face recognition
- Experimental Setup and Results
- Discussion and Limitations
- Conclusion + References

## Looking Ahead

With Rynalde integrated and the project scope defined, Week 3 will focus on building the **state-of-the-art section**, deep-diving into the relevant literature for all components and beginning to populate each article subsection.

---

*The project is defined. Six team members, two modules, one article. Let's build.*
