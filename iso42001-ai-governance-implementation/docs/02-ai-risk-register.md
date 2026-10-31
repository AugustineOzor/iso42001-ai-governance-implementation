[← README](../README.md) · [Assets](01-ai-asset-inventory.md) · **Risks** · [Controls](03-ai-control-catalog.md) · [Policies](04-ai-policies.md)

# AI Risk Register

6 risks written in the format **[Threat] exploits [Vulnerability] causing [Impact] to [Asset]**. Score is likelihood × impact. Rating bands: Low 1 to 4, Medium 5 to 9, High 10 to 16, Critical 17 to 25.

## Summary

| Critical | High | Medium | Low |
|---|---|---|---|
| 0 | 4 | 2 | 0 |

### Heat map

Rows are likelihood and columns are impact. Each cell lists the risks that sit there.

| Likelihood ↓ / Impact → | 1 Negligible | 2 Minor | 3 Moderate | 4 Major | 5 Severe |
|---|---|---|---|---|---|
| 5 Almost Certain | · | · | · | · | · |
| 4 Likely | · | · | · | [RSK-006](#rsk-006) | · |
| 3 Possible | · | · | [RSK-004](#rsk-004) | [RSK-002](#rsk-002) | [RSK-001](#rsk-001) |
| 2 Unlikely | · | · | · | [RSK-005](#rsk-005) | [RSK-003](#rsk-003) |
| 1 Rare | · | · | · | · | · |

### Register

| ID | Risk | Category | Status | L × I | Score | Rating | Owner |
|---|---|---|---|---|---|---|---|
| [RSK-006](#rsk-006) | New EU AI Act and Canadian AI law obligations exploit the lack of a conformity assessment and technical documentation process causing the high-risk Diagnostic Imaging Model to be sold without required evidence | Compliance | Open | 4 × 4 | 16 | **High** | AI Governance Lead |
| [RSK-001](#rsk-001) | Unrepresentative training data exploits the absence of subgroup fairness testing causing biased diagnostic results for under-represented patient groups in the Diagnostic Imaging Model | Other | In Progress | 3 × 5 | 15 | **High** | Head of Clinical AI |
| [RSK-002](#rsk-002) | Automation bias among time-pressured clinicians exploits weak human oversight controls causing incorrect model outputs to be accepted without review in the Human Oversight Review Console | Human Error | Open | 3 × 4 | 12 | **High** | AI Governance Lead |
| [RSK-003](#rsk-003) | External attacker or malicious insider exploits over-broad access to the training data lake causing exposure of sensitive health and financial records in the Clinical and Financial Training Data Lake | Access Control | In Progress | 2 × 5 | 10 | **High** | Data Engineering Lead |
| [RSK-004](#rsk-004) | Shifts in economic conditions exploit missing drift monitoring and retraining triggers causing inaccurate and unfair credit risk scores in the Financial Risk Scoring Model | Compliance | Open | 3 × 3 | 9 | **Medium** | Head of Financial AI |
| [RSK-005](#rsk-005) | Compromised third-party pretrained model or open-source library exploits missing supply chain vetting causing poisoned or backdoored components in the MLOps Cloud Account | Vendor Risk | Open | 2 × 4 | 8 | **Medium** | ML Platform Lead |

## Risk records

<a id="rsk-001"></a>
### RSK-001: Unrepresentative training data exploits the absence of subgroup fairness testing causing biased diagnostic results for under-represented patient groups in the Diagnostic Imaging Model

| Field | Value |
|---|---|
| Category | Other |
| Status | In Progress |
| Likelihood | 3 - Possible |
| Impact | 5 - Severe |
| Risk score | 15 (3 × 5), **High** |
| Owner | Head of Clinical AI |
| Description | Training images come mostly from a few hospital networks, so some age groups, skin tones and scanner types are thin in the data. Performance by subgroup is not yet measured before release. Affects AST-001 and AST-003. Bias testing is part of the planned model risk assessment (ISO 42001 clause 6.1.2; NIST AI RMF MEASURE 2.11; EU AI Act Article 10). |
| Decision rationale | Possible because the data gaps are known but the effect has not been measured, and no release gate checks subgroup results yet. Severe because a missed or wrong diagnosis harms patients, the system is high-risk under the EU AI Act, and a bias finding could stop sales in the EU. |
| Affected assets | [AST-001](01-ai-asset-inventory.md#ast-001) (Diagnostic Imaging Model (v3.2)), [AST-003](01-ai-asset-inventory.md#ast-003) (Clinical and Financial Training Data Lake) |
| Treated by controls | [CTL-001](03-ai-control-catalog.md#ctl-001) (Subgroup fairness and performance gate before every high-...) |

<a id="rsk-002"></a>
### RSK-002: Automation bias among time-pressured clinicians exploits weak human oversight controls causing incorrect model outputs to be accepted without review in the Human Oversight Review Console

| Field | Value |
|---|---|
| Category | Human Error |
| Status | Open |
| Likelihood | 3 - Possible |
| Impact | 4 - Major |
| Risk score | 12 (3 × 4), **High** |
| Owner | AI Governance Lead |
| Description | The console shows the model output and confidence, but override and escalation are optional and no one measures how often reviewers simply accept the result. Affects AST-005 and AST-001. EU AI Act Article 14 requires oversight that people can actually use. |
| Decision rationale | Possible because busy reviewers tend to follow automated output, and nothing currently flags a run of unchallenged accepts. Major rather than severe because a clinician still signs off and most errors would be caught later, but some harm to patients and clients is likely when they are not. |
| Affected assets | [AST-001](01-ai-asset-inventory.md#ast-001) (Diagnostic Imaging Model (v3.2)), [AST-005](01-ai-asset-inventory.md#ast-005) (Human Oversight Review Console) |
| Treated by controls | [CTL-002](03-ai-control-catalog.md#ctl-002) (Human oversight with a recorded reason for every accept o...), [CTL-010](03-ai-control-catalog.md#ctl-010) (Tamper-evident logging of model decisions and reviewer ac...) |

<a id="rsk-003"></a>
### RSK-003: External attacker or malicious insider exploits over-broad access to the training data lake causing exposure of sensitive health and financial records in the Clinical and Financial Training Data Lake

| Field | Value |
|---|---|
| Category | Access Control |
| Status | In Progress |
| Likelihood | 2 - Unlikely |
| Impact | 5 - Severe |
| Risk score | 10 (2 × 5), **High** |
| Owner | Data Engineering Lead |
| Description | Many data scientists hold standing read access to all datasets, and access is reviewed only once a year. Data is de-identified or anonymized, but re-identification is possible when records are combined. Affects AST-003. Region rules for Canada and the EU apply. |
| Decision rationale | Unlikely because the data is de-identified, encrypted and behind single sign-on with MFA. Severe because exposure would involve sensitive personal data from clinical and banking clients, trigger notification duties in Canada and the EU, and breach client contracts. |
| Affected assets | [AST-003](01-ai-asset-inventory.md#ast-003) (Clinical and Financial Training Data Lake) |
| Treated by controls | [CTL-003](03-ai-control-catalog.md#ctl-003) (Role-based access to training data with quarterly recerti...), [CTL-004](03-ai-control-catalog.md#ctl-004) (De-identification and re-identification testing of traini...) |

<a id="rsk-004"></a>
### RSK-004: Shifts in economic conditions exploit missing drift monitoring and retraining triggers causing inaccurate and unfair credit risk scores in the Financial Risk Scoring Model

| Field | Value |
|---|---|
| Category | Compliance |
| Status | Open |
| Likelihood | 3 - Possible |
| Impact | 3 - Moderate |
| Risk score | 9 (3 × 3), **Medium** |
| Owner | Head of Financial AI |
| Description | The model is checked at release, but there is no live monitoring of score distribution or outcomes by group, and no rule that sets when to retrain. Affects AST-002. Post-market monitoring is expected for high-risk systems (EU AI Act Article 72; NIST AI RMF MANAGE 4.1). |
| Decision rationale | Possible because economic conditions change often and drift would go unseen. Moderate because scores are one input to a decision that a human analyst reviews, so harm is limited and recoverable, though unfair outcomes could still draw client and regulator attention. |
| Affected assets | [AST-002](01-ai-asset-inventory.md#ast-002) (Financial Risk Scoring Model (v2.7)) |
| Treated by controls | [CTL-005](03-ai-control-catalog.md#ctl-005) (Daily drift monitoring with defined retraining triggers) |

<a id="rsk-005"></a>
### RSK-005: Compromised third-party pretrained model or open-source library exploits missing supply chain vetting causing poisoned or backdoored components in the MLOps Cloud Account

| Field | Value |
|---|---|
| Category | Vendor Risk |
| Status | Open |
| Likelihood | 2 - Unlikely |
| Impact | 4 - Major |
| Risk score | 8 (2 × 4), **Medium** |
| Owner | ML Platform Lead |
| Description | Teams pull pretrained models and packages from public sources without a scan or an approved list, and the registry does not record where each component came from. Affects AST-004 and any model built in it. |
| Decision rationale | Unlikely because few components come from untrusted sources and production promotion needs approval. Major because a poisoned component could alter model behavior across several products before anyone noticed. |
| Affected assets | [AST-004](01-ai-asset-inventory.md#ast-004) (MLOps Cloud Account and Model Registry) |
| Treated by controls | [CTL-006](03-ai-control-catalog.md#ctl-006) (Approved sources and scanning for third-party models and...), [CTL-007](03-ai-control-catalog.md#ctl-007) (Two-person approval to promote a model to production) |

<a id="rsk-006"></a>
### RSK-006: New EU AI Act and Canadian AI law obligations exploit the lack of a conformity assessment and technical documentation process causing the high-risk Diagnostic Imaging Model to be sold without required evidence

| Field | Value |
|---|---|
| Category | Compliance |
| Status | Open |
| Likelihood | 4 - Likely |
| Impact | 4 - Major |
| Risk score | 16 (4 × 4), **High** |
| Owner | AI Governance Lead |
| Description | High-risk systems need technical documentation, a risk management system, logging, human oversight and a conformity assessment before they are placed on the EU market (EU AI Act Articles 9 to 15 and 43). No owner or process is set up yet. Affects AST-001 and AST-002. Canada's proposed AIDA would add similar duties. |
| Decision rationale | Likely because EU clients are already buying and the deadlines are fixed, while the documentation and assessment work has not started. Major because a missing conformity assessment can block EU sales and lead to fines, though the issue can be fixed with time and resources. |
| Affected assets | [AST-001](01-ai-asset-inventory.md#ast-001) (Diagnostic Imaging Model (v3.2)), [AST-002](01-ai-asset-inventory.md#ast-002) (Financial Risk Scoring Model (v2.7)) |
| Treated by controls | [CTL-009](03-ai-control-catalog.md#ctl-009) (AI obligations register and conformity assessment workplan), [CTL-010](03-ai-control-catalog.md#ctl-010) (Tamper-evident logging of model decisions and reviewer ac...) |


---

[← Previous](01-ai-asset-inventory.md) · [Next →](03-ai-control-catalog.md) · [Back to README](../README.md)
