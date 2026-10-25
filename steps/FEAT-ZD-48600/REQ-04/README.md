# REQ-04 BRD Preparation (Requirement agent)

**Item:** FEAT-ZD-48600 · **status:** done
**Trigger:** Previous Step  
**Action:** asks the business question set, drafts the BRD against the template and runs the validation check  
**Outcome expected:** Business Requirement Document

## Inputs (what the agent was given)

| Item | Prepared input (this repository) | Read from (producer in GitHub) | Commit | Produced by |
|---|---|---|---|---|
| feat.fitment | hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-04/feat.fitment.md | hobasa-requirement-agent/outputs/FEAT-ZD-48600/feat.fitment.md | 2bf67bd | REQ-03 |
| feat.intake | hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-04/feat.intake.md | hobasa-requirement-agent/outputs/FEAT-ZD-48600/feat.intake.md | 9919dd4 | REQ-01 |
| org.templates | hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-04/org.templates.md | hobasa-agentic-sdlc/org/org.templates.md | 9fbbfba | source |
| org.strategy_capability | hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-04/org.strategy_capability.md | hobasa-agentic-sdlc/org/org.strategy_capability.md | 9fbbfba | source |
| org.decision_log | hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-04/org.decision_log.md | hobasa-agentic-sdlc/org/org.decision_log.md | 9fbbfba | source |

Full brief per attempt: `brief_attempt<N>.md` (trigger event, owner answers, tool view, refusal reasons).

## Outputs (what the agent produced)

| Item | GitHub file |
|---|---|
| feat.brd | hobasa-requirement-agent/outputs/FEAT-ZD-48600/feat.brd.md |

## How the agent worked

- Approach: This attempt fixes all three G1 refusals and rewrites feat.brd in full.

1. SM-5 no longer says 'the only change to an existing function'. It now names both additive changes exactly as feat.classification records them ('Two changes touch existing behaviour, and both are additive'): CR-4, the optional argument on build_explanation_request; and CR-1, feed ingestion accepting the optional paid_date, with the new reject reason 'paid_date' and the new field Invoice.paid_date. The section 4 intro now lists the same two changes and the four new functions, citing feat.classification. OS-6 reads 'Changes to existing behaviour beyond the two additive changes'.
2. The R-AP-12 row no longer says the outcome 'delivers' the roadmap item. It says feat.fitment gives R-AP-12 as the linked roadmap item, and that feat.fitment's agent judgement is that the entry matches it. BQ-5 was reworded to match.
3. The auditability row and the strategy row are now labelled 'agent judgement, recorded in feat.fitment', with the underlying source facts kept separate. My own uncited sentence 'Every rule in this BRD is explicit' was removed.

I then ran the verifier again and applied all 7 wording findings:
- The FIT-Y-ROADMAP caveat (FQ-5) was added.
- The REQ-03 approvals are now shown as the SIMULATED gate decisions recorded in COMMUNICATION.md.
- BQ-9 'must stay distinct' became feat.fitment's recommendation.
- The category is attributed to the REQ-02 classification.
- The question-set intro no longer says every question was answered.
- S-1 now reads 'each paid invoice'.
- 'Primary' user became 'the users named in the ticket'.
- The four repositories now cite the feat.intake Source table.
- Tools used: Skill:requirement-steps, Read, Glob, Grep, mcp__hobasa-context__context_list, mcp__hobasa-context__context_get, mcp__hobasa-context__memory_search, Write, Edit, Agent:verifier
- Helper subagents: Agent
- Connector calls: none

## Attempts (checks before any person saw the output)

| Attempt | Session | Checks failed | Judge unsupported | Judge scores |
|---|---|---|---|---|
| 1 | new | 2 | 2 | {'correct': 5, 'complete': 4, 'grounded': 4, 'useful': 5} |
| 2 | resumed | 1 | 1 | {'correct': 5, 'complete': 5, 'grounded': 4, 'useful': 5} |
| 3 | resumed | 3 | 3 | {'correct': 4, 'complete': 5, 'grounded': 4, 'useful': 5} |
| 1 | resumed | 0 | 0 | {'correct': 5, 'complete': 4, 'grounded': 5, 'useful': 5} |

Details: `result_attempt<N>.json` (claims with sources), `checks_attempt<N>.json`, `judge_attempt<N>.json`.

## Human evaluation

| Role | By | Decision | Scores | Comment or reason |
|---|---|---|---|---|
| Leadership | sim.leadership | approve | — | automated checks and the independent judge passed |
