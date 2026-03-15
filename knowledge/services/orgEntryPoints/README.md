These are the entry-point services that business, product, engineering, HR, procurement, security, support, and operations teams are most likely to request directly.
# Entry Points

## Get privacy advice and triage

- Description: Front-door intake for privacy questions, early guidance, and routing when a requester knows something is privacy-relevant but does not yet know which service should handle it.
- When to use:
  - The input is a question about the following to the extent it relates to privacy or data protection:
    - what does the law say?
    - what are company rules on X?
    - can we do X?
  - The subject matter is in conception stage and only broad responses are needed.
- When not to use:
  - Does not relate to personal data
  - Despite the similarity to privacy impact review service, this service is a "dry run", meaning that it will not create artifacts, schedule controls etc
  - The project is in design or later stages, in which case the privacy impact review service shall be used.
- Relative path: `getPrivacyAdviceAndTriage.md`

## Request a privacy impact review

- Description: Runs a structured privacy review for a new or changed initiative to identify privacy risks, findings, mitigations, and evidence needs.
- When to use:
  - We launch a new or alter an existing project, feature
  - The subject matters creates and edits privacy context:
    - categories of personal data
    - categories of data subjects
    - purpose of processing
    - source of data
    - recipient of data
    - storage periods
    - storage location
  - The processing is novel, high-impact, hard to explain, or likely to affect individuals materially.
  - A team needs documented risk decisions before launch or rollout.
- When not to use:
  - See scope of privacy advice and differentiation with this service
- Relative path: `requestPrivacyImpactReview.md`

## Request privacy training or awareness support

- Description: Delivers privacy training, awareness sessions, issue-driven briefings, and audience-specific learning support.
- When to use:
  - A team needs onboarding, refresher training, or role-based privacy guidance.
  - A new project is launched and requires onboarding to company rules and processes.
  - A business area wants reusable privacy learning content or a live training session.
- When not to use:
  - The need is a case review or project assessment rather than training.
- Relative path: `requestPrivacyTrainingOrAwarenessSupport.md`

## Review a vendor, partner, or data-sharing arrangement

- Description: Reviews an external relationship or disclosure arrangement, linking the counterparty, role, flows, transfer mechanism, and due diligence expectations.
- When to use:
  - Procurement or a business owner wants to onboard, renew, or materially change a vendor or partner.
  - Personal data will be disclosed externally or accessed by another party.
  - Cross-border transfer or contractual role questions need privacy review.
  - No influence if the counterparty is a group member, review still required. 
- When not to use:
  - No external party or disclosure is involved.
  - Does not concern personal data.
- Relative path: `reviewVendorPartnerOrDataSharingArrangement.md`

## Handle a privacy request or complaint

- Description: Manages intake and coordination for formal privacy requests or complaints received from individuals or external parties.
- When to use:
  - A team receives an access, deletion, correction, portability, objection, restriction, or similar request.
  - An individual raises a complaint about privacy practices, notices, or use of data.
  - A case needs assignment, deadline tracking, and documented response handling.
- When not to use:
  - The need is to design a general notice or preference experience rather than handle a live case.
  - The issue is a live incident that needs breach response.
- Relative path: `handlePrivacyRequestOrComplaint.md`

## Report a privacy incident or suspected breach

- Description: Opens and manages a privacy incident record so the team can investigate, contain, assess harm, and make notification decisions.
- When to use:
  - Personal data may have been exposed, lost, misdirected, altered, or improperly accessed.
  - A suspected privacy event needs investigation even if facts are still incomplete.
  - A third party, system, or team reports a privacy-relevant security or handling issue.
- When not to use:
  - The need is preventive design review before launch.
  - The issue is only a policy question with no live or suspected event.
- Relative path: `reportPrivacyIncidentOrSuspectedBreach.md`

# Terminology

## Personal Data

Personal data is any information relating to an identified or identifiable natural person - in practice, a living individual. The legal idea is deliberately broad. A person may be identified directly, for example by name or passport number, or indirectly, for example through an IP address, cookie ID, location trail, employee number, or a combination of data points that together single them out. The key question is not whether the data looks obviously private, but whether it relates to a person and can be used to distinguish, trace, profile, or otherwise connect information back to that person. Under the GDPR framework, data that has been pseudonymised or encrypted still counts as personal data if re-identification remains possible, while truly irreversible anonymised data does not.

Examples of personal data therefore include the obvious things - a person’s name, home address, personal email address, ID number, passport number, social security number, school grades, hospital records, bank account details, a photograph, a vehicle registration number, browsing history, IP address, cookie ID, phone advertising ID, and location data. Even information that seems technical or impersonal can still be personal data when it is tied to a user, device, or account. A useful way to think about it is this: if the information tells you something about a specific person, lets you pick them out from others, or can reasonably be linked back to them, it is personal data.

What is not personal data is information that cannot relate to an identifiable individual. Classic examples are a company registration number, a generic corporate email like info@company.com
, or data that has been anonymised so thoroughly that no person can realistically be identified from it. Likewise, aggregated statistics such as "18% of customers prefer option A" are not personal data if no individual can be singled out from them. The boundary matters: a random code or dataset may look anonymous at first, but if the organisation can link it back to a customer, employee, patient, or user, it is still personal data. So the dividing line is identifiability - if a real person is reasonably linkable, the GDPR treats the information as personal data; if not, it does not.