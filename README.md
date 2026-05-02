# AI‑Based Tender Generator for Bachelor’s/Master’s Theses

This repository provides a **high‑level overview** of the AI‑based Tender Generator used at the Production Engineering of E‑Mobility Components (PEM) chair to automate the creation of professional thesis tenders.  It contains design documentation, diagrams and usage guides, but **not** the proprietary source code.

## Motivation and main goal

The Tender Generator streamlines the production of branded announcements for bachelor’s and master’s theses.  Users enter a title, short free‑text descriptions of the **Initial Situation** and **Your Task**, choose a language (English or German), provide a contact name and select an image folder.  The system leverages a GPT model to expand and polish the descriptions and fills a PowerPoint template using `python‑pptx`【241218893498853†L46-L66】.  The architecture deliberately separates content generation, configuration, and slide filling, ensuring flexibility and maintainability.

## Key features

* **User‑friendly web form**.  The browser‑based UI prompts for language selection, announcement title, short descriptions, contact name and an image folder【241218893498853†L69-L90】.
* **GPT‑based text generation**.  The generator expands the initial situation and task descriptions into concise paragraphs with predefined word limits【241218893498853†L46-L66】.
* **Privacy‑preserving pseudonymisation**.  A deterministic SHA‑256‑based anonymizer hashes the contact name before it ever leaves the browser and again on the server; clear‑text names never appear in prompts or logs【241218893498853†L119-L136】.
* **Optional grounding**.  The application can briefly search publicly available PEM/RWTH thesis postings and PDFs to ground the generated text with up‑to‑date phrasing【241218893498853†L100-L113】.
* **Template‑driven slide filling**.  A PPTX renderer fills placeholders in branded EN/DE templates and optionally inserts a single image on the first slide【241218893498853†L60-L66】.
* **Configurable providers and paths**.  Settings such as API provider (Azure or OpenAI), keys, output directory and image root are stored in a `config.ini` and `.env` under `C:\ProgramData\PEM_TenderGenerator`【241218893498853†L150-L190】.
* **Secure by design**.  API keys are kept in `.env`, directories under `ProgramData` should be restricted to administrators, and no clear‑text names are logged【241218893498853†L236-L244】.

## Repository contents

| File/Folder | Description |
|------------|-------------|
| `README.md` | This overview. |
| `CHANGELOG.md` | Version history for the Tender Generator documentation. |
| `LICENSE.md` | Copyright and usage information. |
| `NOTICE.md` | Legal notices and acknowledgements. |
| `docs/architecture.md` | Detailed architecture description with diagrams【241218893498853†L248-L280】. |
| `docs/user-workflows.md` | Step‑by‑step user guide for operating the Tender Generator【241218893498853†L69-L99】. |
| `docs/deployment.md` | Instructions for installation, configuration and running the application【241218893498853†L150-L236】. |
| `docs/security-and-privacy.md` | Best practices for protecting secrets and personal data【241218893498853†L119-L144】. |
| `docs/portfolio-evidence.md` | Summary of technical achievements and professional highlights. |
| `docs/github-repository-description.txt` | Short professional description for the GitHub repository listing. |
| `docs/assets/` | PNG versions of architecture and flow diagrams. |
| `docs/diagrams/` | Source diagram files (e.g. .dot). |

The actual program code is intentionally omitted.  For access to executables or source code, please contact the author under appropriate NDA/licensing terms.

## Copyright

© 2026 Martin Khadjavian – All rights reserved.  This repository is provided for documentation purposes only; reproduction or distribution of the underlying software requires written permission.