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
| org.roadmap | hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-01/org.roadmap.md | hobasa-agentic-sdlc/org/org.roadmap.md | 9fbbfba | source |
| org.regulatory_sources | hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-01/org.regulatory_sources.md | hobasa-agentic-sdlc/org/org.regulatory_sources.md | 9fbbfba | source |
| org.connector_inventory | hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-01/org.connector_inventory.md | hobasa-agentic-sdlc/org/org.connector_inventory.md | 9fbbfba | source |
| org.model_dependency_map | hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-01/org.model_dependency_map.md | hobasa-agentic-sdlc/features/FEAT-ZD-48600/org-overrides/org.model_dependency_map.md | 9fbbfba | source |
| org.decision_log | hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-01/org.decision_log.md | hobasa-agentic-sdlc/org/org.decision_log.md | 9fbbfba | source |

Full brief per attempt: `brief_attempt<N>.md` (trigger event, owner answers, tool view, refusal reasons).

## Outputs (what the agent produced)

| Item | GitHub file |
|---|---|
| feat.intake | hobasa-requirement-agent/outputs/FEAT-ZD-48600/feat.intake.md |
| feat.prebacklog | hobasa-requirement-agent/outputs/FEAT-ZD-48600/feat.prebacklog.md |

## How the agent worked

- Approach: Attempt 3 fixes the one refusal reason. A-2 said amounts were formatted to two decimals "only when rendered". That contradicted the architecture override in requirements/ZD-48600.md, which says JSON between services carries amounts as strings with two decimals.

A-2 now follows the sources. Inside ap_aging the amount is the Invoice amount (Decimal, 2 dp). It travels to ap_portal as a two-decimal string in JSON, and ap_portal shows it to two decimals. It never passes through float. I aligned the D-2026-044 row's result with this wording.

Everything else is unchanged from attempt 2, which already fixed the earlier refusals (title, REQ-02/CMP-P01 references, statement about the agent's role, notification). That includes the pending capability_request for a notification channel. I rewrote both output files in full from the inputs already read this session: the five contracted inputs, requirements/ZD-48600.md, ZD-48211, ZD-48501 and ZD-48455.
- Tools used: Skill:requirement-steps, Read, Glob, Grep, Write, ToolSearch, mcp__hobasa-context__capabilities_list, mcp__hobasa-context__capability_request
- Helper subagents: none
- Connector calls: none

## Attempts (checks before any person saw the output)

| Attempt | Session | Checks failed | Judge unsupported | Judge scores |
|---|---|---|---|---|
| 1 | new | 5 | 5 | {'correct': 4, 'complete': 3, 'grounded': 4, 'useful': 4} |
| 2 | resumed | 1 | 1 | {'correct': 4, 'complete': 4, 'grounded': 4, 'useful': 4} |
| 3 | resumed | 0 | 0 | {'correct': 5, 'complete': 4, 'grounded': 5, 'useful': 5} |

Details: `result_attempt<N>.json` (claims with sources), `checks_attempt<N>.json`, `judge_attempt<N>.json`.

## Human evaluation

| Role | By | Decision | Scores | Comment or reason |
|---|---|---|---|---|
| PM | sim.pm | approve | — | automated checks and the independent judge passed |
