# Stratagem StarNet Fork — Baseline Audit & Modification Plan

Status: active
Owner: Stratagem Group
Upstream: androoAGI/starnet
Baseline branch: feat/harness-backend
Working branch: stratagem/bootstrap-audit
Initial fork version observed: 0.12.4

## Purpose

This fork is a standalone operational multi-agent system. It is not part of Nomentis and is not an Echo Lite integration target. It may be used in parallel while those systems are developed.

The guiding principle for this fork is pragmatic usefulness: preserve what already works, harden the dangerous edges, improve routing and operations, and avoid unnecessary architectural rewrites.

## Baseline findings

- Local-first desktop architecture with a Node sidecar and Tauri shell.
- Core runtime centers on a single sidecar process and one agent loop.
- Multi-provider support includes OpenAI-compatible providers, Anthropic, Gemini, OpenRouter, and related adapters.
- Agent workspaces, permissions, memory, schedules, channels, MCP connectors, orchestration, and persistent stores are already implemented.
- Execution backends include local host execution, Docker Safe Cell isolation, and SSH remote execution.
- Loopback API includes host/origin checks and per-launch token protection.
- Permission broker supports hard-deny, full-access bypass, persistent/session grants, safe-read auto-allow, and interactive approval.
- Full Access is intentionally extremely broad upstream and can encompass host shell, filesystem, GUI/screen/input, .env, and .git according to the upstream decision log.
- Cron, background/night-shift style operation, orchestration, and ephemeral sub-agents are already present.
- Test/QA tooling is unusually extensive and should be preserved.

## Fork strategy

### Phase 0 — Preserve provenance and establish a known-good baseline

1. Keep upstream attribution and MIT notices intact.
2. Preserve an upstream remote in normal developer clones.
3. Record the upstream baseline commit before first behavioral modification.
4. Do not change shared event/schema contracts until a concrete need is proven.
5. Run baseline tests before customization.

Required baseline checks:

- npm run test:fast
- npm run test:http
- npm start
- source UI reachable at localhost:8787
- one provider configured and exercised
- one agent created and run
- memory read/write/forget path exercised
- Docker Safe Cell exercised if Docker is available
- MCP connector path exercised
- delegation/sub-agent path exercised
- backup/restore path inspected

### Phase 1 — Fork identity and release isolation

Goal: stop accidental coupling to upstream release/update infrastructure while preserving legal attribution.

Tasks:

- update repository/homepage/bugs metadata to stratagem-group/starnet
- inspect all upstream release/update feed references before shipping a forked desktop build
- preserve NOTICE/LICENSE attribution
- identify branding/artwork that cannot be redistributed under MIT branding terms
- choose fork product name before public redistribution
- leave internal skynet.* compatibility keys alone unless a migration is justified

### Phase 2 — Security posture hardening

Goal: preserve expert power without making broad host authority the normal posture.

Proposed operating profiles:

1. ISOLATED
   - Docker Safe Cell
   - no host shell
   - no arbitrary host filesystem
   - restricted network/connectors

2. STANDARD
   - scoped workspace access
   - safe reads allowed
   - host mutations require approval

3. TRUSTED
   - selected host paths/integrations
   - standing grants allowed
   - broader execution scope

4. FULL ACCESS
   - explicit expert escalation
   - whole-host authority where supported
   - strong warning/confirmation
   - immediate revocation
   - high-visibility telemetry

Initial security tasks:

- verify current full-access activation and persistence paths
- verify master bypass cannot be model-controlled
- inspect .env/.git handling under restricted vs unrestricted modes
- verify autonomous surfaces cannot self-approve writes/exec outside explicitly authorized profiles
- verify channel-origin tasks inherit correct permission boundaries
- review API token exposure and SSE/query-token exceptions
- inspect secret storage/keychain migration
- inspect MCP credential handling and OAuth callback/state validation
- inspect update-signature and installer trust paths

### Phase 3 — Model/provider routing

Goal: make model choice operational instead of merely per-agent static selection.

Desired capabilities:

- per-agent primary/fallback provider
- task-class routing
- cheap/bulk worker model
- local/private model option
- failure fallback policy
- cost ceilings by agent and task
- provider health telemetry
- routing decisions visible in run metadata

Do not add routing until current provider adapters and fallback behavior are fully mapped.

### Phase 4 — Stratagem crew and operating model

Initial role families:

- Lead / Operations
- Research
- Analysis / Critique
- Engineering
- Security
- DevOps
- Intelligence / Monitoring
- Content
- Administrative automation

Roles should be templates, not always-on agents. Each role should define:

- model policy
- execution profile
- tool grants
- memory scope
- spending ceiling
- allowed connectors
- unattended-work eligibility

### Phase 5 — Operations dashboard and observability

Goal: make the system easy to trust and operate.

Priorities:

- consolidated run/activity timeline
- per-agent cost and budget
- provider/model health
- permission grants and escalations
- background task health
- failed/stalled delegation visibility
- connector health
- storage/backups status
- restart/recovery truth

Preserve StarNet's core rule: UI claims must be backed by runtime evidence.

### Phase 6 — Useful autonomy

Only after baseline reliability and security are proven.

Candidate routines:

- research monitoring and delta briefs
- GitHub issue triage and reproduction
- scheduled repository health checks
- content preparation workflows
- low-risk administrative routines
- recurring intelligence summaries

Autonomous mutation should require an explicit profile or standing grant. Silent escalation is forbidden.

## Things we will not do

- integrate Echo Lite into this fork
- use this fork as the Nomentis architecture
- port Nomentis cognitive architecture into StarNet
- rewrite working subsystems only for architectural purity
- make outside agent frameworks foundational to Nomentis
- weaken truthful telemetry for spectacle
- remove upstream attribution required by license

## Immediate engineering backlog

P0
- establish baseline commit and branch
- verify repo metadata after organization transfer
- run test:fast
- run test:http
- run source sidecar
- prove one provider + one agent path
- inspect secrets/keychain path
- inspect update/release feed coupling

P1
- fork-specific metadata
- fork-specific updater/release isolation
- security profile design
- Full Access escalation UX
- provider routing design
- initial crew templates
- local model/Ollama path verification

P2
- per-agent budget controls
- consolidated ops dashboard
- MCP administration improvements
- routine templates
- audit timeline improvements
- backup/export workflow

P3
- GitHub engineering workflows
- research workflows
- email/calendar integrations where appropriate
- content/social workflows
- mobile control/messaging

P4
- long-running autonomous workflows
- self-evaluation/retry policy
- smarter delegation/routing
- cross-agent work products
- fleet health and recovery

## First modification rule

No behavioral changes until the fork passes a clean baseline run and the baseline test receipts are captured.
