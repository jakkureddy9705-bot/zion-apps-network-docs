# Commercial Routing — Client-Safe Discovery Handoffs

[Docs index](docs-index.md) · [Discovery benefits](discovery-benefits.md) · [Discovery rollout](discovery-rollout.md) · [Commercial routing](commercial-routing.md) · [Commercial questionnaire](commercial-questionnaire.md) · [App index](app-index.md) · [App interlinks](app-interlinks.md) · [Promotional overview](promotional-overview.md)

## Purpose and current boundary

The commercial coordination address for this workflow is [commercial@ziontechgroup.com](mailto:commercial@ziontechgroup.com). The [Discovery page](https://ziontechgroup.com/discovery/) describes a copy to the submitted address and to Commercial. The [showcase](https://ziontechgroup.com/apps-network-showcase/) explicitly warns that email delivery depends on the provider and recipient inbox.

This document specifies the desired workflow. It does not assert mailbox access, installed automation, successful submission, sending, delivery, a customer relationship, or marketing permission. No email is sent by publishing it.

## Routing contract

| Leg | Recipient | Permitted content | Evidence required |
| --- | --- | --- | --- |
| Client | The submitted, validated client email | The reviewed client-safe summary, assumptions, limitations, and next-step options | Leg-specific request/message identity and separately recorded delivery outcome |
| Commercial | commercial@ziontechgroup.com | The same client-safe summary and request reference | A distinct Commercial-leg receipt and outcome |
| Internal review, if separately needed | Only explicitly authorized internal reviewers | Minimum internal notes in a restricted workspace | Separate access and purpose; never leak into the client-safe payload |

Use two separately tracked copies, rather than silently adding CC/BCC recipients or forwarding a private conversation. Keep the summary version consistent between the client and Commercial legs. Do not add partner recipients, subscribe the submitter to marketing, create a deal, or trigger follow-up automatically.

## Request state machine

`RECEIVED → VALIDATED → SUMMARY_GENERATED → REVIEWED → ROUTING_READY`

From ROUTING_READY, each leg has its own sequence:

`NOT_QUEUED → QUEUED → PROVIDER_ACCEPTED/SENT → DELIVERED`, with distinct `FAILED`, `BOUNCED`, `UNKNOWN`, `SUPPRESSED_DUPLICATE`, and reviewed-retry states.

A provider may not supply delivery evidence. Keep UNKNOWN when appropriate; do not relabel SENT as DELIVERED. A completed client leg does not imply a completed Commercial leg, and vice versa.

## Minimum routing ledger

| Field | Purpose | Handling rule |
| --- | --- | --- |
| request_id | Stable logical request identity | Persist before generating side effects |
| created_at / updated_at | Audit chronology | Use explicit timezone, preferably UTC |
| schema_version / summary_version | Trace the validated answers and reviewed result | Increment on substantive revision |
| client_email_validation | Record validation outcome | Do not guess or repair an address without confirmation |
| review_status / reviewer_role | Show human review and open questions | Unknown remains unassigned or pending |
| payload_hash | Confirm the intended client-safe summary | Compare the common summary, not hidden internal notes |
| client_leg_status / commercial_leg_status | Separate operational progress | Never collapse into one green checkbox |
| provider_message_id per leg | Identify provider acceptance | Not delivery proof by itself |
| delivery_evidence per leg | Record delivery/bounce evidence, if available | Keep unavailable evidence explicit |
| idempotency_key per leg | Prevent repeat side effects | Use request + summary version + recipient leg |
| failure_code / retry_count / next_action | Recover without duplicate sends | Retry only a failed leg under approved rules |
| retention_class / access_review | Constrain data exposure | Set approved values before live intake |

## Failure and exception playbook

1. Reject missing or invalid recipient data before queueing a message.
2. Stop routing when summary generation or review fails; keep a safe request status and route the issue to the assigned operator.
3. If one leg succeeds, preserve its receipt and retry only the failed leg after review.
4. If provider acceptance is recorded but delivery is unknown, report that distinction; do not resend merely to make a dashboard green.
5. Suppress duplicate clicks and retries using the persisted idempotency key, not only a short browser timer.
6. Keep security, privacy, abuse, opt-out, and bounce exceptions separate from normal commercial qualification.
7. Record the actual outcome and next owner. A template, draft, or label is not a configured enforcement mechanism.

## Client-safe summary outline

- Request reference and the single process under review.
- Current systems, known constraints, and the accountable business role.
- Baseline facts versus assumptions and missing information.
- Relevant planning resources or catalog routes, with their evidence/maturity limitations.
- A bounded recommendation: proceed, measure first, wait, or do not automate.
- The free scope, optional separately scoped work, and a clear stop option.
- How to ask a correction or discuss the next step with Commercial.

Exclude credentials, internal supplier costs, confidential margin calculations, private memory links, unrelated personal correspondence, and unverified identity or consent claims.

## Message template — drafting reference only

**Subject:** Zion Discovery | {request_id} | {process_short_name}

Hello,

Here is the client-safe Discovery summary for the process described in request {request_id}. It separates known facts, assumptions, and remaining questions, and includes relevant reading resources. The questionnaire and this summary are free under the documented rollout. Any consulting trial or implementation requires a separately agreed scope; there is no automatic paid conversion.

Recommendation: {proceed / measure first / wait / do not automate}.

To correct the brief or discuss next steps, contact commercial@ziontechgroup.com.

This is a template stored as documentation, not a message that was sent or an authorized future campaign.

## Commercial and operational release

Questionnaire completion is not a qualified lead, buying intent, a contract, or marketing consent. Track optional marketing separately from requested result delivery. Verify current offer wording before quoting; source pages contain inconsistent Discovery pricing descriptions.

Before a purchase, reservation, supplier commitment, or field dispatch, obtain written client confirmation of scope and price, the corresponding PO, and a separate Zion operational release, as described in the public showcase. Do not invent costs, taxes, availability, coverage, acceptance, or PO status. The [questionnaire tracker](commercial-questionnaire.md) and [rollout gates](discovery-rollout.md) define the supporting records; the [app index](app-index.md) does not establish delivery capability.
