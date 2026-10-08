# OPSLOOP — PRE-ARCH Candidate v0.5

**Status:** CONDITIONALLY APPROVED BY OWNER — NOT ARCHITECTURE CONFIRMED  
**Owner approval:** 2026-10-08 (DA-T11)  
**Recorded under:** DA-T12  
**Basis:** D-001/L-001 and D-002/L-002 (LOCKED in [ZASS.md](ZASS.md))  
**Implementation authorization:** NONE. No coding or technology selection authorized by this approval.

## 1. Purpose and boundaries

OPSLOOP is a solo-first Hybrid Lightweight Workspace for post-production operational decisions, verified outcomes, maintenance, reliability and learning. It begins following accepted handoff of a production release into operational ownership. Federated Authority is mandatory: monitoring owns original telemetry; GitHub/development tooling owns engineering work; CI/CD/deployment tools own their execution outcomes; commitment owners approve applicable SLA/SLO commitments. OPSLOOP owns authorized operational declarations/decisions, curated history, operational verification and learning. It is not a ZASS module or a replacement for monitoring, engineering trackers or deployment systems.

This document is an **owner-approved conditional conceptual baseline**, not the final architecture, a physical component diagram or executable proof.

## 2. Three approved logical capabilities

1. **Operational Workspace:** Progressive observation, incident handling, response, maintenance, verification, follow-through and learning. Normal observations and preventive maintenance require no artificial incident.
2. **Controlled Acceptance:** Actor/scope authorization, evidence sufficiency, protected transitions, safe handling of contradictory commands, and accepted/rejected/unknown write outcomes.
3. **Durable Operational Record:** Recoverable decision context, provenance, significant timeline, receipts, corrections, evidence gaps, verification and retrospective reconciliation.

These are logical capabilities **not** mandated services, modules, tables or databases. One lightweight deployable application remains possible.

## 3. Five approved architecture contracts

### AAC-01 — Authoritative Acceptance Contract
A protected operational decision is Accepted only after the minimum internally consistent record is durably committed with the applicable authorization and evidence prerequisites satisfied. A write reports **Accepted**, **Rejected** or **Unknown** honestly; ambiguous acknowledgment is reconciled before unsafe retry. Repeating the same logical operation must not silently create duplicate authoritative decisions. Local acceptance is distinct from external command execution and production outcome verification. No cross-system atomic transaction is implied.

### ERC-01 — Evidence & Record Context Contract
Source observation, preserved evidence, assessment, authorized decision, action, verification and correction remain semantically distinct. Material records preserve subject/scope, source, temporal context, provenance, uncertainty, evidence sufficiency/freshness/availability and traceable correction as relevant. Historical support is not automatically current evidence. Missing/stale information is not healthy service. Material evidence support is appropriately preserved or its later unverifiability is disclosed; wholesale telemetry copying is not required.

### ATC-01 — Authority & Transition Control Contract
Protected changes require effective scoped actor authority and transition-specific evidence. Conflicting decisions/commands follow D-002's seven stages: **DETECT → PRESERVE → CLASSIFY → CONTAIN → EVALUATE → RESOLVE/ESCALATE → RECONCILE**. Enforcement must cover actual in-scope authoritative write paths, not merely UI acknowledgments. AI has no autonomous authority promotion. Privileged repair and separately authorized emergency production recovery are exceptional and distinct from normal OPSLOOP acceptance. Any unconstrained owner/admin privileges must be disclosed as residual trust limitations.

### RC-01 — Operational Recovery Separation Contract
Restoring OPSLOOP's records does not prove production health; restoring production does not prove OPSLOOP record integrity. Authorized emergency production actions must remain possible if OPSLOOP is offline. Retrospective entries distinguish event/observation times from recording times, preserve actual outcomes and unresolved gaps, and reconcile late/conflicting records without silent overwrite. No guarantee of perfect reconstruction of irretrievably lost evidence.

### SUC-01 — Solo Usability & Continuity Contract
Progressive capture, risk-proportionate requirements and a coherent operator workspace preserve solo simplicity. A single person can hold authorized operational roles; no artificial multi-person approval chain. Maintenance can begin directly from service context; engineering issue closure is not automatically operational effectiveness verification. Additional controls arise only as a claim or transition becomes consequential.

## 4. T2-A — Approved initial MVP trust boundary

**Human-controlled authoritative writes with AI-assisted preparation.** AI may read permitted context and draft/summarize/correlate/propose. AI cannot autonomously declare incidents, change severity, verify recovery, confirm root causes, approve commitments, close protected actions or perform privileged repair. An authorized human reviews and authorizes protected transitions and an enforceable write path commits the accepted record. Human approval in chat/UI alone does not prove durable acceptance.

Initial AI receives no unrestricted authoritative-store write privilege. An agent using owner-level GitHub/storage credentials to bypass the controlled acceptance path is **not** compliant with T2-A. Human owner and authorized operators act only within applicable scopes; separate privileged repair requires explicit exceptional handling/audit; independent emergency production recovery remains legitimate under pre-established authority. Source systems retain original external authority.

**Deferred:** T2-B (technically scoped AI-mediated submissions after specific human approval), autonomous delegated AI writes and any additional automation authority. Each requires distinct owner authorization and executable enforcement evidence.

## 5. Minimum semantic record envelope

A common **logical** envelope with conditional requirements:
- Logical record/operation identity and affected subject/scope.
- Semantic kind: observation, assessment, decision, action, verification, follow-through or correction.
- The actual claim/decision/action; actor and effective authority when relevant.
- Event/observation time, decision time and recorded time where applicable; UNKNOWN explicitly retained.
- Evidence source, references, provenance, sufficiency, freshness, accessibility and uncertainty as relevant.
- Relevant prior context/state for consequential transitions; acceptance outcome and correction/related-record lineage.

Not every observation needs every field. Verified recovery **cannot** pass without the required appropriate evidence; a missing optional attachment can be disclosed without silently falsifying a previously valid decision. Service health, incident lifecycle and follow-through status are independent; epistemic status and write outcome are separate dimensions. An incident may affect multiple services. Exact schema, states and validators remain OPEN.

## 6. Seven approved acceptance scenarios

These are **expected behaviors, NOT executed tests**:

| Gate | Scenario | Expected behavior |
|---|---|---|
| PA-01 | Interrupted write | No false success receipt |
| PA-02 | Lost ACK and retry | Reconcile original operation; no duplicate authoritative decision |
| PA-03 | AI attempts unapproved recovery closure | Protected change denied / never silently accepted |
| PA-04 | Concurrent conflicting operator decisions | No silent overwrite; preserve, contain and resolve/escalate |
| PA-05 | External evidence expires | Preserve original context and disclose current evidence availability |
| PA-06 | OPSLOOP unavailable during production incident | Independent authorized recovery possible; later truthful reconstruction |
| PA-07 | Solo preventive maintenance | Direct service-linked work without artificial incident/approval hierarchy |

The selected implementation must later demonstrate relevant gates and explain residual limitations before production acceptance.

## 7. Candidate MVP scope and exclusions

**In-scope conceptual capabilities:** service ownership/expectations, manual observations, optional operational cases, authorized decisions and actions, evidence-linked verification, preventive maintenance, corrective follow-through, durable learning/history and retrospective reconciliation.

**Not mandatory for initial MVP:** continuous monitoring ingestion, autonomous AI operations, bidirectional GitHub sync, enterprise IAM/multiple approval chains, sophisticated offline queues, distributed transaction engines, wholesale logs or dedicated workflow orchestration.

No implementation feature is exempt from an applicable LOCKED invariant merely because it is included in MVP.

## 8. Explicitly OPEN implementation choices

| ID | Not yet selected |
|---|---|
| IM-01 | Git/Markdown, embedded database or other persistence |
| IM-02 | Atomic commit/durability mechanism |
| IM-03 | Operation identifiers, retry and deduplication implementation |
| IM-04 | Identity, permissions, credentials, enforcement topology |
| IM-05 | Evidence retention/snapshots/freshness thresholds/privacy |
| IM-06 | Offline capture/reconciliation implementation |
| IM-07 | Concurrency control, coordination and succession |
| IM-08 | CLI/web/chat/UI design |
| IM-09 | Monitoring/GitHub/CI-CD integrations |
| IM-10 | Hosting, backup/restore, recovery objectives |
| IM-11 | Exact status enums, state machine and protected transition enforcement |
| IM-12 | AI-mediated or autonomous write capabilities beyond T2-A |

Choices are deferred, **not waived**. Architecture and implementation must prove applicable guarantees rather than silently weaken them.

## 9. Acceptance readiness and residual risks

**Conceptual coherence:** owner conditionally approved.  
**Executed acceptance evidence:** NONE.  
**Architecture confirmed:** NO.  
**Coding authorized:** NO.

Residual risks: trustworthy enforcement against direct privileged AI writes; crash/ACK-loss durability; concurrency; evidence loss; undue solo-operator burden. Relevant mechanisms and tests must be resolved in subsequent architecture/implementation gates. PRE-ARCH conditional approval is not a claim that these risks have passed tests.

## 10. Audit lineage and approval receipt

- Discovery Tasks 1–4 → D-001/L-001 (LOCKED product foundation and federated ownership).
- D-002 proposal → Challenge Round 2 → owner-approved INV-11–INV-14 and CONTAIN → D-002/L-002 (LOCKED operational invariants).
- DA-T01 v0.1 → DA-T02 challenge → DA-T03 v0.2 (REV-01–REV-07).
- DA-T04 challenge → DA-T05 v0.3 (REV-08–REV-14).
- DA-T06 challenge → DA-T07 v0.4 (REV-15–REV-20).
- DA-T08 PRE-ARCH readiness → DA-T09 T2-A boundary proposal → DA-T10 v0.5 consolidation.
- **DA-T11 explicit owner approval:** “approve = 3 logical capabilities + 5 architecture contracts + T2-A trust boundary + 7 acceptance scenarios.”
- **DA-T12:** Repository recording of that *conditional* approval, without new D/L lock and without changing implementation authorization.

**Change control:** Any future alteration to this conditional baseline requires a traceable owner decision. No `ARCHITECTURE CONFIRMED` designation is authorized; final evidence-backed confirmation remains subject to the project's ZASS confirmation gate.
