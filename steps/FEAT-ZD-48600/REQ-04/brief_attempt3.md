Your previous result for this step was refused. Fix every point, rewrite the output files in full, and return the structured result again.

## Refusal reasons
G1 judge found an unsupported statement: "**Business Requirement Document, status: Draft for the Leadership gate.** ... Leadership approves; the PM owns the item. (record:brief; feat.fitment)" (Neither the brief nor feat.fitment says who approves the REQ-04 BRD gate. The brief names no gate role for this step. feat.fitment only names PM as the R-AP-12 )
G1 judge found an unsupported statement: "Leadership | Approve this BRD (REQ-04 gate); decide OQ-B1 with the PM; decide OQ-B2 | Pending | record:brief; feat.fitment (OQ-F1, OQ-F3)" (The cited sources do not establish that the REQ-04 gate is a Leadership approval. record:brief does not name an approver role for the BRD. The OQ-B1 and OQ-B2 a)
G1 judge found an unsupported statement: "BR-10 | When a risk level is given, the payment-delay explanation ends with " Risk level: <risk>.". Without it, the explanation is unchanged." (CR-4 in feat.intake says the *prompt* built by build_explanation_request ends with ' Risk level: <risk>.', not the explanation itself. The explanation is the mo)

## Step brief (unchanged except the attempt number)
# Step REQ-04: BRD Preparation (attempt 3) for FEAT-ZD-48600

- Workbook trigger: Previous Step
- Workbook action: asks the business question set, drafts the BRD against the template and runs the validation check
- Workbook outcome: Business Requirement Document

## Inputs (GitHub checkout; read them with Read, or context_get for a receipt)
- feat.fitment (Fitment verdict with evidence and reason code): `hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-04/feat.fitment.md` (from hobasa-requirement-agent/outputs/FEAT-ZD-48600/feat.fitment.md at commit 3603ae6)
- feat.intake (Original intake item with source link): `hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-04/feat.intake.md` (from hobasa-requirement-agent/outputs/FEAT-ZD-48600/feat.intake.md at commit fd588b3)
- org.templates (BRD, PRD, TRD and story templates; business question set; EARS/Gherkin rules): `hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-04/org.templates.md` (from hobasa-agentic-sdlc/org/org.templates.md at commit bf63f34)
- org.strategy_capability (Product capability, strategy and vision for fitment): `hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-04/org.strategy_capability.md` (from hobasa-agentic-sdlc/org/org.strategy_capability.md at commit bf63f34)
- org.decision_log (Prior leadership and product decisions): `hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-04/org.decision_log.md` (from hobasa-agentic-sdlc/org/org.decision_log.md at commit bf63f34)

## Outputs (write each file in full; the spine commits and pushes after evaluation and approval)
- feat.brd (Approved BRD): write `hobasa-requirement-agent/outputs/FEAT-ZD-48600/feat.brd.md`


## How to work
Decide the best way to do this step from the inputs and the workbook action, plan it (TodoWrite for multi-part work), then do it. Helper subagents you can delegate to: explorer, verifier (use the verifier before you finish when the output makes many factual statements). Use the shared memory (memory_search) for decisions and lessons. Connectors approved for you: api:github (GitHub REST API for the Hobasa repositories: issues, pull requests, checks (GET /repos/<owner>/<repo>/...)). Use one only when your inputs do not hold what you need; request a missing one with capability_request. You may also read any other file in the GitHub checkouts your step needs (for example other requirements when grouping, or code); cite it as file:<repository>/<path>.

Finish with the structured result: approach, tools_used, claims (each citing an input item name, a tool view, api:<name>, mcp:<server>, file:<repository>/<path> for any other GitHub file you read, record:intake, record:owner_answer, record:memory or record:brief for this brief; a claim drawing on several sources lists them separated by ';'; every number must appear in what you cite), open questions (BLOCKING: only when you cannot finish), summary.