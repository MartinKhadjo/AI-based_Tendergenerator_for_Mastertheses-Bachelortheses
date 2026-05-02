# Architecture

This document describes the high‑level architecture of the AI‑based Tender Generator and the interactions between its components.  The design emphasises separation of concerns, privacy and configurability.

## Overview

The Tender Generator is a Flask web application that collects user inputs via a browser, uses a GPT model to generate polished text, and fills a PowerPoint template with the help of `python‑pptx`.  Its primary modules are:

* **Web layer** – HTML pages (`index.html`, `success.html`), CSS and static assets that collect user inputs and display the download page【241218893498853†L69-L90】.
* **Controller (`announcer_fixed.py`)** – Flask routes that handle form submissions (`POST /`), manage configuration, call the GPT provider and orchestrate PPTX generation【241218893498853†L248-L280】.
* **Text generation** – GPT calls to expand the Initial Situation and Task descriptions into coherent paragraphs with word limits【241218893498853†L46-L66】.
* **Optional grounding** – A search routine that fetches context from public PEM/RWTH thesis postings and PDFs and blends it with user input【241218893498853†L100-L113】.
* **Anonymizer (`anonymizer.py`)** – Deterministic SHA‑256 pseudonymisation of the contact name used both client‑side and server‑side【241218893498853†L119-L136】.
* **Configuration loader (`tender_config.py`)** – Reads `config.ini` and `.env` from `C:\ProgramData\PEM_TenderGenerator` to configure provider credentials, output directories, image root and template paths【241218893498853†L150-L236】.
* **Template management and PPTX renderer** – Functions that select the EN or DE template, replace placeholders, insert an optional image and save the finished PPTX【241218893498853†L60-L66】【241218893498853†L269-L274】.

![Architecture Overview](assets/architecture-overview.png)

## Component details

### Web layer

The user interacts with two main pages:

* **Form page** (`index.html`) – Presents input fields for language, announcement title, two text fields, contact name and image folder.  An optional button shows the anonymised contact name using client‑side hashing【241218893498853†L69-L94】.
* **Success page** (`success.html`) – After generation, displays a download link for the generated PPTX【241218893498853†L95-L99】.

These pages are rendered by Flask using Jinja2 templates and static CSS/JS.

### Controller and generation pipeline

The controller in `announcer_fixed.py` orchestrates the generation:

1. **Parse request**.  When the form is submitted (`POST /`), the controller reads the fields and loads settings from `tender_config.py`【241218893498853†L248-L280】.
2. **Initialize provider**.  Depending on `OPENAI_PROVIDER`, it sets API base, version and keys for Azure OpenAI or public OpenAI【241218893498853†L150-L190】.
3. **Anonymize**.  Before constructing prompts, it pseudonymises the contact name to a deterministic alias【241218893498853†L119-L136】.
4. **Optional grounding**.  The controller may fetch context snippets from public thesis postings and PDFs【241218893498853†L100-L113】.
5. **Generate texts**.  It calls the LLM twice to produce the Initial Situation and Your Task paragraphs within specified word limits【241218893498853†L60-L66】【241218893498853†L248-L280】.
6. **Template selection**.  The language choice determines which PPTX template (DE or EN) and mapping file to load【241218893498853†L269-L271】.
7. **Slide filling**.  The system fills placeholders with the generated text, inserts an image from the selected folder (if provided) and saves the presentation【241218893498853†L269-L274】.
8. **File delivery**.  The generated PPTX is saved to `OUTPUT_DIR` with a timestamped filename, and the user is redirected to `/success/<filename>`【241218893498853†L274-L279】.

### Configuration and provider management

Configuration values are stored in `config.ini` and `.env` in the `ProgramData` directory【241218893498853†L199-L236】.  Key parameters include API keys and endpoints, output and image directories, and template paths【241218893498853†L214-L226】.  Administrators should protect this folder and treat API keys as secrets【241218893498853†L236-L244】.

### Anonymizer

The anonymizer uses a fixed salt and SHA‑256 to generate a pseudonym for the contact name.  Both the browser and server implement the same algorithm to ensure that names are never transmitted in clear text【241218893498853†L119-L136】.  The pseudonym (e.g., `ANON_7C3A_...`) is used consistently in prompts and logs, and is deterministic but not reversible【241218893498853†L282-L304】.

## Processing flow

The following diagram summarises the end‑to‑end processing flow:

![Processing Flow](assets/processing-flow.png)

1. **User input** – The user enters the language, title, descriptions, contact name and image folder and submits the form【241218893498853†L69-L90】.
2. **Load config & provider** – The server loads settings from `tender_config.py` and initialises the selected API provider【241218893498853†L248-L280】.
3. **Anonymise & gather context** – It pseudonymises the contact name and optionally fetches external context from thesis postings【241218893498853†L100-L113】【241218893498853†L119-L136】.
4. **Generate text** – The LLM produces the initial situation and task paragraphs with word limits【241218893498853†L60-L66】.
5. **Select template** – Based on the chosen language, the system loads the corresponding PPTX template and mapping【241218893498853†L269-L271】.
6. **Fill & save** – Placeholders are filled, an image is inserted and the PPTX is saved【241218893498853†L269-L274】.
7. **Redirect** – The user is redirected to the success page, where they can download the presentation【241218893498853†L274-L279】.

This modular design allows each step to be updated independently and ensures that sensitive information is never mishandled.