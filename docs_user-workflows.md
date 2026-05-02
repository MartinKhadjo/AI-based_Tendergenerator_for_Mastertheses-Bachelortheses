# User Workflows

This guide walks through the typical steps a student or staff member follows when generating a tender using the Tender Generator.

## Getting started

To access the application, navigate to the host and port where the Tender Generator runs (e.g. `http://<host>:5000`)【241218893498853†L69-L76】.  If the page is unreachable, ensure the app is running, confirm the host/port and check firewall rules【241218893498853†L69-L77】.

## Filling the form

1. **Choose language** – Select English or German to match the desired template【241218893498853†L79-L82】.
2. **Enter title** – Provide a concise announcement title.
3. **Describe the initial situation** – Write a short free text summarising the context of the thesis【241218893498853†L84-L86】.
4. **Describe the task** – Write a short free text outlining the student’s tasks【241218893498853†L84-L86】.
5. **Enter the contact name** – Provide the name of the person responsible at PEM【241218893498853†L84-L90】.
6. **Select an image folder** – Pick a subfolder within the configured `IMAGE_ROOT` containing one or more images.  A random valid image may be placed on the first slide【241218893498853†L88-L90】.
7. **Preview anonymized details (optional)** – Click *Show Anonymized Details* to see the deterministic alias that will replace the contact name.  This preview runs locally in the browser and never transmits the raw name【241218893498853†L91-L94】.

## Generating and downloading

After filling the form, click **Generate PowerPoint**.  The server will process your input, expand the descriptions using the selected GPT provider, fill the template and save the finished PPTX under the configured output directory【241218893498853†L95-L99】.  Once complete, you will be redirected to a success page that contains a download link for your file.

Use the download link to save the presentation.  Generated files have timestamped filenames to avoid collisions.

## Tips and troubleshooting

* Keep your descriptions factual and within a few sentences; the generator enforces word limits【241218893498853†L114-L115】.
* If an error occurs, check the console window and `app.log` on the server for details【241218893498853†L115-L116】.
* Missing or expired API credentials will cause errors; update the settings in `config.ini` or `.env` and restart the application【241218893498853†L149-L190】.
* If images are not inserted, verify the selected folder contains valid formats (`.png`, `.jpg`, `.jpeg`, `.bmp`, `.gif`)【241218893498853†L372-L375】.