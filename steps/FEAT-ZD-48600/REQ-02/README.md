# REQ-02 Grouping (Requirement agent)

**Item:** FEAT-ZD-48600 · **status:** done
**Trigger:** Previous Requirement Intake
Technical has to be a sub-category under each and should be classified as Technical Only
This could go as a qualifier during requirement approval or as applicable ²  
**Action:** New Ticket gets created  
**Outcome expected:** Entry classified by category, duplicates merged

## Inputs (what the agent was given)

| Item | Prepared input (this repository) | Read from (producer in GitHub) | Commit | Produced by |
|---|---|---|---|---|
| feat.prebacklog | hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-02/feat.prebacklog.md | hobasa-requirement-agent/outputs/FEAT-ZD-48600/feat.prebacklog.md | fd588b3 | REQ-01 |
| feat.intake | hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-02/feat.intake.md | hobasa-requirement-agent/outputs/FEAT-ZD-48600/feat.intake.md | fd588b3 | REQ-01 |
| org.routing_map | hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-02/org.routing_map.md | hobasa-agentic-sdlc/features/FEAT-ZD-48600/org-overrides/org.routing_map.md | bf63f34 | source |
| org.architecture | hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-02/org.architecture.md | hobasa-agentic-sdlc/features/FEAT-ZD-48600/org-overrides/org.architecture.md | bf63f34 | source |

Full brief per attempt: `brief_attempt<N>.md` (trigger event, owner answers, tool view, refusal reasons).

## Outputs (what the agent produced)

| Item | GitHub file |
|---|---|
| feat.classification | hobasa-requirement-agent/outputs/FEAT-ZD-48600/feat.classification.md |

## How the agent worked

- Approach: Attempt 2 fixes both G1 refusals, and I rewrote feat.classification in full. (1) In the ZD-48470 overlap row I removed the inferred claim that both changes use the same transform.to_model reject path. The row now states only what the files say: both change the ap_pipeline vendor feed and both add a row rejection ('InvalidCurrency' in feed v2, 'paid_date' in feed v3). (2) I removed the sentence "Only CR-6 is customer-visible on its own" and the per-CR "customer-visible" column. The qualifier now rests only on sourced facts: the business need for AP managers, CR-6's new portal table, and how RETRO-2026-19 uses "Technical only". Whether other CRs, for example the CR-4 explanation prompt, are visible to users is now open question OQ-E. While re-checking the file I also tightened the FIN-OPS row ("the ticket does not mention max_tokens"). Everything else is unchanged from the inputs and requirement files read in attempt 1: same category, routing, impacted repositories and duplicate decisions. Shell use is blocked for this step (G9), so I read files with Read.
- Tools used: Skill:requirement-steps, Read, Glob, Grep, Write, Edit
- Helper subagents: none
- Connector calls: none

## Attempts (checks before any person saw the output)

| Attempt | Session | Checks failed | Judge unsupported | Judge scores |
|---|---|---|---|---|
| 1 | new | 2 | 2 | {'correct': 5, 'complete': 5, 'grounded': 4, 'useful': 5} |
| 2 | resumed | 0 | 0 | {'correct': 5, 'complete': 4, 'grounded': 5, 'useful': 4} |

Details: `result_attempt<N>.json` (claims with sources), `checks_attempt<N>.json`, `judge_attempt<N>.json`.

## Human evaluation

| Role | By | Decision | Scores | Comment or reason |
|---|---|---|---|---|
| PM | sim.pm | approve | — | automated checks and the independent judge passed |
