# Discovery Rollout — Evidence-Gated Launch Plan

[Docs index](docs-index.md) · [Discovery benefits](discovery-benefits.md) · [Discovery rollout](discovery-rollout.md) · [Commercial routing](commercial-routing.md) · [Commercial questionnaire](commercial-questionnaire.md) · [App index](app-index.md) · [App interlinks](app-interlinks.md) · [Promotional overview](promotional-overview.md)

## Release position

The documentation and route review are not a live questionnaire, email-delivery, production-integration, or implementation test. No form was submitted and no email was sent by this documentation workflow. The launch plan below is a controlled operating design; its gates remain open until actual evidence is attached.

The [public Discovery page](https://ziontechgroup.com/discovery/) is Portuguese and includes seven business questions plus an email field. Reconcile the observed free versus paid offer descriptions, on-screen versus assisted-report expectations, and advertised response/diagnostic timings before a launch announcement. See [benefits and limitations](discovery-benefits.md).

## Rollout stages

| Stage | Work | Exit evidence | Accountable role | Current evidence boundary |
| --- | --- | --- | --- | --- |
| 0 — Documentation | Publish source-backed benefits, schema, routing, catalog, and copy | Readback and link-validation report | Documentation owner | Publication can be verified independently of product launch |
| 1 — Offer and governance | Confirm scope, free access, optional trial terms, language, privacy, retention, and support ownership | Approved decision log and named reviewers | Product + Commercial + privacy reviewer | Written decisions still required |
| 2 — Technical readiness | Implement validation, summary generation, review, idempotency, routing ledger, access controls, and observability | Reviewed implementation and test plan | Engineering owner | Not implemented by publishing these files |
| 3 — Controlled validation | Run separately authorized synthetic submissions and delivery tests | Per-case evidence, including both routing legs | Test/release owner | No submissions or sends performed in this workflow |
| 4 — Limited pilot | Admit only the approved audience and process scope | Signed scope, operating checklist, monitoring and rollback ownership | Commercial + operational release owner | No clients, dates, or commitments invented |
| 5 — Release and improvement | Publish approved claims and monitor real outcomes | Release decision, measured baseline, incident and change log | Product/operations owner | Not automatic on completion of documentation |

## Acceptance-test matrix

| Case | Expected control | Required evidence |
| --- | --- | --- |
| Valid questionnaire | Exactly one logical request with validated business answers | Request ID and schema-validation result |
| Invalid email | Explain the problem without sending to a guessed address | Validation response; no queued client message |
| Missing required answer | Keep useful entered data and identify the missing field | Accessible error state and corrected resubmission |
| Duplicate click or retry | Do not generate duplicate requests or repeat successful sends | Stable idempotency key and deduplicated ledger |
| Summary-generation failure | Retain request state, show a safe status, and alert the assigned operator | Failure code and controlled recovery record |
| Sensitive or unexpected input | Minimize, reject, or redact according to approved policy | Redaction/review evidence without leaked content |
| Client leg succeeds; Commercial fails | Retry only the failed leg after review | Independent statuses and preserved success receipt |
| Commercial succeeds; client fails | Do not assume the client received results | Bounce/failure record and reviewed recovery path |
| Provider accepts message | Record SENT/accepted, not DELIVERED | Provider message ID, distinct from delivery evidence |
| Browser or network interruption | Safe recovery without duplicate side effects | Retry test with stable request identity |
| Accessibility and language | Labels, keyboard use, errors, and Portuguese/English expectations are clear | Human accessibility and localization review |
| Consent and retention | Delivery purpose is distinct from optional marketing | Approved notices, access checks, and retention/deletion test |

A live test may send real messages even with fictional business answers. Obtain separate authorization for the test and actual recipient addresses. Never treat documentation approval as permission to submit forms or run outbound tests.

## Operating metrics

| Metric | Definition | Interpretation rule |
| --- | --- | --- |
| Completion rate | Valid completed requests / started questionnaires | Define a start and exclude agreed internal tests |
| Generation success | Reviewed summaries produced / valid requests | Do not count a fallback error page as a report |
| Routing success by leg | Confirmed successful leg events / attempted leg events | Report client and Commercial separately |
| Duplicate prevention | Suppressed duplicate side effects / duplicate attempts | Count attempts without resending successful legs |
| Review turnaround | Time from valid intake to human-reviewed next action | Publish measured distribution, not an invented SLA |
| Evidence completeness | Requests with required scope, review, and routing fields / eligible requests | Unknown is not zero and does not equal complete |
| Pilot outcome | Agreed KPI change relative to a measured baseline | Separate estimates from observed results |

## Release and rollback controls

Before release: assign owners; reconcile offer copy; approve privacy and retention; verify the current destination; review failure handling; obtain controlled-test evidence; document support hours and escalation; and approve the exact public copy.

If a live implementation later misroutes data, loses review controls, repeats messages, or makes unsupported claims, the release owner should follow an approved rollback plan. Potential actions include pausing intake, disabling a sending worker, or reverting copy, but none is executed or automatically authorized by this document. Preserve evidence and successful delivery records; do not silently replay or delete customer data.

## Executive decision record

| Decision | Status to record before launch | Do not substitute |
| --- | --- | --- |
| Offer, scope, language, timings | Approved / rejected / needs revision, with reviewer and date | A screenshot or historical advertisement |
| Data and access model | Approved controls and responsible reviewer | Generic security or compliance badges |
| Routing readiness | Evidence for each leg and each failure case | A submitted form or single send receipt |
| Pilot permission | Written audience, scope, acceptance, and stop conditions | A marketing CTA |
| Operational release | Separate authorized release decision | Documentation publication |

Use the [commercial questionnaire](commercial-questionnaire.md), [routing ledger](commercial-routing.md), [catalog](app-index.md), and [interlinks](app-interlinks.md) as linked references, not as substitutes for these decisions.
