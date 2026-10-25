# REQ-03 Product Fitment Validation (Requirement agent)

**Item:** FEAT-ZD-48600 · **status:** done
**Trigger:** Previous Grouping  
**Action:** Checks the entry against capability, roadmap and strategy and returns a verdict with its evidence : Yes or No  
**Outcome expected:** Fitment verdict with evidence. Notification to PM and Leadership to decide
Yes or No ³

## Inputs (what the agent was given)

| Item | Prepared input (this repository) | Read from (producer in GitHub) | Commit | Produced by |
|---|---|---|---|---|
| feat.classification | hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-03/feat.classification.md | hobasa-requirement-agent/outputs/FEAT-ZD-48600/feat.classification.md | 59cf8bf | REQ-02 |
| org.strategy_capability | hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-03/org.strategy_capability.md | hobasa-agentic-sdlc/org/org.strategy_capability.md | bf63f34 | source |
| org.roadmap | hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-03/org.roadmap.md | hobasa-agentic-sdlc/org/org.roadmap.md | bf63f34 | source |

Full brief per attempt: `brief_attempt<N>.md` (trigger event, owner answers, tool view, refusal reasons).

## Outputs (what the agent produced)

| Item | GitHub file |
|---|---|
| feat.fitment | hobasa-requirement-agent/outputs/FEAT-ZD-48600/feat.fitment.md |

## How the agent worked

- Approach: Attempt 2 fixes both G1 refusals, and I rewrote feat.fitment in full.

(1) I removed the claim that the entry supports 'help finance teams pay on time and avoid late-payment penalties'. Section 4 now quotes the strategy and the ticket side by side. It states that no input links them, and it passes that judgement to PM and Leadership as OQ-F1. The verdict now rests on the roadmap evidence only.

(2) I renamed the 'Risk to the existing capability' row to 'Risk note recorded in the source file'. It now gives only the recorded content.

I applied the same rule to other inferred wording:
- I removed the 'same user, same object' equation between the roadmap and the ticket. The R-AP-12 link now cites the PM-approved REQ-01 record (feat.prebacklog).
- I removed 'open (unpaid)' and 'delivers what the roadmap asks for'.
- I limited the capability check to quoted facts, including the architecture's 'Keep every existing signature; add new functions'.

Inputs read: feat.classification, org.strategy_capability, org.roadmap. Background: journey:feat.intake and journey:feat.prebacklog, read via context_get in attempt 1, and requirements/ZD-48600.md.
- Tools used: Skill:requirement-steps, Read, mcp__hobasa-context__context_list, mcp__hobasa-context__context_get, mcp__hobasa-context__memory_search, Write
- Helper subagents: none
- Connector calls: none

## Attempts (checks before any person saw the output)

| Attempt | Session | Checks failed | Judge unsupported | Judge scores |
|---|---|---|---|---|
| 1 | new | 2 | 2 | {'correct': 5, 'complete': 4, 'grounded': 5, 'useful': 4} |
| 2 | resumed | 0 | 0 | {'correct': 5, 'complete': 4, 'grounded': 5, 'useful': 4} |

Details: `result_attempt<N>.json` (claims with sources), `checks_attempt<N>.json`, `judge_attempt<N>.json`.

## Human evaluation

| Role | By | Decision | Scores | Comment or reason |
|---|---|---|---|---|
| PM | sim.pm | approve | — | automated checks and the independent judge passed |
| Leadership | sim.leadership | approve | — | automated checks and the independent judge passed |
