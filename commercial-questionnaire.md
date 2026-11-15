# Commercial Questionnaire — Intake Schema and Tracking Specification

[Docs index](docs-index.md) · [Discovery benefits](discovery-benefits.md) · [Discovery rollout](discovery-rollout.md) · [Commercial routing](commercial-routing.md) · [Commercial questionnaire](commercial-questionnaire.md) · [App index](app-index.md) · [App interlinks](app-interlinks.md) · [Promotional overview](promotional-overview.md)

## Scope and source

The reviewed [Discovery page](https://ziontechgroup.com/discovery/) labels its questionnaire as seven questions, then displays seven business questions and an eighth email-destination field. This specification preserves that distinction: **seven business answers plus one email field**. The live page is Portuguese. This English documentation is a planning and tracking specification, not a deployed translation or a tested form.

No real questionnaire submissions, customer records, leads, consent records, or sales opportunities are created by this document.

## Field dictionary

| Key | Source question | Source options or expected value | Validation and handling |
| --- | --- | --- | --- |
| industry | What is your sector? | Field Service/MSP; healthcare; finance/FinOps; energy; retail/e-commerce; other | Use an explicit allowed value; avoid collecting sensitive industry records |
| main_challenge | What is the biggest challenge now? | Support overload; SLA/reliability; cloud/operating cost; sales/lead generation; data/reporting | Capture the stated challenge, not inferred buying intent |
| company_size | Company size? | 1–10; 11–100; 101–1,000; 1,000+ | Preserve the selected band; do not infer an exact headcount |
| desired_horizon | When do you want results? | Days; weeks; this quarter | Preference only; not a reserved delivery date or SLA |
| ai_maturity | Do you already use AI tools? | Not yet; some; many | Self-report; not a technical or compliance assessment |
| priority_outcome | Priority result? | Save time; reduce costs; increase revenue; reduce risk | A goal, not a guaranteed or achieved outcome |
| deployment_preference | Deployment preference? | SaaS; our cloud; on-prem/hybrid | Preference, not evidence of an available connector or deployment package |
| client_email | Where should results be sent? | A valid submitted email address | Validate before routing; do not add CC/BCC or marketing enrollment |

For this operating design, the seven business fields and the email field must pass validation before any delivery side effect. Final required/optional UI behavior, language, accessibility, notices, and retention still need a product/privacy review. Do not claim that the observed page already enforces these rules.

## Request tracking table design

| Group | Fields | Operational meaning |
| --- | --- | --- |
| Identity | request_id, source_url, received_at_utc, schema_version | One logical request, not one record per button click |
| Business answers | industry, main_challenge, company_size, desired_horizon, ai_maturity, priority_outcome, deployment_preference | Preserve the submitter's actual selections |
| Scope | process_summary, known_systems, assumptions, missing_evidence | Optional follow-up only when appropriate; minimize data |
| Validation | email_validation, required_fields_status, privacy_notice_version | Readiness to process, not marketing permission |
| Review | review_status, reviewer_role, reviewed_at_utc, recommendation | Separate generation from human review |
| Summary | summary_version, client_safe_payload_hash | Trace the reviewed result sent to both destinations |
| Client route | client_leg_status, client_message_id, client_delivery_evidence | Distinguish queued, accepted, delivered, failed, and unknown |
| Commercial route | commercial_leg_status, commercial_message_id, commercial_delivery_evidence | Independently track commercial@ziontechgroup.com |
| Exceptions | failure_code, duplicate_of, retry_count, next_action, next_owner_role | Recover without repeating successful side effects |
| Governance | retention_class, restricted_access, correction_or_deletion_request | Apply approved policy and record actual actions |

The new tracker starts without imported client rows. An empty tracker does not mean Zion has no historical requests; it means this workflow has not audited or imported them. Keep old mailbox/CRM history outside the public repository.

## Status definitions

| Status | Meaning | Must not mean |
| --- | --- | --- |
| Received | Input reached the intake system | Valid, reviewed, qualified, or delivered |
| Needs correction | Required data is missing or invalid | A guessed address or silently edited answer |
| Ready for review | Validation and generation completed | Commercial approval or operational release |
| Reviewed | A reviewer accepted the client-safe content | Authority to perform paid work |
| Routing partial | Only one required leg has succeeded | End-to-end completion |
| Sent, delivery unknown | Provider accepted the message without delivery proof | Confirmed recipient receipt |
| Complete for intake scope | Required review and routing evidence meet the defined acceptance rule | Contracted revenue, implementation, or customer success |
| On hold | A named evidence or approval gap remains | A fabricated deadline or implicit acceptance |

## Review checklist

- [ ] The record contains one stable request ID and the correct schema version.
- [ ] Business preferences are not recast as verified requirements or commitments.
- [ ] Email validation is complete and delivery purpose is clear.
- [ ] The current free/paid Discovery wording is reconciled before customer promises.
- [ ] Summary assumptions, limitations, and relevant [catalog records](app-index.md) are visible.
- [ ] The client and Commercial legs use the same reviewed client-safe summary version.
- [ ] Duplicate suppression, one-leg failure, bounce, generation failure, and correction flows are covered.
- [ ] Marketing opt-in, if ever requested, is separate, optional, and not inferred from result delivery.
- [ ] Access and retention are approved before live data collection.

## Measurement and handoff

Report valid intake count, missing-field rate, review turnaround, generation success, and separate delivery-leg outcomes using explicit denominators and time windows. Do not populate dashboard numbers from synthetic examples or historical memories of a different workspace.

Follow [commercial routing](commercial-routing.md) for the ledger and failure handling, [rollout](discovery-rollout.md) for authorized tests and release gates, [benefits](discovery-benefits.md) for client expectations, [interlinks](app-interlinks.md) for relevant reading paths, and [promotional copy](promotional-overview.md) for language that does not overstate readiness.
