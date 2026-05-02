# Architecture

## Objective
The Tendergenerator automates the creation of thesis tender PowerPoints while preserving branded formatting, language-specific templates, privacy-aware text generation and a simple browser workflow.

## High-level flow
The system can be understood as five cooperating layers:
1. **Web UI** – data capture in the browser
2. **Application layer** – form handling, orchestration and routing
3. **Privacy layer** – deterministic pseudonymization of the contact name
4. **Generation layer** – LLM-assisted text creation
5. **Rendering layer** – template filling and PPTX export

## Runtime sequence
![Sequence diagram](assets/sequence-diagram-form-submission.png)

The sequence diagram from the manual shows the central interaction pattern:
- the user fills the form and submits it,
- the Flask application initializes the selected AI provider,
- input is anonymized and optional context is collected,
- the model generates tender-ready text for *Initial Situation* and *Your Task*,
- the PPTX layer fills a template and optionally inserts an image,
- the finished file is saved and returned through a success/download flow.

## Component hierarchy
![Component hierarchy](assets/component-hierarchy.png)

The component hierarchy highlights a maintainable modular structure:
- **Web layer**
  - `index.html` input form
  - `success.html` download page
  - `static/` for styling and visual assets
- **Generation pipeline**
  - `announcer_fixed.py` for routes and orchestration
  - `tender_config.py` for configuration loading
  - `anonymizer.py` for deterministic pseudonymization
- **Resources**
  - `templates/` for language-specific PowerPoint templates
- **Output**
  - generated `.pptx` files made available for download

## Architectural strengths
- simple but complete end-to-end workflow,
- privacy-aware design with deterministic anonymization,
- support for Azure OpenAI and public OpenAI,
- language-sensitive template switching,
- deterministic rendering after model generation,
- strong separation between input, generation and document rendering.

## Public-safe scope
This document intentionally omits reusable implementation details such as private prompt text, internal code logic and operational secrets.
