# Xenexus independence and hardening: Work execution handoff

Date: 2026-09-24
Owner: TJ / Stratagem Group
Status: READY FOR SOURCE REMEDIATION; FIRST-RUN HOLD REMAINS
Repository: `stratagem-group/starnet`
Working branch: `stratagem/bootstrap-audit`
Draft PR: `#1`, HOLD: Xenexus X1–X6 — pre-test review
Reviewed runtime candidate: `80990c2c786e40141a71273289237b04c5ede544`
Inherited baseline: `7ee93ceac14c6bcb500ab263e92186e3a2d8b5d7`

## 1. Mission and authority

TJ has authorized repository remediation and confirmed full write access to Stratagem. This is an execution assignment, not a request for another proposal. Inspect, repair, add regression coverage, commit bounded changes, and report evidence. Do not ask TJ to reauthorize ordinary source edits already covered by this assignment.

Latest binding instructions:

- Cut ALL operational connections to StarNet. A cloud service, account, credential, hosted dependency or update channel needed by Xenexus must be owned/controlled by TJ or Stratagem, or be a deliberately configured direct third-party service under their own account.
- Replace useful StarNet-dependent functionality with our own equivalent. Disabling it temporarily is containment, not completion. Record how continuity is restored.
- Secure and harden the system before TJ's first test. Review all source, not only the rebrand diff. Do not silently narrow this to the 53 changed files.
- Preserve the existing live station, look/layout/style, rooms, corridors, agent characters, movement, pathing, workstations, capabilities, conveyors, routing, camera and CRT behavior. Do not replace the engine with a static dashboard.
- Preserve the approved Xenexus blue/gold/black identity and richer original key art. Current lightweight SVGs and reused neutral sprites are integration scaffolding, not proof that final approved artwork has been integrated.
- Xenexus is for personal/internal use, possibly close friends, not a commercial SaaS launch. Do not build a payment business just to reproduce upstream packaging.
- Xenexus remains operationally separate from Otto, Echo Lite and Nomentis. No Nomentis/Echo Lite secrets, architecture, repositories or research enter this task.

Authority is scoped to this project. No production deployment, public release, paid provisioning, domain purchase, real-provider call, broad credential access, history rewrite, force push, repository deletion, or merge is authorized by this handoff. Prepare provider registrations/infrastructure definitions; ask only for genuinely necessary owner authentication, account selection, costs, or consequential changes. Never place secret values in chat, commits, artifacts or command transcripts.

## 2. Current reality, not prior completion language

X1–X6 edits exist at the candidate SHA. They have NOT been certified by a clean runtime, test, build, migration or visual receipt. The previous review read the full 53-file delta and selected surrounding code, not every inherited source file. No application tests were executed in that review.

At handoff preparation GitHub reports PR #1 open, draft, unmerged; its head remains the candidate SHA. The source repository is public. A later handoff-only commit will change the branch tip without changing the reviewed runtime candidate. Re-read the current tip and diff it; do not assume the old SHA remains HEAD.

Do not treat mergeability as a quality signal or a HOLD title as enforced branch protection. Recheck permissions, workflow settings and branch state through actual readbacks. Never claim a control was disabled because a document says so.

Read first:

1. This handoff and `XENEXUS_SERVICE_REPLACEMENT_PLAN.md` in the same directory.
2. PR #1 reviews, especially review IDs `5306273228` and `5307109989`.
3. `docs/XENEXUS_FRONTEND_PRESERVATION_DOCTRINE.md`, `docs/XENEXUS_FRONTEND_BUCKET_MAP.md`, and the X1–X6 implementation documents.
4. `docs/AI_SYSTEMS_OPERATING_CHARTER.md`, `docs/SPRINT_1_BACKLOG.md`, `docs/STRATAGEM_FORK_STATUS.md` and release-isolation audit. Several contain outdated claims; correct them against code.
5. The attached original `XENEXUS_PRETEST_REVIEW_80990c2.md` and `XENEXUS_REVIEW_LEDGER_80990c2.json`. Their 15 finding IDs must survive in the remediation ledger.

The package includes these original reports under `evidence/`. If attachments are unavailable, use the PR reviews plus the complete finding register below. Do not stall on attachment retrieval when the repository is readable.

## 3. First actions in Work

1. Verify the actual repository and authenticated permissions. Inspect `git status`, current branch, remotes and HEAD. Preserve unrelated local work. Use an isolated worktree when needed; never reset somebody else's checkout.
2. Fetch the Stratagem working branch, not the repository's default branch. Confirm the candidate is an ancestor and classify every newer commit. Continue on the same branch when clean and uncontended. For parallel work, create bounded `stratagem/remediate-*` branches from the verified tip, then integrate through one coordinator. Never use `viral-fawkes/*`.
3. Inspect all workflows BEFORE pushing code. Prevent unintended release, website publication, mirror synchronization and unreviewed execution. A commit skip marker is only an additional safeguard, not the control itself. Avoid automatic test execution while the source-review hold applies.
4. Create `docs/security/XENEXUS_REMEDIATION_LEDGER.json` and `docs/security/XENEXUS_SOURCE_COVERAGE.md`. Record scanned, reviewed, corrected, statically checked, tested and blocked as DIFFERENT states. Every entry needs paths, SHA, disposition and acceptance evidence.
5. Build a complete tracked-file and dependency inventory. Include native code, scripts, test lists, public website mirror, generated files, package locks, binary downloads, containers and service definitions. Track omitted generated/binary content explicitly rather than claiming a line review of it.
6. Begin containment and narrow remediation. Do not install dependencies, execute repository scripts/tests, start the app, authorize OAuth or contact model providers until the appropriate review gate has been cleared.

Reading files, Git inspection and self-authored static text-analysis tools are allowed. They are not application/test execution. Parser-only checks can be proposed separately; do not run arbitrary project code under a misleading “static check” label.

## 4. What “all connections cut” means

Remove executable dependence on upstream domains, cloud account systems, credit gateways, device linking, OAuth registrations, callback relays, update signing roots, release mirrors, support endpoints, demo deployments, remote content/catalogs and hidden fallback hosts. Include native Rust paths and subprocess/browser navigation paths, not just JavaScript fetch.

Scan for direct URLs, split/constructed URLs, aliases, environment defaults, service account IDs, audience/issuer values, OAuth client IDs, package/repository destinations, release workflow targets and bootstrap injection. Review config override precedence and restored-state paths. A blank default or absent URL does not prove a service cannot be revived by an old environment variable or saved record.

Preserve LICENSE, required NOTICE/third-party attribution and provenance. Historical text and inert data-schema names are not network connections. Keep an exact, justified historical-reference allowlist; do not exempt an entire source directory. Remove active upstream remotes/automation when independence is established, but preserve the baseline provenance locally. Do not fetch future upstream changes automatically.

Migrate native identity, keychain service, browser storage, filesystem root, locks and IPC credentials coherently. Select a unique application identifier and document it; do not claim ownership of an unverified domain. No silent import, token resurrection or auto-resume of legacy routines. Importing old layouts/content must be explicit, secret-free by default and leave automation/grants off.

Do not impersonate StarNet's OAuth client, forge an entitlement, return fake credit balances, or relabel an upstream service as Xenexus. No replacement-ready message until our actual implementation exists and passes its contract gate.

## 5. Required finding-by-finding remediation

| ID | Required correction | Closure evidence |
| --- | --- | --- |
| XR-01 | Reconcile Full Power with hardline enforcement. Inventory downstream bypasses as well as `permissions.js`; make mandatory boundaries non-bypassable and retain explicit, revocable approvals for permitted work. Default first-run posture must not be Full Power. | Source trace through admission, registry, filesystem, shell, desktop, delegation and revocation; policy matrix; negative-test source followed by later execution receipts. |
| XR-02 | Establish independent native/data/keychain/origin identity. Isolate locks, workspaces, browser storage, credentials and recovery. No automatic legacy adoption or armed-job import. | Namespace/migration matrix, clean-profile design, explicit import rules, later old/new profile non-interference receipts. |
| XR-03 | Retire/gate every publishing route, especially `.github/workflows/sync-source-release.yml`. Its scheduled upstream mirror is independent of `release-train.yml`. | Inventory of all workflow/script entry points and actual disabled/fail-closed readbacks. No upstream artifact publication through any path. |
| XR-04 | Remove upstream update fallback and verification trust. Disable checking AND installation in frontend/native code until an owned signing/distribution chain is configured. A nonexistent URL is not a control. | Config and callable-route review, no fallback to upstream, later tampered-signature/wrong-key/downgrade tests and offline startup proof. |
| XR-05 | Resolve public source versus internal-use intent and fork-network attachment. Prefer a private standalone Stratagem home. Preserve history/review records; do not delete the source fork or force-push as a shortcut. | Owner-approved target; supported migration route; readback of visibility, origin, permissions, protections and new canonical location. Pending owner decision must stay open. |
| XR-06 | Repair branding-dependent tests and add substantive regression coverage. Test the actual Xenexus assets, not unused upstream files. Preserve mask parsing, geometry, accessibility, z-order and dock wiring checks. | Reviewed test changes, new regression source for identity/portrait/defaults/isolation and later test receipts. No wholesale suppression of old gates. |
| XR-07 | Resolve stale `website/app` deliberately. Prefer retiring unused public publishing scope; if a private demo remains, generate it correctly from the source. | Supported-surface manifest; generator and matching test/build updates; zero active upstream deployment targets. |
| XR-08 | Fix `AgentPortraits.paint()` fallback state: stable request identity separate from resolved source, cached failure/fallback, bounded or explicit retries, handlers before requests, cleanup and stale-callback guards. | Regression source for failed explicit portrait, repeated paints, disconnected/reused nodes, rapid identity change and fallback failure. |
| XR-09 | Replace first-canvas-only dossier image callbacks with shared load promises/current-consumer notifications. Guard agent, canvas and render generation. | Regression source for re-open/rebuild while pending, concurrent consumers, stale selection and failure. No engine changes. |
| XR-10 | Restore `ACTIVE COMMS` or equally scoped wording; do not imply all background work is counted. Preserve unavailable/stale distinction. | Every displayed metric mapped to its real source; confirmed COMMS-only count tests. |
| XR-11 | Reconcile dock labels, window titles, help, dynamic title writers, tutorial and prop descriptions. Keep stable handler/schema keys unless independently migrated. | Complete entry-to-title map; no contradictory visible directions; title tests updated meaningfully. |
| XR-12 | Replace plain clone/run instructions with reviewed branch-and-SHA selection and isolated profile prerequisites. Default branch is not this candidate. | Installation doc tied to an approved future test SHA; HOLD clear before runnable onboarding instructions. |
| XR-13 | Label temporary SVGs, reused sprites, portrait plumbing, approved artwork and original sprite delivery separately. Preserve all approved art; do not claim the X3B pack exists. | Asset provenance/reference manifest, integration checklist, explicit remaining art work and later actual screenshots. |
| XR-14 | Rebrand native window/tray/installer identity together with XR-02. Inspect explicit `.title("StarNet")`, icons, resource paths, executable names and signing assumptions. | Native identity/build matrix; later clean-install receipt. |
| XR-15 | Complete inherited-source, dependency/provenance and history-secret review. Close gaps with actual inspection, not the absence of PR changes. | Full coverage ledger with exclusions, dependency/license/SBOM records, reviewed external downloads, secret findings handled without exposure, independent review. |

Priority order: containment and identity (XR-02/03/04/05), service cutover and security policy (XR-01/15), UI/data correctness (XR-08/09/10/11), tests/generation/docs/assets (XR-06/07/12/13/14). Dependencies may justify reordering, but no finding vanishes from the ledger.

## 6. Replacement program and continuity

Execute the companion service plan. It starts with source-confirmed managed credits, cloud device pairing, updates and release mirroring, plus documented provider/channel/search/voice/credential dependencies. It is a seed inventory, not an exhaustive endpoint audit.

For each dependency record: source location and SHA; trigger; boot/background behavior; endpoint/redirect chain; upstream owner; data sent; credential owner; requested scopes; fallback behavior; replacement owner; local/direct/owned-hosted disposition; setup; cost approval; privacy impact; rollback; acceptance evidence; current status.

Preserve useful function before removing its old interface. An old adapter may remain as an internal, disabled compatibility seam during development, but the supported runtime must not reach upstream through it. Unconfigured replacements return explicit unavailable/configuration-required states, not success, empty data or fabricated balances. No degraded feature can quietly send traffic back to StarNet.

Default target: local station and memory/workflows; direct provider calls using our credentials or explicitly selected local models; own connector registrations; local truthful budgets. Optional shared auth/gateway/storage/remote services only when justified. There is no assumption that StarNet's server-side backend source is present in this repository.

## 7. Hardening acceptance requirements

### Host and tool authority

Keep mandatory boundaries before privilege bypass. Prevent agent modification of policy, grants, release trust, credentials, escape routes or audit settings. Delegation inherits no more authority than its parent. Unattended grants are explicit and revocable; failure must never increase privilege. Review shell access separately from filesystem tool jails: a local host shell is not sandboxed merely because file APIs are jailed. Constrain it through the actual execution backend. E-STOP must stop work and remain effective across restart. Use time, concurrency, process-tree, memory and spend limits.

### Network and secrets

Audit all egress, including Node fetch/http/https/WebSocket, DNS/redirects, native clients, browser opens, tool subprocesses, MCP and downloaded packages. A JavaScript denylist alone cannot enforce a boundary against an unrestricted shell. Enforce a narrow policy at process/container/network boundaries too. First-run profile has no general Internet access; later allow explicit providers/connectors. Preserve anti-SSRF protection for metadata/private addresses, including redirects and DNS rebinding. Allow intended local services through specific grants, not broad private-network exemptions.

Use per-launch local API credentials, strict host/origin checks, narrow method-specific exceptions and controlled native IPC. Do not expose the sidecar port to friends or the public Internet. Secrets remain in an independently namespaced OS vault or appropriately encrypted store; no silent plaintext fallback in supported source or desktop mode. Keep failed/corrupt vault state distinct from an empty vault. Logs, prompts, subprocess environments, diagnostic packages and backups must not leak tokens. Disk encryption and access controls complement, not replace, application protections.

### Owned services

Separate development and production resources. Adopt short-lived scoped credentials, least-privilege service identities, authenticated administration, rate limits, TLS, audit logs and tested revocation. Reject token passthrough to arbitrary MCP resource servers. Bind OAuth to exact clients, resources, redirects, state and PKCE as appropriate. Validate callback expiry and replay. The owner must not share one unrestricted token across friends.

### Data and delivery

Keep atomic saves, recovery copies and explicit schema versions. Encrypt backups before remote storage; exercise recovery later before relying on them. Do not copy OAuth/provider secrets in an ordinary layout export. Pin build inputs and review install hooks and executable downloads. Use private preview artifacts, protected release environments and separate signing keys. Never disable verification to make a build or updater work.

## 8. Review and execution gates

A. Source remediation gate: all files inventoried; all applicable findings corrected or explicitly blocked; service/egress inventory complete; no active StarNet paths; source contracts reviewed; no production data/credentials; regressions written. Record exact commit and peer review. This is not runtime certification.

B. Isolated verification gate: after presenting A, obtain TJ's explicit approval for the first isolated execution. Review scripts before running them. Use clean disposable workspace/browser profile/container, no real tokens and denied external egress. Run syntax/build/fast/HTTP and relevant regressions in deliberate order. Separate baseline defects, fork regressions, environment limitations and unverified cases. Do not run tests as a side effect of a source push before approval.

C. Controlled functional gate: explicit temporary provider/connector credentials, real but bounded spend, failure injection, revocation, restore, restart, no-upstream packet/egress receipts and visual checks. Confirm rooms, agents, conveyors, paths, camera and CRT remain intact. Check denied actions, stale telemetry, portrait failures, resize/theme/saved-layout behavior.

D. Personal production gate: only after source plus runtime evidence, owned-service continuity, backup recovery, secret rotation, update posture and owner sign-off. Friends require separate identities/permissions/data before access. Do not advertise full security or production readiness from static review alone.

## 9. Required outputs from Work

- Remediation ledger for XR-01 through XR-15, with correction SHA, verification type, evidence and blockers.
- Complete source-coverage and external-service/egress inventories.
- Owned-service setup runbooks and infrastructure-as-code where needed; no secrets in source.
- Native/storage/keychain/legacy import migration plan and implementation.
- Focused fixes and regression coverage in small commits, coordinated without hot-file conflicts.
- Updated privacy, installation, fork-status and art-completion documentation.
- Review checkpoint with exact next test candidate SHA, rollback instructions, residual risks and the narrow approval needed for isolated execution.

Persist progress to repository documents at each logical checkpoint. Continue through ordinary source remediation without asking “shall I proceed?” after every file. Stop only for a true security/permission/cost boundary, a concurrent change conflict, an owner decision, or the first execution gate. Never report started work as completed, queued work as running, or source inspection as a passing test.

## 10. Evidence anchors

Repository source is authoritative over this handoff when facts differ; document the discrepancy.

- PR: https://github.com/stratagem-group/starnet/pull/1
- Reviewed source: https://github.com/stratagem-group/starnet/tree/80990c2c786e40141a71273289237b04c5ede544
- Upstream baseline is provenance only; no new upstream fetch is required for this task.
- Official OAuth guidance: https://www.rfc-editor.org/rfc/rfc9700.html
- Native OAuth guidance: https://www.rfc-editor.org/rfc/rfc8252.html
- Official Tauri update signing: https://v2.tauri.app/plugin/updater/
- GitHub fork visibility: https://docs.github.com/en/pull-requests/reference/forks

This handoff is a scoped execution contract and a continuity record. It does not claim a Work session has started, that source fixes have been applied, or that replacement cloud infrastructure has been provisioned.
