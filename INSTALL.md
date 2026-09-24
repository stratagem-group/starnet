# Installing / Running the Stratagem Fork

> **Internal engineering status:** this fork does not yet have an approved desktop distribution.
> Do not treat upstream StarNet installers as builds of the Stratagem fork.

## Run from source

Requirements:

- Node.js 18+ (Node.js 22 matches upstream CI)
- Git
- Rust + Tauri prerequisites only when building the desktop shell

Clone the Stratagem repository:

```bash
git clone https://github.com/stratagem-group/starnet.git
cd starnet
```

Run the local sidecar/UI:

```bash
node sidecar/index.js
```

Open:

```text
http://127.0.0.1:8787
```

For desktop development:

```bash
npm ci
npm run desktop:dev
```

For local desktop build testing:

```bash
npm run desktop:build
```

Local builds are engineering artifacts only until the Stratagem release/signing chain is established.

## Local models

Ollama can be used without a cloud API key. Install Ollama, pull a model, and select OLLAMA under
the provider settings. The application expects Ollama on `127.0.0.1:11434`.

## Desktop distribution gate

A Stratagem desktop release must not be published until all of the following exist and are validated:

- derivative product name
- derivative logo and artwork
- unique desktop identifier
- Stratagem-controlled publisher/signing identity
- Stratagem-owned updater signing key
- Stratagem-owned release repository/channel
- Windows signing configuration
- macOS Developer ID/notarization configuration where applicable
- updated privacy/support documentation
- clean-install and update-path test receipts

The current updater configuration has been severed from the upstream release repository and points
at the reserved Stratagem release location. That location must remain unpublished until the fork-owned
signing key and release process are established.

See:

- `docs/STRATAGEM_RELEASE_ISOLATION_AUDIT.md`
- `docs/STARNET_PRODUCTION_READINESS_PROGRAM.md`
- `docs/SPRINT_1_BACKLOG.md`

## Data location warning

The current code still uses the historical `ai.skynet.harness` application-data identifier for
backward compatibility. Do not rename or migrate that identifier casually; it is part of the runtime
state/keychain migration audit and will be changed only with an explicit migration plan.
