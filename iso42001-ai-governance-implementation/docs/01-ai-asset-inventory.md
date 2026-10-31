[← README](../README.md) · **Assets** · [Risks](02-ai-risk-register.md) · [Controls](03-ai-control-catalog.md) · [Policies](04-ai-policies.md)

# AI Asset Inventory

5 AI assets in scope for the AI management system, with classification, owner and environment. Each asset links to the risks that affect it and the controls that protect it. Lifecycle stages tracked in the model registry are development, validation, deployed and retired.

## Summary

| ID | Name | Type | Classification | Owner | Environment |
|---|---|---|---|---|---|
| [AST-001](#ast-001) | Diagnostic Imaging Model (v3.2) | Application | Critical | Head of Clinical AI | Production |
| [AST-002](#ast-002) | Financial Risk Scoring Model (v2.7) | Application | High | Head of Financial AI | Production |
| [AST-003](#ast-003) | Clinical and Financial Training Data Lake | Data Store | Critical | Data Engineering Lead | Production |
| [AST-004](#ast-004) | MLOps Cloud Account and Model Registry | Cloud Account | High | ML Platform Lead | Development |
| [AST-005](#ast-005) | Human Oversight Review Console | Application | High | AI Governance Lead | Production |

## Asset records

<a id="ast-001"></a>
### AST-001: Diagnostic Imaging Model (v3.2)

| Field | Value |
|---|---|
| Type | Application |
| Classification | Critical |
| Owner | Head of Clinical AI |
| Environment | Production |
| Description | Machine learning model that flags suspected abnormalities in medical images for radiologists at hospital clients in Canada and the EU. Classified as a high-risk AI system under the EU AI Act. Outputs are advisory and reviewed by a clinician before any decision; bias, drift and performance are monitored. |
| Risks | [RSK-001](02-ai-risk-register.md#rsk-001) (Unrepresentative training data exploits the absence of su...), [RSK-002](02-ai-risk-register.md#rsk-002) (Automation bias among time-pressured clinicians exploits...), [RSK-006](02-ai-risk-register.md#rsk-006) (New EU AI Act and Canadian AI law obligations exploit the...) |
| Controls | [CTL-001](03-ai-control-catalog.md#ctl-001) (Subgroup fairness and performance gate before every high-...), [CTL-008](03-ai-control-catalog.md#ctl-008) (AI asset inventory with lifecycle stage tracking), [CTL-009](03-ai-control-catalog.md#ctl-009) (AI obligations register and conformity assessment workplan) |

<a id="ast-002"></a>
### AST-002: Financial Risk Scoring Model (v2.7)

| Field | Value |
|---|---|
| Type | Application |
| Classification | High |
| Owner | Head of Financial AI |
| Environment | Production |
| Description | Model that scores credit and financial risk for banking clients in Canada and the EU. Treated as high-risk because it affects access to financial services. Fairness testing across protected groups is run before each release, and adverse decisions are routed for human review. |
| Risks | [RSK-004](02-ai-risk-register.md#rsk-004) (Shifts in economic conditions exploit missing drift monit...), [RSK-006](02-ai-risk-register.md#rsk-006) (New EU AI Act and Canadian AI law obligations exploit the...) |
| Controls | [CTL-001](03-ai-control-catalog.md#ctl-001) (Subgroup fairness and performance gate before every high-...), [CTL-005](03-ai-control-catalog.md#ctl-005) (Daily drift monitoring with defined retraining triggers), [CTL-008](03-ai-control-catalog.md#ctl-008) (AI asset inventory with lifecycle stage tracking), [CTL-009](03-ai-control-catalog.md#ctl-009) (AI obligations register and conformity assessment workplan) |

<a id="ast-003"></a>
### AST-003: Clinical and Financial Training Data Lake

| Field | Value |
|---|---|
| Type | Data Store |
| Classification | Critical |
| Owner | Data Engineering Lead |
| Environment | Production |
| Description | Central store of de-identified health records and anonymized financial data used to train, validate and test models. Holds sensitive personal data, with lineage and consent records tracked and data kept in the region required by each client contract. |
| Risks | [RSK-001](02-ai-risk-register.md#rsk-001) (Unrepresentative training data exploits the absence of su...), [RSK-003](02-ai-risk-register.md#rsk-003) (External attacker or malicious insider exploits over-broa...) |
| Controls | [CTL-003](03-ai-control-catalog.md#ctl-003) (Role-based access to training data with quarterly recerti...), [CTL-004](03-ai-control-catalog.md#ctl-004) (De-identification and re-identification testing of traini...), [CTL-008](03-ai-control-catalog.md#ctl-008) (AI asset inventory with lifecycle stage tracking) |

<a id="ast-004"></a>
### AST-004: MLOps Cloud Account and Model Registry

| Field | Value |
|---|---|
| Type | Cloud Account |
| Classification | High |
| Owner | ML Platform Lead |
| Environment | Development |
| Description | Cloud account hosting experiment tracking, training pipelines and the model registry that records each model version, its approval status and lifecycle stage (development, validation, deployed, retired). Access is restricted by role and every promotion to production needs a recorded approval. |
| Risks | [RSK-005](02-ai-risk-register.md#rsk-005) (Compromised third-party pretrained model or open-source l...) |
| Controls | [CTL-006](03-ai-control-catalog.md#ctl-006) (Approved sources and scanning for third-party models and...), [CTL-007](03-ai-control-catalog.md#ctl-007) (Two-person approval to promote a model to production), [CTL-008](03-ai-control-catalog.md#ctl-008) (AI asset inventory with lifecycle stage tracking) |

<a id="ast-005"></a>
### AST-005: Human Oversight Review Console

| Field | Value |
|---|---|
| Type | Application |
| Classification | High |
| Owner | AI Governance Lead |
| Environment | Production |
| Description | Web application that shows clinicians and risk analysts each model output with its explanation and confidence, lets them accept, override or escalate it, and logs every decision. Supports the human oversight requirement for high-risk AI systems and provides an audit trail. |
| Risks | [RSK-002](02-ai-risk-register.md#rsk-002) (Automation bias among time-pressured clinicians exploits...) |
| Controls | [CTL-002](03-ai-control-catalog.md#ctl-002) (Human oversight with a recorded reason for every accept o...), [CTL-008](03-ai-control-catalog.md#ctl-008) (AI asset inventory with lifecycle stage tracking), [CTL-010](03-ai-control-catalog.md#ctl-010) (Tamper-evident logging of model decisions and reviewer ac...) |


---

[Next →](02-ai-risk-register.md) · [Back to README](../README.md)
