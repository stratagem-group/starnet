# Xenexus Agent Identity Layer

**Status:** X3 implemented, pending runtime/visual validation  
**Date:** 2026-09-23

## Objective

Give Xenexus its own agent identity system without rewriting the existing sprite/animation engine.

## Design

Xenexus uses two complementary identity layers:

### Live world
- existing proven sprite animation contract
- 8/16-bit style
- movement/pathing unchanged
- current neutral sprite sets reused as animation chassis

### Portrait / dossier
- explicit Xenexus portrait assets
- richer character identity
- used in crew rail, COMMS, and dossier when available
- sprite-crop fallback remains in place

## Initial Xenexus identities

| ID | Codename | Animation chassis | Identity role |
|---|---|---|---|
| `xenexus_command` | Vanguard | `approved_blank_amber` | command visual |
| `xenexus_research` | Cipher | `approved_blank_blue` | research visual |
| `xenexus_engineering` | Forge | `approved_blank_green` | engineering visual |
| `xenexus_intelligence` | Specter | `approved_android` | intelligence visual |
| `xenexus_security` | Aegis | `approved_robot` | security visual |
| `xenexus_systems` | Relay | `approved_blank_red` | systems visual |

The codenames are appearance identities only. They do not grant tools, permissions, specialties, or capabilities.

## Compatibility

Legacy skin IDs remain in `DATA.SKINS` so old saves continue to resolve.

Legacy skins are hidden from normal Xenexus pickers but remain addressable by exact saved ID.

The dossier preserves the current legacy skin as a selectable/current item when viewing an old save.

## Portrait contract

A skin may declare:

```js
portrait: "assets/brand/portraits/example.svg"
```

Portrait resolution order:

1. explicit portrait asset
2. cropped `rot_south.png` sprite
3. existing procedural fallback where applicable

Failure of a portrait asset does not break the agent or world sprite.

## Files changed

- `frontend/app/data-shim.js`
- `frontend/app/agentportraits.js`
- `frontend/app/app.js`
- `frontend/app/stationui.js`
- `frontend/app/marketplace.js`
- `frontend/css/app.css`
- `frontend/assets/brand/portraits/*`

## Mechanics explicitly preserved

- sprite manifest contract
- world animation state
- directional walking
- sitting
- pathing
- agent IDs
- roster state
- specialties
- permissions
- capability grants
- model/provider selection

## Future X3B art pass

The current implementation deliberately reuses proven animation chassis.

A later art-only pass may replace those chassis with fully original Xenexus directional sprite sets, provided each new set satisfies the existing manifest/state contract and does not require world-engine changes.
