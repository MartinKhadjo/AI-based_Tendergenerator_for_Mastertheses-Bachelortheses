# Portfolio Evidence

This repository is designed to showcase the architecture and design quality of the Tender Generator without exposing proprietary code.  It highlights key achievements and engineering practices to demonstrate capability for prospective employers and collaborators.

## High‑level capabilities

* **AI‑augmented document generation** – Utilises GPT models to transform short, user‑provided descriptions into polished tender sections【241218893498853†L60-L66】.
* **Modular architecture** – Separates the web layer, controller, anonymisation, configuration and template management into distinct modules【241218893498853†L248-L280】.  This separation eases maintenance and allows each part to evolve independently.
* **Internationalisation** – Supports both English and German templates and can be extended to additional languages through parameterised mappings【241218893498853†L79-L82】.
* **Privacy by design** – Implements deterministic pseudonymisation to ensure names are never exposed to the language model or stored in logs【241218893498853†L119-L136】.
* **Extensibility** – Optional grounding enables the system to incorporate fresh context from publicly available thesis postings and PDFs【241218893498853†L100-L113】.
* **Configurable deployment** – Uses INI and ENV files for configuration; administrators can adjust providers, API versions and file paths without modifying code【241218893498853†L199-L236】.

## Engineering highlights

* **Configuration isolation** – All secrets and environment‑specific settings live outside of the codebase (`config.ini`, `.env`), aligning with the [12‑factor app](https://12factor.net/config).
* **Pseudonymisation algorithm** – A simple, deterministic SHA‑256 hash with an internal salt produces a consistent alias; both client and server use the same routine【241218893498853†L288-L297】.
* **Stateless generation** – Each request is self‑contained; the server loads configuration, anonymises inputs, calls the GPT provider and writes the output file, leaving no session state on the server.
* **Defensive file handling** – Only valid image formats are accepted; invalid or unsupported formats are rejected or converted, ensuring the PPTX remains intact【241218893498853†L272-L274】.
* **Cross‑platform templating** – Uses `python‑pptx` to fill placeholders in PowerPoint templates; slide layouts are decoupled from generation logic for flexible design【241218893498853†L60-L66】.

## Suggested improvements

While the core system is robust, the following enhancements could further strengthen the Tender Generator:

1. **Additional field anonymisation** – Extend the pseudonymisation module to other sensitive fields (e.g., email addresses)【241218893498853†L300-L302】.
2. **Validation and sanitisation** – Enforce stricter input validation for free‑text fields to prevent prompt injection or malicious content.
3. **Monitoring and metrics** – Add structured logging and metrics around generation times and error rates to aid in performance tuning and troubleshooting.
4. **User‑controlled word limits** – Allow administrators to configure word limits for the generated sections via the settings file.
5. **Integration with internal services** – Provide connectors to internal thesis management systems for automatic posting or tracking.

These suggestions reflect standard software engineering practices and do not reveal any proprietary algorithms.