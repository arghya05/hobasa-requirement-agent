# feat.prebacklog: FEAT-ZD-48600

**Pre Backlog entry, status: Draft for PM review.** This step does not approve or prioritize anything.

## 1. Entry

| Field | Value | Source |
|---|---|---|
| Trace ID | FEAT-ZD-48600 | record:brief |
| Title | Overdue invoices ranked by vendor late-payment risk (feed -> delays -> risk -> overdue list -> portal table) | record:intake |
| Intake | Zendesk ticket ZD-48600 (sample, synthetic), Customer Feedback, received 2026-10-24 | record:intake |
| Source link | `hobasa-agentic-sdlc/requirements/ZD-48600.md` (full intake in feat.intake) | record:intake; file:hobasa-agentic-sdlc/requirements/ZD-48600.md |
| Business need | AP managers want to see which overdue invoices belong to vendors that usually pay late, so they can chase them first. | record:intake |
| Linked roadmap item | **R-AP-12**, "give AP managers earlier visibility of overdue payables" (Q4 2026 roadmap, AP module, owner PM) | org.roadmap |
| Not linked | R-AP-14, "aging export for finance close". The ticket asks for no export. | org.roadmap; record:intake |
| Affected components | ap_pipeline (CR-1, CR-2), ap_forecast (CR-3, CR-4), ap_aging (CR-5), ap_portal (CR-6), plus an end-to-end proof across all four (CR-7) | record:intake |
| Routing named in the source file | ap_pipeline -> Data Engineering Coding Agent; ap_forecast -> Data Science Agent; ap_aging -> Backend Coding Agent; ap_portal -> Frontend Coding Agent; integration and end-to-end tests across all four -> Testing Agent | file:hobasa-agentic-sdlc/requirements/ZD-48600.md |
| Item type stated in the source file | New Feature | file:hobasa-agentic-sdlc/requirements/ZD-48600.md |
| Risk note in the source file | No finance posting, authentication, tenancy or payment execution; tier T2; the risk label is advisory only | file:hobasa-agentic-sdlc/requirements/ZD-48600.md |
| Owner | PM | org.roadmap |

## 2. Intake checks

| Check (workbook action) | Result | Source |
|---|---|---|
| Read the roadmap item and match it to planned work | The item matches R-AP-12. The ticket's goal (seeing overdue invoices so they can be chased first) falls under "earlier visibility of overdue payables". | org.roadmap; record:intake |
| Check against the Pre Backlog sheet and the DevOps board | **Not possible.** Neither the sheet nor the board was in this step's context. As a substitute I read the related requirement files in the repository. No duplicate was found, but there are three related open items (section 3). | record:brief; file:hobasa-agentic-sdlc/requirements/ZD-48211.md; file:hobasa-agentic-sdlc/requirements/ZD-48455.md; file:hobasa-agentic-sdlc/requirements/ZD-48501.md |
| Check the decision for conflict with prior decisions | No conflict found (section 4). | org.decision_log; record:memory |
| Match the change against the connector inventory | **ap_aging (CR-5):** the inventory states that no source-system connector is affected by the ap_aging library. **ap_pipeline, ap_forecast, ap_portal (CR-1 to CR-4, CR-6):** the inventory says nothing about these repositories, so this step cannot confirm whether any connector is affected. CR-1 changes the vendor feed (a new optional `paid_date` column). The source file records this as vendor feed v3, with the daily 02:00 Asia/Kolkata schedule unchanged. Whether that counts as a connector change is open (OQ-3). | org.connector_inventory; record:intake; file:hobasa-agentic-sdlc/requirements/ZD-48600.md |
| Capture regulatory section and page, and the rules affected | Not applicable. No regulatory source applies to this change, so there is no section or page to cite and no rule is changed or added. | org.regulatory_sources |
| Match the change against the model dependency map | ap_forecast uses provider acme-llm, model acme-text-2 (config `src/ap_forecast/models.json`), for the payment-delay explanation. CR-4 changes the prompt of the explanation request, so the feature depends on this model. `vendor_risk` (CR-3) uses no LLM; it is a rule on the predicted delay. The ticket does not mention any change of provider or model. | org.model_dependency_map; record:intake |
| Gather external patterns and cite each source | Not applicable. This is a customer ticket and no market or competitive input was part of the trigger. | record:intake |
| Transcript / meeting gateways | Not applicable. The channel is Customer Feedback (a ticket), not a meeting transcript. | record:intake |

## 3. Related open requirements (possible overlap)

These are not duplicates, but should be considered together when the entry is grouped.

| File | Received / status / repositories | Overlap with this entry | Source |
|---|---|---|---|
| `requirements/ZD-48211.md` | 2026-10-20; open; ap_aging | Asks to flag every open invoice more than 30 days past its due date as overdue, and to add an overdue summary (number of overdue invoices and their total amount). Paid invoices never count as overdue. CR-5 in this entry uses the same overdue rule. | file:hobasa-agentic-sdlc/requirements/ZD-48211.md |
| `requirements/ZD-48501.md` | 2026-10-24; open; ap_aging, ap_portal | Adds `overdue_summary(invoices, as_of)` returning `{'count': int, 'total': Decimal}` for unpaid invoices more than 30 days past due, plus a `badge-overdue` portal badge. Same overdue rule and the same `as_of` parameter style as CR-5; different function and view. | file:hobasa-agentic-sdlc/requirements/ZD-48501.md |
| `requirements/ZD-48455.md` | 2026-10-22; open; ap_portal | Highlights the 61-90 and 'Over 90 days' aging rows as overdue risk (CSS class `row-overdue`) and adds a total row. The name is similar to this entry's `overdue-risk` table and `risk-*` row classes, but it is a different view (the aging summary table). | file:hobasa-agentic-sdlc/requirements/ZD-48455.md |

Comparison against this entry: record:intake

## 4. Decision log and lessons check

| Item | Bearing on this entry | Conflict? | Source |
|---|---|---|---|
| D-2026-031: aging buckets use calendar days after due date | Applies to CR-5 "days past due". I assume the overdue count also uses calendar days (A-1). The decision covers aging buckets only, so it does not settle the day unit for `delay_days` in CR-2 (OQ-2). | No | org.decision_log; record:intake |
| D-2026-044: monetary amounts use Decimal, never float | CR-5 `amount` must stay Decimal. Per the source file, JSON between services carries amounts as strings with two decimals; CR-6 shows them to two decimals. | No | org.decision_log; record:intake; file:hobasa-agentic-sdlc/requirements/ZD-48600.md |
| D-2026-050: paid invoices are excluded from aging | CR-5 covers unpaid invoices only, which is consistent. CR-2 uses paid records only for delay history, not for aging. | No | org.decision_log; record:intake |
| L-007: test the boundary day (exactly 30 days) explicitly | Boundaries to test: exactly 30 days past due (CR-5, `> 30`), and predicted delay of exactly 30 and exactly 10 (CR-3, `> 30` / `> 10`). | n/a | record:memory; record:intake |
| L-011: keep Decimal arithmetic; never convert amounts to float | Applies to amounts carried through CR-5 and CR-7. | n/a | record:memory |

## 5. Assumptions (non-blocking)

- **A-1:** "days past due" in CR-5 means calendar days after the due date, in line with D-2026-031. (org.decision_log)
- **A-2:** `delay_days` in CR-2 can be zero or negative when a vendor paid on or before the due date. Such values are kept in feed order. (record:intake; see OQ-2)
- **A-3:** `risk_by_vendor` (CR-5) is built from `vendor_risk` (CR-3) applied to each vendor's `delays_by_vendor` history (CR-2). This follows from the flow named in CR-7. (record:intake)
- **A-4:** The `RISK` placeholder in `<tr class="risk-RISK">` (CR-6) is the risk value of the row: high, medium, low or unknown. The source file names the classes `risk-high`, `risk-medium`, `risk-low` and `risk-unknown`. (record:intake; file:hobasa-agentic-sdlc/requirements/ZD-48600.md)

## 6. Open questions (non-blocking)

- **OQ-1:** The Pre Backlog sheet and the DevOps board were not available, so the duplicate check covered only the repository's requirement files. PM: please confirm there is no existing entry for this need.
- **OQ-2:** Is the day unit for `delay_days` (CR-2) calendar days, and should early payments (zero or negative delay) be included? D-2026-031 covers aging buckets only.
- **OQ-3:** The connector inventory covers only ap_aging. Is any source-system connector affected by the ap_pipeline vendor-feed change (the new `paid_date` column, CR-1), or by the ap_forecast or ap_portal changes? Should the feed change be recorded in the connector inventory?
- **OQ-4:** How should a row be handled if `paid` and `paid_date` disagree (for example, paid with an empty `paid_date`, or unpaid with a date)? The ticket defines only the invalid-date rejection.
- **OQ-5:** What should `vendor_risk` return for a vendor with an empty history? This depends on how `predict_delay_days` behaves today, which this step did not read.
- **OQ-6:** Should vendor names and ids be HTML-escaped in `renderOverdueRisk` (CR-6)? The ticket does not say.
- **OQ-7:** Should this entry be grouped with, or sequenced after, the related open items ZD-48211 and ZD-48501, which share the same overdue rule (unpaid, more than 30 days past due)?

## 7. Notification

This step sent no notification. This entry is the notification content for the PM gate on FEAT-ZD-48600. Sending it is left to the workflow after evaluation. (record:brief)
