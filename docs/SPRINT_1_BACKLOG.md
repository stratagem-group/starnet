# Sprint 1 Backlog — Baseline, Isolation, Safety

**Branch:** `stratagem/bootstrap-audit`  
**Status:** Active  
**Started:** 2026-09-23

GitHub Issues are currently disabled for this repository, so this file is the authoritative Sprint 1 tracker until issue tracking is enabled.

## Status legend

- [ ] Not started
- [~] In progress
- [x] Complete
- [!] Blocked / decision required

## Execution order

### 1. Fork baseline and provenance — P0
Status: [x]

Completed:
- upstream/fork baseline pinned at `7ee93ceac14c6bcb500ab263e92186e3a2d8b5d7`
- repository transferred to `stratagem-group/starnet`
- working branch established as `stratagem/bootstrap-audit`
- package repository/homepage/issues metadata repointed to Stratagem
- AI systems charter committed
- production-readiness program committed
- workflow-routing guide committed

Recommended local remotes:
- `origin` → `https://github.com/stratagem-group/starnet.git`
- `upstream` → `https://github.com/androoAGI/starnet.git`

Acceptance:
- exact lineage is reconstructable
- baseline upstream and fork commit are identical at the point of fork

### 2. Baseline test suite — P0
Status: [ ]

Run:
- `npm run test:fast`
- `npm run test:http`

Acceptance:
- logs/receipts tied to exact commit
- failures classified before behavioral work

### 3. Source runtime proof — P0
Status: [ ]

Run:
- `npm start`
- verify `127.0.0.1:8787`
- verify health route
- verify clean stop/restart
- identify workspace/data path

Acceptance:
- clean baseline runtime observed

### 4. Release/update isolation — P0
Status: [~]

Confirmed upstream coupling:
- Tauri updater endpoint points to `androoAGI/starnet-releases`
- embedded updater public key belongs to upstream release chain
- release workflow stages drafts to upstream release repository
- release scripts default to upstream release repository
- release runbook assumes upstream repositories and upstream operator credentials
- README download links point to upstream releases

Remaining:
- design Stratagem-owned release/update channel
- generate fork-owned updater signing key
- define fork release repository
- update workflow/scripts/config after baseline runtime proof
- remove upstream distribution links from fork-facing documentation

Acceptance:
- no Stratagem binary can consume or publish through upstream release infrastructure

### 5. Secrets and credential storage — P0
Status: [ ]

Scope:
- native keychain
- legacy migration
- provider credentials
- channels
- MCP
- OAuth
- environment variables

### 6. Permission/execution profile audit — P0
Status: [ ]

Scope:
- broker
- grants
- master bypass
- unrestricted host mode
- local
- Docker
- SSH
- autonomous/channel/delegated inheritance

### 7. Provider end-to-end proof — P0
Status: [ ]

Acceptance:
- one provider, one agent, one safe tool, persisted run/cost record

### 8. Memory + delegation proof — P1
Status: [ ]

Acceptance:
- memory lifecycle proven
- persistent and ephemeral worker paths proven

### 9. Stratagem operating defaults — P1
Status: [ ]

Decide:
- default profile
- Full Access escalation
- model/provider policy
- budgets
- unattended defaults
- connector defaults
- audit retention

### 10. First production workflow — P1
Status: [ ]

Candidate:
- GitHub repository health / issue triage

Acceptance:
- repeatable, bounded, observable, human-approved consequential writes

## Distribution gate

The upstream `NOTICE.md` explicitly states that the StarNet name, logo, station artwork, sprites, and brand identity are not licensed with the MIT code.

Therefore public distribution is blocked until the fork has:
- a distinct product name
- distinct logo
- replacement artwork/sprites where required
- fork-owned desktop identity
- fork-owned signing identity
- fork-owned updater/release channel
- revised public-facing documentation

Internal source evaluation and engineering may proceed before that rebrand.
