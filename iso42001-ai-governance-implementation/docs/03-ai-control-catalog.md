[← README](../README.md) · [Assets](01-ai-asset-inventory.md) · [Risks](02-ai-risk-register.md) · **Controls** · [Policies](04-ai-policies.md)

# AI Control Catalog

10 controls that treat the risks in the register. Each is specific, measurable and testable, with an effectiveness rating and the reason for it. The primary framework follows the lab form; ISO 42001 and NIST AI RMF references are given in each description.

## Summary

| Effective | Partially Effective | Ineffective | Not Tested |
|---|---|---|---|
| 2 | 3 | 3 | 2 |

| ID | Control | Framework | Reference | Effectiveness | Frequency | Owner |
|---|---|---|---|---|---|---|
| [CTL-001](#ctl-001) | Subgroup fairness and performance gate before every high-risk model release | GDPR | Art. 5(1)(a) | **Ineffective** | Quarterly | Head of Clinical AI |
| [CTL-002](#ctl-002) | Human oversight with a recorded reason for every accept or override | GDPR | Art. 22 | **Partially Effective** | Continuous | AI Governance Lead |
| [CTL-003](#ctl-003) | Role-based access to training data with quarterly recertification | CIS Controls | 6.8 | **Partially Effective** | Quarterly | Data Engineering Lead |
| [CTL-004](#ctl-004) | De-identification and re-identification testing of training datasets | GDPR | Art. 25 | **Not Tested** | Quarterly | Data Protection Officer |
| [CTL-005](#ctl-005) | Daily drift monitoring with defined retraining triggers | SOC 2 | CC7.2 | **Ineffective** | Continuous | Head of Financial AI |
| [CTL-006](#ctl-006) | Approved sources and scanning for third-party models and libraries | CIS Controls | 16.4 | **Ineffective** | Monthly | ML Platform Lead |
| [CTL-007](#ctl-007) | Two-person approval to promote a model to production | SOC 2 | CC8.1 | **Partially Effective** | Continuous | ML Platform Lead |
| [CTL-008](#ctl-008) | AI asset inventory with lifecycle stage tracking | NIST CSF | ID.AM-02 | **Effective** | Monthly | AI Governance Lead |
| [CTL-009](#ctl-009) | AI obligations register and conformity assessment workplan | ISO 27001 | A.5.31 | **Not Tested** | Quarterly | AI Governance Lead |
| [CTL-010](#ctl-010) | Tamper-evident logging of model decisions and reviewer actions | ISO 27001 | A.8.15 | **Effective** | Continuous | ML Platform Lead |

## Control records

<a id="ctl-001"></a>
### CTL-001: Subgroup fairness and performance gate before every high-risk model release

| Field | Value |
|---|---|
| Primary framework | GDPR, Art. 5(1)(a) |
| Effectiveness | **Ineffective** |
| Frequency | Quarterly |
| Owner | Head of Clinical AI |
| Description | Block release of any high-risk model unless a signed fairness report shows sensitivity and specificity for every subgroup (age band, sex, skin tone and scanner type) within 5 percentage points of the overall result. The model owner and AI Governance Lead sign the report, and it is stored in the model registry. Also supports ISO 42001 clause 6.1.4 and NIST AI RMF MEASURE 2.11. |
| Decision rationale | No subgroup testing is done today, so the control is not operating and RSK-001 stays High. Rating moves up once the first signed report exists and a release has been blocked or passed under the gate. Linked to RSK-001, AST-001 and AST-002. |
| Treats risks | [RSK-001](02-ai-risk-register.md#rsk-001) (Unrepresentative training data exploits the absence of su...) |
| Protects assets | [AST-001](01-ai-asset-inventory.md#ast-001) (Diagnostic Imaging Model (v3.2)), [AST-002](01-ai-asset-inventory.md#ast-002) (Financial Risk Scoring Model (v2.7)) |
| Required by policy | [POL-002](04-ai-policies.md#pol-002) (Model Risk Assessment and Fairness Testing Policy) |

<a id="ctl-002"></a>
### CTL-002: Human oversight with a recorded reason for every accept or override

| Field | Value |
|---|---|
| Primary framework | GDPR, Art. 22 |
| Effectiveness | **Partially Effective** |
| Frequency | Continuous |
| Owner | AI Governance Lead |
| Description | In the Human Oversight Review Console, require the reviewer to record accept, override or escalate with a short reason for 100% of high-risk outputs. Flag any reviewer who accepts more than 98% of outputs unchanged in a week for a calibration review. Also supports EU AI Act Article 14, ISO 42001 Annex A.9 and NIST AI RMF GOVERN 3.2. |
| Decision rationale | The console already shows outputs and confidence and logs decisions, but the reason is optional and acceptance rates are not measured, so over-reliance would go unnoticed. Design is sound; coverage is incomplete. Linked to RSK-002 and AST-005. |
| Treats risks | [RSK-002](02-ai-risk-register.md#rsk-002) (Automation bias among time-pressured clinicians exploits...) |
| Protects assets | [AST-005](01-ai-asset-inventory.md#ast-005) (Human Oversight Review Console) |
| Required by policy | [POL-003](04-ai-policies.md#pol-003) (Human Oversight and Automated Decision Policy) |

<a id="ctl-003"></a>
### CTL-003: Role-based access to training data with quarterly recertification

| Field | Value |
|---|---|
| Primary framework | CIS Controls, 6.8 |
| Effectiveness | **Partially Effective** |
| Frequency | Quarterly |
| Owner | Data Engineering Lead |
| Description | Grant access to the Training Data Lake only through role groups per dataset, with just-in-time approval that expires after 30 days for sensitive datasets. Recertify all access every quarter and remove anything not re-approved. Target: zero standing access to sensitive datasets. |
| Decision rationale | Role groups, single sign-on and MFA are in place, but many data scientists still hold standing read access to every dataset, and reviews are annual. Partly effective until standing access is removed. Linked to RSK-003 and AST-003. |
| Treats risks | [RSK-003](02-ai-risk-register.md#rsk-003) (External attacker or malicious insider exploits over-broa...) |
| Protects assets | [AST-003](01-ai-asset-inventory.md#ast-003) (Clinical and Financial Training Data Lake) |
| Required by policy | None recorded |

<a id="ctl-004"></a>
### CTL-004: De-identification and re-identification testing of training datasets

| Field | Value |
|---|---|
| Primary framework | GDPR, Art. 25 |
| Effectiveness | **Not Tested** |
| Frequency | Quarterly |
| Owner | Data Protection Officer |
| Description | Before a dataset enters the Training Data Lake, apply de-identification, run a re-identification test (target: k-anonymity of 5 or more on quasi-identifiers) and record the result. Re-test datasets every quarter or when new fields are added. Also supports ISO 42001 Annex A.7 and NIST AI RMF MEASURE 2.10. |
| Decision rationale | De-identification is applied, but no re-identification test has been run, so its strength is unknown. Rated Not Tested until the first quarterly test results are on file. Linked to RSK-003 and AST-003. |
| Treats risks | [RSK-003](02-ai-risk-register.md#rsk-003) (External attacker or malicious insider exploits over-broa...) |
| Protects assets | [AST-003](01-ai-asset-inventory.md#ast-003) (Clinical and Financial Training Data Lake) |
| Required by policy | None recorded |

<a id="ctl-005"></a>
### CTL-005: Daily drift monitoring with defined retraining triggers

| Field | Value |
|---|---|
| Primary framework | SOC 2, CC7.2 |
| Effectiveness | **Ineffective** |
| Frequency | Continuous |
| Owner | Head of Financial AI |
| Description | Calculate the population stability index of input data and scores daily, alert at 0.2 or higher, and check outcomes by group every month. Trigger a model review when accuracy falls more than 3 points below the release baseline. Report results monthly to the AI governance group. Also supports EU AI Act Article 72 and NIST AI RMF MANAGE 4.1. |
| Decision rationale | The Financial Risk Scoring Model is tested only at release, with no live monitoring or retraining rule, so drift would not be seen. The control does not operate yet. Linked to RSK-004 and AST-002. |
| Treats risks | [RSK-004](02-ai-risk-register.md#rsk-004) (Shifts in economic conditions exploit missing drift monit...) |
| Protects assets | [AST-002](01-ai-asset-inventory.md#ast-002) (Financial Risk Scoring Model (v2.7)) |
| Required by policy | [POL-002](04-ai-policies.md#pol-002) (Model Risk Assessment and Fairness Testing Policy) |

<a id="ctl-006"></a>
### CTL-006: Approved sources and scanning for third-party models and libraries

| Field | Value |
|---|---|
| Primary framework | CIS Controls, 16.4 |
| Effectiveness | **Ineffective** |
| Frequency | Monthly |
| Owner | ML Platform Lead |
| Description | Allow only pretrained models and packages from an approved source list. Scan every component for known vulnerabilities and malicious content, verify checksums, and record the source in the model registry. Target: 100% of components in production have a recorded source and a clean scan. Also supports ISO 42001 Annex A.10 and NIST AI RMF GOVERN 6.1. |
| Decision rationale | Teams pull models and packages from public sources with no list, no scan and no provenance record, so nothing is checked. The control is not in place. Linked to RSK-005 and AST-004. |
| Treats risks | [RSK-005](02-ai-risk-register.md#rsk-005) (Compromised third-party pretrained model or open-source l...) |
| Protects assets | [AST-004](01-ai-asset-inventory.md#ast-004) (MLOps Cloud Account and Model Registry) |
| Required by policy | None recorded |

<a id="ctl-007"></a>
### CTL-007: Two-person approval to promote a model to production

| Field | Value |
|---|---|
| Primary framework | SOC 2, CC8.1 |
| Effectiveness | **Partially Effective** |
| Frequency | Continuous |
| Owner | ML Platform Lead |
| Description | Allow promotion to production only through the pipeline, and only with approval from the model owner and the AI Governance Lead and a linked validation report. Review every production promotion each month against its approval record. Target: 100% of production models trace to an approval. |
| Decision rationale | The registry requires one approval, which stops casual changes, but a single person can approve their own model and the validation report is not enforced. Reviewed on a sample of last quarter's promotions. Linked to RSK-005 and AST-004. |
| Treats risks | [RSK-005](02-ai-risk-register.md#rsk-005) (Compromised third-party pretrained model or open-source l...) |
| Protects assets | [AST-004](01-ai-asset-inventory.md#ast-004) (MLOps Cloud Account and Model Registry) |
| Required by policy | [POL-004](04-ai-policies.md#pol-004) (AI Asset Inventory and Model Lifecycle Policy) |

<a id="ctl-008"></a>
### CTL-008: AI asset inventory with lifecycle stage tracking

| Field | Value |
|---|---|
| Primary framework | NIST CSF, ID.AM-02 |
| Effectiveness | **Effective** |
| Frequency | Monthly |
| Owner | AI Governance Lead |
| Description | Record every model, dataset, pipeline and review tool in the AI asset inventory with owner, classification, environment and lifecycle stage (development, validation, deployed, retired). Reconcile the inventory against the cloud accounts and the model registry each month. Target: 100% match. Also supports ISO 42001 clause 7.5 and NIST AI RMF GOVERN 1.6. |
| Decision rationale | The inventory covers the five core assets, was reconciled against the cloud account and registry with no differences, and each record has an owner and a lifecycle stage. Rated Effective, with coverage to grow as new models are added. Linked to AST-001 to AST-005. |
| Treats risks | None recorded |
| Protects assets | [AST-001](01-ai-asset-inventory.md#ast-001) (Diagnostic Imaging Model (v3.2)), [AST-002](01-ai-asset-inventory.md#ast-002) (Financial Risk Scoring Model (v2.7)), [AST-003](01-ai-asset-inventory.md#ast-003) (Clinical and Financial Training Data Lake), [AST-004](01-ai-asset-inventory.md#ast-004) (MLOps Cloud Account and Model Registry), [AST-005](01-ai-asset-inventory.md#ast-005) (Human Oversight Review Console) |
| Required by policy | [POL-004](04-ai-policies.md#pol-004) (AI Asset Inventory and Model Lifecycle Policy) |

<a id="ctl-009"></a>
### CTL-009: AI obligations register and conformity assessment workplan

| Field | Value |
|---|---|
| Primary framework | ISO 27001, A.5.31 |
| Effectiveness | **Not Tested** |
| Frequency | Quarterly |
| Owner | AI Governance Lead |
| Description | Keep a register of legal obligations for each AI system (EU AI Act Articles 9 to 15 and 43, GDPR, and Canadian requirements) with an owner, evidence and due date. Complete a conformity assessment checklist for 100% of high-risk systems before they are placed on the EU market. Review the register each quarter with Compliance. Also supports ISO 42001 clause 4.2 and NIST AI RMF GOVERN 1.1. |
| Decision rationale | The register and checklist have been designed but not yet used on a real release, so there is no evidence they work. Not Tested until the first conformity assessment is run against it. Linked to RSK-006, AST-001 and AST-002. |
| Treats risks | [RSK-006](02-ai-risk-register.md#rsk-006) (New EU AI Act and Canadian AI law obligations exploit the...) |
| Protects assets | [AST-001](01-ai-asset-inventory.md#ast-001) (Diagnostic Imaging Model (v3.2)), [AST-002](01-ai-asset-inventory.md#ast-002) (Financial Risk Scoring Model (v2.7)) |
| Required by policy | None recorded |

<a id="ctl-010"></a>
### CTL-010: Tamper-evident logging of model decisions and reviewer actions

| Field | Value |
|---|---|
| Primary framework | ISO 27001, A.8.15 |
| Effectiveness | **Effective** |
| Frequency | Continuous |
| Owner | ML Platform Lead |
| Description | Write every model output, reviewer action and model version to append-only storage with time stamps, and keep it for at least 6 years. Test the trail every month by tracing 30 sampled decisions from input to reviewer action. Target: 30 of 30 traced. Also supports EU AI Act Article 12 and ISO 42001 Annex A.6. |
| Decision rationale | The last two monthly samples traced fully from input to reviewer action, and logs are append-only with restricted access. Operating as designed, with coverage to extend to the financial model. Linked to RSK-002, RSK-006 and AST-005. |
| Treats risks | [RSK-002](02-ai-risk-register.md#rsk-002) (Automation bias among time-pressured clinicians exploits...), [RSK-006](02-ai-risk-register.md#rsk-006) (New EU AI Act and Canadian AI law obligations exploit the...) |
| Protects assets | [AST-005](01-ai-asset-inventory.md#ast-005) (Human Oversight Review Console) |
| Required by policy | [POL-003](04-ai-policies.md#pol-003) (Human Oversight and Automated Decision Policy) |


---

[← Previous](02-ai-risk-register.md) · [Next →](04-ai-policies.md) · [Back to README](../README.md)
