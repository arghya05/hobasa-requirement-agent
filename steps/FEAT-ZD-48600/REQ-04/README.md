# REQ-04 · BRD Preparation

**Agent:** Requirement · **Item:** FEAT-ZD-48600 · **Status:** ✅ done · approved in an earlier run, reused
**Approved by:** Leadership: approve by sim.leadership

**What this step does:** asks the business question set, drafts the BRD against the template and runs the validation check

**Expected outcome:** Business Requirement Document

**Started by:** Previous Step

## Input: what the agent received

| # | Input | What it is | Produced by | Open |
|---|---|---|---|---|
| 1 | `feat.fitment` | Fitment verdict with evidence and reason code | Requirement agent · REQ-03 | [input copy](https://github.com/arghya05/hobasa-requirement-agent/blob/main/inputs/FEAT-ZD-48600/REQ-04/feat.fitment.md) · [original](https://github.com/arghya05/hobasa-requirement-agent/blob/main/outputs/FEAT-ZD-48600/feat.fitment.md) · [HTML](https://htmlpreview.github.io/?https://raw.githubusercontent.com/arghya05/hobasa-requirement-agent/main/docs/FEAT-ZD-48600/REQ-03_feat-fitment.html) · [PDF](https://github.com/arghya05/hobasa-requirement-agent/blob/main/docs/FEAT-ZD-48600/REQ-03_feat-fitment.pdf) |
| 2 | `feat.intake` | Original intake item with source link | Requirement agent · REQ-01 | [input copy](https://github.com/arghya05/hobasa-requirement-agent/blob/main/inputs/FEAT-ZD-48600/REQ-04/feat.intake.md) · [original](https://github.com/arghya05/hobasa-requirement-agent/blob/main/outputs/FEAT-ZD-48600/feat.intake.md) · [HTML](https://htmlpreview.github.io/?https://raw.githubusercontent.com/arghya05/hobasa-requirement-agent/main/docs/FEAT-ZD-48600/REQ-01_feat-intake.html) · [PDF](https://github.com/arghya05/hobasa-requirement-agent/blob/main/docs/FEAT-ZD-48600/REQ-01_feat-intake.pdf) |
| 3 | `org.templates` | BRD, PRD, TRD and story templates; business question set; EARS/Gherkin rules | organisation source | [input copy](https://github.com/arghya05/hobasa-requirement-agent/blob/main/inputs/FEAT-ZD-48600/REQ-04/org.templates.md) · [original](https://github.com/arghya05/hobasa-agentic-sdlc/blob/main/org/org.templates.md) |
| 4 | `org.strategy_capability` | Product capability, strategy and vision for fitment | organisation source | [input copy](https://github.com/arghya05/hobasa-requirement-agent/blob/main/inputs/FEAT-ZD-48600/REQ-04/org.strategy_capability.md) · [original](https://github.com/arghya05/hobasa-agentic-sdlc/blob/main/org/org.strategy_capability.md) |
| 5 | `org.decision_log` | Prior leadership and product decisions | organisation source | [input copy](https://github.com/arghya05/hobasa-requirement-agent/blob/main/inputs/FEAT-ZD-48600/REQ-04/org.decision_log.md) · [original](https://github.com/arghya05/hobasa-agentic-sdlc/blob/main/org/org.decision_log.md) |

The full brief the agent was given, attempt by attempt: `brief_attempt<N>.md` in this folder.

## Output: what the agent produced

| # | Output | What it is | Open |
|---|---|---|---|
| 1 | `feat.brd` | Approved BRD | [Markdown](https://github.com/arghya05/hobasa-requirement-agent/blob/main/outputs/FEAT-ZD-48600/feat.brd.md) · [HTML](https://htmlpreview.github.io/?https://raw.githubusercontent.com/arghya05/hobasa-requirement-agent/main/docs/FEAT-ZD-48600/REQ-04_feat-brd.html) · [PDF](https://github.com/arghya05/hobasa-requirement-agent/blob/main/docs/FEAT-ZD-48600/REQ-04_feat-brd.pdf) |

## Checks and approval

| Attempt | Session | Problems found by the checks | Unsupported statements (judge) | Judge scores |
|---|---|---|---|---|
| 1 | continued | 0 | 0 | {'correct': 5, 'complete': 4, 'grounded': 5, 'useful': 5} |
| 2 | continued | 1 | 1 | {'correct': 5, 'complete': 5, 'grounded': 4, 'useful': 5} |
| 3 | continued | 3 | 3 | {'correct': 4, 'complete': 5, 'grounded': 4, 'useful': 5} |

## How the agent worked

- **Approach:** Attempt 3 fixes the single G1 refusal, and feat.brd is rewritten in full. SM-5 said "No existing function signature changes", which was stronger than the source. It now quotes the architecture rule exactly: "Keep every existing signature; add new functions". It says the new behaviour comes from four new functions (CR-2, CR-3, CR-5, CR-6). It names the one change to an existing function: CR-4 adds an optional `risk` argument to `build_explanation_request`, which feat.classification calls additive. That callers who don't pass `risk` get today's prompt stays assumption B-A6. I then searched the file for the same overstatement. Two more places made it, and I reworded both. The section 4 intro said "Existing behaviour is kept"; it now quotes the rule and names the two additive changes, CR-1 and CR-4, citing feat.classification. OS-6 now reads "Changes to existing signatures beyond the two additive changes named in section 4". Everything else carries over from attempt 2: the file: citation form, the corrected SM-3, the template-ordered sections, the business question set and the validation check.
- **Tools used:** Skill:requirement-steps, Read, Glob, Grep, mcp__hobasa-context__context_list, mcp__hobasa-context__context_get, mcp__hobasa-context__memory_search, Write, Edit, Agent:verifier
- **Helper subagents:** Agent
- **Connector calls:** none

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
