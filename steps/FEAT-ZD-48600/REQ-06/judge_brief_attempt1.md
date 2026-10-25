# Evaluate step REQ-06: Prototype ⁷ for FEAT-ZD-48600

- Workbook action: builds the prototype prompt applying the design system, screen inventory, states and synthetic data rules, then checks the output against the PRD
- Workbook outcome: Low Fidelity Wireframes

## Outputs to evaluate
- `final_document/e2e-run/runs/run-20261025-111239-feat-zd-48600/workspace/agents/hobasa-requirement-agent/outputs/FEAT-ZD-48600/feat.prototype.md`

## Inputs the agent was given
- feat.prd: `final_document/e2e-run/runs/run-20261025-111239-feat-zd-48600/workspace/agents/hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-06/feat.prd.md`
- org.design_library: `final_document/e2e-run/runs/run-20261025-111239-feat-zd-48600/workspace/agents/hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-06/org.design_library.md`

## Other GitHub files the agent read (valid sources when cited as file:<repository>/<path>)
- `final_document/e2e-run/runs/run-20261025-111239-feat-zd-48600/workspace/agents/hobasa-requirement-agent/outputs/FEAT-ZD-48600/feat.prototype.md`
- `final_document/e2e-run/runs/run-20261025-111239-feat-zd-48600/workspace/ap_portal/README.md`
- `final_document/e2e-run/runs/run-20261025-111239-feat-zd-48600/workspace/ap_portal/src/ap_portal/index.js`

Shared memory and conventions: `memory/MEMORY.md` and `CLAUDE.md` in the SDLC repository.

## The step brief the agent was given (a valid source, cited as record:brief)

Your previous result for this step was refused. Fix every point, rewrite the output files in full, and return the structured result again.

## Refusal reasons
G1 judge found an unsupported statement: "No secrets or personal data in outputs (G8) | record:brief" (Neither the step brief nor any input mentions a gate or rule called "G8", or a rule against secrets or personal data. The only gate ID in the brief is G2, in th)
G1 judge found an unsupported statement: "| SD-1 | Synthetic data only: ids prefixed `SYN-INV-`, vendor names "Synthetic Vendor <letter>"; no real vendor, person, bank or contact data | ... | record:bri" (The brief names synthetic data rules in the workbook action, but it defines none. Section 6 and PQ-P5 correctly say that SD-1 to SD-6 are agent judgement, yet S)

## Step brief (unchanged except the attempt number)
# Step REQ-06: Prototype ⁷ (attempt 1) for FEAT-ZD-48600

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