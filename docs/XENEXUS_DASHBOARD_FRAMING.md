# Xenexus Dashboard Framing

**Status:** X5 implemented, pending runtime/visual validation  
**Date:** 2026-09-23

## Objective

Apply the approved Xenexus dashboard framing to the existing live station without introducing a second dashboard architecture or duplicating runtime state.

## Existing layout preserved

The current game-screen layout remains:

- left: agents + sessions/projects
- center: live station canvas
- right: COMMS
- top: brand + real telemetry rail + station/uplink state
- bottom: existing docks + real telemetry rail + context gauge

No grid region was moved or replaced.

## X5 changes

### Agent rail

Visible label:

- `CREW` → `AGENTS`

Internal IDs and persistence keys remain unchanged:
- `#left`
- `#crew`
- `starnet.crewrail`
- `data-group="crew"`

This avoids unnecessary migration risk.

### Live station identity

A small static center-stage identifier now reads:

```text
XENEXUS  LIVE STATION
```

This is identity only, not telemetry.

The existing camera HUD remains authoritative for:
- camera readout
- connection state
- feed state
- activity ticker

### Fresh-install telemetry defaults

Fresh Xenexus installs begin with a restrained truthful telemetry layout:

Top rail:
- AGENTS
- ACTIVE
- NEEDS YOU

Bottom rail:
- RUNS · 24H
- QUEUE
- ROUTINES

Every one of these already existed and reads real application/runtime state.

A persisted widget layout always wins, including an intentionally empty layout. Existing users are not force-rearranged.

### Command-shell styling

When `theme-xenexus` is active:
- side-panel framing gains restrained blue structure
- panel headers gain a gold command accent
- the live station bezel gains a subtle Xenexus blue halo

No dimensions, resizing behavior, z-order contracts, or breakpoints were changed.

## Explicitly not implemented

X5 does **not** add:
- fake gauges
- fake CPU/storage/network percentages
- a separate world map
- a duplicate agent model
- a second task store
- a new inspector state model
- a replacement for COMMS
- changes to world.js behavior

## Dashboard principle

The approved concept is now represented as:

```text
┌──────────────────────────────────────────────────────────────┐
│ XENEXUS      [real pinned telemetry]       UPLINK / STATUS  │
├────────────┬───────────────────────────────┬─────────────────┤
│ AGENTS     │                               │ COMMS           │
│ sessions   │       LIVE STATION            │ focused agent   │
│ projects   │ rooms / agents / routing      │ conversation    │
│            │ conveyors / work / movement   │ model controls  │
├────────────┴───────────────────────────────┴─────────────────┤
│ docks       [real pinned telemetry]             CTX         │
└──────────────────────────────────────────────────────────────┘
```

The station remains the center of the product.
