<!-- input feat.classification for REQ-03: from hobasa-requirement-agent/outputs/FEAT-ZD-48600/feat.classification.md at commit b25a15f, produced by REQ-02 -->
# feat.classification: FEAT-ZD-48600

Grouping result for the Pre Backlog entry FEAT-ZD-48600 (ZD-48600). It gives the category, the Technical sub-category and qualifier, and the duplicate check against the other open intake items. This is a draft for automated checks and sampled human evaluation.

## Classification

| Field | Value | Source |
|---|---|---|
| Trace ID | FEAT-ZD-48600 | record:brief; feat.prebacklog |
| Intake ID / channel | ZD-48600 / Customer Feedback, received 2026-10-24 | feat.intake |
| Title | Show which overdue invoices belong to vendors that usually pay late | feat.prebacklog |
| **Category** | **New Feature** (reasoning under "Why New Feature") | feat.intake; org.architecture |
| Technical sub-category | Present in every repository part (see "Technical sub-category per change request") | feat.intake; org.architecture |
| **Qualifier** | **Not Technical Only.** The item adds a capability that customers can see: an overdue-risk table in the portal for AP managers. | feat.intake |
| Linked roadmap item | R-AP-12 "give AP managers earlier visibility of overdue payables" | feat.prebacklog |
| Risk tier (from the source item) | T2. "No finance posting, authentication, tenancy or payment execution in this change". The risk label is advisory only. | feat.intake |
| Duplicates merged | None. No open item asks for the same change (see "Duplicate check"). | file:hobasa-agentic-sdlc/requirements/ZD-48211.md; file:hobasa-agentic-sdlc/requirements/ZD-48501.md; file:hobasa-agentic-sdlc/requirements/ZD-48455.md |
| Related items grouped with this entry | ZD-48501 and ZD-48211 share the overdue rule. ZD-48470 and PROV-ACME-2026-11 change the same code (the vendor feed; `build_explanation_request`). None of them is a duplicate. | see "Duplicate check" |

Impacted repositories: ap_pipeline, ap_forecast, ap_aging, ap_portal

(Routing: org.routing_map; file:hobasa-agentic-sdlc/org/org.routing_map.md. See "Routing by repository".)

## Why New Feature

- The ticket asks for new behaviour that does not exist today. It adds four new functions: `delays_by_vendor`, `vendor_risk`, `overdue_with_risk` and `renderOverdueRisk`. It also adds a new optional feed column, `paid_date`. (feat.intake, CR-1 to CR-6)
- The existing functions are kept. The architecture says "Keep every existing signature; add new functions". The current functions (`aging_buckets`, `days_past_due`, `bucket_for`, `predict_delay_days`, `renderAgingSummary`, and others) are not redefined. Two changes touch existing behaviour, and both are additive:
  - `build_explanation_request` gains an optional argument (CR-4).
  - Feed ingestion accepts the new optional `paid_date` column. This also adds a new reject reason, `'paid_date'`, and a new field, `Invoice.paid_date` (CR-1).

  (org.architecture; feat.intake)
- It is not a Defect: no current behaviour is reported as wrong. It is not Documentation only or Configuration only, because code behaviour changes in four repositories. It is not Compliance: "No regulatory source applies to this change". (feat.intake; feat.prebacklog)

## Technical sub-category per change request

The workbook trigger for this step says "Technical has to be a sub-category under each and should be classified as Technical Only" where it applies (record:brief). Each part below has technical work. In this agent's judgement, none of the parts is Technical Only on its own, because each one feeds the customer-visible table. The "Category of the part" column is also this agent's judgement; the sources do not state it. The flow is "feed -> delays -> risk -> overdue list -> portal table" (CR-7).

| CR | Repository / area | Category of the part | Technical sub-category (what is technical in it) | Source |
|---|---|---|---|---|
| CR-1 | ap_pipeline / Data engineering | New Feature (data input) | Feed schema change: vendor feed v3 adds optional `paid_date` (ISO date, empty when unpaid), mapped to `Invoice.paid_date`. An invalid value rejects the row with reason `'paid_date'`. The schedule is unchanged. The connector impact is still open (feat.prebacklog Q-2). | feat.intake; feat.prebacklog |
| CR-2 | ap_pipeline / Data engineering | New Feature | New transform `delays_by_vendor(records)`; day-count rule `delay_days = (paid_date - due_date)` | feat.intake |
| CR-3 | ap_forecast / AI / data science | New Feature | New rule `vendor_risk(history)` on `predict_delay_days`, with thresholds `> 30` and `> 10`. It "uses no LLM; it is a rule on the predicted delay". | feat.intake; feat.prebacklog |
| CR-4 | ap_forecast / AI / data science | Enhancement within the feature | LLM prompt change: `build_explanation_request` gains an optional `risk` argument. Today ap_forecast uses provider acme-llm, model acme-text-2, for the payment-delay explanation. This ticket itself asks for no change of provider or model. A separate open item, PROV-ACME-2026-11, replaces acme-text-2 with acme-text-3 because acme-text-2 is deprecated on 2026-12-01. CR-4 must therefore not assume a particular model. See OQ-3. | feat.intake; feat.prebacklog; file:hobasa-agentic-sdlc/requirements/PROV-ACME-2026-11.md |
| CR-5 | ap_aging / Backend | New Feature | New function `overdue_with_risk(invoices, as_of, risk_by_vendor)`; rule "more than 30 days past due"; amounts stay Decimal (D-2026-044, L-011); paid invoices are excluded (D-2026-050) | feat.intake; feat.prebacklog; record:memory |
| CR-6 | ap_portal / Frontend | New Feature (customer-visible) | New renderer `renderOverdueRisk(rows)`; amounts arrive as strings with two decimals in the JSON between services | feat.intake; org.architecture |
| CR-7 | Cross-repository | Testing scope | End-to-end proof across all four repositories. The feature routing map sends it to the Testing Agent. | feat.intake; org.routing_map |

## Duplicate check

I compared ZD-48600 with every other intake item in `hobasa-agentic-sdlc/requirements/`. All of them are open. None asks for the same change, so nothing was merged. Four items share a rule or touch the same code; they are grouped here so that later steps can keep them consistent and plan their order. The rest are not grouped.

| Item | Status | Relation | Grouping decision | Source |
|---|---|---|---|---|
| ZD-48501 | open | Uses the same overdue rule in ap_aging: "unpaid invoices more than 30 days past due". It asks for a different function, `overdue_summary` (count and total), and a different portal output, `badge-overdue`. | Grouped as related (shared rule), not a duplicate. Both should share one overdue definition. See OQ-1. | file:hobasa-agentic-sdlc/requirements/ZD-48501.md |
| ZD-48211 | open | Uses the same overdue definition: "more than 30 days past its due date"; "Paid invoices should never count as overdue". It asks for an overdue flag and an overdue summary in the aging output. | Grouped as related (shared rule), not a duplicate. Share the definition. See OQ-1. | file:hobasa-agentic-sdlc/requirements/ZD-48211.md |
| ZD-48470 | open | Also changes the vendor feed in ap_pipeline: feed v2 adds `currency`. CR-1 refers to feed v3 adding `paid_date`. | Grouped as related (shared code), not a duplicate. Whether v3 must wait for v2 is unconfirmed. See OQ-2. | file:hobasa-agentic-sdlc/requirements/ZD-48470.md; feat.intake |
| PROV-ACME-2026-11 | open | Also changes `build_explanation_request` in ap_forecast: acme-text-2 (deprecated on 2026-12-01) is replaced by acme-text-3, and a `system` field is added. CR-4 adds a `risk` argument to the same function. | Grouped as related (shared code), not a duplicate. Both change the same function, so the changes need ordering. See OQ-3. | file:hobasa-agentic-sdlc/requirements/PROV-ACME-2026-11.md; feat.intake |
| ZD-48455 | open | Also an ap_portal table change with "overdue risk" wording. It uses a different table (the aging table) and a different class: `row-overdue`, where this item uses `overdue-risk` and `risk-RISK`. | Not grouped and not a duplicate. The wording overlaps, so the class names must stay distinct. | file:hobasa-agentic-sdlc/requirements/ZD-48455.md; feat.intake |
| FIN-OPS-2026-07 | open | Configuration change only: reduce the ap_forecast explanation max_tokens from 300 to 200, with "No code or behaviour change other than this configuration value". ZD-48600 does not touch max_tokens. | Not grouped and not a duplicate: it shares no rule or code with this item. A side observation for the PM, outside this item: FIN-OPS-2026-07 conflicts with PROV-ACME-2026-11, which says "Our explanation requests must keep max_tokens at 300" (see OQ-5). | file:hobasa-agentic-sdlc/requirements/FIN-OPS-2026-07.md; file:hobasa-agentic-sdlc/requirements/PROV-ACME-2026-11.md |
| ZD-48510 | open | Similar goal (acting on overdue invoices), but it asks for payment execution. Payment execution is out of scope for this item ("No ... payment execution in this change"). | Not grouped | file:hobasa-agentic-sdlc/requirements/ZD-48510.md; feat.intake |
| ZD-48377, RETRO-2026-19, ZD-48480, REG-LPR-2026-4.2 | open | All four are about ap_aging: a boundary defect in the aging buckets, error messages for missing fields, README bucket definitions, and the Late rule at more than 60 days. None asks for vendor risk or an overdue-risk list. | Not grouped; not duplicates | file:hobasa-agentic-sdlc/requirements/ZD-48377.md; file:hobasa-agentic-sdlc/requirements/RETRO-2026-19.md; file:hobasa-agentic-sdlc/requirements/ZD-48480.md; file:hobasa-agentic-sdlc/requirements/REG-LPR-2026-4.2.md |

Limitation: the Pre Backlog sheet and the DevOps board are not in this step's context. This duplicate check covers only the intake files in `requirements/`. This carries forward feat.prebacklog Q-1.

## New ticket (workbook action)

| Field | Value | Source |
|---|---|---|
| Ticket | FEAT-ZD-48600, category New Feature, qualifier Not Technical Only, linked to roadmap item R-AP-12 | record:brief; feat.prebacklog |
| Created in an external tracker | No. The connector approved for this step is api:github, which allows GET requests on the Hobasa repositories. It cannot create tickets. This file is the ticket record. The spine pushes it after evaluation. | record:brief |

## Routing by repository

| Repository | Owner agent (feature routing map) | Source |
|---|---|---|
| ap_pipeline | Data Engineering Coding Agent | org.routing_map |
| ap_forecast | Data Science Agent | org.routing_map |
| ap_aging | Backend Coding Agent; owner: backend developer | org.routing_map; file:hobasa-agentic-sdlc/org/org.routing_map.md |
| ap_portal | Frontend Coding Agent | org.routing_map |
| Integration and end-to-end (CR-7) | Testing Agent | org.routing_map |

The organisation-level routing map (`org/org.routing_map.md`) lists only ap_aging. The routing for the other three repositories comes from the feature override. See OQ-4.

## Open questions (non-blocking)

- **OQ-1**: ZD-48501, ZD-48211 and CR-5 all use "unpaid and more than 30 days past due". Should one shared overdue definition in ap_aging serve all three, so they cannot drift apart? Or should they stay separate? This needs a PM decision. Nothing was merged.
- **OQ-2**: CR-1 names feed v3, and ZD-48470 brings feed v2 (`currency`). Must ZD-48470 be delivered first, or is v3 independent of v2?
- **OQ-3**: PROV-ACME-2026-11 and CR-4 both change `build_explanation_request`. PROV-ACME-2026-11 moves it from acme-text-2 to acme-text-3 and adds a `system` field; CR-4 adds `risk`. Which order should they land in? Should the CR-4 tests run against whichever model is current at delivery?
- **OQ-4**: Should `org/org.routing_map.md` be updated with the owners of ap_pipeline, ap_forecast and ap_portal? Today they exist only in the feature override.
- **OQ-5** (outside this item, for the PM): PROV-ACME-2026-11 keeps max_tokens at 300, while FIN-OPS-2026-07 lowers it from 300 to 200. Which one applies?
- Carried forward from feat.prebacklog:
  - Q-1: duplicate check against the Pre Backlog sheet and DevOps board.
  - Q-2: is feed v3 a registered connector?
  - Q-3: notification channel.
  - Q-4: how to handle an unpaid row that has a `paid_date`.
  - Q-5: HTML escaping in `renderOverdueRisk`.
