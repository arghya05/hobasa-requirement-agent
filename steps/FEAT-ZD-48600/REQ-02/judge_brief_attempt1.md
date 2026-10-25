# Evaluate step REQ-02: Grouping for FEAT-ZD-48600

- Workbook action: New Ticket gets created
- Workbook outcome: Entry classified by category, duplicates merged

## Outputs to evaluate
- `final_document/e2e-run/runs/run-20261025-111239-feat-zd-48600/workspace/agents/hobasa-requirement-agent/outputs/FEAT-ZD-48600/feat.classification.md`

## Inputs the agent was given
- feat.prebacklog: `final_document/e2e-run/runs/run-20261025-111239-feat-zd-48600/workspace/agents/hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-02/feat.prebacklog.md`
- feat.intake: `final_document/e2e-run/runs/run-20261025-111239-feat-zd-48600/workspace/agents/hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-02/feat.intake.md`
- org.routing_map: `final_document/e2e-run/runs/run-20261025-111239-feat-zd-48600/workspace/agents/hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-02/org.routing_map.md`
- org.architecture: `final_document/e2e-run/runs/run-20261025-111239-feat-zd-48600/workspace/agents/hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-02/org.architecture.md`

## Other GitHub files the agent read (valid sources when cited as file:<repository>/<path>)
- `final_document/e2e-run/runs/run-20261025-111239-feat-zd-48600/workspace/agents/hobasa-requirement-agent/outputs/FEAT-ZD-48600/feat.classification.md`
- `final_document/e2e-run/runs/run-20261025-111239-feat-zd-48600/workspace/hobasa-agentic-sdlc/org/org.routing_map.md`
- `final_document/e2e-run/runs/run-20261025-111239-feat-zd-48600/workspace/hobasa-agentic-sdlc/requirements/FIN-OPS-2026-07.md`
- `final_document/e2e-run/runs/run-20261025-111239-feat-zd-48600/workspace/hobasa-agentic-sdlc/requirements/PROV-ACME-2026-11.md`
- `final_document/e2e-run/runs/run-20261025-111239-feat-zd-48600/workspace/hobasa-agentic-sdlc/requirements/REG-LPR-2026-4.2.md`
- `final_document/e2e-run/runs/run-20261025-111239-feat-zd-48600/workspace/hobasa-agentic-sdlc/requirements/RETRO-2026-19.md`
- `final_document/e2e-run/runs/run-20261025-111239-feat-zd-48600/workspace/hobasa-agentic-sdlc/requirements/ZD-48211.md`
- `final_document/e2e-run/runs/run-20261025-111239-feat-zd-48600/workspace/hobasa-agentic-sdlc/requirements/ZD-48377.md`
- `final_document/e2e-run/runs/run-20261025-111239-feat-zd-48600/workspace/hobasa-agentic-sdlc/requirements/ZD-48455.md`
- `final_document/e2e-run/runs/run-20261025-111239-feat-zd-48600/workspace/hobasa-agentic-sdlc/requirements/ZD-48470.md`
- `final_document/e2e-run/runs/run-20261025-111239-feat-zd-48600/workspace/hobasa-agentic-sdlc/requirements/ZD-48480.md`
- `final_document/e2e-run/runs/run-20261025-111239-feat-zd-48600/workspace/hobasa-agentic-sdlc/requirements/ZD-48501.md`
- `final_document/e2e-run/runs/run-20261025-111239-feat-zd-48600/workspace/hobasa-agentic-sdlc/requirements/ZD-48510.md`
- `final_document/e2e-run/runs/run-20261025-111239-feat-zd-48600/workspace/hobasa-agentic-sdlc/requirements/ZD-48600.md`

Shared memory and conventions: `memory/MEMORY.md` and `CLAUDE.md` in the SDLC repository.

## The step brief the agent was given (a valid source, cited as record:brief)

Your previous result for this step was refused. Fix every point, rewrite the output files in full, and return the structured result again.

## Refusal reasons
G1 judge found an unsupported statement: "The pre-backlog entry status stays "Draft entry for review"." (feat.prebacklog does record the status as "Draft entry for review; gate: PM". But the workspace history (commit 0648784 "FEAT-ZD-48600 REQ-01 Requirement Intake)
G1 judge found an unsupported statement: "The source item's own type tag is `New Feature`, which matches this classification." (In requirements/ZD-48600.md the field is `expected_type: New Feature`, an expected or oracle value, not a type tag on the ticket. The value is correct, but the )

## Step brief (unchanged except the attempt number)
# Step REQ-02: Grouping (attempt 1) for FEAT-ZD-48600

- Workbook trigger: Previous Requirement Intake
Technical has to be a sub-category under each and should be classified as Technical Only
This could go as a qualifier during requirement approval or as applicable ²
- Workbook action: New Ticket gets created
- Workbook outcome: Entry classified by category, duplicates merged
- Owner of this step: PM
- Gate (who approves this output): no gate: automated checks, the independent judge and sampled human evaluation

## Inputs (GitHub checkout; read them with Read, or context_get for a receipt)
- feat.prebacklog (Pre-backlog entry linked to roadmap and trace ID): `final_document/e2e-run/runs/run-20261025-111239-feat-zd-48600/workspace/agents/hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-02/feat.prebacklog.md` (from hobasa-requirement-agent/outputs/FEAT-ZD-48600/feat.prebacklog.md at commit 9919dd4)
- feat.intake (Original intake item with source link): `final_document/e2e-run/runs/run-20261025-111239-feat-zd-48600/workspace/agents/hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-02/feat.intake.md` (from hobasa-requirement-agent/outputs/FEAT-ZD-48600/feat.intake.md at commit 9919dd4)
- org.routing_map (Component-to-owner routing for defects): `final_document/e2e-run/runs/run-20261025-111239-feat-zd-48600/workspace/agents/hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-02/org.routing_map.md` (from hobasa-agentic-sdlc/features/FEAT-ZD-48600/org-overrides/org.routing_map.md at commit 9fbbfba)
- org.architecture (Platform architecture, contracts and tenancy rules): `final_document/e2e-run/runs/run-20261025-111239-feat-zd-48600/workspace/agents/hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-02/org.architecture.md` (from hobasa-agentic-sdlc/features/FEAT-ZD-48600/org-overrides/org.architecture.md at commit 9fbbfba)

## Outputs (write each file in full; the spine commits and pushes after evaluation and approval)
- feat.classification (Category, qualifier and merged duplicates): write `final_document/e2e-run/runs/run-20261025-111239-feat-zd-48600/workspace/agents/hobasa-requirement-agent/outputs/FEAT-ZD-48600/feat.classification.md`

## Impacted repositories
Decide which repositories this item must change, from the requirement and the routing map (`final_document/e2e-run/runs/run-20261025-111239-feat-zd-48600/workspace/hobasa-agentic-sdlc/org/org.routing_map.md`; read it). Bound repositories: ap_aging (Python 3.9 (standard library); BE); ap_forecast (Python 3.9 (standard library); DS); ap_pipeline (Python 3.9 (standard library); DE); ap_portal (Node.js 22 (CommonJS, node:test); FE). Add one line to your output exactly as `Impacted repositories: <comma-separated names>` (only those whose behaviour changes; documentation-only or configuration-only items name the repository whose docs or configuration change). Cite the routing map.

## How to work
Decide the best way to do this step from the inputs and the workbook action, plan it (TodoWrite for multi-part work), then do it. Helper subagents you can delegate to: explorer, verifier (use the verifier before you finish when the output makes many factual statements). Use the shared memory (memory_search) for decisions and lessons. Connectors approved for you: api:github (GitHub REST API for the Hobasa repositories: issues, pull requests, checks (GET /repos/<owner>/<repo>/...)). Use one only when your inputs do not hold what you need; request a missing one with capability_request. You may also read any other file in the GitHub checkouts your step needs (for example other requirements when grouping, or code); cite it as file:<repository>/<path>.

Finish with the structured result: approach, tools_used, claims (each citing an input item name, a tool view, api:<name>, mcp:<server>, file:<repository>/<path> for any other GitHub file you read, record:intake, record:owner_answer, record:memory or record:brief for this brief; a claim drawing on several sources lists them separated by ';'; every number must appear in what you cite), open questions (BLOCKING: only when you cannot finish), summary.