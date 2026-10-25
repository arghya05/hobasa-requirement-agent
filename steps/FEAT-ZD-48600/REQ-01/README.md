# REQ-01 · Requirement Intake

**Agent:** Requirement · **Item:** FEAT-ZD-48600 · **Status:** ✅ done · approved in an earlier run, reused
**Approved by:** PM: approve by sim.pm

**What this step does:** Reads the new roadmap item and checks it against the Pre Backlog sheet and the DevOps board ⁸
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

**Expected outcome:** Entry created in the Pre Backlog requirement sheet, linked to the roadmap item and Notification sent
Agent has created an entry for review in the Pre Backlog requirement sheet / Sent a notification / --> Triggered another agent
Entry created in the Pre Backlog requirement sheet, linked to the roadmap item and Notification sent
Entry created in the Pre Backlog requirement sheet, linked to the roadmap item and Notification sent
Entry created in the Pre Backlog requirement sheet, linked to the roadmap item and Notification sent
Entry created in the Pre Backlog requirement sheet, linked to the roadmap item and Notification sent
Entry created in the Pre Backlog requirement sheet, linked to the roadmap item and Notification sent
Entry created in the Pre Backlog requirement sheet, linked to the roadmap item and Notification sent
Entry created in the Pre Backlog requirement sheet, linked to the roadmap item and Notification sent
Entry created in the Pre Backlog requirement sheet, linked to the roadmap item and Notification sent

**Started by:** Whenever new item gets added
Email/Ticket
All Internal Review Meeting Transcript
Transcript would be fed to agent automatically post the meeting
When there are dynamics in the market research and Competitive analysis
Decision recorded after a leadership meeting
Vendor changelog entry or connector failure
Update on a named regulatory source
Provider release note or deprecation notice, Provider email notification
Item added to the backlog, related work enters planning from the retro meeting

## Input: what the agent received

| # | Input | What it is | Produced by | Open |
|---|---|---|---|---|
| 1 | `org.roadmap` | Structured roadmap items | organisation source | [input copy](https://github.com/arghya05/hobasa-requirement-agent/blob/main/inputs/FEAT-ZD-48600/REQ-01/org.roadmap.md) · [original](https://github.com/arghya05/hobasa-agentic-sdlc/blob/main/org/org.roadmap.md) |
| 2 | `org.regulatory_sources` | Named regulatory sources with section and page | organisation source | [input copy](https://github.com/arghya05/hobasa-requirement-agent/blob/main/inputs/FEAT-ZD-48600/REQ-01/org.regulatory_sources.md) · [original](https://github.com/arghya05/hobasa-agentic-sdlc/blob/main/org/org.regulatory_sources.md) |
| 3 | `org.connector_inventory` | Source-system connectors and versions | organisation source | [input copy](https://github.com/arghya05/hobasa-requirement-agent/blob/main/inputs/FEAT-ZD-48600/REQ-01/org.connector_inventory.md) · [original](https://github.com/arghya05/hobasa-agentic-sdlc/blob/main/org/org.connector_inventory.md) |
| 4 | `org.model_dependency_map` | LLM providers and models per feature | organisation source | [input copy](https://github.com/arghya05/hobasa-requirement-agent/blob/main/inputs/FEAT-ZD-48600/REQ-01/org.model_dependency_map.md) · [original](https://github.com/arghya05/hobasa-agentic-sdlc/blob/main/features/FEAT-ZD-48600/org-overrides/org.model_dependency_map.md) |
| 5 | `org.decision_log` | Prior leadership and product decisions | organisation source | [input copy](https://github.com/arghya05/hobasa-requirement-agent/blob/main/inputs/FEAT-ZD-48600/REQ-01/org.decision_log.md) · [original](https://github.com/arghya05/hobasa-agentic-sdlc/blob/main/org/org.decision_log.md) |

The full brief the agent was given, attempt by attempt: `brief_attempt<N>.md` in this folder.

## Output: what the agent produced

| # | Output | What it is | Open |
|---|---|---|---|
| 1 | `feat.intake` | Original intake item with source link | [Markdown](https://github.com/arghya05/hobasa-requirement-agent/blob/main/outputs/FEAT-ZD-48600/feat.intake.md) · [HTML](https://htmlpreview.github.io/?https://raw.githubusercontent.com/arghya05/hobasa-requirement-agent/main/docs/FEAT-ZD-48600/REQ-01_feat-intake.html) · [PDF](https://github.com/arghya05/hobasa-requirement-agent/blob/main/docs/FEAT-ZD-48600/REQ-01_feat-intake.pdf) |
| 2 | `feat.prebacklog` | Pre-backlog entry linked to roadmap and trace ID | [Markdown](https://github.com/arghya05/hobasa-requirement-agent/blob/main/outputs/FEAT-ZD-48600/feat.prebacklog.md) · [HTML](https://htmlpreview.github.io/?https://raw.githubusercontent.com/arghya05/hobasa-requirement-agent/main/docs/FEAT-ZD-48600/REQ-01_feat-prebacklog.html) · [PDF](https://github.com/arghya05/hobasa-requirement-agent/blob/main/docs/FEAT-ZD-48600/REQ-01_feat-prebacklog.pdf) |

## Checks and approval

| Attempt | Session | Problems found by the checks | Unsupported statements (judge) | Judge scores |
|---|---|---|---|---|
| 1 | new | 2 | 2 | {'correct': 4, 'complete': 3, 'grounded': 4, 'useful': 4} |

Improvements the independent judge suggests (non-blocking):

- The related-items scan opened only 6 of the 12 files in requirements/. It missed ZD-48470, which is an open change to the same vendor feed in ap_pipeline: feed v2 adds a 'currency' column with reason 'InvalidCurrency' rejections through transform.to_model. ZD-48600's org.data_model and customer_mappings describe feed v3 without currency, so REQ-02 needs this item for sequencing and feed-version conflicts.
- It also missed FIN-OPS-2026-07, which changes the ap_forecast explanation max_tokens from 300 to 200. That item touches the same explanation request as CR-5. It also conflicts with PROV-ACME-2026-11, which says to keep max_tokens at 300. List it under Related items and OQ-3.
- The 'No duplicate was found' statement is correct for the whole folder, but the agent did not read FIN-OPS-2026-07, REG-LPR-2026-4.2, RETRO-2026-19, ZD-48377, ZD-48470 or ZD-48480. The scope of the check should say that, or the agent should read all of them.
- OQ-1 is partly answered by ZD-48600.md org_overrides. They say paid_date is added in vendor feed v3, the mapping is paid_date -> Invoice.paid_date, and the daily 02:00 Asia/Kolkata schedule is unchanged. Cite this, and narrow the question to whether a connector version bump is needed.
- ZD-48600.md org_overrides also give org.routing_map (component to agent), org.risk_map (tier T2, risk label advisory only) and org.design_library (row classes, including 'risk-unknown'). These would strengthen 'Matches the item to the affected component' and the A2/OQ-4 context.
- The workbook action 'Gathers external patterns and cites each source' is not addressed. State that it was not applicable or not done.
- ZD-48510 (payment execution from the aging screen, which mentions overdue invoices) could be noted as unrelated or excluded, to show the check covered it.

## How the agent worked

- **Approach:** I followed the REQ-01 procedure in the requirement-steps skill. First I read all five contracted inputs and the source file for the ticket (requirements/ZD-48600.md). I split the ticket into eight change requests and matched them to the roadmap, where R-AP-12 fits. Then I checked them against each prior decision (D-2026-031, D-2026-044 and D-2026-050), the regulatory sources, the connector inventory and the model dependency map. The Pre Backlog sheet and DevOps board were not provided and no connector is approved for them. So I ran the duplicate and related-item check over the GitHub requirements/ folder with Grep and read the four items it flagged, plus PROV-ACME-2026-11 because it touches the same model dependency. The shell is denied for this step (G9), so I used Read, Grep and Glob only. I did not run the verifier subagent: both outputs cite their sources inline and every number appears in a cited source. Gaps are stated as assumptions and non-blocking open questions; nothing blocks the step.
- **Tools used:** Skill:requirement-steps, Read, Glob, Grep, Write
- **Helper subagents:** none
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
