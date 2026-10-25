# Evaluate step REQ-04: BRD Preparation for FEAT-ZD-48600

- Workbook action: asks the business question set, drafts the BRD against the template and runs the validation check
- Workbook outcome: Business Requirement Document

## Outputs to evaluate
- `hobasa-requirement-agent/outputs/FEAT-ZD-48600/feat.brd.md`

## Inputs the agent was given
- feat.fitment: `hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-04/feat.fitment.md`
- feat.intake: `hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-04/feat.intake.md`
- org.templates: `hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-04/org.templates.md`
- org.strategy_capability: `hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-04/org.strategy_capability.md`
- org.decision_log: `hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-04/org.decision_log.md`

## Other GitHub files the agent read (valid sources when cited as file:<repository>/<path>)
- `hobasa-requirement-agent/outputs/FEAT-ZD-48600/feat.brd.md`
- `hobasa-requirement-agent/outputs/FEAT-ZD-48600/feat.classification.md`
- `hobasa-requirement-agent/outputs/FEAT-ZD-48600/feat.prebacklog.md`
- `hobasa-agentic-sdlc/features/FEAT-ZD-48600/COMMUNICATION.md`
- `hobasa-agentic-sdlc/requirements/ZD-48600.md`

Shared memory and conventions: `memory/MEMORY.md` and `CLAUDE.md` in the SDLC repository.

## The step brief the agent was given (a valid source, cited as record:brief)

Your previous result for this step was refused. Fix every point, rewrite the output files in full, and return the structured result again.

## Refusal reasons
G2 claim cites mcp:hobasa-context but that connector was not used in this session

## Step brief (unchanged except the attempt number)
# Step REQ-04: BRD Preparation (attempt 2) for FEAT-ZD-48600

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