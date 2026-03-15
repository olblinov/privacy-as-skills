# tl;dv review for B2B partner meeting transcription

Service used: `Review a vendor, partner, or data-sharing arrangement`

Outcome: `Conditionally approve`

tl;dv can be used for selected meetings with prospective B2B partners if Acme treats tl;dv as a processor, keeps the workflow narrowly scoped, and adds controller-side guardrails before go-live.

## Why this is not a full rejection

- The DPA is broadly aligned with GDPR Article 28 processor terms: it covers purpose, nature of processing, categories of data, data subjects, confidentiality, security, subprocessor controls, assistance, breach notice, audit support, and return or deletion.
- The default hosting footprint is largely in Europe, with Google, Wasabi, Hetzner, and Mistral locations described in Germany, Finland, and Sweden.
- The DPA gives advance notice and objection rights for subprocessor changes and says non-EU transfers require the 2021 SCCs.

## Why this is not an unconditional approval

- The DPA says Anthropic in the United States may be used for summaries when selected by the client. That creates an optional restricted-transfer path that is not approved for this use case yet.
- The DPA puts legal basis, transparency, and rights-handling obligations on Acme as controller. The contract does not solve how partner representatives are informed before recording starts.
- The service can capture broad meeting content: voice, image, screen shares, and anything said during the call. Without usage rules, this is easy to over-collect.

## Decision

Approve only if all of the following are in place before use:

1. Keep tl;dv in an EEA-only configuration and disable Anthropic or any other non-EEA summary feature.
2. Use it only for selected partnership meetings where recording is genuinely needed for follow-up.
3. Add a meeting invite notice and opening script that say the call will be recorded and transcribed, why, how long the record is kept, and how a participant can object or request a non-recorded alternative.
4. Set retention to 30 days or less and verify that a single meeting recording and transcript can be deleted quickly.
5. Restrict access to the internal attendees and business owner; do not use recordings as a default shared knowledge base.
6. Do not use this workflow for HR, whistleblowing, special-category, or similarly high-sensitivity discussions.

## Likely legal framing

- Likely GDPR legal basis: `legitimate interests` for documenting business development discussions and follow-up actions.
- Separate recording-law checks may still apply depending on where participants are located. If local law or meeting context makes consent the safer route, obtain explicit agreement before recording or do not record.

## Key findings

### 1. Optional US summaries are the main contractual risk

The DPA explicitly says Anthropic in the United States may be used to generate summaries if Acme selects that option. For this review, that feature should stay off. No US transfer record has been created in the structured data because that path is out of scope for the approval. If the business later wants it, run a separate transfer review and document the mechanism and supplementary measures first.

### 2. Participant notice is an internal obligation, not a vendor deliverable

For prospective partner meetings, the biggest practical compliance issue is not the Article 28 wording. It is whether Acme gives a clear notice before recording starts and has a workable fallback if the other side does not want a recorded call.

### 3. Retention and deletion need operational proof

The DPA supports deletion at end of service and mentions deletion of disputed meetings when consent is withdrawn. Acme still needs its own short retention setting and a tested deletion workflow for individual recordings.

## Residual risk view

- `High if US summary features are enabled without a separate transfer review`
- `Medium with the conditions above applied`
- `Not acceptable for sensitive meeting types or blanket always-on recording`

## Structured records created

Core records created for the review, plus supporting findings, mitigation, control, and evidence entries:

- `knowledge/data/thirdPartyEngagement.csv`: `tpe-tldv-partner-meetings`
- `knowledge/data/processingActivity.csv`: `pa-b2b-partner-meeting-transcription`
- `knowledge/data/assessment.csv`: `asmt-tldv-2026-03`
- `knowledge/data/privacyRisks.csv`: `pr-tldv-partner-overcapture`, `pr-tldv-optional-us-transfer`, `pr-tldv-deletion-and-rights-lag`
