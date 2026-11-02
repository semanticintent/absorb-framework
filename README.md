# ABSORB

**Agentic Bottleneck, Speed & Output Readiness Baseline**

> **Status: draft v0.1. A proposed framework, not a validated standard.** Scoring thresholds and maturity levels are proposals. See [Status and limitations](#status-and-limitations).

AI has made code cheap to produce. It has not made software cheap to deliver, because delivery also needs deciding, specifying, verifying, releasing and adopting. ABSORB is a diagnostic for one question: **can this organization turn faster AI-driven coding into faster, safer delivery?**

## The idea in three lines

1. Development speed and delivery speed are different quantities. AI mostly raised the first.
2. The slowest stage sets the pace, and the constraint moves when you relieve it.
3. Verification and human attention become the scarce resources, so readiness depends on how well the system around the code absorbs the speed.

The first line is not new. DORA's 2025 report calls AI an amplifier of an organization's existing strengths and weaknesses. ABSORB adds a way to act on that:

- **Find where the speed is lost.** Time each stage of a typical change, split into hands-on time and waiting, and estimate how much speeding up one stage can lift the whole path. If coding is 30% of the path and becomes 3 times faster, the whole path is only 1.25 times faster.
- **Decide what may run with less review.** Four autonomy tiers (no human, one human, owner plus reviewer, sign-off). Readiness for each tier comes from the weakest of verification, governance, platform and ownership, not from an average.
- **Be wrong in public.** The hypotheses and pass/fail thresholds are written down before any data is collected.

## What is in this repository

| Path | What it is |
| --- | --- |
| [`SPEC.md`](SPEC.md) | The full framework: philosophy, method, eight dimensions, maturity levels, autonomy tiers, metrics, caveats, and a table of sources showing how each figure was checked |
| [`assessment/index.html`](assessment/index.html) | A self-contained interactive self-assessment. Open it in a browser; it needs no server and makes no network requests |
| [`VALIDATION.md`](VALIDATION.md) | Hypotheses, falsification criteria, study designs and threats to validity (nothing has been run yet) |
| [`PRIOR_ART.md`](PRIOR_ART.md) | Related frameworks (DORA, Codurance, Augment Code), what each was read from, and which claimed differences held up |
| [`HISTORICAL_LENS.md`](HISTORICAL_LENS.md) | An interpretive note comparing the thesis with electrification and the dotcom era (not part of the testable spec) |
| [`case-studies/TEMPLATE.md`](case-studies/TEMPLATE.md) | A template for documenting an application of the framework |
| [`CHANGELOG.md`](CHANGELOG.md) | What changed, and why |
| [`CITATION.cff`](CITATION.cff) | Citation metadata |

## Quick start

1. Read the "At a glance" section at the top of [`SPEC.md`](SPEC.md).
2. Open `assessment/index.html` in a browser. It loads example answers so you can see the output; choose "Start fresh" to enter your own.
3. Pick a goal, enter the elapsed days a typical change spends at each stage (and the hands-on part, if you know it), rate 24 statements from 0 to 4, and optionally record baseline metrics.
4. Read the results: readiness level, weakest dimension, where work waits, which autonomy tiers are ready, and first moves.
5. Fix the binding constraint first, then re-assess.

## The eight dimensions

D1 Flow and constraints, D2 Verification and evidence, D3 Risk-tiered governance, D4 Intent and specification, D5 Environment and platform, D6 Accountability and ownership, D7 Measurement, D8 People and change.

## Status and limitations

- Drafted 2026-10-26 and revised 2026-11-02 from public reports. Each figure in `SPEC.md` is traced to its source, and the table says how it was checked. Most come from vendors or company self-reports; one comes from a randomized trial.
- Maturity levels, autonomy tiers, thresholds and the dimension list are proposals. No study has validated them.
- No field results are included yet. `VALIDATION.md` lists what would count as evidence for or against the framework. Case studies are invited (see the template).
- The link between readiness and headcount decisions is a hypothesis, not a finding.

## How to cite

See [`CITATION.cff`](CITATION.cff). Please cite the version you used.

## License

Not yet chosen. Until a `LICENSE` file is added, this work is not open source.

## Contributing and feedback

Critique is the most useful contribution. Open an issue with what you applied it to, what scored wrongly or felt wrong, and what would change your mind about a threshold or dimension.

## Authorship and AI assistance

Authored by Michael Shatny. Drafted and revised with AI assistance (Claude), using the public sources listed in `SPEC.md`.
