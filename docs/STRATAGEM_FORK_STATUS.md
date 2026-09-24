# Stratagem Fork Status

**Repository:** `stratagem-group/starnet`  
**Upstream:** `androoAGI/starnet`  
**Baseline:** `7ee93ceac14c6bcb500ab263e92186e3a2d8b5d7`  
**Status:** Internal hardening / pre-production

## Ownership boundary

The Stratagem repository is now operationally independent from the upstream repository for ongoing development.

Stratagem-owned:
- source repository
- working branches
- package repository metadata
- release destination configuration
- release workflow activation
- production-readiness doctrine
- workflow-routing doctrine
- future product/release decisions

Preserved from upstream by design:
- Git history
- MIT license and copyright
- NOTICE and third-party attribution
- internal compatibility names/keys until an explicit migration is designed
- upstream architectural documentation retained as provenance/history

## Updater / release boundary

The fork no longer points its updater or release tooling at `androoAGI/starnet-releases`.

Reserved Stratagem release location:
`stratagem-group/starnet-releases`

The release workflow is additionally fail-closed behind the repository variable:

`STRATAGEM_RELEASE_ENABLED=true`

Until that variable is deliberately enabled and a fork-owned signing chain exists, the release train must not produce a Stratagem distribution.

## Remaining identity work

The code fork is ours; the public product identity is not yet complete.

Before distribution we still must replace:
- StarNet product name
- StarNet logo
- upstream-owned station artwork/sprites where required by NOTICE
- desktop application identifier
- updater signing key
- code-signing/notarization identities
- public support/privacy/release presentation

## Development rule

Upstream remains a source of patches and ideas, not an operational authority.

Normal developer remotes:

```text
origin   https://github.com/stratagem-group/starnet.git
upstream https://github.com/androoAGI/starnet.git
```

Upstream changes are intentionally reviewed and merged; they are not treated as automatically authoritative for the Stratagem fork.
