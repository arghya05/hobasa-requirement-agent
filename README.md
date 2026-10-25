# Hobasa Requirement agent

Requirement Agent in the Hobasa agentic SDLC. Owner: PM, with leadership and domain SMEs for fitment and business approval.. It runs on Claude Code: every step is one Claude Code session started by the Hobasa spine, with this agent's prompt and step skill (`.claude/`), helper subagents, guardrail hooks and the shared context server.

**Reads from GitHub:** each step's inputs are prepared in `inputs/<trace>/<STEP>/` with the repository, path and commit they came from (other agents' `outputs/`, the requirements and organisation sources in `hobasa-agentic-sdlc`, code in the `*-sample` repositories).

**Writes back to GitHub:** approved outputs in `outputs/<trace>/`; every step run in `steps/<trace>/<STEP>/` (brief, attempts, claims, checks, independent judge, human decision). Code changes go to the `*-sample` repositories. Journey, evaluations and shared memory: `hobasa-agentic-sdlc`.

## Steps

| Step | Name | Reads | Writes | Gate |
|---|---|---|---|---|
| REQ-01 | Requirement Intake | org.roadmap, org.regulatory_sources, org.connector_inventory, org.model_dependency_map, org.decision_log | feat.intake, feat.prebacklog | PM |
| REQ-02 | Grouping | feat.prebacklog, feat.intake | feat.classification | checks + sampled evaluation |
| REQ-03 | Product Fitment Validation | feat.classification, org.strategy_capability, org.roadmap | feat.fitment | PM, Leadership |
| REQ-04 | BRD Preparation | feat.fitment, feat.intake, org.templates, org.strategy_capability, org.decision_log | feat.brd | Leadership |
| REQ-05 | Product Requirement Preparation | feat.brd, org.templates | feat.prd | PM |
| REQ-06 | Prototype ⁷ | feat.prd, org.design_library | feat.prototype | UX lead |
| REQ-07 | Technical Requirement Document | feat.prd, feat.prototype, org.architecture | feat.trd | Architect |
| REQ-08 | User Story Preparation | feat.prd, feat.prototype, feat.trd, org.templates | feat.stories | PM |
| CMP-P01 | Regulatory impact analysis (proposed) | feat.intake, org.regulatory_sources, org.rule_catalogue | feat.rule_impact | Compliance SME |
| CMP-P02 | Rule specification and ground truth (proposed) | feat.rule_impact | feat.rule_spec | Compliance SME |

<!-- work:FEAT-ZD-48600:start -->
## Work done for FEAT-ZD-48600

| Step | Name | Status | Input | Output | Details |
|---|---|---|---|---|---|
| REQ-01 | Requirement Intake | done | `org.roadmap`, `org.regulatory_sources`, `org.connector_inventory`, `org.model_dependency_map`, `org.decision_log` | `feat.intake`: [Markdown](https://github.com/arghya05/hobasa-requirement-agent/blob/main/outputs/FEAT-ZD-48600/feat.intake.md) · [HTML](https://htmlpreview.github.io/?https://raw.githubusercontent.com/arghya05/hobasa-requirement-agent/main/docs/FEAT-ZD-48600/REQ-01_feat-intake.html) · [PDF](https://github.com/arghya05/hobasa-requirement-agent/blob/main/docs/FEAT-ZD-48600/REQ-01_feat-intake.pdf)<br>`feat.prebacklog`: [Markdown](https://github.com/arghya05/hobasa-requirement-agent/blob/main/outputs/FEAT-ZD-48600/feat.prebacklog.md) · [HTML](https://htmlpreview.github.io/?https://raw.githubusercontent.com/arghya05/hobasa-requirement-agent/main/docs/FEAT-ZD-48600/REQ-01_feat-prebacklog.html) · [PDF](https://github.com/arghya05/hobasa-requirement-agent/blob/main/docs/FEAT-ZD-48600/REQ-01_feat-prebacklog.pdf) | [step record](https://github.com/arghya05/hobasa-requirement-agent/blob/main/steps/FEAT-ZD-48600/REQ-01/README.md) |
| REQ-02 | Grouping | done | `feat.prebacklog`, `feat.intake`, `org.routing_map`, `org.architecture` | `feat.classification`: [Markdown](https://github.com/arghya05/hobasa-requirement-agent/blob/main/outputs/FEAT-ZD-48600/feat.classification.md) · [HTML](https://htmlpreview.github.io/?https://raw.githubusercontent.com/arghya05/hobasa-requirement-agent/main/docs/FEAT-ZD-48600/REQ-02_feat-classification.html) · [PDF](https://github.com/arghya05/hobasa-requirement-agent/blob/main/docs/FEAT-ZD-48600/REQ-02_feat-classification.pdf) | [step record](https://github.com/arghya05/hobasa-requirement-agent/blob/main/steps/FEAT-ZD-48600/REQ-02/README.md) |
| REQ-03 | Product Fitment Validation | done | `feat.classification`, `org.strategy_capability`, `org.roadmap` | `feat.fitment`: [Markdown](https://github.com/arghya05/hobasa-requirement-agent/blob/main/outputs/FEAT-ZD-48600/feat.fitment.md) · [HTML](https://htmlpreview.github.io/?https://raw.githubusercontent.com/arghya05/hobasa-requirement-agent/main/docs/FEAT-ZD-48600/REQ-03_feat-fitment.html) · [PDF](https://github.com/arghya05/hobasa-requirement-agent/blob/main/docs/FEAT-ZD-48600/REQ-03_feat-fitment.pdf) | [step record](https://github.com/arghya05/hobasa-requirement-agent/blob/main/steps/FEAT-ZD-48600/REQ-03/README.md) |
<!-- work:FEAT-ZD-48600:end -->
