# Changelog

## 0.2.0 (2026-11-02)

Version DOI [10.5281/zenodo.23898389](https://doi.org/10.5281/zenodo.23898389).

### Pipeline view

- The "Where a change waits" chart is now a pipeline view. Each stage is a block sized by elapsed days and split into hands-on time (solid) and waiting (light). The constraint is amber, the stage being changed is teal, and other stages are grey. Two rows, today and what-if, share one scale, so the effect of a change shows as a shorter path.
- Two sliders for one stage: **Work** (1 to 20 times faster) and **Waiting** (cut 0 to 90%). A large headline shows the whole-path speedup. Two "Try" buttons: make Build 10× faster, or halve the waiting at the constraint. On the example data these give 1.04× and 1.14×.
- Tooltips on hover and keyboard focus, and a "Show as a table" view, so no value is available only on hover.
- Chart colours were checked for contrast and colour-blind separation in light and dark mode.
- The spec gains the waiting term in the speedup formula. It is for exploring only and changes no score, level or tier.

### Compare with a colleague

- Each result has a short code (`ABSORB1-` plus 24 ratings and a check character). Paste a colleague's code to see both raters' dimension scores side by side, with agreement shown as a ring around the dot.
- Reports the average gap per dimension against the 0.5 aim in H5, how many statements agree within 1 point, a weighted kappa (marked indicative), and the statements where the two differ by 2 points or more, under "Talk about these first".
- Codes hold only the ratings. A mistyped code is caught by the check character. The comparison is included in the copied summary.

### Decision record

- State the constraint you believe in, the change you will make, and a prediction on one baseline metric (from, to, by a date). Save a snapshot of today's constraint, level and scores.
- At the next assessment, enter the actual value: the record says whether the prediction was met, partly met or not met, whether the constraint moved since the snapshot (H4), and which dimension scores changed. Included in the copied summary.

### Guided mode

- Answer one statement at a time, with large 0–4 buttons, keys 0–4 to answer and arrow keys to move, a progress strip, and "What counts as evidence" for each dimension. "All at once" keeps the original list. A fresh start opens in guided mode; the example opens in the list.

No change to the statements, scoring, level rule or tier thresholds.

## 0.1.1 (2026-11-02)

Version DOI [10.5281/zenodo.23896316](https://doi.org/10.5281/zenodo.23896316). Bug fixes to the assessment page. No change to the framework, scoring or wording.

- The Answer panel always showed below Results, because a display rule overrode the `hidden` attribute. The Results and Answer tabs now switch.
- Added `<!DOCTYPE html>` and a UTF-8 character encoding. Without them Safari showed "×" and "·" as garbled characters, and browsers rendered the page in quirks mode.
- Removed a leftover meta tag from the drafting tool.

## 0.1.0 (2026-11-02)

### 2026-11-02: review pass before first release

**Assessment and spec, kept in sync**

- Stage timing takes optional hands-on days. The whole-path speedup check now speeds up hands-on time only, because waiting does not shrink when the work gets faster. Without hands-on days, the result is shown as an upper bound ("at most"). Answers saved by the earlier page still load.
- Four statements now ask one thing each:
  - D2(2): "Checks are independent of the AI that wrote the code, and humans audit a sample of approvals" became "Changes are checked by tests or reviewers that are independent of the AI that wrote them."
  - D6(1): "named owner and an on-call rota" became "named owner."
  - D7(3): "reviewed on a schedule and change decisions" became "Reviews of these metrics regularly change decisions."
  - D8(2): "training and time … and roles reflect the new work" became "training and time to learn to work with AI tools."

  The dropped halves moved to the evidence column of the dimensions table.
- T3 shows that sign-off is still required, even when the evidence floor marks it Ready.
- The page no longer loads Google Fonts, so it makes no network requests.
- **No change** to the level rule, the autonomy floor or any tier threshold.

**Evidence**

- Every figure in `SPEC.md` was traced to a source and checked against the page where possible. Sources are now a table: claim, source, type, and how it was checked.
- Corrections:
  - Coding share is 20–30% of lead time, matching the cited source (was 25–35%).
  - The Anthropic "at most one human" setup is described as achieved, not as a goal.
  - The 25,264-PR paper (Raida and Hou, 2026) is no longer implied to support the review-wait figure, because it does not measure review waits.
- Added: Anthropic's primary post, LinearB, Faros AI and DX Q3 2026 reports, and the METR randomized trial.
- Removed: the unsourced claim that companies were reversing AI-driven cuts.

**Positioning**

- `PRIOR_ART.md` rewritten from what was actually read: DORA 2025 and two DORA capability guides, Codurance DARA, Augment Code, and the Anthropic posts. The "how ABSORB differs" claims are marked confirmed, partly confirmed or refuted. The main finding is that the amplifier thesis is DORA's.
- Defined "agentic". Explained the name through absorptive capacity (Cohen and Levinthal, 1990).
- Name check: no conflicting framework on GitHub or Zenodo. git-absorb, a popular Git tool, shares the name.

### 2026-11-02: released

- Published as v0.1.0 on GitHub and archived on Zenodo. Concept DOI [10.5281/zenodo.23895787](https://doi.org/10.5281/zenodo.23895787); v0.1.0 DOI [10.5281/zenodo.23895788](https://doi.org/10.5281/zenodo.23895788).

### 2026-11-02: license and repository name

- MIT license added for the whole repository, matching the author's other records. Planned repository: `semanticintent/absorb-framework`.

### 2026-10-26: first draft

- Framework, assessment page, validation plan, historical note and case-study template drafted in a working session.
