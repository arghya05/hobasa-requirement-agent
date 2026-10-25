# REQ-02 · Grouping

**Agent:** Requirement · **Item:** FEAT-ZD-48600 · **Status:** ✅ done · approved in an earlier run, reused
**Approved by:** PM: approve by sim.pm

**What this step does:** New Ticket gets created

**Expected outcome:** Entry classified by category, duplicates merged

**Started by:** Previous Requirement Intake
Technical has to be a sub-category under each and should be classified as Technical Only
This could go as a qualifier during requirement approval or as applicable ²

## Input: what the agent received

| # | Input | What it is | Produced by | Open |
|---|---|---|---|---|
| 1 | `feat.prebacklog` | Pre-backlog entry linked to roadmap and trace ID | Requirement agent · REQ-01 | [input copy](https://github.com/arghya05/hobasa-requirement-agent/blob/main/inputs/FEAT-ZD-48600/REQ-02/feat.prebacklog.md) · [original](https://github.com/arghya05/hobasa-requirement-agent/blob/main/outputs/FEAT-ZD-48600/feat.prebacklog.md) · [HTML](https://htmlpreview.github.io/?https://raw.githubusercontent.com/arghya05/hobasa-requirement-agent/main/docs/FEAT-ZD-48600/REQ-01_feat-prebacklog.html) · [PDF](https://github.com/arghya05/hobasa-requirement-agent/blob/main/docs/FEAT-ZD-48600/REQ-01_feat-prebacklog.pdf) |
| 2 | `feat.intake` | Original intake item with source link | Requirement agent · REQ-01 | [input copy](https://github.com/arghya05/hobasa-requirement-agent/blob/main/inputs/FEAT-ZD-48600/REQ-02/feat.intake.md) · [original](https://github.com/arghya05/hobasa-requirement-agent/blob/main/outputs/FEAT-ZD-48600/feat.intake.md) · [HTML](https://htmlpreview.github.io/?https://raw.githubusercontent.com/arghya05/hobasa-requirement-agent/main/docs/FEAT-ZD-48600/REQ-01_feat-intake.html) · [PDF](https://github.com/arghya05/hobasa-requirement-agent/blob/main/docs/FEAT-ZD-48600/REQ-01_feat-intake.pdf) |
| 3 | `org.routing_map` | Component-to-owner routing for defects | organisation source | [input copy](https://github.com/arghya05/hobasa-requirement-agent/blob/main/inputs/FEAT-ZD-48600/REQ-02/org.routing_map.md) · [original](https://github.com/arghya05/hobasa-agentic-sdlc/blob/main/features/FEAT-ZD-48600/org-overrides/org.routing_map.md) |
| 4 | `org.architecture` | Platform architecture, contracts and tenancy rules | organisation source | [input copy](https://github.com/arghya05/hobasa-requirement-agent/blob/main/inputs/FEAT-ZD-48600/REQ-02/org.architecture.md) · [original](https://github.com/arghya05/hobasa-agentic-sdlc/blob/main/features/FEAT-ZD-48600/org-overrides/org.architecture.md) |

The full brief the agent was given, attempt by attempt: `brief_attempt<N>.md` in this folder.

## Output: what the agent produced

| # | Output | What it is | Open |
|---|---|---|---|
| 1 | `feat.classification` | Category, qualifier and merged duplicates | [Markdown](https://github.com/arghya05/hobasa-requirement-agent/blob/main/outputs/FEAT-ZD-48600/feat.classification.md) · [HTML](https://htmlpreview.github.io/?https://raw.githubusercontent.com/arghya05/hobasa-requirement-agent/main/docs/FEAT-ZD-48600/REQ-02_feat-classification.html) · [PDF](https://github.com/arghya05/hobasa-requirement-agent/blob/main/docs/FEAT-ZD-48600/REQ-02_feat-classification.pdf) |

## Checks and approval

| Attempt | Session | Problems found by the checks | Unsupported statements (judge) | Judge scores |
|---|---|---|---|---|
| 1 | continued | 1 | 1 | {'correct': 5, 'complete': 5, 'grounded': 4, 'useful': 5} |
| 2 | continued | 0 | 0 | {'correct': 5, 'complete': 5, 'grounded': 5, 'useful': 5} |
| 3 | continued | 2 | 2 | {'correct': 5, 'complete': 5, 'grounded': 4, 'useful': 5} |

## How the agent worked

- **Approach:** Attempt 3 fixes the G1 refusal. The CR-4 row said without qualification that provider acme-llm and model acme-text-2 do not change. That overstated feat.prebacklog, which says only that the ticket itself asks for no change of provider or model. It also conflicted with PROV-ACME-2026-11, which replaces acme-text-2 with acme-text-3 because of a deprecation on 2026-12-01. The row now states the current model, limits 'no change' to this ticket, and points to the PROV-ACME-2026-11 model swap. OQ-3 now asks about ordering and about which model the CR-4 tests run against. I checked the rest of the file for similar unscoped statements and found none. All cited requirement files were opened with Read in this session. The rest of the classification is unchanged: New Feature, Not Technical Only, a Technical sub-category for each CR, no duplicates merged, related items grouped, and the impacted repositories taken from the routing maps. I rewrote the file in full.
- **Tools used:** Skill:requirement-steps, Read, Glob, Grep, Write, Edit, Agent:verifier
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
