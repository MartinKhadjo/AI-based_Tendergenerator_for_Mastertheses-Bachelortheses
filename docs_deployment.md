# Deployment & Configuration

This guide is intended for system administrators who install and maintain the Tender Generator.

## Installation with Inno Setup

Run `PEM_Tendergenerator_Setup.exe`.  The setup wizard guides you through the following steps【241218893498853†L150-L171】:

1. **Output and image folders** – Choose where generated PPTX files are written (UNC or local path) and optionally a root folder containing subfolders of images【241218893498853†L153-L158】.
2. **Server bindings** – Specify the host and port.  Use `0.0.0.0` and port `5000` to make the app accessible on your network【241218893498853†L159-L161】.
3. **Provider & credentials** – Select `azure` or `openai` and enter the corresponding API base/version/key and deployment name or model name【241218893498853†L162-L190】.  Azure deployments require specifying an API base (e.g., `https://<resource>.openai.azure.com`), API version and deployment name; public OpenAI requires a model name (default `gpt-4o`) and API key【241218893498853†L167-L188】.
4. **Firewall rule** – The installer opens a Windows firewall rule for inbound TCP on the chosen port【241218893498853†L191-L193】.

After installation, a primary `config.ini` and `.env` file are placed in `C:\ProgramData\PEM_TenderGenerator`【241218893498853†L199-L214】.

## Post‑installation configuration

You can edit `.env` or `config.ini` at any time to adjust:

* `OPENAI_PROVIDER` – `azure` (deployment‑based) or `openai` (model‑based)【241218893498853†L212-L220】.
* **Azure settings** – `AZURE_OPENAI_API_BASE`, `AZURE_OPENAI_API_VERSION`, `AZURE_OPENAI_API_KEY`, `AZURE_OPENAI_DEPLOYMENT`【241218893498853†L214-L217】.
* **Public OpenAI settings** – `OPENAI_API_KEY` and `OPENAI_MODEL`【241218893498853†L219-L221】.
* **Paths** – `OUTPUT_DIR` and `IMAGE_ROOT`; for network shares use fully qualified UNC paths【241218893498853†L223-L229】.

After editing, restart the application to apply changes【241218893498853†L231-L236】.  The server starts in a console window and logs messages to `app.log`.

## Notes and best practices

* Keep the `ProgramData` directory restricted to administrators【241218893498853†L236-L244】.
* Use a separate service or user account with write permissions to the output directory when running as a network service.
* The default GPT model `gpt-4o` supports both text and multimodal inputs; only change it if required and supported【241218893498853†L188-L190】.
* For network shares, ensure the service account has permission to create files and directories; otherwise the app will fail to write outputs【241218893498853†L223-L230】.