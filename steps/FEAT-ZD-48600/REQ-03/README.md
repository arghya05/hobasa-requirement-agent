# REQ-03 · Product Fitment Validation

**Agent:** Requirement · **Item:** FEAT-ZD-48600 · **Status:** ✅ done · approved in run-20261025-201308-feat-zd-48600, reused
**Approved by:** PM: approve by sim.pm; Leadership: approve by sim.leadership

**What this step does:** Checks the entry against capability, roadmap and strategy and returns a verdict with its evidence : Yes or No

**Expected outcome:** Fitment verdict with evidence. Notification to PM and Leadership to decide
Yes or No ³

**Started by:** Previous Grouping

## Input: what the agent received

| # | Input | What it is | Produced by | Open |
|---|---|---|---|---|
| 1 | `feat.classification` | Category, qualifier and merged duplicates | — | not applicable for this item, or passed by reference |
| 2 | `org.strategy_capability` | Product capability, strategy and vision for fitment | — | not applicable for this item, or passed by reference |
| 3 | `org.roadmap` | Structured roadmap items | — | not applicable for this item, or passed by reference |

The full brief the agent was given, attempt by attempt: `brief_attempt<N>.md` in this folder.

## Output: what the agent produced

| # | Output | What it is | Open |
|---|---|---|---|
| 1 | `feat.fitment` | Fitment verdict with evidence and reason code | [Markdown](https://github.com/arghya05/hobasa-requirement-agent/blob/main/outputs/FEAT-ZD-48600/feat.fitment.md) · [HTML](https://htmlpreview.github.io/?https://raw.githubusercontent.com/arghya05/hobasa-requirement-agent/main/docs/FEAT-ZD-48600/REQ-03_feat-fitment.html) · [PDF](https://github.com/arghya05/hobasa-requirement-agent/blob/main/docs/FEAT-ZD-48600/REQ-03_feat-fitment.pdf) |

## Human evaluation

| Role | By | Decision | Scores (correct, complete, grounded, useful) | Comment or reason |
|---|---|---|---|---|
| PM | sim.pm | approve | — | automated checks and the independent judge passed |
| Leadership | sim.leadership | approve | — | automated checks and the independent judge passed |

## Files in this folder (audit trail)

- `brief_attempt<N>.md`: the exact brief the agent received
- `result_attempt<N>.json`: the agent's structured answer (approach, tools, claims with their sources, open questions)
- `checks_attempt<N>.json`: what the automated guardrail checks found
- `judge_attempt<N>.json`, `judge_brief_attempt<N>.md`: the independent judge
- `outputs/`: the outputs as approved
