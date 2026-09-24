# Xenexus Frontend Bucket Map

**Status:** Approved implementation map  
**Date:** 2026-09-23  
**Branch:** `stratagem/bootstrap-audit`  
**Governing doctrine:** `docs/XENEXUS_FRONTEND_PRESERVATION_DOCTRINE.md`

## Objective

Rebrand StarNet into **Xenexus AI Operations Command** primarily by changing the skin, feel, terminology, and visual assets while preserving the existing layout, interaction model, world engine, runtime mechanics, and truthful telemetry.

This map divides the frontend into three buckets:

1. **KEEP UNCHANGED** — core mechanics and state logic
2. **RESKIN / REBRAND** — visual presentation, art, palette, labels, chrome
3. **SURGICALLY MODIFY** — small presentation adapters where Xenexus needs existing runtime state surfaced differently

The rule is: **do not rebuild what already works.**

---

# Bucket 1 — KEEP UNCHANGED

These modules are runtime/mechanics infrastructure. They should not be modified merely to achieve the Xenexus look.

## World / station mechanics

### `frontend/app/world.js`
**KEEP core behavior unchanged.**

Preserve:
- multi-room world rendering
- corridors / door traversal
- hero and crew bodies
- walking / pathing
- activity state
- workstation behavior
- conveyor simulation
- routing-plan consumption
- live route state
- camera pan / zoom / follow
- world rebuild behavior
- CRT pipeline mechanics
- honest runtime event projection

Allowed later:
- read-only theme inputs
- asset-path changes
- small rendering constants if purely visual

Do not rewrite its state model.

### `frontend/app/worldmodel.js`
Preserve:
- station graph/model
- room/prop semantics
- capability mapping
- placement rules
- path topology

Do not duplicate this data model in a new dashboard layer.

### `frontend/app/stationbake.js`
Preserve:
- procedural station geometry
- room/corridor baking
- geometry projection
- collision/path structure

Visual assets may change around it; bake semantics stay.

### `frontend/app/conveyor.js`
Preserve:
- real work-item movement
- conveyor lifecycle
- routing behavior

Only appearance of belts/items may change.

### `frontend/app/pipeline.js`
Preserve:
- workflow/routing semantics
- compiler behavior
- actual routing plan

### `frontend/app/zones.js`
Preserve:
- room/zone containment
- movement boundaries

### `frontend/app/terrain.js`
Preserve terrain/geometry semantics unless a visual-only parameter is explicitly identified.

### `frontend/app/worldrenderer.js`
Preserve renderer behavior and fallback logic.
Only visual constants may be tuned after baseline proof.

### `frontend/app/worldlight.js`
Preserve lighting mechanics.
Palette/light color may be retuned later.

## Agent/runtime logic

### `frontend/app/harness.js`
Keep unchanged except for unavoidable product-label strings.

### `frontend/app/queryspine.js`
Keep unchanged.
It is a runtime truth/query utility, not presentation.

### `frontend/app/autonomy.js`
### `frontend/app/autonomystore.js`
### `frontend/app/autopilot.js`
### `frontend/app/autopilotstore.js`
### `frontend/app/autojobs.js`
### `frontend/app/autojobstore.js`
Keep behavioral logic unchanged during rebrand.

### `frontend/app/permissions.js`
### `frontend/app/permissionsstore.js`
Keep authorization logic unchanged.

### `frontend/app/backup.js`
### `frontend/app/cloudsave.js`
### `frontend/app/save.js`
### `frontend/app/freshstart.js`
Preserve persistence and recovery behavior.

### `frontend/app/cronhuman.js`
### `frontend/app/schedpicker.js`
Preserve scheduling semantics.

### `frontend/app/updatecore.js`
Keep update planning logic unchanged; release endpoints/branding live elsewhere.

## Memory / intelligence stores

Keep behavioral logic unchanged:
- `dossier.js`
- `dossierstore.js`
- `profile.js`
- `profilestore.js`
- `recommend.js`
- `recquality.js`
- `recqualitystore.js`
- `goals.js`
- `goalstore.js`
- `understanding.js`
- `understandingstore.js`
- `trust.js`
- `truststore.js`
- `worksignal.js`
- `worksignalstore.js`
- `workstreams.js`

Their **rendered presentation** may be reskinned by CSS or wrapper markup, but the state logic remains.

## Provider / voice / channels behavior

Keep mechanics unchanged:
- `modelpicker.js`
- `codexsignin.js`
- `channels.js`
- `group-chat.js`
- `voice.js`
- `voice-live.js`
- `voice-stream.js`
- `keepawake.js`
- `lifecycle.js`
- `emergency-control.js`

Labels/chrome may change.

---

# Bucket 2 — RESKIN / REBRAND

This is the main Xenexus conversion surface.

## A. Global theme / palette

### `frontend/css/style.css`
**Primary Xenexus theme entry point.**

Current code already exposes centralized theme tokens:
- `--ph`
- `--ph-bright`
- `--ph-dim`
- `--ph-faint`
- `--ink`
- `--ph-glow`
- `--ph-glow2`
- `--bg`
- `--panel`
- `--panel2`
- `--gold`
- `--text`
- RGB companion tokens
- camera grade

Action:
- add a dedicated `body.theme-xenexus`
- make Xenexus the internal default
- primary: electric blue / cyan
- accent: Xenexus yellow/gold
- background: near-black/navy
- semantic green stays reserved for actual success/online state
- semantic red stays reserved for faults/danger

Important:
Do not make green the brand color. It remains a semantic status color.

## B. Secondary CSS surfaces

Reskin, do not rewrite behavior:

- `frontend/css/app.css`
- `frontend/css/interface.css`
- `frontend/css/panelchrome.css`
- `frontend/css/topbar.css`
- `frontend/css/titlebar.css`
- `frontend/css/widgets.css`
- `frontend/css/comms.css`
- `frontend/css/comms-layout.css`
- `frontend/css/glass-comms.css`
- `frontend/css/menu-glass.css`
- `frontend/css/settings.css`
- `frontend/css/onboarding.css`
- `frontend/css/overseer-setup.css`
- `frontend/css/agent-dossier.css`
- `frontend/css/marketplace.css`
- `frontend/css/refit.css`
- `frontend/css/refit-kit.css`
- `frontend/css/refit-polish.css`
- `frontend/css/tasks.css`
- `frontend/css/quests.css`
- `frontend/css/project-home.css`
- `frontend/css/workhub.css`
- `frontend/css/warroom.css`
- `frontend/css/beat-cards.css`
- `frontend/css/utility-menus.css`
- `frontend/css/readability.css`
- `frontend/css/motion.css`
- `frontend/css/asciifx.css`

Approach:
- inherit Xenexus tokens
- avoid one-off literal colors where possible
- preserve existing geometry/layout
- preserve accessibility states and control-floor behavior

## C. Brand assets

### Replace:
- `frontend/assets/brand/starnet-logo.png`
- `frontend/assets/brand/starnet-logo-small.png`
- `frontend/assets/brand/starnet-wordmark.svg`

With Xenexus equivalents.

Recommended new files:
- `frontend/assets/brand/xenexus-logo.png`
- `frontend/assets/brand/xenexus-logo-small.png`
- `frontend/assets/brand/xenexus-wordmark.svg`
- `frontend/assets/brand/xenexus-emblem.png`
- `frontend/assets/brand/xenexus-keyart.png`

Keep provider/platform logos separate and unchanged.

## D. Sprite / character skin system

### `frontend/assets/sprites/`
**Reskin content, preserve structure.**

Current runtime expects sprite sets + manifest-defined frames.

Action:
- add Xenexus-original agent sprite sets
- retain expected directional/animation filenames
- update `manifest.json` through the existing asset workflow
- phase out inappropriate third-party/pop-culture skins from the internal default selection
- preserve animation/state contract

Recommended initial Xenexus roles/skins:
- Overseer / Command
- Research
- Engineering
- Intelligence
- Security
- Data
- Infrastructure
- Creator / Media

Art direction:
- operational sprites stay 8/16-bit inspired
- richer comic portraits may be separate dossier art

## E. Furniture / props

### `frontend/assets/furniture/`
Reskin selectively.

High-value replacements:
- workstation/desk
- console
- screens
- holotable
- core
- war table
- comms wall
- chart wall
- racks
- conveyor belts
- outbox/parcels/crates
- recruitment/specialist equipment where visible

Preserve file footprint/dimensions where practical to avoid geometry changes.

## F. Prop rendering assets

### `frontend/app/propsprites.js`
Do not rewrite logic.
Update sprite definitions/assets where necessary.

### `frontend/app/prop-catalog-data.js`
Mostly labels/art metadata.
Rebrand visible names/descriptions while preserving capability object types.

### `frontend/app/classicons.js`
Keep class semantics.
Reskin the seal/icon visual language into Xenexus.

## G. Industrial/world surface art

Reskin:
- `industrialtextures.js`
- `worldsurface.js`
- authored furniture/machine visual config modules
- backdrop assets
- room texture presets

Preserve geometry and behavior.

## H. Typography

Keep local/offline font behavior.

VT323 already fits the retro operational layer well.

Possible Xenexus split:
- runtime console: VT323 / pixel terminal
- rich dossier/key art: separate local display treatment

Do not introduce a network font dependency.

---

# Bucket 3 — SURGICALLY MODIFY

These modules need small, deliberate edits because they bridge runtime state and presentation.

## 1. `frontend/index.html`

Modify:
- document title: STARNET → XENEXUS
- ARIA/product labels
- splash logo path
- boot veil product name
- splash subtitle
- visible terminology
- body default theme → Xenexus
- preload path for chosen Xenexus boot asset

Preserve:
- IDs
- element structure
- script order
- screen structure
- event hook targets

This is high leverage and low architectural risk.

## 2. `frontend/app/app.js`

Surgical changes only.

Modify:
- visible product terminology
- default Xenexus theme selection
- default skin roster if desired
- default lead/Overseer presentation
- user-facing labels that still say StarNet
- possibly suit-color palette to match Xenexus

Preserve:
- `agents = new Map()`
- focus behavior
- roster mechanics
- provider handling
- approval-mode behavior
- agent create/resume flow
- bridge authority logic

Do not refactor app state for visual reasons.

## 3. `frontend/app/stationui.js`

This is a major presentation controller and therefore a surgical surface.

Modify:
- visible window/panel labels
- theme application
- Xenexus terminology
- chrome presentation hooks
- inspector labels

Preserve:
- runtime state mapping
- event handling
- window behavior
- telemetry provenance

## 4. `frontend/app/topbar.js`

Modify:
- logo/name treatment
- status wording if appropriate
- Xenexus header chrome

Preserve actual signal truth.

## 5. `frontend/app/navdock.js`
## 6. `frontend/app/leftrail.js`
## 7. `frontend/app/modeldock.js`
## 8. `frontend/app/widgets.js`

These are the best place to introduce the approved dashboard framing without touching the world engine.

Possible Xenexus use:
- left rail = active agents / major operations shortcuts
- right or dock widgets = focused-agent / room / task telemetry
- bottom widgets = routing, activity, cost, system health

Only use real runtime signals.

## 9. `frontend/app/agentportraits.js`

Current portrait system crops `rot_south.png` from the active sprite set.

Surgical enhancement opportunity:
- preserve current behavior as fallback
- optionally support a richer explicit portrait asset per Xenexus skin
- if rich portrait missing, keep current sprite crop

This cleanly enables:
- retro sprite in world
- comic-style portrait in dossier/roster

without touching world rendering.

Suggested convention:
`assets/sprites/<set>/portrait.png`

## 10. `frontend/app/skinstage.js`

Preserve animation logic.
Modify only:
- Xenexus labels
- default available sets
- possibly portrait/preview framing

## 11. `frontend/app/build.js`

Preserve build/refit mechanics.

Modify visible:
- room/category labels
- Xenexus naming
- art previews
- prop descriptions
- skin/theme chrome

Do not alter world placement semantics.

## 12. `frontend/app/marketplace.js`

Preserve:
- specialist/recruitment mechanics
- class selection
- recipes
- summon flow
- loadout semantics

Modify:
- “Recruitment Bay” visual language if desired
- Xenexus class names/labels
- class seals
- dossier presentation
- role terminology

## 13. `frontend/app/recruiter.js`

Preserve recommendation logic.
Modify visible wording/labels only.

## 14. `frontend/app/chat.js`

Very large and high-risk.

Do not broadly refactor.

Surgical changes:
- Xenexus terminology
- COMMS styling hooks
- product name
- agent portrait presentation if necessary

Preserve:
- conversation state
- streaming
- tool/run interaction
- recommendation beats
- task brief behavior

## 15. `frontend/app/crtlab.js`

Preserve tool.
Use it to tune Xenexus CRT parameters rather than hardcoding blindly.

## 16. `frontend/app/world.js`

Bucket 1 for behavior, Bucket 3 for tiny visual hooks only.

Allowed:
- read Xenexus palette constants
- Xenexus room-label style
- Xenexus route/belt colors
- Xenexus visual asset references
- CRT tuning
- sprite asset references

Not allowed:
- new world model
- new pathing
- new room semantics
- duplicated agent state
- dashboard-specific fake state

---

# Existing UI ↔ Xenexus target mapping

| Existing StarNet surface | Xenexus treatment | Bucket |
|---|---|---|
| Live station canvas | Keep center stage; recolor/re-art | 1 + 2 |
| Crew sprites | Xenexus original retro sprites | 2 |
| Agent portraits | Optional richer Xenexus portraits | 3 |
| Rooms/corridors | Same geometry, Xenexus textures/labels | 2 |
| Workstations/props | Same capabilities, new art | 2 |
| Conveyor/work items | Same mechanics, Xenexus colors/assets | 2 |
| Routing lines | Same routing truth, Xenexus blue/yellow language | 2/3 |
| Splash | Xenexus key art / wordmark | 2/3 |
| Top bar | Xenexus brand chrome | 3 |
| Left rail | Active crew / shortcuts | 3 |
| Widgets | Real status/task/cost/health telemetry | 3 |
| COMMS | Same functionality, Xenexus chrome | 2/3 |
| Recruitment Bay | Same mechanic, Xenexus class identity | 2/3 |
| Dossier | Same state, richer comic portrait treatment | 2/3 |
| Refit/build mode | Same station editing, Xenexus catalog art | 2/3 |
| Settings | Same controls, Xenexus theme | 2 |
| CRT | Preserve and tune | 1/3 |

---

# Recommended implementation order

## Phase X1 — Brand shell

**Status:** Implemented on `stratagem/bootstrap-audit`; draft PR #1 open for validation.

Low risk, immediate visual payoff.

1. add Xenexus theme tokens
2. set internal default to `theme-xenexus`
3. replace product title/name strings in `index.html`
4. add Xenexus wordmark/emblem assets
5. replace splash/boot branding
6. update topbar/titlebar branding
7. keep layout exactly as-is

Gate:
- no DOM IDs changed
- no behavior changed
- `test:fast` remains green

## Phase X2 — Station palette

**Status:** Implemented on `stratagem/bootstrap-audit`; pending visual/runtime validation.

Implemented:
- Xenexus blue/gold conveyor palette
- blue live-route/merge activity treatment
- gold route-direction and dock emphasis
- Xenexus bay/name plates
- Xenexus-blue room stencils
- existing dark-blue WorldLight illumination retained because it already aligns with the target palette
- no changes to conveyor simulation, routing compiler, pathing, geometry, or world state

1. tune camera grade
2. change world UI overlays from amber/green dominance to blue/yellow Xenexus
3. tune CRT via existing CRT lab
4. reskin route/conveyor visual accents
5. preserve semantic online/error colors

Gate:
- world interactions unchanged
- camera/pathing unchanged
- route truth unchanged

## Phase X3 — Agent identity

**Status:** Implemented as compatibility-first identity layer; pending runtime/visual validation.

Implemented:
- six visible Xenexus identities: Vanguard, Cipher, Forge, Specter, Aegis, Relay
- Xenexus-first default skin catalog
- legacy skins remain readable for existing saves but hidden from normal new-agent pickers
- explicit richer portrait assets for crew/COMMS/dossier
- portrait fallback to existing sprite crop
- Xenexus suit/accent palette
- no changes to sprite manifest, pathing, movement state, specialties, tools, or permissions

Art note:
- current world sprites reuse proven neutral animation chassis
- fully original Xenexus directional sprite sets are deferred to an art-only X3B pass

1. create first Xenexus sprite family
2. integrate via current sprite manifest
3. add optional `portrait.png` support
4. retain sprite-crop fallback
5. retheme class seals

Gate:
- same agent IDs/state
- same movement/animation state machine
- no roster changes

## Phase X4 — Rooms and props

1. re-art high-visibility props
2. retheme room surfaces
3. rename visible room labels if desired
4. keep objectType/capability contracts unchanged

Gate:
- placement/pathfinding unchanged
- capability grants unchanged

## Phase X5 — Dashboard framing

Use existing surfaces instead of introducing a second dashboard application.

1. left rail → active agents / operations
2. topbar → Xenexus command chrome
3. widgets → real task/provider/cost/system telemetry
4. focused-agent/room inspector via existing windows/widgets
5. live station remains the center

Gate:
- every displayed metric has a real source
- no duplicated state

## Phase X6 — Secondary surfaces

Reskin:
- COMMS
- dossier
- recruitment
- settings
- tasks
- routines
- connectors
- outbox
- logbook
- refit

Do not change behavior unless separately approved.

---

# Approximate change ratio

Target:

- **70–80% existing code/mechanics untouched**
- **15–20% CSS/assets/labels**
- **5–10% surgical presentation adapters**

If the implementation starts requiring large new data models or major changes to `world.js`, stop and reassess.

---

# High-risk files

Treat these as hot files:

- `frontend/app/world.js`
- `frontend/app/stationui.js`
- `frontend/app/app.js`
- `frontend/app/chat.js`
- `frontend/app/build.js`
- `frontend/index.html`
- `frontend/css/app.css`
- `frontend/css/style.css`

Changes should be narrow, tested, and staged.

---

# Low-risk/high-value files

Best first targets:

- `frontend/assets/brand/*`
- new Xenexus asset folders
- `frontend/css/style.css` theme token block
- `frontend/css/topbar.css`
- `frontend/css/titlebar.css`
- `frontend/index.html` visible branding strings/assets
- `frontend/app/topbar.js` visible labels
- `frontend/app/agentportraits.js` optional portrait fallback support

---

# Locked implementation principle

> **Change the skin, feel, terminology, and art. Keep the look/layout/style and keep the runtime mechanics.**

Xenexus should feel like the same sophisticated live station, now wearing a coherent Xenexus identity.
