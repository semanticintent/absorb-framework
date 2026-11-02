# ABSORB

**Agentic Bottleneck, Speed & Output Readiness Baseline**

> **Status: draft v0.1. A proposed framework, not a validated standard.** Scoring thresholds and maturity levels are proposals. See [Status and limitations](#status-and-limitations).

AI has made code cheap to produce. It has not made software cheap to deliver, because delivery also needs deciding, specifying, verifying, releasing and adopting. ABSORB is a diagnostic for one question: **can this organization turn faster AI-driven coding into faster, safer delivery?**

## The idea in three lines

1. Development speed and delivery speed are different quantities. AI mostly raised the first.
2. The slowest stage sets the pace, and the constraint moves when you relieve it.
3. Verification and human attention become the scarce resources, so readiness depends on how well the system around the code absorbs the speed.

## What is in this repository

| Path | What it is |
| --- | --- |
| [`SPEC.md`](SPEC.md) | The full framework: philosophy, purpose, method, eight dimensions, maturity levels, autonomy tiers, metrics, caveats and sources |
| [`assessment/index.html`](assessment/index.html) | A self-contained interactive self-assessment (open it in a browser; no server needed) |
| [`VALIDATION.md`](VALIDATION.md) | Hypotheses, falsification criteria, study designs and threats to validity (nothing has been run yet) |
| [`HISTORICAL_LENS.md`](HISTORICAL_LENS.md) | An interpretive note comparing the framework's thesis with electrification and the dotcom era (not part of the testable spec) |
| [`PRIOR_ART.md`](PRIOR_ART.md) | Related frameworks and foundational ideas, and how ABSORB relates to them |
| [`case-studies/TEMPLATE.md`](case-studies/TEMPLATE.md) | A template for documenting an application of the framework |
| [`CITATION.cff`](CITATION.cff) | Citation metadata |
| [`LICENSE_NOTES.md`](LICENSE_NOTES.md) | Suggested licenses and release steps |

## Quick start

1. Read the one-page summary at the top of [`SPEC.md`](SPEC.md).
2. Open `assessment/index.html` in a browser. It loads example answers so you can see the output; choose "Start fresh" to enter your own.
3. Answer 24 statements (0 to 4), enter the elapsed days a typical change spends at each stage, and optionally record baseline metrics.
4. Read the results: readiness level, weakest dimension, where work waits, which autonomy tiers are ready, and first moves.
5. Fix the binding constraint first, then re-assess.

## The eight dimensions

D1 Flow and constraints, D2 Verification and evidence, D3 Risk-tiered governance, D4 Intent and specification, D5 Environment and platform, D6 Accountability and ownership, D7 Measurement, D8 People and change.

## Status and limitations

- Drafted on 2026-10-26 from public reports and a working session. Many source figures come from vendors, trade blogs or company self-reports.
- Maturity levels, autonomy tiers, thresholds and the dimension list are proposals. No study has validated them.
- No field results are included yet. `VALIDATION.md` lists what would count as evidence for or against the framework. Case studies are invited (see the template).
- The link between readiness and headcount decisions is a hypothesis, not a finding.

## Prior art

ABSORB is not the first AI-readiness framework. See [`PRIOR_ART.md`](PRIOR_ART.md) for related work and where ABSORB aims to differ.

## How to cite

See [`CITATION.cff`](CITATION.cff). Please cite the version you used.

## License

Suggested: CC BY 4.0 for the written framework, Apache-2.0 or MIT for the assessment code. See [`LICENSE_NOTES.md`](LICENSE_NOTES.md). The license is not final until a `LICENSE` file is added.

## Contributing and feedback

Critique is the most useful contribution. Open an issue with: what you applied it to, what scored wrongly or felt wrong, and what would change your mind about a threshold or dimension.

## Authorship and AI assistance

Authored by Michael Shatny (confirm before publishing). Drafted with AI assistance (Claude), with research from public sources listed in `SPEC.md`.
