# AI Systems Operating Charter

**Owner:** TJ  
**Organization:** Stratagem Group  
**Status:** Adopted  
**Version:** 1.0  
**Last updated:** 2026-09-23

---

## 1. Purpose

This charter defines the role, scope, routing logic, and authority boundaries for the AI systems used across TJ's personal, professional, research, creative, and technical workflows.

The goal is to avoid tool overlap, preserve security boundaries, reduce unnecessary complexity, and ensure each system is used where it provides the greatest value.

The governing principle is simple:

> **Automate the predictable. Delegate the intelligent. Supervise the consequential. Experiment separately. Build the future from first principles.**

---

## 2. System Roles

### 2.1 ChatGPT / Command Layer

**Primary role:** strategy, design, supervision, synthesis, and high-consequence reasoning.

ChatGPT / Command is the primary planning and decision-support layer.

Use it for:

- strategy
- architecture
- planning
- synthesis
- sensitive reasoning
- cross-system coordination
- major technical decisions
- security decisions
- legal and financial reasoning support
- workflow design
- review of outputs from other systems
- final approval of consequential actions

ChatGPT / Command is where missions are defined, work is routed, boundaries are set, and outputs are reviewed before high-consequence execution.

---

### 2.2 Otto

**Primary role:** predictable automation.

Otto handles mundane, repetitive, low-risk, non-critical personal and business workflows that can be expressed as deterministic triggers, routines, SOPs, or app-to-app automations.

#### Otto Category A — Routine Administration

Examples:

- reminders
- calendar housekeeping
- appointment logistics
- routine email triage
- standard follow-ups
- checklist automation
- simple filing and organization
- recurring administrative housekeeping

#### Otto Category B — App-to-App Automation

Examples:

- email → task
- form → spreadsheet
- calendar → reminder
- file arrival → folder
- approved content → scheduled publishing queue
- notification → tracker update
- routine data movement between systems

#### Otto Category C — Low-Risk Recurring Operations

Examples:

- collect routine metrics
- generate basic recurring status reports
- organize content calendars
- send standard reminders
- watch for simple state changes
- maintain recurring trackers
- routine file hygiene

#### Otto Category D — Mundane Personal Productivity

Examples:

- repetitive personal workflows
- standard task management
- templated responses
- recurring household or administrative reminders
- predictable coordination tasks

### Otto Routing Rule

> **If a competent administrative assistant could perform the task reliably from a written SOP without substantial judgment, Otto is the preferred system.**

### Otto Exclusions

Otto must not be used for:

- sensitive legal matters
- consequential debt or settlement decisions
- personal financial execution
- medical matters
- security-clearance matters
- critical credentials
- Nomentis internals
- Echo Lite internals
- sensitive research architecture
- high-consequence security actions
- confidential strategic decisions

Otto operates under least privilege and should remain intentionally narrow.

---

### 2.3 StarNet

**Primary role:** agentic operations.

StarNet handles substantial work that requires reasoning, tool use, iteration, persistence, delegation, specialization, or bounded autonomy.

StarNet is not a simple automation engine. It is the operational environment for AI workers.

#### StarNet Category X — Agentic Knowledge Work

Examples:

- technical research
- academic research
- repository analysis
- code review
- software engineering investigation
- threat analysis
- intelligence gathering
- comparative analysis
- structured synthesis
- debugging
- incident investigation
- deliverable creation that requires judgment

Typical pattern:

```text
TJ objective
    ↓
Lead agent
    ↓
Task decomposition
    ↓
Specialist work
    ↓
Critique / verification
    ↓
Synthesis
    ↓
Deliverable
```

#### StarNet Category Y — Long-Running Autonomous Operations

Examples:

- scheduled research sweeps
- repository health checks
- recurring engineering analysis
- bounded maintenance workflows
- monitored intelligence collection
- background technical investigation
- recurring code/test/review cycles
- long-running backlog processing

Autonomous execution must remain bounded by explicit permissions, execution profiles, budgets, and review rules.

#### StarNet Category Z — Multi-Agent Operations

Examples:

- lead + researcher + critic + synthesizer workflows
- engineering + QA + security workflows
- intelligence + analysis + briefing workflows
- parallel research teams
- specialist delegation
- ephemeral worker swarms
- persistent expert crews
- mixed-model task execution

### StarNet Routing Rule

> **If completing the task requires an AI worker to figure things out through reasoning, tools, delegation, iteration, or bounded autonomy, StarNet is the preferred system.**

---

### 2.4 Echo Lite

**Primary role:** cognitive experimentation.

Echo Lite exists to test concepts, hypotheses, interaction patterns, memory approaches, agent behaviors, and architectural ideas.

Use Echo Lite for:

- proof-of-concept experiments
- cognition-related tests
- memory experiments
- identity experiments
- continuity experiments
- controlled architecture validation
- experimental human-AI interaction research

Echo Lite is not a production operations platform.

Lessons may inform future work, but operational convenience must not turn Echo Lite into a general automation system.

---

### 2.5 Nomentis

**Primary role:** greenfield cognitive AI architecture.

Nomentis is the long-term system for deeper cognition, identity, continuity, metacognition, memory, learning, and human-AI interaction.

Nomentis must remain architecturally independent.

External harnesses, agent frameworks, automation systems, and third-party orchestration systems may be studied, but they are not to become foundational architecture.

Nomentis remains a first-principles build.

---

## 3. System Boundary Summary

| System | Primary Function | Governing Rule |
|---|---|---|
| ChatGPT / Command | Strategy, supervision, sensitive reasoning | Supervise the consequential |
| Otto | Predictable automation | Automate the predictable |
| StarNet | Agentic operations | Delegate the intelligent |
| Echo Lite | Cognitive experimentation | Test the experimental |
| Nomentis | Greenfield cognitive architecture | Build the future from first principles |

---

## 4. Workflow Routing

Every new workflow must be assigned to a system before implementation.

### Route to Otto when:

- the workflow is deterministic
- the workflow is repetitive
- the steps can be expressed as a stable SOP
- the consequences of an error are low
- little or no adaptive reasoning is needed
- the work is primarily app-to-app automation or routine administration

### Route to StarNet when:

- the task requires judgment
- the task requires investigation
- the task benefits from persistent workers
- multiple specialists may be useful
- tool use is required
- the work must adapt as new information appears
- the task may span a long period
- the work requires critique, synthesis, or iterative refinement

### Keep in ChatGPT / Command when:

- the matter is highly strategic
- the matter is sensitive
- consequences are substantial
- legal, financial, medical, security, clearance, or major architectural judgment is involved
- the user has not yet approved operational execution
- the problem itself still needs to be framed

### Route to Echo Lite when:

- the objective is experimentation rather than operational output
- the work concerns cognition, identity, continuity, memory, or experimental architecture
- failure is acceptable and learning is the primary objective

### Route to Nomentis when:

- the work is part of the actual Nomentis architecture
- the work contributes directly to the long-term cognitive system
- the requirement should be implemented from first principles rather than imported from an external harness

---

## 5. Authority and Security Model

### 5.1 Least Privilege

Every system, agent, integration, and workflow receives only the authority necessary to complete its intended job.

Broader access must be justified, explicit, and revocable.

---

### 5.2 StarNet Execution Profiles

StarNet agents should operate under explicit execution profiles.

#### ISOLATED

Default for untrusted, experimental, or high-uncertainty work.

- Docker Safe Cell
- no arbitrary host shell
- no broad host filesystem
- limited connectors
- narrow network authority
- strict execution boundaries

#### STANDARD

Default for routine agentic knowledge work.

- scoped workspace access
- safe reads
- bounded tools
- mutations require approval where appropriate
- no broad host authority

#### TRUSTED

For proven agents and workflows requiring broader capability.

- selected host access
- selected connectors
- standing grants where justified
- broader execution rights
- full audit visibility

#### FULL ACCESS

Exceptional expert mode only.

- broad host authority where supported
- shell access
- host filesystem access
- GUI/screen/input access where supported
- external connectors as explicitly configured
- explicit Commander authorization
- high-visibility telemetry
- immediate revocation capability

Full Access must never become the casual default.

---

## 6. High-Consequence Work

The following require explicit review and should remain under ChatGPT / Command supervision unless a separate operating policy explicitly authorizes automation:

- legal strategy
- debt settlement or litigation actions
- personal financial decisions
- medical decisions
- security-clearance matters
- destructive infrastructure changes
- credential changes
- high-impact cybersecurity actions
- public releases with material reputational consequences
- Nomentis core architecture decisions
- any action that is difficult to reverse

---

## 7. Operating Principles

### 7.1 Truthful Telemetry

No system may claim an action was completed, verified, approved, or successful unless runtime evidence supports that claim.

### 7.2 Human Authority

Autonomy assists human decision-making. It does not replace final human authority for consequential actions.

### 7.3 Reversibility First

Prefer actions that are inspectable, bounded, reversible, and recoverable.

### 7.4 Separation of Concerns

Do not allow:

- Otto to become StarNet
- StarNet to become Echo Lite
- StarNet to become Nomentis
- Echo Lite to become production infrastructure by accident
- convenience tooling to dictate Nomentis architecture

### 7.5 Explicit Escalation

Higher privilege must be consciously granted.

No system or agent may silently promote itself into a more permissive operating posture.

### 7.6 Auditability

Important workflows must retain enough provenance to determine:

- what acted
- when it acted
- why it acted
- what tools were used
- what data or evidence informed the action
- what permissions were active
- what the result was

### 7.7 Workflow Assignment Before Implementation

No new automation or agentic workflow should be built until its owning system is identified.

---

## 8. Workflow Intake Template

Before implementing a new workflow, answer:

1. What is the objective?
2. Is the work deterministic or agentic?
3. Does it require substantial reasoning?
4. Is the work repetitive?
5. Is the work low-risk or high-consequence?
6. Does it require one worker or multiple specialists?
7. Does it require persistent context or memory?
8. Does it require host or external-system access?
9. Does it involve sensitive information?
10. What system should own it?
11. What permissions are required?
12. What approvals are required?
13. What audit trail is required?
14. How is failure detected?
15. How is the workflow stopped or rolled back?

---

## 9. Quick Routing Matrix

| Question | Route |
|---|---|
| Can this be expressed as a stable SOP? | Otto |
| Is this mostly app-to-app plumbing? | Otto |
| Does the worker need to investigate or reason? | StarNet |
| Does the work benefit from specialist delegation? | StarNet |
| Does it need long-running bounded autonomy? | StarNet |
| Is the matter sensitive or high-consequence? | ChatGPT / Command |
| Is the primary objective experimentation? | Echo Lite |
| Is this part of the actual cognitive architecture? | Nomentis |

---

## 10. Initial Approved Scope

### Otto

Approved initial scope:

- reminders
- calendar support
- routine task logistics
- file organization
- templated administrative follow-up
- simple cross-app automation
- recurring low-risk reports
- content scheduling pipelines
- predictable personal productivity routines

### StarNet

Approved initial scope:

- repository analysis
- software engineering support
- multi-agent research
- technical investigation
- intelligence monitoring
- code / test / fix workflows
- bounded autonomous maintenance
- multi-step knowledge work
- specialist-team operations
- persistent agent workflows
- controlled background work

---

## 11. Governance

**Owner:** TJ

The owner retains final authority over:

- system boundaries
- privilege escalation
- deployment
- production use
- high-consequence execution
- architecture changes
- exceptions to this charter

ChatGPT / Command acts as the primary planning, coordination, and review layer.

Changes to this charter should be deliberate and versioned.

---

## 12. Adoption

This charter governs current AI-system usage unless explicitly superseded by a later approved version.

When routing is ambiguous:

1. prefer the narrower system
2. prefer the lower privilege level
3. keep consequential work under direct human review
4. escalate only when the operational need is clear

