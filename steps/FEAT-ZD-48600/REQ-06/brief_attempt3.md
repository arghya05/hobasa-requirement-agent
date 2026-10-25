Your previous result for this step was refused. Fix every point, rewrite the output files in full, and return the structured result again.

## Refusal reasons
G2 claim cites file:ap_portal/src/ap_portal/index.js but the agent never read that file in this session

## Step brief (unchanged except the attempt number)
# Step REQ-06: Prototype ⁷ (attempt 3) for FEAT-ZD-48600

- Workbook trigger: PRD Reviewed
- Workbook action: builds the prototype prompt applying the design system, screen inventory, states and synthetic data rules, then checks the output against the PRD
- Workbook outcome: Low Fidelity Wireframes
- Owner of this step: PM
- Gate (who approves this output): UX lead

## Inputs (GitHub checkout; read them with Read, or context_get for a receipt)
- feat.prd (Approved PRD): `final_document/e2e-run/runs/run-20261025-111239-feat-zd-48600/workspace/agents/hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-06/feat.prd.md` (from hobasa-requirement-agent/outputs/FEAT-ZD-48600/feat.prd.md at commit 908b58d)
- org.design_library (Hobasa design library and variables (tokens)): `final_document/e2e-run/runs/run-20261025-111239-feat-zd-48600/workspace/agents/hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-06/org.design_library.md` (from hobasa-agentic-sdlc/features/FEAT-ZD-48600/org-overrides/org.design_library.md at commit 9fbbfba)

## Outputs (write each file in full; the spine commits and pushes after evaluation and approval)
- feat.prototype (FigJam flow and Figma Make prototype): write `final_document/e2e-run/runs/run-20261025-111239-feat-zd-48600/workspace/agents/hobasa-requirement-agent/outputs/FEAT-ZD-48600/feat.prototype.md`


## How to work
Decide the best way to do this step from the inputs and the workbook action, plan it (TodoWrite for multi-part work), then do it. Helper subagents you can delegate to: explorer, verifier (use the verifier before you finish when the output makes many factual statements). Use the shared memory (memory_search) for decisions and lessons. Connectors approved for you: api:github (GitHub REST API for the Hobasa repositories: issues, pull requests, checks (GET /repos/<owner>/<repo>/...)). Use one only when your inputs do not hold what you need; request a missing one with capability_request. You may also read any other file in the GitHub checkouts your step needs (for example other requirements when grouping, or code); cite it as file:<repository>/<path>.

Finish with the structured result: approach, tools_used, claims (each citing an input item name, a tool view, api:<name>, mcp:<server>, file:<repository>/<path> for any other GitHub file you read, record:intake, record:owner_answer, record:memory or record:brief for this brief; a claim drawing on several sources lists them separated by ';'; every number must appear in what you cite), open questions (BLOCKING: only when you cannot finish), summary.