# Step REQ-02: Grouping (attempt 1) for FEAT-ZD-48600

- Workbook trigger: Previous Requirement Intake
Technical has to be a sub-category under each and should be classified as Technical Only
This could go as a qualifier during requirement approval or as applicable ²
- Workbook action: New Ticket gets created
- Workbook outcome: Entry classified by category, duplicates merged

## Inputs (GitHub checkout; read them with Read, or context_get for a receipt)
- feat.prebacklog (Pre-backlog entry linked to roadmap and trace ID): `hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-02/feat.prebacklog.md` (from hobasa-requirement-agent/outputs/FEAT-ZD-48600/feat.prebacklog.md at commit ee6f26c)
- feat.intake (Original intake item with source link): `hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-02/feat.intake.md` (from hobasa-requirement-agent/outputs/FEAT-ZD-48600/feat.intake.md at commit ee6f26c)

## Outputs (write each file in full; the spine commits and pushes after evaluation and approval)
- feat.classification (Category, qualifier and merged duplicates): write `hobasa-requirement-agent/outputs/FEAT-ZD-48600/feat.classification.md`

## Impacted repositories
Decide which repositories this item must change, from the requirement and the routing map (`hobasa-agentic-sdlc/org/org.routing_map.md`; read it). Bound repositories: ap_aging (Python 3.9 (standard library); BE); ap_forecast (Python 3.9 (standard library); DS); ap_pipeline (Python 3.9 (standard library); DE); ap_portal (Node.js 22 (CommonJS, node:test); FE). Add one line to your output exactly as `Impacted repositories: <comma-separated names>` (only those whose behaviour changes; documentation-only or configuration-only items name the repository whose docs or configuration change). Cite the routing map.

## How to work
Decide the best way to do this step from the inputs and the workbook action, plan it (TodoWrite for multi-part work), then do it. Helper subagents you can delegate to: explorer, verifier (use the verifier before you finish when the output makes many factual statements). Use the shared memory (memory_search) for decisions and lessons. Connectors approved for you: api:github (GitHub REST API for the Hobasa repositories: issues, pull requests, checks (GET /repos/<owner>/<repo>/...)). Use one only when your inputs do not hold what you need; request a missing one with capability_request.

Finish with the structured result: approach, tools_used, claims (each citing an input item name, a tool view, api:<name>, mcp:<server>, record:intake, record:owner_answer, record:memory or record:brief for this brief; a claim drawing on several sources lists them separated by ';'; every number must appear in what you cite), open questions (BLOCKING: only when you cannot finish), summary.