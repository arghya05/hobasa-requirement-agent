# REQ-07 Technical Requirement Document (Requirement agent)

**Item:** FEAT-ZD-48600 · **status:** blocked
**Trigger:** Prototype Approved  
**Action:** drafts the TRD from the PRD, prototype and current architecture  
**Outcome expected:** Technical Requirement Document

## Inputs (what the agent was given)

| Item | Prepared input (this repository) | Read from (producer in GitHub) | Commit | Produced by |
|---|---|---|---|---|
| feat.prd | hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-07/feat.prd.md | hobasa-requirement-agent/outputs/FEAT-ZD-48600/feat.prd.md | 908b58d | REQ-05 |
| feat.prototype | hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-07/feat.prototype.md | hobasa-requirement-agent/outputs/FEAT-ZD-48600/feat.prototype.md | 8fce3b3 | REQ-06 |
| org.architecture | hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-07/org.architecture.md | hobasa-agentic-sdlc/features/FEAT-ZD-48600/org-overrides/org.architecture.md | 9fbbfba | source |

Full brief per attempt: `brief_attempt<N>.md` (trigger event, owner answers, tool view, refusal reasons).

## Outputs (what the agent produced)

| Item | GitHub file |
|---|---|
| feat.trd | — |

## How the agent worked

- Approach: This attempt fixes the one G3 refusal. The claim that cited org.templates included the section numbers "2" and "7" ("sections 2 to 7"), and those numbers do not appear in org.templates.

What I changed:
- I removed the section numbers from that claim. It now names the template sections and says the TRD has a section for each.
- I made the same fix in the TRD's validation-check row that cites org.templates. It now names the TRD's sections instead of numbering them.

In this session I re-read every source the TRD cites:
- org/org.templates.md
- the three inputs: org.architecture, feat.prd, and the feat.prototype dataset section
- requirements/ZD-48600.md
- memory/MEMORY.md

I then rewrote feat.trd in full. Apart from that row, the content is the same as the previous attempt.

I checked every number in the claims against its cited sources:
- 3.9 and 22: org.architecture
- 30 and 10: feat.prd
- 75 and 1250.00: feat.prototype
- 2 dp, 02:00 and T2: requirements/ZD-48600.md
- decision and lesson IDs: memory
- Tools used: Read, Write
- Helper subagents: Agent
- Connector calls: none

## Attempts (checks before any person saw the output)

| Attempt | Session | Checks failed | Judge unsupported | Judge scores |
|---|---|---|---|---|
| 1 | new | 13 | — | — |
| 2 | resumed | 19 | — | — |
| 3 | resumed | 1 | — | — |
| 1 | resumed | 6 | 6 | {'correct': 4, 'complete': 3, 'grounded': 3, 'useful': 4} |
| 2 | resumed | 1 | — | — |
| 3 | resumed | 6 | 6 | {'correct': 4, 'complete': 4, 'grounded': 4, 'useful': 3} |

Details: `result_attempt<N>.json` (claims with sources), `checks_attempt<N>.json`, `judge_attempt<N>.json`.
