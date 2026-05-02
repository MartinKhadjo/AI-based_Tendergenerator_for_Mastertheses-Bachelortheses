# Security & Privacy

Protecting personal data and API credentials is a core requirement of the Tender Generator.  This page summarises how the system addresses privacy and outlines best practices for secure operation.

## Privacy by design

The only personally identifiable input is the contact name.  To prevent disclosure, the application applies a deterministic pseudonymisation scheme:

* **Client‑side pseudonymisation** – When you click *Show Anonymized Details*, the browser computes a SHA‑256 hash of the contact name with a fixed salt.  The resulting alias (e.g., `ANON_7C3A_…`) is displayed to the user【241218893498853†L119-L136】.  The raw name never leaves the browser during this preview【241218893498853†L292-L294】.
* **Server‑side pseudonymisation** – When the form is submitted, the server runs the same hashing routine before constructing prompts for the GPT provider【241218893498853†L295-L299】.  Only the alias is stored in logs or sent to the model【241218893498853†L298-L300】.
* **Determinism** – The same input always produces the same alias, which keeps the identity consistent across runs while preventing reversal【241218893498853†L288-L291】.

Avoid placing other sensitive personal data (student IDs, email addresses, phone numbers) into free‑text fields【241218893498853†L137-L140】.  The pseudonymiser currently applies only to the contact name, but the code could be extended to additional fields【241218893498853†L300-L302】.

## Data handling

* **No raw names in logs** – The server writes only aliases and error messages to `app.log`; real names are never persisted【241218893498853†L299-L300】.
* **Optional context fetch** – The optional search routine downloads publicly available thesis postings and PDFs for context.  It uses only publicly accessible pages and does not transmit user data【241218893498853†L100-L113】.

## Securing credentials & configuration

* Store API keys (Azure or OpenAI) in the `.env` file under `C:\ProgramData\PEM_TenderGenerator` and ensure this directory is restricted to administrators【241218893498853†L178-L236】.
* Never commit API keys or secrets to version control【241218893498853†L241-L242】.
* Use strong permissions for the output and image directories, especially when they reside on network shares【241218893498853†L223-L230】.
* Restart the application after editing configuration files to apply changes【241218893498853†L231-L236】.

## Limitations

Pseudonymisation mitigates the risk of exposing contact names but does not guarantee absolute privacy【241218893498853†L143-L145】.  Always use neutral, non‑identifying language in free‑text fields.