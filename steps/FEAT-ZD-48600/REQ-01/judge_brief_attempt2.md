# Evaluate step REQ-01: Requirement Intake for FEAT-ZD-48600

- Workbook action: Reads the new roadmap item and checks it against the Pre Backlog sheet and the DevOps board ⁸
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
- Workbook outcome: Entry created in the Pre Backlog requirement sheet, linked to the roadmap item and Notification sent
Agent has created an entry for review in the Pre Backlog requirement sheet / Sent a notification / --> Triggered another agent
Entry created in the Pre Backlog requirement sheet, linked to the roadmap item and Notification sent
Entry created in the Pre Backlog requirement sheet, linked to the roadmap item and Notification sent
Entry created in the Pre Backlog requirement sheet, linked to the roadmap item and Notification sent
Entry created in the Pre Backlog requirement sheet, linked to the roadmap item and Notification sent
Entry created in the Pre Backlog requirement sheet, linked to the roadmap item and Notification sent
Entry created in the Pre Backlog requirement sheet, linked to the roadmap item and Notification sent
Entry created in the Pre Backlog requirement sheet, linked to the roadmap item and Notification sent
Entry created in the Pre Backlog requirement sheet, linked to the roadmap item and Notification sent

## Outputs to evaluate
- `hobasa-requirement-agent/outputs/FEAT-ZD-48600/feat.intake.md`
- `hobasa-requirement-agent/outputs/FEAT-ZD-48600/feat.prebacklog.md`

## Inputs the agent was given
- org.roadmap: `hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-01/org.roadmap.md`
- org.regulatory_sources: `hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-01/org.regulatory_sources.md`
- org.connector_inventory: `hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-01/org.connector_inventory.md`
- org.model_dependency_map: `hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-01/org.model_dependency_map.md`
- org.decision_log: `hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-01/org.decision_log.md`

## Trigger event
{"intake": {"channel": "Customer Feedback", "source": "Zendesk ticket ZD-48600 (sample, synthetic)", "received": "2026-10-24", "text": "AP managers want to see which overdue invoices belong to vendors that usually pay late, so they can chase them first. (1) Data engineering, ap_pipeline: the vendor feed gains an optional paid_date column (ISO date, empty when unpaid); an invalid paid_date rejects the row with reason 'paid_date'; add delays_by_vendor(records) returning {vendor: [delay_days, ...]} for paid records with a paid_date, where delay_days = (paid_date - due_date) in days, in feed order. (2) AI / data science, ap_forecast: add vendor_risk(history) returning 'high' when predict_delay_days(history) > 30, 'medium' when it is > 10, otherwise 'low'; build_explanation_request gains an optional risk argument and, when given, the prompt ends with ' Risk level: <risk>.'. (3) Backend, ap_aging: add overdue_with_risk(invoices, as_of, risk_by_vendor) returning, for unpaid invoices more than 30 days past due, a list of {'id', 'vendor', 'days', 'amount', 'risk'} sorted by days descending then id, with risk 'unknown' for vendors not in risk_by_vendor. (4) Frontend, ap_portal: add renderOverdueRisk(rows) rendering '<table class=\"overdue-risk\">' with one '<tr class=\"risk-RISK\">' per row showing id, vendor, days and amount to two decimals, and an empty string when there are no rows. The whole flow must be proven end to end: feed -> delays -> risk -> overdue list -> portal table.", "github": "hobasa-agentic-sdlc/requirements/ZD-48600.md"}}

Shared memory and conventions: `memory/MEMORY.md` and `CLAUDE.md` in the SDLC repository.

## The step brief the agent was given (a valid source, cited as record:brief)

Your previous result for this step was refused. Fix every point, rewrite the output files in full, and return the structured result again.

## Refusal reasons
G1 judge found an unsupported statement: "Entry status | NEW in pre-backlog. Classification, duplicate merge and fitment are left to REQ-02 and REQ-03. | record:brief" (The brief does not name REQ-02 or REQ-03 and does not say which later steps handle classification, duplicate merge or fitment. The cited source does not contain)
G1 judge found an unsupported statement: "Status: **Draft, waiting for PM review** (gate: PM)." (None of the inputs or the brief names a PM gate for REQ-01. The brief says only that 'the spine commits and pushes after evaluation and approval'.)
G1 judge found an unsupported statement: "No regulatory impact analysis (CMP-P01) is triggered." (No input or the brief mentions CMP-P01. The step ID is invented.)
G1 judge found an unsupported statement: "This entry is recorded as NEW. The duplicate merge belongs to REQ-02 (Grouping) (record:brief)." (The brief does not mention REQ-02 or 'Grouping'. The citation to record:brief is wrong.)
G1 judge found an unsupported statement: "When this entry passes the PM gate, the spine notifies the PM and starts REQ-02 (Grouping) (record:brief)." (The brief says nothing about the spine notifying the PM or starting REQ-02 (Grouping). The workbook outcome says only 'Notification sent / Triggered another age)

## Step brief (unchanged except the attempt number)
# Step REQ-01: Requirement Intake (attempt 2) for FEAT-ZD-48600

- Workbook trigger: Whenever new item gets added
Email/Ticket
All Internal Review Meeting Transcript
Transcript would be fed to agent automatically post the meeting
When there are dynamics in the market research and Competitive analysis
Decision recorded after a leadership meeting
Vendor changelog entry or connector failure
Update on a named regulatory source
Provider release note or deprecation notice, Provider email notification
Item added to the backlog, related work enters planning from the retro meeting
- Workbook action: Reads the new roadmap item and checks it against the Pre Backlog sheet and the DevOps board ⁸
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
- Workbook outcome: Entry created in the Pre Backlog requirement sheet, linked to the roadmap item and Notification sent
Agent has created an entry for review in the Pre Backlog requirement sheet / Sent a notification / --> Triggered another agent
Entry created in the Pre Backlog requirement sheet, linked to the roadmap item and Notification sent
Entry created in the Pre Backlog requirement sheet, linked to the roadmap item and Notification sent
Entry created in the Pre Backlog requirement sheet, linked to the roadmap item and Notification sent
Entry created in the Pre Backlog requirement sheet, linked to the roadmap item and Notification sent
Entry created in the Pre Backlog requirement sheet, linked to the roadmap item and Notification sent
Entry created in the Pre Backlog requirement sheet, linked to the roadmap item and Notification sent
Entry created in the Pre Backlog requirement sheet, linked to the roadmap item and Notification sent
Entry created in the Pre Backlog requirement sheet, linked to the roadmap item and Notification sent

## Inputs (GitHub checkout; read them with Read, or context_get for a receipt)
- org.roadmap (Structured roadmap items): `hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-01/org.roadmap.md` (from hobasa-agentic-sdlc/org/org.roadmap.md at commit 5988080)
- org.regulatory_sources (Named regulatory sources with section and page): `hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-01/org.regulatory_sources.md` (from hobasa-agentic-sdlc/org/org.regulatory_sources.md at commit 5988080)
- org.connector_inventory (Source-system connectors and versions): `hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-01/org.connector_inventory.md` (from hobasa-agentic-sdlc/org/org.connector_inventory.md at commit 5988080)
- org.model_dependency_map (LLM providers and models per feature): `hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-01/org.model_dependency_map.md` (from hobasa-agentic-sdlc/features/FEAT-ZD-48600/org-overrides/org.model_dependency_map.md at commit 5988080)
- org.decision_log (Prior leadership and product decisions): `hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-01/org.decision_log.md` (from hobasa-agentic-sdlc/org/org.decision_log.md at commit 5988080)

## Outputs (write each file in full; the spine commits and pushes after evaluation and approval)
- feat.intake (Original intake item with source link): write `hobasa-requirement-agent/outputs/FEAT-ZD-48600/feat.intake.md`
- feat.prebacklog (Pre-backlog entry linked to roadmap and trace ID): write `hobasa-requirement-agent/outputs/FEAT-ZD-48600/feat.prebacklog.md`


## How to work
Decide the best way to do this step from the inputs and the workbook action, plan it (TodoWrite for multi-part work), then do it. Helper subagents you can delegate to: explorer, verifier (use the verifier before you finish when the output makes many factual statements). Use the shared memory (memory_search) for decisions and lessons. Connectors approved for you: api:github (GitHub REST API for the Hobasa repositories: issues, pull requests, checks (GET /repos/<owner>/<repo>/...)). Use one only when your inputs do not hold what you need; request a missing one with capability_request.

## Trigger event (cite as record:intake)
{
  "intake": {
    "channel": "Customer Feedback",
    "source": "Zendesk ticket ZD-48600 (sample, synthetic)",
    "received": "2026-10-24",
    "text": "AP managers want to see which overdue invoices belong to vendors that usually pay late, so they can chase them first. (1) Data engineering, ap_pipeline: the vendor feed gains an optional paid_date column (ISO date, empty when unpaid); an invalid paid_date rejects the row with reason 'paid_date'; add delays_by_vendor(records) returning {vendor: [delay_days, ...]} for paid records with a paid_date, where delay_days = (paid_date - due_date) in days, in feed order. (2) AI / data science, ap_forecast: add vendor_risk(history) returning 'high' when predict_delay_days(history) > 30, 'medium' when it is > 10, otherwise 'low'; build_explanation_request gains an optional risk argument and, when given, the prompt ends with ' Risk level: <risk>.'. (3) Backend, ap_aging: add overdue_with_risk(invoices, as_of, risk_by_vendor) returning, for unpaid invoices more than 30 days past due, a list of {'id', 'vendor', 'days', 'amount', 'risk'} sorted by days descending then id, with risk 'unknown' for vendors not in risk_by_vendor. (4) Frontend, ap_portal: add renderOverdueRisk(rows) rendering '<table class=\"overdue-risk\">' with one '<tr class=\"risk-RISK\">' per row showing id, vendor, days and amount to two decimals, and an empty string when there are no rows. The whole flow must be proven end to end: feed -> delays -> risk -> overdue list -> portal table.",
    "github": "hobasa-agentic-sdlc/requirements/ZD-48600.md"
  }
}

Finish with the structured result: approach, tools_used, claims (each citing an input item name, a tool view, api:<name>, mcp:<server>, record:intake, record:owner_answer, record:memory or record:brief for this brief; a claim drawing on several sources lists them separated by ';'; every number must appear in what you cite), open questions (BLOCKING: only when you cannot finish), summary.