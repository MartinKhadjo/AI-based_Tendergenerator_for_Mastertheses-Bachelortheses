# Deployment and Operations

## Installation model
According to the manual, the application is installed using an Inno Setup installer.
The installer guides administrators through:
- output folder configuration,
- image-root configuration,
- host/port setup,
- provider selection,
- credential configuration,
- firewall rule setup.

## Configuration model
Operational settings are stored under a ProgramData directory and include:
- provider selection (`azure` or `openai`),
- Azure endpoint/version/key/deployment,
- OpenAI key/model,
- output directory,
- image root,
- template paths.

## Runtime model
The system is exposed through a browser-accessible service. Generated PPTX files are written to the configured output directory and downloaded by users via the success page.

## Operational strengths
- deployment does not require source-code modification,
- configuration is externalized,
- output paths can point to local or network locations,
- runtime behavior is simple to operate for internal institutional usage.

## Public-safe limitation
No actual keys, hosts, endpoints, UNC paths or private operational details are published here.
