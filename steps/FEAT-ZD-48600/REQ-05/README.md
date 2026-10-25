# REQ-05 · Product Requirement Preparation

**Agent:** Requirement · **Item:** FEAT-ZD-48600 · **Status:** ✅ done · approved in an earlier run, reused
**Approved by:** PM: approve by sim.pm

**What this step does:** drafts the PRD carrying approved BRD decisions forward and runs the validation check

**Expected outcome:** Product Requirement Document

**Started by:** BRD approved

## Input: what the agent received

| # | Input | What it is | Produced by | Open |
|---|---|---|---|---|
| 1 | `feat.brd` | Approved BRD | Requirement agent · REQ-04 | [input copy](https://github.com/arghya05/hobasa-agentic-sdlc/blob/main//Users/arghyamukherjee/Documents/automaiton/final_document/e2e-run/runs/run-20261025-111239-feat-zd-48600/workspace/agents/hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-05/feat.brd.md) · [original](https://github.com/arghya05/hobasa-requirement-agent/blob/main/outputs/FEAT-ZD-48600/feat.brd.md) · [HTML](https://htmlpreview.github.io/?https://raw.githubusercontent.com/arghya05/hobasa-requirement-agent/main/docs/FEAT-ZD-48600/REQ-04_feat-brd.html) · [PDF](https://github.com/arghya05/hobasa-requirement-agent/blob/main/docs/FEAT-ZD-48600/REQ-04_feat-brd.pdf) |
| 2 | `org.templates` | BRD, PRD, TRD and story templates; business question set; EARS/Gherkin rules | organisation source | [input copy](https://github.com/arghya05/hobasa-agentic-sdlc/blob/main//Users/arghyamukherjee/Documents/automaiton/final_document/e2e-run/runs/run-20261025-111239-feat-zd-48600/workspace/agents/hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-05/org.templates.md) · [original](https://github.com/arghya05/hobasa-agentic-sdlc/blob/main/org/org.templates.md) |

The full brief the agent was given, attempt by attempt: `brief_attempt<N>.md` in this folder.

## Output: what the agent produced

| # | Output | What it is | Open |
|---|---|---|---|
| 1 | `feat.prd` | Approved PRD | [Markdown](https://github.com/arghya05/hobasa-requirement-agent/blob/main/outputs/FEAT-ZD-48600/feat.prd.md) · [HTML](https://htmlpreview.github.io/?https://raw.githubusercontent.com/arghya05/hobasa-requirement-agent/main/docs/FEAT-ZD-48600/REQ-05_feat-prd.html) · [PDF](https://github.com/arghya05/hobasa-requirement-agent/blob/main/docs/FEAT-ZD-48600/REQ-05_feat-prd.pdf) |

## Checks and approval

| Attempt | Session | Problems found by the checks | Unsupported statements (judge) | Judge scores |
|---|---|---|---|---|
| 1 | new | 1 | 1 | {'correct': 5, 'complete': 5, 'grounded': 5, 'useful': 5} |
| 2 | continued | 0 | 0 | {'correct': 5, 'complete': 5, 'grounded': 5, 'useful': 5} |

## How the agent worked

- **Approach:** Attempt 2 fixes the single G1 refusal. The old NFR-10, "Runtimes are unchanged: ... Python 3.9 ... Node.js 22 CommonJS", turned the runtime description in org.architecture into a requirement that no source states. I removed it from the non-functional requirements. It now appears below the table as a labelled background note: org.architecture describes those runtimes, no input sets a runtime requirement, and runtime matters are left to the TRD. The former NFR-11 (terminology) and NFR-12 (performance targets) are renumbered NFR-10 and NFR-11. Their references in OQ-B2, PQ-4 and the traceability table are updated to match. I checked that the remaining "unchanged" statement is sourced. NFR-9, the feed schedule, is backed by BRD S-1 ("The schedule is unchanged") and by org.customer_mappings ("(unchanged)"), and both are now quoted in its source cell. A new validation-check row confirms that every NFR is backed by a BRD item, a decision, a lesson or a stated source rule. I rewrote feat.prd in full. All other content is the same as attempt 1, after the verifier fixes from that attempt (AC-2 limited to paid rows so OQ-B6 stays open; "So that" clauses and P-A4 labelled as judgement).
- **Tools used:** Skill (requirement-steps), Read, Write, Edit, Grep, Agent (verifier, attempt 1)
- **Helper subagents:** Agent
- **Connector calls:** none

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
