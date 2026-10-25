# REQ-07 Technical Requirement Document (Requirement agent)

**Item:** FEAT-ZD-48600 · **status:** done
**Trigger:** Prototype Approved  
**Action:** drafts the TRD from the PRD, prototype and current architecture  
**Outcome expected:** Technical Requirement Document

## Inputs (what the agent was given)

| Item | Prepared input (this repository) | Read from (producer in GitHub) | Commit | Produced by |
|---|---|---|---|---|
| feat.prd | hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-07/feat.prd.md | hobasa-requirement-agent/outputs/FEAT-ZD-48600/feat.prd.md | 908b58d | REQ-05 |
| feat.prototype | hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-07/feat.prototype.md | hobasa-requirement-agent/outputs/FEAT-ZD-48600/feat.prototype.md | 8fce3b3 | REQ-06 |
| org.architecture | hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-07/org.architecture.md | hobasa-agentic-sdlc/features/FEAT-ZD-48600/org-overrides/org.architecture.md | a6b3e2a | source |

Full brief per attempt: `brief_attempt<N>.md` (trigger event, owner answers, tool view, refusal reasons).

## Outputs (what the agent produced)

| Item | GitHub file |
|---|---|
| feat.trd | hobasa-requirement-agent/outputs/FEAT-ZD-48600/feat.trd.md |

## How the agent worked

- Approach: Attempt 3 fixes the repeated G2 refusals. The cause was a repository-name mismatch, not a missing read. I had cited the local checkout folder names (file:ap_pipeline/…, file:ap_forecast/…, file:ap_aging/…, file:ap_portal/…). The read tracker records these files under their GitHub repository names: ap-pipeline-sample, ap-forecast-sample, ap-aging-sample and ap-portal-sample. I found this in this item's earlier REQ-07 step record (steps/FEAT-ZD-48600/REQ-07/judge_brief_attempt3.md, which lists the files read under those names). I re-read every cited code file again in this attempt and rewrote feat.trd in full. Every code citation now uses the GitHub repository name, and the header states the folder-to-repository mapping. The content is otherwise the same as the verified draft. It follows the org.templates TRD sections (components affected, interfaces/contracts, data, security and tenancy, testing approach, risks). It builds on cited code findings F-1 to F-15, which include two existing-code conflicts for the Architect. It ends with assumptions, questions TQ-1 to TQ-11, PRD traceability and a decision-log check. I also called context_list to confirm the step's contracted inputs. No connector was needed.
- Tools used: Read, Write, Grep, mcp__hobasa-context__context_list, Skill (requirement-steps, attempt 1), Agent (verifier, attempt 1)
- Helper subagents: Agent
- Connector calls: none

## Attempts (checks before any person saw the output)

| Attempt | Session | Checks failed | Judge unsupported | Judge scores |
|---|---|---|---|---|
| 1 | new | 17 | — | — |
| 2 | resumed | 19 | — | — |
| 3 | resumed | 0 | 0 | {'correct': 5, 'complete': 5, 'grounded': 4, 'useful': 5} |

## Improvements the independent judge suggests (non-blocking, for the people at the gate)

- Citation repository names: the TRD cites code as `file:ap-pipeline-sample/…`, `file:ap-forecast-sample/…`, `file:ap-aging-sample/…` and `file:ap-portal-sample/…`. This session's read list and the refusal reasons name the same files as `ap_pipeline/…`, `ap_forecast/…`, `ap_aging/…` and `ap_portal/…`. The `-sample` names are not invented: they appear in judge_brief_attempt3.md, which the agent read. But the mismatch may trip the mechanical G2 'never read' check again. Use the repository form that the current read list uses.
- `ap_pipeline/src/ap_pipeline/schedule.json` is in the read list but is not cited. D-1 and NFR-9 ('daily 02:00 Asia/Kolkata unchanged') could be confirmed against the current schedule in code instead of resting only on the org override and the PRD.
- T-3, T-11 and T-16 say existing tests must keep passing, but only `ap_portal/tests/portal.test.js` is cited. Name the existing Python test modules, or say they were not read, so the regression baseline is concrete for the coding lanes.
- IF-1.5 (existing reject reasons take precedence over 'paid_date') narrows AC-3. It is correctly raised as TQ-10, but the Architect should decide it explicitly because it changes test expectations in T-2 and T-3.
- `to_model` strips `vendor`, and `delays_by_vendor` and `overdue_with_risk` key on that stripped value. Saying explicitly in IF-2 or IF-5 that both must use the same `records` (as IF-8 does) would remove a possible key-mismatch ambiguity if the lanes test with hand-built invoices.

Details: `result_attempt<N>.json` (claims with sources), `checks_attempt<N>.json`, `judge_attempt<N>.json`.

## Human evaluation

| Role | By | Decision | Scores | Comment or reason |
|---|---|---|---|---|
| Architect | sim.architect | approve | — | automated checks and the independent judge passed |
