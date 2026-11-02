# Changelog

## 0.1.0 (unreleased)

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

### 2026-10-26: first draft

- Framework, assessment page, validation plan, historical note and case-study template drafted in a working session.
