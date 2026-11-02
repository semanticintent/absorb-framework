# Prior art and positioning

ABSORB is not the first readiness framework for AI in software delivery, and its central observation is not new. This file records what related work says, where ABSORB overlaps with it, and what ABSORB adds. Each entry states how it was read. Last checked 2026-11-02.

## The short version

DORA's 2025 report already makes ABSORB's core argument: AI is an amplifier, and the returns come from the organizational system around the tools. DORA's capability catalogue also covers value-stream visibility and lightweight change approval. ABSORB should cite DORA as the main prior work and claim only what it adds:

1. **A whole-path speedup check from stage timing.** It separates hands-on time from waiting and applies Amdahl's law to estimate how much a faster stage can lift the whole path.
2. **Autonomy tiers tied to an evidence floor.** It states which change types may merge with no human, one human, or a board, and derives readiness for each tier from the weakest of verification, governance, platform and ownership.
3. **A small, falsifiable instrument.** It has 24 statements, a written scoring rule, an offline assessment page and pre-registered hypotheses (`VALIDATION.md`).

## Related frameworks

### DORA: State of AI-assisted Software Development (2025) and the AI Capabilities Model

- **Read:** the report's landing page, the AI Capabilities Model page, and two capability guides, [Visibility of work in the value stream](https://dora.dev/capabilities/work-visibility-in-value-stream/) and [Streamlining change approval](https://dora.dev/capabilities/streamlining-change-approval/). The full report PDF was not read.
- **What it says:** "AI's primary role is as an amplifier, magnifying an organization's existing strengths and weaknesses." "The greatest returns on AI investment come not from the tools themselves, but from a strategic focus on the underlying organizational system." The companion model names seven capabilities that amplify the benefits of AI. They are listed in the report, which was not read.
- **Value stream guide:** recommends mapping 5 to 15 process blocks from idea to customer and recording lead time and process time for each. It notes that "improving efficiency in areas that aren't bottlenecks won't have much impact on overall lead times," but gives no quantitative model, and the page does not mention AI.
- **Change approval guide:** favors peer review with automated checks over approval boards, warns against "treating all changes equally," and suggests extra scrutiny for high-risk changes. It does not define tiers or mention AI agents.
- **Overlap with ABSORB:** the thesis; D1 (value stream); D3 (risk-based approval); D5 and D7 through DORA's platform, CI and measurement capabilities.
- **Where ABSORB differs:** it adds the hands-on/wait split with an explicit speedup estimate, autonomy tiers for agent-authored change with evidence thresholds, and a scored self-assessment with a written rule. DORA is a far larger research program with survey data behind it, which ABSORB does not have.
- **Treatment:** cite DORA as the source of the amplifier finding. Map D1 to D8 to DORA capabilities in a later version (open question).

### Codurance: Data and AI Readiness Assessment (DARA)

- **Read:** the [assessment page](https://www.codurance.com/data-ai-readiness-assessment). The draft's original link (`/ai-readiness-assessment`) now redirects here.
- **What it is:** a paid three-to-four-week consultancy engagement. It assesses whether platforms, data and delivery capability can support AI agents that automate business processes. It has six pillars: use case identification and agent design; platform and API readiness; data engineering readiness; data governance and AI compliance; agent delivery capability; capacity and skills.
- **Overlap:** the governance pillar asks what actions an agent may take and who authorizes them, which is close to ABSORB's tiers.
- **Difference:** DARA is about deploying agents into business processes, not about the software delivery path, and it does not cover review queues or delivery stages. Codurance lists a separate "AI Engineering Assessment" for the engineering lifecycle. **Not read:** no public description was found. It is the closer comparison and should be checked before release.

### Augment Code: AI readiness assessment framework

- **Read:** the [guide](https://www.augmentcode.com/guides/ai-readiness-assessment-framework).
- **What it is:** a vendor guide that compiles several existing models rather than defining one. Its main pillar set has seven entries: Strategy and Leadership, Data Foundations, Technology/Infrastructure, Talent/Skills, Governance and Ethics, Culture and Change Readiness, Engineering/Delivery. The checklist questions are scored 1 to 5, and any dimension below 3.0 is treated as a blocker. It cites Gartner and MIT CISR maturity models.
- **Overlap:** it uses DORA-style delivery metrics, says to address bottlenecks outside coding, and asks whether senior review load is manageable.
- **Difference:** it has no stage-level timing, no autonomy levels tied to evidence, no downloadable tool and no single scoring rule. Its "blocker below 3.0" rule plays the same role as ABSORB's weakest-dimension cap, which is worth acknowledging.

### Agentic AI Readiness: A Process-Oriented Assessment Framework (University of Hawaiʻi ScholarSpace)

- **Not read.** The [record page](https://scholarspace.manoa.hawaii.edu/items/174fe069-9545-4445-96ef-9cf693bd87ea) blocked automated access on 2026-11-02. Its title suggests it is the closest academic work. Read it before release, or remove it from this list.

### Company self-reports: Anthropic

- **Read:** [Redesigning source control at Anthropic](https://www.anthropic.com/engineering/redesigning-source-control) (2026-10-13) and [How the Claude Code team does code review](https://claude.dev/blog/solving-code-review-at-anthropic/).
- **Use in ABSORB:** a worked example of the constraint moving (from coding to source control, builds and CI) and of a level 4 setup. These are self-reports from one unusual organization, not evidence for the framework.

## Foundational ideas

| Idea | Role in ABSORB |
| --- | --- |
| Amdahl's law, theory of constraints, Little's law, queueing theory (Kingman), Brooks's law, Goodhart's law, Conway's law | Lenses on one principle: the slowest stage sets the pace and the constraint moves. Sources and caveats are in `SPEC.md`. |
| Absorptive capacity (Cohen and Levinthal, 1990, [doi:10.2307/2393553](https://doi.org/10.2307/2393553)) | The source of the name. It is a firm's ability to recognize, assimilate and apply new outside knowledge. ABSORB applies the intuition to delivery capacity rather than learning. ABSORB does not claim to measure absorptive capacity in the original sense. |
| Value stream mapping (lean) | The method behind step 2. DORA's guide above is a current software-specific version. |

## Historical analogies

See `HISTORICAL_LENS.md` for an interpretive comparison with electrification (Paul David, 1990) and the dotcom era. It is context, not evidence for the framework.

## How ABSORB differs: hypotheses tested

The draft listed four claimed differences to check after reading the related work. Results:

| Claimed difference | Verdict | Basis |
| --- | --- | --- |
| ABSORB asks whether the system downstream of coding can absorb speed, not whether teams are ready to adopt AI tools | **Refuted as a difference from DORA**, confirmed against Codurance DARA and Augment | DORA's amplifier finding is the same argument. Present it as DORA's finding, not ABSORB's |
| It derives autonomy tiers from verification and governance evidence, not from a single maturity score | **Confirmed** for the works read; unclear for DORA's full report | None of the pages read defines tiers for agent-authored change. DORA's change-approval guide implies risk-based scrutiny without tiers |
| It pairs stage timing with an Amdahl-style speedup check, so the constraint is found from data | **Partly confirmed** | DORA's value-stream guide records lead and process time per block but gives no speedup model. No other work read does either |
| It is a self-contained, open, offline assessment with a written spec | **Confirmed, with one condition** | DARA is a paid engagement, Augment offers no tool, and DORA's quick check is an online survey. ABSORB is not open source until a `LICENSE` file is added |

## Related work by the author

ABSORB stands on its own and draws its theory from outside sources. These earlier records by the same author address neighboring questions. The lines below summarize each record's own description.

| Record | DOI | How it relates |
| --- | --- | --- |
| Governance-Driven Design (GDD): Formalizing Intent Before the Machine Runs, v0.1.0 | [10.5281/zenodo.20938778](https://doi.org/10.5281/zenodo.20938778) | Describes how to formalize constraints before agents run. ABSORB's D3 and D4 ask whether an organization has done that kind of work; GDD describes one way to do it |
| Capability-as-Infrastructure: Software on Demand, v0.1.0 | [10.5281/zenodo.23438908](https://doi.org/10.5281/zenodo.23438908) | States hypotheses with a validation protocol, the pattern `VALIDATION.md` follows |
| Governance-as-Infrastructure; The Synthesis Gate; Semantic Intent series; Agentic Traffic Control; TRACE; Machine Legibility Dimensions | DOIs to add | Cover where human judgment sits in agent pipelines, intent as a governed source, orchestration, execution records as audit evidence, and a dimension-rating framework of the same shape. Add a line for each once the DOIs are confirmed |

## Name check

- No framework named ABSORB was found in web searches on 2026-10-26 for AI readiness and software delivery.
- "Absorptive capacity" is an established academic concept (above). The name is chosen to echo it, and `SPEC.md` says so.
- GitHub, 2026-11-02: no framework or assessment named ABSORB. The most prominent use is [git-absorb](https://github.com/tummychow/git-absorb), a popular Git tool (about 5,700 stars). It is a different kind of thing, but it is in front of the same developer audience and will share search results. Prefer a qualified repository name such as `absorb-framework`.
- Zenodo, 2026-11-02: no record on delivery readiness. The nearest match is an unrelated "AbsORB" metadata corpus on online book reviews.
- Not yet done: a trademark database search (for example USPTO and CIPO) in the software and consulting classes. PROOF and SPAN remain fallbacks.
