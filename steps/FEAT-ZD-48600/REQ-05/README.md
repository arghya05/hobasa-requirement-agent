# REQ-05 · Product Requirement Preparation

**Agent:** Requirement · **Item:** FEAT-ZD-48600 · **Status:** ✅ done · approved in run-20261025-201308-feat-zd-48600, reused
**Approved by:** PM: approve by sim.pm

**What this step does:** drafts the PRD carrying approved BRD decisions forward and runs the validation check

**Expected outcome:** Product Requirement Document

**Started by:** BRD approved

## Input: what the agent received

| # | Input | What it is | Produced by | Open |
|---|---|---|---|---|
| 1 | `feat.brd` | Approved BRD | — | not applicable for this item, or passed by reference |
| 2 | `org.templates` | BRD, PRD, TRD and story templates; business question set; EARS/Gherkin rules | — | not applicable for this item, or passed by reference |

The full brief the agent was given, attempt by attempt: `brief_attempt<N>.md` in this folder.

## Output: what the agent produced

| # | Output | What it is | Open |
|---|---|---|---|
| 1 | `feat.prd` | Approved PRD | [Markdown](https://github.com/arghya05/hobasa-requirement-agent/blob/main/outputs/FEAT-ZD-48600/feat.prd.md) · [HTML](https://htmlpreview.github.io/?https://raw.githubusercontent.com/arghya05/hobasa-requirement-agent/main/docs/FEAT-ZD-48600/REQ-05_feat-prd.html) · [PDF](https://github.com/arghya05/hobasa-requirement-agent/blob/main/docs/FEAT-ZD-48600/REQ-05_feat-prd.pdf) |

## Human evaluation

| Role | By | Decision | Scores (correct, complete, grounded, useful) | Comment or reason |
|---|---|---|---|---|
| PM | sim.pm | approve | — | automated checks and the independent judge passed |

## Files in this folder (audit trail)

- `brief_attempt<N>.md`: the exact brief the agent received
- `result_attempt<N>.json`: the agent's structured answer (approach, tools, claims with their sources, open questions)
- `checks_attempt<N>.json`: what the automated guardrail checks found
- `judge_attempt<N>.json`, `judge_brief_attempt<N>.md`: the independent judge
- `outputs/`: the outputs as approved
