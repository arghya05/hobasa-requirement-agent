# feat.brd: FEAT-ZD-48600

Business Requirement Document for FEAT-ZD-48600 (ZD-48600, "Show which overdue invoices belong to vendors that usually pay late"). This is a draft for the REQ-04 gate.

Statements marked "agent judgement" are an agent's own assessment, and no input states them as fact. Where the judgement was made in an earlier step, the step is named. Assumptions are listed in section 10 and need confirmation at the gate.

| Field | Value | Source |
|---|---|---|
| Trace ID | FEAT-ZD-48600 | record:brief; feat.intake |
| Intake | ZD-48600, Zendesk ticket (sample, synthetic), channel Customer Feedback, received 2026-10-24 | feat.intake |
| Source link (GitHub) | `hobasa-agentic-sdlc/requirements/ZD-48600.md` | feat.intake; file:hobasa-agentic-sdlc/requirements/ZD-48600.md |
| Fitment | feat.fitment recommends "Yes", with reason code FIT-Y-ROADMAP and linked roadmap item R-AP-12. FIT-Y-ROADMAP is the REQ-03 agent's own code; no approved list of reason codes exists (FQ-5). The REQ-03 gate decisions were "PM: approve by sim.pm" and "Leadership: approve by sim.leadership"; gates in this run are SIMULATED. | feat.fitment; file:hobasa-agentic-sdlc/features/FEAT-ZD-48600/COMMUNICATION.md |
| Category / qualifier | New Feature / Not Technical Only, as classified by the REQ-02 agent (feat.classification) and carried in feat.fitment | feat.fitment; file:hobasa-requirement-agent/outputs/FEAT-ZD-48600/feat.classification.md |
| Risk tier (advisory) | T2. "The risk label is advisory only." | feat.fitment; feat.intake |
| Owner of this step | PM | record:brief |
| Gate for this document | Leadership | record:brief |
| Template | BRD template: problem, business outcome, users, scope, out of scope, business rules, success measures, approvals | org.templates |

## 1. Problem

| Statement | Source |
|---|---|
| "AP managers want to see which overdue invoices belong to vendors that usually pay late, so they can chase them first." | feat.intake (CR-0) |
| Today the AP module's capability is that the "ap_aging service computes aging buckets (current, 1-30, 31-60, 61-90, 90+) for open invoices". The capability statement mentions neither a vendor payment-delay history nor a vendor risk level. feat.fitment records that the entry adds both (`delays_by_vendor` in ap_pipeline, `vendor_risk` in ap_forecast). | org.strategy_capability; feat.fitment |
| The business meaning is still open. feat.fitment notes, as agent judgement, that in an AP context the vendor is the party being paid, so "vendors that usually pay late" and "chase them first" are ambiguous. It assumed that "the risk level helps AP managers decide which overdue payables to act on first". This BRD keeps that assumption (B-A1) and carries the question forward (OQ-B1). | feat.fitment (FQ-1) |

## 2. Business outcome

| Outcome | Source |
|---|---|
| AP managers see a table in the portal. It lists unpaid invoices more than 30 days past due, sorted by days descending then id, "each with a vendor risk level". Each row carries a risk class (`risk-high`, `risk-medium`, `risk-low` or `risk-unknown`). The visible columns are Invoice, Vendor, Days overdue and Amount. Whether the risk level is also shown as visible text is open (OQ-B9). | feat.fitment; feat.intake (CR-5, CR-6); file:hobasa-agentic-sdlc/requirements/ZD-48600.md |
| Roadmap link. feat.fitment gives R-AP-12, "give AP managers earlier visibility of overdue payables" (Q4 2026 roadmap, AP module), as the linked roadmap item. Its agent judgement is that the entry matches R-AP-12: both name AP managers as the users, and both are about seeing overdue items. | feat.fitment |
| Strategy link (agent judgement, recorded in feat.fitment). Showing overdue payables with a priority signal supports acting on them sooner, and so supports the strategy statement "help finance teams pay on time and avoid late-payment penalties". The sources do not say how the risk level should change the order in which invoices are paid (OQ-B1). | org.strategy_capability; feat.fitment |
| Product-promise link (agent judgement, recorded in feat.fitment). Explicit rules and a named reject reason support the promise "auditability and traceability are core product promises". The facts behind this judgement come from the sources: `vendor_risk` "uses no LLM; it is a rule on the predicted delay", and an invalid `paid_date` is rejected with the reason `'paid_date'`. | org.strategy_capability; feat.fitment; feat.intake; file:hobasa-agentic-sdlc/requirements/ZD-48600.md |

## 3. Users

| User | Need | Source |
|---|---|---|
| AP managers (the users named in the ticket) | See which overdue invoices belong to vendors that usually pay late, so they can chase them first. | feat.intake |
| Finance teams (agent judgement: they benefit indirectly, as the group named in the strategy) | The strategy is to "help finance teams pay on time and avoid late-payment penalties". | org.strategy_capability |

The inputs name no other user group.

## 4. Scope

The flow in scope is "feed -> delays -> risk -> overdue list -> portal table", across the repositories named on the source item: ap_pipeline, ap_forecast, ap_aging and ap_portal (feat.intake, Source table and CR-7). The architecture rule is "Keep every existing signature; add new functions" (feat.intake; file:hobasa-agentic-sdlc/requirements/ZD-48600.md). feat.classification records that the ticket adds four new functions (`delays_by_vendor`, `vendor_risk`, `overdue_with_risk`, `renderOverdueRisk`). It also records that "Two changes touch existing behaviour, and both are additive":

- `build_explanation_request` gains an optional argument (CR-4).
- Feed ingestion accepts the new optional `paid_date` column, which also adds a new reject reason, `'paid_date'`, and a new field, `Invoice.paid_date` (CR-1).

(file:hobasa-requirement-agent/outputs/FEAT-ZD-48600/feat.classification.md)

| ID | In scope (business view) | Repository / area | Change request | Source |
|---|---|---|---|---|
| S-1 | Capture when each paid invoice was paid. The vendor feed gains an optional `paid_date` column (ISO date, empty when unpaid), mapped to `Invoice.paid_date` (vendor feed v3). The schedule is unchanged. | ap_pipeline / Data engineering | CR-1 | feat.intake |
| S-2 | Build each vendor's payment-delay history. `delays_by_vendor(records)` returns `{vendor: [delay_days, ...]}` for paid records with a `paid_date`, in feed order. | ap_pipeline / Data engineering | CR-2 | feat.intake |
| S-3 | Give each vendor a risk level from its predicted delay: `vendor_risk(history)`. | ap_forecast / AI / data science | CR-3 | feat.intake |
| S-4 | `build_explanation_request` gains an optional `risk` argument. When it is given, the prompt ends with `' Risk level: <risk>.'`. | ap_forecast / AI / data science | CR-4 | feat.intake |
| S-5 | Produce the overdue list with risk: `overdue_with_risk(invoices, as_of, risk_by_vendor)`. | ap_aging / Backend | CR-5 | feat.intake |
| S-6 | Show the overdue-risk table in the portal: `renderOverdueRisk(rows)`. | ap_portal / Frontend | CR-6 | feat.intake |
| S-7 | Prove the whole flow end to end: feed -> delays -> risk -> overdue list -> portal table. | Cross-repository | CR-7 | feat.intake |

## 5. Out of scope

| ID | Out of scope | Source |
|---|---|---|
| OS-1 | Finance posting, authentication, tenancy and payment execution: "No finance posting, authentication, tenancy or payment execution in this change". | feat.intake; file:hobasa-agentic-sdlc/requirements/ZD-48600.md |
| OS-2 | Acting on the risk level automatically (agent judgement from "The risk label is advisory only."). | feat.intake |
| OS-3 | An aging export for finance close (roadmap item R-AP-14). No change request adds an export. | feat.fitment |
| OS-4 | Changing the LLM provider or model. The ticket asks for no change of provider or model. The model replacement is a separate open item, PROV-ACME-2026-11. | file:hobasa-requirement-agent/outputs/FEAT-ZD-48600/feat.prebacklog.md; feat.fitment |
| OS-5 | Using an LLM to set the risk level. `vendor_risk` "uses no LLM; it is a rule on the predicted delay". | file:hobasa-agentic-sdlc/requirements/ZD-48600.md |
| OS-6 | Changes to existing behaviour beyond the two additive changes named in section 4 (CR-1, CR-4): "Keep every existing signature; add new functions." | feat.intake; file:hobasa-requirement-agent/outputs/FEAT-ZD-48600/feat.classification.md |
| OS-7 | The work asked for in the related open items ZD-48501 and ZD-48211 (overdue summary, overdue flag, overdue badge). They share this item's overdue rule but were not merged with it. | feat.fitment; file:hobasa-requirement-agent/outputs/FEAT-ZD-48600/feat.classification.md |
| OS-8 | The regulatory "Late" rule (REG-LPR-2026-4.2, a payable "more than 60 days past its due date" that remains unpaid). This item's "overdue" is a different label. | feat.fitment |

## 6. Business rules

| ID | Rule | Source |
|---|---|---|
| BR-1 | `paid_date` is optional. It is an ISO date, and it is empty when the invoice is unpaid. | feat.intake (CR-1) |
| BR-2 | A feed row with an invalid `paid_date` is rejected with the reason `'paid_date'`. | feat.intake (CR-1) |
| BR-3 | A vendor's payment delay is `delay_days = (paid_date - due_date)` in days. It is computed only for paid records that have a `paid_date`, and the values are kept in feed order. | feat.intake (CR-2) |
| BR-4 | Vendor risk is `'high'` when `predict_delay_days(history) > 30`, `'medium'` when it is `> 10`, and `'low'` otherwise. | feat.intake (CR-3) |
| BR-5 | The risk thresholds are strict. A predicted delay of exactly 30 is `'medium'`, and exactly 10 is `'low'` (agent judgement, read directly from the `>` comparisons). | feat.intake (CR-3) |
| BR-6 | The vendor risk level is a rule on the predicted delay. It uses no LLM. | file:hobasa-agentic-sdlc/requirements/ZD-48600.md |
| BR-7 | An invoice is in the overdue list only when it is unpaid and more than 30 days past due. An invoice exactly 30 days past due is not listed. | feat.intake (CR-5); file:hobasa-requirement-agent/outputs/FEAT-ZD-48600/feat.prebacklog.md |
| BR-8 | Paid invoices are excluded. | org.decision_log (D-2026-050); feat.intake (CR-5) |
| BR-9 | Days past due are counted in calendar days after the due date. This BRD applies D-2026-031 to the overdue list; the ticket does not say how days are counted (assumption B-A2, OQ-B4). | org.decision_log (D-2026-031); feat.fitment (FQ-4) |
| BR-10 | Each overdue row carries `id`, `vendor`, `days`, `amount` and `risk`. Rows are sorted by days descending, then by id. | feat.intake (CR-5) |
| BR-11 | A vendor with no risk level in `risk_by_vendor` gets risk `'unknown'`. | feat.intake (CR-5) |
| BR-12 | Monetary amounts use Decimal, never float. The Invoice `amount` is Decimal, 2 dp. JSON between services carries amounts as strings with two decimals and dates as ISO strings. The `amount` in the overdue list is assumed to be the Invoice amount (B-A7). | org.decision_log (D-2026-044); record:memory (L-011); feat.intake; file:hobasa-agentic-sdlc/requirements/ZD-48600.md |
| BR-13 | The portal table is `<table class="overdue-risk">`, with one `<tr class="risk-RISK">` per row showing id, vendor, days and amount to two decimals. When there are no rows, the result is an empty string. | feat.intake (CR-6) |
| BR-14 | Row classes are `risk-high`, `risk-medium`, `risk-low` or `risk-unknown`. The columns are Invoice, Vendor, Days overdue and Amount (two decimals). | file:hobasa-agentic-sdlc/requirements/ZD-48600.md |
| BR-15 | When a `risk` argument is given to `build_explanation_request`, the prompt it builds ends with `' Risk level: <risk>.'`. | feat.intake (CR-4) |
| BR-16 | The risk label is advisory only. | feat.intake; file:hobasa-agentic-sdlc/requirements/ZD-48600.md |

## 7. Success measures

The inputs give no business KPI, for example a target for faster chasing or fewer late-payment penalties. This BRD therefore states delivery success measures that can be checked, and asks the owners for a business KPI (OQ-B3).

| ID | Success measure | Source |
|---|---|---|
| SM-1 | The whole flow is proven end to end: feed -> delays -> risk -> overdue list -> portal table. | feat.intake (CR-7) |
| SM-2 | Every day-count boundary is tested explicitly: an invoice exactly 30 days past due (not listed), and the strict risk thresholds at exactly 30 and exactly 10 (BR-5). | record:memory (L-007); file:hobasa-requirement-agent/outputs/FEAT-ZD-48600/feat.prebacklog.md; feat.intake |
| SM-3 | Amounts follow the stated representation at each point. The Invoice `amount` is Decimal (2 dp), and Decimal arithmetic is kept (never float). In the JSON between services, amounts travel as strings with two decimals. The ap_portal table (Node.js) shows the amount to two decimals. The inputs do not say how ap_portal handles the amount string internally; that is left to the PRD and TRD (OQ-B10). | org.decision_log (D-2026-044); record:memory (L-011); feat.intake (CR-6); file:hobasa-agentic-sdlc/requirements/ZD-48600.md |
| SM-4 | A row with an invalid `paid_date` is rejected with reason `'paid_date'`. | feat.intake (CR-1) |
| SM-5 | The architecture rule "Keep every existing signature; add new functions" is met. Existing behaviour changes only in the two additive ways recorded in feat.classification: the optional argument added to `build_explanation_request` (CR-4), and feed ingestion accepting the optional `paid_date` column with the new reject reason `'paid_date'` and the new field `Invoice.paid_date` (CR-1). Callers that do not pass `risk` are assumed to get today's prompt (B-A6). | feat.intake; file:hobasa-requirement-agent/outputs/FEAT-ZD-48600/feat.classification.md |
| SM-6 | Business KPI: not defined in the inputs (OQ-B3). | this file |

## 8. Approvals

| Role | What is asked | Status | Source |
|---|---|---|---|
| Leadership | Approve or reject this BRD (REQ-04 gate). | Pending | record:brief |

Open questions that need a business decision are listed in section 11, with the owners recorded by the step that raised them.

## 9. Business question set

The step action asks for the business question set. org.templates names the templates (BRD, PRD, TRD, story) but holds no separate business question set (OQ-B7). The questions below are therefore this agent's own set. They cover the BRD template sections and the checks this step must make. Each was checked against the inputs; no stakeholder was contacted in this step. BQ-3 has no answer in the inputs. Questions without an answer go to the owners as open questions.

| # | Question | Answer from the inputs | Source |
|---|---|---|---|
| BQ-1 | What business problem is being solved? | AP managers want to see which overdue invoices belong to vendors that usually pay late, so they can chase them first. | feat.intake |
| BQ-2 | Who are the users? | AP managers. Finance teams, the group named in the strategy, benefit indirectly (agent judgement). | feat.intake; org.strategy_capability |
| BQ-3 | What do "vendors that usually pay late" and "chase them first" mean in AP? | Not answered. Assumed: the risk level helps AP managers decide which overdue payables to act on first (B-A1). | feat.fitment (FQ-1) → OQ-B1 |
| BQ-4 | What is in scope and out of scope? | See sections 4 and 5. | feat.intake; feat.fitment |
| BQ-5 | Which roadmap item and strategy is it linked to? | Linked roadmap item R-AP-12, which feat.fitment judges the entry matches. The strategy statement is "help finance teams pay on time and avoid late-payment penalties" (the strategy fit is agent judgement in feat.fitment). | feat.fitment; org.strategy_capability |
| BQ-6 | What are the business rules? | See section 6. | feat.intake; org.decision_log |
| BQ-7 | How is success measured? | By delivery measures SM-1 to SM-5. There is no business KPI. | feat.intake → OQ-B3 |
| BQ-8 | Does any prior decision conflict? | No conflict (section 12). | org.decision_log |
| BQ-9 | Does a regulation apply? | "No regulatory source applies to this change." The regulatory "Late" label (more than 60 days) is a different term. As agent judgement, feat.fitment recommends keeping the two labels distinct (OQ-B2). | file:hobasa-requirement-agent/outputs/FEAT-ZD-48600/feat.prebacklog.md; feat.fitment (FQ-2) |
| BQ-10 | Is there money movement, posting or payment execution? | No: "No finance posting, authentication, tenancy or payment execution in this change." | feat.intake |
| BQ-11 | Who approves? | Leadership, at the REQ-04 gate. | record:brief |

## 10. Assumptions (non-blocking; please confirm at the gate)

| ID | Assumption | Source |
|---|---|---|
| B-A1 | The risk level helps AP managers decide which overdue payables to act on first. | feat.fitment (FQ-1) |
| B-A2 | "Days past due" (BR-7) and `delay_days` (BR-3) are calendar days, following D-2026-031. | org.decision_log; file:hobasa-requirement-agent/outputs/FEAT-ZD-48600/feat.prebacklog.md (A-1) |
| B-A3 | The `history` given to `vendor_risk` is one vendor's list of `delay_days` from `delays_by_vendor`. `risk_by_vendor` maps each vendor to its `vendor_risk` result. This follows the flow "feed -> delays -> risk -> overdue list". | file:hobasa-requirement-agent/outputs/FEAT-ZD-48600/feat.prebacklog.md (A-3); feat.intake |
| B-A4 | A negative `delay_days` (paid before the due date) is kept as computed. The rule sets no floor. | file:hobasa-requirement-agent/outputs/FEAT-ZD-48600/feat.prebacklog.md (A-4) |
| B-A5 | A record marked paid that has no `paid_date` is left out of the delay history. It is not rejected. | file:hobasa-requirement-agent/outputs/FEAT-ZD-48600/feat.prebacklog.md (A-5) |
| B-A6 | When no `risk` argument is given, `build_explanation_request` builds the same prompt as today. This is agent judgement from "Keep every existing signature"; CR-4 does not say it. | feat.intake |
| B-A7 | Inside ap_aging, `amount` in the overdue list is the Invoice `amount (Decimal, 2 dp)`. When the list passes from ap_aging to ap_portal as JSON, the amount travels as a string with two decimals. | file:hobasa-requirement-agent/outputs/FEAT-ZD-48600/feat.prebacklog.md (A-2) |

## 11. Open questions (non-blocking)

| ID | Question | Owner (as recorded by the raising step) | Source |
|---|---|---|---|
| OQ-B1 | Confirm the business meaning of "vendors that usually pay late" and "chase them first" (B-A1). If a different meaning is intended, the strategy fit should be checked again. | PM / Leadership | feat.fitment (FQ-1) |
| OQ-B2 | Keep "overdue" (more than 30 days) and the regulatory "Late" (more than 60 days, REG-LPR-2026-4.2) as distinct labels in the portal and in later documents. | Not recorded | feat.fitment (FQ-2) |
| OQ-B3 | What business KPI should measure success, for example time to chase or late-payment penalties avoided? The inputs give none. | Not recorded | this file |
| OQ-B4 | Confirm calendar days for "days past due" in `overdue_with_risk` (D-2026-031), with the 30-day boundary tested (L-007). | Not recorded | feat.fitment (FQ-4) |
| OQ-B5 | Should one shared overdue definition serve this item, ZD-48501 and ZD-48211? | PM | file:hobasa-requirement-agent/outputs/FEAT-ZD-48600/feat.classification.md (OQ-1) |
| OQ-B6 | How should an unpaid row that has a `paid_date` be handled: reject it, or ignore the date? | Not recorded | file:hobasa-requirement-agent/outputs/FEAT-ZD-48600/feat.prebacklog.md (Q-4) |
| OQ-B7 | The brief describes org.templates as holding the business question set, but its content holds only the templates. Should an approved question set be added? | Not recorded | org.templates; record:brief |
| OQ-B8 | Should `renderOverdueRisk` HTML-escape the vendor names and ids it renders? | Not recorded | file:hobasa-requirement-agent/outputs/FEAT-ZD-48600/feat.prebacklog.md (Q-5) |
| OQ-B9 | Should the portal show the risk level as visible text, or only as the row class `risk-RISK`? CR-6 lists the shown values as id, vendor, days and amount. | Not recorded | feat.intake (CR-6); file:hobasa-agentic-sdlc/requirements/ZD-48600.md |
| OQ-B10 | How should ap_portal (Node.js) format the two-decimal amount string it receives without converting it to a binary floating-point number (D-2026-044)? This is for the PRD and TRD. | Not recorded | org.decision_log; file:hobasa-agentic-sdlc/requirements/ZD-48600.md |
| — | Carried forward unchanged: feat.fitment FQ-3, FQ-5 and FQ-6. Also carried forward: the open questions that feat.fitment records as carried from feat.classification (OQ-1 to OQ-5) and feat.prebacklog (Q-1 to Q-5). | — | feat.fitment |

## 12. Validation check

### Decision log

| Decision | Result | Source |
|---|---|---|
| D-2026-031: aging buckets use calendar days after due date | No conflict. BR-9 applies it to the overdue list as an assumption (B-A2). | org.decision_log |
| D-2026-044: monetary amounts use Decimal, never float | Consistent (BR-12, SM-3). The handling inside ap_portal is open (OQ-B10). | org.decision_log |
| D-2026-050: paid invoices are excluded from aging | Consistent (BR-8). | org.decision_log |

No conflict with a recorded decision was found.

### Template and grounding

| Check | Result | Source |
|---|---|---|
| All BRD template sections are present (problem, business outcome, users, scope, out of scope, business rules, success measures, approvals) | Pass: sections 1 to 8. | org.templates |
| Every change request CR-0 to CR-7 is covered | Pass: CR-0 in section 1, and CR-1 to CR-7 in S-1 to S-7. | feat.intake |
| Every business rule cites its source | Pass: BR-1 to BR-16 each cite an input or a source file. No regulation applies, so no section and page are cited. | file:hobasa-requirement-agent/outputs/FEAT-ZD-48600/feat.prebacklog.md |
| The fitment verdict is consistent with this BRD | Pass: Yes, linked to R-AP-12. Out of scope matches the fitment evidence (R-AP-14, payment execution). | feat.fitment |
| A business KPI is present | Not met: the inputs have no KPI (OQ-B3). This does not block the BRD. | this file |

### Risks and dependencies (do not change scope)

| Item | Source |
|---|---|
| PROV-ACME-2026-11 replaces acme-text-2 (deprecated on 2026-12-01) with acme-text-3 and changes `build_explanation_request`, the same function as CR-4. The two changes need ordering. | feat.fitment |
| CR-1 needs feed v3, and ZD-48470 brings feed v2. | feat.fitment |
| ZD-48501 and ZD-48211 use the same "more than 30 days past due" rule. | feat.fitment |
