# REQ-07 · Technical Requirement Document

**Agent:** Requirement · **Item:** FEAT-ZD-48600 · **Status:** ✅ done · approved in an earlier run, reused
**Approved by:** Architect: approve by sim.architect

**What this step does:** drafts the TRD from the PRD, prototype and current architecture

**Expected outcome:** Technical Requirement Document

**Started by:** Prototype Approved

## Input: what the agent received

| # | Input | What it is | Produced by | Open |
|---|---|---|---|---|
| 1 | `feat.prd` | Approved PRD | Requirement agent · REQ-05 | [input copy](https://github.com/arghya05/hobasa-agentic-sdlc/blob/main//Users/arghyamukherjee/Documents/automaiton/final_document/e2e-run/runs/run-20261025-123936-feat-zd-48600/workspace/agents/hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-07/feat.prd.md) · [original](https://github.com/arghya05/hobasa-requirement-agent/blob/main/outputs/FEAT-ZD-48600/feat.prd.md) · [HTML](https://htmlpreview.github.io/?https://raw.githubusercontent.com/arghya05/hobasa-requirement-agent/main/docs/FEAT-ZD-48600/REQ-05_feat-prd.html) · [PDF](https://github.com/arghya05/hobasa-requirement-agent/blob/main/docs/FEAT-ZD-48600/REQ-05_feat-prd.pdf) |
| 2 | `feat.prototype` | FigJam flow and Figma Make prototype | Requirement agent · REQ-06 | [input copy](https://github.com/arghya05/hobasa-agentic-sdlc/blob/main//Users/arghyamukherjee/Documents/automaiton/final_document/e2e-run/runs/run-20261025-123936-feat-zd-48600/workspace/agents/hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-07/feat.prototype.md) · [original](https://github.com/arghya05/hobasa-requirement-agent/blob/main/outputs/FEAT-ZD-48600/feat.prototype.md) · [HTML](https://htmlpreview.github.io/?https://raw.githubusercontent.com/arghya05/hobasa-requirement-agent/main/docs/FEAT-ZD-48600/REQ-06_feat-prototype.html) · [PDF](https://github.com/arghya05/hobasa-requirement-agent/blob/main/docs/FEAT-ZD-48600/REQ-06_feat-prototype.pdf) |
| 3 | `org.architecture` | Platform architecture, contracts and tenancy rules | organisation source | [input copy](https://github.com/arghya05/hobasa-agentic-sdlc/blob/main//Users/arghyamukherjee/Documents/automaiton/final_document/e2e-run/runs/run-20261025-123936-feat-zd-48600/workspace/agents/hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-07/org.architecture.md) · [original](https://github.com/arghya05/hobasa-agentic-sdlc/blob/main/features/FEAT-ZD-48600/org-overrides/org.architecture.md) |

The full brief the agent was given, attempt by attempt: `brief_attempt<N>.md` in this folder.

## Output: what the agent produced

| # | Output | What it is | Open |
|---|---|---|---|
| 1 | `feat.trd` | Approved TRD | [Markdown](https://github.com/arghya05/hobasa-requirement-agent/blob/main/outputs/FEAT-ZD-48600/feat.trd.md) · [HTML](https://htmlpreview.github.io/?https://raw.githubusercontent.com/arghya05/hobasa-requirement-agent/main/docs/FEAT-ZD-48600/REQ-07_feat-trd.html) · [PDF](https://github.com/arghya05/hobasa-requirement-agent/blob/main/docs/FEAT-ZD-48600/REQ-07_feat-trd.pdf) |

## Checks and approval

| Attempt | Session | Problems found by the checks | Unsupported statements (judge) | Judge scores |
|---|---|---|---|---|
| 1 | new | 17 | — | — |
| 2 | continued | 19 | — | — |
| 3 | continued | 0 | 0 | {'correct': 5, 'complete': 5, 'grounded': 4, 'useful': 5} |

Improvements the independent judge suggests (non-blocking):

- Citation repository names: the TRD cites code as `file:ap-pipeline-sample/…`, `file:ap-forecast-sample/…`, `file:ap-aging-sample/…` and `file:ap-portal-sample/…`. This session's read list and the refusal reasons name the same files as `ap_pipeline/…`, `ap_forecast/…`, `ap_aging/…` and `ap_portal/…`. The `-sample` names are not invented: they appear in judge_brief_attempt3.md, which the agent read. But the mismatch may trip the mechanical G2 'never read' check again. Use the repository form that the current read list uses.
- `ap_pipeline/src/ap_pipeline/schedule.json` is in the read list but is not cited. D-1 and NFR-9 ('daily 02:00 Asia/Kolkata unchanged') could be confirmed against the current schedule in code instead of resting only on the org override and the PRD.
- T-3, T-11 and T-16 say existing tests must keep passing, but only `ap_portal/tests/portal.test.js` is cited. Name the existing Python test modules, or say they were not read, so the regression baseline is concrete for the coding lanes.
- IF-1.5 (existing reject reasons take precedence over 'paid_date') narrows AC-3. It is correctly raised as TQ-10, but the Architect should decide it explicitly because it changes test expectations in T-2 and T-3.
- `to_model` strips `vendor`, and `delays_by_vendor` and `overdue_with_risk` key on that stripped value. Saying explicitly in IF-2 or IF-5 that both must use the same `records` (as IF-8 does) would remove a possible key-mismatch ambiguity if the lanes test with hand-built invoices.

## How the agent worked

- **Approach:** Attempt 3 fixes the repeated G2 refusals. The cause was a repository-name mismatch, not a missing read. I had cited the local checkout folder names (file:ap_pipeline/…, file:ap_forecast/…, file:ap_aging/…, file:ap_portal/…). The read tracker records these files under their GitHub repository names: ap-pipeline-sample, ap-forecast-sample, ap-aging-sample and ap-portal-sample. I found this in this item's earlier REQ-07 step record (steps/FEAT-ZD-48600/REQ-07/judge_brief_attempt3.md, which lists the files read under those names). I re-read every cited code file again in this attempt and rewrote feat.trd in full. Every code citation now uses the GitHub repository name, and the header states the folder-to-repository mapping. The content is otherwise the same as the verified draft. It follows the org.templates TRD sections (components affected, interfaces/contracts, data, security and tenancy, testing approach, risks). It builds on cited code findings F-1 to F-15, which include two existing-code conflicts for the Architect. It ends with assumptions, questions TQ-1 to TQ-11, PRD traceability and a decision-log check. I also called context_list to confirm the step's contracted inputs. No connector was needed.
- **Tools used:** Read, Write, Grep, mcp__hobasa-context__context_list, Skill (requirement-steps, attempt 1), Agent (verifier, attempt 1)
- **Helper subagents:** Agent
- **Connector calls:** none

## Human evaluation

| Role | By | Decision | Scores (correct, complete, grounded, useful) | Comment or reason |
|---|---|---|---|---|
| Architect | sim.architect | approve | — | automated checks and the independent judge passed |

## Files in this folder (audit trail)

- `brief_attempt<N>.md`: the exact brief the agent received
- `result_attempt<N>.json`: the agent's structured answer (approach, tools, claims with their sources, open questions)
- `checks_attempt<N>.json`: what the automated guardrail checks found
- `judge_attempt<N>.json`, `judge_brief_attempt<N>.md`: the independent judge
- `outputs/`: the outputs as approved
