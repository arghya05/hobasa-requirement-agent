# REQ-08 · User Story Preparation

**Agent:** Requirement · **Item:** FEAT-ZD-48600 · **Status:** ✅ done · approved in an earlier run, reused
**Approved by:** PM: approve by sim.pm

**What this step does:** decomposes into epic, feature, story and task with numbered acceptance criteria, dependencies and specification depth

**Expected outcome:** User Stories in NEW state

Document all the assumptions, and if there are any unresolved open items ⁶

**Started by:** Prototype approved ⁵

## Input: what the agent received

| # | Input | What it is | Produced by | Open |
|---|---|---|---|---|
| 1 | `feat.prd` | Approved PRD | Requirement agent · REQ-05 | [input copy](https://github.com/arghya05/hobasa-agentic-sdlc/blob/main//Users/arghyamukherjee/Documents/automaiton/final_document/e2e-run/runs/run-20261025-123936-feat-zd-48600/workspace/agents/hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-08/feat.prd.md) · [original](https://github.com/arghya05/hobasa-requirement-agent/blob/main/outputs/FEAT-ZD-48600/feat.prd.md) · [HTML](https://htmlpreview.github.io/?https://raw.githubusercontent.com/arghya05/hobasa-requirement-agent/main/docs/FEAT-ZD-48600/REQ-05_feat-prd.html) · [PDF](https://github.com/arghya05/hobasa-requirement-agent/blob/main/docs/FEAT-ZD-48600/REQ-05_feat-prd.pdf) |
| 2 | `feat.prototype` | FigJam flow and Figma Make prototype | Requirement agent · REQ-06 | [input copy](https://github.com/arghya05/hobasa-agentic-sdlc/blob/main//Users/arghyamukherjee/Documents/automaiton/final_document/e2e-run/runs/run-20261025-123936-feat-zd-48600/workspace/agents/hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-08/feat.prototype.md) · [original](https://github.com/arghya05/hobasa-requirement-agent/blob/main/outputs/FEAT-ZD-48600/feat.prototype.md) · [HTML](https://htmlpreview.github.io/?https://raw.githubusercontent.com/arghya05/hobasa-requirement-agent/main/docs/FEAT-ZD-48600/REQ-06_feat-prototype.html) · [PDF](https://github.com/arghya05/hobasa-requirement-agent/blob/main/docs/FEAT-ZD-48600/REQ-06_feat-prototype.pdf) |
| 3 | `feat.trd` | Approved TRD | Requirement agent · REQ-07 | [input copy](https://github.com/arghya05/hobasa-agentic-sdlc/blob/main//Users/arghyamukherjee/Documents/automaiton/final_document/e2e-run/runs/run-20261025-123936-feat-zd-48600/workspace/agents/hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-08/feat.trd.md) · [original](https://github.com/arghya05/hobasa-requirement-agent/blob/main/outputs/FEAT-ZD-48600/feat.trd.md) · [HTML](https://htmlpreview.github.io/?https://raw.githubusercontent.com/arghya05/hobasa-requirement-agent/main/docs/FEAT-ZD-48600/REQ-07_feat-trd.html) · [PDF](https://github.com/arghya05/hobasa-requirement-agent/blob/main/docs/FEAT-ZD-48600/REQ-07_feat-trd.pdf) |
| 4 | `org.templates` | BRD, PRD, TRD and story templates; business question set; EARS/Gherkin rules | organisation source | [input copy](https://github.com/arghya05/hobasa-agentic-sdlc/blob/main//Users/arghyamukherjee/Documents/automaiton/final_document/e2e-run/runs/run-20261025-123936-feat-zd-48600/workspace/agents/hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-08/org.templates.md) · [original](https://github.com/arghya05/hobasa-agentic-sdlc/blob/main/org/org.templates.md) |

The full brief the agent was given, attempt by attempt: `brief_attempt<N>.md` in this folder.

## Output: what the agent produced

| # | Output | What it is | Open |
|---|---|---|---|
| 1 | `feat.stories` | Epics, stories and tasks with numbered AC, frame links, assumptions and open items (latest revision) | [Markdown](https://github.com/arghya05/hobasa-requirement-agent/blob/main/outputs/FEAT-ZD-48600/feat.stories.md) · [HTML](https://htmlpreview.github.io/?https://raw.githubusercontent.com/arghya05/hobasa-requirement-agent/main/docs/FEAT-ZD-48600/REQ-08_feat-stories.html) · [PDF](https://github.com/arghya05/hobasa-requirement-agent/blob/main/docs/FEAT-ZD-48600/REQ-08_feat-stories.pdf) |

## Checks and approval

| Attempt | Session | Problems found by the checks | Unsupported statements (judge) | Judge scores |
|---|---|---|---|---|
| 1 | new | 1 | — | — |
| 2 | continued | 0 | 0 | {'correct': 5, 'complete': 4, 'grounded': 5, 'useful': 5} |

Improvements the independent judge suggests (non-blocking):

- The Mermaid diagram in section 2 leaves out the STORY-01 → STORY-08 and STORY-05 → STORY-08 edges, but the dependency table lists both for STORY-08 ("STORY-01, 02, 03, 05, 06, 07"). The diagram should match the table.
- NFR-9 (feed schedule unchanged: daily 02:00 Asia/Kolkata) is traced to STORY-01 in its PRD trace and in section 7, but no STORY-01 acceptance criterion or task covers it. Either add a short criterion saying the schedule and configuration are not changed, or say plainly that NFR-9 has no testable criterion.
- AC-08.4 lists outcomes the end-to-end harness must assert: the invalid row appears in reject_reasons as 'paid_date', and rows of the vendor with no paid history get the class risk-unknown. TRD T-17 only lists these cases as feed contents, not as assertions. The criteria follow from AC-3, AC-17 and IF-2.5, but the trace column should cite IF-2.5 and F-4 as well as T-17.
- The revision note on line 11 describes the structured-result claims, not the stories. Gate reviewers don't need it in the deliverable; move it to the structured result or drop it.
- The workbook outcome is 'User Stories in NEW state'. The file states NEW for every story, but nothing records creating or syncing the stories on the DevOps board. Add an open item saying who moves these stories onto the board, or confirm that the file is the system of record.
- STORY-06's actor and purpose are agent judgement (SA-7), and it reuses US-1 as its PRD story. Consider asking the PM in SQ-1 or SQ-4 whether a technical enabler story (no 'As a') is the better form here.

## How the agent worked

- **Approach:** Attempt 2 fixes the G3 refusal. One claim quoted story labels I assigned in this step (for example "STORY-06"). The check read their digits as numbers, and they do not appear in feat.trd or feat.prd. In this result, every claim describes a story by its function (the paid_date story, the serialiser story and so on). Every remaining digit in a claim comes from the source it cites. I rewrote feat.stories in full. Its story content is the attempt-1 version after the verifier's corrections. It now also has a note saying the EP/FT/STORY/TK/AC-nn.n/SA/SQ labels are assigned in this step, a revision note for attempt 2, and one fix in the carried open-items map: OQ-B6 now also lists the delay-history story. The method is the same as attempt 1. I read the four contracted inputs, the existing unit test files and predict.py. I split the work into one epic, five features (one per lane), eight NEW stories and their tasks, following the story template. Each story gives frame links to the prototype's text frames, dependencies, a specification depth, and [Pending] markers on criteria that rest on open questions. No priority is set. A verifier pass on attempt 1 found 11 issues, and all of them are fixed in this content.
- **Tools used:** Skill (requirement-steps), Read, Glob, Grep, Write, Edit, Agent (verifier)
- **Helper subagents:** Agent
- **Connector calls:** none

## Human evaluation

| Role | By | Decision | Scores (correct, complete, grounded, useful) | Comment or reason |
|---|---|---|---|---|
| PM | sim.pm | approve | — | automated checks and the independent judge passed |

## Files in this folder (audit trail)

- `brief_attempt<N>.md`: the exact brief the agent received
- `result_attempt<N>.json`: the agent's structured answer (approach, tools, claims with their sources, open questions)
- `checks_attempt<N>.json`: what the automated guardrail checks found
- `judge_attempt<N>.json`, `judge_brief_attempt<N>.md`: the independent judge
- `outputs/`: the outputs as approved
