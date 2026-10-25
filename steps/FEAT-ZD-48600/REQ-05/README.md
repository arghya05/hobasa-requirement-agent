# REQ-05 Product Requirement Preparation (Requirement agent)

**Item:** FEAT-ZD-48600 · **status:** done
**Trigger:** BRD approved  
**Action:** drafts the PRD carrying approved BRD decisions forward and runs the validation check  
**Outcome expected:** Product Requirement Document

## Inputs (what the agent was given)

| Item | Prepared input (this repository) | Read from (producer in GitHub) | Commit | Produced by |
|---|---|---|---|---|
| feat.brd | hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-05/feat.brd.md | hobasa-requirement-agent/outputs/FEAT-ZD-48600/feat.brd.md | 517ceb7 | REQ-04 |
| org.templates | hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-05/org.templates.md | hobasa-agentic-sdlc/org/org.templates.md | 9fbbfba | source |

Full brief per attempt: `brief_attempt<N>.md` (trigger event, owner answers, tool view, refusal reasons).

## Outputs (what the agent produced)

| Item | GitHub file |
|---|---|
| feat.prd | hobasa-requirement-agent/outputs/FEAT-ZD-48600/feat.prd.md |

## How the agent worked

- Approach: Attempt 2 fixes the single G1 refusal. The old NFR-10, "Runtimes are unchanged: ... Python 3.9 ... Node.js 22 CommonJS", turned the runtime description in org.architecture into a requirement that no source states. I removed it from the non-functional requirements. It now appears below the table as a labelled background note: org.architecture describes those runtimes, no input sets a runtime requirement, and runtime matters are left to the TRD. The former NFR-11 (terminology) and NFR-12 (performance targets) are renumbered NFR-10 and NFR-11. Their references in OQ-B2, PQ-4 and the traceability table are updated to match. I checked that the remaining "unchanged" statement is sourced. NFR-9, the feed schedule, is backed by BRD S-1 ("The schedule is unchanged") and by org.customer_mappings ("(unchanged)"), and both are now quoted in its source cell. A new validation-check row confirms that every NFR is backed by a BRD item, a decision, a lesson or a stated source rule. I rewrote feat.prd in full. All other content is the same as attempt 1, after the verifier fixes from that attempt (AC-2 limited to paid rows so OQ-B6 stays open; "So that" clauses and P-A4 labelled as judgement).
- Tools used: Skill (requirement-steps), Read, Write, Edit, Grep, Agent (verifier, attempt 1)
- Helper subagents: Agent
- Connector calls: none

## Attempts (checks before any person saw the output)

| Attempt | Session | Checks failed | Judge unsupported | Judge scores |
|---|---|---|---|---|
| 1 | new | 1 | 1 | {'correct': 5, 'complete': 5, 'grounded': 5, 'useful': 5} |
| 2 | resumed | 0 | 0 | {'correct': 5, 'complete': 5, 'grounded': 5, 'useful': 5} |

Details: `result_attempt<N>.json` (claims with sources), `checks_attempt<N>.json`, `judge_attempt<N>.json`.

## Human evaluation

| Role | By | Decision | Scores | Comment or reason |
|---|---|---|---|---|
| PM | sim.pm | approve | — | automated checks and the independent judge passed |
