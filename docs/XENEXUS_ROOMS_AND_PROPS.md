# Xenexus Rooms and Props Skin

**Status:** X4 implemented, pending runtime/visual validation  
**Date:** 2026-09-23

## Objective

Make the physical station read as Xenexus without changing its world model, geometry, pathing, prop footprints, capability contracts, or routing semantics.

## New-station identity

New stations now begin as:

- station name: `XENEXUS COMMAND`
- starter room: `COMMAND CORE`
- starter deck: cobalt panel surface

Existing saved stations retain their saved room names and materials unless the user edits them.

## Built-in template presentation

The built-in furnished templates now use Xenexus-facing names and cooler dark-blue deck choices.

| Existing template id | Xenexus-facing name |
|---|---|
| `default` | COMMAND CORE |
| `retreat` | QUIET ARCHIVE |
| `cozy` | ENGINEERING NODE |
| `creative` | CREATIVE NODE |
| `research` | RESEARCH NODE |
| `engineering` | ENGINEERING COMPLEX |
| `operations` | OPERATIONS COMPLEX |

Common room labels now include:

- COMMAND
- ENGINEERING
- RESEARCH
- CREATIVE LAB
- REVIEW
- COMMS
- ARCHIVES
- CREW LOUNGE

The physical layouts and hallway coordinates are unchanged.

## Surface treatment

Xenexus templates prefer existing cool/dark material combinations such as:

- cobalt
- indigo
- resin
- tread
- panel
- soft

No new floor geometry or material engine was introduced.

The existing world-surface and WorldLight systems remain authoritative.

## High-visibility prop labels

User-facing labels were changed where the object identity is presentation-only.

Examples:

| Prop ID | Xenexus-facing label |
|---|---|
| `desk` | WORKSTATION |
| `desk2` | DUAL WORKSTATION |
| `console` | COMMAND CONSOLE |
| `consoleL` | COMMAND CONSOLE L |
| `workbench` | ENGINEERING BENCH |
| `bay` | AGENT BAY |
| `core` | MEMORY CORE |
| `missionboard` | COMMAND BOARD |
| `bridge_consolebank` | COMMAND CONSOLE BANK |
| `bridge_tacticaltable` | OPS TABLE |
| `bigscreen` | OPS DISPLAY |
| `chartwall` | ANALYTICS WALL |
| `wartable` | OPS TABLE |
| `calwall` | SCHEDULE WALL |
| `bridge_tacscreen` | TACTICAL DISPLAY |
| `war_threatcore` | RISK CORE |

## Functional IDs remain unchanged

The following names are examples of IDs that must stay stable because runtime code depends on them:

- `intake`
- `bay`
- `outbox`
- `workbench`
- `connector_portal`
- `core`
- `missionboard`
- `airlock`

Only their display labels may change.

## Prop artwork

The existing procedural prop renderer is preserved.

Important existing behavior already aligns with Xenexus:
- decorative electronics are remastered toward a cyan/amber visual vocabulary
- screen emissives are runtime-driven
- activity/status lights are tied to real state
- prop geometry and silhouettes remain readable at the 12px tile scale

Therefore X4 does not introduce a second Xenexus prop renderer.

Future prop-art changes should be asset/palette refinements inside the existing renderer only.

## Mechanics explicitly preserved

- room rectangles
- room graph
- corridors
- door/path topology
- room kinds
- prop IDs
- prop dimensions
- blocking/walkability
- seat behavior
- capability mapping
- bay assignment
- conveyor routing
- workflow blueprint topology
- station serialization schema

## Guiding rule

> Xenexus changes what the room and equipment feel like, not what the room and equipment are.
