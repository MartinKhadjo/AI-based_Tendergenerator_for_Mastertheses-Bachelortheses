# Performance and Scalability

## Scope
The Tendergenerator is optimized for practical internal document generation, not for massive distributed batch processing.

## Performance drivers
Response time is mainly influenced by:
- latency of the chosen AI provider,
- text-generation time for two generated sections,
- template loading and PowerPoint rendering,
- file I/O to the configured output directory,
- optional image insertion and validation.

## Suitable usage pattern
The documented architecture is well suited for:
- internal faculty or department use,
- moderate concurrent use,
- repeated creation of high-quality thesis postings.

## Reasonable future extensions
A future roadmap could include:
- queue-based execution,
- retry and job status tracking,
- structured observability,
- template version management,
- packaged release binaries,
- CI-based artifact production.
