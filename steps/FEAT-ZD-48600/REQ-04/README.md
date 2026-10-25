# REQ-04 · BRD Preparation

**Agent:** Requirement · **Item:** FEAT-ZD-48600 · **Status:** ✅ done · approved in run-20261025-201308-feat-zd-48600, reused
**Approved by:** Leadership: approve by sim.leadership

**What this step does:** asks the business question set, drafts the BRD against the template and runs the validation check

**Expected outcome:** Business Requirement Document

**Started by:** Previous Step

## Input: what the agent received

| # | Input | What it is | Produced by | Open |
|---|---|---|---|---|
| 1 | `feat.fitment` | Fitment verdict with evidence and reason code | — | not applicable for this item, or passed by reference |
| 2 | `feat.intake` | Original intake item with source link | — | not applicable for this item, or passed by reference |
| 3 | `org.templates` | BRD, PRD, TRD and story templates; business question set; EARS/Gherkin rules | — | not applicable for this item, or passed by reference |
| 4 | `org.strategy_capability` | Product capability, strategy and vision for fitment | — | not applicable for this item, or passed by reference |
| 5 | `org.decision_log` | Prior leadership and product decisions | — | not applicable for this item, or passed by reference |

The full brief the agent was given, attempt by attempt: `brief_attempt<N>.md` in this folder.

## Output: what the agent produced

| # | Output | What it is | Open |
|---|---|---|---|
| 1 | `feat.brd` | Approved BRD | [Markdown](https://github.com/arghya05/hobasa-requirement-agent/blob/main/outputs/FEAT-ZD-48600/feat.brd.md) · [HTML](https://htmlpreview.github.io/?https://raw.githubusercontent.com/arghya05/hobasa-requirement-agent/main/docs/FEAT-ZD-48600/REQ-04_feat-brd.html) · [PDF](https://github.com/arghya05/hobasa-requirement-agent/blob/main/docs/FEAT-ZD-48600/REQ-04_feat-brd.pdf) |

## Human evaluation

| Role | By | Decision | Scores (correct, complete, grounded, useful) | Comment or reason |
|---|---|---|---|---|
| Leadership | sim.leadership | approve | — | automated checks and the independent judge passed |

## Files in this folder (audit trail)

- `brief_attempt<N>.md`: the exact brief the agent received
- `result_attempt<N>.json`: the agent's structured answer (approach, tools, claims with their sources, open questions)
- `checks_attempt<N>.json`: what the automated guardrail checks found
- `judge_attempt<N>.json`, `judge_brief_attempt<N>.md`: the independent judge
- `outputs/`: the outputs as approved
