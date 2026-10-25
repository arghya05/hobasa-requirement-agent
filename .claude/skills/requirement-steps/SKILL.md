---
name: requirement-steps
description: Procedures, inputs, outputs and gates for every Requirement agent step in the Hobasa agentic SDLC. Use when running any REQ-01, REQ-02, REQ-03, REQ-04, REQ-05, REQ-06… step.
---

# Requirement agent steps

## REQ-01 Requirement Intake

- Trigger: Whenever new item gets added
Email/Ticket
All Internal Review Meeting Transcript
Transcript would be fed to agent automatically post the meeting
When there are dynamics in the market research and Competitive analysis
Decision recorded after a leadership meeting
Vendor changelog entry or connector failure
Update on a named regulatory source
Provider release note or deprecation notice, Provider email notification
Item added to the backlog, related work enters planning from the retro meeting
- Action: Reads the new roadmap item and checks it against the Pre Backlog sheet and the DevOps board ⁸
Reads the ticket
Reads the transcript and extracts the change requests raised
4 gateways to requirement in-take for internal meetings and leadership discussions

1. Define meeting cadence and give the meeting names to the agent

2. Add the agent to any out of sequence meetings before meeting happens, add qualifier only PM can do this

3. Meeting transcript to be given to the agent if out of sequence meeting was missed to invite agent

4.PM will have the permission to add requirement to backlog manually ⁴
Gathers external patterns and cites each source
Reads the decision and checks for conflict with a prior decision
Matches the change against the connector inventory and assesses which features are affected
Captures the change with its section and page and assesses which rules are affected or they are new rules
Matches the change against the model dependency map and assesses affected features
Matches the item to the affected component and to planned work
- Outcome: Entry created in the Pre Backlog requirement sheet, linked to the roadmap item and Notification sent
Agent has created an entry for review in the Pre Backlog requirement sheet / Sent a notification / --> Triggered another agent
Entry created in the Pre Backlog requirement sheet, linked to the roadmap item and Notification sent
Entry created in the Pre Backlog requirement sheet, linked to the roadmap item and Notification sent
Entry created in the Pre Backlog requirement sheet, linked to the roadmap item and Notification sent
Entry created in the Pre Backlog requirement sheet, linked to the roadmap item and Notification sent
Entry created in the Pre Backlog requirement sheet, linked to the roadmap item and Notification sent
Entry created in the Pre Backlog requirement sheet, linked to the roadmap item and Notification sent
Entry created in the Pre Backlog requirement sheet, linked to the roadmap item and Notification sent
Entry created in the Pre Backlog requirement sheet, linked to the roadmap item and Notification sent
- Reads: org.roadmap, org.regulatory_sources, org.connector_inventory, org.model_dependency_map, org.decision_log
- Writes: feat.intake, feat.prebacklog
- Gate: PM

## REQ-02 Grouping

- Trigger: Previous Requirement Intake
Technical has to be a sub-category under each and should be classified as Technical Only
This could go as a qualifier during requirement approval or as applicable ²
- Action: New Ticket gets created
- Outcome: Entry classified by category, duplicates merged
- Reads: feat.prebacklog, feat.intake
- Writes: feat.classification
- Gate: automated checks; sampled human evaluation

## REQ-03 Product Fitment Validation

- Trigger: Previous Grouping
- Action: Checks the entry against capability, roadmap and strategy and returns a verdict with its evidence : Yes or No
- Outcome: Fitment verdict with evidence. Notification to PM and Leadership to decide
Yes or No ³
- Reads: feat.classification, org.strategy_capability, org.roadmap
- Writes: feat.fitment
- Gate: PM, Leadership

## REQ-04 BRD Preparation

- Trigger: Previous Step
- Action: asks the business question set, drafts the BRD against the template and runs the validation check
- Outcome: Business Requirement Document
- Reads: feat.fitment, feat.intake, org.templates, org.strategy_capability, org.decision_log
- Writes: feat.brd
- Gate: Leadership

## REQ-05 Product Requirement Preparation

- Trigger: BRD approved
- Action: drafts the PRD carrying approved BRD decisions forward and runs the validation check
- Outcome: Product Requirement Document
- Reads: feat.brd, org.templates
- Writes: feat.prd
- Gate: PM

## REQ-06 Prototype ⁷

- Trigger: PRD Reviewed
- Action: builds the prototype prompt applying the design system, screen inventory, states and synthetic data rules, then checks the output against the PRD
- Outcome: Low Fidelity Wireframes
- Reads: feat.prd, org.design_library
- Writes: feat.prototype
- Gate: UX lead

## REQ-07 Technical Requirement Document

- Trigger: Prototype Approved
- Action: drafts the TRD from the PRD, prototype and current architecture
- Outcome: Technical Requirement Document
- Reads: feat.prd, feat.prototype, org.architecture
- Writes: feat.trd
- Gate: Architect

## REQ-08 User Story Preparation

- Trigger: Prototype approved ⁵
- Action: decomposes into epic, feature, story and task with numbered acceptance criteria, dependencies and specification depth
- Outcome: User Stories in NEW state

Document all the assumptions, and if there are any unresolved open items ⁶
- Reads: feat.prd, feat.prototype, feat.trd, org.templates
- Writes: feat.stories
- Gate: PM

## CMP-P01 Regulatory impact analysis (proposed)

- Trigger: Regulatory change entry from REQ-01
- Action: Map the changed section and page to the Rule Engine rule catalogue; classify each rule as changed, new or retired; cite the source
- Outcome: Rule impact list with citations
- Reads: feat.intake, org.regulatory_sources, org.rule_catalogue
- Writes: feat.rule_impact
- Gate: Compliance SME

## CMP-P02 Rule specification and ground truth (proposed)

- Trigger: Impact list approved
- Action: Write each rule as a machine-readable specification (conditions, thresholds, jurisdiction, effective date) with SME-approved worked examples
- Outcome: Rule specification and protected test examples
- Reads: feat.rule_impact
- Writes: feat.rule_spec
- Gate: Compliance SME

## Templates

BRD template: problem, business outcome, users, scope, out of scope, business rules, success measures, approvals. PRD template: summary, user stories, numbered acceptance criteria (EARS: When <trigger>, the system shall <response>), non-functional requirements, open questions. TRD template: components affected, interfaces/contracts, data, security and tenancy, testing approach, risks. Story template: ID, title, As a/I want/So that, acceptance criteria in Gherkin (Given/When/Then), assumptions, open items.

