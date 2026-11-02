# ABSORB: Agentic Bottleneck, Speed & Output Readiness Baseline

Version 0.1 (draft), first drafted 2026-10-26, revised 2026-11-02. See `CHANGELOG.md` for what changed.

## At a glance

ABSORB answers one question: can this organization turn faster AI-driven coding into faster, safer delivery? The name is the reminder that the whole system, not just the dev team, has to absorb the new speed.

| Letter | Stands for | Meaning |
| --- | --- | --- |
| A | Agentic | Work done by AI agents under human direction |
| B | Bottleneck | The slowest untouched stage, which caps end-to-end speed |
| S | Speed | Delivery speed from request to customer use, not typing speed |
| O | Output | Value shipped safely, judged by outcomes rather than activity |
| R | Readiness | How prepared people, process and platform are to absorb agent-speed change |
| B | Baseline | A measured starting point to re-assess against |

The core claim: development speed and delivery speed are different quantities. AI mostly raised the first. ABSORB measures and raises the second.

**What "agentic" means here.** Any AI that writes or changes code for a human who stays accountable for it, from an assistant in the editor to an agent that opens its own pull requests. ABSORB is about what happens to that code after it is written, so it does not depend on how autonomous the agent is.

**Why the name.** It borrows on purpose from *absorptive capacity*, a firm's ability to recognize new outside knowledge, take it in and put it to use (Cohen and Levinthal, 1990). That idea is about learning. ABSORB applies the same intuition to delivery: a new capability pays off only as fast as the organization around it can take it in.

Alternate names considered: PROOF (Pipeline Readiness, Oversight & Output Fidelity), which stresses verification, and SPAN (System Pace Absorption Navigator).

Status: a proposed framework drafted from public reports and a working session. It is not a validated standard (see Evidence caveats). Its central observation is not new: DORA's 2025 report describes AI as an amplifier of an organization's existing strengths and weaknesses. ABSORB's contribution is a method for finding *where* the system fails to absorb the speed, and for deciding *what may run with less human review*, not the observation itself. See `PRIOR_ART.md`.

## Why: the philosophy

AI made code cheap to produce. It did not make software cheap to deliver, because delivery also needs deciding, specifying, verifying, releasing and adopting. Eight principles follow from that.

1. **Writing code is not delivering software.** Coding is a minority of lead time (one analysis estimates roughly 20 to 30%), so speeding it up alone lifts the whole by far less. The measured gains vary by source and are rising: a DX analysis of about 121,000 developers reported pull-request throughput up about 10% at near-universal AI use, while DX's Q3 2026 report (500+ companies) shows median weekly PRs per developer up 75.5% over four quarters. The same report finds that organizations producing the most AI code wait 105% longer for a first review, and that recovery time from failed deployments has not improved in four quarters. In a randomized trial, experienced open-source developers were 19% slower with early-2025 AI tools while believing they were faster (METR, 2025). So more code is being produced, but producing a pull request is not delivering it: the gain shows up as longer queues at the stages that follow.
2. **The slowest stage sets the pace, and the constraint moves.** Fix one stage and the queue forms at the next. Anthropic reports that its merges rose from about 2,500 a day in May 2026 to over 30,000 in September, and that "the bottleneck, now, is all of the developer infrastructure built for human scale: source control, builds, and CI."
3. **Trust is the scarce resource.** When generation is cheap, verification becomes the expensive step, and human attention becomes the budget to spend carefully.
4. **People move from doing to governing.** The durable human work is owning risk, defining intent, designing evidence, and being accountable for what ships.
5. **Readiness depends on the goal.** A company that wants more output and one that wants lower cost need different targets from the same capability. Name the goal first.
6. **Outcomes over activity.** PR counts and the share of AI-written code say little if reverts, incidents and rework rise alongside them.
7. **Fix the system before the headcount.** Cutting people at an unfixed constraint leaves the constraint in place, and the people cut are often the ones who would relieve it, such as reviewers and owners.
8. **Readiness is temporary.** Models, tools and costs keep changing. An assessment is a baseline to revisit, not a certificate.

**One principle, several laws.** The second principle is general: a system's output is set by its most limited part, and relieving that part exposes the next one. Several well-known ideas from systems thinking and software describe the same pattern from different angles. They are used here as lenses, not as proofs.

| Law or idea | What it says | What it means here |
| --- | --- | --- |
| Amdahl's law | Speeding up one part of a process is capped by that part's share of the whole. | Faster coding helps little when coding is a minority of the path. See the formula in the method section. |
| Theory of constraints | A system's output is set by its slowest stage. Improve that stage and the next one becomes the limit. | Fix the binding constraint first, then re-assess. |
| Little's law | The average amount of work in a system equals the rate work arrives times the time it spends there. | If agents add changes faster than people clear them, the review queue and the wait both grow. |
| Queueing theory | Waiting time climbs steeply as a stage approaches full utilization. | Reviewers kept at full capacity make every change wait. Leave slack at stages that gate release. |
| Brooks's law | Adding people to a late software project tends to make it later, because coordination costs rise. | More developers or reviewers is not a direct fix for a stalled stage. |
| Goodhart's law | When a measure becomes a target, it stops being a good measure. | Targeting PR counts or the share of AI-written code invites gaming. It supports principle 6. |
| Conway's law | Systems tend to mirror the communication structure of the organization that builds them. | Handoffs between teams become delivery stages, so the org chart is part of the pipeline. |

## What for: purpose and outcomes

The assessment exists to tell an organization where its next unit of effort pays off, and to stop it from spending that effort in the wrong place.

| Who | Question it answers |
| --- | --- |
| CTO or engineering leader | Where does speed stall between a finished change and a customer using it? |
| Delivery or platform lead | Is the platform ready for agent-scale volume, or is it already the constraint? |
| Risk, security, compliance | Which changes can run with less human review, and what evidence makes that safe? |
| Finance or the business sponsor | Should we take the gain as more output or as lower cost, and is the system ready for either? |
| Team lead | What should my people spend their time on now that code is cheaper? |

It is meant to produce five outcomes:

1. The binding constraint, named with evidence.
2. A decision between adding agent capacity and removing a bottleneck.
3. Autonomy tiers: what merges with no human, one human, or a review board.
4. A measured baseline to re-assess against.
5. A sequenced plan, so effort goes to the constraint first.

## How: the method

The assessment runs in seven steps and then repeats. The first is the one most often skipped.

1. **Declare intent.** Decide whether the goal is more output, lower cost, lower risk, or a mix, plus the target multiplier and time horizon.
2. **Map the value stream.** Trace a change from request to customer use. Record elapsed time and touch time for every stage, including stages outside engineering such as approvals, release windows and training.
3. **Assess the eight dimensions.** Gather evidence from repo and CI data, incident history, policy documents and interviews.
4. **Score and name the constraint.** Score each dimension 0 to 4, then state the single stage that currently caps end-to-end speed.
5. **Design autonomy tiers.** Define which change types merge with no human, one human, or a review board, and what evidence each tier requires.
6. **Sequence the interventions.** Fix the binding constraint first. Plan in 30, 60 and 90 day steps and expect the constraint to move.
7. **Re-measure.** Repeat quarterly and after any major model or tooling change.

A quick test for step 2 is Amdahl's law: the gain from speeding up one part of a process is capped by the share of the whole that part represents. If stage i makes up fraction f of the work and gets s times faster, the end-to-end speedup is:

```latex
\text{speedup} = \frac{1}{\sum_i f_i / s_i}
```

Example: coding is 30% of the work and becomes 3 times faster while everything else stays the same. The result is 1 / (0.3/3 + 0.7) = 1.25, not 3.

**Speed up the work, not the wait.** A stage's elapsed time is hands-on time plus waiting time, and AI shortens only the hands-on part. A change that sits two days in a review queue still waits two days when the review itself takes minutes. So the check applies the speedup to hands-on time only:

```latex
\text{speedup} = \frac{E}{E - t_k + t_k / s}
```

where E is the total elapsed time of the path and t_k is the hands-on time of the stage that gets s times faster. If hands-on time is not known, using the stage's whole elapsed time gives an upper bound, and the assessment labels it that way. Waiting is usually the larger share, which is why the constraint is found from where work waits rather than from where work is done.

**Cutting the wait.** Process changes, not faster tools, shorten waiting: smaller batches, earlier review pickup, fewer hand-offs, automated approvals. The assessment's what-if view lets a team try both levers on one stage k, a work speedup s and a cut r to its waiting time w_k:

```latex
\text{speedup} = \frac{E}{E - t_k + t_k / s - r\,w_k}
```

With r = 0 this is the formula above. The what-if view is for exploring, not scoring: it changes no dimension score, level or tier. Waiting can only be modelled for a stage whose hands-on time is entered.

## The eight dimensions

Each dimension is a place where speed can stall.

| # | Dimension | Covers | Evidence to gather | Red flag |
| --- | --- | --- | --- | --- |
| D1 | Flow and constraints | The end-to-end path from request to customer use, including non-engineering stages | Value stream map, queue times, lead time by stage | Approval or release stages that wait days and were never touched by AI |
| D2 | Verification and evidence | Tests, independent checks, AI review, proof a change is safe | Coverage, flaky-test rate, escaped defects, who writes the tests and the review, sampled human audits of approved changes | One model writes the code, the tests and the review; unreviewed merges rising |
| D3 | Risk-tiered governance | Which changes need which level of human involvement | Merge policy, exception logs, audit trail | Either every change gets the same heavy review, or green CI alone means merge |
| D4 | Intent and specification | Clarity of requirements, acceptance criteria, decision records | Sample tickets, spec-to-test links, ADRs | Vague tickets; tests written after the code |
| D5 | Environment and platform | CI speed, repo scale, previews, rollback, observability, agent context files | CI queue time, rollback time, doc quality | CI wait grows with agent volume; no one-step rollback |
| D6 | Accountability and ownership | Named humans for services and for release decisions | Ownership map, on-call rota, incident reviews | Nobody can say who approves production for a service |
| D7 | Measurement | Outcome metrics versus activity metrics | Dashboards in use, metric definitions | Dashboards show PR counts and AI-code share only |
| D8 | People and change | Skills, roles, junior pipeline, incentives, training | Interviews, attrition, reviewer load, training records, current role definitions | Reviewers overloaded; AI mandates without enablement; no path for juniors |

Weights are not fixed. The binding constraint matters more than the average score, so a strong D5 does not offset a failing D2.

## Maturity levels and autonomy tiers

Most organizations should aim for level 2 or 3, not level 4. Both scales below are proposals for this framework, not industry standards.

| Level | Name | What it looks like |
| --- | --- | --- |
| 0 | Ad hoc | Individuals use AI; no shared process; personal gains do not reach delivery |
| 1 | Assisted | Tools are licensed and widely used; process is unchanged; the queue forms at review |
| 2 | Gated | Review and test gates adapted; AI review on every change; some outcome metrics |
| 3 | Governed | Risk-tiered merge policy; independent verification; named owners; outcome metrics drive decisions |
| 4 | Adaptive | Platform built for agent volume; most low-risk changes merge without humans; people focus on intent, risk and audit; reassessed continuously |

Anthropic's reported setup is an example of level 4 on the dimensions it has published: in the Claude Code repositories, changes merge with at most one human in the loop, who may be the author, and the company reports no increase in reverts or incidents. It tracks human approvals per PR (median and 95th percentile) and how long a PR waits on a person. It is an extreme case, and its figures are the company's own.

Autonomy tiers set how much human involvement a change needs. The examples are illustrative and each organization sets its own.

| Tier | Example changes | Human involvement | Evidence required |
| --- | --- | --- | --- |
| T0 Low risk | Docs, test-only changes, internal tooling | None beyond AI review | Automated checks, AI review, automatic rollback |
| T1 Standard | Routine features in well-tested services | One human, who may be the author | Passing tests, AI review, canary release |
| T2 Elevated | Shared libraries, schema migrations, authentication, payments | Named owner plus a second reviewer | T1 plus staged rollout and a written rollback plan |
| T3 Critical | Safety-critical, regulated, financial ledgers, security-sensitive | Explicit sign-off or change board | T2 plus audit trail and independent verification |

## Deliverables and baseline metrics

An engagement produces seven artifacts, and the metrics below become the baseline that later re-assessments compare against.

1. A value stream map with queue time per stage.
2. A scorecard for D1 to D8 (0 to 4) with the evidence behind each score.
3. A one-paragraph statement of the binding constraint.
4. A draft autonomy tier policy.
5. A 30, 60 and 90 day sequence of interventions.
6. A baseline metric set with targets.
7. An executive readout that frames the output-versus-cost choice.

| Metric | Why it matters |
| --- | --- |
| Lead time, request to production | The end-to-end result, not a stage |
| Review pickup time | How long a change waits for its first human look |
| Human approvals and wait per PR | Whether human attention is being spent or queued |
| Share of merges with zero review, by tier | Where the safety net is thin |
| Change failure and revert rate | Quality of what ships |
| Incidents per 100 merged changes | Whether speed is creating production risk |
| CI queue time and flake rate | Platform fit for agent volume |
| Time to roll back | Cost of being wrong |
| Changes linked to acceptance criteria | Specification discipline |
| Backlog trend | Whether extra output is absorbed or piling up |

Reported reference points, from vendor reports and best treated as directional:

- LinearB's 2026 benchmarks (8.1 million pull requests from 4,800 teams) report that agentic PRs wait 5.3 times longer for pickup than unassisted ones, and that AI-generated PRs are accepted 32.7% of the time against 84.4% for manual PRs.
- Faros AI's 2026 report (two years of telemetry, 22,000 developers, 4,000 teams, comparing each organization's lowest and highest AI adoption periods) reports pull requests merged without any review up 31.3% and the incidents-to-PR ratio up 242.7%.
- DX's Q3 2026 report finds a 105% longer wait for first review at organizations producing the most AI code.

Both vendors sell measurement tools, so they have a reason to find a problem worth measuring.

## Self-assessment tool

An interactive version of this framework scores D1 to D8, reads the maturity level, and shows which autonomy tiers are ready. In this repository it is `assessment/index.html`. Answers are kept in the viewer's own browser only.

| Input | What you enter | What it produces |
| --- | --- | --- |
| Goal | More output, lower cost, lower risk, or a mix | A readout line that frames the results |
| Stage timing | Elapsed days at seven stages, optional hands-on days, and where AI has sped up the work | A pipeline view of every stage split into hands-on and waiting time, the longest stage not yet sped up, and a what-if for one stage (faster work, less waiting) with its whole-path speedup (an upper bound when hands-on days are missing) |
| Statements | 24 ratings from 0 (not true) to 4 (fully true), one at a time (guided, keyboard-friendly) or all at once | A score per dimension and the weakest dimension |
| Second rater (optional) | A colleague's result code, which holds only their 24 ratings | Both raters' dimension scores side by side, the average gap per dimension against the 0.5 aim in H5, agreement within 1 point, weighted kappa, and the statements where the two differ by 2 points or more |
| Baseline metrics (optional) | Seven metrics from the metrics table above | Values recorded in the summary, not scored |

Scoring rules:

1. A dimension score is the average of its three statements, on a 0 to 4 scale.
2. The readiness level is the lower of two numbers: the whole-number part of the overall average, and the whole-number part of the weakest dimension plus one. It never exceeds 4.
3. The autonomy floor is the lowest score among D2, D3, D5 and D6.
4. Each tier is Ready, Conditional or Not yet, according to the floor (below). Conditional means extra evidence or monitoring is needed first. T3 changes always keep explicit sign-off: Ready at T3 means the evidence supports agent-authored critical changes reaching sign-off, not that sign-off can be dropped.

| Tier | Ready at floor of | Conditional at floor of |
| --- | --- | --- |
| T0 Low risk | 2.0 | 1.5 |
| T1 Standard | 2.5 | 2.0 |
| T2 Elevated | 3.0 | 2.5 |
| T3 Critical | 3.5 | 3.0 |

The thresholds and the level rule are proposals. Tune them after running the assessment on real teams.

The 24 statements, rated from 0 (not true) to 4 (fully true). Each asks one thing, so a rater never has to average two answers in their head. Related practices that used to share a statement (audit sampling, on-call rotas, roles) remain in the evidence column of the dimensions table.

| Dimension | Statements |
| --- | --- |
| D1 Flow and constraints | (1) We have mapped the path from request to customer use, including stages outside engineering. (2) We know how long changes wait at each stage, not only how long the work takes. (3) Approvals, releases and rollouts have been sped up or redesigned, not only coding. |
| D2 Verification and evidence | (1) Automated tests give us enough confidence to ship routine changes. (2) Changes are checked by tests or reviewers that are independent of the AI that wrote them. (3) We track escaped defects and use them to improve tests and review. |
| D3 Risk-tiered governance | (1) Changes are sorted into risk tiers with different review requirements. (2) A written policy says which changes may merge with no human or with one human. (3) Exceptions and overrides are logged and reviewed. |
| D4 Intent and specification | (1) Work arrives with clear acceptance criteria before building starts. (2) Decisions and constraints are recorded where both people and agents can read them. (3) Each change can be traced to a requirement and to the tests that check it. |
| D5 Environment and platform | (1) CI and builds stay fast as the number of changes grows. (2) Any release can be rolled back quickly and safely. (3) Agents have the context they need: repository docs, conventions, preview environments and observability. |
| D6 Accountability and ownership | (1) Every service has a named owner. (2) A named person approves production releases for each service. (3) Incidents involving AI-written changes have a clear review process. |
| D7 Measurement | (1) We measure outcomes such as lead time, reverts and production incidents. (2) We do not treat PR counts or the share of AI-written code as success measures. (3) Reviews of these metrics regularly change decisions. |
| D8 People and change | (1) Reviewers' workload is sustainable at the current volume of changes. (2) People have training and time to learn to work with AI tools. (3) Junior engineers have a path to build judgment. |

## Failure modes, scope, roles and caveats

The most common mistakes are the ones the assessment is built to catch:

- Cutting headcount while the real constraint sits elsewhere.
- Scaling agent output into a review queue that cannot grow.
- Letting green CI alone mean merge for every change type.
- Using the same model to write the code, the tests and the review.
- Reporting the share of AI-written code as success.
- Treating the assessment as a one-time certificate.

What ABSORB is not: a tool-selection exercise, a productivity audit of individuals, a headcount-reduction model, or a validated benchmark. It can inform a headcount decision but does not make one.

The skills it draws on, which also describe the niche:

- Verification engineering: test strategy and independent checks.
- Delivery and platform engineering: CI, rollback, observability, agent-ready repos.
- Risk and governance design: tiers, policy, audit evidence.
- Technical product work: intent, specs, acceptance criteria.
- Measurement: outcome metrics and baselines.
- Change leadership: roles, incentives, training, junior pipeline.

**Evidence caveats.** This framework was first synthesized on 2026-10-26 from search results. On 2026-11-02 each figure in the spec was traced to the source listed below and checked against the page itself where it could be opened; the table records how each was checked. Most figures still come from vendors or company self-reports, including Anthropic's own, and vendors that sell measurement tools have a reason to find problems worth measuring. Only the METR trial is a controlled study. The maturity levels, tier definitions and dimension list are proposals, not validated standards. No study measures how much "missing developer headcount" is relabeling or redistribution, so the readiness-to-headcount link is a hypothesis.

## Sources

**Figures used in this spec** (checked 2026-11-02)

| Claim | Source | Type | How checked |
| --- | --- | --- | --- |
| Merges rose from about 2,500 a day (May 2026) to over 30,000 (September); the bottleneck is infrastructure built for human scale | Anthropic, [Redesigning source control at Anthropic](https://www.anthropic.com/engineering/redesigning-source-control), 2026-10-13 | Company self-report | Opened; quoted |
| Claude Code repos merge with at most one human in the loop, with no increase in reverts or incidents; approvals and wait per PR tracked | [How the Claude Code team does code review](https://claude.dev/blog/solving-code-review-at-anthropic/) | Company self-report | Opened |
| Agentic PRs wait 5.3 times longer for pickup; AI-generated PR acceptance 32.7% against 84.4% | LinearB, [2026 Software Engineering Benchmarks Report](https://linearb.io/engineering-benchmarks/) | Vendor report | Opened the report page |
| PRs merged without any review up 31.3%; incidents-to-PR ratio up 242.7% | Faros AI, [Ten takeaways from the AI Engineering Report 2026: The Acceleration Whiplash](https://faros.ai/blog/ai-acceleration-whiplash-takeaways), 2026-04-12 | Vendor report | Opened the vendor's summary, not the full report |
| Median weekly PRs per developer up 75.5% over four quarters; 105% longer first-review wait at the highest-AI organizations; failed-deployment recovery flat | DX, [State of AI Impact in Engineering: Q3 Report](https://getdx.com/uploads/state-of-ai-impact-in-engineering-q3-report.pdf), 2026 | Vendor report | Opened; quoted |
| About 121,000 developers, 93% using AI, PR throughput up about 10% | DX "AI efficiency plateau" analysis, via [a summary on DEV](https://dev.to/mr_manushukla/the-2026-ai-coding-productivity-paradox-93-adoption-10-gains-and-what-engineering-leaders-3e3l) | Vendor analysis, secondary | DX's original not opened. Superseded in part by the Q3 report |
| Coding is roughly 20 to 30% of lead time | [AI coding productivity at scale: why the gains disappear](https://getunblocked.com/blog/ai-coding-gains-disappear-at-scale/) (Unblocked) | Vendor blog, an estimate | Opened. The estimate is the author's, not a measurement |
| Experienced developers 19% slower with early-2025 AI tools while believing they were faster | J. Becker et al. (METR), [Measuring the Impact of Early-2025 AI on Experienced Open-Source Developer Productivity](https://arxiv.org/abs/2507.09089), 2025 | Randomized controlled trial, 16 developers, 246 tasks | Abstract read |

**Background reading** (opened, not cited for a figure): [Addy Osmani, Agentic code review](https://addyosmani.com/blog/agentic-code-review/); [Why code review became the bottleneck](https://www.softwareseni.com/why-code-review-became-the-bottleneck-and-what-the-numbers-show/) (SoftwareSeni), a useful synthesis of the vendor reports above; M. N. Raida and D. Hou, [Early Adoption of Agentic Coding Tools by GitHub Projects](https://arxiv.org/abs/2607.14037) (2026), 25,264 agentic PRs, which finds that oversight is mostly one human per agent PR. It does not measure review waits, so it is not cited for them.

**Name.** W. M. Cohen and D. A. Levinthal, "Absorptive Capacity: A New Perspective on Learning and Innovation," *Administrative Science Quarterly* 35(1), 128–152, 1990. [doi:10.2307/2393553](https://doi.org/10.2307/2393553) (citation record checked).

**Sources for "One principle, several laws"** (checked 2026-10-26; "opened" means the page was read in the drafting session, otherwise the link comes from a search result)

- Amdahl's law: G. M. Amdahl, "Validity of the single processor approach to achieving large scale computing capabilities" (1967). [PDF](https://www3.cs.stonybrook.edu/~rezaul/Spring-2019/CSE613/reading/Amdahl-1967.pdf), [IEEE record](https://ieeexplore.ieee.org/document/4785615) (not opened).
- Theory of constraints: E. Goldratt and J. Cox, *The Goal* (1984). Secondary overview: [Flying Logic](https://docs.flyinglogic.com/thinking-with-flying-logic/overview-of-the-theory-of-constraints) (not opened).
- Little's law: J. D. C. Little, "A Proof for the Queuing Formula: L = λW", Operations Research (1961). [Citation record](https://www.citedrive.com/en/discovery/a-proof-for-the-queuing-formula-ili-%CE%BBiwi) and [50th anniversary retrospective](https://pubsonline.informs.org/doi/fpi/10.1287/opre.1110.0940) (not opened).
- Queueing theory near full utilization: J. F. C. Kingman, "The single server queue in heavy traffic" (1961). [Kingman's formula](https://en.wikipedia.org/wiki/Kingman%27s_formula) (opened; the page confirms the 1961 paper and the formula's accuracy near saturation).
- Brooks's law: F. Brooks, *The Mythical Man-Month* (1975). [Overview](https://en.wikipedia.org/wiki/The_Mythical_Man-Month) (opened).
- Goodhart's law: originally a remark by economist Charles Goodhart on UK monetary policy; the popular wording is from Marilyn Strathern's paper "Improving Ratings: Audit in the British University System". [A New Morality of Attainment](https://unintendedconsequenc.es/new-morality-of-attainment-goodharts-law/) (opened).
- Conway's law: M. Conway, "How Do Committees Invent?" (1968). [O'Reilly excerpt](https://www.oreilly.com/library/view/making-software/9780596808310/ch11s01.html) and [interview with Conway](https://stefanlesser.substack.com/p/voices-on-software-design-melvin) (not opened).

The "What it means here" column in the laws table is this framework's own interpretation, not a claim made by the original authors.
