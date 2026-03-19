# Privacy as Skills

This repository captures how a privacy team works as a structured knowledge base. The content in `knowledge/` links privacy services, operational models, and flat-file example data so the team can describe work in a way that is reusable by people and AI agents.

## What is in `knowledge/`

- `knowledge/services/` describes the privacy service catalog, including six org-facing entry points such as privacy advice, impact reviews, vendor reviews, rights handling, training support, and incident intake.
- `knowledge/models/` defines 36 YAML models across seven domains, covering governance, training, processing inventory, third-party management, notices and rights, risk and controls, and incidents.
- `knowledge/data/` contains 24 CSV datasets that instantiate the model with sample organizational, legal, processing, vendor, assessment, and risk records.

## How the repository is organized

The knowledge base is designed to connect intake to execution:

1. A stakeholder starts from a service entry point in `knowledge/services/orgEntryPoints/`.
2. That service maps to one or more domain models in `knowledge/models/`.
3. The models can be populated or updated through the flat-file records in `knowledge/data/`.

The model is centered on `ProcessingActivity`, which ties together purpose, legal basis, retention, data categories, parties, data flows, assessments, risks, notices, requests, and incidents.

## Domain coverage

- Governance and accountability: organizations, business units, parties, policies, legal requirements, regulatory changes, and program structure.
- Training and awareness: reusable training programs and assignment tracking.
- Processing inventory and data mapping: systems, purposes, legal bases, retention, data categories and elements, activities, roles, flows, and transfer mechanisms.
- Third-party management: vendor, processor, partner, and data-sharing engagements.
- Notices, preferences, rights, and complaints: notices, consent or preference records, requests, and complaints.
- Assessments, risk, controls, and monitoring: assessments, findings, privacy risks, taxonomy, mitigations, controls, evidence, and metrics.
- Incidents and breach response: incidents and breach notifications.

## Data characteristics

- The CSV data uses a sample organization (`org-acme-inc`) to show how the schema can be populated in practice.
- Several records align to GDPR-oriented obligations such as processor terms, transfer mechanisms, transparency, minimization, records of processing, and security.
- The privacy risk taxonomy is grounded in NIST Privacy Framework problematic data actions and privacy problems.

## Good starting points

- Read `knowledge/services/README.md` for the end-to-end privacy service catalog.
- Read `knowledge/services/orgEntryPoints/README.md` for the front-door workflows most teams would request.
- Read `knowledge/models/README.md` for the full model map and relationships.
- Inspect `knowledge/data/processingActivity.csv`, `knowledge/data/legalRequirement.csv`, and `knowledge/data/privacyRiskTaxonomy.csv` to see the model instantiated as flat files.

## Intended use

Use this repository to:

- document how a privacy team operates,
- build reusable prompts, skills, or workflows around privacy services,
- test privacy operating models against concrete data and schemas,
- and keep service definitions, models, and working records aligned.
