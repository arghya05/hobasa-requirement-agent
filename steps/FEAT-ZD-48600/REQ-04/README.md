# REQ-04 BRD Preparation (Requirement agent)

**Item:** FEAT-ZD-48600 · **status:** blocked
**Trigger:** Previous Step  
**Action:** asks the business question set, drafts the BRD against the template and runs the validation check  
**Outcome expected:** Business Requirement Document

## Inputs (what the agent was given)

| Item | Prepared input (this repository) | Read from (producer in GitHub) | Commit | Produced by |
|---|---|---|---|---|
| feat.fitment | hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-04/feat.fitment.md | hobasa-requirement-agent/outputs/FEAT-ZD-48600/feat.fitment.md | 3603ae6 | REQ-03 |
| feat.intake | hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-04/feat.intake.md | hobasa-requirement-agent/outputs/FEAT-ZD-48600/feat.intake.md | fd588b3 | REQ-01 |
| org.templates | hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-04/org.templates.md | hobasa-agentic-sdlc/org/org.templates.md | bf63f34 | source |
| org.strategy_capability | hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-04/org.strategy_capability.md | hobasa-agentic-sdlc/org/org.strategy_capability.md | bf63f34 | source |
| org.decision_log | hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-04/org.decision_log.md | hobasa-agentic-sdlc/org/org.decision_log.md | bf63f34 | source |

Full brief per attempt: `brief_attempt<N>.md` (trigger event, owner answers, tool view, refusal reasons).

## Outputs (what the agent produced)

| Item | GitHub file |
|---|---|
| feat.brd | — |

## How the agent worked

- Approach: Attempt 3 fixes the three G1 refusals, and I rewrote feat.brd in full. (1) Header: I removed the uncited sentence "Leadership approves; the PM owns the item". The header table now has two separately sourced rows. The REQ-04 gate is Leadership, from the requirement-steps skill file (REQ-04, "Gate: Leadership"), which I read with Grep. The owner of the Pre Backlog entry is PM, from journey:feat.prebacklog. (2) Approvals: the Leadership row now cites that skill file only, and the PM row cites journey:feat.prebacklog. The OQ-B1 and OQ-B2 owners are stated only as feat.fitment records them: OQ-F1 is owned by PM / Leadership and OQ-F3 by Leadership. The table no longer says those roles "decide" them. (3) BR-10 now follows CR-4 exactly: `build_explanation_request` takes an optional `risk` argument, and when it is given the prompt it builds ends with " Risk level: <risk>.". The uncited "explanation is unchanged" clause became assumption B-A5. S-4 is reworded the same way and cites only feat.intake. Everything else carries over from attempt 2: the template-ordered BRD, the business question set, the validation check, the attempt-1 verifier fixes, and no mcp: citations.
- Tools used: Skill:requirement-steps, Read, Glob, Grep, mcp__hobasa-context__context_list, mcp__hobasa-context__context_get, mcp__hobasa-context__memory_search, Write, Edit, Agent:verifier
- Helper subagents: Agent
- Connector calls: none

## Attempts (checks before any person saw the output)

| Attempt | Session | Checks failed | Judge unsupported | Judge scores |
|---|---|---|---|---|
| 1 | new | 1 | — | — |
| 2 | resumed | 3 | 3 | {'correct': 4, 'complete': 4, 'grounded': 4, 'useful': 4} |
| 3 | resumed | 1 | 1 | {'correct': 5, 'complete': 5, 'grounded': 4, 'useful': 5} |

Details: `result_attempt<N>.json` (claims with sources), `checks_attempt<N>.json`, `judge_attempt<N>.json`.
