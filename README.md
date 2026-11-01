# Segmind

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Segmind is a serverless GPU inference platform that puts 200+ generative AI models — image, video, audio, 3D and LLM — behind one REST gateway with a single API key. Calls are metered per GPU-second or per generation against a prepaid credit balance, with the cost of every request reported inline on the response. The v2 asynchronous API is a submit-poll-fetch job contract built for long-running video and upscaling work, while the v1 synchronous route remains for fast models. Alongside the gateway, PixelFlow is a visual workflow builder that chains models on a canvas and publishes any workflow as its own production REST API, and dedicated endpoints run a chosen model on reserved GPUs with autoscaling. A first-party Python SDK, a browser playground, media-editing endpoints and a weekly dated changelog round out the developer surface.

**Areas:** Artificial Intelligence · Machine Learning · Generative AI · Inference · Image Generation · Video Generation · Serverless · GPU · Workflows · Fine-Tuning

## Segmind on APIs.io

Everything profiled for Segmind is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/segmind/](https://apis.io/providers/segmind/)** — or go straight to one of the APIs or properties below.

### APIs (7)

- [Segmind](https://apis.io/apis/segmind/segmind/) — The Segmind AI Gateway — one REST surface in front of 200+ generative AI models for image, video, audio, 3D and text, authenticated with a single API key…
- [Segmind Inference API](https://apis.io/apis/segmind/segmind-inference-api/) — Synchronous (v1) and asynchronous (v2) model inference. v2 is the current contract — submit a job, poll a lightweight status endpoint, fetch the result —…
- [Segmind Account API](https://apis.io/apis/segmind/segmind-account-api/) — Read the account's spendable and free credit balance. Runs no model and costs nothing, and is the documented way to verify that an API key works.
- [Segmind Storage API](https://apis.io/apis/segmind/segmind-storage-api/) — Upload a file to Segmind Storage and get a reusable URL to pass as an image input to any model, instead of re-uploading the same file. Served from the…
- [Segmind PixelFlow Workflow API](https://apis.io/apis/segmind/segmind-workflow-api/) — Call a published PixelFlow workflow over REST. Submit to POST /workflows/v2/{slug} with the key names given to the workflow's input nodes, poll the status…
- [Segmind Dedicated Endpoints API](https://apis.io/apis/segmind/segmind-endpoints-api/) — Manage dedicated GPU endpoints programmatically — list, add, update capacity and delete. Served from a separate control-plane host and authenticated with…
- [Segmind Fine-tuning API](https://apis.io/apis/segmind/segmind-fine-tuning-api/) — DEPRECATED. Fine-tuning request management and data handling. Segmind's fine-tuning service no longer accepts new training jobs; existing fine-tuned models…

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### AsyncAPI (1)

Event-driven and webhook contracts.

- [Segmind Webhooks](https://apis.io/asyncapis/segmind/segmind-webhooks/)

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [segmind-mcp.yml](https://apis.io/servers/segmind/segmind-mcp-yml/)

#### Agentic access (1)

Which operations an agent can call, which act, and which need a human in the loop.

- [Segmind Agentic Access](https://apis.io/agentic-access/segmind/segmind-agentic-access/)

#### Collections (5)

Postman and Open Collection request collections.

- [Segmind API](https://apis.io/collections/segmind/open-segmind/)
- [Segmind Account API](https://apis.io/collections/segmind/open-segmind-account-api/)
- [Segmind Account Fine-tuning API](https://apis.io/collections/segmind/open-segmind-fine-tuning-api/)
- [Segmind Account Inference API](https://apis.io/collections/segmind/open-segmind-inference-api/)
- [Segmind Account Storage API](https://apis.io/collections/segmind/open-segmind-storage-api/)

#### Overlays (8)

OpenAPI overlays, including conversational phrasing for each operation.

- [Segmind Account Api Overlay](https://apis.io/overlays/segmind/segmind-account-api-overlay/)
- [Segmind Account Api Phrasing Overlay](https://apis.io/overlays/segmind/segmind-account-api-phrasing-overlay/)
- [Segmind Fine Tuning Api Overlay](https://apis.io/overlays/segmind/segmind-fine-tuning-api-overlay/)
- [Segmind Fine Tuning Api Phrasing Overlay](https://apis.io/overlays/segmind/segmind-fine-tuning-api-phrasing-overlay/)
- [Segmind Inference Api Overlay](https://apis.io/overlays/segmind/segmind-inference-api-overlay/)
- [Segmind Inference Api Phrasing Overlay](https://apis.io/overlays/segmind/segmind-inference-api-phrasing-overlay/)
- [Segmind Storage Api Overlay](https://apis.io/overlays/segmind/segmind-storage-api-overlay/)
- [Segmind Storage Api Phrasing Overlay](https://apis.io/overlays/segmind/segmind-storage-api-phrasing-overlay/)

#### Security (2)

Authentication, trust centre, and vulnerability disclosure.

- [Segmind Authentication](https://apis.io/security/segmind/segmind-authentication/)
- [Segmind Domain Security](https://apis.io/security/segmind/segmind-domain-security/)

#### OAuth scopes (1)

The permissions the API asks for.

- [Segmind Scopes](https://apis.io/scopes/segmind/segmind-scopes/)

#### Plans and pricing (1)

Published plans, tiers and prices.

- [Segmind Plans Pricing](https://apis.io/plans/segmind/segmind-plans-pricing/)

#### Rate limits (1)

Published request limits.

- [Segmind Rate Limits](https://apis.io/rate-limits/segmind/segmind-rate-limits/)

#### FinOps (1)

What the API costs to run, by operation.

- [Segmind Finops](https://apis.io/finops/segmind/segmind-finops/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://www.segmind.com/)
- [Documentation](https://docs.segmind.com/)
- [Getting started](https://docs.segmind.com/docs/get-started/quickstart)
- [API reference](https://docs.segmind.com/docs/serverless-api)
- [Pricing](https://www.segmind.com/pricing)
- [Sign up](https://platform.segmind.com/)
- [Support](https://docs.segmind.com/docs/get-started/support)
- [Blog](https://blog.segmind.com/feed)
- [Terms of service](https://www.segmind.com/terms)
- [Privacy policy](https://www.segmind.com/privacy)
- [GitHub](https://github.com/segmind)
- [Status](https://status.segmind.com)

## API Evangelist rating

**Kin Score 66.9** — exemplar · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 73.2 |
| Contract quality | 52.8 |
| Contract governance | 18.2 |
| Operational transparency | 73.7 |
| Developer ergonomics | 78.6 |
| Access clarity | 84.2 |

**Agent readiness 32.0** — agent-ready

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | derived (partial credit) |
| Reversibility Documented | — |
| MCP Server | — |
| Auth Clarity | bearer (partial credit) |
| Idempotency | — |
| Error Semantics | documented (partial credit) |
| OpenAPI Examples | — |
| Rate Limit Signal | documented (partial credit) |
| Event Surface Described | yes |
| Agent Skills | yes |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | — |
| Delegated Identity | — |
| Protected Resource Metadata | — |
| Dynamic Client Registration | — |
| Agentic Commerce | — |
| Pagination Ratio | na |
| Operation Distinctiveness | distinct |

**Regulatory alignment 36.4** — AI & Biometrics

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/segmind/](https://apis.io/providers/segmind/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for Segmind: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/segmind/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
