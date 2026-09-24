# Xenexus owned-service replacement and setup plan

Date: 2026-09-24
Status: SOURCE-GROUNDED SEED INVENTORY AND IMPLEMENTATION REQUIREMENTS
Source snapshot: `80990c2c786e40141a71273289237b04c5ede544`
Companion: `XENEXUS_INDEPENDENCE_WORK_HANDOFF.md`

## 1. Objective and interpretation

Remove StarNet operational dependence without losing the useful functions it supplied. “Our own” means TJ/Stratagem controls the relevant service account, configuration, authorization, data and lifecycle. Using a deliberately selected third-party model/API under our account is compatible with this goal. It does not mean rewriting model providers, OAuth standards or every commodity cloud component.

Do not replace a local component simply because its file name contains “cloud.” Do not claim an optional hosted feature is mandatory. Do not assume server-side StarNet cloud code is included in this desktop repository. Inventory the actual callers, endpoints and ownership before coding.

This document distinguishes:

- **Source confirmed:** implementation or workflow source inspected directly.
- **Documented; verify wiring:** the repository describes the behavior, but the current complete caller/endpoint path still needs review.
- **Investigation item:** not confirmed as a StarNet-hosted dependency; must not be invented or silently omitted.

No service has been provisioned by preparing this plan. No hostname, private bucket, OAuth registration, client ID, secret or signing key below should be treated as already created. Setup work is source/config preparation until the owner's account, cost and deployment boundaries are cleared.

## 2. Initial service registry

| ID | Function | Evidence level | Independent replacement | Initial posture |
| --- | --- | --- | --- | --- |
| XS-01 | Managed model gateway | Documented; verify factory/bootstrap wiring | Direct provider credentials or a private Stratagem gateway | Direct/local-only; upstream gateway unreachable |
| XS-02 | Credit wallet, metering and purchase surface | Source confirmed in `sidecar/credits.js` | Real local cost/budget ledger; shared quota service only if needed | No upstream purchases or fictitious balances |
| XS-03 | Cloud account and station/device pairing | Source confirmed in `sidecar/credits-link.js`; email/Stripe described in privacy doc | Local identity for one user; owned private identity/device registry for shared service | No upstream link/refresh/recovery |
| XS-04 | Connector OAuth registration/callback relay | Documented; inspect every provider and MCP caller | Own provider app registrations and native/direct flows where supported | Missing owned registration disables that connection honestly |
| XS-05 | Chat/channel bots and webhook transport | Documented; verify adapters | Own bots, tokens, optional bridges and callback endpoints | Off until explicitly paired to an owner |
| XS-06 | Update discovery, signing and distribution | Source confirmed | Manual internal candidate first; owned signed update service later | Checking/installing disabled until complete trust chain |
| XS-07 | Release mirror, CI artifacts and deployment | Source confirmed | Private Stratagem build/release pipeline with deliberate promotion | Upstream mirror and public publishing paths retired/gated |
| XS-08 | Durable state, backup and optional cloud sync | Local mirror documented; remote sync not established | Existing local state plus owned encrypted backup target if selected | No automatic remote sync or legacy secret import |
| XS-09 | Web search and page reading | Documented; verify current transports/fallbacks | Reviewed direct provider/self-hosted search and reader as needed | Explicit egress and data-use policy; no silent fallback |
| XS-10 | Speech, transcription and model/media downloads | Documented; current dependencies require caller audit | Explicit local or own-key speech/media services; verified local model cache | Off until selected and downloads reviewed |
| XS-11 | Catalogs, recipes, skills, manuals and extensions | Local catalogs documented; all remote feeds require investigation | Bundled reviewed catalogs; optional owned signed registry | No arbitrary remote code or upstream feed fallback |
| XS-12 | Website/demo, help, privacy and support | Source confirmed website tree and generated-copy contract | Local command manual and internal support; private demo only if useful | Upstream marketing/pricing/deployment targets removed from supported runtime |
| XS-13 | Remote control, relay or notifications beyond channels | Investigation item | Direct private access or a narrow owned relay only if genuinely required | No invented relay requirement; never expose the sidecar broadly |
| XS-14 | Diagnostics/crash reporting/analytics | Privacy document says absent; source audit still required | Redacted local diagnostics; optional owned observability | No claim of absence until current transports are inventoried |

Expand this registry when source inspection finds additional dependencies, including hidden bootstrap defaults and platform app IDs. A seed registry with 14 categories is not proof that every endpoint has been found.

## 3. Service setup and acceptance

### XS-01. Model access and optional gateway

Repository privacy documentation describes direct BYOK providers and a separate credits path that relays prompts/replies through StarNet servers. Inspect `sidecar/providers/`, bootstrap configuration, model discovery, token refresh, media/voice routes and all fallback paths. Confirm which selected-provider state can activate managed routing.

Implement direct provider mode as the default independent route. Keep existing adapter contracts where sound: text/streaming, tool calls, errors, cancellation, model discovery and cost records. Require an explicit base URL and our own credentials for custom endpoints. Support selected local models without an Internet gateway. Do not pretend a ChatGPT subscription is an API key or assume a provider permits arbitrary third-party OAuth registration.

An owned gateway is optional for centrally funded friend/device access. If needed, place it in a dedicated Stratagem account/project. Authenticate each device/user, store provider secrets server-side, allow only configured providers/models, enforce per-run and aggregate reservations, stream with bounded timeouts, propagate cancellation and reject arbitrary proxy destinations. Use narrow service identity and separate administration. Do not let model traffic or credentials fall back to StarNet on errors.

Acceptance: source trace and later egress receipt prove the exact provider destination; incorrect or missing configuration fails clearly; unknown usage is not $0; streaming/cancellation and tool schemas remain functional. Shared gateway tests must include concurrent admission, exhaustion, disconnection and ambiguous provider outcomes.

### XS-02. Cost controls instead of a commercial credit store

`sidecar/credits.js` currently expects a configured HTTP backend with `GET /v1/balance`, `POST /v1/debit`, `POST /v1/credit` and `GET /v1/history`; purchasing opens a separate browser URL. Its adapter has an inert BYOK mode. Inspect callers before changing admission.

For personal use preserve real usage records, spending ceilings, alerts and per-agent/task budgets without an upstream account or checkout requirement. Distinguish measured cost, estimates, pending settlements and unknown totals. A local budget is not a purchased wallet. Preserve telemetry field meaning, not merely field names.

If shared funding is needed, build a private quota/accounting service, not a Stripe clone. Use server-side transactional reservations and idempotent settlement IDs. Do not copy the old client optimistic-cache contract as a security boundary. Derive the account from authenticated identity; never trust a caller-supplied account ID, debit amount or refund to define financial authority. Disable public credit/grant endpoints; administrative grants are audited separately.

Acceptance: model execution works independently of purchase/subscription UI; caps survive concurrent calls; retries cannot double-debit/refund; cancellation and incomplete usage reconcile safely. No hardcoded “unlimited credit” or fake balance is an acceptable replacement.

### XS-03. Identity and device enrollment

`sidecar/credits-link.js` describes `/v1/link/start` and `/v1/link/poll`, a sidecar-held polling secret, a confirmed device token/account ID, saved link state, and desktop keychain adoption. The privacy document describes emailed account sign-in. These are cloud contracts, not evidence that a cloud backend is present in this repo.

For one local user use an isolated local installation identity; no cloud login is required merely to use the station. Remove implicit upstream linking, refresh, account recovery and account-store UI. Old tokens must never resurrect a severed link.

For shared owned services adopt an established identity implementation under our tenant/project instead of creating authentication cryptography. Use allowlisted members, scoped device tokens, short-lived access, refresh rotation or sender-constraining as appropriate, revocation and MFA/passkeys where available. A device pairing code must be short-lived, rate-limited, single-use and bound to a server-side secret; never expose the polling secret to a browser/agent. Maintain explicit enrollment consent and tested lost-device revocation. Transactional email is needed only if the chosen identity flow requires it, using our verified sender/account.

Acceptance: no StarNet-issued token, issuer or account can authenticate a Xenexus service; old links are ignored/quarantined, not adopted; expired/replayed codes fail; each friend's device is revocable independently.

### XS-04. Own connector OAuth clients and callbacks

Inventory `sidecar/mcp/`, connector catalogs, Google integrations, GitHub device flow, Spotify, provider sign-ins, dynamic client registration and native injection. Do not infer ownership from a human label. Record each real client ID, authorization/token endpoint, issuer, resource/audience, scopes, redirect and code owner without leaking secrets.

Create app registrations under TJ/Stratagem for services that require a developer client. Use the provider-supported native authorization-code/PKCE or device flow; use exact registered callbacks, external-browser sign-in and least-privilege scopes. A desktop binary cannot keep a confidential client secret. Use a private backend only when the provider actually requires one. Provider-owned officially supported clients are not automatically StarNet-owned; verify support rather than replacing IDs blindly. Where no supported independent login exists, use our own API credentials or report that integration blocked.

Store token material in the independent vault; bind callback state to the attempt, expire it, reject replay and clear superseded attempts. Validate issuer/resource and do not forward tokens across MCP servers or arbitrary redirects. Scopes should be granted incrementally; never broaden to a full account just because a narrow scope is harder to configure.

Acceptance: flow uses our registered identity, revoked credentials fail, callbacks reject mismatches, no legacy/upstream redirect survives, and declared service readiness requires actual verification. Preserve useful integrations instead of merely removing their buttons.

### XS-05. Channels, bots and notification delivery

The privacy document lists user-configured Discord, Telegram, Slack, Matrix and Signal bridge paths. This is not proof they depend on StarNet hosting. Inspect actual adapters, callback URLs and defaults.

Use our bot/app registrations and secrets. Prefer the provider's supported outbound connection/polling when it avoids exposing the host. If a callback is required, put a narrowly scoped receiver behind TLS under our account, with authentic request verification, replay protection, idempotency and limits. Use distinct allowlisted owner identities per channel. Read/write/command privileges remain separate. A remote message is not permission to bypass local approvals. Signal/Matrix bridges, if selected, need independent authentication and private access.

Acceptance: unauthorized sender, forged webhook, duplicate event and revoked bot cases fail safely; E-STOP and owner revocation prevent follow-on work; secrets do not enter transcripts or child environments.

### XS-06. Owned update trust

The candidate's `frontend/app/updates.js` still has an upstream manual fallback, while Tauri uses a Stratagem URL and an upstream-derived verification key. Treat XR-04 as an incomplete trust chain.

First implement an explicit updates-disabled state in native and frontend routes, including manual checks and install commands. Do not use a 404 URL as the safety mechanism. Retain informative installed-version/status reporting without background requests.

Later create an owned artifact bucket/release channel and independent Tauri signing key. Keep the private signing material out of app binaries, source, handoff bundles and build logs. Separate updater signatures from platform signing/notarization. Use controlled promotion, immutable artifacts, documented key rotation/recovery and a signed manifest/artifact verification flow consistent with the installed Tauri version. A GitHub private release requires an intentional client authentication design; do not embed a broad PAT in the app.

Acceptance: no request to upstream update hosts; wrong-key/tampered/unsigned artifacts refused; downgrade policy explicit; failed download/install does not erase local state. No distribution before signing and rollback are verified.

### XS-07. Build/release ownership

Inspect all `.github/workflows/`, package scripts, release helpers, source mirrors, website tasks, artifact fetches, signing expectations and default-branch controls. `sync-source-release.yml` is a separate scheduled upstream mirror and cannot be secured by gating only the release train.

Retire upstream publishing/mirroring. Rebuild private candidate artifacts under Stratagem with minimum job permissions, pinned actions and reviewed downloads. Prefer workload identity to persistent broad cloud keys where the chosen platform supports it. Keep protected manual promotion and signing separate from untrusted PR jobs. Disable public deploy schedules and upstream release destinations. Review the public default branch too: an unmerged remediation branch does not change default-branch scheduled behavior.

Acceptance: readback proves all live execution/publishing paths have intended targets and gates. No claim that an advisory PR HOLD disables GitHub Actions. Repository/network migration must preserve history and PR evidence; never delete to simulate independence.

### XS-08. Local state, backup and optional sync

The code map describes `frontend/app/cloudsave.js` as a durable sidecar mirror. Verify that implementation before inventing a cloud replacement. Keep local persistence and recovery rather than adding a backend gratuitously.

Create independent app/keychain/browser namespaces and a clean first-run profile. Existing legacy content imports require preview, explicit approval and validation; do not import credentials, standing grants, armed routines or release trust automatically. Maintain save versions, atomic writes, corruption distinction and recovery copies.

For owned off-device backup, use a dedicated private object-store prefix/account and client-side encryption with a separately protected key. Keep retention, deletion, access logging and recovery runbooks. Do not synchronise active database files while open. If multi-device sync is required, design conflict resolution, identities and schema evolution explicitly; backup is not conflict-safe sync.

Acceptance: no data/secret collision with StarNet; restart does not activate imported jobs; offline continuity works; restore and key-loss failure modes are exercised after execution approval.

### XS-09. Web search and reading

The privacy document mentions Mojeek, DuckDuckGo, Jina and optional provider web tooling. Verify all current request paths and fallbacks; these are not necessarily StarNet-hosted.

Select direct APIs under our account or explicitly approved independent keyless/local services. Self-host a reader only where justified. Make query/document destinations visible, enforce request/response limits, content-type checks, timeouts and redirect/DNS-aware anti-SSRF defenses. Untrusted pages are evidence, never authority to change policies or run commands. Do not pass authenticated private documents through public reader services without specific approval.

Acceptance: no hidden provider fallback or data relay; private/metadata address requests blocked except narrowly granted intended local endpoints; failed search is unavailable, not invented results.

### XS-10. Voice and media/model assets

The privacy document describes optional speech services and plaintext historical token caches; package metadata and source references also require a current audit of local model/speech dependencies. Inspect speech, transcription, image/media, model-download and update paths rather than trusting the old privacy list.

Keep locally supported speech/media where practical; use our own keys for selected hosted processing. Make automatic downloads explicit, pin versions/revisions and verify trusted hashes/signatures where available. Remove upstream-hosted model/voice assets or mirror permitted artifacts into our controlled storage. Respect each asset license; retain local font behavior. Disable unsupported voice integrations with a clear setup state rather than silently switching providers.

Acceptance: requests only to selected destinations, no tokens in filenames/logs, no unannounced background download; models still load offline after approved caching; local-provider failures do not activate a hosted fallback.

### XS-11. Catalogs, skills and extensions

The code map describes shared local specialty catalogs and modular tool/recipe systems. Search for remote registries, dynamically loaded packages, example URLs, source remotes and update feeds before determining what needs replacement.

Bundle reviewed catalogs first. Provide a signed/versioned private registry only when dynamic sharing is needed. Treat every imported skill, plugin, recipe, MCP command and model-generated script as untrusted input. Preserve preview/provenance, capability limits and approval. Do not let an extension change gateway destinations, grant itself access or modify mandatory policy. Pin package sources and review install scripts.

Acceptance: useful existing catalogs work offline; no upstream marketplace requirement; unsigned/unknown registry items are not automatically executed; engine and class/skin boundaries remain unchanged.

### XS-12. Website, help and support

The repository contains a marketing/pricing site, `CNAME`, public legal/help pages and generated `website/app`. The generated-copy gate exists and must be reconciled.

Keep local command documentation, version/about details, privacy disclosure and redacted diagnostic export. Remove upstream support/account deletion/pricing/checkout destinations from the supported app. Retire public demo publishing, or keep a properly generated private demo with no user credentials and explicit synthetic-data labeling. Update its build/tests deliberately, not by disabling unrelated gates.

Acceptance: Help, About, manual update, error recovery and account/settings actions do not open upstream pages. No reserved/unknown host is falsely advertised as our support service. Historical attribution remains in legal/provenance records.

### XS-13 and XS-14. Investigation gates, not invented requirements

Search for remote-owner leases, relay/tunnel endpoints, push delivery, crash upload and analytics. Classify each actual caller. The privacy document asserts no analytics/crash collection, but that is not a substitute for inspection of the current tree and dependencies.

If remote access is useful, prefer a private access boundary and distinct user identity; never port-forward the localhost agent engine. If a relay is necessary, implement only the required message channel, verify both endpoints and scopes, bound queued data and maintain revocation. Keep diagnostics local/redacted unless an owned destination is explicitly configured. Do not add telemetry merely to reproduce an upstream name.

Acceptance: a completed inventory explicitly records absence or actual replacement for each category. Observed network behavior must later match the source inventory.

## 4. Resource and ownership worksheet

Before provisioning any resource, fill out the following. Do not substitute an invented domain or another project's resource.

| Resource | Required now? | Owner input / configuration | Security condition |
| --- | --- | --- | --- |
| Private standalone source home | Strongly preferred before sensitive work | Confirm supported detach/mirror route and canonical repo | Preserve review history; explicit visibility readback |
| Application identifier and local data root | Yes | Unique documented Xenexus namespace | No legacy token/state adoption |
| Model-provider projects/accounts | For real model tests later | Select actual provider/project and scoped secret | Temporary test key first; budget controls |
| OAuth client registrations | Per enabled integration | Owner-authenticated app registration and exact callbacks | Minimal scopes; no desktop client secret |
| Cloud runtime | Only if a gateway/relay is needed | Dedicated Stratagem project/region and budget | Private admin; narrow runtime permissions |
| Identity/database | Only for shared hosted functions | Dedicated project/tenant; separate dev/prod | Tenant isolation; scoped device credentials |
| Object storage | Optional backup/update artifacts | Dedicated private bucket/prefix | Encryption, restricted access, retention |
| Domain/DNS/TLS | Only for a chosen hosted surface | Confirm owned domain and hostnames | No unused/dangling DNS; verified TLS |
| Email delivery | Only for chosen auth/notifications | Verified owned sender/account | Anti-abuse controls and no secrets in mail |
| Update/platform signing | Before distribution/update enablement | Owner-held keys and platform credentials | Separate signing environments; escrow/recovery |
| External monitoring | Optional | Owned destination and retention | Redaction; no prompts/tokens by default |

Existing connected cloud tools do not prove which account/project is approved for Xenexus. Read available projects before proposing reuse. Never put Xenexus resources into Nomentis, Echo Lite or an unrelated production project.

## 5. Completion checklist

A service category is complete only when its inventory, replacement implementation/configuration, owned identity, secret handling, continuity behavior, disable/revoke path, fail-closed behavior and evidence are recorded. `disabled_pending_replacement` is an honest interim state, not `complete`.

Every enabled feature must have a traceable dependency path. Every disabled feature must name why and what unlocks it. Every retained third-party connection must be explicitly selected and independently owned/authorized. Every removed upstream capability must be replaced locally/directly/privately, or be a deliberate nonessential product removal with owner agreement.

The source-review hold remains until the main handoff's gates are satisfied. Later testing must include no-upstream egress, failure/recovery, credential revocation, data isolation and feature continuity. “No matching brand text” alone is not proof of network independence.

## 6. Evidence and current technical references

Repository evidence, all at the pinned snapshot:

- `sidecar/credits.js`: managed credit HTTP contract, BYOK inert mode and settlement/cache behavior.
- `sidecar/credits-link.js`: device-link/start/poll, token persistence and unlink generations.
- `frontend/app/updates.js` and `src-tauri/tauri.conf.json`: manual fallback, endpoint and signing configuration.
- `.github/workflows/sync-source-release.yml`: independent scheduled artifact mirror.
- `scripts/sync-website-app.mjs`, `website/app/index.html`, website tree: generated demo and marketing/deployment surfaces.
- `PRIVACY.md`: documented outbound services, managed gateway/accounting and credential storage; verify all statements against implementation.
- `CODE_MAP.md`: navigation aid for local stores and provider/MCP/tool modules; sizes/version claims are historical, not current measurements.

Current primary-source guidance checked during handoff preparation:

- OAuth Security BCP: https://www.rfc-editor.org/rfc/rfc9700.html
- Tauri updater/signing: https://v2.tauri.app/plugin/updater/
- GitHub fork visibility/network constraints: https://docs.github.com/en/pull-requests/reference/forks

Recheck provider-specific registration and cloud deployment instructions at implementation time. No costs, service availability, provider permissions or exact deployment support have been assumed here.
