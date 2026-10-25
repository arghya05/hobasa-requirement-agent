# feat.fitment: FEAT-ZD-48600

**Product Fitment Validation, status: Draft for the PM and Leadership gate.** This step returns a recommended verdict with its evidence. It does not approve, prioritize or route the entry. PM and Leadership make the Yes or No decision. (record:brief)

## 1. Verdict

| Field | Value | Source |
|---|---|---|
| Trace ID | FEAT-ZD-48600 | record:brief |
| Entry | Overdue invoices ranked by vendor late-payment risk (feed -> delays -> risk -> overdue list -> portal table) | feat.classification |
| Category / qualifier | New Feature / Not Technical Only | feat.classification |
| **Recommended verdict** | **Yes**, based on the roadmap evidence in section 2. The capability check (section 3) shows only new additions and no replacement. Strategy fit (section 4) is not established by the inputs and is left to PM and Leadership (OQ-F1). | sections 2 to 4 below |
| **Reason code** | **FIT-YES-ROADMAP**: the entry is linked to a planned roadmap item. | org.roadmap; journey:feat.prebacklog |
| Linked roadmap item | R-AP-12, "give AP managers earlier visibility of overdue payables" (Q4 2026 roadmap, AP module, owner PM) | org.roadmap; feat.classification |

## 2. Roadmap fit: Yes

| Check | Finding | Source |
|---|---|---|
| Roadmap item text | R-AP-12: "give AP managers earlier visibility of overdue payables". | org.roadmap |
| Ticket's business need | "AP managers want to see which overdue invoices belong to vendors that usually pay late, so they can chase them first." | journey:feat.intake |
| Link recorded at intake | REQ-01 linked the entry to R-AP-12. It recorded that the ticket's goal (seeing overdue invoices so they can be chased first) falls under "earlier visibility of overdue payables". The PM approved that step. | journey:feat.prebacklog; feat.classification |
| What the entry adds for AP managers | CR-5 returns unpaid invoices more than 30 days past due with a risk label. CR-6 renders them in a new portal table (`renderOverdueRisk`). | journey:feat.intake; feat.classification |
| Other roadmap items | R-AP-14, "aging export for finance close", is not linked. The ticket asks for no export. | org.roadmap; journey:feat.prebacklog |

## 3. Capability check: adds to the documented capability, replaces nothing

| Check | Finding | Source |
|---|---|---|
| Documented capability | "ap_aging service computes aging buckets (current, 1-30, 31-60, 61-90, 90+) for open invoices." | org.strategy_capability |
| Change in ap_aging | CR-5 adds a new function, `overdue_with_risk(invoices, as_of, risk_by_vendor)`, for unpaid invoices more than 30 days past due. | journey:feat.intake; feat.classification |
| Existing behaviour | The architecture recorded for this item says: "Keep every existing signature; add new functions." | file:hobasa-agentic-sdlc/requirements/ZD-48600.md; feat.classification |
| Parts outside the documented capability | CR-1 and CR-2 (ap_pipeline), CR-3 and CR-4 (ap_forecast), and CR-6 (ap_portal). org.strategy_capability describes only the ap_aging service, so it has no capability text for these repositories (OQ-F2). | feat.classification; org.strategy_capability |
| Risk note recorded in the source file | No finance posting, authentication, tenancy or payment execution; tier T2; the risk label is advisory only. | feat.classification; file:hobasa-agentic-sdlc/requirements/ZD-48600.md |

## 4. Strategy check: not established by the inputs

| Strategy statement | What the inputs say about this entry | Source |
|---|---|---|
| "help finance teams pay on time and avoid late-payment penalties" | No input links this entry to paying on time or to late-payment penalties. The ticket's stated purpose is to see overdue invoices of "vendors that usually pay late, so they can chase them first". Whether that purpose serves this strategy is for PM and Leadership to judge (OQ-F1). | org.strategy_capability; journey:feat.intake |
| "auditability and traceability are core product promises" | The flow must be proven end to end (CR-7). The inputs do not say whether the risk label, or the delay history and predicted delay behind it, must be recorded for audit (OQ-F3). | org.strategy_capability; feat.classification |

## 5. Decision log check

No conflict found. D-2026-050 says paid invoices are excluded from aging. CR-5 covers unpaid invoices only. D-2026-031 and D-2026-044 were checked at intake with no conflict, and this step adds no new rule. (record:memory; journey:feat.prebacklog; feat.classification)

## 6. Assumptions (non-blocking)

- **F-1:** The roadmap item speaks of "overdue payables". The ticket speaks of "vendors that usually pay late" and asks to "chase them first". CR-2 computes delay as `paid_date - due_date`. The verdict assumes the ticket concerns the AP module's overdue invoices, as REQ-01 recorded when it linked the entry to R-AP-12. (org.roadmap; journey:feat.intake; journey:feat.prebacklog)
- **F-2:** No list of fitment reason codes was in this step's inputs. FIT-YES-ROADMAP is a descriptive code proposed here (OQ-F4). (record:brief)

## 7. Open questions (non-blocking)

- **OQ-F1 (PM / Leadership):** Does this entry serve the strategy "help finance teams pay on time and avoid late-payment penalties"? What do "vendors that usually pay late" and "chase them first" mean for an AP (payables) module? The inputs do not say.
- **OQ-F2 (PM / Leadership):** org.strategy_capability describes only the ap_aging service. If this entry is approved, should it be updated to cover ap_pipeline, ap_forecast and ap_portal, and a vendor risk capability?
- **OQ-F3 (Leadership):** The strategy names auditability and traceability as core product promises. Should the vendor risk label, and the delay history and predicted delay behind it, be recorded or explainable for audit? This could become a business rule in the BRD (REQ-04).
- **OQ-F4 (PM):** Is there an approved list of fitment reason codes? If so, which code should replace FIT-YES-ROADMAP?
- Carried forward from feat.classification. These do not affect the verdict:
  - OQ-A to OQ-D: sequencing with ZD-48211, ZD-48501, ZD-48470, PROV-ACME-2026-11 and ZD-48377.
  - OQ-F: the Pre Backlog sheet and the DevOps board were not available.

## 8. Notification

This step sent no notification. This file is the notification content for PM and Leadership to decide Yes or No on FEAT-ZD-48600. Sending it is left to the workflow after evaluation. (record:brief)
