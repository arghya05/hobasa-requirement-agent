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
| feat.prebacklog | hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-02/feat.prebacklog.md | hobasa-requirement-agent/outputs/FEAT-ZD-48600/feat.prebacklog.md | 9919dd4 | REQ-01 |
| feat.intake | hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-02/feat.intake.md | hobasa-requirement-agent/outputs/FEAT-ZD-48600/feat.intake.md | 9919dd4 | REQ-01 |
| org.routing_map | hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-02/org.routing_map.md | hobasa-agentic-sdlc/features/FEAT-ZD-48600/org-overrides/org.routing_map.md | 9fbbfba | source |
| org.architecture | hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-02/org.architecture.md | hobasa-agentic-sdlc/features/FEAT-ZD-48600/org-overrides/org.architecture.md | 9fbbfba | source |

Full brief per attempt: `brief_attempt<N>.md` (trigger event, owner answers, tool view, refusal reasons).

## Outputs (what the agent produced)

| Item | GitHub file |
|---|---|
| feat.classification | hobasa-requirement-agent/outputs/FEAT-ZD-48600/feat.classification.md |

## How the agent worked

- Approach: This attempt fixes the G1 refusal. FIN-OPS-2026-07 had been listed among the related items said to share a rule or code with ZD-48600. It is a configuration-only change to max_tokens and shares neither, so I removed it from the grouped list and marked it "Not grouped" in the duplicate table. Its max_tokens conflict with PROV-ACME-2026-11 is kept only as a side observation for the PM (new OQ-5), split out of OQ-3. The grouped list now names four items, each with its link stated: ZD-48501 and ZD-48211 (shared overdue rule), and ZD-48470 and PROV-ACME-2026-11 (shared code). The fixes from earlier attempts are kept: the CR-4 provider/model statement is scoped to this ticket, there is no status or oracle-field statement, and every cited file was opened with Read. The classification is unchanged: New Feature, Not Technical Only, a Technical sub-category for each CR, no duplicates merged, and the impacted repositories taken from the routing maps. I rewrote the file in full.
- Tools used: Skill:requirement-steps, Read, Glob, Grep, Write, Edit, Agent:verifier
- Helper subagents: Agent
- Connector calls: none

## Attempts (checks before any person saw the output)

| Attempt | Session | Checks failed | Judge unsupported | Judge scores |
|---|---|---|---|---|
| 1 | new | 4 | — | — |
| 2 | resumed | 1 | 1 | {'correct': 5, 'complete': 5, 'grounded': 5, 'useful': 5} |
| 3 | resumed | 2 | 2 | {'correct': 5, 'complete': 5, 'grounded': 4, 'useful': 5} |
| 1 | resumed | 1 | 1 | {'correct': 5, 'complete': 5, 'grounded': 4, 'useful': 5} |
| 2 | resumed | 0 | 0 | {'correct': 5, 'complete': 5, 'grounded': 5, 'useful': 5} |

Details: `result_attempt<N>.json` (claims with sources), `checks_attempt<N>.json`, `judge_attempt<N>.json`.

## Human evaluation

| Role | By | Decision | Scores | Comment or reason |
|---|---|---|---|---|
| PM | sim.pm | approve | — | automated checks and the independent judge passed |
