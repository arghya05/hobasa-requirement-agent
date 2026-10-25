# REQ-06 · Prototype ⁷

**Agent:** Requirement · **Item:** FEAT-ZD-48600 · **Status:** ✅ done · approved in an earlier run, reused
**Approved by:** UX lead: approve by sim.ux_lead

**What this step does:** builds the prototype prompt applying the design system, screen inventory, states and synthetic data rules, then checks the output against the PRD

**Expected outcome:** Low Fidelity Wireframes

**Started by:** PRD Reviewed

## Input: what the agent received

| # | Input | What it is | Produced by | Open |
|---|---|---|---|---|
| 1 | `feat.prd` | Approved PRD | Requirement agent · REQ-05 | [input copy](https://github.com/arghya05/hobasa-requirement-agent/blob/main/inputs/FEAT-ZD-48600/REQ-06/feat.prd.md) · [original](https://github.com/arghya05/hobasa-requirement-agent/blob/main/outputs/FEAT-ZD-48600/feat.prd.md) · [HTML](https://htmlpreview.github.io/?https://raw.githubusercontent.com/arghya05/hobasa-requirement-agent/main/docs/FEAT-ZD-48600/REQ-05_feat-prd.html) · [PDF](https://github.com/arghya05/hobasa-requirement-agent/blob/main/docs/FEAT-ZD-48600/REQ-05_feat-prd.pdf) |
| 2 | `org.design_library` | Hobasa design library and variables (tokens) | organisation source | [input copy](https://github.com/arghya05/hobasa-requirement-agent/blob/main/inputs/FEAT-ZD-48600/REQ-06/org.design_library.md) · [original](https://github.com/arghya05/hobasa-agentic-sdlc/blob/main/features/FEAT-ZD-48600/org-overrides/org.design_library.md) |

The full brief the agent was given, attempt by attempt: `brief_attempt<N>.md` in this folder.

## Output: what the agent produced

| # | Output | What it is | Open |
|---|---|---|---|
| 1 | `feat.prototype` | FigJam flow and Figma Make prototype | [Markdown](https://github.com/arghya05/hobasa-requirement-agent/blob/main/outputs/FEAT-ZD-48600/feat.prototype.md) · [HTML](https://htmlpreview.github.io/?https://raw.githubusercontent.com/arghya05/hobasa-requirement-agent/main/docs/FEAT-ZD-48600/REQ-06_feat-prototype.html) · [PDF](https://github.com/arghya05/hobasa-requirement-agent/blob/main/docs/FEAT-ZD-48600/REQ-06_feat-prototype.pdf) |

## Checks and approval

| Attempt | Session | Problems found by the checks | Unsupported statements (judge) | Judge scores |
|---|---|---|---|---|
| 1 | continued | 0 | 0 | {'correct': 5, 'complete': 4, 'grounded': 5, 'useful': 4} |
| 2 | continued | 1 | — | — |
| 3 | continued | 2 | 2 | {'correct': 5, 'complete': 4, 'grounded': 4, 'useful': 4} |

## How the agent worked

- **Approach:** Attempt 3 fixes the remaining G2 refusal. The citation file:ap_portal/src/ap_portal/index.js was not recognised as read in this step's context. So I removed it from the output and from the claims instead of relying on a read the checker does not see.

The background note that depended on that file (the existing aging-summary table and formatAmount) is gone. The amount-display rule now rests only on feat.prd:
- NFR-3: show two decimals "without converting it to a binary floating-point number"
- AC-18: the amount travels as a two-decimal string
- OQ-B10: how ap_portal formats the amount is left to the TRD

The attempt-2 fix still holds: no capabilities_list citation, and the "no Figma connector" point cites org.design_library and record:brief.

Before rewriting the file in full, I re-read both contracted inputs (feat.prd and org.design_library) in this session. A grep confirms that the output no longer contains ap_portal/src, index.js, formatAmount, capabilities_list or "tool view". Every claim now cites only feat.prd, org.design_library, record:memory or record:brief.

Nothing else in the design changed:
- the 4 design-library rules
- a one-screen inventory and five states
- a FigJam flow in Mermaid form
- ASCII low-fidelity wireframes for the populated and empty table
- synthetic data rules and a labelled dataset
- a Figma Make prompt with the basis of each rule
- a check against the PRD acceptance criteria and NFRs, and against the decision log
- **Tools used:** Read, Write, Grep
- **Helper subagents:** Agent
- **Connector calls:** none

## Human evaluation

| Role | By | Decision | Scores (correct, complete, grounded, useful) | Comment or reason |
|---|---|---|---|---|
| UX lead | sim.ux_lead | approve | — | automated checks and the independent judge passed |

## Files in this folder (audit trail)

- `brief_attempt<N>.md`: the exact brief the agent received
- `result_attempt<N>.json`: the agent's structured answer (approach, tools, claims with their sources, open questions)
- `checks_attempt<N>.json`: what the automated guardrail checks found
- `judge_attempt<N>.json`, `judge_brief_attempt<N>.md`: the independent judge
- `outputs/`: the outputs as approved
