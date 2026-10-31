<p align="center">
  <img src="assets/banner.jpg" alt="ISO 42001 AI Governance Implementation" width="100%">
</p>

# ISO 42001 AI Governance Implementation

![ISO/IEC 42001](https://img.shields.io/badge/ISO%2FIEC-42001%3A2023-1f3864) ![NIST AI RMF](https://img.shields.io/badge/NIST-AI%20RMF-1f3864) ![EU AI Act](https://img.shields.io/badge/EU-AI%20Act-1f3864) ![Status](https://img.shields.io/badge/case%20study-fictional-5eead4)

A fictional GRC case study showing how an AI Governance Lead sets up an AI management system aligned with **ISO/IEC 42001:2023** and the **NIST AI RMF**: an AI asset inventory with lifecycle tracking, a risk register that includes bias, fairness and human oversight risks, a catalog of testable controls, and policies for responsible AI development and deployment.

## Scenario

**MindfulAI Labs** (Toronto, 200 employees) builds machine learning models for healthcare diagnostics and financial risk scoring for clients in Canada and the EU. The EU AI Act classifies its healthcare models as high-risk AI systems, and Canada's proposed AIDA is on the horizon. As **AI Governance Lead**, the task is to implement the management system, document model risk assessments including bias and fairness testing, establish human oversight for automated decisions, create the asset inventory, and develop the policies.

## At a glance

| AI assets | Risks | Controls | Policies |
|---|---|---|---|
| 5 | 6 (4 High, 2 Medium) | 10 | 4 |

## Contents

| # | Document | What it covers |
|---|---|---|
| 1 | [AI Asset Inventory](docs/01-ai-asset-inventory.md) | 5 assets: two high-risk models, the training data lake, the MLOps account and model registry, and the human oversight console |
| 2 | [AI Risk Register](docs/02-ai-risk-register.md) | 6 scored risks with a heat map: bias, automation bias, data exposure, drift, supply chain and regulatory readiness |
| 3 | [AI Control Catalog](docs/03-ai-control-catalog.md) | 10 controls with framework references, effectiveness ratings and rationale |
| 4 | [AI Policies](docs/04-ai-policies.md) | 4 policies with status, owner and review date |

The same data is in `files/` as four Excel workbooks, shaped like the forms in the GRC practice lab.

## Key findings

- **Highest risks:** [RSK-006](docs/02-ai-risk-register.md#rsk-006) (no conformity assessment for EU high-risk rules, High, score 16), then [RSK-001](docs/02-ai-risk-register.md#rsk-001) (biased results from unrepresentative training data, score 15) and [RSK-002](docs/02-ai-risk-register.md#rsk-002) (automation bias with weak human oversight, score 12).
- **Control gaps:** 3 controls are Ineffective and 2 are Not Tested, so the priority actions are [CTL-001](docs/03-ai-control-catalog.md#ctl-001), [CTL-004](docs/03-ai-control-catalog.md#ctl-004), [CTL-005](docs/03-ai-control-catalog.md#ctl-005), [CTL-006](docs/03-ai-control-catalog.md#ctl-006), [CTL-009](docs/03-ai-control-catalog.md#ctl-009).
- **Strengths:** 2 controls are Effective: the asset inventory ([CTL-008](docs/03-ai-control-catalog.md#ctl-008)) and decision logging ([CTL-010](docs/03-ai-control-catalog.md#ctl-010)).

## How the documents connect

Every record has an anchor, and each document links to the others, so a reviewer can follow one thread from asset to risk to control to policy.

**Example trace:** [RSK-001](docs/02-ai-risk-register.md#rsk-001) (biased results from unrepresentative training data) affects [AST-001](docs/01-ai-asset-inventory.md#ast-001) and [AST-003](docs/01-ai-asset-inventory.md#ast-003), is treated by [CTL-001](docs/03-ai-control-catalog.md#ctl-001), which is required by [POL-002](docs/04-ai-policies.md#pol-002). Assets list their risks and controls, risks list the controls that treat them, and controls list the policies that require them. The cross-references are a portfolio mapping created for this case study.

## Alignment with ISO/IEC 42001 and NIST AI RMF

| Topic | ISO/IEC 42001:2023 | NIST AI RMF | Where it is addressed |
|---|---|---|---|
| AI policy | Clause 5.2 | GOVERN | [POL-001](docs/04-ai-policies.md#pol-001) |
| AI risk assessment | Clauses 6.1.2 and 8.2 | MAP, MEASURE | [Risk Register](docs/02-ai-risk-register.md) |
| AI risk treatment | Clauses 6.1.3 and 8.3 | MANAGE | [Control Catalog](docs/03-ai-control-catalog.md) |
| AI system impact assessment, bias and fairness | Clauses 6.1.4 and 8.4 | MEASURE 2.11 | [RSK-001](docs/02-ai-risk-register.md#rsk-001), [CTL-001](docs/03-ai-control-catalog.md#ctl-001), [POL-002](docs/04-ai-policies.md#pol-002) |
| Human oversight | Annex A.9 (use of AI systems) | GOVERN 3.2 | [RSK-002](docs/02-ai-risk-register.md#rsk-002), [CTL-002](docs/03-ai-control-catalog.md#ctl-002), [POL-003](docs/04-ai-policies.md#pol-003) |
| AI system lifecycle and asset inventory | Annex A.6; clause 7.5 | GOVERN 1.6 | [Asset Inventory](docs/01-ai-asset-inventory.md), [CTL-007](docs/03-ai-control-catalog.md#ctl-007), [CTL-008](docs/03-ai-control-catalog.md#ctl-008), [POL-004](docs/04-ai-policies.md#pol-004) |
| Data for AI systems | Annex A.7 | MEASURE 2.10 | [CTL-003](docs/03-ai-control-catalog.md#ctl-003), [CTL-004](docs/03-ai-control-catalog.md#ctl-004) |
| Third-party and supply chain | Annex A.10 | GOVERN 6.1 | [RSK-005](docs/02-ai-risk-register.md#rsk-005), [CTL-006](docs/03-ai-control-catalog.md#ctl-006) |
| Monitoring and evidence | Clause 9.1 | MANAGE 4.1 | [CTL-005](docs/03-ai-control-catalog.md#ctl-005), [CTL-010](docs/03-ai-control-catalog.md#ctl-010) |
| Legal and regulatory obligations | Clause 4.2 | GOVERN 1.1 | [RSK-006](docs/02-ai-risk-register.md#rsk-006), [CTL-009](docs/03-ai-control-catalog.md#ctl-009) |

## What this project demonstrates

- Building an AI asset inventory with owners, classification and lifecycle stages
- Writing AI risks in a clear, testable format and scoring them with documented reasoning
- Planning bias and fairness testing, human oversight and drift monitoring as measurable controls
- Mapping controls to ISO/IEC 42001, NIST AI RMF, the EU AI Act, GDPR, SOC 2 and CIS Controls
- Keeping GRC records cross-referenced so an auditor can follow one thread end to end

## Repository structure

```
iso42001-ai-governance-implementation/
├── README.md
├── assets/banner.jpg
├── docs/
│   ├── 01-ai-asset-inventory.md
│   ├── 02-ai-risk-register.md
│   ├── 03-ai-control-catalog.md
│   └── 04-ai-policies.md
└── files/            Excel versions of the four registers
```

## Disclaimer

MindfulAI Labs is a fictional company. All assets, risks, controls, policies, owners, ratings and dates are examples created for skills practice and portfolio use. This is not legal advice or a compliance determination. Framework and law references are paraphrased pointers, so verify them against the source text before relying on them.

## Author

Augustine Ozor, AI Governance and Cybersecurity GRC. [GitHub](https://github.com/AugustineOzor) · [LinkedIn](https://www.linkedin.com/in/augustinetettehozor)
