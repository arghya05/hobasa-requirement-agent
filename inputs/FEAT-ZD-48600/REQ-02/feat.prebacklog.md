<!-- input feat.prebacklog for REQ-02: from hobasa-requirement-agent/outputs/FEAT-ZD-48600/feat.prebacklog.md at commit ee6f26c, produced by REQ-01 -->
# feat.prebacklog: FEAT-ZD-48600

The Pre Backlog requirement entry for this item, linked to the roadmap item and the trace ID. Step REQ-01 (Requirement Intake), attempt 3. Status: **entry created for review** (record:brief).

## Entry

| Field | Value | Source |
|---|---|---|
| Trace ID | FEAT-ZD-48600 | record:brief |
| Title | Overdue invoices with vendor late-payment risk, so AP managers can chase the riskiest first | record:intake |
| Intake item | `feat.intake.md` (Zendesk ticket ZD-48600, sample, synthetic) | record:intake |
| Source link (GitHub) | `hobasa-agentic-sdlc/requirements/ZD-48600.md` | record:intake |
| Channel | Customer Feedback | record:intake |
| Received | 2026-10-24 | record:intake |
| Requested by (persona) | AP managers | record:intake |
| Linked roadmap item | **R-AP-12**: give AP managers earlier visibility of overdue payables (Q4 2026 roadmap, AP module) | org.roadmap |
| Roadmap owner | PM | org.roadmap |
| Other roadmap item checked | R-AP-14, aging export for finance close. Not linked, because the ticket asks for no export. | org.roadmap; record:intake |
| Entry status | Created for review | record:brief |

## Affected components and planned work

| Repository | Change in this item | Source |
|---|---|---|
| ap_pipeline | Optional `paid_date` column in the vendor feed. A row with an invalid `paid_date` is rejected with reason `'paid_date'`. New `delays_by_vendor(records)`. | record:intake |
| ap_forecast | New `vendor_risk(history)`, a rule on the predicted delay. Optional `risk` argument on `build_explanation_request`. | record:intake; org.model_dependency_map |
| ap_aging | New `overdue_with_risk(invoices, as_of, risk_by_vendor)`. | record:intake |
| ap_portal | New `renderOverdueRisk(rows)` table. | record:intake |

**Planned work:** the item matches R-AP-12 on the Q4 2026 roadmap (org.roadmap).

**Data flow:** feed -> delays -> risk -> overdue list -> portal table. The ticket asks for this whole flow to be proven end to end (record:intake).

## Checks

### Decision log (conflict check)

| Decision | Bearing on this item | Result | Source |
|---|---|---|---|
| D-2026-031: aging buckets use calendar days after due date | `overdue_with_risk` in ap_aging selects unpaid invoices "more than 30 days past due". Counting those days as calendar days after the due date keeps it aligned with this decision (assumption A-1). The decision covers aging buckets only, so it does not settle the day unit for `delay_days` in ap_pipeline (see OQ-6). | Consistent, provided A-1 holds | org.decision_log; record:intake |
| D-2026-044: monetary amounts use Decimal, never float | `overdue_with_risk` returns `amount`, and the portal shows it to two decimals. The amount should stay Decimal and be formatted only for display. | Consistent, provided Decimal is kept | org.decision_log; record:memory; record:intake |
| D-2026-050: paid invoices are excluded from aging | `overdue_with_risk` returns unpaid invoices only. `delays_by_vendor` uses paid records only to build payment-delay history, not the aging list. | Consistent | org.decision_log; record:intake |

No conflict with a prior decision was found.

### Connector inventory

- The inventory states: "No source-system connector is affected by the ap_aging library" (org.connector_inventory).
- This item also changes the **vendor feed** in ap_pipeline by adding the optional `paid_date` column (record:intake). The inventory does not say which source-system connector supplies the vendor feed, so that impact cannot be assessed here (see OQ-1).

### Regulatory sources

- The source list states: "No regulatory source applies to this change" (org.regulatory_sources).
- So no section or page is captured, and no rule is affected or new.

### Model dependency map

- ap_forecast uses provider acme-llm, model acme-text-2, for the payment-delay explanation (config `src/ap_forecast/models.json`) (org.model_dependency_map).
- **Affected feature: the payment-delay explanation.** When `risk` is given, the prompt that `build_explanation_request` sends to acme-text-2 ends with `' Risk level: <risk>.'` (record:intake; org.model_dependency_map). The provider and model do not change.
- `vendor_risk` uses no LLM. It is a rule on the predicted delay (org.model_dependency_map).

### Shared memory (lessons to carry forward)

- L-007: test the boundary day explicitly for any day-count rule (record:memory). This item has three thresholds: more than 30 days past due in ap_aging, and a predicted delay > 30 and > 10 in ap_forecast (record:intake).
- L-011: keep Decimal arithmetic and never convert amounts to float (record:memory).

### Pre Backlog sheet and DevOps board

- The workbook action asks for a check against the Pre Backlog sheet and the DevOps board (record:brief). Neither was in this step's context, so the duplicate check could not be done (see OQ-2).

## Assumptions (non-blocking)

| # | Assumption | Basis |
|---|---|---|
| A-1 | Days past due in `overdue_with_risk` are calendar days from `due_date` to `as_of`. An invoice exactly 30 days past due is **not** included, because the ticket says "more than 30". | org.decision_log (D-2026-031, aging buckets); record:intake; record:memory (L-007) |
| A-2 | `delay_days` may be zero or negative when an invoice was paid on or before its due date, and such values are kept in the history. | record:intake (the formula has no floor) |
| A-3 | The risk thresholds are strict: a predicted delay of exactly 30 is `'medium'`, and exactly 10 is `'low'`. | record:intake ("> 30", "> 10") |
| A-4 | The `id` tie-break in the overdue list is ascending. | record:intake ("sorted by days descending then id") |
| A-5 | The row class `risk-RISK` takes the row's risk value, including `risk-unknown` for a vendor not in `risk_by_vendor`. | record:intake |
| A-6 | Amounts stay Decimal and are formatted to two decimals only in the portal. | org.decision_log (D-2026-044); record:memory (L-011) |

## Open questions (non-blocking)

- **OQ-1:** Which source-system connector supplies the ap_pipeline vendor feed, and does it already provide a paid date? org.connector_inventory speaks only to the ap_aging library.
- **OQ-2:** The Pre Backlog sheet and the DevOps board were not in this step's context. Is there a duplicate or related open item for this request?
- **OQ-3:** What should `vendor_risk` return for a vendor with an empty payment history? The ticket does not say.
- **OQ-4:** Please confirm assumptions A-1 to A-4: the 30-day boundary, negative delays, strict risk thresholds and the ascending `id` tie-break.
- **OQ-5:** Which rounding rule applies to amounts shown to two decimals in the portal? Should vendor names be HTML-escaped in `renderOverdueRisk`?
- **OQ-6:** Should `delay_days` in `delays_by_vendor` count calendar days? The ticket says only "in days", and D-2026-031 covers aging buckets, not payment-delay history.

## Notification

The workbook outcome for this step includes "Notification sent" (record:brief). This agent has not sent a notification itself. This entry is the content of that notification.
