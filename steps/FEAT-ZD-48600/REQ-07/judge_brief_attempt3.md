# Evaluate step REQ-07: Technical Requirement Document for FEAT-ZD-48600

- Workbook action: drafts the TRD from the PRD, prototype and current architecture
- Workbook outcome: Technical Requirement Document

## Outputs to evaluate
- `hobasa-requirement-agent/outputs/FEAT-ZD-48600/feat.trd.md`

## Inputs the agent was given
- feat.prd: `hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-07/feat.prd.md`
- feat.prototype: `hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-07/feat.prototype.md`
- org.architecture: `hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-07/org.architecture.md`

## Other GitHub files the agent read (valid sources when cited as file:<repository>/<path>)
- `hobasa-requirement-agent/outputs/FEAT-ZD-48600/feat.trd.md`
- `ap-aging-sample/CLAUDE.md`
- `ap-aging-sample/README.md`
- `ap-aging-sample/ci.py`
- `ap-aging-sample/src/ap_aging/__init__.py`
- `ap-aging-sample/src/ap_aging/aging.py`
- `ap-aging-sample/tests/test_aging.py`
- `ap-forecast-sample/CLAUDE.md`
- `ap-forecast-sample/README.md`
- `ap-forecast-sample/ci.py`
- `ap-forecast-sample/src/ap_forecast/__init__.py`
- `ap-forecast-sample/src/ap_forecast/explain.py`
- `ap-forecast-sample/src/ap_forecast/models.json`
- `ap-forecast-sample/src/ap_forecast/predict.py`
- `ap-forecast-sample/tests/test_forecast.py`
- `ap-pipeline-sample/CLAUDE.md`
- `ap-pipeline-sample/README.md`
- `ap-pipeline-sample/ci.py`
- `ap-pipeline-sample/src/ap_pipeline/__init__.py`
- `ap-pipeline-sample/src/ap_pipeline/dq.py`
- `ap-pipeline-sample/src/ap_pipeline/ingest.py`
- `ap-pipeline-sample/src/ap_pipeline/pipeline.py`
- `ap-pipeline-sample/src/ap_pipeline/schedule.json`
- `ap-pipeline-sample/src/ap_pipeline/transform.py`
- `ap-pipeline-sample/tests/test_pipeline.py`
- `ap-portal-sample/CLAUDE.md`
- `ap-portal-sample/README.md`
- `ap-portal-sample/ci.mjs`
- `ap-portal-sample/package.json`
- `ap-portal-sample/src/ap_portal/index.js`
- `ap-portal-sample/tests/portal.test.js`
- `hobasa-agentic-sdlc/memory/MEMORY.md`
- `hobasa-agentic-sdlc/org/org.templates.md`
- `hobasa-agentic-sdlc/requirements/ZD-48600.md`

Shared memory and conventions: `memory/MEMORY.md` and `CLAUDE.md` in the SDLC repository.

## The step brief the agent was given (a valid source, cited as record:brief)

Your previous result for this step was refused. Fix every point, rewrite the output files in full, and return the structured result again.

## Refusal reasons
G3 numbers ['2', '7'] in "The TRD template sections are components affected, interfaces/contracts, data, security and tenancy," do not appear in file:hobasa-agentic-sdlc/org/org.templates.md

## Step brief (unchanged except the attempt number)
# Step REQ-07: Technical Requirement Document (attempt 3) for FEAT-ZD-48600

- Workbook trigger: Prototype Approved
- Workbook action: drafts the TRD from the PRD, prototype and current architecture
- Workbook outcome: Technical Requirement Document
- Owner of this step: PM
- Gate (who approves this output): Architect

## Inputs (GitHub checkout; read them with Read, or context_get for a receipt)
- feat.prd (Approved PRD): `hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-07/feat.prd.md` (from hobasa-requirement-agent/outputs/FEAT-ZD-48600/feat.prd.md at commit 908b58d)
- feat.prototype (FigJam flow and Figma Make prototype): `hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-07/feat.prototype.md` (from hobasa-requirement-agent/outputs/FEAT-ZD-48600/feat.prototype.md at commit 8fce3b3)
- org.architecture (Platform architecture, contracts and tenancy rules): `hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-07/org.architecture.md` (from hobasa-agentic-sdlc/features/FEAT-ZD-48600/org-overrides/org.architecture.md at commit 9fbbfba)

## Outputs (write each file in full; the spine commits and pushes after evaluation and approval)
- feat.trd (Approved TRD): write `hobasa-requirement-agent/outputs/FEAT-ZD-48600/feat.trd.md`


## How to work
Decide the best way to do this step from the inputs and the workbook action, plan it (TodoWrite for multi-part work), then do it. Helper subagents you can delegate to: explorer, verifier (use the verifier before you finish when the output makes many factual statements). Use the shared memory (memory_search) for decisions and lessons. Connectors approved for you: api:github (GitHub REST API for the Hobasa repositories: issues, pull requests, checks (GET /repos/<owner>/<repo>/...)). Use one only when your inputs do not hold what you need; request a missing one with capability_request. You may also read any other file in the GitHub checkouts your step needs (for example other requirements when grouping, or code); cite it as file:<repository>/<path>.

Finish with the structured result: approach, tools_used, claims (each citing an input item name, a tool view, api:<name>, mcp:<server>, file:<repository>/<path> for any other GitHub file you read, record:intake, record:owner_answer, record:memory or record:brief for this brief; a claim drawing on several sources lists them separated by ';'; every number must appear in what you cite), open questions (BLOCKING: only when you cannot finish), summary.