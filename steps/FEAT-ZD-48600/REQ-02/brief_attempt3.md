Your previous result for this step was refused. Fix every point, rewrite the output files in full, and return the structured result again.

## Refusal reasons
G1 judge found an unsupported statement: "ZD-48211 and ZD-48501 use the same "more than 30 days past due" rule in ap_aging as CR-5." (Neither feat.intake, feat.prebacklog nor the brief mentions ZD-48211 or ZD-48501. The IDs and the numbers in them (48211, 48501) come from a search outside the )
G1 judge found an unsupported statement: "ZD-48455 changes the portal aging table and uses the words "overdue risk"." (ZD-48455 does not appear in any input or in the brief. The ID and its number come from an out-of-context search of requirements/.)
G1 judge found an unsupported statement: "ZD-48470 changes the same vendor feed and its row rejection in ap_pipeline as CR-1. In what order should the two feed changes land?" (ZD-48470 does not appear in any input or in the brief. The source is out of context and the statement is uncited.)
G1 judge found an unsupported statement: "PROV-ACME-2026-11 says to keep the signature of `build_explanation_request`." (PROV-ACME-2026-11 and its 'keep signature' instruction are not in feat.intake, feat.prebacklog or the brief. This content comes from an out-of-context requireme)
G1 judge found an unsupported statement: "A feature-level override for FEAT-ZD-48600 lists ap_pipeline -> Data Engineering, ap_forecast -> Data Science, ap_aging -> Backend, ap_portal -> Frontend, and e" (This repeats the contents of features/FEAT-ZD-48600/org-overrides/org.routing_map.md. The previous refusal flagged that file under G2 as not in this step's cont)
G1 judge found an unsupported statement: "A search outside this step's contract found other open requirement items that touch the same functions or the same feed." (The output itself says this rests on a search outside the step's contract. No input supports it.)
G1 judge found an unsupported statement: "This agent has no write access to a ticketing system." (No input or brief states this. The brief lists only an approved GET-only api:github connector. 'No ticketing access' is an inference and is not cited.)

## Step brief (unchanged except the attempt number)
# Step REQ-02: Grouping (attempt 3) for FEAT-ZD-48600

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