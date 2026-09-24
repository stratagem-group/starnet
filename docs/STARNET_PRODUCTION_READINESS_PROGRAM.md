# StarNet Production Readiness Program

**Organization:** Stratagem Group  
**Repository:** `stratagem-group/starnet`  
**Status:** Active  
**Version:** 1.0  
**Working branch:** `stratagem/bootstrap-audit`  
**Date:** 2026-09-23

## Objective

Prepare the Stratagem fork for dependable production use as an agentic operations environment while preserving upstream provenance, truthful telemetry, existing test discipline, and separation from Otto, Echo Lite, and Nomentis.

Production work follows the AI Systems Operating Charter in `docs/AI_SYSTEMS_OPERATING_CHARTER.md`.

## Production gates

The fork is not production-ready until all of the following are proven on the fork:

- clean baseline test receipts
- clean source startup
- at least one provider completes an end-to-end agent run
- delegation/sub-agent path is verified
- memory lifecycle is verified
- execution profiles and privilege escalation are understood and tested
- secrets/keychain handling is reviewed
- updater/release infrastructure is isolated from upstream
- backup/restore is exercised
- failure/recovery behavior is documented
- at least one real Stratagem workflow runs successfully under bounded permissions

## Sprint 1 — Baseline, isolation, and safety

### Task 1 — Capture fork baseline and provenance

Priority: P0

Work:
- record current upstream lineage and fork head
- preserve MIT/NOTICE attribution
- document upstream remote convention
- identify baseline version and default branch

Acceptance:
- provenance is documented in-repo
- no ambiguity exists about upstream vs Stratagem-owned changes

### Task 2 — Prove baseline test suite

Priority: P0

Run:
- `npm run test:fast`
- `npm run test:http`

Acceptance:
- full receipts captured against an exact commit SHA
- any failures are recorded as pre-existing or fork-induced
- no behavioral modification proceeds until failures are classified

### Task 3 — Prove source runtime

Priority: P0

Run:
- `npm start`
- verify UI on `127.0.0.1:8787`
- verify loopback API health
- verify shutdown/restart behavior

Acceptance:
- clean start/stop/restart observed
- runtime workspace path identified
- no unexplained startup errors

### Task 4 — Isolate fork from upstream release infrastructure

Priority: P0

Audit:
- Tauri updater endpoint
- updater public key
- release workflow targets
- release scripts
- README download links
- release runbook
- source/release repository assumptions

Acceptance:
- no Stratagem-built binary can accidentally consume or publish to upstream release infrastructure
- replacement signing/update plan documented before any distributable build is produced

### Task 5 — Review secrets and credential storage

Priority: P0

Audit:
- native keychain implementation
- legacy secret migration
- provider keys
- messaging-channel tokens
- MCP credentials
- OAuth state/callback handling
- environment-variable exposure

Acceptance:
- secret locations and trust boundaries documented
- no plaintext credential persistence discovered without explicit remediation
- connector/provider credentials never exposed to the renderer without a documented reason

### Task 6 — Map and test execution/permission profiles

Priority: P0

Audit:
- informed-consent broker
- standing grants
- master bypass
- unrestricted host access
- local execution
- Docker Safe Cell
- SSH execution
- autonomous and channel-origin runs
- delegated worker inheritance

Acceptance:
- effective authority for each execution posture is documented
- restricted modes cannot silently become Full Access
- autonomous workers cannot self-approve prohibited actions
- revocation takes effect as designed

### Task 7 — Prove one provider end-to-end

Priority: P0

Work:
- configure one supported provider
- create/run one agent
- exercise streaming response
- exercise one safe tool
- verify cost/run ledger
- restart and verify persistence

Acceptance:
- one provider path is proven from UI to provider to tool to persistent run record

### Task 8 — Prove memory and delegation

Priority: P1

Work:
- verify memory creation/proposal behavior
- verify recall
- verify edit/forget
- verify provenance/origin
- delegate to a persistent worker
- spawn an ephemeral sub-agent
- verify completion/error visibility

Acceptance:
- memory lifecycle is inspectable and reversible
- delegation corresponds to real worker execution
- no phantom/faked worker state

### Task 9 — Establish Stratagem operating defaults

Priority: P1

Define:
- default execution profile
- Full Access escalation policy
- initial model/provider policy
- agent budget defaults
- unattended-work defaults
- connector defaults
- audit/log retention expectations

Acceptance:
- a new agent receives conservative defaults without manual hardening
- privileged modes require explicit escalation

### Task 10 — Build first production workflow

Priority: P1

Candidate:
- GitHub repository health / issue triage workflow

Pattern:
- lead triage
- specialist investigation
- optional code worker
- QA/review worker
- human approval before consequential write/merge

Acceptance:
- workflow completes repeatedly
- permissions and costs remain bounded
- failure is visible
- output is reviewable
- human approval remains authoritative

## Change sequencing

1. Documentation and fork hygiene
2. Baseline testing
3. Runtime proof
4. Release/update isolation
5. Secret/security audit
6. Permission/execution audit
7. Provider proof
8. Memory/delegation proof
9. Operating-default changes
10. Production workflow

Behavioral changes before Steps 2–3 are limited to fixes required to make the unmodified baseline runnable and must be clearly identified as such.

## Production definition

For Stratagem, “production” means safe and dependable for real internal operational work. It does not imply public commercial distribution.

Public distribution adds additional gates:

- fork branding and artwork rights
- unique desktop identifier
- publisher/signing identity
- fork-owned updater signing key
- fork-owned release channel
- installer signing/notarization
- clean-install validation
- public privacy/support documentation
- distribution-specific threat review
