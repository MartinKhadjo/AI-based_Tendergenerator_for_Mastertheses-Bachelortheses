# Security and Privacy

## Core privacy feature
The standout privacy feature of the Tendergenerator is deterministic pseudonymization of the contact name.
Before the LLM is called, the server replaces the real name with a stable alias.
The same logic is also available client-side for preview.

## Why this matters
This reduces the exposure of personally identifiable information in prompts and logs, and it demonstrates that the product was engineered with privacy in mind rather than treating privacy as an afterthought.

## Security-relevant observations from the manual
- only administrators should modify configuration files,
- AI provider credentials must be treated as secrets,
- output paths should be access-controlled,
- logs should avoid clear-text personal data,
- users should avoid placing sensitive data into free-text fields.

## Public-safe security guidance
For a production environment, the following best practices are appropriate:
- keep credentials out of version control,
- restrict write access to configuration locations,
- log minimally and safely,
- review data-handling obligations for the selected provider,
- separate public portfolio materials from any internal operational artifacts.
