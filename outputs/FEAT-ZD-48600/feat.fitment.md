# feat.fitment: FEAT-ZD-48600

Product fitment check for the Pre Backlog entry FEAT-ZD-48600 (ZD-48600, "Show which overdue invoices belong to vendors that usually pay late"). The entry is checked against the product capability, the Q4 2026 roadmap and the product strategy. This is a draft verdict. The PM and Leadership decide Yes or No at the gate.

Statements marked "agent judgement" are this agent's own assessment. No input states them.

## Verdict

| Field | Value | Source |
|---|---|---|
| Trace ID | FEAT-ZD-48600 | record:brief; feat.classification |
| **Fitment verdict** | **Yes** (recommended; agent judgement). The PM and Leadership make the decision. | evidence below |
| **Reason code** | **FIT-Y-ROADMAP**: the entry fits a named roadmap item (R-AP-12), builds on the existing capability, and supports the stated strategy. | org.roadmap; org.strategy_capability; feat.classification |
| Linked roadmap item | R-AP-12 "give AP managers earlier visibility of overdue payables" (Q4 2026 roadmap, AP module, owner: PM) | org.roadmap; feat.classification |
| Category / qualifier | New Feature / Not Technical Only | feat.classification |
| Risk tier (advisory) | T2: "No finance posting, authentication, tenancy or payment execution in this change". The risk label is advisory only. | feat.classification |
| Conditions on the Yes | None blocking. The gate should confirm FQ-1, the business meaning of "vendors that usually pay late" and "chase them first". See "Open questions". | this file |

FIT-Y-ROADMAP is this agent's own code. This step's inputs contain no list of reason codes (see FQ-5).

## Evidence

### 1. Roadmap fit

| Check | Evidence | Source |
|---|---|---|
| Is there a roadmap item? | Yes. The Q4 2026 AP module roadmap lists (R-AP-12) "give AP managers earlier visibility of overdue payables". feat.classification records R-AP-12 as the entry's linked roadmap item, citing feat.prebacklog as the source of the link. | org.roadmap; feat.classification |
| Does the entry match it? | The ticket says "AP managers want to see which overdue invoices belong to vendors that usually pay late, so they can chase them first". Agent judgement: this matches R-AP-12. Both name AP managers as the users. Both are about overdue items: R-AP-12 says "overdue payables" and the ticket says "overdue invoices". Both aim at seeing those items. The entry adds a portal table of unpaid invoices "more than 30 days past due", each with a vendor risk level. | org.roadmap; file:hobasa-agentic-sdlc/requirements/ZD-48600.md |
| Overlap with the other roadmap item | R-AP-14 is "aging export for finance close". No change request in feat.classification (CR-1 to CR-7) adds an export. | org.roadmap; feat.classification |

### 2. Capability fit

| Check | Evidence | Source |
|---|---|---|
| Current capability | "ap_aging service computes aging buckets (current, 1-30, 31-60, 61-90, 90+) for open invoices." | org.strategy_capability |
| How the entry relates | CR-5 adds `overdue_with_risk(invoices, as_of, risk_by_vendor)` to ap_aging for unpaid invoices "more than 30 days past due". The architecture says "Keep every existing signature; add new functions". The existing functions (`aging_buckets`, `days_past_due`, `bucket_for` and others) are not redefined. Agent judgement: the entry builds on the current capability's invoices and days past due. | feat.classification; file:hobasa-agentic-sdlc/requirements/ZD-48600.md |
| New capability added | The entry adds a vendor payment-delay history (`delays_by_vendor`, ap_pipeline). It adds a vendor risk rule (`vendor_risk`, ap_forecast). It adds a customer-visible overdue-risk table (`renderOverdueRisk`, ap_portal). | feat.classification |
| Gap in the capability statement | org.strategy_capability describes ap_aging and does not mention ap_pipeline, ap_forecast or ap_portal. In the material read for this step, those three repositories are described in the feature's architecture override (ZD-48600). For those three repositories, this check therefore draws on the override, not on the org capability statement (FQ-3). | org.strategy_capability; file:hobasa-agentic-sdlc/requirements/ZD-48600.md |
| Product scope boundaries | org.strategy_capability states no explicit out-of-scope list, so this step cannot check the entry against one (FQ-6). Related facts: the feature's risk map, which sets the advisory tier, records "No finance posting, authentication, tenancy or payment execution in this change". ZD-48510 asks for payment execution, and feat.classification marks it "Not grouped" with this entry. | org.strategy_capability; feat.classification |

### 3. Strategy fit

| Strategy statement | Evidence | Source |
|---|---|---|
| "help finance teams pay on time and avoid late-payment penalties" | The table lists unpaid invoices more than 30 days past due, "sorted by days descending then id", each with a vendor risk level. The ticket's stated purpose is "so they can chase them first". Agent judgement: showing overdue payables with a priority signal supports acting on them sooner, and so supports this statement. The sources do not say how the risk level should change the order in which invoices are paid (FQ-1). | org.strategy_capability; file:hobasa-agentic-sdlc/requirements/ZD-48600.md |
| "auditability and traceability are core product promises" | Each rule in the entry is stated explicitly. `vendor_risk` "uses no LLM; it is a rule on the predicted delay", with thresholds `> 30` and `> 10`. The delay rule is `delay_days = (paid_date - due_date)`. A row with an invalid `paid_date` is rejected with the reason `'paid_date'`. A vendor not in `risk_by_vendor` gets risk `'unknown'`. Agent judgement: explicit rules and a named reject reason (`'paid_date'`) support auditability and traceability. | org.strategy_capability; feat.classification; file:hobasa-agentic-sdlc/requirements/ZD-48600.md |

### 4. Consistency with the decision log

| Decision | Status | Source |
|---|---|---|
| D-2026-050: paid invoices are excluded from aging | Consistent. `overdue_with_risk` covers only unpaid invoices. | record:memory; file:hobasa-agentic-sdlc/requirements/ZD-48600.md |
| D-2026-044: monetary amounts use Decimal, never float | Consistent. CR-5 keeps amounts as Decimal. Between services, amounts travel as strings with two decimals. | record:memory; feat.classification |
| D-2026-031: aging buckets use calendar days after due date | No conflict found. The entry does not say how "days past due" is counted. Assumption: it follows D-2026-031 (calendar days). The BRD should confirm this (FQ-4). | record:memory; file:hobasa-agentic-sdlc/requirements/ZD-48600.md |

No conflict with a recorded decision was found.

## Risks and dependencies that do not change the verdict

These items come from feat.classification and the related intake files. They affect delivery planning, not fitment (agent judgement).

- **Model deprecation**: PROV-ACME-2026-11 replaces acme-text-2, which is deprecated on 2026-12-01, with acme-text-3. It changes `build_explanation_request`, the same function that CR-4 changes. The two changes need ordering (feat.classification OQ-3).
- **Shared overdue definition**: ZD-48501 and ZD-48211 use the same "more than 30 days past due" rule (feat.classification OQ-1).
- **Feed order**: CR-1 needs feed v3, and ZD-48470 brings feed v2 (feat.classification OQ-2).
- **Terminology**: the open regulatory item REG-LPR-2026-4.2 defines "Late" as a payable "more than 60 days past its due date" that remains unpaid. This entry's "overdue" means more than 30 days past due. Recommendation (agent judgement): keep the two labels distinct in the portal and the BRD (FQ-2). Source: file:hobasa-agentic-sdlc/requirements/REG-LPR-2026-4.2.md.

## Notification (workbook outcome)

| Field | Value | Source |
|---|---|---|
| To | PM and Leadership, the gate owners for REQ-03 | record:brief |
| Message | "FEAT-ZD-48600 fitment: Yes recommended (FIT-Y-ROADMAP, R-AP-12). Please decide Yes or No and confirm FQ-1 at the gate." | this file |
| Channel | Not set. The notification channel is still open (feat.prebacklog Q-3, carried forward in feat.classification). The only connector approved for this step is api:github, limited to GET requests on the Hobasa repositories, so no message was sent. This file, pushed by the spine after the gate, is the notification record. | feat.classification; record:brief |

## Open questions (non-blocking)

- **FQ-1 (PM / Leadership, business meaning)**: The roadmap item is about "overdue payables". The ticket asks about "vendors that usually pay late" and wants to "chase them first". It measures delay as `paid_date - due_date` on invoices from each vendor. Agent judgement: in an AP context the vendor is the party being paid, so this wording is ambiguous. Assumption used for the verdict: the risk level helps AP managers decide which overdue payables to act on first. Please confirm. If a different meaning is intended, the strategy fit should be checked again.
- **FQ-2**: Keep "overdue" (more than 30 days) and the regulatory "Late" (more than 60 days, REG-LPR-2026-4.2) as distinct labels.
- **FQ-3**: Should org.strategy_capability be extended to cover ap_pipeline, ap_forecast and ap_portal? Today it does not mention them.
- **FQ-4**: Confirm that "days past due" in `overdue_with_risk` uses calendar days (D-2026-031), and test the boundary of exactly 30 days (L-007).
- **FQ-5**: Is there an approved list of fitment reason codes? FIT-Y-ROADMAP is this agent's own code.
- **FQ-6**: org.strategy_capability states no product out-of-scope list. Should one be added so that later fitment checks can test scope explicitly?
- Carried forward from feat.classification: OQ-1 to OQ-5, and feat.prebacklog Q-1 to Q-5.
