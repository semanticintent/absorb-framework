# Prior art and positioning

ABSORB is not the first readiness framework for AI in software delivery. This file records related work and the questions to answer before claiming differences. Entries marked "not yet read" were found by title in a web search on 2026-10-26 and have not been opened. Do not describe their content until they have been read.

## Related AI-readiness frameworks

| Work | Type | Link | Status |
| --- | --- | --- | --- |
| AI in Engineering Assessment (Codurance) | Consultancy assessment | https://www.codurance.com/ai-readiness-assessment | Not yet read |
| AI readiness assessment framework (Augment Code) | Vendor guide | https://www.augmentcode.com/guides/ai-readiness-assessment-framework | Not yet read |
| Agentic AI Readiness: A Process-Oriented Assessment Framework | Academic paper | https://scholarspace.manoa.hawaii.edu/items/174fe069-9545-4445-96ef-9cf693bd87ea | Not yet read |
| DORA research on AI-assisted software development (Google) | Research program | https://dora.dev/dora-report-2025 | Mentioned in secondary sources; not yet read |
| Anthropic engineering posts on source control scale and code review | Company self-report | See `SPEC.md` sources | Partially read via secondary coverage |

## Foundational ideas ABSORB builds on

Amdahl's law, theory of constraints, Little's law, queueing theory, Brooks's law, Goodhart's law and Conway's law. Sources and caveats are in `SPEC.md`. ABSORB uses them as lenses on one principle: the slowest stage sets the pace and the constraint moves.

## Historical analogies

See `HISTORICAL_LENS.md` for an interpretive comparison with electrification (Paul David, 1990) and the dotcom era. It is context, not evidence for the framework.

## Hypotheses about how ABSORB differs (unverified)

These are claims to test after reading the related work, not conclusions.

| Hypothesis | How to verify |
| --- | --- |
| ABSORB focuses on whether the system downstream of coding can absorb speed, rather than whether teams are ready to adopt AI tools | Compare the dimensions and questions in each framework |
| It derives autonomy tiers from verification and governance evidence, not from a single maturity score | Check whether other frameworks tie permitted autonomy to evidence |
| It pairs a stage-timing input with an Amdahl-style speedup check, so the constraint is found from data | Check for stage-level timing in the other assessments |
| It is a self-contained, open, offline assessment with a written spec | Check availability, licensing and format of the others |

## Relationship to the author's earlier frameworks

First pass done from Zenodo abstracts only: see `COMPARISON.md`. Closest records are Governance-Driven Design, Governance-as-Infrastructure, the Synthesis Gate, the Semantic Intent papers, Agentic Traffic Control, TRACE and Machine Legibility Dimensions. Full texts still need reading. Remaining questions:

- Shared vocabulary, scales and structure that ABSORB should reuse or deliberately depart from.
- Overlaps that suggest merging, cross-referencing or renaming.
- Any earlier claims or terminology that ABSORB contradicts.
- Naming and citation conventions used in earlier Zenodo records.

## Name check

A web search on 2026-10-26 for "ABSORB framework AI agentic readiness assessment software delivery" surfaced no framework with this name. That is not a trademark or registry search. Check Zenodo, GitHub and a trademark database before publishing, and consider PROOF or SPAN as fallbacks.
