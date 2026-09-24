# Stratagem Fork Release / Update Isolation Audit

**Status:** Initial audit complete  
**Date:** 2026-09-23  
**Scope:** non-runtime inspection of distribution coupling

## Finding 1 — Desktop updater is hard-wired to upstream

`src-tauri/tauri.conf.json` currently embeds:

- upstream updater public key
- endpoint: `https://github.com/androoAGI/starnet-releases/releases/latest/download/latest.json`

Impact:
A derivative desktop build produced without changing this configuration would participate in the upstream update trust/channel assumptions.

Disposition:
Do not distribute a Stratagem-built desktop binary until the endpoint and signing chain are replaced.

## Finding 2 — Release workflow is upstream-specific

`.github/workflows/release-train.yml` explicitly stages release artifacts to `androoAGI/starnet-releases` and expects upstream-specific release secrets and signing infrastructure.

Impact:
The workflow is not safe to use as Stratagem's release path without modification.

Disposition:
Keep the workflow for study only until the Stratagem release design is approved.

## Finding 3 — Release scripts default to upstream

`scripts/release-cut.mjs` defaults `STARNET_RELEASES_REPO` to `androoAGI/starnet-releases`.

The release verification/runbook paths are likewise written around the upstream distribution repository and upstream operator process.

Impact:
A careless local release command could target assumptions that belong to upstream.

Disposition:
After baseline runtime proof, replace hard-coded/default upstream release targets with explicit Stratagem-owned configuration and fail closed when fork release configuration is absent.

## Finding 4 — README still advertises upstream binaries

The fork README currently displays upstream release badges, download links, support contact, and clone instructions.

Impact:
Users could mistake upstream binaries for Stratagem builds or mistake the fork for an endorsed upstream distribution.

Disposition:
Add an immediate fork-status notice. Remove/replace public distribution language during rebrand.

## Finding 5 — Branding is not MIT-licensed

`NOTICE.md` states that the StarNet name, logo, station artwork, sprites, and broader brand identity are owned by Andrew Sims and are not licensed with the MIT code.

Impact:
A derivative may use and modify the MIT-licensed code, but public distribution must use its own name, logo, and artwork and must not present itself as StarNet or as endorsed by upstream.

Disposition:
Rebrand is a hard public-distribution gate.

## Finding 6 — Upstream attribution must remain

`LICENSE` retains Andrew Sims's 2026 copyright and the MIT license.
`NOTICE.md` contains third-party attribution and licensing information.

Disposition:
Preserve these notices. Add Stratagem-specific notices separately rather than replacing upstream attribution.

## Required production changes after baseline proof

1. choose derivative product name
2. replace product artwork/branding required by NOTICE
3. choose unique desktop identifier
4. create fork-owned release repository
5. generate and securely escrow fork-owned updater signing key
6. replace updater public key and endpoint
7. replace upstream release workflow destinations
8. replace release-script defaults
9. rewrite release runbook for Stratagem
10. revise README/install/privacy/support references
11. validate upgrade path only after fork-owned signing/update chain exists

## Current release posture

**DO NOT DISTRIBUTE FORK-BUILT DESKTOP BINARIES.**

Source development and internal runtime testing may proceed.
