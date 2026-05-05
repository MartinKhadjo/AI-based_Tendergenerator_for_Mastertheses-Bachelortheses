# Demo Video

This repository does not include the original demo video file because large video assets should not be committed directly to Git. Instead, the product walkthrough is published as a public-safe YouTube demo and linked from the repository.

## Watch the Demo

[![Watch the AI-based Tendergenerator demo](https://img.youtube.com/vi/NoMPp8PkVJw/hqdefault.jpg)](https://www.youtube.com/watch?v=NoMPp8PkVJw)

**Direct link:** [https://www.youtube.com/watch?v=NoMPp8PkVJw](https://www.youtube.com/watch?v=NoMPp8PkVJw)

## What the demo shows

The video demonstrates the AI-based Tendergenerator as a public-safe product walkthrough. It is intended for recruiters, engineering managers, headhunters and technical reviewers who want to understand the product workflow and engineering value without accessing proprietary source code.

The walkthrough can be used to evaluate:

- the browser-based tender-generation workflow;
- the structured input process for Bachelor’s and Master’s thesis postings;
- AI-assisted transformation of short task descriptions into presentation-ready content;
- privacy-aware handling of contact information;
- PowerPoint automation and template-based document generation;
- the practical usability of the system for non-technical users;
- the project’s maturity as an applied AI and enterprise automation portfolio item.

## Why the video is linked instead of committed

The original video file is too large for a normal Git repository and would make the repository unnecessarily heavy. Keeping the video on YouTube and linking it here is the recommended portfolio approach because it:

- keeps the repository lightweight;
- avoids GitHub file-size limitations;
- makes the demo easy to watch in the browser;
- keeps proprietary source code private;
- still provides strong visual evidence that the software exists and works;
- supports a professional evidence-layer setup for employers and recruiters.

## Public Showcase Boundary

This demo is part of the public evidence layer. It does not disclose:

- proprietary source code;
- private prompt implementations;
- API keys or `.env` files;
- internal template mappings in reusable detail;
- deployment secrets;
- customer, institute or project-confidential data.

For deeper technical review, code walkthroughs or deployable artifacts should be shared only privately under appropriate NDA or licensing terms.

## Recommended Repository Placement

Place this file at:

```text
docs/demo/demo_video.md
```

Then link it from the main `README.md`:

```markdown
## Demo Video

A public-safe walkthrough of the AI-based Tendergenerator is available here:

[Watch the demo](docs/demo/demo_video.md)
```
