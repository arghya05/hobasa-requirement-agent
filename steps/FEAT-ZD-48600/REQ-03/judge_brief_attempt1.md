# Evaluate step REQ-03: Product Fitment Validation for FEAT-ZD-48600

- Workbook action: Checks the entry against capability, roadmap and strategy and returns a verdict with its evidence : Yes or No
- Workbook outcome: Fitment verdict with evidence. Notification to PM and Leadership to decide
Yes or No ³

## Outputs to evaluate
- `hobasa-requirement-agent/outputs/FEAT-ZD-48600/feat.fitment.md`

## Inputs the agent was given
- feat.classification: `hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-03/feat.classification.md`
- org.strategy_capability: `hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-03/org.strategy_capability.md`
- org.roadmap: `hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-03/org.roadmap.md`

## Other GitHub files the agent read (valid sources when cited as file:<repository>/<path>)
- `hobasa-agentic-sdlc/requirements/ZD-48600.md`

Shared memory and conventions: `memory/MEMORY.md` and `CLAUDE.md` in the SDLC repository.

## The step brief the agent was given (a valid source, cited as record:brief)

# Step REQ-03: Product Fitment Validation (attempt 1) for FEAT-ZD-48600

- Workbook trigger: Previous Grouping
- Workbook action: Checks the entry against capability, roadmap and strategy and returns a verdict with its evidence : Yes or No
- Workbook outcome: Fitment verdict with evidence. Notification to PM and Leadership to decide
Yes or No ³

## Inputs (GitHub checkout; read them with Read, or context_get for a receipt)
- feat.classification (Category, qualifier and merged duplicates): `hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-03/feat.classification.md` (from hobasa-requirement-agent/outputs/FEAT-ZD-48600/feat.classification.md at commit 59cf8bf)
- org.strategy_capability (Product capability, strategy and vision for fitment): `hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-03/org.strategy_capability.md` (from hobasa-agentic-sdlc/org/org.strategy_capability.md at commit bf63f34)
- org.roadmap (Structured roadmap items): `hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-03/org.roadmap.md` (from hobasa-agentic-sdlc/org/org.roadmap.md at commit bf63f34)

## Outputs (write each file in full; the spine commits and pushes after evaluation and approval)
- feat.fitment (Fitment verdict with evidence and reason code): write `hobasa-requirement-agent/outputs/FEAT-ZD-48600/feat.fitment.md`


## How to work
Decide the best way to do this step from the inputs and the workbook action, plan it (TodoWrite for multi-part work), then do it. Helper subagents you can delegate to: explorer, verifier (use the verifier before you finish when the output makes many factual statements). Use the shared memory (memory_search) for decisions and lessons. Connectors approved for you: api:github (GitHub REST API for the Hobasa repositories: issues, pull requests, checks (GET /repos/<owner>/<repo>/...)). Use one only when your inputs do not hold what you need; request a missing one with capability_request. You may also read any other file in the GitHub checkouts your step needs (for example other requirements when grouping, or code); cite it as file:<repository>/<path>.

Finish with the structured result: approach, tools_used, claims (each citing an input item name, a tool view, api:<name>, mcp:<server>, file:<repository>/<path> for any other GitHub file you read, record:intake, record:owner_answer, record:memory or record:brief for this brief; a claim drawing on several sources lists them separated by ';'; every number must appear in what you cite), open questions (BLOCKING: only when you cannot finish), summary.