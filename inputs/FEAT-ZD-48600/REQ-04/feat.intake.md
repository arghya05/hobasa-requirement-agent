<!-- input feat.intake for REQ-04: from hobasa-requirement-agent/outputs/FEAT-ZD-48600/feat.intake.md at commit fd588b3, produced by REQ-01 -->
# feat.intake: FEAT-ZD-48600

| Field | Value | Source |
|---|---|---|
| Trace ID | FEAT-ZD-48600 | record:brief |
| Channel | Customer Feedback | record:intake |
| Source | Zendesk ticket ZD-48600 (sample, synthetic) | record:intake |
| Received | 2026-10-24 | record:intake |
| Source link (GitHub) | `hobasa-agentic-sdlc/requirements/ZD-48600.md` | record:intake; file:hobasa-agentic-sdlc/requirements/ZD-48600.md |
| Repositories named in the source file | ap_pipeline, ap_forecast, ap_aging, ap_portal | file:hobasa-agentic-sdlc/requirements/ZD-48600.md |

## Original intake text (verbatim, treated as data)

> AP managers want to see which overdue invoices belong to vendors that usually pay late, so they can chase them first. (1) Data engineering, ap_pipeline: the vendor feed gains an optional paid_date column (ISO date, empty when unpaid); an invalid paid_date rejects the row with reason 'paid_date'; add delays_by_vendor(records) returning {vendor: [delay_days, ...]} for paid records with a paid_date, where delay_days = (paid_date - due_date) in days, in feed order. (2) AI / data science, ap_forecast: add vendor_risk(history) returning 'high' when predict_delay_days(history) > 30, 'medium' when it is > 10, otherwise 'low'; build_explanation_request gains an optional risk argument and, when given, the prompt ends with ' Risk level: <risk>.'. (3) Backend, ap_aging: add overdue_with_risk(invoices, as_of, risk_by_vendor) returning, for unpaid invoices more than 30 days past due, a list of {'id', 'vendor', 'days', 'amount', 'risk'} sorted by days descending then id, with risk 'unknown' for vendors not in risk_by_vendor. (4) Frontend, ap_portal: add renderOverdueRisk(rows) rendering '<table class="overdue-risk">' with one '<tr class="risk-RISK">' per row showing id, vendor, days and amount to two decimals, and an empty string when there are no rows. The whole flow must be proven end to end: feed -> delays -> risk -> overdue list -> portal table.

Source: record:intake; file:hobasa-agentic-sdlc/requirements/ZD-48600.md

## Extracted change requests

These are faithful splits of the text above. No facts have been added.

| ID | Area / repository (as named in the ticket) | Change requested |
|---|---|---|
| CR-0 | Business need | AP managers can see which overdue invoices belong to vendors that usually pay late, so they can chase them first. |
| CR-1 | Data engineering / ap_pipeline | The vendor feed gains an optional `paid_date` column (ISO date, empty when unpaid). An invalid `paid_date` rejects the row with reason `'paid_date'`. |
| CR-2 | Data engineering / ap_pipeline | New `delays_by_vendor(records)` returns `{vendor: [delay_days, ...]}` for paid records with a `paid_date`, where `delay_days = (paid_date - due_date)` in days, in feed order. |
| CR-3 | AI / data science / ap_forecast | New `vendor_risk(history)` returns `'high'` when `predict_delay_days(history) > 30`, `'medium'` when it is `> 10`, and `'low'` otherwise. |
| CR-4 | AI / data science / ap_forecast | `build_explanation_request` gains an optional `risk` argument. When `risk` is given, the prompt ends with `' Risk level: <risk>.'`. |
| CR-5 | Backend / ap_aging | New `overdue_with_risk(invoices, as_of, risk_by_vendor)`. For unpaid invoices more than 30 days past due, it returns a list of `{'id', 'vendor', 'days', 'amount', 'risk'}`, sorted by days descending and then by id. A vendor not in `risk_by_vendor` gets risk `'unknown'`. |
| CR-6 | Frontend / ap_portal | New `renderOverdueRisk(rows)` renders `<table class="overdue-risk">` with one `<tr class="risk-RISK">` per row. Each row shows id, vendor, days and amount (amount to two decimals). It returns an empty string when there are no rows. |
| CR-7 | Cross-repository | The whole flow must be proven end to end: feed -> delays -> risk -> overdue list -> portal table. |

Source for every row: record:intake
