# Xenexus Frontend Preservation Doctrine

**Status:** Locked  
**Date:** 2026-09-23  
**Applies to:** Stratagem's internal Xenexus derivative of StarNet

## Core decision

Xenexus will **preserve the existing StarNet world/station engine** and rebrand, reskin, and reorganize the presentation around it.

The live station is not to be replaced by a static dashboard.

## Preserve as core product behavior

The following existing capabilities are considered foundational and must remain intact unless a separate defect or architecture decision explicitly requires change:

- multi-room station rendering
- rooms and corridors
- agents physically represented as characters
- agent walking/pathing between rooms
- workstations and capability props
- multiple crew members
- conveyor/work-item movement
- compiled routing plans
- energized/live routes
- task activity
- camera pan/zoom
- CRT rendering and scanline effects
- live rebuilds when the station layout changes

## Xenexus design rule

The Xenexus redesign should operate primarily through:

- branding
- color system
- typography
- application chrome
- splash/boot presentation
- room labels and naming
- room visual treatment
- character sprites
- agent portraits/dossiers
- capability icons
- workstation art
- flooring/wall textures
- panel framing
- navigation presentation
- telemetry presentation
- terminology

The runtime mechanics should remain the source of truth.

## Dashboard relationship

The approved Xenexus dashboard concept is a **visual shell / framing reference**, not a replacement architecture.

Preferred composition:

```text
┌─────────────────────────────────────────────────────────────┐
│ XENEXUS                                   SYSTEM / STATUS   │
├────────────┬──────────────────────────────┬─────────────────┤
│ ACTIVE     │                              │ FOCUSED AGENT   │
│ AGENTS     │      LIVE STATION WORLD      │ / ROOM INSPECTOR│
│            │                              │                 │
│ portraits  │ rooms • agents • movement   │ model           │
│ roles      │ workstations • workflows    │ permissions     │
│ activity   │ conveyors • data flow       │ tasks           │
│            │                              │ tools / cost    │
├────────────┼──────────────────────────────┼─────────────────┤
│ TASK QUEUE │ ROUTING / ACTIVITY / HEALTH / FLOW            │
└────────────┴────────────────────────────────────────────────┘
```

The center remains the existing live station canvas.

## Truthful telemetry

No dashboard widget, status indicator, gauge, percentage, chart, or alert may be added unless the underlying runtime can prove the value.

Preferred real signals include:

- active agents
- queued/running tasks
- run count
- tool calls
- provider latency
- token use
- model cost
- failed runs
- Docker / execution backend health
- connector health
- MCP health
- real routing/work-item state

Decorative fake telemetry is prohibited.

## Art layering

Xenexus uses two complementary presentation layers:

### Runtime world

- retro 8-bit / 16-bit visual language
- readable pixel/terminal presentation
- simple character sprites
- lightweight room art
- high clarity during live operation

### Identity / key art

- richer comic-book-inspired art
- agent portraits
- dossiers
- splash/key art
- branding and promotional/internal presentation

This allows character identity to be visually rich without making the operational world heavy or difficult to read.

## Implementation preference

Favor:

1. theme tokens
2. CSS changes
3. asset replacement
4. label/terminology changes
5. presentation-layer composition
6. small adapters around existing runtime state

Avoid:

- replacing `world.js`
- duplicating world state
- inventing a second dashboard data model
- creating fake agent/room state for presentation
- rewriting pathing, routing, or crew behavior for visual reasons
- turning the station into a static analytics console

## Guiding statement

> **Reskin and reorganize StarNet into Xenexus. Preserve its world model, runtime mechanics, agent state, room system, workflow visualization, and truthful telemetry. Add Xenexus presentation around those systems rather than replacing them.**
