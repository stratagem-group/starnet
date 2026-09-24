# Xenexus Secondary Surfaces

**Status:** X6 implemented, pending runtime/visual validation  
**Date:** 2026-09-23

## Objective

Bring secondary application surfaces into the Xenexus identity without changing their handlers, stores, API routes, window keys, persistence keys, or workflow semantics.

## Surfaces covered

- COMMS
- Agent dossier
- Commander profile
- Recruitment / Agent Registry
- Settings
- Operations board
- Routines / Automation
- Connectors / Abilities
- Outbox
- Logbook / Record
- REFIT / Build mode
- Manual / Objectives

## Terminology changes

### Window names

- AGENT DOSSIER → XENEXUS AGENT DOSSIER
- COMMANDER DOSSIER → COMMANDER PROFILE
- TASK BOARD → OPERATIONS BOARD
- FIELD MANUAL → COMMAND MANUAL
- QUEST LOG → OBJECTIVES
- RECRUITMENT BAY → AGENT REGISTRY

Core concepts retained:
- COMMS
- OUTBOX
- ROUTINES
- AUTOMATION
- ABILITIES
- SETTINGS
- REFIT / BUILD
- AGENT RECORD

These already fit the Xenexus operating model and are not renamed merely for novelty.

## Build mode

Visible build-mode identity now uses:
- XENEXUS BUILD MODE
- XENEXUS / STATION PRESETS
- XENEXUS · QUICK GUIDE

The build engine, palette IDs, prop IDs, geometry, and event handling are unchanged.

## Secondary window chrome

Under `theme-xenexus`, floating windows receive:
- blue structural border
- subtle blue halo
- gold title/section accents
- gold active rail marker
- dark command-console header treatment

No dimensions, drag behavior, resize behavior, focus behavior, or console layout were changed.

## Connector / extension copy

Visible local extension copy now describes extending Xenexus rather than StarNet.

External service names are not blindly relabeled when they refer to a real upstream/external service contract.

## Compatibility

Internal identifiers remain stable, including examples such as:
- `tasks`
- `agents`
- `commander`
- `manual`
- `quests`
- `connectors`
- `outbox`
- `crew`
- localStorage keys under the historical `starnet.*` namespace

Those internal names are compatibility surfaces, not branding.

## Guiding rule

> Rebrand the surface, not the contract.
