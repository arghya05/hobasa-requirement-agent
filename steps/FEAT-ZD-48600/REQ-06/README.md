# REQ-06 Prototype ⁷ (Requirement agent)

**Item:** FEAT-ZD-48600 · **status:** done
**Trigger:** PRD Reviewed  
**Action:** builds the prototype prompt applying the design system, screen inventory, states and synthetic data rules, then checks the output against the PRD  
**Outcome expected:** Low Fidelity Wireframes

## Inputs (what the agent was given)

| Item | Prepared input (this repository) | Read from (producer in GitHub) | Commit | Produced by |
|---|---|---|---|---|
| feat.prd | hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-06/feat.prd.md | hobasa-requirement-agent/outputs/FEAT-ZD-48600/feat.prd.md | 908b58d | REQ-05 |
| org.design_library | hobasa-requirement-agent/inputs/FEAT-ZD-48600/REQ-06/org.design_library.md | hobasa-agentic-sdlc/features/FEAT-ZD-48600/org-overrides/org.design_library.md | 9fbbfba | source |

Full brief per attempt: `brief_attempt<N>.md` (trigger event, owner answers, tool view, refusal reasons).

## Outputs (what the agent produced)

| Item | GitHub file |
|---|---|
| feat.prototype | hobasa-requirement-agent/outputs/FEAT-ZD-48600/feat.prototype.md |

## How the agent worked

- Approach: Attempt 4 fixes both G1 refusals in feat.prototype. I re-read both contracted inputs and the current output first. The complete feat.prototype file is on disk; I applied the fixes to it as targeted edits rather than writing the file again.

(1) SD-1 row: the "Why" cell said "No secrets or personal data in outputs (G8)" and cited record:brief. Neither the step brief nor any input mentions G8 or such a rule. The cell now reads "Keeps real vendor and contact data out of a design artefact (agent judgement)", and the source is "agent judgement".

(2) Synthetic data attribution: the section 6 intro now says that the workbook action in the brief names "synthetic data rules" but that neither the brief nor any input defines them. That is the only fact the brief supports. SD-1 to SD-6 are stated as agent judgement and raised as PQ-P5. The prompt-basis row "Synthetic data only" now says the same.

A grep confirms that no G-gate ID remains in the output. Each remaining record:brief citation matches text in the brief:
- trigger, owner, gate, outcome and inputs
- "Connectors approved for you: api:github"
- the workbook action wording

The design content is unchanged from attempt 3.
- Tools used: Read, Edit, Grep
- Helper subagents: Agent
- Connector calls: none

## Attempts (checks before any person saw the output)

| Attempt | Session | Checks failed | Judge unsupported | Judge scores |
|---|---|---|---|---|
| 1 | new | 1 | — | — |
| 2 | resumed | 1 | — | — |
| 3 | resumed | 2 | 2 | {'correct': 5, 'complete': 4, 'grounded': 4, 'useful': 4} |
| 1 | resumed | 0 | 0 | {'correct': 5, 'complete': 4, 'grounded': 5, 'useful': 4} |

Details: `result_attempt<N>.json` (claims with sources), `checks_attempt<N>.json`, `judge_attempt<N>.json`.

## Human evaluation

| Role | By | Decision | Scores | Comment or reason |
|---|---|---|---|---|
| UX lead | sim.ux_lead | approve | — | automated checks and the independent judge passed |
