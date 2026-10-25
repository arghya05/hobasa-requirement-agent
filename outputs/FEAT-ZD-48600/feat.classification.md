# feat.classification: FEAT-ZD-48600

**Grouping result, status: Draft for sampled human evaluation.** This step classifies the entry and checks for duplicates. It does not approve, prioritize or create a ticket in an external system. The record below is the content of the new ticket. (record:brief)

## 1. Classification

| Field | Value | Source |
|---|---|---|
| Trace ID | FEAT-ZD-48600 | record:brief |
| Pre Backlog entry | Overdue invoices ranked by vendor late-payment risk (feed -> delays -> risk -> overdue list -> portal table), linked to roadmap item R-AP-12 | feat.prebacklog |
| **Category** | **New Feature** | file:hobasa-agentic-sdlc/requirements/ZD-48600.md; feat.prebacklog |
| Why this category | The source file records the item type as New Feature. The ticket asks for new functions (`delays_by_vendor`, `vendor_risk`, `overdue_with_risk`, `renderOverdueRisk`), a new optional feed column and a new optional argument. The architecture says to keep every existing signature and add new functions. feat.prebacklog records that no regulatory source applies. | file:hobasa-agentic-sdlc/requirements/ZD-48600.md; feat.intake; org.architecture; feat.prebacklog |
| **Qualifier** | **Not Technical Only** | feat.intake |
| Why this qualifier | The business need is that AP managers can see which overdue invoices belong to vendors that usually pay late. CR-6 adds a new portal table (`renderOverdueRisk`) for this. RETRO-2026-19 uses "Technical only" for an item with "no customer-visible change". This entry does not fit that description. | feat.intake; file:hobasa-agentic-sdlc/requirements/RETRO-2026-19.md |
| Route named in the source file | full | file:hobasa-agentic-sdlc/requirements/ZD-48600.md |
| Risk note in the source file | No finance posting, authentication, tenancy or payment execution; tier T2; the risk label is advisory only | file:hobasa-agentic-sdlc/requirements/ZD-48600.md; feat.prebacklog |

## 2. Technical sub-categories (one per change request)

The trigger asks for a technical sub-category under each entry. Each change request below is a technical sub-item of this New Feature, grouped by the area the ticket names and routed by the feature routing map.

| CR | Technical sub-category (area named in the ticket) | Repository | Owner agent (routing map) | Source |
|---|---|---|---|---|
| CR-1 | Data engineering: optional `paid_date` feed column; invalid `paid_date` rejects the row with reason `'paid_date'` | ap_pipeline | Data Engineering Coding Agent | feat.intake; org.routing_map |
| CR-2 | Data engineering: new `delays_by_vendor(records)` | ap_pipeline | Data Engineering Coding Agent | feat.intake; org.routing_map |
| CR-3 | AI / data science: new `vendor_risk(history)`, a rule on the predicted delay (no LLM) | ap_forecast | Data Science Agent | feat.intake; feat.prebacklog; org.routing_map |
| CR-4 | AI / data science: optional `risk` argument on `build_explanation_request` (prompt of the payment-delay explanation; depends on acme-llm, acme-text-2) | ap_forecast | Data Science Agent | feat.intake; feat.prebacklog; org.routing_map |
| CR-5 | Backend: new `overdue_with_risk(invoices, as_of, risk_by_vendor)` | ap_aging | Backend Coding Agent | feat.intake; org.routing_map |
| CR-6 | Frontend: new `renderOverdueRisk(rows)` portal table | ap_portal | Frontend Coding Agent | feat.intake; org.routing_map |
| CR-7 | Integration and end-to-end tests across all four repositories | all four | Testing Agent | feat.intake; org.routing_map |

Impacted repositories: ap_pipeline, ap_forecast, ap_aging, ap_portal

Basis: the feature routing map routes ap_pipeline, ap_forecast, ap_aging and ap_portal to their coding agents and routes the end-to-end tests across all four to the Testing Agent (org.routing_map). The ticket asks for a change in each of them (feat.intake). The organisation-level routing map lists only ap_aging (file:hobasa-agentic-sdlc/org/org.routing_map.md). The feature override covers the other three.

## 3. Duplicate check and merge decision

**No duplicates found. Nothing was merged.** I compared the entry with every requirement file in `hobasa-agentic-sdlc/requirements/`. The Pre Backlog sheet and the DevOps board were not in this step's context (OQ-1 in feat.prebacklog stays open).

| Item | Category in its file | Overlap with FEAT-ZD-48600 | Decision | Source |
|---|---|---|---|---|
| ZD-48211 | New Feature (ap_aging) | Same overdue rule as CR-5: open invoices more than 30 days past due; paid invoices never count as overdue. It asks for an overdue flag and an overdue summary (count and total amount), not a list with vendor risk. | **Related, not a duplicate. Keep separate.** | file:hobasa-agentic-sdlc/requirements/ZD-48211.md; feat.intake |
| ZD-48501 | New Feature (ap_aging, ap_portal) | Same overdue rule and the same `as_of` parameter as CR-5. It adds `overdue_summary` and a `badge-overdue` portal badge, which are a different function and a different view. | **Related, not a duplicate. Keep separate.** | file:hobasa-agentic-sdlc/requirements/ZD-48501.md; feat.intake |
| ZD-48470 | Enhancement (ap_pipeline) | Both change the vendor feed in ap_pipeline and both add a row rejection. ZD-48470 adds `currency` (feed v2, reason `'InvalidCurrency'`). This entry adds `paid_date` (feed v3, reason `'paid_date'`). | **Related, not a duplicate. Sequencing question (OQ-B).** | file:hobasa-agentic-sdlc/requirements/ZD-48470.md; file:hobasa-agentic-sdlc/requirements/ZD-48600.md; feat.intake |
| PROV-ACME-2026-11 | Technical (ap_forecast) | Replaces model acme-text-2 with acme-text-3 and adds a `system` field to the explanation requests. CR-4 changes the prompt built by `build_explanation_request`. | **Related, not a duplicate. Sequencing question (OQ-C).** | file:hobasa-agentic-sdlc/requirements/PROV-ACME-2026-11.md; feat.intake |
| ZD-48377 | Defect (ap_aging) | An invoice exactly 30 days past due lands in the 31-60 bucket instead of 1-30. CR-5 uses the same boundary (more than 30 days past due), and L-007 says to test that boundary explicitly. The defect file does not say whether the fault is in the day count or in the bucket mapping. | **Related, not a duplicate. Sequencing question (OQ-D).** | file:hobasa-agentic-sdlc/requirements/ZD-48377.md; feat.intake; record:memory |
| ZD-48455 | Enhancement (ap_portal) | A different view (the aging summary table, class `row-overdue`). Only the naming is similar. | Not a duplicate. | file:hobasa-agentic-sdlc/requirements/ZD-48455.md; feat.prebacklog |
| FIN-OPS-2026-07 | Configuration (ap_forecast) | Changes only the explanation `max_tokens`. The ZD-48600 ticket does not mention `max_tokens`. | Not a duplicate. | file:hobasa-agentic-sdlc/requirements/FIN-OPS-2026-07.md; feat.intake |
| REG-LPR-2026-4.2 | Compliance (ap_aging) | A "Late" rule for invoices more than 60 days past due. Different threshold and purpose. | Not a duplicate. | file:hobasa-agentic-sdlc/requirements/REG-LPR-2026-4.2.md |
| ZD-48480, ZD-48510, RETRO-2026-19 | Documentation, New Feature (vendor payment execution), Technical | They share only the repository (ap_aging). They do not ask for any of the functions or views in this entry. | Not duplicates. | file:hobasa-agentic-sdlc/requirements/ZD-48480.md; file:hobasa-agentic-sdlc/requirements/ZD-48510.md; file:hobasa-agentic-sdlc/requirements/RETRO-2026-19.md; feat.intake |

## 4. Decision log check

No classification here conflicts with D-2026-031, D-2026-044 or D-2026-050. feat.prebacklog recorded these as no conflict, and this step adds no new rule. (feat.prebacklog; record:memory)

## 5. Assumptions (non-blocking)

- **G-1:** "Technical Only" is a qualifier for items with no customer-visible change, as RETRO-2026-19 uses it. Because this entry adds a portal table for AP managers (CR-6), the qualifier is not applied to the entry as a whole. Each change request is still listed as a technical sub-category in section 2. (record:brief; file:hobasa-agentic-sdlc/requirements/RETRO-2026-19.md; feat.intake)
- **G-2:** Related items are kept as separate entries, not merged, because each asks for a different function or view. (feat.intake; the requirement files cited in section 3)

## 6. Open questions (non-blocking)

- **OQ-A:** The overdue rule (unpaid, more than 30 days past due) appears in ZD-48211, ZD-48501 and CR-5. Should ap_aging have one shared overdue rule used by all three, and in which order should they be built? (Carries OQ-7 from feat.prebacklog forward.)
- **OQ-B:** ZD-48470 brings feed v2 (`currency`). This entry is recorded as feed v3 (`paid_date`), but the v3 column list in the ZD-48600 source file does not include `currency`. Should ZD-48470 land first, and should feed v3 include `currency`?
- **OQ-C:** PROV-ACME-2026-11 replaces acme-text-2 and adds a `system` field to the explanation requests, and CR-4 changes the prompt of the same request. Which change lands first, and should CR-4 be built against the new request shape?
- **OQ-D:** Should the ZD-48377 boundary fix land before CR-5, so that the exactly-30-days boundary in `overdue_with_risk` is tested against corrected boundary handling?
- **OQ-E:** Are any of the change requests besides CR-6 visible to users? For example, does the explanation prompt in CR-4 reach users? The inputs do not say. This does not change the entry-level qualifier.
- **OQ-F:** The Pre Backlog sheet and the DevOps board were not available, so the duplicate check covered only the repository's requirement files (same as OQ-1 in feat.prebacklog).
