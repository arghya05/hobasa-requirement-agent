# feat.intake: FEAT-ZD-48600

The original intake item and its source link. Step REQ-01 (Requirement Intake), attempt 3.

## Source record

| Field | Value | Source |
|---|---|---|
| Trace ID | FEAT-ZD-48600 | record:brief |
| Channel | Customer Feedback | record:intake |
| Source | Zendesk ticket ZD-48600 (sample, synthetic) | record:intake |
| Received | 2026-10-24 | record:intake |
| Source link (GitHub) | `hobasa-agentic-sdlc/requirements/ZD-48600.md` | record:intake |
| Trigger type | Email/Ticket ("Reads the ticket") | record:brief |

## Original text (verbatim, treated as data)

> AP managers want to see which overdue invoices belong to vendors that usually pay late, so they can chase them first. (1) Data engineering, ap_pipeline: the vendor feed gains an optional paid_date column (ISO date, empty when unpaid); an invalid paid_date rejects the row with reason 'paid_date'; add delays_by_vendor(records) returning {vendor: [delay_days, ...]} for paid records with a paid_date, where delay_days = (paid_date - due_date) in days, in feed order. (2) AI / data science, ap_forecast: add vendor_risk(history) returning 'high' when predict_delay_days(history) > 30, 'medium' when it is > 10, otherwise 'low'; build_explanation_request gains an optional risk argument and, when given, the prompt ends with ' Risk level: <risk>.'. (3) Backend, ap_aging: add overdue_with_risk(invoices, as_of, risk_by_vendor) returning, for unpaid invoices more than 30 days past due, a list of {'id', 'vendor', 'days', 'amount', 'risk'} sorted by days descending then id, with risk 'unknown' for vendors not in risk_by_vendor. (4) Frontend, ap_portal: add renderOverdueRisk(rows) rendering '<table class="overdue-risk">' with one '<tr class="risk-RISK">' per row showing id, vendor, days and amount to two decimals, and an empty string when there are no rows. The whole flow must be proven end to end: feed -> delays -> risk -> overdue list -> portal table.

Source: record:intake

## Change requests extracted from the ticket

| # | Area / repository | Change request | Source |
|---|---|---|---|
| CR-1 | Data engineering / ap_pipeline | The vendor feed gains an optional `paid_date` column (ISO date, empty when unpaid). An invalid `paid_date` rejects the row with reason `'paid_date'`. | record:intake |
| CR-2 | Data engineering / ap_pipeline | Add `delays_by_vendor(records)`. It returns `{vendor: [delay_days, ...]}` for paid records with a `paid_date`, where `delay_days = (paid_date - due_date)` in days, in feed order. | record:intake |
| CR-3 | AI / data science / ap_forecast | Add `vendor_risk(history)`. It returns `'high'` when `predict_delay_days(history) > 30`, `'medium'` when the value is `> 10`, and `'low'` otherwise. | record:intake |
| CR-4 | AI / data science / ap_forecast | `build_explanation_request` gains an optional `risk` argument. When `risk` is given, the prompt ends with `' Risk level: <risk>.'`. | record:intake |
| CR-5 | Backend / ap_aging | Add `overdue_with_risk(invoices, as_of, risk_by_vendor)`. For unpaid invoices more than 30 days past due, it returns a list of `{'id', 'vendor', 'days', 'amount', 'risk'}` sorted by days descending, then by id. Risk is `'unknown'` for vendors not in `risk_by_vendor`. | record:intake |
| CR-6 | Frontend / ap_portal | Add `renderOverdueRisk(rows)`. It renders `<table class="overdue-risk">` with one `<tr class="risk-RISK">` per row, showing id, vendor, days and amount to two decimals. It returns an empty string when there are no rows. | record:intake |
| CR-7 | Cross-cutting | The whole flow must be proven end to end: feed -> delays -> risk -> overdue list -> portal table. | record:intake |

## Business need (as stated)

AP managers want to see which overdue invoices belong to vendors that usually pay late, so they can chase those first (record:intake).

## Notes for the reviewer

- This file holds the original item only. The roadmap link, the checks, the assumptions and the open questions are in `feat.prebacklog.md`.
- The ticket says it is a synthetic sample (record:intake).
