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
| org.roadmap | hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-01/org.roadmap.md | hobasa-agentic-sdlc/org/org.roadmap.md | bf63f34 | source |
| org.regulatory_sources | hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-01/org.regulatory_sources.md | hobasa-agentic-sdlc/org/org.regulatory_sources.md | bf63f34 | source |
| org.connector_inventory | hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-01/org.connector_inventory.md | hobasa-agentic-sdlc/org/org.connector_inventory.md | bf63f34 | source |
| org.model_dependency_map | hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-01/org.model_dependency_map.md | hobasa-agentic-sdlc/features/FEAT-ZD-48600/org-overrides/org.model_dependency_map.md | bf63f34 | source |
| org.decision_log | hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-01/org.decision_log.md | hobasa-agentic-sdlc/org/org.decision_log.md | bf63f34 | source |

Full brief per attempt: `brief_attempt<N>.md` (trigger event, owner answers, tool view, refusal reasons).

## Outputs (what the agent produced)

| Item | GitHub file |
|---|---|
| feat.intake | hobasa-requirement-agent/outputs/FEAT-ZD-48600/feat.intake.md |
| feat.prebacklog | hobasa-requirement-agent/outputs/FEAT-ZD-48600/feat.prebacklog.md |

## How the agent worked

- Approach: Attempt 3 fixes the G1 refusal on the connector check. I removed the blanket sentence "No source-system connector is affected". The connector row in feat.prebacklog now matches what org.connector_inventory says: no connector is affected by the ap_aging library, and the inventory says nothing about ap_pipeline, ap_forecast or ap_portal. That gap is now open question OQ-3, which asks whether the CR-1 vendor-feed change or the other repositories affect a connector. While re-checking for similar overreach, I also changed "The ticket asks for no change of provider or model" to "The ticket does not mention any change of provider or model". Both files are rewritten in full; feat.intake has no content change. Everything else carries over from attempt 2. The ticket is split into CR-0 to CR-7 and linked to R-AP-12. The entry is checked against D-2026-031, D-2026-044, D-2026-050, L-007 and L-011, the regulatory sources and the model dependency map. ZD-48211, ZD-48501 and ZD-48455 were read in this session and are listed as related, not duplicates. The Pre Backlog sheet and DevOps board were not available, so their absence is disclosed as OQ-1. Shell use is denied in this step, so I used only Read, Glob, Grep and Write.
- Tools used: Skill:requirement-steps, Read, Glob, Grep, Write
- Helper subagents: none
- Connector calls: none

## Attempts (checks before any person saw the output)

| Attempt | Session | Checks failed | Judge unsupported | Judge scores |
|---|---|---|---|---|
| 1 | new | 3 | — | — |
| 2 | resumed | 1 | 1 | {'correct': 5, 'complete': 4, 'grounded': 4, 'useful': 5} |
| 3 | resumed | 0 | 0 | {'correct': 5, 'complete': 4, 'grounded': 5, 'useful': 5} |

Details: `result_attempt<N>.json` (claims with sources), `checks_attempt<N>.json`, `judge_attempt<N>.json`.

## Human evaluation

| Role | By | Decision | Scores | Comment or reason |
|---|---|---|---|---|
| PM | sim.pm | approve | — | automated checks and the independent judge passed |
