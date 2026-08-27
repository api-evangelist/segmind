---
name: segmind-async-inference
description: >-
  Run any model on the Segmind AI Gateway using the v2 asynchronous contract — submit,
  poll, fetch — and read cost and remaining credits off the result. Use this instead of
  the blocking v1 call for anything that can take more than ten seconds (video, upscaling,
  LLMs).
api: segmind:segmind-inference-api
operations:
  - invokeModelAsync
  - getRequestStatus
  - getRequestResult
  - getUserCredits
source: https://docs.segmind.com/docs/serverless-api/async-inference
generated: '2026-08-27'
method: generated
---

# Run a Segmind model asynchronously

Every operationId below is verified against `openapi/segmind-inference-api-openapi.yml`
and `openapi/segmind-account-api-openapi.yml` in this repo. The semantics are taken from
https://docs.segmind.com/docs/serverless-api/async-inference.

## Before you start

- Authenticate with an API key in the **`x-api-key`** header. The gateway does **not**
  accept the key as a bearer token — sending it in `Authorization` returns `401` on every
  endpoint.
- Base URL is `https://api.segmind.com`.
- Optionally call `getUserCredits` (`GET /v1/get-user-credits`) first. It runs no model
  and costs nothing, and a model request is refused with `406` when the balance is below
  the cost of the model being called — not only when it reaches zero.

## Steps

1. **Submit** — `invokeModelAsync` (`POST /v2/{model_name}`). The body is the model's own
   parameter set; open the model's API tab on segmind.com to see it. The response is
   always `status: QUEUED` and carries `request_id`, `status_url` and `response_url`.
2. **Poll** — `getRequestStatus` (`GET /v2/requests/{request_id}/status`). Use this, not
   the result endpoint, while waiting: it returns status and metrics without the output
   payload. Default to a 1 s interval; back off to 5–10 s for long video or LLM jobs.
   Status moves `QUEUED` → `PROCESSING` → `COMPLETED` | `FAILED`.
3. **Fetch** — `getRequestResult` (`GET /v2/requests/{request_id}`) once status is
   `COMPLETED`. Read `output` (present for every modality), plus `images[]`, `video` or
   `audio` depending on what the model produces.
4. **Record the output URL immediately.** The request record expires well before the
   output file does; once it expires all three poll endpoints return `404` and the URL
   cannot be recovered from the API. Output files are retained 7 days.

## Rules that matter

- **Do not retry a successful submit.** Each `POST /v2/{model_name}` creates a new
  `request_id` and a second billable job. There is no idempotency key on this API. A `5xx`
  *on the submit itself* is the only thing worth retrying; every `GET` is safe to retry.
- **Use an overall deadline of ≤ 600 s** for most models, and prefer webhooks over polling
  for fire-and-forget jobs.
- **Billing:** only HTTP 200 is charged. A failed job returns `422` with
  `status: FAILED`, an `error` string, timings, and **no** `cost` field. Read
  `metrics.cost` and `metrics.remaining_credits` off the result rather than diffing your
  balance.
- **Output URLs are public.** They need no API key — treat them as unlisted share links,
  not as access control.
- **Fetching results needs `images.segmind.com` allowed** through any egress allowlist or
  CSP; allowing the API host alone is not enough.

## Errors you will actually hit

| Code | Means |
|---|---|
| `401` | Key missing (header never arrived) or key rejected — the two 401 bodies differ. |
| `403` | The model is restricted for your team. Retrying will not help. |
| `404` | No such model, or the request record has expired. |
| `406` | Most often a missing or wrong `Content-Type`; also insufficient credits, a rejected parameter value, or a team spend limit. |
| `410` | The model has been retired or deprecated. Not charged. |
| `422` | v2 only — the job ran and failed. Read `error`. |
| `429` | Rate limit exceeded. See `rate-limits/segmind-rate-limits.yml`. |

See also `errors/segmind-error-codes.yml` and `conventions/segmind-conventions.yml` in
this repo.
