# User Workflows

## Primary user workflow
1. Open the Tendergenerator in the browser.
2. Select the target language (German or English).
3. Enter the announcement title.
4. Provide short free-text input for **Initial Situation** and **Your Task**.
5. Enter the PEM contact name.
6. Select an image folder.
7. Optionally preview the anonymized alias.
8. Click **Generate PowerPoint**.
9. Open the success page and download the generated `.pptx` file.

## UI reference
![Browser UI](assets/browser-ui.png)

## What makes the workflow good
The workflow is intentionally minimal: users only provide compact inputs, while the system handles wording, structure, template choice and output creation.
This reduces repetitive manual presentation work and keeps thesis announcements consistent.

## Administrator workflow
Administrators are responsible for:
- installation of the application,
- setting output and image folders,
- configuring host/port,
- choosing Azure OpenAI or OpenAI,
- storing and updating credentials securely,
- restarting the application after configuration changes.
