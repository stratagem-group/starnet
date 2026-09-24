# StarNet Workflow Routing Guide

This guide implements the routing policy in `AI_SYSTEMS_OPERATING_CHARTER.md`.

## Otto vs StarNet

Use **Otto** when the work can be reduced to a predictable SOP, trigger, transfer, reminder, or low-risk recurring routine.

Use **StarNet** when the worker must investigate, reason, adapt, use tools, maintain task context, delegate, critique, or operate autonomously within a bounded authority.

## Quick examples

| Workflow | Owner |
|---|---|
| Calendar reminder | Otto |
| Email → task automation | Otto |
| Move approved file to destination | Otto |
| Scheduled approved social post | Otto |
| Routine metrics collection | Otto |
| Research a technical question | StarNet |
| Analyze a repository | StarNet |
| Reproduce and diagnose a bug | StarNet |
| Research + critique + synthesis | StarNet |
| Scheduled intelligence analysis | StarNet |
| Multi-agent engineering workflow | StarNet |

## StarNet X / Y / Z taxonomy

### X — Agentic knowledge work

Use for finite tasks that require adaptive reasoning and tools.

Examples:
- research
- analysis
- engineering
- code review
- debugging
- threat analysis
- OSINT
- synthesis

### Y — Long-running bounded autonomy

Use for recurring or prolonged work where the worker must decide what to do inside an explicit scope.

Examples:
- repository health sweeps
- scheduled research monitoring
- recurring technical investigations
- maintenance backlogs

### Z — Multi-agent operations

Use where specialization or parallelism adds value.

Examples:
- lead + researcher + critic
- developer + QA + security
- intelligence collector + analyst + briefer
- persistent specialist crew + ephemeral workers

## Intake decision

Before creating a StarNet workflow, record:

- objective
- category: X, Y, or Z
- sensitivity
- execution profile
- model/provider policy
- tool grants
- connector grants
- budget
- unattended eligibility
- approval gates
- failure signal
- stop/rollback method
- required audit evidence

## Escalation

A workflow may move from Otto to StarNet when deterministic automation is insufficient.

A StarNet workflow may move from STANDARD to TRUSTED or FULL ACCESS only when the operational requirement is documented and narrower authority is inadequate.

No workflow gains additional authority merely because it failed.
