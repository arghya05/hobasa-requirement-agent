# Evaluate step REQ-05: Product Requirement Preparation for FEAT-ZD-48600

- Workbook action: drafts the PRD carrying approved BRD decisions forward and runs the validation check
- Workbook outcome: Product Requirement Document

## Outputs to evaluate
- `hobasa-requirement-agent/outputs/FEAT-ZD-48600/feat.prd.md`

## Inputs the agent was given
- feat.brd: `hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-05/feat.brd.md`
- org.templates: `hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-05/org.templates.md`

## Other GitHub files the agent read (valid sources when cited as file:<repository>/<path>)
- `hobasa-requirement-agent/outputs/FEAT-ZD-48600/feat.prd.md`
- `hobasa-agentic-sdlc/requirements/ZD-48600.md`

Shared memory and conventions: `memory/MEMORY.md` and `CLAUDE.md` in the SDLC repository.

## The step brief the agent was given (a valid source, cited as record:brief)

# Step REQ-05: Product Requirement Preparation (attempt 1) for FEAT-ZD-48600

- Workbook trigger: BRD approved
- Workbook action: drafts the PRD carrying approved BRD decisions forward and runs the validation check
- Workbook outcome: Product Requirement Document
- Owner of this step: PM
- Gate (who approves this output): PM

## Inputs (GitHub checkout; read them with Read, or context_get for a receipt)
- feat.brd (Approved BRD): `hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-05/feat.brd.md` (from hobasa-requirement-agent/outputs/FEAT-ZD-48600/feat.brd.md at commit 517ceb7)
- org.templates (BRD, PRD, TRD and story templates; business question set; EARS/Gherkin rules): `hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-05/org.templates.md` (from hobasa-agentic-sdlc/org/org.templates.md at commit 9fbbfba)

## Outputs (write each file in full; the spine commits and pushes after evaluation and approval)
- feat.prd (Approved PRD): write `hobasa-requirement-agent/outputs/FEAT-ZD-48600/feat.prd.md`


## How to work
Decide the best way to do this step from the inputs and the workbook action, plan it (TodoWrite for multi-part work), then do it. Helper subagents you can delegate to: explorer, verifier (use the verifier before you finish when the output makes many factual statements). Use the shared memory (memory_search) for decisions and lessons. Connectors approved for you: api:github (GitHub REST API for the Hobasa repositories: issues, pull requests, checks (GET /repos/<owner>/<repo>/...)). Use one only when your inputs do not hold what you need; request a missing one with capability_request. You may also read any other file in the GitHub checkouts your step needs (for example other requirements when grouping, or code); cite it as file:<repository>/<path>.

Finish with the structured result: approach, tools_used, claims (each citing an input item name, a tool view, api:<name>, mcp:<server>, file:<repository>/<path> for any other GitHub file you read, record:intake, record:owner_answer, record:memory or record:brief for this brief; a claim drawing on several sources lists them separated by ';'; every number must appear in what you cite), open questions (BLOCKING: only when you cannot finish), summary.