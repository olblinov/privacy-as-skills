# Privacy Team ORM Model (Table Format)

## Modeling principles

| Decision | Why |
| --- | --- |
| Center the model on `ProcessingActivity` | Most privacy-team work clusters around processing, purpose, legal basis, notices, risks, requests, and incidents |
| Reuse `Party` for all actors | Internal owners, DPOs, processors, vendors, regulators, auditors, and external stakeholders share common identity fields |
| Represent proof as `Evidence` | Privacy programs need artifacts for audits, assessments, requests, complaints, and control testing |

## Domain map

| Domain | Primary models | Model folder |
| --- | --- | --- |
| Governance and accountability | `Organization`, `BusinessUnit`, `Party`, `PrivacyProgram`, `Policy`, `LegalRequirement`, `RegulatoryChange` | `governance-and-accountability/` |
| Training and awareness | `TrainingProgram`, `TrainingAssignment` | `training-and-awareness/` |
| Processing inventory and data mapping | `SystemAsset`, `ProcessingPurpose`, `LegalBasis`, `RetentionRule`, `DataSubjectCategory`, `DataCategory`, `DataElement`, `ProcessingActivity`, `ProcessingPartyRole`, `DataFlow`, `TransferMechanism` | `processing-inventory-and-data-mapping/` |
| Third-party management | `ThirdPartyEngagement` | `third-party-management/` |
| Notices, preferences, rights, and complaints | `Notice`, `PreferenceRecord`, `DataSubjectRequest`, `Complaint` | `notices-preferences-rights-and-complaints/` |
| Assessments, risk, controls, and monitoring | `Assessment`, `AssessmentFinding`, `PrivacyRisk`, `MitigationAction`, `Control`, `Evidence`, `Metric` | `assessments-risk-controls-and-monitoring/` |
| Incidents and breach response | `Incident`, `BreachNotification` | `incidents-and-breach-response/` |

## Governance and accountability

| Model | Purpose | Key relations | Model file |
| --- | --- | --- | --- |
| `Organization` | Root entity for the privacy program | `business_units[]`, `privacy_programs[]`, `policies[]`, `legal_requirements[]` | `governance-and-accountability/Organization.yaml` |
| `BusinessUnit` | Organizational subdivision owning systems and activities | `organization`, `systems[]`, `processing_activities[]`, `policies[]` | `governance-and-accountability/BusinessUnit.yaml` |
| `Party` | Reusable actor for people and organizations | `processing_roles[]`, `third_party_engagements[]`, `training_assignments[]` | `governance-and-accountability/Party.yaml` |
| `PrivacyProgram` | Program-level governance, ownership, and strategy | `organization`, `program_owner`, `dpo`, `policies[]`, `controls[]`, `metrics[]` | `governance-and-accountability/PrivacyProgram.yaml` |
| `Policy` | Internal privacy policies and procedures | `organization`, `business_unit`, `privacy_program`, `legal_requirements[]`, `controls[]`, `evidence[]` | `governance-and-accountability/Policy.yaml` |
| `LegalRequirement` | Law, regulation, contractual, or code obligation | `policies[]`, `controls[]`, `processing_activities[]`, `notices[]` | `governance-and-accountability/LegalRequirement.yaml` |
| `RegulatoryChange` | Tracks new laws, guidance, and implementation decisions | `legal_requirements[]`, `assessments[]`, `evidence[]` | `governance-and-accountability/RegulatoryChange.yaml` |

## Training and awareness

| Model | Purpose | Key relations | Model file |
| --- | --- | --- | --- |
| `TrainingProgram` | Privacy training definition by audience and cadence | `assignments[]`, `evidence[]` | `training-and-awareness/TrainingProgram.yaml` |
| `TrainingAssignment` | Tracks who must complete training | `training_program`, `party` | `training-and-awareness/TrainingAssignment.yaml` |

## Processing inventory and data mapping

| Model | Purpose | Key relations | Model file |
| --- | --- | --- | --- |
| `SystemAsset` | System, product, service, or environment used in processing | `processing_activities[]`, `controls[]`, `data_flows_as_source[]`, `data_flows_as_target[]` | `processing-inventory-and-data-mapping/SystemAsset.yaml` |
| `ProcessingPurpose` | Catalog of approved purposes for processing | `processing_activities[]` | `processing-inventory-and-data-mapping/ProcessingPurpose.yaml` |
| `LegalBasis` | Permitted basis for processing under a jurisdiction | `processing_activities[]`, `preference_records[]` | `processing-inventory-and-data-mapping/LegalBasis.yaml` |
| `RetentionRule` | Retention and deletion schedule | `processing_activities[]`, `data_elements[]` | `processing-inventory-and-data-mapping/RetentionRule.yaml` |
| `DataSubjectCategory` | Groups of people whose data is processed | `processing_activities[]` | `processing-inventory-and-data-mapping/DataSubjectCategory.yaml` |
| `DataCategory` | Type/classification of personal data | `data_elements[]`, `processing_activities[]` | `processing-inventory-and-data-mapping/DataCategory.yaml` |
| `DataElement` | Concrete field or attribute used in processing | `data_category`, `processing_activities[]`, `retention_rule?` | `processing-inventory-and-data-mapping/DataElement.yaml` |
| `ProcessingActivity` | Central record of a processing operation | `purpose`, `legal_basis`, `retention_rule`, `data_subject_categories[]`, `data_categories[]`, `data_elements[]`, `party_roles[]`, `data_flows[]`, `notices[]`, `assessments[]`, `risks[]`, `incidents[]` | `processing-inventory-and-data-mapping/ProcessingActivity.yaml` |
| `ProcessingPartyRole` | Joins a party to an activity with a role | `processing_activity`, `party` | `processing-inventory-and-data-mapping/ProcessingPartyRole.yaml` |
| `DataFlow` | Transfer or disclosure path inside or outside the organization | `processing_activity`, `source_system`, `target_system`, `from_party`, `to_party`, `transfer_mechanism` | `processing-inventory-and-data-mapping/DataFlow.yaml` |
| `TransferMechanism` | Cross-border or regulated transfer mechanism | `data_flows[]`, `third_party_engagements[]` | `processing-inventory-and-data-mapping/TransferMechanism.yaml` |

## Third-party management

| Model | Purpose | Key relations | Model file |
| --- | --- | --- | --- |
| `ThirdPartyEngagement` | Vendor, processor, or partner relationship under privacy oversight | `party`, `business_owner`, `transfer_mechanism`, `processing_activities[]`, `assessments[]`, `incidents[]` | `third-party-management/ThirdPartyEngagement.yaml` |

## Notices, preferences, rights, and complaints

| Model | Purpose | Key relations | Model file |
| --- | --- | --- | --- |
| `Notice` | Privacy notice used at collection or disclosure points | `processing_activities[]`, `legal_requirements[]`, `evidence[]` | `notices-preferences-rights-and-complaints/Notice.yaml` |
| `PreferenceRecord` | Consent, opt-out, or other processing preference | `processing_activity`, `legal_basis`, `notice` | `notices-preferences-rights-and-complaints/PreferenceRecord.yaml` |
| `DataSubjectRequest` | Formal rights request workflow | `processing_activity`, `assigned_party`, `evidence[]` | `notices-preferences-rights-and-complaints/DataSubjectRequest.yaml` |
| `Complaint` | Concern or complaint about privacy practices | `processing_activity`, `assigned_party`, `related_request?`, `evidence[]` | `notices-preferences-rights-and-complaints/Complaint.yaml` |

## Assessments, risk, controls, and monitoring

| Model | Purpose | Key relations | Model file |
| --- | --- | --- | --- |
| `Assessment` | PIA, DPIA, vendor review, audit, or similar evaluation | `processing_activity`, `system_asset`, `third_party_engagement`, `lead_assessor`, `findings[]`, `risks[]`, `evidence[]` | `assessments-risk-controls-and-monitoring/Assessment.yaml` |
| `AssessmentFinding` | Specific issue found in an assessment | `assessment`, `owner`, `mitigation_actions[]`, `evidence[]` | `assessments-risk-controls-and-monitoring/AssessmentFinding.yaml` |
| `PrivacyRisk` | Privacy harm or compliance risk to be treated | `processing_activity`, `assessment`, `owner`, `controls[]`, `mitigation_actions[]`, `evidence[]` | `assessments-risk-controls-and-monitoring/PrivacyRisk.yaml` |
| `MitigationAction` | Action item created from risk or finding | `privacy_risk`, `assessment_finding`, `control`, `owner` | `assessments-risk-controls-and-monitoring/MitigationAction.yaml` |
| `Control` | Privacy or privacy-relevant safeguard | `privacy_program`, `control_owner`, `policies[]`, `legal_requirements[]`, `processing_activities[]`, `systems[]`, `risks[]`, `evidence[]` | `assessments-risk-controls-and-monitoring/Control.yaml` |
| `Evidence` | Artifact proving design, operation, review, or response | `policy?`, `training_program?`, `notice?`, `assessment?`, `assessment_finding?`, `privacy_risk?`, `control?`, `request?`, `complaint?`, `regulatory_change?` | `assessments-risk-controls-and-monitoring/Evidence.yaml` |
| `Metric` | Periodic privacy-program metric | `privacy_program` | `assessments-risk-controls-and-monitoring/Metric.yaml` |

## Incidents and breach response

| Model | Purpose | Key relations | Model file |
| --- | --- | --- | --- |
| `Incident` | Privacy incident or breach record | `processing_activity`, `system_asset`, `third_party_engagement`, `response_owner`, `notifications[]`, `evidence[]` | `incidents-and-breach-response/Incident.yaml` |
| `BreachNotification` | Notification sent to regulators, individuals, or others | `incident`, `recipient` | `incidents-and-breach-response/BreachNotification.yaml` |