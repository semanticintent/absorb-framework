# ABSORB validation plan

Version 0.1 (draft), 2026-10-26, revised 2026-11-02. **ABSORB is a proposed framework. Nothing here has been run.** This file states in advance what would count as evidence for or against it, so the framework can be wrong in public.

## Purpose and rules

1. Hypotheses and pass/fail thresholds are written **before** data is collected, and are not edited afterward except through the calibration log.
2. **Failures are published.** A hypothesis that fails is reported as failed, and the affected part of `SPEC.md` is revised or withdrawn.
3. Every change to a threshold, scoring rule or dimension is recorded in the calibration log below, with the date and the evidence behind it.
4. Thresholds in this file (such as "60%") are starting values chosen for this plan, not results. Revise them only before data collection, and say why.
5. Data from organizations is anonymized and shared only with permission (see the case-study template).

## What ABSORB claims, in testable form

| # | Hypothesis | Measured by | Falsified if |
| --- | --- | --- | --- |
| H1 | **Constraint identification.** The stage the assessment names as the longest not yet sped up is the stage with the longest measured wait in workflow data. | Assessment output versus timestamps (ticket, PR open, first review, merge, release) | The two agree in fewer than 60% of teams assessed |
| H2 | **Whole-path speedup.** The Amdahl-style estimate lands near the measured change in lead time after AI adoption. | Predicted versus measured lead-time ratio | Median absolute error exceeds 50% of the measured change |
| H3 | **Safety floor.** A lower autonomy floor (the lowest of D2, D3, D5, D6) goes with more reverts and incidents per 100 changes, controlling for the share of AI-written changes. | Rank correlation across teams; revert and incident counts | No negative relationship between floor and quality, or a positive one |
| H4 | **The constraint moves.** After the named constraint is fixed, a different stage becomes the longest within 90 days. | Stage timings before and after | The same stage remains the longest in most cases, which would mean either no real fix or no movement |
| H5 | **Inter-rater reliability.** Two people scoring the same team independently produce dimension scores within 0.5 points. | Mean absolute difference and weighted kappa on the 24 statements | Mean absolute difference exceeds 0.5, or kappa is below 0.4 |
| H6 | **Statement coherence.** The three statements of a dimension move together more than they move with statements from other dimensions. | Item-level correlations; factor analysis if there are enough responses | Statements do not cluster by dimension, or one dimension shows no internal consistency |
| H7 | **Level ordering.** At similar AI usage, higher readiness levels go with shorter lead time. | Lead time by level, controlling for team size and AI share | No ordering, or the reverse |
| H8 | **Absorption ratio (proposed, not yet in the spec).** At gate stages where arrivals divided by clearing capacity exceed about 0.8, waits grow disproportionately. | Per-stage arrival rate, capacity, and wait time | Waits show no steep rise as the ratio approaches 1 |

H8 depends on adding the ratio to `SPEC.md` and the assessment page. Until then it stays a candidate.

**Measurement notes** (these clarify how a hypothesis is measured; they do not change any hypothesis or threshold):

- **H2** uses hands-on time where the team entered it. Estimates made from elapsed time alone are upper bounds, so they are reported separately and not pooled with the others. Pooling them would bias the error in one direction.
- **H5 and H6** depend on each statement asking one thing. Four double statements were split or narrowed before any data was collected (see the calibration log).
- **H5** can be collected with the assessment page itself: each rater copies a result code, and the comparison reports the dimension-level mean absolute difference and a quadratic-weighted kappa on the 24 statements. With one pair of raters, kappa on 24 items is indicative only; pool pairs across teams for the test.
- **H1** compares against the longest measured *wait*. Where hands-on time is entered, wait = elapsed minus hands-on.

## Studies, cheapest first

### Study A. Public-repository retrospective (tests H1 and H4 in part)

- **Data:** open-source projects with public PR timelines and release dates.
- **Method:** compute wait time per stage from timestamps. Score the stages as the assessment would, using only public evidence. Compare the named constraint with the measured one.
- **Limits:** public repositories lack approval, adoption and prioritization stages, so this tests only the part of the path that is visible. Projects that publish this data are not a typical enterprise. Treat it as a feasibility test, not proof.
- **Cost:** low. No permission needed, but follow each platform's terms of use and rate limits.

### Study B. Single-team before and after (tests H1 to H4)

- **Who:** the author's own team, or any team willing to share.
- **Method:** baseline assessment and stage timing, one intervention on the named constraint, re-measure at 30, 60 and 90 days, and record where the constraint went.
- **Limits:** n = 1. Confounded by anything else that changed in 90 days. Report all concurrent changes.
- **Output:** a case study using `case-studies/TEMPLATE.md`.

### Study C. Multi-team pilot (tests H1 to H7)

- **Who:** 5 to 10 teams, preferably in different organizations and industries.
- **Method:** each team completes the assessment; two raters per team where possible (H5); share anonymized stage timings and incident counts; follow-up at 90 days.
- **Limits:** volunteers are probably more mature and more measurement-minded than average. Fewer than about 30 teams will not support factor analysis (H6), so treat H6 results as indicative.

### Study D. Opt-in submissions (later)

- Needs a submission path that does not exist yet. The assessment page currently stores answers only in the viewer's browser. Adding submission requires a privacy design and consent text first.

## Threats to validity

| Threat | Why it matters | Mitigation |
| --- | --- | --- |
| Self-report bias | Raters may flatter their own team | Require evidence per score; use a second rater; compare with measured data |
| Selection | Teams that volunteer are unrepresentative | Report who was excluded; recruit outside the author's network |
| Confounding | Tools, headcount and priorities change within 90 days | Log concurrent changes; avoid causal claims from n = 1 |
| Moving target | Models and tools change quickly, so a result may expire | Date every result; re-run on a schedule |
| Author involvement | The author designed the framework and may run the studies | Have someone else score at least some teams; publish raw scores |
| Metric gaming | Teams may optimize the metrics (Goodhart's law) | Track outcomes such as incidents and lead time alongside the scores |
| Small samples | Factor analysis and correlation need more teams than a pilot gives | State confidence plainly; call early results indicative |

## Reporting template

For each study, publish:

- Hypotheses tested, with thresholds as written here
- Sample: how many teams, how chosen, how many dropped out
- Result per hypothesis: passed, failed, or inconclusive, with the numbers
- Changes to `SPEC.md` made as a result
- Concurrent changes and other caveats

## Status board

| Hypothesis | Status | Evidence |
| --- | --- | --- |
| H1 | Untested | None |
| H2 | Untested | None |
| H3 | Untested | None |
| H4 | Untested | None |
| H5 | Untested | None |
| H6 | Untested | None |
| H7 | Untested | None |
| H8 | Candidate, not in spec | None |

## Calibration log

| Date | Change | Reason and evidence |
| --- | --- | --- |
| 2026-10-26 | Initial plan | Thresholds are starting values, not findings |
| 2026-11-02 | Statements D2(2), D6(1), D7(3), D8(2) reworded to ask one thing each | Double statements make inter-rater agreement (H5) and dimension clustering (H6) harder to read. Done before any data collection, as rule 4 allows. No threshold or level rule changed |
| 2026-11-02 | Optional hands-on time added to stage timing; the speedup check applies only to hands-on time | Elapsed time includes waiting, which a faster stage does not shorten, so the old check overstated the speedup. This changes how H2 is measured, not its threshold |

## Notes on alignment with the author's other records

The author's Machine Legibility Dimensions record states that it is proposed and that empirical validation is the next step, and the Capability-as-Infrastructure record states hypotheses with a validation protocol. This file follows the second pattern. These two records were read from abstracts only, so align terminology and format after reading the full texts.
