<!-- input org.model_dependency_map for REQ-01: from hobasa-agentic-sdlc/features/FEAT-ZD-48600/org-overrides/org.model_dependency_map.md at commit 5988080, produced by source -->
# org.model_dependency_map (for FEAT-ZD-48600)

ap_forecast uses provider acme-llm model acme-text-2 (config src/ap_forecast/models.json) for the payment-delay explanation. vendor_risk uses no LLM; it is a rule on the predicted delay.
