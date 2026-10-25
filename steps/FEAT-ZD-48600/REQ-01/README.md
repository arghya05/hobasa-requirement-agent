# REQ-01 Requirement Intake (Requirement agent)

**Item:** FEAT-ZD-48600 · **status:** done
**Trigger:** Whenever new item gets added
Email/Ticket
All Internal Review Meeting Transcript
Transcript would be fed to agent automatically post the meeting
When there are dynamics in the market research and Competitive analysis
Decision recorded after a leadership meeting
Vendor changelog entry or connector failure
Update on a named regulatory source
Provider release note or deprecation notice, Provider email notification
Item added to the backlog, related work enters planning from the retro meeting  
**Action:** Reads the new roadmap item and checks it against the Pre Backlog sheet and the DevOps board ⁸
Reads the ticket
Reads the transcript and extracts the change requests raised
4 gateways to requirement in-take for internal meetings and leadership discussions

1. Define meeting cadence and give the meeting names to the agent

2. Add the agent to any out of sequence meetings before meeting happens, add qualifier only PM can do this

3. Meeting transcript to be given to the agent if out of sequence meeting was missed to invite agent

4.PM will have the permission to add requirement to backlog manually ⁴
Gathers external patterns and cites each source
Reads the decision and checks for conflict with a prior decision
Matches the change against the connector inventory and assesses which features are affected
Captures the change with its section and page and assesses which rules are affected or they are new rules
Matches the change against the model dependency map and assesses affected features
Matches the item to the affected component and to planned work  
**Outcome expected:** Entry created in the Pre Backlog requirement sheet, linked to the roadmap item and Notification sent
Agent has created an entry for review in the Pre Backlog requirement sheet / Sent a notification / --> Triggered another agent
Entry created in the Pre Backlog requirement sheet, linked to the roadmap item and Notification sent
Entry created in the Pre Backlog requirement sheet, linked to the roadmap item and Notification sent
Entry created in the Pre Backlog requirement sheet, linked to the roadmap item and Notification sent
Entry created in the Pre Backlog requirement sheet, linked to the roadmap item and Notification sent
Entry created in the Pre Backlog requirement sheet, linked to the roadmap item and Notification sent
Entry created in the Pre Backlog requirement sheet, linked to the roadmap item and Notification sent
Entry created in the Pre Backlog requirement sheet, linked to the roadmap item and Notification sent
Entry created in the Pre Backlog requirement sheet, linked to the roadmap item and Notification sent

## Inputs (what the agent was given)

| Item | Prepared input (this repository) | Read from (producer in GitHub) | Commit | Produced by |
|---|---|---|---|---|
| org.roadmap | hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-01/org.roadmap.md | hobasa-agentic-sdlc/org/org.roadmap.md | 5988080 | source |
| org.regulatory_sources | hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-01/org.regulatory_sources.md | hobasa-agentic-sdlc/org/org.regulatory_sources.md | 5988080 | source |
| org.connector_inventory | hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-01/org.connector_inventory.md | hobasa-agentic-sdlc/org/org.connector_inventory.md | 5988080 | source |
| org.model_dependency_map | hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-01/org.model_dependency_map.md | hobasa-agentic-sdlc/features/FEAT-ZD-48600/org-overrides/org.model_dependency_map.md | 5988080 | source |
| org.decision_log | hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-01/org.decision_log.md | hobasa-agentic-sdlc/org/org.decision_log.md | 5988080 | source |

Full brief per attempt: `brief_attempt<N>.md` (trigger event, owner answers, tool view, refusal reasons).

## Outputs (what the agent produced)

| Item | GitHub file |
|---|---|
| feat.intake | hobasa-requirement-agent/outputs/FEAT-ZD-48600/feat.intake.md |
| feat.prebacklog | hobasa-requirement-agent/outputs/FEAT-ZD-48600/feat.prebacklog.md |

## How the agent worked

- Approach: Attempt 3 rewrites both files in full and fixes the one remaining G1 refusal. D-2026-031 is now applied only to overdue_with_risk in ap_aging, which is the aging case, and that link is stated as assumption A-1. The output now says the decision covers aging buckets only and does not settle the day unit for delay_days in ap_pipeline. That question is raised as new open question OQ-6. The attempt-2 fixes are kept: no later-step names, no PM-gate claim and no notification claim. Everything else is unchanged. I read the ticket from the trigger record and the five contracted inputs, and used the shared memory (D-2026-031/044/050, L-007, L-011). The work extracts the change requests, links the item to roadmap R-AP-12, and checks it against decisions, connectors, regulatory sources and model dependencies. The Pre Backlog sheet and DevOps board were not in context, so they are listed as an open question rather than guessed.
- Tools used: Skill:requirement-steps, Read, Glob, mcp__hobasa-context__context_list, mcp__hobasa-context__memory_search, Write, Edit
- Helper subagents: none
- Connector calls: none

## Attempts (checks before any person saw the output)

| Attempt | Session | Checks failed | Judge unsupported | Judge scores |
|---|---|---|---|---|
| 1 | new | 5 | 5 | {'correct': 4, 'complete': 4, 'grounded': 4, 'useful': 4} |
| 2 | resumed | 1 | 1 | {'correct': 5, 'complete': 4, 'grounded': 5, 'useful': 5} |
| 3 | resumed | 0 | 0 | {'correct': 5, 'complete': 4, 'grounded': 5, 'useful': 5} |

Details: `result_attempt<N>.json` (claims with sources), `checks_attempt<N>.json`, `judge_attempt<N>.json`.

## Human evaluation

| Role | By | Decision | Scores | Comment or reason |
|---|---|---|---|---|
| PM | sim.pm | approve | — | automated checks and the independent judge passed |
