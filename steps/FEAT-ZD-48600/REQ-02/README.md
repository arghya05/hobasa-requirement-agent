# REQ-02 · Grouping

**Agent:** Requirement · **Item:** FEAT-ZD-48600 · **Status:** ✅ done · approved in run-20261025-201308-feat-zd-48600, reused
**Approved by:** PM: approve by sim.pm

**What this step does:** New Ticket gets created

**Expected outcome:** Entry classified by category, duplicates merged

**Started by:** Previous Requirement Intake
Technical has to be a sub-category under each and should be classified as Technical Only
This could go as a qualifier during requirement approval or as applicable ²

## Input: what the agent received

| # | Input | What it is | Produced by | Open |
|---|---|---|---|---|
| 1 | `feat.prebacklog` | Pre-backlog entry linked to roadmap and trace ID | — | not applicable for this item, or passed by reference |
| 2 | `feat.intake` | Original intake item with source link | — | not applicable for this item, or passed by reference |
| 3 | `org.routing_map` | Component-to-owner routing for defects | — | not applicable for this item, or passed by reference |
| 4 | `org.architecture` | Platform architecture, contracts and tenancy rules | — | not applicable for this item, or passed by reference |

The full brief the agent was given, attempt by attempt: `brief_attempt<N>.md` in this folder.

## Output: what the agent produced

| # | Output | What it is | Open |
|---|---|---|---|
| 1 | `feat.classification` | Category, qualifier and merged duplicates | [Markdown](https://github.com/arghya05/hobasa-requirement-agent/blob/main/outputs/FEAT-ZD-48600/feat.classification.md) · [HTML](https://htmlpreview.github.io/?https://raw.githubusercontent.com/arghya05/hobasa-requirement-agent/main/docs/FEAT-ZD-48600/REQ-02_feat-classification.html) · [PDF](https://github.com/arghya05/hobasa-requirement-agent/blob/main/docs/FEAT-ZD-48600/REQ-02_feat-classification.pdf) |

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
