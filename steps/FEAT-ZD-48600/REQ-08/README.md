# REQ-08 User Story Preparation (Requirement agent)

**Item:** FEAT-ZD-48600 · **status:** done
**Trigger:** Prototype approved ⁵  
**Action:** decomposes into epic, feature, story and task with numbered acceptance criteria, dependencies and specification depth  
**Outcome expected:** User Stories in NEW state

Document all the assumptions, and if there are any unresolved open items ⁶

## Inputs (what the agent was given)

| Item | Prepared input (this repository) | Read from (producer in GitHub) | Commit | Produced by |
|---|---|---|---|---|
| feat.prd | hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-08/feat.prd.md | hobasa-requirement-agent/outputs/FEAT-ZD-48600/feat.prd.md | 908b58d | REQ-05 |
| feat.prototype | hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-08/feat.prototype.md | hobasa-requirement-agent/outputs/FEAT-ZD-48600/feat.prototype.md | 8fce3b3 | REQ-06 |
| feat.trd | hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-08/feat.trd.md | hobasa-requirement-agent/outputs/FEAT-ZD-48600/feat.trd.md | 3637e51 | REQ-07 |
| org.templates | hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-08/org.templates.md | hobasa-agentic-sdlc/org/org.templates.md | a6b3e2a | source |

Full brief per attempt: `brief_attempt<N>.md` (trigger event, owner answers, tool view, refusal reasons).

## Outputs (what the agent produced)

| Item | GitHub file |
|---|---|
| feat.stories | hobasa-requirement-agent/outputs/FEAT-ZD-48600/feat.stories.md |

## How the agent worked

- Approach: Attempt 2 fixes the G3 refusal. One claim quoted story labels I assigned in this step (for example "STORY-06"). The check read their digits as numbers, and they do not appear in feat.trd or feat.prd. In this result, every claim describes a story by its function (the paid_date story, the serialiser story and so on). Every remaining digit in a claim comes from the source it cites. I rewrote feat.stories in full. Its story content is the attempt-1 version after the verifier's corrections. It now also has a note saying the EP/FT/STORY/TK/AC-nn.n/SA/SQ labels are assigned in this step, a revision note for attempt 2, and one fix in the carried open-items map: OQ-B6 now also lists the delay-history story. The method is the same as attempt 1. I read the four contracted inputs, the existing unit test files and predict.py. I split the work into one epic, five features (one per lane), eight NEW stories and their tasks, following the story template. Each story gives frame links to the prototype's text frames, dependencies, a specification depth, and [Pending] markers on criteria that rest on open questions. No priority is set. A verifier pass on attempt 1 found 11 issues, and all of them are fixed in this content.
- Tools used: Skill (requirement-steps), Read, Glob, Grep, Write, Edit, Agent (verifier)
- Helper subagents: Agent
- Connector calls: none

## Attempts (checks before any person saw the output)

| Attempt | Session | Checks failed | Judge unsupported | Judge scores |
|---|---|---|---|---|
| 1 | new | 1 | — | — |
| 2 | resumed | 0 | 0 | {'correct': 5, 'complete': 4, 'grounded': 5, 'useful': 5} |

## Improvements the independent judge suggests (non-blocking, for the people at the gate)

- The Mermaid diagram in section 2 leaves out the STORY-01 → STORY-08 and STORY-05 → STORY-08 edges, but the dependency table lists both for STORY-08 ("STORY-01, 02, 03, 05, 06, 07"). The diagram should match the table.
- NFR-9 (feed schedule unchanged: daily 02:00 Asia/Kolkata) is traced to STORY-01 in its PRD trace and in section 7, but no STORY-01 acceptance criterion or task covers it. Either add a short criterion saying the schedule and configuration are not changed, or say plainly that NFR-9 has no testable criterion.
- AC-08.4 lists outcomes the end-to-end harness must assert: the invalid row appears in reject_reasons as 'paid_date', and rows of the vendor with no paid history get the class risk-unknown. TRD T-17 only lists these cases as feed contents, not as assertions. The criteria follow from AC-3, AC-17 and IF-2.5, but the trace column should cite IF-2.5 and F-4 as well as T-17.
- The revision note on line 11 describes the structured-result claims, not the stories. Gate reviewers don't need it in the deliverable; move it to the structured result or drop it.
- The workbook outcome is 'User Stories in NEW state'. The file states NEW for every story, but nothing records creating or syncing the stories on the DevOps board. Add an open item saying who moves these stories onto the board, or confirm that the file is the system of record.
- STORY-06's actor and purpose are agent judgement (SA-7), and it reuses US-1 as its PRD story. Consider asking the PM in SQ-1 or SQ-4 whether a technical enabler story (no 'As a') is the better form here.

Details: `result_attempt<N>.json` (claims with sources), `checks_attempt<N>.json`, `judge_attempt<N>.json`.

## Human evaluation

| Role | By | Decision | Scores | Comment or reason |
|---|---|---|---|---|
| PM | sim.pm | approve | — | automated checks and the independent judge passed |
