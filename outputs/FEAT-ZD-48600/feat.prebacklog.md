# feat.prebacklog: FEAT-ZD-48600

Pre Backlog requirement entry. This is a draft for review at the PM gate.

## Entry

| Field | Value | Source |
|---|---|---|
| Trace ID | FEAT-ZD-48600 | record:brief |
| Title | Show which overdue invoices belong to vendors that usually pay late | record:intake |
| Intake link | ZD-48600, `hobasa-agentic-sdlc/requirements/ZD-48600.md` (full text in feat.intake) | record:intake |
| Channel / received | Customer Feedback / 2026-10-24 | record:intake |
| Business need | AP managers want to see which overdue invoices belong to vendors that usually pay late, so they can chase them first. | record:intake |
| Linked roadmap item | **R-AP-12**: "give AP managers earlier visibility of overdue payables" (Q4 2026 roadmap, AP module, owner PM) | org.roadmap |
| Not linked | R-AP-14 (aging export for finance close). The ticket asks for no export. | org.roadmap; record:intake |
| Affected components | ap_pipeline (Data engineering), ap_forecast (AI / data science), ap_aging (Backend), ap_portal (Frontend), plus an end-to-end proof of the flow feed -> delays -> risk -> overdue list -> portal table | record:intake |
| Change requests | CR-0 to CR-7, listed in feat.intake | record:intake |
| Status | Draft entry for review; gate: PM | record:brief |

## Intake checks (workbook action)

| Check | Result | Source |
|---|---|---|
| Read the ticket | Done. The ticket text is captured word for word and split into CR-0 to CR-7 (feat.intake). | record:intake |
| Read the roadmap item and match it to planned work | Matches **R-AP-12**. The ticket asks to see overdue invoices so they can be chased first. This falls under "earlier visibility of overdue payables". | org.roadmap; record:intake |
| Check against the Pre Backlog sheet and DevOps board | Neither the Pre Backlog sheet nor the DevOps board is in this step's context. As a substitute, I read the related intake files in `requirements/`. That found no duplicate, but it did find three related open items (see "Related items"). See open question Q-1. | file:hobasa-agentic-sdlc/requirements/ZD-48211.md; file:hobasa-agentic-sdlc/requirements/ZD-48501.md; file:hobasa-agentic-sdlc/requirements/ZD-48455.md |
| Check the decision for conflict with prior decisions | No conflict found (see "Decision log check"). | org.decision_log; record:intake |
| Regulatory sources (section and page) | Not applicable: "No regulatory source applies to this change." No section or page is captured, and no rule is affected. | org.regulatory_sources |
| Connector inventory | The inventory states: "No source-system connector is affected by the ap_aging library." It does not mention the vendor feed that ap_pipeline ingests, and CR-1 changes that feed (new optional `paid_date` column, feed v3). The connector impact of CR-1 is therefore unconfirmed. See open question Q-2. | org.connector_inventory; record:intake; file:hobasa-agentic-sdlc/requirements/ZD-48600.md |
| Model dependency map | ap_forecast uses provider acme-llm, model acme-text-2 (config `src/ap_forecast/models.json`), for the payment-delay explanation. CR-4 changes the prompt sent to it (optional trailing `' Risk level: <risk>.'`); the ticket asks for no change of provider or model. `vendor_risk` (CR-3) "uses no LLM; it is a rule on the predicted delay". Affected feature: the payment-delay explanation. | org.model_dependency_map; record:intake |
| External patterns / market research | Not applicable. The trigger is a customer ticket (channel Customer Feedback), not a market research or competitive analysis change, so no external sources were gathered. | record:intake; record:brief |
| Notification | Not sent. The only connector approved for this step is api:github, which allows GET only. I filed a capability_request for a notification channel. It is pending approval. See open question Q-3. | mcp:hobasa-context; record:brief |

## Decision log check

| Decision / lesson | Relation to this item | Result | Source |
|---|---|---|---|
| D-2026-031: aging buckets use calendar days after due date | CR-5 "more than 30 days past due" and CR-2 `delay_days = (paid_date - due_date) in days`. Assumed to be calendar days (A-1). | Consistent | org.decision_log; record:intake |
| D-2026-044: monetary amounts use Decimal, never float | CR-5 returns `amount`; CR-6 shows amount to two decimals. The data model has `amount (Decimal, 2 dp)`, and JSON between services carries amounts as strings with two decimals. | Consistent, provided amounts stay Decimal or two-decimal strings and never pass through float (A-2) | org.decision_log; record:intake; file:hobasa-agentic-sdlc/requirements/ZD-48600.md |
| D-2026-050: paid invoices are excluded from aging | CR-5 covers only unpaid invoices. | Consistent | org.decision_log; record:intake |
| L-007: test the boundary day (exactly 30 days) explicitly for any day-count rule | CR-5 uses "more than 30 days", so an invoice exactly 30 days past due is not listed. CR-3 uses the strict thresholds `> 30` and `> 10`. Both boundaries need explicit tests. | Carry forward to testing | record:memory; record:intake |
| L-011: keep Decimal arithmetic; never convert amounts to float | Same as D-2026-044 for CR-5 and CR-6. | Carry forward to design | record:memory |

## Related items (open; not duplicates)

| Item | Overlap | Source |
|---|---|---|
| ZD-48501 (open) | `overdue_summary(invoices, as_of)` in ap_aging, for "unpaid invoices more than 30 days past due". This is the same overdue rule as CR-5, but it adds a different function and a portal badge (`badge-overdue`). | file:hobasa-agentic-sdlc/requirements/ZD-48501.md |
| ZD-48211 (open) | Flag every open invoice "more than 30 days past its due date" as overdue and add an overdue summary. "Paid invoices should never count as overdue." This is the same overdue definition. | file:hobasa-agentic-sdlc/requirements/ZD-48211.md |
| ZD-48455 (open) | ap_portal aging table: highlight rows as "overdue risk" with CSS class `row-overdue`. This uses similar wording but a different table and class from CR-6 (`overdue-risk`, `risk-RISK`). | file:hobasa-agentic-sdlc/requirements/ZD-48455.md |

## Assumptions (non-blocking; please confirm at the PM gate)

- **A-1**: "Days past due" in CR-5 and `delay_days` in CR-2 are calendar days, following D-2026-031. (org.decision_log)
- **A-2**: Inside ap_aging, `amount` in the CR-5 output is the Invoice `amount (Decimal, 2 dp)`. When the overdue list passes from ap_aging to ap_portal as JSON, the amount travels as a string with two decimals, as the architecture states for all JSON between services. ap_portal (CR-6) then shows it to two decimals. At no point is it converted to float (D-2026-044, L-011). (org.decision_log; record:memory; record:intake; file:hobasa-agentic-sdlc/requirements/ZD-48600.md)
- **A-3**: The `history` passed to `vendor_risk` (CR-3) is one vendor's list of `delay_days` from `delays_by_vendor` (CR-2). `risk_by_vendor` (CR-5) maps each vendor to that vendor's `vendor_risk` result. This follows the stated flow "feed -> delays -> risk -> overdue list". (record:intake)
- **A-4**: A negative `delay_days` (paid before the due date) is kept as computed. The ticket defines `delay_days = (paid_date - due_date)` and sets no floor. (record:intake)
- **A-5**: A record marked paid that has no `paid_date` is left out of `delays_by_vendor`. It is not rejected, because the ticket covers only "paid records with a paid_date". (record:intake)
- **A-6**: The risk label is advisory only. No finance posting or payment execution is in scope. (file:hobasa-agentic-sdlc/requirements/ZD-48600.md)

## Open questions (non-blocking)

- **Q-1**: The Pre Backlog sheet and DevOps board were not available to this step. The duplicate check covered only the related `requirements/` intake files. Can the PM confirm that no existing board item covers this? Should this item share one overdue definition with ZD-48501 and ZD-48211, or be merged with them?
- **Q-2**: Is the vendor feed (feed v3, new `paid_date` column) a registered source-system connector? If so, the connector inventory needs an entry and a version update. The current inventory speaks only about the ap_aging library.
- **Q-3**: A notification channel is pending approval through capability_request. Until it is approved, who notifies the PM of this entry?
- **Q-4**: How should a row that is unpaid but has a `paid_date` be handled: reject it, or ignore the date? The ticket defines rejection only for an invalid `paid_date`.
- **Q-5**: Should `renderOverdueRisk` (CR-6) HTML-escape the vendor names and ids it renders? The ticket does not say.
