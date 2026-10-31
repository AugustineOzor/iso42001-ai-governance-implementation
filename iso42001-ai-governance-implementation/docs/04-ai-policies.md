[← README](../README.md) · [Assets](01-ai-asset-inventory.md) · [Risks](02-ai-risk-register.md) · [Controls](03-ai-control-catalog.md) · **Policies**

# AI Policies

4 policies for responsible AI development and deployment. Each links to the controls that put it into practice.

## Summary

| ID | Policy | Status | Owner | Review date |
|---|---|---|---|---|
| [POL-001](#pol-001) | Responsible AI Policy | Approved | AI Governance Lead | 30/09/2027 |
| [POL-002](#pol-002) | Model Risk Assessment and Fairness Testing Policy | Under Review | Head of Clinical AI | 30/11/2026 |
| [POL-003](#pol-003) | Human Oversight and Automated Decision Policy | Draft | AI Governance Lead | 15/12/2026 |
| [POL-004](#pol-004) | AI Asset Inventory and Model Lifecycle Policy | Approved | ML Platform Lead | 31/08/2027 |

## Policy records

<a id="pol-001"></a>
### POL-001: Responsible AI Policy

| Field | Value |
|---|---|
| Status | Approved |
| Owner | AI Governance Lead |
| Review date | 30/09/2027 |
| Purpose | Sets the AI principles (fairness, transparency, accountability, safety and privacy), the scope of the AI management system and who is responsible. Supports ISO 42001 clause 5.2 and NIST AI RMF GOVERN 1. |
| Implemented by controls | None recorded |

<a id="pol-002"></a>
### POL-002: Model Risk Assessment and Fairness Testing Policy

| Field | Value |
|---|---|
| Status | Under Review |
| Owner | Head of Clinical AI |
| Review date | 30/11/2026 |
| Purpose | Requires a documented risk and impact assessment, subgroup bias and fairness testing, and a signed result before any high-risk model is released, with monitoring afterwards. Supports ISO 42001 clauses 6.1.2 and 6.1.4, NIST AI RMF MEASURE 2.11 and EU AI Act Articles 9, 10 and 15. Linked to CTL-001 and CTL-005. |
| Implemented by controls | [CTL-001](03-ai-control-catalog.md#ctl-001) (Subgroup fairness and performance gate before every high-...), [CTL-005](03-ai-control-catalog.md#ctl-005) (Daily drift monitoring with defined retraining triggers) |

<a id="pol-003"></a>
### POL-003: Human Oversight and Automated Decision Policy

| Field | Value |
|---|---|
| Status | Draft |
| Owner | AI Governance Lead |
| Review date | 15/12/2026 |
| Purpose | Defines which AI outputs need human review, who may review them, how reviewers can override a result, and what must be logged. Supports EU AI Act Article 14, GDPR Article 22 and NIST AI RMF GOVERN 3.2. Linked to CTL-002 and CTL-010. |
| Implemented by controls | [CTL-002](03-ai-control-catalog.md#ctl-002) (Human oversight with a recorded reason for every accept o...), [CTL-010](03-ai-control-catalog.md#ctl-010) (Tamper-evident logging of model decisions and reviewer ac...) |

<a id="pol-004"></a>
### POL-004: AI Asset Inventory and Model Lifecycle Policy

| Field | Value |
|---|---|
| Status | Approved |
| Owner | ML Platform Lead |
| Review date | 31/08/2027 |
| Purpose | Requires every model, dataset and pipeline to be recorded with an owner and lifecycle stage (development, validation, deployed, retired), with approval to promote or retire. Supports ISO 42001 Annex A.6 and NIST AI RMF GOVERN 1.6. Linked to CTL-007 and CTL-008. |
| Implemented by controls | [CTL-007](03-ai-control-catalog.md#ctl-007) (Two-person approval to promote a model to production), [CTL-008](03-ai-control-catalog.md#ctl-008) (AI asset inventory with lifecycle stage tracking) |


---

[← Previous](03-ai-control-catalog.md) · [Back to README](../README.md)
